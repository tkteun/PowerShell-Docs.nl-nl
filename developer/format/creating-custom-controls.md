---
title: Het maken van aangepaste besturingselementen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3baa406-cd33-4420-be5a-07ef09d93480
caps.latest.revision: 8
ms.openlocfilehash: 3504ab1d974c55e9279172d0e851961474ccb926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844847"
---
# <a name="creating-custom-controls"></a><span data-ttu-id="fa17f-102">Aangepaste besturingselementen maken</span><span class="sxs-lookup"><span data-stu-id="fa17f-102">Creating Custom Controls</span></span>

<span data-ttu-id="fa17f-103">Aangepaste besturingselementen zijn het meest flexibele onderdelen van een opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="fa17f-103">Custom controls are the most flexible components of a formatting file.</span></span> <span data-ttu-id="fa17f-104">In tegenstelling tot de tabel, lijst en breed weergaven die een formele structuur van gegevens, zoals een tabel met gegevens definieert, kunt aangepaste besturingselementen u definiëren hoe een individueel gedeelte met gegevens wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="fa17f-104">Unlike table, list, and wide views that define a formal structure of data, such as a table of data, custom controls allow you to define how an individual piece of data is displayed.</span></span> <span data-ttu-id="fa17f-105">U kunt een gemeenschappelijke set aangepaste besturingselementen die beschikbaar voor alle weergaven van de opmaak bestand zijn definiëren, kunt u aangepaste besturingselementen die beschikbaar voor een specifieke weergave zijn definiëren of kunt u een set besturingselementen die beschikbaar voor een groep objecten zijn.</span><span class="sxs-lookup"><span data-stu-id="fa17f-105">You can define a common set of custom controls that are available to all the views of the formatting file, you can define custom controls that are available to a specific view, or you can define a set of controls that are available to a group of objects.</span></span>

## <a name="custom-control-example"></a><span data-ttu-id="fa17f-106">Voorbeeld van het aangepaste besturingselement</span><span class="sxs-lookup"><span data-stu-id="fa17f-106">Custom Control Example</span></span>

<span data-ttu-id="fa17f-107">Het volgende voorbeeld ziet een aangepast besturingselement dat is gedefinieerd in het bestand Certificates.Format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="fa17f-107">The following example shows a custom control that is defined in the Certificates.Format.ps1xml file.</span></span> <span data-ttu-id="fa17f-108">Deze aangepaste besturingselementen wordt gebruikt voor het scheiden van de [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objecten in een tabel weergegeven.</span><span class="sxs-lookup"><span data-stu-id="fa17f-108">This custom control is used to separate the [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objects displayed in a table view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fa17f-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fa17f-109">See Also</span></span>

[<span data-ttu-id="fa17f-110">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="fa17f-110">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
