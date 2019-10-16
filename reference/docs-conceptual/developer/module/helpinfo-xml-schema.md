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
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="2bc77-102">HelpInfo-XML-schema</span><span class="sxs-lookup"><span data-stu-id="2bc77-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="2bc77-103">Dit onderwerp bevat het XML-schema voor bijwerk bare Help-informatie bestanden, algemeen bekend als ' HelpInfo XML-bestanden '.</span><span class="sxs-lookup"><span data-stu-id="2bc77-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="2bc77-104">HelpInfo-XML-schema</span><span class="sxs-lookup"><span data-stu-id="2bc77-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="2bc77-105">HelpInfo XML-bestanden zijn gebaseerd op het volgende XML-schema.</span><span class="sxs-lookup"><span data-stu-id="2bc77-105">HelpInfo XML files are based on the following XML schema.</span></span>

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

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="2bc77-106">HelpInfo XML-elementen</span><span class="sxs-lookup"><span data-stu-id="2bc77-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="2bc77-107">Het HelpInfo XML-bestand bevat de volgende elementen.</span><span class="sxs-lookup"><span data-stu-id="2bc77-107">The HelpInfo XML file includes the following elements.</span></span>

<span data-ttu-id="2bc77-108">HelpContentURI bevat de URI van de locatie van de CAB-bestanden voor de Help voor de module.</span><span class="sxs-lookup"><span data-stu-id="2bc77-108">HelpContentURI Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="2bc77-109">De URI moet beginnen met http of https.</span><span class="sxs-lookup"><span data-stu-id="2bc77-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="2bc77-110">De URI moet een Internet locatie opgeven, maar mag de naam van het CAB-bestand niet bevatten.</span><span class="sxs-lookup"><span data-stu-id="2bc77-110">The URI should specify an Internet location, but must not include the CAB file name.</span></span> <span data-ttu-id="2bc77-111">De **HelpContentURI** -waarde kan gelijk zijn aan of verschillen van de **HelpInfoURI** -waarde.</span><span class="sxs-lookup"><span data-stu-id="2bc77-111">The **HelpContentURI** value can be the  same or different from the **HelpInfoURI** value.</span></span>

<span data-ttu-id="2bc77-112">SupportedUICultures vertegenwoordigt de Help-bestanden van de module in alle GEBRUIKERSINTERFACE culturen.</span><span class="sxs-lookup"><span data-stu-id="2bc77-112">SupportedUICultures Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="2bc77-113">Bevat **uiCulture** -elementen, die elk een set Help-bestanden voor de module in een opgegeven UI-cultuur vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="2bc77-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

<span data-ttu-id="2bc77-114">UICulture vertegenwoordigt een set Help-bestanden voor de module in een opgegeven UI-cultuur.</span><span class="sxs-lookup"><span data-stu-id="2bc77-114">UICulture Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="2bc77-115">Voeg een **uiCulture** -element toe voor elke UI-cultuur waarin de Help bestanden zijn geschreven.</span><span class="sxs-lookup"><span data-stu-id="2bc77-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

<span data-ttu-id="2bc77-116">UICultureName bevat de taal code voor de UI-cultuur waarin de Help-bestanden zijn geschreven.</span><span class="sxs-lookup"><span data-stu-id="2bc77-116">UICultureName Contains the language code for the UI culture in which the help files are written.</span></span>

<span data-ttu-id="2bc77-117">UICultureVersion bevat een versie nummer van 4 onderdelen in N1. N2. N3. N4: dit is de indeling die de versie van het CAB-bestand van de Help vertegenwoordigt in de UI-cultuur.</span><span class="sxs-lookup"><span data-stu-id="2bc77-117">UICultureVersion Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="2bc77-118">Verhoog dit versie nummer telkens wanneer u nieuwe CAB-bestanden van de Help uploadt in de UI-cultuur die is opgegeven door **UICultureName**.</span><span class="sxs-lookup"><span data-stu-id="2bc77-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="2bc77-119">Zie "version-klasse (systeem)" in MSDN voor meer informatie over deze waarde.</span><span class="sxs-lookup"><span data-stu-id="2bc77-119">For more information about this value, see "Version Class (System)" in MSDN.</span></span>