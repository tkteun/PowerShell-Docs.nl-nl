---
title: Fout rapportage voor cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error records [PowerShell], terminating
- non-terminating errors [PowerShell]
- error records [PowerShell]
- terminating errors [PowerShell]
- error records [PowerShell], non-terminating
ms.assetid: 0b014035-52ea-44cb-ab38-bbe463c5465a
caps.latest.revision: 8
ms.openlocfilehash: 5dfec318438ca139518c596011ac5e56445738ea
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356565"
---
# <a name="cmdlet-error-reporting"></a>Fout rapportage voor cmdlets

Cmdlets moeten fouten anders rapporteren, afhankelijk van het feit of fouten of niet-afsluit fouten worden afgesloten. Afsluit fouten zijn fouten die ervoor zorgen dat de pijp lijn onmiddellijk wordt beëindigd of fouten die optreden wanneer er geen reden is om de verwerking voort te zetten. Niet-afsluit fouten zijn die fouten die een actuele fout hebben gerapporteerd, maar de cmdlet kan invoer objecten blijven verwerken. Bij niet-afsluit fouten wordt de gebruiker doorgaans op de hoogte gesteld van het probleem, maar de cmdlet blijft het volgende invoer object verwerken.

## <a name="terminating-and-nonterminating-errors"></a>Fout bij beëindigen en niet afsluiten

De volgende richt lijnen kunnen worden gebruikt om te bepalen of een fout een afsluit fout of een niet-afsluit fout is.

- Wordt de fout voor komen dat uw cmdlet verdere invoer objecten verwerkt? Als dit het geval is, is dit een afsluit fout.

- Is de fout voorwaarde gerelateerd aan een specifiek invoer object of een subset van invoer objecten? Als dit het geval is, is dit een niet-afsluit fout.

- Accepteert de cmdlet meerdere invoer objecten, zodat de verwerking kan slagen voor een ander invoer object? Als dit het geval is, is dit een niet-afsluit fout.

- Cmdlets die meerdere invoer objecten kunnen accepteren, moeten bepalen wat er moet worden beëindigd en niet-afsluit fouten, zelfs wanneer een bepaalde situatie alleen van toepassing is op één invoer object.

- Cmdlets kunnen elk wille keurig aantal invoer objecten ontvangen en een wille keurig aantal geslaagde of fout objecten verzenden voordat een afsluitende uitzonde ring wordt gegenereerd. Er is geen relatie tussen het aantal ontvangen invoer objecten en het aantal geslaagde en fout objecten dat is verzonden.

- Cmdlets die slechts 0-1 invoer objecten kunnen accepteren en alleen uitvoer objecten van 0-1 genereren, moeten fouten behandelen als afsluit fouten en het genereren van afsluit uitzonderingen.

## <a name="reporting-nonterminating-errors"></a>Niet-afsluit fouten rapporteren

De rapportage van een niet-afsluitende fout moet altijd worden uitgevoerd binnen de implementatie van de cmdlet [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) , de methode [System. Management.](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Automation. cmdlet. ProcessRecord, of met de methode [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Deze typen fouten worden gerapporteerd door het aanroepen van de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) die op zijn beurt een fout record naar de fout stroom verzendt.

## <a name="reporting-terminating-errors"></a>Fout bij het rapporteren van het rapport

Afsluit fouten worden gerapporteerd door uitzonde ringen te genereren of door het aanroepen van de methode [System. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) . Houd er rekening mee dat cmdlets ook uitzonde ringen kunnen ondervangen en genereren, zoals **OutOfMemory**, maar ze zijn niet vereist voor het opnieuw genereren van uitzonde ringen omdat de Power shell-runtime deze ook kan onderscheppen.

U kunt ook uw eigen uitzonde ringen definiëren voor problemen die specifiek zijn voor uw situatie, of extra informatie toevoegen aan een bestaande uitzonde ring met behulp van de fout record.

## <a name="error-records"></a>Fout records

In Power shell wordt een niet-afsluit fout beschreven met [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -objecten. Elk object bevat informatie over de fout categorie, een optioneel doel object en Details over de fout voorwaarde.

### <a name="error-identifiers"></a>Fout-id's

De fout-id is een eenvoudige teken reeks waarmee de fout voorwaarde binnen de cmdlet wordt geïdentificeerd.
Power shell combineert deze id met een cmdlet-id om een volledig gekwalificeerde fout-id te maken die later kan worden gebruikt bij het filteren van fout stromen of logboek registratie fouten, wanneer deze reageert op specifieke fouten of met andere gebruikersspecifieke activiteiten.

De volgende richt lijnen moeten worden gevolgd wanneer fout-id's worden opgegeven:

- Verschillende, zeer specifieke fout-id's toewijzen aan verschillende code paden. Elk codepad dat [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) of [System. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) aanroept, moet een eigen fout-id hebben.

- Fout-id's moeten uniek zijn voor uitzonderings typen van common language runtime (CLR) voor zowel afsluit-als niet-afsluit fouten.

- Wijzig niet de semantiek van een fout-id tussen versies van uw cmdlet of Power shell-provider. Nadat de semantiek van een fout-id tot stand is gebracht, moet deze gedurende de levens cyclus van de cmdlet constant blijven.

- Gebruik voor het beëindigen van fouten een unieke fout-id voor een bepaald CLR-uitzonderings type. Als het type uitzonde ring wordt gewijzigd, gebruikt u een nieuwe fout-id.

- Gebruik voor niet-afsluit fouten een specifieke fout-id voor een specifiek invoer object.

- Kies tekst voor de id die tersely overeenkomt met de fout die wordt gerapporteerd. Gebruik geen spaties of lees tekens.

- Genereer geen fout-id's die niet reproduceerbaar zijn. Genereer bijvoorbeeld geen id's die een proces-id bevatten. Fout-id's zijn alleen nuttig wanneer ze overeenkomen met id's die worden gezien door andere gebruikers die hetzelfde probleem ondervinden.

### <a name="error-categories"></a>Fout Categorieën

Fout categorieën worden gebruikt om fouten te groeperen voor de gebruiker. In Power shell worden deze categorieën en cmdlets en Power shell-providers gedefinieerd om te kiezen bij het genereren van de fout record.

Zie [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) -inventarisatie voor een beschrijving van de fout categorieën die beschikbaar zijn. Over het algemeen moet u voor komen dat u, indien mogelijk, **UndefinedError**en **algemene fout** **gebruiken.**

Gebruikers kunnen fouten weer geven op basis van categorie wanneer ze `$ErrorView` instellen op **CategoryView**.

## <a name="see-also"></a>Zie ook

[Overzicht van de cmdlet](./cmdlet-overview.md)

[Typen cmdlet-uitvoer](./types-of-cmdlet-output.md)

[Naslag informatie voor Windows Power shell](../windows-powershell-reference.md)
