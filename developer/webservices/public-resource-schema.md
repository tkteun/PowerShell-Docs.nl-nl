---
title: Openbare Resource Schema | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057243"
---
# <a name="public-resource-schema"></a>Schema van openbare resources

MOF Management OData gebruikt voor het definiëren van resources en hun eigenschappen. De eigenschappen van een entiteit Management OData komen overeen met rechtstreeks naar de eigenschappen van het beheerde type dat wordt geretourneerd door de onderliggende cmdlet.

## <a name="defining-a-resource"></a>Een resource te definiëren

Elke resource komt overeen met een object dat wordt geretourneerd door een Windows PowerShell-cmdlet. In de openbare resource MOF-bestand definieert u een resource door op te geven van een klasse. De klasse bestaat uit de eigenschappen die overeenkomen met de eigenschappen van het object. Bijvoorbeeld, in het volgende voorbeeld wordt de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) klasse wordt vertegenwoordigd door de volgende MOF.

```csharp
class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required] SInt32 HandleCount;
    [Required] string MachineName;
    [Required] SInt32 MainWindowHandle;

    ...
};
```

De eigenschapnaam van elke wordt voorafgegaan door een gegevenstype. De gegevenstypen in dit voorbeeld komen overeen met primitieve CLR-gegevenstypen in de .NET-Frameworks, maar eigenschappen kunnen ook worden verwijzingen naar andere resources of complexe typen die zijn beide later wordt beschreven.

De `Key` kwalificatie geeft aan dat een eigenschap wordt gebruikt voor het aanduiden van een resource-exemplaar. Een resource kan meer dan één sleutel hebben.

De `Required` kwalificatie geeft aan dat de eigenschap vereist is. Als een eigenschap wordt aangeduid met de `Key` kwalificatie, deze wordt beschouwd als vereist, en de `Required` kwalificatie is niet nodig.

### <a name="complex-data-types"></a>Complexe gegevenstypen

Eigenschappen van entiteiten kunnen complexe gegevenstypen hebben. Complexe gegevenstypen zijn typen die zijn opgebouwd uit andere typen, vergelijkbaar met de structuren in de programmeertaal. Een complex type is gedeclareerd in het MOF-bestand als een klasse met de `ComplexType` kwalificatie, zoals in het volgende voorbeeld.

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

Als u wilt een entiteitseigenschap als een complex type declareren, declareert u als een `string` type met de `EmbeddedInstance` kwalificatie, met inbegrip van de naam van het complexe type. Het volgende voorbeeld ziet u de declaratie van een eigenschap van de `PswsTest_ProcessModule` type gedeclareerd in het vorige voorbeeld.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>Entiteiten koppelen

U kunt twee entiteiten koppelen met behulp van de koppeling en AssociationClass kwalificaties. Zie voor meer informatie, [Management OData-entiteiten koppelen](./associating-management-odata-entities.md).

### <a name="derived-types"></a>Afgeleide typen

U kunt een type afgeleid van een ander type. Het afgeleide type neemt alle van de eigenschappen van het type waarvan deze is afgeleid, naast eventuele eigenschappen expliciet afgeleid. Het volgende voorbeeld ziet een typedeclaratie en vervolgens een verklaring van de twee typen die zijn afgeleid van dat type.

```csharp
Class Product {

    [Key] String ProductName;

};

Class DairyProduct : Product {

    Uint16 PercentFat;
};
Class POPProduct : Product {

    Boolean IsCarbonated;
};
```