---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample02
description: AccessDBProviderSample02
ms.openlocfilehash: ebba2381370cf73f1e39015990f81dc4fd6dd937
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667433"
---
# <a name="accessdbprovidersample02"></a>AccessDBProviderSample02

In dit voor beeld ziet u hoe u de methoden [System. Management. Automation. provider. Drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) en [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) overschrijft om aanroepen naar de `New-PSDrive` cmdlets en te ondersteunen `Remove-PSDrive` . De provider klasse in dit voor beeld is afgeleid van de klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .

## <a name="demonstrates"></a>Demonstreert

> [!IMPORTANT]
> Uw provider klasse is hoogstwaarschijnlijk afgeleid van een van de volgende klassen en implementeert mogelijk andere provider interfaces:
>
> - Klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Zie [AccessDBProviderSample03](./accessdbprovidersample03.md).
> - Klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Zie [AccessDBProviderSample04](./accessdbprovidersample04.md).
> - Klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Zie [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Zie [uw Windows Power shell-provider ontwerpen](./provider-types.md)voor meer informatie over het kiezen van welke provider klasse moet worden afgeleid op basis van provider functies.

In dit voor beeld ziet u het volgende:

- Declareer het `CmdletProvider` kenmerk.

- Een provider klasse definiëren die stations uit de klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .

- De methode [System. Management. Automation. provider. Drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) wordt overschreven ter ondersteuning van het maken van nieuwe stations. (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters aan de cmdlet kunt toevoegen `New-PSDrive` .)

- De methode [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) wordt overschreven om het verwijderen van bestaande stations te ondersteunen.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u hoe u de methoden [System. Management. Automation. provider. Drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) en [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) overschrijft. Wanneer de verbindings gegevens van een station worden gemaakt voor deze voorbeeld provider, worden deze opgeslagen in een- `AccessDBPsDriveInfo` object.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a>Zie ook

[System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Uw Windows PowerShell-provider ontwerpen](./provider-types.md)
