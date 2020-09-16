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
