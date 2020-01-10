---
ms.date: 12/31/2019
keywords: Power shell, cmdlet
title: Het ISEAddOnToolCollection-object
ms.openlocfilehash: e07a47169381307b50ac190165307c926b4ad94e
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737012"
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="9b995-103">Het ISEAddOnToolCollection-object</span><span class="sxs-lookup"><span data-stu-id="9b995-103">The ISEAddOnToolCollection Object</span></span>

<span data-ttu-id="9b995-104">Het **ISEAddOnToolCollection** -object is een verzameling **ISEAddOnTool** -objecten.</span><span class="sxs-lookup"><span data-stu-id="9b995-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="9b995-105">Een voor beeld is het `$psISE.CurrentPowerShellTab.VerticalAddOnTools`-object.</span><span class="sxs-lookup"><span data-stu-id="9b995-105">An example is the `$psISE.CurrentPowerShellTab.VerticalAddOnTools` object.</span></span>

## <a name="methods"></a><span data-ttu-id="9b995-106">Methoden</span><span class="sxs-lookup"><span data-stu-id="9b995-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="9b995-107">\( name, ControlType, \[IsVisible\] \) toevoegen</span><span class="sxs-lookup"><span data-stu-id="9b995-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>

<span data-ttu-id="9b995-108">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="9b995-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="9b995-109">Hiermee voegt u een nieuw hulp programma toe aan de verzameling.</span><span class="sxs-lookup"><span data-stu-id="9b995-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="9b995-110">Hiermee wordt het zojuist toegevoegde hulp programma voor toevoegen geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="9b995-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="9b995-111">Voordat u deze opdracht uitvoert, moet u het hulp programma voor toevoegen installeren op de lokale computer en de assembly laden.</span><span class="sxs-lookup"><span data-stu-id="9b995-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

<span data-ttu-id="9b995-112">**Naam** -teken reeks Hiermee geeft u de weergave naam op van het hulp programma voor toevoegen dat wordt toegevoegd aan Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9b995-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

<span data-ttu-id="9b995-113">**ControlType** -type Hiermee geeft u het besturings element op dat wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="9b995-113">**ControlType** -Type Specifies the control that is added.</span></span>

<span data-ttu-id="9b995-114">**\[IsVisible\]** -optionele Booleaanse waarde als deze is ingesteld op `$true`, wordt het hulp programma voor toevoegen direct weer gegeven in het bijbehorende deel venster.</span><span class="sxs-lookup"><span data-stu-id="9b995-114">**\[IsVisible\]** - optional Boolean If set to `$true`, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="9b995-115">\( item verwijderen \)</span><span class="sxs-lookup"><span data-stu-id="9b995-115">Remove\( Item \)</span></span>

<span data-ttu-id="9b995-116">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="9b995-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="9b995-117">Hiermee verwijdert u het opgegeven hulp programma voor invoeg toepassingen uit de verzameling.</span><span class="sxs-lookup"><span data-stu-id="9b995-117">Removes the specified add-on tool from the collection.</span></span>

<span data-ttu-id="9b995-118">**Item** -Microsoft. Power shell. host. ISE. ISEAddOnTool geeft het object op dat uit Windows PowerShell ISE moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="9b995-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="9b995-119">SetSelectedPowerShellTab\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="9b995-119">SetSelectedPowerShellTab\( psTab \)</span></span>

<span data-ttu-id="9b995-120">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="9b995-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="9b995-121">Hiermee selecteert u het Power shell-tabblad waarop de para meter **psTab** is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9b995-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="9b995-122">**psTab** : micro soft. Power shell. host. ISE. PowerShellTab het Power shell-tabblad om te selecteren.</span><span class="sxs-lookup"><span data-stu-id="9b995-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a><span data-ttu-id="9b995-123">\( psTab \) verwijderen</span><span class="sxs-lookup"><span data-stu-id="9b995-123">Remove\( psTab \)</span></span>

<span data-ttu-id="9b995-124">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="9b995-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="9b995-125">Hiermee verwijdert u het Power shell-tabblad waarop de para meter **psTab** is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9b995-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="9b995-126">**psTab** : micro soft. Power shell. host. ISE. PowerShellTab het Power shell-tabblad dat u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="9b995-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="9b995-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9b995-127">See Also</span></span>

- [<span data-ttu-id="9b995-128">Het PowerShellTab-object</span><span class="sxs-lookup"><span data-stu-id="9b995-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="9b995-129">Doel van het Windows PowerShell ISE scripting object model</span><span class="sxs-lookup"><span data-stu-id="9b995-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="9b995-130">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="9b995-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
