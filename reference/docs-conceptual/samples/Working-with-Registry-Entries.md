---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Met registervermeldingen werken
ms.openlocfilehash: 7f8ee87cebb8b220570bcb969445071a72a68526
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/04/2020
ms.locfileid: "87758479"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="168dd-103">Met registervermeldingen werken</span><span class="sxs-lookup"><span data-stu-id="168dd-103">Working with Registry Entries</span></span>

<span data-ttu-id="168dd-104">Omdat Register vermeldingen eigenschappen van sleutels zijn en, als zodanig, niet rechtstreeks kunnen worden doorzocht, moeten we een iets andere benadering nemen wanneer ze ermee werken.</span><span class="sxs-lookup"><span data-stu-id="168dd-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

## <a name="listing-registry-entries"></a><span data-ttu-id="168dd-105">Register vermeldingen weer geven</span><span class="sxs-lookup"><span data-stu-id="168dd-105">Listing Registry Entries</span></span>

<span data-ttu-id="168dd-106">Er zijn veel verschillende manieren om Register vermeldingen te controleren.</span><span class="sxs-lookup"><span data-stu-id="168dd-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="168dd-107">De eenvoudigste manier is om de namen van de eigenschappen van een sleutel op te halen.</span><span class="sxs-lookup"><span data-stu-id="168dd-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="168dd-108">Als u bijvoorbeeld de namen van de vermeldingen in de register sleutel wilt weer geven `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion` , gebruikt u `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="168dd-108">For example, to see the names of the entries in the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`.</span></span> <span data-ttu-id="168dd-109">Register sleutels hebben een eigenschap met de algemene naam ' Property ' die een lijst met Register vermeldingen in de sleutel is.</span><span class="sxs-lookup"><span data-stu-id="168dd-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span>
<span data-ttu-id="168dd-110">Met de volgende opdracht wordt de eigenschap Property geselecteerd en worden de items uitgevouwen zodat deze in een lijst worden weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="168dd-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="168dd-111">Als u de Register vermeldingen in een meer Lees bare vorm wilt weer geven, gebruikt u `Get-ItemProperty` :</span><span class="sxs-lookup"><span data-stu-id="168dd-111">To view the registry entries in a more readable form, use `Get-ItemProperty`:</span></span>

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
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

<span data-ttu-id="168dd-112">De Windows Power shell-gerelateerde eigenschappen voor de sleutel worden allemaal voorafgegaan door "PS", zoals **PSPath**, **PSParentPath**, **PSChildName**en **PSProvider**.</span><span class="sxs-lookup"><span data-stu-id="168dd-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="168dd-113">U kunt de `*.*` notatie gebruiken voor het verwijzen naar de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="168dd-113">You can use the `*.*` notation for referring to the current location.</span></span> <span data-ttu-id="168dd-114">U kunt gebruiken `Set-Location` om eerst naar de **CurrentVersion** -register container te overschakelen:</span><span class="sxs-lookup"><span data-stu-id="168dd-114">You can use `Set-Location` to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="168dd-115">U kunt ook het ingebouwde HKLM-PSDrive gebruiken met `Set-Location` :</span><span class="sxs-lookup"><span data-stu-id="168dd-115">Alternatively, you can use the built-in HKLM PSDrive with `Set-Location`:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="168dd-116">U kunt vervolgens de `*.*` notatie voor de huidige locatie gebruiken om de eigenschappen weer te geven zonder een volledig pad op te gave:</span><span class="sxs-lookup"><span data-stu-id="168dd-116">You can then use the `*.*` notation for the current location to list the properties without specifying a full path:</span></span>

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="168dd-117">Pad-uitbrei ding werkt op dezelfde manier als in het bestands systeem, dus vanaf deze locatie kunt u de **item Property** -vermelding voor `HKLM:\SOFTWARE\Microsoft\Windows\Help` gebruiken met behulp van `Get-ItemProperty -Path ..\Help` .</span><span class="sxs-lookup"><span data-stu-id="168dd-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for `HKLM:\SOFTWARE\Microsoft\Windows\Help` by using `Get-ItemProperty -Path ..\Help`.</span></span>

