---
description: Hierin worden de para meters beschreven die kunnen worden gebruikt met een wille keurige cmdlet.
Locale: en-US
ms.date: 11/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CommonParameters
ms.openlocfilehash: 44503e9c251cd3cccf9b879ceb71262c65d8e5e9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705530"
---
# <a name="about-commonparameters"></a>Over CommonParameters

## <a name="short-description"></a>KORTE BESCHRIJVING

Hierin worden de para meters beschreven die kunnen worden gebruikt met een wille keurige cmdlet.

## <a name="long-description"></a>LANGE BESCHRIJVING

De algemene para meters zijn een set cmdlet-para meters die u met een wille keurige cmdlet kunt gebruiken. Ze worden geïmplementeerd door Power shell, niet door de cmdlet-ontwikkelaar en ze zijn automatisch beschikbaar voor alle cmdlets.

U kunt de algemene para meters voor elke cmdlet gebruiken, maar ze hebben mogelijk geen invloed op alle cmdlets. Als een cmdlet bijvoorbeeld geen uitgebreide uitvoer genereert, heeft het gebruik van de **uitgebreide** para meter algemeen geen effect.

De algemene para meters zijn ook beschikbaar voor geavanceerde functies die gebruikmaken van het kenmerk **CmdletBinding** of het **parameter** kenmerk.

Verschillende algemene para meters overschrijven systeem standaarden of voor keuren die u instelt met behulp van de voorkeurs variabelen van Power shell. In tegens telling tot de voorkeurs variabelen zijn de algemene para meters alleen van invloed op de opdrachten waarin ze worden gebruikt.

Zie [about_Preference_Variables](./about_Preference_Variables.md)voor meer informatie.

De volgende lijst geeft de algemene para meters weer. Hun aliassen worden tussen haakjes weer gegeven.

- **Debug** (DB)
- **Error Action** (EA)
- **ErrorVariable** (EV)
- **Information Action** (infa)
- **InformationVariable** (IV)
- **Outvariable** (ov)
- **Outbuffer** (Ob)
- **PipelineVariable** (PV)
- **Uitgebreid** (VB)
- **WarningAction** (WA)
- **WarningVariable** (WV)

De **actie** parameters zijn waarden van het type **ActionPreference** .
**ActionPreference** is een opsomming met de volgende waarden:

| Name             | Waarde |
|------------------|-------|
| Onderbreken          | 5     |
| Negeren           | 4     |
| Inquire          | 3     |
| Doorgaan         | 2     |
| Stoppen             | 1     |
| SilentlyContinue | 0     |

U kunt de naam of de waarde gebruiken met de para meter.

Naast de algemene para meters bieden veel cmdlets para meters voor risico beperking. Cmdlets die Risico's voor het systeem of gebruikers gegevens vereisen, bieden doorgaans deze para meters.

De para meters voor risico beperking zijn:

- **WhatIf** (Wi)
- **Bevestigen** (CF)

### <a name="common-parameter-descriptions"></a>ALGEMENE PARAMETER BESCHRIJVINGEN

#### <a name="debug"></a>Fouten opsporen

Geeft details op programmeer niveau weer over de bewerking die door de opdracht wordt uitgevoerd. Deze para meter werkt alleen als de opdracht een fout opsporingsgegevens genereert. Deze para meter werkt bijvoorbeeld als een opdracht de cmdlet bevat `Write-Debug` .

```yaml
Type: SwitchParameter
Aliases: db

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

Standaard worden fout opsporings berichten niet weer gegeven omdat de waarde van de `$DebugPreference` variabele **SilentlyContinue** is.

In de interactieve modus overschrijft de para meter **debug** de waarde van de `$DebugPreference` variabele voor de huidige opdracht, waarbij de waarde wordt ingesteld `$DebugPreference` op voor **query's**.

In de niet-interactieve modus overschrijft de para meter **debug** de waarde van de `$DebugPreference` variabele voor de huidige opdracht, waarbij u de waarde van opgeeft `$DebugPreference` om **door te gaan**.

`-Debug:$true` heeft hetzelfde effect als `-Debug` . Gebruik `-Debug:$false` om de weer gave van fout opsporings berichten te onderdrukken wanneer `$DebugPreference` deze niet **SilentlyContinue** is. Dit is de standaard instelling.

#### <a name="erroraction"></a>Error Action

Hiermee wordt bepaald hoe de cmdlet reageert op een niet-afsluit fout van de opdracht.
Deze para meter werkt alleen als de opdracht een niet-afsluit fout genereert, zoals die van de `Write-Error` cmdlet.

```yaml
Type: ActionPreference
Aliases: ea
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

