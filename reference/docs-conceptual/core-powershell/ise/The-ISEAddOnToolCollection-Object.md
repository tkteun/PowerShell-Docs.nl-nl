---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Het Object ISEAddOnToolCollection
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ba8b4e0e3952226407f00dea8b32785633256089
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="23aa9-103">Het Object ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="23aa9-103">The ISEAddOnToolCollection Object</span></span>
  <span data-ttu-id="23aa9-104">De **ISEAddOnToolCollection** object is een verzameling **ISEAddOnTool** objecten.</span><span class="sxs-lookup"><span data-stu-id="23aa9-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="23aa9-105">Een voorbeeld is de **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span><span class="sxs-lookup"><span data-stu-id="23aa9-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="23aa9-106">Methoden</span><span class="sxs-lookup"><span data-stu-id="23aa9-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="23aa9-107">Voeg\( naam, besturingselementtype, \[IsVisible\]\)</span><span class="sxs-lookup"><span data-stu-id="23aa9-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>
  <span data-ttu-id="23aa9-108">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="23aa9-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="23aa9-109">Voegt een nieuw hulpprogramma van de invoegtoepassing toe aan de verzameling.</span><span class="sxs-lookup"><span data-stu-id="23aa9-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="23aa9-110">Retourneert het zojuist toegevoegde invoegtoepassing hulpprogramma.</span><span class="sxs-lookup"><span data-stu-id="23aa9-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="23aa9-111">Voordat u deze opdracht uitvoert, moet u het hulpprogramma invoegtoepassing installeren op de lokale computer en de assembly niet laden.</span><span class="sxs-lookup"><span data-stu-id="23aa9-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

 <span data-ttu-id="23aa9-112">**Naam** -tekenreeks geeft de weergavenaam van het hulpprogramma invoegtoepassing die wordt toegevoegd aan Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="23aa9-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

 <span data-ttu-id="23aa9-113">**Besturingselementtype** -Type geeft aan dat het besturingselement dat wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="23aa9-113">**ControlType** -Type Specifies the control that is added.</span></span>

 <span data-ttu-id="23aa9-114">**\[IsVisible\]**  -optionele Booleaanse als ingesteld op **$true**, het hulpprogramma invoegtoepassing direct zichtbaar in het bijbehorende werkvenster is.</span><span class="sxs-lookup"><span data-stu-id="23aa9-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="23aa9-115">Verwijder\( Item\)</span><span class="sxs-lookup"><span data-stu-id="23aa9-115">Remove\( Item \)</span></span>
  <span data-ttu-id="23aa9-116">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="23aa9-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="23aa9-117">Hiermee verwijdert u het hulpprogramma opgegeven invoegtoepassing uit de verzameling.</span><span class="sxs-lookup"><span data-stu-id="23aa9-117">Removes the specified add-on tool from the collection.</span></span>

 <span data-ttu-id="23aa9-118">**Item** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool specificeert het object worden verwijderd uit de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="23aa9-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="23aa9-119">SetSelectedPowerShellTab\( psTab\)</span><span class="sxs-lookup"><span data-stu-id="23aa9-119">SetSelectedPowerShellTab\( psTab \)</span></span>
  <span data-ttu-id="23aa9-120">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="23aa9-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="23aa9-121">Selecteert de PowerShell tabblad die de **psTab** parameter geeft u op.</span><span class="sxs-lookup"><span data-stu-id="23aa9-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

 <span data-ttu-id="23aa9-122">**psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab het PowerShell-tab om te selecteren.</span><span class="sxs-lookup"><span data-stu-id="23aa9-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
      $newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

### <a name="remove-pstab-"></a><span data-ttu-id="23aa9-123">Verwijder\( psTab\)</span><span class="sxs-lookup"><span data-stu-id="23aa9-123">Remove\( psTab \)</span></span>
  <span data-ttu-id="23aa9-124">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="23aa9-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="23aa9-125">Hiermee verwijdert u de PowerShell tabblad die de **psTab** parameter geeft u op.</span><span class="sxs-lookup"><span data-stu-id="23aa9-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

 <span data-ttu-id="23aa9-126">**psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab het PowerShell-tabblad te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="23aa9-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="23aa9-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="23aa9-127">See Also</span></span>
- [<span data-ttu-id="23aa9-128">Het Object PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="23aa9-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="23aa9-129">De Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="23aa9-129">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="23aa9-130">Naslaginformatie voor Windows PowerShell ISE-objectmodel</span><span class="sxs-lookup"><span data-stu-id="23aa9-130">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="23aa9-131">De hiërarchie ISE</span><span class="sxs-lookup"><span data-stu-id="23aa9-131">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
