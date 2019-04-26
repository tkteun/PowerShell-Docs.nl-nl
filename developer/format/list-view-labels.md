---
title: Lijstweergave (Labels) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 27de41c88e224f7610c10a764e51524016ecc8cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065271"
---
# <a name="list-view-labels"></a>Lijstweergave (Labels)

In dit voorbeeld laat zien hoe voor het implementeren van een lijstweergave met een aangepaste label voor elke rij van de lijst weergegeven. In deze lijstweergave geeft de eigenschappen van de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object dat wordt geretourneerd door de [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet. Zie voor meer informatie over de onderdelen van een lijst weergeven, [het maken van een lijstweergave](./creating-a-list-view.md).

### <a name="to-load-this-formatting-file"></a>Deze opmaak bestand laden

1. Kopieer het XML-bestand van de voorbeeld-sectie van dit onderwerp in een tekstbestand.

2. Bewaar het tekstbestand. Zorg ervoor dat om toe te voegen de `format.ps1xml` uitbreiding van het bestand om het te identificeren als een opmaak-bestand.

3. Open Windows PowerShell en voer de volgende opdracht om de opmaak bestand laden in de huidige sessie: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Deze opmaak bestand definieert de weergave van een object dat al is gedefinieerd door een bestand van Windows PowerShell-opmaak. Moet u de `prependPath` parameter wanneer u de cmdlet uitvoert, en deze opmaak kan niet worden geladen als een module-bestand.

## <a name="demonstrates"></a>Ziet u

Deze opmaak bestand ziet u de volgende XML-elementen:

- De [naam](./name-element-for-view-format.md) -element voor de weergave.

- De [ViewSelectedBy](./viewselectedby-element-format.md) element waarmee wordt gedefinieerd welke objecten worden weergegeven in de weergave.

- De [ListControl](./listcontrol-element-format.md) element waarmee wordt gedefinieerd welke eigenschap van de weergave wordt weergegeven.

- De [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element die definieert wat wordt weergegeven in een rij in de lijstweergave.

- De [Label](./label-element-for-listitem-for-listcontrol-format.md) element die definieert wat wordt weergegeven in een rij in de lijstweergave.

- De [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element waarmee wordt gedefinieerd welke eigenschap wordt weergegeven.

## <a name="example"></a>Voorbeeld

Het volgende XML-bestand definieert een lijstweergave met een aangepaste label in elke rij weergegeven. In dit geval wordt het label bevat de naam van de eigenschap met alle letters in hoofdletters zijn en het woord 'eigenschap'. In elke rij, wordt de naam van de eigenschap weergegeven, gevolgd door de waarde van de eigenschap.

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

Het volgende voorbeeld laat zien hoe de Windows PowerShell wordt weergegeven de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten na het laden van deze bestandsindeling.

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

[Voorbeelden van opmaak bestanden](./examples-of-formatting-files.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
