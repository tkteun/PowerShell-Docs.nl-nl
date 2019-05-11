---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met behulp van de tabbladuitbreiding
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 437c1e3c04352f2c5c3aba4c67b542821975f739
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229427"
---
# <a name="using-tab-expansion"></a><span data-ttu-id="251aa-103">Met behulp van de tabbladuitbreiding</span><span class="sxs-lookup"><span data-stu-id="251aa-103">Using Tab Expansion</span></span>

<span data-ttu-id="251aa-104">Een manier voor het automatisch voltooien van de namen van grote bestanden of opdrachten bieden opdrachtregel shells vaak opdracht vermelding versnellen en het geven van aanbevolen basisservers.</span><span class="sxs-lookup"><span data-stu-id="251aa-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing hints.</span></span> <span data-ttu-id="251aa-105">PowerShell kunt u in te vullen in bestandsnamen en namen van de cmdlets door te drukken de <kbd>tabblad</kbd> sleutel.</span><span class="sxs-lookup"><span data-stu-id="251aa-105">PowerShell allows you to fill in file names and cmdlet names by pressing the <kbd>Tab</kbd> key.</span></span>

> [!NOTE]
> <span data-ttu-id="251aa-106">Tabbladuitbreiding wordt bepaald door de interne functie TabExpansion of TabExpansion2.</span><span class="sxs-lookup"><span data-stu-id="251aa-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="251aa-107">Omdat deze functie kan worden gewijzigd of overschreven, is deze discussie een handleiding voor het gedrag van de standaardconfiguratie van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="251aa-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default PowerShell configuration.</span></span>

<span data-ttu-id="251aa-108">Automatisch doorvoeren in een bestandsnaam of het pad van de beschikbare opties, typt u deel uit van de naam en druk op de <kbd>tabblad</kbd> sleutel.</span><span class="sxs-lookup"><span data-stu-id="251aa-108">To fill in a filename or path from the available choices automatically, type part of the name and press the <kbd>Tab</kbd> key.</span></span> <span data-ttu-id="251aa-109">PowerShell wordt de naam van de automatisch uitgebreid naar de eerste overeenkomende reeks gevonden.</span><span class="sxs-lookup"><span data-stu-id="251aa-109">PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="251aa-110">Druk op de <kbd>tabblad</kbd> sleutel herhaaldelijk wordt bladeren door alle van de beschikbare opties.</span><span class="sxs-lookup"><span data-stu-id="251aa-110">Pressing the <kbd>Tab</kbd> key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="251aa-111">Het tabbladuitbreiding van de namen van de cmdlets is enigszins anders.</span><span class="sxs-lookup"><span data-stu-id="251aa-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="251aa-112">Voor het gebruik van tabbladuitbreiding op de cmdletnaam van een, typt u het hele eerste deel van de naam (de term) en het afbreekstreepje dat erop volgt.</span><span class="sxs-lookup"><span data-stu-id="251aa-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="251aa-113">U kunt invullen in meer van de naam van een gedeeltelijke overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="251aa-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="251aa-114">Als u bijvoorbeeld `get-co` en druk vervolgens op de <kbd>tabblad</kbd> sleutel, PowerShell wordt automatisch uitgebreid met deze de `Get-Command` cmdlet (Let op dat deze wordt ook de weergave van letters gewijzigd naar hun standaard vorm).</span><span class="sxs-lookup"><span data-stu-id="251aa-114">For example, if you type `get-co` and then press the <kbd>Tab</kbd> key, PowerShell will automatically expand this to the `Get-Command` cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="251aa-115">Als u druk op <kbd>tabblad</kbd> sleutel opnieuw, PowerShell vervangt deze door de alleen andere overeenkomende cmdlet-naam, `Get-Content`.</span><span class="sxs-lookup"><span data-stu-id="251aa-115">If you press <kbd>Tab</kbd> key again, PowerShell replaces this with the only other matching cmdlet name, `Get-Content`.</span></span>

<span data-ttu-id="251aa-116">U kunt herhaaldelijk tabbladuitbreiding gebruiken op dezelfde regel.</span><span class="sxs-lookup"><span data-stu-id="251aa-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="251aa-117">U kunt bijvoorbeeld tabbladuitbreiding gebruiken op de naam van de `Get-Content` cmdlet door in te voeren:</span><span class="sxs-lookup"><span data-stu-id="251aa-117">For example, you can use tab expansion on the name of the `Get-Content` cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="251aa-118">Wanneer u drukt u op de <kbd>tabblad</kbd> sleutel, de opdracht wordt er uitgebreid naar:</span><span class="sxs-lookup"><span data-stu-id="251aa-118">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="251aa-119">U kunt vervolgens gedeeltelijk Geef het pad op naar het logboekbestand Active Setup en tabbladuitbreiding opnieuw gebruiken:</span><span class="sxs-lookup"><span data-stu-id="251aa-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="251aa-120">Wanneer u drukt u op de <kbd>tabblad</kbd> sleutel, de opdracht wordt er uitgebreid naar:</span><span class="sxs-lookup"><span data-stu-id="251aa-120">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="251aa-121">Een beperking van het tabblad-uitbreidingsproces is dat tabbladen altijd worden geïnterpreteerd als pogingen om uit te voeren van een woord.</span><span class="sxs-lookup"><span data-stu-id="251aa-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="251aa-122">Als u kopieert en plakt opdrachtvoorbeelden in een PowerShell-console, controleert u of het voorbeeld bevat geen tabbladen. Als dit het geval is, worden de resultaten onvoorspelbaar en bijna zeker worden niet juist.</span><span class="sxs-lookup"><span data-stu-id="251aa-122">If you copy and paste command examples into a PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>