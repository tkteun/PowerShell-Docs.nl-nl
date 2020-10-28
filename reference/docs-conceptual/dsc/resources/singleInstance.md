---
ms.date: 07/08/2020
keywords: DSC, Power shell, configuratie, installatie
title: Een DSC-resource met één instantie schrijven (aanbevolen)
description: In dit artikel wordt een best practice beschreven voor het definiëren van een DSC-resource waarmee slechts één exemplaar in een configuratie kan worden gedefinieerd.
ms.openlocfilehash: 4744136b5a733c86b517b239b2c37ce57a4246f7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662643"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="47e7b-104">Een DSC-resource met één instantie schrijven (aanbevolen)</span><span class="sxs-lookup"><span data-stu-id="47e7b-104">Writing a single-instance DSC resource (best practice)</span></span>

> [!NOTE]
> <span data-ttu-id="47e7b-105">In dit artikel wordt een best practice beschreven voor het definiëren van een DSC-resource waarmee slechts één exemplaar in een configuratie kan worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="47e7b-105">This article describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="47e7b-106">Er is momenteel geen ingebouwde DSC-functie om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="47e7b-106">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="47e7b-107">Dit kan in de toekomst worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="47e7b-107">That might change in the future.</span></span>

<span data-ttu-id="47e7b-108">Er zijn situaties waarin u niet wilt toestaan dat een resource meerdere keren in een configuratie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="47e7b-108">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="47e7b-109">Zo kan een configuratie in een eerdere implementatie van de [xTimeZone](https://github.com/PowerShell/xTimeZone) -resource meerdere keren aanroepen, waarbij de tijd zone wordt ingesteld op een andere instelling in elk resource blok:</span><span class="sxs-lookup"><span data-stu-id="47e7b-109">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

```powershell
Configuration SetTimeZone
{
    Param
    (
        [String[]]$NodeName = $env:COMPUTERNAME

    )

    Import-DSCResource -ModuleName xTimeZone


    Node $NodeName
    {
         xTimeZone TimeZoneExample
         {

            TimeZone = 'Eastern Standard Time'
         }

         xTimeZone TimeZoneExample2
         {

            TimeZone = 'Pacific Standard Time'

         }

    }
}
```

<span data-ttu-id="47e7b-110">Dit komt door de manier waarop DSC-resource sleutels werken.</span><span class="sxs-lookup"><span data-stu-id="47e7b-110">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="47e7b-111">Een resource moet ten minste één sleutel eigenschap hebben.</span><span class="sxs-lookup"><span data-stu-id="47e7b-111">A resource must have at least one key property.</span></span> <span data-ttu-id="47e7b-112">Een bron exemplaar wordt als uniek beschouwd als de combi natie van de waarden van alle sleutel eigenschappen uniek is.</span><span class="sxs-lookup"><span data-stu-id="47e7b-112">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="47e7b-113">In de vorige implementatie heeft de [xTimeZone](https://github.com/PowerShell/xTimeZone) -resource slechts één eigenschap-- **time zone** , die vereist is om een sleutel te zijn.</span><span class="sxs-lookup"><span data-stu-id="47e7b-113">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property-- **TimeZone** , which was required to be a key.</span></span> <span data-ttu-id="47e7b-114">Als gevolg hiervan zou een configuratie zoals die hierboven zou worden gecompileerd en uitgevoerd zonder waarschuwing.</span><span class="sxs-lookup"><span data-stu-id="47e7b-114">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="47e7b-115">Elk van de **xTimeZone** -resource blokken wordt als uniek beschouwd.</span><span class="sxs-lookup"><span data-stu-id="47e7b-115">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="47e7b-116">Hierdoor wordt de configuratie herhaaldelijk toegepast op het knoop punt, en wordt de tijd zone terug en weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="47e7b-116">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="47e7b-117">Om ervoor te zorgen dat een configuratie de tijd zone voor een doel knooppunt slechts eenmaal kan instellen, is de resource bijgewerkt om een tweede eigenschap toe te voegen, **IsSingleInstance** , die de sleutel eigenschap werd geworden.</span><span class="sxs-lookup"><span data-stu-id="47e7b-117">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance** , that became the key property.</span></span> <span data-ttu-id="47e7b-118">De **IsSingleInstance** is beperkt tot één waarde, ' Yes ' door een **ValueMap** te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="47e7b-118">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap** .</span></span> <span data-ttu-id="47e7b-119">Het oude MOF-schema voor de resource is:</span><span class="sxs-lookup"><span data-stu-id="47e7b-119">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="47e7b-120">Het bijgewerkte MOF-schema voor de resource is:</span><span class="sxs-lookup"><span data-stu-id="47e7b-120">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="47e7b-121">Het bron script is ook bijgewerkt voor gebruik van de nieuwe para meter.</span><span class="sxs-lookup"><span data-stu-id="47e7b-121">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="47e7b-122">Hier ziet u hoe het bron script is gewijzigd:</span><span class="sxs-lookup"><span data-stu-id="47e7b-122">Here how the resource script was changed:</span></span>

```powershell
function Get-TargetResource
{
    [CmdletBinding()]
    [OutputType([Hashtable])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Get the current TimeZone
    $CurrentTimeZone = Get-TimeZone

    $returnValue = @{
        TimeZone = $CurrentTimeZone
        IsSingleInstance = 'Yes'
    }

    #Output the target resource
    $returnValue
}

function Set-TargetResource
{
    [CmdletBinding()]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output the result of Get-TargetResource function.
    $CurrentTimeZone = Get-TimeZone

    Write-Verbose -Message "Replace the System Time Zone to $TimeZone"

    try
    {
        if($CurrentTimeZone -ne $TimeZone)
        {
            Write-Verbose -Verbose "Setting the TimeZone"
            Set-TimeZone -TimeZone $TimeZone
        }
        else
        {
            Write-Verbose -Verbose "TimeZone already set to $TimeZone"
        }
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose -Verbose $ErrorMsg
    }
}


function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([Boolean])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output from Get-TargetResource
    $CurrentTimeZone = Get-TimeZone

    if($TimeZone -eq $CurrentTimeZone)
    {
        return $true
    }
    else
    {
        return $false
    }
}

Function Get-TimeZone {
    [CmdletBinding()]
    param()

    & tzutil.exe /g
}

Function Set-TimeZone {
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true)]
        [System.String]
        $TimeZone
    )

    try
    {
        & tzutil.exe /s $TimeZone
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose $ErrorMsg
    }
}

Export-ModuleMember -Function *-TargetResource
```

<span data-ttu-id="47e7b-123">U ziet dat de eigenschap **time zone** niet langer een sleutel is.</span><span class="sxs-lookup"><span data-stu-id="47e7b-123">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="47e7b-124">Als een configuratie nu twee keer probeert om de tijd zone in te stellen (door gebruik te maken van twee verschillende **xTimeZone** -blokken met verschillende **Tijdzone** waarden), treedt er een fout op:</span><span class="sxs-lookup"><span data-stu-id="47e7b-124">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

```Output
Test-ConflictingResources : A conflict was detected between resources '[xTimeZone]TimeZoneExample (::15::10::xTimeZone)' and
'[xTimeZone]TimeZoneExample2 (::22::10::xTimeZone)' in node 'CONTOSO-CLIENT'. Resources have identical key properties but there are differences in the
following non-key properties: 'TimeZone'. Values 'Eastern Standard Time' don't match values 'Pacific Standard Time'. Please update these property
values so that they are identical in both cases.
At line:271 char:9
+         Test-ConflictingResources $keywordName $canonicalizedValue $k ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : ConflictingDuplicateResource,Test-ConflictingResources
Errors occurred while processing configuration 'SetTimeZone'.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3705 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (SetTimeZone:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```
