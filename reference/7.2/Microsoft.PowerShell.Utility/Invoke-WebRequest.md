---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/05/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: 49fa39807a522c86b94f950ba63c8ff54a112953
ms.sourcegitcommit: 241071803915ab7d544576b5652ac23349a86369
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/07/2021
ms.locfileid: "107027223"
---
# <span data-ttu-id="3c7fd-102">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="3c7fd-102">Invoke-WebRequest</span></span>

## <span data-ttu-id="3c7fd-103">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="3c7fd-103">Synopsis</span></span>
<span data-ttu-id="3c7fd-104">Hiermee wordt inhoud opgehaald van een webpagina op internet.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-104">Gets content from a web page on the internet.</span></span>

## <span data-ttu-id="3c7fd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3c7fd-105">Syntax</span></span>

### <span data-ttu-id="3c7fd-106">StandardMethod (standaard)</span><span class="sxs-lookup"><span data-stu-id="3c7fd-106">StandardMethod (Default)</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Method <WebRequestMethod>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="3c7fd-107">StandardMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="3c7fd-107">StandardMethodNoProxy</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Method <WebRequestMethod>] -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck]
 [-PreserveAuthorizationOnRedirect] [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="3c7fd-108">CustomMethod</span><span class="sxs-lookup"><span data-stu-id="3c7fd-108">CustomMethod</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -CustomMethod <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="3c7fd-109">CustomMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="3c7fd-109">CustomMethodNoProxy</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -CustomMethod <String> -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck]
 [-PreserveAuthorizationOnRedirect] [-SkipHeaderValidation] [<CommonParameters>]
```

## <span data-ttu-id="3c7fd-110">Description</span><span class="sxs-lookup"><span data-stu-id="3c7fd-110">Description</span></span>

<span data-ttu-id="3c7fd-111">De `Invoke-WebRequest` cmdlet verzendt HTTP-en HTTPS-aanvragen naar een webpagina of webservice.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-111">The `Invoke-WebRequest` cmdlet sends HTTP and HTTPS requests to a web page or web service.</span></span> <span data-ttu-id="3c7fd-112">Hiermee wordt het antwoord geparseerd en worden verzamelingen van koppelingen, afbeeldingen en andere belang rijke HTML-elementen geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-112">It parses the response and returns collections of links, images, and other significant HTML elements.</span></span>

<span data-ttu-id="3c7fd-113">Deze cmdlet is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-113">This cmdlet was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="3c7fd-114">Vanaf Power shell 7,0 `Invoke-WebRequest` ondersteunt proxy configuratie die is gedefinieerd door omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-114">Beginning in PowerShell 7.0, `Invoke-WebRequest` supports proxy configuration defined by environment variables.</span></span> <span data-ttu-id="3c7fd-115">Zie de sectie [opmerkingen](#notes) van dit artikel.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-115">See the [Notes](#notes) section of this article.</span></span>

## <span data-ttu-id="3c7fd-116">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="3c7fd-116">Examples</span></span>

### <span data-ttu-id="3c7fd-117">Voor beeld 1: een webaanvraag verzenden</span><span class="sxs-lookup"><span data-stu-id="3c7fd-117">Example 1: Send a web request</span></span>

<span data-ttu-id="3c7fd-118">In dit voor beeld wordt de `Invoke-WebRequest` cmdlet gebruikt voor het verzenden van een webaanvraag naar de Bing.com-site.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-118">This example uses the `Invoke-WebRequest` cmdlet to send a web request to the Bing.com site.</span></span>

```powershell
$Response = Invoke-WebRequest -URI https://www.bing.com/search?q=how+many+feet+in+a+mile
$Response.InputFields | Where-Object {
    $_.name -like "* Value*"
} | Select-Object Name, Value
```

```Output
name       value
----       -----
From Value 1
To Value   5280
```

<span data-ttu-id="3c7fd-119">Met de eerste opdracht wordt de aanvraag uitgegeven en wordt het antwoord in de `$Response` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-119">The first command issues the request and saves the response in the `$Response` variable.</span></span>

<span data-ttu-id="3c7fd-120">Met de tweede opdracht wordt een wille keurige **InputField** opgehaald waarbij de eigenschap **name** like is `"* Value"` .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-120">The second command gets any **InputField** where the **Name** property is like `"* Value"`.</span></span> <span data-ttu-id="3c7fd-121">De gefilterde resultaten worden gepiped om `Select-Object` de **naam** en **waarde** -eigenschappen te selecteren.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-121">The filtered results are piped to `Select-Object` to select the **Name** and **Value** properties.</span></span>

### <span data-ttu-id="3c7fd-122">Voor beeld 2: een stateful webservice gebruiken</span><span class="sxs-lookup"><span data-stu-id="3c7fd-122">Example 2: Use a stateful web service</span></span>

<span data-ttu-id="3c7fd-123">In dit voor beeld ziet u hoe u de `Invoke-WebRequest` cmdlet gebruikt met een stateful webservice.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-123">This example shows how to use the `Invoke-WebRequest` cmdlet with a stateful web service.</span></span>

```powershell
$Body = @{
    User = 'jdoe'
    password = 'P@S$w0rd!'
}
$LoginResponse = Invoke-WebRequest 'https://www.contoso.com/login/' -SessionVariable 'Session' -Body $Body -Method 'POST'

$Session

$ProfileResponse = Invoke-WebRequest 'https://www.contoso.com/profile/' -WebSession $Session

