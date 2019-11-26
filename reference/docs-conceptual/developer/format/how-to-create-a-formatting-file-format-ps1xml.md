---
title: Een opmaak bestand (. Format. ps1xml) maken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354955"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>Een opmaakbestand (.format.ps1xml) maken

In dit onderwerp wordt beschreven hoe u een opmaak bestand (. Format. ps1xml) maakt.

> [!NOTE]
> U kunt ook een opmaak bestand maken door een kopie te maken van een van de bestanden die worden meegeleverd met Windows Power shell. Als u een kopie van een bestaand bestand maakt, verwijdert u de bestaande digitale hand tekening en voegt u uw eigen hand tekening toe aan het nieuwe bestand.

### <a name="to-create-a-formatps1xml-file"></a>Maken van een. Format. ps1xml-bestand.

1. Maak een tekst bestand (. txt) met behulp van een tekst editor zoals Klad blok.

2. Kopieer de volgende regels naar het opmaak bestand.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - Met de \<Configuration > \</Configuration > Tags wordt het hoofd knooppunt `Configuration` gedefinieerd. Alle extra XML-tags worden inge sloten binnen dit knoop punt.

   - De <ViewDefinitions></ViewDefinitions> Tags definiëren het knoop punt `ViewDefinitions`. Alle weer gaven worden binnen dit knoop punt gedefinieerd.

3. Sla het bestand op naar de installatiemap van Windows Power shell, naar de map module, of naar een submap van de map module. Gebruik de volgende naam indeling wanneer u het bestand opslaat: `MyFile.format.ps1xml`. Het format teren van bestanden moet de uitbrei ding `.format.ps1xml` gebruiken.

   U bent nu klaar om weer gaven toe te voegen aan het opmaak bestand. Er is geen limiet voor het aantal weer gaven dat kan worden gedefinieerd in een opmaak bestand. U kunt één weer gave voor elk object, meerdere weer gaven voor hetzelfde object of één weer gave die wordt gebruikt door meerdere objecten toevoegen.

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-indeling en-type bestand schrijven](./writing-a-powershell-formatting-file.md)