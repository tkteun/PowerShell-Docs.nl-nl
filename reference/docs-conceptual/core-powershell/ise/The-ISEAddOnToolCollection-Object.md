---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEAddOnToolCollection-object
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ff4f19d1a85a592f2f4f09c62caa0971751bdff7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="the-iseaddontoolcollection-object"></a>Het ISEAddOnToolCollection-object

De **ISEAddOnToolCollection** object is een verzameling **ISEAddOnTool** objecten. Een voorbeeld is de **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.

## <a name="methods"></a>Methoden

### <a name="add-name-controltype-isvisible-"></a>Voeg\( naam, besturingselementtype, \[IsVisible\] \)

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Voegt een nieuw hulpprogramma van de invoegtoepassing toe aan de verzameling. Retourneert het zojuist toegevoegde invoegtoepassing hulpprogramma. Voordat u deze opdracht uitvoert, moet u het hulpprogramma invoegtoepassing installeren op de lokale computer en de assembly niet laden.

**Naam** -tekenreeks geeft de weergavenaam van het hulpprogramma invoegtoepassing die wordt toegevoegd aan Windows PowerShell ISE.

**Besturingselementtype** -Type geeft aan dat het besturingselement dat wordt toegevoegd.

**\[IsVisible\]**  -optionele Booleaanse als ingesteld op **$true**, het hulpprogramma invoegtoepassing direct zichtbaar in het bijbehorende werkvenster is.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>Verwijder\( Item \)

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee verwijdert u het hulpprogramma opgegeven invoegtoepassing uit de verzameling.

**Item** -Microsoft.PowerShell.Host.ISE.ISEAddOnTool specificeert het object worden verwijderd uit de Windows PowerShell ISE.

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab \)

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Selecteert de PowerShell tabblad die de **psTab** parameter geeft u op.

**psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab het PowerShell-tab om te selecteren.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a>Verwijder\( psTab \)

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee verwijdert u de PowerShell tabblad die de **psTab** parameter geeft u op.

**psTab** -Microsoft.PowerShell.Host.ISE.PowerShellTab het PowerShell-tabblad te verwijderen.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a>Zie ook

- [Het Object PowerShellTab](The-PowerShellTab-Object.md)
- [Doel van de Windows PowerShell ISE-objectmodel Scripting](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)