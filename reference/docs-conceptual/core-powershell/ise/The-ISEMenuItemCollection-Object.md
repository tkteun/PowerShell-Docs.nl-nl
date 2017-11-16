---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Het Object ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7ce9132021d4d5e755503e0adb355beb388a625a
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="the-isemenuitemcollection-object"></a>Het Object ISEMenuItemCollection
  Een **ISEMenuItemCollection** object is een verzameling **ISEMenuItem** objecten. Er is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Een voorbeeld is de **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object dat wordt gebruikt voor het aanpassen van de **invoegtoepassing** menu in Windows PowerShell® Integrated Scripting Environment (ISE).

## <a name="method"></a>Methode

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Voeg\(DisplayName, System.Management.Automation.ScriptBlock actie System.Windows.Input.KeyGesture snelkoppeling string\)
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 Een menu-item wordt toegevoegd aan de verzameling.

 **DisplayName** de weergavenaam van het menu moet worden toegevoegd.

 **Actie** de **System.Management.Automation.ScriptBlock** -object dat Hiermee geeft u de actie die is gekoppeld aan dit menu-item.

 **Snelkoppeling** de sneltoets voor de actie.

 **Retourneert** de ISEMenuItem-object dat zojuist is toegevoegd.

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a>Wissen\(\)
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 Verwijdert alle submenu's van de menuopdracht.

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a>Zie ook
- [Het Object ISEMenuItem](The-ISEMenuItem-Object.md) 
- [De Windows PowerShell ISE-objectmodel Scripting](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Naslaginformatie voor Windows PowerShell ISE-objectmodel](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [De hiërarchie ISE](The-ISE-Object-Model-Hierarchy.md)

  
