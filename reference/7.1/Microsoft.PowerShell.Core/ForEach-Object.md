---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: e1680e5ad182051bce217efd6f1eb48d44798146
ms.sourcegitcommit: 366304d096c1caf52f0e17962f6ed23d20f86e7b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2021
ms.locfileid: "107543837"
---
# ForEach-Object

## Synopsis
Voert een bewerking uit op elk item in een verzameling invoerobjecten.

## Syntax

### ScriptBlockSet (standaard)

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PropertyAndMethodSet

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ParallelParameterSet

```
ForEach-Object -Parallel <scriptblock> [-InputObject <PSObject>] [-ThrottleLimit <int>]
[-UseNewRunspace] [-TimeoutSeconds <int>] [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

De `ForEach-Object` cmdlet voert een bewerking uit op elk item in een verzameling invoerobjecten. De invoerobjecten kunnen worden doorgegeven aan de cmdlet of worden opgegeven met behulp van de **parameter InputObject.**

Vanaf Windows PowerShell 3.0 zijn er twee verschillende manieren om een opdracht te `ForEach-Object` maken.

- **Scriptblok.** U kunt een scriptblok gebruiken om de bewerking op te geven. Gebruik in het scriptblok de variabele `$_` om het huidige object weer te geven. Het scriptblok is de waarde van de **procesparameter.** Het scriptblok kan elk PowerShell-script bevatten.

  Met de volgende opdracht wordt bijvoorbeeld de waarde van de eigenschap **ProcessName** van elk proces op de computer opgeslagen.

  `Get-Process | ForEach-Object {$_.ProcessName}`

  `ForEach-Object` ondersteunt de `begin` blokken , en zoals `process` `end` beschreven in [about_functions](about/about_functions.md#piping-objects-to-functions).

  > [!NOTE]
  > De scriptblokken worden uitgevoerd in het bereik van de aanroeper. Daarom hebben de blokken toegang tot variabelen in dat bereik en kunnen nieuwe variabelen worden gemaakt die in dat bereik blijven bestaan nadat de cmdlet is voltooid.

- **Bewerkings-instructie**. U kunt ook een bewerkingsverklaring schrijven, die veel meer lijkt op natuurlijke taal. U kunt de bewerkings-instructie gebruiken om een eigenschapswaarde op te geven of een methode aan te roepen. Bewerkingsverklaringen zijn geïntroduceerd in Windows PowerShell 3.0.

  Met de volgende opdracht wordt bijvoorbeeld ook de waarde van de eigenschap **ProcessName** van elk proces op de computer opgeslagen.

  `Get-Process | ForEach-Object ProcessName`

- **Parallel uitvoerend scriptblok**. Vanaf PowerShell 7.0 is er een derde parameterset beschikbaar die elk scriptblok parallel wordt uitgevoerd. Met **de parameter ThrottleLimit** beperkt u het aantal parallelle scripts dat tegelijk wordt uitgevoerd. Net als voorheen gebruikt u de `$_` variabele om het huidige invoerobject in het scriptblok weer te geven. Gebruik het `$using:` trefwoord om variabeleverwijzingen door te geven aan het script dat wordt uitgevoerd.

  In PowerShell 7 wordt voor elke lus-iteratie een nieuwe runspace gemaakt om maximale isolatie te garanderen.
  Dit kan een grote prestatie- en resource-hit zijn als het werk dat u doet klein is in vergelijking met het maken van nieuwe runspaces of als er veel iteraties zijn die aanzienlijk werk verrichten. Vanaf PowerShell 7.1 worden runspaces uit een runspacegroep standaard opnieuw gebruikt. De grootte van de runspacegroep wordt opgegeven door de parameter **ThrottleLimit.** De standaardgrootte van de runspacegroep is 5. U kunt nog steeds een nieuwe runspace maken voor elke iteratie met behulp van **de switch UseNewRunspace.**

  De parallelle scriptblokkeringen gebruiken standaard de huidige werkmap van de aanroeper die de parallelle taken heeft gestart.

  Niet-beëindigingsfouten worden naar de foutstroom van de cmdlet geschreven wanneer deze zich voordoen in parallelle scriptblokkeringen. Omdat de uitvoeringsorder voor parallelle scriptblokkering niet kan worden bepaald, is de volgorde waarin fouten worden weergegeven in de foutstroom willekeurig. Berichten die naar andere gegevensstromen worden geschreven, zoals waarschuwing, uitgebreid of informatie, worden in een onbepaalde volgorde naar deze gegevensstromen geschreven.

  Het beëindigen van fouten, zoals uitzonderingen, beëindigt de afzonderlijke parallelle instantie van de scriptblokkeringen waarin ze optreden. Een beëindigingsfout in één scriptblokkering veroorzaakt mogelijk niet de beëindiging van de `Foreach-Object` cmdlet. De andere scriptblokkeringen, die parallel worden uitgevoerd, blijven actief, tenzij ze ook een beëindigingsfout tegenkomen. De eindfout wordt naar de foutgegevensstroom geschreven als een **ErrorRecord** met een **FullyQualifiedErrorId** van `PSTaskException` .
  Beëindigingsfouten kunnen worden geconverteerd naar niet-beëindigingsfouten met behulp van PowerShell-try-/catch- of trapblokken.

## Voorbeelden

### Voorbeeld 1: Gehele getallen in een matrix delen

In dit voorbeeld wordt een matrix van drie gehele getallen gebruikt en wordt elk van deze door 1024 verdeeld.

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### Voorbeeld 2: de lengte van alle bestanden in een map op te halen

In dit voorbeeld worden de bestanden en mappen in de PowerShell-installatiemap `$PSHOME` verwerkt.

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

Als het object geen map is, haalt het scriptblok de naam van het bestand op, deelt de waarde van de eigenschap **Length** door 1024 en voegt een spatie ("") toe om het te scheiden van de volgende vermelding. De cmdlet gebruikt de **eigenschap PSISContainer** om te bepalen of een object een map is.

### Voorbeeld 3: Werken met de meest recente systeemgebeurtenissen

In dit voorbeeld worden de 1000 meest recente gebeurtenissen uit het systeemgebeurtenislogboek naar een tekstbestand geschreven. De huidige tijd wordt weergegeven voor en na het verwerken van de gebeurtenissen.

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

`Get-EventLog` haalt de 1000 meest recente gebeurtenissen uit het gebeurtenislogboek van het systeem op en slaat deze op in de `$Events` variabele . `$Events` wordt vervolgens doorspijpt naar `ForEach-Object` de cmdlet . De **begin** parameter geeft de huidige datum en tijd. Vervolgens gebruikt de parameter **Process** de cmdlet om een tekstbestand met de naam events.txt te maken en slaat de bericht-eigenschap van elk van de gebeurtenissen `Out-File` in dat bestand op. Ten laatste wordt de parameter **End** gebruikt om de datum en tijd weer te geven nadat alle verwerking is voltooid.

### Voorbeeld 4: De waarde van een registersleutel wijzigen

In dit voorbeeld wordt de waarde van de **RemotePath-registerinvoer** in alle subsleutels onder de sleutel gewijzigd in `HKCU:\Network` hoofdletters.

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

U kunt deze indeling gebruiken om het formulier of de inhoud van een registerinvoerwaarde te wijzigen.

Elke subsleutel in de **netwerksleutel** vertegenwoordigt een gekoppeld netwerkstation dat opnieuw verbinding maakt bij aanmelding. De **vermelding RemotePath** bevat het UNC-pad van het verbonden station. Als u bijvoorbeeld het E:-station toe wijst aan , wordt `\\Server\Share` er een **E-subsleutel** gemaakt in met de `HKCU:\Network` **registerwaarde RemotePath** ingesteld op `\\Server\Share` .

De opdracht gebruikt de cmdlet om alle subsleutels van de netwerksleutel op te halen en de cmdlet om de waarde van de `Get-ItemProperty`  `Set-ItemProperty` **RemotePath-registerinvoer** in elke sleutel te wijzigen.
In de `Set-ItemProperty` opdracht is het pad de waarde van de eigenschap **PSPath** van de registersleutel. Dit is een eigenschap van het Microsoft .NET Framework-object dat de registersleutel vertegenwoordigt, niet een registerinvoer. De opdracht maakt gebruik **van de methode ToUpper()** van de **waarde RemotePath.** Dit is een tekenreeks (REG_SZ).

Omdat `Set-ItemProperty` de eigenschap van elke sleutel verandert, is de `ForEach-Object` cmdlet vereist voor toegang tot de eigenschap .

### Voorbeeld 5: de automatische $Null gebruiken

In dit voorbeeld ziet u het effect van het doorspitten van `$Null` de automatische variabele naar de `ForEach-Object` cmdlet .

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

Omdat PowerShell null als een expliciete tijdelijke aanduiding behandelt, genereert de cmdlet een waarde voor , net als voor andere objecten die u er `ForEach-Object` naar doorspijpt. `$Null`

### Voorbeeld 6: eigenschapswaarden op halen

In dit voorbeeld wordt de waarde van de **eigenschap Path** van alle geïnstalleerde PowerShell-modules met behulp van de **parameter MemberName** van de `ForEach-Object` cmdlet .

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

De tweede opdracht is gelijk aan de eerste. Hierbij wordt de alias van de cmdlet gebruikt en wordt de naam van de `Foreach` `ForEach-Object` parameter **MemberName** weglaat, wat optioneel is.

De cmdlet is handig voor het verkrijgen van eigenschapswaarden, omdat deze de waarde krijgt zonder het type te wijzigen, in tegenstelling tot de cmdlets Format of `ForEach-Object` de cmdlet , waarmee het waardetype van de eigenschap wordt  `Select-Object` gewijzigd.

### Voorbeeld 7: Modulenamen splitsen in onderdeelnamen

In dit voorbeeld ziet u drie manieren om twee modulenamen met punten te splitsen in de onderdeelnamen.

```powershell
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object {$_.Split(".")}
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object -MemberName Split -ArgumentList "."
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | Foreach Split "."
```

```Output
Microsoft
PowerShell
Core
Microsoft
PowerShell
Host
```

Met de opdrachten wordt de **methode Split van** tekenreeksen aanroepen. De drie opdrachten gebruiken een andere syntaxis, maar ze zijn gelijkwaardig en uitwisselbaar.

De eerste opdracht maakt gebruik van de traditionele syntaxis, die een scriptblok en de huidige objectoperator `$_` bevat. Er wordt gebruikgemaakt van de puntsyntaxis om de methode en haakjes op te geven om het scheidingsteken te omsluiten.

De tweede opdracht maakt gebruik van de **parameter MemberName** om de methode **Split** en de parameter **ArgumentName** op te geven om de punt (".") te identificeren als het scheidingsteken voor splitsen.

De derde opdracht maakt gebruik van de **Foreach-alias** van de cmdlet en laat de namen van de `ForEach-Object` parameters **MemberName** en **ArgumentList** weg, die optioneel zijn.

### Voorbeeld 8: Een ForEach-Object twee scriptblokken gebruiken

In dit voorbeeld geven we twee scriptblokken positioneel door. Alle scriptblokken worden aan de parameter **Process** binden. Ze worden echter behandeld alsof ze zijn doorgegeven aan de **parameters Begin** **en Process.**

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### Voorbeeld 9: Een ForEach-Object meer dan twee scriptblokken gebruiken

In dit voorbeeld geven we twee scriptblokken positioneel door. Alle scriptblokken worden aan de parameter **Process** binden. Ze worden echter behandeld alsof ze zijn doorgegeven aan de parameters **Begin,** **Process** en **End.**

```powershell
1..2 | ForEach-Object { 'begin' } { 'process A' }  { 'process B' }  { 'end' }
```

```Output
begin
process A
process B
process A
process B
end
```

> [!NOTE]
> Het eerste scriptblok wordt altijd aan het blok toegesneden, het laatste blok is aan het blok en de blokken ertussen worden allemaal aan het `begin` `end` blok `process` toegesneden.

### Voorbeeld 10: Meerdere scriptblokken uitvoeren voor elk pijplijnitem

Zoals u in het vorige voorbeeld kunt zien, worden meerdere scriptblokken die zijn doorgegeven met behulp van de parameter **Process,** aan de parameters **Begin** en **End** doorgegeven. Als u deze toewijzing wilt voorkomen, moet u expliciete waarden opgeven voor de parameters **Begin** **en End.**

```powershell
1..2 | ForEach-Object -Begin $null -Process { 'one' }, { 'two' }, { 'three' } -End $null
```

```Output
one
two
three
one
two
three
```

### Voorbeeld 11: Langzaam script uitvoeren in parallelle batches

In dit voorbeeld wordt een eenvoudig scriptblok uitgevoerd dat een tekenreeks evalueert en één seconde in de slaapstand gaat.

```powershell
$Message = "Output:"

