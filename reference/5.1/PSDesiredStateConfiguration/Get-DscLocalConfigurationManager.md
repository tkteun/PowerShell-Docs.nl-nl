---
external help file: Get-DSCLocalConfigurationManager.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscLocalConfigurationManager
ms.openlocfilehash: 162770d8eb3a8953dcfaeb31f30742a46353b33b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250770"
---
# <span data-ttu-id="0e3a0-103">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0e3a0-103">Get-DscLocalConfigurationManager</span></span>

## <span data-ttu-id="0e3a0-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="0e3a0-104">SYNOPSIS</span></span>

<span data-ttu-id="0e3a0-105">Hiermee worden de instellingen van lokale Configuration Manager (LCM) en statussen voor het knoop punt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-105">Gets Local Configuration Manager (LCM) settings and states for the node.</span></span>

## <span data-ttu-id="0e3a0-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="0e3a0-106">SYNTAX</span></span>

```
Get-DscLocalConfigurationManager [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [<CommonParameters>]
```

## <span data-ttu-id="0e3a0-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0e3a0-107">DESCRIPTION</span></span>

<span data-ttu-id="0e3a0-108">De `Get-DscLocalConfigurationManager` cmdlet krijgt instellingen voor de ICM, meta configuratie en de status van LCM voor het knoop punt.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-108">The `Get-DscLocalConfigurationManager` cmdlet gets LCM settings, or meta-configuration, and the states of LCM for the node.</span></span> <span data-ttu-id="0e3a0-109">Geef computers op met behulp van Common Information Model (CIM)-sessies.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-109">Specify computers by using Common Information Model (CIM) sessions.</span></span> <span data-ttu-id="0e3a0-110">Als u geen doel computer opgeeft, worden de configuratie-instellingen van de lokale computer opgehaald met de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-110">If you do not specify a target computer, the cmdlet gets the configuration settings from the local computer.</span></span>

## <span data-ttu-id="0e3a0-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="0e3a0-111">EXAMPLES</span></span>

### <span data-ttu-id="0e3a0-112">Voor beeld 1: de ICM-instellingen voor de lokale computer ophalen</span><span class="sxs-lookup"><span data-stu-id="0e3a0-112">Example 1: Get LCM settings for the local computer</span></span>

```powershell
Get-DscLocalConfigurationManager
```

```Output
ActionAfterReboot              : ContinueConfiguration
AgentId                        : 47edd8c9-2798-4827-839a-b35cc87e69fb
AllowModuleOverWrite           : False
CertificateID                  :
ConfigurationDownloadManagers  : {}
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 15
Credential                     :
DebugMode                      : {NONE}
DownloadManagerCustomData      :
DownloadManagerName            :
LCMCompatibleVersions          : {1.0, 2.0}
LCMState                       : Idle
LCMStateDetail                 :
LCMVersion                     : 2.0
StatusRetentionTimeInDays      : 10
SignatureValidationPolicy      : NONE
SignatureValidations           : {}
MaximumDownloadSizeMB          : 500
PartialConfigurations          :
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 30
RefreshMode                    : PUSH
ReportManagers                 : {}
ResourceModuleManagers         : {}
PSComputerName
```

<span data-ttu-id="0e3a0-113">Met deze opdracht worden de ICM-instellingen voor de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-113">This command gets LCM settings for the local computer.</span></span>

