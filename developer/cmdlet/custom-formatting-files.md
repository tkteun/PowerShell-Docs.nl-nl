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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850034"
---
# <a name="custom-formatting-files"></a>Aangepaste opmaakbestanden

De notatie voor de objecten die zijn geretourneerd door cmdlets, functies en scripts worden gedefinieerd met behulp van opmaak-bestanden (format.ps1xml). Aantal van deze bestanden worden geleverd door Windows PowerShell voor het definiëren van de standaardindeling voor de weergave voor die objecten geretourneerd door de Windows PowerShell-cmdlets. U kunt echter ook uw eigen aangepaste opmaak bestanden te overschrijven van de standaard-notatie of voor het definiëren van de weergave van objecten die worden geretourneerd door uw eigen opdrachten maken.

Windows PowerShell gebruikt de gegevens in deze opmaak bestanden om te bepalen wat wordt weergegeven en hoe de gegevens zijn opgemaakt. De weergegeven gegevens kunnen de eigenschappen van een object of de waarde van een scriptblok bevatten.  Scriptblokken worden gebruikt als u wilt weergeven van een waarde die rechtstreeks in de eigenschappen van een object is niet beschikbaar. U wilt bijvoorbeeld de waarde van de twee eigenschappen van een object toevoegen en de som weergegeven als een afzonderlijke hoeveelheid gegevens. Wanneer u uw eigen opmaak-bestand schrijven, moet u voor het definiëren van *weergaven* voor de objecten die u wilt weergeven. U kunt voor elk object één weergave definiëren, kunt u één weergave voor meerdere objecten of kunt u meerdere weergaven voor hetzelfde object. Er is geen limiet voor het aantal weergaven die u kunt definiëren.

> [!IMPORTANT]
> Opmaak bestanden bepalen de elementen van een object die worden geretourneerd aan de pijplijn niet. Wanneer een object wordt geretourneerd aan de pijplijn, vindt u alle leden van dat object.

## <a name="format-views"></a>Indeling weergaven

Opmaak weergaven kunnen objecten weergeven in de vorm van een tabel, een indeling heeft, een breed indeling en een aangepaste notatie. Voor het overgrote deel wordt elke opmaak definitie beschreven door een set XML-labels die worden beschreven van een weergave. Elke weergave bevat de naam van de weergave de objecten die gebruikmaken van de weergave en de elementen van de weergave, zoals de kolommen en rijen gegevens voor een tabelweergave.

De volgende weergaven zijn beschikbaar.

Tabelweergave worden de eigenschappen van een object of een waarde voor het blokkeren van script in een of meer kolommen. Elke kolom vertegenwoordigt een eigenschap van het object of de waarde van een script blokkeren. Weergeven als een tabel waarin alle eigenschappen van een object, een subset van de eigenschappen van een object of een combinatie van eigenschappen en script blok waarden worden weergegeven, kunt u definiëren. Elke rij van de tabel vertegenwoordigt een geretourneerde object. Zie voor meer informatie over deze weergave [tabelweergave](../format/creating-a-table-view.md).

Lijstweergave geeft een lijst van de eigenschappen van een object of een waarde voor het blokkeren van script in één kolom. Elke rij van de lijst geeft een optioneel label of de naam van de eigenschap gevolgd door de waarde van het blok eigenschap of het script. Zie voor meer informatie over deze weergave [lijstweergave](../format/creating-a-list-view.md).

Brede weergave bevat één eigenschap van een object of een waarde voor het blokkeren van script in een of meer kolommen. Er is geen label of de header voor deze weergave. Zie voor meer informatie over deze weergave [brede weergave](../format/creating-a-wide-view.md).

Aangepaste weergave bevat een aanpasbare weergave van eigenschappen van het object of script blok waarden die niet in overeenstemming is met de Star structuur van de tabelweergaven, lijstweergaven of breed weergaven. Kunt u een aangepaste weergave van zelfstandige of kunt u een aangepaste weergave die wordt gebruikt door een andere weergave, zoals een tabel of lijstweergave. Zie voor meer informatie over deze weergave [aangepaste weergave](../format/creating-custom-controls.md).

## <a name="view-xml-elements"></a>XML-elementen weergeven

Het volgende voorbeeld ziet de XML-labels die worden gebruikt voor het definiëren van weergeven als een tabel met twee kolommen. De [ViewDefinitions](../format/viewdefinitions-element-format.md) element is de containerelement voor de weergaven die zijn gedefinieerd in het bestand met opmaak. De [weergave](../format/view-element-format.md) element wordt gedefinieerd voor de specifieke tabel, lijst, breed of een aangepaste weergave. Binnen elke weergave de [naam](../format/name-element-for-view-format.md) element Hiermee geeft u de naam van de weergave de [ViewSelectedBy](../format/viewselectedby-element-format.md) element definieert de objecten die gebruikmaken van de weergave en de verschillende beheer-elementen (zoals de `TableControl` element) de indeling van de weergave definiëren.

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

[Tabelweergave](../format/creating-a-table-view.md)

[Lijstweergave](../format/creating-a-list-view.md)

[Brede weergave](../format/creating-a-wide-view.md)

[Aangepaste weergave](../format/creating-custom-controls.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
