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
# <a name="how-to-create-a-helpinfo-xml-file"></a>Een HelpInfo-XML-bestand maken

Deze onderwerpen in deze sectie wordt uitgelegd hoe u maken en vullen van een helpbestand informatie, gewoonlijk bekend als 'HelpInfo XML-bestand,' voor de Windows PowerShell bij te werken Help-functie.

## <a name="helpinfo-xml-file-overview"></a>Overzicht van HelpInfo XML-bestand

Het HelpInfo XML-bestand is de primaire bron van informatie over het bij te werken Help voor de module. Dit omvat de locatie van de help-bestanden voor de modules, de ondersteunde culturen voor de gebruikersinterface en de versienummers die bij te werken Help gebruikt om te bepalen of de gebruiker de meest recente help-bestanden.

Elke module heeft slechts één HelpInfo XML-bestand, zelfs als de module meerdere help-bestanden voor meerdere UI culturen bevat. De module-auteur het HelpInfo XML-bestand wordt gemaakt en plaatst het in de Internet-locatie die is opgegeven door de **HelpInfoUri** sleutel in de module-manifest. Wanneer de module help-bestanden worden bijgewerkt en worden geüpload, wordt de module-auteur werkt het HelpInfo XML-bestand en vervangt het oorspronkelijke HelpInfo XML-bestand met de nieuwe versie.

Het is essentieel dat het HelpInfo XML-bestand zorgvuldig wordt gehandhaafd. Als u nieuwe bestanden uploaden, maar vergeet de versienummers toenemen, bij te werken Help wordt niet de nieuwe bestanden downloaden naar computers van gebruikers. Als u help-bestanden voor een nieuwe gebruikersinterfacecultuur toevoegen, maar geen HelpInfo XML-bestand of plaats deze in de juiste locatie, wordt er bij het bij te werken Help niet de nieuwe bestanden downloaden.

## <a name="in-this-section"></a>In deze sectie

Deze sectie bevat de volgende onderwerpen:

- [HelpInfo XML Schema](./helpinfo-xml-schema.md)

- [HelpInfo XML-voorbeeldbestand](./helpinfo-xml-sample-file.md)

- [Naamconventies voor een HelpInfo XML-bestand](./how-to-name-a-helpinfo-xml-file.md)

- [Over het instellen van de versienummers HelpInfo XML](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>Zie ook

[Ondersteunende Help die kan worden bijgewerkt](./supporting-updatable-help.md)