---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-tracesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TraceSource
ms.openlocfilehash: c196d00359c9b20b5dc1fefc0ab2b94655703f6f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705931"
---
# <span data-ttu-id="2a674-102">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="2a674-102">Get-TraceSource</span></span>

## <span data-ttu-id="2a674-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2a674-103">SYNOPSIS</span></span>
<span data-ttu-id="2a674-104">Hiermee haalt u Power shell-onderdelen op die worden geinstrumenteerd voor tracering.</span><span class="sxs-lookup"><span data-stu-id="2a674-104">Gets PowerShell components that are instrumented for tracing.</span></span>

## <span data-ttu-id="2a674-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2a674-105">SYNTAX</span></span>

```
Get-TraceSource [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="2a674-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2a674-106">DESCRIPTION</span></span>

<span data-ttu-id="2a674-107">De cmdlet **Get-TraceSource** haalt de tracerings bronnen voor Power shell-onderdelen op die momenteel in gebruik zijn.</span><span class="sxs-lookup"><span data-stu-id="2a674-107">The **Get-TraceSource** cmdlet gets the trace sources for PowerShell components that are currently in use.</span></span>
<span data-ttu-id="2a674-108">U kunt de gegevens gebruiken om te bepalen welke Power shell-onderdelen u kunt traceren.</span><span class="sxs-lookup"><span data-stu-id="2a674-108">You can use the data to determine which PowerShell components you can trace.</span></span>
<span data-ttu-id="2a674-109">Bij tracering genereert het onderdeel gedetailleerde berichten over elke stap in de interne verwerking.</span><span class="sxs-lookup"><span data-stu-id="2a674-109">When tracing, the component generates detailed messages about each step in its internal processing.</span></span>
<span data-ttu-id="2a674-110">Ontwikkel aars gebruiken de tracerings gegevens om de gegevens stroom, uitvoering van Program ma's en fouten te bewaken.</span><span class="sxs-lookup"><span data-stu-id="2a674-110">Developers use the trace data to monitor data flow, program execution, and errors.</span></span>

<span data-ttu-id="2a674-111">De tracerings-cmdlets zijn ontworpen voor Power shell-ontwikkel aars, maar ze zijn beschikbaar voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="2a674-111">The tracing cmdlets were designed for PowerShell developers, but they are available to all users.</span></span>

## <span data-ttu-id="2a674-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2a674-112">EXAMPLES</span></span>

### <span data-ttu-id="2a674-113">Voor beeld 1: tracerings bronnen op naam ophalen</span><span class="sxs-lookup"><span data-stu-id="2a674-113">Example 1: Get trace sources by name</span></span>

```
PS C:\> Get-TraceSource -Name "*provider*"
```

<span data-ttu-id="2a674-114">Met deze opdracht worden alle tracerings bronnen opgehaald die de naam van de provider bevatten.</span><span class="sxs-lookup"><span data-stu-id="2a674-114">This command gets all of the trace sources that have names that include provider.</span></span>

### <span data-ttu-id="2a674-115">Voor beeld 2: alle tracerings bronnen ophalen</span><span class="sxs-lookup"><span data-stu-id="2a674-115">Example 2: Get all trace sources</span></span>

```
PS C:\> Get-TraceSource
```

<span data-ttu-id="2a674-116">Met deze opdracht worden alle Power shell-onderdelen opgehaald die kunnen worden getraceerd.</span><span class="sxs-lookup"><span data-stu-id="2a674-116">This command gets all of the PowerShell components that can be traced.</span></span>

## <span data-ttu-id="2a674-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2a674-117">PARAMETERS</span></span>

### <span data-ttu-id="2a674-118">-Name</span><span class="sxs-lookup"><span data-stu-id="2a674-118">-Name</span></span>

<span data-ttu-id="2a674-119">Hiermee geeft u de tracerings bronnen op die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2a674-119">Specifies the trace sources to get.</span></span>
<span data-ttu-id="2a674-120">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="2a674-120">Wildcards are permitted.</span></span>
<span data-ttu-id="2a674-121">De parameter naam *naam* is optioneel.</span><span class="sxs-lookup"><span data-stu-id="2a674-121">The parameter name *Name* is optional.</span></span>

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

### <span data-ttu-id="2a674-122">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2a674-122">CommonParameters</span></span>

<span data-ttu-id="2a674-123">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2a674-123">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2a674-124">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2a674-124">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2a674-125">INVOER</span><span class="sxs-lookup"><span data-stu-id="2a674-125">INPUTS</span></span>

### <span data-ttu-id="2a674-126">System. String</span><span class="sxs-lookup"><span data-stu-id="2a674-126">System.String</span></span>

<span data-ttu-id="2a674-127">U kunt een teken reeks die de naam van een tracerings bron bevat, door sluizen als **Get-TraceSource**.</span><span class="sxs-lookup"><span data-stu-id="2a674-127">You can pipe a string that contains the name of a trace source to **Get-TraceSource**.</span></span>

## <span data-ttu-id="2a674-128">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2a674-128">OUTPUTS</span></span>

### <span data-ttu-id="2a674-129">System. Management. Automation. PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="2a674-129">System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="2a674-130">**Get-TraceSource** retourneert objecten die de traceer bronnen vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="2a674-130">**Get-TraceSource** returns objects that represent the trace sources.</span></span>

## <span data-ttu-id="2a674-131">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2a674-131">NOTES</span></span>

## <span data-ttu-id="2a674-132">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2a674-132">RELATED LINKS</span></span>

[<span data-ttu-id="2a674-133">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="2a674-133">Set-TraceSource</span></span>](Set-TraceSource.md)

[<span data-ttu-id="2a674-134">Tracering-opdracht</span><span class="sxs-lookup"><span data-stu-id="2a674-134">Trace-Command</span></span>](Trace-Command.md)

