---
title: Dynamische Parameters toevoegen aan een Help-onderwerp Provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849523"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Dynamische parameters toevoegen aan een Help-onderwerp over providers

In deze sectie wordt uitgelegd hoe u voor het vullen van de **dynamische PARAMETERS** gedeelte van een provider help-onderwerp.

*Dynamische parameters* parameters van een cmdlet of functie die beschikbaar zijn alleen onder de opgegeven voorwaarden.

De dynamische parameters die worden beschreven in een provider help-onderwerp zijn de dynamische parameters waarmee de provider wordt toegevoegd aan de cmdlet of functie wanneer de cmdlet of de functie wordt gebruikt in het station van de provider.

Dynamische parameters kunnen ook worden beschreven in de aangepaste cmdlet help voor een provider. Bij het schrijven van zowel provider help en aangepaste cmdlet help voor een provider, moet u de documentatie van de dynamische parameter opnemen in beide documenten. Zie voor meer informatie over aangepaste cmdlet help [schrijven Windows PowerShell aangepaste Cmdlet Help voor Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).

Als een provider wordt niet geïmplementeerd voor dynamische parameters, de provider help-onderwerp bevat een lege `DynamicParameters` element.

### <a name="to-add-dynamic-parameters"></a>Dynamische Parameters toevoegen

1. In de *AssemblyName*.dll-help.xml-bestand, vanuit de `providerHelp` element toevoegen een `DynamicParameters` element. De `DynamicParameters` element moet worden weergegeven na de `Tasks` element en voordat de `RelatedLinks` element.

   Bijvoorbeeld:

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   Als de provider wordt niet geïmplementeerd voor dynamische parameters, de `DynamicParameters` element kan niet leeg zijn.

2. Binnen de `DynamicParameters` -element voor elk dynamische parameter toevoegen een `DynamicParameter` element.

   Bijvoorbeeld:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. In elk `DynamicParameter` -element, Voeg een `Name` en `CmdletSupported` element.

   |Naam van element|Description|
   |------------------|-----------------|
   |Naam|Hiermee geeft u de parameternaam van de.|
   |CmdletSupported|Hiermee geeft u de cmdlets waarbij de parameter geldig is. Typ een door komma's gescheiden lijst met namen van de cmdlets.|

   Bijvoorbeeld, de volgende XML-documenten de `Encoding` dynamische parameter waarmee het bestandssysteem van Windows PowerShell-provider wordt toegevoegd aan de `Add-Content`, `Get-Content`, `Set-Content` cmdlets.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. In elk `DynamicParameter` -element, Voeg een `Type` element. De `Type` element is een container voor de `Name` element waarin het .NET-type van de waarde van de dynamische parameter.

   Bijvoorbeeld, het volgende XML-bestand ziet u dat het .NET-type van de `Encoding` dynamische parameter wordt de [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) opsomming.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

5. Voeg de `Description` -element een korte beschrijving van de dynamische parameter bevat. Bij het samenstellen van de beschrijving, gebruikt u de richtlijnen voor alle cmdlet-parameters in voorgeschreven [over het toevoegen van parameterinformatie](./how-to-add-parameter-information.md).

   Het volgende XML-bestand bevat bijvoorbeeld de beschrijving van de `Encoding` dynamische parameter.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

6. Voeg de `PossibleValues` -element en de onderliggende elementen. Deze elementen beschrijven samen de waarden van de dynamische parameter. Dit element is ontworpen voor opsommingswaarden zijn. Als de dynamische parameter neemt een waarde, zoals het geval is bij een switch-parameter is of de waarden kunnen niet worden geïnventariseerd, toevoegen van een lege `PossibleValues` element.

   De volgende tabel geeft een lijst van en beschrijft de `PossibleValues` -element en de onderliggende elementen.

   |Naam van element|Description|
   |------------------|-----------------|
   |PossibleValues|Dit element is een container. De onderliggende elementen worden hieronder beschreven. Voeg een `PossibleValues` element elke provider help-onderwerp. Het element kan niet leeg zijn.|
   |PossibleValue|Dit element is een container. De onderliggende elementen worden hieronder beschreven. Voeg een `PossibleValue` -element voor elke waarde van de dynamische parameter.|
   |Waarde|Hiermee geeft u de naam van de.|
   |Description|Dit element bevat een `Para` element. De tekst in de `Para` element wordt aangegeven wat de meerwaarde met de naam in de `Value` element.|

   Het volgende XML-bestand ziet u bijvoorbeeld een `PossibleValue` element van de `Encoding` dynamische parameter.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld wordt de `DynamicParameters` element van de `Encoding` dynamische parameter.

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```