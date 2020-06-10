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
# <a name="accessdbprovidersample05"></a><span data-ttu-id="ff9cc-102">AccessDBProviderSample05</span><span class="sxs-lookup"><span data-stu-id="ff9cc-102">AccessDBProviderSample05</span></span>

<span data-ttu-id="ff9cc-103">In dit voor beeld ziet u hoe u container methoden overschrijft ter ondersteuning van aanroepen naar de- `Move-Item` en- `Join-Path` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-103">This sample shows how to overwrite container methods to support calls to the `Move-Item` and `Join-Path` cmdlets.</span></span> <span data-ttu-id="ff9cc-104">Deze methoden moeten worden geïmplementeerd wanneer de gebruiker items in een container moet verplaatsen en als het gegevens archief geneste containers bevat.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-104">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span> <span data-ttu-id="ff9cc-105">De provider klasse in dit voor beeld is afgeleid van de klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="ff9cc-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ff9cc-106">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="ff9cc-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ff9cc-107">Uw provider klasse is hoogstwaarschijnlijk afgeleid van een van de volgende klassen en implementeert mogelijk andere provider interfaces:</span><span class="sxs-lookup"><span data-stu-id="ff9cc-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="ff9cc-108">Klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="ff9cc-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="ff9cc-109">Zie [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="ff9cc-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="ff9cc-110">Klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="ff9cc-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="ff9cc-111">Zie [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="ff9cc-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="ff9cc-112">Klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="ff9cc-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="ff9cc-113">Zie [uw Windows Power shell-provider ontwerpen](./provider-types.md)voor meer informatie over het kiezen van welke provider klasse moet worden afgeleid op basis van provider functies.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="ff9cc-114">In dit voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="ff9cc-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="ff9cc-115">Declareer het `CmdletProvider` kenmerk.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="ff9cc-116">Een provider klasse definiëren die is afgeleid van de klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="ff9cc-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

- <span data-ttu-id="ff9cc-117">De methode [System. Management. Automation. provider. Navigationcmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) wordt overschreven om het gedrag van de cmdlet te wijzigen `Move-Item` , waardoor de gebruiker items van de ene locatie naar de andere kan verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-117">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method to change the behavior of the `Move-Item` cmdlet, allowing the user to move items from one location to another.</span></span> <span data-ttu-id="ff9cc-118">(In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters aan de cmdlet kunt toevoegen `Move-Item` .)</span><span class="sxs-lookup"><span data-stu-id="ff9cc-118">(This sample does not show how to add dynamic parameters to the `Move-Item` cmdlet.)</span></span>

- <span data-ttu-id="ff9cc-119">De methode [System. Management. Automation. provider. Navigationcmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) wordt overschreven om het gedrag van de cmdlet te wijzigen `Join-Path` .</span><span class="sxs-lookup"><span data-stu-id="ff9cc-119">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method to change the behavior of the `Join-Path` cmdlet.</span></span>

- <span data-ttu-id="ff9cc-120">De methode [System. Management. Automation. provider. Navigationcmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-120">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method.</span></span>

- <span data-ttu-id="ff9cc-121">De methode [System. Management. Automation. provider. Navigationcmdletprovider. Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-121">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method.</span></span>

- <span data-ttu-id="ff9cc-122">De methode [System. Management. Automation. provider. Navigationcmdletprovider. Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-122">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method.</span></span>

- <span data-ttu-id="ff9cc-123">De methode [System. Management. Automation. provider. Navigationcmdletprovider. Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-123">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method.</span></span>

## <a name="example"></a><span data-ttu-id="ff9cc-124">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ff9cc-124">Example</span></span>

<span data-ttu-id="ff9cc-125">In dit voor beeld ziet u hoe u de methoden overschrijft die nodig zijn om items in een micro soft Access-Data Base te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="ff9cc-125">This sample shows how to overwrite the methods needed to move items in a Microsoft Access data base.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="11-1960":::

## <a name="see-also"></a><span data-ttu-id="ff9cc-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ff9cc-126">See Also</span></span>

[<span data-ttu-id="ff9cc-127">System. Management. Automation. provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="ff9cc-127">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="ff9cc-128">System. Management. Automation. provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="ff9cc-128">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="ff9cc-129">System. Management. Automation. provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="ff9cc-129">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="ff9cc-130">Uw Windows PowerShell-provider ontwerpen</span><span class="sxs-lookup"><span data-stu-id="ff9cc-130">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
