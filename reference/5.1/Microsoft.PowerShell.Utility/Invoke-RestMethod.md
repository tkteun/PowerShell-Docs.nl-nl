---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/05/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-RestMethod
ms.openlocfilehash: 916c221a4fb0886494a4632e38f25a639d5d414e
ms.sourcegitcommit: d95a7255f6775b2973aa9473611185a5583881ff
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106555504"
---
# <span data-ttu-id="da855-103">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="da855-103">Invoke-RestMethod</span></span>

## <span data-ttu-id="da855-104">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="da855-104">Synopsis</span></span>
<span data-ttu-id="da855-105">Hiermee verzendt u een HTTP-of HTTPS-aanvraag naar een REST webservice.</span><span class="sxs-lookup"><span data-stu-id="da855-105">Sends an HTTP or HTTPS request to a RESTful web service.</span></span>

## <span data-ttu-id="da855-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="da855-106">Syntax</span></span>

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-CertificateThumbprint <String>] [-Certificate <X509Certificate>]
 [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>] [-Headers <IDictionary>]
 [-MaximumRedirection <Int32>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials]
 [-Body <Object>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>]
 [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="da855-107">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="da855-107">Description</span></span>

<span data-ttu-id="da855-108">De `Invoke-RestMethod` cmdlet verzendt HTTP-en HTTPS-aanvragen voor het representatief-webservices (rest) voor het retour neren van gegevens die Rich structured data worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="da855-108">The `Invoke-RestMethod` cmdlet sends HTTP and HTTPS requests to Representational State Transfer (REST) web services that returns richly structured data.</span></span>

<span data-ttu-id="da855-109">Windows Power shell formatteert de reactie op basis van het gegevens type.</span><span class="sxs-lookup"><span data-stu-id="da855-109">Windows PowerShell formats the response based to the data type.</span></span> <span data-ttu-id="da855-110">Voor een RSS-of ATOM-feed retourneert Windows Power shell het item of de XML-knoop punten van de vermelding.</span><span class="sxs-lookup"><span data-stu-id="da855-110">For an RSS or ATOM feed, Windows PowerShell returns the Item or Entry XML nodes.</span></span> <span data-ttu-id="da855-111">Voor JavaScript Object Notation (JSON) of XML, wordt de inhoud door Windows Power shell geconverteerd (of gedeserialiseerd) naar objecten.</span><span class="sxs-lookup"><span data-stu-id="da855-111">For JavaScript Object Notation (JSON) or XML, Windows PowerShell converts (or deserializes) the content into objects.</span></span>

<span data-ttu-id="da855-112">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="da855-112">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="da855-113">Standaard kan script code op de webpagina worden uitgevoerd wanneer de pagina wordt geparseerd om de eigenschap in te vullen `ParsedHtml` .</span><span class="sxs-lookup"><span data-stu-id="da855-113">By default, script code in the web page may be run when the page is being parsed to populate the `ParsedHtml` property.</span></span> <span data-ttu-id="da855-114">Gebruik de schakel optie **UseBasicParsing** om dit te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="da855-114">Use the **UseBasicParsing** switch to suppress this.</span></span>

## <span data-ttu-id="da855-115">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="da855-115">Examples</span></span>

### <span data-ttu-id="da855-116">Voor beeld 1: de Power shell-RSS-feed ophalen</span><span class="sxs-lookup"><span data-stu-id="da855-116">Example 1: Get the PowerShell RSS feed</span></span>

```powershell
Invoke-RestMethod -Uri https://devblogs.microsoft.com/powershell/feed/ |
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

<span data-ttu-id="da855-117">Met deze opdracht wordt de `Invoke-RestMethod` cmdlet gebruikt om informatie op te halen uit de RSS-feed voor het Power shell-blog.</span><span class="sxs-lookup"><span data-stu-id="da855-117">This command uses the `Invoke-RestMethod` cmdlet to get information from the PowerShell Blog RSS feed.</span></span> <span data-ttu-id="da855-118">De opdracht gebruikt de `Format-Table` cmdlet om de waarden van de eigenschappen **title** en **pubDate** van elke blog in een tabel weer te geven.</span><span class="sxs-lookup"><span data-stu-id="da855-118">The command uses the `Format-Table` cmdlet to display the values of the **Title** and **pubDate** properties of each blog in a table.</span></span>

### <span data-ttu-id="da855-119">Voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="da855-119">Example 2</span></span>

<span data-ttu-id="da855-120">In het volgende voor beeld wordt een gebruiker uitgevoerd `Invoke-RestMethod` om een post-aanvraag uit te voeren op een intranet website in de organisatie van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="da855-120">In the following example, a user runs `Invoke-RestMethod` to perform a POST request on an intranet website in the user's organization.</span></span>

```powershell
$Cred = Get-Credential

# Next, allow the use of self-signed SSL certificates.

[System.Net.ServicePointManager]::ServerCertificateValidationCallback = { $True }

# Create variables to store the values consumed by the Invoke-RestMethod command.
# The search variable contents are later embedded in the body variable.

$Server = 'server.contoso.com'
$Url = "https://${server}:8089/services/search/jobs/export"
$Search = "search index=_internal | reverse | table index,host,source,sourcetype,_raw"

# The cmdlet handles URL encoding. The body variable describes the search criteria, specifies CSV as
# the output mode, and specifies a time period for returned data that starts two days ago and ends
# one day ago. The body variable specifies values for parameters that apply to the particular REST
# API with which Invoke-RestMethod is communicating.

$Body = @{
    search = $Search
    output_mode = "csv"
    earliest_time = "-2d@d"
    latest_time = "-1d@d"
}

# Now, run the Invoke-RestMethod command with all variables in place, specifying a path and file
# name for the resulting CSV output file.

Invoke-RestMethod -Method Post -Uri $url -Credential $Cred -Body $body -OutFile output.csv

{"preview":true,"offset":0,"result":{"sourcetype":"contoso1","count":"9624"}}

{"preview":true,"offset":1,"result":{"sourcetype":"contoso2","count":"152"}}

{"preview":true,"offset":2,"result":{"sourcetype":"contoso3","count":"88494"}}

{"preview":true,"offset":3,"result":{"sourcetype":"contoso4","count":"15277"}}
```

### <span data-ttu-id="da855-121">Voor beeld 3: meerdere headers door geven</span><span class="sxs-lookup"><span data-stu-id="da855-121">Example 3: Pass multiple headers</span></span>

<span data-ttu-id="da855-122">In dit voor beeld ziet u hoe u meerdere headers kunt door geven van een- `hash-table` naar-rest API.</span><span class="sxs-lookup"><span data-stu-id="da855-122">This example demonstrates, how to pass multiple headers in from a `hash-table` to a REST API.</span></span>

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

<span data-ttu-id="da855-123">Api's vereisen vaak door gegeven headers voor verificatie, validatie, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="da855-123">APIs often require passed headers for authentication, validation etc.</span></span>

### <span data-ttu-id="da855-124">Voor beeld 3: formulier gegevens verzenden</span><span class="sxs-lookup"><span data-stu-id="da855-124">Example 3: Submitting form data</span></span>

<span data-ttu-id="da855-125">Wanneer de hoofd tekst een formulier is of de uitvoer van een andere `Invoke-WebRequest` aanroep, stelt Power shell de aanvraag inhoud in op de formulier velden.</span><span class="sxs-lookup"><span data-stu-id="da855-125">When the body is a form, or it is the output of another `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>

<span data-ttu-id="da855-126">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="da855-126">For example:</span></span>

```powershell
$R = Invoke-WebRequest https://website.com/login.aspx
$R.Forms[0].Name = "MyName"
$R.Forms[0].Password = "MyPassword"
Invoke-RestMethod https://website.com/service.aspx -Body $R.Forms[0]
```

## <span data-ttu-id="da855-127">Parameters</span><span class="sxs-lookup"><span data-stu-id="da855-127">Parameters</span></span>

### <span data-ttu-id="da855-128">-Hoofd tekst</span><span class="sxs-lookup"><span data-stu-id="da855-128">-Body</span></span>

<span data-ttu-id="da855-129">Hiermee geeft u de hoofd tekst van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="da855-129">Specifies the body of the request.</span></span> <span data-ttu-id="da855-130">De hoofd tekst is de inhoud van de aanvraag die de headers volgt.</span><span class="sxs-lookup"><span data-stu-id="da855-130">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="da855-131">U kunt ook de waarde van een hoofd tekst sluist naar `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="da855-131">You can also pipe a body value to `Invoke-RestMethod`.</span></span>

<span data-ttu-id="da855-132">De para meter **Body** kan worden gebruikt om een lijst met query parameters op te geven of de inhoud van het antwoord op te geven.</span><span class="sxs-lookup"><span data-stu-id="da855-132">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="da855-133">Wanneer de invoer een GET-aanvraag is en de hoofd tekst een IDictionary is (meestal een hash-tabel), wordt de hoofd tekst als query parameters toegevoegd aan de URI.</span><span class="sxs-lookup"><span data-stu-id="da855-133">When the input is a GET request, and the body is an IDictionary (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="da855-134">Voor andere aanvraag typen (zoals POST) wordt de hoofd tekst ingesteld als de waarde van de aanvraag tekst in de notatie standaard naam = waarde.</span><span class="sxs-lookup"><span data-stu-id="da855-134">For other request types (such as POST), the body is set as the value of the request body in the standard name=value format.</span></span>

> [!WARNING]
> <span data-ttu-id="da855-135">De uitgebreide uitvoer van een POST hoofdtekst eindigt met, hoewel `with -1-byte payload` de hoofd tekst zowel bekend als in de `Content-Length` http-header wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="da855-135">The verbose output of a POST body will end with `with -1-byte payload`, even though the size of the body is both known and sent in the `Content-Length` HTTP header.</span></span>

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

### <span data-ttu-id="da855-136">-Certificaat</span><span class="sxs-lookup"><span data-stu-id="da855-136">-Certificate</span></span>

<span data-ttu-id="da855-137">Hiermee geeft u het client certificaat op dat wordt gebruikt voor een beveiligde webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="da855-137">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="da855-138">Voer een variabele in die een certificaat of een opdracht of expressie bevat waarmee het certificaat wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="da855-138">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="da855-139">Als u een certificaat wilt zoeken, gebruikt `Get-PfxCertificate` of gebruikt u de `Get-ChildItem` cmdlet in het certificaat `Cert:` station.</span><span class="sxs-lookup"><span data-stu-id="da855-139">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="da855-140">Als het certificaat ongeldig is of niet voldoende autoriteit heeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="da855-140">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="da855-141">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="da855-141">-CertificateThumbprint</span></span>

<span data-ttu-id="da855-142">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat gemachtigd is om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="da855-142">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="da855-143">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="da855-143">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="da855-144">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="da855-144">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="da855-145">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="da855-145">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="da855-146">Gebruik de `Get-Item` `Get-ChildItem` opdracht of in het Windows Power Shell-station () om een certificaat vingerafdruk te verkrijgen `Cert:` .</span><span class="sxs-lookup"><span data-stu-id="da855-146">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the Windows PowerShell (`Cert:`) drive.</span></span>

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

### <span data-ttu-id="da855-147">-Content type</span><span class="sxs-lookup"><span data-stu-id="da855-147">-ContentType</span></span>

<span data-ttu-id="da855-148">Hiermee geeft u het type inhoud van de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="da855-148">Specifies the content type of the web request.</span></span>

<span data-ttu-id="da855-149">Als deze para meter wordt wegge laten en de aanvraag methode is `Invoke-RestMethod` ingesteld op post, stelt het inhouds type in op ' Application/x-www-form-urlencoded '.</span><span class="sxs-lookup"><span data-stu-id="da855-149">If this parameter is omitted and the request method is POST, `Invoke-RestMethod` sets the content type to "application/x-www-form-urlencoded".</span></span> <span data-ttu-id="da855-150">Anders is het inhouds type niet opgegeven in de aanroep.</span><span class="sxs-lookup"><span data-stu-id="da855-150">Otherwise, the content type is not specified in the call.</span></span>

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

### <span data-ttu-id="da855-151">-Credential</span><span class="sxs-lookup"><span data-stu-id="da855-151">-Credential</span></span>

<span data-ttu-id="da855-152">Hiermee geeft u een gebruikers account op dat gemachtigd is om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="da855-152">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="da855-153">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="da855-153">The default is the current user.</span></span>

<span data-ttu-id="da855-154">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**, of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="da855-154">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="da855-155">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="da855-155">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="da855-156">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="da855-156">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="da855-157">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="da855-157">-DisableKeepAlive</span></span>

<span data-ttu-id="da855-158">Hiermee stelt u de **keepalive** -waarde in de http-header in op ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="da855-158">Sets the **KeepAlive** value in the HTTP header to False.</span></span> <span data-ttu-id="da855-159">Standaard is **keepalive** ingesteld op True.</span><span class="sxs-lookup"><span data-stu-id="da855-159">By default, **KeepAlive** is True.</span></span>
<span data-ttu-id="da855-160">Met **keepalive** wordt een permanente verbinding met de server tot stand gebracht om volgende aanvragen te vergemakkelijken.</span><span class="sxs-lookup"><span data-stu-id="da855-160">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: KeepAlive
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="da855-161">-Headers</span><span class="sxs-lookup"><span data-stu-id="da855-161">-Headers</span></span>

<span data-ttu-id="da855-162">Hiermee geeft u de kopteksten van de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="da855-162">Specifies the headers of the web request.</span></span> <span data-ttu-id="da855-163">Voer een hash-tabel of-woorden lijst in.</span><span class="sxs-lookup"><span data-stu-id="da855-163">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="da855-164">Gebruik de **agent** -para meter om de agent headers in te stellen.</span><span class="sxs-lookup"><span data-stu-id="da855-164">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="da855-165">U kunt deze para meter niet gebruiken om de headers van User agent of cookie op te geven.</span><span class="sxs-lookup"><span data-stu-id="da855-165">You cannot use this parameter to specify UserAgent or cookie headers.</span></span>

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

### <span data-ttu-id="da855-166">-Inbestand</span><span class="sxs-lookup"><span data-stu-id="da855-166">-InFile</span></span>

<span data-ttu-id="da855-167">Hiermee wordt de inhoud van de webaanvraag opgehaald uit een bestand.</span><span class="sxs-lookup"><span data-stu-id="da855-167">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="da855-168">Voer een pad en een bestands naam in.</span><span class="sxs-lookup"><span data-stu-id="da855-168">Enter a path and file name.</span></span> <span data-ttu-id="da855-169">Als u het pad weglaat, de standaard instelling is de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="da855-169">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="da855-170">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="da855-170">-MaximumRedirection</span></span>

<span data-ttu-id="da855-171">Bepaalt hoe vaak Windows Power shell een verbinding met een alternatieve URI (Uniform Resource Identifier) omleidt voordat de verbinding is mislukt.</span><span class="sxs-lookup"><span data-stu-id="da855-171">Determines how many times Windows PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="da855-172">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="da855-172">The default value is 5.</span></span> <span data-ttu-id="da855-173">Een waarde van 0 (nul) voor komt dat alle omleidingen.</span><span class="sxs-lookup"><span data-stu-id="da855-173">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="da855-174">-Methode</span><span class="sxs-lookup"><span data-stu-id="da855-174">-Method</span></span>

<span data-ttu-id="da855-175">Hiermee geeft u de methode op die voor de webaanvraag wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="da855-175">Specifies the method used for the web request.</span></span> <span data-ttu-id="da855-176">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="da855-176">The acceptable values for this parameter are:</span></span>

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

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestMethod
Parameter Sets: (All)
Aliases:
Accepted values: Default, Get, Head, Post, Put, Delete, Trace, Options, Merge, Patch

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="da855-177">-Outfile</span><span class="sxs-lookup"><span data-stu-id="da855-177">-OutFile</span></span>

<span data-ttu-id="da855-178">Hiermee wordt de antwoord tekst in het opgegeven uitvoer bestand opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="da855-178">Saves the response body in the specified output file.</span></span> <span data-ttu-id="da855-179">Voer een pad en een bestands naam in.</span><span class="sxs-lookup"><span data-stu-id="da855-179">Enter a path and file name.</span></span> <span data-ttu-id="da855-180">Als u het pad weglaat, de standaard instelling is de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="da855-180">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="da855-181">`Invoke-RestMethod`De resultaten worden standaard naar de pijp lijn geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="da855-181">By default, `Invoke-RestMethod` returns the results to the pipeline.</span></span> <span data-ttu-id="da855-182">Als u de resultaten naar een bestand en naar de pijp lijn wilt verzenden, gebruikt u de para meter **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="da855-182">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="da855-183">-PassThru</span><span class="sxs-lookup"><span data-stu-id="da855-183">-PassThru</span></span>

<span data-ttu-id="da855-184">Hiermee worden de resultaten geretourneerd, naast het schrijven naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="da855-184">Returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="da855-185">Deze para meter is alleen geldig wanneer de **outfile** -para meter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="da855-185">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="da855-186">-Proxy</span><span class="sxs-lookup"><span data-stu-id="da855-186">-Proxy</span></span>

<span data-ttu-id="da855-187">Maakt gebruik van een proxy server voor de aanvraag, in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="da855-187">Uses a proxy server for the request, rather than connecting directly to the Internet resource.</span></span> <span data-ttu-id="da855-188">Voer de URI van een netwerk proxy server in.</span><span class="sxs-lookup"><span data-stu-id="da855-188">Enter the URI of a network proxy server.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="da855-189">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="da855-189">-ProxyCredential</span></span>

<span data-ttu-id="da855-190">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="da855-190">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="da855-191">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="da855-191">The default is the current user.</span></span>

<span data-ttu-id="da855-192">Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="da855-192">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="da855-193">Deze para meter is alleen geldig wanneer de **proxy** parameter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="da855-193">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="da855-194">U kunt de para meters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="da855-194">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="da855-195">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="da855-195">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="da855-196">Gebruikt de referenties van de huidige gebruiker om toegang te krijgen tot de proxy server die is opgegeven door de **proxy** -para meter.</span><span class="sxs-lookup"><span data-stu-id="da855-196">Uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="da855-197">Deze para meter is alleen geldig wanneer de **proxy** parameter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="da855-197">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="da855-198">U kunt de para meters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="da855-198">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="da855-199">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="da855-199">-SessionVariable</span></span>

<span data-ttu-id="da855-200">Hiermee maakt u een web Request-sessie en slaat u deze op in de waarde van de opgegeven variabele.</span><span class="sxs-lookup"><span data-stu-id="da855-200">Creates a web request session and saves it in the value of the specified variable.</span></span> <span data-ttu-id="da855-201">Geef een naam op voor de variabele zonder het dollar teken ( `$` )-symbool.</span><span class="sxs-lookup"><span data-stu-id="da855-201">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="da855-202">Wanneer u een sessie variabele opgeeft, `Invoke-RestMethod` maakt een webaanvraag sessie object en wijst deze toe aan een variabele met de opgegeven naam in uw Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="da855-202">When you specify a session variable, `Invoke-RestMethod` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="da855-203">U kunt de variabele in uw sessie gebruiken zodra de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="da855-203">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="da855-204">In tegens telling tot een externe sessie is de sessie voor webaanvragen geen permanente verbinding.</span><span class="sxs-lookup"><span data-stu-id="da855-204">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="da855-205">Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximum omleidings waarde en de teken reeks van de gebruikers agent.</span><span class="sxs-lookup"><span data-stu-id="da855-205">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="da855-206">U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="da855-206">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="da855-207">Als u de webaanvraag sessie in volgende webaanvragen wilt gebruiken, geeft u de sessie variabele op in de waarde van de para meter **websessie** .</span><span class="sxs-lookup"><span data-stu-id="da855-207">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="da855-208">Windows Power shell gebruikt de gegevens in het sessie object voor webaanvragen wanneer de nieuwe verbinding tot stand wordt gebracht.</span><span class="sxs-lookup"><span data-stu-id="da855-208">Windows PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="da855-209">Als u een waarde in de sessie voor webaanvragen wilt overschrijven, gebruikt u een cmdlet-para meter, zoals **User agent** of **Credential**.</span><span class="sxs-lookup"><span data-stu-id="da855-209">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="da855-210">Parameter waarden hebben prioriteit boven waarden in de webaanvraag sessie.</span><span class="sxs-lookup"><span data-stu-id="da855-210">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="da855-211">U kunt de para meters **SessionVariable** en **websession** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="da855-211">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="da855-212">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="da855-212">-TimeoutSec</span></span>

<span data-ttu-id="da855-213">Hiermee geeft u op hoe lang de aanvraag in behandeling kan zijn voordat er een time-out optreedt. Voer een waarde in seconden in.</span><span class="sxs-lookup"><span data-stu-id="da855-213">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="da855-214">De standaard waarde, 0, geeft een onbeperkte time-outwaarde.</span><span class="sxs-lookup"><span data-stu-id="da855-214">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="da855-215">Het kan tot vijf tien seconden duren voordat een Domain Name System query (DNS) wordt uitgevoerd of een time-out kan worden geretourneerd. Als uw aanvraag een hostnaam bevat waarvoor omzetting vereist is en u TimeoutSec instelt op een waarde die groter is dan nul, maar minder dan 15 seconden, kan het vijf tien seconden of langer duren voordat een webuitzondering wordt gegenereerd en er een time-out optreedt voor uw aanvraag.</span><span class="sxs-lookup"><span data-stu-id="da855-215">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set TimeoutSec to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="da855-216">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="da855-216">-TransferEncoding</span></span>

<span data-ttu-id="da855-217">Hiermee geeft u een waarde op voor de header van de HTTP-reactie voor overdracht/versleuteling.</span><span class="sxs-lookup"><span data-stu-id="da855-217">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="da855-218">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="da855-218">The acceptable values for this parameter are:</span></span>

- `Chunked`
- `Compress`
- `Deflate`
- `GZip`
- `Identity`

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

### <span data-ttu-id="da855-219">-URI</span><span class="sxs-lookup"><span data-stu-id="da855-219">-Uri</span></span>

<span data-ttu-id="da855-220">Hiermee geeft u de URI (Uniform Resource Identifier) op van de Internet bron waarnaar de webaanvraag wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="da855-220">Specifies the Uniform Resource Identifier (URI) of the Internet resource to which the web request is sent.</span></span> <span data-ttu-id="da855-221">Deze para meter ondersteunt HTTP-, HTTPS-, FTP-en FILE-waarden.</span><span class="sxs-lookup"><span data-stu-id="da855-221">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="da855-222">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="da855-222">This parameter is required.</span></span> <span data-ttu-id="da855-223">De parameter naam (**URI**) is optioneel.</span><span class="sxs-lookup"><span data-stu-id="da855-223">The parameter name (**Uri**) is optional.</span></span>

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

### <span data-ttu-id="da855-224">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="da855-224">-UseBasicParsing</span></span>

<span data-ttu-id="da855-225">Geeft aan dat de cmdlet gebruikmaakt van basis parsering.</span><span class="sxs-lookup"><span data-stu-id="da855-225">Indicates that the cmdlet uses basic parsing.</span></span> <span data-ttu-id="da855-226">De cmdlet retourneert de onbewerkte HTML in een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="da855-226">The cmdlet returns the raw HTML in a **String** object.</span></span>

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

### <span data-ttu-id="da855-227">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="da855-227">-UseDefaultCredentials</span></span>

<span data-ttu-id="da855-228">Gebruikt de referenties van de huidige gebruiker om de webaanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="da855-228">Uses the credentials of the current user to send the web request.</span></span>

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

### <span data-ttu-id="da855-229">-User agent</span><span class="sxs-lookup"><span data-stu-id="da855-229">-UserAgent</span></span>

<span data-ttu-id="da855-230">Hiermee geeft u een teken reeks voor de gebruikers agent op voor de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="da855-230">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="da855-231">De standaard gebruikers agent is vergelijkbaar met ' Mozilla/5.0 ' (Windows NT; Windows NT 6,1; en-US) WindowsPowerShell/3.0 ' met kleine variaties voor elk besturings systeem en platform.</span><span class="sxs-lookup"><span data-stu-id="da855-231">The default user agent is similar to "Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0" with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="da855-232">Als u een website wilt testen met de standaard teken reeks van de gebruikers agent die wordt gebruikt door de meeste Internet browsers, gebruikt u de eigenschappen van de [PSUserAgent](/dotnet/api/microsoft.powershell.commands) -klasse, zoals Chrome, Firefox, Internet Explorer, Opera en Safari.</span><span class="sxs-lookup"><span data-stu-id="da855-232">To test a website with the standard user agent string that is used by most Internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands) class, such as Chrome, FireFox, Internet Explorer, Opera, and Safari.</span></span>

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

### <span data-ttu-id="da855-233">-Websessie</span><span class="sxs-lookup"><span data-stu-id="da855-233">-WebSession</span></span>

<span data-ttu-id="da855-234">Hiermee geeft u een sessie voor webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="da855-234">Specifies a web request session.</span></span> <span data-ttu-id="da855-235">Voer de naam van de variabele in, met inbegrip van het dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="da855-235">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="da855-236">Als u een waarde in de sessie voor webaanvragen wilt overschrijven, gebruikt u een cmdlet-para meter, zoals **User agent** of **Credential**.</span><span class="sxs-lookup"><span data-stu-id="da855-236">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="da855-237">Parameter waarden hebben prioriteit boven waarden in de webaanvraag sessie.</span><span class="sxs-lookup"><span data-stu-id="da855-237">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="da855-238">In tegens telling tot een externe sessie is de sessie voor webaanvragen geen permanente verbinding.</span><span class="sxs-lookup"><span data-stu-id="da855-238">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="da855-239">Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximum omleidings waarde en de teken reeks van de gebruikers agent.</span><span class="sxs-lookup"><span data-stu-id="da855-239">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="da855-240">U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="da855-240">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="da855-241">Als u een webaanvraag sessie wilt maken, voert u een naam in voor de variabele (zonder een dollar teken) in de waarde van de para meter **SessionVariable** van een `Invoke-RestMethod` opdracht.</span><span class="sxs-lookup"><span data-stu-id="da855-241">To create a web request session, enter a variable name (without a dollar sign) in the value of the **SessionVariable** parameter of an `Invoke-RestMethod` command.</span></span> <span data-ttu-id="da855-242">`Invoke-RestMethod` Hiermee maakt u de sessie en slaat u deze op in de variabele.</span><span class="sxs-lookup"><span data-stu-id="da855-242">`Invoke-RestMethod` creates the session and saves it in the variable.</span></span> <span data-ttu-id="da855-243">Gebruik in volgende opdrachten de variabele als de waarde van de para meter **websession** .</span><span class="sxs-lookup"><span data-stu-id="da855-243">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="da855-244">U kunt de para meters **SessionVariable** en **websession** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="da855-244">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="da855-245">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="da855-245">CommonParameters</span></span>

<span data-ttu-id="da855-246">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="da855-246">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="da855-247">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="da855-247">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="da855-248">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="da855-248">Inputs</span></span>

### <span data-ttu-id="da855-249">System. object</span><span class="sxs-lookup"><span data-stu-id="da855-249">System.Object</span></span>

<span data-ttu-id="da855-250">U kunt de hoofd tekst van een webaanvraag door sluizen naar `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="da855-250">You can pipe the body of a web request to `Invoke-RestMethod`.</span></span>

## <span data-ttu-id="da855-251">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="da855-251">Outputs</span></span>

### <span data-ttu-id="da855-252">System.Xml.Xmldocument, Microsoft.PowerShell.Commands.HtmlWebResponseObject, System. String</span><span class="sxs-lookup"><span data-stu-id="da855-252">System.Xml.XmlDocument, Microsoft.PowerShell.Commands.HtmlWebResponseObject, System.String</span></span>

<span data-ttu-id="da855-253">De uitvoer van de cmdlet is afhankelijk van de indeling van de inhoud die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="da855-253">The output of the cmdlet depends upon the format of the content that is retrieved.</span></span>

### <span data-ttu-id="da855-254">PSObject</span><span class="sxs-lookup"><span data-stu-id="da855-254">PSObject</span></span>

<span data-ttu-id="da855-255">Als de aanvraag JSON-teken reeksen retourneert, `Invoke-RestMethod` retourneert een PSObject die de teken reeksen vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="da855-255">If the request returns JSON strings, `Invoke-RestMethod` returns a PSObject that represents the strings.</span></span>

## <span data-ttu-id="da855-256">Notities</span><span class="sxs-lookup"><span data-stu-id="da855-256">Notes</span></span>

## <span data-ttu-id="da855-257">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="da855-257">Related Links</span></span>

[<span data-ttu-id="da855-258">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="da855-258">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="da855-259">ConvertFrom-JSON</span><span class="sxs-lookup"><span data-stu-id="da855-259">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="da855-260">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="da855-260">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)
