---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Het Object PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: dcdc16ae126453b6ade64917ac4950cc05e5f8ad
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="ff612-103">Het Object PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="ff612-103">The PowerShellTabCollection Object</span></span>
  <span data-ttu-id="ff612-104">De **PowerShellTab** verzamelingsobject is een verzameling **PowerShellTab** objecten.</span><span class="sxs-lookup"><span data-stu-id="ff612-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="ff612-105">Elke **PowerShellTab** object fungeert als een afzonderlijke runtime-omgeving.</span><span class="sxs-lookup"><span data-stu-id="ff612-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="ff612-106">Het is een instantie van klasse Microsoft.PowerShell.Host.ISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="ff612-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="ff612-107">Een voorbeeld is de **$psISE.PowerShellTabs** object.</span><span class="sxs-lookup"><span data-stu-id="ff612-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="ff612-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="ff612-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="ff612-109">Toevoegen\(\)</span><span class="sxs-lookup"><span data-stu-id="ff612-109">Add\(\)</span></span>
  <span data-ttu-id="ff612-110">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ff612-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff612-111">Voegt een nieuwe PowerShell-tabblad toe aan de verzameling.</span><span class="sxs-lookup"><span data-stu-id="ff612-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="ff612-112">Retourneert het zojuist toegevoegde tabblad.</span><span class="sxs-lookup"><span data-stu-id="ff612-112">It returns the newly added tab.</span></span>

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="ff612-113">Verwijder\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="ff612-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="ff612-114">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ff612-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff612-115">Hiermee verwijdert u het tabblad dat wordt opgegeven door de **psTab** parameter.</span><span class="sxs-lookup"><span data-stu-id="ff612-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

 <span data-ttu-id="ff612-116">**psTab** het PowerShell-tabblad te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="ff612-116">**psTab** The PowerShell tab to remove.</span></span>

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="ff612-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="ff612-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="ff612-118">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ff612-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="ff612-119">Hiermee selecteert u het PowerShell-tabblad die is opgegeven door de **psTab** parameter zodat deze de momenteel actieve PowerShell-tabblad.</span><span class="sxs-lookup"><span data-stu-id="ff612-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

 <span data-ttu-id="ff612-120">**psTab** het PowerShell-tab om te selecteren.</span><span class="sxs-lookup"><span data-stu-id="ff612-120">**psTab** The PowerShell tab to select.</span></span>

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## <a name="see-also"></a><span data-ttu-id="ff612-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ff612-121">See Also</span></span>
- [<span data-ttu-id="ff612-122">Het Object PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="ff612-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="ff612-123">De Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="ff612-123">The Windows PowerShell ISE Scripting Object Model</span></span>](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="ff612-124">Naslaginformatie voor Windows PowerShell ISE-objectmodel</span><span class="sxs-lookup"><span data-stu-id="ff612-124">Windows PowerShell ISE Object Model Reference</span></span>](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="ff612-125">De hiërarchie ISE</span><span class="sxs-lookup"><span data-stu-id="ff612-125">The ISE Object Model Hierarchy</span></span>](../ise/The-ISE-Object-Model-Hierarchy.md)

  
