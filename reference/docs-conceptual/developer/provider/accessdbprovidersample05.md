---
title: AccessDBProviderSample05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a26661f2-a63c-4ca7-ad3e-dcb4d32ce5a1
caps.latest.revision: 8
ms.openlocfilehash: 43d18672ec4f52961b2a2460635468a2d6fb41e5
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633376"
---
# <a name="accessdbprovidersample05"></a>AccessDBProviderSample05

In dit voor beeld ziet u hoe u container methoden overschrijft ter ondersteuning van aanroepen naar de- `Move-Item` en- `Join-Path` cmdlets. Deze methoden moeten worden geïmplementeerd wanneer de gebruiker items in een container moet verplaatsen en als het gegevens archief geneste containers bevat. De provider klasse in dit voor beeld is afgeleid van de klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

## <a name="demonstrates"></a>Demonstreert

> [!IMPORTANT]
> Uw provider klasse is hoogstwaarschijnlijk afgeleid van een van de volgende klassen en implementeert mogelijk andere provider interfaces:
>
> - Klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Zie [AccessDBProviderSample03](./accessdbprovidersample03.md).
> - Klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Zie [AccessDBProviderSample04](./accessdbprovidersample04.md).
> - Klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .
>
> Zie [uw Windows Power shell-provider ontwerpen](./provider-types.md)voor meer informatie over het kiezen van welke provider klasse moet worden afgeleid op basis van provider functies.

In dit voor beeld ziet u het volgende:

- Declareer het `CmdletProvider` kenmerk.

- Een provider klasse definiëren die is afgeleid van de klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

- De methode [System. Management. Automation. provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) wordt overschreven om het gedrag van de cmdlet te wijzigen `Move-Item` , waardoor de gebruiker items van de ene locatie naar de andere kan verplaatsen. (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters aan de cmdlet kunt toevoegen `Move-Item` .)

- De methode [System. Management. Automation. provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) wordt overschreven om het gedrag van de cmdlet te wijzigen `Join-Path` .

- De methode [System. Management. Automation. provider. Navigationcmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) wordt overschreven.

- De methode [System. Management. Automation. provider. Navigationcmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) wordt overschreven.

- De methode [System. Management. Automation. provider. Navigationcmdletprovider. Getparentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) wordt overschreven.

- De methode [System. Management. Automation. provider. Navigationcmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) wordt overschreven.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u hoe u de methoden overschrijft die nodig zijn om items in een micro soft Access-Data Base te verplaatsen.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="11-1960":::

## <a name="see-also"></a>Zie ook

[System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Uw Windows PowerShell-provider ontwerpen](./provider-types.md)
