---
ms.date: 12/31/2019
keywords: Power shell, cmdlet
title: Het ISEAddOnToolCollection-object
ms.openlocfilehash: e07a47169381307b50ac190165307c926b4ad94e
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737012"
---
# <a name="the-iseaddontoolcollection-object"></a>Het ISEAddOnToolCollection-object

Het **ISEAddOnToolCollection** -object is een verzameling **ISEAddOnTool** -objecten. Een voor beeld is het `$psISE.CurrentPowerShellTab.VerticalAddOnTools`-object.

## <a name="methods"></a>Methoden

### <a name="add-name-controltype-isvisible-"></a>\( name, ControlType, \[IsVisible\] \) toevoegen

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee voegt u een nieuw hulp programma toe aan de verzameling. Hiermee wordt het zojuist toegevoegde hulp programma voor toevoegen geretourneerd. Voordat u deze opdracht uitvoert, moet u het hulp programma voor toevoegen installeren op de lokale computer en de assembly laden.

**Naam** -teken reeks Hiermee geeft u de weergave naam op van het hulp programma voor toevoegen dat wordt toegevoegd aan Windows PowerShell ISE.

**ControlType** -type Hiermee geeft u het besturings element op dat wordt toegevoegd.

**\[IsVisible\]** -optionele Booleaanse waarde als deze is ingesteld op `$true`, wordt het hulp programma voor toevoegen direct weer gegeven in het bijbehorende deel venster.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>\( item verwijderen \)

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee verwijdert u het opgegeven hulp programma voor invoeg toepassingen uit de verzameling.

**Item** -Microsoft. Power shell. host. ISE. ISEAddOnTool geeft het object op dat uit Windows PowerShell ISE moet worden verwijderd.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab \)

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee selecteert u het Power shell-tabblad waarop de para meter **psTab** is opgegeven.

**psTab** : micro soft. Power shell. host. ISE. PowerShellTab het Power shell-tabblad om te selecteren.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a>\( psTab \) verwijderen

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
- [Doel van het Windows PowerShell ISE scripting object model](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)
