---
title: Bijlage A-Help-syntaxis
description: In dit artikel wordt uitgelegd hoe u de syntaxis van een cmdlet die wordt weer gegeven door Get-Help, kunt lezen en begrijpen.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: b8fe218f2a9af1ad1ee6b88740414ecede0194bd
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98216107"
---
# <a name="appendix-a---help-syntax"></a><span data-ttu-id="80f5d-103">Bijlage A-Help-syntaxis</span><span class="sxs-lookup"><span data-stu-id="80f5d-103">Appendix A - Help Syntax</span></span>

<span data-ttu-id="80f5d-104">In het volgende voor beeld wordt de sectie **syntaxis** van de Help voor de cmdlet weer gegeven `Get-EventLog` .</span><span class="sxs-lookup"><span data-stu-id="80f5d-104">The following example shows the **SYNTAX** section of the help for the `Get-EventLog` cmdlet.</span></span>

```powershell
help Get-EventLog
```

```Output
NAME
    Get-EventLog

SYNOPSIS
    Gets the events in an event log, or a list of the event logs, on the local or remote
    computers.


SYNTAX
    Get-EventLog [-LogName] <String> [[-InstanceId] <Int64[]>] [-After <DateTime>]
    [-AsBaseObject] [-Before <DateTime>] [-ComputerName <String[]>] [-EntryType {Error |
    Information | FailureAudit | SuccessAudit | Warning}] [-Index <Int32[]>] [-Message
    <String>] [-Newest <Int32>] [-Source <String[]>] [-UserName <String[]>]
    [<CommonParameters>]

    Get-EventLog [-AsString] [-ComputerName <String[]>] [-List] [<CommonParameters>]
```

<span data-ttu-id="80f5d-105">In dit voor beeld wordt alleen het relevante gedeelte van de Help weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="80f5d-105">Only the relevant portion of the help is shown in this example.</span></span>

<span data-ttu-id="80f5d-106">De syntaxis bestaat voornamelijk uit verschillende sets openings-en afsluit haken ( `[]` ).</span><span class="sxs-lookup"><span data-stu-id="80f5d-106">The syntax is primarily made up of several sets of opening and closing brackets (`[]`).</span></span> <span data-ttu-id="80f5d-107">Er zijn twee verschillende betekenissen, afhankelijk van hoe ze worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="80f5d-107">These have two different meanings depending on how they're used.</span></span> <span data-ttu-id="80f5d-108">Alles tussen vier Kante haken is optioneel, tenzij ze een set lege vier Kante haken zijn `[]` .</span><span class="sxs-lookup"><span data-stu-id="80f5d-108">Anything contained within square brackets is optional unless they're a set of empty square brackets `[]`.</span></span> <span data-ttu-id="80f5d-109">Lege vier Kante haken worden alleen weer gegeven na een gegevens type zoals `<string[]>` .</span><span class="sxs-lookup"><span data-stu-id="80f5d-109">Empty square brackets only appear after a datatype such as `<string[]>`.</span></span> <span data-ttu-id="80f5d-110">Dit betekent dat bepaalde para meters meer dan één waarde van dat type kunnen accepteren.</span><span class="sxs-lookup"><span data-stu-id="80f5d-110">This means that particular parameter can accept more than one value of that type.</span></span>

<span data-ttu-id="80f5d-111">De eerste para meter in de eerste para meter set van `Get-EventLog` is **LogName**.</span><span class="sxs-lookup"><span data-stu-id="80f5d-111">The first parameter in the first parameter set of `Get-EventLog` is **LogName**.</span></span> <span data-ttu-id="80f5d-112">LogName wordt tussen vier Kante haken geplaatst, wat betekent dat het een positionele para meter is.</span><span class="sxs-lookup"><span data-stu-id="80f5d-112">LogName is surrounded by square brackets which means that it's a positional parameter.</span></span> <span data-ttu-id="80f5d-113">Met andere woorden, waarbij u de naam van de para meter zelf opgeeft, is optioneel zolang deze is opgegeven op de juiste positie.</span><span class="sxs-lookup"><span data-stu-id="80f5d-113">In other words, specifying the name of the parameter itself is optional as long as it's specified in the correct position.</span></span> <span data-ttu-id="80f5d-114">De informatie in de punt haken ( `<>` ) na de parameter naam geeft aan dat er een enkele **teken reeks** waarde nodig is.</span><span class="sxs-lookup"><span data-stu-id="80f5d-114">The information in the angle brackets (`<>`) after the parameter name indicates that it needs a single **string** value.</span></span> <span data-ttu-id="80f5d-115">De volledige parameter naam en het gegevens type worden niet tussen vier Kante haken geplaatst, dus de para meter **LogName** is vereist wanneer u deze para meter set gebruikt.</span><span class="sxs-lookup"><span data-stu-id="80f5d-115">The entire parameter name and datatype are not surrounded by square brackets so the **LogName** parameter is required when using this parameter set.</span></span>

```powershell
Get-EventLog [-LogName] <String>
```

