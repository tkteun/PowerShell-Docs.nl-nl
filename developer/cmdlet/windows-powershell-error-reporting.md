---
title: Windows PowerShell die fouten rapporteren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61b7773a-c346-4835-a928-7212dc4c85bc
caps.latest.revision: 7
ms.openlocfilehash: 259de341fd2fcce2b0c4629f806b4348cba1ff2c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846919"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="7c52f-102">Windows PowerShell-foutrapportage</span><span class="sxs-lookup"><span data-stu-id="7c52f-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="7c52f-103">De onderwerpen in deze sectie bespreken hoe cmdlets fouten rapporteren.</span><span class="sxs-lookup"><span data-stu-id="7c52f-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7c52f-104">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="7c52f-104">In This Section</span></span>

<span data-ttu-id="7c52f-105">[Fout melden concepten](./error-reporting-concepts.md) beschrijft de twee methoden die cmdlets om fouten te melden gebruiken kunt.</span><span class="sxs-lookup"><span data-stu-id="7c52f-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="7c52f-106">[Beëindigen van fouten](./terminating-errors.md) beschrijving van de methode die wordt gebruikt voor het rapporteren van wordt beëindigd wanneer deze methode worden aangeroepen vanuit binnen de cmdlet,-fouten en uitzonderingen die door de Windows PowerShell-runtime kunnen worden geretourneerd wanneer de methode wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="7c52f-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="7c52f-107">[Niet-afsluitfouten](./non-terminating-errors.md) beschrijving van de methode die wordt gebruikt voor het rapporteren van niet-afsluitfouten en waar deze methode kan worden aangeroepen in de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c52f-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="7c52f-108">[Informatie over de fout op categorie weergeven](./displaying-error-information.md) worden beschreven van de manieren kunnen gebruikers fout weergeven.</span><span class="sxs-lookup"><span data-stu-id="7c52f-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="7c52f-109">[Windows PowerShell-foutrecords](./windows-powershell-error-records.md) beschrijft de onderdelen van een foutrecord voor een.</span><span class="sxs-lookup"><span data-stu-id="7c52f-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="7c52f-110">[ErrorRecord objecten interpreteren](./interpreting-errorrecord-objects.md) wordt beschreven hoe ErrorRecord objecten worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="7c52f-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c52f-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7c52f-111">See Also</span></span>

[<span data-ttu-id="7c52f-112">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7c52f-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
