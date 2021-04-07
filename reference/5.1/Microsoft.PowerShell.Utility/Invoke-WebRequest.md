---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/05/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: 4aa3b889ed00c6b0442a1191f055e1228f252631
ms.sourcegitcommit: d95a7255f6775b2973aa9473611185a5583881ff
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106555522"
---
# Invoke-WebRequest

## Samen vatting
Hiermee wordt inhoud opgehaald van een webpagina op internet.

## Syntax

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>] [-SessionVariable <String>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-CertificateThumbprint <String>]
 [-Certificate <X509Certificate>] [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>]
 [-Headers <IDictionary>] [-MaximumRedirection <Int32>] [-Method <WebRequestMethod>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>] [-ContentType <String>]
 [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>] [-PassThru] [<CommonParameters>]
```

## Beschrijving

De `Invoke-WebRequest` cmdlet verzendt http-, HTTPS-, FTP-en file-aanvragen naar een webpagina of webservice.
Hiermee wordt het antwoord geparseerd en worden verzamelingen van formulieren, koppelingen, afbeeldingen en andere belang rijke HTML-elementen geretourneerd.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

> [!NOTE]
> Standaard kan script code op de webpagina worden uitgevoerd wanneer de pagina wordt geparseerd om de eigenschap in te vullen `ParsedHtml` . Gebruik de `-UseBasicParsing` Schakel optie om dit te onderdrukken.

## Voorbeelden

### Voor beeld 1: een webaanvraag verzenden

Met deze opdracht wordt de `Invoke-WebRequest` cmdlet gebruikt voor het verzenden van een webaanvraag naar de Bing.com-site.

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

Met de eerste opdracht wordt de aanvraag uitgegeven en wordt het antwoord in de `$R` variabele opgeslagen.

Met de tweede opdracht wordt gefilterd op de objecten in **de eigenschap voor de gegevens, waarbij** de eigenschap **name** als "* waarde" is en de **tagName** "input" is. De gefilterde resultaten worden gepiped om `Select-Object` de **naam** en **waarde** -eigenschappen te selecteren.

### Voor beeld 2: een stateful webservice gebruiken

In dit voor beeld ziet u hoe u de `Invoke-WebRequest` cmdlet gebruikt met een stateful webservice, zoals Facebook.

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

De eerste opdracht gebruikt de `Invoke-WebRequest` cmdlet om een aanmeldings aanvraag te verzenden. Met de opdracht wordt de waarde ' FB ' opgegeven voor de waarde van de para meter **SessionVariable** en wordt het resultaat opgeslagen in de `$R` variabele. Wanneer de opdracht is voltooid, `$R` bevat de variabele een **HtmlWebResponseObject** en `$FB` bevat de variabele een **WebRequestSession** -object.

Nadat de `Invoke-WebRequest` cmdlet is aangemeld bij Facebook, geeft de eigenschap **StatusDescription** van het Web Response-object in de `$R` variabele aan dat de gebruiker is aangemeld.

### Voor beeld 3: koppelingen van een webpagina ophalen

Met deze opdracht worden de koppelingen op een webpagina opgehaald.

```powershell
(Invoke-WebRequest -Uri "https://devblogs.microsoft.com/powershell/").Links.Href
```

`Invoke-WebRequest`Met de cmdlet wordt de inhoud van de webpagina opgehaald. De eigenschap **links** van het geretourneerde **HtmlWebResponseObject** wordt gebruikt om de eigenschap **href** van elke koppeling weer te geven.

### Voor beeld 4: berichten over niet-geslaagde artikelen van Invoke-WebRequest

Wanneer er `Invoke-WebRequest` een niet-geslaagd http-bericht wordt aangetroffen (404, 500, etc.), wordt er geen uitvoer geretourneerd en wordt er een afsluit fout gegenereerd. Als u de fout wilt opvangen en de **status** code wilt weer geven, kunt u de uitvoering in een `try/catch` blok insluiten. In het volgende voor beeld ziet u hoe u dit kunt doen.

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

De afsluit fout wordt geblokkeerd door het `catch` blok, waardoor de **status** code wordt opgehaald uit het **uitzonderings** object.

## Parameters

### -Hoofd tekst

Hiermee geeft u de hoofd tekst van de aanvraag.
De hoofd tekst is de inhoud van de aanvraag die de headers volgt.
U kunt ook de waarde van een hoofd tekst sluist naar `Invoke-WebRequest` .

De para meter **Body** kan worden gebruikt om een lijst met query parameters op te geven of de inhoud van het antwoord op te geven.

Wanneer de invoer een GET-aanvraag is en de hoofd tekst een **IDictionary** is (meestal een hash-tabel), wordt de hoofd tekst als query parameters toegevoegd aan de URI. Voor andere GET-aanvragen wordt de hoofd tekst ingesteld als de waarde van de hoofd tekst van de aanvraag in de standaard `name=value` indeling.

Wanneer de hoofd tekst een formulier is of de uitvoer van een `Invoke-WebRequest` aanroep, stelt Power shell de aanvraag inhoud in op de formulier velden.
Bijvoorbeeld:

`$r = Invoke-WebRequest https://website.com/login.aspx`
`$r.Forms\[0\].Name = "MyName"`
`$r.Forms\[0\].Password = "MyPassword"`
`Invoke-RestMethod https://website.com/service.aspx -Body $r`

