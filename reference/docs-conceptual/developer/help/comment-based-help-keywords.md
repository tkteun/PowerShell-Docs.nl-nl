---
ms.date: 06/09/2020
ms.topic: reference
title: Trefwoorden voor Help op basis van opmerkingen
description: Trefwoorden voor Help op basis van opmerkingen
ms.openlocfilehash: d87dde8700813767f6c09cfce70ed06c7964ebc7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645466"
---
# <a name="comment-based-help-keywords"></a>Trefwoorden voor Help op basis van opmerkingen

In dit onderwerp worden de tref woorden in Help op basis van opmerkingen vermeld en beschreven.

## <a name="keywords-in-comment-based-help"></a>Tref woorden in Comment-Based Help

Hieronder vindt u geldige Help-tref woorden op basis van opmerkingen. Ze worden weer gegeven in de volg orde waarin ze doorgaans worden weer gegeven in een Help-onderwerp samen met het beoogde gebruik. Deze tref woorden kunnen in een wille keurige volg orde in de op opmerkingen gebaseerde Help worden weer gegeven en zijn niet hoofdletter gevoelig.

Houd er rekening mee dat het `.EXTERNALHELP` sleutel woord voor rang krijgt op alle andere op opmerkingen gebaseerde Help-tref woorden.
Wanneer `.EXTERNALHELP` aanwezig is, wordt in de cmdlet [micro soft. Power shell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) geen Help op basis van opmerkingen weer gegeven, zelfs wanneer er geen Help-bestand wordt gevonden dat overeenkomt met de waarde van het sleutel woord.

## <a name="synopsis"></a>. SAMEN VATTING

Een korte beschrijving van de functie of het script. Dit sleutel woord kan slechts eenmaal in elk onderwerp worden gebruikt.

## <a name="description"></a>. BESCHRIJVINGEN

Een gedetailleerde beschrijving van de functie of het script. Dit sleutel woord kan slechts eenmaal in elk onderwerp worden gebruikt.

## <a name="parameter-parameter-name"></a>. BEPAALDE \<Parameter-Name>

De beschrijving van een para meter. U kunt een `.PARAMETER` tref woord voor elke para meter toevoegen in de functie of het script.

De `.PARAMETER` tref woorden kunnen in een wille keurige volg orde in het blok met opmerkingen worden weer gegeven, maar de volg orde waarin de para meters worden weer gegeven in de declaratie van de `Param` instructie of functie, bepaalt de volg orde waarin de para meters in het Help-onderwerp Als u de volg orde van de para meters in het Help-onderwerp wilt wijzigen, wijzigt u de volg orde van de para meters in de `Param` declaratie instructie of functie.

U kunt ook een beschrijving van een para meter opgeven door een opmerking in de `Param` instructie direct vóór de naam van de parameter variabele in te stellen. Als u zowel een `Param` Opmerking Als een `.PARAMETER` tref woord gebruikt, wordt de beschrijving die is gekoppeld aan het `.PARAMETER` tref woord gebruikt en wordt de opmerking voor de `Param` instructie genegeerd.

## <a name="example"></a>. Hierbij

Een voor beeld van een opdracht die gebruikmaakt van de functie of het script, eventueel gevolgd door voorbeeld uitvoer en een beschrijving. Herhaal dit tref woord voor elk voor beeld.

## <a name="inputs"></a>. INVOER

De Microsoft .NET Framework typen objecten die kunnen worden gesluisd met de functie of het script. U kunt ook een beschrijving van de invoer objecten toevoegen.

## <a name="outputs"></a>. UITVOER

Het .NET Framework type van de objecten die door de cmdlet worden geretourneerd. U kunt ook een beschrijving van de geretourneerde objecten toevoegen.

## <a name="notes"></a>. NOTEN

Aanvullende informatie over de functie of het script.

## <a name="link"></a>. GEKOPPELD

De naam van een verwant onderwerp. Herhaal dit tref woord voor elk verwant onderwerp. Deze inhoud wordt weer gegeven in de sectie verwante koppelingen van het Help-onderwerp.

De `.LINK` inhoud van het sleutel woord kan ook een URI (Uniform Resource Identifier) bevatten naar een online versie van hetzelfde Help-onderwerp. De online versie wordt geopend wanneer u de `Online` para meter van gebruikt `Get-Help` . De URI moet beginnen met http of https.

