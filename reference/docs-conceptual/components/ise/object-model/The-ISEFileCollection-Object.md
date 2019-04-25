---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEFileCollection-object
ms.assetid: 0f86a427-ea38-4bce-85f8-06c98d30d508
ms.openlocfilehash: eb4b2784820cbe51f662fd2fd945d8760ef9dbff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086745"
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="4b600-103">Het ISEFileCollection-object</span><span class="sxs-lookup"><span data-stu-id="4b600-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="4b600-104">De **ISEFileCollection** object is een verzameling van **ISEFile** objecten.</span><span class="sxs-lookup"><span data-stu-id="4b600-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="4b600-105">Een voorbeeld is de verzameling $psISE.CurrentPowerShellTab.Files.</span><span class="sxs-lookup"><span data-stu-id="4b600-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="4b600-106">Methoden</span><span class="sxs-lookup"><span data-stu-id="4b600-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="4b600-107">Voeg\( \[fullPath\] \)</span><span class="sxs-lookup"><span data-stu-id="4b600-107">Add\( \[fullPath\] \)</span></span>

<span data-ttu-id="4b600-108">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="4b600-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="4b600-109">Maakt en retourneert een nieuwe naamloos bestand en toegevoegd aan de verzameling.</span><span class="sxs-lookup"><span data-stu-id="4b600-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="4b600-110">De **IsUntitled** eigenschap van het zojuist gemaakte bestand is **$true**.</span><span class="sxs-lookup"><span data-stu-id="4b600-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

<span data-ttu-id="4b600-111">**\[fullPath\]**  - optioneel het volledig opgegeven pad van het bestand de tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="4b600-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="4b600-112">Een uitzondering wordt gegenereerd als u de **fullPath** parameter en een relatief pad, of als u een bestandsnaam in plaats van het volledige pad gebruiken.</span><span class="sxs-lookup"><span data-stu-id="4b600-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="4b600-113">Verwijder\( bestand \[forceren\] \)</span><span class="sxs-lookup"><span data-stu-id="4b600-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="4b600-114">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="4b600-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="4b600-115">Hiermee verwijdert u een opgegeven bestand van het huidige PowerShell-tabblad.</span><span class="sxs-lookup"><span data-stu-id="4b600-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="4b600-116">**Bestand** -tekenreeks het ISEFile-bestand dat u wilt verwijderen uit de verzameling.</span><span class="sxs-lookup"><span data-stu-id="4b600-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="4b600-117">Als het bestand niet is opgeslagen, wordt met deze methode een uitzondering genereert.</span><span class="sxs-lookup"><span data-stu-id="4b600-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="4b600-118">Gebruik de **forceren** overschakelen van de parameter als u wilt afdwingen dat het verwijderen van een niet-opgeslagen bestand.</span><span class="sxs-lookup"><span data-stu-id="4b600-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="4b600-119">**\[Force\]**  -optionele Booleaanse als ingesteld op **$true**, een machtiging verleend voor het verwijderen van het bestand, zelfs als deze niet na het laatst hebt gebruikt opgeslagen is.</span><span class="sxs-lookup"><span data-stu-id="4b600-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="4b600-120">De standaardwaarde is **$false**.</span><span class="sxs-lookup"><span data-stu-id="4b600-120">The default is **$false**.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="4b600-121">SetSelectedFile\( selectedFile \)</span><span class="sxs-lookup"><span data-stu-id="4b600-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="4b600-122">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="4b600-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="4b600-123">Hiermee selecteert u het bestand dat is opgegeven door de **selectedFile** parameter.</span><span class="sxs-lookup"><span data-stu-id="4b600-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

<span data-ttu-id="4b600-124">**selectedFile** -Microsoft.PowerShell.Host.ISE.ISEFile het ISEFile-bestand dat u wilt selecteren.</span><span class="sxs-lookup"><span data-stu-id="4b600-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="4b600-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4b600-125">See Also</span></span>

- [<span data-ttu-id="4b600-126">Het ISEFile-Object</span><span class="sxs-lookup"><span data-stu-id="4b600-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="4b600-127">Doel van de Scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="4b600-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="4b600-128">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="4b600-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)