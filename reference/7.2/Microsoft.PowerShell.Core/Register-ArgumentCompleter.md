---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-argumentcompleter?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ArgumentCompleter
ms.openlocfilehash: 6044b27c0d339d62bd6e75fd2fee27eb65a89b79
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705893"
---
# <span data-ttu-id="9cf26-102">Register-ArgumentCompleter</span><span class="sxs-lookup"><span data-stu-id="9cf26-102">Register-ArgumentCompleter</span></span>

## <span data-ttu-id="9cf26-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9cf26-103">SYNOPSIS</span></span>

<span data-ttu-id="9cf26-104">Hiermee registreert u een volledig aangepaste argument.</span><span class="sxs-lookup"><span data-stu-id="9cf26-104">Registers a custom argument completer.</span></span>

## <span data-ttu-id="9cf26-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9cf26-105">SYNTAX</span></span>

### <span data-ttu-id="9cf26-106">Systeem eigenset</span><span class="sxs-lookup"><span data-stu-id="9cf26-106">NativeSet</span></span>

```
Register-ArgumentCompleter -CommandName <String[]> -ScriptBlock <ScriptBlock> [-Native]
 [<CommonParameters>]
```

### <span data-ttu-id="9cf26-107">Power shell-set</span><span class="sxs-lookup"><span data-stu-id="9cf26-107">PowerShellSet</span></span>

```
Register-ArgumentCompleter [-CommandName <String[]>] -ParameterName <String>
 -ScriptBlock <ScriptBlock> [<CommonParameters>]
```

## <span data-ttu-id="9cf26-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9cf26-108">DESCRIPTION</span></span>

<span data-ttu-id="9cf26-109">De `Register-ArgumentCompleter` cmdlet registreert een volledig aangepaste argument.</span><span class="sxs-lookup"><span data-stu-id="9cf26-109">The `Register-ArgumentCompleter` cmdlet registers a custom argument completer.</span></span> <span data-ttu-id="9cf26-110">Met de functie voor het argument voltooid kunt u tijdens runtime dynamische tabblad voltooiing opgeven voor elke opdracht die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="9cf26-110">An argument completer allows you to provide dynamic tab completion, at run time for any command that you specify.</span></span>

## <span data-ttu-id="9cf26-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9cf26-111">EXAMPLES</span></span>

### <span data-ttu-id="9cf26-112">Voor beeld 1: een volledig aangepaste argument registreren</span><span class="sxs-lookup"><span data-stu-id="9cf26-112">Example 1: Register a custom argument completer</span></span>

<span data-ttu-id="9cf26-113">In het volgende voor beeld wordt een argument voltooid geregistreerd voor de para meter **id** van de `Set-TimeZone` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9cf26-113">The following example registers an argument completer for the **Id** parameter of the `Set-TimeZone` cmdlet.</span></span>

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