<span data-ttu-id="0e3a0-114">Zie de documentatie over [het configureren van de lokale Configuration Manager](../../docs-conceptual/dsc/managing-nodes/metaconfig.md#basic-settings) voor meer informatie over de afzonderlijke kenmerken van de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-114">For more information on the individual attributes of the output, see the [Configuring the Local Configuration Manager](../../docs-conceptual/dsc/managing-nodes/metaconfig.md#basic-settings) documentation.</span></span>

### <span data-ttu-id="0e3a0-115">Voor beeld 2: instellingen voor de ICM ophalen voor een opgegeven computer</span><span class="sxs-lookup"><span data-stu-id="0e3a0-115">Example 2: Get LCM settings for a specified computer</span></span>

```powershell
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Get-DscLocalConfigurationManager -CimSession $Session
```

```Output
ActionAfterReboot              : ContinueConfiguration
AgentId                        : 169dfa57-a7f9-43be-a7a5-9dd06587e052
AllowModuleOverWrite           : False
CertificateID                  :
ConfigurationDownloadManagers  : {}
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 15
Credential                     :
DebugMode                      : {NONE}
DownloadManagerCustomData      :
DownloadManagerName            :
LCMCompatibleVersions          : {1.0, 2.0}
LCMState                       : Idle
LCMStateDetail                 :
LCMVersion                     : 2.0
StatusRetentionTimeInDays      : 10
SignatureValidationPolicy      : NONE
SignatureValidations           : {}
MaximumDownloadSizeMB          : 500
PartialConfigurations          :
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 30
RefreshMode                    : PUSH
ReportManagers                 : {}
ResourceModuleManagers         : {}
PSComputerName                 : Server01
PSComputerName                 : Server01
```

<span data-ttu-id="0e3a0-116">In dit voor beeld worden de ICM-instellingen opgehaald voor een computer die is opgegeven door een CIM-sessie.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-116">This example gets LCM settings for a computer specified by a CIM session.</span></span>
<span data-ttu-id="0e3a0-117">In het voor beeld wordt een CIM-sessie voor een computer met de naam Server01 gemaakt voor gebruik met de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-117">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="0e3a0-118">U kunt ook een matrix met CIM-sessies maken om de cmdlet op meerdere opgegeven computers toe te passen.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-118">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="0e3a0-119">Met de eerste opdracht maakt u een CIM-sessie met behulp van de `New-CimSession` cmdlet. vervolgens slaat u het **CimSession** -object op in de variabele $Session.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-119">The first command creates a CIM session by using the `New-CimSession` cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span> <span data-ttu-id="0e3a0-120">De opdracht vraagt u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-120">The command prompts you for a password.</span></span> <span data-ttu-id="0e3a0-121">Typ `Get-Help New-CimSession` voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-121">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="0e3a0-122">Met de tweede opdracht worden lokale Configuration Manager-instellingen opgehaald voor de computers die worden geïdentificeerd door de **CimSession** -objecten die zijn opgeslagen in de $Session-variabele.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-122">The second command gets Local Configuration Manager settings for the computers identified by the **CimSession** objects stored in the $Session variable.</span></span> <span data-ttu-id="0e3a0-123">In dit geval de computer met de naam Server01.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-123">In this case, the computer named Server01.</span></span>

## <span data-ttu-id="0e3a0-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0e3a0-124">PARAMETERS</span></span>

### <span data-ttu-id="0e3a0-125">-AsJob</span><span class="sxs-lookup"><span data-stu-id="0e3a0-125">-AsJob</span></span>

<span data-ttu-id="0e3a0-126">Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-126">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="0e3a0-127">-CimSession</span><span class="sxs-lookup"><span data-stu-id="0e3a0-127">-CimSession</span></span>

<span data-ttu-id="0e3a0-128">Voert de cmdlet uit in een externe sessie of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-128">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="0e3a0-129">Voer een computer naam of een sessie object in, zoals de uitvoer van een- `New-CimSession` of- `Get-CimSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-129">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span>

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

### <span data-ttu-id="0e3a0-130">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="0e3a0-130">-ThrottleLimit</span></span>

<span data-ttu-id="0e3a0-131">Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-131">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>

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

### <span data-ttu-id="0e3a0-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0e3a0-132">CommonParameters</span></span>

<span data-ttu-id="0e3a0-133">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0e3a0-134">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0e3a0-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0e3a0-135">INVOER</span><span class="sxs-lookup"><span data-stu-id="0e3a0-135">INPUTS</span></span>

## <span data-ttu-id="0e3a0-136">UITVOER</span><span class="sxs-lookup"><span data-stu-id="0e3a0-136">OUTPUTS</span></span>

## <span data-ttu-id="0e3a0-137">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="0e3a0-137">NOTES</span></span>

## <span data-ttu-id="0e3a0-138">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="0e3a0-138">RELATED LINKS</span></span>

[<span data-ttu-id="0e3a0-139">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="0e3a0-139">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="0e3a0-140">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="0e3a0-140">Set-DscLocalConfigurationManager</span></span>](Set-DscLocalConfigurationManager.md)
