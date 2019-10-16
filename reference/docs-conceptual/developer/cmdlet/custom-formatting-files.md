---
title: Aangepaste indelings bestanden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359416"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="75751-102">Aangepaste opmaakbestanden</span><span class="sxs-lookup"><span data-stu-id="75751-102">Custom Formatting Files</span></span>

<span data-ttu-id="75751-103">De weer gave-indeling voor objecten die worden geretourneerd door cmdlets, functies en scripts worden gedefinieerd met behulp van indelings bestanden (ps1xml-bestanden).</span><span class="sxs-lookup"><span data-stu-id="75751-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="75751-104">Een aantal van deze bestanden wordt geleverd door Windows Power shell om de standaard weergave-indeling te definiëren voor de objecten die worden geretourneerd door Windows Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="75751-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="75751-105">U kunt echter ook uw eigen aangepaste opmaak bestanden maken om de standaard weergave indelingen te overschrijven of om de weer gave van objecten te definiëren die door uw eigen opdrachten worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="75751-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="75751-106">Windows Power shell gebruikt de gegevens in deze indelings bestanden om te bepalen wat wordt weer gegeven en hoe de gegevens worden opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="75751-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="75751-107">De weer gegeven gegevens kunnen de eigenschappen van een object of de waarde van een script blok bevatten.</span><span class="sxs-lookup"><span data-stu-id="75751-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="75751-108">Script blokken worden gebruikt als u een bepaalde waarde wilt weer geven die niet rechtstreeks vanuit de eigenschappen van een object beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="75751-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="75751-109">U kunt bijvoorbeeld de waarde van twee eigenschappen van een object toevoegen en de som als afzonderlijke gegevens weer geven.</span><span class="sxs-lookup"><span data-stu-id="75751-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="75751-110">Wanneer u uw eigen opmaak bestand schrijft, moet u *weer gaven* definiëren voor de objecten die u wilt weer geven.</span><span class="sxs-lookup"><span data-stu-id="75751-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="75751-111">U kunt één weer gave definiëren voor elk object, u kunt één weer gave voor meerdere objecten definiëren, maar u kunt ook meerdere weer gaven definiëren voor hetzelfde object.</span><span class="sxs-lookup"><span data-stu-id="75751-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="75751-112">Er is geen limiet voor het aantal weer gaven dat u kunt definiëren.</span><span class="sxs-lookup"><span data-stu-id="75751-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="75751-113">Indelings bestanden bepalen niet welke elementen van een object worden geretourneerd naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="75751-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="75751-114">Wanneer een object wordt geretourneerd naar de pijp lijn, zijn alle leden van dat object beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="75751-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="75751-115">Opmaak weergaven</span><span class="sxs-lookup"><span data-stu-id="75751-115">Format Views</span></span>

<span data-ttu-id="75751-116">In opmaak weergaven kunnen objecten worden weer gegeven in een tabel indeling, een lijst opmaak, een brede indeling en een aangepaste notatie.</span><span class="sxs-lookup"><span data-stu-id="75751-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="75751-117">Voor de meeste delen wordt elke opmaak definitie beschreven met een set XML-tags die een weer gave beschrijven.</span><span class="sxs-lookup"><span data-stu-id="75751-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="75751-118">Elke weer gave bevat de naam van de weer gave, de objecten die gebruikmaken van de weer gave en de elementen van de weer gave, zoals de kolom-en rij-informatie voor een tabel weergave.</span><span class="sxs-lookup"><span data-stu-id="75751-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="75751-119">De volgende weer gaven zijn beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="75751-119">The following views are available.</span></span>

