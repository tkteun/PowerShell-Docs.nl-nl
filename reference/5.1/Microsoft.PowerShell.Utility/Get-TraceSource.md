---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-tracesource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TraceSource
ms.openlocfilehash: 7d57e7cff0dc3ca0eff36dbe38e240efdd324060
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250426"
---
# <span data-ttu-id="9fbb0-103">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="9fbb0-103">Get-TraceSource</span></span>

## <span data-ttu-id="9fbb0-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9fbb0-104">SYNOPSIS</span></span>
<span data-ttu-id="9fbb0-105">Hiermee haalt u Power shell-onderdelen op die worden geinstrumenteerd voor tracering.</span><span class="sxs-lookup"><span data-stu-id="9fbb0-105">Gets PowerShell components that are instrumented for tracing.</span></span>

## <span data-ttu-id="9fbb0-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9fbb0-106">SYNTAX</span></span>

```
Get-TraceSource [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="9fbb0-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9fbb0-107">DESCRIPTION</span></span>

<span data-ttu-id="9fbb0-108">De cmdlet **Get-TraceSource** haalt de tracerings bronnen voor Power shell-onderdelen op die momenteel in gebruik zijn.</span><span class="sxs-lookup"><span data-stu-id="9fbb0-108">The **Get-TraceSource** cmdlet gets the trace sources for PowerShell components that are currently in use.</span></span>
<span data-ttu-id="9fbb0-109">U kunt de gegevens gebruiken om te bepalen welke Power shell-onderdelen u kunt traceren.</span><span class="sxs-lookup"><span data-stu-id="9fbb0-109">You can use the data to determine which PowerShell components you can trace.</span></span>
<span data-ttu-id="9fbb0-110">Bij tracering genereert het onderdeel gedetailleerde berichten over elke stap in de interne verwerking.</span><span class="sxs-lookup"><span data-stu-id="9fbb0-110">When tracing, the component generates detailed messages about each step in its internal processing.</span></span>
<span data-ttu-id="9fbb0-111">Ontwikkel aars gebruiken de tracerings gegevens om de gegevens stroom, uitvoering van Program ma's en fouten te bewaken.</span><span class="sxs-lookup"><span data-stu-id="9fbb0-111">Developers use the trace data to monitor data flow, program execution, and errors.</span></span>

<span data-ttu-id="9fbb0-112">De tracerings-cmdlets zijn ontworpen voor Power shell-ontwikkel aars, maar ze zijn beschikbaar voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="9fbb0-112">The tracing cmdlets were designed for PowerShell developers, but they are available to all users.</span></span>

## <span data-ttu-id="9fbb0-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9fbb0-113">EXAMPLES</span></span>

### <span data-ttu-id="9fbb0-114">Voor beeld 1: tracerings bronnen op naam ophalen</span><span class="sxs-lookup"><span data-stu-id="9fbb0-114">Example 1: Get trace sources by name</span></span>

```
PS C:\> Get-TraceSource -Name "*provider*"
```

<span data-ttu-id="9fbb0-115">Met deze opdracht worden alle tracerings bronnen opgehaald die de naam van de provider bevatten.</span><span class="sxs-lookup"><span data-stu-id="9fbb0-115">This command gets all of the trace sources that have names that include provider.</span></span>

### <span data-ttu-id="9fbb0-116">Voor beeld 2: alle tracerings bronnen ophalen</span><span class="sxs-lookup"><span data-stu-id="9fbb0-116">Example 2: Get all trace sources</span></span>

```
PS C:\> Get-TraceSource
```

<span data-ttu-id="9fbb0-117">Met deze opdracht worden alle Power shell-onderdelen opgehaald die kunnen worden getraceerd.</span><span class="sxs-lookup"><span data-stu-id="9fbb0-117">This command gets all of the PowerShell components that can be traced.</span></span>

## <span data-ttu-id="9fbb0-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9fbb0-118">PARAMETERS</span></span>

### <span data-ttu-id="9fbb0-119">-Name</span><span class="sxs-lookup"><span data-stu-id="9fbb0-119">-Name</span></span>

<span data-ttu-id="9fbb0-120">Hiermee geeft u de tracerings bronnen op die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9fbb0-120">Specifies the trace sources to get.</span></span>
<span data-ttu-id="9fbb0-121">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="9fbb0-121">Wildcards are permitted.</span></span>
<span data-ttu-id="9fbb0-122">De parameter naam *naam* is optioneel.</span><span class="sxs-lookup"><span data-stu-id="9fbb0-122">The parameter name *Name* is optional.</span></span>

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

### <span data-ttu-id="9fbb0-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9fbb0-123">CommonParameters</span></span>

<span data-ttu-id="9fbb0-124">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9fbb0-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9fbb0-125">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9fbb0-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9fbb0-126">INVOER</span><span class="sxs-lookup"><span data-stu-id="9fbb0-126">INPUTS</span></span>

### <span data-ttu-id="9fbb0-127">System. String</span><span class="sxs-lookup"><span data-stu-id="9fbb0-127">System.String</span></span>

<span data-ttu-id="9fbb0-128">U kunt een teken reeks die de naam van een tracerings bron bevat, door sluizen als **Get-TraceSource**.</span><span class="sxs-lookup"><span data-stu-id="9fbb0-128">You can pipe a string that contains the name of a trace source to **Get-TraceSource**.</span></span>

## <span data-ttu-id="9fbb0-129">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9fbb0-129">OUTPUTS</span></span>

### <span data-ttu-id="9fbb0-130">System. Management. Automation. PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="9fbb0-130">System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="9fbb0-131">**Get-TraceSource** retourneert objecten die de traceer bronnen vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="9fbb0-131">**Get-TraceSource** returns objects that represent the trace sources.</span></span>

## <span data-ttu-id="9fbb0-132">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9fbb0-132">NOTES</span></span>

## <span data-ttu-id="9fbb0-133">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9fbb0-133">RELATED LINKS</span></span>

[<span data-ttu-id="9fbb0-134">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="9fbb0-134">Set-TraceSource</span></span>](Set-TraceSource.md)

[<span data-ttu-id="9fbb0-135">Tracering-opdracht</span><span class="sxs-lookup"><span data-stu-id="9fbb0-135">Trace-Command</span></span>](Trace-Command.md)
