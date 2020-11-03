---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: 08c9d61f210761e2ed7a3a5014812b2bd362201b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250331"
---
# <span data-ttu-id="bd5fc-103">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="bd5fc-103">Enable-WSManTrace</span></span>

## <span data-ttu-id="bd5fc-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="bd5fc-104">SYNOPSIS</span></span>
<span data-ttu-id="bd5fc-105">Start een logboek registratie sessie met de WSMan-providers ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="bd5fc-105">Start a logging session with the WSMan providers enabled.</span></span>

## <span data-ttu-id="bd5fc-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="bd5fc-106">SYNTAX</span></span>

```
Enable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="bd5fc-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="bd5fc-107">DESCRIPTION</span></span>
<span data-ttu-id="bd5fc-108">Met deze cmdlet wordt een logboek registratie sessie gestart met de WSMan-providers ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="bd5fc-108">This cmdlet starts a logging session with the WSMan providers enabled.</span></span> <span data-ttu-id="bd5fc-109">De volgende gebeurtenis providers zijn ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="bd5fc-109">The following event providers are enabled:</span></span>

- <span data-ttu-id="bd5fc-110">Gebeurtenis door sturen</span><span class="sxs-lookup"><span data-stu-id="bd5fc-110">Event Forwarding</span></span>
- <span data-ttu-id="bd5fc-111">IpmiDrv</span><span class="sxs-lookup"><span data-stu-id="bd5fc-111">IpmiDrv</span></span>
- <span data-ttu-id="bd5fc-112">IPMIPrv</span><span class="sxs-lookup"><span data-stu-id="bd5fc-112">IPMIPrv</span></span>
- <span data-ttu-id="bd5fc-113">WinRM</span><span class="sxs-lookup"><span data-stu-id="bd5fc-113">WinRM</span></span>
- <span data-ttu-id="bd5fc-114">WinrsCmd</span><span class="sxs-lookup"><span data-stu-id="bd5fc-114">WinrsCmd</span></span>
- <span data-ttu-id="bd5fc-115">WinrsExe</span><span class="sxs-lookup"><span data-stu-id="bd5fc-115">WinrsExe</span></span>
- <span data-ttu-id="bd5fc-116">WinrsMgr</span><span class="sxs-lookup"><span data-stu-id="bd5fc-116">WinrsMgr</span></span>
- <span data-ttu-id="bd5fc-117">WSManProvHost</span><span class="sxs-lookup"><span data-stu-id="bd5fc-117">WSManProvHost</span></span>

<span data-ttu-id="bd5fc-118">De sessie heeft de naam ' wsmlog '.</span><span class="sxs-lookup"><span data-stu-id="bd5fc-118">The session is named 'wsmlog'.</span></span>

<span data-ttu-id="bd5fc-119">Deze cmdlet maakt gebruik van de `Start-Trace` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bd5fc-119">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="bd5fc-120">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="bd5fc-120">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="bd5fc-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="bd5fc-121">EXAMPLES</span></span>

### <span data-ttu-id="bd5fc-122">Voor beeld 1: een WSMan-logboek registratie sessie starten.</span><span class="sxs-lookup"><span data-stu-id="bd5fc-122">Example 1: Start a WSMan logging session.</span></span>

```powershell
Enable-WSManTrace
```

## <span data-ttu-id="bd5fc-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bd5fc-123">PARAMETERS</span></span>

### <span data-ttu-id="bd5fc-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bd5fc-124">CommonParameters</span></span>

<span data-ttu-id="bd5fc-125">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bd5fc-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bd5fc-126">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bd5fc-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bd5fc-127">INVOER</span><span class="sxs-lookup"><span data-stu-id="bd5fc-127">INPUTS</span></span>

### <span data-ttu-id="bd5fc-128">Geen</span><span class="sxs-lookup"><span data-stu-id="bd5fc-128">None</span></span>

## <span data-ttu-id="bd5fc-129">UITVOER</span><span class="sxs-lookup"><span data-stu-id="bd5fc-129">OUTPUTS</span></span>

### <span data-ttu-id="bd5fc-130">System. object</span><span class="sxs-lookup"><span data-stu-id="bd5fc-130">System.Object</span></span>

## <span data-ttu-id="bd5fc-131">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="bd5fc-131">NOTES</span></span>

## <span data-ttu-id="bd5fc-132">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="bd5fc-132">RELATED LINKS</span></span>

[<span data-ttu-id="bd5fc-133">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="bd5fc-133">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="bd5fc-134">Start-traceren</span><span class="sxs-lookup"><span data-stu-id="bd5fc-134">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="bd5fc-135">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="bd5fc-135">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)
