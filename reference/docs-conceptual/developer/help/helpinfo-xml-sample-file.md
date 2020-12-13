---
ms.date: 09/12/2016
ms.topic: reference
title: HelpInfo-XML-voorbeeldbestand
description: HelpInfo-XML-voorbeeldbestand
ms.openlocfilehash: 321793d61ab5df3cccc7c353b6c93f5a7275b533
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647768"
---
# <a name="helpinfo-xml-sample-file"></a>HelpInfo-XML-voorbeeldbestand

In dit onderwerp wordt een voor beeld weer gegeven van een juist opgemaakt bestand met Help-informatie, algemeen bekend als ' HelpInfo XML-bestand '. In dit voorbeeld bestand worden de UI-cultuur-elementen in alfabetische volg orde gerangschikt op naam van de UI-cultuur. Alfabetische volg orde is een best practice, maar dit is niet vereist.

## <a name="helpinfo-xml-sample-file"></a>HelpInfo-XML-voorbeeldbestand

```xml

<?xml version="1.0" encoding="utf-8"?>
<HelpInfo xmlns="http://schemas.microsoft.com/powershell/help/2010/05">
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
