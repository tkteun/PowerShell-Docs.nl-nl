---
ms.date: 12/31/2019
keywords: Power shell, cmdlet
title: Het ISEMenuItem-object
ms.openlocfilehash: c3ffe6e8f0b28987543fe0a873c552292dc5158a
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736978"
---
# <a name="the-isemenuitem-object"></a>Het ISEMenuItem-object

Een **ISEMenuItem** -object is een exemplaar van de klasse **micro soft. Power shell. host. ISE. ISEMenuItem** .
Alle menu-objecten in het menu **met invoeg toepassingen** zijn exemplaren van de klasse **micro soft. Power shell. host. ISE. ISEMenuItem** .

## <a name="properties"></a>Eigenschappen

### <a name="displayname"></a>DisplayName

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap waarmee de weergave naam van de menu opdracht wordt opgehaald.

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a>Actie

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap waarmee het script blok wordt opgehaald. De actie wordt geactiveerd wanneer u op de menu opdracht klikt.

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a>Shortcutdimensie

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap waarmee de Windows-invoer toetsenbord snel wordt opgehaald voor de menu opdracht.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a>Submenu's

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap waarmee de [lijst met](The-ISEMenuItemCollection-Object.md) submenu's van de menu opdracht wordt opgehaald.

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a>Script voorbeeld

Lees het volgende script voorbeeld voor meer informatie over het gebruik van het menu add-ins en de eigenschappen van het script.

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

## <a name="see-also"></a>Zie ook

- [Het ISEMenuItemCollection-object](The-ISEMenuItemCollection-Object.md)
- [Doel van het Windows PowerShell ISE scripting object model](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)
