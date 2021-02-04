---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-argumentcompleter?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ArgumentCompleter
ms.openlocfilehash: c81c50152209a922c486005b5919ac4a1e7295a2
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490312"
---
# Register-ArgumentCompleter

## SAMENVATTING

Hiermee registreert u een volledig aangepaste argument.

## SYNTAXIS

### Systeem eigenset

```
Register-ArgumentCompleter -CommandName <String[]> -ScriptBlock <ScriptBlock> [-Native]
 [<CommonParameters>]
```

### Power shell-set

```
Register-ArgumentCompleter [-CommandName <String[]>] -ParameterName <String>
 -ScriptBlock <ScriptBlock> [<CommonParameters>]
```

## BESCHRIJVING

De `Register-ArgumentCompleter` cmdlet registreert een volledig aangepaste argument. Met de functie voor het argument voltooid kunt u tijdens runtime dynamische tabblad voltooiing opgeven voor elke opdracht die u opgeeft.

## VOORBEELDEN

### Voor beeld 1: een volledig aangepaste argument registreren

In het volgende voor beeld wordt een argument voltooid geregistreerd voor de para meter **id** van de `Set-TimeZone` cmdlet.

```powershell
$scriptBlock = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)

    (Get-TimeZone -ListAvailable).Id | Where-Object {
        $_ -like "$wordToComplete*"
    } | ForEach-Object {
          "'$_'"
    }
}
Register-ArgumentCompleter -CommandName Set-TimeZone -ParameterName Id -ScriptBlock $scriptBlock
```

Met de eerste opdracht maakt u een script blok waarbij de vereiste para meters worden gebruikt die worden door gegeven wanneer de gebruiker op het <kbd>tabblad</kbd>klikt. Zie de beschrijving van de para meter **script Block** voor meer informatie.

Binnen het script blok worden de beschik bare waarden voor **id** opgehaald met behulp van de `Get-TimeZone` cmdlet. De eigenschap **id** voor elke tijd zone wordt door gegeven aan de `Where-Object` cmdlet. De `Where-Object` cmdlet filtert alle id's die niet beginnen met de waarde die is opgegeven door `$wordToComplete` , die de tekst bevat die de gebruiker heeft getypt voordat ze op <kbd>Tab</kbd>werden gedrukt. De gefilterde id's worden door gegeven aan de `ForEach-Object` cmdlet die elke waarde in de aanhalings tekens omsluit, wanneer de waarde spaties bevat.

Met de tweede opdracht wordt het argument completer geregistreerd door de script Block, de **para meter** **-id** en de **opdracht** naam door te geven `Set-TimeZone` .

### Voor beeld 2: Details toevoegen aan de waarden voor het volt ooien van het tabblad

In het volgende voor beeld wordt het volt ooien van het tabblad voor de para meter **name** van de cmdlet overschreven `Stop-Service` en worden alleen actieve services geretourneerd.

```powershell
$s = {
    param($commandName, $parameterName, $wordToComplete, $commandAst, $fakeBoundParameters)
    $services = Get-Service | Where-Object {$_.Status -eq "Running" -and $_.Name -like "$wordToComplete*"}
    $services | ForEach-Object {
        New-Object -Type System.Management.Automation.CompletionResult -ArgumentList $_.Name,
            $_.Name,
            "ParameterValue",
            $_.Name
    }
}
Register-ArgumentCompleter -CommandName Stop-Service -ParameterName Name -ScriptBlock $s
```

Met de eerste opdracht maakt u een script blok waarbij de vereiste para meters worden gebruikt die worden door gegeven wanneer de gebruiker op het <kbd>tabblad</kbd>klikt. Zie de beschrijving van de para meter **script Block** voor meer informatie.

In het-script blok haalt de eerste opdracht alle actieve services op met de `Where-Object` cmdlet. De services worden door gegeven aan de `ForEach-Object` cmdlet. `ForEach-Object`Met de cmdlet wordt een nieuw [System. Management. Automation. CompletionResult](/dotnet/api/system.management.automation.completionresult) -object gemaakt en gevuld met de naam van de huidige service (vertegenwoordigd door de pijplijn variabele `$_.Name` ).

Met het **CompletionResult** -object kunt u aanvullende Details voor elke geretourneerde waarde opgeven:

- **completionText** (teken reeks): de tekst die moet worden gebruikt als resultaat van automatisch volt ooien. Dit is de waarde die wordt verzonden naar de opdracht.
- **listItemText** (teken reeks): de tekst die moet worden weer gegeven in een lijst, bijvoorbeeld wanneer de gebruiker op de <kbd>CTRL</kbd>- + <kbd>spatie</kbd>klikt. Dit wordt alleen gebruikt voor weer gave en wordt niet door gegeven aan de opdracht wanneer deze is geselecteerd.
- **resultType** ([CompletionResultType](/dotnet/api/system.management.automation.completionresulttype)): het type voltooiings resultaat.
- **knop info** (teken reeks): de tekst voor de knop info met details die moeten worden weer gegeven over het object.
  Dit is zichtbaar wanneer de gebruiker een item selecteert nadat u op <kbd>CTRL</kbd>-spatie hebt gedrukt + <kbd></kbd>.

Met de laatste opdracht wordt gedemonstreerd dat gestopte services nog steeds hand matig kunnen worden door gegeven aan de `Stop-Service` cmdlet. Het vullen van het tabblad is alleen van invloed op het onderhouds aspect.

