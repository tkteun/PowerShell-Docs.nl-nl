---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Het ISEMenuItemCollection-object
ms.openlocfilehash: b3795af1a6ed61ed6e371e5fc20cc4e95f643fd4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030537"
---
# <a name="the-isemenuitemcollection-object"></a>Het ISEMenuItemCollection-object

Een **ISEMenuItemCollection** -object is een verzameling **ISEMenuItem** -objecten. Het is een exemplaar van de klasse micro soft. Power shell. host. ISE. ISEMenuItemCollection. Een voor beeld is het object **$psISE. CurrentPowerShellTab. AddOnsMenu. submenu's** dat wordt gebruikt voor het aanpassen van het **invoeg** menu in Windows Power shell® Integrated Scripting Environment (ISE).

## <a name="method"></a>Methode

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>\(teken reeks weergave naam, System. Management. Automation. script block-actie, System. Windows. input. toets-beweging toevoegen \)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee wordt een menu opdracht toegevoegd aan de verzameling.

**DisplayName** De weergave naam van het menu dat moet worden toegevoegd.

**Actie** Het object **System. Management. Automation. script Block** dat de actie specificeert die is gekoppeld aan deze menu opdracht.

**Snelkoppeling** De sneltoets voor de actie.

**Retourneert** Het ISEMenuItem-object dat zojuist is toegevoegd.

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>\(\) wissen

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee verwijdert u alle submenu's uit de menu opdracht.

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>Zie ook

- [Het ISEMenuItem-object](The-ISEMenuItem-Object.md)
- [Doel van het Windows PowerShell ISE scripting object model](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)
