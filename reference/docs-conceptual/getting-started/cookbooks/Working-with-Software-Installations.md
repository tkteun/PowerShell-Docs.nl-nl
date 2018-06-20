---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met software-installaties werken
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: bb97ad37c4295351c0fc2e3c6e1209c8dd673f06
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952814"
---
# <a name="working-with-software-installations"></a>Met software-installaties werken

Toepassingen die zijn ontworpen voor gebruik van Windows Installer is toegankelijk via WMI van **Win32_Product** klasse, maar niet alle toepassingen in gebruik vandaag gebruik van Windows Installer. Omdat Windows Installer een groot aantal standaard technieken biedt voor het werken met installeerbare toepassingen, gaan we in voornamelijk op deze toepassingen. Toepassingen die gebruikmaken van routines alternatieve instellen zullen in het algemeen niet worden beheerd door de Windows Installer. Specifieke technieken voor het werken met deze toepassingen, is afhankelijk van de installer-software en de beslissingen van de ontwikkelaar van de toepassing.

> [!NOTE]
> De door toepassingsbestanden te kopiëren naar de computer doorgaans geïnstalleerde toepassingen kunnen niet worden beheerd met behulp van technieken die worden besproken hier. U kunt deze toepassingen als bestanden en mappen beheren met behulp van de technieken beschreven in de sectie 'Werken met bestanden en mappen'.

### <a name="listing-windows-installer-applications"></a>Windows Installer-toepassingen weergeven

Als de toepassingen zijn geïnstalleerd met Windows Installer op een lokale of externe systeem weergeven, gebruikt u de volgende eenvoudige WMI-query:

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

Als u wilt weergeven alle eigenschappen van het object Win32_Product naar de weergave, gebruikt u de eigenschappen-parameter van de opmaak cmdlets, zoals de cmdlet lijst indelen met een waarde van \* (alle).

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

Of u kunt de **Get-WmiObject Filter** parameter alleen Microsoft .NET Framework 2.0 te selecteren. Omdat het filter dat wordt gebruikt in deze opdracht een WMI-filter is, gebruikt de syntaxis van de WMI Query Language (WQL), niet voor Windows PowerShell-syntaxis. In plaats daarvan:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

Houd er rekening mee dat WQL-query's vaak gebruik tekens, zoals spaties of gelijk tekens, die een speciale betekenis in Windows PowerShell hebben. Daarom is het verstandig om te altijd de waarde van de parameter Filter plaats tussen aanhalingstekens. U kunt ook de Windows PowerShell-escape-teken, een backtick (\`), hoewel deze mogelijk niet betere leesbaarheid. De volgende opdracht komt overeen met de vorige opdracht en dezelfde resultaten retourneert, maar de backtick gebruikt als escapeteken voor speciale tekens, in plaats van de hele filtertekenreeks aan te geven.

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

U kunt alleen de eigenschappen die u interesseren gebruiken de parameter Property van de opmaak-cmdlets voor een lijst met de gewenste eigenschappen.

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

Ten slotte vinden alleen de namen van de geïnstalleerde toepassingen, een eenvoudige **indeling hele** instructie vereenvoudigt de uitvoer:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

Hoewel we nu verschillende manieren om te kijken naar toepassingen die het Windows-installatieprogramma voor installatie gebruikt hebben, hebben we niet beschouwd als andere toepassingen. Omdat hun verwijderprogramma meest standaardtoepassingen bij Windows registreren, kunnen we werken met die lokaal door ze te zoeken in het Windows-register.

### <a name="listing-all-uninstallable-applications"></a>Alle kan worden verwijderd toepassingen weergeven

Hoewel er geen gegarandeerde manier om te zoeken naar elke toepassing die op een systeem, is het mogelijk om alle programma's met aanbiedingen weergegeven in het dialoogvenster een programma verwijderen of vinden. Toevoegen of software vindt deze toepassingen in de volgende registersleutel:

**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\verwijderen**.

We kunnen deze sleutel om te zoeken naar toepassingen onderzoeken. Om het gemakkelijker om weer te geven van de sleutel verwijderen, kunnen we een Windows PowerShell-station toewijzen aan deze registerlocatie:

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> De **HKLM:** station is toegewezen aan de hoofdmap van **HKEY_LOCAL_MACHINE**, zodat we dat station in het pad naar de sleutel verwijderen gebruikt. In plaats van **HKLM:** we kan het registerpad hebt opgegeven met behulp van **HKLM** of **HKEY_LOCAL_MACHINE**. Het voordeel van een bestaand register-station is dat we invullen van de tabbladen gebruiken kunt om in te vullen de namen van sleutels, zodat we niet hoeft te geven.

