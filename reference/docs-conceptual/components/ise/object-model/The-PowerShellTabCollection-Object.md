---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Het PowerShellTabCollection-object
ms.openlocfilehash: 0aad885afd3ba3ae3b00f5c11d2c62a9ff303798
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736110"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="3f893-103">Het PowerShellTabCollection-object</span><span class="sxs-lookup"><span data-stu-id="3f893-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="3f893-104">Het **PowerShellTab** -verzamelings object is een verzameling **PowerShellTab** -objecten.</span><span class="sxs-lookup"><span data-stu-id="3f893-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="3f893-105">Elk **PowerShellTab** -object fungeert als een afzonderlijke runtime-omgeving.</span><span class="sxs-lookup"><span data-stu-id="3f893-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="3f893-106">Het is een exemplaar van de klasse micro soft. Power shell. host. ISE. PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="3f893-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="3f893-107">Een voor beeld is `$psISE.PowerShellTabs` het object.</span><span class="sxs-lookup"><span data-stu-id="3f893-107">An example is the `$psISE.PowerShellTabs` object.</span></span>

## <a name="methods"></a><span data-ttu-id="3f893-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="3f893-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="3f893-109">Toe\(\)</span><span class="sxs-lookup"><span data-stu-id="3f893-109">Add\(\)</span></span>

<span data-ttu-id="3f893-110">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="3f893-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="3f893-111">Hiermee voegt u een nieuw Power shell-tabblad aan de verzameling toe.</span><span class="sxs-lookup"><span data-stu-id="3f893-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="3f893-112">Het zojuist toegevoegde tabblad wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3f893-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="3f893-113">Verwijder\(micro soft. Power shell. host. ISE. PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="3f893-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="3f893-114">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="3f893-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="3f893-115">Hiermee verwijdert u het tabblad dat is opgegeven door de para meter **psTab** .</span><span class="sxs-lookup"><span data-stu-id="3f893-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="3f893-116">**psTab** Het Power shell-tabblad dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="3f893-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="3f893-117">SetSelectedPowerShellTab\(micro soft. Power shell. host. ISE. PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="3f893-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="3f893-118">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="3f893-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="3f893-119">Hiermee selecteert u het Power shell-tabblad dat is opgegeven door de para meter **psTab** om het momenteel actieve Power shell-tabblad te maken.</span><span class="sxs-lookup"><span data-stu-id="3f893-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="3f893-120">**psTab** Het Power shell-tabblad om te selecteren.</span><span class="sxs-lookup"><span data-stu-id="3f893-120">**psTab** The PowerShell tab to select.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3f893-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3f893-121">See Also</span></span>

- [<span data-ttu-id="3f893-122">Het PowerShellTab-object</span><span class="sxs-lookup"><span data-stu-id="3f893-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="3f893-123">Doel van het scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="3f893-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="3f893-124">De ISE-object model hiërarchie</span><span class="sxs-lookup"><span data-stu-id="3f893-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
