---
title: AccessDBProviderSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: 57b6cfaa5f29300c60a5a745797111b6beba3133
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081062"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

In dit voorbeeld laat zien hoe u overschrijven de [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) en [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methoden voor de ondersteuning van aanroepen naar de `Get-Item` en `Set-Item` cmdlets. De providerklasse in dit voorbeeld is afgeleid van de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasse.

## <a name="demonstrates"></a>Ziet u

> [!IMPORTANT]
> Uw providerklasse wordt waarschijnlijk zijn afgeleid van een van de volgende klassen en mogelijk andere provider-interfaces te implementeren:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class. Zie [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class. Zie [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Voor meer informatie over het kiezen van welke providerklasse afgeleid op basis van de functies van resourceproviders, raadpleeg dan [het ontwerpen van uw Windows PowerShell-Provider](./provider-types.md).

In dit voorbeeld ziet u het volgende:

- Declareren de `CmdletProvider` kenmerk.

- Het definiëren van een klasse in de provider die is afgeleid van de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasse.

- Overschrijven de [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) methode voor het wijzigen van het gedrag van de `New-PSDrive` cmdlet, zodat de gebruiker om nieuwe stations te maken. (In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `New-PSDrive` cmdlet.)

- Overschrijven de [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methode voor het verwijderen van bestaande stations ondersteunen.

- Overschrijven de [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) methode voor het wijzigen van het gedrag van de `Get-Item` cmdlet, zodat de gebruiker om items te halen uit het gegevensarchief. (In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `Get-Item` cmdlet.)

- Overschrijven de [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methode voor het wijzigen van het gedrag van de `Set-Item` cmdlet, zodat de gebruiker om bij te werken van de items in het gegevensarchief. (In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `Get-Item` cmdlet.)

- Overschrijven de [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) methode voor het wijzigen van het gedrag van de `Test-Path` cmdlet. (In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `Test-Path` cmdlet.)

- Overschrijven de [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) methode om te bepalen of het opgegeven pad geldig is.

## <a name="example"></a>Voorbeeld

In dit voorbeeld laat zien hoe de methoden die nodig zijn voor het ophalen en instellen van items in een Microsoft Access-gegevens base overschrijven.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Het ontwerpen van uw Windows PowerShell-Provider](./provider-types.md)