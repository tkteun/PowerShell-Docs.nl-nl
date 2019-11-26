---
ms.date: 07/09/2019
keywords: DSC, GPO, Power shell, configuratie, installatie
title: Quick Start-groepsbeleid converteren naar DSC
ms.openlocfilehash: 8c89dbbce5b2b146194b799d7e36ecce3105bfeb
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941605"
---
> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

# <a name="quickstart-convert-group-policy-into-dsc"></a>Snelstartgids groepsbeleid converteren naar DSC

U kunt een DSC-configuratie genereren vanuit een groepsbeleid of Azure Security Center basis lijn. De [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) -module bevat de volgende opdrachten voor het uitvoeren van deze taak.

- `ConvertFrom-GPO`: groeps beleid wordt geconverteerd, opgeslagen als bestanden. U kunt ook een map met meerdere beleids regels opgeven die worden gecombineerd in één configuratie.
  - Als u groeps beleid in uw omgeving wilt exporteren, gebruikt u de cmdlet [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) of volgt u de instructies in [een groeps beleidsobject exporteren naar een bestand](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).
- `ConvertFrom-SCM`-Hiermee worden de basis lijnen van Security Compliance Manager geconverteerd, opgeslagen als `.xml`-bestanden.
- `ConvertFrom-ASC`: converteert Azure Security Center basis lijnen die zijn opgeslagen als `.json`-bestanden.
- `Merge-GPOs`: groeps beleid dat wordt toegepast op een doel computer, wordt geconverteerd.

Met de cmdlets die hierboven worden weer gegeven, wordt een basis lijn geconverteerd naar een DSC `.mof`-bestand. U kunt er ook voor kiezen om een configuratie script (`.ps1`) uit te voeren dat u kunt bewerken en opnieuw compileren. De cmdlets detecteren compilatie fouten voor ontbrekende resources of dubbele resource blokken. Resource blokken waardoor er geen opmerkingen kunnen worden gevonden.

In het volgende voor beeld wordt een [micro soft-beveiligings basislijn](https://www.microsoft.com/en-us/download/details.aspx?id=55319) geconverteerd naar een DSC-configuratie script (`.ps1`) en `.mof`-bestand.

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

Na het uitvoeren van de opdrachten ziet u twee bestanden in de standaard directory "uitvoer" die is gemaakt onder uw huidige pad.

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

Elk beheerd knoop punt heeft ook de volgende twee modules nodig:

- [SecurityPolicyDSC](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [AuditPolicyDSC](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> **BaselineManagement** is een oplossing ontwikkeld door de community om DSC meer detecteerbaar te maken voor de ondersteuning van Community-oplossingen van het project Maintainers en niet van micro soft. U kunt een nieuw probleem openen voor **BaselineManagement** op [github](https://github.com/microsoft/BaselineManagement).

## <a name="next-steps"></a>Volgende stappen

- Zie [aan](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation)de slag om uw configuratie script te uploaden naar de configuratie van Azure Automation status.
- Voeg de **SecurityPolicyDSC** -en **AuditPolicyDSC** -modules toe aan uw [Automation-account](/azure/automation/shared-resources/modules).
- DSC-configuraties en-resources zoeken in de [PowerShell Gallery](https://www.powershellgallery.com/).