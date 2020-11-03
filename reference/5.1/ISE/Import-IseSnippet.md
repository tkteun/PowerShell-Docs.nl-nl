---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/import-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-IseSnippet
ms.openlocfilehash: 810be675fc593f665ccc6f3d5b86ac2f6b633863
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250047"
---
# <span data-ttu-id="7c081-103">Import-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="7c081-103">Import-IseSnippet</span></span>

## <span data-ttu-id="7c081-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7c081-104">SYNOPSIS</span></span>
<span data-ttu-id="7c081-105">Hiermee worden ISE-fragmenten in de huidige sessie geïmporteerd</span><span class="sxs-lookup"><span data-stu-id="7c081-105">Imports ISE snippets into the current session</span></span>

## <span data-ttu-id="7c081-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7c081-106">SYNTAX</span></span>

### <span data-ttu-id="7c081-107">FromFolder (standaard)</span><span class="sxs-lookup"><span data-stu-id="7c081-107">FromFolder (Default)</span></span>

```
Import-IseSnippet [-Path] <String> [-Recurse] [<CommonParameters>]
```

### <span data-ttu-id="7c081-108">FromModule</span><span class="sxs-lookup"><span data-stu-id="7c081-108">FromModule</span></span>

```
Import-IseSnippet [-Recurse] -Module <String> [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="7c081-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7c081-109">DESCRIPTION</span></span>

<span data-ttu-id="7c081-110">`Import-IseSnippet`Met de cmdlet worden Herbruikbare tekst fragmenten uit een module of een map in de huidige sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="7c081-110">The `Import-IseSnippet` cmdlet imports reusable text "snippets" from a module or a directory into the current session.</span></span> <span data-ttu-id="7c081-111">De fragmenten zijn direct beschikbaar voor gebruik in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="7c081-111">The snippets are immediately available for use in Windows PowerShell ISE.</span></span> <span data-ttu-id="7c081-112">Deze cmdlet werkt alleen in Windows Power shell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="7c081-112">This cmdlet works only in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

<span data-ttu-id="7c081-113">Als u de geïmporteerde fragmenten wilt bekijken en gebruiken, klikt u in het menu Windows PowerShell ISE **bewerken** op **fragmenten starten** of drukt u op <kbd>CTRL</kbd> + <kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="7c081-113">To view and use the imported snippets, from the Windows PowerShell ISE **Edit** menu, click **Start Snippets** or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

<span data-ttu-id="7c081-114">Geïmporteerde fragmenten zijn alleen beschikbaar in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="7c081-114">Imported snippets are available only in the current session.</span></span> <span data-ttu-id="7c081-115">Als u de fragmenten wilt importeren in alle Windows PowerShell ISE sessies, voegt `Import-IseSnippet` u een opdracht toe aan uw Windows Power shell-profiel of kopieert u de fragment bestanden naar uw lokale map met fragmenten `$home\Documents\WindowsPowershell\Snippets` .</span><span class="sxs-lookup"><span data-stu-id="7c081-115">To import the snippets into all Windows PowerShell ISE sessions, add an `Import-IseSnippet` command to your Windows PowerShell profile or copy the snippet files to your local snippets directory `$home\Documents\WindowsPowershell\Snippets`.</span></span>

<span data-ttu-id="7c081-116">Als u fragmenten wilt importeren, moeten ze juist zijn ingedeeld in het XML-code fragment voor Windows PowerShell ISE fragmenten en worden opgeslagen in Snippet.ps1XML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="7c081-116">To import snippets, they must be properly formatted in the snippet XML for Windows PowerShell ISE snippets and saved in Snippet.ps1xml files.</span></span> <span data-ttu-id="7c081-117">Als u in aanmerking komende fragmenten wilt maken, gebruikt u de `New-IseSnippet` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c081-117">To create eligible snippets, use the `New-IseSnippet` cmdlet.</span></span> <span data-ttu-id="7c081-118">`New-IseSnippet` Hiermee maakt u een `<SnippetTitle>.Snippets.ps1xml` bestand in de `$home\Documents\WindowsPowerShell\Snippets` map.</span><span class="sxs-lookup"><span data-stu-id="7c081-118">`New-IseSnippet` creates a `<SnippetTitle>.Snippets.ps1xml` file in the `$home\Documents\WindowsPowerShell\Snippets` directory.</span></span> <span data-ttu-id="7c081-119">U kunt de fragmenten verplaatsen of kopiëren naar de map fragmenten van een Windows Power shell-module of naar een andere map.</span><span class="sxs-lookup"><span data-stu-id="7c081-119">You can move or copy the snippets to the Snippets directory of a Windows PowerShell module, or to any other directory.</span></span>

<span data-ttu-id="7c081-120">`Get-IseSnippet`Met de cmdlet, waarmee door de gebruiker gemaakte fragmenten worden opgehaald in de map lokale fragmenten, worden geen geïmporteerde fragmenten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7c081-120">The `Get-IseSnippet` cmdlet, which gets user-created snippets in the local snippets directory, does not get imported snippets.</span></span>

<span data-ttu-id="7c081-121">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="7c081-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="7c081-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7c081-122">EXAMPLES</span></span>

### <span data-ttu-id="7c081-123">Voor beeld 1: fragmenten uit een Directory importeren</span><span class="sxs-lookup"><span data-stu-id="7c081-123">Example 1: Import snippets from a directory</span></span>

<span data-ttu-id="7c081-124">In dit voor beeld worden de fragmenten uit de `\\Server01\Public\Snippets` map in de huidige sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="7c081-124">This example imports the snippets from the `\\Server01\Public\Snippets` directory into the current session.</span></span> <span data-ttu-id="7c081-125">De **recursieve** para meter wordt gebruikt voor het ophalen van fragmenten uit alle submappen van de map fragmenten.</span><span class="sxs-lookup"><span data-stu-id="7c081-125">It uses the **Recurse** parameter to get snippets from all subdirectories of the Snippets directory.</span></span>

```powershell
Import-IseSnippet -Path \\Server01\Public\Snippets -Recurse
```

### <span data-ttu-id="7c081-126">Voor beeld 2: fragmenten uit een module importeren</span><span class="sxs-lookup"><span data-stu-id="7c081-126">Example 2: Import snippets from a module</span></span>

<span data-ttu-id="7c081-127">In dit voor beeld worden de fragmenten uit de **SnippetModule** -module geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="7c081-127">This example imports the snippets from the **SnippetModule** module.</span></span> <span data-ttu-id="7c081-128">De opdracht gebruikt de para meter **ListAvailable** om de fragmenten te importeren, zelfs als de module **SnippetModule** niet is geïmporteerd in de sessie van de gebruiker wanneer de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7c081-128">The command uses the **ListAvailable** parameter to import the snippets even if the **SnippetModule** module is not imported into the user's session when the command runs.</span></span>

```powershell
Import-IseSnippet -Module SnippetModule -ListAvailable
```

### <span data-ttu-id="7c081-129">Voor beeld 3: fragmenten in modules zoeken</span><span class="sxs-lookup"><span data-stu-id="7c081-129">Example 3: Find snippets in modules</span></span>

<span data-ttu-id="7c081-130">In dit voor beeld worden fragmenten in alle geïnstalleerde modules in de omgevings variabele PSModulePath opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7c081-130">This example gets snippets in all installed modules in the PSModulePath environment variable.</span></span>

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$_.fullname}
```

