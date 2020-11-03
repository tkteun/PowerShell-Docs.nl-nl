---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-path?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Path
ms.openlocfilehash: ced5a5db05674c15fefada73ab55969d724117e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250526"
---
# Test-Path

## SAMENVATTING
Hiermee wordt bepaald of alle elementen van een pad bestaan.

## SYNTAXIS

### Pad (standaard)

```
Test-Path [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>] [-UseTransaction]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

### LiteralPath

```
Test-Path -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>] [-UseTransaction]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

## BESCHRIJVING

De `Test-Path` cmdlet bepaalt of alle elementen van het pad bestaan. Het wordt geretourneerd `$True` als alle elementen bestaan en `$False` als deze ontbreken. U kunt ook zien of de syntaxis van het pad geldig is en of het pad naar een container of een Terminal-of Leaf-element leidt. Als het een `Path` spatie is, `$False` wordt geretourneerd. Als de `Path` is een lege teken reeks, `$null` matrix van `$null` of lege matrix, wordt een niet-afsluit fout geretourneerd.

## VOORBEELDEN

### Voor beeld 1: een pad testen

```powershell
Test-Path -Path "C:\Documents and Settings\DavidC"
```

```Output
True
```

Met deze opdracht wordt gecontroleerd of alle elementen in het pad bestaan, dat wil zeggen, de map C:, de map documenten en instellingen en de DavidC-map. Als er ontbreekt, wordt de cmdlet geretourneerd `$False` .
Als dat niet het geval is, wordt geretourneerd `$True` .

### Voor beeld 2: het pad van een profiel testen

```powershell
Test-Path -Path $profile
```

```Output
False
```

```powershell
Test-Path -Path $profile -IsValid
```

```Output
True
```

Met deze opdrachten wordt het pad van het Power shell-profiel getest.

Met de eerste opdracht wordt bepaald of alle elementen in het pad bestaan. Met de tweede opdracht wordt bepaald of de syntaxis van het pad juist is. In dit geval is het pad `$False` , maar de syntaxis is juist `$True` . Met deze opdrachten `$profile` wordt de automatische variabele gebruikt die naar de locatie van het profiel verwijst, zelfs als het profiel niet bestaat.

Zie about_Automatic_Variables voor meer informatie over automatische variabelen.

### Voor beeld 3: controleren of er bestanden zijn behalve een opgegeven type

```powershell
Test-Path -Path "C:\CAD\Commercial Buildings\*" -Exclude *.dwg
```

```Output
False
```

Met deze opdracht wordt gecontroleerd of er bestanden aanwezig zijn in de andere map voor commerciële doel einden dan. DWG-bestanden.

De opdracht gebruikt de para meter **Path** om het pad op te geven. Omdat het pad een spatie bevat, wordt het pad tussen dubbele aanhalings tekens geplaatst. Het sterretje aan het einde van het pad geeft de inhoud van de map voor commerciële samen stellen aan. Met lange paden, zoals deze, typt u de eerste paar letters van het pad en vervolgens gebruikt u de TAB-toets om het pad te volt ooien.

De opdracht geeft de **exclude** -para meter op om bestanden op te geven die worden wegge laten uit de evaluatie.

In dit geval, omdat de map alleen DWG-bestanden bevat, is het resultaat `$False` .

### Voor beeld 4: controleren op een bestand

```powershell
Test-Path -Path $profile -PathType leaf
```

```Output
True
```

Met deze opdracht wordt gecontroleerd of het pad dat is opgeslagen in de `$profile` variabele leidt naar een bestand. In dit geval, omdat het Power shell-profiel een `.ps1` bestand is, retourneert de cmdlet `$True` .

### Voor beeld 5: paden in het REGI ster controleren

Deze opdrachten worden gebruikt `Test-Path` met de Power shell-register provider.

Met de eerste opdracht wordt getest of het registerpad van de register sleutel **micro soft. Power shell** juist is op het systeem. Als Power shell correct is geïnstalleerd, retourneert de cmdlet `$True` .

> [!IMPORTANT]
> `Test-Path` werkt niet correct met alle Power shell-providers. U kunt bijvoorbeeld gebruiken `Test-Path` om het pad van een register sleutel te testen, maar als u dit gebruikt om het pad van een register vermelding te testen, wordt het altijd geretourneerd `$False` , zelfs als de register vermelding aanwezig is.

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell"
```

```Output
True
```

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell\ExecutionPolicy"
```

```Output
False
```

### Voor beeld 6: testen of een bestand nieuwer is dan een opgegeven datum

Met deze opdracht wordt de dynamische para meter **NewerThan** gebruikt om te bepalen of het bestand ' PowerShell.exe ' op de computer nieuwer is dan 13 juli 2009.

De para meter NewerThan werkt alleen op stations met een bestands systeem.

```powershell
Test-Path $pshome\PowerShell.exe -NewerThan "July 13, 2009"
```

```Output
True
```

### Voor beeld 7: een pad testen met Null als waarde

De fout die is geretourneerd voor `null` , matrix van `null` of lege matrix is een niet-afsluit fout. Deze kan worden onderdrukt met behulp van `-ErrorAction SilentlyContinue` . In het volgende voor beeld ziet u alle gevallen waarin de fout wordt geretourneerd `NullPathNotPermitted` .

