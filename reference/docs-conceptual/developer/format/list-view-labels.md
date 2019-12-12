---
title: Lijst weergave (labels) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 27de41c88e224f7610c10a764e51524016ecc8cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354374"
---
# <a name="list-view-labels"></a><span data-ttu-id="a4d2b-102">Lijstweergave (Labels)</span><span class="sxs-lookup"><span data-stu-id="a4d2b-102">List View (Labels)</span></span>

<span data-ttu-id="a4d2b-103">In dit voor beeld ziet u hoe u een lijst weergave implementeert waarin een aangepast label wordt weer gegeven voor elke rij van de lijst.</span><span class="sxs-lookup"><span data-stu-id="a4d2b-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="a4d2b-104">In deze lijst weergave worden de eigenschappen van [System. ServiceProcess. servicecontroller weer gegeven? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -object dat wordt geretourneerd door de cmdlet [Get-service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) .</span><span class="sxs-lookup"><span data-stu-id="a4d2b-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="a4d2b-105">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over de onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="a4d2b-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="a4d2b-106">Dit indelings bestand laden</span><span class="sxs-lookup"><span data-stu-id="a4d2b-106">To load this formatting file</span></span>

1. <span data-ttu-id="a4d2b-107">Kopieer de XML uit de sectie voor beeld van dit onderwerp naar een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="a4d2b-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="a4d2b-108">Sla het tekstbestand op.</span><span class="sxs-lookup"><span data-stu-id="a4d2b-108">Save the text file.</span></span> <span data-ttu-id="a4d2b-109">Zorg ervoor dat u de extensie `format.ps1xml` toevoegt aan het bestand om het te identificeren als een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="a4d2b-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="a4d2b-110">Open Windows Power shell en voer de volgende opdracht uit om het opmaak bestand in de huidige sessie te laden: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="a4d2b-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="a4d2b-111">Dit opmaak bestand definieert de weer gave van een object dat al is gedefinieerd door een Windows Power shell-indelings bestand.</span><span class="sxs-lookup"><span data-stu-id="a4d2b-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="a4d2b-112">U moet de para meter `prependPath` gebruiken wanneer u de cmdlet uitvoert. u kunt dit indelings bestand niet laden als een module.</span><span class="sxs-lookup"><span data-stu-id="a4d2b-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a4d2b-113">Hier ziet u</span><span class="sxs-lookup"><span data-stu-id="a4d2b-113">Demonstrates</span></span>

<span data-ttu-id="a4d2b-114">In dit opmaak bestand worden de volgende XML-elementen gedemonstreerd:</span><span class="sxs-lookup"><span data-stu-id="a4d2b-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="a4d2b-115">Het [naam](./name-element-for-view-format.md) element voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="a4d2b-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="a4d2b-116">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element dat definieert welke objecten worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="a4d2b-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="a4d2b-117">Het element [ListControl](./listcontrol-element-format.md) dat definieert welke eigenschap wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="a4d2b-117">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="a4d2b-118">Het [lijst item](./listitem-element-for-listitems-for-listcontrol-format.md) -element dat definieert wat wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="a4d2b-118">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="a4d2b-119">Het [Label](./label-element-for-listitem-for-listcontrol-format.md) -element dat definieert wat wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="a4d2b-119">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="a4d2b-120">Het element [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) waarmee wordt gedefinieerd welke eigenschap wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a4d2b-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="a4d2b-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="a4d2b-121">Example</span></span>

<span data-ttu-id="a4d2b-122">De volgende XML definieert een lijst weergave waarin een aangepast label wordt weer gegeven in elke rij.</span><span class="sxs-lookup"><span data-stu-id="a4d2b-122">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="a4d2b-123">In dit geval bevat het label de naam van de eigenschap met een hoofd letter en het woord "eigenschap".</span><span class="sxs-lookup"><span data-stu-id="a4d2b-123">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="a4d2b-124">In elke rij wordt de naam van de eigenschap weer gegeven gevolgd door de waarde van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="a4d2b-124">In each row, the name of the property is displayed followed by the value of the property.</span></span>

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

<span data-ttu-id="a4d2b-125">In het volgende voor beeld ziet u hoe de [System. ServiceProcess. servicecontroller wordt weer gegeven in Windows Power shell? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten nadat dit indelings bestand is geladen.</span><span class="sxs-lookup"><span data-stu-id="a4d2b-125">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a4d2b-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a4d2b-126">See Also</span></span>

[<span data-ttu-id="a4d2b-127">Voor beelden van het format teren van bestanden</span><span class="sxs-lookup"><span data-stu-id="a4d2b-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="a4d2b-128">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="a4d2b-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
