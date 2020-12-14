---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-clixml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Clixml
ms.openlocfilehash: 3658ea5eded0fed95a1c9a1ea6e7d84a557e1e36
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706166"
---
# <span data-ttu-id="b7f1a-102">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="b7f1a-102">Import-Clixml</span></span>

## <span data-ttu-id="b7f1a-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b7f1a-103">SYNOPSIS</span></span>
<span data-ttu-id="b7f1a-104">Hiermee wordt een CLIXML-bestand geïmporteerd en worden de bijbehorende objecten in Power shell gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-104">Imports a CLIXML file and creates corresponding objects in PowerShell.</span></span>

## <span data-ttu-id="b7f1a-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b7f1a-105">SYNTAX</span></span>

### <span data-ttu-id="b7f1a-106">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="b7f1a-106">ByPath (Default)</span></span>

```
Import-Clixml [-Path] <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

### <span data-ttu-id="b7f1a-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="b7f1a-107">ByLiteralPath</span></span>

```
Import-Clixml -LiteralPath <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

## <span data-ttu-id="b7f1a-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b7f1a-108">DESCRIPTION</span></span>

<span data-ttu-id="b7f1a-109">`Import-Clixml`Met de cmdlet wordt een CLI-XML-bestand (Common Language Infrastructure) geïmporteerd met gegevens die Microsoft .NET Framework-objecten vertegenwoordigen en de Power shell-objecten worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-109">The `Import-Clixml` cmdlet imports a Common Language Infrastructure (CLI) XML file with data that represents Microsoft .NET Framework objects and creates the PowerShell objects.</span></span> <span data-ttu-id="b7f1a-110">Zie [taal onafhankelijkheid](/dotnet/standard/language-independence)voor meer informatie over cli.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-110">For more information about CLI, see [Language independence](/dotnet/standard/language-independence).</span></span>

<span data-ttu-id="b7f1a-111">Een waardevol gebruik van `Import-Clixml` op Windows-computers is het importeren van referenties en beveiligde teken reeksen die zijn geëxporteerd als beveiligde XML met `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="b7f1a-111">A valuable use of `Import-Clixml` on Windows computers is to import credentials and secure strings that were exported as secure XML using `Export-Clixml`.</span></span> <span data-ttu-id="b7f1a-112">Zie voor beeld 2 voor een voor beeld.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-112">For an example, see Example 2.</span></span>

<span data-ttu-id="b7f1a-113">`Import-Clixml` maakt gebruik van de byte-order-Mark (BOM) om de coderings indeling van het bestand te detecteren.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-113">`Import-Clixml` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="b7f1a-114">Als het bestand geen stuk lijst heeft, wordt ervan uitgegaan dat de code ring UTF8 is.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-114">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="b7f1a-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b7f1a-115">EXAMPLES</span></span>

### <span data-ttu-id="b7f1a-116">Voor beeld 1: een geserialiseerd bestand importeren en een object opnieuw maken</span><span class="sxs-lookup"><span data-stu-id="b7f1a-116">Example 1: Import a serialized file and recreate an object</span></span>

<span data-ttu-id="b7f1a-117">In dit voor beeld wordt de `Export-Clixml` cmdlet gebruikt om een geserialiseerde kopie van de proces gegevens op te slaan die worden geretourneerd door `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="b7f1a-117">This example uses the `Export-Clixml` cmdlet to save a serialized copy of the process information returned by `Get-Process`.</span></span> <span data-ttu-id="b7f1a-118">`Import-Clixml` Hiermee wordt de inhoud van het geserialiseerde bestand opgehaald en wordt een object gemaakt dat is opgeslagen in de `$Processes` variabele.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-118">`Import-Clixml` retrieves the serialized file's contents and recreates an object that is stored in the `$Processes` variable.</span></span>

```powershell
Get-Process | Export-Clixml -Path .\pi.xml
$Processes = Import-Clixml -Path .\pi.xml
```

### <span data-ttu-id="b7f1a-119">Voor beeld 2: een beveiligd referentie object importeren</span><span class="sxs-lookup"><span data-stu-id="b7f1a-119">Example 2: Import a secure credential object</span></span>

