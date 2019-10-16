---
title: HelpInfo XML-schema | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 0f965f4ee1ef92a6a538b52b4348c04366cabf66
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352932"
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

HelpContentURI bevat de URI van de locatie van de CAB-bestanden voor de Help voor de module. De URI moet beginnen met http of https. De URI moet een Internet locatie opgeven, maar mag de naam van het CAB-bestand niet bevatten. De **HelpContentURI** -waarde kan gelijk zijn aan of verschillen van de **HelpInfoURI** -waarde.

SupportedUICultures vertegenwoordigt de Help-bestanden van de module in alle GEBRUIKERSINTERFACE culturen. Bevat **uiCulture** -elementen, die elk een set Help-bestanden voor de module in een opgegeven UI-cultuur vertegenwoordigen.

UICulture vertegenwoordigt een set Help-bestanden voor de module in een opgegeven UI-cultuur. Voeg een **uiCulture** -element toe voor elke UI-cultuur waarin de Help bestanden zijn geschreven.

UICultureName bevat de taal code voor de UI-cultuur waarin de Help-bestanden zijn geschreven.

UICultureVersion bevat een versie nummer van 4 onderdelen in N1. N2. N3. N4: dit is de indeling die de versie van het CAB-bestand van de Help vertegenwoordigt in de UI-cultuur. Verhoog dit versie nummer telkens wanneer u nieuwe CAB-bestanden van de Help uploadt in de UI-cultuur die is opgegeven door **UICultureName**. Zie "version-klasse (systeem)" in MSDN voor meer informatie over deze waarde.