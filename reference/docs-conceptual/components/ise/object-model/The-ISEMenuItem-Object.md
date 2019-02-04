---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEMenuItem-object
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 556f88117c07100b1734c8ffd8956dce6efe6fb1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688768"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="83fba-103">Het ISEMenuItem-object</span><span class="sxs-lookup"><span data-stu-id="83fba-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="83fba-104">Een **ISEMenuItem** object is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEMenuItem.</span><span class="sxs-lookup"><span data-stu-id="83fba-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="83fba-105">Alle menu-objecten in de **invoegtoepassingen** menu zijn exemplaren van de **Microsoft.PowerShell.Host.ISE.ISEMenuItem** klasse.</span><span class="sxs-lookup"><span data-stu-id="83fba-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="83fba-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="83fba-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="83fba-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="83fba-107">DisplayName</span></span>

<span data-ttu-id="83fba-108">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="83fba-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="83fba-109">De alleen-lezen eigenschap die de weergavenaam van het menu-item opgehaald.</span><span class="sxs-lookup"><span data-stu-id="83fba-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="83fba-110">Actie</span><span class="sxs-lookup"><span data-stu-id="83fba-110">Action</span></span>

<span data-ttu-id="83fba-111">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="83fba-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="83fba-112">De alleen-lezen eigenschap waarmee het scriptblok worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="83fba-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="83fba-113">Deze roept de actie wanneer u klikt op het menu-item.</span><span class="sxs-lookup"><span data-stu-id="83fba-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="83fba-114">Snelkoppeling</span><span class="sxs-lookup"><span data-stu-id="83fba-114">Shortcut</span></span>

<span data-ttu-id="83fba-115">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="83fba-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="83fba-116">De alleen-lezen eigenschap die opgehaald van de Windows invoer sneltoets voor de menuopdracht.</span><span class="sxs-lookup"><span data-stu-id="83fba-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="83fba-117">Submenu 's</span><span class="sxs-lookup"><span data-stu-id="83fba-117">Submenus</span></span>

<span data-ttu-id="83fba-118">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="83fba-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="83fba-119">De alleen-lezen eigenschap die krijgt de [lijst submenu](The-ISEMenuItemCollection-Object.md) van het menu-item.</span><span class="sxs-lookup"><span data-stu-id="83fba-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="83fba-120">Voorbeeld van het uitvoeren van scripts</span><span class="sxs-lookup"><span data-stu-id="83fba-120">Scripting example</span></span>

<span data-ttu-id="83fba-121">Lees voor meer informatie over het gebruik van het menu invoegtoepassingen en de bijbehorende scripts eigenschappen, het volgende voorbeeld voor het uitvoeren van scripts.</span><span class="sxs-lookup"><span data-stu-id="83fba-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="83fba-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="83fba-122">See Also</span></span>

- [<span data-ttu-id="83fba-123">Het ISEMenuItemCollection-Object</span><span class="sxs-lookup"><span data-stu-id="83fba-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="83fba-124">Doel van de Scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="83fba-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="83fba-125">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="83fba-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)