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
# <span data-ttu-id="1320e-103">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="1320e-103">Get-PSReadLineOption</span></span>

## <span data-ttu-id="1320e-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1320e-104">SYNOPSIS</span></span>
<span data-ttu-id="1320e-105">Hiermee worden waarden opgehaald voor de opties die kunnen worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="1320e-105">Gets values for the options that can be configured.</span></span>

## <span data-ttu-id="1320e-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1320e-106">SYNTAX</span></span>

```
Get-PSReadLineOption [<CommonParameters>]
```

## <span data-ttu-id="1320e-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1320e-107">DESCRIPTION</span></span>

<span data-ttu-id="1320e-108">De `Get-PSReadLineOption` cmdlet retourneert de huidige status van de instellingen die kunnen worden geconfigureerd met behulp van de `Set-PSReadLineOption` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1320e-108">The `Get-PSReadLineOption` cmdlet returns the current state of the settings that can be configured by using the `Set-PSReadLineOption` cmdlet.</span></span> <span data-ttu-id="1320e-109">U kunt het geretourneerde object gebruiken om opties voor **PSReadLine** te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="1320e-109">You can use the returned object to change **PSReadLine** options.</span></span> <span data-ttu-id="1320e-110">Dit biedt een iets eenvoudiger manier om opties voor syntaxis kleuren in te stellen voor meerdere soorten tokens.</span><span class="sxs-lookup"><span data-stu-id="1320e-110">This provides a slightly simpler way to set syntax coloring options for multiple kinds of tokens.</span></span>

## <span data-ttu-id="1320e-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1320e-111">EXAMPLES</span></span>

### <span data-ttu-id="1320e-112">Voor beeld 1: opties en waarden ophalen</span><span class="sxs-lookup"><span data-stu-id="1320e-112">Example 1: Get options and their values</span></span>

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

<span data-ttu-id="1320e-113">Met deze opdracht wordt de lijst met beschik bare PSReadLine-opties en de huidige waarden ervan geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1320e-113">This command returns the list of available PSReadLine options and their current values.</span></span>

## <span data-ttu-id="1320e-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1320e-114">PARAMETERS</span></span>

### <span data-ttu-id="1320e-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1320e-115">CommonParameters</span></span>

<span data-ttu-id="1320e-116">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1320e-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1320e-117">Zie [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1320e-117">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1320e-118">INVOER</span><span class="sxs-lookup"><span data-stu-id="1320e-118">INPUTS</span></span>

### <span data-ttu-id="1320e-119">Geen</span><span class="sxs-lookup"><span data-stu-id="1320e-119">None</span></span>

<span data-ttu-id="1320e-120">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="1320e-120">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="1320e-121">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1320e-121">OUTPUTS</span></span>

### <span data-ttu-id="1320e-122">Micro soft. Power shell. PSConsoleReadLineOptions</span><span class="sxs-lookup"><span data-stu-id="1320e-122">Microsoft.PowerShell.PSConsoleReadLineOptions</span></span>

<span data-ttu-id="1320e-123">Een exemplaar van de huidige opties.</span><span class="sxs-lookup"><span data-stu-id="1320e-123">An instance of the current options.</span></span> <span data-ttu-id="1320e-124">Als u de eigenschaps waarden van dit object wijzigt, worden de instellingen in PSReadLine rechtstreeks bijgewerkt zonder aan te roepen `Set-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="1320e-124">Changing the property values of this object updates the settings in PSReadLine directly without invoking `Set-PSReadLineOption`.</span></span>

## <span data-ttu-id="1320e-125">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1320e-125">NOTES</span></span>

## <span data-ttu-id="1320e-126">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1320e-126">RELATED LINKS</span></span>

[<span data-ttu-id="1320e-127">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="1320e-127">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="1320e-128">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="1320e-128">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="1320e-129">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="1320e-129">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="1320e-130">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="1320e-130">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
