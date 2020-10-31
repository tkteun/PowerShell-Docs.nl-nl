---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-script resource
description: DSC-script resource
ms.openlocfilehash: f404bf3137caa9f57ad56034895cb15c8944ec07
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142970"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="f8f14-103">DSC-script resource</span><span class="sxs-lookup"><span data-stu-id="f8f14-103">DSC Script Resource</span></span>

> <span data-ttu-id="f8f14-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="f8f14-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="f8f14-105">De `Script` resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het uitvoeren van Windows Power shell-script blokken op doel knooppunten.</span><span class="sxs-lookup"><span data-stu-id="f8f14-105">The `Script` resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="f8f14-106">De `Script` resource gebruikt `GetScript` 
 `SetScript` en `TestScript` eigenschappen die script blokken bevatten die u definieert om de bijbehorende DSC-status bewerkingen uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f8f14-106">The `Script` resource uses `GetScript`
`SetScript`, and `TestScript` properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="f8f14-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="f8f14-107">Syntax</span></span>

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
> <span data-ttu-id="f8f14-108">`GetScript``TestScript`en `SetScript` blokken worden opgeslagen als teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f8f14-108">`GetScript` `TestScript`, and `SetScript` blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="f8f14-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="f8f14-109">Properties</span></span>

|  <span data-ttu-id="f8f14-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="f8f14-110">Property</span></span>  |                                          <span data-ttu-id="f8f14-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f8f14-111">Description</span></span>                                          |
| ---------- | --------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f8f14-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="f8f14-112">GetScript</span></span>  | <span data-ttu-id="f8f14-113">Een script blok dat de huidige status van het knoop punt retourneert.</span><span class="sxs-lookup"><span data-stu-id="f8f14-113">A script block that returns the current state of the Node.</span></span>                                    |
| <span data-ttu-id="f8f14-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="f8f14-114">SetScript</span></span>  | <span data-ttu-id="f8f14-115">Een script blok dat door DSC wordt gebruikt om naleving af te dwingen wanneer het knoop punt niet de gewenste status heeft.</span><span class="sxs-lookup"><span data-stu-id="f8f14-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span> |
| <span data-ttu-id="f8f14-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="f8f14-116">TestScript</span></span> | <span data-ttu-id="f8f14-117">Een script blok dat bepaalt of het knoop punt de gewenste status heeft.</span><span class="sxs-lookup"><span data-stu-id="f8f14-117">A script block that determines if the Node is in the desired state.</span></span>                           |
| <span data-ttu-id="f8f14-118">Referentie</span><span class="sxs-lookup"><span data-stu-id="f8f14-118">Credential</span></span> | <span data-ttu-id="f8f14-119">Hiermee geeft u de referenties op die moeten worden gebruikt voor het uitvoeren van dit script, indien referenties vereist zijn.</span><span class="sxs-lookup"><span data-stu-id="f8f14-119">Indicates the credentials to use for running this script, if credentials are required.</span></span>        |

## <a name="common-properties"></a><span data-ttu-id="f8f14-120">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="f8f14-120">Common properties</span></span>

|       <span data-ttu-id="f8f14-121">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="f8f14-121">Property</span></span>       |                                            <span data-ttu-id="f8f14-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f8f14-122">Description</span></span>                                            |
| -------------------- | ------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f8f14-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f8f14-123">DependsOn</span></span>            | <span data-ttu-id="f8f14-124">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="f8f14-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> |
| <span data-ttu-id="f8f14-125">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f8f14-125">PsDscRunAsCredential</span></span> | <span data-ttu-id="f8f14-126">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="f8f14-126">Sets the credential for running the entire resource as.</span></span>                                           |

> [!NOTE]
> <span data-ttu-id="f8f14-127">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="f8f14-127">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="f8f14-128">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f8f14-128">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="f8f14-129">Aanvullende informatie</span><span class="sxs-lookup"><span data-stu-id="f8f14-129">Additional information</span></span>

#### <a name="getscript"></a><span data-ttu-id="f8f14-130">GetScript</span><span class="sxs-lookup"><span data-stu-id="f8f14-130">GetScript</span></span>

<span data-ttu-id="f8f14-131">DSC maakt geen gebruik van de uitvoer van `GetScript` de cmdlet [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) wordt uitgevoerd `GetScript` om de huidige status van een knoop punt op te halen.</span><span class="sxs-lookup"><span data-stu-id="f8f14-131">DSC does not use the output from `GetScript` The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes `GetScript` to retrieve a node's current state.</span></span> <span data-ttu-id="f8f14-132">Een retour waarde is niet vereist `GetScript` Als u een retour waarde opgeeft, moet deze een hashtabel zijn met een **resultaat** sleutel waarvan de waarde een teken reeks is.</span><span class="sxs-lookup"><span data-stu-id="f8f14-132">A return value is not required from `GetScript` If you specify a return value, it must be a hashtable containing a **Result** key whose value is a String.</span></span>

