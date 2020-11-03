---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-experimentalfeature?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ExperimentalFeature
ms.openlocfilehash: 79884c73bc6e010eb218f1b722d26e0aaa05ef53
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249705"
---
# <span data-ttu-id="efcf0-102">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="efcf0-102">Enable-ExperimentalFeature</span></span>

## <span data-ttu-id="efcf0-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="efcf0-103">SYNOPSIS</span></span>
<span data-ttu-id="efcf0-104">Een experimentele functie inschakelen bij het opstarten van een nieuw exemplaar van Power shell.</span><span class="sxs-lookup"><span data-stu-id="efcf0-104">Enable an experimental feature on startup of new instance of PowerShell.</span></span>

## <span data-ttu-id="efcf0-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="efcf0-105">SYNTAX</span></span>

```
Enable-ExperimentalFeature [-Name] <String[]> [-Scope <ConfigScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="efcf0-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="efcf0-106">DESCRIPTION</span></span>

<span data-ttu-id="efcf0-107">De `Enable-ExperimentalFeature` cmdlet maakt experimentele functies mogelijk door de genoemde experimentele functies toe te voegen aan het `powershell.config.json` instellingen bestand dat in Power shell wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="efcf0-107">The `Enable-ExperimentalFeature` cmdlet enables experimental features by adding the named experimental features to the `powershell.config.json` settings file read on PowerShell startup.</span></span>

<span data-ttu-id="efcf0-108">Deze cmdlet is geïntroduceerd in Power shell 6,2.</span><span class="sxs-lookup"><span data-stu-id="efcf0-108">This cmdlet was introduced in PowerShell 6.2.</span></span>

> [!NOTE]
> <span data-ttu-id="efcf0-109">Wijzigingen in de status van experimentele functies worden alleen van kracht bij het opnieuw opstarten van Power shell</span><span class="sxs-lookup"><span data-stu-id="efcf0-109">Any changes to experimental feature state only takes effect on restart of PowerShell</span></span>

## <span data-ttu-id="efcf0-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="efcf0-110">EXAMPLES</span></span>

### <span data-ttu-id="efcf0-111">Voor beeld 1: een experimentele functie inschakelen</span><span class="sxs-lookup"><span data-stu-id="efcf0-111">Example 1: Enable an experimental feature</span></span>

<span data-ttu-id="efcf0-112">Als deze experimentele functie eerder is uitgeschakeld, wordt het bestand in dit voor beeld `powershell.config.json` bijgewerkt zodat de gebruiker die functie inschakelt nadat Power shell opnieuw is opgestart.</span><span class="sxs-lookup"><span data-stu-id="efcf0-112">In this example, if this experimental feature was previously disabled, then the `powershell.config.json` file is updated for the user to enable that feature once PowerShell is restarted.</span></span>
<span data-ttu-id="efcf0-113">Wanneer het succes is, wordt er niets naar de pijp lijn uitgevoerd en wordt er alleen een waarschuwings bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="efcf0-113">Upon success nothing is output to the pipeline and only a warning message is displayed.</span></span>

```powershell
Enable-ExperimentalFeature PSImplicitRemotingBatching
```

```Output
WARNING: Enabling and disabling experimental features do not take effect until next start of PowerShell.
```

## <span data-ttu-id="efcf0-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="efcf0-114">PARAMETERS</span></span>

### <span data-ttu-id="efcf0-115">-Confirm</span><span class="sxs-lookup"><span data-stu-id="efcf0-115">-Confirm</span></span>

<span data-ttu-id="efcf0-116">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="efcf0-116">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efcf0-117">-Name</span><span class="sxs-lookup"><span data-stu-id="efcf0-117">-Name</span></span>

<span data-ttu-id="efcf0-118">De naam of namen van de experimentele functies die moeten worden ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="efcf0-118">The name or names of the experimental features to enable.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="efcf0-119">-Bereik</span><span class="sxs-lookup"><span data-stu-id="efcf0-119">-Scope</span></span>

<span data-ttu-id="efcf0-120">Hiermee wordt bepaald welke `powershell.config.json` moet worden bijgewerkt of dit van invloed is op alle gebruikers of alleen de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="efcf0-120">Determines which `powershell.config.json` to update whether it affects all users or just the current user.</span></span>

```yaml
Type: System.Management.Automation.Configuration.ConfigScope
Parameter Sets: (All)
Aliases:
Accepted values: AllUsers, CurrentUser

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efcf0-121">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="efcf0-121">-WhatIf</span></span>

<span data-ttu-id="efcf0-122">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="efcf0-122">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="efcf0-123">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="efcf0-123">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efcf0-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="efcf0-124">CommonParameters</span></span>

<span data-ttu-id="efcf0-125">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="efcf0-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="efcf0-126">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="efcf0-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="efcf0-127">INVOER</span><span class="sxs-lookup"><span data-stu-id="efcf0-127">INPUTS</span></span>

### <span data-ttu-id="efcf0-128">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="efcf0-128">ExperimentalFeature</span></span>

<span data-ttu-id="efcf0-129">Pipe-exemplaren van ExperimentalFeature van de `Get-ExperimentalFeature` cmdlet die u wilt inschakelen.</span><span class="sxs-lookup"><span data-stu-id="efcf0-129">Pipe instances of ExperimentalFeature from `Get-ExperimentalFeature` cmdlet to enable.</span></span>

## <span data-ttu-id="efcf0-130">UITVOER</span><span class="sxs-lookup"><span data-stu-id="efcf0-130">OUTPUTS</span></span>

### <span data-ttu-id="efcf0-131">Geen</span><span class="sxs-lookup"><span data-stu-id="efcf0-131">None</span></span>

<span data-ttu-id="efcf0-132">Met deze cmdlet wordt geen uitvoer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="efcf0-132">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="efcf0-133">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="efcf0-133">NOTES</span></span>

<span data-ttu-id="efcf0-134">Wijzigingen in de status van een experimentele functie worden alleen van kracht bij het opnieuw opstarten van Power shell.</span><span class="sxs-lookup"><span data-stu-id="efcf0-134">Changes to state of an experimental feature only take effect on restart of PowerShell.</span></span>

## <span data-ttu-id="efcf0-135">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="efcf0-135">RELATED LINKS</span></span>

[<span data-ttu-id="efcf0-136">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="efcf0-136">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="efcf0-137">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="efcf0-137">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)
