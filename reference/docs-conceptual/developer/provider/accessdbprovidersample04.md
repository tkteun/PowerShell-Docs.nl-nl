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
ms.openlocfilehash: 7096f8066568c214a5902f6943a2c093932d3b56
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356859"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="392d5-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="392d5-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="392d5-103">In dit voor beeld ziet u hoe u container methoden overschrijft ter ondersteuning van aanroepen naar de `Copy-Item`, `Get-ChildItem`, `New-Item` en `Remove-Item`-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="392d5-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="392d5-104">Deze methoden moeten worden geïmplementeerd wanneer het gegevens archief items bevat die containers zijn.</span><span class="sxs-lookup"><span data-stu-id="392d5-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="392d5-105">Een container is een groep onderliggende items onder een gemeen schappelijk bovenliggend item.</span><span class="sxs-lookup"><span data-stu-id="392d5-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="392d5-106">De provider klasse in dit voor beeld is afgeleid van de klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="392d5-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="392d5-107">Laat zien</span><span class="sxs-lookup"><span data-stu-id="392d5-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="392d5-108">Uw provider klasse wordt hoogstwaarschijnlijk afgeleid van [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="392d5-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="392d5-109">In dit voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="392d5-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="392d5-110">Het kenmerk `CmdletProvider` declareren.</span><span class="sxs-lookup"><span data-stu-id="392d5-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="392d5-111">Een provider klasse definiëren die is afgeleid van de klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="392d5-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="392d5-112">De methode [System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) wordt overschreven om het gedrag van de cmdlet `Copy-Item` te wijzigen, waarmee de gebruiker items van de ene locatie naar de andere kan kopiëren.</span><span class="sxs-lookup"><span data-stu-id="392d5-112">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="392d5-113">(In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters toevoegt aan de `Copy-Item`-cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="392d5-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="392d5-114">De methode [System. Management. Automation. provider. Containercmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) wordt overschreven om het gedrag van de cmdlet Get-ChildItems te wijzigen, waarmee de gebruiker de onderliggende items van het bovenliggende item kan ophalen.</span><span class="sxs-lookup"><span data-stu-id="392d5-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="392d5-115">(In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters toevoegt aan de cmdlet Get-ChildItems.)</span><span class="sxs-lookup"><span data-stu-id="392d5-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="392d5-116">De methode [System. Management. Automation. provider. Containercmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) wordt overschreven om het gedrag van de cmdlet Get-ChildItems te wijzigen wanneer de para meter `Name` van de cmdlet is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="392d5-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="392d5-117">De methode [System. Management. Automation. provider. Containercmdletprovider. NewItem mag \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) wordt overschreven om het gedrag van de cmdlet `New-Item` te wijzigen, waardoor de gebruiker items kan toevoegen aan het gegevens archief.</span><span class="sxs-lookup"><span data-stu-id="392d5-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="392d5-118">(In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters toevoegt aan de `New-Item`-cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="392d5-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="392d5-119">De methode [System. Management. Automation. provider. Containercmdletprovider. RemoveItem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) wordt overschreven om het gedrag van de cmdlet `Remove-Item` te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="392d5-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="392d5-120">(In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters toevoegt aan de `Remove-Item`-cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="392d5-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="392d5-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="392d5-121">Example</span></span>

<span data-ttu-id="392d5-122">In dit voor beeld ziet u hoe u de methoden overschrijft die nodig zijn voor het kopiëren, maken en verwijderen van items, evenals methoden voor het ophalen van de onderliggende items van een bovenliggend item.</span><span class="sxs-lookup"><span data-stu-id="392d5-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="392d5-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="392d5-123">See Also</span></span>

[<span data-ttu-id="392d5-124">System. Management. Automation. provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="392d5-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="392d5-125">System. Management. Automation. provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="392d5-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="392d5-126">System. Management. Automation. provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="392d5-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="392d5-127">Uw Windows Power shell-provider ontwerpen</span><span class="sxs-lookup"><span data-stu-id="392d5-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
