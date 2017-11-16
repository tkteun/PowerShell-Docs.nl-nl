---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Het Object ISEFileCollection
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: 60bf4dae33f3a71c31e7fdbed0f4fd6ab27a8bd1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="87440-103">Het Object ISEFileCollection</span><span class="sxs-lookup"><span data-stu-id="87440-103">The ISEFileCollection Object</span></span>
  <span data-ttu-id="87440-104">De **ISEFileCollection** object is een verzameling **ISEFile** objecten.</span><span class="sxs-lookup"><span data-stu-id="87440-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="87440-105">Een voorbeeld is de verzameling $psISE.CurrentPowerShellTab.Files.</span><span class="sxs-lookup"><span data-stu-id="87440-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="87440-106">Methoden</span><span class="sxs-lookup"><span data-stu-id="87440-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="87440-107">Voeg\( \[fullPath\]\)</span><span class="sxs-lookup"><span data-stu-id="87440-107">Add\( \[fullPath\] \)</span></span>
  <span data-ttu-id="87440-108">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="87440-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="87440-109">Maakt een nieuw bestand naamloze retourneert en voegt het toe aan de verzameling.</span><span class="sxs-lookup"><span data-stu-id="87440-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="87440-110">De **IsUntitled** eigenschap van het nieuwe bestand is **$true**.</span><span class="sxs-lookup"><span data-stu-id="87440-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

 <span data-ttu-id="87440-111">**\[fullPath\]**  : optioneel het volledig opgegeven pad van het bestand string.</span><span class="sxs-lookup"><span data-stu-id="87440-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="87440-112">Er is een uitzondering gegenereerd als u de **fullPath** parameter en een relatief pad, of als u een bestandsnaam in plaats van het volledige pad gebruikt.</span><span class="sxs-lookup"><span data-stu-id="87440-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")

```

### <a name="remove-file-force-"></a><span data-ttu-id="87440-113">Verwijder\( bestand \[Force\]\)</span><span class="sxs-lookup"><span data-stu-id="87440-113">Remove\( File, \[Force\] \)</span></span>
  <span data-ttu-id="87440-114">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="87440-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="87440-115">Verwijdert een opgegeven bestand uit het huidige PowerShell-tabblad.</span><span class="sxs-lookup"><span data-stu-id="87440-115">Removes a specified file from the current PowerShell tab.</span></span>

 <span data-ttu-id="87440-116">**Bestand** -tekenreeks de ISEFile-bestand dat u wilt verwijderen uit de verzameling.</span><span class="sxs-lookup"><span data-stu-id="87440-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="87440-117">Als het bestand niet opgeslagen is, is deze methode er een uitzondering gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="87440-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="87440-118">Gebruik de **forceren** overschakelen van de parameter voor het afdwingen van het verwijderen van een niet-opgeslagen bestand.</span><span class="sxs-lookup"><span data-stu-id="87440-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

 <span data-ttu-id="87440-119">**\[Force\]**  -optionele Booleaanse als ingesteld op **$true**, verleent u machtiging voor het verwijderen van het bestand, zelfs als deze niet na de laatste keer is opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="87440-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="87440-120">De standaardwaarde is **$false**.</span><span class="sxs-lookup"><span data-stu-id="87440-120">The default is **$false**.</span></span>

```
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="87440-121">SetSelectedFile\( selectedFile\)</span><span class="sxs-lookup"><span data-stu-id="87440-121">SetSelectedFile\( selectedFile \)</span></span>
  <span data-ttu-id="87440-122">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="87440-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="87440-123">Hiermee selecteert u het bestand dat is opgegeven door de **selectedFile** parameter.</span><span class="sxs-lookup"><span data-stu-id="87440-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

 <span data-ttu-id="87440-124">**selectedFile** -Microsoft.PowerShell.Host.ISE.ISEFile de ISEFile-bestand dat u wilt selecteren.</span><span class="sxs-lookup"><span data-stu-id="87440-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```

# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)

```

## <a name="see-also"></a><span data-ttu-id="87440-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="87440-125">See Also</span></span>
- [<span data-ttu-id="87440-126">Het Object ISEFile</span><span class="sxs-lookup"><span data-stu-id="87440-126">The ISEFile Object</span></span>](The-ISEFile-Object.md) 
- [<span data-ttu-id="87440-127">De Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="87440-127">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="87440-128">Naslaginformatie voor Windows PowerShell ISE-objectmodel</span><span class="sxs-lookup"><span data-stu-id="87440-128">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="87440-129">De hiërarchie ISE</span><span class="sxs-lookup"><span data-stu-id="87440-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
