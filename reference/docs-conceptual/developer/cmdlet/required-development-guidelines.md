---
ms.date: 09/13/2016
ms.topic: reference
title: Vereiste richtlijnen voor de ontwikkeling
description: Vereiste richtlijnen voor de ontwikkeling
ms.openlocfilehash: 98db075b314eb7f54f2deb56022799d9f830f9ef
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655750"
---
# <a name="required-development-guidelines"></a>Vereiste richtlijnen voor de ontwikkeling

De volgende richt lijnen moeten worden gevolgd wanneer u uw cmdlets schrijft. Ze zijn onderverdeeld in richt lijnen voor het ontwerpen van cmdlets en richt lijnen voor het schrijven van uw cmdlet-code. Als u deze richt lijnen niet volgt, kunnen de cmdlets mislukken en kunnen uw gebruikers een slechte ervaring hebben wanneer ze uw cmdlets gebruiken.

## <a name="in-this-topic"></a>In dit onderwerp

### <a name="design-guidelines"></a>Ontwerprichtlijnen

- [Alleen goedgekeurde werk woorden gebruiken (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Cmdlet-namen: tekens die niet kunnen worden gebruikt (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Parameter namen die niet kunnen worden gebruikt (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Ondersteunings bevestigings aanvragen (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Ondersteuning voor Force-para meter voor interactieve sessies (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Document uitvoer objecten (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Code richtlijnen

- [Afgeleid van de cmdlet-of PSCmdlet-klassen (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [Het cmdlet-kenmerk (RC02) opgeven](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Een invoer verwerkings methode overschrijven (RC03)](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [Het kenmerk output type opgeven (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [Geen ingangen bewaren voor uitvoer objecten (RC05)](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Fouten op een robuuste manier afhandelen (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Een Windows Power shell-module gebruiken voor het implementeren van uw cmdlets (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Ontwerprichtlijnen

De volgende richt lijnen moeten worden gevolgd bij het ontwerpen van cmdlets om een consistente gebruikers ervaring te garanderen tussen het gebruik van uw cmdlets en andere cmdlets. Als u een ontwerp richtlijn vindt die van toepassing is op uw situatie, raadpleegt u de code richtlijnen voor vergelijk bare richt lijnen.

### <a name="use-only-approved-verbs-rd01"></a>Alleen goedgekeurde werk woorden gebruiken (RD01)

De opdracht die is opgegeven in het cmdlet-kenmerk moet afkomstig zijn uit de herkende set termen die worden geleverd door Windows Power shell. Het mag niet een van de verboden synoniemen zijn. Gebruik de constante teken reeksen die zijn gedefinieerd door de volgende opsommingen om cmdlet-termen op te geven:

- [System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Zie cmdlet-werk [woorden](./approved-verbs-for-windows-powershell-commands.md)voor meer informatie over de namen van goedgekeurde werk woorden.

Gebruikers moeten een set Detecteer bare en verwachte cmdlet-namen hebben. Gebruik de juiste opdracht, zodat de gebruiker een snelle beoordeling kan doen van wat een cmdlet doet en om eenvoudig de mogelijkheden van het systeem te ontdekken. De volgende opdracht regel opdracht haalt bijvoorbeeld een lijst op met alle opdrachten op het systeem waarvan de naam begint met ' Start ': `get-command start-*` . Gebruik de zelfstandige naam woorden in de cmdlets om uw cmdlets te onderscheiden van andere cmdlets. Het zelfstandig naam woord geeft de resource aan waarop de bewerking wordt uitgevoerd. De bewerking zelf wordt vertegenwoordigd door de term.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Cmdlet-namen: tekens die niet kunnen worden gebruikt (RD02)

Wanneer u een naam voor cmdlets gebruikt, mag u de volgende speciale tekens niet gebruiken.

|Teken|Naam|
|---------------|----------|
|#|nummer teken|
|,|Geplaatst|
|()|haakjes|
|{}|accolades|
|[]|haken|
|&|operator|
|-|afbreek streepje **:**  het koppel teken kan worden gebruikt om de term van het zelfstandig naam woord te scheiden, maar kan niet worden gebruikt binnen het zelfstandige zelfstandig of in de term.|
|/|slash-teken|
|\\| back slash|
|$|dollarteken|
|^|dakje|
|;|dubbele|
|:|punt|
|"|dubbel aanhalings teken|
|'|enkel aanhalings teken|
|<>|punt haken|
|&#124;|verticale balk|
|?|vraagteken|
|@|at-teken|
|`|schuine streep (accent grave)|
|*|sterretje|
|%|procent teken|
|+|plus teken|
|=|gelijkteken|
|~|tilde|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Parameter namen die niet kunnen worden gebruikt (RD03)

Windows Power shell biedt een gemeen schappelijke set para meters voor alle cmdlets plus aanvullende para meters die in bepaalde situaties worden toegevoegd. Bij het ontwerpen van uw eigen cmdlets kunt u de volgende namen niet gebruiken: bevestigen, fouten opsporen, error Action, ErrorVariable, outbuffer, outvariable, WarningAction, WarningVariable, WhatIf, UseTransaction en uitgebreid. Zie [common para meter names](./common-parameter-names.md)(Engelstalig) voor meer informatie over deze para meters.

### <a name="support-confirmation-requests-rd04"></a>Ondersteunings bevestigings aanvragen (RD04)

Voor cmdlets die een bewerking uitvoeren waardoor het systeem wordt gewijzigd, moeten ze de methode [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aanroepen om een bevestiging aan te vragen. in speciale gevallen wordt de methode [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aangeroepen. (De methode [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) moet alleen worden aangeroepen nadat de methode [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is aangeroepen.)

Als u deze aanroepen wilt maken, moet de cmdlet opgeven dat deze bevestigings aanvragen ondersteunt door het `SupportsShouldProcess` sleutel woord van het cmdlet-kenmerk in te stellen. Zie [cmdlet kenmerk declaratie](./cmdlet-attribute-declaration.md)voor meer informatie over het instellen van dit kenmerk.

> [!NOTE]
> Als het cmdlet-kenmerk van de klasse cmdlet aangeeft dat de cmdlet aanroepen ondersteunt naar de methode [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en de cmdlet de aanroep naar de methode [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) niet kan aanroepen, kan de gebruiker het systeem onverwacht wijzigen.

Gebruik de methode [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) voor elke wijziging van het systeem. Een gebruikers voorkeur en de `WhatIf` para meter bepalen de methode [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . De aanroep [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) voert daarentegen een extra controle uit op mogelijke schadelijke wijzigingen. Deze methode wordt niet beheerd door een gebruikers voorkeur of de `WhatIf` para meter. Als uw cmdlet de methode [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aanroept, moet deze een `Force` para meter hebben die de aanroepen naar deze twee methoden omzeilt en die de bewerking doorloopt. Dit is belang rijk omdat de cmdlet kan worden gebruikt in niet-interactieve scripts en hosts.

Als uw cmdlets ondersteuning bieden voor deze aanroepen, kan de gebruiker bepalen of de actie daad werkelijk moet worden uitgevoerd. De cmdlet [Stop-process](/powershell/module/microsoft.powershell.management/stop-process) roept bijvoorbeeld de methode [System. Management. Automation. cmdlet. ShouldContinue *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aan voordat een set kritieke processen wordt gestopt, met inbegrip van de systeem-, Winlogon-en Spoolsv-processen.

Zie [bevestiging aanvragen](./requesting-confirmation-from-cmdlets.md)voor meer informatie over het ondersteunen van deze methoden.

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Ondersteuning voor Force-para meter voor interactieve sessies (RD05)

Als uw cmdlet interactief wordt gebruikt, moet u altijd een Force-para meter opgeven voor het overschrijven van de interactieve acties, zoals prompts of het lezen van regels van invoer. Dit is belang rijk omdat de cmdlet kan worden gebruikt in niet-interactieve scripts en hosts. De volgende methoden kunnen worden geïmplementeerd door een interactieve host.

- [System. Management. Automation. host. PSHostUserInterface. prompt *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System. Management. Automation. host. Pshostuserinterface. PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System. Management. Automation. host. Ihostuisupportsmultiplechoiceselection. PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System. Management. Automation. host. Pshostuserinterface. PromptForCredential *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System. Management. Automation. host. Pshostuserinterface. ReadLine *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System. Management. Automation. host. Pshostuserinterface. ReadLineAsSecureString *](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Document uitvoer objecten (RD06)

Windows Power Shell maakt gebruik van de objecten die naar de pijp lijn zijn geschreven. Om gebruikers te laten profiteren van de objecten die door elke cmdlet worden geretourneerd, moet u de objecten die worden geretourneerd, documenteren en moet u documenteren waarvoor de leden van die geretourneerde objecten worden gebruikt.

## <a name="code-guidelines"></a>Code richtlijnen

De volgende richt lijnen moeten worden gevolgd bij het schrijven van de cmdlet-code. Wanneer u een code richtlijn vindt die van toepassing is op uw situatie, raadpleegt u de ontwerp richtlijnen voor vergelijk bare richt lijnen.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Afgeleid van de cmdlet-of PSCmdlet-klassen (RC01)

Een cmdlet moet worden afgeleid van de basis klasse [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) of [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . Cmdlets die zijn afgeleid van de klasse [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) zijn niet afhankelijk van de Windows Power shell-runtime. Ze kunnen rechtstreeks vanuit elke Microsoft .NET Framework-taal worden aangeroepen. Cmdlets die zijn afgeleid van de klasse [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) zijn afhankelijk van de Windows Power shell-runtime. Daarom worden ze binnen een runs Pace uitgevoerd.

Alle cmdlet-klassen die u implementeert, moeten open bare klassen zijn. Zie overzicht van de [cmdlet](./cmdlet-overview.md)voor meer informatie over deze cmdlet-klassen.

### <a name="specify-the-cmdlet-attribute-rc02"></a>Het cmdlet-kenmerk (RC02) opgeven

Voor een cmdlet die wordt herkend door Windows Power shell, moet de .NET Framework klasse zijn voorzien van het cmdlet-kenmerk. Met dit kenmerk geeft u de volgende functies van de cmdlet op.

- De combi natie van verb en samen stelling waarmee de cmdlet wordt geïdentificeerd.

- De standaard parameterset die wordt gebruikt wanneer meerdere parameter sets worden opgegeven. De standaard parameterset wordt gebruikt als Windows Power shell niet voldoende informatie heeft om te bepalen welke para meter moet worden gebruikt.

- Hiermee wordt aangegeven of de cmdlet aanroepen ondersteunt naar de methode [System. Management. Automation. cmdlet. ShouldProcess *](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Met deze methode wordt een bevestigings bericht voor de gebruiker weer gegeven voordat de cmdlet een wijziging in het systeem aanbrengt. Zie [verzoeken om bevestiging](./requesting-confirmation-from-cmdlets.md)voor meer informatie over de wijze waarop bevestigings aanvragen worden gedaan.

- Geef het impact niveau (of de ernst) aan van de actie die is gekoppeld aan het bevestigings bericht. In de meeste gevallen moet de standaard waarde van medium worden gebruikt. Voor meer informatie over hoe het impact niveau van invloed is op de bevestigings aanvragen die voor de gebruiker worden weer gegeven, raadpleegt u [bevestiging aanvragen](./requesting-confirmation-from-cmdlets.md).

Zie [CmdletAttribute-declaratie](./cmdlet-attribute-declaration.md)voor meer informatie over het declareren van het cmdlet-kenmerk.

### <a name="override-an-input-processing-method-rc03"></a>Een invoer verwerkings methode overschrijven (RC03)

Als u de cmdlet wilt gebruiken in de Windows Power shell-omgeving, moet deze ten minste één van de volgende *invoer verwerkings methoden* onderdrukken.

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) deze methode wordt één keer aangeroepen en wordt gebruikt om de functionaliteit van de voor verwerking te bieden.

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) deze methode wordt meerdere keren aangeroepen en wordt gebruikt om de functionaliteit van de record-voor-record te bieden.

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) deze methode wordt één keer aangeroepen en wordt gebruikt om een verwerkings functionaliteit te bieden.

### <a name="specify-the-outputtype-attribute-rc04"></a>Het kenmerk output type opgeven (RC04)

Het kenmerk output type (geïntroduceerd in Windows Power Shell 2,0) Hiermee geeft u de .NET Framework op die door de cmdlet wordt geretourneerd naar de pijp lijn. Door het uitvoer type van de cmdlets op te geven, maakt u de objecten die door de cmdlet worden geretourneerd, beter gedetecteerd door andere cmdlets. Zie output type- [kenmerk declaratie](./outputtype-attribute-declaration.md)voor meer informatie over het verf raaien van de cmdlet-klasse met dit kenmerk.

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>Geen ingangen bewaren voor uitvoer objecten (RC05)

De cmdlet mag geen ingangen behouden voor de objecten die worden door gegeven aan de methode [System. Management. Automation. cmdlet. WriteObject *](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Deze objecten worden door gegeven aan de volgende cmdlet in de pijp lijn of worden gebruikt door een script. Als u de ingangen naar de objecten behoudt, zullen twee entiteiten eigenaar zijn van elk object, waardoor fouten worden veroorzaakt.

### <a name="handle-errors-robustly-rc06"></a>Fouten op een robuuste manier afhandelen (RC06)

Een beheer omgeving detecteert en brengt belang rijke wijzigingen aan in het systeem dat u beheert. Daarom is het essentieel dat cmdlets fouten op de juiste wijze afhandelen. Zie [Windows Power shell Error Reporting](./error-reporting-concepts.md)(Engelstalig) voor meer informatie over fout records.

- Als een fout verhindert dat een cmdlet meer records verwerkt, is het een afsluit fout. De cmdlet moet de methode [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) aanroepen die verwijst naar een [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -object. Als een uitzonde ring niet wordt onderschept door de cmdlet, genereert de Windows Power shell-runtime zelf een afsluit fout die minder informatie bevat.

- Voor een niet-afsluit fout die geen bewerking stopt voor het volgende record dat afkomstig is van de pijp lijn (bijvoorbeeld een record die wordt geproduceerd door een ander proces), moet de cmdlet de methode [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aanroepen die verwijst naar een [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -object. Een voor beeld van een niet-afsluit fout is de fout die optreedt als een bepaald proces niet kan worden gestopt. Door de methode [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aan te roepen, kan de gebruiker consistent de gevraagde acties uitvoeren en de informatie bewaren voor bepaalde acties die mislukken. De cmdlet moet elke record zo onafhankelijk mogelijk verwerken.

- Het [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -object waarnaar wordt verwezen door de methoden [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) en [System. Management. Automation. cmdlet. WriteError *](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) , vereist een uitzonde ring op de kern. Volg de .NET Framework ontwerp richtlijnen wanneer u de uitzonde ring bepaalt die moet worden gebruikt. Als de fout semantisch gelijk is aan die van een bestaande uitzonde ring, moet u die uitzonde ring gebruiken of afleiden van die uitzonde ring. Anders moet u een nieuwe uitzonde ring of uitzonderings hiërarchie rechtstreeks van het type [System. Exception](/dotnet/api/System.Exception) afleiden.

Voor een object [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) is ook een fout categorie vereist waarin fouten voor de gebruiker worden gegroepeerd. De gebruiker kan fouten weer geven op basis van de categorie door de waarde van de `$ErrorView` shell-variabele in te stellen op CategoryView. De mogelijke categorieën worden gedefinieerd door de inventarisatie [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) .

- Als een cmdlet een nieuwe thread maakt en de code die in die thread wordt uitgevoerd, een niet-verwerkte uitzonde ring genereert, wordt de fout niet onderschept door Windows Power shell en wordt het proces beëindigd.

- Als een object code in de Destruct heeft die een niet-verwerkte uitzonde ring veroorzaakt, wordt de fout niet onderschept door Windows Power shell en wordt het proces beëindigd. Dit doet zich ook voor als een object Dispose-methoden aanroept die een onverwerkte uitzonde ring veroorzaken.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Een Windows Power shell-module gebruiken voor het implementeren van uw cmdlets (RC07)

Maak een Windows Power shell-module voor het inpakken en implementeren van uw cmdlets. Ondersteuning voor modules is geïntroduceerd in Windows Power Shell 2,0. U kunt de assembly's die uw cmdlet-klassen bevatten rechtstreeks als binaire module bestanden gebruiken (dit is erg handig bij het testen van uw cmdlets) of u kunt een module manifest maken dat verwijst naar de cmdlet-assembly's. (U kunt ook bestaande module-assembly's toevoegen wanneer u modules gebruikt.) Zie [een Windows Power shell-module schrijven](../module/writing-a-windows-powershell-module.md)voor meer informatie over modules.

## <a name="see-also"></a>Zie ook

[Zeer aangeraden richtlijnen voor de ontwikkeling](./strongly-encouraged-development-guidelines.md)

[Geadviseerde richtlijnen voor de ontwikkeling](./advisory-development-guidelines.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
