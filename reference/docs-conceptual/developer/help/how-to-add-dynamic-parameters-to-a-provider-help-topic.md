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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353303"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Dynamische parameters toevoegen aan een Help-onderwerp over providers

In deze sectie wordt uitgelegd hoe u de sectie **dynamische para meters** van een Help-onderwerp van een provider vult.

*Dynamische para meters* zijn para meters van een cmdlet of functie die alleen beschikbaar zijn onder opgegeven voor waarden.

De dynamische para meters die zijn gedocumenteerd in het Help-onderwerp van de provider zijn de dynamische para meters die de provider toevoegt aan de cmdlet of functie wanneer de cmdlet of functie wordt gebruikt in het provider station.

Dynamische para meters kunnen ook worden gedocumenteerd in de Help voor aangepaste cmdlets voor een provider. Wanneer u de Help van de provider en aangepaste cmdlet-Help voor een provider schrijft, neemt u de dynamische parameter documentatie op in beide documenten.

Als een provider geen dynamische para meters implementeert, bevat het Help-onderwerp van de provider een leeg `DynamicParameters`-element.

### <a name="to-add-dynamic-parameters"></a>Dynamische para meters toevoegen

1. Voeg in het bestand *assemblyname*. dll-Help. XML binnen het element `providerHelp` een `DynamicParameters`-element toe. Het element `DynamicParameters` moet worden weer gegeven na het element `Tasks` en vóór het element `RelatedLinks`.

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

   Als de provider geen dynamische para meters implementeert, mag het element `DynamicParameters` leeg zijn.

2. Voeg binnen het element `DynamicParameters`, voor elke dynamische para meter, een `DynamicParameter`-element toe.

   Bijvoorbeeld:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. Voeg in elk element `DynamicParameter` een `Name`-en `CmdletSupported`-element toe.

   |Naam van element|Beschrijving|
   |------------------|-----------------|
   |Naam|Hiermee geeft u de parameter naam.|
   |CmdletSupported|Hiermee geeft u de cmdlets op waarin de para meter geldig is. Typ een door komma's gescheiden lijst met cmdlet-namen.|

   Met de volgende XML-bestanden wordt bijvoorbeeld de `Encoding`-para meter die de Windows Power shell-bestandssysteem provider toevoegt aan de `Add-Content`, `Get-Content`, `Set-Content`-cmdlets.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. Voeg in elk element `DynamicParameter` een `Type`-element toe. Het element `Type` is een container voor het element `Name` dat het .NET-type van de waarde van de dynamische para meter bevat.

   Het volgende XML-bestand laat bijvoorbeeld zien dat het .NET-type van de dynamische para meter `Encoding` is de opsomming van [micro soft. Power shell. commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .

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

5. Voeg het element `Description` toe, dat een korte beschrijving van de dynamische para meter bevat. Gebruik bij het samen stellen van de beschrijving de richt lijnen die zijn vastgelegd voor alle cmdlet-para meters bij [het toevoegen van parameter informatie](./how-to-add-parameter-information.md).

   De volgende XML bevat bijvoorbeeld de beschrijving van de dynamische para meter `Encoding`.

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

6. Voeg het element `PossibleValues` en de onderliggende elementen toe. Samen beschrijven deze elementen de waarden van de dynamische para meter. Dit element is ontworpen voor opsommings waarden. Als de dynamische para meter geen waarde heeft, zoals het geval is met een switch parameter, of als de waarden niet kunnen worden geïnventariseerd, voegt u een leeg `PossibleValues`-element toe.

   In de volgende tabel worden het element `PossibleValues` en de onderliggende elementen ervan beschreven.

   |Naam van element|Beschrijving|
   |------------------|-----------------|
   |PossibleValues|Dit element is een container. De onderliggende elementen worden hieronder beschreven. Voeg één `PossibleValues`-element toe aan elk provider Help-onderwerp. Het element mag leeg zijn.|
   |PossibleValue|Dit element is een container. De onderliggende elementen worden hieronder beschreven. Voeg één `PossibleValue`-element toe voor elke waarde van de dynamische para meter.|
   |Value|Hiermee geeft u de naam van de waarde.|
   |Beschrijving|Dit element bevat een element `Para`. De tekst in het element `Para` beschrijft de waarde die wordt genoemd in het element `Value`.|

   In het volgende XML-bestand ziet u bijvoorbeeld één `PossibleValue`-element van de para meter `Encoding` Dynamic.

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

In het volgende voor beeld wordt het element `DynamicParameters` van de dynamische para meter `Encoding` weer gegeven.

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