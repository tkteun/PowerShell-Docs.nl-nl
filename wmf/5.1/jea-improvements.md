---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
contributor: ryanpu
title: Verbeteringen in Just Enough Administration (JEA)
ms.openlocfilehash: 47a58a6fae9f3a41ec527ec1f77ac1c196336669
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222414"
---
# <a name="improvements-to-just-enough-administration-jea"></a>Verbeteringen in Just Enough Administration (JEA)

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>Beperkte bestandskopie uit JEA-eindpunten

U kunt nu bestanden op afstand kopiëren/van een JEA eindpunt en rest gegarandeerd dat de gebruiker verbinding maakt alleen kan niet kopiëren *eventuele* bestand op uw systeem.
Dit is mogelijk door het configureren van uw bestand voor om te koppelen van een station van de gebruiker voor de verbinding van gebruikers.
De schijf van de gebruiker is een nieuwe PSDrive die uniek is voor elke gebruiker die verbinding maakt en blijft bestaan tussen sessies.
Wanneer het Item kopiëren wordt gebruikt om bestanden te kopiëren naar of van een sessie JEA, is deze beperkt tot alleen toegang tot de schijf van de gebruiker toestaan.
Pogingen om bestanden te kopiëren naar een andere PSDrive mislukken.

Gebruik de volgende nieuwe velden voordat u de schijf van de gebruiker in uw configuratiebestand JEA-sessie kunt instellen:

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

De map back-ups maken van de schijf van de gebruiker wordt gemaakt op `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`

Als u wilt gebruikmaken van de schijf van de gebruiker en kopieer de bestanden naar/van een eindpunt JEA is geconfigureerd om de schijf van de gebruiker weer te geven, gebruikt u de `-ToSession` en `-FromSession` parameters op Copy-Item.

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

U kunt vervolgens aangepaste functies om te verwerken van de gegevens die zijn opgeslagen in het station van de gebruiker en deze beschikbaar te maken voor gebruikers in uw bestand rol mogelijkheid schrijven.

## <a name="support-for-group-managed-service-accounts"></a>Ondersteuning voor de groep Managed Service Accounts

In sommige gevallen moet een taak die een gebruiker moet uitvoeren in een sessie JEA mogelijk toegang tot bronnen voorbij de lokale computer.
Wanneer een sessie JEA is geconfigureerd voor gebruik van een virtueel account, wordt elke poging tot deze bronnen afkomstig zijn van de identiteit van de lokale computer, niet de virtueel account of verbonden gebruiker weergegeven.
In TP5, hebben we ondersteuning voor het uitvoeren van JEA onder de context van een [groep beheerd serviceaccount](https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx) ingeschakeld, waardoor het veel eenvoudiger toegang tot netwerkbronnen met behulp van de identiteit van een domein.

Gebruik voor het configureren van een sessie JEA worden uitgevoerd onder een beheerd serviceaccount voor de volgende sleutel in uw bestand voor:

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> **Opmerking:** isolatie of beperkte mogelijkheden van virtuele accounts komen niet toestaan van beheerde serviceaccounts voor groepen.
> Elke gebruiker die verbinding maakt, wordt de hetzelfde gMSA-identiteit die mogelijk machtigingen van het gehele bedrijf delen.
> Wees voorzichtig bij het selecteren van een gMSA te gebruiken en altijd liever virtuele accounts die zijn beperkt tot de lokale machine indien mogelijk.

## <a name="conditional-access-policies"></a>Beleid voor voorwaardelijke toegang

JEA is een goede beperkt wat iemand kunt doen wanneer ze hebt aangesloten op een systeem voor het beheren, maar wat als u ook wilt beperken *wanneer* iemand JEA kunt gebruiken?
Configuratie-opties in de configuratiebestanden sessie (.pssc) waarin u kunt opgeven beveiligingsgroepen waartoe een gebruiker behoren moet om een sessie JEA stand te brengen, hebben we toegevoegd.
Dit is vooral handig als u een systeem net In tijd (Just in time) in uw omgeving hebt en maken van uw gebruikers hun bevoegdheden wilt voor de toegang tot een hoge bevoegdheden JEA-eindpunt.

De nieuwe *RequiredGroups* veld in het bestand voor kunt u de logica om na te gaan als een gebruiker verbinding met JEA maken kan opgeven.
Bestaat uit het opgeven van een hashtabel (eventueel geneste) die gebruikmaakt van de 'En' en 'Of' sleutels u uw regels samenstelt.
Hier volgen enkele voorbeelden van hoe u dit veld:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a>Vaste: Virtuele accounts worden nu ondersteund op Windows Server 2008 R2
WMF 5.1 bent u nu virtuele accounts gebruiken op Windows Server 2008 R2 inschakelen consistente configuraties en functie pariteit via Windows Server 2008 R2 - 2016.
Virtuele accounts blijven wordt niet ondersteund wanneer u JEA op Windows 7.
