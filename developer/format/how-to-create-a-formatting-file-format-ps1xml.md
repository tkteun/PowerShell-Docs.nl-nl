---
title: Over het maken van een opmaak-bestand (. format.ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851686"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>Een opmaakbestand (.format.ps1xml) maken

In dit onderwerp wordt beschreven hoe u een opmaak bestand te maken (. format.ps1xml).

> [!NOTE]
> U kunt ook een opmaak bestand maken door een kopie van een van de bestanden die worden geleverd door Windows PowerShell te maken. Als u bijvoorbeeld een kopie van een bestaand bestand, verwijder de bestaande digitale handtekening en uw eigen handtekening toevoegen aan het nieuwe bestand.

### <a name="to-create-a-formatps1xml-file"></a>Maakt een. format.ps1xml-bestand.

1. Maak een tekstbestand (.txt) met behulp van een SMS-bericht zoals Kladblok.

2. Kopieer de volgende regels in de opmaak bestand.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - De \<Configuration >\</Configuration > tags definiëren de hoofdmap `Configuration` knooppunt. Alle andere XML-labels wordt ingesloten in dit knooppunt.

   - De <ViewDefinitions> </ViewDefinitions> tags definiëren de `ViewDefinitions` knooppunt. Alle weergaven worden gedefinieerd in dit knooppunt.

3. Sla het bestand naar de installatiemap van Windows PowerShell, naar de modulemap van uw of naar een submap van de modulemap. Gebruik de volgende indeling wanneer u het bestand opslaat: `MyFile.format.ps1xml`. Opmaak bestanden moeten gebruiken de `.format.ps1xml` extensie.

   U bent nu klaar weergaven toevoegen aan de opmaak bestand. Er is geen limiet voor het aantal weergaven die kunnen worden gedefinieerd in een bestand met opmaak. U kunt één weergave voor elk object, meerdere weergaven voor hetzelfde object of een enkelvoudige weergave die wordt gebruikt door meerdere objecten toevoegen.

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell opmaak en het bestand van het type](./writing-a-powershell-formatting-file.md)
