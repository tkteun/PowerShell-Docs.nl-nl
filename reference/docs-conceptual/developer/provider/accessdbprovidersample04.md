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
ms.openlocfilehash: 7096f8066568c214a5902f6943a2c093932d3b56
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356859"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

In dit voor beeld ziet u hoe u container methoden overschrijft ter ondersteuning van aanroepen naar de `Copy-Item`, `Get-ChildItem`, `New-Item`en `Remove-Item`-cmdlets. Deze methoden moeten worden geïmplementeerd wanneer het gegevens archief items bevat die containers zijn. Een container is een groep onderliggende items onder een gemeen schappelijk bovenliggend item. De provider klasse in dit voor beeld is afgeleid van de klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .

## <a name="demonstrates"></a>Hier ziet u

> [!IMPORTANT]
> Uw provider klasse wordt hoogstwaarschijnlijk afgeleid van [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

In dit voor beeld ziet u het volgende:

- Declareer het `CmdletProvider` kenmerk.

- Een provider klasse definiëren die is afgeleid van de klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .

- De methode [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) wordt overschreven om het gedrag van de `Copy-Item`-cmdlet te wijzigen waarmee de gebruiker items van de ene locatie naar de andere kan kopiëren. (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters toevoegt aan de `Copy-Item` cmdlet.)

- De methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) wordt overschreven om het gedrag van de cmdlet Get-ChildItems te wijzigen, waarmee de gebruiker de onderliggende items van het bovenliggende item kan ophalen. (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters toevoegt aan de cmdlet Get-ChildItems.)

- De methode [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) wordt overschreven om het gedrag van de cmdlet Get-ChildItems te wijzigen wanneer de para meter `Name` van de cmdlet is opgegeven.

- Het overschrijven van de methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) voor het wijzigen van het gedrag van de cmdlet `New-Item`, waarmee de gebruiker items kan toevoegen aan het gegevens archief. (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters toevoegt aan de `New-Item` cmdlet.)

- De methode [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) wordt overschreven om het gedrag van de cmdlet `Remove-Item` te wijzigen. (In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters toevoegt aan de `Remove-Item` cmdlet.)

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u hoe u de methoden overschrijft die nodig zijn voor het kopiëren, maken en verwijderen van items, evenals methoden voor het ophalen van de onderliggende items van een bovenliggend item.

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Zie ook

[System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Uw Windows Power shell-provider ontwerpen](./provider-types.md)
