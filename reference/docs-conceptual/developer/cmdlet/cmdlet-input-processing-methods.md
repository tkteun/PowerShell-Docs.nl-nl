---
ms.date: 09/13/2016
ms.topic: reference
title: Invoerverwerkingsmethoden voor cmdlets
description: Invoerverwerkingsmethoden voor cmdlets
ms.openlocfilehash: e1a7b58517d6285250edbf16d14810388c242218
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653390"
---
# <a name="cmdlet-input-processing-methods"></a>Invoerverwerkingsmethoden voor cmdlets

Cmdlets moeten een of meer van de invoer verwerkings methoden die in dit onderwerp worden beschreven, overschrijven om hun werk uit te voeren.
Met deze methoden kan de cmdlet bewerkingen uitvoeren van vóór verwerking, invoer verwerking en na de verwerking.
Met deze methoden kunt u ook de verwerking van de cmdlet stoppen.
Zie [SelectStr-zelf studie](selectstr-tutorial.md)voor een gedetailleerd voor beeld van het gebruik van deze methoden.

## <a name="pre-processing-operations"></a>Pre-processing bewerkingen

Cmdlets moeten de methode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) overschrijven om voor verwerking van bewerkingen toe te voegen die geldig zijn voor alle records die later worden verwerkt door de cmdlet.
Wanneer Power shell een opdracht pijplijn verwerkt, roept Power shell deze methode één keer aan voor elk exemplaar van de cmdlet in de pijp lijn.
Zie [cmdlet processing Lifecycle](/previous-versions/ms714429(v=vs.85))voor meer informatie over hoe Power shell de opdracht pijplijn aanroept.

De volgende code toont een implementatie van de methode BeginProcessing.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>Invoer bewerkingen

Cmdlets kunnen de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) overschrijven om de invoer te verwerken die naar de cmdlet wordt verzonden.
Wanneer Power shell een opdracht pijplijn verwerkt, roept Power shell deze methode aan voor elk invoer record dat door de cmdlet wordt verwerkt.
Zie [cmdlet processing Lifecycle](/previous-versions/ms714429(v=vs.85))voor meer informatie over hoe Power shell de opdracht pijplijn aanroept.

De volgende code toont een implementatie van de methode ProcessRecord.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>Bewerkingen na verwerking

Cmdlets moeten de methode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) overschrijven om verwerkings bewerkingen toe te voegen die geldig zijn voor alle records die zijn verwerkt door de cmdlet.
Stel dat uw cmdlet object variabelen moet opschonen nadat de verwerking is voltooid.

Wanneer Power shell een opdracht pijplijn verwerkt, roept Power shell deze methode één keer aan voor elk exemplaar van de cmdlet in de pijp lijn.
Het is echter belang rijk te weten dat de methode EndProcessing niet wordt aangeroepen door de Power shell-runtime als de cmdlet halverwege wordt geannuleerd door de invoer verwerking of als er een afsluit fout optreedt in een deel van de cmdlet.
Daarom moet een cmdlet die het opruimen van objecten vereist, het volledige [System. IDisposable](/dotnet/api/System.IDisposable) -patroon implementeren, met inbegrip van een FINALIZE, zodat de runtime zowel de methoden EndProcessing als [System. IDisposable. Dispose](/dotnet/api/System.IDisposable.Dispose) aan het einde van de verwerking kan aanroepen.
Zie [cmdlet processing Lifecycle](/previous-versions/ms714429(v=vs.85))voor meer informatie over hoe Power shell de opdracht pijplijn aanroept.

De volgende code toont een implementatie van de methode EndProcessing.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>Zie ook

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[SelectStr-zelfstudie](selectstr-tutorial.md)

[System. IDisposable](/dotnet/api/System.IDisposable)

[Windows Power shell shell SDK](../windows-powershell-reference.md)