De para meter **Error Action** overschrijft de waarde van de `$ErrorActionPreference` variabele voor de huidige opdracht. Omdat de standaard waarde van de `$ErrorActionPreference` variabele wordt **voortgezet**, worden er fout berichten weer gegeven en wordt de uitvoering voortgezet, tenzij u de para meter **Error Action** gebruikt.

De para meter **Error Action** heeft geen invloed op de afsluit fouten (zoals ontbrekende gegevens, para meters die ongeldig zijn of onvoldoende machtigingen) waarmee wordt voor komen dat een opdracht kan worden voltooid.

`-ErrorAction:Continue` het fout bericht weer geven en door gaan met het uitvoeren van de opdracht. `Continue` is de standaardwaarde.

`-ErrorAction:Ignore` onderdrukt het fout bericht en gaat door met het uitvoeren van de opdracht. In tegens telling tot **SilentlyContinue** **, wordt** het fout bericht niet toegevoegd aan de `$Error` Automatische variabele. De waarde **Ignore** wordt geïntroduceerd in power Shell 3,0.

`-ErrorAction:Inquire` Hiermee wordt het fout bericht weer gegeven en wordt u gevraagd om bevestiging voordat u doorgaat met de uitvoering. Deze waarde wordt zelden gebruikt.

`-ErrorAction:SilentlyContinue` onderdrukt het fout bericht en gaat door met het uitvoeren van de opdracht.

`-ErrorAction:Stop` geeft het fout bericht weer en stopt met het uitvoeren van de opdracht.

`-ErrorAction:Suspend` is alleen beschikbaar voor werk stromen die niet worden ondersteund in Power shell 6 en hoger.

> [!NOTE]
> De para meter **Error Action** wordt overschreven, maar de waarde van de voorkeurs variabele wordt niet vervangen `$ErrorAction` wanneer de para meter wordt gebruikt in een opdracht voor het uitvoeren van een script of functie.

#### <a name="errorvariable"></a>ErrorVariable

**ErrorVariable** slaat fout berichten over de opdracht op in de opgegeven variabele en in de `$Error` Automatische variabele. Zie [about_Automatic_Variables](about_Automatic_Variables.md) voor meer informatie.

```yaml
Type: String
Aliases: ev

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

Nieuwe fout berichten overschrijven standaard fout berichten die al zijn opgeslagen in de variabele. Als u het fout bericht wilt toevoegen aan de variabele inhoud, typt u een plus teken ( `+` ) voor de naam van de variabele.

Met de volgende opdracht wordt bijvoorbeeld de `$a` variabele gemaakt en vervolgens eventuele fouten erin opgeslagen:

```powershell
Get-Process -Id 6 -ErrorVariable a
```

Met de volgende opdracht worden eventuele fout berichten aan de `$a` variabele toegevoegd:

```powershell
Get-Process -Id 2 -ErrorVariable +a
```

Met de volgende opdracht wordt de inhoud van weer gegeven `$a` :

```powershell
$a
```

U kunt deze para meter gebruiken om een variabele te maken die alleen fout berichten uit specifieke opdrachten bevat. Dit heeft geen invloed op het gedrag van de `$Error` Automatische variabele. De `$Error` Automatische variabele bevat fout berichten van alle opdrachten in de sessie. U kunt matrix notatie gebruiken, zoals `$a[0]` of `$error[1,2]` om te verwijzen naar specifieke fouten die zijn opgeslagen in de variabelen.

> [!NOTE]
> De variabele met de aangepaste fout bevat alle fouten die zijn gegenereerd door de opdracht, inclusief fouten van aanroepen naar geneste functies of scripts.

#### <a name="informationaction"></a>Information Action

Geïntroduceerd in Power shell 5,0. In de opdracht of het script waarin het wordt gebruikt, overschrijft de algemene para meter **Information Action** de waarde van de `$InformationPreference` Voorkeurs variabele, die standaard is ingesteld op **SilentlyContinue**. Wanneer u gebruikt `Write-Information` in een script met **Information Action**, `Write-Information` worden waarden weer gegeven, afhankelijk van de waarde van de para meter **Information Action** . Zie about_Preference_Variables voor meer informatie over `$InformationPreference` . [](./about_Preference_Variables.md)

```yaml
Type: ActionPreference
Aliases: ia
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

