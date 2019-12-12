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
# <a name="associating-management-odata-entities"></a>Management OData-entiteiten koppelen

Het is vaak handig om een koppeling tussen twee verschillende beheer-OData-entiteiten te maken. Een OData-beheer service kan bijvoorbeeld entiteiten hebben die een catalogus van producten beheren die zijn ingedeeld in categorieën en de entiteiten `Product` en `Category`definiëren. Door deze twee entiteiten te koppelen, kan een client informatie ophalen over alle producten in een categorie met één aanvraag voor de webservice.

Een voor beeld dat laat zien hoe u koppelingen tussen entiteiten kunt maken, kan worden gedownload bij [koppelings voorbeeld](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).

## <a name="creating-the-association-in-the-resource-schema-file"></a>De koppeling in het resource schema bestand maken

Met de volgende MOF worden twee entiteiten gedefinieerd. Er wordt een koppeling tussen deze items gemaakt.

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

De klasse `Category` definieert een eigenschap die een matrix is van de namen van de producten die bij die categorie horen.

Als u twee entiteiten wilt koppelen, moet u een klasse met het kenmerk `Association` definiëren in het MOF-bestand van het resource schema voor de service. De klasse moet de twee entiteiten definiëren die moeten worden gekoppeld, de zogenaamde `ends` van de koppeling. In het volgende voor beeld ziet u een definitie van een klasse die een koppeling tussen de entiteiten categorie en Products definieert.

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

U moet ook de declaratie van de eigenschap Products in de klasse categorie wijzigen. U gebruikt het sleutel woord `AssociationClass` om op te geven dat de eigenschap zich op één uiteinde van de koppeling bevindt. De eigenschap moet ook worden gedefinieerd als een verwijzing naar een afzonderlijke entiteit, in plaats van een matrix met teken reeksen. U kunt dit doen met behulp van het sleutel woord `ref`. In het volgende voor beeld ziet u de eigenschaps definitie voor de koppeling.

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

Ten slotte moet u het andere einde van de koppeling declareren door een eigenschaps definitie toe te voegen aan de klasse `Product`. Dit is een verwijzing naar een matrix of één entiteit. Ervan uitgaande dat elk product tot slechts één categorie behoort, is de definitie als volgt.

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

De eigenschappen die de twee uiteinden van de koppeling vertegenwoordigen, worden navigatie-eigenschappen genoemd.

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>Stappen voor het koppelen van entiteiten in het resource schema bestand

- Definieer de koppeling als een klasse met behulp van het sleutel woord `Association`.

- Definieer de uiteinden van de koppeling met behulp van het sleutel woord AssociationClass om de eigenschappen van de gekoppelde entiteiten te kwalificeren.

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>De koppeling in het XML-bestand van de resource toewijzing maken

Er zijn drie verschillende gevallen waarin u rekening moet houden wanneer u een koppeling in het XML-bestand van de resource toewijzing toewijst.

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>Bepalen hoe entiteiten in het bron toewijzings bestand moeten worden gekoppeld

- Als de navigatie-eigenschap aanwezig is in de onderliggende. .NET Framework type en die eigenschap refererende sleutels bevat, hoeft geen expliciete toewijzing te worden toegewezen.

- Als de navigatie-eigenschap niet bestaat in het onderliggende .NET Framework type, moet u een cmdlet opgeven waarmee de lijst met sleutels van de gekoppelde exemplaren wordt opgehaald. U doet dit door een `Association` element toe te voegen dat is genest onder het element `CmdletImplementation`, door de elementen te volgen waarmee de `cmdlets` voor de andere ruwe opdrachten worden gedefinieerd.

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

- Als de navigatie-eigenschap bestaat in het onderliggende .NET Framework type, maar deze object instanties bevat in plaats van refererende sleutels, moet u een cmdlet maken (door een Windows Power shell-functie of-script te schrijven) om de refererende sleutels op te halen. Vervolgens geeft u die cmdlet op in het bron toewijzings bestand. Het script voor het ophalen van de sleutels ziet er bijvoorbeeld als volgt uit.

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  En de XML in het bron toewijzings bestand zou er als volgt uitzien.

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

- Naast het opgeven van een cmdlet om de gekoppelde entiteiten op te halen, kunt u ook cmdlets opgeven om verwijzingen toe te voegen aan of te verwijderen uit de verzameling. In het volgende voor beeld wordt ervan uitgegaan dat de cmdlets Add-ProductToCategory en Remove-ProductFromCategory bestaan (ze kunnen ook worden gedefinieerd in een script of functie, zoals in het vorige voor beeld).

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

## <a name="querying-associated-entities"></a>Query's uitvoeren op gekoppelde entiteiten

De client kan een lijst met de exemplaren die aan een entiteit zijn gekoppeld, ophalen door specifieke query's te maken.

#### <a name="constructing-queries-for-associated-entities"></a>Query's maken voor gekoppelde entiteiten

- Een client kan de details van een categorie opvragen zonder de bijbehorende producten op te halen. Met de volgende aanvraag worden bijvoorbeeld details van de categorie `food` opgehaald.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  Als u de gekoppelde producten van de categorie wilt ophalen (maar niet de details van de categorie zelf, specificeert de client de navigatie-eigenschap in de aanvraag.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- Als u alleen Url's van de producten wilt ophalen, gebruikt u de `$links` kwalificatie in de aanvraag.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- De client kan de categorie gegevens en de bijbehorende producten ophalen met behulp van de `$expand` kwalificatie.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>Zie ook

[Een management OData IIS extension-webservice maken](./creating-a-management-odata-web-service.md)