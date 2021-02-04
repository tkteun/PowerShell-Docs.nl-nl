---
description: Hierin worden de functies voor script intertalen beschreven waarmee scripts eenvoudig berichten en instructies voor gebruikers worden weer gegeven in de taal van de gebruikers interface (UI).
Locale: en-US
ms.date: 03/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_internationalization?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Internationalization
ms.openlocfilehash: 283ea6788e76b481c912fc5672350efd2e8bafaa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706209"
---
# <a name="about-script-internationalization"></a><span data-ttu-id="98104-103">Over script intertalen</span><span class="sxs-lookup"><span data-stu-id="98104-103">About Script Internationalization</span></span>

## <a name="short-description"></a><span data-ttu-id="98104-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="98104-104">Short Description</span></span>
<span data-ttu-id="98104-105">Hierin worden de functies voor script intertalen beschreven waarmee scripts eenvoudig berichten en instructies voor gebruikers worden weer gegeven in de taal van de gebruikers interface (UI).</span><span class="sxs-lookup"><span data-stu-id="98104-105">Describes the script internationalization features that make it easy for scripts to display messages and instructions to users in their user interface (UI) language.</span></span>

## <a name="long-description"></a><span data-ttu-id="98104-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="98104-106">Long Description</span></span>

<span data-ttu-id="98104-107">Met de functies voor intertalen in Power shell-script kunt u gebruikers in de hele wereld beter van dienst zijn door Help-en gebruikers berichten in de taal van de gebruiker weer te geven.</span><span class="sxs-lookup"><span data-stu-id="98104-107">The PowerShell script internationalization features allow you to better serve users throughout the world by displaying help and user messages in the user's language.</span></span>

<span data-ttu-id="98104-108">De functies voor script intertalen voeren een query uit op de UI-cultuur van het besturings systeem tijdens de uitvoering, importeer de juiste vertaalde teken reeksen en geef deze weer in de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="98104-108">The script internationalization features query the UI culture of the operating system during execution, import the appropriate translated text strings, and display them to the user.</span></span> <span data-ttu-id="98104-109">Met de sectie gegevens kunt u tekst reeksen gescheiden van code opslaan, zodat ze gemakkelijk kunnen worden geïdentificeerd en geëxtraheerd.</span><span class="sxs-lookup"><span data-stu-id="98104-109">The Data section lets you store text strings separate from code so they are easily identified and extracted.</span></span> <span data-ttu-id="98104-110">Een nieuwe cmdlet, `ConvertFrom-StringData` , converteert teken reeksen naar woordenboek achtige hash-tabellen om de vertaling te vergemakkelijken.</span><span class="sxs-lookup"><span data-stu-id="98104-110">A new cmdlet, `ConvertFrom-StringData`, converts text strings into dictionary-like hash tables to facilitate translation.</span></span>

<span data-ttu-id="98104-111">Power shell bevat de volgende functies ter ondersteuning van internationale Help-tekst:</span><span class="sxs-lookup"><span data-stu-id="98104-111">To support international Help text, PowerShell includes the following features:</span></span>

- <span data-ttu-id="98104-112">Een gegevens sectie waarmee tekst reeksen worden gescheiden van code-instructies.</span><span class="sxs-lookup"><span data-stu-id="98104-112">A Data section that separates text strings from code instructions.</span></span> <span data-ttu-id="98104-113">Zie [about_Data_Sections](about_Data_Sections.md)voor meer informatie over de sectie gegevens.</span><span class="sxs-lookup"><span data-stu-id="98104-113">For more information about the Data section, see [about_Data_Sections](about_Data_Sections.md).</span></span>

- <span data-ttu-id="98104-114">Nieuwe automatische variabelen `$PSCulture` en `$PSUICulture` .</span><span class="sxs-lookup"><span data-stu-id="98104-114">New automatic variables, `$PSCulture` and `$PSUICulture`.</span></span> <span data-ttu-id="98104-115">`$PSCulture` slaat de naam op van de taal van de gebruikers interface die op het systeem wordt gebruikt voor elementen zoals de datum, tijd en valuta.</span><span class="sxs-lookup"><span data-stu-id="98104-115">`$PSCulture` stores the name of the UI language used on the system for elements such as the date, time, and currency.</span></span> <span data-ttu-id="98104-116">De `$PSUICulture` variabele bevat de naam van de taal van de gebruikers interface die op het systeem wordt gebruikt voor elementen van gebruikers interfaces, zoals menu's en tekst teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="98104-116">The `$PSUICulture` variable stores the name of the UI language used on the system for user interface elements such as menus and text strings.</span></span>

