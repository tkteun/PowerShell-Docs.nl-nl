---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-script resource
ms.openlocfilehash: e09e86011fa7dbb2a4d7f28b5032b4328b6f6ec2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941325"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="7a6dd-103">DSC-script resource</span><span class="sxs-lookup"><span data-stu-id="7a6dd-103">DSC Script Resource</span></span>

> <span data-ttu-id="7a6dd-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x</span><span class="sxs-lookup"><span data-stu-id="7a6dd-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="7a6dd-105">De **script** bron in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het uitvoeren van Windows Power shell-script blokken op doel knooppunten.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="7a6dd-106">De **script** bron maakt gebruik van **GetScript**-, **SetScript**-en **TestScript** -eigenschappen die script blokken bevatten die u definieert om de bijbehorende DSC-status bewerkingen uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-106">The **Script** resource uses **GetScript**, **SetScript**, and **TestScript** properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="7a6dd-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7a6dd-107">Syntax</span></span>

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
> <span data-ttu-id="7a6dd-108">**GetScript**-, **TestScript**-en **SetScript** -blokken worden opgeslagen als teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-108">**GetScript**, **TestScript**, and **SetScript** blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="7a6dd-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="7a6dd-109">Properties</span></span>

|<span data-ttu-id="7a6dd-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="7a6dd-110">Property</span></span> |<span data-ttu-id="7a6dd-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7a6dd-111">Description</span></span> |
|---|---|
|<span data-ttu-id="7a6dd-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="7a6dd-112">GetScript</span></span> |<span data-ttu-id="7a6dd-113">Een script blok dat de huidige status van het knoop punt retourneert.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-113">A script block that returns the current state of the Node.</span></span> |
|<span data-ttu-id="7a6dd-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="7a6dd-114">SetScript</span></span> |<span data-ttu-id="7a6dd-115">Een script blok dat door DSC wordt gebruikt om naleving af te dwingen wanneer het knoop punt niet de gewenste status heeft.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span> |
|<span data-ttu-id="7a6dd-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="7a6dd-116">TestScript</span></span> |<span data-ttu-id="7a6dd-117">Een script blok dat bepaalt of het knoop punt de gewenste status heeft.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-117">A script block that determines if the Node is in the desired state.</span></span> |
|<span data-ttu-id="7a6dd-118">Referentie</span><span class="sxs-lookup"><span data-stu-id="7a6dd-118">Credential</span></span> |<span data-ttu-id="7a6dd-119">Hiermee geeft u de referenties op die moeten worden gebruikt voor het uitvoeren van dit script, indien referenties vereist zijn.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-119">Indicates the credentials to use for running this script, if credentials are required.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="7a6dd-120">Algemene eigenschappen</span><span class="sxs-lookup"><span data-stu-id="7a6dd-120">Common properties</span></span>

|<span data-ttu-id="7a6dd-121">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="7a6dd-121">Property</span></span> |<span data-ttu-id="7a6dd-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7a6dd-122">Description</span></span> |
|---|---|
|<span data-ttu-id="7a6dd-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7a6dd-123">DependsOn</span></span> |<span data-ttu-id="7a6dd-124">Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7a6dd-125">De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-125">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="7a6dd-126">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7a6dd-126">PsDscRunAsCredential</span></span> |<span data-ttu-id="7a6dd-127">Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-127">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="7a6dd-128">De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-128">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="7a6dd-129">Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-129">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="7a6dd-130">Aanvullende informatie</span><span class="sxs-lookup"><span data-stu-id="7a6dd-130">Additional information</span></span>

#### <a name="getscript"></a><span data-ttu-id="7a6dd-131">GetScript</span><span class="sxs-lookup"><span data-stu-id="7a6dd-131">GetScript</span></span>

<span data-ttu-id="7a6dd-132">DSC maakt geen gebruik van de uitvoer van **GetScript**.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-132">DSC does not use the output from **GetScript**.</span></span> <span data-ttu-id="7a6dd-133">De cmdlet [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) voert **GetScript** uit om de huidige status van een knoop punt op te halen.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-133">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes **GetScript** to retrieve a node's current state.</span></span> <span data-ttu-id="7a6dd-134">Er is geen retour waarde vereist vanuit **GetScript**.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-134">A return value is not required from **GetScript**.</span></span> <span data-ttu-id="7a6dd-135">Als u een retour waarde opgeeft, moet deze een hashtabel zijn met een **resultaat** sleutel waarvan de waarde een teken reeks is.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-135">If you specify a return value, it must be a hashtable containing a **Result** key whose value is a String.</span></span>

