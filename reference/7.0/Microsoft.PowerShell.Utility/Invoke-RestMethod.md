---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/20/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-RestMethod
ms.openlocfilehash: bba455397736357e3f2a8ac22fe6622c79fe36b8
ms.sourcegitcommit: b10731301412afd4111743b85da95e8c25583533
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/20/2021
ms.locfileid: "107756257"
---
# <span data-ttu-id="9d558-102">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="9d558-102">Invoke-RestMethod</span></span>

## <span data-ttu-id="9d558-103">Synopsis</span><span class="sxs-lookup"><span data-stu-id="9d558-103">Synopsis</span></span>
<span data-ttu-id="9d558-104">Verzendt een HTTP- of HTTPS-aanvraag naar een RESTful-webservice.</span><span class="sxs-lookup"><span data-stu-id="9d558-104">Sends an HTTP or HTTPS request to a RESTful web service.</span></span>

## <span data-ttu-id="9d558-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9d558-105">Syntax</span></span>

### <span data-ttu-id="9d558-106">StandardMethod (standaard)</span><span class="sxs-lookup"><span data-stu-id="9d558-106">StandardMethod (Default)</span></span>

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

### <span data-ttu-id="9d558-107">StandardMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="9d558-107">StandardMethodNoProxy</span></span>

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

### <span data-ttu-id="9d558-108">CustomMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="9d558-108">CustomMethodNoProxy</span></span>

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

### <span data-ttu-id="9d558-109">CustomMethod</span><span class="sxs-lookup"><span data-stu-id="9d558-109">CustomMethod</span></span>

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

## <span data-ttu-id="9d558-110">Description</span><span class="sxs-lookup"><span data-stu-id="9d558-110">Description</span></span>

<span data-ttu-id="9d558-111">De `Invoke-RestMethod` cmdlet verzendt HTTP- en HTTPS-aanvragen naar Representational State Transfer (REST)-webservices die rijke gestructureerde gegevens retourneren.</span><span class="sxs-lookup"><span data-stu-id="9d558-111">The `Invoke-RestMethod` cmdlet sends HTTP and HTTPS requests to Representational State Transfer (REST) web services that return richly structured data.</span></span>

<span data-ttu-id="9d558-112">PowerShell formatteert het antwoord op basis van het gegevenstype.</span><span class="sxs-lookup"><span data-stu-id="9d558-112">PowerShell formats the response based to the data type.</span></span> <span data-ttu-id="9d558-113">Voor een RSS- of ATOM-feed retourneert PowerShell de XML-knooppunten Item of Entry.</span><span class="sxs-lookup"><span data-stu-id="9d558-113">For an RSS or ATOM feed, PowerShell returns the Item or Entry XML nodes.</span></span> <span data-ttu-id="9d558-114">Voor JavaScript Object Notation (JSON) of XML converteert of deserialiseert PowerShell de inhoud naar `[PSCustomObject]` objecten.</span><span class="sxs-lookup"><span data-stu-id="9d558-114">For JavaScript Object Notation (JSON) or XML, PowerShell converts, or deserializes, the content into `[PSCustomObject]` objects.</span></span>

> [!NOTE]
> <span data-ttu-id="9d558-115">Wanneer het REST-eindpunt meerdere objecten retourneert, worden de objecten ontvangen als een matrix.</span><span class="sxs-lookup"><span data-stu-id="9d558-115">When the REST endpoint returns multiple objects, the objects are received as an array.</span></span> <span data-ttu-id="9d558-116">Als u de uitvoer doorspijpt `Invoke-RestMethod` van naar een andere opdracht, wordt deze als één object `[Object[]]` verzonden.</span><span class="sxs-lookup"><span data-stu-id="9d558-116">If you pipe the output from `Invoke-RestMethod` to another command, it is sent as a single `[Object[]]` object.</span></span> <span data-ttu-id="9d558-117">De inhoud van die matrix wordt niet geïndefeerd voor de volgende opdracht in de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="9d558-117">The contents of that array are not enumerated for the next command on the pipeline.</span></span>

