---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-error?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Error
ms.openlocfilehash: d0ee66e1002e4f1d58f63e198bcb7f03b1c8d3a8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705689"
---
# <span data-ttu-id="5a317-102">Write-Error</span><span class="sxs-lookup"><span data-stu-id="5a317-102">Write-Error</span></span>

## <span data-ttu-id="5a317-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="5a317-103">SYNOPSIS</span></span>
<span data-ttu-id="5a317-104">Schrijft een object naar de fout stroom.</span><span class="sxs-lookup"><span data-stu-id="5a317-104">Writes an object to the error stream.</span></span>

## <span data-ttu-id="5a317-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="5a317-105">SYNTAX</span></span>

### <span data-ttu-id="5a317-106">Except (standaard)</span><span class="sxs-lookup"><span data-stu-id="5a317-106">NoException (Default)</span></span>

```
Write-Error [-Message] <String> [-Category <ErrorCategory>] [-ErrorId <String>] [-TargetObject <Object>]
 [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="5a317-107">WithException</span><span class="sxs-lookup"><span data-stu-id="5a317-107">WithException</span></span>

```
Write-Error -Exception <Exception> [[-Message] <String>] [-Category <ErrorCategory>] [-ErrorId <String>]
 [-TargetObject <Object>] [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="5a317-108">ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="5a317-108">ErrorRecord</span></span>

```
Write-Error -ErrorRecord <ErrorRecord> [-RecommendedAction <String>] [-CategoryActivity <String>]
 [-CategoryReason <String>] [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

## <span data-ttu-id="5a317-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5a317-109">DESCRIPTION</span></span>

<span data-ttu-id="5a317-110">De `Write-Error` cmdlet declareert een niet-afsluit fout.</span><span class="sxs-lookup"><span data-stu-id="5a317-110">The `Write-Error` cmdlet declares a non-terminating error.</span></span> <span data-ttu-id="5a317-111">Standaard worden fouten in de fout stroom naar het hostprogramma verzonden, samen met de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="5a317-111">By default, errors are sent in the error stream to the host program to be displayed, along with output.</span></span>

<span data-ttu-id="5a317-112">Als u een niet-afsluit fout wilt schrijven, voert u een teken reeks voor het fout bericht, een **ErrorRecord** -object of een **uitzonderings** object in.</span><span class="sxs-lookup"><span data-stu-id="5a317-112">To write a non-terminating error, enter an error message string, an **ErrorRecord** object, or an **Exception** object.</span></span> <span data-ttu-id="5a317-113">Gebruik de andere para meters van `Write-Error` om de fout record in te vullen.</span><span class="sxs-lookup"><span data-stu-id="5a317-113">Use the other parameters of `Write-Error` to populate the error record.</span></span>

<span data-ttu-id="5a317-114">Bij niet-afsluit fouten wordt een fout naar de fout stroom geschreven, maar de opdracht verwerking wordt niet gestopt.</span><span class="sxs-lookup"><span data-stu-id="5a317-114">Non-terminating errors write an error to the error stream, but they do not stop command processing.</span></span>
<span data-ttu-id="5a317-115">Als een niet-afsluit fout wordt gedeclareerd voor één item in een verzameling invoer items, blijft de opdracht door gaan met het verwerken van de andere items in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="5a317-115">If a non-terminating error is declared on one item in a collection of input items, the command continues to process the other items in the collection.</span></span>

<span data-ttu-id="5a317-116">Als u een afsluit fout wilt declareren, gebruikt u het `Throw` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="5a317-116">To declare a terminating error, use the `Throw` keyword.</span></span>
<span data-ttu-id="5a317-117">Zie [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5a317-117">For more information, see [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md).</span></span>

## <span data-ttu-id="5a317-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="5a317-118">EXAMPLES</span></span>

### <span data-ttu-id="5a317-119">Voor beeld 1: een fout voor RegistryKey-object schrijven</span><span class="sxs-lookup"><span data-stu-id="5a317-119">Example 1: Write an error for RegistryKey object</span></span>

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

<span data-ttu-id="5a317-120">Met deze opdracht wordt een niet-afsluit fout gedeclareerd wanneer de `Get-ChildItem` cmdlet een `Microsoft.Win32.RegistryKey` object retourneert, zoals de objecten in de `HKLM:` of de `HKCU:` stations van de Power shell-register provider.</span><span class="sxs-lookup"><span data-stu-id="5a317-120">This command declares a non-terminating error when the `Get-ChildItem` cmdlet returns a `Microsoft.Win32.RegistryKey` object, such as the objects in the `HKLM:` or `HKCU:` drives of the PowerShell Registry provider.</span></span>

### <span data-ttu-id="5a317-121">Voor beeld 2: een fout bericht naar de console schrijven</span><span class="sxs-lookup"><span data-stu-id="5a317-121">Example 2: Write an error message to the console</span></span>

```powershell
Write-Error "Access denied."
```

<span data-ttu-id="5a317-122">Met deze opdracht wordt een niet-afsluit fout gedeclareerd en wordt de fout ' toegang geweigerd ' geschreven.</span><span class="sxs-lookup"><span data-stu-id="5a317-122">This command declares a non-terminating error and writes an "Access denied" error.</span></span> <span data-ttu-id="5a317-123">De opdracht gebruikt de para meter **Message** om het bericht op te geven, maar laat de optionele **bericht** parameter naam achterwege.</span><span class="sxs-lookup"><span data-stu-id="5a317-123">The command uses the **Message** parameter to specify the message, but omits the optional **Message** parameter name.</span></span>

### <span data-ttu-id="5a317-124">Voor beeld 3: een fout naar de console schrijven en de categorie opgeven</span><span class="sxs-lookup"><span data-stu-id="5a317-124">Example 3: Write an error to the console and specify the category</span></span>

```powershell
Write-Error -Message "Error: Too many input values." -Category InvalidArgument
```

<span data-ttu-id="5a317-125">Met deze opdracht wordt een niet-afsluit fout gedeclareerd en wordt een fout categorie opgegeven.</span><span class="sxs-lookup"><span data-stu-id="5a317-125">This command declares a non-terminating error and specifies an error category.</span></span>

### <span data-ttu-id="5a317-126">Voor beeld 4: een fout schrijven met behulp van een uitzonderings object</span><span class="sxs-lookup"><span data-stu-id="5a317-126">Example 4: Write an error using an Exception object</span></span>

```powershell
$E = [System.Exception]@{Source="Get-ParameterNames.ps1";HelpLink="https://go.microsoft.com/fwlink/?LinkID=113425"}
Write-Error -Exception $E -Message "Files not found. The $Files location does not contain any XML files."
```

<span data-ttu-id="5a317-127">Met deze opdracht wordt een **uitzonderings** object gebruikt om een niet-afsluit fout te declareren.</span><span class="sxs-lookup"><span data-stu-id="5a317-127">This command uses an **Exception** object to declare a non-terminating error.</span></span>

<span data-ttu-id="5a317-128">De eerste opdracht maakt gebruik van een hash-tabel om het object **System. Exception** te maken.</span><span class="sxs-lookup"><span data-stu-id="5a317-128">The first command uses a hash table to create the **System.Exception** object.</span></span> <span data-ttu-id="5a317-129">Hiermee wordt het uitzonderings object in de `$E` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="5a317-129">It saves the exception object in the `$E` variable.</span></span> <span data-ttu-id="5a317-130">U kunt een hash-tabel gebruiken om een object van een type te maken dat een null-constructor heeft.</span><span class="sxs-lookup"><span data-stu-id="5a317-130">You can use a hash table to create any object of a type that has a null constructor.</span></span>

<span data-ttu-id="5a317-131">De tweede opdracht gebruikt de `Write-Error` cmdlet om een niet-afsluit fout te declareren.</span><span class="sxs-lookup"><span data-stu-id="5a317-131">The second command uses the `Write-Error` cmdlet to declare a non-terminating error.</span></span> <span data-ttu-id="5a317-132">De waarde van de **uitzonderings** parameter is het **uitzonderings** object in de `$E` variabele.</span><span class="sxs-lookup"><span data-stu-id="5a317-132">The value of the **Exception** parameter is the **Exception** object in the `$E` variable.</span></span>

## <span data-ttu-id="5a317-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5a317-133">PARAMETERS</span></span>

### <span data-ttu-id="5a317-134">-Categorie</span><span class="sxs-lookup"><span data-stu-id="5a317-134">-Category</span></span>

<span data-ttu-id="5a317-135">Hiermee geeft u de categorie van de fout op.</span><span class="sxs-lookup"><span data-stu-id="5a317-135">Specifies the category of the error.</span></span> <span data-ttu-id="5a317-136">De standaard waarde is **NotSpecified**.</span><span class="sxs-lookup"><span data-stu-id="5a317-136">The default value is **NotSpecified**.</span></span> <span data-ttu-id="5a317-137">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="5a317-137">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5a317-138">NotSpecified</span><span class="sxs-lookup"><span data-stu-id="5a317-138">NotSpecified</span></span>
- <span data-ttu-id="5a317-139">Openstaande fout</span><span class="sxs-lookup"><span data-stu-id="5a317-139">OpenError</span></span>
- <span data-ttu-id="5a317-140">CloseError</span><span class="sxs-lookup"><span data-stu-id="5a317-140">CloseError</span></span>
- <span data-ttu-id="5a317-141">DeviceError</span><span class="sxs-lookup"><span data-stu-id="5a317-141">DeviceError</span></span>
- <span data-ttu-id="5a317-142">DeadlockDetected</span><span class="sxs-lookup"><span data-stu-id="5a317-142">DeadlockDetected</span></span>
- <span data-ttu-id="5a317-143">InvalidArgument</span><span class="sxs-lookup"><span data-stu-id="5a317-143">InvalidArgument</span></span>
- <span data-ttu-id="5a317-144">InvalidData</span><span class="sxs-lookup"><span data-stu-id="5a317-144">InvalidData</span></span>
- <span data-ttu-id="5a317-145">InvalidOperation</span><span class="sxs-lookup"><span data-stu-id="5a317-145">InvalidOperation</span></span>
- <span data-ttu-id="5a317-146">InvalidResult</span><span class="sxs-lookup"><span data-stu-id="5a317-146">InvalidResult</span></span>
- <span data-ttu-id="5a317-147">InvalidType</span><span class="sxs-lookup"><span data-stu-id="5a317-147">InvalidType</span></span>
- <span data-ttu-id="5a317-148">MetadataError</span><span class="sxs-lookup"><span data-stu-id="5a317-148">MetadataError</span></span>
- <span data-ttu-id="5a317-149">Niet geïmplementeerd</span><span class="sxs-lookup"><span data-stu-id="5a317-149">NotImplemented</span></span>
- <span data-ttu-id="5a317-150">NotInstalled</span><span class="sxs-lookup"><span data-stu-id="5a317-150">NotInstalled</span></span>
- <span data-ttu-id="5a317-151">ObjectNotFound</span><span class="sxs-lookup"><span data-stu-id="5a317-151">ObjectNotFound</span></span>
- <span data-ttu-id="5a317-152">OperationStopped</span><span class="sxs-lookup"><span data-stu-id="5a317-152">OperationStopped</span></span>
- <span data-ttu-id="5a317-153">OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="5a317-153">OperationTimeout</span></span>
- <span data-ttu-id="5a317-154">SyntaxError</span><span class="sxs-lookup"><span data-stu-id="5a317-154">SyntaxError</span></span>
- <span data-ttu-id="5a317-155">ParserError</span><span class="sxs-lookup"><span data-stu-id="5a317-155">ParserError</span></span>
- <span data-ttu-id="5a317-156">PermissionDenied</span><span class="sxs-lookup"><span data-stu-id="5a317-156">PermissionDenied</span></span>
- <span data-ttu-id="5a317-157">ResourceBusy</span><span class="sxs-lookup"><span data-stu-id="5a317-157">ResourceBusy</span></span>
- <span data-ttu-id="5a317-158">ResourceExists</span><span class="sxs-lookup"><span data-stu-id="5a317-158">ResourceExists</span></span>
- <span data-ttu-id="5a317-159">ResourceUnavailable</span><span class="sxs-lookup"><span data-stu-id="5a317-159">ResourceUnavailable</span></span>
- <span data-ttu-id="5a317-160">ReadError</span><span class="sxs-lookup"><span data-stu-id="5a317-160">ReadError</span></span>
- <span data-ttu-id="5a317-161">WriteError</span><span class="sxs-lookup"><span data-stu-id="5a317-161">WriteError</span></span>
- <span data-ttu-id="5a317-162">FromStdErr</span><span class="sxs-lookup"><span data-stu-id="5a317-162">FromStdErr</span></span>
- <span data-ttu-id="5a317-163">SecurityError</span><span class="sxs-lookup"><span data-stu-id="5a317-163">SecurityError</span></span>
- <span data-ttu-id="5a317-164">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="5a317-164">ProtocolError</span></span>
- <span data-ttu-id="5a317-165">ConnectionError</span><span class="sxs-lookup"><span data-stu-id="5a317-165">ConnectionError</span></span>
- <span data-ttu-id="5a317-166">AuthenticationError</span><span class="sxs-lookup"><span data-stu-id="5a317-166">AuthenticationError</span></span>
- <span data-ttu-id="5a317-167">LimitsExceeded</span><span class="sxs-lookup"><span data-stu-id="5a317-167">LimitsExceeded</span></span>
- <span data-ttu-id="5a317-168">QuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="5a317-168">QuotaExceeded</span></span>
- <span data-ttu-id="5a317-169">NotEnabled</span><span class="sxs-lookup"><span data-stu-id="5a317-169">NotEnabled</span></span>

<span data-ttu-id="5a317-170">Zie [ErrorCategory Enumeration](https://go.microsoft.com/fwlink/?LinkId=143600)(Engelstalig) voor meer informatie over de fout categorieën.</span><span class="sxs-lookup"><span data-stu-id="5a317-170">For information about the error categories, see [ErrorCategory Enumeration](https://go.microsoft.com/fwlink/?LinkId=143600).</span></span>

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

### <span data-ttu-id="5a317-171">-CategoryActivity</span><span class="sxs-lookup"><span data-stu-id="5a317-171">-CategoryActivity</span></span>

<span data-ttu-id="5a317-172">Hiermee geeft u de actie op die de fout heeft veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="5a317-172">Specifies the action that caused the error.</span></span>

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

### <span data-ttu-id="5a317-173">-CategoryReason</span><span class="sxs-lookup"><span data-stu-id="5a317-173">-CategoryReason</span></span>

<span data-ttu-id="5a317-174">Hiermee geeft u op hoe of waarom de activiteit de fout heeft veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="5a317-174">Specifies how or why the activity caused the error.</span></span>

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

### <span data-ttu-id="5a317-175">-CategoryTargetName</span><span class="sxs-lookup"><span data-stu-id="5a317-175">-CategoryTargetName</span></span>

<span data-ttu-id="5a317-176">Hiermee geeft u de naam op van het object dat werd verwerkt toen de fout optrad.</span><span class="sxs-lookup"><span data-stu-id="5a317-176">Specifies the name of the object that was being processed when the error occurred.</span></span>

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

### <span data-ttu-id="5a317-177">-CategoryTargetType</span><span class="sxs-lookup"><span data-stu-id="5a317-177">-CategoryTargetType</span></span>

<span data-ttu-id="5a317-178">Hiermee geeft u het type van het object op dat werd verwerkt toen de fout optrad.</span><span class="sxs-lookup"><span data-stu-id="5a317-178">Specifies the type of the object that was being processed when the error occurred.</span></span>

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

### <span data-ttu-id="5a317-179">-ErrorId</span><span class="sxs-lookup"><span data-stu-id="5a317-179">-ErrorId</span></span>

<span data-ttu-id="5a317-180">Hiermee geeft u een ID-teken reeks op om de fout te identificeren.</span><span class="sxs-lookup"><span data-stu-id="5a317-180">Specifies an ID string to identify the error.</span></span> <span data-ttu-id="5a317-181">De teken reeks moet uniek zijn voor de fout.</span><span class="sxs-lookup"><span data-stu-id="5a317-181">The string should be unique to the error.</span></span>

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

### <span data-ttu-id="5a317-182">-ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="5a317-182">-ErrorRecord</span></span>

<span data-ttu-id="5a317-183">Hiermee geeft u een fout record object op dat de fout vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="5a317-183">Specifies an error record object that represents the error.</span></span> <span data-ttu-id="5a317-184">Gebruik de eigenschappen van het object om de fout te beschrijven.</span><span class="sxs-lookup"><span data-stu-id="5a317-184">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="5a317-185">Als u een fout record object wilt maken, gebruikt u de `New-Object` cmdlet of haalt u een fout record object op uit de matrix in de `$Error` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="5a317-185">To create an error record object, use the `New-Object` cmdlet or get an error record object from the array in the `$Error` automatic variable.</span></span>

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

### <span data-ttu-id="5a317-186">-Uitzonde ring</span><span class="sxs-lookup"><span data-stu-id="5a317-186">-Exception</span></span>

<span data-ttu-id="5a317-187">Hiermee geeft u een uitzonderings object op dat de fout vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="5a317-187">Specifies an exception object that represents the error.</span></span> <span data-ttu-id="5a317-188">Gebruik de eigenschappen van het object om de fout te beschrijven.</span><span class="sxs-lookup"><span data-stu-id="5a317-188">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="5a317-189">Als u een uitzonderings object wilt maken, gebruikt u een hash-tabel of gebruikt u de `New-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5a317-189">To create an exception object, use a hash table or use the `New-Object` cmdlet.</span></span>

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

### <span data-ttu-id="5a317-190">-Bericht</span><span class="sxs-lookup"><span data-stu-id="5a317-190">-Message</span></span>

<span data-ttu-id="5a317-191">Hiermee geeft u de bericht tekst van de fout op.</span><span class="sxs-lookup"><span data-stu-id="5a317-191">Specifies the message text of the error.</span></span> <span data-ttu-id="5a317-192">Als de tekst spaties of speciale tekens bevat, plaatst u deze tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="5a317-192">If the text includes spaces or special characters, enclose it in quotation marks.</span></span> <span data-ttu-id="5a317-193">U kunt ook een bericht teken reeks door sluizen naar `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="5a317-193">You can also pipe a message string to `Write-Error`.</span></span>

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

### <span data-ttu-id="5a317-194">-RecommendedAction</span><span class="sxs-lookup"><span data-stu-id="5a317-194">-RecommendedAction</span></span>

<span data-ttu-id="5a317-195">Hiermee geeft u de actie op die de gebruiker moet ondernemen om de fout op te lossen of te voor komen.</span><span class="sxs-lookup"><span data-stu-id="5a317-195">Specifies the action that the user should take to resolve or prevent the error.</span></span>

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

### <span data-ttu-id="5a317-196">-Target object</span><span class="sxs-lookup"><span data-stu-id="5a317-196">-TargetObject</span></span>

<span data-ttu-id="5a317-197">Hiermee geeft u het object op dat werd verwerkt toen de fout optrad.</span><span class="sxs-lookup"><span data-stu-id="5a317-197">Specifies the object that was being processed when the error occurred.</span></span> <span data-ttu-id="5a317-198">Voer het object in, een variabele die het object bevat of een opdracht die het object ophaalt.</span><span class="sxs-lookup"><span data-stu-id="5a317-198">Enter the object, a variable that contains the object, or a command that gets the object.</span></span>

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

### <span data-ttu-id="5a317-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5a317-199">CommonParameters</span></span>

<span data-ttu-id="5a317-200">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5a317-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5a317-201">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5a317-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5a317-202">INVOER</span><span class="sxs-lookup"><span data-stu-id="5a317-202">INPUTS</span></span>

### <span data-ttu-id="5a317-203">System. String</span><span class="sxs-lookup"><span data-stu-id="5a317-203">System.String</span></span>

<span data-ttu-id="5a317-204">U kunt een teken reeks die een fout bericht bevat door sluizen naar `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="5a317-204">You can pipe a string that contains an error message to `Write-Error`.</span></span>

## <span data-ttu-id="5a317-205">UITVOER</span><span class="sxs-lookup"><span data-stu-id="5a317-205">OUTPUTS</span></span>

### <span data-ttu-id="5a317-206">Fout object</span><span class="sxs-lookup"><span data-stu-id="5a317-206">Error object</span></span>

<span data-ttu-id="5a317-207">`Write-Error` schrijft alleen naar de fout stroom.</span><span class="sxs-lookup"><span data-stu-id="5a317-207">`Write-Error` writes only to the error stream.</span></span> <span data-ttu-id="5a317-208">Er worden geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="5a317-208">It does not return any objects.</span></span>

## <span data-ttu-id="5a317-209">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="5a317-209">NOTES</span></span>

<span data-ttu-id="5a317-210">`Write-Error` de waarde van de automatische variabele wordt niet gewijzigd `$?` , dus er wordt geen afsluitende fout weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5a317-210">`Write-Error` does not change the value of the `$?` automatic variable, therefore it does not signal a terminating error condition.</span></span> <span data-ttu-id="5a317-211">Als u een afsluitende fout wilt verzenden, gebruikt u de methode [$PSCmdlet. WriteError ()](/dotnet/api/system.management.automation.cmdlet.writeerror) .</span><span class="sxs-lookup"><span data-stu-id="5a317-211">To signal a terminating error, use the [$PSCmdlet.WriteError()](/dotnet/api/system.management.automation.cmdlet.writeerror) method.</span></span>

## <span data-ttu-id="5a317-212">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="5a317-212">RELATED LINKS</span></span>

[<span data-ttu-id="5a317-213">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="5a317-213">about_Automatic_Variables</span></span>](../microsoft.powershell.core/about/about_automatic_variables.md)

[<span data-ttu-id="5a317-214">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="5a317-214">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="5a317-215">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="5a317-215">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="5a317-216">Schrijf fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="5a317-216">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="5a317-217">Write-host</span><span class="sxs-lookup"><span data-stu-id="5a317-217">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="5a317-218">Write-output</span><span class="sxs-lookup"><span data-stu-id="5a317-218">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="5a317-219">Schrijf voortgang</span><span class="sxs-lookup"><span data-stu-id="5a317-219">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="5a317-220">Write-verbose</span><span class="sxs-lookup"><span data-stu-id="5a317-220">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="5a317-221">Waarschuwing voor schrijven</span><span class="sxs-lookup"><span data-stu-id="5a317-221">Write-Warning</span></span>](Write-Warning.md)
