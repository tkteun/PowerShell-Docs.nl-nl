---
title: Dynamische para meters toevoegen aan het Help-onderwerp van een provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: 59839e9b8b6f2a56f2f1a9c755f2f1a85deb34aa
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848112"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Dynamische parameters toevoegen aan een Help-onderwerp over providers

In deze sectie wordt uitgelegd hoe u de sectie **dynamische para meters** van een Help-onderwerp van een provider vult.

*Dynamische para meters* zijn para meters van een cmdlet of functie die alleen beschikbaar zijn onder opgegeven voor waarden.

De dynamische para meters die zijn gedocumenteerd in het Help-onderwerp van de provider zijn de dynamische para meters die de provider toevoegt aan de cmdlet of functie wanneer de cmdlet of functie wordt gebruikt in het provider station.

Dynamische para meters kunnen ook worden gedocumenteerd in de Help voor aangepaste cmdlets voor een provider. Wanneer u de Help van de provider en aangepaste cmdlet-Help voor een provider schrijft, neemt u de dynamische parameter documentatie op in beide documenten.

Als een provider geen dynamische para meters implementeert, bevat het Help-onderwerp van `DynamicParameters` de provider een leeg element.

### <a name="to-add-dynamic-parameters"></a>Dynamische para meters toevoegen

1. Voeg in het bestand *assemblyname*. dll-Help. XML binnen het `providerHelp` -element een `DynamicParameters` -element toe. Het `DynamicParameters` element moet na het `Tasks` element en vóór het `RelatedLinks` element worden weer gegeven.

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

   Als de provider geen dynamische para meters implementeert, `DynamicParameters` mag het element leeg zijn.

2. In het `DynamicParameters` -element voegt u voor elke dynamische para meter `DynamicParameter` een-element toe.

   Bijvoorbeeld:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. Voeg in `DynamicParameter` elk-element een `Name` - `CmdletSupported` element en toe.

   |Naam van element|Description|
   |------------------|-----------------|
   |Naam|Hiermee geeft u de parameter naam.|
   |CmdletSupported|Hiermee geeft u de cmdlets op waarin de para meter geldig is. Typ een door komma's gescheiden lijst met cmdlet-namen.|

   Met de volgende XML-code wordt bijvoorbeeld `Encoding` de dynamische para meter gedocumenteerd die de Windows Power shell- `Add-Content` `Get-Content` `Set-Content` bestandssysteem provider toevoegt aan de cmdlets.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. Voeg in `DynamicParameter` elk element een `Type` -element toe. Het `Type` element is een container voor het `Name` element dat het .net-type van de waarde van de dynamische para meter bevat.

   De volgende XML laat bijvoorbeeld zien dat het .net-type van de `Encoding` dynamische para meter de [micro soft. Power shell. commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) -inventarisatie.

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

5. Voeg het `Description` element toe, dat een korte beschrijving van de dynamische para meter bevat. Gebruik bij het samen stellen van de beschrijving de richt lijnen die zijn vastgelegd voor alle cmdlet-para meters bij [het toevoegen van parameter informatie](./how-to-add-parameter-information.md).

   De volgende XML bevat bijvoorbeeld de beschrijving van de `Encoding` dynamische para meter.

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

6. Voeg het `PossibleValues` element en de onderliggende elementen toe. Samen beschrijven deze elementen de waarden van de dynamische para meter. Dit element is ontworpen voor opsommings waarden. Als de dynamische para meter geen waarde heeft, zoals het geval is met een switch parameter, of als de waarden niet kunnen worden geïnventariseerd, voegt u een leeg `PossibleValues` element toe.

   In de volgende tabel worden het `PossibleValues` element en de onderliggende elementen ervan beschreven.

   |Naam van element|Description|
   |------------------|-----------------|
   |PossibleValues|Dit element is een container. De onderliggende elementen worden hieronder beschreven. Voeg één `PossibleValues` element toe aan elk provider Help-onderwerp. Het element mag leeg zijn.|
   |PossibleValue|Dit element is een container. De onderliggende elementen worden hieronder beschreven. Voeg één `PossibleValue` element toe voor elke waarde van de dynamische para meter.|
   |Waarde|Hiermee geeft u de naam van de waarde.|
   |Description|Dit element bevat een `Para` -element. De tekst in het `Para` element beschrijft de waarde die in het `Value` element wordt genoemd.|

   De volgende XML-code bevat bijvoorbeeld één `PossibleValue` element van de `Encoding` dynamische para meter.

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

In het volgende voor beeld `DynamicParameters` wordt het element `Encoding` van de dynamische para meter weer gegeven.

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