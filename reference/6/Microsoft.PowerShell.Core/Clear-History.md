---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-history?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-History
ms.openlocfilehash: 859738998de9d2a61a5fb7d9f39ff6ef8b74ad4d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250719"
---
# <span data-ttu-id="18f82-103">Clear-History</span><span class="sxs-lookup"><span data-stu-id="18f82-103">Clear-History</span></span>

## <span data-ttu-id="18f82-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="18f82-104">SYNOPSIS</span></span>
<span data-ttu-id="18f82-105">Hiermee verwijdert u vermeldingen uit de geschiedenis van de Power shell-sessie opdracht.</span><span class="sxs-lookup"><span data-stu-id="18f82-105">Deletes entries from the PowerShell session command history.</span></span>

## <span data-ttu-id="18f82-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="18f82-106">SYNTAX</span></span>

### <span data-ttu-id="18f82-107">IDParameter (standaard)</span><span class="sxs-lookup"><span data-stu-id="18f82-107">IDParameter (Default)</span></span>

```
Clear-History [[-Id] <int[]>] [[-Count] <int>] [-Newest] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="18f82-108">CommandLineParameter</span><span class="sxs-lookup"><span data-stu-id="18f82-108">CommandLineParameter</span></span>

```
Clear-History [[-Count] <int>] [-CommandLine <string[]>] [-Newest] [-WhatIf] [-Confirm]
[<CommonParameters>]
```

## <span data-ttu-id="18f82-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="18f82-109">DESCRIPTION</span></span>

<span data-ttu-id="18f82-110">`Clear-History` Hiermee verwijdert u de opdracht geschiedenis uit een Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="18f82-110">`Clear-History` deletes the command history from a PowerShell session.</span></span> <span data-ttu-id="18f82-111">Elke Power shell-sessie heeft een eigen opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="18f82-111">Each PowerShell session has its own command history.</span></span> <span data-ttu-id="18f82-112">Als u de opdracht geschiedenis wilt weer geven, gebruikt u de- `Get-History` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="18f82-112">To display the command history, use the `Get-History` cmdlet.</span></span>

<span data-ttu-id="18f82-113">`Clear-History`Verwijdert standaard de volledige opdracht geschiedenis uit een Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="18f82-113">By default, `Clear-History` deletes the entire command history from a PowerShell session.</span></span> <span data-ttu-id="18f82-114">U kunt para meters gebruiken `Clear-History` om geselecteerde opdrachten te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="18f82-114">You can use parameters with `Clear-History` to delete selected commands.</span></span>

<span data-ttu-id="18f82-115">`Clear-History` Hiermee wordt het `PSReadLine` opdracht geschiedenis bestand niet gewist.</span><span class="sxs-lookup"><span data-stu-id="18f82-115">`Clear-History` does not clear the `PSReadLine` command history file.</span></span> <span data-ttu-id="18f82-116">`PSReadLine`In de module wordt een geschiedenis bestand opgeslagen dat elke Power shell-opdracht uit elke Power shell-sessie bevat.</span><span class="sxs-lookup"><span data-stu-id="18f82-116">The `PSReadLine` module stores a history file that contains every PowerShell command from every PowerShell session.</span></span> <span data-ttu-id="18f82-117">Gebruik vanuit een Power shell-prompt de pijl omhoog en omlaag op het toetsen bord om door de opdracht geschiedenis te bladeren.</span><span class="sxs-lookup"><span data-stu-id="18f82-117">From a PowerShell prompt, use the up and down arrows on your keyboard to scroll through the command history.</span></span> <span data-ttu-id="18f82-118">Als u de `PSReadLine` configuratie voor de opdracht geschiedenis wilt weer geven, gebruikt u `Get-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="18f82-118">To display the `PSReadLine` configuration for command history, use `Get-PSReadLineOption`.</span></span>
<span data-ttu-id="18f82-119">`PSReadLine` geleverd met Power shell 5,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="18f82-119">`PSReadLine` shipped with PowerShell 5.0 and above.</span></span> <span data-ttu-id="18f82-120">Zie [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="18f82-120">For more information, see [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="18f82-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="18f82-121">EXAMPLES</span></span>

### <span data-ttu-id="18f82-122">Voor beeld 1: de opdracht geschiedenis uit een Power shell-sessie verwijderen</span><span class="sxs-lookup"><span data-stu-id="18f82-122">Example 1: Delete the command history from a PowerShell session</span></span>

<span data-ttu-id="18f82-123">Met deze opdracht worden alle opdrachten verwijderd uit de geschiedenis van een Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="18f82-123">This command deletes all of the commands from a PowerShell session's history.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location .\Test
   2 Update-Help
   3 Set-Location C:\Test\Logs
   4 Get-Location
```

```powershell
Clear-History
Get-History
```

```Output
  Id CommandLine
  -- -----------
   5 Clear-History
```

<span data-ttu-id="18f82-124">Met de `Get-History` cmdlet wordt de geschiedenis van de Power shell-sessie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="18f82-124">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="18f82-125">`Clear-History` Hiermee verwijdert u de volledige opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="18f82-125">`Clear-History` deletes the entire command history.</span></span> <span data-ttu-id="18f82-126">`Get-History` Hiermee wordt de bijgewerkte opdracht geschiedenis weer gegeven en wordt bevestigd dat de eerdere geschiedenis is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="18f82-126">`Get-History` displays the updated command history and confirms the prior history was deleted.</span></span>

### <span data-ttu-id="18f82-127">Voor beeld 2: de nieuwste opdrachten verwijderen</span><span class="sxs-lookup"><span data-stu-id="18f82-127">Example 2: Delete the newest commands</span></span>

<span data-ttu-id="18f82-128">Met deze opdracht worden de laatste en **laatste** para meters **uit de geschiedenis** van een Power shell-sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="18f82-128">This command uses the **Count** and **Newest** parameters to delete the newest commands from a PowerShell session's history.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Count 5 -Newest
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
  11 Clear-History -Count 5 -Newest
```

<span data-ttu-id="18f82-129">Met de `Get-History` cmdlet wordt de geschiedenis van de Power shell-sessie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="18f82-129">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="18f82-130">`Clear-History` wordt gebruikt voor het verwijderen van de opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="18f82-130">`Clear-History` is used to delete the command history.</span></span> <span data-ttu-id="18f82-131">De para meter **aantal** bepaalt het aantal opdrachten dat moet worden verwijderd, inclusief de opgegeven **id**. De **nieuwste** para meter geeft aan dat de nieuwste opdrachten uit de geschiedenis worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="18f82-131">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id**. The **Newest** parameter specifies that the newest commands are cleared from the history.</span></span> <span data-ttu-id="18f82-132">`Get-History`de bijgewerkte opdracht geschiedenis wordt weer gegeven en er wordt bevestigd dat de vijf nieuwste opdrachten zijn verwijderd, **id 6**  -  **id 10**.</span><span class="sxs-lookup"><span data-stu-id="18f82-132">`Get-History` displays the updated command history and confirms that the five newest commands were deleted, **Id 6** - **Id 10**.</span></span>

### <span data-ttu-id="18f82-133">Voor beeld 3: opdrachten verwijderen die aan bepaalde criteria voldoen</span><span class="sxs-lookup"><span data-stu-id="18f82-133">Example 3: Delete commands that match specific criteria</span></span>

<span data-ttu-id="18f82-134">Met deze opdracht worden opdrachten verwijderd die overeenkomen met specifieke criteria die zijn gedefinieerd door de para meter **commandline** .</span><span class="sxs-lookup"><span data-stu-id="18f82-134">This command deletes commands that match specific criteria defined by the **CommandLine** parameter.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
```

```powershell
Clear-History -CommandLine *Help*, *Syntax
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   4 Get-Command Clear-History -ShowCommandInfo
   8 Clear-History -CommandLine *Help*, *Syntax
```

<span data-ttu-id="18f82-135">Met de `Get-History` cmdlet wordt de geschiedenis van de Power shell-sessie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="18f82-135">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="18f82-136">`Clear-History` Hiermee verwijdert u de opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="18f82-136">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="18f82-137">De para meter **commandline** bevat opdrachten die **Help** of end met **syntaxis** bevatten.</span><span class="sxs-lookup"><span data-stu-id="18f82-137">The **CommandLine** parameter specifies commands that contain **Help** or end with **Syntax**.</span></span> <span data-ttu-id="18f82-138">`Get-History` de bijgewerkte opdracht geschiedenis wordt weer gegeven en er wordt bevestigd dat de opdrachten **id 3** , **id 5** , **id 6** en **id 7** zijn verwijderd.</span><span class="sxs-lookup"><span data-stu-id="18f82-138">`Get-History` displays the updated command history and confirms that commands **Id 3** , **Id 5** , **Id 6** , and **Id 7** were deleted.</span></span>

### <span data-ttu-id="18f82-139">Voor beeld 4: opdrachten op id-nummer verwijderen</span><span class="sxs-lookup"><span data-stu-id="18f82-139">Example 4: Delete commands by Id number</span></span>

<span data-ttu-id="18f82-140">Met deze opdracht worden specifieke geschiedenis items verwijderd met behulp van de **id**. Als u meerdere opdrachten wilt verwijderen, dient u een door komma's gescheiden lijst met **id-** nummers in te dienen.</span><span class="sxs-lookup"><span data-stu-id="18f82-140">This command deletes specific history items using the **Id**. To delete multiple commands, submit a comma-separated list of **Id** numbers.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   3 Get-Help Get-Alias
   4 Get-Command Clear-History
   5 Get-Command Clear-History -Syntax
   6 Get-Command Clear-History -ShowCommandInfo
```

```powershell
Clear-History -Id 3, 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   4 Get-Command Clear-History
   6 Get-Command Clear-History -ShowCommandInfo
   7 Get-History
   8 Clear-History -Id 3, 5
```

<span data-ttu-id="18f82-141">Met de `Get-History` cmdlet wordt de geschiedenis van de Power shell-sessie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="18f82-141">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="18f82-142">`Clear-History` Hiermee verwijdert u de opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="18f82-142">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="18f82-143">De **id-** para meter geeft aan welke opdrachten moeten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="18f82-143">The **Id** parameter specifies which commands to delete.</span></span> <span data-ttu-id="18f82-144">`Get-History` Hiermee wordt de bijgewerkte opdracht geschiedenis weer gegeven en wordt bevestigd dat **id 3** en **id 5** zijn verwijderd.</span><span class="sxs-lookup"><span data-stu-id="18f82-144">`Get-History` displays the updated command history and confirms that **Id 3** and **Id 5** were deleted.</span></span>

### <span data-ttu-id="18f82-145">Voor beeld 5: opdrachten op id-nummer en aantal verwijderen</span><span class="sxs-lookup"><span data-stu-id="18f82-145">Example 5: Delete commands by Id number and count</span></span>

<span data-ttu-id="18f82-146">Met deze opdracht worden de para meters **id** en **aantal** gebruikt voor het verwijderen van de opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="18f82-146">This command uses the **Id** and **Count** parameters to delete command history.</span></span> <span data-ttu-id="18f82-147">Opdrachten worden verwijderd uit de opgegeven **id** in omgekeerde volg orde, van nieuw naar oud.</span><span class="sxs-lookup"><span data-stu-id="18f82-147">Commands are deleted from the specified **Id** in reverse order, newest to oldest.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Id 7 -Count 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
  11 Clear-History -Id 7 -Count 5
```

<span data-ttu-id="18f82-148">Met de `Get-History` cmdlet wordt de geschiedenis van de Power shell-sessie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="18f82-148">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="18f82-149">`Clear-History` Hiermee verwijdert u de opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="18f82-149">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="18f82-150">De **id-** para meter geeft aan dat begint met **id 7**.</span><span class="sxs-lookup"><span data-stu-id="18f82-150">The **Id** parameter specifies to begin with **Id 7**.</span></span> <span data-ttu-id="18f82-151">De para meter **aantal** geeft aan dat vijf opdrachten moeten worden verwijderd, inclusief de opgegeven **id**. `Get-History`Hiermee wordt de bijgewerkte opdracht geschiedenis weer gegeven en wordt bevestigd dat er vijf opdrachten zijn verwijderd, **id 3**  -  **-id 7**.</span><span class="sxs-lookup"><span data-stu-id="18f82-151">The **Count** parameter specifies to delete five commands, inclusive of the specified **Id**. `Get-History` displays the updated command history and confirms that five commands were deleted, **Id 3** - **Id 7**.</span></span>

## <span data-ttu-id="18f82-152">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="18f82-152">PARAMETERS</span></span>

### <span data-ttu-id="18f82-153">-CommandLine</span><span class="sxs-lookup"><span data-stu-id="18f82-153">-CommandLine</span></span>

<span data-ttu-id="18f82-154">Hiermee verwijdert u de opdracht geschiedenis uit een Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="18f82-154">Deletes command history from a PowerShell session.</span></span> <span data-ttu-id="18f82-155">De teken reeks moet exact overeenkomen of joker tekens gebruiken om opdrachten in de Power shell-sessie geschiedenis weer gegeven door te vergelijken `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="18f82-155">The string must be an exact match or use wildcards to match commands in the PowerShell session history displayed by `Get-History`.</span></span> <span data-ttu-id="18f82-156">Als u meer dan één teken reeks opgeeft, `Clear-History` worden opdrachten verwijderd die overeenkomen met een van de teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="18f82-156">If you enter more than one string, `Clear-History` deletes commands that match any of the strings.</span></span> <span data-ttu-id="18f82-157">De para meter **commandline** kan worden gebruikt met **Count**.</span><span class="sxs-lookup"><span data-stu-id="18f82-157">The **CommandLine** parameter can be used with **Count**.</span></span>

<span data-ttu-id="18f82-158">Gebruik voor teken reeksen met een spatie enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="18f82-158">For strings with a space, use single quotations.</span></span> <span data-ttu-id="18f82-159">Zie [about_Quoting_Rules](About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="18f82-159">For more information, see [about_Quoting_Rules](About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandLineParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="18f82-160">-Aantal</span><span class="sxs-lookup"><span data-stu-id="18f82-160">-Count</span></span>

<span data-ttu-id="18f82-161">Hiermee geeft u het aantal geschiedenis vermeldingen op dat wordt `Clear-History` verwijderd.</span><span class="sxs-lookup"><span data-stu-id="18f82-161">Specifies the number of history entries that `Clear-History` deletes.</span></span> <span data-ttu-id="18f82-162">Opdrachten worden in volg orde verwijderd, te beginnen met de oudste vermelding in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="18f82-162">Commands are deleted in order, beginning with the oldest entry in the history.</span></span>

<span data-ttu-id="18f82-163">De para meters **Count** en **id** kunnen samen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="18f82-163">The **Count** and **Id** parameters can be used together.</span></span> <span data-ttu-id="18f82-164">De para meter **aantal** bepaalt het aantal opdrachten dat moet worden verwijderd, inclusief de opgegeven **id**. Vanaf de opgegeven **id** worden opdrachten in omgekeerde sequentiële volg orde verwijderd.</span><span class="sxs-lookup"><span data-stu-id="18f82-164">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id**. Beginning at the specified **Id** , commands are deleted in reverse sequential order.</span></span> <span data-ttu-id="18f82-165">Als de **id** bijvoorbeeld 30 is en de **telling** 10, `Clear-History` worden de items 21 tot en met 30 verwijderd.</span><span class="sxs-lookup"><span data-stu-id="18f82-165">For example, if the **Id** is 30 and the **Count** is 10, `Clear-History` deletes items 21 through 30.</span></span>

<span data-ttu-id="18f82-166">De para meters **Count** en **commandline** kunnen samen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="18f82-166">The **Count** and **CommandLine** parameters can be used together.</span></span> <span data-ttu-id="18f82-167">**Count** Hiermee geeft u het aantal opdrachten dat moet worden verwijderd dat overeenkomt met de waarde van de **commandline** -para meter.</span><span class="sxs-lookup"><span data-stu-id="18f82-167">**Count** specifies the number of commands to delete that match **CommandLine** parameter value.</span></span> <span data-ttu-id="18f82-168">De opdrachten worden in sequentiële volg orde verwijderd.</span><span class="sxs-lookup"><span data-stu-id="18f82-168">The commands are deleted in sequential order.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="18f82-169">-Id</span><span class="sxs-lookup"><span data-stu-id="18f82-169">-Id</span></span>

<span data-ttu-id="18f82-170">Hiermee geeft u de opdracht geschiedenis **-id** die wordt `Clear-History` verwijderd.</span><span class="sxs-lookup"><span data-stu-id="18f82-170">Specifies the command history **Id** that `Clear-History` deletes.</span></span> <span data-ttu-id="18f82-171">Als u **id-** nummers wilt weer geven, gebruikt u de `Get-History` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="18f82-171">To display **Id** numbers, use the `Get-History` cmdlet.</span></span> <span data-ttu-id="18f82-172">De **id-** nummers zijn opeenvolgend en opdrachten blijven hun **id-** nummer in een Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="18f82-172">The **Id** numbers are sequential and commands keep their **Id** number throughout a PowerShell session.</span></span> <span data-ttu-id="18f82-173">De **id-** para meter kan worden gebruikt met **aantal** en **Nieuw**.</span><span class="sxs-lookup"><span data-stu-id="18f82-173">The **Id** parameter can be used with **Count** and **Newest**.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IDParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="18f82-174">-Nieuwste</span><span class="sxs-lookup"><span data-stu-id="18f82-174">-Newest</span></span>

<span data-ttu-id="18f82-175">Wanneer de **nieuwste** para meter wordt gebruikt, `Clear-History` worden de meest recente vermeldingen in de geschiedenis verwijderd.</span><span class="sxs-lookup"><span data-stu-id="18f82-175">When the **Newest** parameter is used, `Clear-History` deletes the newest entries in the history.</span></span> <span data-ttu-id="18f82-176">Standaard `Clear-History` verwijdert de oudste vermeldingen in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="18f82-176">By default, `Clear-History` deletes the oldest entries in the history.</span></span>

<span data-ttu-id="18f82-177">De **nieuwste** para meter kan worden gebruikt met **id** en **aantal**.</span><span class="sxs-lookup"><span data-stu-id="18f82-177">The **Newest** parameter can be used with **Id** and **Count**.</span></span> <span data-ttu-id="18f82-178">De para meter **aantal** bepaalt het aantal opdrachten dat moet worden verwijderd, inclusief de opgegeven **id**. Vanaf de opgegeven **id** worden opdrachten in sequentiële volg orde verwijderd.</span><span class="sxs-lookup"><span data-stu-id="18f82-178">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id**. Beginning at the specified **Id** , commands are deleted in sequential order.</span></span> <span data-ttu-id="18f82-179">Als de **id** bijvoorbeeld 30 is en de **telling** 10, verwijdert u de `Clear-History` items 30 tot en met 39.</span><span class="sxs-lookup"><span data-stu-id="18f82-179">For example, if the **Id** is 30 and the **Count** is 10, `Clear-History` deletes items 30 through 39.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="18f82-180">-Confirm</span><span class="sxs-lookup"><span data-stu-id="18f82-180">-Confirm</span></span>

<span data-ttu-id="18f82-181">Vraagt u om bevestiging voordat de cmdlet wordt uitgevoerd `Clear-History` .</span><span class="sxs-lookup"><span data-stu-id="18f82-181">Prompts you for confirmation before running the `Clear-History` cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="18f82-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="18f82-182">-WhatIf</span></span>

<span data-ttu-id="18f82-183">Laat zien wat er zou gebeuren als de `Clear-History` cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="18f82-183">Shows what would happen if the `Clear-History` cmdlet runs.</span></span> <span data-ttu-id="18f82-184">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="18f82-184">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="18f82-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="18f82-185">CommonParameters</span></span>

<span data-ttu-id="18f82-186">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="18f82-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="18f82-187">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="18f82-187">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="18f82-188">INVOER</span><span class="sxs-lookup"><span data-stu-id="18f82-188">INPUTS</span></span>

### <span data-ttu-id="18f82-189">Geen</span><span class="sxs-lookup"><span data-stu-id="18f82-189">None</span></span>

<span data-ttu-id="18f82-190">U kunt geen objecten pipeen naar `Clear-History` .</span><span class="sxs-lookup"><span data-stu-id="18f82-190">You cannot pipe objects to `Clear-History`.</span></span>

## <span data-ttu-id="18f82-191">UITVOER</span><span class="sxs-lookup"><span data-stu-id="18f82-191">OUTPUTS</span></span>

### <span data-ttu-id="18f82-192">Geen</span><span class="sxs-lookup"><span data-stu-id="18f82-192">None</span></span>

<span data-ttu-id="18f82-193">`Clear-History` Er wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="18f82-193">`Clear-History` does not generate any output.</span></span>

## <span data-ttu-id="18f82-194">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="18f82-194">NOTES</span></span>

<span data-ttu-id="18f82-195">De Power shell-sessie geschiedenis is een lijst met opdrachten die tijdens een Power shell-sessie zijn ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="18f82-195">The PowerShell session history is a list of the commands entered during a PowerShell session.</span></span> <span data-ttu-id="18f82-196">U kunt de geschiedenis bekijken, opdrachten toevoegen en verwijderen en opdrachten uit de geschiedenis uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="18f82-196">You can view the history, add and delete commands, and run commands from the history.</span></span> <span data-ttu-id="18f82-197">Zie [about_History](About/about_History.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="18f82-197">For more information, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="18f82-198">De sessie geschiedenis wordt afzonderlijk beheerd vanaf de geschiedenis die wordt onderhouden door de **PSReadLine** -module.</span><span class="sxs-lookup"><span data-stu-id="18f82-198">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="18f82-199">Beide geschiedenissen zijn beschikbaar in sessies waarin **PSReadLine** wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="18f82-199">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="18f82-200">Deze cmdlet werkt alleen met de sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="18f82-200">This cmdlet only works with the session history.</span></span> <span data-ttu-id="18f82-201">Zie [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="18f82-201">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="18f82-202">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="18f82-202">RELATED LINKS</span></span>

[<span data-ttu-id="18f82-203">about_History</span><span class="sxs-lookup"><span data-stu-id="18f82-203">about_History</span></span>](About/about_History.md)

[<span data-ttu-id="18f82-204">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="18f82-204">about_PSReadLine</span></span>](../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="18f82-205">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="18f82-205">about_Quoting_Rules</span></span>](About/about_Quoting_Rules.md)

[<span data-ttu-id="18f82-206">Toevoegen-geschiedenis</span><span class="sxs-lookup"><span data-stu-id="18f82-206">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="18f82-207">Get-geschiedenis</span><span class="sxs-lookup"><span data-stu-id="18f82-207">Get-History</span></span>](Get-History.md)

[<span data-ttu-id="18f82-208">Invoke-geschiedenis</span><span class="sxs-lookup"><span data-stu-id="18f82-208">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="18f82-209">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="18f82-209">Get-PSReadLineOption</span></span>](/powershell/module/psreadline/get-psreadlineoption)

[<span data-ttu-id="18f82-210">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="18f82-210">Set-PSReadLineOption</span></span>](/powershell/module/psreadline/set-psreadlineoption)
