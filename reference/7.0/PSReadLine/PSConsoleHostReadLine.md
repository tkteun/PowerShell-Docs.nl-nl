---
external help file: PSReadLine-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/psconsolehostreadline?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSConsoleHostReadLine
ms.openlocfilehash: 47d97fd50294a0dda1064bad123dc17931f8a470
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253196"
---
# <span data-ttu-id="a8f13-103">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="a8f13-103">PSConsoleHostReadLine</span></span>

## <span data-ttu-id="a8f13-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a8f13-104">SYNOPSIS</span></span>
<span data-ttu-id="a8f13-105">Deze functie is het belangrijkste toegangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="a8f13-105">This function is the main entry point for PSReadLine.</span></span>

## <span data-ttu-id="a8f13-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a8f13-106">SYNTAX</span></span>

```
PSConsoleHostReadLine
```

## <span data-ttu-id="a8f13-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a8f13-107">DESCRIPTION</span></span>

<span data-ttu-id="a8f13-108">`PSConsoleHostReadLine` is het belangrijkste ingangs punt voor de PSReadLine-module.</span><span class="sxs-lookup"><span data-stu-id="a8f13-108">`PSConsoleHostReadLine` is the main entry point for the PSReadLine module.</span></span> <span data-ttu-id="a8f13-109">De Power shell-console host laadt automatisch de PSReadLine-module en roept deze functie aan.</span><span class="sxs-lookup"><span data-stu-id="a8f13-109">The PowerShell console host automatically loads the PSReadLine module and calls this function.</span></span> <span data-ttu-id="a8f13-110">Onder normale bedrijfs omstandigheden is deze functie niet bedoeld om te worden gebruikt vanaf de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="a8f13-110">Under normal operating conditions, this function is not intended to be used from the command line.</span></span>

<span data-ttu-id="a8f13-111">Het uitbreidings punt `PSConsoleHostReadLine` is speciaal voor de host van de console.</span><span class="sxs-lookup"><span data-stu-id="a8f13-111">The extension point `PSConsoleHostReadLine` is special to the console host.</span></span> <span data-ttu-id="a8f13-112">De host roept een alias, functie of script aan met deze naam.</span><span class="sxs-lookup"><span data-stu-id="a8f13-112">The host calls any alias, function, or script with this name.</span></span> <span data-ttu-id="a8f13-113">PSReadLine definieert deze functie zodat deze wordt aangeroepen vanaf de-console-host.</span><span class="sxs-lookup"><span data-stu-id="a8f13-113">PSReadLine defines this function so that it is called from the console host.</span></span>

## <span data-ttu-id="a8f13-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a8f13-114">EXAMPLES</span></span>

### <span data-ttu-id="a8f13-115">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="a8f13-115">Example 1</span></span>

<span data-ttu-id="a8f13-116">Deze functie is niet bedoeld om te worden gebruikt vanaf de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="a8f13-116">This function is not intended to be used from the command line.</span></span>

## <span data-ttu-id="a8f13-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a8f13-117">PARAMETERS</span></span>

## <span data-ttu-id="a8f13-118">INVOER</span><span class="sxs-lookup"><span data-stu-id="a8f13-118">INPUTS</span></span>

### <span data-ttu-id="a8f13-119">Geen</span><span class="sxs-lookup"><span data-stu-id="a8f13-119">None</span></span>

## <span data-ttu-id="a8f13-120">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a8f13-120">OUTPUTS</span></span>

### <span data-ttu-id="a8f13-121">Geen</span><span class="sxs-lookup"><span data-stu-id="a8f13-121">None</span></span>

## <span data-ttu-id="a8f13-122">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a8f13-122">NOTES</span></span>

## <span data-ttu-id="a8f13-123">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a8f13-123">RELATED LINKS</span></span>

[<span data-ttu-id="a8f13-124">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="a8f13-124">about_PSReadLine</span></span>](./About/about_PSReadLine.md)
