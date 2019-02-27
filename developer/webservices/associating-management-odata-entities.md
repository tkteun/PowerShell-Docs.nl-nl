---
title: U koppelt Management OData-entiteiten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850188"
---
# <a name="associating-management-odata-entities"></a><span data-ttu-id="84ae6-102">Management OData-entiteiten koppelen</span><span class="sxs-lookup"><span data-stu-id="84ae6-102">Associating Management OData Entities</span></span>

<span data-ttu-id="84ae6-103">Het is vaak handig voor het maken van een koppeling tussen twee verschillende Management OData-entiteiten.</span><span class="sxs-lookup"><span data-stu-id="84ae6-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="84ae6-104">Bijvoorbeeld, een OData-Management-service kan beschikt over entiteiten die een lijst van producten die zijn ingedeeld in categorieën beheren en de entiteiten definiëren `Product` en `Category`.</span><span class="sxs-lookup"><span data-stu-id="84ae6-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="84ae6-105">Een client krijgen door deze twee entiteiten koppelen, informatie over alle producten in een categorie aan een enkele aanvraag met de webservice.</span><span class="sxs-lookup"><span data-stu-id="84ae6-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="84ae6-106">Een voorbeeld over het maken van koppelingen tussen entiteiten kan worden gedownload op [koppeling voorbeeld](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span><span class="sxs-lookup"><span data-stu-id="84ae6-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="84ae6-107">Het maken van de koppeling in het schemabestand resource</span><span class="sxs-lookup"><span data-stu-id="84ae6-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="84ae6-108">De volgende MOF definieert twee entiteiten.</span><span class="sxs-lookup"><span data-stu-id="84ae6-108">The following MOF defines two entities.</span></span> <span data-ttu-id="84ae6-109">We gaan een koppeling tussen deze maken.</span><span class="sxs-lookup"><span data-stu-id="84ae6-109">We will create an association between them.</span></span>

```csharp
class Product {

[key] string ProductName;

// other fields ...
};

class Category {

[key] string CategoryName;

string Products[];

// other fields
}
```

