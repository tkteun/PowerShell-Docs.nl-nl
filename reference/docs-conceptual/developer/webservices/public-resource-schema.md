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
# <a name="public-resource-schema"></a><span data-ttu-id="75c57-102">Schema van openbare resources</span><span class="sxs-lookup"><span data-stu-id="75c57-102">Public Resource Schema</span></span>

<span data-ttu-id="75c57-103">Management OData gebruikt MOF om resources en hun eigenschappen te definiëren.</span><span class="sxs-lookup"><span data-stu-id="75c57-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="75c57-104">De eigenschappen van een OData-beheer entiteit komen overeen met de eigenschappen van het beheerde type dat door de onderliggende cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="75c57-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="75c57-105">Een resource definiëren</span><span class="sxs-lookup"><span data-stu-id="75c57-105">Defining a resource</span></span>

<span data-ttu-id="75c57-106">Elke resource komt overeen met een object dat wordt geretourneerd door een Windows Power shell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="75c57-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="75c57-107">In het MOF-bestand van de open bare resource definieert u een resource door een klasse te declareren.</span><span class="sxs-lookup"><span data-stu-id="75c57-107">In the public resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="75c57-108">De klasse bestaat uit eigenschappen die overeenkomen met de eigenschappen van het object.</span><span class="sxs-lookup"><span data-stu-id="75c57-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="75c57-109">In het volgende voor beeld wordt de klasse [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) vertegenwoordigd door de volgende MOF.</span><span class="sxs-lookup"><span data-stu-id="75c57-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

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

<span data-ttu-id="75c57-110">Elke eigenschaps naam wordt voorafgegaan door een gegevens type.</span><span class="sxs-lookup"><span data-stu-id="75c57-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="75c57-111">De gegevens typen in dit voor beeld komen overeen met primitieve CLR-gegevens typen in de .NET Frameworks, maar eigenschappen kunnen ook verwijzingen naar andere bronnen of complexe typen zijn, die beide later worden beschreven.</span><span class="sxs-lookup"><span data-stu-id="75c57-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="75c57-112">De kwalificatie `Key` geeft aan dat een eigenschap wordt gebruikt om een bron exemplaar uniek te identificeren.</span><span class="sxs-lookup"><span data-stu-id="75c57-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="75c57-113">Een resource kan meer dan één sleutel hebben.</span><span class="sxs-lookup"><span data-stu-id="75c57-113">A resource can have more than one key.</span></span>

<span data-ttu-id="75c57-114">De kwalificatie `Required` geeft aan dat de eigenschap vereist is.</span><span class="sxs-lookup"><span data-stu-id="75c57-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="75c57-115">Als een eigenschap is gelabeld met de kwalificatie `Key`, wordt aangenomen dat deze vereist is en is de kwalificatie van het `Required` niet nodig.</span><span class="sxs-lookup"><span data-stu-id="75c57-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="75c57-116">Complexe gegevens typen</span><span class="sxs-lookup"><span data-stu-id="75c57-116">Complex data types</span></span>

<span data-ttu-id="75c57-117">Eigenschappen van entiteiten kunnen complexe gegevens typen hebben.</span><span class="sxs-lookup"><span data-stu-id="75c57-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="75c57-118">Complexe gegevens typen zijn typen die bestaan uit andere typen, vergelijkbaar met structs in de programmeer taal C.</span><span class="sxs-lookup"><span data-stu-id="75c57-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="75c57-119">Een complex type wordt in het MOF-bestand gedeclareerd als een klasse met de kwalificatie `ComplexType`, zoals in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="75c57-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="75c57-120">Als u een entiteit eigenschap wilt declareren als een complex type, declareert u deze als een `string`-type met de `EmbeddedInstance`-kwalificatie, met inbegrip van de naam van het complexe type.</span><span class="sxs-lookup"><span data-stu-id="75c57-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="75c57-121">In het volgende voor beeld ziet u de declaratie van een eigenschap van het type @no__t 0 dat in het vorige voor beeld is gedeclareerd.</span><span class="sxs-lookup"><span data-stu-id="75c57-121">The following example shows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="75c57-122">Entiteiten koppelen</span><span class="sxs-lookup"><span data-stu-id="75c57-122">Associating entities</span></span>

<span data-ttu-id="75c57-123">U kunt twee entiteiten koppelen met behulp van de Association and AssociationClass-kwalificaties.</span><span class="sxs-lookup"><span data-stu-id="75c57-123">You can associate two entities by using the Association and AssociationClass qualifiers.</span></span> <span data-ttu-id="75c57-124">Zie [beheer OData-entiteiten koppelen](./associating-management-odata-entities.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="75c57-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="75c57-125">Afgeleide typen</span><span class="sxs-lookup"><span data-stu-id="75c57-125">Derived types</span></span>

<span data-ttu-id="75c57-126">U kunt een type van een ander type afleiden.</span><span class="sxs-lookup"><span data-stu-id="75c57-126">You can derive a type from another type.</span></span> <span data-ttu-id="75c57-127">Het afgeleide type neemt alle eigenschappen over van het type waaruit het is afgeleid, naast de eigenschappen die expliciet zijn afgeleid.</span><span class="sxs-lookup"><span data-stu-id="75c57-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="75c57-128">In het volgende voor beeld ziet u een type declaratie en vervolgens een declaratie van twee typen die zijn afgeleid van dat type.</span><span class="sxs-lookup"><span data-stu-id="75c57-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

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