#### <a name="testscript"></a><span data-ttu-id="7a6dd-136">TestScript</span><span class="sxs-lookup"><span data-stu-id="7a6dd-136">TestScript</span></span>

<span data-ttu-id="7a6dd-137">**TestScript** wordt uitgevoerd door DSC om te bepalen of **SetScript** moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-137">**TestScript** is executed by DSC to determine if **SetScript** should be run.</span></span> <span data-ttu-id="7a6dd-138">Als **TestScript** retourneert `$false`, voert DSC **SetScript** uit om het knoop punt weer in de gewenste staat te brengen.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-138">If **TestScript** returns `$false`, DSC executes **SetScript** to bring the node back to the desired state.</span></span> <span data-ttu-id="7a6dd-139">Deze moet een Booleaanse waarde Retour neren.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-139">It must return a boolean value.</span></span> <span data-ttu-id="7a6dd-140">Een resultaat van `$true` geeft aan dat het knoop punt compatibel is en dat **SetScript** niet moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-140">A result of `$true` indicates that the node is compliant and **SetScript** should not executed.</span></span>

<span data-ttu-id="7a6dd-141">Met de cmdlet [test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) wordt **TestScript** uitgevoerd om de knoop punten te verkrijgen die voldoen aan de **script** bronnen.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-141">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes **TestScript** to retrieve the nodes compliance with the **Script** resources.</span></span>
<span data-ttu-id="7a6dd-142">In dit geval wordt **SetScript** echter niet uitgevoerd, ongeacht welk **TestScript** Block retourneert.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-142">However, in this case, **SetScript** does not run, no matter what **TestScript** block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="7a6dd-143">Alle uitvoer van uw **TestScript** maakt deel uit van de geretourneerde waarde.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-143">All output from your **TestScript** is part of its return value.</span></span> <span data-ttu-id="7a6dd-144">Power shell interpreteert niet-onderdrukte uitvoer als niet-nul, **TestScript** wat betekent dat `$true` uw TestScript wordt geretourneerd, ongeacht de status van uw knoop punt.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-144">PowerShell interprets unsuppressed output as non-zero, which means that your **TestScript** will return `$true` regardless of your node's state.</span></span> <span data-ttu-id="7a6dd-145">Dit resulteert in onvoorspelbare resultaten, fout-positieven en veroorzaakt problemen tijdens het oplossen van problemen.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-145">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

#### <a name="setscript"></a><span data-ttu-id="7a6dd-146">SetScript</span><span class="sxs-lookup"><span data-stu-id="7a6dd-146">SetScript</span></span>

<span data-ttu-id="7a6dd-147">**SetScript** wijzigt het knoop punt om de gewenste status af te dwingen.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-147">**SetScript** modifies the node to enforce the desired state.</span></span> <span data-ttu-id="7a6dd-148">Deze wordt aangeroepen door DSC als het **TestScript** -script blok `$false`retourneert.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-148">It is called by DSC if the **TestScript** script block returns `$false`.</span></span> <span data-ttu-id="7a6dd-149">De **SetScript** mag geen retour waarde hebben.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-149">The **SetScript** should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="7a6dd-150">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="7a6dd-150">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="7a6dd-151">Voor beeld 1: voorbeeld tekst schrijven met behulp van een script resource</span><span class="sxs-lookup"><span data-stu-id="7a6dd-151">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="7a6dd-152">In dit voor beeld wordt getest of `C:\TempFolder\TestFile.txt` op elk knoop punt bestaat.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-152">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="7a6dd-153">Als deze niet bestaat, wordt deze gemaakt met behulp `SetScript`van de.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-153">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="7a6dd-154">Het `GetScript` retourneert de inhoud van het bestand en de geretourneerde waarde wordt niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-154">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

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

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="7a6dd-155">Voor beeld 2: versie-informatie vergelijken met een script resource</span><span class="sxs-lookup"><span data-stu-id="7a6dd-155">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="7a6dd-156">In dit voor beeld worden de gegevens van de *compatibele* versie opgehaald uit een tekst bestand op de ontwerp computer en `$version` opgeslagen in de variabele.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-156">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="7a6dd-157">Bij het genereren van het MOF-bestand van het knoop `$using:version` punt vervangt DSC de variabelen in elk script blok met `$version` de waarde van de variabele.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-157">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>
<span data-ttu-id="7a6dd-158">Tijdens de uitvoering wordt de *compatibele* versie opgeslagen in een tekst bestand op elk knoop punt en vergeleken en bijgewerkt bij de volgende uitvoeringen.</span><span class="sxs-lookup"><span data-stu-id="7a6dd-158">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

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