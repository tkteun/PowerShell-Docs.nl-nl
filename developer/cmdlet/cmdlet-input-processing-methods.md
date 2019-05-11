---
title: Cmdlet invoer verwerkingsmethoden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670314"
---
# <a name="cmdlet-input-processing-methods"></a>Invoerverwerkingsmethoden voor cmdlets

Cmdlets moet een of meer van de verwerking van methoden die worden beschreven in dit onderwerp om hun werk te verrichten invoer overschrijven.
Deze methoden kunt de cmdlet bewerkingen van het vooraf verwerken, verwerking van invoer en nabewerking uit te voeren.
Deze methoden kunnen u de verwerking van de cmdlet stop.
Zie voor een uitgebreider voorbeeld over het gebruik van deze methoden, [SelectStr zelfstudie](selectstr-tutorial.md).

## <a name="pre-processing-operations"></a>Vooraf verwerken bewerkingen

Cmdlets moet worden overschreven de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode om toe te voegen voorverwerking bewerkingen die geldig zijn voor alle records die later worden verwerkt door de cmdlet.
Wanneer PowerShell een pijplijn opdracht verwerkt, aanroept PowerShell deze methode, eenmaal voor elk exemplaar van de cmdlet in de pijplijn.
Zie voor meer informatie over hoe PowerShell de opdracht-pipeline roept [Cmdlet verwerking Lifecycle](/previous-versions/ms714429(v=vs.85)).

De volgende code toont een implementatie van de methode BeginProcessing.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>Invoer verwerkingen

Cmdlets kunt overschrijven de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode voor het verwerken van de invoer die is verzonden naar de cmdlet.
Wanneer PowerShell een pijplijn opdracht verwerkt, aanroepen PowerShell met deze methode voor elke invoer record dat is verwerkt door de cmdlet.
Zie voor meer informatie over hoe PowerShell de opdracht-pipeline roept [Cmdlet verwerking Lifecycle](/previous-versions/ms714429(v=vs.85)).

De volgende code toont een implementatie van de methode ProcessRecord.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>Na verwerking bewerkingen

Cmdlets moet worden overschreven de [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode om toe te voegen na verwerking bewerkingen die geldig zijn voor alle records die zijn verwerkt door de cmdlet.
Bijvoorbeeld, de cmdlet om op te schonen objectvariabelen nadat deze is voltooid mogelijk verwerken.

Wanneer PowerShell een pijplijn opdracht verwerkt, aanroept PowerShell deze methode, eenmaal voor elk exemplaar van de cmdlet in de pijplijn.
Het is echter belangrijk te weten dat de PowerShell-runtime niet de methode EndProcessing roept als de cmdlet halverwege is geannuleerd door de verwerking van invoer of als er een afsluitfout optreedt in een deel van de cmdlet.
Om deze reden moet een cmdlet die opschonen voor object vereist de volledige implementeren [System.IDisposable](/dotnet/api/System.IDisposable) patroon, waaronder een finalizer, zodat de runtime kan zowel de EndProcessing aanroepen en [ System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methoden aan het einde van de verwerking.
Zie voor meer informatie over hoe PowerShell de opdracht-pipeline roept [Cmdlet verwerking Lifecycle](/previous-versions/ms714429(v=vs.85)).

De volgende code toont een implementatie van de methode EndProcessing.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[SelectStr-zelfstudie](selectstr-tutorial.md)

[System.IDisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
