---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionoption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionOption
ms.openlocfilehash: c8d51054b2beb4da0e7d54280d85b9688928147e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251295"
---
# New-PSSessionOption

## SAMENVATTING
Hiermee maakt u een object dat geavanceerde opties bevat voor een PSSession.

## SYNTAXIS

```
New-PSSessionOption [-MaximumRedirection <Int32>] [-NoCompression] [-NoMachineProfile] [-Culture <CultureInfo>]
 [-UICulture <CultureInfo>] [-MaximumReceivedDataSizePerCommand <Int32>] [-MaximumReceivedObjectSize <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-MaxConnectionRetryCount <Int32>]
 [-ApplicationArguments <PSPrimitiveDictionary>] [-OpenTimeout <Int32>] [-CancelTimeout <Int32>]
 [-IdleTimeout <Int32>] [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <AuthenticationMechanism>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [-IncludePortInSPN] [<CommonParameters>]
```

## BESCHRIJVING

De `New-PSSessionOption` cmdlet maakt een object dat geavanceerde opties bevat voor een door de gebruiker beheerde sessie ( **PSSession** ). U kunt het object gebruiken als de waarde van de para meter **SessionOption** van cmdlets die een **PSSession** maken, zoals `New-PSSession` , `Enter-PSSession` , en `Invoke-Command` .

Zonder para meters `New-PSSessionOption` genereert een object dat de standaard waarden voor alle opties bevat. Omdat alle eigenschappen kunnen worden bewerkt, kunt u het resulterende object als sjabloon gebruiken en standaard optie objecten maken voor uw onderneming.

U kunt ook een sessie optie object opslaan in de `$PSSessionOption` Voorkeurs variabele. Met de waarden van deze variabele worden nieuwe standaard waarden voor de sessie opties ingesteld. Ze zijn effectief wanneer er geen sessie opties zijn ingesteld voor de sessie en ze hebben voor rang boven de opties die zijn ingesteld in de sessie configuratie, maar u kunt ze negeren door sessie opties of een sessie optie object op te geven in een cmdlet waarmee een sessie wordt gemaakt. Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` Voorkeurs variabele [about_Preference_Variables](About/about_Preference_Variables.md).

Wanneer u een sessie optie object gebruikt in een cmdlet die een sessie maakt, hebben de sessie optie waarden prioriteit boven de standaard waarden voor sessies die zijn ingesteld in de $PSSessionOption voorkeurs variabele en in de sessie configuratie. Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie. Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

## VOORBEELDEN

### Voor beeld 1: een standaard sessie maken-optie

Met deze opdracht wordt een sessie optie object gemaakt met alle standaard waarden.

```powershell
New-PSSessionOption
```

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

### Voor beeld 2: een sessie configureren met behulp van een sessie optie object

In dit voor beeld ziet u hoe u een sessie optie object gebruikt voor het configureren van een sessie.

```powershell
$pso = New-PSSessionOption -Culture "fr-fr" -MaximumReceivedObjectSize 10MB
New-PSSession -ComputerName Server01 -SessionOption $pso
```

Met de eerste opdracht wordt een nieuw sessie optie object gemaakt en opgeslagen in de waarde van de `$pso` variabele. De tweede opdracht gebruikt de `New-PSSession` cmdlet om een sessie te maken op de externe computer Server01. De opdracht gebruikt het object Session Option in de waarde van de `$pso` variabele als de waarde van de para meter **SessionOption** van de opdracht.

### Voor beeld 3: een interactieve sessie starten

Met deze opdracht wordt de `Enter-PSSession` cmdlet gebruikt om een interactieve sessie met de Server01-computer te starten.

```powershell
Enter-PSSession -ComputerName Server01 -SessionOption (New-PSSessionOption -NoEncryption -NoCompression)
```

De waarde van de para meter **SessionOption** is een `New-PSSessionOption` opdracht met de para meters geen **versleuteling** en geen **compressie** .

De `New-PSSessionOption` opdracht bevindt zich tussen haakjes om er zeker van te zijn dat deze vóór de opdracht wordt uitgevoerd `Enter-PSSession` .

### Voor beeld 4: een sessie optie object wijzigen

Dit voor beeld laat zien dat u het sessie optie object kunt wijzigen. Alle eigenschappen hebben lees-en schrijf waarden.

```powershell
$a = New-PSSessionOption
$a.OpenTimeout
```

```Output
Days              : 0
Hours             : 0
Minutes           : 3
Seconds           : 0
Milliseconds      : 0
Ticks             : 1800000000
TotalDays         : 0.00208333333333333
TotalHours        : 0.05
TotalMinutes      : 3
TotalSeconds      : 180
TotalMilliseconds : 180000
```

```powershell
$a.UICulture = (Get-UICulture)
$a.OpenTimeout = (New-Timespan -Minutes 4)
$a.MaximumConnectionRedirectionCount = 1
$a
```

```Output
MaximumConnectionRedirectionCount : 1
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         : en-US
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:04:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

