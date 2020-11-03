---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-process?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Process
ms.openlocfilehash: 713a25bd09b7abc63a0f4974eb905a88c1d4c0e1
ms.sourcegitcommit: 4fc8cf397cb725ae973751d1d5d542f34f0db2d7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2020
ms.locfileid: "93251699"
---
# <span data-ttu-id="af95b-103">Start-Process</span><span class="sxs-lookup"><span data-stu-id="af95b-103">Start-Process</span></span>

## <span data-ttu-id="af95b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="af95b-104">SYNOPSIS</span></span>
<span data-ttu-id="af95b-105">Start een of meer processen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="af95b-105">Starts one or more processes on the local computer.</span></span>

## <span data-ttu-id="af95b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="af95b-106">SYNTAX</span></span>

### <span data-ttu-id="af95b-107">Standaard (standaard instelling)</span><span class="sxs-lookup"><span data-stu-id="af95b-107">Default (Default)</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-Credential <PSCredential>]
 [-WorkingDirectory <String>] [-LoadUserProfile] [-NoNewWindow] [-PassThru]
 [-RedirectStandardError <String>] [-RedirectStandardInput <String>]
 [-RedirectStandardOutput <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-UseNewEnvironment]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="af95b-108">Useshellexecute worden</span><span class="sxs-lookup"><span data-stu-id="af95b-108">UseShellExecute</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-WorkingDirectory <String>]
 [-PassThru] [-Verb <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="af95b-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="af95b-109">DESCRIPTION</span></span>

<span data-ttu-id="af95b-110">De `Start-Process` cmdlet start een of meer processen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="af95b-110">The `Start-Process` cmdlet starts one or more processes on the local computer.</span></span> <span data-ttu-id="af95b-111">`Start-Process`Maakt standaard een nieuw proces dat alle omgevings variabelen overneemt die in het huidige proces zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="af95b-111">By default, `Start-Process` creates a new process that inherits all the environment variables that are defined in the current process.</span></span>

<span data-ttu-id="af95b-112">Als u het programma wilt opgeven dat in het proces wordt uitgevoerd, voert u een uitvoerbaar bestand of script bestand in of een bestand dat kan worden geopend met behulp van een programma op de computer.</span><span class="sxs-lookup"><span data-stu-id="af95b-112">To specify the program that runs in the process, enter an executable file or script file, or a file that can be opened by using a program on the computer.</span></span> <span data-ttu-id="af95b-113">Als u een niet-uitvoerbaar bestand opgeeft, `Start-Process` wordt het programma gestart dat is gekoppeld aan het bestand, vergelijkbaar met de `Invoke-Item` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="af95b-113">If you specify a non-executable file, `Start-Process` starts the program that is associated with the file, similar to the `Invoke-Item` cmdlet.</span></span>

<span data-ttu-id="af95b-114">U kunt de para meters van gebruiken `Start-Process` om opties op te geven, zoals het laden van een gebruikers profiel, het starten van het proces in een nieuw venster of het gebruik van alternatieve referenties.</span><span class="sxs-lookup"><span data-stu-id="af95b-114">You can use the parameters of `Start-Process` to specify options, such as loading a user profile, starting the process in a new window, or using alternate credentials.</span></span>

## <span data-ttu-id="af95b-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="af95b-115">EXAMPLES</span></span>

### <span data-ttu-id="af95b-116">Voor beeld 1: een proces starten dat gebruikmaakt van standaard waarden</span><span class="sxs-lookup"><span data-stu-id="af95b-116">Example 1: Start a process that uses default values</span></span>

<span data-ttu-id="af95b-117">In dit voor beeld wordt een proces gestart dat gebruikmaakt `Sort.exe` van het bestand in de huidige map.</span><span class="sxs-lookup"><span data-stu-id="af95b-117">This example starts a process that uses the `Sort.exe` file in the current folder.</span></span> <span data-ttu-id="af95b-118">De opdracht gebruikt alle standaard waarden, met inbegrip van de standaard venster stijl, werkmap en referenties.</span><span class="sxs-lookup"><span data-stu-id="af95b-118">The command uses all of the default values, including the default window style, working folder, and credentials.</span></span>

```powershell
Start-Process -FilePath "sort.exe"
```

### <span data-ttu-id="af95b-119">Voor beeld 2: een tekst bestand afdrukken</span><span class="sxs-lookup"><span data-stu-id="af95b-119">Example 2: Print a text file</span></span>

<span data-ttu-id="af95b-120">In dit voor beeld wordt een proces gestart waarmee het bestand wordt afgedrukt `C:\PS-Test\MyFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="af95b-120">This example starts a process that prints the `C:\PS-Test\MyFile.txt` file.</span></span>

```powershell
Start-Process -FilePath "myfile.txt" -WorkingDirectory "C:\PS-Test" -Verb Print
```

### <span data-ttu-id="af95b-121">Voor beeld 3: een proces starten om items naar een nieuw bestand te sorteren</span><span class="sxs-lookup"><span data-stu-id="af95b-121">Example 3: Start a process to sort items to a new file</span></span>

<span data-ttu-id="af95b-122">In dit voor beeld wordt een proces gestart waarmee items in het bestand worden gesorteerd `Testsort.txt` en de gesorteerde items in de bestanden worden geretourneerd `Sorted.txt` .</span><span class="sxs-lookup"><span data-stu-id="af95b-122">This example starts a process that sorts items in the `Testsort.txt` file and returns the sorted items in the `Sorted.txt` files.</span></span> <span data-ttu-id="af95b-123">Eventuele fouten worden naar het `SortError.txt` bestand geschreven.</span><span class="sxs-lookup"><span data-stu-id="af95b-123">Any errors are written to the `SortError.txt` file.</span></span>

```powershell
Start-Process -FilePath "Sort.exe" -RedirectStandardInput "Testsort.txt" -RedirectStandardOutput "Sorted.txt" -RedirectStandardError "SortError.txt" -UseNewEnvironment
```

<span data-ttu-id="af95b-124">De para meter **UseNewEnvironment** geeft aan dat het proces wordt uitgevoerd met de eigen omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="af95b-124">The **UseNewEnvironment** parameter specifies that the process runs with its own environment variables.</span></span>

### <span data-ttu-id="af95b-125">Voor beeld 4: een proces in een gemaximaliseerd venster starten</span><span class="sxs-lookup"><span data-stu-id="af95b-125">Example 4: Start a process in a maximized window</span></span>

<span data-ttu-id="af95b-126">In dit voor beeld wordt het `Notepad.exe` proces gestart.</span><span class="sxs-lookup"><span data-stu-id="af95b-126">This example starts the `Notepad.exe` process.</span></span> <span data-ttu-id="af95b-127">Het maximaliseert het venster en behoudt het venster totdat het proces is voltooid.</span><span class="sxs-lookup"><span data-stu-id="af95b-127">It maximizes the window and retains the window until the process completes.</span></span>

```powershell
Start-Process -FilePath "notepad" -Wait -WindowStyle Maximized
```

### <span data-ttu-id="af95b-128">Voor beeld 5: Power shell starten als beheerder</span><span class="sxs-lookup"><span data-stu-id="af95b-128">Example 5: Start PowerShell as an administrator</span></span>

<span data-ttu-id="af95b-129">In dit voor beeld wordt Power shell gestart met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="af95b-129">This example starts PowerShell by using the **Run as administrator** option.</span></span>

```powershell
Start-Process -FilePath "powershell" -Verb RunAs
```

### <span data-ttu-id="af95b-130">Voor beeld 6: verschillende woorden gebruiken om een proces te starten</span><span class="sxs-lookup"><span data-stu-id="af95b-130">Example 6: Using different verbs to start a process</span></span>

<span data-ttu-id="af95b-131">In dit voor beeld ziet u hoe u de termen vindt die kunnen worden gebruikt bij het starten van een proces.</span><span class="sxs-lookup"><span data-stu-id="af95b-131">This example shows how to find the verbs that can be used when starting a process.</span></span> <span data-ttu-id="af95b-132">De beschik bare termen worden bepaald door de bestandsnaam extensie van het bestand dat in het proces wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="af95b-132">The available verbs are determined by the filename extension of the file that runs in the process.</span></span>

```powershell
$startExe = New-Object System.Diagnostics.ProcessStartInfo -Args PowerShell.exe
$startExe.verbs
```

```Output
open
runas
runasuser
```

<span data-ttu-id="af95b-133">In het voor beeld wordt gebruikt `New-Object` om een **System. Diagnostics. ProcessStartInfo** -object te maken voor **PowerShell.exe** , het bestand dat in het Power Shell-proces wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="af95b-133">The example uses `New-Object` to create a **System.Diagnostics.ProcessStartInfo** object for **PowerShell.exe** , the file that runs in the PowerShell process.</span></span> <span data-ttu-id="af95b-134">De eigenschap **verbs** van het object **ProcessStartInfo** laat zien dat u de werk woorden **Open** en **runas** kunt gebruiken met `PowerShell.exe` , of met elk proces waarmee een bestand wordt uitgevoerd `.exe` .</span><span class="sxs-lookup"><span data-stu-id="af95b-134">The **Verbs** property of the **ProcessStartInfo** object shows that you can use the **Open** and **RunAs** verbs with `PowerShell.exe`, or with any process that runs a `.exe` file.</span></span>

### <span data-ttu-id="af95b-135">Voor beeld 7: argumenten opgeven voor het proces</span><span class="sxs-lookup"><span data-stu-id="af95b-135">Example 7: Specifying arguments to the process</span></span>

<span data-ttu-id="af95b-136">Met beide opdrachten start u de Windows-opdracht-interpreter, waarbij een opdracht wordt uitgegeven `dir` in de `Program Files` map.</span><span class="sxs-lookup"><span data-stu-id="af95b-136">Both commands start the Windows command interpreter, issuing a `dir` command on the `Program Files` folder.</span></span> <span data-ttu-id="af95b-137">Omdat deze mapnaam een spatie bevat, moet de waarde tussen dubbele aanhalings tekens worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="af95b-137">Because this foldername contains a space, the value needs surrounded with escaped quotes.</span></span>
<span data-ttu-id="af95b-138">Houd er rekening mee dat met de eerste opdracht een teken reeks wordt opgegeven als **argument List**.</span><span class="sxs-lookup"><span data-stu-id="af95b-138">Note that the first command specifies a string as **ArgumentList**.</span></span> <span data-ttu-id="af95b-139">De tweede opdracht is een teken reeks matrix.</span><span class="sxs-lookup"><span data-stu-id="af95b-139">The second command is a string array.</span></span>

```powershell
Start-Process -FilePath "$env:comspec" -ArgumentList "/c dir `"%systemdrive%\program files`""
Start-Process -FilePath "$env:comspec" -ArgumentList "/c","dir","`"%systemdrive%\program files`""
```

## <span data-ttu-id="af95b-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="af95b-140">PARAMETERS</span></span>

### <span data-ttu-id="af95b-141">-Argument List</span><span class="sxs-lookup"><span data-stu-id="af95b-141">-ArgumentList</span></span>

<span data-ttu-id="af95b-142">Hiermee geeft u para meters of parameter waarden op die moeten worden gebruikt wanneer deze cmdlet het proces start.</span><span class="sxs-lookup"><span data-stu-id="af95b-142">Specifies parameters or parameter values to use when this cmdlet starts the process.</span></span> <span data-ttu-id="af95b-143">Argumenten kunnen worden geaccepteerd als één teken reeks met de argumenten gescheiden door spaties, of als een matrix met teken reeksen gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="af95b-143">Arguments can be accepted as a single string with the arguments separated by spaces, or as an array of strings separated by commas.</span></span>

<span data-ttu-id="af95b-144">Als para meters of parameter waarden een spatie bevatten, moeten deze tussen dubbele aanhalings tekens worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="af95b-144">If parameters or parameter values contain a space, they need to be surrounded with escaped double quotes.</span></span> <span data-ttu-id="af95b-145">Zie [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="af95b-145">For more information, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af95b-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="af95b-146">-Credential</span></span>

<span data-ttu-id="af95b-147">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="af95b-147">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="af95b-148">De cmdlet maakt standaard gebruik van de referenties van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="af95b-148">By default, the cmdlet uses the credentials of the current user.</span></span>

<span data-ttu-id="af95b-149">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="af95b-149">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="af95b-150">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="af95b-150">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="af95b-151">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="af95b-151">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="af95b-152">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="af95b-152">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Default
Aliases: RunAs

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af95b-153">-FilePath</span><span class="sxs-lookup"><span data-stu-id="af95b-153">-FilePath</span></span>

<span data-ttu-id="af95b-154">Hiermee geeft u het pad en de bestands naam op van het programma dat in het proces wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="af95b-154">Specifies the optional path and filename of the program that runs in the process.</span></span> <span data-ttu-id="af95b-155">Voer de naam in van een uitvoerbaar bestand of van een document, zoals een `.txt` of `.doc` -bestand, dat is gekoppeld aan een programma op de computer.</span><span class="sxs-lookup"><span data-stu-id="af95b-155">Enter the name of an executable file or of a document, such as a `.txt` or `.doc` file, that is associated with a program on the computer.</span></span> <span data-ttu-id="af95b-156">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="af95b-156">This parameter is required.</span></span>

<span data-ttu-id="af95b-157">Als u alleen een bestands naam opgeeft, gebruikt u de para meter **variabele workingdirectory** om het pad op te geven.</span><span class="sxs-lookup"><span data-stu-id="af95b-157">If you specify only a filename, use the **WorkingDirectory** parameter to specify the path.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af95b-158">-LoadUserProfile</span><span class="sxs-lookup"><span data-stu-id="af95b-158">-LoadUserProfile</span></span>

<span data-ttu-id="af95b-159">Geeft aan dat met deze cmdlet het Windows-gebruikers profiel wordt geladen dat is opgeslagen in de `HKEY_USERS` register sleutel voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="af95b-159">Indicates that this cmdlet loads the Windows user profile stored in the `HKEY_USERS` registry key for the current user.</span></span> <span data-ttu-id="af95b-160">De para meter is niet van toepassing op niet-Windows-systemen.</span><span class="sxs-lookup"><span data-stu-id="af95b-160">The parameter does not apply for non-Windows systems.</span></span>

<span data-ttu-id="af95b-161">Deze para meter heeft geen invloed op de Power shell-profielen.</span><span class="sxs-lookup"><span data-stu-id="af95b-161">This parameter does not affect the PowerShell profiles.</span></span> <span data-ttu-id="af95b-162">Zie [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="af95b-162">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: Lup

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af95b-163">-Outnewwindow</span><span class="sxs-lookup"><span data-stu-id="af95b-163">-NoNewWindow</span></span>

<span data-ttu-id="af95b-164">Start het nieuwe proces in het huidige console venster.</span><span class="sxs-lookup"><span data-stu-id="af95b-164">Start the new process in the current console window.</span></span> <span data-ttu-id="af95b-165">In Windows wordt standaard een nieuw venster geopend.</span><span class="sxs-lookup"><span data-stu-id="af95b-165">By default on Windows, PowerShell opens a new window.</span></span> <span data-ttu-id="af95b-166">Op niet-Windows-systemen krijgt u nooit een nieuw terminal venster.</span><span class="sxs-lookup"><span data-stu-id="af95b-166">On non-Windows systems, you never get a new terminal window.</span></span>

<span data-ttu-id="af95b-167">U kunt de para meters voor niet- **NewWindow** en **WindowStyle** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="af95b-167">You cannot use the **NoNewWindow** and **WindowStyle** parameters in the same command.</span></span>

<span data-ttu-id="af95b-168">De para meter is niet van toepassing op niet-Windows-systemen.</span><span class="sxs-lookup"><span data-stu-id="af95b-168">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: nnw

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af95b-169">-PassThru</span><span class="sxs-lookup"><span data-stu-id="af95b-169">-PassThru</span></span>

<span data-ttu-id="af95b-170">Retourneert een proces object voor elk proces dat door de cmdlet is gestart.</span><span class="sxs-lookup"><span data-stu-id="af95b-170">Returns a process object for each process that the cmdlet started.</span></span> <span data-ttu-id="af95b-171">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="af95b-171">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="af95b-172">-RedirectStandardError</span><span class="sxs-lookup"><span data-stu-id="af95b-172">-RedirectStandardError</span></span>

<span data-ttu-id="af95b-173">Hiermee geeft u een bestand.</span><span class="sxs-lookup"><span data-stu-id="af95b-173">Specifies a file.</span></span> <span data-ttu-id="af95b-174">Met deze cmdlet worden fouten verzonden die door het proces worden gegenereerd naar een bestand dat u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="af95b-174">This cmdlet sends any errors generated by the process to a file that you specify.</span></span>
<span data-ttu-id="af95b-175">Voer het pad en de bestands naam in.</span><span class="sxs-lookup"><span data-stu-id="af95b-175">Enter the path and filename.</span></span> <span data-ttu-id="af95b-176">De fouten worden standaard weer gegeven in de-console.</span><span class="sxs-lookup"><span data-stu-id="af95b-176">By default, the errors are displayed in the console.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af95b-177">-RedirectStandardInput</span><span class="sxs-lookup"><span data-stu-id="af95b-177">-RedirectStandardInput</span></span>

<span data-ttu-id="af95b-178">Hiermee geeft u een bestand.</span><span class="sxs-lookup"><span data-stu-id="af95b-178">Specifies a file.</span></span> <span data-ttu-id="af95b-179">Met deze cmdlet wordt de invoer van het opgegeven bestand gelezen.</span><span class="sxs-lookup"><span data-stu-id="af95b-179">This cmdlet reads input from the specified file.</span></span> <span data-ttu-id="af95b-180">Voer het pad en de bestands naam van het invoer bestand in.</span><span class="sxs-lookup"><span data-stu-id="af95b-180">Enter the path and filename of the input file.</span></span> <span data-ttu-id="af95b-181">Het proces krijgt standaard de invoer van het toetsen bord.</span><span class="sxs-lookup"><span data-stu-id="af95b-181">By default, the process gets its input from the keyboard.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af95b-182">-RedirectStandardOutput</span><span class="sxs-lookup"><span data-stu-id="af95b-182">-RedirectStandardOutput</span></span>

<span data-ttu-id="af95b-183">Hiermee geeft u een bestand.</span><span class="sxs-lookup"><span data-stu-id="af95b-183">Specifies a file.</span></span> <span data-ttu-id="af95b-184">Met deze cmdlet wordt de uitvoer die door het proces is gegenereerd, verzonden naar een bestand dat u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="af95b-184">This cmdlet sends the output generated by the process to a file that you specify.</span></span>
<span data-ttu-id="af95b-185">Voer het pad en de bestands naam in.</span><span class="sxs-lookup"><span data-stu-id="af95b-185">Enter the path and filename.</span></span> <span data-ttu-id="af95b-186">Standaard wordt de uitvoer in de-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="af95b-186">By default, the output is displayed in the console.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af95b-187">-UseNewEnvironment</span><span class="sxs-lookup"><span data-stu-id="af95b-187">-UseNewEnvironment</span></span>

<span data-ttu-id="af95b-188">Geeft aan dat deze cmdlet nieuwe omgevings variabelen gebruikt die zijn opgegeven voor het proces.</span><span class="sxs-lookup"><span data-stu-id="af95b-188">Indicates that this cmdlet uses new environment variables specified for the process.</span></span> <span data-ttu-id="af95b-189">Standaard wordt het gestarte proces uitgevoerd met de omgevings variabelen die zijn overgenomen van het bovenliggende proces.</span><span class="sxs-lookup"><span data-stu-id="af95b-189">By default, the started process runs with the environment variables inherited from the parent process.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af95b-190">-Verb</span><span class="sxs-lookup"><span data-stu-id="af95b-190">-Verb</span></span>

<span data-ttu-id="af95b-191">Hiermee geeft u een term op die moet worden gebruikt wanneer deze cmdlet het proces start.</span><span class="sxs-lookup"><span data-stu-id="af95b-191">Specifies a verb to use when this cmdlet starts the process.</span></span> <span data-ttu-id="af95b-192">De beschik bare termen worden bepaald door de bestandsnaam extensie van het bestand dat in het proces wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="af95b-192">The verbs that are available are determined by the filename extension of the file that runs in the process.</span></span>

<span data-ttu-id="af95b-193">In de volgende tabel ziet u de bewerkingen voor een aantal algemene proces bestands typen.</span><span class="sxs-lookup"><span data-stu-id="af95b-193">The following table shows the verbs for some common process file types.</span></span>

| <span data-ttu-id="af95b-194">Bestands type</span><span class="sxs-lookup"><span data-stu-id="af95b-194">File type</span></span> |                <span data-ttu-id="af95b-195">Termen</span><span class="sxs-lookup"><span data-stu-id="af95b-195">Verbs</span></span>                |
| --------- | ----------------------------------- |
| <span data-ttu-id="af95b-196">cmd</span><span class="sxs-lookup"><span data-stu-id="af95b-196">.cmd</span></span>      | <span data-ttu-id="af95b-197">Bewerken, openen, afdrukken, runas, RunAsUser</span><span class="sxs-lookup"><span data-stu-id="af95b-197">Edit, Open, Print, RunAs, RunAsUser</span></span> |
| <span data-ttu-id="af95b-198">.exe</span><span class="sxs-lookup"><span data-stu-id="af95b-198">.exe</span></span>      | <span data-ttu-id="af95b-199">Open, runas, RunAsUser</span><span class="sxs-lookup"><span data-stu-id="af95b-199">Open, RunAs, RunAsUser</span></span>              |
| <span data-ttu-id="af95b-200">.txt</span><span class="sxs-lookup"><span data-stu-id="af95b-200">.txt</span></span>      | <span data-ttu-id="af95b-201">Openen, afdrukken, PrintTo</span><span class="sxs-lookup"><span data-stu-id="af95b-201">Open, Print, PrintTo</span></span>                |
| <span data-ttu-id="af95b-202">.wav</span><span class="sxs-lookup"><span data-stu-id="af95b-202">.wav</span></span>      | <span data-ttu-id="af95b-203">Openen, afspelen</span><span class="sxs-lookup"><span data-stu-id="af95b-203">Open, Play</span></span>                          |

<span data-ttu-id="af95b-204">Als u de woorden wilt vinden die kunnen worden gebruikt in combi natie met het bestand dat in een proces wordt uitgevoerd, gebruikt u de `New-Object` cmdlet om een **System. Diagnostics. ProcessStartInfo** -object voor het bestand te maken.</span><span class="sxs-lookup"><span data-stu-id="af95b-204">To find the verbs that can be used with the file that runs in a process, use the `New-Object` cmdlet to create a **System.Diagnostics.ProcessStartInfo** object for the file.</span></span> <span data-ttu-id="af95b-205">De beschik bare termen bevinden zich in de eigenschap **verbs** van het object **ProcessStartInfo** .</span><span class="sxs-lookup"><span data-stu-id="af95b-205">The available verbs are in the **Verbs** property of the **ProcessStartInfo** object.</span></span> <span data-ttu-id="af95b-206">Zie de voor beelden voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="af95b-206">For details, see the examples.</span></span>

<span data-ttu-id="af95b-207">De para meter is niet van toepassing op niet-Windows-systemen.</span><span class="sxs-lookup"><span data-stu-id="af95b-207">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.String
Parameter Sets: UseShellExecute
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af95b-208">-Wachten</span><span class="sxs-lookup"><span data-stu-id="af95b-208">-Wait</span></span>

<span data-ttu-id="af95b-209">Hiermee wordt aangegeven dat met deze cmdlet wordt gewacht op het opgegeven proces en de descendanten die moeten worden voltooid voordat meer invoer wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="af95b-209">Indicates that this cmdlet waits for the specified process and its descendants to complete before accepting more input.</span></span> <span data-ttu-id="af95b-210">Met deze para meter wordt de opdracht prompt onderdrukt of wordt het venster bewaard totdat de processen zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="af95b-210">This parameter suppresses the command prompt or retains the window until the processes finish.</span></span>

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

### <span data-ttu-id="af95b-211">-WindowStyle</span><span class="sxs-lookup"><span data-stu-id="af95b-211">-WindowStyle</span></span>

<span data-ttu-id="af95b-212">Hiermee geeft u de status van het venster dat voor het nieuwe proces wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="af95b-212">Specifies the state of the window that is used for the new process.</span></span> <span data-ttu-id="af95b-213">De acceptabele waarden voor deze para meter zijn: **normaal** , **verborgen** , **geminimaliseerd** en **gemaximaliseerd**.</span><span class="sxs-lookup"><span data-stu-id="af95b-213">The acceptable values for this parameter are: **Normal** , **Hidden** , **Minimized** , and **Maximized**.</span></span> <span data-ttu-id="af95b-214">De standaard waarde is **Normal**.</span><span class="sxs-lookup"><span data-stu-id="af95b-214">The default value is **Normal**.</span></span>

<span data-ttu-id="af95b-215">U kunt de para meters **WindowStyle** en **NewWindow** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="af95b-215">You cannot use the **WindowStyle** and **NoNewWindow** parameters in the same command.</span></span>

<span data-ttu-id="af95b-216">De para meter is niet van toepassing op niet-Windows-systemen.</span><span class="sxs-lookup"><span data-stu-id="af95b-216">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.Diagnostics.ProcessWindowStyle
Parameter Sets: (All)
Aliases:
Accepted values: Normal, Hidden, Minimized, Maximized

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af95b-217">-Variabele workingdirectory</span><span class="sxs-lookup"><span data-stu-id="af95b-217">-WorkingDirectory</span></span>

<span data-ttu-id="af95b-218">Hiermee geeft u de locatie op waar het nieuwe proces moet worden gestart.</span><span class="sxs-lookup"><span data-stu-id="af95b-218">Specifies the location that the new process should start in.</span></span> <span data-ttu-id="af95b-219">De standaard waarde is de locatie van het uitvoer bare bestand of het document dat wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="af95b-219">The default is the location of the executable file or document being started.</span></span> <span data-ttu-id="af95b-220">Het pad dat wordt gegeven, wordt beschouwd als een letterlijk pad.</span><span class="sxs-lookup"><span data-stu-id="af95b-220">The path provided is treated as a literal path.</span></span> <span data-ttu-id="af95b-221">Jokertekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="af95b-221">Wildcards are not supported.</span></span> <span data-ttu-id="af95b-222">U moet het pad tussen enkele aanhalings tekens plaatsen ( `'` ) als de padnaam letters bevat die als Joker teken worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="af95b-222">You must enclose the path in single quotes (`'`) if the path name contains characters that would be interpreted as wildcards.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af95b-223">-Confirm</span><span class="sxs-lookup"><span data-stu-id="af95b-223">-Confirm</span></span>

<span data-ttu-id="af95b-224">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="af95b-224">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af95b-225">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="af95b-225">-WhatIf</span></span>

<span data-ttu-id="af95b-226">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="af95b-226">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="af95b-227">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="af95b-227">The cmdlet is not run.</span></span>

<span data-ttu-id="af95b-228">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="af95b-228">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af95b-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="af95b-229">CommonParameters</span></span>

<span data-ttu-id="af95b-230">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="af95b-230">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="af95b-231">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="af95b-231">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="af95b-232">INVOER</span><span class="sxs-lookup"><span data-stu-id="af95b-232">INPUTS</span></span>

### <span data-ttu-id="af95b-233">Geen</span><span class="sxs-lookup"><span data-stu-id="af95b-233">None</span></span>

<span data-ttu-id="af95b-234">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="af95b-234">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="af95b-235">UITVOER</span><span class="sxs-lookup"><span data-stu-id="af95b-235">OUTPUTS</span></span>

### <span data-ttu-id="af95b-236">Geen, System. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="af95b-236">None, System.Diagnostics.Process</span></span>

<span data-ttu-id="af95b-237">Met deze cmdlet wordt een **System. Diagnostics. process** -object gegenereerd als u de para meter **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="af95b-237">This cmdlet generates a **System.Diagnostics.Process** object, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="af95b-238">Anders retourneert deze cmdlet geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="af95b-238">Otherwise, this cmdlet does not return any output.</span></span>

## <span data-ttu-id="af95b-239">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="af95b-239">NOTES</span></span>

- <span data-ttu-id="af95b-240">Deze cmdlet wordt geïmplementeerd met behulp van de methode **Start** van de klasse **System. Diagnostics. process** .</span><span class="sxs-lookup"><span data-stu-id="af95b-240">This cmdlet is implemented by using the **Start** method of the **System.Diagnostics.Process** class.</span></span> <span data-ttu-id="af95b-241">Zie [process. Start-methode](/dotnet/api/system.diagnostics.process.start#overloads)voor meer informatie over deze methode.</span><span class="sxs-lookup"><span data-stu-id="af95b-241">For more information about this method, see [Process.Start Method](/dotnet/api/system.diagnostics.process.start#overloads).</span></span>

- <span data-ttu-id="af95b-242">Wanneer u **UseNewEnvironment** gebruikt in Windows, begint het nieuwe proces alleen met de standaard omgevings variabelen die voor het **computer** bereik zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="af95b-242">On Windows, when you use **UseNewEnvironment** , the new process starts only containing the default environment variables defined for the **Machine** scope.</span></span> <span data-ttu-id="af95b-243">Dit is de zijde die van invloed is op de `$env:USERNAME` is ingesteld op **System**.</span><span class="sxs-lookup"><span data-stu-id="af95b-243">This has the side affect that the `$env:USERNAME` is set to **SYSTEM**.</span></span> <span data-ttu-id="af95b-244">Geen van de variabelen uit het **gebruikers** bereik is opgenomen.</span><span class="sxs-lookup"><span data-stu-id="af95b-244">None of the variables from the **User** scope are included.</span></span>

- <span data-ttu-id="af95b-245">In Windows is de meest voorkomende use-case voor het `Start-Process` gebruik van de **wait** -para meter om de voortgang te blok keren totdat het nieuwe proces wordt afgesloten.</span><span class="sxs-lookup"><span data-stu-id="af95b-245">On Windows, the most common use case for `Start-Process` is to use the **Wait** parameter to block progress until the new process exits.</span></span> <span data-ttu-id="af95b-246">Op niet-Windows-systemen is dit zelden nodig omdat het standaard gedrag voor opdracht regel toepassingen gelijk is aan `Start-Process -Wait` .</span><span class="sxs-lookup"><span data-stu-id="af95b-246">On non-Windows system, this is rarely needed since the default behavior for command-line applications is equivalent to `Start-Process -Wait`.</span></span>

- <span data-ttu-id="af95b-247">Wanneer `Start-Process` u op niet-Windows-systemen gebruikt, beschikt u nooit over een nieuw terminal venster.</span><span class="sxs-lookup"><span data-stu-id="af95b-247">When using `Start-Process` on non-Windows systems, you never get a new terminal window.</span></span>

## <span data-ttu-id="af95b-248">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="af95b-248">RELATED LINKS</span></span>

[<span data-ttu-id="af95b-249">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="af95b-249">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="af95b-250">Debug-proces</span><span class="sxs-lookup"><span data-stu-id="af95b-250">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="af95b-251">Get-Process</span><span class="sxs-lookup"><span data-stu-id="af95b-251">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="af95b-252">Start-Service</span><span class="sxs-lookup"><span data-stu-id="af95b-252">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="af95b-253">Stoppen-proces</span><span class="sxs-lookup"><span data-stu-id="af95b-253">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="af95b-254">Wacht proces</span><span class="sxs-lookup"><span data-stu-id="af95b-254">Wait-Process</span></span>](Wait-Process.md)
