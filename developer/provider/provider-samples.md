---
title: Voorbeelden van de provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4933dad-fec9-4337-a1a9-9dc16ee87cc3
caps.latest.revision: 9
ms.openlocfilehash: 1e7aeb5bcb6bd5a2845648c3327e2245e6c428ba
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844798"
---
# <a name="provider-samples"></a>Voorbeelden van providers

Deze sectie bevat voorbeelden van providers die toegang hebben tot een Microsoft Access-database. Deze voorbeelden bevatten de klassen van de provider die zijn afgeleid van alle klassen van de basis-provider.

## <a name="in-this-section"></a>In deze sectie

Deze sectie bevat de volgende onderwerpen:

[Voorbeeld van AccessDBProviderSample01](./accessdbprovidersample01.md) in dit voorbeeld laat zien hoe u de providerklasse die is afgeleid rechtstreeks van declareren de [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klasse. Het is hier opgenomen voor de volledigheid.

[AccessDBProviderSample02](./accessdbprovidersample02.md) in dit voorbeeld laat zien hoe u overschrijven de [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) en [ System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methoden voor de ondersteuning van aanroepen naar de `New-PSDrive` en `Remove-PSDrive` cmdlets. De providerklasse in dit voorbeeld is afgeleid van de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klasse.

[AccessDBProviderSample03](./accessdbprovidersample03.md) in dit voorbeeld laat zien hoe u overschrijven de [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) en [ System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methoden voor de ondersteuning van aanroepen naar de `Get-Item` en `Set-Item` cmdlets. De providerklasse in dit voorbeeld is afgeleid van de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasse.

[AccessDBProviderSample04](./accessdbprovidersample04.md) in dit voorbeeld laat zien hoe u containermethoden ter ondersteuning van aanroepen naar overschrijven de `Copy-Item`, `Get-ChildItem`, `New-Item`, en `Remove-Item` cmdlets. Deze methoden moeten worden uitgevoerd wanneer het gegevensarchief bevat items die containers zijn. Een container is een groep van onderliggende items onder een gemeenschappelijk bovenliggend item. De providerklasse in dit voorbeeld is afgeleid van de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasse.

[AccessDBProviderSample05](./accessdbprovidersample05.md) in dit voorbeeld laat zien hoe u containermethoden ter ondersteuning van aanroepen naar overschrijven de `Move-Item` en `Join-Path` cmdlets. Deze methoden moeten worden uitgevoerd wanneer de gebruiker nodig heeft om items in een container te verplaatsen en als het gegevensarchief geneste containers bevat. De providerklasse in dit voorbeeld is afgeleid van de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasse.

[AccessDBProviderSample06](./accessdbprovidersample06.md) in dit voorbeeld laat zien hoe u inhoud methoden ter ondersteuning van aanroepen naar overschrijven de `Clear-Content`, `Get-Content`, en `Set-Content` cmdlets. Deze methoden moeten worden uitgevoerd wanneer de gebruiker nodig heeft voor het beheren van de inhoud van de items in het gegevensarchief. De providerklasse in dit voorbeeld is afgeleid van de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasse en implementeert de [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Provider](./writing-a-windows-powershell-provider.md)