<span data-ttu-id="9cf26-114">Met de eerste opdracht maakt u een script blok waarbij de vereiste para meters worden gebruikt die worden door gegeven wanneer de gebruiker op het <kbd>tabblad</kbd>klikt. Zie de beschrijving van de para meter **script Block** voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9cf26-114">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="9cf26-115">Binnen het script blok worden de beschik bare waarden voor **id** opgehaald met behulp van de `Get-TimeZone` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9cf26-115">Within the script block, the available values for **Id** are retrieved using the `Get-TimeZone` cmdlet.</span></span> <span data-ttu-id="9cf26-116">De eigenschap **id** voor elke tijd zone wordt door gegeven aan de `Where-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9cf26-116">The **Id** property for each Time Zone is piped to the `Where-Object` cmdlet.</span></span> <span data-ttu-id="9cf26-117">De `Where-Object` cmdlet filtert alle id's die niet beginnen met de waarde die is opgegeven door `$wordToComplete` , die de tekst bevat die de gebruiker heeft getypt voordat ze op <kbd>Tab</kbd>werden gedrukt. De gefilterde id's worden door gegeven aan de `For-EachObject` cmdlet die elke waarde in de aanhalings tekens omsluit, wanneer de waarde spaties bevat.</span><span class="sxs-lookup"><span data-stu-id="9cf26-117">The `Where-Object` cmdlet filters out any ids that do not start with the value provided by `$wordToComplete`, which represents the text the user typed before they pressed <kbd>Tab</kbd>. The filtered ids are piped to the `For-EachObject` cmdlet which encloses each value in quotes, should the value contain spaces.</span></span>

<span data-ttu-id="9cf26-118">Met de tweede opdracht wordt het argument completer geregistreerd door de script Block, de **para meter** **-id** en de **opdracht** naam door te geven `Set-TimeZone` .</span><span class="sxs-lookup"><span data-stu-id="9cf26-118">The second command registers the argument completer by passing the scriptblock, the **ParameterName** **Id** and the **CommandName** `Set-TimeZone`.</span></span>

### <span data-ttu-id="9cf26-119">Voor beeld 2: Details toevoegen aan de waarden voor het volt ooien van het tabblad</span><span class="sxs-lookup"><span data-stu-id="9cf26-119">Example 2: Add details to your tab completion values</span></span>

<span data-ttu-id="9cf26-120">In het volgende voor beeld wordt het volt ooien van het tabblad voor de para meter **name** van de cmdlet overschreven `Stop-Service` en worden alleen actieve services geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="9cf26-120">The following example overwrites tab completion for the **Name** parameter of the `Stop-Service` cmdlet and only returns running services.</span></span>

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

<span data-ttu-id="9cf26-121">Met de eerste opdracht maakt u een script blok waarbij de vereiste para meters worden gebruikt die worden door gegeven wanneer de gebruiker op het <kbd>tabblad</kbd>klikt. Zie de beschrijving van de para meter **script Block** voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9cf26-121">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="9cf26-122">In het-script blok haalt de eerste opdracht alle actieve services op met de `Where-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9cf26-122">Within the script block, the first command retrieves all running services using the `Where-Object` cmdlet.</span></span> <span data-ttu-id="9cf26-123">De services worden door gegeven aan de `ForEach-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9cf26-123">The services are piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="9cf26-124">`ForEach-Object`Met de cmdlet wordt een nieuw [System. Management. Automation. CompletionResult](/dotnet/api/system.management.automation.completionresult) -object gemaakt en gevuld met de naam van de huidige service (vertegenwoordigd door de pijplijn variabele `$_.Name` ).</span><span class="sxs-lookup"><span data-stu-id="9cf26-124">The `ForEach-Object` cmdlet creates a new [System.Management.Automation.CompletionResult](/dotnet/api/system.management.automation.completionresult) object and populates it with the name of the current service (represented by the pipeline variable `$_.Name`).</span></span>

<span data-ttu-id="9cf26-125">Met het **CompletionResult** -object kunt u aanvullende Details voor elke geretourneerde waarde opgeven:</span><span class="sxs-lookup"><span data-stu-id="9cf26-125">The **CompletionResult** object allows you to provide additional details to each returned value:</span></span>

- <span data-ttu-id="9cf26-126">**completionText** (teken reeks): de tekst die moet worden gebruikt als resultaat van automatisch volt ooien.</span><span class="sxs-lookup"><span data-stu-id="9cf26-126">**completionText** (String) - The text to be used as the auto completion result.</span></span> <span data-ttu-id="9cf26-127">Dit is de waarde die wordt verzonden naar de opdracht.</span><span class="sxs-lookup"><span data-stu-id="9cf26-127">This is the value sent to the command.</span></span>
- <span data-ttu-id="9cf26-128">**listItemText** (teken reeks): de tekst die moet worden weer gegeven in een lijst, bijvoorbeeld wanneer de gebruiker op de <kbd>CTRL</kbd>- + <kbd>spatie</kbd>klikt.</span><span class="sxs-lookup"><span data-stu-id="9cf26-128">**listItemText** (String) - The text to be displayed in a list, such as when the user presses <kbd>Ctrl</kbd>+<kbd>Space</kbd>.</span></span> <span data-ttu-id="9cf26-129">Dit wordt alleen gebruikt voor weer gave en wordt niet door gegeven aan de opdracht wanneer deze is geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="9cf26-129">This is used for display only and is not passed to the command when selected.</span></span>
- <span data-ttu-id="9cf26-130">**resultType** ([CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)): het type voltooiings resultaat.</span><span class="sxs-lookup"><span data-stu-id="9cf26-130">**resultType** ([CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)) - The type of completion result.</span></span>
- <span data-ttu-id="9cf26-131">**knop info** (teken reeks): de tekst voor de knop info met details die moeten worden weer gegeven over het object.</span><span class="sxs-lookup"><span data-stu-id="9cf26-131">**toolTip** (String) - The text for the tooltip with details to be displayed about the object.</span></span>
  <span data-ttu-id="9cf26-132">Dit is zichtbaar wanneer de gebruiker een item selecteert nadat u op <kbd>CTRL</kbd>-spatie hebt gedrukt + <kbd></kbd>.</span><span class="sxs-lookup"><span data-stu-id="9cf26-132">This is visible when the user selects an item after pressing <kbd>Ctrl</kbd>+<kbd>Space</kbd>.</span></span>

