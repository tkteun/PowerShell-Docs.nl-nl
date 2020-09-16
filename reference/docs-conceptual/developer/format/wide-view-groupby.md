---
title: Brede weer gave (GroupBy) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e53714f0b4240b5fe7f62cccda83af1e5badd33c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784993"
---
# <a name="wide-view-groupby"></a>Brede weergave (GroupBy)

In dit voor beeld ziet u hoe u een brede weer gave implementeert waarin groepen [System. ServiceProcess. servicecontroller worden weer gegeven? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten die door de `Get-Service` cmdlet worden geretourneerd. Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.

### <a name="to-load-this-formatting-file"></a>Dit indelings bestand laden

1. Kopieer de XML uit de sectie voor beeld van dit onderwerp naar een tekst bestand.

2. Sla het tekstbestand op. Zorg ervoor dat u de `format.ps1xml` extensie toevoegt aan het bestand om het te identificeren als een indelings bestand.

3. Open Windows Power shell en voer de volgende opdracht uit om het opmaak bestand in de huidige sessie te laden: `Update-formatdata -prependpath PathToFormattingFile` .

   > [!WARNING]
   > Dit opmaak bestand definieert de weer gave van een object dat al is gedefinieerd door een Windows Power shell-indelings bestanden. U moet de `prependPath` para meter gebruiken bij het uitvoeren van de cmdlet en u kunt dit indelings bestand niet laden als een module.

## <a name="demonstrates"></a>Demonstreert

In dit opmaak bestand worden de volgende XML-elementen gedemonstreerd:

- Het [naam](./name-element-for-view-format.md) element voor de weer gave.

- Het [ViewSelectedBy](./viewselectedby-element-format.md) -element dat definieert welke objecten worden weer gegeven in de weer gave.

- Het element [GroupBy](./groupby-element-for-view-format.md) dat definieert wanneer een nieuwe groep wordt weer gegeven.

- Het [WideItem](./wideitem-element-for-widecontrol-format.md) -element waarmee wordt gedefinieerd welke eigenschap wordt weer gegeven in de weer gave.

## <a name="example"></a>Voorbeeld

De volgende XML definieert een brede weer gave waarin groepen objecten worden weer gegeven. Elke nieuwe groep wordt gestart wanneer de waarde van de eigenschap [System. ServiceProcess. servicecontroller. service](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) type wordt gewijzigd.

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

In het volgende voor beeld ziet u hoe de [System. ServiceProcess. servicecontroller wordt weer gegeven in Windows Power shell? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten nadat dit indelings bestand is geladen.

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a>Zie ook

[Voorbeelden van opmaakbestanden](./examples-of-formatting-files.md)

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