## <a name="getting-a-single-registry-entry"></a><span data-ttu-id="168dd-118">Eén register vermelding ophalen</span><span class="sxs-lookup"><span data-stu-id="168dd-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="168dd-119">Als u een specifieke vermelding in een register sleutel wilt ophalen, kunt u een van de verschillende mogelijke benaderingen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="168dd-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="168dd-120">In dit voor beeld wordt gezocht naar de waarde van **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion` .</span><span class="sxs-lookup"><span data-stu-id="168dd-120">This example finds the value of **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

<span data-ttu-id="168dd-121">`Get-ItemProperty`Gebruik met de para meter **Path** om de naam van de sleutel op te geven en de para meter **name** om de naam van het item **DevicePath** op te geven.</span><span class="sxs-lookup"><span data-stu-id="168dd-121">Using `Get-ItemProperty`, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="168dd-122">Met deze opdracht worden de standaard eigenschappen van Windows Power shell en de eigenschap **DevicePath** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="168dd-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="168dd-123">Hoewel de `Get-ItemProperty` para meters **filter**, **include**en **exclude** zijn, kunnen ze niet worden gebruikt om te filteren op naam van eigenschap.</span><span class="sxs-lookup"><span data-stu-id="168dd-123">Although `Get-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="168dd-124">Deze para meters verwijzen naar register sleutels, die item paden zijn en geen register vermeldingen, die item eigenschappen zijn.</span><span class="sxs-lookup"><span data-stu-id="168dd-124">These parameters refer to registry keys, which are item paths and not registry entries, which are item properties.</span></span>

<span data-ttu-id="168dd-125">Een andere optie is het gebruik van het Reg.exe opdracht regel programma.</span><span class="sxs-lookup"><span data-stu-id="168dd-125">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="168dd-126">Voor hulp bij reg.exe, typt u `reg.exe /?` bij een opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="168dd-126">For help with reg.exe, type `reg.exe /?` at a command prompt.</span></span> <span data-ttu-id="168dd-127">Als u de vermelding DevicePath wilt vinden, gebruikt u reg.exe zoals weer gegeven in de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="168dd-127">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="168dd-128">U kunt ook het COM-object **WshShell** gebruiken om enkele register vermeldingen te vinden, hoewel deze methode niet werkt met grote binaire gegevens of met namen van Register vermeldingen die tekens bevatten zoals " \\ ").</span><span class="sxs-lookup"><span data-stu-id="168dd-128">You can also use the **WshShell** COM object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="168dd-129">Voeg de naam van de eigenschap toe aan het pad van het item met een \\ scheidings teken:</span><span class="sxs-lookup"><span data-stu-id="168dd-129">Append the property name to the item path with a \\ separator:</span></span>

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a><span data-ttu-id="168dd-130">Eén register vermelding instellen</span><span class="sxs-lookup"><span data-stu-id="168dd-130">Setting a Single Registry Entry</span></span>

<span data-ttu-id="168dd-131">Als u een specifieke vermelding in een register sleutel wilt wijzigen, kunt u een van de verschillende mogelijke benaderingen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="168dd-131">If you want to change a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="168dd-132">In dit voor beeld wordt de invoer van het **pad** in gewijzigd `HKEY_CURRENT_USER\Environment` .</span><span class="sxs-lookup"><span data-stu-id="168dd-132">This example modifies the **Path** entry under `HKEY_CURRENT_USER\Environment`.</span></span> <span data-ttu-id="168dd-133">De **pad** -vermelding geeft aan waar uitvoer bare bestanden moeten worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="168dd-133">The **Path** entry specifies where to find executable files.</span></span>

