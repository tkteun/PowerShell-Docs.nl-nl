---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: 9a0a7f9fa81242fae10325e0c69ffc627088ae71
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93249277"
---
# <span data-ttu-id="ab5f0-103">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="ab5f0-103">Enable-WSManTrace</span></span>

## <span data-ttu-id="ab5f0-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ab5f0-104">SYNOPSIS</span></span>
<span data-ttu-id="ab5f0-105">Start een logboek registratie sessie met de WSMan-providers ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="ab5f0-105">Start a logging session with the WSMan providers enabled.</span></span>

## <span data-ttu-id="ab5f0-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ab5f0-106">SYNTAX</span></span>

```
Enable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="ab5f0-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ab5f0-107">DESCRIPTION</span></span>
<span data-ttu-id="ab5f0-108">Met deze cmdlet wordt een logboek registratie sessie gestart met de WSMan-providers ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="ab5f0-108">This cmdlet starts a logging session with the WSMan providers enabled.</span></span> <span data-ttu-id="ab5f0-109">De volgende gebeurtenis providers zijn ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="ab5f0-109">The following event providers are enabled:</span></span>

- <span data-ttu-id="ab5f0-110">Gebeurtenis door sturen</span><span class="sxs-lookup"><span data-stu-id="ab5f0-110">Event Forwarding</span></span>
- <span data-ttu-id="ab5f0-111">IpmiDrv</span><span class="sxs-lookup"><span data-stu-id="ab5f0-111">IpmiDrv</span></span>
- <span data-ttu-id="ab5f0-112">IPMIPrv</span><span class="sxs-lookup"><span data-stu-id="ab5f0-112">IPMIPrv</span></span>
- <span data-ttu-id="ab5f0-113">WinRM</span><span class="sxs-lookup"><span data-stu-id="ab5f0-113">WinRM</span></span>
- <span data-ttu-id="ab5f0-114">WinrsCmd</span><span class="sxs-lookup"><span data-stu-id="ab5f0-114">WinrsCmd</span></span>
- <span data-ttu-id="ab5f0-115">WinrsExe</span><span class="sxs-lookup"><span data-stu-id="ab5f0-115">WinrsExe</span></span>
- <span data-ttu-id="ab5f0-116">WinrsMgr</span><span class="sxs-lookup"><span data-stu-id="ab5f0-116">WinrsMgr</span></span>
- <span data-ttu-id="ab5f0-117">WSManProvHost</span><span class="sxs-lookup"><span data-stu-id="ab5f0-117">WSManProvHost</span></span>

<span data-ttu-id="ab5f0-118">De sessie heeft de naam ' wsmlog '.</span><span class="sxs-lookup"><span data-stu-id="ab5f0-118">The session is named 'wsmlog'.</span></span>

<span data-ttu-id="ab5f0-119">Deze cmdlet maakt gebruik van de `Start-Trace` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab5f0-119">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="ab5f0-120">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="ab5f0-120">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="ab5f0-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ab5f0-121">EXAMPLES</span></span>

### <span data-ttu-id="ab5f0-122">Voor beeld 1: een WSMan-logboek registratie sessie starten.</span><span class="sxs-lookup"><span data-stu-id="ab5f0-122">Example 1: Start a WSMan logging session.</span></span>

```powershell
Enable-WSManTrace
```

## <span data-ttu-id="ab5f0-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ab5f0-123">PARAMETERS</span></span>

### <span data-ttu-id="ab5f0-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ab5f0-124">CommonParameters</span></span>

<span data-ttu-id="ab5f0-125">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ab5f0-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ab5f0-126">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ab5f0-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ab5f0-127">INVOER</span><span class="sxs-lookup"><span data-stu-id="ab5f0-127">INPUTS</span></span>

### <span data-ttu-id="ab5f0-128">Geen</span><span class="sxs-lookup"><span data-stu-id="ab5f0-128">None</span></span>

## <span data-ttu-id="ab5f0-129">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ab5f0-129">OUTPUTS</span></span>

### <span data-ttu-id="ab5f0-130">Geen</span><span class="sxs-lookup"><span data-stu-id="ab5f0-130">None</span></span>

## <span data-ttu-id="ab5f0-131">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ab5f0-131">NOTES</span></span>

## <span data-ttu-id="ab5f0-132">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ab5f0-132">RELATED LINKS</span></span>

[<span data-ttu-id="ab5f0-133">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="ab5f0-133">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="ab5f0-134">Start-traceren</span><span class="sxs-lookup"><span data-stu-id="ab5f0-134">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="ab5f0-135">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="ab5f0-135">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

