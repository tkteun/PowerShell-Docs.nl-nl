---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-clixml?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Clixml
ms.openlocfilehash: 549cb3a33c0020f8033c4a21ccea3f8c2c7ad64c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250687"
---
# Import-Clixml

## SAMENVATTING
Hiermee wordt een CLIXML-bestand geïmporteerd en worden de bijbehorende objecten in Power shell gemaakt.

## SYNTAXIS

### ByPath (standaard)

```
Import-Clixml [-Path] <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

### ByLiteralPath

```
Import-Clixml -LiteralPath <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

## BESCHRIJVING

`Import-Clixml`Met de cmdlet wordt een CLI-XML-bestand (Common Language Infrastructure) geïmporteerd met gegevens die Microsoft .NET Framework-objecten vertegenwoordigen en de Power shell-objecten worden gemaakt. Zie [taal onafhankelijkheid](/dotnet/standard/language-independence)voor meer informatie over cli.

Een waardevol gebruik van `Import-Clixml` op Windows-computers is het importeren van referenties en beveiligde teken reeksen die zijn geëxporteerd als beveiligde XML met `Export-Clixml` . Zie voor beeld 2 voor een voor beeld.

`Import-Clixml` maakt gebruik van de byte-order-Mark (BOM) om de coderings indeling van het bestand te detecteren. Als het bestand geen stuk lijst heeft, wordt ervan uitgegaan dat de code ring UTF8 is.

## VOORBEELDEN

### Voor beeld 1: een geserialiseerd bestand importeren en een object opnieuw maken

In dit voor beeld wordt de `Export-Clixml` cmdlet gebruikt om een geserialiseerde kopie van de proces gegevens op te slaan die worden geretourneerd door `Get-Process` . `Import-Clixml` Hiermee wordt de inhoud van het geserialiseerde bestand opgehaald en wordt een object gemaakt dat is opgeslagen in de `$Processes` variabele.

```powershell
Get-Process | Export-Clixml -Path .\pi.xml
$Processes = Import-Clixml -Path .\pi.xml
```

### Voor beeld 2: een beveiligd referentie object importeren

In dit voor beeld krijgt u een referentie die u hebt opgeslagen in de `$Credential` variabele door de `Get-Credential` cmdlet uit te voeren, kunt u de `Export-Clixml` cmdlet uitvoeren om de referentie op schijf op te slaan.

> [!IMPORTANT]
> `Export-Clixml` exporteert alleen versleutelde referenties in Windows. Op niet-Windows-besturings systemen, zoals macOS en Linux, worden referenties geëxporteerd als tekst zonder opmaak.

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

`Export-Clixml`Met de cmdlet worden referentie objecten versleuteld met behulp van de Windows [Data Protection-API](/previous-versions/windows/apps/hh464970(v=win.10)).
De versleuteling zorgt ervoor dat alleen uw gebruikers account de inhoud van het referentie object kan ontsleutelen. Het geëxporteerde `CLIXML` bestand kan niet worden gebruikt op een andere computer of door een andere gebruiker.

In het voor beeld wordt het bestand waarin de referentie is opgeslagen vertegenwoordigd door `TestScript.ps1.credential` . Vervang **TestScript** door de naam van het script waarmee u de referentie laadt.

U stuurt het referentie object omlaag in de pijp lijn naar `Export-Clixml` en slaat het op in het pad, `$Credxmlpath` , dat u hebt opgegeven in de eerste opdracht.

Als u de referentie automatisch wilt importeren in uw script, voert u de laatste twee opdrachten uit. Voer uit `Import-Clixml` om het beveiligde referentie object te importeren in uw script. Deze import elimineert het risico dat wacht woorden met onbewerkte tekst in uw script worden weer gegeven.

## PARAMETERS

### -Eerste

Hiermee wordt alleen het opgegeven aantal objecten opgehaald. Voer het aantal objecten in dat moet worden opgehaald.

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeTotalCount

Hiermee wordt het totale aantal objecten in de gegevensset gerapporteerd, gevolgd door de geselecteerde objecten. Als de cmdlet het totale aantal niet kan bepalen, wordt het **onbekende totale aantal** weer gegeven. Het gehele getal heeft een **nauw** keurige eigenschap die de betrouw baarheid van de totale aantal waarden aangeeft. De waarde van **nauw keurigheid** ligt van `0.0` tot `1.0` waar `0.0` betekent dat de cmdlet de objecten niet kan tellen, `1.0` betekent dat het aantal precies is en een waarde tussen `0.0` en een `1.0` steeds betrouw bare schatting aangeeft.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u het pad naar de XML-bestanden. In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt zoals deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad naar de XML-bestanden.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Overs Laan

Hiermee wordt het opgegeven aantal objecten genegeerd en worden vervolgens de resterende objecten opgehaald. Voer het aantal objecten in dat moet worden overgeslagen.

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

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

U kunt een teken reeks die een pad bevat naar een pijp lijn `Import-Clixml` .

## UITVOER

### PSObject

`Import-Clixml` retourneert objecten die zijn gedeserialiseerd van de opgeslagen XML-bestanden.

## OPMERKINGEN

Wanneer u meerdere waarden voor een para meter opgeeft, moet u komma's gebruiken om de waarden van elkaar te scheiden. Bijvoorbeeld `<parameter-name> <value1>, <value2>`.

## GERELATEERDE KOPPELINGEN

[Exporteren-Clixml](Export-Clixml.md)

[Inleiding tot XML-serialisatie](/dotnet/standard/serialization/introducing-xml-serialization)

[Pad voor samen voegen](../Microsoft.PowerShell.Management/Join-Path.md)

[Referenties veilig opslaan op schijf](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[Power shell gebruiken om referenties door te geven aan verouderde systemen](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)