1. <span data-ttu-id="168dd-134">Haal de huidige waarde van het **pad** op met behulp van `Get-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="168dd-134">Retrieve the current value of the **Path** entry using `Get-ItemProperty`.</span></span>
2. <span data-ttu-id="168dd-135">Voeg de nieuwe waarde toe, gescheiden met een `;` .</span><span class="sxs-lookup"><span data-stu-id="168dd-135">Add the new value, separating it with a `;`.</span></span>
3. <span data-ttu-id="168dd-136">Gebruik `Set-ItemProperty` met de opgegeven sleutel, vermeldings naam en waarde om de register vermelding te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="168dd-136">Use `Set-ItemProperty` with the specified key, entry name, and value to modify the registry entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> <span data-ttu-id="168dd-137">Hoewel de `Set-ItemProperty` para meters **filter**, **include**en **exclude** zijn, kunnen ze niet worden gebruikt om te filteren op naam van eigenschap.</span><span class="sxs-lookup"><span data-stu-id="168dd-137">Although `Set-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="168dd-138">Deze para meters verwijzen naar register sleutels, die item paden zijn, en geen register vermeldingen, die item eigenschappen zijn.</span><span class="sxs-lookup"><span data-stu-id="168dd-138">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="168dd-139">Een andere optie is het gebruik van het Reg.exe opdracht regel programma.</span><span class="sxs-lookup"><span data-stu-id="168dd-139">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="168dd-140">Voor hulp bij reg.exe, typt u **reg.exe/?**</span><span class="sxs-lookup"><span data-stu-id="168dd-140">For help with reg.exe, type **reg.exe /?**</span></span>
<span data-ttu-id="168dd-141">bij een opdrachtprompt.</span><span class="sxs-lookup"><span data-stu-id="168dd-141">at a command prompt.</span></span>

<span data-ttu-id="168dd-142">In het volgende voor beeld wordt de invoer van het **pad** gewijzigd door het pad dat in bovenstaand voor beeld is toegevoegd, te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="168dd-142">The following example changes the **Path** entry by removing the path added in the example above.</span></span>
<span data-ttu-id="168dd-143">`Get-ItemProperty` wordt nog steeds gebruikt voor het ophalen van de huidige waarde om te voor komen dat de geretourneerde teken reeks moet worden geparseerd `reg query` .</span><span class="sxs-lookup"><span data-stu-id="168dd-143">`Get-ItemProperty` is still used to retrieve the current value to avoid having to parse the string returned from `reg query`.</span></span> <span data-ttu-id="168dd-144">De **subtekenreeks** -en **LastIndexOf** -methoden worden gebruikt voor het ophalen van het laatste pad dat is toegevoegd aan het **pad** .</span><span class="sxs-lookup"><span data-stu-id="168dd-144">The **SubString** and **LastIndexOf** methods are used to retrieve the last path added to the **Path** entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a><span data-ttu-id="168dd-145">Nieuwe register vermeldingen maken</span><span class="sxs-lookup"><span data-stu-id="168dd-145">Creating New Registry Entries</span></span>

