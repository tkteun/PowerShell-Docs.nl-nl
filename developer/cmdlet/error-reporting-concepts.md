---
title: Concepten voor foutrapportage | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: 2f185e415e3effc2cf09a282ca1167e3bcfb7d6a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068178"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="c491b-102">Concepten voor foutrapportage</span><span class="sxs-lookup"><span data-stu-id="c491b-102">Error Reporting Concepts</span></span>

<span data-ttu-id="c491b-103">Windows PowerShell biedt twee methoden voor die fouten rapporteren: een mechanisme voor *wordt beëindigd fouten* en een ander mechanisme voor *niet-afsluitfouten*.</span><span class="sxs-lookup"><span data-stu-id="c491b-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="c491b-104">Het is goed belangrijk voor uw cmdlet fouten rapporteren zodat de hosttoepassing die uw cmdlets wordt uitgevoerd op de juiste manier kan reageren.</span><span class="sxs-lookup"><span data-stu-id="c491b-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="c491b-105">De cmdlet moet aanroepen de [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) methode wanneer er een fout optreedt die niet bestaat of kunt u voorkomen dat de cmdlet om door te gaan voor het verwerken van de invoer-objecten.</span><span class="sxs-lookup"><span data-stu-id="c491b-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="c491b-106">De cmdlet moet aanroepen de [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode voor het rapporteren van niet-afsluitfouten wanneer de cmdlet kunt doorgaan met het verwerken van de invoer-objecten.</span><span class="sxs-lookup"><span data-stu-id="c491b-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="c491b-107">Beide methoden bieden een foutrecord die de host-toepassing gebruiken kunt om de oorzaak van de fout onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="c491b-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="c491b-108">Gebruik de volgende richtlijnen om te bepalen of een fout wordt een afsluitende of niet-afsluitfout.</span><span class="sxs-lookup"><span data-stu-id="c491b-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="c491b-109">Een fout is een afsluitfout als deze wordt voorkomen uw cmdlet dat voortgezet voor het verwerken van het huidige object of verwerken, is verdere invoer objecten, ongeacht hun inhoud.</span><span class="sxs-lookup"><span data-stu-id="c491b-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="c491b-110">Een fout is een afsluitfout als u de cmdlet niet wilt doorgaan met het verwerken van het huidige object of eventuele verdere invoer objecten, ongeacht hun inhoud.</span><span class="sxs-lookup"><span data-stu-id="c491b-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="c491b-111">Een fout is een afsluitfout als dit zich voordoet in een cmdlet die niet wordt geaccepteerd of een object geretourneerd of als het vindt plaats in een cmdlet die accepteert of slechts één object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c491b-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="c491b-112">Een fout is een niet-afsluitfout als u de cmdlet wilt doorgaan met het verwerken van het huidige object en alle verdere invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="c491b-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="c491b-113">Een fout is een niet-afsluitfout als deze is gekoppeld aan een specifieke invoer object of een subset van de invoer-objecten.</span><span class="sxs-lookup"><span data-stu-id="c491b-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="c491b-114">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c491b-114">See Also</span></span>

[<span data-ttu-id="c491b-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span><span class="sxs-lookup"><span data-stu-id="c491b-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="c491b-116">System.Management.Automation.Cmdlet.WriteError</span><span class="sxs-lookup"><span data-stu-id="c491b-116">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="c491b-117">Windows PowerShell-foutrecords</span><span class="sxs-lookup"><span data-stu-id="c491b-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="c491b-118">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c491b-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
