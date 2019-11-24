---
title: Brede weer gave (basis) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358722"
---
# <a name="wide-view-basic"></a>Brede weergave (Basis)

In dit voor beeld ziet u hoe u een algemene weer gave implementeert waarin [System. ServiceProcess. servicecontroller wordt weer gegeven? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten die door de `Get-Service`-cmdlet worden geretourneerd. Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.

### <a name="to-load-this-formatting-file"></a>Dit indelings bestand laden

1. Kopieer de XML uit de sectie voor beeld van dit onderwerp naar een tekst bestand.

2. Sla het tekst bestand op. Zorg ervoor dat u de extensie `format.ps1xml` toevoegt aan het bestand om het te identificeren als een opmaak bestand.

3. Open Windows Power shell en voer de volgende opdracht uit om het opmaak bestand in de huidige sessie te laden: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Dit opmaak bestand definieert de weer gave van een object dat al is gedefinieerd door een Windows Power shell-indelings bestand. U moet de para meter `prependPath` gebruiken wanneer u de cmdlet uitvoert. u kunt dit indelings bestand niet laden als een module.

## <a name="demonstrates"></a>Laat zien

In dit opmaak bestand worden de volgende XML-elementen gedemonstreerd:

- Het [naam](./name-element-for-view-format.md) element voor de weer gave.

- Het [ViewSelectedBy](./viewselectedby-element-format.md) -element dat definieert welke objecten worden weer gegeven in de weer gave.

- Het [WideItem](./wideitem-element-for-widecontrol-format.md) -element waarmee wordt gedefinieerd welke eigenschap wordt weer gegeven in de weer gave.

## <a name="example"></a>Voorbeeld

De volgende XML definieert een brede weer gave waarin de waarde van de eigenschap [System. ServiceProcess. servicecontroller. ServiceName](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) wordt weer gegeven.

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
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
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a>Zie ook

[Voor beelden van het format teren van bestanden](./examples-of-formatting-files.md)

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
