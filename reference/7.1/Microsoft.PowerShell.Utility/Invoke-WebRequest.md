---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/05/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: 4d95eb45497c8c3592825c4d4606580de4bccd84
ms.sourcegitcommit: 241071803915ab7d544576b5652ac23349a86369
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/07/2021
ms.locfileid: "107027257"
---
# Invoke-WebRequest

## Samen vatting
Hiermee wordt inhoud opgehaald van een webpagina op internet.

## Syntax

### StandardMethod (standaard)

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

### StandardMethodNoProxy

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

### CustomMethod

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

### CustomMethodNoProxy

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

## Description

De `Invoke-WebRequest` cmdlet verzendt HTTP-en HTTPS-aanvragen naar een webpagina of webservice. Hiermee wordt het antwoord geparseerd en worden verzamelingen van koppelingen, afbeeldingen en andere belang rijke HTML-elementen geretourneerd.

Deze cmdlet is geïntroduceerd in Power Shell 3,0.

Vanaf Power shell 7,0 `Invoke-WebRequest` ondersteunt proxy configuratie die is gedefinieerd door omgevings variabelen. Zie de sectie [opmerkingen](#notes) van dit artikel.

## Voorbeelden

### Voor beeld 1: een webaanvraag verzenden

In dit voor beeld wordt de `Invoke-WebRequest` cmdlet gebruikt voor het verzenden van een webaanvraag naar de Bing.com-site.

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

Met de eerste opdracht wordt de aanvraag uitgegeven en wordt het antwoord in de `$Response` variabele opgeslagen.

Met de tweede opdracht wordt een wille keurige **InputField** opgehaald waarbij de eigenschap **name** like is `"* Value"` . De gefilterde resultaten worden gepiped om `Select-Object` de **naam** en **waarde** -eigenschappen te selecteren.

### Voor beeld 2: een stateful webservice gebruiken

In dit voor beeld ziet u hoe u de `Invoke-WebRequest` cmdlet gebruikt met een stateful webservice.

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

De eerste aanroep om `Invoke-WebRequest` een aanmeldings aanvraag te verzenden. Met de opdracht wordt de waarde ' session ' opgegeven voor de waarde van de para meter **-SessionVariable** en wordt het resultaat opgeslagen in de `$LoginResponse` variabele. Wanneer de opdracht is voltooid, `$LoginResponse` bevat de variabele een `BasicHtmlWebResponseObject` en de `$Session` variabele bevat een- `WebRequestSession` object. Hiermee wordt de gebruiker geregistreerd bij de-site.

De aanroep naar `$Session` zelf toont het `WebRequestSession` object in de variabele.

De tweede aanroep om `Invoke-WebRequest` het profiel van de gebruiker op te halen waarvoor de gebruiker moet zijn aangemeld bij de site. De sessie gegevens die zijn opgeslagen in de `$Session` variabele worden gebruikt om sessie cookies te bieden aan de site die tijdens de aanmelding is gemaakt. Het resultaat wordt opgeslagen in de `$ProfileResponse` variabele.

Op de aanroep `$ProfileResponse` zelf wordt de `BasicHtmlWebResponseObject` in de variabele weer gegeven.

### Voor beeld 3: koppelingen van een webpagina ophalen

In dit voor beeld worden de koppelingen op een webpagina opgehaald. Hiermee wordt de- `Invoke-WebRequest` cmdlet gebruikt om de inhoud van de webpagina op te halen. Vervolgens wordt de eigenschap **links** van de `BasicHtmlWebResponseObject` `Invoke-WebRequest` geretourneerde en de eigenschap **href** van elke koppeling gebruikt.

```powershell
(Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs").Links.Href
```

### Voor beeld 4: schrijft de antwoord inhoud naar een bestand met behulp van de code ring die op de aangevraagde pagina is gedefinieerd.

In dit voor beeld wordt de `Invoke-WebRequest` cmdlet gebruikt om de webpagina-inhoud van een Power shell-documentatie pagina op te halen.

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

De eerste opdracht haalt de pagina op en slaat het antwoord object op in de `$Response` variabele.

Met de tweede opdracht maakt `StreamWriter` u een om de antwoord inhoud naar een bestand te schrijven. De eigenschap **Encoding** van het Response-object wordt gebruikt om de code ring voor het bestand in te stellen.

Met de laatste opdrachten wordt de eigenschap **Content** geschreven naar het bestand en vervolgens verwijderd `StreamWriter` .

Houd er rekening mee dat de eigenschap **Encoding** null is als de webaanvraag geen tekst inhoud retourneert.

### Voor beeld 5: een meerdelige/formulier-gegevens bestand verzenden

In dit voor beeld wordt de cmdlet gebruikt om `Invoke-WebRequest` een bestand te uploaden als een `multipart/form-data` verzen ding. Het bestand `c:\document.txt` wordt verzonden als het formulier veld `document` met de `Content-Type` van `text/plain` .

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

### Voor beeld 6: vereenvoudigd meerdelige/Form-Data-verzen ding

Voor sommige Api's zijn `multipart/form-data` inzendingen vereist om bestanden en gemengde inhoud te uploaden. In dit voor beeld ziet u hoe u een gebruikers profiel bijwerkt.

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

Voor het profiel formulier zijn de volgende velden vereist: `firstName` ,, `lastName` ,, `email` `avatar` `birthday` en `hobbies` . De API verwacht een installatie kopie voor het gebruikers profiel pic dat in het veld moet worden opgegeven `avatar` . De API accepteert ook meerdere `hobbies` vermeldingen die in hetzelfde formulier moeten worden ingediend.

Wanneer u de `$Form` hashtabel maakt, worden de sleutel namen gebruikt als formulier veld namen. Standaard worden de waarden van de hashtabel geconverteerd naar teken reeksen. Als er een **System. io. file info** -waarde aanwezig is, wordt de bestands inhoud verzonden. Als er een verzameling zoals matrices of lijsten aanwezig is, wordt het formulier veld meerdere keren ingediend.

Door `Get-Item` op de `avatar` sleutel te gebruiken, `FileInfo` wordt het object ingesteld als de waarde. Het resultaat is dat de afbeeldings gegevens voor `jdoe.png` worden verzonden.

Door een lijst aan de sleutel toe te voegen `hobbies` , `hobbies` wordt het veld voor elk lijst item één keer weer gegeven in de-verzen ding.

### Voor beeld 7: berichten over niet-geslaagde artikelen van Invoke-WebRequest

Wanneer er `Invoke-WebRequest` een niet-geslaagd http-bericht wordt aangetroffen (404, 500, etc.), wordt er geen uitvoer geretourneerd en wordt er een afsluit fout gegenereerd. Als u de fout wilt opvangen en de **status** code wilt weer geven, kunt u de uitvoering in een `try/catch` blok insluiten.

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

### -AllowUnencryptedAuthentication

Hiermee staat u het verzenden van referenties en geheimen over niet-versleutelde verbindingen toe. Standaard wordt **referentie** verstrekt of een **authenticatie** optie met een **URI** die niet begint met `https://` resulteert in een fout en de aanvraag wordt afgebroken om onbedoeld geheimen te communiceren in tekst zonder opmaak over niet-versleutelde verbindingen. U kunt dit gedrag voor eigen risico negeren door de para meter **AllowUnencryptedAuthentication** op te geven.

> [!WARNING]
> Het gebruik van deze para meter is niet beveiligd en wordt niet aanbevolen. Het is alleen beschikbaar voor compatibiliteit met oudere systemen die geen versleutelde verbindingen kunnen bieden. Gebruiken op eigen risico.

Deze functie is toegevoegd aan Power shell 6.0.0.

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

### -Verificatie

Hiermee geeft u het expliciete verificatie type op dat moet worden gebruikt voor de aanvraag. De standaardwaarde is **None**.
**Authenticatie** kan niet worden gebruikt met **UseDefaultCredentials**.

Beschik bare verificatie opties:

- `None`: Dit is de standaard optie wanneer **authenticatie** niet is opgegeven. Er wordt geen expliciete authenticatie gebruikt.
- `Basic`: Vereist **referentie**. De referenties worden verzonden in een RFC 7617-basis verificatie header in de indeling van `base64(user:password)` .
- `Bearer`: **Token** vereist. Verzendt een RFC 6750- `Authorization: Bearer` header met het opgegeven token. Dit is een alias voor **OAuth**
- `OAuth`: **Token** vereist. Verzendt een RFC 6750- `Authorization: Bearer` header met het opgegeven token. Dit is een alias voor **Bearer**

Het opgeven van een **verificatie** heeft `Authorization` voor rang op alle headers die worden geleverd aan **headers** of die zijn opgenomen in **websessie**.

Deze functie is toegevoegd aan Power shell 6.0.0.

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

### -Hoofd tekst

Hiermee geeft u de hoofd tekst van de aanvraag. De hoofd tekst is de inhoud van de aanvraag die de headers volgt.
U kunt ook de waarde van een hoofd tekst sluist naar `Invoke-WebRequest` .

De para meter **Body** kan worden gebruikt om een lijst met query parameters op te geven of de inhoud van het antwoord op te geven.

Wanneer de invoer een GET-aanvraag is en de hoofd tekst een `IDictionary` (meestal een hash-tabel) is, wordt de hoofd tekst als query parameters aan de URI toegevoegd. Voor andere aanvraag typen (zoals POST) wordt de hoofd tekst ingesteld als de waarde van de hoofd tekst van de aanvraag in de standaard `name=value` indeling.

De para meter **Body** kan ook een `System.Net.Http.MultipartFormDataContent` object accepteren. Dit vergemakkelijkt `multipart/form-data` aanvragen. Wanneer er een **MultipartFormDataContent** -object wordt opgegeven voor de **hoofd tekst**, worden alle inhoud die aan de para meter **Content type**, **headers** of **websession** is gekoppeld, overschreven door de inhouds headers van het **MultipartFormDataContent** -object. Deze functie is toegevoegd aan Power shell 6.0.0.

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

Als u een certificaat wilt zoeken, gebruikt `Get-PfxCertificate` of gebruikt u de `Get-ChildItem` cmdlet in het certificaat `Cert:` station. Als het certificaat ongeldig is of niet voldoende autoriteit heeft, mislukt de opdracht.

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

Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat gemachtigd is om de aanvraag te verzenden. Voer de vinger afdruk van het certificaat in.

Certificaten worden gebruikt in authenticatie op basis van client certificaten. Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.

Gebruik de `Get-Item` `Get-ChildItem` opdracht of in het Power Shell-station om een certificaat vingerafdruk te verkrijgen `Cert:` .

> [!NOTE]
> Deze functie wordt momenteel alleen ondersteund op Windows-besturings systemen.

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

Als deze para meter wordt wegge laten en de aanvraag methode is `Invoke-WebRequest` ingesteld op post, stelt het inhouds type in op `application/x-www-form-urlencoded` . Anders is het inhouds type niet opgegeven in de aanroep.

**Content type** wordt overschreven wanneer een **MultipartFormDataContent** -object wordt opgegeven voor de **hoofd tekst**.

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

**Referentie** kan alleen worden gebruikt of in combi natie met bepaalde opties voor **verificatie** parameters. Als u alleen gebruikt, worden er alleen referenties voor de externe server verstrekt als de externe server een aanvraag voor verificatie controle verzendt. Wanneer u gebruikt met **verificatie** opties, worden de referenties expliciet verzonden.

Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.

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

### -CustomMethod

Hiermee geeft u een aangepaste methode op die wordt gebruikt voor de webaanvraag. Dit kan worden gebruikt als de aanvraag methode die door het eind punt wordt vereist, geen beschik bare optie is voor de **methode**. **Methode** en **CustomMethod** kunnen niet tegelijk worden gebruikt.

In dit voor beeld wordt een `TEST` HTTP-aanvraag naar de API gemaakt:

`Invoke-WebRequest -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

Deze functie is toegevoegd aan Power shell 6.0.0.

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

### -Vorm

Converteert een woorden lijst naar een `multipart/form-data` inzending. Het **formulier** kan niet worden gebruikt met een **hoofd tekst**.
Als **Content type** wordt gebruikt, wordt dit genegeerd.

De sleutels van de woorden lijst worden gebruikt als de namen van het formulier veld. Standaard worden formulier waarden geconverteerd naar teken reeks waarden.

Als de waarde een **System. io. file info** -object is, wordt de inhoud van het binaire bestand verzonden. De naam van het bestand wordt verzonden als de eigenschap **filename** . Het MIME-type is ingesteld als `application/octet-stream` . `Get-Item` kan worden gebruikt om het object **System. io. file info** te vereenvoudigen.

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

Als de waarde een verzamelings type is, zoals matrices of lijsten, worden het veld voor meerdere keren verzonden.
De waarden van de lijst worden standaard als teken reeksen beschouwd. Als de waarde een **System. io. file info** -object is, wordt de inhoud van het binaire bestand verzonden. Geneste verzamelingen worden niet ondersteund.

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

In het bovenstaande voor beeld `tags` wordt het veld drie keer in het formulier opgegeven, eenmaal voor elk van `Vacation` , `Italy` en `2017` . Het `pictures` veld wordt ook eenmaal ingediend voor elk bestand in de `2017-Italy` map. De binaire inhoud van de bestanden in die map wordt verzonden als de waarden.

Deze functie is toegevoegd aan Power shell 6.1.0.

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

### -Headers

Hiermee geeft u de kopteksten van de webaanvraag. Voer een hash-tabel of-woorden lijst in.

Gebruik de **agent** -para meter om de agent headers in te stellen. U kunt deze para meter niet gebruiken om **gebruikers agent-** of cookie headers op te geven.

Inhouds gerelateerde kopteksten, zoals `Content-Type` wordt overschreven wanneer een **MultipartFormDataContent** -object wordt opgegeven voor de **hoofd tekst**.

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

Hiermee wordt de inhoud van de webaanvraag opgehaald uit een bestand. Voer een pad en een bestands naam in. Als u het pad weglaat, de standaard instelling is de huidige locatie.

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
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumRetryCount

Hiermee geeft u op hoe vaak Power shell een verbinding probeert te verbreken wanneer een fout code tussen 400 en 599, inclusief of 304 wordt ontvangen. Zie ook de para meter **RetryIntervalSec** voor het opgeven van het aantal nieuwe pogingen.

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

De para meter **CustomMethod** kan worden gebruikt voor aanvraag methoden die hierboven niet worden vermeld.

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

### -De proxy

Geeft aan dat de cmdlet geen proxy moet gebruiken om de bestemming te bereiken. Wanneer u de in de omgeving geconfigureerde proxy wilt overs Laan, gebruikt u deze schakel optie. Deze functie is toegevoegd aan Power shell 6.0.0.

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

### -Outfile

Hiermee geeft u het uitvoer bestand op waarvoor deze cmdlet de antwoord tekst opslaat. Voer een pad en een bestands naam in.
Als u het pad weglaat, de standaard instelling is de huidige locatie. De naam wordt beschouwd als een letterlijk pad.
Namen die vier Kante haakjes () bevatten, `[]` moeten tussen enkele aanhalings tekens () worden geplaatst `'` .

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

### -PreserveAuthorizationOnRedirect

Hiermee wordt aangegeven dat de cmdlet de header moet behouden `Authorization` , indien aanwezig, over de omleidingen.

De-cmdlet verwijdert standaard de `Authorization` header voordat deze wordt omgeleid. Als u deze para meter opgeeft, wordt deze logica uitgeschakeld voor gevallen waarin de header moet worden verzonden naar de omleidings locatie.

Deze functie is toegevoegd aan Power shell 6.0.0.

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
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** . Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**, **User@Domain.Com** of voer een `PSCredential` object in, bijvoorbeeld het type dat door de cmdlet wordt gegenereerd `Get-Credential` .

Deze para meter is alleen geldig wanneer de **proxy** parameter ook in de opdracht wordt gebruikt. U kunt de para meters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.

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

### -ProxyUseDefaultCredentials

Geeft aan dat de cmdlet de referenties van de huidige gebruiker gebruikt om toegang te krijgen tot de proxy server die is opgegeven door de para meter **proxy** .

Deze para meter is alleen geldig wanneer de **proxy** parameter ook in de opdracht wordt gebruikt. U kunt de para meters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.

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

### -Hervatten

Hiermee wordt een beste poging gedaan om het downloaden van een gedeeltelijk bestand te hervatten. Voor **hervatten** is **outfile** vereist.

**Resume** werkt alleen op de grootte van het lokale bestand en het externe bestand en voert geen andere validatie uit dat het lokale bestand en het externe bestand hetzelfde zijn.

Als de lokale bestands grootte kleiner is dan de grootte van het externe bestand, probeert de cmdlet het downloaden van het bestand te hervatten en de resterende bytes toe te voegen aan het einde van het bestand.

Als de grootte van het lokale bestand hetzelfde is als de grootte van het externe bestand, wordt er geen actie ondernomen en wordt ervan uitgegaan dat de down load al is voltooid.

Als de grootte van het lokale bestand groter is dan de grootte van het externe bestand, wordt het lokale bestand overschreven en wordt het hele externe bestand opnieuw gedownload. Dit gedrag is hetzelfde als het gebruik van een **bestand** zonder de bewerking te **hervatten**.

Als de externe server downloaden niet kan hervatten, wordt het lokale bestand overschreven en wordt het hele externe bestand opnieuw gedownload. Dit gedrag is hetzelfde als het gebruik van een **bestand** zonder de bewerking te **hervatten**.

Als het lokale bestand niet bestaat, wordt het lokale bestand gemaakt en wordt het hele externe bestand gedownload. Dit gedrag is hetzelfde als het gebruik van een **bestand** zonder de bewerking te **hervatten**.

Deze functie is toegevoegd aan Power shell 6.1.0.

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

### -RetryIntervalSec

Hiermee geeft u het interval tussen nieuwe pogingen voor de verbinding op wanneer er een fout code tussen 400 en 599, inclusief of 304 wordt ontvangen. Zie ook de para meter **MaximumRetryCount** voor het opgeven van het aantal nieuwe pogingen.

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

### -SkipCertificateCheck

Hiermee worden controles van certificaat validatie overs Laan. Dit omvat alle validaties zoals verval datum, intrekking, vertrouwde basis instantie, enzovoort.

> [!WARNING]
> Het gebruik van deze para meter is niet beveiligd en wordt niet aanbevolen. Deze schakel optie is alleen bedoeld om te worden gebruikt voor bekende hosts met behulp van een zelfondertekend certificaat voor test doeleinden. Gebruiken op eigen risico.

Deze functie is toegevoegd aan Power shell 6.0.0.

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

### -SkipHeaderValidation

Hiermee wordt aangegeven dat de cmdlet headers zonder validatie moet toevoegen aan de aanvraag.

Deze schakel optie moet worden gebruikt voor sites waarvoor header waarden zijn vereist die niet voldoen aan de standaarden.
Als u deze switch opgeeft, wordt de validatie uitgeschakeld zodat de waarde die wordt door gegeven, niet kan worden gecontroleerd. Als u deze opgeeft, worden alle headers zonder validatie toegevoegd.

Met deze switch wordt de validatie uitgeschakeld voor waarden die zijn door gegeven aan de para meters **Content type**, **headers** en **User agent** .

Deze functie is toegevoegd aan Power shell 6.0.0.

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

### -SkipHttpErrorCheck

Deze para meter zorgt ervoor dat de cmdlet HTTP-fout statussen negeert en de antwoorden blijft verwerken.
De fout reacties worden naar de pijp lijn geschreven alsof ze zijn geslaagd.

Deze para meter is geïntroduceerd in Power shell 7.

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

### -SslProtocol

Hiermee stelt u de SSL/TLS-protocollen die zijn toegestaan voor de webaanvraag. Standaard zijn alle SSL/TLS-protocollen die door het systeem worden ondersteund, toegestaan. Met **SslProtocol** wordt het beperken van specifieke protocollen voor nalevings doeleinden toegestaan.

Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag. U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter. De waarden kunnen worden door gegeven aan de **SslProtocol** -para meter als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden. Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking. Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien. U kunt mogelijk niet meerdere opties definiëren op alle platformen.

> [!NOTE]
> Op niet-Windows-platforms is het niet mogelijk om te leveren `Tls` of `Tls12` als optie. Ondersteuning voor `Tls13` is niet beschikbaar op alle besturings systemen en moet worden geverifieerd op basis van elk besturings systeem.

Deze functie is toegevoegd aan Power shell 6.0.0 en ondersteuning voor `Tls13` is toegevoegd in Power shell 7,1.

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

### -TimeoutSec

Hiermee geeft u op hoe lang de aanvraag in behandeling kan zijn voordat er een time-out optreedt. Voer een waarde in seconden in. De standaard waarde, 0, geeft een onbeperkte time-outwaarde.

Het kan tot vijf tien seconden duren voordat een Domain Name System query (DNS) wordt uitgevoerd of een time-out kan worden geretourneerd. Als uw aanvraag een hostnaam bevat waarvoor omzetting vereist is en u **TimeoutSec** instelt op een waarde die groter is dan nul, maar minder dan 15 seconden, kan het vijf tien seconden of langer duren voordat een webuitzondering wordt gegenereerd en er een time-out optreedt voor uw aanvraag.

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

### -Token

Het OAuth-of Bearer-token dat in de aanvraag moet worden meegenomen. Het **token** is vereist voor bepaalde **verificatie** opties. Deze kan niet onafhankelijk worden gebruikt.

**Token** neemt een token in beslag `SecureString` . Gebruik het volgende om het token hand matig op te geven:

`Invoke-WebRequest -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

Deze para meter is geïntroduceerd in Power shell 6,0.

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

### -TransferEncoding

Hiermee geeft u een waarde op voor de header van de HTTP-reactie voor overdracht/versleuteling. De aanvaardbare waarden voor deze parameter zijn:

- Gesegmenteerde
- Comprimeren
- Deflate
- GZip
- Identiteit

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

Hiermee geeft u de URI (Uniform Resource Identifier) op van de Internet bron waarnaar de webaanvraag wordt verzonden. Voer een URI in. Deze para meter biedt alleen ondersteuning voor HTTP of HTTPS.

Deze parameter is vereist. De parameter naam **URI** is optioneel.

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

Deze para meter is afgeschaft. Vanaf Power shell 6.0.0 gebruiken alle webaanvragen alleen basis parsering. Deze para meter is alleen opgenomen voor achterwaartse compatibiliteit en het gebruik ervan heeft geen invloed op de werking van de cmdlet.

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

Geeft aan dat de cmdlet de referenties van de huidige gebruiker gebruikt om de webaanvraag te verzenden. Deze kan niet worden gebruikt met **verificatie** of **referentie** en wordt mogelijk niet ondersteund op alle platforms.

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

Hiermee geeft u een teken reeks voor de gebruikers agent op voor de webaanvraag.

De standaard gebruikers agent is vergelijkbaar `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` met kleine variaties voor elk besturings systeem en platform.

Als u een website wilt testen met de standaard teken reeks van de gebruikers agent die wordt gebruikt door de meeste Internet browsers, gebruikt u de eigenschappen van de [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) -klasse, zoals Chrome, Firefox, InternetExplorer, Opera en Safari.

De volgende opdracht maakt bijvoorbeeld gebruik van de teken reeks van de gebruikers agent voor Internet Explorer: `Invoke-WebRequest -Uri https://website.com/ -UserAgent ([Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer)`

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

Als u een waarde in de sessie voor webaanvragen wilt overschrijven, gebruikt u een cmdlet-para meter, zoals **User agent** of **Credential**. Parameter waarden hebben prioriteit boven waarden in de webaanvraag sessie. Inhouds gerelateerde kopteksten, zoals `Content-Type` , worden ook genegeerd wanneer een **MultipartFormDataContent** -object wordt opgegeven voor de **hoofd tekst**.

In tegens telling tot een externe sessie is de sessie van de webaanvraag geen permanente verbinding. Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximum omleidings waarde en de teken reeks van de gebruikers agent. U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.

Als u een webonderdeelverzoek wilt maken, voert u de naam van een variabele zonder een dollar teken in de waarde van de para meter **SessionVariable** van een `Invoke-WebRequest` opdracht in. `Invoke-WebRequest` Hiermee maakt u de sessie en slaat u deze op in de variabele. Gebruik in volgende opdrachten de variabele als de waarde van de para meter **websession** .

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## Invoerwaarden

### System. object

U kunt de hoofd tekst van een webaanvraag door sluizen naar `Invoke-WebRequest` .

## Uitvoerwaarden

### Micro soft. Power shell. commands. BasicHtmlWebResponseObject

## Notities

Vanaf Power shell 6.0.0 `Invoke-WebRequest` ondersteunt alleen basis parsering.

Zie [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject)voor meer informatie.

Vanwege wijzigingen in .NET Core 3,1, Power shell 7,0 en hoger, gebruikt u de eigenschap [httpclient maakt. DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) om de proxy configuratie te bepalen.

De waarde van deze eigenschap wordt bepaald door uw platform:

- **Voor Windows**: Hiermee leest u de proxy configuratie van omgevings variabelen. Als deze variabelen niet worden gedefinieerd, wordt de eigenschap afgeleid van de proxy-instellingen van de gebruiker.
- **Voor macOS**: leest de proxy configuratie van omgevings variabelen. Als deze variabelen niet worden gedefinieerd, wordt de eigenschap afgeleid van de proxy-instellingen van het systeem.
- **Voor Linux**: Hiermee leest u de proxy configuratie van omgevings variabelen. Als deze variabelen niet zijn gedefinieerd, initialiseert de eigenschap een niet-geconfigureerd exemplaar dat alle adressen omzeilt.

De omgevings variabelen die worden gebruikt voor de `DefaultProxy` initialisatie op Windows-en UNIX-platforms zijn:

- `HTTP_PROXY`: de hostnaam of het IP-adres van de proxy server die wordt gebruikt voor HTTP-aanvragen.
- `HTTPS_PROXY`: de hostnaam of het IP-adres van de proxy server die wordt gebruikt voor HTTPS-aanvragen.
- `ALL_PROXY`: de hostnaam of het IP-adres van de proxy server die wordt gebruikt voor HTTP-en HTTPS-aanvragen `HTTP_PROXY` of `HTTPS_PROXY` die niet zijn gedefinieerd.
- `NO_PROXY`: een door komma's gescheiden lijst met hostnamen die moeten worden uitgesloten van de proxy.

## Verwante koppelingen

[Invoke-RestMethod](Invoke-RestMethod.md)

[ConvertFrom-JSON](ConvertFrom-Json.md)

[ConvertTo-Json](ConvertTo-Json.md)
