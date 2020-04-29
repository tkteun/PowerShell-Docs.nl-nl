---
ms.date: 12/23/2019
keywords: Power shell, cmdlet
title: Met software-installaties werken
ms.openlocfilehash: f3023d8819d6cdcc9f55befcfedb21e6ff9d282c
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "76996130"
---
# <a name="working-with-software-installations"></a>Met software-installaties werken

Toepassingen die zijn ontworpen om Windows Installer te gebruiken, zijn toegankelijk via de **Win32_Product** klasse van WMI, maar niet alle toepassingen die tegenwoordig gebruiken, gebruiken de Windows Installer.
Toepassingen die alternatieve installatie routines gebruiken, worden doorgaans niet beheerd door de Windows Installer.
Specifieke technieken voor het werken met deze toepassingen zijn afhankelijk van de installatie software en beslissingen van de ontwikkelaar van de toepassing. Toepassingen die zijn geïnstalleerd door het kopiëren van de bestanden naar een map op de computer, kunnen bijvoorbeeld doorgaans niet worden beheerd met behulp van technieken die hier worden beschreven. U kunt deze toepassingen beheren als bestanden en mappen met behulp van de technieken die worden beschreven in [werken met bestanden en mappen](Working-with-Files-and-Folders.md).

> [!CAUTION]
> Er is geen query geoptimaliseerd voor de **Win32_Product** klasse. Query's die gebruikmaken van Joker filters, veroorzaken WMI de MSI-provider voor het inventariseren van alle geïnstalleerde producten en vervolgens de volledige lijst opeenvolgend parseren om het filter af te handelen. Dit initieert ook een consistentie controle van de geïnstalleerde pakketten, het verifiëren en herstellen van de installatie. De validatie is een traag proces en kan leiden tot fouten in de gebeurtenis Logboeken. Zoek [KB-artikel 974524](https://support.microsoft.com/help/974524)voor meer informatie.

## <a name="listing-windows-installer-applications"></a>Windows Installer-toepassingen weer geven

