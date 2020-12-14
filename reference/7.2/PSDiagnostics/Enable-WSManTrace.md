---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: a9d91eab94666186c13f8d5c928d83055f6dbefa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705668"
---
# <span data-ttu-id="754b6-102">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="754b6-102">Enable-WSManTrace</span></span>

## <span data-ttu-id="754b6-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="754b6-103">SYNOPSIS</span></span>
<span data-ttu-id="754b6-104">Start een logboek registratie sessie met de WSMan-providers ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="754b6-104">Start a logging session with the WSMan providers enabled.</span></span>

## <span data-ttu-id="754b6-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="754b6-105">SYNTAX</span></span>

```
Enable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="754b6-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="754b6-106">DESCRIPTION</span></span>
<span data-ttu-id="754b6-107">Met deze cmdlet wordt een logboek registratie sessie gestart met de WSMan-providers ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="754b6-107">This cmdlet starts a logging session with the WSMan providers enabled.</span></span> <span data-ttu-id="754b6-108">De volgende gebeurtenis providers zijn ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="754b6-108">The following event providers are enabled:</span></span>

- <span data-ttu-id="754b6-109">Gebeurtenis door sturen</span><span class="sxs-lookup"><span data-stu-id="754b6-109">Event Forwarding</span></span>
- <span data-ttu-id="754b6-110">IpmiDrv</span><span class="sxs-lookup"><span data-stu-id="754b6-110">IpmiDrv</span></span>
- <span data-ttu-id="754b6-111">IPMIPrv</span><span class="sxs-lookup"><span data-stu-id="754b6-111">IPMIPrv</span></span>
- <span data-ttu-id="754b6-112">WinRM</span><span class="sxs-lookup"><span data-stu-id="754b6-112">WinRM</span></span>
- <span data-ttu-id="754b6-113">WinrsCmd</span><span class="sxs-lookup"><span data-stu-id="754b6-113">WinrsCmd</span></span>
- <span data-ttu-id="754b6-114">WinrsExe</span><span class="sxs-lookup"><span data-stu-id="754b6-114">WinrsExe</span></span>
- <span data-ttu-id="754b6-115">WinrsMgr</span><span class="sxs-lookup"><span data-stu-id="754b6-115">WinrsMgr</span></span>
- <span data-ttu-id="754b6-116">WSManProvHost</span><span class="sxs-lookup"><span data-stu-id="754b6-116">WSManProvHost</span></span>

<span data-ttu-id="754b6-117">De sessie heeft de naam ' wsmlog '.</span><span class="sxs-lookup"><span data-stu-id="754b6-117">The session is named 'wsmlog'.</span></span>

<span data-ttu-id="754b6-118">Deze cmdlet maakt gebruik van de `Start-Trace` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="754b6-118">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="754b6-119">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="754b6-119">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="754b6-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="754b6-120">EXAMPLES</span></span>

### <span data-ttu-id="754b6-121">Voor beeld 1: een WSMan-logboek registratie sessie starten.</span><span class="sxs-lookup"><span data-stu-id="754b6-121">Example 1: Start a WSMan logging session.</span></span>

```powershell
Enable-WSManTrace
```

## <span data-ttu-id="754b6-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="754b6-122">PARAMETERS</span></span>

### <span data-ttu-id="754b6-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="754b6-123">CommonParameters</span></span>

<span data-ttu-id="754b6-124">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="754b6-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="754b6-125">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="754b6-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="754b6-126">INVOER</span><span class="sxs-lookup"><span data-stu-id="754b6-126">INPUTS</span></span>

### <span data-ttu-id="754b6-127">Geen</span><span class="sxs-lookup"><span data-stu-id="754b6-127">None</span></span>

## <span data-ttu-id="754b6-128">UITVOER</span><span class="sxs-lookup"><span data-stu-id="754b6-128">OUTPUTS</span></span>

### <span data-ttu-id="754b6-129">Geen</span><span class="sxs-lookup"><span data-stu-id="754b6-129">None</span></span>

## <span data-ttu-id="754b6-130">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="754b6-130">NOTES</span></span>

## <span data-ttu-id="754b6-131">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="754b6-131">RELATED LINKS</span></span>

[<span data-ttu-id="754b6-132">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="754b6-132">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="754b6-133">Start-traceren</span><span class="sxs-lookup"><span data-stu-id="754b6-133">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="754b6-134">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="754b6-134">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

