---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-String
ms.openlocfilehash: 665a0ca8332c4052b59362c7947e408ba811c5f2
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/01/2020
ms.locfileid: "93251882"
---
# <span data-ttu-id="cd7cb-103">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="cd7cb-103">ConvertFrom-String</span></span>

## <span data-ttu-id="cd7cb-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="cd7cb-104">SYNOPSIS</span></span>
<span data-ttu-id="cd7cb-105">Hiermee worden gestructureerde eigenschappen geëxtraheerd en geparseerd uit de teken reeks inhoud.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-105">Extracts and parses structured properties from string content.</span></span>

## <span data-ttu-id="cd7cb-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cd7cb-106">SYNTAX</span></span>

### <span data-ttu-id="cd7cb-107">ByDelimiter (standaard)</span><span class="sxs-lookup"><span data-stu-id="cd7cb-107">ByDelimiter (Default)</span></span>

```
ConvertFrom-String [-Delimiter <String>] [-PropertyNames <String[]>] [-InputObject] <String>
 [<CommonParameters>]
```

### <span data-ttu-id="cd7cb-108">TemplateParsing</span><span class="sxs-lookup"><span data-stu-id="cd7cb-108">TemplateParsing</span></span>

```
ConvertFrom-String [-TemplateFile <String[]>] [-TemplateContent <String[]>] [-IncludeExtent] [-UpdateTemplate]
 [-InputObject] <String> [<CommonParameters>]
```

## <span data-ttu-id="cd7cb-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cd7cb-109">DESCRIPTION</span></span>

<span data-ttu-id="cd7cb-110">Met de **ConvertFrom-** cmdlet worden gestructureerde eigenschappen geëxtraheerd uit de teken reeks inhoud en geparseerd.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-110">The **ConvertFrom-String** cmdlet extracts and parses structured properties from string content.</span></span>
<span data-ttu-id="cd7cb-111">Met deze cmdlet wordt een object gegenereerd door tekst van een traditionele tekst stroom te parseren.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-111">This cmdlet generates an object by parsing text from a traditional text stream.</span></span>
<span data-ttu-id="cd7cb-112">Voor elke teken reeks in de pijp lijn splitst de cmdlet de invoer met een scheidings teken of een parseringsstructuur en wijst vervolgens eigenschapnamen toe aan elk van de resulterende Splits elementen.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-112">For each string in the pipeline, the cmdlet splits the input by either a delimiter or a parse expression, and then assigns property names to each of the resulting split elements.</span></span>
<span data-ttu-id="cd7cb-113">U kunt deze eigenschapnamen opgeven. Als u dit niet doet, worden ze automatisch voor u gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-113">You can provide these property names; if you do not, they are automatically generated for you.</span></span>

<span data-ttu-id="cd7cb-114">De standaard parameterset van de cmdlet **ByDelimiter** , wordt exact op het reguliere expressie scheidings teken gesplitst.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-114">The cmdlet's default parameter set, **ByDelimiter** , splits exactly on the regular expression delimiter.</span></span>
<span data-ttu-id="cd7cb-115">Er worden geen aanhalings tekens of scheidings tekens voor het afstemmen van de `Import-Csv` cmdlet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-115">It does not perform quote matching or delimiter escaping as the `Import-Csv` cmdlet does.</span></span>

<span data-ttu-id="cd7cb-116">De alternatieve parameterset van de cmdlet, **TemplateParsing** , genereert elementen van de groepen die worden vastgelegd met een reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-116">The cmdlet's alternate parameter set, **TemplateParsing** , generates elements from the groups that are captured by a regular expression.</span></span> <span data-ttu-id="cd7cb-117">Zie [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)voor meer informatie over reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-117">For more information on regular expressions, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span>

