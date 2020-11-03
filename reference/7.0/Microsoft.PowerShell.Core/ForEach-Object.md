---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: 8257f1fba2d4367e61121d4876a51197f710da41
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/10/2020
ms.locfileid: "93251904"
---
# ForEach-Object

## Samen vatting
Hiermee wordt een bewerking uitgevoerd voor elk item in een verzameling invoer objecten.

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
ForEach-Object [-InputObject <PSObject>] -Parallel <ScriptBlock> [-ThrottleLimit <Int32>]
 [-TimeoutSeconds <Int32>] [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Beschrijving

`ForEach-Object`Met de cmdlet wordt een bewerking uitgevoerd op elk item in een verzameling invoer objecten. De invoer objecten kunnen worden gesluizen naar de cmdlet of worden opgegeven met behulp van de para meter **input object** .

Vanaf Windows Power Shell 3,0 zijn er twee verschillende manieren om een opdracht te maken `ForEach-Object` .

- **Script blok**. U kunt een script blok gebruiken om de bewerking op te geven. In het-script blok gebruikt `$_` u de variabele om het huidige object weer te geven. Het script blok is de waarde van de para meter **process** . Het script blok kan elk Power shell-script bevatten.

  Met de volgende opdracht wordt bijvoorbeeld de waarde van de eigenschap **proces** naam van elk proces op de computer opgehaald.

  `Get-Process | ForEach-Object {$_.ProcessName}`

  `ForEach-Object` ondersteunt de `begin` , `process` , en `end` blokken zoals beschreven in [about_functions](about/about_functions.md#piping-objects-to-functions).

  > [!NOTE]
  > De script blokken worden uitgevoerd in het bereik van de aanroeper. De blokken hebben daarom toegang tot variabelen in dat bereik en kunnen nieuwe variabelen maken die in dat bereik behouden blijven nadat de cmdlet is voltooid.

- **Bewerkings instructie**. U kunt ook een bewerkings instructie schrijven die veel meer lijkt op natuurlijke taal. U kunt de bewerkings instructie gebruiken om een eigenschaps waarde op te geven of een methode aan te roepen. Er zijn bewerkings instructies geïntroduceerd in Windows Power Shell 3,0.

  Met de volgende opdracht wordt ook de waarde van de eigenschap **proces** naam van elk proces op de computer opgehaald.

  `Get-Process | ForEach-Object ProcessName`

- **Parallel uitgevoerd script blok**. Vanaf Power shell 7,0 is een derde parameterset beschikbaar die elk script blok parallel uitvoert. De para meter **ThrottleLimit** beperkt het aantal parallelle scripts dat op een bepaald moment wordt uitgevoerd. Net als voorheen kunt u met de `$_` variabele het huidige invoer object weer geven in het-script blok. Gebruik het `$using:` sleutel woord om variabele verwijzingen door te geven aan het script dat wordt uitgevoerd.

  In Power shell 7 wordt een nieuwe runs Pace voor elke lus-iteratie gemaakt om de maximale isolatie te garanderen.
  Dit kan een grote prestatie en een bron zijn als het werk dat u uitvoert klein is in vergelijking met het maken van nieuwe runspaces of als er veel iteraties zijn die een aanzienlijke hoeveelheid werk uitvoeren.

  Standaard gebruikt de parallelle scriptblocks de huidige werkmap van de aanroeper die de parallelle taken heeft gestart.

  Niet-afsluit fouten worden naar de cmdlet-fout stroom geschreven, zoals deze optreden in parallelle uitvoering van scriptblocks. Omdat de volg orde van de parallelle script Block niet kan worden bepaald, is de volg orde waarin fouten worden weer gegeven in de fout stroom wille keurig. Op dezelfde manier worden berichten die zijn geschreven naar andere gegevens stromen, zoals waarschuwing, uitgebreide gegevens of informatie, naar deze gegevens stromen geschreven in een onbepaalde volg orde.

  Als u fouten afsluit, zoals uitzonde ringen, beëindigt u de afzonderlijke parallelle instantie van de scriptblocks waarin deze zich voordoen. Een afsluit fout in één scriptblocks veroorzaakt mogelijk geen beëindiging van de `Foreach-Object` cmdlet. De andere scriptblocks, die parallel worden uitgevoerd, blijven worden uitgevoerd, tenzij er ook een afsluit fout optreedt. De afsluit fout wordt naar de gegevens stroom van de fout geschreven als een **ErrorRecord** met een **FullyQualifiedErrorId** van `PSTaskException` .
  Het beëindigen van fouten kan worden geconverteerd naar niet-afsluit fouten met behulp van Power shell-try/catch-of trap-blokken.

## Voorbeelden

### Voor beeld 1: gehele getallen in een matrix delen

In dit voor beeld wordt een matrix van drie gehele getallen gebruikt en worden elke reeks gedeeld door 1024.

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### Voor beeld 2: de lengte van alle bestanden in een map ophalen

In dit voor beeld worden de bestanden en mappen in de installatie directory van Power shell verwerkt `$PSHOME` .

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

Als het object geen map is, wordt de naam van het bestand door het script blok opgehaald, wordt de waarde van de eigenschap **Length** gedeeld door 1024 en wordt een spatie ("") toegevoegd om het te scheiden van de volgende vermelding. De cmdlet gebruikt de eigenschap **PSISContainer** om te bepalen of een object een directory is.

### Voor beeld 3: uitvoeren op de meest recente systeem gebeurtenissen

In dit voor beeld worden de 1000 meest recente gebeurtenissen van het systeem gebeurtenis logboek naar een tekst bestand geschreven. De huidige tijd wordt weer gegeven vóór en na de verwerking van de gebeurtenissen.

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

`Get-EventLog` Hiermee worden de 1000 meest recente gebeurtenissen van het systeem gebeurtenis logboek opgehaald en opgeslagen in de `$Events` variabele. `$Events` wordt vervolgens door gegeven aan de `ForEach-Object` cmdlet. Met de para meter **begin** worden de huidige datum en tijd weer gegeven. Vervolgens gebruikt de para meter **process** de `Out-File` cmdlet om een tekst bestand te maken met de naam events.txt en wordt de bericht eigenschap van elk van de gebeurtenissen in dat bestand opgeslagen. De laatste para meter **End** wordt gebruikt om de datum en tijd weer te geven nadat alle verwerking is voltooid.

### Voor beeld 4: de waarde van een register sleutel wijzigen

In dit voor beeld wordt de waarde van de register vermelding **remotepath** in alle subsleutels onder de sleutel gewijzigd in `HKCU:\Network` hoofd letters.

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

U kunt deze indeling gebruiken om het formulier of de inhoud van een register vermelding te wijzigen.

Elke subsleutel in de **netwerk** sleutel vertegenwoordigt een toegewezen netwerk station waarmee opnieuw verbinding wordt gemaakt bij het aanmelden. De vermelding **remotepath** bevat het UNC-pad van het verbonden station. Als u bijvoorbeeld het station E: toewijst aan `\\Server\Share` , wordt er een **e** -subsleutel gemaakt in `HKCU:\Network` met de register waarde **remotepath** ingesteld op `\\Server\Share` .

De opdracht gebruikt de `Get-ItemProperty` cmdlet om alle subsleutels van de **netwerk** sleutel en de `Set-ItemProperty` cmdlet te verkrijgen om de waarde van de register **vermelding remotepath** in elke sleutel te wijzigen.
In de `Set-ItemProperty` opdracht is het pad de waarde van de eigenschap **PSPath** van de register sleutel. Dit is een eigenschap van het Microsoft .NET Framework-object dat de register sleutel vertegenwoordigt, niet een register vermelding. De opdracht maakt gebruik van de methode **ToUpper ()** van de **remotepath** -waarde. Dit is een teken reeks (REG_SZ).

Omdat `Set-ItemProperty` de eigenschap van elke sleutel wordt gewijzigd, `ForEach-Object` is de cmdlet vereist voor toegang tot de eigenschap.

### Voor beeld 5: de $Null automatische variabele gebruiken

In dit voor beeld ziet u het effect van de `$Null` Automatische variabele voor de `ForEach-Object` cmdlet.

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

Omdat in Power shell NULL wordt behandeld als een expliciete tijdelijke aanduiding, `ForEach-Object` genereert de cmdlet een waarde voor `$Null` , net zoals voor andere objecten die u naar de pipet.

### Voor beeld 6: eigenschaps waarden ophalen

In dit voor beeld wordt de waarde van de eigenschap **Path** van alle geïnstalleerde Power shell-modules opgehaald met behulp van de para meter **membernaam** van de `ForEach-Object` cmdlet.

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

De tweede opdracht is gelijk aan de eerste. Het gebruikt de `Foreach` alias van de `ForEach-Object` cmdlet en laat de naam van de para meter **lidnaam** , die optioneel is.

De `ForEach-Object` cmdlet is handig voor het ophalen van eigenschaps waarden, omdat deze de waarde ophaalt zonder het type te wijzigen, in tegens telling tot de **notatie** -cmdlets of de `Select-Object` cmdlet, waarmee het type eigenschaps waarde wordt gewijzigd.

### Voor beeld 7: module namen splitsen in onderdeel namen

In dit voor beeld ziet u drie manieren om twee punt-gescheiden module namen te splitsen in hun onderdeel namen.

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

Met de opdrachten wordt de **Splits** methode van teken reeksen aangeroepen. De drie opdrachten gebruiken een andere syntaxis, maar ze zijn gelijkwaardig en kunnen worden gewijzigd.

De eerste opdracht maakt gebruik van de traditionele syntaxis, die een script blok en de huidige object operator bevat `$_` . De punt notatie wordt gebruikt om de methode en haakjes op te geven voor het argument scheidings teken.

De tweede opdracht gebruikt de para meter **lidnaam** om de **Split** -methode en de para meter **argumentnaam** op te geven om de punt (".") als scheidings teken te identificeren.

De derde opdracht maakt gebruik van de **foreach** -alias van de `ForEach-Object` cmdlet en laat de namen van de para meters **lidnaam** en **argument List** , die optioneel zijn.

### Voor beeld 8: ForEach-Object gebruiken met twee script blokken

In dit voor beeld worden twee script blokken positioneel door gegeven. Alle script blokken binden aan de **proces** parameter. Ze worden echter behandeld alsof ze zijn door gegeven aan de **begin** -en **proces** parameters.

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### Voor beeld 9: ForEach-Object gebruiken met meer dan twee script blokken

In dit voor beeld worden twee script blokken positioneel door gegeven. Alle script blokken binden aan de **proces** parameter. Ze worden echter behandeld alsof ze zijn door gegeven aan de **begin** -, **proces** -en **End** -para meters.

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
> Het eerste script blok wordt altijd toegewezen aan het `begin` blok, het laatste blok wordt toegewezen aan het `end` blok en de blokken tussen zijn allemaal toegewezen aan het blok `process` .

### Voor beeld 10: meerdere script blokken uitvoeren voor elk pijplijn item

Zoals weer gegeven in het vorige voor beeld, worden er meerdere script blokken door gegeven met behulp van de **proces** parameter Get toegewezen aan de **begin** -en **End** -para meters. Om deze toewijzing te vermijden, moet u expliciete waarden opgeven voor de **begin** -en **eind** parameters.

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

### Voor beeld 11: een langzaam script uitvoeren in parallelle batches

In dit voor beeld wordt een eenvoudig script blok uitgevoerd waarmee een teken reeks en slaap stand gedurende één seconde worden geëvalueerd.

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

De waarde van de para meter **ThrottleLimit** is ingesteld op 4 zodat de invoer wordt verwerkt in batches van vier.
Het `$using:` sleutel woord wordt gebruikt om de variabele door te geven aan `$Message` elk parallel-script blok.

### Voor beeld 12: logboek vermeldingen parallel ophalen

In dit voor beeld worden 50.000 logboek vermeldingen van 5 systeem logboeken op een lokale Windows-computer opgehaald.

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

Met de **parallelle** para meter wordt het script blok opgegeven dat parallel wordt uitgevoerd voor elke invoer logboek naam. De para meter **ThrottleLimit** zorgt ervoor dat alle vijf de script blokken tegelijk worden uitgevoerd.

### Voor beeld 13: parallel uitvoeren als een taak

In dit voor beeld wordt een eenvoudig script blok parallel uitgevoerd, waarbij twee achtergrond taken tegelijk worden gemaakt.

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

de `$job` variabele ontvangt het taak object waarmee uitvoer gegevens worden verzameld en de status van monitors wordt uitgevoerd.
Het taak object wordt gepiped `Receive-Job` met de para meter **wait** switch. En deze streams worden uitgevoerd naar de-console, net zoals bij het `ForEach-Object -Parallel` uitvoeren zonder **AsJob**.

### Voor beeld 14: met behulp van thread safe-verwijzingen naar variabelen

In dit voor beeld worden script blokken parallel aangeroepen om unieke benoemde proces objecten te verzamelen.

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

Er wordt één exemplaar van een **ConcurrentDictionary** -object door gegeven aan elk script blok om de objecten te verzamelen. Omdat de **ConcurrentDictionary** thread-safe is, is het veilig om door elk parallel schrift te worden gewijzigd. Een niet-thread-veilig object, zoals **System. Collections. generic. Dictionary** , is hier niet veilig te gebruiken.

> [!NOTE]
> Dit voor beeld is een zeer inefficiënt gebruik van een **parallelle** para meter. Het script voegt eenvoudigweg het invoer object toe aan een object met een gelijktijdig woorden lijst. Het is lastig en niet de overhead van het aanroepen van elk script in een afzonderlijke thread. `ForEach-Object`Normaal gesp roken werkt **zonder parallelle** switch veel efficiënter en sneller. Dit voor beeld is alleen bedoeld om te laten zien hoe u thread-safe variabelen kunt gebruiken.

### Voor beeld 15: fouten schrijven met parallelle uitvoering

In dit voor beeld wordt de fout stroom parallel geschreven, waarbij de volg orde van de geschreven fouten wille keurig is.

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

### Voor beeld 16: fouten bij parallelle uitvoering beëindigen

In dit voor beeld wordt een afsluit fout in één parallel uitgevoerde script Block gedemonstreerd.

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

`Output: 3` is nooit geschreven, omdat de parallelle script Block voor die herhaling is beëindigd.

## Parameters

### -Argument List

Hiermee geeft u een matrix op met argumenten voor een methode aanroep. Zie [about_Splatting](about/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

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

Hiermee geeft u een script blok op dat wordt uitgevoerd voordat deze cmdlet invoer objecten verwerkt. Dit script blok wordt slechts één keer uitgevoerd voor de volledige pijp lijn. Zie about_Functions voor meer informatie over het `begin` blok [about_Functions](about/about_functions.md#piping-objects-to-functions).

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

Hiermee geeft u een script blok op dat wordt uitgevoerd nadat deze cmdlet alle invoer objecten heeft verwerkt. Dit script blok wordt slechts één keer uitgevoerd voor de volledige pijp lijn. Zie about_Functions voor meer informatie over het `end` blok [about_Functions](about/about_functions.md#piping-objects-to-functions).

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

### -Input object

Hiermee worden de invoer objecten opgegeven. `ForEach-Object` Hiermee wordt het script blok of de bewerkings instructie voor elk invoer object uitgevoerd. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

Wanneer u de para meter **input object** gebruikt in `ForEach-Object` plaats van de resultaten van de pijpleiding opdracht, `ForEach-Object` wordt de waarde van **input object** behandeld als een enkel object. Dit geldt ook als de waarde een verzameling is die het resultaat is van een opdracht, zoals `-InputObject (Get-Process)` .
Omdat **input object** geen individuele eigenschappen van een matrix of verzameling van objecten kan retour neren, raden we u aan dat als u gebruikt `ForEach-Object` om bewerkingen uit te voeren op een verzameling objecten voor objecten met specifieke waarden in gedefinieerde eigenschappen, u `ForEach-Object` in de pijp lijn gebruikt, zoals wordt weer gegeven in de voor beelden in dit onderwerp.

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

### -Lidnaam

Hiermee geeft u de eigenschap op die moet worden opgehaald of de methode die moet worden aangeroepen.

Joker tekens zijn toegestaan, maar werken alleen als de resulterende teken reeks wordt omgezet in een unieke waarde.
Als u bijvoorbeeld uitvoert `Get-Process | ForEach -MemberName *Name` , komt het Joker teken patroon overeen met meer dan één lid waardoor de opdracht mislukt.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

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

Hiermee geeft u de bewerking op die op elk invoer object wordt uitgevoerd. Dit script blok wordt uitgevoerd voor elk object in de pijp lijn. Zie about_Functions voor meer informatie over het `process` blok [about_Functions](about/about_functions.md#piping-objects-to-functions).

Wanneer u meerdere script blokken voor de para meter **process** opgeeft, wordt het eerste script blok altijd toegewezen aan het `begin` blok. Als er slechts twee script blokken zijn, wordt het tweede blok toegewezen aan het `process` blok. Als er drie of meer script blokken zijn, wordt het eerste script blok altijd toegewezen aan het `begin` blok, wordt het laatste blok toegewezen aan het `end` blok en worden de blokken tussen beide toegewezen aan het `process` blok.

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

Hiermee geeft u alle script blokken op die niet worden gebruikt door de **proces** parameter.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

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

Hiermee geeft u het script blok op dat moet worden gebruikt voor parallelle verwerking van invoer objecten. Voer een script blok in dat de bewerking beschrijft.

Deze para meter is geïntroduceerd in Power shell 7,0.

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

Hiermee geeft u het aantal script blokken op dat parallel is. Invoer objecten worden geblokkeerd totdat het aantal actieve script blokken onder het **ThrottleLimit** valt. De standaardwaarde is `5`.

Deze para meter is geïntroduceerd in Power shell 7,0.

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimeoutSeconds

Hiermee geeft u het aantal seconden op dat moet worden gewacht totdat alle invoer parallel wordt verwerkt. Na de opgegeven time-outperiode worden alle actieve scripts gestopt. En alle resterende invoer objecten die moeten worden verwerkt, worden genegeerd. De standaard waarde van `0` de time-out uitschakelen en `ForEach-Object -Parallel` kan oneindig worden uitgevoerd. Als u <kbd>CTRL</kbd> + <kbd>C</kbd> op de opdracht regel typt, wordt een uitvoering van de `ForEach-Object -Parallel` opdracht gestopt. Deze para meter kan niet worden gebruikt in combi natie met de para meter **AsJob** .

Deze para meter is geïntroduceerd in Power shell 7,0.

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

### -AsJob

Zorgt ervoor dat de parallelle aanroep als een Power shell-taak wordt uitgevoerd. Er wordt één taak object geretourneerd in plaats van uitvoer van de actieve script blokken. Het taak object bevat onderliggende taken voor elk parallel-script blok dat wordt uitgevoerd. Het taak object kan worden gebruikt door alle Power shell-taak-cmdlets, om de uitvoerings status te controleren en gegevens op te halen.

Deze para meter is geïntroduceerd in Power shell 7,0.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## Invoerwaarden

### System. Management. Automation. PSObject

U kunt elk object door sluizen naar deze cmdlet.

## Uitvoer

### System. Management. Automation. PSObject

Deze cmdlet retourneert objecten die worden bepaald door de invoer.

## Opmerkingen

- De `ForEach-Object` cmdlet werkt op dezelfde manier als de **foreach** -instructie, behalve dat u invoer niet kunt door sluizen naar een **foreach** -instructie. Zie [about_Foreach](./About/about_Foreach.md)voor meer informatie over de instructie **foreach** .

- Vanaf Power Shell 4,0 `Where` en `ForEach` methoden zijn toegevoegd voor gebruik met verzamelingen. U kunt hier meer lezen over deze nieuwe methoden [about_arrays](./About/about_Arrays.md)

- De `ForEach-Object -Parallel` para meter set gebruikt de interne API van Power shell om elk script blok uit te voeren. Dit is aanzienlijk meer overhead dan `ForEach-Object` normaal uitvoeren met sequentiële verwerking. Het is belang rijk om **parallel** te gebruiken waarbij de overhead van parallelle uitvoering klein is in vergelijking met het werk dat door het script blok wordt uitgevoerd. Bijvoorbeeld:

  - Computerintensieve scripts op multicore-computers
  - Scripts die tijd wachten op resultaten of het uitvoeren van bestands bewerkingen

  Het gebruik van de **parallelle** para meter kan ertoe leiden dat scripts veel langzamer worden uitgevoerd dan normaal. Met name als de parallelle scripts trivial zijn. Experimenteer met **parallel** om te ontdekken waar het nuttig kan zijn.

  > [!IMPORTANT]
  > `ForEach-Object -Parallel`Met de parameterset worden script blokken parallel uitgevoerd in afzonderlijke proces threads. Met het `$using:` sleutel woord kunnen variabelen verwijzingen door geven van de aanroep thread van de cmdlet naar elke actieve script blok thread. Aangezien de script blokken worden uitgevoerd in verschillende threads, moeten de object variabelen die worden door gegeven door verwijzing, veilig worden gebruikt. Over het algemeen is het veilig om te lezen van objecten waarnaar wordt verwezen en die niet worden gewijzigd. Maar als de object status wordt gewijzigd, moet u de beveiligde objecten van de thread gebruiken, zoals .net **System. verzameling. gelijktijdige** typen (Zie voor beeld 11).

## Verwante koppelingen

[Compare-object](../Microsoft.PowerShell.Utility/Compare-Object.md)

[Where-object](Where-Object.md)

[Groep-object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Meting object](../Microsoft.PowerShell.Utility/Measure-Object.md)

[New-Object](../Microsoft.PowerShell.Utility/New-Object.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Sorteer object](../Microsoft.PowerShell.Utility/Sort-Object.md)

[T-object](../Microsoft.PowerShell.Utility/Tee-Object.md)
