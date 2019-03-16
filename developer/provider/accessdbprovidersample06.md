---
title: AccessDBProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055543"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="ed340-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="ed340-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="ed340-103">In dit voorbeeld laat zien hoe u inhoud methoden ter ondersteuning van aanroepen naar overschrijven de `Clear-Content`, `Get-Content`, en `Set-Content` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="ed340-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="ed340-104">Deze methoden moeten worden uitgevoerd wanneer de gebruiker nodig heeft voor het beheren van de inhoud van de items in het gegevensarchief.</span><span class="sxs-lookup"><span data-stu-id="ed340-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="ed340-105">De providerklasse in dit voorbeeld is afgeleid van de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasse en implementeert de [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="ed340-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ed340-106">Hier ziet u</span><span class="sxs-lookup"><span data-stu-id="ed340-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ed340-107">Uw providerklasse wordt waarschijnlijk zijn afgeleid van een van de volgende klassen en mogelijk andere provider-interfaces te implementeren:</span><span class="sxs-lookup"><span data-stu-id="ed340-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="ed340-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="ed340-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="ed340-109">Zie [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="ed340-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="ed340-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="ed340-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="ed340-111">Zie [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="ed340-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="ed340-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="ed340-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="ed340-113">Voor meer informatie over het kiezen van welke providerklasse afgeleid op basis van de functies van resourceproviders, raadpleeg dan [het ontwerpen van uw Windows PowerShell-Provider](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="ed340-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="ed340-114">In dit voorbeeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="ed340-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="ed340-115">Declareren de `CmdletProvider` kenmerk.</span><span class="sxs-lookup"><span data-stu-id="ed340-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="ed340-116">Het definiëren van een klasse in de provider die is afgeleid van de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasse en die verklaart de [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="ed340-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="ed340-117">Overschrijven de [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) methode voor het wijzigen van het gedrag van de `Clear-Content` cmdlet, zodat de gebruiker de inhoud uit een item te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="ed340-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="ed340-118">(In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `Clear-Content` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="ed340-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="ed340-119">Overschrijven de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) methode voor het wijzigen van het gedrag van de `Get-Content` cmdlet, zodat de gebruiker ophalen van de inhoud van een item.</span><span class="sxs-lookup"><span data-stu-id="ed340-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="ed340-120">(In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `Get-Content` cmdlet.).</span><span class="sxs-lookup"><span data-stu-id="ed340-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="ed340-121">Overschrijven de [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) methode voor het wijzigen van het gedrag van de `Set-Content` cmdlet, zodat de gebruiker de inhoud van een item bijwerken.</span><span class="sxs-lookup"><span data-stu-id="ed340-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="ed340-122">(In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `Set-Content` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="ed340-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="ed340-123">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ed340-123">Example</span></span>

<span data-ttu-id="ed340-124">Dit voorbeeld laat zien hoe u het overschrijven van de methoden die nodig zijn om te wissen, ophalen en de inhoud van items in een Microsoft Access-gegevens instellen.</span><span class="sxs-lookup"><span data-stu-id="ed340-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="ed340-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ed340-125">See Also</span></span>

[<span data-ttu-id="ed340-126">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="ed340-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="ed340-127">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="ed340-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="ed340-128">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="ed340-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="ed340-129">Het ontwerpen van uw Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="ed340-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)