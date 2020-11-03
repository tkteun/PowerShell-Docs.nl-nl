---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/13/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-RestMethod
ms.openlocfilehash: c89f7351e9c874cea2cc0cd5e0912e3ca0d8b0bf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250406"
---
# <span data-ttu-id="f2d44-103">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="f2d44-103">Invoke-RestMethod</span></span>

## <span data-ttu-id="f2d44-104">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="f2d44-104">Synopsis</span></span>
<span data-ttu-id="f2d44-105">Hiermee verzendt u een HTTP-of HTTPS-aanvraag naar een REST webservice.</span><span class="sxs-lookup"><span data-stu-id="f2d44-105">Sends an HTTP or HTTPS request to a RESTful web service.</span></span>

## <span data-ttu-id="f2d44-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f2d44-106">Syntax</span></span>

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-CertificateThumbprint <String>] [-Certificate <X509Certificate>]
 [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>] [-Headers <IDictionary>]
 [-MaximumRedirection <Int32>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials]
 [-Body <Object>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>]
 [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="f2d44-107">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f2d44-107">Description</span></span>

<span data-ttu-id="f2d44-108">De `Invoke-RestMethod` cmdlet verzendt HTTP-en HTTPS-aanvragen voor het representatief-webservices (rest) voor het retour neren van gegevens die Rich structured data worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f2d44-108">The `Invoke-RestMethod` cmdlet sends HTTP and HTTPS requests to Representational State Transfer (REST) web services that returns richly structured data.</span></span>

<span data-ttu-id="f2d44-109">Windows Power shell formatteert de reactie op basis van het gegevens type.</span><span class="sxs-lookup"><span data-stu-id="f2d44-109">Windows PowerShell formats the response based to the data type.</span></span> <span data-ttu-id="f2d44-110">Voor een RSS-of ATOM-feed retourneert Windows Power shell het item of de XML-knoop punten van de vermelding.</span><span class="sxs-lookup"><span data-stu-id="f2d44-110">For an RSS or ATOM feed, Windows PowerShell returns the Item or Entry XML nodes.</span></span> <span data-ttu-id="f2d44-111">Voor JavaScript Object Notation (JSON) of XML, wordt de inhoud door Windows Power shell geconverteerd (of gedeserialiseerd) naar objecten.</span><span class="sxs-lookup"><span data-stu-id="f2d44-111">For JavaScript Object Notation (JSON) or XML, Windows PowerShell converts (or deserializes) the content into objects.</span></span>

<span data-ttu-id="f2d44-112">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f2d44-112">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="f2d44-113">Standaard kan script code op de webpagina worden uitgevoerd wanneer de pagina wordt geparseerd om de eigenschap in te vullen `ParsedHtml` .</span><span class="sxs-lookup"><span data-stu-id="f2d44-113">By default, script code in the web page may be run when the page is being parsed to populate the `ParsedHtml` property.</span></span> <span data-ttu-id="f2d44-114">Gebruik de schakel optie **UseBasicParsing** om dit te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="f2d44-114">Use the **UseBasicParsing** switch to suppress this.</span></span>

## <span data-ttu-id="f2d44-115">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="f2d44-115">Examples</span></span>

### <span data-ttu-id="f2d44-116">Voor beeld 1: de Power shell-RSS-feed ophalen</span><span class="sxs-lookup"><span data-stu-id="f2d44-116">Example 1: Get the PowerShell RSS feed</span></span>

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

<span data-ttu-id="f2d44-117">Met deze opdracht wordt de `Invoke-RestMethod` cmdlet gebruikt om informatie op te halen uit de RSS-feed voor het Power shell-blog.</span><span class="sxs-lookup"><span data-stu-id="f2d44-117">This command uses the `Invoke-RestMethod` cmdlet to get information from the PowerShell Blog RSS feed.</span></span> <span data-ttu-id="f2d44-118">De opdracht gebruikt de `Format-Table` cmdlet om de waarden van de eigenschappen **title** en **pubDate** van elke blog in een tabel weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f2d44-118">The command uses the `Format-Table` cmdlet to display the values of the **Title** and **pubDate** properties of each blog in a table.</span></span>

### <span data-ttu-id="f2d44-119">Voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="f2d44-119">Example 2</span></span>

<span data-ttu-id="f2d44-120">In het volgende voor beeld wordt een gebruiker uitgevoerd `Invoke-RestMethod` om een post-aanvraag uit te voeren op een intranet website in de organisatie van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f2d44-120">In the following example, a user runs `Invoke-RestMethod` to perform a POST request on an intranet website in the user's organization.</span></span>

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

### <span data-ttu-id="f2d44-121">Voor beeld 3: meerdere headers door geven</span><span class="sxs-lookup"><span data-stu-id="f2d44-121">Example 3: Pass multiple headers</span></span>

<span data-ttu-id="f2d44-122">In dit voor beeld ziet u hoe u meerdere headers kunt door geven van een- `hash-table` naar-rest API.</span><span class="sxs-lookup"><span data-stu-id="f2d44-122">This example demonstrates, how to pass multiple headers in from a `hash-table` to a REST API.</span></span>

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

<span data-ttu-id="f2d44-123">Api's vereisen vaak door gegeven headers voor verificatie, validatie, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="f2d44-123">APIs often require passed headers for authentication, validation etc.</span></span>

### <span data-ttu-id="f2d44-124">Voor beeld 3: formulier gegevens verzenden</span><span class="sxs-lookup"><span data-stu-id="f2d44-124">Example 3: Submitting form data</span></span>

<span data-ttu-id="f2d44-125">Wanneer de hoofd tekst een formulier is of de uitvoer van een andere `Invoke-WebRequest` aanroep, stelt Power shell de aanvraag inhoud in op de formulier velden.</span><span class="sxs-lookup"><span data-stu-id="f2d44-125">When the body is a form, or it is the output of another `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>

<span data-ttu-id="f2d44-126">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f2d44-126">For example:</span></span>

```powershell
$R = Invoke-WebRequest https://website.com/login.aspx
$R.Forms[0].Name = "MyName"
$R.Forms[0].Password = "MyPassword"
Invoke-RestMethod https://website.com/service.aspx -Body $R.Forms[0]
```

## <span data-ttu-id="f2d44-127">Parameters</span><span class="sxs-lookup"><span data-stu-id="f2d44-127">Parameters</span></span>

### <span data-ttu-id="f2d44-128">-Hoofd tekst</span><span class="sxs-lookup"><span data-stu-id="f2d44-128">-Body</span></span>

<span data-ttu-id="f2d44-129">Hiermee geeft u de hoofd tekst van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="f2d44-129">Specifies the body of the request.</span></span> <span data-ttu-id="f2d44-130">De hoofd tekst is de inhoud van de aanvraag die de headers volgt.</span><span class="sxs-lookup"><span data-stu-id="f2d44-130">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="f2d44-131">U kunt ook de waarde van een hoofd tekst sluist naar `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="f2d44-131">You can also pipe a body value to `Invoke-RestMethod`.</span></span>

<span data-ttu-id="f2d44-132">De para meter **Body** kan worden gebruikt om een lijst met query parameters op te geven of de inhoud van het antwoord op te geven.</span><span class="sxs-lookup"><span data-stu-id="f2d44-132">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="f2d44-133">Wanneer de invoer een GET-aanvraag is en de hoofd tekst een IDictionary is (meestal een hash-tabel), wordt de hoofd tekst als query parameters toegevoegd aan de URI.</span><span class="sxs-lookup"><span data-stu-id="f2d44-133">When the input is a GET request, and the body is an IDictionary (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="f2d44-134">Voor andere aanvraag typen (zoals POST) wordt de hoofd tekst ingesteld als de waarde van de aanvraag tekst in de notatie standaard naam = waarde.</span><span class="sxs-lookup"><span data-stu-id="f2d44-134">For other request types (such as POST), the body is set as the value of the request body in the standard name=value format.</span></span>

> [!WARNING]
> <span data-ttu-id="f2d44-135">De uitgebreide uitvoer van een POST hoofdtekst eindigt met, hoewel `with -1-byte payload` de hoofd tekst zowel bekend als in de `Content-Length` http-header wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="f2d44-135">The verbose output of a POST body will end with `with -1-byte payload`, even though the size of the body is both known and sent in the `Content-Length` HTTP header.</span></span>

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

### <span data-ttu-id="f2d44-136">-Certificaat</span><span class="sxs-lookup"><span data-stu-id="f2d44-136">-Certificate</span></span>

<span data-ttu-id="f2d44-137">Hiermee geeft u het client certificaat op dat wordt gebruikt voor een beveiligde webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="f2d44-137">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="f2d44-138">Voer een variabele in die een certificaat of een opdracht of expressie bevat waarmee het certificaat wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f2d44-138">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="f2d44-139">Als u een certificaat wilt zoeken, gebruikt `Get-PfxCertificate` of gebruikt u de `Get-ChildItem` cmdlet in het certificaat `Cert:` station.</span><span class="sxs-lookup"><span data-stu-id="f2d44-139">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="f2d44-140">Als het certificaat ongeldig is of niet voldoende autoriteit heeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="f2d44-140">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="f2d44-141">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="f2d44-141">-CertificateThumbprint</span></span>

<span data-ttu-id="f2d44-142">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat gemachtigd is om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="f2d44-142">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="f2d44-143">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="f2d44-143">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="f2d44-144">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="f2d44-144">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="f2d44-145">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="f2d44-145">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="f2d44-146">Gebruik de `Get-Item` `Get-ChildItem` opdracht of in het Windows Power Shell-station () om een certificaat vingerafdruk te verkrijgen `Cert:` .</span><span class="sxs-lookup"><span data-stu-id="f2d44-146">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the Windows PowerShell (`Cert:`) drive.</span></span>

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

### <span data-ttu-id="f2d44-147">-Content type</span><span class="sxs-lookup"><span data-stu-id="f2d44-147">-ContentType</span></span>

<span data-ttu-id="f2d44-148">Hiermee geeft u het type inhoud van de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="f2d44-148">Specifies the content type of the web request.</span></span>

<span data-ttu-id="f2d44-149">Als deze para meter wordt wegge laten en de aanvraag methode is `Invoke-RestMethod` ingesteld op post, stelt het inhouds type in op ' Application/x-www-form-urlencoded '.</span><span class="sxs-lookup"><span data-stu-id="f2d44-149">If this parameter is omitted and the request method is POST, `Invoke-RestMethod` sets the content type to "application/x-www-form-urlencoded".</span></span> <span data-ttu-id="f2d44-150">Anders is het inhouds type niet opgegeven in de aanroep.</span><span class="sxs-lookup"><span data-stu-id="f2d44-150">Otherwise, the content type is not specified in the call.</span></span>

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

### <span data-ttu-id="f2d44-151">-Credential</span><span class="sxs-lookup"><span data-stu-id="f2d44-151">-Credential</span></span>

<span data-ttu-id="f2d44-152">Hiermee geeft u een gebruikers account op dat gemachtigd is om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="f2d44-152">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="f2d44-153">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f2d44-153">The default is the current user.</span></span>

<span data-ttu-id="f2d44-154">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="f2d44-154">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="f2d44-155">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="f2d44-155">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="f2d44-156">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="f2d44-156">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="f2d44-157">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="f2d44-157">-DisableKeepAlive</span></span>

<span data-ttu-id="f2d44-158">Hiermee stelt u de **keepalive** -waarde in de http-header in op ONWAAR.</span><span class="sxs-lookup"><span data-stu-id="f2d44-158">Sets the **KeepAlive** value in the HTTP header to False.</span></span> <span data-ttu-id="f2d44-159">Standaard is **keepalive** ingesteld op True.</span><span class="sxs-lookup"><span data-stu-id="f2d44-159">By default, **KeepAlive** is True.</span></span>
<span data-ttu-id="f2d44-160">Met **keepalive** wordt een permanente verbinding met de server tot stand gebracht om volgende aanvragen te vergemakkelijken.</span><span class="sxs-lookup"><span data-stu-id="f2d44-160">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="f2d44-161">-Headers</span><span class="sxs-lookup"><span data-stu-id="f2d44-161">-Headers</span></span>

<span data-ttu-id="f2d44-162">Hiermee geeft u de kopteksten van de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="f2d44-162">Specifies the headers of the web request.</span></span> <span data-ttu-id="f2d44-163">Voer een hash-tabel of-woorden lijst in.</span><span class="sxs-lookup"><span data-stu-id="f2d44-163">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="f2d44-164">Gebruik de **agent** -para meter om de agent headers in te stellen.</span><span class="sxs-lookup"><span data-stu-id="f2d44-164">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="f2d44-165">U kunt deze para meter niet gebruiken om de headers van User agent of cookie op te geven.</span><span class="sxs-lookup"><span data-stu-id="f2d44-165">You cannot use this parameter to specify UserAgent or cookie headers.</span></span>

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

### <span data-ttu-id="f2d44-166">-Inbestand</span><span class="sxs-lookup"><span data-stu-id="f2d44-166">-InFile</span></span>

<span data-ttu-id="f2d44-167">Hiermee wordt de inhoud van de webaanvraag opgehaald uit een bestand.</span><span class="sxs-lookup"><span data-stu-id="f2d44-167">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="f2d44-168">Voer een pad en een bestands naam in.</span><span class="sxs-lookup"><span data-stu-id="f2d44-168">Enter a path and file name.</span></span> <span data-ttu-id="f2d44-169">Als u het pad weglaat, de standaard instelling is de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="f2d44-169">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="f2d44-170">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="f2d44-170">-MaximumRedirection</span></span>

<span data-ttu-id="f2d44-171">Bepaalt hoe vaak Windows Power shell een verbinding met een alternatieve URI (Uniform Resource Identifier) omleidt voordat de verbinding is mislukt.</span><span class="sxs-lookup"><span data-stu-id="f2d44-171">Determines how many times Windows PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="f2d44-172">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="f2d44-172">The default value is 5.</span></span> <span data-ttu-id="f2d44-173">Een waarde van 0 (nul) voor komt dat alle omleidingen.</span><span class="sxs-lookup"><span data-stu-id="f2d44-173">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="f2d44-174">-Methode</span><span class="sxs-lookup"><span data-stu-id="f2d44-174">-Method</span></span>

<span data-ttu-id="f2d44-175">Hiermee geeft u de methode op die voor de webaanvraag wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f2d44-175">Specifies the method used for the web request.</span></span> <span data-ttu-id="f2d44-176">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="f2d44-176">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f2d44-177">Standaard</span><span class="sxs-lookup"><span data-stu-id="f2d44-177">Default</span></span>
- <span data-ttu-id="f2d44-178">Verwijderen</span><span class="sxs-lookup"><span data-stu-id="f2d44-178">Delete</span></span>
- <span data-ttu-id="f2d44-179">Ophalen</span><span class="sxs-lookup"><span data-stu-id="f2d44-179">Get</span></span>
- <span data-ttu-id="f2d44-180">Head</span><span class="sxs-lookup"><span data-stu-id="f2d44-180">Head</span></span>
- <span data-ttu-id="f2d44-181">Samenvoegen</span><span class="sxs-lookup"><span data-stu-id="f2d44-181">Merge</span></span>
- <span data-ttu-id="f2d44-182">Opties</span><span class="sxs-lookup"><span data-stu-id="f2d44-182">Options</span></span>
- <span data-ttu-id="f2d44-183">Patch</span><span class="sxs-lookup"><span data-stu-id="f2d44-183">Patch</span></span>
- <span data-ttu-id="f2d44-184">Plaatsen</span><span class="sxs-lookup"><span data-stu-id="f2d44-184">Post</span></span>
- <span data-ttu-id="f2d44-185">Put</span><span class="sxs-lookup"><span data-stu-id="f2d44-185">Put</span></span>
- <span data-ttu-id="f2d44-186">Tracering</span><span class="sxs-lookup"><span data-stu-id="f2d44-186">Trace</span></span>

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

### <span data-ttu-id="f2d44-187">-Outfile</span><span class="sxs-lookup"><span data-stu-id="f2d44-187">-OutFile</span></span>

<span data-ttu-id="f2d44-188">Hiermee wordt de antwoord tekst in het opgegeven uitvoer bestand opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="f2d44-188">Saves the response body in the specified output file.</span></span> <span data-ttu-id="f2d44-189">Voer een pad en een bestands naam in.</span><span class="sxs-lookup"><span data-stu-id="f2d44-189">Enter a path and file name.</span></span> <span data-ttu-id="f2d44-190">Als u het pad weglaat, de standaard instelling is de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="f2d44-190">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="f2d44-191">`Invoke-RestMethod`De resultaten worden standaard naar de pijp lijn geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f2d44-191">By default, `Invoke-RestMethod` returns the results to the pipeline.</span></span> <span data-ttu-id="f2d44-192">Als u de resultaten naar een bestand en naar de pijp lijn wilt verzenden, gebruikt u de para meter **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="f2d44-192">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="f2d44-193">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f2d44-193">-PassThru</span></span>

<span data-ttu-id="f2d44-194">Hiermee worden de resultaten geretourneerd, naast het schrijven naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="f2d44-194">Returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="f2d44-195">Deze para meter is alleen geldig wanneer de **outfile** -para meter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f2d44-195">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="f2d44-196">-Proxy</span><span class="sxs-lookup"><span data-stu-id="f2d44-196">-Proxy</span></span>

<span data-ttu-id="f2d44-197">Maakt gebruik van een proxy server voor de aanvraag, in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="f2d44-197">Uses a proxy server for the request, rather than connecting directly to the Internet resource.</span></span> <span data-ttu-id="f2d44-198">Voer de URI van een netwerk proxy server in.</span><span class="sxs-lookup"><span data-stu-id="f2d44-198">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="f2d44-199">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="f2d44-199">-ProxyCredential</span></span>

<span data-ttu-id="f2d44-200">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="f2d44-200">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="f2d44-201">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f2d44-201">The default is the current user.</span></span>

<span data-ttu-id="f2d44-202">Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f2d44-202">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="f2d44-203">Deze para meter is alleen geldig wanneer de **proxy** parameter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f2d44-203">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="f2d44-204">U kunt de para meters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f2d44-204">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="f2d44-205">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="f2d44-205">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="f2d44-206">Gebruikt de referenties van de huidige gebruiker om toegang te krijgen tot de proxy server die is opgegeven door de **proxy** -para meter.</span><span class="sxs-lookup"><span data-stu-id="f2d44-206">Uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="f2d44-207">Deze para meter is alleen geldig wanneer de **proxy** parameter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f2d44-207">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="f2d44-208">U kunt de para meters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f2d44-208">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="f2d44-209">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="f2d44-209">-SessionVariable</span></span>

<span data-ttu-id="f2d44-210">Hiermee maakt u een web Request-sessie en slaat u deze op in de waarde van de opgegeven variabele.</span><span class="sxs-lookup"><span data-stu-id="f2d44-210">Creates a web request session and saves it in the value of the specified variable.</span></span> <span data-ttu-id="f2d44-211">Geef een naam op voor de variabele zonder het dollar teken ( `$` )-symbool.</span><span class="sxs-lookup"><span data-stu-id="f2d44-211">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="f2d44-212">Wanneer u een sessie variabele opgeeft, `Invoke-RestMethod` maakt een webaanvraag sessie object en wijst deze toe aan een variabele met de opgegeven naam in uw Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="f2d44-212">When you specify a session variable, `Invoke-RestMethod` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="f2d44-213">U kunt de variabele in uw sessie gebruiken zodra de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="f2d44-213">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="f2d44-214">In tegens telling tot een externe sessie is de sessie voor webaanvragen geen permanente verbinding.</span><span class="sxs-lookup"><span data-stu-id="f2d44-214">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="f2d44-215">Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximum omleidings waarde en de teken reeks van de gebruikers agent.</span><span class="sxs-lookup"><span data-stu-id="f2d44-215">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="f2d44-216">U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="f2d44-216">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="f2d44-217">Als u de webaanvraag sessie in volgende webaanvragen wilt gebruiken, geeft u de sessie variabele op in de waarde van de para meter **websessie** .</span><span class="sxs-lookup"><span data-stu-id="f2d44-217">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="f2d44-218">Windows Power shell gebruikt de gegevens in het sessie object voor webaanvragen wanneer de nieuwe verbinding tot stand wordt gebracht.</span><span class="sxs-lookup"><span data-stu-id="f2d44-218">Windows PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="f2d44-219">Als u een waarde in de sessie voor webaanvragen wilt overschrijven, gebruikt u een cmdlet-para meter, zoals **User agent** of **Credential**.</span><span class="sxs-lookup"><span data-stu-id="f2d44-219">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="f2d44-220">Parameter waarden hebben prioriteit boven waarden in de webaanvraag sessie.</span><span class="sxs-lookup"><span data-stu-id="f2d44-220">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="f2d44-221">U kunt de para meters **SessionVariable** en **websession** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="f2d44-221">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="f2d44-222">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="f2d44-222">-TimeoutSec</span></span>

<span data-ttu-id="f2d44-223">Hiermee geeft u op hoe lang de aanvraag in behandeling kan zijn voordat er een time-out optreedt. Voer een waarde in seconden in.</span><span class="sxs-lookup"><span data-stu-id="f2d44-223">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="f2d44-224">De standaard waarde, 0, geeft een onbeperkte time-outwaarde.</span><span class="sxs-lookup"><span data-stu-id="f2d44-224">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="f2d44-225">Het kan tot vijf tien seconden duren voordat een Domain Name System query (DNS) wordt uitgevoerd of een time-out kan worden geretourneerd. Als uw aanvraag een hostnaam bevat waarvoor omzetting vereist is en u TimeoutSec instelt op een waarde die groter is dan nul, maar minder dan 15 seconden, kan het vijf tien seconden of langer duren voordat een webuitzondering wordt gegenereerd en er een time-out optreedt voor uw aanvraag.</span><span class="sxs-lookup"><span data-stu-id="f2d44-225">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set TimeoutSec to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="f2d44-226">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="f2d44-226">-TransferEncoding</span></span>

<span data-ttu-id="f2d44-227">Hiermee geeft u een waarde op voor de header van de HTTP-reactie voor overdracht/versleuteling.</span><span class="sxs-lookup"><span data-stu-id="f2d44-227">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="f2d44-228">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="f2d44-228">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f2d44-229">Gesegmenteerde</span><span class="sxs-lookup"><span data-stu-id="f2d44-229">Chunked</span></span>
- <span data-ttu-id="f2d44-230">Comprimeren</span><span class="sxs-lookup"><span data-stu-id="f2d44-230">Compress</span></span>
- <span data-ttu-id="f2d44-231">Deflate</span><span class="sxs-lookup"><span data-stu-id="f2d44-231">Deflate</span></span>
- <span data-ttu-id="f2d44-232">GZip</span><span class="sxs-lookup"><span data-stu-id="f2d44-232">GZip</span></span>
- <span data-ttu-id="f2d44-233">Identiteit</span><span class="sxs-lookup"><span data-stu-id="f2d44-233">Identity</span></span>

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

### <span data-ttu-id="f2d44-234">-URI</span><span class="sxs-lookup"><span data-stu-id="f2d44-234">-Uri</span></span>

<span data-ttu-id="f2d44-235">Hiermee geeft u de URI (Uniform Resource Identifier) op van de Internet bron waarnaar de webaanvraag wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="f2d44-235">Specifies the Uniform Resource Identifier (URI) of the Internet resource to which the web request is sent.</span></span> <span data-ttu-id="f2d44-236">Deze para meter ondersteunt HTTP-, HTTPS-, FTP-en FILE-waarden.</span><span class="sxs-lookup"><span data-stu-id="f2d44-236">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="f2d44-237">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="f2d44-237">This parameter is required.</span></span> <span data-ttu-id="f2d44-238">De parameter naam ( **URI** ) is optioneel.</span><span class="sxs-lookup"><span data-stu-id="f2d44-238">The parameter name ( **Uri** ) is optional.</span></span>

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

### <span data-ttu-id="f2d44-239">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="f2d44-239">-UseBasicParsing</span></span>

<span data-ttu-id="f2d44-240">Geeft aan dat de cmdlet gebruikmaakt van basis parsering.</span><span class="sxs-lookup"><span data-stu-id="f2d44-240">Indicates that the cmdlet uses basic parsing.</span></span> <span data-ttu-id="f2d44-241">De cmdlet retourneert de onbewerkte HTML in een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="f2d44-241">The cmdlet returns the raw HTML in a **String** object.</span></span>

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

### <span data-ttu-id="f2d44-242">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="f2d44-242">-UseDefaultCredentials</span></span>

<span data-ttu-id="f2d44-243">Gebruikt de referenties van de huidige gebruiker om de webaanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="f2d44-243">Uses the credentials of the current user to send the web request.</span></span>

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

### <span data-ttu-id="f2d44-244">-User agent</span><span class="sxs-lookup"><span data-stu-id="f2d44-244">-UserAgent</span></span>

<span data-ttu-id="f2d44-245">Hiermee geeft u een teken reeks voor de gebruikers agent op voor de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="f2d44-245">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="f2d44-246">De standaard gebruikers agent is vergelijkbaar met ' Mozilla/5.0 ' (Windows NT; Windows NT 6,1; en-US) WindowsPowerShell/3.0 ' met kleine variaties voor elk besturings systeem en platform.</span><span class="sxs-lookup"><span data-stu-id="f2d44-246">The default user agent is similar to "Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0" with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="f2d44-247">Als u een website wilt testen met de standaard teken reeks van de gebruikers agent die wordt gebruikt door de meeste Internet browsers, gebruikt u de eigenschappen van de [PSUserAgent](/dotnet/api/microsoft.powershell.commands) -klasse, zoals Chrome, Firefox, Internet Explorer, Opera en Safari.</span><span class="sxs-lookup"><span data-stu-id="f2d44-247">To test a website with the standard user agent string that is used by most Internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands) class, such as Chrome, FireFox, Internet Explorer, Opera, and Safari.</span></span>

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

### <span data-ttu-id="f2d44-248">-Websessie</span><span class="sxs-lookup"><span data-stu-id="f2d44-248">-WebSession</span></span>

<span data-ttu-id="f2d44-249">Hiermee geeft u een sessie voor webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="f2d44-249">Specifies a web request session.</span></span> <span data-ttu-id="f2d44-250">Voer de naam van de variabele in, met inbegrip van het dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="f2d44-250">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="f2d44-251">Als u een waarde in de sessie voor webaanvragen wilt overschrijven, gebruikt u een cmdlet-para meter, zoals **User agent** of **Credential**.</span><span class="sxs-lookup"><span data-stu-id="f2d44-251">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="f2d44-252">Parameter waarden hebben prioriteit boven waarden in de webaanvraag sessie.</span><span class="sxs-lookup"><span data-stu-id="f2d44-252">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="f2d44-253">In tegens telling tot een externe sessie is de sessie voor webaanvragen geen permanente verbinding.</span><span class="sxs-lookup"><span data-stu-id="f2d44-253">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="f2d44-254">Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximum omleidings waarde en de teken reeks van de gebruikers agent.</span><span class="sxs-lookup"><span data-stu-id="f2d44-254">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="f2d44-255">U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="f2d44-255">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="f2d44-256">Als u een webaanvraag sessie wilt maken, voert u een naam in voor de variabele (zonder een dollar teken) in de waarde van de para meter **SessionVariable** van een `Invoke-RestMethod` opdracht.</span><span class="sxs-lookup"><span data-stu-id="f2d44-256">To create a web request session, enter a variable name (without a dollar sign) in the value of the **SessionVariable** parameter of an `Invoke-RestMethod` command.</span></span> <span data-ttu-id="f2d44-257">`Invoke-RestMethod` Hiermee maakt u de sessie en slaat u deze op in de variabele.</span><span class="sxs-lookup"><span data-stu-id="f2d44-257">`Invoke-RestMethod` creates the session and saves it in the variable.</span></span> <span data-ttu-id="f2d44-258">Gebruik in volgende opdrachten de variabele als de waarde van de para meter **websession** .</span><span class="sxs-lookup"><span data-stu-id="f2d44-258">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="f2d44-259">U kunt de para meters **SessionVariable** en **websession** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="f2d44-259">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="f2d44-260">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f2d44-260">CommonParameters</span></span>

<span data-ttu-id="f2d44-261">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f2d44-261">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f2d44-262">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f2d44-262">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f2d44-263">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="f2d44-263">Inputs</span></span>

### <span data-ttu-id="f2d44-264">System. object</span><span class="sxs-lookup"><span data-stu-id="f2d44-264">System.Object</span></span>

<span data-ttu-id="f2d44-265">U kunt de hoofd tekst van een webaanvraag door sluizen naar `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="f2d44-265">You can pipe the body of a web request to `Invoke-RestMethod`.</span></span>

## <span data-ttu-id="f2d44-266">Uitvoer</span><span class="sxs-lookup"><span data-stu-id="f2d44-266">Outputs</span></span>

### <span data-ttu-id="f2d44-267">System.Xml.Xmldocument, Microsoft.PowerShell.Commands.HtmlWebResponseObject, System. String</span><span class="sxs-lookup"><span data-stu-id="f2d44-267">System.Xml.XmlDocument, Microsoft.PowerShell.Commands.HtmlWebResponseObject, System.String</span></span>

<span data-ttu-id="f2d44-268">De uitvoer van de cmdlet is afhankelijk van de indeling van de inhoud die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f2d44-268">The output of the cmdlet depends upon the format of the content that is retrieved.</span></span>

### <span data-ttu-id="f2d44-269">PSObject</span><span class="sxs-lookup"><span data-stu-id="f2d44-269">PSObject</span></span>

<span data-ttu-id="f2d44-270">Als de aanvraag JSON-teken reeksen retourneert, `Invoke-RestMethod` retourneert een PSObject die de teken reeksen vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f2d44-270">If the request returns JSON strings, `Invoke-RestMethod` returns a PSObject that represents the strings.</span></span>

## <span data-ttu-id="f2d44-271">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f2d44-271">Notes</span></span>

## <span data-ttu-id="f2d44-272">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="f2d44-272">Related Links</span></span>

[<span data-ttu-id="f2d44-273">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="f2d44-273">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="f2d44-274">ConvertFrom-JSON</span><span class="sxs-lookup"><span data-stu-id="f2d44-274">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="f2d44-275">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="f2d44-275">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)
