---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-script resource
ms.openlocfilehash: 50d4667396c8c619079288ec51599152ed2d6cd5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557019"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="6e10b-103">DSC-script resource</span><span class="sxs-lookup"><span data-stu-id="6e10b-103">DSC Script Resource</span></span>

> <span data-ttu-id="6e10b-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="6e10b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="6e10b-105">De **script** bron in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het uitvoeren van Windows Power shell-script blokken op doel knooppunten.</span><span class="sxs-lookup"><span data-stu-id="6e10b-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="6e10b-106">De **script** bron maakt gebruik van **GetScript**-, **SetScript**-en **TestScript** -eigenschappen die script blokken bevatten die u definieert om de bijbehorende DSC-status bewerkingen uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="6e10b-106">The **Script** resource uses **GetScript**, **SetScript**, and **TestScript** properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="6e10b-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="6e10b-107">Syntax</span></span>

```Syntax
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> <span data-ttu-id="6e10b-108">**GetScript**-, **TestScript**-en **SetScript** -blokken worden opgeslagen als teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="6e10b-108">**GetScript**, **TestScript**, and **SetScript** blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="6e10b-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="6e10b-109">Properties</span></span>

|<span data-ttu-id="6e10b-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="6e10b-110">Property</span></span> |<span data-ttu-id="6e10b-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6e10b-111">Description</span></span> |
|---|---|
|<span data-ttu-id="6e10b-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="6e10b-112">GetScript</span></span> |<span data-ttu-id="6e10b-113">Een script blok dat de huidige status van het knoop punt retourneert.</span><span class="sxs-lookup"><span data-stu-id="6e10b-113">A script block that returns the current state of the Node.</span></span> |
|<span data-ttu-id="6e10b-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="6e10b-114">SetScript</span></span> |<span data-ttu-id="6e10b-115">Een script blok dat door DSC wordt gebruikt om naleving af te dwingen wanneer het knoop punt niet de gewenste status heeft.</span><span class="sxs-lookup"><span data-stu-id="6e10b-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span> |
|<span data-ttu-id="6e10b-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="6e10b-116">TestScript</span></span> |<span data-ttu-id="6e10b-117">Een script blok dat bepaalt of het knoop punt de gewenste status heeft.</span><span class="sxs-lookup"><span data-stu-id="6e10b-117">A script block that determines if the Node is in the desired state.</span></span> |
|<span data-ttu-id="6e10b-118">Referentie</span><span class="sxs-lookup"><span data-stu-id="6e10b-118">Credential</span></span> |<span data-ttu-id="6e10b-119">Hiermee geeft u de referenties op die moeten worden gebruikt voor het uitvoeren van dit script, indien referenties vereist zijn.</span><span class="sxs-lookup"><span data-stu-id="6e10b-119">Indicates the credentials to use for running this script, if credentials are required.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="6e10b-120">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="6e10b-120">Common properties</span></span>

|<span data-ttu-id="6e10b-121">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="6e10b-121">Property</span></span> |<span data-ttu-id="6e10b-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6e10b-122">Description</span></span> |
|---|---|
|<span data-ttu-id="6e10b-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6e10b-123">DependsOn</span></span> |<span data-ttu-id="6e10b-124">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="6e10b-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6e10b-125">De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="6e10b-125">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="6e10b-126">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="6e10b-126">PsDscRunAsCredential</span></span> |<span data-ttu-id="6e10b-127">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="6e10b-127">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="6e10b-128">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="6e10b-128">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="6e10b-129">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6e10b-129">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="6e10b-130">Aanvullende informatie</span><span class="sxs-lookup"><span data-stu-id="6e10b-130">Additional information</span></span>

#### <a name="getscript"></a><span data-ttu-id="6e10b-131">GetScript</span><span class="sxs-lookup"><span data-stu-id="6e10b-131">GetScript</span></span>

<span data-ttu-id="6e10b-132">DSC maakt geen gebruik van de uitvoer van **GetScript**.</span><span class="sxs-lookup"><span data-stu-id="6e10b-132">DSC does not use the output from **GetScript**.</span></span> <span data-ttu-id="6e10b-133">De cmdlet [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) voert **GetScript** uit om de huidige status van een knoop punt op te halen.</span><span class="sxs-lookup"><span data-stu-id="6e10b-133">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes **GetScript** to retrieve a node's current state.</span></span> <span data-ttu-id="6e10b-134">Er is geen retour waarde vereist vanuit **GetScript**.</span><span class="sxs-lookup"><span data-stu-id="6e10b-134">A return value is not required from **GetScript**.</span></span> <span data-ttu-id="6e10b-135">Als u een retour waarde opgeeft, moet deze een hashtabel zijn met een **resultaat** sleutel waarvan de waarde een teken reeks is.</span><span class="sxs-lookup"><span data-stu-id="6e10b-135">If you specify a return value, it must be a hashtable containing a **Result** key whose value is a String.</span></span>

#### <a name="testscript"></a><span data-ttu-id="6e10b-136">TestScript</span><span class="sxs-lookup"><span data-stu-id="6e10b-136">TestScript</span></span>

<span data-ttu-id="6e10b-137">**TestScript** wordt uitgevoerd door DSC om te bepalen of **SetScript** moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6e10b-137">**TestScript** is executed by DSC to determine if **SetScript** should be run.</span></span> <span data-ttu-id="6e10b-138">Als **TestScript** retourneert `$false` , voert DSC **SetScript** uit om het knoop punt weer in de gewenste staat te brengen.</span><span class="sxs-lookup"><span data-stu-id="6e10b-138">If **TestScript** returns `$false`, DSC executes **SetScript** to bring the node back to the desired state.</span></span> <span data-ttu-id="6e10b-139">Deze moet een Booleaanse waarde Retour neren.</span><span class="sxs-lookup"><span data-stu-id="6e10b-139">It must return a boolean value.</span></span> <span data-ttu-id="6e10b-140">Een resultaat van `$true` geeft aan dat het knoop punt compatibel is en dat **SetScript** niet moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6e10b-140">A result of `$true` indicates that the node is compliant and **SetScript** should not executed.</span></span>

<span data-ttu-id="6e10b-141">Met de cmdlet [test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) wordt **TestScript** uitgevoerd om de knoop punten te verkrijgen die voldoen aan de **script** bronnen.</span><span class="sxs-lookup"><span data-stu-id="6e10b-141">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes **TestScript** to retrieve the nodes compliance with the **Script** resources.</span></span>
<span data-ttu-id="6e10b-142">In dit geval wordt **SetScript** echter niet uitgevoerd, ongeacht welk **TestScript** Block retourneert.</span><span class="sxs-lookup"><span data-stu-id="6e10b-142">However, in this case, **SetScript** does not run, no matter what **TestScript** block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="6e10b-143">Alle uitvoer van uw **TestScript** maakt deel uit van de geretourneerde waarde.</span><span class="sxs-lookup"><span data-stu-id="6e10b-143">All output from your **TestScript** is part of its return value.</span></span> <span data-ttu-id="6e10b-144">Power shell interpreteert niet-onderdrukte uitvoer als niet-nul, wat betekent dat uw **TestScript** wordt geretourneerd, `$true` ongeacht de status van uw knoop punt.</span><span class="sxs-lookup"><span data-stu-id="6e10b-144">PowerShell interprets unsuppressed output as non-zero, which means that your **TestScript** will return `$true` regardless of your node's state.</span></span> <span data-ttu-id="6e10b-145">Dit resulteert in onvoorspelbare resultaten, fout-positieven en veroorzaakt problemen tijdens het oplossen van problemen.</span><span class="sxs-lookup"><span data-stu-id="6e10b-145">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

#### <a name="setscript"></a><span data-ttu-id="6e10b-146">SetScript</span><span class="sxs-lookup"><span data-stu-id="6e10b-146">SetScript</span></span>

<span data-ttu-id="6e10b-147">**SetScript** wijzigt het knoop punt om de gewenste status af te dwingen.</span><span class="sxs-lookup"><span data-stu-id="6e10b-147">**SetScript** modifies the node to enforce the desired state.</span></span> <span data-ttu-id="6e10b-148">Deze wordt aangeroepen door DSC als het **TestScript** -script blok retourneert `$false` .</span><span class="sxs-lookup"><span data-stu-id="6e10b-148">It is called by DSC if the **TestScript** script block returns `$false`.</span></span> <span data-ttu-id="6e10b-149">De **SetScript** mag geen retour waarde hebben.</span><span class="sxs-lookup"><span data-stu-id="6e10b-149">The **SetScript** should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="6e10b-150">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="6e10b-150">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="6e10b-151">Voor beeld 1: voorbeeld tekst schrijven met behulp van een script resource</span><span class="sxs-lookup"><span data-stu-id="6e10b-151">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="6e10b-152">In dit voor beeld wordt getest of `C:\TempFolder\TestFile.txt` op elk knoop punt bestaat.</span><span class="sxs-lookup"><span data-stu-id="6e10b-152">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="6e10b-153">Als deze niet bestaat, wordt deze gemaakt met behulp van de `SetScript` .</span><span class="sxs-lookup"><span data-stu-id="6e10b-153">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="6e10b-154">Het `GetScript` retourneert de inhoud van het bestand en de geretourneerde waarde wordt niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6e10b-154">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="6e10b-155">Voor beeld 2: versie-informatie vergelijken met een script resource</span><span class="sxs-lookup"><span data-stu-id="6e10b-155">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="6e10b-156">In dit voor beeld worden de gegevens van de *compatibele* versie opgehaald uit een tekst bestand op de ontwerp computer en opgeslagen in de `$version` variabele.</span><span class="sxs-lookup"><span data-stu-id="6e10b-156">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="6e10b-157">Bij het genereren van het MOF-bestand van het knoop punt vervangt DSC de `$using:version` variabelen in elk script blok met de waarde van de `$version` variabele.</span><span class="sxs-lookup"><span data-stu-id="6e10b-157">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>
<span data-ttu-id="6e10b-158">Tijdens de uitvoering wordt de *compatibele* versie opgeslagen in een tekst bestand op elk knoop punt en vergeleken en bijgewerkt bij de volgende uitvoeringen.</span><span class="sxs-lookup"><span data-stu-id="6e10b-158">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }
                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            }
        }
    }
}
```

### <a name="example-3-utilizing-parameters-in-a-script-resource"></a><span data-ttu-id="6e10b-159">Voor beeld 3: para meters gebruiken in een script bron</span><span class="sxs-lookup"><span data-stu-id="6e10b-159">Example 3: Utilizing parameters in a Script resource</span></span>

<span data-ttu-id="6e10b-160">In dit voor beeld worden para meters uit de script resource geopend door het `using` bereik te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="6e10b-160">This example accesses parameters from within the Script resource by making use of the `using` scope.</span></span> <span data-ttu-id="6e10b-161">Houd er rekening mee dat **ConfigurationData** op een vergelijk bare manier kan worden benaderd.</span><span class="sxs-lookup"><span data-stu-id="6e10b-161">Please note that **ConfigurationData** can be accessed in a similar way.</span></span> <span data-ttu-id="6e10b-162">Net als voor beeld 2 wordt een versie naar verwachting opgeslagen in een lokaal bestand op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="6e10b-162">Like example 2, a version is expected to be stored inside a local file on the target node.</span></span> <span data-ttu-id="6e10b-163">Zowel het pad naar het lokale bestand als de versie kunnen worden geconfigureerd, maar ook code uit configuratie gegevens ontkoppelen.</span><span class="sxs-lookup"><span data-stu-id="6e10b-163">Both the local file path as well as the version are configurable however, decoupling code from configuration data.</span></span>

