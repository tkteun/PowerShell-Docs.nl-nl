---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-information?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Information
ms.openlocfilehash: f15902c1c6c298dd02db3edf061d56e1446ecb1f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705688"
---
# Write-Information

## SAMENVATTING

Hiermee geeft u op hoe Power shell gegevens streamen voor een opdracht verwerkt.

## SYNTAXIS

```
Write-Information [-MessageData] <Object> [[-Tags] <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Write-Information` cmdlet geeft u op hoe Power shell gegevens streamen voor een opdracht verwerkt.

Windows Power shell 5,0 introduceert een nieuwe, gestructureerde informatie stroom. U kunt deze stroom gebruiken om gestructureerde gegevens te verzenden tussen een script en de aanroepers of de hosttoepassing.
`Write-Information` Hiermee kunt u een informatief bericht toevoegen aan de stream en opgeven hoe Power shell gegevens streamen voor een opdracht verwerkt. Informatie stromen werkt ook voor `PowerShell.Streams` , taken en geplande taken.

> [!NOTE]
> De informatie stroom volgt niet de standaard Conventie voor het voor voegsel van de berichten met ' [Stream name]: '. Dit is bedoeld voor het gezichts boog en het visuele goed.

De `$InformationPreference` waarde van de voorkeurs variabele bepaalt of het bericht dat u opgeeft `Write-Information` , wordt weer gegeven op het verwachte punt in de bewerking van een script. Omdat de standaard waarde van deze variabele `SilentlyContinue` standaard is, worden informatieve berichten niet weer gegeven. Als u de waarde van niet wilt wijzigen `$InformationPreference` , kunt u de waarde ervan overschrijven door de `InformationAction` para meter common toe te voegen aan de opdracht. Zie [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) en [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

> [!NOTE]
> Met ingang van Windows Power shell 5,0 `Write-Host` is een wrapper waarmee `Write-Information` u `Write-Host` de uitvoer naar de informatie stroom kunt verzenden. Hierdoor kan het **vastleggen** of **onderdrukken** van gegevens die zijn geschreven met behoud van `Write-Host` achterwaartse compatibiliteit. Zie [Write-host (Engelstalig)](Write-Host.md) voor meer informatie.

`Write-Information` is ook een ondersteunde werk stroom activiteit in Power shell 5. x.

## VOORBEELDEN

### Voor beeld 1: informatie schrijven voor Get-Results

In dit voor beeld ziet u een informatief bericht ' kreeg uw functies! ', na het uitvoeren `Get-WindowsFeature` van de opdracht om alle functies te vinden met een naam waarde die begint met ' p '.
Omdat de `$InformationPreference` variabele nog steeds is ingesteld op de standaard instelling, `SilentlyContinue` voegt u de `InformationAction` para meter toe om de waarde te overschrijven `$InformationPreference` en wordt het bericht weer gegeven. De `InformationAction` waarde wordt voortgezet, wat betekent dat uw bericht wordt weer gegeven, maar het script of de opdracht wordt voortgezet als dit nog niet is voltooid.

```powershell
Get-WindowsFeature -Name p*
Write-Information -MessageData "Got your features!" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
Got your features!
```

### Voor beeld 2: gegevens schrijven en deze labelen

In dit voor beeld gebruikt u `Write-Information` om gebruikers te laten weten dat ze een andere opdracht moeten uitvoeren nadat ze klaar zijn met het uitvoeren van de huidige opdracht. In het voor beeld worden de label instructies aan het informatie bericht toegevoegd. Als u na het uitvoeren van deze opdracht de informatie stroom doorzoekt naar berichten met instructies, is het bericht dat u hier hebt opgegeven, onder de resultaten.

```powershell
$message = "To filter your results for PowerShell, pipe your results to the Where-Object cmdlet."
Get-WindowsFeature -Name p*
Write-Information -MessageData $message -Tags "Instructions" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
To filter your results for PowerShell, pipe your results to the Where-Object cmdlet.
```

### Voor beeld 3: gegevens naar een bestand schrijven

In dit voor beeld leidt u de gegevens stroom in de functie om naar een `Info.txt` met behulp van de code `6>` . Wanneer u het `Info.txt` bestand opent, ziet u de tekst ' hier gaat u '.

```powershell
function Test-Info
{
    Get-Process P*
    Write-Information "Here you go"
}
Test-Info 6> Info.txt
```

### Voor beeld 4: object door geven om informatie te schrijven

In dit voor beeld kunt u gebruiken `Write-Information` om de tien beste processen voor CPU-gebruik te schrijven van de `Get-Process` object uitvoer die door meerdere pijp lijnen wordt door gegeven.

```powershell
Get-Process | Sort-Object CPU -Descending |
    Select-Object Id, ProcessName, CPU -First 10 |
        Write-Information -InformationAction Continue
```

```Output
@{Id=12692; ProcessName=chrome; CPU=39431.296875}
@{Id=21292; ProcessName=OUTLOOK; CPU=23991.875}
@{Id=10548; ProcessName=CefSharp.BrowserSubprocess; CPU=20546.203125}
@{Id=312848; ProcessName=Taskmgr; CPU=13173.1875}
@{Id=10848; ProcessName=SnapClient; CPU=7014.265625}
@{Id=9760; ProcessName=Receiver; CPU=6792.359375}
@{Id=12040; ProcessName=Teams; CPU=5605.578125}
@{Id=498388; ProcessName=chrome; CPU=3062.453125}
@{Id=6900; ProcessName=chrome; CPU=2546.9375}
@{Id=9044; ProcessName=explorer; CPU=2358.765625}
```

## PARAMETERS

### -MessageData

Hiermee geeft u een informatief bericht op dat u wilt weer geven aan gebruikers wanneer ze een script of opdracht uitvoeren. Voor de beste resultaten plaatst u het informatie bericht tussen aanhalings tekens.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Tags

Hiermee geeft u een eenvoudige teken reeks op die u kunt gebruiken om berichten die u aan de informatie stroom hebt toegevoegd, te sorteren en te filteren `Write-Information` . Deze para meter werkt op dezelfde manier als de **labels** -para meter in `New-ModuleManifest` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. object

`Write-Information` Hiermee worden objecten van het pipet geaccepteerd om aan de informatie stroom te worden door gegeven.

## UITVOER

### System. Management. Automation. InformationRecord

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)

[about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Schrijf fouten opsporen](Write-Debug.md)

[Write-host](Write-Host.md)

[Write-Information](Write-Information.md)

[Schrijf voortgang](Write-Progress.md)

[Write-verbose](Write-Verbose.md)

[Waarschuwing voor schrijven](Write-Warning.md)

[Write-output](Write-Output.md)