<span data-ttu-id="cd7cb-118">Deze cmdlet biedt ondersteuning voor twee modi: basis-gescheiden parsering en automatisch gegenereerde, voor beeld-geparseerd parseren.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-118">This cmdlet supports two modes: basic delimited parsing, and automatically-generated, example-driven parsing.</span></span>

<span data-ttu-id="cd7cb-119">Met een scheidings teken voor het parseren wordt standaard de invoer gesplitst in witruimte en worden eigenschapnamen toegewezen aan de resulterende groepen.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-119">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="cd7cb-120">U kunt het scheidings teken aanpassen door de resultaten te pijpleidingen `ConvertFrom-String` in een van de `Format-*` cmdlets, of u kunt de para meter **scheidings teken** gebruiken.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-120">You can customize the delimiter by piping the `ConvertFrom-String` results into one of the `Format-*` cmdlets, or you can use the **Delimiter** parameter.</span></span>

<span data-ttu-id="cd7cb-121">De cmdlet biedt ook ondersteuning voor automatisch gegenereerde, voor beelden geparseerd parseren op basis van de [FlashExtract, onderzoek werkzaamheden door micro soft Research](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples/).</span><span class="sxs-lookup"><span data-stu-id="cd7cb-121">The cmdlet also supports automatically-generated, example-driven parsing based on the [FlashExtract, research work by Microsoft Research](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples/).</span></span>

## <span data-ttu-id="cd7cb-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cd7cb-122">EXAMPLES</span></span>

### <span data-ttu-id="cd7cb-123">Voor beeld 1: een object met standaard eigenschapnamen genereren</span><span class="sxs-lookup"><span data-stu-id="cd7cb-123">Example 1: Generate an object with default property names</span></span>

```powershell
"Hello World" | ConvertFrom-String
```

```Output
P1    P2
--    --
Hello World
```

<span data-ttu-id="cd7cb-124">Met deze opdracht wordt een object gegenereerd met standaard namen van eigenschappen, **P1** en **P2**.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-124">This command generates an object with default property names, **P1** and **P2**.</span></span>

### <span data-ttu-id="cd7cb-125">Voor beeld 1A: meer weten over het gegenereerde object</span><span class="sxs-lookup"><span data-stu-id="cd7cb-125">Example 1A: Get to know the generated object</span></span>

<span data-ttu-id="cd7cb-126">Met deze opdracht wordt één object gegenereerd met de eigenschappen **P1** , **P2** ; beide eigenschappen zijn standaard van het type **teken reeks** .</span><span class="sxs-lookup"><span data-stu-id="cd7cb-126">This command generates one object with properties **P1** , **P2** ; both properties are of **String** type, by default.</span></span>

```powershell
"Hello World" | ConvertFrom-String | Get-Member
```

```Output

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
P1          NoteProperty string P1=Hello
P2          NoteProperty string P2=World
```

### <span data-ttu-id="cd7cb-127">Voor beeld 2: een object met standaard eigenschapnamen genereren met behulp van een scheidings teken</span><span class="sxs-lookup"><span data-stu-id="cd7cb-127">Example 2: Generate an object with default property names using a delimiter</span></span>

