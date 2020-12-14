---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/get-psreadlineoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSReadLineOption
ms.openlocfilehash: 3b2c789225a1d76391015c39e3fc919ba65f0a1b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705915"
---
# <span data-ttu-id="44635-102">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="44635-102">Get-PSReadLineOption</span></span>

## <span data-ttu-id="44635-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="44635-103">SYNOPSIS</span></span>
<span data-ttu-id="44635-104">Hiermee worden waarden opgehaald voor de opties die kunnen worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="44635-104">Gets values for the options that can be configured.</span></span>

## <span data-ttu-id="44635-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="44635-105">SYNTAX</span></span>

```
Get-PSReadLineOption [<CommonParameters>]
```

## <span data-ttu-id="44635-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="44635-106">DESCRIPTION</span></span>

<span data-ttu-id="44635-107">De `Get-PSReadLineOption` cmdlet retourneert de huidige status van de instellingen die kunnen worden geconfigureerd met behulp van de `Set-PSReadLineOption` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="44635-107">The `Get-PSReadLineOption` cmdlet returns the current state of the settings that can be configured by using the `Set-PSReadLineOption` cmdlet.</span></span> <span data-ttu-id="44635-108">U kunt het geretourneerde object gebruiken om opties voor **PSReadLine** te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="44635-108">You can use the returned object to change **PSReadLine** options.</span></span> <span data-ttu-id="44635-109">Dit biedt een iets eenvoudiger manier om opties voor syntaxis kleuren in te stellen voor meerdere soorten tokens.</span><span class="sxs-lookup"><span data-stu-id="44635-109">This provides a slightly simpler way to set syntax coloring options for multiple kinds of tokens.</span></span>

## <span data-ttu-id="44635-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="44635-110">EXAMPLES</span></span>

### <span data-ttu-id="44635-111">Voor beeld 1: opties en waarden ophalen</span><span class="sxs-lookup"><span data-stu-id="44635-111">Example 1: Get options and their values</span></span>

```powershell
Get-PSReadLineOption
```

```Output
EditMode                               : Windows
AddToHistoryHandler                    : System.Func`2[System.String,System.Object]
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

<span data-ttu-id="44635-112">Met deze opdracht wordt de lijst met beschik bare PSReadLine-opties en de huidige waarden ervan geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="44635-112">This command returns the list of available PSReadLine options and their current values.</span></span>

## <span data-ttu-id="44635-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="44635-113">PARAMETERS</span></span>

### <span data-ttu-id="44635-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="44635-114">CommonParameters</span></span>

<span data-ttu-id="44635-115">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="44635-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="44635-116">Zie [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="44635-116">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="44635-117">INVOER</span><span class="sxs-lookup"><span data-stu-id="44635-117">INPUTS</span></span>

### <span data-ttu-id="44635-118">Geen</span><span class="sxs-lookup"><span data-stu-id="44635-118">None</span></span>

<span data-ttu-id="44635-119">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="44635-119">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="44635-120">UITVOER</span><span class="sxs-lookup"><span data-stu-id="44635-120">OUTPUTS</span></span>

### <span data-ttu-id="44635-121">Micro soft. Power shell. PSConsoleReadLineOptions</span><span class="sxs-lookup"><span data-stu-id="44635-121">Microsoft.PowerShell.PSConsoleReadLineOptions</span></span>

<span data-ttu-id="44635-122">Een exemplaar van de huidige opties.</span><span class="sxs-lookup"><span data-stu-id="44635-122">An instance of the current options.</span></span> <span data-ttu-id="44635-123">Als u de eigenschaps waarden van dit object wijzigt, worden de instellingen in PSReadLine rechtstreeks bijgewerkt zonder aan te roepen `Set-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="44635-123">Changing the property values of this object updates the settings in PSReadLine directly without invoking `Set-PSReadLineOption`.</span></span>

## <span data-ttu-id="44635-124">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="44635-124">NOTES</span></span>

## <span data-ttu-id="44635-125">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="44635-125">RELATED LINKS</span></span>

[<span data-ttu-id="44635-126">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="44635-126">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="44635-127">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="44635-127">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="44635-128">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="44635-128">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="44635-129">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="44635-129">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
