---
title: Brede weergave (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083651"
---
# <a name="wide-view-groupby"></a>Brede weergave (GroupBy)

Dit voorbeeld laat zien hoe u een brede weergave met beveiligingsgroepen van implementeert [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten die worden geretourneerd door de `Get-Service` cmdlet. Zie voor meer informatie over de onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).

### <a name="to-load-this-formatting-file"></a>Deze opmaak bestand laden

1. Kopieer het XML-bestand van de voorbeeld-sectie van dit onderwerp in een tekstbestand.

2. Bewaar het tekstbestand. Zorg ervoor dat om toe te voegen de `format.ps1xml` uitbreiding van het bestand om het te identificeren als een opmaak-bestand.

3. Open Windows PowerShell en voer de volgende opdracht om de opmaak bestand laden in de huidige sessie: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Deze opmaak bestand definieert de weergave van een object dat al is gedefinieerd door een Windows PowerShell opmaak van bestanden. Moet u de `prependPath` parameter wanneer u de cmdlet uitvoert, en deze opmaak kan niet worden geladen als een module-bestand.

## <a name="demonstrates"></a>Ziet u

Deze opmaak bestand ziet u de volgende XML-elementen:

- De [naam](./name-element-for-view-format.md) -element voor de weergave.

- De [ViewSelectedBy](./viewselectedby-element-format.md) element waarmee wordt gedefinieerd welke objecten worden weergegeven in de weergave.

- De [GroupBy](./groupby-element-for-view-format.md) element waarmee wordt gedefinieerd wanneer een nieuwe groep wordt weergegeven.

- De [WideItem](./wideitem-element-for-widecontrol-format.md) element waarmee wordt gedefinieerd welke eigenschap van de weergave wordt weergegeven.

## <a name="example"></a>Voorbeeld

Het volgende XML-bestand definieert een brede weergave waarin te zien van groepen objecten. Elke nieuwe groep wordt gestart wanneer de waarde van de [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) wijzigingen in de eigenschappen.

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

Het volgende voorbeeld laat zien hoe de Windows PowerShell wordt weergegeven de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten na het laden van deze bestandsindeling.

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

[Voorbeelden van opmaak bestanden](./examples-of-formatting-files.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
