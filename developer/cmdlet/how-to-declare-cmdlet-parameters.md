---
title: Het Cmdlet-Parameters declareren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067908"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="ba72b-102">Cmdlet-parameters declareren</span><span class="sxs-lookup"><span data-stu-id="ba72b-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="ba72b-103">Deze voorbeelden laten zien hoe met de naam, positionele, vereist, optioneel declareren en verwissel de parameters.</span><span class="sxs-lookup"><span data-stu-id="ba72b-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="ba72b-104">Deze voorbeelden laten ook zien hoe een parameteralias definiëren.</span><span class="sxs-lookup"><span data-stu-id="ba72b-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="ba72b-105">Hoe u een benoemde Parameter declareren</span><span class="sxs-lookup"><span data-stu-id="ba72b-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="ba72b-106">Een openbare eigenschap definiëren, zoals wordt weergegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="ba72b-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="ba72b-107">Wanneer u de Parameter-kenmerk toevoegen, laat de `Position` sleutelwoord uit het kenmerk.</span><span class="sxs-lookup"><span data-stu-id="ba72b-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="ba72b-108">Zie voor meer informatie over het parameterkenmerk [kenmerk parameterdeclaratie](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ba72b-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="ba72b-109">Hoe u positionele Parameter declareren</span><span class="sxs-lookup"><span data-stu-id="ba72b-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="ba72b-110">Een openbare eigenschap definiëren, zoals wordt weergegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="ba72b-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="ba72b-111">Wanneer u de Parameter-kenmerk toevoegen, stelt de `Position` trefwoord op de positie van het argument.</span><span class="sxs-lookup"><span data-stu-id="ba72b-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="ba72b-112">Een waarde van 0 geeft aan dat de eerste positie.</span><span class="sxs-lookup"><span data-stu-id="ba72b-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="ba72b-113">Zie voor meer informatie over het parameterkenmerk [kenmerk parameterdeclaratie](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ba72b-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="ba72b-114">Hoe u een verplichte Parameter declareren</span><span class="sxs-lookup"><span data-stu-id="ba72b-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="ba72b-115">Een openbare eigenschap definiëren, zoals wordt weergegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="ba72b-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="ba72b-116">Wanneer u de Parameter-kenmerk toevoegen, stelt de `Mandatory` trefwoord `true`.</span><span class="sxs-lookup"><span data-stu-id="ba72b-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="ba72b-117">Zie voor meer informatie over het parameterkenmerk [kenmerk parameterdeclaratie](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ba72b-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="ba72b-118">Hoe u een optionele Parameter declareren</span><span class="sxs-lookup"><span data-stu-id="ba72b-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="ba72b-119">Een openbare eigenschap definiëren, zoals wordt weergegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="ba72b-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="ba72b-120">Wanneer u de Parameter-kenmerk toevoegen, laat de `Mandatory` trefwoord.</span><span class="sxs-lookup"><span data-stu-id="ba72b-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="ba72b-121">Hoe u een Switch-Parameter declareren</span><span class="sxs-lookup"><span data-stu-id="ba72b-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="ba72b-122">Een openbare eigenschap definiëren als type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), en vervolgens het parameterkenmerk declareren.</span><span class="sxs-lookup"><span data-stu-id="ba72b-122">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="ba72b-123">Zie voor meer informatie over het parameterkenmerk [kenmerk parameterdeclaratie](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ba72b-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="ba72b-124">Hoe u een Parameter met de aliassen declareren</span><span class="sxs-lookup"><span data-stu-id="ba72b-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="ba72b-125">Een openbare eigenschap definiëren, zoals wordt weergegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="ba72b-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="ba72b-126">Een Alias-kenmerk met een lijst met de aliassen voor de parameter toevoegen.</span><span class="sxs-lookup"><span data-stu-id="ba72b-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="ba72b-127">In dit voorbeeld worden drie aliassen zijn gedefinieerd voor dezelfde parameter.</span><span class="sxs-lookup"><span data-stu-id="ba72b-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="ba72b-128">De eerste alias bevat een snelkoppeling naar.</span><span class="sxs-lookup"><span data-stu-id="ba72b-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="ba72b-129">De tweede en derde aliassen opgeven namen die voor verschillende scenario's kunt u.</span><span class="sxs-lookup"><span data-stu-id="ba72b-129">The second and third aliases provide names you can use for different scenarios.</span></span>

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="ba72b-130">Zie voor meer informatie over het kenmerk Alias [Alias kenmerkdeclaratie](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="ba72b-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ba72b-131">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ba72b-131">See Also</span></span>

[<span data-ttu-id="ba72b-132">System.Management.Automation.SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="ba72b-132">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="ba72b-133">Kenmerk parameterdeclaratie</span><span class="sxs-lookup"><span data-stu-id="ba72b-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="ba72b-134">De declaratie van de alias-kenmerk</span><span class="sxs-lookup"><span data-stu-id="ba72b-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="ba72b-135">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ba72b-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
