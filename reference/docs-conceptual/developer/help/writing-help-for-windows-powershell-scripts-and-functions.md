---
ms.date: 09/13/2016
ms.topic: reference
title: Hulp voor het schrijven van Power shell-scripts en-functies
description: Hulp voor het schrijven van Power shell-scripts en-functies
ms.openlocfilehash: f72742e2a131f41ba8ffdcec4901c7c3ea1da1ad
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654644"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>Hulp voor het schrijven van Power shell-scripts en-functies

Power shell-scripts en-functies moeten volledig worden gedocumenteerd wanneer ze met anderen worden gedeeld.
De `Get-Help` cmdlet geeft de Help-onderwerpen script en functie weer in dezelfde indeling als de Help voor cmdlets wordt weer gegeven. alle `Get-Help` para meters werken in de Help-onderwerpen over scripts en functies.

Power shell-scripts kunnen een Help-onderwerp bevatten over het script en Help-onderwerpen over de functies in het script. Functies die onafhankelijk van scripts worden gedeeld, kunnen hun eigen Help-onderwerpen bevatten.

In dit document worden de indeling en de juiste plaatsing van de Help-onderwerpen uitgelegd en worden richt lijnen voor de inhoud voorgesteld.

## <a name="types-of-script-and-function-help"></a>Typen script en functie Help

### <a name="comment-based-help"></a>Help bij Comment-Based

Het Help-onderwerp waarin een script of functie wordt beschreven, kan worden geïmplementeerd als een set opmerkingen binnen het script of de functie. Wanneer u op opmerkingen gebaseerde Help voor een script en voor functies in een script schrijft, moet u zorgvuldig letten op de regels voor het plaatsen van de op opmerkingen gebaseerde Help. De plaatsing bepaalt of de `Get-Help` cmdlet het Help-onderwerp koppelt aan het script of een functie. Zie [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)voor meer informatie over het schrijven van Help-onderwerpen over opmerkingen.

### <a name="xml-based-command-help"></a>Help bij XML-Based-opdracht

Het Help-onderwerp waarin een script of functie wordt beschreven, kan worden geïmplementeerd in een XML-bestand dat gebruikmaakt van het opdracht Help-schema. Als u het script of de functie wilt koppelen aan het XML-bestand, gebruikt u het `ExternalHelp` sleutel woord opmerking, gevolgd door het pad en de naam van het XML-bestand.

Wanneer het `ExternalHelp` tref woord opmerking aanwezig is, heeft dit een hogere prioriteit dan de Help op basis van opmerkingen, zelfs wanneer `Get-Help` er geen Help-bestand wordt gevonden dat overeenkomt met de waarde van het `ExternalHelp` sleutel woord.

### <a name="online-help"></a>Online-Help

U kunt de Help-onderwerpen op Internet plaatsen en vervolgens rechtstreeks `Get-Help` naar de onderwerpen openen. Zie [ondersteuning voor online-Help](../module/supporting-online-help.md)voor meer informatie over het schrijven van Help-onderwerpen over opmerkingen.

Er is geen vastgelegde methode voor het schrijven van conceptuele (' about ') onderwerpen voor scripts en functies.
U kunt de onderwerpen en de bijbehorende Url's echter op de Internet lijst plaatsen in het gedeelte Verwante koppelingen van een opdracht Help-onderwerp.

## <a name="content-considerations-for-script-and-function-help"></a>Inhouds overwegingen voor Help van script en functie

- Als u een zeer korte Help-onderwerp schrijft met slechts enkele van de beschik bare Help-secties van de opdracht, moet u ervoor zorgen dat u duidelijke beschrijvingen van de script-of function-para meters opneemt. Neem ook een of twee voorbeeld opdrachten op in de sectie voor beelden, zelfs als u besluit om voorbeeld beschrijvingen weg te laten.

- In alle beschrijvingen, raadpleegt u de opdracht als een script of functie. Deze informatie helpt de gebruiker om de opdracht te begrijpen en te beheren.

  Met de volgende gedetailleerde beschrijving wordt bijvoorbeeld aangegeven dat de New-Topic opdracht een script is.
  Dit herinnert gebruikers dat ze het pad en de volledige naam moeten opgeven wanneer ze dit uitvoeren.

  > "Het New-Topic script maakt een leeg conceptueel onderwerp voor elke onderwerpnaam in het invoer bestand..."

  In de volgende gedetailleerde beschrijving staat `Disable-PSRemoting` een functie. Deze informatie is vooral nuttig voor gebruikers wanneer de sessie meerdere opdrachten met dezelfde naam bevat, waarvan sommige worden verborgen met een opdracht met een hogere prioriteit.

  > `Disable-PSRemoting`Met de functie worden alle sessie configuraties uitgeschakeld op de lokale computer...

- In een Help-onderwerp in een script wordt uitgelegd hoe u het script als geheel kunt gebruiken. Als u de Help-onderwerpen over functies in het script ook schrijft, noteert u de functies in het Help-onderwerp van het script en neemt u verwijzingen op naar de Help-onderwerpen over functies in het gedeelte Verwante koppelingen van het Help-onderwerp van het script.
  Als een functie daarentegen deel uitmaakt van een script, wordt in het Help-onderwerp van de functie uitgelegd dat de functie in het script wordt afgespeeld en hoe deze onafhankelijk kan worden gebruikt. Vervolgens wordt het Help-onderwerp van het script weer geven in het gedeelte Verwante koppelingen van het Help-onderwerp van de functie.

- Bij het schrijven van voor beelden voor een Help-onderwerp in een script moet u het pad naar het script bestand in de voor beeld-opdracht toevoegen. Dit herinnert gebruikers dat ze het pad expliciet moeten opgeven, zelfs wanneer het script zich in de huidige map bevindt.

- In het Help-onderwerp van een functie herinnert u gebruikers dat de functie alleen bestaat in de huidige sessie en om deze te gebruiken in andere sessies, ze moeten deze toevoegen of een Power shell-profiel toevoegen.

- `Get-Help` Hiermee wordt het Help-onderwerp voor een script of functie alleen weer gegeven wanneer het script bestand en Help-onderwerp bestanden worden opgeslagen op de juiste locaties. Daarom is het niet handig instructies voor het installeren van Power shell op te geven, of het script of de functie in een Help-onderwerp in een script of functie op te slaan of te installeren. Neem in plaats daarvan installatie-instructies op in het document dat u gebruikt om het script of de functie te distribueren.

## <a name="see-also"></a>Zie ook

[Help-onderwerpen op basis van opmerkingen schrijven](./writing-comment-based-help-topics.md)
