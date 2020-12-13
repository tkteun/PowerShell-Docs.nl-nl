---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample03
description: AccessDBProviderSample03
ms.openlocfilehash: bfd402903a9023b58dec8865663e3d649a50e1e1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667399"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

In dit voor beeld ziet u hoe u de methoden [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) en [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) overschrijft om aanroepen naar de `Get-Item` cmdlets en te ondersteunen `Set-Item` . De provider klasse in dit voor beeld is afgeleid van de klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .

## <a name="demonstrates"></a>Demonstreert

> [!IMPORTANT]
> Uw provider klasse is hoogstwaarschijnlijk afgeleid van een van de volgende klassen en implementeert mogelijk andere provider interfaces:
>
> - Klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .
> - Klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Zie [AccessDBProviderSample04](./accessdbprovidersample04.md).
> - Klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Zie [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Zie [uw Windows Power shell-provider ontwerpen](./provider-types.md)voor meer informatie over het kiezen van welke provider klasse moet worden afgeleid op basis van provider functies.

In dit voor beeld ziet u het volgende:

- Declareer het `CmdletProvider` kenmerk.
- Een provider klasse definiëren die is afgeleid van de klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .
- De methode [System. Management. Automation. provider. Drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) wordt overschreven om het gedrag van de cmdlet te wijzigen `New-PSDrive` , waardoor de gebruiker nieuwe stations kan maken.
  (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters aan de cmdlet kunt toevoegen `New-PSDrive` .)
- De methode [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) wordt overschreven om het verwijderen van bestaande stations te ondersteunen.
- De methode [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) wordt overschreven om het gedrag van de cmdlet te wijzigen `Get-Item` , waardoor de gebruiker items uit het gegevens archief kan ophalen. (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters aan de cmdlet kunt toevoegen `Get-Item` .)
- De methode [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) wordt overschreven om het gedrag van de cmdlet te wijzigen `Set-Item` , waardoor de gebruiker de items in het gegevens archief kan bijwerken. (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters aan de cmdlet kunt toevoegen `Get-Item` .)
- De methode [System. Management. Automation. provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) wordt overschreven om het gedrag van de cmdlet te wijzigen `Test-Path` . (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters aan de cmdlet kunt toevoegen `Test-Path` .)
- De methode [System. Management. Automation. provider. Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) wordt overschreven om te bepalen of het gegeven pad geldig is.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u hoe u de methoden overschrijft die nodig zijn om items in een micro soft Access-Data Base op te halen en in te stellen.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs" range="11-976":::

## <a name="see-also"></a>Zie ook

[System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Uw Windows PowerShell-provider ontwerpen](./provider-types.md)
