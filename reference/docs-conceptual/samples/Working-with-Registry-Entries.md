---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met registervermeldingen werken
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404461"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="1e977-103">Met registervermeldingen werken</span><span class="sxs-lookup"><span data-stu-id="1e977-103">Working with Registry Entries</span></span>

<span data-ttu-id="1e977-104">Omdat de registervermeldingen zijn eigenschappen van sleutels en, als zodanig kunnen niet worden rechtstreeks gebladerd, moet een lichtjes andere benadering nemen bij het werken met hen.</span><span class="sxs-lookup"><span data-stu-id="1e977-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="1e977-105">Registervermeldingen van aanbieding</span><span class="sxs-lookup"><span data-stu-id="1e977-105">Listing Registry Entries</span></span>

<span data-ttu-id="1e977-106">Er zijn veel verschillende manieren om te onderzoeken registervermeldingen.</span><span class="sxs-lookup"><span data-stu-id="1e977-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="1e977-107">De eenvoudigste manier is om op te halen van de namen van eigenschappen die zijn gekoppeld aan een sleutel.</span><span class="sxs-lookup"><span data-stu-id="1e977-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="1e977-108">Bijvoorbeeld, om te zien van de namen van de vermeldingen in de registersleutel **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, gebruikt u **Get-Item** .</span><span class="sxs-lookup"><span data-stu-id="1e977-108">For example, to see the names of the entries in the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, use **Get-Item**.</span></span> <span data-ttu-id="1e977-109">Registersleutels hebben een eigenschap met de algemene naam van 'Eigenschap' die een lijst met vermeldingen in de sleutel is.</span><span class="sxs-lookup"><span data-stu-id="1e977-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span> <span data-ttu-id="1e977-110">De volgende opdracht uit de eigenschap selecteert en de items wordt uitgebreid zodat ze worden weergegeven in een lijst:</span><span class="sxs-lookup"><span data-stu-id="1e977-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="1e977-111">U kunt de registervermeldingen weergeven in een beter leesbare vorm, met **Get-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="1e977-111">To view the registry entries in a more readable form, use **Get-ItemProperty**:</span></span>

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

<span data-ttu-id="1e977-112">De Windows PowerShell-eigenschappen voor de sleutel worden alle voorafgegaan door 'PS', zoals **PSPath**, **PSParentPath**, **PSChildName**, en **PSProvider** .</span><span class="sxs-lookup"><span data-stu-id="1e977-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="1e977-113">U kunt de "**.**" notatie voor verwijzen naar de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="1e977-113">You can use the "**.**" notation for referring to the current location.</span></span> <span data-ttu-id="1e977-114">U kunt **locatie instellen** wijzigen in de **CurrentVersion** container registry eerste:</span><span class="sxs-lookup"><span data-stu-id="1e977-114">You can use **Set-Location** to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="1e977-115">U kunt ook kunt u de ingebouwde HKLM PSDrive met **locatie instellen**:</span><span class="sxs-lookup"><span data-stu-id="1e977-115">Alternatively, you can use the built-in HKLM PSDrive with **Set-Location**:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="1e977-116">Vervolgens kunt u de '**.**"notatie voor de huidige locatie om de eigenschappen zonder op te geven van een volledig pad:</span><span class="sxs-lookup"><span data-stu-id="1e977-116">You can then use the "**.**" notation for the current location to list the properties without specifying a full path:</span></span>

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="1e977-117">Pad uitbreiding werkt hetzelfde als in het bestandssysteem, zodat u vanaf deze locatie krijgt u de **ItemProperty** aanbieding voor **HKLM:\\SOFTWARE\\Microsoft\\Windows \\Help** met behulp van **Get-ItemProperty-pad... \\Help**.</span><span class="sxs-lookup"><span data-stu-id="1e977-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** by using **Get-ItemProperty -Path ..\\Help**.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="1e977-118">Een enkel register-item ophalen</span><span class="sxs-lookup"><span data-stu-id="1e977-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="1e977-119">Als u ophalen van een bepaalde vermelding in een registersleutel wilt, kunt u een van verschillende mogelijke methoden.</span><span class="sxs-lookup"><span data-stu-id="1e977-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="1e977-120">In dit voorbeeld wordt gezocht naar de waarde van **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="1e977-120">This example finds the value of **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span>

<span data-ttu-id="1e977-121">Met behulp van **Get-ItemProperty**, gebruikt u de **pad** parameter opgeven voor de naam van de sleutel en de **naam** parameter opgeven voor de naam van de **DevicePath** vermelding.</span><span class="sxs-lookup"><span data-stu-id="1e977-121">Using **Get-ItemProperty**, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="1e977-122">Met deze opdracht retourneert de standaardeigenschappen van Windows PowerShell, evenals de **DevicePath** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="1e977-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="1e977-123">Hoewel **Get-ItemProperty** heeft **Filter**, **opnemen**, en **uitsluiten** parameters, ze om te filteren op naam van de eigenschap kunnen niet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1e977-123">Although **Get-ItemProperty** has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="1e977-124">Deze parameters verwijzen naar registersleutels: item paden zijn, en niet de registervermeldingen: welke eigenschappen van het item zijn.</span><span class="sxs-lookup"><span data-stu-id="1e977-124">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="1e977-125">Een andere optie is het gebruik van het hulpprogramma Reg.exe vanaf de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="1e977-125">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="1e977-126">Typ voor help met reg.exe **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="1e977-126">For help with reg.exe, type **reg.exe /?**</span></span> <span data-ttu-id="1e977-127">bij een opdrachtprompt.</span><span class="sxs-lookup"><span data-stu-id="1e977-127">at a command prompt.</span></span> <span data-ttu-id="1e977-128">Als u de vermelding DevicePath zoekt, gebruikt u reg.exe zoals wordt weergegeven in de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="1e977-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="1e977-129">U kunt ook de **WshShell COM** object ook te vinden van sommige registervermeldingen, hoewel deze methode niet werkt met grote binaire gegevens of met de namen van de Register-vermeldingen die tekens zoals bevatten '\\').</span><span class="sxs-lookup"><span data-stu-id="1e977-129">You can also use the **WshShell COM** object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="1e977-130">Naam van de eigenschap toevoegen aan het pad van het item met een \\ scheidingsteken:</span><span class="sxs-lookup"><span data-stu-id="1e977-130">Append the property name to the item path with a \\ separator:</span></span>

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="1e977-131">Het maken van nieuwe registervermeldingen</span><span class="sxs-lookup"><span data-stu-id="1e977-131">Creating New Registry Entries</span></span>

