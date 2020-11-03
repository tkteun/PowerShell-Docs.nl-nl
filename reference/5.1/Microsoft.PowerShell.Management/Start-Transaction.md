---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transaction
ms.openlocfilehash: 53be131f45f15e5d2053b183040dc7b3dca4a14c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250541"
---
# Start-Transaction

## SAMENVATTING
Start een trans actie.

## SYNTAXIS

```
Start-Transaction [-Timeout <Int32>] [-Independent] [-RollbackPreference <RollbackSeverity>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Start-trans actie** wordt een trans actie gestart. Dit is een reeks opdrachten die als een eenheid worden beheerd.
Een trans actie kan worden voltooid of worden doorgevoerd.
Het kan ook volledig ongedaan worden gemaakt of teruggedraaid, zodat alle gegevens die door de trans actie worden gewijzigd naar de oorspronkelijke status worden teruggezet.
Omdat de opdrachten in een trans actie als eenheid worden beheerd, worden alle opdrachten vastgelegd of worden alle opdrachten teruggedraaid.

Standaard worden trans acties automatisch teruggedraaid als een opdracht in de trans actie een fout genereert.
U kunt de para meter *RollbackPreference* gebruiken om dit gedrag te wijzigen.

De cmdlets die in een trans actie worden gebruikt, moeten zijn ontworpen ter ondersteuning van trans acties.
Cmdlets die trans acties ondersteunen, hebben een *UseTransaction* -para meter.
Voor het uitvoeren van trans acties in een provider moet de provider trans acties ondersteunen.
De Windows Power shell-register provider in Windows Vista en latere versies van het Windows-besturings systeem ondersteunt trans acties.
U kunt ook de klasse **micro soft. Power shell. commands. Management. TransactedString** gebruiken om expressies op te genomen in trans acties op elke versie van het Windows-systeem dat Windows Power shell ondersteunt.
Andere Windows Power shell-providers kunnen ook trans acties ondersteunen.

Er kan slechts één trans actie tegelijk actief zijn.
Als u een nieuwe, onafhankelijke trans actie start terwijl een trans actie wordt uitgevoerd, wordt de nieuwe trans actie de actieve trans actie en moet u de nieuwe trans actie door voeren of terugdraaien voordat u wijzigingen aanbrengt in de oorspronkelijke trans actie.

De cmdlet **Start-Trans Action** is een van een set cmdlets die ondersteuning biedt voor de trans actions-functie in Windows Power shell.
Zie about_Transactions voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: een trans actie starten en terugdraaien

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Undo-Transaction
```

Deze opdrachten worden gestart en de trans actie wordt teruggedraaid.
Omdat de trans actie ongedaan wordt gemaakt, worden er geen wijzigingen in het REGI ster aangebracht.

### Voor beeld 2: een trans actie starten en volt ooien

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Complete-Transaction
```

Deze opdrachten beginnen en volt ooien een trans actie.
Er worden geen wijzigingen aangebracht in het REGI ster tot de opdracht **volt ooien-trans actie** wordt gebruikt.

### Voor beeld 3: verschillende terugdraai voorkeuren gebruiken

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction -RollbackPreference never
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction

# Start-Transaction (-rollbackpreference error)

PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
New-Item : The registry key at the specified path does not exist.
At line:1 char:9
+ new-item <<<<  -Path NoPath -Name ContosoCompany -UseTransaction

PS HKCU:\software> New-Item -Path . -Name "Contoso" -UseTransaction

New-Item : Cannot use transaction. The transaction has been rolled back or has timed out.
At line:1 char:9
+ new-item <<<<  -Path . -Name ContosoCompany -UseTransaction

# Start-Transaction (-rollbackpreference never)

PS HKCU:\software> Start-Transaction -RollbackPreference never
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction

New-Item : The registry key at the specified path does not exist.
At line:1 char:9
+ new-item <<<<  -Path NoPath -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany                 {}
PS HKCU:\Software> Complete-Transaction

# Succeeds
```

Dit voor beeld toont het effect van het wijzigen van de waarde van de para meter *RollbackPreference* .

In de eerste set met opdrachten maakt **Start-trans actie** geen gebruik van *RollbackPreference*.
Als gevolg hiervan wordt de standaard waarde (fout) gebruikt.
Als er een fout optreedt in een trans actie-opdracht, dat wil zeggen dat het opgegeven pad niet bestaat, wordt de trans actie automatisch teruggezet.

In de tweede set opdrachten maakt **Start-trans actie** gebruik van *RollbackPreference* met de waarde nooit.
Als er een fout optreedt in een trans actie-opdracht, is de trans actie dus nog actief en kan deze worden voltooid.

