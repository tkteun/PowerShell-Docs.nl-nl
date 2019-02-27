---
title: Provider-cmdlet-parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: d0fb81ee1ca1f80e216c021e1bd64771b8de4dc3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849691"
---
# <a name="provider-cmdlet-parameters"></a>Parameters voor provider-cmdlets

Provider-cmdlets worden geleverd met een set van statische parameters die beschikbaar zijn voor alle providers die ondersteuning bieden voor de cmdlet, ook als dynamische parameters die worden toegevoegd wanneer de gebruiker Hiermee geeft u een bepaalde waarde voor bepaalde statische parameters van de provider-cmdlet.

## <a name="provider-cmdlet-static-parameters"></a>Provider statische Cmdlet-Parameters

Statische parameters worden gedefinieerd door de Windows PowerShell. Een grote verzameling van deze parameters wordt geïmplementeerd door Windows PowerShell voor consistentie voor alle providers en om een eenvoudigere ontwikkelingservaring te bieden. Voorbeelden van deze parameters zijn de `literalPath`, `exclude`, en `include` parameters van de `Get-Item` cmdlet. Een kleiner aantal deze parameters kan worden overschreven voor acties die specifiek voor uw provider zijn. Voorbeelden van deze parameters zijn de `Path` en `Value` parameter van de `Set-Item` cmdlet. Hier volgt een lijst van de parameters die voor de cmdlets van de provider kan worden overschreven.

`Clear-Content` cmdlet u hoe de provider wordt gebruikt voor de waarden worden doorgegeven definiëren kunt aan de `Path` parameter van de `Clear-Content` cmdlet door het implementeren van de [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)methode.

`Clear-Item` cmdlet u hoe de provider wordt gebruikt voor de waarden worden doorgegeven definiëren kunt aan de `Path` parameter van de `Clear-Item` cmdlet door het implementeren van de [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) methode.

`Clear-ItemProperty` cmdlet u hoe de provider wordt gebruikt voor de waarden worden doorgegeven definiëren kunt aan de `Path` en `Name` parameters van de `Clear-ItemProperty` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) methode.

`Copy-Item` cmdlet u hoe de provider wordt gebruikt voor de waarden worden doorgegeven definiëren kunt aan de `Path`, `Destination`, en `Recurse` parameters van de `Copy-Item` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) methode.

Get-ChildItems cmdlet u hoe de provider wordt gebruikt voor de waarden worden doorgegeven definiëren kunt aan de `Path` en `Recures` parameters van de `Get-ChildItem` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) en [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) methoden.

`Get-Content` cmdlet u hoe de provider wordt gebruikt voor de waarden worden doorgegeven definiëren kunt aan de `Path` parameter van de `Get-Content` cmdlet door het implementeren van de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) methode.

`Get-Item` cmdlet u hoe de provider wordt gebruikt voor de waarden worden doorgegeven definiëren kunt aan de `Path` parameter van de `Get-Item` cmdlet door het implementeren van de [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) methode.

`Get-ItemProperty` cmdlet u hoe de provider wordt gebruikt voor de waarden worden doorgegeven definiëren kunt aan de `Path` en `Name` parameters van de `Get-ItemProperty` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) methode.

`Invoke-Item` cmdlet u hoe de provider wordt gebruikt voor de waarden worden doorgegeven definiëren kunt aan de `Path` parameter van de `Invoke-Item` cmdlet door het implementeren van de [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)methode.

`Move-Item` cmdlet u hoe de provider wordt gebruikt voor de waarden worden doorgegeven definiëren kunt aan de `Path` en `Destination` parameters van de `Move-Item` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) methode.

`New-Item` cmdlet u hoe de provider wordt gebruikt voor de waarden worden doorgegeven definiëren kunt aan de `Path`, `ItemType`, en `Value` parameters van de `New-Item` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) methode.

`New-ItemProperty` cmdlet u hoe de provider wordt gebruikt voor de waarden worden doorgegeven definiëren kunt aan de `Path`, `Name`, `PropertyType`, en `Value` parameters van de `New-ItemProperty` cmdlet door het implementeren van de [ Microsoft.Powershell.Commands.Registryprovider.Newproperty*](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) methode.

`Remove-Item` U kunt definiëren hoe de provider wordt gebruikt voor de waarden worden doorgegeven aan de `Path` en `Recurse` parameters van de `Remove-Item` cmdlet door het implementeren van de [System.Management.Automation.Provider.Containercmdletprovider.Removeitem* ](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) methode.

`Remove-ItemProperty` U kunt definiëren hoe de provider wordt gebruikt voor de waarden worden doorgegeven aan de `Path` en `Name` parameters van de `Remove-ItemProperty` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) methode.

`Rename-Item` cmdlet u hoe de provider wordt gebruikt voor de waarden worden doorgegeven definiëren kunt aan de `Path` en `NewName` parameters van de `Rename-Item` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) methode.

`Rename-ItemProperty` U kunt definiëren hoe de provider wordt gebruikt voor de waarden worden doorgegeven aan de `Path`, `NewName`, en `Name` parameters van de `Rename-ItemProperty` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) methode.

`Set-Content` cmdlet u hoe de provider wordt gebruikt voor de waarden worden doorgegeven definiëren kunt aan de `Path` parameter van de `Set-Content` cmdlet door het implementeren van de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) methode.

`Set-Item` cmdlet u hoe de provider wordt gebruikt voor de waarden worden doorgegeven definiëren kunt aan de `Path` en `Value` parameters van de `Set-Item` cmdlet door het implementeren van de [System.Management.Automation.Provider.Itemcmdletprovider.Setitem* ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methode.

`Set-ItemProperty` cmdlet u hoe de provider wordt gebruikt voor de waarden worden doorgegeven definiëren kunt aan de `Path` en `Value` parameters van de `Set-Item` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) methode.

`Test-Path` cmdlet u hoe de provider wordt gebruikt voor de waarden worden doorgegeven definiëren kunt aan de `Path` parameter van de `Test-Path` cmdlet door het implementeren van de [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)methode.

Bovendien kunt u de kenmerken van deze parameters, zoals of ze optioneel of vereist zijn, niet opgeven en kunt u deze parameters geven een alias of een van de validatie kenmerken opgeven. Daarentegen, kunt u kenmerken van de parameter in zelfstandige cmdlets met behulp van kenmerken, zoals de `Parameters` kenmerk.

## <a name="provider-cmdlet-dynamic-parameters"></a>Provider Cmdlet dynamische Parameters

Dynamische parameters voor cmdlet-providers zijn vergelijkbaar met de dynamische-providers voor zelfstandige-cmdlets. In beide gevallen wordt de parameters zijn toegevoegd aan de cmdlet wanneer de gebruiker een bepaalde waarde voor een van de standaardparameters, zoals de `path` parameter. Niet alle van de statische parameters kan echter worden gebruikt voor het activeren van het toevoegen van dynamische parameters. Zie voor meer informatie over dynamische parameters [Provider Cmdlet dynamische Parameters](./provider-cmdlet-dynamic-parameters.md).

## <a name="see-also"></a>Zie ook

[Provider Cmdlet dynamische Parameters](./provider-cmdlet-dynamic-parameters.md)

[Schrijven van een Windows PowerShell-Provider](./writing-a-windows-powershell-provider.md)