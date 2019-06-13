---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met registervermeldingen werken
ms.openlocfilehash: c1fd6f57f13240eb2039f2d5756796678800aee0
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030732"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="df386-103">Met registervermeldingen werken</span><span class="sxs-lookup"><span data-stu-id="df386-103">Working with Registry Entries</span></span>

<span data-ttu-id="df386-104">Omdat de registervermeldingen zijn eigenschappen van sleutels en, als zodanig kunnen niet worden rechtstreeks gebladerd, moet een lichtjes andere benadering nemen bij het werken met hen.</span><span class="sxs-lookup"><span data-stu-id="df386-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

## <a name="listing-registry-entries"></a><span data-ttu-id="df386-105">Registervermeldingen van aanbieding</span><span class="sxs-lookup"><span data-stu-id="df386-105">Listing Registry Entries</span></span>

<span data-ttu-id="df386-106">Er zijn veel verschillende manieren om te onderzoeken registervermeldingen.</span><span class="sxs-lookup"><span data-stu-id="df386-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="df386-107">De eenvoudigste manier is om op te halen van de namen van eigenschappen die zijn gekoppeld aan een sleutel.</span><span class="sxs-lookup"><span data-stu-id="df386-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="df386-108">Bijvoorbeeld, om te zien van de namen van de vermeldingen in de registersleutel `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, gebruikt u `Get-Item`.</span><span class="sxs-lookup"><span data-stu-id="df386-108">For example, to see the names of the entries in the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`.</span></span> <span data-ttu-id="df386-109">Registersleutels hebben een eigenschap met de algemene naam van 'Eigenschap' die een lijst met vermeldingen in de sleutel is.</span><span class="sxs-lookup"><span data-stu-id="df386-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span>
<span data-ttu-id="df386-110">De volgende opdracht uit de eigenschap selecteert en de items wordt uitgebreid zodat ze worden weergegeven in een lijst:</span><span class="sxs-lookup"><span data-stu-id="df386-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

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

<span data-ttu-id="df386-111">U kunt de registervermeldingen weergeven in een beter leesbare vorm, met `Get-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="df386-111">To view the registry entries in a more readable form, use `Get-ItemProperty`:</span></span>

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

<span data-ttu-id="df386-112">De Windows PowerShell-eigenschappen voor de sleutel worden alle voorafgegaan door 'PS', zoals **PSPath**, **PSParentPath**, **PSChildName**, en **PSProvider** .</span><span class="sxs-lookup"><span data-stu-id="df386-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="df386-113">U kunt de `*.*` notatie voor verwijzen naar de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="df386-113">You can use the `*.*` notation for referring to the current location.</span></span> <span data-ttu-id="df386-114">U kunt `Set-Location` wijzigen in de **CurrentVersion** container registry eerste:</span><span class="sxs-lookup"><span data-stu-id="df386-114">You can use `Set-Location` to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="df386-115">U kunt ook kunt u de ingebouwde HKLM PSDrive met `Set-Location`:</span><span class="sxs-lookup"><span data-stu-id="df386-115">Alternatively, you can use the built-in HKLM PSDrive with `Set-Location`:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="df386-116">Vervolgens kunt u de `*.*` notatie voor de huidige locatie om de eigenschappen zonder op te geven van een volledig pad:</span><span class="sxs-lookup"><span data-stu-id="df386-116">You can then use the `*.*` notation for the current location to list the properties without specifying a full path:</span></span>

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

<span data-ttu-id="df386-117">Pad uitbreiding werkt hetzelfde als in het bestandssysteem, zodat u vanaf deze locatie krijgt u de **ItemProperty** aanbieding voor `HKLM:\SOFTWARE\Microsoft\Windows\Help` met behulp van `Get-ItemProperty -Path ..\Help`.</span><span class="sxs-lookup"><span data-stu-id="df386-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for `HKLM:\SOFTWARE\Microsoft\Windows\Help` by using `Get-ItemProperty -Path ..\Help`.</span></span>

## <a name="getting-a-single-registry-entry"></a><span data-ttu-id="df386-118">Een enkel register-item ophalen</span><span class="sxs-lookup"><span data-stu-id="df386-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="df386-119">Als u ophalen van een bepaalde vermelding in een registersleutel wilt, kunt u een van verschillende mogelijke methoden.</span><span class="sxs-lookup"><span data-stu-id="df386-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="df386-120">In dit voorbeeld wordt gezocht naar de waarde van **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span><span class="sxs-lookup"><span data-stu-id="df386-120">This example finds the value of **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

<span data-ttu-id="df386-121">Met behulp van `Get-ItemProperty`, gebruikt u de **pad** parameter opgeven voor de naam van de sleutel en de **naam** parameter opgeven voor de naam van de **DevicePath** vermelding.</span><span class="sxs-lookup"><span data-stu-id="df386-121">Using `Get-ItemProperty`, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

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

<span data-ttu-id="df386-122">Met deze opdracht retourneert de standaardeigenschappen van Windows PowerShell, evenals de **DevicePath** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="df386-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="df386-123">Hoewel `Get-ItemProperty` heeft **Filter**, **opnemen**, en **uitsluiten** parameters, ze om te filteren op naam van de eigenschap kunnen niet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="df386-123">Although `Get-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="df386-124">Deze parameters verwijzen naar registersleutels, item paden en geen vermeldingen in het register.</span><span class="sxs-lookup"><span data-stu-id="df386-124">These parameters refer to registry keys, which are item paths and not registry entries.</span></span> <span data-ttu-id="df386-125">De registervermeldingen die eigenschappen van het item.</span><span class="sxs-lookup"><span data-stu-id="df386-125">Registry entries which are item properties.</span></span>

