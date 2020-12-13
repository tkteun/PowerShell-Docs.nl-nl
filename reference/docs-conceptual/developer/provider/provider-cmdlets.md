---
ms.date: 09/12/2016
ms.topic: reference
title: Provider-cmdlets
description: Provider-cmdlets
ms.openlocfilehash: 522dacfe4d7190c12ea0de148fe83bf6b5fed10f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92662902"
---
# <a name="provider-cmdlets"></a>Provider-cmdlets

De cmdlets die de gebruiker kan uitvoeren voor het beheren van een gegevens archief, worden provider-cmdlets genoemd. Als u deze cmdlets wilt ondersteunen, moet u enkele van de methoden die zijn gedefinieerd door de basis provider klassen en-interfaces overschrijven.

## <a name="provider-cmdlets"></a>Provider-cmdlets

Dit zijn de provider-cmdlets die kunnen worden uitgevoerd door de gebruiker:

### <a name="psdrive-cmdlets"></a>PSDrive-cmdlets

- `Get-PSDrive`: Met deze cmdlet worden de Windows Power Shell-stations in de huidige sessie geretourneerd. U hoeft geen enkele methode te overschrijven om deze cmdlet te ondersteunen.

- `New-PSDrive`: Met deze cmdlet kan de gebruiker Windows Power Shell-stations maken om toegang te krijgen tot het gegevens archief. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Drivecmdletprovider. newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) en [System. Management. Automation. provider. Drivecmdletprovider. Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) overschrijven.

- `Remove-PSDrive`: Met deze cmdlet kan de gebruiker Windows Power Shell-stations verwijderen die toegang hebben tot het gegevens archief. Als u deze cmdlet wilt ondersteunen, overschrijft u de methode [System. Management. Automation. provider. Drivecmdletprovider. Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) .

### <a name="item-cmdlets"></a>Cmdlets voor items

- `Clear-Item`: Met deze cmdlet kan de gebruiker de waarde van een item in het gegevens archief verwijderen. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Itemcmdletprovider. Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) en [System. Management. Automation. provider. Itemcmdletprovider. Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) overschrijven.

- `Copy-Item`: Met deze cmdlet kan de gebruiker een item kopiëren van de ene locatie naar een andere. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Containercmdletprovider. Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) en [System. Management. Automation. provider. Containercmdletprovider. Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) overschrijven.

- `Get-Item`: Met deze cmdlet kan de gebruiker gegevens ophalen uit het gegevens archief. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Itemcmdletprovider. GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) en [System. Management. Automation. provider. Itemcmdletprovider. Getitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) overschrijven.

