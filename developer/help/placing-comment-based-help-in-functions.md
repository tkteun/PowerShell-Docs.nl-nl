---
title: Help op basis van een opmerking plaatsen in Functions | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083192"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="8667a-102">Help op basis van opmerkingen in functies plaatsen</span><span class="sxs-lookup"><span data-stu-id="8667a-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="8667a-103">Dit onderwerp wordt uitgelegd waar u de help voor een functie op basis van een opmerking plaatsen zodat het `Get-Help` cmdlet het helponderwerp op basis van een opmerking koppelt aan de juiste functie.</span><span class="sxs-lookup"><span data-stu-id="8667a-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="8667a-104">Waar plaatst u de Help op basis van een opmerking voor een functie</span><span class="sxs-lookup"><span data-stu-id="8667a-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="8667a-105">Aan het begin van de hoofdtekst van de functie.</span><span class="sxs-lookup"><span data-stu-id="8667a-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="8667a-106">Aan het einde van de hoofdtekst van de functie.</span><span class="sxs-lookup"><span data-stu-id="8667a-106">At the end of the function body.</span></span>

- <span data-ttu-id="8667a-107">Voordat u de `Function` trefwoord.</span><span class="sxs-lookup"><span data-stu-id="8667a-107">Before the `Function` keyword.</span></span> <span data-ttu-id="8667a-108">Wanneer de functie zich in een script of een scriptmodule, er mag niet meer dan één lege regel tussen de laatste regel van de help op basis van een opmerking en de `Function` trefwoord.</span><span class="sxs-lookup"><span data-stu-id="8667a-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="8667a-109">Anders `Get-Help` koppelt u de help met het script, niet met de functie.</span><span class="sxs-lookup"><span data-stu-id="8667a-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="8667a-110">Voorbeelden van de plaatsing van de Help-informatie in een functie</span><span class="sxs-lookup"><span data-stu-id="8667a-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="8667a-111">De volgende voorbeelden ziet elk van de van de drie plaatsingsopties voor meer informatie over op basis van een opmerking voor een functie.</span><span class="sxs-lookup"><span data-stu-id="8667a-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="8667a-112">Help weer bij het begin van de hoofdtekst van een functie</span><span class="sxs-lookup"><span data-stu-id="8667a-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="8667a-113">Het volgende voorbeeld ziet u op basis van een opmerking aan het begin van de hoofdtekst van een functie.</span><span class="sxs-lookup"><span data-stu-id="8667a-113">The following example shows comment-based at the beginning of a function body.</span></span>

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

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="8667a-114">Help weer bij het einde van de hoofdtekst van een functie</span><span class="sxs-lookup"><span data-stu-id="8667a-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="8667a-115">Het volgende voorbeeld ziet Opmerking gebaseerde aan het einde van de hoofdtekst van een functie.</span><span class="sxs-lookup"><span data-stu-id="8667a-115">The following example shows comment-based at the end of a function body.</span></span>

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

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="8667a-116">Help voor de functie-trefwoord</span><span class="sxs-lookup"><span data-stu-id="8667a-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="8667a-117">De volgende voorbeelden ziet u op basis van een opmerking op de regel voor de functie trefwoord.</span><span class="sxs-lookup"><span data-stu-id="8667a-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```