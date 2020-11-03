---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-pscallstack?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSCallStack
ms.openlocfilehash: 45c2ea5bc166e2d21153ae8b19c1c0afe4ca0640
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93247173"
---
# <span data-ttu-id="82c5a-103">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="82c5a-103">Get-PSCallStack</span></span>

## <span data-ttu-id="82c5a-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="82c5a-104">SYNOPSIS</span></span>
<span data-ttu-id="82c5a-105">Hiermee wordt de huidige aanroep stack weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="82c5a-105">Displays the current call stack.</span></span>

## <span data-ttu-id="82c5a-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="82c5a-106">SYNTAX</span></span>

```
Get-PSCallStack [<CommonParameters>]
```

## <span data-ttu-id="82c5a-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="82c5a-107">DESCRIPTION</span></span>
<span data-ttu-id="82c5a-108">Met de cmdlet **Get-PSCallStack** wordt de huidige aanroep stack weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="82c5a-108">The **Get-PSCallStack** cmdlet displays the current call stack.</span></span>

<span data-ttu-id="82c5a-109">Hoewel het is ontworpen om te worden gebruikt in combi natie met de Windows Power shell-debugger, kunt u deze cmdlet gebruiken om de aanroep stack weer te geven in een script of functie buiten het fout opsporingsprogramma.</span><span class="sxs-lookup"><span data-stu-id="82c5a-109">Although it is designed to be used with the Windows PowerShell debugger, you can use this cmdlet to display the call stack in a script or function outside of the debugger.</span></span>

<span data-ttu-id="82c5a-110">Als u de opdracht **Get-PSCallStack** wilt uitvoeren terwijl het fout opsporingsprogramma is, typt `k` of `Get-PSCallStack` .</span><span class="sxs-lookup"><span data-stu-id="82c5a-110">To run a **Get-PSCallStack** command while in the debugger, type `k` or `Get-PSCallStack`.</span></span>

## <span data-ttu-id="82c5a-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="82c5a-111">EXAMPLES</span></span>

### <span data-ttu-id="82c5a-112">Voor beeld 1: de aanroep stack ophalen voor een functie</span><span class="sxs-lookup"><span data-stu-id="82c5a-112">Example 1: Get the call stack for a function</span></span>

```
PS C:\> function my-alias {
$p = $args[0]
Get-Alias | where {$_.definition -like "*$p"} | format-table definition, name -auto
}
PS C:\ps-test> Set-PSBreakpoint -Command my-alias
Command    : my-alias
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : prompt PS C:\> my-alias Get-Content

Entering debug mode. Use h or ? for help.
Hit Command breakpoint on 'prompt:my-alias'
my-alias get-content
[DBG]: PS C:\ps-test> s
$p = $args[0]
DEBUG: Stepped to ':    $p = $args[0]    '
[DBG]: PS C:\ps-test> s
get-alias | Where {$_.Definition -like "*$p*"} | format-table Definition,
[DBG]: PS C:\ps-test>get-pscallstack

Name        CommandLineParameters         UnboundArguments              Location
----        ---------------------         ----------------              --------
prompt      {}                            {}                            prompt
my-alias    {}                            {get-content}                 prompt
prompt      {}                            {}                            prompt PS C:\> [DBG]: PS C:\ps-test> o
Definition  Name
----------  ----
Get-Content gc
Get-Content cat
Get-Content type
```

<span data-ttu-id="82c5a-113">Met deze opdracht wordt de cmdlet **Get-PSCallStack** gebruikt voor het weer geven van de aanroep stack voor mijn-alias, een eenvoudige functie die de aliassen voor de naam van een cmdlet ophaalt.</span><span class="sxs-lookup"><span data-stu-id="82c5a-113">This command uses the **Get-PSCallStack** cmdlet to display the call stack for My-Alias, a simple function that gets the aliases for a cmdlet name.</span></span>