#### <a name="testscript"></a><span data-ttu-id="f8f14-133">TestScript</span><span class="sxs-lookup"><span data-stu-id="f8f14-133">TestScript</span></span>

<span data-ttu-id="f8f14-134">`TestScript` wordt uitgevoerd door DSC om te bepalen of het `SetScript` moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f8f14-134">`TestScript` is executed by DSC to determine if `SetScript` should be run.</span></span> <span data-ttu-id="f8f14-135">Als `TestScript` `$false` u retourneert, wordt DSC uitgevoerd `SetScript` om het knoop punt weer in de gewenste staat te brengen.</span><span class="sxs-lookup"><span data-stu-id="f8f14-135">If `TestScript` returns `$false`, DSC executes `SetScript` to bring the node back to the desired state.</span></span> <span data-ttu-id="f8f14-136">Deze moet een Booleaanse waarde Retour neren.</span><span class="sxs-lookup"><span data-stu-id="f8f14-136">It must return a boolean value.</span></span> <span data-ttu-id="f8f14-137">Een resultaat van `$true` geeft aan dat het knoop punt compatibel is en `SetScript` niet moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f8f14-137">A result of `$true` indicates that the node is compliant and `SetScript` should not executed.</span></span>

<span data-ttu-id="f8f14-138">De cmdlet [test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) wordt uitgevoerd `TestScript` voor het ophalen van de knoop punten die voldoen aan de `Script` resources.</span><span class="sxs-lookup"><span data-stu-id="f8f14-138">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes `TestScript` to retrieve the nodes compliance with the `Script` resources.</span></span> <span data-ttu-id="f8f14-139">In dit geval `SetScript` wordt echter niet uitgevoerd, ongeacht welk `TestScript` blok wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f8f14-139">However, in this case, `SetScript` does not run, no matter what `TestScript` block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="f8f14-140">Alle uitvoer van uw `TestScript` maakt deel uit van de geretourneerde waarde.</span><span class="sxs-lookup"><span data-stu-id="f8f14-140">All output from your `TestScript` is part of its return value.</span></span> <span data-ttu-id="f8f14-141">Power shell interpreteert niet-onderdrukte uitvoer als niet-nul, wat betekent dat uw `TestScript` knoop punt wordt geretourneerd, `$true` ongeacht de staat van de node.</span><span class="sxs-lookup"><span data-stu-id="f8f14-141">PowerShell interprets unsuppressed output as non-zero, which means that your `TestScript` will return `$true` regardless of your node's state.</span></span> <span data-ttu-id="f8f14-142">Dit resulteert in onvoorspelbare resultaten, fout-positieven en veroorzaakt problemen tijdens het oplossen van problemen.</span><span class="sxs-lookup"><span data-stu-id="f8f14-142">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

#### <a name="setscript"></a><span data-ttu-id="f8f14-143">SetScript</span><span class="sxs-lookup"><span data-stu-id="f8f14-143">SetScript</span></span>

