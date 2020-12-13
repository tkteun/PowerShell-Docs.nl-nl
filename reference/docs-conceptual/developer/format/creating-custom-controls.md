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
# <a name="creating-custom-controls"></a>Aangepaste besturingselementen maken

Aangepaste besturings elementen zijn de meest flexibele onderdelen van een opmaak bestand. In tegens telling tot tabel-, lijst-en brede weer gaven waarin een formele structuur van gegevens wordt gedefinieerd, zoals een tabel met gegevens, kunt u met aangepaste besturings elementen definiëren hoe een afzonderlijke hoeveelheid gegevens wordt weer gegeven. U kunt een algemene set aangepaste besturings elementen definiëren die beschikbaar zijn voor alle weer gaven van het opmaak bestand, u kunt aangepaste besturings elementen definiëren die beschikbaar zijn voor een specifieke weer gave of u kunt een set besturings elementen definiëren die beschikbaar zijn voor een groep objecten.

## <a name="custom-control-example"></a>Voor beeld van aangepast besturings element

In het volgende voor beeld ziet u een aangepast besturings element dat is gedefinieerd in het Certificates.Format.ps1XML-bestand. Dit aangepaste besturings element wordt gebruikt om de objecten [System. Management. Automation. Signature](/dotnet/api/System.Management.Automation.Signature) te scheiden die in een tabel weergave worden weer gegeven.

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

[Een PowerShell-opmaakbestand schrijven](./writing-a-powershell-formatting-file.md)
