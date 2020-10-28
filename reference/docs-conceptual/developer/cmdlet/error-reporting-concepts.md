---
ms.date: 09/13/2016
ms.topic: reference
title: Concepten voor foutrapportage
description: Concepten voor foutrapportage
ms.openlocfilehash: 353e628c63667a2db010556b2ed9169809b742f4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653045"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="ef774-103">Concepten voor foutrapportage</span><span class="sxs-lookup"><span data-stu-id="ef774-103">Error Reporting Concepts</span></span>

<span data-ttu-id="ef774-104">Windows Power shell biedt twee mechanismen voor het rapporteren van fouten: één mechanisme voor het *beëindigen van fouten* en een ander mechanisme voor *niet-afsluit fouten* .</span><span class="sxs-lookup"><span data-stu-id="ef774-104">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors* .</span></span> <span data-ttu-id="ef774-105">Het is belang rijk om ervoor te zorgen dat uw cmdlet fouten correct rapporteert, zodat de hosttoepassing waarop uw cmdlets worden uitgevoerd, op de juiste manier kan reageren.</span><span class="sxs-lookup"><span data-stu-id="ef774-105">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="ef774-106">De cmdlet moet de methode [System. Management. Automation. cmdlet. Throwterminatingerror \*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) aanroepen als er een fout optreedt waarbij de cmdlet de invoer objecten niet kan blijven verwerken.</span><span class="sxs-lookup"><span data-stu-id="ef774-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="ef774-107">De cmdlet moet de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aanroepen om niet-afsluit fouten te rapporteren wanneer de cmdlet de verwerking van de invoer objecten kan voortzetten.</span><span class="sxs-lookup"><span data-stu-id="ef774-107">Your cmdlet should call the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="ef774-108">Beide methoden bieden een fout record die de hosttoepassing kan gebruiken om de oorzaak van de fout te onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="ef774-108">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="ef774-109">Gebruik de volgende richt lijnen om te bepalen of een fout een afsluitende of niet-afsluit fout is.</span><span class="sxs-lookup"><span data-stu-id="ef774-109">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="ef774-110">Een fout is een afsluit fout als wordt voor komen dat de cmdlet doorgaat met het verwerken van het huidige object of door het verwerken van andere invoer objecten, ongeacht de inhoud.</span><span class="sxs-lookup"><span data-stu-id="ef774-110">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="ef774-111">Een fout wordt beëindigd als u niet wilt dat de cmdlet het huidige object of andere invoer objecten verwerkt, ongeacht de inhoud.</span><span class="sxs-lookup"><span data-stu-id="ef774-111">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="ef774-112">Een fout is een afsluit fout als deze optreedt in een cmdlet die geen object accepteert of retourneert, of als het probleem optreedt in een cmdlet die slechts één object accepteert of retourneert.</span><span class="sxs-lookup"><span data-stu-id="ef774-112">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="ef774-113">Een fout is een niet-afsluit fout als u wilt dat uw cmdlet doorgaat met de verwerking van het huidige object en andere invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="ef774-113">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="ef774-114">Een fout is een niet-afsluit fout als deze is gerelateerd aan een specifiek invoer object of subset van invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="ef774-114">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef774-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ef774-115">See Also</span></span>

[<span data-ttu-id="ef774-116">System. Management. Automation. cmdlet. Throwterminatingerror \*</span><span class="sxs-lookup"><span data-stu-id="ef774-116">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="ef774-117">System. Management. Automation. cmdlet. WriteError</span><span class="sxs-lookup"><span data-stu-id="ef774-117">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="ef774-118">Windows PowerShell-foutrecords</span><span class="sxs-lookup"><span data-stu-id="ef774-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="ef774-119">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="ef774-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