<span data-ttu-id="df386-126">Een andere optie is het gebruik van het hulpprogramma Reg.exe vanaf de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="df386-126">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="df386-127">Typ voor help met reg.exe `reg.exe /?` achter de opdrachtprompt.</span><span class="sxs-lookup"><span data-stu-id="df386-127">For help with reg.exe, type `reg.exe /?` at a command prompt.</span></span> <span data-ttu-id="df386-128">Als u de vermelding DevicePath zoekt, gebruikt u reg.exe zoals wordt weergegeven in de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="df386-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="df386-129">U kunt ook de **WshShell** COM-object ook te vinden van sommige registervermeldingen, hoewel deze methode niet werkt met grote binaire gegevens of met de namen van de Register-vermeldingen die tekens zoals bevatten '\\').</span><span class="sxs-lookup"><span data-stu-id="df386-129">You can also use the **WshShell** COM object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="df386-130">Naam van de eigenschap toevoegen aan het pad van het item met een \\ scheidingsteken:</span><span class="sxs-lookup"><span data-stu-id="df386-130">Append the property name to the item path with a \\ separator:</span></span>

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a><span data-ttu-id="df386-131">Instellen van een enkel register-item</span><span class="sxs-lookup"><span data-stu-id="df386-131">Setting a Single Registry Entry</span></span>

<span data-ttu-id="df386-132">Als u wijzigen van een bepaalde vermelding in een registersleutel wilt, kunt u een van verschillende mogelijke methoden gebruiken.</span><span class="sxs-lookup"><span data-stu-id="df386-132">If you want to change a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="df386-133">In dit voorbeeld wijzigt de **pad** item onder `HKEY_CURRENT_USER\Environment`.</span><span class="sxs-lookup"><span data-stu-id="df386-133">This example modifies the **Path** entry under `HKEY_CURRENT_USER\Environment`.</span></span> <span data-ttu-id="df386-134">De **pad** vermelding wordt opgegeven waar zich uitvoerbare bestanden.</span><span class="sxs-lookup"><span data-stu-id="df386-134">The **Path** entry specifies where to find executable files.</span></span>

