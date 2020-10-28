---
ms.date: 09/13/2016
ms.topic: reference
title: Lijstweergave (Labels)
description: Lijstweergave (Labels)
ms.openlocfilehash: 2d341ae95d025e0f95b5d88b96afb846b62b092f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666685"
---
# <a name="list-view-labels"></a><span data-ttu-id="30dc1-103">Lijstweergave (Labels)</span><span class="sxs-lookup"><span data-stu-id="30dc1-103">List View (Labels)</span></span>

<span data-ttu-id="30dc1-104">In dit voor beeld ziet u hoe u een lijst weergave implementeert waarin een aangepast label wordt weer gegeven voor elke rij van de lijst.</span><span class="sxs-lookup"><span data-stu-id="30dc1-104">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="30dc1-105">In deze lijst weergave worden de eigenschappen van [System. ServiceProcess. servicecontroller weer gegeven? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -object dat wordt geretourneerd door de cmdlet [Get-service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) .</span><span class="sxs-lookup"><span data-stu-id="30dc1-105">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="30dc1-106">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over de onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="30dc1-106">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="30dc1-107">Dit indelings bestand laden</span><span class="sxs-lookup"><span data-stu-id="30dc1-107">To load this formatting file</span></span>

1. <span data-ttu-id="30dc1-108">Kopieer de XML uit de sectie voor beeld van dit onderwerp naar een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="30dc1-108">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="30dc1-109">Sla het tekstbestand op.</span><span class="sxs-lookup"><span data-stu-id="30dc1-109">Save the text file.</span></span> <span data-ttu-id="30dc1-110">Zorg ervoor dat u de `format.ps1xml` extensie toevoegt aan het bestand om het te identificeren als een indelings bestand.</span><span class="sxs-lookup"><span data-stu-id="30dc1-110">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="30dc1-111">Open Windows Power shell en voer de volgende opdracht uit om het opmaak bestand in de huidige sessie te laden: `Update-formatdata -prependpath PathToFormattingFile` .</span><span class="sxs-lookup"><span data-stu-id="30dc1-111">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="30dc1-112">Dit opmaak bestand definieert de weer gave van een object dat al is gedefinieerd door een Windows Power shell-indelings bestand.</span><span class="sxs-lookup"><span data-stu-id="30dc1-112">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="30dc1-113">U moet de `prependPath` para meter gebruiken bij het uitvoeren van de cmdlet en u kunt dit indelings bestand niet laden als een module.</span><span class="sxs-lookup"><span data-stu-id="30dc1-113">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="30dc1-114">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="30dc1-114">Demonstrates</span></span>

<span data-ttu-id="30dc1-115">In dit opmaak bestand worden de volgende XML-elementen gedemonstreerd:</span><span class="sxs-lookup"><span data-stu-id="30dc1-115">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="30dc1-116">Het [naam](./name-element-for-view-format.md) element voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="30dc1-116">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="30dc1-117">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element dat definieert welke objecten worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="30dc1-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="30dc1-118">Het element [ListControl](./listcontrol-element-format.md) dat definieert welke eigenschap wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="30dc1-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="30dc1-119">Het [lijst item](./listitem-element-for-listitems-for-listcontrol-format.md) -element dat definieert wat wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="30dc1-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="30dc1-120">Het [Label](./label-element-for-listitem-for-listcontrol-format.md) -element dat definieert wat wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="30dc1-120">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="30dc1-121">Het element [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) waarmee wordt gedefinieerd welke eigenschap wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="30dc1-121">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="30dc1-122">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="30dc1-122">Example</span></span>

<span data-ttu-id="30dc1-123">De volgende XML definieert een lijst weergave waarin een aangepast label wordt weer gegeven in elke rij.</span><span class="sxs-lookup"><span data-stu-id="30dc1-123">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="30dc1-124">In dit geval bevat het label de naam van de eigenschap met een hoofd letter en het woord "eigenschap".</span><span class="sxs-lookup"><span data-stu-id="30dc1-124">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="30dc1-125">In elke rij wordt de naam van de eigenschap weer gegeven gevolgd door de waarde van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="30dc1-125">In each row, the name of the property is displayed followed by the value of the property.</span></span>

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

<span data-ttu-id="30dc1-126">In het volgende voor beeld ziet u hoe de [System. ServiceProcess. servicecontroller wordt weer gegeven in Windows Power shell? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten nadat dit indelings bestand is geladen.</span><span class="sxs-lookup"><span data-stu-id="30dc1-126">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="30dc1-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="30dc1-127">See Also</span></span>

[<span data-ttu-id="30dc1-128">Voorbeelden van opmaakbestanden</span><span class="sxs-lookup"><span data-stu-id="30dc1-128">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="30dc1-129">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="30dc1-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
