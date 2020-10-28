---
ms.date: 09/07/2018
ms.topic: reference
title: Goedgekeurde werkwoorden voor PowerShell-opdrachten
description: Goedgekeurde werkwoorden voor PowerShell-opdrachten
ms.openlocfilehash: 237355ba9729cfe16c335b39f19ab20e40999457
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655820"
---
# <a name="approved-verbs-for-powershell-commands"></a>Goedgekeurde werkwoorden voor PowerShell-opdrachten

Power shell gebruikt een combi natie van verb-woorden voor de namen van cmdlets en voor de afgeleide .NET-klassen.
Het term gedeelte van de naam geeft de actie aan die door de cmdlet wordt uitgevoerd. Het deel van de naam van het zelfstandige onderdeel van de name identificeert de entiteit waarop de actie wordt uitgevoerd. De `Get-Command` cmdlet haalt bijvoorbeeld alle opdrachten op die zijn geregistreerd in Power shell.

> [!NOTE]
> Power shell gebruikt de term _Verb_ om een woord te beschrijven dat een actie impliceert, zelfs als dat woord niet een standaardwerk woord is in de Engelse taal. De term _New_ is bijvoorbeeld een geldige naam voor een Power shell-term omdat deze een actie impliceert, ook al is het geen werk woord in de Engelse taal.

<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->

Voor elke goedgekeurde term is een bijbehorend _alias voorvoegsel_ gedefinieerd.
We gebruiken dit alias voorvoegsel in aliassen voor opdrachten die deze term gebruiken.
Het voor voegsel van de alias voor `Import` is bijvoorbeeld `ip` en, dienovereenkomstig, de alias voor `Import-Module` is `ipmo` .  Dit is een aanbeveling, maar geen regel; in het bijzonder hoeft niet te worden voldaan aan de opdracht aliassen mimicking goed bekende opdrachten uit andere omgevingen.

## <a name="verb-naming-recommendations"></a>Aanbevelingen voor naamgeving van woorden

De volgende aanbevelingen helpen u bij het kiezen van een geschikt werk woord voor uw cmdlet om consistentie te garanderen tussen de cmdlets die u maakt, de cmdlets die worden verschaft door Power shell en de cmdlets die door anderen zijn ontworpen.

