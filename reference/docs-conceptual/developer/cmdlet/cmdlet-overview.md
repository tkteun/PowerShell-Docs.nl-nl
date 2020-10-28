---
ms.date: 06/11/2020
ms.topic: reference
title: Overzicht van cmdlets
description: Overzicht van cmdlets
ms.openlocfilehash: ed3082e1a821bb9643ea2eef13b7348eb48488e4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653228"
---
# <a name="cmdlet-overview"></a>Overzicht van cmdlets

Een cmdlet is een licht gewicht opdracht die wordt gebruikt in de Power shell-omgeving. De Power shell-runtime roept deze cmdlets aan binnen de context van de automatiserings scripts die op de opdracht regel worden gegeven. De Power shell-runtime roept deze ook programmatisch aan via Power shell-Api's.

## <a name="cmdlets"></a>Cmdlets

Cmdlets voeren een actie uit en retour neren doorgaans een Microsoft .NET-object naar de volgende opdracht in de pijp lijn. Een cmdlet is één opdracht die deel uitmaakt van de pijplijn semantiek van Power shell.
Dit omvat binaire (C#) cmdlets, geavanceerde script functies, CDXML en werk stromen.

In deze SDK-documentatie wordt beschreven hoe u binaire cmdlets maakt die zijn geschreven in C#. Zie voor informatie over cmdlets op basis van een script:

- [about_Functions_Advanced](/powershell/module/microsoft.powershell.core/about/about_functions_advanced)
- [about_Functions_CmdletBindingAttribute](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute)
- [about_Functions_Advanced_Methods](/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods)

Als u een binaire cmdlet wilt maken, moet u een cmdlet-klasse implementeren die is afgeleid van een van de twee gespecialiseerde cmdlet-basis klassen. De afgeleide klasse moet:

- Declareer een kenmerk dat de afgeleide klasse identificeert als een cmdlet.
- Definieer open bare eigenschappen die zijn gedecoreerd met kenmerken die de open bare eigenschappen identificeren als cmdlet-para meters.
- Overschrijf een of meer van de invoer verwerkings methoden om records te verwerken.

U kunt de assembly met de klasse rechtstreeks laden met behulp van de cmdlet [import-module](/powershell/module/microsoft.powershell.core/import-module) , maar u kunt ook een hosttoepassing maken die de assembly laadt met behulp van de tialsessionstate-API van [System.Management.Automation.Runspaces.Ini](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) . Beide methoden bieden programmatische en opdracht regel toegang tot de functionaliteit van de cmdlet.

## <a name="cmdlet-terms"></a>Cmdlet-voor waarden

De volgende termen worden regel matig gebruikt in de Power shell-cmdlet-documentatie:

### <a name="cmdlet-attribute"></a>Cmdlet-kenmerk

Een .NET-kenmerk dat wordt gebruikt voor het declareren van een cmdlet-klasse als een cmdlet. Hoewel Power shell verschillende andere kenmerken gebruikt die optioneel zijn, is het cmdlet-kenmerk vereist. Zie voor meer informatie over dit kenmerk de [cmdlet-kenmerk declaratie](cmdlet-attribute-declaration.md).

### <a name="cmdlet-parameter"></a>Cmdlet-para meter

De open bare eigenschappen waarmee de para meters worden gedefinieerd die beschikbaar zijn voor de gebruiker of voor de toepassing die de cmdlet uitvoert. Cmdlets kunnen de para meters vereist, benoemde, positioneel en *Switch* hebben. Switch parameters geven u de mogelijkheid om para meters te definiëren die alleen worden geëvalueerd als de para meters worden opgegeven in de aanroep. Zie [cmdlet-para meters](cmdlet-parameters.md)voor meer informatie over de verschillende typen para meters.

### <a name="parameter-set"></a>Parameterset

Een groep para meters die in dezelfde opdracht kunnen worden gebruikt om een specifieke actie uit te voeren. Een cmdlet kan meerdere parameter sets hebben, maar elke parameterset moet ten minste één para meter hebben die uniek is. Een goed cmdlet-ontwerp raadt sterk aan dat de unieke para meter ook een vereiste para meter is.
Zie [cmdlet-parameter sets](cmdlet-parameter-sets.md)voor meer informatie over parameter sets.

### <a name="dynamic-parameter"></a>Dynamische para meter

Een para meter die tijdens runtime wordt toegevoegd aan de cmdlet. Normaal gesp roken worden de dynamische para meters toegevoegd aan de cmdlet wanneer een andere para meter op een specifieke waarde is ingesteld. Zie [cmdlet Dynamic para meters](cmdlet-dynamic-parameters.md)voor meer informatie over dynamische para meters.

### <a name="input-processing-methods"></a>Invoer verwerkings methoden

De klasse [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) biedt de volgende virtuele methoden die worden gebruikt voor het verwerken van records. Alle afgeleide cmdlet-klassen moeten een of meer van de eerste drie methoden overschrijven:

- [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): wordt gebruikt om een optionele, vooraf verwerkings functionaliteit te bieden voor de cmdlet.
- [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): wordt gebruikt voor het leveren van de verwerking van records per record voor de cmdlet. De methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) kan elk wille keurig aantal keren worden aangeroepen, al naar gelang de invoer van de cmdlet.
- [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): wordt gebruikt om de optionele eenmalige, verwerkings functionaliteit voor de cmdlet te bieden.
- [System. Management. Automation. cmdlet. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): wordt gebruikt om de verwerking te stoppen wanneer de gebruiker de cmdlet asynchroon stopt (bijvoorbeeld door op <kbd>CTRL</kbd> + <kbd>C</kbd>te drukken).

