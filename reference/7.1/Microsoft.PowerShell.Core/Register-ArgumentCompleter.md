---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-argumentcompleter?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ArgumentCompleter
ms.openlocfilehash: 6ada7bd821632054649c3ccf377fea844d2ae0c8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251193"
---
# <span data-ttu-id="2514b-103">Register-ArgumentCompleter</span><span class="sxs-lookup"><span data-stu-id="2514b-103">Register-ArgumentCompleter</span></span>

## <span data-ttu-id="2514b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2514b-104">SYNOPSIS</span></span>

<span data-ttu-id="2514b-105">Hiermee registreert u een volledig aangepaste argument.</span><span class="sxs-lookup"><span data-stu-id="2514b-105">Registers a custom argument completer.</span></span>

## <span data-ttu-id="2514b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2514b-106">SYNTAX</span></span>

### <span data-ttu-id="2514b-107">Systeem eigenset</span><span class="sxs-lookup"><span data-stu-id="2514b-107">NativeSet</span></span>

```
Register-ArgumentCompleter -CommandName <String[]> -ScriptBlock <ScriptBlock> [-Native]
 [<CommonParameters>]
```

### <span data-ttu-id="2514b-108">Power shell-set</span><span class="sxs-lookup"><span data-stu-id="2514b-108">PowerShellSet</span></span>

```
Register-ArgumentCompleter [-CommandName <String[]>] -ParameterName <String>
 -ScriptBlock <ScriptBlock> [<CommonParameters>]
```

## <span data-ttu-id="2514b-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2514b-109">DESCRIPTION</span></span>

<span data-ttu-id="2514b-110">De `Register-ArgumentCompleter` cmdlet registreert een volledig aangepaste argument.</span><span class="sxs-lookup"><span data-stu-id="2514b-110">The `Register-ArgumentCompleter` cmdlet registers a custom argument completer.</span></span> <span data-ttu-id="2514b-111">Met de functie voor het argument voltooid kunt u tijdens runtime dynamische tabblad voltooiing opgeven voor elke opdracht die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="2514b-111">An argument completer allows you to provide dynamic tab completion, at run time for any command that you specify.</span></span>

## <span data-ttu-id="2514b-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2514b-112">EXAMPLES</span></span>

### <span data-ttu-id="2514b-113">Voor beeld 1: een volledig aangepaste argument registreren</span><span class="sxs-lookup"><span data-stu-id="2514b-113">Example 1: Register a custom argument completer</span></span>

<span data-ttu-id="2514b-114">In het volgende voor beeld wordt een argument voltooid geregistreerd voor de para meter **id** van de `Set-TimeZone` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2514b-114">The following example registers an argument completer for the **Id** parameter of the `Set-TimeZone` cmdlet.</span></span>

```powershell
$scriptBlock = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)

    (Get-TimeZone -ListAvailable).Id | Where-Object {
        $_ -like "$wordToComplete*"
    } | ForEach-Object {
          "'$_'"
    }
}
Register-ArgumentCompleter -CommandName Set-TimeZone -ParameterName Id -ScriptBlock $scriptBlock
```

