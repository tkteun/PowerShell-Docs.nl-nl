---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: Lijst met pakketten opzeggen
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71329027"
---
# <a name="unlisting-packages"></a>Pakketten uit de catalogus verwijderen

**Waarom wordt het verwijderen van een pakket uit PowerShell Gallery niet weer gegeven als een optie?**

De PowerShell Gallery biedt geen ondersteuning voor gebruikers die hun pakketten permanent verwijderen.
Op deze manier kunnen anderen afhankelijkheden maken op uw pakketten zonder dat u in de toekomst over mogelijke onderbrekingen hoeft te zorgen.
Als de insluitings module bijvoorbeeld afhankelijk is van de Azure-module en de Azure-module uit de galerie is verwijderd, kan de gebruiker niet langer gebruikmaken van de module Pest.

In plaats van een pakket te verwijderen, kunt u de weer gave echter opheffen.

**Wat houdt het weer geven van een pakket op PowerShell Gallery?**

Het opheffen van de weer geven van een pakket, zoals module of script op PowerShell Gallery, wordt verwijderd uit het tabblad pakketten. Daarnaast kunnen niet-vermelde pakketten niet worden gedetecteerd met behulp van de zoek balk.
De enige manier om een niet-vermeld pakket te downloaden, is door de exacte naam en versie van het pakket op te geven.
Als gevolg hiervan worden de onvermelding van een pakket geen andere modules of scripts die hiervan afhankelijk zijn, verbroken.

Ga naar de pagina pakket Details en selecteer module verwijderen om het pakket weer te geven. Schakel het selectie vakje ' weer gegeven ' uit en klik op opslaan.

**Hoe kan ik een pakket verwijderen?**

Als u een scenario ondervindt waarbij het verwijderen van pakketten nood zakelijk is, neemt u contact op met de PowerShell Gallery-beheerders.
Geldige verwijderings scenario's zijn:
- Problemen met inbreuk op het auteurs recht.
- Het pakket bevat mogelijk schadelijke inhoud.
- Het pakket bevat gevoelige gegevens.

Als u een aanvraag voor het verwijderen van een pakket wilt indienen bij de PowerShell Gallery beheerders, gaat u naar de detail pagina van uw pakket en selecteert u contact opnemen met ondersteuning.
