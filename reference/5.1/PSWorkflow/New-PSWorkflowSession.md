---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflow
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowsession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowSession
ms.openlocfilehash: 995dd8a6df3ac8ebd7a204d2aefef3fa6aa71e14
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250288"
---
# New-PSWorkflowSession

## SAMENVATTING
Hiermee maakt u een werk stroom sessie.

## SYNTAXIS

```
New-PSWorkflowSession [[-ComputerName] <String[]>] [-Credential <Object>] [-Name <String[]>] [-Port <Int32>]
 [-UseSSL] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-EnableNetworkAccess]
 [<CommonParameters>]
```

## BESCHRIJVING

Met de `New-PSWorkflowSession` cmdlet maakt u een door de gebruiker beheerde sessie ( **PSSession** ) die is bedoeld voor het uitvoeren van Windows Power shell-werk stromen. Hierbij wordt gebruikgemaakt van de configuratie van de micro soft. Power shell. werk stroom sessie, die scripts bevat, typen en Format teren van bestanden en opties die vereist zijn voor werk stromen.

U kunt `New-PSWorkflowSession` de alias gebruiken `nwsn` .

U kunt ook algemene werk stroom parameters toevoegen aan deze opdracht. Zie [about_WorkflowCommonParameters](./about/about_WorkflowCommonParameters.md) voor meer informatie over algemene werk stroom parameters

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een werk stroom sessie op een externe computer maken

In dit voor beeld wordt de **WorkflowTests** -sessie gemaakt op de externe computer met ServerNode01.

```powershell
$params = @{
    ComputerName = "ServerNode01"
    Name = "WorkflowTests"
    SessionOption = (New-PSSessionOption -OutputBufferingMode Drop)
}
New-PSWorkflowSession @params
```

De waarde van de para meter **SessionOption** is een `New-PSSessionOption` opdracht waarmee de uitvoer buffer modus in de te **verwijderen** sessie wordt ingesteld.

### Voor beeld 2: werk stroom sessies op meerdere externe computers maken

In dit voor beeld worden werk stroom sessies op de ServerNode01-en Server12-computers gemaakt. De opdracht gebruikt de para meter **Credential** om uit te voeren met de machtigingen van de domein beheerder.

```powershell
"ServerNode01", "Server12" |
    New-PSWorkflowSession -Name WorkflowSession -Credential Domain01\Admin01 -ThrottleLimit 150
```

De opdracht gebruikt de para meter **ThrottleLimit** om de beperking per opdracht te verhogen tot 150.
Deze waarde heeft voor rang op de standaard beperkings limiet van 100 die is ingesteld in de **micro soft. Power shell. workflow** -sessie configuratie.

## PARAMETERS

### -ApplicationName

Hiermee geeft u het segment van de toepassings naam van de verbindings-URI op.

