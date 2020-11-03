---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: 25da6262e93be3e3749aabaf4950e2fbcd91ff5c
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/10/2020
ms.locfileid: "93251740"
---
# <span data-ttu-id="4d898-103">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="4d898-103">Invoke-WebRequest</span></span>

## <span data-ttu-id="4d898-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="4d898-104">SYNOPSIS</span></span>
<span data-ttu-id="4d898-105">Hiermee wordt inhoud opgehaald van een webpagina op internet.</span><span class="sxs-lookup"><span data-stu-id="4d898-105">Gets content from a web page on the Internet.</span></span>

## <span data-ttu-id="4d898-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="4d898-106">SYNTAX</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>] [-SessionVariable <String>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-CertificateThumbprint <String>]
 [-Certificate <X509Certificate>] [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>]
 [-Headers <IDictionary>] [-MaximumRedirection <Int32>] [-Method <WebRequestMethod>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>] [-ContentType <String>]
 [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="4d898-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4d898-107">DESCRIPTION</span></span>

<span data-ttu-id="4d898-108">De `Invoke-WebRequest` cmdlet verzendt http-, HTTPS-, FTP-en file-aanvragen naar een webpagina of webservice.</span><span class="sxs-lookup"><span data-stu-id="4d898-108">The `Invoke-WebRequest` cmdlet sends HTTP, HTTPS, FTP, and FILE requests to a web page or web service.</span></span>
<span data-ttu-id="4d898-109">Hiermee wordt het antwoord geparseerd en worden verzamelingen van formulieren, koppelingen, afbeeldingen en andere belang rijke HTML-elementen geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4d898-109">It parses the response and returns collections of forms, links, images, and other significant HTML elements.</span></span>

<span data-ttu-id="4d898-110">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4d898-110">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="4d898-111">Standaard kan script code op de webpagina worden uitgevoerd wanneer de pagina wordt geparseerd om de eigenschap in te vullen `ParsedHtml` .</span><span class="sxs-lookup"><span data-stu-id="4d898-111">By default, script code in the web page may be run when the page is being parsed to populate the `ParsedHtml` property.</span></span>
> <span data-ttu-id="4d898-112">Gebruik de `-UseBasicParsing` Schakel optie om dit te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="4d898-112">Use the `-UseBasicParsing` switch to suppress this.</span></span>

## <span data-ttu-id="4d898-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="4d898-113">EXAMPLES</span></span>

### <span data-ttu-id="4d898-114">Voor beeld 1: een webaanvraag verzenden</span><span class="sxs-lookup"><span data-stu-id="4d898-114">Example 1: Send a web request</span></span>

<span data-ttu-id="4d898-115">Met deze opdracht wordt de `Invoke-WebRequest` cmdlet gebruikt voor het verzenden van een webaanvraag naar de Bing.com-site.</span><span class="sxs-lookup"><span data-stu-id="4d898-115">This command uses the `Invoke-WebRequest` cmdlet to send a web request to the Bing.com site.</span></span>

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

<span data-ttu-id="4d898-116">Met de eerste opdracht wordt de aanvraag uitgegeven en wordt het antwoord in de `$R` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="4d898-116">The first command issues the request and saves the response in the `$R` variable.</span></span>

<span data-ttu-id="4d898-117">Met de tweede opdracht wordt gefilterd op de objecten in **de eigenschap voor de gegevens, waarbij** de eigenschap **name** als "\* waarde" is en de **tagName** "input" is.</span><span class="sxs-lookup"><span data-stu-id="4d898-117">The second command filters the objects in the **AllElements** property where the **name** property is like "\* Value" and the **tagName** is "INPUT".</span></span> <span data-ttu-id="4d898-118">De gefilterde resultaten worden gepiped om `Select-Object` de **naam** en **waarde** -eigenschappen te selecteren.</span><span class="sxs-lookup"><span data-stu-id="4d898-118">The filtered results are piped to `Select-Object` to select the **name** and **value** properties.</span></span>

### <span data-ttu-id="4d898-119">Voor beeld 2: een stateful webservice gebruiken</span><span class="sxs-lookup"><span data-stu-id="4d898-119">Example 2: Use a stateful web service</span></span>

<span data-ttu-id="4d898-120">In dit voor beeld ziet u hoe u de `Invoke-WebRequest` cmdlet gebruikt met een stateful webservice, zoals Facebook.</span><span class="sxs-lookup"><span data-stu-id="4d898-120">This example shows how to use the `Invoke-WebRequest` cmdlet with a stateful web service, such as Facebook.</span></span>

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

<span data-ttu-id="4d898-121">De eerste opdracht gebruikt de `Invoke-WebRequest` cmdlet om een aanmeldings aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="4d898-121">The first command uses the `Invoke-WebRequest` cmdlet to send a sign-in request.</span></span> <span data-ttu-id="4d898-122">Met de opdracht wordt de waarde ' FB ' opgegeven voor de waarde van de para meter **SessionVariable** en wordt het resultaat opgeslagen in de `$R` variabele.</span><span class="sxs-lookup"><span data-stu-id="4d898-122">The command specifies a value of "FB" for the value of the **SessionVariable** parameter, and saves the result in the `$R` variable.</span></span> <span data-ttu-id="4d898-123">Wanneer de opdracht is voltooid, `$R` bevat de variabele een **HtmlWebResponseObject** en `$FB` bevat de variabele een **WebRequestSession** -object.</span><span class="sxs-lookup"><span data-stu-id="4d898-123">When the command completes, the `$R` variable contains an **HtmlWebResponseObject** and the `$FB` variable contains a **WebRequestSession** object.</span></span>

<span data-ttu-id="4d898-124">Nadat de `Invoke-WebRequest` cmdlet is aangemeld bij Facebook, geeft de eigenschap **StatusDescription** van het Web Response-object in de `$R` variabele aan dat de gebruiker is aangemeld.</span><span class="sxs-lookup"><span data-stu-id="4d898-124">After the `Invoke-WebRequest` cmdlet signs in to facebook, the **StatusDescription** property of the web response object in the `$R` variable indicates that the user is signed in successfully.</span></span>

### <span data-ttu-id="4d898-125">Voor beeld 3: koppelingen van een webpagina ophalen</span><span class="sxs-lookup"><span data-stu-id="4d898-125">Example 3: Get links from a web page</span></span>

<span data-ttu-id="4d898-126">Met deze opdracht worden de koppelingen op een webpagina opgehaald.</span><span class="sxs-lookup"><span data-stu-id="4d898-126">This command gets the links in a web page.</span></span>

```powershell
(Invoke-WebRequest -Uri "https://devblogs.microsoft.com/powershell/").Links.Href
```

<span data-ttu-id="4d898-127">`Invoke-WebRequest`Met de cmdlet wordt de inhoud van de webpagina opgehaald.</span><span class="sxs-lookup"><span data-stu-id="4d898-127">The `Invoke-WebRequest` cmdlet gets the web page content.</span></span> <span data-ttu-id="4d898-128">De eigenschap **links** van het geretourneerde **HtmlWebResponseObject** wordt gebruikt om de eigenschap **href** van elke koppeling weer te geven.</span><span class="sxs-lookup"><span data-stu-id="4d898-128">Then the **Links** property of the returned **HtmlWebResponseObject** is used to display the **Href** property of each link.</span></span>

### <span data-ttu-id="4d898-129">Voor beeld 4: berichten over niet-geslaagde artikelen van Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="4d898-129">Example 4: Catch non success messages from Invoke-WebRequest</span></span>

<span data-ttu-id="4d898-130">Wanneer er `Invoke-WebRequest` een niet-geslaagd http-bericht wordt aangetroffen (404, 500, etc.), wordt er geen uitvoer geretourneerd en wordt er een afsluit fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="4d898-130">When `Invoke-WebRequest` encounters a non-success HTTP message (404, 500, etc.), it returns no output and throws a terminating error.</span></span> <span data-ttu-id="4d898-131">Als u de fout wilt opvangen en de **status** code wilt weer geven, kunt u de uitvoering in een `try/catch` blok insluiten.</span><span class="sxs-lookup"><span data-stu-id="4d898-131">To catch the error and view the **StatusCode** you can enclose execution in a `try/catch` block.</span></span> <span data-ttu-id="4d898-132">In het volgende voor beeld ziet u hoe u dit kunt doen.</span><span class="sxs-lookup"><span data-stu-id="4d898-132">The following example shows how to accomplish this.</span></span>

```powershell
try
{
    $response = Invoke-WebRequest -Uri "www.microsoft.com/unkownhost" -ErrorAction Stop
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

<span data-ttu-id="4d898-133">De eerste opdracht roept `Invoke-WebRequest` met een **Error Action** van **Stop** , waarmee wordt geforceerd dat er `Invoke-WebRequest` een afsluit fout optreedt bij mislukte aanvragen.</span><span class="sxs-lookup"><span data-stu-id="4d898-133">The first command calls `Invoke-WebRequest` with an **ErrorAction** of **Stop** , which forces `Invoke-WebRequest` to throw a terminating error on any failed requests.</span></span> <span data-ttu-id="4d898-134">De afsluit fout wordt onderschept door het `catch` blok dat de **status** code van het **uitzonderings** object ophaalt.</span><span class="sxs-lookup"><span data-stu-id="4d898-134">The terminating error is caught by the `catch` block which retrieves the **StatusCode** from the **Exception** object.</span></span>

## <span data-ttu-id="4d898-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4d898-135">PARAMETERS</span></span>

### <span data-ttu-id="4d898-136">-Hoofd tekst</span><span class="sxs-lookup"><span data-stu-id="4d898-136">-Body</span></span>

<span data-ttu-id="4d898-137">Hiermee geeft u de hoofd tekst van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="4d898-137">Specifies the body of the request.</span></span>
<span data-ttu-id="4d898-138">De hoofd tekst is de inhoud van de aanvraag die de headers volgt.</span><span class="sxs-lookup"><span data-stu-id="4d898-138">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="4d898-139">U kunt ook de waarde van een hoofd tekst sluist naar `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="4d898-139">You can also pipe a body value to `Invoke-WebRequest`.</span></span>

<span data-ttu-id="4d898-140">De para meter **Body** kan worden gebruikt om een lijst met query parameters op te geven of de inhoud van het antwoord op te geven.</span><span class="sxs-lookup"><span data-stu-id="4d898-140">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="4d898-141">Wanneer de invoer een GET-aanvraag is en de hoofd tekst een **IDictionary** is (meestal een hash-tabel), wordt de hoofd tekst als query parameters toegevoegd aan de URI.</span><span class="sxs-lookup"><span data-stu-id="4d898-141">When the input is a GET request and the body is an **IDictionary** (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="4d898-142">Voor andere GET-aanvragen wordt de hoofd tekst ingesteld als de waarde van de hoofd tekst van de aanvraag in de standaard `name=value` indeling.</span><span class="sxs-lookup"><span data-stu-id="4d898-142">For other GET requests, the body is set as the value of the request body in the standard `name=value` format.</span></span>

<span data-ttu-id="4d898-143">Wanneer de hoofd tekst een formulier is of de uitvoer van een `Invoke-WebRequest` aanroep, stelt Power shell de aanvraag inhoud in op de formulier velden.</span><span class="sxs-lookup"><span data-stu-id="4d898-143">When the body is a form, or it is the output of an `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>
<span data-ttu-id="4d898-144">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="4d898-144">For example:</span></span>

`$r = Invoke-WebRequest https://website.com/login.aspx`
`$r.Forms\[0\].Name = "MyName"`
`$r.Forms\[0\].Password = "MyPassword"`
`Invoke-RestMethod https://website.com/service.aspx -Body $r`

- <span data-ttu-id="4d898-145">of</span><span class="sxs-lookup"><span data-stu-id="4d898-145">or -</span></span>

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

### <span data-ttu-id="4d898-146">-Certificaat</span><span class="sxs-lookup"><span data-stu-id="4d898-146">-Certificate</span></span>

<span data-ttu-id="4d898-147">Hiermee geeft u het client certificaat op dat wordt gebruikt voor een beveiligde webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="4d898-147">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="4d898-148">Voer een variabele in die een certificaat of een opdracht of expressie bevat waarmee het certificaat wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="4d898-148">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="4d898-149">Als u een certificaat wilt zoeken, gebruikt `Get-PfxCertificate` of gebruikt u de `Get-ChildItem` cmdlet in het **certificaat** `Cert:` station.</span><span class="sxs-lookup"><span data-stu-id="4d898-149">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the **Certificate** (`Cert:`) drive.</span></span> <span data-ttu-id="4d898-150">Als het certificaat ongeldig is of niet voldoende autoriteit heeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="4d898-150">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="4d898-151">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="4d898-151">-CertificateThumbprint</span></span>

<span data-ttu-id="4d898-152">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat gemachtigd is om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="4d898-152">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="4d898-153">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="4d898-153">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="4d898-154">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="4d898-154">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="4d898-155">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="4d898-155">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="4d898-156">Gebruik de `Get-Item` `Get-ChildItem` opdracht of in het Power Shell-station om een certificaat vingerafdruk te verkrijgen `Cert:` .</span><span class="sxs-lookup"><span data-stu-id="4d898-156">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

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

### <span data-ttu-id="4d898-157">-Content type</span><span class="sxs-lookup"><span data-stu-id="4d898-157">-ContentType</span></span>

<span data-ttu-id="4d898-158">Hiermee geeft u het type inhoud van de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="4d898-158">Specifies the content type of the web request.</span></span>

<span data-ttu-id="4d898-159">Als deze para meter wordt wegge laten en de aanvraag methode POST is, `Invoke-WebRequest` wordt het inhouds type ingesteld op Application/x-www-form-urlencoded.</span><span class="sxs-lookup"><span data-stu-id="4d898-159">If this parameter is omitted and the request method is POST, `Invoke-WebRequest` sets the content type to application/x-www-form-urlencoded.</span></span> <span data-ttu-id="4d898-160">Anders is het inhouds type niet opgegeven in de aanroep.</span><span class="sxs-lookup"><span data-stu-id="4d898-160">Otherwise, the content type is not specified in the call.</span></span>

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

### <span data-ttu-id="4d898-161">-Credential</span><span class="sxs-lookup"><span data-stu-id="4d898-161">-Credential</span></span>

<span data-ttu-id="4d898-162">Hiermee geeft u een gebruikers account op dat gemachtigd is om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="4d898-162">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="4d898-163">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="4d898-163">The default is the current user.</span></span>

<span data-ttu-id="4d898-164">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="4d898-164">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="4d898-165">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="4d898-165">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="4d898-166">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="4d898-166">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="4d898-167">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="4d898-167">-DisableKeepAlive</span></span>

<span data-ttu-id="4d898-168">Geeft aan dat de cmdlet de **keepalive** -waarde in de http-header instelt op **False**.</span><span class="sxs-lookup"><span data-stu-id="4d898-168">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to **False**.</span></span> <span data-ttu-id="4d898-169">Standaard is **keepalive** ingesteld op **True**.</span><span class="sxs-lookup"><span data-stu-id="4d898-169">By default, **KeepAlive** is **True**.</span></span> <span data-ttu-id="4d898-170">Met **keepalive** wordt een permanente verbinding met de server tot stand gebracht om volgende aanvragen te vergemakkelijken.</span><span class="sxs-lookup"><span data-stu-id="4d898-170">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="4d898-171">-Headers</span><span class="sxs-lookup"><span data-stu-id="4d898-171">-Headers</span></span>

<span data-ttu-id="4d898-172">Hiermee geeft u de kopteksten van de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="4d898-172">Specifies the headers of the web request.</span></span> <span data-ttu-id="4d898-173">Voer een hash-tabel of-woorden lijst in.</span><span class="sxs-lookup"><span data-stu-id="4d898-173">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="4d898-174">Gebruik de **agent** -para meter om de **agent** headers in te stellen.</span><span class="sxs-lookup"><span data-stu-id="4d898-174">To set **UserAgent** headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="4d898-175">U kunt deze para meter niet gebruiken om de headers van **User agent** of cookie op te geven.</span><span class="sxs-lookup"><span data-stu-id="4d898-175">You cannot use this parameter to specify **UserAgent** or cookie headers.</span></span>

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

### <span data-ttu-id="4d898-176">-Inbestand</span><span class="sxs-lookup"><span data-stu-id="4d898-176">-InFile</span></span>

<span data-ttu-id="4d898-177">Hiermee wordt de inhoud van de webaanvraag opgehaald uit een bestand.</span><span class="sxs-lookup"><span data-stu-id="4d898-177">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="4d898-178">Voer een pad en een bestands naam in.</span><span class="sxs-lookup"><span data-stu-id="4d898-178">Enter a path and file name.</span></span> <span data-ttu-id="4d898-179">Als u het pad weglaat, de standaard instelling is de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="4d898-179">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="4d898-180">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="4d898-180">-MaximumRedirection</span></span>

<span data-ttu-id="4d898-181">Hiermee geeft u op hoe vaak Power shell een verbinding met een alternatieve URI (Uniform Resource Identifier) omleidt voordat de verbinding is mislukt.</span><span class="sxs-lookup"><span data-stu-id="4d898-181">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="4d898-182">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="4d898-182">The default value is 5.</span></span> <span data-ttu-id="4d898-183">Een waarde van 0 (nul) voor komt dat alle omleidingen.</span><span class="sxs-lookup"><span data-stu-id="4d898-183">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="4d898-184">-Methode</span><span class="sxs-lookup"><span data-stu-id="4d898-184">-Method</span></span>

<span data-ttu-id="4d898-185">Hiermee geeft u de methode op die voor de webaanvraag wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4d898-185">Specifies the method used for the web request.</span></span> <span data-ttu-id="4d898-186">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="4d898-186">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4d898-187">Standaard</span><span class="sxs-lookup"><span data-stu-id="4d898-187">Default</span></span>
- <span data-ttu-id="4d898-188">Verwijderen</span><span class="sxs-lookup"><span data-stu-id="4d898-188">Delete</span></span>
- <span data-ttu-id="4d898-189">Ophalen</span><span class="sxs-lookup"><span data-stu-id="4d898-189">Get</span></span>
- <span data-ttu-id="4d898-190">Head</span><span class="sxs-lookup"><span data-stu-id="4d898-190">Head</span></span>
- <span data-ttu-id="4d898-191">Samenvoegen</span><span class="sxs-lookup"><span data-stu-id="4d898-191">Merge</span></span>
- <span data-ttu-id="4d898-192">Opties</span><span class="sxs-lookup"><span data-stu-id="4d898-192">Options</span></span>
- <span data-ttu-id="4d898-193">Patch</span><span class="sxs-lookup"><span data-stu-id="4d898-193">Patch</span></span>
- <span data-ttu-id="4d898-194">Plaatsen</span><span class="sxs-lookup"><span data-stu-id="4d898-194">Post</span></span>
- <span data-ttu-id="4d898-195">Put</span><span class="sxs-lookup"><span data-stu-id="4d898-195">Put</span></span>
- <span data-ttu-id="4d898-196">Tracering</span><span class="sxs-lookup"><span data-stu-id="4d898-196">Trace</span></span>

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

### <span data-ttu-id="4d898-197">-Outfile</span><span class="sxs-lookup"><span data-stu-id="4d898-197">-OutFile</span></span>

<span data-ttu-id="4d898-198">Hiermee geeft u het uitvoer bestand op waarvoor deze cmdlet de antwoord tekst opslaat.</span><span class="sxs-lookup"><span data-stu-id="4d898-198">Specifies the output file for which this cmdlet saves the response body.</span></span> <span data-ttu-id="4d898-199">Voer een pad en een bestands naam in.</span><span class="sxs-lookup"><span data-stu-id="4d898-199">Enter a path and file name.</span></span>
<span data-ttu-id="4d898-200">Als u het pad weglaat, de standaard instelling is de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="4d898-200">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="4d898-201">`Invoke-WebRequest`De resultaten worden standaard naar de pijp lijn geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4d898-201">By default, `Invoke-WebRequest` returns the results to the pipeline.</span></span> <span data-ttu-id="4d898-202">Als u de resultaten naar een bestand en naar de pijp lijn wilt verzenden, gebruikt u de para meter **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="4d898-202">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="4d898-203">-PassThru</span><span class="sxs-lookup"><span data-stu-id="4d898-203">-PassThru</span></span>

<span data-ttu-id="4d898-204">Geeft aan dat de cmdlet de resultaten retourneert, naast het schrijven naar een bestand.</span><span class="sxs-lookup"><span data-stu-id="4d898-204">Indicates that the cmdlet returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="4d898-205">Deze para meter is alleen geldig wanneer de **outfile** -para meter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4d898-205">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="4d898-206">-Proxy</span><span class="sxs-lookup"><span data-stu-id="4d898-206">-Proxy</span></span>

<span data-ttu-id="4d898-207">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="4d898-207">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>
<span data-ttu-id="4d898-208">Voer de URI van een netwerk proxy server in.</span><span class="sxs-lookup"><span data-stu-id="4d898-208">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="4d898-209">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="4d898-209">-ProxyCredential</span></span>

<span data-ttu-id="4d898-210">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="4d898-210">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="4d898-211">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="4d898-211">The default is the current user.</span></span>

<span data-ttu-id="4d898-212">Typ een gebruikers naam, zoals `User01` of `Domain01\User01` , of voer een **PSCredential** -object in, zoals het certificaat dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4d898-212">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="4d898-213">Deze para meter is alleen geldig wanneer de **proxy** parameter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4d898-213">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="4d898-214">U kunt de para meters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="4d898-214">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="4d898-215">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="4d898-215">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="4d898-216">Geeft aan dat de cmdlet de referenties van de huidige gebruiker gebruikt om toegang te krijgen tot de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="4d898-216">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="4d898-217">Deze para meter is alleen geldig wanneer de **proxy** parameter ook in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4d898-217">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="4d898-218">U kunt de para meters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="4d898-218">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="4d898-219">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="4d898-219">-SessionVariable</span></span>

<span data-ttu-id="4d898-220">Hiermee geeft u een variabele op waarvoor deze cmdlet een sessie voor een webaanvraag maakt en opslaat in de waarde.</span><span class="sxs-lookup"><span data-stu-id="4d898-220">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="4d898-221">Geef een naam op voor de variabele zonder het dollar teken ( `$` )-symbool.</span><span class="sxs-lookup"><span data-stu-id="4d898-221">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="4d898-222">Wanneer u een sessie variabele opgeeft, `Invoke-WebRequest` maakt een webaanvraag sessie object en wijst deze toe aan een variabele met de opgegeven naam in uw Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="4d898-222">When you specify a session variable, `Invoke-WebRequest` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="4d898-223">U kunt de variabele in uw sessie gebruiken zodra de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="4d898-223">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="4d898-224">In tegens telling tot een externe sessie is de sessie voor webaanvragen geen permanente verbinding.</span><span class="sxs-lookup"><span data-stu-id="4d898-224">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="4d898-225">Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximum omleidings waarde en de teken reeks van de gebruikers agent.</span><span class="sxs-lookup"><span data-stu-id="4d898-225">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="4d898-226">U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="4d898-226">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="4d898-227">Als u de webaanvraag sessie in volgende webaanvragen wilt gebruiken, geeft u de sessie variabele op in de waarde van de para meter **websessie** .</span><span class="sxs-lookup"><span data-stu-id="4d898-227">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="4d898-228">Power shell gebruikt de gegevens in het sessie object voor webaanvragen bij het tot stand brengen van de nieuwe verbinding.</span><span class="sxs-lookup"><span data-stu-id="4d898-228">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="4d898-229">Als u een waarde in de sessie voor webaanvragen wilt overschrijven, gebruikt u een cmdlet-para meter, zoals **User agent** of **Credential**.</span><span class="sxs-lookup"><span data-stu-id="4d898-229">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="4d898-230">Parameter waarden hebben prioriteit boven waarden in de webaanvraag sessie.</span><span class="sxs-lookup"><span data-stu-id="4d898-230">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="4d898-231">U kunt de para meters **SessionVariable** en **websession** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="4d898-231">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="4d898-232">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="4d898-232">-TimeoutSec</span></span>

<span data-ttu-id="4d898-233">Hiermee geeft u op hoe lang de aanvraag in behandeling kan zijn voordat er een time-out optreedt. Voer een waarde in seconden in.</span><span class="sxs-lookup"><span data-stu-id="4d898-233">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="4d898-234">De standaard waarde, 0, geeft een onbeperkte time-outwaarde.</span><span class="sxs-lookup"><span data-stu-id="4d898-234">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="4d898-235">Het kan tot vijf tien seconden duren voordat een Domain Name System query (DNS) wordt uitgevoerd of een time-out kan worden geretourneerd. Als uw aanvraag een hostnaam bevat waarvoor omzetting vereist is en u **TimeoutSec** instelt op een waarde die groter is dan nul, maar minder dan 15 seconden, kan het vijf tien seconden of langer duren **voordat een** webuitzondering wordt gegenereerd en er een time-out optreedt voor uw aanvraag.</span><span class="sxs-lookup"><span data-stu-id="4d898-235">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a **WebException** is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="4d898-236">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="4d898-236">-TransferEncoding</span></span>

<span data-ttu-id="4d898-237">Hiermee geeft u een waarde op voor de header van de HTTP-reactie voor overdracht/versleuteling.</span><span class="sxs-lookup"><span data-stu-id="4d898-237">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="4d898-238">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="4d898-238">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4d898-239">Gesegmenteerde</span><span class="sxs-lookup"><span data-stu-id="4d898-239">Chunked</span></span>
- <span data-ttu-id="4d898-240">Comprimeren</span><span class="sxs-lookup"><span data-stu-id="4d898-240">Compress</span></span>
- <span data-ttu-id="4d898-241">Deflate</span><span class="sxs-lookup"><span data-stu-id="4d898-241">Deflate</span></span>
- <span data-ttu-id="4d898-242">GZip</span><span class="sxs-lookup"><span data-stu-id="4d898-242">GZip</span></span>
- <span data-ttu-id="4d898-243">Identiteit</span><span class="sxs-lookup"><span data-stu-id="4d898-243">Identity</span></span>

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

### <span data-ttu-id="4d898-244">-URI</span><span class="sxs-lookup"><span data-stu-id="4d898-244">-Uri</span></span>

<span data-ttu-id="4d898-245">Hiermee geeft u de URI (Uniform Resource Identifier) op van de Internet bron waarnaar de webaanvraag wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="4d898-245">Specifies the Uniform Resource Identifier (URI) of the Internet resource to which the web request is sent.</span></span> <span data-ttu-id="4d898-246">Voer een URI in.</span><span class="sxs-lookup"><span data-stu-id="4d898-246">Enter a URI.</span></span> <span data-ttu-id="4d898-247">Deze para meter ondersteunt HTTP-, HTTPS-, FTP-en FILE-waarden.</span><span class="sxs-lookup"><span data-stu-id="4d898-247">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="4d898-248">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="4d898-248">This parameter is required.</span></span>

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

### <span data-ttu-id="4d898-249">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="4d898-249">-UseBasicParsing</span></span>

<span data-ttu-id="4d898-250">Geeft aan dat de cmdlet gebruikmaakt van het antwoord object voor HTML-inhoud zonder dat het parseren van Document Object Model (DOM) wordt geparseerd.</span><span class="sxs-lookup"><span data-stu-id="4d898-250">Indicates that the cmdlet uses the response object for HTML content without Document Object Model (DOM) parsing.</span></span> <span data-ttu-id="4d898-251">Deze para meter is vereist als Internet Explorer niet is geïnstalleerd op de computers, zoals op een Server Core-installatie van een Windows Server-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="4d898-251">This parameter is required when Internet Explorer is not installed on the computers, such as on a Server Core installation of a Windows Server operating system.</span></span>

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

### <span data-ttu-id="4d898-252">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="4d898-252">-UseDefaultCredentials</span></span>

<span data-ttu-id="4d898-253">Geeft aan dat de cmdet de referenties van de huidige gebruiker gebruikt om de webaanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="4d898-253">Indicates that the cmdet uses the credentials of the current user to send the web request.</span></span>

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

### <span data-ttu-id="4d898-254">-User agent</span><span class="sxs-lookup"><span data-stu-id="4d898-254">-UserAgent</span></span>

<span data-ttu-id="4d898-255">Hiermee geeft u een teken reeks voor de gebruikers agent op voor de webaanvraag.</span><span class="sxs-lookup"><span data-stu-id="4d898-255">Specifies a user agent string for the web request.</span></span> <span data-ttu-id="4d898-256">De standaard gebruikers agent is vergelijkbaar `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` met kleine variaties voor elk besturings systeem en platform.</span><span class="sxs-lookup"><span data-stu-id="4d898-256">The default user agent is similar to `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="4d898-257">Als u een website wilt testen met de standaard teken reeks van de gebruikers agent die wordt gebruikt door de meeste Internet browsers, gebruikt u de eigenschappen van de [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) -klasse, zoals Chrome, Firefox, InternetExplorer, Opera en Safari.</span><span class="sxs-lookup"><span data-stu-id="4d898-257">To test a website with the standard user agent string that is used by most Internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span> <span data-ttu-id="4d898-258">De volgende opdracht maakt bijvoorbeeld gebruik van de teken reeks van de gebruikers agent voor Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="4d898-258">For example, the following command uses the user agent string for Internet Explorer</span></span>

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

### <span data-ttu-id="4d898-259">-Websessie</span><span class="sxs-lookup"><span data-stu-id="4d898-259">-WebSession</span></span>

<span data-ttu-id="4d898-260">Hiermee geeft u een sessie voor webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="4d898-260">Specifies a web request session.</span></span> <span data-ttu-id="4d898-261">Voer de naam van de variabele in, met inbegrip van het dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="4d898-261">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="4d898-262">Als u een waarde in de sessie voor webaanvragen wilt overschrijven, gebruikt u een cmdlet-para meter, zoals **User agent** of **Credential**.</span><span class="sxs-lookup"><span data-stu-id="4d898-262">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="4d898-263">Parameter waarden hebben prioriteit boven waarden in de webaanvraag sessie.</span><span class="sxs-lookup"><span data-stu-id="4d898-263">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="4d898-264">In tegens telling tot een externe sessie is de sessie voor webaanvragen geen permanente verbinding.</span><span class="sxs-lookup"><span data-stu-id="4d898-264">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="4d898-265">Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximum omleidings waarde en de teken reeks van de gebruikers agent.</span><span class="sxs-lookup"><span data-stu-id="4d898-265">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="4d898-266">U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.</span><span class="sxs-lookup"><span data-stu-id="4d898-266">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="4d898-267">Als u een webaanvraag sessie wilt maken, voert u een naam in voor de variabele (zonder een dollar teken) in de waarde van de para meter **SessionVariable** van een `Invoke-WebRequest` opdracht.</span><span class="sxs-lookup"><span data-stu-id="4d898-267">To create a web request session, enter a variable name (without a dollar sign) in the value of the **SessionVariable** parameter of an `Invoke-WebRequest` command.</span></span> <span data-ttu-id="4d898-268">`Invoke-WebRequest` Hiermee maakt u de sessie en slaat u deze op in de variabele.</span><span class="sxs-lookup"><span data-stu-id="4d898-268">`Invoke-WebRequest` creates the session and saves it in the variable.</span></span> <span data-ttu-id="4d898-269">Gebruik in volgende opdrachten de variabele als de waarde van de para meter **websession** .</span><span class="sxs-lookup"><span data-stu-id="4d898-269">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="4d898-270">U kunt de para meters **SessionVariable** en **websession** niet gebruiken in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="4d898-270">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="4d898-271">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4d898-271">CommonParameters</span></span>

<span data-ttu-id="4d898-272">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="4d898-272">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="4d898-273">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4d898-273">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4d898-274">INVOER</span><span class="sxs-lookup"><span data-stu-id="4d898-274">INPUTS</span></span>

### <span data-ttu-id="4d898-275">System. object</span><span class="sxs-lookup"><span data-stu-id="4d898-275">System.Object</span></span>

<span data-ttu-id="4d898-276">U kunt de hoofd tekst van een webaanvraag door sluizen naar `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="4d898-276">You can pipe the body of a web request to `Invoke-WebRequest`.</span></span>

## <span data-ttu-id="4d898-277">UITVOER</span><span class="sxs-lookup"><span data-stu-id="4d898-277">OUTPUTS</span></span>

### <span data-ttu-id="4d898-278">Microsoft.PowerShell.Commands.HtmlWebResponseObject</span><span class="sxs-lookup"><span data-stu-id="4d898-278">Microsoft.PowerShell.Commands.HtmlWebResponseObject</span></span>

## <span data-ttu-id="4d898-279">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="4d898-279">NOTES</span></span>

## <span data-ttu-id="4d898-280">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="4d898-280">RELATED LINKS</span></span>

[<span data-ttu-id="4d898-281">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="4d898-281">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="4d898-282">ConvertFrom-JSON</span><span class="sxs-lookup"><span data-stu-id="4d898-282">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="4d898-283">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="4d898-283">ConvertTo-Json</span></span>](ConvertTo-Json.md)