- <span data-ttu-id="98104-117">Een cmdlet, `ConvertFrom-StringData` , waarmee tekst reeksen worden geconverteerd naar woordenboek achtige hash-tabellen om de vertaling te vergemakkelijken.</span><span class="sxs-lookup"><span data-stu-id="98104-117">A cmdlet, `ConvertFrom-StringData`, that converts text strings into dictionary-like hash tables to facilitate translation.</span></span> <span data-ttu-id="98104-118">Zie [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="98104-118">For more information, see [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData).</span></span>

- <span data-ttu-id="98104-119">Een nieuw bestands type, `.psd1` dat vertaalde teken reeksen opslaat.</span><span class="sxs-lookup"><span data-stu-id="98104-119">A new file type, `.psd1`, that stores translated text strings.</span></span> <span data-ttu-id="98104-120">De `.psd1` bestanden worden opgeslagen in taalspecifieke submappen van de script Directory.</span><span class="sxs-lookup"><span data-stu-id="98104-120">The `.psd1` files are stored in language-specific subdirectories of the script directory.</span></span>

- <span data-ttu-id="98104-121">Een cmdlet, `Import-LocalizedData` , waarmee de vertaalde teken reeksen voor een opgegeven taal worden geïmporteerd in een script tijdens runtime.</span><span class="sxs-lookup"><span data-stu-id="98104-121">A cmdlet, `Import-LocalizedData`, that imports translated text strings for a specified language into a script at runtime.</span></span> <span data-ttu-id="98104-122">Met deze cmdlet worden teken reeksen in een door Windows ondersteunde taal herkend en geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="98104-122">This cmdlet recognizes and imports strings in any Windows-supported language.</span></span> <span data-ttu-id="98104-123">Zie [import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="98104-123">For more information see [Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData).</span></span>

### <a name="the-data-section-storing-default-strings"></a><span data-ttu-id="98104-124">De sectie gegevens: standaard reeksen opslaan</span><span class="sxs-lookup"><span data-stu-id="98104-124">The Data Section: Storing Default Strings</span></span>

<span data-ttu-id="98104-125">Gebruik een gegevens sectie in het script om de teken reeksen in de standaard taal op te slaan.</span><span class="sxs-lookup"><span data-stu-id="98104-125">Use a Data section in the script to store the text strings in the default language.</span></span> <span data-ttu-id="98104-126">Rang Schik de teken reeksen in sleutel-waardeparen in een hier-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="98104-126">Arrange the strings in key/value pairs in a here-string.</span></span> <span data-ttu-id="98104-127">Elke sleutel/waarde-paar moet op een afzonderlijke regel staan.</span><span class="sxs-lookup"><span data-stu-id="98104-127">Each key/value pair must be on a separate line.</span></span> <span data-ttu-id="98104-128">Als u opmerkingen toevoegt, moeten de opmerkingen op afzonderlijke regels staan.</span><span class="sxs-lookup"><span data-stu-id="98104-128">If you include comments, the comments must be on separate lines.</span></span>

<span data-ttu-id="98104-129">Met de `ConvertFrom-StringData` cmdlet worden de sleutel-waardeparen in de hier-teken reeks geconverteerd naar een woordenboek achtige hash-tabel die is opgeslagen in de waarde van de variabele gegevens sectie.</span><span class="sxs-lookup"><span data-stu-id="98104-129">The `ConvertFrom-StringData` cmdlet converts the key/value pairs in the here-string into a dictionary-like hash table that is stored in the value of the Data section variable.</span></span>

<span data-ttu-id="98104-130">In het volgende voor beeld bevat de sectie gegevens van het `World.ps1` script de English-United Staten (en-US) die zijn ingesteld op prompt berichten voor een script.</span><span class="sxs-lookup"><span data-stu-id="98104-130">In the following example, the Data section of the `World.ps1` script includes the English-United States (en-US) set of prompt messages for a script.</span></span> <span data-ttu-id="98104-131">`ConvertFrom-StringData`Met de cmdlet worden de teken reeksen omgezet in een hash-tabel en opgeslagen in de `$msgtable` variabele.</span><span class="sxs-lookup"><span data-stu-id="98104-131">The `ConvertFrom-StringData` cmdlet converts the strings into a hash table and stores them in the `$msgtable` variable.</span></span>

```powershell
$msgTable = Data {
    #culture="en-US"
    ConvertFrom-StringData @'
    helloWorld = Hello, World.
    errorMsg1 = You cannot leave the user name field blank.
    promptMsg = Please enter your user name.
'@
}
```

<span data-ttu-id="98104-132">Zie [about_Quoting_Rules](about_Quoting_Rules.md)voor meer informatie over hier teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="98104-132">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

### <a name="psd1-files-storing-translated-strings"></a><span data-ttu-id="98104-133">PSD1-bestanden: vertaalde teken reeksen opslaan</span><span class="sxs-lookup"><span data-stu-id="98104-133">PSD1 Files: Storing Translated Strings</span></span>

<span data-ttu-id="98104-134">Sla de script berichten voor elke taal van de gebruikers interface op in afzonderlijke tekst bestanden met dezelfde naam als het script en de `.psd1` bestandsnaam extensie.</span><span class="sxs-lookup"><span data-stu-id="98104-134">Save the script messages for each UI language in separate text files with the same name as the script and the `.psd1` file name extension.</span></span> <span data-ttu-id="98104-135">Sla de bestanden in submappen van de script Directory op met namen van cultures in de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="98104-135">Store the files in subdirectories of the script directory with names of cultures in the following format:</span></span>

`<language>-<region>`

<span data-ttu-id="98104-136">Voor beelden: de-DE, AR-SA en zh-Hans</span><span class="sxs-lookup"><span data-stu-id="98104-136">Examples: de-DE, ar-SA, and zh-Hans</span></span>

<span data-ttu-id="98104-137">Als het `World.ps1` script bijvoorbeeld wordt opgeslagen in de `C:\Scripts` map, maakt u een mapstructuur die er ongeveer als volgt uitziet:</span><span class="sxs-lookup"><span data-stu-id="98104-137">For example, if the `World.ps1` script is stored in the `C:\Scripts` directory, you would create a file directory structure that resembles the following:</span></span>

```
C:\Scripts
C:\Scripts\World.ps1
C:\Scripts\de-DE\World.psd1
C:\Scripts\ar-SA\World.psd1
C:\Scripts\zh-CN\World.psd1
...
```

<span data-ttu-id="98104-138">Het `World.psd1` bestand in de subdirectory van de script Directory bevat mogelijk de volgende instructie:</span><span class="sxs-lookup"><span data-stu-id="98104-138">The `World.psd1` file in the de-DE subdirectory of the script directory might include the following statement:</span></span>

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = Hallo, Welt.
errorMsg1 = Das Feld Benutzername darf nicht leer sein.
promptMsg = Geben Sie Ihren Benutzernamen ein.
'@
```

<span data-ttu-id="98104-139">Het `World.psd1` bestand in de subdirectory AR-SA van de script Directory kan er ook als volgt uitzien:</span><span class="sxs-lookup"><span data-stu-id="98104-139">Similarly, the `World.psd1` file in the ar-SA subdirectory of the script directory might includes the following statement:</span></span>

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = مرحبًا أيها العالَم
errorMsg1 = لا يمكنك ترك حقل اسم المستخدم فارغًا
promptMsg = يرجى إدخال اسم المستخدم الخاص بك
'@
```

### <a name="import-localizeddata-dynamic-retrieval-of-translated-strings"></a><span data-ttu-id="98104-140">Import-LocalizedData: dynamische ophalen van vertaalde teken reeksen</span><span class="sxs-lookup"><span data-stu-id="98104-140">Import-LocalizedData: Dynamic Retrieval of Translated Strings</span></span>

<span data-ttu-id="98104-141">Als u de teken reeksen wilt ophalen in de taal van de gebruikers interface van de huidige gebruiker, gebruikt u de `Import-LocalizedData` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="98104-141">To retrieve the strings in the UI language of the current user, use the `Import-LocalizedData` cmdlet.</span></span>

<span data-ttu-id="98104-142">`Import-LocalizedData` Hiermee wordt de waarde van de `$PSUICulture` Automatische variabele opgehaald en wordt de inhoud van de `<script-name>.psd1` bestanden in de submap die overeenkomt met de `$PSUICulture` waarde geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="98104-142">`Import-LocalizedData` finds the value of the `$PSUICulture` automatic variable and imports the content of the `<script-name>.psd1` files in the subdirectory that matches the `$PSUICulture` value.</span></span> <span data-ttu-id="98104-143">Vervolgens wordt de geïmporteerde inhoud opgeslagen in de variabele die is opgegeven door de waarde van de para meter **BindingVariable** .</span><span class="sxs-lookup"><span data-stu-id="98104-143">Then, it saves the imported content in the variable specified by the value of the **BindingVariable** parameter.</span></span>

```powershell
Import-LocalizedData -BindingVariable msgTable
```

<span data-ttu-id="98104-144">Als de `Import-LocalizedData` opdracht bijvoorbeeld wordt weer gegeven in het `C:\Scripts\World.ps1` script en de waarde van `$PSUICulture` is ' AR-SA ', `Import-LocalizedData` zoekt het volgende bestand:</span><span class="sxs-lookup"><span data-stu-id="98104-144">For example, if the `Import-LocalizedData` command appears in the `C:\Scripts\World.ps1` script and the value of `$PSUICulture` is "ar-SA", `Import-LocalizedData` finds the following file:</span></span>

`C:\Scripts\ar-SA\World.psd1`

<span data-ttu-id="98104-145">Vervolgens worden de Arabische teken reeksen uit het bestand in de variabele geïmporteerd `$msgTable` , waarbij alle standaard reeksen worden vervangen die kunnen worden gedefinieerd in de sectie gegevens van het `World.ps1` script.</span><span class="sxs-lookup"><span data-stu-id="98104-145">Then, it imports the Arabic text strings from the file into the `$msgTable` variable, replacing any default strings that might be defined in the Data section of the `World.ps1` script.</span></span>

<span data-ttu-id="98104-146">Als gevolg hiervan `$msgTable` worden de berichten in het Arabisch weer gegeven wanneer het script de variabele gebruikt om gebruikers berichten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="98104-146">As a result, when the script uses the `$msgTable` variable to display user messages, the messages are displayed in Arabic.</span></span>

<span data-ttu-id="98104-147">Het volgende script geeft bijvoorbeeld het bericht ' Geef uw gebruikers naam op ' in het Arabisch op:</span><span class="sxs-lookup"><span data-stu-id="98104-147">For example, the following script displays the "Please enter your user name" message in Arabic:</span></span>

```powershell
if (!($username)) { $msgTable.promptMsg }
```

<span data-ttu-id="98104-148">Als `Import-LocalizedData` er geen bestand kan worden gevonden `.psd1` dat overeenkomt met de waarde van `$PSUIculture` , wordt de waarde van `$msgTable` niet vervangen en wordt de aanroep om `$msgTable.promptMsg` de terugval-en-US-teken reeksen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="98104-148">If `Import-LocalizedData` cannot find a `.psd1` file that matches the value of `$PSUIculture`, the value of `$msgTable` is not replaced, and the call to `$msgTable.promptMsg` displays the fallback en-US strings.</span></span>

## <a name="examples"></a><span data-ttu-id="98104-149">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="98104-149">Examples</span></span>

<span data-ttu-id="98104-150">In dit voor beeld ziet u hoe de script functies voor meerdere talen worden gebruikt in een script om een dag van de week weer te geven voor gebruikers in de taal die op de computer is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="98104-150">This example shows how the script internationalization features are used in a script to display a day of the week to users in the language that is set on the computer.</span></span>

<span data-ttu-id="98104-151">Hier volgt een volledige lijst van het Sample1.ps1-script bestand.</span><span class="sxs-lookup"><span data-stu-id="98104-151">The following is a complete listing of the Sample1.ps1 script file.</span></span>

<span data-ttu-id="98104-152">Het script begint met een gegevens sectie met de naam Day ($Day) die een `ConvertFrom-StringData` opdracht bevat.</span><span class="sxs-lookup"><span data-stu-id="98104-152">The script begins with a Data section named Day ($Day) that contains a `ConvertFrom-StringData` command.</span></span> <span data-ttu-id="98104-153">De expressie `ConvertFrom-StringData` die wordt verzonden naar is een hier-teken reeks die de namen van de dagen in de standaard gebruikersinterface cultuur, en-us, in sleutel/waarde-paren bevat.</span><span class="sxs-lookup"><span data-stu-id="98104-153">The expression submitted to `ConvertFrom-StringData` is a here-string that contains the day names in the default UI culture, en-US, in key/value pairs.</span></span> <span data-ttu-id="98104-154">Met de `ConvertFrom-StringData` cmdlet worden de sleutel-waardeparen in de hier-teken reeks geconverteerd naar een hash-tabel en vervolgens opgeslagen in de waarde van de `$Day` variabele.</span><span class="sxs-lookup"><span data-stu-id="98104-154">The `ConvertFrom-StringData` cmdlet converts the key/value pairs in the here-string into a hash table and then saves it in the value of the `$Day` variable.</span></span>

<span data-ttu-id="98104-155">De `Import-LocalizedData` opdracht importeert de inhoud van het `.psd1` bestand in de map die overeenkomt met de waarde van de `$PSUICulture` Automatische variabele en slaat deze vervolgens op in de `$Day` variabele. vervolgens worden de waarden van `$Day` die zijn gedefinieerd in de sectie gegevens vervangen.</span><span class="sxs-lookup"><span data-stu-id="98104-155">The `Import-LocalizedData` command imports the contents of the `.psd1` file in the directory that matches the value of the `$PSUICulture` automatic variable and then saves it in the `$Day` variable, replacing the values of `$Day` that are defined in the Data section.</span></span>

<span data-ttu-id="98104-156">Met de overige opdrachten worden de teken reeksen in een matrix geladen en weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="98104-156">The remaining commands load the strings into an array and display them.</span></span>

```powershell
$Day = Data {
#culture="en-US"
ConvertFrom-StringData -StringData @'
    messageDate = Today is
    d0 = Sunday
    d1 = Monday
    d2 = Tuesday
    d3 = Wednesday
    d4 = Thursday
    d5 = Friday
    d6 = Saturday
'@
}

Import-LocalizedData -BindingVariable Day

#Build an array of weekdays.
$a = $Day.d0, $Day.d1, $Day.d2, $Day.d3, $Day.d4, $Day.d5, $Day.d6

# Get the day of the week as a number (Monday = 1).
# Index into $a to get the name of the day.
# Use string formatting to build a sentence.

"{0} {1}" -f $Day.messageDate, $a[(Get-Date -UFormat %u)] | Out-Host
```

<span data-ttu-id="98104-157">De `.psd1` bestanden die het script ondersteunen, worden opgeslagen in submappen van de script Directory met namen die overeenkomen met de `$PSUICulture` waarden.</span><span class="sxs-lookup"><span data-stu-id="98104-157">The `.psd1` files that support the script are saved in subdirectories of the script directory with names that match the `$PSUICulture` values.</span></span>

<span data-ttu-id="98104-158">Hieronder vindt u een volledige lijst met `.\de-DE\sample1.psd1` :</span><span class="sxs-lookup"><span data-stu-id="98104-158">The following is a complete listing of `.\de-DE\sample1.psd1`:</span></span>

```powershell
# culture="de-DE"
ConvertFrom-StringData @'
    messageDate = Heute ist
    d0 = Sonntag
    d1 = Montag
    d2 = Dienstag
    d3 = Mittwoch
    d4 = Donnerstag
    d5 = Freitag
    d6 = Samstag
'@
```

<span data-ttu-id="98104-159">Als u Sample.ps1 uitvoert op een systeem waarop de waarde van `$PSUICulture` is, is de uitvoer van het script:</span><span class="sxs-lookup"><span data-stu-id="98104-159">As a result, when you run Sample.ps1 on a system on which the value of `$PSUICulture` is de-DE, the output of the script is:</span></span>

```Output
Heute ist Freitag
```

## <a name="see-also"></a><span data-ttu-id="98104-160">Zie ook</span><span class="sxs-lookup"><span data-stu-id="98104-160">See also</span></span>

- [<span data-ttu-id="98104-161">about_Data_Sections</span><span class="sxs-lookup"><span data-stu-id="98104-161">about_Data_Sections</span></span>](about_Data_Sections.md)
- [<span data-ttu-id="98104-162">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="98104-162">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="98104-163">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="98104-163">about_Hash_Tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="98104-164">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="98104-164">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
- [<span data-ttu-id="98104-165">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="98104-165">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
- [<span data-ttu-id="98104-166">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="98104-166">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)
