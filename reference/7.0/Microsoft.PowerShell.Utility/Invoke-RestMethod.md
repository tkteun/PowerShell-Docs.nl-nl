---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-RestMethod
ms.openlocfilehash: aab7ae73d223f349fc0c103332331710a3eb2efe
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249468"
---
# <span data-ttu-id="f9674-103">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="f9674-103">Invoke-RestMethod</span></span>

## <span data-ttu-id="f9674-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f9674-104">SYNOPSIS</span></span>
<span data-ttu-id="f9674-105">Hiermee verzendt u een HTTP-of HTTPS-aanvraag naar een REST webservice.</span><span class="sxs-lookup"><span data-stu-id="f9674-105">Sends an HTTP or HTTPS request to a RESTful web service.</span></span>

## <span data-ttu-id="f9674-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f9674-106">SYNTAX</span></span>

### <span data-ttu-id="f9674-107">StandardMethod (standaard)</span><span class="sxs-lookup"><span data-stu-id="f9674-107">StandardMethod (Default)</span></span>

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="f9674-108">StandardMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="f9674-108">StandardMethodNoProxy</span></span>

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -NoProxy [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="f9674-109">CustomMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="f9674-109">CustomMethodNoProxy</span></span>

```
Invoke-RestMethod -CustomMethod <String> [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -NoProxy [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="f9674-110">CustomMethod</span><span class="sxs-lookup"><span data-stu-id="f9674-110">CustomMethod</span></span>

```
Invoke-RestMethod -CustomMethod <String> [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

## <span data-ttu-id="f9674-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f9674-111">Description</span></span>

<span data-ttu-id="f9674-112">De `Invoke-RestMethod` cmdlet verzendt HTTP-en HTTPS-aanvragen voor het representatief verzenden van (rest) webservices voor het retour neren van Rich gestructureerde gegevens.</span><span class="sxs-lookup"><span data-stu-id="f9674-112">The `Invoke-RestMethod` cmdlet sends HTTP and HTTPS requests to Representational State Transfer (REST) web services that return richly structured data.</span></span>

<span data-ttu-id="f9674-113">Power shell formatteert het antwoord op basis van het gegevens type.</span><span class="sxs-lookup"><span data-stu-id="f9674-113">PowerShell formats the response based to the data type.</span></span> <span data-ttu-id="f9674-114">Voor een RSS-of ATOM-feed retourneert Power shell het item of de XML-knoop punten van de vermelding.</span><span class="sxs-lookup"><span data-stu-id="f9674-114">For an RSS or ATOM feed, PowerShell returns the Item or Entry XML nodes.</span></span> <span data-ttu-id="f9674-115">Voor JavaScript Object Notation (JSON) of XML, wordt de inhoud door Power shell geconverteerd of gedeserialiseerd naar objecten.</span><span class="sxs-lookup"><span data-stu-id="f9674-115">For JavaScript Object Notation (JSON) or XML, PowerShell converts, or deserializes, the content into objects.</span></span>

<span data-ttu-id="f9674-116">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f9674-116">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="f9674-117">Vanaf Power shell 7,0 `Invoke-RestMethod` ondersteunt proxy configuratie die is gedefinieerd door omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="f9674-117">Beginning in PowerShell 7.0, `Invoke-RestMethod` supports proxy configuration defined by environment variables.</span></span> <span data-ttu-id="f9674-118">Zie de sectie [opmerkingen](#notes) van dit artikel.</span><span class="sxs-lookup"><span data-stu-id="f9674-118">See the [Notes](#notes) section of this article.</span></span>

## <span data-ttu-id="f9674-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f9674-119">EXAMPLES</span></span>

### <span data-ttu-id="f9674-120">Voor beeld 1: de Power shell-RSS-feed ophalen</span><span class="sxs-lookup"><span data-stu-id="f9674-120">Example 1: Get the PowerShell RSS feed</span></span>

<span data-ttu-id="f9674-121">In dit voor beeld wordt de `Invoke-RestMethod` cmdlet gebruikt om informatie op te halen uit de RSS-feed voor het Power shell-blog.</span><span class="sxs-lookup"><span data-stu-id="f9674-121">This example uses the `Invoke-RestMethod` cmdlet to get information from the PowerShell Blog RSS feed.</span></span> <span data-ttu-id="f9674-122">De opdracht gebruikt de `Format-Table` cmdlet om de waarden van de eigenschappen **title** en **pubDate** van elke blog in een tabel weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f9674-122">The command uses the `Format-Table` cmdlet to display the values of the **Title** and **pubDate** properties of each blog in a table.</span></span>

```powershell
Invoke-RestMethod -Uri https://blogs.msdn.microsoft.com/powershell/feed/ |
  Format-Table -Property Title, pubDate
```

```Output
Title                                                                pubDate
-----                                                                -------
Join the PowerShell 10th Anniversary Celebration!                    Tue, 08 Nov 2016 23:00:04 +0000
DSC Resource Kit November 2016 Release                               Thu, 03 Nov 2016 00:19:07 +0000
PSScriptAnalyzer Community Call - Oct 18, 2016                       Thu, 13 Oct 2016 17:52:35 +0000
New Home for In-Box DSC Resources                                    Sat, 08 Oct 2016 07:13:10 +0000
New Social Features on Gallery                                       Fri, 30 Sep 2016 23:04:34 +0000
PowerShellGet and PackageManagement in PowerShell Gallery and GitHub Thu, 29 Sep 2016 22:21:42 +0000
PowerShell Security at DerbyCon                                      Wed, 28 Sep 2016 01:13:19 +0000
DSC Resource Kit September Release                                   Thu, 22 Sep 2016 00:25:37 +0000
PowerShell DSC and implicit remoting broken in KB3176934             Tue, 23 Aug 2016 15:07:50 +0000
PowerShell on Linux and Open Source!                                 Thu, 18 Aug 2016 15:32:02 +0000
```

### <span data-ttu-id="f9674-123">Voor beeld 2: een POST-aanvraag uitvoeren</span><span class="sxs-lookup"><span data-stu-id="f9674-123">Example 2: Run a POST request</span></span>

<span data-ttu-id="f9674-124">In dit voor beeld wordt een gebruiker uitgevoerd `Invoke-RestMethod` om een post-aanvraag uit te voeren op een intranet website in de organisatie van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f9674-124">In this example, a user runs `Invoke-RestMethod` to do a POST request on an intranet website in the user's organization.</span></span>

```powershell
$Cred = Get-Credential
$Url = "https://server.contoso.com:8089/services/search/jobs/export"
$Body = @{
    search = "search index=_internal | reverse | table index,host,source,sourcetype,_raw"
    output_mode = "csv"
    earliest_time = "-2d@d"
    latest_time = "-1d@d"
}
Invoke-RestMethod -Method 'Post' -Uri $url -Credential $Cred -Body $body -OutFile output.csv
```

<span data-ttu-id="f9674-125">De referenties worden gevraagd en vervolgens opgeslagen in `$Cred` en de URL waartoe toegang wordt gegeven, wordt gedefinieerd in `$Url` .</span><span class="sxs-lookup"><span data-stu-id="f9674-125">The credentials are prompted for and then stored in `$Cred` and the URL that will be access is defined in `$Url`.</span></span>

<span data-ttu-id="f9674-126">De `$Body` variabele beschrijft de zoek criteria, geeft CSV op als uitvoer modus en geeft een periode op voor de geretourneerde gegevens die twee dagen geleden worden gestart en eindigt een dag geleden.</span><span class="sxs-lookup"><span data-stu-id="f9674-126">The `$Body` variable describes the search criteria, specifies CSV as the output mode, and specifies a time period for returned data that starts two days ago and ends one day ago.</span></span> <span data-ttu-id="f9674-127">De variabele body geeft waarden op voor para meters die van toepassing zijn op het specifieke REST API waarmee `Invoke-RestMethod` wordt gecommuniceerd.</span><span class="sxs-lookup"><span data-stu-id="f9674-127">The body variable specifies values for parameters that apply to the particular REST API with which `Invoke-RestMethod` is communicating.</span></span>

<span data-ttu-id="f9674-128">De `Invoke-RestMethod` opdracht wordt uitgevoerd met alle variabelen op locatie, waarbij een pad en een bestands naam voor het resulterende CSV-uitvoer bestand worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f9674-128">The `Invoke-RestMethod` command is run with all variables in place, specifying a path and file name for the resulting CSV output file.</span></span>

### <span data-ttu-id="f9674-129">Voor beeld 3: relatie koppelingen volgen</span><span class="sxs-lookup"><span data-stu-id="f9674-129">Example 3: Follow relation links</span></span>

<span data-ttu-id="f9674-130">Sommige REST Api's ondersteunen paginering via relatie koppelingen per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span><span class="sxs-lookup"><span data-stu-id="f9674-130">Some REST APIs support pagination via Relation Links per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span></span> <span data-ttu-id="f9674-131">In plaats van de header te parseren om de URL voor de volgende pagina op te halen, kunt u de cmdlet dit voor u laten doen.</span><span class="sxs-lookup"><span data-stu-id="f9674-131">Instead of parsing the header to get the URL for the next page, you can have the cmdlet do this for you.</span></span> <span data-ttu-id="f9674-132">In dit voor beeld worden de eerste twee pagina's met problemen uit de Power shell GitHub-opslag plaats geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f9674-132">This example returns the first two pages of issues from the PowerShell GitHub repository.</span></span>

```powershell
$url = 'https://api.github.com/repos/powershell/powershell/issues'
Invoke-RestMethod $url -FollowRelLink -MaximumFollowRelLink 2
```

### <span data-ttu-id="f9674-133">Voor beeld 4: vereenvoudigd meerdelige/formulier-data verzen ding</span><span class="sxs-lookup"><span data-stu-id="f9674-133">Example 4: Simplified Multipart/Form-Data Submission</span></span>

<span data-ttu-id="f9674-134">Voor sommige Api's zijn `multipart/form-data` inzendingen vereist om bestanden en gemengde inhoud te uploaden.</span><span class="sxs-lookup"><span data-stu-id="f9674-134">Some APIs require `multipart/form-data` submissions to upload files and mixed content.</span></span> <span data-ttu-id="f9674-135">In dit voor beeld ziet u hoe u het profiel van een gebruiker bijwerkt.</span><span class="sxs-lookup"><span data-stu-id="f9674-135">This example demonstrates how to update a user's profile.</span></span>

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
$Result = Invoke-RestMethod -Uri $Uri -Method Post -Form $Form
```

<span data-ttu-id="f9674-136">Voor het profiel formulier zijn de volgende velden vereist: `firstName` ,, `lastName` ,, `email` `avatar` `birthday` en `hobbies` .</span><span class="sxs-lookup"><span data-stu-id="f9674-136">The profile form requires these fields: `firstName`, `lastName`, `email`, `avatar`, `birthday`, and `hobbies`.</span></span> <span data-ttu-id="f9674-137">De API verwacht een installatie kopie voor het gebruikers profiel pic dat in het veld moet worden opgegeven `avatar` .</span><span class="sxs-lookup"><span data-stu-id="f9674-137">The API is expecting an image for the user profile pic to be supplied in the `avatar` field.</span></span> <span data-ttu-id="f9674-138">In de API worden ook meerdere `hobbies` vermeldingen geaccepteerd die in hetzelfde formulier moeten worden ingediend.</span><span class="sxs-lookup"><span data-stu-id="f9674-138">The API will also accept multiple `hobbies` entries to be submitted in the same form.</span></span>

<span data-ttu-id="f9674-139">Wanneer u de `$Form` hashtabel maakt, worden de sleutel namen gebruikt als formulier veld namen.</span><span class="sxs-lookup"><span data-stu-id="f9674-139">When creating the `$Form` HashTable, the key names are used as form field names.</span></span> <span data-ttu-id="f9674-140">Standaard worden de waarden van de hashtabel geconverteerd naar teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f9674-140">By default, the values of the HashTable will be converted to strings.</span></span> <span data-ttu-id="f9674-141">Als er een `System.IO.FileInfo` waarde aanwezig is, wordt de inhoud van het bestand verzonden.</span><span class="sxs-lookup"><span data-stu-id="f9674-141">If a `System.IO.FileInfo` value is present, the file contents will be submitted.</span></span> <span data-ttu-id="f9674-142">Als er een verzameling zoals matrices of lijsten aanwezig is, wordt het formulier veld meerdere keren verzonden.</span><span class="sxs-lookup"><span data-stu-id="f9674-142">If a collection such as arrays or lists are present, the form field will be submitted multiple times.</span></span>

<span data-ttu-id="f9674-143">Door `Get-Item` op de sleutel te gebruiken `avatar` , `FileInfo` wordt het object ingesteld als de waarde.</span><span class="sxs-lookup"><span data-stu-id="f9674-143">By using `Get-Item` on the `avatar` key, the `FileInfo` object will be set as the value.</span></span> <span data-ttu-id="f9674-144">Het resultaat is dat de afbeeldings gegevens voor worden `jdoe.png` verzonden.</span><span class="sxs-lookup"><span data-stu-id="f9674-144">The result is that the image data for `jdoe.png` will be submitted.</span></span>

<span data-ttu-id="f9674-145">Door een lijst aan de sleutel toe te voegen `hobbies` , `hobbies` wordt het veld voor elk lijst item één keer weer gegeven in de-verzen ding.</span><span class="sxs-lookup"><span data-stu-id="f9674-145">By supplying a list to the `hobbies` key, the `hobbies` field will be present in the submissions once for each list item.</span></span>

### <span data-ttu-id="f9674-146">Voor beeld 5: meerdere headers door geven</span><span class="sxs-lookup"><span data-stu-id="f9674-146">Example 5: Pass multiple headers</span></span>

<span data-ttu-id="f9674-147">Api's vereisen vaak door gegeven headers voor verificatie of validatie.</span><span class="sxs-lookup"><span data-stu-id="f9674-147">APIs often require passed headers for authentication or validation.</span></span> <span data-ttu-id="f9674-148">In dit voor beeld ziet u hoe u meerdere headers van een `hash-table` naar een rest API doorgeeft.</span><span class="sxs-lookup"><span data-stu-id="f9674-148">This example demonstrates, how to pass multiple headers from a `hash-table` to a REST API.</span></span>

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

## <span data-ttu-id="f9674-149">Parameters</span><span class="sxs-lookup"><span data-stu-id="f9674-149">Parameters</span></span>

### <span data-ttu-id="f9674-150">-AllowUnencryptedAuthentication</span><span class="sxs-lookup"><span data-stu-id="f9674-150">-AllowUnencryptedAuthentication</span></span>

<span data-ttu-id="f9674-151">Hiermee staat u het verzenden van referenties en geheimen over niet-versleutelde verbindingen toe.</span><span class="sxs-lookup"><span data-stu-id="f9674-151">Allows sending of credentials and secrets over unencrypted connections.</span></span> <span data-ttu-id="f9674-152">Standaard leidt het leveren van **referenties** of een **authenticatie** optie met een **URI** die niet begint met een `https://` fout en wordt de aanvraag afgebroken om onbedoeld geheimen te communiceren in tekst zonder opmaak over niet-versleutelde verbindingen.</span><span class="sxs-lookup"><span data-stu-id="f9674-152">By default, supplying **Credential** or any **Authentication** option with a **Uri** that does not begin with `https://` will result in an error and the request will abort to prevent unintentionally communicating secrets in plain text over unencrypted connections.</span></span> <span data-ttu-id="f9674-153">U kunt dit gedrag voor eigen risico negeren door de para meter **AllowUnencryptedAuthentication** op te geven.</span><span class="sxs-lookup"><span data-stu-id="f9674-153">To override this behavior at your own risk, supply the **AllowUnencryptedAuthentication** parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="f9674-154">Het gebruik van deze para meter is niet beveiligd en wordt niet aanbevolen.</span><span class="sxs-lookup"><span data-stu-id="f9674-154">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="f9674-155">Het is alleen beschikbaar voor compatibiliteit met oudere systemen die geen versleutelde verbindingen kunnen bieden.</span><span class="sxs-lookup"><span data-stu-id="f9674-155">It is provided only for compatibility with legacy systems that cannot provide encrypted connections.</span></span> <span data-ttu-id="f9674-156">Gebruiken op eigen risico.</span><span class="sxs-lookup"><span data-stu-id="f9674-156">Use at your own risk.</span></span>

<span data-ttu-id="f9674-157">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="f9674-157">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="f9674-158">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="f9674-158">-Authentication</span></span>

<span data-ttu-id="f9674-159">Hiermee geeft u het expliciete verificatie type op dat moet worden gebruikt voor de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="f9674-159">Specifies the explicit authentication type to use for the request.</span></span> <span data-ttu-id="f9674-160">De standaardwaarde is **None**.</span><span class="sxs-lookup"><span data-stu-id="f9674-160">The default is **None**.</span></span>
<span data-ttu-id="f9674-161">**Authenticatie** kan niet worden gebruikt met **UseDefaultCredentials**.</span><span class="sxs-lookup"><span data-stu-id="f9674-161">**Authentication** can't be used with **UseDefaultCredentials**.</span></span>

<span data-ttu-id="f9674-162">Beschik bare verificatie opties:</span><span class="sxs-lookup"><span data-stu-id="f9674-162">Available Authentication Options:</span></span>

- <span data-ttu-id="f9674-163">**Geen** : dit is de standaard optie wanneer er geen **verificatie** is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f9674-163">**None** : This is the default option when **Authentication** is not supplied.</span></span> <span data-ttu-id="f9674-164">Er wordt geen expliciete authenticatie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f9674-164">No explicit authentication will be used.</span></span>
- <span data-ttu-id="f9674-165">**Basic** : vereist **referentie**.</span><span class="sxs-lookup"><span data-stu-id="f9674-165">**Basic** : Requires **Credential**.</span></span> <span data-ttu-id="f9674-166">De referenties worden gebruikt voor het verzenden van een RFC 7617-basis verificatie `Authorization: Basic` header in de indeling van `base64(user:password)` .</span><span class="sxs-lookup"><span data-stu-id="f9674-166">The credentials will be used to send an RFC 7617 Basic Authentication `Authorization: Basic` header in the format of `base64(user:password)`.</span></span>
- <span data-ttu-id="f9674-167">**Bearer** : **token** vereist.</span><span class="sxs-lookup"><span data-stu-id="f9674-167">**Bearer** : Requires **Token**.</span></span> <span data-ttu-id="f9674-168">Verzendt en RFC 6750- `Authorization: Bearer` header met het opgegeven token.</span><span class="sxs-lookup"><span data-stu-id="f9674-168">Will send and RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="f9674-169">Dit is een alias voor **OAuth**</span><span class="sxs-lookup"><span data-stu-id="f9674-169">This is an alias for **OAuth**</span></span>
- <span data-ttu-id="f9674-170">**OAuth** : **token** vereist.</span><span class="sxs-lookup"><span data-stu-id="f9674-170">**OAuth** : Requires **Token**.</span></span> <span data-ttu-id="f9674-171">Er wordt een RFC 6750- `Authorization: Bearer` header verzonden met het opgegeven token.</span><span class="sxs-lookup"><span data-stu-id="f9674-171">Will send an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="f9674-172">Dit is een alias voor **Bearer**</span><span class="sxs-lookup"><span data-stu-id="f9674-172">This is an alias for **Bearer**</span></span>

<span data-ttu-id="f9674-173">Bij het leveren van **verificatie** worden alle `Authorization` headers die zijn opgegeven in **headers** of opgenomen in **websessie** , overschreven.</span><span class="sxs-lookup"><span data-stu-id="f9674-173">Supplying **Authentication** will override any `Authorization` headers supplied to **Headers** or included in **WebSession**.</span></span>

<span data-ttu-id="f9674-174">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="f9674-174">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="f9674-175">-Hoofd tekst</span><span class="sxs-lookup"><span data-stu-id="f9674-175">-Body</span></span>

<span data-ttu-id="f9674-176">Hiermee geeft u de hoofd tekst van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="f9674-176">Specifies the body of the request.</span></span> <span data-ttu-id="f9674-177">De hoofd tekst is de inhoud van de aanvraag die de headers volgt.</span><span class="sxs-lookup"><span data-stu-id="f9674-177">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="f9674-178">U kunt ook de waarde van een hoofd tekst sluist naar `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="f9674-178">You can also pipe a body value to `Invoke-RestMethod`.</span></span>

<span data-ttu-id="f9674-179">De para meter **Body** kan worden gebruikt om een lijst met query parameters op te geven of de inhoud van het antwoord op te geven.</span><span class="sxs-lookup"><span data-stu-id="f9674-179">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="f9674-180">Wanneer de invoer een GET-aanvraag is en de hoofd tekst een `IDictionary` (meestal een hash-tabel) is, wordt de hoofd tekst als query parameters aan de URI (Uniform Resource Identifier) toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="f9674-180">When the input is a GET request, and the body is an `IDictionary` (typically, a hash table), the body is added to the Uniform Resource Identifier (URI) as query parameters.</span></span> <span data-ttu-id="f9674-181">Voor andere aanvraag typen (zoals POST) wordt de hoofd tekst ingesteld als de waarde van de aanvraag tekst in de notatie standaard naam = waarde.</span><span class="sxs-lookup"><span data-stu-id="f9674-181">For other request types (such as POST), the body is set as the value of the request body in the standard name=value format.</span></span>

<span data-ttu-id="f9674-182">Wanneer de hoofd tekst een formulier is of de uitvoer van een andere `Invoke-WebRequest` aanroep is, stelt Power shell de aanvraag inhoud in op de formulier velden.</span><span class="sxs-lookup"><span data-stu-id="f9674-182">When the body is a form, or it's the output of another `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>

<span data-ttu-id="f9674-183">De para meter **Body** kan ook een **systeem .net. http. MultipartFormDataContent-** object accepteren.</span><span class="sxs-lookup"><span data-stu-id="f9674-183">The **Body** parameter may also accept a **System.Net.Http.MultipartFormDataContent** object.</span></span> <span data-ttu-id="f9674-184">Hierdoor kunnen aanvragen worden vergemakkelijkt `multipart/form-data` .</span><span class="sxs-lookup"><span data-stu-id="f9674-184">This will facilitate `multipart/form-data` requests.</span></span> <span data-ttu-id="f9674-185">Wanneer een **MultipartFormDataContent** -object wordt opgegeven voor de **hoofd tekst** , worden alle aan de inhouds headers van het object gerelateerde kopteksten die zijn opgegeven voor de **Content type** -, **headers** -of **websessie** -para meters, overschreven `MultipartFormDataContent` .</span><span class="sxs-lookup"><span data-stu-id="f9674-185">When a **MultipartFormDataContent** object is supplied for **Body** , any content related headers supplied to the **ContentType** , **Headers** , or **WebSession** parameters will be overridden by the content headers of the `MultipartFormDataContent` object.</span></span> <span data-ttu-id="f9674-186">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="f9674-186">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="f9674-187">-Certificaat</span><span class="sxs-lookup"><span data-stu-id="f9674-187">-Certificate</span></span>

<span data-ttu-id="f9674-188">Hiermee geeft u het client certificaat op dat wordt gebruikt voor een beveiligde webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="f9674-188">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="f9674-189">Voer een variabele in die een certificaat of een opdracht of expressie bevat waarmee het certificaat wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f9674-189">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="f9674-190">Als u een certificaat wilt zoeken, gebruikt `Get-PfxCertificate` of gebruikt u de `Get-ChildItem` cmdlet in het certificaat `Cert:` station.</span><span class="sxs-lookup"><span data-stu-id="f9674-190">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="f9674-191">Als het certificaat ongeldig is of niet voldoende autoriteit heeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="f9674-191">If the certificate isn't valid or doesn't have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="f9674-192">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="f9674-192">-CertificateThumbprint</span></span>

<span data-ttu-id="f9674-193">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat gemachtigd is om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="f9674-193">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="f9674-194">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="f9674-194">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="f9674-195">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="f9674-195">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="f9674-196">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="f9674-196">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="f9674-197">Gebruik de `Get-Item` `Get-ChildItem` opdracht of in het Power Shell-station om een certificaat vingerafdruk te verkrijgen `Cert:` .</span><span class="sxs-lookup"><span data-stu-id="f9674-197">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

> [!NOTE]
> <span data-ttu-id="f9674-198">Deze functie wordt momenteel alleen ondersteund op Windows-besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="f9674-198">This feature is currently only supported on Windows OS platforms.</span></span>

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

### <span data-ttu-id="f9674-199">-Content type</span><span class="sxs-lookup"><span data-stu-id="f9674-199">-ContentType</span></span>

<span data-ttu-id="f9674-200">Hiermee geeft u het type inhoud van de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="f9674-200">Specifies the content type of the web request.</span></span>

<span data-ttu-id="f9674-201">Als deze para meter wordt wegge laten en de aanvraag methode is `Invoke-RestMethod` ingesteld op post, stelt het inhouds type in op `application/x-www-form-urlencoded` .</span><span class="sxs-lookup"><span data-stu-id="f9674-201">If this parameter is omitted and the request method is POST, `Invoke-RestMethod` sets the content type to `application/x-www-form-urlencoded`.</span></span> <span data-ttu-id="f9674-202">Anders is het inhouds type niet opgegeven in de aanroep.</span><span class="sxs-lookup"><span data-stu-id="f9674-202">Otherwise, the content type isn't specified in the call.</span></span>

<span data-ttu-id="f9674-203">**Content type** wordt overschreven wanneer een `MultipartFormDataContent` object wordt opgegeven voor de **hoofd tekst**.</span><span class="sxs-lookup"><span data-stu-id="f9674-203">**ContentType** will be overridden when a `MultipartFormDataContent` object is supplied for **Body**.</span></span>

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

### <span data-ttu-id="f9674-204">-Credential</span><span class="sxs-lookup"><span data-stu-id="f9674-204">-Credential</span></span>

<span data-ttu-id="f9674-205">Hiermee geeft u een gebruikers account op dat gemachtigd is om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="f9674-205">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="f9674-206">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f9674-206">The default is the current user.</span></span>

<span data-ttu-id="f9674-207">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="f9674-207">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="f9674-208">**Referentie** kan alleen worden gebruikt of in combi natie met bepaalde opties voor **verificatie** parameters.</span><span class="sxs-lookup"><span data-stu-id="f9674-208">**Credential** can be used alone or in conjunction with certain **Authentication** parameter options.</span></span> <span data-ttu-id="f9674-209">Als u alleen gebruikt, worden er alleen referenties voor de externe server verstrekt als de externe server een aanvraag voor verificatie controle verzendt.</span><span class="sxs-lookup"><span data-stu-id="f9674-209">When used alone, it will only supply credentials to the remote server if the remote server sends an authentication challenge request.</span></span> <span data-ttu-id="f9674-210">Wanneer u gebruikt met **verificatie** opties, worden de referenties expliciet verzonden.</span><span class="sxs-lookup"><span data-stu-id="f9674-210">When used with **Authentication** options, the credentials will be explicitly sent.</span></span>

<span data-ttu-id="f9674-211">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="f9674-211">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="f9674-212">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="f9674-212">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="f9674-213">-CustomMethod</span><span class="sxs-lookup"><span data-stu-id="f9674-213">-CustomMethod</span></span>

<span data-ttu-id="f9674-214">Hiermee geeft u de aangepaste methode op die voor de webaanvraag wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f9674-214">Specifies custom method used for the web request.</span></span> <span data-ttu-id="f9674-215">Dit kan worden gebruikt met de aanvraag methode die door het eind punt wordt vereist, is geen beschik bare optie voor de **methode**.</span><span class="sxs-lookup"><span data-stu-id="f9674-215">This can be used with the Request Method required by the endpoint is not an available option on the **Method**.</span></span> <span data-ttu-id="f9674-216">**Methode** en **CustomMethod** kunnen niet tegelijk worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f9674-216">**Method** and **CustomMethod** cannot be used together.</span></span>

<span data-ttu-id="f9674-217">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f9674-217">Example:</span></span>

`Invoke-RestMethod -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

<span data-ttu-id="f9674-218">Hiermee maakt `TEST` u een HTTP-aanvraag voor de API.</span><span class="sxs-lookup"><span data-stu-id="f9674-218">This makes a `TEST` HTTP request to the API.</span></span>

<span data-ttu-id="f9674-219">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="f9674-219">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.String
Parameter Sets: CustomMethodNoProxy, CustomMethod
Aliases: CM

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9674-220">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="f9674-220">-DisableKeepAlive</span></span>

<span data-ttu-id="f9674-221">Geeft aan dat de cmdlet de **keepalive** -waarde in de http-header instelt op false.</span><span class="sxs-lookup"><span data-stu-id="f9674-221">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to False.</span></span> <span data-ttu-id="f9674-222">Standaard is **keepalive** ingesteld op True.</span><span class="sxs-lookup"><span data-stu-id="f9674-222">By default, **KeepAlive** is True.</span></span> <span data-ttu-id="f9674-223">Met **keepalive** wordt een permanente verbinding met de server tot stand gebracht om volgende aanvragen te vergemakkelijken.</span><span class="sxs-lookup"><span data-stu-id="f9674-223">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="f9674-224">-FollowRelLink</span><span class="sxs-lookup"><span data-stu-id="f9674-224">-FollowRelLink</span></span>

<span data-ttu-id="f9674-225">Hiermee wordt aangegeven dat de cmdlet relatie koppelingen moet volgen.</span><span class="sxs-lookup"><span data-stu-id="f9674-225">Indicates the cmdlet should follow relation links.</span></span>

<span data-ttu-id="f9674-226">Sommige REST Api's ondersteunen paginering via relatie koppelingen per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span><span class="sxs-lookup"><span data-stu-id="f9674-226">Some REST APIs support pagination via Relation Links per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span></span> <span data-ttu-id="f9674-227">In plaats van de header te parseren om de URL voor de volgende pagina op te halen, kunt u de cmdlet dit voor u laten doen.</span><span class="sxs-lookup"><span data-stu-id="f9674-227">Instead of parsing the header to get the URL for the next page, you can have the cmdlet do this for you.</span></span> <span data-ttu-id="f9674-228">Als u wilt instellen hoe vaak de relatie koppelingen moet worden gevolgd, gebruikt u de para meter **MaximumFollowRelLink** .</span><span class="sxs-lookup"><span data-stu-id="f9674-228">To set how many times to follow relation links, use the **MaximumFollowRelLink** parameter.</span></span>

<span data-ttu-id="f9674-229">Wanneer u deze switch gebruikt, retourneert de cmdlet een verzameling pagina's met resultaten.</span><span class="sxs-lookup"><span data-stu-id="f9674-229">When using this switch, the cmdlet returns a collection of pages of results.</span></span> <span data-ttu-id="f9674-230">Elke pagina met resultaten kan meerdere resultaten items bevatten.</span><span class="sxs-lookup"><span data-stu-id="f9674-230">Each page of results may contain multiple result items.</span></span>

<span data-ttu-id="f9674-231">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="f9674-231">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: FL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9674-232">-Vorm</span><span class="sxs-lookup"><span data-stu-id="f9674-232">-Form</span></span>

<span data-ttu-id="f9674-233">Converteert een woorden lijst naar een `multipart/form-data` inzending.</span><span class="sxs-lookup"><span data-stu-id="f9674-233">Converts a dictionary to a `multipart/form-data` submission.</span></span> <span data-ttu-id="f9674-234">Het **formulier** kan niet worden gebruikt met een **hoofd tekst**.</span><span class="sxs-lookup"><span data-stu-id="f9674-234">**Form** may not be used with **Body**.</span></span>
<span data-ttu-id="f9674-235">Als **Content type** wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="f9674-235">If **ContentType** will be ignored.</span></span>

<span data-ttu-id="f9674-236">De sleutels van de woorden lijst worden gebruikt als de veld namen van het formulier.</span><span class="sxs-lookup"><span data-stu-id="f9674-236">The keys of the dictionary will be used as the form field names.</span></span> <span data-ttu-id="f9674-237">Standaard worden formulier waarden geconverteerd naar teken reeks waarden.</span><span class="sxs-lookup"><span data-stu-id="f9674-237">By default, form values will be converted to string values.</span></span>

<span data-ttu-id="f9674-238">Als de waarde een **System. io. file info** -object is, wordt de inhoud van het binaire bestand verzonden.</span><span class="sxs-lookup"><span data-stu-id="f9674-238">If the value is a **System.IO.FileInfo** object, then the binary file contents will be submitted.</span></span>
<span data-ttu-id="f9674-239">De naam van het bestand wordt verzonden als `filename` .</span><span class="sxs-lookup"><span data-stu-id="f9674-239">The name of the file will be submitted as the `filename`.</span></span> <span data-ttu-id="f9674-240">De MIME wordt ingesteld als `application/octet-stream` .</span><span class="sxs-lookup"><span data-stu-id="f9674-240">The MIME will be set as `application/octet-stream`.</span></span> <span data-ttu-id="f9674-241">`Get-Item` kan worden gebruikt om het object **System. io. file info** te vereenvoudigen.</span><span class="sxs-lookup"><span data-stu-id="f9674-241">`Get-Item` can be used to simplify supplying the **System.IO.FileInfo** object.</span></span>

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

<span data-ttu-id="f9674-242">Als de waarde een verzamelings type is, zoals een matrix of lijst, wordt het veld voor meerdere keren verzonden.</span><span class="sxs-lookup"><span data-stu-id="f9674-242">If the value is a collection type, such as an Array or List, the for field will be submitted multiple times.</span></span> <span data-ttu-id="f9674-243">De waarden van de lijst worden standaard beschouwd als teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f9674-243">The values of the list will be treated as strings by default.</span></span> <span data-ttu-id="f9674-244">Als de waarde een **System. io. file info** -object is, wordt de inhoud van het binaire bestand verzonden.</span><span class="sxs-lookup"><span data-stu-id="f9674-244">If the value is a **System.IO.FileInfo** object, then the binary file contents will be submitted.</span></span> <span data-ttu-id="f9674-245">Geneste verzamelingen worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="f9674-245">Nested collections aren't supported.</span></span>

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

<span data-ttu-id="f9674-246">In het bovenstaande voor beeld `tags` wordt het veld drie keer in het formulier opgegeven, eenmaal voor elk van `Vacation` , `Italy` en `2017` .</span><span class="sxs-lookup"><span data-stu-id="f9674-246">In the above example, the `tags` field will be supplied three times in the form, once for each of `Vacation`, `Italy`, and `2017`.</span></span> <span data-ttu-id="f9674-247">Het `pictures` veld wordt ook één keer verzonden voor elk bestand in de `2017-Italy` map.</span><span class="sxs-lookup"><span data-stu-id="f9674-247">The `pictures` field will also be submitted once for each file in the `2017-Italy` folder.</span></span> <span data-ttu-id="f9674-248">De binaire inhoud van de bestanden in die map wordt verzonden als de waarden.</span><span class="sxs-lookup"><span data-stu-id="f9674-248">The binary contents of the files in that folder will be submitted as the values.</span></span>

<span data-ttu-id="f9674-249">Deze functie is toegevoegd aan Power shell 6.1.0.</span><span class="sxs-lookup"><span data-stu-id="f9674-249">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="f9674-250">-Headers</span><span class="sxs-lookup"><span data-stu-id="f9674-250">-Headers</span></span>

<span data-ttu-id="f9674-251">Hiermee geeft u de kopteksten van de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="f9674-251">Specifies the headers of the web request.</span></span> <span data-ttu-id="f9674-252">Voer een hash-tabel of-woorden lijst in.</span><span class="sxs-lookup"><span data-stu-id="f9674-252">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="f9674-253">Gebruik de **agent** -para meter om de agent headers in te stellen.</span><span class="sxs-lookup"><span data-stu-id="f9674-253">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="f9674-254">U kunt deze para meter niet gebruiken om headers op te geven `User-Agent` of te cookie.</span><span class="sxs-lookup"><span data-stu-id="f9674-254">You cannot use this parameter to specify `User-Agent` or cookie headers.</span></span>

<span data-ttu-id="f9674-255">Aan inhoud gerelateerde kopteksten, zoals `Content-Type` wordt overschreven wanneer een `MultipartFormDataContent` object wordt opgegeven voor de **hoofd tekst**.</span><span class="sxs-lookup"><span data-stu-id="f9674-255">Content related headers, such as `Content-Type` will be overridden when a `MultipartFormDataContent` object is supplied for **Body**.</span></span>

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

### <span data-ttu-id="f9674-256">-Inbestand</span><span class="sxs-lookup"><span data-stu-id="f9674-256">-InFile</span></span>

<span data-ttu-id="f9674-257">Hiermee wordt de inhoud van de webaanvraag opgehaald uit een bestand.</span><span class="sxs-lookup"><span data-stu-id="f9674-257">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="f9674-258">Voer een pad en een bestands naam in.</span><span class="sxs-lookup"><span data-stu-id="f9674-258">Enter a path and file name.</span></span> <span data-ttu-id="f9674-259">Als u het pad weglaat, de standaard instelling is de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="f9674-259">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="f9674-260">-MaximumFollowRelLink</span><span class="sxs-lookup"><span data-stu-id="f9674-260">-MaximumFollowRelLink</span></span>

<span data-ttu-id="f9674-261">Hiermee geeft u op hoe vaak de relatie koppelingen moeten worden gevolgd als **FollowRelLink** wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f9674-261">Specifies how many times to follow relation links if **FollowRelLink** is used.</span></span> <span data-ttu-id="f9674-262">Een kleinere waarde kan nodig zijn als de REST API-beperking door te veel aanvragen is.</span><span class="sxs-lookup"><span data-stu-id="f9674-262">A smaller value may be needed if the REST api throttles due to too many requests.</span></span> <span data-ttu-id="f9674-263">De standaardwaarde is `[Int32]::MaxValue`.</span><span class="sxs-lookup"><span data-stu-id="f9674-263">The default value is `[Int32]::MaxValue`.</span></span> <span data-ttu-id="f9674-264">Een waarde van 0 (nul) voor komt de volgende relatie koppelingen.</span><span class="sxs-lookup"><span data-stu-id="f9674-264">A value of 0 (zero) prevents following relation links.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: ML

Required: False
Position: Named
Default value: Int32.MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9674-265">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="f9674-265">-MaximumRedirection</span></span>

<span data-ttu-id="f9674-266">Hiermee geeft u op hoe vaak Power shell een verbinding met een alternatieve URI (Uniform Resource Identifier) omleidt voordat de verbinding is mislukt.</span><span class="sxs-lookup"><span data-stu-id="f9674-266">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="f9674-267">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="f9674-267">The default value is 5.</span></span> <span data-ttu-id="f9674-268">Een waarde van 0 (nul) voor komt dat alle omleidingen.</span><span class="sxs-lookup"><span data-stu-id="f9674-268">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="f9674-269">-MaximumRetryCount</span><span class="sxs-lookup"><span data-stu-id="f9674-269">-MaximumRetryCount</span></span>

<span data-ttu-id="f9674-270">Hiermee geeft u op hoe vaak Power shell een verbinding probeert te verbreken wanneer een fout code tussen 400 en 599, inclusief of 304 wordt ontvangen.</span><span class="sxs-lookup"><span data-stu-id="f9674-270">Specifies how many times PowerShell retries a connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="f9674-271">Zie ook de para meter **RetryIntervalSec** voor het opgeven van het aantal nieuwe pogingen.</span><span class="sxs-lookup"><span data-stu-id="f9674-271">Also see **RetryIntervalSec** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="f9674-272">-Methode</span><span class="sxs-lookup"><span data-stu-id="f9674-272">-Method</span></span>

<span data-ttu-id="f9674-273">Hiermee geeft u de methode op die voor de webaanvraag wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f9674-273">Specifies the method used for the web request.</span></span> <span data-ttu-id="f9674-274">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="f9674-274">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f9674-275">Standaard</span><span class="sxs-lookup"><span data-stu-id="f9674-275">Default</span></span>
- <span data-ttu-id="f9674-276">Verwijderen</span><span class="sxs-lookup"><span data-stu-id="f9674-276">Delete</span></span>
- <span data-ttu-id="f9674-277">Ophalen</span><span class="sxs-lookup"><span data-stu-id="f9674-277">Get</span></span>
- <span data-ttu-id="f9674-278">Head</span><span class="sxs-lookup"><span data-stu-id="f9674-278">Head</span></span>
- <span data-ttu-id="f9674-279">Samenvoegen</span><span class="sxs-lookup"><span data-stu-id="f9674-279">Merge</span></span>
- <span data-ttu-id="f9674-280">Opties</span><span class="sxs-lookup"><span data-stu-id="f9674-280">Options</span></span>
- <span data-ttu-id="f9674-281">Patch</span><span class="sxs-lookup"><span data-stu-id="f9674-281">Patch</span></span>
- <span data-ttu-id="f9674-282">Plaatsen</span><span class="sxs-lookup"><span data-stu-id="f9674-282">Post</span></span>
- <span data-ttu-id="f9674-283">Put</span><span class="sxs-lookup"><span data-stu-id="f9674-283">Put</span></span>
- <span data-ttu-id="f9674-284">Tracering</span><span class="sxs-lookup"><span data-stu-id="f9674-284">Trace</span></span>

<span data-ttu-id="f9674-285">De para meter **CustomMethod** kan worden gebruikt voor aanvraag methoden die hierboven niet worden vermeld.</span><span class="sxs-lookup"><span data-stu-id="f9674-285">The **CustomMethod** parameter can be used for Request Methods not listed above.</span></span>

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

### <span data-ttu-id="f9674-286">-De proxy</span><span class="sxs-lookup"><span data-stu-id="f9674-286">-NoProxy</span></span>

<span data-ttu-id="f9674-287">Geeft aan dat de cmdlet geen gebruik maakt van een proxy om de bestemming te bereiken.</span><span class="sxs-lookup"><span data-stu-id="f9674-287">Indicates that the cmdlet will not use a proxy to reach the destination.</span></span>

<span data-ttu-id="f9674-288">Als u de geconfigureerde proxy in Internet Explorer wilt overs Laan of een proxy die in de omgeving is opgegeven, gebruikt u deze schakel optie.</span><span class="sxs-lookup"><span data-stu-id="f9674-288">When you need to bypass the proxy configured in Internet Explorer, or a proxy specified in the environment, use this switch.</span></span>

<span data-ttu-id="f9674-289">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="f9674-289">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="f9674-290">-Outfile</span><span class="sxs-lookup"><span data-stu-id="f9674-290">-OutFile</span></span>

<span data-ttu-id="f9674-291">Hiermee wordt de antwoord tekst in het opgegeven uitvoer bestand opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="f9674-291">Saves the response body in the specified output file.</span></span> <span data-ttu-id="f9674-292">Voer een pad en een bestands naam in.</span><span class="sxs-lookup"><span data-stu-id="f9674-292">Enter a path and file name.</span></span> <span data-ttu-id="f9674-293">Als u het pad weglaat, de standaard instelling is de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="f9674-293">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="f9674-294">`Invoke-RestMethod`De resultaten worden standaard naar de pijp lijn geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f9674-294">By default, `Invoke-RestMethod` returns the results to the pipeline.</span></span> <span data-ttu-id="f9674-295">Als u de resultaten naar een bestand en naar de pijp lijn wilt verzenden, gebruikt u de para meter **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="f9674-295">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="f9674-296">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f9674-296">-PassThru</span></span>

<span data-ttu-id="f9674-297">Hiermee worden de resultaten geretourneerd, naast het schrijven naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="f9674-297">Returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="f9674-298">Deze para meter is alleen geldig wanneer de **outfile** -para meter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f9674-298">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No output
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9674-299">-PreserveAuthorizationOnRedirect</span><span class="sxs-lookup"><span data-stu-id="f9674-299">-PreserveAuthorizationOnRedirect</span></span>

<span data-ttu-id="f9674-300">Hiermee wordt aangegeven dat de cmdlet de header moet behouden `Authorization` , indien aanwezig, over de omleidingen.</span><span class="sxs-lookup"><span data-stu-id="f9674-300">Indicates the cmdlet should preserve the `Authorization` header, when present, across redirections.</span></span>

<span data-ttu-id="f9674-301">De-cmdlet verwijdert standaard de `Authorization` header voordat deze wordt omgeleid.</span><span class="sxs-lookup"><span data-stu-id="f9674-301">By default, the cmdlet strips the `Authorization` header before redirecting.</span></span> <span data-ttu-id="f9674-302">Als u deze para meter opgeeft, wordt deze logica uitgeschakeld voor gevallen waarin de header moet worden verzonden naar de omleidings locatie.</span><span class="sxs-lookup"><span data-stu-id="f9674-302">Specifying this parameter disables this logic for cases where the header needs to be sent to the redirection location.</span></span>

<span data-ttu-id="f9674-303">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="f9674-303">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="f9674-304">-Proxy</span><span class="sxs-lookup"><span data-stu-id="f9674-304">-Proxy</span></span>

<span data-ttu-id="f9674-305">Maakt gebruik van een proxy server voor de aanvraag, in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="f9674-305">Uses a proxy server for the request, rather than connecting directly to the internet resource.</span></span> <span data-ttu-id="f9674-306">Geef de URI (Uniform Resource Identifier) van een netwerk proxy server op.</span><span class="sxs-lookup"><span data-stu-id="f9674-306">Enter the Uniform Resource Identifier (URI) of a network proxy server.</span></span>

<span data-ttu-id="f9674-307">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="f9674-307">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="f9674-308">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="f9674-308">-ProxyCredential</span></span>

<span data-ttu-id="f9674-309">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="f9674-309">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="f9674-310">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f9674-310">The default is the current user.</span></span>

<span data-ttu-id="f9674-311">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , **User@Domain.Com** of voer een `PSCredential` object in, bijvoorbeeld het type dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="f9674-311">Type a user name, such as **User01** or **Domain01\User01** , **User@Domain.Com** , or enter a `PSCredential` object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="f9674-312">Deze para meter is alleen geldig wanneer de **proxy** parameter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f9674-312">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="f9674-313">U kunt de para meters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f9674-313">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9674-314">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="f9674-314">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="f9674-315">Geeft aan dat de cmdlet de referenties van de huidige gebruiker gebruikt om toegang te krijgen tot de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="f9674-315">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="f9674-316">Deze para meter is alleen geldig wanneer de **proxy** parameter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f9674-316">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="f9674-317">U kunt de para meters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f9674-317">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="f9674-318">-ResponseHeadersVariable</span><span class="sxs-lookup"><span data-stu-id="f9674-318">-ResponseHeadersVariable</span></span>

<span data-ttu-id="f9674-319">Hiermee maakt u een woorden lijst met antwoord koppen en slaat u deze op in de waarde van de opgegeven variabele.</span><span class="sxs-lookup"><span data-stu-id="f9674-319">Creates a Response Headers Dictionary and saves it in the value of the specified variable.</span></span> <span data-ttu-id="f9674-320">De sleutels van de woorden lijst bevatten de veld namen van de antwoord header die door de webserver wordt geretourneerd en de waarden zijn de respectieve veld waarden.</span><span class="sxs-lookup"><span data-stu-id="f9674-320">The keys of the dictionary will contain the field names of the Response Header returned by the web server and the values will be the respective field values.</span></span>

<span data-ttu-id="f9674-321">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="f9674-321">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: RHV

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9674-322">-Hervatten</span><span class="sxs-lookup"><span data-stu-id="f9674-322">-Resume</span></span>

<span data-ttu-id="f9674-323">Hiermee wordt een beste poging gedaan om het downloaden van een gedeeltelijk bestand te hervatten.</span><span class="sxs-lookup"><span data-stu-id="f9674-323">Performs a best effort attempt to resume downloading a partial file.</span></span> <span data-ttu-id="f9674-324">De para meter **Resume** vereist de **outfile** -para meter.</span><span class="sxs-lookup"><span data-stu-id="f9674-324">The **Resume** parameter requires the **OutFile** parameter.</span></span>

<span data-ttu-id="f9674-325">**Resume** werkt alleen op de grootte van het lokale bestand en het externe bestand en voert geen andere validatie uit dat het lokale bestand en het externe bestand hetzelfde zijn.</span><span class="sxs-lookup"><span data-stu-id="f9674-325">**Resume** only operates on the size of the local file and remote file and performs no other validation that the local file and the remote file are the same.</span></span>

<span data-ttu-id="f9674-326">Als de lokale bestands grootte kleiner is dan de grootte van het externe bestand, probeert de cmdlet het downloaden van het bestand te hervatten en de resterende bytes toe te voegen aan het einde van het bestand.</span><span class="sxs-lookup"><span data-stu-id="f9674-326">If the local file size is smaller than the remote file size, then the cmdlet will attempt to resume downloading the file and append the remaining bytes to the end of the file.</span></span>

<span data-ttu-id="f9674-327">Als de grootte van het lokale bestand hetzelfde is als de grootte van het externe bestand, wordt er geen actie ondernomen en wordt ervan uitgegaan dat de down load al is voltooid.</span><span class="sxs-lookup"><span data-stu-id="f9674-327">If the local file size is the same as the remote file size, then no action is taken and the cmdlet assumes the download already completed.</span></span>

<span data-ttu-id="f9674-328">Als de grootte van het lokale bestand groter is dan de grootte van het externe bestand, wordt het lokale bestand overschreven en wordt het hele externe bestand volledig opnieuw gedownload.</span><span class="sxs-lookup"><span data-stu-id="f9674-328">If the local file size is larger than the remote file size, then the local file will be overwritten and the entire remote file will be completely re-downloaded.</span></span> <span data-ttu-id="f9674-329">Dit gedrag is hetzelfde als het gebruik van een **bestand** zonder de bewerking te **hervatten**.</span><span class="sxs-lookup"><span data-stu-id="f9674-329">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="f9674-330">Als de externe server downloaden niet kan hervatten, wordt het lokale bestand overschreven en wordt het hele externe bestand volledig opnieuw gedownload.</span><span class="sxs-lookup"><span data-stu-id="f9674-330">If the remote server does not support download resuming, then the local file will be overwritten and the entire remote file will be completely re-downloaded.</span></span> <span data-ttu-id="f9674-331">Dit gedrag is hetzelfde als het gebruik van een **bestand** zonder de bewerking te **hervatten**.</span><span class="sxs-lookup"><span data-stu-id="f9674-331">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="f9674-332">Als het lokale bestand niet bestaat, wordt het lokale bestand gemaakt en wordt het hele externe bestand volledig gedownload.</span><span class="sxs-lookup"><span data-stu-id="f9674-332">If the local file doesn't exist, then the local file will be created and the entire remote file will be completely downloaded.</span></span> <span data-ttu-id="f9674-333">Dit gedrag is hetzelfde als het gebruik van een **bestand** zonder de bewerking te **hervatten**.</span><span class="sxs-lookup"><span data-stu-id="f9674-333">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="f9674-334">Deze functie is toegevoegd aan Power shell 6.1.0.</span><span class="sxs-lookup"><span data-stu-id="f9674-334">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="f9674-335">-RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="f9674-335">-RetryIntervalSec</span></span>

<span data-ttu-id="f9674-336">Hiermee geeft u het interval tussen nieuwe pogingen voor de verbinding op wanneer er een fout code tussen 400 en 599, inclusief of 304 wordt ontvangen.</span><span class="sxs-lookup"><span data-stu-id="f9674-336">Specifies the interval between retries for the connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="f9674-337">Zie ook de para meter **MaximumRetryCount** voor het opgeven van het aantal nieuwe pogingen.</span><span class="sxs-lookup"><span data-stu-id="f9674-337">Also see **MaximumRetryCount** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="f9674-338">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="f9674-338">-SessionVariable</span></span>

<span data-ttu-id="f9674-339">Hiermee geeft u een variabele op waarvoor deze cmdlet een sessie voor een webaanvraag maakt en opslaat in de waarde.</span><span class="sxs-lookup"><span data-stu-id="f9674-339">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="f9674-340">Geef een naam op voor de variabele zonder het dollar teken ( `$` )-symbool.</span><span class="sxs-lookup"><span data-stu-id="f9674-340">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="f9674-341">Wanneer u een sessie variabele opgeeft, `Invoke-RestMethod` maakt een webaanvraag sessie object en wijst deze toe aan een variabele met de opgegeven naam in uw Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="f9674-341">When you specify a session variable, `Invoke-RestMethod` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="f9674-342">U kunt de variabele in uw sessie gebruiken zodra de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="f9674-342">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="f9674-343">In tegens telling tot een externe sessie is de sessie van de webaanvraag geen permanente verbinding.</span><span class="sxs-lookup"><span data-stu-id="f9674-343">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="f9674-344">Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximum omleidings waarde en de teken reeks van de gebruikers agent.</span><span class="sxs-lookup"><span data-stu-id="f9674-344">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="f9674-345">U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="f9674-345">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="f9674-346">Als u de webaanvraag sessie in volgende webaanvragen wilt gebruiken, geeft u de sessie variabele op in de waarde van de para meter **websessie** .</span><span class="sxs-lookup"><span data-stu-id="f9674-346">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="f9674-347">Power shell gebruikt de gegevens in het sessie object voor webaanvragen bij het tot stand brengen van de nieuwe verbinding.</span><span class="sxs-lookup"><span data-stu-id="f9674-347">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="f9674-348">Als u een waarde in de sessie voor webaanvragen wilt overschrijven, gebruikt u een cmdlet-para meter, zoals **User agent** of **Credential**.</span><span class="sxs-lookup"><span data-stu-id="f9674-348">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="f9674-349">Parameter waarden hebben prioriteit boven waarden in de webaanvraag sessie.</span><span class="sxs-lookup"><span data-stu-id="f9674-349">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="f9674-350">U kunt de para meters **SessionVariable** en **websession** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="f9674-350">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="f9674-351">-SkipCertificateCheck</span><span class="sxs-lookup"><span data-stu-id="f9674-351">-SkipCertificateCheck</span></span>

<span data-ttu-id="f9674-352">Hiermee worden controles van certificaat validaties overgeslagen die alle validaties bevatten, zoals verval datum, intrekking, vertrouwde basis instantie, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="f9674-352">Skips certificate validation checks that include all validations such as expiration, revocation, trusted root authority, etc.</span></span>

> [!WARNING]
> <span data-ttu-id="f9674-353">Het gebruik van deze para meter is niet beveiligd en wordt niet aanbevolen.</span><span class="sxs-lookup"><span data-stu-id="f9674-353">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="f9674-354">Deze schakel optie is alleen bedoeld om te worden gebruikt voor bekende hosts met behulp van een zelfondertekend certificaat voor test doeleinden.</span><span class="sxs-lookup"><span data-stu-id="f9674-354">This switch is only intended to be used against known hosts using a self-signed certificate for testing purposes.</span></span> <span data-ttu-id="f9674-355">Gebruiken op eigen risico.</span><span class="sxs-lookup"><span data-stu-id="f9674-355">Use at your own risk.</span></span>

<span data-ttu-id="f9674-356">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="f9674-356">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="f9674-357">-SkipHeaderValidation</span><span class="sxs-lookup"><span data-stu-id="f9674-357">-SkipHeaderValidation</span></span>

<span data-ttu-id="f9674-358">Hiermee wordt aangegeven dat de cmdlet headers zonder validatie moet toevoegen aan de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="f9674-358">Indicates the cmdlet should add headers to the request without validation.</span></span>

<span data-ttu-id="f9674-359">Deze schakel optie moet worden gebruikt voor sites waarvoor header waarden zijn vereist die niet voldoen aan de standaarden.</span><span class="sxs-lookup"><span data-stu-id="f9674-359">This switch should be used for sites that require header values that do not conform to standards.</span></span>
<span data-ttu-id="f9674-360">Als u deze switch opgeeft, wordt de validatie uitgeschakeld zodat de waarde die wordt door gegeven, niet kan worden gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="f9674-360">Specifying this switch disables validation to allow the value to be passed unchecked.</span></span> <span data-ttu-id="f9674-361">Als u deze opgeeft, worden alle headers zonder validatie toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="f9674-361">When specified, all headers are added without validation.</span></span>

<span data-ttu-id="f9674-362">Hiermee wordt de validatie uitgeschakeld voor waarden die zijn door gegeven aan de para meters **Content type** , **headers** en **User agent** .</span><span class="sxs-lookup"><span data-stu-id="f9674-362">This will disable validation for values passed to the **ContentType** , **Headers** , and **UserAgent** parameters.</span></span>

<span data-ttu-id="f9674-363">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="f9674-363">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="f9674-364">-SkipHttpErrorCheck</span><span class="sxs-lookup"><span data-stu-id="f9674-364">-SkipHttpErrorCheck</span></span>

<span data-ttu-id="f9674-365">Deze para meter zorgt ervoor dat de cmdlet HTTP-fout statussen negeert en de antwoorden blijft verwerken.</span><span class="sxs-lookup"><span data-stu-id="f9674-365">This parameter causes the cmdlet to ignore HTTP error statuses and continue to process responses.</span></span>
<span data-ttu-id="f9674-366">De fout reacties worden naar de pijp lijn geschreven alsof ze zijn geslaagd.</span><span class="sxs-lookup"><span data-stu-id="f9674-366">The error responses are written to the pipeline just as if they were successful.</span></span>

<span data-ttu-id="f9674-367">Deze para meter is geïntroduceerd in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="f9674-367">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="f9674-368">-SslProtocol</span><span class="sxs-lookup"><span data-stu-id="f9674-368">-SslProtocol</span></span>

<span data-ttu-id="f9674-369">Hiermee stelt u de SSL/TLS-protocollen die zijn toegestaan voor de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="f9674-369">Sets the SSL/TLS protocols that are permissible for the web request.</span></span> <span data-ttu-id="f9674-370">Standaard zijn alle SSL/TLS-protocollen die door het systeem worden ondersteund, toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f9674-370">By default all, SSL/TLS protocols supported by the system are allowed.</span></span> <span data-ttu-id="f9674-371">Met **SslProtocol** wordt het beperken van specifieke protocollen voor nalevings doeleinden toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f9674-371">**SslProtocol** allows for limiting to specific protocols for compliance purposes.</span></span>

<span data-ttu-id="f9674-372">**SslProtocol** maakt gebruik van de `WebSslProtocol` Flag-opsomming.</span><span class="sxs-lookup"><span data-stu-id="f9674-372">**SslProtocol** uses the `WebSslProtocol` Flag Enum.</span></span> <span data-ttu-id="f9674-373">Het is mogelijk om meer dan één protocol aan te bieden met behulp van de vlag notatie of meerdere opties combi neren `WebSslProtocol` met `-bor` , maar het leveren van meerdere protocollen wordt niet op alle platforms ondersteund.</span><span class="sxs-lookup"><span data-stu-id="f9674-373">It is possible to supply more than one protocol using flag notation or combining multiple `WebSslProtocol` options with `-bor`, however supplying multiple protocols is not supported on all platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="f9674-374">Op niet-Windows-platforms is het niet mogelijk om `'Tls, Tls12'` als optie te leveren.</span><span class="sxs-lookup"><span data-stu-id="f9674-374">On non-Windows platforms it may not be possible to supply `'Tls, Tls12'` as an option.</span></span>

<span data-ttu-id="f9674-375">Deze functie is toegevoegd aan Power shell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="f9674-375">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="f9674-376">-StatusCodeVariable</span><span class="sxs-lookup"><span data-stu-id="f9674-376">-StatusCodeVariable</span></span>

<span data-ttu-id="f9674-377">Met deze para meter geeft u een variabele op waaraan de waarde van het gehele getal van de status code is toegewezen.</span><span class="sxs-lookup"><span data-stu-id="f9674-377">This parameter specifies a variable that's assigned a status code's integer value.</span></span> <span data-ttu-id="f9674-378">Met de para meter kunnen succes berichten of fout berichten worden geïdentificeerd wanneer deze worden gebruikt in combi natie met de para meter **SkipHttpErrorCheck** .</span><span class="sxs-lookup"><span data-stu-id="f9674-378">The parameter can identify success messages or failure messages when used with the **SkipHttpErrorCheck** parameter.</span></span>

<span data-ttu-id="f9674-379">Voer de variabele naam van de para meter in als een teken reeks zoals `-StatusCodeVariable "scv"` .</span><span class="sxs-lookup"><span data-stu-id="f9674-379">Input the parameter's variable name as a string such as `-StatusCodeVariable "scv"`.</span></span>

<span data-ttu-id="f9674-380">Deze para meter is geïntroduceerd in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="f9674-380">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9674-381">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="f9674-381">-TimeoutSec</span></span>

<span data-ttu-id="f9674-382">Hiermee geeft u op hoe lang de aanvraag in behandeling kan zijn voordat er een time-out optreedt. Voer een waarde in seconden in.</span><span class="sxs-lookup"><span data-stu-id="f9674-382">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="f9674-383">De standaard waarde, 0, geeft een onbeperkte time-outwaarde.</span><span class="sxs-lookup"><span data-stu-id="f9674-383">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="f9674-384">Het kan tot vijf tien seconden duren voordat een Domain Name System query (DNS) wordt uitgevoerd of een time-out kan worden geretourneerd. Als uw aanvraag een hostnaam bevat waarvoor omzetting vereist is en u **TimeoutSec** instelt op een waarde die groter is dan nul, maar minder dan 15 seconden, kan het vijf tien seconden of langer duren voordat een webuitzondering wordt gegenereerd en er een time-out optreedt voor uw aanvraag.</span><span class="sxs-lookup"><span data-stu-id="f9674-384">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="f9674-385">-Token</span><span class="sxs-lookup"><span data-stu-id="f9674-385">-Token</span></span>

<span data-ttu-id="f9674-386">Het OAuth-of Bearer-token dat in de aanvraag moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="f9674-386">The OAuth or Bearer token to include in the request.</span></span> <span data-ttu-id="f9674-387">Het **token** is vereist voor bepaalde **verificatie** opties.</span><span class="sxs-lookup"><span data-stu-id="f9674-387">**Token** is required by certain **Authentication** options.</span></span> <span data-ttu-id="f9674-388">Deze kan niet onafhankelijk worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f9674-388">It can't be used independently.</span></span>

<span data-ttu-id="f9674-389">**Token** neemt een `SecureString` met het token.</span><span class="sxs-lookup"><span data-stu-id="f9674-389">**Token** takes a `SecureString` that contains the token.</span></span> <span data-ttu-id="f9674-390">Als u het token wilt opgeven, gebruikt u hand matig het volgende:</span><span class="sxs-lookup"><span data-stu-id="f9674-390">To supply the token, manually use the following:</span></span>

`Invoke-RestMethod -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

<span data-ttu-id="f9674-391">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="f9674-391">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="f9674-392">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="f9674-392">-TransferEncoding</span></span>

<span data-ttu-id="f9674-393">Hiermee geeft u een waarde op voor de header van de HTTP-reactie voor overdracht/versleuteling.</span><span class="sxs-lookup"><span data-stu-id="f9674-393">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="f9674-394">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="f9674-394">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f9674-395">Gesegmenteerde</span><span class="sxs-lookup"><span data-stu-id="f9674-395">Chunked</span></span>
- <span data-ttu-id="f9674-396">Comprimeren</span><span class="sxs-lookup"><span data-stu-id="f9674-396">Compress</span></span>
- <span data-ttu-id="f9674-397">Deflate</span><span class="sxs-lookup"><span data-stu-id="f9674-397">Deflate</span></span>
- <span data-ttu-id="f9674-398">GZip</span><span class="sxs-lookup"><span data-stu-id="f9674-398">GZip</span></span>
- <span data-ttu-id="f9674-399">Identiteit</span><span class="sxs-lookup"><span data-stu-id="f9674-399">Identity</span></span>

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

### <span data-ttu-id="f9674-400">-URI</span><span class="sxs-lookup"><span data-stu-id="f9674-400">-Uri</span></span>

<span data-ttu-id="f9674-401">Hiermee geeft u de URI (Uniform Resource Identifier) op van de Internet bron waarnaar de webaanvraag wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="f9674-401">Specifies the Uniform Resource Identifier (URI) of the internet resource to which the web request is sent.</span></span> <span data-ttu-id="f9674-402">Deze para meter ondersteunt HTTP-, HTTPS-, FTP-en FILE-waarden.</span><span class="sxs-lookup"><span data-stu-id="f9674-402">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="f9674-403">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="f9674-403">This parameter is required.</span></span> <span data-ttu-id="f9674-404">De parameter naam ( **URI** ) is optioneel.</span><span class="sxs-lookup"><span data-stu-id="f9674-404">The parameter name ( **Uri** ) is optional.</span></span>

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

### <span data-ttu-id="f9674-405">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="f9674-405">-UseBasicParsing</span></span>

<span data-ttu-id="f9674-406">Deze para meter is afgeschaft.</span><span class="sxs-lookup"><span data-stu-id="f9674-406">This parameter has been deprecated.</span></span> <span data-ttu-id="f9674-407">Vanaf Power shell 6.0.0 gebruiken alle webaanvragen alleen basis parsering.</span><span class="sxs-lookup"><span data-stu-id="f9674-407">Beginning with PowerShell 6.0.0, all Web requests use basic parsing only.</span></span> <span data-ttu-id="f9674-408">Deze para meter is alleen opgenomen voor achterwaartse compatibiliteit en het gebruik ervan heeft geen invloed op de werking van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9674-408">This parameter is included for backwards compatibility only and any use of it will have no effect on the operation of the cmdlet.</span></span>

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

### <span data-ttu-id="f9674-409">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="f9674-409">-UseDefaultCredentials</span></span>

<span data-ttu-id="f9674-410">Geeft aan dat de cmdlet de referenties van de huidige gebruiker gebruikt om de webaanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="f9674-410">Indicates that the cmdlet uses the credentials of the current user to send the web request.</span></span> <span data-ttu-id="f9674-411">Deze kan niet worden gebruikt met **verificatie** of **referentie** en wordt mogelijk niet ondersteund op alle platforms.</span><span class="sxs-lookup"><span data-stu-id="f9674-411">This can't be used with **Authentication** or **Credential** and may not be supported on all platforms.</span></span>

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

### <span data-ttu-id="f9674-412">-User agent</span><span class="sxs-lookup"><span data-stu-id="f9674-412">-UserAgent</span></span>

<span data-ttu-id="f9674-413">Hiermee geeft u een teken reeks voor de gebruikers agent op voor de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="f9674-413">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="f9674-414">De standaard gebruikers agent is vergelijkbaar `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` met kleine variaties voor elk besturings systeem en platform.</span><span class="sxs-lookup"><span data-stu-id="f9674-414">The default user agent is similar to `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="f9674-415">Als u een website wilt testen met de standaard teken reeks van de gebruikers agent die wordt gebruikt door de meeste Internet browsers, gebruikt u de eigenschappen van de [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) -klasse, zoals Chrome, Firefox, InternetExplorer, Opera en Safari.</span><span class="sxs-lookup"><span data-stu-id="f9674-415">To test a website with the standard user agent string that is used by most internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span>

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

### <span data-ttu-id="f9674-416">-Websessie</span><span class="sxs-lookup"><span data-stu-id="f9674-416">-WebSession</span></span>

<span data-ttu-id="f9674-417">Hiermee geeft u een sessie voor webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="f9674-417">Specifies a web request session.</span></span> <span data-ttu-id="f9674-418">Voer de naam van de variabele in, met inbegrip van het dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="f9674-418">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="f9674-419">Als u een waarde in de sessie voor webaanvragen wilt overschrijven, gebruikt u een cmdlet-para meter, zoals **User agent** of **Credential**.</span><span class="sxs-lookup"><span data-stu-id="f9674-419">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="f9674-420">Parameter waarden hebben prioriteit boven waarden in de webaanvraag sessie.</span><span class="sxs-lookup"><span data-stu-id="f9674-420">Parameter values take precedence over values in the web request session.</span></span> <span data-ttu-id="f9674-421">Inhouds gerelateerde kopteksten, zoals `Content-Type` , worden ook genegeerd wanneer een **MultipartFormDataContent** -object wordt opgegeven voor de **hoofd tekst**.</span><span class="sxs-lookup"><span data-stu-id="f9674-421">Content related headers, such as `Content-Type`, will be also be overridden when a **MultipartFormDataContent** object is supplied for **Body**.</span></span>

<span data-ttu-id="f9674-422">In tegens telling tot een externe sessie is de sessie van de webaanvraag geen permanente verbinding.</span><span class="sxs-lookup"><span data-stu-id="f9674-422">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="f9674-423">Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximum omleidings waarde en de teken reeks van de gebruikers agent.</span><span class="sxs-lookup"><span data-stu-id="f9674-423">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="f9674-424">U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="f9674-424">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="f9674-425">Als u een webonderdeelverzoek wilt maken, voert u de naam van een variabele zonder een dollar teken in de waarde van de para meter **SessionVariable** van een `Invoke-RestMethod` opdracht in.</span><span class="sxs-lookup"><span data-stu-id="f9674-425">To create a web request session, enter a variable name, without a dollar sign, in the value of the **SessionVariable** parameter of an `Invoke-RestMethod` command.</span></span> <span data-ttu-id="f9674-426">`Invoke-RestMethod` Hiermee maakt u de sessie en slaat u deze op in de variabele.</span><span class="sxs-lookup"><span data-stu-id="f9674-426">`Invoke-RestMethod` creates the session and saves it in the variable.</span></span> <span data-ttu-id="f9674-427">Gebruik in volgende opdrachten de variabele als de waarde van de para meter **websession** .</span><span class="sxs-lookup"><span data-stu-id="f9674-427">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="f9674-428">U kunt de para meters **SessionVariable** en **websession** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="f9674-428">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="f9674-429">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f9674-429">CommonParameters</span></span>

<span data-ttu-id="f9674-430">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f9674-430">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f9674-431">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f9674-431">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f9674-432">INVOER</span><span class="sxs-lookup"><span data-stu-id="f9674-432">INPUTS</span></span>

### <span data-ttu-id="f9674-433">System. object</span><span class="sxs-lookup"><span data-stu-id="f9674-433">System.Object</span></span>

<span data-ttu-id="f9674-434">U kunt de hoofd tekst van een webaanvraag door sluizen naar `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="f9674-434">You can pipe the body of a web request to `Invoke-RestMethod`.</span></span>

## <span data-ttu-id="f9674-435">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f9674-435">OUTPUTS</span></span>

### <span data-ttu-id="f9674-436">Systeem. Int64, System. String, System.Xml.Xmldocument</span><span class="sxs-lookup"><span data-stu-id="f9674-436">System.Int64, System.String, System.Xml.XmlDocument</span></span>

<span data-ttu-id="f9674-437">De uitvoer van de cmdlet is afhankelijk van de indeling van de inhoud die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f9674-437">The output of the cmdlet depends upon the format of the content that is retrieved.</span></span>

### <span data-ttu-id="f9674-438">PSObject</span><span class="sxs-lookup"><span data-stu-id="f9674-438">PSObject</span></span>

<span data-ttu-id="f9674-439">Als de aanvraag JSON-teken reeksen retourneert, `Invoke-RestMethod` retourneert een **PSObject** die de teken reeksen vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f9674-439">If the request returns JSON strings, `Invoke-RestMethod` returns a **PSObject** that represents the strings.</span></span>

## <span data-ttu-id="f9674-440">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f9674-440">NOTES</span></span>

<span data-ttu-id="f9674-441">Sommige functies zijn mogelijk niet beschikbaar op alle platforms.</span><span class="sxs-lookup"><span data-stu-id="f9674-441">Some features may not be available on all platforms.</span></span>

<span data-ttu-id="f9674-442">Vanwege wijzigingen in .NET Core 3,1, Power shell 7,0 en hoger, gebruikt u de eigenschap [httpclient maakt. DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) om de proxy configuratie te bepalen.</span><span class="sxs-lookup"><span data-stu-id="f9674-442">Because of changes in .NET Core 3.1, PowerShell 7.0 and higher use the [HttpClient.DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) property to determine the proxy configuration.</span></span>

<span data-ttu-id="f9674-443">De waarde van deze eigenschap wordt bepaald door uw platform:</span><span class="sxs-lookup"><span data-stu-id="f9674-443">The value of this property is determined by your platform:</span></span>

- <span data-ttu-id="f9674-444">**Voor Windows** : Hiermee leest u de proxy configuratie van omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="f9674-444">**For Windows** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="f9674-445">Als deze variabelen niet worden gedefinieerd, wordt de eigenschap afgeleid van de proxy-instellingen van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f9674-445">If those variables are not defined the property is derived from the user's proxy settings.</span></span>
- <span data-ttu-id="f9674-446">**Voor macOS** : leest de proxy configuratie van omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="f9674-446">**For macOS** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="f9674-447">Als deze variabelen niet worden gedefinieerd, wordt de eigenschap afgeleid van de proxy-instellingen van het systeem.</span><span class="sxs-lookup"><span data-stu-id="f9674-447">If those variables are not defined the property is derived from the system's proxy settings.</span></span>
- <span data-ttu-id="f9674-448">**Voor Linux** : Hiermee leest u de proxy configuratie van omgevings variabelen.</span><span class="sxs-lookup"><span data-stu-id="f9674-448">**For Linux** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="f9674-449">Als deze variabelen niet zijn gedefinieerd, initialiseert de eigenschap een niet-geconfigureerd exemplaar dat alle adressen omzeilt.</span><span class="sxs-lookup"><span data-stu-id="f9674-449">If those variables are not defined the property initializes a non-configured instance that bypasses all addresses.</span></span>

<span data-ttu-id="f9674-450">De omgevings variabelen die worden gebruikt voor de `DefaultProxy` initialisatie op Windows-en UNIX-platforms zijn:</span><span class="sxs-lookup"><span data-stu-id="f9674-450">The environment variables used for `DefaultProxy` initialization on Windows and Unix-based platforms are:</span></span>

- <span data-ttu-id="f9674-451">` HTTP_PROXY`: de hostnaam of het IP-adres van de proxy server die wordt gebruikt voor HTTP-aanvragen.</span><span class="sxs-lookup"><span data-stu-id="f9674-451">` HTTP_PROXY`: the hostname or IP address of the proxy server used on HTTP requests.</span></span>
- <span data-ttu-id="f9674-452">`HTTPS_PROXY`: de hostnaam of het IP-adres van de proxy server die wordt gebruikt voor HTTPS-aanvragen.</span><span class="sxs-lookup"><span data-stu-id="f9674-452">`HTTPS_PROXY`: the hostname or IP address of the proxy server used on HTTPS requests.</span></span>
- <span data-ttu-id="f9674-453">`ALL_PROXY`: de hostnaam of het IP-adres van de proxy server die wordt gebruikt voor HTTP-en HTTPS-aanvragen `HTTP_PROXY` of `HTTPS_PROXY` die niet zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="f9674-453">`ALL_PROXY`: the hostname or IP address of the proxy server used on HTTP and HTTPS requests in case `HTTP_PROXY` or `HTTPS_PROXY` are not defined.</span></span>
- <span data-ttu-id="f9674-454">`NO_PROXY`: een door komma's gescheiden lijst met hostnamen die moeten worden uitgesloten van de proxy.</span><span class="sxs-lookup"><span data-stu-id="f9674-454">`NO_PROXY`: a comma-separated list of hostnames that should be excluded from proxying.</span></span>

## <span data-ttu-id="f9674-455">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f9674-455">RELATED LINKS</span></span>

[<span data-ttu-id="f9674-456">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="f9674-456">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="f9674-457">ConvertFrom-JSON</span><span class="sxs-lookup"><span data-stu-id="f9674-457">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="f9674-458">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="f9674-458">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)
