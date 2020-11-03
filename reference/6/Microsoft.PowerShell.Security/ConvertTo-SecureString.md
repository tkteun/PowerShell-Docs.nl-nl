---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertto-securestring?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-SecureString
ms.openlocfilehash: 71b2a36601281d148bed6742ce3f3cb78e11acf4
ms.sourcegitcommit: df80c558e9a4b89c9798f084bd04012ece15155c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/23/2020
ms.locfileid: "93253219"
---
# <span data-ttu-id="e1f02-103">ConvertTo-SecureString</span><span class="sxs-lookup"><span data-stu-id="e1f02-103">ConvertTo-SecureString</span></span>

## <span data-ttu-id="e1f02-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e1f02-104">SYNOPSIS</span></span>
<span data-ttu-id="e1f02-105">Converteert tekst zonder opmaak of versleutelde teken reeksen naar beveiligde teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="e1f02-105">Converts plain text or encrypted strings to secure strings.</span></span>

## <span data-ttu-id="e1f02-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e1f02-106">SYNTAX</span></span>

### <span data-ttu-id="e1f02-107">Beveiligd (standaard)</span><span class="sxs-lookup"><span data-stu-id="e1f02-107">Secure (Default)</span></span>

```
ConvertTo-SecureString [-String] <String> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### <span data-ttu-id="e1f02-108">PlainText</span><span class="sxs-lookup"><span data-stu-id="e1f02-108">PlainText</span></span>

```
ConvertTo-SecureString [-String] <String> [-AsPlainText] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="e1f02-109">Openen</span><span class="sxs-lookup"><span data-stu-id="e1f02-109">Open</span></span>

```
ConvertTo-SecureString [-String] <String> [-Key <Byte[]>] [<CommonParameters>]
```

## <span data-ttu-id="e1f02-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e1f02-110">DESCRIPTION</span></span>

<span data-ttu-id="e1f02-111">Met de `ConvertTo-SecureString` cmdlet worden versleutelde standaard teken reeksen omgezet in beveiligde teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="e1f02-111">The `ConvertTo-SecureString` cmdlet converts encrypted standard strings into secure strings.</span></span> <span data-ttu-id="e1f02-112">Het kan ook tekst zonder opmaak converteren naar beveiligde teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="e1f02-112">It can also convert plain text to secure strings.</span></span> <span data-ttu-id="e1f02-113">Deze wordt gebruikt met `ConvertFrom-SecureString` en `Read-Host` .</span><span class="sxs-lookup"><span data-stu-id="e1f02-113">It is used with `ConvertFrom-SecureString` and `Read-Host`.</span></span> <span data-ttu-id="e1f02-114">De beveiligde teken reeks die door de cmdlet wordt gemaakt, kan worden gebruikt met cmdlets of functies die een para meter van het type **SecureString** vereisen.</span><span class="sxs-lookup"><span data-stu-id="e1f02-114">The secure string created by the cmdlet can be used with cmdlets or functions that require a parameter of type **SecureString**.</span></span> <span data-ttu-id="e1f02-115">De beveiligde teken reeks kan worden omgezet naar een versleutelde, standaard teken reeks met behulp van de `ConvertFrom-SecureString` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e1f02-115">The secure string can be converted back to an encrypted, standard string using the `ConvertFrom-SecureString` cmdlet.</span></span> <span data-ttu-id="e1f02-116">Hierdoor kan het worden opgeslagen in een bestand voor later gebruik.</span><span class="sxs-lookup"><span data-stu-id="e1f02-116">This enables it to be stored in a file for later use.</span></span>

<span data-ttu-id="e1f02-117">Als de standaard teken reeks die wordt geconverteerd, is versleuteld met `ConvertFrom-SecureString` behulp van een opgegeven sleutel, moet diezelfde sleutel worden opgegeven als de waarde van de **sleutel** -of **SecureKey** -para meter van de `ConvertTo-SecureString` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e1f02-117">If the standard string being converted was encrypted with `ConvertFrom-SecureString` using a specified key, that same key must be provided as the value of the **Key** or **SecureKey** parameter of the `ConvertTo-SecureString` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="e1f02-118">Houd er rekening mee dat de inhoud van een SecureString per [DotNet](/dotnet/api/system.security.securestring#remarks)niet wordt versleuteld op niet-Windows-systemen.</span><span class="sxs-lookup"><span data-stu-id="e1f02-118">Note that per [DotNet](/dotnet/api/system.security.securestring#remarks), the contents of a SecureString are not encrypted on non-Windows systems.</span></span>

