---
title: Cmdlet-para meters voor provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: ad7f9737c646dd5cea5abb14b828236e40feac5a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356838"
---
# <a name="provider-cmdlet-parameters"></a>Parameters voor provider-cmdlets

Provider-cmdlets worden geleverd met een set statische para meters die beschikbaar zijn voor alle providers die de cmdlet ondersteunen, evenals dynamische para meters die worden toegevoegd wanneer de gebruiker een bepaalde waarde voor bepaalde statische para meters van de provider-cmdlet opgeeft.

## <a name="provider-cmdlet-static-parameters"></a>Statische para meters van provider-cmdlet

Statische para meters worden gedefinieerd door Windows Power shell. Een groot aantal van deze para meters wordt geïmplementeerd door Windows Power shell om consistentie te bieden voor alle providers en om een eenvoudigere ontwikkel ervaring te bieden. Voor beelden van deze para meters zijn de `literalPath`, `exclude`en `include` para meters van de cmdlet `Get-Item`. Een kleinere set van deze para meters kan worden overschreven om acties te bieden die specifiek zijn voor uw provider. Voor beelden van deze para meters zijn de para meter `Path` en `Value` van de cmdlet `Set-Item`. Hier volgt een lijst met de para meters die kunnen worden overschreven voor de provider-cmdlets.

`Clear-Content`-cmdlet kunt u definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de para meter `Path` van de cmdlet `Clear-Content` door de implementatie van de methode [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) .

`Clear-Item`-cmdlet kunt u definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de para meter `Path` van de cmdlet `Clear-Item` door de implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) .

`Clear-ItemProperty`-cmdlet kunt u definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de `Path` en `Name` para meters van de `Clear-ItemProperty`-cmdlet door de methode [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) te implementeren.

`Copy-Item`-cmdlet kunt u definiëren hoe de-provider de waarden gebruikt die zijn door gegeven aan de para meters `Path`, `Destination`en `Recurse` van de `Copy-Item` cmdlet door de implementatie van de methode [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) .

De cmdlet Get-ChildItems kunt u definiëren hoe de gegevens worden gebruikt door de provider die wordt door gegeven aan de `Path` en `Recurse` para meters van de cmdlet `Get-ChildItem` door de implementatie van de methoden [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) en [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) .

`Get-Content`-cmdlet kunt u definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de para meter `Path` van de cmdlet `Get-Content` door de implementatie van de methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) .

`Get-Item`-cmdlet kunt u definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de para meter `Path` van de cmdlet `Get-Item` door de implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) .

`Get-ItemProperty`-cmdlet kunt u definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de `Path` en `Name` para meters van de `Get-ItemProperty`-cmdlet door de methode [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) te implementeren.

`Invoke-Item`-cmdlet kunt u definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de para meter `Path` van de cmdlet `Invoke-Item` door de implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

`Move-Item`-cmdlet kunt u definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de `Path` en `Destination` para meters van de `Move-Item`-cmdlet door de methode [System. Management. Automation. provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) te implementeren.

`New-Item`-cmdlet kunt u definiëren hoe de-provider de waarden gebruikt die zijn door gegeven aan de para meters `Path`, `ItemType`en `Value` van de `New-Item` cmdlet door de methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) te implementeren.

`New-ItemProperty`-cmdlet kunt u definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de para meters `Path`, `Name`, `PropertyType`en `Value` van de `New-ItemProperty` cmdlet door de implementatie van de methode [micro soft. Power shell. commands. Registryprovider. NewProperty *](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) .

`Remove-Item` kunt u definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de `Path` en `Recurse` para meters van de `Remove-Item`-cmdlet door de methode [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) te implementeren.

`Remove-ItemProperty` kunt u definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de `Path` en `Name` para meters van de `Remove-ItemProperty` cmdlet door de methode [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Removeproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) te implementeren.

`Rename-Item`-cmdlet kunt u definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de `Path` en `NewName` para meters van de `Rename-Item`-cmdlet door de methode [System. Management. Automation. provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) te implementeren.

`Rename-ItemProperty` kunt u definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de para meters `Path`, `NewName`en `Name` van de `Rename-ItemProperty` cmdlet door de methode [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Renameproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) te implementeren.

`Set-Content`-cmdlet kunt u definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de para meter `Path` van de cmdlet `Set-Content` door de implementatie van de methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) .

`Set-Item`-cmdlet kunt u definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de `Path` en `Value` para meters van de `Set-Item`-cmdlet door de methode [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) te implementeren.

`Set-ItemProperty`-cmdlet kunt u definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de `Path` en `Value` para meters van de `Set-Item`-cmdlet door de methode [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) te implementeren.

`Test-Path`-cmdlet kunt u definiëren hoe uw provider de waarden gebruikt die zijn door gegeven aan de para meter `Path` van de cmdlet `Test-Path` door de implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

Daarnaast kunt u de kenmerken van deze para meters niet opgeven, bijvoorbeeld of ze optioneel of vereist zijn, en u moet deze para meters ook een alias geven of een van de validatie kenmerken opgeven. U kunt daarentegen parameter kenmerken in zelfstandige cmdlets opgeven door gebruik te maken van kenmerken zoals het kenmerk `Parameters`.

## <a name="provider-cmdlet-dynamic-parameters"></a>Dynamische para meters van provider-cmdlet

Dynamische para meters voor cmdlet-providers zijn vergelijkbaar met dynamische providers voor zelfstandige cmdlets. In beide gevallen worden de para meters toegevoegd aan de cmdlet wanneer de gebruiker een bepaalde waarde opgeeft voor een van de standaard parameters, zoals de para meter `path`. Niet alle statische para meters kunnen echter worden gebruikt voor het activeren van de toevoeging van dynamische para meters. Zie [dynamische para meters](./provider-cmdlet-dynamic-parameters.md)van de provider voor meer informatie over dynamische para meters.

## <a name="see-also"></a>Zie ook

[Dynamische para meters van provider-cmdlet](./provider-cmdlet-dynamic-parameters.md)

[Een Windows Power shell-provider schrijven](./writing-a-windows-powershell-provider.md)