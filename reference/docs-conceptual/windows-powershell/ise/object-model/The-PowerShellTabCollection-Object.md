---
ms.date: 06/05/2017
title: Het PowerShellTabCollection-object
description: Het PowerShellTab-verzamelings object is een verzameling PowerShellTab-objecten. Elk PowerShellTab-object fungeert als een afzonderlijke runtime-omgeving.
ms.openlocfilehash: 60f8001f096b50bd8433a5685f1f70a350f07f61
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658267"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="d3853-104">Het PowerShellTabCollection-object</span><span class="sxs-lookup"><span data-stu-id="d3853-104">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="d3853-105">Het **PowerShellTab** -verzamelings object is een verzameling **PowerShellTab** -objecten.</span><span class="sxs-lookup"><span data-stu-id="d3853-105">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="d3853-106">Elk **PowerShellTab** -object fungeert als een afzonderlijke runtime-omgeving.</span><span class="sxs-lookup"><span data-stu-id="d3853-106">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="d3853-107">Het is een exemplaar van de klasse micro soft. Power shell. host. ISE. PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="d3853-107">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="d3853-108">Een voor beeld is het `$psISE.PowerShellTabs` object.</span><span class="sxs-lookup"><span data-stu-id="d3853-108">An example is the `$psISE.PowerShellTabs` object.</span></span>

## <a name="methods"></a><span data-ttu-id="d3853-109">Methoden</span><span class="sxs-lookup"><span data-stu-id="d3853-109">Methods</span></span>

### <a name="add"></a><span data-ttu-id="d3853-110">Toe\(\)</span><span class="sxs-lookup"><span data-stu-id="d3853-110">Add\(\)</span></span>

<span data-ttu-id="d3853-111">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="d3853-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d3853-112">Hiermee voegt u een nieuw Power shell-tabblad aan de verzameling toe.</span><span class="sxs-lookup"><span data-stu-id="d3853-112">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="d3853-113">Het zojuist toegevoegde tabblad wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d3853-113">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="d3853-114">Verwijder \( micro soft. Power shell. host. ISE. PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="d3853-114">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="d3853-115">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="d3853-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d3853-116">Hiermee verwijdert u het tabblad dat is opgegeven door de para meter **psTab** .</span><span class="sxs-lookup"><span data-stu-id="d3853-116">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="d3853-117">**psTab** Het Power shell-tabblad dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d3853-117">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="d3853-118">SetSelectedPowerShellTab \( micro soft. Power shell. host. ISE. PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="d3853-118">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="d3853-119">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="d3853-119">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d3853-120">Hiermee selecteert u het Power shell-tabblad dat is opgegeven door de para meter **psTab** om het momenteel actieve Power shell-tabblad te maken.</span><span class="sxs-lookup"><span data-stu-id="d3853-120">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="d3853-121">**psTab** Het Power shell-tabblad om te selecteren.</span><span class="sxs-lookup"><span data-stu-id="d3853-121">**psTab** The PowerShell tab to select.</span></span>

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a><span data-ttu-id="d3853-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d3853-122">See Also</span></span>

- [<span data-ttu-id="d3853-123">Het PowerShellTab-object</span><span class="sxs-lookup"><span data-stu-id="d3853-123">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="d3853-124">Doel van het scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d3853-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="d3853-125">De ISE-object model hiërarchie</span><span class="sxs-lookup"><span data-stu-id="d3853-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
