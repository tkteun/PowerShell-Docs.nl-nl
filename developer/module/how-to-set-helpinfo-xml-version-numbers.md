---
title: Over het instellen van de versienummers HelpInfo XML | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: d69e8a734aa96ff9b7911815fb43b81103548b59
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794345"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>HelpInfo-XML-versienummers instellen

In dit onderwerp wordt uitgelegd hoe u het instellen en het verhogen van de versienummers in een bestand bij te werken Help-informatie, bekend als een 'HelpInfo XML file'.

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>HelpInfo-XML-versienummers instellen

De versienummers in een HelpInfo XML-bestand zijn essentieel voor de werking van het bij te werken Help. De [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en [Help opslaan](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets nieuwe help-bestanden te downloaden alleen wanneer het versienummer voor een UI-cultuur in de externe HelpInfo XML-bestand is groter dan het versienummer voor die gebruikersinterfacecultuur in de lokale HelpInfo XML, of er is geen lokale HelpInfo XML-bestand.

Het HelpInfo XML-bestand maakt gebruik van de 4-onderdeel versienummer dat is gedefinieerd in de **System.Version** klasse van Microsoft .NET Framework. De indeling is `N1.N2.N3.N4`. Module-auteurs kunnen een schema dat is toegestaan door de nummering versie gebruiken de **System.Version** klasse. Bij te werken Help vereist alleen dat het versienummer voor een verhoging van de cultuur gebruikersinterface wanneer een nieuwe versie van het CAB-bestand voor dat gebruikersinterfacecultuur wordt geüpload naar de locatie die is opgegeven door de **HelpContentURI** -element in het HelpInfo XML-bestand.

Het volgende voorbeeld ziet u de elementen van het HelpInfo XML-bestand voor de Duitse (nl-nl) gebruikersinterface van de cultuur als de versie 2.15.0.10.

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

Het versienummer voor een gebruikersinterfacecultuur geeft de versie van het CAB-bestand voor dat gebruikersinterfacecultuur. Het versienummer is van toepassing op het hele CAB-bestand. U kunt verschillende versienummers voor verschillende bestanden niet instellen in het CAB-bestand. Het versienummer voor elk gebruikersinterfacecultuur onafhankelijk wordt geëvalueerd en moet niet worden gerelateerd aan de versienummers voor andere UI-culturen die ondersteuning biedt voor de module.