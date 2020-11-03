---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 08/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/enable-wsmancredssp?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManCredSSP
ms.openlocfilehash: 0b4ec4902df2b2e93def549586e3f6cde70fadee
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251529"
---
# Enable-WSManCredSSP

## SAMENVATTING
Hiermee schakelt u CredSSP-verificatie (Credential Security Support Provider) in op een computer.

## SYNTAXIS

### Alles

```
Enable-WSManCredSSP [-Role] <String> [[-DelegateComputer] <String[]>] [-Force] [<CommonParameters>]
```

## BESCHRIJVING

`Enable-WSManCredSSP`Met de cmdlet wordt CredSSP-verificatie op een client of op een Server computer ingeschakeld.
Wanneer CredSSP-verificatie wordt gebruikt, worden de gebruikers referenties door gegeven aan een externe computer die moet worden geverifieerd. Dit type verificatie is ontworpen voor opdrachten die een externe sessie vanuit een andere externe sessie maken. Als u bijvoorbeeld een achtergrond taak wilt uitvoeren op een externe computer, gebruikt u dit type verificatie.

`Enable-WSManCredSSP` kan CredSSP inschakelen op een **client** of een **Server**. Als u CredSSP wilt inschakelen op een client, geeft u de **client** op in de para meter **Role** . Clients dragen expliciete referenties over aan een server wanneer Server verificatie wordt behaald. Als u CredSSP wilt inschakelen op een server, geeft u de **Server** op in de para meter **Role** . Een server fungeert als gemachtigde voor clients. Zie voor meer informatie **rol** in het gedeelte para meters.

> [!CAUTION]
> CredSSP-verificatie delegeert de gebruikers referenties van de lokale computer naar een externe computer. Deze procedure verhoogt het beveiligings risico van de externe bewerking. Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.

## VOORBEELDEN

### Voor beeld 1: Client Referenties delegeren

In dit voor beeld kunnen de client referenties worden gedelegeerd naar een computer met behulp van de Fully Qualified Domain Name.

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "Server02.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### Voor beeld 2: Client Referenties delegeren naar alle computers in een domein

In dit voor beeld kunnen de client referenties worden gedelegeerd naar alle computers in het domein **fabrikam.com** . Met het `*` Joker teken sterretje () geeft u alle computers op.

> [!NOTE]
> Door gebruik te maken van joker tekens met de para meter **DelegateComputer** kan CredSSP op meer computers dan nodig worden ingeschakeld.

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "*.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### Voor beeld 3: Client Referenties delegeren naar meerdere computers

In dit voor beeld kunnen de client referenties worden gedelegeerd naar meerdere computers.

```powershell
$servers = "server02.fabrikam.com", "server03.fabrikam.com", "server04.fabrikam.com"
Enable-WSManCredSSP -Role "Client" -DelegateComputer $servers
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

De `$servers` variabele bevat een lijst met server namen. `Enable-WSManCredSSP` maakt gebruik van de para meter **Role** om de **client** functie op te geven. De **DelegateComputer** haalt de computer namen op uit de `$servers` variabele.

### Voor beeld 4: een computer toestaan als gemachtigde fungeren

In dit voor beeld kan een computer fungeren als een gemachtigde voor een andere. De `Enable-WSManCredSSP` cmdlet, zoals weer gegeven in de eerdere voor beelden, schakelt alleen CredSSP-verificatie in op de client en geeft de externe computers op die namens u kunnen handelen. Om ervoor te zorgen dat de externe computer als gemachtigde voor de client fungeert, moet het CredSSP-item in het **service** knooppunt van WSMan worden ingesteld op True. In dit voor beeld wordt het CredSSP-item in het **service** knooppunt van WSMan ingesteld op True.

```powershell
Enable-WSManCredSSP -Role "Server"
```

### Voor beeld 5: een computer toestaan om te fungeren als een gemachtigde met behulp van Set-Item

In dit voor beeld kan een computer fungeren als een gemachtigde voor een andere computer. De `Enable-WSManCredSSP` opdrachten, die worden weer gegeven in de eerdere voor beelden, maken CredSSP-verificatie alleen op de client computer en geven de externe computers op die namens de client computer kunnen optreden. Als u wilt dat de externe computer als gemachtigde fungeert voor de client computer, moet het CredSSP-item in de service Directory van de WSMan-provider worden ingesteld op True.

```powershell
Connect-WSMan -ComputerName "server02"
Set-Item -Path "WSMan:\server02\service\auth\credSSP" -Value $True
```

`Connect-WSMan` Hiermee maakt u een verbinding met de externe computer, server02. `Set-Item` maakt gebruik van de para meter **Path** om de locatie van de **WSMan** -provider op te geven. De **waarde** para meter stelt de **service** -instelling in op waar.

## PARAMETERS

### -DelegateComputer

Hiermee geeft u de servers aan waarnaar de client referenties worden gedelegeerd. De best practice is het gebruik van volledig gekwalificeerde domein namen.

Joker tekens worden geaccepteerd, maar kunnen CredSSP inschakelen op meer computers dan nodig zijn.

Als de **Role** para meter Role **client** is, moet u deze para meter opgeven. Als **Role** de rol **Server** is, geeft u deze para meter niet op.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.

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

### -Rol

Hiermee geeft u op of CredSSP moet worden ingeschakeld als een client of als server. De acceptabele waarden voor deze para meter zijn: **client** en **Server**.

Als u **client** opgeeft, worden de volgende acties uitgevoerd. Met deze instellingen kan de client expliciete referenties delegeren aan een server wanneer Server verificatie wordt bereikt.

- CredSSP wordt ingeschakeld op de client.
- Hiermee stelt u de WS-Management-instelling `\<localhost|computername\>\Client\Auth\CredSSP` in op waar.
- Hiermee stelt u de **AllowFreshCredentials** van het Windows-CredSSP-beleid in op **WSMan/delegeren** op de client.

Als u **Server** opgeeft, worden de volgende acties uitgevoerd. Met deze beleids instelling kan de server fungeren als gemachtigde voor clients.

- Hiermee schakelt u CredSSP op de server in.
- Hiermee stelt u de WS-Management-instelling `\<localhost|computername\>\Service\Auth\CredSSP` in op waar.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Client, Server

Required: True
Position: 0
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

### System.Xml.Xml-element

Als CredSSP-verificatie is ingeschakeld, wordt met deze cmdlet een **XMLElement** -object gegenereerd.

## OPMERKINGEN

Als u CredSSP-verificatie wilt uitschakelen, gebruikt u de `Disable-WSManCredSSP` cmdlet.

## GERELATEERDE KOPPELINGEN

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Verbinding verbreken-WSMan](Disconnect-WSMan.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Testen-WSMan](Test-WSMan.md)
