---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-PSSession
ms.openlocfilehash: 334746589ed991ea817929eb31100f92c2dfda1f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705460"
---
# <span data-ttu-id="bd7a3-102">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="bd7a3-102">Export-PSSession</span></span>

## <span data-ttu-id="bd7a3-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="bd7a3-103">SYNOPSIS</span></span>

<span data-ttu-id="bd7a3-104">Exporteert opdrachten vanuit een andere sessie en slaat ze op in een Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-104">Exports commands from another session and saves them in a PowerShell module.</span></span>

## <span data-ttu-id="bd7a3-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="bd7a3-105">SYNTAX</span></span>

### <span data-ttu-id="bd7a3-106">Alles</span><span class="sxs-lookup"><span data-stu-id="bd7a3-106">All</span></span>

```
Export-PSSession [-OutputModule] <String> [-Force] [-Encoding <Encoding>]
 [[-CommandName] <String[]>] [-AllowClobber] [-ArgumentList <Object[]>]
 [-CommandType <CommandTypes>] [-Module <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-FormatTypeName] <String[]>] [-Certificate <X509Certificate2>] [-Session] <PSSession>
 [<CommonParameters>]
```

## <span data-ttu-id="bd7a3-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="bd7a3-107">DESCRIPTION</span></span>

<span data-ttu-id="bd7a3-108">De `Export-PSSession` cmdlet haalt cmdlets, functies, aliassen en andere opdracht typen van een andere Power shell-sessie (PSSession) op een lokale of externe computer op en slaat ze op in een Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-108">The `Export-PSSession` cmdlet gets cmdlets, functions, aliases, and other command types from another PowerShell session (PSSession) on a local or remote computer and saves them in a PowerShell module.</span></span> <span data-ttu-id="bd7a3-109">Gebruik de cmdlet om de opdrachten van de module toe te voegen aan de huidige sessie `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="bd7a3-109">To add the commands from the module to the current session, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="bd7a3-110">In tegens telling tot `Import-PSSession` , waarmee opdrachten vanuit een andere PSSession worden geïmporteerd in de huidige sessie, `Export-PSSession` worden de opdrachten in een module opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-110">Unlike `Import-PSSession`, which imports commands from another PSSession into the current session, `Export-PSSession` saves the commands in a module.</span></span> <span data-ttu-id="bd7a3-111">De opdrachten worden niet in de huidige sessie geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-111">The commands are not imported into the current session.</span></span>

<span data-ttu-id="bd7a3-112">Voor het exporteren van opdrachten gebruikt u de `New-PSSession` cmdlet om een PSSession te maken met de opdrachten die u wilt exporteren.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-112">To export commands, use the `New-PSSession` cmdlet to create a PSSession that has the commands that you want to export.</span></span> <span data-ttu-id="bd7a3-113">Gebruik vervolgens de `Export-PSSession` cmdlet om de opdrachten te exporteren.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-113">Then use the `Export-PSSession` cmdlet to export the commands.</span></span>

<span data-ttu-id="bd7a3-114">Om conflicten met opdracht namen te voor komen, is de standaard instelling voor het `Export-PSSession` exporteren van alle opdrachten, met uitzonde ring van opdrachten die voor komen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-114">To prevent command name conflicts, the default for `Export-PSSession` is to export all commands, except for commands that exist in the current session.</span></span> <span data-ttu-id="bd7a3-115">U kunt de para meter **opdrachtnaam** gebruiken om de opdrachten op te geven die moeten worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-115">You can use the **CommandName** parameter to specify the commands to export.</span></span>

<span data-ttu-id="bd7a3-116">De `Export-PSSession` cmdlet maakt gebruik van de impliciete externe functie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-116">The `Export-PSSession` cmdlet uses the implicit remoting feature of PowerShell.</span></span> <span data-ttu-id="bd7a3-117">Wanneer u opdrachten in de huidige sessie importeert, worden deze impliciet uitgevoerd in de oorspronkelijke sessie of in een vergelijk bare sessie op de oorspronkelijke computer.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-117">When you import commands into the current session, they run implicitly in the original session or in a similar session on the originating computer.</span></span>

## <span data-ttu-id="bd7a3-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="bd7a3-118">EXAMPLES</span></span>

### <span data-ttu-id="bd7a3-119">Voor beeld 1: opdrachten van een PSSession exporteren</span><span class="sxs-lookup"><span data-stu-id="bd7a3-119">Example 1: Export commands from a PSSession</span></span>

