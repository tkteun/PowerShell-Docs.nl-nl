---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Werken met Software-installaties
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: 2078376a8be19c9ff8ecc44183eb89f14bc388ed
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="working-with-software-installations"></a><span data-ttu-id="57f1f-103">Werken met Software-installaties</span><span class="sxs-lookup"><span data-stu-id="57f1f-103">Working with Software Installations</span></span>
<span data-ttu-id="57f1f-104">Toepassingen die zijn ontworpen voor gebruik van Windows Installer is toegankelijk via WMI van **Win32_Product** klasse, maar niet alle toepassingen in gebruik vandaag gebruik van Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="57f1f-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span> <span data-ttu-id="57f1f-105">Omdat Windows Installer een groot aantal standaard technieken biedt voor het werken met installeerbare toepassingen, gaan we in voornamelijk op deze toepassingen.</span><span class="sxs-lookup"><span data-stu-id="57f1f-105">Because the Windows Installer provides the widest range of standard techniques for working with installable applications, we will focus primarily on those applications.</span></span> <span data-ttu-id="57f1f-106">Toepassingen die gebruikmaken van routines alternatieve instellen zullen in het algemeen niet worden beheerd door de Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="57f1f-106">Applications that use alternate setup routines will generally not be managed by the Windows Installer.</span></span> <span data-ttu-id="57f1f-107">Specifieke technieken voor het werken met deze toepassingen, is afhankelijk van de installer-software en de beslissingen van de ontwikkelaar van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="57f1f-107">Specific techniques for working with those applications will depend on the installer software and decisions made by the application developer.</span></span>

> [!NOTE]
> <span data-ttu-id="57f1f-108">De door toepassingsbestanden te kopiëren naar de computer doorgaans geïnstalleerde toepassingen kunnen niet worden beheerd met behulp van technieken die worden besproken hier.</span><span class="sxs-lookup"><span data-stu-id="57f1f-108">Applications that are installed by copying the application files to the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="57f1f-109">U kunt deze toepassingen als bestanden en mappen beheren met behulp van de technieken beschreven in de sectie 'Werken met bestanden en mappen'.</span><span class="sxs-lookup"><span data-stu-id="57f1f-109">You can manage these applications as files and folders by using the techniques discussed in the "Working With Files and Folders" section.</span></span>

### <a name="listing-windows-installer-applications"></a><span data-ttu-id="57f1f-110">Windows Installer-toepassingen weergeven</span><span class="sxs-lookup"><span data-stu-id="57f1f-110">Listing Windows Installer Applications</span></span>
<span data-ttu-id="57f1f-111">Als de toepassingen zijn geïnstalleerd met Windows Installer op een lokale of externe systeem weergeven, gebruikt u de volgende eenvoudige WMI-query:</span><span class="sxs-lookup"><span data-stu-id="57f1f-111">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

<span data-ttu-id="57f1f-112">Als u wilt weergeven alle eigenschappen van het object Win32_Product naar de weergave, gebruikt u de eigenschappen-parameter van de opmaak cmdlets, zoals de cmdlet lijst indelen met een waarde van \* (alle).</span><span class="sxs-lookup"><span data-stu-id="57f1f-112">To display all of the properties of the Win32_Product object to the display, use the Properties parameter of the formatting cmdlets, such as the Format-List cmdlet, with a value of \* (all).</span></span>

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

<span data-ttu-id="57f1f-113">Of u kunt de **Get-WmiObject Filter** parameter alleen Microsoft .NET Framework 2.0 te selecteren.</span><span class="sxs-lookup"><span data-stu-id="57f1f-113">Or, you could use the **Get-WmiObject Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="57f1f-114">Omdat het filter dat wordt gebruikt in deze opdracht een WMI-filter is, gebruikt de syntaxis van de WMI Query Language (WQL), niet voor Windows PowerShell-syntaxis.</span><span class="sxs-lookup"><span data-stu-id="57f1f-114">Because the filter used in this command is a WMI filter, it uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="57f1f-115">In plaats daarvan:</span><span class="sxs-lookup"><span data-stu-id="57f1f-115">Instead,:</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

