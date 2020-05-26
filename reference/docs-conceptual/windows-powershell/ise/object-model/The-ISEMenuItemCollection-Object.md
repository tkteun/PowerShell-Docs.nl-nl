---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Het ISEMenuItemCollection-object
ms.openlocfilehash: 39e8547c9b19ba323d4b224a46eda416542b2807
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810937"
---
# <a name="the-isemenuitemcollection-object"></a>Het ISEMenuItemCollection-object

Een **ISEMenuItemCollection** -object is een verzameling **ISEMenuItem** -objecten. Het is een exemplaar van de klasse **micro soft. Power shell. host. ISE. ISEMenuItemCollection** . Een voor beeld is het `$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus` object dat wordt gebruikt voor het aanpassen van het **invoeg** menu in Windows Power Shell® integrated SCRIPTING Environment (ISE).

## <a name="method"></a>Methode

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>\(Teken reeks DisplayName, System. Management. Automation. script block-actie, System. Windows. input. toets-beweging toevoegen\)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee wordt een menu opdracht toegevoegd aan de verzameling.

**DisplayName** De weergave naam van het menu dat moet worden toegevoegd.

**Actie** Het object **System. Management. Automation. script Block** dat de actie specificeert die is gekoppeld aan deze menu opdracht.

**Snelkoppeling** De sneltoets voor de actie.

**Retourneert** Het **ISEMenuItem** -object dat zojuist is toegevoegd.

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Maak\(\)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee verwijdert u alle submenu's uit de menu opdracht.

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>Zie ook

- [Het ISEMenuItem-object](The-ISEMenuItem-Object.md)
- [Doel van het scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De ISE-object model hiërarchie](The-ISE-Object-Model-Hierarchy.md)
