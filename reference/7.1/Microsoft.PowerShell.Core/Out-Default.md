---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-default?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Default
ms.openlocfilehash: c1293b93079fed439c42d6ba41747cbe6a0c33fe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251294"
---
# Out-Default

## SAMENVATTING
Hiermee wordt de uitvoer naar de standaard Formatter en naar de standaard uitvoer-cmdlet verzonden.

## SYNTAXIS

```
Out-Default [-Transcript] [-InputObject <PSObject>] [<CommonParameters>]
```

## BESCHRIJVING

Power shell voegt automatisch `Out-Default` aan het einde van elke pijp lijn toe. `Out-Default` bepaalt hoe de object stroom moet worden ingedeeld en uitgevoerd. Als de object stroom een stroom van teken reeksen is, `Out-Default` sluizen deze direct waarmee `Out-Host` de juiste api's worden aangeroepen die door de host worden verschaft. Als de object stroom geen teken reeksen bevat, `Out-Default` inspecteert het object om te bepalen wat er moet gebeuren.
Eerst wordt gekeken naar het object type en wordt bepaald of er een geregistreerde _weer gave_ is voor dit object type.

Power shell definieert XML-schema en een mechanisme (de `Update-FormatData` cmdlet) waar iedereen weer gaven voor een object type kan registreren. U kunt **brede** , **lijst** -, **tabel** -of **aangepaste** weer gaven voor elk object type opgeven. In de weer gaven kunt u opgeven welke eigenschappen moeten worden weer gegeven en hoe deze moeten worden weer gegeven. Als een weer gave is geregistreerd, wordt gedefinieerd welke formatter moet worden gebruikt. Dus als de geregistreerde weer gave een **tabel** weergave is, worden `Out-Default` de objecten naar gestreamd `Format-Table | Out-Host` . `Format-Table` transformeert de objecten naar een stroom met opmaak records (aangedreven door de gegevens in de weergave definitie) en `Out-Host` transformeert de indelings records in aanroepen van de host-interface.

## VOORBEELDEN

### Voorbeeld 1

Hoewel deze cmdlet niet bedoeld is om rechtstreeks door de eind gebruiker te worden uitgevoerd, kan het zijn.

```powershell
Get-Process | Select-Object -First 5 | Out-Default
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     12     2.56       5.20       0.00    7376   0 aesm_service
     48    34.32      18.10      26.64    9320  13 AlertusDesktopAlert
     24    13.97      12.74       0.77   12656  13 ApplicationFrameHost
      8     1.79       4.41       0.00    8180   0 AppVShNotify
      9     1.99       5.07       0.19   19320  13 AppVShNotify
```

## PARAMETERS

### -Input object

Hiermee wordt invoer naar de cmdlet geaccepteerd.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Transcript

Hiermee wordt bepaald of de uitvoer naar de transcriptie-services van Power shell moet worden verzonden.

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

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Format-Custom](../Microsoft.PowerShell.Utility/Format-Custom.md)

[Format-List](../Microsoft.PowerShell.Utility/Format-List.md)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Format-Wide](../Microsoft.PowerShell.Utility/Format-Wide.md)

[about_Format.ps1XML](About/about_Format.ps1xml.md)

[Hoe Power shell-opmaak en-uitvoer echt werkt](https://devblogs.microsoft.com/powershell/how-powershell-formatting-and-outputting-really-works/)

