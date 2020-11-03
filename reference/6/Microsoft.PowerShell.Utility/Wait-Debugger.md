---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-debugger?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Debugger
ms.openlocfilehash: 7c850b94e2c64d8beb72a83fe8ae503594d20864
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93249269"
---
# <span data-ttu-id="9a565-103">Wait-Debugger</span><span class="sxs-lookup"><span data-stu-id="9a565-103">Wait-Debugger</span></span>

## <span data-ttu-id="9a565-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9a565-104">SYNOPSIS</span></span>
<span data-ttu-id="9a565-105">Stopt een script in het fout opsporingsprogramma voordat de volgende instructie in het script wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9a565-105">Stops a script in the debugger before running the next statement in the script.</span></span>

## <span data-ttu-id="9a565-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9a565-106">SYNTAX</span></span>

```
Wait-Debugger [<CommonParameters>]
```

## <span data-ttu-id="9a565-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9a565-107">DESCRIPTION</span></span>

<span data-ttu-id="9a565-108">Stopt de uitvoerings engine van Power shell-script op het punt onmiddellijk na de `Wait-Debugger` cmdlet en wacht totdat een fout opsporingsprogramma is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="9a565-108">Stops the PowerShell script execution engine at the point immediately after the `Wait-Debugger` cmdlet and waits for a debugger to be attached.</span></span> <span data-ttu-id="9a565-109">Dit is vergelijkbaar met het gebruik `Enable-RunspaceDebug -BreakAll` in een DSC-resource, maar verbreekt op een specifiek punt in het script.</span><span class="sxs-lookup"><span data-stu-id="9a565-109">This is similar to using `Enable-RunspaceDebug -BreakAll` in a DSC resource but breaks at a specific point in the script.</span></span>

> [!CAUTION]
> <span data-ttu-id="9a565-110">Zorg ervoor dat u de `Wait-Debugger` regels verwijdert nadat u klaar bent.</span><span class="sxs-lookup"><span data-stu-id="9a565-110">Make sure you remove the `Wait-Debugger` lines after you are done.</span></span> <span data-ttu-id="9a565-111">Een actief script lijkt te zijn vastgelopen wanneer het wordt gestopt bij a `Wait-Debugger` .</span><span class="sxs-lookup"><span data-stu-id="9a565-111">A running script appears to be hung when it is stopped at a `Wait-Debugger`.</span></span>

## <span data-ttu-id="9a565-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9a565-112">EXAMPLES</span></span>

### <span data-ttu-id="9a565-113">Voor beeld 1: onderbrekings punt invoegen voor fout opsporing</span><span class="sxs-lookup"><span data-stu-id="9a565-113">Example 1: Insert breakpoint for debugging</span></span>

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

## <span data-ttu-id="9a565-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9a565-114">PARAMETERS</span></span>

### <span data-ttu-id="9a565-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9a565-115">CommonParameters</span></span>

<span data-ttu-id="9a565-116">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9a565-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9a565-117">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9a565-117">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="9a565-118">INVOER</span><span class="sxs-lookup"><span data-stu-id="9a565-118">INPUTS</span></span>

### <span data-ttu-id="9a565-119">Geen</span><span class="sxs-lookup"><span data-stu-id="9a565-119">None</span></span>

## <span data-ttu-id="9a565-120">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9a565-120">OUTPUTS</span></span>

### <span data-ttu-id="9a565-121">Geen</span><span class="sxs-lookup"><span data-stu-id="9a565-121">None</span></span>

## <span data-ttu-id="9a565-122">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9a565-122">NOTES</span></span>

## <span data-ttu-id="9a565-123">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9a565-123">RELATED LINKS</span></span>

[<span data-ttu-id="9a565-124">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="9a565-124">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
