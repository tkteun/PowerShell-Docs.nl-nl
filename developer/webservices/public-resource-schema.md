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
ms.openlocfilehash: a9204ca7b28fc5792ef9bd18f6b0b24964de7386
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849292"
---
# <a name="public-resource-schema"></a><span data-ttu-id="303b2-102">Schema van openbare resources</span><span class="sxs-lookup"><span data-stu-id="303b2-102">Public Resource Schema</span></span>

<span data-ttu-id="303b2-103">MOF Management OData gebruikt voor het definiëren van resources en hun eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="303b2-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="303b2-104">De eigenschappen van een entiteit Management OData komen overeen met rechtstreeks naar de eigenschappen van het beheerde type dat wordt geretourneerd door de onderliggende cmdlet.</span><span class="sxs-lookup"><span data-stu-id="303b2-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="303b2-105">Een resource te definiëren</span><span class="sxs-lookup"><span data-stu-id="303b2-105">Defining a resource</span></span>

<span data-ttu-id="303b2-106">Elke resource komt overeen met een object dat wordt geretourneerd door een Windows PowerShell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="303b2-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="303b2-107">In het publc resource MOF-bestand definieert u een resource door op te geven van een klasse.</span><span class="sxs-lookup"><span data-stu-id="303b2-107">In the publc resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="303b2-108">De klasse bestaat uit de eigenschappen die overeenkomen met de eigenschappen van het object.</span><span class="sxs-lookup"><span data-stu-id="303b2-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="303b2-109">Bijvoorbeeld, in het volgende voorbeeld wordt de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) klasse wordt vertegenwoordigd door de volgende MOF.</span><span class="sxs-lookup"><span data-stu-id="303b2-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

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

<span data-ttu-id="303b2-110">De eigenschapnaam van elke wordt voorafgegaan door een gegevenstype.</span><span class="sxs-lookup"><span data-stu-id="303b2-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="303b2-111">De gegevenstypen in dit voorbeeld komen overeen met primitieve CLR-gegevenstypen in de .NET-Frameworks, maar eigenschappen kunnen ook worden verwijzingen naar andere resources of complexe typen die zijn beide later wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="303b2-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="303b2-112">De `Key` kwalificatie geeft aan dat een eigenschap wordt gebruikt voor het aanduiden van een resource-exemplaar.</span><span class="sxs-lookup"><span data-stu-id="303b2-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="303b2-113">Een resource kan meer dan één sleutel hebben.</span><span class="sxs-lookup"><span data-stu-id="303b2-113">A resource can have more than one key.</span></span>

<span data-ttu-id="303b2-114">De `Required` kwalificatie geeft aan dat de eigenschap vereist is.</span><span class="sxs-lookup"><span data-stu-id="303b2-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="303b2-115">Als een eigenschap wordt aangeduid met de `Key` kwalificatie, deze wordt beschouwd als vereist, en de `Required` kwalificatie is niet nodig.</span><span class="sxs-lookup"><span data-stu-id="303b2-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="303b2-116">Complexe gegevenstypen</span><span class="sxs-lookup"><span data-stu-id="303b2-116">Complex data types</span></span>

<span data-ttu-id="303b2-117">Eigenschappen van entiteiten kunnen complexe gegevenstypen hebben.</span><span class="sxs-lookup"><span data-stu-id="303b2-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="303b2-118">Complexe gegevenstypen zijn typen die zijn opgebouwd uit andere typen, vergelijkbaar met de structuren in de programmeertaal.</span><span class="sxs-lookup"><span data-stu-id="303b2-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="303b2-119">Een complex type is gedeclareerd in het MOF-bestand als een klasse met de `ComplexType` kwalificatie, zoals in het volgende voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="303b2-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="303b2-120">Als u wilt een entiteitseigenschap als een complex type declareren, declareert u als een `string` type met de `EmbeddedInstance` kwalificatie, met inbegrip van de naam van het complexe type.</span><span class="sxs-lookup"><span data-stu-id="303b2-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="303b2-121">Het volgende voorbeeld hshows de declaratie van een eigenschap van de `PswsTest_ProcessModule` type gedeclareerd in het vorige voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="303b2-121">The following example hshows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="303b2-122">Entiteiten koppelen</span><span class="sxs-lookup"><span data-stu-id="303b2-122">Associating entities</span></span>

<span data-ttu-id="303b2-123">U kunt twee entiteiten koppelen met behulp van de koppeling en AssocationClass kwalificaties.</span><span class="sxs-lookup"><span data-stu-id="303b2-123">You can associate two entities by using the Association and AssocationClass qualifiers.</span></span> <span data-ttu-id="303b2-124">Zie voor meer informatie, [Management OData-entiteiten koppelen](./associating-management-odata-entities.md).</span><span class="sxs-lookup"><span data-stu-id="303b2-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="303b2-125">Afgeleide typen</span><span class="sxs-lookup"><span data-stu-id="303b2-125">Derived types</span></span>

<span data-ttu-id="303b2-126">U kunt een type afgeleid van een ander type.</span><span class="sxs-lookup"><span data-stu-id="303b2-126">You can derive a type from another type.</span></span> <span data-ttu-id="303b2-127">Het afgeleide type neemt alle van de eigenschappen van het type waarvan deze is afgeleid, naast eventuele eigenschappen expliciet afgeleid.</span><span class="sxs-lookup"><span data-stu-id="303b2-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="303b2-128">Het volgende voorbeeld ziet een typedeclaratie en vervolgens een verklaring van de twee typen die zijn afgeleid van dat type.</span><span class="sxs-lookup"><span data-stu-id="303b2-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

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