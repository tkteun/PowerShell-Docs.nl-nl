---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-host?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Host
ms.openlocfilehash: 98a9d7d5775bd6d92f60035efedc9d97ae7e8618
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251039"
---
# Out-Host

## SAMENVATTING
Verzendt uitvoer naar de opdracht regel.

## SYNTAXIS

### Alles

```
Out-Host [-Paging] [-InputObject <PSObject>] [<CommonParameters>]
```

## BESCHRIJVING

De `Out-Host` cmdlet verzendt uitvoer naar de Power shell-host om weer te geven. Op de host wordt de uitvoer op de opdracht regel weer gegeven. Omdat `Out-Host` de standaard waarde is, hoeft u deze niet op te geven, tenzij u de para meters wilt gebruiken.

`Out-Host` wordt automatisch toegevoegd aan elke opdracht die wordt uitgevoerd. De uitvoer van de pijp lijn wordt door gegeven aan de host die de opdracht uitvoert. `Out-Host` Hiermee worden ANSI-escape reeksen genegeerd. De escape-reeksen worden verwerkt door de host. `Out-Host` Hiermee worden ANSI-escape reeksen aan de host door gegeven zonder te worden geïnterpreteerd of gewijzigd.

## VOORBEELDEN

### Voor beeld 1: uitvoer één pagina per keer weer geven

In dit voor beeld wordt de systeem processen per pagina weer gegeven.

```powershell
Get-Process | Out-Host -Paging
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     30    24.12      36.95      15.86   21004  14 ApplicationFrameHost
     55    24.33      60.48      10.80   12904  14 BCompare
<SPACE> next page; <CR> next line; Q quit
      9     4.71       8.94       0.00   16864  14 explorer
<SPACE> next page; <CR> next line; Q quit
```

`Get-Process` Hiermee worden de systeem processen opgehaald en worden de objecten van de pijp lijn omlaag verzonden. `Out-Host` maakt gebruik van de para meter **paging** om één pagina met gegevens per keer weer te geven.

### Voor beeld 2: een variabele als invoer gebruiken

In dit voor beeld worden objecten gebruikt die zijn opgeslagen in een variabele als invoer voor `Out-Host` .

```powershell
$io = Get-History
Out-Host -InputObject $io
```

`Get-History` Hiermee wordt de geschiedenis van de Power shell-sessie opgehaald en worden de objecten in de `$io` variabele opgeslagen.
`Out-Host` maakt gebruik van de para meter **input object** om de variabele op te geven `$io` en geeft de geschiedenis weer.

## PARAMETERS

### -Input object

Hiermee geeft u de objecten die naar de-console worden geschreven. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

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

### -Paging

Hiermee wordt aangegeven dat `Out-Host` één pagina met uitvoer per keer wordt weer gegeven en wacht op invoer van de gebruiker voordat de resterende pagina's worden weer gegeven. Standaard wordt alle uitvoer op één pagina weer gegeven. De pagina grootte wordt bepaald door de kenmerken van de host.

Druk op de <kbd>spatie</kbd> balk om de volgende uitvoer pagina of de <kbd>Enter</kbd> -toets weer te geven om de volgende uitvoer regel weer te geven. Druk op <kbd>Q</kbd> om af te sluiten.

**Paginering** is vergelijkbaar met de **meer** opdracht.

> [!NOTE]
> De **paginerings** parameter wordt niet ondersteund door de Power shell ISE-host.

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

### System. Management. Automation. PSObject

U kunt objecten naar beneden verplaatsen in de pijp lijn `Out-Host` .

## UITVOER

### Geen

`Out-Host` Er wordt geen uitvoer gegenereerd. Er worden objecten naar de host verzonden om weer te geven.

## OPMERKINGEN

De **paginerings** parameter wordt niet ondersteund door alle Power shell-hosts. Als u bijvoorbeeld de para meter **paging** in het Power shell-ISE gebruikt, wordt de volgende fout weer gegeven: `out-lineoutput : The method or operation is not implemented.`

De cmdlets die de **out** -verb bevatten, `Out-` en objecten niet opdelen. Ze genereren objecten en verzenden ze naar het opgegeven weergave doel. Als u een niet-opgemaakt object naar een `Out-` cmdlet verzendt, verzendt de cmdlet het naar een format-cmdlet voordat deze wordt weer gegeven.

De `Out-` cmdlets hebben geen para meters voor namen of bestands paden. Als u gegevens naar een `Out-` cmdlet wilt verzenden, gebruikt u de pijp lijn om de uitvoer van een Power shell-opdracht naar de cmdlet te verzenden. Of u kunt gegevens opslaan in een variabele en de para meter **input object** gebruiken om de gegevens door te geven aan de cmdlet.

`Out-Host` gegevens worden verzonden, maar er worden geen uitvoer objecten geproduceerd. Als u de uitvoer van `Out-Host` naar de cmdlet pijp lijnt `Get-Member` , `Get-Member` rapporten dat er geen objecten zijn opgegeven.

## GERELATEERDE KOPPELINGEN

[Wissen-host](Clear-Host.md)

[Out-standaard](Out-Default.md)

[Out-file](../Microsoft.PowerShell.Utility/Out-File.md)

[Out-Null](Out-Null.md)

[Out-teken reeks](../Microsoft.PowerShell.Utility/Out-String.md)

[Write-host](../Microsoft.PowerShell.Utility/Write-Host.md)
