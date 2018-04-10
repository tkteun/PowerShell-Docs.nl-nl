---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEMenuItem-object
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 556f88117c07100b1734c8ffd8956dce6efe6fb1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="5f74d-103">Het ISEMenuItem-object</span><span class="sxs-lookup"><span data-stu-id="5f74d-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="5f74d-104">Een **ISEMenuItem** object is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEMenuItem.</span><span class="sxs-lookup"><span data-stu-id="5f74d-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="5f74d-105">Alle menu-objecten in de **invoegtoepassingen** menu zijn exemplaren van de **Microsoft.PowerShell.Host.ISE.ISEMenuItem** klasse.</span><span class="sxs-lookup"><span data-stu-id="5f74d-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="5f74d-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="5f74d-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="5f74d-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="5f74d-107">DisplayName</span></span>

<span data-ttu-id="5f74d-108">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="5f74d-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="5f74d-109">De alleen-lezen eigenschap die de weergavenaam van de menuopdracht opgehaald.</span><span class="sxs-lookup"><span data-stu-id="5f74d-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="5f74d-110">Actie</span><span class="sxs-lookup"><span data-stu-id="5f74d-110">Action</span></span>

<span data-ttu-id="5f74d-111">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="5f74d-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="5f74d-112">De alleen-lezen eigenschap waarin het scriptblok worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="5f74d-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="5f74d-113">Deze roept de actie wanneer u klikt op de menuopdracht.</span><span class="sxs-lookup"><span data-stu-id="5f74d-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="5f74d-114">Snelkoppeling</span><span class="sxs-lookup"><span data-stu-id="5f74d-114">Shortcut</span></span>

<span data-ttu-id="5f74d-115">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="5f74d-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="5f74d-116">De alleen-lezen eigenschap die opgehaald van de Windows invoer sneltoets voor de menuopdracht.</span><span class="sxs-lookup"><span data-stu-id="5f74d-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="5f74d-117">Submenu 's</span><span class="sxs-lookup"><span data-stu-id="5f74d-117">Submenus</span></span>

<span data-ttu-id="5f74d-118">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="5f74d-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="5f74d-119">De alleen-lezen eigenschap die krijgt de [lijst van vervolgmenu's](The-ISEMenuItemCollection-Object.md) van de menuopdracht.</span><span class="sxs-lookup"><span data-stu-id="5f74d-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="5f74d-120">Voorbeeld van het uitvoeren van scripts</span><span class="sxs-lookup"><span data-stu-id="5f74d-120">Scripting example</span></span>

<span data-ttu-id="5f74d-121">Lees voor meer informatie over het gebruik van het menu invoegtoepassingen en de bijbehorende scriptbare eigenschappen, het volgende voorbeeld voor het uitvoeren van scripts.</span><span class="sxs-lookup"><span data-stu-id="5f74d-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a><span data-ttu-id="5f74d-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5f74d-122">See Also</span></span>

- [<span data-ttu-id="5f74d-123">Het Object ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="5f74d-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="5f74d-124">Doel van de Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="5f74d-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="5f74d-125">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="5f74d-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)