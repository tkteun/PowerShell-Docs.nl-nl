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
# <a name="the-isemenuitem-object"></a>Het Object ISEMenuItem
  Een **ISEMenuItem** object is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEMenuItem. Alle menu-objecten in de **invoegtoepassingen** menu zijn exemplaren van de **Microsoft.PowerShell.Host.ISE.ISEMenuItem** klasse.

## <a name="properties"></a>Eigenschappen

### <a name="displayname"></a>DisplayName
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 De alleen-lezen eigenschap die de weergavenaam van de menuopdracht opgehaald.

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

### <a name="action"></a>Actie
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 De alleen-lezen eigenschap waarin het scriptblok worden opgehaald. Deze roept de actie wanneer u klikt op de menuopdracht.

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a>Snelkoppeling
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 De alleen-lezen eigenschap die opgehaald van de Windows invoer sneltoets voor de menuopdracht.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a>Submenu 's
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 De alleen-lezen eigenschap die krijgt de [lijst van vervolgmenu's](The-ISEMenuItemCollection-Object.md) van de menuopdracht.

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a>Voorbeeld van het uitvoeren van scripts
 Lees voor meer informatie over het gebruik van het menu invoegtoepassingen en de bijbehorende scriptbare eigenschappen, het volgende voorbeeld voor het uitvoeren van scripts.

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

## <a name="see-also"></a>Zie ook
- [Het Object ISEMenuItemCollection](The-ISEMenuItemCollection-Object.md) 
- [De Windows PowerShell ISE-objectmodel Scripting](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Naslaginformatie voor Windows PowerShell ISE-objectmodel](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [De hiërarchie ISE](The-ISE-Object-Model-Hierarchy.md)
