---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: 8a151da1b60b1956e580f9a0393d4eb137ef3447
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/09/2020
ms.locfileid: "93251424"
---
# <span data-ttu-id="c2b26-103">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="c2b26-103">ConvertFrom-SecureString</span></span>

## <span data-ttu-id="c2b26-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c2b26-104">SYNOPSIS</span></span>
<span data-ttu-id="c2b26-105">Converteert een beveiligde teken reeks naar een versleutelde standaard teken reeks.</span><span class="sxs-lookup"><span data-stu-id="c2b26-105">Converts a secure string to an encrypted standard string.</span></span>

## <span data-ttu-id="c2b26-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c2b26-106">SYNTAX</span></span>

### <span data-ttu-id="c2b26-107">Beveiligd (standaard)</span><span class="sxs-lookup"><span data-stu-id="c2b26-107">Secure (Default)</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### <span data-ttu-id="c2b26-108">Openen</span><span class="sxs-lookup"><span data-stu-id="c2b26-108">Open</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-Key <Byte[]>] [<CommonParameters>]
```

## <span data-ttu-id="c2b26-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c2b26-109">DESCRIPTION</span></span>

<span data-ttu-id="c2b26-110">Met de cmdlet **ConvertFrom-SecureString** wordt een beveiligde teken reeks ( **System. Security. SecureString** ) geconverteerd naar een versleutelde standaard teken reeks ( **System. String** ).</span><span class="sxs-lookup"><span data-stu-id="c2b26-110">The **ConvertFrom-SecureString** cmdlet converts a secure string ( **System.Security.SecureString** ) into an encrypted standard string ( **System.String** ).</span></span> <span data-ttu-id="c2b26-111">In tegens telling tot een beveiligde teken reeks kan een gecodeerde standaard teken reeks worden opgeslagen in een bestand voor later gebruik.</span><span class="sxs-lookup"><span data-stu-id="c2b26-111">Unlike a secure string, an encrypted standard string can be saved in a file for later use.</span></span> <span data-ttu-id="c2b26-112">De versleutelde standaard teken reeks kan worden teruggeconverteerd naar de beveiligde teken reeks indeling met behulp van de- `ConvertTo-SecureString` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c2b26-112">The encrypted standard string can be converted back to its secure string format by using the `ConvertTo-SecureString` cmdlet.</span></span>

<span data-ttu-id="c2b26-113">Als een versleutelings sleutel is opgegeven met behulp van de **sleutel** -of **SecureKey** para meters, wordt het versleutelings ALGORITME voor Advanced Encryption Standard (AES) gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c2b26-113">If an encryption key is specified by using the **Key** or **SecureKey** parameters, the Advanced Encryption Standard (AES) encryption algorithm is used.</span></span> <span data-ttu-id="c2b26-114">De opgegeven sleutel moet een lengte hebben van 128, 192 of 256 bits, omdat dit de sleutel lengtes zijn die worden ondersteund door de AES-versleutelings algoritme.</span><span class="sxs-lookup"><span data-stu-id="c2b26-114">The specified key must have a length of 128, 192, or 256 bits because those are the key lengths supported by the AES encryption algorithm.</span></span> <span data-ttu-id="c2b26-115">Als er geen sleutel is opgegeven, wordt de Windows Data Protection API (DPAPI) gebruikt om de standaard teken reeks representatie te versleutelen.</span><span class="sxs-lookup"><span data-stu-id="c2b26-115">If no key is specified, the Windows Data Protection API (DPAPI) is used to encrypt the standard string representation.</span></span>

> [!NOTE]
> <span data-ttu-id="c2b26-116">Houd er rekening mee dat de inhoud van een SecureString per [DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks)niet wordt versleuteld op niet-Windows-systemen.</span><span class="sxs-lookup"><span data-stu-id="c2b26-116">Note that per [DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks), the contents of a SecureString are not encrypted on non-Windows systems.</span></span>

## <span data-ttu-id="c2b26-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c2b26-117">EXAMPLES</span></span>

### <span data-ttu-id="c2b26-118">Voor beeld 1: een veilige teken reeks maken</span><span class="sxs-lookup"><span data-stu-id="c2b26-118">Example 1: Create a secure string</span></span>

```powershell
$SecureString = Read-Host -AsSecureString
```

<span data-ttu-id="c2b26-119">Met deze opdracht maakt u een beveiligde teken reeks van tekens die u typt bij de opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="c2b26-119">This command creates a secure string from characters that you type at the command prompt.</span></span> <span data-ttu-id="c2b26-120">Nadat u de opdracht hebt ingevoerd, typt u de teken reeks die u wilt opslaan als een veilige teken reeks.</span><span class="sxs-lookup"><span data-stu-id="c2b26-120">After entering the command, type the string you want to store as a secure string.</span></span> <span data-ttu-id="c2b26-121">Er wordt een asterisk ( `*` ) weer gegeven voor elk teken dat u typt.</span><span class="sxs-lookup"><span data-stu-id="c2b26-121">An asterisk (`*`) is displayed to represent each character that you type.</span></span>

### <span data-ttu-id="c2b26-122">Voor beeld 2: een beveiligde teken reeks converteren naar een versleutelde standaard teken reeks</span><span class="sxs-lookup"><span data-stu-id="c2b26-122">Example 2: Convert a secure string to an encrypted standard string</span></span>

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

<span data-ttu-id="c2b26-123">Met deze opdracht wordt de beveiligde teken reeks in de `$SecureString` variabele geconverteerd naar een versleutelde standaard teken reeks.</span><span class="sxs-lookup"><span data-stu-id="c2b26-123">This command converts the secure string in the `$SecureString` variable to an encrypted standard string.</span></span> <span data-ttu-id="c2b26-124">De resulterende versleutelde standaard teken reeks wordt opgeslagen in de `$StandardString` variabele.</span><span class="sxs-lookup"><span data-stu-id="c2b26-124">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

### <span data-ttu-id="c2b26-125">Voor beeld 3: een beveiligde teken reeks converteren naar een versleutelde standaard teken reeks met een 192-bits sleutel</span><span class="sxs-lookup"><span data-stu-id="c2b26-125">Example 3: Convert a secure string to an encrypted standard string with a 192-bit key</span></span>

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

<span data-ttu-id="c2b26-126">Deze opdrachten gebruiken het Advanced Encryption Standard (AES)-algoritme voor het converteren van de beveiligde teken reeks die is opgeslagen in de `$SecureString` variabele naar een versleutelde standaard teken reeks met een 192-bits sleutel.</span><span class="sxs-lookup"><span data-stu-id="c2b26-126">These commands use the Advanced Encryption Standard (AES) algorithm to convert the secure string stored in the `$SecureString` variable to an encrypted standard string with a 192-bit key.</span></span> <span data-ttu-id="c2b26-127">De resulterende versleutelde standaard teken reeks wordt opgeslagen in de `$StandardString` variabele.</span><span class="sxs-lookup"><span data-stu-id="c2b26-127">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

<span data-ttu-id="c2b26-128">Met de eerste opdracht wordt een sleutel in de `$Key` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="c2b26-128">The first command stores a key in the `$Key` variable.</span></span> <span data-ttu-id="c2b26-129">De sleutel is een matrix van 24 decimale cijfers, die elk kleiner dan 256 moeten zijn om te passen binnen één niet-ondertekende byte.</span><span class="sxs-lookup"><span data-stu-id="c2b26-129">The key is an array of 24 decimal numerals, each of which must be less than 256 to fit within a single unsigned byte.</span></span>

<span data-ttu-id="c2b26-130">Omdat elk decimaal getal bestaat uit één byte (8 bits), heeft de sleutel 24 cijfers voor een totaal van 192 bits (8 x 24).</span><span class="sxs-lookup"><span data-stu-id="c2b26-130">Because each decimal numeral represents a single byte (8 bits), the key has 24 digits for a total of 192 bits (8 x 24).</span></span> <span data-ttu-id="c2b26-131">Dit is een geldige sleutel lengte voor het AES-algoritme.</span><span class="sxs-lookup"><span data-stu-id="c2b26-131">This is a valid key length for the AES algorithm.</span></span>

<span data-ttu-id="c2b26-132">Met de tweede opdracht wordt de sleutel in de `$Key` variabele gebruikt om de beveiligde teken reeks om te zetten in een versleutelde standaard teken reeks.</span><span class="sxs-lookup"><span data-stu-id="c2b26-132">The second command uses the key in the `$Key` variable to convert the secure string to an encrypted standard string.</span></span>

## <span data-ttu-id="c2b26-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c2b26-133">PARAMETERS</span></span>

### <span data-ttu-id="c2b26-134">-Sleutel</span><span class="sxs-lookup"><span data-stu-id="c2b26-134">-Key</span></span>

<span data-ttu-id="c2b26-135">Hiermee geeft u de versleutelings sleutel als een byte matrix.</span><span class="sxs-lookup"><span data-stu-id="c2b26-135">Specifies the encryption key as a byte array.</span></span>

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

### <span data-ttu-id="c2b26-136">-SecureKey</span><span class="sxs-lookup"><span data-stu-id="c2b26-136">-SecureKey</span></span>

<span data-ttu-id="c2b26-137">Hiermee geeft u de versleutelings sleutel als een beveiligde teken reeks.</span><span class="sxs-lookup"><span data-stu-id="c2b26-137">Specifies the encryption key as a secure string.</span></span> <span data-ttu-id="c2b26-138">De waarde van de beveiligde teken reeks wordt geconverteerd naar een byte matrix voordat deze wordt gebruikt als de sleutel.</span><span class="sxs-lookup"><span data-stu-id="c2b26-138">The secure string value is converted to a byte array before being used as the key.</span></span>

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

### <span data-ttu-id="c2b26-139">-SecureString</span><span class="sxs-lookup"><span data-stu-id="c2b26-139">-SecureString</span></span>

<span data-ttu-id="c2b26-140">Hiermee geeft u de beveiligde teken reeks op die moet worden geconverteerd naar een versleutelde standaard teken reeks.</span><span class="sxs-lookup"><span data-stu-id="c2b26-140">Specifies the secure string to convert to an encrypted standard string.</span></span>

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

### <span data-ttu-id="c2b26-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c2b26-141">CommonParameters</span></span>

<span data-ttu-id="c2b26-142">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="c2b26-142">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`,`-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span>
<span data-ttu-id="c2b26-143">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c2b26-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c2b26-144">INVOER</span><span class="sxs-lookup"><span data-stu-id="c2b26-144">INPUTS</span></span>

### <span data-ttu-id="c2b26-145">System. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="c2b26-145">System.Security.SecureString</span></span>

<span data-ttu-id="c2b26-146">U kunt een **SecureString** -object door sluizen naar ConvertFrom-SecureString.</span><span class="sxs-lookup"><span data-stu-id="c2b26-146">You can pipe a **SecureString** object to ConvertFrom-SecureString.</span></span>

## <span data-ttu-id="c2b26-147">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c2b26-147">OUTPUTS</span></span>

### <span data-ttu-id="c2b26-148">System. String</span><span class="sxs-lookup"><span data-stu-id="c2b26-148">System.String</span></span>

<span data-ttu-id="c2b26-149">ConvertFrom-SecureString retourneert een standaard teken reeks object.</span><span class="sxs-lookup"><span data-stu-id="c2b26-149">ConvertFrom-SecureString returns a standard string object.</span></span>

## <span data-ttu-id="c2b26-150">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c2b26-150">NOTES</span></span>

- <span data-ttu-id="c2b26-151">Gebruik de para meter **AsSecureString** van de cmdlet om een beveiligde teken reeks te maken van tekens die worden getypt bij de opdracht prompt `Read-Host` .</span><span class="sxs-lookup"><span data-stu-id="c2b26-151">To create a secure string from characters that are typed at the command prompt, use the **AsSecureString** parameter of the `Read-Host` cmdlet.</span></span>
- <span data-ttu-id="c2b26-152">Wanneer u de para meters **Key** of **SecureKey** gebruikt om een sleutel op te geven, moet de sleutel lengte juist zijn.</span><span class="sxs-lookup"><span data-stu-id="c2b26-152">When you use the **Key** or **SecureKey** parameters to specify a key, the key length must be correct.</span></span> <span data-ttu-id="c2b26-153">Een sleutel van 128 bits kan bijvoorbeeld worden opgegeven als een byte matrix van 16 decimalen.</span><span class="sxs-lookup"><span data-stu-id="c2b26-153">For example, a key of 128 bits can be specified as a byte array of 16 decimal numerals.</span></span>
  <span data-ttu-id="c2b26-154">Op dezelfde manier komen 192 bits-en 256-bits sleutels overeen met een byte matrix van respectievelijk 24 en 32 decimale cijfers.</span><span class="sxs-lookup"><span data-stu-id="c2b26-154">Similarly, 192-bit and 256-bit keys correspond to byte arrays of 24 and 32 decimal numerals, respectively.</span></span>
- <span data-ttu-id="c2b26-155">Sommige tekens, zoals emoticons, komen overeen met verschillende code punten in de teken reeks die ze bevatten.</span><span class="sxs-lookup"><span data-stu-id="c2b26-155">Some characters, such as emoticons, correspond to several code points in the string that contains them.</span></span> <span data-ttu-id="c2b26-156">Vermijd het gebruik van deze tekens omdat deze problemen kunnen veroorzaken en de oorzaak is van het gebruik van een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="c2b26-156">Avoid using these characters because they may cause problems and misunderstandings when used in a password.</span></span>

## <span data-ttu-id="c2b26-157">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c2b26-157">RELATED LINKS</span></span>

[<span data-ttu-id="c2b26-158">ConvertTo-SecureString</span><span class="sxs-lookup"><span data-stu-id="c2b26-158">ConvertTo-SecureString</span></span>](ConvertTo-SecureString.md)

[<span data-ttu-id="c2b26-159">Read-host</span><span class="sxs-lookup"><span data-stu-id="c2b26-159">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)
