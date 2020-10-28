---
ms.date: 09/12/2016
ms.topic: reference
title: Help op basis van opmerkingen in scripts plaatsen
description: Help op basis van opmerkingen in scripts plaatsen
ms.openlocfilehash: b0d32b7ab063269085899a643b0c3a17da2073fc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645437"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="178f0-103">Help op basis van opmerkingen in scripts plaatsen</span><span class="sxs-lookup"><span data-stu-id="178f0-103">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="178f0-104">In dit onderwerp wordt uitgelegd waar u op opmerkingen gebaseerde hulp voor een script kunt plaatsen zodat de `Get-Help` cmdlet het Help-onderwerp op basis van opmerkingen koppelt aan scripts en niet met functies die mogelijk in het script zijn.</span><span class="sxs-lookup"><span data-stu-id="178f0-104">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="178f0-105">Waar kunt u Comment-Based Help voor een script plaatsen</span><span class="sxs-lookup"><span data-stu-id="178f0-105">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="178f0-106">Aan het begin van het script bestand.</span><span class="sxs-lookup"><span data-stu-id="178f0-106">At the beginning of the script file.</span></span>

  <span data-ttu-id="178f0-107">De Help van het script kan alleen worden voorafgegaan door opmerkingen en lege regels in het script.</span><span class="sxs-lookup"><span data-stu-id="178f0-107">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="178f0-108">Aan het einde van het script bestand.</span><span class="sxs-lookup"><span data-stu-id="178f0-108">At the end of the script file.</span></span>

  <span data-ttu-id="178f0-109">Als het eerste item in de hoofd tekst van het script (na de Help) een functie declaratie is, moeten er ten minste twee lege regels tussen het einde van de script-Help en de functie declaratie zijn.</span><span class="sxs-lookup"><span data-stu-id="178f0-109">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="178f0-110">Anders wordt de Help geïnterpreteerd als hulp voor de functie, en niet bij het script.</span><span class="sxs-lookup"><span data-stu-id="178f0-110">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="178f0-111">Voor beelden van de plaatsing van een Help in een script</span><span class="sxs-lookup"><span data-stu-id="178f0-111">Examples of Help Placement in a Script</span></span>

<span data-ttu-id="178f0-112">In de volgende voor beelden ziet u de plaatsings opties voor Help op basis van opmerkingen voor een script.</span><span class="sxs-lookup"><span data-stu-id="178f0-112">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="178f0-113">Help aan het begin van een script</span><span class="sxs-lookup"><span data-stu-id="178f0-113">Help at the Beginning of a Script</span></span>

<span data-ttu-id="178f0-114">In het volgende voor beeld wordt een opmerking weer gegeven aan het begin van een script.</span><span class="sxs-lookup"><span data-stu-id="178f0-114">The following example shows comment-based at the beginning of a script.</span></span>

```powershell
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="178f0-115">Help aan het einde van een script</span><span class="sxs-lookup"><span data-stu-id="178f0-115">Help at the End of a Script</span></span>

 <span data-ttu-id="178f0-116">In het volgende voor beeld wordt een opmerking weer gegeven aan het einde van een script.</span><span class="sxs-lookup"><span data-stu-id="178f0-116">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>
```