Gebruik deze methode om een standaard sessie object te maken voor uw onderneming en vervolgens aangepaste versies van de toepassing te maken voor specifiek gebruik.

### Voor beeld 5: een voorkeurs variabele maken

Met deze opdracht maakt u een `$PSSessionOption` Voorkeurs variabele.

```powershell
$PSSessionOption = New-PSSessionOption -OpenTimeOut 120000
```

Wanneer de `$PSSessionOption` Voorkeurs variabele in de sessie plaatsvindt, worden er standaard waarden ingesteld voor opties in de sessies die worden gemaakt met behulp van de `New-PSSession` `Enter-PSSession` `Invoke-Command` cmdlets, en.

Als u de `$PSSessionOption` variabele beschikbaar wilt maken in alle sessies, voegt u deze toe aan uw Power shell-sessie en aan uw Power shell-profiel.

Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` Voorkeurs variabele [about_Preference_Variables](About/about_Preference_Variables.md).
Zie [about_Profiles](About/about_Profiles.md)voor meer informatie over profielen.

### Voor beeld 6: voldoen aan de vereisten voor een configuratie van een externe sessie

In dit voor beeld ziet u hoe u een **SessionOption** -object gebruikt om te voldoen aan de vereisten voor een configuratie van een externe sessie.

```powershell
$skipCN = New-PSSessionOption -SkipCNCheck
New-PSSession -ComputerName 171.09.21.207 -UseSSL -Credential Domain01\User01 -SessionOption $SkipCN
```

De eerste opdracht gebruikt de `New-PSSessionOption` cmdlet om een sessie optie object te maken met de eigenschap **SkipCNCheck** . De opdracht slaat het resulterende sessie object op in de `$skipCN` variabele.

Met de tweede opdracht wordt de `New-PSSession` cmdlet gebruikt om een nieuwe sessie te maken op een externe computer. De `$skipCN` controle variabele wordt gebruikt in de waarde van de para meter **SessionOption** .

Omdat de computer wordt geïdentificeerd aan de hand van het IP-adres, komt de waarde van de para meter **ComputerName** niet overeen met een van de algemene namen in het certificaat dat wordt gebruikt voor Secure Sockets Layer (SSL). Als gevolg hiervan is de optie **SkipCNCheck** vereist.

### Voor beeld 7: argumenten beschikbaar maken voor een externe sessie

In dit voor beeld ziet u hoe u de para meter **ApplicationArguments** van de `New-PSSessionOption` cmdlet gebruikt om extra gegevens beschikbaar te maken voor de externe sessie.

```powershell
$team = @{Team="IT"; Use="Testing"}
$TeamOption = New-PSSessionOption -ApplicationArguments $team
$s = New-PSSession -ComputerName Server01 -SessionOption $TeamOption
Invoke-Command -Session $s {$PSSenderInfo.ApplicationArguments}
```

```Output
Name                 Value
----                 -----
Team                 IT
Use                  Testing
PSVersionTable       {CLRVersion, BuildVersion, PSVersion, WSManStackVersion...}
```

```powershell
Invoke-Command -Session $s {
  if ($PSSenderInfo.ApplicationArguments.Use -ne "Testing") {
    .\logFiles.ps1
  }
  else {
    "Just testing."
  }
}
```

```Output
Just testing.
```

Met de eerste opdracht maakt u een hash-tabel met twee sleutels, **team** en **gebruik**. Met de opdracht wordt de hash-tabel in de `$team` variabele opgeslagen. Zie [about_Hash_Tables](about/about_Hash_Tables.md)voor meer informatie over hash-tabellen.

Vervolgens maakt de `New-PSSessionOption` cmdlet met de para meter **ApplicationArguments** een sessie optie object dat is opgeslagen in de `$team` variabele. Wanneer `New-PSSessionOption` u het sessie optie object maakt, wordt de hash-tabel in de waarde van de para meter **ApplicationArguments** automatisch geconverteerd naar een primitieve woorden lijst, zodat de gegevens betrouwbaar kunnen worden verzonden naar de externe sessie.

`New-PSSession`Met de cmdlet wordt een sessie gestart op de Server01-computer. De para meter **SessionOption** wordt gebruikt voor het toevoegen van de opties in de `$teamOption` variabele.

De `Invoke-Command` cmdlet laat zien dat de gegevens in de `$team` variabele beschikbaar zijn voor opdrachten in de externe sessie. De gegevens worden weer gegeven in de eigenschap **ApplicationArguments** van de `$PSSenderInfo` Automatische variabele.

In het eind `Invoke-Command` ziet u hoe de gegevens kunnen worden gebruikt.

## PARAMETERS

### -ApplicationArguments

Hiermee geeft u een primitieve woorden lijst op die naar de externe sessie wordt verzonden. Opdrachten en scripts in de externe sessie, met inbegrip van opstart scripts in de sessie configuratie, kunnen deze woorden lijst vinden in de eigenschap **ApplicationArguments** van de `$PSSenderInfo` Automatische variabele. U kunt deze para meter gebruiken om gegevens te verzenden naar de externe sessie.

Zie [about_Hash_Tables](about/about_Hash_Tables.md), [about_Session_Configurations](About/about_Session_Configurations.md)en [about_Automatic_Variables](about/about_Automatic_Variables.md)voor meer informatie.

```yaml
Type: System.Management.Automation.PSPrimitiveDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CancelTimeout

