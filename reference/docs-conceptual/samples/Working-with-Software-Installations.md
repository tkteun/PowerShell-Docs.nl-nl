---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met software-installaties werken
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: bb97ad37c4295351c0fc2e3c6e1209c8dd673f06
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404614"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="9a602-103">Met software-installaties werken</span><span class="sxs-lookup"><span data-stu-id="9a602-103">Working with Software Installations</span></span>

<span data-ttu-id="9a602-104">Toepassingen die zijn ontworpen voor het gebruik van Windows Installer is toegankelijk via WMI van **Win32_Product** klasse, maar niet alle toepassingen in gebruik vandaag nog gebruik van het Windows-installatieprogramma.</span><span class="sxs-lookup"><span data-stu-id="9a602-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span> <span data-ttu-id="9a602-105">Omdat het installatieprogramma voor Windows de breedste scala aan standard technieken biedt voor het werken met installeerbare toepassingen, we richten ons voornamelijk aan deze toepassingen.</span><span class="sxs-lookup"><span data-stu-id="9a602-105">Because the Windows Installer provides the widest range of standard techniques for working with installable applications, we will focus primarily on those applications.</span></span> <span data-ttu-id="9a602-106">Toepassingen die gebruikmaken van routines alternatieve instellen in het algemeen niet beheerd door de Windows-installatieservice.</span><span class="sxs-lookup"><span data-stu-id="9a602-106">Applications that use alternate setup routines will generally not be managed by the Windows Installer.</span></span> <span data-ttu-id="9a602-107">Specifieke technieken voor het werken met deze toepassingen, is afhankelijk van de installer-software en de beslissingen die worden genomen door de ontwikkelaar van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="9a602-107">Specific techniques for working with those applications will depend on the installer software and decisions made by the application developer.</span></span>

> [!NOTE]
> <span data-ttu-id="9a602-108">Toepassingen die zijn geïnstalleerd door de toepassingsbestanden zijn gekopieerd naar de computer meestal kunnen niet worden beheerd met behulp van technieken die worden besproken hier.</span><span class="sxs-lookup"><span data-stu-id="9a602-108">Applications that are installed by copying the application files to the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="9a602-109">U kunt deze toepassingen als uitvoerbare bestanden en mappen beheren met behulp van de technieken beschreven in de sectie 'Werken met bestanden en mappen'.</span><span class="sxs-lookup"><span data-stu-id="9a602-109">You can manage these applications as files and folders by using the techniques discussed in the "Working With Files and Folders" section.</span></span>

### <a name="listing-windows-installer-applications"></a><span data-ttu-id="9a602-110">Windows Installer-toepassingen weergeven</span><span class="sxs-lookup"><span data-stu-id="9a602-110">Listing Windows Installer Applications</span></span>

<span data-ttu-id="9a602-111">Als u de toepassingen zijn geïnstalleerd met de Windows Installer op een lokale of externe systeem, gebruik de volgende eenvoudige WMI-query:</span><span class="sxs-lookup"><span data-stu-id="9a602-111">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

<span data-ttu-id="9a602-112">Wilt weergeven alle van de eigenschappen van het object Win32_Product bij het weergeven, gebruikt u de parameter eigenschappen van de opmaak-cmdlets, zoals de cmdlet lijst met een waarde van \* (alle).</span><span class="sxs-lookup"><span data-stu-id="9a602-112">To display all of the properties of the Win32_Product object to the display, use the Properties parameter of the formatting cmdlets, such as the Format-List cmdlet, with a value of \* (all).</span></span>

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

<span data-ttu-id="9a602-113">Of u kunt de **Get-WmiObject Filter** parameter selecteren alleen Microsoft .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="9a602-113">Or, you could use the **Get-WmiObject Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="9a602-114">Omdat het filter gebruikt in deze opdracht een WMI-filter is, wordt de syntaxis van de WMI Query Language (WQL), niet Windows PowerShell-syntaxis.</span><span class="sxs-lookup"><span data-stu-id="9a602-114">Because the filter used in this command is a WMI filter, it uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="9a602-115">In plaats daarvan:</span><span class="sxs-lookup"><span data-stu-id="9a602-115">Instead,:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

