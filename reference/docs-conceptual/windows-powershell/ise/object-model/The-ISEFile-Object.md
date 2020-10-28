---
ms.date: 12/31/2019
title: Het ISEFile-object
description: Een ISEFile-object vertegenwoordigt een bestand in Windows PowerShell ISE.
ms.openlocfilehash: 0de19c45bde7e5629d5721635150d3b0915aaa7d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662135"
---
# <a name="the-isefile-object"></a><span data-ttu-id="576a9-103">Het ISEFile-object</span><span class="sxs-lookup"><span data-stu-id="576a9-103">The ISEFile Object</span></span>

<span data-ttu-id="576a9-104">Een **ISEFile** -object vertegenwoordigt een bestand in Windows Power shell &reg; Integrated SCRIPTING Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="576a9-104">An **ISEFile** object represents a file in Windows PowerShell&reg; Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="576a9-105">Het is een exemplaar van de klasse **micro soft. Power shell. host. ISE. ISEFile** .</span><span class="sxs-lookup"><span data-stu-id="576a9-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEFile** class.</span></span> <span data-ttu-id="576a9-106">In dit onderwerp worden de methoden en lideigenschappen van leden vermeld.</span><span class="sxs-lookup"><span data-stu-id="576a9-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="576a9-107">De `$psISE.CurrentFile` bestanden in de verzameling bestanden in een Power shell-tabblad zijn alle exemplaren van de klasse \* \* \* \* micro soft. Power shell. host. ISE. ISEFile \* \*.</span><span class="sxs-lookup"><span data-stu-id="576a9-107">The `$psISE.CurrentFile` and the files in the Files collection in a PowerShell tab are all instances of the \*\*\*\*Microsoft.PowerShell.Host.ISE.ISEFile\*\* class.</span></span>

## <a name="methods"></a><span data-ttu-id="576a9-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="576a9-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="576a9-109">\( \[ SaveEncoding \] opslaan\)</span><span class="sxs-lookup"><span data-stu-id="576a9-109">Save\( \[saveEncoding\] \)</span></span>

<span data-ttu-id="576a9-110">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="576a9-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="576a9-111">Hiermee slaat u het bestand op schijf.</span><span class="sxs-lookup"><span data-stu-id="576a9-111">Saves the file to disk.</span></span>

<span data-ttu-id="576a9-112">**\[ saveEncoding \]** -optioneel [System. Text. encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) een optionele teken coderings parameter die moet worden gebruikt voor het opgeslagen bestand.</span><span class="sxs-lookup"><span data-stu-id="576a9-112">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="576a9-113">De standaard waarde is **utf8** .</span><span class="sxs-lookup"><span data-stu-id="576a9-113">The default value is **UTF8** .</span></span>

### <a name="exceptions"></a><span data-ttu-id="576a9-114">Uitzonderingen</span><span class="sxs-lookup"><span data-stu-id="576a9-114">Exceptions</span></span>

