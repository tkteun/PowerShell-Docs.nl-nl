---
title: Een HelpInfo XML-bestand maken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 1f09146a9e6456584f67edb52407193d8a9330ce
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811294"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>Een HelpInfo-XML-bestand maken

In deze onderwerpen in deze sectie wordt uitgelegd hoe u een Help-informatie bestand maakt en vult, ook wel bekend als een ' HelpInfo XML-bestand ', voor de Help-functie van Windows Power shell die kan worden bijgewerkt.

## <a name="helpinfo-xml-file-overview"></a>Overzicht van HelpInfo XML-bestand

Het HelpInfo XML-bestand is de primaire bron van informatie over de bij te werken Help voor de module. Het bevat de locatie van de Help-bestanden voor de modules, de ondersteunde GEBRUIKERSINTERFACE culturen en de versie nummers die kunnen worden bijgewerkt om te bepalen of de gebruiker de nieuwste Help-bestanden heeft.

Elke module heeft slechts één HelpInfo XML-bestand, zelfs als de module meerdere Help-bestanden voor meerdere GEBRUIKERSINTERFACE culturen bevat. De auteur van de module maakt het HelpInfo XML-bestand en plaatst het op de Internet locatie die is opgegeven door de sleutel **HelpInfoUri** in het module manifest. Wanneer de Help-bestanden van de module zijn bijgewerkt en geüpload, wordt het HelpInfo XML-bestand door de module Auteur bijgewerkt en wordt het oorspronkelijke HelpInfo XML-bestand vervangen door de nieuwe versie.

Het is essentieel dat het XML-bestand HelpInfo zorgvuldig wordt bewaard. Als u nieuwe bestanden uploadt, maar vergeet de versie nummers niet te verhogen, worden de nieuwe bestanden niet gedownload naar de computers van gebruikers. Als u Help-bestanden toevoegt voor een nieuwe UI-cultuur, maar u het XML-bestand HelpInfo niet bijwerkt of op de juiste locatie plaatst, worden de nieuwe bestanden niet gedownload met de Help die kan worden bijgewerkt.

## <a name="in-this-section"></a>In deze sectie doet u het volgende

Deze sectie bevat de volgende onderwerpen:

- [HelpInfo-XML-schema](./helpinfo-xml-schema.md)

- [HelpInfo-XML-voorbeeldbestand](./helpinfo-xml-sample-file.md)

- [Een naam geven aan een HelpInfo-XML-bestand](./how-to-name-a-helpinfo-xml-file.md)

- [HelpInfo-XML-versienummers instellen](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>Zie ook

[Ondersteunende help die kan worden bijgewerkt](./supporting-updatable-help.md)
