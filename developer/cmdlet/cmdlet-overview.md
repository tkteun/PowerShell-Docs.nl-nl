---
title: Overzicht van de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK]
- cmdlets [PowerShell SDK], described
ms.assetid: 0aa32589-4447-4ead-a5dd-a3be99113140
caps.latest.revision: 21
ms.openlocfilehash: 14200aed2fb94c37c8b8af29650f602945e7ac1c
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229360"
---
# <a name="cmdlet-overview"></a>Overzicht van cmdlets

Een cmdlet is een lichtgewicht opdracht die wordt gebruikt in de Windows PowerShell-omgeving. De Windows PowerShell-runtime roept deze cmdlets binnen de context van automatiseringsscripts die beschikbaar zijn op de opdrachtregel. De runtime van de Windows PowerShell ook roept deze via een programma via Windows PowerShell-APIs.

## <a name="cmdlets"></a>Cmdlets

Cmdlets een actie uitvoert en een Microsoft .NET Framework-object doorgaans terug te keren naar de volgende opdracht in de pijplijn. Voor het schrijven van een cmdlet, moet u een cmdlet-klasse die is afgeleid van een van twee gespecialiseerde cmdlet-basisklassen te implementeren. De afgeleide klasse moet:

- Een kenmerk waarmee de afgeleide klasse als een cmdlet declareren.

- Openbare eigenschappen die zijn voorzien van kenmerken die welke openbare eigenschappen als cmdlet-parameters aangeven definiëren.

- Een of meer van de invoer voor het verwerken van methoden voor het procesrecords overschrijven.

