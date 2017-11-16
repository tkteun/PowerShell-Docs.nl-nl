---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Het Object ISEFile
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: a1fbd48e872684cc578adb03f52430eabdc54c2c
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefile-object"></a><span data-ttu-id="7bc24-103">Het Object ISEFile</span><span class="sxs-lookup"><span data-stu-id="7bc24-103">The ISEFile Object</span></span>
  <span data-ttu-id="7bc24-104">Een **ISEFile** object vertegenwoordigt een bestand in Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="7bc24-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="7bc24-105">Er is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="7bc24-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="7bc24-106">In dit onderwerp bevat de methoden en eigenschappen van lid.</span><span class="sxs-lookup"><span data-stu-id="7bc24-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="7bc24-107">De **$psISE.CurrentFile** en de bestanden in de verzameling bestanden op een tabblad PowerShell zijn alle exemplaren van de klasse Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="7bc24-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="7bc24-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="7bc24-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="7bc24-109">Sla\( \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="7bc24-109">Save\( \[saveEncoding\] \)</span></span>
  <span data-ttu-id="7bc24-110">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7bc24-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="7bc24-111">Het bestand opslaat op schijf.</span><span class="sxs-lookup"><span data-stu-id="7bc24-111">Saves the file to disk.</span></span>

 <span data-ttu-id="7bc24-112">**\[saveEncoding\]**  : optioneel [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) een optioneel teken codering van de parameter moet worden gebruikt voor het opgeslagen bestand.</span><span class="sxs-lookup"><span data-stu-id="7bc24-112">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="7bc24-113">De standaardwaarde is **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="7bc24-113">The default value is **UTF8**.</span></span>

 <span data-ttu-id="7bc24-114">**Uitzonderingen**</span><span class="sxs-lookup"><span data-stu-id="7bc24-114">**Exceptions**</span></span>
 -   <span data-ttu-id="7bc24-115">**System.IO.IOException**: het bestand kan niet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="7bc24-115">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="7bc24-116">SaveAs\(bestandsnaam, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="7bc24-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>
  <span data-ttu-id="7bc24-117">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7bc24-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="7bc24-118">Hiermee slaat u het bestand met de opgegeven bestandsnaam en de codering.</span><span class="sxs-lookup"><span data-stu-id="7bc24-118">Saves the file with the specified file name and encoding.</span></span>

 <span data-ttu-id="7bc24-119">**bestandsnaam** -tekenreeks van de naam die moet worden gebruikt voor het opslaan van het bestand.</span><span class="sxs-lookup"><span data-stu-id="7bc24-119">**filename** - String The name to be used to save the file.</span></span>

 <span data-ttu-id="7bc24-120">**\[saveEncoding\]**  : optioneel [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) een optioneel teken codering van de parameter moet worden gebruikt voor het opgeslagen bestand.</span><span class="sxs-lookup"><span data-stu-id="7bc24-120">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="7bc24-121">De standaardwaarde is **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="7bc24-121">The default value is **UTF8**.</span></span>

 <span data-ttu-id="7bc24-122">**Uitzonderingen**</span><span class="sxs-lookup"><span data-stu-id="7bc24-122">**Exceptions**</span></span>
 -   <span data-ttu-id="7bc24-123">**System.ArgumentNullException**: de **filename** -parameter is null.</span><span class="sxs-lookup"><span data-stu-id="7bc24-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>

- <span data-ttu-id="7bc24-124">**System.ArgumentException**: de **filename** parameter is leeg.</span><span class="sxs-lookup"><span data-stu-id="7bc24-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>

- <span data-ttu-id="7bc24-125">**System.IO.IOException**: het bestand kan niet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="7bc24-125">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a><span data-ttu-id="7bc24-126">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="7bc24-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="7bc24-127">DisplayName</span><span class="sxs-lookup"><span data-stu-id="7bc24-127">DisplayName</span></span>
  <span data-ttu-id="7bc24-128">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7bc24-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="7bc24-129">De alleen-lezen eigenschap waarin de tekenreeks met de weergavenaam van dit bestand worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7bc24-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="7bc24-130">De naam wordt weergegeven op de **bestand** boven op het tabblad van de editor.</span><span class="sxs-lookup"><span data-stu-id="7bc24-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="7bc24-131">De aanwezigheid van een sterretje \( \* \) aan het einde van de naam geeft aan dat het bestand wijzigingen die niet zijn opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="7bc24-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

### <a name="editor"></a><span data-ttu-id="7bc24-132">Editor</span><span class="sxs-lookup"><span data-stu-id="7bc24-132">Editor</span></span>
  <span data-ttu-id="7bc24-133">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7bc24-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="7bc24-134">De alleen-lezen eigenschap die krijgt de [editor-object](The-ISEEditor-Object.md) die wordt gebruikt voor het opgegeven bestand.</span><span class="sxs-lookup"><span data-stu-id="7bc24-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

### <a name="encoding"></a><span data-ttu-id="7bc24-135">Codering</span><span class="sxs-lookup"><span data-stu-id="7bc24-135">Encoding</span></span>
  <span data-ttu-id="7bc24-136">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7bc24-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="7bc24-137">De alleen-lezen eigenschap die de oorspronkelijke bestandscodering opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7bc24-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="7bc24-138">Dit is een **System.Text.Encoding** object.</span><span class="sxs-lookup"><span data-stu-id="7bc24-138">This is a **System.Text.Encoding** object.</span></span>

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

### <a name="fullpath"></a><span data-ttu-id="7bc24-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="7bc24-139">FullPath</span></span>
  <span data-ttu-id="7bc24-140">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7bc24-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="7bc24-141">De alleen-lezen eigenschap die de tekenreeks die opgeeft van het volledige pad van het geopende bestand opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7bc24-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

### <a name="issaved"></a><span data-ttu-id="7bc24-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="7bc24-142">IsSaved</span></span>
  <span data-ttu-id="7bc24-143">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7bc24-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="7bc24-144">De alleen-lezen Boole-eigenschap die als resultaat geeft **$true** als het bestand is opgeslagen nadat het laatst is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="7bc24-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

### <a name="isuntitled"></a><span data-ttu-id="7bc24-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="7bc24-145">IsUntitled</span></span>
  <span data-ttu-id="7bc24-146">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7bc24-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="7bc24-147">De alleen-lezen eigenschap die retourneert **$true** als het bestand nooit een titel gegeven is.</span><span class="sxs-lookup"><span data-stu-id="7bc24-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a><span data-ttu-id="7bc24-148">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7bc24-148">See Also</span></span>
- [<span data-ttu-id="7bc24-149">De ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="7bc24-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md) 
- [<span data-ttu-id="7bc24-150">De Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="7bc24-150">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="7bc24-151">Naslaginformatie voor Windows PowerShell ISE-objectmodel</span><span class="sxs-lookup"><span data-stu-id="7bc24-151">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="7bc24-152">De hiërarchie ISE</span><span class="sxs-lookup"><span data-stu-id="7bc24-152">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
