---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Computer
ms.openlocfilehash: c1527c04d795206b8de968daf62456837627a098
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250846"
---
# Add-Computer

## SAMENVATTING
De lokale computer toevoegen aan een domein of werk groep.

## SYNTAXIS

### Domein (standaard)

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>]
 [-UnjoinDomainCredential <PSCredential>] -Credential <PSCredential> [-DomainName] <String> [-OUPath <String>]
 [-Server <String>] [-Unsecure] [-Options <JoinOptions>] [-Restart] [-PassThru] [-NewName <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Werkgroep

```
Add-Computer [-ComputerName <String[]>] [-LocalCredential <PSCredential>] [-Credential <PSCredential>]
 [-WorkgroupName] <String> [-Restart] [-PassThru] [-NewName <String>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Add-Computer` cmdlet voegt de lokale computer of externe computers toe aan een domein of werk groep, of verplaatst ze van het ene domein naar het andere.
Er wordt ook een domein account gemaakt als de computer wordt toegevoegd aan het domein zonder een account.

U kunt de para meters van deze cmdlet gebruiken om een organisatie-eenheid (OE) en domein controller op te geven of een niet-beveiligde samen voeging uit te voeren.

Als u de resultaten van de opdracht wilt weer geven, gebruikt u de para meters **uitgebreid** en **PassThru** .

## VOORBEELDEN

### Voor beeld 1: een lokale computer toevoegen aan een domein en de computer opnieuw opstarten

```powershell
Add-Computer -DomainName Domain01 -Restart
```

Met deze opdracht wordt de lokale computer aan het domein Domain01 toegevoegd en wordt de computer opnieuw opgestart om de wijziging van kracht te laten worden.

### Voor beeld 2: een lokale computer toevoegen aan een werk groep

```powershell
Add-Computer -WorkgroupName WORKGROUP-A
```

Met deze opdracht wordt de lokale computer toegevoegd aan de werk groep-een werk groep.

### Voor beeld 3: een lokale computer toevoegen aan een domein

```powershell
Add-Computer -DomainName Domain01 -Server Domain01\DC01 -PassThru -Verbose
```

Met deze opdracht wordt de lokale computer aan het Domain01-domein toegevoegd met behulp van de Domain01\DC01-domein controller.

De opdracht gebruikt de para meter **PassThru** en **uitgebreid** om gedetailleerde informatie over de resultaten van de opdracht op te halen.

### Voor beeld 4: een lokale computer aan een domein toevoegen met behulp van de para meter OUPath

```powershell
Add-Computer -DomainName Domain02 -OUPath "OU=testOU,DC=domain,DC=Domain,DC=com"
```

Met deze opdracht wordt de lokale computer aan het domein Domain02 toegevoegd.
De para meter OUPath wordt gebruikt om de organisatie-eenheid voor de nieuwe accounts op te geven.

### Voor beeld 5: een lokale computer toevoegen aan een domein met behulp van referenties

```powershell
Add-Computer -ComputerName Server01 -LocalCredential Server01\Admin01 -DomainName Domain02 -Credential Domain02\Admin02 -Restart -Force
```

Met deze opdracht wordt de Server01-computer toegevoegd aan het domein Domain02.
De para meter **LocalCredential** wordt gebruikt om een gebruikers account op te geven dat is gemachtigd om verbinding te maken met de Server01-computer.
De para meter **Credential** wordt gebruikt om een gebruikers account op te geven dat gemachtigd is om computers aan het domein toe te voegen.
De para meter **restart** wordt gebruikt om de computer opnieuw op te starten nadat de samen voeging is voltooid en de para meter **Force** om bevestigings berichten van gebruikers te onderdrukken.

### Voor beeld 6: een groep computers verplaatsen naar een nieuw domein

```powershell
Add-Computer -ComputerName Server01, Server02, localhost -DomainName Domain02 -LocalCredential Domain01\User01 -UnjoinDomainCredential Domain01\Admin01 -Credential Domain02\Admin01 -Restart
```

Met deze opdracht worden de Server01-en Server02-computers en de lokale computer verplaatst van Domain01 naar Domain02.

De para meter **LocalCredential** wordt gebruikt om een gebruikers account op te geven dat is gemachtigd om verbinding te maken met de drie betrokken computers.
De para meter **UnjoinDomainCredential** wordt gebruikt om een gebruikers account op te geven dat gemachtigd is om de computers uit het domein Domain01 te ontkoppelen en de para meter **Credential** om een gebruikers account op te geven dat gemachtigd is om de computers toe te voegen aan het Domain02-domein.
De para meter **restart** wordt gebruikt om alle drie de computers opnieuw op te starten nadat de verplaatsing is voltooid.

### Voor beeld 7: een computer verplaatsen naar een nieuw domein en de naam van de computer wijzigen

```powershell
Add-Computer -ComputerName Server01 -DomainName Domain02 -NewName Server044 -Credential Domain02\Admin01 -Restart
```

Met deze opdracht wordt de Server01-computer verplaatst naar de Domain02 en wordt de naam van de computer gewijzigd in Server044.

Met de opdracht wordt de referentie van de huidige gebruiker gebruikt om verbinding te maken met de Server01-computer en ontkoppelt van het huidige domein.
De para meter **Credential** wordt gebruikt om een gebruikers account op te geven dat gemachtigd is om de computer toe te voegen aan het domein Domain02.

### Voor beeld 8: computers die worden vermeld in een bestand toevoegen aan een nieuw domein

```powershell
Add-Computer -ComputerName (Get-Content Servers.txt) -DomainName Domain02 -Credential Domain02\Admin02 -Options Win9xUpgrade  -Restart
```

Met deze opdracht worden de computers die worden vermeld in het Servers.txt-bestand toegevoegd aan het domein Domain02.
De para meter **Options** wordt gebruikt om de optie **Win9xUpgrade** op te geven.
Met de para meter **restart** worden alle pas toegevoegde computers opnieuw opgestart nadat de samen voeging is voltooid.

### Voor beeld 9: een computer toevoegen aan een domein met behulp van vooraf gedefinieerde computer referenties

Deze eerste opdracht moet worden uitgevoerd door een beheerder vanaf een computer die al is toegevoegd aan het domein `Domain03` :

```powershell
New-ADComputer -Name "Server02" -AccountPassword (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)

# Then this command is run from `Server02` which is not yet domain-joined:

$joinCred = New-Object pscredential -ArgumentList ([pscustomobject]@{
    UserName = $null
    Password = (ConvertTo-SecureString -String 'TempJoinPA$$' -AsPlainText -Force)[0]
})
Add-Computer -Domain "Domain03" -Options UnsecuredJoin,PasswordPass -Credential $joinCred
```

Met deze combi natie van opdrachten maakt u een nieuw computer account met een vooraf gedefinieerde naam en een tijdelijk wacht woord voor samen voegen in een domein met een bestaande computer die lid is van een domein.
Vervolgens wordt de computer met de vooraf gedefinieerde naam afzonderlijk toegevoegd aan het domein met alleen de computer naam en het tijdelijke wacht woord voor samen voegen.
Het vooraf gedefinieerde wacht woord wordt alleen gebruikt ter ondersteuning van de koppelings bewerking en wordt vervangen als onderdeel van de normale procedure voor computer accounts nadat de verbinding met de computer is voltooid.

## PARAMETERS

### -ComputerName

Specificeert de computers die aan een domein of werk groep moeten worden toegevoegd.
Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een Internet Protocol IP-adres of een Fully Qualified Domain Name van elke externe computer.
Typ de computer naam, een punt (.) of ' localhost ' om de lokale computer op te geven.

Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.
U kunt de para meter **ComputerName** gebruiken `Add-Computer` , zelfs als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat gemachtigd is om de computers toe te voegen aan een nieuw domein.
Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.
Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.

Als u een gebruikers account wilt opgeven dat is gemachtigd om de computer uit het huidige domein te verwijderen, gebruikt u de para meter **UnjoinDomainCredential** .
Als u een gebruikers account wilt opgeven dat is gemachtigd om verbinding te maken met een externe computer, gebruikt u de para meter **LocalCredential** .

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain, Workgroup
Aliases: DomainCredential

Required: True (Domain), False (Workgroup)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DomainName

Hiermee geeft u het domein waaraan de computers worden toegevoegd.
Deze para meter is vereist bij het toevoegen van de computers aan een domein.

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DN, Domain

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Onderdrukt de vraag om bevestiging van de gebruiker.
Als u deze para meter niet opgeeft, `Add-Computer` moet u de toevoeging van elke computer bevestigen.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

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

### -LocalCredential

Hiermee geeft u een gebruikers account op dat is gemachtigd om verbinding te maken met de computers die zijn opgegeven door de para meter **ComputerName** .
Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.
Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.

Als u een gebruikers account wilt opgeven dat gemachtigd is om de computers toe te voegen aan een nieuw domein, gebruikt u de para meter **Credential** .
Als u een gebruikers account wilt opgeven dat gemachtigd is om de computers uit hun huidige domein te verwijderen, gebruikt u de para meter **UnjoinDomainCredential** .

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

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

### -NewName

Hiermee geeft u een nieuwe naam voor de computer in het nieuwe domein.
Deze para meter is alleen geldig wanneer er één computer wordt toegevoegd of verplaatst.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

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

### -Opties

Hiermee geeft u geavanceerde opties op voor de **toevoeg bewerking toevoegen** aan de computer.
Voer een of meer waarden in een door komma's gescheiden teken reeks in.

De aanvaardbare waarden voor deze parameter zijn:

- **AccountCreate** : Hiermee wordt een domein account gemaakt. De cmdlet **add-computer** maakt automatisch een domein account wanneer een computer wordt toegevoegd aan een domein. Deze optie is opgenomen voor volledigheid.

- **Win9XUpgrade** : geeft aan dat de koppelings bewerking deel uitmaakt van een upgrade van het Windows-besturings systeem.

- **UnsecuredJoin** : voert een niet-beveiligde samen voeging uit. Als u een niet-beveiligde samen voeging wilt aanvragen, gebruikt u de para meter *unsecure* of deze optie. Als u een computer wachtwoord wilt door geven, moet u deze optie gebruiken in combi natie met `PasswordPass` optie.

- **PasswordPass** : het computer wachtwoord wordt ingesteld op de waarde van de para meter *Credential* (DomainCredential) nadat een niet-beveiligde samen voeging is uitgevoerd. Deze optie geeft ook aan dat de waarde van de *referentie* -para meter (DomainCredential) een computer wachtwoord is, niet een gebruikers wachtwoord. Deze optie is alleen geldig als de `UnsecuredJoin` optie is opgegeven. Wanneer u deze optie gebruikt, moet de referentie die aan de `-Credential` para meter is gegeven, een null-gebruikers naam hebben. *must*

- **JoinWithNewName** : de naam van de computer naam in het nieuwe domein wordt gewijzigd in de naam die is opgegeven met de para meter *newname* . Wanneer u de para meter *newname* gebruikt, wordt deze optie automatisch ingesteld. Deze optie is ontworpen om te worden gebruikt met de cmdlet Rename-Computer. Als u de naam van de computer wijzigt met de cmdlet **Rename-computer** , maar de computer niet opnieuw opstart om de wijziging van kracht te laten worden, kunt u deze para meter gebruiken om de computer toe te voegen aan een domein met de nieuwe naam.

- **JoinReadOnly** : gebruikt een bestaand machine account om de computer toe te voegen aan een alleen-lezen domein controller. Het computer account moet worden toegevoegd aan de lijst met toegestane accounts voor het beleid voor wachtwoord replicatie en het account wachtwoord moet worden gerepliceerd naar de alleen-lezen domein controller vóór de koppelings bewerking.

- **InstallInvoke** : stelt de vlaggen Create (0x2) en Delete (0x4) van de para meter **FJoinOptions** van de methode **JoinDomainOrWorkgroup** in. Zie de [methode JoinDomainOrWorkgroup van de klasse Win32_ComputerSystem](https://msdn.microsoft.com/library/aa392154) in de MSDN-bibliotheek voor meer informatie over de **JoinDomainOrWorkgroup** -methode. Zie de [functie NetJoinDomain](https://msdn.microsoft.com/library/aa370433) in de MSDN-bibliotheek voor meer informatie over deze opties.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: Microsoft.PowerShell.Commands.JoinOptions
Parameter Sets: Domain
Aliases:
Accepted values: AccountCreate, Win9XUpgrade, UnsecuredJoin, PasswordPass, DeferSPNSet, JoinWithNewName, JoinReadOnly, InstallInvoke

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OUPath

Hiermee geeft u een organisatie-eenheid (OE) voor het domein account op.
Voer tussen aanhalings tekens de volledige DN-naam van de organisatie-eenheid in.
De standaard waarde is de standaard organisatie-eenheid voor computer objecten in het domein.

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: OU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourneert een object dat het item vertegenwoordigt waarmee u werkt.
Deze cmdlet genereert standaard geen uitvoer.

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

### -Restart

Hiermee worden de computers die zijn toegevoegd aan het domein of de werk groep opnieuw opgestart.
Het is vaak nood zakelijk om opnieuw op te starten om de wijziging van kracht te laten worden.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

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

### -Server

Hiermee geeft u de naam van een domein controller die de computer aan het domein toevoegt.
Geef de naam op in de DomainName\ComputerName-indeling.
Standaard is er geen domein controller opgegeven.

```yaml
Type: System.String
Parameter Sets: Domain
Aliases: DC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UnjoinDomainCredential

Hiermee geeft u een gebruikers account op dat gemachtigd is om de computers uit hun huidige domeinen te verwijderen.
Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.
Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.

Gebruik deze para meter wanneer u computers verplaatst naar een ander domein.
Als u een gebruikers account wilt opgeven dat is gemachtigd om lid te worden van het nieuwe domein, gebruikt u de para meter **Credential** .
Als u een gebruikers account wilt opgeven dat is gemachtigd om verbinding te maken met een externe computer, gebruikt u de para meter **LocalCredential** .

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Niet beveiligd

Hiermee wordt een niet-beveiligde koppeling naar het opgegeven domein uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Domain
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Werkgroepnaam

Hiermee geeft u de naam op van een werk groep waaraan de computers worden toegevoegd.
De standaard waarde is werk groep.

```yaml
Type: System.String
Parameter Sets: Workgroup
Aliases: WGN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. String

U kunt computer namen en nieuwe namen door sluizen naar de `Add-Computer` cmdlet.

## UITVOER

### Micro soft. Power shell. commands. ComputerChangeInfo

Wanneer u de para meter **PassThru** gebruikt, `Add-Computer` wordt een **ComputerChangeInfo** -object geretourneerd.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

- In Windows Power Shell 2,0 is de **Server** parameter van `Add-Computer` mislukt, zelfs als de server aanwezig is. In Windows Power Shell 3,0 is de implementatie van de **Server** parameter zodanig gewijzigd dat deze betrouwbaar werkt.

## GERELATEERDE KOPPELINGEN

[Checkpoint-Computer](Checkpoint-Computer.md)

[Verwijderen-computer](Remove-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Naam wijzigen-computer](Rename-Computer.md)

[Herstellen-computer](Restore-Computer.md)

[Stop-computer](Stop-Computer.md)

[Test-Connection](Test-Connection.md)
