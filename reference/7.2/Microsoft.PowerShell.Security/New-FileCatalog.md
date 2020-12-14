---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/new-filecatalog?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-FileCatalog
ms.openlocfilehash: 230f027a021017e948c8c53e5e6d0c092127ad85
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705855"
---
# New-FileCatalog

## SAMENVATTING
`New-FileCatalog` Hiermee maakt u een catalogus bestand met bestands-hashes dat kan worden gebruikt om de authenticiteit van een bestand te valideren.

## SYNTAXIS

```
New-FileCatalog [-CatalogVersion <Int32>] [-CatalogFilePath] <String> [[-Path] <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING

`New-FileCatalog` Hiermee maakt u een [Windows-catalogus bestand](/windows-hardware/drivers/install/catalog-files) voor een set mappen en bestanden. Dit catalogus bestand bevat hashes voor alle bestanden in de gegeven paden. Gebruikers kunnen de catalogus vervolgens distribueren met hun bestanden, zodat gebruikers kunnen valideren of er wijzigingen zijn aangebracht in de mappen sinds de aanmaak tijd van de catalogus.

Catalogus versies 1 en 2 worden ondersteund. Versie 1 maakt gebruik van het (afgeschafte) SHA1 hash-algoritme om bestands-hashes te maken en versie 2 maakt gebruik van SHA256. Catalogus versie 2 wordt niet ondersteund in Windows Server 2008 R2 of Windows 7. U moet Catalog versie 2 gebruiken voor Windows 8, Windows Server 2012 en latere besturings systemen.

## VOORBEELDEN

### Voor beeld 1: een bestands catalogus maken voor `Microsoft.PowerShell.Utility`

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         11/2/2018 11:58 AM            950 Microsoft.PowerShell.Utility.cat
```

## PARAMETERS

### -CatalogFilePath

Een pad naar een bestand of map waar het catalogus bestand (. cat) moet worden geplaatst. Als er een mappad is opgegeven, wordt de standaard bestandsnaam `catalog.cat` gebruikt.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -CatalogVersion

Accepteert `1.0` of `2.0` als mogelijke waarden voor het opgeven van de catalogus versie. `1.0` moet zoveel mogelijk worden gebruikt, aangezien het het onveilige SHA-1-hash-algoritme gebruikt, terwijl `2.0` het beveiligde SHA-256-algoritme wordt gebruikt `1.0` . Dit is echter het enige ondersteunde algoritme voor Windows 7 en Server 2008R2.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Hiermee wordt een pad of matrix met paden geaccepteerd naar bestanden of mappen die moeten worden opgenomen in het catalogus bestand. Als er een map is opgegeven, worden ook alle bestanden in de map opgenomen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

## INVOER

### System. String

De pijp lijn neemt een teken reeks die wordt gebruikt als de naam van de catalogus.

## UITVOER

### System. IO. file info

## OPMERKINGEN

Deze cmdlet is alleen beschikbaar op Windows-platforms.

## GERELATEERDE KOPPELINGEN

[Test-FileCatalog](Test-FileCatalog.md)

[PowerShellGet](/powerShell/module/powershellget)
