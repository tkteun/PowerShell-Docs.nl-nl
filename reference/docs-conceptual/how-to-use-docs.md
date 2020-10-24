---
ms.date: 07/29/2020
keywords: powershell,cmdlet
title: De Power shell-documentatie gebruiken
description: In deze artikelen wordt uitgelegd hoe u de functies van deze site gebruikt, inclusief het filteren van zoeken en de versie selectie.
ms.openlocfilehash: 32f0c613e10329cc4830386b744e766eeeab0187
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501113"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="2569e-104">De Power shell-documentatie gebruiken</span><span class="sxs-lookup"><span data-stu-id="2569e-104">How to use the PowerShell documentation</span></span>

<span data-ttu-id="2569e-105">Welkom bij de online documentatie voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="2569e-105">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="2569e-106">Deze site bevat een cmdlet-verwijzing voor de volgende versies van Power shell:</span><span class="sxs-lookup"><span data-stu-id="2569e-106">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="2569e-107">PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="2569e-107">PowerShell 7</span></span>
- <span data-ttu-id="2569e-108">Power shell 6</span><span class="sxs-lookup"><span data-stu-id="2569e-108">PowerShell 6</span></span>
- <span data-ttu-id="2569e-109">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="2569e-109">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="2569e-110">Artikelen zoeken en een versie selecteren</span><span class="sxs-lookup"><span data-stu-id="2569e-110">Finding articles and selecting a version</span></span>

<span data-ttu-id="2569e-111">Er zijn twee manieren om te zoeken naar inhoud in docs. De eenvoudigste manier is het vak Filteren onder versie kiezer te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2569e-111">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="2569e-112">U hoeft alleen maar een woord in te voeren dat wordt weer gegeven in de titel van een artikel.</span><span class="sxs-lookup"><span data-stu-id="2569e-112">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="2569e-113">Op de pagina wordt een lijst met overeenkomende artikelen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2569e-113">The page displays a list of matching articles.</span></span> <span data-ttu-id="2569e-114">U kunt ook de optie selecteren om te zoeken in de hele site vanuit deze lijst.</span><span class="sxs-lookup"><span data-stu-id="2569e-114">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="2569e-115">Deze site geeft standaard documentatie weer voor de meest recente versie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="2569e-115">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="2569e-116">Sommige cmdlets werken anders in verschillende versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="2569e-116">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="2569e-117">Zorg ervoor dat u de documentatie bekijkt voor de versie van Power shell die u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2569e-117">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="2569e-118">Gebruik de versie kiezer boven aan de pagina om de gewenste versie van Power shell te selecteren.</span><span class="sxs-lookup"><span data-stu-id="2569e-118">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![De versie kiezer gebruiken](media/how-to-use-docs/version-search.gif)

<span data-ttu-id="2569e-120">U kunt controleren welke versie van Power shell u gebruikt door de waarde te controleren `$PSversionTable.PSVersion` .</span><span class="sxs-lookup"><span data-stu-id="2569e-120">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="2569e-121">In het volgende voor beeld ziet u de uitvoer voor Windows Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="2569e-121">The following example shows the output for Windows PowerShell 5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      19041  1
```

<span data-ttu-id="2569e-122">Zie [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax)als u geen ervaring hebt met Power shell en meer informatie wilt over de syntaxis van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="2569e-122">If you are new to PowerShell and need help understanding the command syntax, see [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax).</span></span>

## <a name="finding-articles-for-previous-versions"></a><span data-ttu-id="2569e-123">Artikelen zoeken voor eerdere versies</span><span class="sxs-lookup"><span data-stu-id="2569e-123">Finding articles for previous versions</span></span>

<span data-ttu-id="2569e-124">Documentatie voor oudere versies van Power shell is gearchiveerd in onze [vorige versies](https://aka.ms/PSLegacyDocs) site.</span><span class="sxs-lookup"><span data-stu-id="2569e-124">Documentation for older versions of PowerShell has been archived in our [Previous Versions](https://aka.ms/PSLegacyDocs) site.</span></span>

<span data-ttu-id="2569e-125">Deze site bevat documentatie voor de volgende onderwerpen:</span><span class="sxs-lookup"><span data-stu-id="2569e-125">This site contains documentation for the following topics:</span></span>

- <span data-ttu-id="2569e-126">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="2569e-126">PowerShell 3.0</span></span>
- <span data-ttu-id="2569e-127">PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="2569e-127">PowerShell 4.0</span></span>
- <span data-ttu-id="2569e-128">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2569e-128">PowerShell 5.0</span></span>
- <span data-ttu-id="2569e-129">Power shell-werk stromen</span><span class="sxs-lookup"><span data-stu-id="2569e-129">PowerShell Workflows</span></span>
- <span data-ttu-id="2569e-130">Power shell-webtoegang</span><span class="sxs-lookup"><span data-stu-id="2569e-130">PowerShell Web Access</span></span>
