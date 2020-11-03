---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-clixml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Clixml
ms.openlocfilehash: 8485591165cce0425c85d52fbd31d40614af6249
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250459"
---
# Export-Clixml

## SAMENVATTING
Hiermee maakt u een XML-weer gave van een object of objecten en slaat u deze op in een bestand.

## SYNTAXIS

### ByPath (standaard)

```
Export-Clixml [-Path] <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Export-Clixml -LiteralPath <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Export-Clixml`Met de cmdlet maakt u een XML-weer gave op basis van een gemeen schappelijke taal infrastructuur (CLI) van een object of objecten en slaat u deze op in een bestand. U kunt de cmdlet vervolgens gebruiken `Import-Clixml` om het opgeslagen object opnieuw te maken op basis van de inhoud van het bestand.
Zie [taal onafhankelijkheid](/dotnet/standard/language-independence)voor meer informatie over cli.

Deze cmdlet is vergelijkbaar met `ConvertTo-Xml` , behalve dat `Export-Clixml` de resulterende XML in een bestand wordt opgeslagen. `ConvertTo-XML` retourneert de XML, zodat u deze kunt blijven verwerken in Power shell.

Een waardevol gebruik van `Export-Clixml` op Windows-computers is het exporteren van referenties en het veilig beveiligen van teken reeksen als XML. Zie voor beeld 3.

## VOORBEELDEN

### Voor beeld 1: een teken reeks exporteren naar een XML-bestand

In dit voor beeld wordt een XML-bestand gemaakt dat wordt opgeslagen in de huidige map. Dit is een weer gave van de teken reeks **Dit is een test**.

```powershell
"This is a test" | Export-Clixml -Path .\sample.xml
```

De teken reeks die **Dit is, wordt een test** verzonden naar de pijp lijn. `Export-Clixml` maakt gebruik van de para meter **Path** voor het maken van een XML-bestand met `sample.xml` de naam in de huidige map.

### Voor beeld 2: een object exporteren naar een XML-bestand

In dit voor beeld ziet u hoe u een object exporteert naar een XML-bestand en vervolgens een object maakt door de XML uit het bestand te importeren.

```powershell
Get-Acl C:\test.txt | Export-Clixml -Path .\FileACL.xml
$fileacl = Import-Clixml -Path .\FileACL.xml
```

De `Get-Acl` cmdlet haalt de security descriptor van het `Test.txt` bestand op. Het object wordt via de pijp lijn verzonden om de security descriptor aan te geven `Export-Clixml` . De XML-weer gave van het object wordt opgeslagen in een bestand met de naam `FileACL.xml` .

De `Import-Clixml` cmdlet maakt een object van de XML in het `FileACL.xml` bestand. Vervolgens wordt het object in de variabele opgeslagen `$fileacl` .

### Voor beeld 3: een geëxporteerd referentie object versleutelen

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
De versleuteling zorgt ervoor dat alleen uw gebruikers account alleen op die computer de inhoud van het referentie object kan ontsleutelen. Het geëxporteerde `CLIXML` bestand kan niet worden gebruikt op een andere computer of door een andere gebruiker.

In het voor beeld wordt het bestand waarin de referentie is opgeslagen vertegenwoordigd door `TestScript.ps1.credential` . Vervang **TestScript** door de naam van het script waarmee u de referentie laadt.

U stuurt het referentie object omlaag in de pijp lijn naar `Export-Clixml` en slaat het op in het pad, `$Credxmlpath` , dat u hebt opgegeven in de eerste opdracht.

Als u de referentie automatisch wilt importeren in uw script, voert u de laatste twee opdrachten uit. Voer uit `Import-Clixml` om het beveiligde referentie object te importeren in uw script. Deze import elimineert het risico dat wacht woorden met onbewerkte tekst in uw script worden weer gegeven.

## PARAMETERS

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

### -Diepte

Hiermee geeft u op hoeveel niveaus van Inge sloten objecten worden opgenomen in de XML-weer gave. De standaardwaarde is `2`.

De standaard waarde kan worden overschreven voor het object type in de `Types.ps1xml` bestanden. Zie [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)voor meer informatie.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

Hiermee geeft u het type code ring voor het doel bestand op. De standaard waarde is **Unicode**.

De acceptabele waarden voor deze para meter zijn als volgt:

- `ASCII` Maakt gebruik van ASCII-tekenset (7-bits).
- `BigEndianUnicode` Maakt gebruik van UTF-16 met de byte volgorde big endian.
- `Default` Gebruikt de code ring die overeenkomt met de actieve code tabel van het systeem (meestal ANSI).
- `OEM` Gebruikt de code ring die overeenkomt met de huidige OEM-code tabel van het systeem.
- `Unicode` Maakt gebruik van UTF-16 met de byte volgorde little endian.
- `UTF7` Maakt gebruik van UTF-7.
- `UTF8` Maakt gebruik van UTF-8.
- `UTF32` Maakt gebruik van UTF-32 met de byte volgorde little endian.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Unicode
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.

Hiermee wordt de cmdlet zo nodig gewist van het alleen-lezen kenmerk van het uitvoer bestand. De cmdlet probeert het kenmerk alleen-lezen opnieuw in te stellen wanneer de opdracht is voltooid.

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

### -Input object

Geeft het object aan dat moet worden geconverteerd. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald. U kunt ook objecten pipeen naar `Export-Clixml` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u het pad op naar het bestand waarin de XML-weer gave van het object wordt opgeslagen. In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt zoals deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

Geeft aan dat de cmdlet de inhoud van een bestaand bestand niet overschrijft. Als een bestand bestaat in het opgegeven pad, wordt standaard `Export-Clixml` het bestand overschreven zonder dat er een waarschuwing wordt gegeven.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad op naar het bestand waarin de XML-weer gave van het object wordt opgeslagen.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
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

## INVOER

### System. Management. Automation. PSObject

U kunt elk object pijp lijnen naar `Export-Clixml` .

## UITVOER

### System. IO. file info

`Export-Clixml` Hiermee maakt u een bestand dat de XML bevat.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[ConvertTo-Html](ConvertTo-Html.md)

[ConvertTo-Xml](ConvertTo-Xml.md)

[Exporteren-CSV](Export-Csv.md)

[Import-Clixml](Import-Clixml.md)

[Pad voor samen voegen](../Microsoft.PowerShell.Management/Join-Path.md)

[Referenties veilig opslaan op schijf](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[Power shell gebruiken om referenties door te geven aan verouderde systemen](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

[Windows. Security. Cryptography. DataProtection](/uwp/api/windows.security.cryptography.dataprotection)
