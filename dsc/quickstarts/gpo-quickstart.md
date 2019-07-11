---
ms.date: 07/09/2019
keywords: DSC, groepsbeleidsobject, powershell, configuratie, instellingen
title: Snelstartgids - Groepsbeleid converteren naar DSC
ms.openlocfilehash: 8c89dbbce5b2b146194b799d7e36ecce3105bfeb
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67785136"
---
> <span data-ttu-id="80f6a-103">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="80f6a-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart-convert-group-policy-into-dsc"></a><span data-ttu-id="80f6a-104">Snelstartgids: Groepsbeleid converteren naar DSC</span><span class="sxs-lookup"><span data-stu-id="80f6a-104">Quickstart: Convert Group Policy into DSC</span></span>

<span data-ttu-id="80f6a-105">U kunt een DSC-configuratie genereren op basis van een basislijn voor Groepsbeleid of Azure Security Center.</span><span class="sxs-lookup"><span data-stu-id="80f6a-105">You can generate a DSC configuration from a Group Policy or Azure Security Center baseline.</span></span> <span data-ttu-id="80f6a-106">De [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) -module bevat de volgende opdrachten voor het uitvoeren van deze taak.</span><span class="sxs-lookup"><span data-stu-id="80f6a-106">The [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) module includes the following commands for accomplishing this task.</span></span>

- <span data-ttu-id="80f6a-107">`ConvertFrom-GPO` -Zet groep beleid, opgeslagen als bestanden.</span><span class="sxs-lookup"><span data-stu-id="80f6a-107">`ConvertFrom-GPO` - Converts Group Policies, stored as files.</span></span> <span data-ttu-id="80f6a-108">U kunt ook een map met meerdere beleidsregels die zal worden gecombineerd in één configuratie opgeven.</span><span class="sxs-lookup"><span data-stu-id="80f6a-108">You can also specify a directory containing multiple policies that will be combined into one Configuration.</span></span>
  - <span data-ttu-id="80f6a-109">Als u wilt exporteren groepsbeleidsregels in uw omgeving, gebruikt u de [back-up groepsbeleidsobject](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) -cmdlet of volg de instructies in [een GPO exporteren naar een bestand](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span><span class="sxs-lookup"><span data-stu-id="80f6a-109">To export Group Policies in your environment, use the [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet, or follow the instructions in [Export a GPO to a File](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span></span>
- <span data-ttu-id="80f6a-110">`ConvertFrom-SCM` -Security Compliance Manager basislijnen, opgeslagen als converteert `.xml` bestanden.</span><span class="sxs-lookup"><span data-stu-id="80f6a-110">`ConvertFrom-SCM` - Converts Security Compliance Manager baselines, stored as `.xml` files.</span></span>
- <span data-ttu-id="80f6a-111">`ConvertFrom-ASC` -Zet Azure Security Center basislijnen, opgeslagen als `.json` bestanden.</span><span class="sxs-lookup"><span data-stu-id="80f6a-111">`ConvertFrom-ASC` - Converts Azure Security Center baselines, stored as `.json` files.</span></span>
- <span data-ttu-id="80f6a-112">`Merge-GPOs` -Zet groep beleid toegepast op een doelcomputer.</span><span class="sxs-lookup"><span data-stu-id="80f6a-112">`Merge-GPOs` - Converts Group Policies applied to a target computer.</span></span>

<span data-ttu-id="80f6a-113">De bovenstaande cmdlets een basislijn converteren naar een DSC `.mof` bestand.</span><span class="sxs-lookup"><span data-stu-id="80f6a-113">The cmdlets listed above convert a baseline into a DSC `.mof` file.</span></span> <span data-ttu-id="80f6a-114">U kunt er ook voor kiezen om uit te voeren van een configuratiescript (`.ps1`), die u kunt bewerken en opnieuw te compileren.</span><span class="sxs-lookup"><span data-stu-id="80f6a-114">You can also choose to output a Configuration script (`.ps1`), that you can edit and recompile.</span></span> <span data-ttu-id="80f6a-115">De cmdlets detecteren compilatiefouten voor ontbrekende resources of dubbele resource-blokken.</span><span class="sxs-lookup"><span data-stu-id="80f6a-115">The cmdlets detect compilation errors for missing resources, or duplicate resource blocks.</span></span> <span data-ttu-id="80f6a-116">Resource-blokken die kan leiden compilatiefouten dat ertoe zijn opgenomen als opmerkingen.</span><span class="sxs-lookup"><span data-stu-id="80f6a-116">Resource blocks that would cause compilation errors are commented out.</span></span>

<span data-ttu-id="80f6a-117">Het volgende voorbeeld wordt geconverteerd naar een [Microsoft basisbeveiliging](https://www.microsoft.com/en-us/download/details.aspx?id=55319) in een DSC-configuratiescript (`.ps1`) en `.mof` bestand.</span><span class="sxs-lookup"><span data-stu-id="80f6a-117">The following example converts a [Microsoft Security Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) into a DSC configuration script (`.ps1`) and `.mof` file.</span></span>

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

<span data-ttu-id="80f6a-118">Na het uitvoeren van de opdrachten, ziet u twee bestanden in de map met de standaard 'Uitvoer' gemaakt op basis van het huidige pad.</span><span class="sxs-lookup"><span data-stu-id="80f6a-118">After running the commands, you see two files in the default "Output" directory created under your current path.</span></span>

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

<span data-ttu-id="80f6a-119">Elke beheerde knooppunt moet ook de volgende twee modules:</span><span class="sxs-lookup"><span data-stu-id="80f6a-119">Each managed node will also need the following two modules:</span></span>

- [<span data-ttu-id="80f6a-120">SecurityPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="80f6a-120">SecurityPolicyDSC</span></span>](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [<span data-ttu-id="80f6a-121">AuditPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="80f6a-121">AuditPolicyDSC</span></span>](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> <span data-ttu-id="80f6a-122">**BaselineManagement** is een oplossing ontwikkeld door de community om DSC sneller wordt ontdekt voor ondersteuning voor community-oplossingen afkomstig uit het project instaan en niet van Microsoft zijn.</span><span class="sxs-lookup"><span data-stu-id="80f6a-122">**BaselineManagement** is a solution developed by the community to make DSC more discoverable for Support for community solutions come from the project maintainers and not from Microsoft.</span></span> <span data-ttu-id="80f6a-123">U kunt een nieuw probleem voor openen **BaselineManagement** op [GitHub](https://github.com/microsoft/BaselineManagement).</span><span class="sxs-lookup"><span data-stu-id="80f6a-123">You can open a new issue for **BaselineManagement** on [GitHub](https://github.com/microsoft/BaselineManagement).</span></span>

## <a name="next-steps"></a><span data-ttu-id="80f6a-124">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="80f6a-124">Next steps</span></span>

- <span data-ttu-id="80f6a-125">Als u wilt uw configuratiescript uploaden naar Azure Automation State Configuration, Zie [aan de slag](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span><span class="sxs-lookup"><span data-stu-id="80f6a-125">To upload your configuration script into Azure Automation State Configuration, see [Getting Started](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span></span>
- <span data-ttu-id="80f6a-126">Voeg de **SecurityPolicyDSC** en **AuditPolicyDSC** modules naar uw [Automation-Account](/azure/automation/shared-resources/modules).</span><span class="sxs-lookup"><span data-stu-id="80f6a-126">Add the **SecurityPolicyDSC** and **AuditPolicyDSC** modules to your [Automation Account](/azure/automation/shared-resources/modules).</span></span>
- <span data-ttu-id="80f6a-127">DSC-configuraties en resources in de [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="80f6a-127">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
