---
description: Hierin wordt uitgelegd hoe u lokale en externe variabelen gebruikt in externe opdrachten.
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Variables
ms.openlocfilehash: 1cd6d0c4562fcd63fc56f103ec41aa6f0bb4c01c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705791"
---
# <a name="about-remote-variables"></a>Over externe variabelen

## <a name="short-description"></a>Korte beschrijving

Hierin wordt uitgelegd hoe u lokale en externe variabelen gebruikt in externe opdrachten.

## <a name="long-description"></a>Lange beschrijving

U kunt variabelen gebruiken in opdrachten die u uitvoert op externe computers. Wijs een waarde toe aan de variabele en gebruik vervolgens de variabele in plaats van de waarde.

Standaard worden de variabelen in externe opdrachten geacht te zijn gedefinieerd in de sessie die de opdracht uitvoert. Variabelen die in een lokale sessie worden gedefinieerd, moeten worden aangeduid als lokale variabelen in de opdracht.

## <a name="using-remote-variables"></a>Externe variabelen gebruiken

In Power shell wordt ervan uitgegaan dat de variabelen die worden gebruikt in externe opdrachten worden gedefinieerd in de sessie waarin de opdracht wordt uitgevoerd.

In dit voor beeld `$ps` wordt de variabele gedefinieerd in de tijdelijke sessie waarin de `Get-WinEvent` opdracht wordt uitgevoerd.

```powershell
Invoke-Command -ComputerName S1 -ScriptBlock {
  $ps = "*PowerShell*"; Get-WinEvent -LogName $ps
}
```

Wanneer de opdracht wordt uitgevoerd in een permanente sessie, **PSSession**, moet de externe variabele in die sessie worden gedefinieerd.

```powershell
$s = New-PSSession -ComputerName S1
Invoke-Command -Session $s -ScriptBlock {$ps = "*PowerShell*"}
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $ps}
```

## <a name="using-local-variables"></a>Lokale variabelen gebruiken

U kunt lokale variabelen gebruiken in externe opdrachten, maar de variabele moet in de lokale sessie worden gedefinieerd.

Vanaf Power Shell 3,0 kunt u de `Using` Scope modificator gebruiken om een lokale variabele te identificeren in een externe opdracht.

De syntaxis van `Using` is als volgt:

```
$Using:<VariableName>
```

In het volgende voor beeld `$ps` wordt de variabele in de lokale sessie gemaakt, maar wordt deze gebruikt in de sessie waarin de opdracht wordt uitgevoerd. De `Using` wijzigings functie van het bereik identificeert `$ps` als een lokale variabele.

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  Get-WinEvent -LogName $Using:ps
}
```

De `Using` aanpassings functie voor bereik kan worden gebruikt in een **PSSession**.

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $Using:ps}
```

