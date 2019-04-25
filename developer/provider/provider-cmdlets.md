---
title: Provider-cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2465420-0970-4408-9ee5-260cf444cb67
caps.latest.revision: 8
ms.openlocfilehash: e6a0711cff6a550100f584fb64ae7f59f71a3cfb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080948"
---
# <a name="provider-cmdlets"></a>Provider-cmdlets

De cmdlets die de gebruiker kan worden uitgevoerd voor het beheren van een gegevensarchief worden aangeduid als provider-cmdlets. Ter ondersteuning van deze cmdlets, moet u enkele van de methoden die zijn gedefinieerd door de basis-providerklassen en interfaces overschrijven.

## <a name="provider-cmdlets"></a>Provider-Cmdlets

Hier volgen de provider-cmdlets die kunnen worden uitgevoerd door de gebruiker:

### <a name="psdrive-cmdlets"></a>PSDrive-cmdlets

- `Get-PSDrive`: Deze cmdlet retourneert dat de Windows PowerShell-stations in de huidige sessie. U hoeft niet te overschrijven alle methoden ter ondersteuning van deze cmdlet.

- `New-PSDrive`: Deze cmdlet kan de gebruiker om Windows PowerShell-stations voor toegang tot het gegevensarchief te maken. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) en [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) methoden.

- `Remove-PSDrive`: Deze cmdlet kan de gebruiker te verwijderen van Windows PowerShell-stations die toegang hebben tot het gegevensarchief. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methode.

### <a name="item-cmdlets"></a>Item-cmdlets

- `Clear-Item`: Deze cmdlet kan de gebruiker te verwijderen van de waarde van een item in het gegevensarchief. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) en [ System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) methoden.

- `Copy-Item`: Deze cmdlet kan de gebruiker een item te kopiëren van de ene locatie naar een andere. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Containercmdletprovider.Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) en [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) methoden.

- `Get-Item`: Deze cmdlet kan de gebruiker voor het ophalen van gegevens uit het gegevensarchief. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Itemcmdletprovider.Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) en [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) methoden.

- `Get-ChildItem`: Deze cmdlet kan de gebruiker om op te halen van de onderliggende items van het bovenliggende item. Ter ondersteuning van deze cmdlet, overschrijven de volgende methoden:

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`: Deze cmdlet kan de gebruiker om uit te voeren van de standaardactie die is opgegeven door het item. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) en [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) methoden.

- `Move-Item`: Deze cmdlet kan de gebruiker een item van de ene locatie verplaatsen naar een andere locatie. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) en [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)s methoden.

- `New-ItemProperty`: Deze cmdlet kan de gebruiker te maken van een nieuw item in het gegevensarchief.

- `Remove-Item`: Deze cmdlet kan de gebruiker om items te verwijderen uit het gegevensarchief. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Containercmdletprovider.Removeitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) en [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) methoden.

- `Rename-Item`: Deze cmdlet kan de gebruiker om te wijzigen van items in het gegevensarchief. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Containercmdletprovider.Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) en [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) methoden.

- `Set-Item`: Deze cmdlet kan de gebruiker om bij te werken van de waarden van items in het gegevensarchief. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Itemcmdletprovider.Setitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) en [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) methoden.

### <a name="item-content-cmdlets"></a>Inhoud item-cmdlets

- `Add-Content`: Deze cmdlet kan de gebruiker inhoud toevoegen aan een item.

- `Clear-Content`: Deze cmdlet kan de gebruiker naar de inhoud van een item verwijderen zonder te verwijderen van het item. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) en [ System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) methoden.

- `Get-Content`: Deze cmdlet kan de gebruiker om op te halen van de inhoud van een item. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) en [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) methoden. De [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) methode retourneert een [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) interface waarmee wordt gedefinieerd de methoden die worden gebruikt om de inhoud te lezen.

- `Set-Content`: Deze cmdlet kan de gebruiker de inhoud van een item bijwerken. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) en [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) methoden. De [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) methode retourneert een [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) interface waarmee wordt gedefinieerd de methoden die wordt gebruikt voor het schrijven van de inhoud.

### <a name="item-property-cmdlets"></a>Item-cmdlets voor eigenschap

- `Clear-ItemProperty`: Deze cmdlet kan de gebruiker om de waarde van een eigenschap te verwijderen. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) en [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) methoden.

- `Copy-ItemProperty`: Deze cmdlet kan de gebruiker naar een eigenschap en de waarde van de ene locatie naar de andere kopiëren. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) en [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) methoden.

- `Get-ItemProperty`: Deze cmdlet worden de eigenschappen van een item opgehaald. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) en [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) methoden.

- `Move-ItemProperty`: Deze cmdlet kan de gebruiker een eigenschap en de waarde van de ene locatie verplaatsen naar een andere. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) en [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) methoden.

- `New-ItemProperty`: Deze cmdlet kan de gebruiker te maken van een nieuwe eigenschap en stel de waarde. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) en [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) methoden.

- `Remove-ItemProperty`: Deze cmdlet kan de gebruiker te verwijderen van een eigenschap en de waarde ervan. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) en [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) methoden.

- `Rename-ItemProperty`: Deze cmdlet kan de gebruiker de naam van een eigenschap te wijzigen. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) en [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) methoden.

- `Set-ItemProperty`: Deze cmdlet kan de gebruiker om de eigenschappen van een item te werken. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) en [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) methoden.

### <a name="location-cmdlets"></a>Locatie-cmdlets

- `Get-Location`: Haalt informatie op over de huidige werklocatie. U hoeft niet te overschrijven alle methoden ter ondersteuning van deze cmdlet.

- `Pop-Location`: Deze cmdlet worden de huidige locatie gewijzigd naar de locatie van meest recent gepusht naar de stack. U hoeft niet te overschrijven alle methoden ter ondersteuning van deze cmdlet.

- `Push-Location`: Deze cmdlet wordt de huidige locatie toegevoegd aan het begin van een lijst met locaties (een ' stack'). U hoeft niet te overschrijven alle methoden ter ondersteuning van deze cmdlet.

- `Set-Location`: Deze cmdlet wordt de huidige locatie van de werkende ingesteld voor een opgegeven locatie. U hoeft niet te overschrijven alle methoden ter ondersteuning van deze cmdlet.

### <a name="path-cmdlets"></a>Pad-cmdlets

- `Join-Path`: Deze cmdlet kan de gebruiker een bovenliggende en onderliggende padsegment voor het maken van een provider interne pad combineren. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) methode.

- `Convert-Path`: Deze cmdlet converteert een pad van een Windows PowerShell-pad naar een pad naar een Windows PowerShell-provider.

- `Split-Path`: Retourneert het opgegeven onderdeel van een pad.

- `Resolve-Path`: Oplossing voor de jokertekens in een pad en de pad-inhoud wordt weergegeven.

- `Test-Path`: Deze cmdlet wordt bepaald of alle elementen van een pad bestaat. Ter ondersteuning van deze cmdlet, overschrijven de [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) en [ System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) methoden.

### <a name="psprovider-cmdlets"></a>PSProvider-cmdlets

- `Get-PSProvider`: Deze cmdlet retourneert informatie over de providers die beschikbaar zijn in de sessie. U hoeft niet te overschrijven alle methoden ter ondersteuning van deze cmdlet.