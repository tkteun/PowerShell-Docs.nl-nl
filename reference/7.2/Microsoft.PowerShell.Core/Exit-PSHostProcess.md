---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: a1a8c6fcc16bcddc3bfcdade56cd75aadd179b74
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705641"
---
# <span data-ttu-id="aa8f9-102">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="aa8f9-102">Exit-PSHostProcess</span></span>

## <span data-ttu-id="aa8f9-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="aa8f9-103">SYNOPSIS</span></span>
<span data-ttu-id="aa8f9-104">Hiermee sluit u een interactieve sessie met een lokaal proces.</span><span class="sxs-lookup"><span data-stu-id="aa8f9-104">Closes an interactive session with a local process.</span></span>

## <span data-ttu-id="aa8f9-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="aa8f9-105">SYNTAX</span></span>

```
Exit-PSHostProcess [<CommonParameters>]
```

## <span data-ttu-id="aa8f9-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="aa8f9-106">DESCRIPTION</span></span>

<span data-ttu-id="aa8f9-107">De `Exit-PSHostProcess` cmdlet sluit een interactieve sessie met een lokaal proces dat u hebt geopend door de cmdlet uit te voeren `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="aa8f9-107">The `Exit-PSHostProcess` cmdlet closes an interactive session with a local process that you have opened by running the `Enter-PSHostProcess` cmdlet.</span></span> <span data-ttu-id="aa8f9-108">U voert de `Exit-PSHostProcess` cmdlet uit vanuit het proces, wanneer u klaar bent met het opsporen van fouten of het oplossen van problemen met een script dat in een proces wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aa8f9-108">You run the `Exit-PSHostProcess` cmdlet from within the process, when you are finished debugging or troubleshooting a script that is running within a process.</span></span> <span data-ttu-id="aa8f9-109">Vanaf Power shell 6,2 wordt deze cmdlet ondersteund op niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="aa8f9-109">Beginning in PowerShell 6.2, this cmdlet is supported on non-Windows platforms.</span></span>

## <span data-ttu-id="aa8f9-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="aa8f9-110">EXAMPLES</span></span>

### <span data-ttu-id="aa8f9-111">Voor beeld 1: een proces afsluiten</span><span class="sxs-lookup"><span data-stu-id="aa8f9-111">Example 1: Exit a process</span></span>

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

<span data-ttu-id="aa8f9-112">In dit voor beeld hebt u in een actief proces gewerkt om fouten op te sporen in een script dat wordt uitgevoerd in een runs Pace in het proces, zoals beschreven in `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="aa8f9-112">In this example, you have been working in an active process to debug a script running in a runspace in the process, as described in `Enter-PSHostProcess`.</span></span> <span data-ttu-id="aa8f9-113">Nadat u de `exit` opdracht voor het fout opsporingsprogramma hebt getypt, voert u de `Exit-PSHostProcess` cmdlet uit om uw interactieve sessie met het proces te sluiten.</span><span class="sxs-lookup"><span data-stu-id="aa8f9-113">After you type the `exit` command to exit the debugger, run the `Exit-PSHostProcess` cmdlet to close your interactive session with the process.</span></span>
<span data-ttu-id="aa8f9-114">De cmdlet sluit uw sessie in het proces en keert u terug naar de `PS C:\>` prompt.</span><span class="sxs-lookup"><span data-stu-id="aa8f9-114">The cmdlet closes your session in the process, and returns you to the `PS C:\>` prompt.</span></span>

## <span data-ttu-id="aa8f9-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aa8f9-115">PARAMETERS</span></span>

### <span data-ttu-id="aa8f9-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aa8f9-116">CommonParameters</span></span>

<span data-ttu-id="aa8f9-117">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aa8f9-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aa8f9-118">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aa8f9-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aa8f9-119">INVOER</span><span class="sxs-lookup"><span data-stu-id="aa8f9-119">INPUTS</span></span>

## <span data-ttu-id="aa8f9-120">UITVOER</span><span class="sxs-lookup"><span data-stu-id="aa8f9-120">OUTPUTS</span></span>

## <span data-ttu-id="aa8f9-121">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="aa8f9-121">NOTES</span></span>

## <span data-ttu-id="aa8f9-122">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="aa8f9-122">RELATED LINKS</span></span>

[<span data-ttu-id="aa8f9-123">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="aa8f9-123">Enter-PSHostProcess</span></span>](Enter-PSHostProcess.md)

