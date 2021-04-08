---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/05/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: 516e73b36668bcb1606df77b0c6f63c3d477ac7c
ms.sourcegitcommit: 241071803915ab7d544576b5652ac23349a86369
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/07/2021
ms.locfileid: "107027206"
---
# <span data-ttu-id="fc233-102">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="fc233-102">Invoke-WebRequest</span></span>

## <span data-ttu-id="fc233-103">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="fc233-103">Synopsis</span></span>
<span data-ttu-id="fc233-104">Hiermee wordt inhoud opgehaald van een webpagina op internet.</span><span class="sxs-lookup"><span data-stu-id="fc233-104">Gets content from a web page on the Internet.</span></span>

## <span data-ttu-id="fc233-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fc233-105">Syntax</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>] [-SessionVariable <String>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-CertificateThumbprint <String>]
 [-Certificate <X509Certificate>] [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>]
 [-Headers <IDictionary>] [-MaximumRedirection <Int32>] [-Method <WebRequestMethod>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>] [-ContentType <String>]
 [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="fc233-106">Description</span><span class="sxs-lookup"><span data-stu-id="fc233-106">Description</span></span>

<span data-ttu-id="fc233-107">De `Invoke-WebRequest` cmdlet verzendt http-, HTTPS-, FTP-en file-aanvragen naar een webpagina of webservice.</span><span class="sxs-lookup"><span data-stu-id="fc233-107">The `Invoke-WebRequest` cmdlet sends HTTP, HTTPS, FTP, and FILE requests to a web page or web service.</span></span>
<span data-ttu-id="fc233-108">Hiermee wordt het antwoord geparseerd en worden verzamelingen van formulieren, koppelingen, afbeeldingen en andere belang rijke HTML-elementen geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="fc233-108">It parses the response and returns collections of forms, links, images, and other significant HTML elements.</span></span>

<span data-ttu-id="fc233-109">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="fc233-109">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="fc233-110">Standaard kan script code op de webpagina worden uitgevoerd wanneer de pagina wordt geparseerd om de eigenschap in te vullen `ParsedHtml` .</span><span class="sxs-lookup"><span data-stu-id="fc233-110">By default, script code in the web page may be run when the page is being parsed to populate the `ParsedHtml` property.</span></span> <span data-ttu-id="fc233-111">Gebruik de `-UseBasicParsing` Schakel optie om dit te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="fc233-111">Use the `-UseBasicParsing` switch to suppress this.</span></span>

## <span data-ttu-id="fc233-112">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="fc233-112">Examples</span></span>

### <span data-ttu-id="fc233-113">Voor beeld 1: een webaanvraag verzenden</span><span class="sxs-lookup"><span data-stu-id="fc233-113">Example 1: Send a web request</span></span>

<span data-ttu-id="fc233-114">Met deze opdracht wordt de `Invoke-WebRequest` cmdlet gebruikt voor het verzenden van een webaanvraag naar de Bing.com-site.</span><span class="sxs-lookup"><span data-stu-id="fc233-114">This command uses the `Invoke-WebRequest` cmdlet to send a web request to the Bing.com site.</span></span>

```powershell
$R = Invoke-WebRequest -URI https://www.bing.com?q=how+many+feet+in+a+mile
$R.AllElements | Where-Object {
    $_.name -like "* Value" -and $_.tagName -eq "INPUT"
} | Select-Object Name, Value
```

```Output
name       value
----       -----
From Value 1
To Value   5280
```

<span data-ttu-id="fc233-115">Met de eerste opdracht wordt de aanvraag uitgegeven en wordt het antwoord in de `$R` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="fc233-115">The first command issues the request and saves the response in the `$R` variable.</span></span>

<span data-ttu-id="fc233-116">Met de tweede opdracht wordt gefilterd op de objecten in **de eigenschap voor de gegevens, waarbij** de eigenschap **name** als "\* waarde" is en de **tagName** "input" is.</span><span class="sxs-lookup"><span data-stu-id="fc233-116">The second command filters the objects in the **AllElements** property where the **name** property is like "\* Value" and the **tagName** is "INPUT".</span></span> <span data-ttu-id="fc233-117">De gefilterde resultaten worden gepiped om `Select-Object` de **naam** en **waarde** -eigenschappen te selecteren.</span><span class="sxs-lookup"><span data-stu-id="fc233-117">The filtered results are piped to `Select-Object` to select the **name** and **value** properties.</span></span>

### <span data-ttu-id="fc233-118">Voor beeld 2: een stateful webservice gebruiken</span><span class="sxs-lookup"><span data-stu-id="fc233-118">Example 2: Use a stateful web service</span></span>

<span data-ttu-id="fc233-119">In dit voor beeld ziet u hoe u de `Invoke-WebRequest` cmdlet gebruikt met een stateful webservice, zoals Facebook.</span><span class="sxs-lookup"><span data-stu-id="fc233-119">This example shows how to use the `Invoke-WebRequest` cmdlet with a stateful web service, such as Facebook.</span></span>

```powershell
$R = Invoke-WebRequest https://www.facebook.com/login.php -SessionVariable fb
# This command stores the first form in the Forms property of the $R variable in the $Form variable.
$Form = $R.Forms[0]
# This command shows the fields available in the Form.
$Form.fields
```

```Output
Key                     Value
---                     -----
...
email
pass
...
```

```powershell
# These commands populate the username and password of the respective Form fields.
$Form.Fields["email"]="User01@Fabrikam.com"
$Form.Fields["pass"]="P@ssw0rd"
# This command creates the Uri that will be used to log in to facebook.
# The value of the Uri parameter is the value of the Action property of the form.
$Uri = "https://www.facebook.com" + $Form.Action
# Now the Invoke-WebRequest cmdlet is used to sign into the Facebook web service.
# The WebRequestSession object in the $FB variable is passed as the value of the WebSession parameter.
# The value of the Body parameter is the hash table in the Fields property of the form.
# The value of the *Method* parameter is POST. The command saves the output in the $R variable.
$R = Invoke-WebRequest -Uri $Uri -WebSession $FB -Method POST -Body $Form.Fields
$R.StatusDescription
```

<span data-ttu-id="fc233-120">De eerste opdracht gebruikt de `Invoke-WebRequest` cmdlet om een aanmeldings aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="fc233-120">The first command uses the `Invoke-WebRequest` cmdlet to send a sign-in request.</span></span> <span data-ttu-id="fc233-121">Met de opdracht wordt de waarde ' FB ' opgegeven voor de waarde van de para meter **SessionVariable** en wordt het resultaat opgeslagen in de `$R` variabele.</span><span class="sxs-lookup"><span data-stu-id="fc233-121">The command specifies a value of "FB" for the value of the **SessionVariable** parameter, and saves the result in the `$R` variable.</span></span> <span data-ttu-id="fc233-122">Wanneer de opdracht is voltooid, `$R` bevat de variabele een **HtmlWebResponseObject** en `$FB` bevat de variabele een **WebRequestSession** -object.</span><span class="sxs-lookup"><span data-stu-id="fc233-122">When the command completes, the `$R` variable contains an **HtmlWebResponseObject** and the `$FB` variable contains a **WebRequestSession** object.</span></span>

<span data-ttu-id="fc233-123">Nadat de `Invoke-WebRequest` cmdlet is aangemeld bij Facebook, geeft de eigenschap **StatusDescription** van het Web Response-object in de `$R` variabele aan dat de gebruiker is aangemeld.</span><span class="sxs-lookup"><span data-stu-id="fc233-123">After the `Invoke-WebRequest` cmdlet signs in to facebook, the **StatusDescription** property of the web response object in the `$R` variable indicates that the user is signed in successfully.</span></span>

### <span data-ttu-id="fc233-124">Voor beeld 3: koppelingen van een webpagina ophalen</span><span class="sxs-lookup"><span data-stu-id="fc233-124">Example 3: Get links from a web page</span></span>

<span data-ttu-id="fc233-125">Met deze opdracht worden de koppelingen op een webpagina opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fc233-125">This command gets the links in a web page.</span></span>

```powershell
(Invoke-WebRequest -Uri "https://devblogs.microsoft.com/powershell/").Links.Href
```

<span data-ttu-id="fc233-126">`Invoke-WebRequest`Met de cmdlet wordt de inhoud van de webpagina opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fc233-126">The `Invoke-WebRequest` cmdlet gets the web page content.</span></span> <span data-ttu-id="fc233-127">De eigenschap **links** van het geretourneerde **HtmlWebResponseObject** wordt gebruikt om de eigenschap **href** van elke koppeling weer te geven.</span><span class="sxs-lookup"><span data-stu-id="fc233-127">Then the **Links** property of the returned **HtmlWebResponseObject** is used to display the **Href** property of each link.</span></span>

### <span data-ttu-id="fc233-128">Voor beeld 4: berichten over niet-geslaagde artikelen van Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="fc233-128">Example 4: Catch non success messages from Invoke-WebRequest</span></span>

<span data-ttu-id="fc233-129">Wanneer er `Invoke-WebRequest` een niet-geslaagd http-bericht wordt aangetroffen (404, 500, etc.), wordt er geen uitvoer geretourneerd en wordt er een afsluit fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="fc233-129">When `Invoke-WebRequest` encounters a non-success HTTP message (404, 500, etc.), it returns no output and throws a terminating error.</span></span> <span data-ttu-id="fc233-130">Als u de fout wilt opvangen en de **status** code wilt weer geven, kunt u de uitvoering in een `try/catch` blok insluiten.</span><span class="sxs-lookup"><span data-stu-id="fc233-130">To catch the error and view the **StatusCode** you can enclose execution in a `try/catch` block.</span></span> <span data-ttu-id="fc233-131">In het volgende voor beeld ziet u hoe u dit kunt doen.</span><span class="sxs-lookup"><span data-stu-id="fc233-131">The following example shows how to accomplish this.</span></span>

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

<span data-ttu-id="fc233-132">De afsluit fout wordt geblokkeerd door het `catch` blok, waardoor de **status** code wordt opgehaald uit het **uitzonderings** object.</span><span class="sxs-lookup"><span data-stu-id="fc233-132">The terminating error is caught by the `catch` block, which retrieves the **StatusCode** from the **Exception** object.</span></span>

## <span data-ttu-id="fc233-133">Parameters</span><span class="sxs-lookup"><span data-stu-id="fc233-133">Parameters</span></span>

### <span data-ttu-id="fc233-134">-Hoofd tekst</span><span class="sxs-lookup"><span data-stu-id="fc233-134">-Body</span></span>

<span data-ttu-id="fc233-135">Hiermee geeft u de hoofd tekst van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="fc233-135">Specifies the body of the request.</span></span>
<span data-ttu-id="fc233-136">De hoofd tekst is de inhoud van de aanvraag die de headers volgt.</span><span class="sxs-lookup"><span data-stu-id="fc233-136">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="fc233-137">U kunt ook de waarde van een hoofd tekst sluist naar `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="fc233-137">You can also pipe a body value to `Invoke-WebRequest`.</span></span>

<span data-ttu-id="fc233-138">De para meter **Body** kan worden gebruikt om een lijst met query parameters op te geven of de inhoud van het antwoord op te geven.</span><span class="sxs-lookup"><span data-stu-id="fc233-138">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="fc233-139">Wanneer de invoer een GET-aanvraag is en de hoofd tekst een **IDictionary** is (meestal een hash-tabel), wordt de hoofd tekst als query parameters toegevoegd aan de URI.</span><span class="sxs-lookup"><span data-stu-id="fc233-139">When the input is a GET request and the body is an **IDictionary** (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="fc233-140">Voor andere GET-aanvragen wordt de hoofd tekst ingesteld als de waarde van de hoofd tekst van de aanvraag in de standaard `name=value` indeling.</span><span class="sxs-lookup"><span data-stu-id="fc233-140">For other GET requests, the body is set as the value of the request body in the standard `name=value` format.</span></span>

<span data-ttu-id="fc233-141">Wanneer de hoofd tekst een formulier is of de uitvoer van een `Invoke-WebRequest` aanroep, stelt Power shell de aanvraag inhoud in op de formulier velden.</span><span class="sxs-lookup"><span data-stu-id="fc233-141">When the body is a form, or it is the output of an `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>
<span data-ttu-id="fc233-142">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="fc233-142">For example:</span></span>

`$r = Invoke-WebRequest https://website.com/login.aspx`
`$r.Forms\[0\].Name = "MyName"`
`$r.Forms\[0\].Password = "MyPassword"`
`Invoke-RestMethod https://website.com/service.aspx -Body $r`

- <span data-ttu-id="fc233-143">of</span><span class="sxs-lookup"><span data-stu-id="fc233-143">or -</span></span>

`Invoke-RestMethod https://website.com/service.aspx -Body $r.Forms\[0\]`

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

### <span data-ttu-id="fc233-144">-Certificaat</span><span class="sxs-lookup"><span data-stu-id="fc233-144">-Certificate</span></span>

<span data-ttu-id="fc233-145">Hiermee geeft u het client certificaat op dat wordt gebruikt voor een beveiligde webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="fc233-145">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="fc233-146">Voer een variabele in die een certificaat of een opdracht of expressie bevat waarmee het certificaat wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fc233-146">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="fc233-147">Als u een certificaat wilt zoeken, gebruikt `Get-PfxCertificate` of gebruikt u de `Get-ChildItem` cmdlet in het **certificaat** `Cert:` station.</span><span class="sxs-lookup"><span data-stu-id="fc233-147">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the **Certificate** (`Cert:`) drive.</span></span> <span data-ttu-id="fc233-148">Als het certificaat ongeldig is of niet voldoende autoriteit heeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="fc233-148">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="fc233-149">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="fc233-149">-CertificateThumbprint</span></span>

<span data-ttu-id="fc233-150">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat gemachtigd is om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="fc233-150">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="fc233-151">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="fc233-151">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="fc233-152">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="fc233-152">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="fc233-153">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="fc233-153">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="fc233-154">Gebruik de `Get-Item` `Get-ChildItem` opdracht of in het Power Shell-station om een certificaat vingerafdruk te verkrijgen `Cert:` .</span><span class="sxs-lookup"><span data-stu-id="fc233-154">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

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

### <span data-ttu-id="fc233-155">-Content type</span><span class="sxs-lookup"><span data-stu-id="fc233-155">-ContentType</span></span>

<span data-ttu-id="fc233-156">Hiermee geeft u het type inhoud van de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="fc233-156">Specifies the content type of the web request.</span></span>

<span data-ttu-id="fc233-157">Als deze para meter wordt wegge laten en de aanvraag methode POST is, `Invoke-WebRequest` wordt het inhouds type ingesteld op Application/x-www-form-urlencoded.</span><span class="sxs-lookup"><span data-stu-id="fc233-157">If this parameter is omitted and the request method is POST, `Invoke-WebRequest` sets the content type to application/x-www-form-urlencoded.</span></span> <span data-ttu-id="fc233-158">Anders is het inhouds type niet opgegeven in de aanroep.</span><span class="sxs-lookup"><span data-stu-id="fc233-158">Otherwise, the content type is not specified in the call.</span></span>

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

### <span data-ttu-id="fc233-159">-Credential</span><span class="sxs-lookup"><span data-stu-id="fc233-159">-Credential</span></span>

<span data-ttu-id="fc233-160">Hiermee geeft u een gebruikers account op dat gemachtigd is om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="fc233-160">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="fc233-161">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="fc233-161">The default is the current user.</span></span>

<span data-ttu-id="fc233-162">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**, of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="fc233-162">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="fc233-163">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="fc233-163">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="fc233-164">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="fc233-164">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc233-165">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="fc233-165">-DisableKeepAlive</span></span>

<span data-ttu-id="fc233-166">Geeft aan dat de cmdlet de **keepalive** -waarde in de http-header instelt op **False**.</span><span class="sxs-lookup"><span data-stu-id="fc233-166">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to **False**.</span></span> <span data-ttu-id="fc233-167">Standaard is **keepalive** ingesteld op **True**.</span><span class="sxs-lookup"><span data-stu-id="fc233-167">By default, **KeepAlive** is **True**.</span></span> <span data-ttu-id="fc233-168">Met **keepalive** wordt een permanente verbinding met de server tot stand gebracht om volgende aanvragen te vergemakkelijken.</span><span class="sxs-lookup"><span data-stu-id="fc233-168">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="fc233-169">-Headers</span><span class="sxs-lookup"><span data-stu-id="fc233-169">-Headers</span></span>

<span data-ttu-id="fc233-170">Hiermee geeft u de kopteksten van de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="fc233-170">Specifies the headers of the web request.</span></span> <span data-ttu-id="fc233-171">Voer een hash-tabel of-woorden lijst in.</span><span class="sxs-lookup"><span data-stu-id="fc233-171">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="fc233-172">Gebruik de **agent** -para meter om de **agent** headers in te stellen.</span><span class="sxs-lookup"><span data-stu-id="fc233-172">To set **UserAgent** headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="fc233-173">U kunt deze para meter niet gebruiken om de headers van **User agent** of cookie op te geven.</span><span class="sxs-lookup"><span data-stu-id="fc233-173">You cannot use this parameter to specify **UserAgent** or cookie headers.</span></span>

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

### <span data-ttu-id="fc233-174">-Inbestand</span><span class="sxs-lookup"><span data-stu-id="fc233-174">-InFile</span></span>

<span data-ttu-id="fc233-175">Hiermee wordt de inhoud van de webaanvraag opgehaald uit een bestand.</span><span class="sxs-lookup"><span data-stu-id="fc233-175">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="fc233-176">Voer een pad en een bestands naam in.</span><span class="sxs-lookup"><span data-stu-id="fc233-176">Enter a path and file name.</span></span> <span data-ttu-id="fc233-177">Als u het pad weglaat, de standaard instelling is de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="fc233-177">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="fc233-178">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="fc233-178">-MaximumRedirection</span></span>

<span data-ttu-id="fc233-179">Hiermee geeft u op hoe vaak Power shell een verbinding met een alternatieve URI (Uniform Resource Identifier) omleidt voordat de verbinding is mislukt.</span><span class="sxs-lookup"><span data-stu-id="fc233-179">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="fc233-180">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="fc233-180">The default value is 5.</span></span> <span data-ttu-id="fc233-181">Een waarde van 0 (nul) voor komt dat alle omleidingen.</span><span class="sxs-lookup"><span data-stu-id="fc233-181">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="fc233-182">-Methode</span><span class="sxs-lookup"><span data-stu-id="fc233-182">-Method</span></span>

<span data-ttu-id="fc233-183">Hiermee geeft u de methode op die voor de webaanvraag wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fc233-183">Specifies the method used for the web request.</span></span> <span data-ttu-id="fc233-184">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="fc233-184">The acceptable values for this parameter are:</span></span>

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
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc233-185">-Outfile</span><span class="sxs-lookup"><span data-stu-id="fc233-185">-OutFile</span></span>

<span data-ttu-id="fc233-186">Hiermee geeft u het uitvoer bestand op waarvoor deze cmdlet de antwoord tekst opslaat.</span><span class="sxs-lookup"><span data-stu-id="fc233-186">Specifies the output file for which this cmdlet saves the response body.</span></span> <span data-ttu-id="fc233-187">Voer een pad en een bestands naam in.</span><span class="sxs-lookup"><span data-stu-id="fc233-187">Enter a path and file name.</span></span>
<span data-ttu-id="fc233-188">Als u het pad weglaat, de standaard instelling is de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="fc233-188">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="fc233-189">`Invoke-WebRequest`De resultaten worden standaard naar de pijp lijn geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="fc233-189">By default, `Invoke-WebRequest` returns the results to the pipeline.</span></span> <span data-ttu-id="fc233-190">Als u de resultaten naar een bestand en naar de pijp lijn wilt verzenden, gebruikt u de para meter **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="fc233-190">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="fc233-191">-PassThru</span><span class="sxs-lookup"><span data-stu-id="fc233-191">-PassThru</span></span>

<span data-ttu-id="fc233-192">Geeft aan dat de cmdlet de resultaten retourneert, naast het schrijven naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="fc233-192">Indicates that the cmdlet returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="fc233-193">Deze para meter is alleen geldig wanneer de **outfile** -para meter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fc233-193">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="fc233-194">-Proxy</span><span class="sxs-lookup"><span data-stu-id="fc233-194">-Proxy</span></span>

<span data-ttu-id="fc233-195">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="fc233-195">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>
<span data-ttu-id="fc233-196">Voer de URI van een netwerk proxy server in.</span><span class="sxs-lookup"><span data-stu-id="fc233-196">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="fc233-197">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="fc233-197">-ProxyCredential</span></span>

<span data-ttu-id="fc233-198">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="fc233-198">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="fc233-199">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="fc233-199">The default is the current user.</span></span>

<span data-ttu-id="fc233-200">Typ een gebruikers naam, zoals `User01` of `Domain01\User01` , of voer een **PSCredential** -object in, zoals het certificaat dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fc233-200">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="fc233-201">Deze para meter is alleen geldig wanneer de **proxy** parameter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fc233-201">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="fc233-202">U kunt de para meters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="fc233-202">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc233-203">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="fc233-203">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="fc233-204">Geeft aan dat de cmdlet de referenties van de huidige gebruiker gebruikt om toegang te krijgen tot de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="fc233-204">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="fc233-205">Deze para meter is alleen geldig wanneer de **proxy** parameter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fc233-205">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="fc233-206">U kunt de para meters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="fc233-206">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="fc233-207">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="fc233-207">-SessionVariable</span></span>

<span data-ttu-id="fc233-208">Hiermee geeft u een variabele op waarvoor deze cmdlet een sessie voor een webaanvraag maakt en opslaat in de waarde.</span><span class="sxs-lookup"><span data-stu-id="fc233-208">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="fc233-209">Geef een naam op voor de variabele zonder het dollar teken ( `$` )-symbool.</span><span class="sxs-lookup"><span data-stu-id="fc233-209">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="fc233-210">Wanneer u een sessie variabele opgeeft, `Invoke-WebRequest` maakt een webaanvraag sessie object en wijst deze toe aan een variabele met de opgegeven naam in uw Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="fc233-210">When you specify a session variable, `Invoke-WebRequest` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="fc233-211">U kunt de variabele in uw sessie gebruiken zodra de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="fc233-211">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="fc233-212">In tegens telling tot een externe sessie is de sessie voor webaanvragen geen permanente verbinding.</span><span class="sxs-lookup"><span data-stu-id="fc233-212">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="fc233-213">Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximum omleidings waarde en de teken reeks van de gebruikers agent.</span><span class="sxs-lookup"><span data-stu-id="fc233-213">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="fc233-214">U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="fc233-214">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="fc233-215">Als u de webaanvraag sessie in volgende webaanvragen wilt gebruiken, geeft u de sessie variabele op in de waarde van de para meter **websessie** .</span><span class="sxs-lookup"><span data-stu-id="fc233-215">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="fc233-216">Power shell gebruikt de gegevens in het sessie object voor webaanvragen bij het tot stand brengen van de nieuwe verbinding.</span><span class="sxs-lookup"><span data-stu-id="fc233-216">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="fc233-217">Als u een waarde in de sessie voor webaanvragen wilt overschrijven, gebruikt u een cmdlet-para meter, zoals **User agent** of **Credential**.</span><span class="sxs-lookup"><span data-stu-id="fc233-217">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="fc233-218">Parameter waarden hebben prioriteit boven waarden in de webaanvraag sessie.</span><span class="sxs-lookup"><span data-stu-id="fc233-218">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="fc233-219">U kunt de para meters **SessionVariable** en **websession** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="fc233-219">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="fc233-220">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="fc233-220">-TimeoutSec</span></span>

<span data-ttu-id="fc233-221">Hiermee geeft u op hoe lang de aanvraag in behandeling kan zijn voordat er een time-out optreedt. Voer een waarde in seconden in.</span><span class="sxs-lookup"><span data-stu-id="fc233-221">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="fc233-222">De standaard waarde, 0, geeft een onbeperkte time-outwaarde.</span><span class="sxs-lookup"><span data-stu-id="fc233-222">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="fc233-223">Het kan tot vijf tien seconden duren voordat een Domain Name System query (DNS) wordt uitgevoerd of een time-out kan worden geretourneerd. Als uw aanvraag een hostnaam bevat waarvoor omzetting vereist is en u **TimeoutSec** instelt op een waarde die groter is dan nul, maar minder dan 15 seconden, kan het vijf tien seconden of langer duren **voordat een** webuitzondering wordt gegenereerd en er een time-out optreedt voor uw aanvraag.</span><span class="sxs-lookup"><span data-stu-id="fc233-223">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a **WebException** is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="fc233-224">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="fc233-224">-TransferEncoding</span></span>

<span data-ttu-id="fc233-225">Hiermee geeft u een waarde op voor de header van de HTTP-reactie voor overdracht/versleuteling.</span><span class="sxs-lookup"><span data-stu-id="fc233-225">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="fc233-226">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="fc233-226">The acceptable values for this parameter are:</span></span>

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

### <span data-ttu-id="fc233-227">-URI</span><span class="sxs-lookup"><span data-stu-id="fc233-227">-Uri</span></span>

<span data-ttu-id="fc233-228">Hiermee geeft u de URI (Uniform Resource Identifier) op van de Internet bron waarnaar de webaanvraag wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="fc233-228">Specifies the Uniform Resource Identifier (URI) of the Internet resource to which the web request is sent.</span></span> <span data-ttu-id="fc233-229">Voer een URI in.</span><span class="sxs-lookup"><span data-stu-id="fc233-229">Enter a URI.</span></span> <span data-ttu-id="fc233-230">Deze para meter ondersteunt HTTP-, HTTPS-, FTP-en FILE-waarden.</span><span class="sxs-lookup"><span data-stu-id="fc233-230">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="fc233-231">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="fc233-231">This parameter is required.</span></span>

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

### <span data-ttu-id="fc233-232">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="fc233-232">-UseBasicParsing</span></span>

<span data-ttu-id="fc233-233">Geeft aan dat de cmdlet gebruikmaakt van het antwoord object voor HTML-inhoud zonder dat het parseren van Document Object Model (DOM) wordt geparseerd.</span><span class="sxs-lookup"><span data-stu-id="fc233-233">Indicates that the cmdlet uses the response object for HTML content without Document Object Model (DOM) parsing.</span></span> <span data-ttu-id="fc233-234">Deze para meter is vereist als Internet Explorer niet is geïnstalleerd op de computers, zoals op een Server Core-installatie van een Windows Server-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="fc233-234">This parameter is required when Internet Explorer is not installed on the computers, such as on a Server Core installation of a Windows Server operating system.</span></span>

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

### <span data-ttu-id="fc233-235">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="fc233-235">-UseDefaultCredentials</span></span>

<span data-ttu-id="fc233-236">Geeft aan dat de cmdlet de referenties van de huidige gebruiker gebruikt om de webaanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="fc233-236">Indicates that the cmdlet uses the credentials of the current user to send the web request.</span></span>

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

### <span data-ttu-id="fc233-237">-User agent</span><span class="sxs-lookup"><span data-stu-id="fc233-237">-UserAgent</span></span>

<span data-ttu-id="fc233-238">Hiermee geeft u een teken reeks voor de gebruikers agent op voor de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="fc233-238">Specifies a user agent string for the web request.</span></span> <span data-ttu-id="fc233-239">De standaard gebruikers agent is vergelijkbaar `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` met kleine variaties voor elk besturings systeem en platform.</span><span class="sxs-lookup"><span data-stu-id="fc233-239">The default user agent is similar to `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="fc233-240">Als u een website wilt testen met de standaard teken reeks van de gebruikers agent die wordt gebruikt door de meeste Internet browsers, gebruikt u de eigenschappen van de [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) -klasse, zoals Chrome, Firefox, InternetExplorer, Opera en Safari.</span><span class="sxs-lookup"><span data-stu-id="fc233-240">To test a website with the standard user agent string that is used by most Internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span> <span data-ttu-id="fc233-241">De volgende opdracht maakt bijvoorbeeld gebruik van de teken reeks van de gebruikers agent voor Internet Explorer: `Invoke-WebRequest -Uri https://website.com/ -UserAgent ([Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer)`</span><span class="sxs-lookup"><span data-stu-id="fc233-241">For example, the following command uses the user agent string for Internet Explorer: `Invoke-WebRequest -Uri https://website.com/ -UserAgent ([Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer)`</span></span>

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

### <span data-ttu-id="fc233-242">-Websessie</span><span class="sxs-lookup"><span data-stu-id="fc233-242">-WebSession</span></span>

<span data-ttu-id="fc233-243">Hiermee geeft u een sessie voor webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="fc233-243">Specifies a web request session.</span></span> <span data-ttu-id="fc233-244">Voer de naam van de variabele in, met inbegrip van het dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="fc233-244">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="fc233-245">Als u een waarde in de sessie voor webaanvragen wilt overschrijven, gebruikt u een cmdlet-para meter, zoals **User agent** of **Credential**.</span><span class="sxs-lookup"><span data-stu-id="fc233-245">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="fc233-246">Parameter waarden hebben prioriteit boven waarden in de webaanvraag sessie.</span><span class="sxs-lookup"><span data-stu-id="fc233-246">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="fc233-247">In tegens telling tot een externe sessie is de sessie voor webaanvragen geen permanente verbinding.</span><span class="sxs-lookup"><span data-stu-id="fc233-247">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="fc233-248">Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximum omleidings waarde en de teken reeks van de gebruikers agent.</span><span class="sxs-lookup"><span data-stu-id="fc233-248">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="fc233-249">U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="fc233-249">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="fc233-250">Als u een webaanvraag sessie wilt maken, voert u een naam in voor de variabele (zonder een dollar teken) in de waarde van de para meter **SessionVariable** van een `Invoke-WebRequest` opdracht.</span><span class="sxs-lookup"><span data-stu-id="fc233-250">To create a web request session, enter a variable name (without a dollar sign) in the value of the **SessionVariable** parameter of an `Invoke-WebRequest` command.</span></span> <span data-ttu-id="fc233-251">`Invoke-WebRequest` Hiermee maakt u de sessie en slaat u deze op in de variabele.</span><span class="sxs-lookup"><span data-stu-id="fc233-251">`Invoke-WebRequest` creates the session and saves it in the variable.</span></span> <span data-ttu-id="fc233-252">Gebruik in volgende opdrachten de variabele als de waarde van de para meter **websession** .</span><span class="sxs-lookup"><span data-stu-id="fc233-252">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="fc233-253">U kunt de para meters **SessionVariable** en **websession** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="fc233-253">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="fc233-254">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fc233-254">CommonParameters</span></span>

<span data-ttu-id="fc233-255">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="fc233-255">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="fc233-256">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fc233-256">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fc233-257">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="fc233-257">Inputs</span></span>

### <span data-ttu-id="fc233-258">System. object</span><span class="sxs-lookup"><span data-stu-id="fc233-258">System.Object</span></span>

<span data-ttu-id="fc233-259">U kunt de hoofd tekst van een webaanvraag door sluizen naar `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="fc233-259">You can pipe the body of a web request to `Invoke-WebRequest`.</span></span>

## <span data-ttu-id="fc233-260">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="fc233-260">Outputs</span></span>

### <span data-ttu-id="fc233-261">Microsoft.PowerShell.Commands.HtmlWebResponseObject</span><span class="sxs-lookup"><span data-stu-id="fc233-261">Microsoft.PowerShell.Commands.HtmlWebResponseObject</span></span>

## <span data-ttu-id="fc233-262">Notities</span><span class="sxs-lookup"><span data-stu-id="fc233-262">Notes</span></span>

## <span data-ttu-id="fc233-263">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="fc233-263">Related Links</span></span>

[<span data-ttu-id="fc233-264">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="fc233-264">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="fc233-265">ConvertFrom-JSON</span><span class="sxs-lookup"><span data-stu-id="fc233-265">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="fc233-266">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="fc233-266">ConvertTo-Json</span></span>](ConvertTo-Json.md)
