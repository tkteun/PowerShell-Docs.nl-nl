---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met software-installaties werken
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: 9369e3c5ac670895cd4fbd3ebc895c50efd02051
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293218"
---
# <a name="working-with-software-installations"></a>Met software-installaties werken

Toepassingen die zijn ontworpen voor het gebruik van Windows Installer is toegankelijk via WMI van **Win32_Product** klasse, maar niet alle toepassingen in gebruik vandaag nog gebruik van het Windows-installatieprogramma. Omdat het installatieprogramma voor Windows de breedste scala aan standard technieken biedt voor het werken met installeerbare toepassingen, we richten ons voornamelijk aan deze toepassingen. Toepassingen die gebruikmaken van routines alternatieve instellen in het algemeen niet beheerd door de Windows-installatieservice. Specifieke technieken voor het werken met deze toepassingen, is afhankelijk van de installer-software en de beslissingen die worden genomen door de ontwikkelaar van de toepassing.

> [!NOTE]
> Toepassingen die zijn geïnstalleerd door de toepassingsbestanden zijn gekopieerd naar de computer meestal kunnen niet worden beheerd met behulp van technieken die worden besproken hier. U kunt deze toepassingen als uitvoerbare bestanden en mappen beheren met behulp van de technieken beschreven in de sectie 'Werken met bestanden en mappen'.

## <a name="listing-windows-installer-applications"></a>Windows Installer-toepassingen weergeven

Als u de toepassingen zijn geïnstalleerd met de Windows Installer op een lokale of externe systeem, gebruik de volgende eenvoudige WMI-query:

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

Wilt weergeven alle van de eigenschappen van het object Win32_Product bij het weergeven, gebruikt u de parameter eigenschappen van de opmaak-cmdlets, zoals de cmdlet lijst met een waarde van \* (alle).

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *

Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

Of u kunt de **Get-WmiObject Filter** parameter selecteren alleen Microsoft .NET Framework 2.0. Omdat het filter gebruikt in deze opdracht een WMI-filter is, wordt de syntaxis van de WMI Query Language (WQL), niet Windows PowerShell-syntaxis. In plaats daarvan:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

Houd er rekening mee dat WQL-query's regelmatig gebruik tekens, zoals spaties of gelijktekens, waarvoor een speciale betekenis in Windows PowerShell. Daarom is het verstandig om te altijd de waarde van de filterparameter tussen aanhalingstekens plaatsen. U kunt ook de Windows PowerShell-escape-teken, een backtick (\`), hoewel de leesbaarheid niet kan worden verbeterd. De volgende opdracht is gelijk aan de vorige opdracht en retourneert hetzelfde resultaat, maar de backtick gebruikt als escapeteken voor speciale tekens bevatten, in plaats van de aanhalingstekens voor de hele filtertekenreeks.

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

Als u alleen de eigenschappen die u interesseren, door de parameter eigenschap van de opmaak-cmdlets te gebruiken om de gewenste eigenschappen weer te geven.

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

Ten slotte, om te zoeken naar alleen de namen van de geïnstalleerde toepassingen, een eenvoudige **indeling hele** instructie vereenvoudigt de uitvoer:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

Hoewel we nu verschillende manieren om te kijken naar toepassingen die het Windows-installatieprogramma voor de installatie gebruikt hebben, hebben we niet beschouwd als andere toepassingen. Omdat de meeste standaard toepassingen registreren hun verwijderprogramma bij Windows, die we kunnen werken met die lokaal door ze te vinden in het Windows-register.

## <a name="listing-all-uninstallable-applications"></a>Lijst van alle toepassingen die kan worden verwijderd

Hoewel er geen gegarandeerde manier om te vinden van elke toepassing op een systeem is, is het mogelijk om te zoeken van alle programma's met aanbiedingen weergegeven in het dialoogvenster toevoegen of verwijderen van programma's. Toevoegen of verwijderen van programma's vindt deze toepassingen in de volgende registersleutel:

**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.

We kunnen ook naar de deze sleutel om te zoeken naar toepassingen. Als u wilt maken het gemakkelijker om de sleutel verwijderen weer te geven, kunnen we een Windows PowerShell-station worden toegewezen aan deze registerlocatie:

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> De **HKLM:** stationsaanduiding is toegewezen aan de hoofdmap van **HKEY_LOCAL_MACHINE**, zodat we dat station in het pad naar de sleutel verwijderen gebruikt. In plaats van **HKLM:** we kan hebt opgegeven het registerpad met behulp van **HKLM** of **HKEY_LOCAL_MACHINE**. Het voordeel van het gebruik van een bestaand register-station is dat tabvoltooiing kunnen worden gebruikt om in te vullen in de namen van de sleutels, zodat we niet zelf hoeft te geven.

