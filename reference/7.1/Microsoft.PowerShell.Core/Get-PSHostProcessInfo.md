---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pshostprocessinfo?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSHostProcessInfo
ms.openlocfilehash: 655cc02e10bdb11092412271c16a002ab89089c3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251356"
---
# <span data-ttu-id="b6e30-103">Get-PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="b6e30-103">Get-PSHostProcessInfo</span></span>

## <span data-ttu-id="b6e30-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b6e30-104">SYNOPSIS</span></span>
<span data-ttu-id="b6e30-105">Hiermee wordt proces informatie over de Power shell-host opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b6e30-105">Gets process information about the PowerShell host.</span></span>

## <span data-ttu-id="b6e30-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b6e30-106">SYNTAX</span></span>

### <span data-ttu-id="b6e30-107">ProcessNameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="b6e30-107">ProcessNameParameterSet (Default)</span></span>

```
Get-PSHostProcessInfo [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="b6e30-108">ProcessParameterSet</span><span class="sxs-lookup"><span data-stu-id="b6e30-108">ProcessParameterSet</span></span>

```
Get-PSHostProcessInfo [-Process] <Process[]> [<CommonParameters>]
```

### <span data-ttu-id="b6e30-109">ProcessIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="b6e30-109">ProcessIdParameterSet</span></span>

```
Get-PSHostProcessInfo [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="b6e30-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b6e30-110">DESCRIPTION</span></span>

<span data-ttu-id="b6e30-111">De `Get-PSHostProcessInfo` cmdlet haalt informatie op over de Power shell-hostproces processen die op de lokale computer worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b6e30-111">The `Get-PSHostProcessInfo` cmdlet gets information about PowerShell host processes running on the local computer.</span></span>

<span data-ttu-id="b6e30-112">Vanaf Power shell 6,2 wordt deze cmdlet ondersteund op niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="b6e30-112">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

## <span data-ttu-id="b6e30-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b6e30-113">EXAMPLES</span></span>

### <span data-ttu-id="b6e30-114">1: een lijst met Power shell-hosts die worden uitgevoerd op het systeem ophalen</span><span class="sxs-lookup"><span data-stu-id="b6e30-114">1: Get a list of PowerShell hosts running on the system</span></span>

```powershell
Get-PSHostProcessInfo
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell      11204 DefaultAppDomain
pwsh            13912 DefaultAppDomain
```

### <span data-ttu-id="b6e30-115">2: informatie over de Power shell-host ophalen voor een specifieke proces naam</span><span class="sxs-lookup"><span data-stu-id="b6e30-115">2: Get PowerShell host information for a specific process name</span></span>

```powershell
Get-PSHostProcessInfo -Name pwsh
```

```Output
ProcessName ProcessId AppDomainName
----------- --------- -------------
pwsh            13912 DefaultAppDomain
```

## <span data-ttu-id="b6e30-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b6e30-116">PARAMETERS</span></span>

### <span data-ttu-id="b6e30-117">-Id</span><span class="sxs-lookup"><span data-stu-id="b6e30-117">-Id</span></span>

<span data-ttu-id="b6e30-118">Hiermee geeft u een proces met de proces-ID op.</span><span class="sxs-lookup"><span data-stu-id="b6e30-118">Specifies a process by the process ID.</span></span> <span data-ttu-id="b6e30-119">Voer de cmdlet uit om een proces-ID op te halen `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="b6e30-119">To get a process ID, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b6e30-120">-Name</span><span class="sxs-lookup"><span data-stu-id="b6e30-120">-Name</span></span>

<span data-ttu-id="b6e30-121">Hiermee geeft u een proces op met de proces naam.</span><span class="sxs-lookup"><span data-stu-id="b6e30-121">Specifies a process by the process name.</span></span> <span data-ttu-id="b6e30-122">Voer de cmdlet uit om een proces naam op te halen `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="b6e30-122">To get a process name, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b6e30-123">-Proces</span><span class="sxs-lookup"><span data-stu-id="b6e30-123">-Process</span></span>

<span data-ttu-id="b6e30-124">Hiermee geeft u een proces op voor het proces object.</span><span class="sxs-lookup"><span data-stu-id="b6e30-124">Specifies a process by the process object.</span></span> <span data-ttu-id="b6e30-125">De eenvoudigste manier om deze para meter te gebruiken is het opslaan van de resultaten van een `Get-Process` opdracht die het proces retourneert dat u in een variabele wilt invoeren, en vervolgens geeft u de variabele op als de waarde van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="b6e30-125">The simplest way to use this parameter is to save the results of a `Get-Process` command that returns process that you want to enter in a variable, and then specify the variable as the value of this parameter.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b6e30-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b6e30-126">CommonParameters</span></span>

<span data-ttu-id="b6e30-127">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b6e30-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b6e30-128">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b6e30-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b6e30-129">INVOER</span><span class="sxs-lookup"><span data-stu-id="b6e30-129">INPUTS</span></span>

### <span data-ttu-id="b6e30-130">System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="b6e30-130">System.Diagnostics.Process</span></span>

<span data-ttu-id="b6e30-131">U kunt een **proces** object door sluizen van `Get-Process` naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b6e30-131">You can pipe a **Process** object from `Get-Process` to this cmdlet.</span></span>

## <span data-ttu-id="b6e30-132">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b6e30-132">OUTPUTS</span></span>

### <span data-ttu-id="b6e30-133">Micro soft. Power shell. commands. PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="b6e30-133">Microsoft.PowerShell.Commands.PSHostProcessInfo</span></span>

## <span data-ttu-id="b6e30-134">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b6e30-134">NOTES</span></span>

## <span data-ttu-id="b6e30-135">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b6e30-135">RELATED LINKS</span></span>

[<span data-ttu-id="b6e30-136">Get-Process</span><span class="sxs-lookup"><span data-stu-id="b6e30-136">Get-Process</span></span>](../Microsoft.PowerShell.Management/get-process.md)