- <span data-ttu-id="576a9-115">**System. io. IOException** : het bestand kan niet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="576a9-115">**System.IO.IOException** : The file could not be saved.</span></span>

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="576a9-116">\(Bestands naam: opslaan als, \[ saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="576a9-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>

<span data-ttu-id="576a9-117">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="576a9-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="576a9-118">Hiermee slaat u het bestand op met de opgegeven bestands naam en-code ring.</span><span class="sxs-lookup"><span data-stu-id="576a9-118">Saves the file with the specified file name and encoding.</span></span>

<span data-ttu-id="576a9-119">**Bestands naam** : de naam van de teken reeks die moet worden gebruikt om het bestand op te slaan.</span><span class="sxs-lookup"><span data-stu-id="576a9-119">**filename** - String The name to be used to save the file.</span></span>

<span data-ttu-id="576a9-120">**\[ saveEncoding \]** -optioneel [System. Text. encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) een optionele teken coderings parameter die moet worden gebruikt voor het opgeslagen bestand.</span><span class="sxs-lookup"><span data-stu-id="576a9-120">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="576a9-121">De standaard waarde is **utf8** .</span><span class="sxs-lookup"><span data-stu-id="576a9-121">The default value is **UTF8** .</span></span>

### <a name="exceptions"></a><span data-ttu-id="576a9-122">Uitzonderingen</span><span class="sxs-lookup"><span data-stu-id="576a9-122">Exceptions</span></span>

- <span data-ttu-id="576a9-123">**System. ArgumentNullException** : de **filename** -para meter is null.</span><span class="sxs-lookup"><span data-stu-id="576a9-123">**System.ArgumentNullException** : The **filename** parameter is null.</span></span>
- <span data-ttu-id="576a9-124">**System. ArgumentException** : de **filename** -para meter is leeg.</span><span class="sxs-lookup"><span data-stu-id="576a9-124">**System.ArgumentException** : The **filename** parameter is empty.</span></span>
- <span data-ttu-id="576a9-125">**System. io. IOException** : het bestand kan niet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="576a9-125">**System.IO.IOException** : The file could not be saved.</span></span>

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a><span data-ttu-id="576a9-126">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="576a9-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="576a9-127">DisplayName</span><span class="sxs-lookup"><span data-stu-id="576a9-127">DisplayName</span></span>

<span data-ttu-id="576a9-128">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="576a9-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="576a9-129">De alleen-lezen eigenschap waarmee de teken reeks wordt opgehaald die de weergave naam van dit bestand bevat.</span><span class="sxs-lookup"><span data-stu-id="576a9-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="576a9-130">De naam wordt weer gegeven op het tabblad **bestand** boven aan de editor.</span><span class="sxs-lookup"><span data-stu-id="576a9-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="576a9-131">De aanwezigheid van een sterretje `(*)` aan het einde van de naam geeft aan dat het bestand wijzigingen bevat die niet zijn opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="576a9-131">The presence of an asterisk `(*)` at the end of the name indicates that the file has changes that have not been saved.</span></span>

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a><span data-ttu-id="576a9-132">Editor</span><span class="sxs-lookup"><span data-stu-id="576a9-132">Editor</span></span>

<span data-ttu-id="576a9-133">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="576a9-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="576a9-134">De alleen-lezen eigenschap waarmee het [object editor](The-ISEEditor-Object.md) wordt opgehaald dat voor het opgegeven bestand wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="576a9-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a><span data-ttu-id="576a9-135">Encoding</span><span class="sxs-lookup"><span data-stu-id="576a9-135">Encoding</span></span>

<span data-ttu-id="576a9-136">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="576a9-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="576a9-137">De alleen-lezen eigenschap waarmee de oorspronkelijke bestands codering wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="576a9-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="576a9-138">Dit is een **System. Text. encoding** -object.</span><span class="sxs-lookup"><span data-stu-id="576a9-138">This is a **System.Text.Encoding** object.</span></span>

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a><span data-ttu-id="576a9-139">Pad</span><span class="sxs-lookup"><span data-stu-id="576a9-139">FullPath</span></span>

<span data-ttu-id="576a9-140">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="576a9-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="576a9-141">De alleen-lezen eigenschap waarmee de teken reeks wordt opgehaald die het volledige pad van het geopende bestand opgeeft.</span><span class="sxs-lookup"><span data-stu-id="576a9-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a><span data-ttu-id="576a9-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="576a9-142">IsSaved</span></span>

<span data-ttu-id="576a9-143">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="576a9-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="576a9-144">De alleen-lezen Booleaanse eigenschap die retourneert `$true` als het bestand is opgeslagen nadat het voor het laatst is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="576a9-144">The read-only Boolean property that returns `$true` if the file has been saved after it was last modified.</span></span>

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a><span data-ttu-id="576a9-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="576a9-145">IsUntitled</span></span>

<span data-ttu-id="576a9-146">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="576a9-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="576a9-147">De alleen-lezen eigenschap die retourneert `$true` als er nooit een titel is opgegeven voor het bestand.</span><span class="sxs-lookup"><span data-stu-id="576a9-147">The read-only property that returns `$true` if the file has never been given a title.</span></span>

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a><span data-ttu-id="576a9-148">Zie ook</span><span class="sxs-lookup"><span data-stu-id="576a9-148">See Also</span></span>

- [<span data-ttu-id="576a9-149">De ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="576a9-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md)
- [<span data-ttu-id="576a9-150">Doel van het scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="576a9-150">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="576a9-151">De ISE-object model hiërarchie</span><span class="sxs-lookup"><span data-stu-id="576a9-151">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