U kunt laden van de assembly die de klasse rechtstreeks met behulp van bevat de [Import-Module](/powershell/module/microsoft.powershell.core/import-module) cmdlet of maak een hosttoepassing die de assembly met behulp van geladen de [ System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API. Beide methoden bieden programmatische en opdrachtregel toegang tot de functionaliteit van de cmdlet.

## <a name="cmdlet-terms"></a>Cmdlet-voorwaarden

De volgende termen worden vaak gebruikt in de documentatie van Windows PowerShell-cmdlet:

### <a name="cmdlet-attribute"></a>Cmdlet-kenmerk

Een .NET Framework-kenmerk dat wordt gebruikt om aan te geven van een cmdlet-klasse als een cmdlet.
Hoewel PowerShell wordt gebruikt voor verschillende andere kenmerken die optioneel zijn, is het Cmdlet-kenmerk vereist.
Zie voor meer informatie over dit kenmerk [Cmdlet kenmerkdeclaratie](cmdlet-attribute-declaration.md).

### <a name="cmdlet-parameter"></a>Cmdlet-parameter

De openbare eigenschappen die de parameters gedefinieerd die beschikbaar zijn voor de gebruiker of de toepassing die de cmdlet wordt uitgevoerd.
Cmdlets kunt vereiste, met de naam, positionele, en *overschakelen* parameters.
Switch-parameters kunnen u parameters definiëren die alleen als de parameters zijn opgegeven in de aanroep van worden geëvalueerd.
Zie voor meer informatie over de verschillende typen parameters [Cmdlet-Parameters](cmdlet-parameters.md).

### <a name="parameter-set"></a>Parameterset

Een groep van de parameters die kunnen worden gebruikt in dezelfde opdracht een bepaalde actie uit te voeren.
Een cmdlet kunt hebben meerdere parametersets moet, maar elke parameterset ten minste één parameter die uniek is.
Goede cmdlet ontwerp raadt dat de unieke parameter ook niet een vereiste parameter.
Zie voor meer informatie over parametersets [Cmdlet-Parameter stelt](cmdlet-parameter-sets.md).

### <a name="dynamic-parameter"></a>dynamische parameter

Een parameter die wordt toegevoegd aan de cmdlet tijdens runtime.
Normaal gesproken worden de dynamische parameters toegevoegd aan de cmdlet, wanneer een andere parameter is ingesteld op een specifieke waarde.
Zie voor meer informatie over dynamische parameters [dynamische Parameters van de Cmdlet](cmdlet-dynamic-parameters.md).

### <a name="input-processing-method"></a>verwerken van methode invoer

Een methode die een cmdlet gebruiken kunt voor het verwerken van de records die deze ontvangt als invoer.
De van invoer-verwerkingsmethoden zijn onder meer de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode, de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode, de [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode, en de [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) methode. Wanneer u een cmdlet implementeert, moet u ten minste één van overschrijven de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), en [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methoden.
Normaal gesproken de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) is de methode die u overschrijven omdat deze wordt aangeroepen voor elke record die de cmdlet wordt verwerkt.
Daarentegen de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode en de [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode worden één keer aangeroepen om uit te voeren vooraf verwerken of na verwerking van de records.
Zie voor meer informatie over deze methoden, [invoer verwerking methoden](cmdlet-input-processing-methods.md).

### <a name="shouldprocess-feature"></a>De functie shouldprocess wordt overgeslagen

PowerShell kunt u cmdlets die de gebruiker om feedback vragen voordat de cmdlet een wijziging aan het systeem maakt maken.
Deze functie wilt gebruiken, de cmdlet moet worden gedeclareerd dat het ondersteuning biedt voor de functie shouldprocess wordt overgeslagen wanneer u de Cmdlet-kenmerk declareren en moet worden aangeroepen door de cmdlet de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methoden van binnen een invoer verwerken van methode.
Zie voor meer informatie over hoe u ondersteuning voor de functionaliteit shouldprocess wordt overgeslagen [aanvragen bevestiging](requesting-confirmation-from-cmdlets.md).

### <a name="transaction"></a>Transactie

Een logische groep opdrachten die worden behandeld als één taak.
De taak automatisch wordt uitgevoerd als een opdracht in de groep mislukt en de gebruiker de keuze om te accepteren of weigeren van de acties die worden uitgevoerd binnen de transactie heeft.
Om deel te nemen in een transactie, moet de cmdlet declareert dat deze biedt ondersteuning voor transacties wanneer de Cmdlet-kenmerk is gedeclareerd.
Ondersteuning voor transacties is geïntroduceerd in Windows PowerShell 2.0.
Zie voor meer informatie over transacties [hoe u ondersteuning voor transacties](how-to-support-transactions.md).

## <a name="how-cmdlets-differ-from-commands"></a>Hoe Cmdlets verschillen van opdrachten

Cmdlets verschillen van de opdrachten in andere omgevingen opdrachtshell in de volgende manieren:

- -Cmdlets zijn exemplaren van .NET Framework-klassen; ze zijn niet zelfstandig uitvoerbare bestanden.

- Cmdlets kunnen worden gemaakt op basis van slechts tien regels code.

- Cmdlets in het algemeen niet hun eigen parseren, fout presentatie, of het opmaken van uitvoer. Parseren, fout presentatie en opmaken van uitvoer worden afgehandeld door de Windows PowerShell-runtime.

- Cmdlets proces invoer objecten uit de pijplijn in plaats van vanaf streams van tekst en cmdlets bieden doorgaans objecten als uitvoer aan de pijplijn.

- -Cmdlets zijn record gerichte omdat zij één object per keer verwerken.

## <a name="cmdlet-base-classes"></a>Cmdlet Base klassen

Windows PowerShell ondersteunt-cmdlets die zijn afgeleid van de volgende twee basisklassen.

- De meeste cmdlets zijn gebaseerd op .NET Framework-klassen die zijn afgeleid van de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) basisklasse. Die is afgeleid van deze klasse kan een cmdlet voor het gebruik van de minimale set van afhankelijkheden in de Windows PowerShell-runtime. Dit heeft twee voordelen. Het eerste voordeel is dat de cmdlet-objecten kleiner zijn en bent u minder waarschijnlijk worden beïnvloed door wijzigingen in de Windows PowerShell-runtime. Het tweede voordeel is dat, als u hebt, kunt u rechtstreeks een exemplaar van de cmdlet-object te maken en vervolgens rechtstreeks in plaats van het aanroepen van deze via de Windows PowerShell-runtime aanroepen.

- De cmdlets complexere zijn gebaseerd op .NET Framework-klassen die zijn afgeleid van de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) basisklasse. Die is afgeleid van deze klasse biedt u veel meer toegang tot de Windows PowerShell-runtime. Deze toegang kunt de cmdlet voor het aanroepen van scripts, voor toegang tot providers, en voor toegang tot de status van de huidige sessie. (Voor toegang tot de status van de huidige sessie, u ophalen en instellen van sessievariabelen en voorkeuren.) Echter, die is afgeleid van deze klasse neemt de omvang van de cmdlet-object en betekent dit dat uw cmdlet meer nauw is gekoppeld aan de huidige versie van de Windows PowerShell-runtime.

