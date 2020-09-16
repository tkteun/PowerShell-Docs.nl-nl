---
title: Een lijst weergave maken | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 24eb673e0db011a1439fa5ba1f2966fcc3bdc338
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783769"
---
# <a name="creating-a-list-view"></a>Een lijstweergave maken

In een lijst weergave worden gegevens in één kolom weer gegeven (in sequentiële volg orde). De gegevens die in de lijst worden weer gegeven, kunnen de waarde van een .NET-eigenschap of de waarde van een script zijn.

## <a name="a-list-view-display"></a>Een lijst weergave weer geven

In de volgende uitvoer ziet u hoe de eigenschappen van [System. ServiceProcess. servicecontroller worden weer gegeven in Windows Power shell? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten die worden geretourneerd door de cmdlet [Get-service](/powershell/module/microsoft.powershell.management/get-service) . In dit voor beeld zijn er drie objecten geretourneerd, waarbij elk object is gescheiden van het voor gaande object door een lege regel.

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

## <a name="defining-the-list-view"></a>De lijst weergave definiëren

In het volgende XML-bestand wordt het lijst weergave schema weer gegeven voor het weer geven van verschillende eigenschappen van [System. ServiceProcess. servicecontroller? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -object. U moet elke eigenschap opgeven die u wilt weer geven in de lijst weergave.

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

De volgende XML-elementen worden gebruikt voor het definiëren van een lijst weergave:

- Het element [View](./view-element-format.md) is het bovenliggende element van de lijst weergave. (Dit is hetzelfde bovenliggende element voor de tabel-, brede en aangepaste besturings elementen.)

- Het element [name](./name-element-for-view-format.md) specificeert de naam van de weer gave. Dit element is vereist voor alle weer gaven.

- Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert de objecten die gebruikmaken van de weer gave. Dit element is vereist.

- Het element [GroupBy](./groupby-element-for-view-format.md) definieert wanneer een nieuwe groep objecten wordt weer gegeven. Er wordt een nieuwe groep gestart wanneer de waarde van een specifieke eigenschap of script wordt gewijzigd. Dit element is optioneel.

- Het element [Controls](./controls-element-for-view-format.md) definieert de aangepaste besturings elementen die door de lijst weergave worden gedefinieerd. Met besturings elementen kunt u nader aangeven hoe de gegevens worden weer gegeven. Dit element is optioneel. Een weer gave kan zijn eigen aangepaste besturings elementen definiëren, maar u kunt ook algemene besturings elementen gebruiken die kunnen worden gebruikt door elke weer gave in het opmaak bestand. Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over aangepaste besturings elementen.

- Het element [ListControl](./listcontrol-element-format.md) definieert wat wordt weer gegeven in de weer gave en hoe het is opgemaakt. Net als bij alle andere weer gaven kunnen in een lijst weergave de waarden van object eigenschappen of waarden worden weer gegeven die door het script worden gegenereerd.

Zie [lijst weergave (Basic)](./list-view-basic.md)voor een voor beeld van een volledig opmaak bestand dat een eenvoudige lijst weergave definieert.

## <a name="providing-definitions-for-your-list-view"></a>Definities opgeven voor de lijst weergave

Lijst Weergaven kunnen een of meer definities bieden met behulp van de onderliggende elementen van het element [ListControl](./listcontrol-element-format.md) . Normaal gesp roken bevat een weer gave slechts één definitie. In het volgende voor beeld bevat de weer gave één definitie waarin verschillende eigenschappen van het [systeem. Diagnostics. process worden weer gegeven? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) -object. Een lijst weergave kan de waarde van een eigenschap of de waarde van een script weer geven (niet weer gegeven in het voor beeld).

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

De volgende XML-elementen kunnen worden gebruikt om definities op te geven voor een lijst weergave:

- Het element [ListControl](./listcontrol-element-format.md) en de onderliggende elementen bepalen wat wordt weer gegeven in de weer gave.

- Het element [List entries](./listentries-element-for-listcontrol-format.md) bevat de definities van de weer gave. In de meeste gevallen heeft een weer gave slechts één definitie. Dit element is vereist.

- Het element [List entry](./listentry-element-for-listcontrol-format.md) bevat een definitie van de weer gave. Er is ten minste één [List entry](./listentry-element-for-listcontrol-format.md) vereist; Er is echter geen maximum limiet voor het aantal elementen dat u kunt toevoegen. In de meeste gevallen heeft een weer gave slechts één definitie.

- Het [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -element geeft de objecten aan die door een specifieke definitie worden weer gegeven. Dit element is optioneel en is alleen nodig wanneer u meerdere [List entry](./listentry-element-for-listcontrol-format.md) -elementen definieert waarin verschillende objecten worden weer gegeven.

- Het [list items](./listitems-element-for-listentry-for-listcontrol-format.md) -element geeft de eigenschappen en scripts op waarvan de waarden worden weer gegeven in de rijen van de lijst weergave.

- Het element [lijst item](./listitems-element-for-listentry-for-listcontrol-format.md) geeft een eigenschap of script op waarvan de waarde wordt weer gegeven in een rij van de lijst weergave. In een lijst weergave moet ten minste één eigenschap of script worden opgegeven. Er is geen maximum limiet voor het aantal rijen dat kan worden opgegeven.

- Met het element [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) wordt de eigenschap opgegeven waarvan de waarde wordt weer gegeven in de rij. U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.

- Het [script Block](./scriptblock-element-for-listitem-for-listcontrol-format.md) -element geeft het script op waarvan de waarde wordt weer gegeven in de rij. U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.

- Het [Label](./label-element-for-listitem-for-listcontrol-format.md) element geeft het label aan dat links van de eigenschap of script waarde in de rij wordt weer gegeven. Dit element is optioneel. Als er geen label is opgegeven, wordt de naam van de eigenschap of het script weer gegeven. Zie [lijst weergave (labels)](./list-view-labels.md)voor een volledig voor beeld.

- Het [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) -element geeft een voor waarde aan die moet bestaan om de rij weer te geven. Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het toevoegen van voor waarden aan de lijst weergave. Dit element is optioneel.

- Het element [formats Tring](./formatstring-element-for-listitem-for-listcontrol-format.md) geeft een patroon op dat wordt gebruikt om de waarde van de eigenschap of het script weer te geven. Dit element is optioneel.

Zie [lijst weergave (Basic)](./list-view-basic.md)voor een voor beeld van een volledig opmaak bestand dat een eenvoudige lijst weergave definieert.

## <a name="defining-the-objects-that-use-the-list-view"></a>De objecten definiëren die gebruikmaken van de lijst weergave

Er zijn twee manieren om te definiëren welke .NET-objecten gebruikmaken van de lijst weergave. U kunt het element [ViewSelectedBy](./viewselectedby-element-format.md) gebruiken om de objecten te definiëren die door alle definities van de weer gave kunnen worden weer gegeven, of u kunt het element [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) gebruiken om te definiëren welke objecten worden weer gegeven met een specifieke definitie van de weer gave. In de meeste gevallen heeft een weer gave slechts één definitie, waardoor objecten doorgaans worden gedefinieerd door het element [ViewSelectedBy](./viewselectedby-element-format.md) .

In het volgende voor beeld ziet u hoe u de objecten definieert die worden weer gegeven in de lijst weergave met behulp van de elementen [ViewSelectedBy](./viewselectedby-element-format.md) en [TypeName](./typename-element-for-viewselectedby-format.md) . Er is geen limiet voor het aantal [TypeName](./typename-element-for-viewselectedby-format.md) -elementen dat u kunt opgeven en de volg orde hiervan is niet belang rijk.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door de lijst weergave:

- Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert welke objecten worden weer gegeven in de lijst weergave.

- Het element [TypeName](./typename-element-for-viewselectedby-format.md) specificeert het .net-object dat wordt weer gegeven in de weer gave. De volledig gekwalificeerde .NET-type naam is vereist. U moet ten minste één type of selectieset voor de weer gave opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.

Zie [lijst weergave (Basic)](./list-view-basic.md)voor een voor beeld van een volledig indelings bestand.

In het volgende voor beeld worden de elementen [ViewSelectedBy](./viewselectedby-element-format.md) en [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) gebruikt. Gebruik selectie sets waar u een gerelateerde set objecten hebt die worden weer gegeven met behulp van meerdere weer gaven, zoals wanneer u een lijst weergave definieert en een tabel weergave voor dezelfde objecten. Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het maken van een selectie reeks.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door de lijst weergave:

- Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert welke objecten worden weer gegeven in de lijst weergave.

- Het [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -element geeft een set objecten op die door de weer gave kan worden weer gegeven. U moet ten minste één selectieset of type voor de weer gave opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.

In het volgende voor beeld ziet u hoe u de objecten definieert die worden weer gegeven met een specifieke definitie van de lijst weergave met behulp van het element [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) . Met dit element kunt u de .NET-type naam van het object, een selectieset van objecten of een selectie voorwaarde opgeven die opgeeft wanneer de definitie wordt gebruikt. Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het maken van een selectie voorwaarden.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door een specifieke definitie van de lijst weergave:

- Het [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -element definieert welke objecten worden weer gegeven door de definitie.

- Het element [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) specificeert het .net-object dat wordt weer gegeven door de definitie. Wanneer u dit element gebruikt, is de volledig gekwalificeerde .NET-type naam vereist. U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.

- Het [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) -element (niet weer gegeven) bevat een set objecten die kunnen worden weer gegeven door deze definitie. U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.

- Het element [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) (niet weer gegeven) bevat een voor waarde die voor deze definitie moet bestaan. U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven. Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het definiëren van selectie voorwaarden.

## <a name="displaying-groups-of-objects-in-a-list-view"></a>Groepen van objecten in een lijst weergave weer geven

U kunt de objecten die door de lijst weergave worden weer gegeven, scheiden in groepen. Dit betekent niet dat u een groep definieert, alleen dat Windows Power shell een nieuwe groep start wanneer de waarde van een specifieke eigenschap of script wordt gewijzigd. In het volgende voor beeld wordt een nieuwe groep gestart wanneer de waarde van de eigenschap [System. ServiceProcess. servicecontroller. service](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) type wordt gewijzigd.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

De volgende XML-elementen worden gebruikt om te definiëren wanneer een groep wordt gestart:

- Het element [GroupBy](./groupby-element-for-view-format.md) definieert de eigenschap of het script waarmee de nieuwe groep wordt gestart en definieert hoe de groep wordt weer gegeven.

- Met het element [PropertyName](./propertyname-element-for-groupby-format.md) wordt de eigenschap opgegeven waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd. U moet een eigenschap of script opgeven om de groep te starten, maar u kunt niet beide opgeven.

- Het [script Block](./scriptblock-element-for-groupby-format.md) -element geeft het script op waarmee een nieuwe groep wordt gestart wanneer de waarde ervan wordt gewijzigd. U moet een script of eigenschap opgeven om de groep te starten, maar u kunt niet beide opgeven.

- Het element [Label](./label-element-for-groupby-format.md) definieert een label dat aan het begin van elke groep wordt weer gegeven. Naast de tekst die door dit element is opgegeven, wordt in Windows Power shell de waarde weer gegeven die de nieuwe groep heeft geactiveerd en wordt een lege regel toegevoegd vóór en na het label. Dit element is optioneel.

- Het [CustomControl](./customcontrol-element-for-groupby-format.md) -element definieert een besturings element dat wordt gebruikt om de gegevens weer te geven. Dit element is optioneel.

- Het [CustomControlName](./customcontrolname-element-for-groupby-format.md) -element geeft een algemeen of weergave besturings element op dat wordt gebruikt om de gegevens weer te geven. Dit element is optioneel.

Zie [lijst weergave (GroupBy)](./list-view-groupby.md)voor een voor beeld van een volledig indelings bestand waarmee groepen worden gedefinieerd.

## <a name="using-format-strings"></a>Opmaak teken reeksen gebruiken

Opmaak teken reeksen kunnen worden toegevoegd aan een weer gave om te bepalen hoe de gegevens worden weer gegeven. In het volgende voor beeld ziet u hoe u een opmaak teken reeks definieert voor de waarde van de `StartTime` eigenschap.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

De volgende XML-elementen kunnen worden gebruikt om een notatie patroon op te geven:

- Het element [lijst item](./listitem-element-for-listitems-for-listcontrol-format.md) geeft de gegevens aan die worden weer gegeven in de weer gave.

- Met het element [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) wordt de eigenschap opgegeven waarvan de waarde wordt weer gegeven in de weer gave. U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.

- Het element [formats Tring](./formatstring-element-for-listitem-for-listcontrol-format.md) geeft een opmaak patroon op dat bepaalt hoe de eigenschap of script waarde wordt weer gegeven in de weer gave.

- Het element [script Block](./scriptblock-element-for-listitem-for-listcontrol-format.md) (niet weer gegeven) Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de weer gave. U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.

In het volgende voor beeld wordt de- `ToString` methode aangeroepen om de waarde van het script op te maken. Scripts kunnen een wille keurige methode van een object aanroepen. Als een object een methode heeft, zoals `ToString` die opmaak parameters heeft, kan het script deze methode ook aanroepen om de uitvoer waarde van het script op te maken.

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

Het volgende XML-element kan worden gebruikt om de methode aan te roepen `ToString` :

- Het element [lijst item](./listitem-element-for-listitems-for-listcontrol-format.md) geeft de gegevens aan die worden weer gegeven in de weer gave.

- Het element [script Block](./scriptblock-element-for-listitem-for-listcontrol-format.md) (niet weer gegeven) Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de weer gave. U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-cmdlet schrijven](../cmdlet/writing-a-windows-powershell-cmdlet.md)
