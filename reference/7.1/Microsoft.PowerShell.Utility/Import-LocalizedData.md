---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-localizeddata?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-LocalizedData
ms.openlocfilehash: d19279133a42e3aea17f02348e44aec161ba5a23
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/03/2020
ms.locfileid: "93253298"
---
# <span data-ttu-id="00b52-103">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="00b52-103">Import-LocalizedData</span></span>

## <span data-ttu-id="00b52-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="00b52-104">SYNOPSIS</span></span>
<span data-ttu-id="00b52-105">Hiermee worden taalspecifieke gegevens in scripts en functies geïmporteerd op basis van de UI-cultuur die is geselecteerd voor het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="00b52-105">Imports language-specific data into scripts and functions based on the UI culture that is selected for the operating system.</span></span>

## <span data-ttu-id="00b52-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="00b52-106">SYNTAX</span></span>

```
Import-LocalizedData [[-BindingVariable] <String>] [[-UICulture] <String>] [-BaseDirectory <String>]
 [-FileName <String>] [-SupportedCommand <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="00b52-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="00b52-107">DESCRIPTION</span></span>

<span data-ttu-id="00b52-108">De `Import-LocalizedData` cmdlet haalt op dynamische wijze teken reeksen op uit een submap waarvan de naam overeenkomt met de taal van de gebruikers interface die is ingesteld voor de huidige gebruiker van het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="00b52-108">The `Import-LocalizedData` cmdlet dynamically retrieves strings from a subdirectory whose name matches the UI language set for the current user of the operating system.</span></span> <span data-ttu-id="00b52-109">Het is ontworpen om scripts in te scha kelen voor het weer geven van gebruikers berichten in de taal van de gebruikers interface die door de huidige gebruiker is geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="00b52-109">It is designed to enable scripts to display user messages in the UI language selected by the current user.</span></span>

<span data-ttu-id="00b52-110">`Import-LocalizedData``.psd1`Hiermee worden gegevens uit bestanden in taalspecifieke submappen van de script Directory geïmporteerd en opgeslagen in een lokale variabele die in de opdracht is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="00b52-110">`Import-LocalizedData` imports data from `.psd1` files in language-specific subdirectories of the script directory and saves them in a local variable that is specified in the command.</span></span> <span data-ttu-id="00b52-111">De cmdlet selecteert de submap en het bestand op basis van de waarde van de `$PSUICulture` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="00b52-111">The cmdlet selects the subdirectory and file based on the value of the `$PSUICulture` automatic variable.</span></span> <span data-ttu-id="00b52-112">Wanneer u de lokale variabele in het script gebruikt om een gebruikers bericht weer te geven, wordt het bericht weer gegeven in de gebruikers interface taal van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="00b52-112">When you use the local variable in the script to display a user message, the message appears in the user's UI language.</span></span>

<span data-ttu-id="00b52-113">U kunt de para meters van gebruiken `Import-LocalizedData` om een alternatieve UI-cultuur, pad en bestands naam op te geven om ondersteunde opdrachten toe te voegen en om het fout bericht te onderdrukken dat wordt weer gegeven als de `.psd1` bestanden niet worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="00b52-113">You can use the parameters of `Import-LocalizedData` to specify an alternate UI culture, path, and filename, to add supported commands, and to suppress the error message that appears if the `.psd1` files are not found.</span></span>

<span data-ttu-id="00b52-114">De `Import-LocalizedData` cmdlet ondersteunt het script voor de intertalen van scripts dat is geïntroduceerd in Windows Power shell 2,0.</span><span class="sxs-lookup"><span data-stu-id="00b52-114">The `Import-LocalizedData` cmdlet supports the script internationalization initiative that was introduced in Windows PowerShell 2.0.</span></span> <span data-ttu-id="00b52-115">Dit initiatief is erop gericht om gebruikers wereld wijd beter van dienst te zijn door scripts in staat te stellen gebruikers berichten te laten weer geven in de taal van de gebruikers interface van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="00b52-115">This initiative aims to better serve users worldwide by making it easy for scripts to display user messages in the UI language of the current user.</span></span> <span data-ttu-id="00b52-116">Zie about_Script_Internationalization voor meer informatie over deze en de indeling van de `.psd1` bestanden. [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md)</span><span class="sxs-lookup"><span data-stu-id="00b52-116">For more information about this and about the format of the `.psd1` files, see [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).</span></span>

## <span data-ttu-id="00b52-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="00b52-117">EXAMPLES</span></span>

### <span data-ttu-id="00b52-118">Voor beeld 1: tekst reeksen importeren</span><span class="sxs-lookup"><span data-stu-id="00b52-118">Example 1: Import text strings</span></span>

<span data-ttu-id="00b52-119">In dit voor beeld worden tekst reeksen in de `$Messages` variabele geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="00b52-119">This example imports text strings into the `$Messages` variable.</span></span> <span data-ttu-id="00b52-120">De standaard waarden van alle andere cmdlet-para meters worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="00b52-120">It uses the default values of all other cmdlet parameters.</span></span>

```powershell
Import-LocalizedData -BindingVariable "Messages"
```

<span data-ttu-id="00b52-121">Als de opdracht is opgenomen in het Archives.ps1 script in de `C:\Test` map en de waarde van de `$PsUICulture` Automatische variabele is zh-cn, `Import-LocalizedData` importeert het `Archives.psd1` bestand in de map in de- `C:\test\zh-CN` `$Messages` variabele.</span><span class="sxs-lookup"><span data-stu-id="00b52-121">If the command is included in the Archives.ps1 script in the `C:\Test` directory, and the value of the `$PsUICulture` automatic variable is zh-CN, `Import-LocalizedData` imports the `Archives.psd1` file in the `C:\test\zh-CN` directory into the `$Messages` variable.</span></span>

### <span data-ttu-id="00b52-122">Voor beeld 2: gelokaliseerde gegevens reeksen importeren</span><span class="sxs-lookup"><span data-stu-id="00b52-122">Example 2: Import localized data strings</span></span>

<span data-ttu-id="00b52-123">Dit voor beeld wordt uitgevoerd op de opdracht regel, niet in een script.</span><span class="sxs-lookup"><span data-stu-id="00b52-123">This example is run at the command line not in a script.</span></span> <span data-ttu-id="00b52-124">De gelokaliseerde gegevens reeksen worden opgehaald uit het bestand Test.psd1 en weer gegeven op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="00b52-124">It gets localized data strings from the Test.psd1 file and displays them at the command line.</span></span> <span data-ttu-id="00b52-125">Omdat de opdracht niet in een script wordt gebruikt, is de **filename** -para meter vereist.</span><span class="sxs-lookup"><span data-stu-id="00b52-125">Because the command is not used in a script, the **FileName** parameter is required.</span></span> <span data-ttu-id="00b52-126">De opdracht gebruikt de para meter **uiCulture** om de-en-US-cultuur op te geven.</span><span class="sxs-lookup"><span data-stu-id="00b52-126">The command uses the **UICulture** parameter to specify the en-US culture.</span></span>

```powershell
Import-LocalizedData -FileName "Test.psd1" -UICulture "en-US"
```

```Output
Name                           Value
----                           -----
Msg3                           "Use $_ to represent the object that is being processed."
Msg2                           "This command requires the credentials of a member of the Administrators group on the...
Msg1                           "The Name parameter is missing from the command."
```

<span data-ttu-id="00b52-127">`Import-LocalizedData` retourneert een hash-tabel die de gelokaliseerde gegevens reeksen bevat.</span><span class="sxs-lookup"><span data-stu-id="00b52-127">`Import-LocalizedData` returns a hash table that contains the localized data strings.</span></span>

### <span data-ttu-id="00b52-128">Voor beeld 3: UI-cultuur teken reeksen importeren</span><span class="sxs-lookup"><span data-stu-id="00b52-128">Example 3: Import UI culture strings</span></span>

```powershell
Import-LocalizedData -BindingVariable "MsgTbl" -UICulture "ar-SA" -FileName "Simple" -BaseDirectory "C:\Data\Localized"
```

<span data-ttu-id="00b52-129">Met deze opdracht worden tekst teken reeksen in de `$MsgTbl` variabele van een script geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="00b52-129">This command imports text strings into the `$MsgTbl` variable of a script.</span></span>

<span data-ttu-id="00b52-130">De para meter **uiCulture** wordt gebruikt om de cmdlet te gebruiken voor het importeren van gegevens uit het `Simple.psd1` bestand in de `ar-SA` submap van `C:\Data\Localized` .</span><span class="sxs-lookup"><span data-stu-id="00b52-130">It uses the **UICulture** parameter to direct the cmdlet to import data from the `Simple.psd1` file in the `ar-SA` subdirectory of `C:\Data\Localized`.</span></span>

### <span data-ttu-id="00b52-131">Voor beeld 4: gelokaliseerde gegevens in een script importeren</span><span class="sxs-lookup"><span data-stu-id="00b52-131">Example 4: Import localized data into a script</span></span>

<span data-ttu-id="00b52-132">In dit voor beeld ziet u hoe u gelokaliseerde gegevens in een eenvoudig script gebruikt.</span><span class="sxs-lookup"><span data-stu-id="00b52-132">This example shows how to use localized data in a simple script.</span></span>

```powershell
PS C:\> # In C:\Test\en-US\Test.psd1:

