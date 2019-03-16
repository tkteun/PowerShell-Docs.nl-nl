---
title: Cmdlet die fouten rapporteren | Microsoft Docs
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
ms.openlocfilehash: 45f5934314a2871ceb921c7a66b9dfb658d0bd99
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057940"
---
# <a name="cmdlet-error-reporting"></a>Foutrapportage voor cmdlets

Cmdlets wilt laten rapporteren fouten anders, afhankelijk van of de fouten fouten wordt beëindigd of afsluitfouten. Afsluitende fouten zijn fouten die ertoe leiden dat de pijplijn moet onmiddellijk worden beëindigd of fouten die zich voordoen als er geen reden om door te gaan met de verwerking. Afsluitfouten zijn die fouten die een huidige fout rapporteren, maar de cmdlet kunt doorgaan met het verwerken van invoer objecten. De gebruiker is doorgaans op de hoogte gesteld van het probleem met afsluitfouten, maar de cmdlet voor het verwerken van de volgende invoerobject blijft.

## <a name="terminating-and-nonterminating-errors"></a>Afsluitfouten als Nonterminating

De volgende richtlijnen kunnen worden gebruikt om te bepalen of een fout wordt er een afsluitfout of een nonterminating-fout.

- Het probleem voorkomt dat uw cmdlet verwerken, is geen verdere invoer objecten? Als dit het geval is, is dit een afsluitfout.

- Is het probleem met betrekking tot een specifiek object van de invoer of een subset van invoer objecten? Als dit het geval is, is dit een nonterminating fout.

- Accepteert de cmdlet meerdere invoer-objecten, zoals dat verwerking mogelijk wel op een andere invoerobject? Als dit het geval is, is dit een nonterminating fout.

- Cmdlets die meerdere invoer objecten kunt accepteren moet kiezen tussen wat wordt beëindigd en afsluitfouten, zelfs wanneer een bepaalde situatie is van toepassing op slechts één invoer-object.

- Cmdlets kan een willekeurig aantal invoer objecten ontvangen en verzenden van een willekeurig aantal objecten voltooid of fout voordat u die een afsluitende uitzondering veroorzaakt. Er is geen relatie tussen het aantal invoer ontvangen van objecten en het aantal succes- en objecten die zijn verzonden.

- Cmdlets kan accepteren alleen 0-1 invoer objecten en alleen 0-1 genereren uitvoer van objecten moeten fouten behandelen als fouten wordt beëindigd en wordt beëindigd uitzonderingen genereren.

## <a name="reporting-nonterminating-errors"></a>Rapportage afsluitfouten

De rapportage van een nonterminating fout moet altijd worden uitgevoerd binnen de implementatie van de cmdlet van de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) methode, de [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode, of de [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methode. Dergelijke fouten worden gerapporteerd door het aanroepen van de [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode die op zijn beurt een foutrecord worden verzonden naar de foutstroom.

## <a name="reporting-terminating-errors"></a>Rapportage van fouten wordt beëindigd

Afsluitende fouten worden gerapporteerd door uitzonderingen of door het aanroepen van de [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) methode. Let erop dat cmdlets ook ontdekken en uitzonderingen, zoals OutOfMemory opnieuw genereert, maar ze zijn niet verplicht om opnieuw uitzonderingen genereren als de Windows PowerShell-runtime ze ook worden catch.

U kunt ook uw eigen uitzonderingen definiëren voor problemen die specifiek zijn voor uw situatie of aanvullende informatie toevoegen aan een bestaande uitzondering met behulp van de foutrecord.

## <a name="error-records"></a>Foutrecords

Windows PowerShell beschrijft een nonterminating fout via het gebruik van [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objecten. Elke [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object biedt foutinformatie categorie, een optionele doelobject en meer informatie over het probleem.

### <a name="error-identifiers"></a>Fout-id 's

De fout-id is een eenvoudige tekenreeks die de fout in de cmdlet aanduidt. Windows PowerShell combineert deze met een cmdlet-id voor het maken van een volledig gekwalificeerde fout-id die later kan worden gebruikt bij het filteren van foutstromen of logboekregistratie van fouten, reageren op specifieke fouten, of met andere activiteiten voor specifieke gebruikers-id.

De volgende richtlijnen moeten worden gevolgd als fout-id's op te geven.

- Andere, zeer specifieke fout-id's toewijzen aan andere codepaden. Elk codepad die worden aangeroepen [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) of [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) zijn eigen fout-id moet hebben.

- Fout-id's moeten uniek zijn voor CLR-uitzonderingstypen voor zowel afsluitfouten als nonterminating.

- De semantiek van een fout-id tussen versies van de cmdlet of Windows PowerShell-provider niet wijzigen. Wanneer de semantiek van een fout-id is ingesteld, moet deze ongewijzigd blijft gedurende de levenscyclus van de cmdlet.

- Gebruik een unieke fout-id voor een bepaald type van de CLR-uitzondering voor de afsluitende fouten. Als het uitzonderingstype wordt gewijzigd, gebruikt u een nieuwe fout-id.

- Voor afsluitfouten, gebruikt u een specifieke fout-id voor een specifiek object van de invoer.

- Kies tekst voor de id die tersely komt overeen met de fout wordt gerapporteerd. Gebruik geen spaties of leestekens.

- Geen fout-id's die niet reproduceerbaar worden gegenereerd. Bijvoorbeeld, id's die een proces-id niet genereren. Fout-id's zijn handig alleen als ze overeenkomen met de id's die zijn zichtbaar voor andere gebruikers die hetzelfde probleem ondervindt.

### <a name="error-categories"></a>Foutcategorieën

Foutcategorieën worden gebruikt voor het groeperen van fouten voor de eindgebruiker. Windows PowerShell definieert deze categorieën en -cmdlets en providers van Windows PowerShell moeten kiezen tussen deze bij het genereren van de foutrecord.

Zie voor een beschrijving van de foutcategorieën die beschikbaar zijn, de [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) opsomming. In het algemeen Vermijd het gebruik van NoError UndefinedError en GenericError indien mogelijk.

Gebruikers kunnen fouten op basis van categorie wanneer ze ingesteld bekijken '`$ErrorView`' naar 'CategoryView'.

## <a name="see-also"></a>Zie ook

[Windows PowerShell-Cmdlets](./cmdlet-overview.md)

[Cmdlet-uitvoer](./types-of-cmdlet-output.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
