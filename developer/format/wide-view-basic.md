---
title: Brede weergave (basis) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849684"
---
# <a name="wide-view-basic"></a><span data-ttu-id="6fe5a-102">Brede weergave (Basis)</span><span class="sxs-lookup"><span data-stu-id="6fe5a-102">Wide View (Basic)</span></span>

<span data-ttu-id="6fe5a-103">In dit voorbeeld laat zien hoe voor het implementeren van een eenvoudige brede weergave die wordt weergegeven de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten die worden geretourneerd door de `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6fe5a-103">This example shows how to implement a basic wide view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="6fe5a-104">Zie voor meer informatie over de onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="6fe5a-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="6fe5a-105">Deze opmaak bestand laden</span><span class="sxs-lookup"><span data-stu-id="6fe5a-105">To load this formatting file</span></span>

1. <span data-ttu-id="6fe5a-106">Kopieer het XML-bestand van de voorbeeld-sectie van dit onderwerp in een tekstbestand.</span><span class="sxs-lookup"><span data-stu-id="6fe5a-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="6fe5a-107">Bewaar het tekstbestand.</span><span class="sxs-lookup"><span data-stu-id="6fe5a-107">Save the text file.</span></span> <span data-ttu-id="6fe5a-108">Zorg ervoor dat om toe te voegen de `format.ps1xml` uitbreiding van het bestand om het te identificeren als een opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="6fe5a-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="6fe5a-109">Open Windows PowerShell en voer de volgende opdracht om de opmaak bestand laden in de huidige sessie: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="6fe5a-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="6fe5a-110">Deze opmaak bestand definieert de weergave van een object dat al is gedefinieerd door een bestand van Windows PowerShell-opmaak.</span><span class="sxs-lookup"><span data-stu-id="6fe5a-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="6fe5a-111">Moet u de `prependPath` parameter wanneer u de cmdlet uitvoert, en deze opmaak kan niet worden geladen als een module-bestand.</span><span class="sxs-lookup"><span data-stu-id="6fe5a-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="6fe5a-112">Hier ziet u</span><span class="sxs-lookup"><span data-stu-id="6fe5a-112">Demonstrates</span></span>

<span data-ttu-id="6fe5a-113">Deze opmaak bestand ziet u de volgende XML-elementen:</span><span class="sxs-lookup"><span data-stu-id="6fe5a-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="6fe5a-114">De [naam](./name-element-for-view-format.md) -element voor de weergave.</span><span class="sxs-lookup"><span data-stu-id="6fe5a-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="6fe5a-115">De [ViewSelectedBy](./viewselectedby-element-format.md) element waarmee wordt gedefinieerd welke objecten worden weergegeven in de weergave.</span><span class="sxs-lookup"><span data-stu-id="6fe5a-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="6fe5a-116">De [WideItem](./wideitem-element-for-widecontrol-format.md) element waarmee wordt gedefinieerd welke eigenschap van de weergave wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="6fe5a-116">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="6fe5a-117">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="6fe5a-117">Example</span></span>

<span data-ttu-id="6fe5a-118">Het volgende XML-bestand definieert een brede weergave waarin de waarde van de [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) eigenschap.</span><span class="sxs-lookup"><span data-stu-id="6fe5a-118">The following XML defines a wide view that displays the value of the [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) property.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
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

<span data-ttu-id="6fe5a-119">Het volgende voorbeeld laat zien hoe de Windows PowerShell wordt weergegeven de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objecten na het laden van deze bestandsindeling.</span><span class="sxs-lookup"><span data-stu-id="6fe5a-119">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="6fe5a-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6fe5a-120">See Also</span></span>

[<span data-ttu-id="6fe5a-121">Voorbeelden van opmaak bestanden</span><span class="sxs-lookup"><span data-stu-id="6fe5a-121">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="6fe5a-122">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="6fe5a-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
