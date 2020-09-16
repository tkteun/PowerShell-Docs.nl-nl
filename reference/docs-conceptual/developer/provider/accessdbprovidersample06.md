---
title: AccessDBProviderSample06 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 893eb80574c7f142f92906961588e22b1ced0052
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786829"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

In dit voor beeld ziet u hoe inhouds methoden worden overschreven om aanroepen naar de `Clear-Content` `Get-Content` cmdlets, en te ondersteunen `Set-Content` . Deze methoden moeten worden geïmplementeerd wanneer de gebruiker de inhoud van de items in het gegevens archief moet beheren. De provider klasse in dit voor beeld is afgeleid van de klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) en implementeert de interface [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .

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
- Het definiëren van een provider klasse die is afgeleid van de klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) en die de interface [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) declareert.
- De methode [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) wordt overschreven om het gedrag van de cmdlet te wijzigen `Clear-Content` , waardoor de gebruiker de inhoud van een item kan verwijderen. (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters aan de cmdlet kunt toevoegen `Clear-Content` .)
- De methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) wordt overschreven om het gedrag van de cmdlet te wijzigen `Get-Content` , waardoor de gebruiker de inhoud van een item kan ophalen. (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters toevoegt aan de `Get-Content` cmdlet.).
- De methode [micro soft. Power shell. commands. Filesystemprovider. Getcontentwriter *](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) wordt overschreven om het gedrag van de cmdlet te wijzigen `Set-Content` , waardoor de gebruiker de inhoud van een item kan bijwerken. (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters aan de cmdlet kunt toevoegen `Set-Content` .)

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u hoe u de methoden overschrijft die nodig zijn om de inhoud van items in een micro soft Access-Data Base te wissen, op te halen en in te stellen.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-2399":::

## <a name="see-also"></a>Zie ook

[System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Uw Windows PowerShell-provider ontwerpen](./provider-types.md)
