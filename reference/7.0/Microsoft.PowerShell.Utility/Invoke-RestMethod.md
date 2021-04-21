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
# Invoke-RestMethod

## Synopsis
Verzendt een HTTP- of HTTPS-aanvraag naar een RESTful-webservice.

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

## Description

De `Invoke-RestMethod` cmdlet verzendt HTTP- en HTTPS-aanvragen naar Representational State Transfer (REST)-webservices die rijke gestructureerde gegevens retourneren.

PowerShell formatteert het antwoord op basis van het gegevenstype. Voor een RSS- of ATOM-feed retourneert PowerShell de XML-knooppunten Item of Entry. Voor JavaScript Object Notation (JSON) of XML converteert of deserialiseert PowerShell de inhoud naar `[PSCustomObject]` objecten.

> [!NOTE]
> Wanneer het REST-eindpunt meerdere objecten retourneert, worden de objecten ontvangen als een matrix. Als u de uitvoer doorspijpt `Invoke-RestMethod` van naar een andere opdracht, wordt deze als één object `[Object[]]` verzonden. De inhoud van die matrix wordt niet geïndefeerd voor de volgende opdracht in de pijplijn.

Deze cmdlet is geïntroduceerd in Windows PowerShell 3.0.

Vanaf PowerShell 7.0 ondersteunt proxyconfiguratie gedefinieerd `Invoke-RestMethod` door omgevingsvariabelen. Zie de [sectie Opmerkingen](#notes) van dit artikel.

## Voorbeelden

### Voorbeeld 1: de PowerShell RSS-feed op halen

In dit voorbeeld wordt de `Invoke-RestMethod` cmdlet gebruikt om informatie op te halen uit de RSS-feed van het PowerShell-blog. De opdracht gebruikt de cmdlet om de waarden van de eigenschappen Titel en `Format-Table` **pubDate** van elke  blog in een tabel weer te geven.

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

### Voorbeeld 2: Een POST-aanvraag uitvoeren

In dit voorbeeld voert een gebruiker uit om `Invoke-RestMethod` een POST-aanvraag uit te doen op een intranetwebsite in de organisatie van de gebruiker.

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

De referenties worden gevraagd en vervolgens opgeslagen in en de `$Cred` URL die wordt gebruikt, wordt gedefinieerd in `$Url` .

De variabele beschrijft de zoekcriteria, geeft CSV op als uitvoermodus en geeft een tijdsperiode op voor geretourneerde gegevens die twee dagen geleden begint en één dag `$Body` geleden eindigt. De variabele body geeft waarden op voor parameters die van toepassing zijn op de REST API waarmee `Invoke-RestMethod` wordt gecommuniceerd.

De opdracht wordt uitgevoerd met alle variabelen op de plaats, waarbij een pad en bestandsnaam voor het resulterende `Invoke-RestMethod` CSV-uitvoerbestand worden opgegeven.

### Voorbeeld 3: Koppelingen voor relaties volgen

Sommige REST API's ondersteunen paginering via Relation Links per [RFC5988.](https://tools.ietf.org/html/rfc5988#page-6) In plaats van de header te parseren om de URL voor de volgende pagina op te halen, kunt u de cmdlet dit voor u laten doen. In dit voorbeeld worden de eerste twee pagina's met problemen uit de PowerShell GitHub-opslagplaats weergegeven.

```powershell
$url = 'https://api.github.com/repos/powershell/powershell/issues'
Invoke-RestMethod $url -FollowRelLink -MaximumFollowRelLink 2
```

### Voorbeeld 4: Vereenvoudigde verzending van meerdere onderdelen/formuliergegevens

Sommige API's vereisen `multipart/form-data` inzendingen om bestanden en gemengde inhoud te uploaden. In dit voorbeeld wordt gedemonstreerd hoe u het profiel van een gebruiker bijwerkt.

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

Voor het profielformulier zijn de volgende `firstName` velden `lastName` vereist: , `email` , , , en `avatar` `birthday` `hobbies` . De API verwacht een afbeelding voor de afbeelding van het gebruikersprofiel die in het veld moet worden `avatar` opgegeven. De API accepteert ook meerdere `hobbies` vermeldingen die in dezelfde vorm moeten worden ingediend.

Bij het maken `$Form` van de hashtabel worden de sleutelnamen gebruikt als formulierveldnamen. Standaard worden de waarden van de hashtabel geconverteerd naar tekenreeksen. Als er `System.IO.FileInfo` een waarde aanwezig is, wordt de bestandsinhoud verzonden. Als een verzameling zoals matrices of lijsten aanwezig is, wordt het formulierveld meerdere keren verzonden.

Door op `Get-Item` de `avatar` sleutel te gebruiken, wordt het object `FileInfo` ingesteld als de waarde. Het resultaat is dat de afbeeldingsgegevens `jdoe.png` voor worden verzonden.

Door een lijst op te geven voor de sleutel, is het veld eenmaal `hobbies` `hobbies` aanwezig in de inzendingen voor elk lijstitem.

### Voorbeeld 5: Meerdere headers doorgeven

API's vereisen vaak doorgegeven headers voor verificatie of validatie. In dit voorbeeld wordt gedemonstreerd hoe u meerdere headers van een naar `hash-table` een REST API.

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

### Voorbeeld 6: Geretourneerde items in de pijplijn opsnoemen

GitHub retourneert meerdere objecten in een matrix. Als u de uitvoer doorspijpt naar een andere opdracht, wordt deze als één `[Object[]]` object verzonden.

Als u de objecten in de pijplijn wilt opsnoemen, sleet u de resultaten door naar of verpakt u de `Write-Output` cmdlet tussen haakjes. In het volgende voorbeeld wordt het aantal objecten geteld dat door GitHub wordt geretourneerd. Vervolgens wordt het aantal objecten geteld dat in de pijplijn is opgeteld.

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

## Parameters

### -AllowUnencryptedAuthentication

Hiermee kunt u referenties en geheimen verzenden via niet-versleutelde verbindingen. Standaard leidt  het verstrekken  van referenties of een verificatieoptie met een **URI** die niet begint met tot een fout en wordt de aanvraag afgebroken om te voorkomen dat geheimen per ongeluk worden gecommuniceerd in tekst zonder e-mail via niet-versleutelde `https://` verbindingen. Als u dit gedrag voor eigen risico wilt overschrijven, geeft u de parameter **AllowUnencryptedAuthentication** op.

> [!WARNING]
> Het gebruik van deze parameter is niet veilig en wordt niet aanbevolen. Het wordt alleen verstrekt voor compatibiliteit met oudere systemen die geen versleutelde verbindingen kunnen bieden. Gebruik dit op uw eigen risico.

Deze functie is toegevoegd in PowerShell 6.0.0.

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

Hiermee geeft u het expliciete verificatietype op dat voor de aanvraag moet worden gebruikt. De standaardwaarde is **None**.
**Verificatie** kan niet worden gebruikt met **UseDefaultCredentials.**

Beschikbare verificatieopties:

- `None`: dit is de standaardoptie wanneer **verificatie** niet is opgegeven. Er wordt geen expliciete verificatie gebruikt.
- `Basic`: vereist **referentie**. De referenties worden gebruikt voor het verzenden van een RFC 7617 Basic `Authorization: Basic` Authentication-header in de indeling `base64(user:password)` van .
- `Bearer`: hiervoor is **Token vereist.** Verzendt en RFC 6750-header `Authorization: Bearer` met het opgegeven token. Dit is een alias voor **OAuth**
- `OAuth`: hiervoor is **Token vereist.** Verzendt een RFC 6750-header `Authorization: Bearer` met het opgegeven token. Dit is een alias voor **Bearer**

Als **verificatie wordt** opgegeven, worden alle headers overschrijven die worden geleverd aan `Authorization` **headers** of die zijn opgenomen in **WebSession**.

Deze functie is toegevoegd in PowerShell 6.0.0.

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

### -Body

Hiermee geeft u de body van de aanvraag. De hoofdtekst is de inhoud van de aanvraag die volgt op de headers.
U kunt ook een waarde voor de body doorspijpen naar `Invoke-RestMethod` .

De **parameter Body** kan worden gebruikt om een lijst met queryparameters op te geven of om de inhoud van het antwoord op te geven.

Wanneer de invoer een GET-aanvraag is en de body een is (meestal een hash-tabel), wordt de body als queryparameters toegevoegd aan de `IDictionary` Uniform Resource Identifier (URI). Voor andere aanvraagtypen (zoals POST) wordt de body ingesteld als de waarde van de aanvraag body in de standaardindeling name=value.

Wanneer de body een formulier is of de uitvoer van een andere aanroep, stelt PowerShell de aanvraaginhoud in `Invoke-WebRequest` op de formuliervelden.

De **parameter Body** kan ook een **System.Net.Http.MultipartFormDataContent-object** accepteren. Hierdoor kunnen aanvragen worden `multipart/form-data` gefaciliiliteert. Wanneer een **MultipartFormDataContent-object** wordt opgegeven voor **Hoofdtekst,** worden alle inhoudsgerelateerde headers die zijn opgegeven voor de parameters **ContentType,** **Headers** of **WebSession** overgeslagen door de inhoudsheaders van het `MultipartFormDataContent` object. Deze functie is toegevoegd in PowerShell 6.0.0.

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

Hiermee geeft u het clientcertificaat op dat wordt gebruikt voor een beveiligde webaanvraag. Voer een variabele in die een certificaat bevat of een opdracht of expressie die het certificaat op haalt.

Als u een certificaat wilt zoeken, `Get-PfxCertificate` gebruikt of gebruikt u de `Get-ChildItem` cmdlet in het station Certificaat ( `Cert:` ). Als het certificaat niet geldig is of onvoldoende bevoegdheid heeft, mislukt de opdracht.

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

Hiermee geeft u het digitale openbare-sleutelcertificaat (X509) op van een gebruikersaccount dat toestemming heeft om de aanvraag te verzenden. Voer de vingerafdruk van het certificaat in.

Certificaten worden gebruikt in verificatie op basis van clientcertificaten. Ze kunnen alleen worden toe te staan aan lokale gebruikersaccounts; ze werken niet met domeinaccounts.

Gebruik de opdracht of in het PowerShell-station om een vingerafdruk van het `Get-Item` `Get-ChildItem` certificaat op te `Cert:` halen.

> [!NOTE]
> Deze functie wordt momenteel alleen ondersteund op Windows-besturingssysteemplatforms.

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

### -ContentType

Hiermee geeft u het inhoudstype van de webaanvraag.

Als deze parameter wordt weggelaten en de aanvraagmethode POST is, `Invoke-RestMethod` stelt u het inhoudstype in op `application/x-www-form-urlencoded` . Anders wordt het inhoudstype niet opgegeven in de aanroep.

**ContentType** wordt overschrijven wanneer een `MultipartFormDataContent` object wordt opgegeven voor **Body**.

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

Hiermee geeft u een gebruikersaccount op dat toestemming heeft om de aanvraag te verzenden. Standaard is dit de huidige gebruiker.

Typ een gebruikersnaam, zoals **User01** of **Domain01\User01,** of voer een **PSCredential-object** in dat is gegenereerd door de `Get-Credential` cmdlet .

**Referenties** kunnen alleen worden gebruikt of in combinatie met bepaalde opties voor verificatieparameters.  Als u alleen gebruikt, geeft deze alleen referenties aan de externe server als de externe server een aanvraag voor verificatie-vraag verzendt. Wanneer u **verificatieopties** gebruikt, worden de referenties expliciet verzonden.

Referenties worden opgeslagen in een [PSCredential-object](/dotnet/api/system.management.automation.pscredential) en het wachtwoord wordt opgeslagen als een [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie Hoe veilig is **SecureString?** voor meer informatie over [SecureString-gegevensbeveiliging.](/dotnet/api/system.security.securestring#how-secure-is-securestring)

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

Hiermee geeft u de aangepaste methode op die wordt gebruikt voor de webaanvraag. Dit kan worden gebruikt met de aanvraagmethode die vereist is voor het eindpunt is geen beschikbare optie op de **methode**. **Methode** en **CustomMethod** kunnen niet samen worden gebruikt.

Voorbeeld:

`Invoke-RestMethod -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

Hiermee wordt een `TEST` HTTP-aanvraag naar de API ingediend.

Deze functie is toegevoegd in PowerShell 6.0.0.

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

Geeft aan dat de cmdlet de **KeepAlive-waarde** in de HTTP-header in stelt op False. **KeepAlive** is standaard True. **KeepAlive brengt** een permanente verbinding met de server tot stand om volgende aanvragen mogelijk te maken.

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

Geeft aan dat de cmdlet relationele koppelingen moet volgen.

Sommige REST API's ondersteunen paginering via Relation Links per [RFC5988.](https://tools.ietf.org/html/rfc5988#page-6) In plaats van de header te parseren om de URL voor de volgende pagina op te halen, kunt u de cmdlet dit voor u laten doen. Gebruik de parameter **MaximumFollowRelLink** om in te stellen hoe vaak u de relatiekoppelingen moet volgen.

Wanneer u deze switch gebruikt, retourneert de cmdlet een verzameling pagina's met resultaten. Elke pagina met resultaten kan meerdere resultaatitems bevatten.

Deze functie is toegevoegd in PowerShell 6.0.0.

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

### -Form

Converteert een woordenlijst naar een `multipart/form-data` inzending. **Formulier** kan niet worden gebruikt met **Body**.
Als **ContentType** wordt genegeerd.

De sleutels van de woordenlijst worden gebruikt als de namen van formulierveld. Standaard worden formulierwaarden geconverteerd naar tekenreekswaarden.

Als de waarde een **System.IO.FileInfo-object** is, wordt de inhoud van het binaire bestand verzonden.
De naam van het bestand wordt verzonden als de `filename` . De MIME wordt ingesteld als `application/octet-stream` . `Get-Item` kan worden gebruikt om het leveren van het **object System.IO.FileInfo te** vereenvoudigen.

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

Als de waarde een verzamelingstype is, zoals een Matrix of Lijst, wordt het veld for meerdere keren verzonden. De waarden van de lijst worden standaard behandeld als tekenreeksen. Als de waarde een **System.IO.FileInfo-object** is, wordt de inhoud van het binaire bestand verzonden. Geneste verzamelingen worden niet ondersteund.

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

In het bovenstaande voorbeeld wordt het veld drie keer in het formulier opgegeven, één keer `tags` voor elk van , en `Vacation` `Italy` `2017` . Het `pictures` veld wordt ook eenmaal verzonden voor elk bestand in de `2017-Italy` map. De binaire inhoud van de bestanden in die map wordt verzonden als de waarden.

Deze functie is toegevoegd in PowerShell 6.1.0.

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

Hiermee geeft u de headers van de webaanvraag. Voer een hashtabel of -woordenlijst in.

Als u UserAgent-headers wilt instellen, gebruikt u de parameter **UserAgent.** U kunt deze parameter niet gebruiken om headers of `User-Agent` cookies op te geven.

Inhoudsgerelateerde headers, zoals `Content-Type` , worden overschrijven wanneer een `MultipartFormDataContent` object wordt opgegeven voor **Hoofdtekst.**

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

### -InFile

Haalt de inhoud van de webaanvraag op uit een bestand.

Voer een pad en bestandsnaam in. Als u het pad weglaten, is de standaardwaarde de huidige locatie.

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

Hiermee geeft u op hoe vaak u relatiekoppelingen moet volgen **als FollowRelLink** wordt gebruikt. Mogelijk is er een kleinere waarde nodig als de REST API wordt beperkt vanwege te veel aanvragen. De standaardwaarde is `[Int32]::MaxValue`. Een waarde van 0 (nul) voorkomt het volgen van relatiekoppelingen.

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

Hiermee geeft u op hoe vaak PowerShell een verbinding omleiden naar een alternatieve Uniform Resource Identifier (URI) voordat de verbinding mislukt. De standaardwaarde is 5. Met de waarde 0 (nul) wordt alle omleiding voorkomen.

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

Hiermee geeft u op hoe vaak PowerShell opnieuw verbinding maakt wanneer een foutcode tussen 400 en 599 wordt ontvangen, inclusief of 304. Zie ook **de parameter RetryIntervalSec** voor het opgeven van het aantal nieuwe poging.

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

Hiermee geeft u de methode die wordt gebruikt voor de webaanvraag. De aanvaardbare waarden voor deze parameter zijn:

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

De **parameter CustomMethod** kan worden gebruikt voor aanvraagmethoden die hierboven niet worden vermeld.

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

### -NoProxy

Geeft aan dat de cmdlet geen proxy gebruikt om de bestemming te bereiken.

Wanneer u de proxy wilt omzeilen die is geconfigureerd in Internet Explorer of een proxy die is opgegeven in de omgeving, gebruikt u deze switch.

Deze parameter is geïntroduceerd in PowerShell 6.0.

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

### -OutFile

Slaat de antwoord-body in het opgegeven uitvoerbestand. Voer een pad en bestandsnaam in. Als u het pad weglaten, is de standaardwaarde de huidige locatie.

Retourneert `Invoke-RestMethod` standaard de resultaten naar de pijplijn. Als u de resultaten wilt verzenden naar een bestand en naar de pijplijn, gebruikt u de parameter **Passthru.**

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

Retourneert de resultaten, naast het schrijven ervan naar een bestand. Deze parameter is alleen geldig wanneer **de OutFile** parameter wordt ook gebruikt in de opdracht.

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

Geeft aan dat de cmdlet de header, indien aanwezig, moet behouden `Authorization` tussen omleidingen.

De cmdlet ontdoet de `Authorization` header standaard voordat deze wordt omgeleid. Als u deze parameter opgeeft, wordt deze logica uitgeschakeld voor gevallen waarin de header naar de omleidingslocatie moet worden verzonden.

Deze functie is toegevoegd in PowerShell 6.0.0.

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

Maakt gebruik van een proxyserver voor de aanvraag, in plaats van rechtstreeks verbinding te maken met de internetresource. Voer de Uniform Resource Identifier (URI) van een netwerkproxyserver in.

Deze functie is toegevoegd in PowerShell 6.0.0.

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

Hiermee geeft u een gebruikersaccount dat is gemachtigd voor het gebruik van de proxyserver die is opgegeven door de **proxyparameter.** Standaard is dit de huidige gebruiker.

Typ een gebruikersnaam, zoals **User01** of **Domain01\User01,** of voer een -object in, zoals een object dat wordt gegenereerd door **User@Domain.Com** `PSCredential` de `Get-Credential` cmdlet .

Deze parameter is alleen geldig wanneer de **Proxy** parameter wordt ook gebruikt in de opdracht. U kunt de parameters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.

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

Geeft aan dat de cmdlet de referenties van de huidige gebruiker gebruikt voor toegang tot de proxyserver die is opgegeven door de **proxyparameter.**

Deze parameter is alleen geldig wanneer de **proxy** parameter wordt ook gebruikt in de opdracht. U kunt de parameters **ProxyCredential** en **ProxyUseDefaultCredentials** niet gebruiken in dezelfde opdracht.

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

Hiermee maakt u een woordenlijst antwoordheaders en slaat u deze op in de waarde van de opgegeven variabele. De sleutels van de woordenlijst bevatten de veldnamen van de antwoordheader die wordt geretourneerd door de webserver en de waarden zijn de respectieve veldwaarden.

Deze functie is toegevoegd in PowerShell 6.0.0.

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

Voert een poging uit om het downloaden van een gedeeltelijk bestand te hervatten. Voor de parameter **Resume** is de parameter **OutFile** vereist.

**Hervatten** werkt alleen op de grootte van het lokale bestand en externe bestand en voert geen andere validatie uit dat het lokale bestand en het externe bestand hetzelfde zijn.

Als de grootte van het lokale bestand kleiner is dan de externe bestandsgrootte, probeert de cmdlet het downloaden van het bestand te hervatten en de resterende bytes toe te toevoegen aan het einde van het bestand.

Als de grootte van het lokale bestand hetzelfde is als de grootte van het externe bestand, wordt er geen actie ondernomen en wordt ervan uitgenomen dat het downloaden al is voltooid.

Als de lokale bestandsgrootte groter is dan de grootte van het externe bestand, wordt het lokale bestand overschreven en wordt het hele externe bestand volledig opnieuw gedownload. Dit gedrag is hetzelfde als het gebruik van **OutFile** zonder **Hervatten.**

Als de externe server geen ondersteuning biedt voor het downloaden van het downloaden, wordt het lokale bestand overschreven en wordt het hele externe bestand volledig opnieuw gedownload. Dit gedrag is hetzelfde als het gebruik van **OutFile** zonder **Hervatten.**

Als het lokale bestand niet bestaat, wordt het lokale bestand gemaakt en wordt het hele externe bestand volledig gedownload. Dit gedrag is hetzelfde als het gebruik van **OutFile** zonder **Hervatten.**

Deze functie is toegevoegd in PowerShell 6.1.0.

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

Hiermee geeft u het interval op tussen nieuwe proberen voor de verbinding wanneer een foutcode tussen 400 en 599 wordt ontvangen, inclusief of 304. Zie ook **de parameter MaximumRetryCount** voor het opgeven van het aantal nieuwe poging.

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

Hiermee geeft u een variabele waarvoor deze cmdlet maakt een webaanvraagsessie en slaat deze in de waarde.
Voer een variabelenaam in zonder het dollarteken ( `$` ).

Wanneer u een sessievariabele opgeeft, maakt een webaanvraagsessieobject en wijst u dit toe aan een variabele met de opgegeven `Invoke-RestMethod` naam in uw PowerShell-sessie. U kunt de variabele in uw sessie gebruiken zodra de opdracht is voltooid.

In tegenstelling tot een externe sessie is de webaanvraagsessie geen permanente verbinding. Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximale omleidingswaarde en de tekenreeks van de gebruikersagent. U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.

Als u de webaanvraagsessie in volgende webaanvragen wilt gebruiken, geeft u de sessievariabele op in de waarde van de parameter **WebSession.** PowerShell gebruikt de gegevens in het webaanvraagsessieobject bij het tot stand brengen van de nieuwe verbinding. Als u een waarde in de webaanvraagsessie wilt overschrijven, gebruikt u een cmdlet-parameter, zoals **UserAgent** of **Credential.** Parameterwaarden hebben voorrang op waarden in de webaanvraagsessie.

U kunt de parameters **SessionVariable en** **WebSession** niet gebruiken in dezelfde opdracht.

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

Certificaatvalidatiecontroles die alle validaties bevatten, zoals verloop, intrekking, vertrouwde basisinstantie, enzovoort, worden overgeslagen.

> [!WARNING]
> Het gebruik van deze parameter is niet veilig en wordt niet aanbevolen. Deze switch is alleen bedoeld om te worden gebruikt voor bekende hosts die een zelf-ondertekend certificaat gebruiken voor testdoeleinden. Gebruik op uw eigen risico.

Deze functie is toegevoegd in PowerShell 6.0.0.

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

Geeft aan dat de cmdlet headers moet toevoegen aan de aanvraag zonder validatie.

Deze switch moet worden gebruikt voor sites waarvoor headerwaarden zijn vereist die niet voldoen aan de standaarden.
Als u deze switch opgeeft, wordt validatie uitgeschakeld zodat de waarde niet kan worden doorgegeven. Wanneer dit is opgegeven, worden alle headers zonder validatie toegevoegd.

Hiermee wordt validatie uitgeschakeld voor waarden die worden doorgegeven aan de parameters **ContentType,** **Headers** en **UserAgent.**

Deze functie is toegevoegd in PowerShell 6.0.0.

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

Deze parameter zorgt ervoor dat de cmdlet HTTP-foutstatussen negeert en antwoorden blijft verwerken.
De foutreacties worden naar de pijplijn geschreven alsof ze zijn geslaagd.

Deze parameter is geïntroduceerd in PowerShell 7.

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

Hiermee stelt u de SSL/TLS-protocollen in die toegestaan zijn voor de webaanvraag. Standaard zijn alle SSL/TLS-protocollen toegestaan die door het systeem worden ondersteund. **Met SslProtocol** kunt u beperken tot specifieke protocollen voor nalevingsdoeleinden.

Deze waarden worden gedefinieerd als een op vlag gebaseerde enumeratie. U kunt meerdere waarden combineren om meerdere vlaggen in te stellen met behulp van deze parameter. De waarden kunnen worden doorgegeven aan de **parameter SslProtocol** als een matrix met waarden of als een door komma's gescheiden tekenreeks van deze waarden. De cmdlet combineert de waarden met behulp van een binaire-OR-bewerking. Het doorgeven van waarden als een matrix is de eenvoudigste optie. Hiermee kunt u ook tab-completion gebruiken voor de waarden. Mogelijk kunt u niet meerdere waarden op alle platformen leveren.

> [!NOTE]
> Op niet-Windows-platforms is het mogelijk niet mogelijk om op te `'Tls, Tls12'` geven als een optie.

Deze functie is toegevoegd in PowerShell 6.0.0.

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

Met deze parameter geeft u een variabele op die het gehele getal van een statuscode krijgt toegewezen. De parameter kan succesberichten of foutberichten identificeren wanneer deze worden gebruikt met de parameter **SkipHttpErrorCheck.**

Voer de variabelenaam van de parameter in als een tekenreeks zoals `-StatusCodeVariable "scv"` .

Deze parameter is geïntroduceerd in PowerShell 7.

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

Hiermee geeft u op hoe lang de aanvraag in behandeling kan zijn voordat er een times-out wordt uitgevoerd. Voer een waarde in seconden in. De standaardwaarde, 0, geeft een onbeperkte time-out aan.

Het Domain Name System (DNS)-query kan tot 15 seconden duren voordat er een time-out of retourneren is. Als uw aanvraag een hostnaam bevat die een oplossing vereist en u **TimeoutSec** in stelt op een waarde die groter is dan nul, maar minder dan 15 seconden, kan het 15 seconden of langer duren voordat een WebException wordt gegeven en er een time-out van uw aanvraag wordt gegeven.

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

Het OAuth- of Bearer-token dat in de aanvraag moet worden op te nemen. **Token** is vereist voor bepaalde **verificatieopties.** Deze kan niet onafhankelijk worden gebruikt.

**Token** neemt een `SecureString` die het token bevat. Gebruik het volgende handmatig om het token op te leveren:

`Invoke-RestMethod -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

Deze parameter is geïntroduceerd in PowerShell 6.0.

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

Hiermee geeft u een waarde op voor de HTTP-antwoordheader voor overdrachtcoderen. De aanvaardbare waarden voor deze parameter zijn:

- Ge chunked
- Comprimeren
- Deflate
- Gzip
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

Hiermee geeft u de Uniform Resource Identifier (URI) op van de internetresource waar de webaanvraag naar wordt verzonden. Deze parameter ondersteunt http-, HTTPS-, FTP- en BESTANDswaarden.

Deze parameter is vereist. De parameternaam (**URI**) is optioneel.

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

Deze parameter is afgeschaft. Vanaf PowerShell 6.0.0 gebruiken alle webaanvragen alleen basisparsering. Deze parameter is alleen opgenomen voor achterwaartse compatibiliteit en elk gebruik ervan heeft geen invloed op de werking van de cmdlet.

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

Geeft aan dat de cmdlet de referenties van de huidige gebruiker gebruikt om de webaanvraag te verzenden. Dit kan niet worden gebruikt met **verificatie of** **referentie** en wordt mogelijk niet ondersteund op alle platforms.

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

### -UserAgent

Hiermee geeft u een tekenreeks voor de gebruikersagent op voor de webaanvraag.

De standaardgebruikersagent is vergelijkbaar met `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` met kleine variaties voor elk besturingssysteem en platform.

Als u een website wilt testen met de standaard tekenreeks van de gebruikersagent die door de meeste internetbrowsers wordt gebruikt, gebruikt u de eigenschappen van de [klasse PSUserAgent,](/dotnet/api/microsoft.powershell.commands.psuseragent) zoals Chrome, FireFox, InternetExplorer, Opera en Safari.

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

### -WebSession

Hiermee geeft u een webaanvraagsessie. Voer de naam van de variabele in, inclusief het dollarteken ( `$` ).

Als u een waarde in de webaanvraagsessie wilt overschrijven, gebruikt u een cmdlet-parameter, zoals **UserAgent** of **Credential.** Parameterwaarden hebben voorrang op waarden in de webaanvraagsessie. Inhoudsgerelateerde headers, zoals , worden ook overschrijven wanneer een `Content-Type` **MultipartFormDataContent-object** wordt opgegeven voor **Hoofdtekst.**

In tegenstelling tot een externe sessie is de webaanvraagsessie geen permanente verbinding. Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximale omleidingswaarde en de tekenreeks van de gebruikersagent. U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.

Als u een webaanvraagsessie wilt maken, voert u een variabelenaam in, zonder dollarteken, in de waarde van de parameter **SessionVariable** van een `Invoke-RestMethod` opdracht. `Invoke-RestMethod` maakt de sessie en slaat deze op in de variabele . In volgende opdrachten gebruikt u de variabele als de waarde van de parameter **WebSession.**

U kunt de parameters **SessionVariable en** **WebSession** niet gebruiken in dezelfde opdracht.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## Invoerwaarden

### System.Object

U kunt de body van een webaanvraag doorseen naar `Invoke-RestMethod` .

## Uitvoerwaarden

### System.Int64, System.String, System.Xml.XmlDocument

De uitvoer van de cmdlet is afhankelijk van de indeling van de inhoud die wordt opgehaald.

### PSObject

Als de aanvraag JSON-tekenreeksen retourneert, `Invoke-RestMethod` retourneert een **PSObject** dat de tekenreeksen vertegenwoordigt.

## Notities

Sommige functies zijn mogelijk niet op alle platforms beschikbaar.

Vanwege wijzigingen in .NET Core 3.1 gebruikt PowerShell 7.0 en hoger de eigenschap [HttpClient.DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) om de proxyconfiguratie te bepalen.

De waarde van deze eigenschap wordt bepaald door uw platform:

- **Voor Windows:** leest proxyconfiguratie uit omgevingsvariabelen. Als deze variabelen niet zijn gedefinieerd, wordt de eigenschap afgeleid van de proxy-instellingen van de gebruiker.
- **Voor macOS:** leest proxyconfiguratie uit omgevingsvariabelen. Als deze variabelen niet zijn gedefinieerd, wordt de eigenschap afgeleid van de proxy-instellingen van het systeem.
- **Voor Linux:** leest proxyconfiguratie uit omgevingsvariabelen. Als deze variabelen niet zijn gedefinieerd, initialiseert de eigenschap een niet-geconfigureerd exemplaar dat alle adressen omzeilt.

De omgevingsvariabelen die worden `DefaultProxy` gebruikt voor initialisatie op Windows- en Unix-platforms zijn:

- `HTTP_PROXY`: de hostnaam of het IP-adres van de proxyserver die wordt gebruikt voor HTTP-aanvragen.
- `HTTPS_PROXY`: de hostnaam of het IP-adres van de proxyserver die wordt gebruikt voor HTTPS-aanvragen.
- `ALL_PROXY`: de hostnaam of het IP-adres van de proxyserver die wordt gebruikt voor HTTP- en HTTPS-aanvragen voor het geval `HTTP_PROXY` of `HTTPS_PROXY` niet zijn gedefinieerd.
- `NO_PROXY`: een door komma's gescheiden lijst met hostnamen die moeten worden uitgesloten van proxying.

## Verwante koppelingen

[ConvertTo-Json](ConvertTo-Json.md)

[ConvertFrom-Json](ConvertFrom-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)
