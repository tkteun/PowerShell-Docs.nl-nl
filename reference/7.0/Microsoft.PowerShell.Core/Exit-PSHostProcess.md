---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: 381d7d9cb32ed4682729ad304e82bb994a21190d
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93249296"
---
# <span data-ttu-id="3e387-103">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="3e387-103">Exit-PSHostProcess</span></span>

## <span data-ttu-id="3e387-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3e387-104">SYNOPSIS</span></span>
<span data-ttu-id="3e387-105">Hiermee sluit u een interactieve sessie met een lokaal proces.</span><span class="sxs-lookup"><span data-stu-id="3e387-105">Closes an interactive session with a local process.</span></span>

## <span data-ttu-id="3e387-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3e387-106">SYNTAX</span></span>

```
Exit-PSHostProcess [<CommonParameters>]
```

## <span data-ttu-id="3e387-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3e387-107">DESCRIPTION</span></span>

<span data-ttu-id="3e387-108">Met de cmdlet **Exit-PSHostProcess** wordt een interactieve sessie gesloten met een lokaal proces dat u hebt geopend door de Enter-PSHostProcess-cmdlet uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="3e387-108">The **Exit-PSHostProcess** cmdlet closes an interactive session with a local process that you have opened by running the Enter-PSHostProcess cmdlet.</span></span> <span data-ttu-id="3e387-109">U voert de cmdlet **Exit-PSHostProcess** uit vanuit het proces, wanneer u klaar bent met het opsporen van fouten of het oplossen van problemen met een script dat in een proces wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3e387-109">You run the **Exit-PSHostProcess** cmdlet from within the process, when you are finished debugging or troubleshooting a script that is running within a process.</span></span>

## <span data-ttu-id="3e387-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3e387-110">EXAMPLES</span></span>

### <span data-ttu-id="3e387-111">Voor beeld 1: een proces afsluiten</span><span class="sxs-lookup"><span data-stu-id="3e387-111">Example 1: Exit a process</span></span>

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

<span data-ttu-id="3e387-112">In dit voor beeld hebt u in een actief proces gewerkt om fouten op te sporen in een script dat wordt uitgevoerd in een runs Pace in het proces, zoals beschreven in Enter-PSHostProcess.</span><span class="sxs-lookup"><span data-stu-id="3e387-112">In this example, you have been working in an active process to debug a script running in a runspace in the process, as described in Enter-PSHostProcess.</span></span> <span data-ttu-id="3e387-113">Nadat u de opdracht **Exit** hebt getypt om de fout opsporing af te sluiten, voert u de cmdlet **Exit-PSHostProcess** uit om uw interactieve sessie met het proces te sluiten.</span><span class="sxs-lookup"><span data-stu-id="3e387-113">After you type the **exit** command to exit the debugger, run the **Exit-PSHostProcess** cmdlet to close your interactive session with the process.</span></span>
<span data-ttu-id="3e387-114">De cmdlet sluit uw sessie in het proces en keert u terug naar de PS C:- \\ \> prompt.</span><span class="sxs-lookup"><span data-stu-id="3e387-114">The cmdlet closes your session in the process, and returns you to the PS C:\\\> prompt.</span></span>

## <span data-ttu-id="3e387-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3e387-115">PARAMETERS</span></span>

### <span data-ttu-id="3e387-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3e387-116">CommonParameters</span></span>

<span data-ttu-id="3e387-117">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3e387-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3e387-118">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3e387-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3e387-119">INVOER</span><span class="sxs-lookup"><span data-stu-id="3e387-119">INPUTS</span></span>

## <span data-ttu-id="3e387-120">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3e387-120">OUTPUTS</span></span>

## <span data-ttu-id="3e387-121">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3e387-121">NOTES</span></span>

## <span data-ttu-id="3e387-122">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3e387-122">RELATED LINKS</span></span>

[<span data-ttu-id="3e387-123">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="3e387-123">Enter-PSHostProcess</span></span>](Enter-PSHostProcess.md)