<span data-ttu-id="57f1f-116">Houd er rekening mee dat WQL-query's vaak gebruik tekens, zoals spaties of gelijk tekens, die een speciale betekenis in Windows PowerShell hebben.</span><span class="sxs-lookup"><span data-stu-id="57f1f-116">Note that WQL queries frequently use characters, such as spaces or equal signs, that have a special meaning in Windows PowerShell.</span></span> <span data-ttu-id="57f1f-117">Daarom is het verstandig om te altijd de waarde van de parameter Filter plaats tussen aanhalingstekens.</span><span class="sxs-lookup"><span data-stu-id="57f1f-117">For this reason, it is prudent to always enclose the value of the Filter parameter in quotation marks.</span></span> <span data-ttu-id="57f1f-118">U kunt ook de Windows PowerShell-escape-teken, een backtick (\\`), hoewel deze mogelijk niet betere leesbaarheid.</span><span class="sxs-lookup"><span data-stu-id="57f1f-118">You can also use the Windows PowerShell escape character, a backtick (\\`), although it may not improve readability.</span></span> <span data-ttu-id="57f1f-119">De volgende opdracht komt overeen met de vorige opdracht en dezelfde resultaten retourneert, maar de backtick gebruikt als escapeteken voor speciale tekens, in plaats van de hele filtertekenreeks aan te geven.</span><span class="sxs-lookup"><span data-stu-id="57f1f-119">The following command is equivalent to the previous command and returns the same results, but uses the backtick to escape special characters, instead of quoting the entire filter string.</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

<span data-ttu-id="57f1f-120">U kunt alleen de eigenschappen die u interesseren gebruiken de parameter Property van de opmaak-cmdlets voor een lijst met de gewenste eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="57f1f-120">To list only the properties that interest you, use the Property parameter of the formatting cmdlets to list the desired properties.</span></span>

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

<span data-ttu-id="57f1f-121">Ten slotte vinden alleen de namen van de geïnstalleerde toepassingen, een eenvoudige **indeling hele** instructie vereenvoudigt de uitvoer:</span><span class="sxs-lookup"><span data-stu-id="57f1f-121">Finally, to find only the names of installed applications, a simple **Format-Wide** statement simplifies the output:</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

<span data-ttu-id="57f1f-122">Hoewel we nu verschillende manieren om te kijken naar toepassingen die het Windows-installatieprogramma voor installatie gebruikt hebben, hebben we niet beschouwd als andere toepassingen.</span><span class="sxs-lookup"><span data-stu-id="57f1f-122">Although we now have several ways to look at applications that used the Windows Installer for installation, we have not considered other applications.</span></span> <span data-ttu-id="57f1f-123">Omdat hun verwijderprogramma meest standaardtoepassingen bij Windows registreren, kunnen we werken met die lokaal door ze te zoeken in het Windows-register.</span><span class="sxs-lookup"><span data-stu-id="57f1f-123">Because most standard applications register their uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span>

### <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="57f1f-124">Alle kan worden verwijderd toepassingen weergeven</span><span class="sxs-lookup"><span data-stu-id="57f1f-124">Listing All Uninstallable Applications</span></span>
<span data-ttu-id="57f1f-125">Hoewel er geen gegarandeerde manier om te zoeken naar elke toepassing die op een systeem, is het mogelijk om alle programma's met aanbiedingen weergegeven in het dialoogvenster een programma verwijderen of vinden.</span><span class="sxs-lookup"><span data-stu-id="57f1f-125">Although there is no guaranteed way to find every application on a system, it is possible to find all programs with listings displayed in the Add or Remove Programs dialog box.</span></span> <span data-ttu-id="57f1f-126">Toevoegen of software vindt deze toepassingen in de volgende registersleutel:</span><span class="sxs-lookup"><span data-stu-id="57f1f-126">Add or Remove Programs finds these applications in the following registry key:</span></span>

<span data-ttu-id="57f1f-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\verwijderen**.</span><span class="sxs-lookup"><span data-stu-id="57f1f-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span></span>

<span data-ttu-id="57f1f-128">We kunnen deze sleutel om te zoeken naar toepassingen onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="57f1f-128">We can also examine this key to find applications.</span></span> <span data-ttu-id="57f1f-129">Om het gemakkelijker om weer te geven van de sleutel verwijderen, kunnen we een Windows PowerShell-station toewijzen aan deze registerlocatie:</span><span class="sxs-lookup"><span data-stu-id="57f1f-129">To make it easier to view the Uninstall key, we can map a Windows PowerShell drive to this registry location:</span></span>

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall    

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> <span data-ttu-id="57f1f-130">De **HKLM:** station is toegewezen aan de hoofdmap van **HKEY_LOCAL_MACHINE**, zodat we dat station in het pad naar de sleutel verwijderen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="57f1f-130">The **HKLM:** drive is mapped to the root of **HKEY_LOCAL_MACHINE**, so we used that drive in the path to the Uninstall key.</span></span> <span data-ttu-id="57f1f-131">In plaats van **HKLM:** we kan het registerpad hebt opgegeven met behulp van **HKLM** of **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="57f1f-131">Instead of **HKLM:** we could have specified the registry path by using either **HKLM** or **HKEY_LOCAL_MACHINE**.</span></span> <span data-ttu-id="57f1f-132">Het voordeel van een bestaand register-station is dat we invullen van de tabbladen gebruiken kunt om in te vullen de namen van sleutels, zodat we niet hoeft te geven.</span><span class="sxs-lookup"><span data-stu-id="57f1f-132">The advantage of using an existing registry drive is that we can use tab-completion to fill in the keys names, so we do not need to type them.</span></span>

