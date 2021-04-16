---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 07/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: ba360e133800ae0e569643c12b1254a53aaac6ff
ms.sourcegitcommit: 366304d096c1caf52f0e17962f6ed23d20f86e7b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2021
ms.locfileid: "107543741"
---
# <span data-ttu-id="29a19-102">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="29a19-102">ConvertFrom-SecureString</span></span>

## <span data-ttu-id="29a19-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="29a19-103">SYNOPSIS</span></span>
<span data-ttu-id="29a19-104">Converteert een beveiligde tekenreeks naar een versleutelde standaardreeks.</span><span class="sxs-lookup"><span data-stu-id="29a19-104">Converts a secure string to an encrypted standard string.</span></span>

## <span data-ttu-id="29a19-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="29a19-105">SYNTAX</span></span>

### <span data-ttu-id="29a19-106">Veilig (standaard)</span><span class="sxs-lookup"><span data-stu-id="29a19-106">Secure (Default)</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### <span data-ttu-id="29a19-107">AsPlainText</span><span class="sxs-lookup"><span data-stu-id="29a19-107">AsPlainText</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-AsPlainText] [<CommonParameters>]
```

### <span data-ttu-id="29a19-108">Openen</span><span class="sxs-lookup"><span data-stu-id="29a19-108">Open</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-Key <Byte[]>] [<CommonParameters>]
```

## <span data-ttu-id="29a19-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="29a19-109">DESCRIPTION</span></span>

<span data-ttu-id="29a19-110">De **cmdlet ConvertFrom-SecureString** converteert een beveiligde tekenreeks (**System.Security.SecureString**) naar een versleutelde standaardtekenreeks (**System.String**).</span><span class="sxs-lookup"><span data-stu-id="29a19-110">The **ConvertFrom-SecureString** cmdlet converts a secure string (**System.Security.SecureString**) into an encrypted standard string (**System.String**).</span></span> <span data-ttu-id="29a19-111">In tegenstelling tot een beveiligde tekenreeks kan een versleutelde standaardreeks worden opgeslagen in een bestand voor later gebruik.</span><span class="sxs-lookup"><span data-stu-id="29a19-111">Unlike a secure string, an encrypted standard string can be saved in a file for later use.</span></span> <span data-ttu-id="29a19-112">De versleutelde standaardreeks kan met behulp van de cmdlet worden geconverteerd naar de beveiligde `ConvertTo-SecureString` tekenreeksindeling.</span><span class="sxs-lookup"><span data-stu-id="29a19-112">The encrypted standard string can be converted back to its secure string format by using the `ConvertTo-SecureString` cmdlet.</span></span>

<span data-ttu-id="29a19-113">Als een versleutelingssleutel wordt opgegeven met behulp van de parameters **Sleutel** of **SecureKey,** wordt het AES Advanced Encryption Standard-versleutelingsalgoritme gebruikt.</span><span class="sxs-lookup"><span data-stu-id="29a19-113">If an encryption key is specified by using the **Key** or **SecureKey** parameters, the Advanced Encryption Standard (AES) encryption algorithm is used.</span></span> <span data-ttu-id="29a19-114">De opgegeven sleutel moet een lengte van 128, 192 of 256 bits hebben, omdat dit de sleutellengten zijn die worden ondersteund door het AES-versleutelingsalgoritme.</span><span class="sxs-lookup"><span data-stu-id="29a19-114">The specified key must have a length of 128, 192, or 256 bits because those are the key lengths supported by the AES encryption algorithm.</span></span> <span data-ttu-id="29a19-115">Als er geen sleutel is opgegeven, wordt de Windows Data Protection API (DPAPI) gebruikt om de standaardreeksweergave te versleutelen.</span><span class="sxs-lookup"><span data-stu-id="29a19-115">If no key is specified, the Windows Data Protection API (DPAPI) is used to encrypt the standard string representation.</span></span>