- Gebruik een van de vooraf gedefinieerde term namen van Power shell
- Gebruik de term om het algemene bereik van de actie te beschrijven en gebruik para meters om de actie van de cmdlet verder te verfijnen.
- Gebruik geen synoniem van een goedgekeurde term. Gebruik bijvoorbeeld altijd `Remove` , nooit gebruiken `Delete` of `Eliminate` .
- Gebruik alleen de vorm van elke term die in dit onderwerp wordt vermeld. U kunt bijvoorbeeld gebruiken `Get` , maar niet gebruiken `Getting` of `Gets` .
- Gebruik de volgende gereserveerde termen of aliassen niet. De Power shell-taal of een zeldzame paar van de cmdlets maakt gebruik van deze termen onder uitzonderlijke omstandigheden.
    - ForEach (foreach)
    - [Indeling](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f): rangschikt objecten in een opgegeven formulier of indeling
    - [Groep](/dotnet/api/System.Management.Automation.VerbsData.Group) (GP): Hiermee rangschikt of koppelt u een of meer resources
    - [Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (PI)
    - Sorteren (SR)
    - T (te)
    - Waar (w)

Mogelijk krijgt u een volledige lijst met termen met behulp van de- `Get-Verb` cmdlet.

## <a name="similar-verbs-for-different-actions"></a>Vergelijk bare werk woorden voor verschillende acties

De volgende vergelijk bare termen vertegenwoordigen verschillende acties.

### <a name="new-vs-set"></a>Nieuw versus set

Gebruik de `New` opdracht om een nieuwe resource te maken. Gebruik de `Set` opdracht voor het wijzigen van een bestaande resource, eventueel om deze te maken als deze niet bestaat, zoals de `Set-Variable` cmdlet.

### <a name="find-vs-search"></a>Zoeken versus zoeken

Gebruik de `Find` opdracht om een object te zoeken. Gebruik de `Search` opdracht om een verwijzing naar een resource in een container te maken.

### <a name="get-vs-read"></a>Ophalen versus lezen

Gebruik de `Get` opdracht voor het verkrijgen van informatie over een resource (zoals een bestand) of voor het verkrijgen van een object waarmee u de resource in de toekomst kunt openen. Gebruik de `Read` opdracht om een resource te openen en de informatie in op te halen.

### <a name="invoke-vs-start"></a>Aanroepen versus starten

Gebruik de opdracht `Invoke` om synchrone bewerkingen uit te voeren, zoals het uitvoeren van een opdracht en wacht totdat de bewerking is beëindigd. De `Start` term gebruiken wordt gebruikt voor het starten van asynchrone bewerkingen, zoals het starten van een autonoom proces.

### <a name="ping-vs-test"></a>Ping versus testen

Gebruik de `Test` term.

## <a name="common-verbs"></a>Veelvoorkomende termen

Power shell gebruikt de opsommings klasse [System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) om algemene acties te definiëren die van toepassing kunnen zijn op bijna elke cmdlet. De volgende tabel bevat de meeste gedefinieerde termen.

|Verb (alias)|Actie|Synoniemen om te voor komen|
|--------------------|------------|--------------|
|[Toevoegen](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Hiermee voegt u een resource toe aan een container of koppelt u een item aan een ander item. De `Add-Content` cmdlet voegt bijvoorbeeld inhoud toe aan een bestand. Deze term is gekoppeld aan `Remove` .|Toevoegen, koppelen, samen voegen, invoegen|
|[Wissen](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (CL)|Hiermee worden alle resources uit een container verwijderd, maar wordt de container niet verwijderd. `Clear-Content`Met de cmdlet wordt bijvoorbeeld de inhoud van een bestand verwijderd, maar wordt het bestand niet verwijderd.|Leegmaken, wissen, vrijgeven, uitschakeling, uitschakelen, verwijderen|
|[Sluiten](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (CS)|Hiermee wordt de status van een resource gewijzigd om deze ontoegankelijk, niet beschikbaar of onbruikbaar te maken. Deze term is gekoppeld aan `Open.`||
|[Kopiëren](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (CP)|Kopieert een resource naar een andere naam of naar een andere container. Met de cmdlet wordt bijvoorbeeld `Copy-Item` een item (zoals een bestand) gekopieerd van de ene locatie in het gegevens archief naar een andere locatie.|Dupliceren, klonen, repliceren, synchroniseren|
|[Voer](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et) in|Hiermee geeft u een actie op waarmee de gebruiker naar een resource kan worden verplaatst. De `Enter-PSSession` cmdlet plaatst de gebruiker bijvoorbeeld in een interactieve sessie. Deze term is gekoppeld aan `Exit` .|Pushen naar|
|[Afsluiten](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (ex)|Hiermee stelt u de huidige omgeving of context in op de meest recent gebruikte context. De `Exit-PSSession` cmdlet plaatst bijvoorbeeld de gebruiker in de sessie die is gebruikt om de interactieve sessie te starten. Deze term is gekoppeld aan `Enter` .|Pop, uit|
|[Zoeken](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (FD)|Zoekt naar een object in een container die onbekend, impliciet, optioneel of opgegeven is.|Search|
|[Get](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Hiermee geeft u een actie op waarmee een resource wordt opgehaald. Deze term is gekoppeld aan `Set` .|Lezen, openen, kat, type, dir, verkrijgen, dump, ophalen, onderzoeken, zoeken, zoeken|
|[Verbergen](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Hiermee kan een bron niet worden gedetecteerd. Een cmdlet waarvan de naam de opdracht Hide bevat, kan bijvoorbeeld een service van een gebruiker verbergen. Deze term is gekoppeld aan `Show` .|Blokkeren|
|[Lid worden](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Hiermee worden resources gecombineerd tot één resource. De `Join-Path` cmdlet combineert bijvoorbeeld een pad met een van de onderliggende paden om één pad te maken. Deze term is gekoppeld aan `Split` .|Combi neren, eenheid, verbinden, koppelen|
|[Vergren deling](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (LK)|Een resource beveiligen. Deze term is gekoppeld aan `Unlock` .|Beperken, beveiligen|
|[Verplaatsen](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Hiermee verplaatst u een resource van de ene locatie naar een andere. Met de cmdlet wordt bijvoorbeeld `Move-Item` een item verplaatst van de ene locatie in het gegevens archief naar een andere locatie.|Overdracht, naam, migreren|
|[Nieuw](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Hiermee maakt u een resource. (De `Set` term kan ook worden gebruikt bij het maken van een resource die gegevens bevat, zoals de `Set-Variable` cmdlet.)|Maken, genereren, bouwen, maken, toewijzen|
|[Openen](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (op)|Hiermee wordt de status van een resource gewijzigd om deze toegankelijk, beschikbaar of bruikbaar te maken. Deze term is gekoppeld aan `Close` .||
|[Optimaliseren](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (om)|Verhoogt de effectiviteit van een resource.||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|Hiermee verwijdert u een item boven aan een stack. Met de cmdlet wordt bijvoorbeeld `Pop-Location` de huidige locatie gewijzigd in de locatie die het meest recent is gepusht naar de stack.||
|[Push](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (PU)|Voegt een item toe aan de bovenkant van een stack. Met de cmdlet wordt bijvoorbeeld `Push-Location` de huidige locatie naar de stack gepusht.||
|[Opnieuw uitvoeren](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (opnieuw)|Hiermee wordt een resource opnieuw ingesteld op de status die ongedaan is gemaakt.||
|[Verwijderen](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Hiermee verwijdert u een resource uit een container. De `Remove-Variable` cmdlet verwijdert bijvoorbeeld een variabele en de waarde ervan. Deze term is gekoppeld aan `Add` .|Wissen, knippen, verwijderen, verwijderen, wissen|
|[Rename](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (RN)|Hiermee wordt de naam van een resource gewijzigd. De `Rename-Item` cmdlet, die wordt gebruikt voor toegang tot opgeslagen gegevens, wijzigt bijvoorbeeld de naam van een item in het gegevens archief.|Wijziging|
|[Opnieuw instellen](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (RS)|Hiermee wordt een resource teruggezet naar de oorspronkelijke staat.||
|[Formaat wijzigen](/dotnet/api/System.Management.Automation.VerbsCommon.Resize)(RZ)|Hiermee wordt de grootte van een resource gewijzigd.||
|[Zoeken](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (SR)|Hiermee maakt u een verwijzing naar een resource in een container.|Zoeken, zoeken|
|[Selecteren](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (SC)|Hiermee wordt een bron in een container gezocht. `Select-String`Met de cmdlet vindt u bijvoorbeeld tekst in teken reeksen en bestanden.|Zoeken, zoeken|
|[Set](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|Vervangt gegevens over een bestaande resource of maakt een resource die een aantal gegevens bevat. De `Set-Date` cmdlet wijzigt bijvoorbeeld de systeem tijd op de lokale computer. (De `New` term kan ook worden gebruikt om een resource te maken.) Deze term is gekoppeld aan `Get` .|Schrijven, opnieuw instellen, toewijzen, configureren|
|[Weer geven](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (sh)|Hiermee wordt een resource zichtbaar voor de gebruiker. Deze term is gekoppeld aan `Hide` .|Weer geven, produceren|
|[Overs Laan](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (SK)|Omzeilt een of meer resources of punten in een reeks.|Bypass, Jump|
|[Splitsen](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (SL)|Scheidt delen van een resource. De `Split-Path` cmdlet retourneert bijvoorbeeld verschillende onderdelen van een pad. Deze term is gekoppeld aan `Join` .|Scheiding|
|[Stap](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (St)|Verplaatst naar het volgende punt of de resource in een reeks.||
|[Switch](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (SW)|Hiermee geeft u een actie op die tussen twee resources afwijkt, bijvoorbeeld om te scha kelen tussen twee locaties, verantwoordelijkheden of statussen.||
|[Ongedaan maken](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (verwijderen)|Hiermee stelt u een resource in op de vorige status.||
|[Ontgrendelen](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (UK)|Geeft een resource vrij die is vergrendeld. Deze term is gekoppeld aan `Lock` .|Vrijgeven, onperken, onbeveiligd|
|[Horloge](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (WC)|Hiermee wordt een bron doorlopend gecontroleerd of gecontroleerd op wijzigingen.||

## <a name="communications-verbs"></a>Communicatie bewerkingen

Power Shell maakt gebruik van de klasse [System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) om acties te definiëren die van toepassing zijn op communicatie. De volgende tabel bevat de meeste gedefinieerde termen.

|Verb (alias)|Actie|Synoniemen om te voor komen|
|--------------------|------------|--------------|
|[Verbinding maken](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (CC)|Hiermee maakt u een koppeling tussen een bron en een bestemming. Deze term is gekoppeld aan `Disconnect` .|Toevoegen aan Telnet|
|[Verbinding verbreken](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (DC)|De koppeling tussen een bron en een bestemming wordt verbroken. Deze term is gekoppeld aan `Connect` .|Onderbreken, afmelden|
|[Lezen](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (RD)|Verkrijgt informatie van een bron. Deze term is gekoppeld aan `Write` .|Ophalen, vragen, ophalen|
|[Ontvangen](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (RC)|Hiermee worden gegevens geaccepteerd die vanuit een bron zijn verzonden. Deze term is gekoppeld aan `Send` .|Lezen, accepteren, bekijken|
|[Verzenden](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (SD)|Levert informatie aan een bestemming. Deze term is gekoppeld aan `Receive` .|Put, broadcast, mail, Fax|
|[Schrijven](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (WR)|Hiermee voegt u informatie toe aan een doel. Deze term is gekoppeld aan `Read` .|Plaatsen, afdrukken|

## <a name="data-verbs"></a>Gegevens bewerkingen

Power shell gebruikt de klasse [System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData) om acties te definiëren die van toepassing zijn op de verwerking van gegevens. De volgende tabel bevat de meeste gedefinieerde termen.

|Werkwoord naam (alias)|Actie|Synoniemen om te voor komen|
|-------------------------|------------|--------------|
|[Back-up](/dotnet/api/System.Management.Automation.VerbsData.Backup) (BA)|Hiermee worden gegevens opgeslagen door deze te repliceren.|Opslaan, branden, repliceren, synchroniseren|
|[Controle punt](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (CH)|Hiermee maakt u een moment opname van de huidige status van de gegevens of van de configuratie ervan.|Versch|
|[Compare](/dotnet/api/System.Management.Automation.VerbsData.Compare) (CR)|Hiermee worden de gegevens van de ene resource geëvalueerd op basis van de gegevens van een andere resource.|Versch|
|[Comprimeren](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|Comprimeert de gegevens van een resource. Combi natie met `Expand` .|Comprimeren|
|[Converteren](/dotnet/api/System.Management.Automation.VerbsData.Convert) (AVK)|Wijzigt de gegevens van de ene weer gave naar de andere wanneer de cmdlet bidirectionele conversie ondersteunt of wanneer de cmdlet conversie ondersteunt tussen meerdere gegevens typen.|Wijzigen, verg Roten/verkleinen, opnieuw bemonsteren|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (CF)|Converteert één primair type invoer (de cmdlet zelfstandig geeft de invoer aan) aan een of meer ondersteunde uitvoer typen.|Exporteren, uitvoer, uit|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (CT)|Converteert van een of meer typen invoer naar een primair uitvoer type (de cmdlet zelfstandig geeft het uitvoer type aan).|Importeren, invoeren, in|
|[Ontkoppelen](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (DM)|Koppelt een benoemde entiteit los van een locatie. Deze term is gekoppeld aan `Mount` .|Ontkoppelen, ontkoppelen|
|[Bewerken](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|Bestaande gegevens worden gewijzigd door inhoud toe te voegen of te verwijderen.|Wijzigen, bijwerken, wijzigen|
|[Uitvouwen](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|Hiermee worden de gegevens hersteld van een bron die in de oorspronkelijke staat is gecomprimeerd. Deze term is gekoppeld aan `Compress` .|Exploderen, decomprimeren|
|[Exporteren](/dotnet/api/System.Management.Automation.VerbsData.Export) (EP)|Hiermee wordt de primaire invoer ingekapseld in een permanente gegevens opslag, zoals een bestand, of in een Interchange-indeling. Deze term is gekoppeld aan `Import` .|Extra heren, back-up maken|
|[Importeren](/dotnet/api/System.Management.Automation.VerbsData.Import) (IP)|Hiermee maakt u een resource op basis van gegevens die zijn opgeslagen in een permanente gegevens opslag (zoals een bestand) of in een Interchange-indeling. De `Import-CSV` cmdlet importeert bijvoorbeeld gegevens uit een CSV-bestand (Comma-Separated Value) naar objecten die kunnen worden gebruikt door andere cmdlets. Deze term is gekoppeld aan `Export` .|BulkLoad, laden|
|[Initialiseren](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|Bereidt een resource voor op gebruik en stelt deze in op de standaard status.|Wissen, init, vernieuwen, opnieuw samen stellen, opnieuw initialiseren en instellen|
|[Limiet](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Hiermee worden beperkingen toegepast op een resource.|Quota|
|[Samen voegen](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|Hiermee maakt u één resource van meerdere resources.|Combi neren, samen voegen|
|[Koppelen](/dotnet/api/System.Management.Automation.VerbsData.Mount) (MT)|Hiermee wordt een benoemde entiteit aan een locatie gekoppeld. Deze term is gekoppeld aan `Dismount` .|Verbinding maken|
|[Uit](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Verzendt gegevens uit de omgeving. De `Out-Printer` cmdlet verzendt bijvoorbeeld gegevens naar een printer.||
|[Publiceren](/dotnet/api/System.Management.Automation.VerbsData.Publish) (PB)|Hiermee wordt een resource beschikbaar voor anderen. Deze term is gekoppeld aan `Unpublish` .|Implementeren, vrijgeven, installeren|
|[Herstellen](/dotnet/api/System.Management.Automation.VerbsData.Restore) (RR)|Hiermee stelt u een resource in op een vooraf gedefinieerde status, zoals een status die is ingesteld door `Checkpoint` . `Restore-Computer`Met de cmdlet wordt bijvoorbeeld een systeem herstel gestart op de lokale computer.|Herstellen, retour neren, ongedaan maken, herstellen|
|[Opslaan](/dotnet/api/System.Management.Automation.VerbsData.Save) (SV)|Hiermee worden gegevens bewaard om verlies te voor komen.||
|[Synchronisatie](/dotnet/api/System.Management.Automation.VerbsData.Sync) (SY)|Garandeert dat twee of meer resources zich in dezelfde staat bevinden.|Repliceren, afdwingen, vergelijken|
|[Publicatie ongedaan](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) maken (UB)|Hiermee wordt een bron niet beschikbaar voor anderen. Deze term is gekoppeld aan `Publish` .|Verwijderen, herstellen, verbergen|
|[Update](/dotnet/api/System.Management.Automation.VerbsData.Update) (UD)|Brengt een resource up-to-date om de staat, nauw keurigheid, overeenstemming of naleving te hand haven. De cmdlet wordt bijvoorbeeld `Update-FormatData` bijgewerkt en voegt opmaak bestanden toe aan de huidige Power shell-console.|Vernieuwen, vernieuwen, herberekenen, opnieuw indexeren|

## <a name="diagnostic-verbs"></a>Diagnose woorden

Power Shell maakt gebruik van de klasse [System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) om acties te definiëren die van toepassing zijn op diagnostische gegevens. De volgende tabel bevat de meeste gedefinieerde termen.

|Verb (alias)|Actie|Synoniemen om te voor komen|
|--------------------|------------|--------------|
|[Debug](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (DB)|Onderzoekt een resource om operationele problemen vast te stellen.|Vaststellen|
|[Meting](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (MS)|Identificeert bronnen die worden gebruikt door een opgegeven bewerking of waarmee statistieken over een resource worden opgehaald.|Berekenen, vaststellen, analyseren|
|[Herstellen](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (RP)|Hiermee wordt een resource teruggezet naar een bruikbare voor waarde|Herstellen, herstellen|
|[Oplossen](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (RV)|Wijst een steno weergave van een resource toe aan een meer volledige weer gave.|Uitvouwen, bepalen|
|[Testen](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Hiermee wordt de bewerking of consistentie van een resource gecontroleerd.|Diagnosticeren, analyseren, Restren, controleren|
|[Trace](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (tr)|Houdt de activiteiten van een resource bij.|Bijhouden, volgen, inspecteren, graven|

## <a name="lifecycle-verbs"></a>Levenscyclus werk woorden

Power shell gebruikt de klasse [System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) om acties te definiëren die van toepassing zijn op de levens cyclus van een resource. De volgende tabel bevat de meeste gedefinieerde termen.

|Verb (alias)|Actie|Synoniemen om te voor komen|
|--------------------|------------|--------------|
|[Goed keuren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (AP)|Bevestigt of gaat akkoord met de status van een resource of proces.||
|[Bevestiging](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (as)|Bevestigt de status van een resource.|Certify|
|[Build](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (BD)|Hiermee maakt u een artefact (doorgaans een binair of document) uit een set invoer bestanden (meestal bron code of declaratieve documenten). Deze term is toegevoegd in Power shell 6.||
|[Volt ooien](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (CP)|Een bewerking wordt beëindigd.||
|[Bevestigen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (CN)|Hiermee erkent, verifieert of valideert de status van een resource of proces.|Erkennen, akkoord, certificeren, valideren, verifiëren|
|[Weigeren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (DN)|Hiermee wordt de status van een resource of proces geweigerd, geblokeerd of.|Blok, object, weigeren, afwijzen|
|[Implementeren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (DP)|Hiermee wordt een toepassing, website of oplossing naar een extern doel [s] verzonden, zodat een gebruiker van die oplossing deze kan openen nadat de implementatie is voltooid. Deze term is toegevoegd in Power shell 6.||
|[Uitschakelen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Hiermee configureert u een resource met een niet-beschik bare of inactieve status. De `Disable-PSBreakpoint` cmdlet maakt bijvoorbeeld een onderbrekings punt inactief. Deze term is gekoppeld aan `Enable` .|Stoppen, verbergen|
|[Inschakelen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Hiermee configureert u een resource voor een beschik bare of actieve status. Met de `Enable-PSBreakpoint` cmdlet wordt bijvoorbeeld een onderbrekings punt actief. Deze term is gekoppeld aan `Disable` .|Starten, beginnen|
|[Installeren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (is)|Plaatst een bron op een locatie en initialiseert deze desgewenst. Deze term is gekoppeld aan `Uninstall` .|Instellen|
|[Invoke](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Hiermee wordt een actie uitgevoerd, zoals het uitvoeren van een opdracht of methode.|Uitvoeren, starten|
|[Registreren](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (RG)|Hiermee maakt u een vermelding voor een resource in een opslag plaats, zoals een Data Base. Deze term is gekoppeld aan `Unregister` .||
|[Aanvraag](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (RQ)|U wordt gevraagd om een resource of om toestemming wordt gevraagd.||
|[Opnieuw opstarten](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (RT)|Hiermee stopt u een bewerking en start u deze opnieuw. De `Restart-Service` cmdlet stopt bijvoorbeeld en start vervolgens een service.|Prullenbak|
|[Hervatten](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (ru)|Hiermee wordt een bewerking gestart die is onderbroken. `Resume-Service`Met de cmdlet wordt bijvoorbeeld een service gestart die is onderbroken. Deze term is gekoppeld aan `Suspend` .||
|[Starten](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (SA)|Initieert een bewerking. Met de `Start-Service` cmdlet wordt bijvoorbeeld een service gestart. Deze term is gekoppeld aan `Stop` .|Starten, initiëren, opstarten|
|[Stoppen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (SP)|De activiteit wordt stopgezet. Deze term is gekoppeld aan `Start` .|Beëindigen, afsluiten, beëindigen, annuleren|
|[Verzenden](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (SB)|Geeft een resource voor goed keuring.|Plaatsen|
|[Suspend](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (SS)|Hiermee wordt een activiteit onderbroken. De `Suspend-Service` cmdlet onderbreekt bijvoorbeeld een service. Deze term is gekoppeld aan `Resume` .|Onderbreken|
|[Verwijderen](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (VS)|Hiermee verwijdert u een resource van een opgegeven locatie. Deze term is gekoppeld aan `Install` .||
|[Registratie ongedaan maken](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (uw)|Hiermee verwijdert u de vermelding voor een resource uit een opslag plaats. Deze term is gekoppeld aan `Register` .|Verwijderen|
|[Wachten](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Hiermee wordt een bewerking onderbroken totdat een opgegeven gebeurtenis optreedt. De `Wait-Job` cmdlet pauzeert bijvoorbeeld bewerkingen totdat een of meer van de achtergrond taken zijn voltooid.|Slaap stand, onderbreken|

## <a name="security-verbs"></a>Beveiligings bewerkingen

Power shell gebruikt de klasse [System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) om acties te definiëren die van toepassing zijn op de beveiliging. De volgende tabel bevat de meeste gedefinieerde termen.

|Verb (alias)|Actie|Synoniemen om te voor komen|
|--------------------|------------|--------------|
|[Blok keren](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (BL)|Hiermee beperkt u de toegang tot een resource. Deze term is gekoppeld aan `Unblock` .|Voor komen, beperken, weigeren|
|[Verlenen](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (GR)|Hiermee krijgt u toegang tot een resource. Deze term is gekoppeld aan `Revoke` .|Toestaan, inschakelen|
|[Beveiligen](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (PT)|Beveiligt een bron tegen aanvallen of verlies. Deze term is gekoppeld aan `Unprotect` .|Versleutelen, beveiligen, verzegelen|
|[Intrekken](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (RK)|Hiermee wordt een actie opgegeven die geen toegang tot een resource toestaat. Deze term is gekoppeld aan `Grant` .|Verwijderen, uitschakelen|
|[Blok kering opheffen](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (UL)|Hiermee verwijdert u de beperkingen voor een resource. Deze term is gekoppeld aan `Block` .|Wissen, toestaan|
|[Beveiliging opheffen](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (omhoog)|Hiermee worden de beveiligingen verwijderd uit een resource die is toegevoegd om de aanval of het verlies te voor komen. Deze term is gekoppeld aan `Protect` .|Ontsleutelen, Ontzegelen|

## <a name="other-verbs"></a>Andere bewerkingen

Power Shell maakt gebruik van de klasse [System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) om canonieke namen van woorden te definiëren die niet in een specifieke termen categorie staan, zoals de termen common, Communications, Data, Lifecycle of Security term names.

|Verb (alias)|Actie|Synoniemen om te voor komen|
|--------------------|------------|--------------|
|[Gebruik](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Maakt gebruik van of bevat een resource om iets te doen.||

## <a name="see-also"></a>Zie ook

- [System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)
- [System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)
- [System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData)
- [System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)
- [System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)
- [System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)
- [System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)
- [Cmdlet-declaratie](./cmdlet-class-declaration.md)
- [Handleiding voor Windows PowerShell-programmeurs](../prog-guide/windows-powershell-programmer-s-guide.md)
- [Windows Power shell shell SDK](../windows-powershell-reference.md)