1. <span data-ttu-id="df386-135">Ophalen van de huidige waarde van de **pad** met behulp van vermelding `Get-ItemProperty`.</span><span class="sxs-lookup"><span data-stu-id="df386-135">Retrieve the current value of the **Path** entry using `Get-ItemProperty`.</span></span>
2. <span data-ttu-id="df386-136">Voeg de nieuwe waarde, scheiden met een `;`.</span><span class="sxs-lookup"><span data-stu-id="df386-136">Add the new value, separating it with a `;`.</span></span>
3. <span data-ttu-id="df386-137">Gebruik `Set-ItemProperty` met de opgegeven sleutel, naam en waarde te wijzigen van het register-item.</span><span class="sxs-lookup"><span data-stu-id="df386-137">Use `Set-ItemProperty` with the specified key, entry name, and value to modify the registry entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> <span data-ttu-id="df386-138">Hoewel `Set-ItemProperty` heeft **Filter**, **opnemen**, en **uitsluiten** parameters, ze om te filteren op naam van de eigenschap kunnen niet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="df386-138">Although `Set-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="df386-139">Deze parameters verwijzen naar registersleutels: item paden zijn, en niet de registervermeldingen: welke eigenschappen van het item zijn.</span><span class="sxs-lookup"><span data-stu-id="df386-139">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="df386-140">Een andere optie is het gebruik van het hulpprogramma Reg.exe vanaf de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="df386-140">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="df386-141">Typ voor help met reg.exe **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="df386-141">For help with reg.exe, type **reg.exe /?**</span></span>
<span data-ttu-id="df386-142">bij een opdrachtprompt.</span><span class="sxs-lookup"><span data-stu-id="df386-142">at a command prompt.</span></span>

<span data-ttu-id="df386-143">Het volgende voorbeeld van de wijzigingen de **pad** vermelding door het verwijderen van het pad dat is toegevoegd in het bovenstaande voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="df386-143">The following example changes the **Path** entry by removing the path added in the example above.</span></span>
<span data-ttu-id="df386-144">`Get-ItemProperty` nog steeds wordt gebruikt om op te halen van de huidige waarde om te voorkomen dat de tekenreeks die is geretourneerd door parseren `reg query`.</span><span class="sxs-lookup"><span data-stu-id="df386-144">`Get-ItemProperty` is still used to retrieve the current value to avoid having to parse the string returned from `reg query`.</span></span> <span data-ttu-id="df386-145">De **subtekenreeks** en **LastIndexOf** methoden worden gebruikt voor het ophalen van het laatste pad toegevoegd aan de **pad** vermelding.</span><span class="sxs-lookup"><span data-stu-id="df386-145">The **SubString** and **LastIndexOf** methods are used to retrieve the last path added to the **Path** entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a><span data-ttu-id="df386-146">Het maken van nieuwe registervermeldingen</span><span class="sxs-lookup"><span data-stu-id="df386-146">Creating New Registry Entries</span></span>

<span data-ttu-id="df386-147">Een nieuwe vermelding met de naam 'PowerShellPath' toevoegen aan de **CurrentVersion** , sleutelgebruik `New-ItemProperty` met het pad naar de sleutel, naam van de vermelding en de waarde van het item.</span><span class="sxs-lookup"><span data-stu-id="df386-147">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use `New-ItemProperty` with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="df386-148">In dit voorbeeld wordt de waarde van de Windows PowerShell-variabele duurt `$PSHome`, waarin het pad naar de installatiemap voor Windows PowerShell wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="df386-148">For this example, we will take the value of the Windows PowerShell variable `$PSHome`, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="df386-149">U kunt het nieuwe item toevoegen aan de sleutel met behulp van de volgende opdracht en de opdracht retourneert ook informatie over het nieuwe item:</span><span class="sxs-lookup"><span data-stu-id="df386-149">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

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

<span data-ttu-id="df386-150">De **%d{PropertyType/** moet de naam van een **Microsoft.Win32.RegistryValueKind** lid van de opsomming van de volgende tabel:</span><span class="sxs-lookup"><span data-stu-id="df386-150">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="df386-151">%D{PropertyType/ waarde</span><span class="sxs-lookup"><span data-stu-id="df386-151">PropertyType Value</span></span>|<span data-ttu-id="df386-152">Betekenis</span><span class="sxs-lookup"><span data-stu-id="df386-152">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="df386-153">Binary</span><span class="sxs-lookup"><span data-stu-id="df386-153">Binary</span></span>|<span data-ttu-id="df386-154">Binaire gegevens</span><span class="sxs-lookup"><span data-stu-id="df386-154">Binary data</span></span>|
|<span data-ttu-id="df386-155">DWord</span><span class="sxs-lookup"><span data-stu-id="df386-155">DWord</span></span>|<span data-ttu-id="df386-156">Een getal dat is een geldige UInt32</span><span class="sxs-lookup"><span data-stu-id="df386-156">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="df386-157">ExpandString</span><span class="sxs-lookup"><span data-stu-id="df386-157">ExpandString</span></span>|<span data-ttu-id="df386-158">Een tekenreeks is die u kunt omgevingsvariabelen die dynamisch worden uitgebreid bevatten</span><span class="sxs-lookup"><span data-stu-id="df386-158">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="df386-159">MultiString</span><span class="sxs-lookup"><span data-stu-id="df386-159">MultiString</span></span>|<span data-ttu-id="df386-160">Een tekenreeks met meerdere regels</span><span class="sxs-lookup"><span data-stu-id="df386-160">A multiline string</span></span>|
|<span data-ttu-id="df386-161">Reeks</span><span class="sxs-lookup"><span data-stu-id="df386-161">String</span></span>|<span data-ttu-id="df386-162">een string-waarde</span><span class="sxs-lookup"><span data-stu-id="df386-162">Any string value</span></span>|
|<span data-ttu-id="df386-163">QWord</span><span class="sxs-lookup"><span data-stu-id="df386-163">QWord</span></span>|<span data-ttu-id="df386-164">8 bytes van binaire gegevens</span><span class="sxs-lookup"><span data-stu-id="df386-164">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="df386-165">U kunt een registervermelding toevoegen aan meerdere locaties door te geven van een matrix met waarden voor de **pad** parameter:</span><span class="sxs-lookup"><span data-stu-id="df386-165">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="df386-166">U kunt ook een bestaande vermelding registerwaarde overschrijven door toe te voegen de **Force** parameter aan een `New-ItemProperty` opdracht.</span><span class="sxs-lookup"><span data-stu-id="df386-166">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any `New-ItemProperty` command.</span></span>

## <a name="renaming-registry-entries"></a><span data-ttu-id="df386-167">Naam van de registervermeldingen</span><span class="sxs-lookup"><span data-stu-id="df386-167">Renaming Registry Entries</span></span>

<span data-ttu-id="df386-168">Naam wijzigen van de **PowerShellPath** vermelding "PSHome," Gebruik `Rename-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="df386-168">To rename the **PowerShellPath** entry to "PSHome," use `Rename-ItemProperty`:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="df386-169">De nieuwe naam als waarde wilt weergeven, toevoegen de **PassThru** parameter aan de opdracht.</span><span class="sxs-lookup"><span data-stu-id="df386-169">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a><span data-ttu-id="df386-170">Registervermeldingen verwijderen</span><span class="sxs-lookup"><span data-stu-id="df386-170">Deleting Registry Entries</span></span>

<span data-ttu-id="df386-171">Als u wilt de PSHome en PowerShellPath registervermeldingen verwijderen, gebruikt u `Remove-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="df386-171">To delete both the PSHome and PowerShellPath registry entries, use `Remove-ItemProperty`:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
