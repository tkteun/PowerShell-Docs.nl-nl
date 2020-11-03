---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmansessionoption?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManSessionOption
ms.openlocfilehash: 8996c550147ab7e0857d97b0a47baf92fac514d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250082"
---
# New-WSManSessionOption

## SAMENVATTING
Maakt een hash-tabel voor sessie-opties die moet worden gebruikt als invoer parameters voor WS-Management-cmdlets.

## SYNTAXIS

```
New-WSManSessionOption [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <ProxyAuthentication>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck] [-SPNPort <Int32>]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **New-WSManSessionOption** maakt u een hash-tabel voor Wsman-sessie opties die kan worden door gegeven aan WSMan-cmdlets:

- Get-WSManInstance
- Set-WSManInstance
- Invoke-WSManAction
- Connect-WSMan

## VOORBEELDEN

### Voor beeld 1: een verbinding maken die gebruikmaakt van verbindings opties

```
PS C:\> $a = New-WSManSessionOption -OperationTimeout 30000
PS C:\> Connect-WSMan -ComputerName "server01" -SessionOption $a
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

In dit voor beeld wordt een verbinding met de externe Server01-computer gemaakt met behulp van de verbindings opties die zijn gedefinieerd door **New-WSManSessionOption**.

De eerste opdracht maakt gebruik van **New-WSManSessionOption** voor het opslaan van een set opties voor Verbindings instellingen in de variabele $a.
In dit geval stelt de sessie opties een verbindings tijd in van 30 seconden (30.000 milliseconden).

De tweede opdracht gebruikt de para meter *SessionOption* om de referenties door te geven die zijn opgeslagen in de $a variabele om **verbinding te maken-WSMan**.
**Connect-WSMan** maakt verbinding met de externe Server01-computer met behulp van de opgegeven sessie opties.

**Connect-WSMan** wordt doorgaans gebruikt in de context van de WSMan-provider om verbinding te maken met een externe computer, in dit geval de Server01-computer.
U kunt de cmdlet echter gebruiken om verbindingen met externe computers tot stand te brengen voordat u overschakelt naar de WSMan-provider.
Deze verbindingen worden weer gegeven in de lijst **computer naam** .

## PARAMETERS

### -Geen versleuteling
Geeft aan dat de verbinding geen versleuteling gebruikt voor externe bewerkingen via HTTP.

Standaard is niet-versleuteld verkeer niet ingeschakeld.
Deze moet worden ingeschakeld in de lokale configuratie.

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

### -OperationTimeout
Hiermee geeft u de time-out op, in milliseconden, voor de WS-Management bewerking.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAccessType
Hiermee geeft u het mechanisme op waarmee de proxy server zich bevindt.
De aanvaardbare waarden voor deze parameter zijn:

- ProxyIEConfig.
Gebruik de proxy configuratie van Internet Explorer voor de huidige gebruiker.
- ProxyWinHttpConfig.
De WSMan-client gebruikt de proxy-instellingen die zijn geconfigureerd voor WinHTTP, met behulp van het ProxyCfg.exe-hulp programma.
- ProxyAutoDetect.
Automatische detectie van een proxy server afdwingen.
- ProxyNoProxyServer.
Gebruik geen proxy server.
Alle hostnamen lokaal oplossen.

De standaard waarde is ProxyIEConfig.

```yaml
Type: Microsoft.WSMan.Management.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: ProxyIEConfig, ProxyWinHttpConfig, ProxyAutoDetect, ProxyNoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAuthentication
Hiermee geeft u de verificatie methode op die moet worden gebruikt bij de proxy.
De aanvaardbare waarden voor deze parameter zijn:

- Hoofd.
Basic is een schema waarin de gebruikers naam en het wacht woord in ongecodeerde tekst worden verzonden naar de server of proxy.
- Vatting.
Digest is een vraag/antwoord-schema dat gebruikmaakt van een door de server opgegeven gegevens reeks voor de uitdaging.
- Afspraken.
Onderhandelen is een vraag/antwoord-schema waarmee wordt onderhandeld over de server of proxy om te bepalen welk schema moet worden gebruikt voor verificatie.
Voor beelden zijn het Kerberos-protocol en NTLM.

De standaard waarde is Negotiate.

```yaml
Type: Microsoft.WSMan.Management.ProxyAuthentication
Parameter Sets: (All)
Aliases:
Accepted values: Negotiate, Basic, Digest

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential
Hiermee geeft u een gebruikers account op dat gemachtigd is om toegang te krijgen via een tussenliggende webproxy.

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

### -SkipCACheck
Hiermee geeft u op dat, wanneer de verbinding via HTTPS maakt, niet door de client wordt gecontroleerd of het server certificaat is ondertekend door een vertrouwde certificerings instantie (CA).
Gebruik deze optie alleen als de externe computer wordt vertrouwd door een andere methode, bijvoorbeeld als de externe computer deel uitmaakt van een netwerk dat fysiek is beveiligd en geïsoleerd of als de externe computer wordt vermeld als een vertrouwde host in de WS-Management configuratie.

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

### -SkipCNCheck
Hiermee geeft u op dat de algemene naam (CN) van het certificaat van de server niet overeenkomt met de hostnaam van de server.
Dit wordt alleen gebruikt in externe bewerkingen met behulp van HTTPS.
Deze optie mag alleen worden gebruikt voor vertrouwde computers.

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

### -SkipRevocationCheck
Geeft aan dat de verbinding de intrekkings status van het server certificaat niet verifieert.

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

### -SPNPort
Hiermee geeft u een poort nummer op dat moet worden toegevoegd aan de SPN (Service Principal Name) van de externe server.
Er wordt een SPN gebruikt wanneer het verificatie mechanisme Kerberos of Negotiate is.

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

### -UseUTF16
Geeft aan dat de verbinding de aanvraag in een UTF16-indeling versleutelt in plaats van UTF8-indeling.
De standaard waarde is UTF8-code ring.

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

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

### SessionOption

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

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Testen-WSMan](Test-WSMan.md)
