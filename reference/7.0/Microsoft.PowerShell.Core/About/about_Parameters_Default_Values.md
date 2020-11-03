---
description: Hierin wordt beschreven hoe u aangepaste standaard waarden instelt voor cmdlet-para meters en geavanceerde functies.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 5/31/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters_default_values?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters_Default_Values
ms.openlocfilehash: c2bc8c64b6b3c0d3627d9db61132dde58522555e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252709"
---
# <a name="about-parameters-default-values"></a><span data-ttu-id="ef659-104">Over de standaard waarden van para meters</span><span class="sxs-lookup"><span data-stu-id="ef659-104">About Parameters Default Values</span></span>

## <a name="short-description"></a><span data-ttu-id="ef659-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="ef659-105">Short description</span></span>

<span data-ttu-id="ef659-106">Hierin wordt beschreven hoe u aangepaste standaard waarden instelt voor cmdlet-para meters en geavanceerde functies.</span><span class="sxs-lookup"><span data-stu-id="ef659-106">Describes how to set custom default values for cmdlet parameters and advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="ef659-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="ef659-107">Long description</span></span>

<span data-ttu-id="ef659-108">Met de `$PSDefaultParameterValues` Voorkeurs variabele kunt u aangepaste standaard waarden opgeven voor een cmdlet of een geavanceerde functie.</span><span class="sxs-lookup"><span data-stu-id="ef659-108">The `$PSDefaultParameterValues` preference variable lets you specify custom default values for any cmdlet or advanced function.</span></span> <span data-ttu-id="ef659-109">Cmdlets en geavanceerde functies gebruiken de aangepaste standaard waarde tenzij u een andere waarde in de opdracht opgeeft.</span><span class="sxs-lookup"><span data-stu-id="ef659-109">Cmdlets and advanced functions use the custom default value unless you specify another value in the command.</span></span>

<span data-ttu-id="ef659-110">De auteurs van cmdlets en geavanceerde functies stellen standaard waarden in voor de para meters.</span><span class="sxs-lookup"><span data-stu-id="ef659-110">The authors of cmdlets and advanced functions set standard default values for their parameters.</span></span> <span data-ttu-id="ef659-111">Normaal gesp roken zijn de standaard waarden handig, maar ze zijn mogelijk niet geschikt voor alle omgevingen.</span><span class="sxs-lookup"><span data-stu-id="ef659-111">Typically, the standard default values are useful, but they might not be appropriate for all environments.</span></span>

<span data-ttu-id="ef659-112">Deze functie is vooral nuttig wanneer u dezelfde alternatieve parameter waarde moet opgeven bijna elke keer dat u de opdracht gebruikt of wanneer een bepaalde parameter waarde moeilijk te onthouden is, zoals de naam van een e-mail server of project-GUID.</span><span class="sxs-lookup"><span data-stu-id="ef659-112">This feature is especially useful when you must specify the same alternate parameter value nearly every time you use the command or when a particular parameter value is difficult to remember, such as an email server name or project GUID.</span></span>

<span data-ttu-id="ef659-113">Als de gewenste standaard waarde zoals verwacht varieert, kunt u een script blok opgeven dat verschillende standaard waarden voor een para meter onder verschillende omstandigheden levert.</span><span class="sxs-lookup"><span data-stu-id="ef659-113">If the desired default value varies predictably, you can specify a script block that provides different default values for a parameter under different conditions.</span></span>

<span data-ttu-id="ef659-114">`$PSDefaultParameterValues` is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ef659-114">`$PSDefaultParameterValues` was introduced in PowerShell 3.0.</span></span>

## <a name="syntax"></a><span data-ttu-id="ef659-115">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef659-115">Syntax</span></span>

