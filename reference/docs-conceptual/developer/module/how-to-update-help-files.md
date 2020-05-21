---
title: Help-bestanden bijwerken | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 35b3fd696419d0135fd6f662223e6c8586df443a
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561387"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="8a114-102">Help-bestanden bijwerken</span><span class="sxs-lookup"><span data-stu-id="8a114-102">How to Update Help Files</span></span>

<span data-ttu-id="8a114-103">In dit onderwerp wordt uitgelegd hoe u Help-bestanden bijwerkt voor een module die kan worden bijgewerkt met ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="8a114-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="8a114-104">Help-bestanden bijwerken</span><span class="sxs-lookup"><span data-stu-id="8a114-104">Updating Help Files</span></span>

<span data-ttu-id="8a114-105">Er zijn veel redenen om Help-bestanden bij te werken, zoals het corrigeren van fouten, het verduidelijken van een concept, het beantwoorden van een veelgestelde vraag, het toevoegen van nieuwe bestanden of het toevoegen van nieuwe en betere voor beelden.</span><span class="sxs-lookup"><span data-stu-id="8a114-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="8a114-106">Een Help-bestand bijwerken:</span><span class="sxs-lookup"><span data-stu-id="8a114-106">To update a help file:</span></span>

1. <span data-ttu-id="8a114-107">Wijzig de bestanden.</span><span class="sxs-lookup"><span data-stu-id="8a114-107">Change the files.</span></span>

2. <span data-ttu-id="8a114-108">De bestanden vertalen in andere GEBRUIKERSINTERFACE culturen.</span><span class="sxs-lookup"><span data-stu-id="8a114-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="8a114-109">Verzamel alle Help-bestanden (nieuw, gewijzigd en ongewijzigd) voor de module in elke GEBRUIKERSINTERFACE cultuur.</span><span class="sxs-lookup"><span data-stu-id="8a114-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="8a114-110">Valideer de bestanden op basis van het XML-schema.</span><span class="sxs-lookup"><span data-stu-id="8a114-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="8a114-111">Bouw de CAB-bestanden opnieuw op voor elke GEBRUIKERSINTERFACE cultuur.</span><span class="sxs-lookup"><span data-stu-id="8a114-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="8a114-112">In het XML-bestand HelpInfo verhoogt u de versie nummers van het CAB-bestand voor elke GEBRUIKERSINTERFACE cultuur.</span><span class="sxs-lookup"><span data-stu-id="8a114-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="8a114-113">Upload de nieuwe CAB-bestanden naar de locatie die is opgegeven door de waarde van het element **HelpContentUri** in het XML-bestand HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="8a114-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="8a114-114">Vervang de oudere CAB-bestanden door de nieuwe CAB-bestanden.</span><span class="sxs-lookup"><span data-stu-id="8a114-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="8a114-115">Upload het bijgewerkte XML-bestand HelpInfo naar de locatie die is opgegeven door de sleutel **HelpInfoUri** in het module manifest.</span><span class="sxs-lookup"><span data-stu-id="8a114-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="8a114-116">Vervang het oudere HelpInfo XML-bestand door het nieuwe bestand.</span><span class="sxs-lookup"><span data-stu-id="8a114-116">Replace the older HelpInfo XML file with the new file.</span></span>
