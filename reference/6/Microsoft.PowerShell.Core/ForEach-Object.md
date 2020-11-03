---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: 5a1a53c2b312ef36c80ecfb2a771d2fee2ebea7f
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/10/2020
ms.locfileid: "93251905"
---
# <span data-ttu-id="311e8-103">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="311e8-103">ForEach-Object</span></span>

## <span data-ttu-id="311e8-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="311e8-104">SYNOPSIS</span></span>
<span data-ttu-id="311e8-105">Hiermee wordt een bewerking uitgevoerd voor elk item in een verzameling invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="311e8-105">Performs an operation against each item in a collection of input objects.</span></span>

## <span data-ttu-id="311e8-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="311e8-106">SYNTAX</span></span>

### <span data-ttu-id="311e8-107">ScriptBlockSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="311e8-107">ScriptBlockSet (Default)</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="311e8-108">PropertyAndMethodSet</span><span class="sxs-lookup"><span data-stu-id="311e8-108">PropertyAndMethodSet</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="311e8-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="311e8-109">DESCRIPTION</span></span>

<span data-ttu-id="311e8-110">`ForEach-Object`Met de cmdlet wordt een bewerking uitgevoerd op elk item in een verzameling invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="311e8-110">The `ForEach-Object` cmdlet performs an operation on each item in a collection of input objects.</span></span> <span data-ttu-id="311e8-111">De invoer objecten kunnen worden gesluizen naar de cmdlet of worden opgegeven met behulp van de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="311e8-111">The input objects can be piped to the cmdlet or specified by using the **InputObject** parameter.</span></span>

