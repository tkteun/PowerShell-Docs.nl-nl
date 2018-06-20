---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEMenuItemCollection-object
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7e5030416df394aaa9e9d3f63978e204a7faabf1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954701"
---
# <a name="the-isemenuitemcollection-object"></a>Het ISEMenuItemCollection-object

Een **ISEMenuItemCollection** object is een verzameling **ISEMenuItem** objecten. Er is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection. Een voorbeeld is de **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object dat wordt gebruikt voor het aanpassen van de **invoegtoepassing** menu in Windows PowerShell® Integrated Scripting Environment (ISE).

## <a name="method"></a>Methode

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Voeg\(DisplayName, System.Management.Automation.ScriptBlock actie System.Windows.Input.KeyGesture snelkoppeling string \)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Een menu-item wordt toegevoegd aan de verzameling.

**DisplayName** de weergavenaam van het menu moet worden toegevoegd.

**Actie** de **System.Management.Automation.ScriptBlock** -object dat Hiermee geeft u de actie die is gekoppeld aan dit menu-item.

**Snelkoppeling** de sneltoets voor de actie.

**Retourneert** de ISEMenuItem-object dat zojuist is toegevoegd.

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Wissen\(\)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Verwijdert alle submenu's van de menuopdracht.

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>Zie ook

- [Het Object ISEMenuItem](The-ISEMenuItem-Object.md)
- [Doel van de Windows PowerShell ISE-objectmodel Scripting](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)