---
ms.date: 05/22/2020
keywords: powershell,cmdlet
title: De Power shell-documentatie gebruiken
ms.openlocfilehash: 259eb1eea1dc7e8b5ae5730f97c938b838a320bf
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808262"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="0fb70-103">De Power shell-documentatie gebruiken</span><span class="sxs-lookup"><span data-stu-id="0fb70-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="0fb70-104">Welkom bij de online documentatie voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="0fb70-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="0fb70-105">Deze site bevat een cmdlet-verwijzing voor de volgende versies van Power shell:</span><span class="sxs-lookup"><span data-stu-id="0fb70-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="0fb70-106">Power shell 7</span><span class="sxs-lookup"><span data-stu-id="0fb70-106">PowerShell 7</span></span>
- <span data-ttu-id="0fb70-107">Power shell 6</span><span class="sxs-lookup"><span data-stu-id="0fb70-107">PowerShell 6</span></span>
- <span data-ttu-id="0fb70-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="0fb70-108">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="0fb70-109">Artikelen zoeken en een versie selecteren</span><span class="sxs-lookup"><span data-stu-id="0fb70-109">Finding articles and selecting a version</span></span>

<span data-ttu-id="0fb70-110">Er zijn twee manieren om te zoeken naar inhoud in docs. De eenvoudigste manier is het vak Filteren onder versie kiezer te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="0fb70-110">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="0fb70-111">U hoeft alleen maar een woord in te voeren dat wordt weer gegeven in de titel van een artikel.</span><span class="sxs-lookup"><span data-stu-id="0fb70-111">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="0fb70-112">Op de pagina wordt een lijst met overeenkomende artikelen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0fb70-112">The page displays a list of matching articles.</span></span> <span data-ttu-id="0fb70-113">U kunt ook de optie selecteren om te zoeken in de hele site vanuit deze lijst.</span><span class="sxs-lookup"><span data-stu-id="0fb70-113">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="0fb70-114">Deze site geeft standaard documentatie weer voor de meest recente versie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="0fb70-114">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="0fb70-115">Sommige cmdlets werken anders in verschillende versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="0fb70-115">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="0fb70-116">Zorg ervoor dat u de documentatie bekijkt voor de versie van Power shell die u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0fb70-116">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="0fb70-117">Gebruik de versie kiezer boven aan de pagina om de gewenste versie van Power shell te selecteren.</span><span class="sxs-lookup"><span data-stu-id="0fb70-117">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![versiekiezer](media/how-to-use-docs/version-search.gif)

<span data-ttu-id="0fb70-119">U kunt controleren welke versie van Power shell u gebruikt door de waarde te controleren `$PSversionTable.PSVersion` .</span><span class="sxs-lookup"><span data-stu-id="0fb70-119">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="0fb70-120">In het volgende voor beeld ziet u de uitvoer voor Windows Power shell v 5.1.</span><span class="sxs-lookup"><span data-stu-id="0fb70-120">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

## <a name="finding-articles-for-previous-versions"></a><span data-ttu-id="0fb70-121">Artikelen zoeken voor eerdere versies</span><span class="sxs-lookup"><span data-stu-id="0fb70-121">Finding articles for previous versions</span></span>

<span data-ttu-id="0fb70-122">Documentatie voor oudere versies van Power shell is gearchiveerd in onze [vorige versies](https://aka.ms/PSLegacyDocs) site.</span><span class="sxs-lookup"><span data-stu-id="0fb70-122">Documentation for older versions of PowerShell has been archived in our [Previous Versions](https://aka.ms/PSLegacyDocs) site.</span></span>

<span data-ttu-id="0fb70-123">Deze site bevat documentatie voor de volgende onderwerpen:</span><span class="sxs-lookup"><span data-stu-id="0fb70-123">This site contains documentation for the following topics:</span></span>

- <span data-ttu-id="0fb70-124">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="0fb70-124">PowerShell 3.0</span></span>
- <span data-ttu-id="0fb70-125">PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="0fb70-125">PowerShell 4.0</span></span>
- <span data-ttu-id="0fb70-126">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0fb70-126">PowerShell 5.0</span></span>
- <span data-ttu-id="0fb70-127">Power shell-werk stromen</span><span class="sxs-lookup"><span data-stu-id="0fb70-127">PowerShell Workflows</span></span>
- <span data-ttu-id="0fb70-128">Power shell-webtoegang</span><span class="sxs-lookup"><span data-stu-id="0fb70-128">PowerShell Web Access</span></span>
