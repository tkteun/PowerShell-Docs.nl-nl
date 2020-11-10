---
description: Hierin wordt beschreven hoe u alternatieve namen gebruikt voor cmdlets en opdrachten in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_aliases?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Aliases
ms.openlocfilehash: 9094e34d4d3cbb8ee951593e15411e8e3234fa1a
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387767"
---
# <a name="about-aliases"></a><span data-ttu-id="85c4e-104">Over aliassen</span><span class="sxs-lookup"><span data-stu-id="85c4e-104">About Aliases</span></span>

## <a name="short-description"></a><span data-ttu-id="85c4e-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="85c4e-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="85c4e-106">Hierin wordt beschreven hoe u alternatieve namen gebruikt voor cmdlets en opdrachten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="85c4e-106">Describes how to use alternate names for cmdlets and commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="85c4e-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="85c4e-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="85c4e-108">Een alias is een alternatieve naam of bijnaam voor een cmdlet of voor een opdracht element, zoals een functie, script, bestand of een uitvoerbaar bestand.</span><span class="sxs-lookup"><span data-stu-id="85c4e-108">An alias is an alternate name or nickname for a cmdlet or for a command element, such as a function, script, file, or executable file.</span></span> <span data-ttu-id="85c4e-109">U kunt de alias gebruiken in plaats van de naam van de opdracht in Power shell-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="85c4e-109">You can use the alias instead of the command name in any PowerShell commands.</span></span>

<span data-ttu-id="85c4e-110">Als u een alias wilt maken, gebruikt u de cmdlet New-Alias.</span><span class="sxs-lookup"><span data-stu-id="85c4e-110">To create an alias, use the New-Alias cmdlet.</span></span> <span data-ttu-id="85c4e-111">Met de volgende opdracht wordt bijvoorbeeld het ' gas ' alias voor de `Get-AuthenticodeSignature` cmdlet gemaakt:</span><span class="sxs-lookup"><span data-stu-id="85c4e-111">For example, the following command creates the "gas" alias for the `Get-AuthenticodeSignature` cmdlet:</span></span>

```powershell
New-Alias -Name gas -Value Get-AuthenticodeSignature
```

<span data-ttu-id="85c4e-112">Nadat u de alias voor de naam van de cmdlet hebt gemaakt, kunt u de alias gebruiken in plaats van de naam van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="85c4e-112">After you create the alias for the cmdlet name, you can use the alias instead of the cmdlet name.</span></span> <span data-ttu-id="85c4e-113">Als u bijvoorbeeld de Authenticode-hand tekening wilt ophalen voor het SqlScript.ps1 bestand, typt u:</span><span class="sxs-lookup"><span data-stu-id="85c4e-113">For example, to get the Authenticode signature for the SqlScript.ps1 file, type:</span></span>

```powershell
Get-AuthenticodeSignature SqlScript.ps1
```

<span data-ttu-id="85c4e-114">Of typ:</span><span class="sxs-lookup"><span data-stu-id="85c4e-114">Or, type:</span></span>

```powershell
gas SqlScript.ps1
```

<span data-ttu-id="85c4e-115">Als u ' Word ' maakt als alias voor Microsoft Office woord, typt u ' woord ' in plaats van het volgende:</span><span class="sxs-lookup"><span data-stu-id="85c4e-115">If you create "word" as the alias for Microsoft Office Word, you can type "word" instead of the following:</span></span>

```powershell
"C:\Program Files\Microsoft Office\Office11\Winword.exe"
```

## <a name="built-in-aliases"></a><span data-ttu-id="85c4e-116">INGEBOUWDE ALIASSEN</span><span class="sxs-lookup"><span data-stu-id="85c4e-116">BUILT-IN ALIASES</span></span>

<span data-ttu-id="85c4e-117">Power shell bevat een reeks ingebouwde aliassen, waaronder "CD" en "chdir" voor de Set-Location cmdlet en "ls" en "dir" voor de Get-ChildItem-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="85c4e-117">PowerShell includes a set of built-in aliases, including "cd" and "chdir" for the Set-Location cmdlet, and "ls" and "dir" for the Get-ChildItem cmdlet.</span></span>

