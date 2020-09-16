---
title: Lijst weergave (basis) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 74ff8f6eee0a9358c123455aa00736a11e7f085d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783548"
---
# <a name="list-view-basic"></a><span data-ttu-id="379e6-102">Lijstweergave (Basis)</span><span class="sxs-lookup"><span data-stu-id="379e6-102">List View (Basic)</span></span>

<span data-ttu-id="379e6-103">In dit voor beeld ziet u hoe u een basis lijst weergave implementeert waarin [System. ServiceProcess. servicecontroller wordt weer gegeven? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten die door de [Get-service-](/powershell/module/microsoft.powershell.management/get-service) cmdlet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="379e6-103">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="379e6-104">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over de onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="379e6-104">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="379e6-105">Dit indelings bestand laden</span><span class="sxs-lookup"><span data-stu-id="379e6-105">To load this formatting file</span></span>

1. <span data-ttu-id="379e6-106">Kopieer de XML uit de sectie voor beeld van dit onderwerp naar een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="379e6-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="379e6-107">Sla het tekstbestand op.</span><span class="sxs-lookup"><span data-stu-id="379e6-107">Save the text file.</span></span> <span data-ttu-id="379e6-108">Zorg ervoor dat u de `format.ps1xml` extensie toevoegt aan het bestand om het te identificeren als een indelings bestand.</span><span class="sxs-lookup"><span data-stu-id="379e6-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="379e6-109">Open Windows Power shell en voer de volgende opdracht uit om het opmaak bestand in de huidige sessie te laden: `Update-formatdata -prependpath PathToFormattingFile` .</span><span class="sxs-lookup"><span data-stu-id="379e6-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="379e6-110">Dit opmaak bestand definieert de weer gave van een object dat al is gedefinieerd door een Windows Power shell-indelings bestand.</span><span class="sxs-lookup"><span data-stu-id="379e6-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="379e6-111">U moet de `prependPath` para meter gebruiken bij het uitvoeren van de cmdlet en u kunt dit indelings bestand niet laden als een module.</span><span class="sxs-lookup"><span data-stu-id="379e6-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="379e6-112">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="379e6-112">Demonstrates</span></span>

<span data-ttu-id="379e6-113">In dit opmaak bestand worden de volgende XML-elementen gedemonstreerd:</span><span class="sxs-lookup"><span data-stu-id="379e6-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="379e6-114">Het [naam](./name-element-for-view-format.md) element voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="379e6-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="379e6-115">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element dat definieert welke objecten worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="379e6-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="379e6-116">Het element [ListControl](./listcontrol-element-format.md) dat definieert welke eigenschap wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="379e6-116">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="379e6-117">Het [lijst item](./listitem-element-for-listitems-for-listcontrol-format.md) -element dat definieert wat wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="379e6-117">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="379e6-118">Het element [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) waarmee wordt gedefinieerd welke eigenschap wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="379e6-118">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="379e6-119">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="379e6-119">Example</span></span>

<span data-ttu-id="379e6-120">In het volgende XML-bestand wordt een lijst weergave gedefinieerd die vier eigenschappen van [System. ServiceProcess. servicecontroller weergeeft? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -object.</span><span class="sxs-lookup"><span data-stu-id="379e6-120">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="379e6-121">In elke rij wordt de naam van de eigenschap weer gegeven gevolgd door de waarde van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="379e6-121">In each row, the name of the property is displayed followed by the value of the property.</span></span>

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

<span data-ttu-id="379e6-122">In het volgende voor beeld ziet u hoe de [System. ServiceProcess. servicecontroller wordt weer gegeven in Windows Power shell? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten nadat dit indelings bestand is geladen.</span><span class="sxs-lookup"><span data-stu-id="379e6-122">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="379e6-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="379e6-123">See Also</span></span>

[<span data-ttu-id="379e6-124">Voorbeelden van opmaakbestanden</span><span class="sxs-lookup"><span data-stu-id="379e6-124">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="379e6-125">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="379e6-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
