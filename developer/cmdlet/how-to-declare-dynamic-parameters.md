---
title: Hoe u dynamische Parameters declareren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db04f1df-def5-4456-8869-336024cda723
caps.latest.revision: 8
ms.openlocfilehash: a9c530cdc66302eb6b3d9d2b284eeb486c3b2ba9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847969"
---
# <a name="how-to-declare-dynamic-parameters"></a><span data-ttu-id="57e71-102">Dynamische parameters declareren</span><span class="sxs-lookup"><span data-stu-id="57e71-102">How to Declare Dynamic Parameters</span></span>

<span data-ttu-id="57e71-103">In dit voorbeeld ziet u hoe u dynamische parameters die zijn toegevoegd aan de cmdlet tijdens runtime.</span><span class="sxs-lookup"><span data-stu-id="57e71-103">This example shows how to define dynamic parameters that are added to the cmdlet at runtime.</span></span> <span data-ttu-id="57e71-104">In dit voorbeeld wordt de `Department` parameter is toegevoegd aan de cmdlet wanneer de gebruiker Hiermee geeft u de `Employee` parameter overschakelen.</span><span class="sxs-lookup"><span data-stu-id="57e71-104">In this example, the `Department` parameter is added to the cmdlet whenever the user specifies the `Employee` switch parameter.</span></span> <span data-ttu-id="57e71-105">Zie voor meer informatie over dynamische parameters [dynamische Parameters van de Cmdlet](./cmdlet-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="57e71-105">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).</span></span>

## <a name="to-define-dynamic-parameters"></a><span data-ttu-id="57e71-106">Dynamische parameters definiëren</span><span class="sxs-lookup"><span data-stu-id="57e71-106">To define dynamic parameters</span></span>

1. <span data-ttu-id="57e71-107">Voeg in de declaratie van de klasse cmdlet de [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interface zoals wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="57e71-107">In the cmdlet class declaration, add the [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interface as shown.</span></span>

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. <span data-ttu-id="57e71-108">Roep de [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) methode retourneert een object waarin de dynamische parameters zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="57e71-108">Call the [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) method, which returns the object in which the dynamic parameters are defined.</span></span> <span data-ttu-id="57e71-109">In dit voorbeeld wordt de methode wordt aangeroepen wanneer de `Employee` parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="57e71-109">In this example, the method is called when the `Employee` parameter is specified.</span></span>

   ```csharp
   public object GetDynamicParameters()
   {
       if (employee)
       {
         context= new SendGreetingCommandDynamicParameters();
         return context;
       }
       return null;
   }
   private SendGreetingCommandDynamicParameters context;
   ```

3. <span data-ttu-id="57e71-110">Declareer een klasse die de dynamische parameters definieert moeten worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="57e71-110">Declare a class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="57e71-111">U kunt de kenmerken die u hebt gebruikt om aan te geven van de statische cmdlet-parameters op te geven van de dynamische parameters gebruiken.</span><span class="sxs-lookup"><span data-stu-id="57e71-111">You can use the attributes that you used to declare the static cmdlet parameters to declare the dynamic parameters.</span></span>

   ```csharp
   public class SendGreetingCommandDynamicParameters
   {
     [Parameter]
     [ValidateSet ("Marketing", "Sales", "Development")]
     public string Department
     {
       get { return department; }
       set { department = value; }
     }
     private string department;
   }
   ```

## <a name="example"></a><span data-ttu-id="57e71-112">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="57e71-112">Example</span></span>

<span data-ttu-id="57e71-113">In dit voorbeeld wordt de `Department` parameter wordt toegevoegd wanneer de gebruiker Hiermee geeft u de `Employee` parameter.</span><span class="sxs-lookup"><span data-stu-id="57e71-113">In this example, the `Department` parameter is added whenever the user specifies the `Employee` parameter.</span></span> <span data-ttu-id="57e71-114">De `Department` parameter is een optionele parameter en het kenmerk ValidateSet wordt gebruikt om op te geven van de toegestane argumenten.</span><span class="sxs-lookup"><span data-stu-id="57e71-114">The `Department` parameter is an optional parameter, and the ValidateSet attribute is used to specify the allowed arguments.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;     // PowerShell assembly.

namespace SendGreeting
{
  // Declare the cmdlet class that supports the
  // IDynamicParameters interface.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet, IDynamicParameters
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    [Parameter]
    [Alias ("FTE")]
    public SwitchParameter Employee
    {
      get { return employee; }
      set { employee = value; }
    }
    private Boolean employee;

    // Implement GetDynamicParameters to
    // retrieve the dynamic parameter.
    public object GetDynamicParameters()
    {
      if (employee)
      {
        context= new SendGreetingCommandDynamicParameters();
        return context;
      }
      return null;
   }
   private SendGreetingCommandDynamicParameters context;

    // Overide the ProcessRecord method to process the
    // supplied user name and write out a greeting to
    // the user by calling the WriteObject method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "! ");
      if (employee)
      {
        WriteObject("Department: " + context.Department);
      }
    }
  }

  // Define the dynamic parameters to be added
  public class SendGreetingCommandDynamicParameters
  {
    [Parameter]
    [ValidateSet ("Marketing", "Sales", "Development")]
    public string Department
    {
      get { return department; }
      set { department = value; }
    }
    private string department;
  }
}
```

## <a name="see-also"></a><span data-ttu-id="57e71-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="57e71-115">See Also</span></span>

[<span data-ttu-id="57e71-116">System.Management.Automation.Runtimedefinedparameterdictionary</span><span class="sxs-lookup"><span data-stu-id="57e71-116">System.Management.Automation.Runtimedefinedparameterdictionary</span></span>](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[<span data-ttu-id="57e71-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="57e71-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="57e71-118">Dynamische cmdlet-Parameters</span><span class="sxs-lookup"><span data-stu-id="57e71-118">Cmdlet Dynamic Parameters</span></span>](./cmdlet-dynamic-parameters.md)

[<span data-ttu-id="57e71-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="57e71-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)