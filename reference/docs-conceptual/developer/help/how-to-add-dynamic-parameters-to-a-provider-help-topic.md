---
title: Dynamische parameters toevoegen aan een Help-onderwerp over providers
ms.date: 09/13/2016
ms.openlocfilehash: ddf964292ee7bf477767a2ca17c717aef84bad51
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893455"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="11dd0-102">Dynamische parameters toevoegen aan een Help-onderwerp over providers</span><span class="sxs-lookup"><span data-stu-id="11dd0-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="11dd0-103">In deze sectie wordt uitgelegd hoe u de sectie **dynamische para meters** van een Help-onderwerp van een provider vult.</span><span class="sxs-lookup"><span data-stu-id="11dd0-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="11dd0-104">*Dynamische para meters* zijn para meters van een cmdlet of functie die alleen beschikbaar zijn onder opgegeven voor waarden.</span><span class="sxs-lookup"><span data-stu-id="11dd0-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="11dd0-105">De dynamische para meters die zijn gedocumenteerd in het Help-onderwerp van de provider zijn de dynamische para meters die de provider toevoegt aan de cmdlet of functie wanneer de cmdlet of functie wordt gebruikt in het provider station.</span><span class="sxs-lookup"><span data-stu-id="11dd0-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="11dd0-106">Dynamische para meters kunnen ook worden gedocumenteerd in de Help voor aangepaste cmdlets voor een provider.</span><span class="sxs-lookup"><span data-stu-id="11dd0-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="11dd0-107">Wanneer u de Help van de provider en aangepaste cmdlet-Help voor een provider schrijft, neemt u de dynamische parameter documentatie op in beide documenten.</span><span class="sxs-lookup"><span data-stu-id="11dd0-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="11dd0-108">Als een provider geen dynamische para meters implementeert, bevat het Help-onderwerp van de provider een leeg `DynamicParameters` element.</span><span class="sxs-lookup"><span data-stu-id="11dd0-108">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="11dd0-109">Dynamische para meters toevoegen</span><span class="sxs-lookup"><span data-stu-id="11dd0-109">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="11dd0-110">Voeg in het `<AssemblyName>.dll-help.xml` bestand, binnen het `providerHelp` element, een- `DynamicParameters` element toe.</span><span class="sxs-lookup"><span data-stu-id="11dd0-110">In the `<AssemblyName>.dll-help.xml` file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="11dd0-111">Het `DynamicParameters` element moet na het `Tasks` element en vóór het element worden weer gegeven `RelatedLinks` .</span><span class="sxs-lookup"><span data-stu-id="11dd0-111">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="11dd0-112">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="11dd0-112">For example:</span></span>

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

   <span data-ttu-id="11dd0-113">Als de provider geen dynamische para meters implementeert, `DynamicParameters` mag het element leeg zijn.</span><span class="sxs-lookup"><span data-stu-id="11dd0-113">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

1. <span data-ttu-id="11dd0-114">In het `DynamicParameters` -element voegt u voor elke dynamische para meter een- `DynamicParameter` element toe.</span><span class="sxs-lookup"><span data-stu-id="11dd0-114">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="11dd0-115">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="11dd0-115">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

1. <span data-ttu-id="11dd0-116">Voeg in elk `DynamicParameter` -element een `Name` - `CmdletSupported` element en toe.</span><span class="sxs-lookup"><span data-stu-id="11dd0-116">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   - <span data-ttu-id="11dd0-117">Naam: Hiermee geeft u de parameter naam op</span><span class="sxs-lookup"><span data-stu-id="11dd0-117">Name - Specifies the parameter name</span></span>
   - <span data-ttu-id="11dd0-118">CmdletSupported: Hiermee geeft u de cmdlets op waarin de para meter geldig is.</span><span class="sxs-lookup"><span data-stu-id="11dd0-118">CmdletSupported - Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="11dd0-119">Typ een door komma's gescheiden lijst met cmdlet-namen.</span><span class="sxs-lookup"><span data-stu-id="11dd0-119">Type a comma-separated list of cmdlet names.</span></span>

   <span data-ttu-id="11dd0-120">Met de volgende XML-code wordt bijvoorbeeld de `Encoding` dynamische para meter gedocumenteerd die de Windows Power shell-bestandssysteem provider toevoegt aan de `Add-Content` `Get-Content` `Set-Content` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="11dd0-120">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

