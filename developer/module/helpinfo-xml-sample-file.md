---
title: HelpInfo XML-voorbeeldbestand | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6544070f-5549-407f-8603-5df60fe9e013
caps.latest.revision: 7
ms.openlocfilehash: 11804db56ec47554e82f04fe6954920ad9577370
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082427"
---
# <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="eeac8-102">HelpInfo-XML-voorbeeldbestand</span><span class="sxs-lookup"><span data-stu-id="eeac8-102">HelpInfo XML Sample File</span></span>

<span data-ttu-id="eeac8-103">In dit onderwerp geeft een voorbeeld van een opgemaakte bij te werken Help-informatie-bestand, bekend als "HelpInfo XML-bestand."</span><span class="sxs-lookup"><span data-stu-id="eeac8-103">This topic displays a sample of a well-formed Updatable Help Information file, commonly known as "HelpInfo XML file."</span></span> <span data-ttu-id="eeac8-104">In dit voorbeeldbestand zijn de cultuur UI-elementen in alfabetische volgorde geordend op cultuurnaam gebruikersinterface.</span><span class="sxs-lookup"><span data-stu-id="eeac8-104">In this sample file, the UI culture elements are arranged in alphabetical order by UI culture name.</span></span> <span data-ttu-id="eeac8-105">Alfabetische volgorde is een aanbevolen procedure, maar dit is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="eeac8-105">Alphabetical ordering is a best practice, but it is not required.</span></span>

## <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="eeac8-106">HelpInfo-XML-voorbeeldbestand</span><span class="sxs-lookup"><span data-stu-id="eeac8-106">HelpInfo XML Sample File</span></span>

```xml

<?xml version="1.0" encoding="utf-8"?>
<HelpInfo xmlns="http://schemas.microsoft.com/powershell/help/2010/05">
   <HelpContentURI>http://go.microsoft.com/fwlink/?LinkID=141553</HelpContentURI>
   <SupportedUICultures>
    <UICulture>
      <UICultureName>de-DE</UICultureName>
      <UICultureVersion>2.15.0.10</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>en-US</UICultureName>
      <UICultureVersion>3.2.0.7</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>it-IT</UICultureName>
      <UICultureVersion>1.1.0.5</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>ja-JP</UICultureName>
      <UICultureVersion>3.2.0.4</UICultureVersion>
    </UICulture>
   </SupportedUICultures>
</HelpInfo>

```