- of

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

### -Certificaat

Hiermee geeft u het client certificaat op dat wordt gebruikt voor een beveiligde webaanvraag. Voer een variabele in die een certificaat of een opdracht of expressie bevat waarmee het certificaat wordt opgehaald.

Als u een certificaat wilt zoeken, gebruikt `Get-PfxCertificate` of gebruikt u de `Get-ChildItem` cmdlet in het **certificaat** `Cert:` station. Als het certificaat ongeldig is of niet voldoende autoriteit heeft, mislukt de opdracht.

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

### -CertificateThumbprint

Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat gemachtigd is om de aanvraag te verzenden. Voer de vinger afdruk van het certificaat in. Certificaten worden gebruikt in authenticatie op basis van client certificaten. Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.

Gebruik de `Get-Item` `Get-ChildItem` opdracht of in het Power Shell-station om een certificaat vingerafdruk te verkrijgen `Cert:` .

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

### -Content type

Hiermee geeft u het type inhoud van de webaanvraag.

Als deze para meter wordt wegge laten en de aanvraag methode POST is, `Invoke-WebRequest` wordt het inhouds type ingesteld op Application/x-www-form-urlencoded. Anders is het inhouds type niet opgegeven in de aanroep.

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

### -Credential

Hiermee geeft u een gebruikers account op dat gemachtigd is om de aanvraag te verzenden. Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**, of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .

Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.

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

### -DisableKeepAlive

Geeft aan dat de cmdlet de **keepalive** -waarde in de http-header instelt op **False**. Standaard is **keepalive** ingesteld op **True**. Met **keepalive** wordt een permanente verbinding met de server tot stand gebracht om volgende aanvragen te vergemakkelijken.

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

### -Headers

Hiermee geeft u de kopteksten van de webaanvraag. Voer een hash-tabel of-woorden lijst in.

Gebruik de **agent** -para meter om de **agent** headers in te stellen. U kunt deze para meter niet gebruiken om de headers van **User agent** of cookie op te geven.

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

### -Inbestand

Hiermee wordt de inhoud van de webaanvraag opgehaald uit een bestand.

Voer een pad en een bestands naam in. Als u het pad weglaat, de standaard instelling is de huidige locatie.

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

### -MaximumRedirection

Hiermee geeft u op hoe vaak Power shell een verbinding met een alternatieve URI (Uniform Resource Identifier) omleidt voordat de verbinding is mislukt. De standaard waarde is 5. Een waarde van 0 (nul) voor komt dat alle omleidingen.

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

### -Methode

Hiermee geeft u de methode op die voor de webaanvraag wordt gebruikt. De aanvaardbare waarden voor deze parameter zijn:

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

### -Outfile

Hiermee geeft u het uitvoer bestand op waarvoor deze cmdlet de antwoord tekst opslaat. Voer een pad en een bestands naam in.
Als u het pad weglaat, de standaard instelling is de huidige locatie.

`Invoke-WebRequest`De resultaten worden standaard naar de pijp lijn geretourneerd. Als u de resultaten naar een bestand en naar de pijp lijn wilt verzenden, gebruikt u de para meter **PassThru** .

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

### -PassThru

Geeft aan dat de cmdlet de resultaten retourneert, naast het schrijven naar een bestand. Deze para meter is alleen geldig wanneer de **outfile** -para meter ook in de opdracht wordt gebruikt.

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

### -Proxy

Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.
Voer de URI van een netwerk proxy server in.

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

### -ProxyCredential

Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** . Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals `User01` of `Domain01\User01` , of voer een **PSCredential** -object in, zoals het certificaat dat is gegenereerd door de `Get-Credential` cmdlet.

Deze para meter is alleen geldig wanneer de **proxy** parameter ook in de opdracht wordt gebruikt. U kunt de para meters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.

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

### -ProxyUseDefaultCredentials

Geeft aan dat de cmdlet de referenties van de huidige gebruiker gebruikt om toegang te krijgen tot de proxy server die is opgegeven door de para meter **proxy** .

Deze para meter is alleen geldig wanneer de **proxy** parameter ook in de opdracht wordt gebruikt. U kunt de para meters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.

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

### -SessionVariable

Hiermee geeft u een variabele op waarvoor deze cmdlet een sessie voor een webaanvraag maakt en opslaat in de waarde.
Geef een naam op voor de variabele zonder het dollar teken ( `$` )-symbool.

