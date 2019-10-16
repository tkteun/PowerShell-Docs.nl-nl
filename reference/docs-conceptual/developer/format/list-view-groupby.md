---
title: Lijst weergave (GroupBy) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: c178c4a48f9595001bcc249d5f55886fa54bb9f2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356019"
---
# <a name="list-view-groupby"></a><span data-ttu-id="9c7c2-102">Lijstweergave (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="9c7c2-102">List View (GroupBy)</span></span>

<span data-ttu-id="9c7c2-103">In dit voor beeld ziet u hoe u een lijst weergave implementeert waarmee de rijen van de lijst worden gescheiden in groepen.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="9c7c2-104">In deze lijst weergave worden de eigenschappen van [System. ServiceProcess. servicecontroller weer gegeven? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten die door de [Get-service-](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="9c7c2-105">Zie [een lijst weergave maken](./creating-a-list-view.md)voor meer informatie over de onderdelen van een lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="9c7c2-106">Dit indelings bestand laden</span><span class="sxs-lookup"><span data-stu-id="9c7c2-106">To load this formatting file</span></span>

1. <span data-ttu-id="9c7c2-107">Kopieer de XML uit de sectie voor beeld van dit onderwerp naar een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="9c7c2-108">Sla het tekst bestand op.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-108">Save the text file.</span></span> <span data-ttu-id="9c7c2-109">Zorg ervoor dat u de extensie @no__t 0 toevoegt aan het bestand om het te identificeren als een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="9c7c2-110">Open Windows Power shell en voer de volgende opdracht uit om het opmaak bestand in de huidige sessie te laden: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="9c7c2-111">Dit opmaak bestand definieert de weer gave van een object dat al is gedefinieerd door een Windows Power shell-indelings bestand.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="9c7c2-112">U moet de para meter `prependPath` gebruiken wanneer u de cmdlet uitvoert. u kunt dit indelings bestand niet laden als een module.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="9c7c2-113">Laat zien</span><span class="sxs-lookup"><span data-stu-id="9c7c2-113">Demonstrates</span></span>

<span data-ttu-id="9c7c2-114">In dit opmaak bestand worden de volgende XML-elementen gedemonstreerd:</span><span class="sxs-lookup"><span data-stu-id="9c7c2-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="9c7c2-115">Het [naam](./name-element-for-view-format.md) element voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="9c7c2-116">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element dat definieert welke objecten worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="9c7c2-117">Het element [GroupBy](./viewselectedby-element-format.md) dat definieert hoe een nieuwe groep objecten wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-117">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="9c7c2-118">Het element [ListControl](./listcontrol-element-format.md) dat definieert welke eigenschap wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="9c7c2-119">Het [lijst item](./listitem-element-for-listitems-for-listcontrol-format.md) -element dat definieert wat wordt weer gegeven in een rij van de lijst weergave.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="9c7c2-120">Het element [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) waarmee wordt gedefinieerd welke eigenschap wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="9c7c2-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="9c7c2-121">Example</span></span>

<span data-ttu-id="9c7c2-122">De volgende XML definieert een lijst weergave waarmee een nieuwe groep wordt gestart wanneer de waarde van de eigenschap [System. ServiceProcess. servicecontroller. status](/dotnet/api/System.ServiceProcess.ServiceController.Status) wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-122">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="9c7c2-123">Wanneer elke groep wordt gestart, wordt een aangepast label weer gegeven met daarin de nieuwe waarde van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-123">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

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

<span data-ttu-id="9c7c2-124">In het volgende voor beeld ziet u hoe de [System. ServiceProcess. servicecontroller wordt weer gegeven in Windows Power shell? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten nadat dit indelings bestand is geladen.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="9c7c2-125">De lege regels die voor en na het groeps label worden toegevoegd, worden automatisch toegevoegd door Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="9c7c2-125">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9c7c2-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9c7c2-126">See Also</span></span>

[<span data-ttu-id="9c7c2-127">Voor beelden van het format teren van bestanden</span><span class="sxs-lookup"><span data-stu-id="9c7c2-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="9c7c2-128">Een Power shell-indelings bestand schrijven</span><span class="sxs-lookup"><span data-stu-id="9c7c2-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
