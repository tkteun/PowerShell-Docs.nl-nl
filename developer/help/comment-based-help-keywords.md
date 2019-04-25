---
title: Help op basis van een opmerking trefwoorden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: af8a151070d26ffe236800076115c964f625e572
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083532"
---
# <a name="comment-based-help-keywords"></a>Trefwoorden voor Help op basis van opmerkingen

Dit onderwerp geeft een lijst van en beschrijft de trefwoorden in de help op basis van een opmerking.

## <a name="keywords-in-comment-based-help"></a>Trefwoorden in de Help op basis van een opmerking

Hieronder vindt u Help-informatie voor geldige op basis van een opmerking trefwoorden. Ze worden weergegeven in de volgorde waarin ze doorgaans worden weergegeven in een Help-onderwerp samen met het bedoelde gebruik. Deze trefwoorden kunnen worden weergegeven in een willekeurige volgorde in de Help op basis van een opmerking en ze zijn niet hoofdlettergevoelig.

Houd er rekening mee dat de `.ExternalHelp` sleutelwoord voorrang boven alle andere trefwoorden help op basis van een opmerking. Wanneer `.ExternalHelp` aanwezig is, de [Microsoft.PowerShell.Commands.Get-Help](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) cmdlet wordt niet weergegeven op basis van een opmerking Help-informatie, zelfs wanneer deze een help-bestand dat overeenkomt met de waarde van het trefwoord kan vinden.

`.Synopsis` Een korte beschrijving van de functie of het script. Dit trefwoord kan slechts één keer worden gebruikt in elk onderwerp.

`.Description` Een gedetailleerde beschrijving van de functie of het script. Dit trefwoord kan slechts één keer worden gebruikt in elk onderwerp.

`.Parameter` *\<Parameter-Name >* de beschrijving van een parameter. U kunt opnemen een `.Parameter` sleutelwoord voor elke parameter in de functie of het script.

De `.Parameter` trefwoorden kunnen worden weergegeven in een willekeurige volgorde in het Opmerkingenblok, maar de volgorde waarin de parameters worden weergegeven in de `Param` instructie of functie declaratie bepaalt de volgorde waarin de parameters worden weergegeven in de Help-onderwerp. U wijzigt de volgorde van de parameters in het Help-onderwerp, wijzigt de volgorde van de parameters in de `Param` instructie of functie declaratie.

U kunt ook een beschrijving van de parameter opgeven door een opmerking in het `Param` instructie direct vóór de naam van de parameter-variabele. Als u zowel een `Param` instructie opmerking en een `.Parameter` #trefwoord, de beschrijving die zijn gekoppeld aan de `.Parameter` trefwoord wordt gebruikt, en de `Param` instructie opmerking wordt genegeerd.

`.Example` Een voorbeeldopdracht die gebruikmaakt van de functie of het script, eventueel gevolgd door een voorbeeld van uitvoer en een beschrijving in. Herhaal dit trefwoord voor elk voorbeeld.

`.Inputs` De typen Microsoft .NET Framework-objecten die kan worden doorgesluisd naar de functie of het script. U kunt ook een beschrijving van de invoer-objecten bevatten.

`.Outputs` Het .NET Framework-type van de objecten die de cmdlet retourneert. U kunt ook een beschrijving van de geretourneerde objecten bevatten.

`.Notes` Meer informatie over de functie of het script.

`.Link` De naam van een gerelateerd onderwerp. Herhaal dit trefwoord voor elke verwant onderwerp. Deze inhoud wordt weergegeven in de sectie Verwante koppelingen van het Help-onderwerp.

De `.Link` sleutelwoord inhoud kan ook bestaan uit een URI Uniform Resource Identifier () naar een onlineversie van de dezelfde Help-onderwerp. De online versie geopend wanneer u de `Online` parameter van Get-Help. De URI moet beginnen met 'http' of 'https'.

`.Component` De technologie of functie die gebruikmaakt van de functie of het script of waaraan deze is gekoppeld. Deze inhoud wordt weergegeven wanneer de opdracht Get-Help bevat de `Component` parameter van Get-Help.

`.Role` De gebruikersrol van het Help-onderwerp. Deze inhoud wordt weergegeven wanneer de opdracht Get-Help bevat de `Role` parameter van Get-Help.

`.Functionality` Het beoogde gebruik van de functie. Deze inhoud wordt weergegeven wanneer de opdracht Get-Help bevat de `Functionality` parameter van Get-Help.

`.ForwardHelpTargetName` `<Command-Name>` Omleidingen naar het Help-onderwerp voor de opgegeven opdracht. U kunt gebruikers omleiden naar een Help-onderwerp, met inbegrip van Help-onderwerpen voor een functie, het script, de cmdlet of de provider.

`.ForwardHelpCategory` `<Category>` Hiermee geeft u de categorie hulp van het item in ForwardHelpTargetName. Geldige waarden zijn Alias, Cmdlet, Help-bestand, functie, Provider, algemeen, veelgestelde vragen over, woordenlijst, ScriptCommand, ExternalScript, Filter of alle. Gebruik dit trefwoord om conflicten te voorkomen wanneer er opdrachten met dezelfde naam.

`.RemoteHelpRunspace` `<PSSession-variable>` Hiermee geeft u een sessie met het Help-onderwerp. Voer een variabele met een PSSession. Dit sleutelwoord wordt gebruikt door de `Export-PSSession` cmdlet voor het vinden van de Help-onderwerpen voor de uitgevoerde opdrachten.

`.ExternalHelp` `<XML Help File>` Hiermee geeft u het pad en/of de naam van een Help-informatie op basis van een XML-bestand voor het script of functie.

De `.ExternalHelp` sleutelwoord vertelt de [Microsoft.PowerShell.Commands.Get-Help](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) cmdlet voor hulp bij het script of functie in een XML-bestand. De **. ExternalHelp** sleutelwoord is vereist bij het gebruik van een help op basis van een XML-bestand voor een script of functie. Zonder dit `Get-Help` wordt een help-bestand voor de functie of het script niet vinden.

De `.ExternalHelp` sleutelwoord voorrang boven alle andere trefwoorden help op basis van een opmerking. Wanneer `.ExternalHelp` aanwezig is, de [Microsoft.PowerShell.Commands.Get-Help](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) cmdlet wordt niet weergegeven op basis van een opmerking Help-informatie, zelfs wanneer deze een help-bestand dat overeenkomt met de waarde van het trefwoord kan vinden.

Wanneer de functie wordt geëxporteerd met een scriptmodule, de waarde van `.ExternalHelp` moet een bestandsnaam zonder een pad. `Get-Help` zoekt naar het bestand in een submap van de taalinstelling van de modulemap. Er zijn geen vereisten voor de bestandsnaam, maar een best practice is het gebruik van de volgende bestandsindeling: naam: `<ScriptModule>.psm1-help.xml`.

Wanneer de functie niet gekoppeld aan een module is, neemt u een pad en de naam in de waarde van de **. ExternalHelp** trefwoord. Als het opgegeven pad naar het XML-bestand UI-cultuur-specifieke submappen bevat, `Get-Help` zoekt naar de submappen recursief voor een XML-bestand met de naam van het script of functie in overeenstemming met de terugval standaarden tot stand gebracht voor taal Windows, net zoals doet voor alle XML gebaseerde Help-onderwerpen.

Zie voor meer informatie over de cmdlet Help op basis van een Help-XML-bestandsindeling [schrijven Windows PowerShell-Cmdlet Help](./writing-help-for-windows-powershell-cmdlets.md).