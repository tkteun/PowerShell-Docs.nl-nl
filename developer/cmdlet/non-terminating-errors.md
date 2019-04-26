---
title: Niet-afsluitfouten fouten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067651"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="2ce21-102">Fouten waarbij de functie of bewerking niet wordt beëindigd</span><span class="sxs-lookup"><span data-stu-id="2ce21-102">Non-Terminating Errors</span></span>

<span data-ttu-id="2ce21-103">In dit onderwerp worden de methode die wordt gebruikt voor het rapporteren van niet-afsluitfouten.</span><span class="sxs-lookup"><span data-stu-id="2ce21-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="2ce21-104">Hierin worden ook over het aanroepen van de methode van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2ce21-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="2ce21-105">Wanneer er een niet-afsluitfout optreedt, de cmdlet moet Meld deze fout door het aanroepen van de [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode.</span><span class="sxs-lookup"><span data-stu-id="2ce21-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="2ce21-106">Wanneer de cmdlet een niet-afsluitfout meldt, de cmdlet kan door blijven werken op dit invoerobject en verdere inkomende pipeline-objecten.</span><span class="sxs-lookup"><span data-stu-id="2ce21-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="2ce21-107">Als de cmdlet roept de [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode, de cmdlet kunt schrijven een foutrecord die beschrijft de voorwaarde dat de niet-afsluitfouten fout heeft veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="2ce21-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="2ce21-108">Zie voor meer informatie over foutrecords [Windows PowerShell-foutrecords](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="2ce21-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="2ce21-109">Cmdlets kan aanroepen [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) zo nodig uit binnen hun invoer verwerkingsmethoden.</span><span class="sxs-lookup"><span data-stu-id="2ce21-109">Cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="2ce21-110">Echter cmdlets kan aanroepen [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) alleen vanaf de thread die met de naam de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), of [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) invoermethode voor verwerking.</span><span class="sxs-lookup"><span data-stu-id="2ce21-110">However, cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="2ce21-111">Roep niet [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) via een andere thread.</span><span class="sxs-lookup"><span data-stu-id="2ce21-111">Do not call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="2ce21-112">In plaats daarvan communiceren fouten terug naar de hoofdthread.</span><span class="sxs-lookup"><span data-stu-id="2ce21-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ce21-113">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2ce21-113">See Also</span></span>

[<span data-ttu-id="2ce21-114">System.Management.Automation.Cmdlet.WriteError</span><span class="sxs-lookup"><span data-stu-id="2ce21-114">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="2ce21-115">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="2ce21-115">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="2ce21-116">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="2ce21-116">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="2ce21-117">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="2ce21-117">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="2ce21-118">Windows PowerShell-foutrecords</span><span class="sxs-lookup"><span data-stu-id="2ce21-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="2ce21-119">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2ce21-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
