---
title: Schrijfhulp voor PowerShell-Scripts en -functies | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: 98a3f61ff4fa2367f69357173d4e8e14288ff429
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847843"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>Schrijfhulp voor PowerShell-Scripts en functies

PowerShell-scripts en functies moeten worden volledig gedocumenteerd wanneer ze worden gedeeld met anderen.
De `Get-Help` cmdlet geeft de help-onderwerpen van het script en de functie weer in dezelfde indeling als de help voor cmdlets en alle worden weergegeven de `Get-Help` parameters werken op script en de functie help-onderwerpen.

PowerShell-scripts kunnen opnemen een help-onderwerp over het script en help-onderwerpen over alle functies in het script.
Functies die worden gedeeld onafhankelijk van scripts kunnen hun eigen help-onderwerpen bevatten.

Dit document wordt uitgelegd voor de indeling en de juiste plaatsing van de help-onderwerpen en er wordt verwezen naar richtlijnen voor de inhoud.

## <a name="types-of-script-and-function-help"></a>Typen van Script en de functie Help

### <a name="comment-based-help"></a>Help op basis van een opmerking
Het help-onderwerp waarin wordt beschreven van een script of functie kan worden geïmplementeerd als een set van opmerkingen in het script of functie.
Bij het schrijven van help voor een script en functies op basis van een opmerking in een script, betaalt u zorgvuldige aandacht aan de regels voor het plaatsen van de help op basis van een opmerking.
De plaatsing wordt bepaald of de `Get-Help` cmdlet het helponderwerp wordt gekoppeld aan het script of een functie.
Zie voor meer informatie over het schrijven van help-onderwerpen op basis van een opmerking [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

### <a name="xml-based-command-help"></a>Help bij op basis van een XML-opdracht
Het help-onderwerp waarin wordt beschreven van een script of functie kan worden geïmplementeerd in een XML-bestand die gebruikmaakt van de opdracht help-schema.
Als u wilt koppelen aan het script of functie het XML-bestand, gebruik de `ExternalHelp` Opmerking trefwoord gevolgd door het pad en de naam van het XML-bestand.

Wanneer de `ExternalHelp` sleutelwoord aanwezig is, heeft deze prioriteit boven help op basis van een opmerking opmerking, zelfs wanneer `Get-Help` niet vinden een help-bestand dat overeenkomt met de waarde van de `ExternalHelp` trefwoord.

### <a name="online-help"></a>Online-Help
U kunt de help-onderwerpen op het Internet te plaatsen en vervolgens direct `Get-Help` te openen in de onderwerpen.
Zie voor meer informatie over het schrijven van help-onderwerpen op basis van een opmerking [ondersteunende Online Help](../module/supporting-online-help.md).

Er is geen tot stand gebrachte methode voor schrijven conceptuele ('About'),-onderwerpen voor scripts en functies.
Echter, u kunt boeken conceptuele onderwerpen in de lijst met Internet de onderwerpen en de URL's in de sectie Verwante koppelingen van een opdracht help-onderwerp.

## <a name="content-considerations-for-script-and-function-help"></a>Help-inhoud overwegingen voor het Script en de functie

- Als u een zeer korte help-onderwerp met slechts enkele van de secties van de Help-informatie beschikbaar opdracht schrijft, zorg er dan voor dat zijn duidelijk beschrijvingen van de parameters-script of functie. Ook één of twee Voorbeeldopdrachten bevatten in de sectie voorbeelden, zelfs als u besluit voorbeeld beschrijvingen weglaten.

- In alle beschrijvingen, verwijzen naar de opdracht als een script of functie. Deze informatie helpt de gebruiker om te begrijpen en beheren van de opdracht.

  Bijvoorbeeld, geeft de volgende gedetailleerde beschrijving aan dat de opdracht New-onderwerp een script. Deze herinnering gebruikers die ze nodig hebben om op te geven van het pad en de volledige naam wanneer ze het uitvoert.

  > 'Het script New-onderwerp maakt een lege conceptueel onderwerp voor de naam van elk onderwerp in het invoerbestand...'

  De volgende uitvoerige beschrijving vermeld dat `Disable-PSRemoting` is een functie. Deze informatie is met name handig voor gebruikers wanneer de sessie meerdere opdrachten met dezelfde naam bevat, waarvan sommige mogelijk worden verborgen door een opdracht met een hogere prioriteit.

  > De `Disable-PSRemoting` functie alle sessieconfiguraties op de lokale computer wordt uitgeschakeld...

- In een script help-onderwerp wordt uitgelegd hoe u het script te gebruiken als geheel. Als u ook help-onderwerpen voor functies in het script schrijft, vermeld de functies in uw script help-onderwerp en bevatten verwijzingen naar de functie help-onderwerpen in de sectie Verwante koppelingen van het script help-onderwerp. Daarentegen als een functie onderdeel van een script is, wordt uitgelegd in de functie help-onderwerp de rol die de functie speelt in het script en hoe deze onafhankelijk van elkaar kan worden gebruikt. Vervolgens een lijst voor het script help-onderwerp in de sectie Verwante koppelingen van de functie help-onderwerp.

- Bij het schrijven van voorbeelden voor een script help-onderwerp, moet u het pad naar het scriptbestand in het voorbeeld opnemen. Deze herinnering gebruikers dat ze het pad expliciet, geeft moeten zelfs wanneer het script in de huidige map is.

- In een functie help-onderwerp Herinner de gebruikers die de functie alleen aanwezig is in de huidige sessie en, als u wilt gebruiken in andere sessies, moeten ze toe te voegen of deze een PowerShell-profiel toevoegen.

- `Get-Help` Geeft de help-onderwerp voor een script of functie alleen wanneer het scriptbestand en help-Onderwerpbestanden worden opgeslagen in de juiste locaties. Het is daarom niet nuttig om instructies voor het installeren van PowerShell, of opslaan of installeren van het script of functie in een script of functie help-onderwerp. In plaats daarvan de installatie-instructies in het document dat u gebruikt voor het distribueren van het script of functie opnemen.

## <a name="see-also"></a>Zie ook

 [Schrijven van Help-onderwerpen op basis van XML voor Scripts en functies](./writing-xml-based-help-topics-for-scripts-and-functions.md)

 [Schrijven van Help-onderwerpen op basis van XML voor opdrachten](./writing-xml-based-help-topics-for-commands.md)

 [Schrijven van Help-onderwerpen op basis van een opmerking](./writing-comment-based-help-topics.md)
