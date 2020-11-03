---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: 5d92acbe080b0d232047f1184c9a369b8837845c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250543"
---
# Split-Path

## SAMENVATTING
Retourneert het opgegeven deel van een pad.

## SYNTAXIS

### Bovenliggendeset (standaard)

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### Geen Kwalificatieset

```
Split-Path [-Path] <String[]> [-NoQualifier] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### Blade

```
Split-Path [-Path] <String[]> [-Leaf] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### Kwalificatieset

```
Split-Path [-Path] <String[]> [-Qualifier] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### IsAbsoluteSet

```
Split-Path [-Path] <String[]> [-Resolve] [-IsAbsolute] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### LiteralPathSet

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

## BESCHRIJVING

De cmdlet **Split-Path** retourneert alleen het opgegeven deel van een pad, zoals de bovenliggende map, een submap of een bestands naam.
Er kunnen ook items worden opgehaald waarnaar wordt verwezen door het Splits pad en te zien of het pad relatief of absoluut is.

U kunt deze cmdlet gebruiken om alleen een geselecteerd deel van een pad op te halen of in te dienen.

## VOORBEELDEN

### Voor beeld 1: de kwalificatie van een pad ophalen

```
PS C:\> Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
HKCU:
```

Met deze opdracht wordt alleen de kwalificatie van het pad geretourneerd.
De kwalificatie is het station.

### Voor beeld 2: bestands namen weer geven

```
PS C:\> Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
Pass1.log
Pass2.log
...
```

Met deze opdracht worden de bestanden weer gegeven waarnaar wordt verwezen door het Splits pad.
Omdat dit pad wordt gesplitst naar het laatste item, ook wel het Leaf genoemd, worden in de opdracht alleen de bestands namen weer gegeven.

De para meter *resolver* vertelt **gesplitste paden** om de items weer te geven waarnaar de Splits pad verwijst, in plaats van het Splits pad weer te geven.

Net als bij alle opdracht **Split-paden** retourneert deze opdracht teken reeksen.
Er worden geen **file info** -objecten geretourneerd die de bestanden vertegenwoordigen.

### Voor beeld 3: de bovenliggende container ophalen

```
PS C:\> Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

Met deze opdracht worden alleen de bovenliggende containers van het pad geretourneerd.
Omdat het geen para meters bevat om de split op te geven, gebruikt **Split Path** de standaard locatie voor splitsen, de *bovenliggende* map.

### Voor beeld 4: Hiermee wordt bepaald of een pad absoluut is

```
PS C:\> Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
False
```

Met deze opdracht bepaalt u of het pad relatief of absoluut is.
In dit geval, omdat het pad relatief is ten opzichte van de huidige map, die wordt vertegenwoordigd door een punt (.), wordt $False geretourneerd.

### Voor beeld 5: locatie wijzigen naar een opgegeven pad

```
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

Met deze opdracht wordt uw locatie gewijzigd in de map met het Power shell-profiel.

De opdracht tussen haakjes gebruikt een **Split-pad** om alleen het bovenliggende item te retour neren van het pad dat is opgeslagen in de ingebouwde $profile variabele.
De *bovenliggende* para meter is de standaard waarde voor de Splits locatie.
Daarom kunt u deze uit de opdracht weglaten.
De haakjes direct Power shell om de opdracht eerst uit te voeren.
Dit is een handige manier om over te stappen op een map met een lange padnaam.

### Voor beeld 6: een pad splitsen met behulp van de pijp lijn

```
PS C:\> 'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
C:\Documents and Settings\User01\My Documents
```

Met deze opdracht wordt een pijplijn operator (|) gebruikt voor het verzenden van een pad naar een **Split-pad**.
Het pad wordt tussen aanhalings tekens geplaatst om aan te geven dat het een enkel token is.

## PARAMETERS

### -Credential

> [!NOTE]
> Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.
> Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.

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

### -IsAbsolute

