---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/05/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-RestMethod
ms.openlocfilehash: 4003912cf9845163467a10d21b603c85ec25b02b
ms.sourcegitcommit: d95a7255f6775b2973aa9473611185a5583881ff
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106555165"
---
# Invoke-RestMethod

## Samen vatting
Hiermee verzendt u een HTTP-of HTTPS-aanvraag naar een REST webservice.

## Syntax

### StandardMethod (standaard)

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

### StandardMethodNoProxy

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

### CustomMethodNoProxy

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

### CustomMethod

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

## Beschrijving

De `Invoke-RestMethod` cmdlet verzendt HTTP-en HTTPS-aanvragen voor het representatief verzenden van (rest) webservices voor het retour neren van Rich gestructureerde gegevens.

Power shell formatteert het antwoord op basis van het gegevens type. Voor een RSS-of ATOM-feed retourneert Power shell het item of de XML-knoop punten van de vermelding. Voor JavaScript Object Notation (JSON) of XML, wordt de inhoud door Power shell geconverteerd of gedeserialiseerd naar objecten.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

Vanaf Power shell 7,0 `Invoke-RestMethod` ondersteunt proxy configuratie die is gedefinieerd door omgevings variabelen. Zie de sectie [opmerkingen](#notes) van dit artikel.

## Voorbeelden

### Voor beeld 1: de Power shell-RSS-feed ophalen

In dit voor beeld wordt de `Invoke-RestMethod` cmdlet gebruikt om informatie op te halen uit de RSS-feed voor het Power shell-blog. De opdracht gebruikt de `Format-Table` cmdlet om de waarden van de eigenschappen **title** en **pubDate** van elke blog in een tabel weer te geven.

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

### Voor beeld 2: een POST-aanvraag uitvoeren

In dit voor beeld wordt een gebruiker uitgevoerd `Invoke-RestMethod` om een post-aanvraag uit te voeren op een intranet website in de organisatie van de gebruiker.

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

De referenties worden gevraagd en vervolgens opgeslagen in `$Cred` en de URL waartoe toegang wordt gegeven, wordt gedefinieerd in `$Url` .

De `$Body` variabele beschrijft de zoek criteria, geeft CSV op als uitvoer modus en geeft een periode op voor de geretourneerde gegevens die twee dagen geleden worden gestart en eindigt een dag geleden. De variabele body geeft waarden op voor para meters die van toepassing zijn op het specifieke REST API waarmee `Invoke-RestMethod` wordt gecommuniceerd.

De `Invoke-RestMethod` opdracht wordt uitgevoerd met alle variabelen op locatie, waarbij een pad en een bestands naam voor het resulterende CSV-uitvoer bestand worden opgegeven.

### Voor beeld 3: relatie koppelingen volgen

Sommige REST Api's ondersteunen paginering via relatie koppelingen per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6). In plaats van de header te parseren om de URL voor de volgende pagina op te halen, kunt u de cmdlet dit voor u laten doen. In dit voor beeld worden de eerste twee pagina's met problemen uit de Power shell GitHub-opslag plaats geretourneerd.

```powershell
$url = 'https://api.github.com/repos/powershell/powershell/issues'
Invoke-RestMethod $url -FollowRelLink -MaximumFollowRelLink 2
```

### Voor beeld 4: vereenvoudigd meerdelige/formulier-data verzen ding

Voor sommige Api's zijn `multipart/form-data` inzendingen vereist om bestanden en gemengde inhoud te uploaden. In dit voor beeld ziet u hoe u het profiel van een gebruiker bijwerkt.

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

Voor het profiel formulier zijn de volgende velden vereist: `firstName` ,, `lastName` ,, `email` `avatar` `birthday` en `hobbies` . De API verwacht een installatie kopie voor het gebruikers profiel pic dat in het veld moet worden opgegeven `avatar` . In de API worden ook meerdere `hobbies` vermeldingen geaccepteerd die in hetzelfde formulier moeten worden ingediend.

Wanneer u de `$Form` hashtabel maakt, worden de sleutel namen gebruikt als formulier veld namen. Standaard worden de waarden van de hashtabel geconverteerd naar teken reeksen. Als er een `System.IO.FileInfo` waarde aanwezig is, wordt de inhoud van het bestand verzonden. Als er een verzameling zoals matrices of lijsten aanwezig is, wordt het formulier veld meerdere keren verzonden.

Door `Get-Item` op de sleutel te gebruiken `avatar` , `FileInfo` wordt het object ingesteld als de waarde. Het resultaat is dat de afbeeldings gegevens voor worden `jdoe.png` verzonden.

Door een lijst aan de sleutel toe te voegen `hobbies` , `hobbies` wordt het veld voor elk lijst item één keer weer gegeven in de-verzen ding.

### Voor beeld 5: meerdere headers door geven

Api's vereisen vaak door gegeven headers voor verificatie of validatie. In dit voor beeld ziet u hoe u meerdere headers van een `hash-table` naar een rest API doorgeeft.

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

## Parameters

### -AllowUnencryptedAuthentication

Hiermee staat u het verzenden van referenties en geheimen over niet-versleutelde verbindingen toe. Standaard leidt het leveren van **referenties** of een **authenticatie** optie met een **URI** die niet begint met een `https://` fout en wordt de aanvraag afgebroken om onbedoeld geheimen te communiceren in tekst zonder opmaak over niet-versleutelde verbindingen. U kunt dit gedrag voor eigen risico negeren door de para meter **AllowUnencryptedAuthentication** op te geven.

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

- `None`: Dit is de standaard optie wanneer er geen **verificatie** is opgegeven. Er wordt geen expliciete authenticatie gebruikt.
- `Basic`: Vereist **referentie**. De referenties worden gebruikt voor het verzenden van een RFC 7617-basis verificatie `Authorization: Basic` header in de indeling van `base64(user:password)` .
- `Bearer`: **Token** vereist. Verzendt en RFC 6750- `Authorization: Bearer` header met het opgegeven token. Dit is een alias voor **OAuth**
- `OAuth`: **Token** vereist. Er wordt een RFC 6750- `Authorization: Bearer` header verzonden met het opgegeven token. Dit is een alias voor **Bearer**

Bij het leveren van **verificatie** worden alle `Authorization` headers die zijn opgegeven in **headers** of opgenomen in **websessie**, overschreven.

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
U kunt ook de waarde van een hoofd tekst sluist naar `Invoke-RestMethod` .

De para meter **Body** kan worden gebruikt om een lijst met query parameters op te geven of de inhoud van het antwoord op te geven.

Wanneer de invoer een GET-aanvraag is en de hoofd tekst een `IDictionary` (meestal een hash-tabel) is, wordt de hoofd tekst als query parameters aan de URI (Uniform Resource Identifier) toegevoegd. Voor andere aanvraag typen (zoals POST) wordt de hoofd tekst ingesteld als de waarde van de aanvraag tekst in de notatie standaard naam = waarde.

Wanneer de hoofd tekst een formulier is of de uitvoer van een andere `Invoke-WebRequest` aanroep is, stelt Power shell de aanvraag inhoud in op de formulier velden.

De para meter **Body** kan ook een **systeem .net. http. MultipartFormDataContent-** object accepteren. Hierdoor kunnen aanvragen worden vergemakkelijkt `multipart/form-data` . Wanneer een **MultipartFormDataContent** -object wordt opgegeven voor de **hoofd tekst**, worden alle aan de inhouds headers van het object gerelateerde kopteksten die zijn opgegeven voor de **Content type**-, **headers**-of **websessie** -para meters, overschreven `MultipartFormDataContent` . Deze functie is toegevoegd aan Power shell 6.0.0.

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

Als deze para meter wordt wegge laten en de aanvraag methode is `Invoke-RestMethod` ingesteld op post, stelt het inhouds type in op `application/x-www-form-urlencoded` . Anders is het inhouds type niet opgegeven in de aanroep.

**Content type** wordt overschreven wanneer een `MultipartFormDataContent` object wordt opgegeven voor de **hoofd tekst**.

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

Hiermee geeft u de aangepaste methode op die voor de webaanvraag wordt gebruikt. Dit kan worden gebruikt met de aanvraag methode die door het eind punt wordt vereist, is geen beschik bare optie voor de **methode**. **Methode** en **CustomMethod** kunnen niet tegelijk worden gebruikt.

Voorbeeld:

`Invoke-RestMethod -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

Hiermee maakt `TEST` u een HTTP-aanvraag voor de API.

Deze functie is toegevoegd aan Power shell 6.0.0.

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

### -DisableKeepAlive

Geeft aan dat de cmdlet de **keepalive** -waarde in de http-header instelt op false. Standaard is **keepalive** ingesteld op True. Met **keepalive** wordt een permanente verbinding met de server tot stand gebracht om volgende aanvragen te vergemakkelijken.

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

### -FollowRelLink

Hiermee wordt aangegeven dat de cmdlet relatie koppelingen moet volgen.

Sommige REST Api's ondersteunen paginering via relatie koppelingen per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6). In plaats van de header te parseren om de URL voor de volgende pagina op te halen, kunt u de cmdlet dit voor u laten doen. Als u wilt instellen hoe vaak de relatie koppelingen moet worden gevolgd, gebruikt u de para meter **MaximumFollowRelLink** .

Wanneer u deze switch gebruikt, retourneert de cmdlet een verzameling pagina's met resultaten. Elke pagina met resultaten kan meerdere resultaten items bevatten.

Deze functie is toegevoegd aan Power shell 6.0.0.

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

### -Vorm

Converteert een woorden lijst naar een `multipart/form-data` inzending. Het **formulier** kan niet worden gebruikt met een **hoofd tekst**.
Als **Content type** wordt genegeerd.

De sleutels van de woorden lijst worden gebruikt als de veld namen van het formulier. Standaard worden formulier waarden geconverteerd naar teken reeks waarden.

Als de waarde een **System. io. file info** -object is, wordt de inhoud van het binaire bestand verzonden.
De naam van het bestand wordt verzonden als `filename` . De MIME wordt ingesteld als `application/octet-stream` . `Get-Item` kan worden gebruikt om het object **System. io. file info** te vereenvoudigen.

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

Als de waarde een verzamelings type is, zoals een matrix of lijst, wordt het veld voor meerdere keren verzonden. De waarden van de lijst worden standaard beschouwd als teken reeksen. Als de waarde een **System. io. file info** -object is, wordt de inhoud van het binaire bestand verzonden. Geneste verzamelingen worden niet ondersteund.

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

In het bovenstaande voor beeld `tags` wordt het veld drie keer in het formulier opgegeven, eenmaal voor elk van `Vacation` , `Italy` en `2017` . Het `pictures` veld wordt ook één keer verzonden voor elk bestand in de `2017-Italy` map. De binaire inhoud van de bestanden in die map wordt verzonden als de waarden.

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

Gebruik de **agent** -para meter om de agent headers in te stellen. U kunt deze para meter niet gebruiken om headers op te geven `User-Agent` of te cookie.

Aan inhoud gerelateerde kopteksten, zoals `Content-Type` wordt overschreven wanneer een `MultipartFormDataContent` object wordt opgegeven voor de **hoofd tekst**.

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

### -MaximumFollowRelLink

Hiermee geeft u op hoe vaak de relatie koppelingen moeten worden gevolgd als **FollowRelLink** wordt gebruikt. Een kleinere waarde kan nodig zijn als de REST API-beperking door te veel aanvragen is. De standaardwaarde is `[Int32]::MaxValue`. Een waarde van 0 (nul) voor komt de volgende relatie koppelingen.

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

Geeft aan dat de cmdlet geen gebruik maakt van een proxy om de bestemming te bereiken.

Als u de geconfigureerde proxy in Internet Explorer wilt overs Laan of een proxy die in de omgeving is opgegeven, gebruikt u deze schakel optie.

Deze para meter is geïntroduceerd in Power shell 6,0.

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

Hiermee wordt de antwoord tekst in het opgegeven uitvoer bestand opgeslagen. Voer een pad en een bestands naam in. Als u het pad weglaat, de standaard instelling is de huidige locatie.

`Invoke-RestMethod`De resultaten worden standaard naar de pijp lijn geretourneerd. Als u de resultaten naar een bestand en naar de pijp lijn wilt verzenden, gebruikt u de para meter **PassThru** .

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

Hiermee worden de resultaten geretourneerd, naast het schrijven naar een bestand. Deze para meter is alleen geldig wanneer de **outfile** -para meter ook in de opdracht wordt gebruikt.

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

Maakt gebruik van een proxy server voor de aanvraag, in plaats van rechtstreeks verbinding te maken met de Internet resource. Geef de URI (Uniform Resource Identifier) van een netwerk proxy server op.

Deze functie is toegevoegd aan Power shell 6.0.0.

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
Default value: None
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

### -ResponseHeadersVariable

Hiermee maakt u een woorden lijst met antwoord koppen en slaat u deze op in de waarde van de opgegeven variabele. De sleutels van de woorden lijst bevatten de veld namen van de antwoord header die door de webserver wordt geretourneerd en de waarden zijn de respectieve veld waarden.

Deze functie is toegevoegd aan Power shell 6.0.0.

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

### -Hervatten

Hiermee wordt een beste poging gedaan om het downloaden van een gedeeltelijk bestand te hervatten. De para meter **Resume** vereist de **outfile** -para meter.

**Resume** werkt alleen op de grootte van het lokale bestand en het externe bestand en voert geen andere validatie uit dat het lokale bestand en het externe bestand hetzelfde zijn.

Als de lokale bestands grootte kleiner is dan de grootte van het externe bestand, probeert de cmdlet het downloaden van het bestand te hervatten en de resterende bytes toe te voegen aan het einde van het bestand.

Als de grootte van het lokale bestand hetzelfde is als de grootte van het externe bestand, wordt er geen actie ondernomen en wordt ervan uitgegaan dat de down load al is voltooid.

Als de grootte van het lokale bestand groter is dan de grootte van het externe bestand, wordt het lokale bestand overschreven en wordt het hele externe bestand volledig opnieuw gedownload. Dit gedrag is hetzelfde als het gebruik van een **bestand** zonder de bewerking te **hervatten**.

Als de externe server downloaden niet kan hervatten, wordt het lokale bestand overschreven en wordt het hele externe bestand volledig opnieuw gedownload. Dit gedrag is hetzelfde als het gebruik van een **bestand** zonder de bewerking te **hervatten**.

Als het lokale bestand niet bestaat, wordt het lokale bestand gemaakt en wordt het hele externe bestand volledig gedownload. Dit gedrag is hetzelfde als het gebruik van een **bestand** zonder de bewerking te **hervatten**.

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

Wanneer u een sessie variabele opgeeft, `Invoke-RestMethod` maakt een webaanvraag sessie object en wijst deze toe aan een variabele met de opgegeven naam in uw Power shell-sessie. U kunt de variabele in uw sessie gebruiken zodra de opdracht is voltooid.

In tegens telling tot een externe sessie is de sessie van de webaanvraag geen permanente verbinding. Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximum omleidings waarde en de teken reeks van de gebruikers agent. U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.

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

Hiermee worden controles van certificaat validaties overgeslagen die alle validaties bevatten, zoals verval datum, intrekking, vertrouwde basis instantie, enzovoort.

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

Hiermee wordt de validatie uitgeschakeld voor waarden die zijn door gegeven aan de para meters **Content type**, **headers** en **User agent** .

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

Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag. U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter. De waarden kunnen worden door gegeven aan de **SslProtocol** -para meter als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden. Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking. Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien. U kunt mogelijk niet meerdere waarden op alle platforms opgeven.

> [!NOTE]
> Op niet-Windows-platforms is het niet mogelijk om `'Tls, Tls12'` als optie te leveren.

Deze functie is toegevoegd aan Power shell 6.0.0.

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

### -StatusCodeVariable

Met deze para meter geeft u een variabele op waaraan de waarde van het gehele getal van de status code is toegewezen. Met de para meter kunnen succes berichten of fout berichten worden geïdentificeerd wanneer deze worden gebruikt in combi natie met de para meter **SkipHttpErrorCheck** .

Voer de variabele naam van de para meter in als een teken reeks zoals `-StatusCodeVariable "scv"` .

Deze para meter is geïntroduceerd in Power shell 7.

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

### -TimeoutSec

Hiermee geeft u op hoe lang de aanvraag in behandeling kan zijn voordat er een time-out optreedt. Voer een waarde in seconden in. De standaard waarde, 0, geeft een onbeperkte time-outwaarde.

Het kan tot vijf tien seconden duren voordat een Domain Name System query (DNS) wordt uitgevoerd of een time-out kan worden geretourneerd. Als uw aanvraag een hostnaam bevat waarvoor omzetting vereist is en u **TimeoutSec** instelt op een waarde die groter is dan nul, maar minder dan 15 seconden, kan het vijf tien seconden of langer duren voordat een webuitzondering wordt gegenereerd en er een time-out optreedt voor uw aanvraag.

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

### -Token

Het OAuth-of Bearer-token dat in de aanvraag moet worden meegenomen. Het **token** is vereist voor bepaalde **verificatie** opties. Deze kan niet onafhankelijk worden gebruikt.

**Token** neemt een `SecureString` met het token. Als u het token wilt opgeven, gebruikt u hand matig het volgende:

`Invoke-RestMethod -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

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

Hiermee geeft u de URI (Uniform Resource Identifier) op van de Internet bron waarnaar de webaanvraag wordt verzonden. Deze para meter ondersteunt HTTP-, HTTPS-, FTP-en FILE-waarden.

Deze parameter is vereist. De parameter naam (**URI**) is optioneel.

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

Als u een webonderdeelverzoek wilt maken, voert u de naam van een variabele zonder een dollar teken in de waarde van de para meter **SessionVariable** van een `Invoke-RestMethod` opdracht in. `Invoke-RestMethod` Hiermee maakt u de sessie en slaat u deze op in de variabele. Gebruik in volgende opdrachten de variabele als de waarde van de para meter **websession** .

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

U kunt de hoofd tekst van een webaanvraag door sluizen naar `Invoke-RestMethod` .

## Uitvoerwaarden

### Systeem. Int64, System. String, System.Xml.Xmldocument

De uitvoer van de cmdlet is afhankelijk van de indeling van de inhoud die wordt opgehaald.

### PSObject

Als de aanvraag JSON-teken reeksen retourneert, `Invoke-RestMethod` retourneert een **PSObject** die de teken reeksen vertegenwoordigt.

## Notities

Sommige functies zijn mogelijk niet beschikbaar op alle platforms.

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

[ConvertTo-Json](ConvertTo-Json.md)

[ConvertFrom-JSON](ConvertFrom-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)
