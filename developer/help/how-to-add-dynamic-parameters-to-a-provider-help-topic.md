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
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="0e63e-102">Dynamische parameters toevoegen aan een Help-onderwerp over providers</span><span class="sxs-lookup"><span data-stu-id="0e63e-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="0e63e-103">In deze sectie wordt uitgelegd hoe u voor het vullen van de **dynamische PARAMETERS** gedeelte van een provider help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="0e63e-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="0e63e-104">*Dynamische parameters* parameters van een cmdlet of functie die beschikbaar zijn alleen onder de opgegeven voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="0e63e-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="0e63e-105">De dynamische parameters die worden beschreven in een provider help-onderwerp zijn de dynamische parameters waarmee de provider wordt toegevoegd aan de cmdlet of functie wanneer de cmdlet of de functie wordt gebruikt in het station van de provider.</span><span class="sxs-lookup"><span data-stu-id="0e63e-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="0e63e-106">Dynamische parameters kunnen ook worden beschreven in de aangepaste cmdlet help voor een provider.</span><span class="sxs-lookup"><span data-stu-id="0e63e-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="0e63e-107">Bij het schrijven van zowel provider help en aangepaste cmdlet help voor een provider, moet u de documentatie van de dynamische parameter opnemen in beide documenten.</span><span class="sxs-lookup"><span data-stu-id="0e63e-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="0e63e-108">Zie voor meer informatie over aangepaste cmdlet help [schrijven Windows PowerShell aangepaste Cmdlet Help voor Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span><span class="sxs-lookup"><span data-stu-id="0e63e-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="0e63e-109">Als een provider wordt niet geïmplementeerd voor dynamische parameters, de provider help-onderwerp bevat een lege `DynamicParameters` element.</span><span class="sxs-lookup"><span data-stu-id="0e63e-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="0e63e-110">Dynamische Parameters toevoegen</span><span class="sxs-lookup"><span data-stu-id="0e63e-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="0e63e-111">In de *AssemblyName*.dll-help.xml-bestand, vanuit de `providerHelp` element toevoegen een `DynamicParameters` element.</span><span class="sxs-lookup"><span data-stu-id="0e63e-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="0e63e-112">De `DynamicParameters` element moet worden weergegeven na de `Tasks` element en voordat de `RelatedLinks` element.</span><span class="sxs-lookup"><span data-stu-id="0e63e-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="0e63e-113">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="0e63e-113">For example:</span></span>

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

   <span data-ttu-id="0e63e-114">Als de provider wordt niet geïmplementeerd voor dynamische parameters, de `DynamicParameters` element kan niet leeg zijn.</span><span class="sxs-lookup"><span data-stu-id="0e63e-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="0e63e-115">Binnen de `DynamicParameters` -element voor elk dynamische parameter toevoegen een `DynamicParameter` element.</span><span class="sxs-lookup"><span data-stu-id="0e63e-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="0e63e-116">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="0e63e-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="0e63e-117">In elk `DynamicParameter` -element, Voeg een `Name` en `CmdletSupported` element.</span><span class="sxs-lookup"><span data-stu-id="0e63e-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="0e63e-118">Naam van element</span><span class="sxs-lookup"><span data-stu-id="0e63e-118">Element Name</span></span>|<span data-ttu-id="0e63e-119">Description</span><span class="sxs-lookup"><span data-stu-id="0e63e-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="0e63e-120">Naam</span><span class="sxs-lookup"><span data-stu-id="0e63e-120">Name</span></span>|<span data-ttu-id="0e63e-121">Hiermee geeft u de parameternaam van de.</span><span class="sxs-lookup"><span data-stu-id="0e63e-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="0e63e-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="0e63e-122">CmdletSupported</span></span>|<span data-ttu-id="0e63e-123">Hiermee geeft u de cmdlets waarbij de parameter geldig is.</span><span class="sxs-lookup"><span data-stu-id="0e63e-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="0e63e-124">Typ een door komma's gescheiden lijst met namen van de cmdlets.</span><span class="sxs-lookup"><span data-stu-id="0e63e-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="0e63e-125">Bijvoorbeeld, de volgende XML-documenten de `Encoding` dynamische parameter waarmee het bestandssysteem van Windows PowerShell-provider wordt toegevoegd aan de `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="0e63e-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="0e63e-126">In elk `DynamicParameter` -element, Voeg een `Type` element.</span><span class="sxs-lookup"><span data-stu-id="0e63e-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="0e63e-127">De `Type` element is een container voor de `Name` element waarin het .NET-type van de waarde van de dynamische parameter.</span><span class="sxs-lookup"><span data-stu-id="0e63e-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="0e63e-128">Bijvoorbeeld, het volgende XML-bestand ziet u dat het .NET-type van de `Encoding` dynamische parameter wordt de [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) opsomming.</span><span class="sxs-lookup"><span data-stu-id="0e63e-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="0e63e-129">Voeg de `Description` -element een korte beschrijving van de dynamische parameter bevat.</span><span class="sxs-lookup"><span data-stu-id="0e63e-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="0e63e-130">Bij het samenstellen van de beschrijving, gebruikt u de richtlijnen voor alle cmdlet-parameters in voorgeschreven [over het toevoegen van parameterinformatie](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="0e63e-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="0e63e-131">Het volgende XML-bestand bevat bijvoorbeeld de beschrijving van de `Encoding` dynamische parameter.</span><span class="sxs-lookup"><span data-stu-id="0e63e-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="0e63e-132">Voeg de `PossibleValues` -element en de onderliggende elementen.</span><span class="sxs-lookup"><span data-stu-id="0e63e-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="0e63e-133">Deze elementen beschrijven samen de waarden van de dynamische parameter.</span><span class="sxs-lookup"><span data-stu-id="0e63e-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="0e63e-134">Dit element is ontworpen voor opsommingswaarden zijn.</span><span class="sxs-lookup"><span data-stu-id="0e63e-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="0e63e-135">Als de dynamische parameter neemt een waarde, zoals het geval is bij een switch-parameter is of de waarden kunnen niet worden geïnventariseerd, toevoegen van een lege `PossibleValues` element.</span><span class="sxs-lookup"><span data-stu-id="0e63e-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="0e63e-136">De volgende tabel geeft een lijst van en beschrijft de `PossibleValues` -element en de onderliggende elementen.</span><span class="sxs-lookup"><span data-stu-id="0e63e-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="0e63e-137">Naam van element</span><span class="sxs-lookup"><span data-stu-id="0e63e-137">Element Name</span></span>|<span data-ttu-id="0e63e-138">Description</span><span class="sxs-lookup"><span data-stu-id="0e63e-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="0e63e-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="0e63e-139">PossibleValues</span></span>|<span data-ttu-id="0e63e-140">Dit element is een container.</span><span class="sxs-lookup"><span data-stu-id="0e63e-140">This element is a container.</span></span> <span data-ttu-id="0e63e-141">De onderliggende elementen worden hieronder beschreven.</span><span class="sxs-lookup"><span data-stu-id="0e63e-141">Its child elements are described below.</span></span> <span data-ttu-id="0e63e-142">Voeg een `PossibleValues` element elke provider help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="0e63e-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="0e63e-143">Het element kan niet leeg zijn.</span><span class="sxs-lookup"><span data-stu-id="0e63e-143">The element can be empty.</span></span>|
   |<span data-ttu-id="0e63e-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="0e63e-144">PossibleValue</span></span>|<span data-ttu-id="0e63e-145">Dit element is een container.</span><span class="sxs-lookup"><span data-stu-id="0e63e-145">This element is a container.</span></span> <span data-ttu-id="0e63e-146">De onderliggende elementen worden hieronder beschreven.</span><span class="sxs-lookup"><span data-stu-id="0e63e-146">Its child elements are described below.</span></span> <span data-ttu-id="0e63e-147">Voeg een `PossibleValue` -element voor elke waarde van de dynamische parameter.</span><span class="sxs-lookup"><span data-stu-id="0e63e-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="0e63e-148">Waarde</span><span class="sxs-lookup"><span data-stu-id="0e63e-148">Value</span></span>|<span data-ttu-id="0e63e-149">Hiermee geeft u de naam van de.</span><span class="sxs-lookup"><span data-stu-id="0e63e-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="0e63e-150">Description</span><span class="sxs-lookup"><span data-stu-id="0e63e-150">Description</span></span>|<span data-ttu-id="0e63e-151">Dit element bevat een `Para` element.</span><span class="sxs-lookup"><span data-stu-id="0e63e-151">This element contains a `Para` element.</span></span> <span data-ttu-id="0e63e-152">De tekst in de `Para` element wordt aangegeven wat de meerwaarde met de naam in de `Value` element.</span><span class="sxs-lookup"><span data-stu-id="0e63e-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="0e63e-153">Het volgende XML-bestand ziet u bijvoorbeeld een `PossibleValue` element van de `Encoding` dynamische parameter.</span><span class="sxs-lookup"><span data-stu-id="0e63e-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="0e63e-154">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="0e63e-154">Example</span></span>

<span data-ttu-id="0e63e-155">Het volgende voorbeeld wordt de `DynamicParameters` element van de `Encoding` dynamische parameter.</span><span class="sxs-lookup"><span data-stu-id="0e63e-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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