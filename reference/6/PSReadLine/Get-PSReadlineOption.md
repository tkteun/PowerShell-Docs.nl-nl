---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/get-psreadlineoption?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSReadLineOption
ms.openlocfilehash: 624978c94c9ed24c07c6dad384236c852b8a7fde
ms.sourcegitcommit: 105c69ecedfe5180d8c12e8015d667c5f1a71579
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/02/2020
ms.locfileid: "93249381"
---
# Get-PSReadLineOption

## SAMENVATTING
Hiermee worden waarden opgehaald voor de opties die kunnen worden geconfigureerd.

## SYNTAXIS

```
Get-PSReadLineOption [<CommonParameters>]
```

## BESCHRIJVING

De `Get-PSReadLineOption` cmdlet retourneert de huidige status van de instellingen die kunnen worden geconfigureerd met behulp van de `Set-PSReadLineOption` cmdlet. U kunt het geretourneerde object gebruiken om opties voor **PSReadLine** te wijzigen. Dit biedt een iets eenvoudiger manier om opties voor syntaxis kleuren in te stellen voor meerdere soorten tokens.

## VOORBEELDEN

### Voor beeld 1: opties en waarden ophalen

```powershell
Get-PSReadLineOption
```

```Output
EditMode                               : Windows
AddToHistoryHandler                    :
HistoryNoDuplicates                    : True
HistorySavePath                        : C:\Users\username\AppData\Roaming\Microsoft\Windows\
                                         PowerShell\PSReadLine\ConsoleHost_history.txt
HistorySaveStyle                       : SaveIncrementally
HistorySearchCaseSensitive             : False
HistorySearchCursorMovesToEnd          : False
MaximumHistoryCount                    : 4096
ContinuationPrompt                     : >>
ExtraPromptLineCount                   : 0
PromptText                             : {> }
BellStyle                              : Audible
DingDuration                           : 50
DingTone                               : 1221
CommandsToValidateScriptBlockArguments : {ForEach-Object, %, Invoke-Command, icm...}
CommandValidationHandler               :
CompletionQueryItems                   : 100
MaximumKillRingCount                   : 10
ShowToolTips                           : True
ViModeIndicator                        : None
WordDelimiters                         : ;:,.[]{}()/\|^&*-=+'"---
AnsiEscapeTimeout                      : 100
CommandColor                           : "`e[93m"
CommentColor                           : "`e[32m"
ContinuationPromptColor                : "`e[97m"
DefaultTokenColor                      : "`e[97m"
EmphasisColor                          : "`e[96m"
ErrorColor                             : "`e[91m"
KeywordColor                           : "`e[92m"
MemberColor                            : "`e[97m"
NumberColor                            : "`e[97m"
OperatorColor                          : "`e[90m"
ParameterColor                         : "`e[90m"
SelectionColor                         : "`e[30;107m"
StringColor                            : "`e[36m"
TypeColor                              : "`e[37m"
VariableColor                          : "`e[92m"
```

Met deze opdracht wordt de lijst met beschik bare PSReadLine-opties en de huidige waarden ervan geretourneerd.

## PARAMETERS

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen objecten naar deze cmdlet pipeen.

## UITVOER

### Micro soft. Power shell. PSConsoleReadLineOptions

Een exemplaar van de huidige opties. Als u de eigenschaps waarden van dit object wijzigt, worden de instellingen in PSReadLine rechtstreeks bijgewerkt zonder aan te roepen `Set-PSReadLineOption` .

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Remove-PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)

[Get-PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[Set-PSReadLineOption](Set-PSReadLineOption.md)

[Set-PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)
