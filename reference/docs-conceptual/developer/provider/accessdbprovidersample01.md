---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample01
description: AccessDBProviderSample01
ms.openlocfilehash: 8bdfa3ad492935a22ce06846294c02961cab2c65
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653756"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="b97e6-103">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="b97e6-103">AccessDBProviderSample01</span></span>

<span data-ttu-id="b97e6-104">In dit voor beeld ziet u hoe u een provider klasse declareert die rechtstreeks is afgeleid van de klasse [System. Management. Automation. provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b97e6-104">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="b97e6-105">Deze is alleen opgenomen voor volledigheid.</span><span class="sxs-lookup"><span data-stu-id="b97e6-105">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b97e6-106">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="b97e6-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b97e6-107">Uw provider klasse is hoogstwaarschijnlijk afgeleid van een van de volgende klassen en implementeert mogelijk andere provider interfaces:</span><span class="sxs-lookup"><span data-stu-id="b97e6-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="b97e6-108">Klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b97e6-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="b97e6-109">Zie [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="b97e6-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="b97e6-110">Klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b97e6-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="b97e6-111">Zie [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="b97e6-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="b97e6-112">Klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b97e6-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="b97e6-113">Zie [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="b97e6-113">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="b97e6-114">Zie [uw Windows Power shell-provider ontwerpen](./provider-types.md)voor meer informatie over het kiezen van welke provider klasse moet worden afgeleid op basis van provider functies.</span><span class="sxs-lookup"><span data-stu-id="b97e6-114">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="b97e6-115">In dit voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="b97e6-115">This sample demonstrates the following:</span></span>

- <span data-ttu-id="b97e6-116">Declareer het `CmdletProvider` kenmerk.</span><span class="sxs-lookup"><span data-stu-id="b97e6-116">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="b97e6-117">Een provider klasse definiëren die rechtstreeks is afgeleid van de klasse [System. Management. Automation. provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b97e6-117">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="b97e6-118">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="b97e6-118">Example</span></span>

<span data-ttu-id="b97e6-119">In dit voor beeld ziet u hoe u een provider klasse definieert en hoe u het kenmerk declareert `CmdletProvider` .</span><span class="sxs-lookup"><span data-stu-id="b97e6-119">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a><span data-ttu-id="b97e6-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b97e6-120">See Also</span></span>

[<span data-ttu-id="b97e6-121">System. Management. Automation. provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="b97e6-121">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="b97e6-122">System. Management. Automation. provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="b97e6-122">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="b97e6-123">System. Management. Automation. provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="b97e6-123">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="b97e6-124">Uw Windows PowerShell-provider ontwerpen</span><span class="sxs-lookup"><span data-stu-id="b97e6-124">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
