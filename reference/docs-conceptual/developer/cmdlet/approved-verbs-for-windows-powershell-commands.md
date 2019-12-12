---
title: Goedgekeurde werk woorden voor Power shell-opdrachten | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359469"
---
# <a name="approved-verbs-for-powershell-commands"></a>Goedgekeurde werk woorden voor Power shell-opdrachten

Power shell gebruikt een combi natie van verb-woorden voor de namen van cmdlets en voor de afgeleide Microsoft .NET Framework-klassen.
De `Get-Command` cmdlet van Power shell wordt bijvoorbeeld gebruikt om alle opdrachten op te halen die zijn geregistreerd in Power shell.
Het term gedeelte van de naam geeft de actie aan die door de cmdlet wordt uitgevoerd.
Het deel van de naam van het zelfstandige onderdeel van de name identificeert de entiteit waarop de actie wordt uitgevoerd.

> [!NOTE]
> Power shell gebruikt de term *Verb* om een woord te beschrijven dat een actie impliceert, zelfs als dat woord niet een standaardwerk woord is in de Engelse taal.
> De term *New* is bijvoorbeeld een geldige naam voor een Power shell-term omdat deze een actie impliceert, ook al is het geen werk woord in de Engelse taal.

## <a name="verb-naming-rules"></a>Naamgevings regels voor termen

De volgende lijst bevat richt lijnen waarmee u rekening moet houden wanneer u de term voor een cmdlet-naam kiest:

* Wanneer u de term opgeeft, raden we u aan om een van de vooraf gedefinieerde termen te gebruiken die worden geleverd door Power shell (aliassen voor deze vooraf gedefinieerde woorden zijn opgenomen in de volgende tabellen).
  Wanneer u een vooraf gedefinieerde term gebruikt, zorgt u ervoor dat de-cmdlets die u maakt consistent zijn met de cmdlets die door Power shell worden verschaft en de cmdlets die door anderen zijn ontworpen.

* Gebruik de vooraf gedefinieerde termen om het algemene bereik van de actie te beschrijven en gebruik para meters om de actie van de cmdlet verder te verfijnen.

* Als u consistentie tussen cmdlets wilt afdwingen, gebruikt u geen synoniem van een goedgekeurde term.

* Gebruik alleen de vorm van elke term die in dit onderwerp wordt vermeld.
  Gebruik bijvoorbeeld ' Get ', maar gebruik geen ' ophalen ' of ' opgehaald '.

* Gebruik Pascal-behuizing voor termen.
  In Pascal-behuizing is de eerste letter van elk woord gekapitaliseerd, zoals ' ForEach '.

* Gebruik de volgende gereserveerde termen of aliassen niet.
  Deze woorden worden gebruikt door de Power shell-taal of door speciale cmdlets die worden meegeleverd met Power shell.
  - ForEach (foreach)
  - Indeling (f)
  - Groep (GP)
  - Sorteren (SR)
  - T (te)
  - Waar (w)

## <a name="similar-verbs-for-different-actions"></a>Vergelijk bare werk woorden voor verschillende acties

De volgende vergelijk bare termen vertegenwoordigen verschillende acties.

### <a name="new-vs-set"></a>Nieuw versus set
De `New`-werk woord wordt gebruikt om een nieuwe resource te maken.
De `Set`-werk woord wordt gebruikt om een bestaande resource te wijzigen, waarbij u eventueel de resource maakt als deze niet bestaat, zoals de `Set-Variable`-cmdlet.

### <a name="find-vs-search"></a>Zoeken versus zoeken
De `Find`-werk woord wordt gebruikt om een object te zoeken.
De `Search`-werk woord wordt gebruikt voor het maken van een verwijzing naar een resource in een container.

### <a name="get-vs-read"></a>Ophalen versus lezen
Het `Get` werk woord wordt gebruikt om een resource, zoals een bestand, op te halen.
De `Read` werk woord wordt gebruikt om informatie op te halen uit een bron, zoals een bestand.

