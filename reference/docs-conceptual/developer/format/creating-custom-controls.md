---
title: Aangepaste besturings elementen maken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3baa406-cd33-4420-be5a-07ef09d93480
caps.latest.revision: 8
ms.openlocfilehash: 3504ab1d974c55e9279172d0e851961474ccb926
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354787"
---
# <a name="creating-custom-controls"></a>Aangepaste besturingselementen maken

Aangepaste besturings elementen zijn de meest flexibele onderdelen van een opmaak bestand. In tegens telling tot tabel-, lijst-en brede weer gaven waarin een formele structuur van gegevens wordt gedefinieerd, zoals een tabel met gegevens, kunt u met aangepaste besturings elementen definiëren hoe een afzonderlijke hoeveelheid gegevens wordt weer gegeven. U kunt een algemene set aangepaste besturings elementen definiëren die beschikbaar zijn voor alle weer gaven van het opmaak bestand, u kunt aangepaste besturings elementen definiëren die beschikbaar zijn voor een specifieke weer gave of u kunt een set besturings elementen definiëren die beschikbaar zijn voor een groep objecten.

## <a name="custom-control-example"></a>Voor beeld van aangepast besturings element

In het volgende voor beeld ziet u een aangepast besturings element dat is gedefinieerd in het bestand certificates. Format. ps1xml. Dit aangepaste besturings element wordt gebruikt om de objecten [System. Management. Automation. Signature](/dotnet/api/System.Management.Automation.Signature) te scheiden die in een tabel weergave worden weer gegeven.

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

## <a name="see-also"></a>Zie ook

[Een Power shell-indelings bestand schrijven](./writing-a-powershell-formatting-file.md)
