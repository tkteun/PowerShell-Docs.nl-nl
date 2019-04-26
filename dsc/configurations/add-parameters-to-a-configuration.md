---
ms.date: 12/12/2018
keywords: DSC, powershell, resource, galerie, instellen
title: Parameters toevoegen aan een configuratie
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080251"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="e10f0-103">Parameters toevoegen aan een configuratie</span><span class="sxs-lookup"><span data-stu-id="e10f0-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="e10f0-104">Functies, zoals [configuraties](configurations.md) kunnen als parameters worden gebruikt om toe te staan van meer dynamische configuraties op basis van de invoer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="e10f0-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="e10f0-105">De stappen zijn vergelijkbaar met die wordt beschreven in [functies met Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="e10f0-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="e10f0-106">In dit voorbeeld begint met een basisconfiguratie om configureert u de 'Spooler' service ' Actief '.</span><span class="sxs-lookup"><span data-stu-id="e10f0-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
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

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="e10f0-107">Ingebouwde configuratieparameters</span><span class="sxs-lookup"><span data-stu-id="e10f0-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="e10f0-108">In tegenstelling tot een functie echter de [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) kenmerk geen functionaliteit wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="e10f0-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="e10f0-109">Naast [algemene Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), configuraties kunnen ook de volgende parameters, zonder dat u voor het definiëren van deze ingebouwde gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e10f0-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="e10f0-110">Parameter</span><span class="sxs-lookup"><span data-stu-id="e10f0-110">Parameter</span></span>  |<span data-ttu-id="e10f0-111">Description</span><span class="sxs-lookup"><span data-stu-id="e10f0-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="e10f0-112">Gebruikt bij het definiëren van [samengestelde configuraties](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="e10f0-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="e10f0-113">Gebruikt bij het definiëren van [samengestelde configuraties](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="e10f0-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="e10f0-114">Gebruikt bij het definiëren van [samengestelde configuraties](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="e10f0-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="e10f0-115">Gebruikt om door te geven in gestructureerde [configuratiegegevens](configData.md) voor gebruik in de configuratie.</span><span class="sxs-lookup"><span data-stu-id="e10f0-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="e10f0-116">Gebruikt om op te geven waar uw "\<computername\>.mof ' wordt gecompileerd aan de bestand</span><span class="sxs-lookup"><span data-stu-id="e10f0-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="e10f0-117">Uw eigen parameters toe te voegen aan configuraties</span><span class="sxs-lookup"><span data-stu-id="e10f0-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="e10f0-118">Naast de ingebouwde parameters kunt u ook uw eigen parameters toevoegen aan uw configuraties.</span><span class="sxs-lookup"><span data-stu-id="e10f0-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="e10f0-119">Het parameterblok gaat direct in de declaratie van de configuratie, net als een functie.</span><span class="sxs-lookup"><span data-stu-id="e10f0-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="e10f0-120">Een configuratie-parameterblok moet buiten een **knooppunt** declaraties, en boven een *importeren* instructies.</span><span class="sxs-lookup"><span data-stu-id="e10f0-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="e10f0-121">Door parameters toe te voegen, kunt u uw configuraties meer robuuste en dynamisch.</span><span class="sxs-lookup"><span data-stu-id="e10f0-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="e10f0-122">Voeg een parameter ComputerName toe</span><span class="sxs-lookup"><span data-stu-id="e10f0-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="e10f0-123">De eerste parameter, u toevoegen kunt, is een `-Computername` parameter, zodat u een bestand ".mof" dynamisch voor een compileren kunt `-Computername` u doorgeeft aan uw configuratie.</span><span class="sxs-lookup"><span data-stu-id="e10f0-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="e10f0-124">Functies, zoals kunt u ook definiëren een standaardwaarde in het geval de gebruiker voldoet niet aan een waarde voor `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="e10f0-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="e10f0-125">In de configuratie, geeft u aan uw `-ComputerName` parameter bij het definiëren van uw blok knooppunt.</span><span class="sxs-lookup"><span data-stu-id="e10f0-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="e10f0-126">Aanroepen van de configuratie met parameters</span><span class="sxs-lookup"><span data-stu-id="e10f0-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="e10f0-127">Nadat u parameters aan uw configuratie hebt toegevoegd, kunt u ze gebruiken, net zoals u zou met een cmdlet doen.</span><span class="sxs-lookup"><span data-stu-id="e10f0-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="e10f0-128">Compileren van meerdere MOF-bestanden</span><span class="sxs-lookup"><span data-stu-id="e10f0-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="e10f0-129">Het knooppunt blok kan ook een door komma's gescheiden lijst van computernamen accepteren en MOF-bestanden voor elk gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="e10f0-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="e10f0-130">U kunt uitvoeren in het volgende voorbeeld voor het genereren van 'MOF-bestanden voor alle computers die is doorgegeven aan de `-ComputerName` parameter.</span><span class="sxs-lookup"><span data-stu-id="e10f0-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="e10f0-131">Geavanceerde parameters in configuraties</span><span class="sxs-lookup"><span data-stu-id="e10f0-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="e10f0-132">Naast een `-ComputerName` parameter, kunnen we de parameters voor de servicenaam en staat toevoegen.</span><span class="sxs-lookup"><span data-stu-id="e10f0-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="e10f0-133">Het volgende voorbeeld wordt een parameterblok met een `-ServiceName` parameter en gebruikt deze om dynamisch te bepalen de **Service** resource blokkeren.</span><span class="sxs-lookup"><span data-stu-id="e10f0-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="e10f0-134">Ook wordt toegevoegd een `-State` parameter om dynamisch te bepalen de **status** in de **Service** resource blokkeren.</span><span class="sxs-lookup"><span data-stu-id="e10f0-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

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

    # It is best practice to implicitly import any required resources or modules.
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
> <span data-ttu-id="e10f0-135">In andere advacned-scenario's, kan het zinvol meer dynamische gegevens verplaatsen naar een gestructureerde [configuratiegegevens](configData.md).</span><span class="sxs-lookup"><span data-stu-id="e10f0-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="e10f0-136">De configuratie van het voorbeeld wordt een dynamisch `$ServiceName`, maar als deze niet is opgegeven, compileren van een fout leidt.</span><span class="sxs-lookup"><span data-stu-id="e10f0-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="e10f0-137">U kunt een standaardwaarde zoals in dit voorbeeld kan toevoegen.</span><span class="sxs-lookup"><span data-stu-id="e10f0-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="e10f0-138">In dit geval echter het verstandig meer om gewoon de gebruiker te dwingen een waarde opgeven voor de `$ServiceName` parameter.</span><span class="sxs-lookup"><span data-stu-id="e10f0-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="e10f0-139">De `parameter` kenmerk kunt u verdere validatie en pijplijn ondersteuning voor parameters van uw configuratie toevoegen.</span><span class="sxs-lookup"><span data-stu-id="e10f0-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="e10f0-140">Boven een parameterdeclaratie toevoegen de `parameter` kenmerk blokkeren zoals in het onderstaande voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="e10f0-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="e10f0-141">U kunt argumenten aan elk opgeven `parameter` kenmerk voor het besturingselement aspecten van de gedefinieerde parameter.</span><span class="sxs-lookup"><span data-stu-id="e10f0-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="e10f0-142">Het volgende voorbeeld wordt de `$ServiceName` een **verplichte** parameter.</span><span class="sxs-lookup"><span data-stu-id="e10f0-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="e10f0-143">Voor de `$State` parameter, willen we graag om te voorkomen dat de gebruiker op te geven waarden buiten een vooraf gedefinieerde set (zoals die wordt uitgevoerd, gestopt) de `ValidationSet*`kenmerk dat de gebruiker van de waarden buiten een vooraf gedefinieerde set (zoals die wordt uitgevoerd, op te geven Gestopt).</span><span class="sxs-lookup"><span data-stu-id="e10f0-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="e10f0-144">Het volgende voorbeeld wordt de `ValidationSet` kenmerk aan de `$State` parameter.</span><span class="sxs-lookup"><span data-stu-id="e10f0-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="e10f0-145">Omdat we niet wilt maken de `$State` parameter **verplichte**, moeten we een standaardwaarde voor het toevoegen.</span><span class="sxs-lookup"><span data-stu-id="e10f0-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="e10f0-146">U hoeft niet om op te geven een `parameter` kenmerk bij het gebruik van een `validation` kenmerk.</span><span class="sxs-lookup"><span data-stu-id="e10f0-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="e10f0-147">U kunt meer lezen over de `parameter` en validatie kenmerken in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e10f0-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="e10f0-148">Configuratie van volledig met parameters</span><span class="sxs-lookup"><span data-stu-id="e10f0-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="e10f0-149">We hebben nu een geparameteriseerde configuratie die ervoor zorgt dat de gebruiker om op te geven een `-InstanceName`, `-ServiceName`, en valideert de `-State` parameter.</span><span class="sxs-lookup"><span data-stu-id="e10f0-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

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

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="see-also"></a><span data-ttu-id="e10f0-150">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e10f0-150">See also</span></span>

- [<span data-ttu-id="e10f0-151">Schrijven van de help voor DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="e10f0-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="e10f0-152">Dynamische configuraties</span><span class="sxs-lookup"><span data-stu-id="e10f0-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="e10f0-153">Van configuratiegegevens in uw configuraties gebruiken</span><span class="sxs-lookup"><span data-stu-id="e10f0-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="e10f0-154">Afzonderlijke configuratie- en omgevingsgegevens gegevens</span><span class="sxs-lookup"><span data-stu-id="e10f0-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
