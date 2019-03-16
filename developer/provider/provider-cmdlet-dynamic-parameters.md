---
title: Dynamische parameters van de cmdlet provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058229"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Dynamische parameters voor provider-cmdlets

Providers kunnen dynamische parameters die worden toegevoegd aan een cmdlet provider wanneer de gebruiker Hiermee geeft u een bepaalde waarde voor een van de statische parameters van de cmdlet definiëren. Bijvoorbeeld, een provider verschillende dynamische parameters op basis van kunt toevoegen op welk pad van de gebruiker opgeeft wanneer ze bellen de `Get-Item` of `Set-Item` provider-cmdlets.

## <a name="dynamic-parameter-methods"></a>Dynamische Parameter-methoden

Dynamische parameters zijn gedefinieerd door het implementeren van een van de dynamische parameter-methoden, zoals de [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) en [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s methoden. Deze methoden retourneren een object met openbare eigenschappen die zijn voorzien van kenmerken die vergelijkbaar zijn met die van zelfstandige-cmdlets. Hier volgt een voorbeeld van een implementatie van de [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) methode die is overgenomen uit de certificaat-provider:

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

In tegenstelling tot de statische parameters van de provider-cmdlets, kunt u de kenmerken van deze parameters opgeven op dezelfde manier dat parameters zijn gedefinieerd in zelfstandige-cmdlets. Hier volgt een voorbeeld van een dynamische parameter-klasse die is overgenomen uit de certificaat-provider:

```csharp
internal sealed class CertificateProviderDynamicParameters
{
  /// <summary>
  /// Dynamic parameter the controls whether we only return
  /// code signing certs.
  /// </summary>
  [Parameter()]
  public SwitchParameter CodeSigningCert
  {
    get
    {
      {
        return codeSigningCert;
      }
    }

    set
    {
      {
        codeSigningCert = value;
      }
    }
  }

    private SwitchParameter codeSigningCert = new SwitchParameter();
}
```

## <a name="dynamic-parameters"></a>Dynamische Parameters

Hier volgt een lijst van de statische parameters die kunnen worden gebruikt om toe te voegen dynamische parameters.

`Clear-Content` cmdlet kunt u dynamische parameters die worden geactiveerd door de `Path` parameter van de cmdlet wissen wissen door het implementeren van de [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) methode.

`Clear-Item` cmdlet kunt u dynamische parameters die worden geactiveerd door de `Path` parameter van de `Clear-Item` cmdlet door het implementeren van de [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) methode.

`Clear-ItemProperty` cmdlet kunt u dynamische parameters die worden geactiveerd door de `Path` parameter van de `Clear-ItemProperty` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) methode.

`Copy-Item` cmdlet kunt u dynamische parameters die worden geactiveerd door de `Path`, `Destination`, en `Recurse` parameters van de `Copy-Item` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) methode.

De cmdlet Get-ChildItems kunt u dynamische parameters die worden geactiveerd door de `Path` en `Recurse` parameters van de `Get-ChildItem` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) en [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) methoden.

`Get-Content` cmdlet kunt u dynamische parameters die worden geactiveerd door de `Path` parameter van de `Get-Content` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) methode.

`Get-Item` cmdlet kunt u dynamische parameters die worden geactiveerd door de `Path` parameter van de `Get-Item` cmdlet door het implementeren van de [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) methode.

`Get-ItemProperty` cmdlet kunt u dynamische parameters die worden geactiveerd door de `Path` en `Name` parameters van de `Get-ItemProperty` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) methode.

`Invoke-Item` cmdlet kunt u dynamische parameters die worden geactiveerd door de `Path` parameter van de `Invoke-Item` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) methode.

`Move-Item` cmdlet kunt u dynamische parameters die worden geactiveerd door de `Path` en `Destination` parameters van de `Move-Item` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) methode.

`New-Item` cmdlet kunt u dynamische parameters die worden geactiveerd door de `Path`, `ItemType`, en `Value` parameters van de `New-Item` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) methode.

`New-ItemProperty` cmdlet kunt u dynamische parameters die worden geactiveerd door de `Path`, `Name`, `PropertyType`, en `Value` parameters van de `New-ItemProperty` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) methode.

`New-PSDrive` cmdlet kunt u dynamische parameters die worden geactiveerd door de [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object dat wordt geretourneerd door de `New-PSDrive` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) methode.

`Remove-Item` U kunt dynamische parameters gedefinieerd die worden geactiveerd door de `Path` en `Recurse` parameters van de `Remove-Item` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) methode.

`Remove-ItemProperty` U kunt dynamische parameters gedefinieerd die worden geactiveerd door de `Path` en `Name` parameters van de `Remove-ItemProperty` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) methode.

`Rename-Item` cmdlet kunt u dynamische parameters die worden geactiveerd door de `Path` en `NewName` parameters van de `Rename-Item` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) methode.

`Rename-ItemProperty` U kunt dynamische parameters gedefinieerd die worden geactiveerd door de `Path`, `Name`, en `NewName` parameters van de `Rename-ItemProperty` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) methode.

`Set-Content` cmdlet kunt u dynamische parameters die worden geactiveerd door de `Path` parameter van de `Set-Content` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) methode.

`Set-Item` cmdlet kunt u dynamische parameters die worden geactiveerd door de `Path` en `Value` parameters van de `Set-Item` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) methode.

`Set-ItemProperty` cmdlet kunt u dynamische parameters die worden geactiveerd door de `Path` en `Value` parameters van de `Set-Item` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) methode.

`Test-Path` cmdlet kunt u dynamische parameters die worden geactiveerd door de `Path` parameter van de `Test-Path` cmdlet door het implementeren van de [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) methode.

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Provider](./writing-a-windows-powershell-provider.md)