<span data-ttu-id="84ae6-110">De `Category` klasse definieert een eigenschap die een matrix van de namen van de producten die deel uitmaken van deze categorie.</span><span class="sxs-lookup"><span data-stu-id="84ae6-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="84ae6-111">Als u wilt koppelen twee entiteiten, definieert u een klasse met de `Association` kenmerk in het resource-schema MOF-bestand voor de service.</span><span class="sxs-lookup"><span data-stu-id="84ae6-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="84ae6-112">De twee entiteiten die zijn gekoppeld, met de naam moet definiëren van de klasse `ends` van de koppeling.</span><span class="sxs-lookup"><span data-stu-id="84ae6-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="84ae6-113">Het volgende voorbeeld bevat een definitie van een klasse die een koppeling tussen de categorie en producten entiteiten definieert.</span><span class="sxs-lookup"><span data-stu-id="84ae6-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="84ae6-114">U moet ook de declaratie van de eigenschap producten in de categorie-klasse wijzigen.</span><span class="sxs-lookup"><span data-stu-id="84ae6-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="84ae6-115">U gebruikt de `AssociationClass` trefwoord om op te geven dat de eigenschap ene uiteinde van de koppeling is.</span><span class="sxs-lookup"><span data-stu-id="84ae6-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="84ae6-116">De eigenschap moet ook worden gedefinieerd als een verwijzing naar een aparte entiteit in plaats van een matrix met tekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="84ae6-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="84ae6-117">U dit doen met behulp van de `ref` trefwoord.</span><span class="sxs-lookup"><span data-stu-id="84ae6-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="84ae6-118">Het volgende voorbeeld ziet de definitie van de eigenschap voor de koppeling.</span><span class="sxs-lookup"><span data-stu-id="84ae6-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="84ae6-119">Ten slotte het andere uiteinde van de koppeling moet worden gedeclareerd door toe te voegen van de eigenschapsdefinitie van een aan de `Product` klasse.</span><span class="sxs-lookup"><span data-stu-id="84ae6-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="84ae6-120">Dit is een verwijzing naar een matrix of één entiteit.</span><span class="sxs-lookup"><span data-stu-id="84ae6-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="84ae6-121">Ervan uitgaande dat elk product tot slechts één categorie behoort, zou als volgt de definitie zijn.</span><span class="sxs-lookup"><span data-stu-id="84ae6-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="84ae6-122">De eigenschappen die staan voor de twee kanten van de koppeling, navigatie-eigenschappen worden genoemd.</span><span class="sxs-lookup"><span data-stu-id="84ae6-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="84ae6-123">Stappen voor het koppelen van entiteiten in het resource-schemabestand</span><span class="sxs-lookup"><span data-stu-id="84ae6-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="84ae6-124">De koppeling definiëren als een klasse met behulp van de `Association` trefwoord.</span><span class="sxs-lookup"><span data-stu-id="84ae6-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="84ae6-125">Het einde van de koppeling definiëren met behulp van het sleutelwoord AssociationClass om eigenschappen van de gekoppelde entiteiten te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="84ae6-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="84ae6-126">Het maken van de koppeling in het XML-bestand van de resource-toewijzing</span><span class="sxs-lookup"><span data-stu-id="84ae6-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="84ae6-127">Er zijn drie verschillende gevallen om te overwegen bij het toewijzen van een koppeling in het XML-bestand van de resource-toewijzing.</span><span class="sxs-lookup"><span data-stu-id="84ae6-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="84ae6-128">Bepaalt hoe u entiteiten in het toewijzingsbestand van de resource koppelen</span><span class="sxs-lookup"><span data-stu-id="84ae6-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="84ae6-129">Als de navigatie-eigenschap in de onderliggende aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="84ae6-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="84ae6-130">.NET framework-type, en dat bevat de eigenschap refererende sleutels, er is geen expliciete toewijzing nodig is.</span><span class="sxs-lookup"><span data-stu-id="84ae6-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="84ae6-131">Als de navigatie-eigenschap niet in het onderliggende type van de .NET Framework bestaat, moet u een cmdlet die worden opgehaald van de lijst met sleutels van de bijbehorende exemplaren opgeven.</span><span class="sxs-lookup"><span data-stu-id="84ae6-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="84ae6-132">U dit doen door het toevoegen van een `Association` element genest onder het `CmdletImplementation` -element, na de elementen die definieert de `cmdlets` voor de andere CRUD-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="84ae6-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="84ae6-133">Als de navigatie-eigenschap in het onderliggende type van de .NET Framework bestaat, maar deze instanties van objecten in plaats van refererende sleutels bevat, dan u een cmdlet maken moet (door een Windows PowerShell-functie of een script schrijven) de refererende sleutels wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="84ae6-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="84ae6-134">Vervolgens geeft u deze cmdlet in het toewijzingsbestand van de resource.</span><span class="sxs-lookup"><span data-stu-id="84ae6-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="84ae6-135">Bijvoorbeeld, het script voor het ophalen van de sleutels zou de volgende notatie.</span><span class="sxs-lookup"><span data-stu-id="84ae6-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="84ae6-136">En het XML-bestand in het bronbestand van de toewijzing eruitziet als volgt uit.</span><span class="sxs-lookup"><span data-stu-id="84ae6-136">And the XML in the resource mapping file would look like the following.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory.ps1</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="84ae6-137">Naast het opgeven van een cmdlet om op te halen van de gekoppelde entiteiten, kunt u ook de cmdlets voor het toevoegen en verwijderen van referenties uit de verzameling opgeven.</span><span class="sxs-lookup"><span data-stu-id="84ae6-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="84ae6-138">Het volgende voorbeeld wordt ervan uitgegaan dat de cmdlets Add-ProductToCategory en Remove-ProductFromCategory bestaan (ze kunnen ook worden gedefinieerd in een script of functie, zoals in het vorige voorbeeld).</span><span class="sxs-lookup"><span data-stu-id="84ae6-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

  ```xml
  Class Name="Sample.Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
  ...
              </GetReference>
        <AddReference>
     <CmdletName>"Add-ProductToCategory"</>
     <ParameterForThisObject>"Product"</>
     <ParameterForReferredObject>"Category"</>
        </AddReference>
        <RemoveReference>
     <CmdletName="Remove-ProductFromCategory"/>
     <ParameterForThisObject >"Product"</>
     <ParameterForReferredObject >"Category"</>
        </RemoveReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

## <a name="querying-associated-entities"></a><span data-ttu-id="84ae6-139">Gekoppelde entiteiten opvragen</span><span class="sxs-lookup"><span data-stu-id="84ae6-139">Querying associated entities</span></span>

<span data-ttu-id="84ae6-140">De client kan een lijst van de exemplaren die zijn gekoppeld aan een entiteit met het maken van specifieke query's ophalen.</span><span class="sxs-lookup"><span data-stu-id="84ae6-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="84ae6-141">Query's voor de gekoppelde entiteiten maken</span><span class="sxs-lookup"><span data-stu-id="84ae6-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="84ae6-142">Een client kan de details van een categorie aanvraagt zonder op te halen van de bijbehorende producten.</span><span class="sxs-lookup"><span data-stu-id="84ae6-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="84ae6-143">Bijvoorbeeld, de volgende aanvraag krijgt u informatie van de `food` categorie.</span><span class="sxs-lookup"><span data-stu-id="84ae6-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="84ae6-144">Om op te halen van de bijbehorende producten van de categorie (maar niet de details van de categorie zelf, de client geeft de navigatie-eigenschap in de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="84ae6-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="84ae6-145">Als u wilt ophalen van URL's van de producten, gebruikt u de `$links` kwalificatie in de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="84ae6-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="84ae6-146">De client kan zowel de Categoriedetails van de en de bijbehorende producten ophalen met behulp van de `$expand` kwalificatie.</span><span class="sxs-lookup"><span data-stu-id="84ae6-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="84ae6-147">Zie ook</span><span class="sxs-lookup"><span data-stu-id="84ae6-147">See Also</span></span>

[<span data-ttu-id="84ae6-148">Het maken van een webservice Management OData IIS-extensie</span><span class="sxs-lookup"><span data-stu-id="84ae6-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)