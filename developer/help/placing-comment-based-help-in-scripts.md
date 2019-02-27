---
title: Help op basis van een opmerking in Scripts plaatsen | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850146"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="47b18-102">Help op basis van opmerkingen in scripts plaatsen</span><span class="sxs-lookup"><span data-stu-id="47b18-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="47b18-103">Dit onderwerp wordt uitgelegd waar u de help voor een script op basis van een opmerking plaatsen zodat het `Get-Help` cmdlet het helponderwerp op basis van een opmerking koppelt met scripts en niet met alle functies die mogelijk in het script.</span><span class="sxs-lookup"><span data-stu-id="47b18-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="47b18-104">Waar plaatst u de Help op basis van een opmerking voor een Script</span><span class="sxs-lookup"><span data-stu-id="47b18-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="47b18-105">Aan het begin van het scriptbestand.</span><span class="sxs-lookup"><span data-stu-id="47b18-105">At the beginning of the script file.</span></span> <span data-ttu-id="47b18-106">Script Help kunt in het script worden voorafgegaan door opmerkingen en lege regels.</span><span class="sxs-lookup"><span data-stu-id="47b18-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="47b18-107">Aan het einde van het scriptbestand.</span><span class="sxs-lookup"><span data-stu-id="47b18-107">At the end of the script file.</span></span>

  <span data-ttu-id="47b18-108">Als het eerste item in de hoofdtekst van het script (na de Help) een functiedeclaratie is, moet er ten minste twee lege regels tussen het einde van het Help-script en de functiedeclaratie.</span><span class="sxs-lookup"><span data-stu-id="47b18-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="47b18-109">Anders wordt de Help geïnterpreteerd als hulp voor de functie niet Help voor het script.</span><span class="sxs-lookup"><span data-stu-id="47b18-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="47b18-110">Voorbeelden van de plaatsing van de Help-informatie in een Script</span><span class="sxs-lookup"><span data-stu-id="47b18-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="47b18-111">De volgende voorbeelden ziet elk van de opties voor plaatsing voor meer informatie over op basis van een opmerking voor een script.</span><span class="sxs-lookup"><span data-stu-id="47b18-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="47b18-112">Help weer bij het begin van een Script</span><span class="sxs-lookup"><span data-stu-id="47b18-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="47b18-113">Het volgende voorbeeld ziet u op basis van een opmerking aan het begin van een script.</span><span class="sxs-lookup"><span data-stu-id="47b18-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="47b18-114">Help weer bij het einde van een Script</span><span class="sxs-lookup"><span data-stu-id="47b18-114">Help at the End of a Script</span></span>

 <span data-ttu-id="47b18-115">Het volgende voorbeeld ziet Opmerking gebaseerde aan het einde van een script.</span><span class="sxs-lookup"><span data-stu-id="47b18-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```