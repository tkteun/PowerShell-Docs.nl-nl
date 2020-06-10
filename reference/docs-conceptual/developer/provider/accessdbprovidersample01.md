---
title: AccessDBProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: 5d738de60bc47d000377779ee4e564bff4ad31ad
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633427"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="21a2b-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="21a2b-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="21a2b-103">In dit voor beeld ziet u hoe u een provider klasse declareert die rechtstreeks is afgeleid van de klasse [System. Management. Automation. provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="21a2b-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="21a2b-104">Deze is alleen opgenomen voor volledigheid.</span><span class="sxs-lookup"><span data-stu-id="21a2b-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="21a2b-105">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="21a2b-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="21a2b-106">Uw provider klasse is hoogstwaarschijnlijk afgeleid van een van de volgende klassen en implementeert mogelijk andere provider interfaces:</span><span class="sxs-lookup"><span data-stu-id="21a2b-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="21a2b-107">Klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="21a2b-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="21a2b-108">Zie [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="21a2b-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="21a2b-109">Klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="21a2b-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="21a2b-110">Zie [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="21a2b-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="21a2b-111">Klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="21a2b-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="21a2b-112">Zie [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="21a2b-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="21a2b-113">Zie [uw Windows Power shell-provider ontwerpen](./provider-types.md)voor meer informatie over het kiezen van welke provider klasse moet worden afgeleid op basis van provider functies.</span><span class="sxs-lookup"><span data-stu-id="21a2b-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="21a2b-114">In dit voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="21a2b-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="21a2b-115">Declareer het `CmdletProvider` kenmerk.</span><span class="sxs-lookup"><span data-stu-id="21a2b-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="21a2b-116">Een provider klasse definiëren die rechtstreeks is afgeleid van de klasse [System. Management. Automation. provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="21a2b-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="21a2b-117">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="21a2b-117">Example</span></span>

<span data-ttu-id="21a2b-118">In dit voor beeld ziet u hoe u een provider klasse definieert en hoe u het kenmerk declareert `CmdletProvider` .</span><span class="sxs-lookup"><span data-stu-id="21a2b-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a><span data-ttu-id="21a2b-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="21a2b-119">See Also</span></span>

[<span data-ttu-id="21a2b-120">System. Management. Automation. provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="21a2b-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="21a2b-121">System. Management. Automation. provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="21a2b-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="21a2b-122">System. Management. Automation. provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="21a2b-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="21a2b-123">Uw Windows PowerShell-provider ontwerpen</span><span class="sxs-lookup"><span data-stu-id="21a2b-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
