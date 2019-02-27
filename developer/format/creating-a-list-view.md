---
title: Het maken van een lijst weergeven | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850713"
---
# <a name="creating-a-list-view"></a>Een lijstweergave maken

Een lijstweergave geeft gegevens weer in één kolom (in opeenvolgende volgorde). De gegevens die worden weergegeven in de lijst is de waarde van een eigenschap .NET of de waarde van een script.

## <a name="a-list-view-display"></a>Een lijst met weergave worden weergegeven

De volgende uitvoer ziet u hoe Windows PowerShell worden weergegeven in de eigenschappen van [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten die worden geretourneerd door de [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. In dit voorbeeld drie objecten zijn opgehaald, met elk object van het voorgaande object gescheiden door een lege regel.

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a>De lijstweergave definiëren

Het volgende XML-bestand bevat de lijst met weergave-schema voor het weergeven van verschillende eigenschappen van de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object. U moet elke eigenschap die u weergeven in de lijstweergave wilt.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

De volgende XML-elementen worden gebruikt voor het definiëren van een lijst weergeven:

- De [weergave](./view-element-format.md) -element is het bovenliggende element van de lijstweergave. (Dit is hetzelfde bovenliggende element voor de tabel, breed en aangepaste weergaven.)

- De [naam](./name-element-for-view-format.md) element Hiermee geeft u de naam van de weergave. Dit element is vereist voor alle weergaven.

- De [ViewSelectedBy](./viewselectedby-element-format.md) element definieert de objecten die gebruikmaken van de weergave. Dit element is vereist.

- De [GroupBy](./groupby-element-for-view-format.md) element wordt gedefinieerd wanneer een nieuwe groep objecten wordt weergegeven. Een nieuwe groep wordt gestart wanneer de waarde van een bepaalde eigenschap of script wijzigt. Dit element is optioneel.

- De [besturingselementen](./controls-element-for-view-format.md) element wordt gedefinieerd voor de aangepaste besturingselementen die zijn gedefinieerd door de lijstweergave. Besturingselementen kunnen u nader aangeven hoe de gegevens worden weergegeven. Dit element is optioneel. Een weergave een eigen aangepaste besturingselementen kunt definiëren of deze algemene besturingselementen die kunnen worden gebruikt door elke weergave in de opmaak-bestand kunt gebruiken. Zie voor meer informatie over aangepaste besturingselementen [het maken van aangepaste besturingselementen](./creating-custom-controls.md).

- De [ListControl](./listcontrol-element-format.md) element wordt gedefinieerd wat wordt weergegeven in de weergave en hoe dit wordt geformatteerd. Net als bij alle andere weergaven, een lijst met weergave kan de waarden van eigenschappen van het object of de waarden die worden gegenereerd door het script.

Zie voor een voorbeeld van een volledige opmaak bestand dat een eenvoudige lijstweergave definieert [lijstweergave (basis)](./list-view-basic.md).

## <a name="providing-definitions-for-your-list-view"></a>Definities voor de weergave te bieden

Lijstweergaven kunnen een of meer netwerkdefinities opgeven met behulp van de onderliggende elementen van de [ListControl](./listcontrol-element-format.md) element. Een weergave wordt meestal slechts één definitie hebben. In het volgende voorbeeld wordt de weergave bevat één definitie die verschillende van eigenschappen de [System.Diagnostics.Process? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) object. Een lijst met weergave kan de waarde van een eigenschap of de waarde van een script (niet weergegeven in het voorbeeld).

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

De volgende XML-elementen kunnen worden gebruikt voor definities voor een lijst weergeven:

- De [ListControl](./listcontrol-element-format.md) -element en de onderliggende elementen definiëren wat wordt weergegeven in de weergave.

- De [ListEntries](./listentries-element-for-listcontrol-format.md) element bevat de definities van de weergave. In de meeste gevallen wordt een weergave slechts één definitie hebben. Dit element is vereist.

- De [ListEntry](./listentry-element-for-listcontrol-format.md) -element bevat een definitie van de weergave. Ten minste één [ListEntry](./listentry-element-for-listcontrol-format.md) is vereist; er is echter geen maximale limiet voor het aantal elementen die u kunt toevoegen. In de meeste gevallen wordt een weergave slechts één definitie hebben.

- De [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element Hiermee geeft u de objecten die worden weergegeven door de definitie van een specifieke. Dit element is optioneel en is alleen nodig wanneer u meerdere definiëren [ListEntry](./listentry-element-for-listcontrol-format.md) elementen die verschillende objecten worden weergegeven.

- De [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element Hiermee geeft u de eigenschappen en -scripts waarvan de waarden worden weergegeven in de rijen van de lijstweergave.

- De [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element Hiermee geeft u een eigenschap of een script waarvan de waarde wordt weergegeven in een rij in de lijstweergave. Een lijst weergeven moet ten minste één eigenschap of script opgeven. Er is geen maximale limiet voor het aantal rijen dat kan worden opgegeven.

- De [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u de eigenschap waarvan de waarde wordt weergegeven in de rij. U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.

- De [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u het script waarvan de waarde wordt weergegeven in de rij. U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.

- De [Label](./label-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u het label dat wordt weergegeven aan de linkerkant van de waarde voor eigenschap of het script in de rij. Dit element is optioneel. Als een label niet opgegeven is, wordt de naam van de eigenschap of het script wordt weergegeven. Zie voor een compleet voorbeeld [lijstweergave (Labels)](./list-view-labels.md).

- De [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u een voorwaarde die moet aanwezig zijn voor de rij moet worden weergegeven. Zie voor meer informatie over het toevoegen van voorwaarden aan de lijstweergave [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md). Dit element is optioneel.

- De [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u een patroon dat wordt gebruikt om de waarde van de eigenschap of het script weer te geven. Dit element is optioneel.

Zie voor een voorbeeld van een volledige opmaak bestand dat een eenvoudige lijstweergave definieert [lijstweergave (basis)](./list-view-basic.md).

## <a name="defining-the-objects-that-use-the-list-view"></a>Definieert de objecten die gebruikmaken van de lijstweergave

Er zijn twee manieren om te definiëren welke .NET-objecten worden gebruikt in de lijstweergave. U kunt de [ViewSelectedBy](./viewselectedby-element-format.md) element voor het definiëren van de objecten die kunnen worden weergegeven door de definities van de weergave, of u kunt de [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element te definiëren welke objecten worden weergegeven door een de definitie van de weergave van specifieke. In de meeste gevallen een weergave heeft slechts één definitie zodat objecten worden gewoonlijk gedefinieerd door de [ViewSelectedBy](./viewselectedby-element-format.md) element.

Het volgende voorbeeld ziet u hoe u de objecten die worden weergegeven door de lijst weergeven met behulp van de [ViewSelectedBy](./viewselectedby-element-format.md) en [TypeName](./typename-element-for-viewselectedby-format.md) elementen. Er is geen limiet voor het aantal [TypeName](./typename-element-for-viewselectedby-format.md) elementen dat u opgeven kunt en de volgorde niet belangrijk is.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door de lijstweergave:

- De [ViewSelectedBy](./viewselectedby-element-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de lijstweergave.

- De [TypeName](./typename-element-for-viewselectedby-format.md) element Hiermee geeft u de .NET-object dat door de weergave wordt weergegeven. De volledig gekwalificeerde naam van de .NET-type is vereist. U moet ten minste één type of de selectie instellen voor de weergave opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.

Zie voor een voorbeeld van een volledige opmaak bestand [lijstweergave (basis)](./list-view-basic.md).

Het volgende voorbeeld wordt de [ViewSelectedBy](./viewselectedby-element-format.md) en [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elementen. Gebruik selectie wordt ingesteld wanneer er een gerelateerde set van objecten die worden weergegeven met behulp van meerdere weergaven, zoals wanneer u een lijst weergeven en een tabelweergave voor dezelfde objecten definiëren. Zie voor meer informatie over het maken van een selectieset [selectiesets definiëren](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door de lijstweergave:

- De [ViewSelectedBy](./viewselectedby-element-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de lijstweergave.

- De [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element Hiermee geeft u een set van objecten die kunnen worden weergegeven in de weergave. U moet ten minste één selectie instellen of type voor de weergave opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.

Het volgende voorbeeld ziet u hoe u de objecten weergegeven door een specifieke definitie van de lijst weergeven met behulp van de [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element. Met behulp van dit element, kunt u de .NET-typenaam van het object, een selectieset objecten of een selectievoorwaarde waarmee wordt aangegeven wanneer de definitie wordt gebruikt. Zie voor meer informatie over het maken van een selectie voorwaarden [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

De volgende XML-elementen kunnen worden gebruikt om op te geven van de objecten die worden gebruikt door een specifieke definitie van de lijstweergave:

- De [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element wordt gedefinieerd welke objecten worden weergegeven door de definitie.

- De [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element Hiermee geeft u de .NET-object dat door de definitie wordt weergegeven. Wanneer u dit element gebruikt, is de volledig gekwalificeerde naam van de .NET-type is vereist. U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.

- De [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (niet weergegeven) Hiermee geeft u een set van objecten die kunnen worden weergegeven door deze definitie. U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven.

- De [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (niet weergegeven) Hiermee geeft u een voorwaarde moet bestaan voor deze definitie moet worden gebruikt. U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van de opgeven, maar er is geen maximum aantal elementen die kunnen worden opgegeven. Zie voor meer informatie over het definiëren van de voorwaarden van de selectie [voorwaarden definiëren voor het weergeven van gegevens](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-list-view"></a>Groepen of objecten weergeven in een lijst weergeven

U kunt de objecten die worden weergegeven door de lijstweergave in groepen te scheiden. Dit betekent niet dat u een groep definieert, alleen of Windows PowerShell wordt een nieuwe groep gestart wanneer de waarde van een bepaalde eigenschap of script wijzigt. In het volgende voorbeeld wordt een nieuwe groep wordt gestart wanneer de waarde van de [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) wijzigingen in de eigenschappen.

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

Zie voor een voorbeeld van een volledige opmaak bestand dat groepen worden gedefinieerd, [lijstweergave (GroupBy)](./list-view-groupby.md).

## <a name="using-format-strings"></a>Met behulp van opmaaktekenreeksen

Opmaak tekenreeksen kunnen worden toegevoegd aan een weergave om verder te definiëren hoe de gegevens worden weergegeven. Het volgende voorbeeld ziet u hoe u een opmaaktekenreeks voor de waarde van de `StartTime` eigenschap.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

De volgende XML-elementen kunnen worden gebruikt om op te geven van een patroon indeling:

- De [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element Hiermee geeft u de gegevens die worden weergegeven in de weergave.

- De [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u de eigenschap waarvan de waarde wordt weergegeven in de weergave. U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.

- De [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element Hiermee geeft u een indeling patroon waarmee wordt gedefinieerd hoe de waarde voor eigenschap of het script wordt weergegeven in de weergave.

- De [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (niet weergegeven) Hiermee geeft u het script waarvan de waarde wordt weergegeven in de weergave. U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.

In het volgende voorbeeld wordt de `ToString` methode aangeroepen om de indeling van de waarde van het script. Scripts kunnen elke methode van een object aangeroepen. Dus als een object een methode, zoals heeft `ToString`, met parameters voor formatteren, het script dat methode voor de indeling van de uitvoerwaarde van het script kunt aanroepen.

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

De volgende XML-element kan worden gebruikt voor aanroepen de `ToString` methode:

- De [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element Hiermee geeft u de gegevens die worden weergegeven in de weergave.

- De [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (niet weergegeven) Hiermee geeft u het script waarvan de waarde wordt weergegeven in de weergave. U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)
