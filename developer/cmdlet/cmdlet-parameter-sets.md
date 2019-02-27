---
title: Hiermee stelt u cmdlet-Parameter | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847696"
---
# <a name="cmdlet-parameter-sets"></a>Parametersets voor cmdlets

Windows PowerShell maakt gebruik van parametersets zodat u één cmdlet die u verschillende acties voor verschillende scenario's uitvoeren kunt te schrijven. Parametersets kunnen u om verschillende parameters, zodat de gebruiker zichtbaar te maken en om andere informatie op basis van de parameters die is opgegeven door de gebruiker te retourneren.

## <a name="examples-of-parameter-sets"></a>Voorbeelden van parametersets

Bijvoorbeeld, de `Get-EventLog` cmdlet (geleverd door Windows PowerShell) retourneert verschillende gegevens afhankelijk van of de gebruiker Hiermee geeft u de `List` of `LogName` parameter. Als de `List` parameter is opgegeven, wordt de cmdlet retourneert informatie over de logboekbestanden zelf, maar niet de gebeurtenisgegevens die ze bevatten. Als de `LogName` parameter is opgegeven, wordt de cmdlet retourneert informatie over de gebeurtenissen in een specifiek gebeurtenislogboek. De `List` en `LogName` parameters identificeren twee afzonderlijke parametersets.

## <a name="unique-parameter"></a>De unieke Parameter

Elke parameter is ingesteld, moet een unieke parameter die de Windows PowerShell-runtime gebruiken kunt om de juiste parameterset beschikbaar te hebben. De unieke parameter moet indien mogelijk een verplichte parameter. Als een parameter verplicht is, wordt de gebruiker wordt gedwongen om op te geven van de parameter en de Windows PowerShell-runtime kunt deze parameter gebruiken om te identificeren van de parameter is ingesteld om te gebruiken. De unieke parameter mag niet verplicht als u de cmdlet is ontworpen om te worden uitgevoerd zonder parameters op te geven.

## <a name="multiple-parameter-sets"></a>Meerdere parametersets

In de volgende afbeelding ziet u in de linkerkolom drie geldig parametersets. Parameter een uniek is voor de eerste parameter is ingesteld, parameter B uniek is voor de tweede parameter is ingesteld en parameter C uniek is voor de derde parameter is ingesteld. Echter, in de rechterkolom de parametersets geen een unieke parameter.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Parameter vereisten instellen

De volgende vereisten zijn van toepassing op alle parametersets.

- Elke parameter is ingesteld, moet ten minste één unieke parameter hebben. Indien mogelijk, maken deze parameter een verplichte parameter.

- Een parameterset waarin meerdere positionele parameters moet unieke functies voor alle parameters definiëren. Er zijn geen twee positionele parameters kunnen dezelfde positie opgeven.

- Slechts één parameter in een set kunt declareren de `ValueFromPipeline` sleutelwoord met de waarde `true`. Meerdere parameters kunnen definiëren de `ValueFromPipelineByPropertyName` sleutelwoord met de waarde `true`.

- Als er geen parameter is ingesteld voor een parameter is opgegeven, wordt de parameter hoort bij alle parametersets.

## <a name="default-parameter-sets"></a>Standaard parametersets

Wanneer er meerdere parametersets zijn gedefinieerd, kunt u de `DefaultParameterSetName` het kenmerk Cmdlet om op te geven van de standaardset van de parameter door u opgegeven trefwoord. Windows PowerShell maakt gebruik van de standaardparameter ingesteld als deze niet kan bepalen de parameter is ingesteld om te gebruiken op basis van de informatie die door de opdracht. Zie voor meer informatie over de Cmdlet-kenmerk [Cmdlet kenmerkdeclaratie](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Parametersets declareren

Voor het maken van een parameter is ingesteld, moet u de `ParameterSetName` sleutelwoord wanneer u de Parameter-kenmerk voor elke parameter in de parameterset declareren. Voor de parameters die deel uitmaken van meerdere parametersets, Voeg een parameterkenmerk voor elke parameter ingesteld. Hiermee kunt u voor het definiëren van de parameter anders voor elke parameter is ingesteld. U kunt bijvoorbeeld een parameter definiëren als in één set verplichte en optionele in een andere. Elke parameter is ingesteld, moet echter een unieke parameter bevatten.

In het volgende voorbeeld wordt de `UserName` parameter is de unieke parameter van de parameterset Test01 en de `ComputerName` parameter is de unieke parameter van de parameterset Test02. De `SharedParam` parameter behoort tot beide sets en is verplicht voor de parameter Test01 is ingesteld, maar voor de parameterset Test02 optioneel.

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```