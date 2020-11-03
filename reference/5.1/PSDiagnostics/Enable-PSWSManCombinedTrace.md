---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: f67b5d9fe8da48cca5fd4ec7d2056a4702d3ff16
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250332"
---
# <span data-ttu-id="cd6a7-103">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="cd6a7-103">Enable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="cd6a7-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="cd6a7-104">SYNOPSIS</span></span>
<span data-ttu-id="cd6a7-105">Start een logboek registratie sessie met de WSMan-en Power shell-providers ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="cd6a7-105">Start a logging session with the WSMan and PowerShell providers enabled.</span></span>

## <span data-ttu-id="cd6a7-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cd6a7-106">SYNTAX</span></span>

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## <span data-ttu-id="cd6a7-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cd6a7-107">DESCRIPTION</span></span>

<span data-ttu-id="cd6a7-108">Met deze cmdlet wordt een logboek registratie sessie gestart met de volgende Power shell-providers ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="cd6a7-108">This cmdlet starts a logging session with the following PowerShell providers enabled:</span></span>

- <span data-ttu-id="cd6a7-109">Micro soft-Windows-Power shell</span><span class="sxs-lookup"><span data-stu-id="cd6a7-109">Microsoft-Windows-PowerShell</span></span>
- <span data-ttu-id="cd6a7-110">Micro soft-Windows-WinRM</span><span class="sxs-lookup"><span data-stu-id="cd6a7-110">Microsoft-Windows-WinRM</span></span>

<span data-ttu-id="cd6a7-111">De sessie heeft de naam ' PSTrace '.</span><span class="sxs-lookup"><span data-stu-id="cd6a7-111">The session is named 'PSTrace'.</span></span>

<span data-ttu-id="cd6a7-112">Deze cmdlet maakt gebruik van de `Start-Trace` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cd6a7-112">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="cd6a7-113">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="cd6a7-113">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="cd6a7-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cd6a7-114">EXAMPLES</span></span>

### <span data-ttu-id="cd6a7-115">Voor beeld 1: een gecombineerde logboek registratie sessie starten</span><span class="sxs-lookup"><span data-stu-id="cd6a7-115">Example 1: Start a combined logging session</span></span>

```powershell
Enable-PSWSManCombinedTrace
```

## <span data-ttu-id="cd6a7-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cd6a7-116">PARAMETERS</span></span>

### <span data-ttu-id="cd6a7-117">-DoNotOverwriteExistingTrace</span><span class="sxs-lookup"><span data-stu-id="cd6a7-117">-DoNotOverwriteExistingTrace</span></span>

<span data-ttu-id="cd6a7-118">Standaard worden de gebeurtenissen geschreven naar ' $pshome \Traces\PSTrace.etl '.</span><span class="sxs-lookup"><span data-stu-id="cd6a7-118">By default, the events are written to "$pshome\Traces\PSTrace.etl".</span></span> <span data-ttu-id="cd6a7-119">Als deze para meter wordt gebruikt, maakt de cmdlet een unieke bestands naam: "$pshome \Traces\ PSTrace_ {GUID}. etl"</span><span class="sxs-lookup"><span data-stu-id="cd6a7-119">When this parameter is used, the cmdlet creates a unique filename: "$pshome\Traces\PSTrace_{guid}.etl"</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd6a7-120">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cd6a7-120">CommonParameters</span></span>

<span data-ttu-id="cd6a7-121">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cd6a7-121">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cd6a7-122">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cd6a7-122">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cd6a7-123">INVOER</span><span class="sxs-lookup"><span data-stu-id="cd6a7-123">INPUTS</span></span>

### <span data-ttu-id="cd6a7-124">Geen</span><span class="sxs-lookup"><span data-stu-id="cd6a7-124">None</span></span>

## <span data-ttu-id="cd6a7-125">UITVOER</span><span class="sxs-lookup"><span data-stu-id="cd6a7-125">OUTPUTS</span></span>

### <span data-ttu-id="cd6a7-126">System. object</span><span class="sxs-lookup"><span data-stu-id="cd6a7-126">System.Object</span></span>

## <span data-ttu-id="cd6a7-127">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="cd6a7-127">NOTES</span></span>

## <span data-ttu-id="cd6a7-128">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="cd6a7-128">RELATED LINKS</span></span>

[<span data-ttu-id="cd6a7-129">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="cd6a7-129">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="cd6a7-130">Start-traceren</span><span class="sxs-lookup"><span data-stu-id="cd6a7-130">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="cd6a7-131">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="cd6a7-131">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)