Geeft aan dat deze cmdlet $True retourneert als het pad absoluut is en $False als het relatief is.
Een absoluut pad heeft een lengte die groter is dan nul en gebruikt geen punt (.) om het huidige pad aan te geven.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsAbsoluteSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Leaf

Geeft aan dat deze cmdlet alleen de laatste item of container in het pad retourneert.
In het pad `C:\Test\Logs\Pass1.log` retourneert bijvoorbeeld alleen Pass1. log.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u de paden op die moeten worden gesplitst.
In tegens telling tot *Path* wordt de waarde van *LiteralPath* precies zo gebruikt als deze wordt getypt.
Er worden geen tekens geïnterpreteerd als joker tekens.
Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.
Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: LiteralPathSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Indicator

Geeft aan dat deze cmdlet het pad retourneert zonder de kwalificatie.
Voor het bestands systeem of register providers is de kwalificatie het station van het pad naar de provider, zoals C: of HKCU:.
In het pad `C:\Test\Logs\Pass1.log` retourneert het bijvoorbeeld alleen \Test\Logs\Pass1.log.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoQualifierSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Bovenliggend item

Geeft aan dat deze cmdlet alleen de bovenliggende containers van het item of de container retourneert die door het pad worden opgegeven.
In het pad `C:\Test\Logs\Pass1.log` retourneert het bijvoorbeeld C:\Test\Logs.
De *bovenliggende* para meter is de standaard waarde voor de Splits locatie.

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

Hiermee geeft u de paden op die moeten worden gesplitst.
Joker tekens zijn toegestaan.
Als het pad spaties bevat, plaatst u het tussen aanhalings tekens.
U kunt ook een pad naar deze cmdlet pipeen.

```yaml
Type: System.String[]
Parameter Sets: ParentSet, NoQualifierSet, LeafSet, QualifierSet, IsAbsoluteSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Kwalificatie

Geeft aan dat met deze cmdlet alleen de kwalificatie van het opgegeven pad wordt geretourneerd.
Voor het bestands systeem of register providers is de kwalificatie het station van het pad naar de provider, zoals C: of HKCU:.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: QualifierSet
Aliases:

Required: False
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

### -UseTransaction

Hiermee wordt de opdracht opgenomen in de actieve transactie.
Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.
Zie about_Transactions voor meer informatie.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks met een pad naar deze cmdlet door sluizen.

## UITVOER

### System. String, System. Boolean

**Split-Path** retourneert tekst teken reeksen.
Wanneer u de para meter voor *omzetten* opgeeft, retourneert **Split-Path** een teken reeks die de locatie van de items beschrijft. het retourneert geen objecten die de items vertegenwoordigen, zoals een **file info** -of **RegistryKey** -object.

Wanneer u de para meter *IsAbsolute* opgeeft, retourneert **Split-Path** een **Boole** -waarde.

## OPMERKINGEN

* De para meters voor de Splits locatie ( *Kwalificatie* , *bovenliggend element* , *Leaf* en geen *Kwalificatie* ) zijn exclusief. U kunt slechts één in elke opdracht gebruiken.

  De cmdlets die het **pad naar** de tijdelijke naam (de **pad** -cmdlets) bevatten, werken met padnamen en retour neren de namen in een beknopt formaat dat alle Power shell-providers kunnen interpreteren.
Ze zijn ontworpen voor gebruik in Program ma's en scripts waarvoor u de volledige of gedeeltelijke naam van een pad wilt weer geven in een bepaalde indeling.
U kunt ze gebruiken op de manier waarop u **mapnaam** , **Normpath** , **realpath** , **join's** of andere pad-werkers zou gebruiken.

  U kunt de **pad** -cmdlets samen met verschillende providers gebruiken.
Dit zijn onder andere het bestands systeem, het REGI ster en de certificaat providers.

  **Split-Path** is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.
Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .
Zie about_Providers voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Convert-pad](Convert-Path.md)

[Pad voor samen voegen](Join-Path.md)

[Oplossen-pad](Resolve-Path.md)

[Test-pad](Test-Path.md)