<span data-ttu-id="2514b-115">Met de eerste opdracht maakt u een script blok waarbij de vereiste para meters worden gebruikt die worden door gegeven wanneer de gebruiker op het <kbd>tabblad</kbd>klikt. Zie de beschrijving van de para meter **script Block** voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2514b-115">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="2514b-116">Binnen het script blok worden de beschik bare waarden voor **id** opgehaald met behulp van de `Get-TimeZone` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2514b-116">Within the script block, the available values for **Id** are retrieved using the `Get-TimeZone` cmdlet.</span></span> <span data-ttu-id="2514b-117">De eigenschap **id** voor elke tijd zone wordt door gegeven aan de `Where-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2514b-117">The **Id** property for each Time Zone is piped to the `Where-Object` cmdlet.</span></span> <span data-ttu-id="2514b-118">De `Where-Object` cmdlet filtert alle id's die niet beginnen met de waarde die is opgegeven door `$wordToComplete` , die de tekst bevat die de gebruiker heeft getypt voordat ze op <kbd>Tab</kbd>werden gedrukt. De gefilterde id's worden door gegeven aan de `For-EachObject` cmdlet die elke waarde in de aanhalings tekens omsluit, wanneer de waarde spaties bevat.</span><span class="sxs-lookup"><span data-stu-id="2514b-118">The `Where-Object` cmdlet filters out any ids that do not start with the value provided by `$wordToComplete`, which represents the text the user typed before they pressed <kbd>Tab</kbd>. The filtered ids are piped to the `For-EachObject` cmdlet which encloses each value in quotes, should the value contain spaces.</span></span>

<span data-ttu-id="2514b-119">Met de tweede opdracht wordt het argument completer geregistreerd door de script Block, de **para meter** **-id** en de **opdracht** naam door te geven `Set-TimeZone` .</span><span class="sxs-lookup"><span data-stu-id="2514b-119">The second command registers the argument completer by passing the scriptblock, the **ParameterName** **Id** and the **CommandName** `Set-TimeZone`.</span></span>

### <span data-ttu-id="2514b-120">Voor beeld 2: Details toevoegen aan de waarden voor het volt ooien van het tabblad</span><span class="sxs-lookup"><span data-stu-id="2514b-120">Example 2: Add details to your tab completion values</span></span>

<span data-ttu-id="2514b-121">In het volgende voor beeld wordt het volt ooien van het tabblad voor de para meter **name** van de cmdlet overschreven `Stop-Service` en worden alleen actieve services geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2514b-121">The following example overwrites tab completion for the **Name** parameter of the `Stop-Service` cmdlet and only returns running services.</span></span>

```powershell
$s = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)
    $services = Get-Service | Where-Object {$_.Status -eq "Running" -and $_.Name -like "$wordToComplete*"}
    $services | ForEach-Object {
        New-Object -Type System.Management.Automation.CompletionResult -ArgumentList $_.Name,
            $_.Name,
            "ParameterValue",
            $_.Name
    }
}
Register-ArgumentCompleter -CommandName Stop-Service -ParameterName Name -ScriptBlock $s
```

<span data-ttu-id="2514b-122">Met de eerste opdracht maakt u een script blok waarbij de vereiste para meters worden gebruikt die worden door gegeven wanneer de gebruiker op het <kbd>tabblad</kbd>klikt. Zie de beschrijving van de para meter **script Block** voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2514b-122">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="2514b-123">In het-script blok haalt de eerste opdracht alle actieve services op met de `Where-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2514b-123">Within the script block, the first command retrieves all running services using the `Where-Object` cmdlet.</span></span> <span data-ttu-id="2514b-124">De services worden door gegeven aan de `ForEach-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2514b-124">The services are piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="2514b-125">`ForEach-Object`Met de cmdlet wordt een nieuw [System. Management. Automation. CompletionResult](/dotnet/api/system.management.automation.completionresult) -object gemaakt en gevuld met de naam van de huidige service (vertegenwoordigd door de pijplijn variabele `$_.Name` ).</span><span class="sxs-lookup"><span data-stu-id="2514b-125">The `ForEach-Object` cmdlet creates a new [System.Management.Automation.CompletionResult](/dotnet/api/system.management.automation.completionresult) object and populates it with the name of the current service (represented by the pipeline variable `$_.Name`).</span></span>

<span data-ttu-id="2514b-126">Met het **CompletionResult** -object kunt u aanvullende Details voor elke geretourneerde waarde opgeven:</span><span class="sxs-lookup"><span data-stu-id="2514b-126">The **CompletionResult** object allows you to provide additional details to each returned value:</span></span>

- <span data-ttu-id="2514b-127">**completionText** (teken reeks): de tekst die moet worden gebruikt als resultaat van automatisch volt ooien.</span><span class="sxs-lookup"><span data-stu-id="2514b-127">**completionText** (String) - The text to be used as the auto completion result.</span></span> <span data-ttu-id="2514b-128">Dit is de waarde die wordt verzonden naar de opdracht.</span><span class="sxs-lookup"><span data-stu-id="2514b-128">This is the value sent to the command.</span></span>
- <span data-ttu-id="2514b-129">**listItemText** (teken reeks): de tekst die moet worden weer gegeven in een lijst, bijvoorbeeld wanneer de gebruiker op de <kbd>CTRL</kbd>- + <kbd>spatie</kbd>klikt.</span><span class="sxs-lookup"><span data-stu-id="2514b-129">**listItemText** (String) - The text to be displayed in a list, such as when the user presses <kbd>Ctrl</kbd>+<kbd>Space</kbd>.</span></span> <span data-ttu-id="2514b-130">Dit wordt alleen gebruikt voor weer gave en wordt niet door gegeven aan de opdracht wanneer deze is geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="2514b-130">This is used for display only and is not passed to the command when selected.</span></span>
- <span data-ttu-id="2514b-131">**resultType** ( [CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)): het type voltooiings resultaat.</span><span class="sxs-lookup"><span data-stu-id="2514b-131">**resultType** ([CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)) - The type of completion result.</span></span>
- <span data-ttu-id="2514b-132">**knop info** (teken reeks): de tekst voor de knop info met details die moeten worden weer gegeven over het object.</span><span class="sxs-lookup"><span data-stu-id="2514b-132">**toolTip** (String) - The text for the tooltip with details to be displayed about the object.</span></span>
  <span data-ttu-id="2514b-133">Dit is zichtbaar wanneer de gebruiker een item selecteert nadat u op <kbd>CTRL</kbd>-spatie hebt gedrukt + <kbd>Space</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2514b-133">This is visible when the user selects an item after pressing <kbd>Ctrl</kbd>+<kbd>Space</kbd>.</span></span>

