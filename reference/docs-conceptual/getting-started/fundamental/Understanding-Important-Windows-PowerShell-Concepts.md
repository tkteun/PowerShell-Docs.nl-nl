---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Informatie over belangrijke Windows PowerShell-concepten
ms.assetid: 3e601e38-4520-4578-a48d-b6779f1d35ee
ms.openlocfilehash: 07ceaa2f3e6a192c6281cb4c99aed4c3f66afc7e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951083"
---
# <a name="understanding-important-windows-powershell-concepts"></a>Informatie over belangrijke Windows PowerShell-concepten
Het ontwerp van de Windows PowerShell integreert concepten van veel verschillende omgevingen. Meerdere personen met ervaring in specifieke houders of programmeeromgevingen bekend zijn, maar heel weinig mensen weten over deze. Sommige van deze concepten kijken bevat een handig overzicht van de shell.

### <a name="commands-are-not-text-based"></a>Opdrachten zijn niet op basis van tekst
In tegenstelling tot traditionele opdrachtregelinterface opdrachten, Windows PowerShell-cmdlets zijn ontworpen om te gaan met objecten - gestructureerde gegevens die meer dan gewoon een verzonnen reeks tekens op het scherm wordt weergegeven. Er zijn voor de opdrachtuitvoer altijd langs extra informatie die u gebruiken kunt als u deze nodig hebt. In dit onderwerp in de diepte in dit document wordt besproken.

Als u hulpprogramma's voor tekst-de verwerking opdrachtregelprogramma om gegevens te verwerken in het verleden hebt gebruikt, zult u merken dat ze zich anders gedragen als u probeert te gebruiken in Windows PowerShell. In de meeste gevallen moet u geen tekst-de verwerking hulpprogramma's om specifieke informatie te extraheren. Delen van de gegevens kunt u openen via standaard Windows PowerShell-object manipulatie opdrachten.

### <a name="the-command-family-is-extensible"></a>De opdracht-familie kan worden uitgebreid
Interfaces zoals Cmd.exe beschikken niet over een manier om u de ingebouwde opdrachtenset rechtstreeks kunt uitbreiden. Kunt u externe opdrachtregelprogramma's die worden uitgevoerd in Cmd.exe, maar deze externe hulpprogramma's hebben geen services, zoals Help-integratie en Cmd.exe niet automatisch weet dat ze de geldige opdrachten zijn.

De systeemeigen binary-opdrachten in Windows PowerShell, ook wel *cmdlets* (uitgesproken opdracht-kunt), kunnen worden uitgebreid door die u maakt en u met modules toevoegen aan Windows PowerShell-cmdlets. Windows PowerShell *-modules* worden gecompileerd, net als binaire hulpprogramma's in een andere interface. U kunt deze Windows PowerShell-providers toevoegen aan de shell, evenals de nieuwe cmdlets gebruiken.

Vanwege de speciale aard van de interne Windows PowerShell-opdrachten, wordt verwezen als *cmdlets*.

> [!NOTE]
> Windows PowerShell kunt opdrachten dan cmdlets uitvoeren. We zullen niet worden bespreken ze toegelicht in de Windows PowerShell User's Guide, maar ze zijn handig om te weten over als categorieën van de opdrachttypen. Windows PowerShell biedt ondersteuning voor scripts die zijn vergelijkbaar met UNIX-shell-scripts en Cmd.exe batch-bestanden, maar een .ps1-bestandsnaamextensie hebben. Windows PowerShell kunt u interne functies die kunnen worden gebruikt in de interface rechtstreeks, hetzij in scripts maken.

### <a name="windows-powershell-handles-console-input-and-display"></a>Windows PowerShell-ingangen Console-invoer en weergeven
Wanneer u een opdracht typt, verwerkt Windows PowerShell altijd de opdrachtregel invoer rechtstreeks. Windows PowerShell ook de opmaak van de uitvoer die u op het scherm te zien. Dit is van belang omdat deze het werk dat nodig van elke cmdlet vermindert en zorgt ervoor dat u kunt altijd dingen doen dezelfde manier ongeacht welke cmdlet die u gebruikt. Een voorbeeld van hoe dit vereenvoudigt de levenscyclus voor hulpprogramma voor ontwikkelaars en gebruikers is Help voor de opdrachtregel.

Traditionele opdrachtregelprogramma's hebben hun eigen schema's voor het aanvragen en Help-informatie weergeven. Bepaalde opdrachtregelprogramma's gebruiken **/?** voor het activeren van het Help-scherm; anderen gebruiken **-?**, **/H**, of zelfs **//**. Sommige wordt Help niet weergeven in een GUI-venster, in plaats van de consoleweergave. Sommige complexe programma's, zoals toepassing updaters, uitpakken interne bestanden voordat hun Help wordt weergegeven. Als u de onjuiste parameter gebruikt, kan het hulpprogramma wat u hebt getypt en begint automatisch uitvoeren van een taak negeren.

Wanneer u een opdracht in Windows PowerShell invoert, is alles wat u automatisch geparseerd en vooraf worden verwerkt door Windows PowerShell. Als u de **-?** parameter met een Windows PowerShell-cmdlet altijd betekent 'me Help weergeven voor deze opdracht'. Cmdlet ontwikkelaars hoeven niet te parseren van de opdracht. ze hoeft alleen te bieden de Help-tekst.

Het is belangrijk te weten dat het Help-functies van Windows PowerShell beschikbaar zijn, zelfs wanneer u traditionele opdrachtregelprogramma's in Windows PowerShell uitvoeren. Windows PowerShell de parameters en worden de resultaten naar de externe hulpprogramma's.

> [!NOTE]
> Als u een grafische toepassing in Windows PowerShell uitvoert, wordt het venster voor de toepassing wordt geopend. Windows PowerShell is opgetreden alleen wanneer verwerking van de opdrachtregel invoer u levering of de toepassing-uitvoer geretourneerd naar het consolevenster; Dit heeft geen invloed op hoe de toepassing intern werkt.

### <a name="windows-powershell-uses-some-c-syntax"></a>Sommige C#-syntaxis wordt gebruikt door Windows PowerShell
Windows PowerShell bevat van de syntaxisfuncties en sleutelwoorden die vergelijkbaar met die worden gebruikt in de C# zijn-programmeertaal, omdat Windows PowerShell is gebaseerd op .NET Framework. Van Windows PowerShell maakt het eenvoudiger voor meer informatie over C#, als u geïnteresseerd in de taal bent.

Als u niet een C#-programmeurs, is deze overeenkomst niet belangrijk. Echter, als u al bekend met C# bent, de overeenkomsten kunnen maken van Windows PowerShell veel gemakkelijker.