Hiermee wordt bepaald hoe lang Power shell wacht tot een annulerings bewerking (CTRL + C) is voltooid voordat deze wordt beëindigd.
Voer een waarde in milliseconden in.

De standaard waarde is 60000 (één minuut). Een waarde van 0 (nul) betekent geen time-out; de opdracht wordt voor onbepaalde tijd voortgezet.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: CancelTimeoutMSec

Required: False
Position: Named
Default value: 60000
Accept pipeline input: False
Accept wildcard characters: False
```

### -Cultuur

Hiermee geeft u de cultuur op die voor de sessie moet worden gebruikt. Voer een cultuur naam in de `<languagecode2>-<country/regioncode2>` indeling (like `ja-JP` ) in, een variabele die een **Culture info** -object bevat of een opdracht waarmee een **Culture info** -object wordt opgehaald.

De standaard waarde is `$Null` en de cultuur die in het besturings systeem is ingesteld, wordt in de sessie gebruikt.

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IdleTimeout

Hiermee wordt bepaald hoe lang de sessie geopend blijft als de externe computer geen communicatie van de lokale computer ontvangt. Dit omvat het heartbeat-signaal. Wanneer het interval is verlopen, wordt de sessie gesloten.

De time-outwaarde voor inactiviteit is van groot belang als u van plan bent om de verbinding met een sessie te verbreken en opnieuw te verbinden. U kunt opnieuw verbinding maken als er geen time-out is opgetreden voor de sessie.

Voer een waarde in milliseconden in. De minimum waarde is 60000 (1 minuut). Het maximum is de waarde van de eigenschap **MaxIdleTimeoutms** van de sessie configuratie. De standaard waarde,-1, heeft geen time-out voor inactiviteit.

De sessie gebruikt de time-out voor inactiviteit die is ingesteld in de sessie opties, indien van toepassing. Als geen is ingesteld (-1), gebruikt de sessie de waarde van de eigenschap **IdleTimeoutMs** van de sessie configuratie of de time-outwaarde van de WSMan-shell ( `WSMan:\<ComputerName>\Shell\IdleTimeout` ), afhankelijk van wat het kleinste is.

Als de time-out voor inactiviteit in de sessie opties groter is dan de waarde van de eigenschap **MaxIdleTimeoutMs** van de sessie configuratie, mislukt de opdracht voor het maken van een sessie.

De **IdleTimeoutMs** -waarde van de standaard **micro soft. Power shell** -sessie configuratie is 7200000 milliseconden (2 uur). De **MaxIdleTimeoutMs** -waarde is 2147483647 milliseconden ( \> 24 dagen). De standaard waarde van de time-out voor inactiviteit van de WSMan-shell `WSMan:\<ComputerName>\Shell\IdleTimeout` is 7200000 milliseconden (2 uur).

De time-outwaarde voor inactiviteit van een sessie kan ook worden gewijzigd wanneer de verbinding met een sessie wordt verbroken of als er opnieuw verbinding wordt gemaakt met een sessie. Zie voor meer informatie `Disconnect-PSSession` en `Connect-PSSession`.

In Windows Power Shell 2,0 is de standaard waarde van de para meter **IdleTimeout** 240000 (4 minuten).

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: IdleTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludePortInSPN

Bevat het poort nummer in de SPN (Service Principal Name) die voor Kerberos-verificatie wordt gebruikt, bijvoorbeeld `HTTP://<ComputerName>:5985` . Met deze optie kan een client die een niet-standaard SPN gebruikt, verifiëren bij een externe computer die gebruikmaakt van Kerberos-verificatie.

