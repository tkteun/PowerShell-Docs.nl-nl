---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 16b41711e98276fee37d56f77f57e7372daa4cf3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705750"
---
# <span data-ttu-id="c2b1e-102">Stop-Transcript</span><span class="sxs-lookup"><span data-stu-id="c2b1e-102">Stop-Transcript</span></span>

## <span data-ttu-id="c2b1e-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c2b1e-103">SYNOPSIS</span></span>
<span data-ttu-id="c2b1e-104">Hiermee wordt een transcript gestopt.</span><span class="sxs-lookup"><span data-stu-id="c2b1e-104">Stops a transcript.</span></span>

## <span data-ttu-id="c2b1e-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c2b1e-105">SYNTAX</span></span>

```
Stop-Transcript [<CommonParameters>]
```

## <span data-ttu-id="c2b1e-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c2b1e-106">DESCRIPTION</span></span>

<span data-ttu-id="c2b1e-107">De `Stop-Transcript` cmdlet stopt een transcript dat is gestart door de `Start-Transcript` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c2b1e-107">The `Stop-Transcript` cmdlet stops a transcript that was started by the `Start-Transcript` cmdlet.</span></span>
<span data-ttu-id="c2b1e-108">U kunt ook een sessie beëindigen om een transcript te stoppen.</span><span class="sxs-lookup"><span data-stu-id="c2b1e-108">Alternatively, you can end a session to stop a transcript.</span></span>

## <span data-ttu-id="c2b1e-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c2b1e-109">EXAMPLES</span></span>

### <span data-ttu-id="c2b1e-110">Voor beeld 1: alle transcripten stoppen</span><span class="sxs-lookup"><span data-stu-id="c2b1e-110">Example 1: Stop all transcripts</span></span>

```powershell
Stop-Transcript
```

<span data-ttu-id="c2b1e-111">Met deze opdracht worden alle transcripten gestopt.</span><span class="sxs-lookup"><span data-stu-id="c2b1e-111">This command stops all transcripts.</span></span>

## <span data-ttu-id="c2b1e-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c2b1e-112">PARAMETERS</span></span>

### <span data-ttu-id="c2b1e-113">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c2b1e-113">CommonParameters</span></span>

<span data-ttu-id="c2b1e-114">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c2b1e-114">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c2b1e-115">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c2b1e-115">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c2b1e-116">INVOER</span><span class="sxs-lookup"><span data-stu-id="c2b1e-116">INPUTS</span></span>

### <span data-ttu-id="c2b1e-117">Geen</span><span class="sxs-lookup"><span data-stu-id="c2b1e-117">None</span></span>

<span data-ttu-id="c2b1e-118">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c2b1e-118">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c2b1e-119">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c2b1e-119">OUTPUTS</span></span>

### <span data-ttu-id="c2b1e-120">System. String</span><span class="sxs-lookup"><span data-stu-id="c2b1e-120">System.String</span></span>

<span data-ttu-id="c2b1e-121">Deze cmdlet retourneert een teken reeks die een status bericht en het pad naar het uitvoer bestand bevat.</span><span class="sxs-lookup"><span data-stu-id="c2b1e-121">This cmdlet returns a string that contains a status message and the path to the output file.</span></span>

## <span data-ttu-id="c2b1e-122">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c2b1e-122">NOTES</span></span>

* <span data-ttu-id="c2b1e-123">Als er geen transcript is gestart, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="c2b1e-123">If a transcript has not been started, the command fails.</span></span>

*

## <span data-ttu-id="c2b1e-124">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c2b1e-124">RELATED LINKS</span></span>

[<span data-ttu-id="c2b1e-125">Start-transcript</span><span class="sxs-lookup"><span data-stu-id="c2b1e-125">Start-Transcript</span></span>](Start-Transcript.md)

