---
title: Opmaak-overzicht | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851917"
---
# <a name="formatting-file-overview"></a>Overzicht voor opmaakbestanden

De notatie voor de objecten die worden geretourneerd door opdrachten (cmdlets, functies en scripts) worden gedefinieerd met behulp van opmaak-bestanden (format.ps1xml). Aantal van deze bestanden worden geleverd door PowerShell voor het definiëren van de weergave-indeling voor die objecten geretourneerd door de opgegeven PowerShell opdrachten, zoals de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object dat wordt geretourneerd door de `Get-Process` cmdlet. Echter, u kunt ook uw eigen aangepaste opmaak bestanden als u wilt overschrijven van de standaard weergave-indelingen maken of kunt u een aangepaste opmaak bestand voor het definiëren van de weergave van objecten die worden geretourneerd door uw eigen opdrachten.

> [!IMPORTANT]
> Opmaak bestanden bepalen de elementen van een object die worden geretourneerd aan de pijplijn niet. Wanneer een object wordt geretourneerd aan de pijplijn, zijn alle leden van dat object beschikbaar, zelfs als sommige worden niet weergegeven.

PowerShell maakt gebruik van de gegevens in deze opmaak bestanden om te bepalen wat wordt weergegeven en hoe de weergegeven gegevens zijn opgemaakt. De weergegeven gegevens kunnen de eigenschappen van een object of de waarde van een script bevatten. Scripts worden gebruikt als u weergeven van een waarde die niet rechtstreeks vanuit de eigenschappen van een object wilt, zoals het toevoegen van de waarde van de twee eigenschappen van een object en klikt u vervolgens de som weer te geven als een onderdeel van de gegevens beschikbaar is. Opmaak van de weergegeven gegevens wordt gedaan door het definiëren van weergaven voor de objecten die u wilt weergeven. U kunt voor elk object één weergave definiëren, kunt u één weergave voor meerdere objecten of kunt u meerdere weergaven voor hetzelfde object. Er is geen limiet voor het aantal weergaven die u kunt definiëren.

## <a name="common-features-of-formatting-files"></a>Algemene functies van opmaak bestanden

Elk bestand opmaak kunt de volgende onderdelen die kunnen worden gedeeld met alle weergaven die zijn gedefinieerd door het bestand definiëren:

- Standaard configuratie-instelling, zoals of de gegevens die worden weergegeven in de rijen van tabellen worden weergegeven op de volgende regel als de gegevens langer dan de breedte van de kolom is. Zie voor meer informatie over deze instellingen [algemene configuratie-instellingen definiëren](./defining-common-configuration-features.md).

- Sets van objecten die kunnen worden weergegeven door een van de weergaven van de opmaak-bestand. Voor meer informatie over deze sets (aangeduid als *selectiesets*), Zie [ingesteld definiëren van objecten](./defining-selection-sets.md).

- Algemene besturingselementen die kunnen worden gebruikt door alle weergaven van de opmaak-bestand. Besturingselementen kunnen u de mate van controle op hoe gegevens worden weergegeven. Zie voor meer informatie over de besturingselementen [definiëren van aangepaste besturingselementen](./creating-custom-controls.md).

## <a name="formatting-views"></a>Opmaak van weergaven

Opmaak weergaven kunnen objecten weergeven in een tabelindeling, lijstweergave, beeldschermen en aangepaste notatie. Voor het overgrote deel wordt elke opmaak definitie beschreven door een set XML-labels die worden beschreven van de weergave. Elke weergave bevat de naam van de weergave de objecten die gebruikmaken van de weergave en de elementen van de weergave, zoals de kolommen en rijen gegevens voor een tabelweergave.

Tabel weergave bevat de eigenschappen van een object of een waarde voor het blokkeren van script in een of meer kolommen. Elke kolom vertegenwoordigt een enkele eigenschap van het object of de Scriptwaarde van een. U kunt weergeven als een tabel waarin de eigenschappen van een object, een subset van de eigenschappen van een object of een combinatie van eigenschappen en waarden van script definiëren. Elke rij van de tabel vertegenwoordigt een geretourneerde object. Het maken van de tabelweergave van een is heel vergelijkbaar met wanneer u een object doorgeven aan de `Format-Table` cmdlet. Zie voor meer informatie over deze weergave [tabelweergave](./creating-a-table-view.md).

