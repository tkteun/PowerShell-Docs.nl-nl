---
title: AccessDBProviderSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aaf9351e-157f-4d48-8b8f-1fd64855b682
caps.latest.revision: 10
ms.openlocfilehash: 219f8c2367939d16da928ede789843669b4451c6
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633410"
---
# <a name="accessdbprovidersample02"></a><span data-ttu-id="05202-102">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="05202-102">AccessDBProviderSample02</span></span>

<span data-ttu-id="05202-103">In dit voor beeld ziet u hoe u de methoden [System. Management. Automation. provider. Drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) en [System. Management. Automation. provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) overschrijft om aanroepen naar de `New-PSDrive` cmdlets en te ondersteunen `Remove-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="05202-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span> <span data-ttu-id="05202-104">De provider klasse in dit voor beeld is afgeleid van de klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="05202-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="05202-105">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="05202-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="05202-106">Uw provider klasse is hoogstwaarschijnlijk afgeleid van een van de volgende klassen en implementeert mogelijk andere provider interfaces:</span><span class="sxs-lookup"><span data-stu-id="05202-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="05202-107">Klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="05202-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="05202-108">Zie [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="05202-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="05202-109">Klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="05202-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="05202-110">Zie [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="05202-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="05202-111">Klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="05202-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="05202-112">Zie [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="05202-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="05202-113">Zie [uw Windows Power shell-provider ontwerpen](./provider-types.md)voor meer informatie over het kiezen van welke provider klasse moet worden afgeleid op basis van provider functies.</span><span class="sxs-lookup"><span data-stu-id="05202-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="05202-114">In dit voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="05202-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="05202-115">Declareer het `CmdletProvider` kenmerk.</span><span class="sxs-lookup"><span data-stu-id="05202-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="05202-116">Een provider klasse definiëren die stations uit de klasse [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="05202-116">Defining a provider class that drives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

- <span data-ttu-id="05202-117">De methode [System. Management. Automation. provider. Drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) wordt overschreven ter ondersteuning van het maken van nieuwe stations.</span><span class="sxs-lookup"><span data-stu-id="05202-117">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to support creating new drives.</span></span> <span data-ttu-id="05202-118">(In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters aan de cmdlet kunt toevoegen `New-PSDrive` .)</span><span class="sxs-lookup"><span data-stu-id="05202-118">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="05202-119">De methode [System. Management. Automation. provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) wordt overschreven om het verwijderen van bestaande stations te ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="05202-119">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

## <a name="example"></a><span data-ttu-id="05202-120">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="05202-120">Example</span></span>

<span data-ttu-id="05202-121">In dit voor beeld ziet u hoe u de methoden [System. Management. Automation. provider. Drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) en [System. Management. Automation. provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) overschrijft.</span><span class="sxs-lookup"><span data-stu-id="05202-121">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods.</span></span> <span data-ttu-id="05202-122">Wanneer de verbindings gegevens van een station worden gemaakt voor deze voorbeeld provider, worden deze opgeslagen in een- `AccessDBPsDriveInfo` object.</span><span class="sxs-lookup"><span data-stu-id="05202-122">For this sample provider, when a drive is created its connection information is stored in an `AccessDBPsDriveInfo` object.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a><span data-ttu-id="05202-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="05202-123">See Also</span></span>

[<span data-ttu-id="05202-124">System. Management. Automation. provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="05202-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="05202-125">System. Management. Automation. provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="05202-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="05202-126">System. Management. Automation. provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="05202-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="05202-127">Uw Windows PowerShell-provider ontwerpen</span><span class="sxs-lookup"><span data-stu-id="05202-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