Een verwijzing naar een variabele, zoals wordt `$using:var` uitgebreid naar de waarde van de variabele `$var` van de context van de aanroeper. U krijgt geen toegang tot het object variable van de aanroeper.
De `Using` aanpassings functie voor bereik kan niet worden gebruikt voor het wijzigen van een lokale variabele in de **PSSession**. De volgende code werkt bijvoorbeeld niet:

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {$Using:ps = 'Cannot assign new value'}
```

`Using`Zie [about_Scopes](./about_Scopes.md) voor meer informatie over

### <a name="using-splatting"></a>Splatting gebruiken

Power shell splatting geeft een verzameling parameter namen en waarden door aan een opdracht. Zie [about_Splatting](about_Splatting.md)voor meer informatie.

In dit voor beeld is de variabele splatting `$Splat` een hash-tabel die is ingesteld op de lokale computer. De `Invoke-Command` verbinding met een externe computer sessie maken. De **script Block** gebruikt de `Using` aanpassings functie van het bereik met het symbool at ( `@` ) om de splatted-variabele weer te geven.

```powershell
$Splat = @{ Name = "Win*"; Include = "WinRM" }
Invoke-Command -Session $s -ScriptBlock { Get-Service @Using:Splat }
```

### <a name="other-situations-where-the-using-scope-modifier-is-needed"></a>Andere situaties waarin de aanpassings functie voor het gebruik van het bereik is vereist

Voor elk script of elke opdracht die uit de sessie wordt uitgevoerd, hebt u de `Using` bereik wijzigings functie nodig om variabele waarden van het aanroepende sessie bereik in te sluiten, zodat out of Session-code er toegang toe heeft. De `Using` aanpassing van het bereik wordt ondersteund in de volgende contexten:

- Extern uitgevoerde opdrachten, begonnen met `Invoke-Command` het gebruik van **ComputerName**, **hostname**, **SSHConnection** of **Session** para meters (externe sessie)
- Achtergrond taken, begonnen met `Start-Job` (out-of-process-sessie)
- Thread taken, gestart via `Start-ThreadJob` of `ForEach-Object -Parallel` (afzonderlijke thread sessie)

Afhankelijk van de context, zijn Inge sloten variabelen waarden ofwel onafhankelijke kopieën van de gegevens in het bereik of verwijzingen naar de aanroeper. In externe en out-of-process-sessies zijn ze altijd onafhankelijke kopieën. In thread sessies worden ze door gegeven door verwijzing.

## <a name="serialization-of-variable-values"></a>Serialisatie van variabele waarden

Extern uitgevoerde opdrachten en achtergrond taken worden out-of-process uitgevoerd.
Out-of-process-sessies gebruiken op XML gebaseerde serialisatie en deserialisatie om de waarden van variabelen beschikbaar te maken voor de grenzen van het proces. Het serialization-proces converteert objecten naar een **PSObject** die de eigenschappen van de oorspronkelijke objecten bevat, maar niet de methoden ervan.

Voor een beperkte set typen worden objecten door deserialisatie opnieuw naar het oorspronkelijke type gehydrateerd. Het opnieuw gehydrateerde object is een kopie van het oorspronkelijke object exemplaar.
Deze bevat de type-eigenschappen en-methoden. Voor eenvoudige typen, zoals **System. versie**, is de kopie gelijk. Voor complexe typen is de kopie niet perfect. Bijvoorbeeld: opnieuw gehydrateerde certificaat objecten bevatten niet de persoonlijke sleutel.

Exemplaren van alle andere typen zijn **PSObject** -exemplaren. De eigenschap **PSTypeNames** bevat de oorspronkelijke type naam, voorafgegaan door een **gedeserialiseerd**, bijvoorbeeld **Deserialized.System. Data. DataTable**

## <a name="using-local-variables-with-argumentlist-parameter"></a>Lokale variabelen gebruiken met de para meter **argument List**

U kunt lokale variabelen gebruiken in een externe opdracht door para meters voor de externe opdracht te definiëren en de para meter **argument List** van de `Invoke-Command` cmdlet te gebruiken om de lokale variabele als de parameter waarde op te geven.

- Gebruik het `param` sleutel woord om para meters te definiëren voor de externe opdracht. De parameter namen zijn tijdelijke aanduidingen die niet moeten overeenkomen met de naam van de lokale variabele.

- Gebruik de para meters die zijn gedefinieerd door het `param` sleutel woord in de opdracht.

- Gebruik de para meter **argument List** van de `Invoke-Command` cmdlet om de lokale variabele op te geven als de parameter waarde.

De volgende opdrachten definiëren bijvoorbeeld de `$ps` variabele in de lokale sessie en gebruiken deze vervolgens in een externe opdracht. De opdracht wordt gebruikt `$log` als de parameter naam en de lokale variabele, `$ps` als waarde.

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  param($log)
  Get-WinEvent -LogName $log
} -ArgumentList $ps
```

## <a name="see-also"></a>Zie ook

[about_PSSessions](about_PSSessions.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[about_Splatting](about_Splatting.md)

[about_Variables](about_Variables.md)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Invoke-opdracht](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Start-ThreadJob](xref:ThreadJob.Start-ThreadJob)

@Microsoft.PowerShell.Core.ForEach-Object

