---
title: Invoer methoden voor het verwerken van cmdlets | Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359477"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="3acd1-102">Invoerverwerkingsmethoden voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="3acd1-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="3acd1-103">Cmdlets moeten een of meer van de invoer verwerkings methoden die in dit onderwerp worden beschreven, overschrijven om hun werk uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="3acd1-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="3acd1-104">Met deze methoden kan de cmdlet bewerkingen uitvoeren van vóór verwerking, invoer verwerking en na de verwerking.</span><span class="sxs-lookup"><span data-stu-id="3acd1-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="3acd1-105">Met deze methoden kunt u ook de verwerking van de cmdlet stoppen.</span><span class="sxs-lookup"><span data-stu-id="3acd1-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="3acd1-106">Zie [SelectStr-zelf studie](selectstr-tutorial.md)voor een gedetailleerd voor beeld van het gebruik van deze methoden.</span><span class="sxs-lookup"><span data-stu-id="3acd1-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="3acd1-107">Pre-processing bewerkingen</span><span class="sxs-lookup"><span data-stu-id="3acd1-107">Pre-Processing Operations</span></span>

<span data-ttu-id="3acd1-108">Cmdlets moeten de methode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) overschrijven om voor verwerking van bewerkingen toe te voegen die geldig zijn voor alle records die later worden verwerkt door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3acd1-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="3acd1-109">Wanneer Power shell een opdracht pijplijn verwerkt, roept Power shell deze methode één keer aan voor elk exemplaar van de cmdlet in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="3acd1-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="3acd1-110">Zie [cmdlet processing Lifecycle](/previous-versions/ms714429(v=vs.85))voor meer informatie over hoe Power shell de opdracht pijplijn aanroept.</span><span class="sxs-lookup"><span data-stu-id="3acd1-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="3acd1-111">De volgende code toont een implementatie van de methode BeginProcessing.</span><span class="sxs-lookup"><span data-stu-id="3acd1-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="3acd1-112">Invoer bewerkingen</span><span class="sxs-lookup"><span data-stu-id="3acd1-112">Input Processing Operations</span></span>

<span data-ttu-id="3acd1-113">Cmdlets kunnen de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) overschrijven om de invoer te verwerken die naar de cmdlet wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="3acd1-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="3acd1-114">Wanneer Power shell een opdracht pijplijn verwerkt, roept Power shell deze methode aan voor elk invoer record dat door de cmdlet wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="3acd1-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="3acd1-115">Zie [cmdlet processing Lifecycle](/previous-versions/ms714429(v=vs.85))voor meer informatie over hoe Power shell de opdracht pijplijn aanroept.</span><span class="sxs-lookup"><span data-stu-id="3acd1-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="3acd1-116">De volgende code toont een implementatie van de methode ProcessRecord.</span><span class="sxs-lookup"><span data-stu-id="3acd1-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="3acd1-117">Bewerkingen na verwerking</span><span class="sxs-lookup"><span data-stu-id="3acd1-117">Post-Processing Operations</span></span>

<span data-ttu-id="3acd1-118">Cmdlets moeten de methode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) overschrijven om verwerkings bewerkingen toe te voegen die geldig zijn voor alle records die zijn verwerkt door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3acd1-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="3acd1-119">Stel dat uw cmdlet object variabelen moet opschonen nadat de verwerking is voltooid.</span><span class="sxs-lookup"><span data-stu-id="3acd1-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="3acd1-120">Wanneer Power shell een opdracht pijplijn verwerkt, roept Power shell deze methode één keer aan voor elk exemplaar van de cmdlet in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="3acd1-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="3acd1-121">Het is echter belang rijk te weten dat de methode EndProcessing niet wordt aangeroepen door de Power shell-runtime als de cmdlet halverwege wordt geannuleerd door de invoer verwerking of als er een afsluit fout optreedt in een deel van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3acd1-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="3acd1-122">Daarom moet een cmdlet die het opruimen van objecten vereist, het volledige [System. IDisposable](/dotnet/api/System.IDisposable) -patroon implementeren, met inbegrip van een FINALIZE, zodat de runtime zowel de methoden EndProcessing als [System. IDisposable. Dispose](/dotnet/api/System.IDisposable.Dispose) aan het einde van bezig.</span><span class="sxs-lookup"><span data-stu-id="3acd1-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="3acd1-123">Zie [cmdlet processing Lifecycle](/previous-versions/ms714429(v=vs.85))voor meer informatie over hoe Power shell de opdracht pijplijn aanroept.</span><span class="sxs-lookup"><span data-stu-id="3acd1-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="3acd1-124">De volgende code toont een implementatie van de methode EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="3acd1-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="3acd1-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3acd1-125">See Also</span></span>

[<span data-ttu-id="3acd1-126">System. Management. Automation. cmdlet. BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="3acd1-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="3acd1-127">System. Management. Automation. cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="3acd1-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="3acd1-128">System. Management. Automation. cmdlet. EndProcessing</span><span class="sxs-lookup"><span data-stu-id="3acd1-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="3acd1-129">Zelf studie voor SelectStr</span><span class="sxs-lookup"><span data-stu-id="3acd1-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="3acd1-130">System. IDisposable</span><span class="sxs-lookup"><span data-stu-id="3acd1-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="3acd1-131">Windows Power shell shell SDK</span><span class="sxs-lookup"><span data-stu-id="3acd1-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
