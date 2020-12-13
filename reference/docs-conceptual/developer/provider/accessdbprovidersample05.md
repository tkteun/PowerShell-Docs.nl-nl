---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample05
description: AccessDBProviderSample05
ms.openlocfilehash: ad273720ded0b200530f4f81482d01a8fbb82aa3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92656913"
---
# <a name="accessdbprovidersample05"></a><span data-ttu-id="0501d-103">AccessDBProviderSample05</span><span class="sxs-lookup"><span data-stu-id="0501d-103">AccessDBProviderSample05</span></span>

<span data-ttu-id="0501d-104">In dit voor beeld ziet u hoe u container methoden overschrijft ter ondersteuning van aanroepen naar de- `Move-Item` en- `Join-Path` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="0501d-104">This sample shows how to overwrite container methods to support calls to the `Move-Item` and `Join-Path` cmdlets.</span></span> <span data-ttu-id="0501d-105">Deze methoden moeten worden geïmplementeerd wanneer de gebruiker items in een container moet verplaatsen en als het gegevens archief geneste containers bevat.</span><span class="sxs-lookup"><span data-stu-id="0501d-105">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span> <span data-ttu-id="0501d-106">De provider klasse in dit voor beeld is afgeleid van de klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="0501d-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="0501d-107">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="0501d-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0501d-108">Uw provider klasse is hoogstwaarschijnlijk afgeleid van een van de volgende klassen en implementeert mogelijk andere provider interfaces:</span><span class="sxs-lookup"><span data-stu-id="0501d-108">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="0501d-109">Klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="0501d-109">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="0501d-110">Zie [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="0501d-110">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="0501d-111">Klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="0501d-111">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="0501d-112">Zie [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="0501d-112">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="0501d-113">Klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="0501d-113">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="0501d-114">Zie [uw Windows Power shell-provider ontwerpen](./provider-types.md)voor meer informatie over het kiezen van welke provider klasse moet worden afgeleid op basis van provider functies.</span><span class="sxs-lookup"><span data-stu-id="0501d-114">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="0501d-115">In dit voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="0501d-115">This sample demonstrates the following:</span></span>

- <span data-ttu-id="0501d-116">Declareer het `CmdletProvider` kenmerk.</span><span class="sxs-lookup"><span data-stu-id="0501d-116">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="0501d-117">Een provider klasse definiëren die is afgeleid van de klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="0501d-117">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

- <span data-ttu-id="0501d-118">De methode [System. Management. Automation. provider. Navigationcmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) wordt overschreven om het gedrag van de cmdlet te wijzigen `Move-Item` , waardoor de gebruiker items van de ene locatie naar de andere kan verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="0501d-118">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method to change the behavior of the `Move-Item` cmdlet, allowing the user to move items from one location to another.</span></span> <span data-ttu-id="0501d-119">(In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters aan de cmdlet kunt toevoegen `Move-Item` .)</span><span class="sxs-lookup"><span data-stu-id="0501d-119">(This sample does not show how to add dynamic parameters to the `Move-Item` cmdlet.)</span></span>

- <span data-ttu-id="0501d-120">De methode [System. Management. Automation. provider. Navigationcmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) wordt overschreven om het gedrag van de cmdlet te wijzigen `Join-Path` .</span><span class="sxs-lookup"><span data-stu-id="0501d-120">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method to change the behavior of the `Join-Path` cmdlet.</span></span>

- <span data-ttu-id="0501d-121">De methode [System. Management. Automation. provider. Navigationcmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="0501d-121">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method.</span></span>

- <span data-ttu-id="0501d-122">De methode [System. Management. Automation. provider. Navigationcmdletprovider. Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="0501d-122">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method.</span></span>

- <span data-ttu-id="0501d-123">De methode [System. Management. Automation. provider. Navigationcmdletprovider. Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="0501d-123">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method.</span></span>

- <span data-ttu-id="0501d-124">De methode [System. Management. Automation. provider. Navigationcmdletprovider. Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="0501d-124">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method.</span></span>

## <a name="example"></a><span data-ttu-id="0501d-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="0501d-125">Example</span></span>

<span data-ttu-id="0501d-126">In dit voor beeld ziet u hoe u de methoden overschrijft die nodig zijn om items in een micro soft Access-Data Base te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="0501d-126">This sample shows how to overwrite the methods needed to move items in a Microsoft Access data base.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="11-1960":::

## <a name="see-also"></a><span data-ttu-id="0501d-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0501d-127">See Also</span></span>

[<span data-ttu-id="0501d-128">System. Management. Automation. provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="0501d-128">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="0501d-129">System. Management. Automation. provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="0501d-129">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="0501d-130">System. Management. Automation. provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="0501d-130">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="0501d-131">Uw Windows PowerShell-provider ontwerpen</span><span class="sxs-lookup"><span data-stu-id="0501d-131">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