<span data-ttu-id="9a602-116">Houd er rekening mee dat WQL-query's regelmatig gebruik tekens, zoals spaties of gelijktekens, waarvoor een speciale betekenis in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a602-116">Note that WQL queries frequently use characters, such as spaces or equal signs, that have a special meaning in Windows PowerShell.</span></span> <span data-ttu-id="9a602-117">Daarom is het verstandig om te altijd de waarde van de filterparameter tussen aanhalingstekens plaatsen.</span><span class="sxs-lookup"><span data-stu-id="9a602-117">For this reason, it is prudent to always enclose the value of the Filter parameter in quotation marks.</span></span> <span data-ttu-id="9a602-118">U kunt ook de Windows PowerShell-escape-teken, een backtick (\`), hoewel de leesbaarheid niet kan worden verbeterd.</span><span class="sxs-lookup"><span data-stu-id="9a602-118">You can also use the Windows PowerShell escape character, a backtick (\`), although it may not improve readability.</span></span> <span data-ttu-id="9a602-119">De volgende opdracht is gelijk aan de vorige opdracht en retourneert hetzelfde resultaat, maar de backtick gebruikt als escapeteken voor speciale tekens bevatten, in plaats van de aanhalingstekens voor de hele filtertekenreeks.</span><span class="sxs-lookup"><span data-stu-id="9a602-119">The following command is equivalent to the previous command and returns the same results, but uses the backtick to escape special characters, instead of quoting the entire filter string.</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

<span data-ttu-id="9a602-120">Als u alleen de eigenschappen die u interesseren, door de parameter eigenschap van de opmaak-cmdlets te gebruiken om de gewenste eigenschappen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="9a602-120">To list only the properties that interest you, use the Property parameter of the formatting cmdlets to list the desired properties.</span></span>

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

<span data-ttu-id="9a602-121">Ten slotte, om te zoeken naar alleen de namen van de geïnstalleerde toepassingen, een eenvoudige **indeling hele** instructie vereenvoudigt de uitvoer:</span><span class="sxs-lookup"><span data-stu-id="9a602-121">Finally, to find only the names of installed applications, a simple **Format-Wide** statement simplifies the output:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

<span data-ttu-id="9a602-122">Hoewel we nu verschillende manieren om te kijken naar toepassingen die het Windows-installatieprogramma voor de installatie gebruikt hebben, hebben we niet beschouwd als andere toepassingen.</span><span class="sxs-lookup"><span data-stu-id="9a602-122">Although we now have several ways to look at applications that used the Windows Installer for installation, we have not considered other applications.</span></span> <span data-ttu-id="9a602-123">Omdat de meeste standaard toepassingen registreren hun verwijderprogramma bij Windows, die we kunnen werken met die lokaal door ze te vinden in het Windows-register.</span><span class="sxs-lookup"><span data-stu-id="9a602-123">Because most standard applications register their uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span>

### <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="9a602-124">Lijst van alle toepassingen die kan worden verwijderd</span><span class="sxs-lookup"><span data-stu-id="9a602-124">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="9a602-125">Hoewel er geen gegarandeerde manier om te vinden van elke toepassing op een systeem is, is het mogelijk om te zoeken van alle programma's met aanbiedingen weergegeven in het dialoogvenster toevoegen of verwijderen van programma's.</span><span class="sxs-lookup"><span data-stu-id="9a602-125">Although there is no guaranteed way to find every application on a system, it is possible to find all programs with listings displayed in the Add or Remove Programs dialog box.</span></span> <span data-ttu-id="9a602-126">Toevoegen of verwijderen van programma's vindt deze toepassingen in de volgende registersleutel:</span><span class="sxs-lookup"><span data-stu-id="9a602-126">Add or Remove Programs finds these applications in the following registry key:</span></span>

<span data-ttu-id="9a602-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\verwijderen**.</span><span class="sxs-lookup"><span data-stu-id="9a602-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span></span>

<span data-ttu-id="9a602-128">We kunnen ook naar de deze sleutel om te zoeken naar toepassingen.</span><span class="sxs-lookup"><span data-stu-id="9a602-128">We can also examine this key to find applications.</span></span> <span data-ttu-id="9a602-129">Als u wilt maken het gemakkelijker om de sleutel verwijderen weer te geven, kunnen we een Windows PowerShell-station worden toegewezen aan deze registerlocatie:</span><span class="sxs-lookup"><span data-stu-id="9a602-129">To make it easier to view the Uninstall key, we can map a Windows PowerShell drive to this registry location:</span></span>

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> <span data-ttu-id="9a602-130">De **HKLM:** stationsaanduiding is toegewezen aan de hoofdmap van **HKEY_LOCAL_MACHINE**, zodat we dat station in het pad naar de sleutel verwijderen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9a602-130">The **HKLM:** drive is mapped to the root of **HKEY_LOCAL_MACHINE**, so we used that drive in the path to the Uninstall key.</span></span> <span data-ttu-id="9a602-131">In plaats van **HKLM:** we kan hebt opgegeven het registerpad met behulp van **HKLM** of **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="9a602-131">Instead of **HKLM:** we could have specified the registry path by using either **HKLM** or **HKEY_LOCAL_MACHINE**.</span></span> <span data-ttu-id="9a602-132">Het voordeel van het gebruik van een bestaand register-station is dat tabvoltooiing kunnen worden gebruikt om in te vullen in de namen van de sleutels, zodat we niet zelf hoeft te geven.</span><span class="sxs-lookup"><span data-stu-id="9a602-132">The advantage of using an existing registry drive is that we can use tab-completion to fill in the keys names, so we do not need to type them.</span></span>

