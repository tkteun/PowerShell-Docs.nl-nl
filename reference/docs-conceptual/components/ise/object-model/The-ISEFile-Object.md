---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEFile-object
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 24549720b8bc35435882533b0eb138de432ede65
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404406"
---
# <a name="the-isefile-object"></a><span data-ttu-id="c56e1-103">Het ISEFile-object</span><span class="sxs-lookup"><span data-stu-id="c56e1-103">The ISEFile Object</span></span>

<span data-ttu-id="c56e1-104">Een **ISEFile** object vertegenwoordigt een bestand in Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="c56e1-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="c56e1-105">Het is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="c56e1-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="c56e1-106">In dit onderwerp bevat de methoden en lideigenschappen.</span><span class="sxs-lookup"><span data-stu-id="c56e1-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="c56e1-107">De **$psISE.CurrentFile** en de bestanden in de verzameling bestanden in een PowerShell-tabblad zijn alle exemplaren van de klasse Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="c56e1-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="c56e1-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="c56e1-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="c56e1-109">Sla\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="c56e1-109">Save\( \[saveEncoding\] \)</span></span>

<span data-ttu-id="c56e1-110">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c56e1-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c56e1-111">Hiermee slaat u het bestand op schijf.</span><span class="sxs-lookup"><span data-stu-id="c56e1-111">Saves the file to disk.</span></span>

<span data-ttu-id="c56e1-112">**\[saveEncoding\]**  - optioneel [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) een optioneel teken codering parameter moet worden gebruikt voor het opgeslagen bestand.</span><span class="sxs-lookup"><span data-stu-id="c56e1-112">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="c56e1-113">De standaardwaarde is **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="c56e1-113">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="c56e1-114">Uitzonderingen</span><span class="sxs-lookup"><span data-stu-id="c56e1-114">Exceptions</span></span>

- <span data-ttu-id="c56e1-115">**System.IO.IOException**: Het bestand kan niet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="c56e1-115">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="c56e1-116">Opslaan\(filename, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="c56e1-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>

<span data-ttu-id="c56e1-117">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c56e1-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c56e1-118">Hiermee slaat u het bestand met de opgegeven bestandsnaam en de codering.</span><span class="sxs-lookup"><span data-stu-id="c56e1-118">Saves the file with the specified file name and encoding.</span></span>

<span data-ttu-id="c56e1-119">**FileName** -tekenreeks van de naam moet worden gebruikt om op te slaan van het bestand.</span><span class="sxs-lookup"><span data-stu-id="c56e1-119">**filename** - String The name to be used to save the file.</span></span>

<span data-ttu-id="c56e1-120">**\[saveEncoding\]**  - optioneel [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) een optioneel teken codering parameter moet worden gebruikt voor het opgeslagen bestand.</span><span class="sxs-lookup"><span data-stu-id="c56e1-120">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="c56e1-121">De standaardwaarde is **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="c56e1-121">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="c56e1-122">Uitzonderingen</span><span class="sxs-lookup"><span data-stu-id="c56e1-122">Exceptions</span></span>

- <span data-ttu-id="c56e1-123">**System.ArgumentNullException**: De **filename** -parameter is null.</span><span class="sxs-lookup"><span data-stu-id="c56e1-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>
- <span data-ttu-id="c56e1-124">**System.ArgumentException**: De **filename** parameter is leeg.</span><span class="sxs-lookup"><span data-stu-id="c56e1-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>
- <span data-ttu-id="c56e1-125">**System.IO.IOException**: Het bestand kan niet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="c56e1-125">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a><span data-ttu-id="c56e1-126">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="c56e1-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="c56e1-127">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c56e1-127">DisplayName</span></span>

<span data-ttu-id="c56e1-128">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c56e1-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c56e1-129">De alleen-lezen eigenschap die de tekenreeks zijn met de naam van dit bestand opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c56e1-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="c56e1-130">De naam wordt weergegeven op de **bestand** tabblad aan de bovenkant van de editor.</span><span class="sxs-lookup"><span data-stu-id="c56e1-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="c56e1-131">De aanwezigheid van een sterretje \( \* \) aan het einde van de naam van de geeft aan dat het bestand heeft die niet zijn opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="c56e1-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a><span data-ttu-id="c56e1-132">Editor</span><span class="sxs-lookup"><span data-stu-id="c56e1-132">Editor</span></span>

<span data-ttu-id="c56e1-133">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c56e1-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c56e1-134">De alleen-lezen eigenschap die krijgt de [editor-object](The-ISEEditor-Object.md) die wordt gebruikt voor het opgegeven bestand.</span><span class="sxs-lookup"><span data-stu-id="c56e1-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a><span data-ttu-id="c56e1-135">Encoding</span><span class="sxs-lookup"><span data-stu-id="c56e1-135">Encoding</span></span>

<span data-ttu-id="c56e1-136">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c56e1-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c56e1-137">De alleen-lezen eigenschap die de oorspronkelijke bestandscodering opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c56e1-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="c56e1-138">Dit is een **System.Text.Encoding** object.</span><span class="sxs-lookup"><span data-stu-id="c56e1-138">This is a **System.Text.Encoding** object.</span></span>

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a><span data-ttu-id="c56e1-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="c56e1-139">FullPath</span></span>

<span data-ttu-id="c56e1-140">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c56e1-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c56e1-141">De alleen-lezen eigenschap die de tekenreeks die Hiermee geeft u het volledige pad van het geopende bestand opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c56e1-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a><span data-ttu-id="c56e1-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="c56e1-142">IsSaved</span></span>

<span data-ttu-id="c56e1-143">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c56e1-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c56e1-144">De alleen-lezen Booleaanse eigenschap waarmee wordt geretourneerd **$true** als het bestand is opgeslagen nadat het laatst is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c56e1-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a><span data-ttu-id="c56e1-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="c56e1-145">IsUntitled</span></span>

<span data-ttu-id="c56e1-146">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c56e1-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c56e1-147">De alleen-lezen eigenschap die retourneert **$true** als het bestand nooit een titel ontvangen heeft.</span><span class="sxs-lookup"><span data-stu-id="c56e1-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a><span data-ttu-id="c56e1-148">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c56e1-148">See Also</span></span>

- [<span data-ttu-id="c56e1-149">De ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="c56e1-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md)
- [<span data-ttu-id="c56e1-150">Doel van de Scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c56e1-150">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="c56e1-151">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="c56e1-151">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)