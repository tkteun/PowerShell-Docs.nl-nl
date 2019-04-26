---
title: Interpreteren ErrorRecord objecten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: 32ebf2531237bfd1042310ccc4155193a58401fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067634"
---
# <a name="interpreting-errorrecord-objects"></a>ErrorRecord-objecten interpreteren

In de meeste gevallen een [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object vertegenwoordigt een niet-afsluitfout die worden gegenereerd door een opdracht of script. Beëindigen van fouten kunt ook opgeven de aanvullende gegevens in een ErrorRecord via de [System.Management.Automation.Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) interface.

Als u de foutafhandeling schrijven in uw script of een host wilt voor het afhandelen van specifieke fouten die optreden tijdens het uitvoeren van de opdracht of script, u moet interpreteren de [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object om te bepalen of deze Hiermee geeft u de klasse van de fout die u wilt verwerken.

Wanneer een cmdlet wordt een afsluitende aangetroffen of niet-afsluitfout, moet deze een foutrecord die worden beschreven het probleem te maken. De hosttoepassing moet deze foutrecords onderzoeken en welke actie wordt de fout verhelpen uitvoeren. De hosttoepassing moet ook onderzoeken foutrecords voor afsluitfouten die is mislukt voor het verwerken van een record, maar konden om door te gaan en deze moet onderzoeken van foutrecords voor afsluitende fouten waardoor de pijplijn te stoppen.

> [!NOTE]
> Voor fouten wordt beëindigd, de cmdlet roept de [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) methode. Voor niet-afsluitfouten, de cmdlet roept de [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode.

## <a name="error-record-design"></a>Fout bij vastleggen ontwerp

Foutrecords zijn ontworpen om u te bieden aanvullende informatie die is niet beschikbaar in uitzonderingen terwijl ervoor te zorgen dat de gecombineerde gegevens in elke foutrecord uniek is. Deze uniekheid kan de hosttoepassing om te controleren van de verschillende onderdelen van de foutrecord zodat deze het probleem identificeren kunt en de host van de actie moet ondernemen.

## <a name="interpreting-error-records"></a>Interpretatie van foutrecords

U kunt verschillende onderdelen van de foutrecord om de fout vast te bekijken. Deze onderdelen zijn onder andere het volgende:

- De Foutcategorie

- De foutuitzondering

- De volledig gekwalificeerde fout-id (FQID)

- Andere informatie

### <a name="the-error-category"></a>De Foutcategorie

De Foutcategorie van de foutrecord is een van de vooraf gedefinieerde constanten geleverd door de [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) opsomming. Deze informatie is beschikbaar via de [System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) eigenschap van de [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object.

De cmdlet kunt opgeven voor de categorieën CloseError, OpenError, InvalidType, ReadError en WriteError, en andere fout. De hosttoepassing kunt u de Foutcategorie gebruiken om vast te leggen van groepen van fouten.

### <a name="the-exception"></a>De uitzondering

De uitzondering die is opgenomen in de foutrecord wordt geleverd door de cmdlet en is toegankelijk via de [System.Management.Automation.ErrorRecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) eigenschap van de [ System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object.

Hosttoepassingen kunnen gebruikmaken van de `is` trefwoord dat u wilt dat de uitzondering van een bepaalde klasse of van een afgeleide klasse is identificeren. Het is beter om branch via het uitzonderingstype, zoals wordt weergegeven in het volgende voorbeeld.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

Op deze manier u variabel de afgeleide klassen. Er zijn echter problemen als de uitzondering is gedeserialiseerd.

### <a name="the-fqid"></a>De FQID

De FQID is de meest specifieke informatie die u gebruiken kunt voor het identificeren van de fout. Het is een tekenreeks die bestaat uit een cmdlet gedefinieerde id, de naam van de cmdlet-klasse en de bron die de fout gemeld. In het algemeen is een foutrecord vergelijkbaar met de gebeurtenisrecord van een van een Windows-gebeurtenislogboek. De FQID is vergelijkbaar met de volgende tuple, waarin de klasse van de record van de gebeurtenis: (*logboeknaam*, *bron*, *gebeurtenis-ID*).

De FQID is ontworpen om te worden gecontroleerd op een enkele tekenreeks. Echter bestaan gevallen waarin de fout-id is ontworpen om te worden geparseerd door de hosttoepassing. Het volgende voorbeeld is een goed ingedeelde volledig gekwalificeerde fout-id.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

In het vorige voorbeeld is de eerste token de fout-id, die wordt gevolgd door de naam van de cmdlet-klasse. De fout-id kan een enkele token, of een punt gescheiden id voor de vertakking van de inspectie van de id kan zijn. Gebruik geen spaties of leestekens in de fout-id. Is het belangrijk om niet te gebruiken van een door komma's; een door komma's wordt gebruikt door Windows PowerShell voor het scheiden van de id en de naam van de cmdlet-klasse.

### <a name="other-information"></a>Andere informatie

De [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object bieden mogelijk ook informatie over de omgeving waarin de fout is opgetreden. Deze informatie omvat items zoals foutdetails, aanroepen van gegevens en het doelobject dat wordt verwerkt als de fout is opgetreden. Hoewel deze informatie mogelijk nuttig voor de host-toepassing, wordt deze niet doorgaans gebruikt voor het identificeren van de fout. Deze informatie is beschikbaar via de volgende eigenschappen:

[System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System.Management.Automation.ErrorRecord.InvocationInfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System.Management.Automation.ErrorRecord.TargetObject](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>Zie ook

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[Toevoegen van niet-afsluitfouten die fouten rapporteren aan uw Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell die fouten rapporteren](./error-reporting-concepts.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