## <a name="component"></a>. ONDERDEEL

De naam van de technologie of functie die de functie of het script gebruikt of waaraan deze is gerelateerd.
De **onderdeel** parameter van `Get-Help` gebruikt deze waarde om de zoek resultaten te filteren die worden geretourneerd door `Get-Help` .

## <a name="role"></a>. Rolvak

De naam van de gebruikersrol voor het Help-onderwerp. De para meter **Role** van `Get-Help` gebruikt deze waarde om de zoek resultaten te filteren die worden geretourneerd door `Get-Help` .

## <a name="functionality"></a>. VOORZIENING

De tref woorden die het beoogde gebruik van de functie beschrijven. De **functie** parameter van `Get-Help` gebruikt deze waarde om de zoek resultaten te filteren die worden geretourneerd door `Get-Help` .

## <a name="forwardhelptargetname-command-name"></a>. FORWARDHELPTARGETNAME \<Command-Name>

Omleiding naar het Help-onderwerp voor de opgegeven opdracht. U kunt gebruikers omleiden naar een Help-onderwerp, inclusief Help-onderwerpen voor een functie, script, cmdlet of provider.

## <a name="forwardhelpcategory-category"></a>. FORWARDHELPCATEGORY \<Category>

Hiermee geeft u de Help-categorie van het item in op `.FORWARDHELPTARGETNAME` . Gebruik dit tref woord om conflicten te voor komen wanneer er opdrachten met dezelfde naam zijn.

Geldige waarden zijn:

- Alias
- Cmdlet
- File
- Functie
- Provider
- Algemeen
- Veelgestelde vragen
- Woordenlijst
- ScriptCommand
- ExternalScript
- Filter
- Alles

## <a name="remotehelprunspace-pssession-variable"></a>. REMOTEHELPRUNSPACE \<PSSession-variable>

Hiermee geeft u een sessie die het Help-onderwerp bevat. Voer een variabele in die een PSSession bevat. Dit sleutel woord wordt door de `Export-PSSession` cmdlet gebruikt om de Help-onderwerpen voor de geëxporteerde opdrachten te vinden.

## <a name="externalhelp-xml-help-file"></a>. EXTERNALHELP \<XML Help File>

Hiermee geeft u het pad en/of de naam op van een XML-Help-bestand voor het script of de functie.

Het `.EXTERNALHELP` sleutel woord vertelt de cmdlet [micro soft. Power shell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) om hulp te krijgen voor het script of de functie in een XML-bestand. Het `.EXTERNALHELP` sleutel woord is vereist wanneer u een XML-Help-bestand gebruikt voor een script of functie. Geen Help- `Get-Help` bestand voor de functie of het script wordt niet gevonden.

Het `.EXTERNALHELP` tref woord heeft voor rang op alle andere op opmerkingen gebaseerde Help-tref woorden. Wanneer `.EXTERNALHELP` aanwezig is, wordt in de cmdlet [micro soft. Power shell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) geen Help op basis van opmerkingen weer gegeven, zelfs wanneer er geen Help-bestand wordt gevonden dat overeenkomt met de waarde van het sleutel woord.

Wanneer de functie wordt geëxporteerd door een script module, moet de waarde van `.EXTERNALHELP` een bestands naam zonder pad zijn. `Get-Help` zoekt naar het bestand in een landspecifieke submap van de module directory. Er zijn geen vereisten voor de bestands naam, maar een best practice is het gebruik van de volgende bestands indeling: `<ScriptModule>.psm1-help.xml` .

Als de functie niet is gekoppeld aan een module, neemt u een pad en een bestands naam op in de waarde van het `.EXTERNALHELP` sleutel woord. Als het opgegeven pad naar het XML-bestand de submappen met de gebruikers interface-cultuur bevat, `Get-Help` doorzoekt de submappen recursief voor een XML-bestand met de naam van het script of de functie in overeenstemming met de taal vereisten die voor Windows zijn vastgesteld, net zoals voor alle Help-onderwerpen over XML.

Zie de [Help van Windows Power shell-cmdlets schrijven](./writing-help-for-windows-powershell-cmdlets.md)voor meer informatie over de XML-indeling van de Help-functie voor cmdlets.
