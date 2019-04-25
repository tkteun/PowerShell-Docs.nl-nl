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
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="77323-102">HelpInfo-XML-schema</span><span class="sxs-lookup"><span data-stu-id="77323-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="77323-103">In dit onderwerp bevat de XML-schema voor de bestanden bij te werken Help-informatie, bekend als "HelpInfo XML-bestanden."</span><span class="sxs-lookup"><span data-stu-id="77323-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="77323-104">HelpInfo-XML-schema</span><span class="sxs-lookup"><span data-stu-id="77323-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="77323-105">HelpInfo XML-bestanden zijn gebaseerd op het volgende XML-schema.</span><span class="sxs-lookup"><span data-stu-id="77323-105">HelpInfo XML files are based on the following XML schema.</span></span>

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

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="77323-106">HelpInfo XML-elementen</span><span class="sxs-lookup"><span data-stu-id="77323-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="77323-107">Het HelpInfo XML-bestand bevat de volgende elementen.</span><span class="sxs-lookup"><span data-stu-id="77323-107">The HelpInfo XML file includes the following elements.</span></span>

<span data-ttu-id="77323-108">HelpContentURI bevat de URI van de locatie van de help van CAB-bestanden voor de module.</span><span class="sxs-lookup"><span data-stu-id="77323-108">HelpContentURI Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="77323-109">De URI moet beginnen met 'http' of 'https'.</span><span class="sxs-lookup"><span data-stu-id="77323-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="77323-110">De URI moet een Internet-locatie opgeven, maar niet de naam van het CAB-bestand moet bevatten.</span><span class="sxs-lookup"><span data-stu-id="77323-110">The URI should specify an Internet location, but must not include the CAB file name.</span></span> <span data-ttu-id="77323-111">De **HelpContentURI** waarde kan zijn dezelfde of verschillend is van de **HelpInfoURI** waarde.</span><span class="sxs-lookup"><span data-stu-id="77323-111">The **HelpContentURI** value can be the  same or different from the **HelpInfoURI** value.</span></span>

<span data-ttu-id="77323-112">SupportedUICultures geeft de help-bestanden van de module in alle culturen van de gebruikersinterface.</span><span class="sxs-lookup"><span data-stu-id="77323-112">SupportedUICultures Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="77323-113">Bevat **UICulture** elementen, die elk een set van help-bestanden voor de module in een opgegeven gebruikersinterfacecultuur vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="77323-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

<span data-ttu-id="77323-114">UICulture vertegenwoordigt een reeks help-bestanden voor de module in een opgegeven gebruikersinterfacecultuur.</span><span class="sxs-lookup"><span data-stu-id="77323-114">UICulture Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="77323-115">Voeg een **UICulture** -element voor elk UI-cultuur waarin u de help-bestanden worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="77323-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

<span data-ttu-id="77323-116">UICultureName bevat de taalcode voor de UI-cultuur waarin u de help-bestanden worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="77323-116">UICultureName Contains the language code for the UI culture in which the help files are written.</span></span>

<span data-ttu-id="77323-117">UICultureVersion bevat een versienummer van 4-onderdeel in 'N1. N2. N3. N4 '-indeling die de versie van de help CAB-bestand in de gebruikersinterfacecultuur vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="77323-117">UICultureVersion Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="77323-118">Dit versienummer verhoogd telkens wanneer u nieuwe help CAB-bestanden in de UI-cultuur die is opgegeven door uploaden **UICultureName**.</span><span class="sxs-lookup"><span data-stu-id="77323-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="77323-119">Zie "Versie Class (systeem)" in MSDN voor meer informatie over deze waarde.</span><span class="sxs-lookup"><span data-stu-id="77323-119">For more information about this value, see "Version Class (System)" in MSDN.</span></span>