---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmaninstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManInstance
ms.openlocfilehash: 3f4ee9edf6e8dfce21a51ff9c055fe56a0cbef3c
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251570"
---
# Set-WSManInstance

## SAMENVATTING
Hiermee wijzigt u de beheer gegevens die zijn gerelateerd aan een resource.

## SYNTAXIS

### Computer naam (standaard)

```
Set-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-Dialect <Uri>] [-FilePath <String>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri>
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### URI

```
Set-WSManInstance [-ConnectionURI <Uri>] [-Dialect <Uri>] [-FilePath <String>] [-Fragment <String>]
 [-OptionSet <Hashtable>] [-ResourceURI] <Uri> [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-ValueSet <Hashtable>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet Set-WSManInstance worden de beheer gegevens van een resource gewijzigd.

Deze cmdlet maakt gebruik van de WinRM-verbinding/Trans Port-laag voor het wijzigen van de gegevens.

## VOORBEELDEN

### Voor beeld 1: een listener op de lokale computer uitschakelen

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.171, ::1, 2001:4898:0:fff:0:5efe:172.30.168.171...}
```

Met deze opdracht wordt de https-listener op de lokale computer uitgeschakeld.

Belang rijk: de *waardeset* -para meter is hoofdletter gevoelig bij het vergelijken van de opgegeven eigenschappen.

In deze opdracht bijvoorbeeld

Dit mislukt: `-ValueSet @{enabled="False"}`

Dit is geslaagd: `-ValueSet @{Enabled="False"}`

### Voor beeld 2: de maximale envelop grootte op de lokale computer instellen

```powershell
Set-WSManInstance -ResourceURI winrm/config -ValueSet @{MaxEnvelopeSizekb = "200"}
```

```Output
cfg                 : http://schemas.microsoft.com/wbem/wsman/1/config
lang                : en-US
MaxEnvelopeSizekb   : 200
MaxTimeoutms        : 60000
MaxBatchItems       : 32000
MaxProviderRequests : 4294967295
Client              : Client
Service             : Service
Winrs               : Winrs
```

Met deze opdracht wordt de waarde voor MaxEnvelopeSizekb ingesteld op 200 op de lokale computer.

Belang rijk: de waardeset-para meter is hoofdletter gevoelig bij het vergelijken van de opgegeven eigenschappen.

Gebruik bijvoorbeeld de bovenstaande opdracht.

Dit mislukt:-waardeset @ {MaxEnvelopeSizeKB = "200"}

Dit is het volgende:-values-waarde @ {MaxEnvelopeSizekb = "200"}

### Voor beeld 3: een listener op een externe computer uitschakelen

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -ComputerName SERVER02 -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.172, ::1, 2001:4898:0:fff:0:5efe:172.30.168.172...}
```

Met deze opdracht wordt de https-listener op de externe computer SERVER02 uitgeschakeld.

Belang rijk: de waardeset-para meter is hoofdletter gevoelig bij het vergelijken van de opgegeven eigenschappen.

Gebruik bijvoorbeeld de bovenstaande opdracht.

Dit mislukt:-values @ {enabled = "false"}

Dit is het volgende:-values-waarde @ {enabled = "false"}

## PARAMETERS

### -ApplicationName

Hiermee geeft u de naam van de toepassing in de verbinding.
De standaard waarde van de para meter ApplicationName is WSMAN.
De volledige id voor het externe eind punt heeft de volgende indeling:

\<transport\>://\<server\>:\<port\>/\<ApplicationName\>

Bijvoorbeeld:

`http://server01:8080/WSMAN`

