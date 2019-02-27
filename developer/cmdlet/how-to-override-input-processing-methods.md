---
title: Het onderdrukken van invoer verwerkingsmethoden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: eff40a01b60985788ae0e21156fec7ec4e27fcf1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846751"
---
# <a name="how-to-override-input-processing-methods"></a>Invoerverwerkingsmethoden negeren

Deze voorbeelden laten zien hoe de invoer voor het verwerken van methoden die in een cmdlet overschrijven. Deze methoden worden gebruikt om uit te voeren van de volgende bewerkingen:

- De [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode wordt gebruikt voor het opstarten van eenmalige-bewerkingen die geldig voor alle objecten die zijn verwerkt door de cmdlet zijn uitvoeren. Deze methode worden slechts één keer aanroept in de Windows PowerShell-runtime.

- De [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode wordt gebruikt voor het verwerken van de objecten die zijn doorgegeven aan de cmdlet. De Windows PowerShell-runtime wordt deze methode voor elk object doorgegeven aan de cmdlet.

- De [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode wordt gebruikt voor het uitvoeren van bewerkingen voor de verwerking eenmalige post. Deze methode worden slechts één keer aanroept in de Windows PowerShell-runtime.

## <a name="to-override-the-beginprocessing-method"></a>Voor de onderdrukking van de methode BeginProcessing

- Declareer een beveiligde onderdrukking van de [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode.

De volgende klasse worden afgedrukt een voorbeeldbericht weergegeven. Voor het gebruik van deze klasse het werkwoord en een zelfstandig naamwoord in de Cmdlet-kenmerk wijzigen, wijzigt u de naam van de klasse in overeenstemming met de nieuwe werkwoord en een zelfstandig naamwoord en vervolgens de gewenste functionaliteit toevoegen aan de onderdrukking van de [System.Management.Automation.Cmdlet.Beginprocessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode.

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

## <a name="to-override-the-processrecord-method"></a>Voor de onderdrukking van de methode ProcessRecord

- Declareer een beveiligde onderdrukking van de [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode.

De volgende klasse worden afgedrukt een voorbeeldbericht weergegeven. Voor het gebruik van deze klasse het werkwoord en een zelfstandig naamwoord in de Cmdlet-kenmerk wijzigen, wijzigt u de naam van de klasse in overeenstemming met de nieuwe werkwoord en een zelfstandig naamwoord en vervolgens de gewenste functionaliteit toevoegen aan de onderdrukking van de [System.Management.Automation.Cmdlet.Processrecord* ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode.

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

## <a name="to-override-the-endprocessing-method"></a>Voor de onderdrukking van de methode EndProcessing

- Declareer een beveiligde onderdrukking van de [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode.

De volgende klasse worden afgedrukt een voorbeeld. Voor het gebruik van deze klasse het werkwoord en een zelfstandig naamwoord in de Cmdlet-kenmerk wijzigen, wijzigt u de naam van de klasse in overeenstemming met de nieuwe werkwoord en een zelfstandig naamwoord en vervolgens de gewenste functionaliteit toevoegen aan de onderdrukking van de [System.Management.Automation.Cmdlet.Endprocessing* ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode.

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

[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
