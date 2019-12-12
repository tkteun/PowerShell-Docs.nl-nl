---
ms.date: 07/09/2019
keywords: DSC, GPO, Power shell, configuratie, installatie
title: Quick Start-groepsbeleid converteren naar DSC
ms.openlocfilehash: 8c89dbbce5b2b146194b799d7e36ecce3105bfeb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941605"
---
> <span data-ttu-id="2476f-103">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="2476f-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart-convert-group-policy-into-dsc"></a><span data-ttu-id="2476f-104">Snelstartgids: groepsbeleid converteren naar DSC</span><span class="sxs-lookup"><span data-stu-id="2476f-104">Quickstart: Convert Group Policy into DSC</span></span>

<span data-ttu-id="2476f-105">U kunt een DSC-configuratie genereren vanuit een groepsbeleid of Azure Security Center basis lijn.</span><span class="sxs-lookup"><span data-stu-id="2476f-105">You can generate a DSC configuration from a Group Policy or Azure Security Center baseline.</span></span> <span data-ttu-id="2476f-106">De [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) -module bevat de volgende opdrachten voor het uitvoeren van deze taak.</span><span class="sxs-lookup"><span data-stu-id="2476f-106">The [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) module includes the following commands for accomplishing this task.</span></span>

- <span data-ttu-id="2476f-107">`ConvertFrom-GPO`: groeps beleid wordt geconverteerd, opgeslagen als bestanden.</span><span class="sxs-lookup"><span data-stu-id="2476f-107">`ConvertFrom-GPO` - Converts Group Policies, stored as files.</span></span> <span data-ttu-id="2476f-108">U kunt ook een map met meerdere beleids regels opgeven die worden gecombineerd in één configuratie.</span><span class="sxs-lookup"><span data-stu-id="2476f-108">You can also specify a directory containing multiple policies that will be combined into one Configuration.</span></span>
  - <span data-ttu-id="2476f-109">Als u groeps beleid in uw omgeving wilt exporteren, gebruikt u de cmdlet [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) of volgt u de instructies in [een groeps beleidsobject exporteren naar een bestand](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span><span class="sxs-lookup"><span data-stu-id="2476f-109">To export Group Policies in your environment, use the [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet, or follow the instructions in [Export a GPO to a File](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span></span>
- <span data-ttu-id="2476f-110">`ConvertFrom-SCM`-basis lijnen van Security Compliance Manager worden geconverteerd, opgeslagen als `.xml` bestanden.</span><span class="sxs-lookup"><span data-stu-id="2476f-110">`ConvertFrom-SCM` - Converts Security Compliance Manager baselines, stored as `.xml` files.</span></span>
- <span data-ttu-id="2476f-111">`ConvertFrom-ASC`-Azure Security Center basis lijnen worden geconverteerd, opgeslagen als `.json` bestanden.</span><span class="sxs-lookup"><span data-stu-id="2476f-111">`ConvertFrom-ASC` - Converts Azure Security Center baselines, stored as `.json` files.</span></span>
- <span data-ttu-id="2476f-112">`Merge-GPOs`-groeps beleid dat wordt toegepast op een doel computer, wordt geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="2476f-112">`Merge-GPOs` - Converts Group Policies applied to a target computer.</span></span>

<span data-ttu-id="2476f-113">Met de cmdlets die hierboven worden weer gegeven, wordt een basis lijn geconverteerd naar een DSC `.mof`-bestand.</span><span class="sxs-lookup"><span data-stu-id="2476f-113">The cmdlets listed above convert a baseline into a DSC `.mof` file.</span></span> <span data-ttu-id="2476f-114">U kunt er ook voor kiezen om een configuratie script (`.ps1`) uit te voeren dat u kunt bewerken en opnieuw compileren.</span><span class="sxs-lookup"><span data-stu-id="2476f-114">You can also choose to output a Configuration script (`.ps1`), that you can edit and recompile.</span></span> <span data-ttu-id="2476f-115">De cmdlets detecteren compilatie fouten voor ontbrekende resources of dubbele resource blokken.</span><span class="sxs-lookup"><span data-stu-id="2476f-115">The cmdlets detect compilation errors for missing resources, or duplicate resource blocks.</span></span> <span data-ttu-id="2476f-116">Resource blokken waardoor er geen opmerkingen kunnen worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="2476f-116">Resource blocks that would cause compilation errors are commented out.</span></span>

<span data-ttu-id="2476f-117">In het volgende voor beeld wordt een [micro soft-beveiligings basislijn](https://www.microsoft.com/en-us/download/details.aspx?id=55319) geconverteerd naar een DSC-configuratie script (`.ps1`) en `.mof` bestand.</span><span class="sxs-lookup"><span data-stu-id="2476f-117">The following example converts a [Microsoft Security Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) into a DSC configuration script (`.ps1`) and `.mof` file.</span></span>

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

<span data-ttu-id="2476f-118">Na het uitvoeren van de opdrachten ziet u twee bestanden in de standaard directory "uitvoer" die is gemaakt onder uw huidige pad.</span><span class="sxs-lookup"><span data-stu-id="2476f-118">After running the commands, you see two files in the default "Output" directory created under your current path.</span></span>

```powershell
Get-ChildItem -Path .\Output
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----         7/9/2019   9:35 AM   227.37KB DSCFromGPO.ps1
-a----         7/9/2019   9:35 AM   410.03KB localhost.mof
```

<span data-ttu-id="2476f-119">Elk beheerd knoop punt heeft ook de volgende twee modules nodig:</span><span class="sxs-lookup"><span data-stu-id="2476f-119">Each managed node will also need the following two modules:</span></span>

- [<span data-ttu-id="2476f-120">SecurityPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="2476f-120">SecurityPolicyDSC</span></span>](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [<span data-ttu-id="2476f-121">AuditPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="2476f-121">AuditPolicyDSC</span></span>](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> <span data-ttu-id="2476f-122">**BaselineManagement** is een oplossing ontwikkeld door de community om DSC meer detecteerbaar te maken voor de ondersteuning van Community-oplossingen van het project Maintainers en niet van micro soft.</span><span class="sxs-lookup"><span data-stu-id="2476f-122">**BaselineManagement** is a solution developed by the community to make DSC more discoverable for Support for community solutions come from the project maintainers and not from Microsoft.</span></span> <span data-ttu-id="2476f-123">U kunt een nieuw probleem openen voor **BaselineManagement** op [github](https://github.com/microsoft/BaselineManagement).</span><span class="sxs-lookup"><span data-stu-id="2476f-123">You can open a new issue for **BaselineManagement** on [GitHub](https://github.com/microsoft/BaselineManagement).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2476f-124">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="2476f-124">Next steps</span></span>

- <span data-ttu-id="2476f-125">Zie [aan](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation)de slag om uw configuratie script te uploaden naar de configuratie van Azure Automation status.</span><span class="sxs-lookup"><span data-stu-id="2476f-125">To upload your configuration script into Azure Automation State Configuration, see [Getting Started](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span></span>
- <span data-ttu-id="2476f-126">Voeg de **SecurityPolicyDSC** -en **AuditPolicyDSC** -modules toe aan uw [Automation-account](/azure/automation/shared-resources/modules).</span><span class="sxs-lookup"><span data-stu-id="2476f-126">Add the **SecurityPolicyDSC** and **AuditPolicyDSC** modules to your [Automation Account](/azure/automation/shared-resources/modules).</span></span>
- <span data-ttu-id="2476f-127">DSC-configuraties en-resources zoeken in de [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="2476f-127">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