```powershell
Test-Path $null
Test-Path $null, $null
Test-Path @()
```

```Output
Test-Path : Cannot bind argument to parameter 'Path' because it is null.
At line:1 char:11
+ Test-Path $null
+           ~~~~~
    + CategoryInfo          : InvalidData: (:) [Test-Path], ParameterBindingValidationException
    + FullyQualifiedErrorId : ParameterArgumentValidationErrorNullNotAllowed,Microsoft.PowerShell.Commands.TestPathCommand
```

### Voor beeld 8: een pad testen met een spatie als waarde

Als er een spatie teken reeks wordt gegeven voor de `-Path` para meter, wordt **True** geretourneerd. Als er een lege teken reeks wordt opgegeven, `Test-Path` wordt er een fout geretourneerd. In het volgende voor beeld worden spaties en lege teken reeksen weer gegeven.

```powershell
Test-Path ' '
Test-Path ''
```

```Output
True
Test-Path : Cannot bind argument to parameter 'Path' because it is an empty string.
At line:1 char:11
+ Test-Path ''
+           ~~
    + CategoryInfo          : InvalidData: (:) [Test-Path], ParameterBindingValidationException
    + FullyQualifiedErrorId : ParameterArgumentValidationErrorEmptyStringNotAllowed,Microsoft.PowerShell.Commands.TestPathCommand
```

## PARAMETERS

### -Credential

> [!NOTE]
> Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell. Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Uitsluiten

Hiermee geeft u de items die met deze cmdlet worden wegge laten. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . Voer een element of patroon van een pad in, zoals *. txt. Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter

Hiermee geeft u een filter op in de indeling of taal van de provider. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider. Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de objecten worden opgehaald in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

Hiermee geeft u de paden op die met deze cmdlet worden getest. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . Voer een element of patroon van een pad in, zoals *. txt. Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -IsValid

Geeft aan dat met deze cmdlet de syntaxis van het pad wordt getest, ongeacht of de elementen van het pad bestaan. Met deze cmdlet wordt geretourneerd `$True` als de syntaxis van het pad geldig is en `$False` als dit niet het geval is.

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

### -LiteralPath

Hiermee geeft u een pad op dat moet worden getest. In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt. Er worden geen tekens geïnterpreteerd als joker tekens. Als het pad tekens bevat die kunnen worden geïnterpreteerd door Power shell als escape-teken reeksen, moet u het pad in één aanhalings teken plaatsen zodat ze niet worden geïnterpreteerd.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NewerThan

Geef een tijd op als een **DateTime** -object.

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OlderThan

Geef een tijd op als een **DateTime** -object.

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Hiermee geeft u een pad op dat moet worden getest. Joker tekens zijn toegestaan. Als het pad spaties bevat, plaatst u het tussen aanhalings tekens.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -PathType

Hiermee geeft u het type van het laatste element in het pad op. Met deze cmdlet wordt geretourneerd `$True` als het element van het opgegeven type is en `$False` als dit niet het geval is. De aanvaardbare waarden voor deze parameter zijn:

- Verpakking.
  Een element met andere elementen, zoals een map of register sleutel.
- Vertakking.
  Een element dat geen andere elementen bevat, zoals een bestand.
- Iedere.
  Ofwel een container of een Leaf.

Hiermee wordt aangegeven of het laatste element in het pad van een bepaald type is.

> [!CAUTION]
>
> Tot en met de Power shell-versie 6.1.2, wanneer de opties **IsValid** en **PathType** samen worden opgegeven, wordt `Test-Path` de schakel optie **PathType** door de cmdlet genegeerd en wordt alleen het pad van de syntactisch gevalideerd zonder het padtype te valideren.
>
> Op basis van het [probleem #8607](https://github.com/PowerShell/PowerShell/issues/8607), kan het oplossen van dit gedrag een belang rijke wijziging in een toekomstige versie zijn, waarbij de functies **IsValid** en **PathType** deel uitmaken van afzonderlijke parameter sets, en dus niet gezamenlijk kunnen worden gebruikt om deze Verwar ring te voor komen.

```yaml
Type: Microsoft.PowerShell.Commands.TestPathType
Parameter Sets: (All)
Aliases: Type
Accepted values: Any, Container, Leaf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseTransaction

Hiermee wordt de opdracht opgenomen in de actieve transactie. Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd. Zie [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md) voor meer informatie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` . Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks die een pad bevat, maar geen letterlijk pad, naar deze cmdlet pipet.

## UITVOER

### System. Boolean

De cmdlet retourneert een **Booleaanse** waarde.

## OPMERKINGEN

De cmdlets die het **pad naar** de tijdelijke naam (de **pad** -cmdlets) bevatten, werken met padnamen en retour neren de namen in een beknopt formaat dat alle Power shell-providers kunnen interpreteren. Ze zijn ontworpen voor gebruik in Program ma's en scripts waarvoor u de volledige of gedeeltelijke naam van een pad wilt weer geven in een bepaalde indeling.
Gebruik deze zoals u **mapnaam** , **Normpath** , **realpath** , **join's** of andere pad-werkers zou gebruiken.

De `Test-Path` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.
Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .
Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Convert-pad](Convert-Path.md)

[Pad voor samen voegen](Join-Path.md)

[Oplossen-pad](Resolve-Path.md)

[Split-pad](Split-Path.md)
