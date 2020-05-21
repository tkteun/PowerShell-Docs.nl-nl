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
ms.openlocfilehash: 9e70fbeaef61d04e66f16d06519742ff2f679df6
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564237"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Dynamische parameters voor provider-cmdlets

Providers kunnen dynamische para meters definiëren die worden toegevoegd aan een provider-cmdlet wanneer de gebruiker een bepaalde waarde voor een van de statische para meters van de cmdlet opgeeft. Een provider kan bijvoorbeeld verschillende dynamische para meters toevoegen op basis van het pad dat door de gebruiker wordt opgegeven wanneer ze de `Get-Item` `Set-Item` cmdlets of provider aanroepen.

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

`Clear-Content`cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` para meter van de cmdlet Clear-Clear door de methode [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) te implementeren.

`Clear-Item`cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` para meter van de `Clear-Item` cmdlet door de methode [System. Management. Automation. provider. Itemcmdletprovider. Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) te implementeren.

`Clear-ItemProperty`cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` para meter van de `Clear-ItemProperty` cmdlet door de methode [System. Management. Automation. provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) te implementeren.

`Copy-Item`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` `Destination` `Recurse` para meters, en, door de `Copy-Item` implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) .

De cmdlet Get-ChildItems kunt u dynamische para meters definiëren die door de `Path` `Recurse` para meters van de cmdlet worden geactiveerd `Get-ChildItem` door de implementatie van de methoden [System. Management. Automation. provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) en [System. Management. Automation. provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) .

`Get-Content`cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` para meter van de `Get-Content` cmdlet door de methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) te implementeren.

`Get-Item`cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` para meter van de `Get-Item` cmdlet door de methode [System. Management. Automation. provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) te implementeren.

`Get-ItemProperty`cmdlet kunt u dynamische para meters definiëren die door de `Path` `Name` para meters van de `Get-ItemProperty` cmdlet worden geactiveerd door de implementatie van de methode [System. Management. Automation. provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) .

`Invoke-Item`cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` para meter van de `Invoke-Item` cmdlet door de methode [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) te implementeren.

`Move-Item`cmdlet kunt u dynamische para meters definiëren die door de `Path` `Destination` para meters van de `Move-Item` cmdlet worden geactiveerd door de implementatie van de methode [System. Management. Automation. provider. Navigationcmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) .

`New-Item`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` `ItemType` `Value` para meters, en, door de `New-Item` implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) .

`New-ItemProperty`-cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` `Name` `PropertyType` `Value` para meters,, en van de `New-ItemProperty` cmdlet door de implementatie van de methode [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Newpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) .

`New-PSDrive`cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door het object [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) dat door de cmdlet wordt geretourneerd `New-PSDrive` door de implementatie van de methode [System. Management. Automation. provider. Drivecmdletprovider. Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .

`Remove-Item`U kunt dynamische para meters definiëren die worden geactiveerd door `Path` de `Recurse` para meters van de `Remove-Item` cmdlet, door de methode [System. Management. Automation. provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) te implementeren.

`Remove-ItemProperty`U kunt dynamische para meters definiëren die worden geactiveerd door `Path` de `Name` para meters van de `Remove-ItemProperty` cmdlet, door de methode [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Removepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) te implementeren.

`Rename-Item`cmdlet kunt u dynamische para meters definiëren die door de `Path` `NewName` para meters van de `Rename-Item` cmdlet worden geactiveerd door de implementatie van de methode [System. Management. Automation. provider. Containercmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) .

`Rename-ItemProperty`U kunt de dynamische para meters definiëren die worden geactiveerd door de `Path` `Name` `NewName` para meters,, en uit de `Rename-ItemProperty` cmdlets door de methode [System. Management. Automation. provider. Idynamicpropertycmdletprovider. Renamepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) te implementeren.

`Set-Content`cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` para meter van de `Set-Content` cmdlet door de methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) te implementeren.

`Set-Item`cmdlet kunt u dynamische para meters definiëren die door de `Path` `Value` para meters van de `Set-Item` cmdlet worden geactiveerd door de implementatie van de methode [System. Management. Automation. provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) .

`Set-ItemProperty`cmdlet kunt u dynamische para meters definiëren die door de `Path` `Value` para meters van de `Set-Item` cmdlet worden geactiveerd door de implementatie van de methode [System. Management. Automation. provider. Ipropertycmdletprovider. Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) .

`Test-Path`cmdlet kunt u dynamische para meters definiëren die worden geactiveerd door de `Path` para meter van de `Test-Path` cmdlet door de methode [System. Management. Automation. provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) te implementeren.

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-provider schrijven](./writing-a-windows-powershell-provider.md)