### <span data-ttu-id="7c081-131">Voor beeld 4: alle module fragmenten importeren</span><span class="sxs-lookup"><span data-stu-id="7c081-131">Example 4: Import all module snippets</span></span>

<span data-ttu-id="7c081-132">In dit voor beeld worden alle fragmenten van alle geïnstalleerde modules in de huidige sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="7c081-132">This example imports all snippets from all installed modules into the current session.</span></span> <span data-ttu-id="7c081-133">Normaal gesp roken hoeft u geen opdracht als volgt uit te voeren, omdat modules met fragmenten de cmdlet gebruiken `Import-IseSnippet` om ze te importeren wanneer de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="7c081-133">Typically, you don't need to run a command like this because modules that have snippets will use the `Import-IseSnippet` cmdlet to import them for you when the module is imported.</span></span>

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$psise.CurrentPowerShellTab.Snippets.Load($_)}
```

### <span data-ttu-id="7c081-134">Voor beeld 5: alle module fragmenten kopiëren</span><span class="sxs-lookup"><span data-stu-id="7c081-134">Example 5: Copy all module snippets</span></span>

<span data-ttu-id="7c081-135">In dit voor beeld worden de fragment bestanden van alle geïnstalleerde modules gekopieerd naar de map fragmenten van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="7c081-135">This example copies the snippet files from all installed modules into the Snippets directory of the current user.</span></span> <span data-ttu-id="7c081-136">In tegens telling tot geïmporteerde fragmenten die alleen van invloed zijn op de huidige sessie, zijn gekopieerde fragmenten beschikbaar in elke Windows PowerShell ISE sessie.</span><span class="sxs-lookup"><span data-stu-id="7c081-136">Unlike imported snippets, which affect only the current session, copied snippets are available in every Windows PowerShell ISE session.</span></span>

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    Copy-Item -Destination $home\Documents\WindowsPowerShell\Snippets
```

