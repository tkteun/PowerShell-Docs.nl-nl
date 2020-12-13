---
ms.date: 09/12/2016
ms.topic: reference
title: Een gedeelte Zie ook toevoegen aan een Help-onderwerp over providers
description: Een gedeelte Zie ook toevoegen aan een Help-onderwerp over providers
ms.openlocfilehash: df0b14ba84e04baf404081944ef62ef6745d74b2
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667654"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Een gedeelte Zie ook toevoegen aan een Help-onderwerp over providers

In deze sectie wordt uitgelegd hoe u de sectie **Zie ook** in het Help-onderwerp van een provider vult.

De sectie **Zie ook** bestaat uit een lijst met onderwerpen die betrekking hebben op de provider of waarmee de gebruiker de provider beter kan begrijpen en gebruiken. De lijst met onderwerpen kan Help-onderwerpen over de cmdlet Help, de Help van de provider en conceptuele informatie ("about") bevatten in Windows Power shell. Het kan ook verwijzingen bevatten naar boeken, papier en online onderwerpen, met inbegrip van een online versie van het Help-onderwerp van de huidige provider.

Wanneer u verwijst naar online-onderwerpen, geeft u de URI of een zoek term op in tekst zonder opmaak. De `Get-Help` cmdlet wordt niet gekoppeld of omgeleid naar een van de onderwerpen in de lijst. De `Online` para meter van de `Get-Help` cmdlet werkt ook niet met de Help van de provider.

De sectie **Zie ook** wordt gemaakt van het `RelatedLinks` element en de labels die het bevat.
In het volgende XML-bestand ziet u hoe u de tags kunt toevoegen.

### <a name="to-add-see-also-topics"></a>Zie ook onderwerpen om toe te voegen

1. Voeg in het `<AssemblyName>.dll-help.xml` bestand, binnen het `providerHelp` element, een- `RelatedLinks` element toe. Het `RelatedLinks` element moet het laatste element in het- `providerHelp` element zijn. Er is slechts één `RelatedLinks` element toegestaan in elk Help-onderwerp van de provider.

   Bijvoorbeeld:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

1. Voor elk onderwerp in de sectie **Zie ook** , binnen het `RelatedLinks` element, voegt u een- `navigationLink` element toe. Voeg vervolgens binnen elk `navigationLink` element één `linkText` element en één element toe `uri` . Als u het element niet gebruikt `uri` , kunt u dit als een leeg element () toevoegen \<uri/> .

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

1. Typ de naam van het onderwerp tussen de `linkText` Tags. Als u een URI opgeeft, typt u deze tussen de `uri` Tags. Als u de online versie van het Help-onderwerp van de huidige provider wilt aangeven tussen de `linkText` Tags, typt u ' online versie: ' in plaats van de naam van het onderwerp. Normaal gesp roken is de koppeling ' online versie: ' het eerste onderwerp in de lijst Zie ook topics.

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
                <uri>https://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```
