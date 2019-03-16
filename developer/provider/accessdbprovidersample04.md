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
ms.openlocfilehash: d9109e8d5b69a25ad52b90bcaff9628b01067211
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057617"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

In dit voorbeeld laat zien hoe u containermethoden ter ondersteuning van aanroepen naar overschrijven de `Copy-Item`, `Get-ChildItem`, `New-Item`, en `Remove-Item` cmdlets. Deze methoden moeten worden uitgevoerd wanneer het gegevensarchief bevat items die containers zijn. Een container is een groep van onderliggende items onder een gemeenschappelijk bovenliggend item. De providerklasse in dit voorbeeld is afgeleid van de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasse.

## <a name="demonstrates"></a>Hier ziet u

> [!IMPORTANT]
> Uw providerklasse waarschijnlijk wordt afgeleid van de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

In dit voorbeeld ziet u het volgende:

- Declareren de `CmdletProvider` kenmerk.

- Het definiëren van een klasse in de provider die is afgeleid van de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasse.

- Overschrijven de [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) methode voor het wijzigen van het gedrag van de `Copy-Item` cmdlet waarmee de gebruiker om items te kopiëren van de ene locatie naar een andere. (In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `Copy-Item` cmdlet.)

- Overschrijven de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) methode om het gedrag van de cmdlet Get-ChildItems, waarmee de gebruiker om op te halen van de onderliggende items van het bovenliggende item te wijzigen . (In dit voorbeeld wordt dynamische parameters toevoegen aan de cmdlet Get-ChildItems niet weergegeven.)

- Overschrijven de [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) methode om het gedrag van de cmdlet Get-ChildItems te wijzigen wanneer de `Name` parameter van de cmdlet is opgegeven.

- Overschrijven de [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) methode voor het wijzigen van het gedrag van de `New-Item` cmdlet, waarmee de gebruiker items toevoegen aan het gegevensarchief. (In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `New-Item` cmdlet.)

- Overschrijven de [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) methode voor het wijzigen van het gedrag van de `Remove-Item` cmdlet. (In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `Remove-Item` cmdlet.)

## <a name="example"></a>Voorbeeld

In dit voorbeeld laat zien hoe de methoden die nodig zijn om te kopiëren, maken en verwijderen van items, evenals de methoden voor het ophalen van de onderliggende items van een bovenliggend item overschrijven.

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Het ontwerpen van uw Windows PowerShell-Provider](./provider-types.md)