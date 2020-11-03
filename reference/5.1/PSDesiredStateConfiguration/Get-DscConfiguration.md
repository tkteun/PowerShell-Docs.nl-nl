---
external help file: Get-DSCConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfiguration
ms.openlocfilehash: 42b24e72de4c4bcc9326d52861c08a05853b18e0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250780"
---
# <span data-ttu-id="672cc-103">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="672cc-103">Get-DscConfiguration</span></span>

## <span data-ttu-id="672cc-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="672cc-104">SYNOPSIS</span></span>
<span data-ttu-id="672cc-105">Hiermee wordt de huidige configuratie van de knoop punten opgehaald.</span><span class="sxs-lookup"><span data-stu-id="672cc-105">Gets the current configuration of the nodes.</span></span>

## <span data-ttu-id="672cc-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="672cc-106">SYNTAX</span></span>

```
Get-DscConfiguration [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [<CommonParameters>]
```

## <span data-ttu-id="672cc-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="672cc-107">DESCRIPTION</span></span>
<span data-ttu-id="672cc-108">Met de cmdlet **Get-DscConfiguration** wordt de huidige configuratie van de knoop punten opgehaald als de configuratie bestaat.</span><span class="sxs-lookup"><span data-stu-id="672cc-108">The **Get-DscConfiguration** cmdlet gets the current configuration of the nodes, if the configuration exists.</span></span>
<span data-ttu-id="672cc-109">Geef computers op met behulp van Common Information Model (CIM)-sessies.</span><span class="sxs-lookup"><span data-stu-id="672cc-109">Specify computers by using Common Information Model (CIM) sessions.</span></span>
<span data-ttu-id="672cc-110">Als u geen doel computer opgeeft, wordt de configuratie door de cmdlet opgehaald van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="672cc-110">If you do not specify a target computer, the cmdlet gets the configuration from the local computer.</span></span>

## <span data-ttu-id="672cc-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="672cc-111">EXAMPLES</span></span>

### <span data-ttu-id="672cc-112">Voor beeld 1: de configuratie voor de lokale computer ophalen</span><span class="sxs-lookup"><span data-stu-id="672cc-112">Example 1: Get the configuration for the local computer</span></span>

```
PS C:\> Get-DscConfiguration
```

<span data-ttu-id="672cc-113">Met deze opdracht wordt de huidige status voor de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="672cc-113">This command gets the current state for the local computer.</span></span>

### <span data-ttu-id="672cc-114">Voor beeld 2: de configuratie voor een opgegeven computer ophalen</span><span class="sxs-lookup"><span data-stu-id="672cc-114">Example 2: Get the configuration for a specified computer</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Get-DscConfiguration -CimSession $Session
```

<span data-ttu-id="672cc-115">In dit voor beeld wordt de huidige status opgehaald van een computer die is opgegeven door een CIM-sessie.</span><span class="sxs-lookup"><span data-stu-id="672cc-115">This example gets the current state from a computer specified by a CIM session.</span></span>
<span data-ttu-id="672cc-116">In het voor beeld wordt een CIM-sessie voor een computer met de naam Server01 gemaakt voor gebruik met de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="672cc-116">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="672cc-117">U kunt ook een matrix met CIM-sessies maken om de cmdlet op meerdere opgegeven computers toe te passen.</span><span class="sxs-lookup"><span data-stu-id="672cc-117">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="672cc-118">Met de eerste opdracht maakt u een CIM-sessie met behulp van de cmdlet **New-CimSession** en slaat u het **CimSession** -object op in de variabele **$Session** .</span><span class="sxs-lookup"><span data-stu-id="672cc-118">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the **$Session** variable.</span></span>
<span data-ttu-id="672cc-119">De opdracht vraagt u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="672cc-119">The command prompts you for a password.</span></span>
<span data-ttu-id="672cc-120">Typ `Get-Help New-CimSession` voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="672cc-120">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="672cc-121">Met de tweede opdracht wordt de huidige configuratie opgehaald voor de computers die worden geïdentificeerd door de **CimSession** -objecten die zijn opgeslagen in de variabele **$Session** , in dit geval de computer met de naam Server01.</span><span class="sxs-lookup"><span data-stu-id="672cc-121">The second command gets the current configuration for the computers identified by the **CimSession** objects stored in the **$Session** variable, in this case, the computer named Server01.</span></span>

## <span data-ttu-id="672cc-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="672cc-122">PARAMETERS</span></span>

### <span data-ttu-id="672cc-123">-AsJob</span><span class="sxs-lookup"><span data-stu-id="672cc-123">-AsJob</span></span>
<span data-ttu-id="672cc-124">Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="672cc-124">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="672cc-125">-CimSession</span><span class="sxs-lookup"><span data-stu-id="672cc-125">-CimSession</span></span>
<span data-ttu-id="672cc-126">Voert de cmdlet uit in een externe sessie of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="672cc-126">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="672cc-127">Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) of [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) .</span><span class="sxs-lookup"><span data-stu-id="672cc-127">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="672cc-128">De standaard waarde is de huidige sessie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="672cc-128">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="672cc-129">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="672cc-129">-ThrottleLimit</span></span>
<span data-ttu-id="672cc-130">Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="672cc-130">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="672cc-131">Als deze para meter wordt wegge laten of een waarde van `0` wordt ingevoerd, wordt in Windows Power shell een optimale bandbreedte limiet voor de cmdlet berekend op basis van het aantal CIM-cmdlets dat op de computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="672cc-131">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="672cc-132">De beperkings limiet geldt alleen voor de huidige cmdlet, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="672cc-132">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="672cc-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="672cc-133">CommonParameters</span></span>
<span data-ttu-id="672cc-134">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="672cc-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="672cc-135">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="672cc-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="672cc-136">INVOER</span><span class="sxs-lookup"><span data-stu-id="672cc-136">INPUTS</span></span>

## <span data-ttu-id="672cc-137">UITVOER</span><span class="sxs-lookup"><span data-stu-id="672cc-137">OUTPUTS</span></span>

## <span data-ttu-id="672cc-138">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="672cc-138">NOTES</span></span>

## <span data-ttu-id="672cc-139">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="672cc-139">RELATED LINKS</span></span>

[<span data-ttu-id="672cc-140">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="672cc-140">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="672cc-141">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="672cc-141">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="672cc-142">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="672cc-142">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="672cc-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="672cc-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="672cc-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="672cc-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
