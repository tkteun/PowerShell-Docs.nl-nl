---
title: Ondersteunende Online Help | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848151"
---
# <a name="supporting-online-help"></a>Ondersteunende online help

Vanaf Windows PowerShell 3.0, er zijn twee manieren voor de ondersteuning van de `Get-Help` Online-functie voor Windows PowerShell-opdrachten. In dit onderwerp wordt uitgelegd hoe u deze functie voor verschillende opdrachttypen implementeren.

## <a name="about-online-help"></a>Informatie over Online Help

Online-help is altijd een essentieel onderdeel van Windows PowerShell. Hoewel de `Get-Help` cmdlet geeft help-onderwerpen bij de opdrachtprompt, die veel gebruikers de voorkeur geeft aan de ervaring voor het lezen van online, met inbegrip van kleurcodering, hyperlinks en delen ideeën in Community-inhoud en documenten op basis van een wiki. Voordat u de opkomst van bij te werken Help opgegeven online-help belangrijker nog, de meest recente versie van de help-bestanden.

Met de komst van bij te werken Help in Windows PowerShell 3.0, in online-help nog steeds een belangrijke rol speelt. Naast de flexibele gebruikerservaring biedt online-help help voor gebruikers die niet of niet bij te werken Help voor het downloaden van help-onderwerpen gebruiken.

## <a name="how-get-help--online-works"></a>Hoe Get-Help-Online werkt

Om u te helpen bij het zoeken van de online help-onderwerpen voor opdrachten de `Get-Help` opdracht heeft een Online-parameter die de online versie van help-onderwerp voor een opdracht in de standaardinternetbrowser van de gebruiker wordt geopend.

Bijvoorbeeld, de volgende opdracht wordt geopend met de online help-onderwerp voor de `Invoke-Command` cmdlet.

```powershell
Get-Help Invoke-Command -Online
```

Voor het implementeren van `Get-Help` -Online, de `Get-Help` cmdlet ziet er uit voor een Uniform Resource Identifier (URI) voor de versie van de online help-onderwerp in de volgende locaties.

- De eerste koppeling in de sectie Verwante koppelingen van het help-onderwerp voor de opdracht. Het help-onderwerp moet worden geïnstalleerd op de computer van de gebruiker. Deze functie is geïntroduceerd in Windows PowerShell 2.0.

- De eigenschap HelpUri van een opdracht. De eigenschap HelpUri is toegankelijk is, zelfs wanneer het help-onderwerp voor de opdracht is niet geïnstalleerd op de computer van de gebruiker. Deze functie is geïntroduceerd in Windows PowerShell 3.0.

  `Get-Help` zoekt naar een URI zijn die in de eerste vermelding in het gedeelte Verwante koppelingen alvorens de waarde van de eigenschap HelpUri. Als de eigenschapswaarde onjuist is of is gewijzigd, kunt u deze overschrijven door te voeren van een andere waarde in de eerste gerelateerde koppeling. De eerste gerelateerde koppeling werkt echter alleen wanneer de help-onderwerpen op de computer van de gebruiker zijn geïnstalleerd.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Een URI toe te voegen aan de eerste gerelateerde koppeling van een opdracht help-onderwerp

U kunt ondersteunen `Get-Help` -Online voor elke opdracht door een geldige URI toe te voegen aan het eerste item in de sectie Verwante koppelingen van het help-onderwerp op basis van XML voor de opdracht. Deze optie is alleen geldig in de help-onderwerpen op basis van XML en werkt alleen als het help-onderwerp is geïnstalleerd op de computer van de gebruiker. Wanneer het help-onderwerp is geïnstalleerd en de URI is gevuld, deze waarde heeft voorrang op de **HelpUri** eigenschap van de opdracht. Zie voor meer informatie over het help-onderwerpen op basis van XML voor opdrachten [Writing XML-Based Help-onderwerpen voor opdrachten](../help/writing-xml-based-help-topics-for-commands.md).

Ter ondersteuning van deze functie, moet de URI worden weergegeven de `maml:uri` element onder de eerste `maml:relatedLinks/maml:navigationLink` -element in de `maml:relatedLinks` element.

Het volgende XML-bestand ziet u de juiste plaatsing van de URI. De ' onlineversie: "tekst in de `maml:linkText` element is een aanbevolen procedure, maar dit is niet vereist.

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>De eigenschap HelpUri aan een opdracht toe te voegen

Deze sectie wordt beschreven hoe u de eigenschap HelpUri toevoegen aan de opdrachten van verschillende typen.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Een eigenschap HelpUri toe te voegen aan een Cmdlet

Voor cmdlets die zijn geschreven in C#, Voeg een **HelpUri** kenmerk aan de Cmdlet-klasse. De waarde van het kenmerk moet een URI die met 'http' of 'https begint'.

De volgende code toont het kenmerk HelpUri van de `Get-History` cmdlet-klasse.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Een eigenschap HelpUri toe te voegen aan een geavanceerde functie

Voor geavanceerde functies, voegt u toe een **HelpUri** eigenschap in op de **CmdletBinding** kenmerk. De waarde van de eigenschap moet een URI die met 'http' of 'https begint'.

De volgende code toont het kenmerk HelpUri van de functie New-agenda

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Een kenmerk HelpUri toe te voegen aan een CIM-opdracht

Voor de CIM-opdrachten, voegt u toe een **HelpUri** kenmerk aan de **CmdletMetadata** element in het bestand CDXML. De waarde van het kenmerk moet een URI die met 'http' of 'https begint'.

De volgende code toont het kenmerk HelpUri van de begin-Debug CIM-opdracht

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Een kenmerk HelpUri toe te voegen aan een werkstroom

Voor werkstromen die zijn geschreven in de Windows PowerShell-taal, voegt u toe een **. ExternalHelp** Opmerking-richtlijn voor de werkstroomcode. De waarde van de richtlijn moet een URI die met 'http' of 'https begint'.

> [!NOTE]
> De eigenschap HelpUri wordt niet ondersteund voor werkstromen op basis van XAML in Windows PowerShell.

De volgende code toont de. ExternalHelp richtlijn in een werkstroombestand.

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```