`-InformationAction:Stop` Hiermee stopt u een opdracht of script bij een exemplaar van de `Write-Information` opdracht.

`-InformationAction:Ignore` onderdrukt het informatie bericht en gaat verder met het uitvoeren van de opdracht. In tegens telling tot **SilentlyContinue**, wordt met **negeren** het informatieve bericht volledig verg eten. het informatie bericht wordt niet toegevoegd aan de informatie stroom.

`-InformationAction:Inquire` Hiermee wordt het informatie bericht weer gegeven dat u in een `Write-Information` opdracht opgeeft. vervolgens wordt u gevraagd of u wilt door gaan.

`-InformationAction:Continue` het informatieve bericht wordt weer gegeven en blijft actief.

`-InformationAction:Suspend` wordt niet ondersteund in Power shell core omdat deze alleen beschikbaar is voor werk stromen.

`-InformationAction:SilentlyContinue` geen effect omdat het informatieve bericht niet (standaard) wordt weer gegeven en het script zonder onderbreking wordt voortgezet.

> [!NOTE]
> De para meter **Information Action** wordt overschreven, maar de waarde van de voorkeurs variabele wordt niet vervangen `$InformationAction` wanneer de para meter wordt gebruikt in een opdracht voor het uitvoeren van een script of functie.

#### <a name="informationvariable"></a>InformationVariable

Geïntroduceerd in Power shell 5,0. Binnen de opdracht of het script waarin het wordt gebruikt, wordt in de algemene para meter **InformationVariable** in een variabele een teken reeks opgeslagen die u opgeeft door de opdracht toe te voegen `Write-Information` . `Write-Information` de waarden worden weer gegeven, afhankelijk van de waarde van de algemene para meter **Information Action** . Als u de algemene para meter **Information Action** niet toevoegt, `Write-Information` worden teken reeksen weer gegeven, afhankelijk van de waarde van de `$InformationPreference` Voorkeurs variabele. Zie about_Preference_Variables voor meer informatie over `$InformationPreference` . [](./about_Preference_Variables.md)

> [!NOTE]
> De informatie variabele bevat alle informatie berichten die door de opdracht worden gegenereerd, inclusief informatie berichten van aanroepen naar geneste functies of scripts.

```yaml
Type: String
Aliases: iv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

#### <a name="outbuffer"></a>OutBuffer

Bepaalt het aantal objecten dat in een buffer moet worden verzameld voordat er objecten via de pijp lijn worden verzonden. Als u deze para meter weglaat, worden er objecten verzonden wanneer ze worden gegenereerd.

```yaml
Type: Int32
Aliases: ob

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

Deze resource management-para meter is ontworpen voor ervaren gebruikers. Wanneer u deze para meter gebruikt, verzendt Power shell gegevens naar de volgende cmdlet in batches van `OutBuffer + 1` .

In het volgende voor beeld wordt een alternatief weer gegeven tussen voor het `ForEach-Object` verwerken van blokken die gebruikmaken van de- `Write-Host` cmdlet. De weergave alternatieven in batches van 2 of `OutBuffer + 1` .

```powershell
1..4 | ForEach-Object {
        Write-Host "$($_): First"; $_
      } -OutBuffer 1 | ForEach-Object {
                        Write-Host "$($_): Second" }
```

```Output
1: First
2: First
1: Second
2: Second
3: First
4: First
3: Second
4: Second
```

#### <a name="outvariable"></a>OutVariable

Slaat uitvoer objecten op uit de opdracht in de opgegeven variabele, naast het verzenden van de uitvoer langs de pijp lijn.

