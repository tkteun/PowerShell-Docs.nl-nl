---
ms.date: 06/03/2019
keywords: PowerShell-cmdlet
title: Met software-installaties werken
ms.openlocfilehash: 6d2111a332f0e8c1b545186d3d950e936aed1834
ms.sourcegitcommit: 4ec9e10647b752cc62b1eabb897ada3dc03c93eb
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830291"
---
# <a name="working-with-software-installations"></a>Met software-installaties werken

Toepassingen die zijn ontworpen voor het gebruik van Windows Installer is toegankelijk via WMI van **Win32_Product** klasse, maar niet alle toepassingen in gebruik vandaag nog gebruik van het Windows-installatieprogramma.
Toepassingen die gebruikmaken van alternatieve installatieprocedure meestal niet worden beheerd door de Windows-installatieservice.
Specifieke technieken voor het werken met deze toepassingen, is afhankelijk van de installer-software en beslissingen door de ontwikkelaar van de toepassing. Bijvoorbeeld kunnen niet toepassingen zijn geïnstalleerd door de bestanden zijn gekopieerd naar een map op de computer meestal worden beheerd met behulp van technieken die worden besproken hier. U kunt beheren van deze toepassingen als bestanden en mappen met behulp van de technieken beschreven in [werken met bestanden en mappen](Working-with-Files-and-Folders.md).

> [!CAUTION]
> De **Win32_Product** klasse is geen query geoptimaliseerd. Query's die gebruikmaken van jokertekens filters ertoe leiden dat WMI om met het MSI-provider te inventariseren van alle geïnstalleerde producten en parseren van de volledige lijst sequentieel worden verwerkt voor het afhandelen van het filter. Hiermee initieert ook een consistentiecontrole uit van pakketten geïnstalleerd, te controleren en herstellen van de installatie. De validatie is een trage proces en kan leiden tot fouten in de gebeurtenislogboeken. Voor meer informatie zoeken [KB-artikel 974524](https://support.microsoft.com/help/974524).

## <a name="listing-windows-installer-applications"></a>Windows Installer-toepassingen weergeven

