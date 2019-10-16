---
title: Een sectie ' Zie ook ' toevoegen aan het Help-onderwerp van een provider | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357867"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Een gedeelte Zie ook toevoegen aan een Help-onderwerp over providers

In deze sectie wordt uitgelegd hoe u de sectie **Zie ook** in het Help-onderwerp van een provider vult.

De sectie **Zie ook** bestaat uit een lijst met onderwerpen die betrekking hebben op de provider of waarmee de gebruiker de provider beter kan begrijpen en gebruiken. De lijst met onderwerpen kan Help-onderwerpen over de cmdlet Help, de Help van de provider en conceptuele informatie ("about") bevatten in Windows Power shell. Het kan ook verwijzingen bevatten naar boeken, papier en online onderwerpen, met inbegrip van een online versie van het Help-onderwerp van de huidige provider.

Wanneer u verwijst naar online-onderwerpen, geeft u de URI of een zoek term op in tekst zonder opmaak. De `Get-Help`-cmdlet wordt niet gekoppeld of omgeleid naar een van de onderwerpen in de lijst. Daarnaast werkt de `Online`-para meter van de cmdlet `Get-Help` niet met de Help van de provider.

De sectie Zie ook wordt gemaakt van het element `RelatedLinks` en de tags die het bevat. In het volgende XML-bestand ziet u hoe u de tags kunt toevoegen.

### <a name="to-add-see-also-topics"></a>Voor het toevoegen van ' Zie ook onderwerpen '

1. Voeg in het bestand *assemblyname*. dll-Help. XML binnen het element `providerHelp` een `RelatedLinks`-element toe. Het element `RelatedLinks` moet het laatste element zijn in het element `providerHelp`. Er is slechts één `RelatedLinks`-element toegestaan in elk Help-onderwerp van de provider.

   Bijvoorbeeld:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. Voor elk onderwerp in de sectie **Zie ook** , in het element `RelatedLinks`, voegt u een `navigationLink`-element toe. Voeg vervolgens binnen elk element `navigationLink` één element `linkText` en één element `uri` toe. Als u het element `uri` niet gebruikt, kunt u dit toevoegen als een leeg element (\<uri/>).

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

3. Typ de naam van het onderwerp tussen de Tags `linkText`. Als u een URI opgeeft, typt u deze tussen de Tags `uri`. Als u de online versie van het Help-onderwerp van de huidige provider wilt aangeven tussen de Tags `linkText`, typt u ' online versie: ' in plaats van de onderwerpnaam. Normaal gesp roken is de koppeling ' online versie: ' het eerste onderwerp in de lijst Zie ook topics.

   In het volgende voor beeld zijn drie Zie ook onderwerpen. De eerste keer naar de online versie van het huidige onderwerp. De tweede verwijst naar het Help-onderwerp van een Windows Power shell-cmdlet. De derde verwijst naar een ander online onderwerp.

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