> [!NOTE]
> <span data-ttu-id="29a19-116">Houd er rekening mee dat de inhoud van een SecureString per [DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks)niet is versleuteld op niet-Windows-systemen.</span><span class="sxs-lookup"><span data-stu-id="29a19-116">Note that per [DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks), the contents of a SecureString are not encrypted on non-Windows systems.</span></span>

## <span data-ttu-id="29a19-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="29a19-117">EXAMPLES</span></span>

### <span data-ttu-id="29a19-118">Voorbeeld 1: Een beveiligde tekenreeks maken</span><span class="sxs-lookup"><span data-stu-id="29a19-118">Example 1: Create a secure string</span></span>

```powershell
$SecureString = Read-Host -AsSecureString
```

<span data-ttu-id="29a19-119">Met deze opdracht maakt u een beveiligde tekenreeks van tekens die u typt bij de opdrachtprompt.</span><span class="sxs-lookup"><span data-stu-id="29a19-119">This command creates a secure string from characters that you type at the command prompt.</span></span> <span data-ttu-id="29a19-120">Nadat u de opdracht hebt invoeren, typt u de tekenreeks die u wilt opslaan als een beveiligde tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="29a19-120">After entering the command, type the string you want to store as a secure string.</span></span> <span data-ttu-id="29a19-121">Er wordt een sterretje () weergegeven om elk teken dat u typt `*` weer te geven.</span><span class="sxs-lookup"><span data-stu-id="29a19-121">An asterisk (`*`) is displayed to represent each character that you type.</span></span>

### <span data-ttu-id="29a19-122">Voorbeeld 2: Een beveiligde tekenreeks converteren naar een versleutelde standaardreeks</span><span class="sxs-lookup"><span data-stu-id="29a19-122">Example 2: Convert a secure string to an encrypted standard string</span></span>

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

<span data-ttu-id="29a19-123">Met deze opdracht wordt de beveiligde tekenreeks in de `$SecureString` variabele ge converteerd naar een versleutelde standaardreeks.</span><span class="sxs-lookup"><span data-stu-id="29a19-123">This command converts the secure string in the `$SecureString` variable to an encrypted standard string.</span></span> <span data-ttu-id="29a19-124">De resulterende versleutelde standaardreeks wordt opgeslagen in de `$StandardString` variabele .</span><span class="sxs-lookup"><span data-stu-id="29a19-124">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

### <span data-ttu-id="29a19-125">Voorbeeld 3: Een beveiligde tekenreeks converteren naar een versleutelde standaardreeks met een 192-bits sleutel</span><span class="sxs-lookup"><span data-stu-id="29a19-125">Example 3: Convert a secure string to an encrypted standard string with a 192-bit key</span></span>

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

<span data-ttu-id="29a19-126">Deze opdrachten gebruiken het AES-algoritme (Advanced Encryption Standard) om de beveiligde tekenreeks die is opgeslagen in de variabele te converteren naar een versleutelde standaardreeks met een `$SecureString` 192-bits sleutel.</span><span class="sxs-lookup"><span data-stu-id="29a19-126">These commands use the Advanced Encryption Standard (AES) algorithm to convert the secure string stored in the `$SecureString` variable to an encrypted standard string with a 192-bit key.</span></span> <span data-ttu-id="29a19-127">De resulterende versleutelde standaardreeks wordt opgeslagen in de `$StandardString` variabele .</span><span class="sxs-lookup"><span data-stu-id="29a19-127">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

<span data-ttu-id="29a19-128">De eerste opdracht slaat een sleutel op in de `$Key` variabele .</span><span class="sxs-lookup"><span data-stu-id="29a19-128">The first command stores a key in the `$Key` variable.</span></span> <span data-ttu-id="29a19-129">De sleutel is een matrix van 24 decimale cijfers, die elk minder dan 256 moeten zijn om binnen één niet-ondertekende byte te passen.</span><span class="sxs-lookup"><span data-stu-id="29a19-129">The key is an array of 24 decimal numerals, each of which must be less than 256 to fit within a single unsigned byte.</span></span>

