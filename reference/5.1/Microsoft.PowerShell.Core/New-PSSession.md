---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSession
ms.openlocfilehash: 1835d0bd4294161f83728a63e8da8fc64c2bf9e0
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251481"
---
# New-PSSession

## SAMENVATTING
Hiermee maakt u een permanente verbinding met een lokale of externe computer.

## SYNTAXIS

### Computer naam (standaard)

```
New-PSSession [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Name <String[]>]
 [-EnableNetworkAccess] [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### URI

```
New-PSSession [-Credential <PSCredential>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### VMId

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 [-VMId] <Guid[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### VMName

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 -VMName <String[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### Sessie

```
New-PSSession [[-Session] <PSSession[]>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### ContainerId

```
New-PSSession [-Name <String[]>] [-ConfigurationName <String>] -ContainerId <String[]>
 [-RunAsAdministrator] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

## BESCHRIJVING

`New-PSSession`Met de cmdlet maakt u een Power shell-sessie ( **PSSession** ) op een lokale of externe computer. Wanneer u een **PSSession** maakt, brengt Power shell een permanente verbinding met de externe computer tot stand.

Gebruik een **PSSession** om meerdere opdrachten uit te voeren die gegevens delen, zoals een functie of de waarde van een variabele. Gebruik de cmdlet om opdrachten uit te voeren in een **PSSession** `Invoke-Command` . Als u de **PSSession** wilt gebruiken om rechtstreeks te communiceren met een externe computer, gebruikt u de `Enter-PSSession` cmdlet. Zie [about_PSSessions](about/about_PSSessions.md)voor meer informatie.

U kunt opdrachten uitvoeren op een externe computer zonder een **PSSession** te maken met behulp van de **ComputerName** -para meters van `Enter-PSSession` of `Invoke-Command` . Wanneer u de para meter **ComputerName** gebruikt, maakt Power shell een tijdelijke verbinding die wordt gebruikt voor de opdracht en vervolgens gesloten.

## VOORBEELDEN

### Voor beeld 1: een sessie op de lokale computer maken

```powershell
$s = New-PSSession
```

Met deze opdracht maakt u een nieuwe **PSSession** op de lokale computer en slaat de **PSSession** op in de `$s` variabele.

U kunt deze **PSSession** nu gebruiken om opdrachten uit te voeren op de lokale computer.

### Voor beeld 2: een sessie op een externe computer maken

```powershell
$Server01 = New-PSSession -ComputerName Server01
```

Met deze opdracht maakt u een nieuwe **PSSession** op de Server01-computer en slaat deze op in de `$Server01` variabele.

Wanneer u meerdere **PSSession** -objecten maakt, moet u deze toewijzen aan variabelen met nuttige namen. Dit helpt u bij het beheren van de **PSSession** -objecten in volgende opdrachten.

### Voor beeld 3: sessies op meerdere computers maken

```powershell
$s1, $s2, $s3 = New-PSSession -ComputerName Server01,Server02,Server03
```

Met deze opdracht worden drie **PSSession** -objecten gemaakt, één op elke computer die is opgegeven door de para meter **ComputerName** .

De opdracht gebruikt de toewijzings operator (=) om de nieuwe **PSSession** -objecten toe te wijzen aan variabelen: `$s1` , `$s2` , `$s3` . De Server01 **PSSession** wordt toegewezen aan `$s1` , de Server02 **PSSession** aan `$s2` en de Server03 **PSSession** tot `$s3` .

Wanneer u meerdere objecten toewijst aan een reeks variabelen, wijst Power shell elk object toe aan een variabele in de reeks. Als er meer objecten zijn dan variabelen, worden alle resterende objecten toegewezen aan de laatste variabele. Als er meer variabelen zijn dan objecten, zijn de resterende variabelen leeg (null).

### Voor beeld 4: een sessie met een opgegeven poort maken

```powershell
New-PSSession -ComputerName Server01 -Port 8081 -UseSSL -ConfigurationName E12
```

Met deze opdracht maakt u een nieuwe **PSSession** op de Server01-computer die verbinding maakt met server poort 8081 en gebruikmaakt van het SSL-protocol. De nieuwe **PSSession** gebruikt een alternatieve sessie configuratie met de naam E12.

Voordat u de poort instelt, moet u de WinRM-listener op de externe computer configureren om te Luis teren op poort 8081. Zie de beschrijving van de **poort** parameter voor meer informatie.

### Voor beeld 5: een sessie maken op basis van een bestaande sessie

```powershell
New-PSSession -Session $s -Credential Domain01\User01
```

Met deze opdracht maakt u een **PSSession** met dezelfde eigenschappen als een bestaande **PSSession**. U kunt deze opdracht indeling gebruiken wanneer de resources van een bestaand **PSSession** uitgeput zijn en er een nieuwe **PSSession** nodig is om een deel van de vraag te offloaden.

De opdracht gebruikt de **sessie** parameter van `New-PSSession` om de **PSSession** op te geven die is opgeslagen in de `$s` variabele. Het gebruikt de referenties van de Domain1\Admin01-gebruiker om de opdracht te volt ooien.

### Voor beeld 6: een sessie met een globaal bereik in een ander domein maken

```powershell
$global:s = New-PSSession -ComputerName Server1.Domain44.Corpnet.Fabrikam.com -Credential Domain01\Admin01
```

In dit voor beeld ziet u hoe u een **PSSession** maakt met een globaal bereik op een computer in een ander domein.

**PSSession** -objecten die zijn gemaakt op de opdracht regel, worden standaard gemaakt met een lokale scope en **PSSession** -objecten die zijn gemaakt in een script, hebben een script bereik.

Als u een **PSSession** met een globaal bereik wilt maken, maakt u een nieuwe **PSSession** en slaat u vervolgens de **PSSession** op in een variabele die wordt geconverteerd naar een globaal bereik. In dit geval wordt de `$s` variabele geconverteerd naar een globaal bereik.

De opdracht gebruikt de para meter **ComputerName** om de externe computer op te geven. Omdat de computer zich in een ander domein bevindt dan het gebruikers account, wordt de volledige naam van de computer opgegeven samen met de referenties van de gebruiker.

### Voor beeld 7: sessies maken voor veel computers

```powershell
$rs = Get-Content C:\Test\Servers.txt | New-PSSession -ThrottleLimit 50
```

Met deze opdracht maakt u een **PSSession** op elk van de 200-computers die worden vermeld in het Servers.txt-bestand en wordt de resulterende **PSSession** in de `$rs` variabele opgeslagen. De **PSSession** -objecten hebben een beperkings limiet van 50.

U kunt deze opdracht indeling gebruiken wanneer de namen van computers worden opgeslagen in een Data Base, een werk blad, een tekst bestand of een andere Converteer bare tekst indeling.

### Voor beeld 8: een sessie maken met behulp van een URI

```powershell
$s = New-PSSession -URI http://Server01:91/NewSession -Credential Domain01\User01
```

Met deze opdracht maakt u een **PSSession** op de Server01-computer en slaat u deze op in de `$s` variabele. De para meter **URI** wordt gebruikt om het transport protocol, de externe computer, de poort en een alternatieve sessie configuratie op te geven. Ook wordt de para meter **Credential** gebruikt om een gebruikers account op te geven dat gemachtigd is om een sessie te maken op de externe computer.

### Voor beeld 9: een achtergrond taak uitvoeren in een reeks sessies

```powershell
$s = New-PSSession -ComputerName (Get-Content Servers.txt) -Credential Domain01\Admin01 -ThrottleLimit 16
Invoke-Command -Session $s -ScriptBlock {Get-Process PowerShell} -AsJob
```

Met deze opdrachten maakt u een set **PSSession** -objecten en voert u vervolgens een achtergrond taak uit in elk van de **PSSession** -objecten.

Met de eerste opdracht maakt u een nieuwe **PSSession** op elke computer die wordt vermeld in het Servers.txt-bestand. De cmdlet wordt gebruikt `New-PSSession` om de **PSSession** te maken. De waarde van de para meter **ComputerName** is een opdracht die gebruikmaakt `Get-Content` van de cmdlet om de lijst met computer namen op te halen in het Servers.txt-bestand.

De opdracht gebruikt de para meter **Credential** om de **PSSession** -objecten te maken die de machtiging van een domein beheerder hebben en de para meter **ThrottleLimit** wordt gebruikt om de opdracht te beperken tot 16 gelijktijdige verbindingen. Met de opdracht worden de **PSSession** -objecten in de `$s` variabele opgeslagen.

De tweede opdracht maakt gebruik van de para meter **AsJob** van de `Invoke-Command` cmdlet om een achtergrond taak te starten die een `Get-Process PowerShell` opdracht uitvoert in elk van de **PSSession** -objecten in `$s` .

Zie [about_Jobs](About/about_Jobs.md) en [about_Remote_Jobs](About/about_Remote_Jobs.md)voor meer informatie over Power shell-achtergrond taken.

### Voor beeld 10: een sessie maken voor een computer met behulp van de bijbehorende URI

```powershell
New-PSSession -ConnectionURI https://management.exchangelabs.com/Management
```

Met deze opdracht maakt u een **PSSession** -object dat verbinding maakt met een computer die is opgegeven met een URI in plaats van een computer naam.

### Voor beeld 11: een sessie optie maken

```powershell
$so = New-PSSessionOption -SkipCACheck
New-PSSession -ConnectionUri https://management.exchangelabs.com/Management -SessionOption $so -Credential Server01\Admin01
```

In dit voor beeld ziet u hoe u een sessie optie object maakt en hoe u de para meter **SessionOption** .

De eerste opdracht gebruikt de `New-PSSessionOption` cmdlet om een sessie optie te maken. Hiermee wordt het resulterende **SessionOption** -object in de `$so` variabele opgeslagen.

Met de tweede opdracht wordt de optie in een nieuwe sessie gebruikt. De opdracht gebruikt de `New-PSSession` cmdlet om een nieuwe sessie te maken. De waarde van de para meter SessionOption is het object **SessionOption** in de `$so` variabele.

## PARAMETERS

### -AllowRedirection

Geeft aan dat deze cmdlet omleiding van deze verbinding met een alternatieve URI (Uniform Resource Identifier) mogelijk maakt.

Wanneer u de para meter **ConnectionURI** gebruikt, kan de externe bestemming een instructie retour neren die wordt omgeleid naar een andere URI. Standaard worden verbindingen niet door Power shell omgeleid, maar u kunt deze para meter gebruiken om de verbinding te omleiden.

U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de waarde van de **MaximumConnectionRedirectionCount** -sessie optie te wijzigen. Gebruik de para meter **MaximumRedirection** van de `New-PSSessionOption` cmdlet of stel de eigenschap **MaximumConnectionRedirectionCount** van de voorkeurs variabele **$PSSessionOption** in. De standaard waarde is 5.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

Hiermee geeft u het segment van de toepassings naam van de verbindings-URI op. Gebruik deze para meter om de naam van de toepassing op te geven wanneer u de para meter **ConnectionURI** niet gebruikt in de opdracht.

De standaard waarde is de waarde van de `$PSSessionApplicationName` Voorkeurs variabele op de lokale computer. Als deze voorkeurs variabele niet is gedefinieerd, is de standaard waarde WSMAN. Deze waarde is geschikt voor de meeste toepassingen. Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie.

De WinRM-service gebruikt de naam van de toepassing om een listener te selecteren om de verbindings aanvraag te onderhouden.
De waarde van deze para meter moet overeenkomen met de waarde van de eigenschap **URLPrefix** van een listener op de externe computer.

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Verificatie

Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren.
De aanvaardbare waarden voor deze parameter zijn:

- Standaard
- Basic
- CredSSP
- Samenvatting
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

De standaard waarde is standaard.

Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.

> [!CAUTION]
> CredSSP-verificatie (Credential Security Support Provider), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share. Dit mechanisme verhoogt het beveiligings risico van de externe bewerking. Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren. Voer de vinger afdruk van het certificaat in.

Certificaten worden gebruikt in authenticatie op basis van client certificaten. Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.

Als u een certificaat wilt ophalen, gebruikt u de `Get-Item` of- `Get-ChildItem` opdracht in het Power shell-certificaat: station.

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u een matrix met namen van computers op. Met deze cmdlet wordt een permanente verbinding ( **PSSession** ) gemaakt met de opgegeven computer. Als u meerdere computer namen opgeeft, `New-PSSession` maakt meerdere **PSSession** -objecten, één voor elke computer. Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een of meer externe computers. Typ de computer naam, localhost of een punt (.) om de lokale computer op te geven. Wanneer de computer zich in een ander domein bevindt dan de gebruiker, is de Fully Qualified Domain Name vereist. U kunt ook een computer naam (tussen aanhalings tekens) door sluizen naar `New-PSSession` .

Als u een IP-adres wilt gebruiken in de waarde van de para meter **ComputerName** , moet de opdracht de para meter **Credential** bevatten. De computer moet ook worden geconfigureerd voor HTTPS-Trans Port of het IP-adres van de externe computer moet worden opgenomen in de WinRM TrustedHosts-lijst op de lokale computer. Zie "een computer toevoegen aan de lijst met vertrouwde hosts" in [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md)voor instructies voor het toevoegen van een computer naam aan de lijst TrustedHosts.

Als u de lokale computer in de waarde van de para meter **ComputerName** wilt gebruiken, start u Windows Power shell met de optie als administrator uitvoeren.

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Configuratiepad

Hiermee geeft u de sessie configuratie op die wordt gebruikt voor de nieuwe **PSSession**.

Voer een configuratie naam of de volledig gekwalificeerde resource-URI in voor een sessie configuratie. Als u alleen de configuratie naam opgeeft, wordt de volgende schema-URI voor voegsel: `http://schemas.microsoft.com/PowerShell` .

De sessie configuratie voor een sessie bevindt zich op de externe computer. Als de opgegeven sessie configuratie niet bestaat op de externe computer, mislukt de opdracht.

De standaard waarde is de waarde van de `$PSSessionConfigurationName` Voorkeurs variabele op de lokale computer. Als deze voorkeurs variabele niet is ingesteld, is de standaard instelling micro soft. Power shell. Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie.

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

Hiermee geeft u een URI op die het verbindings eindpunt voor de sessie definieert. De URI moet volledig gekwalificeerd zijn. De indeling van deze teken reeks is als volgt:

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

De standaard waarde is als volgt:

`http://localhost:5985/WSMAN`

Als u geen **ConnectionURI** opgeeft, kunt u de para meters **UseSSL** , **ComputerName** , **Port** en **ApplicationName** gebruiken om de **ConnectionURI** -waarden op te geven.

Geldige waarden voor het transport segment van de URI zijn HTTP en HTTPS. Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met standaard poorten: 80 voor HTTP en 443 voor HTTPS. Als u de standaard poorten voor externe communicatie van Power shell wilt gebruiken, geeft u poort 5985 voor HTTP of 5986 op voor HTTPS.

Als de doel computer de verbinding omleidt naar een andere URI, wordt de omleiding door Power shell voor komen, tenzij u de para meter **AllowRedirection** in de opdracht gebruikt.

```yaml
Type: System.Uri[]
Parameter Sets: Uri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

Hiermee geeft u een matrix met Id's van containers op. Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven containers. Gebruik de `docker ps` opdracht om een lijst met container-id's op te halen. Zie de Help voor de opdracht [docker PS](https://docs.docker.com/engine/reference/commandline/ps/) voor meer informatie.

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat gemachtigd is om deze actie uit te voeren. Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` . Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.

Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

Geeft aan dat met deze cmdlet een interactief beveiligings token wordt toegevoegd aan loop Back-sessies. Met het interactieve token kunt u opdrachten uitvoeren in de loop back-sessie die gegevens van andere computers ophalen. U kunt bijvoorbeeld een opdracht uitvoeren in de sessie waarmee XML-bestanden van een externe computer naar de lokale computer worden gekopieerd.

Een loop back-sessie is een **PSSession** die afkomstig is van en eindigt op dezelfde computer. Als u een loop back-sessie wilt maken, laat u de para meter **ComputerName** weg of stelt u de waarde in op punt (.), localhost of de naam van de lokale computer.

Met deze cmdlet worden standaard loop Back-sessies gemaakt met behulp van een netwerk token, dat mogelijk niet voldoende machtigingen biedt om te verifiëren bij externe computers.

De para meter **EnableNetworkAccess** is alleen effectief in loop Back-sessies. Als u **EnableNetworkAccess** gebruikt wanneer u een sessie op een externe computer maakt, mislukt de opdracht, maar wordt de para meter genegeerd.

U kunt ook externe toegang inschakelen in een loop back-sessie met behulp van de CredSSP-waarde van de para meter **Authentication** , waarmee de sessie referenties worden overgedragen aan andere computers.

Om de computer te beschermen tegen kwaad aardige toegang, kunnen niet-verbonden loop Back-sessies met interactieve tokens, die zijn gemaakt met behulp van de para meter **EnableNetworkAccess** , alleen opnieuw worden aangesloten op de computer waarop de sessie is gemaakt. Verbroken sessies die gebruikmaken van CredSSP-verificatie, kunnen opnieuw worden aangesloten op andere computers. Voor meer informatie raadpleegt u `Disconnect-PSSession`.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri, Session
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een beschrijvende naam op voor de **PSSession**.

U kunt de naam gebruiken om te verwijzen naar de **PSSession** wanneer u andere cmdlets gebruikt, zoals `Get-PSSession` en `Enter-PSSession` . De naam hoeft niet uniek te zijn voor de computer of de huidige sessie.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Hiermee geeft u de netwerk poort op de externe computer op die voor deze verbinding wordt gebruikt. Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt. De standaard poorten zijn 5985, de WinRM-poort voor HTTP en 5986, de WinRM-poort voor HTTPS.

Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren. Gebruik de volgende opdrachten om de listener te configureren:

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

Gebruik de para meter **poort** alleen als dat nodig is. De poort instelling in de opdracht is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd. Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.

```yaml
Type: System.Int32
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsAdministrator

Geeft aan dat de **PSSession** wordt uitgevoerd als beheerder.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sessie

Hiermee geeft u een matrix met **PSSession** -objecten op die met deze cmdlet als model voor de nieuwe **PSSession** wordt gebruikt. Met deze para meter maakt u nieuwe **PSSession** -objecten die dezelfde eigenschappen hebben als de opgegeven **PSSession** -objecten.

Voer een variabele in die de **PSSession** -objecten bevat of een opdracht waarmee de **PSSession** -objecten, zoals een of-opdracht, worden gemaakt of opgehaald `New-PSSession` `Get-PSSession` .

De resulterende **PSSession** -objecten hebben dezelfde computer naam, toepassings naam, VERBINDINGS-URI, poort, configuratie naam, beperkings limiet en Secure Sockets Layer (SSL) als de oorspronkelijke waarden, maar ze hebben een andere weergave naam, id en exemplaar-id (GUID).

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

Hiermee geeft u geavanceerde opties voor de sessie op. Voer een **SessionOption** -object in, zoals het, dat u maakt met behulp van de `New-PSSessionOption` cmdlet of een hash-tabel waarin de sleutels de naam van de sessie optie zijn en de waarden voor de waarden van de sessie.

De standaard waarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld. Anders worden de standaard waarden bepaald door opties die zijn ingesteld in de sessie configuratie.

De waarden van de sessie optie hebben voor rang op de standaard waarden voor sessies die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en in de sessie configuratie. Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie.

Zie voor een beschrijving van de sessie opties die de standaard waarden bevatten `New-PSSessionOption` . Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` voorkeurs [about_Preference_Variables](About/about_Preference_Variables.md)variabele. Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.
Als u deze para meter weglaat of een waarde van 0 (nul) opgeeft, wordt de standaard waarde 32 gebruikt.

De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.

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

### -UseSSL

Geeft aan dat deze cmdlet het SSL-protocol gebruikt om verbinding te maken met de externe computer.
Standaard wordt SSL niet gebruikt.

WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden. De para meter **UseSSL** biedt een extra beveiliging voor het verzenden van de gegevens via een HTTPS-verbinding in plaats van een http-verbinding.

Als u deze para meter gebruikt, maar SSL is niet beschikbaar op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

Hiermee geeft u een ID-matrix van virtuele machines op. Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines. Als u de virtuele machines wilt zien die voor u beschikbaar zijn, gebruikt u de volgende opdracht:

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

Hiermee geeft u een matrix met namen van virtuele machines op. Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines. Gebruik de cmdlet om de virtuele machines weer te geven die voor u beschikbaar zijn `Get-VM` .

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie about_CommonParameters (voor meer informatie https://go.microsoft.com/fwlink/?LinkID=113216) .

## INVOER

### System. String, System. URI, System. Management. Automation. Runspaces. PSSession

U kunt een teken reeks, URI of sessie object door sluizen naar deze cmdlet.

## UITVOER

### System. Management. Automation. Runspaces. PSSession

## OPMERKINGEN

- Deze cmdlet maakt gebruik van de externe infra structuur van Power shell. Als u deze cmdlet wilt gebruiken, moeten de lokale computer en alle externe computers worden geconfigureerd voor externe communicatie met Power shell. Zie [about_Remote_Requirements](About/about_Remote_Requirements.md)voor meer informatie.
- Als u een **PSSession** op de lokale computer wilt maken, start u Power shell met de optie als administrator uitvoeren.
- Wanneer u klaar bent met de **PSSession** , gebruikt u de `Remove-PSSession` cmdlet om de **PSSession** te verwijderen en de bijbehorende resources vrij te geven.

## GERELATEERDE KOPPELINGEN

[Connect-PSSession](Connect-PSSession.md)

[Verbinding verbreken-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Afsluiten-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-opdracht](Invoke-Command.md)

[Receive-PSSession](Receive-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)