<span data-ttu-id="80f5d-116">De tweede para meter is **InstanceId**.</span><span class="sxs-lookup"><span data-stu-id="80f5d-116">The second parameter is **InstanceId**.</span></span> <span data-ttu-id="80f5d-117">U ziet dat de parameter naam en het gegevens type beide volledig tussen vier Kante haken staan.</span><span class="sxs-lookup"><span data-stu-id="80f5d-117">Notice that the parameter name and the datatype are both completely surrounded by square brackets.</span></span> <span data-ttu-id="80f5d-118">Dit betekent dat de **InstanceId** -para meter optioneel is, niet verplicht.</span><span class="sxs-lookup"><span data-stu-id="80f5d-118">This means that the **InstanceId** parameter is optional, not mandatory.</span></span> <span data-ttu-id="80f5d-119">U ziet ook dat **InstanceId** wordt omgeven door een eigen set vier Kante haken.</span><span class="sxs-lookup"><span data-stu-id="80f5d-119">Also notice that **InstanceId** is surrounded by its own set of square brackets.</span></span> <span data-ttu-id="80f5d-120">Net als bij de para meter **LogName** betekent dit dat de para meter positioneel is.</span><span class="sxs-lookup"><span data-stu-id="80f5d-120">As with the **LogName** parameter, this means the parameter is positional.</span></span> <span data-ttu-id="80f5d-121">Er is een laatste set vier Kante haakjes achter het gegevens type.</span><span class="sxs-lookup"><span data-stu-id="80f5d-121">There's one last set of square brackets after the datatype.</span></span> <span data-ttu-id="80f5d-122">Dit betekent dat het meer dan één waarde kan accepteren in de vorm van een matrix of een door komma's gescheiden lijst.</span><span class="sxs-lookup"><span data-stu-id="80f5d-122">This means that it can accept more than one value in the form of an array or a comma-separated list.</span></span>

```
[[-InstanceId] <Int64[]>]
```

<span data-ttu-id="80f5d-123">De tweede parameterset heeft een **lijst** parameter.</span><span class="sxs-lookup"><span data-stu-id="80f5d-123">The second parameter set has a **List** parameter.</span></span> <span data-ttu-id="80f5d-124">Het is een switch parameter omdat er geen gegevens type is volgens de parameter naam.</span><span class="sxs-lookup"><span data-stu-id="80f5d-124">It's a switch parameter because there's no datatype following the parameter name.</span></span> <span data-ttu-id="80f5d-125">Wanneer de **lijst** parameter is opgegeven, is de waarde **True**.</span><span class="sxs-lookup"><span data-stu-id="80f5d-125">When the **List** parameter is specified, the value is **True**.</span></span> <span data-ttu-id="80f5d-126">Wanneer deze niet is opgegeven, is de waarde **False**.</span><span class="sxs-lookup"><span data-stu-id="80f5d-126">When it's not specified, the value is **False**.</span></span>

```
[-List]
```

<span data-ttu-id="80f5d-127">De syntaxis gegevens voor een opdracht kunnen ook worden opgehaald met `Get-Command` behulp van de **syntaxis** parameter.</span><span class="sxs-lookup"><span data-stu-id="80f5d-127">The syntax information for a command can also be retrieved using `Get-Command` using the **Syntax** parameter.</span></span> <span data-ttu-id="80f5d-128">Dit is een handige snelkoppeling die ik altijd gebruik.</span><span class="sxs-lookup"><span data-stu-id="80f5d-128">This is a handy shortcut that I use all the time.</span></span> <span data-ttu-id="80f5d-129">Zo kunt u snel zien hoe u een opdracht kunt gebruiken zonder dat u meerdere pagina's met Help-informatie hoeft te door lopen.</span><span class="sxs-lookup"><span data-stu-id="80f5d-129">It allows me to quickly learn how to use a command without having to sift through multiple pages of help information.</span></span> <span data-ttu-id="80f5d-130">Als ik meer informatie nodig heb, keer ik terug naar het gebruik van de werkelijke Help-inhoud.</span><span class="sxs-lookup"><span data-stu-id="80f5d-130">If I end up needing more information, then I'll revert to using the actual help content.</span></span>

```powershell
Get-Command -Name Get-EventLog -Syntax
```

```Output
Get-EventLog [-LogName] <string> [[-InstanceId] <long[]>] [-ComputerName <string[]>] [-Newest <int>]
 [-After <datetime>] [-Before <datetime>] [-UserName <string[]>] [-Index <int[]> ]
 [-EntryType <string[]>] [-Source <string[]>] [-Message <string>] [-AsBaseObject]
 [<CommonParameters>]

Get-EventLog [-ComputerName <string[]>] [-List] [-AsString] [<CommonParameters>]
```

<span data-ttu-id="80f5d-131">Hoe meer u het Help-systeem in Power shell gebruikt, hoe eenvoudiger alle verschillende nuances worden onthouden.</span><span class="sxs-lookup"><span data-stu-id="80f5d-131">The more you use the help system in PowerShell, the easier remembering all of the different nuances becomes.</span></span> <span data-ttu-id="80f5d-132">Voordat u het weet, wordt het gebruik van de tweede aard.</span><span class="sxs-lookup"><span data-stu-id="80f5d-132">Before you know it, using it becomes second nature.</span></span>