<span data-ttu-id="85c4e-118">Als u alle aliassen op de computer wilt ophalen, inclusief de ingebouwde aliassen, typt u:</span><span class="sxs-lookup"><span data-stu-id="85c4e-118">To get all the aliases on the computer, including the built-in aliases, type:</span></span>

```powershell
Get-Alias
```

## <a name="alias-cmdlets"></a><span data-ttu-id="85c4e-119">ALIAS-CMDLETS</span><span class="sxs-lookup"><span data-stu-id="85c4e-119">ALIAS CMDLETS</span></span>

<span data-ttu-id="85c4e-120">Power shell bevat de volgende cmdlets, die zijn ontworpen voor het werken met aliassen:</span><span class="sxs-lookup"><span data-stu-id="85c4e-120">PowerShell includes the following cmdlets, which are designed for working with aliases:</span></span>

- <span data-ttu-id="85c4e-121">`Get-Alias` -Haalt alle aliassen in de huidige sessie op.</span><span class="sxs-lookup"><span data-stu-id="85c4e-121">`Get-Alias` - Gets all the aliases in the current session.</span></span>
- <span data-ttu-id="85c4e-122">`New-Alias` -Maakt een nieuwe alias.</span><span class="sxs-lookup"><span data-stu-id="85c4e-122">`New-Alias` - Creates a new alias.</span></span>
- <span data-ttu-id="85c4e-123">`Set-Alias` -Maakt of wijzigt een alias.</span><span class="sxs-lookup"><span data-stu-id="85c4e-123">`Set-Alias` - Creates or changes an alias.</span></span>
- <span data-ttu-id="85c4e-124">`Export-Alias` -Exporteert een of meer aliassen naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="85c4e-124">`Export-Alias` - Exports one or more aliases to a file.</span></span>
- <span data-ttu-id="85c4e-125">`Import-Alias` -Hiermee wordt een alias bestand in Power shell geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="85c4e-125">`Import-Alias` - Imports an alias file into PowerShell.</span></span>

<span data-ttu-id="85c4e-126">Voor gedetailleerde informatie over de cmdlets typt u:</span><span class="sxs-lookup"><span data-stu-id="85c4e-126">For detailed information about the cmdlets, type:</span></span>

```powershell
Get-Help <cmdlet-Name> -Detailed
```

<span data-ttu-id="85c4e-127">Typ bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="85c4e-127">For example, type:</span></span>

```powershell
Get-Help Export-Alias -Detailed
```

## <a name="creating-an-alias"></a><span data-ttu-id="85c4e-128">EEN ALIAS MAKEN</span><span class="sxs-lookup"><span data-stu-id="85c4e-128">CREATING AN ALIAS</span></span>

<span data-ttu-id="85c4e-129">Als u een nieuwe alias wilt maken, gebruikt u de cmdlet New-Alias.</span><span class="sxs-lookup"><span data-stu-id="85c4e-129">To create a new alias, use the New-Alias cmdlet.</span></span> <span data-ttu-id="85c4e-130">Als u bijvoorbeeld de alias "GH" wilt maken voor Get-Help, typt u:</span><span class="sxs-lookup"><span data-stu-id="85c4e-130">For example, to create the "gh" alias for Get-Help, type:</span></span>

```powershell
New-Alias -Name gh -Value Get-Help
```

<span data-ttu-id="85c4e-131">U kunt de alias gebruiken in opdrachten, net zoals u de volledige naam van de cmdlet gebruikt, en u kunt de alias gebruiken met para meters.</span><span class="sxs-lookup"><span data-stu-id="85c4e-131">You can use the alias in commands, just as you would use the full cmdlet name, and you can use the alias with parameters.</span></span>

<span data-ttu-id="85c4e-132">Als u bijvoorbeeld gedetailleerde Help-informatie voor de cmdlet Get-WmiObject wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="85c4e-132">For example, to get detailed Help for the Get-WmiObject cmdlet, type:</span></span>

```powershell
Get-Help Get-WmiObject -Detailed
```

<span data-ttu-id="85c4e-133">Of typ:</span><span class="sxs-lookup"><span data-stu-id="85c4e-133">Or, type:</span></span>

```powershell
gh Get-WmiObject -Detailed
```