### Voor beeld 3: een aangepaste systeem eigen argument voor de volledige functie registreren

U kunt de **systeem eigen** para meter gebruiken om het volt ooien van een opdracht in te stellen. In het volgende voor beeld wordt het volt ooien van het tabblad voor de `dotnet` opdracht regel interface (CLI) toegevoegd.

> [!NOTE]
> De `dotnet complete` opdracht is alleen beschikbaar in versie 2,0 en hoger van de DotNet-cli.

```powershell
$scriptblock = {
    param($wordToComplete, $commandAst, $cursorPosition)
        dotnet complete --position $cursorPosition $commandAst.ToString() | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
        }
}
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock $scriptblock
```

Met de eerste opdracht maakt u een script blok waarbij de vereiste para meters worden gebruikt die worden door gegeven wanneer de gebruiker op het <kbd>tabblad</kbd>klikt. Zie de beschrijving van de para meter **script Block** voor meer informatie.

In het-script blok `dotnet complete` wordt de opdracht gebruikt om het volt ooien van het tabblad uit te voeren.
De resultaten worden door gegeven aan de `ForEach-Object` cmdlet die gebruikmaakt van de **nieuwe** statische methode van de klasse [System. Management. Automation. CompletionResult](/dotnet/api/system.management.automation.completionresult) om voor elke waarde een nieuw **CompletionResult** -object te maken.

## PARAMETERS

### -Opdrachtnaam

Hiermee geeft u de naam van de opdrachten als een matrix.

```yaml
Type: System.String[]
Parameter Sets: NativeSet, PowerShellSet
Aliases:

Required: True (NativeSet), False (PowerShellSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Systeem eigen

Geeft aan dat het argument volledig is voor een systeem eigen opdracht waarbij Power shell geen parameter namen kan volt ooien.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NativeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Para meternaam

Hiermee geeft u de naam van de para meter op waarvan het argument wordt voltooid. De opgegeven parameter naam kan geen opsommings waarde zijn, zoals de para meter **ForegroundColor** van de `Write-Host` cmdlet.

Zie [about_Enum](./About/about_Enum.md)voor meer informatie over enums.

```yaml
Type: System.String
Parameter Sets: PowerShellSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Script Block

Hiermee geeft u de opdrachten op die moeten worden uitgevoerd om de tabblad voltooiing uit te voeren. Het script blok dat u opgeeft, moet de waarden retour neren die de invoer hebben voltooid. Het script blok moet de waarden van de pijp lijn ( `ForEach-Object` , `Where-Object` enzovoort) of een andere geschikte methode ongedaan maken. Als u een matrix met waarden retourneert, wordt de gehele matrix als **één** waarde voor het volt ooien van een tab behandeld.

Het script blok moet de volgende para meters accepteren in de opgegeven volg orde. De namen van de para meters zijn niet belang rijk omdat Power shell in de waarden van de positie wordt door gegeven.

- `$commandName` (Positie 0): deze para meter is ingesteld op de naam van de opdracht waarvoor het script blok het volt ooien van het tabblad oplevert.
- `$parameterName` (Positie 1)-deze para meter wordt ingesteld op de para meter waarvan de waarde het volt ooien van het tabblad vereist.
- `$wordToComplete` (Positie 2): deze para meter is ingesteld op waarde die de gebruiker heeft opgegeven voordat deze <kbd>Tab</kbd>werd ingedrukt. Het script blok moet deze waarde gebruiken om de waarden voor het volt ooien van tabs te bepalen.
- `$commandAst` (Positie 3): deze para meter is ingesteld op de abstracte syntaxis structuur (AST) voor de huidige invoer regel. Zie [AST class](/dotnet/api/system.management.automation.language.ast)(Engelstalig) voor meer informatie.
- `$fakeBoundParameters` (Positie 4): deze para meter is ingesteld op een hashtabel die de `$PSBoundParameters` voor de cmdlet bevat, voordat het <kbd>tabblad</kbd>van de gebruiker wordt ingedrukt. Zie [about_Automatic_Variables](./About/about_Automatic_Variables.md)voor meer informatie.

Wanneer u de **systeem eigen** para meter opgeeft, moet het script blok de volgende para meters in de opgegeven volg orde hebben. De namen van de para meters zijn niet belang rijk omdat Power shell in de waarden van de positie wordt door gegeven.

- `$wordToComplete` (Positie 0): deze para meter is ingesteld op waarde die de gebruiker heeft opgegeven voordat deze <kbd>Tab</kbd>werd ingedrukt. Het script blok moet deze waarde gebruiken om de waarden voor het volt ooien van tabs te bepalen.
- `$commandAst` (Positie 1): deze para meter is ingesteld op de abstracte syntaxis structuur (AST) voor de huidige invoer regel. Zie [AST class](/dotnet/api/system.management.automation.language.ast)(Engelstalig) voor meer informatie.
- `$cursorPosition` (Positie 2): deze para meter wordt ingesteld op de positie van de cursor wanneer het <kbd>tabblad</kbd>van de gebruiker wordt ingedrukt.

U kunt ook een **ArgumentCompleter** als parameter kenmerk opgeven. Zie [about_Functions_Advanced_Parameters](./About/about_Functions_Advanced_Parameters.md)voor meer informatie.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](./About/about_CommonParameters.md)voor meer informatie.

## INVOER

### Geen

U kunt geen objecten naar deze cmdlet pipeen.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer geretourneerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN
