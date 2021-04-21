---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/20/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-RestMethod
ms.openlocfilehash: 136ae55388256076e1b5843f0569c6ab4b28f0b6
ms.sourcegitcommit: b10731301412afd4111743b85da95e8c25583533
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/20/2021
ms.locfileid: "107756258"
---
# <span data-ttu-id="82c47-102">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="82c47-102">Invoke-RestMethod</span></span>

## <span data-ttu-id="82c47-103">Synopsis</span><span class="sxs-lookup"><span data-stu-id="82c47-103">Synopsis</span></span>
<span data-ttu-id="82c47-104">Verzendt een HTTP- of HTTPS-aanvraag naar een RESTful-webservice.</span><span class="sxs-lookup"><span data-stu-id="82c47-104">Sends an HTTP or HTTPS request to a RESTful web service.</span></span>

## <span data-ttu-id="82c47-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="82c47-105">Syntax</span></span>

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-CertificateThumbprint <String>] [-Certificate <X509Certificate>]
 [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>] [-Headers <IDictionary>]
 [-MaximumRedirection <Int32>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials]
 [-Body <Object>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>]
 [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="82c47-106">Description</span><span class="sxs-lookup"><span data-stu-id="82c47-106">Description</span></span>

<span data-ttu-id="82c47-107">De `Invoke-RestMethod` cmdlet verzendt HTTP- en HTTPS-aanvragen naar Representational State Transfer (REST)-webservices die rijke gestructureerde gegevens retourneren.</span><span class="sxs-lookup"><span data-stu-id="82c47-107">The `Invoke-RestMethod` cmdlet sends HTTP and HTTPS requests to Representational State Transfer (REST) web services that return richly structured data.</span></span>

<span data-ttu-id="82c47-108">PowerShell formatteert het antwoord op basis van het gegevenstype.</span><span class="sxs-lookup"><span data-stu-id="82c47-108">PowerShell formats the response based to the data type.</span></span> <span data-ttu-id="82c47-109">Voor een RSS- of ATOM-feed retourneert PowerShell de XML-knooppunten Item of Entry.</span><span class="sxs-lookup"><span data-stu-id="82c47-109">For an RSS or ATOM feed, PowerShell returns the Item or Entry XML nodes.</span></span> <span data-ttu-id="82c47-110">Voor JavaScript Object Notation (JSON) of XML converteert of deserialiseert PowerShell de inhoud naar `[PSCustomObject]` objecten.</span><span class="sxs-lookup"><span data-stu-id="82c47-110">For JavaScript Object Notation (JSON) or XML, PowerShell converts, or deserializes, the content into `[PSCustomObject]` objects.</span></span>

> [!NOTE]
> <span data-ttu-id="82c47-111">Wanneer het REST-eindpunt meerdere objecten retourneert, worden de objecten ontvangen als een matrix.</span><span class="sxs-lookup"><span data-stu-id="82c47-111">When the REST endpoint returns multiple objects, the objects are received as an array.</span></span> <span data-ttu-id="82c47-112">Als u de uitvoer doorspijpt `Invoke-RestMethod` van naar een andere opdracht, wordt deze als één object `[Object[]]` verzonden.</span><span class="sxs-lookup"><span data-stu-id="82c47-112">If you pipe the output from `Invoke-RestMethod` to another command, it is sent as a single `[Object[]]` object.</span></span> <span data-ttu-id="82c47-113">De inhoud van die matrix wordt niet geïndefeerd voor de volgende opdracht in de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="82c47-113">The contents of that array are not enumerated for the next command on the pipeline.</span></span>

<span data-ttu-id="82c47-114">Deze cmdlet is geïntroduceerd in Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="82c47-114">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="82c47-115">Standaard kan scriptcode op de webpagina worden uitgevoerd wanneer de pagina wordt geparseerd om de eigenschap te `ParsedHtml` vullen.</span><span class="sxs-lookup"><span data-stu-id="82c47-115">By default, script code in the web page may be run when the page is being parsed to populate the `ParsedHtml` property.</span></span> <span data-ttu-id="82c47-116">Gebruik de **schakelknop UseBasicParsing** om dit te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="82c47-116">Use the **UseBasicParsing** switch to suppress this.</span></span>

## <span data-ttu-id="82c47-117">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="82c47-117">Examples</span></span>

### <span data-ttu-id="82c47-118">Voorbeeld 1: de PowerShell RSS-feed op halen</span><span class="sxs-lookup"><span data-stu-id="82c47-118">Example 1: Get the PowerShell RSS feed</span></span>

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

<span data-ttu-id="82c47-119">Met deze opdracht wordt de `Invoke-RestMethod` cmdlet gebruikt om informatie op te halen uit de RSS-feed van het PowerShell-blog.</span><span class="sxs-lookup"><span data-stu-id="82c47-119">This command uses the `Invoke-RestMethod` cmdlet to get information from the PowerShell Blog RSS feed.</span></span> <span data-ttu-id="82c47-120">De opdracht gebruikt de cmdlet om de waarden van de eigenschappen Titel en `Format-Table` **pubDate** van elke  blog in een tabel weer te geven.</span><span class="sxs-lookup"><span data-stu-id="82c47-120">The command uses the `Format-Table` cmdlet to display the values of the **Title** and **pubDate** properties of each blog in a table.</span></span>

### <span data-ttu-id="82c47-121">Voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="82c47-121">Example 2</span></span>

<span data-ttu-id="82c47-122">In het volgende voorbeeld wordt een gebruiker uitgevoerd om `Invoke-RestMethod` een POST-aanvraag uit te voeren op een intranetwebsite in de organisatie van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="82c47-122">In the following example, a user runs `Invoke-RestMethod` to perform a POST request on an intranet website in the user's organization.</span></span>

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

### <span data-ttu-id="82c47-123">Voorbeeld 3: Meerdere headers doorgeven</span><span class="sxs-lookup"><span data-stu-id="82c47-123">Example 3: Pass multiple headers</span></span>

<span data-ttu-id="82c47-124">In dit voorbeeld wordt gedemonstreerd hoe u meerdere headers van een naar `hash-table` een REST API.</span><span class="sxs-lookup"><span data-stu-id="82c47-124">This example demonstrates, how to pass multiple headers in from a `hash-table` to a REST API.</span></span>

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

<span data-ttu-id="82c47-125">API's vereisen vaak doorgegeven headers voor verificatie, validatie, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="82c47-125">APIs often require passed headers for authentication, validation etc.</span></span>

### <span data-ttu-id="82c47-126">Voorbeeld 3: Formuliergegevens verzenden</span><span class="sxs-lookup"><span data-stu-id="82c47-126">Example 3: Submitting form data</span></span>

<span data-ttu-id="82c47-127">Wanneer de body een formulier is of de uitvoer van een andere aanroep is, stelt PowerShell de aanvraaginhoud in `Invoke-WebRequest` op de formuliervelden.</span><span class="sxs-lookup"><span data-stu-id="82c47-127">When the body is a form, or it is the output of another `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>

<span data-ttu-id="82c47-128">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="82c47-128">For example:</span></span>

```powershell
$R = Invoke-WebRequest https://website.com/login.aspx
$R.Forms[0].Name = "MyName"
$R.Forms[0].Password = "MyPassword"
Invoke-RestMethod https://website.com/service.aspx -Body $R.Forms[0]
```

### <span data-ttu-id="82c47-129">Voorbeeld 4: Geretourneerde items in de pijplijn opsnoemen</span><span class="sxs-lookup"><span data-stu-id="82c47-129">Example 4: Enumerate returned items on the pipeline</span></span>

<span data-ttu-id="82c47-130">GitHub retourneert meerdere objecten in een matrix.</span><span class="sxs-lookup"><span data-stu-id="82c47-130">GitHub returns multiple objects an array.</span></span> <span data-ttu-id="82c47-131">Als u de uitvoer doorspijpt naar een andere opdracht, wordt deze als één `[Object[]]` object verzonden.</span><span class="sxs-lookup"><span data-stu-id="82c47-131">If you pipe the output to another command, it is sent as a single `[Object[]]`object.</span></span>

<span data-ttu-id="82c47-132">Als u de objecten in de pijplijn wilt opsnoemen, sloop de resultaten door naar of verpakt u de `Write-Output` cmdlet tussen haakjes.</span><span class="sxs-lookup"><span data-stu-id="82c47-132">To enumerate the objects into the pipeline, pipe the results to `Write-Output` or wrap the cmdlet in parentheses.</span></span> <span data-ttu-id="82c47-133">In het volgende voorbeeld wordt het aantal objecten geteld dat door GitHub wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="82c47-133">The following example counts the number of objects returned by GitHub.</span></span> <span data-ttu-id="82c47-134">Vervolgens wordt het aantal objecten geteld dat in de pijplijn is geïnsemaneerd.</span><span class="sxs-lookup"><span data-stu-id="82c47-134">Then counts the number of objects enumerated to the pipeline.</span></span>

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

## <span data-ttu-id="82c47-135">Parameters</span><span class="sxs-lookup"><span data-stu-id="82c47-135">Parameters</span></span>

### <span data-ttu-id="82c47-136">-Body</span><span class="sxs-lookup"><span data-stu-id="82c47-136">-Body</span></span>

<span data-ttu-id="82c47-137">Hiermee geeft u de body van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="82c47-137">Specifies the body of the request.</span></span> <span data-ttu-id="82c47-138">De hoofdtekst is de inhoud van de aanvraag die volgt op de headers.</span><span class="sxs-lookup"><span data-stu-id="82c47-138">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="82c47-139">U kunt ook een bodywaarde doorspijpen naar `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="82c47-139">You can also pipe a body value to `Invoke-RestMethod`.</span></span>

<span data-ttu-id="82c47-140">De **parameter Body** kan worden gebruikt om een lijst met queryparameters op te geven of om de inhoud van het antwoord op te geven.</span><span class="sxs-lookup"><span data-stu-id="82c47-140">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="82c47-141">Wanneer de invoer een GET-aanvraag is en de body een IDictionary is (meestal een hash-tabel), wordt de body als queryparameters toegevoegd aan de URI.</span><span class="sxs-lookup"><span data-stu-id="82c47-141">When the input is a GET request, and the body is an IDictionary (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="82c47-142">Voor andere aanvraagtypen (zoals POST) wordt de body ingesteld als de waarde van de aanvraag body in de standaardindeling name=value.</span><span class="sxs-lookup"><span data-stu-id="82c47-142">For other request types (such as POST), the body is set as the value of the request body in the standard name=value format.</span></span>

> [!WARNING]
> <span data-ttu-id="82c47-143">De uitgebreide uitvoer van een POST-hoofdtekst eindigt met , ook al is de grootte van de hoofdtekst bekend en `with -1-byte payload` verzonden in de `Content-Length` HTTP-header.</span><span class="sxs-lookup"><span data-stu-id="82c47-143">The verbose output of a POST body will end with `with -1-byte payload`, even though the size of the body is both known and sent in the `Content-Length` HTTP header.</span></span>

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

### <span data-ttu-id="82c47-144">-Certificaat</span><span class="sxs-lookup"><span data-stu-id="82c47-144">-Certificate</span></span>

<span data-ttu-id="82c47-145">Hiermee geeft u het clientcertificaat op dat wordt gebruikt voor een beveiligde webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="82c47-145">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="82c47-146">Voer een variabele in die een certificaat bevat of een opdracht of expressie die het certificaat op haalt.</span><span class="sxs-lookup"><span data-stu-id="82c47-146">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="82c47-147">Als u een certificaat wilt zoeken, `Get-PfxCertificate` gebruikt of gebruikt u de `Get-ChildItem` cmdlet in het station Certificaat ( `Cert:` ).</span><span class="sxs-lookup"><span data-stu-id="82c47-147">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="82c47-148">Als het certificaat niet geldig is of onvoldoende bevoegdheid heeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="82c47-148">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="82c47-149">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="82c47-149">-CertificateThumbprint</span></span>

<span data-ttu-id="82c47-150">Hiermee geeft u het digitale openbare-sleutelcertificaat (X509) op van een gebruikersaccount dat toestemming heeft om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="82c47-150">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="82c47-151">Voer de vingerafdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="82c47-151">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="82c47-152">Certificaten worden gebruikt in verificatie op basis van clientcertificaten.</span><span class="sxs-lookup"><span data-stu-id="82c47-152">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="82c47-153">Ze kunnen alleen worden toe te staan aan lokale gebruikersaccounts; ze werken niet met domeinaccounts.</span><span class="sxs-lookup"><span data-stu-id="82c47-153">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="82c47-154">Als u een vingerafdruk van het certificaat wilt verkrijgen, gebruikt u `Get-Item` de opdracht of op het Windows PowerShell ( `Get-ChildItem` `Cert:` ).</span><span class="sxs-lookup"><span data-stu-id="82c47-154">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the Windows PowerShell (`Cert:`) drive.</span></span>

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

### <span data-ttu-id="82c47-155">-ContentType</span><span class="sxs-lookup"><span data-stu-id="82c47-155">-ContentType</span></span>

<span data-ttu-id="82c47-156">Hiermee geeft u het inhoudstype van de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="82c47-156">Specifies the content type of the web request.</span></span>

<span data-ttu-id="82c47-157">Als deze parameter wordt weggelaten en de aanvraagmethode POST is, stelt u het inhoudstype in op `Invoke-RestMethod` 'application/x-www-form-urlencoded'.</span><span class="sxs-lookup"><span data-stu-id="82c47-157">If this parameter is omitted and the request method is POST, `Invoke-RestMethod` sets the content type to "application/x-www-form-urlencoded".</span></span> <span data-ttu-id="82c47-158">Anders wordt het inhoudstype niet opgegeven in de aanroep.</span><span class="sxs-lookup"><span data-stu-id="82c47-158">Otherwise, the content type is not specified in the call.</span></span>

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

### <span data-ttu-id="82c47-159">-Credential</span><span class="sxs-lookup"><span data-stu-id="82c47-159">-Credential</span></span>

<span data-ttu-id="82c47-160">Hiermee geeft u een gebruikersaccount op dat toestemming heeft om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="82c47-160">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="82c47-161">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="82c47-161">The default is the current user.</span></span>

<span data-ttu-id="82c47-162">Typ een gebruikersnaam, zoals **User01** of **Domain01\User01,** of voer een **PSCredential-object** in dat door de `Get-Credential` cmdlet is gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="82c47-162">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="82c47-163">Referenties worden opgeslagen in een [PSCredential-object](/dotnet/api/system.management.automation.pscredential) en het wachtwoord wordt opgeslagen als een [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="82c47-163">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="82c47-164">Zie How secure is **SecureString?** (Hoe veilig is SecureString?) voor meer informatie over [SecureString-gegevensbeveiliging.](/dotnet/api/system.security.securestring#how-secure-is-securestring)</span><span class="sxs-lookup"><span data-stu-id="82c47-164">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="82c47-165">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="82c47-165">-DisableKeepAlive</span></span>

<span data-ttu-id="82c47-166">Hiermee stelt **u de KeepAlive-waarde** in de HTTP-header in op False.</span><span class="sxs-lookup"><span data-stu-id="82c47-166">Sets the **KeepAlive** value in the HTTP header to False.</span></span> <span data-ttu-id="82c47-167">**KeepAlive** is standaard Waar.</span><span class="sxs-lookup"><span data-stu-id="82c47-167">By default, **KeepAlive** is True.</span></span>
<span data-ttu-id="82c47-168">**KeepAlive brengt** een permanente verbinding met de server tot stand om volgende aanvragen mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="82c47-168">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="82c47-169">-Headers</span><span class="sxs-lookup"><span data-stu-id="82c47-169">-Headers</span></span>

<span data-ttu-id="82c47-170">Hiermee geeft u de headers van de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="82c47-170">Specifies the headers of the web request.</span></span> <span data-ttu-id="82c47-171">Voer een hashtabel of -woordenlijst in.</span><span class="sxs-lookup"><span data-stu-id="82c47-171">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="82c47-172">Als u UserAgent-headers wilt instellen, gebruikt u de parameter **UserAgent.**</span><span class="sxs-lookup"><span data-stu-id="82c47-172">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="82c47-173">U kunt deze parameter niet gebruiken om UserAgent- of cookieheaders op te geven.</span><span class="sxs-lookup"><span data-stu-id="82c47-173">You cannot use this parameter to specify UserAgent or cookie headers.</span></span>

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

### <span data-ttu-id="82c47-174">-InFile</span><span class="sxs-lookup"><span data-stu-id="82c47-174">-InFile</span></span>

<span data-ttu-id="82c47-175">Haalt de inhoud van de webaanvraag op uit een bestand.</span><span class="sxs-lookup"><span data-stu-id="82c47-175">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="82c47-176">Voer een pad en bestandsnaam in.</span><span class="sxs-lookup"><span data-stu-id="82c47-176">Enter a path and file name.</span></span> <span data-ttu-id="82c47-177">Als u het pad weglaten, is de standaardwaarde de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="82c47-177">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="82c47-178">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="82c47-178">-MaximumRedirection</span></span>

<span data-ttu-id="82c47-179">Hiermee bepaalt u hoe vaak Windows PowerShell verbinding omleiden naar een alternatieve Uniform Resource Identifier (URI) voordat de verbinding mislukt.</span><span class="sxs-lookup"><span data-stu-id="82c47-179">Determines how many times Windows PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="82c47-180">De standaardwaarde is 5.</span><span class="sxs-lookup"><span data-stu-id="82c47-180">The default value is 5.</span></span> <span data-ttu-id="82c47-181">Met de waarde 0 (nul) wordt alle omleiding voorkomen.</span><span class="sxs-lookup"><span data-stu-id="82c47-181">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="82c47-182">-Methode</span><span class="sxs-lookup"><span data-stu-id="82c47-182">-Method</span></span>

<span data-ttu-id="82c47-183">Hiermee geeft u de methode die wordt gebruikt voor de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="82c47-183">Specifies the method used for the web request.</span></span> <span data-ttu-id="82c47-184">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="82c47-184">The acceptable values for this parameter are:</span></span>

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

### <span data-ttu-id="82c47-185">-OutFile</span><span class="sxs-lookup"><span data-stu-id="82c47-185">-OutFile</span></span>

<span data-ttu-id="82c47-186">Slaat de antwoord-body in het opgegeven uitvoerbestand.</span><span class="sxs-lookup"><span data-stu-id="82c47-186">Saves the response body in the specified output file.</span></span> <span data-ttu-id="82c47-187">Voer een pad en bestandsnaam in.</span><span class="sxs-lookup"><span data-stu-id="82c47-187">Enter a path and file name.</span></span> <span data-ttu-id="82c47-188">Als u het pad weglaten, is de standaardwaarde de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="82c47-188">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="82c47-189">Retourneert `Invoke-RestMethod` standaard de resultaten naar de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="82c47-189">By default, `Invoke-RestMethod` returns the results to the pipeline.</span></span> <span data-ttu-id="82c47-190">Als u de resultaten wilt verzenden naar een bestand en naar de pijplijn, gebruikt u de parameter **Passthru.**</span><span class="sxs-lookup"><span data-stu-id="82c47-190">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="82c47-191">-PassThru</span><span class="sxs-lookup"><span data-stu-id="82c47-191">-PassThru</span></span>

<span data-ttu-id="82c47-192">Retourneert de resultaten, naast het schrijven ervan naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="82c47-192">Returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="82c47-193">Deze parameter is alleen geldig wanneer **de OutFile** parameter wordt ook gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="82c47-193">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="82c47-194">-Proxy</span><span class="sxs-lookup"><span data-stu-id="82c47-194">-Proxy</span></span>

<span data-ttu-id="82c47-195">Maakt gebruik van een proxyserver voor de aanvraag, in plaats van rechtstreeks verbinding te maken met de internetresource.</span><span class="sxs-lookup"><span data-stu-id="82c47-195">Uses a proxy server for the request, rather than connecting directly to the Internet resource.</span></span> <span data-ttu-id="82c47-196">Voer de URI van een netwerkproxyserver in.</span><span class="sxs-lookup"><span data-stu-id="82c47-196">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="82c47-197">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="82c47-197">-ProxyCredential</span></span>

<span data-ttu-id="82c47-198">Hiermee geeft u een gebruikersaccount dat is gemachtigd voor het gebruik van de proxyserver die is opgegeven door de **proxyparameter.**</span><span class="sxs-lookup"><span data-stu-id="82c47-198">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="82c47-199">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="82c47-199">The default is the current user.</span></span>

<span data-ttu-id="82c47-200">Typ een gebruikersnaam, zoals 'User01' of 'Domain01\User01', of voer een **PSCredential-object** in, zoals een object dat wordt gegenereerd door de `Get-Credential` cmdlet .</span><span class="sxs-lookup"><span data-stu-id="82c47-200">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="82c47-201">Deze parameter is alleen geldig wanneer de **Proxy** parameter wordt ook gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="82c47-201">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="82c47-202">U kunt de parameters **ProxyCredential** en **ProxyUseDefaultCredentials** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="82c47-202">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="82c47-203">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="82c47-203">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="82c47-204">Gebruikt de referenties van de huidige gebruiker voor toegang tot de proxyserver die is opgegeven door de **proxyparameter.**</span><span class="sxs-lookup"><span data-stu-id="82c47-204">Uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="82c47-205">Deze parameter is alleen geldig wanneer de **Proxy** parameter wordt ook gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="82c47-205">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="82c47-206">U kunt de parameters **ProxyCredential** en **ProxyUseDefaultCredentials** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="82c47-206">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="82c47-207">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="82c47-207">-SessionVariable</span></span>

<span data-ttu-id="82c47-208">Hiermee maakt u een webaanvraagsessie en slaat u deze op in de waarde van de opgegeven variabele.</span><span class="sxs-lookup"><span data-stu-id="82c47-208">Creates a web request session and saves it in the value of the specified variable.</span></span> <span data-ttu-id="82c47-209">Voer een variabelenaam in zonder het dollarteken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="82c47-209">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="82c47-210">Wanneer u een sessievariabele opgeeft, maakt een webaanvraagsessieobject en wijst u dit toe aan een variabele met de opgegeven `Invoke-RestMethod` naam in uw PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="82c47-210">When you specify a session variable, `Invoke-RestMethod` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="82c47-211">U kunt de variabele in uw sessie gebruiken zodra de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="82c47-211">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="82c47-212">In tegenstelling tot een externe sessie is de webaanvraagsessie geen permanente verbinding.</span><span class="sxs-lookup"><span data-stu-id="82c47-212">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="82c47-213">Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximale omleidingswaarde en de tekenreeks van de gebruikersagent.</span><span class="sxs-lookup"><span data-stu-id="82c47-213">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="82c47-214">U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="82c47-214">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="82c47-215">Als u de webaanvraagsessie in volgende webaanvragen wilt gebruiken, geeft u de sessievariabele op in de waarde van de parameter **WebSession.**</span><span class="sxs-lookup"><span data-stu-id="82c47-215">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="82c47-216">Windows PowerShell gebruikt de gegevens in het webaanvraagsessieobject bij het tot stand brengen van de nieuwe verbinding.</span><span class="sxs-lookup"><span data-stu-id="82c47-216">Windows PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="82c47-217">Als u een waarde in de webaanvraagsessie wilt overschrijven, gebruikt u een cmdlet-parameter, zoals **UserAgent** of **Credential.**</span><span class="sxs-lookup"><span data-stu-id="82c47-217">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="82c47-218">Parameterwaarden hebben voorrang op waarden in de webaanvraagsessie.</span><span class="sxs-lookup"><span data-stu-id="82c47-218">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="82c47-219">U kunt de parameters **SessionVariable en** **WebSession** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="82c47-219">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="82c47-220">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="82c47-220">-TimeoutSec</span></span>

<span data-ttu-id="82c47-221">Hiermee geeft u op hoe lang de aanvraag in behandeling kan zijn voordat er een times-out wordt uitgevoerd. Voer een waarde in seconden in.</span><span class="sxs-lookup"><span data-stu-id="82c47-221">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="82c47-222">De standaardwaarde, 0, geeft een onbeperkte time-out aan.</span><span class="sxs-lookup"><span data-stu-id="82c47-222">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="82c47-223">Het Domain Name System (DNS)-query kan tot 15 seconden duren om een retour- of time-out te retourneren. Als uw aanvraag een hostnaam bevat die een oplossing vereist en u TimeoutSec in stelt op een waarde die groter is dan nul, maar minder dan 15 seconden, kan het 15 seconden of langer duren voordat een WebException wordt gegeven en er een time-out van uw aanvraag wordt gegeven.</span><span class="sxs-lookup"><span data-stu-id="82c47-223">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set TimeoutSec to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="82c47-224">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="82c47-224">-TransferEncoding</span></span>

<span data-ttu-id="82c47-225">Hiermee geeft u een waarde op voor de HTTP-antwoordheader voor overdrachtcoderen.</span><span class="sxs-lookup"><span data-stu-id="82c47-225">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="82c47-226">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="82c47-226">The acceptable values for this parameter are:</span></span>

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

### <span data-ttu-id="82c47-227">-URI</span><span class="sxs-lookup"><span data-stu-id="82c47-227">-Uri</span></span>

<span data-ttu-id="82c47-228">Hiermee geeft u de Uniform Resource Identifier (URI) op van de internetresource waar de webaanvraag naar wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="82c47-228">Specifies the Uniform Resource Identifier (URI) of the Internet resource to which the web request is sent.</span></span> <span data-ttu-id="82c47-229">Deze parameter ondersteunt de waarden HTTP, HTTPS, FTP en FILE.</span><span class="sxs-lookup"><span data-stu-id="82c47-229">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="82c47-230">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="82c47-230">This parameter is required.</span></span> <span data-ttu-id="82c47-231">De parameternaam (**URI**) is optioneel.</span><span class="sxs-lookup"><span data-stu-id="82c47-231">The parameter name (**Uri**) is optional.</span></span>

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

### <span data-ttu-id="82c47-232">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="82c47-232">-UseBasicParsing</span></span>

<span data-ttu-id="82c47-233">Geeft aan dat de cmdlet basisparsering gebruikt.</span><span class="sxs-lookup"><span data-stu-id="82c47-233">Indicates that the cmdlet uses basic parsing.</span></span> <span data-ttu-id="82c47-234">De cmdlet retourneert de onbewerkte HTML in een **tekenreeksobject.**</span><span class="sxs-lookup"><span data-stu-id="82c47-234">The cmdlet returns the raw HTML in a **String** object.</span></span>

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

### <span data-ttu-id="82c47-235">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="82c47-235">-UseDefaultCredentials</span></span>

<span data-ttu-id="82c47-236">Gebruikt de referenties van de huidige gebruiker om de webaanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="82c47-236">Uses the credentials of the current user to send the web request.</span></span>

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

### <span data-ttu-id="82c47-237">-UserAgent</span><span class="sxs-lookup"><span data-stu-id="82c47-237">-UserAgent</span></span>

<span data-ttu-id="82c47-238">Hiermee geeft u een tekenreeks voor de gebruikersagent op voor de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="82c47-238">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="82c47-239">De standaardgebruikersagent is vergelijkbaar met Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0" met kleine variaties voor elk besturingssysteem en platform.</span><span class="sxs-lookup"><span data-stu-id="82c47-239">The default user agent is similar to "Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0" with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="82c47-240">Als u een website wilt testen met de standaard gebruikersagentreeks die door de meeste internetbrowsers wordt gebruikt, gebruikt u de eigenschappen van de [klasse PSUserAgent,](/dotnet/api/microsoft.powershell.commands) zoals Chrome, FireFox, Internet Explorer, Opera en Safari.</span><span class="sxs-lookup"><span data-stu-id="82c47-240">To test a website with the standard user agent string that is used by most Internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands) class, such as Chrome, FireFox, Internet Explorer, Opera, and Safari.</span></span>

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

### <span data-ttu-id="82c47-241">-WebSession</span><span class="sxs-lookup"><span data-stu-id="82c47-241">-WebSession</span></span>

<span data-ttu-id="82c47-242">Hiermee geeft u een webaanvraagsessie.</span><span class="sxs-lookup"><span data-stu-id="82c47-242">Specifies a web request session.</span></span> <span data-ttu-id="82c47-243">Voer de naam van de variabele in, inclusief het dollarteken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="82c47-243">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="82c47-244">Als u een waarde in de webaanvraagsessie wilt overschrijven, gebruikt u een cmdlet-parameter, zoals **UserAgent** of **Credential.**</span><span class="sxs-lookup"><span data-stu-id="82c47-244">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="82c47-245">Parameterwaarden hebben voorrang op waarden in de webaanvraagsessie.</span><span class="sxs-lookup"><span data-stu-id="82c47-245">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="82c47-246">In tegenstelling tot een externe sessie is de webaanvraagsessie geen permanente verbinding.</span><span class="sxs-lookup"><span data-stu-id="82c47-246">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="82c47-247">Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximale omleidingswaarde en de tekenreeks van de gebruikersagent.</span><span class="sxs-lookup"><span data-stu-id="82c47-247">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="82c47-248">U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="82c47-248">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="82c47-249">Als u een webaanvraagsessie wilt maken, voert u een variabelenaam (zonder dollarteken) in de waarde van de parameter **SessionVariable** van een `Invoke-RestMethod` opdracht in.</span><span class="sxs-lookup"><span data-stu-id="82c47-249">To create a web request session, enter a variable name (without a dollar sign) in the value of the **SessionVariable** parameter of an `Invoke-RestMethod` command.</span></span> <span data-ttu-id="82c47-250">`Invoke-RestMethod` maakt de sessie en slaat deze op in de variabele .</span><span class="sxs-lookup"><span data-stu-id="82c47-250">`Invoke-RestMethod` creates the session and saves it in the variable.</span></span> <span data-ttu-id="82c47-251">In volgende opdrachten gebruikt u de variabele als de waarde van de parameter **WebSession.**</span><span class="sxs-lookup"><span data-stu-id="82c47-251">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="82c47-252">U kunt de parameters **SessionVariable en** **WebSession** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="82c47-252">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="82c47-253">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="82c47-253">CommonParameters</span></span>

<span data-ttu-id="82c47-254">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="82c47-254">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="82c47-255">Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="82c47-255">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="82c47-256">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="82c47-256">Inputs</span></span>

### <span data-ttu-id="82c47-257">System.Object</span><span class="sxs-lookup"><span data-stu-id="82c47-257">System.Object</span></span>

<span data-ttu-id="82c47-258">U kunt de body van een webaanvraag doorseen naar `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="82c47-258">You can pipe the body of a web request to `Invoke-RestMethod`.</span></span>

## <span data-ttu-id="82c47-259">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="82c47-259">Outputs</span></span>

### <span data-ttu-id="82c47-260">System.Xml.XmlDocument, Microsoft.PowerShell.Commands.HtmlWebResponseObject, System.String</span><span class="sxs-lookup"><span data-stu-id="82c47-260">System.Xml.XmlDocument, Microsoft.PowerShell.Commands.HtmlWebResponseObject, System.String</span></span>

<span data-ttu-id="82c47-261">De uitvoer van de cmdlet is afhankelijk van de indeling van de inhoud die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="82c47-261">The output of the cmdlet depends upon the format of the content that is retrieved.</span></span>

### <span data-ttu-id="82c47-262">PSObject</span><span class="sxs-lookup"><span data-stu-id="82c47-262">PSObject</span></span>

<span data-ttu-id="82c47-263">Als de aanvraag JSON-tekenreeksen retourneert, `Invoke-RestMethod` retourneert een PSObject dat de tekenreeksen vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="82c47-263">If the request returns JSON strings, `Invoke-RestMethod` returns a PSObject that represents the strings.</span></span>

## <span data-ttu-id="82c47-264">Notities</span><span class="sxs-lookup"><span data-stu-id="82c47-264">Notes</span></span>

## <span data-ttu-id="82c47-265">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="82c47-265">Related Links</span></span>

[<span data-ttu-id="82c47-266">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="82c47-266">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="82c47-267">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="82c47-267">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="82c47-268">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="82c47-268">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)
