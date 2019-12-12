---
title: Een brede weer gave maken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359075"
---
# <a name="creating-a-wide-view"></a>Een brede weergave maken

In een brede weer gave wordt één waarde weer gegeven voor elk object dat wordt weer gegeven. De weer gegeven waarde kan de waarde van een .NET-object eigenschap of de waarde van een script zijn. Standaard is er geen label of kop voor deze weer gave.

## <a name="a-wide-view-display"></a>Een brede weer gave

In het volgende voor beeld ziet u hoe in Windows Power shell het [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -object wordt weer gegeven dat wordt geretourneerd door de cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) wanneer de uitvoer wordt gepiped naar de [indeling-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet. (De cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) retourneert standaard een tabel weergave.) In dit voor beeld worden de twee kolommen gebruikt om de naam van het proces voor elk geretourneerd object weer te geven. De naam van de eigenschap van het object wordt niet weer gegeven, alleen de waarde van de eigenschap.

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

## <a name="defining-the-wide-view"></a>De brede weer gave definiëren

De volgende XML-code toont het breedste weergave schema voor het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .

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

De volgende XML-elementen worden gebruikt voor het definiëren van een brede weer gave:

- Het element [View](./view-element-format.md) is het bovenliggende element van de brede weer gave. (Dit is hetzelfde bovenliggende element voor de tabel-, lijst-en aangepaste besturings elementen.)

- Het element [name](./name-element-for-view-format.md) specificeert de naam van de weer gave. Dit element is vereist voor alle weer gaven.

- Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert de objecten die gebruikmaken van de weer gave. Dit element is vereist.

- Het element [GroupBy](./groupby-element-for-view-format.md) definieert wanneer een nieuwe groep objecten wordt weer gegeven. Er wordt een nieuwe groep gestart wanneer de waarde van een specifieke eigenschap of script wordt gewijzigd. Dit element is optioneel.

- De elementen [Controls](./controls-element-for-view-format.md) definieert de aangepaste besturings elementen die worden gedefinieerd door de brede weer gave. Met besturings elementen kunt u nader aangeven hoe de gegevens worden weer gegeven. Dit element is optioneel. Een weer gave kan zijn eigen aangepaste besturings elementen definiëren, maar u kunt ook algemene besturings elementen gebruiken die kunnen worden gebruikt door elke weer gave in het opmaak bestand. Zie [aangepaste besturings elementen maken](./creating-custom-controls.md)voor meer informatie over aangepaste besturings elementen.

- Het [WideControl](./widecontrol-element-format.md) -element en de onderliggende elementen bepalen wat er in de weer gave wordt weer gegeven. In het voor gaande voor beeld is de weer gave ontworpen om de eigenschap [System. Diagnostics. process. Autoprocesnaam](/dotnet/api/System.Diagnostics.Process.ProcessName) weer te geven.

Zie [Wide View (Basic)](./wide-view-basic.md)voor een voor beeld van een compleet opmaak bestand dat een eenvoudige, brede weer gave definieert.

## <a name="providing-definitions-for-your-wide-view"></a>Definities opgeven voor de brede weer gave

Breedbeeld weergaven kunnen een of meer definities bieden met behulp van de onderliggende elementen van het element [WideControl](./widecontrol-element-format.md) . Normaal gesp roken bevat een weer gave slechts één definitie. In het volgende voor beeld bevat de weer gave één definitie waarmee de waarde van de eigenschap [System. Diagnostics. process. Autoprocesnaam](/dotnet/api/System.Diagnostics.Process.ProcessName) wordt weer gegeven. Een brede weer gave kan de waarde van een eigenschap of de waarde van een script weer geven (niet weer gegeven in het voor beeld).

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

De volgende XML-elementen kunnen worden gebruikt om definities te bieden voor een brede weer gave:

- Het [WideControl](./widecontrol-element-format.md) -element en de onderliggende elementen bepalen wat er in de weer gave wordt weer gegeven.

- Het element [AutoSize](./autosize-element-for-widecontrol-format.md) geeft aan of de kolom grootte en het aantal kolommen worden aangepast op basis van de grootte van de gegevens. Dit element is optioneel.

- Het [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) -element geeft het aantal kolommen op dat wordt weer gegeven in de brede weer gave. Dit element is optioneel.