## <span data-ttu-id="e1f02-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e1f02-119">EXAMPLES</span></span>

### <span data-ttu-id="e1f02-120">Voor beeld 1: een beveiligde teken reeks converteren naar een versleutelde teken reeks</span><span class="sxs-lookup"><span data-stu-id="e1f02-120">Example 1: Convert a secure string to an encrypted string</span></span>

<span data-ttu-id="e1f02-121">In dit voor beeld ziet u hoe u een veilige teken reeks maakt op basis van gebruikers invoer, de beveiligde teken reeks converteert naar een versleutelde standaard teken reeks en de versleutelde standaard teken reeks vervolgens weer converteert naar een veilige teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e1f02-121">This example shows how to create a secure string from user input, convert the secure string to an encrypted standard string, and then convert the encrypted standard string back to a secure string.</span></span>

```powershell
PS C:\> $Secure = Read-Host -AsSecureString
PS C:\> $Secure
System.Security.SecureString
PS C:\> $Encrypted = ConvertFrom-SecureString -SecureString $Secure
PS C:\> $Encrypted
01000000d08c9ddf0115d1118c7a00c04fc297eb010000001a114d45b8dd3f4aa11ad7c0abdae98000000000
02000000000003660000a8000000100000005df63cea84bfb7d70bd6842e7efa79820000000004800000a000
000010000000f10cd0f4a99a8d5814d94e0687d7430b100000008bf11f1960158405b2779613e9352c6d1400
0000e6b7bf46a9d485ff211b9b2a2df3bd6eb67aae41
PS C:\> $Secure2 = ConvertTo-SecureString -String $Encrypted
PS C:\> $Secure2
System.Security.SecureString
```

<span data-ttu-id="e1f02-122">De eerste opdracht maakt gebruik van de para meter **AsSecureString** van de `Read-Host` cmdlet om een beveiligde teken reeks te maken.</span><span class="sxs-lookup"><span data-stu-id="e1f02-122">The first command uses the **AsSecureString** parameter of the `Read-Host` cmdlet to create a secure string.</span></span> <span data-ttu-id="e1f02-123">Nadat u de opdracht hebt ingevoerd, worden de door u getypte tekens omgezet in een beveiligde teken reeks en vervolgens opgeslagen in de `$Secure` variabele.</span><span class="sxs-lookup"><span data-stu-id="e1f02-123">After you enter the command, any characters that you type are converted into a secure string and then saved in the `$Secure` variable.</span></span>

<span data-ttu-id="e1f02-124">Met de tweede opdracht wordt de inhoud van de variabele weer gegeven `$Secure` .</span><span class="sxs-lookup"><span data-stu-id="e1f02-124">The second command displays the contents of the `$Secure` variable.</span></span> <span data-ttu-id="e1f02-125">Omdat de `$Secure` variabele een beveiligde teken reeks bevat, wordt in Power shell alleen het type **System. Security. SecureString** weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e1f02-125">Because the `$Secure` variable contains a secure string, PowerShell displays only the **System.Security.SecureString** type.</span></span>

<span data-ttu-id="e1f02-126">De derde opdracht gebruikt de `ConvertFrom-SecureString` cmdlet om de beveiligde teken reeks in de `$Secure` variabele te converteren naar een versleutelde standaard teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e1f02-126">The third command uses the `ConvertFrom-SecureString` cmdlet to convert the secure string in the `$Secure` variable into an encrypted standard string.</span></span> <span data-ttu-id="e1f02-127">Het resultaat wordt opgeslagen in de `$Encrypted` variabele.</span><span class="sxs-lookup"><span data-stu-id="e1f02-127">It saves the result in the `$Encrypted` variable.</span></span>

<span data-ttu-id="e1f02-128">Met de vierde opdracht wordt de versleutelde teken reeks weer gegeven in de waarde van de `$Encrypted` variabele.</span><span class="sxs-lookup"><span data-stu-id="e1f02-128">The fourth command displays the encrypted string in the value of the `$Encrypted` variable.</span></span>