We hebben nu een station met de naam 'Verwijderen' die kan worden gebruikt om snel en gemakkelijk zoekt installaties van toepassingen. We kunnen het aantal geïnstalleerde toepassingen zoeken door het aantal registersleutels in het verwijderen te tellen: Windows PowerShell-station:

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

We kunnen deze lijst van toepassingen meer zoeken met behulp van tal van technieken vanaf **Get-ChildItem**. Een lijst met toepassingen ophalen en opslaan in de **$UninstallableApplications** variabele, gebruikt u de volgende opdracht:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> We langdurige variabele hier een naam voor de duidelijkheid gebruiken. Er is geen reden lang namen gebruiken in het werkelijke gebruik. Hoewel u tabblad voltooiing voor namen van variabelen gebruiken kunt, kunt u ook 1-2 teken namen voor snelheid. Langer, beschrijvende namen zijn handig als u code opnieuw kunnen worden gebruikt ontwikkelt.

Gebruik de methode GetValue van de registersleutels zodat de waarden van de registervermeldingen in de registersleutels onder verwijderen. De waarde van de methode is de naam van het register-item.

Bijvoorbeeld, om de namen weergegeven van toepassingen in de sleutel verwijderen, gebruik de volgende opdracht:

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

### <a name="installing-applications"></a>Installatie van toepassingen

U kunt de **Win32_Product** klasse voor het installeren van Windows Installer-pakketten extern of lokaal.

> [!NOTE]
> Op Windows Vista, Windows Server 2008 en nieuwere versies van Windows, een toepassing te installeren, moet u beginnen Windows PowerShell met de optie 'Als administrator uitvoeren'.

Bij het op afstand installeren via een netwerkpad Universal Naming Convention (UNC) opgeven het pad naar het MSI-pakket, omdat het WMI-subsysteem niet paden met Windows PowerShell begrijpt. Bijvoorbeeld, zich in de netwerkshare voor het installeren van het pakket NewPackage.msi \\ \\AppServ\\dsp op de externe computer PC01, typ de volgende opdracht achter de Windows PowerShell-prompt:

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

Toepassingen die geen van Windows Installer-technologie gebruikmaken misschien toepassingsspecifieke methoden beschikbaar voor automatische implementatie. Raadpleeg de documentatie voor de toepassing om te bepalen of er een methode voor het automatiseren van de implementatie is, of neem contact op ondersteuningssysteem van de leverancier van de toepassing. In sommige gevallen, zelfs als de toepassing voor het automatiseren van de installatie is niet specifiek ontwerp-leverancier van de toepassing de fabrikant van de software installer mogelijk bepaalde technieken voor automatisering.

### <a name="removing-applications"></a>Toepassingen verwijderen

Verwijderen van een Windows Installer-pakket met Windows PowerShell werkt op ongeveer dezelfde manier als een pakket installeert. Hier volgt een voorbeeld waarin selecteert het pakket te verwijderen op basis van de naam; in sommige gevallen kan zijn gemakkelijker te filteren met de **id-nummer**:

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

Verwijderen van andere toepassingen is niet zo eenvoudig, zelfs wanneer lokaal wordt uitgevoerd. We kunnen de opdrachtregel verwijderen tekenreeksen vinden voor deze toepassingen door uit te pakken de **UninstallString** eigenschap. Deze methode werkt voor Windows Installer-toepassingen en oudere programma's die wordt weergegeven onder de sleutel verwijderen:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

U kunt de uitvoer als u dit wilt filteren op de weergavenaam:

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Maar deze tekenreeksen mogelijk niet direct toegankelijk is vanaf de Windows PowerShell-prompt zonder enige aanpassing.

### <a name="upgrading-windows-installer-applications"></a>Een upgrade van Windows Installer-toepassingen

Om een toepassing een upgrade uitvoert, moet u de naam van de toepassing en het pad op het updatepakket van een toepassing weet. Deze informatie kunt u een toepassing met een enkel Windows PowerShell-opdracht upgraden:

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```