<span data-ttu-id="2514b-134">Met de laatste opdracht wordt gedemonstreerd dat gestopte services nog steeds hand matig kunnen worden door gegeven aan de `Stop-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2514b-134">The last command demonstrates that stopped services can still be passed in manually to the `Stop-Service` cmdlet.</span></span> <span data-ttu-id="2514b-135">Het vullen van het tabblad is alleen van invloed op het onderhouds aspect.</span><span class="sxs-lookup"><span data-stu-id="2514b-135">The tab completion is the only aspect affected.</span></span>

### <span data-ttu-id="2514b-136">Voor beeld 3: een aangepaste systeem eigen argument voor de volledige functie registreren</span><span class="sxs-lookup"><span data-stu-id="2514b-136">Example 3: Register a custom Native argument completer</span></span>

<span data-ttu-id="2514b-137">U kunt de **systeem eigen** para meter gebruiken om het volt ooien van een opdracht in te stellen.</span><span class="sxs-lookup"><span data-stu-id="2514b-137">You can use the **Native** parameter to provide tab-completion for a native command.</span></span> <span data-ttu-id="2514b-138">In het volgende voor beeld wordt het volt ooien van het tabblad voor de `dotnet` opdracht regel interface (CLI) toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="2514b-138">The following example adds tab-completion for the `dotnet` Command Line Interface (CLI).</span></span>

> [!NOTE]
> <span data-ttu-id="2514b-139">De `dotnet complete` opdracht is alleen beschikbaar in versie 2,0 en hoger van de DotNet-cli.</span><span class="sxs-lookup"><span data-stu-id="2514b-139">The `dotnet complete` command is only available in version 2.0 and greater of the dotnet cli.</span></span>

```powershell
$scriptblock = {
    param($wordToComplete, $commandAst, $cursorPosition)
        dotnet complete --position $cursorPosition $commandAst.ToString() | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
        }
}
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock $scriptblock
```

<span data-ttu-id="2514b-140">Met de eerste opdracht maakt u een script blok waarbij de vereiste para meters worden gebruikt die worden door gegeven wanneer de gebruiker op het <kbd>tabblad</kbd>klikt. Zie de beschrijving van de para meter **script Block** voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2514b-140">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="2514b-141">In het-script blok `dotnet complete` wordt de opdracht gebruikt om het volt ooien van het tabblad uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="2514b-141">Within the script block, the `dotnet complete` command is used to perform the tab completion.</span></span>
<span data-ttu-id="2514b-142">De resultaten worden door gegeven aan de `ForEach-Object` cmdlet die gebruikmaakt van de **nieuwe** statische methode van de klasse [System. Management. Automation. CompletionResult](/dotnet/api/system.management.automation.completionresult) om voor elke waarde een nieuw **CompletionResult** -object te maken.</span><span class="sxs-lookup"><span data-stu-id="2514b-142">The results are piped to the `ForEach-Object` cmdlet which use the **new** static method of the [System.Management.Automation.CompletionResult](/dotnet/api/system.management.automation.completionresult) class to create a new **CompletionResult** object for each value.</span></span>

## <span data-ttu-id="2514b-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2514b-143">PARAMETERS</span></span>

### <span data-ttu-id="2514b-144">-Opdrachtnaam</span><span class="sxs-lookup"><span data-stu-id="2514b-144">-CommandName</span></span>

<span data-ttu-id="2514b-145">Hiermee geeft u de naam van de opdrachten als een matrix.</span><span class="sxs-lookup"><span data-stu-id="2514b-145">Specifies the name of the commands as an array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NativeSet, PowerShellSet
Aliases:

Required: True (NativeSet), False (PowerShellSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2514b-146">-Systeem eigen</span><span class="sxs-lookup"><span data-stu-id="2514b-146">-Native</span></span>

<span data-ttu-id="2514b-147">Geeft aan dat het argument volledig is voor een systeem eigen opdracht waarbij Power shell geen parameter namen kan volt ooien.</span><span class="sxs-lookup"><span data-stu-id="2514b-147">Indicates that the argument completer is for a native command where PowerShell cannot complete parameter names.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NativeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2514b-148">-Para meternaam</span><span class="sxs-lookup"><span data-stu-id="2514b-148">-ParameterName</span></span>

<span data-ttu-id="2514b-149">Hiermee geeft u de naam van de para meter op waarvan het argument wordt voltooid.</span><span class="sxs-lookup"><span data-stu-id="2514b-149">Specifies the name of the parameter whose argument is being completed.</span></span> <span data-ttu-id="2514b-150">De opgegeven parameter naam kan geen opsommings waarde zijn, zoals de para meter **ForegroundColor** van de `Write-Host` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2514b-150">The parameter name specified cannot be an enumerated value, such as the **ForegroundColor** parameter of the `Write-Host` cmdlet.</span></span>

<span data-ttu-id="2514b-151">Zie [about_Enum](./About/about_Enum.md)voor meer informatie over enums.</span><span class="sxs-lookup"><span data-stu-id="2514b-151">For more information on enums, see [about_Enum](./About/about_Enum.md).</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2514b-152">-Script Block</span><span class="sxs-lookup"><span data-stu-id="2514b-152">-ScriptBlock</span></span>

<span data-ttu-id="2514b-153">Hiermee geeft u de opdrachten op die moeten worden uitgevoerd om de tabblad voltooiing uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="2514b-153">Specifies the commands to run to perform tab completion.</span></span> <span data-ttu-id="2514b-154">Het script blok dat u opgeeft, moet de waarden retour neren die de invoer hebben voltooid.</span><span class="sxs-lookup"><span data-stu-id="2514b-154">The script block you provide should return the values that complete the input.</span></span> <span data-ttu-id="2514b-155">Het script blok moet de waarden van de pijp lijn ( `ForEach-Object` , `Where-Object` enzovoort) of een andere geschikte methode ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="2514b-155">The script block must unroll the values using the pipeline (`ForEach-Object`, `Where-Object`, etc.), or another suitable method.</span></span> <span data-ttu-id="2514b-156">Als u een matrix met waarden retourneert, wordt de gehele matrix als **één** waarde voor het volt ooien van een tab behandeld.</span><span class="sxs-lookup"><span data-stu-id="2514b-156">Returning an array of values causes PowerShell to treat the entire array as **one** tab completion value.</span></span>

<span data-ttu-id="2514b-157">Het script blok moet de volgende para meters accepteren in de opgegeven volg orde.</span><span class="sxs-lookup"><span data-stu-id="2514b-157">The script block must accept the following parameters in the order specified below.</span></span> <span data-ttu-id="2514b-158">De namen van de para meters zijn niet belang rijk omdat Power shell in de waarden van de positie wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="2514b-158">The names of the parameters aren't important because PowerShell passes in the values by position.</span></span>

- <span data-ttu-id="2514b-159">`$commandName` (Positie 0): deze para meter is ingesteld op de naam van de opdracht waarvoor het script blok het volt ooien van het tabblad oplevert.</span><span class="sxs-lookup"><span data-stu-id="2514b-159">`$commandName` (Position 0) - This parameter is set to the name of the command for which the script block is providing tab completion.</span></span>
- <span data-ttu-id="2514b-160">`$parameterName` (Positie 1)-deze para meter wordt ingesteld op de para meter waarvan de waarde het volt ooien van het tabblad vereist.</span><span class="sxs-lookup"><span data-stu-id="2514b-160">`$parameterName` (Position 1) - This parameter is set to the parameter whose value requires tab completion.</span></span>
- <span data-ttu-id="2514b-161">`$wordToComplete` (Positie 2): deze para meter is ingesteld op waarde die de gebruiker heeft opgegeven voordat deze <kbd>Tab</kbd>werd ingedrukt. Het script blok moet deze waarde gebruiken om de waarden voor het volt ooien van tabs te bepalen.</span><span class="sxs-lookup"><span data-stu-id="2514b-161">`$wordToComplete` (Position 2) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="2514b-162">`$commandAst` (Positie 3): deze para meter is ingesteld op de abstracte syntaxis structuur (AST) voor de huidige invoer regel.</span><span class="sxs-lookup"><span data-stu-id="2514b-162">`$commandAst` (Position 3) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="2514b-163">Zie [AST class](/dotnet/api/system.management.automation.language.ast)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2514b-163">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="2514b-164">`$fakeBoundParameters` (Positie 4): deze para meter is ingesteld op een hashtabel die de `$PSBoundParameters` voor de cmdlet bevat, voordat het <kbd>tabblad</kbd>van de gebruiker wordt ingedrukt. Zie [about_Automatic_Variables](./About/about_Automatic_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2514b-164">`$fakeBoundParameters` (Position 4) - This parameter is set to a hashtable containing the `$PSBoundParameters` for the cmdlet, before the user pressed <kbd>Tab</kbd>. For more information, see [about_Automatic_Variables](./About/about_Automatic_Variables.md).</span></span>

<span data-ttu-id="2514b-165">Wanneer u de **systeem eigen** para meter opgeeft, moet het script blok de volgende para meters in de opgegeven volg orde hebben.</span><span class="sxs-lookup"><span data-stu-id="2514b-165">When you specify the **Native** parameter, the script block must take the following parameters in the specified order.</span></span> <span data-ttu-id="2514b-166">De namen van de para meters zijn niet belang rijk omdat Power shell in de waarden van de positie wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="2514b-166">The names of the parameters aren't important because PowerShell passes in the values by position.</span></span>

- <span data-ttu-id="2514b-167">`$wordToComplete` (Positie 0): deze para meter is ingesteld op waarde die de gebruiker heeft opgegeven voordat deze <kbd>Tab</kbd>werd ingedrukt. Het script blok moet deze waarde gebruiken om de waarden voor het volt ooien van tabs te bepalen.</span><span class="sxs-lookup"><span data-stu-id="2514b-167">`$wordToComplete` (Position 0) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="2514b-168">`$commandAst` (Positie 1): deze para meter is ingesteld op de abstracte syntaxis structuur (AST) voor de huidige invoer regel.</span><span class="sxs-lookup"><span data-stu-id="2514b-168">`$commandAst` (Position 1) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="2514b-169">Zie [AST class](/dotnet/api/system.management.automation.language.ast)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2514b-169">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="2514b-170">`$cursorPosition` (Positie 2): deze para meter wordt ingesteld op de positie van de cursor wanneer het <kbd>tabblad</kbd>van de gebruiker wordt ingedrukt.</span><span class="sxs-lookup"><span data-stu-id="2514b-170">`$cursorPosition` (Position 2) - This parameter is set to the position of the cursor when the user pressed <kbd>Tab</kbd>.</span></span>

<span data-ttu-id="2514b-171">U kunt ook een **ArgumentCompleter** als parameter kenmerk opgeven.</span><span class="sxs-lookup"><span data-stu-id="2514b-171">You can also provide an **ArgumentCompleter** as a parameter attribute.</span></span> <span data-ttu-id="2514b-172">Zie [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2514b-172">For more information, see [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2514b-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2514b-173">CommonParameters</span></span>

<span data-ttu-id="2514b-174">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2514b-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2514b-175">Zie [about_CommonParameters](./About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2514b-175">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="2514b-176">INVOER</span><span class="sxs-lookup"><span data-stu-id="2514b-176">INPUTS</span></span>

### <span data-ttu-id="2514b-177">Geen</span><span class="sxs-lookup"><span data-stu-id="2514b-177">None</span></span>

<span data-ttu-id="2514b-178">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="2514b-178">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="2514b-179">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2514b-179">OUTPUTS</span></span>

### <span data-ttu-id="2514b-180">Geen</span><span class="sxs-lookup"><span data-stu-id="2514b-180">None</span></span>

<span data-ttu-id="2514b-181">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2514b-181">This cmdlet returns no output.</span></span>

## <span data-ttu-id="2514b-182">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2514b-182">NOTES</span></span>

## <span data-ttu-id="2514b-183">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2514b-183">RELATED LINKS</span></span>

