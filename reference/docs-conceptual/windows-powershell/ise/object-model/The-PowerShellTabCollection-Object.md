---
ms.date: 06/05/2017
title: Het PowerShellTabCollection-object
description: Het PowerShellTab-verzamelings object is een verzameling PowerShellTab-objecten. Elk PowerShellTab-object fungeert als een afzonderlijke runtime-omgeving.
ms.openlocfilehash: 60f8001f096b50bd8433a5685f1f70a350f07f61
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658267"
---
# <a name="the-powershelltabcollection-object"></a>Het PowerShellTabCollection-object

Het **PowerShellTab** -verzamelings object is een verzameling **PowerShellTab** -objecten. Elk **PowerShellTab** -object fungeert als een afzonderlijke runtime-omgeving. Het is een exemplaar van de klasse micro soft. Power shell. host. ISE. PowerShellTabs. Een voor beeld is het `$psISE.PowerShellTabs` object.

## <a name="methods"></a>Methoden

### <a name="add"></a>Toe\(\)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee voegt u een nieuw Power shell-tabblad aan de verzameling toe. Het zojuist toegevoegde tabblad wordt geretourneerd.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Verwijder \( micro soft. Power shell. host. ISE. PowerShellTab psTab\)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee verwijdert u het tabblad dat is opgegeven door de para meter **psTab** .

**psTab** Het Power shell-tabblad dat moet worden verwijderd.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab \( micro soft. Power shell. host. ISE. PowerShellTab psTab\)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee selecteert u het Power shell-tabblad dat is opgegeven door de para meter **psTab** om het momenteel actieve Power shell-tabblad te maken.

**psTab** Het Power shell-tabblad om te selecteren.

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a>Zie ook

- [Het PowerShellTab-object](The-PowerShellTab-Object.md)
- [Doel van het scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De ISE-object model hi??rarchie](The-ISE-Object-Model-Hierarchy.md)
