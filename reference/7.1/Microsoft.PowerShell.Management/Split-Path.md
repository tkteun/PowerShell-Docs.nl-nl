---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: c0ee5552e33792f208faba63dc05ddb93473bc49
ms.sourcegitcommit: 9a53e53e7a3ef9ac0a212c61005efff9e9902452
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/18/2020
ms.locfileid: "93251837"
---
# Split-Path

## SAMENVATTING
Retourneert het opgegeven deel van een pad.

## SYNTAXIS

### Bovenliggendeset (standaard)

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### Blade

```
Split-Path [-Path] <String[]> -Leaf [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

### LeafBaseSet

```
Split-Path [-Path] <String[]> -LeafBase [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### Uitbreidingsset

```
Split-Path [-Path] <String[]> -Extension [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### Kwalificatieset

```
Split-Path [-Path] <String[]> -Qualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### Geen Kwalificatieset

```
Split-Path [-Path] <String[]> -NoQualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### IsAbsoluteSet

```
Split-Path [-Path] <String[]> [-Resolve] -IsAbsolute [-Credential <PSCredential>]
 [<CommonParameters>]
```

### LiteralPathSet

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

## BESCHRIJVING

De `Split-Path` cmdlet retourneert alleen het opgegeven deel van een pad, zoals de bovenliggende map, een submap of een bestands naam. Er kunnen ook items worden opgehaald waarnaar wordt verwezen door het Splits pad en te zien of het pad relatief of absoluut is.

U kunt deze cmdlet gebruiken om alleen een geselecteerd deel van een pad op te halen of in te dienen.

## VOORBEELDEN

### Voor beeld 1: de kwalificatie van een pad ophalen

```powershell
Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
```

```Output
HKCU:
```

Met deze opdracht wordt alleen de kwalificatie van het pad geretourneerd. De kwalificatie is het station.

### Voor beeld 2: bestands namen weer geven

```powershell
Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
```

```Output
Pass1.log
Pass2.log
...
```

Met deze opdracht worden de bestanden weer gegeven waarnaar wordt verwezen door het Splits pad. Omdat dit pad wordt gesplitst naar het laatste item, ook wel het Leaf genoemd, worden in de opdracht alleen de bestands namen weer gegeven.

De para meter **resolver** geeft `Split-Path` aan dat de items waarnaar het Splits pad verwijst, worden weer gegeven in plaats van het Splits pad weer te geven.

Net als alle `Split-Path` opdrachten retourneert deze opdracht teken reeksen. Er worden geen **file info** -objecten geretourneerd die de bestanden vertegenwoordigen.

### Voor beeld 3: de bovenliggende container ophalen

```powershell
Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
```

```Output
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

Met deze opdracht worden alleen de bovenliggende containers van het pad geretourneerd. Omdat het geen para meters bevat om de splitsing op te geven, `Split-Path` gebruikt de standaard locatie van de Splits site, die **ouder** is.

### Voor beeld 4: Hiermee wordt bepaald of een pad absoluut is

```powershell
Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
```

```Output
False
```

Met deze opdracht bepaalt u of het pad relatief of absoluut is. In dit geval, omdat het pad relatief is ten opzichte van de huidige map, die wordt vertegenwoordigd door een punt ( `.` ), wordt geretourneerd `$False` .

### Voor beeld 5: locatie wijzigen naar een opgegeven pad

```powershell
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

Met deze opdracht wordt uw locatie gewijzigd in de map met het Power shell-profiel.

De opdracht tussen haakjes wordt gebruikt `Split-Path` om alleen het bovenliggende item te retour neren van het pad dat is opgeslagen in de ingebouwde `$Profile` variabele. De **bovenliggende** para meter is de standaard waarde voor de Splits locatie.
Daarom kunt u deze uit de opdracht weglaten. De haakjes direct Power shell om de opdracht eerst uit te voeren. Dit is een handige manier om over te stappen op een map met een lange padnaam.

### Voor beeld 6: een pad splitsen met behulp van de pijp lijn

```powershell
'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
```

```Output
C:\Documents and Settings\User01\My Documents
```

Met deze opdracht wordt een pijplijn operator ( `|` ) gebruikt om een pad naar te verzenden `Split-Path` . Het pad wordt tussen aanhalings tekens geplaatst om aan te geven dat het een enkel token is.

## PARAMETERS

### -Credential

> [!NOTE]
> Deze para meter wordt niet ondersteund door providers die zijn ge??nstalleerd met Power shell. Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.

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

### -Extensie

Geeft aan dat deze cmdlet alleen de uitbrei ding van het blad retourneert. In het pad retourneert de waarde bijvoorbeeld `C:\Test\Logs\Pass1.log` alleen `.log` .

Deze para meter is ge??ntroduceerd in Power shell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ExtensionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IsAbsolute

Geeft aan dat deze cmdlet $True retourneert als het pad absoluut is en $False als het relatief is. Een absoluut pad heeft een lengte die groter is dan nul en gebruikt geen punt ( `.` ) om het huidige pad aan te geven.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsAbsoluteSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Leaf

Geeft aan dat deze cmdlet alleen de laatste item of container in het pad retourneert. In het pad `C:\Test\Logs\Pass1.log` retourneert bijvoorbeeld alleen Pass1. log.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LeafBase

Geeft aan dat deze cmdlet alleen de basis naam van het blad retourneert. In het pad retourneert de waarde bijvoorbeeld `C:\Test\Logs\Pass1.log` alleen `Pass1` .

Deze para meter is ge??ntroduceerd in Power shell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafBaseSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u de paden op die moeten worden gesplitst. In tegens telling tot **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt. Er worden geen tekens ge??nterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: LiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Indicator

Geeft aan dat deze cmdlet het pad retourneert zonder de kwalificatie. Voor het bestands systeem of register providers is de kwalificatie het station van het pad naar de provider, zoals `C:` of `HKCU:` . In het pad retourneert de waarde bijvoorbeeld `C:\Test\Logs\Pass1.log` alleen `\Test\Logs\Pass1.log` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoQualifierSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Bovenliggend item

Geeft aan dat deze cmdlet alleen de bovenliggende containers van het item of de container retourneert die door het pad worden opgegeven. In het pad retourneert het bijvoorbeeld `C:\Test\Logs\Pass1.log` `C:\Test\Logs` .
De **bovenliggende** para meter is de standaard waarde voor de Splits locatie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParentSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Hiermee geeft u de paden op die moeten worden gesplitst. Joker tekens zijn toegestaan. Als het pad spaties bevat, plaatst u het tussen aanhalings tekens. U kunt ook een pad naar deze cmdlet pipeen.

```yaml
Type: System.String[]
Parameter Sets: ParentSet, LeafSet, LeafBaseSet, ExtensionSet, QualifierSet, NoQualifierSet, IsAbsoluteSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Kwalificatie

Geeft aan dat met deze cmdlet alleen de kwalificatie van het opgegeven pad wordt geretourneerd. Voor het bestands systeem of register providers is de kwalificatie het station van het pad naar de provider, zoals `C:` of `HKCU:` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: QualifierSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Oplossen

Geeft aan dat met deze cmdlet de items worden weer gegeven waarnaar wordt verwezen door het resulterende Splits pad in plaats van de elementen van het pad weer te geven.

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks met een pad naar deze cmdlet door sluizen.

## UITVOER

### System. String, System. Boolean

`Split-Path` Retourneert tekst teken reeksen. Wanneer u de para meter voor het **oplossen** opgeeft, `Split-Path` retourneert een teken reeks die de locatie van de items beschrijft; deze retourneert geen objecten die de items vertegenwoordigen, zoals een **file info** -of **RegistryKey** -object.

Wanneer u de para meter **IsAbsolute** opgeeft, `Split-Path` wordt een **Booleaanse** waarde geretourneerd.

## OPMERKINGEN

- De para meters voor de Splits locatie ( **Kwalificatie** , **bovenliggend element** , **uitbrei ding** , **blad** , **LeafBase** en geen **Kwalificatie** ) zijn exclusief. U kunt slechts ????n in elke opdracht gebruiken.

- De cmdlets die het **pad naar** de tijdelijke naam (de **pad** -cmdlets) bevatten, werken met padnamen en retour neren de namen in een beknopt formaat dat alle Power shell-providers kunnen interpreteren. Ze zijn ontworpen voor gebruik in Program ma's en scripts waarvoor u de volledige of gedeeltelijke naam van een pad wilt weer geven in een bepaalde indeling. U kunt ze gebruiken op de manier waarop u **mapnaam** , **Normpath** , **realpath** , **join's** of andere pad-werkers zou gebruiken.

- U kunt de **pad** -cmdlets samen met verschillende providers gebruiken. Dit zijn onder andere het bestands systeem, het REGI ster en de certificaat providers.

- `Split-Path` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven. Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` . Zie about_Providers voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Convert-pad](Convert-Path.md)

[Pad voor samen voegen](Join-Path.md)

[Oplossen-pad](Resolve-Path.md)

[Test-pad](Test-Path.md)
