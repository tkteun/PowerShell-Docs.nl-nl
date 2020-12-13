---
ms.date: 09/13/2016
ms.topic: reference
title: Brede weergave (GroupBy)
description: Brede weergave (GroupBy)
ms.openlocfilehash: 807bea2a5d44c38e2c9977f792bea2fb9bca0fc3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667671"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="37ce1-103">Brede weergave (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="37ce1-103">Wide View (GroupBy)</span></span>

<span data-ttu-id="37ce1-104">In dit voor beeld ziet u hoe u een brede weer gave implementeert waarin groepen [System. ServiceProcess. servicecontroller worden weer gegeven? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten die door de `Get-Service` cmdlet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="37ce1-104">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="37ce1-105">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="37ce1-105">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="37ce1-106">Dit indelings bestand laden</span><span class="sxs-lookup"><span data-stu-id="37ce1-106">To load this formatting file</span></span>

1. <span data-ttu-id="37ce1-107">Kopieer de XML uit de sectie voor beeld van dit onderwerp naar een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="37ce1-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="37ce1-108">Sla het tekstbestand op.</span><span class="sxs-lookup"><span data-stu-id="37ce1-108">Save the text file.</span></span> <span data-ttu-id="37ce1-109">Zorg ervoor dat u de `format.ps1xml` extensie toevoegt aan het bestand om het te identificeren als een indelings bestand.</span><span class="sxs-lookup"><span data-stu-id="37ce1-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="37ce1-110">Open Windows Power shell en voer de volgende opdracht uit om het opmaak bestand in de huidige sessie te laden: `Update-formatdata -prependpath PathToFormattingFile` .</span><span class="sxs-lookup"><span data-stu-id="37ce1-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="37ce1-111">Dit opmaak bestand definieert de weer gave van een object dat al is gedefinieerd door een Windows Power shell-indelings bestanden.</span><span class="sxs-lookup"><span data-stu-id="37ce1-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="37ce1-112">U moet de `prependPath` para meter gebruiken bij het uitvoeren van de cmdlet en u kunt dit indelings bestand niet laden als een module.</span><span class="sxs-lookup"><span data-stu-id="37ce1-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="37ce1-113">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="37ce1-113">Demonstrates</span></span>

<span data-ttu-id="37ce1-114">In dit opmaak bestand worden de volgende XML-elementen gedemonstreerd:</span><span class="sxs-lookup"><span data-stu-id="37ce1-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="37ce1-115">Het [naam](./name-element-for-view-format.md) element voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="37ce1-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="37ce1-116">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element dat definieert welke objecten worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="37ce1-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="37ce1-117">Het element [GroupBy](./groupby-element-for-view-format.md) dat definieert wanneer een nieuwe groep wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="37ce1-117">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="37ce1-118">Het [WideItem](./wideitem-element-for-widecontrol-format.md) -element waarmee wordt gedefinieerd welke eigenschap wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="37ce1-118">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="37ce1-119">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="37ce1-119">Example</span></span>

<span data-ttu-id="37ce1-120">De volgende XML definieert een brede weer gave waarin groepen objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="37ce1-120">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="37ce1-121">Elke nieuwe groep wordt gestart wanneer de waarde van de eigenschap [System. ServiceProcess. servicecontroller. service](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) type wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="37ce1-121">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

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

<span data-ttu-id="37ce1-122">In het volgende voor beeld ziet u hoe de [System. ServiceProcess. servicecontroller wordt weer gegeven in Windows Power shell? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten nadat dit indelings bestand is geladen.</span><span class="sxs-lookup"><span data-stu-id="37ce1-122">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="37ce1-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="37ce1-123">See Also</span></span>

[<span data-ttu-id="37ce1-124">Voorbeelden van opmaakbestanden</span><span class="sxs-lookup"><span data-stu-id="37ce1-124">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="37ce1-125">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="37ce1-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
