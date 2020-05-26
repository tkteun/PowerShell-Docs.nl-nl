---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Met behulp van de tabbladuitbreiding
ms.openlocfilehash: d96cbf848f464aff29a7bed9b70d0b6a000aa808
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810692"
---
# <a name="using-tab-expansion"></a><span data-ttu-id="979ee-103">Met behulp van de tabbladuitbreiding</span><span class="sxs-lookup"><span data-stu-id="979ee-103">Using Tab Expansion</span></span>

<span data-ttu-id="979ee-104">Opdracht regel shells bieden vaak een manier om de namen van lange bestanden of opdrachten automatisch te volt ooien, opdracht invoer te versnellen en hints te bieden.</span><span class="sxs-lookup"><span data-stu-id="979ee-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing hints.</span></span> <span data-ttu-id="979ee-105">Met Power shell kunt u bestands namen en namen van cmdlets invullen door op de <kbd>Tab</kbd> -toets te drukken.</span><span class="sxs-lookup"><span data-stu-id="979ee-105">PowerShell allows you to fill in file names and cmdlet names by pressing the <kbd>Tab</kbd> key.</span></span>

> [!NOTE]
> <span data-ttu-id="979ee-106">Tabblad uitbreiding wordt bepaald door de interne functie TabExpansion of TabExpansion2.</span><span class="sxs-lookup"><span data-stu-id="979ee-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="979ee-107">Omdat deze functie kan worden gewijzigd of overschreven, is deze discussie een hand leiding voor het gedrag van de standaard-Power shell-configuratie.</span><span class="sxs-lookup"><span data-stu-id="979ee-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default PowerShell configuration.</span></span>

<span data-ttu-id="979ee-108">Als u automatisch een bestands naam of pad van de beschik bare opties wilt invullen, typt u een deel van de naam en drukt u op de <kbd>Tab</kbd> -toets.</span><span class="sxs-lookup"><span data-stu-id="979ee-108">To fill in a filename or path from the available choices automatically, type part of the name and press the <kbd>Tab</kbd> key.</span></span> <span data-ttu-id="979ee-109">Power shell breidt de naam automatisch uit naar het eerste overeenkomende item dat wordt gevonden.</span><span class="sxs-lookup"><span data-stu-id="979ee-109">PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="979ee-110">Door herhaaldelijk op de <kbd>Tab</kbd> -toets te drukken, worden alle beschik bare opties door lopen.</span><span class="sxs-lookup"><span data-stu-id="979ee-110">Pressing the <kbd>Tab</kbd> key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="979ee-111">De tabblad-uitbrei ding van de namen van cmdlets is iets anders.</span><span class="sxs-lookup"><span data-stu-id="979ee-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="979ee-112">Als u tabblad uitbrei ding wilt gebruiken voor de naam van een cmdlet, typt u het volledige eerste deel van de naam (de opdracht) en het afbreek streepje dat deze volgt.</span><span class="sxs-lookup"><span data-stu-id="979ee-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="979ee-113">U kunt de naam van een gedeeltelijke overeenkomst invullen.</span><span class="sxs-lookup"><span data-stu-id="979ee-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="979ee-114">Als u bijvoorbeeld typt `get-co` en vervolgens op de <kbd>Tab</kbd> -toets drukt, wordt dit door Power shell automatisch uitgebreid naar de `Get-Command` cmdlet (u ziet dat het hoofdletter gebruik ook wordt gewijzigd in het standaard formulier).</span><span class="sxs-lookup"><span data-stu-id="979ee-114">For example, if you type `get-co` and then press the <kbd>Tab</kbd> key, PowerShell will automatically expand this to the `Get-Command` cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="979ee-115">Als u opnieuw op <kbd>Tab</kbd> drukt, wordt dit door Power shell vervangen door de enige andere overeenkomende naam van de cmdlet `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="979ee-115">If you press <kbd>Tab</kbd> key again, PowerShell replaces this with the only other matching cmdlet name, `Get-Content`.</span></span>

<span data-ttu-id="979ee-116">U kunt de tab-uitbrei ding herhaaldelijk op dezelfde regel gebruiken.</span><span class="sxs-lookup"><span data-stu-id="979ee-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="979ee-117">U kunt bijvoorbeeld tabblad uitbrei ding op de naam van de `Get-Content` cmdlet gebruiken door het volgende in te voeren:</span><span class="sxs-lookup"><span data-stu-id="979ee-117">For example, you can use tab expansion on the name of the `Get-Content` cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="979ee-118">Wanneer u op de <kbd>Tab</kbd> -toets drukt, wordt de opdracht uitgebreid naar:</span><span class="sxs-lookup"><span data-stu-id="979ee-118">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="979ee-119">Vervolgens kunt u het pad naar het actieve Setup-logboek bestand opgeven en de tab-uitbrei ding opnieuw gebruiken:</span><span class="sxs-lookup"><span data-stu-id="979ee-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="979ee-120">Wanneer u op de <kbd>Tab</kbd> -toets drukt, wordt de opdracht uitgebreid naar:</span><span class="sxs-lookup"><span data-stu-id="979ee-120">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="979ee-121">Een beperking van het tabblad expansie proces is dat tabbladen altijd worden geïnterpreteerd als pogingen om een woord te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="979ee-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="979ee-122">Als u voor beelden van de opdracht kopieert en plakt naar een Power shell-console, moet u ervoor zorgen dat het voor beeld geen tabbladen bevat. Als dat het geval is, kunnen de resultaten onvoorspelbaar zijn en is bijna zeker niet wat u hebt beoogd.</span><span class="sxs-lookup"><span data-stu-id="979ee-122">If you copy and paste command examples into a PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>
