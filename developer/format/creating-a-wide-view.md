---
title: Het maken van een brede weergave | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066716"
---
# <a name="creating-a-wide-view"></a>Een brede weergave maken

Een brede weergave toont één waarde voor elk object dat wordt weergegeven. De weergegeven waarde mag de waarde van de eigenschap van een .NET-object of de waarde van een script. Standaard is er geen label of de header voor deze weergave.

## <a name="a-wide-view-display"></a>Een brede weergave weer te geven

Het volgende voorbeeld laat zien hoe de Windows PowerShell wordt weergegeven de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object dat wordt geretourneerd door de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet wanneer de uitvoer is doorgesluisd naar de [ Indeling hele](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet. (Standaard het [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet retourneert een tabelweergave.) In dit voorbeeld worden de twee kolommen worden gebruikt om de naam van het proces voor elke geretourneerde object weer te geven. De naam van eigenschap van het object niet wordt weergegeven, alleen de waarde van de eigenschap.

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a>De brede weergave definiëren

Het volgende XML-bestand ziet u het schema van de brede weergave voor de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

De volgende XML-elementen worden gebruikt voor het definiëren van een brede weergave:

- De [weergave](./view-element-format.md) -element is het bovenliggende element van de brede weergave. (Dit is hetzelfde bovenliggende element voor de tabel, lijst en weergaven voor het aangepaste besturingselement).

- De [naam](./name-element-for-view-format.md) element Hiermee geeft u de naam van de weergave. Dit element is vereist voor alle weergaven.

- De [ViewSelectedBy](./viewselectedby-element-format.md) element definieert de objecten die gebruikmaken van de weergave. Dit element is vereist.

- De [GroupBy](./groupby-element-for-view-format.md) element wordt gedefinieerd wanneer een nieuwe groep objecten wordt weergegeven. Een nieuwe groep wordt gestart wanneer de waarde van een bepaalde eigenschap of script wijzigt. Dit element is optioneel.

- De [besturingselementen](./controls-element-for-view-format.md) elementen definieert de aangepaste besturingselementen die zijn gedefinieerd door de brede weergave. Besturingselementen kunnen u nader aangeven hoe de gegevens worden weergegeven. Dit element is optioneel. Een weergave een eigen aangepaste besturingselementen kunt definiëren of deze algemene besturingselementen die kunnen worden gebruikt door elke weergave in de opmaak-bestand kunt gebruiken. Zie voor meer informatie over aangepaste besturingselementen [het maken van aangepaste besturingselementen](./creating-custom-controls.md).

- De [WideControl](./widecontrol-element-format.md) -element en de onderliggende elementen definiëren wat wordt weergegeven in de weergave. In het voorgaande voorbeeld wordt de weergave is ontworpen om weer te geven de [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) eigenschap.

Zie voor een voorbeeld van een volledige opmaak bestand dat een eenvoudige brede weergave definieert [brede weergave (basis)](./wide-view-basic.md).

## <a name="providing-definitions-for-your-wide-view"></a>Definities voor uw brede weergave bieden

Breed weergaven kunnen een of meer definities bieden met behulp van de onderliggende elementen van de [WideControl](./widecontrol-element-format.md) element. Een weergave wordt meestal slechts één definitie hebben. In het volgende voorbeeld wordt de weergave bevat één definitie die de waarde van wordt de [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) eigenschap. Een brede weergave kan de waarde van een eigenschap of de waarde van een script (niet weergegeven in het voorbeeld).

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

De volgende XML-elementen kunnen worden gebruikt voor definities voor een brede weergave:

- De [WideControl](./widecontrol-element-format.md) -element en de onderliggende elementen definiëren wat wordt weergegeven in de weergave.

- De [AutoSize](./autosize-element-for-widecontrol-format.md) element geeft aan of de kolomgrootte en het aantal kolommen zijn aangepast op basis van de grootte van de gegevens. Dit element is optioneel.

- De [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element Hiermee geeft u het aantal kolommen in de brede weergave. Dit element is optioneel.

- De [WideEntries](./wideentries-element-for-widecontrol-format.md) element bevat de definities van de weergave. In de meeste gevallen wordt een weergave slechts één definitie hebben. Dit element is vereist.

- De [WideEntry](./wideentry-element-for-widecontrol-format.md) -element bevat een definitie van de weergave. Ten minste één [WideEntry](./wideentry-element-for-widecontrol-format.md) is vereist; er is echter geen maximale limiet voor het aantal elementen die u kunt toevoegen. In de meeste gevallen wordt een weergave slechts één definitie hebben.

- De [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element Hiermee geeft u de objecten die worden weergegeven door de definitie van een specifieke. Dit element is optioneel en is alleen nodig wanneer u meerdere definiëren [WideEntry](./wideentry-element-for-widecontrol-format.md) elementen die verschillende objecten worden weergegeven.

- De [WideItem](./wideitem-element-for-widecontrol-format.md) element Hiermee geeft u de gegevens die worden weergegeven in de weergave. In tegenstelling tot andere typen weergaven, een breed besturingselement kan slechts één item worden weergegeven.

- De [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element Hiermee geeft u de eigenschap waarvan de waarde wordt weergegeven in de weergave. U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.

- De [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element Hiermee geeft u het script waarvan de waarde wordt weergegeven in de weergave. U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.

- De [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element Hiermee geeft u een patroon dat wordt gebruikt om de gegevens weer te geven. Dit element is optioneel.

Zie voor een voorbeeld van een volledige opmaak-bestand dat de definitie van een brede weergave definieert [brede weergave (basis)](./wide-view-basic.md).

## <a name="defining-the-objects-that-use-the-wide-view"></a>De objecten die gebruikmaken van de brede weergave definiëren

Er zijn twee manieren om te definiëren welke objecten .NET gebruik maken van de brede weergave. U kunt de [ViewSelectedBy](./viewselectedby-element-format.md) element voor het definiëren van de objecten die kunnen worden weergegeven door de definities van de weergave, of u kunt de [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element te definiëren welke objecten worden weergegeven door een de definitie van de weergave van specifieke. In de meeste gevallen een weergave heeft slechts één definitie zodat objecten worden gewoonlijk gedefinieerd door de [ViewSelectedBy](./viewselectedby-element-format.md) element.

Het volgende voorbeeld ziet u hoe u de objecten die worden weergegeven met behulp van de brede weergave de [ViewSelectedBy](./viewselectedby-element-format.md) en [TypeName](./typename-element-for-viewselectedby-format.md) elementen. Er is geen limiet voor het aantal [TypeName](./typename-element-for-viewselectedby-format.md) elementen dat u opgeven kunt en de volgorde niet belangrijk is.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door de brede weergave:

- De [ViewSelectedBy](./viewselectedby-element-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de brede weergave.

- De [TypeName](./typename-element-for-viewselectedby-format.md) element Hiermee geeft u de .NET die wordt weergegeven in de weergave. De volledig gekwalificeerde naam van de .NET-type is vereist. U moet ten minste één type of de selectie instellen voor de weergave opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.

Zie voor een voorbeeld van een volledige opmaak bestand [brede weergave (basis)](./wide-view-basic.md).

Het volgende voorbeeld wordt de [ViewSelectedBy](./viewselectedby-element-format.md) en [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementen. Gebruik selectiesets waarin u een gerelateerde set van objecten die worden weergegeven met behulp van meerdere weergaven, zoals wanneer u een brede weergave definiëren en een tabelweergave voor dezelfde objecten hebben. Zie voor meer informatie over het maken van een selectieset [selectiesets definiëren](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door de brede weergave:

- De [ViewSelectedBy](./viewselectedby-element-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de brede weergave.

- De [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element Hiermee geeft u een set van objecten die kunnen worden weergegeven in de weergave. U moet ten minste één selectie instellen of type voor de weergave opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.

Het volgende voorbeeld ziet u hoe u de objecten die met een specifieke definitie van het gebruik van de brede weergave wordt weergegeven de [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element. Met behulp van dit element, kunt u de .NET-typenaam van het object, een selectieset objecten of een selectievoorwaarde waarmee wordt aangegeven wanneer de definitie wordt gebruikt. Zie voor meer informatie over het maken van een selectie voorwaarden [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door een specifieke definitie van de brede weergave:

- De [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de definitie.

- De [TypeName](./typename-element-for-viewselectedby-format.md) element Hiermee geeft u de .NET die wordt weergegeven door de definitie. Bij het gebruik van dit element is de volledig gekwalificeerde naam van de .NET-type is vereist. U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.

- De [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (niet weergegeven) Hiermee geeft u een set van objecten die kunnen worden weergegeven door deze definitie. U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.

- De [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (niet weergegeven) Hiermee geeft u een voorwaarde moet bestaan voor deze definitie moet worden gebruikt. U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven. Zie voor meer informatie over het definiëren van de voorwaarden van de selectie [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>Groepen van objecten weergeven in een brede weergave

U kunt de objecten die worden weergegeven door de brede weergave in groepen te scheiden. Dit betekent niet dat u een groep definieert, alleen of Windows PowerShell wordt een nieuwe groep gestart wanneer de waarde van een bepaalde eigenschap of script wijzigt. In het volgende voorbeeld wordt een nieuwe groep wordt gestart wanneer de waarde van de [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) wijzigingen in de eigenschappen.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

De volgende XML-elementen worden gebruikt om te definiëren wanneer een groep wordt gestart:

- De [GroupBy](./groupby-element-for-view-format.md) element wordt gedefinieerd voor de eigenschap of het script dat de nieuwe groep wordt gestart en wordt gedefinieerd hoe de groep wordt weergegeven.

- De [PropertyName](./propertyname-element-for-groupby-format.md) element Hiermee geeft u de eigenschap waarmee een nieuwe groep wordt gestart wanneer de waarde ervan verandert. U moet een eigenschap of het script voor het starten van de groep opgeven, maar u kunt niet beide opgeven.

- De [ScriptBlock](./scriptblock-element-for-groupby-format.md) element Hiermee geeft u het script dat een nieuwe groep wordt gestart wanneer de waarde ervan verandert. U moet een script of een eigenschap te starten van de groep opgeven, maar u kunt niet beide opgeven.

- De [Label](./label-element-for-groupby-format.md) element een label dat wordt weergegeven aan het begin van elke groep wordt gedefinieerd. Naast de tekst die is opgegeven door dit element, wordt de waarde die de nieuwe groep geactiveerd en wordt een lege regel toegevoegd voor en na het label weergegeven in Windows PowerShell. Dit element is optioneel.

- De [CustomControl](./customcontrol-element-for-groupby-format.md) element wordt gedefinieerd voor een besturingselement dat wordt gebruikt om de gegevens weer te geven. Dit element is optioneel.

- De [CustomControlName](./customcontrolname-element-for-groupby-format.md) element Hiermee geeft u een algemene of besturingselement dat wordt gebruikt om de gegevens weer te geven. Dit element is optioneel.

Zie voor een voorbeeld van een volledige opmaak bestand dat groepen worden gedefinieerd, [brede weergave (GroupBy)](./wide-view-groupby.md).

## <a name="using-format-strings"></a>Met behulp van opmaaktekenreeksen

Opmaak tekenreeksen kunnen worden toegevoegd aan een brede weergave om verder te definiëren hoe de gegevens worden weergegeven. Het volgende voorbeeld ziet u hoe u een opmaaktekenreeks voor de waarde van de `StartTime` eigenschap.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

De volgende XML-elementen kunnen worden gebruikt om op te geven van een patroon indeling:

- De [WideItem](./wideitem-element-for-widecontrol-format.md) element Hiermee geeft u de gegevens die worden weergegeven in de weergave.

- De [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element Hiermee geeft u de eigenschap waarvan de waarde wordt weergegeven in de weergave. U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.

- De [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script wordt weergegeven in de weergave

- De [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (niet weergegeven) Hiermee geeft u het script waarvan de waarde wordt weergegeven in de weergave. U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.

In het volgende voorbeeld wordt de `ToString` methode aangeroepen om de indeling van de waarde van het script. Scripts kunnen elke methode van een object aangeroepen. Dus als een object een methode, zoals heeft `ToString`, met parameters voor formatteren, het script dat methode voor de indeling van de uitvoerwaarde van het script kunt aanroepen.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

De volgende XML-element kan worden gebruikt voor aanroepen de `ToString` methode:

- De [WideItem](./wideitem-element-for-widecontrol-format.md) element Hiermee geeft u de gegevens die worden weergegeven in de weergave.

- De [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (niet weergegeven) Hiermee geeft u het script waarvan de waarde wordt weergegeven in de weergave. U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Brede weergave (basis)](./wide-view-basic.md)

[Brede weergave (GroupBy)](./wide-view-groupby.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
