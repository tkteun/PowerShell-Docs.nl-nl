---
title: Beheer OData-entiteiten koppelen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352281"
---
# <a name="associating-management-odata-entities"></a><span data-ttu-id="46ab6-102">Management OData-entiteiten koppelen</span><span class="sxs-lookup"><span data-stu-id="46ab6-102">Associating Management OData Entities</span></span>

<span data-ttu-id="46ab6-103">Het is vaak handig om een koppeling tussen twee verschillende beheer-OData-entiteiten te maken.</span><span class="sxs-lookup"><span data-stu-id="46ab6-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="46ab6-104">Een OData-beheer service kan bijvoorbeeld entiteiten hebben die een catalogus van producten beheren die zijn ingedeeld in categorieën en de entiteiten `Product` en `Category`definiëren.</span><span class="sxs-lookup"><span data-stu-id="46ab6-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="46ab6-105">Door deze twee entiteiten te koppelen, kan een client informatie ophalen over alle producten in een categorie met één aanvraag voor de webservice.</span><span class="sxs-lookup"><span data-stu-id="46ab6-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="46ab6-106">Een voor beeld dat laat zien hoe u koppelingen tussen entiteiten kunt maken, kan worden gedownload bij [koppelings voorbeeld](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span><span class="sxs-lookup"><span data-stu-id="46ab6-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="46ab6-107">De koppeling in het resource schema bestand maken</span><span class="sxs-lookup"><span data-stu-id="46ab6-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="46ab6-108">Met de volgende MOF worden twee entiteiten gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="46ab6-108">The following MOF defines two entities.</span></span> <span data-ttu-id="46ab6-109">Er wordt een koppeling tussen deze items gemaakt.</span><span class="sxs-lookup"><span data-stu-id="46ab6-109">We will create an association between them.</span></span>

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

<span data-ttu-id="46ab6-110">De klasse `Category` definieert een eigenschap die een matrix is van de namen van de producten die bij die categorie horen.</span><span class="sxs-lookup"><span data-stu-id="46ab6-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="46ab6-111">Als u twee entiteiten wilt koppelen, moet u een klasse met het kenmerk `Association` definiëren in het MOF-bestand van het resource schema voor de service.</span><span class="sxs-lookup"><span data-stu-id="46ab6-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="46ab6-112">De klasse moet de twee entiteiten definiëren die moeten worden gekoppeld, de zogenaamde `ends` van de koppeling.</span><span class="sxs-lookup"><span data-stu-id="46ab6-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="46ab6-113">In het volgende voor beeld ziet u een definitie van een klasse die een koppeling tussen de entiteiten categorie en Products definieert.</span><span class="sxs-lookup"><span data-stu-id="46ab6-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="46ab6-114">U moet ook de declaratie van de eigenschap Products in de klasse categorie wijzigen.</span><span class="sxs-lookup"><span data-stu-id="46ab6-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="46ab6-115">U gebruikt het sleutel woord `AssociationClass` om op te geven dat de eigenschap zich op één uiteinde van de koppeling bevindt.</span><span class="sxs-lookup"><span data-stu-id="46ab6-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="46ab6-116">De eigenschap moet ook worden gedefinieerd als een verwijzing naar een afzonderlijke entiteit, in plaats van een matrix met teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="46ab6-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="46ab6-117">U kunt dit doen met behulp van het sleutel woord `ref`.</span><span class="sxs-lookup"><span data-stu-id="46ab6-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="46ab6-118">In het volgende voor beeld ziet u de eigenschaps definitie voor de koppeling.</span><span class="sxs-lookup"><span data-stu-id="46ab6-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="46ab6-119">Ten slotte moet u het andere einde van de koppeling declareren door een eigenschaps definitie toe te voegen aan de klasse `Product`.</span><span class="sxs-lookup"><span data-stu-id="46ab6-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="46ab6-120">Dit is een verwijzing naar een matrix of één entiteit.</span><span class="sxs-lookup"><span data-stu-id="46ab6-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="46ab6-121">Ervan uitgaande dat elk product tot slechts één categorie behoort, is de definitie als volgt.</span><span class="sxs-lookup"><span data-stu-id="46ab6-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="46ab6-122">De eigenschappen die de twee uiteinden van de koppeling vertegenwoordigen, worden navigatie-eigenschappen genoemd.</span><span class="sxs-lookup"><span data-stu-id="46ab6-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="46ab6-123">Stappen voor het koppelen van entiteiten in het resource schema bestand</span><span class="sxs-lookup"><span data-stu-id="46ab6-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="46ab6-124">Definieer de koppeling als een klasse met behulp van het sleutel woord `Association`.</span><span class="sxs-lookup"><span data-stu-id="46ab6-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="46ab6-125">Definieer de uiteinden van de koppeling met behulp van het sleutel woord AssociationClass om de eigenschappen van de gekoppelde entiteiten te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="46ab6-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="46ab6-126">De koppeling in het XML-bestand van de resource toewijzing maken</span><span class="sxs-lookup"><span data-stu-id="46ab6-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="46ab6-127">Er zijn drie verschillende gevallen waarin u rekening moet houden wanneer u een koppeling in het XML-bestand van de resource toewijzing toewijst.</span><span class="sxs-lookup"><span data-stu-id="46ab6-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="46ab6-128">Bepalen hoe entiteiten in het bron toewijzings bestand moeten worden gekoppeld</span><span class="sxs-lookup"><span data-stu-id="46ab6-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="46ab6-129">Als de navigatie-eigenschap aanwezig is in de onderliggende.</span><span class="sxs-lookup"><span data-stu-id="46ab6-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="46ab6-130">.NET Framework type en die eigenschap refererende sleutels bevat, hoeft geen expliciete toewijzing te worden toegewezen.</span><span class="sxs-lookup"><span data-stu-id="46ab6-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="46ab6-131">Als de navigatie-eigenschap niet bestaat in het onderliggende .NET Framework type, moet u een cmdlet opgeven waarmee de lijst met sleutels van de gekoppelde exemplaren wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="46ab6-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="46ab6-132">U doet dit door een `Association` element toe te voegen dat is genest onder het element `CmdletImplementation`, door de elementen te volgen waarmee de `cmdlets` voor de andere ruwe opdrachten worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="46ab6-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

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