## <span data-ttu-id="7c081-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7c081-137">PARAMETERS</span></span>

### <span data-ttu-id="7c081-138">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="7c081-138">-ListAvailable</span></span>

<span data-ttu-id="7c081-139">Hiermee wordt aangegeven dat met deze cmdlet fragmenten worden opgehaald uit modules die zijn geïnstalleerd op de computer, zelfs als de modules niet in de huidige sessie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="7c081-139">Indicates that this cmdlet gets snippets from modules that are installed on the computer, even if the modules are not imported into the current session.</span></span> <span data-ttu-id="7c081-140">Als deze para meter wordt wegge laten en de module die is opgegeven door de **module** para meter, niet in de huidige sessie wordt geïmporteerd, mislukt de poging om de fragmenten uit de module op te halen.</span><span class="sxs-lookup"><span data-stu-id="7c081-140">If this parameter is omitted, and the module that is specified by the **Module** parameter is not imported into the current session, the attempt to get the snippets from the module fails.</span></span>

<span data-ttu-id="7c081-141">Deze para meter is alleen geldig wanneer de **module** parameter in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7c081-141">This parameter is valid only when the **Module** parameter is used in the command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromModule
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c081-142">-Module</span><span class="sxs-lookup"><span data-stu-id="7c081-142">-Module</span></span>

<span data-ttu-id="7c081-143">Hiermee worden fragmenten uit de opgegeven module geïmporteerd in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="7c081-143">Imports snippets from the specified module into the current session.</span></span> <span data-ttu-id="7c081-144">Joker tekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7c081-144">Wildcard characters are not supported.</span></span>

<span data-ttu-id="7c081-145">Met deze para meter worden fragmenten geïmporteerd uit Snippet.ps1XML-bestanden in de submap fragmenten in het pad van de module, zoals `$home\Documents\WindowsPowerShell\Modules\<ModuleName>\Snippets` .</span><span class="sxs-lookup"><span data-stu-id="7c081-145">This parameter imports snippets from Snippet.ps1xml files in the Snippets subdirectory in the module path, such as `$home\Documents\WindowsPowerShell\Modules\<ModuleName>\Snippets`.</span></span>

<span data-ttu-id="7c081-146">Deze para meter is ontworpen om te worden gebruikt door module auteurs in een opstart script, zoals een script dat is opgegeven in de **ScriptsToProcess** -sleutel van een module manifest.</span><span class="sxs-lookup"><span data-stu-id="7c081-146">This parameter is designed to be used by module authors in a startup script, such as a script specified in the **ScriptsToProcess** key of a module manifest.</span></span> <span data-ttu-id="7c081-147">Fragmenten in een module worden niet automatisch met de module geïmporteerd, maar u kunt een opdracht gebruiken `Import-IseSnippet` om ze te importeren.</span><span class="sxs-lookup"><span data-stu-id="7c081-147">Snippets in a module are not automatically imported with the module, but you can use an `Import-IseSnippet` command to import them.</span></span>

```yaml
Type: System.String
Parameter Sets: FromModule
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c081-148">-Path</span><span class="sxs-lookup"><span data-stu-id="7c081-148">-Path</span></span>

<span data-ttu-id="7c081-149">Hiermee geeft u het pad op naar de map met fragmenten waarin met deze cmdlet fragmenten worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="7c081-149">Specifies the path to the snippets directory in which this cmdlet imports snippets.</span></span>

```yaml
Type: System.String
Parameter Sets: FromFolder
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="7c081-150">-Recursief</span><span class="sxs-lookup"><span data-stu-id="7c081-150">-Recurse</span></span>

<span data-ttu-id="7c081-151">Geeft aan dat met deze cmdlet fragmenten worden geïmporteerd uit alle submappen van de waarde van de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="7c081-151">Indicates that this cmdlet imports snippets from all subdirectories of the value of the **Path** parameter.</span></span>

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

### <span data-ttu-id="7c081-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7c081-152">CommonParameters</span></span>

<span data-ttu-id="7c081-153">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7c081-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7c081-154">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7c081-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7c081-155">INVOER</span><span class="sxs-lookup"><span data-stu-id="7c081-155">INPUTS</span></span>

