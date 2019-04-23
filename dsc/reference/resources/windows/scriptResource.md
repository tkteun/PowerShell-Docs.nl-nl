---
ms.date: 08/24/2018
keywords: DSC, powershell, configuratie en installatie
title: Script voor DSC-Resource
ms.openlocfilehash: 4eee5625add4d96ade7ababf7f534f597a26712d
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984286"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="a27be-103">Script voor DSC-Resource</span><span class="sxs-lookup"><span data-stu-id="a27be-103">DSC Script Resource</span></span>

> <span data-ttu-id="a27be-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="a27be-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="a27be-105">De **Script** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het uitvoeren van Windows PowerShell-scriptblokken op doelknooppunten.</span><span class="sxs-lookup"><span data-stu-id="a27be-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="a27be-106">De **Script** maakt gebruik van resource `GetScript`, `SetScript`, en `TestScript` -eigenschappen die u definieert om uit te voeren van de bijbehorende DSC scriptblokken bevatten status bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="a27be-106">The **Script** resource uses `GetScript`, `SetScript`, and `TestScript` properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="a27be-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a27be-107">Syntax</span></span>

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="a27be-108">De `GetScript`, `TestScript`, en `SetScript` blokken worden opgeslagen als tekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="a27be-108">The `GetScript`, `TestScript`, and `SetScript` blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="a27be-109">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="a27be-109">Properties</span></span>

|<span data-ttu-id="a27be-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="a27be-110">Property</span></span>|<span data-ttu-id="a27be-111">Description</span><span class="sxs-lookup"><span data-stu-id="a27be-111">Description</span></span>|
|--------|-----------|
|<span data-ttu-id="a27be-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="a27be-112">GetScript</span></span>|<span data-ttu-id="a27be-113">Een scriptblok waarmee de huidige status van het knooppunt wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="a27be-113">A script block that returns the current state of the Node.</span></span>|
|<span data-ttu-id="a27be-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="a27be-114">SetScript</span></span>|<span data-ttu-id="a27be-115">Een scriptblok die DSC gebruikt voor het afdwingen van naleving bij het knooppunt niet is opgenomen in de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="a27be-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span>|
|<span data-ttu-id="a27be-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="a27be-116">TestScript</span></span>|<span data-ttu-id="a27be-117">Een scriptblok die bepaalt of het knooppunt in de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="a27be-117">A script block that determines if the Node is in the desired state.</span></span>|
|<span data-ttu-id="a27be-118">Referentie</span><span class="sxs-lookup"><span data-stu-id="a27be-118">Credential</span></span>| <span data-ttu-id="a27be-119">Geeft aan dat de referenties wilt gebruiken voor het uitvoeren van dit script als referenties vereist zijn.</span><span class="sxs-lookup"><span data-stu-id="a27be-119">Indicates the credentials to use for running this script, if credentials are required.</span></span>|
|<span data-ttu-id="a27be-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a27be-120">DependsOn</span></span>| <span data-ttu-id="a27be-121">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="a27be-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a27be-122">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a27be-122">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

### <a name="getscript"></a><span data-ttu-id="a27be-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="a27be-123">GetScript</span></span>

