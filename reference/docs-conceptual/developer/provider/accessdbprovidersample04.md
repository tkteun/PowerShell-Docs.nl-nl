---
title: AccessDBProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: c0efd10680d3323b6c8d932604176c4425e7266a
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633359"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

In dit voor beeld ziet u hoe u container methoden overschrijft ter ondersteuning van aanroepen naar de `Copy-Item` `Get-ChildItem` cmdlets,, `New-Item` en `Remove-Item` . Deze methoden moeten worden geïmplementeerd wanneer het gegevens archief items bevat die containers zijn. Een container is een groep onderliggende items onder een gemeen schappelijk bovenliggend item. De provider klasse in dit voor beeld is afgeleid van de klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .

## <a name="demonstrates"></a>Demonstreert

> [!IMPORTANT]
> Uw provider klasse wordt hoogstwaarschijnlijk afgeleid van [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

In dit voor beeld ziet u het volgende:

- Declareer het `CmdletProvider` kenmerk.
- Een provider klasse definiëren die is afgeleid van de klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .
- De methode [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) wordt overschreven om het gedrag van de cmdlet te wijzigen `Copy-Item` waarmee de gebruiker items van de ene locatie naar de andere kan kopiëren. (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters aan de cmdlet kunt toevoegen `Copy-Item` .)
- De methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) wordt overschreven om het gedrag van de cmdlet Get-ChildItems te wijzigen, waarmee de gebruiker de onderliggende items van het bovenliggende item kan ophalen. (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters toevoegt aan de cmdlet Get-ChildItems.)
- De methode [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) wordt overschreven om het gedrag van de cmdlet Get-ChildItems te wijzigen wanneer de `Name` para meter van de cmdlet wordt opgegeven.
- De methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) wordt overschreven om het gedrag van de cmdlet te wijzigen `New-Item` , waardoor de gebruiker items kan toevoegen aan het gegevens archief. (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters aan de cmdlet kunt toevoegen `New-Item` .)
- De methode [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) wordt overschreven om het gedrag van de cmdlet te wijzigen `Remove-Item` . (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters aan de cmdlet kunt toevoegen `Remove-Item` .)

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u hoe u de methoden overschrijft die nodig zijn voor het kopiëren, maken en verwijderen van items, evenals methoden voor het ophalen van de onderliggende items van een bovenliggend item.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a>Zie ook

[System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Uw Windows PowerShell-provider ontwerpen](./provider-types.md)
