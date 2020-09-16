---
title: Voor beelden van providers | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9eb8eb64bbe585ebd8024c0215853ff04a5c3e54
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778441"
---
# <a name="provider-samples"></a>Voorbeelden van providers

Deze sectie bevat voor beelden van providers die toegang hebben tot een micro soft Access-Data Base. Deze voor beelden bevatten provider klassen die zijn afgeleid van alle basis provider klassen.

## <a name="in-this-section"></a>In deze sectie

Deze sectie bevat de volgende onderwerpen:

[AccessDBProviderSample01](./accessdbprovidersample01.md) -voor beeld In dit voor beeld ziet u hoe u de provider klasse declareert die rechtstreeks is afgeleid van de klasse [System. Management. Automation. provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) . Deze is alleen opgenomen voor volledigheid.

[AccessDBProviderSample02](./accessdbprovidersample02.md) In dit voor beeld ziet u hoe u de methoden [System. Management. Automation. provider. Drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) en [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) overschrijft om aanroepen naar de `New-PSDrive` cmdlets en te ondersteunen `Remove-PSDrive` . De provider klasse in dit voor beeld is afgeleid van de klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .

[AccessDBProviderSample03](./accessdbprovidersample03.md) In dit voor beeld ziet u hoe u de methoden [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) en [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) overschrijft om aanroepen naar de `Get-Item` cmdlets en te ondersteunen `Set-Item` . De provider klasse in dit voor beeld is afgeleid van de klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .

[AccessDBProviderSample04](./accessdbprovidersample04.md) In dit voor beeld ziet u hoe u container methoden overschrijft ter ondersteuning van aanroepen naar de `Copy-Item` `Get-ChildItem` cmdlets,, `New-Item` en `Remove-Item` . Deze methoden moeten worden geïmplementeerd wanneer het gegevens archief items bevat die containers zijn. Een container is een groep onderliggende items onder een gemeen schappelijk bovenliggend item. De provider klasse in dit voor beeld is afgeleid van de klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .

[AccessDBProviderSample05](./accessdbprovidersample05.md) In dit voor beeld ziet u hoe u container methoden overschrijft ter ondersteuning van aanroepen naar de- `Move-Item` en- `Join-Path` cmdlets. Deze methoden moeten worden geïmplementeerd wanneer de gebruiker items in een container moet verplaatsen en als het gegevens archief geneste containers bevat. De provider klasse in dit voor beeld is afgeleid van de klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

[AccessDBProviderSample06](./accessdbprovidersample06.md) In dit voor beeld ziet u hoe inhouds methoden worden overschreven om aanroepen naar de `Clear-Content` `Get-Content` cmdlets, en te ondersteunen `Set-Content` . Deze methoden moeten worden geïmplementeerd wanneer de gebruiker de inhoud van de items in het gegevens archief moet beheren. De provider klasse in dit voor beeld is afgeleid van de klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) en implementeert de interface [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-provider schrijven](./writing-a-windows-powershell-provider.md)
