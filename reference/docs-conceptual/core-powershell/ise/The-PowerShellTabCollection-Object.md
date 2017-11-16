---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Het Object PowerShellTabCollection
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: dcdc16ae126453b6ade64917ac4950cc05e5f8ad
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="the-powershelltabcollection-object"></a>Het Object PowerShellTabCollection
  De **PowerShellTab** verzamelingsobject is een verzameling **PowerShellTab** objecten. Elke **PowerShellTab** object fungeert als een afzonderlijke runtime-omgeving. Het is een instantie van klasse Microsoft.PowerShell.Host.ISE.PowerShellTabs. Een voorbeeld is de **$psISE.PowerShellTabs** object.

## <a name="methods"></a>Methoden

### <a name="add"></a>Toevoegen\(\)
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 Voegt een nieuwe PowerShell-tabblad toe aan de verzameling. Retourneert het zojuist toegevoegde tabblad.

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Verwijder\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 Hiermee verwijdert u het tabblad dat wordt opgegeven door de **psTab** parameter.

 **psTab** het PowerShell-tabblad te verwijderen.

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  In Windows PowerShell ISE 2.0 en hoger ondersteund. 

 Hiermee selecteert u het PowerShell-tabblad die is opgegeven door de **psTab** parameter zodat deze de momenteel actieve PowerShell-tabblad.

 **psTab** het PowerShell-tab om te selecteren.

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## <a name="see-also"></a>Zie ook
- [Het Object PowerShellTab](The-PowerShellTab-Object.md) 
- [De Windows PowerShell ISE-objectmodel Scripting](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Naslaginformatie voor Windows PowerShell ISE-objectmodel](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [De hiërarchie ISE](../ise/The-ISE-Object-Model-Hierarchy.md)

  