<span data-ttu-id="311e8-112">Vanaf Windows Power Shell 3,0 zijn er twee verschillende manieren om een opdracht te maken `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="311e8-112">Starting in Windows PowerShell 3.0, there are two different ways to construct a `ForEach-Object` command.</span></span>

- <span data-ttu-id="311e8-113">**Script blok**.</span><span class="sxs-lookup"><span data-stu-id="311e8-113">**Script block**.</span></span> <span data-ttu-id="311e8-114">U kunt een script blok gebruiken om de bewerking op te geven.</span><span class="sxs-lookup"><span data-stu-id="311e8-114">You can use a script block to specify the operation.</span></span> <span data-ttu-id="311e8-115">In het-script blok gebruikt `$_` u de variabele om het huidige object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="311e8-115">Within the script block, use the `$_` variable to represent the current object.</span></span> <span data-ttu-id="311e8-116">Het script blok is de waarde van de para meter **process** .</span><span class="sxs-lookup"><span data-stu-id="311e8-116">The script block is the value of the **Process** parameter.</span></span> <span data-ttu-id="311e8-117">Het script blok kan elk Power shell-script bevatten.</span><span class="sxs-lookup"><span data-stu-id="311e8-117">The script block can contain any PowerShell script.</span></span>

  <span data-ttu-id="311e8-118">Met de volgende opdracht wordt bijvoorbeeld de waarde van de eigenschap **proces** naam van elk proces op de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="311e8-118">For example, the following command gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object {$_.ProcessName}`

  <span data-ttu-id="311e8-119">`ForEach-Object` ondersteunt de `begin` , `process` , en `end` blokken zoals beschreven in [about_functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="311e8-119">`ForEach-Object` supports the `begin`, `process`, and `end` blocks as described in [about_functions](about/about_functions.md#piping-objects-to-functions).</span></span>

  > [!NOTE]
  > <span data-ttu-id="311e8-120">De script blokken worden uitgevoerd in het bereik van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="311e8-120">The script blocks run in the caller's scope.</span></span> <span data-ttu-id="311e8-121">De blokken hebben daarom toegang tot variabelen in dat bereik en kunnen nieuwe variabelen maken die in dat bereik behouden blijven nadat de cmdlet is voltooid.</span><span class="sxs-lookup"><span data-stu-id="311e8-121">Therefore the blocks have access to variables in that scope and can create new variables that persist in that scope after the cmdlet completes.</span></span>

- <span data-ttu-id="311e8-122">**Bewerkings instructie**.</span><span class="sxs-lookup"><span data-stu-id="311e8-122">**Operation statement**.</span></span> <span data-ttu-id="311e8-123">U kunt ook een bewerkings instructie schrijven die veel meer lijkt op natuurlijke taal.</span><span class="sxs-lookup"><span data-stu-id="311e8-123">You can also write an operation statement, which is much more like natural language.</span></span> <span data-ttu-id="311e8-124">U kunt de bewerkings instructie gebruiken om een eigenschaps waarde op te geven of een methode aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="311e8-124">You can use the operation statement to specify a property value or call a method.</span></span> <span data-ttu-id="311e8-125">Er zijn bewerkings instructies geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="311e8-125">Operation statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="311e8-126">Met de volgende opdracht wordt ook de waarde van de eigenschap **proces** naam van elk proces op de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="311e8-126">For example, the following command also gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object ProcessName`

## <span data-ttu-id="311e8-127">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="311e8-127">EXAMPLES</span></span>

### <span data-ttu-id="311e8-128">Voor beeld 1: gehele getallen in een matrix delen</span><span class="sxs-lookup"><span data-stu-id="311e8-128">Example 1: Divide integers in an array</span></span>

<span data-ttu-id="311e8-129">In dit voor beeld wordt een matrix van drie gehele getallen gebruikt en worden elke reeks gedeeld door 1024.</span><span class="sxs-lookup"><span data-stu-id="311e8-129">This example takes an array of three integers and divides each one of them by 1024.</span></span>

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### <span data-ttu-id="311e8-130">Voor beeld 2: de lengte van alle bestanden in een map ophalen</span><span class="sxs-lookup"><span data-stu-id="311e8-130">Example 2: Get the length of all the files in a directory</span></span>

<span data-ttu-id="311e8-131">In dit voor beeld worden de bestanden en mappen in de installatie directory van Power shell verwerkt `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="311e8-131">This example processes the files and directories in the PowerShell installation directory `$PSHOME`.</span></span>

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

<span data-ttu-id="311e8-132">Als het object geen map is, wordt de naam van het bestand door het script blok opgehaald, wordt de waarde van de eigenschap **Length** gedeeld door 1024 en wordt een spatie ("") toegevoegd om het te scheiden van de volgende vermelding.</span><span class="sxs-lookup"><span data-stu-id="311e8-132">If the object is not a directory, the script block gets the name of the file, divides the value of its **Length** property by 1024, and adds a space (" ") to separate it from the next entry.</span></span> <span data-ttu-id="311e8-133">De cmdlet gebruikt de eigenschap **PSISContainer** om te bepalen of een object een directory is.</span><span class="sxs-lookup"><span data-stu-id="311e8-133">The cmdlet uses the **PSISContainer** property to determine whether an object is a directory.</span></span>

### <span data-ttu-id="311e8-134">Voor beeld 3: uitvoeren op de meest recente systeem gebeurtenissen</span><span class="sxs-lookup"><span data-stu-id="311e8-134">Example 3: Operate on the most recent System events</span></span>

<span data-ttu-id="311e8-135">In dit voor beeld worden de 1000 meest recente gebeurtenissen van het systeem gebeurtenis logboek naar een tekst bestand geschreven.</span><span class="sxs-lookup"><span data-stu-id="311e8-135">This example write the 1000 most recent events from the System event log to a text file.</span></span> <span data-ttu-id="311e8-136">De huidige tijd wordt weer gegeven vóór en na de verwerking van de gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="311e8-136">The current time is displayed before and after processing the events.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

<span data-ttu-id="311e8-137">`Get-EventLog` Hiermee worden de 1000 meest recente gebeurtenissen van het systeem gebeurtenis logboek opgehaald en opgeslagen in de `$Events` variabele.</span><span class="sxs-lookup"><span data-stu-id="311e8-137">`Get-EventLog` gets the 1000 most recent events from the System event log and stores them in the `$Events` variable.</span></span> <span data-ttu-id="311e8-138">`$Events` wordt vervolgens door gegeven aan de `ForEach-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="311e8-138">`$Events` is then piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="311e8-139">Met de para meter **begin** worden de huidige datum en tijd weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="311e8-139">The **Begin** parameter displays the current date and time.</span></span> <span data-ttu-id="311e8-140">Vervolgens gebruikt de para meter **process** de `Out-File` cmdlet om een tekst bestand te maken met de naam events.txt en wordt de bericht eigenschap van elk van de gebeurtenissen in dat bestand opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="311e8-140">Next, the **Process** parameter uses the `Out-File` cmdlet to create a text file that is named events.txt and stores the message property of each of the events in that file.</span></span> <span data-ttu-id="311e8-141">De laatste para meter **End** wordt gebruikt om de datum en tijd weer te geven nadat alle verwerking is voltooid.</span><span class="sxs-lookup"><span data-stu-id="311e8-141">Last, the **End** parameter is used to display the date and time after all of the processing has completed.</span></span>

### <span data-ttu-id="311e8-142">Voor beeld 4: de waarde van een register sleutel wijzigen</span><span class="sxs-lookup"><span data-stu-id="311e8-142">Example 4: Change the value of a Registry key</span></span>

<span data-ttu-id="311e8-143">In dit voor beeld wordt de waarde van de register vermelding **remotepath** in alle subsleutels onder de sleutel gewijzigd in `HKCU:\Network` hoofd letters.</span><span class="sxs-lookup"><span data-stu-id="311e8-143">This example changes the value of the **RemotePath** registry entry in all of the subkeys under the `HKCU:\Network` key to uppercase text.</span></span>

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

<span data-ttu-id="311e8-144">U kunt deze indeling gebruiken om het formulier of de inhoud van een register vermelding te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="311e8-144">You can use this format to change the form or content of a registry entry value.</span></span>

<span data-ttu-id="311e8-145">Elke subsleutel in de **netwerk** sleutel vertegenwoordigt een toegewezen netwerk station waarmee opnieuw verbinding wordt gemaakt bij het aanmelden.</span><span class="sxs-lookup"><span data-stu-id="311e8-145">Each subkey in the **Network** key represents a mapped network drive that will reconnect at logon.</span></span>
<span data-ttu-id="311e8-146">De vermelding **remotepath** bevat het UNC-pad van het verbonden station.</span><span class="sxs-lookup"><span data-stu-id="311e8-146">The **RemotePath** entry contains the UNC path of the connected drive.</span></span> <span data-ttu-id="311e8-147">Als u bijvoorbeeld het station E: toewijst aan `\\Server\Share` , wordt er een **e** -subsleutel van `HKCU:\Network` en de waarde van de register vermelding **remotepath** in de **E** -subsleutel `\\Server\Share` .</span><span class="sxs-lookup"><span data-stu-id="311e8-147">For example, if you map the E: drive to `\\Server\Share`, there will be an **E** subkey of `HKCU:\Network` and the value of the **RemotePath** registry entry in the **E** subkey is `\\Server\Share`.</span></span>

<span data-ttu-id="311e8-148">De opdracht gebruikt de `Get-ItemProperty` cmdlet om alle subsleutels van de **netwerk** sleutel en de `Set-ItemProperty` cmdlet te verkrijgen om de waarde van de register **vermelding remotepath** in elke sleutel te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="311e8-148">The command uses the `Get-ItemProperty` cmdlet to get all of the subkeys of the **Network** key and the `Set-ItemProperty` cmdlet to change the value of the **RemotePath** registry entry in each key.</span></span>
<span data-ttu-id="311e8-149">In de `Set-ItemProperty` opdracht is het pad de waarde van de eigenschap **PSPath** van de register sleutel.</span><span class="sxs-lookup"><span data-stu-id="311e8-149">In the `Set-ItemProperty` command, the path is the value of the **PSPath** property of the registry key.</span></span> <span data-ttu-id="311e8-150">Dit is een eigenschap van het Microsoft .NET Framework-object dat de register sleutel vertegenwoordigt, niet een register vermelding.</span><span class="sxs-lookup"><span data-stu-id="311e8-150">This is a property of the Microsoft .NET Framework object that represents the registry key, not a registry entry.</span></span> <span data-ttu-id="311e8-151">De opdracht maakt gebruik van de methode **ToUpper ()** van de **remotepath** -waarde. Dit is een teken reeks (REG_SZ).</span><span class="sxs-lookup"><span data-stu-id="311e8-151">The command uses the **ToUpper()** method of the **RemotePath** value, which is a string (REG_SZ).</span></span>

<span data-ttu-id="311e8-152">Omdat `Set-ItemProperty` de eigenschap van elke sleutel wordt gewijzigd, `ForEach-Object` is de cmdlet vereist voor toegang tot de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="311e8-152">Because `Set-ItemProperty` is changing the property of each key, the `ForEach-Object` cmdlet is required to access the property.</span></span>

### <span data-ttu-id="311e8-153">Voor beeld 5: de $Null automatische variabele gebruiken</span><span class="sxs-lookup"><span data-stu-id="311e8-153">Example 5: Use the $Null automatic variable</span></span>

<span data-ttu-id="311e8-154">In dit voor beeld ziet u het effect van de `$Null` Automatische variabele voor de `ForEach-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="311e8-154">This example shows the effect of piping the `$Null` automatic variable to the `ForEach-Object` cmdlet.</span></span>

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

<span data-ttu-id="311e8-155">Omdat in Power shell NULL wordt behandeld als een expliciete tijdelijke aanduiding, `ForEach-Object` genereert de cmdlet een waarde voor `$Null` , net zoals voor andere objecten die u naar de pipet.</span><span class="sxs-lookup"><span data-stu-id="311e8-155">Because PowerShell treats null as an explicit placeholder, the `ForEach-Object` cmdlet generates a value for `$Null`, just as it does for other objects that you pipe to it.</span></span>

### <span data-ttu-id="311e8-156">Voor beeld 6: eigenschaps waarden ophalen</span><span class="sxs-lookup"><span data-stu-id="311e8-156">Example 6: Get property values</span></span>

<span data-ttu-id="311e8-157">In dit voor beeld wordt de waarde van de eigenschap **Path** van alle geïnstalleerde Power shell-modules opgehaald met behulp van de para meter **membernaam** van de `ForEach-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="311e8-157">This example gets the value of the **Path** property of all installed PowerShell modules by using the **MemberName** parameter of the `ForEach-Object` cmdlet.</span></span>

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

<span data-ttu-id="311e8-158">De tweede opdracht is gelijk aan de eerste.</span><span class="sxs-lookup"><span data-stu-id="311e8-158">The second command is equivalent to the first.</span></span> <span data-ttu-id="311e8-159">Het gebruikt de `Foreach` alias van de `ForEach-Object` cmdlet en laat de naam van de para meter **lidnaam** , die optioneel is.</span><span class="sxs-lookup"><span data-stu-id="311e8-159">It uses the `Foreach` alias of the `ForEach-Object` cmdlet and omits the name of the **MemberName** parameter, which is optional.</span></span>

<span data-ttu-id="311e8-160">De `ForEach-Object` cmdlet is erg handig voor het ophalen van eigenschaps waarden, omdat deze de waarde ophaalt zonder het type te wijzigen, in tegens telling tot de **notatie** -cmdlets of de `Select-Object` cmdlet, waarmee het type eigenschaps waarde wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="311e8-160">The `ForEach-Object` cmdlet is very useful for getting property values, because it gets the value without changing the type, unlike the **Format** cmdlets or the `Select-Object` cmdlet, which change the property value type.</span></span>

### <span data-ttu-id="311e8-161">Voor beeld 7: module namen splitsen in onderdeel namen</span><span class="sxs-lookup"><span data-stu-id="311e8-161">Example 7: Split module names into component names</span></span>

<span data-ttu-id="311e8-162">In deze voor beelden ziet u drie manieren om twee punt-gescheiden module namen te splitsen in hun onderdeel namen.</span><span class="sxs-lookup"><span data-stu-id="311e8-162">This examples shows three ways to split two dot-separated module names into their component names.</span></span>

```powershell
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object {$_.Split(".")}
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object -MemberName Split -ArgumentList "."
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | Foreach Split "."
```

```Output
Microsoft
PowerShell
Core
Microsoft
PowerShell
Host
```

<span data-ttu-id="311e8-163">Met de opdrachten wordt de **Splits** methode van teken reeksen aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="311e8-163">The commands call the **Split** method of strings.</span></span> <span data-ttu-id="311e8-164">De drie opdrachten gebruiken een andere syntaxis, maar ze zijn gelijkwaardig en kunnen worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="311e8-164">The three commands use different syntax, but they are equivalent and interchangeable.</span></span>

<span data-ttu-id="311e8-165">De eerste opdracht maakt gebruik van de traditionele syntaxis, die een script blok en de huidige object operator bevat `$_` .</span><span class="sxs-lookup"><span data-stu-id="311e8-165">The first command uses the traditional syntax, which includes a script block and the current object operator `$_`.</span></span> <span data-ttu-id="311e8-166">De punt notatie wordt gebruikt om de methode en haakjes op te geven voor het argument scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="311e8-166">It uses the dot syntax to specify the method and parentheses to enclose the delimiter argument.</span></span>

<span data-ttu-id="311e8-167">De tweede opdracht gebruikt de para meter **lidnaam** om de **Split** -methode en de para meter **argumentnaam** op te geven om de punt (".") als scheidings teken te identificeren.</span><span class="sxs-lookup"><span data-stu-id="311e8-167">The second command uses the **MemberName** parameter to specify the **Split** method and the **ArgumentName** parameter to identify the dot (".") as the split delimiter.</span></span>

<span data-ttu-id="311e8-168">De derde opdracht maakt gebruik van de **foreach** -alias van de `ForEach-Object` cmdlet en laat de namen van de para meters **lidnaam** en **argument List** , die optioneel zijn.</span><span class="sxs-lookup"><span data-stu-id="311e8-168">The third command uses the **Foreach** alias of the `ForEach-Object` cmdlet and omits the names of the **MemberName** and **ArgumentList** parameters, which are optional.</span></span>

### <span data-ttu-id="311e8-169">Voor beeld 8: ForEach-Object gebruiken met twee script blokken</span><span class="sxs-lookup"><span data-stu-id="311e8-169">Example 8: Using ForEach-Object with two script blocks</span></span>

<span data-ttu-id="311e8-170">In dit voor beeld geven we twee script blokken op positie.</span><span class="sxs-lookup"><span data-stu-id="311e8-170">In this example we pass two script blocks positionally.</span></span> <span data-ttu-id="311e8-171">Alle script blokken binden aan de **proces** parameter.</span><span class="sxs-lookup"><span data-stu-id="311e8-171">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="311e8-172">Ze worden echter behandeld alsof ze zijn door gegeven aan de **begin** -en **proces** parameters.</span><span class="sxs-lookup"><span data-stu-id="311e8-172">However, they are treated as if they had been passed to the **Begin** and **Process** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### <span data-ttu-id="311e8-173">Voor beeld 9: ForEach-Object gebruiken met meer dan twee script blokken</span><span class="sxs-lookup"><span data-stu-id="311e8-173">Example 9: Using ForEach-Object with more than two script blocks</span></span>

<span data-ttu-id="311e8-174">In dit voor beeld geven we twee script blokken op positie.</span><span class="sxs-lookup"><span data-stu-id="311e8-174">In this example we pass two script blocks positionally.</span></span> <span data-ttu-id="311e8-175">Alle script blokken binden aan de **proces** parameter.</span><span class="sxs-lookup"><span data-stu-id="311e8-175">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="311e8-176">Ze worden echter behandeld alsof ze zijn door gegeven aan de **begin** -, **proces** -en **End** -para meters.</span><span class="sxs-lookup"><span data-stu-id="311e8-176">However, they are treated as if they had been passed to the **Begin** , **Process** , and **End** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process A' }  { 'process B' }  { 'end' }
```

```Output
begin
process A
process B
process A
process B
end
```

> [!NOTE]
> <span data-ttu-id="311e8-177">Het eerste script blok wordt altijd toegewezen aan het `begin` blok, het laatste blok wordt toegewezen aan het `end` blok en de blokken tussen zijn allemaal toegewezen aan het blok `process` .</span><span class="sxs-lookup"><span data-stu-id="311e8-177">The first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

### <span data-ttu-id="311e8-178">Voor beeld 10: meerdere script blokken uitvoeren voor elk pijplijn item</span><span class="sxs-lookup"><span data-stu-id="311e8-178">Example 10: Run multiple script blocks for each pipeline item</span></span>

<span data-ttu-id="311e8-179">Zoals weer gegeven in het vorige voor beeld, worden er meerdere script blokken door gegeven met behulp van de **proces** parameter Get toegewezen aan de **begin** -en **End** -para meters.</span><span class="sxs-lookup"><span data-stu-id="311e8-179">As shown in the previous example, multiple script blocks passed using the **Process** parameter get mapped to the **Begin** and **End** parameters.</span></span> <span data-ttu-id="311e8-180">Om deze toewijzing te vermijden, moet u expliciete waarden opgeven voor de **begin** -en **eind** parameters.</span><span class="sxs-lookup"><span data-stu-id="311e8-180">To avoid this mapping, you must provide explicit values for the **Begin** and **End** parameters.</span></span>

```powershell
1..2 | ForEach-Object -Begin $null -Process { 'one' }, { 'two' }, { 'three' } -End $null
```

```Output
one
two
three
one
two
three
```

## <span data-ttu-id="311e8-181">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="311e8-181">PARAMETERS</span></span>

### <span data-ttu-id="311e8-182">-Argument List</span><span class="sxs-lookup"><span data-stu-id="311e8-182">-ArgumentList</span></span>

<span data-ttu-id="311e8-183">Hiermee geeft u een matrix op met argumenten voor een methode aanroep.</span><span class="sxs-lookup"><span data-stu-id="311e8-183">Specifies an array of arguments to a method call.</span></span> <span data-ttu-id="311e8-184">Zie [about_Splatting](about/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="311e8-184">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="311e8-185">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="311e8-185">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: PropertyAndMethodSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="311e8-186">-Begin</span><span class="sxs-lookup"><span data-stu-id="311e8-186">-Begin</span></span>

<span data-ttu-id="311e8-187">Hiermee geeft u een script blok op dat wordt uitgevoerd voordat deze cmdlet invoer objecten verwerkt.</span><span class="sxs-lookup"><span data-stu-id="311e8-187">Specifies a script block that runs before this cmdlet processes any input objects.</span></span> <span data-ttu-id="311e8-188">Dit script blok wordt slechts één keer uitgevoerd voor de volledige pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="311e8-188">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="311e8-189">Zie about_Functions voor meer informatie over het `begin` blok [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="311e8-189">For more information about the `begin` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="311e8-190">-End</span><span class="sxs-lookup"><span data-stu-id="311e8-190">-End</span></span>

<span data-ttu-id="311e8-191">Hiermee geeft u een script blok op dat wordt uitgevoerd nadat deze cmdlet alle invoer objecten heeft verwerkt.</span><span class="sxs-lookup"><span data-stu-id="311e8-191">Specifies a script block that runs after this cmdlet processes all input objects.</span></span> <span data-ttu-id="311e8-192">Dit script blok wordt slechts één keer uitgevoerd voor de volledige pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="311e8-192">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="311e8-193">Zie about_Functions voor meer informatie over het `end` blok [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="311e8-193">For more information about the `end` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="311e8-194">-Input object</span><span class="sxs-lookup"><span data-stu-id="311e8-194">-InputObject</span></span>

<span data-ttu-id="311e8-195">Hiermee worden de invoer objecten opgegeven.</span><span class="sxs-lookup"><span data-stu-id="311e8-195">Specifies the input objects.</span></span> <span data-ttu-id="311e8-196">`ForEach-Object` Hiermee wordt het script blok of de bewerkings instructie voor elk invoer object uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="311e8-196">`ForEach-Object` runs the script block or operation statement on each input object.</span></span> <span data-ttu-id="311e8-197">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="311e8-197">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="311e8-198">Wanneer u de para meter **input object** gebruikt in `ForEach-Object` plaats van de resultaten van de pijpleiding opdracht, `ForEach-Object` wordt de waarde van **input object** behandeld als een enkel object.</span><span class="sxs-lookup"><span data-stu-id="311e8-198">When you use the **InputObject** parameter with `ForEach-Object`, instead of piping command results to `ForEach-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="311e8-199">Dit geldt ook als de waarde een verzameling is die het resultaat is van een opdracht, zoals `-InputObject (Get-Process)` .</span><span class="sxs-lookup"><span data-stu-id="311e8-199">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span>
<span data-ttu-id="311e8-200">Omdat **input object** geen individuele eigenschappen van een matrix of verzameling van objecten kan retour neren, raden we u aan dat als u gebruikt `ForEach-Object` om bewerkingen uit te voeren op een verzameling objecten voor objecten met specifieke waarden in gedefinieerde eigenschappen, u `ForEach-Object` in de pijp lijn gebruikt, zoals wordt weer gegeven in de voor beelden in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="311e8-200">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that if you use `ForEach-Object` to perform operations on a collection of objects for those objects that have specific values in defined properties, you use `ForEach-Object` in the pipeline, as shown in the examples in this topic.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="311e8-201">-Lidnaam</span><span class="sxs-lookup"><span data-stu-id="311e8-201">-MemberName</span></span>

<span data-ttu-id="311e8-202">Hiermee geeft u de eigenschap op die moet worden opgehaald of de methode die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="311e8-202">Specifies the property to get or the method to call.</span></span>

<span data-ttu-id="311e8-203">Joker tekens zijn toegestaan, maar werken alleen als de resulterende teken reeks wordt omgezet in een unieke waarde.</span><span class="sxs-lookup"><span data-stu-id="311e8-203">Wildcard characters are permitted, but work only if the resulting string resolves to a unique value.</span></span>
<span data-ttu-id="311e8-204">Als u bijvoorbeeld uitvoert `Get-Process | ForEach -MemberName *Name` , en er meer dan één lid bestaat met een naam die de naam van de teken reeks bevat, zoals de **ProcessName** eigenschappen van de **naam** van de computer en name, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="311e8-204">If, for example, you run `Get-Process | ForEach -MemberName *Name`, and more than one member exists with a name that contains the string Name, such as the **ProcessName** and **Name** properties, the command fails.</span></span>

<span data-ttu-id="311e8-205">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="311e8-205">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: PropertyAndMethodSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="311e8-206">-Proces</span><span class="sxs-lookup"><span data-stu-id="311e8-206">-Process</span></span>

<span data-ttu-id="311e8-207">Hiermee geeft u de bewerking op die op elk invoer object wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="311e8-207">Specifies the operation that is performed on each input object.</span></span> <span data-ttu-id="311e8-208">Dit script blok wordt uitgevoerd voor elk object in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="311e8-208">This script block is run for every object in the pipeline.</span></span> <span data-ttu-id="311e8-209">Zie about_Functions voor meer informatie over het `process` blok [about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="311e8-209">For more information about the `process` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

<span data-ttu-id="311e8-210">Wanneer u meerdere script blokken voor de para meter **process** opgeeft, wordt het eerste script blok altijd toegewezen aan het `begin` blok.</span><span class="sxs-lookup"><span data-stu-id="311e8-210">When you provide multiple script blocks to the **Process** parameter, the first script block is always mapped to the `begin` block.</span></span> <span data-ttu-id="311e8-211">Als er slechts twee script blokken zijn, wordt het tweede blok toegewezen aan het `process` blok.</span><span class="sxs-lookup"><span data-stu-id="311e8-211">If there are only two script blocks, the second block is mapped to the `process` block.</span></span> <span data-ttu-id="311e8-212">Als er drie of meer script blokken zijn, wordt het eerste script blok altijd toegewezen aan het `begin` blok, wordt het laatste blok toegewezen aan het `end` blok en worden de blokken tussen beide toegewezen aan het `process` blok.</span><span class="sxs-lookup"><span data-stu-id="311e8-212">If there are three or more script blocks, first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="311e8-213">-RemainingScripts</span><span class="sxs-lookup"><span data-stu-id="311e8-213">-RemainingScripts</span></span>

<span data-ttu-id="311e8-214">Hiermee geeft u alle script blokken op die niet worden gebruikt door de **proces** parameter.</span><span class="sxs-lookup"><span data-stu-id="311e8-214">Specifies all script blocks that are not taken by the **Process** parameter.</span></span>

<span data-ttu-id="311e8-215">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="311e8-215">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="311e8-216">-Confirm</span><span class="sxs-lookup"><span data-stu-id="311e8-216">-Confirm</span></span>

<span data-ttu-id="311e8-217">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="311e8-217">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="311e8-218">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="311e8-218">-WhatIf</span></span>

<span data-ttu-id="311e8-219">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="311e8-219">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="311e8-220">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="311e8-220">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="311e8-221">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="311e8-221">CommonParameters</span></span>

<span data-ttu-id="311e8-222">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="311e8-222">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="311e8-223">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="311e8-223">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="311e8-224">INVOER</span><span class="sxs-lookup"><span data-stu-id="311e8-224">INPUTS</span></span>

### <span data-ttu-id="311e8-225">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="311e8-225">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="311e8-226">U kunt elk object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="311e8-226">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="311e8-227">UITVOER</span><span class="sxs-lookup"><span data-stu-id="311e8-227">OUTPUTS</span></span>

### <span data-ttu-id="311e8-228">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="311e8-228">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="311e8-229">Deze cmdlet retourneert objecten die worden bepaald door de invoer.</span><span class="sxs-lookup"><span data-stu-id="311e8-229">This cmdlet returns objects that are determined by the input.</span></span>

## <span data-ttu-id="311e8-230">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="311e8-230">NOTES</span></span>

- <span data-ttu-id="311e8-231">De `ForEach-Object` cmdlet werkt op dezelfde manier als de **foreach** -instructie, behalve dat u invoer niet kunt door sluizen naar een **foreach** -instructie.</span><span class="sxs-lookup"><span data-stu-id="311e8-231">The `ForEach-Object` cmdlet works much like the **Foreach** statement, except that you cannot pipe input to a **Foreach** statement.</span></span> <span data-ttu-id="311e8-232">Zie [about_Foreach](./About/about_Foreach.md)voor meer informatie over de instructie **foreach** .</span><span class="sxs-lookup"><span data-stu-id="311e8-232">For more information about the **Foreach** statement, see [about_Foreach](./About/about_Foreach.md).</span></span>

- <span data-ttu-id="311e8-233">Vanaf Power Shell 4,0 `Where` en `ForEach` methoden zijn toegevoegd voor gebruik met verzamelingen.</span><span class="sxs-lookup"><span data-stu-id="311e8-233">Starting in PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span> <span data-ttu-id="311e8-234">U kunt hier meer lezen over deze nieuwe methoden [about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="311e8-234">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

## <span data-ttu-id="311e8-235">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="311e8-235">RELATED LINKS</span></span>

[<span data-ttu-id="311e8-236">Compare-object</span><span class="sxs-lookup"><span data-stu-id="311e8-236">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="311e8-237">Where-object</span><span class="sxs-lookup"><span data-stu-id="311e8-237">Where-Object</span></span>](Where-Object.md)

[<span data-ttu-id="311e8-238">Groep-object</span><span class="sxs-lookup"><span data-stu-id="311e8-238">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="311e8-239">Meting object</span><span class="sxs-lookup"><span data-stu-id="311e8-239">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="311e8-240">New-Object</span><span class="sxs-lookup"><span data-stu-id="311e8-240">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="311e8-241">Select-Object</span><span class="sxs-lookup"><span data-stu-id="311e8-241">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="311e8-242">Sorteer object</span><span class="sxs-lookup"><span data-stu-id="311e8-242">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="311e8-243">T-object</span><span class="sxs-lookup"><span data-stu-id="311e8-243">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)