### <span data-ttu-id="7c081-156">Geen</span><span class="sxs-lookup"><span data-stu-id="7c081-156">None</span></span>

<span data-ttu-id="7c081-157">Deze cmdlet neemt geen invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="7c081-157">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="7c081-158">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7c081-158">OUTPUTS</span></span>

### <span data-ttu-id="7c081-159">Geen</span><span class="sxs-lookup"><span data-stu-id="7c081-159">None</span></span>

<span data-ttu-id="7c081-160">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="7c081-160">This cmdlet does not generate output.</span></span>

## <span data-ttu-id="7c081-161">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7c081-161">NOTES</span></span>

- <span data-ttu-id="7c081-162">U kunt de cmdlet niet gebruiken `Get-IseSnippet` om geïmporteerde fragmenten op te halen.</span><span class="sxs-lookup"><span data-stu-id="7c081-162">You cannot use the `Get-IseSnippet` cmdlet to get imported snippets.</span></span> <span data-ttu-id="7c081-163">`Get-IseSnippet` haalt alleen fragmenten op in de `$home\Documents\WindowsPowerShell\Snippets` map.</span><span class="sxs-lookup"><span data-stu-id="7c081-163">`Get-IseSnippet` gets only snippets in the `$home\Documents\WindowsPowerShell\Snippets` directory.</span></span>
- <span data-ttu-id="7c081-164">`Import-IseSnippet` maakt gebruik van de statische methode **Load** van **micro soft. Power shell. host. ISE. ISESnippetCollection** -objecten.</span><span class="sxs-lookup"><span data-stu-id="7c081-164">`Import-IseSnippet` uses the **Load** static method of **Microsoft.PowerShell.Host.ISE.ISESnippetCollection** objects.</span></span> <span data-ttu-id="7c081-165">U kunt ook de methode voor het **laden** van fragmenten in het object model van Windows PowerShell ISE gebruiken: `$psISE.CurrentPowerShellTab.Snippets.Load()`</span><span class="sxs-lookup"><span data-stu-id="7c081-165">You can also use the **Load** method of snippets in the Windows PowerShell ISE object model: `$psISE.CurrentPowerShellTab.Snippets.Load()`</span></span>
- <span data-ttu-id="7c081-166">De `New-IseSnippet` cmdlet slaat nieuwe door de gebruiker gemaakte fragmenten op in niet-ondertekende. ps1xml-bestanden.</span><span class="sxs-lookup"><span data-stu-id="7c081-166">The `New-IseSnippet` cmdlet stores new user-created snippets in unsigned .ps1xml files.</span></span> <span data-ttu-id="7c081-167">Windows Power shell kan deze niet laden in een sessie waarin het uitvoerings beleid **Alles ondertekend** of **beperkt** is.</span><span class="sxs-lookup"><span data-stu-id="7c081-167">As such, Windows PowerShell cannot load them into a session in which the execution policy is **AllSigned** or **Restricted**.</span></span> <span data-ttu-id="7c081-168">In een **beperkte** of **Alles ondertekende** sessie kunt u niet-ondertekende door de gebruiker gemaakte fragmenten maken, ophalen en importeren, maar u kunt ze niet gebruiken in de sessie.</span><span class="sxs-lookup"><span data-stu-id="7c081-168">In a **Restricted** or **AllSigned** session, you can create, get, and import unsigned user-created snippets, but you cannot use them in the session.</span></span>

  <span data-ttu-id="7c081-169">Als u niet-ondertekende door de gebruiker gemaakte fragmenten wilt gebruiken die `Import-IseSnippet` door de cmdlet worden geretourneerd, wijzigt u het uitvoerings beleid en start u Windows PowerShell ISE opnieuw.</span><span class="sxs-lookup"><span data-stu-id="7c081-169">To use unsigned user-created snippets that the `Import-IseSnippet` cmdlet returns, change the execution policy, and then restart Windows PowerShell ISE.</span></span>

  <span data-ttu-id="7c081-170">Zie [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)voor meer informatie over het uitvoerings beleid van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="7c081-170">For more information about Windows PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="7c081-171">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7c081-171">RELATED LINKS</span></span>

[<span data-ttu-id="7c081-172">Get-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="7c081-172">Get-IseSnippet</span></span>](Get-IseSnippet.md)

[<span data-ttu-id="7c081-173">New-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="7c081-173">New-IseSnippet</span></span>](New-IseSnippet.md)
