---
title: HelpInfo XML-voorbeeld bestand | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6544070f-5549-407f-8603-5df60fe9e013
caps.latest.revision: 7
ms.openlocfilehash: 448cfbce4b387c31ea07fdd31376711f74f5d80c
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995910"
---
# <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="089b5-102">HelpInfo-XML-voorbeeldbestand</span><span class="sxs-lookup"><span data-stu-id="089b5-102">HelpInfo XML Sample File</span></span>

<span data-ttu-id="089b5-103">In dit onderwerp wordt een voor beeld weer gegeven van een juist opgemaakt bestand met Help-informatie, algemeen bekend als ' HelpInfo XML-bestand '.</span><span class="sxs-lookup"><span data-stu-id="089b5-103">This topic displays a sample of a well-formed Updatable Help Information file, commonly known as "HelpInfo XML file."</span></span> <span data-ttu-id="089b5-104">In dit voorbeeld bestand worden de UI-cultuur-elementen in alfabetische volg orde gerangschikt op naam van de UI-cultuur.</span><span class="sxs-lookup"><span data-stu-id="089b5-104">In this sample file, the UI culture elements are arranged in alphabetical order by UI culture name.</span></span> <span data-ttu-id="089b5-105">Alfabetische volg orde is een best practice, maar dit is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="089b5-105">Alphabetical ordering is a best practice, but it is not required.</span></span>

## <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="089b5-106">HelpInfo-XML-voorbeeldbestand</span><span class="sxs-lookup"><span data-stu-id="089b5-106">HelpInfo XML Sample File</span></span>

```xml

<?xml version="1.0" encoding="utf-8"?>
<HelpInfo xmlns="https://schemas.microsoft.com/powershell/help/2010/05">
   <HelpContentURI>https://go.microsoft.com/fwlink/?LinkID=141553</HelpContentURI>
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