```yaml
Type: String
Aliases: ov

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

Als u de uitvoer wilt toevoegen aan de variabele, typt u een plus teken ( `+` ) voor de naam van de variabele, in plaats van de uitvoer te vervangen die daar mogelijk al is opgeslagen.

Met de volgende opdracht wordt bijvoorbeeld de `$out` variabele gemaakt en wordt het proces object opgeslagen:

```powershell
Get-Process PowerShell -OutVariable out
```

Met de volgende opdracht wordt het proces object aan de `$out` variabele toegevoegd:

```powershell
Get-Process iexplore -OutVariable +out
```

Met de volgende opdracht wordt de inhoud van de variabele weer gegeven `$out` :

```powershell
$out
```

> [!NOTE]
> De variabele die door de para meter **outvariable** wordt gemaakt, is een `[System.Collections.ArrayList]` .

#### <a name="pipelinevariable"></a>PipelineVariable

**PipelineVariable** slaat de waarde van het huidige pijplijn element op als een variabele voor elke benoemde opdracht terwijl het door de pijp lijn loopt.

```yaml
Type: String
Aliases: pv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

Geldige waarden zijn teken reeksen, hetzelfde als voor alle namen van variabelen.

Hier volgt een voor beeld van hoe **PipelineVariable** werkt. In dit voor beeld wordt de para meter **PipelineVariable** toegevoegd aan een `Foreach-Object` opdracht voor het opslaan van de resultaten van de opdracht in variabelen. Een reeks cijfers, 1 tot en met 10, wordt in de eerste `Foreach-Object` opdracht geplaatst, waarbij de resultaten worden opgeslagen in een variabele met de naam **Left**.

De resultaten van de eerste `Foreach-Object` opdracht worden in een tweede opdracht gepiped `Foreach-Object` , waarmee de objecten worden gefilterd die door de eerste opdracht worden geretourneerd `Foreach-Object` . De resultaten van de tweede opdracht worden opgeslagen in een variabele met de naam **rechts**.

In de derde `Foreach-Object` opdracht worden de resultaten van de eerste twee `Foreach-Object` gepipede opdrachten, vertegenwoordigd door de variabelen **links** en **rechts**, verwerkt met behulp van een vermenigvuldigings operator. De opdracht geeft objecten die zijn opgeslagen in de **linker** -en **rechter** variabelen die moeten worden vermenigvuldigd en geeft aan dat de resultaten moeten worden weer gegeven als ' lid van ' links bereik * rechter bereik lid = product '.

```powershell
1..10 | Foreach-Object -PipelineVariable Left -Process { $_ } |
  Foreach-Object -PV Right -Process { 1..10 } |
  Foreach-Object -Process { "$Left * $Right = " + ($Left*$Right) }
```

```output
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
1 * 4 = 4
1 * 5 = 5
...
```

#### <a name="verbose"></a>Uitgebreid

Geeft gedetailleerde informatie weer over de bewerking die door de opdracht wordt uitgevoerd. Deze informatie komt overeen met de informatie in een tracering of in een transactie logboek. Deze para meter werkt alleen als de opdracht een uitgebreid bericht genereert. Deze para meter werkt bijvoorbeeld als een opdracht de cmdlet bevat `Write-Verbose` .

```yaml
Type: SwitchParameter
Aliases: vb

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

De para meter **uitgebreid** overschrijft de waarde van de `$VerbosePreference` variabele voor de huidige opdracht. Omdat de standaard waarde van de `$VerbosePreference` variabele **SilentlyContinue** is, worden uitgebreide berichten niet standaard weer gegeven.

`-Verbose:$true` heeft hetzelfde effect als `-Verbose`

`-Verbose:$false` onderdrukt de weer gave van uitgebreide berichten. Gebruik deze para meter als de waarde van `$VerbosePreference` niet **SilentlyContinue** is (de standaard instelling).

#### <a name="warningaction"></a>WarningAction

Hiermee wordt bepaald hoe de cmdlet reageert op een waarschuwing van de opdracht. **Continue** is de standaard waarde. Deze para meter werkt alleen als er een waarschuwings bericht wordt gegenereerd door de opdracht. Deze para meter werkt bijvoorbeeld als een opdracht de cmdlet bevat `Write-Warning` .

```yaml
Type: ActionPreference
Aliases: wa
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

