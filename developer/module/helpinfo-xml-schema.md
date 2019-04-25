---
title: HelpInfo XML-Schema | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 0f965f4ee1ef92a6a538b52b4348c04366cabf66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082461"
---
# <a name="helpinfo-xml-schema"></a>HelpInfo-XML-schema

In dit onderwerp bevat de XML-schema voor de bestanden bij te werken Help-informatie, bekend als "HelpInfo XML-bestanden."

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

HelpContentURI bevat de URI van de locatie van de help van CAB-bestanden voor de module. De URI moet beginnen met 'http' of 'https'. De URI moet een Internet-locatie opgeven, maar niet de naam van het CAB-bestand moet bevatten. De **HelpContentURI** waarde kan zijn dezelfde of verschillend is van de **HelpInfoURI** waarde.

SupportedUICultures geeft de help-bestanden van de module in alle culturen van de gebruikersinterface. Bevat **UICulture** elementen, die elk een set van help-bestanden voor de module in een opgegeven gebruikersinterfacecultuur vertegenwoordigt.

UICulture vertegenwoordigt een reeks help-bestanden voor de module in een opgegeven gebruikersinterfacecultuur. Voeg een **UICulture** -element voor elk UI-cultuur waarin u de help-bestanden worden geschreven.

UICultureName bevat de taalcode voor de UI-cultuur waarin u de help-bestanden worden geschreven.

UICultureVersion bevat een versienummer van 4-onderdeel in 'N1. N2. N3. N4 '-indeling die de versie van de help CAB-bestand in de gebruikersinterfacecultuur vertegenwoordigt. Dit versienummer verhoogd telkens wanneer u nieuwe help CAB-bestanden in de UI-cultuur die is opgegeven door uploaden **UICultureName**. Zie "Versie Class (systeem)" in MSDN voor meer informatie over deze waarde.