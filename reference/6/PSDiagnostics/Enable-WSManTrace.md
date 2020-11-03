---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: 70ce4849e78262fc3553502d307e1df4e9ecfcf3
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93249243"
---
# <span data-ttu-id="766c7-103">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="766c7-103">Enable-WSManTrace</span></span>

## <span data-ttu-id="766c7-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="766c7-104">SYNOPSIS</span></span>
<span data-ttu-id="766c7-105">Start een logboek registratie sessie met de WSMan-providers ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="766c7-105">Start a logging session with the WSMan providers enabled.</span></span>

## <span data-ttu-id="766c7-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="766c7-106">SYNTAX</span></span>

```
Enable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="766c7-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="766c7-107">DESCRIPTION</span></span>
<span data-ttu-id="766c7-108">Met deze cmdlet wordt een logboek registratie sessie gestart met de WSMan-providers ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="766c7-108">This cmdlet starts a logging session with the WSMan providers enabled.</span></span> <span data-ttu-id="766c7-109">De volgende gebeurtenis providers zijn ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="766c7-109">The following event providers are enabled:</span></span>

- <span data-ttu-id="766c7-110">Gebeurtenis door sturen</span><span class="sxs-lookup"><span data-stu-id="766c7-110">Event Forwarding</span></span>
- <span data-ttu-id="766c7-111">IpmiDrv</span><span class="sxs-lookup"><span data-stu-id="766c7-111">IpmiDrv</span></span>
- <span data-ttu-id="766c7-112">IPMIPrv</span><span class="sxs-lookup"><span data-stu-id="766c7-112">IPMIPrv</span></span>
- <span data-ttu-id="766c7-113">WinRM</span><span class="sxs-lookup"><span data-stu-id="766c7-113">WinRM</span></span>
- <span data-ttu-id="766c7-114">WinrsCmd</span><span class="sxs-lookup"><span data-stu-id="766c7-114">WinrsCmd</span></span>
- <span data-ttu-id="766c7-115">WinrsExe</span><span class="sxs-lookup"><span data-stu-id="766c7-115">WinrsExe</span></span>
- <span data-ttu-id="766c7-116">WinrsMgr</span><span class="sxs-lookup"><span data-stu-id="766c7-116">WinrsMgr</span></span>
- <span data-ttu-id="766c7-117">WSManProvHost</span><span class="sxs-lookup"><span data-stu-id="766c7-117">WSManProvHost</span></span>

<span data-ttu-id="766c7-118">De sessie heeft de naam ' wsmlog '.</span><span class="sxs-lookup"><span data-stu-id="766c7-118">The session is named 'wsmlog'.</span></span>

<span data-ttu-id="766c7-119">Deze cmdlet maakt gebruik van de `Start-Trace` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="766c7-119">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="766c7-120">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="766c7-120">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="766c7-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="766c7-121">EXAMPLES</span></span>

### <span data-ttu-id="766c7-122">Voor beeld 1: een WSMan-logboek registratie sessie starten.</span><span class="sxs-lookup"><span data-stu-id="766c7-122">Example 1: Start a WSMan logging session.</span></span>

```powershell
Enable-WSManTrace
```

## <span data-ttu-id="766c7-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="766c7-123">PARAMETERS</span></span>

### <span data-ttu-id="766c7-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="766c7-124">CommonParameters</span></span>

<span data-ttu-id="766c7-125">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="766c7-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="766c7-126">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="766c7-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="766c7-127">INVOER</span><span class="sxs-lookup"><span data-stu-id="766c7-127">INPUTS</span></span>

### <span data-ttu-id="766c7-128">Geen</span><span class="sxs-lookup"><span data-stu-id="766c7-128">None</span></span>

## <span data-ttu-id="766c7-129">UITVOER</span><span class="sxs-lookup"><span data-stu-id="766c7-129">OUTPUTS</span></span>

### <span data-ttu-id="766c7-130">Geen</span><span class="sxs-lookup"><span data-stu-id="766c7-130">None</span></span>

## <span data-ttu-id="766c7-131">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="766c7-131">NOTES</span></span>

## <span data-ttu-id="766c7-132">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="766c7-132">RELATED LINKS</span></span>

[<span data-ttu-id="766c7-133">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="766c7-133">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="766c7-134">Start-traceren</span><span class="sxs-lookup"><span data-stu-id="766c7-134">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="766c7-135">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="766c7-135">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)
