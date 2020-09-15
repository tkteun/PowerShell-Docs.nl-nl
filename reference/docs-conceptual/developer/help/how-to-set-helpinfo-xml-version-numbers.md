---
title: HelpInfo-XML-versienummers instellen
ms.date: 09/12/2016
ms.openlocfilehash: 42164f98414da0b6f1a0021e9d860c57a63a9eec
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892979"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>HelpInfo-XML-versienummers instellen

In dit onderwerp wordt uitgelegd hoe u de versie nummers instelt en verhoogt in een Help-informatie bestand dat kan worden bijgewerkt, ook wel bekend als een ' HelpInfo XML-bestand '.

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>HelpInfo-XML-versienummers instellen

De versie nummers in een HelpInfo XML-bestand zijn essentieel voor de werking van de Help-informatie die kan worden bijgewerkt. Met de cmdlets [Update Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) worden nieuwe Help-bestanden alleen gedownload wanneer het versie nummer voor een gebruikersinterface cultuur in het HelpInfo-bestand van de externe-XML groter is dan het versie nummer voor die gebruikersinterface cultuur in de lokale HelpInfo-XML, of er is geen lokaal HelpInfo XML-bestand.

Het HelpInfo XML-bestand maakt gebruik van het versie nummer van 4 onderdelen dat is gedefinieerd in de klasse **System. version** van het Microsoft .NET Framework. De indeling is `N1.N2.N3.N4`. Module auteurs kunnen elk schema voor versie nummering gebruiken dat is toegestaan door de klasse **System. version** . Bij te werken Help is alleen vereist dat het versie nummer van een UI-cultuur toeneemt wanneer een nieuwe versie van het CAB-bestand voor die GEBRUIKERSINTERFACE cultuur wordt geüpload naar de locatie die is opgegeven door het element **HelpContentURI** in het XML-bestand HelpInfo.

In het volgende voor beeld ziet u de elementen van het HelpInfo XML-bestand voor de Duitse interface cultuur (de-DE) wanneer de versie 2.15.0.10 is.

```xml
<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

Het versie nummer voor een GEBRUIKERSINTERFACE cultuur weerspiegelt de versie van het CAB-bestand voor die GEBRUIKERSINTERFACE cultuur. Het versie nummer is van toepassing op het hele CAB-bestand. U kunt geen andere versie nummers instellen voor verschillende bestanden in het CAB-bestand. Het versie nummer voor elke UI-cultuur wordt onafhankelijk geëvalueerd en hoeft niet te zijn gerelateerd aan de versie nummers voor andere GEBRUIKERSINTERFACE culturen die door de module worden ondersteund.
