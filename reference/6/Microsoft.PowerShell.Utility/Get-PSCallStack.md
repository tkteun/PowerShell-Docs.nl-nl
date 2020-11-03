---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-pscallstack?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSCallStack
ms.openlocfilehash: 0052543842f97dc1a19caae15222fd1b97d49902
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93249267"
---
# Get-PSCallStack

## SAMENVATTING
Hiermee wordt de huidige aanroep stack weer gegeven.

## SYNTAXIS

```
Get-PSCallStack [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **Get-PSCallStack** wordt de huidige aanroep stack weer gegeven.

Hoewel het is ontworpen om te worden gebruikt met de Power Shell-fout opsporing, kunt u deze cmdlet gebruiken om de aanroep stack weer te geven in een script of functie buiten het fout opsporingsprogramma.

Als u de opdracht **Get-PSCallStack** wilt uitvoeren terwijl het fout opsporingsprogramma is, typt `k` of `Get-PSCallStack` .

## VOORBEELDEN

### Voor beeld 1: de aanroep stack ophalen voor een functie

```
PS C:\> function my-alias {
$p = $args[0]
Get-Alias | where {$_.definition -like "*$p"} | format-table definition, name -auto
}
PS C:\ps-test> Set-PSBreakpoint -Command my-alias
Command    : my-alias
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : prompt PS C:\> my-alias Get-Content

Entering debug mode. Use h or ? for help.
Hit Command breakpoint on 'prompt:my-alias'
my-alias get-content
[DBG]: PS C:\ps-test> s
$p = $args[0]
DEBUG: Stepped to ':    $p = $args[0]    '
[DBG]: PS C:\ps-test> s
get-alias | Where {$_.Definition -like "*$p*"} | format-table Definition,
[DBG]: PS C:\ps-test>get-pscallstack

Name        CommandLineParameters         UnboundArguments              Location
----        ---------------------         ----------------              --------
prompt      {}                            {}                            prompt
my-alias    {}                            {get-content}                 prompt
prompt      {}                            {}                            prompt PS C:\> [DBG]: PS C:\ps-test> o
Definition  Name
----------  ----
Get-Content gc
Get-Content cat
Get-Content type
```

Met deze opdracht wordt de cmdlet **Get-PSCallStack** gebruikt voor het weer geven van de aanroep stack voor mijn-alias, een eenvoudige functie die de aliassen voor de naam van een cmdlet ophaalt.

De eerste opdracht voert de functie in bij de Power shell-prompt.
De tweede opdracht maakt gebruik van de cmdlet Set-PSBreakpoint om een onderbrekings punt in te stellen voor de functie My-Alias.
De derde opdracht gebruikt de functie My-Alias om alle aliassen in de huidige sessie op te halen voor de Get-Content-cmdlet.

Het fout opsporingsprogramma breekt op bij de functie aanroep.
Er zijn twee opeenvolgende opdrachten voor het uitvoeren van de functie regel per regel.
Vervolgens wordt de opdracht **Get-PSCallStack** gebruikt om de aanroep stack op te halen.

De laatste opdracht is een Step-Out-opdracht (o) waarmee de fout opsporing wordt afgesloten en het script verder wordt uitgevoerd om te worden voltooid.

## PARAMETERS

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen objecten naar deze cmdlet pipeen.

## UITVOER

### System. Management. Automation. CallStackFrame

**Get-PSCallStack** retourneert een-object dat de items in de aanroep stack vertegenwoordigt.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Format-Table](Format-Table.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)
