---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/stop-trace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Trace
ms.openlocfilehash: 2629ae1beb722282065e76600174b511bfe5fbc9
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249738"
---
# <span data-ttu-id="5deac-103">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="5deac-103">Stop-Trace</span></span>

## <span data-ttu-id="5deac-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="5deac-104">SYNOPSIS</span></span>
<span data-ttu-id="5deac-105">Stop een logboek registratie sessie voor gebeurtenis tracering.</span><span class="sxs-lookup"><span data-stu-id="5deac-105">Stop an Event Trace logging session.</span></span>

## <span data-ttu-id="5deac-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="5deac-106">SYNTAX</span></span>

```
Stop-Trace [-SessionName] <Object> [-ETS] [<CommonParameters>]
```

## <span data-ttu-id="5deac-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5deac-107">DESCRIPTION</span></span>

<span data-ttu-id="5deac-108">Met deze cmdlet wordt een Windows-sessie voor logboek registratie van gebeurtenissen gestopt.</span><span class="sxs-lookup"><span data-stu-id="5deac-108">This cmdlet stops a Windows Event Trace logging session.</span></span>

<span data-ttu-id="5deac-109">Deze cmdlet wordt gebruikt door de volgende cmdlets:</span><span class="sxs-lookup"><span data-stu-id="5deac-109">This cmdlet is used by the following cmdlets:</span></span>

- `Disable-PSWSManCombinedTrace`
- `Disable-WSManTrace`

<span data-ttu-id="5deac-110">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="5deac-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="5deac-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="5deac-111">EXAMPLES</span></span>

### <span data-ttu-id="5deac-112">Voor beeld 1: een sessie met WSMan-traceer logboeken stoppen</span><span class="sxs-lookup"><span data-stu-id="5deac-112">Example 1: Stop a WSMan Trace logging session</span></span>

```powershell
Stop-Trace -SessionName 'wsmlog'
```

## <span data-ttu-id="5deac-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5deac-113">PARAMETERS</span></span>

### <span data-ttu-id="5deac-114">-ETS</span><span class="sxs-lookup"><span data-stu-id="5deac-114">-ETS</span></span>
<span data-ttu-id="5deac-115">Opdrachten zonder opslaan of plannen rechtstreeks naar Gebeurtenissessies Trace kunnen verzenden.</span><span class="sxs-lookup"><span data-stu-id="5deac-115">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5deac-116">-Sessie naam</span><span class="sxs-lookup"><span data-stu-id="5deac-116">-SessionName</span></span>
<span data-ttu-id="5deac-117">De naam van de gebeurtenis tracerings sessie die moet worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="5deac-117">The name of the Event Trace session to be stopped.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5deac-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5deac-118">CommonParameters</span></span>
<span data-ttu-id="5deac-119">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5deac-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5deac-120">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5deac-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5deac-121">INVOER</span><span class="sxs-lookup"><span data-stu-id="5deac-121">INPUTS</span></span>

### <span data-ttu-id="5deac-122">Geen</span><span class="sxs-lookup"><span data-stu-id="5deac-122">None</span></span>

## <span data-ttu-id="5deac-123">UITVOER</span><span class="sxs-lookup"><span data-stu-id="5deac-123">OUTPUTS</span></span>

### <span data-ttu-id="5deac-124">Geen</span><span class="sxs-lookup"><span data-stu-id="5deac-124">None</span></span>

## <span data-ttu-id="5deac-125">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="5deac-125">NOTES</span></span>

## <span data-ttu-id="5deac-126">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="5deac-126">RELATED LINKS</span></span>

[<span data-ttu-id="5deac-127">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="5deac-127">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="5deac-128">Start-traceren</span><span class="sxs-lookup"><span data-stu-id="5deac-128">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="5deac-129">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="5deac-129">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="5deac-130">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="5deac-130">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="5deac-131">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="5deac-131">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="5deac-132">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="5deac-132">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)