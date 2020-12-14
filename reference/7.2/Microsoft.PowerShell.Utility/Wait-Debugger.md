---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-debugger?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Debugger
ms.openlocfilehash: a2ef114a43a63b18f5dc2d28acf7cbc0de8392bd
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705695"
---
# <span data-ttu-id="f583e-102">Wait-Debugger</span><span class="sxs-lookup"><span data-stu-id="f583e-102">Wait-Debugger</span></span>

## <span data-ttu-id="f583e-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f583e-103">SYNOPSIS</span></span>
<span data-ttu-id="f583e-104">Stopt een script in het fout opsporingsprogramma voordat de volgende instructie in het script wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f583e-104">Stops a script in the debugger before running the next statement in the script.</span></span>

## <span data-ttu-id="f583e-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f583e-105">SYNTAX</span></span>

```
Wait-Debugger [<CommonParameters>]
```

## <span data-ttu-id="f583e-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f583e-106">DESCRIPTION</span></span>

<span data-ttu-id="f583e-107">Stopt de uitvoerings engine van Power shell-script op het punt onmiddellijk na de `Wait-Debugger` cmdlet en wacht totdat een fout opsporingsprogramma is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="f583e-107">Stops the PowerShell script execution engine at the point immediately after the `Wait-Debugger` cmdlet and waits for a debugger to be attached.</span></span> <span data-ttu-id="f583e-108">Dit is vergelijkbaar met het gebruik `Enable-RunspaceDebug -BreakAll` in een DSC-resource, maar verbreekt op een specifiek punt in het script.</span><span class="sxs-lookup"><span data-stu-id="f583e-108">This is similar to using `Enable-RunspaceDebug -BreakAll` in a DSC resource but breaks at a specific point in the script.</span></span>

> [!CAUTION]
> <span data-ttu-id="f583e-109">Zorg ervoor dat u de `Wait-Debugger` regels verwijdert nadat u klaar bent.</span><span class="sxs-lookup"><span data-stu-id="f583e-109">Make sure you remove the `Wait-Debugger` lines after you are done.</span></span> <span data-ttu-id="f583e-110">Een actief script lijkt te zijn vastgelopen wanneer het wordt gestopt bij a `Wait-Debugger` .</span><span class="sxs-lookup"><span data-stu-id="f583e-110">A running script appears to be hung when it is stopped at a `Wait-Debugger`.</span></span>

## <span data-ttu-id="f583e-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f583e-111">EXAMPLES</span></span>

### <span data-ttu-id="f583e-112">Voor beeld 1: onderbrekings punt invoegen voor fout opsporing</span><span class="sxs-lookup"><span data-stu-id="f583e-112">Example 1: Insert breakpoint for debugging</span></span>

```
[DscResource()]
class FileResource
{
    [DscProperty(Key)]
    [string] $Path

    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    [DscProperty(Mandatory)]
    [string] $SourcePath

    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime


    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (! $fileExists)
            {
               $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    [bool] Test()
    {
        $present = Test-Path -LiteralPath $this.Path

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return (! $present)
        }
    }

    [FileResource] Get()
    {
        $present = Test-Path -Path $this.Path

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    [void] CopyFile()
    {
        # Testing only - Remove before deployment!
        Wait-Debugger

        if (! (Test-Path -LiteralPath $this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose "Copying $($this.SourcePath) to $($this.Path)"

        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
}
```

## <span data-ttu-id="f583e-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f583e-113">PARAMETERS</span></span>

### <span data-ttu-id="f583e-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f583e-114">CommonParameters</span></span>

<span data-ttu-id="f583e-115">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f583e-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f583e-116">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f583e-116">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="f583e-117">INVOER</span><span class="sxs-lookup"><span data-stu-id="f583e-117">INPUTS</span></span>

### <span data-ttu-id="f583e-118">Geen</span><span class="sxs-lookup"><span data-stu-id="f583e-118">None</span></span>

## <span data-ttu-id="f583e-119">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f583e-119">OUTPUTS</span></span>

### <span data-ttu-id="f583e-120">Geen</span><span class="sxs-lookup"><span data-stu-id="f583e-120">None</span></span>

## <span data-ttu-id="f583e-121">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f583e-121">NOTES</span></span>

## <span data-ttu-id="f583e-122">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f583e-122">RELATED LINKS</span></span>

[<span data-ttu-id="f583e-123">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="f583e-123">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)

