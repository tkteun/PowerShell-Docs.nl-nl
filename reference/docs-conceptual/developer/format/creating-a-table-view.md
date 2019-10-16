---
title: Een tabel weergave maken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354808"
---
# <a name="creating-a-table-view"></a>Een tabelweergave maken

In een tabel weergave worden gegevens in een of meer kolommen weer gegeven. Elke rij in de tabel vertegenwoordigt een .NET-object en elke kolom van de tabel vertegenwoordigt een eigenschap van het object of een script waarde. U kunt een tabel weergave definiëren waarin alle eigenschappen van een object of een subset van de eigenschappen van een object worden weer gegeven.

## <a name="a-table-view-display"></a>Een tabel weergave weer geven

In het volgende voor beeld ziet u hoe in Windows Power shell het object [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) wordt weer gegeven dat wordt geretourneerd door de cmdlet [Get-service](/powershell/module/microsoft.powershell.management/get-service) . Voor dit object heeft Windows Power shell een tabel weergave gedefinieerd waarin de eigenschap `Status` wordt weer gegeven, de eigenschap `Name` (deze eigenschap is een alias eigenschap voor de eigenschap `ServiceName`) en de eigenschap `DisplayName`. Elke rij in de tabel vertegenwoordigt een object dat door de cmdlet wordt geretourneerd.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>De tabel weergave definiëren

