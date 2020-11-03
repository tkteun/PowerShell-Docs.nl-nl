---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: f7ec371e0d9826dc095fbf71c4785cae2856875b
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93249242"
---
# <span data-ttu-id="b482b-103">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="b482b-103">Disable-WSManTrace</span></span>

## <span data-ttu-id="b482b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b482b-104">SYNOPSIS</span></span>
<span data-ttu-id="b482b-105">Stop de WSMan-logboek registratie sessie die is gestart door Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="b482b-105">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

## <span data-ttu-id="b482b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b482b-106">SYNTAX</span></span>

```
Disable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="b482b-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b482b-107">DESCRIPTION</span></span>
<span data-ttu-id="b482b-108">Met deze cmdlet stopt u de WSMan-logboek registratie sessie die is gestart door Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="b482b-108">This cmdlet stops the WSMan logging session started by Enable-WSManTrace.</span></span>

<span data-ttu-id="b482b-109">Deze cmdlet maakt gebruik van de `Stop-Trace` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b482b-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="b482b-110">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="b482b-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="b482b-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b482b-111">EXAMPLES</span></span>

### <span data-ttu-id="b482b-112">Voor beeld 1: WSMan-tracering stoppen</span><span class="sxs-lookup"><span data-stu-id="b482b-112">Example 1: Stop a WSMan trace</span></span>

```powershell
Disable-WSManTrace
```

## <span data-ttu-id="b482b-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b482b-113">PARAMETERS</span></span>

### <span data-ttu-id="b482b-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b482b-114">CommonParameters</span></span>

<span data-ttu-id="b482b-115">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b482b-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b482b-116">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b482b-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b482b-117">INVOER</span><span class="sxs-lookup"><span data-stu-id="b482b-117">INPUTS</span></span>

### <span data-ttu-id="b482b-118">Geen</span><span class="sxs-lookup"><span data-stu-id="b482b-118">None</span></span>

## <span data-ttu-id="b482b-119">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b482b-119">OUTPUTS</span></span>

### <span data-ttu-id="b482b-120">Geen</span><span class="sxs-lookup"><span data-stu-id="b482b-120">None</span></span>

## <span data-ttu-id="b482b-121">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b482b-121">NOTES</span></span>

## <span data-ttu-id="b482b-122">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b482b-122">RELATED LINKS</span></span>

[<span data-ttu-id="b482b-123">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="b482b-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="b482b-124">Stoppen-traceren</span><span class="sxs-lookup"><span data-stu-id="b482b-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="b482b-125">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="b482b-125">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
