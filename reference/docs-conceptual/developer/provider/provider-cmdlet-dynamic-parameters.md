---
title: Dynamische para meters van provider-cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352379"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Dynamische parameters voor provider-cmdlets

Providers kunnen dynamische para meters definiëren die worden toegevoegd aan een provider-cmdlet wanneer de gebruiker een bepaalde waarde voor een van de statische para meters van de cmdlet opgeeft. Een provider kan bijvoorbeeld verschillende dynamische para meters toevoegen op basis van het pad dat de gebruiker opgeeft wanneer ze de `Get-Item`-of `Set-Item` provider-cmdlets aanroepen.

## <a name="dynamic-parameter-methods"></a>Dynamische parameter methoden

Dynamische para meters worden gedefinieerd door een van de dynamische parameter methoden te implementeren, zoals de methoden [System. Management. Automation. provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) en [System. Management. Automation. provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s. Deze methoden retour neren een object met open bare eigenschappen die zijn gedecoreerd met kenmerken die vergelijkbaar zijn met die van zelfstandige cmdlets. Hier volgt een voor beeld van een implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) die is gemaakt van de certificaat provider:

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

In tegens telling tot de statische para meters van provider-cmdlets, kunt u de kenmerken van deze para meters op dezelfde manier opgeven als de para meters die zijn gedefinieerd in zelfstandige cmdlets. Hier volgt een voor beeld van een dynamische para meter-klasse die is gemaakt van de certificaat provider:

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

## <a name="dynamic-parameters"></a>Dynamische para meters

Hier volgt een lijst met de statische para meters die kunnen worden gebruikt om dynamische para meters toe te voegen.

`Clear-Content`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de para meter `Path` van de cmdlet Clear-Clear door de methode [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) te implementeren.

`Clear-Item`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de para meter `Path` van de cmdlet `Clear-Item` door de implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) .

`Clear-ItemProperty`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de para meter `Path` van de cmdlet `Clear-ItemProperty` door de implementatie van de methode [System. Management. Automation. provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) .

`Copy-Item`-cmdlet kunt u dynamische para meters definiëren die door de para meters `Path`, `Destination`en `Recurse` van de `Copy-Item` cmdlet worden geactiveerd door de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) .

De cmdlet Get-ChildItems kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` en `Recurse` para meters van de cmdlet `Get-ChildItem` door de implementatie van de methoden [System. Management. Automation. provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) en [System. Management. Automation. provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) .

`Get-Content`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de para meter `Path` van de cmdlet `Get-Content` door de implementatie van de methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) .

`Get-Item`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de para meter `Path` van de cmdlet `Get-Item` door de implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) .

`Get-ItemProperty`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` en `Name` para meters van de cmdlet `Get-ItemProperty` door de implementatie van de methode [System. Management. Automation. provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) .

`Invoke-Item`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de para meter `Path` van de cmdlet `Invoke-Item` door de implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) .

`Move-Item`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` en `Destination` para meters van de cmdlet `Move-Item` door de implementatie van de methode [System. Management. Automation. provider. Navigationcmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) .

`New-Item`-cmdlet kunt u dynamische para meters definiëren die door de para meters `Path`, `ItemType`en `Value` van de `New-Item` cmdlet worden geactiveerd door de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) .

`New-ItemProperty`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de para meters `Path`, `Name`, `PropertyType`en `Value` van de cmdlet `New-ItemProperty` door de implementatie van de methode [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Newpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) .

`New-PSDrive`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door het object [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) , dat door de `New-PSDrive`-cmdlet wordt geretourneerd door de implementatie van de methode [System. Management. Automation. provider. Drivecmdletprovider. Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .

`Remove-Item` kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` en `Recurse` para meters van de cmdlet `Remove-Item` door de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) .

`Remove-ItemProperty` kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` en `Name` para meters van de cmdlet `Remove-ItemProperty` door de implementatie van de methode [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Removepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) .

`Rename-Item`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` en `NewName` para meters van de cmdlet `Rename-Item` door de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) .

`Rename-ItemProperty` kunt u dynamische para meters definiëren die worden geactiveerd door de para meters `Path`, `Name`en `NewName` van de `Rename-ItemProperty` cmdlet door de methode [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Renamepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) te implementeren.

`Set-Content`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de para meter `Path` van de cmdlet `Set-Content` door de implementatie van de methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) .

`Set-Item`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` en `Value` para meters van de cmdlet `Set-Item` door de implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) .

`Set-ItemProperty`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` en `Value` para meters van de cmdlet `Set-Item` door de implementatie van de methode [System. Management. Automation. provider. Ipropertycmdletprovider. Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) .

`Test-Path`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de para meter `Path` van de cmdlet `Test-Path` door de implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) .

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-provider schrijven](./writing-a-windows-powershell-provider.md)