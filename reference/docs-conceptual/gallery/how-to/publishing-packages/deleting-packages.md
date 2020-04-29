---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: Pakketten verwijderen
ms.openlocfilehash: 6bfb43b95e51d38bd606198cb8d2d9af0aa0be1e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328789"
---
# <a name="deleting-packages"></a>Pakketten verwijderen

De PowerShell Gallery biedt geen ondersteuning voor het permanent verwijderen van pakketten, omdat hierdoor iedereen die afhankelijk is van de beschik bare hoeveelheid, wordt verbroken.

In plaats daarvan ondersteunt de PowerShell Gallery een manier om de lijst van een pakket op te zeggen, dat kan worden uitgevoerd op de pagina pakket beheer op de website.
Wanneer een pakket niet is vermeld, wordt het niet meer weer gegeven in de zoek opdracht en in een pakket vermelding, zowel op de PowerShell Gallery als met PowerShellGet-opdrachten.
Het kan echter wel worden gedownload door de exacte versie op te geven. Dit houdt in dat de geautomatiseerde scripts blijven werken.

Als u een uitzonderlijke situatie hebt waarbij een van uw pakketten moet worden verwijderd, kan dit hand matig worden verwerkt door het PowerShell Gallery team.
Als er bijvoorbeeld sprake is van een inbreuk op het auteurs recht of mogelijk schadelijke inhoud, kan dit een geldige reden voor het verwijderen van het probleem zijn.
U moet in dat geval een ondersteunings aanvraag indienen via [PowerShell Gallery](https://www.PowerShellGallery.com) .