<span data-ttu-id="29a19-130">Omdat elk decimaal getal één byte (8 bits) vertegenwoordigt, heeft de sleutel 24 cijfers voor een totaal van 192 bits (8 x 24).</span><span class="sxs-lookup"><span data-stu-id="29a19-130">Because each decimal numeral represents a single byte (8 bits), the key has 24 digits for a total of 192 bits (8 x 24).</span></span> <span data-ttu-id="29a19-131">Dit is een geldige sleutellengte voor het AES-algoritme.</span><span class="sxs-lookup"><span data-stu-id="29a19-131">This is a valid key length for the AES algorithm.</span></span>

<span data-ttu-id="29a19-132">De tweede opdracht maakt gebruik van de sleutel in de `$Key` variabele om de beveiligde tekenreeks te converteren naar een versleutelde standaardreeks.</span><span class="sxs-lookup"><span data-stu-id="29a19-132">The second command uses the key in the `$Key` variable to convert the secure string to an encrypted standard string.</span></span>

### <span data-ttu-id="29a19-133">Voorbeeld 4: Een beveiligde tekenreeks rechtstreeks converteren naar een tekst zonder tekst</span><span class="sxs-lookup"><span data-stu-id="29a19-133">Example 4: Convert a secure string directly to a plaintext string</span></span>

```powershell
$secureString = ConvertTo-SecureString -String 'Example' -AsPlainText
$secureString # 'System.Security.SecureString'
ConvertFrom-SecureString -SecureString $secureString -AsPlainText # 'Example'
```

## <span data-ttu-id="29a19-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="29a19-134">PARAMETERS</span></span>

### <span data-ttu-id="29a19-135">-AsPlainText</span><span class="sxs-lookup"><span data-stu-id="29a19-135">-AsPlainText</span></span>

<span data-ttu-id="29a19-136">Wanneer deze is ingesteld, `ConvertFrom-SecureString` converteert beveiligde tekenreeksen naar de ontsleutelde tekst zonder tekst als uitvoer.</span><span class="sxs-lookup"><span data-stu-id="29a19-136">When set, `ConvertFrom-SecureString` will convert secure strings to the decrypted plaintext string as output.</span></span>

<span data-ttu-id="29a19-137">Deze parameter is toegevoegd in PowerShell 7.0.</span><span class="sxs-lookup"><span data-stu-id="29a19-137">This parameter was added in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsPlainText
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="29a19-138">-Key</span><span class="sxs-lookup"><span data-stu-id="29a19-138">-Key</span></span>

<span data-ttu-id="29a19-139">Hiermee geeft u de versleutelingssleutel op als een bytematrix.</span><span class="sxs-lookup"><span data-stu-id="29a19-139">Specifies the encryption key as a byte array.</span></span>

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

### <span data-ttu-id="29a19-140">-SecureKey</span><span class="sxs-lookup"><span data-stu-id="29a19-140">-SecureKey</span></span>

<span data-ttu-id="29a19-141">Hiermee geeft u de versleutelingssleutel als een beveiligde tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="29a19-141">Specifies the encryption key as a secure string.</span></span> <span data-ttu-id="29a19-142">De waarde van de beveiligde tekenreeks wordt geconverteerd naar een bytematrice voordat deze als sleutel wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="29a19-142">The secure string value is converted to a byte array before being used as the key.</span></span>

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

### <span data-ttu-id="29a19-143">-SecureString</span><span class="sxs-lookup"><span data-stu-id="29a19-143">-SecureString</span></span>

<span data-ttu-id="29a19-144">Hiermee geeft u de beveiligde tekenreeks om te converteren naar een versleutelde standaardreeks.</span><span class="sxs-lookup"><span data-stu-id="29a19-144">Specifies the secure string to convert to an encrypted standard string.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="29a19-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="29a19-145">CommonParameters</span></span>

