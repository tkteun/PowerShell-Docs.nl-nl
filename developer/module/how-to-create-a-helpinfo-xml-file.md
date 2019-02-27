---
title: Over het maken van een HelpInfo XML-bestand | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844896"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="998a4-102">Een HelpInfo-XML-bestand maken</span><span class="sxs-lookup"><span data-stu-id="998a4-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="998a4-103">Deze onderwerpen in deze sectie wordt uitgelegd hoe u maken en vullen van een helpbestand informatie, gewoonlijk bekend als 'HelpInfo XML-bestand,' voor de Windows PowerShell bij te werken Help-functie.</span><span class="sxs-lookup"><span data-stu-id="998a4-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the Windows PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="998a4-104">Overzicht van HelpInfo XML-bestand</span><span class="sxs-lookup"><span data-stu-id="998a4-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="998a4-105">Het HelpInfo XML-bestand is de primaire bron van informatie over het bij te werken Help voor de module.</span><span class="sxs-lookup"><span data-stu-id="998a4-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="998a4-106">Dit omvat de locatie van de help-bestanden voor de modules, de ondersteunde culturen voor de gebruikersinterface en de versienummers die bij te werken Help gebruikt om te bepalen of de gebruiker de meest recente help-bestanden.</span><span class="sxs-lookup"><span data-stu-id="998a4-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="998a4-107">Elke module heeft slechts één HelpInfo XML-bestand, zelfs als de module meerdere help-bestanden voor meerdere UI culturen bevat.</span><span class="sxs-lookup"><span data-stu-id="998a4-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="998a4-108">De module-auteur het HelpInfo XML-bestand wordt gemaakt en plaatst het in de Internet-locatie die is opgegeven door de **HelpInfoUri** sleutel in de module-manifest.</span><span class="sxs-lookup"><span data-stu-id="998a4-108">The module author creates the HelpInfo XML file and places it in the Internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="998a4-109">Wanneer de module help-bestanden worden bijgewerkt en worden geüpload, wordt de module-auteur werkt het HelpInfo XML-bestand en vervangt het oorspronkelijke HelpInfo XML-bestand met de nieuwe versie.</span><span class="sxs-lookup"><span data-stu-id="998a4-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="998a4-110">Het is essentieel dat het HelpInfo XML-bestand zorgvuldig wordt gehandhaafd.</span><span class="sxs-lookup"><span data-stu-id="998a4-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="998a4-111">Als u nieuwe bestanden uploaden, maar vergeet de versienummers toenemen, bij te werken Help wordt niet de nieuwe bestanden downloaden naar computers van gebruikers.</span><span class="sxs-lookup"><span data-stu-id="998a4-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="998a4-112">Als u help-bestanden voor een nieuwe gebruikersinterfacecultuur toevoegen, maar geen HelpInfo XML-bestand of plaats deze in de juiste locatie, wordt er bij het bij te werken Help niet de nieuwe bestanden downloaden.</span><span class="sxs-lookup"><span data-stu-id="998a4-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="998a4-113">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="998a4-113">In this section</span></span>

<span data-ttu-id="998a4-114">Deze sectie bevat de volgende onderwerpen:</span><span class="sxs-lookup"><span data-stu-id="998a4-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="998a4-115">HelpInfo XML Schema</span><span class="sxs-lookup"><span data-stu-id="998a4-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="998a4-116">HelpInfo XML-voorbeeldbestand</span><span class="sxs-lookup"><span data-stu-id="998a4-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="998a4-117">Naamconventies voor een HelpInfo XML-bestand</span><span class="sxs-lookup"><span data-stu-id="998a4-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="998a4-118">Over het instellen van de versienummers HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="998a4-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="998a4-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="998a4-119">See Also</span></span>

[<span data-ttu-id="998a4-120">Ondersteunende Help die kan worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="998a4-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)