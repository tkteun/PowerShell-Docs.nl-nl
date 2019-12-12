---
ms.date: 06/03/2019
keywords: Power shell, cmdlet
title: Met software-installaties werken
ms.openlocfilehash: 6d2111a332f0e8c1b545186d3d950e936aed1834
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "66830291"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="9f190-103">Met software-installaties werken</span><span class="sxs-lookup"><span data-stu-id="9f190-103">Working with Software Installations</span></span>

<span data-ttu-id="9f190-104">Toepassingen die zijn ontworpen om Windows Installer te gebruiken, zijn toegankelijk via de **Win32_Product** klasse van WMI, maar niet alle toepassingen die tegenwoordig gebruiken, gebruiken de Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="9f190-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span>
<span data-ttu-id="9f190-105">Toepassingen die alternatieve installatie routines gebruiken, worden doorgaans niet beheerd door de Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="9f190-105">Applications that use alternate setup routines are not usually managed by the Windows Installer.</span></span>
<span data-ttu-id="9f190-106">Specifieke technieken voor het werken met deze toepassingen zijn afhankelijk van de installatie software en beslissingen van de ontwikkelaar van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="9f190-106">Specific techniques for working with those applications depends on the installer software and decisions made by the application developer.</span></span> <span data-ttu-id="9f190-107">Toepassingen die zijn geïnstalleerd door het kopiëren van de bestanden naar een map op de computer, kunnen bijvoorbeeld doorgaans niet worden beheerd met behulp van technieken die hier worden beschreven.</span><span class="sxs-lookup"><span data-stu-id="9f190-107">For example, applications installed by copying the files to a folder on the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="9f190-108">U kunt deze toepassingen beheren als bestanden en mappen met behulp van de technieken die worden beschreven in [werken met bestanden en mappen](Working-with-Files-and-Folders.md).</span><span class="sxs-lookup"><span data-stu-id="9f190-108">You can manage these applications as files and folders by using the techniques discussed in [Working With Files and Folders](Working-with-Files-and-Folders.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="9f190-109">Er is geen query geoptimaliseerd voor de **Win32_Product** klasse.</span><span class="sxs-lookup"><span data-stu-id="9f190-109">The **Win32_Product** class is not query optimized.</span></span> <span data-ttu-id="9f190-110">Query's die gebruikmaken van Joker filters, veroorzaken WMI de MSI-provider voor het inventariseren van alle geïnstalleerde producten en vervolgens de volledige lijst opeenvolgend parseren om het filter af te handelen.</span><span class="sxs-lookup"><span data-stu-id="9f190-110">Queries that use wildcard filters cause WMI to use the MSI provider to enumerate all installed products then parse the full list sequentially to handle the filter.</span></span> <span data-ttu-id="9f190-111">Dit initieert ook een consistentie controle van de geïnstalleerde pakketten, het verifiëren en herstellen van de installatie.</span><span class="sxs-lookup"><span data-stu-id="9f190-111">This also initiates a consistency check of packages installed, verifying and repairing the install.</span></span> <span data-ttu-id="9f190-112">De validatie is een traag proces en kan leiden tot fouten in de gebeurtenis Logboeken.</span><span class="sxs-lookup"><span data-stu-id="9f190-112">The validation is a slow process and may result in errors in the event logs.</span></span> <span data-ttu-id="9f190-113">Zoek [KB-artikel 974524](https://support.microsoft.com/help/974524)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9f190-113">For more information seek [KB article 974524](https://support.microsoft.com/help/974524).</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="9f190-114">Windows Installer-toepassingen weer geven</span><span class="sxs-lookup"><span data-stu-id="9f190-114">Listing Windows Installer Applications</span></span>

<span data-ttu-id="9f190-115">Als u de toepassingen wilt weer geven die zijn geïnstalleerd met de Windows Installer op een lokaal of extern systeem, gebruikt u de volgende eenvoudige WMI-query:</span><span class="sxs-lookup"><span data-stu-id="9f190-115">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)"
```

```Output
Name               Caption                     Vendor                 Version      IdentifyingNumber
----               -------                     ------                 -------      -----------------
Microsoft .NET ... Microsoft .NET Core Runt... Microsoft Corporation  16.72.26629  {ACC73072-9AD5-416C-94B...
```

<span data-ttu-id="9f190-116">Als u alle eigenschappen van het **Win32_Product** -object wilt weer geven in de weer gave, gebruikt u de para meter **Eigenschappen** van de opmaak-cmdlets, zoals de `Format-List` cmdlet, met de waarde `*` (alle).</span><span class="sxs-lookup"><span data-stu-id="9f190-116">To display all the properties of the **Win32_Product** object to the display, use the **Properties** parameter of the formatting cmdlets, such as the `Format-List` cmdlet, with a value of `*` (all).</span></span>

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

<span data-ttu-id="9f190-117">U kunt ook de para meter `Get-CimInstance` **filter** gebruiken om alleen Microsoft .NET Framework 2,0 te selecteren.</span><span class="sxs-lookup"><span data-stu-id="9f190-117">Or, you could use the `Get-CimInstance` **Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="9f190-118">De waarde van de **filter** parameter maakt gebruik van de syntaxis WMI Query Language (WQL), geen Windows Power shell-syntaxis.</span><span class="sxs-lookup"><span data-stu-id="9f190-118">The value of the **Filter** parameter uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="9f190-119">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9f190-119">For example:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property *
```

<span data-ttu-id="9f190-120">Als u alleen de eigenschappen wilt weer geven die u interesseren, gebruikt u de para meter **Property** van de Format-cmdlets om de gewenste eigenschappen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="9f190-120">To list only the properties that interest you, use the **Property** parameter of the formatting cmdlets to list the desired properties.</span></span>

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

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="9f190-121">Alle toepassingen weer geven die niet worden geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="9f190-121">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="9f190-122">Omdat de meeste standaard toepassingen een verwijderer bij Windows registreren, kunnen we deze lokaal samen met hen door vinden in het Windows-REGI ster.</span><span class="sxs-lookup"><span data-stu-id="9f190-122">Because most standard applications register an uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span> <span data-ttu-id="9f190-123">Er is geen gegarandeerde manier om elke toepassing op een systeem te vinden.</span><span class="sxs-lookup"><span data-stu-id="9f190-123">There is no guaranteed way to find every application on a system.</span></span> <span data-ttu-id="9f190-124">Het is echter mogelijk om alle Program ma's te vinden met vermeldingen die worden weer gegeven in het **onderdeel Software**.</span><span class="sxs-lookup"><span data-stu-id="9f190-124">However, it is possible to find all programs with listings displayed in **Add or Remove Programs**.</span></span> <span data-ttu-id="9f190-125">In **Program Ma's toevoegen of verwijderen** vindt u deze toepassingen in de volgende register sleutel:</span><span class="sxs-lookup"><span data-stu-id="9f190-125">**Add or Remove Programs** finds these applications in the following registry key:</span></span>

<span data-ttu-id="9f190-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span><span class="sxs-lookup"><span data-stu-id="9f190-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span></span>

<span data-ttu-id="9f190-127">We kunnen deze sleutel onderzoeken om toepassingen te vinden.</span><span class="sxs-lookup"><span data-stu-id="9f190-127">We can examine this key to find applications.</span></span> <span data-ttu-id="9f190-128">Om het weer geven van de verwijderings sleutel gemakkelijker te maken, kunnen we een Power Shell-station toewijzen aan deze register locatie:</span><span class="sxs-lookup"><span data-stu-id="9f190-128">To make it easier to view the Uninstall key, we can map a PowerShell drive to this registry location:</span></span>

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```
<span data-ttu-id="9f190-129">We hebben nu een station met de naam ' uninstall: ' dat kan worden gebruikt om snel en eenvoudig te zoeken naar toepassings installaties.</span><span class="sxs-lookup"><span data-stu-id="9f190-129">We now have a drive named "Uninstall:" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="9f190-130">We kunnen het aantal geïnstalleerde toepassingen vinden door het aantal register sleutels in het verwijderen te tellen: Power Shell-station:</span><span class="sxs-lookup"><span data-stu-id="9f190-130">We can find the number of installed applications by counting the number of registry keys in the Uninstall: PowerShell drive:</span></span>

```
(Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="9f190-131">We kunnen deze lijst met toepassingen verder doorzoeken door gebruik te maken van verschillende technieken, beginnend met **Get-Child item**.</span><span class="sxs-lookup"><span data-stu-id="9f190-131">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="9f190-132">Gebruik de volgende opdracht om een lijst met toepassingen op te halen en deze op te slaan in de variabele **$UninstallableApplications** :</span><span class="sxs-lookup"><span data-stu-id="9f190-132">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

<span data-ttu-id="9f190-133">Als u de waarden van de Register vermeldingen in de register sleutels onder verwijderen wilt weer geven, gebruikt u de methode GetValue van de register sleutels.</span><span class="sxs-lookup"><span data-stu-id="9f190-133">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="9f190-134">De waarde van de methode is de naam van de register vermelding.</span><span class="sxs-lookup"><span data-stu-id="9f190-134">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="9f190-135">Gebruik bijvoorbeeld de volgende opdracht om de weergave namen van de toepassingen in de uninstall-sleutel te vinden:</span><span class="sxs-lookup"><span data-stu-id="9f190-135">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="9f190-136">Er is geen garantie dat deze waarden uniek zijn.</span><span class="sxs-lookup"><span data-stu-id="9f190-136">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="9f190-137">In het volgende voor beeld worden twee geïnstalleerde items weer gegeven als ' Windows Media Encoder 9 Series ':</span><span class="sxs-lookup"><span data-stu-id="9f190-137">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

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

## <a name="installing-applications"></a><span data-ttu-id="9f190-138">Toepassingen installeren</span><span class="sxs-lookup"><span data-stu-id="9f190-138">Installing Applications</span></span>

<span data-ttu-id="9f190-139">U kunt de klasse **Win32_Product** gebruiken om Windows Installer pakketten extern of lokaal te installeren.</span><span class="sxs-lookup"><span data-stu-id="9f190-139">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="9f190-140">Als u een toepassing wilt installeren, moet u Power shell starten met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="9f190-140">To install an application, you must start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="9f190-141">Wanneer u extern installeert, gebruikt u een UNC-netwerkpad (Universal Naming Convention) om het pad naar het MSI-pakket op te geven, omdat het WMI-subsysteem geen Power shell-paden begrijpt.</span><span class="sxs-lookup"><span data-stu-id="9f190-141">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand PowerShell paths.</span></span> <span data-ttu-id="9f190-142">Als u bijvoorbeeld het pakket NewPackage. msi wilt installeren dat zich bevindt in de netwerk share `\\AppServ\dsp` op de externe computer PC01, typt u de volgende opdracht achter de Power shell-prompt:</span><span class="sxs-lookup"><span data-stu-id="9f190-142">For example, to install the NewPackage.msi package located in the network share `\\AppServ\dsp` on the remote computer PC01, type the following command at the PowerShell prompt:</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

<span data-ttu-id="9f190-143">Toepassingen die geen gebruik maken van Windows Installer technologie, kunnen toepassingsspecifieke methoden hebben voor automatische implementatie.</span><span class="sxs-lookup"><span data-stu-id="9f190-143">Applications that do not use Windows Installer technology may have application-specific methods for automated deployment.</span></span> <span data-ttu-id="9f190-144">Raadpleeg de documentatie bij de toepassing of Raadpleeg het ondersteunings systeem van de leverancier van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="9f190-144">Check the documentation for the application or consult the application vendor's support system.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="9f190-145">Toepassingen verwijderen</span><span class="sxs-lookup"><span data-stu-id="9f190-145">Removing Applications</span></span>

<span data-ttu-id="9f190-146">Het verwijderen van een Windows Installer-pakket met behulp van Power shell werkt op ongeveer dezelfde manier als het installeren van een pakket.</span><span class="sxs-lookup"><span data-stu-id="9f190-146">Removing a Windows Installer package using PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="9f190-147">Hier volgt een voor beeld van het selecteren van het pakket dat moet worden verwijderd op basis van de naam. in sommige gevallen kan het gemakkelijker worden gefilterd met de **nummer**:</span><span class="sxs-lookup"><span data-stu-id="9f190-147">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

<span data-ttu-id="9f190-148">Het verwijderen van andere toepassingen is niet helemaal eenvoudig, zelfs wanneer deze lokaal worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9f190-148">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="9f190-149">U kunt de opdracht regel verwijderings teken reeksen voor deze toepassingen vinden door de eigenschap **UninstallString** uit te pakken.</span><span class="sxs-lookup"><span data-stu-id="9f190-149">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span>
<span data-ttu-id="9f190-150">Deze methode werkt voor Windows Installer toepassingen en voor oudere Program ma's die worden weer gegeven onder de sleutel Uninstall:</span><span class="sxs-lookup"><span data-stu-id="9f190-150">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="9f190-151">U kunt de uitvoer filteren op de weergave naam, indien gewenst:</span><span class="sxs-lookup"><span data-stu-id="9f190-151">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="9f190-152">Deze teken reeksen kunnen echter niet rechtstreeks worden gebruikt vanuit de Power shell-prompt zonder enige aanpassing.</span><span class="sxs-lookup"><span data-stu-id="9f190-152">However, these strings may not be directly usable from the PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="9f190-153">Windows Installer-toepassingen bijwerken</span><span class="sxs-lookup"><span data-stu-id="9f190-153">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="9f190-154">Als u een toepassing wilt bijwerken, moet u de naam van de toepassing en het pad voor het upgrade pakket van de toepassing weten.</span><span class="sxs-lookup"><span data-stu-id="9f190-154">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="9f190-155">Met deze informatie kunt u een toepassing bijwerken met één Power shell-opdracht:</span><span class="sxs-lookup"><span data-stu-id="9f190-155">With that information, you can upgrade an application with a single PowerShell command:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