<span data-ttu-id="ef659-116">De `$PSDefaultParameterValues` variabele is een hash-tabel die de indeling van sleutels valideert als object type **System. Management. Automation. DefaultParameterDictionary**.</span><span class="sxs-lookup"><span data-stu-id="ef659-116">The `$PSDefaultParameterValues` variable is a hash table that validates the format of keys as an object type of **System.Management.Automation.DefaultParameterDictionary**.</span></span> <span data-ttu-id="ef659-117">De hash-tabel bevat **sleutel-** waardeparen.</span><span class="sxs-lookup"><span data-stu-id="ef659-117">The hash table contains **Key/Value** pairs.</span></span> <span data-ttu-id="ef659-118">Een **sleutel** heeft de indeling `CmdletName:ParameterName` .</span><span class="sxs-lookup"><span data-stu-id="ef659-118">A **Key** is in the format `CmdletName:ParameterName`.</span></span> <span data-ttu-id="ef659-119">Een **waarde** is de **DefaultValue** of **script Block** die is toegewezen aan de sleutel.</span><span class="sxs-lookup"><span data-stu-id="ef659-119">A **Value** is the **DefaultValue** or **ScriptBlock** assigned to the key.</span></span>

<span data-ttu-id="ef659-120">De syntaxis van de `$PSDefaultParameterValues` Voorkeurs variabele is als volgt:</span><span class="sxs-lookup"><span data-stu-id="ef659-120">The syntax of the `$PSDefaultParameterValues` preference variable is as follows:</span></span>

```
$PSDefaultParameterValues=@{"CmdletName:ParameterName"="DefaultValue"}

$PSDefaultParameterValues=@{ "CmdletName:ParameterName"={{ScriptBlock}} }

$PSDefaultParameterValues["Disabled"]=$True | $False
```

<span data-ttu-id="ef659-121">Joker tekens zijn toegestaan in de waarden van de **cmdlet** -en **para meter** .</span><span class="sxs-lookup"><span data-stu-id="ef659-121">Wildcard characters are permitted in the **CmdletName** and **ParameterName** values.</span></span>

<span data-ttu-id="ef659-122">Als u een specifieke **sleutel/waarde-** paar wilt instellen, wijzigen, toevoegen of verwijderen `$PSDefaultParameterValues` , gebruikt u de methoden om een standaard-hash-tabel te bewerken.</span><span class="sxs-lookup"><span data-stu-id="ef659-122">To set, change, add, or remove a specific **Key/Value** pair from `$PSDefaultParameterValues`, use the methods to edit a standard hash table.</span></span> <span data-ttu-id="ef659-123">Bijvoorbeeld de methoden **toevoegen** en **verwijderen** .</span><span class="sxs-lookup"><span data-stu-id="ef659-123">For example, the **Add** and **Remove** methods.</span></span> <span data-ttu-id="ef659-124">Met deze methoden worden andere waarden in de hash-tabel niet overschreven.</span><span class="sxs-lookup"><span data-stu-id="ef659-124">These methods don't overwrite other values in the hash table.</span></span>

<span data-ttu-id="ef659-125">Er is een andere syntaxis die geen bestaande hash-tabel overschrijft `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="ef659-125">There's another syntax that doesn't overwrite an existing `$PSDefaultParameterValues` hash table.</span></span> <span data-ttu-id="ef659-126">Als u een specifieke **sleutel/waarde-** paar wilt toevoegen of wijzigen, gebruikt u de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="ef659-126">To add or change a specific **Key/Value** pair, use the following syntax:</span></span>

```
$PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

<span data-ttu-id="ef659-127">De **cmdletnaam** moet de naam zijn van een cmdlet of de naam van een geavanceerde functie die gebruikmaakt van het kenmerk **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="ef659-127">The **CmdletName** must be the name of a cmdlet or the name of an advanced function that uses the **CmdletBinding** attribute.</span></span> <span data-ttu-id="ef659-128">U kunt niet gebruiken `$PSDefaultParameterValues` om standaard waarden voor scripts of eenvoudige functies op te geven.</span><span class="sxs-lookup"><span data-stu-id="ef659-128">You can't use `$PSDefaultParameterValues` to specify default values for scripts or simple functions.</span></span>

