---
ms.date: 12/12/2018
keywords: DSC, Power shell, resource, Galerie, Setup
title: Parameters toevoegen aan een configuratie
ms.openlocfilehash: 72e6c15593d11ed39d7fe8ea79f794089f410cf8
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942116"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="61579-103">Parameters toevoegen aan een configuratie</span><span class="sxs-lookup"><span data-stu-id="61579-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="61579-104">Net als-functies kunnen [configuraties](configurations.md) worden para meters om meer dynamische configuraties op basis van gebruikers invoer toe te staan.</span><span class="sxs-lookup"><span data-stu-id="61579-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="61579-105">De stappen zijn vergelijkbaar met die beschreven in [functies met para meters](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="61579-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="61579-106">Dit voor beeld begint met een basis configuratie waarmee de ' Spooler-service ' wordt uitgevoerd '.</span><span class="sxs-lookup"><span data-stu-id="61579-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="61579-107">Ingebouwde configuratie parameters</span><span class="sxs-lookup"><span data-stu-id="61579-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="61579-108">In tegens telling tot een functie, voegt het kenmerk [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) geen functionaliteit toe.</span><span class="sxs-lookup"><span data-stu-id="61579-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="61579-109">Naast de [algemene para meters](/powershell/module/microsoft.powershell.core/about/about_commonparameters)kunnen configuraties ook gebruikmaken van de volgende ingebouwde para meters, zonder dat u ze hoeft te definiëren.</span><span class="sxs-lookup"><span data-stu-id="61579-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="61579-110">Parameter</span><span class="sxs-lookup"><span data-stu-id="61579-110">Parameter</span></span>  |<span data-ttu-id="61579-111">Description</span><span class="sxs-lookup"><span data-stu-id="61579-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="61579-112">Gebruikt voor het definiëren van [samengestelde configuraties](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="61579-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="61579-113">Gebruikt voor het definiëren van [samengestelde configuraties](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="61579-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="61579-114">Gebruikt voor het definiëren van [samengestelde configuraties](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="61579-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="61579-115">Wordt gebruikt voor het door geven van gestructureerde [configuratie gegevens](configData.md) voor gebruik in de configuratie.</span><span class="sxs-lookup"><span data-stu-id="61579-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="61579-116">Wordt gebruikt om op te geven waar uw ' @no__t -0computername\>.mof-bestand wordt gecompileerd</span><span class="sxs-lookup"><span data-stu-id="61579-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="61579-117">Uw eigen para meters aan configuraties toevoegen</span><span class="sxs-lookup"><span data-stu-id="61579-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="61579-118">Naast de ingebouwde para meters kunt u ook uw eigen para meters aan uw configuraties toevoegen.</span><span class="sxs-lookup"><span data-stu-id="61579-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="61579-119">Het parameter blok gaat direct in de configuratie declaratie, net als een functie.</span><span class="sxs-lookup"><span data-stu-id="61579-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="61579-120">Een configuratie parameter blok moet zich buiten eventuele **knooppunt** declaraties bevinden en boven alle *import* instructies.</span><span class="sxs-lookup"><span data-stu-id="61579-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="61579-121">Door para meters toe te voegen, kunt u uw configuraties robuuster en dynamisch maken.</span><span class="sxs-lookup"><span data-stu-id="61579-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="61579-122">Een ComputerName-para meter toevoegen</span><span class="sxs-lookup"><span data-stu-id="61579-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="61579-123">De eerste para meter die u kunt toevoegen is een `-Computername` para meter, zodat u dynamisch een '. MOF-bestand ' kunt compileren voor elke `-Computername` die u aan uw configuratie doorgeeft.</span><span class="sxs-lookup"><span data-stu-id="61579-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="61579-124">Net als functions kunt u ook een standaard waarde definiëren, voor het geval de gebruiker geen waarde geeft voor `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="61579-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="61579-125">Binnen uw configuratie kunt u de para meter `-ComputerName` opgeven wanneer u het knooppunt blok wilt definiëren.</span><span class="sxs-lookup"><span data-stu-id="61579-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="61579-126">Uw configuratie met para meters aanroepen</span><span class="sxs-lookup"><span data-stu-id="61579-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="61579-127">Nadat u para meters aan uw configuratie hebt toegevoegd, kunt u ze op dezelfde manier gebruiken als met een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="61579-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="61579-128">Meerdere MOF-bestanden compileren</span><span class="sxs-lookup"><span data-stu-id="61579-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="61579-129">Het knooppunt blok kan ook een door komma's gescheiden lijst met computer namen accepteren en de MOF-bestanden genereren.</span><span class="sxs-lookup"><span data-stu-id="61579-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="61579-130">U kunt het volgende voor beeld uitvoeren om ". MOF"-bestanden te genereren voor alle computers die worden door gegeven aan de para meter `-ComputerName`.</span><span class="sxs-lookup"><span data-stu-id="61579-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="61579-131">Geavanceerde para meters in configuraties</span><span class="sxs-lookup"><span data-stu-id="61579-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="61579-132">Naast een `-ComputerName`-para meter kunnen we para meters voor de service naam en-status toevoegen.</span><span class="sxs-lookup"><span data-stu-id="61579-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="61579-133">In het volgende voor beeld wordt een parameter blok met een `-ServiceName`-para meter toegevoegd en gebruikt om het **service** bron blok dynamisch te definiëren.</span><span class="sxs-lookup"><span data-stu-id="61579-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="61579-134">Er wordt ook een `-State`-para meter toegevoegd om de **status** in het **service** resource blok dynamisch te definiëren.</span><span class="sxs-lookup"><span data-stu-id="61579-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="61579-135">In meer advacned scenario's is het wellicht beter om uw dynamische gegevens te verplaatsen naar een Structured [configuratie gegevens](configData.md).</span><span class="sxs-lookup"><span data-stu-id="61579-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="61579-136">De voorbeeld configuratie heeft nu een dynamische `$ServiceName`, maar als er geen is opgegeven, wordt er een fout opgetreden bij het compileren van resultaten.</span><span class="sxs-lookup"><span data-stu-id="61579-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="61579-137">U kunt bijvoorbeeld een standaard waarde toevoegen, zoals in dit voor beeld.</span><span class="sxs-lookup"><span data-stu-id="61579-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="61579-138">In dit geval is het beter om de gebruiker te dwingen een waarde voor de para meter `$ServiceName` op te geven.</span><span class="sxs-lookup"><span data-stu-id="61579-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="61579-139">Met het kenmerk `parameter` kunt u verdere validatie-en pijplijn ondersteuning toevoegen aan de para meters van uw configuratie.</span><span class="sxs-lookup"><span data-stu-id="61579-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="61579-140">Voeg boven een parameter declaratie het `parameter`-kenmerk blok toe, zoals in het onderstaande voor beeld.</span><span class="sxs-lookup"><span data-stu-id="61579-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="61579-141">U kunt argumenten voor elk kenmerk `parameter` opgeven om de aspecten van de gedefinieerde para meter te beheren.</span><span class="sxs-lookup"><span data-stu-id="61579-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="61579-142">In het volgende voor beeld wordt de `$ServiceName` een **verplichte** para meter.</span><span class="sxs-lookup"><span data-stu-id="61579-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="61579-143">Voor de para meter `$State` willen we voor komen dat de gebruiker waarden opgeeft buiten een vooraf gedefinieerde set (zoals actief, gestopt). de `ValidationSet*`attribute zou voor komen dat de gebruiker waarden opgeeft buiten een vooraf gedefinieerde set (zoals actief, gestopt).</span><span class="sxs-lookup"><span data-stu-id="61579-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="61579-144">In het volgende voor beeld wordt het kenmerk `ValidationSet` toegevoegd aan de para meter `$State`.</span><span class="sxs-lookup"><span data-stu-id="61579-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="61579-145">Omdat we de `$State`-para meter niet **verplicht**moeten maken, moeten we een standaard waarde voor het veld toevoegen.</span><span class="sxs-lookup"><span data-stu-id="61579-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="61579-146">U hoeft geen `parameter`-kenmerk op te geven wanneer u een `validation`-kenmerk gebruikt.</span><span class="sxs-lookup"><span data-stu-id="61579-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="61579-147">Meer informatie over de `parameter` en validatie kenmerken vindt u in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span><span class="sxs-lookup"><span data-stu-id="61579-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="61579-148">Volledig geparametriseerde configuratie</span><span class="sxs-lookup"><span data-stu-id="61579-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="61579-149">We hebben nu een configuratie met para meters waarmee de gebruiker wordt gedwongen een `-InstanceName`, `-ServiceName` op te geven en de para meter `-State` te valideren.</span><span class="sxs-lookup"><span data-stu-id="61579-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="61579-150">Zie ook</span><span class="sxs-lookup"><span data-stu-id="61579-150">See also</span></span>

- [<span data-ttu-id="61579-151">Schrijf hulp voor DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="61579-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="61579-152">Dynamische configuraties</span><span class="sxs-lookup"><span data-stu-id="61579-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="61579-153">Configuratie gegevens in uw configuraties gebruiken</span><span class="sxs-lookup"><span data-stu-id="61579-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="61579-154">Afzonderlijke configuratie-en omgevings gegevens</span><span class="sxs-lookup"><span data-stu-id="61579-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