1. <span data-ttu-id="11dd0-121">Voeg in elk `DynamicParameter` element een- `Type` element toe.</span><span class="sxs-lookup"><span data-stu-id="11dd0-121">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="11dd0-122">Het `Type` element is een container voor het `Name` element dat het .net-type van de waarde van de dynamische para meter bevat.</span><span class="sxs-lookup"><span data-stu-id="11dd0-122">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="11dd0-123">De volgende XML laat bijvoorbeeld zien dat het .NET-type van de `Encoding` dynamische para meter de [FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) -inventarisatie is.</span><span class="sxs-lookup"><span data-stu-id="11dd0-123">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

1. <span data-ttu-id="11dd0-124">Voeg het `Description` element toe, dat een korte beschrijving van de dynamische para meter bevat.</span><span class="sxs-lookup"><span data-stu-id="11dd0-124">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="11dd0-125">Gebruik bij het samen stellen van de beschrijving de richt lijnen die zijn vastgelegd voor alle cmdlet-para meters bij [het toevoegen van parameter informatie](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="11dd0-125">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="11dd0-126">De volgende XML bevat bijvoorbeeld de beschrijving van de `Encoding` dynamische para meter.</span><span class="sxs-lookup"><span data-stu-id="11dd0-126">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

1. <span data-ttu-id="11dd0-127">Voeg het `PossibleValues` element en de onderliggende elementen toe.</span><span class="sxs-lookup"><span data-stu-id="11dd0-127">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="11dd0-128">Samen beschrijven deze elementen de waarden van de dynamische para meter.</span><span class="sxs-lookup"><span data-stu-id="11dd0-128">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="11dd0-129">Dit element is ontworpen voor opsommings waarden.</span><span class="sxs-lookup"><span data-stu-id="11dd0-129">This element is designed for enumerated values.</span></span> <span data-ttu-id="11dd0-130">Als de dynamische para meter geen waarde heeft, zoals het geval is met een switch parameter, of als de waarden niet kunnen worden geïnventariseerd, voegt u een leeg `PossibleValues` element toe.</span><span class="sxs-lookup"><span data-stu-id="11dd0-130">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="11dd0-131">In de volgende tabel worden het `PossibleValues` element en de onderliggende elementen ervan beschreven.</span><span class="sxs-lookup"><span data-stu-id="11dd0-131">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   - <span data-ttu-id="11dd0-132">PossibleValues: dit element is een container.</span><span class="sxs-lookup"><span data-stu-id="11dd0-132">PossibleValues - This element is a container.</span></span> <span data-ttu-id="11dd0-133">De onderliggende elementen worden hieronder beschreven.</span><span class="sxs-lookup"><span data-stu-id="11dd0-133">Its child elements are described below.</span></span> <span data-ttu-id="11dd0-134">Voeg één `PossibleValues` element toe aan elk provider Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="11dd0-134">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="11dd0-135">Het element mag leeg zijn.</span><span class="sxs-lookup"><span data-stu-id="11dd0-135">The element can be empty.</span></span>
   - <span data-ttu-id="11dd0-136">PossibleValue: dit element is een container.</span><span class="sxs-lookup"><span data-stu-id="11dd0-136">PossibleValue - This element is a container.</span></span> <span data-ttu-id="11dd0-137">De onderliggende elementen worden hieronder beschreven.</span><span class="sxs-lookup"><span data-stu-id="11dd0-137">Its child elements are described below.</span></span> <span data-ttu-id="11dd0-138">Voeg één `PossibleValue` element toe voor elke waarde van de dynamische para meter.</span><span class="sxs-lookup"><span data-stu-id="11dd0-138">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>
   - <span data-ttu-id="11dd0-139">Waarde: Hiermee geeft u de naam van de waarde op.</span><span class="sxs-lookup"><span data-stu-id="11dd0-139">Value - Specifies the value name.</span></span>
   - <span data-ttu-id="11dd0-140">Beschrijving: dit element bevat een- `Para` element.</span><span class="sxs-lookup"><span data-stu-id="11dd0-140">Description - This element contains a `Para` element.</span></span> <span data-ttu-id="11dd0-141">De tekst in het `Para` element beschrijft de waarde die in het element wordt genoemd `Value` .</span><span class="sxs-lookup"><span data-stu-id="11dd0-141">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>

   <span data-ttu-id="11dd0-142">De volgende XML-code bevat bijvoorbeeld één `PossibleValue` element van de `Encoding` dynamische para meter.</span><span class="sxs-lookup"><span data-stu-id="11dd0-142">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="11dd0-143">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="11dd0-143">Example</span></span>

<span data-ttu-id="11dd0-144">In het volgende voor beeld wordt het `DynamicParameters` element van de `Encoding` dynamische para meter weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="11dd0-144">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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