We hebben nu een station met de naam 'Verwijderen', die kan worden gebruikt om snel en gemakkelijk zoeken voor installaties van toepassingen. Er vindt het aantal geïnstalleerde toepassingen door het aantal registersleutels in de verwijdering te tellen: Windows PowerShell-station:

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

We kunnen deze lijst met toepassingen verder zoeken met behulp van verschillende technieken, beginnen met **Get-ChildItem**. Voor het ophalen van een lijst met toepassingen en slaat u ze in de **$UninstallableApplications** variabele, gebruikt u de volgende opdracht:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> We gebruiken een langdurige variabelenaam voor de duidelijkheid. Werkelijke gebruikt is er geen reden lange namen te gebruiken. Hoewel u tabvoltooiing voor namen van variabelen gebruiken kunt, kunt u de namen van 1-2-teken voor snelheid ook gebruiken. Langer, beschrijvende namen zijn handig als u code voor hergebruik ontwikkelt.

Als de waarden van de registervermeldingen in de registersleutels onder verwijderen weergeven, gebruikt u de GetValue-methode van de registersleutels. De waarde van de methode is de naam van het register-item.

Bijvoorbeeld, als u zoekt de weergavenamen van toepassingen in de sleutel verwijderen, gebruik de volgende opdracht:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Er is geen garantie dat deze waarden uniek zijn. In het volgende voorbeeld worden twee geïnstalleerde items weergegeven als 'Windows Media Encoder 9 Series':

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

## <a name="installing-applications"></a>Installeren van toepassingen

U kunt de **Win32_Product** klasse voor het installeren van Windows Installer-pakketten, extern of lokaal.

> [!NOTE]
> Op Windows Vista, Windows Server 2008 en latere versies van Windows, voor het installeren van een toepassing, moet u beginnen Windows PowerShell met de optie "Uitvoeren als administrator".

Bij de installatie op afstand, moet u een netwerkpad Universal Naming Convention (UNC) gebruiken om op te geven van het pad naar het MSI-pakket, omdat het WMI-subsysteem heeft niet informatie over Windows PowerShell-paden. Bijvoorbeeld, zich in de netwerkshare voor het installeren van het pakket NewPackage.msi \\ \\AppServ\\dsp op de externe computer PC01, typt u de volgende opdracht achter de Windows PowerShell-prompt:

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

Toepassingen die geen gebruik maken van Windows Installer-technologie hebben toepassingsspecifieke methoden beschikbaar voor automatische implementatie. Raadpleeg de documentatie voor de toepassing om te bepalen of er een methode voor het automatiseren van de implementatie is, of neem contact op ondersteuning van system van de leverancier van de toepassing. In sommige gevallen, zelfs als de leverancier van de toepassing is niet specifiek de toepassing ontwerpen voor installatie-automatisering, de fabrikant van de software installer mogelijk bepaalde technieken voor automation.

## <a name="removing-applications"></a>Toepassingen verwijderen

Verwijderen van een Windows Installer-pakket met behulp van Windows PowerShell werkt op ongeveer dezelfde manier als een pakket installeert. Hier volgt een voorbeeld waarin selecteert het pakket te verwijderen op basis van de naam; in sommige gevallen kan het eenvoudiger om te filteren met zijn de **id-nummer**:

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

Verwijderen van andere toepassingen is niet zo eenvoudig, zelfs wanneer lokaal uitgevoerd. We kunnen de opdrachtregel verwijderen tekenreeksen voor deze toepassingen vinden door te extraheren de **UninstallString** eigenschap. Deze methode werkt voor Windows Installer-toepassingen en oudere programma's die wordt weergegeven onder de sleutel verwijderen:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

U kunt desgewenst de uitvoer filteren op de weergavenaam:

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Deze tekenreeksen kunnen echter niet worden rechtstreeks vanuit de Windows PowerShell-prompt zonder enige wijziging gebruikt.

## <a name="upgrading-windows-installer-applications"></a>Upgraden van Windows Installer-toepassingen

Als u een toepassing bijwerken, moet u de naam van de toepassing en het pad kennen op het updatepakket van toepassing. Met deze informatie kunt u een toepassing met een enkel Windows PowerShell-opdracht bijwerken:

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```