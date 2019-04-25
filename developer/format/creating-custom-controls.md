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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066682"
---
# <a name="creating-custom-controls"></a>Aangepaste besturingselementen maken

Aangepaste besturingselementen zijn het meest flexibele onderdelen van een opmaak-bestand. In tegenstelling tot de tabel, lijst en breed weergaven die een formele structuur van gegevens, zoals een tabel met gegevens definieert, kunt aangepaste besturingselementen u definiëren hoe een individueel gedeelte met gegevens wordt weergegeven. U kunt een gemeenschappelijke set aangepaste besturingselementen die beschikbaar voor alle weergaven van de opmaak bestand zijn definiëren, kunt u aangepaste besturingselementen die beschikbaar voor een specifieke weergave zijn definiëren of kunt u een set besturingselementen die beschikbaar voor een groep objecten zijn.

## <a name="custom-control-example"></a>Voorbeeld van het aangepaste besturingselement

Het volgende voorbeeld ziet een aangepast besturingselement dat is gedefinieerd in het bestand Certificates.Format.ps1xml. Deze aangepaste besturingselementen wordt gebruikt voor het scheiden van de [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objecten in een tabel weergegeven.

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

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