- `Get-ChildItem`: Met deze cmdlet kan de gebruiker de onderliggende items van het bovenliggende item ophalen. Als u deze cmdlet wilt ondersteunen, moet u de volgende methoden overschrijven:

  - [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System. Management. Automation. provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System. Management. Automation. provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`: Met deze cmdlet kan de gebruiker de standaard actie uitvoeren die door het item is opgegeven. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) en [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) overschrijven.

- `Move-Item`: Met deze cmdlet kan de gebruiker een item verplaatsen van de ene locatie naar een andere locatie. Als u deze cmdlet wilt ondersteunen, overschrijft u de methoden [System. Management. Automation. provider. Navigationcmdletprovider. Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) en [System. Management. Automation. provider. Navigationcmdletprovider. Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)s.

- `New-ItemProperty`: Met deze cmdlet kan de gebruiker een nieuw item in het gegevens archief maken.

- `Remove-Item`: Met deze cmdlet kan de gebruiker items uit het gegevens archief verwijderen. Als u deze cmdlet wilt ondersteunen, overschrijft u de methoden [System. Management. Automation. provider. Containercmdletprovider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) en [System. Management. Automation. provider. Containercmdletprovider. Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) .

- `Rename-Item`: Met deze cmdlet kan de gebruiker de naam van items in het gegevens archief wijzigen. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Containercmdletprovider. Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) en [System. Management. Automation. provider. Containercmdletprovider. Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) overschrijven.

- `Set-Item`: Met deze cmdlet kan de gebruiker de waarden van items in het gegevens archief bijwerken. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Itemcmdletprovider. SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) en [System. Management. Automation. provider. Itemcmdletprovider. Setitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) overschrijven.

### <a name="item-content-cmdlets"></a>Cmdlets voor item inhoud

- `Add-Content`: Met deze cmdlet kan de gebruiker inhoud toevoegen aan een item.

- `Clear-Content`: Met deze cmdlet kan de gebruiker inhoud uit een item verwijderen zonder het item te verwijderen. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) en [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) overschrijven.

- `Get-Content`: Met deze cmdlet kan de gebruiker de inhoud van een item ophalen. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) en [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) overschrijven. De methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) retourneert een interface [System. Management. Automation. provider. Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader) waarmee de methoden worden gedefinieerd die worden gebruikt om de inhoud te lezen.

- `Set-Content`: Met deze cmdlet kan de gebruiker de inhoud van een item bijwerken. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) en [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) overschrijven. De methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) retourneert een interface [System. Management. Automation. provider. Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter) waarmee de methoden worden gedefinieerd die worden gebruikt om de inhoud te schrijven.

### <a name="item-property-cmdlets"></a>Cmdlets voor item eigenschappen

- `Clear-ItemProperty`: Met deze cmdlet kan de gebruiker de waarde van een eigenschap verwijderen. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Ipropertycmdletprovider. Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) en [System. Management. Automation. provider. Ipropertycmdletprovider. Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) overschrijven.

- `Copy-ItemProperty`: Met deze cmdlet kan de gebruiker een eigenschap en de waarde ervan kopiëren van de ene locatie naar een andere. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty) en [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters) overschrijven.

- `Get-ItemProperty`: Met deze cmdlet worden de eigenschappen van een item opgehaald. Als u deze cmdlet wilt ondersteunen, overschrijft u de methoden [System. Management. Automation. provider. Ipropertycmdletprovider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) en [System. Management. Automation. provider. Ipropertycmdletprovider. Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) .

- `Move-ItemProperty`: Met deze cmdlet kan de gebruiker een eigenschap en de waarde ervan verplaatsen van de ene locatie naar een andere. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty) en [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters) overschrijven.

- `New-ItemProperty`: Met deze cmdlet kan de gebruiker een nieuwe eigenschap maken en de waarde ervan instellen. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Idynamicpropertycmdletprovider. NewProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty) en [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) overschrijven.

- `Remove-ItemProperty`: Met deze cmdlet kan de gebruiker een eigenschap en de waarde ervan verwijderen. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) en [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) overschrijven.

- `Rename-ItemProperty`: Met deze cmdlet kan de gebruiker de naam van een eigenschap wijzigen. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) en [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) overschrijven.

- `Set-ItemProperty`: Met deze cmdlet kan de gebruiker de eigenschappen van een item bijwerken. Als u deze cmdlet wilt ondersteunen, overschrijft u de methoden [System. Management. Automation. provider. Ipropertycmdletprovider. SetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) en [System. Management. Automation. provider. Ipropertycmdletprovider. Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) .

### <a name="location-cmdlets"></a>Locatie-cmdlets

- `Get-Location`: Haalt informatie op over de huidige werk locatie. U hoeft geen enkele methode te overschrijven om deze cmdlet te ondersteunen.

- `Pop-Location`: Met deze cmdlet wordt de huidige locatie gewijzigd in de locatie die het laatst is gepusht naar de stack. U hoeft geen enkele methode te overschrijven om deze cmdlet te ondersteunen.

- `Push-Location`: Met deze cmdlet wordt de huidige locatie boven aan een lijst met locaties (een ' stack ') toegevoegd. U hoeft geen enkele methode te overschrijven om deze cmdlet te ondersteunen.

- `Set-Location`: Met deze cmdlet wordt de huidige werk locatie ingesteld op een opgegeven locatie. U hoeft geen enkele methode te overschrijven om deze cmdlet te ondersteunen.

### <a name="path-cmdlets"></a>Pad-cmdlets

- `Join-Path`: Met deze cmdlet kan de gebruiker een segment van het bovenliggende en onderliggende pad combi neren om een provider-intern pad te maken. Als u deze cmdlet wilt ondersteunen, overschrijft u de methode [System. Management. Automation. provider. Navigationcmdletprovider. Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) .

- `Convert-Path`: Met deze cmdlet wordt een pad van een Windows Power shell-pad naar een Windows Power shell-provider pad geconverteerd.

- `Split-Path`: Retourneert het opgegeven deel van een pad.

- `Resolve-Path`: Hiermee worden de joker tekens in een pad omgezet en wordt de inhoud van het pad weer gegeven.

- `Test-Path`: Met deze cmdlet wordt bepaald of alle elementen van een pad bestaan. Als u deze cmdlet wilt ondersteunen, moet u de methoden [System. Management. Automation. provider. Itemcmdletprovider. Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) en [System. Management. Automation. provider. Itemcmdletprovider. Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) overschrijven.

### <a name="psprovider-cmdlets"></a>PSProvider-cmdlets

- `Get-PSProvider`: Deze cmdlet retourneert informatie over de providers die beschikbaar zijn in de sessie. U hoeft geen enkele methode te overschrijven om deze cmdlet te ondersteunen.
