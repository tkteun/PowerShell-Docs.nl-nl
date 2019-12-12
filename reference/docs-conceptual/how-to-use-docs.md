---
ms.date: 10/20/2019
keywords: Power shell, cmdlet
title: De Power shell-documentatie gebruiken
ms.openlocfilehash: 80f72bb89b3bb82ee7c4d16b8969395f02d7d4ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72676162"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="10830-103">De Power shell-documentatie gebruiken</span><span class="sxs-lookup"><span data-stu-id="10830-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="10830-104">Welkom bij de online documentatie voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="10830-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="10830-105">Deze site bevat een cmdlet-verwijzing voor de volgende versies van Power shell:</span><span class="sxs-lookup"><span data-stu-id="10830-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="10830-106">Power shell 7 (preview-versie)</span><span class="sxs-lookup"><span data-stu-id="10830-106">PowerShell 7 (preview)</span></span>
- <span data-ttu-id="10830-107">Power shell 6</span><span class="sxs-lookup"><span data-stu-id="10830-107">PowerShell 6</span></span>
- <span data-ttu-id="10830-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="10830-108">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="10830-109">Artikelen zoeken en een versie selecteren</span><span class="sxs-lookup"><span data-stu-id="10830-109">Finding articles and selecting a version</span></span>

<span data-ttu-id="10830-110">Er zijn twee manieren om te zoeken naar inhoud in docs. De eenvoudigste manier is het vak Filteren onder versie kiezer te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="10830-110">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="10830-111">U hoeft alleen maar een woord in te voeren dat wordt weer gegeven in de titel van een artikel.</span><span class="sxs-lookup"><span data-stu-id="10830-111">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="10830-112">Op de pagina wordt een lijst met overeenkomende artikelen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="10830-112">The page displays a list of matching articles.</span></span> <span data-ttu-id="10830-113">U kunt ook de optie selecteren om te zoeken in de hele site vanuit deze lijst.</span><span class="sxs-lookup"><span data-stu-id="10830-113">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="10830-114">Deze site geeft standaard documentatie weer voor de meest recente versie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="10830-114">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="10830-115">Sommige cmdlets werken anders in verschillende versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="10830-115">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="10830-116">Zorg ervoor dat u de documentatie bekijkt voor de versie van Power shell die u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="10830-116">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="10830-117">Gebruik de versie kiezer boven aan de pagina om de gewenste versie van Power shell te selecteren.</span><span class="sxs-lookup"><span data-stu-id="10830-117">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![versie kiezer](images/how-to-use-docs/version-search.gif)

<span data-ttu-id="10830-119">U kunt controleren welke versie van Power shell u gebruikt door de `$PSversionTable.PSVersion` waarde te controleren.</span><span class="sxs-lookup"><span data-stu-id="10830-119">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="10830-120">In het volgende voor beeld ziet u de uitvoer voor Windows Power shell v 5.1.</span><span class="sxs-lookup"><span data-stu-id="10830-120">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```
