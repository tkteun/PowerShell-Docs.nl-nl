---
title: Lijstweergave (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: c178c4a48f9595001bcc249d5f55886fa54bb9f2
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794435"
---
# <a name="list-view-groupby"></a>Lijstweergave (GroupBy)

In dit voorbeeld laat zien hoe voor het implementeren van een lijst weergeven die worden gescheiden van de rijen van de lijst in groepen. In deze lijstweergave geeft de eigenschappen van de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten die worden geretourneerd door de [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet. Zie voor meer informatie over de onderdelen van een lijst weergeven, [het maken van een lijstweergave](./creating-a-list-view.md).

### <a name="to-load-this-formatting-file"></a>Deze opmaak bestand laden

1. Kopieer het XML-bestand van de voorbeeld-sectie van dit onderwerp in een tekstbestand.

2. Bewaar het tekstbestand. Zorg ervoor dat om toe te voegen de `format.ps1xml` uitbreiding van het bestand om het te identificeren als een opmaak-bestand.

3. Open Windows PowerShell en voer de volgende opdracht om de opmaak bestand laden in de huidige sessie: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Deze opmaak bestand definieert de weergave van een object dat al is gedefinieerd door een bestand van Windows PowerShell-opmaak. Moet u de `prependPath` parameter wanneer u de cmdlet uitvoert, en deze opmaak kan niet worden geladen als een module-bestand.

## <a name="demonstrates"></a>Hier ziet u

Deze opmaak bestand ziet u de volgende XML-elementen:

- De [naam](./name-element-for-view-format.md) -element voor de weergave.

- De [ViewSelectedBy](./viewselectedby-element-format.md) element waarmee wordt gedefinieerd welke objecten worden weergegeven in de weergave.

- De [GroupBy](./viewselectedby-element-format.md) element waarmee wordt gedefinieerd hoe een nieuwe groep objecten worden weergegeven.

- De [ListControl](./listcontrol-element-format.md) element waarmee wordt gedefinieerd welke eigenschap van de weergave wordt weergegeven.

- De [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element die definieert wat wordt weergegeven in een rij in de lijstweergave.

- De [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element waarmee wordt gedefinieerd welke eigenschap wordt weergegeven.

## <a name="example"></a>Voorbeeld

Het volgende XML-bestand definieert een lijstweergave met een nieuwe start groep wanneer de waarde van de [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) wijzigingen in de eigenschappen. Wanneer elke groep wordt gestart, wordt een aangepast label met de nieuwe waarde van de eigenschap weergegeven.

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

Het volgende voorbeeld laat zien hoe de Windows PowerShell wordt weergegeven de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten na het laden van deze bestandsindeling. De lege regels voor en na het Groepslabel toegevoegd worden automatisch toegevoegd door Windows PowerShell.

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

[Voorbeelden van opmaak bestanden](./examples-of-formatting-files.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