### <a name="invoke-vs-start"></a>Aanroepen versus starten
De `Invoke`-opdracht wordt gebruikt om een bewerking uit te voeren die doorgaans een synchrone bewerking is, zoals het uitvoeren van een opdracht.
De `Start`-werk woord wordt gebruikt om een bewerking te starten die over het algemeen een asynchrone bewerking is, zoals het starten van een proces.

### <a name="ping-vs-test"></a>Ping versus testen
Gebruik de `Test` term.

## <a name="common-verbs"></a>Veelvoorkomende termen

Power shell gebruikt de opsommings klasse [System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) om algemene acties te definiëren die van toepassing kunnen zijn op bijna elke cmdlet.
De volgende tabel bevat de meeste gedefinieerde termen.

|Verb (alias)|Actie|Opmerkingen|
|--------------------|------------|--------------|
|[Toevoegen](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Hiermee voegt u een resource toe aan een container of koppelt u een item aan een ander item. De `Add-Content` cmdlet voegt bijvoorbeeld inhoud toe aan een bestand. Deze term is gekoppeld aan `Remove`.|Gebruik voor deze actie geen woorden zoals toevoegen, koppelen, samen voegen of invoegen.|
|[Wissen](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (CL)|Hiermee worden alle resources uit een container verwijderd, maar wordt de container niet verwijderd. Met de `Clear-Content` cmdlet wordt bijvoorbeeld de inhoud van een bestand verwijderd, maar wordt het bestand niet verwijderd.|Gebruik voor deze actie geen woorden zoals flush, erase, release, unmarkeren, demarkering, of opheffen.|
|[Sluiten](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (CS)|Hiermee wordt de status van een resource gewijzigd om deze ontoegankelijk, niet beschikbaar of onbruikbaar te maken. Deze term is gekoppeld aan `Open.`||
|[Kopiëren](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (CP)|Kopieert een resource naar een andere naam of naar een andere container. Zo kopieert de `Copy-Item`-cmdlet die wordt gebruikt voor toegang tot opgeslagen gegevens, een item van de ene locatie in het gegevens archief naar een andere locatie.|Gebruik voor deze actie geen woorden zoals dupliceren, klonen, repliceren of synchroniseren.|
|[Voer](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et) in|Hiermee geeft u een actie op waarmee de gebruiker naar een resource kan worden verplaatst. De `Enter-PSSession`-cmdlet plaatst de gebruiker bijvoorbeeld in een interactieve sessie. Deze term is gekoppeld aan `Exit`.|Gebruik voor deze actie geen werk woorden zoals push of into.|
|[Afsluiten](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (ex)|Hiermee stelt u de huidige omgeving of context in op de meest recent gebruikte context. Zo plaatst de `Exit-PSSession`-cmdlet de gebruiker in de sessie die is gebruikt om de interactieve sessie te starten. Deze term is gekoppeld aan `Enter`.|Gebruik voor deze actie geen woorden zoals pop of out.|
|[Zoeken](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (FD)|Zoekt naar een object in een container die onbekend, impliciet, optioneel of opgegeven is.||
|[Indeling](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|Objecten in een opgegeven formulier of indeling ordenen.||
|[Get](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Hiermee geeft u een actie op waarmee een resource wordt opgehaald. Deze term is gekoppeld aan `Set`.|Gebruik voor deze actie geen woorden zoals lezen, openen, kat, type, dir, verkrijgen, dumpen, verkrijgen, zoeken of zoeken.|
|[Verbergen](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Hiermee kan een bron niet worden gedetecteerd. Een cmdlet waarvan de naam de opdracht Hide bevat, kan bijvoorbeeld een service van een gebruiker verbergen. Deze term is gekoppeld aan `Show`.|Gebruik voor deze actie geen term zoals blok keren.|
|[Lid worden](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Hiermee worden resources gecombineerd tot één resource. De `Join-Path` cmdlet combineert bijvoorbeeld een pad met een van de onderliggende paden om één pad te maken. Deze term is gekoppeld aan `Split`.|Gebruik voor deze actie geen woorden zoals combi neren, eenheid toewijzen, verbinden of koppelen.|
|[Vergren deling](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (LK)|Een resource beveiligen. Deze term is gekoppeld aan `Unlock`.|Gebruik voor deze actie geen woorden zoals beperken of beveiligen.|
|[Verplaatsen](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Hiermee verplaatst u een resource van de ene locatie naar een andere. Met de cmdlet `Move-Item` wordt bijvoorbeeld een item verplaatst van de ene locatie in het gegevens archief naar een andere locatie.|Gebruik voor deze actie geen woorden zoals overdracht, naam of migratie.|
|[Nieuw](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Hiermee maakt u een resource. (De `Set` term kan ook worden gebruikt bij het maken van een resource die gegevens bevat, zoals de `Set-Variable`-cmdlet.)|Gebruik voor deze actie geen woorden zoals maken, genereren, bouwen, maken of toewijzen.|
|[Openen](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (op)|Hiermee wordt de status van een resource gewijzigd om deze toegankelijk, beschikbaar of bruikbaar te maken. Deze term is gekoppeld aan `Close`.||
|[Optimaliseren](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (om)|Verhoogt de effectiviteit van een resource.||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|Hiermee verwijdert u een item boven aan een stack. Met de cmdlet `Pop-Location` wordt bijvoorbeeld de huidige locatie gewijzigd in de locatie die het meest recent is gepusht naar de stack.||
|[Push](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (PU)|Voegt een item toe aan de bovenkant van een stack. Met de cmdlet `Push-Location` wordt bijvoorbeeld de huidige locatie naar de stack gepusht.||
|[Opnieuw uitvoeren](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (opnieuw)|Hiermee wordt een resource opnieuw ingesteld op de status die ongedaan is gemaakt.||
|[Verwijderen](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Hiermee verwijdert u een resource uit een container. Met de `Remove-Variable` cmdlet worden bijvoorbeeld een variabele en de bijbehorende waarde verwijderd. Deze term is gekoppeld aan `Add`.|Gebruik voor deze actie geen woorden zoals wissen, knippen, afstoten, verwijderen of wissen.|
|[Rename](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (RN)|Hiermee wordt de naam van een resource gewijzigd. De `Rename-Item`-cmdlet, die wordt gebruikt voor toegang tot opgeslagen gegevens, wijzigt bijvoorbeeld de naam van een item in het gegevens archief.|Gebruik voor deze actie geen term zoals wijzigen.|
|[Opnieuw instellen](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (RS)|Hiermee wordt een resource teruggezet naar de oorspronkelijke staat.||
|[Zoeken](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (SR)|Hiermee maakt u een verwijzing naar een resource in een container.|Gebruik voor deze actie geen woorden zoals zoeken of zoeken.|
|[Selecteren](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (SC)|Hiermee wordt een bron in een container gezocht. De `Select-String` cmdlet vindt bijvoorbeeld tekst in teken reeksen en bestanden.|Gebruik voor deze actie geen woorden zoals zoeken of zoeken.|
|[Set](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|Vervangt gegevens over een bestaande resource of maakt een resource die een aantal gegevens bevat. Zo wijzigt de cmdlet `Set-Date` de systeem tijd op de lokale computer. (De `New`-term kan ook worden gebruikt om een resource te maken.) Deze term is gekoppeld aan `Get`.|Gebruik voor deze actie geen woorden zoals schrijven, opnieuw instellen, toewijzen of configureren.|
|[Weer geven](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (sh)|Hiermee wordt een resource zichtbaar voor de gebruiker. Deze term is gekoppeld aan `Hide`.|Gebruik voor deze actie geen termen zoals weer geven of maken.|
|[Overs Laan](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (SK)|Omzeilt een of meer resources of punten in een reeks.|Gebruik voor deze actie geen term zoals bypass of jump.|
|[Splitsen](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (SL)|Scheidt delen van een resource. De `Split-Path` cmdlet retourneert bijvoorbeeld verschillende onderdelen van een pad. Deze term is gekoppeld aan `Join`.|Gebruik voor deze actie geen term die afzonderlijk wordt gebruikt.|
|[Stap](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (St)|Verplaatst naar het volgende punt of de resource in een reeks.||
|[Switch](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (SW)|Hiermee geeft u een actie op die tussen twee resources afwijkt, bijvoorbeeld om te scha kelen tussen twee locaties, verantwoordelijkheden of statussen.||
|[Ongedaan maken](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (verwijderen)|Hiermee stelt u een resource in op de vorige status.||
|[Ontgrendelen](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (UK)|Geeft een resource vrij die is vergrendeld. Deze term is gekoppeld aan `Lock`.|Gebruik voor deze actie geen woorden zoals vrijgeven, ongedaan maken of onbeveiligd.|
|[Horloge](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (WC)|Hiermee wordt een bron doorlopend gecontroleerd of gecontroleerd op wijzigingen.||

## <a name="communications-verbs"></a>Communicatie bewerkingen

Power Shell maakt gebruik van de klasse [System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) om acties te definiëren die van toepassing zijn op communicatie.
De volgende tabel bevat de meeste gedefinieerde termen.

|Verb (alias)|Actie|Opmerkingen|
|--------------------|------------|--------------|
|[Verbinding maken](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (CC)|Hiermee maakt u een koppeling tussen een bron en een bestemming. Deze term is gekoppeld aan `Disconnect`.|Gebruik voor deze actie geen woorden zoals samen voegen of Telnet.|
|[Verbinding verbreken](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (DC)|De koppeling tussen een bron en een bestemming wordt verbroken. Deze term is gekoppeld aan `Connect`.|Gebruik voor deze actie geen werk woorden zoals afbreek-of afmelden.|
|[Lezen](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (RD)|Verkrijgt informatie van een bron. Deze term is gekoppeld aan `Write`.|Gebruik voor deze actie geen woorden zoals ophalen, vragen of ophalen.|
|[Ontvangen](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (RC)|Hiermee worden gegevens geaccepteerd die vanuit een bron zijn verzonden. Deze term is gekoppeld aan `Send`.|Gebruik voor deze actie geen woorden zoals lezen, accepteren of bekijken.|
|[Verzenden](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (SD)|Levert informatie aan een bestemming. Deze term is gekoppeld aan `Receive`.|Gebruik voor deze actie geen woorden zoals put, broadcast, mail of fax.|
|[Schrijven](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (WR)|Hiermee voegt u informatie toe aan een doel. Deze term is gekoppeld aan `Read`.|Gebruik voor deze actie geen woorden zoals plaatsen of afdrukken.|

## <a name="data-verbs"></a>Gegevens bewerkingen

Power shell gebruikt de klasse [System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData) om acties te definiëren die van toepassing zijn op de verwerking van gegevens.
De volgende tabel bevat de meeste gedefinieerde termen.

|Werkwoord naam (alias)|Actie|Opmerkingen|
|-------------------------|------------|--------------|
|[Back-up](/dotnet/api/System.Management.Automation.VerbsData.Backup) (BA)|Hiermee worden gegevens opgeslagen door deze te repliceren.|Gebruik voor deze actie geen woorden zoals opslaan, branden, repliceren of synchroniseren.|
|[Controle punt](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (CH)|Hiermee maakt u een moment opname van de huidige status van de gegevens of van de configuratie ervan.|Gebruik voor deze actie geen term zoals diff.|
|[Compare](/dotnet/api/System.Management.Automation.VerbsData.Compare) (CR)|Hiermee worden de gegevens van de ene resource geëvalueerd op basis van de gegevens van een andere resource.|Gebruik voor deze actie geen term zoals diff.|
|[Comprimeren](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|Comprimeert de gegevens van een resource. Paren met `Expand`.|Gebruik voor deze actie geen term zoals comprimeren.|
|[Converteren](/dotnet/api/System.Management.Automation.VerbsData.Convert) (AVK)|Wijzigt de gegevens van de ene weer gave naar de andere wanneer de cmdlet bidirectionele conversie ondersteunt of wanneer de cmdlet conversie ondersteunt tussen meerdere gegevens typen.|Voor deze actie moet u geen werk woorden zoals wijzigen, verg Roten/verkleinen of opnieuw bemonsteren gebruiken.|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (CF)|Converteert één primair type invoer (de cmdlet zelfstandig geeft de invoer aan) aan een of meer ondersteunde uitvoer typen.|Gebruik voor deze actie geen woorden zoals exporteren, uitvoer of uitgaand.|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (CT)|Converteert van een of meer typen invoer naar een primair uitvoer type (de cmdlet zelfstandig geeft het uitvoer type aan).|Gebruik voor deze actie geen woorden zoals importeren, invoer of in.|
|[Ontkoppelen](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (DM)|Koppelt een benoemde entiteit los van een locatie. Deze term is gekoppeld aan `Mount`.|Gebruik voor deze actie geen woorden zoals ontkoppelen of ontkoppelen.|
|[Bewerken](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|Bestaande gegevens worden gewijzigd door inhoud toe te voegen of te verwijderen.|Gebruik voor deze actie geen woorden zoals wijzigen, bijwerken of wijzigen.|
|[Uitvouwen](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|Hiermee worden de gegevens hersteld van een bron die in de oorspronkelijke staat is gecomprimeerd. Deze term is gekoppeld aan `Compress`.|Gebruik voor deze actie geen woorden zoals exploderen of decomprimeren.|
|[Exporteren](/dotnet/api/System.Management.Automation.VerbsData.Export) (EP)|Hiermee wordt de primaire invoer ingekapseld in een permanente gegevens opslag, zoals een bestand, of in een Interchange-indeling. Deze term is gekoppeld aan `Import`.|Gebruik voor deze actie geen woorden zoals extract of backup.|
|[Groep](/dotnet/api/System.Management.Automation.VerbsData.Group) (GP)|Hiermee rangschikt of koppelt u een of meer resources.|Gebruik voor deze actie geen woorden zoals aggregatie, ordenen, koppelen of correleren.|
|[Importeren](/dotnet/api/System.Management.Automation.VerbsData.Import) (IP)|Hiermee maakt u een resource op basis van gegevens die zijn opgeslagen in een permanente gegevens opslag (zoals een bestand) of in een Interchange-indeling. Met de cmdlet `Import-CSV` worden bijvoorbeeld gegevens uit een bestand met door komma's gescheiden waarden (CSV) geïmporteerd naar objecten die kunnen worden gebruikt door andere cmdlets. Deze term is gekoppeld aan `Export`.|Gebruik voor deze actie geen woorden zoals BulkLoad of load.|
|[Initialiseren](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|Bereidt een resource voor op gebruik en stelt deze in op de standaard status.|Gebruik voor deze actie geen woorden zoals wissen, init, vernieuwen, opnieuw samen stellen, opnieuw initialiseren of instellen.|
|[Limiet](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Hiermee worden beperkingen toegepast op een resource.|Gebruik voor deze actie geen term zoals quota.|
|[Samen voegen](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|Hiermee maakt u één resource van meerdere resources.|Gebruik voor deze actie geen woorden zoals combi neren of samen voegen.|
|[Koppelen](/dotnet/api/System.Management.Automation.VerbsData.Mount) (MT)|Hiermee wordt een benoemde entiteit aan een locatie gekoppeld. Deze term is gekoppeld aan `Dismount`.|Gebruik voor deze actie niet de term Connect.|
|[Uit](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Verzendt gegevens uit de omgeving. Met de cmdlet `Out-Printer` worden bijvoorbeeld gegevens naar een printer verzonden.||
|[Publiceren](/dotnet/api/System.Management.Automation.VerbsData.Publish) (PB)|Hiermee wordt een resource beschikbaar voor anderen. Deze term is gekoppeld aan `Unpublish`.|Gebruik voor deze actie geen woorden zoals implementeren, vrijgeven of installeren.|
|[Herstellen](/dotnet/api/System.Management.Automation.VerbsData.Restore) (RR)|Hiermee stelt u een resource in op een vooraf gedefinieerde status, zoals een status die is ingesteld door `Checkpoint`. Met de `Restore-Computer` cmdlet wordt bijvoorbeeld een systeem herstel gestart op de lokale computer.|Gebruik voor deze actie geen woorden zoals herstellen, retour neren, ongedaan maken of herstellen.|
|[Opslaan](/dotnet/api/System.Management.Automation.VerbsData.Save) (SV)|Hiermee worden gegevens bewaard om verlies te voor komen.||
|[Synchronisatie](/dotnet/api/System.Management.Automation.VerbsData.Sync) (SY)|Garandeert dat twee of meer resources zich in dezelfde staat bevinden.|Gebruik voor deze actie geen woorden zoals repliceren, afdwingen of vergelijken.|
|[Publicatie ongedaan](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) maken (UB)|Hiermee wordt een bron niet beschikbaar voor anderen. Deze term is gekoppeld aan `Publish`.|Gebruik voor deze actie geen woorden zoals verwijderen, herstellen of verbergen.|
|[Update](/dotnet/api/System.Management.Automation.VerbsData.Update) (UD)|Brengt een resource up-to-date om de staat, nauw keurigheid, overeenstemming of naleving te hand haven. De `Update-FormatData` cmdlet wordt bijvoorbeeld bijgewerkt en voegt opmaak bestanden toe aan de huidige Power shell-console.|Gebruik voor deze actie geen woorden zoals vernieuwen, vernieuwen, herberekenen of opnieuw indexeren.|

## <a name="diagnostic-verbs"></a>Diagnose woorden

Power Shell maakt gebruik van de klasse [System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) om acties te definiëren die van toepassing zijn op diagnostische gegevens.
De volgende tabel bevat de meeste gedefinieerde termen.

|Verb (alias)|Actie|Opmerkingen|
|--------------------|------------|--------------|
|[Debug](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (DB)|Onderzoekt een resource om operationele problemen vast te stellen.|Gebruik voor deze actie geen term zoals diagnose.|
|[Meting](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (MS)|Identificeert bronnen die worden gebruikt door een opgegeven bewerking of waarmee statistieken over een resource worden opgehaald.|Gebruik voor deze actie geen woorden zoals berekenen, bepalen of analyseren.|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (PI)|Gebruik de `Test` term.||
|[Herstellen](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (RP)|Hiermee wordt een resource teruggezet naar een bruikbare voor waarde|Gebruik voor deze actie geen woorden zoals herstellen of herstellen.|
|[Oplossen](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (RV)|Wijst een steno weergave van een resource toe aan een meer volledige weer gave.|Gebruik voor deze actie geen woorden zoals uitbreiden of bepalen.|
|[Testen](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Hiermee wordt de bewerking of consistentie van een resource gecontroleerd.|Gebruik voor deze actie geen woorden zoals het vaststellen, analyseren, Restren of verifiëren.|
|[Trace](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (tr)|Houdt de activiteiten van een resource bij.|Gebruik voor deze actie geen woorden zoals volgen, volgen, inspecteren of graven.|

## <a name="lifecycle-verbs"></a>Levenscyclus werk woorden

Power shell gebruikt de klasse [System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) om acties te definiëren die van toepassing zijn op de levens cyclus van een resource.
De volgende tabel bevat de meeste gedefinieerde termen.

|Verb (alias)|Actie|Opmerkingen|
|--------------------|------------|--------------|
|[Goed keuren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (AP)|Bevestigt of gaat akkoord met de status van een resource of proces.||
|[Bevestiging](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (as)|Bevestigt de status van een resource.|Gebruik voor deze actie geen term zoals certificeren.|
|[Build](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (BD)|Hiermee maakt u een artefact (doorgaans een binair of document) uit een set invoer bestanden (meestal bron code of declaratieve documenten)|Deze term is toegevoegd in Power shell V6|
|[Volt ooien](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (CP)|Een bewerking wordt beëindigd.||
|[Bevestigen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (CN)|Hiermee erkent, verifieert of valideert de status van een resource of proces.|Gebruik voor deze actie geen woorden zoals erkennen, akkoord, certificeren, valideren of verifiëren.|
|[Weigeren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (DN)|Hiermee wordt de status van een resource of proces geweigerd, geblokeerd of.|Gebruik voor deze actie geen woorden zoals blok keren, objecten, weigeren of afwijzen.|
|[Implementeren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (DP)|Hiermee wordt een toepassing, website of oplossing naar een extern doel [s] verzonden, zodat een gebruiker van die oplossing deze kan openen nadat de implementatie is voltooid|Deze term is toegevoegd in Power shell V6|
|[Uitschakelen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Hiermee configureert u een resource met een niet-beschik bare of inactieve status. De `Disable-PSBreakpoint` cmdlet maakt bijvoorbeeld een onderbrekings punt inactief. Deze term is gekoppeld aan `Enable`.|Gebruik voor deze actie geen woorden zoals stoppen of verbergen.|
|[Inschakelen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Hiermee configureert u een resource voor een beschik bare of actieve status. De `Enable-PSBreakpoint`-cmdlet maakt bijvoorbeeld een onderbrekings punt actief. Deze term is gekoppeld aan `Disable`.|Gebruik voor deze actie geen woorden zoals begin of begin.|
|[Installeren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (is)|Plaatst een bron op een locatie en initialiseert deze desgewenst. Deze term is gekoppeld aan `Uninstall`.|Voor deze actie moet u geen use-term gebruiken zoals Setup.|
|[Invoke](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Hiermee wordt een actie uitgevoerd, zoals het uitvoeren van een opdracht of methode.|Gebruik voor deze actie geen woorden zoals uitvoeren of starten.|
|[Registreren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (RG)|Hiermee maakt u een vermelding voor een resource in een opslag plaats, zoals een Data Base. Deze term is gekoppeld aan `Unregister`.||
|[Aanvraag](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (RQ)|U wordt gevraagd om een resource of om toestemming wordt gevraagd.||
|[Opnieuw opstarten](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (RT)|Hiermee stopt u een bewerking en start u deze opnieuw. Zo stopt de cmdlet `Restart-Service` en wordt vervolgens een service gestart.|Gebruik voor deze actie geen term zoals recyclen.|
|[Hervatten](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (ru)|Hiermee wordt een bewerking gestart die is onderbroken. Met de `Resume-Service` cmdlet wordt bijvoorbeeld een service gestart die is onderbroken. Deze term is gekoppeld aan `Suspend`.||
|[Starten](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (SA)|Initieert een bewerking. Met de `Start-Service` cmdlet wordt bijvoorbeeld een service gestart. Deze term is gekoppeld aan `Stop`.|Gebruik voor deze actie geen woorden zoals starten, initiëren of opstarten.|
|[Stoppen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (SP)|De activiteit wordt stopgezet. Deze term is gekoppeld aan `Start`.|Gebruik voor deze actie geen woorden zoals end, Kill, Terminate of Cancel.|
|[Verzenden](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (SB)|Geeft een resource voor goed keuring.|Gebruik voor deze actie geen term zoals post.|
|[Suspend](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (SS)|Hiermee wordt een activiteit onderbroken. Met de `Suspend-Service` cmdlet wordt bijvoorbeeld een service onderbroken. Deze term is gekoppeld aan `Resume`.|Gebruik voor deze actie geen term zoals Pause.|
|[Verwijderen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (VS)|Hiermee verwijdert u een resource van een opgegeven locatie. Deze term is gekoppeld aan `Install`.||
|[Registratie ongedaan maken](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (uw)|Hiermee verwijdert u de vermelding voor een resource uit een opslag plaats. Deze term is gekoppeld aan `Register`.|Gebruik voor deze actie geen term zoals verwijderen.|
|[Wachten](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Hiermee wordt een bewerking onderbroken totdat een opgegeven gebeurtenis optreedt. De `Wait-Job` cmdlet pauzeert bijvoorbeeld bewerkingen totdat een of meer van de achtergrond taken zijn voltooid.|Gebruik voor deze actie geen woorden zoals de slaap stand of pauzeren.|

## <a name="security-verbs"></a>Beveiligings bewerkingen

Power shell gebruikt de klasse [System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) om acties te definiëren die van toepassing zijn op de beveiliging.
De volgende tabel bevat de meeste gedefinieerde termen.

|Verb (alias)|Actie|Opmerkingen|
|--------------------|------------|--------------|
|[Blok keren](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (BL)|Hiermee beperkt u de toegang tot een resource. Deze term is gekoppeld aan `Unblock`.|Gebruik voor deze actie geen woorden zoals het voor komen, beperken of weigeren.|
|[Verlenen](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (GR)|Hiermee krijgt u toegang tot een resource. Deze term is gekoppeld aan `Revoke`.|Voor deze actie moet u geen werk woorden zoals toestaan of inschakelen gebruiken.|
|[Beveiligen](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (PT)|Beveiligt een bron tegen aanvallen of verlies. Deze term is gekoppeld aan `Unprotect`.|Gebruik voor deze actie geen woorden zoals versleutelen, beveiligen of verzegelen.|
|[Intrekken](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (RK)|Hiermee wordt een actie opgegeven die geen toegang tot een resource toestaat. Deze term is gekoppeld aan `Grant`.|Gebruik voor deze actie geen woorden zoals verwijderen of uitschakelen.|
|[Blok kering opheffen](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (UL)|Hiermee verwijdert u de beperkingen voor een resource. Deze term is gekoppeld aan `Block`.|Gebruik voor deze actie geen woorden zoals wissen of toestaan.|
|[Beveiliging opheffen](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (omhoog)|Hiermee worden de beveiligingen verwijderd uit een resource die is toegevoegd om de aanval of het verlies te voor komen. Deze term is gekoppeld aan `Protect`.|Gebruik voor deze actie geen woorden zoals ontsleutelen of Ontzegelen.|

## <a name="other-verbs"></a>Andere bewerkingen

Power Shell maakt gebruik van de klasse [System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) om canonieke namen van woorden te definiëren die niet in een specifieke termen categorie staan, zoals de termen common, Communications, Data, Lifecycle of Security term names.

|Verb (alias)|Actie|Opmerkingen|
|--------------------|------------|--------------|
|[Gebruik](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Maakt gebruik van of bevat een resource om iets te doen.||

## <a name="see-also"></a>Zie ook

[System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[Cmdlet-declaratie](./cmdlet-class-declaration.md)

[Hand leiding voor Windows Power shell-programmeurs](../prog-guide/windows-powershell-programmer-s-guide.md)

[Windows Power shell shell SDK](../windows-powershell-reference.md)
