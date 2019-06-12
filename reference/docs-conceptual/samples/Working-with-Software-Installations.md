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
# <a name="working-with-software-installations"></a><span data-ttu-id="cca1d-103">Met software-installaties werken</span><span class="sxs-lookup"><span data-stu-id="cca1d-103">Working with Software Installations</span></span>

<span data-ttu-id="cca1d-104">Toepassingen die zijn ontworpen voor het gebruik van Windows Installer is toegankelijk via WMI van **Win32_Product** klasse, maar niet alle toepassingen in gebruik vandaag nog gebruik van het Windows-installatieprogramma.</span><span class="sxs-lookup"><span data-stu-id="cca1d-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span>
<span data-ttu-id="cca1d-105">Toepassingen die gebruikmaken van alternatieve installatieprocedure meestal niet worden beheerd door de Windows-installatieservice.</span><span class="sxs-lookup"><span data-stu-id="cca1d-105">Applications that use alternate setup routines are not usually managed by the Windows Installer.</span></span>
<span data-ttu-id="cca1d-106">Specifieke technieken voor het werken met deze toepassingen, is afhankelijk van de installer-software en beslissingen door de ontwikkelaar van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="cca1d-106">Specific techniques for working with those applications depends on the installer software and decisions made by the application developer.</span></span> <span data-ttu-id="cca1d-107">Bijvoorbeeld kunnen niet toepassingen zijn geïnstalleerd door de bestanden zijn gekopieerd naar een map op de computer meestal worden beheerd met behulp van technieken die worden besproken hier.</span><span class="sxs-lookup"><span data-stu-id="cca1d-107">For example, applications installed by copying the files to a folder on the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="cca1d-108">U kunt beheren van deze toepassingen als bestanden en mappen met behulp van de technieken beschreven in [werken met bestanden en mappen](Working-with-Files-and-Folders.md).</span><span class="sxs-lookup"><span data-stu-id="cca1d-108">You can manage these applications as files and folders by using the techniques discussed in [Working With Files and Folders](Working-with-Files-and-Folders.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="cca1d-109">De **Win32_Product** klasse is geen query geoptimaliseerd.</span><span class="sxs-lookup"><span data-stu-id="cca1d-109">The **Win32_Product** class is not query optimized.</span></span> <span data-ttu-id="cca1d-110">Query's die gebruikmaken van jokertekens filters ertoe leiden dat WMI om met het MSI-provider te inventariseren van alle geïnstalleerde producten en parseren van de volledige lijst sequentieel worden verwerkt voor het afhandelen van het filter.</span><span class="sxs-lookup"><span data-stu-id="cca1d-110">Queries that use wildcard filters cause WMI to use the MSI provider to enumerate all installed products then parse the full list sequentially to handle the filter.</span></span> <span data-ttu-id="cca1d-111">Hiermee initieert ook een consistentiecontrole uit van pakketten geïnstalleerd, te controleren en herstellen van de installatie.</span><span class="sxs-lookup"><span data-stu-id="cca1d-111">This also initiates a consistency check of packages installed, verifying and repairing the install.</span></span> <span data-ttu-id="cca1d-112">De validatie is een trage proces en kan leiden tot fouten in de gebeurtenislogboeken.</span><span class="sxs-lookup"><span data-stu-id="cca1d-112">The validation is a slow process and may result in errors in the event logs.</span></span> <span data-ttu-id="cca1d-113">Voor meer informatie zoeken [KB-artikel 974524](https://support.microsoft.com/help/974524).</span><span class="sxs-lookup"><span data-stu-id="cca1d-113">For more information seek [KB article 974524](https://support.microsoft.com/help/974524).</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="cca1d-114">Windows Installer-toepassingen weergeven</span><span class="sxs-lookup"><span data-stu-id="cca1d-114">Listing Windows Installer Applications</span></span>

<span data-ttu-id="cca1d-115">Als u de toepassingen zijn geïnstalleerd met de Windows Installer op een lokale of externe systeem, gebruik de volgende eenvoudige WMI-query:</span><span class="sxs-lookup"><span data-stu-id="cca1d-115">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)"
```

```Output
Name               Caption                     Vendor                 Version      IdentifyingNumber
----               -------                     ------                 -------      -----------------
Microsoft .NET ... Microsoft .NET Core Runt... Microsoft Corporation  16.72.26629  {ACC73072-9AD5-416C-94B...
```

<span data-ttu-id="cca1d-116">Om weer te geven van alle eigenschappen van de **Win32_Product** object aan de weergave, gebruik de **eigenschappen** parameter van de opmaak cmdlets, zoals de `Format-List` cmdlet, met een waarde van `*` (alle).</span><span class="sxs-lookup"><span data-stu-id="cca1d-116">To display all the properties of the **Win32_Product** object to the display, use the **Properties** parameter of the formatting cmdlets, such as the `Format-List` cmdlet, with a value of `*` (all).</span></span>

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

<span data-ttu-id="cca1d-117">Of u kunt de `Get-CimInstance` **Filter** parameter selecteren alleen Microsoft .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="cca1d-117">Or, you could use the `Get-CimInstance` **Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="cca1d-118">De waarde van de **Filter** parameter maakt gebruik van WMI Query Language (WQL)-syntaxis, niet Windows PowerShell-syntaxis.</span><span class="sxs-lookup"><span data-stu-id="cca1d-118">The value of the **Filter** parameter uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="cca1d-119">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="cca1d-119">For example:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property *
```

<span data-ttu-id="cca1d-120">U kunt alleen de eigenschappen die u interesseren gebruiken de **eigenschap** parameter van de opmaak cmdlets om de gewenste eigenschappen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="cca1d-120">To list only the properties that interest you, use the **Property** parameter of the formatting cmdlets to list the desired properties.</span></span>

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

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="cca1d-121">Lijst van alle toepassingen die kan worden verwijderd</span><span class="sxs-lookup"><span data-stu-id="cca1d-121">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="cca1d-122">Omdat een verwijderprogramma meest standaard toepassingen bij Windows registreren, die we kunnen werken met die lokaal door ze te vinden in het Windows-register.</span><span class="sxs-lookup"><span data-stu-id="cca1d-122">Because most standard applications register an uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span> <span data-ttu-id="cca1d-123">Er is geen gegarandeerde manier om te vinden van elke toepassing op een systeem.</span><span class="sxs-lookup"><span data-stu-id="cca1d-123">There is no guaranteed way to find every application on a system.</span></span> <span data-ttu-id="cca1d-124">Het is echter mogelijk om te zoeken van alle programma's met aanbiedingen weergegeven in **software**.</span><span class="sxs-lookup"><span data-stu-id="cca1d-124">However, it is possible to find all programs with listings displayed in **Add or Remove Programs**.</span></span> <span data-ttu-id="cca1d-125">**Toevoegen of verwijderen van programma's** zoekt naar deze toepassingen in de volgende registersleutel:</span><span class="sxs-lookup"><span data-stu-id="cca1d-125">**Add or Remove Programs** finds these applications in the following registry key:</span></span>

<span data-ttu-id="cca1d-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span><span class="sxs-lookup"><span data-stu-id="cca1d-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span></span>

<span data-ttu-id="cca1d-127">We kunt deze sleutel om te zoeken naar toepassingen bekijken.</span><span class="sxs-lookup"><span data-stu-id="cca1d-127">We can examine this key to find applications.</span></span> <span data-ttu-id="cca1d-128">Als u wilt maken het gemakkelijker om de sleutel verwijderen weer te geven, kunnen we een PowerShell-station worden toegewezen aan deze registerlocatie:</span><span class="sxs-lookup"><span data-stu-id="cca1d-128">To make it easier to view the Uninstall key, we can map a PowerShell drive to this registry location:</span></span>

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```
<span data-ttu-id="cca1d-129">We hebben nu een station met de naam "verwijderen: ' kunnen worden gebruikt voor een snel en gemakkelijk zoeken voor installaties van toepassingen.</span><span class="sxs-lookup"><span data-stu-id="cca1d-129">We now have a drive named "Uninstall:" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="cca1d-130">Er vindt het aantal geïnstalleerde toepassingen door het aantal registersleutels in de verwijdering te tellen: PowerShell-station:</span><span class="sxs-lookup"><span data-stu-id="cca1d-130">We can find the number of installed applications by counting the number of registry keys in the Uninstall: PowerShell drive:</span></span>

```
(Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="cca1d-131">We kunnen deze lijst met toepassingen verder zoeken met behulp van verschillende technieken, beginnen met **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="cca1d-131">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="cca1d-132">Voor het ophalen van een lijst met toepassingen en slaat u ze in de **$UninstallableApplications** variabele, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="cca1d-132">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

<span data-ttu-id="cca1d-133">Als de waarden van de registervermeldingen in de registersleutels onder verwijderen weergeven, gebruikt u de GetValue-methode van de registersleutels.</span><span class="sxs-lookup"><span data-stu-id="cca1d-133">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="cca1d-134">De waarde van de methode is de naam van het register-item.</span><span class="sxs-lookup"><span data-stu-id="cca1d-134">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="cca1d-135">Bijvoorbeeld, als u zoekt de weergavenamen van toepassingen in de sleutel verwijderen, gebruik de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="cca1d-135">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="cca1d-136">Er is geen garantie dat deze waarden uniek zijn.</span><span class="sxs-lookup"><span data-stu-id="cca1d-136">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="cca1d-137">In het volgende voorbeeld worden twee geïnstalleerde items weergegeven als 'Windows Media Encoder 9 Series':</span><span class="sxs-lookup"><span data-stu-id="cca1d-137">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

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

## <a name="installing-applications"></a><span data-ttu-id="cca1d-138">Installeren van toepassingen</span><span class="sxs-lookup"><span data-stu-id="cca1d-138">Installing Applications</span></span>

<span data-ttu-id="cca1d-139">U kunt de **Win32_Product** klasse voor het installeren van Windows Installer-pakketten, extern of lokaal.</span><span class="sxs-lookup"><span data-stu-id="cca1d-139">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="cca1d-140">Een toepassing te installeren, moet u PowerShell starten met de optie 'Als administrator uitvoeren'.</span><span class="sxs-lookup"><span data-stu-id="cca1d-140">To install an application, you must start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="cca1d-141">Bij de installatie op afstand, moet u een netwerkpad Universal Naming Convention (UNC) gebruiken om op te geven van het pad naar het MSI-pakket, omdat het WMI-subsysteem heeft niet informatie over PowerShell paden.</span><span class="sxs-lookup"><span data-stu-id="cca1d-141">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand PowerShell paths.</span></span> <span data-ttu-id="cca1d-142">Bijvoorbeeld, voor het installeren van het pakket NewPackage.msi zich in de netwerkshare `\\AppServ\dsp` op de externe computer PC01, typt u de volgende opdracht achter de PowerShell-prompt:</span><span class="sxs-lookup"><span data-stu-id="cca1d-142">For example, to install the NewPackage.msi package located in the network share `\\AppServ\dsp` on the remote computer PC01, type the following command at the PowerShell prompt:</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

<span data-ttu-id="cca1d-143">Toepassingen die geen gebruik maken van Windows Installer-technologie hebben toepassingsspecifieke methoden voor automatische implementatie.</span><span class="sxs-lookup"><span data-stu-id="cca1d-143">Applications that do not use Windows Installer technology may have application-specific methods for automated deployment.</span></span> <span data-ttu-id="cca1d-144">Raadpleeg de documentatie voor de toepassing of neem contact op ondersteuning van system van de leverancier van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="cca1d-144">Check the documentation for the application or consult the application vendor's support system.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="cca1d-145">Toepassingen verwijderen</span><span class="sxs-lookup"><span data-stu-id="cca1d-145">Removing Applications</span></span>

<span data-ttu-id="cca1d-146">Verwijderen van een Windows Installer-pakket met behulp van PowerShell werkt op ongeveer dezelfde manier als een pakket installeert.</span><span class="sxs-lookup"><span data-stu-id="cca1d-146">Removing a Windows Installer package using PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="cca1d-147">Hier volgt een voorbeeld waarin selecteert het pakket te verwijderen op basis van de naam; in sommige gevallen kan het eenvoudiger om te filteren met zijn de **id-nummer**:</span><span class="sxs-lookup"><span data-stu-id="cca1d-147">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

<span data-ttu-id="cca1d-148">Verwijderen van andere toepassingen is niet zo eenvoudig, zelfs wanneer lokaal uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cca1d-148">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="cca1d-149">We kunnen de opdrachtregel verwijderen tekenreeksen voor deze toepassingen vinden door te extraheren de **UninstallString** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="cca1d-149">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span>
<span data-ttu-id="cca1d-150">Deze methode werkt voor Windows Installer-toepassingen en oudere programma's die wordt weergegeven onder de sleutel verwijderen:</span><span class="sxs-lookup"><span data-stu-id="cca1d-150">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="cca1d-151">U kunt desgewenst de uitvoer filteren op de weergavenaam:</span><span class="sxs-lookup"><span data-stu-id="cca1d-151">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="cca1d-152">Deze tekenreeksen kunnen echter niet worden rechtstreeks vanuit de PowerShell-prompt zonder enige wijziging gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cca1d-152">However, these strings may not be directly usable from the PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="cca1d-153">Upgraden van Windows Installer-toepassingen</span><span class="sxs-lookup"><span data-stu-id="cca1d-153">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="cca1d-154">Als u een toepassing bijwerken, moet u de naam van de toepassing en het pad kennen op het updatepakket van toepassing.</span><span class="sxs-lookup"><span data-stu-id="cca1d-154">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="cca1d-155">Met deze informatie kunt u een toepassing met slechts één PowerShell-opdracht bijwerken:</span><span class="sxs-lookup"><span data-stu-id="cca1d-155">With that information, you can upgrade an application with a single PowerShell command:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
