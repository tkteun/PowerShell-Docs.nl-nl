---
title: Help op basis van opmerkingen in scripts plaatsen
ms.date: 09/12/2016
ms.openlocfilehash: a3ade6c3138826b924939056b9d1ffb233006d44
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893183"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="2228b-102">Help op basis van opmerkingen in scripts plaatsen</span><span class="sxs-lookup"><span data-stu-id="2228b-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="2228b-103">In dit onderwerp wordt uitgelegd waar u op opmerkingen gebaseerde hulp voor een script kunt plaatsen zodat de `Get-Help` cmdlet het Help-onderwerp op basis van opmerkingen koppelt aan scripts en niet met functies die mogelijk in het script zijn.</span><span class="sxs-lookup"><span data-stu-id="2228b-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="2228b-104">Waar kunt u op opmerkingen gebaseerde hulp voor een script plaatsen</span><span class="sxs-lookup"><span data-stu-id="2228b-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="2228b-105">Aan het begin van het script bestand.</span><span class="sxs-lookup"><span data-stu-id="2228b-105">At the beginning of the script file.</span></span>

  <span data-ttu-id="2228b-106">De Help van het script kan alleen worden voorafgegaan door opmerkingen en lege regels in het script.</span><span class="sxs-lookup"><span data-stu-id="2228b-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="2228b-107">Aan het einde van het script bestand.</span><span class="sxs-lookup"><span data-stu-id="2228b-107">At the end of the script file.</span></span>

  <span data-ttu-id="2228b-108">Als het eerste item in de hoofd tekst van het script (na de Help) een functie declaratie is, moeten er ten minste twee lege regels tussen het einde van de script-Help en de functie declaratie zijn.</span><span class="sxs-lookup"><span data-stu-id="2228b-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="2228b-109">Anders wordt de Help geïnterpreteerd als hulp voor de functie, en niet bij het script.</span><span class="sxs-lookup"><span data-stu-id="2228b-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="2228b-110">Voor beelden van de plaatsing van een Help in een script</span><span class="sxs-lookup"><span data-stu-id="2228b-110">Examples of Help Placement in a Script</span></span>

<span data-ttu-id="2228b-111">In de volgende voor beelden ziet u de plaatsings opties voor Help op basis van opmerkingen voor een script.</span><span class="sxs-lookup"><span data-stu-id="2228b-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="2228b-112">Help aan het begin van een script</span><span class="sxs-lookup"><span data-stu-id="2228b-112">Help at the Beginning of a Script</span></span>

<span data-ttu-id="2228b-113">In het volgende voor beeld wordt een opmerking weer gegeven aan het begin van een script.</span><span class="sxs-lookup"><span data-stu-id="2228b-113">The following example shows comment-based at the beginning of a script.</span></span>

```powershell
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="2228b-114">Help aan het einde van een script</span><span class="sxs-lookup"><span data-stu-id="2228b-114">Help at the End of a Script</span></span>

 <span data-ttu-id="2228b-115">In het volgende voor beeld wordt een opmerking weer gegeven aan het einde van een script.</span><span class="sxs-lookup"><span data-stu-id="2228b-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>
```
