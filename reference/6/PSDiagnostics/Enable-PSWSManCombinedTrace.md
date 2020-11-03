---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: cfe73dea98cdf858f1364e1daf434334b57a62cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251206"
---
# <span data-ttu-id="b4225-103">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="b4225-103">Enable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="b4225-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b4225-104">SYNOPSIS</span></span>
<span data-ttu-id="b4225-105">Start een logboek registratie sessie met de WSMan-en Power shell-providers ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="b4225-105">Start a logging session with the WSMan and PowerShell providers enabled.</span></span>

## <span data-ttu-id="b4225-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b4225-106">SYNTAX</span></span>

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## <span data-ttu-id="b4225-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b4225-107">DESCRIPTION</span></span>

<span data-ttu-id="b4225-108">Met deze cmdlet wordt een logboek registratie sessie gestart met de volgende Power shell-providers ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="b4225-108">This cmdlet starts a logging session with the following PowerShell providers enabled:</span></span>

- <span data-ttu-id="b4225-109">Micro soft-Windows-Power shell</span><span class="sxs-lookup"><span data-stu-id="b4225-109">Microsoft-Windows-PowerShell</span></span>
- <span data-ttu-id="b4225-110">Micro soft-Windows-WinRM</span><span class="sxs-lookup"><span data-stu-id="b4225-110">Microsoft-Windows-WinRM</span></span>

<span data-ttu-id="b4225-111">De sessie heeft de naam ' PSTrace '.</span><span class="sxs-lookup"><span data-stu-id="b4225-111">The session is named 'PSTrace'.</span></span>

<span data-ttu-id="b4225-112">Deze cmdlet maakt gebruik van de `Start-Trace` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b4225-112">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="b4225-113">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="b4225-113">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="b4225-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b4225-114">EXAMPLES</span></span>

### <span data-ttu-id="b4225-115">Voor beeld 1: een gecombineerde logboek registratie sessie starten</span><span class="sxs-lookup"><span data-stu-id="b4225-115">Example 1: Start a combined logging session</span></span>

```powershell
Enable-PSWSManCombinedTrace
```

## <span data-ttu-id="b4225-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b4225-116">PARAMETERS</span></span>

### <span data-ttu-id="b4225-117">-DoNotOverwriteExistingTrace</span><span class="sxs-lookup"><span data-stu-id="b4225-117">-DoNotOverwriteExistingTrace</span></span>

<span data-ttu-id="b4225-118">Standaard worden de gebeurtenissen geschreven naar ' $pshome \Traces\PSTrace.etl '.</span><span class="sxs-lookup"><span data-stu-id="b4225-118">By default, the events are written to "$pshome\Traces\PSTrace.etl".</span></span> <span data-ttu-id="b4225-119">Als deze para meter wordt gebruikt, maakt de cmdlet een unieke bestands naam: "$pshome \Traces\ PSTrace_ {GUID}. etl"</span><span class="sxs-lookup"><span data-stu-id="b4225-119">When this parameter is used, the cmdlet creates a unique filename: "$pshome\Traces\PSTrace_{guid}.etl"</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b4225-120">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b4225-120">CommonParameters</span></span>

<span data-ttu-id="b4225-121">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b4225-121">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b4225-122">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b4225-122">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b4225-123">INVOER</span><span class="sxs-lookup"><span data-stu-id="b4225-123">INPUTS</span></span>

### <span data-ttu-id="b4225-124">Geen</span><span class="sxs-lookup"><span data-stu-id="b4225-124">None</span></span>

## <span data-ttu-id="b4225-125">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b4225-125">OUTPUTS</span></span>

### <span data-ttu-id="b4225-126">Geen</span><span class="sxs-lookup"><span data-stu-id="b4225-126">None</span></span>

## <span data-ttu-id="b4225-127">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b4225-127">NOTES</span></span>

## <span data-ttu-id="b4225-128">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b4225-128">RELATED LINKS</span></span>

[<span data-ttu-id="b4225-129">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="b4225-129">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="b4225-130">Start-traceren</span><span class="sxs-lookup"><span data-stu-id="b4225-130">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="b4225-131">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="b4225-131">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)