<span data-ttu-id="e1f02-129">De vijfde opdracht gebruikt de `ConvertTo-SecureString` cmdlet om de versleutelde standaard teken reeks in de `$Encrypted` variabele terug te converteren naar een veilige teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e1f02-129">The fifth command uses the `ConvertTo-SecureString` cmdlet to convert the encrypted standard string in the `$Encrypted` variable back into a secure string.</span></span> <span data-ttu-id="e1f02-130">Het resultaat wordt opgeslagen in de `$Secure2` variabele.</span><span class="sxs-lookup"><span data-stu-id="e1f02-130">It saves the result in the `$Secure2` variable.</span></span>
<span data-ttu-id="e1f02-131">Met de zesde opdracht wordt de waarde van de variabele weer gegeven `$Secure2` .</span><span class="sxs-lookup"><span data-stu-id="e1f02-131">The sixth command displays the value of the `$Secure2` variable.</span></span> <span data-ttu-id="e1f02-132">Het type SecureString geeft aan dat de opdracht is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="e1f02-132">The SecureString type indicates that the command was successful.</span></span>

### <span data-ttu-id="e1f02-133">Voor beeld 2: een veilige teken reeks maken op basis van een versleutelde teken reeks in een bestand</span><span class="sxs-lookup"><span data-stu-id="e1f02-133">Example 2: Create a secure string from an encrypted string in a file</span></span>

<span data-ttu-id="e1f02-134">In dit voor beeld ziet u hoe u een veilige teken reeks maakt van een versleutelde standaard teken reeks die in een bestand wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="e1f02-134">This example shows how to create a secure string from an encrypted standard string that is saved in a file.</span></span>

```powershell
$Secure = Read-Host -AsSecureString
$Encrypted = ConvertFrom-SecureString -SecureString $Secure -Key (1..16)
$Encrypted | Set-Content Encrypted.txt
$Secure2 = Get-Content Encrypted.txt | ConvertTo-SecureString -Key (1..16)
```

<span data-ttu-id="e1f02-135">De eerste opdracht maakt gebruik van de para meter **AsSecureString** van de `Read-Host` cmdlet om een beveiligde teken reeks te maken.</span><span class="sxs-lookup"><span data-stu-id="e1f02-135">The first command uses the **AsSecureString** parameter of the `Read-Host` cmdlet to create a secure string.</span></span> <span data-ttu-id="e1f02-136">Nadat u de opdracht hebt ingevoerd, worden de door u getypte tekens omgezet in een beveiligde teken reeks en vervolgens opgeslagen in de `$Secure` variabele.</span><span class="sxs-lookup"><span data-stu-id="e1f02-136">After you enter the command, any characters that you type are converted into a secure string and then saved in the `$Secure` variable.</span></span>

<span data-ttu-id="e1f02-137">Met de tweede opdracht wordt de- `ConvertFrom-SecureString` cmdlet gebruikt om de beveiligde teken reeks in de variabele te converteren `$Secure` naar een versleutelde standaard teken reeks met behulp van de opgegeven sleutel.</span><span class="sxs-lookup"><span data-stu-id="e1f02-137">The second command uses the `ConvertFrom-SecureString` cmdlet to convert the secure string in the `$Secure` variable into an encrypted standard string by using the specified key.</span></span> <span data-ttu-id="e1f02-138">De inhoud wordt opgeslagen in de `$Encrypted` variabele.</span><span class="sxs-lookup"><span data-stu-id="e1f02-138">The contents are saved in the `$Encrypted` variable.</span></span>

<span data-ttu-id="e1f02-139">De derde opdracht maakt gebruik van een pijplijn operator ( `|` ) om de waarde van de `$Encrypted` variabele naar de `Set-Content` cmdlet te verzenden, waarmee de waarde in het Encrypted.txt-bestand wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="e1f02-139">The third command uses a pipeline operator (`|`) to send the value of the `$Encrypted` variable to the `Set-Content` cmdlet, which saves the value in the Encrypted.txt file.</span></span>