<span data-ttu-id="57f1f-133">We hebben nu een station met de naam 'Verwijderen' die kan worden gebruikt om snel en gemakkelijk zoekt installaties van toepassingen.</span><span class="sxs-lookup"><span data-stu-id="57f1f-133">We now have a drive named "Uninstall" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="57f1f-134">We kunnen het aantal geïnstalleerde toepassingen zoeken door het aantal registersleutels in het verwijderen te tellen: Windows PowerShell-station:</span><span class="sxs-lookup"><span data-stu-id="57f1f-134">We can find the number of installed applications by counting the number of registry keys in the Uninstall: Windows PowerShell drive:</span></span>

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="57f1f-135">We kunnen deze lijst van toepassingen meer zoeken met behulp van tal van technieken vanaf **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="57f1f-135">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="57f1f-136">Een lijst met toepassingen ophalen en opslaan in de **$UninstallableApplications** variabele, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="57f1f-136">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> <span data-ttu-id="57f1f-137">We langdurige variabele hier een naam voor de duidelijkheid gebruiken.</span><span class="sxs-lookup"><span data-stu-id="57f1f-137">We are using a lengthy variable name here for clarity.</span></span> <span data-ttu-id="57f1f-138">Er is geen reden lang namen gebruiken in het werkelijke gebruik.</span><span class="sxs-lookup"><span data-stu-id="57f1f-138">In actual use, there is no reason to use long names.</span></span> <span data-ttu-id="57f1f-139">Hoewel u tabblad voltooiing voor namen van variabelen gebruiken kunt, kunt u ook 1-2 teken namen voor snelheid.</span><span class="sxs-lookup"><span data-stu-id="57f1f-139">Although you can use tab-completion for variable names, you can also use 1-2 character names for speed.</span></span> <span data-ttu-id="57f1f-140">Langer, beschrijvende namen zijn handig als u code opnieuw kunnen worden gebruikt ontwikkelt.</span><span class="sxs-lookup"><span data-stu-id="57f1f-140">Longer, descriptive names are most useful when you are developing code for reuse.</span></span>

<span data-ttu-id="57f1f-141">Gebruik de methode GetValue van de registersleutels zodat de waarden van de registervermeldingen in de registersleutels onder verwijderen.</span><span class="sxs-lookup"><span data-stu-id="57f1f-141">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="57f1f-142">De waarde van de methode is de naam van het register-item.</span><span class="sxs-lookup"><span data-stu-id="57f1f-142">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="57f1f-143">Bijvoorbeeld, om de namen weergegeven van toepassingen in de sleutel verwijderen, gebruik de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="57f1f-143">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```
PS> Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue("DisplayName") }
```

<span data-ttu-id="57f1f-144">Er is geen garantie dat deze waarden uniek zijn.</span><span class="sxs-lookup"><span data-stu-id="57f1f-144">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="57f1f-145">In het volgende voorbeeld worden twee geïnstalleerde items weergegeven als 'Windows Media Encoder 9 Series':</span><span class="sxs-lookup"><span data-stu-id="57f1f-145">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

### <a name="installing-applications"></a><span data-ttu-id="57f1f-146">Installatie van toepassingen</span><span class="sxs-lookup"><span data-stu-id="57f1f-146">Installing Applications</span></span>
<span data-ttu-id="57f1f-147">U kunt de **Win32_Product** klasse voor het installeren van Windows Installer-pakketten extern of lokaal.</span><span class="sxs-lookup"><span data-stu-id="57f1f-147">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="57f1f-148">Op Windows Vista, Windows Server 2008 en nieuwere versies van Windows, een toepassing te installeren, moet u beginnen Windows PowerShell met de optie 'Als administrator uitvoeren'.</span><span class="sxs-lookup"><span data-stu-id="57f1f-148">On Windows Vista, Windows Server 2008, and later versions of Windows, to install an application, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="57f1f-149">Bij het op afstand installeren via een netwerkpad Universal Naming Convention (UNC) opgeven het pad naar het MSI-pakket, omdat het WMI-subsysteem niet paden met Windows PowerShell begrijpt.</span><span class="sxs-lookup"><span data-stu-id="57f1f-149">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand Windows PowerShell paths.</span></span> <span data-ttu-id="57f1f-150">Bijvoorbeeld, zich in de netwerkshare voor het installeren van het pakket NewPackage.msi \\ \\AppServ\\dsp op de externe computer PC01, typ de volgende opdracht achter de Windows PowerShell-prompt:</span><span class="sxs-lookup"><span data-stu-id="57f1f-150">For example, to install the NewPackage.msi package located in the network share \\\\AppServ\\dsp on the remote computer PC01, type the following command at the Windows PowerShell prompt:</span></span>

