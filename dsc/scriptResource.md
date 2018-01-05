---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Bron van het DSC-Script
ms.openlocfilehash: 3824cbf48d980069b923d91e1fa24739e5d4e617
ms.sourcegitcommit: 378c7ed4e8c8c1c5fe71417b9ba672a4c990630b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2018
---
# <a name="dsc-script-resource"></a><span data-ttu-id="5f34f-103">Bron van het DSC-Script</span><span class="sxs-lookup"><span data-stu-id="5f34f-103">DSC Script Resource</span></span>

 
> <span data-ttu-id="5f34f-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5f34f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5f34f-105">De **Script** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het uitvoeren van Windows PowerShell-scriptblokken op de doelknooppunten.</span><span class="sxs-lookup"><span data-stu-id="5f34f-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="5f34f-106">De `Script` resource heeft `GetScript`, `SetScript`, en `TestScript` eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="5f34f-106">The `Script` resource has `GetScript`, `SetScript`, and `TestScript` properties.</span></span> <span data-ttu-id="5f34f-107">Deze eigenschappen moeten worden ingesteld op scriptblokken dat wordt uitgevoerd op elk doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="5f34f-107">These properties should be set to script blocks that will run on each target node.</span></span> 

<span data-ttu-id="5f34f-108">De `GetScript` scriptblok als resultaat moet een hashtabel die vertegenwoordigt de status van het huidige knooppunt.</span><span class="sxs-lookup"><span data-stu-id="5f34f-108">The `GetScript` script block should return a hashtable representing the state of the current node.</span></span> <span data-ttu-id="5f34f-109">De hash-tabel mag slechts één sleutelveld bevatten `Result` en de waarde moet van het type `String`.</span><span class="sxs-lookup"><span data-stu-id="5f34f-109">The hashtable must only contain one key `Result` and the value must be of type `String`.</span></span> <span data-ttu-id="5f34f-110">Het is niet vereist voor het resultaat opgeleverd.</span><span class="sxs-lookup"><span data-stu-id="5f34f-110">It is not required to return anything.</span></span> <span data-ttu-id="5f34f-111">DSC geen reactie met de uitvoer van deze scriptblok.</span><span class="sxs-lookup"><span data-stu-id="5f34f-111">DSC doesn't do anything with the output of this script block.</span></span>

<span data-ttu-id="5f34f-112">De `TestScript` scriptblok moet bepalen of het huidige knooppunt moet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="5f34f-112">The `TestScript` script block should determine if the current node needs to be modified.</span></span> <span data-ttu-id="5f34f-113">Er moet worden geretourneerd `$true` als het knooppunt bijgewerkt is.</span><span class="sxs-lookup"><span data-stu-id="5f34f-113">It should return `$true` if the node is up-to-date.</span></span> <span data-ttu-id="5f34f-114">Er moet worden geretourneerd `$false` als de configuratie van het knooppunt verouderd is en moet worden bijgewerkt door de `SetScript` scriptblok.</span><span class="sxs-lookup"><span data-stu-id="5f34f-114">It should return `$false` if the node's configuration is out-of-date and should be updated by the `SetScript` script block.</span></span> <span data-ttu-id="5f34f-115">De `TestScript` scriptblok wordt aangeroepen door DSC.</span><span class="sxs-lookup"><span data-stu-id="5f34f-115">The `TestScript` script block is called by DSC.</span></span>

<span data-ttu-id="5f34f-116">De `SetScript` scriptblok het knooppunt moet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="5f34f-116">The `SetScript` script block should modify the node.</span></span> <span data-ttu-id="5f34f-117">Deze wordt aangeroepen door DSC als de `TestScript` blokkeren return `$false`.</span><span class="sxs-lookup"><span data-stu-id="5f34f-117">It is called by DSC if the `TestScript` block return `$false`.</span></span>

<span data-ttu-id="5f34f-118">Als u wilt gebruiken van variabelen uit het configuratiescript in de `GetScript`, `TestScript`, of `SetScript` scriptblokken, gebruikt u de `$using:` bereik (Zie hieronder voor een voorbeeld).</span><span class="sxs-lookup"><span data-stu-id="5f34f-118">If you need to use variables from your configuration script in the `GetScript`, `TestScript`, or `SetScript` script blocks, use the `$using:` scope (see below for an example).</span></span>


## <a name="syntax"></a><span data-ttu-id="5f34f-119">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5f34f-119">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="5f34f-120">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="5f34f-120">Properties</span></span>