## <a name="saving-aliases"></a><span data-ttu-id="85c4e-134">ALIASSEN OPSLAAN</span><span class="sxs-lookup"><span data-stu-id="85c4e-134">SAVING ALIASES</span></span>

<span data-ttu-id="85c4e-135">De aliassen die u maakt, worden alleen in de huidige sessie opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="85c4e-135">The aliases that you create are saved only in the current session.</span></span> <span data-ttu-id="85c4e-136">Als u de aliassen in een andere sessie wilt gebruiken, voegt u de alias toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="85c4e-136">To use the aliases in a different session, add the alias to your PowerShell profile.</span></span> <span data-ttu-id="85c4e-137">Of gebruik de Export-Alias cmdlet om de aliassen op te slaan in een bestand.</span><span class="sxs-lookup"><span data-stu-id="85c4e-137">Or, use the Export-Alias cmdlet to save the aliases to a file.</span></span>

<span data-ttu-id="85c4e-138">Typ voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="85c4e-138">For more information, type:</span></span>

```powershell
Get-Help about_Profiles
```

## <a name="getting-aliases"></a><span data-ttu-id="85c4e-139">ALIASSEN OPHALEN</span><span class="sxs-lookup"><span data-stu-id="85c4e-139">GETTING ALIASES</span></span>

<span data-ttu-id="85c4e-140">Als u alle aliassen in de huidige sessie wilt ophalen, met inbegrip van de ingebouwde aliassen, de aliassen in uw Power shell-profielen en de aliassen die u hebt gemaakt in de huidige sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="85c4e-140">To get all the aliases in the current session, including the built-in aliases, the aliases in your PowerShell profiles, and the aliases that you have created in the current session, type:</span></span>

```powershell
Get-Alias
```

<span data-ttu-id="85c4e-141">Als u bepaalde aliassen wilt ophalen, gebruikt u de para meter name van de cmdlet Get-Alias.</span><span class="sxs-lookup"><span data-stu-id="85c4e-141">To get particular aliases, use the Name parameter of the Get-Alias cmdlet.</span></span> <span data-ttu-id="85c4e-142">Als u bijvoorbeeld aliassen wilt ophalen die beginnen met ' p ', typt u:</span><span class="sxs-lookup"><span data-stu-id="85c4e-142">For example, to get aliases that begin with "p", type:</span></span>

```powershell
Get-Alias -Name p*
```

<span data-ttu-id="85c4e-143">Als u de aliassen voor een bepaald item wilt ophalen, gebruikt u de para meter definitie.</span><span class="sxs-lookup"><span data-stu-id="85c4e-143">To get the aliases for a particular item, use the Definition parameter.</span></span> <span data-ttu-id="85c4e-144">Als u bijvoorbeeld de aliassen voor het Get-ChildItem-cmdlet-type wilt ophalen:</span><span class="sxs-lookup"><span data-stu-id="85c4e-144">For example, to get the aliases for the Get-ChildItem cmdlet type:</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

### <a name="get-alias-output"></a><span data-ttu-id="85c4e-145">GET-ALIAS UITVOER</span><span class="sxs-lookup"><span data-stu-id="85c4e-145">GET-ALIAS OUTPUT</span></span>

<span data-ttu-id="85c4e-146">Get-Alias retourneert slechts één type object, een AliasInfo-object (System. Management. Automation. AliasInfo).</span><span class="sxs-lookup"><span data-stu-id="85c4e-146">Get-Alias returns only one type of object, an AliasInfo object (System.Management.Automation.AliasInfo).</span></span> <span data-ttu-id="85c4e-147">De naam van aliassen die geen afbreek streepje bevatten, zoals ' cd ' wordt weer gegeven in de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="85c4e-147">The name of aliases that don't include a hyphen, such as "cd" are displayed in the following format:</span></span>

```powershell
Get-Alias ac
```

```Output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Alias           ac -> Add-Content
```

<span data-ttu-id="85c4e-148">Zo kunt u snel en eenvoudig de benodigde informatie ophalen.</span><span class="sxs-lookup"><span data-stu-id="85c4e-148">This makes it very quick and easy to get the information that you need.</span></span>

