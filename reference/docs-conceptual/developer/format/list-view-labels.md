---
ms.date: 09/13/2016
ms.topic: reference
title: Lijstweergave (Labels)
description: Lijstweergave (Labels)
ms.openlocfilehash: 2d341ae95d025e0f95b5d88b96afb846b62b092f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666685"
---
# <a name="list-view-labels"></a>Lijstweergave (Labels)

In dit voor beeld ziet u hoe u een lijst weergave implementeert waarin een aangepast label wordt weer gegeven voor elke rij van de lijst. In deze lijst weergave worden de eigenschappen van [System. ServiceProcess. servicecontroller weer gegeven? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -object dat wordt geretourneerd door de cmdlet [Get-service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) . Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over de onderdelen van een lijst weergave.

### <a name="to-load-this-formatting-file"></a>Dit indelings bestand laden

1. Kopieer de XML uit de sectie voor beeld van dit onderwerp naar een tekst bestand.

2. Sla het tekstbestand op. Zorg ervoor dat u de `format.ps1xml` extensie toevoegt aan het bestand om het te identificeren als een indelings bestand.

3. Open Windows Power shell en voer de volgende opdracht uit om het opmaak bestand in de huidige sessie te laden: `Update-formatdata -prependpath PathToFormattingFile` .

   > [!WARNING]
   > Dit opmaak bestand definieert de weer gave van een object dat al is gedefinieerd door een Windows Power shell-indelings bestand. U moet de `prependPath` para meter gebruiken bij het uitvoeren van de cmdlet en u kunt dit indelings bestand niet laden als een module.

## <a name="demonstrates"></a>Demonstreert

In dit opmaak bestand worden de volgende XML-elementen gedemonstreerd:

- Het [naam](./name-element-for-view-format.md) element voor de weer gave.

- Het [ViewSelectedBy](./viewselectedby-element-format.md) -element dat definieert welke objecten worden weer gegeven in de weer gave.

- Het element [ListControl](./listcontrol-element-format.md) dat definieert welke eigenschap wordt weer gegeven in de weer gave.

- Het [lijst item](./listitem-element-for-listitems-for-listcontrol-format.md) -element dat definieert wat wordt weer gegeven in een rij van de lijst weergave.

- Het [Label](./label-element-for-listitem-for-listcontrol-format.md) -element dat definieert wat wordt weer gegeven in een rij van de lijst weergave.

- Het element [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) waarmee wordt gedefinieerd welke eigenschap wordt weer gegeven.

## <a name="example"></a>Voorbeeld

De volgende XML definieert een lijst weergave waarin een aangepast label wordt weer gegeven in elke rij. In dit geval bevat het label de naam van de eigenschap met een hoofd letter en het woord "eigenschap". In elke rij wordt de naam van de eigenschap weer gegeven gevolgd door de waarde van de eigenschap.

```xml
<Configuration>
  <ViewDefinitions>
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
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>

  </ViewDefinitions>
</Configuration>
```

In het volgende voor beeld ziet u hoe de [System. ServiceProcess. servicecontroller wordt weer gegeven in Windows Power shell? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten nadat dit indelings bestand is geladen.

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a>Zie ook

[Voorbeelden van opmaakbestanden](./examples-of-formatting-files.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
