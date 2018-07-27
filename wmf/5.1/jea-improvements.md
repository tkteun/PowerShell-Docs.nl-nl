---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
contributor: ryanpu
title: Verbeteringen in Just Enough Administration (JEA)
ms.openlocfilehash: 66cbacb78f8a365e9c8556c7c56b3c3525de7395
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267862"
---
# <a name="improvements-to-just-enough-administration-jea"></a>Verbeteringen in Just Enough Administration (JEA)

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>Beperkte bestanden kopiëren naar JEA-eindpunten

Kunt u nu op afstand bestanden te kopiëren/in een JEA-eindpunt en rest kan worden gegarandeerd dat de gebruiker die de verbinding alleen kan niet kopiëren *eventuele* bestand op uw systeem. Dit is mogelijk door het configureren van uw voor-bestand voor het koppelen van een schijf van de gebruiker om verbinding te maken van gebruikers. De schijf van de gebruiker is een nieuwe PSDrive die uniek is voor elke gebruiker die verbinding maakt en clusterverbinding blijven behouden tussen sessies. Wanneer `Copy-Item` wordt gebruikt om bestanden te kopiëren naar of van een JEA-sessie, is deze beperkt tot alleen toegang tot de schijf van de gebruiker toestaan. Pogingen om bestanden te kopiëren naar een andere PSDrive mislukken.

Om in te stellen de schijf van de gebruiker in uw configuratiebestand van de JEA-sessie, gebruikt u de volgende nieuwe velden:

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

De map die de schijf van de gebruiker een back-up wordt gemaakt op `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`

Als u wilt gebruikmaken van de schijf van de gebruiker en kopiëren van bestanden naar/van een JEA-eindpunt dat is geconfigureerd als de schijf van de gebruiker beschikbaar wilt maken, gebruikt u de `-ToSession` en `-FromSession` parameters op `Copy-Item`.

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine.
# You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

U kunt vervolgens aangepaste functies voor het verwerken van de gegevens die zijn opgeslagen in de schijf van de gebruiker en die beschikbaar maken voor gebruikers in uw rol mogelijkheid-bestand schrijven.

## <a name="support-for-group-managed-service-accounts"></a>Ondersteuning voor Group Managed Service Accounts

In sommige gevallen kan een taak die een gebruiker nodig heeft om uit te voeren in een JEA-sessie moet toegang tot bronnen voorbij de lokale computer. Wanneer een JEA-sessie is geconfigureerd voor het gebruik van een virtueel account, wordt elke poging tot deze bronnen afkomstig zijn van de identiteit van de lokale computer, niet de virtuele-account of verbonden gebruiker weergegeven. TP5, is voorzien van ondersteuning voor het uitvoeren van JEA in de context van een [groep beheerd serviceaccount](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), waardoor het veel eenvoudiger toegang krijgen tot netwerkbronnen met behulp van de identiteit van een domein.

Voor het configureren van een JEA-sessie moet worden uitgevoerd in een gMSA-account, gebruikt u de volgende sleutel in het bestand voor:

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> Groep beheerde serviceaccounts doen niet zomaar de isolatie- of beperkte mogelijkheden van virtuele accounts.
> Elke gebruiker die verbinding maakt, wordt de hetzelfde gMSA-id, die mogelijk machtigingen in uw gehele organisatie delen. Wees voorzichtig bij het selecteren van een gMSA gebruiken en altijd de voorkeur geeft aan virtuele accounts die zijn beperkt tot de lokale computer, indien mogelijk.

## <a name="conditional-access-policies"></a>Beleid voor voorwaardelijke toegang

JEA is erg handig bij het beperken van iemand kunt doen wanneer ze hebt verbonden met een systeem te beheren, maar wat als u ook wilt beperken *wanneer* iemand kunt JEA gebruiken? Configuratie-opties in de sessie-configuratiebestanden (.pssc) waarin u kunt opgeven-beveiligingsgroepen waartoe een gebruiker behoren moet om een JEA-sessie tot stand brengen, hebben we toegevoegd. Dit kan vooral nuttig zijn als u een systeem alleen In tijd (JIT) in uw omgeving hebt en maken van uw gebruikers wilt voordat u toegang tot een JEA-eindpunt voor veel bevoegdheden verhogen.

De nieuwe *RequiredGroups* veld in het bestand voor kunt u de logica om na te gaan als een gebruiker verbinding met JEA maken kan opgeven. Er bestaat voor het opgeven van een hash-tabel (eventueel geneste) die gebruikmaakt van de 'En' en 'Of' sleutels te maken van uw regels. Hier volgen enkele voorbeelden van hoe u dit veld:

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

In WMF 5.1 bent u nu te kunnen gebruikmaken van virtuele accounts in Windows Server 2008 R2, waardoor consistente configuraties en functiepariteit voor Windows Server 2008 R2 - 2016. Virtuele accounts blijven wordt niet ondersteund bij het gebruik van JEA op Windows 7.