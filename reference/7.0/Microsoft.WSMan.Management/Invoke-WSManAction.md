---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/invoke-wsmanaction?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WSManAction
ms.openlocfilehash: 18ca64912df0e6b672bd05358aa806f639a590e7
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251526"
---
# Invoke-WSManAction

## SAMENVATTING
Hiermee wordt een actie aangeroepen voor het object dat is opgegeven door de resource-URI en de selecters.

## SYNTAXIS

### URI (standaard)

```
Invoke-WSManAction [-Action] <String> [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>]
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-ValueSet <Hashtable>] [-ResourceURI] <Uri>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### ComputerName

```
Invoke-WSManAction [-Action] <String> [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-UseSSL] [-ValueSet <Hashtable>] [-ResourceURI] <Uri> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## BESCHRIJVING
De **invoke-WSManAction** voert een actie uit op het object dat is opgegeven door RESOURCE_URI, waarbij de para meters worden opgegeven door sleutel waardeparen.

Deze cmdlet maakt gebruik van de WSMan-verbinding/transportlaag om de actie uit te voeren.

## VOORBEELDEN

### Voor beeld 1: een methode aanroepen

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

Met deze opdracht wordt de methode **Start service** aangeroepen van de Win32_Service WMI-klasse-instantie die overeenkomt met de Spooler-service.

De geretourneerde waarde geeft aan of de actie is geslaagd.
In dit geval geeft een geretourneerde waarde van 0 aan dat dit is geslaagd.
Een retour waarde van 5 geeft aan dat de service al is gestart.

### Voor beeld 2: een methode aanroepen

