---
title: Sterk aangeraden ontwikkel richtlijnen | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 02488fea557b42ed30ea5cfde177b3efe0b3f559
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787815"
---
# <a name="strongly-encouraged-development-guidelines"></a>Zeer aangeraden richtlijnen voor de ontwikkeling

In deze sectie worden richt lijnen beschreven die u moet volgen wanneer u uw cmdlets schrijft. Ze zijn onderverdeeld in richt lijnen voor het ontwerpen van cmdlets en richt lijnen voor het schrijven van uw cmdlet-code. Het kan voor komen dat deze richt lijnen niet van toepassing zijn op elk scenario. Als ze echter wel van toepassing zijn en u deze richt lijnen niet volgt, hebben uw gebruikers mogelijk een slechte ervaring wanneer ze uw cmdlets gebruiken.

## <a name="design-guidelines"></a>Ontwerp richtlijnen

- [Een specifiek zelfstandig naam woord gebruiken voor een Cmdletnaam (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Pascal-cases gebruiken voor cmdlet-namen (SD02)](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [Richt lijnen voor het ontwerpen van para meters (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [Feedback geven aan de gebruiker (SD04)](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Een Help-bestand voor cmdlets maken (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>Code richtlijnen

- [Code-para meters (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [Ondersteuning van goed gedefinieerde pijplijn invoer (SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [Eén record naar de pijp lijn schrijven (SC03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Cmdlets hoofdletter gevoelig maken en case-behoud (SC04)](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>Ontwerp richtlijnen

De volgende richt lijnen moeten worden gevolgd bij het ontwerpen van cmdlets om een consistente gebruikers ervaring te garanderen tussen het gebruik van uw cmdlets en andere cmdlets. Als u een ontwerp richtlijn vindt die van toepassing is op uw situatie, raadpleegt u de code richtlijnen voor vergelijk bare richt lijnen.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>Een specifiek zelfstandig naam woord gebruiken voor een Cmdletnaam (SD01)

Zelfstandige naam woorden die worden gebruikt voor de naamgeving van de cmdlet moeten zeer specifiek zijn, zodat de gebruiker uw cmdlets kan detecteren. Voor voegsel van algemene zelfstandige naam woorden, zoals ' server ', met een kortere versie van de product naam. Als een zelfstandig naam woord bijvoorbeeld verwijst naar een server waarop een exemplaar van Microsoft SQL Server, gebruikt u een zelfstandignaam zoals ' SQLServer '. De combi natie van specifieke samen stellingen en de korte lijst met goedgekeurde werk woorden stelt de gebruiker in staat om snel te ontdekken en te anticiperen op functionaliteit, terwijl dubbele namen van cmdlets worden vermeden.

Als u de gebruikers ervaring wilt verbeteren, moet u een zelfstandig naam woord opgeven voor een cmdletnaam. Gebruik bijvoorbeeld de naam `Get-Process` in plaats van **Get-processen**. U kunt deze regel het beste voor alle namen van cmdlets volgen, zelfs wanneer een cmdlet waarschijnlijk op meer dan één item reageert.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Pascal-cases gebruiken voor cmdlet-namen (SD02)

Gebruik Pascal cases voor parameter namen. Met andere woorden, de eerste letter van de term en alle termen die worden gebruikt in het zelfstandig naam woord. Bijvoorbeeld `Clear-ItemProperty`.

### <a name="parameter-design-guidelines-sd03"></a>Richt lijnen voor het ontwerpen van para meters (SD03)

Een cmdlet heeft para meters nodig die de gegevens ontvangen waarop het moet worden uitgevoerd, en para meters die informatie geven die wordt gebruikt om de kenmerken van de bewerking te bepalen. Een cmdlet kan bijvoorbeeld een `Name` para meter hebben waarmee gegevens worden ontvangen van de pijp lijn en de cmdlet kan een `Force` para meter hebben om aan te geven dat de cmdlet kan worden geforceerd om de bewerking uit te voeren. Er is geen limiet voor het aantal para meters dat een cmdlet kan definiëren.

#### <a name="use-standard-parameter-names"></a>Standaard parameter namen gebruiken

De cmdlet moet standaard parameter namen gebruiken, zodat de gebruiker snel kan bepalen wat een bepaalde para meter aangeeft. Als een meer specifieke naam vereist is, gebruikt u een standaard parameter naam en geeft u een specifieke naam op als alias. De `Get-Service` cmdlet heeft bijvoorbeeld een para meter met een algemene naam ( `Name` ) en een meer specifieke alias ( `ServiceName` ). Beide termen kunnen worden gebruikt om de para meter op te geven.

Zie [cmdlet-parameter naam en-functionaliteit](./standard-cmdlet-parameter-names-and-types.md)voor meer informatie over parameter namen en de bijbehorende gegevens typen.

#### <a name="use-singular-parameter-names"></a>Enkelvouds parameter namen gebruiken

Vermijd het gebruik van meervouds namen voor para meters waarvan de waarde één element is. Dit omvat para meters die matrices of lijsten maken, omdat de gebruiker een matrix of lijst met slechts één element kan leveren.

Meervouds parameter namen mogen alleen worden gebruikt in gevallen waarin de waarde van de para meter altijd een waarde met meerdere elementen is. In deze gevallen moet de cmdlet controleren of er meerdere elementen zijn opgegeven en moet de cmdlet een waarschuwing voor de gebruiker weer geven als er geen meerdere elementen zijn opgegeven.

#### <a name="use-pascal-case-for-parameter-names"></a>Pascal-cases gebruiken voor parameter namen

Gebruik Pascal cases voor parameter namen. Met andere woorden, met de eerste letter van elk woord in de parameter naam, met inbegrip van de eerste letter van de naam. De naam van de para meter `ErrorAction` gebruikt bijvoorbeeld het juiste hoofdletter gebruik. De volgende parameter namen gebruiken een onjuist hoofdletter gebruik:

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>Para meters die een lijst met opties maken

Er zijn twee manieren om een para meter te maken waarvan de waarde kan worden geselecteerd uit een set opties.

- Definieer een opsommings type (of gebruik een bestaand opsommings type) dat de geldige waarden opgeeft. Gebruik vervolgens het opsommings type om een para meter van dat type te maken.

- Voeg het kenmerk **Validate** toe aan de parameter declaratie. Zie [Validate kenmerk Declaration](./validateset-attribute-declaration.md)voor meer informatie over dit kenmerk.

#### <a name="use-standard-types-for-parameters"></a>Standaard typen voor para meters gebruiken

Gebruik voor de consistentie met andere cmdlets standaard typen voor para meters die ooit mogelijk zijn. Zie voor meer informatie over de typen die moeten worden gebruikt voor de verschillende para meters [standaard-cmdlet-parameter namen en-typen](./standard-cmdlet-parameter-names-and-types.md). In dit onderwerp vindt u koppelingen naar verschillende onderwerpen waarin de namen en .NET Framework typen worden beschreven voor groepen van standaard parameters, zoals de ' activiteit parameters '.

#### <a name="use-strongly-typed-net-framework-types"></a>Sterk getypeerde .NET Framework typen gebruiken

Para meters moeten worden gedefinieerd als .NET Framework typen voor een betere validatie van de para meters. Para meters die zijn beperkt tot één waarde uit een set waarden, moeten bijvoorbeeld worden gedefinieerd als een opsommings type. Als u een URI-waarde (Uniform Resource Identifier) wilt ondersteunen, definieert u de para meter als een [System. URI](/dotnet/api/System.Uri) -type. Vermijd Basic string-para meters voor alle eigenschappen van een vrije-vorm tekst.

#### <a name="use-consistent-parameter-types"></a>Consistente parameter typen gebruiken

Wanneer dezelfde para meter wordt gebruikt door meerdere cmdlets, moet u altijd hetzelfde parameter type gebruiken.  Als de `Process` para meter bijvoorbeeld een [System. Int16](/dotnet/api/System.Int16) -type is voor één cmdlet, mag u de `Process` para meter niet voor een andere cmdlet van het type [System. Uint16](/dotnet/api/System.UInt16) maken.

#### <a name="parameters-that-take-true-and-false"></a>Para meters die waar en ONWAAR doen

Als uw para meter alleen `true` en gebruikt `false` , definieert u de para meter als type [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter). Een para meter switch wordt beschouwd als `true` wanneer deze in een opdracht wordt opgegeven. Als de para meter niet is opgenomen in een opdracht, beschouwt Windows Power shell de waarde van de para meter `false` . Definieer geen Boole-para meters.

Als uw para meter onderscheid moet maken tussen drie waarden: $true, $false en ' niet opgegeven ', definieert u een para meter van het type nullable \<bool> .  De nood zaak van een derde, niet-opgegeven waarde treedt doorgaans op wanneer de cmdlet een Booleaanse eigenschap van een object kan wijzigen. In dit geval betekent "niet opgegeven" dat de huidige waarde van de eigenschap niet kan worden gewijzigd.

#### <a name="support-arrays-for-parameters"></a>Ondersteunings matrices voor para meters

Gebruikers moeten vaak dezelfde bewerking uitvoeren op meerdere argumenten. Voor deze gebruikers moet een cmdlet een matrix als parameter invoer accepteren, zodat een gebruiker de argumenten kan door geven aan de para meter als een Windows Power shell-variabele. De cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) gebruikt bijvoorbeeld een matrix voor de teken reeksen die de namen van de op te halen processen identificeren.

#### <a name="support-the-passthru-parameter"></a>Ondersteuning voor de PassThru-para meter

Standaard kunnen veel cmdlets die het systeem wijzigen, zoals de cmdlet [Stop-process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) , fungeren als ' sinks ' voor-objecten en geen resultaten retour neren. Deze cmdlet moet de `PassThru` para meter implementeren om ervoor te zorgen dat de cmdlet een object retourneert. Wanneer de `PassThru` para meter is opgegeven, retourneert de cmdlet een-object met behulp van een aanroep van de methode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Met de volgende opdracht wordt het proces berekenen bijvoorbeeld gestopt en wordt het resulterende proces door gegeven aan de pijp lijn.

```powershell
Stop-Process calc -passthru
```

In de meeste gevallen moet het toevoegen, instellen en nieuwe cmdlets een `PassThru` para meter ondersteunen.

#### <a name="support-parameter-sets"></a>Parameter sets ondersteunen

Een cmdlet is bedoeld om één doel te bereiken. Er is echter vaak meer dan één manier om de bewerking of het doel van de bewerking te beschrijven. Een proces kan bijvoorbeeld worden geïdentificeerd door de naam, de id of door een proces object. De cmdlet moet alle redelijke weer gaven van de doelen ondersteunen. Normaal gesp roken voldoet de cmdlet aan deze vereiste door sets para meters (aangeduid als para meter sets) op te geven die samen werken. Een enkele para meter kan deel uitmaken van een wille keurig aantal parameter sets. Zie [cmdlet-parameter sets](./cmdlet-parameter-sets.md)voor meer informatie over parameter sets.

Wanneer u parameter sets opgeeft, stelt u slechts één para meter in de set in op ValueFromPipeline. Zie [ParameterAttribute-declaratie](./parameter-attribute-declaration.md)voor meer informatie over het declareren van het **parameter** kenmerk.

Wanneer er parameter sets worden gebruikt, wordt de standaard parameterset gedefinieerd door het kenmerk **cmdlet** . De standaard parameterset moet de para meters bevatten die waarschijnlijk worden gebruikt in een interactieve Windows Power shell-sessie. Zie [CmdletAttribute-declaratie](./cmdlet-attribute-declaration.md)voor meer informatie over het declareren van het **cmdlet** -kenmerk.

### <a name="provide-feedback-to-the-user-sd04"></a>Feedback geven aan de gebruiker (SD04)

Gebruik de richt lijnen in deze sectie om feedback te geven aan de gebruiker. Met deze feedback kan de gebruiker op de hoogte zijn van wat er in het systeem gebeurt en om betere administratieve beslissingen te nemen.

De Windows Power shell-runtime geeft een gebruiker de mogelijkheid om op te geven hoe de uitvoer van elke aanroep naar de methode moet worden afgehandeld `Write` door een voorkeurs variabele in te stellen. De gebruiker kan verschillende voorkeurs variabelen instellen, met inbegrip van een variabele die bepaalt of het systeem informatie moet weer geven en een variabele die bepaalt of het systeem een query moet uitvoeren op de gebruiker voordat verdere actie wordt ondernomen.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>De WriteWarning-, WriteVerbose-en WriteDebug-methoden ondersteunen

Een cmdlet moet de methode [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) aanroepen wanneer de cmdlet een bewerking uitvoert die een onbedoeld resultaat kan hebben. Een cmdlet moet bijvoorbeeld deze methode aanroepen als de cmdlet een alleen-lezen bestand overschrijft.

Een cmdlet moet de methode [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) aanroepen als de gebruiker enige details nodig heeft over wat de cmdlet uitvoert. Een cmdlet moet deze informatie bijvoorbeeld aanroepen als de maker van de cmdlet laat zien dat er scenario's zijn die mogelijk meer informatie nodig hebben over de werking van de cmdlet.

De cmdlet moet de methode [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) aanroepen wanneer een ontwikkelaar of producttechnische mede werker moet weten wat de cmdlet-bewerking heeft beschadigd. Het is niet nodig dat de cmdlet de methode [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) aanroept in dezelfde code die de methode [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) aanroept omdat de `Debug` para meter beide gegevens sets bevat.

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>Ondersteuning voor WriteProgress voor bewerkingen die veel tijd in beslag nemen

Cmdlet-bewerkingen die veel tijd in beslag nemen en die niet op de achtergrond kunnen worden uitgevoerd, moeten voortgangs rapporten ondersteunen via periodieke aanroepen naar de methode [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) .

#### <a name="use-the-host-interfaces"></a>De interfaces van de host gebruiken

In sommige gevallen moet een cmdlet rechtstreeks communiceren met de gebruiker in plaats van met behulp van de verschillende schrijf-of methode methoden die door de klasse [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) worden ondersteund. In dit geval moet de cmdlet worden afgeleid van de klasse [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) en de eigenschap [System. Management. Automation. PSCmdlet. host *](/dotnet/api/System.Management.Automation.PSCmdlet.Host) gebruiken. Deze eigenschap ondersteunt verschillende communicatie typen, waaronder de typen PromptForChoice, prompt en WriteLine/ReadLine. Op het meest specifieke niveau biedt het ook manieren om afzonderlijke sleutels te lezen en schrijven en om te omgaan met buffers.

Tenzij een cmdlet specifiek is ontworpen voor het genereren van een Graphical User Interface (GUI), mag de host niet worden omzeild met behulp van de eigenschap [System. Management. Automation. PSCmdlet. host *](/dotnet/api/System.Management.Automation.PSCmdlet.Host) . Een voor beeld van een cmdlet die is ontworpen om een GUI te genereren, is de [out-GridView-](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) cmdlet.

> [!NOTE]
> Cmdlets mogen de [System. console](/dotnet/api/System.Console) -API niet gebruiken.

### <a name="create-a-cmdlet-help-file-sd05"></a>Een Help-bestand voor cmdlets maken (SD05)

Maak voor elke cmdlet-assembly een Help.xml-bestand dat informatie over de cmdlet bevat. Deze informatie bevat een beschrijving van de cmdlet, beschrijvingen van de para meters van de cmdlet, voor beelden van het gebruik van de cmdlet en meer.

## <a name="code-guidelines"></a>Code richtlijnen

De volgende richt lijnen moeten worden gevolgd bij het coderen van cmdlets om een consistente gebruikers ervaring te garanderen tussen het gebruik van uw cmdlets en andere cmdlets. Wanneer u een code richtlijn vindt die van toepassing is op uw situatie, raadpleegt u de ontwerp richtlijnen voor vergelijk bare richt lijnen.

### <a name="coding-parameters-sc01"></a>Code-para meters (SC01)

Definieer een para meter door een open bare eigenschap van de cmdlet-klasse te declareren die is gedecoreerd met het **parameter** kenmerk. Para meters hoeven geen statische leden te zijn van de afgeleide .NET Framework klasse voor de cmdlet. Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie over het declareren van het **parameter** kenmerk.

#### <a name="support-windows-powershell-paths"></a>Ondersteuning voor Windows Power shell-paden

Het Windows Power shell-pad is het mechanisme voor het normaliseren van toegang tot naam ruimten. Wanneer u een Windows Power shell-pad toewijst aan een para meter in de cmdlet, kan de gebruiker een aangepast station definiëren dat fungeert als een snelkoppeling naar een specifiek pad. Wanneer een gebruiker een dergelijk station aanwijst, kunnen opgeslagen gegevens, zoals gegevens in het REGI ster, op een consistente manier worden gebruikt.

Als uw cmdlet toestaat dat de gebruiker een bestand of een gegevens bron opgeeft, moet er een para meter van het type [System. String](/dotnet/api/System.String)worden gedefinieerd. Als er meer dan één station wordt ondersteund, moet het type een matrix zijn. De naam van de para meter moet zijn `Path` , met een alias van `PSPath` . Daarnaast moet de `Path` para meter joker tekens ondersteunen. Als ondersteuning voor joker tekens niet is vereist, definieert u een `LiteralPath` para meter.

Als de gegevens die door de cmdlet worden gelezen of geschreven, een bestand moeten zijn, moet de cmdlet Windows Power shell-pad invoer accepteren. de cmdlet moet de eigenschap [System. Management. Automation. sessionState. Path](/dotnet/api/System.Management.Automation.SessionState.Path) gebruiken om de Windows Power shell-paden om te zetten in paden die het bestands systeem herkent. De specifieke mechanismen zijn onder andere de volgende methoden:

- [System. Management. Automation. PSCmdlet. GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System. Management. Automation. PSCmdlet. GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System. Management. Automation. PathIntrinsics. GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System. Management. Automation. PathIntrinsics. GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

Als de gegevens die door de cmdlet worden gelezen of geschreven, slechts een set teken reeksen zijn in plaats van een bestand, moet de cmdlet de inhouds informatie van de provider ( `Content` lid) gebruiken om te lezen en te schrijven. Deze informatie wordt opgehaald uit de eigenschap [System. Management. Automation. provider. CmdletProvider. InvokeProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) . Met deze mechanismen kunnen andere gegevens archieven deel nemen aan het lezen en schrijven van gegevens.

#### <a name="support-wildcard-characters"></a>Joker tekens ondersteunen

Een cmdlet moet zo mogelijk joker tekens ondersteunen. Ondersteuning voor joker tekens vindt plaats op veel plaatsen in een cmdlet (vooral wanneer een para meter een teken reeks gebruikt om een object van een set objecten te identificeren). De voor beeld van de cmdlet **Stop-proc** van de [zelf studie StopProc](./stopproc-tutorial.md) definieert een `Name` para meter voor het afhandelen van teken reeksen die proces namen vertegenwoordigen. Met deze para meter worden joker tekens ondersteund, zodat de gebruiker eenvoudig de processen kan opgeven die moeten worden gestopt.

Wanneer ondersteuning voor joker tekens beschikbaar is, produceert een cmdlet-bewerking meestal een matrix. In sommige gevallen is het niet zinvol een matrix te ondersteunen omdat de gebruiker slechts één item tegelijk kan gebruiken. Zo hoeft de cmdlet [Set-Location](/powershell/module/Microsoft.PowerShell.Management/Set-Location) geen matrix te ondersteunen omdat de gebruiker slechts één locatie instelt. In dit geval ondersteunt de cmdlet nog steeds joker tekens, maar worden oplossingen op één locatie afgedwongen.

Zie [ondersteuning voor joker tekens in cmdlet-para meters](./supporting-wildcard-characters-in-cmdlet-parameters.md)voor meer informatie over Joker teken patronen.

#### <a name="defining-objects"></a>Objecten definiëren

Deze sectie bevat richt lijnen voor het definiëren van objecten voor cmdlets en voor het uitbreiden van bestaande objecten.

##### <a name="define-standard-members"></a>Standaard leden definiëren

Standaard leden definiëren voor het uitbreiden van een object type in een aangepast Types.ps1XML-bestand (gebruik het Windows Power shell-Types.ps1XML-bestand als een sjabloon). Standaard leden worden gedefinieerd door een knoop punt met de naam PSStandardMembers. Met deze definities kunnen andere cmdlets en de Windows Power shell-runtime op een consistente manier werken met uw object.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>ObjectMembers definiëren die moeten worden gebruikt als para meters

Als u een-object ontwerpt voor een cmdlet, moet u ervoor zorgen dat de leden rechtstreeks zijn gekoppeld aan de para meters van de cmdlets die deze gaan gebruiken. Met deze toewijzing kan het object eenvoudig naar de pijp lijn worden verzonden en worden door gegeven van de ene cmdlet naar de andere.

Bestaande .NET Framework objecten die worden geretourneerd door cmdlets, missen vaak enkele belang rijke of handige leden die nodig zijn voor de script ontwikkelaar of gebruiker. Deze ontbrekende leden kunnen met name belang rijk zijn voor weer gave en voor het maken van de juiste lidnamen, zodat het object correct kan worden door gegeven aan de pijp lijn. Maak een aangepast Types.ps1XML-bestand om deze vereiste leden te documenteren. Wanneer u dit bestand maakt, raden we u aan de volgende naam Conventie toe te voegen: *<Your_Product_Name>*.Types.ps1XML.

U kunt bijvoorbeeld een `Mode` script eigenschap toevoegen aan het type [System. io. file info](/dotnet/api/System.IO.FileInfo) om de kenmerken van een bestand duidelijker weer te geven. Daarnaast kunt u een `Count` alias eigenschap toevoegen aan het type [System. array](/dotnet/api/System.Array) om het consistente gebruik van die eigenschaps naam (in plaats van) toe te staan `Length` .

##### <a name="implement-the-icomparable-interface"></a>Implementeer de interface IComparable

Implementeer een [System. IComparable](/dotnet/api/System.IComparable) -interface op alle uitvoer objecten. Hierdoor kunnen de uitvoer objecten eenvoudig worden gesluisd naar verschillende sorteer-en analyse-cmdlets.

##### <a name="update-display-information"></a>Weer gave-informatie bijwerken

Als de weer gave voor een object niet de verwachte resultaten geeft, maakt u een aangepast *\<YourProductName>*.Format.ps1XML-bestand voor dat object.

### <a name="support-well-defined-pipeline-input-sc02"></a>Ondersteuning van goed gedefinieerde pijplijn invoer (SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>Implementeren voor het midden van een pijp lijn

Implementeer een cmdlet, ervan uitgaande dat deze vanuit het midden van een pijp lijn wordt aangeroepen (dat wil zeggen dat andere cmdlets de invoer produceren of de uitvoer verbruiken). U kunt bijvoorbeeld aannemen dat de `Get-Process` cmdlet, omdat deze gegevens genereert, alleen wordt gebruikt als de eerste cmdlet in een pijp lijn. Omdat deze cmdlet echter is ontworpen voor het midden van een pijp lijn, kunnen met deze cmdlet eerdere cmdlets of gegevens in de pijp lijn worden opgegeven voor de processen die moeten worden opgehaald.

#### <a name="support-input-from-the-pipeline"></a>Invoer van de pijp lijn ondersteunen

Voor elke para meter die is ingesteld voor een cmdlet, moet u ten minste één para meter opgeven die invoer van de pijp lijn ondersteunt. Ondersteuning voor pijplijn invoer staat de gebruiker toe om gegevens of objecten op te halen, deze te verzenden naar de juiste parameterset en de resultaten rechtstreeks door te geven aan een cmdlet.

Een para meter accepteert invoer van de pijp lijn als het **parameter** kenmerk het `ValueFromPipeline` sleutel woord, het `ValueFromPipelineByPropertyName` Trefwoord kenmerk of beide sleutel woorden in de declaratie bevat. Als geen van de para meters in een para meter set ondersteuning biedt voor de `ValueFromPipeline` of `ValueFromPipelineByPropertyName` gereserveerde woorden, kan de cmdlet niet relevant worden geplaatst na een andere cmdlet, omdat alle pijplijn invoer wordt genegeerd.

#### <a name="support-the-processrecord-method"></a>Ondersteuning voor de methode ProcessRecord

Voor het accepteren van alle records uit de voor gaande cmdlet in de pijp lijn moet uw cmdlet de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) implementeren. Windows Power shell roept deze methode meerdere keren aan, één keer voor elke record die naar uw cmdlet wordt verzonden.

### <a name="write-single-records-to-the-pipeline-sc03"></a>Eén record naar de pijp lijn schrijven (SC03)

Wanneer een cmdlet objecten retourneert, moet de cmdlet de objecten onmiddellijk schrijven wanneer ze worden gegenereerd. De cmdlet mag niet worden ingecheckt om deze te bufferen in een gecombineerde matrix. De cmdlets die de objecten als invoer ontvangen, kunnen vervolgens de uitvoer objecten zonder vertraging verwerken, weer geven of verwerken en weer geven. Een cmdlet waarmee uitvoer objecten per keer worden gegenereerd moet de methode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) aanroepen. Een cmdlet waarmee uitvoer objecten worden gegenereerd in batches (bijvoorbeeld omdat een onderliggende API een matrix van uitvoer objecten retourneert) moet de methode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) aanroepen met de tweede para meter ingesteld op `true` .

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Cmdlets hoofdletter gevoelig maken en case-behoud (SC04)

Windows Power shell is standaard niet hoofdletter gevoelig. Omdat de IT-omgeving echter veel bestaande systemen behandelt, houdt Windows Power shell cases bij om de werking en compatibiliteit te vereenvoudigen. Met andere woorden, als een teken in hoofd letters wordt opgegeven, wordt het in Windows Power shell in hoofd letters bewaard. Voor een goede werking van systemen moet een cmdlet deze Conventie volgen. Als dat mogelijk is, moet deze op een niet-hoofdletter gevoelige manier worden uitgevoerd. De oorspronkelijke Case voor cmdlets die later in een opdracht of in de pijp lijn worden uitgevoerd, blijft echter behouden.

## <a name="see-also"></a>Zie ook

[Vereiste richtlijnen voor de ontwikkeling](./required-development-guidelines.md)

[Geadviseerde richtlijnen voor de ontwikkeling](./advisory-development-guidelines.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
