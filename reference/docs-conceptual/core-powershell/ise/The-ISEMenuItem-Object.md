---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Het Object ISEMenuItem
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 5561955040e56110a6af0619c286548f5812fb47
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="835fb-103">Het Object ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="835fb-103">The ISEMenuItem Object</span></span>
  <span data-ttu-id="835fb-104">Een **ISEMenuItem** object is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEMenuItem.</span><span class="sxs-lookup"><span data-stu-id="835fb-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="835fb-105">Alle menu-objecten in de **invoegtoepassingen** menu zijn exemplaren van de **Microsoft.PowerShell.Host.ISE.ISEMenuItem** klasse.</span><span class="sxs-lookup"><span data-stu-id="835fb-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="835fb-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="835fb-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="835fb-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="835fb-107">DisplayName</span></span>
  <span data-ttu-id="835fb-108">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="835fb-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="835fb-109">De alleen-lezen eigenschap die de weergavenaam van de menuopdracht opgehaald.</span><span class="sxs-lookup"><span data-stu-id="835fb-109">The read-only property that gets the display name of the menu item.</span></span>

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

### <a name="action"></a><span data-ttu-id="835fb-110">Actie</span><span class="sxs-lookup"><span data-stu-id="835fb-110">Action</span></span>
  <span data-ttu-id="835fb-111">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="835fb-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="835fb-112">De alleen-lezen eigenschap waarin het scriptblok worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="835fb-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="835fb-113">Deze roept de actie wanneer u klikt op de menuopdracht.</span><span class="sxs-lookup"><span data-stu-id="835fb-113">It invokes the action when you click the menu item.</span></span>

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="835fb-114">Snelkoppeling</span><span class="sxs-lookup"><span data-stu-id="835fb-114">Shortcut</span></span>
  <span data-ttu-id="835fb-115">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="835fb-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="835fb-116">De alleen-lezen eigenschap die opgehaald van de Windows invoer sneltoets voor de menuopdracht.</span><span class="sxs-lookup"><span data-stu-id="835fb-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="835fb-117">Submenu 's</span><span class="sxs-lookup"><span data-stu-id="835fb-117">Submenus</span></span>
  <span data-ttu-id="835fb-118">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="835fb-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="835fb-119">De alleen-lezen eigenschap die krijgt de [lijst van vervolgmenu's](The-ISEMenuItemCollection-Object.md) van de menuopdracht.</span><span class="sxs-lookup"><span data-stu-id="835fb-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="835fb-120">Voorbeeld van het uitvoeren van scripts</span><span class="sxs-lookup"><span data-stu-id="835fb-120">Scripting example</span></span>
 <span data-ttu-id="835fb-121">Lees voor meer informatie over het gebruik van het menu invoegtoepassingen en de bijbehorende scriptbare eigenschappen, het volgende voorbeeld voor het uitvoeren van scripts.</span><span class="sxs-lookup"><span data-stu-id="835fb-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```

# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu - a parent and a child submenu item. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")

```

## <a name="see-also"></a><span data-ttu-id="835fb-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="835fb-122">See Also</span></span>
- [<span data-ttu-id="835fb-123">Het Object ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="835fb-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md) 
- [<span data-ttu-id="835fb-124">De Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="835fb-124">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="835fb-125">Naslaginformatie voor Windows PowerShell ISE-objectmodel</span><span class="sxs-lookup"><span data-stu-id="835fb-125">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="835fb-126">De hiërarchie ISE</span><span class="sxs-lookup"><span data-stu-id="835fb-126">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
