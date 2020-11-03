---
external help file: Get-DscConfigurationStatus.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfigurationStatus
ms.openlocfilehash: 0d59ce58a70eab68441ea1fe6097bbdf7792a54f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250782"
---
# <span data-ttu-id="2041c-103">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="2041c-103">Get-DscConfigurationStatus</span></span>

## <span data-ttu-id="2041c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2041c-104">SYNOPSIS</span></span>
<span data-ttu-id="2041c-105">Haalt gegevens op over voltooide configuratie-uitvoeringen.</span><span class="sxs-lookup"><span data-stu-id="2041c-105">Retrieves data about completed configuration runs.</span></span>

## <span data-ttu-id="2041c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2041c-106">SYNTAX</span></span>

```
Get-DscConfigurationStatus [-All] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [<CommonParameters>]
```

## <span data-ttu-id="2041c-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2041c-107">DESCRIPTION</span></span>
<span data-ttu-id="2041c-108">De cmdlet **Get-DscConfigurationStatus** haalt gedetailleerde informatie op over voltooide configuratie-uitvoeringen op het systeem.</span><span class="sxs-lookup"><span data-stu-id="2041c-108">The **Get-DscConfigurationStatus** cmdlet retrieves detailed information about completed configuration runs on the system.</span></span>
<span data-ttu-id="2041c-109">Standaard wordt de informatie over de laatste configuratie-uitvoering geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2041c-109">By default, it returns the information about the last configuration run.</span></span>
<span data-ttu-id="2041c-110">Deze cmdlet is handig voor het vinden van historische informatie over configuratie runs, zoals wanneer de configuraties werden uitgevoerd, de status van de uitvoeringen, het aantal resources in de configuraties en welke resources zijn geslaagd of mislukt.</span><span class="sxs-lookup"><span data-stu-id="2041c-110">This cmdlet is useful for finding historical information about configuration runs, such as when the configurations were run, the status of the runs, the number of resources in the configurations, and which resources succeeded or failed.</span></span>

## <span data-ttu-id="2041c-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2041c-111">EXAMPLES</span></span>

### <span data-ttu-id="2041c-112">Voor beeld 1: informatie over de laatste configuratie-uitvoering ophalen</span><span class="sxs-lookup"><span data-stu-id="2041c-112">Example 1: Get information on the last configuration run</span></span>

```
PS C:\> Get-DscConfigurationStatus
```

<span data-ttu-id="2041c-113">Met deze opdracht wordt informatie over de laatste configuratie-uitvoering opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2041c-113">This command gets information on the last configuration run.</span></span>

### <span data-ttu-id="2041c-114">Voor beeld 2: informatie over alle configuraties ophalen</span><span class="sxs-lookup"><span data-stu-id="2041c-114">Example 2: Get information on all configurations</span></span>

```
PS C:\> Get-DscConfigurationStatus -All
```

<span data-ttu-id="2041c-115">Met deze opdracht wordt informatie opgehaald over alle configuraties die op het systeem zijn uitgevoerd, inclusief de consistentie controle van de desired state Configuration (DSC) van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="2041c-115">This command gets information about all the configurations that were run on the system, including the Windows PowerShell Desired State Configuration (DSC) consistency check.</span></span>

### <span data-ttu-id="2041c-116">Voor beeld 3: informatie over de configuratie uitvoeren op een externe computer</span><span class="sxs-lookup"><span data-stu-id="2041c-116">Example 3: Get information on the configuration run on a remote computer</span></span>

```
PS C:\> Get-DscConfigurationStatus -CimSession "Server01"
```

<span data-ttu-id="2041c-117">Met deze opdracht worden de details van de configuratie-uitvoering opgehaald van de externe computer met de naam Server01.</span><span class="sxs-lookup"><span data-stu-id="2041c-117">This command gets the configuration run details of the remote computer named Server01.</span></span>
<span data-ttu-id="2041c-118">Dit maakt gebruik van het WSMan-Trans Port om verbinding te maken met de externe computer en vereist dat de gebruiker die de verbinding maakt, een beheerder is op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="2041c-118">This uses the WSMan transport to connect to the remote computer and requires that the connecting user be an administrator on the remote computer.</span></span>

## <span data-ttu-id="2041c-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2041c-119">PARAMETERS</span></span>

### <span data-ttu-id="2041c-120">-Alle</span><span class="sxs-lookup"><span data-stu-id="2041c-120">-All</span></span>
<span data-ttu-id="2041c-121">Geeft aan dat deze cmdlet informatie ophaalt over alle configuratie runs op de computer, met inbegrip van de configuratie toepassing en de consistentie controle.</span><span class="sxs-lookup"><span data-stu-id="2041c-121">Indicates that this cmdlet retrieves information about all the configuration runs on the computer, including the configuration application and the consistency check.</span></span>

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

### <span data-ttu-id="2041c-122">-AsJob</span><span class="sxs-lookup"><span data-stu-id="2041c-122">-AsJob</span></span>
<span data-ttu-id="2041c-123">Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="2041c-123">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="2041c-124">-CimSession</span><span class="sxs-lookup"><span data-stu-id="2041c-124">-CimSession</span></span>
<span data-ttu-id="2041c-125">Voert de cmdlet uit in een externe sessie of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="2041c-125">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="2041c-126">Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) of [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="2041c-126">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="2041c-127">De standaard waarde is de huidige sessie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="2041c-127">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2041c-128">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="2041c-128">-ThrottleLimit</span></span>
<span data-ttu-id="2041c-129">Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2041c-129">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="2041c-130">Als deze para meter wordt wegge laten of een waarde van `0` wordt ingevoerd, wordt in Windows Power shell een optimale bandbreedte limiet voor de cmdlet berekend op basis van het aantal CIM-cmdlets dat op de computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2041c-130">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="2041c-131">De beperkings limiet geldt alleen voor de huidige cmdlet, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="2041c-131">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="2041c-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2041c-132">CommonParameters</span></span>
<span data-ttu-id="2041c-133">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2041c-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2041c-134">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2041c-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2041c-135">INVOER</span><span class="sxs-lookup"><span data-stu-id="2041c-135">INPUTS</span></span>

## <span data-ttu-id="2041c-136">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2041c-136">OUTPUTS</span></span>

## <span data-ttu-id="2041c-137">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2041c-137">NOTES</span></span>

## <span data-ttu-id="2041c-138">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2041c-138">RELATED LINKS</span></span>

[<span data-ttu-id="2041c-139">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="2041c-139">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="2041c-140">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2041c-140">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="2041c-141">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2041c-141">Get-DscLocalConfigurationManager</span></span>](Get-DscLocalConfigurationManager.md)

[<span data-ttu-id="2041c-142">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2041c-142">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="2041c-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2041c-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="2041c-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2041c-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