<span data-ttu-id="e1f02-140">De vierde opdracht gebruikt de `Get-Content` cmdlet om de versleutelde standaard teken reeks in het Encrypted.txt-bestand op te halen.</span><span class="sxs-lookup"><span data-stu-id="e1f02-140">The fourth command uses the `Get-Content` cmdlet to get the encrypted standard string in the Encrypted.txt file.</span></span> <span data-ttu-id="e1f02-141">De opdracht maakt gebruik van een pijplijn operator voor het verzenden van de versleutelde teken reeks naar de `ConvertTo-SecureString` cmdlet, die deze converteert naar een beveiligde teken reeks met behulp van de opgegeven sleutel.</span><span class="sxs-lookup"><span data-stu-id="e1f02-141">The command uses a pipeline operator to send the encrypted string to the `ConvertTo-SecureString` cmdlet, which converts it to a secure string by using the specified key.</span></span>
<span data-ttu-id="e1f02-142">De resultaten worden opgeslagen in de `$Secure2` variabele.</span><span class="sxs-lookup"><span data-stu-id="e1f02-142">The results are saved in the `$Secure2` variable.</span></span>

### <span data-ttu-id="e1f02-143">Voor beeld 3: een teken reeks met tekst zonder opmaak converteren naar een veilige teken reeks</span><span class="sxs-lookup"><span data-stu-id="e1f02-143">Example 3: Convert a plain text string to a secure string</span></span>

<span data-ttu-id="e1f02-144">Met deze opdracht wordt de teken reeks met tekst zonder opmaak geconverteerd `P@ssW0rD!` naar een beveiligde teken reeks en wordt het resultaat opgeslagen in de `$Secure_String_Pwd` variabele.</span><span class="sxs-lookup"><span data-stu-id="e1f02-144">This command converts the plain text string `P@ssW0rD!` into a secure string and stores the result in the `$Secure_String_Pwd` variable.</span></span> <span data-ttu-id="e1f02-145">Als u de para meter **AsPlainText** wilt gebruiken, moet de para meter **Forces** ook worden opgenomen in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="e1f02-145">To use the **AsPlainText** parameter, the **Force** parameter must also be included in the command.</span></span>

```powershell
$Secure_String_Pwd = ConvertTo-SecureString "P@ssW0rD!" -AsPlainText -Force
```

> [!CAUTION]
> <span data-ttu-id="e1f02-146">Vermijd het gebruik van teken reeksen met tekst zonder opmaak in een script of vanaf de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="e1f02-146">You should avoid using plain text strings in script or from the command line.</span></span> <span data-ttu-id="e1f02-147">De tekst zonder opmaak kan worden weer gegeven in gebeurtenis logboeken en logboeken van de opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="e1f02-147">The plain text can show up in event logs and command history logs.</span></span>

## <span data-ttu-id="e1f02-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e1f02-148">PARAMETERS</span></span>

### <span data-ttu-id="e1f02-149">-AsPlainText</span><span class="sxs-lookup"><span data-stu-id="e1f02-149">-AsPlainText</span></span>

<span data-ttu-id="e1f02-150">Geeft een teken reeks voor onbewerkte tekst aan die moet worden geconverteerd naar een beveiligde teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e1f02-150">Specifies a plain text string to convert to a secure string.</span></span> <span data-ttu-id="e1f02-151">Met de beveiligde teken reeks-cmdlets kunt u vertrouwelijke tekst beveiligen.</span><span class="sxs-lookup"><span data-stu-id="e1f02-151">The secure string cmdlets help protect confidential text.</span></span> <span data-ttu-id="e1f02-152">De tekst wordt versleuteld voor privacy en wordt verwijderd uit het computer geheugen nadat deze is gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e1f02-152">The text is encrypted for privacy and is deleted from computer memory after it is used.</span></span> <span data-ttu-id="e1f02-153">Als u deze para meter gebruikt om onbewerkte tekst als invoer op te geven, kan het systeem die invoer niet op deze manier beveiligen.</span><span class="sxs-lookup"><span data-stu-id="e1f02-153">If you use this parameter to provide plain text as input, the system cannot protect that input in this manner.</span></span> <span data-ttu-id="e1f02-154">Als u deze para meter wilt gebruiken, moet u ook de para meter **Force** opgeven.</span><span class="sxs-lookup"><span data-stu-id="e1f02-154">To use this parameter, you must also specify the **Force** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1f02-155">-Force</span><span class="sxs-lookup"><span data-stu-id="e1f02-155">-Force</span></span>

<span data-ttu-id="e1f02-156">Hiermee wordt bevestigd dat u de implicaties van het gebruik van de para meter **AsPlainText** begrijpt en deze nog steeds wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e1f02-156">Confirms that you understand the implications of using the **AsPlainText** parameter and still want to use it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1f02-157">-Sleutel</span><span class="sxs-lookup"><span data-stu-id="e1f02-157">-Key</span></span>