Wanneer u een sessie variabele opgeeft, `Invoke-WebRequest` maakt een webaanvraag sessie object en wijst deze toe aan een variabele met de opgegeven naam in uw Power shell-sessie. U kunt de variabele in uw sessie gebruiken zodra de opdracht is voltooid.

In tegens telling tot een externe sessie is de sessie voor webaanvragen geen permanente verbinding. Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximum omleidings waarde en de teken reeks van de gebruikers agent. U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.

Als u de webaanvraag sessie in volgende webaanvragen wilt gebruiken, geeft u de sessie variabele op in de waarde van de para meter **websessie** . Power shell gebruikt de gegevens in het sessie object voor webaanvragen bij het tot stand brengen van de nieuwe verbinding. Als u een waarde in de sessie voor webaanvragen wilt overschrijven, gebruikt u een cmdlet-para meter, zoals **User agent** of **Credential**. Parameter waarden hebben prioriteit boven waarden in de webaanvraag sessie.

U kunt de para meters **SessionVariable** en **websession** niet gebruiken in dezelfde opdracht.

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

### -TimeoutSec

Hiermee geeft u op hoe lang de aanvraag in behandeling kan zijn voordat er een time-out optreedt. Voer een waarde in seconden in. De standaard waarde, 0, geeft een onbeperkte time-outwaarde.

Het kan tot vijf tien seconden duren voordat een Domain Name System query (DNS) wordt uitgevoerd of een time-out kan worden geretourneerd. Als uw aanvraag een hostnaam bevat waarvoor omzetting vereist is en u **TimeoutSec** instelt op een waarde die groter is dan nul, maar minder dan 15 seconden, kan het vijf tien seconden of langer duren **voordat een** webuitzondering wordt gegenereerd en er een time-out optreedt voor uw aanvraag.

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

### -TransferEncoding

Hiermee geeft u een waarde op voor de header van de HTTP-reactie voor overdracht/versleuteling. De aanvaardbare waarden voor deze parameter zijn:

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

### -URI

Hiermee geeft u de URI (Uniform Resource Identifier) op van de Internet bron waarnaar de webaanvraag wordt verzonden. Voer een URI in. Deze para meter ondersteunt HTTP-, HTTPS-, FTP-en FILE-waarden.

Deze parameter is vereist.

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

### -UseBasicParsing

Geeft aan dat de cmdlet gebruikmaakt van het antwoord object voor HTML-inhoud zonder dat het parseren van Document Object Model (DOM) wordt geparseerd. Deze para meter is vereist als Internet Explorer niet is geïnstalleerd op de computers, zoals op een Server Core-installatie van een Windows Server-besturings systeem.

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

### -UseDefaultCredentials

Geeft aan dat de cmdlet de referenties van de huidige gebruiker gebruikt om de webaanvraag te verzenden.

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

### -User agent

Hiermee geeft u een teken reeks voor de gebruikers agent op voor de webaanvraag. De standaard gebruikers agent is vergelijkbaar `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` met kleine variaties voor elk besturings systeem en platform.

Als u een website wilt testen met de standaard teken reeks van de gebruikers agent die wordt gebruikt door de meeste Internet browsers, gebruikt u de eigenschappen van de [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) -klasse, zoals Chrome, Firefox, InternetExplorer, Opera en Safari. De volgende opdracht maakt bijvoorbeeld gebruik van de teken reeks van de gebruikers agent voor Internet Explorer

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

### -Websessie

Hiermee geeft u een sessie voor webaanvragen. Voer de naam van de variabele in, met inbegrip van het dollar teken ( `$` ).

Als u een waarde in de sessie voor webaanvragen wilt overschrijven, gebruikt u een cmdlet-para meter, zoals **User agent** of **Credential**. Parameter waarden hebben prioriteit boven waarden in de webaanvraag sessie.

In tegens telling tot een externe sessie is de sessie voor webaanvragen geen permanente verbinding. Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximum omleidings waarde en de teken reeks van de gebruikers agent. U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.

Als u een webaanvraag sessie wilt maken, voert u een naam in voor de variabele (zonder een dollar teken) in de waarde van de para meter **SessionVariable** van een `Invoke-WebRequest` opdracht. `Invoke-WebRequest` Hiermee maakt u de sessie en slaat u deze op in de variabele. Gebruik in volgende opdrachten de variabele als de waarde van de para meter **websession** .

U kunt de para meters **SessionVariable** en **websession** niet gebruiken in dezelfde opdracht.

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` . Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## Invoerwaarden

### System. object

U kunt de hoofd tekst van een webaanvraag door sluizen naar `Invoke-WebRequest` .

## Uitvoerwaarden

### Microsoft.PowerShell.Commands.HtmlWebResponseObject

## Notities

## Verwante koppelingen

[Invoke-RestMethod](Invoke-RestMethod.md)

[ConvertFrom-JSON](ConvertFrom-Json.md)

[ConvertTo-Json](ConvertTo-Json.md)