<span data-ttu-id="1e977-132">Een nieuwe vermelding met de naam 'PowerShellPath' toevoegen aan de **CurrentVersion** , sleutelgebruik **New-ItemProperty** met het pad naar de sleutel, naam van de vermelding en de waarde van het item.</span><span class="sxs-lookup"><span data-stu-id="1e977-132">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use **New-ItemProperty** with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="1e977-133">In dit voorbeeld wordt de waarde van de Windows PowerShell-variabele duurt **$PSHome**, waarin het pad naar de installatiemap voor Windows PowerShell wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="1e977-133">For this example, we will take the value of the Windows PowerShell variable **$PSHome**, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="1e977-134">U kunt het nieuwe item toevoegen aan de sleutel met behulp van de volgende opdracht en de opdracht retourneert ook informatie over het nieuwe item:</span><span class="sxs-lookup"><span data-stu-id="1e977-134">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="1e977-135">De **%d{PropertyType/** moet de naam van een **Microsoft.Win32.RegistryValueKind** lid van de opsomming van de volgende tabel:</span><span class="sxs-lookup"><span data-stu-id="1e977-135">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="1e977-136">%D{PropertyType/ waarde</span><span class="sxs-lookup"><span data-stu-id="1e977-136">PropertyType Value</span></span>|<span data-ttu-id="1e977-137">Betekenis</span><span class="sxs-lookup"><span data-stu-id="1e977-137">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="1e977-138">Binair</span><span class="sxs-lookup"><span data-stu-id="1e977-138">Binary</span></span>|<span data-ttu-id="1e977-139">Binaire gegevens</span><span class="sxs-lookup"><span data-stu-id="1e977-139">Binary data</span></span>|
|<span data-ttu-id="1e977-140">DWord</span><span class="sxs-lookup"><span data-stu-id="1e977-140">DWord</span></span>|<span data-ttu-id="1e977-141">Een getal dat is een geldige UInt32</span><span class="sxs-lookup"><span data-stu-id="1e977-141">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="1e977-142">ExpandString</span><span class="sxs-lookup"><span data-stu-id="1e977-142">ExpandString</span></span>|<span data-ttu-id="1e977-143">Een tekenreeks is die u kunt omgevingsvariabelen die dynamisch worden uitgebreid bevatten</span><span class="sxs-lookup"><span data-stu-id="1e977-143">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="1e977-144">MultiString</span><span class="sxs-lookup"><span data-stu-id="1e977-144">MultiString</span></span>|<span data-ttu-id="1e977-145">Een tekenreeks met meerdere regels</span><span class="sxs-lookup"><span data-stu-id="1e977-145">A multiline string</span></span>|
|<span data-ttu-id="1e977-146">Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="1e977-146">String</span></span>|<span data-ttu-id="1e977-147">Een string-waarde</span><span class="sxs-lookup"><span data-stu-id="1e977-147">Any string value</span></span>|
|<span data-ttu-id="1e977-148">QWord</span><span class="sxs-lookup"><span data-stu-id="1e977-148">QWord</span></span>|<span data-ttu-id="1e977-149">8 bytes van binaire gegevens</span><span class="sxs-lookup"><span data-stu-id="1e977-149">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="1e977-150">U kunt een registervermelding toevoegen aan meerdere locaties door te geven van een matrix met waarden voor de **pad** parameter:</span><span class="sxs-lookup"><span data-stu-id="1e977-150">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

<span data-ttu-id="1e977-151">U kunt ook een bestaande vermelding registerwaarde overschrijven door toe te voegen de **Force** parameter aan een **New-ItemProperty** opdracht.</span><span class="sxs-lookup"><span data-stu-id="1e977-151">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any **New-ItemProperty** command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="1e977-152">Naam van de registervermeldingen</span><span class="sxs-lookup"><span data-stu-id="1e977-152">Renaming Registry Entries</span></span>

<span data-ttu-id="1e977-153">Naam wijzigen van de **PowerShellPath** vermelding "PSHome," Gebruik **Rename-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="1e977-153">To rename the **PowerShellPath** entry to "PSHome," use **Rename-ItemProperty**:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="1e977-154">De nieuwe naam als waarde wilt weergeven, toevoegen de **PassThru** parameter aan de opdracht.</span><span class="sxs-lookup"><span data-stu-id="1e977-154">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="1e977-155">Registervermeldingen verwijderen</span><span class="sxs-lookup"><span data-stu-id="1e977-155">Deleting Registry Entries</span></span>

<span data-ttu-id="1e977-156">Als u wilt de PSHome en PowerShellPath registervermeldingen verwijderen, gebruikt u **Remove-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="1e977-156">To delete both the PSHome and PowerShellPath registry entries, use **Remove-ItemProperty**:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```