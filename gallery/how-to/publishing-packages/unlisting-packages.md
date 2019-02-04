---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Pakketten uit catalogus verwijderen
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684393"
---
# <a name="unlisting-packages"></a>Pakketten uit de catalogus verwijderen

**Waarom is een pakket verwijderen vanuit PowerShell Gallery is niet beschikbaar zijn gemaakt als een optie?**

De PowerShell Gallery biedt geen ondersteuning voor gebruikers permanent verwijderen van hun pakketten.
Hierdoor kunnen anderen uw pakketten afhankelijkheden uitvoeren zonder dat u eventuele onderbrekingen in de toekomst.
Als de module Pester is afhankelijk van de Azure-module en de Azure-module wordt verwijderd uit de galerie, en vervolgens de gebruiker kan niet meer gebruikt bijvoorbeeld de Pester-module.

In plaats van een pakket is verwijderd, maar kunt u unlist deze in plaats daarvan.

**Wat doet uit catalogus verwijderen een pakket op PowerShell Gallery doen?**

Een pakket, zoals de module of script op PowerShell Gallery uit catalogus verwijderen, wordt deze verwijderd uit het tabblad pakketten. Niet-vermelde pakketten wordt bovendien niet worden gedetecteerd via de zoekbalk.
De enige manier om een niet-vermelde pakket te downloaden is om op te geven van de exacte naam en versie van het pakket.
Als gevolg hiervan wordt uit catalogus verwijderen van een pakket niet verbroken andere modules of scripts die afhankelijk van deze zijn.

Als u wilt uw pakket unlist, gaat u naar de pagina met details van pakket en selecteert u 'Module verwijderen'. Schakel het selectievakje 'Hier' uit en klik op opslaan.

**Hoe kan ik een pakket verwijderen?**

Als u een scenario waarbij pakket verwijderen die nodig zijn, moet u contact op met de PowerShell Gallery-beheerders.
Geldige verwijdering scenario's:
- Problemen met auteursrecht.
- Het pakket bevat mogelijk schadelijke inhoud.
- Pakket bevat gevoelige gegevens.

Als u wilt een verwijderen pakket aanvragen naar de PowerShell Gallery-beheerders, gaat u naar de detailpagina van het pakket en selecteert u contact opnemen met ondersteuning.