$ProfileResponse
```

<span data-ttu-id="3c7fd-124">De eerste aanroep om `Invoke-WebRequest` een aanmeldings aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-124">The first call to `Invoke-WebRequest` sends a sign-in request.</span></span> <span data-ttu-id="3c7fd-125">Met de opdracht wordt de waarde ' session ' opgegeven voor de waarde van de para meter **-SessionVariable** en wordt het resultaat opgeslagen in de `$LoginResponse` variabele.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-125">The command specifies a value of "Session" for the value of the **-SessionVariable** parameter, and saves the result in the `$LoginResponse` variable.</span></span> <span data-ttu-id="3c7fd-126">Wanneer de opdracht is voltooid, `$LoginResponse` bevat de variabele een `BasicHtmlWebResponseObject` en de `$Session` variabele bevat een- `WebRequestSession` object.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-126">When the command completes, the `$LoginResponse` variable contains an `BasicHtmlWebResponseObject` and the `$Session` variable contains a `WebRequestSession` object.</span></span> <span data-ttu-id="3c7fd-127">Hiermee wordt de gebruiker geregistreerd bij de-site.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-127">This logs the user into the site.</span></span>

<span data-ttu-id="3c7fd-128">De aanroep naar `$Session` zelf toont het `WebRequestSession` object in de variabele.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-128">The call to `$Session` by itself shows the `WebRequestSession` object in the variable.</span></span>

<span data-ttu-id="3c7fd-129">De tweede aanroep om `Invoke-WebRequest` het profiel van de gebruiker op te halen waarvoor de gebruiker moet zijn aangemeld bij de site.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-129">The second call to `Invoke-WebRequest` fetches the user's profile which requires that the user be logged into the site.</span></span> <span data-ttu-id="3c7fd-130">De sessie gegevens die zijn opgeslagen in de `$Session` variabele worden gebruikt om sessie cookies te bieden aan de site die tijdens de aanmelding is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-130">The session data stored in the `$Session` variable is used to provide session cookies to the site created during the login.</span></span> <span data-ttu-id="3c7fd-131">Het resultaat wordt opgeslagen in de `$ProfileResponse` variabele.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-131">The result is saved in the `$ProfileResponse` variable.</span></span>

<span data-ttu-id="3c7fd-132">Op de aanroep `$ProfileResponse` zelf wordt de `BasicHtmlWebResponseObject` in de variabele weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-132">The call to `$ProfileResponse` by itself shows the `BasicHtmlWebResponseObject` in the variable.</span></span>

### <span data-ttu-id="3c7fd-133">Voor beeld 3: koppelingen van een webpagina ophalen</span><span class="sxs-lookup"><span data-stu-id="3c7fd-133">Example 3: Get links from a web page</span></span>

<span data-ttu-id="3c7fd-134">In dit voor beeld worden de koppelingen op een webpagina opgehaald.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-134">This example gets the links in a web page.</span></span> <span data-ttu-id="3c7fd-135">Hiermee wordt de- `Invoke-WebRequest` cmdlet gebruikt om de inhoud van de webpagina op te halen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-135">It uses the `Invoke-WebRequest` cmdlet to get the web page content.</span></span> <span data-ttu-id="3c7fd-136">Vervolgens wordt de eigenschap **links** van de `BasicHtmlWebResponseObject` `Invoke-WebRequest` geretourneerde en de eigenschap **href** van elke koppeling gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-136">Then it uses the **Links** property of the `BasicHtmlWebResponseObject` that `Invoke-WebRequest` returns, and the **Href** property of each link.</span></span>

```powershell
(Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs").Links.Href
```

### <span data-ttu-id="3c7fd-137">Voor beeld 4: schrijft de antwoord inhoud naar een bestand met behulp van de code ring die op de aangevraagde pagina is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-137">Example 4: Writes the response content to a file using the encoding defined in the requested page.</span></span>

<span data-ttu-id="3c7fd-138">In dit voor beeld wordt de `Invoke-WebRequest` cmdlet gebruikt om de webpagina-inhoud van een Power shell-documentatie pagina op te halen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-138">This example uses the `Invoke-WebRequest` cmdlet to retrieve the web page content of a PowerShell documentation page.</span></span>

```powershell
$Response = Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs"
$Stream = [System.IO.StreamWriter]::new('.\docspage.html', $false, $Response.Encoding)
try {
    $Stream.Write($Response.Content)
}
finally {
    $Stream.Dispose()
}
```

<span data-ttu-id="3c7fd-139">De eerste opdracht haalt de pagina op en slaat het antwoord object op in de `$Response` variabele.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-139">The first command retrieves the page and saves the response object in the `$Response` variable.</span></span>

<span data-ttu-id="3c7fd-140">Met de tweede opdracht maakt `StreamWriter` u een om de antwoord inhoud naar een bestand te schrijven.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-140">The second command creates a `StreamWriter` to use to write the response content to a file.</span></span> <span data-ttu-id="3c7fd-141">De eigenschap **Encoding** van het Response-object wordt gebruikt om de code ring voor het bestand in te stellen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-141">The **Encoding** property of the response object is used to set the encoding for the file.</span></span>

<span data-ttu-id="3c7fd-142">Met de laatste opdrachten wordt de eigenschap **Content** geschreven naar het bestand en vervolgens verwijderd `StreamWriter` .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-142">The final few commands write the **Content** property to the file then disposes the `StreamWriter`.</span></span>

<span data-ttu-id="3c7fd-143">Houd er rekening mee dat de eigenschap **Encoding** null is als de webaanvraag geen tekst inhoud retourneert.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-143">Note that the **Encoding** property is null if the web request doesn't return text content.</span></span>

### <span data-ttu-id="3c7fd-144">Voor beeld 5: een meerdelige/formulier-gegevens bestand verzenden</span><span class="sxs-lookup"><span data-stu-id="3c7fd-144">Example 5: Submit a multipart/form-data file</span></span>

<span data-ttu-id="3c7fd-145">In dit voor beeld wordt de cmdlet gebruikt om `Invoke-WebRequest` een bestand te uploaden als een `multipart/form-data` verzen ding.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-145">This example uses the `Invoke-WebRequest` cmdlet upload a file as a `multipart/form-data` submission.</span></span> <span data-ttu-id="3c7fd-146">Het bestand `c:\document.txt` wordt verzonden als het formulier veld `document` met de `Content-Type` van `text/plain` .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-146">The file `c:\document.txt` is submitted as the form field `document` with the `Content-Type` of `text/plain`.</span></span>

```powershell
$FilePath = 'c:\document.txt'
$FieldName = 'document'
$ContentType = 'text/plain'

$FileStream = [System.IO.FileStream]::new($filePath, [System.IO.FileMode]::Open)
$FileHeader = [System.Net.Http.Headers.ContentDispositionHeaderValue]::new('form-data')
$FileHeader.Name = $FieldName
$FileHeader.FileName = Split-Path -leaf $FilePath
$FileContent = [System.Net.Http.StreamContent]::new($FileStream)
$FileContent.Headers.ContentDisposition = $FileHeader
$FileContent.Headers.ContentType = [System.Net.Http.Headers.MediaTypeHeaderValue]::Parse($ContentType)

$MultipartContent = [System.Net.Http.MultipartFormDataContent]::new()
$MultipartContent.Add($FileContent)

$Response = Invoke-WebRequest -Body $MultipartContent -Method 'POST' -Uri 'https://api.contoso.com/upload'
```

### <span data-ttu-id="3c7fd-147">Voor beeld 6: vereenvoudigd meerdelige/Form-Data-verzen ding</span><span class="sxs-lookup"><span data-stu-id="3c7fd-147">Example 6: Simplified Multipart/Form-Data Submission</span></span>

<span data-ttu-id="3c7fd-148">Voor sommige Api's zijn `multipart/form-data` inzendingen vereist om bestanden en gemengde inhoud te uploaden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-148">Some APIs require `multipart/form-data` submissions to upload files and mixed content.</span></span> <span data-ttu-id="3c7fd-149">In dit voor beeld ziet u hoe u een gebruikers profiel bijwerkt.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-149">This example demonstrates updating a user profile.</span></span>

```powershell
$Uri = 'https://api.contoso.com/v2/profile'
$Form = @{
    firstName  = 'John'
    lastName   = 'Doe'
    email      = 'john.doe@contoso.com'
    avatar     = Get-Item -Path 'c:\Pictures\jdoe.png'
    birthday   = '1980-10-15'
    hobbies    = 'Hiking','Fishing','Jogging'
}
$Result = Invoke-WebRequest -Uri $Uri -Method Post -Form $Form
```

<span data-ttu-id="3c7fd-150">Voor het profiel formulier zijn de volgende velden vereist: `firstName` ,, `lastName` ,, `email` `avatar` `birthday` en `hobbies` .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-150">The profile form requires these fields: `firstName`, `lastName`, `email`, `avatar`, `birthday`, and `hobbies`.</span></span> <span data-ttu-id="3c7fd-151">De API verwacht een installatie kopie voor het gebruikers profiel pic dat in het veld moet worden opgegeven `avatar` .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-151">The API is expecting an image for the user profile pic to be supplied in the `avatar` field.</span></span> <span data-ttu-id="3c7fd-152">De API accepteert ook meerdere `hobbies` vermeldingen die in hetzelfde formulier moeten worden ingediend.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-152">The API also accepts multiple `hobbies` entries to be submitted in the same form.</span></span>

<span data-ttu-id="3c7fd-153">Wanneer u de `$Form` hashtabel maakt, worden de sleutel namen gebruikt als formulier veld namen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-153">When creating the `$Form` HashTable, the key names are used as form field names.</span></span> <span data-ttu-id="3c7fd-154">Standaard worden de waarden van de hashtabel geconverteerd naar teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-154">By default, the values of the HashTable are converted to strings.</span></span> <span data-ttu-id="3c7fd-155">Als er een **System. io. file info** -waarde aanwezig is, wordt de bestands inhoud verzonden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-155">If a **System.IO.FileInfo** value is present, the file contents are submitted.</span></span> <span data-ttu-id="3c7fd-156">Als er een verzameling zoals matrices of lijsten aanwezig is, wordt het formulier veld meerdere keren ingediend.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-156">If a collection such as arrays or lists are present, the form field is submitted multiple times.</span></span>

<span data-ttu-id="3c7fd-157">Door `Get-Item` op de `avatar` sleutel te gebruiken, `FileInfo` wordt het object ingesteld als de waarde.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-157">By using `Get-Item` on the `avatar` key, the `FileInfo` object is set as the value.</span></span> <span data-ttu-id="3c7fd-158">Het resultaat is dat de afbeeldings gegevens voor `jdoe.png` worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-158">The result is that the image data for `jdoe.png` is submitted.</span></span>

<span data-ttu-id="3c7fd-159">Door een lijst aan de sleutel toe te voegen `hobbies` , `hobbies` wordt het veld voor elk lijst item één keer weer gegeven in de-verzen ding.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-159">By supplying a list to the `hobbies` key, the `hobbies` field is present in the submissions once for each list item.</span></span>

### <span data-ttu-id="3c7fd-160">Voor beeld 7: berichten over niet-geslaagde artikelen van Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="3c7fd-160">Example 7: Catch non success messages from Invoke-WebRequest</span></span>

<span data-ttu-id="3c7fd-161">Wanneer er `Invoke-WebRequest` een niet-geslaagd http-bericht wordt aangetroffen (404, 500, etc.), wordt er geen uitvoer geretourneerd en wordt er een afsluit fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-161">When `Invoke-WebRequest` encounters a non-success HTTP message (404, 500, etc.), it returns no output and throws a terminating error.</span></span> <span data-ttu-id="3c7fd-162">Als u de fout wilt opvangen en de **status** code wilt weer geven, kunt u de uitvoering in een `try/catch` blok insluiten.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-162">To catch the error and view the **StatusCode** you can enclose execution in a `try/catch` block.</span></span>

```powershell
try
{
    $Response = Invoke-WebRequest -Uri "www.microsoft.com/unkownhost"
    # This will only execute if the Invoke-WebRequest is successful.
    $StatusCode = $Response.StatusCode
}
catch
{
    $StatusCode = $_.Exception.Response.StatusCode.value__
}
$StatusCode
```

```Output
404
```

<span data-ttu-id="3c7fd-163">De afsluit fout wordt geblokkeerd door het `catch` blok, waardoor de **status** code wordt opgehaald uit het **uitzonderings** object.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-163">The terminating error is caught by the `catch` block, which retrieves the **StatusCode** from the **Exception** object.</span></span>

## <span data-ttu-id="3c7fd-164">Parameters</span><span class="sxs-lookup"><span data-stu-id="3c7fd-164">Parameters</span></span>

### <span data-ttu-id="3c7fd-165">-AllowUnencryptedAuthentication</span><span class="sxs-lookup"><span data-stu-id="3c7fd-165">-AllowUnencryptedAuthentication</span></span>

<span data-ttu-id="3c7fd-166">Hiermee staat u het verzenden van referenties en geheimen over niet-versleutelde verbindingen toe.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-166">Allows sending of credentials and secrets over unencrypted connections.</span></span> <span data-ttu-id="3c7fd-167">Standaard wordt **referentie** verstrekt of een **authenticatie** optie met een **URI** die niet begint met `https://` resulteert in een fout en de aanvraag wordt afgebroken om onbedoeld geheimen te communiceren in tekst zonder opmaak over niet-versleutelde verbindingen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-167">By default, supplying **Credential** or any **Authentication** option with a **Uri** that does not begin with `https://` results in an error and the request is aborted to prevent unintentionally communicating secrets in plain text over unencrypted connections.</span></span> <span data-ttu-id="3c7fd-168">U kunt dit gedrag voor eigen risico negeren door de para meter **AllowUnencryptedAuthentication** op te geven.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-168">To override this behavior at your own risk, supply the **AllowUnencryptedAuthentication** parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="3c7fd-169">Het gebruik van deze para meter is niet beveiligd en wordt niet aanbevolen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-169">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="3c7fd-170">Het is alleen beschikbaar voor compatibiliteit met oudere systemen die geen versleutelde verbindingen kunnen bieden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-170">It is provided only for compatibility with legacy systems that cannot provide encrypted connections.</span></span> <span data-ttu-id="3c7fd-171">Gebruiken op eigen risico.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-171">Use at your own risk.</span></span>

<span data-ttu-id="3c7fd-172">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-172">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-173">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="3c7fd-173">-Authentication</span></span>

<span data-ttu-id="3c7fd-174">Hiermee geeft u het expliciete verificatie type op dat moet worden gebruikt voor de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-174">Specifies the explicit authentication type to use for the request.</span></span> <span data-ttu-id="3c7fd-175">De standaardwaarde is **None**.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-175">The default is **None**.</span></span>
<span data-ttu-id="3c7fd-176">**Authenticatie** kan niet worden gebruikt met **UseDefaultCredentials**.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-176">**Authentication** cannot be used with **UseDefaultCredentials**.</span></span>

<span data-ttu-id="3c7fd-177">Beschik bare verificatie opties:</span><span class="sxs-lookup"><span data-stu-id="3c7fd-177">Available Authentication Options:</span></span>

- <span data-ttu-id="3c7fd-178">`None`: Dit is de standaard optie wanneer **authenticatie** niet is opgegeven. Er wordt geen expliciete authenticatie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-178">`None`: This is the default option when **Authentication** isn't supplied; no explicit authentication is used.</span></span>
- <span data-ttu-id="3c7fd-179">`Basic`: Vereist **referentie**.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-179">`Basic`: Requires **Credential**.</span></span> <span data-ttu-id="3c7fd-180">De referenties worden verzonden in een RFC 7617-basis verificatie header in de indeling van `base64(user:password)` .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-180">The credentials are sent in an RFC 7617 Basic Authentication header in the format of `base64(user:password)`.</span></span>
- <span data-ttu-id="3c7fd-181">`Bearer`: **Token** vereist.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-181">`Bearer`: Requires **Token**.</span></span> <span data-ttu-id="3c7fd-182">Verzendt een RFC 6750- `Authorization: Bearer` header met het opgegeven token.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-182">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="3c7fd-183">Dit is een alias voor **OAuth**</span><span class="sxs-lookup"><span data-stu-id="3c7fd-183">This is an alias for **OAuth**</span></span>
- <span data-ttu-id="3c7fd-184">`OAuth`: **Token** vereist.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-184">`OAuth`: Requires **Token**.</span></span> <span data-ttu-id="3c7fd-185">Verzendt een RFC 6750- `Authorization: Bearer` header met het opgegeven token.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-185">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="3c7fd-186">Dit is een alias voor **Bearer**</span><span class="sxs-lookup"><span data-stu-id="3c7fd-186">This is an alias for **Bearer**</span></span>

<span data-ttu-id="3c7fd-187">Het opgeven van een **verificatie** heeft `Authorization` voor rang op alle headers die worden geleverd aan **headers** of die zijn opgenomen in **websessie**.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-187">Supplying **Authentication** overrides any `Authorization` headers supplied to **Headers** or included in **WebSession**.</span></span>

<span data-ttu-id="3c7fd-188">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-188">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WebAuthenticationType
Parameter Sets: (All)
Aliases:
Accepted values: None, Basic, Bearer, OAuth

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-189">-Hoofd tekst</span><span class="sxs-lookup"><span data-stu-id="3c7fd-189">-Body</span></span>

<span data-ttu-id="3c7fd-190">Hiermee geeft u de hoofd tekst van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-190">Specifies the body of the request.</span></span> <span data-ttu-id="3c7fd-191">De hoofd tekst is de inhoud van de aanvraag die de headers volgt.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-191">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="3c7fd-192">U kunt ook de waarde van een hoofd tekst sluist naar `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-192">You can also pipe a body value to `Invoke-WebRequest`.</span></span>

<span data-ttu-id="3c7fd-193">De para meter **Body** kan worden gebruikt om een lijst met query parameters op te geven of de inhoud van het antwoord op te geven.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-193">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="3c7fd-194">Wanneer de invoer een GET-aanvraag is en de hoofd tekst een `IDictionary` (meestal een hash-tabel) is, wordt de hoofd tekst als query parameters aan de URI toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-194">When the input is a GET request and the body is an `IDictionary` (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="3c7fd-195">Voor andere aanvraag typen (zoals POST) wordt de hoofd tekst ingesteld als de waarde van de hoofd tekst van de aanvraag in de standaard `name=value` indeling.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-195">For other request types (such as POST), the body is set as the value of the request body in the standard `name=value` format.</span></span>

<span data-ttu-id="3c7fd-196">De para meter **Body** kan ook een `System.Net.Http.MultipartFormDataContent` object accepteren.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-196">The **Body** parameter may also accept a `System.Net.Http.MultipartFormDataContent` object.</span></span> <span data-ttu-id="3c7fd-197">Dit vergemakkelijkt `multipart/form-data` aanvragen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-197">This facilitates `multipart/form-data` requests.</span></span> <span data-ttu-id="3c7fd-198">Wanneer er een **MultipartFormDataContent** -object wordt opgegeven voor de **hoofd tekst**, worden alle inhoud die aan de para meter **Content type**, **headers** of **websession** is gekoppeld, overschreven door de inhouds headers van het **MultipartFormDataContent** -object.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-198">When a **MultipartFormDataContent** object is supplied for **Body**, any Content related headers supplied to the **ContentType**, **Headers**, or **WebSession** parameters is overridden by the Content headers of the **MultipartFormDataContent** object.</span></span> <span data-ttu-id="3c7fd-199">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-199">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-200">-Certificaat</span><span class="sxs-lookup"><span data-stu-id="3c7fd-200">-Certificate</span></span>

<span data-ttu-id="3c7fd-201">Hiermee geeft u het client certificaat op dat wordt gebruikt voor een beveiligde webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-201">Specifies the client certificate that's used for a secure web request.</span></span> <span data-ttu-id="3c7fd-202">Voer een variabele in die een certificaat of een opdracht of expressie bevat waarmee het certificaat wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-202">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="3c7fd-203">Als u een certificaat wilt zoeken, gebruikt `Get-PfxCertificate` of gebruikt u de `Get-ChildItem` cmdlet in het certificaat `Cert:` station.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-203">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="3c7fd-204">Als het certificaat ongeldig is of niet voldoende autoriteit heeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-204">If the certificate isn't valid or doesn't have sufficient authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-205">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="3c7fd-205">-CertificateThumbprint</span></span>

<span data-ttu-id="3c7fd-206">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat gemachtigd is om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-206">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="3c7fd-207">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-207">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="3c7fd-208">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-208">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="3c7fd-209">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-209">They can be mapped only to local user accounts; they don't work with domain accounts.</span></span>

<span data-ttu-id="3c7fd-210">Gebruik de `Get-Item` `Get-ChildItem` opdracht of in het Power Shell-station om een certificaat vingerafdruk te verkrijgen `Cert:` .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-210">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

> [!NOTE]
> <span data-ttu-id="3c7fd-211">Deze functie wordt momenteel alleen ondersteund op Windows-besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-211">This feature is currently only supported on Windows OS platforms.</span></span>

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

### <span data-ttu-id="3c7fd-212">-Content type</span><span class="sxs-lookup"><span data-stu-id="3c7fd-212">-ContentType</span></span>

<span data-ttu-id="3c7fd-213">Hiermee geeft u het type inhoud van de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-213">Specifies the content type of the web request.</span></span>

<span data-ttu-id="3c7fd-214">Als deze para meter wordt wegge laten en de aanvraag methode is `Invoke-WebRequest` ingesteld op post, stelt het inhouds type in op `application/x-www-form-urlencoded` .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-214">If this parameter is omitted and the request method is POST, `Invoke-WebRequest` sets the content type to `application/x-www-form-urlencoded`.</span></span> <span data-ttu-id="3c7fd-215">Anders is het inhouds type niet opgegeven in de aanroep.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-215">Otherwise, the content type isn't specified in the call.</span></span>

<span data-ttu-id="3c7fd-216">**Content type** wordt overschreven wanneer een **MultipartFormDataContent** -object wordt opgegeven voor de **hoofd tekst**.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-216">**ContentType** is overridden when a **MultipartFormDataContent** object is supplied for **Body**.</span></span>

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

### <span data-ttu-id="3c7fd-217">-Credential</span><span class="sxs-lookup"><span data-stu-id="3c7fd-217">-Credential</span></span>

<span data-ttu-id="3c7fd-218">Hiermee geeft u een gebruikers account op dat gemachtigd is om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-218">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="3c7fd-219">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-219">The default is the current user.</span></span>

<span data-ttu-id="3c7fd-220">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**, of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-220">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="3c7fd-221">**Referentie** kan alleen worden gebruikt of in combi natie met bepaalde opties voor **verificatie** parameters.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-221">**Credential** can be used alone or in conjunction with certain **Authentication** parameter options.</span></span> <span data-ttu-id="3c7fd-222">Als u alleen gebruikt, worden er alleen referenties voor de externe server verstrekt als de externe server een aanvraag voor verificatie controle verzendt.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-222">When used alone, it only supplies credentials to the remote server if the remote server sends an authentication challenge request.</span></span> <span data-ttu-id="3c7fd-223">Wanneer u gebruikt met **verificatie** opties, worden de referenties expliciet verzonden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-223">When used with **Authentication** options, the credentials are explicitly sent.</span></span>

<span data-ttu-id="3c7fd-224">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="3c7fd-224">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="3c7fd-225">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-225">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-226">-CustomMethod</span><span class="sxs-lookup"><span data-stu-id="3c7fd-226">-CustomMethod</span></span>

<span data-ttu-id="3c7fd-227">Hiermee geeft u een aangepaste methode op die wordt gebruikt voor de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-227">Specifies a custom method used for the web request.</span></span> <span data-ttu-id="3c7fd-228">Dit kan worden gebruikt als de aanvraag methode die door het eind punt wordt vereist, geen beschik bare optie is voor de **methode**.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-228">This can be used if the Request Method required by the endpoint isn't an available option on the **Method**.</span></span> <span data-ttu-id="3c7fd-229">**Methode** en **CustomMethod** kunnen niet tegelijk worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-229">**Method** and **CustomMethod** can't be used together.</span></span>

<span data-ttu-id="3c7fd-230">In dit voor beeld wordt een `TEST` HTTP-aanvraag naar de API gemaakt:</span><span class="sxs-lookup"><span data-stu-id="3c7fd-230">This example makes a `TEST` HTTP request to the API:</span></span>

`Invoke-WebRequest -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

<span data-ttu-id="3c7fd-231">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-231">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.String
Parameter Sets: CustomMethod, CustomMethodNoProxy
Aliases: CM

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-232">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="3c7fd-232">-DisableKeepAlive</span></span>

<span data-ttu-id="3c7fd-233">Geeft aan dat de cmdlet de **keepalive** -waarde in de http-header instelt op **False**.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-233">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to **False**.</span></span> <span data-ttu-id="3c7fd-234">Standaard is **keepalive** ingesteld op **True**.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-234">By default, **KeepAlive** is **True**.</span></span> <span data-ttu-id="3c7fd-235">Met **keepalive** wordt een permanente verbinding met de server tot stand gebracht om volgende aanvragen te vergemakkelijken.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-235">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-236">-Vorm</span><span class="sxs-lookup"><span data-stu-id="3c7fd-236">-Form</span></span>

<span data-ttu-id="3c7fd-237">Converteert een woorden lijst naar een `multipart/form-data` inzending.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-237">Converts a dictionary to a `multipart/form-data` submission.</span></span> <span data-ttu-id="3c7fd-238">Het **formulier** kan niet worden gebruikt met een **hoofd tekst**.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-238">**Form** may not be used with **Body**.</span></span>
<span data-ttu-id="3c7fd-239">Als **Content type** wordt gebruikt, wordt dit genegeerd.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-239">If **ContentType** is used, it's ignored.</span></span>

<span data-ttu-id="3c7fd-240">De sleutels van de woorden lijst worden gebruikt als de namen van het formulier veld.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-240">The keys of the dictionary are used as the form field names.</span></span> <span data-ttu-id="3c7fd-241">Standaard worden formulier waarden geconverteerd naar teken reeks waarden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-241">By default, form values are converted to string values.</span></span>

<span data-ttu-id="3c7fd-242">Als de waarde een **System. io. file info** -object is, wordt de inhoud van het binaire bestand verzonden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-242">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="3c7fd-243">De naam van het bestand wordt verzonden als de eigenschap **filename** .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-243">The name of the file is submitted as the **filename** property.</span></span> <span data-ttu-id="3c7fd-244">Het MIME-type is ingesteld als `application/octet-stream` .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-244">The MIME type is set as `application/octet-stream`.</span></span> <span data-ttu-id="3c7fd-245">`Get-Item` kan worden gebruikt om het object **System. io. file info** te vereenvoudigen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-245">`Get-Item` can be used to simplify supplying the **System.IO.FileInfo** object.</span></span>

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

<span data-ttu-id="3c7fd-246">Als de waarde een verzamelings type is, zoals matrices of lijsten, worden het veld voor meerdere keren verzonden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-246">If the value is a collection type, such Arrays or Lists, the for field are submitted multiple times.</span></span>
<span data-ttu-id="3c7fd-247">De waarden van de lijst worden standaard als teken reeksen beschouwd.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-247">The values of the list are treated as strings by default.</span></span> <span data-ttu-id="3c7fd-248">Als de waarde een **System. io. file info** -object is, wordt de inhoud van het binaire bestand verzonden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-248">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="3c7fd-249">Geneste verzamelingen worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-249">Nested collections aren't supported.</span></span>

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

<span data-ttu-id="3c7fd-250">In het bovenstaande voor beeld `tags` wordt het veld drie keer in het formulier opgegeven, eenmaal voor elk van `Vacation` , `Italy` en `2017` .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-250">In the above example the `tags` field are supplied three times in the form, once for each of `Vacation`, `Italy`, and `2017`.</span></span> <span data-ttu-id="3c7fd-251">Het `pictures` veld wordt ook eenmaal ingediend voor elk bestand in de `2017-Italy` map.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-251">The `pictures` field is also submitted once for each file in the `2017-Italy` folder.</span></span> <span data-ttu-id="3c7fd-252">De binaire inhoud van de bestanden in die map wordt verzonden als de waarden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-252">The binary contents of the files in that folder are submitted as the values.</span></span>

<span data-ttu-id="3c7fd-253">Deze functie is toegevoegd aan Power shell 6.1.0.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-253">This feature was added in PowerShell 6.1.0.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-254">-Headers</span><span class="sxs-lookup"><span data-stu-id="3c7fd-254">-Headers</span></span>

<span data-ttu-id="3c7fd-255">Hiermee geeft u de kopteksten van de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-255">Specifies the headers of the web request.</span></span> <span data-ttu-id="3c7fd-256">Voer een hash-tabel of-woorden lijst in.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-256">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="3c7fd-257">Gebruik de **agent** -para meter om de agent headers in te stellen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-257">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="3c7fd-258">U kunt deze para meter niet gebruiken om **gebruikers agent-** of cookie headers op te geven.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-258">You can't use this parameter to specify **User-Agent** or cookie headers.</span></span>

<span data-ttu-id="3c7fd-259">Inhouds gerelateerde kopteksten, zoals `Content-Type` wordt overschreven wanneer een **MultipartFormDataContent** -object wordt opgegeven voor de **hoofd tekst**.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-259">Content related headers, such as `Content-Type` is overridden when a **MultipartFormDataContent** object is supplied for **Body**.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-260">-Inbestand</span><span class="sxs-lookup"><span data-stu-id="3c7fd-260">-InFile</span></span>

<span data-ttu-id="3c7fd-261">Hiermee wordt de inhoud van de webaanvraag opgehaald uit een bestand.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-261">Gets the content of the web request from a file.</span></span> <span data-ttu-id="3c7fd-262">Voer een pad en een bestands naam in.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-262">Enter a path and file name.</span></span> <span data-ttu-id="3c7fd-263">Als u het pad weglaat, de standaard instelling is de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-263">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="3c7fd-264">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="3c7fd-264">-MaximumRedirection</span></span>

<span data-ttu-id="3c7fd-265">Hiermee geeft u op hoe vaak Power shell een verbinding met een alternatieve URI (Uniform Resource Identifier) omleidt voordat de verbinding is mislukt.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-265">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="3c7fd-266">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-266">The default value is 5.</span></span> <span data-ttu-id="3c7fd-267">Een waarde van 0 (nul) voor komt dat alle omleidingen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-267">A value of 0 (zero) prevents all redirection.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-268">-MaximumRetryCount</span><span class="sxs-lookup"><span data-stu-id="3c7fd-268">-MaximumRetryCount</span></span>

<span data-ttu-id="3c7fd-269">Hiermee geeft u op hoe vaak Power shell een verbinding probeert te verbreken wanneer een fout code tussen 400 en 599, inclusief of 304 wordt ontvangen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-269">Specifies how many times PowerShell retries a connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="3c7fd-270">Zie ook de para meter **RetryIntervalSec** voor het opgeven van het aantal nieuwe pogingen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-270">Also see **RetryIntervalSec** parameter for specifying number of retries.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-271">-Methode</span><span class="sxs-lookup"><span data-stu-id="3c7fd-271">-Method</span></span>

<span data-ttu-id="3c7fd-272">Hiermee geeft u de methode op die voor de webaanvraag wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-272">Specifies the method used for the web request.</span></span> <span data-ttu-id="3c7fd-273">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="3c7fd-273">The acceptable values for this parameter are:</span></span>

- `Default`
- `Delete`
- `Get`
- `Head`
- `Merge`
- `Options`
- `Patch`
- `Post`
- `Put`
- `Trace`

<span data-ttu-id="3c7fd-274">De para meter **CustomMethod** kan worden gebruikt voor aanvraag methoden die hierboven niet worden vermeld.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-274">The **CustomMethod** parameter can be used for Request Methods not listed above.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestMethod
Parameter Sets: StandardMethod, StandardMethodNoProxy
Aliases:
Accepted values: Default, Get, Head, Post, Put, Delete, Trace, Options, Merge, Patch

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-275">-De proxy</span><span class="sxs-lookup"><span data-stu-id="3c7fd-275">-NoProxy</span></span>

<span data-ttu-id="3c7fd-276">Geeft aan dat de cmdlet geen proxy moet gebruiken om de bestemming te bereiken.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-276">Indicates that the cmdlet shouldn't use a proxy to reach the destination.</span></span> <span data-ttu-id="3c7fd-277">Wanneer u de in de omgeving geconfigureerde proxy wilt overs Laan, gebruikt u deze schakel optie.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-277">When you need to bypass the proxy configured in the environment, use this switch.</span></span> <span data-ttu-id="3c7fd-278">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-278">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StandardMethodNoProxy, CustomMethodNoProxy
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-279">-Outfile</span><span class="sxs-lookup"><span data-stu-id="3c7fd-279">-OutFile</span></span>

<span data-ttu-id="3c7fd-280">Hiermee geeft u het uitvoer bestand op waarvoor deze cmdlet de antwoord tekst opslaat.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-280">Specifies the output file for which this cmdlet saves the response body.</span></span> <span data-ttu-id="3c7fd-281">Voer een pad en een bestands naam in.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-281">Enter a path and file name.</span></span>
<span data-ttu-id="3c7fd-282">Als u het pad weglaat, de standaard instelling is de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-282">If you omit the path, the default is the current location.</span></span> <span data-ttu-id="3c7fd-283">De naam wordt beschouwd als een letterlijk pad.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-283">The name is treated as a literal path.</span></span>
<span data-ttu-id="3c7fd-284">Namen die vier Kante haakjes () bevatten, `[]` moeten tussen enkele aanhalings tekens () worden geplaatst `'` .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-284">Names that contain brackets (`[]`) must be enclosed in single quotes (`'`).</span></span>

<span data-ttu-id="3c7fd-285">`Invoke-WebRequest`De resultaten worden standaard naar de pijp lijn geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-285">By default, `Invoke-WebRequest` returns the results to the pipeline.</span></span> <span data-ttu-id="3c7fd-286">Als u de resultaten naar een bestand en naar de pijp lijn wilt verzenden, gebruikt u de para meter **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-286">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="3c7fd-287">-PassThru</span><span class="sxs-lookup"><span data-stu-id="3c7fd-287">-PassThru</span></span>

<span data-ttu-id="3c7fd-288">Geeft aan dat de cmdlet de resultaten retourneert, naast het schrijven naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-288">Indicates that the cmdlet returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="3c7fd-289">Deze para meter is alleen geldig wanneer de **outfile** -para meter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-289">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-290">-PreserveAuthorizationOnRedirect</span><span class="sxs-lookup"><span data-stu-id="3c7fd-290">-PreserveAuthorizationOnRedirect</span></span>

<span data-ttu-id="3c7fd-291">Hiermee wordt aangegeven dat de cmdlet de header moet behouden `Authorization` , indien aanwezig, over de omleidingen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-291">Indicates the cmdlet should preserve the `Authorization` header, when present, across redirections.</span></span>

<span data-ttu-id="3c7fd-292">De-cmdlet verwijdert standaard de `Authorization` header voordat deze wordt omgeleid.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-292">By default, the cmdlet strips the `Authorization` header before redirecting.</span></span> <span data-ttu-id="3c7fd-293">Als u deze para meter opgeeft, wordt deze logica uitgeschakeld voor gevallen waarin de header moet worden verzonden naar de omleidings locatie.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-293">Specifying this parameter disables this logic for cases where the header needs to be sent to the redirection location.</span></span>

<span data-ttu-id="3c7fd-294">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-294">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-295">-Proxy</span><span class="sxs-lookup"><span data-stu-id="3c7fd-295">-Proxy</span></span>

<span data-ttu-id="3c7fd-296">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-296">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>
<span data-ttu-id="3c7fd-297">Voer de URI van een netwerk proxy server in.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-297">Enter the URI of a network proxy server.</span></span>

```yaml
Type: System.Uri
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-298">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="3c7fd-298">-ProxyCredential</span></span>

<span data-ttu-id="3c7fd-299">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-299">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="3c7fd-300">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-300">The default is the current user.</span></span>

<span data-ttu-id="3c7fd-301">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**, **User@Domain.Com** of voer een `PSCredential` object in, bijvoorbeeld het type dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-301">Type a user name, such as **User01** or **Domain01\User01**, **User@Domain.Com**, or enter a `PSCredential` object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="3c7fd-302">Deze para meter is alleen geldig wanneer de **proxy** parameter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-302">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="3c7fd-303">U kunt de para meters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-303">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-304">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="3c7fd-304">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="3c7fd-305">Geeft aan dat de cmdlet de referenties van de huidige gebruiker gebruikt om toegang te krijgen tot de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-305">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="3c7fd-306">Deze para meter is alleen geldig wanneer de **proxy** parameter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-306">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="3c7fd-307">U kunt de para meters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-307">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-308">-Hervatten</span><span class="sxs-lookup"><span data-stu-id="3c7fd-308">-Resume</span></span>

<span data-ttu-id="3c7fd-309">Hiermee wordt een beste poging gedaan om het downloaden van een gedeeltelijk bestand te hervatten.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-309">Performs a best effort attempt to resume downloading a partial file.</span></span> <span data-ttu-id="3c7fd-310">Voor **hervatten** is **outfile** vereist.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-310">**Resume** requires **OutFile**.</span></span>

<span data-ttu-id="3c7fd-311">**Resume** werkt alleen op de grootte van het lokale bestand en het externe bestand en voert geen andere validatie uit dat het lokale bestand en het externe bestand hetzelfde zijn.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-311">**Resume** only operates on the size of the local file and remote file and performs no other validation that the local file and the remote file are the same.</span></span>

<span data-ttu-id="3c7fd-312">Als de lokale bestands grootte kleiner is dan de grootte van het externe bestand, probeert de cmdlet het downloaden van het bestand te hervatten en de resterende bytes toe te voegen aan het einde van het bestand.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-312">If the local file size is smaller than the remote file size, then the cmdlet attempts to resume downloading the file and append the remaining bytes to the end of the file.</span></span>

<span data-ttu-id="3c7fd-313">Als de grootte van het lokale bestand hetzelfde is als de grootte van het externe bestand, wordt er geen actie ondernomen en wordt ervan uitgegaan dat de down load al is voltooid.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-313">If the local file size is the same as the remote file size, then no action is taken and the cmdlet assumes the download already complete.</span></span>

<span data-ttu-id="3c7fd-314">Als de grootte van het lokale bestand groter is dan de grootte van het externe bestand, wordt het lokale bestand overschreven en wordt het hele externe bestand opnieuw gedownload.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-314">If the local file size is larger than the remote file size, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="3c7fd-315">Dit gedrag is hetzelfde als het gebruik van een **bestand** zonder de bewerking te **hervatten**.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-315">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="3c7fd-316">Als de externe server downloaden niet kan hervatten, wordt het lokale bestand overschreven en wordt het hele externe bestand opnieuw gedownload.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-316">If the remote server does not support download resuming, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="3c7fd-317">Dit gedrag is hetzelfde als het gebruik van een **bestand** zonder de bewerking te **hervatten**.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-317">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="3c7fd-318">Als het lokale bestand niet bestaat, wordt het lokale bestand gemaakt en wordt het hele externe bestand gedownload.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-318">If the local file does not exist, then the local file is created and the entire remote file is downloaded.</span></span> <span data-ttu-id="3c7fd-319">Dit gedrag is hetzelfde als het gebruik van een **bestand** zonder de bewerking te **hervatten**.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-319">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="3c7fd-320">Deze functie is toegevoegd aan Power shell 6.1.0.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-320">This feature was added in PowerShell 6.1.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-321">-RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="3c7fd-321">-RetryIntervalSec</span></span>

<span data-ttu-id="3c7fd-322">Hiermee geeft u het interval tussen nieuwe pogingen voor de verbinding op wanneer er een fout code tussen 400 en 599, inclusief of 304 wordt ontvangen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-322">Specifies the interval between retries for the connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="3c7fd-323">Zie ook de para meter **MaximumRetryCount** voor het opgeven van het aantal nieuwe pogingen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-323">Also see **MaximumRetryCount** parameter for specifying number of retries.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-324">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="3c7fd-324">-SessionVariable</span></span>

<span data-ttu-id="3c7fd-325">Hiermee geeft u een variabele op waarvoor deze cmdlet een sessie voor een webaanvraag maakt en opslaat in de waarde.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-325">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="3c7fd-326">Geef een naam op voor de variabele zonder het dollar teken ( `$` )-symbool.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-326">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="3c7fd-327">Wanneer u een sessie variabele opgeeft, `Invoke-WebRequest` maakt een webaanvraag sessie object en wijst deze toe aan een variabele met de opgegeven naam in uw Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-327">When you specify a session variable, `Invoke-WebRequest` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="3c7fd-328">U kunt de variabele in uw sessie gebruiken zodra de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-328">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="3c7fd-329">In tegens telling tot een externe sessie is de sessie voor webaanvragen geen permanente verbinding.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-329">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="3c7fd-330">Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximum omleidings waarde en de teken reeks van de gebruikers agent.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-330">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="3c7fd-331">U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-331">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="3c7fd-332">Als u de webaanvraag sessie in volgende webaanvragen wilt gebruiken, geeft u de sessie variabele op in de waarde van de para meter **websessie** .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-332">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="3c7fd-333">Power shell gebruikt de gegevens in het sessie object voor webaanvragen bij het tot stand brengen van de nieuwe verbinding.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-333">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="3c7fd-334">Als u een waarde in de sessie voor webaanvragen wilt overschrijven, gebruikt u een cmdlet-para meter, zoals **User agent** of **Credential**.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-334">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="3c7fd-335">Parameter waarden hebben prioriteit boven waarden in de webaanvraag sessie.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-335">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="3c7fd-336">U kunt de para meters **SessionVariable** en **websession** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-336">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SV

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-337">-SkipCertificateCheck</span><span class="sxs-lookup"><span data-stu-id="3c7fd-337">-SkipCertificateCheck</span></span>

<span data-ttu-id="3c7fd-338">Hiermee worden controles van certificaat validatie overs Laan.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-338">Skips certificate validation checks.</span></span> <span data-ttu-id="3c7fd-339">Dit omvat alle validaties zoals verval datum, intrekking, vertrouwde basis instantie, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-339">This includes all validations such as expiration, revocation, trusted root authority, etc.</span></span>

> [!WARNING]
> <span data-ttu-id="3c7fd-340">Het gebruik van deze para meter is niet beveiligd en wordt niet aanbevolen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-340">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="3c7fd-341">Deze schakel optie is alleen bedoeld om te worden gebruikt voor bekende hosts met behulp van een zelfondertekend certificaat voor test doeleinden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-341">This switch is only intended to be used against known hosts using a self-signed certificate for testing purposes.</span></span> <span data-ttu-id="3c7fd-342">Gebruiken op eigen risico.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-342">Use at your own risk.</span></span>

<span data-ttu-id="3c7fd-343">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-343">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-344">-SkipHeaderValidation</span><span class="sxs-lookup"><span data-stu-id="3c7fd-344">-SkipHeaderValidation</span></span>

<span data-ttu-id="3c7fd-345">Hiermee wordt aangegeven dat de cmdlet headers zonder validatie moet toevoegen aan de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-345">Indicates the cmdlet should add headers to the request without validation.</span></span>

<span data-ttu-id="3c7fd-346">Deze schakel optie moet worden gebruikt voor sites waarvoor header waarden zijn vereist die niet voldoen aan de standaarden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-346">This switch should be used for sites that require header values that do not conform to standards.</span></span>
<span data-ttu-id="3c7fd-347">Als u deze switch opgeeft, wordt de validatie uitgeschakeld zodat de waarde die wordt door gegeven, niet kan worden gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-347">Specifying this switch disables validation to allow the value to be passed unchecked.</span></span> <span data-ttu-id="3c7fd-348">Als u deze opgeeft, worden alle headers zonder validatie toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-348">When specified, all headers are added without validation.</span></span>

<span data-ttu-id="3c7fd-349">Met deze switch wordt de validatie uitgeschakeld voor waarden die zijn door gegeven aan de para meters **Content type**, **headers** en **User agent** .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-349">This switch disables validation for values passed to the **ContentType**, **Headers** and **UserAgent** parameters.</span></span>

<span data-ttu-id="3c7fd-350">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-350">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-351">-SkipHttpErrorCheck</span><span class="sxs-lookup"><span data-stu-id="3c7fd-351">-SkipHttpErrorCheck</span></span>

<span data-ttu-id="3c7fd-352">Deze para meter zorgt ervoor dat de cmdlet HTTP-fout statussen negeert en de antwoorden blijft verwerken.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-352">This parameter causes the cmdlet to ignore HTTP error statuses and continue to process responses.</span></span>
<span data-ttu-id="3c7fd-353">De fout reacties worden naar de pijp lijn geschreven alsof ze zijn geslaagd.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-353">The error responses are written to the pipeline just as if they were successful.</span></span>

<span data-ttu-id="3c7fd-354">Deze para meter is geïntroduceerd in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-354">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="3c7fd-355">-SslProtocol</span><span class="sxs-lookup"><span data-stu-id="3c7fd-355">-SslProtocol</span></span>

<span data-ttu-id="3c7fd-356">Hiermee stelt u de SSL/TLS-protocollen die zijn toegestaan voor de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-356">Sets the SSL/TLS protocols that are permissible for the web request.</span></span> <span data-ttu-id="3c7fd-357">Standaard zijn alle SSL/TLS-protocollen die door het systeem worden ondersteund, toegestaan.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-357">By default all, SSL/TLS protocols supported by the system are allowed.</span></span> <span data-ttu-id="3c7fd-358">Met **SslProtocol** wordt het beperken van specifieke protocollen voor nalevings doeleinden toegestaan.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-358">**SslProtocol** allows for limiting to specific protocols for compliance purposes.</span></span>

<span data-ttu-id="3c7fd-359">Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-359">These values are defined as a flag-based enumeration.</span></span> <span data-ttu-id="3c7fd-360">U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-360">You can combine multiple values together to set multiple flags using this parameter.</span></span> <span data-ttu-id="3c7fd-361">De waarden kunnen worden door gegeven aan de **SslProtocol** -para meter als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-361">The values can be passed to the **SslProtocol** parameter as an array of values or as a comma-separated string of those values.</span></span> <span data-ttu-id="3c7fd-362">Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-362">The cmdlet will combine the values using a binary-OR operation.</span></span> <span data-ttu-id="3c7fd-363">Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-363">Passing values as an array is the simplest option and also allows you to use tab-completion on the values.</span></span> <span data-ttu-id="3c7fd-364">U kunt mogelijk niet meerdere opties definiëren op alle platformen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-364">You may not be able to define multiple options on all platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="3c7fd-365">Op niet-Windows-platforms is het niet mogelijk om te leveren `Tls` of `Tls12` als optie.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-365">On non-Windows platforms it may not be possible to supply `Tls` or `Tls12` as an option.</span></span> <span data-ttu-id="3c7fd-366">Ondersteuning voor `Tls13` is niet beschikbaar op alle besturings systemen en moet worden geverifieerd op basis van elk besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-366">Support for `Tls13` is not available on all operating systems and will need to be verified on a per operating system basis.</span></span>

<span data-ttu-id="3c7fd-367">Deze functie is toegevoegd aan Power shell 6.0.0 en ondersteuning voor `Tls13` is toegevoegd in Power shell 7,1.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-367">This feature was added in PowerShell 6.0.0 and support for `Tls13` was added in PowerShell 7.1.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WebSslProtocol
Parameter Sets: (All)
Aliases:
Accepted values: Default, Tls, Tls11, Tls12

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-368">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="3c7fd-368">-TimeoutSec</span></span>

<span data-ttu-id="3c7fd-369">Hiermee geeft u op hoe lang de aanvraag in behandeling kan zijn voordat er een time-out optreedt. Voer een waarde in seconden in.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-369">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="3c7fd-370">De standaard waarde, 0, geeft een onbeperkte time-outwaarde.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-370">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="3c7fd-371">Het kan tot vijf tien seconden duren voordat een Domain Name System query (DNS) wordt uitgevoerd of een time-out kan worden geretourneerd. Als uw aanvraag een hostnaam bevat waarvoor omzetting vereist is en u **TimeoutSec** instelt op een waarde die groter is dan nul, maar minder dan 15 seconden, kan het vijf tien seconden of langer duren voordat een webuitzondering wordt gegenereerd en er een time-out optreedt voor uw aanvraag.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-371">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-372">-Token</span><span class="sxs-lookup"><span data-stu-id="3c7fd-372">-Token</span></span>

<span data-ttu-id="3c7fd-373">Het OAuth-of Bearer-token dat in de aanvraag moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-373">The OAuth or Bearer token to include in the request.</span></span> <span data-ttu-id="3c7fd-374">Het **token** is vereist voor bepaalde **verificatie** opties.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-374">**Token** is required by certain **Authentication** options.</span></span> <span data-ttu-id="3c7fd-375">Deze kan niet onafhankelijk worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-375">It cannot be used independently.</span></span>

<span data-ttu-id="3c7fd-376">**Token** neemt een token in beslag `SecureString` .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-376">**Token** takes a `SecureString` containing the token.</span></span> <span data-ttu-id="3c7fd-377">Gebruik het volgende om het token hand matig op te geven:</span><span class="sxs-lookup"><span data-stu-id="3c7fd-377">To supply the token manually use the following:</span></span>

`Invoke-WebRequest -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

<span data-ttu-id="3c7fd-378">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-378">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-379">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="3c7fd-379">-TransferEncoding</span></span>

<span data-ttu-id="3c7fd-380">Hiermee geeft u een waarde op voor de header van de HTTP-reactie voor overdracht/versleuteling.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-380">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="3c7fd-381">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="3c7fd-381">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3c7fd-382">Gesegmenteerde</span><span class="sxs-lookup"><span data-stu-id="3c7fd-382">Chunked</span></span>
- <span data-ttu-id="3c7fd-383">Comprimeren</span><span class="sxs-lookup"><span data-stu-id="3c7fd-383">Compress</span></span>
- <span data-ttu-id="3c7fd-384">Deflate</span><span class="sxs-lookup"><span data-stu-id="3c7fd-384">Deflate</span></span>
- <span data-ttu-id="3c7fd-385">GZip</span><span class="sxs-lookup"><span data-stu-id="3c7fd-385">GZip</span></span>
- <span data-ttu-id="3c7fd-386">Identiteit</span><span class="sxs-lookup"><span data-stu-id="3c7fd-386">Identity</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: chunked, compress, deflate, gzip, identity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-387">-URI</span><span class="sxs-lookup"><span data-stu-id="3c7fd-387">-Uri</span></span>

<span data-ttu-id="3c7fd-388">Hiermee geeft u de URI (Uniform Resource Identifier) op van de Internet bron waarnaar de webaanvraag wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-388">Specifies the Uniform Resource Identifier (URI) of the internet resource to which the web request is sent.</span></span> <span data-ttu-id="3c7fd-389">Voer een URI in.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-389">Enter a URI.</span></span> <span data-ttu-id="3c7fd-390">Deze para meter biedt alleen ondersteuning voor HTTP of HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-390">This parameter supports HTTP or HTTPS only.</span></span>

<span data-ttu-id="3c7fd-391">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-391">This parameter is required.</span></span> <span data-ttu-id="3c7fd-392">De parameter naam **URI** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-392">The parameter name **Uri** is optional.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-393">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="3c7fd-393">-UseBasicParsing</span></span>

<span data-ttu-id="3c7fd-394">Deze para meter is afgeschaft.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-394">This parameter has been deprecated.</span></span> <span data-ttu-id="3c7fd-395">Vanaf Power shell 6.0.0 gebruiken alle webaanvragen alleen basis parsering.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-395">Beginning with PowerShell 6.0.0, all Web requests use basic parsing only.</span></span> <span data-ttu-id="3c7fd-396">Deze para meter is alleen opgenomen voor achterwaartse compatibiliteit en het gebruik ervan heeft geen invloed op de werking van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-396">This parameter is included for backwards compatibility only and any use of it has no effect on the operation of the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-397">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="3c7fd-397">-UseDefaultCredentials</span></span>

<span data-ttu-id="3c7fd-398">Geeft aan dat de cmdlet de referenties van de huidige gebruiker gebruikt om de webaanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-398">Indicates that the cmdlet uses the credentials of the current user to send the web request.</span></span> <span data-ttu-id="3c7fd-399">Deze kan niet worden gebruikt met **verificatie** of **referentie** en wordt mogelijk niet ondersteund op alle platforms.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-399">This can't be used with **Authentication** or **Credential** and may not be supported on all platforms.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-400">-User agent</span><span class="sxs-lookup"><span data-stu-id="3c7fd-400">-UserAgent</span></span>

<span data-ttu-id="3c7fd-401">Hiermee geeft u een teken reeks voor de gebruikers agent op voor de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-401">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="3c7fd-402">De standaard gebruikers agent is vergelijkbaar `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` met kleine variaties voor elk besturings systeem en platform.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-402">The default user agent is similar to `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="3c7fd-403">Als u een website wilt testen met de standaard teken reeks van de gebruikers agent die wordt gebruikt door de meeste Internet browsers, gebruikt u de eigenschappen van de [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) -klasse, zoals Chrome, Firefox, InternetExplorer, Opera en Safari.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-403">To test a website with the standard user agent string that is used by most internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span>

<span data-ttu-id="3c7fd-404">De volgende opdracht maakt bijvoorbeeld gebruik van de teken reeks van de gebruikers agent voor Internet Explorer: `Invoke-WebRequest -Uri https://website.com/ -UserAgent ([Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer)`</span><span class="sxs-lookup"><span data-stu-id="3c7fd-404">For example, the following command uses the user agent string for Internet Explorer: `Invoke-WebRequest -Uri https://website.com/ -UserAgent ([Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer)`</span></span>

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

### <span data-ttu-id="3c7fd-405">-Websessie</span><span class="sxs-lookup"><span data-stu-id="3c7fd-405">-WebSession</span></span>

<span data-ttu-id="3c7fd-406">Hiermee geeft u een sessie voor webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-406">Specifies a web request session.</span></span> <span data-ttu-id="3c7fd-407">Voer de naam van de variabele in, met inbegrip van het dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="3c7fd-407">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="3c7fd-408">Als u een waarde in de sessie voor webaanvragen wilt overschrijven, gebruikt u een cmdlet-para meter, zoals **User agent** of **Credential**.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-408">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="3c7fd-409">Parameter waarden hebben prioriteit boven waarden in de webaanvraag sessie.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-409">Parameter values take precedence over values in the web request session.</span></span> <span data-ttu-id="3c7fd-410">Inhouds gerelateerde kopteksten, zoals `Content-Type` , worden ook genegeerd wanneer een **MultipartFormDataContent** -object wordt opgegeven voor de **hoofd tekst**.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-410">Content related headers, such as `Content-Type`, are also be overridden when a **MultipartFormDataContent** object is supplied for **Body**.</span></span>

<span data-ttu-id="3c7fd-411">In tegens telling tot een externe sessie is de sessie van de webaanvraag geen permanente verbinding.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-411">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="3c7fd-412">Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximum omleidings waarde en de teken reeks van de gebruikers agent.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-412">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="3c7fd-413">U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-413">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="3c7fd-414">Als u een webonderdeelverzoek wilt maken, voert u de naam van een variabele zonder een dollar teken in de waarde van de para meter **SessionVariable** van een `Invoke-WebRequest` opdracht in.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-414">To create a web request session, enter a variable name, without a dollar sign, in the value of the **SessionVariable** parameter of an `Invoke-WebRequest` command.</span></span> <span data-ttu-id="3c7fd-415">`Invoke-WebRequest` Hiermee maakt u de sessie en slaat u deze op in de variabele.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-415">`Invoke-WebRequest` creates the session and saves it in the variable.</span></span> <span data-ttu-id="3c7fd-416">Gebruik in volgende opdrachten de variabele als de waarde van de para meter **websession** .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-416">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="3c7fd-417">U kunt de para meters **SessionVariable** en **websession** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-417">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3c7fd-418">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3c7fd-418">CommonParameters</span></span>

<span data-ttu-id="3c7fd-419">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-419">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3c7fd-420">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-420">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3c7fd-421">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="3c7fd-421">Inputs</span></span>

### <span data-ttu-id="3c7fd-422">System. object</span><span class="sxs-lookup"><span data-stu-id="3c7fd-422">System.Object</span></span>

<span data-ttu-id="3c7fd-423">U kunt de hoofd tekst van een webaanvraag door sluizen naar `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="3c7fd-423">You can pipe the body of a web request to `Invoke-WebRequest`.</span></span>

## <span data-ttu-id="3c7fd-424">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="3c7fd-424">Outputs</span></span>

### <span data-ttu-id="3c7fd-425">Micro soft. Power shell. commands. BasicHtmlWebResponseObject</span><span class="sxs-lookup"><span data-stu-id="3c7fd-425">Microsoft.PowerShell.Commands.BasicHtmlWebResponseObject</span></span>

## <span data-ttu-id="3c7fd-426">Notities</span><span class="sxs-lookup"><span data-stu-id="3c7fd-426">Notes</span></span>

<span data-ttu-id="3c7fd-427">Vanaf Power shell 6.0.0 `Invoke-WebRequest` ondersteunt alleen basis parsering.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-427">Beginning with PowerShell 6.0.0 `Invoke-WebRequest` supports basic parsing only.</span></span>

<span data-ttu-id="3c7fd-428">Zie [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-428">For more information, see [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject).</span></span>

<span data-ttu-id="3c7fd-429">Vanwege wijzigingen in .NET Core 3,1, Power shell 7,0 en hoger, gebruikt u de eigenschap [httpclient maakt. DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) om de proxy configuratie te bepalen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-429">Because of changes in .NET Core 3.1, PowerShell 7.0 and higher use the [HttpClient.DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) Property to determine the proxy configuration.</span></span>

<span data-ttu-id="3c7fd-430">De waarde van deze eigenschap wordt bepaald door uw platform:</span><span class="sxs-lookup"><span data-stu-id="3c7fd-430">The value of this property is determined by your platform:</span></span>

- <span data-ttu-id="3c7fd-431">**Voor Windows**: Hiermee leest u de proxy configuratie van omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-431">**For Windows**: Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="3c7fd-432">Als deze variabelen niet worden gedefinieerd, wordt de eigenschap afgeleid van de proxy-instellingen van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-432">If those variables are not defined the property is derived from the user's proxy settings.</span></span>
- <span data-ttu-id="3c7fd-433">**Voor macOS**: leest de proxy configuratie van omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-433">**For macOS**: Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="3c7fd-434">Als deze variabelen niet worden gedefinieerd, wordt de eigenschap afgeleid van de proxy-instellingen van het systeem.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-434">If those variables are not defined the property is derived from the system's proxy settings.</span></span>
- <span data-ttu-id="3c7fd-435">**Voor Linux**: Hiermee leest u de proxy configuratie van omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-435">**For Linux**: Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="3c7fd-436">Als deze variabelen niet zijn gedefinieerd, initialiseert de eigenschap een niet-geconfigureerd exemplaar dat alle adressen omzeilt.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-436">If those variables are not defined the property initializes a non-configured instance that bypasses all addresses.</span></span>

<span data-ttu-id="3c7fd-437">De omgevings variabelen die worden gebruikt voor de `DefaultProxy` initialisatie op Windows-en UNIX-platforms zijn:</span><span class="sxs-lookup"><span data-stu-id="3c7fd-437">The environment variables used for `DefaultProxy` initialization on Windows and Unix-based platforms are:</span></span>

- <span data-ttu-id="3c7fd-438">`HTTP_PROXY`: de hostnaam of het IP-adres van de proxy server die wordt gebruikt voor HTTP-aanvragen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-438">`HTTP_PROXY`: the hostname or IP address of the proxy server used on HTTP requests.</span></span>
- <span data-ttu-id="3c7fd-439">`HTTPS_PROXY`: de hostnaam of het IP-adres van de proxy server die wordt gebruikt voor HTTPS-aanvragen.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-439">`HTTPS_PROXY`: the hostname or IP address of the proxy server used on HTTPS requests.</span></span>
- <span data-ttu-id="3c7fd-440">`ALL_PROXY`: de hostnaam of het IP-adres van de proxy server die wordt gebruikt voor HTTP-en HTTPS-aanvragen `HTTP_PROXY` of `HTTPS_PROXY` die niet zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-440">`ALL_PROXY`: the hostname or IP address of the proxy server used on HTTP and HTTPS requests in case `HTTP_PROXY` or `HTTPS_PROXY` are not defined.</span></span>
- <span data-ttu-id="3c7fd-441">`NO_PROXY`: een door komma's gescheiden lijst met hostnamen die moeten worden uitgesloten van de proxy.</span><span class="sxs-lookup"><span data-stu-id="3c7fd-441">`NO_PROXY`: a comma-separated list of hostnames that should be excluded from proxying.</span></span>

## <span data-ttu-id="3c7fd-442">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="3c7fd-442">Related Links</span></span>

[<span data-ttu-id="3c7fd-443">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="3c7fd-443">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="3c7fd-444">ConvertFrom-JSON</span><span class="sxs-lookup"><span data-stu-id="3c7fd-444">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="3c7fd-445">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="3c7fd-445">ConvertTo-Json</span></span>](ConvertTo-Json.md)
