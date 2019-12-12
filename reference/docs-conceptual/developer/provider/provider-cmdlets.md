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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352400"
---
# <a name="provider-cmdlets"></a>Provider-cmdlets

De cmdlets die de gebruiker kan uitvoeren voor het beheren van een gegevens archief, worden provider-cmdlets genoemd. Als u deze cmdlets wilt ondersteunen, moet u enkele van de methoden die zijn gedefinieerd door de basis provider klassen en-interfaces overschrijven.

## <a name="provider-cmdlets"></a>Provider-cmdlets

Dit zijn de provider-cmdlets die kunnen worden uitgevoerd door de gebruiker:

### <a name="psdrive-cmdlets"></a>PSDrive-cmdlets

- `Get-PSDrive`: deze cmdlet retourneert de Windows Power Shell-stations in de huidige sessie. U hoeft geen enkele methode te overschrijven om deze cmdlet te ondersteunen.

- `New-PSDrive`: met deze cmdlet kan de gebruiker Windows Power Shell-stations maken om toegang te krijgen tot het gegevens archief. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Drivecmdletprovider. newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) en [System. Management. Automation. provider. Drivecmdletprovider. Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) overschrijven.

- `Remove-PSDrive`: met deze cmdlet kan de gebruiker Windows Power Shell-stations verwijderen die toegang hebben tot het gegevens archief. Als u deze cmdlet wilt ondersteunen, overschrijft u de methode [System. Management. Automation. provider. Drivecmdletprovider. Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) .

### <a name="item-cmdlets"></a>Cmdlets voor items

- `Clear-Item`: met deze cmdlet kan de gebruiker de waarde van een item in het gegevens archief verwijderen. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Itemcmdletprovider. Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) en [System. Management. Automation. provider. Itemcmdletprovider. Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) overschrijven.

- `Copy-Item`: met deze cmdlet kan de gebruiker een item kopiëren van de ene locatie naar een andere. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Containercmdletprovider. Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) en [System. Management. Automation. provider. Containercmdletprovider. Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) overschrijven.

- `Get-Item`: met deze cmdlet kan de gebruiker gegevens ophalen uit het gegevens archief. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Itemcmdletprovider. GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) en [System. Management. Automation. provider. Itemcmdletprovider. Getitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) overschrijven.

