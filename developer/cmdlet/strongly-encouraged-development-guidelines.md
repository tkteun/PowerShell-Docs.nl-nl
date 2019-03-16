---
title: Ten zeerste aangeraden ontwikkeling-richtlijnen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: 0906d0d37c66b8c1538a0b2e9e0f1ff2fba12ac0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057719"
---
# <a name="strongly-encouraged-development-guidelines"></a>Zeer aangeraden richtlijnen voor de ontwikkeling

Deze sectie beschrijft de richtlijnen die u volgen moet wanneer u uw cmdlets schrijven. Ze worden gescheiden in richtlijnen voor het ontwerpen van cmdlets en richtlijnen voor het schrijven van de cmdlet-code. Mogelijk vindt u deze richtlijnen zijn niet geldig voor elk scenario. Echter, als ze van toepassing en u deze richtlijnen niet uitvoert, hebben uw gebruikers mogelijk een slechte ervaring wanneer ze uw cmdlets gebruiken.

## <a name="design-guidelines"></a>Richtlijnen voor het ontwerpen

- [Een specifieke zelfstandig naamwoord gebruikt voor een Cmdlet-naam (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Use-Case Pascal voor Cmdlet-namen (SD02)](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [Richtlijnen voor het ontwerpen parameter (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [Feedback geven aan de gebruiker (SD04)](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Maken van een Cmdlet Help-bestand (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>Code-richtlijnen

- [Parameters (SC01) coderen](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [Ondersteuning van goed gedefinieerde Pijpleidinginvoer (SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [Schrijven van afzonderlijke Records aan de pijplijn (SC03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Controleer de Cmdlets niet hoofdlettergevoelig en (SC04) met een aanvraag te behouden](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>Richtlijnen voor het ontwerpen

De volgende richtlijnen moeten worden gevolgd bij het ontwerpen van cmdlets om te controleren of een consistente gebruikerservaring tussen het gebruik van de cmdlets en andere cmdlets. Als u een ontwerp richtlijn die van toepassing op uw situatie is, moet u kijken naar de richtlijnen van de Code voor vergelijkbare richtlijnen.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>Een specifieke zelfstandig naamwoord gebruikt voor een Cmdlet-naam (SD01)

Zelfstandige naamwoorden gebruikt in de naam van de cmdlet moeten worden zeer specifieke zodat uw cmdlets door de gebruiker kunt detecteren. Het voorvoegsel dat algemene woorden zoals 'server' met een verkorte versie van de naam van het product. Als een zelfstandig naamwoord naar een server waarop een exemplaar van Microsoft SQL Server wordt uitgevoerd verwijst, bijvoorbeeld een zelfstandig naamwoord, zoals 'SQLServer' gebruiken. De combinatie van specifieke woorden en de korte lijst van goedgekeurde werkwoorden kunt de gebruiker om snel te detecteren en anticiperen op functionaliteit zonder duplicatie tussen de namen van de cmdlets.

Als u wilt de gebruikerservaring te verbeteren, moet het zelfstandig naamwoord dat u voor de naam van een cmdlet kiest rapportgebruiker. Gebruik bijvoorbeeld de naam van de `Get-Process` in plaats van **Get-processen**. Het is raadzaam om te volgen met deze regel voor alle namen van de cmdlet, zelfs wanneer een cmdlet is het waarschijnlijk om te reageren op meer dan één item.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Use-Case Pascal voor Cmdlet-namen (SD02)

Pascal gebruiksvoorbeeld voor de namen van parameters. De eerste letter van de bewerking en alle termen die in het zelfstandig naamwoord gebruikt met andere woorden, een hoofdletter. Bijvoorbeeld, "`Clear-ItemProperty`'.

### <a name="parameter-design-guidelines-sd03"></a>Richtlijnen voor het ontwerpen parameter (SD03)

Een cmdlet moet parameters die de gegevens op die deze moet functioneren ontvangen en parameters die duiden op informatie die wordt gebruikt om te bepalen van de kenmerken van de bewerking. Bijvoorbeeld, een cmdlet mogelijk een `Name` parameter die gegevens van de pijplijn en de cmdlet ontvangt mogelijk een `Force` parameter om aan te geven dat de cmdlet kan worden gedwongen de bewerking uit te voeren. Er is geen limiet voor het aantal parameters die een cmdlet kunt definiëren.

#### <a name="use-standard-parameter-names"></a>Standard parameternamen gebruiken

De cmdlet moet standaard parameternamen gebruiken zodat de gebruiker kan snel bepalen wat een bepaalde parameter betekent. Als een specifiekere naam vereist is, gebruikt u een standard parameternaam en vervolgens een specifiekere naam als een alias opgeven. Bijvoorbeeld, de `Get-Service` cmdlet heeft een parameter waarvoor een algemene naam (`Name`) en een meer specifieke alias (`ServiceName`). Beide termen kunnen worden gebruikt om op te geven van de parameter.

Zie voor meer informatie over de namen van parameters en hun gegevenstypen, [functionaliteit richtlijnen en naam van de Cmdlet-Parameter](./standard-cmdlet-parameter-names-and-types.md).

#### <a name="use-singular-parameter-names"></a>Enkelvoudige parameternamen gebruiken

Vermijd het gebruik van meervoudige namen voor parameters waarvan de waarde één element is. Dit omvat parameters die matrices of een lijst met omdat de gebruiker mogelijk een matrix of een lijst met slechts één element opgeven.

Plural parameternamen moeten alleen worden gebruikt in die gevallen waarin de waarde van de parameter altijd een waarde met meerdere elementen. In dergelijke gevallen moet de cmdlet controleren of dat meerdere elementen worden aangeleverd, en de cmdlet moet een waarschuwing worden weergegeven voor de gebruiker als meerdere elementen zijn niet opgegeven.

#### <a name="use-pascal-case-for-parameter-names"></a>Use-Case Pascal voor namen van parameters

Pascal gebruiksvoorbeeld voor de namen van parameters. Met andere woorden, de eerste letter van elk woord in de parameternaam, inclusief de eerste letter van de naam met een hoofdletter. Bijvoorbeeld: de parameternaam `ErrorAction` maakt gebruik van het juiste hoofdlettergebruik. Onjuist hoofdlettergebruik gebruikt u de parameternamen van de volgende:

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>Parameters die een lijst met opties nemen

Er zijn twee manieren om te maken van een parameter waarvan de waarde kan worden geselecteerd uit een set met opties.

- Definieer een opsommingstype (of gebruik een bestaande opsommingstype) Hiermee worden de geldige waarden. Vervolgens gebruikt u het opsommingstype maken van een parameter van dat type.

- Voeg de **ValidateSet** aan de parameterdeclaratie van het kenmerk. Zie voor meer informatie over dit kenmerk [ValidateSet kenmerkdeclaratie](./validateset-attribute-declaration.md).

#### <a name="use-standard-types-for-parameters"></a>Standard typen voor Parameters gebruiken

Om te zorgen voor consistentie met andere cmdlets, gebruikt u standard typen voor parameters waar ooit mogelijk. Zie voor meer informatie over de typen die moet worden gebruikt voor andere parameter [standaard Cmdlet-parameternamen en typen](./standard-cmdlet-parameter-names-and-types.md). In dit onderwerp vindt u koppelingen naar diverse onderwerpen waarin wordt beschreven van de namen en typen van .NET Framework voor groepen van standard parameters, zoals de 'activiteitsparameters'.

#### <a name="use-strongly-typed-net-framework-types"></a>Gebruik van sterk getypeerde .NET Framework-typen

Parameters moeten worden gedefinieerd als .NET Framework-typen voor betere validatie van de parameter. Parameters die zijn beperkt tot één waarde uit een set waarden moeten bijvoorbeeld worden gedefinieerd als een opsommingstype. Ter ondersteuning van een Uniform Resource Identifier (URI)-waarde, definieert u de parameter als een [System.Uri](/dotnet/api/System.Uri) type. Vermijd basic queryreeksparameters voor eigenschappen van alle vrije tekst.

#### <a name="use-consistent-parameter-types"></a>Consistente parametertypen gebruiken

Wanneer dezelfde parameter wordt gebruikt door meerdere cmdlets, moet u altijd hetzelfde parametertype gebruiken.  Bijvoorbeeld, als de `Process` parameter is een [System.Int16](/dotnet/api/System.Int16) typt u voor een cmdlet, moet u geen maken de `Process` parameter voor een andere cmdlet een [System.Uint16](/dotnet/api/System.UInt16) type.

#### <a name="parameters-that-take-true-and-false"></a>Parameters die True en False

Als de parameter alleen wordt `true` en `false`, definieert u de parameter als type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter). Een switch-parameter wordt beschouwd als `true` wanneer deze is opgegeven in een opdracht. Als de parameter niet is opgenomen in een opdracht, Windows PowerShell rekening gehouden met de waarde van de parameter `false`. Definieer geen Booleaanse parameters.

Als de parameter moet onderscheid maken tussen de 3 waarden: $true, $false en 'Onbekende', definieert u een parameter van het type null-waarden bevatten\<bool >.  De noodzaak voor een 3rd 'Onbekende' waarde treedt meestal op wanneer de cmdlet een Boole-eigenschap van een object kunt wijzigen. In dit geval 'Onbekende' betekent dat de huidige waarde van de eigenschap niet wijzigen.

#### <a name="support-arrays-for-parameters"></a>Ondersteuning voor Arrays voor Parameters

Gebruikers moeten vaak dezelfde bewerking op basis van meerdere argumenten uitvoeren. Voor deze gebruikers moet een cmdlet een matrix accepteren als parameter invoeren zodat een gebruiker kan de argumenten worden doorgegeven in de parameter als een Windows PowerShell-variabele. Bijvoorbeeld, de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet een matrix wordt gebruikt voor de tekenreeksen die identificeren de namen van de processen om op te halen.

#### <a name="support-the-passthru-parameter"></a>Ondersteuning voor de Parameter PassThru gebruikt

Standaard veel cmdlets die wijzigen het systeem, zoals de [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet, fungeren als 'sinks' voor objecten en geen resultaat geretourneerd. Deze cmdlet moet implementeren de `PassThru` parameter om af te dwingen van de cmdlet om een object te retourneren. Wanneer de `PassThru` parameter is opgegeven, wordt de cmdlet retourneert een object met behulp van een aanroep naar de [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) methode. Bijvoorbeeld de volgende opdracht wordt het proces Calc beëindigd en wordt het resulterende proces doorgegeven aan de pijplijn.

```powershell
Stop-Process calc -passthru
```

In de meeste gevallen toevoegen, instellen en nieuwe cmdlets moet ondersteunen een `PassThru` parameter.

#### <a name="support-parameter-sets"></a>Ondersteuning voor parametersets

Een cmdlet is bedoeld om uit te voeren van één doel. Er is echter vaak meer dan één manier om de bewerking of doel van de bewerking te beschrijven. Een proces kan bijvoorbeeld worden geïdentificeerd door de naam, door de id of door een procesobject. De cmdlet moet ondersteuning bieden voor alle redelijke voorstellingen van de doelen. De cmdlet aan normaal gesproken deze vereiste voldoet door sets met parameters (aangeduid als parametersets) wordt uitgevoerd en die worden uitgevoerd bij elkaar op te geven. Één parameter kan deel uitmaken van een willekeurig aantal parametersets. Zie voor meer informatie over parametersets [Cmdlet-Parameter stelt](./cmdlet-parameter-sets.md).

Wanneer u parametersets opgeeft, stelt u slechts één parameter in de set ValueFromPipeline. Voor meer informatie over hoe u declareert de **Parameter** kenmerk, Zie [ParameterAttribute declaratie](./parameter-attribute-declaration.md).

Wanneer parametersets worden gebruikt, de standaardset van de parameter wordt gedefinieerd door de **Cmdlet** kenmerk. De standaardset van de parameter moet de meest waarschijnlijke moet worden gebruikt in een interactieve Windows PowerShell-sessie parameters bevatten. Voor meer informatie over hoe u declareert de **Cmdlet** kenmerk, Zie [CmdletAttribute declaratie](./cmdlet-attribute-declaration.md).

### <a name="provide-feedback-to-the-user-sd04"></a>Feedback geven aan de gebruiker (SD04)

Gebruik de richtlijnen in deze sectie om feedback te geven aan de gebruiker. Deze feedback kan de gebruiker die u moet weten wat in het systeem gebeurt en om beter met beheerdersrechten beslissingen te nemen.

De Windows PowerShell-runtime kan een gebruiker kunt u opgeven hoe voor het afhandelen van uitvoer van elke aanroep naar de `Write` methode door in te stellen van een voorkeursvariabele. De gebruiker kan verschillende voorkeursvariabelen, met inbegrip van een variabele waarmee wordt bepaald of het systeem moet worden weergegeven informatie en een variabele waarmee wordt bepaald of het systeem een query moet de gebruiker voordat u verdere actie onderneemt instellen.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>Ondersteuning voor de WriteWarning, WriteVerbose en WriteDebug methoden

Er moet een cmdlet aanroepen de [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) methode wanneer de cmdlet wordt een bewerking die mogelijk een onbedoelde resultaat. Bijvoorbeeld, een cmdlet moet deze methode niet aanroepen als de cmdlet is een alleen-lezenbestand overschrijven.

Er moet een cmdlet aanroepen de [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) methode als voor de gebruiker is vereist voor sommige details over de cmdlet wordt uitgevoerd. Bijvoorbeeld, een cmdlet die deze informatie moet aanroepen, als de auteur van de cmdlet vindt dat er scenario's die mogelijk meer informatie zijn over de cmdlet wordt uitgevoerd.

De cmdlet moet aanroepen de [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) methode wanneer u een developer- of ondersteuningsmedewerker moet begrijpen wat de cmdlet-bewerking is beschadigd. Het is niet nodig voor de cmdlet om aan te roepen de [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) methode in dezelfde code roept de [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) methode omdat de `Debug` parameter geeft u beide sets met informatie.

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>Ondersteuning voor WriteProgress voor bewerkingen die lange tijd duren

Bewerkingen van de cmdlet die duurt lang duren om uit te voeren en die kan niet worden uitgevoerd op de achtergrond moet ondersteunen voortgangsrapportage via periodieke aanroepen naar de [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) methode.

#### <a name="use-the-host-interfaces"></a>Gebruik van de hostinterfaces

Af en toe een cmdlet moet communiceren rechtstreeks met de gebruiker in plaats van met behulp van de verschillende schrijven, of moeten de methoden die worden ondersteund door de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasse. In dit geval wordt de cmdlet moet zijn afgeleid van de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasse en het gebruik van de [System.Management.Automation.PSCmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) eigenschap. Deze eigenschap ondersteunt verschillende niveaus van het communicatietype, met inbegrip van de typen PromptForChoice-Prompt en WriteLine/ReadLine. Op het meest specifiek niveau, het biedt ook manieren om te lezen en schrijven van afzonderlijke sleutels en buffers zijn getroffen.

Tenzij een cmdlet is speciaal ontworpen voor het genereren van een grafische gebruikersinterface (GUI), moet deze de host niet overslaan met behulp van de [System.Management.Automation.PSCmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) eigenschap. Een voorbeeld van een cmdlet die is ontworpen voor het genereren van een GUI is de [Out GridView](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) cmdlet.

> [!NOTE]
> Cmdlets gebruik niet de [System.Console](/dotnet/api/System.Console) API.

### <a name="create-a-cmdlet-help-file-sd05"></a>Maken van een Cmdlet Help-bestand (SD05)

Maak een Help.xml-bestand dat informatie over de cmdlet bevat voor elke cmdlet-assembly. Deze informatie bevat een beschrijving van de cmdlet, beschrijvingen van parameters van de cmdlet, voorbeelden van het gebruik van de cmdlet, en meer.

## <a name="code-guidelines"></a>Code-richtlijnen

De volgende richtlijnen moeten worden gevolgd bij het coderen van cmdlets om te controleren of een consistente gebruikerservaring tussen het gebruik van de cmdlets en andere cmdlets. Als u een Code-richtlijn die van toepassing op uw situatie is, moet u kijken naar de richtlijnen voor het ontwerpen voor vergelijkbare richtlijnen.

### <a name="coding-parameters-sc01"></a>Parameters (SC01) coderen

Een parameter definiëren door op te geven van een openbare eigenschap van de cmdlet-klasse die is voorzien van de **Parameter** kenmerk. Parameters hoeft niet te worden van statische leden van de afgeleide klasse voor .NET Framework voor de cmdlet. Voor meer informatie over hoe u declareert de **Parameter** kenmerk, Zie [kenmerk parameterdeclaratie](./parameter-attribute-declaration.md).

#### <a name="support-windows-powershell-paths"></a>Ondersteuning voor Windows PowerShell-paden

Het pad van de Windows PowerShell is het mechanisme voor het normaliseren van toegang tot naamruimten. Wanneer u een Windows PowerShell-pad naar een parameter in de cmdlet toewijst, kan de gebruiker een aangepaste 'maken' die als een snelkoppeling naar een specifiek pad fungeert kunt definiëren. Wanneer een gebruiker die een station, kan de opgeslagen gegevens, zoals gegevens in het register worden gebruikt in een consistente manier.

Als de cmdlet kan de gebruiker een bestand of een gegevensbron op te geven, moet deze een parameter van het type definiëren [System.String](/dotnet/api/System.String). Als meer dan één station wordt ondersteund, is het type moet een matrix. De naam van de parameter moet `Path`, met een alias van `PSPath`. Bovendien de `Path` parameter moet ondersteuning bieden voor jokertekens bevatten. Als de ondersteuning voor jokertekens is niet vereist, het definiëren van een `LiteralPath` parameter.

Als de gegevens die de cmdlet leest of schrijft om te worden van een bestand is, wordt de cmdlet Windows PowerShell pad invoer accepteren moet en moet worden gebruikt door de cmdlet de [System.Management.Automation.Sessionstate.Path](/dotnet/api/System.Management.Automation.SessionState.Path) eigenschap voor de omzetting van de Windows PowerShell-paden in de paden die door het bestandssysteem herkend. De specifieke mechanismen zijn onder andere de volgende methoden:

- [System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

Als de gegevens die de cmdlet leest of schrijft alleen is een reeks tekenreeksen in plaats van een bestand, de cmdlet moet gebruiken de gegevens van de provider-inhoud (`Content` lid) te lezen en schrijven. Deze informatie wordt opgehaald uit de [System.Management.Automation.Provider.CmdletProvider.InvokeProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) eigenschap. Deze mechanismen kunnen andere gegevensarchieven deel te nemen aan het lezen en schrijven van gegevens.

#### <a name="support-wildcard-characters"></a>Ondersteuning voor jokertekens

Jokertekens moet indien mogelijk ondersteuning voor een cmdlet. Ondersteuning voor jokertekens vindt plaats op talloze plaatsen in een cmdlet (met name als een parameter een tekenreeks om een object van een set van objecten te identificeren duurt). Bijvoorbeeld, het voorbeeld **Stop-Proc** cmdlet uit de [StopProc zelfstudie](./stopproc-tutorial.md) definieert een `Name` parameter voor het afhandelen van tekenreeksen die staan voor procesnamen. Deze parameter ondersteunt jokertekens bevatten, zodat de gebruiker eenvoudig voor de processen opgeven kan te stoppen.

Wanneer ondersteuning voor jokertekens tekens beschikbaar is, een bewerking cmdlet levert meestal een matrix. Van tijd tot tijd, is het niet verstandig ter ondersteuning van een matrix, omdat de gebruiker kan slechts één item tegelijk gebruiken. Bijvoorbeeld, de [locatie instellen](/powershell/module/Microsoft.PowerShell.Management/Set-Location) cmdlet niet hoeft te ondersteunen, een matrix omdat de gebruiker is bezig met slechts één locatie. In dit geval de cmdlet nog steeds jokertekens worden ondersteund, maar het zorgt ervoor dat het probleem zou moeten op één locatie.

Zie voor meer informatie over jokerteken patronen [jokertekens in de Cmdlet-Parameters ondersteunende](./supporting-wildcard-characters-in-cmdlet-parameters.md).

#### <a name="defining-objects"></a>Objecten definiëren

In deze sectie bevat richtlijnen voor het definiëren van objecten voor cmdlets en voor het uitbreiden van bestaande objecten.

##### <a name="define-standard-members"></a>Standard leden definiëren

Standard leden om uit te breiden een objecttype dat in een aangepaste Types.ps1xml-bestand (Gebruik de Windows PowerShell Types.ps1xml-bestand als een sjabloon) definiëren. Standard leden worden gedefinieerd door een knooppunt met de naam PSStandardMembers. Deze definities kunnen andere cmdlets en de Windows PowerShell-runtime werken met het object in een consistente manier.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>ObjectMembers moet worden gebruikt als Parameters definiëren

Als u het ontwerpen van een object voor een cmdlet, zorgt u ervoor dat de leden ervan rechtstreeks toegewezen aan de parameters van de cmdlets die wordt gebruikt. Deze toewijzing kan het object eenvoudig worden verzonden naar de pijplijn en van een cmdlet worden doorgegeven aan een andere.

Bestaande .NET Framework-objecten die worden geretourneerd door cmdlets ontbreken enkele belangrijke of handige leden die nodig zijn voor het script developer of de gebruiker vaak. Deze ontbrekende leden kunnen zich met name belangrijk om weer te geven en voor het maken van het lid van de juiste namen zodat het object correct kan worden doorgegeven aan de pijplijn. Maak een aangepaste Types.ps1xml-bestand om deze vereiste leden. Wanneer u dit bestand maakt, wordt aangeraden de volgende naamconventie gebruikt: *< Your_Product_Name >*. Types.ps1xml.

Bijvoorbeeld zou u een `Mode` script eigenschap in op de [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) om de kenmerken van een bestand duidelijker weer te geven. Bovendien zou u een `Count` alias-eigenschap op de [System.Array](/dotnet/api/System.Array) type om het consistent gebruik van de naam van die eigenschap (in plaats van `Length`).

##### <a name="implement-the-icomparable-interface"></a>De interface van de IComparable

Implementeer een [System.IComparable](/dotnet/api/System.IComparable) -interface op alle objecten van de uitvoer. Hiermee wordt de uitvoer-objecten voor eenvoudig worden doorgesluisd naar verschillende sorteer- en analyse-cmdlets.

##### <a name="update-display-information"></a>Weergave-informatie bijwerken

Als de weergave voor een object niet de verwachte resultaten biedt, maakt u een aangepaste  *\<YourProductName >*. Format.ps1xml-bestand voor dat object.

### <a name="support-well-defined-pipeline-input-sc02"></a>Ondersteuning van goed gedefinieerde Pijpleidinginvoer (SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>Implementeren voor het midden van een pijplijn

Implementeren van een cmdlet ervan uitgaande dat het wordt aangeroepen vanaf het midden van een pijplijn (dat wil zeggen, andere cmdlets wordt produceren invoer of uitvoer ervan gebruiken). Bijvoorbeeld, u mogelijk wordt ervan uitgegaan dat de `Get-Process` cmdlet, omdat deze gegevens, genereert alleen als de eerste cmdlet in een pijplijn wordt gebruikt. Omdat deze cmdlet is ontworpen voor het midden van een pijplijn, kan deze cmdlet echter vorige cmdlets of gegevens in de pijplijn om op te geven van de processen om op te halen.

#### <a name="support-input-from-the-pipeline"></a>Ondersteuning voor invoer van de pijplijn

In elke parameter ingesteld voor een cmdlet, zoals ten minste één parameter die ondersteuning biedt voor invoer van de pijplijn. Ondersteuning voor invoer van de pijplijn kan de gebruiker gegevens of objecten, verzend dit naar de juiste parameter is ingesteld, en om door te geven van de resultaten rechtstreeks aan een cmdlet ophalen.

Een parameter accepteert invoer van de pijplijn als de **Parameter** kenmerk bevat de `ValueFromPipeline` trefwoord, de `ValueFromPipelineByPropertyName` sleutelwoord kenmerk of beide trefwoorden in de declaratie ervan. Als geen van de parameters in een parameter ondersteuning stelt de `ValueFromPipeline` of `ValueFromPipelineByPropertyName` trefwoorden, de cmdlet kunnen niet zinvolle na een andere cmdlet worden geplaatst omdat het invoer van een pijplijn wordt genegeerd.

#### <a name="support-the-processrecord-method"></a>Ondersteuning voor de methode ProcessRecord

Voor het accepteren van alle records uit de vorige cmdlet in de pijplijn de cmdlet moet worden geïmplementeerd de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode. Windows PowerShell wordt deze methode meerdere keren één keer voor elke record die wordt verzonden aan uw cmdlet.

### <a name="write-single-records-to-the-pipeline-sc03"></a>Schrijven van afzonderlijke Records aan de pijplijn (SC03)

Wanneer een cmdlet objecten retourneert, de cmdlet moet worden gebruikt voor het schrijven van de objecten onmiddellijk nadat ze zijn gegenereerd. De cmdlet moet ze niet bevatten om ze in een gecombineerde matrix van de buffer. De cmdlets die de objecten worden weergegeven als invoer wordt vervolgens mogelijk zijn om te verwerken, weergeven, of verwerken en de uitvoer-objecten onmiddellijk weergegeven. Een cmdlet die uitvoer genereert objecten één voor één moet aanroepen de [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) methode. Een cmdlet die objecten uitvoer gegenereerd in batches (bijvoorbeeld, omdat een onderliggende API een matrix met objecten van de uitvoer retourneert) moet aanroepen de [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) met de tweede parameter is ingesteld naar `true`.

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Controleer de Cmdlets niet hoofdlettergevoelig en (SC04) met een aanvraag te behouden

Windows PowerShell zelf is standaard niet hoofdlettergevoelig. Omdat deze met veel bestaande systemen omgaat, Windows PowerShell echter behouden in geval gemakkelijker te maken van de bewerking en compatibiliteit. Met andere woorden, als een teken wordt geleverd in hoofdletters, Windows PowerShell, blijft het in hoofdletters. Voor systemen om goed werken, moet een cmdlet volgt u deze overeenkomst. Indien mogelijk moet deze worden uitgevoerd op een niet-hoofdlettergevoelige manier. Het moet echter behouden de oorspronkelijke aanvraag voor de cmdlets die later in een opdracht of in de pijplijn.

## <a name="see-also"></a>Zie ook

[Richtlijnen voor vereiste ontwikkeling](./required-development-guidelines.md)

[Richtlijnen voor advies ontwikkeling](./advisory-development-guidelines.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
