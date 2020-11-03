---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pswsmancombinedtrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSWSManCombinedTrace
ms.openlocfilehash: 4a00b843e5e4ec73cf98f4c924ca24a3e1ee0700
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93249322"
---
# <span data-ttu-id="e8d5b-103">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="e8d5b-103">Disable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="e8d5b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e8d5b-104">SYNOPSIS</span></span>
<span data-ttu-id="e8d5b-105">Stop de logboek registratie sessie die is gestart door Enable-PSWSManCombinedTrace.</span><span class="sxs-lookup"><span data-stu-id="e8d5b-105">Stop the logging session started by Enable-PSWSManCombinedTrace.</span></span>

## <span data-ttu-id="e8d5b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e8d5b-106">SYNTAX</span></span>

```
Disable-PSWSManCombinedTrace [<CommonParameters>]
```

## <span data-ttu-id="e8d5b-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e8d5b-107">DESCRIPTION</span></span>

<span data-ttu-id="e8d5b-108">Met deze cmdlet wordt de logboek registratie sessie gestopt door `Enable-PSWSManCombinedTrace` .</span><span class="sxs-lookup"><span data-stu-id="e8d5b-108">This cmdlet stops the logging session started by `Enable-PSWSManCombinedTrace`.</span></span>

<span data-ttu-id="e8d5b-109">Deze cmdlet maakt gebruik van de `Stop-Trace` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e8d5b-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="e8d5b-110">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="e8d5b-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="e8d5b-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e8d5b-111">EXAMPLES</span></span>

### <span data-ttu-id="e8d5b-112">Voor beeld 1: de gecombineerde logboek registratie sessie uitschakelen</span><span class="sxs-lookup"><span data-stu-id="e8d5b-112">Example 1: Disable the combined logging session</span></span>

```powershell
Disable-PSWSManCombinedTrace
```

## <span data-ttu-id="e8d5b-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e8d5b-113">PARAMETERS</span></span>

### <span data-ttu-id="e8d5b-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e8d5b-114">CommonParameters</span></span>

<span data-ttu-id="e8d5b-115">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e8d5b-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e8d5b-116">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e8d5b-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e8d5b-117">INVOER</span><span class="sxs-lookup"><span data-stu-id="e8d5b-117">INPUTS</span></span>

### <span data-ttu-id="e8d5b-118">Geen</span><span class="sxs-lookup"><span data-stu-id="e8d5b-118">None</span></span>

## <span data-ttu-id="e8d5b-119">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e8d5b-119">OUTPUTS</span></span>

### <span data-ttu-id="e8d5b-120">Geen</span><span class="sxs-lookup"><span data-stu-id="e8d5b-120">None</span></span>

## <span data-ttu-id="e8d5b-121">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e8d5b-121">NOTES</span></span>

## <span data-ttu-id="e8d5b-122">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e8d5b-122">RELATED LINKS</span></span>

[<span data-ttu-id="e8d5b-123">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="e8d5b-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="e8d5b-124">Stoppen-traceren</span><span class="sxs-lookup"><span data-stu-id="e8d5b-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="e8d5b-125">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="e8d5b-125">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)
