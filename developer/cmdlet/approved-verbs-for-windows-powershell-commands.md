---
title: Goedgekeurde werkwoorden voor PowerShell-opdrachten | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- action names [PowerShell SDK]
- verb names [PowerShell SDK]
- cmdlets [PowerShell SDK], verb names
ms.assetid: 2d4e58a9-05bc-437c-86b9-d8d55cba7d48
caps.latest.revision: 36
ms.openlocfilehash: 4475b3f5e15826efbe8bab867011985cd7e2e1ae
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293347"
---
# <a name="approved-verbs-for-powershell-commands"></a>Goedgekeurde werkwoorden voor PowerShell-opdrachten

PowerShell wordt een paar werkwoord-zelfstandig naamwoord gebruikt voor de namen van cmdlets en hun afgeleide klassen van Microsoft .NET Framework.
Bijvoorbeeld, de `Get-Command` cmdlet geleverd door PowerShell wordt gebruikt om op te halen van alle opdrachten die zijn geregistreerd in PowerShell.
De bewerking deel van de naam identificeert de actie die de cmdlet uitvoert.
Het zelfstandig naamwoord deel van de naam van de identificeert de entiteit op waarmee de actie wordt uitgevoerd.

> [!NOTE]
> PowerShell wordt de term gebruikt *term* om te beschrijven van een woord dat houdt in een actie, zelfs als dat word niet een standaard term in het Engels is.
> Bijvoorbeeld, de term *nieuw* is een geldige naam van de PowerShell-opdracht, omdat een actie impliceert dat zelfs als het is niet een term in het Engels.

## <a name="verb-naming-rules"></a>Term naamgevingsregels

De volgende lijst bevat richtlijnen bij het kiezen van de term voor een cmdletnaam:

* Wanneer u de opdracht opgeeft, raden wij aan dat u een van de namen van de vooraf gedefinieerde term PowerShell (aliassen voor deze vooraf gedefinieerde bewerkingen zijn opgenomen in de volgende tabellen).
  Wanneer u een vooraf gedefinieerde term gebruikt, zorgen u voor consistentie tussen de cmdlets die u maakt, de cmdlets die worden geboden door PowerShell en de cmdlets die door anderen zijn ontworpen.

* De vooraf gedefinieerde bewerkingen gebruiken om te beschrijven van het algemene bereik van de actie en parameters gebruiken om de actie van de cmdlet verder te verfijnen.

* Als u wilt afdwingen van consistentie tussen cmdlets, moet u een synoniem van een goedgekeurd werkwoord niet gebruiken.

* Gebruik alleen de vorm van elke bewerking die wordt vermeld in dit onderwerp.
  Bijvoorbeeld: 'Get' te gebruiken, maar gebruik niet 'Ophalen' of 'Opgehaald'.

* Gebruik Pascal hoofdlettergebruik voor termen.
  In Pascal hoofdlettergebruik van de eerste letter van elk woord een hoofdletter is, zoals 'ForEach'.

* Gebruik niet de volgende gereserveerde woorden of aliassen.
  Deze termen worden gebruikt door de PowerShell-taal, of door een speciale case cmdlets die worden geleverd door PowerShell.
  - ForEach (foreach)
  - Indeling (f)
  - Groep (gp)
  - Sorteren (sr)
  - T (en)
  - Waar (wat)

## <a name="similar-verbs-for-different-actions"></a>Vergelijkbare bewerkingen voor verschillende acties

De volgende vergelijkbare bewerkingen staan voor verschillende acties.

### <a name="new-vs-set"></a>Nieuwe Visual Studio. Instellen
De `New` term wordt gebruikt om een nieuwe resource te maken.
De `Set` term wordt gebruikt voor het wijzigen van een bestaande resource, (optioneel) het maken van de resource als deze niet, zoals bestaat de `Set-Variable` cmdlet.

