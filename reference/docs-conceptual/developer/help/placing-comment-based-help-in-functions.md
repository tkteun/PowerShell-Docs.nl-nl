---
ms.date: 09/12/2016
ms.topic: reference
title: Help op basis van opmerkingen in functies plaatsen
description: Help op basis van opmerkingen in functies plaatsen
ms.openlocfilehash: 3bd72f0c71d8f6ad54c43c99f044423c072fdeeb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658214"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="6c562-103">Help op basis van opmerkingen in functies plaatsen</span><span class="sxs-lookup"><span data-stu-id="6c562-103">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="6c562-104">In dit onderwerp wordt uitgelegd waar u op opmerkingen gebaseerde hulp voor een functie kunt plaatsen zodat de `Get-Help` cmdlet het Help-onderwerp op basis van opmerkingen koppelt aan de juiste functie.</span><span class="sxs-lookup"><span data-stu-id="6c562-104">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="6c562-105">Waar kunt u Comment-Based hulp voor een functie plaatsen</span><span class="sxs-lookup"><span data-stu-id="6c562-105">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="6c562-106">Aan het begin van de hoofd tekst van de functie.</span><span class="sxs-lookup"><span data-stu-id="6c562-106">At the beginning of the function body.</span></span>

- <span data-ttu-id="6c562-107">Aan het einde van de hoofd tekst van de functie.</span><span class="sxs-lookup"><span data-stu-id="6c562-107">At the end of the function body.</span></span>

- <span data-ttu-id="6c562-108">Vóór het `Function` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="6c562-108">Before the `Function` keyword.</span></span> <span data-ttu-id="6c562-109">Wanneer de functie zich in een script of script module bevindt, kan er niet meer dan één lege regel tussen de laatste regel van de op opmerkingen gebaseerde Help en het `Function` tref woord zijn.</span><span class="sxs-lookup"><span data-stu-id="6c562-109">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="6c562-110">Als dat niet het geval is, `Get-Help` koppelt u de Help aan het script, niet met de functie.</span><span class="sxs-lookup"><span data-stu-id="6c562-110">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="6c562-111">Voor beelden van de plaatsing van een Help in een functie</span><span class="sxs-lookup"><span data-stu-id="6c562-111">Examples of Help Placement in a Function</span></span>

<span data-ttu-id="6c562-112">In de volgende voor beelden ziet u de drie plaatsings opties voor op opmerkingen gebaseerde Help voor een functie.</span><span class="sxs-lookup"><span data-stu-id="6c562-112">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="6c562-113">Help aan het begin van een functie hoofd tekst</span><span class="sxs-lookup"><span data-stu-id="6c562-113">Help at the Beginning of a Function Body</span></span>

<span data-ttu-id="6c562-114">In het volgende voor beeld wordt aan het begin van een functie hoofdtekst een opmerking weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6c562-114">The following example shows comment-based at the beginning of a function body.</span></span>

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

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="6c562-115">Help aan het einde van een functie hoofd tekst</span><span class="sxs-lookup"><span data-stu-id="6c562-115">Help at the End of a Function Body</span></span>

 <span data-ttu-id="6c562-116">In het volgende voor beeld wordt een opmerking weer gegeven aan het einde van de hoofd tekst van een functie.</span><span class="sxs-lookup"><span data-stu-id="6c562-116">The following example shows comment-based at the end of a function body.</span></span>

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

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="6c562-117">Help voor het tref woord function</span><span class="sxs-lookup"><span data-stu-id="6c562-117">Help Before the Function Keyword</span></span>

 <span data-ttu-id="6c562-118">In de volgende voor beelden ziet u opmerkingen op basis van de regel voor het gereserveerde woord function.</span><span class="sxs-lookup"><span data-stu-id="6c562-118">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell
<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}
```