<span data-ttu-id="29a19-146">Deze cmdlet ondersteunt de algemene parameters: `-Debug` , , , , , , , , `-ErrorAction` , , en `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="29a19-146">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`,`-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span>
<span data-ttu-id="29a19-147">Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="29a19-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="29a19-148">INVOER</span><span class="sxs-lookup"><span data-stu-id="29a19-148">INPUTS</span></span>

### <span data-ttu-id="29a19-149">System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="29a19-149">System.Security.SecureString</span></span>

<span data-ttu-id="29a19-150">U kunt een **SecureString-object** doorspijpen naar ConvertFrom-SecureString.</span><span class="sxs-lookup"><span data-stu-id="29a19-150">You can pipe a **SecureString** object to ConvertFrom-SecureString.</span></span>

## <span data-ttu-id="29a19-151">UITVOER</span><span class="sxs-lookup"><span data-stu-id="29a19-151">OUTPUTS</span></span>

### <span data-ttu-id="29a19-152">System.String</span><span class="sxs-lookup"><span data-stu-id="29a19-152">System.String</span></span>

<span data-ttu-id="29a19-153">ConvertFrom-SecureString retourneert een standaard-tekenreeksobject.</span><span class="sxs-lookup"><span data-stu-id="29a19-153">ConvertFrom-SecureString returns a standard string object.</span></span>

## <span data-ttu-id="29a19-154">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="29a19-154">NOTES</span></span>

- <span data-ttu-id="29a19-155">Als u een beveiligde tekenreeks wilt maken van tekens die zijn getypt bij de opdrachtprompt, gebruikt u de parameter **AsSecureString** van de `Read-Host` cmdlet .</span><span class="sxs-lookup"><span data-stu-id="29a19-155">To create a secure string from characters that are typed at the command prompt, use the **AsSecureString** parameter of the `Read-Host` cmdlet.</span></span>
- <span data-ttu-id="29a19-156">Wanneer u de parameters **Sleutel** of **SecureKey gebruikt om** een sleutel op te geven, moet de sleutellengte juist zijn.</span><span class="sxs-lookup"><span data-stu-id="29a19-156">When you use the **Key** or **SecureKey** parameters to specify a key, the key length must be correct.</span></span> <span data-ttu-id="29a19-157">Een sleutel van 128 bits kan bijvoorbeeld worden opgegeven als een bytematrix van 16 decimale cijfers.</span><span class="sxs-lookup"><span data-stu-id="29a19-157">For example, a key of 128 bits can be specified as a byte array of 16 decimal numerals.</span></span>
  <span data-ttu-id="29a19-158">Op dezelfde manier komen 192-bits en 256-bits sleutels overeen met bytematrixen van respectievelijk 24 en 32 decimalen.</span><span class="sxs-lookup"><span data-stu-id="29a19-158">Similarly, 192-bit and 256-bit keys correspond to byte arrays of 24 and 32 decimal numerals, respectively.</span></span>
- <span data-ttu-id="29a19-159">Sommige tekens, zoals emoticons, komen overeen met verschillende codepunten in de tekenreeks die ze bevat.</span><span class="sxs-lookup"><span data-stu-id="29a19-159">Some characters, such as emoticons, correspond to several code points in the string that contains them.</span></span> <span data-ttu-id="29a19-160">Vermijd het gebruik van deze tekens omdat deze problemen en misvattingen kunnen veroorzaken bij gebruik in een wachtwoord.</span><span class="sxs-lookup"><span data-stu-id="29a19-160">Avoid using these characters because they may cause problems and misunderstandings when used in a password.</span></span>

## <span data-ttu-id="29a19-161">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="29a19-161">RELATED LINKS</span></span>

[<span data-ttu-id="29a19-162">ConvertTo-SecureString</span><span class="sxs-lookup"><span data-stu-id="29a19-162">ConvertTo-SecureString</span></span>](ConvertTo-SecureString.md)

[<span data-ttu-id="29a19-163">Read-Host</span><span class="sxs-lookup"><span data-stu-id="29a19-163">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)
