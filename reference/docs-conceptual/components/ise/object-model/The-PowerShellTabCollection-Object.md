---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het PowerShellTabCollection-object
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688733"
---
# <a name="the-powershelltabcollection-object"></a>Het PowerShellTabCollection-object

De **PowerShellTab** verzamelingsobject is een verzameling van **PowerShellTab** objecten. Elke **PowerShellTab** object fungeert als een aparte runtime-omgeving. Het is een exemplaar van Microsoft.PowerShell.Host.ISE.PowerShellTabs klasse. Een voorbeeld is de **$psISE.PowerShellTabs** object.

## <a name="methods"></a>Methoden

### <a name="add"></a>Toevoegen\(\)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Voegt een nieuwe PowerShell-tabblad toe aan de verzameling. Retourneert het zojuist toegevoegde tabblad.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee verwijdert u het tabblad dat is opgegeven door de **psTab** parameter.

**psTab** de PowerShell-tabblad om te verwijderen.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee selecteert u het PowerShell-tabblad die is opgegeven door de **psTab** parameter gemakkelijk de momenteel actieve PowerShell-tabblad.

**psTab** de PowerShell-tabblad om te selecteren.

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

- [The PowerShellTab Object](The-PowerShellTab-Object.md)
- [Doel van de Scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)