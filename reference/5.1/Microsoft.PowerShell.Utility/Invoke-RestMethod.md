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
# Invoke-RestMethod

## Samen vatting
Hiermee verzendt u een HTTP-of HTTPS-aanvraag naar een REST webservice.

## Syntax

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-CertificateThumbprint <String>] [-Certificate <X509Certificate>]
 [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>] [-Headers <IDictionary>]
 [-MaximumRedirection <Int32>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials]
 [-Body <Object>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>]
 [-PassThru] [<CommonParameters>]
```

## Beschrijving

De `Invoke-RestMethod` cmdlet verzendt HTTP-en HTTPS-aanvragen voor het representatief-webservices (rest) voor het retour neren van gegevens die Rich structured data worden geretourneerd.

Windows Power shell formatteert de reactie op basis van het gegevens type. Voor een RSS-of ATOM-feed retourneert Windows Power shell het item of de XML-knoop punten van de vermelding. Voor JavaScript Object Notation (JSON) of XML, wordt de inhoud door Windows Power shell geconverteerd (of gedeserialiseerd) naar objecten.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

> [!NOTE]
> Standaard kan script code op de webpagina worden uitgevoerd wanneer de pagina wordt geparseerd om de eigenschap in te vullen `ParsedHtml` . Gebruik de schakel optie **UseBasicParsing** om dit te onderdrukken.

## Voorbeelden

### Voor beeld 1: de Power shell-RSS-feed ophalen

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

Met deze opdracht wordt de `Invoke-RestMethod` cmdlet gebruikt om informatie op te halen uit de RSS-feed voor het Power shell-blog. De opdracht gebruikt de `Format-Table` cmdlet om de waarden van de eigenschappen **title** en **pubDate** van elke blog in een tabel weer te geven.

### Voorbeeld 2

In het volgende voor beeld wordt een gebruiker uitgevoerd `Invoke-RestMethod` om een post-aanvraag uit te voeren op een intranet website in de organisatie van de gebruiker.

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

### Voor beeld 3: meerdere headers door geven

In dit voor beeld ziet u hoe u meerdere headers kunt door geven van een- `hash-table` naar-rest API.

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

Api's vereisen vaak door gegeven headers voor verificatie, validatie, enzovoort.

### Voor beeld 3: formulier gegevens verzenden

Wanneer de hoofd tekst een formulier is of de uitvoer van een andere `Invoke-WebRequest` aanroep, stelt Power shell de aanvraag inhoud in op de formulier velden.

Bijvoorbeeld:

```powershell
$R = Invoke-WebRequest https://website.com/login.aspx
$R.Forms[0].Name = "MyName"
$R.Forms[0].Password = "MyPassword"
Invoke-RestMethod https://website.com/service.aspx -Body $R.Forms[0]
```

## Parameters

### -Hoofd tekst

Hiermee geeft u de hoofd tekst van de aanvraag. De hoofd tekst is de inhoud van de aanvraag die de headers volgt.
U kunt ook de waarde van een hoofd tekst sluist naar `Invoke-RestMethod` .

De para meter **Body** kan worden gebruikt om een lijst met query parameters op te geven of de inhoud van het antwoord op te geven.

Wanneer de invoer een GET-aanvraag is en de hoofd tekst een IDictionary is (meestal een hash-tabel), wordt de hoofd tekst als query parameters toegevoegd aan de URI. Voor andere aanvraag typen (zoals POST) wordt de hoofd tekst ingesteld als de waarde van de aanvraag tekst in de notatie standaard naam = waarde.

> [!WARNING]
> De uitgebreide uitvoer van een POST hoofdtekst eindigt met, hoewel `with -1-byte payload` de hoofd tekst zowel bekend als in de `Content-Length` http-header wordt verzonden.

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

Gebruik de `Get-Item` `Get-ChildItem` opdracht of in het Windows Power Shell-station () om een certificaat vingerafdruk te verkrijgen `Cert:` .

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

Als deze para meter wordt wegge laten en de aanvraag methode is `Invoke-RestMethod` ingesteld op post, stelt het inhouds type in op ' Application/x-www-form-urlencoded '. Anders is het inhouds type niet opgegeven in de aanroep.

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
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableKeepAlive

Hiermee stelt u de **keepalive** -waarde in de http-header in op ONWAAR. Standaard is **keepalive** ingesteld op True.
Met **keepalive** wordt een permanente verbinding met de server tot stand gebracht om volgende aanvragen te vergemakkelijken.

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

### -Headers

Hiermee geeft u de kopteksten van de webaanvraag. Voer een hash-tabel of-woorden lijst in.

Gebruik de **agent** -para meter om de agent headers in te stellen. U kunt deze para meter niet gebruiken om de headers van User agent of cookie op te geven.

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

Bepaalt hoe vaak Windows Power shell een verbinding met een alternatieve URI (Uniform Resource Identifier) omleidt voordat de verbinding is mislukt. De standaard waarde is 5. Een waarde van 0 (nul) voor komt dat alle omleidingen.

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
Default value: Default
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

### -Proxy

Maakt gebruik van een proxy server voor de aanvraag, in plaats van rechtstreeks verbinding te maken met de Internet resource. Voer de URI van een netwerk proxy server in.

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

Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.

Deze para meter is alleen geldig wanneer de **proxy** parameter ook in de opdracht wordt gebruikt. U kunt de para meters **ProxyCredential** en **ProxyUseDefaultCredentials** niet in dezelfde opdracht gebruiken.

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

### -ProxyUseDefaultCredentials

Gebruikt de referenties van de huidige gebruiker om toegang te krijgen tot de proxy server die is opgegeven door de **proxy** -para meter.

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

Hiermee maakt u een web Request-sessie en slaat u deze op in de waarde van de opgegeven variabele. Geef een naam op voor de variabele zonder het dollar teken ( `$` )-symbool.

Wanneer u een sessie variabele opgeeft, `Invoke-RestMethod` maakt een webaanvraag sessie object en wijst deze toe aan een variabele met de opgegeven naam in uw Power shell-sessie. U kunt de variabele in uw sessie gebruiken zodra de opdracht is voltooid.

In tegens telling tot een externe sessie is de sessie voor webaanvragen geen permanente verbinding. Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximum omleidings waarde en de teken reeks van de gebruikers agent. U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.

Als u de webaanvraag sessie in volgende webaanvragen wilt gebruiken, geeft u de sessie variabele op in de waarde van de para meter **websessie** . Windows Power shell gebruikt de gegevens in het sessie object voor webaanvragen wanneer de nieuwe verbinding tot stand wordt gebracht. Als u een waarde in de sessie voor webaanvragen wilt overschrijven, gebruikt u een cmdlet-para meter, zoals **User agent** of **Credential**. Parameter waarden hebben prioriteit boven waarden in de webaanvraag sessie.

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

Het kan tot vijf tien seconden duren voordat een Domain Name System query (DNS) wordt uitgevoerd of een time-out kan worden geretourneerd. Als uw aanvraag een hostnaam bevat waarvoor omzetting vereist is en u TimeoutSec instelt op een waarde die groter is dan nul, maar minder dan 15 seconden, kan het vijf tien seconden of langer duren voordat een webuitzondering wordt gegenereerd en er een time-out optreedt voor uw aanvraag.

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

Geeft aan dat de cmdlet gebruikmaakt van basis parsering. De cmdlet retourneert de onbewerkte HTML in een **teken reeks** object.

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

Gebruikt de referenties van de huidige gebruiker om de webaanvraag te verzenden.

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

De standaard gebruikers agent is vergelijkbaar met ' Mozilla/5.0 ' (Windows NT; Windows NT 6,1; en-US) WindowsPowerShell/3.0 ' met kleine variaties voor elk besturings systeem en platform.

Als u een website wilt testen met de standaard teken reeks van de gebruikers agent die wordt gebruikt door de meeste Internet browsers, gebruikt u de eigenschappen van de [PSUserAgent](/dotnet/api/microsoft.powershell.commands) -klasse, zoals Chrome, Firefox, Internet Explorer, Opera en Safari.

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

Als u een webaanvraag sessie wilt maken, voert u een naam in voor de variabele (zonder een dollar teken) in de waarde van de para meter **SessionVariable** van een `Invoke-RestMethod` opdracht. `Invoke-RestMethod` Hiermee maakt u de sessie en slaat u deze op in de variabele. Gebruik in volgende opdrachten de variabele als de waarde van de para meter **websession** .

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

### System.Xml.Xmldocument, Microsoft.PowerShell.Commands.HtmlWebResponseObject, System. String

De uitvoer van de cmdlet is afhankelijk van de indeling van de inhoud die wordt opgehaald.

### PSObject

Als de aanvraag JSON-teken reeksen retourneert, `Invoke-RestMethod` retourneert een PSObject die de teken reeksen vertegenwoordigt.

## Notities

## Verwante koppelingen

[ConvertTo-Json](ConvertTo-Json.md)

[ConvertFrom-JSON](ConvertFrom-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)
