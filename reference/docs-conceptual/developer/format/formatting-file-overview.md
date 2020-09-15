---
title: Overzicht van het format teren van bestanden | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: efdd3eed15c5f3c88636fcbe7a39f6c6cfb20ced
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773501"
---
# <a name="formatting-file-overview"></a>Overzicht voor opmaakbestanden

De weer gave-indeling voor de objecten die worden geretourneerd door de opdrachten (cmdlets, functies en scripts) worden gedefinieerd met behulp van indelings bestanden (format.ps1XML-bestanden). Verschillende van deze bestanden worden geleverd door Power shell om de weergave notatie te definiëren voor objecten die worden geretourneerd door Power shell-opdrachten, zoals het [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -object dat door de cmdlet wordt geretourneerd `Get-Process` . U kunt echter ook uw eigen aangepaste opmaak bestanden maken om de standaard notaties te overschrijven of u kunt een aangepast opmaak bestand schrijven om de weer gave van objecten te definiëren die door uw eigen opdrachten worden geretourneerd.

> [!IMPORTANT]
> Indelings bestanden bepalen niet welke elementen van een object worden geretourneerd naar de pijp lijn. Wanneer een object wordt geretourneerd naar de pijp lijn, zijn alle leden van dat object beschikbaar, zelfs als sommige niet worden weer gegeven.

Power shell gebruikt de gegevens in deze indelings bestanden om te bepalen wat wordt weer gegeven en hoe de weer gegeven gegevens worden opgemaakt. De weer gegeven gegevens kunnen de eigenschappen van een object of de waarde van een script bevatten. Scripts worden gebruikt als u een bepaalde waarde wilt weer geven die niet rechtstreeks beschikbaar is vanuit de eigenschappen van een object, zoals het toevoegen van de waarde van twee eigenschappen van een object en de som als een stukje gegevens wordt weer gegeven. De indeling van de weer gegeven gegevens wordt uitgevoerd door weer gaven te definiëren voor de objecten die u wilt weer geven. U kunt één weer gave definiëren voor elk object, u kunt één weer gave voor meerdere objecten definiëren, maar u kunt ook meerdere weer gaven definiëren voor hetzelfde object. Er is geen limiet voor het aantal weer gaven dat u kunt definiëren.

## <a name="common-features-of-formatting-files"></a>Algemene functies van het format teren van bestanden

Elk opmaak bestand kan de volgende onderdelen definiëren die kunnen worden gedeeld in alle weer gaven die door het bestand worden gedefinieerd:

- De standaard configuratie-instelling, zoals of de gegevens in de rijen met tabellen worden weer gegeven op de volgende regel als de gegevens langer zijn dan de breedte van de kolom. Zie [algemene configuratie-instellingen definiëren](./defining-common-configuration-features.md)voor meer informatie over deze instellingen.

- Sets van objecten die kunnen worden weer gegeven in een van de weer gaven van het opmaak bestand. Zie [sets met objecten definiëren](./defining-selection-sets.md)voor meer informatie over deze sets (ook wel *selectie sets*genoemd).

- Algemene besturings elementen die kunnen worden gebruikt door alle weer gaven van het opmaak bestand. Met besturings elementen krijgt u meer controle over de manier waarop gegevens worden weer gegeven. Zie [aangepaste besturings elementen definiëren](./creating-custom-controls.md)voor meer informatie over besturings elementen.

## <a name="formatting-views"></a>Opmaak weergaven

In opmaak weergaven kunnen objecten worden weer gegeven in een tabel indeling, lijst opmaak, brede notatie en aangepaste notatie. Voor de meeste delen wordt elke opmaak definitie beschreven met een set XML-tags die de weer gave beschrijven. Elke weer gave bevat de naam van de weer gave, de objecten die gebruikmaken van de weer gave en de elementen van de weer gave, zoals de kolom-en rij-informatie voor een tabel weergave.

In de tabel weergave worden de eigenschappen van een object of een script blok waarde in een of meer kolommen weer gegeven. Elke kolom vertegenwoordigt één eigenschap van het object of een script waarde. U kunt een tabel weergave definiëren waarin alle eigenschappen van een object, een subset van de eigenschappen van een object of een combi natie van eigenschappen en script waarden worden weer gegeven. Elke rij van de tabel vertegenwoordigt een geretourneerd object. Het maken van een tabel weergave lijkt sterk op wanneer u een object naar de `Format-Table` cmdlet pipet. Zie [tabel weergave](./creating-a-table-view.md)voor meer informatie over deze weer gave.

In de lijst weergave worden de eigenschappen van een object of een script waarde in één kolom weer gegeven. Elke rij van de lijst bevat een optioneel label of de naam van de eigenschap gevolgd door de waarde van de eigenschap of het script. Het maken van een lijst weergave lijkt sterk op het sluizen van een object naar de `Format-List` cmdlet. Zie [lijst weergave](./creating-a-list-view.md)voor meer informatie over deze weer gave.

Breedbeeld weergave bevat een enkele eigenschap van een object of een script waarde in een of meer kolommen. Er is geen label of koptekst voor deze weer gave. Het maken van een brede weer gave lijkt sterk op het sluizen van een object naar de `Format-Wide` cmdlet. Zie [brede weer](./creating-a-wide-view.md)gave voor meer informatie over deze weer gave.

In de aangepaste weer gave wordt een aanpas bare weer gave weer gegeven van object eigenschappen of script waarden die niet voldoen aan de stijve structuur van tabel weergaven, lijst weergaven of brede weer gaven. U kunt een zelfstandige aangepaste weer gave definiëren, maar u kunt ook een aangepaste weer gave definiëren die wordt gebruikt door een andere weer gave, zoals een tabel weergave of lijst weergave. Het maken van een aangepaste weer gave lijkt sterk op het sluizen van een object naar de `Format-Custom` cmdlet. Zie [aangepaste weer gave](./creating-custom-controls.md)voor meer informatie over deze weer gave.

## <a name="components-of-a-view"></a>Onderdelen van een weer gave

In de volgende XML-voor beelden ziet u de algemene XML-onderdelen van een weer gave. De afzonderlijke XML-elementen variëren, afhankelijk van de weer gave die u wilt maken, maar de basis onderdelen van de weer gaven zijn allemaal hetzelfde.

Elke weer gave heeft een `Name` element dat een gebruiks vriendelijke naam specificeert die wordt gebruikt om te verwijzen naar de weer gave om te beginnen met. een `ViewSelectedBy` element dat definieert welke .net-objecten worden weer gegeven in de weer gave en een *Control* -element waarmee de weer gave wordt gedefinieerd.

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

Binnen het element Control kunt u een of meer *invoer* elementen definiëren. Als u meerdere definities gebruikt, moet u opgeven welke .NET-objecten elke definitie gebruiken. Normaal gesp roken is slechts één vermelding, met slechts één definitie, nodig voor elk besturings element.

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

Binnen elk item element van een weer gave geeft u de *element* elementen op waarmee de .net-eigenschappen of-scripts worden gedefinieerd die door die weer gave worden weer gegeven.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

Zoals in de voor gaande voor beelden wordt weer gegeven, kan het opmaak bestand meerdere weer gaven bevatten, een weer gave meerdere definities kan bevatten en elke definitie meerdere items kan bevatten.

## <a name="example-of-a-table-view"></a>Voor beeld van een tabel weergave

In het volgende voor beeld ziet u de XML-labels die worden gebruikt voor het definiëren van een tabel weergave die twee kolommen bevat. Het element [ViewDefinitions](./viewdefinitions-element-format.md) is het container element voor alle weer gaven die in het opmaak bestand zijn gedefinieerd. Het element [weer gave](./view-element-format.md) definieert de specifieke tabel, lijst, brede of aangepaste weer gave. In elk [weer gave](./view-element-format.md) -element geeft het element [name](./name-element-for-view-format.md) de naam van de weer gave, het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert de objecten die gebruikmaken van de weer gave en de verschillende elementen van het besturings element (zoals het `TableControl` element dat in het volgende voor beeld wordt weer gegeven) definiëren het type weer gave.

```xml
<ViewDefinitions>
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

## <a name="see-also"></a>Zie ook

[Een lijstweergave maken](./creating-a-list-view.md)

[Een tabelweergave maken](./creating-a-table-view.md)

[Een brede weergave maken](./creating-a-wide-view.md)

[Aangepaste besturingselementen maken](./creating-custom-controls.md)

[Een Power shell-indeling en-typen bestand schrijven](./writing-a-powershell-formatting-file.md)
