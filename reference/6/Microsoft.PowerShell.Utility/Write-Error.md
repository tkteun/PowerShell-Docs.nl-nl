---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-error?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Error
ms.openlocfilehash: d5f7002eea35924117753d0f73b40e9d9243c64e
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "93252987"
---
# <span data-ttu-id="00094-103">Write-Error</span><span class="sxs-lookup"><span data-stu-id="00094-103">Write-Error</span></span>

## <span data-ttu-id="00094-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="00094-104">SYNOPSIS</span></span>
<span data-ttu-id="00094-105">Schrijft een object naar de fout stroom.</span><span class="sxs-lookup"><span data-stu-id="00094-105">Writes an object to the error stream.</span></span>

## <span data-ttu-id="00094-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="00094-106">SYNTAX</span></span>

### <span data-ttu-id="00094-107">Except (standaard)</span><span class="sxs-lookup"><span data-stu-id="00094-107">NoException (Default)</span></span>

```
Write-Error [-Message] <String> [-Category <ErrorCategory>] [-ErrorId <String>] [-TargetObject <Object>]
 [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="00094-108">WithException</span><span class="sxs-lookup"><span data-stu-id="00094-108">WithException</span></span>

```
Write-Error -Exception <Exception> [-Message <String>] [-Category <ErrorCategory>] [-ErrorId <String>]
 [-TargetObject <Object>] [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="00094-109">ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="00094-109">ErrorRecord</span></span>

```
Write-Error -ErrorRecord <ErrorRecord> [-RecommendedAction <String>] [-CategoryActivity <String>]
 [-CategoryReason <String>] [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

## <span data-ttu-id="00094-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="00094-110">DESCRIPTION</span></span>

<span data-ttu-id="00094-111">De `Write-Error` cmdlet declareert een niet-afsluit fout.</span><span class="sxs-lookup"><span data-stu-id="00094-111">The `Write-Error` cmdlet declares a non-terminating error.</span></span> <span data-ttu-id="00094-112">Standaard worden fouten in de fout stroom naar het hostprogramma verzonden, samen met de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="00094-112">By default, errors are sent in the error stream to the host program to be displayed, along with output.</span></span>

<span data-ttu-id="00094-113">Als u een niet-afsluit fout wilt schrijven, voert u een teken reeks voor het fout bericht, een **ErrorRecord** -object of een **uitzonderings** object in.</span><span class="sxs-lookup"><span data-stu-id="00094-113">To write a non-terminating error, enter an error message string, an **ErrorRecord** object, or an **Exception** object.</span></span> <span data-ttu-id="00094-114">Gebruik de andere para meters van `Write-Error` om de fout record in te vullen.</span><span class="sxs-lookup"><span data-stu-id="00094-114">Use the other parameters of `Write-Error` to populate the error record.</span></span>

<span data-ttu-id="00094-115">Bij niet-afsluit fouten wordt een fout naar de fout stroom geschreven, maar de opdracht verwerking wordt niet gestopt.</span><span class="sxs-lookup"><span data-stu-id="00094-115">Non-terminating errors write an error to the error stream, but they do not stop command processing.</span></span>
<span data-ttu-id="00094-116">Als een niet-afsluit fout wordt gedeclareerd voor één item in een verzameling invoer items, blijft de opdracht door gaan met het verwerken van de andere items in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="00094-116">If a non-terminating error is declared on one item in a collection of input items, the command continues to process the other items in the collection.</span></span>

<span data-ttu-id="00094-117">Als u een afsluit fout wilt declareren, gebruikt u het `Throw` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="00094-117">To declare a terminating error, use the `Throw` keyword.</span></span>
<span data-ttu-id="00094-118">Zie [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="00094-118">For more information, see [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md).</span></span>

## <span data-ttu-id="00094-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="00094-119">EXAMPLES</span></span>

### <span data-ttu-id="00094-120">Voor beeld 1: een fout voor RegistryKey-object schrijven</span><span class="sxs-lookup"><span data-stu-id="00094-120">Example 1: Write an error for RegistryKey object</span></span>

```powershell
Get-ChildItem | ForEach-Object {
    if ($_.GetType().ToString() -eq "Microsoft.Win32.RegistryKey")
    {
        Write-Error "Invalid object" -ErrorId B1 -TargetObject $_
    }
    else
    {
        $_
    }
}
```

<span data-ttu-id="00094-121">Met deze opdracht wordt een niet-afsluit fout gedeclareerd wanneer de `Get-ChildItem` cmdlet een `Microsoft.Win32.RegistryKey` object retourneert, zoals de objecten in de `HKLM:` of de `HKCU:` stations van de Power shell-register provider.</span><span class="sxs-lookup"><span data-stu-id="00094-121">This command declares a non-terminating error when the `Get-ChildItem` cmdlet returns a `Microsoft.Win32.RegistryKey` object, such as the objects in the `HKLM:` or `HKCU:` drives of the PowerShell Registry provider.</span></span>

### <span data-ttu-id="00094-122">Voor beeld 2: een fout bericht naar de console schrijven</span><span class="sxs-lookup"><span data-stu-id="00094-122">Example 2: Write an error message to the console</span></span>

```powershell
Write-Error "Access denied."
```

<span data-ttu-id="00094-123">Met deze opdracht wordt een niet-afsluit fout gedeclareerd en wordt de fout ' toegang geweigerd ' geschreven.</span><span class="sxs-lookup"><span data-stu-id="00094-123">This command declares a non-terminating error and writes an "Access denied" error.</span></span> <span data-ttu-id="00094-124">De opdracht gebruikt de para meter **Message** om het bericht op te geven, maar laat de optionele **bericht** parameter naam achterwege.</span><span class="sxs-lookup"><span data-stu-id="00094-124">The command uses the **Message** parameter to specify the message, but omits the optional **Message** parameter name.</span></span>

### <span data-ttu-id="00094-125">Voor beeld 3: een fout naar de console schrijven en de categorie opgeven</span><span class="sxs-lookup"><span data-stu-id="00094-125">Example 3: Write an error to the console and specify the category</span></span>

```powershell
Write-Error -Message "Error: Too many input values." -Category InvalidArgument
```

<span data-ttu-id="00094-126">Met deze opdracht wordt een niet-afsluit fout gedeclareerd en wordt een fout categorie opgegeven.</span><span class="sxs-lookup"><span data-stu-id="00094-126">This command declares a non-terminating error and specifies an error category.</span></span>

### <span data-ttu-id="00094-127">Voor beeld 4: een fout schrijven met behulp van een uitzonderings object</span><span class="sxs-lookup"><span data-stu-id="00094-127">Example 4: Write an error using an Exception object</span></span>

```powershell
$E = [System.Exception]@{Source="Get-ParameterNames.ps1";HelpLink="https://go.microsoft.com/fwlink/?LinkID=113425"}
Write-Error -Exception $E -Message "Files not found. The $Files location does not contain any XML files."
```

<span data-ttu-id="00094-128">Met deze opdracht wordt een **uitzonderings** object gebruikt om een niet-afsluit fout te declareren.</span><span class="sxs-lookup"><span data-stu-id="00094-128">This command uses an **Exception** object to declare a non-terminating error.</span></span>

<span data-ttu-id="00094-129">De eerste opdracht maakt gebruik van een hash-tabel om het object **System. Exception** te maken.</span><span class="sxs-lookup"><span data-stu-id="00094-129">The first command uses a hash table to create the **System.Exception** object.</span></span> <span data-ttu-id="00094-130">Hiermee wordt het uitzonderings object in de `$E` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="00094-130">It saves the exception object in the `$E` variable.</span></span> <span data-ttu-id="00094-131">U kunt een hash-tabel gebruiken om een object van een type te maken dat een null-constructor heeft.</span><span class="sxs-lookup"><span data-stu-id="00094-131">You can use a hash table to create any object of a type that has a null constructor.</span></span>

<span data-ttu-id="00094-132">De tweede opdracht gebruikt de `Write-Error` cmdlet om een niet-afsluit fout te declareren.</span><span class="sxs-lookup"><span data-stu-id="00094-132">The second command uses the `Write-Error` cmdlet to declare a non-terminating error.</span></span> <span data-ttu-id="00094-133">De waarde van de **uitzonderings** parameter is het **uitzonderings** object in de `$E` variabele.</span><span class="sxs-lookup"><span data-stu-id="00094-133">The value of the **Exception** parameter is the **Exception** object in the `$E` variable.</span></span>

## <span data-ttu-id="00094-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="00094-134">PARAMETERS</span></span>

### <span data-ttu-id="00094-135">-Categorie</span><span class="sxs-lookup"><span data-stu-id="00094-135">-Category</span></span>

<span data-ttu-id="00094-136">Hiermee geeft u de categorie van de fout op.</span><span class="sxs-lookup"><span data-stu-id="00094-136">Specifies the category of the error.</span></span> <span data-ttu-id="00094-137">De standaard waarde is **NotSpecified**.</span><span class="sxs-lookup"><span data-stu-id="00094-137">The default value is **NotSpecified**.</span></span> <span data-ttu-id="00094-138">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="00094-138">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="00094-139">NotSpecified</span><span class="sxs-lookup"><span data-stu-id="00094-139">NotSpecified</span></span>
- <span data-ttu-id="00094-140">Openstaande fout</span><span class="sxs-lookup"><span data-stu-id="00094-140">OpenError</span></span>
- <span data-ttu-id="00094-141">CloseError</span><span class="sxs-lookup"><span data-stu-id="00094-141">CloseError</span></span>
- <span data-ttu-id="00094-142">DeviceError</span><span class="sxs-lookup"><span data-stu-id="00094-142">DeviceError</span></span>
- <span data-ttu-id="00094-143">DeadlockDetected</span><span class="sxs-lookup"><span data-stu-id="00094-143">DeadlockDetected</span></span>
- <span data-ttu-id="00094-144">InvalidArgument</span><span class="sxs-lookup"><span data-stu-id="00094-144">InvalidArgument</span></span>
- <span data-ttu-id="00094-145">InvalidData</span><span class="sxs-lookup"><span data-stu-id="00094-145">InvalidData</span></span>
- <span data-ttu-id="00094-146">InvalidOperation</span><span class="sxs-lookup"><span data-stu-id="00094-146">InvalidOperation</span></span>
- <span data-ttu-id="00094-147">InvalidResult</span><span class="sxs-lookup"><span data-stu-id="00094-147">InvalidResult</span></span>
- <span data-ttu-id="00094-148">InvalidType</span><span class="sxs-lookup"><span data-stu-id="00094-148">InvalidType</span></span>
- <span data-ttu-id="00094-149">MetadataError</span><span class="sxs-lookup"><span data-stu-id="00094-149">MetadataError</span></span>
- <span data-ttu-id="00094-150">Niet geïmplementeerd</span><span class="sxs-lookup"><span data-stu-id="00094-150">NotImplemented</span></span>
- <span data-ttu-id="00094-151">NotInstalled</span><span class="sxs-lookup"><span data-stu-id="00094-151">NotInstalled</span></span>
- <span data-ttu-id="00094-152">ObjectNotFound</span><span class="sxs-lookup"><span data-stu-id="00094-152">ObjectNotFound</span></span>
- <span data-ttu-id="00094-153">OperationStopped</span><span class="sxs-lookup"><span data-stu-id="00094-153">OperationStopped</span></span>
- <span data-ttu-id="00094-154">OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="00094-154">OperationTimeout</span></span>
- <span data-ttu-id="00094-155">SyntaxError</span><span class="sxs-lookup"><span data-stu-id="00094-155">SyntaxError</span></span>
- <span data-ttu-id="00094-156">ParserError</span><span class="sxs-lookup"><span data-stu-id="00094-156">ParserError</span></span>
- <span data-ttu-id="00094-157">PermissionDenied</span><span class="sxs-lookup"><span data-stu-id="00094-157">PermissionDenied</span></span>
- <span data-ttu-id="00094-158">ResourceBusy</span><span class="sxs-lookup"><span data-stu-id="00094-158">ResourceBusy</span></span>
- <span data-ttu-id="00094-159">ResourceExists</span><span class="sxs-lookup"><span data-stu-id="00094-159">ResourceExists</span></span>
- <span data-ttu-id="00094-160">ResourceUnavailable</span><span class="sxs-lookup"><span data-stu-id="00094-160">ResourceUnavailable</span></span>
- <span data-ttu-id="00094-161">ReadError</span><span class="sxs-lookup"><span data-stu-id="00094-161">ReadError</span></span>
- <span data-ttu-id="00094-162">WriteError</span><span class="sxs-lookup"><span data-stu-id="00094-162">WriteError</span></span>
- <span data-ttu-id="00094-163">FromStdErr</span><span class="sxs-lookup"><span data-stu-id="00094-163">FromStdErr</span></span>
- <span data-ttu-id="00094-164">SecurityError</span><span class="sxs-lookup"><span data-stu-id="00094-164">SecurityError</span></span>
- <span data-ttu-id="00094-165">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="00094-165">ProtocolError</span></span>
- <span data-ttu-id="00094-166">ConnectionError</span><span class="sxs-lookup"><span data-stu-id="00094-166">ConnectionError</span></span>
- <span data-ttu-id="00094-167">AuthenticationError</span><span class="sxs-lookup"><span data-stu-id="00094-167">AuthenticationError</span></span>
- <span data-ttu-id="00094-168">LimitsExceeded</span><span class="sxs-lookup"><span data-stu-id="00094-168">LimitsExceeded</span></span>
- <span data-ttu-id="00094-169">QuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="00094-169">QuotaExceeded</span></span>
- <span data-ttu-id="00094-170">NotEnabled</span><span class="sxs-lookup"><span data-stu-id="00094-170">NotEnabled</span></span>

<span data-ttu-id="00094-171">Zie [ErrorCategory Enumeration](https://go.microsoft.com/fwlink/?LinkId=143600)(Engelstalig) voor meer informatie over de fout categorieën.</span><span class="sxs-lookup"><span data-stu-id="00094-171">For information about the error categories, see [ErrorCategory Enumeration](https://go.microsoft.com/fwlink/?LinkId=143600).</span></span>

```yaml
Type: System.Management.Automation.ErrorCategory
Parameter Sets: NoException, WithException
Aliases:
Accepted values: NotSpecified, OpenError, CloseError, DeviceError, DeadlockDetected, InvalidArgument, InvalidData, InvalidOperation, InvalidResult, InvalidType, MetadataError, NotImplemented, NotInstalled, ObjectNotFound, OperationStopped, OperationTimeout, SyntaxError, ParserError, PermissionDenied, ResourceBusy, ResourceExists, ResourceUnavailable, ReadError, WriteError, FromStdErr, SecurityError, ProtocolError, ConnectionError, AuthenticationError, LimitsExceeded, QuotaExceeded, NotEnabled

Required: False
Position: Named
Default value: NotSpecified
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00094-172">-CategoryActivity</span><span class="sxs-lookup"><span data-stu-id="00094-172">-CategoryActivity</span></span>

<span data-ttu-id="00094-173">Hiermee geeft u de actie op die de fout heeft veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="00094-173">Specifies the action that caused the error.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Activity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00094-174">-CategoryReason</span><span class="sxs-lookup"><span data-stu-id="00094-174">-CategoryReason</span></span>

<span data-ttu-id="00094-175">Hiermee geeft u op hoe of waarom de activiteit de fout heeft veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="00094-175">Specifies how or why the activity caused the error.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Reason

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00094-176">-CategoryTargetName</span><span class="sxs-lookup"><span data-stu-id="00094-176">-CategoryTargetName</span></span>

<span data-ttu-id="00094-177">Hiermee geeft u de naam op van het object dat werd verwerkt toen de fout optrad.</span><span class="sxs-lookup"><span data-stu-id="00094-177">Specifies the name of the object that was being processed when the error occurred.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00094-178">-CategoryTargetType</span><span class="sxs-lookup"><span data-stu-id="00094-178">-CategoryTargetType</span></span>

<span data-ttu-id="00094-179">Hiermee geeft u het type van het object op dat werd verwerkt toen de fout optrad.</span><span class="sxs-lookup"><span data-stu-id="00094-179">Specifies the type of the object that was being processed when the error occurred.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetType

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00094-180">-ErrorId</span><span class="sxs-lookup"><span data-stu-id="00094-180">-ErrorId</span></span>

<span data-ttu-id="00094-181">Hiermee geeft u een ID-teken reeks op om de fout te identificeren.</span><span class="sxs-lookup"><span data-stu-id="00094-181">Specifies an ID string to identify the error.</span></span> <span data-ttu-id="00094-182">De teken reeks moet uniek zijn voor de fout.</span><span class="sxs-lookup"><span data-stu-id="00094-182">The string should be unique to the error.</span></span>

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00094-183">-ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="00094-183">-ErrorRecord</span></span>

<span data-ttu-id="00094-184">Hiermee geeft u een fout record object op dat de fout vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="00094-184">Specifies an error record object that represents the error.</span></span> <span data-ttu-id="00094-185">Gebruik de eigenschappen van het object om de fout te beschrijven.</span><span class="sxs-lookup"><span data-stu-id="00094-185">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="00094-186">Als u een fout record object wilt maken, gebruikt u de `New-Object` cmdlet of haalt u een fout record object op uit de matrix in de `$Error` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="00094-186">To create an error record object, use the `New-Object` cmdlet or get an error record object from the array in the `$Error` automatic variable.</span></span>

```yaml
Type: System.Management.Automation.ErrorRecord
Parameter Sets: ErrorRecord
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00094-187">-Uitzonde ring</span><span class="sxs-lookup"><span data-stu-id="00094-187">-Exception</span></span>

<span data-ttu-id="00094-188">Hiermee geeft u een uitzonderings object op dat de fout vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="00094-188">Specifies an exception object that represents the error.</span></span> <span data-ttu-id="00094-189">Gebruik de eigenschappen van het object om de fout te beschrijven.</span><span class="sxs-lookup"><span data-stu-id="00094-189">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="00094-190">Als u een uitzonderings object wilt maken, gebruikt u een hash-tabel of gebruikt u de `New-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="00094-190">To create an exception object, use a hash table or use the `New-Object` cmdlet.</span></span>

```yaml
Type: System.Exception
Parameter Sets: WithException
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00094-191">-Bericht</span><span class="sxs-lookup"><span data-stu-id="00094-191">-Message</span></span>

<span data-ttu-id="00094-192">Hiermee geeft u de bericht tekst van de fout op.</span><span class="sxs-lookup"><span data-stu-id="00094-192">Specifies the message text of the error.</span></span> <span data-ttu-id="00094-193">Als de tekst spaties of speciale tekens bevat, plaatst u deze tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="00094-193">If the text includes spaces or special characters, enclose it in quotation marks.</span></span> <span data-ttu-id="00094-194">U kunt ook een bericht teken reeks door sluizen naar `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="00094-194">You can also pipe a message string to `Write-Error`.</span></span>

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases: Msg

Required: True (NoException), False (WithException)
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="00094-195">-RecommendedAction</span><span class="sxs-lookup"><span data-stu-id="00094-195">-RecommendedAction</span></span>

<span data-ttu-id="00094-196">Hiermee geeft u de actie op die de gebruiker moet ondernemen om de fout op te lossen of te voor komen.</span><span class="sxs-lookup"><span data-stu-id="00094-196">Specifies the action that the user should take to resolve or prevent the error.</span></span>

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

### <span data-ttu-id="00094-197">-Target object</span><span class="sxs-lookup"><span data-stu-id="00094-197">-TargetObject</span></span>

<span data-ttu-id="00094-198">Hiermee geeft u het object op dat werd verwerkt toen de fout optrad.</span><span class="sxs-lookup"><span data-stu-id="00094-198">Specifies the object that was being processed when the error occurred.</span></span> <span data-ttu-id="00094-199">Voer het object in, een variabele die het object bevat of een opdracht die het object ophaalt.</span><span class="sxs-lookup"><span data-stu-id="00094-199">Enter the object, a variable that contains the object, or a command that gets the object.</span></span>

```yaml
Type: System.Object
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00094-200">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="00094-200">CommonParameters</span></span>

<span data-ttu-id="00094-201">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="00094-201">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="00094-202">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="00094-202">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="00094-203">INVOER</span><span class="sxs-lookup"><span data-stu-id="00094-203">INPUTS</span></span>

### <span data-ttu-id="00094-204">System. String</span><span class="sxs-lookup"><span data-stu-id="00094-204">System.String</span></span>

<span data-ttu-id="00094-205">U kunt een teken reeks die een fout bericht bevat door sluizen naar `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="00094-205">You can pipe a string that contains an error message to `Write-Error`.</span></span>

## <span data-ttu-id="00094-206">UITVOER</span><span class="sxs-lookup"><span data-stu-id="00094-206">OUTPUTS</span></span>

### <span data-ttu-id="00094-207">Fout object</span><span class="sxs-lookup"><span data-stu-id="00094-207">Error object</span></span>

<span data-ttu-id="00094-208">`Write-Error` schrijft alleen naar de fout stroom.</span><span class="sxs-lookup"><span data-stu-id="00094-208">`Write-Error` writes only to the error stream.</span></span> <span data-ttu-id="00094-209">Er worden geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="00094-209">It does not return any objects.</span></span>

## <span data-ttu-id="00094-210">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="00094-210">NOTES</span></span>

<span data-ttu-id="00094-211">`Write-Error` de waarde van de automatische variabele wordt niet gewijzigd `$?` , dus er wordt geen afsluitende fout weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="00094-211">`Write-Error` does not change the value of the `$?` automatic variable, therefore it does not signal a terminating error condition.</span></span> <span data-ttu-id="00094-212">Als u een afsluitende fout wilt verzenden, gebruikt u de methode [$PSCmdlet. WriteError ()](/dotnet/api/system.management.automation.cmdlet.writeerror) .</span><span class="sxs-lookup"><span data-stu-id="00094-212">To signal a terminating error, use the [$PSCmdlet.WriteError()](/dotnet/api/system.management.automation.cmdlet.writeerror) method.</span></span>

## <span data-ttu-id="00094-213">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="00094-213">RELATED LINKS</span></span>

[<span data-ttu-id="00094-214">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="00094-214">about_Automatic_Variables</span></span>](../microsoft.powershell.core/about/about_automatic_variables.md)

[<span data-ttu-id="00094-215">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="00094-215">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="00094-216">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="00094-216">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="00094-217">Schrijf fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="00094-217">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="00094-218">Write-host</span><span class="sxs-lookup"><span data-stu-id="00094-218">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="00094-219">Write-output</span><span class="sxs-lookup"><span data-stu-id="00094-219">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="00094-220">Schrijf voortgang</span><span class="sxs-lookup"><span data-stu-id="00094-220">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="00094-221">Write-verbose</span><span class="sxs-lookup"><span data-stu-id="00094-221">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="00094-222">Waarschuwing voor schrijven</span><span class="sxs-lookup"><span data-stu-id="00094-222">Write-Warning</span></span>](Write-Warning.md)
