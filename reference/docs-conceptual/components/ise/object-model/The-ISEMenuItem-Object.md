---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Het ISEMenuItem-object
ms.openlocfilehash: a513a3e9f2eb97f3955fa817faedbcbf4e0ed018
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67028937"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="c4b57-103">Het ISEMenuItem-object</span><span class="sxs-lookup"><span data-stu-id="c4b57-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="c4b57-104">Een **ISEMenuItem** -object is een exemplaar van de klasse micro soft. Power shell. host. ISE. ISEMenuItem.</span><span class="sxs-lookup"><span data-stu-id="c4b57-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="c4b57-105">Alle menu-objecten in het menu **met invoeg toepassingen** zijn exemplaren van de klasse **micro soft. Power shell. host. ISE. ISEMenuItem** .</span><span class="sxs-lookup"><span data-stu-id="c4b57-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="c4b57-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="c4b57-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="c4b57-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c4b57-107">DisplayName</span></span>

<span data-ttu-id="c4b57-108">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c4b57-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c4b57-109">De alleen-lezen eigenschap waarmee de weergave naam van de menu opdracht wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c4b57-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="c4b57-110">Actie</span><span class="sxs-lookup"><span data-stu-id="c4b57-110">Action</span></span>

<span data-ttu-id="c4b57-111">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c4b57-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c4b57-112">De alleen-lezen eigenschap waarmee het script blok wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c4b57-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="c4b57-113">De actie wordt geactiveerd wanneer u op de menu opdracht klikt.</span><span class="sxs-lookup"><span data-stu-id="c4b57-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="c4b57-114">Shortcutdimensie</span><span class="sxs-lookup"><span data-stu-id="c4b57-114">Shortcut</span></span>

<span data-ttu-id="c4b57-115">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c4b57-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c4b57-116">De alleen-lezen eigenschap waarmee de Windows-invoer toetsenbord snel wordt opgehaald voor de menu opdracht.</span><span class="sxs-lookup"><span data-stu-id="c4b57-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="c4b57-117">Submenu's</span><span class="sxs-lookup"><span data-stu-id="c4b57-117">Submenus</span></span>

<span data-ttu-id="c4b57-118">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c4b57-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c4b57-119">De alleen-lezen eigenschap waarmee de [lijst met](The-ISEMenuItemCollection-Object.md) submenu's van de menu opdracht wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c4b57-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="c4b57-120">Script voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c4b57-120">Scripting example</span></span>

<span data-ttu-id="c4b57-121">Lees het volgende script voorbeeld voor meer informatie over het gebruik van het menu add-ins en de eigenschappen van het script.</span><span class="sxs-lookup"><span data-stu-id="c4b57-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c4b57-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c4b57-122">See Also</span></span>

- [<span data-ttu-id="c4b57-123">Het ISEMenuItemCollection-object</span><span class="sxs-lookup"><span data-stu-id="c4b57-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="c4b57-124">Doel van het Windows PowerShell ISE scripting object model</span><span class="sxs-lookup"><span data-stu-id="c4b57-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="c4b57-125">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="c4b57-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
