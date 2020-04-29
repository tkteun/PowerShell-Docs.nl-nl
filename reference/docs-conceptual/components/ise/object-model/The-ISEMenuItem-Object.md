---
ms.date: 12/31/2019
keywords: Power shell, cmdlet
title: Het ISEMenuItem-object
ms.openlocfilehash: c3ffe6e8f0b28987543fe0a873c552292dc5158a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736978"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="ce2ad-103">Het ISEMenuItem-object</span><span class="sxs-lookup"><span data-stu-id="ce2ad-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="ce2ad-104">Een **ISEMenuItem** -object is een exemplaar van de klasse **micro soft. Power shell. host. ISE. ISEMenuItem** .</span><span class="sxs-lookup"><span data-stu-id="ce2ad-104">An **ISEMenuItem** object is an instance of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>
<span data-ttu-id="ce2ad-105">Alle menu-objecten in het menu **met invoeg toepassingen** zijn exemplaren van de klasse **micro soft. Power shell. host. ISE. ISEMenuItem** .</span><span class="sxs-lookup"><span data-stu-id="ce2ad-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="ce2ad-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="ce2ad-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="ce2ad-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ce2ad-107">DisplayName</span></span>

<span data-ttu-id="ce2ad-108">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="ce2ad-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ce2ad-109">De alleen-lezen eigenschap waarmee de weergave naam van de menu opdracht wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ce2ad-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="ce2ad-110">Bewerking</span><span class="sxs-lookup"><span data-stu-id="ce2ad-110">Action</span></span>

<span data-ttu-id="ce2ad-111">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="ce2ad-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ce2ad-112">De alleen-lezen eigenschap waarmee het script blok wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ce2ad-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="ce2ad-113">De actie wordt geactiveerd wanneer u op de menu opdracht klikt.</span><span class="sxs-lookup"><span data-stu-id="ce2ad-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="ce2ad-114">Shortcutdimensie</span><span class="sxs-lookup"><span data-stu-id="ce2ad-114">Shortcut</span></span>

<span data-ttu-id="ce2ad-115">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="ce2ad-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ce2ad-116">De alleen-lezen eigenschap waarmee de Windows-invoer toetsenbord snel wordt opgehaald voor de menu opdracht.</span><span class="sxs-lookup"><span data-stu-id="ce2ad-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="ce2ad-117">Submenu's</span><span class="sxs-lookup"><span data-stu-id="ce2ad-117">Submenus</span></span>

<span data-ttu-id="ce2ad-118">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="ce2ad-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ce2ad-119">De alleen-lezen eigenschap waarmee de [lijst met](The-ISEMenuItemCollection-Object.md) submenu's van de menu opdracht wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ce2ad-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="ce2ad-120">Script voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ce2ad-120">Scripting example</span></span>

<span data-ttu-id="ce2ad-121">Lees het volgende script voorbeeld voor meer informatie over het gebruik van het menu add-ins en de eigenschappen van het script.</span><span class="sxs-lookup"><span data-stu-id="ce2ad-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ce2ad-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ce2ad-122">See Also</span></span>

- [<span data-ttu-id="ce2ad-123">Het ISEMenuItemCollection-object</span><span class="sxs-lookup"><span data-stu-id="ce2ad-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="ce2ad-124">Doel van het scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="ce2ad-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="ce2ad-125">De ISE-object model hiërarchie</span><span class="sxs-lookup"><span data-stu-id="ce2ad-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
