---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Error
ms.openlocfilehash: c29115a65b46d38039d78b10eee293e6944cede5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250224"
---
# Get-Error

## SAMENVATTING

Hiermee worden de meest recente fout berichten uit de huidige sessie opgehaald en weer gegeven.

## SYNTAXIS

### Nieuwste (standaard)

```
Get-Error [[-Newest] <Int32>] [<CommonParameters>]
```

### Fout

```
Get-Error [-InputObject <PSObject>] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Get-Error` cmdlet wordt een **PSExtendedError** -object opgehaald dat de huidige fout Details vertegenwoordigt van de laatste fout die in de sessie is opgetreden.

U kunt gebruiken `Get-Error` om een opgegeven aantal fouten weer te geven dat in de huidige sessie is opgetreden met de **nieuwste** para meter.

De `Get-Error` cmdlet ontvangt ook fout objecten uit een verzameling, zoals `$Error` , om meerdere fouten van de huidige sessie weer te geven.

## VOORBEELDEN

### Voor beeld 1: de meest recente fout Details ophalen

In dit voor beeld `Get-Error` worden de details weer gegeven van de meest recente fout die is opgetreden in de huidige sessie.

```powershell
Get-Childitem -path /NoRealDirectory
Get-Error
```

```
Get-ChildItem: Cannot find path 'C:\NoRealDirectory' because it does not exist.

Exception             :
    ErrorRecord          :
        Exception             :
            Message : Cannot find path 'C:\NoRealDirectory' because it does not exist.
            HResult : -2146233087
        TargetObject          : C:\NoRealDirectory
        CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [], ParentContainsErrorRecordException
        FullyQualifiedErrorId : PathNotFound
    ItemName             : C:\NoRealDirectory
    SessionStateCategory : Drive
    TargetSite           :
        Name          : GetChildItems
        DeclaringType : System.Management.Automation.SessionStateInternal
        MemberType    : Method
        Module        : System.Management.Automation.dll
    StackTrace           :
   at System.Management.Automation.SessionStateInternal.GetChildItems(String path, Boolean recurse, UInt32 depth,
CmdletProviderContext context)
   at System.Management.Automation.ChildItemCmdletProviderIntrinsics.Get(String path, Boolean recurse, UInt32
depth, CmdletProviderContext context)
   at Microsoft.PowerShell.Commands.GetChildItemCommand.ProcessRecord()
    Message              : Cannot find path 'C:\NoRealDirectory' because it does not exist.
    Source               : System.Management.Automation
    HResult              : -2146233087
TargetObject          : C:\NoRealDirectory
CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [Get-ChildItem], ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
InvocationInfo        :
    MyCommand        : Get-ChildItem
    ScriptLineNumber : 1
    OffsetInLine     : 1
    HistoryId        : 57
    Line             : Get-Childitem -path c:\NoRealDirectory
    PositionMessage  : At line:1 char:1
                       + Get-Childitem -path c:\NoRealDirectory
                       + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    InvocationName   : Get-Childitem
    CommandOrigin    : Internal
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo :
```

### Voor beeld 2: het opgegeven aantal fout berichten ophalen dat is opgetreden in de huidige sessie

In dit voor beeld ziet u hoe u `Get-Error` met de **nieuwste** para meter kunt gebruiken. In dit voor beeld retourneert **nieuwste** de details van de drie nieuwste fouten die zijn opgetreden tijdens deze sessie.

```powershell
Get-Error -Newest 3
```

### Voor beeld 3: een verzameling fouten verzenden om gedetailleerde berichten te ontvangen

De `$Error` Automatische variabele bevat een matrix met fout objecten in de huidige sessie. De matrix van objecten kan worden gepiped om `Get-Error` gedetailleerde fout berichten te ontvangen.

In dit voor beeld `$Error` wordt het pipet naar de `Get-Error` cmdlet. het resultaat is een lijst met gedetailleerde fout berichten, vergelijkbaar met het resultaat van voor beeld 1.

```powershell
$Error | Get-Error
```

## PARAMETERS

### -Nieuwste

Hiermee geeft u het aantal fouten op dat moet worden weer gegeven tijdens de huidige sessie.

```yaml
Type: System.Int32
Parameter Sets: Newest
Aliases: Last

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Deze para meter wordt gebruikt voor de invoer van de pijp lijn.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Error
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### PSObject

Ondersteunt invoer van elk **PSObject** , maar de resultaten variëren, tenzij een **ErrorRecord** of een **uitzonderings** object worden opgegeven.

## UITVOER

### System. Management. Automation. ErrorRecord # PSExtendedError

Uitvoer in een **PSExtendedError** -object.

## OPMERKINGEN

`Get-Error` accepteert invoer van de pijp lijn. Bijvoorbeeld `$Error | Get-Error`.

## GERELATEERDE KOPPELINGEN

[about_Try_Catch_Finally](../Microsoft.PowerShell.Core/About/about_Try_Catch_Finally.md)