ConvertFrom-StringData @'

# English strings

Msg1 = "The Name parameter is missing from the command."
Msg2 = "This command requires the credentials of a member of the Administrators group on the computer."
Msg3 = "Use $_ to represent the object that is being processed."
'@

# In C:\Test\Test.ps1

Import-LocalizedData -BindingVariable "Messages"
Write-Host $Messages.Msg2

# In Windows PowerShell

PS C:\> .\Test.ps1

This command requires the credentials of a member of the Administrators group on the computer.
```

<span data-ttu-id="00b52-133">In het eerste deel van het voor beeld ziet u de inhoud van het `Test.psd1` bestand.</span><span class="sxs-lookup"><span data-stu-id="00b52-133">The first part of the example shows the contents of the `Test.psd1` file.</span></span> <span data-ttu-id="00b52-134">Het bevat een `ConvertFrom-StringData` opdracht die een reeks benoemde teken reeksen converteert naar een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="00b52-134">It contains a `ConvertFrom-StringData` command that converts a series of named text strings into a hash table.</span></span> <span data-ttu-id="00b52-135">Het `Test.psd1` bestand bevindt zich in de submap en-US van de `C:\Test` map die het script bevat.</span><span class="sxs-lookup"><span data-stu-id="00b52-135">The `Test.psd1` file is located in the en-US subdirectory of the `C:\Test` directory that contains the script.</span></span>

<span data-ttu-id="00b52-136">In het tweede gedeelte van het voor beeld ziet u de inhoud van het `Test.ps1` script.</span><span class="sxs-lookup"><span data-stu-id="00b52-136">The second part of the example shows the contents of the `Test.ps1` script.</span></span> <span data-ttu-id="00b52-137">Het bevat een `Import-LocalizedData` opdracht waarmee de gegevens uit het overeenkomende `.psd1` bestand worden geïmporteerd in de `$Messages` variabele en een `Write-Host` opdracht waarmee een van de berichten in de `$Messages` variabele naar het hostprogramma wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="00b52-137">It contains an `Import-LocalizedData` command that imports the data from the matching `.psd1` file into the `$Messages` variable and a `Write-Host` command that writes one of the messages in the `$Messages` variable to the host program.</span></span>

<span data-ttu-id="00b52-138">In het laatste deel van het voor beeld wordt het script uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="00b52-138">The last part of the example runs the script.</span></span> <span data-ttu-id="00b52-139">In de uitvoer ziet u dat het juiste gebruikers bericht wordt weer gegeven in de taalset van de gebruikers interface voor de huidige gebruiker van het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="00b52-139">The output shows that it displays the correct user message in the UI language set for the current user of the operating system.</span></span>

### <span data-ttu-id="00b52-140">Voor beeld 5: standaard teken reeksen in een script vervangen</span><span class="sxs-lookup"><span data-stu-id="00b52-140">Example 5: Replace default text strings in a script</span></span>

<span data-ttu-id="00b52-141">In dit voor beeld ziet u hoe u kunt gebruiken `Import-LocalizedData` om standaard teken reeksen te vervangen die zijn gedefinieerd in de sectie gegevens van een script.</span><span class="sxs-lookup"><span data-stu-id="00b52-141">This example shows how to use `Import-LocalizedData` to replace default text strings defined in the DATA section of a script.</span></span>

```powershell
PS C:\> # In TestScript.ps1
$UserMessages = DATA

