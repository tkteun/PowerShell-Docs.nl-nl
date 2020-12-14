---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pswsmancombinedtrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSWSManCombinedTrace
ms.openlocfilehash: 690a8b050fd0e16033a585df210db340f41a83a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704713"
---
# <span data-ttu-id="01ced-102">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="01ced-102">Disable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="01ced-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="01ced-103">SYNOPSIS</span></span>
<span data-ttu-id="01ced-104">Stop de logboek registratie sessie die is gestart door Enable-PSWSManCombinedTrace.</span><span class="sxs-lookup"><span data-stu-id="01ced-104">Stop the logging session started by Enable-PSWSManCombinedTrace.</span></span>

## <span data-ttu-id="01ced-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="01ced-105">SYNTAX</span></span>

```
Disable-PSWSManCombinedTrace [<CommonParameters>]
```

## <span data-ttu-id="01ced-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="01ced-106">DESCRIPTION</span></span>

<span data-ttu-id="01ced-107">Met deze cmdlet wordt de logboek registratie sessie gestopt door `Enable-PSWSManCombinedTrace` .</span><span class="sxs-lookup"><span data-stu-id="01ced-107">This cmdlet stops the logging session started by `Enable-PSWSManCombinedTrace`.</span></span>

<span data-ttu-id="01ced-108">Deze cmdlet maakt gebruik van de `Stop-Trace` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="01ced-108">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="01ced-109">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="01ced-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="01ced-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="01ced-110">EXAMPLES</span></span>

### <span data-ttu-id="01ced-111">Voor beeld 1: de gecombineerde logboek registratie sessie uitschakelen</span><span class="sxs-lookup"><span data-stu-id="01ced-111">Example 1: Disable the combined logging session</span></span>

```powershell
Disable-PSWSManCombinedTrace
```

## <span data-ttu-id="01ced-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="01ced-112">PARAMETERS</span></span>

### <span data-ttu-id="01ced-113">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="01ced-113">CommonParameters</span></span>

<span data-ttu-id="01ced-114">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="01ced-114">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="01ced-115">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="01ced-115">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="01ced-116">INVOER</span><span class="sxs-lookup"><span data-stu-id="01ced-116">INPUTS</span></span>

### <span data-ttu-id="01ced-117">Geen</span><span class="sxs-lookup"><span data-stu-id="01ced-117">None</span></span>

## <span data-ttu-id="01ced-118">UITVOER</span><span class="sxs-lookup"><span data-stu-id="01ced-118">OUTPUTS</span></span>

### <span data-ttu-id="01ced-119">Geen</span><span class="sxs-lookup"><span data-stu-id="01ced-119">None</span></span>

## <span data-ttu-id="01ced-120">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="01ced-120">NOTES</span></span>

## <span data-ttu-id="01ced-121">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="01ced-121">RELATED LINKS</span></span>

[<span data-ttu-id="01ced-122">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="01ced-122">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="01ced-123">Stoppen-traceren</span><span class="sxs-lookup"><span data-stu-id="01ced-123">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="01ced-124">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="01ced-124">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