De optie is ontworpen voor ondernemingen waarbij meerdere services die ondersteuning bieden voor Kerberos-verificatie worden uitgevoerd onder verschillende gebruikers accounts. Zo kan een IIS-toepassing die Kerberos-verificatie toestaat, vereisen dat de standaard-SPN wordt geregistreerd voor een gebruikers account dat verschilt van het computer account. In dergelijke gevallen kan externe communicatie van Power shell met Kerberos niet worden geverifieerd omdat hiervoor een SPN is vereist die is geregistreerd bij het computer account. Om dit probleem op te lossen, kunnen beheerders verschillende Spn's maken, zoals met behulp van **Setspn.exe** , die zijn geregistreerd voor verschillende gebruikers accounts en er onderscheid van kunnen worden gemaakt door het poort nummer in de SPN op te nemen.

Zie [overzicht van Setspn](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10))voor meer informatie.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

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

### -MaxConnectionRetryCount

Hiermee geeft u het aantal keren op dat Power shell probeert verbinding te maken met een doel computer als de huidige poging mislukt vanwege netwerk problemen. De standaard waarde is 5.

Deze para meter is toegevoegd voor Power shell-versie 5,0.

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

### -MaximumReceivedDataSizePerCommand

Hiermee geeft u het maximum aantal bytes op dat de lokale computer kan ontvangen van de externe computer in één opdracht. Voer een waarde in bytes in. Standaard is er geen limiet voor de gegevens grootte.

Deze optie is ontworpen om de resources op de client computer te beveiligen.

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

### -MaximumReceivedObjectSize

Hiermee geeft u de maximale grootte van een object op dat de lokale computer kan ontvangen van de externe computer. Deze optie is ontworpen om de resources op de client computer te beveiligen. Voer een waarde in bytes in.

Als u deze para meter weglaat in Windows Power Shell 2,0, geldt er geen limiet voor de object grootte. Als u deze para meter weglaat in Windows Power Shell 3,0, is de standaard waarde 200 MB.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 200 MB
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumRedirection

Bepaalt hoe vaak Power shell een verbinding met een alternatieve URI (Uniform Resource Identifier) omleidt voordat de verbinding is mislukt. De standaard waarde is 5. Een waarde van 0 (nul) voor komt dat alle omleidingen.

Deze optie wordt alleen in de sessie gebruikt wanneer de para meter **AllowRedirection** wordt gebruikt in de opdracht voor het maken van de sessie.

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

### -Geen compressie

Hiermee schakelt u pakket compressie uit in de sessie. Compressie maakt gebruik van meer processor cycli, maar maakt sneller verzen ding.

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

### -Geen versleuteling

Hiermee schakelt u gegevens versleuteling uit.

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

### -NoMachineProfile

Hiermee wordt voor komen dat het Windows-gebruikers profiel van de gebruiker wordt geladen. Als gevolg hiervan kan de sessie sneller worden gemaakt, maar gebruikersspecifieke register instellingen, items als omgevings variabelen en certificaten zijn niet beschikbaar in de sessie.

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

### -Opentime-out

Hiermee wordt bepaald hoe lang de client computer wacht totdat de sessie verbinding tot stand is gebracht. Wanneer het interval is verlopen, mislukt de opdracht om de verbinding tot stand te brengen. Voer een waarde in milliseconden in.

De standaard waarde is 180000 (3 minuten). Een waarde van 0 (nul) betekent geen time-out; de opdracht wordt voor onbepaalde tijd voortgezet.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OpenTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### -OperationTimeout

Hiermee wordt de maximale tijd bepaald dat elke bewerking in de sessie kan worden uitgevoerd. Wanneer het interval is verlopen, mislukt de bewerking. Voer een waarde in milliseconden in.

De standaard waarde is 180000 (3 minuten). Een waarde van 0 (nul) betekent geen time-out; de bewerking wordt voor onbepaalde tijd voortgezet.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputBufferingMode

Hiermee wordt bepaald hoe de uitvoer van de opdracht wordt beheerd in verbroken sessies wanneer de uitvoer buffer vol raakt.

Als de uitvoer buffer modus niet is ingesteld in de sessie of in de sessie configuratie, is de standaard waarde **blok keren**. Gebruikers kunnen ook de uitvoer buffer modus wijzigen wanneer de verbinding met de sessie wordt verbroken.