<span data-ttu-id="85c4e-149">De op de pijl gebaseerde alias naam indeling wordt niet gebruikt voor aliassen die een koppel teken bevatten.</span><span class="sxs-lookup"><span data-stu-id="85c4e-149">The arrow-based alias name format is not used for aliases that include a hyphen.</span></span> <span data-ttu-id="85c4e-150">Dit zijn waarschijnlijk vervangende namen voor cmdlets en functies, in plaats van gebruikelijke afkortingen of bijnamen, en de auteur wil er mogelijk niet van zijn.</span><span class="sxs-lookup"><span data-stu-id="85c4e-150">These are likely to be preferred substitute names for cmdlets and functions, instead of typical abbreviations or nicknames, and the author might not want them to be as evident.</span></span>

## <a name="alternate-names-for-commands-with-parameters"></a><span data-ttu-id="85c4e-151">ALTERNATIEVE NAMEN VOOR OPDRACHTEN MET PARA METERS</span><span class="sxs-lookup"><span data-stu-id="85c4e-151">ALTERNATE NAMES FOR COMMANDS WITH PARAMETERS</span></span>

<span data-ttu-id="85c4e-152">U kunt een alias toewijzen aan een cmdlet, een script, een functie of een uitvoerbaar bestand.</span><span class="sxs-lookup"><span data-stu-id="85c4e-152">You can assign an alias to a cmdlet, script, function, or executable file.</span></span> <span data-ttu-id="85c4e-153">U kunt een alias niet toewijzen aan een opdracht en de bijbehorende para meters.</span><span class="sxs-lookup"><span data-stu-id="85c4e-153">You cannot assign an alias to a command and its parameters.</span></span> <span data-ttu-id="85c4e-154">U kunt bijvoorbeeld een alias toewijzen aan de `Get-Eventlog` cmdlet, maar u kunt geen alias toewijzen aan de `Get-Eventlog -LogName System` opdracht.</span><span class="sxs-lookup"><span data-stu-id="85c4e-154">For example, you can assign an alias to the `Get-Eventlog` cmdlet, but you cannot assign an alias to the `Get-Eventlog -LogName System` command.</span></span>

<span data-ttu-id="85c4e-155">U kunt een functie maken die de opdracht bevat.</span><span class="sxs-lookup"><span data-stu-id="85c4e-155">You can create a function that includes the command.</span></span> <span data-ttu-id="85c4e-156">Als u een functie wilt maken, typt u het woord ' function ' gevolgd door een naam voor de functie.</span><span class="sxs-lookup"><span data-stu-id="85c4e-156">To create a function, type the word "function" followed by a name for the function.</span></span> <span data-ttu-id="85c4e-157">Typ de opdracht en plaats deze tussen accolades ( {} ).</span><span class="sxs-lookup"><span data-stu-id="85c4e-157">Type the command, and enclose it in braces ({}).</span></span>

<span data-ttu-id="85c4e-158">Met de volgende opdracht maakt u bijvoorbeeld de functie syslog.</span><span class="sxs-lookup"><span data-stu-id="85c4e-158">For example, the following command creates the syslog function.</span></span> <span data-ttu-id="85c4e-159">Deze functie vertegenwoordigt de `Get-Eventlog -LogName System` opdracht:</span><span class="sxs-lookup"><span data-stu-id="85c4e-159">This function represents the `Get-Eventlog -LogName System` command:</span></span>

```powershell
function Get-SystemEventlog {Get-Eventlog -LogName System}
Set-Alias -Name syslog -Value Get-SystemEventlog
```

<span data-ttu-id="85c4e-160">U kunt nu ' syslog ' typen in plaats van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="85c4e-160">You can now type "syslog" instead of the command.</span></span> <span data-ttu-id="85c4e-161">En u kunt aliassen maken voor de nieuwe functie.</span><span class="sxs-lookup"><span data-stu-id="85c4e-161">And, you can create aliases for the new function.</span></span>

<span data-ttu-id="85c4e-162">Typ voor meer informatie over functies:</span><span class="sxs-lookup"><span data-stu-id="85c4e-162">For more information about functions, type:</span></span>

```powershell
Get-Help about_Functions
```