Zie voor meer informatie over deze methoden [cmdlet input processing methods](./cmdlet-input-processing-methods.md).

Wanneer u een cmdlet implementeert, moet u ten minste één van deze invoer verwerkings methoden onderdrukken.
Normaal gesp roken is de **ProcessRecord ()** de methode die u overschrijft, omdat deze wordt aangeroepen voor elke record die door de cmdlet wordt verwerkt. Daarentegen wordt de methode **BeginProcessing ()** en de methode **EndProcessing ()** één keer aangeroepen voor het uitvoeren van vóór verwerking of na verwerking van de records. Zie [invoer verwerkings methoden](cmdlet-input-processing-methods.md)voor meer informatie over deze methoden.

### <a name="shouldprocess-feature"></a>Functie ShouldProcess

Met Power shell kunt u cmdlets maken waarmee de gebruiker wordt gevraagd om feedback voordat de cmdlet een wijziging in het systeem aanbrengt. Voor het gebruik van deze functie moet de cmdlet declareren dat deze de `ShouldProcess` functie ondersteunt wanneer u het cmdlet-kenmerk declareert. de cmdlet moet de methoden System. Management. Automation. [cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) . cmdlet. ShouldContinue aanroepen vanuit een invoer verwerkings methode. `ShouldProcess`Zie [bevestiging aanvragen](requesting-confirmation-from-cmdlets.md)voor meer informatie over het ondersteunen van de functionaliteit.

### <a name="transaction"></a>Transactie

Een logische groep opdrachten die worden behandeld als één taak. De taak mislukt automatisch als een opdracht in de groep mislukt en de gebruiker de mogelijkheid heeft om de acties die in de trans actie worden uitgevoerd, te accepteren of af te wijzen. Om deel te nemen aan een trans actie, moet de cmdlet declareren dat deze trans acties ondersteunt wanneer het cmdlet-kenmerk wordt gedeclareerd. Ondersteuning voor trans acties is geïntroduceerd in Windows Power Shell 2,0. Zie [trans acties ondersteunen](how-to-support-transactions.md)voor meer informatie over trans acties.

## <a name="how-cmdlets-differ-from-commands"></a>Het verschil tussen cmdlets en opdrachten

Cmdlets verschillen van opdrachten in andere opdracht shell-omgevingen op de volgende manieren:

- Cmdlets zijn exemplaren van .NET-klassen; ze zijn geen zelfstandige uitvoer bare bestanden.
- Cmdlets kunnen worden gemaakt van slechts tien regels code.
- Cmdlets maken in het algemeen geen eigen parsering, fout presentatie of uitvoer indeling. Het parseren, de fout presentatie en de uitvoer indeling worden verwerkt door de Power shell-runtime.
- Cmdlets verwerken invoer objecten van de pijp lijn in plaats van van stromen van tekst, en cmdlets leveren doorgaans objecten als uitvoer naar de pijp lijn.
- Cmdlets zijn record gericht omdat ze één object tegelijk verwerken.

## <a name="cmdlet-base-classes"></a>Cmdlet-basis klassen

