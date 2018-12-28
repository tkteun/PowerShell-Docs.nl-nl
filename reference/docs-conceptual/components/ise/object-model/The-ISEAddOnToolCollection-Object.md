---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEAddOnToolCollection-object
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ff4f19d1a85a592f2f4f09c62caa0971751bdff7
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404469"
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="97aad-103">Het ISEAddOnToolCollection-object</span><span class="sxs-lookup"><span data-stu-id="97aad-103">The ISEAddOnToolCollection Object</span></span>

<span data-ttu-id="97aad-104">De **ISEAddOnToolCollection** object is een verzameling van **ISEAddOnTool** objecten.</span><span class="sxs-lookup"><span data-stu-id="97aad-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="97aad-105">Een voorbeeld is de **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span><span class="sxs-lookup"><span data-stu-id="97aad-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="97aad-106">Methoden</span><span class="sxs-lookup"><span data-stu-id="97aad-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="97aad-107">Voeg\( naam, het besturingselementtype, \[IsVisible\] \)</span><span class="sxs-lookup"><span data-stu-id="97aad-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>

<span data-ttu-id="97aad-108">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="97aad-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="97aad-109">Voegt een nieuw hulpprogramma voor de invoegtoepassing toe aan de verzameling.</span><span class="sxs-lookup"><span data-stu-id="97aad-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="97aad-110">Retourneert het zojuist toegevoegde invoegtoepassing-hulpprogramma.</span><span class="sxs-lookup"><span data-stu-id="97aad-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="97aad-111">Voordat u deze opdracht uitvoert, moet u het hulpprogramma invoegtoepassing installeren op de lokale computer en de assembly niet laden.</span><span class="sxs-lookup"><span data-stu-id="97aad-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

<span data-ttu-id="97aad-112">**Naam** -tekenreeks geeft de weergavenaam van het hulpprogramma invoegtoepassing die wordt toegevoegd aan Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="97aad-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

<span data-ttu-id="97aad-113">**Besturingselementtype** -Type wordt opgegeven in het besturingselement dat wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="97aad-113">**ControlType** -Type Specifies the control that is added.</span></span>

<span data-ttu-id="97aad-114">**\[IsVisible\]**  -optionele Booleaanse als ingesteld op **$true**, het hulpprogramma invoegtoepassing is meteen zichtbaar in het deelvenster van de bijbehorende hulpprogramma.</span><span class="sxs-lookup"><span data-stu-id="97aad-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="97aad-115">Verwijder\( Item \)</span><span class="sxs-lookup"><span data-stu-id="97aad-115">Remove\( Item \)</span></span>

<span data-ttu-id="97aad-116">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="97aad-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="97aad-117">Hiermee verwijdert u het hulpprogramma opgegeven invoegtoepassing uit de verzameling.</span><span class="sxs-lookup"><span data-stu-id="97aad-117">Removes the specified add-on tool from the collection.</span></span>

<span data-ttu-id="97aad-118">**Item** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool Hiermee geeft u het object worden verwijderd uit de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="97aad-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="97aad-119">SetSelectedPowerShellTab\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="97aad-119">SetSelectedPowerShellTab\( psTab \)</span></span>

<span data-ttu-id="97aad-120">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="97aad-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="97aad-121">Selecteert het PowerShell-tabblad die de **psTab** parameter specificeert.</span><span class="sxs-lookup"><span data-stu-id="97aad-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="97aad-122">**psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab de PowerShell-tabblad om te selecteren.</span><span class="sxs-lookup"><span data-stu-id="97aad-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a><span data-ttu-id="97aad-123">Verwijder\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="97aad-123">Remove\( psTab \)</span></span>

<span data-ttu-id="97aad-124">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="97aad-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="97aad-125">Hiermee verwijdert u de PowerShell-tabblad die de **psTab** parameter specificeert.</span><span class="sxs-lookup"><span data-stu-id="97aad-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="97aad-126">**psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab de PowerShell-tabblad om te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="97aad-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="97aad-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="97aad-127">See Also</span></span>

- [<span data-ttu-id="97aad-128">Het PowerShellTab-Object</span><span class="sxs-lookup"><span data-stu-id="97aad-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="97aad-129">Doel van de Scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="97aad-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="97aad-130">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="97aad-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)