## <a name="alias-objects"></a><span data-ttu-id="85c4e-163">ALIAS OBJECTEN</span><span class="sxs-lookup"><span data-stu-id="85c4e-163">ALIAS OBJECTS</span></span>

<span data-ttu-id="85c4e-164">Power shell-aliassen worden vertegenwoordigd door objecten die exemplaren zijn van de klasse System. Management. Automation. AliasInfo.</span><span class="sxs-lookup"><span data-stu-id="85c4e-164">PowerShell aliases are represented by objects that are instances of the System.Management.Automation.AliasInfo class.</span></span> <span data-ttu-id="85c4e-165">Zie [AliasInfo-klasse][aliasinfo] in de Power shell-SDK voor meer informatie over dit type object.</span><span class="sxs-lookup"><span data-stu-id="85c4e-165">For more information about this type of object, see [AliasInfo Class][aliasinfo] in the PowerShell SDK.</span></span>

<span data-ttu-id="85c4e-166">Als u de eigenschappen en methoden van de alias objecten wilt bekijken, moet u de aliassen ophalen.</span><span class="sxs-lookup"><span data-stu-id="85c4e-166">To view the properties and methods of the alias objects, get the aliases.</span></span>
<span data-ttu-id="85c4e-167">Vervolgens kunt u ze naar de Get-Member-cmdlet sluizen.</span><span class="sxs-lookup"><span data-stu-id="85c4e-167">Then, pipe them to the Get-Member cmdlet.</span></span> <span data-ttu-id="85c4e-168">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="85c4e-168">For example:</span></span>

```powershell
Get-Alias | Get-Member
```

<span data-ttu-id="85c4e-169">Als u de waarden van de eigenschappen van een specifieke alias, zoals de alias, wilt weer geven, moet u `dir` de alias ophalen.</span><span class="sxs-lookup"><span data-stu-id="85c4e-169">To view the values of the properties of a specific alias, such as the `dir` alias, get the alias.</span></span> <span data-ttu-id="85c4e-170">Vervolgens pipet u het naar de cmdlet Format-List.</span><span class="sxs-lookup"><span data-stu-id="85c4e-170">Then, pipe it to the Format-List cmdlet.</span></span> <span data-ttu-id="85c4e-171">Met de volgende opdracht wordt bijvoorbeeld de alias ' dir ' opgehaald.</span><span class="sxs-lookup"><span data-stu-id="85c4e-171">For example, the following command gets the "dir" alias.</span></span> <span data-ttu-id="85c4e-172">Vervolgens wordt de alias door de opdracht sluizen naar de cmdlet Format-List.</span><span class="sxs-lookup"><span data-stu-id="85c4e-172">Next, the command pipes the alias to the Format-List cmdlet.</span></span> <span data-ttu-id="85c4e-173">Vervolgens gebruikt de opdracht de eigenschaps parameter van Format-List met een Joker teken ( \* ) om alle eigenschappen van de alias weer te geven `dir` .</span><span class="sxs-lookup"><span data-stu-id="85c4e-173">Then, the command uses the Property parameter of Format-List with a wildcard character (\*) to display all the properties of the `dir` alias.</span></span> <span data-ttu-id="85c4e-174">De volgende opdracht voert deze taken uit:</span><span class="sxs-lookup"><span data-stu-id="85c4e-174">The following command performs these tasks:</span></span>

```powershell
Get-Alias -Name dir | Format-List -Property *
```

## <a name="powershell-alias-provider"></a><span data-ttu-id="85c4e-175">Power shell-ALIAS PROVIDER</span><span class="sxs-lookup"><span data-stu-id="85c4e-175">PowerShell ALIAS PROVIDER</span></span>

<span data-ttu-id="85c4e-176">Power shell bevat de alias provider.</span><span class="sxs-lookup"><span data-stu-id="85c4e-176">PowerShell includes the Alias provider.</span></span> <span data-ttu-id="85c4e-177">Met de alias provider kunt u de aliassen in Power shell bekijken alsof ze zich op een bestandssysteem station bevonden.</span><span class="sxs-lookup"><span data-stu-id="85c4e-177">The Alias provider lets you view the aliases in PowerShell as though they were on a file system drive.</span></span>

