---
ms.date: 01/15/2019
ms.topic: reference
title: Een eenvoudige cmdlet schrijven
description: Een eenvoudige cmdlet schrijven
ms.openlocfilehash: 59dce5d797f80647e0b70a1f80faf67198652082
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646497"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="adc59-103">Een cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="adc59-103">How to write a cmdlet</span></span>

<span data-ttu-id="adc59-104">In dit artikel wordt beschreven hoe u een cmdlet schrijft.</span><span class="sxs-lookup"><span data-stu-id="adc59-104">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="adc59-105">De `Send-Greeting` cmdlet gebruikt één gebruikers naam als invoer en schrijft vervolgens een begroeting naar die gebruiker.</span><span class="sxs-lookup"><span data-stu-id="adc59-105">The `Send-Greeting` cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="adc59-106">Hoewel de cmdlet niet veel werk doet, wordt in dit voor beeld de belangrijkste secties van een cmdlet gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="adc59-106">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="adc59-107">Stappen voor het schrijven van een cmdlet</span><span class="sxs-lookup"><span data-stu-id="adc59-107">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="adc59-108">Gebruik het **cmdlet** -kenmerk om de klasse als een cmdlet te declareren.</span><span class="sxs-lookup"><span data-stu-id="adc59-108">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="adc59-109">Het **cmdlet** -kenmerk geeft de term en het zelfstandig naam woord op voor de naam van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="adc59-109">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="adc59-110">Zie [CmdletAttribute-declaratie](cmdlet-attribute-declaration.md)voor meer informatie over het **cmdlet** -kenmerk.</span><span class="sxs-lookup"><span data-stu-id="adc59-110">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="adc59-111">Geef de naam van de klasse op.</span><span class="sxs-lookup"><span data-stu-id="adc59-111">Specify the name of the class.</span></span>

3. <span data-ttu-id="adc59-112">Geef op dat de cmdlet is afgeleid van een van de volgende klassen:</span><span class="sxs-lookup"><span data-stu-id="adc59-112">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="adc59-113">System. Management. Automation. cmdlet</span><span class="sxs-lookup"><span data-stu-id="adc59-113">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="adc59-114">System. Management. Automation. PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="adc59-114">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="adc59-115">Gebruik het **parameter** kenmerk om de para meters voor de cmdlet te definiëren.</span><span class="sxs-lookup"><span data-stu-id="adc59-115">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="adc59-116">In dit geval is er slechts één vereiste para meter opgegeven.</span><span class="sxs-lookup"><span data-stu-id="adc59-116">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="adc59-117">Zie [ParameterAttribute-declaratie](parameter-attribute-declaration.md)voor meer informatie over het **parameter** kenmerk.</span><span class="sxs-lookup"><span data-stu-id="adc59-117">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="adc59-118">Overschrijf de invoer verwerkings methode waarmee de invoer wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="adc59-118">Override the input processing method that processes the input.</span></span> <span data-ttu-id="adc59-119">In dit geval wordt de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) genegeerd.</span><span class="sxs-lookup"><span data-stu-id="adc59-119">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="adc59-120">Als u de begroeting wilt schrijven, gebruikt u de methode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span><span class="sxs-lookup"><span data-stu-id="adc59-120">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="adc59-121">De begroeting wordt weer gegeven in de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="adc59-121">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="adc59-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="adc59-122">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="adc59-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="adc59-123">See also</span></span>

[<span data-ttu-id="adc59-124">System. Management. Automation. cmdlet</span><span class="sxs-lookup"><span data-stu-id="adc59-124">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="adc59-125">System. Management. Automation. PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="adc59-125">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="adc59-126">System. Management. Automation. cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="adc59-126">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="adc59-127">System. Management. Automation. cmdlet. WriteObject</span><span class="sxs-lookup"><span data-stu-id="adc59-127">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="adc59-128">CmdletAttribute-declaratie</span><span class="sxs-lookup"><span data-stu-id="adc59-128">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="adc59-129">ParameterAttribute-declaratie</span><span class="sxs-lookup"><span data-stu-id="adc59-129">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="adc59-130">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="adc59-130">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)
