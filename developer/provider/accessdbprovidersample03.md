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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849194"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="26de0-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="26de0-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="26de0-103">In dit voorbeeld laat zien hoe u overschrijven de [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) en [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methoden voor de ondersteuning van aanroepen naar de `Get-Item` en `Set-Item` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="26de0-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="26de0-104">De providerklasse in dit voorbeeld is afgeleid van de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasse.</span><span class="sxs-lookup"><span data-stu-id="26de0-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="26de0-105">Hier ziet u</span><span class="sxs-lookup"><span data-stu-id="26de0-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26de0-106">Uw providerklasse wordt waarschijnlijk zijn afgeleid van een van de volgende klassen en mogelijk andere provider-interfaces te implementeren:</span><span class="sxs-lookup"><span data-stu-id="26de0-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="26de0-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="26de0-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="26de0-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="26de0-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="26de0-109">Zie [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="26de0-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="26de0-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="26de0-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="26de0-111">Zie [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="26de0-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="26de0-112">Voor meer informatie over het kiezen van welke providerklasse afgeleid op basis van de functies van resourceproviders, raadpleeg dan [het ontwerpen van uw Windows PowerShell-Provider](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="26de0-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="26de0-113">In dit voorbeeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="26de0-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="26de0-114">Declareren de `CmdletProvider` kenmerk.</span><span class="sxs-lookup"><span data-stu-id="26de0-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="26de0-115">Het definiëren van een klasse in de provider die is afgeleid van de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) klasse.</span><span class="sxs-lookup"><span data-stu-id="26de0-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="26de0-116">Overschrijven de [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) methode voor het wijzigen van het gedrag van de `New-PSDrive` cmdlet, zodat de gebruiker om nieuwe stations te maken.</span><span class="sxs-lookup"><span data-stu-id="26de0-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="26de0-117">(In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `New-PSDrive` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="26de0-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="26de0-118">Overschrijven de [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methode voor het verwijderen van bestaande stations ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="26de0-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="26de0-119">Overschrijven de [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) methode voor het wijzigen van het gedrag van de `Get-Item` cmdlet, zodat de gebruiker om items te halen uit het gegevensarchief.</span><span class="sxs-lookup"><span data-stu-id="26de0-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="26de0-120">(In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `Get-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="26de0-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="26de0-121">Overschrijven de [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methode voor het wijzigen van het gedrag van de `Set-Item` cmdlet, zodat de gebruiker om bij te werken van de items in het gegevensarchief.</span><span class="sxs-lookup"><span data-stu-id="26de0-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="26de0-122">(In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `Get-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="26de0-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="26de0-123">Overschrijven de [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) methode voor het wijzigen van het gedrag van de `Test-Path` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="26de0-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="26de0-124">(In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `Test-Path` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="26de0-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="26de0-125">Overschrijven de [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) methode om te bepalen of het opgegeven pad geldig is.</span><span class="sxs-lookup"><span data-stu-id="26de0-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="26de0-126">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="26de0-126">Example</span></span>

<span data-ttu-id="26de0-127">In dit voorbeeld laat zien hoe de methoden die nodig zijn voor het ophalen en instellen van items in een Microsoft Access-gegevens base overschrijven.</span><span class="sxs-lookup"><span data-stu-id="26de0-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="26de0-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="26de0-128">See Also</span></span>

[<span data-ttu-id="26de0-129">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="26de0-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="26de0-130">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="26de0-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="26de0-131">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="26de0-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="26de0-132">Het ontwerpen van uw Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="26de0-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)