<span data-ttu-id="a27be-124">DSC maakt geen gebruik van de uitvoer van `GetScript`.</span><span class="sxs-lookup"><span data-stu-id="a27be-124">DSC does not use the output from `GetScript`.</span></span> <span data-ttu-id="a27be-125">De [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet voert de `GetScript` om op te halen van de huidige status van een knooppunt.</span><span class="sxs-lookup"><span data-stu-id="a27be-125">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes the `GetScript` to retrieve a node's current state.</span></span> <span data-ttu-id="a27be-126">Een retourwaarde hoeft niet uit `GetScript`.</span><span class="sxs-lookup"><span data-stu-id="a27be-126">A return value is not required from `GetScript`.</span></span> <span data-ttu-id="a27be-127">Als u een retourwaarde opgeeft, moet dit een `hashtable` met een **resultaat** sleutel waarvan de waarde is een `String`.</span><span class="sxs-lookup"><span data-stu-id="a27be-127">If you specify a return value, it must be a `hashtable` containing a **Result** key whose value is a `String`.</span></span>

### <a name="testscript"></a><span data-ttu-id="a27be-128">TestScript</span><span class="sxs-lookup"><span data-stu-id="a27be-128">TestScript</span></span>

<span data-ttu-id="a27be-129">De `TestScript` wordt uitgevoerd door DSC om te bepalen of de `SetScript` moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a27be-129">The `TestScript` is executed by DSC to determine if the `SetScript` should be run.</span></span> <span data-ttu-id="a27be-130">Als de `TestScript` retourneert `$false`, DSC wordt uitgevoerd de `SetScript` om het knooppunt terug naar de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="a27be-130">If the `TestScript` returns `$false`, DSC executes the `SetScript` to bring the node back to the desired state.</span></span> <span data-ttu-id="a27be-131">De App moet retourneren een `boolean` waarde.</span><span class="sxs-lookup"><span data-stu-id="a27be-131">It must return a `boolean` value.</span></span> <span data-ttu-id="a27be-132">Een resultaat van `$true` geeft aan dat het knooppunt voldoet en `SetScript` moet niet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a27be-132">A result of `$true` indicates that the node is compliant and `SetScript` should not executed.</span></span>

<span data-ttu-id="a27be-133">De [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) -cmdlet voert de `TestScript` om op te halen van de naleving van de knooppunten van de **Script** resources.</span><span class="sxs-lookup"><span data-stu-id="a27be-133">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes the `TestScript` to retrieve the nodes compliance with the  **Script** resources.</span></span> <span data-ttu-id="a27be-134">Echter, in dit geval de `SetScript` niet wordt uitgevoerd, ongeacht wat de `TestScript` retourneert blokkeren.</span><span class="sxs-lookup"><span data-stu-id="a27be-134">However, in this case, the `SetScript` does not run, no matter what the `TestScript` block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="a27be-135">Alle uitvoer van uw `TestScript` maakt deel uit van de geretourneerde waarde.</span><span class="sxs-lookup"><span data-stu-id="a27be-135">All output from your `TestScript` is part of its return value.</span></span> <span data-ttu-id="a27be-136">PowerShell interpreteert unsuppressed uitvoer als niet-nul, wat dat betekent uw `TestScript` retourneert `$true` , ongeacht de status van het knooppunt.</span><span class="sxs-lookup"><span data-stu-id="a27be-136">PowerShell interprets unsuppressed output as non-zero, which means that your `TestScript` will return `$true` regardless of your node's state.</span></span>
> <span data-ttu-id="a27be-137">Dit leidt tot onvoorspelbare resultaten, fout-positieven, en zorgt ervoor dat problemen tijdens het oplossen van problemen.</span><span class="sxs-lookup"><span data-stu-id="a27be-137">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

### <a name="setscript"></a><span data-ttu-id="a27be-138">SetScript</span><span class="sxs-lookup"><span data-stu-id="a27be-138">SetScript</span></span>

<span data-ttu-id="a27be-139">De `SetScript` Hiermee wijzigt u het knooppunt om af te dwingen de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="a27be-139">The `SetScript` modifies the node to enforce the desired state.</span></span> <span data-ttu-id="a27be-140">Deze wordt aangeroepen door DSC als de `TestScript` script blok retourneert `$false`.</span><span class="sxs-lookup"><span data-stu-id="a27be-140">It is called by DSC if the `TestScript` script block returns `$false`.</span></span> <span data-ttu-id="a27be-141">De `SetScript` moet retourneren geen waarde hebben.</span><span class="sxs-lookup"><span data-stu-id="a27be-141">The `SetScript` should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="a27be-142">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="a27be-142">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="a27be-143">Voorbeeld 1: Voorbeeldtekst met behulp van de bron van een Script schrijven</span><span class="sxs-lookup"><span data-stu-id="a27be-143">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="a27be-144">In dit voorbeeld test sprake is van `C:\TempFolder\TestFile.txt` op elk knooppunt.</span><span class="sxs-lookup"><span data-stu-id="a27be-144">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="a27be-145">Als deze niet bestaat, wordt gemaakt met behulp van de `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="a27be-145">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="a27be-146">De `GetScript` retourneert de inhoud van het bestand en de geretourneerde waarde wordt niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a27be-146">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

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

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="a27be-147">Voorbeeld 2: Versie-informatie met behulp van een bron van het Script vergelijken</span><span class="sxs-lookup"><span data-stu-id="a27be-147">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="a27be-148">In dit voorbeeld wordt de *compatibel* versie-informatie uit een tekstbestand op de computer ontwerpen en slaat deze op in de `$version` variabele.</span><span class="sxs-lookup"><span data-stu-id="a27be-148">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="a27be-149">Bij het genereren van het knooppunt MOF-bestand, DSC vervangt de `$using:version` variabelen in elk script blokkeren met de waarde van de `$version` variabele.</span><span class="sxs-lookup"><span data-stu-id="a27be-149">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span> <span data-ttu-id="a27be-150">Tijdens de uitvoering, de *compatibel* versie is opgeslagen in een tekstbestand op elk knooppunt en vergeleken en op de volgende uitvoeringen worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="a27be-150">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

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
