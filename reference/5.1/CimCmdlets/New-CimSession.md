---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSession
ms.openlocfilehash: 04d0b272995538e88fff2725eb8806c66d217460
ms.sourcegitcommit: 9a53e53e7a3ef9ac0a212c61005efff9e9902452
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/18/2020
ms.locfileid: "93251836"
---
# New-CimSession

## SAMENVATTING

Hiermee maakt u een CIM-sessie.

## SYNTAXIS

### CredentialParameterSet (standaard)

```
New-CimSession [-Authentication <PasswordAuthenticationMechanism>] [[-Credential] <PSCredential>]
 [[-ComputerName] <String[]>] [-Name <String>] [-OperationTimeoutSec <UInt32>] [-SkipTestConnection]
 [-Port <UInt32>] [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

### CertificatePrameterSet

```
New-CimSession [-CertificateThumbprint <String>] [[-ComputerName] <String[]>] [-Name <String>]
 [-OperationTimeoutSec <UInt32>] [-SkipTestConnection] [-Port <UInt32>]
 [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

## BESCHRIJVING

Met de `New-CimSession` cmdlet wordt een CIM-sessie gemaakt. Een CIM-sessie is een client-side-object dat een verbinding met een lokale computer of een externe computer vertegenwoordigt. De CIM-sessie bevat informatie over de verbinding, zoals **ComputerName** , het gebruikte protocol of verschillende id's.

Met deze cmdlet wordt een CIM-sessie object geretourneerd dat kan worden gebruikt door alle andere CIM-cmdlets.

## VOORBEELDEN

### Voor beeld 1: een CIM-sessie met standaard opties maken

In dit voor beeld wordt een lokale CIM-sessie met standaard opties gemaakt. Als **ComputerName** niet is opgegeven, `New-CimSession` maakt een DCOM-sessie naar de lokale computer.

```powershell
New-CimSession
```

### Voor beeld 2: een CIM-sessie maken op een specifieke computer

In dit voor beeld wordt een CIM-sessie gemaakt met de computer die is opgegeven door **ComputerName**.
`New-CimSession`Maakt standaard een WSMan-sessie wanneer **ComputerName** wordt opgegeven.

```powershell
New-CimSession -ComputerName Server01
```

### Voor beeld 3: een CIM-sessie maken op meerdere computers

In dit voor beeld wordt een CIM-sessie gemaakt voor alle computers die zijn opgegeven door **ComputerName** , in de door komma's gescheiden lijst.

```powershell
New-CimSession -ComputerName Server01,Server02,Server03
```

### Voor beeld 4: een CIM-sessie met een beschrijvende naam maken

In dit voor beeld wordt een externe CIM-sessie gemaakt op alle computers die zijn opgegeven door **ComputerName** , in de door komma's gescheiden lijst en wordt een beschrijvende naam toegewezen aan de nieuwe sessies door een **naam** op te geven.

```powershell
New-CimSession -ComputerName Server01,Server02 -Name FileServers
Get-CimSession -Name File*
```

U kunt de beschrijvende naam van een CIM-sessie gebruiken om te verwijzen naar de sessie in andere CIM-cmdlets, bijvoorbeeld [Get-CimSession](Get-CimSession.md).

### Voor beeld 5: een CIM-sessie maken op een computer met behulp van een PSCredential-object

In dit voor beeld wordt een CIM-sessie gemaakt met de computer die is opgegeven door **ComputerName** , met behulp van het **PSCredential** -object dat is opgegeven door **Credential** en het verificatie type dat wordt opgegeven door de **verificatie**.

```powershell
New-CimSession -ComputerName Server01 -Credential $cred -Authentication Negotiate
```

U kunt een **PSCredential** -object maken met behulp van de- [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdlet.

### Voor beeld 6: een CIM-sessie maken op een computer met behulp van een specifieke poort

In dit voor beeld wordt een CIM-sessie gemaakt met de computer die is opgegeven door **computer naam** met behulp van de TCP-poort die is opgegeven door **poort**.

```powershell
New-CimSession -ComputerName Server01 -Port 1234
```

### Voor beeld 7: een CIM-sessie maken met DCOM

In dit voor beeld wordt een CIM-sessie gemaakt met behulp van het gedistribueerde COM-Protocol (DCOM) in plaats van WSMan.

```powershell
$SessionOption = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server1 -SessionOption $SessionOption
```

## PARAMETERS

### -Verificatie

Hiermee geeft u het verificatie type op dat wordt gebruikt voor de referenties van de gebruiker. De aanvaardbare waarden voor deze parameter zijn:

- Standaard
- Samenvatting
- Negotiate
- Basic
- Kerberos
- NtlmDomain
- CredSsp

U kunt het verificatie type **NtlmDomain** niet gebruiken voor verbinding met de lokale computer. **CredSSP** -verificatie is alleen beschikbaar in Windows Vista, windows server 2008 en latere versies van Windows.

> [!CAUTION]
> CredSSP-verificatie (Credential Security service provider) is ontworpen voor opdrachten die verificatie vereisen voor meer dan één bron, zoals het openen van een externe netwerk share. Dit mechanisme verhoogt het beveiligings risico van de externe bewerking. Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: CredentialParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CertificateThumbprint

Hiermee geeft u het digitale open bare-sleutel certificaat (X. 509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren. Voer de vinger afdruk van het certificaat in.

Certificaten worden gebruikt in authenticatie op basis van client certificaten. Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.

Gebruik de [`Get-Item`](../Microsoft.Powershell.Management/Get-Item.md) [`Get-ChildItem`](../Microsoft.Powershell.Management/Get-ChildItem.md) cmdlets in de Power shell-certificaat provider om een certificaat vingerafdruk te verkrijgen.

Zie [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)voor meer informatie.

```yaml
Type: System.String
Parameter Sets: CertificatePrameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u de naam op van de computer waarop u de CIM-sessie wilt maken. Geef een naam op voor één computer of meerdere computer namen gescheiden door een komma.

Als **ComputerName** niet is opgegeven, wordt er een CIM-sessie naar de lokale computer gemaakt. U kunt de waarde voor computer naam opgeven in een van de volgende indelingen:

- Een of meer NetBIOS-namen
- Een of meer IP-adressen
- Een of meer volledig gekwalificeerde domein namen.

Als de computer zich in een ander domein bevindt dan de gebruiker, moet u de Fully Qualified Domain Name opgeven.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren. Als er geen **referentie** is opgegeven, wordt het huidige gebruikers account gebruikt.

Geef de waarde voor **referenties** op met behulp van een van de volgende indelingen:

- Een gebruikers naam: ' gebruiker01 '
- Een domein naam en een gebruikers naam: ' Domain01\User01 '
- Een user principal name: User@Domain.com
- Een PSCredential-object, zoals het dat door de [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) cmdlet wordt geretourneerd.

Wanneer u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialParameterSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een beschrijvende naam op voor de CIM-sessie.

U kunt de naam gebruiken om te verwijzen naar de CIM-sessie wanneer u andere cmdlets gebruikt, zoals de [`Get-CimSession`](Get-CimSession.md) cmdlet.
De naam hoeft niet uniek te zijn voor de computer of de huidige sessie.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OperationTimeoutSec

De duur waarvoor de cmdlet wacht op een reactie van de server.

Standaard is de waarde van deze para meter 0, wat betekent dat de cmdlet de standaard time-outwaarde voor de server gebruikt.

Als de para meter **OperationTimeoutSec** is ingesteld op een waarde die kleiner is dan de robuuste time-out voor de verbinding opnieuw proberen 3 minuten, kunnen netwerk fouten die langer zijn dan de waarde van de para meter **OperationTimeoutSec** , niet worden hersteld, omdat er een time-out optreedt voor de bewerking op de server voordat de client opnieuw verbinding kan maken.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port

Hiermee geeft u de netwerk poort op de externe computer op die voor deze verbinding wordt gebruikt.
Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt.
De standaard poorten zijn 5985 (de WinRM-poort voor HTTP) en 5986 (de WinRM-poort voor HTTPS).

Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren.
Gebruik de volgende opdrachten om de listener te configureren:

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number>"}`

Gebruik de para meter **poort** alleen als dat nodig is. De poort instelling in de opdracht is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd. Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SessionOption

Hiermee stelt u geavanceerde opties in voor de nieuwe CIM-sessie. Voer de naam in van een **CimSessionOption** -object dat is gemaakt met de [`New-CimSessionOption`](New-CimSessionOption.md) cmdlet.

```yaml
Type: Microsoft.Management.Infrastructure.Options.CimSessionOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipTestConnection

De cmdlet maakt standaard `New-CimSession` een verbinding met een extern WS-Management-eind punt om twee redenen: om te controleren of de externe server luistert naar het poort nummer dat is opgegeven met de para meter **poort** en om de opgegeven account referenties te controleren. De verificatie wordt uitgevoerd met behulp van een standaard WS-Identity bewerking. U kunt de para meter **SkipTestConnection** toevoegen als het externe WS-Management-eind punt WS-identify niet kan gebruiken, of om een aantal gegevens overdrachts tijd te verminderen.

```yaml
Type: System.Management.Automation.SwitchParameter
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

### Micro soft. Management. Infrastructure. CimSession

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-Child item](../Microsoft.Powershell.Management/Get-ChildItem.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Get-item](../Microsoft.Powershell.Management/Get-Item.md)

[Get-CimSession](Get-CimSession.md)

[Remove-CimSession](Remove-CimSession.md)

[New-CimSessionOption](New-CimSessionOption.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)
