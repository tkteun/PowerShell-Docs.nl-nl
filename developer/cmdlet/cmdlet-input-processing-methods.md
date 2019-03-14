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
ms.openlocfilehash: 7f8d25e03707052b1d5b62e245caae360da11d0b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794940"
---
# <a name="cmdlet-input-processing-methods"></a>Invoerverwerkingsmethoden voor cmdlets

Cmdlets moet een of meer van de verwerking van methoden die worden beschreven in dit onderwerp om hun werk te verrichten invoer overschrijven. Deze methoden kunt de cmdlet uit te voeren vooraf verwerken bewerkingen, invoer verwerkingen en na verwerking van bewerkingen. Deze methoden kunnen u de verwerking van de cmdlet stop.

## <a name="pre-processing-tasks"></a>Taken vooraf verwerken

Cmdlets moet worden overschreven de [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) methode om toe te voegen voorverwerking bewerkingen die geldig zijn voor alle records die later worden verwerkt door de cmdlet. Wanneer een opdracht pijplijn wordt verwerkt door Windows PowerShell, aanroepen Windows PowerShell met deze methode eenmaal voor elk exemplaar van de cmdlet in de pijplijn. Zie voor meer informatie over hoe de opdracht-pipeline in Windows PowerShell wordt aangeroepen, [Cmdlet verwerking Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

De volgende code toont een implementatie van de [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) methode.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

Voor een uitgebreider voorbeeld van hoe u de [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) methode, Zie [SelectStr zelfstudie](./selectstr-tutorial.md). In deze zelfstudie de **Selecteer Str** cmdlet gebruikt de [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) methode voor het genereren van de reguliere expressie die wordt gebruikt om te zoeken naar de invoer voor het verwerken van records.

## <a name="input-processing-tasks"></a>Invoer van verwerkingstaken

Cmdlets kunt overschrijven de [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) methode voor het verwerken van de invoer die is verzonden naar de cmdlet. Wanneer een opdracht pijplijn wordt verwerkt door Windows PowerShell, aanroepen Windows PowerShell met deze methode voor elke invoer record dat is verwerkt door de cmdlet. Zie voor meer informatie over hoe de opdracht-pipeline in Windows PowerShell wordt aangeroepen, [Cmdlet verwerking Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

De volgende code toont een implementatie van de [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) methode.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

Voor een uitgebreider voorbeeld van hoe u de [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) methode, Zie [SelectStr zelfstudie](./selectstr-tutorial.md).

## <a name="post-processing-tasks"></a>Taken na verwerking

Cmdlets moet worden overschreven de [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) methode om toe te voegen na verwerking bewerkingen die geldig zijn voor alle records die zijn verwerkt door de cmdlet. Bijvoorbeeld, de cmdlet om op te schonen objectvariabelen nadat deze is voltooid mogelijk verwerken.

Wanneer een opdracht pijplijn wordt verwerkt door Windows PowerShell, aanroepen Windows PowerShell met deze methode eenmaal voor elk exemplaar van de cmdlet in de pijplijn. Het is echter belangrijk te weten dat de Windows PowerShell-runtime niet roept de [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) methode als de cmdlet halverwege is geannuleerd door de verwerking van invoer of als een afsluitende fout in een deel van de cmdlet optreedt. Om deze reden moet een cmdlet die opschonen voor object vereist de volledige implementeren [System.Idisposable](/dotnet/api/System.IDisposable) patroon, waaronder een finalizer, zodat de runtime zowel aanroepen kan de [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) en [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) methoden aan het einde van de verwerking. Zie voor meer informatie over hoe de opdracht-pipeline in Windows PowerShell wordt aangeroepen, [Cmdlet verwerking Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

De volgende code toont een implementatie van de [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) methode.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

Voor een uitgebreider voorbeeld van hoe u de [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) methode, Zie [SelectStr zelfstudie](./selectstr-tutorial.md).

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[System.Idisposable](/dotnet/api/System.IDisposable)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
