---
title: Openbaar resource schema | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356810"
---
# <a name="public-resource-schema"></a>Schema van openbare resources

Management OData gebruikt MOF om resources en hun eigenschappen te definiëren. De eigenschappen van een OData-beheer entiteit komen overeen met de eigenschappen van het beheerde type dat door de onderliggende cmdlet wordt geretourneerd.

## <a name="defining-a-resource"></a>Een resource definiëren

Elke resource komt overeen met een object dat wordt geretourneerd door een Windows Power shell-cmdlet. In het MOF-bestand van de open bare resource definieert u een resource door een klasse te declareren. De klasse bestaat uit eigenschappen die overeenkomen met de eigenschappen van het object. In het volgende voor beeld wordt de klasse [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) vertegenwoordigd door de volgende MOF.

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

Elke eigenschaps naam wordt voorafgegaan door een gegevens type. De gegevens typen in dit voor beeld komen overeen met primitieve CLR-gegevens typen in de .NET Frameworks, maar eigenschappen kunnen ook verwijzingen naar andere bronnen of complexe typen zijn, die beide later worden beschreven.

De kwalificatie `Key` geeft aan dat een eigenschap wordt gebruikt om een bron exemplaar uniek te identificeren. Een resource kan meer dan één sleutel hebben.

De kwalificatie `Required` geeft aan dat de eigenschap vereist is. Als een eigenschap is gelabeld met de kwalificatie `Key`, wordt aangenomen dat deze vereist is en is de kwalificatie van het `Required` niet nodig.

### <a name="complex-data-types"></a>Complexe gegevens typen

Eigenschappen van entiteiten kunnen complexe gegevens typen hebben. Complexe gegevens typen zijn typen die bestaan uit andere typen, vergelijkbaar met structs in de programmeer taal C. Een complex type wordt in het MOF-bestand gedeclareerd als een klasse met de kwalificatie `ComplexType`, zoals in het volgende voor beeld.

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

Als u een entiteit eigenschap wilt declareren als een complex type, declareert u deze als een `string`-type met de `EmbeddedInstance`-kwalificatie, met inbegrip van de naam van het complexe type. In het volgende voor beeld ziet u de declaratie van een eigenschap van het type @no__t 0 dat in het vorige voor beeld is gedeclareerd.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>Entiteiten koppelen

U kunt twee entiteiten koppelen met behulp van de Association and AssociationClass-kwalificaties. Zie [beheer OData-entiteiten koppelen](./associating-management-odata-entities.md)voor meer informatie.

### <a name="derived-types"></a>Afgeleide typen

U kunt een type van een ander type afleiden. Het afgeleide type neemt alle eigenschappen over van het type waaruit het is afgeleid, naast de eigenschappen die expliciet zijn afgeleid. In het volgende voor beeld ziet u een type declaratie en vervolgens een declaratie van twee typen die zijn afgeleid van dat type.

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