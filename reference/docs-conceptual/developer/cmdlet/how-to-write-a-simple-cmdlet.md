---
title: Een eenvoudige cmdlet schrijven | Microsoft Docs
ms.date: 01/15/2019
ms.openlocfilehash: 2ff0b47454804c9becd6f03ac521946b9596bb8b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784058"
---
# <a name="how-to-write-a-cmdlet"></a>Een cmdlet schrijven

In dit artikel wordt beschreven hoe u een cmdlet schrijft. De `Send-Greeting` cmdlet gebruikt één gebruikers naam als invoer en schrijft vervolgens een begroeting naar die gebruiker. Hoewel de cmdlet niet veel werk doet, wordt in dit voor beeld de belangrijkste secties van een cmdlet gedemonstreerd.

## <a name="steps-to-write-a-cmdlet"></a>Stappen voor het schrijven van een cmdlet

1. Gebruik het **cmdlet** -kenmerk om de klasse als een cmdlet te declareren. Het **cmdlet** -kenmerk geeft de term en het zelfstandig naam woord op voor de naam van de cmdlet.

   Zie [CmdletAttribute-declaratie](cmdlet-attribute-declaration.md)voor meer informatie over het **cmdlet** -kenmerk.

2. Geef de naam van de klasse op.

3. Geef op dat de cmdlet is afgeleid van een van de volgende klassen:

   * [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)
   * [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

4. Gebruik het **parameter** kenmerk om de para meters voor de cmdlet te definiëren. In dit geval is er slechts één vereiste para meter opgegeven.

   Zie [ParameterAttribute-declaratie](parameter-attribute-declaration.md)voor meer informatie over het **parameter** kenmerk.

5. Overschrijf de invoer verwerkings methode waarmee de invoer wordt verwerkt. In dit geval wordt de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) genegeerd.

6. Als u de begroeting wilt schrijven, gebruikt u de methode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject).
   De begroeting wordt weer gegeven in de volgende indeling:

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

[System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)

[System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)

[CmdletAttribute-declaratie](cmdlet-attribute-declaration.md)

[ParameterAttribute-declaratie](parameter-attribute-declaration.md)

[Een Windows PowerShell-cmdlet schrijven](writing-a-windows-powershell-cmdlet.md)
