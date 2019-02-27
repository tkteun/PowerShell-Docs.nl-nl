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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850748"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="7b354-102">Brede weergave (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="7b354-102">Wide View (GroupBy)</span></span>

<span data-ttu-id="7b354-103">Dit voorbeeld laat zien hoe u een brede weergave met beveiligingsgroepen van implementeert [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten die worden geretourneerd door de `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7b354-103">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="7b354-104">Zie voor meer informatie over de onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="7b354-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="7b354-105">Deze opmaak bestand laden</span><span class="sxs-lookup"><span data-stu-id="7b354-105">To load this formatting file</span></span>

1. <span data-ttu-id="7b354-106">Kopieer het XML-bestand van de voorbeeld-sectie van dit onderwerp in een tekstbestand.</span><span class="sxs-lookup"><span data-stu-id="7b354-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="7b354-107">Bewaar het tekstbestand.</span><span class="sxs-lookup"><span data-stu-id="7b354-107">Save the text file.</span></span> <span data-ttu-id="7b354-108">Zorg ervoor dat om toe te voegen de `format.ps1xml` uitbreiding van het bestand om het te identificeren als een opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="7b354-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="7b354-109">Open Windows PowerShell en voer de volgende opdracht om de opmaak bestand laden in de huidige sessie: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="7b354-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="7b354-110">Deze opmaak bestand definieert de weergave van een object dat al is gedefinieerd door een Windows PowerShell opmaak van bestanden.</span><span class="sxs-lookup"><span data-stu-id="7b354-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="7b354-111">Moet u de `prependPath` parameter wanneer u de cmdlet uitvoert, en deze opmaak kan niet worden geladen als een module-bestand.</span><span class="sxs-lookup"><span data-stu-id="7b354-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="7b354-112">Hier ziet u</span><span class="sxs-lookup"><span data-stu-id="7b354-112">Demonstrates</span></span>

<span data-ttu-id="7b354-113">Deze opmaak bestand ziet u de volgende XML-elementen:</span><span class="sxs-lookup"><span data-stu-id="7b354-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="7b354-114">De [naam](./name-element-for-view-format.md) -element voor de weergave.</span><span class="sxs-lookup"><span data-stu-id="7b354-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="7b354-115">De [ViewSelectedBy](./viewselectedby-element-format.md) element waarmee wordt gedefinieerd welke objecten worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="7b354-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="7b354-116">De [GroupBy](./groupby-element-for-view-format.md) element waarmee wordt gedefinieerd wanneer een nieuwe groep wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="7b354-116">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="7b354-117">De [WideItem](./wideitem-element-for-widecontrol-format.md) element waarmee wordt gedefinieerd welke eigenschap van de weergave wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="7b354-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="7b354-118">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="7b354-118">Example</span></span>

<span data-ttu-id="7b354-119">Het volgende XML-bestand definieert een brede weergave waarin te zien van groepen objecten.</span><span class="sxs-lookup"><span data-stu-id="7b354-119">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="7b354-120">Elke nieuwe groep wordt gestart wanneer de waarde van de [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) wijzigingen in de eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="7b354-120">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

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

<span data-ttu-id="7b354-121">Het volgende voorbeeld laat zien hoe de Windows PowerShell wordt weergegeven de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten na het laden van deze bestandsindeling.</span><span class="sxs-lookup"><span data-stu-id="7b354-121">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7b354-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7b354-122">See Also</span></span>

[<span data-ttu-id="7b354-123">Voorbeelden van opmaak bestanden</span><span class="sxs-lookup"><span data-stu-id="7b354-123">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="7b354-124">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="7b354-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
