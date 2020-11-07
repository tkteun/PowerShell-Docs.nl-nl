---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: 1734758d34e89020f579fffa217cef58eb222736
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344045"
---
# <span data-ttu-id="5d81c-103">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="5d81c-103">Exit-PSHostProcess</span></span>

## <span data-ttu-id="5d81c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="5d81c-104">SYNOPSIS</span></span>
<span data-ttu-id="5d81c-105">Hiermee sluit u een interactieve sessie met een lokaal proces.</span><span class="sxs-lookup"><span data-stu-id="5d81c-105">Closes an interactive session with a local process.</span></span>

## <span data-ttu-id="5d81c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="5d81c-106">SYNTAX</span></span>

```
Exit-PSHostProcess [<CommonParameters>]
```

## <span data-ttu-id="5d81c-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5d81c-107">DESCRIPTION</span></span>

<span data-ttu-id="5d81c-108">De `Exit-PSHostProcess` cmdlet sluit een interactieve sessie met een lokaal proces dat u hebt geopend door de cmdlet uit te voeren `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="5d81c-108">The `Exit-PSHostProcess` cmdlet closes an interactive session with a local process that you have opened by running the `Enter-PSHostProcess` cmdlet.</span></span> <span data-ttu-id="5d81c-109">U voert de `Exit-PSHostProcess` cmdlet uit vanuit het proces, wanneer u klaar bent met het opsporen van fouten of het oplossen van problemen met een script dat in een proces wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5d81c-109">You run the `Exit-PSHostProcess` cmdlet from within the process, when you are finished debugging or troubleshooting a script that is running within a process.</span></span> <span data-ttu-id="5d81c-110">Vanaf Power shell 6,2 wordt deze cmdlet ondersteund op niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="5d81c-110">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

## <span data-ttu-id="5d81c-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="5d81c-111">EXAMPLES</span></span>

### <span data-ttu-id="5d81c-112">Voor beeld 1: een proces afsluiten</span><span class="sxs-lookup"><span data-stu-id="5d81c-112">Example 1: Exit a process</span></span>

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

<span data-ttu-id="5d81c-113">In dit voor beeld hebt u in een actief proces gewerkt om fouten op te sporen in een script dat wordt uitgevoerd in een runs Pace in het proces, zoals beschreven in `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="5d81c-113">In this example, you have been working in an active process to debug a script running in a runspace in the process, as described in `Enter-PSHostProcess`.</span></span> <span data-ttu-id="5d81c-114">Nadat u de `exit` opdracht voor het fout opsporingsprogramma hebt getypt, voert u de `Exit-PSHostProcess` cmdlet uit om uw interactieve sessie met het proces te sluiten.</span><span class="sxs-lookup"><span data-stu-id="5d81c-114">After you type the `exit` command to exit the debugger, run the `Exit-PSHostProcess` cmdlet to close your interactive session with the process.</span></span>
<span data-ttu-id="5d81c-115">De cmdlet sluit uw sessie in het proces en keert u terug naar de `PS C:\>` prompt.</span><span class="sxs-lookup"><span data-stu-id="5d81c-115">The cmdlet closes your session in the process, and returns you to the `PS C:\>` prompt.</span></span>

## <span data-ttu-id="5d81c-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5d81c-116">PARAMETERS</span></span>

### <span data-ttu-id="5d81c-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5d81c-117">CommonParameters</span></span>

<span data-ttu-id="5d81c-118">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5d81c-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5d81c-119">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5d81c-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5d81c-120">INVOER</span><span class="sxs-lookup"><span data-stu-id="5d81c-120">INPUTS</span></span>

## <span data-ttu-id="5d81c-121">UITVOER</span><span class="sxs-lookup"><span data-stu-id="5d81c-121">OUTPUTS</span></span>

## <span data-ttu-id="5d81c-122">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="5d81c-122">NOTES</span></span>

## <span data-ttu-id="5d81c-123">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="5d81c-123">RELATED LINKS</span></span>

[<span data-ttu-id="5d81c-124">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="5d81c-124">Enter-PSHostProcess</span></span>](Enter-PSHostProcess.md)
