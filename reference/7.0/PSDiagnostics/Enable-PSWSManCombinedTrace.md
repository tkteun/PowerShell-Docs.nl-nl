---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: f6b14ea6cda7d83792f7b51b854471a2cb62bfb5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249384"
---
# <span data-ttu-id="e3986-103">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="e3986-103">Enable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="e3986-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e3986-104">SYNOPSIS</span></span>
<span data-ttu-id="e3986-105">Start een logboek registratie sessie met de WSMan-en Power shell-providers ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="e3986-105">Start a logging session with the WSMan and PowerShell providers enabled.</span></span>

## <span data-ttu-id="e3986-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e3986-106">SYNTAX</span></span>

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## <span data-ttu-id="e3986-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e3986-107">DESCRIPTION</span></span>

<span data-ttu-id="e3986-108">Met deze cmdlet wordt een logboek registratie sessie gestart met de volgende Power shell-providers ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="e3986-108">This cmdlet starts a logging session with the following PowerShell providers enabled:</span></span>

- <span data-ttu-id="e3986-109">Micro soft-Windows-Power shell</span><span class="sxs-lookup"><span data-stu-id="e3986-109">Microsoft-Windows-PowerShell</span></span>
- <span data-ttu-id="e3986-110">Micro soft-Windows-WinRM</span><span class="sxs-lookup"><span data-stu-id="e3986-110">Microsoft-Windows-WinRM</span></span>

<span data-ttu-id="e3986-111">De sessie heeft de naam ' PSTrace '.</span><span class="sxs-lookup"><span data-stu-id="e3986-111">The session is named 'PSTrace'.</span></span>

<span data-ttu-id="e3986-112">Deze cmdlet maakt gebruik van de `Start-Trace` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e3986-112">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="e3986-113">U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="e3986-113">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="e3986-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e3986-114">EXAMPLES</span></span>

### <span data-ttu-id="e3986-115">Voor beeld 1: een gecombineerde logboek registratie sessie starten</span><span class="sxs-lookup"><span data-stu-id="e3986-115">Example 1: Start a combined logging session</span></span>

```powershell
Enable-PSWSManCombinedTrace
```

## <span data-ttu-id="e3986-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e3986-116">PARAMETERS</span></span>

### <span data-ttu-id="e3986-117">-DoNotOverwriteExistingTrace</span><span class="sxs-lookup"><span data-stu-id="e3986-117">-DoNotOverwriteExistingTrace</span></span>

<span data-ttu-id="e3986-118">Standaard worden de gebeurtenissen geschreven naar ' $pshome \Traces\PSTrace.etl '.</span><span class="sxs-lookup"><span data-stu-id="e3986-118">By default, the events are written to "$pshome\Traces\PSTrace.etl".</span></span> <span data-ttu-id="e3986-119">Als deze para meter wordt gebruikt, maakt de cmdlet een unieke bestands naam: "$pshome \Traces\ PSTrace_ {GUID}. etl"</span><span class="sxs-lookup"><span data-stu-id="e3986-119">When this parameter is used, the cmdlet creates a unique filename: "$pshome\Traces\PSTrace_{guid}.etl"</span></span>

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

### <span data-ttu-id="e3986-120">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e3986-120">CommonParameters</span></span>

<span data-ttu-id="e3986-121">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e3986-121">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e3986-122">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e3986-122">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e3986-123">INVOER</span><span class="sxs-lookup"><span data-stu-id="e3986-123">INPUTS</span></span>

### <span data-ttu-id="e3986-124">Geen</span><span class="sxs-lookup"><span data-stu-id="e3986-124">None</span></span>

## <span data-ttu-id="e3986-125">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e3986-125">OUTPUTS</span></span>

### <span data-ttu-id="e3986-126">Geen</span><span class="sxs-lookup"><span data-stu-id="e3986-126">None</span></span>

## <span data-ttu-id="e3986-127">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e3986-127">NOTES</span></span>

## <span data-ttu-id="e3986-128">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e3986-128">RELATED LINKS</span></span>

[<span data-ttu-id="e3986-129">Gebeurtenis tracering</span><span class="sxs-lookup"><span data-stu-id="e3986-129">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="e3986-130">Start-traceren</span><span class="sxs-lookup"><span data-stu-id="e3986-130">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="e3986-131">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="e3986-131">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)