1..8 | ForEach-Object -Parallel {
    "$using:Message $_"
    Start-Sleep 1
} -ThrottleLimit 4
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
```

De **parameterwaarde ThrottleLimit** is ingesteld op 4, zodat de invoer wordt verwerkt in batches van vier.
Het `$using:` trefwoord wordt gebruikt om de variabele `$Message` door te geven aan elk parallel scriptblok.

### Voorbeeld 12: Logboekgegevens parallel ophalen

In dit voorbeeld worden 50.000 logboekgegevens opgehaald uit 5 systeemlogboeken op een lokale Windows-computer.

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count
```

```Output
50000
```

De **parameter Parallel** geeft het scriptblok aan dat parallel wordt uitgevoerd voor elke naam van het invoerlogboek. De **parameter ThrottleLimit** zorgt ervoor dat alle vijf scriptblokken tegelijkertijd worden uitgevoerd.

### Voorbeeld 13: Parallel uitvoeren als een taak

In dit voorbeeld wordt een eenvoudig scriptblok parallel uitgevoerd, waardoor er twee achtergrondtaken tegelijk worden gemaakt.

```powershell
$job = 1..10 | ForEach-Object -Parallel {
    "Output: $_"
    Start-Sleep 1
} -ThrottleLimit 2 -AsJob

$job | Receive-Job -Wait
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
Output: 9
Output: 10
```

