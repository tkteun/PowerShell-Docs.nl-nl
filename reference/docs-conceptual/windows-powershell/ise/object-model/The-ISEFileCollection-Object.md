---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Het ISEFileCollection-object
ms.openlocfilehash: 4192afa9dc91d9ea4c4c084d3ba0175483620229
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810664"
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="d37c0-103">Het ISEFileCollection-object</span><span class="sxs-lookup"><span data-stu-id="d37c0-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="d37c0-104">Het **ISEFileCollection** -object is een verzameling **ISEFile** -objecten.</span><span class="sxs-lookup"><span data-stu-id="d37c0-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="d37c0-105">Een voor beeld is de `$psISE.CurrentPowerShellTab.Files` verzameling.</span><span class="sxs-lookup"><span data-stu-id="d37c0-105">An example is the `$psISE.CurrentPowerShellTab.Files` collection.</span></span>

## <a name="methods"></a><span data-ttu-id="d37c0-106">Methoden</span><span class="sxs-lookup"><span data-stu-id="d37c0-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="d37c0-107">\( \[ FullPath \] toevoegen\)</span><span class="sxs-lookup"><span data-stu-id="d37c0-107">Add\( \[FullPath\] \)</span></span>

<span data-ttu-id="d37c0-108">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="d37c0-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d37c0-109">Maakt en retourneert een nieuw naamloos bestand en voegt het toe aan de verzameling.</span><span class="sxs-lookup"><span data-stu-id="d37c0-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="d37c0-110">De eigenschap **IsUntitled** van het zojuist gemaakte bestand is `$true` .</span><span class="sxs-lookup"><span data-stu-id="d37c0-110">The **IsUntitled** property of the newly created file is `$true`.</span></span>

<span data-ttu-id="d37c0-111">\*\* \[ FullPath \] \*\* -optionele teken reeks het volledig opgegeven pad van het bestand.</span><span class="sxs-lookup"><span data-stu-id="d37c0-111">**\[FullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="d37c0-112">Er wordt een uitzonde ring gegenereerd als u de para meter **FullPath** en een relatief pad opneemt, of als u een bestands naam gebruikt in plaats van het volledige pad.</span><span class="sxs-lookup"><span data-stu-id="d37c0-112">An exception is generated if you include the **FullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="d37c0-113">\(Bestand verwijderen, \[ forceren \]\)</span><span class="sxs-lookup"><span data-stu-id="d37c0-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="d37c0-114">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="d37c0-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d37c0-115">Hiermee verwijdert u een opgegeven bestand van het huidige Power shell-tabblad.</span><span class="sxs-lookup"><span data-stu-id="d37c0-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="d37c0-116">**File** -teken reeks het ISEFile-bestand dat u wilt verwijderen uit de verzameling.</span><span class="sxs-lookup"><span data-stu-id="d37c0-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="d37c0-117">Als het bestand niet is opgeslagen, genereert deze methode een uitzonde ring.</span><span class="sxs-lookup"><span data-stu-id="d37c0-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="d37c0-118">Gebruik de para meter **forceren** om het verwijderen van een niet-opgeslagen bestand af te dwingen.</span><span class="sxs-lookup"><span data-stu-id="d37c0-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="d37c0-119">\*\* \[ Force \] \*\* -optionele Booleaanse waarde indien ingesteld op `$true` , geeft toestemming voor het verwijderen van het bestand, zelfs als het niet is opgeslagen na het laatste gebruik.</span><span class="sxs-lookup"><span data-stu-id="d37c0-119">**\[Force\]** - optional Boolean If set to `$true`, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="d37c0-120">De standaardwaarde is `$false`.</span><span class="sxs-lookup"><span data-stu-id="d37c0-120">The default is `$false`.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="d37c0-121">SetSelectedFile \( selectedFile\)</span><span class="sxs-lookup"><span data-stu-id="d37c0-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="d37c0-122">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="d37c0-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d37c0-123">Hiermee selecteert u het bestand dat is opgegeven door de para meter **SelectedFile** .</span><span class="sxs-lookup"><span data-stu-id="d37c0-123">Selects the file that is specified by the **SelectedFile** parameter.</span></span>

<span data-ttu-id="d37c0-124">**SelectedFile** : micro soft. Power shell. host. ISE. ISEFile het ISEFile-bestand dat u wilt selecteren.</span><span class="sxs-lookup"><span data-stu-id="d37c0-124">**SelectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="d37c0-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d37c0-125">See Also</span></span>

- [<span data-ttu-id="d37c0-126">Het ISEFile-object</span><span class="sxs-lookup"><span data-stu-id="d37c0-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="d37c0-127">Doel van het scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d37c0-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="d37c0-128">De ISE-object model hiërarchie</span><span class="sxs-lookup"><span data-stu-id="d37c0-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)