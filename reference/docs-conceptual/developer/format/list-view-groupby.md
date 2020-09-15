---
title: Lijst weergave (GroupBy) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7956d13e196454a3f6da185e9be74f9d3cb8ef63
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773399"
---
# <a name="list-view-groupby"></a>Lijstweergave (GroupBy)

In dit voor beeld ziet u hoe u een lijst weergave implementeert waarmee de rijen van de lijst worden gescheiden in groepen. In deze lijst weergave worden de eigenschappen van [System. ServiceProcess. servicecontroller weer gegeven? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten die door de [Get-service-](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet worden geretourneerd. Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over de onderdelen van een lijst weergave.

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

- Het element [GroupBy](./viewselectedby-element-format.md) dat definieert hoe een nieuwe groep objecten wordt weer gegeven.

- Het element [ListControl](./listcontrol-element-format.md) dat definieert welke eigenschap wordt weer gegeven in de weer gave.

- Het [lijst item](./listitem-element-for-listitems-for-listcontrol-format.md) -element dat definieert wat wordt weer gegeven in een rij van de lijst weergave.

- Het element [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) waarmee wordt gedefinieerd welke eigenschap wordt weer gegeven.

## <a name="example"></a>Voorbeeld

De volgende XML definieert een lijst weergave waarmee een nieuwe groep wordt gestart wanneer de waarde van de eigenschap [System. ServiceProcess. servicecontroller. status](/dotnet/api/System.ServiceProcess.ServiceController.Status) wordt gewijzigd. Wanneer elke groep wordt gestart, wordt een aangepast label weer gegeven met daarin de nieuwe waarde van de eigenschap.

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
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

In het volgende voor beeld ziet u hoe de [System. ServiceProcess. servicecontroller wordt weer gegeven in Windows Power shell? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten nadat dit indelings bestand is geladen. De lege regels die voor en na het groeps label worden toegevoegd, worden automatisch toegevoegd door Windows Power shell.

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a>Zie ook

[Voorbeelden van opmaakbestanden](./examples-of-formatting-files.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