### <a name="find-vs-search"></a>Vs vinden. Search
De `Find` term wordt gebruikt om te zoeken voor een object.
De `Search` term wordt gebruikt om u te maken van een verwijzing naar een resource in een container.

### <a name="get-vs-read"></a>Vs ophalen. Lezen
De `Get` term wordt gebruikt voor het ophalen van een resource, zoals een bestand.
De `Read` term wordt gebruikt voor het ophalen van gegevens uit een bron, zoals een bestand.

### <a name="invoke-vs-start"></a>Visual Studio worden aangeroepen. Start
De `Invoke` term wordt gebruikt voor het uitvoeren van een bewerking die is doorgaans een synchrone bewerking, zoals het uitvoeren van een opdracht.
De `Start` term wordt gebruikt om te beginnen met een bewerking die is doorgaans een asynchrone bewerking, zoals het starten van een proces.

### <a name="ping-vs-test"></a>Ping vs. Test
Gebruik de `Test` term.

## <a name="common-verbs"></a>Algemene termen

Maakt gebruik van PowerShell het [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) opsommingsklasse voor het definiëren van algemene acties die kunnen worden toegepast op bijna elke cmdlet.
De volgende tabel bevat de meeste van de gedefinieerde bewerkingen.

|Term (alias)|Actie|Opmerkingen|
|--------------------|------------|--------------|
|[Voeg](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Een resource toegevoegd aan een container of een item is gekoppeld aan een ander item. Bijvoorbeeld, de `Add-Content` cmdlet inhoud toegevoegd aan een bestand. Deze term is gekoppeld aan `Remove`.|Voor deze actie niet gebruiken-termen, zoals toevoegen, toevoegen, samenvoegen of invoegen.|
|[Schakel](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|Hiermee verwijdert u alle resources uit een container, maar wordt de container niet verwijderd. Bijvoorbeeld, de `Clear-Content` cmdlet worden de inhoud van een bestand wordt verwijderd, maar wordt het bestand niet verwijderen.|Gebruik termen, zoals leegmaken, wissen, Release, markering verwijderen, uitschakelen of Nullify niet voor deze actie.|
|[Sluiten](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (cs)|Wijzigt de status van een resource gemakkelijk toegankelijk zijn, niet beschikbaar of onbruikbaar. Deze term is gekoppeld aan `Open.`||
|[Kopie](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (cp)|Een resource worden gekopieerd naar een andere naam of naar een andere container. Bijvoorbeeld, de `Copy-Item` cmdlet die wordt gebruikt voor toegang tot opgeslagen gegevens een item van de ene locatie in het gegevensarchief worden gekopieerd naar een andere locatie.|Gebruik termen, zoals dupliceren, kloon, replicatie of synchronisatie niet voor deze actie.|
|[Voer](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et)|Hiermee geeft u een actie waarmee de gebruiker om naar een resource te verplaatsen. Bijvoorbeeld, de `Enter-PSSession` cmdlet wordt de gebruiker in een interactieve sessie. Deze term is gekoppeld aan `Exit`.|Gebruik termen zoals Push of in niet voor deze actie.|
|[Afsluiten](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (ex)|De huidige omgeving of context wordt ingesteld op de meest recent gebruikte context. Bijvoorbeeld, de `Exit-PSSession` cmdlet wordt de gebruiker in de sessie die is gebruikt om de interactieve sessie te starten. Deze term is gekoppeld aan `Enter`.|Gebruik termen zoals Pop- of uitgeschaald niet voor deze actie.|
|[Zoek](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (fd)|Zoekt naar een object in een container die is onbekend, impliciet, optioneel of opgegeven.||
|[Indeling](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|Zorgt ervoor dat objecten in een opgegeven formulier of de lay-out.||
|[Ophalen](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Hiermee geeft u een actie die een resource opgehaald. Deze term is gekoppeld aan `Set`.|Gebruik termen, zoals lezen, Open, Cat, Type, Dir, verkrijgen, Dump, ophalen, controleren, zoeken of zoeken niet voor deze actie.|
|[Verbergen](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Maakt een resource kan niet worden getraceerd. Een cmdlet waarvan de naam de term verbergen bevat kan bijvoorbeeld een service verbergen van een gebruiker. Deze term is gekoppeld aan `Show`.|Gebruik een opdracht zoals blok niet voor deze actie.|
|[Deelnemen aan](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Combineert de resources in één resource. Bijvoorbeeld, de `Join-Path` cmdlet combineert een pad met een van de onderliggende paden te maken van een enkel pad. Deze term is gekoppeld aan `Split`.|Gebruik termen, zoals combineren, Unite, verbinding maken of koppelen niet voor deze actie.|
|[Lock](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (lk)|Beveiliging van een resource. Deze term is gekoppeld aan `Unlock`.|Gebruik termen zoals beperken of Secure niet voor deze actie.|
|[Verplaats](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (min.)|Een resource verplaatst van de ene locatie naar een andere. Bijvoorbeeld, de `Move-Item` cmdlet wordt een item verplaatst van de ene locatie in het gegevensarchief naar een andere locatie.|Gebruik termen, zoals de overdracht, naam of migreren niet voor deze actie.|
|[Nieuwe](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Hiermee maakt u een resource. (De `Set` term kan ook worden gebruikt bij het maken van een resource die bevat gegevens, zoals de `Set-Variable` cmdlet.)|Gebruik termen, zoals Create, genereren, Build, maken of toewijzen niet voor deze actie.|
|[Open](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (op)|Wijzigt de status van een resource gemakkelijk toegankelijk is, beschikbaar of bruikbaar. Deze term is gekoppeld aan `Close`.||
|[Optimaliseren](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (Operations Manager)|Vergroot de effectiviteit van een resource.||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|Hiermee verwijdert u een item vanaf de bovenkant van een stapel. Bijvoorbeeld, de `Pop-Location` cmdlet wijzigt, wordt de huidige locatie naar de locatie die het meest recent is gepusht naar de stack.||
|[Push-](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (pu)|Een item wordt toegevoegd aan de bovenkant van een stapel. Bijvoorbeeld, de `Push-Location` cmdlet worden de huidige locatie in de stack.||
|[Opnieuw](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (re)|Hiermee stelt een resource op de status van ongedaan is gemaakt.||
|[Verwijder](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Een resource verwijdert uit een container. Bijvoorbeeld, de `Remove-Variable` cmdlet Hiermee verwijdert u een variabele en de waarde ervan. Deze term is gekoppeld aan `Add`.|Voor deze actie niet gebruiken woorden die als, knippen, verwijderen, verwijderen, of wissen.|
|[Wijzig de naam van](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (rn)|Wijzigt de naam van een resource. Bijvoorbeeld, de `Rename-Item` cmdlet, die wordt gebruikt voor toegang tot opgeslagen gegevens, wijzigt u de naam van een item in het gegevensarchief.|Gebruik een woord, zoals de wijziging niet voor deze actie.|
|[Opnieuw instellen van](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (rs)|Hiermee stelt u een resource terug naar de oorspronkelijke staat.||
|[Search](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (sr)|Hiermee maakt een verwijzing naar een resource in een container.|Gebruik termen, zoals zoeken of zoeken niet voor deze actie.|
|[Selecteer](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (sc)|Zoekt naar een resource in een container. Bijvoorbeeld, de `Select-String` cmdlet tekst wordt gevonden in tekenreeksen en bestanden.|Gebruik termen, zoals zoeken of zoeken niet voor deze actie.|
|[Stel](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|Vervangt de gegevens op een bestaande resource of maakt u een resource die enkele gegevens bevat. Bijvoorbeeld, de `Set-Date` cmdlet de systeemtijd op de lokale computer worden gewijzigd. (De `New` term kan ook worden gebruikt om een resource te maken.) Deze term is gekoppeld aan `Get`.|Gebruik termen, zoals schrijven, opnieuw instellen, toewijzen of configureren niet voor deze actie.|
|[Weergeven](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (v)|Hiermee maakt een resource zichtbaar voor de gebruiker. Deze term is gekoppeld aan `Hide`.|Gebruik termen, zoals weergegeven of produceren niet voor deze actie.|
|[Overslaan](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (sk)|Een of meer resources of punten in een reeks omzeilt.|Gebruik een opdracht zoals overslaan of Jump niet voor deze actie.|
|[Gesplitste](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (lineair)|Onderdelen van een resource zijn gescheiden. Bijvoorbeeld, de `Split-Path` cmdlet retourneert verschillende onderdelen van een pad. Deze term is gekoppeld aan `Join`.|Voor deze actie gebruik niet een term die afzonderlijke.|
|[Stap](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (st)|Hiermee gaat u naar het volgende punt of de resource in een reeks.||
|[Switch](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (sw)|Hiermee geeft u een actie die tussen de twee resources, zoals alternatieven te wisselen tussen twee locaties, verantwoordelijkheden of Staten.||
|[Ongedaan maken](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (VN)|Hiermee stelt u een bron naar de oorspronkelijke staat.||
|[Ontgrendelen](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (VK)|Versies van een resource die is vergrendeld. Deze term is gekoppeld aan `Lock`.|Gebruik termen, zoals de Release, Unrestrict of onbeveiligd niet voor deze actie.|
|[Bekijk](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (wc)|Voortdurend inspecteert of een resource op wijzigingen gecontroleerd.||

## <a name="communications-verbs"></a>Communicatie-termen

Maakt gebruik van PowerShell het [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) klasse voor het definiëren van acties die van toepassing op communicatie zijn.
De volgende tabel bevat de meeste van de gedefinieerde bewerkingen.

|Term (alias)|Actie|Opmerkingen|
|--------------------|------------|--------------|
|[Verbinding maken met](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (cc)|Hiermee maakt u een koppeling tussen een bron en bestemming. Deze term is gekoppeld aan `Disconnect`.|Gebruik termen, zoals Join- of Telnet niet voor deze actie.|
|[Verbinding verbreken](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (dc)|De koppeling tussen een bron- en een verbroken. Deze term is gekoppeld aan `Connect`.|Gebruik termen, zoals Break of afmelden niet voor deze actie.|
|[Lezen](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (extern bureaublad)|Gegevens uit een bron verkrijgt. Deze term is gekoppeld aan `Write`.|Voor deze actie niet gebruiken bewerkingen zoals ophalen, vragen of ophalen.|
|[Ontvangen](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (rc)|Informatie verzonden van een bron accepteert. Deze term is gekoppeld aan `Send`.|Voor deze actie niet-termen, zoals lezen, accepteren, gebruiken en bekijken.|
|[Verzenden](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (sd)|Biedt informatie naar een bestemming. Deze term is gekoppeld aan `Receive`.|Gebruik termen, zoals opslag, uitzenden, e-Mail of Fax niet voor deze actie.|
|[Schrijven](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (wr)|Gegevens worden toegevoegd aan een doel. Deze term is gekoppeld aan `Read`.|Gebruik termen, zoals opslag of afdrukken niet voor deze actie.|

## <a name="data-verbs"></a>Data Verbs

Maakt gebruik van PowerShell het [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData) klasse voor het definiëren van acties die betrekking hebben op de verwerking van gegevens.
De volgende tabel bevat de meeste van de gedefinieerde bewerkingen.

|Naam van de bewerking (alias)|Actie|Opmerkingen|
|-------------------------|------------|--------------|
|[Back-up](/dotnet/api/System.Management.Automation.VerbsData.Backup) (ba)|Gegevens worden opgeslagen door deze te repliceren.|Gebruik termen zoals opslaan, branden, replicatie of synchronisatie niet voor deze actie.|
|[Controlepunt](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (ch)|Hiermee maakt u een momentopname van de huidige status van de gegevens of de configuratie ervan.|Voor deze actie, een werkwoord zoals Diff. niet gebruiken|
|[Vergelijk](/dotnet/api/System.Management.Automation.VerbsData.Compare) (cr)|Evalueert de gegevens van één resource ten opzichte van de gegevens uit een andere resource.|Voor deze actie, een werkwoord zoals Diff. niet gebruiken|
|[Comprimeren](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|Comprimeert de gegevens van een resource. Paren met `Expand`.|Voor deze actie, moet u niet een term gebruiken, zoals cd.|
|[Converteren](/dotnet/api/System.Management.Automation.VerbsData.Convert) (cv)|De gegevens van de ene weergave gewijzigd naar een andere wanneer de cmdlet in twee richtingen conversie ondersteunt of wanneer de cmdlet conversie tussen meerdere gegevenstypen ondersteunt.|Voor deze actie niet gebruiken van termen zoals wijzigen, grootte is gewijzigd, of gegevens.|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (cf)|Een primaire type invoer (de cmdlet-zelfstandig naamwoord geeft aan dat de invoer) converteert naar een of meer ondersteunde uitvoertypen.|Gebruik termen, zoals exporteren, uitvoer of Out niet voor deze actie.|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (ct)|Converteert van een of meer soorten invoer voor een primaire uitvoertype (de cmdlet-zelfstandig naamwoord geeft het uitvoertype).|Voor deze actie gebruik geen werkwoorden zoals importeren, invoer, of In.|
|[Ontkoppelen](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (dm)|Hiermee wordt een named entity vanaf een locatie losgekoppeld. Deze term is gekoppeld aan `Mount`.|Gebruik termen zoals ontkoppelen of ontkoppelen niet voor deze actie.|
|[Bewerken](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|Hiermee wijzigt u bestaande gegevens toevoegen of verwijderen van inhoud.|Gebruik termen, zoals wijzigen, bijwerken of wijzigen niet voor deze actie.|
|[Vouw](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|De gegevens van een resource die is gecomprimeerd herstellen naar de oorspronkelijke staat. Deze term is gekoppeld aan `Compress`.|Gebruik termen zoals exploderen of decomprimeren niet voor deze actie.|
|[Exporteren](/dotnet/api/System.Management.Automation.VerbsData.Export) (ep)|De primaire invoer in een permanent gegevensarchief, zoals een bestand of in een indeling voor berichtenuitwisseling ingekapseld. Deze term is gekoppeld aan `Import`.|Gebruik termen, zoals uitpakken of back-up niet voor deze actie.|
|[Groep](/dotnet/api/System.Management.Automation.VerbsData.Group) (gp)|Zorgt ervoor dat of wordt gekoppeld aan een of meer resources.|Voor deze actie niet gebruiken van termen, zoals aggregatie, rangschikken, koppelen of correleren.|
|[Importeren](/dotnet/api/System.Management.Automation.VerbsData.Import) (ip)|Maakt een resource van de gegevens die zijn opgeslagen in een permanent gegevensarchief (zoals een bestand) of in een indeling voor berichtenuitwisseling. Bijvoorbeeld, de `Import-CSV` cmdlet importeert gegevens uit een bestand met door komma's gescheiden waarden (CSV) voor objecten die kunnen worden gebruikt door andere cmdlets. Deze term is gekoppeld aan `Export`.|Gebruik termen zoals BulkLoad of Load niet voor deze actie.|
|[Initialiseren](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|Bereidt van een resource voor gebruik en ingesteld op een standaardstatus.|Gebruik termen, zoals wissen, Init, vernieuwen, opnieuw maken, opnieuw worden geïnitialiseerd of Setup niet voor deze actie.|
|[Limiet](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Beperkingen geldt voor een resource.|Gebruik een opdracht zoals quotum niet voor deze actie.|
|[Merge](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|Maakt een enkele bron van meerdere resources.|Gebruik termen, zoals combineren of Join niet voor deze actie.|
|[Koppelen](/dotnet/api/System.Management.Automation.VerbsData.Mount) (mt)|Hiermee wordt een named entity gekoppeld naar een locatie. Deze term is gekoppeld aan `Dismount`.|Gebruik de opdracht Connect niet voor deze actie.|
|[Uit](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Verzendt gegevens buiten de omgeving. Bijvoorbeeld, de `Out-Printer` cmdlet verzendt gegevens naar een printer.||
|[Publiceren](/dotnet/api/System.Management.Automation.VerbsData.Publish) (pb)|Maakt een resource beschikbaar voor anderen. Deze term is gekoppeld aan `Unpublish`.|Voor deze actie niet-termen, zoals implementeren, Release, gebruiken of installeren.|
|[Herstellen](/dotnet/api/System.Management.Automation.VerbsData.Restore) (rr)|Hiermee stelt u een resource aan een vooraf gedefinieerde status, zoals een instellen door status `Checkpoint`. Bijvoorbeeld, de `Restore-Computer` cmdlet wordt een systeem herstellen gestart op de lokale computer.|Gebruik termen, zoals herstel, Return, ongedaan maken of oplossing niet voor deze actie.|
|[Sla](/dotnet/api/System.Management.Automation.VerbsData.Save) (sv)|Bewaart gegevens om te voorkomen.||
|[Synchronisatie](/dotnet/api/System.Management.Automation.VerbsData.Sync) (sy)|Zorgt ervoor dat er twee of meer resources in dezelfde staat zijn.|Voor deze actie-termen, zoals repliceren, Coerce, gebruik of niet overeenkomen.|
|[De publicatie ongedaan maken](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (ub)|Maakt een resource niet beschikbaar voor anderen. Deze term is gekoppeld aan `Publish`.|Voor deze actie niet gebruiken van termen zoals verwijderen, herstellen, of verbergen.|
|[Update](/dotnet/api/System.Management.Automation.VerbsData.Update) (ud)|Zorgt voor een resource up-to-date te houden van de status, nauwkeurigheid, conformiteit of naleving. Bijvoorbeeld, de `Update-FormatData` cmdlet-updates en opmaak bestanden toevoegt aan de huidige PowerShell-console.|Voor deze actie niet gebruiken-termen, zoals vernieuwen vernieuwen, herberekenen of opnieuw indexeren.|

## <a name="diagnostic-verbs"></a>Diagnostische termen

Maakt gebruik van PowerShell het [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) klasse voor het definiëren van acties die betrekking hebben op diagnostische gegevens.
De volgende tabel bevat de meeste van de gedefinieerde bewerkingen.

|Term (alias)|Actie|Opmerkingen|
|--------------------|------------|--------------|
|[Fouten opsporen in](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (db)|Een bron uit voor het analyseren van operationele problemen onderzoekt.|Voor deze actie, moet u een term zoals vaststellen niet gebruiken.|
|[Meting](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (ms)|Identificeert de bronnen die worden gebruikt door een opgegeven bewerking of statistieken over een bron worden opgehaald.|Gebruik termen zoals berekenen, bepalen of analyseren niet voor deze actie.|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (pi)|Gebruik de `Test` term.||
|[Reparatie](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (rp)|Een resource herstelt u een bruikbaar voorwaarde|Gebruik termen, zoals de Fix of herstelbewerking niet voor deze actie.|
|[Resolve](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (rv)|Een verkorte versie van weergave van een resource wordt toegewezen aan een volledige weergave.|Gebruik termen, zoals uit te breiden of bepalen niet voor deze actie.|
|[Test](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Controleert of de bewerking of de consistentie van een resource.|Gebruik termen, zoals vaststellen, analyseren, restwaarde of Controleer of niet voor deze actie.|
|[Tracering](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (tr)|De activiteiten van een resource worden bijgehouden.|Voor deze actie niet gebruiken-termen, zoals bijhouden, volgen, inspecteren of graven.|

## <a name="lifecycle-verbs"></a>Levenscyclus van termen

Maakt gebruik van PowerShell het [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) klasse voor het definiëren van acties die betrekking hebben op de levenscyclus van een resource.
De volgende tabel bevat de meeste van de gedefinieerde bewerkingen.

|Term (alias)|Actie|Opmerkingen|
|--------------------|------------|--------------|
|[Goedkeuren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (ap)|Bevestigt of instemt met de status van een resource of proces.||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (als)|Bevestigt de status van een resource.|Voor deze actie, moet u een term zoals Certify niet gebruiken.|
|[Build](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (bd)|Hiermee maakt u een artefact (meestal een binair bestand of document) uit een set van invoerbestanden (meestal broncode of declaratieve documenten)|Deze term is toegevoegd in PowerShell v6|
|[Volledige](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (cp)|Is een bewerking.||
|[Controleer of](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (cn)|Bevestigt, wordt gecontroleerd of valideert de status van een resource of proces.|Gebruik termen, zoals bevestigen, ga akkoord, Certify, valideren of Controleer of niet voor deze actie.|
|[Weigeren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (Distinguished Name)|Weigert, objecten, blokkeert of de status van een resource of proces verzet.|Voor deze actie niet gebruiken van termen zoals blok, Object, weigeren of afwijzen.|
|[Implementeer](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (dp)|Een toepassing, een website of een oplossing verzendt naar een externe target [s] zodanig dat een gebruiker van deze oplossing toegang hebben, nadat de implementatie is voltooid|Deze term is toegevoegd in PowerShell v6|
|[Uitschakelen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Hiermee configureert u een resource aan een niet beschikbaar is of niet-actieve status. Bijvoorbeeld, de `Disable-PSBreakpoint` cmdlet maakt een onderbrekingspunt inactief. Deze term is gekoppeld aan `Enable`.|Gebruik termen, zoals stoppen of verbergen niet voor deze actie.|
|[Schakel](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Hiermee configureert u een resource aan een beschikbaar of de actieve status. Bijvoorbeeld, de `Enable-PSBreakpoint` cmdlet wordt een onderbrekingspunt actief. Deze term is gekoppeld aan `Disable`.|Gebruik termen, zoals het begin of het Begin niet voor deze actie.|
|[Installeer](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (is)|Hiermee plaatst u een resource in een locatie en (optioneel) Hiermee wordt geïnitialiseerd. Deze term is gekoppeld aan `Uninstall`.|Voor deze actie kan niet een term gebruiken zoals Setup.|
|[Aanroepen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Een actie, zoals het uitvoeren van een opdracht of een methode wordt uitgevoerd.|Gebruik termen, zoals uitvoeren of Start niet voor deze actie.|
|[Registreren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (rg)|Hiermee maakt u een vermelding voor een resource in een opslagplaats, zoals een database. Deze term is gekoppeld aan `Unregister`.||
|[Request](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (rq)|Vraagt om een resource of machtigingen gevraagd.||
|[Opnieuw opstarten](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (rt)|Een bewerking gestopt en opnieuw gestart. Bijvoorbeeld, de `Restart-Service` cmdlet stopt en start vervolgens een service.|Gebruik een opdracht zoals Prullenbak niet voor deze actie.|
|[Hervatten](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (ru)|Start een bewerking die is onderbroken. Bijvoorbeeld, de `Resume-Service` cmdlet start-een service die is onderbroken. Deze term is gekoppeld aan `Suspend`.||
|[Start](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|Initieert een bewerking. Bijvoorbeeld, de `Start-Service` cmdlet een service wordt gestart. Deze term is gekoppeld aan `Stop`.|Gebruik termen, zoals starten, initiëren en opstarten niet voor deze actie.|
|[Stop](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (sp)|Stoppen van een activiteit. Deze term is gekoppeld aan `Start`.|Voor deze actie niet gebruiken van termen zoals einde Kill, beëindigen of annuleren.|
|[Indienen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (sb)|Geeft een resource voor goedkeuring.|Gebruik een opdracht zoals Post niet voor deze actie.|
|[Onderbreken](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (GB)|Hiermee wordt een activiteit onderbroken. Bijvoorbeeld, de `Suspend-Service` cmdlet een service wordt onderbroken. Deze term is gekoppeld aan `Resume`.|Voor deze actie, moet u een term zoals onderbreken niet gebruiken.|
|[Verwijder](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (us)|Hiermee verwijdert u een resource vanaf een opgegeven locatie. Deze term is gekoppeld aan `Install`.||
|[De registratie ongedaan maken](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (de)|De vermelding voor een resource verwijdert uit een opslagplaats. Deze term is gekoppeld aan `Register`.|Voor deze actie, moet u een term zoals verwijderen niet gebruiken.|
|[Wacht](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (s)|Hiermee wordt een bewerking onderbroken totdat een specifieke gebeurtenis zich voordoet. Bijvoorbeeld, de `Wait-Job` cmdlet operations onderbroken totdat een of meer van de achtergrondtaken zijn voltooid.|Gebruik termen, zoals de slaap- of onderbreken niet voor deze actie.|

## <a name="security-verbs"></a>Beveiliging-termen

Maakt gebruik van PowerShell het [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) klasse voor het definiëren van acties die betrekking hebben op beveiliging.
De volgende tabel bevat de meeste van de gedefinieerde bewerkingen.

|Term (alias)|Actie|Opmerkingen|
|--------------------|------------|--------------|
|[Blok](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (bl)|Beperkt de toegang tot een resource. Deze term is gekoppeld aan `Unblock`.|Gebruik termen zoals voorkomen, beperken of weigeren niet voor deze actie.|
|[Verleen](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|Biedt toegang tot een resource. Deze term is gekoppeld aan `Revoke`.|Gebruik termen, zoals het toestaan of inschakelen niet voor deze actie.|
|[Beveiligen](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (pt)|Beschermt een resource-aanval of tegen verlies. Deze term is gekoppeld aan `Unprotect`.|Gebruik termen zoals coderen, beveiliging of zegel niet voor deze actie.|
|[Intrekken](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (rk)|Hiermee geeft u een actie die toegang tot een resource niet toelaat. Deze term is gekoppeld aan `Grant`.|Gebruik termen, zoals verwijderen of uitschakelen niet voor deze actie.|
|[De blokkering opheffen](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (ul)|Hiermee verwijdert u beperkingen voor een resource. Deze term is gekoppeld aan `Block`.|Gebruik termen, zoals wissen of toestaan niet voor deze actie.|
|[Beveiliging opheffen](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (maximaal)|Hiermee verwijdert u waarborgen van een resource die zijn toegevoegd om te voorkomen dat deze aanval of tegen verlies. Deze term is gekoppeld aan `Protect`.|Gebruik termen zoals decoderen of Unseal niet voor deze actie.|

## <a name="other-verbs"></a>Andere bewerkingen

Maakt gebruik van PowerShell het [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) klasse om canonieke werkwoord-namen die niet geschikt zijn voor in de categorie van een bepaalde bewerking naam, zoals de algemene, communicatie, gegevens, levenscyclus of beveiliging term namen te definiëren termen.

|Term (alias)|Actie|Opmerkingen|
|--------------------|------------|--------------|
|[Gebruik](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Wordt gebruikt of bevat een resource iets doen.||

## <a name="see-also"></a>Zie ook

[System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[De declaratie van de cmdlet](./cmdlet-class-declaration.md)

[Handleiding voor Windows PowerShell-programmeurs](../prog-guide/windows-powershell-programmer-s-guide.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