<span data-ttu-id="85c4e-178">De alias provider toont de alias: station.</span><span class="sxs-lookup"><span data-stu-id="85c4e-178">The Alias provider exposes the Alias: drive.</span></span> <span data-ttu-id="85c4e-179">Ga naar de alias: station, type:</span><span class="sxs-lookup"><span data-stu-id="85c4e-179">To go into the Alias: drive, type:</span></span>

```powershell
Set-Location Alias:
```

<span data-ttu-id="85c4e-180">Als u de inhoud van het station wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="85c4e-180">To view the contents of the drive, type:</span></span>

```powershell
Get-ChildItem
```

<span data-ttu-id="85c4e-181">Als u de inhoud van het station van een ander Power Shell-station wilt weer geven, start u het pad met de naam van het station.</span><span class="sxs-lookup"><span data-stu-id="85c4e-181">To view the contents of the drive from another PowerShell drive, begin the path with the drive name.</span></span> <span data-ttu-id="85c4e-182">Neem de dubbele punt (:).</span><span class="sxs-lookup"><span data-stu-id="85c4e-182">Include the colon (:).</span></span> <span data-ttu-id="85c4e-183">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="85c4e-183">For example:</span></span>

```powershell
Get-ChildItem -Path Alias:
```

<span data-ttu-id="85c4e-184">Als u informatie wilt ophalen over een bepaalde alias, typt u de naam van het station en de naam van de alias.</span><span class="sxs-lookup"><span data-stu-id="85c4e-184">To get information about a particular alias, type the drive name and the alias name.</span></span> <span data-ttu-id="85c4e-185">Of typ een naam patroon.</span><span class="sxs-lookup"><span data-stu-id="85c4e-185">Or, type a name pattern.</span></span> <span data-ttu-id="85c4e-186">Als u bijvoorbeeld alle aliassen wilt ophalen die beginnen met ' p ', typt u:</span><span class="sxs-lookup"><span data-stu-id="85c4e-186">For example, to get all the aliases that begin with "p", type:</span></span>

```powershell
Get-ChildItem -Path Alias:p*
```

<span data-ttu-id="85c4e-187">Voor meer informatie over de Power shell-alias provider typt u:</span><span class="sxs-lookup"><span data-stu-id="85c4e-187">For more information about the PowerShell Alias provider, type:</span></span>

```powershell
Get-Help Alias
```

## <a name="see-also"></a><span data-ttu-id="85c4e-188">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="85c4e-188">SEE ALSO</span></span>

- [<span data-ttu-id="85c4e-189">Nieuwe alias</span><span class="sxs-lookup"><span data-stu-id="85c4e-189">New-Alias</span></span>](xref:Microsoft.PowerShell.Utility.New-Alias)
- [<span data-ttu-id="85c4e-190">Get-alias</span><span class="sxs-lookup"><span data-stu-id="85c4e-190">Get-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [<span data-ttu-id="85c4e-191">Set-alias</span><span class="sxs-lookup"><span data-stu-id="85c4e-191">Set-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Set-Alias)
- [<span data-ttu-id="85c4e-192">Exporteren-alias</span><span class="sxs-lookup"><span data-stu-id="85c4e-192">Export-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [<span data-ttu-id="85c4e-193">Import-alias</span><span class="sxs-lookup"><span data-stu-id="85c4e-193">Import-Alias</span></span>](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [<span data-ttu-id="85c4e-194">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="85c4e-194">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)
- [<span data-ttu-id="85c4e-195">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="85c4e-195">Get-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [<span data-ttu-id="85c4e-196">about_functions</span><span class="sxs-lookup"><span data-stu-id="85c4e-196">about_functions</span></span>](about_functions.md)
- [<span data-ttu-id="85c4e-197">about_profiles</span><span class="sxs-lookup"><span data-stu-id="85c4e-197">about_profiles</span></span>](about_profiles.md)
- [<span data-ttu-id="85c4e-198">about_providers</span><span class="sxs-lookup"><span data-stu-id="85c4e-198">about_providers</span></span>](about_providers.md)

<!-- External links -->
[aliasinfo]: /dotnet/api/system.management.automation.aliasinfo
