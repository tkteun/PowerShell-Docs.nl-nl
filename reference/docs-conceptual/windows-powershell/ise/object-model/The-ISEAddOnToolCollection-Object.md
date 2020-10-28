---
ms.date: 12/31/2019
title: Het ISEAddOnToolCollection-object
description: Het ISEAddOnToolCollection-object is een verzameling **ISEAddOnTool** -objecten.
ms.openlocfilehash: ba08ffd82a7ff2fa469540a5ea542abee8d4dc82
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658303"
---
# <a name="the-iseaddontoolcollection-object"></a>Het ISEAddOnToolCollection-object

Het **ISEAddOnToolCollection** -object is een verzameling **ISEAddOnTool** -objecten. Een voor beeld is het `$psISE.CurrentPowerShellTab.VerticalAddOnTools` object.

## <a name="methods"></a>Methoden

### <a name="add-name-controltype-isvisible-"></a>\(Name, ControlType, \[ IsVisible \] toevoegen\)

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee voegt u een nieuw hulp programma toe aan de verzameling. Hiermee wordt het zojuist toegevoegde hulp programma voor toevoegen geretourneerd. Voordat u deze opdracht uitvoert, moet u het hulp programma voor toevoegen installeren op de lokale computer en de assembly laden.

**Naam** -teken reeks Hiermee geeft u de weergave naam op van het hulp programma voor toevoegen dat wordt toegevoegd aan Windows PowerShell ISE.

**ControlType** -type Hiermee geeft u het besturings element op dat wordt toegevoegd.

**\[ IsVisible \]** -optionele Booleaanse waarde als deze optie is ingesteld op `$true` , wordt het hulp programma voor toevoegen direct weer gegeven in het bijbehorende deel venster.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>\(Item verwijderen\)

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee verwijdert u het opgegeven hulp programma voor invoeg toepassingen uit de verzameling.

**Item** -Microsoft. Power shell. host. ISE. ISEAddOnTool geeft het object op dat uit Windows PowerShell ISE moet worden verwijderd.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab \( psTab \)

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee selecteert u het Power shell-tabblad waarop de para meter **psTab** is opgegeven.

**psTab** : micro soft. Power shell. host. ISE. PowerShellTab het Power shell-tabblad om te selecteren.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a>\(PsTab verwijderen\)

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee verwijdert u het Power shell-tabblad waarop de para meter **psTab** is opgegeven.

**psTab** : micro soft. Power shell. host. ISE. PowerShellTab het Power shell-tabblad dat u wilt verwijderen.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a>Zie ook

- [Het PowerShellTab-object](The-PowerShellTab-Object.md)
- [Doel van het scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De ISE-object model hiërarchie](The-ISE-Object-Model-Hierarchy.md)
