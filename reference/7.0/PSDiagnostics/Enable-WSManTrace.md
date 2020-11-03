---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: c872b57186a854a67908bb07daac7f1a31bbb995
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93249304"
---
# <span data-ttu-id="c9141-103">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="c9141-103">Enable-WSManTrace</span></span>

## <span data-ttu-id="c9141-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c9141-104">SYNOPSIS</span></span>
<span data-ttu-id="c9141-105">Start een logboek registratie sessie met de WSMan-providers ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="c9141-105">Start a logging session with the WSMan providers enabled.</span></span>

## <span data-ttu-id="c9141-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c9141-106">SYNTAX</span></span>

```
Enable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="c9141-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c9141-107">DESCRIPTION</span></span>
<span data-ttu-id="c9141-108">Met deze cmdlet wordt een logboek registratie sessie gestart met de WSMan-providers ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="c9141-108">This cmdlet starts a logging session with the WSMan providers enabled.</span></span> <span data-ttu-id="c9141-109">De volgende gebeurtenis providers zijn ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="c9141-109">The following event providers are enabled:</span></span>

- <span data-ttu-id="c9141-110">Gebeurtenis door sturen</span><span class="sxs-lookup"><span data-stu-id="c9141-110">Event Forwarding</span></span>
- <span data-ttu-id="c9141-111">IpmiDrv</span><span class="sxs-lookup"><span data-stu-id="c9141-111">IpmiDrv</span></span>
- <span data-ttu-id="c9141-112">IPMIPrv</span><span class="sxs-lookup"><span data-stu-id="c9141-112">IPMIPrv</span></span>
- <span data-ttu-id="c9141-113">WinRM</span><span class="sxs-lookup"><span data-stu-id="c9141-113">WinRM</span></span>
- <span data-ttu-id="c9141-114">WinrsCmd</span><span class="sxs-lookup"><span data-stu-id="c9141-114">WinrsCmd</span></span>
- <span data-ttu-id="c9141-115">WinrsExe</span><span class="sxs-lookup"><span data-stu-id="c9141-115">WinrsExe</span></span>
- <span data-ttu-id="c9141-116">WinrsMgr</span><span class="sxs-lookup"><span data-stu-id="c9141-116">WinrsMgr</span></span>
- <span data-ttu-id="c9141-117">WSManProvHost</span><span class="sxs-lookup"><span data-stu-id="c9141-117">WSManProvHost</span></span>

<span data-ttu-id="c9141-118">De sessie heeft de naam ' wsmlog '.</span><span class="sxs-lookup"><span data-stu-id="c9141-118">The session is named 'wsmlog'.</span></span>

<span data-ttu-id="c9141-119">Deze cmdlet maakt gebruik van de `Start-Trace` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c9141-119">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="c9141-120">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="c9141-120">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="c9141-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c9141-121">EXAMPLES</span></span>

### <span data-ttu-id="c9141-122">Voor beeld 1: een WSMan-logboek registratie sessie starten.</span><span class="sxs-lookup"><span data-stu-id="c9141-122">Example 1: Start a WSMan logging session.</span></span>

```powershell
Enable-WSManTrace
```

## <span data-ttu-id="c9141-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c9141-123">PARAMETERS</span></span>

### <span data-ttu-id="c9141-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c9141-124">CommonParameters</span></span>

<span data-ttu-id="c9141-125">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c9141-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c9141-126">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c9141-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c9141-127">INVOER</span><span class="sxs-lookup"><span data-stu-id="c9141-127">INPUTS</span></span>

### <span data-ttu-id="c9141-128">Geen</span><span class="sxs-lookup"><span data-stu-id="c9141-128">None</span></span>

## <span data-ttu-id="c9141-129">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c9141-129">OUTPUTS</span></span>

### <span data-ttu-id="c9141-130">Geen</span><span class="sxs-lookup"><span data-stu-id="c9141-130">None</span></span>

## <span data-ttu-id="c9141-131">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c9141-131">NOTES</span></span>

## <span data-ttu-id="c9141-132">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c9141-132">RELATED LINKS</span></span>

[<span data-ttu-id="c9141-133">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="c9141-133">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="c9141-134">Start-traceren</span><span class="sxs-lookup"><span data-stu-id="c9141-134">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="c9141-135">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="c9141-135">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)