- <span data-ttu-id="46ab6-133">Als de navigatie-eigenschap bestaat in het onderliggende .NET Framework type, maar deze object instanties bevat in plaats van refererende sleutels, moet u een cmdlet maken (door een Windows Power shell-functie of-script te schrijven) om de refererende sleutels op te halen.</span><span class="sxs-lookup"><span data-stu-id="46ab6-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="46ab6-134">Vervolgens geeft u die cmdlet op in het bron toewijzings bestand.</span><span class="sxs-lookup"><span data-stu-id="46ab6-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="46ab6-135">Het script voor het ophalen van de sleutels ziet er bijvoorbeeld als volgt uit.</span><span class="sxs-lookup"><span data-stu-id="46ab6-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="46ab6-136">En de XML in het bron toewijzings bestand zou er als volgt uitzien.</span><span class="sxs-lookup"><span data-stu-id="46ab6-136">And the XML in the resource mapping file would look like the following.</span></span>

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

- <span data-ttu-id="46ab6-137">Naast het opgeven van een cmdlet om de gekoppelde entiteiten op te halen, kunt u ook cmdlets opgeven om verwijzingen toe te voegen aan of te verwijderen uit de verzameling.</span><span class="sxs-lookup"><span data-stu-id="46ab6-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="46ab6-138">In het volgende voor beeld wordt ervan uitgegaan dat de cmdlets Add-ProductToCategory en Remove-ProductFromCategory bestaan (ze kunnen ook worden gedefinieerd in een script of functie, zoals in het vorige voor beeld).</span><span class="sxs-lookup"><span data-stu-id="46ab6-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

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

## <a name="querying-associated-entities"></a><span data-ttu-id="46ab6-139">Query's uitvoeren op gekoppelde entiteiten</span><span class="sxs-lookup"><span data-stu-id="46ab6-139">Querying associated entities</span></span>

<span data-ttu-id="46ab6-140">De client kan een lijst met de exemplaren die aan een entiteit zijn gekoppeld, ophalen door specifieke query's te maken.</span><span class="sxs-lookup"><span data-stu-id="46ab6-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="46ab6-141">Query's maken voor gekoppelde entiteiten</span><span class="sxs-lookup"><span data-stu-id="46ab6-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="46ab6-142">Een client kan de details van een categorie opvragen zonder de bijbehorende producten op te halen.</span><span class="sxs-lookup"><span data-stu-id="46ab6-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="46ab6-143">Met de volgende aanvraag worden bijvoorbeeld details van de categorie `food` opgehaald.</span><span class="sxs-lookup"><span data-stu-id="46ab6-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="46ab6-144">Als u de gekoppelde producten van de categorie wilt ophalen (maar niet de details van de categorie zelf, specificeert de client de navigatie-eigenschap in de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="46ab6-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="46ab6-145">Als u alleen Url's van de producten wilt ophalen, gebruikt u de `$links` kwalificatie in de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="46ab6-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="46ab6-146">De client kan de categorie gegevens en de bijbehorende producten ophalen met behulp van de `$expand` kwalificatie.</span><span class="sxs-lookup"><span data-stu-id="46ab6-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="46ab6-147">Zie ook</span><span class="sxs-lookup"><span data-stu-id="46ab6-147">See Also</span></span>

[<span data-ttu-id="46ab6-148">Een management OData IIS extension-webservice maken</span><span class="sxs-lookup"><span data-stu-id="46ab6-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)