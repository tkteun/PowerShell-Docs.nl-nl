---
title: Help-tref woorden op basis van opmerkingen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: 3c5736be7066a749744482cb79edad2f53705f07
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564108"
---
# <a name="comment-based-help-keywords"></a>Trefwoorden voor Help op basis van opmerkingen

In dit onderwerp worden de tref woorden in Help op basis van opmerkingen vermeld en beschreven.

## <a name="keywords-in-comment-based-help"></a>Tref woorden in Help op basis van opmerkingen

Hieronder vindt u geldige Help-tref woorden op basis van opmerkingen. Ze worden weer gegeven in de volg orde waarin ze doorgaans worden weer gegeven in een Help-onderwerp samen met het beoogde gebruik. Deze tref woorden kunnen in een wille keurige volg orde in de op opmerkingen gebaseerde Help worden weer gegeven en zijn niet hoofdletter gevoelig.

Houd er rekening mee dat het `.ExternalHelp` sleutel woord voor rang krijgt op alle andere op opmerkingen gebaseerde Help-tref woorden. Wanneer `.ExternalHelp` aanwezig is, wordt in de cmdlet [micro soft. Power shell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) geen Help op basis van opmerkingen weer gegeven, zelfs wanneer er geen Help-bestand wordt gevonden dat overeenkomt met de waarde van het sleutel woord.

`.Synopsis`Een korte beschrijving van de functie of het script. Dit sleutel woord kan slechts eenmaal in elk onderwerp worden gebruikt.

`.Description`Een gedetailleerde beschrijving van de functie of het script. Dit sleutel woord kan slechts eenmaal in elk onderwerp worden gebruikt.

`.Parameter`* \< Para meter-name>* de beschrijving van een para meter. U kunt een `.Parameter` tref woord voor elke para meter toevoegen in de functie of het script.

De `.Parameter` tref woorden kunnen in een wille keurige volg orde in het blok met opmerkingen worden weer gegeven, maar de volg orde waarin de para meters worden weer gegeven in de declaratie van de `Param` instructie of functie, bepaalt de volg orde waarin de para meters in het Help-onderwerp Als u de volg orde van de para meters in het Help-onderwerp wilt wijzigen, wijzigt u de volg orde van de para meters in de `Param` declaratie instructie of functie.

U kunt ook een beschrijving van een para meter opgeven door een opmerking in de `Param` instructie direct vóór de naam van de parameter variabele in te stellen. Als u zowel een `Param` Opmerking Als een `.Parameter` tref woord gebruikt, wordt de beschrijving die is gekoppeld aan het `.Parameter` tref woord gebruikt en wordt de opmerking voor de `Param` instructie genegeerd.

`.Example`Een voor beeld van een opdracht die gebruikmaakt van de functie of het script, eventueel gevolgd door voorbeeld uitvoer en een beschrijving. Herhaal dit tref woord voor elk voor beeld.

`.Inputs`De Microsoft .NET Framework typen objecten die kunnen worden gesluisd met de functie of het script. U kunt ook een beschrijving van de invoer objecten toevoegen.

`.Outputs`Het .NET Framework type van de objecten die door de cmdlet worden geretourneerd. U kunt ook een beschrijving van de geretourneerde objecten toevoegen.

`.Notes`Aanvullende informatie over de functie of het script.

`.Link`De naam van een verwant onderwerp. Herhaal dit tref woord voor elk verwant onderwerp. Deze inhoud wordt weer gegeven in de sectie verwante koppelingen van het Help-onderwerp.

De `.Link` inhoud van het sleutel woord kan ook een URI (Uniform Resource Identifier) bevatten naar een online versie van hetzelfde Help-onderwerp. De online versie wordt geopend wanneer u de `Online` para meter Get-Help gebruikt. De URI moet beginnen met http of https.

`.Component`De technologie of functie die de functie of het script gebruikt of waaraan deze is gerelateerd. Deze inhoud wordt weer gegeven wanneer de opdracht Get-Help de `Component` para meter van Get-Help bevat.

`.Role`De gebruikersrol voor het Help-onderwerp. Deze inhoud wordt weer gegeven wanneer de opdracht Get-Help de `Role` para meter van Get-Help bevat.

`.Functionality`Het beoogde gebruik van de functie. Deze inhoud wordt weer gegeven wanneer de opdracht Get-Help de `Functionality` para meter van Get-Help bevat.

`.ForwardHelpTargetName``<Command-Name>`Omleiding naar het Help-onderwerp voor de opgegeven opdracht. U kunt gebruikers omleiden naar een Help-onderwerp, inclusief Help-onderwerpen voor een functie, script, cmdlet of provider.

`.ForwardHelpCategory``<Category>`Hiermee geeft u de categorie Help op van het item in ForwardHelpTargetName. Geldige waarden zijn alias, cmdlet, Help file, functie, provider, algemeen, veelgestelde vragen, woorden lijst, ScriptCommand, ExternalScript, filter of alle. Gebruik dit tref woord om conflicten te voor komen wanneer er opdrachten met dezelfde naam zijn.

`.RemoteHelpRunspace``<PSSession-variable>`Hiermee geeft u een sessie die het Help-onderwerp bevat. Voer een variabele in die een PSSession bevat. Dit sleutel woord wordt door de `Export-PSSession` cmdlet gebruikt om de Help-onderwerpen voor de geëxporteerde opdrachten te vinden.

`.ExternalHelp``<XML Help File>`Hiermee geeft u het pad en/of de naam op van een XML-Help-bestand voor het script of de functie.

Het `.ExternalHelp` sleutel woord vertelt de cmdlet [micro soft. Power shell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) om hulp te krijgen voor het script of de functie in een XML-bestand. De **. **Het sleutel woord ExternalHelp is vereist wanneer u een XML-Help-bestand gebruikt voor een script of functie. Geen Help- `Get-Help` bestand voor de functie of het script wordt niet gevonden.

Het `.ExternalHelp` tref woord heeft voor rang op alle andere op opmerkingen gebaseerde Help-tref woorden. Wanneer `.ExternalHelp` aanwezig is, wordt in de cmdlet [micro soft. Power shell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) geen Help op basis van opmerkingen weer gegeven, zelfs wanneer er geen Help-bestand wordt gevonden dat overeenkomt met de waarde van het sleutel woord.

Wanneer de functie wordt geëxporteerd door een script module, moet de waarde van `.ExternalHelp` een bestands naam zonder pad zijn. `Get-Help`zoekt naar het bestand in een landspecifieke submap van de module directory. Er zijn geen vereisten voor de bestands naam, maar een best practice is het gebruik van de volgende indeling voor bestands namen: `<ScriptModule>.psm1-help.xml` .

Als de functie niet is gekoppeld aan een module, neemt u een pad en een bestands naam op in de waarde van **. ExternalHelp** sleutel woord. Als het opgegeven pad naar het XML-bestand de submappen met de gebruikers interface-cultuur bevat, `Get-Help` doorzoekt de submappen recursief voor een XML-bestand met de naam van het script of de functie in overeenstemming met de taal vereisten die voor Windows zijn vastgesteld, net zoals voor alle Help-onderwerpen over XML.

Zie de [Help van Windows Power shell-cmdlets schrijven](./writing-help-for-windows-powershell-cmdlets.md)voor meer informatie over de XML-indeling van de Help-functie voor cmdlets.