{    ConvertFrom-StringData @'

    # English strings

        Msg1 = "Enter a name."
        Msg2 = "Enter your employee ID."
        Msg3 = "Enter your building number."
'@
}

Import-LocalizedData -BindingVariable "UserMessages"
$UserMessages.Msg1...
```

<span data-ttu-id="00b52-142">In dit voor beeld bevat de sectie gegevens van het TestScript.ps1 script een `ConvertFrom-StringData` opdracht waarmee de inhoud van de sectie gegevens wordt geconverteerd naar een hash-tabel en die wordt opgeslagen in de waarde van de `$UserMessages` variabele.</span><span class="sxs-lookup"><span data-stu-id="00b52-142">In this example, the DATA section of the TestScript.ps1 script contains a `ConvertFrom-StringData` command that converts the contents of the DATA section to a hash table and stores in the value of the `$UserMessages` variable.</span></span>

<span data-ttu-id="00b52-143">Het script bevat ook een `Import-LocalizedData` opdracht, waarmee een hash-tabel met vertaalde tekst reeksen uit het TestScript.psd1-bestand in de submap die wordt opgegeven door de waarde van de variabele wordt geïmporteerd `$PsUICulture` .</span><span class="sxs-lookup"><span data-stu-id="00b52-143">The script also includes an `Import-LocalizedData` command, which imports a hash table of translated text strings from the TestScript.psd1 file in the subdirectory specified by the value of the `$PsUICulture` variable.</span></span> <span data-ttu-id="00b52-144">Als de opdracht het `.psd1` bestand vindt, worden de vertaalde teken reeksen uit het bestand opgeslagen in de waarde van dezelfde `$UserMessages` variabele, waarbij de hash-tabel wordt overschreven die is opgeslagen door de logica van de gegevens sectie.</span><span class="sxs-lookup"><span data-stu-id="00b52-144">If the command finds the `.psd1` file, it saves the translated strings from the file in the value of the same `$UserMessages` variable, overwriting the hash table saved by the DATA section logic.</span></span>

<span data-ttu-id="00b52-145">Met de derde opdracht wordt het eerste bericht in de variabele weer gegeven `$UserMessages` .</span><span class="sxs-lookup"><span data-stu-id="00b52-145">The third command displays the first message in the `$UserMessages` variable.</span></span>

<span data-ttu-id="00b52-146">Als de `Import-LocalizedData` opdracht een `.psd1` bestand voor de `$PsUICulture` taal vindt, bevat de waarde van de `$UserMessages` variabele de vertaalde teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="00b52-146">If the `Import-LocalizedData` command finds a `.psd1` file for the `$PsUICulture` language, the value of the `$UserMessages` variable contains the translated text strings.</span></span> <span data-ttu-id="00b52-147">Als de opdracht om welke reden dan ook mislukt, geeft de opdracht de standaard teken reeksen weer die zijn gedefinieerd in de sectie gegevens van het script.</span><span class="sxs-lookup"><span data-stu-id="00b52-147">If the command fails for any reason, the command displays the default text strings defined in the DATA section of the script.</span></span>

### <span data-ttu-id="00b52-148">Voor beeld 6: fout berichten onderdrukken als de GEBRUIKERSINTERFACE cultuur niet wordt gevonden</span><span class="sxs-lookup"><span data-stu-id="00b52-148">Example 6: Suppress error messages if the UI culture is not found</span></span>

<span data-ttu-id="00b52-149">In dit voor beeld ziet u hoe u de fout berichten onderdrukt die worden weer gegeven wanneer u `Import-LocalizedData` de mappen die overeenkomen met de gebruikers interface-cultuur van de gebruiker niet kunt vinden of geen `.psd1` bestanden voor het script in deze mappen kunt vinden.</span><span class="sxs-lookup"><span data-stu-id="00b52-149">This example shows how to suppress the error messages that appear when `Import-LocalizedData` cannot find the directories that match the user's UI culture or cannot find a `.psd1` file for the script in those directories.</span></span>

```powershell
PS C:\> # In Day1.ps1