<span data-ttu-id="bd7a3-120">In dit voor beeld wordt een nieuwe PSSession van de lokale computer gemaakt op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-120">This example creates a new PSSession from the local computer to the Server01 computer.</span></span> <span data-ttu-id="bd7a3-121">Alle opdrachten, behalve die in de huidige sessie, worden geëxporteerd naar de module met de naam Server01 op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-121">All of the commands, except those that exist in the current session, are exported to the module named Server01 on the local computer.</span></span> <span data-ttu-id="bd7a3-122">De export bevat de opmaak gegevens voor de opdrachten.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-122">The export includes the formatting data for the commands.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01
Export-PSSession -Session $S -OutputModule Server01
```

<span data-ttu-id="bd7a3-123">`New-PSSession`Met de opdracht maakt u een PSSession op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-123">The `New-PSSession` command creates a PSSession on the Server01 computer.</span></span> <span data-ttu-id="bd7a3-124">De PSSession wordt opgeslagen in de `$S` variabele.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-124">The PSSession is stored in the `$S` variable.</span></span> <span data-ttu-id="bd7a3-125">De `Export-PSSession` opdracht exporteert de `$S` opdrachten van de variabele en formatteert gegevens in de Server01-module.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-125">The `Export-PSSession` command exports the `$S` variable's commands and formatting data into the Server01 module.</span></span>

### <span data-ttu-id="bd7a3-126">Voor beeld 2: de opdrachten Get en set exporteren</span><span class="sxs-lookup"><span data-stu-id="bd7a3-126">Example 2: Export the Get and Set commands</span></span>

<span data-ttu-id="bd7a3-127">In dit voor beeld worden alle- `Get` en- `Set` opdrachten van een server geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-127">This example exports all of the `Get` and `Set` commands from a server.</span></span>

```powershell
$S = New-PSSession -ConnectionUri https://exchange.microsoft.com/mailbox -Credential exchangeadmin01@hotmail.com -Authentication Negotiate
Export-PSSession -Session $S -Module exch* -CommandName Get-*, Set-* -FormatTypeName * -OutputModule $PSHOME\Modules\Exchange -Encoding ASCII
```

<span data-ttu-id="bd7a3-128">Met deze opdrachten exporteert `Get` `Set` u de opdrachten en van een micro soft Exchange Server-module op een externe computer naar een Exchange-module in de `$PSHOME\Modules` map op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-128">These commands export the `Get` and `Set` commands from a Microsoft Exchange Server snap-in on a remote computer to an Exchange module in the `$PSHOME\Modules` directory on the local computer.</span></span>
<span data-ttu-id="bd7a3-129">Als de module in de `$PSHOME\Modules` Directory wordt geplaatst, is deze toegankelijk voor alle gebruikers van de computer.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-129">Placing the module in the `$PSHOME\Modules` directory makes it accessible to all users of the computer.</span></span>

### <span data-ttu-id="bd7a3-130">Voor beeld 3: opdrachten van een externe computer exporteren</span><span class="sxs-lookup"><span data-stu-id="bd7a3-130">Example 3: Export commands from a remote computer</span></span>

<span data-ttu-id="bd7a3-131">In dit voor beeld worden de cmdlets van een PSSession op een externe computer geëxporteerd en opgeslagen in een module op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-131">This example exports cmdlets from a PSSession on a remote computer and saves them in a module on the local computer.</span></span> <span data-ttu-id="bd7a3-132">De cmdlets van de module worden toegevoegd aan de huidige sessie, zodat ze kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-132">The cmdlets from the module are added to the current session so that they can be used.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01 -Credential Server01\User01
Export-PSSession -Session $S -OutputModule TestCmdlets -Type Cmdlet -CommandName *test* -FormatTypeName *
Remove-PSSession $S
Import-Module TestCmdlets
Get-Help Test*
Test-Files
```

<span data-ttu-id="bd7a3-133">Met de `New-PSSession` opdracht maakt u een PSSession op de Server01-computer en slaat u deze op in de `$S` variabele.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-133">The `New-PSSession` command creates a PSSession on the Server01 computer and saves it in the `$S` variable.</span></span> <span data-ttu-id="bd7a3-134">De `Export-PSSession` opdracht exporteert de cmdlets waarvan de naam begint met testen van de PSSession in `$S` naar de TestCmdlets-module op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-134">The `Export-PSSession` command exports the cmdlets whose names begin with Test from the PSSession in `$S` to the TestCmdlets module on the local computer.</span></span>

<span data-ttu-id="bd7a3-135">De `Remove-PSSession` cmdlet verwijdert de PSSession `$S` uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-135">The `Remove-PSSession` cmdlet deletes the PSSession in `$S` from the current session.</span></span> <span data-ttu-id="bd7a3-136">Met deze opdracht wordt aangegeven dat de PSSession niet actief moet zijn om de opdrachten te gebruiken die uit de sessie zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-136">This command shows that the PSSession need not be active to use the commands that were imported from the session.</span></span> <span data-ttu-id="bd7a3-137">De `Import-Module` cmdlet voegt de cmdlets in de TestCmdlets-module toe aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-137">The `Import-Module` cmdlet adds the cmdlets in the TestCmdlets module to the current session.</span></span> <span data-ttu-id="bd7a3-138">De opdracht kan op elk gewenst moment in elke sessie worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-138">The command can be run in any session at any time.</span></span>

<span data-ttu-id="bd7a3-139">De `Get-Help` cmdlet krijgt Help-informatie voor cmdlets waarvan de naam begint met testen.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-139">The `Get-Help` cmdlet gets help for cmdlets whose names begin with Test.</span></span> <span data-ttu-id="bd7a3-140">Nadat de opdrachten in een module aan de huidige sessie zijn toegevoegd, kunt u de `Get-Help` `Get-Command` cmdlets en gebruiken om meer te weten te komen over de geïmporteerde opdrachten.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-140">After the commands in a module are added to the current session, you can use the `Get-Help` and `Get-Command` cmdlets to learn about the imported commands.</span></span> <span data-ttu-id="bd7a3-141">De `Test-Files` cmdlet is geëxporteerd van de Server01-computer en aan de sessie toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-141">The `Test-Files` cmdlet was exported from the Server01 computer and added to the session.</span></span> <span data-ttu-id="bd7a3-142">De `Test-Files` cmdlet wordt uitgevoerd in een externe sessie op de computer van waaruit de opdracht is geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-142">The `Test-Files` cmdlet runs in a remote session on the computer from which the command was imported.</span></span> <span data-ttu-id="bd7a3-143">Power Shell maakt een sessie van informatie die is opgeslagen in de TestCmdlets-module.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-143">PowerShell creates a session from information that is stored in the TestCmdlets module.</span></span>

