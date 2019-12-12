---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Het PowerShellTabCollection-object
ms.openlocfilehash: 5a1318534ddce19c2f5faa0d2013e2b38d8b79e5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030483"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="ee6a7-103">Het PowerShellTabCollection-object</span><span class="sxs-lookup"><span data-stu-id="ee6a7-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="ee6a7-104">Het **PowerShellTab** -verzamelings object is een verzameling **PowerShellTab** -objecten.</span><span class="sxs-lookup"><span data-stu-id="ee6a7-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="ee6a7-105">Elk **PowerShellTab** -object fungeert als een afzonderlijke runtime-omgeving.</span><span class="sxs-lookup"><span data-stu-id="ee6a7-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="ee6a7-106">Het is een exemplaar van de klasse micro soft. Power shell. host. ISE. PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="ee6a7-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="ee6a7-107">Een voor beeld is het **$psISE. PowerShellTabs** -object.</span><span class="sxs-lookup"><span data-stu-id="ee6a7-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="ee6a7-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="ee6a7-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="ee6a7-109">\(\) toevoegen</span><span class="sxs-lookup"><span data-stu-id="ee6a7-109">Add\(\)</span></span>

<span data-ttu-id="ee6a7-110">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="ee6a7-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ee6a7-111">Hiermee voegt u een nieuw Power shell-tabblad aan de verzameling toe.</span><span class="sxs-lookup"><span data-stu-id="ee6a7-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="ee6a7-112">Het zojuist toegevoegde tabblad wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ee6a7-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="ee6a7-113">Verwijder\(Microsoft. Power shell. host. ISE. PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="ee6a7-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="ee6a7-114">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="ee6a7-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ee6a7-115">Hiermee verwijdert u het tabblad dat is opgegeven door de para meter **psTab** .</span><span class="sxs-lookup"><span data-stu-id="ee6a7-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="ee6a7-116">**psTab** Het Power shell-tabblad dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ee6a7-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="ee6a7-117">SetSelectedPowerShellTab\(micro soft. Power shell. host. ISE. PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="ee6a7-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="ee6a7-118">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="ee6a7-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ee6a7-119">Hiermee selecteert u het Power shell-tabblad dat is opgegeven door de para meter **psTab** om het momenteel actieve Power shell-tabblad te maken.</span><span class="sxs-lookup"><span data-stu-id="ee6a7-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="ee6a7-120">**psTab** Het Power shell-tabblad om te selecteren.</span><span class="sxs-lookup"><span data-stu-id="ee6a7-120">**psTab** The PowerShell tab to select.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ee6a7-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ee6a7-121">See Also</span></span>

- [<span data-ttu-id="ee6a7-122">Het PowerShellTab-object</span><span class="sxs-lookup"><span data-stu-id="ee6a7-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="ee6a7-123">Doel van het Windows PowerShell ISE scripting object model</span><span class="sxs-lookup"><span data-stu-id="ee6a7-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="ee6a7-124">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="ee6a7-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