Import-LocalizedData -BindingVariable "Day"

# In Day2.ps1

Import-LocalizedData -BindingVariable "Day" -ErrorAction:SilentlyContinue

PS C:\> .\Day1.ps1
Import-LocalizedData : Cannot find PowerShell data file 'Day1.psd1' in directory 'C:\ps-test\fr-BE\' or any parent culture directories.
At C:\ps-test\Day1.ps1:17 char:21+ Import-LocalizedData <<<<  Day
Today is Tuesday

PS C:\> .\Day2.ps1
Today is Tuesday
```

<span data-ttu-id="00b52-150">U kunt de gemeen schappelijke para meter **Error Action** met de waarde SilentlyContinue gebruiken om het fout bericht te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="00b52-150">You can use the **ErrorAction** common parameter with a value of SilentlyContinue to suppress the error message.</span></span> <span data-ttu-id="00b52-151">Dit is vooral handig wanneer u gebruikers berichten hebt gegeven in een standaard-of terugval taal en er geen fout berichten nodig zijn.</span><span class="sxs-lookup"><span data-stu-id="00b52-151">This is especially useful when you have provided user messages in a default or fallback language, and no error message is needed.</span></span>

<span data-ttu-id="00b52-152">In dit voor beeld worden twee scripts vergeleken `Day1.ps1` en Day2.ps1, die een `Import-LocalizedData` opdracht bevatten.</span><span class="sxs-lookup"><span data-stu-id="00b52-152">This example compares two scripts, `Day1.ps1` and Day2.ps1, that include an `Import-LocalizedData` command.</span></span> <span data-ttu-id="00b52-153">De scripts zijn identiek, behalve dat Day2 de gemeen schappelijke para meter **Error Action** gebruikt met een waarde van `SilentlyContinue` .</span><span class="sxs-lookup"><span data-stu-id="00b52-153">The scripts are identical, except that Day2 uses the **ErrorAction** common parameter with a value of `SilentlyContinue`.</span></span>

<span data-ttu-id="00b52-154">De voorbeeld uitvoer toont de resultaten van het uitvoeren van beide scripts wanneer de GEBRUIKERSINTERFACE cultuur is ingesteld op `fr-BE` en er zijn geen overeenkomende bestanden of mappen voor die gebruikersinterface cultuur.</span><span class="sxs-lookup"><span data-stu-id="00b52-154">The sample output shows the results of running both scripts when the UI culture is set to `fr-BE` and there are no matching files or directories for that UI culture.</span></span> <span data-ttu-id="00b52-155">`Day1.ps1` Hiermee wordt een fout bericht en een Engelse uitvoer weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="00b52-155">`Day1.ps1` displays an error message and English output.</span></span> <span data-ttu-id="00b52-156">`Day2.ps1` Hiermee wordt alleen de Engelse uitvoer weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="00b52-156">`Day2.ps1` just displays the English output.</span></span>

## <span data-ttu-id="00b52-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="00b52-157">PARAMETERS</span></span>

### <span data-ttu-id="00b52-158">-BaseDirectory</span><span class="sxs-lookup"><span data-stu-id="00b52-158">-BaseDirectory</span></span>

<span data-ttu-id="00b52-159">Hiermee geeft u de basis directory op waarin de `.psd1` bestanden zich bevinden.</span><span class="sxs-lookup"><span data-stu-id="00b52-159">Specifies the base directory where the `.psd1` files are located.</span></span> <span data-ttu-id="00b52-160">De standaard waarde is de map waarin het script zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="00b52-160">The default is the directory where the script is located.</span></span> <span data-ttu-id="00b52-161">`Import-LocalizedData` zoekt naar het `.psd1` bestand voor het script in een taalspecifieke submap van de basis directory.</span><span class="sxs-lookup"><span data-stu-id="00b52-161">`Import-LocalizedData` searches for the `.psd1` file for the script in a language-specific subdirectory of the base directory.</span></span>

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

### <span data-ttu-id="00b52-162">-BindingVariable</span><span class="sxs-lookup"><span data-stu-id="00b52-162">-BindingVariable</span></span>

<span data-ttu-id="00b52-163">Hiermee geeft u de variabele op waarnaar de tekst teken reeksen worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="00b52-163">Specifies the variable into which the text strings are imported.</span></span> <span data-ttu-id="00b52-164">Voer een variabelenaam in zonder een dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="00b52-164">Enter a variable name without a dollar sign (`$`).</span></span>

<span data-ttu-id="00b52-165">In Windows Power Shell 2,0 is deze para meter vereist.</span><span class="sxs-lookup"><span data-stu-id="00b52-165">In Windows PowerShell 2.0, this parameter is required.</span></span> <span data-ttu-id="00b52-166">In Windows Power Shell 3,0 is deze para meter optioneel.</span><span class="sxs-lookup"><span data-stu-id="00b52-166">In Windows PowerShell 3.0, this parameter is optional.</span></span> <span data-ttu-id="00b52-167">Als u deze para meter weglaat, `Import-LocalizedData` wordt een hash-tabel van de tekst teken reeksen geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="00b52-167">If you omit this parameter, `Import-LocalizedData` returns a hash table of the text strings.</span></span> <span data-ttu-id="00b52-168">De hash-tabel wordt door gegeven aan de pijp lijn of wordt weer gegeven op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="00b52-168">The hash table is passed down the pipeline or displayed at the command line.</span></span>

<span data-ttu-id="00b52-169">Wanneer u gebruikt `Import-LocalizedData` om standaard teken reeksen te vervangen die zijn opgegeven in de sectie gegevens van een script, wijst u de sectie gegevens toe aan een variabele en voert u de naam van de gegevens sectie variabele in de waarde van de para meter **BindingVariable** .</span><span class="sxs-lookup"><span data-stu-id="00b52-169">When using `Import-LocalizedData` to replace default text strings specified in the DATA section of a script, assign the DATA section to a variable and enter the name of the DATA section variable in the value of the **BindingVariable** parameter.</span></span> <span data-ttu-id="00b52-170">Wanneer `Import-LocalizedData` de geïmporteerde inhoud in de **BindingVariable** opslaat, worden de standaard teken reeksen vervangen door de geïmporteerde gegevens.</span><span class="sxs-lookup"><span data-stu-id="00b52-170">Then, when `Import-LocalizedData` saves the imported content in the **BindingVariable** , the imported data will replace the default text strings.</span></span> <span data-ttu-id="00b52-171">Als u geen standaard teken reeksen opgeeft, kunt u elke naam van een variabele selecteren.</span><span class="sxs-lookup"><span data-stu-id="00b52-171">If you are not specifying default text strings, you can select any variable name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Variable

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00b52-172">-FileName</span><span class="sxs-lookup"><span data-stu-id="00b52-172">-FileName</span></span>

<span data-ttu-id="00b52-173">Hiermee geeft u de naam op van het gegevens bestand ( `.psd1)` dat moet worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="00b52-173">Specifies the name of the data file (`.psd1)` to be imported.</span></span> <span data-ttu-id="00b52-174">Voer een bestands naam in.</span><span class="sxs-lookup"><span data-stu-id="00b52-174">Enter a file name.</span></span> <span data-ttu-id="00b52-175">U kunt een bestands naam opgeven die niet de `.psd1` bestandsnaam extensie bevat, of u kunt de bestands naam opgeven, inclusief de `.psd1` bestandsnaam extensie.</span><span class="sxs-lookup"><span data-stu-id="00b52-175">You can specify a file name that does not include its `.psd1` file name extension, or you can specify the file name including the `.psd1` file name extension.</span></span> <span data-ttu-id="00b52-176">Gegevens bestanden moeten worden opgeslagen als Unicode-of UTF-8.</span><span class="sxs-lookup"><span data-stu-id="00b52-176">Data files should be saved as Unicode or UTF-8.</span></span>

<span data-ttu-id="00b52-177">De **filename** -para meter is vereist wanneer `Import-LocalizedData` niet wordt gebruikt in een script.</span><span class="sxs-lookup"><span data-stu-id="00b52-177">The **FileName** parameter is required when `Import-LocalizedData` is not used in a script.</span></span>
<span data-ttu-id="00b52-178">Anders is de para meter optioneel en de standaard waarde is de basis naam van het script.</span><span class="sxs-lookup"><span data-stu-id="00b52-178">Otherwise, the parameter is optional and the default value is the base name of the script.</span></span> <span data-ttu-id="00b52-179">U kunt deze para meter gebruiken om rechtstreeks `Import-LocalizedData` naar een ander bestand te zoeken `.psd1` .</span><span class="sxs-lookup"><span data-stu-id="00b52-179">You can use this parameter to direct `Import-LocalizedData` to search for a different `.psd1` file.</span></span>

<span data-ttu-id="00b52-180">Als bijvoorbeeld de **Bestands** naam wordt wegge laten en de script naam is FindFiles.ps1, wordt `Import-LocalizedData` gezocht naar het FindFiles.psd1-gegevens bestand.</span><span class="sxs-lookup"><span data-stu-id="00b52-180">For example, if the **FileName** is omitted and the script name is FindFiles.ps1, `Import-LocalizedData` searches for the FindFiles.psd1 data file.</span></span>

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

### <span data-ttu-id="00b52-181">-SupportedCommand</span><span class="sxs-lookup"><span data-stu-id="00b52-181">-SupportedCommand</span></span>

<span data-ttu-id="00b52-182">Hiermee geeft u cmdlets en functies op waarmee alleen gegevens worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="00b52-182">Specifies cmdlets and functions that generate only data.</span></span>

<span data-ttu-id="00b52-183">Gebruik deze para meter als u cmdlets en functies wilt gebruiken die u hebt geschreven of getest.</span><span class="sxs-lookup"><span data-stu-id="00b52-183">Use this parameter to include cmdlets and functions that you have written or tested.</span></span> <span data-ttu-id="00b52-184">Zie [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="00b52-184">For more information, see [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00b52-185">-UICulture</span><span class="sxs-lookup"><span data-stu-id="00b52-185">-UICulture</span></span>

<span data-ttu-id="00b52-186">Hiermee geeft u een alternatieve GEBRUIKERSINTERFACE cultuur.</span><span class="sxs-lookup"><span data-stu-id="00b52-186">Specifies an alternate UI culture.</span></span>
<span data-ttu-id="00b52-187">De standaard instelling is de waarde van de `$PsUICulture` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="00b52-187">The default is the value of the `$PsUICulture` automatic variable.</span></span>
<span data-ttu-id="00b52-188">Voer een GEBRUIKERSINTERFACE cultuur in `<language>-<region>` indeling in, zoals `en-US` , `de-DE` of `ar-SA` .</span><span class="sxs-lookup"><span data-stu-id="00b52-188">Enter a UI culture in `<language>-<region>` format, such as `en-US`, `de-DE`, or `ar-SA`.</span></span>

<span data-ttu-id="00b52-189">De waarde van de para meter **uiCulture** bepaalt de taalspecifieke submap (binnen de basis directory) waaruit `Import-LocalizedData` het `.psd1` bestand voor het script wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="00b52-189">The value of the **UICulture** parameter determines the language-specific subdirectory (within the base directory) from which `Import-LocalizedData` gets the `.psd1` file for the script.</span></span>

<span data-ttu-id="00b52-190">De cmdlet zoekt naar een submap met dezelfde naam als de waarde van de para meter **uiCulture** of de `$PsUICulture` Automatische variabele, zoals `de-DE` of `ar-SA` .</span><span class="sxs-lookup"><span data-stu-id="00b52-190">The cmdlet searches for a subdirectory with the same name as the value of the **UICulture** parameter or the `$PsUICulture` automatic variable, such as `de-DE` or `ar-SA`.</span></span> <span data-ttu-id="00b52-191">Als de Directory niet kan worden gevonden of als de map geen `.psd1` bestand voor het script bevat, wordt gezocht naar een submap met de naam van de taal code, zoals de of AR.</span><span class="sxs-lookup"><span data-stu-id="00b52-191">If it cannot find the directory, or the directory does not contain a `.psd1` file for the script, it searches for a subdirectory with the name of the language code, such as de or ar.</span></span> <span data-ttu-id="00b52-192">Als de submap of het bestand niet kan worden gevonden `.psd1` , mislukt de opdracht en worden de gegevens weer gegeven in de standaard taal die is opgegeven in het script.</span><span class="sxs-lookup"><span data-stu-id="00b52-192">If it cannot find the subdirectory or `.psd1` file, the command fails and the data is displayed in the default language specified in the script.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00b52-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="00b52-193">CommonParameters</span></span>

<span data-ttu-id="00b52-194">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="00b52-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="00b52-195">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="00b52-195">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="00b52-196">INVOER</span><span class="sxs-lookup"><span data-stu-id="00b52-196">INPUTS</span></span>

### <span data-ttu-id="00b52-197">Geen</span><span class="sxs-lookup"><span data-stu-id="00b52-197">None</span></span>

<span data-ttu-id="00b52-198">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="00b52-198">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="00b52-199">UITVOER</span><span class="sxs-lookup"><span data-stu-id="00b52-199">OUTPUTS</span></span>

### <span data-ttu-id="00b52-200">System. Collections. hashtabel</span><span class="sxs-lookup"><span data-stu-id="00b52-200">System.Collections.Hashtable</span></span>

<span data-ttu-id="00b52-201">`Import-LocalizedData` Hiermee slaat u de hash-tabel op in de variabele die wordt opgegeven door de waarde van de para meter **BindingVariable** .</span><span class="sxs-lookup"><span data-stu-id="00b52-201">`Import-LocalizedData` saves the hash table in the variable that is specified by the value of the **BindingVariable** parameter.</span></span>

## <span data-ttu-id="00b52-202">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="00b52-202">NOTES</span></span>

- <span data-ttu-id="00b52-203">`Import-LocalizedData`Lokaliseer uw gebruikers berichten voordat u deze gebruikt.</span><span class="sxs-lookup"><span data-stu-id="00b52-203">Before using `Import-LocalizedData`, localize your user messages.</span></span> <span data-ttu-id="00b52-204">Format teer de berichten voor elke land instelling (UI-cultuur) in een hash-tabel met sleutel-waardeparen en sla de hash-tabel op in een bestand met dezelfde naam als het script en de `.psd1` bestandsnaam extensie.</span><span class="sxs-lookup"><span data-stu-id="00b52-204">Format the messages for each locale (UI culture) in a hash table of key-value pairs, and save the hash table in a file with the same name as the script and a `.psd1` file name extension.</span></span> <span data-ttu-id="00b52-205">Maak een map onder de script Directory voor elke ondersteunde UI-cultuur en sla het `.psd1` bestand op voor elke UI-cultuur in de directory met de naam van de UI-cultuur.</span><span class="sxs-lookup"><span data-stu-id="00b52-205">Create a directory under the script directory for each supported UI culture, and then save the `.psd1` file for each UI culture in the directory with the UI culture name.</span></span>

  <span data-ttu-id="00b52-206">U kunt bijvoorbeeld uw gebruikers berichten lokaliseren voor de land instelling en Format teren in een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="00b52-206">For example, localize your user messages for the de-DE locale and format them in a hash table.</span></span>
  <span data-ttu-id="00b52-207">Sla de hash-tabel op in een `<ScriptName>.psd1` bestand.</span><span class="sxs-lookup"><span data-stu-id="00b52-207">Save the hash table in a `<ScriptName>.psd1` file.</span></span> <span data-ttu-id="00b52-208">Maak vervolgens een `de-DE` submap onder de script Directory en sla het Duitse `<ScriptName\>.psd1` bestand op in de `de-DE` submap.</span><span class="sxs-lookup"><span data-stu-id="00b52-208">Then create a `de-DE` subdirectory under the script directory, and save the German `<ScriptName\>.psd1` file in the `de-DE` subdirectory.</span></span>
  <span data-ttu-id="00b52-209">Herhaal deze methode voor elke land instelling die u ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="00b52-209">Repeat this method for each locale that you support.</span></span>

- <span data-ttu-id="00b52-210">`Import-LocalizedData` Hiermee voert u een gestructureerde zoek opdracht uit voor de gelokaliseerde gebruikers berichten voor een script.</span><span class="sxs-lookup"><span data-stu-id="00b52-210">`Import-LocalizedData` performs a structured search for the localized user messages for a script.</span></span>

  <span data-ttu-id="00b52-211">`Import-LocalizedData` Start de zoek opdracht in de directory waarin het script bestand zich bevindt (of de waarde van de para meter **BaseDirectory** ).</span><span class="sxs-lookup"><span data-stu-id="00b52-211">`Import-LocalizedData` begins the search in the directory where the script file is located (or the value of the **BaseDirectory** parameter).</span></span> <span data-ttu-id="00b52-212">Vervolgens wordt gezocht in de basis directory voor een submap met dezelfde naam als de waarde van de `$PsUICulture` variabele (of de waarde van de para meter **uiCulture** ), zoals `de-DE` of `ar-SA` .</span><span class="sxs-lookup"><span data-stu-id="00b52-212">It then searches within the base directory for a subdirectory with the same name as the value of the `$PsUICulture` variable (or the value of the **UICulture** parameter), such as `de-DE` or `ar-SA`.</span></span> <span data-ttu-id="00b52-213">Vervolgens wordt in die submap gezocht naar een `.psd1` bestand met dezelfde naam als het script (of de waarde van de **filename** -para meter).</span><span class="sxs-lookup"><span data-stu-id="00b52-213">Then, it searches in that subdirectory for a `.psd1` file with the same name as the script (or the value of the **FileName** parameter).</span></span>

  <span data-ttu-id="00b52-214">Als `Import-LocalizedData` u een submap met de naam van de UI-cultuur niet kunt vinden of de submap bevat geen `.psd1` bestand voor het script, zoekt het naar een `.psd1` bestand voor het script in een submap met de naam van de taal code, zoals de of AR.</span><span class="sxs-lookup"><span data-stu-id="00b52-214">If `Import-LocalizedData` cannot find a subdirectory with the name of the UI culture, or the subdirectory does not contain a `.psd1` file for the script, it searches for a `.psd1` file for the script in a subdirectory with the name of the language code, such as de or ar.</span></span> <span data-ttu-id="00b52-215">Als de submap of het bestand niet kan worden gevonden `.psd1` , mislukt de opdracht, worden de gegevens weer gegeven in de standaard taal in het script en wordt er een fout bericht weer gegeven waarin wordt uitgelegd dat de gegevens niet kunnen worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="00b52-215">If it cannot find the subdirectory or `.psd1` file, the command fails, the data is displayed in the default language in the script, and an error message is displayed explaining that the data could not be imported.</span></span> <span data-ttu-id="00b52-216">Als u het bericht wilt onderdrukken en niet goed wilt werken, gebruikt u de gemeen schappelijke **Error Action** -para meter met de waarde SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="00b52-216">To suppress the message and fail gracefully, use the **ErrorAction** common parameter with a value of SilentlyContinue.</span></span>

  <span data-ttu-id="00b52-217">Als `Import-LocalizedData` de submap en het `.psd1` bestand worden gevonden, wordt de hash-tabel met gebruikers berichten geïmporteerd in de waarde van de para meter **BindingVariable** in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="00b52-217">If `Import-LocalizedData` finds the subdirectory and the `.psd1` file, it imports the hash table of user messages into the value of the **BindingVariable** parameter in the command.</span></span> <span data-ttu-id="00b52-218">Wanneer u vervolgens een bericht uit de hash-tabel weergeeft in de variabele, wordt het gelokaliseerde bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="00b52-218">Then, when you display a message from the hash table in the variable, the localized message is displayed.</span></span>

  <span data-ttu-id="00b52-219">Zie [about_Script_Internationalization](../Microsoft.Powershell.Core/About/about_Script_Internationalization.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="00b52-219">For more information, see [about_Script_Internationalization](../Microsoft.Powershell.Core/About/about_Script_Internationalization.md).</span></span>

## <span data-ttu-id="00b52-220">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="00b52-220">RELATED LINKS</span></span>

[<span data-ttu-id="00b52-221">Write-host</span><span class="sxs-lookup"><span data-stu-id="00b52-221">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="00b52-222">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="00b52-222">Import-PowerShellDataFile</span></span>](Import-PowerShellDataFile.md)
