---
ms.date: 12/23/2019
keywords: Power shell, cmdlet
title: Met software-installaties werken
ms.openlocfilehash: d164064418ad7a0209166c81a7c3cc32a9db300a
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737148"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="f48b2-103">Met software-installaties werken</span><span class="sxs-lookup"><span data-stu-id="f48b2-103">Working with Software Installations</span></span>

<span data-ttu-id="f48b2-104">Toepassingen die zijn ontworpen om Windows Installer te gebruiken, zijn toegankelijk via de **Win32_Product** klasse van WMI, maar niet alle toepassingen die tegenwoordig gebruiken, gebruiken de Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="f48b2-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span>
<span data-ttu-id="f48b2-105">Toepassingen die alternatieve installatie routines gebruiken, worden doorgaans niet beheerd door de Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="f48b2-105">Applications that use alternate setup routines are not usually managed by the Windows Installer.</span></span>
<span data-ttu-id="f48b2-106">Specifieke technieken voor het werken met deze toepassingen zijn afhankelijk van de installatie software en beslissingen van de ontwikkelaar van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="f48b2-106">Specific techniques for working with those applications depends on the installer software and decisions made by the application developer.</span></span> <span data-ttu-id="f48b2-107">Toepassingen die zijn geïnstalleerd door het kopiëren van de bestanden naar een map op de computer, kunnen bijvoorbeeld doorgaans niet worden beheerd met behulp van technieken die hier worden beschreven.</span><span class="sxs-lookup"><span data-stu-id="f48b2-107">For example, applications installed by copying the files to a folder on the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="f48b2-108">U kunt deze toepassingen beheren als bestanden en mappen met behulp van de technieken die worden beschreven in [werken met bestanden en mappen](Working-with-Files-and-Folders.md).</span><span class="sxs-lookup"><span data-stu-id="f48b2-108">You can manage these applications as files and folders by using the techniques discussed in [Working With Files and Folders](Working-with-Files-and-Folders.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="f48b2-109">Er is geen query geoptimaliseerd voor de **Win32_Product** klasse.</span><span class="sxs-lookup"><span data-stu-id="f48b2-109">The **Win32_Product** class is not query optimized.</span></span> <span data-ttu-id="f48b2-110">Query's die gebruikmaken van Joker filters, veroorzaken WMI de MSI-provider voor het inventariseren van alle geïnstalleerde producten en vervolgens de volledige lijst opeenvolgend parseren om het filter af te handelen.</span><span class="sxs-lookup"><span data-stu-id="f48b2-110">Queries that use wildcard filters cause WMI to use the MSI provider to enumerate all installed products then parse the full list sequentially to handle the filter.</span></span> <span data-ttu-id="f48b2-111">Dit initieert ook een consistentie controle van de geïnstalleerde pakketten, het verifiëren en herstellen van de installatie.</span><span class="sxs-lookup"><span data-stu-id="f48b2-111">This also initiates a consistency check of packages installed, verifying and repairing the install.</span></span> <span data-ttu-id="f48b2-112">De validatie is een traag proces en kan leiden tot fouten in de gebeurtenis Logboeken.</span><span class="sxs-lookup"><span data-stu-id="f48b2-112">The validation is a slow process and may result in errors in the event logs.</span></span> <span data-ttu-id="f48b2-113">Zoek [KB-artikel 974524](https://support.microsoft.com/help/974524)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f48b2-113">For more information seek [KB article 974524](https://support.microsoft.com/help/974524).</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="f48b2-114">Windows Installer-toepassingen weer geven</span><span class="sxs-lookup"><span data-stu-id="f48b2-114">Listing Windows Installer Applications</span></span>

<span data-ttu-id="f48b2-115">Als u de toepassingen wilt weer geven die zijn geïnstalleerd met de Windows Installer op een lokaal of extern systeem, gebruikt u de volgende eenvoudige WMI-query:</span><span class="sxs-lookup"><span data-stu-id="f48b2-115">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)"
```

```Output
Name             Caption                   Vendor                    Version       IdentifyingNumber
----             -------                   ------                    -------       -----------------
Microsoft .NET … Microsoft .NET Core Runt… Microsoft Corporation     16.84.26919   {BEB59D04-C6DD-4926-AFE…
```

<span data-ttu-id="f48b2-116">Als u alle eigenschappen van het **Win32_Product** -object wilt weer geven in de weer gave, gebruikt u de para meter **Eigenschappen** van de opmaak-cmdlets, zoals de `Format-List` cmdlet, met de waarde `*` (alle).</span><span class="sxs-lookup"><span data-stu-id="f48b2-116">To display all the properties of the **Win32_Product** object to the display, use the **Properties** parameter of the formatting cmdlets, such as the `Format-List` cmdlet, with a value of `*` (all).</span></span>

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

<span data-ttu-id="f48b2-117">U kunt ook de para meter `Get-CimInstance` **filter** gebruiken om alleen Microsoft .net 2,0-runtime te selecteren.</span><span class="sxs-lookup"><span data-stu-id="f48b2-117">Or, you could use the `Get-CimInstance` **Filter** parameter to select only Microsoft .NET 2.0 Runtime.</span></span> <span data-ttu-id="f48b2-118">De waarde van de **filter** parameter maakt gebruik van de syntaxis WMI Query Language (WQL), geen Windows Power shell-syntaxis.</span><span class="sxs-lookup"><span data-stu-id="f48b2-118">The value of the **Filter** parameter uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="f48b2-119">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f48b2-119">For example:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property *
```

<span data-ttu-id="f48b2-120">Als u alleen de eigenschappen wilt weer geven die u interesseren, gebruikt u de para meter **Property** van de Format-cmdlets om de gewenste eigenschappen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f48b2-120">To list only the properties that interest you, use the **Property** parameter of the formatting cmdlets to list the desired properties.</span></span>

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

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="f48b2-121">Alle toepassingen weer geven die niet worden geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="f48b2-121">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="f48b2-122">Omdat de meeste standaard toepassingen een verwijderer bij Windows registreren, kunnen we deze lokaal samen met hen door vinden in het Windows-REGI ster.</span><span class="sxs-lookup"><span data-stu-id="f48b2-122">Because most standard applications register an uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span> <span data-ttu-id="f48b2-123">Er is geen gegarandeerde manier om elke toepassing op een systeem te vinden.</span><span class="sxs-lookup"><span data-stu-id="f48b2-123">There is no guaranteed way to find every application on a system.</span></span> <span data-ttu-id="f48b2-124">Het is echter mogelijk om alle Program ma's te vinden met vermeldingen die worden weer gegeven in het **onderdeel Software** van de volgende register sleutel:</span><span class="sxs-lookup"><span data-stu-id="f48b2-124">However, it is possible to find all programs with listings displayed in **Add or Remove Programs** in the following registry key:</span></span>

<span data-ttu-id="f48b2-125">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span><span class="sxs-lookup"><span data-stu-id="f48b2-125">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span></span>

<span data-ttu-id="f48b2-126">We kunnen deze sleutel onderzoeken om toepassingen te vinden.</span><span class="sxs-lookup"><span data-stu-id="f48b2-126">We can examine this key to find applications.</span></span> <span data-ttu-id="f48b2-127">Om het weer geven van de verwijderings sleutel gemakkelijker te maken, kunnen we een Power Shell-station toewijzen aan deze register locatie:</span><span class="sxs-lookup"><span data-stu-id="f48b2-127">To make it easier to view the Uninstall key, we can map a PowerShell drive to this registry location:</span></span>

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

<span data-ttu-id="f48b2-128">We hebben nu een station met de naam ' uninstall: ' dat kan worden gebruikt om snel en eenvoudig te zoeken naar toepassings installaties.</span><span class="sxs-lookup"><span data-stu-id="f48b2-128">We now have a drive named "Uninstall:" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="f48b2-129">We kunnen het aantal geïnstalleerde toepassingen vinden door het aantal register sleutels in het verwijderen te tellen: Power Shell-station:</span><span class="sxs-lookup"><span data-stu-id="f48b2-129">We can find the number of installed applications by counting the number of registry keys in the Uninstall: PowerShell drive:</span></span>

```powershell
(Get-ChildItem -Path Uninstall:).Count
```

```Output
459
```

<span data-ttu-id="f48b2-130">We kunnen deze lijst met toepassingen verder doorzoeken door gebruik te maken van verschillende technieken, te beginnen met `Get-ChildItem`.</span><span class="sxs-lookup"><span data-stu-id="f48b2-130">We can search this list of applications further by using a variety of techniques, beginning with `Get-ChildItem`.</span></span> <span data-ttu-id="f48b2-131">Gebruik de volgende opdracht om een lijst met toepassingen op te halen en deze op te slaan in de variabele `$UninstallableApplications`:</span><span class="sxs-lookup"><span data-stu-id="f48b2-131">To get a list of applications and save them in the `$UninstallableApplications` variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

<span data-ttu-id="f48b2-132">Als u de waarden van de Register vermeldingen in de register sleutels onder verwijderen wilt weer geven, gebruikt u de methode GetValue van de register sleutels.</span><span class="sxs-lookup"><span data-stu-id="f48b2-132">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="f48b2-133">De waarde van de methode is de naam van de register vermelding.</span><span class="sxs-lookup"><span data-stu-id="f48b2-133">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="f48b2-134">Gebruik bijvoorbeeld de volgende opdracht om de weergave namen van de toepassingen in de uninstall-sleutel te vinden:</span><span class="sxs-lookup"><span data-stu-id="f48b2-134">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="f48b2-135">Er is geen garantie dat deze waarden uniek zijn.</span><span class="sxs-lookup"><span data-stu-id="f48b2-135">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="f48b2-136">In het volgende voor beeld worden twee geïnstalleerde items weer gegeven als ' Windows Media Encoder 9 Series ':</span><span class="sxs-lookup"><span data-stu-id="f48b2-136">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

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
                               HelpLink            : http://go.microsoft.com/fwlink/?LinkID=91955
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

## <a name="installing-applications"></a><span data-ttu-id="f48b2-137">Toepassingen installeren</span><span class="sxs-lookup"><span data-stu-id="f48b2-137">Installing Applications</span></span>

<span data-ttu-id="f48b2-138">U kunt de klasse **Win32_Product** gebruiken om Windows Installer pakketten extern of lokaal te installeren.</span><span class="sxs-lookup"><span data-stu-id="f48b2-138">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="f48b2-139">Als u een toepassing wilt installeren, moet u Power shell starten met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="f48b2-139">To install an application, you must start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="f48b2-140">Wanneer u extern installeert, gebruikt u een UNC-netwerkpad (Universal Naming Convention) om het pad naar het MSI-pakket op te geven, omdat het WMI-subsysteem geen Power shell-paden begrijpt.</span><span class="sxs-lookup"><span data-stu-id="f48b2-140">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand PowerShell paths.</span></span> <span data-ttu-id="f48b2-141">Als u bijvoorbeeld het pakket NewPackage. msi wilt installeren dat zich bevindt in de netwerk share `\\AppServ\dsp` op de externe computer PC01, typt u de volgende opdracht achter de Power shell-prompt:</span><span class="sxs-lookup"><span data-stu-id="f48b2-141">For example, to install the NewPackage.msi package located in the network share `\\AppServ\dsp` on the remote computer PC01, type the following command at the PowerShell prompt:</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

<span data-ttu-id="f48b2-142">Toepassingen die geen gebruik maken van Windows Installer technologie, kunnen toepassingsspecifieke methoden hebben voor automatische implementatie.</span><span class="sxs-lookup"><span data-stu-id="f48b2-142">Applications that do not use Windows Installer technology may have application-specific methods for automated deployment.</span></span> <span data-ttu-id="f48b2-143">Raadpleeg de documentatie bij de toepassing of Raadpleeg het ondersteunings systeem van de leverancier van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="f48b2-143">Check the documentation for the application or consult the application vendor's support system.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="f48b2-144">Toepassingen verwijderen</span><span class="sxs-lookup"><span data-stu-id="f48b2-144">Removing Applications</span></span>

<span data-ttu-id="f48b2-145">Het verwijderen van een Windows Installer-pakket met behulp van Power shell werkt op ongeveer dezelfde manier als het installeren van een pakket.</span><span class="sxs-lookup"><span data-stu-id="f48b2-145">Removing a Windows Installer package using PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="f48b2-146">Hier volgt een voor beeld van het selecteren van het pakket dat moet worden verwijderd op basis van de naam. in sommige gevallen kan het gemakkelijker worden gefilterd met de **nummer**:</span><span class="sxs-lookup"><span data-stu-id="f48b2-146">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

<span data-ttu-id="f48b2-147">Het verwijderen van andere toepassingen is niet helemaal eenvoudig, zelfs wanneer deze lokaal worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f48b2-147">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="f48b2-148">U kunt de opdracht regel verwijderings teken reeksen voor deze toepassingen vinden door de eigenschap **UninstallString** uit te pakken.</span><span class="sxs-lookup"><span data-stu-id="f48b2-148">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span>
<span data-ttu-id="f48b2-149">Deze methode werkt voor Windows Installer toepassingen en voor oudere Program ma's die worden weer gegeven onder de sleutel Uninstall:</span><span class="sxs-lookup"><span data-stu-id="f48b2-149">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="f48b2-150">U kunt de uitvoer filteren op de weergave naam, indien gewenst:</span><span class="sxs-lookup"><span data-stu-id="f48b2-150">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="f48b2-151">Deze teken reeksen kunnen echter niet rechtstreeks worden gebruikt vanuit de Power shell-prompt zonder enige aanpassing.</span><span class="sxs-lookup"><span data-stu-id="f48b2-151">However, these strings may not be directly usable from the PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="f48b2-152">Windows Installer-toepassingen bijwerken</span><span class="sxs-lookup"><span data-stu-id="f48b2-152">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="f48b2-153">Als u een toepassing wilt bijwerken, moet u de naam van de toepassing en het pad voor het upgrade pakket van de toepassing weten.</span><span class="sxs-lookup"><span data-stu-id="f48b2-153">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="f48b2-154">Met deze informatie kunt u een toepassing bijwerken met één Power shell-opdracht:</span><span class="sxs-lookup"><span data-stu-id="f48b2-154">With that information, you can upgrade an application with a single PowerShell command:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