In het volgende XML-bestand wordt het tabel weergave schema weer gegeven voor het weer geven van [System. ServiceProcess. servicecontroller? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -object. U moet elke eigenschap opgeven die u wilt weer geven in de tabel weergave.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

De volgende XML-elementen worden gebruikt voor het definiëren van een lijst weergave:

- Het element [View](./view-element-format.md) is het bovenliggende element van de tabel weergave. (Dit is hetzelfde bovenliggende element voor de lijst weergave, brede en aangepaste besturings elementen.)

- Het element [name](./name-element-for-view-format.md) specificeert de naam van de weer gave. Dit element is vereist voor alle weer gaven.

- Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert de objecten die gebruikmaken van de weer gave. Dit element is vereist.

- Het element [GroupBy](./groupby-element-for-view-format.md) (niet weer gegeven in dit voor beeld) definieert wanneer een nieuwe groep objecten wordt weer gegeven. Er wordt een nieuwe groep gestart wanneer de waarde van een specifieke eigenschap of script wordt gewijzigd. Dit element is optioneel.

- Het element [Controls](./controls-element-for-view-format.md) (in dit voor beeld wordt niet weer gegeven) definieert de aangepaste besturings elementen die door de tabel weergave worden gedefinieerd. Met besturings elementen kunt u nader aangeven hoe de gegevens worden weer gegeven. Dit element is optioneel. Een weer gave kan zijn eigen aangepaste besturings elementen definiëren, maar u kunt ook algemene besturings elementen gebruiken die kunnen worden gebruikt door elke weer gave in het opmaak bestand. Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over aangepaste besturings elementen.

- Het [HideTableHeaders](./hidetableheaders-element-format.md) -element (niet weer gegeven in dit voor beeld) geeft aan dat er geen labels worden weer gegeven boven aan de tabel. Dit element is optioneel.

- Het [TableControl](./tablecontrol-element-format.md) -element waarmee de koptekst en de rij-informatie van de tabel worden gedefinieerd. Net als bij alle andere weer gaven kunnen in een tabel weergave de waarden van object eigenschappen of waarden worden weer gegeven die door scripts worden gegenereerd.

## <a name="defining-column-headers"></a>Kolom koppen definiëren

1. Het [TableHeaders](./tableheaders-element-format.md) -element en de onderliggende elementen bepalen wat er boven aan de tabel wordt weer gegeven.

2. Het element [TableColumnHeader](./tablecolumnheader-element-format.md) definieert wat wordt weer gegeven aan de bovenkant van een kolom van de tabel. Geef deze elementen op in de volg orde waarin de kopteksten moeten worden weer gegeven.

   Er is geen limiet voor het aantal van dit element dat u kunt gebruiken, maar het aantal [TableColumnHeader](./tablecolumnheader-element-format.md) -elementen in de tabel weergave moet gelijk zijn aan het aantal [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) -elementen dat u gebruikt.

3. Het element [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) geeft de tekst aan die wordt weer gegeven. Dit element is optioneel.

4. Met het element [width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) wordt de breedte (in tekens) van de kolom opgegeven. Dit element is optioneel.

5. Het element [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) geeft aan hoe het label wordt weer gegeven. Het label kan aan de linkerkant, rechts of gecentreerd worden uitgelijnd. Dit element is optioneel.

## <a name="defining-the-table-rows"></a>De tabel rijen definiëren

Tabel weergaven kunnen een of meer definities bieden die aangeven welke gegevens in de rijen van de tabel worden weer gegeven door de onderliggende elementen van het element [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) te gebruiken. U kunt meerdere definities opgeven voor de rijen van de tabel, maar de kopteksten van de rijen blijven hetzelfde, ongeacht de rijdefinitie die wordt gebruikt. Normaal gesp roken bevat een tabel slechts één definitie.

In het volgende voor beeld bevat de weer gave één definitie waarmee de waarden van verschillende eigenschappen van het [System. Diagnostics. process worden weer gegeven? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) -object. Een tabel weergave kan de waarde van een eigenschap of de waarde van een script (niet weer gegeven in het voor beeld) weer geven in de rijen.

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

De volgende XML-elementen kunnen worden gebruikt om definities voor een rij op te geven:

- Het element [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) en de onderliggende elementen bepalen wat wordt weer gegeven in de rijen van de tabel.

- Het [TableRowEntry](./listentry-element-for-listcontrol-format.md) -element bevat een definitie van de rij. Er is ten minste één [TableRowEntry](./listentry-element-for-listcontrol-format.md) vereist. Er is echter geen maximum limiet voor het aantal elementen dat u kunt toevoegen. In de meeste gevallen heeft een weer gave slechts één definitie.

- Het [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -element geeft de objecten aan die door een specifieke definitie worden weer gegeven. Dit element is optioneel en is alleen nodig wanneer u meerdere [TableRowEntry](./listentry-element-for-listcontrol-format.md) -elementen definieert waarin verschillende objecten worden weer gegeven.

- Met het [Terugloop](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element wordt aangegeven dat de tekst die de kolom breedte overschrijdt wordt weer gegeven op de volgende regel. Standaard wordt tekst die de kolom breedte overschrijdt, afgekapt.

- Het [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) -element definieert de eigenschappen of scripts waarvan de waarden in de rij worden weer gegeven.

- Het [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element definieert de eigenschap of het script waarvan de waarde wordt weer gegeven in de kolom van de rij. Voor elke kolom van de rij is een [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element vereist. De eerste vermelding wordt weer gegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.

- Met het element [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) wordt de eigenschap opgegeven waarvan de waarde wordt weer gegeven in de rij. U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.

- Het [script Block](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) -element geeft het script op waarvan de waarde wordt weer gegeven in de rij. U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.

- Het element [formats Tring](./label-element-for-listitem-for-listcontrol-format.md) geeft een opmaak patroon op dat bepaalt hoe de eigenschap of script waarde wordt weer gegeven. Dit element is optioneel.

- Het element [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) geeft aan hoe de waarde van de eigenschap of het script wordt weer gegeven. De waarde kan aan de linkerkant, rechts of gecentreerd worden uitgelijnd. Dit element is optioneel.

## <a name="defining-the-objects-that-use-the-table-view"></a>De objecten definiëren die gebruikmaken van de tabel weergave

Er zijn twee manieren om te definiëren welke .NET-objecten gebruikmaken van de tabel weergave. U kunt het element [ViewSelectedBy](./viewselectedby-element-format.md) gebruiken om de objecten te definiëren die door alle definities van de weer gave kunnen worden weer gegeven, of u kunt het element [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) gebruiken om te definiëren welke objecten worden weer gegeven met een specifieke definitie van de weer gave. In de meeste gevallen heeft een weer gave slechts één definitie, waardoor objecten doorgaans worden gedefinieerd door het element [ViewSelectedBy](./viewselectedby-element-format.md) .

In het volgende voor beeld ziet u hoe u de objecten definieert die worden weer gegeven in de tabel weergave met behulp van de elementen [ViewSelectedBy](./viewselectedby-element-format.md) en [TypeName](./typename-element-for-viewselectedby-format.md) . Er is geen limiet voor het aantal [TypeName](./typename-element-for-viewselectedby-format.md) -elementen dat u kunt opgeven en de volg orde hiervan is niet belang rijk.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door de tabel weergave:

- Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert welke objecten worden weer gegeven in de lijst weergave.

- Het element [TypeName](./typename-element-for-viewselectedby-format.md) specificeert het .net-object dat wordt weer gegeven in de weer gave. De volledig gekwalificeerde .NET-type naam is vereist. U moet ten minste één type of selectieset voor de weer gave opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.

In het volgende voor beeld worden de elementen [ViewSelectedBy](./viewselectedby-element-format.md) en [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) gebruikt. Gebruik selectie sets waar u een gerelateerde set objecten hebt die worden weer gegeven met behulp van meerdere weer gaven, zoals wanneer u een lijst weergave definieert en een tabel weergave voor dezelfde objecten. Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het maken van een selectie reeks.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door de lijst weergave:

- Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert welke objecten worden weer gegeven in de lijst weergave.

- Het [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -element geeft een set objecten op die door de weer gave kan worden weer gegeven. U moet ten minste één selectieset of type voor de weer gave opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.

In het volgende voor beeld ziet u hoe u de objecten definieert die worden weer gegeven met een specifieke definitie van de tabel weergave met behulp van het element [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) . Met dit element kunt u de .NET-type naam van het object, een selectieset van objecten of een selectie voorwaarde opgeven die opgeeft wanneer de definitie wordt gebruikt. Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het maken van een selectie voorwaarden.

> [!NOTE]
> Bij het maken van meerdere definities van de tabel weergave kunt u geen andere kolom koppen opgeven. U kunt alleen opgeven wat er wordt weer gegeven in de rijen van de tabel, zoals welke objecten worden weer gegeven.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door een specifieke definitie van de lijst weergave:

- Het [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -element definieert welke objecten worden weer gegeven door de definitie.

- Het element [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) specificeert het .net-object dat wordt weer gegeven door de definitie. Wanneer u dit element gebruikt, is de volledig gekwalificeerde .NET-type naam vereist. U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.

- Het [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) -element (niet weer gegeven) bevat een set objecten die kunnen worden weer gegeven door deze definitie. U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.

- Het element [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (niet weer gegeven) bevat een voor waarde die voor deze definitie moet bestaan. U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven. Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het definiëren van selectie voorwaarden.

## <a name="using-format-strings"></a>Opmaak teken reeksen gebruiken

Opmaak teken reeksen kunnen worden toegevoegd aan een weer gave om te bepalen hoe de gegevens worden weer gegeven. In het volgende voor beeld ziet u hoe u een opmaak teken reeks definieert voor de waarde van de eigenschap `StartTime`.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

De volgende XML-elementen kunnen worden gebruikt om een notatie patroon op te geven:

- Het [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element definieert de eigenschap of het script waarvan de waarde wordt weer gegeven in de kolom van de rij. Voor elke kolom van de rij is een [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element vereist. De eerste vermelding wordt weer gegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.

- Met het element [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) wordt de eigenschap opgegeven waarvan de waarde wordt weer gegeven in de rij. U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.

- Het element [formats Tring](./label-element-for-listitem-for-listcontrol-format.md) geeft een opmaak patroon op dat bepaalt hoe de eigenschap of script waarde wordt weer gegeven.

In het volgende voor beeld wordt de methode `ToString` aangeroepen om de waarde van het script op te maken. Scripts kunnen een wille keurige methode van een object aanroepen. Als een object een methode heeft, zoals `ToString`, die opmaak parameters heeft, kan het script deze methode ook aanroepen om de uitvoer waarde van het script op te maken.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

Het volgende XML-element kan worden gebruikt om de `ToString`-methode aan te roepen:

- Het [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element definieert de eigenschap of het script waarvan de waarde wordt weer gegeven in de kolom van de rij. Voor elke kolom van de rij is een [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -element vereist. De eerste vermelding wordt weer gegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.

- Het [script Block](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) -element geeft het script op waarvan de waarde wordt weer gegeven in de rij. U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