<span data-ttu-id="9a602-133">We hebben nu een station met de naam 'Verwijderen', die kan worden gebruikt om snel en gemakkelijk zoeken voor installaties van toepassingen.</span><span class="sxs-lookup"><span data-stu-id="9a602-133">We now have a drive named "Uninstall" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="9a602-134">Er vindt het aantal geïnstalleerde toepassingen door het aantal registersleutels in de verwijdering te tellen: Windows PowerShell-station:</span><span class="sxs-lookup"><span data-stu-id="9a602-134">We can find the number of installed applications by counting the number of registry keys in the Uninstall: Windows PowerShell drive:</span></span>

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="9a602-135">We kunnen deze lijst met toepassingen verder zoeken met behulp van verschillende technieken, beginnen met **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="9a602-135">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="9a602-136">Voor het ophalen van een lijst met toepassingen en slaat u ze in de **$UninstallableApplications** variabele, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="9a602-136">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> <span data-ttu-id="9a602-137">We gebruiken een langdurige variabelenaam voor de duidelijkheid.</span><span class="sxs-lookup"><span data-stu-id="9a602-137">We are using a lengthy variable name here for clarity.</span></span> <span data-ttu-id="9a602-138">Werkelijke gebruikt is er geen reden lange namen te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="9a602-138">In actual use, there is no reason to use long names.</span></span> <span data-ttu-id="9a602-139">Hoewel u tabvoltooiing voor namen van variabelen gebruiken kunt, kunt u de namen van 1-2-teken voor snelheid ook gebruiken.</span><span class="sxs-lookup"><span data-stu-id="9a602-139">Although you can use tab-completion for variable names, you can also use 1-2 character names for speed.</span></span> <span data-ttu-id="9a602-140">Langer, beschrijvende namen zijn handig als u code voor hergebruik ontwikkelt.</span><span class="sxs-lookup"><span data-stu-id="9a602-140">Longer, descriptive names are most useful when you are developing code for reuse.</span></span>

<span data-ttu-id="9a602-141">Als de waarden van de registervermeldingen in de registersleutels onder verwijderen weergeven, gebruikt u de GetValue-methode van de registersleutels.</span><span class="sxs-lookup"><span data-stu-id="9a602-141">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="9a602-142">De waarde van de methode is de naam van het register-item.</span><span class="sxs-lookup"><span data-stu-id="9a602-142">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="9a602-143">Bijvoorbeeld, als u zoekt de weergavenamen van toepassingen in de sleutel verwijderen, gebruik de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="9a602-143">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="9a602-144">Er is geen garantie dat deze waarden uniek zijn.</span><span class="sxs-lookup"><span data-stu-id="9a602-144">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="9a602-145">In het volgende voorbeeld worden twee geïnstalleerde items weergegeven als 'Windows Media Encoder 9 Series':</span><span class="sxs-lookup"><span data-stu-id="9a602-145">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

### <a name="installing-applications"></a><span data-ttu-id="9a602-146">Installeren van toepassingen</span><span class="sxs-lookup"><span data-stu-id="9a602-146">Installing Applications</span></span>

