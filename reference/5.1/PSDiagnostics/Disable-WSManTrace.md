---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: 90cb571f93243e6fbc59970e5602911e17e25ec7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250334"
---
# <span data-ttu-id="2eeb5-103">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="2eeb5-103">Disable-WSManTrace</span></span>

## <span data-ttu-id="2eeb5-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2eeb5-104">SYNOPSIS</span></span>
<span data-ttu-id="2eeb5-105">Stop de WSMan-logboek registratie sessie die is gestart door Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="2eeb5-105">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

## <span data-ttu-id="2eeb5-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2eeb5-106">SYNTAX</span></span>

```
Disable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="2eeb5-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2eeb5-107">DESCRIPTION</span></span>
<span data-ttu-id="2eeb5-108">Met deze cmdlet stopt u de WSMan-logboek registratie sessie die is gestart door Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="2eeb5-108">This cmdlet stops the WSMan logging session started by Enable-WSManTrace.</span></span>

<span data-ttu-id="2eeb5-109">Deze cmdlet maakt gebruik van de `Stop-Trace` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2eeb5-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="2eeb5-110">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="2eeb5-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="2eeb5-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2eeb5-111">EXAMPLES</span></span>

### <span data-ttu-id="2eeb5-112">Voor beeld 1: WSMan-tracering stoppen</span><span class="sxs-lookup"><span data-stu-id="2eeb5-112">Example 1: Stop a WSMan trace</span></span>

```powershell
Disable-WSManTrace
```

## <span data-ttu-id="2eeb5-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2eeb5-113">PARAMETERS</span></span>

### <span data-ttu-id="2eeb5-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2eeb5-114">CommonParameters</span></span>

<span data-ttu-id="2eeb5-115">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2eeb5-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2eeb5-116">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2eeb5-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2eeb5-117">INVOER</span><span class="sxs-lookup"><span data-stu-id="2eeb5-117">INPUTS</span></span>

### <span data-ttu-id="2eeb5-118">Geen</span><span class="sxs-lookup"><span data-stu-id="2eeb5-118">None</span></span>

## <span data-ttu-id="2eeb5-119">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2eeb5-119">OUTPUTS</span></span>

### <span data-ttu-id="2eeb5-120">System. object</span><span class="sxs-lookup"><span data-stu-id="2eeb5-120">System.Object</span></span>

## <span data-ttu-id="2eeb5-121">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2eeb5-121">NOTES</span></span>

## <span data-ttu-id="2eeb5-122">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2eeb5-122">RELATED LINKS</span></span>

[<span data-ttu-id="2eeb5-123">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="2eeb5-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="2eeb5-124">Stoppen-traceren</span><span class="sxs-lookup"><span data-stu-id="2eeb5-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="2eeb5-125">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="2eeb5-125">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
