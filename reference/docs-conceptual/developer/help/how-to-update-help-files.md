---
ms.date: 09/12/2016
ms.topic: reference
title: Help-bestanden bijwerken
description: Help-bestanden bijwerken
ms.openlocfilehash: 19bf501cf91b1eb5dabb334c2179953590b40232
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649587"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="b99d5-103">Help-bestanden bijwerken</span><span class="sxs-lookup"><span data-stu-id="b99d5-103">How to Update Help Files</span></span>

<span data-ttu-id="b99d5-104">In dit onderwerp wordt uitgelegd hoe u Help-bestanden bijwerkt voor een module die kan worden bijgewerkt met ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="b99d5-104">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="b99d5-105">Help-bestanden bijwerken</span><span class="sxs-lookup"><span data-stu-id="b99d5-105">Updating Help Files</span></span>

<span data-ttu-id="b99d5-106">Er zijn veel redenen om Help-bestanden bij te werken, zoals het corrigeren van fouten, het verduidelijken van een concept, het beantwoorden van een veelgestelde vraag, het toevoegen van nieuwe bestanden of het toevoegen van nieuwe en betere voor beelden.</span><span class="sxs-lookup"><span data-stu-id="b99d5-106">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="b99d5-107">Een Help-bestand bijwerken:</span><span class="sxs-lookup"><span data-stu-id="b99d5-107">To update a help file:</span></span>

1. <span data-ttu-id="b99d5-108">Wijzig de bestanden.</span><span class="sxs-lookup"><span data-stu-id="b99d5-108">Change the files.</span></span>
1. <span data-ttu-id="b99d5-109">De bestanden vertalen in andere GEBRUIKERSINTERFACE culturen.</span><span class="sxs-lookup"><span data-stu-id="b99d5-109">Translate the files into other UI cultures.</span></span>
1. <span data-ttu-id="b99d5-110">Verzamel alle Help-bestanden (nieuw, gewijzigd en ongewijzigd) voor de module in elke GEBRUIKERSINTERFACE cultuur.</span><span class="sxs-lookup"><span data-stu-id="b99d5-110">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>
1. <span data-ttu-id="b99d5-111">Valideer de bestanden op basis van het XML-schema.</span><span class="sxs-lookup"><span data-stu-id="b99d5-111">Validate the files against the XML schema.</span></span>
1. <span data-ttu-id="b99d5-112">Bouw de CAB-bestanden opnieuw op voor elke GEBRUIKERSINTERFACE cultuur.</span><span class="sxs-lookup"><span data-stu-id="b99d5-112">Rebuild the CAB files for each UI culture.</span></span>
1. <span data-ttu-id="b99d5-113">In het XML-bestand HelpInfo verhoogt u de versie nummers van het CAB-bestand voor elke GEBRUIKERSINTERFACE cultuur.</span><span class="sxs-lookup"><span data-stu-id="b99d5-113">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>
1. <span data-ttu-id="b99d5-114">Upload de nieuwe CAB-bestanden naar de locatie die is opgegeven door de waarde van het element **HelpContentUri** in het XML-bestand HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="b99d5-114">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="b99d5-115">Vervang de oudere CAB-bestanden door de nieuwe CAB-bestanden.</span><span class="sxs-lookup"><span data-stu-id="b99d5-115">Replace the older CAB files with the new CAB files.</span></span>
1. <span data-ttu-id="b99d5-116">Upload het bijgewerkte XML-bestand HelpInfo naar de locatie die is opgegeven door de sleutel **HelpInfoUri** in het module manifest.</span><span class="sxs-lookup"><span data-stu-id="b99d5-116">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="b99d5-117">Vervang het oudere HelpInfo XML-bestand door het nieuwe bestand.</span><span class="sxs-lookup"><span data-stu-id="b99d5-117">Replace the older HelpInfo XML file with the new file.</span></span>
