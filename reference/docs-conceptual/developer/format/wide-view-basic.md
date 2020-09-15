---
title: Brede weer gave (basis) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d92c29c33c5104b6186ae53ccf544be197d657b1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772396"
---
# <a name="wide-view-basic"></a><span data-ttu-id="965a9-102">Brede weergave (Basis)</span><span class="sxs-lookup"><span data-stu-id="965a9-102">Wide View (Basic)</span></span>

<span data-ttu-id="965a9-103">In dit voor beeld ziet u hoe u een algemene weer gave implementeert waarin [System. ServiceProcess. servicecontroller wordt weer gegeven? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten die door de `Get-Service` cmdlet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="965a9-103">This example shows how to implement a basic wide view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="965a9-104">Zie [een brede weer gave maken](./creating-a-wide-view.md)voor meer informatie over de onderdelen van een brede weer gave.</span><span class="sxs-lookup"><span data-stu-id="965a9-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="965a9-105">Dit indelings bestand laden</span><span class="sxs-lookup"><span data-stu-id="965a9-105">To load this formatting file</span></span>

1. <span data-ttu-id="965a9-106">Kopieer de XML uit de sectie voor beeld van dit onderwerp naar een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="965a9-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="965a9-107">Sla het tekstbestand op.</span><span class="sxs-lookup"><span data-stu-id="965a9-107">Save the text file.</span></span> <span data-ttu-id="965a9-108">Zorg ervoor dat u de `format.ps1xml` extensie toevoegt aan het bestand om het te identificeren als een indelings bestand.</span><span class="sxs-lookup"><span data-stu-id="965a9-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="965a9-109">Open Windows Power shell en voer de volgende opdracht uit om het opmaak bestand in de huidige sessie te laden: `Update-formatdata -prependpath PathToFormattingFile` .</span><span class="sxs-lookup"><span data-stu-id="965a9-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="965a9-110">Dit opmaak bestand definieert de weer gave van een object dat al is gedefinieerd door een Windows Power shell-indelings bestand.</span><span class="sxs-lookup"><span data-stu-id="965a9-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="965a9-111">U moet de `prependPath` para meter gebruiken bij het uitvoeren van de cmdlet en u kunt dit indelings bestand niet laden als een module.</span><span class="sxs-lookup"><span data-stu-id="965a9-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="965a9-112">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="965a9-112">Demonstrates</span></span>

<span data-ttu-id="965a9-113">In dit opmaak bestand worden de volgende XML-elementen gedemonstreerd:</span><span class="sxs-lookup"><span data-stu-id="965a9-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="965a9-114">Het [naam](./name-element-for-view-format.md) element voor de weer gave.</span><span class="sxs-lookup"><span data-stu-id="965a9-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="965a9-115">Het [ViewSelectedBy](./viewselectedby-element-format.md) -element dat definieert welke objecten worden weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="965a9-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="965a9-116">Het [WideItem](./wideitem-element-for-widecontrol-format.md) -element waarmee wordt gedefinieerd welke eigenschap wordt weer gegeven in de weer gave.</span><span class="sxs-lookup"><span data-stu-id="965a9-116">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="965a9-117">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="965a9-117">Example</span></span>

<span data-ttu-id="965a9-118">De volgende XML definieert een brede weer gave waarin de waarde van de eigenschap [System. ServiceProcess. servicecontroller. ServiceName](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="965a9-118">The following XML defines a wide view that displays the value of the [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) property.</span></span>

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

<span data-ttu-id="965a9-119">In het volgende voor beeld ziet u hoe de [System. ServiceProcess. servicecontroller wordt weer gegeven in Windows Power shell? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) objecten nadat dit indelings bestand is geladen.</span><span class="sxs-lookup"><span data-stu-id="965a9-119">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="965a9-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="965a9-120">See Also</span></span>

[<span data-ttu-id="965a9-121">Voorbeelden van opmaakbestanden</span><span class="sxs-lookup"><span data-stu-id="965a9-121">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="965a9-122">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="965a9-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
