---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet-parameters declareren
description: Cmdlet-parameters declareren
ms.openlocfilehash: ed53f9788c9afb142b137e08966dff33551b9d0f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667093"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="e7a92-103">Cmdlet-parameters declareren</span><span class="sxs-lookup"><span data-stu-id="e7a92-103">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="e7a92-104">In deze voor beelden ziet u hoe u para meters met de naam, positioneel, required, optional en switch declareert.</span><span class="sxs-lookup"><span data-stu-id="e7a92-104">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="e7a92-105">In deze voor beelden ziet u ook hoe u een parameter alias definieert.</span><span class="sxs-lookup"><span data-stu-id="e7a92-105">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="e7a92-106">Een benoemde para meter declareren</span><span class="sxs-lookup"><span data-stu-id="e7a92-106">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="e7a92-107">Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e7a92-107">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e7a92-108">Wanneer u het parameter kenmerk toevoegt, laat u het `Position` tref woord weg uit het kenmerk.</span><span class="sxs-lookup"><span data-stu-id="e7a92-108">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="e7a92-109">Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over het parameter kenmerk.</span><span class="sxs-lookup"><span data-stu-id="e7a92-109">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="e7a92-110">Een positionele para meter declareren</span><span class="sxs-lookup"><span data-stu-id="e7a92-110">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="e7a92-111">Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e7a92-111">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e7a92-112">Wanneer u het parameter kenmerk toevoegt, stelt u het `Position` tref woord in op de argument positie.</span><span class="sxs-lookup"><span data-stu-id="e7a92-112">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="e7a92-113">De waarde 0 geeft de eerste positie aan.</span><span class="sxs-lookup"><span data-stu-id="e7a92-113">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="e7a92-114">Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over het parameter kenmerk.</span><span class="sxs-lookup"><span data-stu-id="e7a92-114">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="e7a92-115">Een verplichte para meter declareren</span><span class="sxs-lookup"><span data-stu-id="e7a92-115">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="e7a92-116">Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e7a92-116">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e7a92-117">Wanneer u het parameter kenmerk toevoegt, stelt u het `Mandatory` sleutel woord in op `true` .</span><span class="sxs-lookup"><span data-stu-id="e7a92-117">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="e7a92-118">Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over het parameter kenmerk.</span><span class="sxs-lookup"><span data-stu-id="e7a92-118">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="e7a92-119">Een optionele para meter declareren</span><span class="sxs-lookup"><span data-stu-id="e7a92-119">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="e7a92-120">Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e7a92-120">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e7a92-121">Als u het parameter kenmerk toevoegt, laat u het `Mandatory` tref woord weg.</span><span class="sxs-lookup"><span data-stu-id="e7a92-121">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="e7a92-122">Een para meter voor een switch declareren</span><span class="sxs-lookup"><span data-stu-id="e7a92-122">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="e7a92-123">Definieer een open bare eigenschap als type [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)en Declareer vervolgens het parameter kenmerk.</span><span class="sxs-lookup"><span data-stu-id="e7a92-123">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="e7a92-124">Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over het parameter kenmerk.</span><span class="sxs-lookup"><span data-stu-id="e7a92-124">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="e7a92-125">Een para meter met aliassen declareren</span><span class="sxs-lookup"><span data-stu-id="e7a92-125">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="e7a92-126">Definieer een open bare eigenschap zoals in de volgende code wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e7a92-126">Define a public property as shown in the following code.</span></span> <span data-ttu-id="e7a92-127">Voeg een alias kenmerk toe met een lijst met de aliassen voor de para meter.</span><span class="sxs-lookup"><span data-stu-id="e7a92-127">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="e7a92-128">In dit voor beeld worden drie aliassen gedefinieerd voor dezelfde para meter.</span><span class="sxs-lookup"><span data-stu-id="e7a92-128">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="e7a92-129">De eerste alias biedt een snelkoppeling.</span><span class="sxs-lookup"><span data-stu-id="e7a92-129">The first alias provides a shortcut.</span></span> <span data-ttu-id="e7a92-130">De tweede en derde alias geven namen op die u voor verschillende scenario's kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e7a92-130">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="e7a92-131">Zie [alias kenmerk declaratie](./alias-attribute-declaration.md)voor meer informatie over het alias kenmerk.</span><span class="sxs-lookup"><span data-stu-id="e7a92-131">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e7a92-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e7a92-132">See Also</span></span>

[<span data-ttu-id="e7a92-133">System. Management. Automation. SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="e7a92-133">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="e7a92-134">Declaratie van het kenmerk Parameter</span><span class="sxs-lookup"><span data-stu-id="e7a92-134">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="e7a92-135">Declaratie van het kenmerk Alias</span><span class="sxs-lookup"><span data-stu-id="e7a92-135">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="e7a92-136">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="e7a92-136">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
