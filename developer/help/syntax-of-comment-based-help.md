---
title: Syntaxis van de Help op basis van een opmerking | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083209"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="c72af-102">Syntaxis van de Help op basis van opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c72af-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="c72af-103">Deze sectie beschrijft de syntaxis van de help op basis van een opmerking.</span><span class="sxs-lookup"><span data-stu-id="c72af-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="c72af-104">Syntaxisschema</span><span class="sxs-lookup"><span data-stu-id="c72af-104">Syntax Diagram</span></span>

 <span data-ttu-id="c72af-105">De syntaxis voor meer informatie over op basis van een opmerking is als volgt:</span><span class="sxs-lookup"><span data-stu-id="c72af-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="c72af-106">Van de syntaxisbeschrijving</span><span class="sxs-lookup"><span data-stu-id="c72af-106">Syntax Description</span></span>

 <span data-ttu-id="c72af-107">Help op basis van een opmerking wordt geschreven als een reeks met opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="c72af-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="c72af-108">Typt u een opmerkingensymbool (#) voor elke regel van opmerkingen of kunt u de '\<# ' en ' #> "symbolen te maken van een opmerkingenblok.</span><span class="sxs-lookup"><span data-stu-id="c72af-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="c72af-109">Alle regels binnen het Opmerkingenblok worden geïnterpreteerd als opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="c72af-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="c72af-110">Elke sectie van de Help op basis van een opmerking wordt gedefinieerd door een trefwoord en elk trefwoord wordt voorafgegaan door een punt (.).</span><span class="sxs-lookup"><span data-stu-id="c72af-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="c72af-111">De trefwoorden kunnen worden weergegeven in een willekeurige volgorde.</span><span class="sxs-lookup"><span data-stu-id="c72af-111">The keywords can appear in any order.</span></span> <span data-ttu-id="c72af-112">Het sleutelwoord namen zijn niet hoofdlettergevoelig.</span><span class="sxs-lookup"><span data-stu-id="c72af-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="c72af-113">Een opmerkingenblok moet ten minste één Help-informatie sleutelwoord bevatten.</span><span class="sxs-lookup"><span data-stu-id="c72af-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="c72af-114">Enkele van de trefwoorden, zoals bijvoorbeeld kunnen vaak worden weergegeven in het hetzelfde opmerkingenblok.</span><span class="sxs-lookup"><span data-stu-id="c72af-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="c72af-115">De Help-inhoud voor elk trefwoord begint op de regel na het sleutelwoord en kan meerdere regels omvatten.</span><span class="sxs-lookup"><span data-stu-id="c72af-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="c72af-116">Alle regels in een opmerking op basis van Help-onderwerp moeten aaneengesloten zijn.</span><span class="sxs-lookup"><span data-stu-id="c72af-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="c72af-117">Als een opmerking op basis van Help-onderwerp wordt gevolgd door een opmerking die geen deel uitmaakt van het Help-onderwerp, moet er ten minste één lege regel tussen de laatste opmerkingsregel van de niet-Help en het begin van de Help op basis van een opmerking.</span><span class="sxs-lookup"><span data-stu-id="c72af-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="c72af-118">Bijvoorbeeld, het volgende op basis van een opmerking help-onderwerp bevat de. Beschrijving trefwoord en de waarde, een beschrijving van een functie of script.</span><span class="sxs-lookup"><span data-stu-id="c72af-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```