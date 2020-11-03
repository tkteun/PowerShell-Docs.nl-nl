---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Transaction
ms.openlocfilehash: bb8e9e1f204c67207f31613181f856d3bcaf8dc3
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93247175"
---
# Get-Transaction

## SAMENVATTING
Hiermee wordt de huidige (actieve) trans actie opgehaald.

## SYNTAXIS

```
Get-Transaction [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **Get-trans actie** haalt een object op dat de huidige trans actie in de sessie vertegenwoordigt.

Deze cmdlet retourneert nooit meer dan één object, omdat er slechts één trans actie tegelijk actief is.
Als u een of meer onafhankelijke trans acties start (met behulp van de onafhankelijke para meter van de start-trans actie), is de laatst gestarte trans actie actief en is de trans actie die wordt **opgehaald-trans actie** geretourneerd.

Wanneer alle actieve trans acties zijn teruggedraaid of doorgevoerd, wordt in deze cmdlet de trans actie weer gegeven die het meest recent actief was in de sessie.

Deze cmdlet is een van een set cmdlets die ondersteuning biedt voor de trans actions-functie in Windows Power shell.
Zie about_Transactions voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: de huidige trans actie ophalen

```
PS C:\> Start-Transaction
PS C:\> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

Met deze opdracht wordt de cmdlet Get-Transaction gebruikt om de huidige trans actie op te halen.

### Voor beeld 2: de eigenschappen en methoden van het transactie object weer geven

```
PS C:\> Get-Transaction | Get-Member

Name               MemberType Definition
----               ---------- ----------
Dispose            Method     System.Void Dispose(), System.Void Dispose(Boolean disposing)
Equals             Method     System.Boolean Equals(Object obj)
GetHashCode        Method     System.Int32 GetHashCode()
GetType            Method     System.Type GetType()
ToString           Method     System.String ToString()
IsCommitted        Property   System.Boolean IsCommitted {get;}
IsRolledBack       Property   System.Boolean IsRolledBack {get;}
RollbackPreference Property   System.Management.Automation.RollbackSeverity RollbackPreference {get;}
SubscriberCount    Property   System.Int32 SubscriberCount {get;set;}
```

Met deze opdracht wordt de Get-Member-cmdlet gebruikt om de eigenschappen en methoden van het transactie object weer te geven.

### Voor beeld 3: de eigenschaps waarden van een teruggedraaide trans actie weer geven

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Undo-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ----------
Error                0                 RolledBack
```

Met deze opdracht worden de eigenschaps waarden weer gegeven van een transactie object voor een trans actie die is teruggedraaid.

### Voor beeld 4: de eigenschaps waarden van een vastgelegde trans actie weer geven

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ---------
Error                1                 Committed
```

Met deze opdracht worden de eigenschaps waarden van een transactie object weer gegeven voor een trans actie die is doorgevoerd.

### Voor beeld 5: een trans actie starten terwijl een andere wordt uitgevoerd

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany2 -UseTransaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ---------
Error                1                 Committed
```

In dit voor beeld ziet u het effect van het transactie object van het starten van een trans actie terwijl er een andere trans actie wordt uitgevoerd.
Dit gebeurt meestal wanneer een script dat een trans actie uitvoert een functie bevat of een script aanroept dat een andere volledige trans actie bevat.

Tenzij de tweede **Start-trans actie** opdracht de *onafhankelijke* para meter bevat, wordt door **Start-trans actie** geen nieuwe trans actie gemaakt.
In plaats daarvan wordt een tweede abonnee toegevoegd aan de oorspronkelijke trans actie.

Met de eerste **Start-trans actie** opdracht wordt de trans actie gestart.
Een New-Item opdracht met de para meter *UseTransaction* maakt deel uit van de trans actie.

Een tweede **Start-trans actie-** opdracht voegt een abonnee aan de trans actie toe.
De volgende New-Item-opdracht maakt ook deel uit van de trans actie.

Met de eerste **Get-trans** actie opdracht wordt de trans actie met meerdere abonnees weer gegeven.
U ziet dat het aantal abonnees 2 is.

Met de eerste Complete-Transaction opdracht wordt de trans actie niet door voeren, maar het aantal abonnees wordt beperkt tot 1.

De tweede opdracht **volt ooien trans** actie voert de trans actie door.

### Voor beeld 6: een onafhankelijke trans actie starten terwijl een andere wordt uitgevoerd

```
PS C:\>
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   IsRolledBack   IsCommitted
------------------   ---------------   ------------   -----------
Error                1                 False          False

HKLM:\SOFTWARE> Start-Transaction -Independent
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   IsRolledBack   IsCommitted
------------------   ---------------   ------------   -----------
Error                1                 False          False

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction
HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction
```

In dit voor beeld ziet u het effect van het transactie object van het starten van een onafhankelijke trans actie terwijl een andere trans actie wordt uitgevoerd.

Met de eerste **Start-trans actie** opdracht wordt de trans actie gestart.
Een **nieuwe item** opdracht met de para meter *UseTransaction* maakt deel uit van de trans actie.

Een tweede **Start-trans actie-** opdracht voegt een abonnee aan de trans actie toe.
De volgende opdracht voor het **nieuwe item** maakt ook deel uit van de trans actie.

Met de eerste **Get-trans** actie opdracht wordt de trans actie met meerdere abonnees weer gegeven.
Houd er rekening mee dat het aantal abonnees 2 is.

De opdracht **volt ooien-trans actie** reduceert het aantal abonnees tot 1, maar voert de trans actie niet door.

De tweede opdracht **volt ooien trans** actie voert de trans actie door.

## PARAMETERS

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen
U kunt geen objecten naar deze cmdlet pipeen.

## UITVOER

### System. Management. Automation. PSTransaction
Met deze cmdlet wordt een object geretourneerd dat de huidige trans actie vertegenwoordigt.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Volt ooien-trans actie](Complete-Transaction.md)

[Start-trans actie](Start-Transaction.md)

[Ongedaan maken-trans actie](Undo-Transaction.md)

[Gebruik-trans actie](Use-Transaction.md)

[Nieuw-item](New-Item.md)
