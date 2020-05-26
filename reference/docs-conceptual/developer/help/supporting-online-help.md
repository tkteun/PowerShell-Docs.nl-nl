---
title: Ondersteuning voor online-Help | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: de25b099e61f82891daff87c4c73bb8cad9111a4
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810125"
---
# <a name="supporting-online-help"></a>Ondersteunende online help

Vanaf Windows Power Shell 3,0 zijn er twee manieren om de `Get-Help` online functie voor Windows Power shell-opdrachten te ondersteunen. In dit onderwerp wordt uitgelegd hoe u deze functie implementeert voor verschillende opdracht typen.

## <a name="about-online-help"></a>Online-Help

Online-Help is altijd een essentieel onderdeel van Windows Power shell. Hoewel `Get-Help` met de cmdlet Help-onderwerpen worden weer gegeven bij de opdracht prompt, hebben veel gebruikers de voor keur aan het online lezen, met inbegrip van kleur codering, hyper links en het delen van ideeën in Community-inhoud en documenten op basis van wiki. In de online Help werd de meest recente versie van de Help-bestanden het belangrijkst, vóór de komst van de Help-informatie die kan worden bijgewerkt.

Met de komst van de bijwerk bare Help in Windows Power Shell 3,0 speelt de online Help nog steeds een belang rijke rol af. Naast de flexibele gebruikers ervaring biedt de online Help hulp bij gebruikers die geen Bewerk bare Help kunnen gebruiken om Help-onderwerpen te downloaden.

## <a name="how-get-help--online-works"></a>Help-online werken

Om gebruikers te helpen de online-Help-onderwerpen voor-opdrachten te vinden, `Get-Help` heeft de opdracht een online-para meter waarmee de online versie van het Help-onderwerp voor een opdracht in de standaard browser van de gebruiker wordt geopend.

Met de volgende opdracht wordt bijvoorbeeld het online-Help-onderwerp voor de `Invoke-Command` cmdlet geopend.

```powershell
Get-Help Invoke-Command -Online
```

Om `Get-Help` -online te implementeren, `Get-Help` zoekt de cmdlet naar een Uniform Resource Identifier (URI) voor het Help-onderwerp online versie op de volgende locaties.

- De eerste koppeling in het gedeelte Verwante koppelingen van het Help-onderwerp voor de opdracht. Het Help-onderwerp moet worden geïnstalleerd op de computer van de gebruiker. Deze functie is geïntroduceerd in Windows Power Shell 2,0.

- De eigenschap HelpUri van een wille keurige opdracht. De eigenschap HelpUri is toegankelijk, zelfs wanneer het Help-onderwerp voor de opdracht niet is geïnstalleerd op de computer van de gebruiker. Deze functie is geïntroduceerd in Windows Power Shell 3,0.

  `Get-Help`zoekt naar een URI in de eerste vermelding in de sectie verwante koppelingen voordat u de waarde van de eigenschap HelpUri ophaalt. Als de waarde van de eigenschap onjuist is of is gewijzigd, kunt u deze overschrijven door een andere waarde in te voeren in de eerste gerelateerde koppeling. De eerste gerelateerde koppeling werkt echter alleen als de Help-onderwerpen zijn geïnstalleerd op de computer van de gebruiker.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Een URI toevoegen aan de eerste gerelateerde koppeling van een Help-onderwerp van een opdracht

U kunt `Get-Help` online een wille keurige opdracht ondersteunen door een geldige URI toe te voegen aan de eerste vermelding in de sectie verwante koppelingen van het Help-onderwerp op basis van XML voor de opdracht. Deze optie is alleen geldig in Help-onderwerpen op basis van XML en werkt alleen wanneer het Help-onderwerp op de computer van de gebruiker is geïnstalleerd. Wanneer het Help-onderwerp is geïnstalleerd en de URI is gevuld, heeft deze waarde voor rang op de eigenschap **HelpUri** van de opdracht.

Ter ondersteuning van deze functie moet de URI worden weer gegeven in het- `maml:uri` element onder het eerste `maml:relatedLinks/maml:navigationLink` element in het- `maml:relatedLinks` element.

In het volgende XML-bestand wordt de juiste plaatsing van de URI weer gegeven. De tekst ' Online version: ' in het `maml:linkText` element is een Best Practice, maar dit is niet vereist.

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>https://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>De eigenschap HelpUri toevoegen aan een opdracht

In deze sectie wordt uitgelegd hoe u de eigenschap HelpUri kunt toevoegen aan opdrachten van verschillende typen.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Een HelpUri-eigenschap toevoegen aan een cmdlet

Voor cmdlets die zijn geschreven in C#, voegt u een **HelpUri** -kenmerk toe aan de klasse cmdlet. De waarde van het kenmerk moet een URI zijn die begint met http of https.

Met de volgende code wordt het kenmerk HelpUri van de `Get-History` klasse cmdlet weer gegeven.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "https://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Een eigenschap HelpUri toevoegen aan een geavanceerde functie

Voor geavanceerde functies voegt u een eigenschap **HelpUri** toe aan het kenmerk **CmdletBinding** . De waarde van de eigenschap moet een URI zijn die begint met http of https.

De volgende code toont het kenmerk HelpUri van de functie New-Calendar

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="https://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Een HelpUri-kenmerk toevoegen aan een CIM-opdracht

Voor CIM-opdrachten voegt u een **HelpUri** -kenmerk toe aan het **CmdletMetadata** -element in het CDXML-bestand. De waarde van het kenmerk moet een URI zijn die begint met http of https.

De volgende code toont het kenmerk HelpUri van de CIM-opdracht start-debug

```
<CmdletMetadata Verb="Debug" HelpUri="https://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Een HelpUri-kenmerk toevoegen aan een werk stroom

Voor werk stromen die in de Windows Power shell-taal zijn geschreven, voegt u een toe **. ExternalHelp** van de opmerkings richtlijn naar de werk stroom code. De waarde van de instructie moet een URI zijn die begint met http of https.

> [!NOTE]
> De eigenschap HelpUri wordt niet ondersteund voor op XAML gebaseerde werk stromen in Windows Power shell.

De volgende code toont de. ExternalHelp-instructie in een werk stroom bestand.

```powershell
# .ExternalHelp "https://go.microsoft.com/fwlink/?LinkID=138338"
```