<span data-ttu-id="e1f02-158">Hiermee geeft u de versleutelings sleutel die wordt gebruikt om de oorspronkelijke beveiligde teken reeks te converteren naar de versleutelde standaard teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e1f02-158">Specifies the encryption key used to convert the original secure string into the encrypted standard string.</span></span> <span data-ttu-id="e1f02-159">Geldige sleutel lengten zijn 16, 24 en 32 bytes.</span><span class="sxs-lookup"><span data-stu-id="e1f02-159">Valid key lengths are 16, 24 and 32 bytes.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: Open
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1f02-160">-SecureKey</span><span class="sxs-lookup"><span data-stu-id="e1f02-160">-SecureKey</span></span>

<span data-ttu-id="e1f02-161">Hiermee geeft u de versleutelings sleutel die wordt gebruikt om de oorspronkelijke beveiligde teken reeks te converteren naar de versleutelde standaard teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e1f02-161">Specifies the encryption key used to convert the original secure string into the encrypted standard string.</span></span> <span data-ttu-id="e1f02-162">De sleutel moet worden vermeld in de indeling van een beveiligde teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e1f02-162">The key must be provided in the format of a secure string.</span></span> <span data-ttu-id="e1f02-163">De beveiligde teken reeks wordt geconverteerd naar een byte matrix die als sleutel moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e1f02-163">The secure string will be converted to a byte array to be used as the key.</span></span> <span data-ttu-id="e1f02-164">Geldige veilige sleutel lengten zijn 8, 12 en 16 code punten.</span><span class="sxs-lookup"><span data-stu-id="e1f02-164">Valid secure key lengths are 8, 12 and 16 code points.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: Secure
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1f02-165">-Teken reeks</span><span class="sxs-lookup"><span data-stu-id="e1f02-165">-String</span></span>

<span data-ttu-id="e1f02-166">Hiermee geeft u de teken reeks die moet worden geconverteerd naar een beveiligde teken reeks.</span><span class="sxs-lookup"><span data-stu-id="e1f02-166">Specifies the string to convert to a secure string.</span></span>

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

### <span data-ttu-id="e1f02-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e1f02-167">CommonParameters</span></span>

<span data-ttu-id="e1f02-168">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e1f02-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e1f02-169">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e1f02-169">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e1f02-170">INVOER</span><span class="sxs-lookup"><span data-stu-id="e1f02-170">INPUTS</span></span>

### <span data-ttu-id="e1f02-171">System. String</span><span class="sxs-lookup"><span data-stu-id="e1f02-171">System.String</span></span>

<span data-ttu-id="e1f02-172">U kunt een standaard versleutelde teken reeks door sluizen naar `ConvertTo-SecureString` .</span><span class="sxs-lookup"><span data-stu-id="e1f02-172">You can pipe a standard encrypted string to `ConvertTo-SecureString`.</span></span>

## <span data-ttu-id="e1f02-173">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e1f02-173">OUTPUTS</span></span>

### <span data-ttu-id="e1f02-174">System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="e1f02-174">System.Security.SecureString</span></span>

<span data-ttu-id="e1f02-175">`ConvertTo-SecureString` retourneert een **SecureString** -object.</span><span class="sxs-lookup"><span data-stu-id="e1f02-175">`ConvertTo-SecureString` returns a **SecureString** object.</span></span>

## <span data-ttu-id="e1f02-176">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e1f02-176">NOTES</span></span>

<span data-ttu-id="e1f02-177">Sommige tekens, zoals emoticons, komen overeen met verschillende code punten in de teken reeks die ze bevatten.</span><span class="sxs-lookup"><span data-stu-id="e1f02-177">Some characters, such as emoticons, correspond to several code points in the string that contains them.</span></span> <span data-ttu-id="e1f02-178">Vermijd het gebruik van deze tekens omdat deze problemen kunnen veroorzaken en de oorzaak is van het gebruik van een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="e1f02-178">Avoid using these characters because they may cause problems and misunderstandings when used in a password.</span></span>

## <span data-ttu-id="e1f02-179">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e1f02-179">RELATED LINKS</span></span>

[<span data-ttu-id="e1f02-180">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="e1f02-180">ConvertFrom-SecureString</span></span>](ConvertFrom-SecureString.md)

[<span data-ttu-id="e1f02-181">Read-host</span><span class="sxs-lookup"><span data-stu-id="e1f02-181">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)