Omdat de meeste trans acties zonder fouten moeten worden uitgevoerd, is de standaard waarde van *RollbackPreference* doorgaans de voor keur.

### Voor beeld 4: deze cmdlet gebruiken terwijl een trans actie wordt uitgevoerd

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction
PS HKCU:\software> Get-Transaction
PS HKCU:\software> New-Item "ContosoCompany2" -UseTransaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\Software> Get-Transaction
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active
```

Dit voor beeld toont het effect van het gebruik van **Start-trans actie** terwijl een trans actie wordt uitgevoerd.
Het effect is vergelijkbaar met het samen voegen van de trans actie die wordt uitgevoerd.

Hoewel dit een vereenvoudigde opdracht is, treedt dit scenario vaak op wanneer de trans actie een script uitvoert dat een volledige trans actie bevat.

Met de eerste **Start-trans actie** opdracht wordt de trans actie gestart.
De eerste opdracht **Nieuw item** maakt deel uit van de trans actie.

Met de tweede **Start-trans actie** opdracht wordt een nieuwe abonnee toegevoegd aan de trans actie.
De opdracht **Get-trans actie** retourneert nu een trans actie met het aantal abonnee 2.
De tweede opdracht **Nieuw item** maakt deel uit van dezelfde trans actie.

Er worden geen wijzigingen aangebracht in het REGI ster tot de hele trans actie is voltooid.
Als u de trans actie wilt volt ooien, moet u twee opdrachten voor **volt ooien van trans acties** invoeren, één voor elke abonnee.
Als u de trans actie op elk gewenst moment terugdraait, wordt de trans actie teruggedraaid voor beide abonnees.

### Voor beeld 5: een onafhankelijke trans actie starten terwijl er een wordt uitgevoerd

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction -Independent
PS HKCU:\software> Get-Transaction
PS HKCU:\software> Undo-Transaction
PS HKCU:\software> New-ItemProperty -Path "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
PS HKCU:\software> Undo-Transaction
PS HKCU:\software> New-ItemProperty -Path "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
MyKey
-----
123
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   1 MyCompany                      {MyKey}
```

Dit voor beeld toont het effect van het gebruik van de *onafhankelijke* para meter van de **Start-trans actie** om een trans actie te starten terwijl een andere trans actie wordt uitgevoerd.
In dit geval wordt de nieuwe trans actie teruggedraaid zonder dat dit van invloed is op de oorspronkelijke trans actie.

Hoewel de trans acties logisch onafhankelijk zijn, omdat er slechts één trans actie tegelijk actief kan zijn, moet u de nieuwste trans actie terugdraaien of door voeren voordat u de oorspronkelijke trans actie opnieuw kunt gebruiken.

Met de eerste set opdrachten wordt een trans actie gestart.
De opdracht **Nieuw item** maakt deel uit van de eerste trans actie.

In de tweede set met opdrachten maakt de **Start-trans actie** opdracht gebruik van de *onafhankelijke* para meter.
Met de opdracht **Get-trans actie** die volgt, wordt het transactie object voor de actieve trans actie weer gegeven. Dit is de nieuwste.
Het aantal abonnees is gelijk aan 1, waarmee wordt aangegeven dat de trans acties niet gerelateerd zijn.

Wanneer de actieve trans actie wordt teruggedraaid met een opdracht voor **ongedaan maken** van de trans actie, wordt de oorspronkelijke trans actie weer actief.

De opdracht **Nieuw-item Property** , die deel uitmaakt van de oorspronkelijke trans actie, eindigt zonder fout en de oorspronkelijke trans actie kan worden voltooid met behulp van de opdracht **volt ooien trans actie** .
Als gevolg hiervan wordt het REGI ster gewijzigd.

### Voor beeld 6: opdrachten uitvoeren die geen deel uitmaken van een trans actie

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany1" -UseTransaction
PS HKCU:\software> New-Item "ContosoCompany2"
PS HKCU:\software> New-Item "ContosoCompany3" -UseTransaction
PS HKCU:\software> dir contoso*
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
PS HKCU:\Software> dir contoso*

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany2                {}