<span data-ttu-id="f8f14-144">`SetScript` Hiermee wijzigt u het knoop punt om de gewenste status af te dwingen.</span><span class="sxs-lookup"><span data-stu-id="f8f14-144">`SetScript` modifies the node to enforce the desired state.</span></span> <span data-ttu-id="f8f14-145">Deze wordt aangeroepen door DSC als het `TestScript` script blok retourneert `$false` .</span><span class="sxs-lookup"><span data-stu-id="f8f14-145">It is called by DSC if the `TestScript` script block returns `$false`.</span></span> <span data-ttu-id="f8f14-146">De `SetScript` mag geen retour waarde hebben.</span><span class="sxs-lookup"><span data-stu-id="f8f14-146">The `SetScript` should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="f8f14-147">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="f8f14-147">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="f8f14-148">Voor beeld 1: voorbeeld tekst schrijven met behulp van een script resource</span><span class="sxs-lookup"><span data-stu-id="f8f14-148">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="f8f14-149">In dit voor beeld wordt getest of `C:\TempFolder\TestFile.txt` op elk knoop punt bestaat.</span><span class="sxs-lookup"><span data-stu-id="f8f14-149">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="f8f14-150">Als deze niet bestaat, wordt deze gemaakt met behulp van de `SetScript` .</span><span class="sxs-lookup"><span data-stu-id="f8f14-150">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="f8f14-151">Het `GetScript` retourneert de inhoud van het bestand en de geretourneerde waarde wordt niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f8f14-151">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

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

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="f8f14-152">Voor beeld 2: versie-informatie vergelijken met een script resource</span><span class="sxs-lookup"><span data-stu-id="f8f14-152">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="f8f14-153">In dit voor beeld worden de gegevens van de _compatibele_ versie opgehaald uit een tekst bestand op de ontwerp computer en opgeslagen in de `$version` variabele.</span><span class="sxs-lookup"><span data-stu-id="f8f14-153">This example retrieves the _compliant_ version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="f8f14-154">Bij het genereren van het MOF-bestand van het knoop punt vervangt DSC de `$using:version` variabelen in elk script blok met de waarde van de `$version` variabele.</span><span class="sxs-lookup"><span data-stu-id="f8f14-154">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>
<span data-ttu-id="f8f14-155">Tijdens de uitvoering wordt de _compatibele_ versie opgeslagen in een tekst bestand op elk knoop punt en vergeleken en bijgewerkt bij de volgende uitvoeringen.</span><span class="sxs-lookup"><span data-stu-id="f8f14-155">During execution, the _compliant_ version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

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

                if( $state.Result -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state.Result,$using:version)
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

### <a name="example-3-utilizing-parameters-in-a-script-resource"></a><span data-ttu-id="f8f14-156">Voor beeld 3: para meters gebruiken in een script bron</span><span class="sxs-lookup"><span data-stu-id="f8f14-156">Example 3: Utilizing parameters in a Script resource</span></span>

<span data-ttu-id="f8f14-157">In dit voor beeld worden para meters uit de script resource geopend door het `using` bereik te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f8f14-157">This example accesses parameters from within the Script resource by making use of the `using` scope.</span></span>
<span data-ttu-id="f8f14-158">Houd er rekening mee dat **ConfigurationData** op een vergelijk bare manier kan worden benaderd.</span><span class="sxs-lookup"><span data-stu-id="f8f14-158">Please note that **ConfigurationData** can be accessed in a similar way.</span></span> <span data-ttu-id="f8f14-159">Net als voor beeld 2 wordt een versie naar verwachting opgeslagen in een lokaal bestand op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="f8f14-159">Like example 2, a version is expected to be stored inside a local file on the target node.</span></span> <span data-ttu-id="f8f14-160">Zowel het pad naar het lokale bestand als de versie kunnen worden geconfigureerd, maar ook code uit configuratie gegevens ontkoppelen.</span><span class="sxs-lookup"><span data-stu-id="f8f14-160">Both the local file path as well as the version are configurable however, decoupling code from configuration data.</span></span>

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

<span data-ttu-id="f8f14-161">Het resulterende MOF-bestand bevat de variabelen en hun waarden die worden geopend via het `using` bereik.</span><span class="sxs-lookup"><span data-stu-id="f8f14-161">The resulting MOF file includes the variables and their values accessed through the `using` scope.</span></span>
<span data-ttu-id="f8f14-162">Ze worden toegevoegd aan elke script Block die gebruikmaakt van de variabelen.</span><span class="sxs-lookup"><span data-stu-id="f8f14-162">They are injected into each scriptblock which uses the variables.</span></span> <span data-ttu-id="f8f14-163">Testen en instellen van scripts zijn verwijderd voor de boog:</span><span class="sxs-lookup"><span data-stu-id="f8f14-163">Test and Set scripts have been removed for brevity:</span></span>

```Output
instance of MSFT_ScriptResource as $MSFT_ScriptResource1ref
{
 GetScript = "$FilePath ='C:\\Config.ini'\n\n $currentVersion = Get-Content -Path $FilePath\n return @{ 'Result' = \"$currentVersion\" }\n";
 TestScript = ...;
 SetScript = ...;
};
```

### <a name="known-limitations"></a><span data-ttu-id="f8f14-164">Bekende beperkingen</span><span class="sxs-lookup"><span data-stu-id="f8f14-164">Known Limitations</span></span>

- <span data-ttu-id="f8f14-165">Referenties die worden door gegeven binnen een script resource zijn niet altijd betrouwbaar wanneer een pull-of push server-model wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f8f14-165">Credentials being passed within a script resource are not always reliable when using a pull or push server model.</span></span> <span data-ttu-id="f8f14-166">Het is raadzaam om een volledige resource te gebruiken in plaats van een script bron in dit geval te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f8f14-166">It is recommended to use a full resource rather than use a script resource in this case.</span></span>
