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
# Invoke-RestMethod

## Synopsis
Verzendt een HTTP- of HTTPS-aanvraag naar een RESTful-webservice.

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

## Description

De `Invoke-RestMethod` cmdlet verzendt HTTP- en HTTPS-aanvragen naar Representational State Transfer (REST)-webservices die rijke gestructureerde gegevens retourneren.

PowerShell formatteert het antwoord op basis van het gegevenstype. Voor een RSS- of ATOM-feed retourneert PowerShell de XML-knooppunten Item of Entry. Voor JavaScript Object Notation (JSON) of XML converteert of deserialiseert PowerShell de inhoud naar `[PSCustomObject]` objecten.

> [!NOTE]
> Wanneer het REST-eindpunt meerdere objecten retourneert, worden de objecten ontvangen als een matrix. Als u de uitvoer doorspijpt `Invoke-RestMethod` van naar een andere opdracht, wordt deze als één object `[Object[]]` verzonden. De inhoud van die matrix wordt niet geïndefeerd voor de volgende opdracht in de pijplijn.

Deze cmdlet is geïntroduceerd in Windows PowerShell 3.0.

> [!NOTE]
> Standaard kan scriptcode op de webpagina worden uitgevoerd wanneer de pagina wordt geparseerd om de eigenschap te `ParsedHtml` vullen. Gebruik de **schakelknop UseBasicParsing** om dit te onderdrukken.

## Voorbeelden

### Voorbeeld 1: de PowerShell RSS-feed op halen

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

Met deze opdracht wordt de `Invoke-RestMethod` cmdlet gebruikt om informatie op te halen uit de RSS-feed van het PowerShell-blog. De opdracht gebruikt de cmdlet om de waarden van de eigenschappen Titel en `Format-Table` **pubDate** van elke  blog in een tabel weer te geven.

### Voorbeeld 2

In het volgende voorbeeld wordt een gebruiker uitgevoerd om `Invoke-RestMethod` een POST-aanvraag uit te voeren op een intranetwebsite in de organisatie van de gebruiker.

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

### Voorbeeld 3: Meerdere headers doorgeven

In dit voorbeeld wordt gedemonstreerd hoe u meerdere headers van een naar `hash-table` een REST API.

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

API's vereisen vaak doorgegeven headers voor verificatie, validatie, enzovoort.

### Voorbeeld 3: Formuliergegevens verzenden

Wanneer de body een formulier is of de uitvoer van een andere aanroep is, stelt PowerShell de aanvraaginhoud in `Invoke-WebRequest` op de formuliervelden.

Bijvoorbeeld:

```powershell
$R = Invoke-WebRequest https://website.com/login.aspx
$R.Forms[0].Name = "MyName"
$R.Forms[0].Password = "MyPassword"
Invoke-RestMethod https://website.com/service.aspx -Body $R.Forms[0]
```

### Voorbeeld 4: Geretourneerde items in de pijplijn opsnoemen

GitHub retourneert meerdere objecten in een matrix. Als u de uitvoer doorspijpt naar een andere opdracht, wordt deze als één `[Object[]]` object verzonden.

Als u de objecten in de pijplijn wilt opsnoemen, sloop de resultaten door naar of verpakt u de `Write-Output` cmdlet tussen haakjes. In het volgende voorbeeld wordt het aantal objecten geteld dat door GitHub wordt geretourneerd. Vervolgens wordt het aantal objecten geteld dat in de pijplijn is geïnsemaneerd.

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

### -Body

Hiermee geeft u de body van de aanvraag. De hoofdtekst is de inhoud van de aanvraag die volgt op de headers.
U kunt ook een bodywaarde doorspijpen naar `Invoke-RestMethod` .

De **parameter Body** kan worden gebruikt om een lijst met queryparameters op te geven of om de inhoud van het antwoord op te geven.

