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
ms.openlocfilehash: 8271512d06047f3ff5e45f81d971ffe2c1f6afd7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067736"
---
# <a name="how-to-write-a-cmdlet"></a>Over het schrijven van een cmdlet

In dit artikel laat zien hoe het schrijven van een cmdlet. De `Send-Greeting` cmdlet wordt de naam van een enkele gebruiker als invoer en vervolgens schrijft een begroeting voor die gebruiker. Hoewel de cmdlet niet veel werk te hoeven, is dit voorbeeld ziet u de belangrijkste secties van een cmdlet.

## <a name="steps-to-write-a-cmdlet"></a>Stappen voor het schrijven van een cmdlet

1. U declareert de klasse als een cmdlet, gebruikt u de **Cmdlet** kenmerk. De **Cmdlet** kenmerk Hiermee geeft u de bewerking en het zelfstandig naamwoord voor de cmdlet-naam.

   Voor meer informatie over de **Cmdlet** kenmerk, Zie [CmdletAttribute declaratie](cmdlet-attribute-declaration.md).

2. Geef de naam van de klasse.

3. Geef op dat de cmdlet is afgeleid van een van de volgende klassen:

   * [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. Voor het definiëren van de parameters voor de cmdlet, de **Parameter** kenmerk. In dit geval vereist slechts één parameter is opgegeven.

   Voor meer informatie over de **Parameter** kenmerk, Zie [ParameterAttribute declaratie](parameter-attribute-declaration.md).

5. Overschrijven de invoer verwerken methode waarmee de invoer wordt verwerkt. In dit geval de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode wordt overschreven.

6. Gebruik de methode voor het schrijven van de begroeting [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).
   De begroeting wordt weergegeven in de volgende indeling:

   ```Output
   Hello <UserName>!
   ```

## <a name="example"></a>Voorbeeld

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

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)

[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[CmdletAttribute declaratie](cmdlet-attribute-declaration.md)

[ParameterAttribute declaratie](parameter-attribute-declaration.md)

[Schrijven van een Windows PowerShell-Cmdlet](writing-a-windows-powershell-cmdlet.md)