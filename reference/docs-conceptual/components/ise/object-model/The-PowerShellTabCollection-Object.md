---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het PowerShellTabCollection-object
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086609"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="58f1b-103">Het PowerShellTabCollection-object</span><span class="sxs-lookup"><span data-stu-id="58f1b-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="58f1b-104">De **PowerShellTab** verzamelingsobject is een verzameling van **PowerShellTab** objecten.</span><span class="sxs-lookup"><span data-stu-id="58f1b-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="58f1b-105">Elke **PowerShellTab** object fungeert als een aparte runtime-omgeving.</span><span class="sxs-lookup"><span data-stu-id="58f1b-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="58f1b-106">Het is een exemplaar van Microsoft.PowerShell.Host.ISE.PowerShellTabs klasse.</span><span class="sxs-lookup"><span data-stu-id="58f1b-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="58f1b-107">Een voorbeeld is de **$psISE.PowerShellTabs** object.</span><span class="sxs-lookup"><span data-stu-id="58f1b-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="58f1b-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="58f1b-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="58f1b-109">Toevoegen\(\)</span><span class="sxs-lookup"><span data-stu-id="58f1b-109">Add\(\)</span></span>

<span data-ttu-id="58f1b-110">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="58f1b-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="58f1b-111">Voegt een nieuwe PowerShell-tabblad toe aan de verzameling.</span><span class="sxs-lookup"><span data-stu-id="58f1b-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="58f1b-112">Retourneert het zojuist toegevoegde tabblad.</span><span class="sxs-lookup"><span data-stu-id="58f1b-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="58f1b-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="58f1b-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="58f1b-114">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="58f1b-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="58f1b-115">Hiermee verwijdert u het tabblad dat is opgegeven door de **psTab** parameter.</span><span class="sxs-lookup"><span data-stu-id="58f1b-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="58f1b-116">**psTab** de PowerShell-tabblad om te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="58f1b-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="58f1b-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="58f1b-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="58f1b-118">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="58f1b-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="58f1b-119">Hiermee selecteert u het PowerShell-tabblad die is opgegeven door de **psTab** parameter gemakkelijk de momenteel actieve PowerShell-tabblad.</span><span class="sxs-lookup"><span data-stu-id="58f1b-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="58f1b-120">**psTab** de PowerShell-tabblad om te selecteren.</span><span class="sxs-lookup"><span data-stu-id="58f1b-120">**psTab** The PowerShell tab to select.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="58f1b-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="58f1b-121">See Also</span></span>

- [<span data-ttu-id="58f1b-122">The PowerShellTab Object</span><span class="sxs-lookup"><span data-stu-id="58f1b-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="58f1b-123">Doel van de Scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="58f1b-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="58f1b-124">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="58f1b-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)