<span data-ttu-id="9a602-147">U kunt de **Win32_Product** klasse voor het installeren van Windows Installer-pakketten, extern of lokaal.</span><span class="sxs-lookup"><span data-stu-id="9a602-147">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="9a602-148">Op Windows Vista, Windows Server 2008 en latere versies van Windows, voor het installeren van een toepassing, moet u beginnen Windows PowerShell met de optie "Uitvoeren als administrator".</span><span class="sxs-lookup"><span data-stu-id="9a602-148">On Windows Vista, Windows Server 2008, and later versions of Windows, to install an application, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="9a602-149">Bij de installatie op afstand, moet u een netwerkpad Universal Naming Convention (UNC) gebruiken om op te geven van het pad naar het MSI-pakket, omdat het WMI-subsysteem heeft niet informatie over Windows PowerShell-paden.</span><span class="sxs-lookup"><span data-stu-id="9a602-149">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand Windows PowerShell paths.</span></span> <span data-ttu-id="9a602-150">Bijvoorbeeld, zich in de netwerkshare voor het installeren van het pakket NewPackage.msi \\ \\AppServ\\dsp op de externe computer PC01, typt u de volgende opdracht achter de Windows PowerShell-prompt:</span><span class="sxs-lookup"><span data-stu-id="9a602-150">For example, to install the NewPackage.msi package located in the network share \\\\AppServ\\dsp on the remote computer PC01, type the following command at the Windows PowerShell prompt:</span></span>

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

<span data-ttu-id="9a602-151">Toepassingen die geen gebruik maken van Windows Installer-technologie hebben toepassingsspecifieke methoden beschikbaar voor automatische implementatie.</span><span class="sxs-lookup"><span data-stu-id="9a602-151">Applications that do not use Windows Installer technology may have application-specific methods available for automated deployment.</span></span> <span data-ttu-id="9a602-152">Raadpleeg de documentatie voor de toepassing om te bepalen of er een methode voor het automatiseren van de implementatie is, of neem contact op ondersteuning van system van de leverancier van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="9a602-152">To determine whether there is a method for deployment automation, check the documentation for the application or consult the application vendor's support system.</span></span> <span data-ttu-id="9a602-153">In sommige gevallen, zelfs als de leverancier van de toepassing is niet specifiek de toepassing ontwerpen voor installatie-automatisering, de fabrikant van de software installer mogelijk bepaalde technieken voor automation.</span><span class="sxs-lookup"><span data-stu-id="9a602-153">In some cases, even if the application vendor did not specifically design the application for installation automation, the installer software manufacturer may have some techniques for automation.</span></span>

### <a name="removing-applications"></a><span data-ttu-id="9a602-154">Toepassingen verwijderen</span><span class="sxs-lookup"><span data-stu-id="9a602-154">Removing Applications</span></span>

<span data-ttu-id="9a602-155">Verwijderen van een Windows Installer-pakket met behulp van Windows PowerShell werkt op ongeveer dezelfde manier als een pakket installeert.</span><span class="sxs-lookup"><span data-stu-id="9a602-155">Removing a Windows Installer package by using Windows PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="9a602-156">Hier volgt een voorbeeld waarin selecteert het pakket te verwijderen op basis van de naam; in sommige gevallen kan het eenvoudiger om te filteren met zijn de **id-nummer**:</span><span class="sxs-lookup"><span data-stu-id="9a602-156">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

<span data-ttu-id="9a602-157">Verwijderen van andere toepassingen is niet zo eenvoudig, zelfs wanneer lokaal uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9a602-157">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="9a602-158">We kunnen de opdrachtregel verwijderen tekenreeksen voor deze toepassingen vinden door te extraheren de **UninstallString** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="9a602-158">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span> <span data-ttu-id="9a602-159">Deze methode werkt voor Windows Installer-toepassingen en oudere programma's die wordt weergegeven onder de sleutel verwijderen:</span><span class="sxs-lookup"><span data-stu-id="9a602-159">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="9a602-160">U kunt desgewenst de uitvoer filteren op de weergavenaam:</span><span class="sxs-lookup"><span data-stu-id="9a602-160">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="9a602-161">Deze tekenreeksen kunnen echter niet worden rechtstreeks vanuit de Windows PowerShell-prompt zonder enige wijziging gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9a602-161">However, these strings may not be directly usable from the Windows PowerShell prompt without some modification.</span></span>

### <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="9a602-162">Upgraden van Windows Installer-toepassingen</span><span class="sxs-lookup"><span data-stu-id="9a602-162">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="9a602-163">Als u een toepassing bijwerken, moet u de naam van de toepassing en het pad kennen op het updatepakket van toepassing.</span><span class="sxs-lookup"><span data-stu-id="9a602-163">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="9a602-164">Met deze informatie kunt u een toepassing met een enkel Windows PowerShell-opdracht bijwerken:</span><span class="sxs-lookup"><span data-stu-id="9a602-164">With that information, you can upgrade an application with a single Windows PowerShell command:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```