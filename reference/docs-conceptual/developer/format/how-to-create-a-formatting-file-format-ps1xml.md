---
ms.date: 09/13/2016
ms.topic: reference
title: Een opmaakbestand (.format.ps1xml) maken
description: Een opmaakbestand (.format.ps1xml) maken
ms.openlocfilehash: 5bbc1ba40bfccf13636abc0f0751938aa724b761
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652009"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>Een opmaakbestand (.format.ps1xml) maken

In dit onderwerp wordt beschreven hoe u een opmaak bestand maakt (.format.ps1XML).

> [!NOTE]
> U kunt ook een opmaak bestand maken door een kopie te maken van een van de bestanden die worden meegeleverd met Windows Power shell. Als u een kopie van een bestaand bestand maakt, verwijdert u de bestaande digitale hand tekening en voegt u uw eigen hand tekening toe aan het nieuwe bestand.

### <a name="to-create-a-formatps1xml-file"></a>Een .format.ps1XML-bestand maken.

1. Maak een tekst bestand (. txt) met behulp van een tekst editor zoals Klad blok.

2. Kopieer de volgende regels naar het opmaak bestand.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - De `<Configuration></Configuration>` Tags definiëren het hoofd `Configuration` knooppunt. Alle extra XML-tags worden inge sloten binnen dit knoop punt.

   - De `<ViewDefinitions></ViewDefinitions>` Tags bepalen het `ViewDefinitions` knoop punt. Alle weer gaven worden binnen dit knoop punt gedefinieerd.

3. Sla het bestand op naar de installatiemap van Windows Power shell, naar de map module, of naar een submap van de map module. Gebruik de volgende naam indeling wanneer u het bestand opslaat:  `MyFile.format.ps1xml` . Het format teren van bestanden moet de `.format.ps1xml` extensie gebruiken.

   U bent nu klaar om weer gaven toe te voegen aan het opmaak bestand. Er is geen limiet voor het aantal weer gaven dat kan worden gedefinieerd in een opmaak bestand. U kunt één weer gave voor elk object, meerdere weer gaven voor hetzelfde object of één weer gave die wordt gebruikt door meerdere objecten toevoegen.

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-indeling en-type bestand schrijven](./writing-a-powershell-formatting-file.md)
