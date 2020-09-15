---
title: Syntaxis van de Help op basis van opmerkingen
ms.date: 09/12/2016
ms.openlocfilehash: 950afecc39f9d27207f77547679faab700481458
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893217"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="2ad2c-102">Syntaxis van de Help op basis van opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2ad2c-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="2ad2c-103">In deze sectie wordt de syntaxis van op opmerkingen gebaseerde Help beschreven.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="2ad2c-104">Syntaxis diagram</span><span class="sxs-lookup"><span data-stu-id="2ad2c-104">Syntax Diagram</span></span>

 <span data-ttu-id="2ad2c-105">De syntaxis voor op opmerkingen gebaseerde Help is als volgt:</span><span class="sxs-lookup"><span data-stu-id="2ad2c-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="2ad2c-106">Syntaxis beschrijving</span><span class="sxs-lookup"><span data-stu-id="2ad2c-106">Syntax Description</span></span>

 <span data-ttu-id="2ad2c-107">Help op basis van opmerkingen wordt geschreven als een reeks opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="2ad2c-108">U kunt een opmerkings symbool ( `#` ) voor elke regel met opmerkingen typen, maar u kunt ook `<#` de `#>` symbolen en gebruiken om een opmerkingen blok te maken.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-108">You can type a comment symbol (`#`) before each line of comments, or you can use the `<#` and `#>` symbols to create a comment block.</span></span> <span data-ttu-id="2ad2c-109">Alle regels in het opmerkingen blok worden geïnterpreteerd als opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="2ad2c-110">Elke sectie van Help op basis van opmerkingen is gedefinieerd met een tref woord en elk tref woord wordt voorafgegaan door een punt ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="2ad2c-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (`.`).</span></span> <span data-ttu-id="2ad2c-111">De tref woorden kunnen in elke wille keurige volg orde worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-111">The keywords can appear in any order.</span></span> <span data-ttu-id="2ad2c-112">De namen van tref woorden zijn niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="2ad2c-113">Een opmerkingen blok moet ten minste één Help-tref woord bevatten.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="2ad2c-114">Sommige tref woorden, zoals **voor beeld**, kunnen vaak in hetzelfde commentaar blok worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-114">Some of the keywords, such as **EXAMPLE**, can appear many times in the same comment block.</span></span> <span data-ttu-id="2ad2c-115">De Help-inhoud voor elk tref woord begint op de regel na het sleutel woord en kan meerdere regels omvatten.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="2ad2c-116">Alle regels in een Help-onderwerp op basis van opmerkingen moeten aaneengesloten zijn.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="2ad2c-117">Als een Help-onderwerp op basis van opmerkingen een opmerking volgt die geen deel uitmaakt van het Help-onderwerp, moet er ten minste één lege regel tussen de laatste niet-Help opmerkings regel en het begin van de op opmerkingen gebaseerde Help zijn.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="2ad2c-118">Het volgende Help-onderwerp op basis van opmerkingen bevat bijvoorbeeld de. Het tref woord Description en de bijbehorende waarde, een beschrijving van een functie of script.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```