Geef een lijst weergeven met de eigenschappen van een object of de Scriptwaarde van een in één kolom. Elke rij van de lijst geeft een optionele label of de naam van de eigenschap gevolgd door de waarde van de eigenschap of het script. Het maken van een lijst weergeven is heel vergelijkbaar met een object te sluizen de `Format-List` cmdlet. Zie voor meer informatie over deze weergave [lijstweergave](./creating-a-list-view.md).

Brede weergave bevat één eigenschap van een object of de Scriptwaarde van een in een of meer kolommen. Er is geen label of de header voor deze weergave. Het maken van een brede weergave is vergelijkbaar met een object te sluizen de `Format-Wide` cmdlet. Zie voor meer informatie over deze weergave [brede weergave](./creating-a-wide-view.md).

Aangepaste weergave bevat een aanpasbare weergave van eigenschappen van het object of script waarden die niet in overeenstemming is met de Star structuur van de tabelweergaven, lijstweergaven of breed weergaven. U kunt een zelfstandige aangepaste weergave definiëren of kunt u een aangepaste weergave die wordt gebruikt door een andere weergave, zoals een tabel of lijstweergave. Het maken van een aangepaste weergave is vergelijkbaar met een object te sluizen de `Format-Custom` cmdlet. Zie voor meer informatie over deze weergave [aangepaste weergave](./creating-custom-controls.md).

## <a name="components-of-a-view"></a>Onderdelen van een weergave

De volgende XML-voorbeelden ziet de basisonderdelen van de XML van een weergave. De afzonderlijke XML-elementen variëren, afhankelijk van welke weergave die u wilt maken, maar de basisonderdelen van de weergaven zijn allemaal hetzelfde.

Te beginnen met elke weergave bevat een `Name` element dat Hiermee geeft u een beschrijvende naam die wordt gebruikt om te verwijzen naar de weergave. een `ViewSelectedBy` element waarmee wordt gedefinieerd welke .NET-objecten worden weergegeven in de weergave en een *besturingselement* element dat de weergave wordt gedefinieerd.

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

In het besturingselement-element, kunt u definiëren een of meer *vermelding* elementen. Als u meerdere definities gebruikt, moet u opgeven welke .NET-objecten gebruiken elke definitie. Meestal is slechts één vermelding, met slechts één definitie nodig voor elk besturingselement.

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

Binnen elk element van de vermelding van een weergave, geeft u de *item* elementen waarmee de .NET-eigenschappen of scripts die worden weergegeven in deze weergave wordt gedefinieerd.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

Zoals weergegeven in de voorgaande voorbeelden, de opmaak-bestand meerdere weergaven kan bevatten, een weergave kan meerdere definities bevatten en elke definitie van meerdere items kan bevatten.

## <a name="example-of-a-table-view"></a>Voorbeeld van een tabelweergave

Het volgende voorbeeld ziet de XML-labels die worden gebruikt voor het definiëren van weergeven als een tabel met twee kolommen. De [ViewDefinitions](./viewdefinitions-element-format.md) element is de containerelement voor de weergaven die zijn gedefinieerd in het bestand met opmaak. De [weergave](./view-element-format.md) element wordt gedefinieerd voor de specifieke tabel, lijst, breed of een aangepaste weergave. Binnen elk [weergave](./view-element-format.md) -element de [naam](./name-element-for-view-format.md) element Hiermee geeft u de naam van de weergave de [ViewSelectedBy](./viewselectedby-element-format.md) element definieert de objecten die gebruikmaken van de weergave en de verschillende controle over de elementen (zoals de `TableControl` element in het volgende voorbeeld wordt weergegeven) het type van de weergave definiëren.

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

[Het maken van een lijst weergeven](./creating-a-list-view.md)

[Het maken van een tabelweergave](./creating-a-table-view.md)

[Het maken van een brede weergave](./creating-a-wide-view.md)

[Het maken van aangepaste besturingselementen](./creating-custom-controls.md)

[Schrijven van een PowerShell-opmaak en typen bestand](./writing-a-powershell-formatting-file.md)