<span data-ttu-id="9cf26-133">Met de laatste opdracht wordt gedemonstreerd dat gestopte services nog steeds hand matig kunnen worden door gegeven aan de `Stop-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9cf26-133">The last command demonstrates that stopped services can still be passed in manually to the `Stop-Service` cmdlet.</span></span> <span data-ttu-id="9cf26-134">Het vullen van het tabblad is alleen van invloed op het onderhouds aspect.</span><span class="sxs-lookup"><span data-stu-id="9cf26-134">The tab completion is the only aspect affected.</span></span>

### <span data-ttu-id="9cf26-135">Voor beeld 3: een aangepaste systeem eigen argument voor de volledige functie registreren</span><span class="sxs-lookup"><span data-stu-id="9cf26-135">Example 3: Register a custom Native argument completer</span></span>

<span data-ttu-id="9cf26-136">U kunt de **systeem eigen** para meter gebruiken om het volt ooien van een opdracht in te stellen.</span><span class="sxs-lookup"><span data-stu-id="9cf26-136">You can use the **Native** parameter to provide tab-completion for a native command.</span></span> <span data-ttu-id="9cf26-137">In het volgende voor beeld wordt het volt ooien van het tabblad voor de `dotnet` opdracht regel interface (CLI) toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="9cf26-137">The following example adds tab-completion for the `dotnet` Command Line Interface (CLI).</span></span>

> [!NOTE]
> <span data-ttu-id="9cf26-138">De `dotnet complete` opdracht is alleen beschikbaar in versie 2,0 en hoger van de DotNet-cli.</span><span class="sxs-lookup"><span data-stu-id="9cf26-138">The `dotnet complete` command is only available in version 2.0 and greater of the dotnet cli.</span></span>

```powershell
$scriptblock = {
    param($wordToComplete, $commandAst, $cursorPosition)
        dotnet complete --position $cursorPosition $commandAst.ToString() | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
        }
}
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock $scriptblock
```

<span data-ttu-id="9cf26-139">Met de eerste opdracht maakt u een script blok waarbij de vereiste para meters worden gebruikt die worden door gegeven wanneer de gebruiker op het <kbd>tabblad</kbd>klikt. Zie de beschrijving van de para meter **script Block** voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9cf26-139">The first command creates a script block which takes the required parameters which are passed in when the user presses <kbd>Tab</kbd>. For more information, see the **ScriptBlock** parameter description.</span></span>

<span data-ttu-id="9cf26-140">In het-script blok `dotnet complete` wordt de opdracht gebruikt om het volt ooien van het tabblad uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="9cf26-140">Within the script block, the `dotnet complete` command is used to perform the tab completion.</span></span>
<span data-ttu-id="9cf26-141">De resultaten worden door gegeven aan de `ForEach-Object` cmdlet die gebruikmaakt van de **nieuwe** statische methode van de klasse [System. Management. Automation. CompletionResult](/dotnet/api/system.management.automation.completionresult) om voor elke waarde een nieuw **CompletionResult** -object te maken.</span><span class="sxs-lookup"><span data-stu-id="9cf26-141">The results are piped to the `ForEach-Object` cmdlet which use the **new** static method of the [System.Management.Automation.CompletionResult](/dotnet/api/system.management.automation.completionresult) class to create a new **CompletionResult** object for each value.</span></span>

## <span data-ttu-id="9cf26-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9cf26-142">PARAMETERS</span></span>

### <span data-ttu-id="9cf26-143">-Opdrachtnaam</span><span class="sxs-lookup"><span data-stu-id="9cf26-143">-CommandName</span></span>

<span data-ttu-id="9cf26-144">Hiermee geeft u de naam van de opdrachten als een matrix.</span><span class="sxs-lookup"><span data-stu-id="9cf26-144">Specifies the name of the commands as an array.</span></span>

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

### <span data-ttu-id="9cf26-145">-Systeem eigen</span><span class="sxs-lookup"><span data-stu-id="9cf26-145">-Native</span></span>

<span data-ttu-id="9cf26-146">Geeft aan dat het argument volledig is voor een systeem eigen opdracht waarbij Power shell geen parameter namen kan volt ooien.</span><span class="sxs-lookup"><span data-stu-id="9cf26-146">Indicates that the argument completer is for a native command where PowerShell cannot complete parameter names.</span></span>

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

### <span data-ttu-id="9cf26-147">-Para meternaam</span><span class="sxs-lookup"><span data-stu-id="9cf26-147">-ParameterName</span></span>

<span data-ttu-id="9cf26-148">Hiermee geeft u de naam van de para meter op waarvan het argument wordt voltooid.</span><span class="sxs-lookup"><span data-stu-id="9cf26-148">Specifies the name of the parameter whose argument is being completed.</span></span> <span data-ttu-id="9cf26-149">De opgegeven parameter naam kan geen opsommings waarde zijn, zoals de para meter **ForegroundColor** van de `Write-Host` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9cf26-149">The parameter name specified cannot be an enumerated value, such as the **ForegroundColor** parameter of the `Write-Host` cmdlet.</span></span>

<span data-ttu-id="9cf26-150">Zie [about_Enum](./About/about_Enum.md)voor meer informatie over enums.</span><span class="sxs-lookup"><span data-stu-id="9cf26-150">For more information on enums, see [about_Enum](./About/about_Enum.md).</span></span>

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

### <span data-ttu-id="9cf26-151">-Script Block</span><span class="sxs-lookup"><span data-stu-id="9cf26-151">-ScriptBlock</span></span>

<span data-ttu-id="9cf26-152">Hiermee geeft u de opdrachten op die moeten worden uitgevoerd om de tabblad voltooiing uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="9cf26-152">Specifies the commands to run to perform tab completion.</span></span> <span data-ttu-id="9cf26-153">Het script blok dat u opgeeft, moet de waarden retour neren die de invoer hebben voltooid.</span><span class="sxs-lookup"><span data-stu-id="9cf26-153">The script block you provide should return the values that complete the input.</span></span> <span data-ttu-id="9cf26-154">Het script blok moet de waarden van de pijp lijn ( `ForEach-Object` , `Where-Object` enzovoort) of een andere geschikte methode ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="9cf26-154">The script block must unroll the values using the pipeline (`ForEach-Object`, `Where-Object`, etc.), or another suitable method.</span></span> <span data-ttu-id="9cf26-155">Als u een matrix met waarden retourneert, wordt de gehele matrix als **één** waarde voor het volt ooien van een tab behandeld.</span><span class="sxs-lookup"><span data-stu-id="9cf26-155">Returning an array of values causes PowerShell to treat the entire array as **one** tab completion value.</span></span>

<span data-ttu-id="9cf26-156">Het script blok moet de volgende para meters accepteren in de opgegeven volg orde.</span><span class="sxs-lookup"><span data-stu-id="9cf26-156">The script block must accept the following parameters in the order specified below.</span></span> <span data-ttu-id="9cf26-157">De namen van de para meters zijn niet belang rijk omdat Power shell in de waarden van de positie wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="9cf26-157">The names of the parameters aren't important because PowerShell passes in the values by position.</span></span>

- <span data-ttu-id="9cf26-158">`$commandName` (Positie 0): deze para meter is ingesteld op de naam van de opdracht waarvoor het script blok het volt ooien van het tabblad oplevert.</span><span class="sxs-lookup"><span data-stu-id="9cf26-158">`$commandName` (Position 0) - This parameter is set to the name of the command for which the script block is providing tab completion.</span></span>
- <span data-ttu-id="9cf26-159">`$parameterName` (Positie 1)-deze para meter wordt ingesteld op de para meter waarvan de waarde het volt ooien van het tabblad vereist.</span><span class="sxs-lookup"><span data-stu-id="9cf26-159">`$parameterName` (Position 1) - This parameter is set to the parameter whose value requires tab completion.</span></span>
- <span data-ttu-id="9cf26-160">`$wordToComplete` (Positie 2): deze para meter is ingesteld op waarde die de gebruiker heeft opgegeven voordat deze <kbd>Tab</kbd>werd ingedrukt. Het script blok moet deze waarde gebruiken om de waarden voor het volt ooien van tabs te bepalen.</span><span class="sxs-lookup"><span data-stu-id="9cf26-160">`$wordToComplete` (Position 2) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="9cf26-161">`$commandAst` (Positie 3): deze para meter is ingesteld op de abstracte syntaxis structuur (AST) voor de huidige invoer regel.</span><span class="sxs-lookup"><span data-stu-id="9cf26-161">`$commandAst` (Position 3) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="9cf26-162">Zie [AST class](/dotnet/api/system.management.automation.language.ast)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9cf26-162">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="9cf26-163">`$fakeBoundParameters` (Positie 4): deze para meter is ingesteld op een hashtabel die de `$PSBoundParameters` voor de cmdlet bevat, voordat het <kbd>tabblad</kbd>van de gebruiker wordt ingedrukt. Zie [about_Automatic_Variables](./About/about_Automatic_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9cf26-163">`$fakeBoundParameters` (Position 4) - This parameter is set to a hashtable containing the `$PSBoundParameters` for the cmdlet, before the user pressed <kbd>Tab</kbd>. For more information, see [about_Automatic_Variables](./About/about_Automatic_Variables.md).</span></span>

<span data-ttu-id="9cf26-164">Wanneer u de **systeem eigen** para meter opgeeft, moet het script blok de volgende para meters in de opgegeven volg orde hebben.</span><span class="sxs-lookup"><span data-stu-id="9cf26-164">When you specify the **Native** parameter, the script block must take the following parameters in the specified order.</span></span> <span data-ttu-id="9cf26-165">De namen van de para meters zijn niet belang rijk omdat Power shell in de waarden van de positie wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="9cf26-165">The names of the parameters aren't important because PowerShell passes in the values by position.</span></span>

- <span data-ttu-id="9cf26-166">`$wordToComplete` (Positie 0): deze para meter is ingesteld op waarde die de gebruiker heeft opgegeven voordat deze <kbd>Tab</kbd>werd ingedrukt. Het script blok moet deze waarde gebruiken om de waarden voor het volt ooien van tabs te bepalen.</span><span class="sxs-lookup"><span data-stu-id="9cf26-166">`$wordToComplete` (Position 0) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="9cf26-167">`$commandAst` (Positie 1): deze para meter is ingesteld op de abstracte syntaxis structuur (AST) voor de huidige invoer regel.</span><span class="sxs-lookup"><span data-stu-id="9cf26-167">`$commandAst` (Position 1) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="9cf26-168">Zie [AST class](/dotnet/api/system.management.automation.language.ast)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9cf26-168">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="9cf26-169">`$cursorPosition` (Positie 2): deze para meter wordt ingesteld op de positie van de cursor wanneer het <kbd>tabblad</kbd>van de gebruiker wordt ingedrukt.</span><span class="sxs-lookup"><span data-stu-id="9cf26-169">`$cursorPosition` (Position 2) - This parameter is set to the position of the cursor when the user pressed <kbd>Tab</kbd>.</span></span>

<span data-ttu-id="9cf26-170">U kunt ook een **ArgumentCompleter** als parameter kenmerk opgeven.</span><span class="sxs-lookup"><span data-stu-id="9cf26-170">You can also provide an **ArgumentCompleter** as a parameter attribute.</span></span> <span data-ttu-id="9cf26-171">Zie [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9cf26-171">For more information, see [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md).</span></span>

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

### <span data-ttu-id="9cf26-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9cf26-172">CommonParameters</span></span>

<span data-ttu-id="9cf26-173">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9cf26-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9cf26-174">Zie [about_CommonParameters](./About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9cf26-174">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="9cf26-175">INVOER</span><span class="sxs-lookup"><span data-stu-id="9cf26-175">INPUTS</span></span>

### <span data-ttu-id="9cf26-176">Geen</span><span class="sxs-lookup"><span data-stu-id="9cf26-176">None</span></span>

<span data-ttu-id="9cf26-177">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="9cf26-177">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="9cf26-178">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9cf26-178">OUTPUTS</span></span>

### <span data-ttu-id="9cf26-179">Geen</span><span class="sxs-lookup"><span data-stu-id="9cf26-179">None</span></span>

<span data-ttu-id="9cf26-180">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="9cf26-180">This cmdlet returns no output.</span></span>

## <span data-ttu-id="9cf26-181">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9cf26-181">NOTES</span></span>

## <span data-ttu-id="9cf26-182">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9cf26-182">RELATED LINKS</span></span>

