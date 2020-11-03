---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Content
ms.openlocfilehash: b318abb06d36be5e28b9dcc3dc62fd4a70ab38fb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250833"
---
# Clear-Content

## SAMENVATTING
Hiermee verwijdert u de inhoud van een item, maar verwijdert u het item niet.

## SYNTAXIS

### Pad (standaard)

```
Clear-Content [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [-Stream <String>] [<CommonParameters>]
```

### LiteralPath

```
Clear-Content -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [-Stream <String>] [<CommonParameters>]
```

## BESCHRIJVING

De `Clear-Content` cmdlet verwijdert de inhoud van een item, zoals het verwijderen van de tekst uit een bestand, maar het item wordt niet verwijderd.
Als gevolg hiervan bestaat het item wel, maar is het leeg.
Het `Clear-Content` is vergelijkbaar met `Clear-Item` , maar het werkt op items met inhoud in plaats van items met waarden.

## VOORBEELDEN

### Voor beeld 1: alle inhoud uit een map verwijderen

```powershell
Clear-Content "..\SmpUsers\*\init.txt"
```

Met deze opdracht wordt alle inhoud verwijderd uit de "init.txt"-bestanden in alle submappen van de SmpUsers-map.
De bestanden worden niet verwijderd, maar ze zijn leeg.

### Voor beeld 2: inhoud van alle bestanden met een Joker teken verwijderen

```powershell
Clear-Content -Path "*" -Filter "*.log" -Force
```

Met deze opdracht wordt de inhoud van alle bestanden in de huidige map verwijderd met de bestandsnaam extensie. log, inclusief bestanden met het kenmerk alleen-lezen.
Het sterretje ( \* ) in het pad staat voor alle items in de huidige map.
Met de para meter **Force** is de opdracht geldig voor alleen-lezen bestanden.
Het gebruik van een filter om de opdracht te beperken tot bestanden met de bestandsnaam extensie. log in plaats van op te geven \* . in het pad wordt de bewerking sneller uitgevoerd.

### Voor beeld 3: alle gegevens uit een stroom wissen

In dit voor beeld ziet u hoe de `Clear-Content` cmdlet de inhoud uit een alternatieve gegevens stroom wist terwijl de stroom intact blijft.

De eerste opdracht gebruikt de `Get-Content` cmdlet om de inhoud van de zone. id-stroom op te halen in het Copy-Script.ps1 bestand, dat is gedownload van het internet.

Met de tweede opdracht wordt de- `Clear-Content` cmdlet gebruikt om de inhoud te wissen.

Met de derde opdracht wordt de eerste opdracht herhaald. Er wordt gecontroleerd of de inhoud is gewist, maar de stroom blijft. Als de stroom is verwijderd, wordt door de opdracht een fout gegenereerd.

U kunt een methode als deze gebruiken om de inhoud van een alternatieve gegevens stroom te wissen. Het is echter niet de aanbevolen manier om beveiligings controles te elimineren waarmee bestanden die worden gedownload van Internet, worden geblokkeerd. Als u controleert of een gedownload bestand veilig is, gebruikt u de `Unblock-File` cmdlet.

```powershell
Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
[ZoneTransfer]
ZoneId=3
```

```powershell
Clear-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output

```

## PARAMETERS

### -Credential

> [!NOTE]
> Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell. Gebruik invoke-Command om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Uitsluiten

Hiermee geeft u als teken reeks matrix teken reeksen op die met deze cmdlet worden wegge laten van het pad naar de inhoud.
De waarde van deze para meter komt in aanmerking voor de para meter **Path** .
Voer een element of patroon van een pad in, zoals *. txt.
Joker tekens zijn toegestaan.

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

Hiermee geeft u een filter op in de indeling of taal van de provider.
De waarde van deze para meter komt in aanmerking voor de para meter **Path** .
De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.
Filters zijn efficiënter dan andere para meters, omdat de provider deze toepast tijdens het ophalen van de objecten, in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.

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

### -Force

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.

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

### -Include

Hiermee geeft u als een teken reeks matrix inhoud op die door deze cmdlet wordt gewist.
De waarde van deze para meter komt in aanmerking voor de para meter **Path** .
Voer een element of patroon van een pad in, zoals *. txt.
Joker tekens zijn toegestaan.

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

### -LiteralPath

Hiermee geeft u de paden op naar de items waarvan de inhoud wordt verwijderd.
In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.
Geen tekens worden geïnterpreteerd als joker tekens.
Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.
Enkele aanhalings tekens geven aan dat Power shell geen karakters kan interpreteren als escape reeksen.

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

### -Path

Hiermee geeft u de paden op naar de items waarvan de inhoud wordt verwijderd.
Joker tekens zijn toegestaan.
De paden moeten paden naar items zijn en niet naar containers.
U moet bijvoorbeeld een pad naar een of meer bestanden opgeven, niet een pad naar een map.
Joker tekens zijn toegestaan.
Deze para meter is vereist, maar de parameter naam ("pad") is optioneel.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Stream

Hiermee geeft u een alternatieve gegevens stroom voor inhoud.
Als de stroom niet bestaat, wordt deze gemaakt met deze cmdlet.
Joker tekens worden niet ondersteund.

**Stream** is een dynamische para meter waaraan de File System Provider toevoegt `Clear-Content` .
Deze para meter werkt alleen op stations met een bestands systeem.

U kunt de- `Clear-Content` cmdlet gebruiken om de inhoud van de zone te wijzigen. id alternatieve gegevens stroom.
Dit wordt echter niet aangeraden als een manier om beveiligings controles te elimineren waarmee bestanden die worden gedownload van Internet, worden geblokkeerd.
Als u controleert of een gedownload bestand veilig is, gebruikt u de `Unblock-File` cmdlet.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String
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
Zie [about_transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)voor meer informatie.

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

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

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

Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` . Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### Geen

U kunt geen objecten pipeen naar `Clear-Content` .

## UITVOER

### Geen

Met deze cmdlet worden geen objecten geretourneerd.

## OPMERKINGEN

U kunt gebruiken `Clear-Content` met de Power shell-bestandssysteem provider en met andere providers die inhoud bewerken.
Als u items wilt wissen die niet worden beschouwd als inhoud, zoals items die worden beheerd door het Power shell-certificaat of register providers, gebruikt u `Clear-Item` .

De `Clear-Content` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.
Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PsProvider` .
Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Add-content](Add-Content.md)

[Get-Content](Get-Content.md)

[Get-item](Get-Item.md)

[Set-Content](Set-Content.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
