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
> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="quickstart-convert-group-policy-into-dsc"></a>Snelstartgids: Groepsbeleid converteren naar DSC

U kunt een DSC-configuratie genereren op basis van een basislijn voor Groepsbeleid of Azure Security Center. De [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) -module bevat de volgende opdrachten voor het uitvoeren van deze taak.

- `ConvertFrom-GPO` -Zet groep beleid, opgeslagen als bestanden. U kunt ook een map met meerdere beleidsregels die zal worden gecombineerd in één configuratie opgeven.
  - Als u wilt exporteren groepsbeleidsregels in uw omgeving, gebruikt u de [back-up groepsbeleidsobject](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) -cmdlet of volg de instructies in [een GPO exporteren naar een bestand](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).
- `ConvertFrom-SCM` -Security Compliance Manager basislijnen, opgeslagen als converteert `.xml` bestanden.
- `ConvertFrom-ASC` -Zet Azure Security Center basislijnen, opgeslagen als `.json` bestanden.
- `Merge-GPOs` -Zet groep beleid toegepast op een doelcomputer.

De bovenstaande cmdlets een basislijn converteren naar een DSC `.mof` bestand. U kunt er ook voor kiezen om uit te voeren van een configuratiescript (`.ps1`), die u kunt bewerken en opnieuw te compileren. De cmdlets detecteren compilatiefouten voor ontbrekende resources of dubbele resource-blokken. Resource-blokken die kan leiden compilatiefouten dat ertoe zijn opgenomen als opmerkingen.

Het volgende voorbeeld wordt geconverteerd naar een [Microsoft basisbeveiliging](https://www.microsoft.com/en-us/download/details.aspx?id=55319) in een DSC-configuratiescript (`.ps1`) en `.mof` bestand.

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

Na het uitvoeren van de opdrachten, ziet u twee bestanden in de map met de standaard 'Uitvoer' gemaakt op basis van het huidige pad.

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

Elke beheerde knooppunt moet ook de volgende twee modules:

- [SecurityPolicyDSC](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [AuditPolicyDSC](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> **BaselineManagement** is een oplossing ontwikkeld door de community om DSC sneller wordt ontdekt voor ondersteuning voor community-oplossingen afkomstig uit het project instaan en niet van Microsoft zijn. U kunt een nieuw probleem voor openen **BaselineManagement** op [GitHub](https://github.com/microsoft/BaselineManagement).

## <a name="next-steps"></a>Volgende stappen

- Als u wilt uw configuratiescript uploaden naar Azure Automation State Configuration, Zie [aan de slag](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).
- Voeg de **SecurityPolicyDSC** en **AuditPolicyDSC** modules naar uw [Automation-Account](/azure/automation/shared-resources/modules).
- DSC-configuraties en resources in de [PowerShell Gallery](https://www.powershellgallery.com/).
