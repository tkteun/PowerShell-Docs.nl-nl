---
external help file: Microsoft.PowerShell.Security.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: 4dae7806cbec85347a8dfa01348be72061214c6c
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/09/2020
ms.locfileid: "93251430"
---
# <span data-ttu-id="a7ca3-103">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="a7ca3-103">ConvertFrom-SecureString</span></span>

## <span data-ttu-id="a7ca3-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a7ca3-104">SYNOPSIS</span></span>
<span data-ttu-id="a7ca3-105">Converteert een beveiligde teken reeks naar een versleutelde standaard teken reeks.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-105">Converts a secure string to an encrypted standard string.</span></span>

## <span data-ttu-id="a7ca3-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a7ca3-106">SYNTAX</span></span>

### <span data-ttu-id="a7ca3-107">Beveiligd (standaard)</span><span class="sxs-lookup"><span data-stu-id="a7ca3-107">Secure (Default)</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### <span data-ttu-id="a7ca3-108">Openen</span><span class="sxs-lookup"><span data-stu-id="a7ca3-108">Open</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-Key <Byte[]>] [<CommonParameters>]
```

## <span data-ttu-id="a7ca3-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a7ca3-109">DESCRIPTION</span></span>

<span data-ttu-id="a7ca3-110">Met de cmdlet **ConvertFrom-SecureString** wordt een beveiligde teken reeks ( **System. Security. SecureString** ) geconverteerd naar een versleutelde standaard teken reeks ( **System. String** ).</span><span class="sxs-lookup"><span data-stu-id="a7ca3-110">The **ConvertFrom-SecureString** cmdlet converts a secure string ( **System.Security.SecureString** ) into an encrypted standard string ( **System.String** ).</span></span> <span data-ttu-id="a7ca3-111">In tegens telling tot een beveiligde teken reeks kan een gecodeerde standaard teken reeks worden opgeslagen in een bestand voor later gebruik.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-111">Unlike a secure string, an encrypted standard string can be saved in a file for later use.</span></span> <span data-ttu-id="a7ca3-112">De versleutelde standaard teken reeks kan worden teruggeconverteerd naar de beveiligde teken reeks indeling met behulp van de- `ConvertTo-SecureString` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-112">The encrypted standard string can be converted back to its secure string format by using the `ConvertTo-SecureString` cmdlet.</span></span>

<span data-ttu-id="a7ca3-113">Als een versleutelings sleutel is opgegeven met behulp van de **sleutel** -of **SecureKey** para meters, wordt het versleutelings ALGORITME voor Advanced Encryption Standard (AES) gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-113">If an encryption key is specified by using the **Key** or **SecureKey** parameters, the Advanced Encryption Standard (AES) encryption algorithm is used.</span></span> <span data-ttu-id="a7ca3-114">De opgegeven sleutel moet een lengte hebben van 128, 192 of 256 bits, omdat dit de sleutel lengtes zijn die worden ondersteund door de AES-versleutelings algoritme.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-114">The specified key must have a length of 128, 192, or 256 bits because those are the key lengths supported by the AES encryption algorithm.</span></span> <span data-ttu-id="a7ca3-115">Als er geen sleutel is opgegeven, wordt de Windows Data Protection API (DPAPI) gebruikt om de standaard teken reeks representatie te versleutelen.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-115">If no key is specified, the Windows Data Protection API (DPAPI) is used to encrypt the standard string representation.</span></span>

## <span data-ttu-id="a7ca3-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a7ca3-116">EXAMPLES</span></span>

### <span data-ttu-id="a7ca3-117">Voor beeld 1: een veilige teken reeks maken</span><span class="sxs-lookup"><span data-stu-id="a7ca3-117">Example 1: Create a secure string</span></span>

```powershell
$SecureString = Read-Host -AsSecureString
```

<span data-ttu-id="a7ca3-118">Met deze opdracht maakt u een beveiligde teken reeks van tekens die u typt bij de opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-118">This command creates a secure string from characters that you type at the command prompt.</span></span> <span data-ttu-id="a7ca3-119">Nadat u de opdracht hebt ingevoerd, typt u de teken reeks die u wilt opslaan als een veilige teken reeks.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-119">After entering the command, type the string you want to store as a secure string.</span></span> <span data-ttu-id="a7ca3-120">Er wordt een asterisk ( `*` ) weer gegeven voor elk teken dat u typt.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-120">An asterisk (`*`) is displayed to represent each character that you type.</span></span>

### <span data-ttu-id="a7ca3-121">Voor beeld 2: een beveiligde teken reeks converteren naar een versleutelde standaard teken reeks</span><span class="sxs-lookup"><span data-stu-id="a7ca3-121">Example 2: Convert a secure string to an encrypted standard string</span></span>

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

<span data-ttu-id="a7ca3-122">Met deze opdracht wordt de beveiligde teken reeks in de `$SecureString` variabele geconverteerd naar een versleutelde standaard teken reeks.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-122">This command converts the secure string in the `$SecureString` variable to an encrypted standard string.</span></span> <span data-ttu-id="a7ca3-123">De resulterende versleutelde standaard teken reeks wordt opgeslagen in de `$StandardString` variabele.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-123">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

### <span data-ttu-id="a7ca3-124">Voor beeld 3: een beveiligde teken reeks converteren naar een versleutelde standaard teken reeks met een 192-bits sleutel</span><span class="sxs-lookup"><span data-stu-id="a7ca3-124">Example 3: Convert a secure string to an encrypted standard string with a 192-bit key</span></span>

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

<span data-ttu-id="a7ca3-125">Deze opdrachten gebruiken het Advanced Encryption Standard (AES)-algoritme voor het converteren van de beveiligde teken reeks die is opgeslagen in de `$SecureString` variabele naar een versleutelde standaard teken reeks met een 192-bits sleutel.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-125">These commands use the Advanced Encryption Standard (AES) algorithm to convert the secure string stored in the `$SecureString` variable to an encrypted standard string with a 192-bit key.</span></span> <span data-ttu-id="a7ca3-126">De resulterende versleutelde standaard teken reeks wordt opgeslagen in de `$StandardString` variabele.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-126">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

<span data-ttu-id="a7ca3-127">Met de eerste opdracht wordt een sleutel in de `$Key` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-127">The first command stores a key in the `$Key` variable.</span></span> <span data-ttu-id="a7ca3-128">De sleutel is een matrix van 24 decimale cijfers, die elk kleiner dan 256 moeten zijn om te passen binnen één niet-ondertekende byte.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-128">The key is an array of 24 decimal numerals, each of which must be less than 256 to fit within a single unsigned byte.</span></span>

<span data-ttu-id="a7ca3-129">Omdat elk decimaal getal bestaat uit één byte (8 bits), heeft de sleutel 24 cijfers voor een totaal van 192 bits (8 x 24).</span><span class="sxs-lookup"><span data-stu-id="a7ca3-129">Because each decimal numeral represents a single byte (8 bits), the key has 24 digits for a total of 192 bits (8 x 24).</span></span> <span data-ttu-id="a7ca3-130">Dit is een geldige sleutel lengte voor het AES-algoritme.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-130">This is a valid key length for the AES algorithm.</span></span>

<span data-ttu-id="a7ca3-131">Met de tweede opdracht wordt de sleutel in de `$Key` variabele gebruikt om de beveiligde teken reeks om te zetten in een versleutelde standaard teken reeks.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-131">The second command uses the key in the `$Key` variable to convert the secure string to an encrypted standard string.</span></span>

## <span data-ttu-id="a7ca3-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a7ca3-132">PARAMETERS</span></span>

### <span data-ttu-id="a7ca3-133">-Sleutel</span><span class="sxs-lookup"><span data-stu-id="a7ca3-133">-Key</span></span>

<span data-ttu-id="a7ca3-134">Hiermee geeft u de versleutelings sleutel als een byte matrix.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-134">Specifies the encryption key as a byte array.</span></span>

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

### <span data-ttu-id="a7ca3-135">-SecureKey</span><span class="sxs-lookup"><span data-stu-id="a7ca3-135">-SecureKey</span></span>

<span data-ttu-id="a7ca3-136">Hiermee geeft u de versleutelings sleutel als een beveiligde teken reeks.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-136">Specifies the encryption key as a secure string.</span></span> <span data-ttu-id="a7ca3-137">De waarde van de beveiligde teken reeks wordt geconverteerd naar een byte matrix voordat deze wordt gebruikt als de sleutel.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-137">The secure string value is converted to a byte array before being used as the key.</span></span>

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

### <span data-ttu-id="a7ca3-138">-SecureString</span><span class="sxs-lookup"><span data-stu-id="a7ca3-138">-SecureString</span></span>

<span data-ttu-id="a7ca3-139">Hiermee geeft u de beveiligde teken reeks op die moet worden geconverteerd naar een versleutelde standaard teken reeks.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-139">Specifies the secure string to convert to an encrypted standard string.</span></span>

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

### <span data-ttu-id="a7ca3-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a7ca3-140">CommonParameters</span></span>

<span data-ttu-id="a7ca3-141">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a7ca3-142">Zie about_CommonParameters (voor meer informatie https://go.microsoft.com/fwlink/?LinkID=113216) .</span><span class="sxs-lookup"><span data-stu-id="a7ca3-142">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a7ca3-143">INVOER</span><span class="sxs-lookup"><span data-stu-id="a7ca3-143">INPUTS</span></span>

### <span data-ttu-id="a7ca3-144">System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="a7ca3-144">System.Security.SecureString</span></span>

<span data-ttu-id="a7ca3-145">U kunt een **SecureString** -object door sluizen naar ConvertFrom-SecureString.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-145">You can pipe a **SecureString** object to ConvertFrom-SecureString.</span></span>

## <span data-ttu-id="a7ca3-146">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a7ca3-146">OUTPUTS</span></span>

### <span data-ttu-id="a7ca3-147">System. String</span><span class="sxs-lookup"><span data-stu-id="a7ca3-147">System.String</span></span>

<span data-ttu-id="a7ca3-148">ConvertFrom-SecureString retourneert een standaard teken reeks object.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-148">ConvertFrom-SecureString returns a standard string object.</span></span>

## <span data-ttu-id="a7ca3-149">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a7ca3-149">NOTES</span></span>

- <span data-ttu-id="a7ca3-150">Gebruik de para meter **AsSecureString** van de cmdlet om een beveiligde teken reeks te maken van tekens die worden getypt bij de opdracht prompt `Read-Host` .</span><span class="sxs-lookup"><span data-stu-id="a7ca3-150">To create a secure string from characters that are typed at the command prompt, use the **AsSecureString** parameter of the `Read-Host` cmdlet.</span></span>
- <span data-ttu-id="a7ca3-151">Wanneer u de para meters **Key** of **SecureKey** gebruikt om een sleutel op te geven, moet de sleutel lengte juist zijn.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-151">When you use the **Key** or **SecureKey** parameters to specify a key, the key length must be correct.</span></span> <span data-ttu-id="a7ca3-152">Een sleutel van 128 bits kan bijvoorbeeld worden opgegeven als een byte matrix van 16 decimalen.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-152">For example, a key of 128 bits can be specified as a byte array of 16 decimal numerals.</span></span>
  <span data-ttu-id="a7ca3-153">Op dezelfde manier komen 192 bits-en 256-bits sleutels overeen met een byte matrix van respectievelijk 24 en 32 decimale cijfers.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-153">Similarly, 192-bit and 256-bit keys correspond to byte arrays of 24 and 32 decimal numerals, respectively.</span></span>
- <span data-ttu-id="a7ca3-154">Sommige tekens, zoals emoticons, komen overeen met verschillende code punten in de teken reeks die ze bevatten.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-154">Some characters, such as emoticons, correspond to several code points in the string that contains them.</span></span> <span data-ttu-id="a7ca3-155">Vermijd het gebruik van deze tekens omdat deze problemen kunnen veroorzaken en de oorzaak is van het gebruik van een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="a7ca3-155">Avoid using these characters because they may cause problems and misunderstandings when used in a password.</span></span>

## <span data-ttu-id="a7ca3-156">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a7ca3-156">RELATED LINKS</span></span>

[<span data-ttu-id="a7ca3-157">ConvertTo-SecureString</span><span class="sxs-lookup"><span data-stu-id="a7ca3-157">ConvertTo-SecureString</span></span>](ConvertTo-SecureString.md)

[<span data-ttu-id="a7ca3-158">Read-host</span><span class="sxs-lookup"><span data-stu-id="a7ca3-158">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)