Internet Information Services (IIS), die als host fungeert voor de sessie, stuurt aanvragen door met dit eind punt naar de opgegeven toepassing.
Deze standaard instelling van ' WSMAN ' is geschikt voor de meeste doel einden.
Deze para meter is ontworpen om te worden gebruikt wanneer talloze computers externe verbindingen tot stand brengen met één computer met Windows Power shell.
In dit geval wordt IIS gehost Web Services for Management (WS-Management) voor efficiëntie.

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: Wsman
Accept pipeline input: False
Accept wildcard characters: False
```

### -Verificatie

Hiermee geeft u het verificatie mechanisme op dat moet worden gebruikt op de server.
Mogelijke waarden zijn:

- Basic: Basic is een schema waarin de gebruikers naam en het wacht woord als niet-gecodeerde tekst naar de server of proxy worden verzonden.
- Standaard: gebruik de verificatie methode die wordt geïmplementeerd door het WS-Management-protocol. Dit is de standaardinstelling.
- Digest: Digest is een vraag/antwoord-schema dat gebruikmaakt van een door de server opgegeven gegevens reeks voor de uitdaging.
- Kerberos: de client computer en de server worden wederzijds geverifieerd met behulp van Kerberos-certificaten.
- Onderhandelen: onderhandelen is een vraag/antwoord-schema dat onderhandelt met de server of proxy om te bepalen welk schema moet worden gebruikt voor verificatie. Deze parameter waarde kan bijvoorbeeld onderhandelen om te bepalen of het Kerberos-protocol of NTLM wordt gebruikt.
- CredSSP: gebruik CredSSP-verificatie (Credential Security Support Provider) waarmee de gebruiker referenties kan delegeren. Deze optie is bedoeld voor opdrachten die op één externe computer worden uitgevoerd, maar die gegevens verzamelen van of extra opdrachten op andere externe computers worden uitgevoerd.

Let op: CredSSP delegeert de referenties van de gebruiker van de lokale computer naar een externe computer.
Deze procedure verhoogt het beveiligings risico van de externe bewerking.
Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.
Voer de vinger afdruk van het certificaat in.

Certificaten worden gebruikt in authenticatie op basis van client certificaten.
Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.

Als u een certificaat vingerafdruk wilt krijgen, gebruikt u de opdracht Get-Item of Get-ChildItem in het Power shell-certificaat: station.

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

### -ComputerName

Hiermee geeft u de computer op waartegen u de beheer bewerking wilt uitvoeren.
De waarde kan een Fully Qualified Domain Name, een NetBIOS-naam of een IP-adres zijn.
Gebruik de naam van de lokale computer, gebruik localhost of gebruik een punt (.) om de lokale computer op te geven.
De lokale computer is de standaard waarde.
Wanneer de externe computer zich in een ander domein van de gebruiker bevindt, moet u een Fully Qualified Domain Name gebruiken.
U kunt een waarde voor deze para meter door geven aan de cmdlet.

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: Named
Default value: Localhost
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionURI

Hiermee geeft u het eind punt van de verbinding.
De notatie van deze teken reeks is:

\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\>

De volgende teken reeks is een correct ingedeelde waarde voor deze para meter:

`http://Server01:8080/WSMAN`

De URI moet volledig gekwalificeerd zijn.

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.
Standaard is dit de huidige gebruiker.
Typ een gebruikers naam, zoals "gebruiker01", "Domain01\User01" of " User@Domain.com ".
U kunt ook een PSCredential-object invoeren, zoals het dat wordt geretourneerd door de cmdlet Get-Credential.
Wanneer u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases: cred, c

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Dialect

Hiermee geeft u het dialect op dat moet worden gebruikt in het filter predicaat.
Dit kan elk dialect zijn dat wordt ondersteund door de externe service.
De volgende aliassen kunnen worden gebruikt voor de dialect-URI:

- WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`
- Selector `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`
- Organisatie `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: http://schemas.microsoft.com/wbem/wsman/1/WQL
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Hiermee geeft u het pad op van een bestand dat wordt gebruikt om een beheer bron bij te werken.
U geeft de beheer bron op met behulp van de para meter ResourceURI en de para meter SelectorSet.
De volgende opdracht maakt bijvoorbeeld gebruik van de FilePath-para meter:

`Invoke-WSManAction -action StopService -resourceuri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:c:\input.xml -authentication default`

Met deze opdracht wordt de stop service-methode voor de spooler aangeroepen met behulp van invoer vanuit een bestand.
Het bestand, Input.xml, bevat de volgende inhoud:

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Fragment

Hiermee geeft u een sectie in het exemplaar op dat moet worden bijgewerkt of opgehaald voor de opgegeven bewerking.
Als u bijvoorbeeld de status van een Spooler-service wilt ophalen, geeft u '-fragment status ' op.

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

### -Optieset

Hiermee wordt een set switches door gegeven aan een service om de aard van de aanvraag te wijzigen of te verfijnen.
Deze zijn vergelijkbaar met de switches die worden gebruikt in opdracht regel shells, omdat deze service-specifiek zijn.
U kunt een wille keurig aantal opties opgeven.

In het volgende voor beeld ziet u de syntaxis waarmee de waarden 1, 2 en 3 worden door gegeven voor de para meters a, b en c:

-Optieset @ {a = 1; b = 2; c = 3}

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Hiermee geeft u de poort op die moet worden gebruikt wanneer de client verbinding maakt met de WinRM-service.
Wanneer het Trans Port HTTP is, is de standaard poort 80.
Wanneer het Trans Port HTTPS is, is de standaard poort 443.
Wanneer u HTTPS gebruikt als het Trans Port, moet de waarde van de para meter ComputerName overeenkomen met de common name (CN) van het server certificaat.
Als de para meter SkipCNCheck echter is opgegeven als onderdeel van de para meter SessionOption, moet de algemene naam van het certificaat van de server niet overeenkomen met de hostnaam van de server.
De para meter SkipCNCheck moet alleen worden gebruikt voor vertrouwde computers.

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

### -ResourceURI

Bevat de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar.
De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.

Een URI bestaat uit een voor voegsel en een pad naar een bron.
Bijvoorbeeld:

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: ruri

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SelectorSet

Hiermee geeft u een set waardeparen op die worden gebruikt om bepaalde beheer resource-instanties te selecteren.
De para meter SelectorSet wordt gebruikt wanneer er meer dan één exemplaar van de bron bestaat.
De waarde van de para meter SelectorSet moet een hash-tabel zijn.
In het volgende voor beeld ziet u hoe u een waarde voor deze para meter opgeeft:

-SelectorSet @ {name = "WinRM"; ID = "yyy"}

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

Hiermee definieert u een set uitgebreide opties voor de WS-Management sessie.
Voer een SessionOption-object in dat u maakt met behulp van de cmdlet New-WSManSessionOption.
Zie New-WSManSessionOption voor meer informatie over de beschik bare opties.

```yaml
Type: Microsoft.WSMan.Management.SessionOption
Parameter Sets: (All)
Aliases: so

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Hiermee geeft u op dat het SSL-protocol (Secure Sockets Layer) moet worden gebruikt om een verbinding met de externe computer tot stand te brengen.
Standaard wordt SSL niet gebruikt.

WS-Management versleutelt alle Windows Power shell-inhoud die via het netwerk wordt verzonden.
Met de para meter UseSSL kunt u de extra beveiliging van HTTPS in plaats van HTTP opgeven.
Als SSL niet beschikbaar is op de poort die voor de verbinding wordt gebruikt en u deze para meter opgeeft, mislukt de opdracht.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases: ssl

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Waardeset

Hiermee geeft u een hash-tabel op waarmee u een beheer bron kunt wijzigen.
U geeft de beheer bron op met behulp van de para meter ResourceURI en de para meter SelectorSet.
De waarde van de para meter voor de waardeset moet een hash-tabel zijn.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### Geen

Deze cmdlet accepteert geen invoer.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Verbinding verbreken-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Testen-WSMan](Test-WSMan.md)