Als u de toepassingen zijn geïnstalleerd met de Windows Installer op een lokale of externe systeem, gebruik de volgende eenvoudige WMI-query:

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)"
```

```Output
Name               Caption                     Vendor                 Version      IdentifyingNumber
----               -------                     ------                 -------      -----------------
Microsoft .NET ... Microsoft .NET Core Runt... Microsoft Corporation  16.72.26629  {ACC73072-9AD5-416C-94B...
```

Om weer te geven van alle eigenschappen van de **Win32_Product** object aan de weergave, gebruik de **eigenschappen** parameter van de opmaak cmdlets, zoals de `Format-List` cmdlet, met een waarde van `*` (alle).

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.2 (x64)
Version               : 16.72.26629
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.2 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.2 (x64)
IdentifyingNumber     : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20180816
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\414c96e.msi
PackageCache          : C:\WINDOWS\Installer\414c96e.msi
PackageCode           : {D20AC783-1EC5-4A58-9277-F452F5EB9AD9}
PackageName           : dotnet-runtime-2.1.2-win-x64.msi
ProductID             :
RegCompany            :
RegOwner              :
Transforms            :
URLInfoAbout          :
URLUpdateInfo         :
WordCount             : 0
PSComputerName        :
CimClass              : root/cimv2:Win32_Product
CimInstanceProperties : {Caption, Description, IdentifyingNumber, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

Of u kunt de `Get-CimInstance` **Filter** parameter selecteren alleen Microsoft .NET Framework 2.0. De waarde van de **Filter** parameter maakt gebruik van WMI Query Language (WQL)-syntaxis, niet Windows PowerShell-syntaxis. Bijvoorbeeld:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property *
```

U kunt alleen de eigenschappen die u interesseren gebruiken de **eigenschap** parameter van de opmaak cmdlets om de gewenste eigenschappen weer te geven.

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.2 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\414c96e.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a>Lijst van alle toepassingen die kan worden verwijderd

Omdat een verwijderprogramma meest standaard toepassingen bij Windows registreren, die we kunnen werken met die lokaal door ze te vinden in het Windows-register. Er is geen gegarandeerde manier om te vinden van elke toepassing op een systeem. Het is echter mogelijk om te zoeken van alle programma's met aanbiedingen weergegeven in **software**. **Toevoegen of verwijderen van programma's** zoekt naar deze toepassingen in de volgende registersleutel:

`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.

We kunt deze sleutel om te zoeken naar toepassingen bekijken. Als u wilt maken het gemakkelijker om de sleutel verwijderen weer te geven, kunnen we een PowerShell-station worden toegewezen aan deze registerlocatie:

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```
We hebben nu een station met de naam "verwijderen: ' kunnen worden gebruikt voor een snel en gemakkelijk zoeken voor installaties van toepassingen. Er vindt het aantal geïnstalleerde toepassingen door het aantal registersleutels in de verwijdering te tellen: PowerShell-station:

```
(Get-ChildItem -Path Uninstall:).Count
459
```

We kunnen deze lijst met toepassingen verder zoeken met behulp van verschillende technieken, beginnen met **Get-ChildItem**. Voor het ophalen van een lijst met toepassingen en slaat u ze in de **$UninstallableApplications** variabele, gebruikt u de volgende opdracht:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

Als de waarden van de registervermeldingen in de registersleutels onder verwijderen weergeven, gebruikt u de GetValue-methode van de registersleutels. De waarde van de methode is de naam van het register-item.

Bijvoorbeeld, als u zoekt de weergavenamen van toepassingen in de sleutel verwijderen, gebruik de volgende opdracht:

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Er is geen garantie dat deze waarden uniek zijn. In het volgende voorbeeld worden twee geïnstalleerde items weergegeven als 'Windows Media Encoder 9 Series':

```powershell
$UninstallableApplications | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}
```

```Output
Name                           Property
----                           --------
{ACC73072-9AD5-416C-94BF-D82DD AuthorizedCDFPrefix :
CEA0F1B}                       Comments            :
                               Contact             :
                               DisplayVersion      : 16.72.26629
                               HelpLink            :
                               HelpTelephone       :
                               InstallDate         : 20180816
                               InstallLocation     :
                               InstallSource       : C:\ProgramData\Package
                               Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
                               ModifyPath          : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               NoModify            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 67156
                               SystemComponent     : 1
                               UninstallString     : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 16
                               VersionMinor        : 72
                               WindowsInstaller    : 1
                               Version             : 273180677
                               Language            : 1033
                               DisplayName         : Microsoft .NET Core Runtime - 2.1.2 (x64)
```

## <a name="installing-applications"></a>Installeren van toepassingen

U kunt de **Win32_Product** klasse voor het installeren van Windows Installer-pakketten, extern of lokaal.

> [!NOTE]
> Een toepassing te installeren, moet u PowerShell starten met de optie 'Als administrator uitvoeren'.

Bij de installatie op afstand, moet u een netwerkpad Universal Naming Convention (UNC) gebruiken om op te geven van het pad naar het MSI-pakket, omdat het WMI-subsysteem heeft niet informatie over PowerShell paden. Bijvoorbeeld, voor het installeren van het pakket NewPackage.msi zich in de netwerkshare `\\AppServ\dsp` op de externe computer PC01, typt u de volgende opdracht achter de PowerShell-prompt:

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

Toepassingen die geen gebruik maken van Windows Installer-technologie hebben toepassingsspecifieke methoden voor automatische implementatie. Raadpleeg de documentatie voor de toepassing of neem contact op ondersteuning van system van de leverancier van de toepassing.

## <a name="removing-applications"></a>Toepassingen verwijderen

Verwijderen van een Windows Installer-pakket met behulp van PowerShell werkt op ongeveer dezelfde manier als een pakket installeert. Hier volgt een voorbeeld waarin selecteert het pakket te verwijderen op basis van de naam; in sommige gevallen kan het eenvoudiger om te filteren met zijn de **id-nummer**:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

Verwijderen van andere toepassingen is niet zo eenvoudig, zelfs wanneer lokaal uitgevoerd. We kunnen de opdrachtregel verwijderen tekenreeksen voor deze toepassingen vinden door te extraheren de **UninstallString** eigenschap.
Deze methode werkt voor Windows Installer-toepassingen en oudere programma's die wordt weergegeven onder de sleutel verwijderen:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

U kunt desgewenst de uitvoer filteren op de weergavenaam:

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Deze tekenreeksen kunnen echter niet worden rechtstreeks vanuit de PowerShell-prompt zonder enige wijziging gebruikt.

## <a name="upgrading-windows-installer-applications"></a>Upgraden van Windows Installer-toepassingen

Als u een toepassing bijwerken, moet u de naam van de toepassing en het pad kennen op het updatepakket van toepassing. Met deze informatie kunt u een toepassing met slechts één PowerShell-opdracht bijwerken:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
