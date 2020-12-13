---
ms.date: 09/12/2016
ms.topic: reference
title: HelpInfo-XML-schema
description: HelpInfo-XML-schema
ms.openlocfilehash: 157fd9c0f47c57efbaa9b7888fa174a34ad9567d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92662021"
---
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="42502-103">HelpInfo-XML-schema</span><span class="sxs-lookup"><span data-stu-id="42502-103">HelpInfo XML Schema</span></span>

<span data-ttu-id="42502-104">Dit onderwerp bevat het XML-schema voor bijwerk bare Help-informatie bestanden, algemeen bekend als ' HelpInfo XML-bestanden '.</span><span class="sxs-lookup"><span data-stu-id="42502-104">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="42502-105">HelpInfo-XML-schema</span><span class="sxs-lookup"><span data-stu-id="42502-105">HelpInfo XML Schema</span></span>

<span data-ttu-id="42502-106">HelpInfo XML-bestanden zijn gebaseerd op het volgende XML-schema.</span><span class="sxs-lookup"><span data-stu-id="42502-106">HelpInfo XML files are based on the following XML schema.</span></span>

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

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="42502-107">HelpInfo XML-elementen</span><span class="sxs-lookup"><span data-stu-id="42502-107">HelpInfo XML Elements</span></span>

<span data-ttu-id="42502-108">Het HelpInfo XML-bestand bevat de volgende elementen.</span><span class="sxs-lookup"><span data-stu-id="42502-108">The HelpInfo XML file includes the following elements.</span></span>

- <span data-ttu-id="42502-109">**HelpContentURI** : bevat de URI van de locatie van de cab-bestanden voor de Help voor de module.</span><span class="sxs-lookup"><span data-stu-id="42502-109">**HelpContentURI** - Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="42502-110">De URI moet beginnen met http of https.</span><span class="sxs-lookup"><span data-stu-id="42502-110">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="42502-111">De URI moet een Internet locatie opgeven, maar mag de CAB-bestands naam niet bevatten.</span><span class="sxs-lookup"><span data-stu-id="42502-111">The URI should specify an internet location, but must not include the CAB filename.</span></span> <span data-ttu-id="42502-112">De **HelpContentURI** -waarde kan gelijk zijn aan of verschillen van de **HelpInfoURI** -waarde.</span><span class="sxs-lookup"><span data-stu-id="42502-112">The **HelpContentURI** value can be the same or different from the **HelpInfoURI** value.</span></span>

- <span data-ttu-id="42502-113">**SupportedUICultures** : dit is de Help-bestanden van de module in alle gebruikersinterface culturen.</span><span class="sxs-lookup"><span data-stu-id="42502-113">**SupportedUICultures** - Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="42502-114">Bevat **uiCulture** -elementen, die elk een set Help-bestanden voor de module in een opgegeven UI-cultuur vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="42502-114">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

- <span data-ttu-id="42502-115">**UiCulture** : vertegenwoordigt een set Help-bestanden voor de module in een opgegeven UI-cultuur.</span><span class="sxs-lookup"><span data-stu-id="42502-115">**UICulture** - Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="42502-116">Voeg een **uiCulture** -element toe voor elke UI-cultuur waarin de Help bestanden zijn geschreven.</span><span class="sxs-lookup"><span data-stu-id="42502-116">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

- <span data-ttu-id="42502-117">**UICultureName** : bevat de taal code voor de UI-cultuur waarin de Help-bestanden zijn geschreven.</span><span class="sxs-lookup"><span data-stu-id="42502-117">**UICultureName** - Contains the language code for the UI culture in which the help files are written.</span></span>

- <span data-ttu-id="42502-118">**UICultureVersion** -bevat een versie nummer van 4 onderdelen in N1. N2. N3. N4: dit is de indeling die de versie van het CAB-bestand van de Help vertegenwoordigt in de UI-cultuur.</span><span class="sxs-lookup"><span data-stu-id="42502-118">**UICultureVersion** - Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="42502-119">Verhoog dit versie nummer telkens wanneer u nieuwe CAB-bestanden van de Help uploadt in de UI-cultuur die is opgegeven door **UICultureName**.</span><span class="sxs-lookup"><span data-stu-id="42502-119">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="42502-120">Zie [versie klasse](/dotnet/api/system.version)voor meer informatie over deze waarde.</span><span class="sxs-lookup"><span data-stu-id="42502-120">For more information about this value, see [Version Class](/dotnet/api/system.version).</span></span>
