---
external help file: PSReadLine-help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/psconsolehostreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSConsoleHostReadLine
ms.openlocfilehash: e02f06137395e187cfe86eb1aeb4b30dbb3f09f1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705581"
---
# <span data-ttu-id="161be-102">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="161be-102">PSConsoleHostReadLine</span></span>

## <span data-ttu-id="161be-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="161be-103">SYNOPSIS</span></span>
<span data-ttu-id="161be-104">Deze functie is het belangrijkste toegangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="161be-104">This function is the main entry point for PSReadLine.</span></span>

## <span data-ttu-id="161be-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="161be-105">SYNTAX</span></span>

```
PSConsoleHostReadLine
```

## <span data-ttu-id="161be-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="161be-106">DESCRIPTION</span></span>

<span data-ttu-id="161be-107">`PSConsoleHostReadLine` is het belangrijkste ingangs punt voor de PSReadLine-module.</span><span class="sxs-lookup"><span data-stu-id="161be-107">`PSConsoleHostReadLine` is the main entry point for the PSReadLine module.</span></span> <span data-ttu-id="161be-108">De Power shell-console host laadt automatisch de PSReadLine-module en roept deze functie aan.</span><span class="sxs-lookup"><span data-stu-id="161be-108">The PowerShell console host automatically loads the PSReadLine module and calls this function.</span></span> <span data-ttu-id="161be-109">Onder normale bedrijfs omstandigheden is deze functie niet bedoeld om te worden gebruikt vanaf de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="161be-109">Under normal operating conditions, this function is not intended to be used from the command line.</span></span>

<span data-ttu-id="161be-110">Het uitbreidings punt `PSConsoleHostReadLine` is speciaal voor de host van de console.</span><span class="sxs-lookup"><span data-stu-id="161be-110">The extension point `PSConsoleHostReadLine` is special to the console host.</span></span> <span data-ttu-id="161be-111">De host roept een alias, functie of script aan met deze naam.</span><span class="sxs-lookup"><span data-stu-id="161be-111">The host calls any alias, function, or script with this name.</span></span> <span data-ttu-id="161be-112">PSReadLine definieert deze functie zodat deze wordt aangeroepen vanaf de-console-host.</span><span class="sxs-lookup"><span data-stu-id="161be-112">PSReadLine defines this function so that it is called from the console host.</span></span>

## <span data-ttu-id="161be-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="161be-113">EXAMPLES</span></span>

### <span data-ttu-id="161be-114">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="161be-114">Example 1</span></span>

<span data-ttu-id="161be-115">Deze functie is niet bedoeld om te worden gebruikt vanaf de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="161be-115">This function is not intended to be used from the command line.</span></span>

## <span data-ttu-id="161be-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="161be-116">PARAMETERS</span></span>

## <span data-ttu-id="161be-117">INVOER</span><span class="sxs-lookup"><span data-stu-id="161be-117">INPUTS</span></span>

### <span data-ttu-id="161be-118">Geen</span><span class="sxs-lookup"><span data-stu-id="161be-118">None</span></span>

## <span data-ttu-id="161be-119">UITVOER</span><span class="sxs-lookup"><span data-stu-id="161be-119">OUTPUTS</span></span>

### <span data-ttu-id="161be-120">Geen</span><span class="sxs-lookup"><span data-stu-id="161be-120">None</span></span>

## <span data-ttu-id="161be-121">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="161be-121">NOTES</span></span>

## <span data-ttu-id="161be-122">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="161be-122">RELATED LINKS</span></span>

[<span data-ttu-id="161be-123">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="161be-123">about_PSReadLine</span></span>](./About/about_PSReadLine.md)

