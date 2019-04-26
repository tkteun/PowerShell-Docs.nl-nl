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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068484"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="939b7-102">Invoerverwerkingsmethoden voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="939b7-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="939b7-103">Cmdlets moet een of meer van de verwerking van methoden die worden beschreven in dit onderwerp om hun werk te verrichten invoer overschrijven.</span><span class="sxs-lookup"><span data-stu-id="939b7-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="939b7-104">Deze methoden kunt de cmdlet bewerkingen van het vooraf verwerken, verwerking van invoer en nabewerking uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="939b7-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="939b7-105">Deze methoden kunnen u de verwerking van de cmdlet stop.</span><span class="sxs-lookup"><span data-stu-id="939b7-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="939b7-106">Zie voor een uitgebreider voorbeeld over het gebruik van deze methoden, [SelectStr zelfstudie](selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="939b7-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="939b7-107">Vooraf verwerken bewerkingen</span><span class="sxs-lookup"><span data-stu-id="939b7-107">Pre-Processing Operations</span></span>

<span data-ttu-id="939b7-108">Cmdlets moet worden overschreven de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode om toe te voegen voorverwerking bewerkingen die geldig zijn voor alle records die later worden verwerkt door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="939b7-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="939b7-109">Wanneer PowerShell een pijplijn opdracht verwerkt, aanroept PowerShell deze methode, eenmaal voor elk exemplaar van de cmdlet in de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="939b7-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="939b7-110">Zie voor meer informatie over hoe PowerShell de opdracht-pipeline roept [Cmdlet verwerking Lifecycle](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="939b7-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="939b7-111">De volgende code toont een implementatie van de methode BeginProcessing.</span><span class="sxs-lookup"><span data-stu-id="939b7-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="939b7-112">Invoer verwerkingen</span><span class="sxs-lookup"><span data-stu-id="939b7-112">Input Processing Operations</span></span>

<span data-ttu-id="939b7-113">Cmdlets kunt overschrijven de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode voor het verwerken van de invoer die is verzonden naar de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="939b7-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="939b7-114">Wanneer PowerShell een pijplijn opdracht verwerkt, aanroepen PowerShell met deze methode voor elke invoer record dat is verwerkt door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="939b7-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="939b7-115">Zie voor meer informatie over hoe PowerShell de opdracht-pipeline roept [Cmdlet verwerking Lifecycle](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="939b7-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="939b7-116">De volgende code toont een implementatie van de methode ProcessRecord.</span><span class="sxs-lookup"><span data-stu-id="939b7-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="939b7-117">Na verwerking bewerkingen</span><span class="sxs-lookup"><span data-stu-id="939b7-117">Post-Processing Operations</span></span>

<span data-ttu-id="939b7-118">Cmdlets moet worden overschreven de [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode om toe te voegen na verwerking bewerkingen die geldig zijn voor alle records die zijn verwerkt door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="939b7-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="939b7-119">Bijvoorbeeld, de cmdlet om op te schonen objectvariabelen nadat deze is voltooid mogelijk verwerken.</span><span class="sxs-lookup"><span data-stu-id="939b7-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="939b7-120">Wanneer PowerShell een pijplijn opdracht verwerkt, aanroept PowerShell deze methode, eenmaal voor elk exemplaar van de cmdlet in de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="939b7-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="939b7-121">Het is echter belangrijk te weten dat de PowerShell-runtime niet de methode EndProcessing roept als de cmdlet halverwege is geannuleerd door de verwerking van invoer of als er een afsluitfout optreedt in een deel van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="939b7-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="939b7-122">Om deze reden moet een cmdlet die opschonen voor object vereist de volledige implementeren [System.IDisposable](/dotnet/api/System.IDisposable) patroon, waaronder een finalizer, zodat de runtime kan zowel de EndProcessing aanroepen en [ System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methoden aan het einde van de verwerking.</span><span class="sxs-lookup"><span data-stu-id="939b7-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="939b7-123">Zie voor meer informatie over hoe PowerShell de opdracht-pipeline roept [Cmdlet verwerking Lifecycle](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="939b7-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="939b7-124">De volgende code toont een implementatie van de methode EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="939b7-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="939b7-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="939b7-125">See Also</span></span>

[<span data-ttu-id="939b7-126">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="939b7-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="939b7-127">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="939b7-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="939b7-128">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="939b7-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="939b7-129">SelectStr-zelfstudie</span><span class="sxs-lookup"><span data-stu-id="939b7-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="939b7-130">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="939b7-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="939b7-131">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="939b7-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
