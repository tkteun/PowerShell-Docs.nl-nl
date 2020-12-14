---
description: Hierin wordt beschreven hoe meerdere teken reeksen worden gecombineerd tot één teken reeks met de operator voor samen voegen (-lid).
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_join?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Join
ms.openlocfilehash: d76e95aaeca1b5b94bb1a2216576a985ffb209c0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705375"
---
# <a name="about-join"></a><span data-ttu-id="f3014-103">Samen voegen</span><span class="sxs-lookup"><span data-stu-id="f3014-103">About join</span></span>

## <a name="short-description"></a><span data-ttu-id="f3014-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f3014-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="f3014-105">Hierin wordt beschreven hoe meerdere teken reeksen worden gecombineerd tot één teken reeks met de operator voor samen voegen (-lid).</span><span class="sxs-lookup"><span data-stu-id="f3014-105">Describes how the join operator (-join) combines multiple strings into a single string.</span></span>

## <a name="long-description"></a><span data-ttu-id="f3014-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f3014-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="f3014-107">De operator voor samen voegen voegt een set teken reeksen samen tot één teken reeks.</span><span class="sxs-lookup"><span data-stu-id="f3014-107">The join operator concatenates a set of strings into a single string.</span></span> <span data-ttu-id="f3014-108">De teken reeksen worden toegevoegd aan de resulterende teken reeks in de volg orde waarin ze worden weer gegeven in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="f3014-108">The strings are appended to the resulting string in the order that they appear in the command.</span></span>

### <a name="syntax"></a><span data-ttu-id="f3014-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="f3014-109">Syntax</span></span>

<span data-ttu-id="f3014-110">In het volgende diagram ziet u de syntaxis voor de operator voor samen voegen.</span><span class="sxs-lookup"><span data-stu-id="f3014-110">The following diagram shows the syntax for the join operator.</span></span>

```powershell
-Join <String[]>
<String[]> -Join <Delimiter>
```

#### <a name="parameters"></a><span data-ttu-id="f3014-111">Parameters</span><span class="sxs-lookup"><span data-stu-id="f3014-111">Parameters</span></span>

<span data-ttu-id="f3014-112">Teken reeks []-Hiermee geeft u een of meer teken reeksen moet worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="f3014-112">String[] - Specifies one or more strings to be joined.</span></span>

<span data-ttu-id="f3014-113">Scheidings teken: Hiermee geeft u een of meer tekens op die tussen de aaneengeschakelde teken reeksen worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="f3014-113">Delimiter - Specifies one or more characters placed between the concatenated strings.</span></span> <span data-ttu-id="f3014-114">De standaard waarde is geen scheidings teken ("").</span><span class="sxs-lookup"><span data-stu-id="f3014-114">The default is no delimiter ("").</span></span>

<span data-ttu-id="f3014-115">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f3014-115">Remarks</span></span>

<span data-ttu-id="f3014-116">De monadische samenvoegings operator (-samen voegen <teken reeks [] >) heeft een hogere prioriteit dan een komma.</span><span class="sxs-lookup"><span data-stu-id="f3014-116">The unary join operator (-join <string[]>) has higher precedence than a comma.</span></span> <span data-ttu-id="f3014-117">Als u dus een door komma's gescheiden lijst met teken reeksen verzendt naar de monadische koppelings operator, wordt alleen de eerste teken reeks (vóór de eerste komma) verzonden naar de operator voor samen voegen.</span><span class="sxs-lookup"><span data-stu-id="f3014-117">As a result, if you submit a comma-separated list of strings to the unary join operator, only the first string (before the first comma) is submitted to the join operator.</span></span>

<span data-ttu-id="f3014-118">Als u de monadische samenvoegings operator wilt gebruiken, plaatst u de teken reeksen tussen haakjes of slaat u de teken reeksen op in een variabele. vervolgens verzendt u de variabele om samen te voegen.</span><span class="sxs-lookup"><span data-stu-id="f3014-118">To use the unary join operator, enclose the strings in parentheses, or store the strings in a variable, and then submit the variable to join.</span></span>

<span data-ttu-id="f3014-119">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f3014-119">For example:</span></span>

```powershell
-join "a", "b", "c"
a
b
c

-join ("a", "b", "c")
abc

$z = "a", "b", "c"
-join $z
abc
```

### <a name="examples"></a><span data-ttu-id="f3014-120">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="f3014-120">Examples</span></span>

<span data-ttu-id="f3014-121">Met de volgende instructie worden drie teken reeksen samengevoegd:</span><span class="sxs-lookup"><span data-stu-id="f3014-121">The following statement joins three strings:</span></span>

```powershell
-join ("Windows", "PowerShell", "2.0")
WindowsPowerShell2.0
```

<span data-ttu-id="f3014-122">Met de volgende instructie worden drie teken reeksen gescheiden door een spatie:</span><span class="sxs-lookup"><span data-stu-id="f3014-122">The following statement joins three strings delimited by a space:</span></span>

```powershell
"Windows", "PowerShell", "2.0" -join " "
Windows PowerShell 2.0
```

<span data-ttu-id="f3014-123">In de volgende instructies wordt een scheidings teken met meerdere tekens gebruikt om drie teken reeksen samen te voegen:</span><span class="sxs-lookup"><span data-stu-id="f3014-123">The following statements use a multiple-character delimiter to join three strings:</span></span>

```powershell
$a = "WIND", "S P", "ERSHELL"
$a -join "OW"
WINDOWS POWERSHELL
```

<span data-ttu-id="f3014-124">Met de volgende instructie worden de regels in een hier-teken reeks toegevoegd aan één teken reeks.</span><span class="sxs-lookup"><span data-stu-id="f3014-124">The following statement joins the lines in a here-string into a single string.</span></span> <span data-ttu-id="f3014-125">Omdat een hier-teken reeks één teken reeks is, moeten de lijnen in de teken reeks hier worden gesplitst voordat ze kunnen worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="f3014-125">Because a here-string is one string, the lines in the here-string must be split before they can be joined.</span></span> <span data-ttu-id="f3014-126">U kunt deze methode gebruiken om de teken reeksen opnieuw samen te voegen in een XML-bestand dat is opgeslagen in een hier-teken reeks:</span><span class="sxs-lookup"><span data-stu-id="f3014-126">You can use this method to rejoin the strings in an XML file that has been saved in a here-string:</span></span>

```powershell
$a = @'
a
b
c
'@

(-split $a) -join " "
a b c
```

## <a name="see-also"></a><span data-ttu-id="f3014-127">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="f3014-127">SEE ALSO</span></span>

[<span data-ttu-id="f3014-128">about_Operators</span><span class="sxs-lookup"><span data-stu-id="f3014-128">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="f3014-129">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="f3014-129">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="f3014-130">about_Split</span><span class="sxs-lookup"><span data-stu-id="f3014-130">about_Split</span></span>](about_Split.md)