<span data-ttu-id="b7f1a-120">In dit voor beeld krijgt u een referentie die u hebt opgeslagen in de `$Credential` variabele door de `Get-Credential` cmdlet uit te voeren, kunt u de `Export-Clixml` cmdlet uitvoeren om de referentie op schijf op te slaan.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-120">In this example, given a credential that you've stored in the `$Credential` variable by running the `Get-Credential` cmdlet, you can run the `Export-Clixml` cmdlet to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b7f1a-121">`Export-Clixml` exporteert alleen versleutelde referenties in Windows.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-121">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="b7f1a-122">Op niet-Windows-besturings systemen, zoals macOS en Linux, worden referenties geëxporteerd als tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-122">On non-Windows operating systems such as macOS and Linux, credentials are exported in plain text.</span></span>

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

<span data-ttu-id="b7f1a-123">`Export-Clixml`Met de cmdlet worden referentie objecten versleuteld met behulp van de Windows [Data Protection-API](/previous-versions/windows/apps/hh464970(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="b7f1a-123">The `Export-Clixml` cmdlet encrypts credential objects by using the Windows [Data Protection API](/previous-versions/windows/apps/hh464970(v=win.10)).</span></span>
<span data-ttu-id="b7f1a-124">De versleuteling zorgt ervoor dat alleen uw gebruikers account de inhoud van het referentie object kan ontsleutelen.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-124">The encryption ensures that only your user account can decrypt the contents of the credential object.</span></span> <span data-ttu-id="b7f1a-125">Het geëxporteerde `CLIXML` bestand kan niet worden gebruikt op een andere computer of door een andere gebruiker.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-125">The exported `CLIXML` file can't be used on a different computer or by a different user.</span></span>

<span data-ttu-id="b7f1a-126">In het voor beeld wordt het bestand waarin de referentie is opgeslagen vertegenwoordigd door `TestScript.ps1.credential` .</span><span class="sxs-lookup"><span data-stu-id="b7f1a-126">In the example, the file in which the credential is stored is represented by `TestScript.ps1.credential`.</span></span> <span data-ttu-id="b7f1a-127">Vervang **TestScript** door de naam van het script waarmee u de referentie laadt.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-127">Replace **TestScript** with the name of the script with which you're loading the credential.</span></span>

<span data-ttu-id="b7f1a-128">U stuurt het referentie object omlaag in de pijp lijn naar `Export-Clixml` en slaat het op in het pad, `$Credxmlpath` , dat u hebt opgegeven in de eerste opdracht.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-128">You send the credential object down the pipeline to `Export-Clixml`, and save it to the path, `$Credxmlpath`, that you specified in the first command.</span></span>

<span data-ttu-id="b7f1a-129">Als u de referentie automatisch wilt importeren in uw script, voert u de laatste twee opdrachten uit.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-129">To import the credential automatically into your script, run the final two commands.</span></span> <span data-ttu-id="b7f1a-130">Voer uit `Import-Clixml` om het beveiligde referentie object te importeren in uw script.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-130">Run `Import-Clixml` to import the secured credential object into your script.</span></span> <span data-ttu-id="b7f1a-131">Deze import elimineert het risico dat wacht woorden met onbewerkte tekst in uw script worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-131">This import eliminates the risk of exposing plain-text passwords in your script.</span></span>

## <span data-ttu-id="b7f1a-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b7f1a-132">PARAMETERS</span></span>

### <span data-ttu-id="b7f1a-133">-Eerste</span><span class="sxs-lookup"><span data-stu-id="b7f1a-133">-First</span></span>

<span data-ttu-id="b7f1a-134">Hiermee wordt alleen het opgegeven aantal objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-134">Gets only the specified number of objects.</span></span> <span data-ttu-id="b7f1a-135">Voer het aantal objecten in dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-135">Enter the number of objects to get.</span></span>

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f1a-136">-IncludeTotalCount</span><span class="sxs-lookup"><span data-stu-id="b7f1a-136">-IncludeTotalCount</span></span>

<span data-ttu-id="b7f1a-137">Hiermee wordt het totale aantal objecten in de gegevensset gerapporteerd, gevolgd door de geselecteerde objecten.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-137">Reports the total number of objects in the data set followed by the selected objects.</span></span> <span data-ttu-id="b7f1a-138">Als de cmdlet het totale aantal niet kan bepalen, wordt het **onbekende totale aantal** weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-138">If the cmdlet can't determine the total count, it displays **Unknown total count**.</span></span> <span data-ttu-id="b7f1a-139">Het gehele getal heeft een **nauw** keurige eigenschap die de betrouw baarheid van de totale aantal waarden aangeeft.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-139">The integer has an **Accuracy** property that indicates the reliability of the total count value.</span></span> <span data-ttu-id="b7f1a-140">De waarde van **nauw keurigheid** ligt van `0.0` tot `1.0` waar `0.0` betekent dat de cmdlet de objecten niet kan tellen, `1.0` betekent dat het aantal precies is en een waarde tussen `0.0` en een `1.0` steeds betrouw bare schatting aangeeft.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-140">The value of **Accuracy** ranges from `0.0` to `1.0` where `0.0` means that the cmdlet couldn't count the objects, `1.0` means that the count is exact, and a value between `0.0` and `1.0` indicates an increasingly reliable estimate.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f1a-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b7f1a-141">-LiteralPath</span></span>

<span data-ttu-id="b7f1a-142">Hiermee geeft u het pad naar de XML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-142">Specifies the path to the XML files.</span></span> <span data-ttu-id="b7f1a-143">In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt zoals deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-143">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="b7f1a-144">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b7f1a-145">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-145">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b7f1a-146">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b7f1a-147">-Path</span><span class="sxs-lookup"><span data-stu-id="b7f1a-147">-Path</span></span>

<span data-ttu-id="b7f1a-148">Hiermee geeft u het pad naar de XML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-148">Specifies the path to the XML files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b7f1a-149">-Overs Laan</span><span class="sxs-lookup"><span data-stu-id="b7f1a-149">-Skip</span></span>

<span data-ttu-id="b7f1a-150">Hiermee wordt het opgegeven aantal objecten genegeerd en worden vervolgens de resterende objecten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-150">Ignores the specified number of objects and then gets the remaining objects.</span></span> <span data-ttu-id="b7f1a-151">Voer het aantal objecten in dat moet worden overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-151">Enter the number of objects to skip.</span></span>

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7f1a-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b7f1a-152">CommonParameters</span></span>

<span data-ttu-id="b7f1a-153">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b7f1a-154">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b7f1a-155">INVOER</span><span class="sxs-lookup"><span data-stu-id="b7f1a-155">INPUTS</span></span>

### <span data-ttu-id="b7f1a-156">System. String</span><span class="sxs-lookup"><span data-stu-id="b7f1a-156">System.String</span></span>

<span data-ttu-id="b7f1a-157">U kunt een teken reeks die een pad bevat naar een pijp lijn `Import-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="b7f1a-157">You can pipeline a string that contains a path to `Import-Clixml`.</span></span>

## <span data-ttu-id="b7f1a-158">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b7f1a-158">OUTPUTS</span></span>

### <span data-ttu-id="b7f1a-159">PSObject</span><span class="sxs-lookup"><span data-stu-id="b7f1a-159">PSObject</span></span>

<span data-ttu-id="b7f1a-160">`Import-Clixml` retourneert objecten die zijn gedeserialiseerd van de opgeslagen XML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-160">`Import-Clixml` returns objects that were deserialized from the stored XML files.</span></span>

## <span data-ttu-id="b7f1a-161">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b7f1a-161">NOTES</span></span>

<span data-ttu-id="b7f1a-162">Wanneer u meerdere waarden voor een para meter opgeeft, moet u komma's gebruiken om de waarden van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-162">When specifying multiple values for a parameter, use commas to separate the values.</span></span> <span data-ttu-id="b7f1a-163">Bijvoorbeeld `<parameter-name> <value1>, <value2>`.</span><span class="sxs-lookup"><span data-stu-id="b7f1a-163">For example, `<parameter-name> <value1>, <value2>`.</span></span>

## <span data-ttu-id="b7f1a-164">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b7f1a-164">RELATED LINKS</span></span>

[<span data-ttu-id="b7f1a-165">Exporteren-Clixml</span><span class="sxs-lookup"><span data-stu-id="b7f1a-165">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="b7f1a-166">Inleiding tot XML-serialisatie</span><span class="sxs-lookup"><span data-stu-id="b7f1a-166">Introducing XML Serialization</span></span>](/dotnet/standard/serialization/introducing-xml-serialization)

[<span data-ttu-id="b7f1a-167">Pad voor samen voegen</span><span class="sxs-lookup"><span data-stu-id="b7f1a-167">Join-Path</span></span>](../Microsoft.PowerShell.Management/Join-Path.md)

[<span data-ttu-id="b7f1a-168">Referenties veilig opslaan op schijf</span><span class="sxs-lookup"><span data-stu-id="b7f1a-168">Securely Store Credentials on Disk</span></span>](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[<span data-ttu-id="b7f1a-169">Power shell gebruiken om referenties door te geven aan verouderde systemen</span><span class="sxs-lookup"><span data-stu-id="b7f1a-169">Use PowerShell to Pass Credentials to Legacy Systems</span></span>](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

