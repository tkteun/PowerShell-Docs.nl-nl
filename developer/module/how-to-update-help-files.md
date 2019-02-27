---
title: Het bijwerken van Help-bestanden | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846478"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="fab58-102">Help-bestanden bijwerken</span><span class="sxs-lookup"><span data-stu-id="fab58-102">How to Update Help Files</span></span>

<span data-ttu-id="fab58-103">In dit onderwerp wordt uitgelegd hoe u help-bestanden voor een module die ondersteuning biedt voor bij te werken Help bijwerken.</span><span class="sxs-lookup"><span data-stu-id="fab58-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="fab58-104">Help-bestanden bijwerken</span><span class="sxs-lookup"><span data-stu-id="fab58-104">Updating Help Files</span></span>

<span data-ttu-id="fab58-105">Er zijn diverse redenen om bij te werken help-bestanden, zoals het corrigeren van fouten, een concept te verduidelijken, een veelgestelde vraag beantwoorden, nieuwe bestanden toe te voegen of toevoegen van nieuwe en betere voorbeelden.</span><span class="sxs-lookup"><span data-stu-id="fab58-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="fab58-106">Bijwerken van een help-bestand:</span><span class="sxs-lookup"><span data-stu-id="fab58-106">To update a help file:</span></span>

1. <span data-ttu-id="fab58-107">De bestanden wijzigen.</span><span class="sxs-lookup"><span data-stu-id="fab58-107">Change the files.</span></span>

2. <span data-ttu-id="fab58-108">De bestanden vertalen in andere culturen gebruikersinterface.</span><span class="sxs-lookup"><span data-stu-id="fab58-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="fab58-109">Alle help-bestanden (nieuwe, gewijzigde en ongewijzigd) voor de module in elke gebruikersinterfacecultuur verzamelen.</span><span class="sxs-lookup"><span data-stu-id="fab58-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="fab58-110">De bestanden op basis van de XML-schema te valideren.</span><span class="sxs-lookup"><span data-stu-id="fab58-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="fab58-111">De CAB-bestanden voor elke gebruikersinterfacecultuur opnieuw.</span><span class="sxs-lookup"><span data-stu-id="fab58-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="fab58-112">In de HelpInfo XML-bestand, verhoog het versienummer van het CAB-bestand voor elke gebruikersinterfacecultuur.</span><span class="sxs-lookup"><span data-stu-id="fab58-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="fab58-113">De nieuwe CAB-bestanden uploaden naar de locatie die is opgegeven door de waarde van de **HelpContentUri** -element in het HelpInfo XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="fab58-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="fab58-114">De oudere CAB-bestanden vervangen door de nieuwe CAB-bestanden.</span><span class="sxs-lookup"><span data-stu-id="fab58-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="fab58-115">Het bijgewerkte HelpInfo XML-bestand uploaden naar de locatie die is opgegeven door de **HelpInfoUri** sleutel in de module-manifest.</span><span class="sxs-lookup"><span data-stu-id="fab58-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="fab58-116">Vervang het oudere HelpInfo XML-bestand door het nieuwe bestand.</span><span class="sxs-lookup"><span data-stu-id="fab58-116">Replace the older HelpInfo XML file with the new file.</span></span>