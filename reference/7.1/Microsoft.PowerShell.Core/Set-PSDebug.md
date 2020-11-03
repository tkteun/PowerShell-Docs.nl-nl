---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-psdebug?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSDebug
ms.openlocfilehash: a0b5d7e86f9d63b487bc093feb18ecc7a4496999
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251186"
---
# Set-PSDebug

## SAMENVATTING
Schakelt functies voor fout opsporing in scripts in-en uitschakelen, stelt het tracerings niveau in en schakelt de strikte modus in.

## SYNTAXIS

### op

```
Set-PSDebug [-Trace <Int32>] [-Step] [-Strict] [<CommonParameters>]
```

### uit

```
Set-PSDebug [-Off] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Set-PSDebug` cmdlet worden functies voor fout opsporing in scripts in-en uitgeschakeld, wordt het tracerings niveau ingesteld en wordt de strikte modus ingeschakeld. De Power shell-functies voor fout opsporing zijn standaard uitgeschakeld.

Wanneer de **tracerings** parameter een waarde van heeft `1` , wordt elke regel van het script getraceerd wanneer deze wordt uitgevoerd. Wanneer de para meter een waarde heeft `2` , worden er ook variabele toewijzingen, functie aanroepen en script aanroepen getraceerd. Als de **stap** parameter is opgegeven, wordt u gevraagd om elke regel van het script wordt uitgevoerd.

## VOORBEELDEN

### Voor beeld 1: het tracerings niveau instellen

In dit voor beeld wordt het tracerings niveau ingesteld op `2` en wordt vervolgens een script uitgevoerd dat de getallen 1, 2 en bevat.
3.

```powershell
Set-PSDebug -Trace 2; foreach ($i in 1..3) {$i}
```

```Output
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in  >>>> 1..3) {$i}
DEBUG:     ! SET $foreach = 'IEnumerator'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '1'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
1
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '2'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
2
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '3'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
3
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $foreach = ''.
```

### Voor beeld 2: Step Ping inschakelen

In dit voor beeld wordt Step ping ingeschakeld en wordt vervolgens een script uitgevoerd waarin de getallen 1, 2 en 3 worden weer gegeven.

```powershell
Set-PSDebug -Step; foreach ($i in 1..3) {$i}
```

```Output
Continue with this operation?
   1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): A
DEBUG:    1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
1
2
3
```

### Voor beeld 3: strikte modus gebruiken

In dit voor beeld wordt Power shell in de strikte modus geplaatst en wordt geprobeerd toegang te krijgen tot een variabele waaraan geen waarde is toegewezen.

```powershell
Set-PSDebug -Strict; $NewVar
```

```Output
The variable '$NewVar' cannot be retrieved because it has not been set.
At line:1 char:22
+ Set-PSDebug -Strict; $NewVar
```

### Voor beeld 4: functies voor fout opsporing uitschakelen

In dit voor beeld worden alle functies voor fout opsporing uitgeschakeld en wordt vervolgens een script uitgevoerd waarin de getallen 1, 2 en 3 worden weer gegeven.

```powershell
Set-PSDebug -Off; foreach ($i in 1..3) {$i}
```

```Output
1
2
3
```

## PARAMETERS

### -Uit

Hiermee schakelt u alle functies voor fout opsporing in scripts uit.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: off
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Stap

Hiermee schakelt u script steping in. Voordat elke regel wordt uitgevoerd, wordt u door Power shell gevraagd om te stoppen, door te gaan of een nieuw interpreter niveau in te voeren om de status van het script te controleren.

Als u de para meter **stap** opgeeft, wordt automatisch een tracerings niveau ingesteld `1` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Strikte

Hiermee geeft u aan dat aan variabelen een waarde moet worden toegewezen voordat ernaar wordt verwezen in een script. Als er wordt verwezen naar een variabele voordat een waarde wordt toegewezen, retourneert Power shell een uitzonderings fout. Dit is gelijk aan `Set-StrictMode -Version 1` . Zie [set-StrictMode](Set-StrictMode.md)voor meer informatie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Traceren

Hiermee geeft u het tracerings niveau voor elke regel in een script. Elke regel wordt getraceerd terwijl deze wordt uitgevoerd.

De acceptabele waarden voor deze para meter zijn als volgt:

- 0: script tracering uitschakelen.
- 1: Traceer script regels wanneer ze worden uitgevoerd.
- 2: Traceer script regels, toewijzing van variabelen, functie aanroepen en scripts.

```yaml
Type: System.Int32
Parameter Sets: on
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

U kunt geen pijplijn invoer voor deze cmdlet.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer geretourneerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[about_Debuggers](./About/about_Debuggers.md)

[Debug-proces](../Microsoft.PowerShell.Management/Debug-Process.md)

[Set-PSBreakpoint](../Microsoft.PowerShell.Utility/Set-PSBreakpoint.md)

[Set-StrictMode](Set-StrictMode.md)

[Schrijf fouten opsporen](../Microsoft.PowerShell.Utility/Write-Debug.md)

