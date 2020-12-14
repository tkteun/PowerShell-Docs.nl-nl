---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: ef333edaa091e96df11a8288e9b16f133614c1e0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705797"
---
# <span data-ttu-id="1ae26-102">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="1ae26-102">Enable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="1ae26-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1ae26-103">SYNOPSIS</span></span>
<span data-ttu-id="1ae26-104">Start een logboek registratie sessie met de WSMan-en Power shell-providers ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="1ae26-104">Start a logging session with the WSMan and PowerShell providers enabled.</span></span>

## <span data-ttu-id="1ae26-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1ae26-105">SYNTAX</span></span>

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## <span data-ttu-id="1ae26-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1ae26-106">DESCRIPTION</span></span>

<span data-ttu-id="1ae26-107">Met deze cmdlet wordt een logboek registratie sessie gestart met de volgende Power shell-providers ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="1ae26-107">This cmdlet starts a logging session with the following PowerShell providers enabled:</span></span>

- <span data-ttu-id="1ae26-108">Micro soft-Windows-Power shell</span><span class="sxs-lookup"><span data-stu-id="1ae26-108">Microsoft-Windows-PowerShell</span></span>
- <span data-ttu-id="1ae26-109">Micro soft-Windows-WinRM</span><span class="sxs-lookup"><span data-stu-id="1ae26-109">Microsoft-Windows-WinRM</span></span>

<span data-ttu-id="1ae26-110">De sessie heeft de naam ' PSTrace '.</span><span class="sxs-lookup"><span data-stu-id="1ae26-110">The session is named 'PSTrace'.</span></span>

<span data-ttu-id="1ae26-111">Deze cmdlet maakt gebruik van de `Start-Trace` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1ae26-111">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="1ae26-112">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="1ae26-112">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="1ae26-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1ae26-113">EXAMPLES</span></span>

### <span data-ttu-id="1ae26-114">Voor beeld 1: een gecombineerde logboek registratie sessie starten</span><span class="sxs-lookup"><span data-stu-id="1ae26-114">Example 1: Start a combined logging session</span></span>

```powershell
Enable-PSWSManCombinedTrace
```

## <span data-ttu-id="1ae26-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1ae26-115">PARAMETERS</span></span>

### <span data-ttu-id="1ae26-116">-DoNotOverwriteExistingTrace</span><span class="sxs-lookup"><span data-stu-id="1ae26-116">-DoNotOverwriteExistingTrace</span></span>

<span data-ttu-id="1ae26-117">Standaard worden de gebeurtenissen geschreven naar ' $pshome \Traces\PSTrace.etl '.</span><span class="sxs-lookup"><span data-stu-id="1ae26-117">By default, the events are written to "$pshome\Traces\PSTrace.etl".</span></span> <span data-ttu-id="1ae26-118">Als deze para meter wordt gebruikt, maakt de cmdlet een unieke bestands naam: "$pshome \Traces\ PSTrace_ {GUID}. etl"</span><span class="sxs-lookup"><span data-stu-id="1ae26-118">When this parameter is used, the cmdlet creates a unique filename: "$pshome\Traces\PSTrace_{guid}.etl"</span></span>

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

### <span data-ttu-id="1ae26-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1ae26-119">CommonParameters</span></span>

<span data-ttu-id="1ae26-120">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1ae26-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1ae26-121">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1ae26-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1ae26-122">INVOER</span><span class="sxs-lookup"><span data-stu-id="1ae26-122">INPUTS</span></span>

### <span data-ttu-id="1ae26-123">Geen</span><span class="sxs-lookup"><span data-stu-id="1ae26-123">None</span></span>

## <span data-ttu-id="1ae26-124">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1ae26-124">OUTPUTS</span></span>

### <span data-ttu-id="1ae26-125">Geen</span><span class="sxs-lookup"><span data-stu-id="1ae26-125">None</span></span>

## <span data-ttu-id="1ae26-126">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1ae26-126">NOTES</span></span>

## <span data-ttu-id="1ae26-127">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1ae26-127">RELATED LINKS</span></span>

[<span data-ttu-id="1ae26-128">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="1ae26-128">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="1ae26-129">Start-traceren</span><span class="sxs-lookup"><span data-stu-id="1ae26-129">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="1ae26-130">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="1ae26-130">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

