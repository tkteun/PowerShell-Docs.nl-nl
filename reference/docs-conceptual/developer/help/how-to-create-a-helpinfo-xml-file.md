---
title: Een HelpInfo-XML-bestand maken
ms.date: 09/13/2016
ms.openlocfilehash: e395746e51309477bbcbff51b4591de3f73ce0db
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893302"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="406e7-102">Een HelpInfo-XML-bestand maken</span><span class="sxs-lookup"><span data-stu-id="406e7-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="406e7-103">In deze onderwerpen in deze sectie wordt uitgelegd hoe u een Help-informatie bestand maakt en vult, ook wel bekend als een ' HelpInfo XML-bestand ', voor de Help-functie die in Power shell kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="406e7-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="406e7-104">Overzicht van HelpInfo XML-bestand</span><span class="sxs-lookup"><span data-stu-id="406e7-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="406e7-105">Het HelpInfo XML-bestand is de primaire bron van informatie over de bij te werken Help voor de module.</span><span class="sxs-lookup"><span data-stu-id="406e7-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="406e7-106">Het bevat de locatie van de Help-bestanden voor de modules, de ondersteunde GEBRUIKERSINTERFACE culturen en de versie nummers die kunnen worden bijgewerkt om te bepalen of de gebruiker de nieuwste Help-bestanden heeft.</span><span class="sxs-lookup"><span data-stu-id="406e7-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="406e7-107">Elke module heeft slechts één HelpInfo XML-bestand, zelfs als de module meerdere Help-bestanden voor meerdere GEBRUIKERSINTERFACE culturen bevat.</span><span class="sxs-lookup"><span data-stu-id="406e7-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="406e7-108">De auteur van de module maakt het HelpInfo XML-bestand en plaatst het op de Internet locatie die is opgegeven door de sleutel **HelpInfoUri** in het module manifest.</span><span class="sxs-lookup"><span data-stu-id="406e7-108">The module author creates the HelpInfo XML file and places it in the internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="406e7-109">Wanneer de Help-bestanden van de module zijn bijgewerkt en geüpload, wordt het HelpInfo XML-bestand door de module Auteur bijgewerkt en wordt het oorspronkelijke HelpInfo XML-bestand vervangen door de nieuwe versie.</span><span class="sxs-lookup"><span data-stu-id="406e7-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="406e7-110">Het is essentieel dat het XML-bestand HelpInfo zorgvuldig wordt bewaard.</span><span class="sxs-lookup"><span data-stu-id="406e7-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="406e7-111">Als u nieuwe bestanden uploadt, maar vergeet de versie nummers niet te verhogen, worden de nieuwe bestanden niet gedownload naar de computers van gebruikers.</span><span class="sxs-lookup"><span data-stu-id="406e7-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="406e7-112">Als u Help-bestanden toevoegt voor een nieuwe UI-cultuur, maar u het XML-bestand HelpInfo niet bijwerkt of op de juiste locatie plaatst, worden de nieuwe bestanden niet gedownload met de Help die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="406e7-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="406e7-113">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="406e7-113">In this section</span></span>

<span data-ttu-id="406e7-114">Deze sectie bevat de volgende onderwerpen:</span><span class="sxs-lookup"><span data-stu-id="406e7-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="406e7-115">HelpInfo-XML-schema</span><span class="sxs-lookup"><span data-stu-id="406e7-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="406e7-116">HelpInfo-XML-voorbeeldbestand</span><span class="sxs-lookup"><span data-stu-id="406e7-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="406e7-117">Een naam geven aan een HelpInfo-XML-bestand</span><span class="sxs-lookup"><span data-stu-id="406e7-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="406e7-118">HelpInfo-XML-versienummers instellen</span><span class="sxs-lookup"><span data-stu-id="406e7-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="406e7-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="406e7-119">See Also</span></span>

[<span data-ttu-id="406e7-120">Ondersteunende help die kan worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="406e7-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)
