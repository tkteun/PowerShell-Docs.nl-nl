---
title: Cmdlet-parameter sets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: d8c00c7ffd369a32af151836785a2c5f47b05a68
ms.sourcegitcommit: 889b93d170aeb3d444288e7ccf67e62ce822cb7c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70936190"
---
# <a name="cmdlet-parameter-sets"></a>Cmdlet-parameter sets

Power shell gebruikt parameter sets om een enkele cmdlet te schrijven die verschillende acties voor verschillende scenario's kan uitvoeren. Met parameter sets kunt u verschillende para meters voor de gebruiker beschikbaar maken. En om andere informatie te retour neren op basis van de para meters die door de gebruiker zijn opgegeven.

## <a name="examples-of-parameter-sets"></a>Voor beelden van parameter sets

De Power shell `Get-EventLog` -cmdlet retourneert bijvoorbeeld verschillende informatie, afhankelijk van het feit of de gebruiker de para meter **List** of **LogName** opgeeft. Als de **List** -para meter is opgegeven, retourneert de cmdlet informatie over de logboek bestanden zelf, maar niet de gebeurtenis gegevens die ze bevatten. Als de para meter **LogName** is opgegeven, retourneert de cmdlet informatie over de gebeurtenissen in een specifiek gebeurtenis logboek. De para meters **List** en **LogName** identificeren twee afzonderlijke parameter sets.

## <a name="unique-parameter"></a>Unieke para meter

Elke parameterset moet een unieke para meter hebben die door de Power shell-runtime wordt gebruikt om de juiste parameterset beschikbaar te stellen. Indien mogelijk moet de unieke para meter een verplichte para meter zijn. Als een para meter verplicht is, moet de gebruiker de para meter opgeven en gebruikt de Power shell-runtime die para meter om de parameterset te identificeren. De unieke para meter kan niet verplicht zijn als uw cmdlet is ontworpen om te worden uitgevoerd zonder para meters op te geven.

## <a name="multiple-parameter-sets"></a>Meerdere parameter sets

In de volgende afbeelding ziet u in de linkerkolom drie geldige parameter sets. **Para meter A** is uniek voor de eerste parameterset, **para meter B** is uniek voor de tweede parameterset en **para meter C** is uniek voor de derde parameterset. In de rechter kolom hebben de parameters sets geen unieke para meter.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Vereisten voor de parameterset

De volgende vereisten zijn van toepassing op alle parameter sets.

- Elke parameterset moet ten minste één unieke para meter hebben. Indien mogelijk moet u voor deze para meter een verplichte para meter opgeven.

- Een parameterset met meerdere positionele para meters moet unieke posities definiëren voor elke para meter. Er kunnen niet twee positionele para meters dezelfde positie opgeven.

- Slechts één para meter in een set kan het `ValueFromPipeline` tref woord declareren met `true`een waarde van.
  Meerdere para meters kunnen `ValueFromPipelineByPropertyName` het sleutel woord definiëren met `true`een waarde van.

- Als er geen parameterset voor een para meter is opgegeven, hoort de para meter bij alle parameter sets.

> [!NOTE]
> Voor een cmdlet of functie geldt een limiet van 32 parameter sets.

## <a name="default-parameter-sets"></a>Standaard parameters sets

Wanneer er meerdere parameter sets zijn gedefinieerd, kunt u het `DefaultParameterSetName` sleutel woord van het **cmdlet** -kenmerk gebruiken om de standaard parameterset op te geven. Power shell gebruikt de standaard parameterset als de ingestelde para meter niet kan worden bepaald op basis van de informatie die wordt verstrekt door de opdracht. Zie voor meer informatie over het **cmdlet** -kenmerk de [cmdlet-kenmerk declaratie](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Parameter sets declareren

Als u een parameterset wilt maken, moet u `ParameterSetName` het sleutel woord opgeven wanneer u het **parameter** kenmerk declareert voor elke para meter in de parameterset. Voor para meters die bij meerdere parameter sets horen, voegt u een **parameter** kenmerk toe voor elke parameterset. Met dit kenmerk kunt u de para meter op verschillende manieren definiëren voor elke parameterset. U kunt bijvoorbeeld een para meter definiëren als verplicht in de ene set en optioneel in een andere. Elke parameterset moet echter één unieke para meter bevatten. Zie [para meter kenmerk declaratie](parameter-attribute-declaration.md)voor meer informatie.

In het volgende voor beeld is de para meter **username** de unieke para meter `Test01` van de parameterset en de para meter **ComputerName** is de unieke para meter `Test02` van de para meter set. De para meter **SharedParam** behoort tot beide sets en is verplicht voor `Test01` de ingestelde para meter, `Test02` maar is optioneel voor de parameterset.

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
private string sharedParam;
```
