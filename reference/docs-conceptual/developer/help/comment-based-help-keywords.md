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
ms.openlocfilehash: 534a6c9a43326c8a01b2181c7a799286fa4d3997
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353373"
---
# <a name="comment-based-help-keywords"></a>Trefwoorden voor Help op basis van opmerkingen

In dit onderwerp worden de tref woorden in Help op basis van opmerkingen vermeld en beschreven.

## <a name="keywords-in-comment-based-help"></a>Tref woorden in Help op basis van opmerkingen

Hieronder vindt u geldige Help-tref woorden op basis van opmerkingen. Ze worden weer gegeven in de volg orde waarin ze doorgaans worden weer gegeven in een Help-onderwerp samen met het beoogde gebruik. Deze tref woorden kunnen in een wille keurige volg orde in de op opmerkingen gebaseerde Help worden weer gegeven en zijn niet hoofdletter gevoelig.

Houd er rekening mee dat het sleutel woord @no__t 0 voor rang heeft boven alle andere Help-tref woorden op basis van opmerkingen. Als `.ExternalHelp` aanwezig is, wordt in de cmdlet [Microsoft. Power shell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) geen Help op basis van opmerkingen weer gegeven, zelfs wanneer er geen Help-bestand wordt gevonden dat overeenkomt met de waarde van het sleutel woord.

`.Synopsis` een korte beschrijving van de functie of het script. Dit sleutel woord kan slechts eenmaal in elk onderwerp worden gebruikt.

`.Description` een gedetailleerde beschrijving van de functie of het script. Dit sleutel woord kan slechts eenmaal in elk onderwerp worden gebruikt.

`.Parameter` *\<Parameter-naam >* de beschrijving van een para meter. U kunt een `.Parameter`-tref woord toevoegen voor elke para meter in de functie of het script.

De `.Parameter` tref woorden kunnen in een wille keurige volg orde in het blok met opmerkingen worden weer gegeven, maar de volg orde waarin de para meters worden weer gegeven in de instructie `Param` of de functie declaratie bepaalt de volg orde waarin de para meters in het Help-onderwerp worden weer gegeven. Als u de volg orde van de para meters in het Help-onderwerp wilt wijzigen, wijzigt u de volg orde van de para meters in de declaratie van de `Param`-instructie of functie.

U kunt ook een beschrijving van een para meter opgeven door een opmerking in de instructie `Param` direct vóór de naam van de parameter variabele in te stellen. Als u een opmerking met een `Param`-instructie en een `.Parameter`-tref woord gebruikt, wordt de beschrijving die is gekoppeld aan het sleutel woord `.Parameter` gebruikt en wordt de opmerking voor de `Param`-instructie genegeerd.

`.Example` een voorbeeld opdracht die gebruikmaakt van de functie of het script, eventueel gevolgd door voorbeeld uitvoer en een beschrijving. Herhaal dit tref woord voor elk voor beeld.

`.Inputs` de Microsoft .NET Framework typen objecten die kunnen worden gesluisd met de functie of het script. U kunt ook een beschrijving van de invoer objecten toevoegen.

`.Outputs` het .NET Framework type van de objecten die door de cmdlet worden geretourneerd. U kunt ook een beschrijving van de geretourneerde objecten toevoegen.

`.Notes` aanvullende informatie over de functie of het script.

`.Link` de naam van een verwant onderwerp. Herhaal dit tref woord voor elk verwant onderwerp. Deze inhoud wordt weer gegeven in de sectie verwante koppelingen van het Help-onderwerp.

De inhoud van het sleutel woord `.Link` kan ook een URI (Uniform Resource Identifier) bevatten naar een online versie van hetzelfde Help-onderwerp. De online versie wordt geopend wanneer u de para meter `Online` van Get-Help gebruikt. De URI moet beginnen met http of https.

`.Component` de technologie of functie die door de functie of het script wordt gebruikt, of waaraan deze is gerelateerd. Deze inhoud wordt weer gegeven wanneer de opdracht Get-Help de para meter `Component` bevat van Get-Help.

`.Role` de gebruikersrol voor het Help-onderwerp. Deze inhoud wordt weer gegeven wanneer de opdracht Get-Help de para meter `Role` bevat van Get-Help.

`.Functionality` het beoogde gebruik van de functie. Deze inhoud wordt weer gegeven wanneer de opdracht Get-Help de para meter `Functionality` bevat van Get-Help.

`.ForwardHelpTargetName` `<Command-Name>` omgeleid naar het Help-onderwerp voor de opgegeven opdracht. U kunt gebruikers omleiden naar een Help-onderwerp, inclusief Help-onderwerpen voor een functie, script, cmdlet of provider.

`.ForwardHelpCategory` `<Category>` geeft de Help-categorie van het item op in ForwardHelpTargetName. Geldige waarden zijn alias, cmdlet, Help file, functie, provider, algemeen, veelgestelde vragen, woorden lijst, ScriptCommand, ExternalScript, filter of alle. Gebruik dit tref woord om conflicten te voor komen wanneer er opdrachten met dezelfde naam zijn.

`.RemoteHelpRunspace` `<PSSession-variable>` geeft een sessie die het Help-onderwerp bevat. Voer een variabele in die een PSSession bevat. Dit sleutel woord wordt gebruikt door de cmdlet `Export-PSSession` om de Help-onderwerpen voor de geëxporteerde opdrachten te vinden.

`.ExternalHelp` `<XML Help File>` Hiermee geeft u het pad en/of de naam op van een XML-bestand met Help-informatie voor het script of de functie.

Het sleutel woord `.ExternalHelp` vertelt de cmdlet [micro soft. Power shell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) om hulp te krijgen voor het script of de functie in een XML-bestand. De **.** Het sleutel woord ExternalHelp is vereist wanneer u een XML-Help-bestand gebruikt voor een script of functie. Zonder deze optie kan `Get-Help` geen Help-bestand vinden voor de functie of het script.

Het sleutel woord @no__t 0 heeft voor rang op alle andere op opmerkingen gebaseerde Help-tref woorden. Als `.ExternalHelp` aanwezig is, wordt in de cmdlet [Microsoft. Power shell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) geen Help op basis van opmerkingen weer gegeven, zelfs wanneer er geen Help-bestand wordt gevonden dat overeenkomt met de waarde van het sleutel woord.

Wanneer de functie wordt geëxporteerd door een script module, moet de waarde van `.ExternalHelp` een bestands naam zonder pad zijn. `Get-Help` zoekt naar het bestand in een land instellingen-specifieke submap van de module directory. Er zijn geen vereisten voor de bestands naam, maar een best practice is het gebruik van de volgende bestands naam notatie: `<ScriptModule>.psm1-help.xml`.

Als de functie niet is gekoppeld aan een module, neemt u een pad en een bestands naam op in de waarde van **. ExternalHelp** sleutel woord. Als het opgegeven pad naar het XML-bestand de submappen met de gebruikers interface-cultuur bevat, `Get-Help` de submappen recursief doorzoeken voor een XML-bestand met de naam van het script of de functie in overeenstemming met de taal terugval standaarden die zijn vastgesteld voor Windows , net zoals voor alle Help-onderwerpen over XML.

Zie de [Help van Windows Power shell-cmdlets schrijven](./writing-help-for-windows-powershell-cmdlets.md)voor meer informatie over de XML-indeling van de Help-functie voor cmdlets.