### <span data-ttu-id="bd7a3-144">Voor beeld 4: opdrachten in de huidige sessie exporteren en Clobber</span><span class="sxs-lookup"><span data-stu-id="bd7a3-144">Example 4: Export and clobber commands in the current session</span></span>

<span data-ttu-id="bd7a3-145">In dit voor beeld worden opdrachten geëxporteerd die in een variabele zijn opgeslagen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-145">This example exports commands that are stored in a variable into the current session.</span></span>

```powershell
Export-PSSession -Session $S -AllowClobber -OutputModule AllCommands
```

<span data-ttu-id="bd7a3-146">Met deze `Export-PSSession` opdracht worden alle opdrachten en alle opmaak gegevens van de PSSession in de `$S` variabele geëxporteerd naar de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-146">This `Export-PSSession` command exports all commands and all formatting data from the PSSession in the `$S` variable into the current session.</span></span> <span data-ttu-id="bd7a3-147">De para meter **AllowClobber** bevat opdrachten met dezelfde namen als opdrachten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-147">The **AllowClobber** parameter includes commands with the same names as commands in the current session.</span></span>

### <span data-ttu-id="bd7a3-148">Voor beeld 5: opdrachten van een gesloten PSSession exporteren</span><span class="sxs-lookup"><span data-stu-id="bd7a3-148">Example 5: Export commands from a closed PSSession</span></span>

<span data-ttu-id="bd7a3-149">In dit voor beeld ziet u hoe u de geëxporteerde opdrachten uitvoert met speciale opties wanneer de PSSession die de geëxporteerde opdrachten heeft gemaakt, is gesloten.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-149">This example shows how to run the exported commands with special options when the PSSession that created the exported commands is closed.</span></span>

<span data-ttu-id="bd7a3-150">Als de oorspronkelijke externe sessie wordt gesloten wanneer een module wordt geïmporteerd, wordt in de module een open externe sessie gebruikt die verbinding maakt met de oorspronkelijke computer.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-150">If the original remote session is closed when a module is imported, the module will use any open remote session that connects to the originating computer.</span></span> <span data-ttu-id="bd7a3-151">Als er geen huidige sessie naar de oorspronkelijke computer is, wordt een sessie door de module opnieuw tot stand gebracht.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-151">If there is no current session to the originating computer, the module will reestablish a session.</span></span>

<span data-ttu-id="bd7a3-152">Als u geëxporteerde opdrachten met speciale opties wilt uitvoeren in een externe sessie, moet u een externe sessie met die opties maken voordat u de module importeert.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-152">To run exported commands with special options in a remote session, you must create a remote session with those options before you import the module.</span></span> <span data-ttu-id="bd7a3-153">De `New-PSSession` cmdlet gebruiken met de para meter **SessionOption**</span><span class="sxs-lookup"><span data-stu-id="bd7a3-153">Use the `New-PSSession` cmdlet with the **SessionOption** parameter</span></span>

```powershell
$Options = New-PSSessionOption -NoMachineProfile
$S = New-PSSession -ComputerName Server01 -SessionOption $Options
Export-PSSession -Session $S -OutputModule Server01
Remove-PSSession $S
New-PSSession -ComputerName Server01 -SessionOption $Options
Import-Module Server01
```

<span data-ttu-id="bd7a3-154">De `New-PSSessionOption` cmdlet maakt een **PSSessionOption** -object en slaat het object op in de `$Options` variabele.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-154">The `New-PSSessionOption` cmdlet creates a **PSSessionOption** object, and it saves the object in the `$Options` variable.</span></span> <span data-ttu-id="bd7a3-155">`New-PSSession`Met de opdracht maakt u een PSSession op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-155">The `New-PSSession` command creates a PSSession on the Server01 computer.</span></span>
<span data-ttu-id="bd7a3-156">De para meter **SessionOption** maakt gebruik van het object dat is opgeslagen in `$Options` .</span><span class="sxs-lookup"><span data-stu-id="bd7a3-156">The **SessionOption** parameter uses the object stored in `$Options`.</span></span> <span data-ttu-id="bd7a3-157">De sessie wordt opgeslagen in de `$S` variabele.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-157">The session is stored in the `$S` variable.</span></span>

<span data-ttu-id="bd7a3-158">De `Export-PSSession` cmdlet exporteert opdrachten van de PSSession in `$S` naar de Server01-module.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-158">The `Export-PSSession` cmdlet exports commands from the PSSession in `$S` to the Server01 module.</span></span>
<span data-ttu-id="bd7a3-159">De `Remove-PSSession` cmdlet verwijdert de PSSession in de `$S` variabele.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-159">The `Remove-PSSession` cmdlet deletes the PSSession in the `$S` variable.</span></span>

