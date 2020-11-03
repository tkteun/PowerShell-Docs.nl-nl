---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 86903ca648ff3ee58ec939143b7881741827f453
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93249317"
---
# <span data-ttu-id="fbbd6-103">Stop-Transcript</span><span class="sxs-lookup"><span data-stu-id="fbbd6-103">Stop-Transcript</span></span>

## <span data-ttu-id="fbbd6-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="fbbd6-104">SYNOPSIS</span></span>
<span data-ttu-id="fbbd6-105">Hiermee wordt een transcript gestopt.</span><span class="sxs-lookup"><span data-stu-id="fbbd6-105">Stops a transcript.</span></span>

## <span data-ttu-id="fbbd6-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="fbbd6-106">SYNTAX</span></span>

```
Stop-Transcript [<CommonParameters>]
```

## <span data-ttu-id="fbbd6-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fbbd6-107">DESCRIPTION</span></span>

<span data-ttu-id="fbbd6-108">De `Stop-Transcript` cmdlet stopt een transcript dat is gestart door de `Start-Transcript` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fbbd6-108">The `Stop-Transcript` cmdlet stops a transcript that was started by the `Start-Transcript` cmdlet.</span></span>
<span data-ttu-id="fbbd6-109">U kunt ook een sessie beëindigen om een transcript te stoppen.</span><span class="sxs-lookup"><span data-stu-id="fbbd6-109">Alternatively, you can end a session to stop a transcript.</span></span>

## <span data-ttu-id="fbbd6-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="fbbd6-110">EXAMPLES</span></span>

### <span data-ttu-id="fbbd6-111">Voor beeld 1: alle transcripten stoppen</span><span class="sxs-lookup"><span data-stu-id="fbbd6-111">Example 1: Stop all transcripts</span></span>

```powershell
Stop-Transcript
```

<span data-ttu-id="fbbd6-112">Met deze opdracht worden alle transcripten gestopt.</span><span class="sxs-lookup"><span data-stu-id="fbbd6-112">This command stops all transcripts.</span></span>

## <span data-ttu-id="fbbd6-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fbbd6-113">PARAMETERS</span></span>

### <span data-ttu-id="fbbd6-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fbbd6-114">CommonParameters</span></span>

<span data-ttu-id="fbbd6-115">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fbbd6-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fbbd6-116">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fbbd6-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fbbd6-117">INVOER</span><span class="sxs-lookup"><span data-stu-id="fbbd6-117">INPUTS</span></span>

### <span data-ttu-id="fbbd6-118">Geen</span><span class="sxs-lookup"><span data-stu-id="fbbd6-118">None</span></span>

<span data-ttu-id="fbbd6-119">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fbbd6-119">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="fbbd6-120">UITVOER</span><span class="sxs-lookup"><span data-stu-id="fbbd6-120">OUTPUTS</span></span>

### <span data-ttu-id="fbbd6-121">System. String</span><span class="sxs-lookup"><span data-stu-id="fbbd6-121">System.String</span></span>

<span data-ttu-id="fbbd6-122">Deze cmdlet retourneert een teken reeks die een status bericht en het pad naar het uitvoer bestand bevat.</span><span class="sxs-lookup"><span data-stu-id="fbbd6-122">This cmdlet returns a string that contains a status message and the path to the output file.</span></span>

## <span data-ttu-id="fbbd6-123">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="fbbd6-123">NOTES</span></span>

* <span data-ttu-id="fbbd6-124">Als er geen transcript is gestart, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="fbbd6-124">If a transcript has not been started, the command fails.</span></span>

*

## <span data-ttu-id="fbbd6-125">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="fbbd6-125">RELATED LINKS</span></span>

[<span data-ttu-id="fbbd6-126">Start-transcript</span><span class="sxs-lookup"><span data-stu-id="fbbd6-126">Start-Transcript</span></span>](Start-Transcript.md)

