---
title: Lijstweergave (basis) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 3c94d8e98f179286112a417230fce659dc0b614c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065305"
---
# <a name="list-view-basic"></a>Lijstweergave (Basis)

In dit voorbeeld laat zien hoe voor het implementeren van een eenvoudige lijstweergave waarop de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten die worden geretourneerd door de [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. Zie voor meer informatie over de onderdelen van een lijst weergeven, [het maken van een lijstweergave](./creating-a-list-view.md).

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

- De [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element waarmee wordt gedefinieerd welke eigenschap wordt weergegeven.

## <a name="example"></a>Voorbeeld

Het volgende XML-bestand definieert een lijst weergeven met vier eigenschappen van de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object. In elke rij, wordt de naam van de eigenschap weergegeven, gevolgd door de waarde van de eigenschap.

```xml
<Configuration>
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
</Configuration>
```

Het volgende voorbeeld laat zien hoe de Windows PowerShell wordt weergegeven de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten na het laden van deze bestandsindeling.

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a>Zie ook

[Voorbeelden van opmaak bestanden](./examples-of-formatting-files.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
