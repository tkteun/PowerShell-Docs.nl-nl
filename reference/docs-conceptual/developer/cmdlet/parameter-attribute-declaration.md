---
title: Parameter kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: 81b1ed95669f51ba554f6f99031d098e239f02e0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356173"
---
# <a name="parameter-attribute-declaration"></a>Declaratie van het kenmerk Parameter

Het parameter kenmerk identificeert een open bare eigenschap van de cmdlet-klasse als een cmdlet-para meter.

## <a name="syntax"></a>Syntaxis

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Parameters

`Mandatory` ([System. Boolean](/dotnet/api/System.Boolean)) een optionele benoemde para meter. `True` geeft aan dat de cmdlet-para meter is vereist. Als een vereiste para meter niet wordt opgegeven wanneer de cmdlet wordt aangeroepen, vraagt Windows Power shell de gebruiker om een parameter waarde. De standaardwaarde is `false`.

`ParameterSetName` ([System. String](/dotnet/api/System.String)) een optionele benoemde para meter. Hiermee geeft u de para meter instellen waarvan deze cmdlet-para meter deel uitmaakt. Als er geen parameterset is opgegeven, hoort de para meter bij alle parameter sets.

`Position` ([System. Int32](/dotnet/api/System.Int32)) een optionele benoemde para meter. Hiermee geeft u de positie van de para meter in een Windows Power shell-opdracht.

`ValueFromPipeline` ([System. Boolean](/dotnet/api/System.Boolean)) een optionele benoemde para meter. `True` geeft aan dat de cmdlet-para meter de waarde ervan uit een pijplijn object haalt. Geef dit tref woord op als de cmdlet toegang heeft tot het volledige object, niet alleen een eigenschap van het object. De standaardwaarde is `false`.

`ValueFromPipelineByPropertyName` ([System. Boolean](/dotnet/api/System.Boolean)) een optionele benoemde para meter. `True` geeft aan dat de cmdlet-para meter de waarde van een eigenschap van een pijplijn object met dezelfde naam of dezelfde alias als deze para meter heeft. Als de cmdlet bijvoorbeeld een `Name`-para meter heeft en het pijplijn object ook een eigenschap `Name` heeft, wordt de waarde van de eigenschap `Name` toegewezen aan de para meter `Name` van de cmdlet. De standaardwaarde is `false`.

`ValueFromRemainingArguments` ([System. Boolean](/dotnet/api/System.Boolean)) een optionele benoemde para meter. `True` geeft aan dat de cmdlet-para meter alle resterende argumenten accepteert die worden door gegeven aan de cmdlet. De standaardwaarde is `false`.

`HelpMessage` optionele benoemde para meter. Hiermee geeft u een korte beschrijving van de para meter. In Windows Power shell wordt dit bericht weer gegeven wanneer een cmdlet wordt uitgevoerd en er geen verplichte para meter is opgegeven.

`HelpMessageBaseName` optionele benoemde para meter. Hiermee geeft u de locatie op waar resource-id's zich bevinden. Met deze para meter kan bijvoorbeeld een bron-assembly worden opgegeven die Help-berichten bevat die u wilt lokaliseren.

`HelpMessageResourceId` optionele benoemde para meter. Hiermee wordt de resource-id voor een Help-bericht opgegeven.

## <a name="remarks"></a>Opmerkingen

- Zie voor meer informatie over het declareren van dit kenmerk [cmdlet-para meters declareren](./how-to-declare-cmdlet-parameters.md).

- Een cmdlet kan een wille keurig aantal para meters hebben. Voor een betere gebruikers ervaring beperkt u echter het aantal para meters.

- Para meters moeten worden gedeclareerd voor open bare niet-statische velden of eigenschappen. Para meters moeten worden gedeclareerd voor eigenschappen. De eigenschap moet een accessor voor een open bare set hebben en als het sleutel woord `ValueFromPipeline` of `ValueFromPipelineByPropertyName` is opgegeven, moet de eigenschap een open bare Get-accessor hebben.

- Wanneer u positionele para meters opgeeft, beperkt u het aantal positionele para meters in een para meter ingesteld op minder dan vijf. En positionele para meters hoeven niet aaneengesloten te zijn. De posities 5, 100 en 250 werken hetzelfde als de posities 0, 1 en 2.

- Wanneer het sleutel woord `Position` niet is opgegeven, moet er naar de cmdlet-para meter worden verwezen met de naam.

- Let op het volgende wanneer u parameter sets gebruikt:

    - Elke parameterset moet ten minste één unieke para meter hebben. Goede cmdlet-ontwerp geeft aan dat deze unieke para meter ook verplicht moet zijn, indien mogelijk. Als uw cmdlet is ontworpen om zonder para meters te worden uitgevoerd, kan de unieke para meter niet verplicht zijn.

    - Geen enkele parameterset mag meer dan één positionele para meter met dezelfde positie bevatten.

    - Er mag slechts één para meter in een parameterset `ValueFromPipeline = true` declareren. Meerdere para meters kunnen `ValueFromPipelineByPropertyName = true` definiëren.

    - Meerdere para meters kunnen `ValueFromPipelineByPropertyName = true` definiëren.

- Zie [cmdlet para meter names](standard-cmdlet-parameter-names-and-types.md)(Engelstalig) voor meer informatie over de richt lijnen voor parameter namen.

- Het parameter kenmerk wordt gedefinieerd door de klasse [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .

## <a name="see-also"></a>Zie ook

[System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Cmdlet-parameter namen](standard-cmdlet-parameter-names-and-types.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
