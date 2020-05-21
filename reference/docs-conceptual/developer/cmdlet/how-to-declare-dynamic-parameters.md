---
title: Dynamische para meters declareren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db04f1df-def5-4456-8869-336024cda723
caps.latest.revision: 8
ms.openlocfilehash: d3c2c339ba9ac6ec4a1958fadbfe1c6d74e3d736
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561049"
---
# <a name="how-to-declare-dynamic-parameters"></a><span data-ttu-id="e21af-102">Dynamische parameters declareren</span><span class="sxs-lookup"><span data-stu-id="e21af-102">How to Declare Dynamic Parameters</span></span>

<span data-ttu-id="e21af-103">In dit voor beeld ziet u hoe u dynamische para meters kunt definiëren die tijdens runtime worden toegevoegd aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e21af-103">This example shows how to define dynamic parameters that are added to the cmdlet at runtime.</span></span> <span data-ttu-id="e21af-104">In dit voor beeld `Department` wordt de para meter toegevoegd aan de cmdlet wanneer de gebruiker de `Employee` para meter switch opgeeft.</span><span class="sxs-lookup"><span data-stu-id="e21af-104">In this example, the `Department` parameter is added to the cmdlet whenever the user specifies the `Employee` switch parameter.</span></span> <span data-ttu-id="e21af-105">Zie [cmdlet Dynamic para meters](./cmdlet-dynamic-parameters.md)voor meer informatie over dynamische para meters.</span><span class="sxs-lookup"><span data-stu-id="e21af-105">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).</span></span>

## <a name="to-define-dynamic-parameters"></a><span data-ttu-id="e21af-106">Dynamische para meters definiëren</span><span class="sxs-lookup"><span data-stu-id="e21af-106">To define dynamic parameters</span></span>

1. <span data-ttu-id="e21af-107">Voeg in de declaratie van de cmdlet-klasse de interface [System. Management. Automation. Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) toe zoals wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e21af-107">In the cmdlet class declaration, add the [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interface as shown.</span></span>

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. <span data-ttu-id="e21af-108">Roep de methode [System. Management. Automation. Idynamicparameters. Getdynamicparameters \*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) aan, waarmee het object wordt geretourneerd waarin de dynamische para meters zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="e21af-108">Call the [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) method, which returns the object in which the dynamic parameters are defined.</span></span> <span data-ttu-id="e21af-109">In dit voor beeld wordt de-methode aangeroepen wanneer de `Employee` para meter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e21af-109">In this example, the method is called when the `Employee` parameter is specified.</span></span>

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

3. <span data-ttu-id="e21af-110">Declareer een klasse die de dynamische para meters definieert die moeten worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="e21af-110">Declare a class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="e21af-111">U kunt de kenmerken gebruiken die u hebt gebruikt voor het declareren van de statische cmdlet-para meters voor het declareren van de dynamische para meters.</span><span class="sxs-lookup"><span data-stu-id="e21af-111">You can use the attributes that you used to declare the static cmdlet parameters to declare the dynamic parameters.</span></span>

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

## <a name="example"></a><span data-ttu-id="e21af-112">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e21af-112">Example</span></span>

<span data-ttu-id="e21af-113">In dit voor beeld `Department` wordt de para meter toegevoegd wanneer de gebruiker de `Employee` para meter opgeeft.</span><span class="sxs-lookup"><span data-stu-id="e21af-113">In this example, the `Department` parameter is added whenever the user specifies the `Employee` parameter.</span></span> <span data-ttu-id="e21af-114">De `Department` para meter is een optionele para meter en het kenmerk validate wordt gebruikt om de toegestane argumenten op te geven.</span><span class="sxs-lookup"><span data-stu-id="e21af-114">The `Department` parameter is an optional parameter, and the ValidateSet attribute is used to specify the allowed arguments.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e21af-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e21af-115">See Also</span></span>

[<span data-ttu-id="e21af-116">System. Management. Automation. Runtimedefinedparameterdictionary</span><span class="sxs-lookup"><span data-stu-id="e21af-116">System.Management.Automation.Runtimedefinedparameterdictionary</span></span>](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[<span data-ttu-id="e21af-117">System. Management. Automation. Idynamicparameters. Getdynamicparameters \*</span><span class="sxs-lookup"><span data-stu-id="e21af-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="e21af-118">Dynamische cmdlet-parameters</span><span class="sxs-lookup"><span data-stu-id="e21af-118">Cmdlet Dynamic Parameters</span></span>](./cmdlet-dynamic-parameters.md)

[<span data-ttu-id="e21af-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e21af-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