<span data-ttu-id="82c5a-114">De eerste opdracht voert de functie in bij de Windows Power shell-prompt.</span><span class="sxs-lookup"><span data-stu-id="82c5a-114">The first command enters the function at the Windows PowerShell prompt.</span></span>
<span data-ttu-id="82c5a-115">De tweede opdracht maakt gebruik van de cmdlet Set-PSBreakpoint om een onderbrekings punt in te stellen voor de functie My-Alias.</span><span class="sxs-lookup"><span data-stu-id="82c5a-115">The second command uses the Set-PSBreakpoint cmdlet to set a breakpoint on the My-Alias function.</span></span>
<span data-ttu-id="82c5a-116">De derde opdracht gebruikt de functie My-Alias om alle aliassen in de huidige sessie op te halen voor de Get-Content-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="82c5a-116">The third command uses the My-Alias function to get all of the aliases in the current session for the Get-Content cmdlet.</span></span>

<span data-ttu-id="82c5a-117">Het fout opsporingsprogramma breekt op bij de functie aanroep.</span><span class="sxs-lookup"><span data-stu-id="82c5a-117">The debugger breaks in at the function call.</span></span>
<span data-ttu-id="82c5a-118">Er zijn twee opeenvolgende opdrachten voor het uitvoeren van de functie regel per regel.</span><span class="sxs-lookup"><span data-stu-id="82c5a-118">Two consecutive step-into (s) commands begin executing the function line by line.</span></span>
<span data-ttu-id="82c5a-119">Vervolgens wordt de opdracht **Get-PSCallStack** gebruikt om de aanroep stack op te halen.</span><span class="sxs-lookup"><span data-stu-id="82c5a-119">Then, a **Get-PSCallStack** command is used to retrieve the call stack.</span></span>

<span data-ttu-id="82c5a-120">De laatste opdracht is een Step-Out-opdracht (o) waarmee de fout opsporing wordt afgesloten en het script verder wordt uitgevoerd om te worden voltooid.</span><span class="sxs-lookup"><span data-stu-id="82c5a-120">The final command is a Step-Out command (o) that exits the debugger and continues executing the script to completion.</span></span>

## <span data-ttu-id="82c5a-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="82c5a-121">PARAMETERS</span></span>

### <span data-ttu-id="82c5a-122">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="82c5a-122">CommonParameters</span></span>
<span data-ttu-id="82c5a-123">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="82c5a-123">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="82c5a-124">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="82c5a-124">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="82c5a-125">INVOER</span><span class="sxs-lookup"><span data-stu-id="82c5a-125">INPUTS</span></span>

### <span data-ttu-id="82c5a-126">Geen</span><span class="sxs-lookup"><span data-stu-id="82c5a-126">None</span></span>
<span data-ttu-id="82c5a-127">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="82c5a-127">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="82c5a-128">UITVOER</span><span class="sxs-lookup"><span data-stu-id="82c5a-128">OUTPUTS</span></span>

### <span data-ttu-id="82c5a-129">System. Management. Automation. CallStackFrame</span><span class="sxs-lookup"><span data-stu-id="82c5a-129">System.Management.Automation.CallStackFrame</span></span>
<span data-ttu-id="82c5a-130">**Get-PSCallStack** retourneert een-object dat de items in de aanroep stack vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="82c5a-130">**Get-PSCallStack** returns an object that represents the items in the call stack.</span></span>

## <span data-ttu-id="82c5a-131">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="82c5a-131">NOTES</span></span>

## <span data-ttu-id="82c5a-132">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="82c5a-132">RELATED LINKS</span></span>

[<span data-ttu-id="82c5a-133">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="82c5a-133">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="82c5a-134">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="82c5a-134">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="82c5a-135">Format-Table</span><span class="sxs-lookup"><span data-stu-id="82c5a-135">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="82c5a-136">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="82c5a-136">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="82c5a-137">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="82c5a-137">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="82c5a-138">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="82c5a-138">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
