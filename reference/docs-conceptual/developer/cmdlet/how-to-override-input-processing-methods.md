---
title: Invoer verwerkings methoden onderdrukken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355550"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="cb753-102">Invoerverwerkingsmethoden negeren</span><span class="sxs-lookup"><span data-stu-id="cb753-102">How to Override Input Processing Methods</span></span>

<span data-ttu-id="cb753-103">In deze voor beelden ziet u hoe u de invoer verwerkings methoden binnen een cmdlet overschrijft.</span><span class="sxs-lookup"><span data-stu-id="cb753-103">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="cb753-104">Deze methoden worden gebruikt om de volgende bewerkingen uit te voeren:</span><span class="sxs-lookup"><span data-stu-id="cb753-104">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="cb753-105">De methode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) wordt gebruikt voor het uitvoeren van eenmalige opstart bewerkingen die geldig zijn voor alle objecten die worden verwerkt door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cb753-105">The [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="cb753-106">De Windows Power shell-runtime roept deze methode slechts één keer op.</span><span class="sxs-lookup"><span data-stu-id="cb753-106">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="cb753-107">De methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) wordt gebruikt om de objecten te verwerken die zijn door gegeven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cb753-107">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="cb753-108">De Windows Power shell-runtime roept deze methode aan voor elk object dat wordt door gegeven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cb753-108">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="cb753-109">Met de methode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) kunt u eenmalige verwerkings bewerkingen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="cb753-109">The [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="cb753-110">De Windows Power shell-runtime roept deze methode slechts één keer op.</span><span class="sxs-lookup"><span data-stu-id="cb753-110">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="cb753-111">De methode BeginProcessing negeren</span><span class="sxs-lookup"><span data-stu-id="cb753-111">To override the BeginProcessing method</span></span>

- <span data-ttu-id="cb753-112">Declareer een beveiligde onderdrukking van de methode [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) .</span><span class="sxs-lookup"><span data-stu-id="cb753-112">Declare a protected override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="cb753-113">Met de volgende klasse wordt een voorbeeld bericht afgedrukt.</span><span class="sxs-lookup"><span data-stu-id="cb753-113">The following class prints a sample message.</span></span> <span data-ttu-id="cb753-114">Als u deze klasse wilt gebruiken, wijzigt u de werk woord en zelfstandig naam woord in het cmdlet-kenmerk, wijzigt u de namen van de klasse zodat deze overeenkomen met de nieuwe term en zelfstandig onderdeel. vervolgens voegt u de functionaliteit toe die u nodig hebt voor het overschrijven van [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode.</span><span class="sxs-lookup"><span data-stu-id="cb753-114">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

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

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="cb753-115">De methode ProcessRecord negeren</span><span class="sxs-lookup"><span data-stu-id="cb753-115">To override the ProcessRecord method</span></span>

- <span data-ttu-id="cb753-116">Declareer een beveiligde onderdrukking van de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="cb753-116">Declare a protected override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="cb753-117">Met de volgende klasse wordt een voorbeeld bericht afgedrukt.</span><span class="sxs-lookup"><span data-stu-id="cb753-117">The following class prints a sample message.</span></span> <span data-ttu-id="cb753-118">Als u deze klasse wilt gebruiken, wijzigt u de werk woord en zelfstandig naam woord in het cmdlet-kenmerk, wijzigt u de namen van de klasse zodanig dat ze overeenkomen met de nieuwe term en zelfstandig gebruik. vervolgens voegt u de functionaliteit toe die u nodig hebt voor het overschrijven van de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="cb753-118">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

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

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="cb753-119">De methode EndProcessing onderdrukken</span><span class="sxs-lookup"><span data-stu-id="cb753-119">To override the EndProcessing method</span></span>

- <span data-ttu-id="cb753-120">Declareer een beveiligde onderdrukking van de methode [System. Management. Automation. cmdlet.](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="cb753-120">Declare a protected override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="cb753-121">Met de volgende klasse wordt een voor beeld afgedrukt.</span><span class="sxs-lookup"><span data-stu-id="cb753-121">The following class prints a sample.</span></span> <span data-ttu-id="cb753-122">Als u deze klasse wilt gebruiken, wijzigt u de werk woord en zelfstandig naam woord in het cmdlet-kenmerk, wijzigt u de namen van de klasse zodanig dat ze overeenkomen met de nieuwe term en zelfstandig gebruik. vervolgens voegt u de functionaliteit toe die u nodig hebt voor het overschrijven van de methode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .</span><span class="sxs-lookup"><span data-stu-id="cb753-122">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cb753-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cb753-123">See Also</span></span>

[<span data-ttu-id="cb753-124">System. Management. Automation. cmdlet. BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="cb753-124">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="cb753-125">System. Management. Automation. cmdlet. EndProcessing</span><span class="sxs-lookup"><span data-stu-id="cb753-125">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="cb753-126">System. Management. Automation. cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="cb753-126">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="cb753-127">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="cb753-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