Als u de toepassingen wilt weer geven die zijn geïnstalleerd met de Windows Installer op een lokaal of extern systeem, gebruikt u de volgende eenvoudige WMI-query:

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)"
```

```Output
Name             Caption                   Vendor                    Version       IdentifyingNumber
----             -------                   ------                    -------       -----------------
Microsoft .NET … Microsoft .NET Core Runt… Microsoft Corporation     16.84.26919   {BEB59D04-C6DD-4926-AFE…
```

Als u alle eigenschappen van het **Win32_Product** -object wilt weer geven in de weer gave, gebruikt u de para meter **Eigenschappen** van de format `Format-List` -cmdlets, zoals de `*` cmdlet, met een waarde van (alle).

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.5 (x64)
Version               : 16.84.26919
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.5 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.5 (x64)
IdentifyingNumber     : {BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20181105
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}v16.84.26919\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\4f97a771.msi
PackageCache          : C:\WINDOWS\Installer\4f97a771.msi
PackageCode           : {9A271A10-039D-49EA-8D24-043D91B9F915}
PackageName           : dotnet-runtime-2.1.5-win-x64.msi
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

U kunt ook de `Get-CimInstance` **filter** parameter gebruiken om alleen Microsoft .net 2,0-runtime te selecteren. De waarde van de **filter** parameter maakt gebruik van de syntaxis WMI Query Language (WQL), geen Windows Power shell-syntaxis. Bijvoorbeeld:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property *
```

Als u alleen de eigenschappen wilt weer geven die u interesseren, gebruikt u de para meter **Property** van de Format-cmdlets om de gewenste eigenschappen weer te geven.

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.5 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\4f97a771.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a>Alle toepassingen weer geven die niet worden geïnstalleerd

Omdat de meeste standaard toepassingen een verwijderer bij Windows registreren, kunnen we deze lokaal samen met hen door vinden in het Windows-REGI ster. Er is geen gegarandeerde manier om elke toepassing op een systeem te vinden. Het is echter mogelijk om alle Program ma's te vinden met vermeldingen die worden weer gegeven in het **onderdeel Software** van de volgende register sleutel:

`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.

We kunnen deze sleutel onderzoeken om toepassingen te vinden. Om het weer geven van de verwijderings sleutel gemakkelijker te maken, kunnen we een Power Shell-station toewijzen aan deze register locatie:

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

We hebben nu een station met de naam ' uninstall: ' dat kan worden gebruikt om snel en eenvoudig te zoeken naar toepassings installaties. We kunnen het aantal geïnstalleerde toepassingen vinden door het aantal register sleutels in het verwijderen te tellen: Power Shell-station:

```powershell
(Get-ChildItem -Path Uninstall:).Count
```

```Output
459
```

We kunnen deze lijst met toepassingen verder doorzoeken door gebruik te maken van verschillende technieken, te `Get-ChildItem`beginnen met. Gebruik de volgende opdracht om een lijst met toepassingen op te `$UninstallableApplications` halen en deze op te slaan in de variabele:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

Als u de waarden van de Register vermeldingen in de register sleutels onder verwijderen wilt weer geven, gebruikt u de methode GetValue van de register sleutels. De waarde van de methode is de naam van de register vermelding.

Gebruik bijvoorbeeld de volgende opdracht om de weergave namen van de toepassingen in de uninstall-sleutel te vinden:

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Er is geen garantie dat deze waarden uniek zijn. In het volgende voor beeld worden twee geïnstalleerde items weer gegeven als ' Windows Media Encoder 9 Series ':

```powershell
$UninstallableApplications | Where-Object -FilterScript {
  $_.GetValue("DisplayName") -eq "Microsoft Silverlight"
}
```

```Output
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name                           Property
----                           --------
{89F4137D-6C26-4A84-BDB8-2E5A4 AuthorizedCDFPrefix :
BB71E00}                       Comments            :
                               Contact             :
                               DisplayVersion      : 5.1.50918.0
                               HelpLink            : https://go.microsoft.com/fwlink/?LinkID=91955
                               HelpTelephone       :
                               InstallDate         : 20190115
                               InstallLocation     : C:\Program Files\Microsoft Silverlight\
                               InstallSource       : c:\ef64c54526db9c34cd477c103e68a254\
                               ModifyPath          : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               NoModify            : 1
                               NoRepair            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 236432
                               UninstallString     : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 5
                               VersionMinor        : 1
                               WindowsInstaller    : 1
                               Version             : 84002534
                               Language            : 1033
                               DisplayName         : Microsoft Silverlight
                               sEstimatedSize2     : 79214
```

## <a name="installing-applications"></a>Toepassingen installeren

U kunt de klasse **Win32_Product** gebruiken om Windows Installer pakketten extern of lokaal te installeren.

> [!NOTE]
> Als u een toepassing wilt installeren, moet u Power shell starten met de optie als administrator uitvoeren.

Wanneer u extern installeert, gebruikt u een UNC-netwerkpad (Universal Naming Convention) om het pad naar het MSI-pakket op te geven, omdat het WMI-subsysteem geen Power shell-paden begrijpt. Als u bijvoorbeeld het pakket NewPackage. msi wilt installeren dat zich bevindt `\\AppServ\dsp` in de netwerk share op de externe computer PC01, typt u de volgende opdracht achter de Power shell-prompt:

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

Toepassingen die geen gebruik maken van Windows Installer technologie, kunnen toepassingsspecifieke methoden hebben voor automatische implementatie. Raadpleeg de documentatie bij de toepassing of Raadpleeg het ondersteunings systeem van de leverancier van de toepassing.

## <a name="removing-applications"></a>Toepassingen verwijderen

Het verwijderen van een Windows Installer-pakket met behulp van Power shell werkt op ongeveer dezelfde manier als het installeren van een pakket. Hier volgt een voor beeld van het selecteren van het pakket dat moet worden verwijderd op basis van de naam. in sommige gevallen kan het gemakkelijker worden gefilterd met de **nummer**:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

Het verwijderen van andere toepassingen is niet helemaal eenvoudig, zelfs wanneer deze lokaal worden uitgevoerd. U kunt de opdracht regel verwijderings teken reeksen voor deze toepassingen vinden door de eigenschap **UninstallString** uit te pakken.
Deze methode werkt voor Windows Installer toepassingen en voor oudere Program ma's die worden weer gegeven onder de sleutel Uninstall:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

U kunt de uitvoer filteren op de weergave naam, indien gewenst:

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Deze teken reeksen kunnen echter niet rechtstreeks worden gebruikt vanuit de Power shell-prompt zonder enige aanpassing.

## <a name="upgrading-windows-installer-applications"></a>Windows Installer-toepassingen bijwerken

Als u een toepassing wilt bijwerken, moet u de naam van de toepassing en het pad voor het upgrade pakket van de toepassing weten. Met deze informatie kunt u een toepassing bijwerken met één Power shell-opdracht:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