```powershell
Invoke-WSManAction -Action stopservice -ResourceURI wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:input.xml -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

Met deze opdracht wordt de **Stop** service-methode voor de spooler aangeroepen met behulp van invoer vanuit een bestand.
Het bestand, Input.xml, bevat de volgende inhoud:

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

### Voor beeld 3: een methode met opgegeven parameter waarden aanroepen

```powershell
Invoke-WSManAction -Action create -ResourceURI wmicimv2/win32_process -ValueSet @{commandline="notepad.exe";currentdirectory="C:\"}
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Process
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ProcessId   : 6356
ReturnValue : 0
```

Met deze opdracht wordt de methode **Create** van de klasse Win32_Process aangeroepen.
Er worden twee parameter waarden voor de methode, Notepad.exe en C:\., door gegeven
Als gevolg hiervan wordt een nieuw proces gemaakt voor het uitvoeren van Klad blok en de huidige map van het nieuwe proces is ingesteld op C:\.

### Voor beeld 4: een methode aanroepen op een externe computer

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -ComputerName server01 -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

Met deze opdracht wordt de methode **Start service** aangeroepen van de Win32_Service WMI-klasse-instantie die overeenkomt met de Spooler-service.
Omdat de para meter *ComputerName* is opgegeven, wordt de opdracht uitgevoerd op de externe Server01-computer.

## PARAMETERS

### -Actie
Hiermee geeft u de methode op die moet worden uitgevoerd op het beheer object dat is opgegeven door de ResourceURI en selecters.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName
Hiermee geeft u de naam van de toepassing in de verbinding.
De standaard waarde van de para meter *ApplicationName* is WSMAN.
De volledige id voor het externe eind punt heeft de volgende indeling:

\<transport\>://\<server\>:\<port\>/\<ApplicationName\>

Bijvoorbeeld: `http://server01:8080/WSMAN`

Internet Information Services (IIS), die als host fungeert voor de sessie, stuurt aanvragen door met dit eind punt naar de opgegeven toepassing.
Deze standaard instelling van WSMAN is geschikt voor de meeste toepassingen.
Deze para meter is ontworpen om te worden gebruikt als veel computers externe verbindingen tot stand brengen met één computer waarop Power shell wordt uitgevoerd.
In dit geval wordt IIS gehost Web Services for Management (WS-Management) voor efficiëntie.

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Verificatie
Hiermee geeft u het verificatie mechanisme op dat moet worden gebruikt op de server.
De aanvaardbare waarden voor deze parameter zijn:

- Hoofd.
Basic is een schema waarin de gebruikers naam en het wacht woord als niet-gecodeerde tekst naar de server of proxy worden verzonden.
- Standaard.
Gebruik de verificatie methode die wordt geïmplementeerd door het WS-Management-protocol.
Dit is de standaardinstelling.
- Vatting.
Digest is een vraag/antwoord-schema dat gebruikmaakt van een door de server opgegeven gegevens reeks voor de uitdaging.
- Kerberos.
De client computer en de server worden wederzijds geverifieerd met behulp van Kerberos-certificaten.
- Afspraken.
Onderhandelen is een vraag/antwoord-schema waarmee wordt onderhandeld over de server of proxy om te bepalen welk schema moet worden gebruikt voor verificatie.
Met deze parameter waarde kan bijvoorbeeld worden geonderhandelingd om te bepalen of het Kerberos-protocol of NTLM wordt gebruikt.
- CredSSP.
Gebruik CredSSP-verificatie (Credential Security Support Provider) waarmee de gebruiker referenties kan delegeren.
Deze optie is bedoeld voor opdrachten die op één externe computer worden uitgevoerd, maar die gegevens verzamelen van of extra opdrachten op andere externe computers worden uitgevoerd.

Let op: CredSSP delegeert de gebruikers referenties van de lokale computer naar een externe computer.
Deze procedure verhoogt het beveiligings risico van de externe bewerking.
Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.

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
Hiermee geeft u de computer op waarop de beheer bewerking moet worden uitgevoerd.
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
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionURI
Hiermee geeft u het eind punt van de verbinding.
De indeling van deze teken reeks is als volgt:

\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\>

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
Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.
Standaard is dit de huidige gebruiker.
Typ een gebruikers naam, zoals gebruiker01, Domain01\User01 of User@Domain.com .
U kunt ook een **PSCredential** -object invoeren, zoals het dat wordt geretourneerd door de cmdlet Get-Credential.
Wanneer u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.

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
Hiermee geeft u het pad op van een bestand dat wordt gebruikt om een beheer bron bij te werken.
U geeft de beheer bron op met behulp van de para meter *ResourceURI* en de para meter *SelectorSet* .
De volgende opdracht maakt bijvoorbeeld gebruik van de *filepath* -para meter:

`Invoke-WSManAction -Action stopservice -ResourceUri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath c:\input.xml -Authentication default`

Met deze opdracht wordt de **Stop** service-methode voor de **spooler** aangeroepen met behulp van invoer vanuit een bestand.
Het bestand, Input.xml, bevat de volgende inhoud:

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
Hiermee geeft u een set switches naar een service op om de aard van de aanvraag te wijzigen of te verfijnen.
Deze lijken op de Schakel opties die worden gebruikt in opdracht regel shells, omdat deze service-specifiek zijn.
U kunt een wille keurig aantal opties opgeven.

In het volgende voor beeld ziet u de syntaxis waarmee de waarden 1, 2 en 3 worden door gegeven voor de para meters a, b en c:

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Port
Hiermee geeft u de poort op die moet worden gebruikt wanneer de client verbinding maakt met de WinRM-service.
Wanneer het Trans Port HTTP is, is de standaard poort 80.
Wanneer het Trans Port HTTPS is, is de standaard poort 443.

Wanneer u HTTPS gebruikt als het Trans Port, moet de waarde van de para meter *ComputerName* overeenkomen met de common name (CN) van het server certificaat.
Als de para meter *SkipCNCheck* echter is opgegeven als onderdeel van de *SessionOption* -para meter, moet de algemene naam van het certificaat van de server niet overeenkomen met de hostnaam van de server.
De para meter *SkipCNCheck* moet alleen worden gebruikt voor vertrouwde computers.

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
Hiermee geeft u de URI van de resource klasse of het exemplaar.
De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.

Een URI bestaat uit een voor voegsel en een pad van een resource.
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
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SelectorSet
Hiermee geeft u een set waardeparen op die worden gebruikt om bepaalde beheer resource-instanties te selecteren.
*SelectorSet* wordt gebruikt wanneer er meer dan één exemplaar van de bron bestaat.
De waarde van *SelectorSet* moet een hash-tabel zijn.

In het volgende voor beeld ziet u hoe u een waarde voor deze para meter opgeeft:

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption
Hiermee worden uitgebreide opties voor de WS-Management-sessie opgegeven.
Voer een **SessionOption** -object in dat u maakt met behulp van de cmdlet New-WSManSessionOption.
Typ voor meer informatie over de beschik bare opties `Get-Help New-WSManSessionOption` .

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
Hiermee geeft u op dat het SSL-protocol (Secure Sockets Layer) wordt gebruikt om verbinding te maken met de externe computer.
Standaard wordt SSL niet gebruikt.

WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden.
Met de para meter *UseSSL* kunt u de extra beveiliging van https in plaats van http opgeven.
Als SSL niet beschikbaar is op de poort die voor de verbinding wordt gebruikt en u deze para meter opgeeft, mislukt de opdracht.

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
Hiermee geeft u een hash-tabel op waarmee u een beheer bron kunt wijzigen.
U geeft de beheer resource op met behulp van *ResourceURI* en *SelectorSet*.
De waarde van de para meter voor de *waardeset* moet een hash-tabel zijn.

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
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

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

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Testen-WSMan](Test-WSMan.md)