De para meter **WarningAction** overschrijft de waarde van de `$WarningPreference` variabele voor de huidige opdracht. Omdat de standaard waarde van de `$WarningPreference` variabele wordt **voortgezet**, worden er waarschuwingen weer gegeven en wordt de uitvoering voortgezet, tenzij u de para meter **WarningAction** gebruikt.

`-WarningAction:Continue` geeft de waarschuwings berichten weer en gaat verder met het uitvoeren van de opdracht. `Continue` is de standaardwaarde.

`-WarningAction:Inquire` Hiermee wordt het waarschuwings bericht weer gegeven en wordt u gevraagd om bevestiging voordat u doorgaat met de uitvoering. Deze waarde wordt zelden gebruikt.

`-WarningAction:SilentlyContinue` onderdrukt het waarschuwings bericht en gaat door met het uitvoeren van de opdracht.

`-WarningAction:Stop` geeft het waarschuwings bericht weer en stopt met het uitvoeren van de opdracht.

> [!NOTE]
> De para meter **WarningAction** wordt overschreven, maar de waarde van de voorkeurs variabele wordt niet vervangen `$WarningAction` wanneer de para meter wordt gebruikt in een opdracht voor het uitvoeren van een script of functie.

#### <a name="warningvariable"></a>WarningVariable

Slaat waarschuwingen over de opdracht op in de opgegeven variabele.

```yaml
Type: String
Aliases: wv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

Alle gegenereerde waarschuwingen worden opgeslagen in de variabele, zelfs als de waarschuwingen niet worden weer gegeven voor de gebruiker.

Als u de waarschuwingen wilt toevoegen aan de variabele inhoud, in plaats van waarschuwingen te vervangen die daar al zijn opgeslagen, typt u een plus teken ( `+` ) voor de naam van de variabele.

Met de volgende opdracht wordt bijvoorbeeld de `$a` variabele gemaakt en vervolgens eventuele waarschuwingen opgeslagen:

```powershell
Get-Process -Id 6 -WarningVariable a
```

Met de volgende opdracht worden eventuele waarschuwingen aan de `$a` variabele toegevoegd:

```powershell
Get-Process -Id 2 -WarningVariable +a
```

Met de volgende opdracht wordt de inhoud van weer gegeven `$a` :

```powershell
$a
```

U kunt deze para meter gebruiken om een variabele te maken die alleen waarschuwingen van specifieke opdrachten bevat. U kunt matrix notatie gebruiken, zoals `$a[0]` of `$warning[1,2]` om te verwijzen naar specifieke waarschuwingen die zijn opgeslagen in de variabele.

> [!NOTE]
> De variabele Warning bevat alle waarschuwingen die zijn gegenereerd door de opdracht, inclusief waarschuwingen van aanroepen naar geneste functies of scripts.

### <a name="risk-management-parameter-descriptions"></a>Beschrijvingen van de para meters voor risico beheer

#### <a name="whatif"></a>WhatIf

Hier wordt een bericht weer gegeven waarin het effect van de opdracht wordt beschreven, in plaats van de opdracht uit te voeren.

```yaml
Type: SwitchParameter
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

De para meter **WhatIf** overschrijft de waarde van de `$WhatIfPreference` variabele voor de huidige opdracht. Omdat de standaard waarde van de `$WhatIfPreference` variabele 0 (uitgeschakeld) is, wordt het gedrag **WhatIf** niet uitgevoerd zonder de para meter **WhatIf** . Zie [about_Preference_Variables](about_Preference_Variables.md) voor meer informatie.

`-WhatIf:$true` heeft hetzelfde effect als `-WhatIf` .

`-WhatIf:$false` onderdrukt het automatische WhatIf-gedrag dat resulteert wanneer de waarde van de `$WhatIfPreference` variabele 1 is.

Met de volgende opdracht wordt bijvoorbeeld de `-WhatIf` para meter gebruikt in een `Remove-Item` opdracht:

```powershell
Remove-Item Date.csv -WhatIf
```

In plaats van het item te verwijderen, worden de bewerkingen weer gegeven die worden uitgevoerd in Power shell en de items die zouden worden beïnvloed. Met deze opdracht wordt de volgende uitvoer gegenereerd:

```output
What if: Performing operation "Remove File" on
Target "C:\ps-test\date.csv".
```