De `$job` variabele ontvangt het taakobject dat uitvoergegevens verzamelt en de status van de uitvoer bewaakt.
Het taakobject wordt doorspijpt `Receive-Job` naar met de parameter **Wait** switch. En deze streamt uitvoer naar de console, alsof `ForEach-Object -Parallel` deze is uitgevoerd zonder **AsJob**.

### Voorbeeld 14: Verwijzingen naar veilige threadvariabelen gebruiken

In dit voorbeeld worden scriptblokken parallel aanroepen om unieke procesobjecten te verzamelen.

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
Get-Process | ForEach-Object -Parallel {
    $dict = $using:threadSafeDictionary
    $dict.TryAdd($_.ProcessName, $_)
}

$threadSafeDictionary["pwsh"]
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     82    82.87     130.85      15.55    2808   2 pwsh
```

Er wordt één exemplaar van een **ConcurrentDictionary-object** doorgegeven aan elk scriptblok om de objecten te verzamelen. Omdat **concurrentDictionary thread-veilig** is, is het veilig om te worden gewijzigd door elk parallel script. Een niet-thread-veilig object, zoals **System.Collections.Generic.Dictionary,** is hier niet veilig te gebruiken.

> [!NOTE]
> Dit voorbeeld is een zeer inefficiënt gebruik van **de parameter Parallel.** Het script voegt gewoon het invoerobject toe aan een gelijktijdig woordenboekobject. Het is eenvoudig en de overhead van het aanroepen van elk script in een afzonderlijke thread niet waard. Normaal `ForEach-Object` uitvoeren zonder de **parallelle** switch is veel efficiënter en sneller. Dit voorbeeld is alleen bedoeld om te laten zien hoe u thread-veilige variabelen gebruikt.

### Voorbeeld 15: Fouten schrijven met parallelle uitvoering

In dit voorbeeld wordt parallel naar de foutstroom geschreven, waarbij de volgorde van geschreven fouten willekeurig is.

```powershell
1..3 | ForEach-Object -Parallel {
    Write-Error "Error: $_"
}
```

```Output
Write-Error: Error: 1
Write-Error: Error: 3
Write-Error: Error: 2
```

### Voorbeeld 16: Fouten bij parallelle uitvoering beëindigen

In dit voorbeeld wordt een beëindigingsfout in één parallel uitgevoerd scriptblok gedemonstreerd.

```powershell
1..5 | ForEach-Object -Parallel {
    if ($_ -eq 3)
    {
        throw "Terminating Error: $_"
    }

    Write-Output "Output: $_"
}
```

```Output
Exception: Terminating Error: 3
Output: 1
Output: 4
Output: 2
Output: 5
```

`Output: 3` wordt nooit geschreven omdat het parallelle scriptblok voor die iteratie is beëindigd.

### Voorbeeld 17: Variabelen doorgeven in genest parallel script ScriptBlockSet

U kunt een variabele buiten een `Foreach-Object -Parallel` scoped scriptblock maken en deze gebruiken in het scriptblok met het trefwoord `$using` .

```powershell
$test1 = 'TestA'
1..2 | Foreach-Object -Parallel {
    $using:test1
}
```

```Output
TestA
TestA
```

```powershell
# You CANNOT create a variable inside a scoped scriptblock
# to be used in a nested foreach parallel scriptblock.
$test1 = 'TestA'
1..2 | Foreach-Object -Parallel {
    $using:test1
    $test2 = 'TestB'
    1..2 | Foreach-Object -Parallel {
        $using:test2
    }
}
```

```Output
Line |
   2 |  1..2 | Foreach-Object -Parallel {
     |         ~~~~~~~~~~~~~~~~~~~~~~~~~~
     | The value of the using variable '$using:test2' cannot be retrieved because it has not been set in the local session.
```

Het geneste scriptblok heeft geen toegang tot de `$test2` variabele en er wordt een foutmelding weergegeven.

## Parameters

### -ArgumentList

Hiermee geeft u een matrix van argumenten op voor een methode-aanroep. Zie voor meer informatie over het gedrag van **ArgumentList** [about_Splatting](about/about_Splatting.md#splatting-with-arrays).

Deze parameter is geïntroduceerd in Windows PowerShell 3.0.

```yaml
Type: System.Object[]
Parameter Sets: PropertyAndMethodSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Begin

Hiermee geeft u een scriptblok op dat wordt uitgevoerd voordat deze cmdlet invoerobjecten verwerkt. Dit scriptblok wordt slechts één keer uitgevoerd voor de hele pijplijn. Zie voor meer informatie `begin` over het [blok about_Functions.](about/about_functions.md#piping-objects-to-functions)

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -End

Hiermee geeft u een scriptblok op dat wordt uitgevoerd nadat deze cmdlet alle invoerobjecten verwerkt. Dit scriptblok wordt slechts één keer uitgevoerd voor de hele pijplijn. Zie voor meer informatie over het `end` [blok about_Functions](about/about_functions.md#piping-objects-to-functions).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Hiermee geeft u de invoerobjecten. `ForEach-Object` voert het scriptblok of de bewerkingsin instructie uit op elk invoerobject. Voer een variabele in die de objecten bevat of typ een opdracht of expressie die de objecten op haalt.

Wanneer u de **parameter InputObject** gebruikt met , in plaats van opdrachtresultaten door te spitten naar , wordt de `ForEach-Object` waarde `ForEach-Object` **InputObject** behandeld als één object. Dit geldt zelfs als de waarde een verzameling is die het resultaat is van een opdracht, zoals `-InputObject (Get-Process)` .
Omdat **InputObject** geen afzonderlijke eigenschappen van een matrix of verzameling objecten kan retourneren, raden we u aan om in de pijplijn te gebruiken om bewerkingen uit te voeren op een verzameling objecten voor objecten die specifieke waarden in gedefinieerde eigenschappen hebben, zoals wordt weergegeven in de voorbeelden `ForEach-Object` in dit `ForEach-Object` onderwerp.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MemberName

Hiermee geeft u de eigenschap op die moet worden get of de methode die moet worden aanroepen.

Jokertekens zijn toegestaan, maar werken alleen als de resulterende tekenreeks wordt opgelost naar een unieke waarde.
Als u bijvoorbeeld gebruikt, komt het jokertekenpatroon overeen met meer dan één lid, waardoor `Get-Process | ForEach -MemberName *Name` de opdracht mislukt.

Deze parameter is geïntroduceerd in Windows PowerShell 3.0.

```yaml
Type: System.String
Parameter Sets: PropertyAndMethodSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Proces

Hiermee geeft u de bewerking die wordt uitgevoerd op elk invoerobject. Dit scriptblok wordt uitgevoerd voor elk object in de pijplijn. Zie voor meer informatie over het `process` [blok about_Functions](about/about_functions.md#piping-objects-to-functions).

Wanneer u meerdere scriptblokken aan de parameter **Process** opgeeft, wordt het eerste scriptblok altijd aan het blok `begin` doorgegeven. Als er slechts twee scriptblokken zijn, wordt het tweede blok aan het blok `process` toegesneden. Als er drie of meer scriptblokken zijn, wordt het eerste scriptblok altijd aan het blok toe te staan, wordt het laatste blok aan het blok toe te staan en worden de blokken daartussen allemaal aan het blok `begin` `end` `process` toegesneden.

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemainingScripts

Hiermee geeft u alle scriptblokken op die niet worden gebruikt door de parameter **Process.**

Deze parameter is geïntroduceerd in Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Parallel

Hiermee geeft u het scriptblok moet worden gebruikt voor parallelle verwerking van invoerobjecten. Voer een scriptblok in dat de bewerking beschrijft.

Deze parameter is geïntroduceerd in PowerShell 7.0.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ParallelParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Hiermee geeft u het aantal scriptblokken op dat parallel wordt uitgevoerd. Invoerobjecten worden geblokkeerd totdat het aantal blokkeringen van lopende scripts onder **throttleLimit valt.** De standaardwaarde is `5`.

Deze parameter is geïntroduceerd in PowerShell 7.0.

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimeoutSeconds

Hiermee geeft u het aantal seconden op dat moet worden gewacht totdat alle invoer parallel wordt verwerkt. Na de opgegeven time-outtijd worden alle scripts gestopt die worden uitgevoerd. En alle resterende invoerobjecten die moeten worden verwerkt, worden genegeerd. De standaardwaarde `0` van schakelt de time-out uit en `ForEach-Object -Parallel` kan voor onbepaalde tijd worden uitgevoerd. Als <kbd>u Ctrl</kbd> + <kbd>C op</kbd> de opdrachtregel typt, wordt een lopende opdracht `ForEach-Object -Parallel` gestopt. Deze parameter kan niet worden gebruikt samen met de **AsJob** parameter.

Deze parameter is geïntroduceerd in PowerShell 7.0.

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseNewRunspace

Zorgt ervoor dat de parallelle aanroep een nieuwe runspace maakt voor elke herhaling van lussen in plaats van runspaces uit de runspace-pool opnieuw te gebruiken.

Deze parameter is geïntroduceerd in PowerShell 7.1

```yaml
Type: SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob

Zorgt ervoor dat de parallelle aanroep wordt uitgevoerd als een PowerShell-taak. Er wordt één taakobject geretourneerd in plaats van uitvoer van de lopende scriptblokken. Het taakobject bevat onderliggende taken voor elk parallel scriptblok dat wordt uitgevoerd. Het taakobject kan worden gebruikt door alle PowerShell-taak-cmdlets om de status van de lopende taak te bewaken en gegevens op te halen.

Deze parameter is geïntroduceerd in PowerShell 7.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

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

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## Invoerwaarden

### System.Management.Automation.PSObject

U kunt elk object doorseen naar deze cmdlet.

## Uitvoerwaarden

### System.Management.Automation.PSObject

Deze cmdlet retourneert objecten die worden bepaald door de invoer.

## Notities

- De `ForEach-Object` cmdlet werkt op dezelfde als de **Foreach-instructie,** behalve dat u geen invoer kunt doorspijpen naar een **Foreach-instructie.** Zie voor meer informatie over de **Foreach-instructie** [about_Foreach.](./About/about_Foreach.md)

- Vanaf PowerShell 4.0 zijn er methoden toegevoegd voor `Where` `ForEach` gebruik met verzamelingen. Meer informatie over deze nieuwe methoden vindt u [hier about_arrays](./About/about_Arrays.md)

- De `ForEach-Object -Parallel` parameterset maakt gebruik van de interne API van PowerShell om elk scriptblok uit te voeren. Dit is aanzienlijk meer overhead dan normaal `ForEach-Object` uitvoeren met sequentiële verwerking. Het is belangrijk om Parallel te **gebruiken,** waarbij de overhead van het parallel uitvoeren klein is in vergelijking met het werk dat het scriptblok uitvoert. Bijvoorbeeld:

  - Rekenintensieve scripts op computers met meerdere kernen
  - Scripts die tijd besteden aan het wachten op resultaten of het uitvoeren van bestandsbewerkingen

  Het gebruik **van de** parameter Parallel kan ertoe leiden dat scripts veel langzamer worden uitgevoerd dan normaal. Met name als de parallelle scripts eenvoudig zijn. Experimenteer **met Parallel** om te ontdekken waar het nuttig kan zijn.

- [Veelvoorkomende parametervariabelen voor PipelineVariable](About/about_CommonParameters.md) worden niet ondersteund in  `Foreach-Object -Parallel` scenario's, zelfs niet met het `$using:` trefwoord .

  > [!IMPORTANT]
  > Met `ForEach-Object -Parallel` de parameterset worden scriptblokken parallel uitgevoerd op afzonderlijke procesthreads. Met `$using:` het trefwoord kunnen variabelenverwijzingen van de cmdlet-aanroepthread worden doorgeven aan elke thread met het lopende scriptblok. Omdat de scriptblokken worden uitgevoerd in verschillende threads, moeten de objectvariabelen die worden doorgegeven door verwijzing veilig worden gebruikt. Over het algemeen is het veilig om te lezen van objecten waarnaar wordt verwezen en die niet worden gewijzigd. Maar als de objecttoestand wordt gewijzigd, moet u thread-veilige objecten gebruiken, zoals .NET **System.Collection.Concurrent-typen** (zie voorbeeld 11).

## Verwante koppelingen

[Compare-Object](../Microsoft.PowerShell.Utility/Compare-Object.md)

[Where-Object](Where-Object.md)

[Group-Object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Measure-Object](../Microsoft.PowerShell.Utility/Measure-Object.md)

[New-Object](../Microsoft.PowerShell.Utility/New-Object.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Sort-Object](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Tee-Object](../Microsoft.PowerShell.Utility/Tee-Object.md)
