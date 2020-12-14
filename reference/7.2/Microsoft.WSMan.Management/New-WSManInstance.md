---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 03/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmaninstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManInstance
ms.openlocfilehash: dd0343e9b6014e079c322309b699874683bacd6a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704718"
---
# New-WSManInstance

## SAMENVATTING
Hiermee maakt u een nieuw exemplaar van een beheer bron.

## SYNTAXIS

### Computer naam (standaard)

```
New-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable>
 [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### URI

```
New-WSManInstance [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## BESCHRIJVING

De `New-WSManInstance` cmdlet maakt een nieuw exemplaar van een beheer bron. Het maakt gebruik van een resource-URI en een ingestelde waarde of invoer bestand om het nieuwe exemplaar van de beheer bron te maken.

Deze cmdlet maakt gebruik van de WinRM-verbinding/Trans Port-laag voor het maken van het beheer resource-exemplaar.

## VOORBEELDEN

### Voor beeld 1: een HTTPS-listener maken

Met deze opdracht maakt u een exemplaar van een WS-Management HTTPS-listener op alle IP-adressen.

```powershell
New-WSManInstance winrm/config/Listener -SelectorSet @{Transport='HTTPS'; Address='*'} -ValueSet @{Hostname="HOST";CertificateThumbprint="XXXXXXXXXX"}
```

## PARAMETERS

### -ApplicationName

Hiermee geeft u de naam van de toepassing in de verbinding. De standaard waarde van de para meter **ApplicationName** is **WSMAN**. De volledige id voor het externe eind punt heeft de volgende indeling:

`<transport>://<server>:<port>/<ApplicationName>`

Bijvoorbeeld:

`http://server01:8080/WSMAN`

Internet Information Services (IIS), die als host fungeert voor de sessie, stuurt aanvragen door met dit eind punt naar de opgegeven toepassing. Deze standaard instelling van **WSMAN** is geschikt voor de meeste toepassingen. Deze para meter is ontworpen om te worden gebruikt wanneer talloze computers externe verbindingen tot stand brengen met één computer met Windows Power shell. In dit geval wordt IIS gehost Web Services for Management (WS-Management) voor efficiëntie.

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

Hiermee geeft u het verificatie mechanisme op dat moet worden gebruikt op de server. Mogelijke waarden zijn:

- Basic: Basic is een schema waarin de gebruikers naam en het wacht woord als niet-gecodeerde tekst naar de server of proxy worden verzonden.
- Standaard: gebruik de verificatie methode die wordt geïmplementeerd door het WS-Management-protocol. Dit is de standaardinstelling.
- Digest: Digest is een vraag/antwoord-schema dat gebruikmaakt van een door de server opgegeven gegevens reeks voor de uitdaging.
- Kerberos: de client computer en de server worden wederzijds geverifieerd met Kerberos-certificaten.
- Onderhandelen: onderhandelen is een vraag/antwoord-schema dat onderhandelt met de server of proxy om te bepalen welk schema moet worden gebruikt voor verificatie. Deze parameter waarde kan bijvoorbeeld onderhandelen om te bepalen of het Kerberos-protocol of NTLM wordt gebruikt.
- CredSSP: gebruik CredSSP-verificatie (Credential Security Support Provider) waarmee de gebruiker referenties kan delegeren. Deze optie is bedoeld voor opdrachten die op één externe computer worden uitgevoerd, maar die gegevens verzamelen van of extra opdrachten op andere externe computers worden uitgevoerd.

> [!CAUTION]
> CredSSP delegeert de referenties van de gebruiker van de lokale computer naar een externe computer. Deze procedure verhoogt het beveiligings risico van de externe bewerking. Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am
Accepted values: None, Default, Digest, Negotiate, Basic, Kerberos, ClientCertificate, Credssp

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren. Voer de vinger afdruk van het certificaat in.

Certificaten worden gebruikt in authenticatie op basis van client certificaten. Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.

Als u een certificaat vingerafdruk wilt ophalen, gebruikt u de `Get-Item` of- `Get-ChildItem` opdracht in het Power shell-certificaat: station.

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

Hiermee geeft u de computer op waartegen u de beheer bewerking wilt uitvoeren. De waarde kan een Fully Qualified Domain Name, een NetBIOS-naam of een IP-adres zijn. Gebruik de naam van de lokale computer, gebruik localhost of gebruik een punt ( `.` ) om de lokale computer op te geven. De lokale computer is de standaard waarde. Wanneer de externe computer zich in een ander domein van de gebruiker bevindt, moet u een Fully Qualified Domain Name gebruiken. U kunt een waarde voor deze para meter door geven aan de cmdlet.

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

`<Transport>://<Server>:<Port>/<ApplicationName>`

De volgende teken reeks is een correct ingedeelde waarde voor deze para meter:

`http://Server01:8080/WSMAN`

De URI moet volledig gekwalificeerd zijn.

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases: CURI, CU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren. Standaard is dit de huidige gebruiker. Typ een gebruikers naam, zoals "gebruiker01", "Domain01\User01" of " User@Domain.com ". U kunt ook een PSCredential-object invoeren, zoals het item dat door de cmdlet wordt geretourneerd `Get-Credential` . Wanneer u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.

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

### -FilePath

Hiermee geeft u het pad op van een bestand dat wordt gebruikt om een beheer bron te maken. U geeft de beheer resource op met behulp van de para meter **ResourceURI** en de para meter **SelectorSet** . Met de volgende opdracht wordt bijvoorbeeld de **File** -para meter gebruikt:

`Invoke-WSManAction -Action stopservice -ResourceUri wmi/cimv2/Win32_Service -SelectorSet @{Name="spooler"} -File c:\input.xml -Authentication Default`

Met deze opdracht wordt de **Stop** service-methode voor de spoolerservice aangeroepen met behulp van invoer uit een bestand. Het bestand, `Input.xml` , bevat de volgende inhoud:

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Optieset

Hiermee wordt een set switches door gegeven aan een service om de aard van de aanvraag te wijzigen of te verfijnen. Deze zijn vergelijkbaar met de switches die worden gebruikt in opdracht regel shells, omdat deze service-specifiek zijn. U kunt een wille keurig aantal opties opgeven.

In het volgende voor beeld ziet u de syntaxis waarmee de waarden 1, 2 en 3 worden door gegeven voor de para meters a, b en c:

`-OptionSet @{a=1;b=2;c=3}`

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

Hiermee geeft u de poort op die moet worden gebruikt wanneer de client verbinding maakt met de WinRM-service. Wanneer het Trans Port HTTP is, is de standaard poort 80. Wanneer het Trans Port HTTPS is, is de standaard poort 443.

Wanneer u HTTPS gebruikt als het Trans Port, moet de waarde van de para meter **ComputerName** overeenkomen met de common name (CN) van het server certificaat. Als de para meter **SkipCNCheck** echter is opgegeven als onderdeel van de **SessionOption** -para meter, moet de algemene naam van het certificaat van de server niet overeenkomen met de hostnaam van de server. De para meter **SkipCNCheck** moet alleen worden gebruikt voor vertrouwde computers.

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

Bevat de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar. De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.

Een URI bestaat uit een voor voegsel en een pad naar een bron. Bijvoorbeeld:

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

Hiermee geeft u een set waardeparen op die worden gebruikt om bepaalde beheer resource-instanties te selecteren. De para meter **SelectorSet** wordt gebruikt wanneer er meer dan één exemplaar van de bron bestaat. De waarde van de para meter **SelectorSet** moet een hash-tabel zijn.

In het volgende voor beeld ziet u hoe u een waarde voor deze para meter opgeeft:

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -SessionOption

Hiermee definieert u een set uitgebreide opties voor de WS-Management sessie. Voer een **SessionOption** -object in dat u maakt met behulp van de `New-WSManSessionOption` cmdlet. Zie voor meer informatie over de beschik bare opties `New-WSManSessionOption` .

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

Hiermee geeft u op dat het SSL-protocol (Secure Sockets Layer) moet worden gebruikt om een verbinding met de externe computer tot stand te brengen. Standaard wordt SSL niet gebruikt.

WS-Management versleutelt alle Windows Power shell-inhoud die via het netwerk wordt verzonden. Met de para meter **UseSSL** kunt u de extra beveiliging van https in plaats van http opgeven. Als SSL niet beschikbaar is op de poort die voor de verbinding wordt gebruikt en u deze para meter opgeeft, mislukt de opdracht.

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

### -Waardeset

Hiermee geeft u een hash-tabel op waarmee u een beheer bron kunt wijzigen. U geeft de beheer resource op met behulp van de para meter **ResourceURI** en de para meter **SelectorSet** . De waarde van de para meter voor de **waardeset** moet een hash-tabel zijn.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

De `Set-WmiInstance` cmdlet, een Windows Management Instrumentation-cmdlet (WMI), is vergelijkbaar.
`Set-WmiInstance` maakt gebruik van de DCOM-verbinding/Trans Port-laag voor het maken of bijwerken van WMI-exemplaren.

## GERELATEERDE KOPPELINGEN

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Verbinding verbreken-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Testen-WSMan](Test-WSMan.md)

