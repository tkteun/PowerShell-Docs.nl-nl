---
title: Cmdlet-para meters declareren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356397"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="d7c04-102">Cmdlet-parameters declareren</span><span class="sxs-lookup"><span data-stu-id="d7c04-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="d7c04-103">In deze voor beelden ziet u hoe u para meters met de naam, positioneel, required, optional en switch declareert.</span><span class="sxs-lookup"><span data-stu-id="d7c04-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="d7c04-104">In deze voor beelden ziet u ook hoe u een parameter alias definieert.</span><span class="sxs-lookup"><span data-stu-id="d7c04-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="d7c04-105">Een benoemde para meter declareren</span><span class="sxs-lookup"><span data-stu-id="d7c04-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="d7c04-106">Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7c04-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="d7c04-107">Wanneer u het parameter kenmerk toevoegt, laat u het sleutel woord `Position` weg van het kenmerk.</span><span class="sxs-lookup"><span data-stu-id="d7c04-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="d7c04-108">Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over het parameter kenmerk.</span><span class="sxs-lookup"><span data-stu-id="d7c04-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="d7c04-109">Een positionele para meter declareren</span><span class="sxs-lookup"><span data-stu-id="d7c04-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="d7c04-110">Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7c04-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="d7c04-111">Wanneer u het parameter kenmerk toevoegt, stelt u het sleutel woord `Position` in op de argument positie.</span><span class="sxs-lookup"><span data-stu-id="d7c04-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="d7c04-112">De waarde 0 geeft de eerste positie aan.</span><span class="sxs-lookup"><span data-stu-id="d7c04-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="d7c04-113">Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over het parameter kenmerk.</span><span class="sxs-lookup"><span data-stu-id="d7c04-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="d7c04-114">Een verplichte para meter declareren</span><span class="sxs-lookup"><span data-stu-id="d7c04-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="d7c04-115">Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7c04-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="d7c04-116">Wanneer u het parameter kenmerk toevoegt, stelt u het sleutel woord `Mandatory` in op `true`.</span><span class="sxs-lookup"><span data-stu-id="d7c04-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="d7c04-117">Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over het parameter kenmerk.</span><span class="sxs-lookup"><span data-stu-id="d7c04-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="d7c04-118">Een optionele para meter declareren</span><span class="sxs-lookup"><span data-stu-id="d7c04-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="d7c04-119">Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7c04-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="d7c04-120">Als u het parameter kenmerk toevoegt, laat u het sleutel woord `Mandatory` weg.</span><span class="sxs-lookup"><span data-stu-id="d7c04-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="d7c04-121">Een para meter voor een switch declareren</span><span class="sxs-lookup"><span data-stu-id="d7c04-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="d7c04-122">Definieer een open bare eigenschap als type [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)en Declareer vervolgens het parameter kenmerk.</span><span class="sxs-lookup"><span data-stu-id="d7c04-122">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="d7c04-123">Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over het parameter kenmerk.</span><span class="sxs-lookup"><span data-stu-id="d7c04-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="d7c04-124">Een para meter met aliassen declareren</span><span class="sxs-lookup"><span data-stu-id="d7c04-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="d7c04-125">Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7c04-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="d7c04-126">Voeg een alias kenmerk toe met een lijst met de aliassen voor de para meter.</span><span class="sxs-lookup"><span data-stu-id="d7c04-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="d7c04-127">In dit voor beeld worden drie aliassen gedefinieerd voor dezelfde para meter.</span><span class="sxs-lookup"><span data-stu-id="d7c04-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="d7c04-128">De eerste alias biedt een snelkoppeling.</span><span class="sxs-lookup"><span data-stu-id="d7c04-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="d7c04-129">De tweede en derde alias geven namen op die u voor verschillende scenario's kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d7c04-129">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="d7c04-130">Zie [alias kenmerk declaratie](./alias-attribute-declaration.md)voor meer informatie over het alias kenmerk.</span><span class="sxs-lookup"><span data-stu-id="d7c04-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d7c04-131">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d7c04-131">See Also</span></span>

[<span data-ttu-id="d7c04-132">System. Management. Automation. SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="d7c04-132">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="d7c04-133">Parameter kenmerk declaratie</span><span class="sxs-lookup"><span data-stu-id="d7c04-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="d7c04-134">Alias kenmerk declaratie</span><span class="sxs-lookup"><span data-stu-id="d7c04-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="d7c04-135">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="d7c04-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
