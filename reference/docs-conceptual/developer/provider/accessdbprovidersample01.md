---
title: AccessDBProviderSample01 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 50ec218e8d0fe6b2be5c8ac00956f72c6723f84a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786914"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="c48a3-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="c48a3-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="c48a3-103">In dit voor beeld ziet u hoe u een provider klasse declareert die rechtstreeks is afgeleid van de klasse [System. Management. Automation. provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="c48a3-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="c48a3-104">Deze is alleen opgenomen voor volledigheid.</span><span class="sxs-lookup"><span data-stu-id="c48a3-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="c48a3-105">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="c48a3-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c48a3-106">Uw provider klasse is hoogstwaarschijnlijk afgeleid van een van de volgende klassen en implementeert mogelijk andere provider interfaces:</span><span class="sxs-lookup"><span data-stu-id="c48a3-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="c48a3-107">Klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="c48a3-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="c48a3-108">Zie [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="c48a3-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="c48a3-109">Klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="c48a3-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="c48a3-110">Zie [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="c48a3-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="c48a3-111">Klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="c48a3-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="c48a3-112">Zie [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="c48a3-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="c48a3-113">Zie [uw Windows Power shell-provider ontwerpen](./provider-types.md)voor meer informatie over het kiezen van welke provider klasse moet worden afgeleid op basis van provider functies.</span><span class="sxs-lookup"><span data-stu-id="c48a3-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="c48a3-114">In dit voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="c48a3-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="c48a3-115">Declareer het `CmdletProvider` kenmerk.</span><span class="sxs-lookup"><span data-stu-id="c48a3-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="c48a3-116">Een provider klasse definiëren die rechtstreeks is afgeleid van de klasse [System. Management. Automation. provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="c48a3-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="c48a3-117">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c48a3-117">Example</span></span>

<span data-ttu-id="c48a3-118">In dit voor beeld ziet u hoe u een provider klasse definieert en hoe u het kenmerk declareert `CmdletProvider` .</span><span class="sxs-lookup"><span data-stu-id="c48a3-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a><span data-ttu-id="c48a3-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c48a3-119">See Also</span></span>

[<span data-ttu-id="c48a3-120">System. Management. Automation. provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="c48a3-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="c48a3-121">System. Management. Automation. provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="c48a3-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="c48a3-122">System. Management. Automation. provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="c48a3-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="c48a3-123">Uw Windows PowerShell-provider ontwerpen</span><span class="sxs-lookup"><span data-stu-id="c48a3-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
