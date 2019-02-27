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
# <a name="associating-management-odata-entities"></a>Management OData-entiteiten koppelen

Het is vaak handig voor het maken van een koppeling tussen twee verschillende Management OData-entiteiten. Bijvoorbeeld, een OData-Management-service kan beschikt over entiteiten die een lijst van producten die zijn ingedeeld in categorieën beheren en de entiteiten definiëren `Product` en `Category`. Een client krijgen door deze twee entiteiten koppelen, informatie over alle producten in een categorie aan een enkele aanvraag met de webservice.

Een voorbeeld over het maken van koppelingen tussen entiteiten kan worden gedownload op [koppeling voorbeeld](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).

## <a name="creating-the-association-in-the-resource-schema-file"></a>Het maken van de koppeling in het schemabestand resource

De volgende MOF definieert twee entiteiten. We gaan een koppeling tussen deze maken.

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

De `Category` klasse definieert een eigenschap die een matrix van de namen van de producten die deel uitmaken van deze categorie.

Als u wilt koppelen twee entiteiten, definieert u een klasse met de `Association` kenmerk in het resource-schema MOF-bestand voor de service. De twee entiteiten die zijn gekoppeld, met de naam moet definiëren van de klasse `ends` van de koppeling. Het volgende voorbeeld bevat een definitie van een klasse die een koppeling tussen de categorie en producten entiteiten definieert.

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

U moet ook de declaratie van de eigenschap producten in de categorie-klasse wijzigen. U gebruikt de `AssociationClass` trefwoord om op te geven dat de eigenschap ene uiteinde van de koppeling is. De eigenschap moet ook worden gedefinieerd als een verwijzing naar een aparte entiteit in plaats van een matrix met tekenreeksen. U dit doen met behulp van de `ref` trefwoord. Het volgende voorbeeld ziet de definitie van de eigenschap voor de koppeling.

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

Ten slotte het andere uiteinde van de koppeling moet worden gedeclareerd door toe te voegen van de eigenschapsdefinitie van een aan de `Product` klasse. Dit is een verwijzing naar een matrix of één entiteit. Ervan uitgaande dat elk product tot slechts één categorie behoort, zou als volgt de definitie zijn.

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

De eigenschappen die staan voor de twee kanten van de koppeling, navigatie-eigenschappen worden genoemd.

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>Stappen voor het koppelen van entiteiten in het resource-schemabestand

- De koppeling definiëren als een klasse met behulp van de `Association` trefwoord.

- Het einde van de koppeling definiëren met behulp van het sleutelwoord AssociationClass om eigenschappen van de gekoppelde entiteiten te kwalificeren.

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>Het maken van de koppeling in het XML-bestand van de resource-toewijzing

Er zijn drie verschillende gevallen om te overwegen bij het toewijzen van een koppeling in het XML-bestand van de resource-toewijzing.

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>Bepaalt hoe u entiteiten in het toewijzingsbestand van de resource koppelen

- Als de navigatie-eigenschap in de onderliggende aanwezig is. .NET framework-type, en dat bevat de eigenschap refererende sleutels, er is geen expliciete toewijzing nodig is.

- Als de navigatie-eigenschap niet in het onderliggende type van de .NET Framework bestaat, moet u een cmdlet die worden opgehaald van de lijst met sleutels van de bijbehorende exemplaren opgeven. U dit doen door het toevoegen van een `Association` element genest onder het `CmdletImplementation` -element, na de elementen die definieert de `cmdlets` voor de andere CRUD-opdrachten.

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

- Als de navigatie-eigenschap in het onderliggende type van de .NET Framework bestaat, maar deze instanties van objecten in plaats van refererende sleutels bevat, dan u een cmdlet maken moet (door een Windows PowerShell-functie of een script schrijven) de refererende sleutels wilt ophalen. Vervolgens geeft u deze cmdlet in het toewijzingsbestand van de resource. Bijvoorbeeld, het script voor het ophalen van de sleutels zou de volgende notatie.

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  En het XML-bestand in het bronbestand van de toewijzing eruitziet als volgt uit.

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

- Naast het opgeven van een cmdlet om op te halen van de gekoppelde entiteiten, kunt u ook de cmdlets voor het toevoegen en verwijderen van referenties uit de verzameling opgeven. Het volgende voorbeeld wordt ervan uitgegaan dat de cmdlets Add-ProductToCategory en Remove-ProductFromCategory bestaan (ze kunnen ook worden gedefinieerd in een script of functie, zoals in het vorige voorbeeld).

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

## <a name="querying-associated-entities"></a>Gekoppelde entiteiten opvragen

De client kan een lijst van de exemplaren die zijn gekoppeld aan een entiteit met het maken van specifieke query's ophalen.

#### <a name="constructing-queries-for-associated-entities"></a>Query's voor de gekoppelde entiteiten maken

- Een client kan de details van een categorie aanvraagt zonder op te halen van de bijbehorende producten. Bijvoorbeeld, de volgende aanvraag krijgt u informatie van de `food` categorie.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  Om op te halen van de bijbehorende producten van de categorie (maar niet de details van de categorie zelf, de client geeft de navigatie-eigenschap in de aanvraag.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- Als u wilt ophalen van URL's van de producten, gebruikt u de `$links` kwalificatie in de aanvraag.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- De client kan zowel de Categoriedetails van de en de bijbehorende producten ophalen met behulp van de `$expand` kwalificatie.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>Zie ook

[Het maken van een webservice Management OData IIS-extensie](./creating-a-management-odata-web-service.md)