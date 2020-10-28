---
ms.date: 09/13/2016
ms.topic: reference
title: Parameters voor provider-cmdlets
description: Parameters voor provider-cmdlets
ms.openlocfilehash: 6fd340f22202d984b7111c34806e3461a356c670
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662783"
---
# <a name="provider-cmdlet-parameters"></a>Parameters voor provider-cmdlets

Provider-cmdlets worden geleverd met een set statische para meters die beschikbaar zijn voor alle providers die de cmdlet ondersteunen, evenals dynamische para meters die worden toegevoegd wanneer de gebruiker een bepaalde waarde voor bepaalde statische para meters van de provider-cmdlet opgeeft.

## <a name="provider-cmdlet-static-parameters"></a>Statische para meters van provider-cmdlet

Statische para meters worden gedefinieerd door Windows Power shell. Een groot aantal van deze para meters wordt geïmplementeerd door Windows Power shell om consistentie te bieden voor alle providers en om een eenvoudigere ontwikkel ervaring te bieden. Voor beelden van deze para meters zijn de `literalPath` `exclude` `include` para meters, en, van de `Get-Item` cmdlet. Een kleinere set van deze para meters kan worden overschreven om acties te bieden die specifiek zijn voor uw provider. Voor beelden van deze para meters zijn de `Path` `Value` para meter en van de `Set-Item` cmdlet. Hier volgt een lijst met de para meters die kunnen worden overschreven voor de provider-cmdlets.

`Clear-Content` cmdlet kunt u definiëren hoe de provider de waarden gebruikt die zijn door gegeven aan de `Path` para meter van de `Clear-Content` cmdlet door de methode [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) te implementeren.

`Clear-Item` cmdlet kunt u definiëren hoe de provider de waarden gebruikt die zijn door gegeven aan de `Path` para meter van de `Clear-Item` cmdlet door de methode [System. Management. Automation. provider. Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) te implementeren.

`Clear-ItemProperty` cmdlet kunt u definiëren hoe de provider de waarden gebruikt die zijn door gegeven aan de `Path` `Name` para meters van de `Clear-ItemProperty` cmdlet door de implementatie van de methode [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) .

`Copy-Item` -cmdlet kunt u definiëren hoe de provider de waarden gebruikt die zijn door gegeven aan de `Path` `Destination` `Recurse` para meters, en, `Copy-Item` door de implementatie van de methode [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) .

Get-ChildItems-cmdlet kunt u definiëren hoe de provider de waarden gebruikt die zijn door gegeven aan de `Path` `Recurse` para meters van de `Get-ChildItem` cmdlet door de implementatie van de methoden [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) en [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) .

`Get-Content` cmdlet kunt u definiëren hoe de provider de waarden gebruikt die zijn door gegeven aan de `Path` para meter van de `Get-Content` cmdlet door de methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) te implementeren.

`Get-Item` cmdlet kunt u definiëren hoe de provider de waarden gebruikt die zijn door gegeven aan de `Path` para meter van de `Get-Item` cmdlet door de methode [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) te implementeren.

`Get-ItemProperty` cmdlet kunt u definiëren hoe de provider de waarden gebruikt die zijn door gegeven aan de `Path` `Name` para meters van de `Get-ItemProperty` cmdlet door de implementatie van de methode [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) .

`Invoke-Item` cmdlet kunt u definiëren hoe de provider de waarden gebruikt die zijn door gegeven aan de `Path` para meter van de `Invoke-Item` cmdlet door de methode [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) te implementeren.

`Move-Item` cmdlet kunt u definiëren hoe de provider de waarden gebruikt die zijn door gegeven aan de `Path` `Destination` para meters van de `Move-Item` cmdlet door de implementatie van de methode [System. Management. Automation. provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) .

`New-Item` -cmdlet kunt u definiëren hoe de provider de waarden gebruikt die zijn door gegeven aan de `Path` `ItemType` `Value` para meters, en, `New-Item` door de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) .

`New-ItemProperty` cmdlet kunt u definiëren hoe de provider de waarden gebruikt die zijn door gegeven aan de `Path` `Name` `PropertyType` para meters,, en `Value` van de `New-ItemProperty` cmdlet door de implementatie van de methode [micro soft. Power shell. commands. Registryprovider. NewProperty *](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) .

`Remove-Item` U kunt definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de `Path` `Recurse` para meters van de `Remove-Item` cmdlet door de methode [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) te implementeren.

`Remove-ItemProperty` U kunt definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de `Path` `Name` para meters van de `Remove-ItemProperty` cmdlet door de implementatie van de methode [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Removeproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) .

`Rename-Item` cmdlet kunt u definiëren hoe de provider de waarden gebruikt die zijn door gegeven aan de `Path` `NewName` para meters van de `Rename-Item` cmdlet door de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) .

`Rename-ItemProperty` U kunt definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de `Path` `NewName` para meters, en, en hoe de `Name` `Rename-ItemProperty` cmdlet [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Renameproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) implementeert.

`Set-Content` cmdlet kunt u definiëren hoe de provider de waarden gebruikt die zijn door gegeven aan de `Path` para meter van de `Set-Content` cmdlet door de methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) te implementeren.

`Set-Item` cmdlet kunt u definiëren hoe de provider de waarden gebruikt die zijn door gegeven aan de `Path` `Value` para meters van de `Set-Item` cmdlet door de implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) .

`Set-ItemProperty` cmdlet kunt u definiëren hoe de provider de waarden gebruikt die zijn door gegeven aan de `Path` `Value` para meters van de `Set-Item` cmdlet door de implementatie van de methode [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) .

`Test-Path` cmdlet kunt u definiëren hoe de provider de waarden gebruikt die zijn door gegeven aan de `Path` para meter van de `Test-Path` cmdlet door de methode [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) te implementeren.

Daarnaast kunt u de kenmerken van deze para meters niet opgeven, bijvoorbeeld of ze optioneel of vereist zijn, en u moet deze para meters ook een alias geven of een van de validatie kenmerken opgeven. Daarentegen kunt u parameter kenmerken in zelfstandige cmdlets opgeven door gebruik te maken van kenmerken zoals het- `Parameters` kenmerk.

## <a name="provider-cmdlet-dynamic-parameters"></a>Dynamische para meters van provider-cmdlet

Dynamische para meters voor cmdlet-providers zijn vergelijkbaar met dynamische providers voor zelfstandige cmdlets. In beide gevallen worden de para meters toegevoegd aan de cmdlet wanneer de gebruiker een bepaalde waarde opgeeft voor een van de standaard parameters, zoals de `path` para meter. Niet alle statische para meters kunnen echter worden gebruikt voor het activeren van de toevoeging van dynamische para meters. Zie [dynamische para meters](./provider-cmdlet-dynamic-parameters.md)van de provider voor meer informatie over dynamische para meters.

## <a name="see-also"></a>Zie ook

[Dynamische para meters van provider-cmdlet](./provider-cmdlet-dynamic-parameters.md)

[Een Windows PowerShell-provider schrijven](./writing-a-windows-powershell-provider.md)
