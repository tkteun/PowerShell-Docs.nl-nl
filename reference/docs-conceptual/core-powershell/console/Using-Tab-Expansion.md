---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Met behulp van de uitbreiding van het tabblad
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 8412bd97a95719f07b16c6671d3b8801bbfab8e3
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2017
---
# <a name="using-tab-expansion"></a><span data-ttu-id="b4e49-103">Met behulp van de uitbreiding van het tabblad</span><span class="sxs-lookup"><span data-stu-id="b4e49-103">Using Tab Expansion</span></span>
<span data-ttu-id="b4e49-104">Opdrachtregelprogramma houders bevatten vaak een manier om de namen van opdrachten of grote bestanden automatisch te voltooien versnellen van de opdracht vermelding en bieden.</span><span class="sxs-lookup"><span data-stu-id="b4e49-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing .</span></span> <span data-ttu-id="b4e49-105">Windows PowerShell kunt u in te vullen bestandsnamen en de namen van cmdlets door op de **tabblad** sleutel.</span><span class="sxs-lookup"><span data-stu-id="b4e49-105">Windows PowerShell allows you to fill in file names and cmdlet names by pressing the **Tab** key.</span></span>

> [!NOTE]
> <span data-ttu-id="b4e49-106">Tabblad uitbreiding wordt bepaald door de interne functie TabExpansion of TabExpansion2.</span><span class="sxs-lookup"><span data-stu-id="b4e49-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="b4e49-107">Omdat deze functie kan worden gewijzigd of overschreven, is deze discussie een handleiding voor het gedrag van de standaardconfiguratie van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b4e49-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default PowerShell configuration.</span></span>

<span data-ttu-id="b4e49-108">Automatisch doorvoeren in een bestandsnaam of het pad van de beschikbare opties, typt u deel van de naam en druk op de **tabblad** sleutel.</span><span class="sxs-lookup"><span data-stu-id="b4e49-108">To fill in a filename or path from the available choices automatically, type part of the name and press the **Tab** key.</span></span> <span data-ttu-id="b4e49-109">PowerShell wordt de naam automatisch uitgebreid naar de eerste overeenkomst gevonden.</span><span class="sxs-lookup"><span data-stu-id="b4e49-109">PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="b4e49-110">Druk op de **tabblad** sleutel herhaaldelijk wordt doorlopen alle van de beschikbare opties.</span><span class="sxs-lookup"><span data-stu-id="b4e49-110">Pressing the **Tab** key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="b4e49-111">De uitbreiding van het tabblad van de namen van de cmdlet verschilt enigszins.</span><span class="sxs-lookup"><span data-stu-id="b4e49-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="b4e49-112">Wilt gebruiken tabblad uitbreiding van de naam van een cmdlet, typt u het volledige eerste deel van de naam (de term) en het afbreekstreepje die erop volgt.</span><span class="sxs-lookup"><span data-stu-id="b4e49-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="b4e49-113">U kunt ook opgeven in meer van de naam van een gedeeltelijke overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="b4e49-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="b4e49-114">Als u bijvoorbeeld **get-co** en druk vervolgens op de **tabblad** sleutel, PowerShell wordt automatisch uitgebreid met deze de **Get-Command** cmdlet (Let op dat deze wordt ook het geval is gewijzigd van letters aan het standaardformulier).</span><span class="sxs-lookup"><span data-stu-id="b4e49-114">For example, if you type **get-co** and then press the **Tab** key, PowerShell will automatically expand this to the **Get-Command** cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="b4e49-115">Als u op **tabblad** sleutel opnieuw, PowerShell wordt vervangen door dit met alleen andere overeenkomende cmdlet naam, **Get-inhoud**.</span><span class="sxs-lookup"><span data-stu-id="b4e49-115">If you press **Tab** key again, PowerShell replaces this with the only other matching cmdlet name, **Get-Content**.</span></span>

<span data-ttu-id="b4e49-116">U kunt herhaaldelijk tabblad uitbreiding gebruiken op dezelfde lijn.</span><span class="sxs-lookup"><span data-stu-id="b4e49-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="b4e49-117">Bijvoorbeeld, kunt u de uitbreiding van het tabblad op de naam van de **Get-inhoud** cmdlet door te voeren:</span><span class="sxs-lookup"><span data-stu-id="b4e49-117">For example, you can use tab expansion on the name of the **Get-Content** cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="b4e49-118">Wanneer u op drukt de **tabblad** sleutel, de opdracht wordt vergroot tot:</span><span class="sxs-lookup"><span data-stu-id="b4e49-118">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="b4e49-119">U kunt gedeeltelijk Geef het pad naar het logboekbestand Active Setup en tabblad uitbreiding opnieuw gebruiken:</span><span class="sxs-lookup"><span data-stu-id="b4e49-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="b4e49-120">Wanneer u op drukt de **tabblad** sleutel, de opdracht wordt vergroot tot:</span><span class="sxs-lookup"><span data-stu-id="b4e49-120">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="b4e49-121">Een beperking van het tabblad uitbreidingsproces is dat tabbladen altijd worden geïnterpreteerd als pogingen tot het voltooien van een woord.</span><span class="sxs-lookup"><span data-stu-id="b4e49-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="b4e49-122">Als u kopieert en plakt u opdrachtvoorbeelden in een PowerShell-console, controleert u of het voorbeeld bevat geen tabbladen. Zo ja, wordt de resultaten onvoorspelbaar en bijna zeker niet juist.</span><span class="sxs-lookup"><span data-stu-id="b4e49-122">If you copy and paste command examples into a PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>

