---
ms.date: 09/13/2016
ms.topic: reference
title: Een HelpInfo-XML-bestand maken
description: Een HelpInfo-XML-bestand maken
ms.openlocfilehash: d5a24306aa6488fdefad0b7b1ea9e2978a93a7b5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647720"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="76331-103">Een HelpInfo-XML-bestand maken</span><span class="sxs-lookup"><span data-stu-id="76331-103">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="76331-104">In deze onderwerpen in deze sectie wordt uitgelegd hoe u een Help-informatie bestand maakt en vult, ook wel bekend als een ' HelpInfo XML-bestand ', voor de Help-functie die in Power shell kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="76331-104">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="76331-105">Overzicht van HelpInfo XML-bestand</span><span class="sxs-lookup"><span data-stu-id="76331-105">HelpInfo XML File Overview</span></span>

<span data-ttu-id="76331-106">Het HelpInfo XML-bestand is de primaire bron van informatie over de bij te werken Help voor de module.</span><span class="sxs-lookup"><span data-stu-id="76331-106">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="76331-107">Het bevat de locatie van de Help-bestanden voor de modules, de ondersteunde GEBRUIKERSINTERFACE culturen en de versie nummers die kunnen worden bijgewerkt om te bepalen of de gebruiker de nieuwste Help-bestanden heeft.</span><span class="sxs-lookup"><span data-stu-id="76331-107">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="76331-108">Elke module heeft slechts één HelpInfo XML-bestand, zelfs als de module meerdere Help-bestanden voor meerdere GEBRUIKERSINTERFACE culturen bevat.</span><span class="sxs-lookup"><span data-stu-id="76331-108">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="76331-109">De auteur van de module maakt het HelpInfo XML-bestand en plaatst het op de Internet locatie die is opgegeven door de sleutel **HelpInfoUri** in het module manifest.</span><span class="sxs-lookup"><span data-stu-id="76331-109">The module author creates the HelpInfo XML file and places it in the internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="76331-110">Wanneer de Help-bestanden van de module zijn bijgewerkt en geüpload, wordt het HelpInfo XML-bestand door de module Auteur bijgewerkt en wordt het oorspronkelijke HelpInfo XML-bestand vervangen door de nieuwe versie.</span><span class="sxs-lookup"><span data-stu-id="76331-110">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="76331-111">Het is essentieel dat het XML-bestand HelpInfo zorgvuldig wordt bewaard.</span><span class="sxs-lookup"><span data-stu-id="76331-111">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="76331-112">Als u nieuwe bestanden uploadt, maar vergeet de versie nummers niet te verhogen, worden de nieuwe bestanden niet gedownload naar de computers van gebruikers.</span><span class="sxs-lookup"><span data-stu-id="76331-112">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="76331-113">Als u Help-bestanden toevoegt voor een nieuwe UI-cultuur, maar u het XML-bestand HelpInfo niet bijwerkt of op de juiste locatie plaatst, worden de nieuwe bestanden niet gedownload met de Help die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="76331-113">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="76331-114">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="76331-114">In this section</span></span>

<span data-ttu-id="76331-115">Deze sectie bevat de volgende onderwerpen:</span><span class="sxs-lookup"><span data-stu-id="76331-115">This section includes the following topics.</span></span>

- [<span data-ttu-id="76331-116">HelpInfo-XML-schema</span><span class="sxs-lookup"><span data-stu-id="76331-116">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="76331-117">HelpInfo-XML-voorbeeldbestand</span><span class="sxs-lookup"><span data-stu-id="76331-117">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="76331-118">Een naam geven aan een HelpInfo-XML-bestand</span><span class="sxs-lookup"><span data-stu-id="76331-118">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="76331-119">HelpInfo-XML-versienummers instellen</span><span class="sxs-lookup"><span data-stu-id="76331-119">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="76331-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="76331-120">See Also</span></span>

[<span data-ttu-id="76331-121">Ondersteunende help die kan worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="76331-121">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)