De standaard waarde is de waarde van de `$PSSessionApplicationName` Voorkeurs variabele op de lokale computer. Als deze voorkeurs variabele niet is gedefinieerd, is de standaard waarde WSMAN. Deze waarde is geschikt voor de meeste toepassingen. Zie [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie.

De WinRM-service gebruikt de naam van de toepassing om een listener te selecteren om de verbindings aanvraag te onderhouden.
De waarde van deze para meter moet overeenkomen met de waarde van de eigenschap **URLPrefix** van een listener op de externe computer.

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

### -Verificatie

Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van de gebruikers referenties.
De aanvaardbare waarden voor deze parameter zijn:

- Standaard
- Basic
- CredSSP
- Samenvatting
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

De standaard waarde is standaard.

CredSSP-verificatie is alleen beschikbaar in Windows Vista, Windows Server 2008 en latere versies van het Windows-besturings systeem.

Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.

> [!CAUTION]
> CredSSP-verificatie (Credential Security service provider), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share. Dit mechanisme verhoogt het beveiligings risico van de externe bewerking. Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren. Voer de vinger afdruk van het certificaat in.

Certificaten worden gebruikt in authenticatie op basis van client certificaten. Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.

Als u een certificaat vingerafdruk wilt ophalen, gebruikt u de `Get-Item` cmdlet of de `Get-ChildItem` cmdlet in het Windows Power shell-certificaat: station.

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

Hiermee maakt u een permanente verbinding ( **PSSession** ) met de opgegeven computer. Als u meerdere computer namen opgeeft, maakt Windows Power shell meerdere **PSSessions** , één voor elke computer. Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een of meer externe computers. Typ de computer naam, localhost of een punt (.) om de lokale computer op te geven. Wanneer de computer zich in een ander domein bevindt dan de gebruiker, is de Fully Qualified Domain Name vereist. U kunt ook een computer naam door geven tussen aanhalings tekens naar `New-PSWorkflowSession` .

Als u een IP-adres wilt gebruiken in de waarde van de para meter **ComputerName** , moet de opdracht de para meter **Credential** bevatten. De computer moet ook worden geconfigureerd voor HTTPS-Trans Port of het IP-adres van de externe computer moet worden opgenomen in de WinRM TrustedHosts-lijst op de lokale computer. Zie "een computer toevoegen aan de lijst met vertrouwde hosts" in [about_Remote_Troubleshooting](../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md)voor instructies voor het toevoegen van een computer naam aan de lijst TrustedHosts.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren. Standaard is dit de huidige gebruiker. Typ een gebruikers naam, zoals gebruiker01, Domain01\User01 of User@Domain.com , of voer een **PSCredential** -object in, zoals het item dat door de `Get-Credential` cmdlet wordt geretourneerd.

Wanneer u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

Geeft aan dat met deze cmdlet een interactief beveiligings token wordt toegevoegd aan loop Back-sessies. Met het interactieve token kunt u opdrachten uitvoeren in de loop back-sessie die gegevens van andere computers ophalen. U kunt bijvoorbeeld een opdracht uitvoeren in de sessie waarmee XML-bestanden van een externe computer naar de lokale computer worden gekopieerd.

Een loop back-sessie is een **PSSession** die afkomstig is van en eindigt op dezelfde computer. Als u een loop back-sessie wilt maken, geeft u de para meter **ComputerName** niet op of stelt u de waarde in op punt, localhost of de naam van de lokale computer.

Loop Back-sessies worden standaard gemaakt met een netwerk token, wat mogelijk niet voldoende machtigingen biedt om te verifiëren bij externe computers.

De para meter **EnableNetworkAccess** is alleen effectief in loop Back-sessies. Als u de para meter **EnableNetworkAccess** opgeeft wanneer u een sessie op een externe computer maakt, mislukt de opdracht, maar wordt de para meter genegeerd.

U kunt externe toegang ook toestaan in een loop back-sessie met behulp van de **CredSSP** -waarde van de **verificatie** parameter, die de sessie referenties delegeert naar andere computers.

Om de computer te beschermen tegen kwaad aardige toegang, niet-verbonden loop Back-sessies met interactieve tokens, die zijn gemaakt met behulp van de para meter **EnableNetworkAccess** , kunnen alleen opnieuw worden verbonden vanaf de computer waarop de sessie is gemaakt. Verbroken sessies die gebruikmaken van CredSSP-verificatie, kunnen opnieuw worden aangesloten op andere computers. Zie de cmdlet voor meer informatie `Disconnect-PSSession` .

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

### -Name

Hiermee geeft u een beschrijvende naam op voor de werk stroom sessie. U kunt de naam gebruiken met andere cmdlets, zoals `Get-PSSession` en `Enter-PSSession` . De naam hoeft niet uniek te zijn voor de computer of de huidige sessie.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Session#
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Hiermee geeft u de netwerk poort op de externe computer op die voor deze verbinding wordt gebruikt. Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt. De standaard poorten zijn 5985 (WinRM-poort voor HTTP) en 5986 (WinRM-poort voor HTTPS).

Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren. Gebruik de volgende opdrachten om de listener te configureren:

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

Gebruik de para meter **poort** alleen als dat nodig is. De poort instelling in de opdracht is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd. Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.

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

### -SessionOption

Hiermee geeft u geavanceerde opties voor de sessie op. Voer een **SessionOption** -object in, zoals een, dat u maakt met behulp van de- `New-PSSessionOption` cmdlet.

De standaard waarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld. Anders worden de standaard waarden bepaald door opties die zijn ingesteld in de sessie configuratie.

De waarden van de sessie optie hebben voor rang op de standaard waarden voor sessies die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en in de sessie configuratie. Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie. Zie [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

Zie voor een beschrijving van de sessie opties, met inbegrip van de standaard waarden `New-PSSessionOption` .
Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` voorkeurs [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)variabele.

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.
Als u deze para meter weglaat of een waarde van 0 (nul) opgeeft, wordt de standaard waarde voor de **micro soft. PowerShellWorkflow** -sessie configuratie, 100, gebruikt.

De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Geeft aan dat deze cmdlet het Secure Sockets Layer-Protocol (SSL) gebruikt om verbinding te maken met de externe computer. Standaard wordt SSL niet gebruikt.

WS-Management versleutelt alle Windows Power shell-inhoud die via het netwerk wordt verzonden. De para meter **UseSSL** is een extra beveiliging waarmee de gegevens worden verzonden via een HTTPS-verbinding in plaats van via een http-verbinding.

Als u deze para meter opgeeft, maar SSL is niet beschikbaar op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.

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

### System. Management. Automation. Runspaces. PSSession [], System. String

U kunt een sessie of een computer naam door geven aan deze cmdlet.

## UITVOER

### System. Management. Automation. Runspaces. PSSession

## OPMERKINGEN

Een `New-PSWorkflowSession` opdracht is gelijk aan de volgende opdracht:

`New-PSSession -ConfigurationName Microsoft.PowerShell.Workflow`

## GERELATEERDE KOPPELINGEN

[Verbinding verbreken-PSSession](../Microsoft.PowerShell.Core/Disconnect-PSSession.md)

[New-PSSession](../Microsoft.PowerShell.Core/New-PSSession.md)

[New-PSTransportOption](../Microsoft.PowerShell.Core/New-PSTransportOption.md)

[Register-PSSessionConfiguration](../Microsoft.PowerShell.Core/Register-PSSessionConfiguration.md)

[about_PSSessions](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)

[about_Workflows](../PSWorkflow/About/about_Workflows.md)

[about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md)