Windows Power shell ondersteunt cmdlets die zijn afgeleid van de volgende twee basis klassen.

- De meeste cmdlets zijn gebaseerd op .NET-klassen die zijn afgeleid van de basis klasse [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .
  Door te worden afgeleid van deze klasse kan een cmdlet de minimale set afhankelijkheden voor de Windows Power shell-runtime gebruiken. Dit heeft twee voor delen. Het eerste voor deel is dat de cmdlet-objecten kleiner zijn en dat de kans op wijzigingen in de Power shell-runtime kleiner wordt. Het tweede voor deel is dat u, indien nodig, rechtstreeks een exemplaar van het object cmdlet kunt maken en dit vervolgens rechtstreeks aanroept in plaats van het aanroepen via de Power shell-runtime.

- De complexere cmdlets zijn gebaseerd op .NET-klassen die zijn afgeleid van de basis klasse [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . Als u deze klasse afleidt, hebt u veel meer toegang tot de Power shell-runtime. Met deze toegang kan uw cmdlet scripts aanroepen, toegang krijgen tot providers en toegang krijgen tot de huidige sessie status.
  (Als u de huidige sessie status wilt openen, stelt u sessie variabelen en voor keuren in.) Als gevolg van deze klasse wordt echter de grootte van het cmdlet-object verhoogd, en het betekent dat de cmdlet nauw keuriger is gekoppeld aan de huidige versie van de Power shell-runtime.

In het algemeen, tenzij u de uitgebreide toegang tot de Power shell-runtime nodig hebt, moet u worden afgeleid van de klasse [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .
De Power shell-runtime heeft echter uitgebreide registratie mogelijkheden voor het uitvoeren van cmdlets. Als uw controle model afhankelijk is van deze logboek registratie, kunt u de uitvoering van de cmdlet vanuit een andere cmdlet voor komen door af te leiden van de klasse [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

## <a name="cmdlet-attributes"></a>Cmdlet-kenmerken

Power shell definieert verschillende .NET-kenmerken die worden gebruikt voor het beheren van cmdlets en het opgeven van algemene functionaliteit die door Power shell wordt verstrekt en die mogelijk vereist zijn voor de cmdlet. Kenmerken worden bijvoorbeeld gebruikt om een klasse aan te wijzen als een cmdlet, om de para meters van de cmdlet op te geven en om de validatie van invoer aan te vragen, zodat cmdlet-ontwikkel aars die functionaliteit niet hoeven te implementeren in hun cmdlet-code. Zie [Power shell-kenmerken](./cmdlet-attributes.md)voor meer informatie over kenmerken.

## <a name="cmdlet-names"></a>Namen van cmdlets

Power shell gebruikt een combi natie van verb en samen stelling om naam-cmdlets te gebruiken. De `Get-Command` cmdlet die is opgenomen in Power shell wordt bijvoorbeeld gebruikt om alle cmdlets op te halen die zijn geregistreerd in de opdracht shell. De opdracht geeft de actie aan die door de cmdlet wordt uitgevoerd en het zelfstandig naam woord identificeert de resource waarop de cmdlet de actie uitvoert.

Deze namen worden opgegeven wanneer de .NET-klasse als een cmdlet is gedeclareerd. Zie [cmdlet-kenmerk declaratie](./cmdlet-class-declaration.md)voor meer informatie over het declareren van een .net-klasse als een cmdlet.

## <a name="writing-cmdlet-code"></a>Cmdlet-code schrijven

Dit document bevat twee manieren om te ontdekken hoe de cmdlet-code wordt geschreven. Zie [voor beelden van cmdlet-code](./examples-of-cmdlet-code.md)als u de code wilt weer geven zonder veel uitleg. Zie de onderwerpen zelf studie voor [GetProc](./getproc-tutorial.md), [StopProc zelf](./stopproc-tutorial.md)studie of [SelectStr zelf studie](./selectstr-tutorial.md) als u meer uitleg over de code wilt.

Zie [richt lijnen voor het ontwikkelen van cmdlets](./cmdlet-development-guidelines.md)voor meer informatie over de richt lijnen voor het schrijven van cmdlets.

## <a name="see-also"></a>Zie ook

[Concepten voor PowerShell-cmdlets](./windows-powershell-cmdlet-concepts.md)

[Een PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)

[PowerShell SDK](../windows-powershell-reference.md)
