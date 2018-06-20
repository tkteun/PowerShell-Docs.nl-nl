---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Een DSC-resource met één instantie schrijven (aanbevolen)
ms.openlocfilehash: 9494964b1b13eaa082ad5cbc279b4586bb7211cc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218359"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a>Een DSC-resource met één instantie schrijven (aanbevolen)

>**Opmerking:** in dit onderwerp beschrijft aanbevolen procedure voor het definiëren van een DSC-resource waarmee slechts één exemplaar in een configuratie. Er is momenteel geen ingebouwde DSC-functie om dit te doen. Dat kan worden gewijzigd in de toekomst.

Zijn er situaties waarin u niet wilt toestaan dat een resource toe aan meerdere keren worden gebruikt in een configuratie. Bijvoorbeeld in een eerdere implementatie van de [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, een configuratie kan aanroepen de resource meerdere keren als u de tijdzone op een andere instelling in elk blok resource:

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

Dit is vanwege de manier waarop DSC-resource sleutels werkt. Een bron moet ten minste één sleuteleigenschap hebben. Een resource-instantie wordt beschouwd als uniek zijn als de combinatie van de waarden van alle van de sleuteleigenschappen uniek is. In de vorige implementatie de [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had u slechts één eigenschap--**tijdzone**, wat een sleutel is vereist. Als gevolg hiervan, zou een configuratie zoals hierboven compileren en uitvoeren zonder waarschuwing. Elk van de **xTimeZone** resource blokken wordt beschouwd als uniek. Hierdoor zou de configuratie van meerdere malen worden toegepast op het knooppunt, functioneert de tijdzone heen en weer.

Om ervoor te zorgen dat een configuratie kan de tijdzone instellen voor een doelknooppunt slechts een keer de resource is bijgewerkt voor het toevoegen van een tweede eigenschap **IsSingleInstance**, die de sleuteleigenschap is geworden.
De **IsSingleInstance** is beperkt tot een enkele waarde 'Ja' met behulp van een **ValueMap**. Het oude MOF-schema voor de resource is:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

Het bijgewerkte MOF-schema voor de resource is:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

De resource-script is ook bijgewerkt voor het gebruik van de nieuwe parameter. Dit is de oude resource-script:

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
    [CmdletBinding(SupportsShouldProcess=$true)]
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

    if($PSCmdlet.ShouldProcess("'$TimeZone'","Replace the System Time Zone"))
    {
        try
        {
            if($CurrentTimeZone -ne $TimeZone)
            {
                Write-Verbose -Verbose "Setting the TimeZone"
                Set-TimeZone -TimeZone $TimeZone}
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

U ziet dat de **tijdzone** eigenschap is niet langer een sleutel. Nu als een configuratie probeert in te stellen de tijdzone tweemaal (met behulp van twee verschillende **xTimeZone** blokken met verschillende **tijdzone** waarden), een fout opgetreden bij het compileren van de configuratie wordt:

```powershell
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