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
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794821"
---
# <a name="list-view-labels"></a><span data-ttu-id="89342-102">Lijstweergave (Labels)</span><span class="sxs-lookup"><span data-stu-id="89342-102">List View (Labels)</span></span>

<span data-ttu-id="89342-103">In dit voorbeeld laat zien hoe voor het implementeren van een lijstweergave met een aangepaste label voor elke rij van de lijst weergegeven.</span><span class="sxs-lookup"><span data-stu-id="89342-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="89342-104">In deze lijstweergave geeft de eigenschappen van de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object dat wordt geretourneerd door de [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="89342-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="89342-105">Zie voor meer informatie over de onderdelen van een lijst weergeven, [het maken van een lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="89342-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="89342-106">Deze opmaak bestand laden</span><span class="sxs-lookup"><span data-stu-id="89342-106">To load this formatting file</span></span>

1. <span data-ttu-id="89342-107">Kopieer het XML-bestand van de voorbeeld-sectie van dit onderwerp in een tekstbestand.</span><span class="sxs-lookup"><span data-stu-id="89342-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="89342-108">Bewaar het tekstbestand.</span><span class="sxs-lookup"><span data-stu-id="89342-108">Save the text file.</span></span> <span data-ttu-id="89342-109">Zorg ervoor dat om toe te voegen de `format.ps1xml` uitbreiding van het bestand om het te identificeren als een opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="89342-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="89342-110">Open Windows PowerShell en voer de volgende opdracht om de opmaak bestand laden in de huidige sessie: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="89342-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="89342-111">Deze opmaak bestand definieert de weergave van een object dat al is gedefinieerd door een bestand van Windows PowerShell-opmaak.</span><span class="sxs-lookup"><span data-stu-id="89342-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="89342-112">Moet u de `prependPath` parameter wanneer u de cmdlet uitvoert, en deze opmaak kan niet worden geladen als een module-bestand.</span><span class="sxs-lookup"><span data-stu-id="89342-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="89342-113">Hier ziet u</span><span class="sxs-lookup"><span data-stu-id="89342-113">Demonstrates</span></span>

<span data-ttu-id="89342-114">Deze opmaak bestand ziet u de volgende XML-elementen:</span><span class="sxs-lookup"><span data-stu-id="89342-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="89342-115">De [naam](./name-element-for-view-format.md) -element voor de weergave.</span><span class="sxs-lookup"><span data-stu-id="89342-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="89342-116">De [ViewSelectedBy](./viewselectedby-element-format.md) element waarmee wordt gedefinieerd welke objecten worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="89342-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="89342-117">De [ListControl](./listcontrol-element-format.md) element waarmee wordt gedefinieerd welke eigenschap van de weergave wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="89342-117">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="89342-118">De [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element die definieert wat wordt weergegeven in een rij in de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="89342-118">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="89342-119">De [Label](./label-element-for-listitem-for-listcontrol-format.md) element die definieert wat wordt weergegeven in een rij in de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="89342-119">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="89342-120">De [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element waarmee wordt gedefinieerd welke eigenschap wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="89342-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="89342-121">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="89342-121">Example</span></span>

<span data-ttu-id="89342-122">Het volgende XML-bestand definieert een lijstweergave met een aangepaste label in elke rij weergegeven.</span><span class="sxs-lookup"><span data-stu-id="89342-122">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="89342-123">In dit geval wordt het label bevat de naam van de eigenschap met alle letters in hoofdletters zijn en het woord 'eigenschap'.</span><span class="sxs-lookup"><span data-stu-id="89342-123">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="89342-124">In elke rij, wordt de naam van de eigenschap weergegeven, gevolgd door de waarde van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="89342-124">In each row, the name of the property is displayed followed by the value of the property.</span></span>

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

<span data-ttu-id="89342-125">Het volgende voorbeeld laat zien hoe de Windows PowerShell wordt weergegeven de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten na het laden van deze bestandsindeling.</span><span class="sxs-lookup"><span data-stu-id="89342-125">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="89342-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="89342-126">See Also</span></span>

[<span data-ttu-id="89342-127">Voorbeelden van opmaak bestanden</span><span class="sxs-lookup"><span data-stu-id="89342-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="89342-128">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="89342-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
