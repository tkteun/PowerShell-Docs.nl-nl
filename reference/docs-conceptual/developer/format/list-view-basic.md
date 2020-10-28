---
ms.date: 09/13/2016
ms.topic: reference
title: Lijstweergave (Basis)
description: Lijstweergave (Basis)
ms.openlocfilehash: d80ac9c6143b976d8bc13e2b184e4f5a2f8a37ab
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666634"
---
# <a name="list-view-basic"></a><span data-ttu-id="f1a90-103">Lijstweergave (Basis)</span><span class="sxs-lookup"><span data-stu-id="f1a90-103">List View (Basic)</span></span>

<span data-ttu-id="f1a90-104">In dit voor beeld ziet u hoe u een basis lijst weergave implementeert waarin [System. ServiceProcess. servicecontroller wordt weer gegeven? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten die door de [Get-service-](/powershell/module/microsoft.powershell.management/get-service) cmdlet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f1a90-104">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="f1a90-105">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over de onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="f1a90-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="f1a90-106">Dit indelings bestand laden</span><span class="sxs-lookup"><span data-stu-id="f1a90-106">To load this formatting file</span></span>

1. <span data-ttu-id="f1a90-107">Kopieer de XML uit de sectie voor beeld van dit onderwerp naar een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="f1a90-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="f1a90-108">Sla het tekstbestand op.</span><span class="sxs-lookup"><span data-stu-id="f1a90-108">Save the text file.</span></span> <span data-ttu-id="f1a90-109">Zorg ervoor dat u de `format.ps1xml` extensie toevoegt aan het bestand om het te identificeren als een indelings bestand.</span><span class="sxs-lookup"><span data-stu-id="f1a90-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="f1a90-110">Open Windows Power shell en voer de volgende opdracht uit om het opmaak bestand in de huidige sessie te laden: `Update-formatdata -prependpath PathToFormattingFile` .</span><span class="sxs-lookup"><span data-stu-id="f1a90-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="f1a90-111">Dit opmaak bestand definieert de weer gave van een object dat al is gedefinieerd door een Windows Power shell-indelings bestand.</span><span class="sxs-lookup"><span data-stu-id="f1a90-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="f1a90-112">U moet de `prependPath` para meter gebruiken bij het uitvoeren van de cmdlet en u kunt dit indelings bestand niet laden als een module.</span><span class="sxs-lookup"><span data-stu-id="f1a90-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f1a90-113">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="f1a90-113">Demonstrates</span></span>

<span data-ttu-id="f1a90-114">In dit opmaak bestand worden de volgende XML-elementen gedemonstreerd:</span><span class="sxs-lookup"><span data-stu-id="f1a90-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="f1a90-115">Het [naam](./name-element-for-view-format.md) element voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="f1a90-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="f1a90-116">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element dat definieert welke objecten worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="f1a90-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="f1a90-117">Het element [ListControl](./listcontrol-element-format.md) dat definieert welke eigenschap wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="f1a90-117">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="f1a90-118">Het [lijst item](./listitem-element-for-listitems-for-listcontrol-format.md) -element dat definieert wat wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="f1a90-118">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="f1a90-119">Het element [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) waarmee wordt gedefinieerd welke eigenschap wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f1a90-119">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="f1a90-120">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="f1a90-120">Example</span></span>

<span data-ttu-id="f1a90-121">In het volgende XML-bestand wordt een lijst weergave gedefinieerd die vier eigenschappen van [System. ServiceProcess. servicecontroller weergeeft? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -object.</span><span class="sxs-lookup"><span data-stu-id="f1a90-121">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="f1a90-122">In elke rij wordt de naam van de eigenschap weer gegeven gevolgd door de waarde van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="f1a90-122">In each row, the name of the property is displayed followed by the value of the property.</span></span>

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

<span data-ttu-id="f1a90-123">In het volgende voor beeld ziet u hoe de [System. ServiceProcess. servicecontroller wordt weer gegeven in Windows Power shell? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten nadat dit indelings bestand is geladen.</span><span class="sxs-lookup"><span data-stu-id="f1a90-123">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f1a90-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f1a90-124">See Also</span></span>

[<span data-ttu-id="f1a90-125">Voorbeelden van opmaakbestanden</span><span class="sxs-lookup"><span data-stu-id="f1a90-125">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="f1a90-126">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="f1a90-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
