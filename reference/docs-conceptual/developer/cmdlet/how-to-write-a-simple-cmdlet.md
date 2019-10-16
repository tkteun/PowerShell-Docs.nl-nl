---
title: Een eenvoudige cmdlet schrijven | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356250"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="92574-102">Een cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="92574-102">How to write a cmdlet</span></span>

<span data-ttu-id="92574-103">In dit artikel wordt beschreven hoe u een cmdlet schrijft.</span><span class="sxs-lookup"><span data-stu-id="92574-103">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="92574-104">De `Send-Greeting`-cmdlet gebruikt één gebruikers naam als invoer en schrijft vervolgens een begroeting naar die gebruiker.</span><span class="sxs-lookup"><span data-stu-id="92574-104">The `Send-Greeting` cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="92574-105">Hoewel de cmdlet niet veel werk doet, wordt in dit voor beeld de belangrijkste secties van een cmdlet gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="92574-105">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="92574-106">Stappen voor het schrijven van een cmdlet</span><span class="sxs-lookup"><span data-stu-id="92574-106">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="92574-107">Gebruik het **cmdlet** -kenmerk om de klasse als een cmdlet te declareren.</span><span class="sxs-lookup"><span data-stu-id="92574-107">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="92574-108">Het **cmdlet** -kenmerk geeft de term en het zelfstandig naam woord op voor de naam van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="92574-108">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="92574-109">Zie [CmdletAttribute-declaratie](cmdlet-attribute-declaration.md)voor meer informatie over het **cmdlet** -kenmerk.</span><span class="sxs-lookup"><span data-stu-id="92574-109">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="92574-110">Geef de naam van de klasse op.</span><span class="sxs-lookup"><span data-stu-id="92574-110">Specify the name of the class.</span></span>

3. <span data-ttu-id="92574-111">Geef op dat de cmdlet is afgeleid van een van de volgende klassen:</span><span class="sxs-lookup"><span data-stu-id="92574-111">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="92574-112">System. Management. Automation. cmdlet</span><span class="sxs-lookup"><span data-stu-id="92574-112">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="92574-113">System. Management. Automation. PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="92574-113">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="92574-114">Gebruik het **parameter** kenmerk om de para meters voor de cmdlet te definiëren.</span><span class="sxs-lookup"><span data-stu-id="92574-114">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="92574-115">In dit geval is er slechts één vereiste para meter opgegeven.</span><span class="sxs-lookup"><span data-stu-id="92574-115">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="92574-116">Zie [ParameterAttribute-declaratie](parameter-attribute-declaration.md)voor meer informatie over het **parameter** kenmerk.</span><span class="sxs-lookup"><span data-stu-id="92574-116">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="92574-117">Overschrijf de invoer verwerkings methode waarmee de invoer wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="92574-117">Override the input processing method that processes the input.</span></span> <span data-ttu-id="92574-118">In dit geval wordt de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) genegeerd.</span><span class="sxs-lookup"><span data-stu-id="92574-118">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="92574-119">Als u de begroeting wilt schrijven, gebruikt u de methode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span><span class="sxs-lookup"><span data-stu-id="92574-119">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="92574-120">De begroeting wordt weer gegeven in de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="92574-120">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="92574-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="92574-121">Example</span></span>

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify the
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory=true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="92574-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="92574-122">See also</span></span>

[<span data-ttu-id="92574-123">System. Management. Automation. cmdlet</span><span class="sxs-lookup"><span data-stu-id="92574-123">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="92574-124">System. Management. Automation. PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="92574-124">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="92574-125">System. Management. Automation. cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="92574-125">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="92574-126">System. Management. Automation. cmdlet. WriteObject</span><span class="sxs-lookup"><span data-stu-id="92574-126">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="92574-127">CmdletAttribute-declaratie</span><span class="sxs-lookup"><span data-stu-id="92574-127">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="92574-128">ParameterAttribute-declaratie</span><span class="sxs-lookup"><span data-stu-id="92574-128">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="92574-129">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="92574-129">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)