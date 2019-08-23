---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Een DSC-resource met één instantie schrijven (aanbevolen)
ms.openlocfilehash: 4d9e07c6aaa064f808a03d4252e8d352b82183ec
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986521"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a>Een DSC-resource met één instantie schrijven (aanbevolen)

>**Opmerking:** Dit onderwerp beschrijft een best practice voor het definiëren van een DSC-resource waarmee slechts één exemplaar in een configuratie kan worden gedefinieerd. Er is momenteel geen ingebouwde DSC-functie om dit te doen. Dit kan in de toekomst worden gewijzigd.

Er zijn situaties waarin u niet wilt toestaan dat een resource meerdere keren in een configuratie wordt gebruikt. Zo kan een configuratie in een eerdere implementatie van de [xTimeZone](https://github.com/PowerShell/xTimeZone) -resource meerdere keren aanroepen, waarbij de tijd zone wordt ingesteld op een andere instelling in elk resource blok:

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

Dit komt door de manier waarop DSC-resource sleutels werken. Een resource moet ten minste één sleutel eigenschap hebben. Een bron exemplaar wordt als uniek beschouwd als de combi natie van de waarden van alle sleutel eigenschappen uniek is. In de vorige implementatie heeft de [xTimeZone](https://github.com/PowerShell/xTimeZone) -resource slechts één eigenschap--**time zone**, die vereist is om een sleutel te zijn. Als gevolg hiervan zou een configuratie zoals die hierboven zou worden gecompileerd en uitgevoerd zonder waarschuwing. Elk van de **xTimeZone** -resource blokken wordt als uniek beschouwd. Hierdoor wordt de configuratie herhaaldelijk toegepast op het knoop punt, en wordt de tijd zone terug en weer gegeven.

Om ervoor te zorgen dat een configuratie de tijd zone voor een doel knooppunt slechts eenmaal kan instellen, is de resource bijgewerkt om een tweede eigenschap toe te voegen, **IsSingleInstance**, die de sleutel eigenschap werd geworden.
De **IsSingleInstance** is beperkt tot één waarde, ' Yes ' door een **ValueMap**te gebruiken. Het oude MOF-schema voor de resource is:

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

Het bron script is ook bijgewerkt voor gebruik van de nieuwe para meter. Hier ziet u hoe het bron script is gewijzigd:

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

U ziet dat de eigenschap **time zone** niet langer een sleutel is. Als een configuratie nu twee keer probeert om de tijd zone in te stellen (door gebruik te maken van twee verschillende **xTimeZone** -blokken met verschillende **Tijdzone** waarden), treedt er een fout op:

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
