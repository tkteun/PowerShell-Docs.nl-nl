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
ms.openlocfilehash: a9c530cdc66302eb6b3d9d2b284eeb486c3b2ba9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355515"
---
# <a name="how-to-declare-dynamic-parameters"></a>Dynamische parameters declareren

In dit voor beeld ziet u hoe u dynamische para meters kunt definiëren die tijdens runtime worden toegevoegd aan de cmdlet. In dit voor beeld wordt de para meter `Department` toegevoegd aan de cmdlet wanneer de gebruiker de para meter `Employee`-switch opgeeft. Zie [cmdlet Dynamic para meters](./cmdlet-dynamic-parameters.md)voor meer informatie over dynamische para meters.

## <a name="to-define-dynamic-parameters"></a>Dynamische para meters definiëren

1. Voeg in de declaratie van de cmdlet-klasse de interface [System. Management. Automation. Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) toe zoals wordt weer gegeven.

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. Roep de methode [System. Management. Automation. Idynamicparameters. Getdynamicparameters *](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) aan, waarmee het object wordt geretourneerd waarin de dynamische para meters zijn gedefinieerd. In dit voor beeld wordt de-methode aangeroepen wanneer de para meter `Employee` is opgegeven.

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

3. Declareer een klasse die de dynamische para meters definieert die moeten worden toegevoegd. U kunt de kenmerken gebruiken die u hebt gebruikt voor het declareren van de statische cmdlet-para meters voor het declareren van de dynamische para meters.

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

## <a name="example"></a>Voorbeeld

In dit voor beeld wordt de para meter `Department` toegevoegd wanneer de gebruiker de para meter `Employee` opgeeft. De para meter `Department` is een optionele para meter en het kenmerk validate wordt gebruikt om de toegestane argumenten op te geven.

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

## <a name="see-also"></a>Zie ook

[System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[System. Management. Automation. Idynamicparameters. Getdynamicparameters *](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Cmdlet dynamische para meters](./cmdlet-dynamic-parameters.md)

[Windows Power shell SDK](../windows-powershell-reference.md)