```powershell
Configuration ScriptTest
{
    param
    (
        [Version]
        $Version,

        [string]
        $FilePath
    )

    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content -Path $using:FilePath
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:Version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }

                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                Set-Content -Path $using:FilePath -Value $using:Version
            }
        }
    }
}
```

<span data-ttu-id="6e10b-164">Het resulterende MOF-bestand bevat de variabelen en hun waarden die worden geopend via het `using` bereik.</span><span class="sxs-lookup"><span data-stu-id="6e10b-164">The resulting MOF file includes the variables and their values accessed through the `using` scope.</span></span>
<span data-ttu-id="6e10b-165">Ze worden toegevoegd aan elke script Block die gebruikmaakt van de variabelen.</span><span class="sxs-lookup"><span data-stu-id="6e10b-165">They are injected into each scriptblock which uses the variables.</span></span> <span data-ttu-id="6e10b-166">Testen en instellen van scripts zijn verwijderd voor de boog:</span><span class="sxs-lookup"><span data-stu-id="6e10b-166">Test and Set scripts have been removed for brevity:</span></span>

```Output
instance of MSFT_ScriptResource as $MSFT_ScriptResource1ref
{
 GetScript = "$FilePath ='C:\\Config.ini'\n\n $currentVersion = Get-Content -Path $FilePath\n return @{ 'Result' = \"$currentVersion\" }\n";
 TestScript = ...;
 SetScript = ...;
};
```