- Het [WideEntries](./wideentries-element-for-widecontrol-format.md) -element bevat de definities van de weer gave. In de meeste gevallen heeft een weer gave slechts één definitie. Dit element is vereist.

- Het [WideEntry](./wideentry-element-for-widecontrol-format.md) -element bevat een definitie van de weer gave. Er is ten minste één [WideEntry](./wideentry-element-for-widecontrol-format.md) vereist. Er is echter geen maximum limiet voor het aantal elementen dat u kunt toevoegen. In de meeste gevallen heeft een weer gave slechts één definitie.

- Het [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) -element geeft de objecten aan die door een specifieke definitie worden weer gegeven. Dit element is optioneel en is alleen nodig wanneer u meerdere [WideEntry](./wideentry-element-for-widecontrol-format.md) -elementen definieert waarin verschillende objecten worden weer gegeven.

- Het element [WideItem](./wideitem-element-for-widecontrol-format.md) geeft de gegevens aan die worden weer gegeven in de weer gave. In tegens telling tot andere soorten weer gaven, kan een breed besturings element slechts één item weer geven.

- Met het element [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) wordt de eigenschap opgegeven waarvan de waarde wordt weer gegeven in de weer gave. U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.

- Het [script Block](./scriptblock-element-for-wideitem-for-widecontrol-format.md) -element geeft het script op waarvan de waarde wordt weer gegeven in de weer gave. U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.

- Het element [formats Tring](./formatstring-element-for-wideitem-for-widecontrol-format.md) geeft een patroon op dat wordt gebruikt om de gegevens weer te geven. Dit element is optioneel.

Zie [Wide View (Basic)](./wide-view-basic.md)voor een voor beeld van een volledige indelings bestand waarin een brede weergave definitie is gedefinieerd.

## <a name="defining-the-objects-that-use-the-wide-view"></a>De objecten definiëren die gebruikmaken van de brede weer gave

Er zijn twee manieren om te definiëren welke .NET-objecten gebruikmaken van de brede weer gave. U kunt het element [ViewSelectedBy](./viewselectedby-element-format.md) gebruiken om de objecten te definiëren die door alle definities van de weer gave kunnen worden weer gegeven, of u kunt het element [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) gebruiken om te definiëren welke objecten worden weer gegeven met een specifieke definitie van de weer gave. In de meeste gevallen heeft een weer gave slechts één definitie, waardoor objecten doorgaans worden gedefinieerd door het element [ViewSelectedBy](./viewselectedby-element-format.md) .

In het volgende voor beeld ziet u hoe u de objecten definieert die door de brede weer gave worden weer gegeven met behulp van de elementen [ViewSelectedBy](./viewselectedby-element-format.md) en [TypeName](./typename-element-for-viewselectedby-format.md) . Er is geen limiet voor het aantal [TypeName](./typename-element-for-viewselectedby-format.md) -elementen dat u kunt opgeven en de volg orde hiervan is niet belang rijk.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door de brede weer gave:

- Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert welke objecten worden weer gegeven door de brede weer gave.

- Het element [TypeName](./typename-element-for-viewselectedby-format.md) specificeert de .net die wordt weer gegeven in de weer gave. De volledig gekwalificeerde .NET-type naam is vereist. U moet ten minste één type of selectieset voor de weer gave opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.

Zie [Wide View (Basic)](./wide-view-basic.md)voor een voor beeld van een volledig indelings bestand.

In het volgende voor beeld worden de elementen [ViewSelectedBy](./viewselectedby-element-format.md) en [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) gebruikt. Gebruik selectie sets waar u een gerelateerde set objecten hebt die met meerdere weer gaven worden weer gegeven, zoals wanneer u een brede weer gave en een tabel weergave voor dezelfde objecten definieert. Zie [selectie sets definiëren](./defining-selection-sets.md)voor meer informatie over het maken van een selectie reeks.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door de brede weer gave:

- Het [ViewSelectedBy](./viewselectedby-element-format.md) -element definieert welke objecten worden weer gegeven door de brede weer gave.