<span data-ttu-id="cd7cb-128">Met deze opdracht wordt een object gegenereerd met een domein en gebruikers naam met behulp van de back slash ( `\` ) als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-128">This command generates an object with a domain and username using the backslash (`\`) as the delimiter.</span></span> <span data-ttu-id="cd7cb-129">Het back slash-teken moet worden voorafgegaan door een andere back slash wanneer reguliere expressies worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-129">The backslash character must be escaped with another backslash when using regular expressions.</span></span>

```powershell
"Contoso\Administrator" | ConvertFrom-String -Delimiter "\\"
```

```Output
P1      P2
--      --
Contoso Administrator
```

### <span data-ttu-id="cd7cb-130">Voor beeld 3: een object genereren dat twee benoemde eigenschappen bevat</span><span class="sxs-lookup"><span data-stu-id="cd7cb-130">Example 3: Generate an object that contains two named properties</span></span>

<span data-ttu-id="cd7cb-131">In het volgende voor beeld worden objecten gemaakt op basis van Windows hosts-bestands vermeldingen.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-131">The following example creates objects from Windows hosts file entries.</span></span>

```powershell
$content = Get-Content C:\Windows\System32\drivers\etc\hosts
$content = $content -match "^[^#]"
$content | ConvertFrom-String -PropertyNames IP, Server
```

```Output
IP             Server
--             ------
192.168.7.10   W2012R2
192.168.7.20   W2016
192.168.7.101  WIN8
192.168.7.102  WIN10
```

<span data-ttu-id="cd7cb-132">De- `Get-Content` cmdlet slaat de inhoud van een Windows hosts-bestand op in `$content` .</span><span class="sxs-lookup"><span data-stu-id="cd7cb-132">The `Get-Content` cmdlet stores the content of a Windows hosts file in `$content`.</span></span> <span data-ttu-id="cd7cb-133">Met de tweede opdracht verwijdert u eventuele opmerkingen aan het begin van het hosts-bestand met behulp van een reguliere expressie die overeenkomt met een regel die niet begint met ( `#` ).</span><span class="sxs-lookup"><span data-stu-id="cd7cb-133">The second command removes any comments at the beginning of the hosts file using a regular expression that matches any line that does not start with (`#`).</span></span> <span data-ttu-id="cd7cb-134">Met de laatste opdracht wordt de resterende tekst geconverteerd naar objecten met de eigenschappen **Server** en **IP** .</span><span class="sxs-lookup"><span data-stu-id="cd7cb-134">The last command converts the remaining text into objects with **Server** and **IP** properties.</span></span>

### <span data-ttu-id="cd7cb-135">Voor beeld 4: een expressie gebruiken als de waarde van de TemplateContent-para meter, sla de resultaten op in een variabele.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-135">Example 4: Use an expression as the value of the TemplateContent parameter, save the results in a variable.</span></span>

<span data-ttu-id="cd7cb-136">Met deze opdracht wordt een expressie gebruikt als de waarde van de para meter **TemplateContent** .</span><span class="sxs-lookup"><span data-stu-id="cd7cb-136">This command uses an expression as the value of the **TemplateContent** parameter.</span></span>
<span data-ttu-id="cd7cb-137">De expressie wordt opgeslagen in een variabele voor eenvoud.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-137">The expression is saved in a variable for simplicity.</span></span>
<span data-ttu-id="cd7cb-138">Windows Power shell begrijpt nu dat de teken reeks die wordt gebruikt voor de pijp lijn `ConvertFrom-String` drie eigenschappen heeft:</span><span class="sxs-lookup"><span data-stu-id="cd7cb-138">Windows PowerShell understands now that the string that is used on the pipeline to `ConvertFrom-String` has three properties:</span></span>

- <span data-ttu-id="cd7cb-139">**Naam**</span><span class="sxs-lookup"><span data-stu-id="cd7cb-139">**Name**</span></span>
- <span data-ttu-id="cd7cb-140">**telefoon**</span><span class="sxs-lookup"><span data-stu-id="cd7cb-140">**phone**</span></span>
- <span data-ttu-id="cd7cb-141">**leeftijd**</span><span class="sxs-lookup"><span data-stu-id="cd7cb-141">**age**</span></span>

```powershell
$template = @'
{Name*:Phoebe Cat}, {phone:425-123-6789}, {age:6}
{Name*:Lucky Shot}, {phone:(206) 987-4321}, {age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789    6
Lucky Shot    (206) 987-4321  12
Elephant Wise 425-888-7766    87
Wild Shrimp   (111)  222-3333 1
```

<span data-ttu-id="cd7cb-142">Elke regel in de invoer wordt geëvalueerd op basis van de voor beelden van overeenkomsten.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-142">Each line in the input is evaluated by the sample matches.</span></span> <span data-ttu-id="cd7cb-143">Als de lijn overeenkomt met de voor beelden die zijn opgegeven in het patroon, worden waarden geëxtraheerd en door gegeven aan de uitvoer variabele.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-143">If the line matches the examples given in the pattern, values are extracted and passed to the output variable.</span></span>

<span data-ttu-id="cd7cb-144">De voorbeeld gegevens, `$template` , biedt twee verschillende telefoon indelingen:</span><span class="sxs-lookup"><span data-stu-id="cd7cb-144">The sample data, `$template`, provides two different phone formats:</span></span>

- `425-123-6789`
- `(206) 987-4321`

<span data-ttu-id="cd7cb-145">De voorbeeld gegevens bieden ook twee verschillende leeftijds notaties:</span><span class="sxs-lookup"><span data-stu-id="cd7cb-145">The sample data also provides two different age formats:</span></span>

- `6`
- `12`

<span data-ttu-id="cd7cb-146">Dit betekent dat telefoons zoals `(206) 987 4321` niet worden herkend, omdat er geen voorbeeld gegevens zijn die overeenkomen met het patroon omdat er geen afbreek streepjes zijn.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-146">This implies that phones like `(206) 987 4321` will not be recognized, because there's no sample data that matches that pattern because there are no hyphens.</span></span>

### <span data-ttu-id="cd7cb-147">Voor beeld 5: gegevens typen opgeven voor de gegenereerde eigenschappen</span><span class="sxs-lookup"><span data-stu-id="cd7cb-147">Example 5: Specifying data types to the generated properties</span></span>

<span data-ttu-id="cd7cb-148">Dit is hetzelfde voor beeld als voor beeld 4 hierboven.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-148">This is the same example as Example 4, above.</span></span>
<span data-ttu-id="cd7cb-149">Het verschil is dat de patroon teken reeks een gegevens type voor elke gewenste eigenschap bevat.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-149">The difference is that the pattern string includes a data type for each desired property.</span></span>

```powershell
$template = @'
{[string]Name*:Phoebe Cat}, {[string]phone:425-123-6789}, {[int]age:6}
{[string]Name*:Lucky Shot}, {[string]phone:(206) 987-4321}, {[int]age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789      6
Lucky Shot    (206) 987-4321   12
Elephant Wise 425-888-7766     87
Wild Shrimp   (111)  222-3333   1
```

```powershell
$PersonalData | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
age         NoteProperty int age=6
Name        NoteProperty string Name=Phoebe Cat
phone       NoteProperty string phone=425-123-6789
```

<span data-ttu-id="cd7cb-150">De `Get-Member` cmdlet wordt gebruikt om aan te geven dat de eigenschap **Age** een geheel getal is.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-150">The `Get-Member` cmdlet is used to show that the **age** property is an integer.</span></span>

## <span data-ttu-id="cd7cb-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cd7cb-151">PARAMETERS</span></span>

### <span data-ttu-id="cd7cb-152">-Scheidings teken</span><span class="sxs-lookup"><span data-stu-id="cd7cb-152">-Delimiter</span></span>

<span data-ttu-id="cd7cb-153">Hiermee geeft u een reguliere expressie op waarmee de grens tussen elementen wordt aangegeven.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-153">Specifies a regular expression that identifies the boundary between elements.</span></span>
<span data-ttu-id="cd7cb-154">Elementen die door de splitsing worden gemaakt, worden eigenschappen in het resulterende object.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-154">Elements that are created by the split become properties in the resulting object.</span></span>
<span data-ttu-id="cd7cb-155">Het scheidings teken wordt uiteindelijk gebruikt in een aanroep van de methode **Split** van het type `[System.Text.RegularExpressions.RegularExpression]` .</span><span class="sxs-lookup"><span data-stu-id="cd7cb-155">The delimiter is ultimately used in a call to the **Split** method of the type `[System.Text.RegularExpressions.RegularExpression]`.</span></span>

```yaml
Type: System.String
Parameter Sets: ByDelimiter
Aliases: DEL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd7cb-156">-IncludeExtent</span><span class="sxs-lookup"><span data-stu-id="cd7cb-156">-IncludeExtent</span></span>

<span data-ttu-id="cd7cb-157">Geeft aan dat deze cmdlet een eigenschap voor de grootte van een tekst bevat die standaard wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-157">Indicates that this cmdlet includes an extent text property that is removed by default.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: IE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd7cb-158">-Input object</span><span class="sxs-lookup"><span data-stu-id="cd7cb-158">-InputObject</span></span>

<span data-ttu-id="cd7cb-159">Specificeert teken reeksen die zijn ontvangen van de pijp lijn of een variabele die een teken reeks object bevat.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-159">Specifies strings received from the pipeline, or a variable that contains a string object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cd7cb-160">-PropertyNames</span><span class="sxs-lookup"><span data-stu-id="cd7cb-160">-PropertyNames</span></span>

<span data-ttu-id="cd7cb-161">Hiermee geeft u een matrix met eigenschapnamen op waaraan u gesplitste waarden in het resulterende object wilt toewijzen.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-161">Specifies an array of property names to which to assign split values in the resulting object.</span></span>
<span data-ttu-id="cd7cb-162">Elke regel tekst die u splitst of parseert, genereert elementen die eigenschaps waarden vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-162">Every line of text that you split or parse generates elements that represent property values.</span></span>
<span data-ttu-id="cd7cb-163">Als het element het resultaat is van een vastleg groep en die vastleg groep heet (bijvoorbeeld `(?<name>)` of `(?'name')` ), wordt de naam van die vastleg groep toegewezen aan de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-163">If the element is the result of a capture group, and that capture group is named (for example, `(?<name>)` or `(?'name')` ), then the name of that capture group is assigned to the property.</span></span>

<span data-ttu-id="cd7cb-164">Als u elementen in de **PropertyName** -matrix opgeeft, worden deze namen toegewezen aan eigenschappen die nog niet zijn benoemd.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-164">If you provide any elements in the **PropertyName** array, those names are assigned to properties that have not yet been named.</span></span>

<span data-ttu-id="cd7cb-165">Als u meer eigenschapnamen opgeeft dan er velden zijn, negeert Power shell de extra eigenschaps namen.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-165">If you provide more property names than there are fields, PowerShell ignores the extra property names.</span></span> <span data-ttu-id="cd7cb-166">Als u niet voldoende eigenschapnamen opgeeft om alle velden een naam te geven, wijst Power shell automatisch numerieke eigenschapnamen toe aan eigenschappen die geen naam hebben: **P1** , **P2** , enzovoort.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-166">If you do not specify enough property names to name all fields, PowerShell automatically assigns numerical property names to any properties that are not named: **P1** , **P2** , etc.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByDelimiter
Aliases: PN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd7cb-167">-TemplateContent</span><span class="sxs-lookup"><span data-stu-id="cd7cb-167">-TemplateContent</span></span>

<span data-ttu-id="cd7cb-168">Hiermee geeft u een expressie op, of een expressie die is opgeslagen als een variabele, waarin de eigenschappen worden beschreven waaraan deze cmdlet teken reeksen toewijst.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-168">Specifies an expression, or an expression saved as a variable, that describes the properties to which this cmdlet assigns strings.</span></span> <span data-ttu-id="cd7cb-169">De syntaxis van een sjabloon veld specificatie is het volgende: `{[optional-typecast]<name>:<example-value>}` .</span><span class="sxs-lookup"><span data-stu-id="cd7cb-169">The syntax of a template field specification is the following: `{[optional-typecast]<name>:<example-value>}`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd7cb-170">-TemplateFile</span><span class="sxs-lookup"><span data-stu-id="cd7cb-170">-TemplateFile</span></span>

<span data-ttu-id="cd7cb-171">Hiermee geeft u een bestand, als een matrix, op dat een sjabloon bevat voor de gewenste parsering van de teken reeks.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-171">Specifies a file, as an array, that contains a template for the desired parsing of the string.</span></span>
<span data-ttu-id="cd7cb-172">In het sjabloon bestand staan eigenschappen en hun waarden tussen vier Kante haken, zoals hieronder wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-172">In the template file, properties and their values are enclosed in brackets, as shown below.</span></span>
<span data-ttu-id="cd7cb-173">Als een eigenschap, zoals de eigenschap **name** en de bijbehorende andere eigenschappen, meerdere keren wordt weer gegeven, kunt u een asterisk ( `*` ) toevoegen om aan te geven dat dit resulteert in meerdere records.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-173">If a property, such as the **Name** property and its associated other properties, appears multiple times, you can add an asterisk (`*`) to indicate that this results in multiple records.</span></span> <span data-ttu-id="cd7cb-174">Dit voor komt dat meerdere eigenschappen worden geëxtraheerd tot één record.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-174">This avoids extracting multiple properties into a single record.</span></span>

```
{Name*:David Chew}
{City:Redmond}, {State:WA}
{Name*:Evan Narvaez}    {Name*:Antonio Moreno}
{City:Issaquah}, {State:WA}
```

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd7cb-175">-UpdateTemplate</span><span class="sxs-lookup"><span data-stu-id="cd7cb-175">-UpdateTemplate</span></span>

<span data-ttu-id="cd7cb-176">Geeft aan dat met deze cmdlet de resultaten van een leer algoritme worden opgeslagen in een opmerking in het sjabloon bestand.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-176">Indicates that this cmdlet saves the results of a learning algorithm into a comment in the template file.</span></span>
<span data-ttu-id="cd7cb-177">Hierdoor wordt het algoritme learning proces sneller uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-177">This makes the algorithm learning process faster.</span></span>
<span data-ttu-id="cd7cb-178">Als u deze para meter wilt gebruiken, moet u ook een sjabloon bestand met de para meter **TemplateFile** opgeven.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-178">To use this parameter, you must also specify a template file with the **TemplateFile** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: UT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cd7cb-179">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cd7cb-179">CommonParameters</span></span>

<span data-ttu-id="cd7cb-180">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="cd7cb-180">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="cd7cb-181">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cd7cb-181">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="cd7cb-182">INVOER</span><span class="sxs-lookup"><span data-stu-id="cd7cb-182">INPUTS</span></span>

### <span data-ttu-id="cd7cb-183">System. String</span><span class="sxs-lookup"><span data-stu-id="cd7cb-183">System.String</span></span>

## <span data-ttu-id="cd7cb-184">UITVOER</span><span class="sxs-lookup"><span data-stu-id="cd7cb-184">OUTPUTS</span></span>

## <span data-ttu-id="cd7cb-185">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="cd7cb-185">NOTES</span></span>

## <span data-ttu-id="cd7cb-186">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="cd7cb-186">RELATED LINKS</span></span>

[<span data-ttu-id="cd7cb-187">ConvertFrom-string: voor beelden van het parseren van tekst</span><span class="sxs-lookup"><span data-stu-id="cd7cb-187">ConvertFrom-String: Example-based text parsing</span></span>](https://devblogs.microsoft.com/powershell/convertfrom-string-example-based-text-parsing/)

[<span data-ttu-id="cd7cb-188">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="cd7cb-188">ConvertFrom-StringData</span></span>](ConvertFrom-StringData.md)

[<span data-ttu-id="cd7cb-189">ConvertFrom-CSV</span><span class="sxs-lookup"><span data-stu-id="cd7cb-189">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="cd7cb-190">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="cd7cb-190">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)
