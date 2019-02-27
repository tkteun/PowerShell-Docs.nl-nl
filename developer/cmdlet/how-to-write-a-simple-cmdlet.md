---
title: Over het schrijven van een eenvoudige Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137543d8-0012-4cba-bcd6-98b25aac83bb
caps.latest.revision: 9
ms.openlocfilehash: 2fc1a3947ca6076387ea85d7f8ba9018ed7385a0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849530"
---
# <a name="how-to-write-a-cmdlet"></a><span data-ttu-id="13aea-102">Over het schrijven van een cmdlet</span><span class="sxs-lookup"><span data-stu-id="13aea-102">How to write a cmdlet</span></span>

<span data-ttu-id="13aea-103">In dit artikel laat zien hoe het schrijven van een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="13aea-103">This article shows how to write a cmdlet.</span></span> <span data-ttu-id="13aea-104">De **verzenden begroeting** cmdlet wordt de naam van een enkele gebruiker als invoer en vervolgens schrijft een begroeting voor die gebruiker.</span><span class="sxs-lookup"><span data-stu-id="13aea-104">The **Send-Greeting** cmdlet takes a single user name as input and then writes a greeting to that user.</span></span> <span data-ttu-id="13aea-105">Hoewel de cmdlet niet veel werk te hoeven, is dit voorbeeld ziet u de belangrijkste secties van een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="13aea-105">Although the cmdlet does not do much work, this example demonstrates the major sections of a cmdlet.</span></span>

## <a name="steps-to-write-a-cmdlet"></a><span data-ttu-id="13aea-106">Stappen voor het schrijven van een cmdlet</span><span class="sxs-lookup"><span data-stu-id="13aea-106">Steps to write a cmdlet</span></span>

1. <span data-ttu-id="13aea-107">U declareert de klasse als een cmdlet, gebruikt u de **Cmdlet** kenmerk.</span><span class="sxs-lookup"><span data-stu-id="13aea-107">To declare the class as a cmdlet, use the **Cmdlet** attribute.</span></span> <span data-ttu-id="13aea-108">De **Cmdlet** kenmerk Hiermee geeft u de bewerking en het zelfstandig naamwoord voor de cmdlet-naam.</span><span class="sxs-lookup"><span data-stu-id="13aea-108">The **Cmdlet** attribute specifies the verb and the noun for the cmdlet name.</span></span>

   <span data-ttu-id="13aea-109">Voor meer informatie over de **Cmdlet** kenmerk, Zie [CmdletAttribute declaratie](cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="13aea-109">For more information about the **Cmdlet** attribute, see [CmdletAttribute Declaration](cmdlet-attribute-declaration.md).</span></span>

2. <span data-ttu-id="13aea-110">Geef de naam van de klasse.</span><span class="sxs-lookup"><span data-stu-id="13aea-110">Specify the name of the class.</span></span>

3. <span data-ttu-id="13aea-111">Geef op dat de cmdlet is afgeleid van een van de volgende klassen:</span><span class="sxs-lookup"><span data-stu-id="13aea-111">Specify that the cmdlet derives from either of the following classes:</span></span>

   * [<span data-ttu-id="13aea-112">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="13aea-112">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)
   * [<span data-ttu-id="13aea-113">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="13aea-113">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

4. <span data-ttu-id="13aea-114">Voor het definiëren van de parameters voor de cmdlet, de **Parameter** kenmerk.</span><span class="sxs-lookup"><span data-stu-id="13aea-114">To define the parameters for the cmdlet, use the **Parameter** attribute.</span></span> <span data-ttu-id="13aea-115">In dit geval vereist slechts één parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="13aea-115">In this case, only one required parameter is specified.</span></span>

   <span data-ttu-id="13aea-116">Voor meer informatie over de **Parameter** kenmerk, Zie [ParameterAttribute declaratie](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="13aea-116">For more information about the **Parameter** attribute, see [ParameterAttribute Declaration](parameter-attribute-declaration.md).</span></span>

5. <span data-ttu-id="13aea-117">Overschrijven de invoer verwerken methode waarmee de invoer wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="13aea-117">Override the input processing method that processes the input.</span></span> <span data-ttu-id="13aea-118">In dit geval de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="13aea-118">In this case, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden.</span></span>

6. <span data-ttu-id="13aea-119">Gebruik de methode voor het schrijven van de begroeting [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span><span class="sxs-lookup"><span data-stu-id="13aea-119">To write the greeting, use the method [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).</span></span>
   <span data-ttu-id="13aea-120">De begroeting wordt weergegeven in de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="13aea-120">The greeting is displayed in the following format:</span></span>

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a><span data-ttu-id="13aea-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="13aea-121">Example</span></span>

```csharp
using System.Management.Automation;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify and
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

## <a name="see-also"></a><span data-ttu-id="13aea-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="13aea-122">See also</span></span>

[<span data-ttu-id="13aea-123">System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="13aea-123">System.Management.Automation.Cmdlet</span></span>](/dotnet/api/System.Management.Automation.Cmdlet)

[<span data-ttu-id="13aea-124">System.Management.Automation.PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="13aea-124">System.Management.Automation.PSCmdlet</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet)

[<span data-ttu-id="13aea-125">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="13aea-125">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="13aea-126">System.Management.Automation.Cmdlet.WriteObject</span><span class="sxs-lookup"><span data-stu-id="13aea-126">System.Management.Automation.Cmdlet.WriteObject</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[<span data-ttu-id="13aea-127">CmdletAttribute declaratie</span><span class="sxs-lookup"><span data-stu-id="13aea-127">CmdletAttribute Declaration</span></span>](cmdlet-attribute-declaration.md)

[<span data-ttu-id="13aea-128">ParameterAttribute declaratie</span><span class="sxs-lookup"><span data-stu-id="13aea-128">ParameterAttribute Declaration</span></span>](parameter-attribute-declaration.md)

[<span data-ttu-id="13aea-129">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="13aea-129">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)
