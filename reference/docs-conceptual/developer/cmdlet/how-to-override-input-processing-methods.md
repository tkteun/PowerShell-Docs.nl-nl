---
ms.date: 09/13/2016
ms.topic: reference
title: Invoerverwerkingsmethoden negeren
description: Invoerverwerkingsmethoden negeren
ms.openlocfilehash: 4e8d71a34a1480ce63435ac6cc5dce60d4219c03
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667008"
---
# <a name="how-to-override-input-processing-methods"></a>Invoerverwerkingsmethoden negeren

In deze voor beelden ziet u hoe u de invoer verwerkings methoden binnen een cmdlet overschrijft. Deze methoden worden gebruikt om de volgende bewerkingen uit te voeren:

- De methode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) wordt gebruikt voor het uitvoeren van eenmalige opstart bewerkingen die geldig zijn voor alle objecten die worden verwerkt door de cmdlet. De Windows Power shell-runtime roept deze methode slechts één keer op.

- De methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) wordt gebruikt om de objecten te verwerken die zijn door gegeven aan de cmdlet. De Windows Power shell-runtime roept deze methode aan voor elk object dat wordt door gegeven aan de cmdlet.

- Met de methode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) kunt u eenmalige verwerkings bewerkingen uitvoeren. De Windows Power shell-runtime roept deze methode slechts één keer op.

## <a name="to-override-the-beginprocessing-method"></a>De methode BeginProcessing negeren

- Declareer een beveiligde onderdrukking van de methode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) .

Met de volgende klasse wordt een voorbeeld bericht afgedrukt. Als u deze klasse wilt gebruiken, wijzigt u de werk woord en zelfstandig naam woord in het cmdlet-kenmerk, wijzigt u de namen van de klasse zodanig dat ze overeenkomen met de nieuwe term en zelfstandig gebruik. vervolgens voegt u de functionaliteit toe die u nodig hebt voor het overschrijven van de methode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) .

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a>De methode ProcessRecord negeren

- Declareer een beveiligde onderdrukking van de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

Met de volgende klasse wordt een voorbeeld bericht afgedrukt. Als u deze klasse wilt gebruiken, wijzigt u de werk woord en zelfstandig naam woord in het cmdlet-kenmerk, wijzigt u de namen van de klasse zodanig dat ze overeenkomen met de nieuwe term en zelfstandig gebruik. vervolgens voegt u de functionaliteit toe die u nodig hebt voor het overschrijven van de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a>De methode EndProcessing onderdrukken

- Declareer een beveiligde onderdrukking van de methode [System. Management. Automation. cmdlet.](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . EndProcessing.

Met de volgende klasse wordt een voor beeld afgedrukt. Als u deze klasse wilt gebruiken, wijzigt u de werk woord en zelfstandig naam woord in het cmdlet-kenmerk, wijzigt u de namen van de klasse zodanig dat ze overeenkomen met de nieuwe term en zelfstandig gebruik. vervolgens voegt u de functionaliteit toe die u nodig hebt voor het overschrijven van de methode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a>Zie ook

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
