---
title: Richtlijnen voor ontwikkeling vereist | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41d2b308-a36a-496f-8542-666b6a21eedc
caps.latest.revision: 19
ms.openlocfilehash: 3f6bcd2e4ef4d9c404b3a5deeaa9f25d3fa42ec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067464"
---
# <a name="required-development-guidelines"></a>Vereiste richtlijnen voor de ontwikkeling

De volgende richtlijnen moeten worden gevolgd bij het schrijven van uw cmdlets. Ze worden gescheiden in richtlijnen voor het ontwerpen van cmdlets en richtlijnen voor het schrijven van de cmdlet-code. Als u deze richtlijnen niet uitvoert, uw cmdlets kan mislukken en uw gebruikers mogelijk een slechte ervaring hebben wanneer ze uw cmdlets gebruiken.

## <a name="in-this-topic"></a>In dit onderwerp

### <a name="design-guidelines"></a>Richtlijnen voor het ontwerpen

- [Gebruik alleen goedgekeurde werkwoorden (RD01)](./required-development-guidelines.md#use-only-approved-verbs-rd01)

- [Namen van de cmdlets: Tekens die niet kunnen worden gebruikt (RD02)](./required-development-guidelines.md#cmdlet-names-characters-that-cannot-be-used-rd02)

- [Namen van parameters die kunnen worden gebruikt (RD03)](./required-development-guidelines.md#parameters-names-that-cannot-be-used-rd03)

- [Bevestiging ondersteuningsaanvragen (RD04)](./required-development-guidelines.md#support-confirmation-requests-rd04)

- [Ondersteuning voor Parameter Force voor interactieve sessies (RD05)](./required-development-guidelines.md#support-force-parameter-for-interactive-sessions-rd05)

- [Document uitvoer-objecten (RD06)](./required-development-guidelines.md#document-output-objects-rd06)

### <a name="code-guidelines"></a>Code-richtlijnen

- [Afgeleid van de Cmdlet of PSCmdlet klassen (RC01)](./required-development-guidelines.md#derive-from-the-cmdlet-or-pscmdlet-classes-rc01)

- [De Cmdlet-kenmerk (RC02) opgeven](./required-development-guidelines.md#specify-the-cmdlet-attribute-rc02)

- [Invoer verwerken (RC03)-methode overschrijven](./required-development-guidelines.md#override-an-input-processing-method-rc03)

- [Geef het kenmerk OutputType (RC04)](./required-development-guidelines.md#specify-the-outputtype-attribute-rc04)

- [Ingangen naar uitvoer-objecten (RC05) blijft niet behouden](./required-development-guidelines.md#do-not-retain-handles-to-output-objects-rc05)

- [Fouten databases robuuster worden verwerkt (RC06)](./required-development-guidelines.md#handle-errors-robustly-rc06)

- [Een Windows PowerShell-Module gebruiken voor het implementeren van uw Cmdlets (RC07)](./required-development-guidelines.md#use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07)

## <a name="design-guidelines"></a>Richtlijnen voor het ontwerpen

De volgende richtlijnen moeten worden gevolgd bij het ontwerpen van cmdlets om te controleren of een consistente gebruikerservaring tussen het gebruik van de cmdlets en andere cmdlets. Als u een ontwerp richtlijn die van toepassing op uw situatie is, moet u kijken naar de richtlijnen van de Code voor vergelijkbare richtlijnen.

### <a name="use-only-approved-verbs-rd01"></a>Gebruik alleen goedgekeurde werkwoorden (RD01)

De bewerking die is opgegeven in de Cmdlet-kenmerk moet afkomstig zijn van de herkende set bewerkingen die worden geleverd door Windows PowerShell. Deze moet niet een van de niet-toegestane synoniemen. Gebruik de constante tekenreeksen die zijn gedefinieerd door de volgende inventarisaties op te geven van de cmdlet-woorden:

- [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

- [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

- [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

- [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

- [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

- [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

- [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

Zie voor meer informatie over de namen van de goedgekeurde bewerking [werkwoorden](./approved-verbs-for-windows-powershell-commands.md).

Gebruikers moeten een verzameling kunnen worden gedetecteerd en de verwachte cmdlet-namen. Gebruik de juiste term zodat de gebruiker een snelle evaluatie van de werking van een cmdlet en voor het detecteren van de mogelijkheden van het systeem eenvoudig kunt maken. Bijvoorbeeld, de volgende opdrachtregel worden opgehaald die een lijst met alle opdrachten op het systeem waarvan de namen met 'start beginnen': `get-command start-*`. De zelfstandige naamwoorden in uw cmdlets gebruiken om te onderscheiden van de cmdlets van andere cmdlets. Het zelfstandig naamwoord geeft aan dat de resource waarop de bewerking wordt uitgevoerd. De bewerking zelf wordt vertegenwoordigd door de bewerking.

### <a name="cmdlet-names-characters-that-cannot-be-used-rd02"></a>Namen van de cmdlets: Tekens die niet kunnen worden gebruikt (RD02)

Als u cmdlets naam, gebruik dan niet een van de volgende speciale tekens bevatten.

|Teken|Naam|
|---------------|----------|
|#|hekje|
|, |door komma 's|
|()|tussen haakjes|
|{}|accolades|
|[]|vierkante haken|
|&|en-teken|
|-|afbreekstreepje **Opmerking:**  Het afbreekstreepje kan worden gebruikt voor het scheiden van de bewerking van het zelfstandig naamwoord, maar binnen het zelfstandig naamwoord of de bewerking kan niet worden gebruikt.|
|/|schuine streep|
|\|backslash|
|$|dollarteken|
|^|caret-teken|
|;|door puntkomma 's|
|:|colon|
|"|dubbel aanhalingsteken|
|'|enkel aanhalingsteken|
|<>|punthaken|
|&#124;|verticale streep|
|?|vraagteken|
|@|bij aanmelding|
|' | back-maatstreepjes (ernstig accent)|
|*|sterretje|
|%|procentteken|
|+|plusteken|
|=|gelijkteken|
|~|tilde|

### <a name="parameters-names-that-cannot-be-used-rd03"></a>Namen van parameters die kunnen worden gebruikt (RD03)

Windows PowerShell biedt een gemeenschappelijke set een parameters voor alle cmdlets plus aanvullende parameters die in bepaalde situaties worden toegevoegd. Bij het ontwerpen van uw eigen cmdlets kunt u de volgende namen niet gebruiken: Bevestig, foutopsporing,-ErrorAction, -ErrorVariable, OutBuffer, OutVariable, WarningAction, WarningVariable, WhatIf, UseTransaction, en uitgebreide. Zie voor meer informatie over deze parameters [algemene parameternamen](./common-parameter-names.md).

### <a name="support-confirmation-requests-rd04"></a>Bevestiging ondersteuningsaanvragen (RD04)

Cmdlets die een bewerking die Hiermee wijzigt u het systeem uitvoeren, moeten ze bellen de [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode bevestiging wordt gevraagd, en in bijzondere gevallen roept de [ System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methode. (De [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methode moet worden aangeroepen nadat de [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode wordt aangeroepen.)

Voor deze aanroepen die de cmdlet moet opgeven dat deze bevestiging aanvragen door in te stellen ondersteunt de `SupportsShouldProcess` sleutelwoord van de Cmdlet-kenmerk. Zie voor meer informatie over het instellen van dit kenmerk [Cmdlet kenmerkdeclaratie](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Als de Cmdlet-kenmerk van de cmdlet-klasse geeft aan dat de cmdlet biedt ondersteuning voor aanroepen naar de [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode en de cmdlet is mislukt voor de aanroep naar de [ System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode, de gebruiker kan het systeem onverwacht wijzigen.

Gebruik de [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode voor een aanpassing van het systeem. Een gebruikersvoorkeur en de `WhatIf` parameterbesturingselement de [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode. Daarentegen de [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -aanroep wordt een extra controle uitgevoerd op mogelijk schadelijke wijzigingen. Deze methode niet wordt beheerd door een gebruikersvoorkeur of de `WhatIf` parameter. Als uw cmdlet roept de [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methode, moet er een `Force` parameter die de aanroepen voor deze twee methoden omzeilt en die met de bewerking wordt voortgezet. Dit is belangrijk omdat hierdoor de cmdlet moet worden gebruikt in niet-interactieve scripts en -hosts.

Als uw cmdlets deze aanroepen ondersteunen, kan de gebruiker kan bepalen of er daadwerkelijk de actie moet worden uitgevoerd. Bijvoorbeeld, de [Stop-Process](/powershell/module/microsoft.powershell.management/stop-process) aanroepen van cmdlet de [System.Management.Automation.Cmdlet.ShouldContinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methode voordat deze stopt met een set van kritieke processen, met inbegrip van het systeem, Winlogon, en Spoolsv processen.

Zie voor meer informatie over het ondersteunen van deze methoden [aanvragen bevestiging](./requesting-confirmation-from-cmdlets.md).

### <a name="support-force-parameter-for-interactive-sessions-rd05"></a>Ondersteuning voor Parameter Force voor interactieve sessies (RD05)

Als de cmdlet interactief wordt gebruikt, altijd opgeven voor een parameter Force als u wilt overschrijven van de interactieve acties, zoals prompts of het lezen van de regels van invoer). Dit is belangrijk omdat hierdoor de cmdlet moet worden gebruikt in niet-interactieve scripts en -hosts. De volgende methoden kunnen worden geïmplementeerd met een interactieve host.

- [System.Management.Automation.Host.PSHostUserInterface.Prompt*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.Prompt)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForChoice](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForChoice)

- [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection.PromptForChoice](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection.PromptForChoice)

- [System.Management.Automation.Host.Pshostuserinterface.PromptForCredential*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.PromptForCredential)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLine*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLine)

- [System.Management.Automation.Host.Pshostuserinterface.ReadLineAsSecureString*](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.ReadLineAsSecureString)

### <a name="document-output-objects-rd06"></a>Document uitvoer-objecten (RD06)

Windows PowerShell maakt gebruik van de objecten die worden geschreven naar de pijplijn. In de volgorde voor gebruikers om te profiteren van de objecten die worden geretourneerd door elke cmdlet, moet u de objecten die worden geretourneerd document en u moet document waarvoor de leden van deze geretourneerde objecten worden gebruikt.

## <a name="code-guidelines"></a>Code-richtlijnen

De volgende richtlijnen moeten worden gevolgd bij het schrijven van code van de cmdlet. Als u een Code-richtlijn die van toepassing op uw situatie is, moet u kijken naar de richtlijnen voor het ontwerpen voor vergelijkbare richtlijnen.

### <a name="derive-from-the-cmdlet-or-pscmdlet-classes-rc01"></a>Afgeleid van de Cmdlet of PSCmdlet klassen (RC01)

Een cmdlet moet zijn afgeleid van hetzij de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) of [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) basisklasse. Cmdlets die zijn afgeleid van de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasse niet afhankelijk van de Windows PowerShell-runtime. Ze kunnen worden aangeroepen rechtstreeks vanuit een willekeurige taal Microsoft .NET Framework. Cmdlets die zijn afgeleid van de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasse is afhankelijk van de Windows PowerShell-runtime. Daarom worden ze uitgevoerd binnen een runspace.

Alle cmdlet-klassen die u implementeert, moeten openbare klassen. Zie voor meer informatie over deze cmdlet-klassen, [Cmdlet overzicht](./cmdlet-overview.md).

### <a name="specify-the-cmdlet-attribute-rc02"></a>De Cmdlet-kenmerk (RC02) opgeven

Voor een cmdlet om te worden erkend door Windows PowerShell, moet met de Cmdlet-kenmerk zijn voorzien van de .NET Framework-klasse. Dit kenmerk bevat de volgende functies van de cmdlet.

- Het werkwoord-en-zelfstandig naamwoord paar die de cmdlet identificeert.

- De standaardset parameter die wordt gebruikt wanneer meerdere parametersets zijn opgegeven. De standaardset van de parameter wordt gebruikt wanneer Windows PowerShell zijn onvoldoende gegevens beschikbaar om te bepalen welke parameter ingesteld voor het gebruik.

- Geeft aan of de cmdlet aanroepen naar ondersteunt de [System.Management.Automation.Cmdlet.ShouldProcess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode. Deze methode wordt een bevestigingsbericht weergegeven voordat de cmdlet een wijziging aan het systeem maakt. Zie voor meer informatie over hoe de bevestiging van aanvragen, [aanvragen bevestiging](./requesting-confirmation-from-cmdlets.md).

- Het niveau van impact (of de ernst) van de actie die is gekoppeld aan het bevestigingsbericht opgeven. In de meeste gevallen moet de standaardwaarde van de media die worden gebruikt. Zie voor meer informatie over de invloed van het niveau van impact op de bevestiging van aanvragen die worden weergegeven aan de gebruiker [aanvragen bevestiging](./requesting-confirmation-from-cmdlets.md).

Zie voor meer informatie over hoe u de cmdlet-kenmerk declareren [CmdletAttribute declaratie](./cmdlet-attribute-declaration.md).

### <a name="override-an-input-processing-method-rc03"></a>Invoer verwerken (RC03)-methode overschrijven

Voor de cmdlet om deel te nemen in de Windows PowerShell-omgeving, moet het ten minste een van de volgende overschrijven *invoer verwerkingsmethoden*.

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) deze methode wordt één keer aangeroepen en wordt gebruikt voor het vooraf verwerken functionaliteit bieden.

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) deze methode wordt meerdere keren aangeroepen en deze wordt gebruikt om record door record functionaliteit te bieden.

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) deze methode wordt aangeroepen één keer, en deze wordt gebruikt om na verwerking functionaliteit te bieden.

### <a name="specify-the-outputtype-attribute-rc04"></a>Geef het kenmerk OutputType (RC04)

Atribut OutputType (geïntroduceerd in Windows PowerShell 2.0) Hiermee geeft u het .NET Framework-type dat de cmdlet aan de pijplijn retourneert. Door het uitvoertype van uw cmdlets op te geven u de objecten die zijn geretourneerd door de cmdlet beter worden gedetecteerd door andere cmdlets. Zie voor meer informatie over het met het inrichten van de cmdlet-klasse met dit kenmerk [OutputType kenmerkdeclaratie](./outputtype-attribute-declaration.md).

### <a name="do-not-retain-handles-to-output-objects-rc05"></a>Ingangen naar uitvoer-objecten (RC05) blijft niet behouden

De cmdlet niet bewaren moet voor alle ingangen voor de objecten die worden doorgegeven aan de [System.Management.Automation.Cmdlet.WriteObject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) methode. Deze objecten worden doorgegeven aan de volgende cmdlet in de pijplijn of ze worden gebruikt door een script. Als u de grepen naar de objecten behoudt, wordt elk object, dat ervoor zorgt fouten dat eigenaar van twee entiteiten.

### <a name="handle-errors-robustly-rc06"></a>Fouten databases robuuster worden verwerkt (RC06)

Een beheer-omgeving is inherent detecteert en belangrijke wijzigingen aanbrengt in het systeem die u beheert. Daarom is het essentieel dat cmdlets fouten correct verwerken. Zie voor meer informatie over foutrecords [Windows PowerShell-foutrapportage](./error-reporting-concepts.md).

- Wanneer een fout voorkomt een cmdlet u verdergaat dat met het verwerken van meer records, is er een afsluitfout. De cmdlet moet worden aangeroepen de [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) methode die verwijst naar een [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object. Als een uitzondering niet door de cmdlet bijgewerkt is, genereert de Windows PowerShell-runtime zelf een afsluitfout die minder gegevens bevat.

- Voor een niet-afsluitfout die niet bewerking op de volgende stopt record die afkomstig is van de pijplijn (bijvoorbeeld een record die wordt geproduceerd door een ander proces), de cmdlet moet worden aangeroepen de [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode die verwijst naar een [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object. Een voorbeeld van een niet-afsluitfout is de fout die optreedt als een bepaald proces niet stoppen. Aanroepen van de [System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode kan de gebruiker consistent de acties die worden aangevraagd en het behouden van de gegevens voor bepaalde acties die mislukken. De cmdlet moet onafhankelijk mogelijk elke record verwerken.

- De [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object waarnaar wordt verwezen door de [System.Management.Automation.Cmdlet.ThrowTerminatingError*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) en [ System.Management.Automation.Cmdlet.WriteError*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methoden is een uitzondering in de kern vereist. Volg de richtlijnen voor het ontwerpen van .NET Framework tijdens het bepalen van de uitzondering te gebruiken. Als de fout semantisch gelijk zijn aan een bestaande uitzondering is, gebruikt u de uitzondering of afgeleid van de uitzondering. Anders wordt afgeleid van een nieuwe uitzondering of uitzonderingen hiërarchie rechtstreeks vanuit de [System.Exception](/dotnet/api/System.Exception) type.

Een [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object moet ook een Foutcategorie waarin fouten voor de gebruiker zijn gegroepeerd. De gebruiker kan zien fouten op basis van de categorie door de waarde van de `$ErrorView` shell-variabele te CategoryView. De mogelijke categorieën worden gedefinieerd door de [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) opsomming.

- Als een cmdlet maakt een nieuwe thread, en als de code die wordt uitgevoerd in deze thread een niet-verwerkte uitzondering genereert, wordt Windows PowerShell wordt de fout niet onderscheppen en wordt het proces is beëindigd.

- Als een object heeft de code in de destructor die ervoor zorgt een niet-verwerkte uitzondering dat, wordt Windows PowerShell wordt de fout niet onderscheppen en wordt het proces is beëindigd. Dit gebeurt ook wanneer een object Dispose methoden aangeroepen die ertoe leiden een onverwerkte uitzondering dat.

### <a name="use-a-windows-powershell-module-to-deploy-your-cmdlets-rc07"></a>Een Windows PowerShell-Module gebruiken voor het implementeren van uw Cmdlets (RC07)

Maak een Windows PowerShell-module voor het verpakken en implementeren van uw cmdlets. Ondersteuning voor modules die is geïntroduceerd in Windows PowerShell 2.0. Kunt u de assembly's die de cmdlet-klassen rechtstreeks als binaire module-bestanden (dit is zeer nuttig bij het testen van uw cmdlets) bevatten of u een modulemanifest dat verwijst naar de cmdlet-assembly's kunt maken. (U kunt ook toevoegen bestaande-module assembly's bij het gebruik van modules.) Zie voor meer informatie over modules [schrijven van een Windows PowerShell-Module](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Zie ook

[De richtlijnen ten zeerste aangeraden ontwikkeling](./strongly-encouraged-development-guidelines.md)

[Richtlijnen voor advies ontwikkeling](./advisory-development-guidelines.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