Wanneer de invoer een GET-aanvraag is en de body een IDictionary is (meestal een hash-tabel), wordt de body als queryparameters toegevoegd aan de URI. Voor andere aanvraagtypen (zoals POST) wordt de body ingesteld als de waarde van de aanvraag body in de standaardindeling name=value.

> [!WARNING]
> De uitgebreide uitvoer van een POST-hoofdtekst eindigt met , ook al is de grootte van de hoofdtekst bekend en `with -1-byte payload` verzonden in de `Content-Length` HTTP-header.

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

Als u een vingerafdruk van het certificaat wilt verkrijgen, gebruikt u `Get-Item` de opdracht of op het Windows PowerShell ( `Get-ChildItem` `Cert:` ).

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

Als deze parameter wordt weggelaten en de aanvraagmethode POST is, stelt u het inhoudstype in op `Invoke-RestMethod` 'application/x-www-form-urlencoded'. Anders wordt het inhoudstype niet opgegeven in de aanroep.

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

Typ een gebruikersnaam, zoals **User01** of **Domain01\User01,** of voer een **PSCredential-object** in dat door de `Get-Credential` cmdlet is gegenereerd.

Referenties worden opgeslagen in een [PSCredential-object](/dotnet/api/system.management.automation.pscredential) en het wachtwoord wordt opgeslagen als een [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie How secure is **SecureString?** (Hoe veilig is SecureString?) voor meer informatie over [SecureString-gegevensbeveiliging.](/dotnet/api/system.security.securestring#how-secure-is-securestring)

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

Hiermee stelt **u de KeepAlive-waarde** in de HTTP-header in op False. **KeepAlive** is standaard Waar.
**KeepAlive brengt** een permanente verbinding met de server tot stand om volgende aanvragen mogelijk te maken.

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

Hiermee geeft u de headers van de webaanvraag. Voer een hashtabel of -woordenlijst in.

Als u UserAgent-headers wilt instellen, gebruikt u de parameter **UserAgent.** U kunt deze parameter niet gebruiken om UserAgent- of cookieheaders op te geven.

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

### -MaximumRedirection

Hiermee bepaalt u hoe vaak Windows PowerShell verbinding omleiden naar een alternatieve Uniform Resource Identifier (URI) voordat de verbinding mislukt. De standaardwaarde is 5. Met de waarde 0 (nul) wordt alle omleiding voorkomen.

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

### -Proxy

Maakt gebruik van een proxyserver voor de aanvraag, in plaats van rechtstreeks verbinding te maken met de internetresource. Voer de URI van een netwerkproxyserver in.

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

Hiermee geeft u een gebruikersaccount dat is gemachtigd voor het gebruik van de proxyserver die is opgegeven door de **proxyparameter.** Standaard is dit de huidige gebruiker.

Typ een gebruikersnaam, zoals 'User01' of 'Domain01\User01', of voer een **PSCredential-object** in, zoals een object dat wordt gegenereerd door de `Get-Credential` cmdlet .

Deze parameter is alleen geldig wanneer de **Proxy** parameter wordt ook gebruikt in de opdracht. U kunt de parameters **ProxyCredential** en **ProxyUseDefaultCredentials** niet gebruiken in dezelfde opdracht.

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

Gebruikt de referenties van de huidige gebruiker voor toegang tot de proxyserver die is opgegeven door de **proxyparameter.**

Deze parameter is alleen geldig wanneer de **Proxy** parameter wordt ook gebruikt in de opdracht. U kunt de parameters **ProxyCredential** en **ProxyUseDefaultCredentials** niet gebruiken in dezelfde opdracht.

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

Hiermee maakt u een webaanvraagsessie en slaat u deze op in de waarde van de opgegeven variabele. Voer een variabelenaam in zonder het dollarteken ( `$` ).

Wanneer u een sessievariabele opgeeft, maakt een webaanvraagsessieobject en wijst u dit toe aan een variabele met de opgegeven `Invoke-RestMethod` naam in uw PowerShell-sessie. U kunt de variabele in uw sessie gebruiken zodra de opdracht is voltooid.

In tegenstelling tot een externe sessie is de webaanvraagsessie geen permanente verbinding. Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximale omleidingswaarde en de tekenreeks van de gebruikersagent. U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.

Als u de webaanvraagsessie in volgende webaanvragen wilt gebruiken, geeft u de sessievariabele op in de waarde van de parameter **WebSession.** Windows PowerShell gebruikt de gegevens in het webaanvraagsessieobject bij het tot stand brengen van de nieuwe verbinding. Als u een waarde in de webaanvraagsessie wilt overschrijven, gebruikt u een cmdlet-parameter, zoals **UserAgent** of **Credential.** Parameterwaarden hebben voorrang op waarden in de webaanvraagsessie.

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

### -TimeoutSec

Hiermee geeft u op hoe lang de aanvraag in behandeling kan zijn voordat er een times-out wordt uitgevoerd. Voer een waarde in seconden in. De standaardwaarde, 0, geeft een onbeperkte time-out aan.

Het Domain Name System (DNS)-query kan tot 15 seconden duren om een retour- of time-out te retourneren. Als uw aanvraag een hostnaam bevat die een oplossing vereist en u TimeoutSec in stelt op een waarde die groter is dan nul, maar minder dan 15 seconden, kan het 15 seconden of langer duren voordat een WebException wordt gegeven en er een time-out van uw aanvraag wordt gegeven.

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

Hiermee geeft u een waarde op voor de HTTP-antwoordheader voor overdrachtcoderen. De aanvaardbare waarden voor deze parameter zijn:

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

Hiermee geeft u de Uniform Resource Identifier (URI) op van de internetresource waar de webaanvraag naar wordt verzonden. Deze parameter ondersteunt de waarden HTTP, HTTPS, FTP en FILE.

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

Geeft aan dat de cmdlet basisparsering gebruikt. De cmdlet retourneert de onbewerkte HTML in een **tekenreeksobject.**

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

### -UserAgent

Hiermee geeft u een tekenreeks voor de gebruikersagent op voor de webaanvraag.

De standaardgebruikersagent is vergelijkbaar met Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0" met kleine variaties voor elk besturingssysteem en platform.

Als u een website wilt testen met de standaard gebruikersagentreeks die door de meeste internetbrowsers wordt gebruikt, gebruikt u de eigenschappen van de [klasse PSUserAgent,](/dotnet/api/microsoft.powershell.commands) zoals Chrome, FireFox, Internet Explorer, Opera en Safari.

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

Als u een waarde in de webaanvraagsessie wilt overschrijven, gebruikt u een cmdlet-parameter, zoals **UserAgent** of **Credential.** Parameterwaarden hebben voorrang op waarden in de webaanvraagsessie.

In tegenstelling tot een externe sessie is de webaanvraagsessie geen permanente verbinding. Het is een object dat informatie bevat over de verbinding en de aanvraag, inclusief cookies, referenties, de maximale omleidingswaarde en de tekenreeks van de gebruikersagent. U kunt deze gebruiken om de status en gegevens te delen tussen webaanvragen.

Als u een webaanvraagsessie wilt maken, voert u een variabelenaam (zonder dollarteken) in de waarde van de parameter **SessionVariable** van een `Invoke-RestMethod` opdracht in. `Invoke-RestMethod` maakt de sessie en slaat deze op in de variabele . In volgende opdrachten gebruikt u de variabele als de waarde van de parameter **WebSession.**

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

### System.Xml.XmlDocument, Microsoft.PowerShell.Commands.HtmlWebResponseObject, System.String

De uitvoer van de cmdlet is afhankelijk van de indeling van de inhoud die wordt opgehaald.

### PSObject

Als de aanvraag JSON-tekenreeksen retourneert, `Invoke-RestMethod` retourneert een PSObject dat de tekenreeksen vertegenwoordigt.

## Notities

## Verwante koppelingen

[ConvertTo-Json](ConvertTo-Json.md)

[ConvertFrom-Json](ConvertFrom-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)