<span data-ttu-id="bd7a3-160">De `New-PSSession` cmdlet maakt een nieuwe PSSession die verbinding maakt met de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-160">The `New-PSSession` cmdlet creates a new PSSession that connects to the Server01 computer.</span></span> <span data-ttu-id="bd7a3-161">De para meter **SessionOption** maakt gebruik van het object dat is opgeslagen in `$Options` .</span><span class="sxs-lookup"><span data-stu-id="bd7a3-161">The **SessionOption** parameter uses the object stored in `$Options`.</span></span> <span data-ttu-id="bd7a3-162">`Import-Module`Met de cmdlet worden de opdrachten uit de Server01-module geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-162">The `Import-Module` cmdlet imports the commands from the Server01 module.</span></span> <span data-ttu-id="bd7a3-163">De opdrachten in de module worden uitgevoerd in de PSSession op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-163">The commands in the module are run in the PSSession on the Server01 computer.</span></span>

## <span data-ttu-id="bd7a3-164">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bd7a3-164">PARAMETERS</span></span>

### <span data-ttu-id="bd7a3-165">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="bd7a3-165">-AllowClobber</span></span>

<span data-ttu-id="bd7a3-166">Exporteert de opgegeven opdrachten, zelfs als ze dezelfde namen hebben als opdrachten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-166">Exports the specified commands, even if they have the same names as commands in the current session.</span></span>

<span data-ttu-id="bd7a3-167">Als u een opdracht exporteert met dezelfde naam als een opdracht in de huidige sessie, worden de oorspronkelijke opdrachten verborgen of vervangen door de geëxporteerde opdracht.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-167">If you export a command with the same name as a command in the current session, the exported command hides or replaces the original commands.</span></span> <span data-ttu-id="bd7a3-168">Zie [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-168">For more information, see [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md).</span></span>

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

### <span data-ttu-id="bd7a3-169">-Argument List</span><span class="sxs-lookup"><span data-stu-id="bd7a3-169">-ArgumentList</span></span>

<span data-ttu-id="bd7a3-170">Exporteert de variant van de opdracht die het resultaat is van het gebruik van de opgegeven argumenten (parameter waarden).</span><span class="sxs-lookup"><span data-stu-id="bd7a3-170">Exports the variant of the command that results from using the specified arguments (parameter values).</span></span>

<span data-ttu-id="bd7a3-171">Als u bijvoorbeeld de variant van de `Get-Item` opdracht in het certificaat (CERT:) wilt exporteren, in het PSSession-station in `$S` , typt u `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:` .</span><span class="sxs-lookup"><span data-stu-id="bd7a3-171">For example, to export the variant of the `Get-Item` command in the certificate (Cert:) drive in the PSSession in `$S`, type `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:`.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd7a3-172">-Certificaat</span><span class="sxs-lookup"><span data-stu-id="bd7a3-172">-Certificate</span></span>

<span data-ttu-id="bd7a3-173">Hiermee geeft u het client certificaat op dat wordt gebruikt voor het ondertekenen van de indelings bestanden (\* .Format.ps1XML) of script module bestanden (. psm1) in de module die `Export-PSSession` wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-173">Specifies the client certificate that is used to sign the format files (\*.Format.ps1xml) or script module files (.psm1) in the module that `Export-PSSession` creates.</span></span> <span data-ttu-id="bd7a3-174">Voer een variabele in die een certificaat of een opdracht of expressie bevat waarmee het certificaat wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-174">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="bd7a3-175">Als u een certificaat wilt zoeken, gebruikt u de `Get-PfxCertificate` cmdlet of gebruikt u de `Get-ChildItem` cmdlet in het certificaat (CERT:) stationsletter.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-175">To find a certificate, use the `Get-PfxCertificate` cmdlet or use the `Get-ChildItem` cmdlet in the Certificate (Cert:) drive.</span></span> <span data-ttu-id="bd7a3-176">Als het certificaat ongeldig is of niet voldoende autoriteit heeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-176">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd7a3-177">-Opdrachtnaam</span><span class="sxs-lookup"><span data-stu-id="bd7a3-177">-CommandName</span></span>

<span data-ttu-id="bd7a3-178">Exporteert alleen de opdrachten met de opgegeven namen of naam patronen.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-178">Exports only the commands with the specified names or name patterns.</span></span> <span data-ttu-id="bd7a3-179">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-179">Wildcards are permitted.</span></span> <span data-ttu-id="bd7a3-180">Gebruik de **naam** van de **opdracht** of de alias.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-180">Use **CommandName** or its alias, **Name**.</span></span>

<span data-ttu-id="bd7a3-181">`Export-PSSession`Exporteert standaard alle opdrachten van de PSSession, met uitzonde ring van opdrachten die dezelfde namen hebben als opdrachten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-181">By default, `Export-PSSession` exports all commands from the PSSession except for commands that have the same names as commands in the current session.</span></span> <span data-ttu-id="bd7a3-182">Zo voor komt u dat opdrachten worden verborgen of vervangen door opdrachten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-182">This prevents commands from being hidden or replaced by commands in the current session.</span></span> <span data-ttu-id="bd7a3-183">Gebruik de para meter **AllowClobber** om alle opdrachten te exporteren, zelfs wanneer deze andere opdrachten verbergen of vervangen.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-183">To export all commands, even those that hide or replace other commands, use the **AllowClobber** parameter.</span></span>

