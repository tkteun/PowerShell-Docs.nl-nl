---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-tracesource?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TraceSource
ms.openlocfilehash: d136dd46eaceb65b5c512e3ff5c98e13d685d45e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251096"
---
# <span data-ttu-id="db6ff-103">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="db6ff-103">Get-TraceSource</span></span>

## <span data-ttu-id="db6ff-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="db6ff-104">SYNOPSIS</span></span>
<span data-ttu-id="db6ff-105">Hiermee haalt u Power shell-onderdelen op die worden geinstrumenteerd voor tracering.</span><span class="sxs-lookup"><span data-stu-id="db6ff-105">Gets PowerShell components that are instrumented for tracing.</span></span>

## <span data-ttu-id="db6ff-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="db6ff-106">SYNTAX</span></span>

```
Get-TraceSource [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="db6ff-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="db6ff-107">DESCRIPTION</span></span>

<span data-ttu-id="db6ff-108">De cmdlet **Get-TraceSource** haalt de tracerings bronnen voor Power shell-onderdelen op die momenteel in gebruik zijn.</span><span class="sxs-lookup"><span data-stu-id="db6ff-108">The **Get-TraceSource** cmdlet gets the trace sources for PowerShell components that are currently in use.</span></span>
<span data-ttu-id="db6ff-109">U kunt de gegevens gebruiken om te bepalen welke Power shell-onderdelen u kunt traceren.</span><span class="sxs-lookup"><span data-stu-id="db6ff-109">You can use the data to determine which PowerShell components you can trace.</span></span>
<span data-ttu-id="db6ff-110">Bij tracering genereert het onderdeel gedetailleerde berichten over elke stap in de interne verwerking.</span><span class="sxs-lookup"><span data-stu-id="db6ff-110">When tracing, the component generates detailed messages about each step in its internal processing.</span></span>
<span data-ttu-id="db6ff-111">Ontwikkel aars gebruiken de tracerings gegevens om de gegevens stroom, uitvoering van Program ma's en fouten te bewaken.</span><span class="sxs-lookup"><span data-stu-id="db6ff-111">Developers use the trace data to monitor data flow, program execution, and errors.</span></span>

<span data-ttu-id="db6ff-112">De tracerings-cmdlets zijn ontworpen voor Power shell-ontwikkel aars, maar ze zijn beschikbaar voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="db6ff-112">The tracing cmdlets were designed for PowerShell developers, but they are available to all users.</span></span>

## <span data-ttu-id="db6ff-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="db6ff-113">EXAMPLES</span></span>

### <span data-ttu-id="db6ff-114">Voor beeld 1: tracerings bronnen op naam ophalen</span><span class="sxs-lookup"><span data-stu-id="db6ff-114">Example 1: Get trace sources by name</span></span>

```
PS C:\> Get-TraceSource -Name "*provider*"
```

<span data-ttu-id="db6ff-115">Met deze opdracht worden alle tracerings bronnen opgehaald die de naam van de provider bevatten.</span><span class="sxs-lookup"><span data-stu-id="db6ff-115">This command gets all of the trace sources that have names that include provider.</span></span>

### <span data-ttu-id="db6ff-116">Voor beeld 2: alle tracerings bronnen ophalen</span><span class="sxs-lookup"><span data-stu-id="db6ff-116">Example 2: Get all trace sources</span></span>

```
PS C:\> Get-TraceSource
```

<span data-ttu-id="db6ff-117">Met deze opdracht worden alle Power shell-onderdelen opgehaald die kunnen worden getraceerd.</span><span class="sxs-lookup"><span data-stu-id="db6ff-117">This command gets all of the PowerShell components that can be traced.</span></span>

## <span data-ttu-id="db6ff-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="db6ff-118">PARAMETERS</span></span>

### <span data-ttu-id="db6ff-119">-Name</span><span class="sxs-lookup"><span data-stu-id="db6ff-119">-Name</span></span>

<span data-ttu-id="db6ff-120">Hiermee geeft u de tracerings bronnen op die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="db6ff-120">Specifies the trace sources to get.</span></span>
<span data-ttu-id="db6ff-121">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="db6ff-121">Wildcards are permitted.</span></span>
<span data-ttu-id="db6ff-122">De parameter naam *naam* is optioneel.</span><span class="sxs-lookup"><span data-stu-id="db6ff-122">The parameter name *Name* is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="db6ff-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="db6ff-123">CommonParameters</span></span>

<span data-ttu-id="db6ff-124">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="db6ff-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="db6ff-125">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="db6ff-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="db6ff-126">INVOER</span><span class="sxs-lookup"><span data-stu-id="db6ff-126">INPUTS</span></span>

### <span data-ttu-id="db6ff-127">System. String</span><span class="sxs-lookup"><span data-stu-id="db6ff-127">System.String</span></span>

<span data-ttu-id="db6ff-128">U kunt een teken reeks die de naam van een tracerings bron bevat, door sluizen als **Get-TraceSource**.</span><span class="sxs-lookup"><span data-stu-id="db6ff-128">You can pipe a string that contains the name of a trace source to **Get-TraceSource**.</span></span>

## <span data-ttu-id="db6ff-129">UITVOER</span><span class="sxs-lookup"><span data-stu-id="db6ff-129">OUTPUTS</span></span>

### <span data-ttu-id="db6ff-130">System. Management. Automation. PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="db6ff-130">System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="db6ff-131">**Get-TraceSource** retourneert objecten die de traceer bronnen vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="db6ff-131">**Get-TraceSource** returns objects that represent the trace sources.</span></span>

## <span data-ttu-id="db6ff-132">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="db6ff-132">NOTES</span></span>

## <span data-ttu-id="db6ff-133">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="db6ff-133">RELATED LINKS</span></span>

[<span data-ttu-id="db6ff-134">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="db6ff-134">Set-TraceSource</span></span>](Set-TraceSource.md)

[<span data-ttu-id="db6ff-135">Tracering-opdracht</span><span class="sxs-lookup"><span data-stu-id="db6ff-135">Trace-Command</span></span>](Trace-Command.md)