|  <span data-ttu-id="5f34f-121">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="5f34f-121">Property</span></span>  |  <span data-ttu-id="5f34f-122">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5f34f-122">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="5f34f-123">Ophalen script</span><span class="sxs-lookup"><span data-stu-id="5f34f-123">GetScript</span></span>| <span data-ttu-id="5f34f-124">Biedt een blok van Windows PowerShell-script dat wordt uitgevoerd wanneer u aanroept de [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f34f-124">Provides a block of Windows PowerShell script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) cmdlet.</span></span> <span data-ttu-id="5f34f-125">Dit blok moet een hashtabel retourneren.</span><span class="sxs-lookup"><span data-stu-id="5f34f-125">This block must return a hashtable.</span></span> <span data-ttu-id="5f34f-126">De hash-tabel mag slechts één sleutelveld bevatten **resultaat** en de waarde moet van het type **tekenreeks**.</span><span class="sxs-lookup"><span data-stu-id="5f34f-126">The hashtable must only contain one key **Result** and the value must be of type **String**.</span></span>| 
| <span data-ttu-id="5f34f-127">SetScript</span><span class="sxs-lookup"><span data-stu-id="5f34f-127">SetScript</span></span>| <span data-ttu-id="5f34f-128">Biedt een blok van Windows PowerShell-script.</span><span class="sxs-lookup"><span data-stu-id="5f34f-128">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="5f34f-129">Wanneer u aanroept de [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) -cmdlet de **TestScript** blok als eerste wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="5f34f-129">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** block runs first.</span></span> <span data-ttu-id="5f34f-130">Als de **TestScript** blokkeren retourneert **$false**, wordt de **SetScript** blok wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5f34f-130">If the **TestScript** block returns **$false**, the **SetScript** block will run.</span></span> <span data-ttu-id="5f34f-131">Als de **TestScript** blokkeren retourneert **$true**, wordt de **SetScript** blok wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5f34f-131">If the **TestScript** block returns **$true**, the **SetScript** block will not run.</span></span>| 
| <span data-ttu-id="5f34f-132">TestScript</span><span class="sxs-lookup"><span data-stu-id="5f34f-132">TestScript</span></span>| <span data-ttu-id="5f34f-133">Biedt een blok van Windows PowerShell-script.</span><span class="sxs-lookup"><span data-stu-id="5f34f-133">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="5f34f-134">Wanneer u aanroept de [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet dit blok wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5f34f-134">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this block runs.</span></span> <span data-ttu-id="5f34f-135">Als het resultaat **$false**, het blok SetScript wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5f34f-135">If it returns **$false**, the SetScript block will run.</span></span> <span data-ttu-id="5f34f-136">Als het resultaat **$true**, SetScript blok wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5f34f-136">If it returns **$true**, the SetScript block will not run.</span></span> <span data-ttu-id="5f34f-137">De **TestScript** blok wordt ook uitgevoerd wanneer u aanroept de [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f34f-137">The **TestScript** block also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="5f34f-138">Echter, in dit geval de **SetScript** blok wordt niet uitgevoerd, ongeacht welke het TestScript waarde blokkeren retourneert.</span><span class="sxs-lookup"><span data-stu-id="5f34f-138">However, in this case, the **SetScript** block will not run, no matter what value the TestScript block returns.</span></span> <span data-ttu-id="5f34f-139">De **TestScript** blok moet True worden geretourneerd als de configuratie van de werkelijke overeenkomt met de huidige configuratie van de gewenste status en False als komt niet overeen met.</span><span class="sxs-lookup"><span data-stu-id="5f34f-139">The **TestScript** block must return True if the actual configuration matches the current desired state configuration, and False if it does not match.</span></span> <span data-ttu-id="5f34f-140">(De huidige configuratie van de gewenste status is de laatste configuratie van kracht op het knooppunt dat van DSC gebruikmaakt.)</span><span class="sxs-lookup"><span data-stu-id="5f34f-140">(The current desired state configuration is the last configuration enacted on the node that is using DSC.)</span></span>| 
| <span data-ttu-id="5f34f-141">referentie</span><span class="sxs-lookup"><span data-stu-id="5f34f-141">Credential</span></span>| <span data-ttu-id="5f34f-142">Hiermee geeft u de referenties gebruiken om dit script uit te voeren als de referenties zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="5f34f-142">Indicates the credentials to use for running this script, if credentials are required.</span></span>| 
| <span data-ttu-id="5f34f-143">dependsOn</span><span class="sxs-lookup"><span data-stu-id="5f34f-143">DependsOn</span></span>| <span data-ttu-id="5f34f-144">Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="5f34f-144">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5f34f-145">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="5f34f-145">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

## <a name="example-1"></a><span data-ttu-id="5f34f-146">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="5f34f-146">Example 1</span></span>
```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript = 
        { 
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }          
    }
}
```

## <a name="example-2"></a><span data-ttu-id="5f34f-147">Voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="5f34f-147">Example 2</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = { 
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Result' = "$currentVersion" }
        }          
        TestScript = { 
            $state = $GetScript
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
```

<span data-ttu-id="5f34f-148">Deze bron is de versie van de configuratie naar een tekstbestand schrijven.</span><span class="sxs-lookup"><span data-stu-id="5f34f-148">This resource is writing the configuration's version to a text file.</span></span> <span data-ttu-id="5f34f-149">Deze versie beschikbaar is op de clientcomputer, maar bevindt zich niet op een van de knooppunten, dus het moet worden doorgegeven aan elk van de `Script` scriptblokken van de resource met de PowerShell `using` bereik.</span><span class="sxs-lookup"><span data-stu-id="5f34f-149">This version is available on the client computer, but isn't on any of the nodes, so it has to be passed to each of the `Script` resource's script blocks with PowerShell's `using` scope.</span></span> <span data-ttu-id="5f34f-150">Wanneer het genereren van het knooppunt MOF-bestand, de waarde van de `$version` variabele wordt gelezen uit een tekstbestand op de clientcomputer.</span><span class="sxs-lookup"><span data-stu-id="5f34f-150">When generating the node's MOF file, the value of the `$version` variable is read from a text file on the client computer.</span></span> <span data-ttu-id="5f34f-151">DSC-vervangt de `$using:version` variabelen in elk script blokkeren met de waarde van de `$version` variabele.</span><span class="sxs-lookup"><span data-stu-id="5f34f-151">DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>