- Het [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -element geeft een set objecten op die door de weer gave kan worden weer gegeven. U moet ten minste één selectieset of type voor de weer gave opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.

In het volgende voor beeld ziet u hoe u de objecten definieert die worden weer gegeven met een specifieke definitie van de brede weer gave met behulp van het element [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) . Met dit element kunt u de .NET-type naam van het object, een selectieset van objecten of een selectie voorwaarde opgeven die opgeeft wanneer de definitie wordt gebruikt. Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het maken van een selectie voorwaarden.

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

De volgende XML-elementen kunnen worden gebruikt om de objecten op te geven die worden gebruikt door een specifieke definitie van de brede weer gave:

- Het [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) -element definieert welke objecten worden weer gegeven door de definitie.

- Het element [TypeName](./typename-element-for-viewselectedby-format.md) specificeert de .net die wordt weer gegeven in de definitie. Wanneer u dit element gebruikt, is de volledig gekwalificeerde .NET-type naam vereist. U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.

- Het [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) -element (niet weer gegeven) bevat een set objecten die kunnen worden weer gegeven door deze definitie. U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven.

- Het element [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) (niet weer gegeven) bevat een voor waarde die voor deze definitie moet bestaan. U moet ten minste één type, selectieset of selectie voorwaarde voor de definitie opgeven, maar er is geen maximum aantal elementen dat kan worden opgegeven. Zie voor [waarden definiëren voor het weer geven van gegevens](./defining-conditions-for-displaying-data.md)voor meer informatie over het definiëren van selectie voorwaarden.

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>Groepen objecten weer geven in een brede weer gave

U kunt de objecten die worden weer gegeven door de brede weer gave, scheiden in groepen. Dit betekent niet dat u een groep definieert, alleen dat Windows Power shell een nieuwe groep start wanneer de waarde van een specifieke eigenschap of script wordt gewijzigd. In het volgende voor beeld wordt een nieuwe groep gestart wanneer de waarde van de eigenschap [System. ServiceProcess. servicecontroller. service](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) type wordt gewijzigd.

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

Zie [Wide View (GroupBy)](./wide-view-groupby.md)voor een voor beeld van een volledig indelings bestand waarmee groepen worden gedefinieerd.

## <a name="using-format-strings"></a>Opmaak teken reeksen gebruiken

Opmaak teken reeksen kunnen worden toegevoegd aan een brede weer gave om te bepalen hoe de gegevens worden weer gegeven. In het volgende voor beeld ziet u hoe u een opmaak teken reeks definieert voor de waarde van de eigenschap `StartTime`.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

De volgende XML-elementen kunnen worden gebruikt om een notatie patroon op te geven:

- Het element [WideItem](./wideitem-element-for-widecontrol-format.md) geeft de gegevens aan die worden weer gegeven in de weer gave.

- Met het element [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) wordt de eigenschap opgegeven waarvan de waarde wordt weer gegeven in de weer gave. U moet een eigenschap of een script opgeven, maar u kunt niet beide opgeven.

- Het element [formats Tring](./formatstring-element-for-wideitem-for-widecontrol-format.md) geeft een opmaak patroon op dat bepaalt hoe de eigenschap of script waarde wordt weer gegeven in de weer gave

- Het element [script Block](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (niet weer gegeven) Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de weer gave. U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.

In het volgende voor beeld wordt de methode `ToString` aangeroepen om de waarde van het script op te maken. Scripts kunnen een wille keurige methode van een object aanroepen. Als een object een methode heeft, zoals `ToString`, die opmaak parameters heeft, kan het script deze methode ook aanroepen om de uitvoer waarde van het script op te maken.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

Het volgende XML-element kan worden gebruikt om de `ToString` methode aan te roepen:

- Het element [WideItem](./wideitem-element-for-widecontrol-format.md) geeft de gegevens aan die worden weer gegeven in de weer gave.

- Het element [script Block](./scriptblock-element-for-wideitem-for-widecontrol-format.md) (niet weer gegeven) Hiermee geeft u het script op waarvan de waarde wordt weer gegeven in de weer gave. U moet een script of een eigenschap opgeven, maar u kunt niet beide opgeven.

## <a name="see-also"></a>Zie ook

[Brede weer gave (basis)](./wide-view-basic.md)

[Brede weer gave (GroupBy)](./wide-view-groupby.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