<span data-ttu-id="ef659-129">De **DefaultValue** kan een object of een script blok zijn.</span><span class="sxs-lookup"><span data-stu-id="ef659-129">The **DefaultValue** can be an object or a script block.</span></span> <span data-ttu-id="ef659-130">Als de waarde een script blok is, wordt het script blok door Power shell geëvalueerd en wordt het resultaat gebruikt als waarde voor de para meter.</span><span class="sxs-lookup"><span data-stu-id="ef659-130">If the value is a script block, PowerShell evaluates the script block and uses the result as the parameter value.</span></span> <span data-ttu-id="ef659-131">Wanneer de opgegeven para meter een script blok waarde accepteert, plaatst u de script blok waarde in een tweede set accolades, zoals:</span><span class="sxs-lookup"><span data-stu-id="ef659-131">When the specified parameter accepts a script block value, enclose the script block value in a second set of braces, such as:</span></span>

```powershell
$PSDefaultParameterValues=@{ "Invoke-Command:ScriptBlock"={{Get-Process}} }
```

<span data-ttu-id="ef659-132">Raadpleeg de volgende documenten voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="ef659-132">For more information, see the following documents:</span></span>

- [<span data-ttu-id="ef659-133">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="ef659-133">about_Hash_Tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="ef659-134">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="ef659-134">about_Script_Blocks</span></span>](about_Script_Blocks.md)
- [<span data-ttu-id="ef659-135">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="ef659-135">about_Preference_Variables</span></span>](about_Preference_Variables.md)

## <a name="examples"></a><span data-ttu-id="ef659-136">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="ef659-136">Examples</span></span>

### <a name="how-to-set-psdefaultparametervalues"></a><span data-ttu-id="ef659-137">\$PSDefaultParameterValues instellen</span><span class="sxs-lookup"><span data-stu-id="ef659-137">How to set \$PSDefaultParameterValues</span></span>

<span data-ttu-id="ef659-138">`$PSDefaultParameterValues` is een voorkeurs variabele, zodat deze alleen bestaat in de sessie waarin deze is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="ef659-138">`$PSDefaultParameterValues` is a preference variable, so it exists only in the session in which it's set.</span></span> <span data-ttu-id="ef659-139">Er is geen standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="ef659-139">It has no default value.</span></span>

<span data-ttu-id="ef659-140">Als u wilt instellen `$PSDefaultParameterValues` , typt u de naam van de variabele en een of meer **sleutel-** waardeparen.</span><span class="sxs-lookup"><span data-stu-id="ef659-140">To set `$PSDefaultParameterValues`, type the variable name and one or more **Key/Value** pairs.</span></span> <span data-ttu-id="ef659-141">Als u een andere `$PSDefaultParameterValues` opdracht uitvoert, wordt de bestaande hash-tabel overschreven.</span><span class="sxs-lookup"><span data-stu-id="ef659-141">If you run another `$PSDefaultParameterValues` command, it overwrites the existing hash table.</span></span>

