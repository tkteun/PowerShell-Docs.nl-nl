---
description: Hierin wordt beschreven hoe meerdere teken reeksen worden gecombineerd tot één teken reeks met de operator voor samen voegen (-lid).
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_join?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Join
ms.openlocfilehash: 3e5bf4363adbded29dc58facde00f6597abeb697
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252612"
---
# <a name="about-join"></a><span data-ttu-id="5ca5b-104">Samen voegen</span><span class="sxs-lookup"><span data-stu-id="5ca5b-104">About join</span></span>

## <a name="short-description"></a><span data-ttu-id="5ca5b-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5ca5b-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="5ca5b-106">Hierin wordt beschreven hoe meerdere teken reeksen worden gecombineerd tot één teken reeks met de operator voor samen voegen (-lid).</span><span class="sxs-lookup"><span data-stu-id="5ca5b-106">Describes how the join operator (-join) combines multiple strings into a single string.</span></span>

## <a name="long-description"></a><span data-ttu-id="5ca5b-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5ca5b-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="5ca5b-108">De operator voor samen voegen voegt een set teken reeksen samen tot één teken reeks.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-108">The join operator concatenates a set of strings into a single string.</span></span> <span data-ttu-id="5ca5b-109">De teken reeksen worden toegevoegd aan de resulterende teken reeks in de volg orde waarin ze worden weer gegeven in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-109">The strings are appended to the resulting string in the order that they appear in the command.</span></span>

### <a name="syntax"></a><span data-ttu-id="5ca5b-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="5ca5b-110">Syntax</span></span>

<span data-ttu-id="5ca5b-111">In het volgende diagram ziet u de syntaxis voor de operator voor samen voegen.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-111">The following diagram shows the syntax for the join operator.</span></span>

```powershell
-Join <String[]>
<String[]> -Join <Delimiter>
```

#### <a name="parameters"></a><span data-ttu-id="5ca5b-112">Parameters</span><span class="sxs-lookup"><span data-stu-id="5ca5b-112">Parameters</span></span>

<span data-ttu-id="5ca5b-113">Teken reeks []-Hiermee geeft u een of meer teken reeksen moet worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-113">String[] - Specifies one or more strings to be joined.</span></span>

<span data-ttu-id="5ca5b-114">Scheidings teken: Hiermee geeft u een of meer tekens op die tussen de aaneengeschakelde teken reeksen worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-114">Delimiter - Specifies one or more characters placed between the concatenated strings.</span></span> <span data-ttu-id="5ca5b-115">De standaard waarde is geen scheidings teken ("").</span><span class="sxs-lookup"><span data-stu-id="5ca5b-115">The default is no delimiter ("").</span></span>

<span data-ttu-id="5ca5b-116">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5ca5b-116">Remarks</span></span>

<span data-ttu-id="5ca5b-117">De monadische samenvoegings operator (-samen voegen <teken reeks [] >) heeft een hogere prioriteit dan een komma.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-117">The unary join operator (-join <string[]>) has higher precedence than a comma.</span></span> <span data-ttu-id="5ca5b-118">Als u dus een door komma's gescheiden lijst met teken reeksen verzendt naar de monadische koppelings operator, wordt alleen de eerste teken reeks (vóór de eerste komma) verzonden naar de operator voor samen voegen.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-118">As a result, if you submit a comma-separated list of strings to the unary join operator, only the first string (before the first comma) is submitted to the join operator.</span></span>

<span data-ttu-id="5ca5b-119">Als u de monadische samenvoegings operator wilt gebruiken, plaatst u de teken reeksen tussen haakjes of slaat u de teken reeksen op in een variabele. vervolgens verzendt u de variabele om samen te voegen.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-119">To use the unary join operator, enclose the strings in parentheses, or store the strings in a variable, and then submit the variable to join.</span></span>

<span data-ttu-id="5ca5b-120">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="5ca5b-120">For example:</span></span>

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

### <a name="examples"></a><span data-ttu-id="5ca5b-121">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="5ca5b-121">Examples</span></span>

<span data-ttu-id="5ca5b-122">Met de volgende instructie worden drie teken reeksen samengevoegd:</span><span class="sxs-lookup"><span data-stu-id="5ca5b-122">The following statement joins three strings:</span></span>

```powershell
-join ("Windows", "PowerShell", "2.0")
WindowsPowerShell2.0
```

<span data-ttu-id="5ca5b-123">Met de volgende instructie worden drie teken reeksen gescheiden door een spatie:</span><span class="sxs-lookup"><span data-stu-id="5ca5b-123">The following statement joins three strings delimited by a space:</span></span>

```powershell
"Windows", "PowerShell", "2.0" -join " "
Windows PowerShell 2.0
```

<span data-ttu-id="5ca5b-124">In de volgende instructies wordt een scheidings teken met meerdere tekens gebruikt om drie teken reeksen samen te voegen:</span><span class="sxs-lookup"><span data-stu-id="5ca5b-124">The following statements use a multiple-character delimiter to join three strings:</span></span>

```powershell
$a = "WIND", "S P", "ERSHELL"
$a -join "OW"
WINDOWS POWERSHELL
```

<span data-ttu-id="5ca5b-125">Met de volgende instructie worden de regels in een hier-teken reeks toegevoegd aan één teken reeks.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-125">The following statement joins the lines in a here-string into a single string.</span></span> <span data-ttu-id="5ca5b-126">Omdat een hier-teken reeks één teken reeks is, moeten de lijnen in de teken reeks hier worden gesplitst voordat ze kunnen worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="5ca5b-126">Because a here-string is one string, the lines in the here-string must be split before they can be joined.</span></span> <span data-ttu-id="5ca5b-127">U kunt deze methode gebruiken om de teken reeksen opnieuw samen te voegen in een XML-bestand dat is opgeslagen in een hier-teken reeks:</span><span class="sxs-lookup"><span data-stu-id="5ca5b-127">You can use this method to rejoin the strings in an XML file that has been saved in a here-string:</span></span>

```powershell
$a = @'
a
b
c
'@

(-split $a) -join " "
a b c
```

## <a name="see-also"></a><span data-ttu-id="5ca5b-128">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="5ca5b-128">SEE ALSO</span></span>

[<span data-ttu-id="5ca5b-129">about_Operators</span><span class="sxs-lookup"><span data-stu-id="5ca5b-129">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="5ca5b-130">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="5ca5b-130">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="5ca5b-131">about_Split</span><span class="sxs-lookup"><span data-stu-id="5ca5b-131">about_Split</span></span>](about_Split.md)
