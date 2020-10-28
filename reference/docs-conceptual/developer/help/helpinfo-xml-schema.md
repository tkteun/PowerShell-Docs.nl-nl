---
ms.date: 09/12/2016
ms.topic: reference
title: HelpInfo-XML-schema
description: HelpInfo-XML-schema
ms.openlocfilehash: 157fd9c0f47c57efbaa9b7888fa174a34ad9567d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662021"
---
# <a name="helpinfo-xml-schema"></a>HelpInfo-XML-schema

Dit onderwerp bevat het XML-schema voor bijwerk bare Help-informatie bestanden, algemeen bekend als ' HelpInfo XML-bestanden '.

## <a name="helpinfo-xml-schema"></a>HelpInfo-XML-schema

HelpInfo XML-bestanden zijn gebaseerd op het volgende XML-schema.

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="http://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
  <element name="HelpInfo">
    <complexType>
      <sequence>
        <element name="HelpContentURI" type="anyURI" minOccurs="1" maxOccurs="1" />
        <element name="SupportedUICultures" minOccurs="1" maxOccurs="1">
          <complexType>
            <sequence>
              <element name="UICulture" minOccurs="1" maxOccurs="unbounded">
                <complexType>
                  <sequence>
                    <element name="UICultureName" type="language" minOccurs="1" maxOccurs="1" />
                    <element name="UICultureVersion" type="string" minOccurs="1" maxOccurs="1" />
                  </sequence>
                </complexType>
              </element>
            </sequence>
          </complexType>
        </element>
      </sequence>
    </complexType>
  </element>
</schema>
```

## <a name="helpinfo-xml-elements"></a>HelpInfo XML-elementen

Het HelpInfo XML-bestand bevat de volgende elementen.

- **HelpContentURI** : bevat de URI van de locatie van de cab-bestanden voor de Help voor de module. De URI moet beginnen met http of https. De URI moet een Internet locatie opgeven, maar mag de CAB-bestands naam niet bevatten. De **HelpContentURI** -waarde kan gelijk zijn aan of verschillen van de **HelpInfoURI** -waarde.

- **SupportedUICultures** : dit is de Help-bestanden van de module in alle gebruikersinterface culturen. Bevat **uiCulture** -elementen, die elk een set Help-bestanden voor de module in een opgegeven UI-cultuur vertegenwoordigen.

- **UiCulture** : vertegenwoordigt een set Help-bestanden voor de module in een opgegeven UI-cultuur. Voeg een **uiCulture** -element toe voor elke UI-cultuur waarin de Help bestanden zijn geschreven.

- **UICultureName** : bevat de taal code voor de UI-cultuur waarin de Help-bestanden zijn geschreven.

- **UICultureVersion** -bevat een versie nummer van 4 onderdelen in N1. N2. N3. N4: dit is de indeling die de versie van het CAB-bestand van de Help vertegenwoordigt in de UI-cultuur. Verhoog dit versie nummer telkens wanneer u nieuwe CAB-bestanden van de Help uploadt in de UI-cultuur die is opgegeven door **UICultureName** . Zie [versie klasse](/dotnet/api/system.version)voor meer informatie over deze waarde.