<span data-ttu-id="bd7a3-184">Als u de para meter **opdrachtnaam** gebruikt, worden de opmaak bestanden voor de opdrachten niet geëxporteerd, tenzij u de para meter **FormatTypeName** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-184">If you use the **CommandName** parameter, the formatting files for the commands are not exported unless you use the **FormatTypeName** parameter.</span></span> <span data-ttu-id="bd7a3-185">Ook als u de para meter **FormatTypeName** gebruikt, worden er geen opdrachten geëxporteerd, tenzij u de para meter **opdrachtnaam** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-185">Similarly, if you use the **FormatTypeName** parameter, no commands are exported unless you use the **CommandName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bd7a3-186">-CommandType</span><span class="sxs-lookup"><span data-stu-id="bd7a3-186">-CommandType</span></span>

<span data-ttu-id="bd7a3-187">Exporteert alleen de opgegeven typen opdracht objecten.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-187">Exports only the specified types of command objects.</span></span> <span data-ttu-id="bd7a3-188">Gebruik **CommandType** of de alias, **Typ**.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-188">Use **CommandType** or its alias, **Type**.</span></span>

<span data-ttu-id="bd7a3-189">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="bd7a3-189">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="bd7a3-190">Toe.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-190">Alias.</span></span> <span data-ttu-id="bd7a3-191">Alle Power shell-aliassen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-191">All PowerShell aliases in the current session.</span></span>
- <span data-ttu-id="bd7a3-192">Hele.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-192">All.</span></span> <span data-ttu-id="bd7a3-193">Alle opdracht typen.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-193">All command types.</span></span> <span data-ttu-id="bd7a3-194">Het is het equivalent van `Get-Command -Name *` .</span><span class="sxs-lookup"><span data-stu-id="bd7a3-194">It is the equivalent of `Get-Command -Name *`.</span></span>
- <span data-ttu-id="bd7a3-195">Modules.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-195">Application.</span></span> <span data-ttu-id="bd7a3-196">Alle bestanden met uitzonde ring van Power Shell-bestanden in paden die worden vermeld in de Path-omgevings variabele ( `$env:path` ), inclusief. txt,. exe en. dll-bestanden.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-196">All files other than PowerShell files in paths listed in the Path environment variable (`$env:path`), including .txt, .exe, and .dll files.</span></span>
- <span data-ttu-id="bd7a3-197">Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-197">Cmdlet.</span></span> <span data-ttu-id="bd7a3-198">De cmdlets in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-198">The cmdlets in the current session.</span></span> <span data-ttu-id="bd7a3-199">Cmdlet is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-199">Cmdlet is the default.</span></span>
- <span data-ttu-id="bd7a3-200">Configuratie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-200">Configuration.</span></span> <span data-ttu-id="bd7a3-201">Een Power shell-configuratie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-201">A PowerShell configuration.</span></span> <span data-ttu-id="bd7a3-202">Zie [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-202">For more information, see [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).</span></span>
- <span data-ttu-id="bd7a3-203">ExternalScript.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-203">ExternalScript.</span></span> <span data-ttu-id="bd7a3-204">Alle. ps1-bestanden in de paden die worden vermeld in de Path-omgevings variabele ( `$env:path` ).</span><span class="sxs-lookup"><span data-stu-id="bd7a3-204">All .ps1 files in the paths listed in the Path environment variable (`$env:path`).</span></span>
- <span data-ttu-id="bd7a3-205">Filter en functie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-205">Filter and Function.</span></span> <span data-ttu-id="bd7a3-206">Alle Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-206">All PowerShell functions.</span></span>
- <span data-ttu-id="bd7a3-207">Schriften.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-207">Script.</span></span> <span data-ttu-id="bd7a3-208">Script blokken in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-208">Script blocks in the current session.</span></span>
- <span data-ttu-id="bd7a3-209">Workflowconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-209">Workflow.</span></span> <span data-ttu-id="bd7a3-210">Een Power shell-werk stroom.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-210">A PowerShell workflow.</span></span> <span data-ttu-id="bd7a3-211">Zie [about_Workflows](/powershell/module/PSWorkflow/About/about_Workflows)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-211">For more information, see [about_Workflows](/powershell/module/PSWorkflow/About/about_Workflows).</span></span>

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, All, Application, Cmdlet, Configuration, ExternalScript, Filter, Function, Script, Workflow

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd7a3-212">-Encoding</span><span class="sxs-lookup"><span data-stu-id="bd7a3-212">-Encoding</span></span>

<span data-ttu-id="bd7a3-213">Hiermee geeft u het type code ring voor het doel bestand op.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-213">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="bd7a3-214">De standaardwaarde is `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-214">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="bd7a3-215">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="bd7a3-215">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="bd7a3-216">`ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="bd7a3-216">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="bd7a3-217">`bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-217">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="bd7a3-218">`bigendianutf32`: Codeert in UTF-32-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-218">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="bd7a3-219">`oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-219">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="bd7a3-220">`unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-220">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="bd7a3-221">`utf7`: Wordt gecodeerd in de indeling UTF-7.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-221">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="bd7a3-222">`utf8`: Wordt gecodeerd in UTF-8-indeling.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-222">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="bd7a3-223">`utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="bd7a3-223">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="bd7a3-224">`utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="bd7a3-224">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="bd7a3-225">`utf32`: Gecodeerd in UTF-32-indeling.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-225">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="bd7a3-226">Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` .</span><span class="sxs-lookup"><span data-stu-id="bd7a3-226">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="bd7a3-227">Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-227">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd7a3-228">-Force</span><span class="sxs-lookup"><span data-stu-id="bd7a3-228">-Force</span></span>

<span data-ttu-id="bd7a3-229">Overschrijft een of meer bestaande uitvoer bestanden, zelfs als het bestand het kenmerk alleen-lezen heeft.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-229">Overwrites one or more existing output files, even if the file has the read-only attribute.</span></span>

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

### <span data-ttu-id="bd7a3-230">-FormatTypeName</span><span class="sxs-lookup"><span data-stu-id="bd7a3-230">-FormatTypeName</span></span>

<span data-ttu-id="bd7a3-231">Exporteert opmaak instructies alleen voor de opgegeven Microsoft .NET Framework typen.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-231">Exports formatting instructions only for the specified Microsoft .NET Framework types.</span></span> <span data-ttu-id="bd7a3-232">Voer de type namen in.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-232">Enter the type names.</span></span> <span data-ttu-id="bd7a3-233">`Export-PSSession`Exporteert standaard opmaak instructies voor alle .NET Framework typen die zich niet in de naam ruimte **System. Management. Automation** bevinden.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-233">By default, `Export-PSSession` exports formatting instructions for all .NET Framework types that are not in the **System.Management.Automation** namespace.</span></span>

<span data-ttu-id="bd7a3-234">De waarde van deze para meter moet de naam van een type zijn dat wordt geretourneerd door een `Get-FormatData` opdracht in de sessie van waaruit de opdrachten worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-234">The value of this parameter must be the name of a type that is returned by a `Get-FormatData` command in the session from which the commands are being imported.</span></span> <span data-ttu-id="bd7a3-235">Als u alle opmaak gegevens in de externe sessie wilt ophalen, typt u `*` .</span><span class="sxs-lookup"><span data-stu-id="bd7a3-235">To get all of the formatting data in the remote session, type `*`.</span></span>

<span data-ttu-id="bd7a3-236">Als u de para meter **FormatTypeName** gebruikt, worden er geen opdrachten geëxporteerd, tenzij u de para meter **opdrachtnaam** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-236">If you use the **FormatTypeName** parameter, no commands are exported unless you use the **CommandName** parameter.</span></span>

<span data-ttu-id="bd7a3-237">Als u de para meter **opdrachtnaam** gebruikt, worden de opmaak bestanden voor de opdrachten niet geëxporteerd, tenzij u de para meter **FormatTypeName** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-237">If you use the **CommandName** parameter, the formatting files for the commands are not exported unless you use the **FormatTypeName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd7a3-238">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="bd7a3-238">-FullyQualifiedModule</span></span>

<span data-ttu-id="bd7a3-239">Hiermee geeft u modules op met namen die zijn opgegeven in de vorm van **ModuleSpecification** -objecten.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-239">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span> <span data-ttu-id="bd7a3-240">Zie de sectie opmerkingen van de [ModuleSpecification-constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="bd7a3-240">See the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="bd7a3-241">De para meter **FullyQualifiedModule** accepteert bijvoorbeeld een module naam die is opgegeven in een van de volgende indelingen:</span><span class="sxs-lookup"><span data-stu-id="bd7a3-241">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in either of these formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="bd7a3-242">**Module** naam en **ModuleVersion** zijn vereist, maar **GUID** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-242">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span> <span data-ttu-id="bd7a3-243">U kunt de para meter **FullyQualifiedModule** niet opgeven in dezelfde opdracht als een **module** parameter.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-243">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="bd7a3-244">de twee para meters sluiten elkaar wederzijds uit.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-244">the two parameters are mutually exclusive.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd7a3-245">-Module</span><span class="sxs-lookup"><span data-stu-id="bd7a3-245">-Module</span></span>

<span data-ttu-id="bd7a3-246">Exporteert alleen de opdrachten in de opgegeven Power shell-modules en-modules.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-246">Exports only the commands in the specified PowerShell snap-ins and modules.</span></span> <span data-ttu-id="bd7a3-247">Voer de module-en module namen in.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-247">Enter the snap-in and module names.</span></span> <span data-ttu-id="bd7a3-248">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-248">Wildcards are not permitted.</span></span>

<span data-ttu-id="bd7a3-249">Zie `Import-Module` en [about_PSSnapins](/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-249">For more information, see `Import-Module` and [about_PSSnapins](/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd7a3-250">-OutputModule</span><span class="sxs-lookup"><span data-stu-id="bd7a3-250">-OutputModule</span></span>

<span data-ttu-id="bd7a3-251">Hiermee geeft u een optioneel pad en een naam voor de module gemaakt door `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="bd7a3-251">Specifies an optional path and name for the module created by `Export-PSSession`.</span></span> <span data-ttu-id="bd7a3-252">Het standaardpad is `$home\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="bd7a3-252">The default path is `$home\Documents\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="bd7a3-253">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-253">This parameter is required.</span></span>

<span data-ttu-id="bd7a3-254">Als de subdirectory van de module of een van de bestanden die `Export-PSSession` al bestaan, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-254">If the module subdirectory or any of the files that `Export-PSSession` creates already exist, the command fails.</span></span> <span data-ttu-id="bd7a3-255">Als u bestaande bestanden wilt overschrijven, gebruikt u de para meter **Force** .</span><span class="sxs-lookup"><span data-stu-id="bd7a3-255">To overwrite existing files, use the **Force** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, ModuleName

Required: True
Position: 1
Default value: $home\Documents\WindowsPowerShell\Modules
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd7a3-256">-Sessie</span><span class="sxs-lookup"><span data-stu-id="bd7a3-256">-Session</span></span>

<span data-ttu-id="bd7a3-257">Hiermee geeft u de PSSession op waaruit de opdrachten worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-257">Specifies the PSSession from which the commands are exported.</span></span> <span data-ttu-id="bd7a3-258">Voer een variabele in die een sessie object bevat of een opdracht waarmee een sessie object wordt opgehaald, zoals een `Get-PSSession` opdracht.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-258">Enter a variable that contains a session object or a command that gets a session object, such as a `Get-PSSession` command.</span></span> <span data-ttu-id="bd7a3-259">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-259">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd7a3-260">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bd7a3-260">CommonParameters</span></span>

<span data-ttu-id="bd7a3-261">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-261">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bd7a3-262">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-262">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bd7a3-263">INVOER</span><span class="sxs-lookup"><span data-stu-id="bd7a3-263">INPUTS</span></span>

### <span data-ttu-id="bd7a3-264">Geen</span><span class="sxs-lookup"><span data-stu-id="bd7a3-264">None</span></span>

<span data-ttu-id="bd7a3-265">U kunt geen objecten pipeen naar `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="bd7a3-265">You cannot pipe objects to `Export-PSSession`.</span></span>

## <span data-ttu-id="bd7a3-266">UITVOER</span><span class="sxs-lookup"><span data-stu-id="bd7a3-266">OUTPUTS</span></span>

### <span data-ttu-id="bd7a3-267">System. IO. file info</span><span class="sxs-lookup"><span data-stu-id="bd7a3-267">System.IO.FileInfo</span></span>

<span data-ttu-id="bd7a3-268">`Export-PSSession` retourneert een lijst met bestanden waaruit de module bestaat die deze heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-268">`Export-PSSession` returns a list of files that comprise the module that it created.</span></span>

## <span data-ttu-id="bd7a3-269">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="bd7a3-269">NOTES</span></span>

<span data-ttu-id="bd7a3-270">`Export-PSSession` is afhankelijk van de externe infra structuur van Power shell.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-270">`Export-PSSession` relies on the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="bd7a3-271">Als u deze cmdlet wilt gebruiken, moet de computer zijn geconfigureerd voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-271">To use this cmdlet, the computer must be configured for remoting.</span></span> <span data-ttu-id="bd7a3-272">Zie [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-272">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="bd7a3-273">U kunt niet gebruiken `Export-PSSession` om een Power shell-provider te exporteren.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-273">You cannot use `Export-PSSession` to export a PowerShell provider.</span></span>

<span data-ttu-id="bd7a3-274">Geëxporteerde opdrachten worden impliciet uitgevoerd in de PSSession van waaruit ze zijn geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-274">Exported commands run implicitly in the PSSession from which they were exported.</span></span> <span data-ttu-id="bd7a3-275">De details van het extern uitvoeren van de opdrachten worden volledig verwerkt door Power shell.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-275">The details of running the commands remotely are handled entirely by PowerShell.</span></span> <span data-ttu-id="bd7a3-276">U kunt de geëxporteerde opdrachten uitvoeren op dezelfde manier als u lokale opdrachten uitvoert.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-276">You can run the exported commands just as you would run local commands.</span></span>

<span data-ttu-id="bd7a3-277">`Export-ModuleMember` Hiermee worden gegevens vastgelegd en opgeslagen over de PSSession in de module die wordt geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-277">`Export-ModuleMember` captures and saves information about the PSSession in the module that it exports.</span></span> <span data-ttu-id="bd7a3-278">Als de PSSession van waaruit de opdrachten zijn geëxporteerd, is gesloten wanneer u de module importeert en er geen actieve PSSessions op dezelfde computer zijn, proberen de opdrachten in de module de PSSession opnieuw te maken.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-278">If the PSSession from which the commands were exported is closed when you import the module, and there are no active PSSessions to the same computer, the commands in the module attempt to recreate the PSSession.</span></span> <span data-ttu-id="bd7a3-279">Als pogingen om de PSSession opnieuw te maken mislukken, worden de geëxporteerde opdrachten niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-279">If attempts to recreate the PSSession fail, the exported commands will not run.</span></span>

<span data-ttu-id="bd7a3-280">De sessie gegevens die `Export-ModuleMember` in de module worden vastgelegd en opgeslagen, bevatten geen sessie opties, zoals die u opgeeft in de `$PSSessionOption` Voorkeurs variabele of met behulp van de para meter **SessionOption** van de `New-PSSession` -, `Enter-PSSession` -of- `Invoke-Command` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-280">The session information that `Export-ModuleMember` captures and saves in the module does not include session options, such as those that you specify in the `$PSSessionOption` preference variable or by using the **SessionOption** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlets.</span></span> <span data-ttu-id="bd7a3-281">Als de oorspronkelijke PSSession is gesloten wanneer u de module importeert, gebruikt de module een andere PSSession naar dezelfde computer, als er een beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-281">If the original PSSession is closed when you import the module, the module will use another PSSession to the same computer, if one is available.</span></span> <span data-ttu-id="bd7a3-282">Als u wilt dat de geïmporteerde opdrachten kunnen worden uitgevoerd in een correct geconfigureerde sessie, maakt u een PSSession met de gewenste opties voordat u de module importeert.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-282">To enable the imported commands to run in a correctly configured session, create a PSSession with the options that you want before you import the module.</span></span>

<span data-ttu-id="bd7a3-283">Voor het zoeken naar de te exporteren opdrachten `Export-PSSession` gebruikt u de `Invoke-Command` cmdlet om een opdracht uit te voeren `Get-Command` in de PSSession.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-283">To find the commands to export, `Export-PSSession` uses the `Invoke-Command` cmdlet to run a `Get-Command` command in the PSSession.</span></span> <span data-ttu-id="bd7a3-284">Voor het ophalen en opslaan van opmaak gegevens voor de opdrachten, worden de- `Get-FormatData` en- `Export-FormatData` cmdlets gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-284">To get and save formatting data for the commands, it uses the `Get-FormatData` and `Export-FormatData` cmdlets.</span></span> <span data-ttu-id="bd7a3-285">U ziet mogelijk fout berichten van `Invoke-Command` , `Get-Command` , `Get-FormatData` en `Export-FormatData` Wanneer u een opdracht uitvoert `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="bd7a3-285">You might see error messages from `Invoke-Command`, `Get-Command`, `Get-FormatData`, and `Export-FormatData` when you run an `Export-PSSession` command.</span></span> <span data-ttu-id="bd7a3-286">Daarnaast `Export-PSSession` kunt u geen opdrachten exporteren vanuit een sessie die geen-,-, `Get-Command` `Get-FormatData` `Select-Object` -en- `Get-Help` cmdlets bevat.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-286">Also, `Export-PSSession` cannot export commands from a session that does not include the `Get-Command`, `Get-FormatData`, `Select-Object`, and `Get-Help` cmdlets.</span></span>

<span data-ttu-id="bd7a3-287">`Export-PSSession` gebruikt de `Write-Progress` cmdlet om de voortgang van de opdracht weer te geven.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-287">`Export-PSSession` uses the `Write-Progress` cmdlet to display the progress of the command.</span></span> <span data-ttu-id="bd7a3-288">Mogelijk wordt de voortgangs balk weer geven terwijl de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-288">You might see the progress bar while the command is running.</span></span>

<span data-ttu-id="bd7a3-289">Geëxporteerde opdrachten hebben dezelfde beperkingen als andere externe opdrachten, waaronder het niet mogelijk is om een programma te starten met een gebruikers interface, zoals Klad blok.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-289">Exported commands have the same limitations as other remote commands, including the inability to start a program with a user interface, such as Notepad.</span></span>

<span data-ttu-id="bd7a3-290">Omdat Power shell-profielen niet worden uitgevoerd in PSSessions, zijn de opdrachten die door een profiel aan een sessie worden toegevoegd, niet beschikbaar voor `Export-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="bd7a3-290">Because PowerShell profiles are not run in PSSessions, the commands that a profile adds to a session are not available to `Export-PSSession`.</span></span> <span data-ttu-id="bd7a3-291">Als u opdrachten uit een profiel wilt exporteren, gebruikt u een `Invoke-Command` opdracht om het profiel hand matig uit te voeren in de PSSession voordat u de opdrachten exporteert.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-291">To export commands from a profile, use an `Invoke-Command` command to run the profile in the PSSession manually before exporting commands.</span></span>

<span data-ttu-id="bd7a3-292">De module die `Export-PSSession` maakt, kan een opmaak bestand bevatten, zelfs als de opdracht geen indelings gegevens importeert.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-292">The module that `Export-PSSession` creates might include a formatting file, even if the command does not import formatting data.</span></span> <span data-ttu-id="bd7a3-293">Als de opdracht geen indelings gegevens importeert, bevatten indelings bestanden die worden gemaakt geen opmaak gegevens.</span><span class="sxs-lookup"><span data-stu-id="bd7a3-293">If the command does not import formatting data, any formatting files that are created will not contain formatting data.</span></span>

## <span data-ttu-id="bd7a3-294">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="bd7a3-294">RELATED LINKS</span></span>

[<span data-ttu-id="bd7a3-295">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="bd7a3-295">about_Command_Precedence</span></span>](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)

[<span data-ttu-id="bd7a3-296">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="bd7a3-296">about_PSSessions</span></span>](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[<span data-ttu-id="bd7a3-297">about_PSSnapins</span><span class="sxs-lookup"><span data-stu-id="bd7a3-297">about_PSSnapins</span></span>](/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1)

[<span data-ttu-id="bd7a3-298">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="bd7a3-298">about_Remote_Requirements</span></span>](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)

[<span data-ttu-id="bd7a3-299">Import-module</span><span class="sxs-lookup"><span data-stu-id="bd7a3-299">Import-Module</span></span>](../Microsoft.PowerShell.Core/Import-Module.md)

[<span data-ttu-id="bd7a3-300">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="bd7a3-300">Import-PSSession</span></span>](Import-PSSession.md)

[<span data-ttu-id="bd7a3-301">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="bd7a3-301">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="bd7a3-302">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="bd7a3-302">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="bd7a3-303">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="bd7a3-303">New-PSSessionOption</span></span>](../Microsoft.PowerShell.Core/New-PSSessionOption.md)

[<span data-ttu-id="bd7a3-304">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="bd7a3-304">Remove-PSSession</span></span>](../Microsoft.PowerShell.Core/Remove-PSSession.md)