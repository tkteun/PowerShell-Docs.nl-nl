---
title: Niet-afsluit fouten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359270"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="c5b17-102">Fouten waarbij de functie of bewerking niet wordt beëindigd</span><span class="sxs-lookup"><span data-stu-id="c5b17-102">Non-Terminating Errors</span></span>

<span data-ttu-id="c5b17-103">In dit onderwerp wordt de methode beschreven die wordt gebruikt om niet-afsluit fouten te rapporteren.</span><span class="sxs-lookup"><span data-stu-id="c5b17-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="c5b17-104">Ook wordt beschreven hoe u de methode aanroept vanuit de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c5b17-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="c5b17-105">Als er een fout optreedt die niet wordt afgesloten, moet de cmdlet deze fout rapporteren door de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="c5b17-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="c5b17-106">Wanneer de cmdlet een niet-afsluit fout rapporteert, kan de cmdlet blijven werken op dit invoer object en op verdere inkomende pijplijn objecten.</span><span class="sxs-lookup"><span data-stu-id="c5b17-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="c5b17-107">Als de cmdlet de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aanroept, kan de cmdlet een fout record schrijven met een beschrijving van de voor waarde die de niet-afsluit bare fout heeft veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="c5b17-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="c5b17-108">Zie [Windows Power Shell-fout records](./windows-powershell-error-records.md)voor meer informatie over fout records.</span><span class="sxs-lookup"><span data-stu-id="c5b17-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="c5b17-109">Cmdlets kunnen [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aanroepen vanuit hun invoer methoden.</span><span class="sxs-lookup"><span data-stu-id="c5b17-109">Cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="c5b17-110">Met cmdlets kan [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) echter alleen worden aangeroepen vanuit de thread met de naam [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Automation. cmdlet. ProcessRecord of [System. Management.](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) Automation. cmdlet. EndProcessing-invoer methode.</span><span class="sxs-lookup"><span data-stu-id="c5b17-110">However, cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="c5b17-111">Roep [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) niet aan vanuit een andere thread.</span><span class="sxs-lookup"><span data-stu-id="c5b17-111">Do not call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="c5b17-112">Communiceert in plaats daarvan fouten terug naar de hoofd thread.</span><span class="sxs-lookup"><span data-stu-id="c5b17-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5b17-113">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c5b17-113">See Also</span></span>

[<span data-ttu-id="c5b17-114">System. Management. Automation. cmdlet. WriteError</span><span class="sxs-lookup"><span data-stu-id="c5b17-114">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="c5b17-115">System. Management. Automation. cmdlet. BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="c5b17-115">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="c5b17-116">System. Management. Automation. cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="c5b17-116">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="c5b17-117">System. Management. Automation. cmdlet. EndProcessing</span><span class="sxs-lookup"><span data-stu-id="c5b17-117">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="c5b17-118">Windows Power Shell-fout records</span><span class="sxs-lookup"><span data-stu-id="c5b17-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="c5b17-119">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="c5b17-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
