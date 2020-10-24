---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Met registervermeldingen werken
description: In dit artikel wordt beschreven hoe u met behulp van Power shell Register vermeldingen kunt verwerken.
ms.openlocfilehash: 65f8b4ed7b2f9af26bfd22f34577a4bd52f35e70
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501453"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="3cdaf-104">Met registervermeldingen werken</span><span class="sxs-lookup"><span data-stu-id="3cdaf-104">Working with Registry Entries</span></span>

<span data-ttu-id="3cdaf-105">Omdat Register vermeldingen eigenschappen van sleutels zijn en, als zodanig, niet rechtstreeks kunnen worden doorzocht, moeten we een iets andere benadering nemen wanneer ze ermee werken.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-105">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

## <a name="listing-registry-entries"></a><span data-ttu-id="3cdaf-106">Register vermeldingen weer geven</span><span class="sxs-lookup"><span data-stu-id="3cdaf-106">Listing Registry Entries</span></span>

<span data-ttu-id="3cdaf-107">Er zijn veel verschillende manieren om Register vermeldingen te controleren.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-107">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="3cdaf-108">De eenvoudigste manier is om de namen van de eigenschappen van een sleutel op te halen.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-108">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="3cdaf-109">Als u bijvoorbeeld de namen van de vermeldingen in de register sleutel wilt weer geven `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion` , gebruikt u `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="3cdaf-109">For example, to see the names of the entries in the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`.</span></span> <span data-ttu-id="3cdaf-110">Register sleutels hebben een eigenschap met de algemene naam ' Property ' die een lijst met Register vermeldingen in de sleutel is.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-110">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span>
<span data-ttu-id="3cdaf-111">Met de volgende opdracht wordt de eigenschap Property geselecteerd en worden de items uitgevouwen zodat deze in een lijst worden weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="3cdaf-111">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

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

<span data-ttu-id="3cdaf-112">Als u de Register vermeldingen in een meer Lees bare vorm wilt weer geven, gebruikt u `Get-ItemProperty` :</span><span class="sxs-lookup"><span data-stu-id="3cdaf-112">To view the registry entries in a more readable form, use `Get-ItemProperty`:</span></span>

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

<span data-ttu-id="3cdaf-113">De Windows Power shell-gerelateerde eigenschappen voor de sleutel worden allemaal voorafgegaan door "PS", zoals **PSPath**, **PSParentPath**, **PSChildName**en **PSProvider**.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-113">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="3cdaf-114">U kunt de `*.*` notatie gebruiken voor het verwijzen naar de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-114">You can use the `*.*` notation for referring to the current location.</span></span> <span data-ttu-id="3cdaf-115">U kunt gebruiken `Set-Location` om eerst naar de **CurrentVersion** -register container te overschakelen:</span><span class="sxs-lookup"><span data-stu-id="3cdaf-115">You can use `Set-Location` to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="3cdaf-116">U kunt ook het ingebouwde HKLM-PSDrive gebruiken met `Set-Location` :</span><span class="sxs-lookup"><span data-stu-id="3cdaf-116">Alternatively, you can use the built-in HKLM PSDrive with `Set-Location`:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="3cdaf-117">U kunt vervolgens de `*.*` notatie voor de huidige locatie gebruiken om de eigenschappen weer te geven zonder een volledig pad op te gave:</span><span class="sxs-lookup"><span data-stu-id="3cdaf-117">You can then use the `*.*` notation for the current location to list the properties without specifying a full path:</span></span>

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

<span data-ttu-id="3cdaf-118">Pad-uitbrei ding werkt op dezelfde manier als in het bestands systeem, dus vanaf deze locatie kunt u de **item Property** -vermelding voor `HKLM:\SOFTWARE\Microsoft\Windows\Help` gebruiken met behulp van `Get-ItemProperty -Path ..\Help` .</span><span class="sxs-lookup"><span data-stu-id="3cdaf-118">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for `HKLM:\SOFTWARE\Microsoft\Windows\Help` by using `Get-ItemProperty -Path ..\Help`.</span></span>