In het algemeen, tenzij u nodig hebt voor de uitgebreide toegang tot de Windows PowerShell-runtime, u moet zijn afgeleid van de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasse. De Windows PowerShell-runtime beschikt echter over mogelijkheden voor uitgebreide logboekregistratie voor het uitvoeren van cmdlets. Als uw controle model is afhankelijk van deze logboekregistratie, kunt u de uitvoering van de cmdlet uit binnen een andere cmdlet voorkomen door die is afgeleid van de [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasse.

## <a name="input-processing-methods"></a>Verwerking van methoden invoer

De [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasse biedt de volgende virtuele methoden die worden gebruikt voor het verwerken van records. Alle afgeleide cmdlet-klassen moeten een of meer van de eerste drie methoden overschrijven:

- [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): Gebruikt voor optionele functies voor eenmalig, vooraf verwerken van de cmdlet.

- [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): Gebruikt voor het verwerken van record door records functionaliteit biedt voor de cmdlet. De [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode kan worden aangeroepen op een willekeurig aantal keren of helemaal niet afhankelijk van de invoer van de cmdlet.

- [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): Gebruikt voor optionele functies voor eenmalig, na verwerking van de cmdlet.

- [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): Gebruikt om te stoppen met het verwerken van wanneer de gebruiker de cmdlet asynchroon stopt (bijvoorbeeld door op CTRL + C).

Zie voor meer informatie over deze methoden, [Cmdlet invoer verwerking methoden](./cmdlet-input-processing-methods.md).

## <a name="cmdlet-attributes"></a>Cmdlet-kenmerken

Windows PowerShell definieert verschillende .NET Framework-kenmerken die worden gebruikt voor het beheren van cmdlets en op te geven van de algemene functionaliteit die wordt geleverd door Windows PowerShell en die kan worden vereist door de cmdlet. Bijvoorbeeld, worden kenmerken gebruikt om een klasse als een cmdlet, om op te geven van de parameters van de cmdlet, en om aan te vragen van de validatie van de invoer, zodat ontwikkelaars cmdlet hoeft te implementeren dat de functionaliteit in de cmdlet-code toe te wijzen. Zie voor meer informatie over kenmerken [Windows PowerShell-kenmerken](./cmdlet-attributes.md).

## <a name="cmdlet-names"></a>Namen van de cmdlets

Windows PowerShell maakt gebruik van een paar werkwoord-en-zelfstandig naamwoord naam voor de naam van cmdlets. Bijvoorbeeld, de `Get-Command` opgenomen in Windows PowerShell cmdlet wordt gebruikt om op te halen van de cmdlets die zijn geregistreerd in de opdrachtshell. De term identificeert de actie die de cmdlet uitvoert, en het zelfstandig naamwoord geeft de bron die de bijbehorende actie wordt uitgevoerd door de cmdlet.

Deze namen zijn opgegeven wanneer de .NET Framework-klasse is gedeclareerd als een cmdlet. Zie voor meer informatie over hoe u een .NET Framework-klasse als een cmdlet declareren [Cmdlet kenmerkdeclaratie](./cmdlet-class-declaration.md).

## <a name="writing-cmdlet-code"></a>Cmdlet-Code schrijven

Dit document biedt twee manieren om te ontdekken hoe de code van de cmdlet wordt geschreven. Als u liever om de code zonder veel uitleg te zien, Zie [voorbeelden van de Code van de Cmdlet](./examples-of-cmdlet-code.md). Als u liever meer uitleg over de code, Zie de [GetProc zelfstudie](./getproc-tutorial.md), [StopProc zelfstudie](./stopproc-tutorial.md), of [SelectStr zelfstudie](./selectstr-tutorial.md) onderwerpen.

Zie voor meer informatie over de richtlijnen voor het schrijven-cmdlets, [Cmdlet ontwikkeling richtlijnen](./cmdlet-development-guidelines.md).

## <a name="see-also"></a>Zie ook

[Concepten van Windows PowerShell-Cmdlet](./windows-powershell-cmdlet-concepts.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
