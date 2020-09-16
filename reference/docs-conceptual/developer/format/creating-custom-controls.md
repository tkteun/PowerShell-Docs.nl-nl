---
title: Aangepaste besturings elementen maken | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c36fa9b778e01501a3c88f735cdefdfbb04411a0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786115"
---
# <a name="creating-custom-controls"></a><span data-ttu-id="f732f-102">Aangepaste besturingselementen maken</span><span class="sxs-lookup"><span data-stu-id="f732f-102">Creating Custom Controls</span></span>

<span data-ttu-id="f732f-103">Aangepaste besturings elementen zijn de meest flexibele onderdelen van een opmaak bestand.</span><span class="sxs-lookup"><span data-stu-id="f732f-103">Custom controls are the most flexible components of a formatting file.</span></span> <span data-ttu-id="f732f-104">In tegens telling tot tabel-, lijst-en brede weer gaven waarin een formele structuur van gegevens wordt gedefinieerd, zoals een tabel met gegevens, kunt u met aangepaste besturings elementen definiëren hoe een afzonderlijke hoeveelheid gegevens wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f732f-104">Unlike table, list, and wide views that define a formal structure of data, such as a table of data, custom controls allow you to define how an individual piece of data is displayed.</span></span> <span data-ttu-id="f732f-105">U kunt een algemene set aangepaste besturings elementen definiëren die beschikbaar zijn voor alle weer gaven van het opmaak bestand, u kunt aangepaste besturings elementen definiëren die beschikbaar zijn voor een specifieke weer gave of u kunt een set besturings elementen definiëren die beschikbaar zijn voor een groep objecten.</span><span class="sxs-lookup"><span data-stu-id="f732f-105">You can define a common set of custom controls that are available to all the views of the formatting file, you can define custom controls that are available to a specific view, or you can define a set of controls that are available to a group of objects.</span></span>

## <a name="custom-control-example"></a><span data-ttu-id="f732f-106">Voor beeld van aangepast besturings element</span><span class="sxs-lookup"><span data-stu-id="f732f-106">Custom Control Example</span></span>

<span data-ttu-id="f732f-107">In het volgende voor beeld ziet u een aangepast besturings element dat is gedefinieerd in het Certificates.Format.ps1XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="f732f-107">The following example shows a custom control that is defined in the Certificates.Format.ps1xml file.</span></span> <span data-ttu-id="f732f-108">Dit aangepaste besturings element wordt gebruikt om de objecten [System. Management. Automation. Signature](/dotnet/api/System.Management.Automation.Signature) te scheiden die in een tabel weergave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f732f-108">This custom control is used to separate the [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objects displayed in a table view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f732f-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f732f-109">See Also</span></span>

[<span data-ttu-id="f732f-110">Een PowerShell-opmaakbestand schrijven</span><span class="sxs-lookup"><span data-stu-id="f732f-110">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
