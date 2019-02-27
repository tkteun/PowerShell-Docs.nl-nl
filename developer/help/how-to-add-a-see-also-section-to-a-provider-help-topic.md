---
title: Hoe u een Zie ook sectie toevoegen aan een Help-onderwerp Provider | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848452"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Een gedeelte Zie ook toevoegen aan een Help-onderwerp over providers

In deze sectie wordt uitgelegd hoe u voor het vullen van de **Zie ook** gedeelte van een provider help-onderwerp.

De **Zie ook** sectie bestaat uit een lijst met onderwerpen die betrekking hebben op de provider of de gebruiker beter te begrijpen en gebruiken van de provider kan helpen. De lijst met onderwerpen help van de cmdlet, provider hulp kunt opnemen en conceptuele ('about'), help-onderwerpen in Windows PowerShell. Het kan ook betekenen verwijzingen naar boeken, document en online onderwerpen, waaronder een onlineversie van de huidige provider help-onderwerp.

Als u naar de online-onderwerpen verwijst, geeft u de URI of een zoekterm in tekst zonder opmaak. De `Get-Help` cmdlet niet koppelen of omleiden naar een van de onderwerpen in de lijst. Ook de `Online` parameter van de `Get-Help` cmdlet werkt niet met behulp van de provider.

De sectie Zie ook is gemaakt op basis van de `RelatedLinks` -element en de labels die deze bevat. De volgende XML-code laat zien hoe de labels toevoegen.

### <a name="to-add-see-also-topics"></a>'Zie ook' onderwerpen toevoegen

1. In de *AssemblyName*.dll-help.xml-bestand, vanuit de `providerHelp` element toevoegen een `RelatedLinks` element. De `RelatedLinks` element moet het laatste element in de `providerHelp` element. Slechts één `RelatedLinks` element is toegestaan in elke provider help-onderwerp.

   Bijvoorbeeld:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. Voor elk onderwerp in de **Zie ook** sectie, binnen de `RelatedLinks` element toevoegen een `navigationLink` element. Klik, vanuit elk `navigationLink` -element, Voeg een `linkText` -element en een `uri` element. Als u niet de `uri` -element, kunt u dit toevoegen als een leeg element (\<uri / >).

   Bijvoorbeeld:

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. Typ de naam van het onderwerp tussen de `linkText` tags. Als u een URI opgeeft, typt u het tussen de `uri` tags. Om aan te geven van de online versie van de help-onderwerp, van de huidige provider tussen de `linkText` tags, type "onlineversie: ' in plaats van de naam van het onderwerp. Normaal gesproken de "onlineversie: ' koppeling is het eerste onderwerp in de lijst Zie ook onderwerp.

   Het volgende voorbeeld zijn drie Zie ook onderwerpen. De eerste verwijzen naar de online versie van het huidige onderwerp. De tweede verwijst naar een Windows PowerShell-cmdlet help-onderwerp. De derde verwijst naar een andere online-onderwerp.

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```