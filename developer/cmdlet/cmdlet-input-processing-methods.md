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
ms.openlocfilehash: 065214647dfa6d376b727930fe75140911095faf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059368"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="a3ad8-102">Invoerverwerkingsmethoden voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="a3ad8-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="a3ad8-103">Cmdlets moet een of meer van de verwerking van methoden die worden beschreven in dit onderwerp om hun werk te verrichten invoer overschrijven.</span><span class="sxs-lookup"><span data-stu-id="a3ad8-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span> <span data-ttu-id="a3ad8-104">Deze methoden kunt de cmdlet uit te voeren vooraf verwerken bewerkingen, invoer verwerkingen en na verwerking van bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="a3ad8-104">These methods allow the cmdlet to perform pre-processing operations, input processing operations, and post-processing operations.</span></span> <span data-ttu-id="a3ad8-105">Deze methoden kunnen u de verwerking van de cmdlet stop.</span><span class="sxs-lookup"><span data-stu-id="a3ad8-105">These methods also allow you to stop cmdlet processing.</span></span>

## <a name="pre-processing-tasks"></a><span data-ttu-id="a3ad8-106">Taken vooraf verwerken</span><span class="sxs-lookup"><span data-stu-id="a3ad8-106">Pre-Processing Tasks</span></span>

<span data-ttu-id="a3ad8-107">Cmdlets moet worden overschreven de [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) methode om toe te voegen voorverwerking bewerkingen die geldig zijn voor alle records die later worden verwerkt door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3ad8-107">Cmdlets should override the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span> <span data-ttu-id="a3ad8-108">Wanneer een opdracht pijplijn wordt verwerkt door Windows PowerShell, aanroepen Windows PowerShell met deze methode eenmaal voor elk exemplaar van de cmdlet in de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="a3ad8-108">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="a3ad8-109">Zie voor meer informatie over hoe de opdracht-pipeline in Windows PowerShell wordt aangeroepen, [Cmdlet verwerking Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="a3ad8-109">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="a3ad8-110">De volgende code toont een implementatie van de [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) methode.</span><span class="sxs-lookup"><span data-stu-id="a3ad8-110">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method.</span></span>

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

<span data-ttu-id="a3ad8-111">Voor een uitgebreider voorbeeld van hoe u de [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) methode, Zie [SelectStr zelfstudie](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="a3ad8-111">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span> <span data-ttu-id="a3ad8-112">In deze zelfstudie de **Selecteer Str** cmdlet gebruikt de [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) methode voor het genereren van de reguliere expressie die wordt gebruikt om te zoeken naar de invoer voor het verwerken van records.</span><span class="sxs-lookup"><span data-stu-id="a3ad8-112">In this tutorial, the **Select-Str** cmdlet uses the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to generate the regular expression that is used to search the input processing records.</span></span>

## <a name="input-processing-tasks"></a><span data-ttu-id="a3ad8-113">Invoer van verwerkingstaken</span><span class="sxs-lookup"><span data-stu-id="a3ad8-113">Input Processing Tasks</span></span>

<span data-ttu-id="a3ad8-114">Cmdlets kunt overschrijven de [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) methode voor het verwerken van de invoer die is verzonden naar de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3ad8-114">Cmdlets can override the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method to process the input that is sent to the cmdlet.</span></span> <span data-ttu-id="a3ad8-115">Wanneer een opdracht pijplijn wordt verwerkt door Windows PowerShell, aanroepen Windows PowerShell met deze methode voor elke invoer record dat is verwerkt door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3ad8-115">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method for each input record that is processed by the cmdlet.</span></span> <span data-ttu-id="a3ad8-116">Zie voor meer informatie over hoe de opdracht-pipeline in Windows PowerShell wordt aangeroepen, [Cmdlet verwerking Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="a3ad8-116">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="a3ad8-117">De volgende code toont een implementatie van de [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) methode.</span><span class="sxs-lookup"><span data-stu-id="a3ad8-117">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

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

<span data-ttu-id="a3ad8-118">Voor een uitgebreider voorbeeld van hoe u de [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) methode, Zie [SelectStr zelfstudie](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="a3ad8-118">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="post-processing-tasks"></a><span data-ttu-id="a3ad8-119">Taken na verwerking</span><span class="sxs-lookup"><span data-stu-id="a3ad8-119">Post-Processing Tasks</span></span>

<span data-ttu-id="a3ad8-120">Cmdlets moet worden overschreven de [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) methode om toe te voegen na verwerking bewerkingen die geldig zijn voor alle records die zijn verwerkt door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3ad8-120">Cmdlets should override the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span> <span data-ttu-id="a3ad8-121">Bijvoorbeeld, de cmdlet om op te schonen objectvariabelen nadat deze is voltooid mogelijk verwerken.</span><span class="sxs-lookup"><span data-stu-id="a3ad8-121">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="a3ad8-122">Wanneer een opdracht pijplijn wordt verwerkt door Windows PowerShell, aanroepen Windows PowerShell met deze methode eenmaal voor elk exemplaar van de cmdlet in de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="a3ad8-122">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="a3ad8-123">Het is echter belangrijk te weten dat de Windows PowerShell-runtime niet roept de [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) methode als de cmdlet halverwege is geannuleerd door de verwerking van invoer of als een afsluitende fout in een deel van de cmdlet optreedt.</span><span class="sxs-lookup"><span data-stu-id="a3ad8-123">However, it is important to remember that the Windows PowerShell runtime will not call the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="a3ad8-124">Om deze reden moet een cmdlet die opschonen voor object vereist de volledige implementeren [System.IDisposable](/dotnet/api/System.IDisposable) patroon, waaronder een finalizer, zodat de runtime zowel aanroepen kan de [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) en [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methoden aan het einde van de verwerking.</span><span class="sxs-lookup"><span data-stu-id="a3ad8-124">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span> <span data-ttu-id="a3ad8-125">Zie voor meer informatie over hoe de opdracht-pipeline in Windows PowerShell wordt aangeroepen, [Cmdlet verwerking Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="a3ad8-125">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="a3ad8-126">De volgende code toont een implementatie van de [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) methode.</span><span class="sxs-lookup"><span data-stu-id="a3ad8-126">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

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

<span data-ttu-id="a3ad8-127">Voor een uitgebreider voorbeeld van hoe u de [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) methode, Zie [SelectStr zelfstudie](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="a3ad8-127">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a3ad8-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a3ad8-128">See Also</span></span>

[<span data-ttu-id="a3ad8-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="a3ad8-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="a3ad8-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="a3ad8-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[<span data-ttu-id="a3ad8-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="a3ad8-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="a3ad8-132">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="a3ad8-132">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="a3ad8-133">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="a3ad8-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
