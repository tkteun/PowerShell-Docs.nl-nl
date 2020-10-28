---
ms.date: 09/13/2016
ms.topic: reference
title: Aangepaste opmaakbestanden
description: Aangepaste opmaakbestanden
ms.openlocfilehash: 16e1c1046e25b35ff346585a5fd930c449c04bf8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653241"
---
# <a name="custom-formatting-files"></a>Aangepaste opmaakbestanden

De weergave notatie voor de objecten die worden geretourneerd door cmdlets, functies en scripts worden gedefinieerd met behulp van indelings bestanden (format.ps1XML-bestanden). Een aantal van deze bestanden wordt geleverd door Windows Power shell om de standaard weergave-indeling te definiëren voor de objecten die worden geretourneerd door Windows Power shell-cmdlets. U kunt echter ook uw eigen aangepaste opmaak bestanden maken om de standaard weergave indelingen te overschrijven of om de weer gave van objecten te definiëren die door uw eigen opdrachten worden geretourneerd.

Windows Power shell gebruikt de gegevens in deze indelings bestanden om te bepalen wat wordt weer gegeven en hoe de gegevens worden opgemaakt. De weer gegeven gegevens kunnen de eigenschappen van een object of de waarde van een script blok bevatten.  Script blokken worden gebruikt als u een bepaalde waarde wilt weer geven die niet rechtstreeks vanuit de eigenschappen van een object beschikbaar is. U kunt bijvoorbeeld de waarde van twee eigenschappen van een object toevoegen en de som als afzonderlijke gegevens weer geven. Wanneer u uw eigen opmaak bestand schrijft, moet u *weer gaven* definiëren voor de objecten die u wilt weer geven. U kunt één weer gave definiëren voor elk object, u kunt één weer gave voor meerdere objecten definiëren, maar u kunt ook meerdere weer gaven definiëren voor hetzelfde object. Er is geen limiet voor het aantal weer gaven dat u kunt definiëren.

> [!IMPORTANT]
> Indelings bestanden bepalen niet welke elementen van een object worden geretourneerd naar de pijp lijn. Wanneer een object wordt geretourneerd naar de pijp lijn, zijn alle leden van dat object beschikbaar.

## <a name="format-views"></a>Opmaak weergaven

In opmaak weergaven kunnen objecten worden weer gegeven in een tabel indeling, een lijst opmaak, een brede indeling en een aangepaste notatie. Voor de meeste delen wordt elke opmaak definitie beschreven met een set XML-tags die een weer gave beschrijven. Elke weer gave bevat de naam van de weer gave, de objecten die gebruikmaken van de weer gave en de elementen van de weer gave, zoals de kolom-en rij-informatie voor een tabel weergave.

De volgende weer gaven zijn beschikbaar.

In de tabel weergave worden de eigenschappen van een object of een script blok waarde in een of meer kolommen weer gegeven. Elke kolom vertegenwoordigt een eigenschap van het object of een script blok waarde. U kunt een tabel weergave definiëren waarin alle eigenschappen van een object, een subset van de eigenschappen van een object of een combi natie van eigenschappen en script blok waarden worden weer gegeven. Elke rij van de tabel vertegenwoordigt een geretourneerd object. Zie [tabel weergave](../format/creating-a-table-view.md)voor meer informatie over deze weer gave.

In de lijst weergave worden de eigenschappen van een object of een script blok waarde in één kolom weer gegeven. Elke rij van de lijst bevat een optioneel label of de naam van de eigenschap gevolgd door de waarde van de eigenschap of het script blok. Zie [lijst weergave](../format/creating-a-list-view.md)voor meer informatie over deze weer gave.

Breedbeeld weergave bevat een enkele eigenschap van een object of een script blok waarde in een of meer kolommen. Er is geen label of koptekst voor deze weer gave. Zie [brede weer](../format/creating-a-wide-view.md)gave voor meer informatie over deze weer gave.

In de aangepaste weer gave wordt een aanpas bare weer gave weer gegeven van object eigenschappen of script blok waarden die niet voldoen aan de stijve structuur van tabel weergaven, lijst weergaven of brede weer gaven. U kunt een zelfstandige aangepaste weer gave definiëren, maar u kunt ook een aangepaste weer gave definiëren die wordt gebruikt door een andere weer gave, zoals een tabel weergave of lijst weergave. Zie [aangepaste weer gave](../format/creating-custom-controls.md)voor meer informatie over deze weer gave.

## <a name="view-xml-elements"></a>XML-elementen weer geven

In het volgende voor beeld ziet u de XML-labels die worden gebruikt voor het definiëren van een tabel weergave die twee kolommen bevat. Het element [ViewDefinitions](../format/viewdefinitions-element-format.md) is het container element voor alle weer gaven die in het opmaak bestand zijn gedefinieerd. Het element [weer gave](../format/view-element-format.md) definieert de specifieke tabel, lijst, brede of aangepaste weer gave. In elke weer gave geeft het element [name](../format/name-element-for-view-format.md) de naam van de weer gave, het [ViewSelectedBy](../format/viewselectedby-element-format.md) -element definieert de objecten die gebruikmaken van de weer gave en de verschillende elementen van het besturings element (zoals het `TableControl` element) definiëren de indeling van de weer gave.

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

## <a name="see-also"></a>Zie ook

[Tabel weergave](../format/creating-a-table-view.md)

[Lijst weergave](../format/creating-a-list-view.md)

[Brede weer gave](../format/creating-a-wide-view.md)

[Aangepaste weer gave](../format/creating-custom-controls.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
