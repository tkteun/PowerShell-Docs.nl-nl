---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-formatdata?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-FormatData
ms.openlocfilehash: 8e04de16aebc467360c7f9b02de6681ddc3e7ca3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251078"
---
# Update-FormatData

## SAMENVATTING
Hiermee werkt u de opmaak gegevens in de huidige sessie bij.

## SYNTAXIS

```
Update-FormatData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING

`Update-FormatData`Met de cmdlet worden de opmaak gegevens opnieuw geladen van indelings bestanden in de huidige sessie. Met deze cmdlet kunt u de opmaak gegevens bijwerken zonder Power shell opnieuw te starten.

Zonder para meters worden `Update-FormatData` de indelings bestanden die eerder zijn geladen, opnieuw geladen.
U kunt de para meters van gebruiken `Update-FormatData` om nieuwe indelings bestanden toe te voegen aan de sessie.

Indelings bestanden zijn tekst bestanden in XML-indeling met de `format.ps1xml` bestandsnaam extensie. De indelings gegevens in de bestanden definiëren de weer gave van Microsoft .NET Framework-objecten in de sessie.

Wanneer Power shell wordt gestart, worden de indelings gegevens van de Power shell-bron code geladen. U kunt echter aangepaste format.ps1XML-bestanden maken om de opmaak in de huidige sessie bij te werken. U kunt gebruiken `Update-FormatData` om de opmaak gegevens opnieuw te laden in de huidige sessie zonder Power shell opnieuw te starten. Dit is handig wanneer u een opmaak bestand hebt toegevoegd of gewijzigd, maar de sessie niet wilt onderbreken.

Zie [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)voor meer informatie over het format teren van bestanden in Power shell.

## VOORBEELDEN

### Voor beeld 1: eerder geladen indelings bestanden opnieuw laden

```powershell
Update-FormatData
```

Met deze opdracht worden de indelings bestanden die eerder zijn geladen, opnieuw geladen.

### Voor beeld 2: indelings bestanden en tracerings-en logboek bestanden opnieuw laden

```powershell
Update-FormatData -AppendPath "trace.format.ps1xml, log.format.ps1xml"
```

Met deze opdracht worden de indelings bestanden opnieuw geladen in de sessie, met inbegrip van twee nieuwe bestanden, Trace.format.ps1XML-en Log.format.ps1XML-bestand.

Omdat de opdracht gebruikmaakt van de para meter **AppendPath** , worden de opmaak gegevens in de nieuwe bestanden geladen na het format teren van de gegevens uit de ingebouwde bestanden.

De para meter **AppendPath** wordt gebruikt omdat de nieuwe bestanden opmaak gegevens bevatten voor objecten waarnaar niet wordt verwezen in de ingebouwde bestanden.

### Voor beeld 3: een opmaak bestand bewerken en opnieuw laden

```powershell
Update-FormatData -PrependPath "c:\test\NewFiles.format.ps1xml"

# Edit the NewFiles.format.ps1 file.

Update-FormatData
```

In dit voor beeld ziet u hoe u een opmaak bestand opnieuw kunt laden nadat u het hebt bewerkt.

Met de eerste opdracht wordt het NewFiles.format.ps1XML-bestand aan de sessie toegevoegd. De para meter **PrependPath** wordt gebruikt omdat het bestand opmaak gegevens bevat voor objecten waarnaar wordt verwezen in de ingebouwde bestanden.

Nadat u het XML-bestand NewFiles.format.ps1hebt toegevoegd en het in deze sessies hebt getest, bewerkt de auteur het bestand.

De tweede opdracht gebruikt de `Update-FormatData` cmdlet om de indelings bestanden opnieuw te laden. Omdat het XML-bestand van de NewFiles.format.ps1eerder is geladen, wordt `Update-FormatData` het automatisch opnieuw geladen zonder para meters te gebruiken.

## PARAMETERS

### -AppendPath

Hiermee geeft u indelings bestanden die met deze cmdlet worden toegevoegd aan de sessie. De bestanden worden geladen nadat Power shell de ingebouwde opmaak bestanden heeft geladen.

Bij het format teren van .NET-objecten gebruikt Power shell de eerste opmaak definitie die wordt gevonden voor elk .NET-type. Als u de para meter **AppendPath** gebruikt, zoekt Power shell de gegevens van de ingebouwde bestanden voordat deze de opmaak gegevens detecteert die u toevoegt.

Gebruik deze para meter om een bestand toe te voegen waarmee een .NET-object wordt opgemaakt waarnaar niet wordt verwezen in de ingebouwde opmaak bestanden.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -PrependPath

Hiermee geeft u indelings bestanden die met deze cmdlet worden toegevoegd aan de sessie. De bestanden worden geladen voordat Power shell de ingebouwde indelings bestanden laadt.

Bij het format teren van .NET-objecten gebruikt Power shell de eerste opmaak definitie die wordt gevonden voor elk .NET-type. Als u de para meter **PrependPath** gebruikt, zoekt Power shell de gegevens van de bestanden die u toevoegt voordat de opmaak gegevens van de ingebouwde bestanden worden aangetroffen.

Gebruik deze para meter om een bestand toe te voegen waarmee een .NET-object wordt opgemaakt waarnaar ook wordt verwezen in de ingebouwde opmaak bestanden.

```yaml
Type: System.String[]
Parameter Sets: (All)
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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks die het pad toevoegen bevat door sluizen naar `Update-FormatData` .

## UITVOER

### Geen

De cmdlet retourneert geen uitvoer.

## OPMERKINGEN

- `Update-FormatData` werkt ook de opmaak gegevens bij voor opdrachten in de sessie die uit modules zijn geïmporteerd. Als het opmaak bestand voor een module wordt gewijzigd, kunt u een `Update-FormatData` opdracht uitvoeren om de opmaak gegevens voor geïmporteerde opdrachten bij te werken. U hoeft de module niet opnieuw te importeren.

## GERELATEERDE KOPPELINGEN

[Get-FormatData](Get-FormatData.md)

[Exporteren-FormatData](Export-FormatData.md)
