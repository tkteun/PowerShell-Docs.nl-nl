---
title: Help in functies op basis van opmerkingen plaatsen | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: 898225a582c7ed25f746dec7f84012db1ae60b98
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557058"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="45b58-102">Help op basis van opmerkingen in functies plaatsen</span><span class="sxs-lookup"><span data-stu-id="45b58-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="45b58-103">In dit onderwerp wordt uitgelegd waar u op opmerkingen gebaseerde hulp voor een functie kunt plaatsen zodat de `Get-Help` cmdlet het Help-onderwerp op basis van opmerkingen koppelt aan de juiste functie.</span><span class="sxs-lookup"><span data-stu-id="45b58-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="45b58-104">Waar kunt u op opmerkingen gebaseerde hulp voor een functie plaatsen</span><span class="sxs-lookup"><span data-stu-id="45b58-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="45b58-105">Aan het begin van de hoofd tekst van de functie.</span><span class="sxs-lookup"><span data-stu-id="45b58-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="45b58-106">Aan het einde van de hoofd tekst van de functie.</span><span class="sxs-lookup"><span data-stu-id="45b58-106">At the end of the function body.</span></span>

- <span data-ttu-id="45b58-107">Vóór het `Function` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="45b58-107">Before the `Function` keyword.</span></span> <span data-ttu-id="45b58-108">Wanneer de functie zich in een script of script module bevindt, kan er niet meer dan één lege regel tussen de laatste regel van de op opmerkingen gebaseerde Help en het `Function` tref woord zijn.</span><span class="sxs-lookup"><span data-stu-id="45b58-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="45b58-109">Als dat niet het geval is, `Get-Help` koppelt u de Help aan het script, niet met de functie.</span><span class="sxs-lookup"><span data-stu-id="45b58-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="45b58-110">Voor beelden van de plaatsing van een Help in een functie</span><span class="sxs-lookup"><span data-stu-id="45b58-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="45b58-111">In de volgende voor beelden ziet u de drie plaatsings opties voor op opmerkingen gebaseerde Help voor een functie.</span><span class="sxs-lookup"><span data-stu-id="45b58-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="45b58-112">Help aan het begin van een functie hoofd tekst</span><span class="sxs-lookup"><span data-stu-id="45b58-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="45b58-113">In het volgende voor beeld wordt aan het begin van een functie hoofdtekst een opmerking weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="45b58-113">The following example shows comment-based at the beginning of a function body.</span></span>

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="45b58-114">Help aan het einde van een functie hoofd tekst</span><span class="sxs-lookup"><span data-stu-id="45b58-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="45b58-115">In het volgende voor beeld wordt een opmerking weer gegeven aan het einde van de hoofd tekst van een functie.</span><span class="sxs-lookup"><span data-stu-id="45b58-115">The following example shows comment-based at the end of a function body.</span></span>

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="45b58-116">Help voor het tref woord function</span><span class="sxs-lookup"><span data-stu-id="45b58-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="45b58-117">In de volgende voor beelden ziet u opmerkingen op basis van de regel voor het gereserveerde woord function.</span><span class="sxs-lookup"><span data-stu-id="45b58-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```
