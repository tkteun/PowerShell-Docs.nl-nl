---
title: Hulp voor het schrijven van Power shell-scripts en-functies | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: af989fb2eeba6b68f2e3e6506f3f60d5be6f7d8a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357804"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>Hulp voor het schrijven van Power shell-scripts en-functies

Power shell-scripts en-functies moeten volledig worden gedocumenteerd wanneer ze met anderen worden gedeeld.
Met de cmdlet `Get-Help` worden de script-en functie Help-onderwerpen weer gegeven in dezelfde indeling als de Help voor cmdlets wordt weer gegeven. alle para meters van `Get-Help` werken met de Help-onderwerpen over scripts en functies.

Power shell-scripts kunnen een Help-onderwerp bevatten over het script en Help-onderwerpen over de functies in het script.
Functies die onafhankelijk van scripts worden gedeeld, kunnen hun eigen Help-onderwerpen bevatten.

In dit document worden de indeling en de juiste plaatsing van de Help-onderwerpen uitgelegd en worden richt lijnen voor de inhoud voorgesteld.

## <a name="types-of-script-and-function-help"></a>Typen script en functie Help

### <a name="comment-based-help"></a>Help op basis van opmerkingen
Het Help-onderwerp waarin een script of functie wordt beschreven, kan worden geïmplementeerd als een set opmerkingen binnen het script of de functie.
Wanneer u op opmerkingen gebaseerde Help voor een script en voor functies in een script schrijft, moet u zorgvuldig letten op de regels voor het plaatsen van de op opmerkingen gebaseerde Help.
De plaatsing bepaalt of de `Get-Help`-cmdlet het Help-onderwerp koppelt aan het script of een functie.
Zie [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)voor meer informatie over het schrijven van Help-onderwerpen over opmerkingen.

### <a name="xml-based-command-help"></a>Help voor op XML gebaseerde opdracht
Het Help-onderwerp waarin een script of functie wordt beschreven, kan worden geïmplementeerd in een XML-bestand dat gebruikmaakt van het opdracht Help-schema.
Als u het script of de functie wilt koppelen aan het XML-bestand, gebruikt u het sleutel woord `ExternalHelp` opmerking, gevolgd door het pad en de naam van het XML-bestand.

Wanneer het tref woord `ExternalHelp` opmerking aanwezig is, heeft het een hogere prioriteit dan een op opmerkingen gebaseerde Help, zelfs wanneer `Get-Help` geen Help-bestand kunt vinden dat overeenkomt met de waarde van het sleutel `ExternalHelp`.

### <a name="online-help"></a>Online-Help
U kunt de Help-onderwerpen op Internet plaatsen en vervolgens direct `Get-Help` om de onderwerpen te openen.
Zie [ondersteuning voor online-Help](../module/supporting-online-help.md)voor meer informatie over het schrijven van Help-onderwerpen over opmerkingen.

Er is geen vastgelegde methode voor het schrijven van conceptuele (' about ') onderwerpen voor scripts en functies.
U kunt de onderwerpen en de bijbehorende Url's echter op de Internet lijst plaatsen in het gedeelte Verwante koppelingen van een opdracht Help-onderwerp.

## <a name="content-considerations-for-script-and-function-help"></a>Inhouds overwegingen voor Help van script en functie

- Als u een zeer korte Help-onderwerp schrijft met slechts enkele van de beschik bare Help-secties van de opdracht, moet u ervoor zorgen dat u duidelijke beschrijvingen van de script-of function-para meters opneemt. Neem ook een of twee voorbeeld opdrachten op in de sectie voor beelden, zelfs als u besluit om voorbeeld beschrijvingen weg te laten.

- In alle beschrijvingen, raadpleegt u de opdracht als een script of functie. Deze informatie helpt de gebruiker om de opdracht te begrijpen en te beheren.

  Met de volgende gedetailleerde beschrijving wordt bijvoorbeeld aangegeven dat de opdracht New-Topic een script is. Dit herinnert gebruikers dat ze het pad en de volledige naam moeten opgeven wanneer ze dit uitvoeren.

  > "Met het script New-Topic maakt u een leeg conceptueel onderwerp voor elke onderwerpnaam in het invoer bestand..."

  In de volgende gedetailleerde beschrijving wordt aangegeven dat `Disable-PSRemoting` een functie is. Deze informatie is vooral nuttig voor gebruikers wanneer de sessie meerdere opdrachten met dezelfde naam bevat, waarvan sommige worden verborgen met een opdracht met een hogere prioriteit.

  > Met de functie `Disable-PSRemoting` worden alle sessie configuraties op de lokale computer uitgeschakeld...

- In een Help-onderwerp in een script wordt uitgelegd hoe u het script als geheel kunt gebruiken. Als u de Help-onderwerpen over functies in het script ook schrijft, noteert u de functies in het Help-onderwerp van het script en neemt u verwijzingen op naar de Help-onderwerpen over functies in het gedeelte Verwante koppelingen van het Help-onderwerp van het script. Als een functie daarentegen deel uitmaakt van een script, wordt in het Help-onderwerp van de functie uitgelegd dat de functie in het script wordt afgespeeld en hoe deze onafhankelijk kan worden gebruikt. Vervolgens wordt het Help-onderwerp van het script weer geven in het gedeelte Verwante koppelingen van het Help-onderwerp van de functie.

- Bij het schrijven van voor beelden voor een Help-onderwerp in een script moet u het pad naar het script bestand in de voor beeld-opdracht toevoegen. Dit herinnert gebruikers dat ze het pad expliciet moeten opgeven, zelfs wanneer het script zich in de huidige map bevindt.

- In het Help-onderwerp van een functie herinnert u gebruikers dat de functie alleen bestaat in de huidige sessie en om deze te gebruiken in andere sessies, ze moeten deze toevoegen of een Power shell-profiel toevoegen.

- `Get-Help` wordt het Help-onderwerp voor een script of functie alleen weer gegeven wanneer het script bestand en Help-onderwerp bestanden worden opgeslagen op de juiste locaties. Daarom is het niet handig instructies voor het installeren van Power shell op te geven, of het script of de functie in een Help-onderwerp in een script of functie op te slaan of te installeren. Neem in plaats daarvan installatie-instructies op in het document dat u gebruikt om het script of de functie te distribueren.

## <a name="see-also"></a>Zie ook

[Help-onderwerpen over opmerkingen schrijven](./writing-comment-based-help-topics.md)