Als u deze para meter weglaat, is de waarde van de **OutputBufferingMode** van het object Session Option geen. De waarde **blok keren** of **verwijderen** overschrijft de transport optie uitvoer buffer modus die in de sessie configuratie is ingesteld. De aanvaardbare waarden voor deze parameter zijn:

- Blok keren. Wanneer de uitvoer buffer vol is, wordt de uitvoering onderbroken totdat de buffer leeg is.
- Directe. Wanneer de uitvoer buffer vol is, wordt de uitvoering voortgezet. Wanneer er een nieuwe uitvoer wordt opgeslagen, wordt de oudste uitvoer verwijderd.
- Geen. Er is geen uitvoer buffer modus opgegeven.

Zie voor meer informatie over de transport optie uitvoer buffer modus `New-PSTransportOption` .

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAccessType

Hiermee wordt bepaald welk mechanisme wordt gebruikt voor het omzetten van de hostnaam. De aanvaardbare waarden voor deze parameter zijn:

- IEConfig
- WinHttpConfig
- Auto detectie
- NoProxyServer
- Geen

De standaard waarde is geen.

Zie [ProxyAccessType Enumeration (Engelstalig)](/dotnet/api/system.management.automation.remoting.proxyaccesstype?redirectedfrom=MSDN&view=powershellsdk-1.1.0)voor meer informatie over de waarden van deze para meter.

```yaml
Type: System.Management.Automation.Remoting.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: None, IEConfig, WinHttpConfig, AutoDetect, NoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAuthentication

Hiermee geeft u de verificatie methode op die wordt gebruikt voor het omzetten van de proxy. De acceptabele waarden voor deze para meter zijn: **Basic** , **Digest** en **Negotiate**. De standaard waarde is **Negotiate**.

Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?redirectedfrom=MSDN&view=powershellsdk-1.1.0)voor meer informatie over de waarden van deze para meter.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Negotiate
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

Hiermee geeft u de referenties op die moeten worden gebruikt voor proxy verificatie. Voer een variabele in die een **PSCredential** -object bevat of een opdracht waarmee een **PSCredential** -object wordt opgehaald, zoals een `Get-Credential` opdracht. Als deze optie niet is ingesteld, worden er geen referenties opgegeven.

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

Hiermee geeft u op dat wanneer verbinding wordt gemaakt via HTTPS, de client niet controleert of het server certificaat is ondertekend door een vertrouwde certificerings instantie (CA).

Gebruik deze optie alleen als de externe computer wordt vertrouwd door een ander mechanisme te gebruiken, bijvoorbeeld wanneer de externe computer deel uitmaakt van een netwerk dat fysiek is beveiligd en geïsoleerd of wanneer de externe computer wordt vermeld als een vertrouwde host in een WinRM-configuratie.

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

### -SkipCNCheck

Hiermee geeft u op dat de algemene naam (CN) van het certificaat van de server niet overeenkomt met de hostnaam van de server. Deze optie wordt alleen gebruikt in externe bewerkingen die gebruikmaken van het HTTPS-protocol.

Gebruik deze optie alleen voor vertrouwde computers.

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

### -SkipRevocationCheck

Valideert niet de intrekkings status van het server certificaat.

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

### -UICulture

Hiermee geeft u de UI-cultuur op die voor de sessie moet worden gebruikt.

Geldige waarden zijn:

- Een cultuur naam in `<languagecode2>-<country/regioncode2>` indeling, zoals `ja-JP`
- Een variabele die een **Culture info** -object bevat
- Een opdracht waarmee een **Culture info** -object wordt opgehaald, zoals `Get-Culture`

De standaard waarde is `$null` en de UI-cultuur die in het besturings systeem is ingesteld tijdens het maken van de sessie, wordt in de sessie gebruikt.

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseUTF16

Geeft aan dat deze cmdlet de aanvraag in een UTF16-indeling codeert in plaats van UTF8-indeling.

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

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. Management. Automation. Remoting. PSSessionOption

## OPMERKINGEN

Als de para meter **SessionOption** niet wordt gebruikt in een opdracht voor het maken van een **PSSession** , worden de sessie opties bepaald door de eigenschaps waarden van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld. Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` variabele [about_Preference_Variables](About/about_Preference_Variables.md).

De eigenschappen van een sessie configuratie object zijn afhankelijk van de opties die zijn ingesteld voor de sessie configuratie en de waarden van deze opties. Daarnaast hebben sessie configuraties die gebruikmaken van een sessie configuratie bestand extra eigenschappen.

## GERELATEERDE KOPPELINGEN

[Enter-PSSession](Enter-PSSession.md)

[Invoke-opdracht](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