PS HKCU:\Software> Complete-Transaction
PS HKCU:\Software> dir contoso*

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany1                     {}
0   0 ContosoCompany2                     {}
0   0 ContosoCompany3                     {}
```

In dit voor beeld ziet u dat opdrachten die worden verzonden terwijl een trans actie wordt uitgevoerd, kunnen worden opgenomen in de trans actie of niet worden opgenomen.
Alleen opdrachten die gebruikmaken van de para meter *UseTransaction* , maken deel uit van de trans actie.

De eerste en derde opdracht voor **nieuwe items** gebruiken de para meter *UseTransaction* .
Deze opdrachten maken deel uit van de trans actie.
Omdat de tweede opdracht **Nieuw item** geen gebruikmaakt van de para meter *UseTransaction* , maakt deze geen deel uit van de trans actie.

Met de eerste opdracht dir wordt het effect weer gegeven.
De tweede opdracht **Nieuw item** wordt onmiddellijk voltooid, maar de eerste en derde opdrachten voor **Nieuw item** zijn pas van kracht als de trans actie is doorgevoerd.

Met de opdracht **volt ooien-trans actie** wordt de trans actie doorgevoerd.
Als gevolg hiervan wordt met de tweede opdracht dir aangegeven dat alle nieuwe items aan het REGI ster worden toegevoegd.

### Voor beeld 7: terugdraaien van een trans actie die niet binnen een opgegeven tijd eindigt

```
PS C:\> Start-Transaction -Timeout 2

# Wait two minutes...

PS C:\> Get-Transaction
PS C:\> New-Item HKCU:\Software\ContosoCompany -UseTransaction
PS C:\> Start-Transaction -Timeout 2

# Wait two minutes...

PS C:\> > Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----------
Error                1                 RolledBack

PS C:\> New-Item HKCU:\Software\ContosoCompany -UseTransaction

New-Item : Cannot use transaction. The transaction has been rolled back or has timed out.
At line:1 char:9
+ new-item <<<<  MyCompany -UseTransaction
```

Met deze opdracht wordt de para meter *time-out* van de **Start-trans actie** gebruikt om een trans actie te starten die binnen twee minuten moet worden voltooid.
Als de trans actie niet is voltooid wanneer de time-outperiode is verlopen, wordt deze automatisch teruggezet.

Wanneer de time-out is verlopen, wordt u niet gewaarschuwd, maar de eigenschap **status** van het transactie object wordt ingesteld op teruggedraaid en opdrachten die de para meter *UseTransaction* gebruiken mislukken.

## PARAMETERS

### -Onafhankelijk
Geeft aan dat deze cmdlet een trans actie start die onafhankelijk is van trans acties die worden uitgevoerd.
Als u **Start-trans actie** gebruikt terwijl er een andere trans actie wordt uitgevoerd, wordt standaard een nieuwe abonnee toegevoegd aan de trans actie die wordt uitgevoerd.
Deze para meter heeft alleen effect wanneer er al een trans actie in de sessie wordt uitgevoerd.

Als u **Start-trans actie** gebruikt terwijl een trans actie wordt uitgevoerd, wordt standaard het bestaande transactie object opnieuw gebruikt en wordt het aantal abonnees verhoogd.
Het effect is vergelijkbaar met het samen voegen van de oorspronkelijke trans actie.
Met een Undo-Transaction-opdracht wordt de hele trans actie teruggedraaid.
Als u de trans actie wilt volt ooien, moet u een Complete-Transaction-opdracht voor elke abonnee opgeven.
Omdat de meeste trans acties die op hetzelfde moment worden uitgevoerd, aan elkaar zijn gerelateerd, is de standaard waarde voldoende voor het meest gebruik.

Als u de *onafhankelijke* para meter opgeeft, maakt deze cmdlet een nieuwe trans actie die kan worden voltooid of ongedaan worden gemaakt zonder dat dit van invloed is op de oorspronkelijke trans actie.
Omdat echter slechts één trans actie tegelijk actief kan zijn, moet u de nieuwe trans actie volt ooien of terugdraaien voordat u het werk voor de oorspronkelijke trans actie hervat.

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

### -RollbackPreference
Hiermee geeft u de voor waarden voor het automatisch terugdraaien van een trans actie.
De aanvaardbare waarden voor deze parameter zijn:

- Fout.
De trans actie wordt automatisch teruggedraaid als er sprake is van een afsluitende of niet-afsluit fout.
- TerminatingError.
De trans actie wordt automatisch teruggezet als er een afsluit fout optreedt.
- Schreven.
De trans actie wordt nooit automatisch hersteld.

De standaard waarde is fout.

```yaml
Type: System.Management.Automation.RollbackSeverity
Parameter Sets: (All)
Aliases:
Accepted values: Error, TerminatingError, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Time-out
Hiermee wordt de maximale tijds duur, in minuten, opgegeven dat de trans actie actief is.
Wanneer de time-outperiode is verlopen, wordt de trans actie automatisch teruggezet.

Standaard is er geen time-out voor trans acties die worden gestart op de opdracht regel.
Wanneer trans acties door een script worden gestart, is de standaard time-out 30 minuten.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutMins

Required: False
Position: Named
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
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen
U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### Geen
Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Volt ooien-trans actie](Complete-Transaction.md)

[Get-trans actie](Get-Transaction.md)

[Ongedaan maken-trans actie](Undo-Transaction.md)

[Gebruik-trans actie](Use-Transaction.md)
