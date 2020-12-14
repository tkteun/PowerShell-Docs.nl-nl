---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-pscallstack?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSCallStack
ms.openlocfilehash: 607e3999a1dbe9a4f22a751f11ac93ee3f9d9409
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705436"
---
# <span data-ttu-id="1c173-102">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="1c173-102">Get-PSCallStack</span></span>

## <span data-ttu-id="1c173-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1c173-103">SYNOPSIS</span></span>
<span data-ttu-id="1c173-104">Hiermee wordt de huidige aanroep stack weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1c173-104">Displays the current call stack.</span></span>

## <span data-ttu-id="1c173-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1c173-105">SYNTAX</span></span>

```
Get-PSCallStack [<CommonParameters>]
```

## <span data-ttu-id="1c173-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1c173-106">DESCRIPTION</span></span>

<span data-ttu-id="1c173-107">Met de cmdlet **Get-PSCallStack** wordt de huidige aanroep stack weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1c173-107">The **Get-PSCallStack** cmdlet displays the current call stack.</span></span>

<span data-ttu-id="1c173-108">Hoewel het is ontworpen om te worden gebruikt met de Power Shell-fout opsporing, kunt u deze cmdlet gebruiken om de aanroep stack weer te geven in een script of functie buiten het fout opsporingsprogramma.</span><span class="sxs-lookup"><span data-stu-id="1c173-108">Although it is designed to be used with the PowerShell debugger, you can use this cmdlet to display the call stack in a script or function outside of the debugger.</span></span>

<span data-ttu-id="1c173-109">Als u de opdracht **Get-PSCallStack** wilt uitvoeren terwijl het fout opsporingsprogramma is, typt `k` of `Get-PSCallStack` .</span><span class="sxs-lookup"><span data-stu-id="1c173-109">To run a **Get-PSCallStack** command while in the debugger, type `k` or `Get-PSCallStack`.</span></span>

## <span data-ttu-id="1c173-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1c173-110">EXAMPLES</span></span>

### <span data-ttu-id="1c173-111">Voor beeld 1: de aanroep stack ophalen voor een functie</span><span class="sxs-lookup"><span data-stu-id="1c173-111">Example 1: Get the call stack for a function</span></span>

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

<span data-ttu-id="1c173-112">Met deze opdracht wordt de cmdlet **Get-PSCallStack** gebruikt voor het weer geven van de aanroep stack voor mijn-alias, een eenvoudige functie die de aliassen voor de naam van een cmdlet ophaalt.</span><span class="sxs-lookup"><span data-stu-id="1c173-112">This command uses the **Get-PSCallStack** cmdlet to display the call stack for My-Alias, a simple function that gets the aliases for a cmdlet name.</span></span>

<span data-ttu-id="1c173-113">De eerste opdracht voert de functie in bij de Power shell-prompt.</span><span class="sxs-lookup"><span data-stu-id="1c173-113">The first command enters the function at the PowerShell prompt.</span></span>
<span data-ttu-id="1c173-114">De tweede opdracht maakt gebruik van de cmdlet Set-PSBreakpoint om een onderbrekings punt in te stellen voor de functie My-Alias.</span><span class="sxs-lookup"><span data-stu-id="1c173-114">The second command uses the Set-PSBreakpoint cmdlet to set a breakpoint on the My-Alias function.</span></span>
<span data-ttu-id="1c173-115">De derde opdracht gebruikt de functie My-Alias om alle aliassen in de huidige sessie op te halen voor de Get-Content-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c173-115">The third command uses the My-Alias function to get all of the aliases in the current session for the Get-Content cmdlet.</span></span>

<span data-ttu-id="1c173-116">Het fout opsporingsprogramma breekt op bij de functie aanroep.</span><span class="sxs-lookup"><span data-stu-id="1c173-116">The debugger breaks in at the function call.</span></span>
<span data-ttu-id="1c173-117">Er zijn twee opeenvolgende opdrachten voor het uitvoeren van de functie regel per regel.</span><span class="sxs-lookup"><span data-stu-id="1c173-117">Two consecutive step-into (s) commands begin executing the function line by line.</span></span>
<span data-ttu-id="1c173-118">Vervolgens wordt de opdracht **Get-PSCallStack** gebruikt om de aanroep stack op te halen.</span><span class="sxs-lookup"><span data-stu-id="1c173-118">Then, a **Get-PSCallStack** command is used to retrieve the call stack.</span></span>

<span data-ttu-id="1c173-119">De laatste opdracht is een Step-Out-opdracht (o) waarmee de fout opsporing wordt afgesloten en het script verder wordt uitgevoerd om te worden voltooid.</span><span class="sxs-lookup"><span data-stu-id="1c173-119">The final command is a Step-Out command (o) that exits the debugger and continues executing the script to completion.</span></span>

## <span data-ttu-id="1c173-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1c173-120">PARAMETERS</span></span>

### <span data-ttu-id="1c173-121">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1c173-121">CommonParameters</span></span>

<span data-ttu-id="1c173-122">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1c173-122">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1c173-123">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1c173-123">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1c173-124">INVOER</span><span class="sxs-lookup"><span data-stu-id="1c173-124">INPUTS</span></span>

### <span data-ttu-id="1c173-125">Geen</span><span class="sxs-lookup"><span data-stu-id="1c173-125">None</span></span>

<span data-ttu-id="1c173-126">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="1c173-126">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="1c173-127">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1c173-127">OUTPUTS</span></span>

### <span data-ttu-id="1c173-128">System. Management. Automation. CallStackFrame</span><span class="sxs-lookup"><span data-stu-id="1c173-128">System.Management.Automation.CallStackFrame</span></span>

<span data-ttu-id="1c173-129">**Get-PSCallStack** retourneert een-object dat de items in de aanroep stack vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="1c173-129">**Get-PSCallStack** returns an object that represents the items in the call stack.</span></span>

## <span data-ttu-id="1c173-130">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1c173-130">NOTES</span></span>

## <span data-ttu-id="1c173-131">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1c173-131">RELATED LINKS</span></span>

[<span data-ttu-id="1c173-132">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="1c173-132">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="1c173-133">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="1c173-133">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="1c173-134">Format-Table</span><span class="sxs-lookup"><span data-stu-id="1c173-134">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="1c173-135">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="1c173-135">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="1c173-136">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="1c173-136">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="1c173-137">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="1c173-137">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

