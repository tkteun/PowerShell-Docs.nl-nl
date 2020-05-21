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
ms.openlocfilehash: 9bd72e8f97c194c98adb1049f5a966549113fd12
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563893"
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