<span data-ttu-id="168dd-146">Als u een nieuwe vermelding met de naam "PowerShellPath" wilt toevoegen aan de **CurrentVersion** -sleutel, gebruikt u `New-ItemProperty` met het pad naar de sleutel, de naam van de vermelding en de waarde van de vermelding.</span><span class="sxs-lookup"><span data-stu-id="168dd-146">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use `New-ItemProperty` with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="168dd-147">In dit voor beeld nemen we de waarde van de Windows Power shell-variabele op `$PSHome` , waarmee het pad naar de installatiemap voor Windows Power shell wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="168dd-147">For this example, we will take the value of the Windows PowerShell variable `$PSHome`, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="168dd-148">U kunt de nieuwe vermelding toevoegen aan de sleutel met behulp van de volgende opdracht, en de opdracht retourneert ook informatie over de nieuwe vermelding:</span><span class="sxs-lookup"><span data-stu-id="168dd-148">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="168dd-149">De **Property type** moet de naam zijn van een **micro soft. Win32. RegistryValueKind** -opsommings element uit de volgende tabel:</span><span class="sxs-lookup"><span data-stu-id="168dd-149">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="168dd-150">Waarde Property type</span><span class="sxs-lookup"><span data-stu-id="168dd-150">PropertyType Value</span></span>|<span data-ttu-id="168dd-151">Betekenis</span><span class="sxs-lookup"><span data-stu-id="168dd-151">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="168dd-152">Binair</span><span class="sxs-lookup"><span data-stu-id="168dd-152">Binary</span></span>|<span data-ttu-id="168dd-153">Binaire gegevens</span><span class="sxs-lookup"><span data-stu-id="168dd-153">Binary data</span></span>|
|<span data-ttu-id="168dd-154">32</span><span class="sxs-lookup"><span data-stu-id="168dd-154">DWord</span></span>|<span data-ttu-id="168dd-155">Een getal dat een geldige UInt32 is</span><span class="sxs-lookup"><span data-stu-id="168dd-155">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="168dd-156">ExpandString</span><span class="sxs-lookup"><span data-stu-id="168dd-156">ExpandString</span></span>|<span data-ttu-id="168dd-157">Een teken reeks die omgevings variabelen kan bevatten die dynamisch worden uitgevouwen</span><span class="sxs-lookup"><span data-stu-id="168dd-157">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="168dd-158">Fixedlength</span><span class="sxs-lookup"><span data-stu-id="168dd-158">MultiString</span></span>|<span data-ttu-id="168dd-159">Een teken reeks met meerdere regels</span><span class="sxs-lookup"><span data-stu-id="168dd-159">A multiline string</span></span>|
|<span data-ttu-id="168dd-160">Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="168dd-160">String</span></span>|<span data-ttu-id="168dd-161">Elke tekenreekswaarde</span><span class="sxs-lookup"><span data-stu-id="168dd-161">Any string value</span></span>|
|<span data-ttu-id="168dd-162">QWord</span><span class="sxs-lookup"><span data-stu-id="168dd-162">QWord</span></span>|<span data-ttu-id="168dd-163">8 bytes aan binaire gegevens</span><span class="sxs-lookup"><span data-stu-id="168dd-163">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="168dd-164">U kunt een register vermelding toevoegen aan meerdere locaties door een matrix met waarden op te geven voor de para meter **Path** :</span><span class="sxs-lookup"><span data-stu-id="168dd-164">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="168dd-165">U kunt ook een vooraf bestaande register vermelding overschrijven door de para meter **Force** toe te voegen aan een `New-ItemProperty` opdracht.</span><span class="sxs-lookup"><span data-stu-id="168dd-165">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any `New-ItemProperty` command.</span></span>

## <a name="renaming-registry-entries"></a><span data-ttu-id="168dd-166">Naam wijzigen van Register vermeldingen</span><span class="sxs-lookup"><span data-stu-id="168dd-166">Renaming Registry Entries</span></span>

<span data-ttu-id="168dd-167">Als u de naam van de **PowerShellPath** -vermelding wilt wijzigen in ' PSHome ', gebruikt u `Rename-ItemProperty` :</span><span class="sxs-lookup"><span data-stu-id="168dd-167">To rename the **PowerShellPath** entry to "PSHome," use `Rename-ItemProperty`:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="168dd-168">Als u de hernoemde waarde wilt weer geven, voegt u de para meter **PassThru** toe aan de opdracht.</span><span class="sxs-lookup"><span data-stu-id="168dd-168">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a><span data-ttu-id="168dd-169">Register vermeldingen verwijderen</span><span class="sxs-lookup"><span data-stu-id="168dd-169">Deleting Registry Entries</span></span>

<span data-ttu-id="168dd-170">Als u de Register vermeldingen PSHome en PowerShellPath wilt verwijderen, gebruikt u `Remove-ItemProperty` :</span><span class="sxs-lookup"><span data-stu-id="168dd-170">To delete both the PSHome and PowerShellPath registry entries, use `Remove-ItemProperty`:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
