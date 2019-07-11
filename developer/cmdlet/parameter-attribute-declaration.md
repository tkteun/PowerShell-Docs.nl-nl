---
title: Kenmerk parameterdeclaratie | Microsoft Docs
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
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735130"
---
# <a name="parameter-attribute-declaration"></a>Declaratie van het kenmerk Parameter

De Parameter-kenmerk geeft aan dat een openbare eigenschap van de cmdlet-klasse cmdlet-parameter.

## <a name="syntax"></a>Syntaxis

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>Parameters

`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) met de naam van parameter optioneel. `True` Geeft aan dat de cmdlet-parameter is vereist. Als een vereiste parameter niet is opgegeven wanneer de cmdlet wordt aangeroepen, wordt de gebruiker voor een parameterwaarde gevraagd in Windows PowerShell. De standaardwaarde is `false`.

`ParameterSetName` ([System.String](/dotnet/api/System.String)) met de naam van parameter optioneel. Hiermee geeft u dat de parameter ingesteld dat deze cmdlet-parameter deel uitmaakt. Als er geen parameterset is opgegeven, wordt de parameter hoort bij alle parametersets.

`Position` ([System.Int32](/dotnet/api/System.Int32)) met de naam van parameter optioneel. Hiermee geeft u de positie van de parameter in een Windows PowerShell-opdracht.

`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) met de naam van parameter optioneel. `True` Geeft aan dat de cmdlet-parameter de waarde van een pijplijn-object heeft. Dit trefwoord opgeven als de cmdlet toegang heeft tot de volledige-object is niet alleen een eigenschap van het object. De standaardwaarde is `false`.

`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) met de naam van parameter optioneel. `True` Geeft aan dat de cmdlet-parameter heeft de waarde van een eigenschap van een pijplijn-object met dezelfde naam of de dezelfde alias als deze parameter. Bijvoorbeeld, als de cmdlet heeft een `Name` parameter en de pijplijn-object heeft ook een `Name` eigenschap, de waarde van de `Name` eigenschap is toegewezen aan de `Name` parameter van de cmdlet. De standaardwaarde is `false`.

`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) met de naam van parameter optioneel. `True` Geeft aan dat de parameter van de cmdlet alle resterende argumenten die zijn doorgegeven aan de cmdlet accepteert. De standaardwaarde is `false`.

`HelpMessage` De optionele parameter met de naam. Hiermee geeft u een korte beschrijving van de parameter. Windows PowerShell wordt deze weergegeven als een cmdlet wordt uitgevoerd en een verplichte parameter is niet opgegeven.

`HelpMessageBaseName` De optionele parameter met de naam. Hiermee geeft u de locatie waar de resource-id's zich bevinden. Deze parameter kan bijvoorbeeld opgeven dat een resource-assembly met Help-berichten die u wilt om te lokaliseren.

`HelpMessageResourceId` De optionele parameter met de naam. Hiermee geeft u de resource-id voor een Help-bericht.

## <a name="remarks"></a>Opmerkingen

- Zie voor meer informatie over hoe u dit kenmerk declareren [hoe u de Cmdlet-Parameters declareren](./how-to-declare-cmdlet-parameters.md).

- Een cmdlet kan een onbeperkt aantal parameters hebben. Echter voor een betere ervaring voor eindgebruikers, beperkt u het aantal parameters.

- Parameters moeten worden gedeclareerd voor het openbare niet-statische velden of properties. Parameters moeten worden gedeclareerd voor eigenschappen. De eigenschap een openbare set-accessor moet hebben en als de `ValueFromPipeline` of `ValueFromPipelineByPropertyName` sleutelwoord is opgegeven, moet de eigenschap een openbare get-accessor heeft hebben.

- Wanneer u positionele parameters opgeeft, moet u het aantal positionele parameters in een parameter is ingesteld op minder dan vijf beperken. En positionele parameters hoeft niet aaneengesloten te zijn. Posities 5, 100 en 250 werken op dezelfde manier als posities 0, 1 en 2.

- Wanneer de `Position` sleutelwoord niet is opgegeven, wordt de cmdlet-parameter moet worden verwezen door de naam ervan.

- Wanneer u parametersets gebruikt, Let op het volgende:

    - Elke parameter is ingesteld, moet ten minste één unieke parameter hebben. Goede cmdlet ontwerp geeft aan dat deze unieke parameter moet ook zijn verplicht, indien mogelijk. Als de cmdlet is ontworpen om te worden uitgevoerd zonder parameters, is de unieke parameter kan niet verplicht.

    - Er is geen parameter ingesteld moet meer dan één positionele parameter met dezelfde positie bevatten.

    - Slechts één parameter in een parameterset moet declareren `ValueFromPipeline = true`. Meerdere parameters kunnen definiëren `ValueFromPipelineByPropertyName = true`.

    - Meerdere parameters kunnen definiëren `ValueFromPipelineByPropertyName = true`.

- Zie voor meer informatie over de richtlijnen voor de namen van parameters [namen van de Cmdlet-parameters](standard-cmdlet-parameter-names-and-types.md).

- De parameterkenmerk wordt gedefinieerd door de [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) klasse.

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Namen van de cmdlet-Parameter](standard-cmdlet-parameter-names-and-types.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
