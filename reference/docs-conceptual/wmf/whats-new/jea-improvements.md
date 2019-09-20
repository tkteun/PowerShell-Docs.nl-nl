---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Verbeteringen van Just Enough Administration (JEA)
ms.openlocfilehash: 847ae92a6225023bcd0ee3dfe7c7058bdc356836
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71145031"
---
# <a name="improvements-to-just-enough-administration-jea"></a>Verbeteringen van Just Enough Administration (JEA)

Net genoeg beheer is een nieuwe functie in WMF 5,0 waarmee beheer op basis van rollen via Power shell Remoting kan worden uitgevoerd. Hiermee wordt de bestaande beperkte eindpunt infrastructuur uitgebreid, omdat niet-beheerders specifieke opdrachten, scripts en uitvoer bare bestanden kunnen uitvoeren als beheerder. Zo kunt u het aantal volledige beheerders in uw omgeving verminderen en de beveiliging verbeteren.

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>Beperkte bestands kopie naar/van JEA-eind punten

U kunt bestanden nu extern kopiëren naar/van een JEA-eind punt en er zeker van zijn dat de gebruiker die de verbinding maakt, alleen *een* bestand op uw systeem kan kopiëren. Dit is mogelijk door uw PSSC-bestand te configureren om een gebruikers station te koppelen voor het verbinden van gebruikers. Het gebruikers station is een nieuwe PSDrive die uniek is voor elke gebruiker die verbinding maakt en die zich in verschillende sessies bevindt. Wanneer `Copy-Item` wordt gebruikt om bestanden te kopiëren naar of van een JEA-sessie, is deze beperkt om alleen toegang tot het gebruikers station toe te staan. Pogingen om bestanden naar andere PSDrive te kopiëren, mislukken.

Als u het gebruikers station in het configuratie bestand van uw JEA-sessie wilt instellen, gebruikt u de volgende nieuwe velden:

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

De map die een back-up maakt van het gebruikers station wordt gemaakt op`$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`

Als u het gebruikers station wilt gebruiken en bestanden wilt kopiëren naar/van een JEA-eind punt dat is geconfigureerd om het gebruikers `-ToSession` station `-FromSession` zichtbaar te `Copy-Item`maken, gebruikt u de para meters en op.

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

U kunt vervolgens aangepaste functies schrijven om de gegevens te verwerken die zijn opgeslagen in het gebruikers station en deze beschikbaar te maken voor gebruikers in uw functie-functionaliteits bestand.

## <a name="support-for-group-managed-service-accounts"></a>Ondersteuning voor door groepen beheerde service accounts

In sommige gevallen moet een taak die een gebruiker moet uitvoeren in een JEA-sessie mogelijk toegang hebben tot bronnen buiten de lokale machine. Wanneer een JEA-sessie is geconfigureerd voor het gebruik van een virtueel account, zal elke poging om dergelijke bronnen te bereiken, afkomstig zijn van de identiteit van de lokale computer, niet van het virtuele account of de verbonden gebruiker. In TP5 hebben we ondersteuning ingeschakeld voor het uitvoeren van JEA in de context van een door een [groep beheerd service account](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), waardoor het veel eenvoudiger is om toegang te krijgen tot netwerk bronnen met behulp van een domein identiteit.

Als u een JEA-sessie wilt configureren om te worden uitgevoerd onder een gMSA-account, gebruikt u de volgende nieuwe sleutel in uw PSSC-bestand:

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> Door groepen beheerde service accounts bieden geen isolatie of beperkt bereik van virtuele accounts.
> Elke gebruiker die verbinding maakt, deelt dezelfde gMSA-identiteit, die mogelijk machtigingen heeft voor uw hele onderneming. Wees voorzichtig bij het selecteren van een gMSA en gebruik altijd de voor keur aan virtuele accounts die worden beperkt tot de lokale machine wanneer dat mogelijk is.

## <a name="conditional-access-policies"></a>Beleid voor voorwaardelijke toegang

JEA is handig om te beperken wat iemand kan doen wanneer ze zijn verbonden met een systeem om het te beheren, maar wat als u ook wilt beperken *Wanneer* iemand JEA kan gebruiken? Er zijn configuratie opties toegevoegd aan de sessie configuratie bestanden (. pssc) waarmee u beveiligings groepen kunt opgeven waarvoor een gebruiker moet behoren om een JEA-sessie tot stand te brengen. Dit is met name handig als u een just-in-time-systeem (JIT) in uw omgeving hebt en u wilt dat uw gebruikers hun bevoegdheden kunnen verhogen voordat ze toegang krijgen tot een JEA-eind punt met hoge privileges.

In het nieuwe veld *RequiredGroups* in het PSSC-bestand kunt u de logica opgeven om te bepalen of een gebruiker verbinding kan maken met jea. Het bestaat uit het opgeven van een hashtabel (optioneel genest) die gebruikmaakt van de-en-of-sleutels om uw regels te maken. Hier volgen enkele voor beelden van het gebruik van dit veld:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a>Vaste Virtuele accounts worden nu ondersteund op Windows Server 2008 R2

In WMF 5,1 kunt u nu virtuele accounts gebruiken op Windows Server 2008 R2, waardoor consistente configuraties en functie pariteit in Windows Server 2008 R2-2016 wordt ingeschakeld. Virtuele accounts blijven niet-ondersteund wanneer JEA wordt gebruikt in Windows 7.