---
title: Het maken van een tabelweergave | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066835"
---
# <a name="creating-a-table-view"></a>Een tabelweergave maken

Gegevens weergegeven weergeven als een tabel in een of meer kolommen. Elke rij in de tabel vertegenwoordigt een .NET-object en elke kolom in de tabel een eigenschap van het object of de Scriptwaarde van een. Weergeven als een tabel die de eigenschappen van een object of een subset van de eigenschappen van een object wordt weergegeven, kunt u definiëren.

## <a name="a-table-view-display"></a>De weergave van een tabel

Het volgende voorbeeld laat zien hoe de Windows PowerShell wordt weergegeven de [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object dat wordt geretourneerd door de [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. Voor dit object is Windows PowerShell weergeven als een tabel die wordt gedefinieerd. de `Status` eigenschap, de `Name` eigenschap (deze eigenschap is een alias-eigenschap voor de `ServiceName` eigenschap), en de `DisplayName` eigenschap. Elke rij in de tabel vertegenwoordigt een object dat wordt geretourneerd door de cmdlet.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>De tabelweergave definiëren

Het volgende XML-bestand ziet u het tabelschema van de weergave voor het weergeven van de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object. U moet elke eigenschap die u weergeven in de tabelweergave wilt.

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

De volgende XML-elementen worden gebruikt voor het definiëren van een lijst weergeven:

- De [weergave](./view-element-format.md) -element is het bovenliggende element van de tabelweergave. (Dit is hetzelfde bovenliggende element voor de lijst, breed en aangepaste weergaven.)

- De [naam](./name-element-for-view-format.md) element Hiermee geeft u de naam van de weergave. Dit element is vereist voor alle weergaven.

- De [ViewSelectedBy](./viewselectedby-element-format.md) element definieert de objecten die gebruikmaken van de weergave. Dit element is vereist.

- De [GroupBy](./groupby-element-for-view-format.md) element (niet weergegeven in dit voorbeeld) wordt gedefinieerd wanneer een nieuwe groep objecten wordt weergegeven. Een nieuwe groep wordt gestart wanneer de waarde van een bepaalde eigenschap of script wijzigt. Dit element is optioneel.

- De [besturingselementen](./controls-element-for-view-format.md) element (niet weergegeven in dit voorbeeld) definieert de aangepaste besturingselementen die zijn gedefinieerd door de tabelweergave. Besturingselementen kunnen u nader aangeven hoe de gegevens worden weergegeven. Dit element is optioneel. Een weergave een eigen aangepaste besturingselementen kunt definiëren of deze algemene besturingselementen die kunnen worden gebruikt door elke weergave in de opmaak-bestand kunt gebruiken. Zie voor meer informatie over aangepaste besturingselementen [het maken van aangepaste besturingselementen](./creating-custom-controls.md).

- De [HideTableHeaders](./hidetableheaders-element-format.md) element (niet weergeven in dit voorbeeld) geeft aan dat de tabel niet in de labels die aan de bovenkant van de tabel weergegeven wordt. Dit element is optioneel.

- De [TableControl](./tablecontrol-element-format.md) element dat de kop- en gegevens van de tabel definieert. Net als bij alle andere weergaven, een tabel weergave kan de waarden van eigenschappen van het object of de waarden die worden gegenereerd door scripts.

## <a name="defining-column-headers"></a>Kolomkoppen definiëren

1. De [TableHeaders](./tableheaders-element-format.md) -element en de onderliggende elementen definiëren wat wordt weergegeven aan de bovenkant van de tabel.

2. De [TableColumnHeader](./tablecolumnheader-element-format.md) element wordt gedefinieerd wat er aan de bovenkant van een kolom van de tabel wordt weergegeven. Geef deze elementen in de volgorde waarin u de headers weergegeven.

   Er is geen limiet voor het aantal van deze element dat u kunt gebruiken, maar het aantal [TableColumnHeader](./tablecolumnheader-element-format.md) elementen in uw tabelweergave moeten gelijk zijn aan het aantal [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elementen die u gebruikt.

3. De [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element Hiermee geeft u de tekst die wordt weergegeven. Dit element is optioneel.

4. De [breedte](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element geeft de breedte (in tekens) van de kolom. Dit element is optioneel.

5. De [uitlijning](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element geeft aan hoe het label wordt weergegeven. Het label kan worden afgestemd op de links aan de rechterkant, of gecentreerd. Dit element is optioneel.

## <a name="defining-the-table-rows"></a>De tabelrijen definiëren

Tabelweergaven krijgt u een of meer definities die welke gegevens worden weergegeven in de rijen van de tabel opgeeft met behulp van de onderliggende elementen van de [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element. U ziet dat u kunt meerdere definities voor de rijen van de tabel opgeven, maar de headers voor de rijen blijft hetzelfde, ongeacht welke rijdefinitie wordt gebruikt. Een tabel wordt meestal slechts één definitie bevatten.

In het volgende voorbeeld wordt de weergave bevat één definitie waarin de waarden van verschillende eigenschappen van de [System.Diagnostics.Process? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) object. Weergeven als een tabel weergeven, de waarde van een eigenschap of de waarde van een script (niet weergegeven in het voorbeeld) in de rijen.

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

De volgende XML-elementen kunnen worden gebruikt voor definities voor een rij:

- De [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) -element en de onderliggende elementen definiëren wat wordt weergegeven in de rijen van de tabel.

- De [TableRowEntry](./listentry-element-for-listcontrol-format.md) -element bevat een definitie van de rij. Ten minste één [TableRowEntry](./listentry-element-for-listcontrol-format.md) is vereist; er is echter geen maximale limiet voor het aantal elementen die u kunt toevoegen. In de meeste gevallen wordt een weergave slechts één definitie hebben.

- De [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element Hiermee geeft u de objecten die worden weergegeven door de definitie van een specifieke. Dit element is optioneel en is alleen nodig wanneer u meerdere definiëren [TableRowEntry](./listentry-element-for-listcontrol-format.md) elementen die verschillende objecten worden weergegeven.

- De [verpakken](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element geeft aan dat de tekst die langer is dan de breedte van de kolom wordt weergegeven op de volgende regel. Standaard de tekst die langer is dan de breedte van legendakolom wordt afgekapt.

- De [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element definieert de eigenschappen of scripts waarvan de waarden worden weergegeven in de rij.

- De [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element wordt gedefinieerd voor de eigenschap of het script waarvan de waarde wordt weergegeven in de kolom van de rij. Een [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is vereist voor elke kolom van de rij. De eerste vermelding wordt weergegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.

- De [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element Hiermee geeft u de eigenschap waarvan de waarde wordt weergegeven in de rij. U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.

- De [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element Hiermee geeft u het script waarvan de waarde wordt weergegeven in de rij. U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.

- De [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script wordt weergegeven. Dit element is optioneel.

- De [uitlijning](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element geeft aan hoe de waarde van de eigenschap of het script wordt weergegeven. De waarde kan worden afgestemd op de links aan de rechterkant, of gecentreerd. Dit element is optioneel.

## <a name="defining-the-objects-that-use-the-table-view"></a>De objecten die gebruikmaken van de tabelweergave definiëren

Er zijn twee manieren om te definiëren welke objecten .NET gebruiken de tabelweergave. U kunt de [ViewSelectedBy](./viewselectedby-element-format.md) element voor het definiëren van de objecten die kunnen worden weergegeven door de definities van de weergave, of u kunt de [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element te definiëren welke objecten worden weergegeven door een de definitie van de weergave van specifieke. In de meeste gevallen een weergave heeft slechts één definitie zodat objecten worden gewoonlijk gedefinieerd door de [ViewSelectedBy](./viewselectedby-element-format.md) element.

Het volgende voorbeeld ziet u hoe u de objecten die worden weergegeven door de tabel weergeven met behulp van de [ViewSelectedBy](./viewselectedby-element-format.md) en [TypeName](./typename-element-for-viewselectedby-format.md) elementen. Er is geen limiet voor het aantal [TypeName](./typename-element-for-viewselectedby-format.md) elementen dat u opgeven kunt en de volgorde niet belangrijk is.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door de tabelweergave:

- De [ViewSelectedBy](./viewselectedby-element-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de lijstweergave.

- De [TypeName](./typename-element-for-viewselectedby-format.md) element Hiermee geeft u de .NET-object dat door de weergave wordt weergegeven. De volledig gekwalificeerde naam van de .NET-type is vereist. U moet ten minste één type of de selectie instellen voor de weergave opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.

Het volgende voorbeeld wordt de [ViewSelectedBy](./viewselectedby-element-format.md) en [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementen. Gebruik selectie wordt ingesteld wanneer er een gerelateerde set van objecten die worden weergegeven met behulp van meerdere weergaven, zoals wanneer u een lijst weergeven en een tabelweergave voor dezelfde objecten definiëren. Zie voor meer informatie over het maken van een selectieset [selectiesets definiëren](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door de lijstweergave:

- De [ViewSelectedBy](./viewselectedby-element-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de lijstweergave.

- De [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element Hiermee geeft u een set van objecten die kunnen worden weergegeven in de weergave. U moet ten minste één selectie instellen of type voor de weergave opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.

Het volgende voorbeeld ziet u hoe u de objecten weergegeven door een specifieke definitie van de tabel weergeven met behulp van de [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element. Met behulp van dit element, kunt u de .NET-typenaam van het object, een selectieset objecten of een selectievoorwaarde waarmee wordt aangegeven wanneer de definitie wordt gebruikt. Zie voor meer informatie over het maken van een selectie voorwaarden [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).

> [!NOTE]
> Bij het maken van meerdere definities van de tabelweergave kunt u verschillende kolomkoppen niet opgeven. U kunt opgeven wat wordt alleen weergegeven in de rijen van de tabel, zoals welke objecten worden weergegeven.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door een specifieke definitie van de lijstweergave:

- De [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de definitie.

- De [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element Hiermee geeft u de .NET-object dat door de definitie wordt weergegeven. Wanneer u dit element gebruikt, is de volledig gekwalificeerde naam van de .NET-type is vereist. U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.

- De [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (niet weergegeven) Hiermee geeft u een set van objecten die kunnen worden weergegeven door deze definitie. U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.

- De [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (niet weergegeven) Hiermee geeft u een voorwaarde moet bestaan voor deze definitie moet worden gebruikt. U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven. Zie voor meer informatie over het definiëren van de voorwaarden van de selectie [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).

## <a name="using-format-strings"></a>Met behulp van opmaaktekenreeksen

Opmaak tekenreeksen kunnen worden toegevoegd aan een weergave om verder te definiëren hoe de gegevens worden weergegeven. Het volgende voorbeeld ziet u hoe u een opmaaktekenreeks voor de waarde van de `StartTime` eigenschap.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

De volgende XML-elementen kunnen worden gebruikt om op te geven van een patroon indeling:

- De [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element wordt gedefinieerd voor de eigenschap of het script waarvan de waarde wordt weergegeven in de kolom van de rij. Een [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is vereist voor elke kolom van de rij. De eerste vermelding wordt weergegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.

- De [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element Hiermee geeft u de eigenschap waarvan de waarde wordt weergegeven in de rij. U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.

- De [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script wordt weergegeven.

In het volgende voorbeeld wordt de `ToString` methode aangeroepen om de indeling van de waarde van het script. Scripts kunnen elke methode van een object aangeroepen. Dus als een object een methode, zoals heeft `ToString`, met parameters voor formatteren, het script dat methode voor de indeling van de uitvoerwaarde van het script kunt aanroepen.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

De volgende XML-element kan worden gebruikt voor aanroepen de `ToString` methode:

- De [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element wordt gedefinieerd voor de eigenschap of het script waarvan de waarde wordt weergegeven in de kolom van de rij. Een [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is vereist voor elke kolom van de rij. De eerste vermelding wordt weergegeven in de eerste kolom, de tweede vermelding in de tweede kolom, enzovoort.

- De [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element Hiermee geeft u het script waarvan de waarde wordt weergegeven in de rij. U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
