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
ms.openlocfilehash: 9d5c9b16fc5daf3d2f753eeeeedb0db925551a67
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845253"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="8c07e-102">Fouten waarbij de functie of bewerking niet wordt beëindigd</span><span class="sxs-lookup"><span data-stu-id="8c07e-102">Non-Terminating Errors</span></span>

<span data-ttu-id="8c07e-103">In dit onderwerp worden de methode die wordt gebruikt voor het rapporteren van niet-afsluitfouten.</span><span class="sxs-lookup"><span data-stu-id="8c07e-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="8c07e-104">Hierin worden ook over het aanroepen van de methode van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c07e-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="8c07e-105">Wanneer er een niet-afsluitfout optreedt, de cmdlet moet Meld deze fout door het aanroepen van de [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode.</span><span class="sxs-lookup"><span data-stu-id="8c07e-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="8c07e-106">Wanneer de cmdlet een niet-afsluitfout meldt, de cmdlet kan door blijven werken op dit invoerobject en verdere inkomende pipeline-objecten.</span><span class="sxs-lookup"><span data-stu-id="8c07e-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="8c07e-107">Als de cmdlet roept de [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode, de cmdlet kunt schrijven een foutrecord die beschrijft de voorwaarde dat de niet-afsluitfouten fout heeft veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="8c07e-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="8c07e-108">Zie voor meer informatie over foutrecords [Windows PowerShell-foutrecords](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="8c07e-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="8c07e-109">Cmdlets kan aanroepen [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) zo nodig uit binnen hun invoer verwerkingsmethoden.</span><span class="sxs-lookup"><span data-stu-id="8c07e-109">Cmdlets can call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="8c07e-110">Echter cmdlets kan aanroepen [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) alleen vanaf de thread die met de naam de [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), of [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) invoermethode voor verwerking.</span><span class="sxs-lookup"><span data-stu-id="8c07e-110">However, cmdlets can call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="8c07e-111">Roep niet [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) via een andere thread.</span><span class="sxs-lookup"><span data-stu-id="8c07e-111">Do not call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="8c07e-112">In plaats daarvan communiceren fouten terug naar de hoofdthread.</span><span class="sxs-lookup"><span data-stu-id="8c07e-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c07e-113">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8c07e-113">See Also</span></span>

[<span data-ttu-id="8c07e-114">System.Management.Automation.Cmdlet.Writeerror\*</span><span class="sxs-lookup"><span data-stu-id="8c07e-114">System.Management.Automation.Cmdlet.Writeerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="8c07e-115">System.Management.Automation.Cmdlet.Beginprocessing\*</span><span class="sxs-lookup"><span data-stu-id="8c07e-115">System.Management.Automation.Cmdlet.Beginprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="8c07e-116">System.Management.Automation.Cmdlet.Processrecord\*</span><span class="sxs-lookup"><span data-stu-id="8c07e-116">System.Management.Automation.Cmdlet.Processrecord\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="8c07e-117">System.Management.Automation.Cmdlet.Endprocessing\*</span><span class="sxs-lookup"><span data-stu-id="8c07e-117">System.Management.Automation.Cmdlet.Endprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="8c07e-118">Windows PowerShell-foutrecords</span><span class="sxs-lookup"><span data-stu-id="8c07e-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="8c07e-119">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8c07e-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
