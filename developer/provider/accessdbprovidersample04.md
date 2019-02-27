---
title: AccessDBProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: fd013384a4b588bcdb397d7771425fe5c031c48f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847297"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="45f0d-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="45f0d-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="45f0d-103">In dit voorbeeld laat zien hoe u containermethoden ter ondersteuning van aanroepen naar overschrijven de `Copy-Item`, `Get-ChildItem`, `New-Item`, en `Remove-Item` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="45f0d-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="45f0d-104">Deze methoden moeten worden uitgevoerd wanneer het gegevensarchief bevat items die containers zijn.</span><span class="sxs-lookup"><span data-stu-id="45f0d-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="45f0d-105">Een container is een groep van onderliggende items onder een gemeenschappelijk bovenliggend item.</span><span class="sxs-lookup"><span data-stu-id="45f0d-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="45f0d-106">De providerklasse in dit voorbeeld is afgeleid van de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasse.</span><span class="sxs-lookup"><span data-stu-id="45f0d-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="45f0d-107">Hier ziet u</span><span class="sxs-lookup"><span data-stu-id="45f0d-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45f0d-108">Uw providerklasse waarschijnlijk wordt afgeleid van de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="45f0d-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="45f0d-109">In dit voorbeeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="45f0d-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="45f0d-110">Declareren de `CmdletProvider` kenmerk.</span><span class="sxs-lookup"><span data-stu-id="45f0d-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="45f0d-111">Het definiëren van een klasse in de provider die is afgeleid van de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klasse.</span><span class="sxs-lookup"><span data-stu-id="45f0d-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="45f0d-112">Overschrijven de [System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) methode voor het wijzigen van het gedrag van de `Copy-Item` cmdlet waarmee de gebruiker om items te kopiëren van de ene locatie naar een andere.</span><span class="sxs-lookup"><span data-stu-id="45f0d-112">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="45f0d-113">(In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `Copy-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="45f0d-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="45f0d-114">Overschrijven de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) methode om het gedrag van de cmdlet Get-ChildItems, waarmee de gebruiker om op te halen van de onderliggende items van het bovenliggende item te wijzigen .</span><span class="sxs-lookup"><span data-stu-id="45f0d-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="45f0d-115">(In dit voorbeeld wordt dynamische parameters toevoegen aan de cmdlet Get-ChildItems niet weergegeven.)</span><span class="sxs-lookup"><span data-stu-id="45f0d-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="45f0d-116">Overschrijven de [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) methode om het gedrag van de cmdlet Get-ChildItems te wijzigen wanneer de `Name` parameter van de cmdlet is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="45f0d-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="45f0d-117">Overschrijven de [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) methode voor het wijzigen van het gedrag van de `New-Item` cmdlet, waarmee de gebruiker items toevoegen aan het gegevensarchief.</span><span class="sxs-lookup"><span data-stu-id="45f0d-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="45f0d-118">(In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `New-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="45f0d-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="45f0d-119">Overschrijven de [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) methode voor het wijzigen van het gedrag van de `Remove-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="45f0d-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="45f0d-120">(In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `Remove-Item` cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="45f0d-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="45f0d-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="45f0d-121">Example</span></span>

<span data-ttu-id="45f0d-122">In dit voorbeeld laat zien hoe de methoden die nodig zijn om te kopiëren, maken en verwijderen van items, evenals de methoden voor het ophalen van de onderliggende items van een bovenliggend item overschrijven.</span><span class="sxs-lookup"><span data-stu-id="45f0d-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="45f0d-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="45f0d-123">See Also</span></span>

[<span data-ttu-id="45f0d-124">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="45f0d-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="45f0d-125">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="45f0d-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="45f0d-126">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="45f0d-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="45f0d-127">Het ontwerpen van uw Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="45f0d-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)