- `Get-ChildItem`: met deze cmdlet kan de gebruiker de onderliggende items van het bovenliggende item ophalen. Als u deze cmdlet wilt ondersteunen, moet u de volgende methoden overschrijven:

  - [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System. Management. Automation. provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System. Management. Automation. provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`: met deze cmdlet kan de gebruiker de standaard actie uitvoeren die door het item is opgegeven. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) en [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) overschrijven.

- `Move-Item`: met deze cmdlet kan de gebruiker een item verplaatsen van de ene locatie naar een andere locatie. Als u deze cmdlet wilt ondersteunen, overschrijft u de methoden [System. Management. Automation. provider. Navigationcmdletprovider. Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) en [System. Management. Automation. provider. Navigationcmdletprovider. Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)s.

- `New-ItemProperty`: met deze cmdlet kan de gebruiker een nieuw item in het gegevens archief maken.

- `Remove-Item`: met deze cmdlet kan de gebruiker items uit het gegevens archief verwijderen. Als u deze cmdlet wilt ondersteunen, overschrijft u de methoden [System. Management. Automation. provider. Containercmdletprovider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) en [System. Management. Automation. provider. Containercmdletprovider. Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) .

- `Rename-Item`: met deze cmdlet kan de gebruiker de naam van items in het gegevens archief wijzigen. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Containercmdletprovider. Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) en [System. Management. Automation. provider. Containercmdletprovider. Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) overschrijven.

- `Set-Item`: met deze cmdlet kan de gebruiker de waarden van items in het gegevens archief bijwerken. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Itemcmdletprovider. SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) en [System. Management. Automation. provider. Itemcmdletprovider. Setitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) overschrijven.

### <a name="item-content-cmdlets"></a>Cmdlets voor item inhoud

- `Add-Content`: met deze cmdlet kan de gebruiker inhoud toevoegen aan een item.

- `Clear-Content`: met deze cmdlet kan de gebruiker inhoud uit een item verwijderen zonder het item te verwijderen. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) en [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) overschrijven.

- `Get-Content`: met deze cmdlet kan de gebruiker de inhoud van een item ophalen. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) en [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) overschrijven. De methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) retourneert een interface [System. Management. Automation. provider. Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) waarmee de methoden worden gedefinieerd die worden gebruikt om de inhoud te lezen.

- `Set-Content`: met deze cmdlet kan de gebruiker de inhoud van een item bijwerken. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) en [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) overschrijven. De methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) retourneert een interface [System. Management. Automation. provider. Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) waarmee de methoden worden gedefinieerd die worden gebruikt om de inhoud te schrijven.

### <a name="item-property-cmdlets"></a>Cmdlets voor item eigenschappen

- `Clear-ItemProperty`: met deze cmdlet kan de gebruiker de waarde van een eigenschap verwijderen. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) en [System. Management. Automation. provider. Ipropertycmdletprovider. Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) overschrijven.

- `Copy-ItemProperty`: met deze cmdlet kan de gebruiker een eigenschap en de waarde ervan kopiëren van de ene locatie naar een andere. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) en [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) overschrijven.

- `Get-ItemProperty`: met deze cmdlet worden de eigenschappen van een item opgehaald. Als u deze cmdlet wilt ondersteunen, overschrijft u de methoden [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) en [System. Management. Automation. provider. Ipropertycmdletprovider. Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) .

- `Move-ItemProperty`: met deze cmdlet kan de gebruiker een eigenschap en de waarde ervan verplaatsen van de ene locatie naar een andere. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) en [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) overschrijven.

- `New-ItemProperty`: met deze cmdlet kan de gebruiker een nieuwe eigenschap maken en de waarde ervan instellen. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Idynamicpropertycmdletprovider. NewProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) en [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) overschrijven.

- `Remove-ItemProperty`: met deze cmdlet kan de gebruiker een eigenschap en de waarde ervan verwijderen. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) en [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) overschrijven.

- `Rename-ItemProperty`: met deze cmdlet kan de gebruiker de naam van een eigenschap wijzigen. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) en [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) overschrijven.

- `Set-ItemProperty`: met deze cmdlet kan de gebruiker de eigenschappen van een item bijwerken. Als u deze cmdlet wilt ondersteunen, overschrijft u de methoden [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) en [System. Management. Automation. provider. Ipropertycmdletprovider. Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) .

### <a name="location-cmdlets"></a>Locatie-cmdlets

- `Get-Location`: haalt informatie op over de huidige werk locatie. U hoeft geen enkele methode te overschrijven om deze cmdlet te ondersteunen.

- `Pop-Location`: met deze cmdlet wordt de huidige locatie gewijzigd in de locatie die het laatst naar de stack is gepusht. U hoeft geen enkele methode te overschrijven om deze cmdlet te ondersteunen.

- `Push-Location`: deze cmdlet voegt de huidige locatie toe aan de bovenkant van een lijst met locaties (een ' stack '). U hoeft geen enkele methode te overschrijven om deze cmdlet te ondersteunen.

- `Set-Location`: met deze cmdlet wordt de huidige werk locatie ingesteld op een opgegeven locatie. U hoeft geen enkele methode te overschrijven om deze cmdlet te ondersteunen.

### <a name="path-cmdlets"></a>Pad-cmdlets

- `Join-Path`: met deze cmdlet kan de gebruiker een bovenliggend en onderliggend pad segment combi neren om een provider-intern pad te maken. Als u deze cmdlet wilt ondersteunen, overschrijft u de methode [System. Management. Automation. provider. Navigationcmdletprovider. Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) .

- `Convert-Path`: met deze cmdlet wordt een pad van een Windows Power shell-pad naar een Windows Power shell-provider pad geconverteerd.

- `Split-Path`: retourneert het opgegeven deel van een pad.

- `Resolve-Path`: de joker tekens in een pad worden omgezet en de inhoud van het pad wordt weer gegeven.

- `Test-Path`: deze cmdlet bepaalt of alle elementen van een pad bestaan. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Itemcmdletprovider. Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) en [System. Management. Automation. provider. Itemcmdletprovider. Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) overschrijven.

### <a name="psprovider-cmdlets"></a>PSProvider-cmdlets

- `Get-PSProvider`: deze cmdlet retourneert informatie over de providers die beschikbaar zijn in de sessie. U hoeft geen enkele methode te overschrijven om deze cmdlet te ondersteunen.