<span data-ttu-id="ef659-142">Zie [waarden toevoegen aan \$ PSDefaultParameterValues](#how-to-add-values-to-psdefaultparametervalues) of informatie over het [wijzigen van waarden in \$ PSDefaultParameterValues](#how-to-change-values-in-psdefaultparametervalues)voor voor beelden van het wijzigen van **sleutel/waarde** -paren zonder bestaande waarden van hash-tabellen te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="ef659-142">For examples about how to change **Key/Value** pairs without overwriting existing hash table values, see [How to add values to \$PSDefaultParameterValues](#how-to-add-values-to-psdefaultparametervalues) or [How to change values in \$PSDefaultParameterValues](#how-to-change-values-in-psdefaultparametervalues).</span></span>

<span data-ttu-id="ef659-143">Als u wilt opslaan `$PSDefaultParameterValues` voor toekomstige sessies, voegt `$PSDefaultParameterValues` u een opdracht toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="ef659-143">To save `$PSDefaultParameterValues` for future sessions, add a `$PSDefaultParameterValues` command to your PowerShell profile.</span></span> <span data-ttu-id="ef659-144">Zie [about_Profiles](about_Profiles.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ef659-144">For more information, see [about_Profiles](about_Profiles.md).</span></span>

#### <a name="set-a-custom-default-value"></a><span data-ttu-id="ef659-145">Een aangepaste standaard waarde instellen</span><span class="sxs-lookup"><span data-stu-id="ef659-145">Set a custom default value</span></span>

<span data-ttu-id="ef659-146">Met het **sleutel/waarde-** paar wordt de `Send-MailMessage:SmtpServer` sleutel ingesteld op een aangepaste standaard waarde van **Server123**.</span><span class="sxs-lookup"><span data-stu-id="ef659-146">The **Key/Value** pair sets the `Send-MailMessage:SmtpServer` key to a custom default value of **Server123**.</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
}
```

#### <a name="set-default-values-for-multiple-parameters"></a><span data-ttu-id="ef659-147">Standaard waarden voor meerdere para meters instellen</span><span class="sxs-lookup"><span data-stu-id="ef659-147">Set default values for multiple parameters</span></span>

<span data-ttu-id="ef659-148">Als u standaard waarden wilt instellen voor meerdere para meters, scheidt u elk **sleutel/waarde** -paar met een punt komma ( `;` ).</span><span class="sxs-lookup"><span data-stu-id="ef659-148">To set default values for multiple parameters, separate each **Key/Value** pair with a semicolon (`;`).</span></span> <span data-ttu-id="ef659-149">De `Send-MailMessage:SmtpServer` `Get-WinEvent:LogName` sleutels en worden ingesteld op aangepaste standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="ef659-149">The `Send-MailMessage:SmtpServer` and `Get-WinEvent:LogName` keys are set to custom default values.</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123";
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
}
```

#### <a name="use-wildcards-and-switch-parameters"></a><span data-ttu-id="ef659-150">Joker tekens en switch parameters gebruiken</span><span class="sxs-lookup"><span data-stu-id="ef659-150">Use wildcards and switch parameters</span></span>

<span data-ttu-id="ef659-151">De cmdlet-en parameter namen mogen joker tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="ef659-151">The cmdlet and parameter names can contain wildcard characters.</span></span> <span data-ttu-id="ef659-152">Gebruik `$True` en `$False` om waarden in te stellen voor switch parameters, zoals **uitgebreid**.</span><span class="sxs-lookup"><span data-stu-id="ef659-152">Use `$True` and `$False` to set values for switch parameters, such as **Verbose**.</span></span> <span data-ttu-id="ef659-153">De para meter **uitgebreid** van de algemene para meter is ingesteld op `$True` voor alle opdrachten.</span><span class="sxs-lookup"><span data-stu-id="ef659-153">The common parameter's **Verbose** parameter is set to `$True` for all commands.</span></span>

```powershell
$PSDefaultParameterValues = @{"*:Verbose"=$True}
```

#### <a name="use-an-array-for-the-default-value"></a><span data-ttu-id="ef659-154">Een matrix gebruiken voor de standaard waarde</span><span class="sxs-lookup"><span data-stu-id="ef659-154">Use an array for the default value</span></span>

<span data-ttu-id="ef659-155">Als een para meter meerdere waarden kan accepteren, een matrix, kunt u meerdere waarden instellen als de standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="ef659-155">If a parameter can accept multiple values, an array, you can set multiple values as the default values.</span></span> <span data-ttu-id="ef659-156">De standaard waarde van de `Invoke-Command:ComputerName` sleutel wordt ingesteld op een matrix waarde van **Server01** en **Server02**.</span><span class="sxs-lookup"><span data-stu-id="ef659-156">The default value of the `Invoke-Command:ComputerName` key is set to an array value of **Server01** and **Server02**.</span></span>

```powershell
$PSDefaultParameterValues = @{
  "Invoke-Command:ComputerName"="Server01","Server02"
}
```

#### <a name="use-a-script-block"></a><span data-ttu-id="ef659-157">Een script blok gebruiken</span><span class="sxs-lookup"><span data-stu-id="ef659-157">Use a script block</span></span>

<span data-ttu-id="ef659-158">U kunt een script blok gebruiken om verschillende standaard waarden op te geven voor een para meter onder verschillende omstandigheden.</span><span class="sxs-lookup"><span data-stu-id="ef659-158">You can use a script block to specify different default values for a parameter under different conditions.</span></span> <span data-ttu-id="ef659-159">Power shell evalueert het script blok en gebruikt het resultaat als de standaard parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="ef659-159">PowerShell evaluates the script block and uses the result as the default parameter value.</span></span>

<span data-ttu-id="ef659-160">De `Format-Table:AutoSize` sleutel stelt die para meter in op de standaard waarde **waar**.</span><span class="sxs-lookup"><span data-stu-id="ef659-160">The `Format-Table:AutoSize` key sets that switch parameter to a default value of **True**.</span></span> <span data-ttu-id="ef659-161">De `If` instructie bevat een voor waarde die de `$host.Name` moet de Power shell-console, **ConsoleHost**.</span><span class="sxs-lookup"><span data-stu-id="ef659-161">The `If` statement contains a condition that the `$host.Name` must be the PowerShell console, **ConsoleHost**.</span></span>

```powershell
$PSDefaultParameterValues=@{
  "Format-Table:AutoSize"={if ($host.Name -eq "ConsoleHost"){$True}}
}
```

<span data-ttu-id="ef659-162">Als een para meter een script blok waarde accepteert, plaatst u het script blok in een extra verzameling accolades.</span><span class="sxs-lookup"><span data-stu-id="ef659-162">If a parameter accepts a script block value, enclose the script block in an extra set of braces.</span></span> <span data-ttu-id="ef659-163">Wanneer Power shell het buitenste script blok evalueert, is het resultaat het interne script blok en dat is ingesteld als de standaard parameter waarde.</span><span class="sxs-lookup"><span data-stu-id="ef659-163">When PowerShell evaluates the outer script block, the result is the inner script block, and that is set as the default parameter value.</span></span>

<span data-ttu-id="ef659-164">De `Invoke-Command:ScriptBlock` sleutel is ingesteld op de standaard waarde van het **logboek voor systeem gebeurtenissen** , omdat het script blok is inge sloten in een tweede set accolades.</span><span class="sxs-lookup"><span data-stu-id="ef659-164">The `Invoke-Command:ScriptBlock` key set to a default value of the **System event log** because the script block is enclosed in a second set of braces.</span></span> <span data-ttu-id="ef659-165">Het resultaat van het script blok wordt door gegeven aan de `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ef659-165">The result of the script block is passed to the `Invoke-Command` cmdlet.</span></span>

```powershell
$PSDefaultParameterValues=@{
  "Invoke-Command:ScriptBlock"={{Get-EventLog -Log System}}
}
```

### <a name="how-to-get-psdefaultparametervalues"></a><span data-ttu-id="ef659-166">\$PSDefaultParameterValues ophalen</span><span class="sxs-lookup"><span data-stu-id="ef659-166">How to get \$PSDefaultParameterValues</span></span>

<span data-ttu-id="ef659-167">De waarden van de hash-tabel worden weer gegeven door `$PSDefaultParameterValues` de Power shell-prompt in te voeren.</span><span class="sxs-lookup"><span data-stu-id="ef659-167">The hash table values are displayed by entering `$PSDefaultParameterValues` at the PowerShell prompt.</span></span>

<span data-ttu-id="ef659-168">Een `$PSDefaultParameterValues` hash-tabel is ingesteld met drie **sleutel-** waardeparen.</span><span class="sxs-lookup"><span data-stu-id="ef659-168">A `$PSDefaultParameterValues` hash table is set with three **Key/Value** pairs.</span></span>
<span data-ttu-id="ef659-169">Deze hash-tabel wordt gebruikt in de volgende voor beelden die beschrijven hoe waarden moeten worden toegevoegd, gewijzigd of verwijderd `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="ef659-169">This hash table is used in the following examples that describe how to add, change, and remove values from `$PSDefaultParameterValues`.</span></span>

```
PS> $PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
  "Get-*:Verbose"=$True
}

PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

<span data-ttu-id="ef659-170">Als u de waarde van een specifieke `CmdletName:ParameterName` sleutel wilt ophalen, gebruikt u de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="ef659-170">To get the value of a specific `CmdletName:ParameterName` key, use the following syntax:</span></span>

```
$PSDefaultParameterValues["CmdletName:ParameterName"]
```

<span data-ttu-id="ef659-171">Als u bijvoorbeeld de waarde voor de sleutel wilt ophalen `Send-MailMessage:SmtpServer` .</span><span class="sxs-lookup"><span data-stu-id="ef659-171">For example, to get the value for the `Send-MailMessage:SmtpServer` key.</span></span>

```
PS> $PSDefaultParameterValues["Send-MailMessage:SmtpServer"]
Server123
```

### <a name="how-to-add-values-to-psdefaultparametervalues"></a><span data-ttu-id="ef659-172">Waarden toevoegen aan \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="ef659-172">How to add values to \$PSDefaultParameterValues</span></span>

<span data-ttu-id="ef659-173">Als u een waarde wilt toevoegen aan `$PSDefaultParameterValues` , gebruikt u de methode **add** .</span><span class="sxs-lookup"><span data-stu-id="ef659-173">To add a value to `$PSDefaultParameterValues`, use the **Add** method.</span></span> <span data-ttu-id="ef659-174">Het toevoegen van een waarde heeft geen invloed op de bestaande waarden van de hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="ef659-174">Adding a value doesn't affect the hash table's existing values.</span></span>

<span data-ttu-id="ef659-175">Gebruik een komma ( `,` ) om de **sleutel** te scheiden van de **waarde**.</span><span class="sxs-lookup"><span data-stu-id="ef659-175">Use a comma (`,`) to separate the **Key** from the **Value**.</span></span> <span data-ttu-id="ef659-176">De volgende syntaxis laat zien hoe u de methode **add** gebruikt voor `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="ef659-176">The following syntax shows how to use the **Add** method for `$PSDefaultParameterValues`.</span></span>

```
PS> $PSDefaultParameterValues.Add("CmdletName:ParameterName", "DefaultValue")
```

<span data-ttu-id="ef659-177">De hash-tabel die in het vorige voor beeld is gemaakt, wordt bijgewerkt met een nieuwe **sleutel/waarde-** paar.</span><span class="sxs-lookup"><span data-stu-id="ef659-177">The hash table created in the prior example is updated with a new **Key/Value** pair.</span></span> <span data-ttu-id="ef659-178">Met de methode **add** wordt de `Get-Process:Name` sleutel ingesteld op de waarde **Power shell**.</span><span class="sxs-lookup"><span data-stu-id="ef659-178">The **Add** method sets the `Get-Process:Name` key to the value **PowerShell**.</span></span>

```powershell
$PSDefaultParameterValues.Add("Get-Process:Name", "PowerShell")
```

<span data-ttu-id="ef659-179">Met de volgende syntaxis wordt hetzelfde resultaat bereikt.</span><span class="sxs-lookup"><span data-stu-id="ef659-179">The following syntax accomplishes the same result.</span></span>

```powershell
$PSDefaultParameterValues["Get-Process:Name"]="PowerShell"
```

<span data-ttu-id="ef659-180">Met de `$PSDefaultParameterValues` variabele wordt de bijgewerkte hash-tabel weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ef659-180">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="ef659-181">De `Get-Process:Name` sleutel is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="ef659-181">The `Get-Process:Name` key was added.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-Process:Name               PowerShell
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-remove-values-from-psdefaultparametervalues"></a><span data-ttu-id="ef659-182">Waarden verwijderen uit \$ PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="ef659-182">How to remove values from \$PSDefaultParameterValues</span></span>

<span data-ttu-id="ef659-183">Als u een waarde uit wilt verwijderen `$PSDefaultParameterValues` , gebruikt u de methode **verwijderen** van hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="ef659-183">To remove a value from `$PSDefaultParameterValues`, use the **Remove** method of hash tables.</span></span> <span data-ttu-id="ef659-184">Het verwijderen van een waarde heeft geen invloed op de bestaande waarden van de hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="ef659-184">Removing a value doesn't affect the hash table's existing values.</span></span>

<span data-ttu-id="ef659-185">De volgende syntaxis laat zien hoe u de methode **Remove** gebruikt op `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="ef659-185">The following syntax shows how to use the **Remove** method on `$PSDefaultParameterValues`.</span></span>

```
PS> $PSDefaultParameterValues.Remove("CmdletName:ParameterName")
```

<span data-ttu-id="ef659-186">In dit voor beeld wordt de in het vorige voor beeld gemaakte hashtabel bijgewerkt om een **sleutel/waarde-** paar te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="ef659-186">In this example, the hash table created in the prior example is updated to remove a **Key/Value** pair.</span></span> <span data-ttu-id="ef659-187">Met de methode **Remove** wordt de `Get-Process:Name` sleutel verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ef659-187">The **Remove** method removes the `Get-Process:Name` key.</span></span>

```powershell
$PSDefaultParameterValues.Remove("Get-Process:Name")
```

<span data-ttu-id="ef659-188">Met de `$PSDefaultParameterValues` variabele wordt de bijgewerkte hash-tabel weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ef659-188">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="ef659-189">De `Get-Process:Name` sleutel is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ef659-189">The `Get-Process:Name` key was removed.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-change-values-in-psdefaultparametervalues"></a><span data-ttu-id="ef659-190">Waarden in \$ PSDefaultParameterValues wijzigen</span><span class="sxs-lookup"><span data-stu-id="ef659-190">How to change values in \$PSDefaultParameterValues</span></span>

<span data-ttu-id="ef659-191">Wijzigingen in een specifieke waarde zijn niet van invloed op bestaande waarden van hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="ef659-191">Changes to a specific value don't affect existing hash table values.</span></span> <span data-ttu-id="ef659-192">Als u een specifiek **sleutel/waardepaar** wilt wijzigen in `$PSDefaultParameterValues` , gebruikt u de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="ef659-192">To change a specific **Key/Value** pair in `$PSDefaultParameterValues`, use the following syntax:</span></span>

```
PS> $PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

<span data-ttu-id="ef659-193">In dit voor beeld wordt de in het vorige voor beeld gemaakte hash-tabel bijgewerkt om een **sleutel/waarde-** paar te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="ef659-193">In this example, the hash table created in the prior example is updated to change a **Key/Value** pair.</span></span> <span data-ttu-id="ef659-194">Met de volgende opdracht wordt de `Send-MailMessage:SmtpServer` sleutel gewijzigd in een nieuwe waarde van **ServerXYZ**.</span><span class="sxs-lookup"><span data-stu-id="ef659-194">The following command changes the `Send-MailMessage:SmtpServer` key to a new value of **ServerXYZ**.</span></span>

```powershell
$PSDefaultParameterValues["Send-MailMessage:SmtpServer"]="ServerXYZ"
```

<span data-ttu-id="ef659-195">Met de `$PSDefaultParameterValues` variabele wordt de bijgewerkte hash-tabel weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ef659-195">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="ef659-196">De `Send-MailMessage:SmtpServer` sleutel is gewijzigd in een nieuwe waarde.</span><span class="sxs-lookup"><span data-stu-id="ef659-196">The `Send-MailMessage:SmtpServer` key was changed to a new value.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

### <a name="how-to-disable-and-re-enable-psdefaultparametervalues"></a><span data-ttu-id="ef659-197">PSDefaultParameterValues uitschakelen en opnieuw inschakelen \$</span><span class="sxs-lookup"><span data-stu-id="ef659-197">How to disable and re-enable \$PSDefaultParameterValues</span></span>

<span data-ttu-id="ef659-198">U kunt tijdelijk uitschakelen en vervolgens weer inschakelen `$PSDefaultParameterValues` .</span><span class="sxs-lookup"><span data-stu-id="ef659-198">You can temporarily disable and then re-enable `$PSDefaultParameterValues`.</span></span>
<span data-ttu-id="ef659-199">Uitschakelen `$PSDefaultParameterValues` is handig als u scripts uitvoert waarvoor verschillende standaard parameter waarden nodig zijn.</span><span class="sxs-lookup"><span data-stu-id="ef659-199">Disabling `$PSDefaultParameterValues` is useful if you're running scripts that need different default parameter values.</span></span>

<span data-ttu-id="ef659-200">Als u wilt uitschakelen `$PSDefaultParameterValues` , voegt u een sleutel toe `Disabled` met de waarde **True**.</span><span class="sxs-lookup"><span data-stu-id="ef659-200">To disable `$PSDefaultParameterValues`, add a key of `Disabled` with a value of **True**.</span></span> <span data-ttu-id="ef659-201">De waarden in blijven `$PSDefaultParameterValues` behouden, maar zijn niet effectief.</span><span class="sxs-lookup"><span data-stu-id="ef659-201">The values in `$PSDefaultParameterValues` are preserved, but aren't effective.</span></span>

```
PS> $PSDefaultParameterValues.Add("Disabled", $True)
```

<span data-ttu-id="ef659-202">Met de volgende syntaxis wordt hetzelfde resultaat bereikt.</span><span class="sxs-lookup"><span data-stu-id="ef659-202">The following syntax accomplishes the same result.</span></span>

```
PS> $PSDefaultParameterValues["Disabled"]=$True
```

<span data-ttu-id="ef659-203">De `$PSDefaultParameterValues` variabele geeft de bijgewerkte hash-tabel weer met de waarde voor de `Disabled` sleutel.</span><span class="sxs-lookup"><span data-stu-id="ef659-203">The `$PSDefaultParameterValues` variable displays the updated hash table with the value for the `Disabled` key.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       True
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

<span data-ttu-id="ef659-204">Als u het opnieuw wilt inschakelen `$PSDefaultParameterValues` , verwijdert u de **Uitgeschakelde** sleutel of wijzigt u de waarde van de **Uitgeschakelde** sleutel in `$False` .</span><span class="sxs-lookup"><span data-stu-id="ef659-204">To re-enable `$PSDefaultParameterValues`, remove the **Disabled** key or change the value of the **Disabled** key to `$False`.</span></span> <span data-ttu-id="ef659-205">De vorige waarde van `$PSDefaultParameterValues` is opnieuw effectief.</span><span class="sxs-lookup"><span data-stu-id="ef659-205">The previous value of `$PSDefaultParameterValues` is effective again.</span></span>

```
PS> $PSDefaultParameterValues.Remove("Disabled")
```

<span data-ttu-id="ef659-206">Met de volgende syntaxis wordt hetzelfde resultaat bereikt.</span><span class="sxs-lookup"><span data-stu-id="ef659-206">The following syntax accomplishes the same result.</span></span>

```
PS> $PSDefaultParameterValues["Disabled"]=$False
```

<span data-ttu-id="ef659-207">Met de `$PSDefaultParameterValues` variabele wordt de bijgewerkte hash-tabel weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ef659-207">The `$PSDefaultParameterValues` variable displays the updated hash table.</span></span> <span data-ttu-id="ef659-208">Wanneer de methode **Remove** wordt gebruikt, `Disabled` wordt de sleutel uit de uitvoer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ef659-208">When the **Remove** method is used, the `Disabled` key is removed from the output.</span></span>
<span data-ttu-id="ef659-209">Als de alternatieve syntaxis is gebruikt om opnieuw in te scha kelen `$PSDefaultParameterValues` , `Disabled` wordt de sleutel weer gegeven als **Onwaar**.</span><span class="sxs-lookup"><span data-stu-id="ef659-209">If the alternate syntax was used to re-enable `$PSDefaultParameterValues`, the `Disabled` key is displayed as **False**.</span></span>

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       False
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

## <a name="see-also"></a><span data-ttu-id="ef659-210">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ef659-210">See also</span></span>

[<span data-ttu-id="ef659-211">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ef659-211">about_CommonParameters</span></span>](https://go.microsoft.com/fwlink/?LinkID=113216)

[<span data-ttu-id="ef659-212">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="ef659-212">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="ef659-213">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="ef659-213">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="ef659-214">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="ef659-214">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="ef659-215">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="ef659-215">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="ef659-216">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="ef659-216">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="ef659-217">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="ef659-217">about_Script_Blocks</span></span>](about_Script_Blocks.md)
