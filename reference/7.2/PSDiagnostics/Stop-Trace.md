---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/stop-trace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Trace
ms.openlocfilehash: 5727ae52326830fa16012722d0b801b7d43e50dd
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705416"
---
# <span data-ttu-id="e2f8b-102">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="e2f8b-102">Stop-Trace</span></span>

## <span data-ttu-id="e2f8b-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e2f8b-103">SYNOPSIS</span></span>
<span data-ttu-id="e2f8b-104">Stop een logboek registratie sessie voor gebeurtenis tracering.</span><span class="sxs-lookup"><span data-stu-id="e2f8b-104">Stop an Event Trace logging session.</span></span>

## <span data-ttu-id="e2f8b-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e2f8b-105">SYNTAX</span></span>

```
Stop-Trace [-SessionName] <Object> [-ETS] [<CommonParameters>]
```

## <span data-ttu-id="e2f8b-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e2f8b-106">DESCRIPTION</span></span>

<span data-ttu-id="e2f8b-107">Met deze cmdlet wordt een Windows-sessie voor logboek registratie van gebeurtenissen gestopt.</span><span class="sxs-lookup"><span data-stu-id="e2f8b-107">This cmdlet stops a Windows Event Trace logging session.</span></span>

<span data-ttu-id="e2f8b-108">Deze cmdlet wordt gebruikt door de volgende cmdlets:</span><span class="sxs-lookup"><span data-stu-id="e2f8b-108">This cmdlet is used by the following cmdlets:</span></span>

- `Disable-PSWSManCombinedTrace`
- `Disable-WSManTrace`

<span data-ttu-id="e2f8b-109">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="e2f8b-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="e2f8b-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e2f8b-110">EXAMPLES</span></span>

### <span data-ttu-id="e2f8b-111">Voor beeld 1: een sessie met WSMan-traceer logboeken stoppen</span><span class="sxs-lookup"><span data-stu-id="e2f8b-111">Example 1: Stop a WSMan Trace logging session</span></span>

```powershell
Stop-Trace -SessionName 'wsmlog'
```

## <span data-ttu-id="e2f8b-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e2f8b-112">PARAMETERS</span></span>

### <span data-ttu-id="e2f8b-113">-ETS</span><span class="sxs-lookup"><span data-stu-id="e2f8b-113">-ETS</span></span>
<span data-ttu-id="e2f8b-114">Opdrachten zonder opslaan of plannen rechtstreeks naar Gebeurtenissessies Trace kunnen verzenden.</span><span class="sxs-lookup"><span data-stu-id="e2f8b-114">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

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

### <span data-ttu-id="e2f8b-115">-Sessie naam</span><span class="sxs-lookup"><span data-stu-id="e2f8b-115">-SessionName</span></span>
<span data-ttu-id="e2f8b-116">De naam van de gebeurtenis tracerings sessie die moet worden gestopt.</span><span class="sxs-lookup"><span data-stu-id="e2f8b-116">The name of the Event Trace session to be stopped.</span></span>

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

### <span data-ttu-id="e2f8b-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e2f8b-117">CommonParameters</span></span>
<span data-ttu-id="e2f8b-118">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e2f8b-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e2f8b-119">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e2f8b-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e2f8b-120">INVOER</span><span class="sxs-lookup"><span data-stu-id="e2f8b-120">INPUTS</span></span>

### <span data-ttu-id="e2f8b-121">Geen</span><span class="sxs-lookup"><span data-stu-id="e2f8b-121">None</span></span>

## <span data-ttu-id="e2f8b-122">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e2f8b-122">OUTPUTS</span></span>

### <span data-ttu-id="e2f8b-123">Geen</span><span class="sxs-lookup"><span data-stu-id="e2f8b-123">None</span></span>

## <span data-ttu-id="e2f8b-124">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e2f8b-124">NOTES</span></span>

## <span data-ttu-id="e2f8b-125">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e2f8b-125">RELATED LINKS</span></span>

[<span data-ttu-id="e2f8b-126">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="e2f8b-126">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="e2f8b-127">Start-traceren</span><span class="sxs-lookup"><span data-stu-id="e2f8b-127">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="e2f8b-128">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="e2f8b-128">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="e2f8b-129">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="e2f8b-129">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="e2f8b-130">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="e2f8b-130">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="e2f8b-131">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="e2f8b-131">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)

