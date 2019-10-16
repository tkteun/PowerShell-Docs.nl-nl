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
ms.openlocfilehash: 9c00ec6de987729fec42dc57245a949d11e31f4b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356852"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="7ef6e-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="7ef6e-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="7ef6e-103">In dit voor beeld ziet u hoe inhouds methoden worden overschreven om aanroepen naar de `Clear-Content`, `Get-Content`-en `Set-Content`-cmdlets te ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="7ef6e-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="7ef6e-104">Deze methoden moeten worden geïmplementeerd wanneer de gebruiker de inhoud van de items in het gegevens archief moet beheren.</span><span class="sxs-lookup"><span data-stu-id="7ef6e-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="7ef6e-105">De provider klasse in dit voor beeld is afgeleid van de klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) en implementeert de interface [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="7ef6e-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="7ef6e-106">Laat zien</span><span class="sxs-lookup"><span data-stu-id="7ef6e-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ef6e-107">Uw provider klasse is hoogstwaarschijnlijk afgeleid van een van de volgende klassen en implementeert mogelijk andere provider interfaces:</span><span class="sxs-lookup"><span data-stu-id="7ef6e-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="7ef6e-108">Klasse [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="7ef6e-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="7ef6e-109">Zie [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="7ef6e-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="7ef6e-110">Klasse [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="7ef6e-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="7ef6e-111">Zie [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="7ef6e-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="7ef6e-112">Klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="7ef6e-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="7ef6e-113">Zie [uw Windows Power shell-provider ontwerpen](./provider-types.md)voor meer informatie over het kiezen van welke provider klasse moet worden afgeleid op basis van provider functies.</span><span class="sxs-lookup"><span data-stu-id="7ef6e-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="7ef6e-114">In dit voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="7ef6e-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="7ef6e-115">Het kenmerk `CmdletProvider` declareren.</span><span class="sxs-lookup"><span data-stu-id="7ef6e-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="7ef6e-116">Het definiëren van een provider klasse die is afgeleid van de klasse [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) en die de interface [System. Management. Automation. provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) declareert.</span><span class="sxs-lookup"><span data-stu-id="7ef6e-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="7ef6e-117">De methode [System. Management. Automation. provider. Icontentcmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) wordt overschreven om het gedrag van de cmdlet `Clear-Content` te wijzigen, waardoor de gebruiker de inhoud van een item kan verwijderen.</span><span class="sxs-lookup"><span data-stu-id="7ef6e-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="7ef6e-118">(In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters toevoegt aan de `Clear-Content`-cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="7ef6e-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="7ef6e-119">De methode [System. Management. Automation. provider. Icontentcmdletprovider. Getcontentreader \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) wordt overschreven om het gedrag van de cmdlet `Get-Content` te wijzigen, waardoor de gebruiker de inhoud van een item kan ophalen.</span><span class="sxs-lookup"><span data-stu-id="7ef6e-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="7ef6e-120">(In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters toevoegt aan de `Get-Content`-cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="7ef6e-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="7ef6e-121">Het overschrijven van de methode [micro soft. Power shell. commands. Filesystemprovider. Getcontentwriter \*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) om het gedrag van de cmdlet `Set-Content` te wijzigen, waardoor de gebruiker de inhoud van een item kan bijwerken.</span><span class="sxs-lookup"><span data-stu-id="7ef6e-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="7ef6e-122">(In dit voor beeld wordt niet weer gegeven hoe u dynamische para meters toevoegt aan de `Set-Content`-cmdlet.)</span><span class="sxs-lookup"><span data-stu-id="7ef6e-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="7ef6e-123">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="7ef6e-123">Example</span></span>

<span data-ttu-id="7ef6e-124">In dit voor beeld ziet u hoe u de methoden overschrijft die nodig zijn om de inhoud van items in een micro soft Access-Data Base te wissen, op te halen en in te stellen.</span><span class="sxs-lookup"><span data-stu-id="7ef6e-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="7ef6e-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7ef6e-125">See Also</span></span>

[<span data-ttu-id="7ef6e-126">System. Management. Automation. provider. Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="7ef6e-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="7ef6e-127">System. Management. Automation. provider. Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="7ef6e-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="7ef6e-128">System. Management. Automation. provider. Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="7ef6e-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="7ef6e-129">Uw Windows Power shell-provider ontwerpen</span><span class="sxs-lookup"><span data-stu-id="7ef6e-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
