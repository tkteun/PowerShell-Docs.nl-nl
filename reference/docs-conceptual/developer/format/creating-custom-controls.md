---
ms.date: 09/13/2016
ms.topic: reference
title: Aangepaste besturingselementen maken
description: Aangepaste besturingselementen maken
ms.openlocfilehash: 78d8cc2970b2b3e493bef25d78404ba1be195bb1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668045"
---
# <a name="creating-custom-controls"></a><span data-ttu-id="f2f54-103">Aangepaste besturingselementen maken</span><span class="sxs-lookup"><span data-stu-id="f2f54-103">Creating Custom Controls</span></span>

<span data-ttu-id="f2f54-104">Aangepaste besturings elementen zijn de meest flexibele onderdelen van een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="f2f54-104">Custom controls are the most flexible components of a formatting file.</span></span> <span data-ttu-id="f2f54-105">In tegens telling tot tabel-, lijst-en brede weer gaven waarin een formele structuur van gegevens wordt gedefinieerd, zoals een tabel met gegevens, kunt u met aangepaste besturings elementen definiëren hoe een afzonderlijke hoeveelheid gegevens wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f2f54-105">Unlike table, list, and wide views that define a formal structure of data, such as a table of data, custom controls allow you to define how an individual piece of data is displayed.</span></span> <span data-ttu-id="f2f54-106">U kunt een algemene set aangepaste besturings elementen definiëren die beschikbaar zijn voor alle weer gaven van het opmaak bestand, u kunt aangepaste besturings elementen definiëren die beschikbaar zijn voor een specifieke weer gave of u kunt een set besturings elementen definiëren die beschikbaar zijn voor een groep objecten.</span><span class="sxs-lookup"><span data-stu-id="f2f54-106">You can define a common set of custom controls that are available to all the views of the formatting file, you can define custom controls that are available to a specific view, or you can define a set of controls that are available to a group of objects.</span></span>

## <a name="custom-control-example"></a><span data-ttu-id="f2f54-107">Voor beeld van aangepast besturings element</span><span class="sxs-lookup"><span data-stu-id="f2f54-107">Custom Control Example</span></span>

<span data-ttu-id="f2f54-108">In het volgende voor beeld ziet u een aangepast besturings element dat is gedefinieerd in het Certificates.Format.ps1XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="f2f54-108">The following example shows a custom control that is defined in the Certificates.Format.ps1xml file.</span></span> <span data-ttu-id="f2f54-109">Dit aangepaste besturings element wordt gebruikt om de objecten [System. Management. Automation. Signature](/dotnet/api/System.Management.Automation.Signature) te scheiden die in een tabel weergave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f2f54-109">This custom control is used to separate the [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objects displayed in a table view.</span></span>

```xml
<Controls>
  <Control>
    <Name>SignatureTypes-GroupingFormat</Name>
    <CustomControl>
      <CustomEntries>
        <CustomEntry>
          <CustomItem>
            <Frame>
              <LeftIndent>4</LeftIndent>
              <CustomItem>
                <Text AssemblyName="System.Management.Automation" BaseName="FileSystemProviderStrings"
                  ResourceId="DirectoryDisplayGrouping"/>
                <ExpressionBinding>
                  <ScriptBlock>split-path $_.Path</ScriptBlock>
                </ExpressionBinding>
                <NewLine/>
              </CustomItem>
            </Frame>
          </CustomItem>
        </CustomEntry>
      </CustomEntries>
    </CustomControl>
  </Control>
</Controls>

```

## <a name="see-also"></a><span data-ttu-id="f2f54-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f2f54-110">See Also</span></span>

[<span data-ttu-id="f2f54-111">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="f2f54-111">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
