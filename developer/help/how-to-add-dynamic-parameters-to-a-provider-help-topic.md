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
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="aac32-102">Dynamische parameters toevoegen aan een Help-onderwerp over providers</span><span class="sxs-lookup"><span data-stu-id="aac32-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="aac32-103">In deze sectie wordt uitgelegd hoe u de sectie **dynamische para meters** van een Help-onderwerp van een provider vult.</span><span class="sxs-lookup"><span data-stu-id="aac32-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="aac32-104">*Dynamische para meters* zijn para meters van een cmdlet of functie die alleen beschikbaar zijn onder opgegeven voor waarden.</span><span class="sxs-lookup"><span data-stu-id="aac32-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="aac32-105">De dynamische para meters die zijn gedocumenteerd in het Help-onderwerp van de provider zijn de dynamische para meters die de provider toevoegt aan de cmdlet of functie wanneer de cmdlet of functie wordt gebruikt in het provider station.</span><span class="sxs-lookup"><span data-stu-id="aac32-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="aac32-106">Dynamische para meters kunnen ook worden gedocumenteerd in de Help voor aangepaste cmdlets voor een provider.</span><span class="sxs-lookup"><span data-stu-id="aac32-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="aac32-107">Wanneer u de Help van de provider en aangepaste cmdlet-Help voor een provider schrijft, neemt u de dynamische parameter documentatie op in beide documenten.</span><span class="sxs-lookup"><span data-stu-id="aac32-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="aac32-108">Als een provider geen dynamische para meters implementeert, bevat het Help-onderwerp van `DynamicParameters` de provider een leeg element.</span><span class="sxs-lookup"><span data-stu-id="aac32-108">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="aac32-109">Dynamische para meters toevoegen</span><span class="sxs-lookup"><span data-stu-id="aac32-109">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="aac32-110">Voeg in het bestand *assemblyname*. dll-Help. XML binnen het `providerHelp` -element een `DynamicParameters` -element toe.</span><span class="sxs-lookup"><span data-stu-id="aac32-110">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="aac32-111">Het `DynamicParameters` element moet na het `Tasks` element en vóór het `RelatedLinks` element worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="aac32-111">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="aac32-112">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="aac32-112">For example:</span></span>

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

   <span data-ttu-id="aac32-113">Als de provider geen dynamische para meters implementeert, `DynamicParameters` mag het element leeg zijn.</span><span class="sxs-lookup"><span data-stu-id="aac32-113">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="aac32-114">In het `DynamicParameters` -element voegt u voor elke dynamische para meter `DynamicParameter` een-element toe.</span><span class="sxs-lookup"><span data-stu-id="aac32-114">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="aac32-115">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="aac32-115">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="aac32-116">Voeg in `DynamicParameter` elk-element een `Name` - `CmdletSupported` element en toe.</span><span class="sxs-lookup"><span data-stu-id="aac32-116">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="aac32-117">Naam van element</span><span class="sxs-lookup"><span data-stu-id="aac32-117">Element Name</span></span>|<span data-ttu-id="aac32-118">Description</span><span class="sxs-lookup"><span data-stu-id="aac32-118">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="aac32-119">Naam</span><span class="sxs-lookup"><span data-stu-id="aac32-119">Name</span></span>|<span data-ttu-id="aac32-120">Hiermee geeft u de parameter naam.</span><span class="sxs-lookup"><span data-stu-id="aac32-120">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="aac32-121">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="aac32-121">CmdletSupported</span></span>|<span data-ttu-id="aac32-122">Hiermee geeft u de cmdlets op waarin de para meter geldig is.</span><span class="sxs-lookup"><span data-stu-id="aac32-122">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="aac32-123">Typ een door komma's gescheiden lijst met cmdlet-namen.</span><span class="sxs-lookup"><span data-stu-id="aac32-123">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="aac32-124">Met de volgende XML-code wordt bijvoorbeeld `Encoding` de dynamische para meter gedocumenteerd die de Windows Power shell- `Add-Content` `Get-Content` `Set-Content` bestandssysteem provider toevoegt aan de cmdlets.</span><span class="sxs-lookup"><span data-stu-id="aac32-124">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="aac32-125">Voeg in `DynamicParameter` elk element een `Type` -element toe.</span><span class="sxs-lookup"><span data-stu-id="aac32-125">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="aac32-126">Het `Type` element is een container voor het `Name` element dat het .net-type van de waarde van de dynamische para meter bevat.</span><span class="sxs-lookup"><span data-stu-id="aac32-126">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="aac32-127">De volgende XML laat bijvoorbeeld zien dat het .net-type van de `Encoding` dynamische para meter de [micro soft. Power shell. commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) -inventarisatie.</span><span class="sxs-lookup"><span data-stu-id="aac32-127">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="aac32-128">Voeg het `Description` element toe, dat een korte beschrijving van de dynamische para meter bevat.</span><span class="sxs-lookup"><span data-stu-id="aac32-128">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="aac32-129">Gebruik bij het samen stellen van de beschrijving de richt lijnen die zijn vastgelegd voor alle cmdlet-para meters bij [het toevoegen van parameter informatie](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="aac32-129">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="aac32-130">De volgende XML bevat bijvoorbeeld de beschrijving van de `Encoding` dynamische para meter.</span><span class="sxs-lookup"><span data-stu-id="aac32-130">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="aac32-131">Voeg het `PossibleValues` element en de onderliggende elementen toe.</span><span class="sxs-lookup"><span data-stu-id="aac32-131">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="aac32-132">Samen beschrijven deze elementen de waarden van de dynamische para meter.</span><span class="sxs-lookup"><span data-stu-id="aac32-132">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="aac32-133">Dit element is ontworpen voor opsommings waarden.</span><span class="sxs-lookup"><span data-stu-id="aac32-133">This element is designed for enumerated values.</span></span> <span data-ttu-id="aac32-134">Als de dynamische para meter geen waarde heeft, zoals het geval is met een switch parameter, of als de waarden niet kunnen worden geïnventariseerd, voegt u een leeg `PossibleValues` element toe.</span><span class="sxs-lookup"><span data-stu-id="aac32-134">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="aac32-135">In de volgende tabel worden het `PossibleValues` element en de onderliggende elementen ervan beschreven.</span><span class="sxs-lookup"><span data-stu-id="aac32-135">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="aac32-136">Naam van element</span><span class="sxs-lookup"><span data-stu-id="aac32-136">Element Name</span></span>|<span data-ttu-id="aac32-137">Description</span><span class="sxs-lookup"><span data-stu-id="aac32-137">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="aac32-138">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="aac32-138">PossibleValues</span></span>|<span data-ttu-id="aac32-139">Dit element is een container.</span><span class="sxs-lookup"><span data-stu-id="aac32-139">This element is a container.</span></span> <span data-ttu-id="aac32-140">De onderliggende elementen worden hieronder beschreven.</span><span class="sxs-lookup"><span data-stu-id="aac32-140">Its child elements are described below.</span></span> <span data-ttu-id="aac32-141">Voeg één `PossibleValues` element toe aan elk provider Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="aac32-141">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="aac32-142">Het element mag leeg zijn.</span><span class="sxs-lookup"><span data-stu-id="aac32-142">The element can be empty.</span></span>|
   |<span data-ttu-id="aac32-143">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="aac32-143">PossibleValue</span></span>|<span data-ttu-id="aac32-144">Dit element is een container.</span><span class="sxs-lookup"><span data-stu-id="aac32-144">This element is a container.</span></span> <span data-ttu-id="aac32-145">De onderliggende elementen worden hieronder beschreven.</span><span class="sxs-lookup"><span data-stu-id="aac32-145">Its child elements are described below.</span></span> <span data-ttu-id="aac32-146">Voeg één `PossibleValue` element toe voor elke waarde van de dynamische para meter.</span><span class="sxs-lookup"><span data-stu-id="aac32-146">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="aac32-147">Waarde</span><span class="sxs-lookup"><span data-stu-id="aac32-147">Value</span></span>|<span data-ttu-id="aac32-148">Hiermee geeft u de naam van de waarde.</span><span class="sxs-lookup"><span data-stu-id="aac32-148">Specifies the value name.</span></span>|
   |<span data-ttu-id="aac32-149">Description</span><span class="sxs-lookup"><span data-stu-id="aac32-149">Description</span></span>|<span data-ttu-id="aac32-150">Dit element bevat een `Para` -element.</span><span class="sxs-lookup"><span data-stu-id="aac32-150">This element contains a `Para` element.</span></span> <span data-ttu-id="aac32-151">De tekst in het `Para` element beschrijft de waarde die in het `Value` element wordt genoemd.</span><span class="sxs-lookup"><span data-stu-id="aac32-151">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="aac32-152">De volgende XML-code bevat bijvoorbeeld één `PossibleValue` element van de `Encoding` dynamische para meter.</span><span class="sxs-lookup"><span data-stu-id="aac32-152">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="aac32-153">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="aac32-153">Example</span></span>

<span data-ttu-id="aac32-154">In het volgende voor beeld `DynamicParameters` wordt het element `Encoding` van de dynamische para meter weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="aac32-154">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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