#### <a name="confirm"></a>Bevestigen

Vraagt u om bevestiging voordat de opdracht wordt uitgevoerd.

```yaml
Type: SwitchParameter
Aliases: cf

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

De para meter **confirm** onderdrukt de waarde van de `$ConfirmPreference` variabele voor de huidige opdracht. De standaardwaarde is waar. Zie [about_Preference_Variables](about_Preference_Variables.md) voor meer informatie.

`-Confirm:$true` heeft hetzelfde effect als `-Confirm` .

`-Confirm:$false` onderdrukt automatische bevestiging. dit gebeurt wanneer de waarde van `$ConfirmPreference` kleiner is dan of gelijk is aan het geschatte risico van de cmdlet.

Met de volgende opdracht wordt bijvoorbeeld de **confirm** -para meter met een `Remove-Item` opdracht gebruikt. Voordat u het item verwijdert, worden de bewerkingen weer gegeven die worden uitgevoerd en de items die zouden worden beïnvloed, en wordt u gevraagd om goed te keuren.

```
PS C:\ps-test> Remove-Item tmp*.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target " C:\ps-test\tmp1.txt
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend
[?] Help (default is "Y"):
```

De opties voor het bevestigen van antwoorden zijn als volgt:

|Antwoord       |Resultaat                                                     |
|---------------|-----------------------------------------------------------|
|Ja (Y)        |Voer de actie uit.                                        |
|Ja op alles (A) |Alle acties uitvoeren en volgende bevestigde query's onderdrukken|
|               |voor deze opdracht.                                          |
|Nee (N):        |Voer de actie niet uit.                                 |
|Nee naar alle (L): |Geen acties uitvoeren en volgende bevestiging onderdrukken |
|               |query's voor deze opdracht.                                  |
|Suspend (S):   |De opdracht onderbreken en een tijdelijke sessie maken.          |
|Help (?)       |Help weer geven voor deze opties.                            |

Met de optie **suspend** wordt de opdracht in de wacht stand geplaatst en wordt er een tijdelijke geneste sessie gemaakt waarin u kunt werken totdat u een optie voor **bevestigen** kiest. De opdracht prompt voor de geneste sessie heeft twee extra caret (>>) om aan te geven dat het een onderliggende bewerking is van de oorspronkelijke bovenliggende opdracht. U kunt opdrachten en scripts uitvoeren in de geneste sessie. Als u de geneste sessie wilt beëindigen en wilt terugkeren naar de bevestigings opties voor de oorspronkelijke opdracht, typt u ' afsluiten '.

In het volgende voor beeld wordt **de optie voor** uitstel (en) gebruikt om een opdracht tijdelijk te onderbreken terwijl de gebruiker de Help voor een opdracht parameter controleert. Nadat de benodigde gegevens zijn verkregen, typt u ' exit ' om de geneste prompt te beëindigen en selecteert u vervolgens het Ja (y)-antwoord op de query bevestigen.

```
PS C:\ps-test> New-Item -ItemType File -Name Test.txt -Confirm

Confirm
Are you sure you want to perform this action?

Performing operation "Create File" on Target "Destination:
C:\ps-test\test.txt".
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default
is "Y"): s

PS C:\ps-test> Get-Help New-Item -Parameter ItemType

-ItemType <string>
Specifies the provider-specified type of the new item.

Required?                    false
Position?                    named
Default value
Accept pipeline input?       true (ByPropertyName)
Accept wildcard characters?  false

PS C:\ps-test> exit

Confirm
Are you sure you want to perform this action?
Performing operation "Create File" on Target "Destination: C:\ps-test\test
.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (defau
lt is "Y"): y

Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         8/27/2010   2:41 PM          0 test.txt
```

## <a name="keywords"></a>WOORD

about_Common_Parameters

## <a name="see-also"></a>ZIE OOK

[about_Preference_Variables](about_Preference_Variables.md)

[Schrijf fouten opsporen](xref:Microsoft.PowerShell.Utility.Write-Debug)

[Waarschuwing voor schrijven](xref:Microsoft.PowerShell.Utility.Write-Warning)

[Schrijf fout](xref:Microsoft.PowerShell.Utility.Write-Error)

[Write-verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)

