---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample04
description: AccessDBProviderSample04
ms.openlocfilehash: 962d0ab673ff797a60b56ccae7a16a810cc43c58
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649041"
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
- Het overschrijven van de methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) voor het wijzigen van het gedrag van de cmdlet Get-ChildItems, waarmee de gebruiker de onderliggende items van het bovenliggende item kan ophalen. (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters toevoegt aan de Get-ChildItems cmdlet.)
- Het overschrijven van de methode [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) om het gedrag van de cmdlet Get-ChildItems te wijzigen wanneer de `Name` para meter van de cmdlet wordt opgegeven.
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
