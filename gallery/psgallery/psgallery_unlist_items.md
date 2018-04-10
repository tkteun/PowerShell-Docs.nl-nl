---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galerie, powershell, cmdlet, psgallery
title: psgallery_unlist_items
ms.openlocfilehash: af48f2ca889dcc101d466e40f2ecbe0cdf62c066
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="unlisting-items"></a>Items uit catalogus verwijderen

**Waarom verwijdert een item van PowerShell Gallery niet wordt weergegeven als een optie?**

De PowerShell-galerie biedt geen ondersteuning voor gebruikers die hun items permanent te verwijderen.
Hierdoor kunnen anderen uw items afhankelijkheden uitvoeren zonder dat u in de toekomst mogelijk einden.
Als de module Pester is afhankelijk van de Azure-module en de Azure-module is verwijderd uit de galerie en vervolgens de gebruiker kan niet meer gebruikt bijvoorbeeld de Pester-module.

In plaats van het verwijderen van een item, maar kunt u unlist deze in plaats daarvan.

**Wat wordt er een item in PowerShell Gallery doen unlisting?**

Een item bijvoorbeeld module of een script op basis van PowerShell Gallery unlisting wordt verwijderd uit het tabblad Items. Niet-vermelde items wordt bovendien niet worden gedetecteerd met behulp van de zoekbalk.
De enige manier om het downloaden van een niet-vermelde item is de exacte naam en versie van het item opgeven.
Als gevolg hiervan wordt unlisting van een item niet verbroken andere modules of scripts die afhankelijk zijn.

Uw item unlist, gaat u naar de pagina met objecten en selecteren Item verwijderen. Schakel het selectievakje 'Hier' uit en klik op opslaan.

**Hoe kan ik een item verwijderen?**

Als u een scenario waarbij item verwijdering nodig ondervindt, moet u contact op met de PowerShell-galerie-beheerders.
Verwijderen van een ongeldig scenario's:
- Problemen met het auteursrecht.
- Item bevat mogelijk schadelijke inhoud.
- Item bevat gevoelige gegevens.

Dien een verwijderd Item aanvraag naar de beheerders van PowerShell-galerie, gaat u naar de detailpagina voor het object en neem contact op met ondersteuning selecteren.