<span data-ttu-id="75751-120">In de tabel weergave worden de eigenschappen van een object of een script blok waarde in een of meer kolommen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="75751-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="75751-121">Elke kolom vertegenwoordigt een eigenschap van het object of een script blok waarde.</span><span class="sxs-lookup"><span data-stu-id="75751-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="75751-122">U kunt een tabel weergave definiëren waarin alle eigenschappen van een object, een subset van de eigenschappen van een object of een combi natie van eigenschappen en script blok waarden worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="75751-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="75751-123">Elke rij van de tabel vertegenwoordigt een geretourneerd object.</span><span class="sxs-lookup"><span data-stu-id="75751-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="75751-124">Zie [tabel weergave](../format/creating-a-table-view.md)voor meer informatie over deze weer gave.</span><span class="sxs-lookup"><span data-stu-id="75751-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="75751-125">In de lijst weergave worden de eigenschappen van een object of een script blok waarde in één kolom weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="75751-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="75751-126">Elke rij van de lijst bevat een optioneel label of de naam van de eigenschap gevolgd door de waarde van de eigenschap of het script blok.</span><span class="sxs-lookup"><span data-stu-id="75751-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="75751-127">Zie [lijst weergave](../format/creating-a-list-view.md)voor meer informatie over deze weer gave.</span><span class="sxs-lookup"><span data-stu-id="75751-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="75751-128">Breedbeeld weergave bevat een enkele eigenschap van een object of een script blok waarde in een of meer kolommen.</span><span class="sxs-lookup"><span data-stu-id="75751-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="75751-129">Er is geen label of koptekst voor deze weer gave.</span><span class="sxs-lookup"><span data-stu-id="75751-129">There is no label or header for this view.</span></span> <span data-ttu-id="75751-130">Zie [brede weer](../format/creating-a-wide-view.md)gave voor meer informatie over deze weer gave.</span><span class="sxs-lookup"><span data-stu-id="75751-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="75751-131">In de aangepaste weer gave wordt een aanpas bare weer gave weer gegeven van object eigenschappen of script blok waarden die niet voldoen aan de stijve structuur van tabel weergaven, lijst weergaven of brede weer gaven.</span><span class="sxs-lookup"><span data-stu-id="75751-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="75751-132">U kunt een zelfstandige aangepaste weer gave definiëren, maar u kunt ook een aangepaste weer gave definiëren die wordt gebruikt door een andere weer gave, zoals een tabel weergave of lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="75751-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="75751-133">Zie [aangepaste weer gave](../format/creating-custom-controls.md)voor meer informatie over deze weer gave.</span><span class="sxs-lookup"><span data-stu-id="75751-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="75751-134">XML-elementen weer geven</span><span class="sxs-lookup"><span data-stu-id="75751-134">View XML Elements</span></span>

<span data-ttu-id="75751-135">In het volgende voor beeld ziet u de XML-labels die worden gebruikt voor het definiëren van een tabel weergave die twee kolommen bevat.</span><span class="sxs-lookup"><span data-stu-id="75751-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="75751-136">Het element [ViewDefinitions](../format/viewdefinitions-element-format.md) is het container element voor alle weer gaven die in het opmaak bestand zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="75751-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="75751-137">Het element [weer gave](../format/view-element-format.md) definieert de specifieke tabel, lijst, brede of aangepaste weer gave.</span><span class="sxs-lookup"><span data-stu-id="75751-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="75751-138">In elke weer gave geeft het element [name](../format/name-element-for-view-format.md) de naam van de weer gave, het [ViewSelectedBy](../format/viewselectedby-element-format.md) -element definieert de objecten die gebruikmaken van de weer gave en de verschillende elementen van het besturings element (zoals het element `TableControl`) definiëren de indeling van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="75751-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

```xml
ViewDefinitions
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="75751-139">Zie ook</span><span class="sxs-lookup"><span data-stu-id="75751-139">See Also</span></span>

[<span data-ttu-id="75751-140">Tabel weergave</span><span class="sxs-lookup"><span data-stu-id="75751-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="75751-141">Lijst weergave</span><span class="sxs-lookup"><span data-stu-id="75751-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="75751-142">Brede weer gave</span><span class="sxs-lookup"><span data-stu-id="75751-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="75751-143">Aangepaste weer gave</span><span class="sxs-lookup"><span data-stu-id="75751-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="75751-144">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="75751-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