## <a name="getting-a-single-registry-entry"></a><span data-ttu-id="3cdaf-119">Eén register vermelding ophalen</span><span class="sxs-lookup"><span data-stu-id="3cdaf-119">Getting a Single Registry Entry</span></span>

<span data-ttu-id="3cdaf-120">Als u een specifieke vermelding in een register sleutel wilt ophalen, kunt u een van de verschillende mogelijke benaderingen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-120">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="3cdaf-121">In dit voor beeld wordt gezocht naar de waarde van **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion` .</span><span class="sxs-lookup"><span data-stu-id="3cdaf-121">This example finds the value of **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

<span data-ttu-id="3cdaf-122">`Get-ItemProperty`Gebruik met de para meter **Path** om de naam van de sleutel op te geven en de para meter **name** om de naam van het item **DevicePath** op te geven.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-122">Using `Get-ItemProperty`, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

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

<span data-ttu-id="3cdaf-123">Met deze opdracht worden de standaard eigenschappen van Windows Power shell en de eigenschap **DevicePath** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-123">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="3cdaf-124">Hoewel de `Get-ItemProperty` para meters **filter**, **include**en **exclude** zijn, kunnen ze niet worden gebruikt om te filteren op naam van eigenschap.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-124">Although `Get-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="3cdaf-125">Deze para meters verwijzen naar register sleutels, die item paden zijn en geen register vermeldingen, die item eigenschappen zijn.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-125">These parameters refer to registry keys, which are item paths and not registry entries, which are item properties.</span></span>

<span data-ttu-id="3cdaf-126">Een andere optie is het gebruik van het Reg.exe opdracht regel programma.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-126">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="3cdaf-127">Voor hulp bij reg.exe, typt u `reg.exe /?` bij een opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-127">For help with reg.exe, type `reg.exe /?` at a command prompt.</span></span> <span data-ttu-id="3cdaf-128">Als u de vermelding DevicePath wilt vinden, gebruikt u reg.exe zoals weer gegeven in de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="3cdaf-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="3cdaf-129">U kunt ook het COM-object **WshShell** gebruiken om enkele register vermeldingen te vinden, hoewel deze methode niet werkt met grote binaire gegevens of met namen van Register vermeldingen die tekens bevatten zoals " \\ ").</span><span class="sxs-lookup"><span data-stu-id="3cdaf-129">You can also use the **WshShell** COM object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="3cdaf-130">Voeg de naam van de eigenschap toe aan het pad van het item met een \\ scheidings teken:</span><span class="sxs-lookup"><span data-stu-id="3cdaf-130">Append the property name to the item path with a \\ separator:</span></span>

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a><span data-ttu-id="3cdaf-131">Eén register vermelding instellen</span><span class="sxs-lookup"><span data-stu-id="3cdaf-131">Setting a Single Registry Entry</span></span>

<span data-ttu-id="3cdaf-132">Als u een specifieke vermelding in een register sleutel wilt wijzigen, kunt u een van de verschillende mogelijke benaderingen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-132">If you want to change a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="3cdaf-133">In dit voor beeld wordt de invoer van het **pad** in gewijzigd `HKEY_CURRENT_USER\Environment` .</span><span class="sxs-lookup"><span data-stu-id="3cdaf-133">This example modifies the **Path** entry under `HKEY_CURRENT_USER\Environment`.</span></span> <span data-ttu-id="3cdaf-134">De **pad** -vermelding geeft aan waar uitvoer bare bestanden moeten worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-134">The **Path** entry specifies where to find executable files.</span></span>

1. <span data-ttu-id="3cdaf-135">Haal de huidige waarde van het **pad** op met behulp van `Get-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="3cdaf-135">Retrieve the current value of the **Path** entry using `Get-ItemProperty`.</span></span>
2. <span data-ttu-id="3cdaf-136">Voeg de nieuwe waarde toe, gescheiden met een `;` .</span><span class="sxs-lookup"><span data-stu-id="3cdaf-136">Add the new value, separating it with a `;`.</span></span>
3. <span data-ttu-id="3cdaf-137">Gebruik `Set-ItemProperty` met de opgegeven sleutel, vermeldings naam en waarde om de register vermelding te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-137">Use `Set-ItemProperty` with the specified key, entry name, and value to modify the registry entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> <span data-ttu-id="3cdaf-138">Hoewel de `Set-ItemProperty` para meters **filter**, **include**en **exclude** zijn, kunnen ze niet worden gebruikt om te filteren op naam van eigenschap.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-138">Although `Set-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="3cdaf-139">Deze para meters verwijzen naar register sleutels, die item paden zijn, en geen register vermeldingen, die item eigenschappen zijn.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-139">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="3cdaf-140">Een andere optie is het gebruik van het Reg.exe opdracht regel programma.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-140">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="3cdaf-141">Voor hulp bij reg.exe, typt u **reg.exe/?**</span><span class="sxs-lookup"><span data-stu-id="3cdaf-141">For help with reg.exe, type **reg.exe /?**</span></span>
<span data-ttu-id="3cdaf-142">bij een opdrachtprompt.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-142">at a command prompt.</span></span>

<span data-ttu-id="3cdaf-143">In het volgende voor beeld wordt de invoer van het **pad** gewijzigd door het pad dat in bovenstaand voor beeld is toegevoegd, te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-143">The following example changes the **Path** entry by removing the path added in the example above.</span></span>
<span data-ttu-id="3cdaf-144">`Get-ItemProperty` wordt nog steeds gebruikt voor het ophalen van de huidige waarde om te voor komen dat de geretourneerde teken reeks moet worden geparseerd `reg query` .</span><span class="sxs-lookup"><span data-stu-id="3cdaf-144">`Get-ItemProperty` is still used to retrieve the current value to avoid having to parse the string returned from `reg query`.</span></span> <span data-ttu-id="3cdaf-145">De **subtekenreeks** -en **LastIndexOf** -methoden worden gebruikt voor het ophalen van het laatste pad dat is toegevoegd aan het **pad** .</span><span class="sxs-lookup"><span data-stu-id="3cdaf-145">The **SubString** and **LastIndexOf** methods are used to retrieve the last path added to the **Path** entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a><span data-ttu-id="3cdaf-146">Nieuwe register vermeldingen maken</span><span class="sxs-lookup"><span data-stu-id="3cdaf-146">Creating New Registry Entries</span></span>

<span data-ttu-id="3cdaf-147">Als u een nieuwe vermelding met de naam "PowerShellPath" wilt toevoegen aan de **CurrentVersion** -sleutel, gebruikt u `New-ItemProperty` met het pad naar de sleutel, de naam van de vermelding en de waarde van de vermelding.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-147">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use `New-ItemProperty` with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="3cdaf-148">In dit voor beeld nemen we de waarde van de Windows Power shell-variabele op `$PSHome` , waarmee het pad naar de installatiemap voor Windows Power shell wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-148">For this example, we will take the value of the Windows PowerShell variable `$PSHome`, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="3cdaf-149">U kunt de nieuwe vermelding toevoegen aan de sleutel met behulp van de volgende opdracht, en de opdracht retourneert ook informatie over de nieuwe vermelding:</span><span class="sxs-lookup"><span data-stu-id="3cdaf-149">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

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

<span data-ttu-id="3cdaf-150">De **Property type** moet de naam zijn van een **micro soft. Win32. RegistryValueKind** -opsommings element uit de volgende tabel:</span><span class="sxs-lookup"><span data-stu-id="3cdaf-150">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="3cdaf-151">Waarde Property type</span><span class="sxs-lookup"><span data-stu-id="3cdaf-151">PropertyType Value</span></span>|<span data-ttu-id="3cdaf-152">Betekenis</span><span class="sxs-lookup"><span data-stu-id="3cdaf-152">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="3cdaf-153">Binair</span><span class="sxs-lookup"><span data-stu-id="3cdaf-153">Binary</span></span>|<span data-ttu-id="3cdaf-154">Binaire gegevens</span><span class="sxs-lookup"><span data-stu-id="3cdaf-154">Binary data</span></span>|
|<span data-ttu-id="3cdaf-155">32</span><span class="sxs-lookup"><span data-stu-id="3cdaf-155">DWord</span></span>|<span data-ttu-id="3cdaf-156">Een getal dat een geldige UInt32 is</span><span class="sxs-lookup"><span data-stu-id="3cdaf-156">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="3cdaf-157">ExpandString</span><span class="sxs-lookup"><span data-stu-id="3cdaf-157">ExpandString</span></span>|<span data-ttu-id="3cdaf-158">Een teken reeks die omgevings variabelen kan bevatten die dynamisch worden uitgevouwen</span><span class="sxs-lookup"><span data-stu-id="3cdaf-158">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="3cdaf-159">Fixedlength</span><span class="sxs-lookup"><span data-stu-id="3cdaf-159">MultiString</span></span>|<span data-ttu-id="3cdaf-160">Een teken reeks met meerdere regels</span><span class="sxs-lookup"><span data-stu-id="3cdaf-160">A multiline string</span></span>|
|<span data-ttu-id="3cdaf-161">Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3cdaf-161">String</span></span>|<span data-ttu-id="3cdaf-162">Elke tekenreekswaarde</span><span class="sxs-lookup"><span data-stu-id="3cdaf-162">Any string value</span></span>|
|<span data-ttu-id="3cdaf-163">QWord</span><span class="sxs-lookup"><span data-stu-id="3cdaf-163">QWord</span></span>|<span data-ttu-id="3cdaf-164">8 bytes aan binaire gegevens</span><span class="sxs-lookup"><span data-stu-id="3cdaf-164">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="3cdaf-165">U kunt een register vermelding toevoegen aan meerdere locaties door een matrix met waarden op te geven voor de para meter **Path** :</span><span class="sxs-lookup"><span data-stu-id="3cdaf-165">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="3cdaf-166">U kunt ook een vooraf bestaande register vermelding overschrijven door de para meter **Force** toe te voegen aan een `New-ItemProperty` opdracht.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-166">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any `New-ItemProperty` command.</span></span>

## <a name="renaming-registry-entries"></a><span data-ttu-id="3cdaf-167">Naam wijzigen van Register vermeldingen</span><span class="sxs-lookup"><span data-stu-id="3cdaf-167">Renaming Registry Entries</span></span>

<span data-ttu-id="3cdaf-168">Als u de naam van de **PowerShellPath** -vermelding wilt wijzigen in ' PSHome ', gebruikt u `Rename-ItemProperty` :</span><span class="sxs-lookup"><span data-stu-id="3cdaf-168">To rename the **PowerShellPath** entry to "PSHome," use `Rename-ItemProperty`:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="3cdaf-169">Als u de hernoemde waarde wilt weer geven, voegt u de para meter **PassThru** toe aan de opdracht.</span><span class="sxs-lookup"><span data-stu-id="3cdaf-169">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a><span data-ttu-id="3cdaf-170">Register vermeldingen verwijderen</span><span class="sxs-lookup"><span data-stu-id="3cdaf-170">Deleting Registry Entries</span></span>

<span data-ttu-id="3cdaf-171">Als u de Register vermeldingen PSHome en PowerShellPath wilt verwijderen, gebruikt u `Remove-ItemProperty` :</span><span class="sxs-lookup"><span data-stu-id="3cdaf-171">To delete both the PSHome and PowerShellPath registry entries, use `Remove-ItemProperty`:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
