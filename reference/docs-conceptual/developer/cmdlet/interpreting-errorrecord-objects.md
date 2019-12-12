---
title: ErrorRecord-objecten interpreteren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: 32ebf2531237bfd1042310ccc4155193a58401fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356215"
---
# <a name="interpreting-errorrecord-objects"></a>ErrorRecord-objecten interpreteren

In de meeste gevallen vertegenwoordigt het object [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) een niet-afsluit bare fout die is gegenereerd door een opdracht of script. Bij het beëindigen van fouten kunt u ook de aanvullende gegevens in een ErrorRecord opgeven via de interface [System. Management. Automation. Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) .

Als u een foutafhandelingsroutine in uw script of een host wilt schrijven voor het verwerken van specifieke fouten die optreden tijdens het uitvoeren van de opdracht of het script, moet u het object [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) interpreteren om te bepalen of het de fout klasse vertegenwoordigt die u wilt verwerken.

Wanneer een cmdlet een afsluitende of niet-afsluit fout tegen komt, moet er een fout record worden gemaakt waarin de fout voorwaarde wordt beschreven. De hosttoepassing moet deze fout records onderzoeken en elke actie uitvoeren die de fout vermindert. De hosttoepassing moet ook fout records onderzoeken voor niet-afsluit fouten waarvoor een record niet kan worden verwerkt, maar wel kunnen door gaan, en er moeten fout records worden onderzocht voor afsluit fouten waardoor de pijp lijn is gestopt.

> [!NOTE]
> Voor het beëindigen van fouten roept de cmdlet de methode [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) aan. Voor niet-afsluit fouten roept de cmdlet de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aan.

## <a name="error-record-design"></a>Fout record ontwerp

Fout records zijn bedoeld om aanvullende fout informatie te bieden die niet beschikbaar is in uitzonde ringen, terwijl u ervoor zorgt dat de gecombineerde gegevens in elke fout record uniek zijn. Met deze unieke waarde kan de hosttoepassing de verschillende delen van de fout record controleren, zodat deze de fout voorwaarde kan identificeren en de actie die de host moet uitvoeren.

## <a name="interpreting-error-records"></a>Fout records interpreteren

U kunt verschillende delen van de fout record bekijken om de fout te identificeren. Dit zijn onder andere de volgende onderdelen:

- De fout categorie

- De fout uitzondering

- De volledig gekwalificeerde fout-id (FQID)

- Andere informatie

### <a name="the-error-category"></a>De fout categorie

De fout categorie van de fout record is een van de vooraf gedefinieerde constanten die worden opgegeven door de inventarisatie [System. Management. Automation. Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) . Deze informatie is beschikbaar via de eigenschap [System. Management. Automation. ErrorRecord. CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) van het object [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) .

Met de cmdlet kunt u de categorieën CloseError, openerror, InvalidType, ReadError en WriteError en andere fout Categorieën opgeven. De hosttoepassing kan de fout categorie gebruiken om groepen fouten vast te leggen.

### <a name="the-exception"></a>De uitzonde ring

De uitzonde ring die is opgenomen in de fout record wordt geleverd door de cmdlet en kan worden geopend via de eigenschap [System. Management. Automation. ErrorRecord. Exception *](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) van het object [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) .

Hosttoepassingen kunnen het sleutel woord `is` gebruiken om te bepalen dat de uitzonde ring van een specifieke klasse of van een afgeleide klasse is. Het is beter vertakking op het uitzonderings type, zoals wordt weer gegeven in het volgende voor beeld.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

Op deze manier worden de afgeleide klassen onderschept. Er zijn echter problemen als de uitzonde ring wordt gedeserialiseerd.

### <a name="the-fqid"></a>De FQID

De FQID is de meest specifieke informatie die u kunt gebruiken om de fout te identificeren. Het is een teken reeks die een door een cmdlet gedefinieerde id, de naam van de cmdlet-klasse en de bron die de fout heeft gerapporteerd bevat. In het algemeen is een fout record gelijk aan een gebeurtenis record van een Windows-gebeurtenis logboek. De FQID is vergelijkbaar met de volgende tuple, waarmee de klasse van de gebeurtenis record wordt geïdentificeerd: (*logboek naam*, *bron*, *gebeurtenis-id*).

De FQID is ontworpen om te worden geïnspecteerd als één teken reeks. Er zijn echter gevallen waarin de fout-id is ontworpen om te worden geparseerd door de hosttoepassing. Het volgende voor beeld is een goed gevormde, volledig gekwalificeerde fout-id.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

In het vorige voor beeld is het eerste token de fout-id, gevolgd door de naam van de cmdlet-klasse. De fout-id kan één token zijn, of kan een met punt gescheiden id zijn die vertakking op inspectie van de id toestaat. Gebruik geen spaties of lees tekens in de fout-id. Het is vooral belang rijk dat u geen komma gebruikt. een komma wordt door Windows Power shell gebruikt voor het scheiden van de id en de naam van de cmdlet-klasse.

### <a name="other-information"></a>Andere informatie

Het object [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) bevat mogelijk ook informatie over de omgeving waarin de fout is opgetreden. Deze informatie omvat items zoals fout details, aanroep informatie en het doel object dat werd verwerkt toen de fout optrad. Hoewel deze informatie nuttig kan zijn voor de hosttoepassing, wordt deze meestal niet gebruikt om de fout te identificeren. Deze informatie is beschikbaar via de volgende eigenschappen:

[System. Management. Automation. ErrorRecord. error Details](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System. Management. Automation. ErrorRecord. InvocationInfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System. Management. Automation. ErrorRecord. target object](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>Zie ook

[System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System. Management. Automation. Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System. Management. Automation. Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[Niet-beëindigde fout rapportage toevoegen aan uw cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows Power Shell-fout rapportage](./error-reporting-concepts.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
