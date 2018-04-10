---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het PowerShellTabCollection-object
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="2706a-103">Het PowerShellTabCollection-object</span><span class="sxs-lookup"><span data-stu-id="2706a-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="2706a-104">De **PowerShellTab** verzamelingsobject is een verzameling **PowerShellTab** objecten.</span><span class="sxs-lookup"><span data-stu-id="2706a-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="2706a-105">Elke **PowerShellTab** object fungeert als een afzonderlijke runtime-omgeving.</span><span class="sxs-lookup"><span data-stu-id="2706a-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="2706a-106">Het is een instantie van klasse Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="2706a-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="2706a-107">Een voorbeeld is de **$psISE.PowerShellTabs** object.</span><span class="sxs-lookup"><span data-stu-id="2706a-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="2706a-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="2706a-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="2706a-109">toevoegen\(\)</span><span class="sxs-lookup"><span data-stu-id="2706a-109">Add\(\)</span></span>

<span data-ttu-id="2706a-110">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="2706a-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2706a-111">Voegt een nieuwe PowerShell-tabblad toe aan de verzameling.</span><span class="sxs-lookup"><span data-stu-id="2706a-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="2706a-112">Retourneert het zojuist toegevoegde tabblad.</span><span class="sxs-lookup"><span data-stu-id="2706a-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="2706a-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="2706a-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="2706a-114">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="2706a-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2706a-115">Hiermee verwijdert u het tabblad dat wordt opgegeven door de **psTab** parameter.</span><span class="sxs-lookup"><span data-stu-id="2706a-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="2706a-116">**psTab** het PowerShell-tabblad te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="2706a-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="2706a-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="2706a-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="2706a-118">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="2706a-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2706a-119">Hiermee selecteert u het PowerShell-tabblad die is opgegeven door de **psTab** parameter zodat deze de momenteel actieve PowerShell-tabblad.</span><span class="sxs-lookup"><span data-stu-id="2706a-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="2706a-120">**psTab** het PowerShell-tab om te selecteren.</span><span class="sxs-lookup"><span data-stu-id="2706a-120">**psTab** The PowerShell tab to select.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2706a-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2706a-121">See Also</span></span>

- [<span data-ttu-id="2706a-122">Het Object PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="2706a-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="2706a-123">Doel van de Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="2706a-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="2706a-124">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="2706a-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)