<span data-ttu-id="9d558-118">Deze cmdlet is geïntroduceerd in Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="9d558-118">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="9d558-119">Vanaf PowerShell 7.0 ondersteunt proxyconfiguratie gedefinieerd `Invoke-RestMethod` door omgevingsvariabelen.</span><span class="sxs-lookup"><span data-stu-id="9d558-119">Beginning in PowerShell 7.0, `Invoke-RestMethod` supports proxy configuration defined by environment variables.</span></span> <span data-ttu-id="9d558-120">Zie de [sectie Opmerkingen](#notes) van dit artikel.</span><span class="sxs-lookup"><span data-stu-id="9d558-120">See the [Notes](#notes) section of this article.</span></span>

## <span data-ttu-id="9d558-121">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="9d558-121">Examples</span></span>

### <span data-ttu-id="9d558-122">Voorbeeld 1: de PowerShell RSS-feed op halen</span><span class="sxs-lookup"><span data-stu-id="9d558-122">Example 1: Get the PowerShell RSS feed</span></span>

<span data-ttu-id="9d558-123">In dit voorbeeld wordt de `Invoke-RestMethod` cmdlet gebruikt om informatie op te halen uit de RSS-feed van het PowerShell-blog.</span><span class="sxs-lookup"><span data-stu-id="9d558-123">This example uses the `Invoke-RestMethod` cmdlet to get information from the PowerShell Blog RSS feed.</span></span> <span data-ttu-id="9d558-124">De opdracht gebruikt de cmdlet om de waarden van de eigenschappen Titel en `Format-Table` **pubDate** van elke  blog in een tabel weer te geven.</span><span class="sxs-lookup"><span data-stu-id="9d558-124">The command uses the `Format-Table` cmdlet to display the values of the **Title** and **pubDate** properties of each blog in a table.</span></span>

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

### <span data-ttu-id="9d558-125">Voorbeeld 2: Een POST-aanvraag uitvoeren</span><span class="sxs-lookup"><span data-stu-id="9d558-125">Example 2: Run a POST request</span></span>

<span data-ttu-id="9d558-126">In dit voorbeeld voert een gebruiker uit om `Invoke-RestMethod` een POST-aanvraag uit te doen op een intranetwebsite in de organisatie van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="9d558-126">In this example, a user runs `Invoke-RestMethod` to do a POST request on an intranet website in the user's organization.</span></span>

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

<span data-ttu-id="9d558-127">De referenties worden gevraagd en vervolgens opgeslagen in en de `$Cred` URL die wordt gebruikt, wordt gedefinieerd in `$Url` .</span><span class="sxs-lookup"><span data-stu-id="9d558-127">The credentials are prompted for and then stored in `$Cred` and the URL that will be access is defined in `$Url`.</span></span>

<span data-ttu-id="9d558-128">De variabele beschrijft de zoekcriteria, geeft CSV op als uitvoermodus en geeft een tijdsperiode op voor geretourneerde gegevens die twee dagen geleden begint en één dag `$Body` geleden eindigt.</span><span class="sxs-lookup"><span data-stu-id="9d558-128">The `$Body` variable describes the search criteria, specifies CSV as the output mode, and specifies a time period for returned data that starts two days ago and ends one day ago.</span></span> <span data-ttu-id="9d558-129">De variabele body geeft waarden op voor parameters die van toepassing zijn op de REST API waarmee `Invoke-RestMethod` wordt gecommuniceerd.</span><span class="sxs-lookup"><span data-stu-id="9d558-129">The body variable specifies values for parameters that apply to the particular REST API with which `Invoke-RestMethod` is communicating.</span></span>

<span data-ttu-id="9d558-130">De opdracht wordt uitgevoerd met alle variabelen op de plaats, waarbij een pad en bestandsnaam voor het resulterende `Invoke-RestMethod` CSV-uitvoerbestand worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9d558-130">The `Invoke-RestMethod` command is run with all variables in place, specifying a path and file name for the resulting CSV output file.</span></span>

### <span data-ttu-id="9d558-131">Voorbeeld 3: Koppelingen voor relaties volgen</span><span class="sxs-lookup"><span data-stu-id="9d558-131">Example 3: Follow relation links</span></span>

<span data-ttu-id="9d558-132">Sommige REST API's ondersteunen paginering via Relation Links per [RFC5988.](https://tools.ietf.org/html/rfc5988#page-6)</span><span class="sxs-lookup"><span data-stu-id="9d558-132">Some REST APIs support pagination via Relation Links per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span></span> <span data-ttu-id="9d558-133">In plaats van de header te parseren om de URL voor de volgende pagina op te halen, kunt u de cmdlet dit voor u laten doen.</span><span class="sxs-lookup"><span data-stu-id="9d558-133">Instead of parsing the header to get the URL for the next page, you can have the cmdlet do this for you.</span></span> <span data-ttu-id="9d558-134">In dit voorbeeld worden de eerste twee pagina's met problemen uit de PowerShell GitHub-opslagplaats weergegeven.</span><span class="sxs-lookup"><span data-stu-id="9d558-134">This example returns the first two pages of issues from the PowerShell GitHub repository.</span></span>

```powershell
$url = 'https://api.github.com/repos/powershell/powershell/issues'
Invoke-RestMethod $url -FollowRelLink -MaximumFollowRelLink 2
```

### <span data-ttu-id="9d558-135">Voorbeeld 4: Vereenvoudigde verzending van meerdere onderdelen/formuliergegevens</span><span class="sxs-lookup"><span data-stu-id="9d558-135">Example 4: Simplified Multipart/Form-Data Submission</span></span>

<span data-ttu-id="9d558-136">Sommige API's vereisen `multipart/form-data` inzendingen om bestanden en gemengde inhoud te uploaden.</span><span class="sxs-lookup"><span data-stu-id="9d558-136">Some APIs require `multipart/form-data` submissions to upload files and mixed content.</span></span> <span data-ttu-id="9d558-137">In dit voorbeeld wordt gedemonstreerd hoe u het profiel van een gebruiker bijwerkt.</span><span class="sxs-lookup"><span data-stu-id="9d558-137">This example demonstrates how to update a user's profile.</span></span>

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

<span data-ttu-id="9d558-138">Voor het profielformulier zijn de volgende `firstName` velden `lastName` vereist: , `email` , , , en `avatar` `birthday` `hobbies` .</span><span class="sxs-lookup"><span data-stu-id="9d558-138">The profile form requires these fields: `firstName`, `lastName`, `email`, `avatar`, `birthday`, and `hobbies`.</span></span> <span data-ttu-id="9d558-139">De API verwacht een afbeelding voor de afbeelding van het gebruikersprofiel die in het veld moet worden `avatar` opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9d558-139">The API is expecting an image for the user profile pic to be supplied in the `avatar` field.</span></span> <span data-ttu-id="9d558-140">De API accepteert ook meerdere `hobbies` vermeldingen die in dezelfde vorm moeten worden ingediend.</span><span class="sxs-lookup"><span data-stu-id="9d558-140">The API will also accept multiple `hobbies` entries to be submitted in the same form.</span></span>

<span data-ttu-id="9d558-141">Bij het maken `$Form` van de hashtabel worden de sleutelnamen gebruikt als formulierveldnamen.</span><span class="sxs-lookup"><span data-stu-id="9d558-141">When creating the `$Form` HashTable, the key names are used as form field names.</span></span> <span data-ttu-id="9d558-142">Standaard worden de waarden van de hashtabel geconverteerd naar tekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="9d558-142">By default, the values of the HashTable will be converted to strings.</span></span> <span data-ttu-id="9d558-143">Als er `System.IO.FileInfo` een waarde aanwezig is, wordt de bestandsinhoud verzonden.</span><span class="sxs-lookup"><span data-stu-id="9d558-143">If a `System.IO.FileInfo` value is present, the file contents will be submitted.</span></span> <span data-ttu-id="9d558-144">Als een verzameling zoals matrices of lijsten aanwezig is, wordt het formulierveld meerdere keren verzonden.</span><span class="sxs-lookup"><span data-stu-id="9d558-144">If a collection such as arrays or lists are present, the form field will be submitted multiple times.</span></span>

<span data-ttu-id="9d558-145">Door op `Get-Item` de `avatar` sleutel te gebruiken, wordt het object `FileInfo` ingesteld als de waarde.</span><span class="sxs-lookup"><span data-stu-id="9d558-145">By using `Get-Item` on the `avatar` key, the `FileInfo` object will be set as the value.</span></span> <span data-ttu-id="9d558-146">Het resultaat is dat de afbeeldingsgegevens `jdoe.png` voor worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="9d558-146">The result is that the image data for `jdoe.png` will be submitted.</span></span>

<span data-ttu-id="9d558-147">Door een lijst op te geven voor de sleutel, is het veld eenmaal `hobbies` `hobbies` aanwezig in de inzendingen voor elk lijstitem.</span><span class="sxs-lookup"><span data-stu-id="9d558-147">By supplying a list to the `hobbies` key, the `hobbies` field will be present in the submissions once for each list item.</span></span>

### <span data-ttu-id="9d558-148">Voorbeeld 5: Meerdere headers doorgeven</span><span class="sxs-lookup"><span data-stu-id="9d558-148">Example 5: Pass multiple headers</span></span>

<span data-ttu-id="9d558-149">API's vereisen vaak doorgegeven headers voor verificatie of validatie.</span><span class="sxs-lookup"><span data-stu-id="9d558-149">APIs often require passed headers for authentication or validation.</span></span> <span data-ttu-id="9d558-150">In dit voorbeeld wordt gedemonstreerd hoe u meerdere headers van een naar `hash-table` een REST API.</span><span class="sxs-lookup"><span data-stu-id="9d558-150">This example demonstrates, how to pass multiple headers from a `hash-table` to a REST API.</span></span>

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

### <span data-ttu-id="9d558-151">Voorbeeld 6: Geretourneerde items in de pijplijn opsnoemen</span><span class="sxs-lookup"><span data-stu-id="9d558-151">Example 6: Enumerate returned items on the pipeline</span></span>

<span data-ttu-id="9d558-152">GitHub retourneert meerdere objecten in een matrix.</span><span class="sxs-lookup"><span data-stu-id="9d558-152">GitHub returns multiple objects an array.</span></span> <span data-ttu-id="9d558-153">Als u de uitvoer doorspijpt naar een andere opdracht, wordt deze als één `[Object[]]` object verzonden.</span><span class="sxs-lookup"><span data-stu-id="9d558-153">If you pipe the output to another command, it is sent as a single `[Object[]]`object.</span></span>

<span data-ttu-id="9d558-154">Als u de objecten in de pijplijn wilt opsnoemen, sleet u de resultaten door naar of verpakt u de `Write-Output` cmdlet tussen haakjes.</span><span class="sxs-lookup"><span data-stu-id="9d558-154">To enumerate the objects into the pipeline, pipe the results to `Write-Output` or wrap the cmdlet in parentheses.</span></span> <span data-ttu-id="9d558-155">In het volgende voorbeeld wordt het aantal objecten geteld dat door GitHub wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="9d558-155">The following example counts the number of objects returned by GitHub.</span></span> <span data-ttu-id="9d558-156">Vervolgens wordt het aantal objecten geteld dat in de pijplijn is opgeteld.</span><span class="sxs-lookup"><span data-stu-id="9d558-156">Then counts the number of objects enumerated to the pipeline.</span></span>

```powershell
$uri = 'https://api.github.com/repos/microsoftdocs/powershell-docs/issues'
$x = 0
Invoke-RestMethod -Uri $uri | ForEach-Object { $x++ }
$x
1

$x = 0
(Invoke-RestMethod -Uri $uri) | ForEach-Object { $x++ }
$x
30

$x = 0
Invoke-RestMethod -Uri $uri | Write-Output | ForEach-Object { $x++ }
$x
30
```

## <span data-ttu-id="9d558-157">Parameters</span><span class="sxs-lookup"><span data-stu-id="9d558-157">Parameters</span></span>

### <span data-ttu-id="9d558-158">-AllowUnencryptedAuthentication</span><span class="sxs-lookup"><span data-stu-id="9d558-158">-AllowUnencryptedAuthentication</span></span>

<span data-ttu-id="9d558-159">Hiermee kunt u referenties en geheimen verzenden via niet-versleutelde verbindingen.</span><span class="sxs-lookup"><span data-stu-id="9d558-159">Allows sending of credentials and secrets over unencrypted connections.</span></span> <span data-ttu-id="9d558-160">Standaard leidt  het verstrekken  van referenties of een verificatieoptie met een **URI** die niet begint met tot een fout en wordt de aanvraag afgebroken om te voorkomen dat geheimen per ongeluk worden gecommuniceerd in tekst zonder e-mail via niet-versleutelde `https://` verbindingen.</span><span class="sxs-lookup"><span data-stu-id="9d558-160">By default, supplying **Credential** or any **Authentication** option with a **Uri** that does not begin with `https://` will result in an error and the request will abort to prevent unintentionally communicating secrets in plain text over unencrypted connections.</span></span> <span data-ttu-id="9d558-161">Als u dit gedrag voor eigen risico wilt overschrijven, geeft u de parameter **AllowUnencryptedAuthentication** op.</span><span class="sxs-lookup"><span data-stu-id="9d558-161">To override this behavior at your own risk, supply the **AllowUnencryptedAuthentication** parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="9d558-162">Het gebruik van deze parameter is niet veilig en wordt niet aanbevolen.</span><span class="sxs-lookup"><span data-stu-id="9d558-162">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="9d558-163">Het wordt alleen verstrekt voor compatibiliteit met oudere systemen die geen versleutelde verbindingen kunnen bieden.</span><span class="sxs-lookup"><span data-stu-id="9d558-163">It is provided only for compatibility with legacy systems that cannot provide encrypted connections.</span></span> <span data-ttu-id="9d558-164">Gebruik dit op uw eigen risico.</span><span class="sxs-lookup"><span data-stu-id="9d558-164">Use at your own risk.</span></span>

<span data-ttu-id="9d558-165">Deze functie is toegevoegd in PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="9d558-165">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="9d558-166">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="9d558-166">-Authentication</span></span>

<span data-ttu-id="9d558-167">Hiermee geeft u het expliciete verificatietype op dat voor de aanvraag moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9d558-167">Specifies the explicit authentication type to use for the request.</span></span> <span data-ttu-id="9d558-168">De standaardwaarde is **None**.</span><span class="sxs-lookup"><span data-stu-id="9d558-168">The default is **None**.</span></span>
<span data-ttu-id="9d558-169">**Verificatie** kan niet worden gebruikt met **UseDefaultCredentials.**</span><span class="sxs-lookup"><span data-stu-id="9d558-169">**Authentication** can't be used with **UseDefaultCredentials**.</span></span>

<span data-ttu-id="9d558-170">Beschikbare verificatieopties:</span><span class="sxs-lookup"><span data-stu-id="9d558-170">Available Authentication Options:</span></span>

- <span data-ttu-id="9d558-171">`None`: dit is de standaardoptie wanneer **verificatie** niet is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9d558-171">`None`: This is the default option when **Authentication** is not supplied.</span></span> <span data-ttu-id="9d558-172">Er wordt geen expliciete verificatie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9d558-172">No explicit authentication will be used.</span></span>
- <span data-ttu-id="9d558-173">`Basic`: vereist **referentie**.</span><span class="sxs-lookup"><span data-stu-id="9d558-173">`Basic`: Requires **Credential**.</span></span> <span data-ttu-id="9d558-174">De referenties worden gebruikt voor het verzenden van een RFC 7617 Basic `Authorization: Basic` Authentication-header in de indeling `base64(user:password)` van .</span><span class="sxs-lookup"><span data-stu-id="9d558-174">The credentials will be used to send an RFC 7617 Basic Authentication `Authorization: Basic` header in the format of `base64(user:password)`.</span></span>
- <span data-ttu-id="9d558-175">`Bearer`: hiervoor is **Token vereist.**</span><span class="sxs-lookup"><span data-stu-id="9d558-175">`Bearer`: Requires **Token**.</span></span> <span data-ttu-id="9d558-176">Verzendt en RFC 6750-header `Authorization: Bearer` met het opgegeven token.</span><span class="sxs-lookup"><span data-stu-id="9d558-176">Will send and RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="9d558-177">Dit is een alias voor **OAuth**</span><span class="sxs-lookup"><span data-stu-id="9d558-177">This is an alias for **OAuth**</span></span>
- <span data-ttu-id="9d558-178">`OAuth`: hiervoor is **Token vereist.**</span><span class="sxs-lookup"><span data-stu-id="9d558-178">`OAuth`: Requires **Token**.</span></span> <span data-ttu-id="9d558-179">Verzendt een RFC 6750-header `Authorization: Bearer` met het opgegeven token.</span><span class="sxs-lookup"><span data-stu-id="9d558-179">Will send an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="9d558-180">Dit is een alias voor **Bearer**</span><span class="sxs-lookup"><span data-stu-id="9d558-180">This is an alias for **Bearer**</span></span>

<span data-ttu-id="9d558-181">Als **verificatie wordt** opgegeven, worden alle headers overschrijven die worden geleverd aan `Authorization` **headers** of die zijn opgenomen in **WebSession**.</span><span class="sxs-lookup"><span data-stu-id="9d558-181">Supplying **Authentication** will override any `Authorization` headers supplied to **Headers** or included in **WebSession**.</span></span>

<span data-ttu-id="9d558-182">Deze functie is toegevoegd in PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="9d558-182">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="9d558-183">-Body</span><span class="sxs-lookup"><span data-stu-id="9d558-183">-Body</span></span>

<span data-ttu-id="9d558-184">Hiermee geeft u de body van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="9d558-184">Specifies the body of the request.</span></span> <span data-ttu-id="9d558-185">De hoofdtekst is de inhoud van de aanvraag die volgt op de headers.</span><span class="sxs-lookup"><span data-stu-id="9d558-185">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="9d558-186">U kunt ook een waarde voor de body doorspijpen naar `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="9d558-186">You can also pipe a body value to `Invoke-RestMethod`.</span></span>

<span data-ttu-id="9d558-187">De **parameter Body** kan worden gebruikt om een lijst met queryparameters op te geven of om de inhoud van het antwoord op te geven.</span><span class="sxs-lookup"><span data-stu-id="9d558-187">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="9d558-188">Wanneer de invoer een GET-aanvraag is en de body een is (meestal een hash-tabel), wordt de body als queryparameters toegevoegd aan de `IDictionary` Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="9d558-188">When the input is a GET request, and the body is an `IDictionary` (typically, a hash table), the body is added to the Uniform Resource Identifier (URI) as query parameters.</span></span> <span data-ttu-id="9d558-189">Voor andere aanvraagtypen (zoals POST) wordt de body ingesteld als de waarde van de aanvraag body in de standaardindeling name=value.</span><span class="sxs-lookup"><span data-stu-id="9d558-189">For other request types (such as POST), the body is set as the value of the request body in the standard name=value format.</span></span>

<span data-ttu-id="9d558-190">Wanneer de body een formulier is of de uitvoer van een andere aanroep, stelt PowerShell de aanvraaginhoud in `Invoke-WebRequest` op de formuliervelden.</span><span class="sxs-lookup"><span data-stu-id="9d558-190">When the body is a form, or it's the output of another `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>

<span data-ttu-id="9d558-191">De **parameter Body** kan ook een **System.Net.Http.MultipartFormDataContent-object** accepteren.</span><span class="sxs-lookup"><span data-stu-id="9d558-191">The **Body** parameter may also accept a **System.Net.Http.MultipartFormDataContent** object.</span></span> <span data-ttu-id="9d558-192">Hierdoor kunnen aanvragen worden `multipart/form-data` gefaciliiliteert.</span><span class="sxs-lookup"><span data-stu-id="9d558-192">This will facilitate `multipart/form-data` requests.</span></span> <span data-ttu-id="9d558-193">Wanneer een **MultipartFormDataContent-object** wordt opgegeven voor **Hoofdtekst,** worden alle inhoudsgerelateerde headers die zijn opgegeven voor de parameters **ContentType,** **Headers** of **WebSession** overgeslagen door de inhoudsheaders van het `MultipartFormDataContent` object.</span><span class="sxs-lookup"><span data-stu-id="9d558-193">When a **MultipartFormDataContent** object is supplied for **Body**, any content related headers supplied to the **ContentType**, **Headers**, or **WebSession** parameters will be overridden by the content headers of the `MultipartFormDataContent` object.</span></span> <span data-ttu-id="9d558-194">Deze functie is toegevoegd in PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="9d558-194">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="9d558-195">-Certificaat</span><span class="sxs-lookup"><span data-stu-id="9d558-195">-Certificate</span></span>

<span data-ttu-id="9d558-196">Hiermee geeft u het clientcertificaat op dat wordt gebruikt voor een beveiligde webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="9d558-196">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="9d558-197">Voer een variabele in die een certificaat bevat of een opdracht of expressie die het certificaat op haalt.</span><span class="sxs-lookup"><span data-stu-id="9d558-197">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="9d558-198">Als u een certificaat wilt zoeken, `Get-PfxCertificate` gebruikt of gebruikt u de `Get-ChildItem` cmdlet in het station Certificaat ( `Cert:` ).</span><span class="sxs-lookup"><span data-stu-id="9d558-198">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="9d558-199">Als het certificaat niet geldig is of onvoldoende bevoegdheid heeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="9d558-199">If the certificate isn't valid or doesn't have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="9d558-200">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="9d558-200">-CertificateThumbprint</span></span>

<span data-ttu-id="9d558-201">Hiermee geeft u het digitale openbare-sleutelcertificaat (X509) op van een gebruikersaccount dat toestemming heeft om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="9d558-201">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="9d558-202">Voer de vingerafdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="9d558-202">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="9d558-203">Certificaten worden gebruikt in verificatie op basis van clientcertificaten.</span><span class="sxs-lookup"><span data-stu-id="9d558-203">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="9d558-204">Ze kunnen alleen worden toe te staan aan lokale gebruikersaccounts; ze werken niet met domeinaccounts.</span><span class="sxs-lookup"><span data-stu-id="9d558-204">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="9d558-205">Gebruik de opdracht of in het PowerShell-station om een vingerafdruk van het `Get-Item` `Get-ChildItem` certificaat op te `Cert:` halen.</span><span class="sxs-lookup"><span data-stu-id="9d558-205">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

> [!NOTE]
> <span data-ttu-id="9d558-206">Deze functie wordt momenteel alleen ondersteund op Windows-besturingssysteemplatforms.</span><span class="sxs-lookup"><span data-stu-id="9d558-206">This feature is currently only supported on Windows OS platforms.</span></span>

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

### <span data-ttu-id="9d558-207">-ContentType</span><span class="sxs-lookup"><span data-stu-id="9d558-207">-ContentType</span></span>

<span data-ttu-id="9d558-208">Hiermee geeft u het inhoudstype van de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="9d558-208">Specifies the content type of the web request.</span></span>

<span data-ttu-id="9d558-209">Als deze parameter wordt weggelaten en de aanvraagmethode POST is, `Invoke-RestMethod` stelt u het inhoudstype in op `application/x-www-form-urlencoded` .</span><span class="sxs-lookup"><span data-stu-id="9d558-209">If this parameter is omitted and the request method is POST, `Invoke-RestMethod` sets the content type to `application/x-www-form-urlencoded`.</span></span> <span data-ttu-id="9d558-210">Anders wordt het inhoudstype niet opgegeven in de aanroep.</span><span class="sxs-lookup"><span data-stu-id="9d558-210">Otherwise, the content type isn't specified in the call.</span></span>

<span data-ttu-id="9d558-211">**ContentType** wordt overschrijven wanneer een `MultipartFormDataContent` object wordt opgegeven voor **Body**.</span><span class="sxs-lookup"><span data-stu-id="9d558-211">**ContentType** will be overridden when a `MultipartFormDataContent` object is supplied for **Body**.</span></span>

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

### <span data-ttu-id="9d558-212">-Credential</span><span class="sxs-lookup"><span data-stu-id="9d558-212">-Credential</span></span>

<span data-ttu-id="9d558-213">Hiermee geeft u een gebruikersaccount op dat toestemming heeft om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="9d558-213">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="9d558-214">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="9d558-214">The default is the current user.</span></span>

<span data-ttu-id="9d558-215">Typ een gebruikersnaam, zoals **User01** of **Domain01\User01,** of voer een **PSCredential-object** in dat is gegenereerd door de `Get-Credential` cmdlet .</span><span class="sxs-lookup"><span data-stu-id="9d558-215">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="9d558-216">**Referenties** kunnen alleen worden gebruikt of in combinatie met bepaalde opties voor verificatieparameters. </span><span class="sxs-lookup"><span data-stu-id="9d558-216">**Credential** can be used alone or in conjunction with certain **Authentication** parameter options.</span></span> <span data-ttu-id="9d558-217">Als u alleen gebruikt, geeft deze alleen referenties aan de externe server als de externe server een aanvraag voor verificatie-vraag verzendt.</span><span class="sxs-lookup"><span data-stu-id="9d558-217">When used alone, it will only supply credentials to the remote server if the remote server sends an authentication challenge request.</span></span> <span data-ttu-id="9d558-218">Wanneer u **verificatieopties** gebruikt, worden de referenties expliciet verzonden.</span><span class="sxs-lookup"><span data-stu-id="9d558-218">When used with **Authentication** options, the credentials will be explicitly sent.</span></span>

<span data-ttu-id="9d558-219">Referenties worden opgeslagen in een [PSCredential-object](/dotnet/api/system.management.automation.pscredential) en het wachtwoord wordt opgeslagen als een [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="9d558-219">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="9d558-220">Zie Hoe veilig is **SecureString?** voor meer informatie over [SecureString-gegevensbeveiliging.](/dotnet/api/system.security.securestring#how-secure-is-securestring)</span><span class="sxs-lookup"><span data-stu-id="9d558-220">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="9d558-221">-CustomMethod</span><span class="sxs-lookup"><span data-stu-id="9d558-221">-CustomMethod</span></span>

<span data-ttu-id="9d558-222">Hiermee geeft u de aangepaste methode op die wordt gebruikt voor de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="9d558-222">Specifies custom method used for the web request.</span></span> <span data-ttu-id="9d558-223">Dit kan worden gebruikt met de aanvraagmethode die vereist is voor het eindpunt is geen beschikbare optie op de **methode**.</span><span class="sxs-lookup"><span data-stu-id="9d558-223">This can be used with the Request Method required by the endpoint is not an available option on the **Method**.</span></span> <span data-ttu-id="9d558-224">**Methode** en **CustomMethod** kunnen niet samen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9d558-224">**Method** and **CustomMethod** cannot be used together.</span></span>

<span data-ttu-id="9d558-225">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9d558-225">Example:</span></span>

`Invoke-RestMethod -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

<span data-ttu-id="9d558-226">Hiermee wordt een `TEST` HTTP-aanvraag naar de API ingediend.</span><span class="sxs-lookup"><span data-stu-id="9d558-226">This makes a `TEST` HTTP request to the API.</span></span>

<span data-ttu-id="9d558-227">Deze functie is toegevoegd in PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="9d558-227">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="9d558-228">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="9d558-228">-DisableKeepAlive</span></span>

<span data-ttu-id="9d558-229">Geeft aan dat de cmdlet de **KeepAlive-waarde** in de HTTP-header in stelt op False.</span><span class="sxs-lookup"><span data-stu-id="9d558-229">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to False.</span></span> <span data-ttu-id="9d558-230">**KeepAlive** is standaard True.</span><span class="sxs-lookup"><span data-stu-id="9d558-230">By default, **KeepAlive** is True.</span></span> <span data-ttu-id="9d558-231">**KeepAlive brengt** een permanente verbinding met de server tot stand om volgende aanvragen mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="9d558-231">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="9d558-232">-FollowRelLink</span><span class="sxs-lookup"><span data-stu-id="9d558-232">-FollowRelLink</span></span>

<span data-ttu-id="9d558-233">Geeft aan dat de cmdlet relationele koppelingen moet volgen.</span><span class="sxs-lookup"><span data-stu-id="9d558-233">Indicates the cmdlet should follow relation links.</span></span>

<span data-ttu-id="9d558-234">Sommige REST API's ondersteunen paginering via Relation Links per [RFC5988.](https://tools.ietf.org/html/rfc5988#page-6)</span><span class="sxs-lookup"><span data-stu-id="9d558-234">Some REST APIs support pagination via Relation Links per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span></span> <span data-ttu-id="9d558-235">In plaats van de header te parseren om de URL voor de volgende pagina op te halen, kunt u de cmdlet dit voor u laten doen.</span><span class="sxs-lookup"><span data-stu-id="9d558-235">Instead of parsing the header to get the URL for the next page, you can have the cmdlet do this for you.</span></span> <span data-ttu-id="9d558-236">Gebruik de parameter **MaximumFollowRelLink** om in te stellen hoe vaak u de relatiekoppelingen moet volgen.</span><span class="sxs-lookup"><span data-stu-id="9d558-236">To set how many times to follow relation links, use the **MaximumFollowRelLink** parameter.</span></span>

<span data-ttu-id="9d558-237">Wanneer u deze switch gebruikt, retourneert de cmdlet een verzameling pagina's met resultaten.</span><span class="sxs-lookup"><span data-stu-id="9d558-237">When using this switch, the cmdlet returns a collection of pages of results.</span></span> <span data-ttu-id="9d558-238">Elke pagina met resultaten kan meerdere resultaatitems bevatten.</span><span class="sxs-lookup"><span data-stu-id="9d558-238">Each page of results may contain multiple result items.</span></span>

<span data-ttu-id="9d558-239">Deze functie is toegevoegd in PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="9d558-239">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="9d558-240">-Form</span><span class="sxs-lookup"><span data-stu-id="9d558-240">-Form</span></span>

<span data-ttu-id="9d558-241">Converteert een woordenlijst naar een `multipart/form-data` inzending.</span><span class="sxs-lookup"><span data-stu-id="9d558-241">Converts a dictionary to a `multipart/form-data` submission.</span></span> <span data-ttu-id="9d558-242">**Formulier** kan niet worden gebruikt met **Body**.</span><span class="sxs-lookup"><span data-stu-id="9d558-242">**Form** may not be used with **Body**.</span></span>
<span data-ttu-id="9d558-243">Als **ContentType** wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="9d558-243">If **ContentType** will be ignored.</span></span>

<span data-ttu-id="9d558-244">De sleutels van de woordenlijst worden gebruikt als de namen van formulierveld.</span><span class="sxs-lookup"><span data-stu-id="9d558-244">The keys of the dictionary will be used as the form field names.</span></span> <span data-ttu-id="9d558-245">Standaard worden formulierwaarden geconverteerd naar tekenreekswaarden.</span><span class="sxs-lookup"><span data-stu-id="9d558-245">By default, form values will be converted to string values.</span></span>

<span data-ttu-id="9d558-246">Als de waarde een **System.IO.FileInfo-object** is, wordt de inhoud van het binaire bestand verzonden.</span><span class="sxs-lookup"><span data-stu-id="9d558-246">If the value is a **System.IO.FileInfo** object, then the binary file contents will be submitted.</span></span>
<span data-ttu-id="9d558-247">De naam van het bestand wordt verzonden als de `filename` .</span><span class="sxs-lookup"><span data-stu-id="9d558-247">The name of the file will be submitted as the `filename`.</span></span> <span data-ttu-id="9d558-248">De MIME wordt ingesteld als `application/octet-stream` .</span><span class="sxs-lookup"><span data-stu-id="9d558-248">The MIME will be set as `application/octet-stream`.</span></span> <span data-ttu-id="9d558-249">`Get-Item` kan worden gebruikt om het leveren van het **object System.IO.FileInfo te** vereenvoudigen.</span><span class="sxs-lookup"><span data-stu-id="9d558-249">`Get-Item` can be used to simplify supplying the **System.IO.FileInfo** object.</span></span>

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

<span data-ttu-id="9d558-250">Als de waarde een verzamelingstype is, zoals een Matrix of Lijst, wordt het veld for meerdere keren verzonden.</span><span class="sxs-lookup"><span data-stu-id="9d558-250">If the value is a collection type, such as an Array or List, the for field will be submitted multiple times.</span></span> <span data-ttu-id="9d558-251">De waarden van de lijst worden standaard behandeld als tekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="9d558-251">The values of the list will be treated as strings by default.</span></span> <span data-ttu-id="9d558-252">Als de waarde een **System.IO.FileInfo-object** is, wordt de inhoud van het binaire bestand verzonden.</span><span class="sxs-lookup"><span data-stu-id="9d558-252">If the value is a **System.IO.FileInfo** object, then the binary file contents will be submitted.</span></span> <span data-ttu-id="9d558-253">Geneste verzamelingen worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="9d558-253">Nested collections aren't supported.</span></span>

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

<span data-ttu-id="9d558-254">In het bovenstaande voorbeeld wordt het veld drie keer in het formulier opgegeven, één keer `tags` voor elk van , en `Vacation` `Italy` `2017` .</span><span class="sxs-lookup"><span data-stu-id="9d558-254">In the above example, the `tags` field will be supplied three times in the form, once for each of `Vacation`, `Italy`, and `2017`.</span></span> <span data-ttu-id="9d558-255">Het `pictures` veld wordt ook eenmaal verzonden voor elk bestand in de `2017-Italy` map.</span><span class="sxs-lookup"><span data-stu-id="9d558-255">The `pictures` field will also be submitted once for each file in the `2017-Italy` folder.</span></span> <span data-ttu-id="9d558-256">De binaire inhoud van de bestanden in die map wordt verzonden als de waarden.</span><span class="sxs-lookup"><span data-stu-id="9d558-256">The binary contents of the files in that folder will be submitted as the values.</span></span>

<span data-ttu-id="9d558-257">Deze functie is toegevoegd in PowerShell 6.1.0.</span><span class="sxs-lookup"><span data-stu-id="9d558-257">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="9d558-258">-Headers</span><span class="sxs-lookup"><span data-stu-id="9d558-258">-Headers</span></span>

<span data-ttu-id="9d558-259">Hiermee geeft u de headers van de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="9d558-259">Specifies the headers of the web request.</span></span> <span data-ttu-id="9d558-260">Voer een hashtabel of -woordenlijst in.</span><span class="sxs-lookup"><span data-stu-id="9d558-260">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="9d558-261">Als u UserAgent-headers wilt instellen, gebruikt u de parameter **UserAgent.**</span><span class="sxs-lookup"><span data-stu-id="9d558-261">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="9d558-262">U kunt deze parameter niet gebruiken om headers of `User-Agent` cookies op te geven.</span><span class="sxs-lookup"><span data-stu-id="9d558-262">You cannot use this parameter to specify `User-Agent` or cookie headers.</span></span>

<span data-ttu-id="9d558-263">Inhoudsgerelateerde headers, zoals `Content-Type` , worden overschrijven wanneer een `MultipartFormDataContent` object wordt opgegeven voor **Hoofdtekst.**</span><span class="sxs-lookup"><span data-stu-id="9d558-263">Content related headers, such as `Content-Type` will be overridden when a `MultipartFormDataContent` object is supplied for **Body**.</span></span>

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

### <span data-ttu-id="9d558-264">-InFile</span><span class="sxs-lookup"><span data-stu-id="9d558-264">-InFile</span></span>

<span data-ttu-id="9d558-265">Haalt de inhoud van de webaanvraag op uit een bestand.</span><span class="sxs-lookup"><span data-stu-id="9d558-265">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="9d558-266">Voer een pad en bestandsnaam in.</span><span class="sxs-lookup"><span data-stu-id="9d558-266">Enter a path and file name.</span></span> <span data-ttu-id="9d558-267">Als u het pad weglaten, is de standaardwaarde de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="9d558-267">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="9d558-268">-MaximumFollowRelLink</span><span class="sxs-lookup"><span data-stu-id="9d558-268">-MaximumFollowRelLink</span></span>

<span data-ttu-id="9d558-269">Hiermee geeft u op hoe vaak u relatiekoppelingen moet volgen **als FollowRelLink** wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9d558-269">Specifies how many times to follow relation links if **FollowRelLink** is used.</span></span> <span data-ttu-id="9d558-270">Mogelijk is er een kleinere waarde nodig als de REST API wordt beperkt vanwege te veel aanvragen.</span><span class="sxs-lookup"><span data-stu-id="9d558-270">A smaller value may be needed if the REST api throttles due to too many requests.</span></span> <span data-ttu-id="9d558-271">De standaardwaarde is `[Int32]::MaxValue`.</span><span class="sxs-lookup"><span data-stu-id="9d558-271">The default value is `[Int32]::MaxValue`.</span></span> <span data-ttu-id="9d558-272">Een waarde van 0 (nul) voorkomt het volgen van relatiekoppelingen.</span><span class="sxs-lookup"><span data-stu-id="9d558-272">A value of 0 (zero) prevents following relation links.</span></span>

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

### <span data-ttu-id="9d558-273">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="9d558-273">-MaximumRedirection</span></span>

<span data-ttu-id="9d558-274">Hiermee geeft u op hoe vaak PowerShell een verbinding omleiden naar een alternatieve Uniform Resource Identifier (URI) voordat de verbinding mislukt.</span><span class="sxs-lookup"><span data-stu-id="9d558-274">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="9d558-275">De standaardwaarde is 5.</span><span class="sxs-lookup"><span data-stu-id="9d558-275">The default value is 5.</span></span> <span data-ttu-id="9d558-276">Met de waarde 0 (nul) wordt alle omleiding voorkomen.</span><span class="sxs-lookup"><span data-stu-id="9d558-276">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="9d558-277">-MaximumRetryCount</span><span class="sxs-lookup"><span data-stu-id="9d558-277">-MaximumRetryCount</span></span>

<span data-ttu-id="9d558-278">Hiermee geeft u op hoe vaak PowerShell opnieuw verbinding maakt wanneer een foutcode tussen 400 en 599 wordt ontvangen, inclusief of 304.</span><span class="sxs-lookup"><span data-stu-id="9d558-278">Specifies how many times PowerShell retries a connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="9d558-279">Zie ook **de parameter RetryIntervalSec** voor het opgeven van het aantal nieuwe poging.</span><span class="sxs-lookup"><span data-stu-id="9d558-279">Also see **RetryIntervalSec** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="9d558-280">-Methode</span><span class="sxs-lookup"><span data-stu-id="9d558-280">-Method</span></span>

<span data-ttu-id="9d558-281">Hiermee geeft u de methode die wordt gebruikt voor de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="9d558-281">Specifies the method used for the web request.</span></span> <span data-ttu-id="9d558-282">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="9d558-282">The acceptable values for this parameter are:</span></span>

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

<span data-ttu-id="9d558-283">De **parameter CustomMethod** kan worden gebruikt voor aanvraagmethoden die hierboven niet worden vermeld.</span><span class="sxs-lookup"><span data-stu-id="9d558-283">The **CustomMethod** parameter can be used for Request Methods not listed above.</span></span>

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

### <span data-ttu-id="9d558-284">-NoProxy</span><span class="sxs-lookup"><span data-stu-id="9d558-284">-NoProxy</span></span>

<span data-ttu-id="9d558-285">Geeft aan dat de cmdlet geen proxy gebruikt om de bestemming te bereiken.</span><span class="sxs-lookup"><span data-stu-id="9d558-285">Indicates that the cmdlet will not use a proxy to reach the destination.</span></span>

<span data-ttu-id="9d558-286">Wanneer u de proxy wilt omzeilen die is geconfigureerd in Internet Explorer of een proxy die is opgegeven in de omgeving, gebruikt u deze switch.</span><span class="sxs-lookup"><span data-stu-id="9d558-286">When you need to bypass the proxy configured in Internet Explorer, or a proxy specified in the environment, use this switch.</span></span>

<span data-ttu-id="9d558-287">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="9d558-287">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="9d558-288">-OutFile</span><span class="sxs-lookup"><span data-stu-id="9d558-288">-OutFile</span></span>

<span data-ttu-id="9d558-289">Slaat de antwoord-body in het opgegeven uitvoerbestand.</span><span class="sxs-lookup"><span data-stu-id="9d558-289">Saves the response body in the specified output file.</span></span> <span data-ttu-id="9d558-290">Voer een pad en bestandsnaam in.</span><span class="sxs-lookup"><span data-stu-id="9d558-290">Enter a path and file name.</span></span> <span data-ttu-id="9d558-291">Als u het pad weglaten, is de standaardwaarde de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="9d558-291">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="9d558-292">Retourneert `Invoke-RestMethod` standaard de resultaten naar de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="9d558-292">By default, `Invoke-RestMethod` returns the results to the pipeline.</span></span> <span data-ttu-id="9d558-293">Als u de resultaten wilt verzenden naar een bestand en naar de pijplijn, gebruikt u de parameter **Passthru.**</span><span class="sxs-lookup"><span data-stu-id="9d558-293">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="9d558-294">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9d558-294">-PassThru</span></span>

<span data-ttu-id="9d558-295">Retourneert de resultaten, naast het schrijven ervan naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="9d558-295">Returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="9d558-296">Deze parameter is alleen geldig wanneer **de OutFile** parameter wordt ook gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="9d558-296">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="9d558-297">-PreserveAuthorizationOnRedirect</span><span class="sxs-lookup"><span data-stu-id="9d558-297">-PreserveAuthorizationOnRedirect</span></span>

<span data-ttu-id="9d558-298">Geeft aan dat de cmdlet de header, indien aanwezig, moet behouden `Authorization` tussen omleidingen.</span><span class="sxs-lookup"><span data-stu-id="9d558-298">Indicates the cmdlet should preserve the `Authorization` header, when present, across redirections.</span></span>

<span data-ttu-id="9d558-299">De cmdlet ontdoet de `Authorization` header standaard voordat deze wordt omgeleid.</span><span class="sxs-lookup"><span data-stu-id="9d558-299">By default, the cmdlet strips the `Authorization` header before redirecting.</span></span> <span data-ttu-id="9d558-300">Als u deze parameter opgeeft, wordt deze logica uitgeschakeld voor gevallen waarin de header naar de omleidingslocatie moet worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="9d558-300">Specifying this parameter disables this logic for cases where the header needs to be sent to the redirection location.</span></span>

<span data-ttu-id="9d558-301">Deze functie is toegevoegd in PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="9d558-301">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="9d558-302">-Proxy</span><span class="sxs-lookup"><span data-stu-id="9d558-302">-Proxy</span></span>

<span data-ttu-id="9d558-303">Maakt gebruik van een proxyserver voor de aanvraag, in plaats van rechtstreeks verbinding te maken met de internetresource.</span><span class="sxs-lookup"><span data-stu-id="9d558-303">Uses a proxy server for the request, rather than connecting directly to the internet resource.</span></span> <span data-ttu-id="9d558-304">Voer de Uniform Resource Identifier (URI) van een netwerkproxyserver in.</span><span class="sxs-lookup"><span data-stu-id="9d558-304">Enter the Uniform Resource Identifier (URI) of a network proxy server.</span></span>

<span data-ttu-id="9d558-305">Deze functie is toegevoegd in PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="9d558-305">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="9d558-306">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="9d558-306">-ProxyCredential</span></span>

<span data-ttu-id="9d558-307">Hiermee geeft u een gebruikersaccount dat is gemachtigd voor het gebruik van de proxyserver die is opgegeven door de **proxyparameter.**</span><span class="sxs-lookup"><span data-stu-id="9d558-307">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="9d558-308">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="9d558-308">The default is the current user.</span></span>

<span data-ttu-id="9d558-309">Typ een gebruikersnaam, zoals **User01** of **Domain01\User01,** of voer een -object in, zoals een object dat wordt gegenereerd door **User@Domain.Com** `PSCredential` de `Get-Credential` cmdlet .</span><span class="sxs-lookup"><span data-stu-id="9d558-309">Type a user name, such as **User01** or **Domain01\User01**, **User@Domain.Com**, or enter a `PSCredential` object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="9d558-310">Deze parameter is alleen geldig wanneer de **Proxy** parameter wordt ook gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="9d558-310">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="9d558-311">U kunt de parameters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="9d558-311">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="9d558-312">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="9d558-312">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="9d558-313">Geeft aan dat de cmdlet de referenties van de huidige gebruiker gebruikt voor toegang tot de proxyserver die is opgegeven door de **proxyparameter.**</span><span class="sxs-lookup"><span data-stu-id="9d558-313">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="9d558-314">Deze parameter is alleen geldig wanneer de **proxy** parameter wordt ook gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="9d558-314">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="9d558-315">U kunt de parameters **ProxyCredential** en **ProxyUseDefaultCredentials** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="9d558-315">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="9d558-316">-ResponseHeadersVariable</span><span class="sxs-lookup"><span data-stu-id="9d558-316">-ResponseHeadersVariable</span></span>

<span data-ttu-id="9d558-317">Hiermee maakt u een woordenlijst antwoordheaders en slaat u deze op in de waarde van de opgegeven variabele.</span><span class="sxs-lookup"><span data-stu-id="9d558-317">Creates a Response Headers Dictionary and saves it in the value of the specified variable.</span></span> <span data-ttu-id="9d558-318">De sleutels van de woordenlijst bevatten de veldnamen van de antwoordheader die wordt geretourneerd door de webserver en de waarden zijn de respectieve veldwaarden.</span><span class="sxs-lookup"><span data-stu-id="9d558-318">The keys of the dictionary will contain the field names of the Response Header returned by the web server and the values will be the respective field values.</span></span>

<span data-ttu-id="9d558-319">Deze functie is toegevoegd in PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="9d558-319">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="9d558-320">-Hervatten</span><span class="sxs-lookup"><span data-stu-id="9d558-320">-Resume</span></span>

<span data-ttu-id="9d558-321">Voert een poging uit om het downloaden van een gedeeltelijk bestand te hervatten.</span><span class="sxs-lookup"><span data-stu-id="9d558-321">Performs a best effort attempt to resume downloading a partial file.</span></span> <span data-ttu-id="9d558-322">Voor de parameter **Resume** is de parameter **OutFile** vereist.</span><span class="sxs-lookup"><span data-stu-id="9d558-322">The **Resume** parameter requires the **OutFile** parameter.</span></span>

<span data-ttu-id="9d558-323">**Hervatten** werkt alleen op de grootte van het lokale bestand en externe bestand en voert geen andere validatie uit dat het lokale bestand en het externe bestand hetzelfde zijn.</span><span class="sxs-lookup"><span data-stu-id="9d558-323">**Resume** only operates on the size of the local file and remote file and performs no other validation that the local file and the remote file are the same.</span></span>

<span data-ttu-id="9d558-324">Als de grootte van het lokale bestand kleiner is dan de externe bestandsgrootte, probeert de cmdlet het downloaden van het bestand te hervatten en de resterende bytes toe te toevoegen aan het einde van het bestand.</span><span class="sxs-lookup"><span data-stu-id="9d558-324">If the local file size is smaller than the remote file size, then the cmdlet will attempt to resume downloading the file and append the remaining bytes to the end of the file.</span></span>

<span data-ttu-id="9d558-325">Als de grootte van het lokale bestand hetzelfde is als de grootte van het externe bestand, wordt er geen actie ondernomen en wordt ervan uitgenomen dat het downloaden al is voltooid.</span><span class="sxs-lookup"><span data-stu-id="9d558-325">If the local file size is the same as the remote file size, then no action is taken and the cmdlet assumes the download already completed.</span></span>

<span data-ttu-id="9d558-326">Als de lokale bestandsgrootte groter is dan de grootte van het externe bestand, wordt het lokale bestand overschreven en wordt het hele externe bestand volledig opnieuw gedownload.</span><span class="sxs-lookup"><span data-stu-id="9d558-326">If the local file size is larger than the remote file size, then the local file will be overwritten and the entire remote file will be completely re-downloaded.</span></span> <span data-ttu-id="9d558-327">Dit gedrag is hetzelfde als het gebruik van **OutFile** zonder **Hervatten.**</span><span class="sxs-lookup"><span data-stu-id="9d558-327">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="9d558-328">Als de externe server geen ondersteuning biedt voor het downloaden van het downloaden, wordt het lokale bestand overschreven en wordt het hele externe bestand volledig opnieuw gedownload.</span><span class="sxs-lookup"><span data-stu-id="9d558-328">If the remote server does not support download resuming, then the local file will be overwritten and the entire remote file will be completely re-downloaded.</span></span> <span data-ttu-id="9d558-329">Dit gedrag is hetzelfde als het gebruik van **OutFile** zonder **Hervatten.**</span><span class="sxs-lookup"><span data-stu-id="9d558-329">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="9d558-330">Als het lokale bestand niet bestaat, wordt het lokale bestand gemaakt en wordt het hele externe bestand volledig gedownload.</span><span class="sxs-lookup"><span data-stu-id="9d558-330">If the local file doesn't exist, then the local file will be created and the entire remote file will be completely downloaded.</span></span> <span data-ttu-id="9d558-331">Dit gedrag is hetzelfde als het gebruik van **OutFile** zonder **Hervatten.**</span><span class="sxs-lookup"><span data-stu-id="9d558-331">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="9d558-332">Deze functie is toegevoegd in PowerShell 6.1.0.</span><span class="sxs-lookup"><span data-stu-id="9d558-332">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="9d558-333">-RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="9d558-333">-RetryIntervalSec</span></span>

<span data-ttu-id="9d558-334">Hiermee geeft u het interval op tussen nieuwe proberen voor de verbinding wanneer een foutcode tussen 400 en 599 wordt ontvangen, inclusief of 304.</span><span class="sxs-lookup"><span data-stu-id="9d558-334">Specifies the interval between retries for the connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="9d558-335">Zie ook **de parameter MaximumRetryCount** voor het opgeven van het aantal nieuwe poging.</span><span class="sxs-lookup"><span data-stu-id="9d558-335">Also see **MaximumRetryCount** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="9d558-336">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="9d558-336">-SessionVariable</span></span>

<span data-ttu-id="9d558-337">Hiermee geeft u een variabele waarvoor deze cmdlet maakt een webaanvraagsessie en slaat deze in de waarde.</span><span class="sxs-lookup"><span data-stu-id="9d558-337">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="9d558-338">Voer een variabelenaam in zonder het dollarteken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="9d558-338">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="9d558-339">Wanneer u een sessievariabele opgeeft, maakt een webaanvraagsessieobject en wijst u dit toe aan een variabele met de opgegeven `Invoke-RestMethod` naam in uw PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="9d558-339">When you specify a session variable, `Invoke-RestMethod` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="9d558-340">U kunt de variabele in uw sessie gebruiken zodra de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="9d558-340">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="9d558-341">In tegenstelling tot een externe sessie is de webaanvraagsessie geen permanente verbinding.</span><span class="sxs-lookup"><span data-stu-id="9d558-341">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="9d558-342">Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximale omleidingswaarde en de tekenreeks van de gebruikersagent.</span><span class="sxs-lookup"><span data-stu-id="9d558-342">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="9d558-343">U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="9d558-343">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="9d558-344">Als u de webaanvraagsessie in volgende webaanvragen wilt gebruiken, geeft u de sessievariabele op in de waarde van de parameter **WebSession.**</span><span class="sxs-lookup"><span data-stu-id="9d558-344">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="9d558-345">PowerShell gebruikt de gegevens in het webaanvraagsessieobject bij het tot stand brengen van de nieuwe verbinding.</span><span class="sxs-lookup"><span data-stu-id="9d558-345">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="9d558-346">Als u een waarde in de webaanvraagsessie wilt overschrijven, gebruikt u een cmdlet-parameter, zoals **UserAgent** of **Credential.**</span><span class="sxs-lookup"><span data-stu-id="9d558-346">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="9d558-347">Parameterwaarden hebben voorrang op waarden in de webaanvraagsessie.</span><span class="sxs-lookup"><span data-stu-id="9d558-347">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="9d558-348">U kunt de parameters **SessionVariable en** **WebSession** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="9d558-348">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="9d558-349">-SkipCertificateCheck</span><span class="sxs-lookup"><span data-stu-id="9d558-349">-SkipCertificateCheck</span></span>

<span data-ttu-id="9d558-350">Certificaatvalidatiecontroles die alle validaties bevatten, zoals verloop, intrekking, vertrouwde basisinstantie, enzovoort, worden overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="9d558-350">Skips certificate validation checks that include all validations such as expiration, revocation, trusted root authority, etc.</span></span>

> [!WARNING]
> <span data-ttu-id="9d558-351">Het gebruik van deze parameter is niet veilig en wordt niet aanbevolen.</span><span class="sxs-lookup"><span data-stu-id="9d558-351">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="9d558-352">Deze switch is alleen bedoeld om te worden gebruikt voor bekende hosts die een zelf-ondertekend certificaat gebruiken voor testdoeleinden.</span><span class="sxs-lookup"><span data-stu-id="9d558-352">This switch is only intended to be used against known hosts using a self-signed certificate for testing purposes.</span></span> <span data-ttu-id="9d558-353">Gebruik op uw eigen risico.</span><span class="sxs-lookup"><span data-stu-id="9d558-353">Use at your own risk.</span></span>

<span data-ttu-id="9d558-354">Deze functie is toegevoegd in PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="9d558-354">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="9d558-355">-SkipHeaderValidation</span><span class="sxs-lookup"><span data-stu-id="9d558-355">-SkipHeaderValidation</span></span>

<span data-ttu-id="9d558-356">Geeft aan dat de cmdlet headers moet toevoegen aan de aanvraag zonder validatie.</span><span class="sxs-lookup"><span data-stu-id="9d558-356">Indicates the cmdlet should add headers to the request without validation.</span></span>

<span data-ttu-id="9d558-357">Deze switch moet worden gebruikt voor sites waarvoor headerwaarden zijn vereist die niet voldoen aan de standaarden.</span><span class="sxs-lookup"><span data-stu-id="9d558-357">This switch should be used for sites that require header values that do not conform to standards.</span></span>
<span data-ttu-id="9d558-358">Als u deze switch opgeeft, wordt validatie uitgeschakeld zodat de waarde niet kan worden doorgegeven.</span><span class="sxs-lookup"><span data-stu-id="9d558-358">Specifying this switch disables validation to allow the value to be passed unchecked.</span></span> <span data-ttu-id="9d558-359">Wanneer dit is opgegeven, worden alle headers zonder validatie toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="9d558-359">When specified, all headers are added without validation.</span></span>

<span data-ttu-id="9d558-360">Hiermee wordt validatie uitgeschakeld voor waarden die worden doorgegeven aan de parameters **ContentType,** **Headers** en **UserAgent.**</span><span class="sxs-lookup"><span data-stu-id="9d558-360">This will disable validation for values passed to the **ContentType**, **Headers**, and **UserAgent** parameters.</span></span>

<span data-ttu-id="9d558-361">Deze functie is toegevoegd in PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="9d558-361">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="9d558-362">-SkipHttpErrorCheck</span><span class="sxs-lookup"><span data-stu-id="9d558-362">-SkipHttpErrorCheck</span></span>

<span data-ttu-id="9d558-363">Deze parameter zorgt ervoor dat de cmdlet HTTP-foutstatussen negeert en antwoorden blijft verwerken.</span><span class="sxs-lookup"><span data-stu-id="9d558-363">This parameter causes the cmdlet to ignore HTTP error statuses and continue to process responses.</span></span>
<span data-ttu-id="9d558-364">De foutreacties worden naar de pijplijn geschreven alsof ze zijn geslaagd.</span><span class="sxs-lookup"><span data-stu-id="9d558-364">The error responses are written to the pipeline just as if they were successful.</span></span>

<span data-ttu-id="9d558-365">Deze parameter is geïntroduceerd in PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="9d558-365">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="9d558-366">-SslProtocol</span><span class="sxs-lookup"><span data-stu-id="9d558-366">-SslProtocol</span></span>

<span data-ttu-id="9d558-367">Hiermee stelt u de SSL/TLS-protocollen in die toegestaan zijn voor de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="9d558-367">Sets the SSL/TLS protocols that are permissible for the web request.</span></span> <span data-ttu-id="9d558-368">Standaard zijn alle SSL/TLS-protocollen toegestaan die door het systeem worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="9d558-368">By default all, SSL/TLS protocols supported by the system are allowed.</span></span> <span data-ttu-id="9d558-369">**Met SslProtocol** kunt u beperken tot specifieke protocollen voor nalevingsdoeleinden.</span><span class="sxs-lookup"><span data-stu-id="9d558-369">**SslProtocol** allows for limiting to specific protocols for compliance purposes.</span></span>

<span data-ttu-id="9d558-370">Deze waarden worden gedefinieerd als een op vlag gebaseerde enumeratie.</span><span class="sxs-lookup"><span data-stu-id="9d558-370">These values are defined as a flag-based enumeration.</span></span> <span data-ttu-id="9d558-371">U kunt meerdere waarden combineren om meerdere vlaggen in te stellen met behulp van deze parameter.</span><span class="sxs-lookup"><span data-stu-id="9d558-371">You can combine multiple values together to set multiple flags using this parameter.</span></span> <span data-ttu-id="9d558-372">De waarden kunnen worden doorgegeven aan de **parameter SslProtocol** als een matrix met waarden of als een door komma's gescheiden tekenreeks van deze waarden.</span><span class="sxs-lookup"><span data-stu-id="9d558-372">The values can be passed to the **SslProtocol** parameter as an array of values or as a comma-separated string of those values.</span></span> <span data-ttu-id="9d558-373">De cmdlet combineert de waarden met behulp van een binaire-OR-bewerking.</span><span class="sxs-lookup"><span data-stu-id="9d558-373">The cmdlet will combine the values using a binary-OR operation.</span></span> <span data-ttu-id="9d558-374">Het doorgeven van waarden als een matrix is de eenvoudigste optie. Hiermee kunt u ook tab-completion gebruiken voor de waarden.</span><span class="sxs-lookup"><span data-stu-id="9d558-374">Passing values as an array is the simplest option and also allows you to use tab-completion on the values.</span></span> <span data-ttu-id="9d558-375">Mogelijk kunt u niet meerdere waarden op alle platformen leveren.</span><span class="sxs-lookup"><span data-stu-id="9d558-375">You may not be able to supply multiple values on all platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="9d558-376">Op niet-Windows-platforms is het mogelijk niet mogelijk om op te `'Tls, Tls12'` geven als een optie.</span><span class="sxs-lookup"><span data-stu-id="9d558-376">On non-Windows platforms it may not be possible to supply `'Tls, Tls12'` as an option.</span></span>

<span data-ttu-id="9d558-377">Deze functie is toegevoegd in PowerShell 6.0.0.</span><span class="sxs-lookup"><span data-stu-id="9d558-377">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="9d558-378">-StatusCodeVariable</span><span class="sxs-lookup"><span data-stu-id="9d558-378">-StatusCodeVariable</span></span>

<span data-ttu-id="9d558-379">Met deze parameter geeft u een variabele op die het gehele getal van een statuscode krijgt toegewezen.</span><span class="sxs-lookup"><span data-stu-id="9d558-379">This parameter specifies a variable that's assigned a status code's integer value.</span></span> <span data-ttu-id="9d558-380">De parameter kan succesberichten of foutberichten identificeren wanneer deze worden gebruikt met de parameter **SkipHttpErrorCheck.**</span><span class="sxs-lookup"><span data-stu-id="9d558-380">The parameter can identify success messages or failure messages when used with the **SkipHttpErrorCheck** parameter.</span></span>

<span data-ttu-id="9d558-381">Voer de variabelenaam van de parameter in als een tekenreeks zoals `-StatusCodeVariable "scv"` .</span><span class="sxs-lookup"><span data-stu-id="9d558-381">Input the parameter's variable name as a string such as `-StatusCodeVariable "scv"`.</span></span>

<span data-ttu-id="9d558-382">Deze parameter is geïntroduceerd in PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="9d558-382">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="9d558-383">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="9d558-383">-TimeoutSec</span></span>

<span data-ttu-id="9d558-384">Hiermee geeft u op hoe lang de aanvraag in behandeling kan zijn voordat er een times-out wordt uitgevoerd. Voer een waarde in seconden in.</span><span class="sxs-lookup"><span data-stu-id="9d558-384">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="9d558-385">De standaardwaarde, 0, geeft een onbeperkte time-out aan.</span><span class="sxs-lookup"><span data-stu-id="9d558-385">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="9d558-386">Het Domain Name System (DNS)-query kan tot 15 seconden duren voordat er een time-out of retourneren is. Als uw aanvraag een hostnaam bevat die een oplossing vereist en u **TimeoutSec** in stelt op een waarde die groter is dan nul, maar minder dan 15 seconden, kan het 15 seconden of langer duren voordat een WebException wordt gegeven en er een time-out van uw aanvraag wordt gegeven.</span><span class="sxs-lookup"><span data-stu-id="9d558-386">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="9d558-387">-Token</span><span class="sxs-lookup"><span data-stu-id="9d558-387">-Token</span></span>

<span data-ttu-id="9d558-388">Het OAuth- of Bearer-token dat in de aanvraag moet worden op te nemen.</span><span class="sxs-lookup"><span data-stu-id="9d558-388">The OAuth or Bearer token to include in the request.</span></span> <span data-ttu-id="9d558-389">**Token** is vereist voor bepaalde **verificatieopties.**</span><span class="sxs-lookup"><span data-stu-id="9d558-389">**Token** is required by certain **Authentication** options.</span></span> <span data-ttu-id="9d558-390">Deze kan niet onafhankelijk worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9d558-390">It can't be used independently.</span></span>

<span data-ttu-id="9d558-391">**Token** neemt een `SecureString` die het token bevat.</span><span class="sxs-lookup"><span data-stu-id="9d558-391">**Token** takes a `SecureString` that contains the token.</span></span> <span data-ttu-id="9d558-392">Gebruik het volgende handmatig om het token op te leveren:</span><span class="sxs-lookup"><span data-stu-id="9d558-392">To supply the token, manually use the following:</span></span>

`Invoke-RestMethod -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

<span data-ttu-id="9d558-393">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="9d558-393">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="9d558-394">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="9d558-394">-TransferEncoding</span></span>

<span data-ttu-id="9d558-395">Hiermee geeft u een waarde op voor de HTTP-antwoordheader voor overdrachtcoderen.</span><span class="sxs-lookup"><span data-stu-id="9d558-395">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="9d558-396">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="9d558-396">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9d558-397">Ge chunked</span><span class="sxs-lookup"><span data-stu-id="9d558-397">Chunked</span></span>
- <span data-ttu-id="9d558-398">Comprimeren</span><span class="sxs-lookup"><span data-stu-id="9d558-398">Compress</span></span>
- <span data-ttu-id="9d558-399">Deflate</span><span class="sxs-lookup"><span data-stu-id="9d558-399">Deflate</span></span>
- <span data-ttu-id="9d558-400">Gzip</span><span class="sxs-lookup"><span data-stu-id="9d558-400">GZip</span></span>
- <span data-ttu-id="9d558-401">Identiteit</span><span class="sxs-lookup"><span data-stu-id="9d558-401">Identity</span></span>

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

### <span data-ttu-id="9d558-402">-URI</span><span class="sxs-lookup"><span data-stu-id="9d558-402">-Uri</span></span>

<span data-ttu-id="9d558-403">Hiermee geeft u de Uniform Resource Identifier (URI) op van de internetresource waar de webaanvraag naar wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="9d558-403">Specifies the Uniform Resource Identifier (URI) of the internet resource to which the web request is sent.</span></span> <span data-ttu-id="9d558-404">Deze parameter ondersteunt http-, HTTPS-, FTP- en BESTANDswaarden.</span><span class="sxs-lookup"><span data-stu-id="9d558-404">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="9d558-405">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="9d558-405">This parameter is required.</span></span> <span data-ttu-id="9d558-406">De parameternaam (**URI**) is optioneel.</span><span class="sxs-lookup"><span data-stu-id="9d558-406">The parameter name (**Uri**) is optional.</span></span>

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

### <span data-ttu-id="9d558-407">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="9d558-407">-UseBasicParsing</span></span>

<span data-ttu-id="9d558-408">Deze parameter is afgeschaft.</span><span class="sxs-lookup"><span data-stu-id="9d558-408">This parameter has been deprecated.</span></span> <span data-ttu-id="9d558-409">Vanaf PowerShell 6.0.0 gebruiken alle webaanvragen alleen basisparsering.</span><span class="sxs-lookup"><span data-stu-id="9d558-409">Beginning with PowerShell 6.0.0, all Web requests use basic parsing only.</span></span> <span data-ttu-id="9d558-410">Deze parameter is alleen opgenomen voor achterwaartse compatibiliteit en elk gebruik ervan heeft geen invloed op de werking van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9d558-410">This parameter is included for backwards compatibility only and any use of it will have no effect on the operation of the cmdlet.</span></span>

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

### <span data-ttu-id="9d558-411">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="9d558-411">-UseDefaultCredentials</span></span>

<span data-ttu-id="9d558-412">Geeft aan dat de cmdlet de referenties van de huidige gebruiker gebruikt om de webaanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="9d558-412">Indicates that the cmdlet uses the credentials of the current user to send the web request.</span></span> <span data-ttu-id="9d558-413">Dit kan niet worden gebruikt met **verificatie of** **referentie** en wordt mogelijk niet ondersteund op alle platforms.</span><span class="sxs-lookup"><span data-stu-id="9d558-413">This can't be used with **Authentication** or **Credential** and may not be supported on all platforms.</span></span>

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

### <span data-ttu-id="9d558-414">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="9d558-414">-UserAgent</span></span>

<span data-ttu-id="9d558-415">Hiermee geeft u een tekenreeks voor de gebruikersagent op voor de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="9d558-415">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="9d558-416">De standaardgebruikersagent is vergelijkbaar met `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` met kleine variaties voor elk besturingssysteem en platform.</span><span class="sxs-lookup"><span data-stu-id="9d558-416">The default user agent is similar to `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="9d558-417">Als u een website wilt testen met de standaard tekenreeks van de gebruikersagent die door de meeste internetbrowsers wordt gebruikt, gebruikt u de eigenschappen van de [klasse PSUserAgent,](/dotnet/api/microsoft.powershell.commands.psuseragent) zoals Chrome, FireFox, InternetExplorer, Opera en Safari.</span><span class="sxs-lookup"><span data-stu-id="9d558-417">To test a website with the standard user agent string that is used by most internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span>

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

### <span data-ttu-id="9d558-418">-WebSession</span><span class="sxs-lookup"><span data-stu-id="9d558-418">-WebSession</span></span>

<span data-ttu-id="9d558-419">Hiermee geeft u een webaanvraagsessie.</span><span class="sxs-lookup"><span data-stu-id="9d558-419">Specifies a web request session.</span></span> <span data-ttu-id="9d558-420">Voer de naam van de variabele in, inclusief het dollarteken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="9d558-420">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="9d558-421">Als u een waarde in de webaanvraagsessie wilt overschrijven, gebruikt u een cmdlet-parameter, zoals **UserAgent** of **Credential.**</span><span class="sxs-lookup"><span data-stu-id="9d558-421">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="9d558-422">Parameterwaarden hebben voorrang op waarden in de webaanvraagsessie.</span><span class="sxs-lookup"><span data-stu-id="9d558-422">Parameter values take precedence over values in the web request session.</span></span> <span data-ttu-id="9d558-423">Inhoudsgerelateerde headers, zoals , worden ook overschrijven wanneer een `Content-Type` **MultipartFormDataContent-object** wordt opgegeven voor **Hoofdtekst.**</span><span class="sxs-lookup"><span data-stu-id="9d558-423">Content related headers, such as `Content-Type`, will be also be overridden when a **MultipartFormDataContent** object is supplied for **Body**.</span></span>

<span data-ttu-id="9d558-424">In tegenstelling tot een externe sessie is de webaanvraagsessie geen permanente verbinding.</span><span class="sxs-lookup"><span data-stu-id="9d558-424">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="9d558-425">Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximale omleidingswaarde en de tekenreeks van de gebruikersagent.</span><span class="sxs-lookup"><span data-stu-id="9d558-425">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="9d558-426">U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="9d558-426">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="9d558-427">Als u een webaanvraagsessie wilt maken, voert u een variabelenaam in, zonder dollarteken, in de waarde van de parameter **SessionVariable** van een `Invoke-RestMethod` opdracht.</span><span class="sxs-lookup"><span data-stu-id="9d558-427">To create a web request session, enter a variable name, without a dollar sign, in the value of the **SessionVariable** parameter of an `Invoke-RestMethod` command.</span></span> <span data-ttu-id="9d558-428">`Invoke-RestMethod` maakt de sessie en slaat deze op in de variabele .</span><span class="sxs-lookup"><span data-stu-id="9d558-428">`Invoke-RestMethod` creates the session and saves it in the variable.</span></span> <span data-ttu-id="9d558-429">In volgende opdrachten gebruikt u de variabele als de waarde van de parameter **WebSession.**</span><span class="sxs-lookup"><span data-stu-id="9d558-429">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="9d558-430">U kunt de parameters **SessionVariable en** **WebSession** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="9d558-430">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="9d558-431">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9d558-431">CommonParameters</span></span>

<span data-ttu-id="9d558-432">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9d558-432">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9d558-433">Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9d558-433">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9d558-434">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="9d558-434">Inputs</span></span>

### <span data-ttu-id="9d558-435">System.Object</span><span class="sxs-lookup"><span data-stu-id="9d558-435">System.Object</span></span>

<span data-ttu-id="9d558-436">U kunt de body van een webaanvraag doorseen naar `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="9d558-436">You can pipe the body of a web request to `Invoke-RestMethod`.</span></span>

## <span data-ttu-id="9d558-437">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="9d558-437">Outputs</span></span>

### <span data-ttu-id="9d558-438">System.Int64, System.String, System.Xml.XmlDocument</span><span class="sxs-lookup"><span data-stu-id="9d558-438">System.Int64, System.String, System.Xml.XmlDocument</span></span>

<span data-ttu-id="9d558-439">De uitvoer van de cmdlet is afhankelijk van de indeling van de inhoud die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9d558-439">The output of the cmdlet depends upon the format of the content that is retrieved.</span></span>

### <span data-ttu-id="9d558-440">PSObject</span><span class="sxs-lookup"><span data-stu-id="9d558-440">PSObject</span></span>

<span data-ttu-id="9d558-441">Als de aanvraag JSON-tekenreeksen retourneert, `Invoke-RestMethod` retourneert een **PSObject** dat de tekenreeksen vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="9d558-441">If the request returns JSON strings, `Invoke-RestMethod` returns a **PSObject** that represents the strings.</span></span>

## <span data-ttu-id="9d558-442">Notities</span><span class="sxs-lookup"><span data-stu-id="9d558-442">Notes</span></span>

<span data-ttu-id="9d558-443">Sommige functies zijn mogelijk niet op alle platforms beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="9d558-443">Some features may not be available on all platforms.</span></span>

<span data-ttu-id="9d558-444">Vanwege wijzigingen in .NET Core 3.1 gebruikt PowerShell 7.0 en hoger de eigenschap [HttpClient.DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) om de proxyconfiguratie te bepalen.</span><span class="sxs-lookup"><span data-stu-id="9d558-444">Because of changes in .NET Core 3.1, PowerShell 7.0 and higher use the [HttpClient.DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) property to determine the proxy configuration.</span></span>

<span data-ttu-id="9d558-445">De waarde van deze eigenschap wordt bepaald door uw platform:</span><span class="sxs-lookup"><span data-stu-id="9d558-445">The value of this property is determined by your platform:</span></span>

- <span data-ttu-id="9d558-446">**Voor Windows:** leest proxyconfiguratie uit omgevingsvariabelen.</span><span class="sxs-lookup"><span data-stu-id="9d558-446">**For Windows**: Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="9d558-447">Als deze variabelen niet zijn gedefinieerd, wordt de eigenschap afgeleid van de proxy-instellingen van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="9d558-447">If those variables are not defined the property is derived from the user's proxy settings.</span></span>
- <span data-ttu-id="9d558-448">**Voor macOS:** leest proxyconfiguratie uit omgevingsvariabelen.</span><span class="sxs-lookup"><span data-stu-id="9d558-448">**For macOS**: Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="9d558-449">Als deze variabelen niet zijn gedefinieerd, wordt de eigenschap afgeleid van de proxy-instellingen van het systeem.</span><span class="sxs-lookup"><span data-stu-id="9d558-449">If those variables are not defined the property is derived from the system's proxy settings.</span></span>
- <span data-ttu-id="9d558-450">**Voor Linux:** leest proxyconfiguratie uit omgevingsvariabelen.</span><span class="sxs-lookup"><span data-stu-id="9d558-450">**For Linux**: Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="9d558-451">Als deze variabelen niet zijn gedefinieerd, initialiseert de eigenschap een niet-geconfigureerd exemplaar dat alle adressen omzeilt.</span><span class="sxs-lookup"><span data-stu-id="9d558-451">If those variables are not defined the property initializes a non-configured instance that bypasses all addresses.</span></span>

<span data-ttu-id="9d558-452">De omgevingsvariabelen die worden `DefaultProxy` gebruikt voor initialisatie op Windows- en Unix-platforms zijn:</span><span class="sxs-lookup"><span data-stu-id="9d558-452">The environment variables used for `DefaultProxy` initialization on Windows and Unix-based platforms are:</span></span>

- <span data-ttu-id="9d558-453">`HTTP_PROXY`: de hostnaam of het IP-adres van de proxyserver die wordt gebruikt voor HTTP-aanvragen.</span><span class="sxs-lookup"><span data-stu-id="9d558-453">`HTTP_PROXY`: the hostname or IP address of the proxy server used on HTTP requests.</span></span>
- <span data-ttu-id="9d558-454">`HTTPS_PROXY`: de hostnaam of het IP-adres van de proxyserver die wordt gebruikt voor HTTPS-aanvragen.</span><span class="sxs-lookup"><span data-stu-id="9d558-454">`HTTPS_PROXY`: the hostname or IP address of the proxy server used on HTTPS requests.</span></span>
- <span data-ttu-id="9d558-455">`ALL_PROXY`: de hostnaam of het IP-adres van de proxyserver die wordt gebruikt voor HTTP- en HTTPS-aanvragen voor het geval `HTTP_PROXY` of `HTTPS_PROXY` niet zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="9d558-455">`ALL_PROXY`: the hostname or IP address of the proxy server used on HTTP and HTTPS requests in case `HTTP_PROXY` or `HTTPS_PROXY` are not defined.</span></span>
- <span data-ttu-id="9d558-456">`NO_PROXY`: een door komma's gescheiden lijst met hostnamen die moeten worden uitgesloten van proxying.</span><span class="sxs-lookup"><span data-stu-id="9d558-456">`NO_PROXY`: a comma-separated list of hostnames that should be excluded from proxying.</span></span>

## <span data-ttu-id="9d558-457">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="9d558-457">Related Links</span></span>

[<span data-ttu-id="9d558-458">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="9d558-458">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="9d558-459">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="9d558-459">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="9d558-460">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="9d558-460">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)
