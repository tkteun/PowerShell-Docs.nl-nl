---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-temporaryfile?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TemporaryFile
ms.openlocfilehash: c4bfe6b4ed04ae638421c18f5095403057dc03c9
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249547"
---
# New-TemporaryFile

## SAMENVATTING
Hiermee maakt u een tijdelijk bestand.

## SYNTAXIS

```
New-TemporaryFile [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

Met deze cmdlet maakt u tijdelijke bestanden die u in scripts kunt gebruiken.

`New-TemporaryFile`Met de cmdlet maakt u een leeg bestand met de `.tmp` bestandsnaam extensie.
Met deze cmdlet wordt het bestand met `tmp<NNNN>.tmp` `<NNNN>` een wille keurig hexadecimaal getal benoemt.
Met de cmdlet maakt u het bestand in de map **temp** .

Deze cmdlet gebruikt de methode [Path. GetTempPath ()](/dotnet/api/system.io.path.gettemppath) om de map **temp** te vinden. Deze methode controleert op het bestaan van omgevings variabelen in de volgende volg orde en maakt gebruik van het eerste pad dat is gevonden:

- Op Windows-platforms:

  1. Het pad dat is opgegeven door de variabele TMP-omgeving.
  1. Het pad dat wordt opgegeven door de omgevings variabele TEMP.
  1. Het pad dat is opgegeven door de omgevings variabele USERPROFILE.
  1. De Windows-map.

- Op niet-Windows-platforms: gebruikt het pad dat is opgegeven door de omgevings variabele TMPDIR.

## VOORBEELDEN

### Voor beeld 1: een tijdelijk bestand maken

```powershell
$TempFile = New-TemporaryFile
```

Met deze opdracht wordt een `.tmp` bestand in de tijdelijke map gegenereerd en wordt een verwijzing naar het bestand in de `$TempFile` variabele opgeslagen. U kunt dit bestand later in uw script gebruiken.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

## UITVOER

### System. IO. file info

Met deze cmdlet wordt een **file info** -object geretourneerd dat het tijdelijke bestand vertegenwoordigt.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN
