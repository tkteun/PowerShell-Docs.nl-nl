---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: 647a7676eddf2175bf29e02b3482cc9c7c4d8ebe
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705584"
---
# <span data-ttu-id="9cd47-102">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="9cd47-102">Disable-WSManTrace</span></span>

## <span data-ttu-id="9cd47-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9cd47-103">SYNOPSIS</span></span>
<span data-ttu-id="9cd47-104">Stop de WSMan-logboek registratie sessie die is gestart door Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="9cd47-104">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

## <span data-ttu-id="9cd47-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9cd47-105">SYNTAX</span></span>

```
Disable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="9cd47-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9cd47-106">DESCRIPTION</span></span>
<span data-ttu-id="9cd47-107">Met deze cmdlet stopt u de WSMan-logboek registratie sessie die is gestart door Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="9cd47-107">This cmdlet stops the WSMan logging session started by Enable-WSManTrace.</span></span>

<span data-ttu-id="9cd47-108">Deze cmdlet maakt gebruik van de `Stop-Trace` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9cd47-108">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="9cd47-109">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="9cd47-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="9cd47-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9cd47-110">EXAMPLES</span></span>

### <span data-ttu-id="9cd47-111">Voor beeld 1: WSMan-tracering stoppen</span><span class="sxs-lookup"><span data-stu-id="9cd47-111">Example 1: Stop a WSMan trace</span></span>

```powershell
Disable-WSManTrace
```

## <span data-ttu-id="9cd47-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9cd47-112">PARAMETERS</span></span>

### <span data-ttu-id="9cd47-113">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9cd47-113">CommonParameters</span></span>

<span data-ttu-id="9cd47-114">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9cd47-114">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9cd47-115">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9cd47-115">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9cd47-116">INVOER</span><span class="sxs-lookup"><span data-stu-id="9cd47-116">INPUTS</span></span>

### <span data-ttu-id="9cd47-117">Geen</span><span class="sxs-lookup"><span data-stu-id="9cd47-117">None</span></span>

## <span data-ttu-id="9cd47-118">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9cd47-118">OUTPUTS</span></span>

### <span data-ttu-id="9cd47-119">Geen</span><span class="sxs-lookup"><span data-stu-id="9cd47-119">None</span></span>

## <span data-ttu-id="9cd47-120">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9cd47-120">NOTES</span></span>

## <span data-ttu-id="9cd47-121">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9cd47-121">RELATED LINKS</span></span>

[<span data-ttu-id="9cd47-122">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="9cd47-122">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="9cd47-123">Stoppen-traceren</span><span class="sxs-lookup"><span data-stu-id="9cd47-123">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="9cd47-124">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="9cd47-124">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)