```
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq "Win32_Product"}).Install(\\AppSrv\dsp\NewPackage.msi)
```

<span data-ttu-id="57f1f-151">Toepassingen die geen van Windows Installer-technologie gebruikmaken misschien toepassingsspecifieke methoden beschikbaar voor automatische implementatie.</span><span class="sxs-lookup"><span data-stu-id="57f1f-151">Applications that do not use Windows Installer technology may have application-specific methods available for automated deployment.</span></span> <span data-ttu-id="57f1f-152">Raadpleeg de documentatie voor de toepassing om te bepalen of er een methode voor het automatiseren van de implementatie is, of neem contact op ondersteuningssysteem van de leverancier van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="57f1f-152">To determine whether there is a method for deployment automation, check the documentation for the application or consult the application vendor's support system.</span></span> <span data-ttu-id="57f1f-153">In sommige gevallen, zelfs als de toepassing voor het automatiseren van de installatie is niet specifiek ontwerp-leverancier van de toepassing de fabrikant van de software installer mogelijk bepaalde technieken voor automatisering.</span><span class="sxs-lookup"><span data-stu-id="57f1f-153">In some cases, even if the application vendor did not specifically design the application for installation automation, the installer software manufacturer may have some techniques for automation.</span></span>

### <a name="removing-applications"></a><span data-ttu-id="57f1f-154">Toepassingen verwijderen</span><span class="sxs-lookup"><span data-stu-id="57f1f-154">Removing Applications</span></span>
<span data-ttu-id="57f1f-155">Verwijderen van een Windows Installer-pakket met Windows PowerShell werkt op ongeveer dezelfde manier als een pakket installeert.</span><span class="sxs-lookup"><span data-stu-id="57f1f-155">Removing a Windows Installer package by using Windows PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="57f1f-156">Hier volgt een voorbeeld waarin selecteert het pakket te verwijderen op basis van de naam; in sommige gevallen kan zijn gemakkelijker te filteren met de **id-nummer**:</span><span class="sxs-lookup"><span data-stu-id="57f1f-156">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

<span data-ttu-id="57f1f-157">Verwijderen van andere toepassingen is niet zo eenvoudig, zelfs wanneer lokaal wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="57f1f-157">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="57f1f-158">We kunnen de opdrachtregel verwijderen tekenreeksen vinden voor deze toepassingen door uit te pakken de **UninstallString** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="57f1f-158">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span> <span data-ttu-id="57f1f-159">Deze methode werkt voor Windows Installer-toepassingen en oudere programma's die wordt weergegeven onder de sleutel verwijderen:</span><span class="sxs-lookup"><span data-stu-id="57f1f-159">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue("UninstallString") }
```

<span data-ttu-id="57f1f-160">U kunt de uitvoer als u dit wilt filteren op de weergavenaam:</span><span class="sxs-lookup"><span data-stu-id="57f1f-160">You can filter the output by the display name, if you like:</span></span>

```
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -like "Win*"} | ForEach-Object -Process { $_.GetValue("UninstallString") }
```

<span data-ttu-id="57f1f-161">Maar deze tekenreeksen mogelijk niet direct toegankelijk is vanaf de Windows PowerShell-prompt zonder enige aanpassing.</span><span class="sxs-lookup"><span data-stu-id="57f1f-161">However, these strings may not be directly usable from the Windows PowerShell prompt without some modification.</span></span>

### <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="57f1f-162">Een upgrade van Windows Installer-toepassingen</span><span class="sxs-lookup"><span data-stu-id="57f1f-162">Upgrading Windows Installer Applications</span></span>
<span data-ttu-id="57f1f-163">Om een toepassing een upgrade uitvoert, moet u de naam van de toepassing en het pad op het updatepakket van een toepassing weet.</span><span class="sxs-lookup"><span data-stu-id="57f1f-163">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="57f1f-164">Deze informatie kunt u een toepassing met een enkel Windows PowerShell-opdracht upgraden:</span><span class="sxs-lookup"><span data-stu-id="57f1f-164">With that information, you can upgrade an application with a single Windows PowerShell command:</span></span>

```
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```

