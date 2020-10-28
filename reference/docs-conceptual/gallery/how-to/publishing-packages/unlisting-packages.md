---
ms.date: 06/12/2017
title: Lijst met pakketten opzeggen
description: De PowerShell Gallery biedt geen ondersteuning voor gebruikers die hun pakketten permanent verwijderen. Op deze manier kunnen anderen afhankelijkheden maken op uw pakketten zonder dat u in de toekomst over mogelijke onderbrekingen hoeft te zorgen.
ms.openlocfilehash: 738167011f64b5174df3504c8e1d06146f4c7db5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662421"
---
# <a name="unlisting-packages"></a>Pakketten uit de catalogus verwijderen

**Waarom wordt het verwijderen van een pakket uit PowerShell Gallery niet weer gegeven als een optie?**

De PowerShell Gallery biedt geen ondersteuning voor gebruikers die hun pakketten permanent verwijderen. Op deze manier kunnen anderen afhankelijkheden maken op uw pakketten zonder dat u in de toekomst over mogelijke onderbrekingen hoeft te zorgen.
Als de insluitings module bijvoorbeeld afhankelijk is van de Azure-module en de Azure-module uit de galerie wordt verwijderd, kunnen gebruikers de module pest niet meer gebruiken.

In plaats van een pakket te verwijderen, kunt u de weer gave ervan opheffen.

**Wat houdt het weer geven van een pakket op PowerShell Gallery?**

Als u de weer geven van een pakket, zoals een module of script in de PowerShell Gallery, verwijdert u dit op het tabblad pakketten. Daarnaast kunnen niet-vermelde pakketten niet worden gedetecteerd met behulp van de zoek balk. De enige manier om een niet-vermeld pakket te downloaden, is door de exacte naam en versie van het pakket op te geven. Als gevolg hiervan worden de onweer gave van een pakket geen andere modules of scripts die hiervan afhankelijk zijn.

Ga naar de pagina pakket Details en selecteer module verwijderen om het pakket weer te geven. Schakel het selectie vakje ' weer gegeven ' uit en selecteer Opslaan.

**Hoe kan ik een pakket verwijderen?**

Als u een scenario ondervindt waarbij het verwijderen van pakketten nood zakelijk is, neemt u contact op met de PowerShell Gallery-beheerders. Geldige verwijderings scenario's zijn:

- Problemen met inbreuk op het auteurs recht.
- Het pakket bevat mogelijk schadelijke inhoud.
- Het pakket bevat gevoelige gegevens.

Als u een aanvraag voor het verwijderen van een pakket wilt indienen bij de PowerShell Gallery beheerders, gaat u naar de detail pagina van uw pakket en selecteert u contact opnemen met ondersteuning.
