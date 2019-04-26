---
title: Aangepaste opmaak bestanden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068297"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="4a4fd-102">Aangepaste opmaakbestanden</span><span class="sxs-lookup"><span data-stu-id="4a4fd-102">Custom Formatting Files</span></span>

<span data-ttu-id="4a4fd-103">De notatie voor de objecten die zijn geretourneerd door cmdlets, functies en scripts worden gedefinieerd met behulp van opmaak-bestanden (format.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="4a4fd-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="4a4fd-104">Aantal van deze bestanden worden geleverd door Windows PowerShell voor het definiëren van de standaardindeling voor de weergave voor die objecten geretourneerd door de Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="4a4fd-105">U kunt echter ook uw eigen aangepaste opmaak bestanden te overschrijven van de standaard-notatie of voor het definiëren van de weergave van objecten die worden geretourneerd door uw eigen opdrachten maken.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="4a4fd-106">Windows PowerShell gebruikt de gegevens in deze opmaak bestanden om te bepalen wat wordt weergegeven en hoe de gegevens zijn opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="4a4fd-107">De weergegeven gegevens kunnen de eigenschappen van een object of de waarde van een scriptblok bevatten.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="4a4fd-108">Scriptblokken worden gebruikt als u wilt weergeven van een waarde die rechtstreeks in de eigenschappen van een object is niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="4a4fd-109">U wilt bijvoorbeeld de waarde van de twee eigenschappen van een object toevoegen en de som weergegeven als een afzonderlijke hoeveelheid gegevens.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="4a4fd-110">Wanneer u uw eigen opmaak-bestand schrijven, moet u voor het definiëren van *weergaven* voor de objecten die u wilt weergeven.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="4a4fd-111">U kunt voor elk object één weergave definiëren, kunt u één weergave voor meerdere objecten of kunt u meerdere weergaven voor hetzelfde object.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="4a4fd-112">Er is geen limiet voor het aantal weergaven die u kunt definiëren.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a4fd-113">Opmaak bestanden bepalen de elementen van een object die worden geretourneerd aan de pijplijn niet.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="4a4fd-114">Wanneer een object wordt geretourneerd aan de pijplijn, vindt u alle leden van dat object.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="4a4fd-115">Indeling weergaven</span><span class="sxs-lookup"><span data-stu-id="4a4fd-115">Format Views</span></span>

<span data-ttu-id="4a4fd-116">Opmaak weergaven kunnen objecten weergeven in de vorm van een tabel, een indeling heeft, een breed indeling en een aangepaste notatie.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="4a4fd-117">Voor het overgrote deel wordt elke opmaak definitie beschreven door een set XML-labels die worden beschreven van een weergave.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="4a4fd-118">Elke weergave bevat de naam van de weergave de objecten die gebruikmaken van de weergave en de elementen van de weergave, zoals de kolommen en rijen gegevens voor een tabelweergave.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="4a4fd-119">De volgende weergaven zijn beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-119">The following views are available.</span></span>

<span data-ttu-id="4a4fd-120">Tabelweergave worden de eigenschappen van een object of een waarde voor het blokkeren van script in een of meer kolommen.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="4a4fd-121">Elke kolom vertegenwoordigt een eigenschap van het object of de waarde van een script blokkeren.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="4a4fd-122">Weergeven als een tabel waarin alle eigenschappen van een object, een subset van de eigenschappen van een object of een combinatie van eigenschappen en script blok waarden worden weergegeven, kunt u definiëren.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="4a4fd-123">Elke rij van de tabel vertegenwoordigt een geretourneerde object.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="4a4fd-124">Zie voor meer informatie over deze weergave [tabelweergave](../format/creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="4a4fd-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="4a4fd-125">Lijstweergave geeft een lijst van de eigenschappen van een object of een waarde voor het blokkeren van script in één kolom.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="4a4fd-126">Elke rij van de lijst geeft een optioneel label of de naam van de eigenschap gevolgd door de waarde van het blok eigenschap of het script.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="4a4fd-127">Zie voor meer informatie over deze weergave [lijstweergave](../format/creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="4a4fd-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="4a4fd-128">Brede weergave bevat één eigenschap van een object of een waarde voor het blokkeren van script in een of meer kolommen.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="4a4fd-129">Er is geen label of de header voor deze weergave.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-129">There is no label or header for this view.</span></span> <span data-ttu-id="4a4fd-130">Zie voor meer informatie over deze weergave [brede weergave](../format/creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="4a4fd-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="4a4fd-131">Aangepaste weergave bevat een aanpasbare weergave van eigenschappen van het object of script blok waarden die niet in overeenstemming is met de Star structuur van de tabelweergaven, lijstweergaven of breed weergaven.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="4a4fd-132">Kunt u een aangepaste weergave van zelfstandige of kunt u een aangepaste weergave die wordt gebruikt door een andere weergave, zoals een tabel of lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="4a4fd-133">Zie voor meer informatie over deze weergave [aangepaste weergave](../format/creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="4a4fd-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="4a4fd-134">XML-elementen weergeven</span><span class="sxs-lookup"><span data-stu-id="4a4fd-134">View XML Elements</span></span>

<span data-ttu-id="4a4fd-135">Het volgende voorbeeld ziet de XML-labels die worden gebruikt voor het definiëren van weergeven als een tabel met twee kolommen.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="4a4fd-136">De [ViewDefinitions](../format/viewdefinitions-element-format.md) element is de containerelement voor de weergaven die zijn gedefinieerd in het bestand met opmaak.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="4a4fd-137">De [weergave](../format/view-element-format.md) element wordt gedefinieerd voor de specifieke tabel, lijst, breed of een aangepaste weergave.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="4a4fd-138">Binnen elke weergave de [naam](../format/name-element-for-view-format.md) element Hiermee geeft u de naam van de weergave de [ViewSelectedBy](../format/viewselectedby-element-format.md) element definieert de objecten die gebruikmaken van de weergave en de verschillende beheer-elementen (zoals de `TableControl` element) de indeling van de weergave definiëren.</span><span class="sxs-lookup"><span data-stu-id="4a4fd-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4a4fd-139">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4a4fd-139">See Also</span></span>

[<span data-ttu-id="4a4fd-140">Tabelweergave</span><span class="sxs-lookup"><span data-stu-id="4a4fd-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="4a4fd-141">Lijstweergave</span><span class="sxs-lookup"><span data-stu-id="4a4fd-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="4a4fd-142">Brede weergave</span><span class="sxs-lookup"><span data-stu-id="4a4fd-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="4a4fd-143">Aangepaste weergave</span><span class="sxs-lookup"><span data-stu-id="4a4fd-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="4a4fd-144">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4a4fd-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
