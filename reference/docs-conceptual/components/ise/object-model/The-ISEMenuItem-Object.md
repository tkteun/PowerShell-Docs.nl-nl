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
# <a name="the-isemenuitem-object"></a>Het ISEMenuItem-object

Een **ISEMenuItem** object is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEMenuItem. Alle menu-objecten in de **invoegtoepassingen** menu zijn exemplaren van de **Microsoft.PowerShell.Host.ISE.ISEMenuItem** klasse.

## <a name="properties"></a>Eigenschappen

### <a name="displayname"></a>DisplayName

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die de weergavenaam van het menu-item opgehaald.

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a>Actie

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap waarmee het scriptblok worden opgehaald. Deze roept de actie wanneer u klikt op het menu-item.

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a>Snelkoppeling

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die opgehaald van de Windows invoer sneltoets voor de menuopdracht.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a>Submenu 's

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die krijgt de [lijst submenu](The-ISEMenuItemCollection-Object.md) van het menu-item.

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a>Voorbeeld van het uitvoeren van scripts

Lees voor meer informatie over het gebruik van het menu invoegtoepassingen en de bijbehorende scripts eigenschappen, het volgende voorbeeld voor het uitvoeren van scripts.

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

- [Het ISEMenuItemCollection-Object](The-ISEMenuItemCollection-Object.md)
- [Doel van de Scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)