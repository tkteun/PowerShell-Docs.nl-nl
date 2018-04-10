---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Voorbereiden voor het gebruik van Windows PowerShell
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
ms.openlocfilehash: 5e095984286ff89958dc0a4e3d27e40eae5b2c5e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="getting-ready-to-use-windows-powershell"></a>Voorbereiden voor het gebruik van Windows PowerShell
Overweeg de volgende opties voor setup bij het Windows PowerShell is geïnstalleerd en gestart. U kunt deze taken uitvoeren op elk gewenst moment.

- **Help-bestanden te installeren.** De cmdlets die zijn opgenomen in Windows PowerShell 3.0 niet afkomstig zijn met help-bestanden. U kunt echter de [Update-Help](/powershell/module/microsoft.powershell.core/update-help) cmdlet downloaden en installeren van de nieuwste help-bestanden op uw computer. Wanneer de bestanden worden geïnstalleerd, kunt u de [Get-Help](/powershell/module/microsoft.powershell.core/get-help) cmdlet weer te geven rechts op de opdrachtregel. Zie voor meer informatie [about_Updatable_Help](/powershell/module/microsoft.powershell.core/about/about_updatable_help).

    Als u besluit om niet te installeren van de help-bestanden, kunt u nog steeds de help-onderwerpen online lezen. De online versie van een cmdlet help-onderwerp, typt: `Get-Help <CmdletName> -Online`. De Windows PowerShell help-onderwerpen Zie bladeren de [PowerShell documentatie](/powershell/scripting).

- **Scripts uitvoeren.** Windows PowerShell om veilig te houden, het standaarduitvoeringsbeleid op Windows PowerShell is **beperkte**. Dit beleid kunt u cmdlets, maar geen scripts worden uitgevoerd. Voor het uitvoeren van scripts, gebruiken de [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) cmdlet om te wijzigen van het uitvoeringsbeleid voor **alles ondertekend** of **RemoteSigned**. Alleen leden van de groep Administrators op de computer, kunnen deze cmdlet uitvoeren. Zie voor meer informatie [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

- **Externe toegang inschakelen.** Het systeem is al geconfigureerd voor u externe opdrachten uitvoeren op andere computers. Het systeem is op Windows Server 2012 R2 en Windows Server 2012, ook geconfigureerd dat externe opdrachten ontvangen, om toe te staan van andere computers om externe opdrachten op de lokale computer. Als u computers met andere versies van Windows om externe opdrachten te ontvangen, voert u de [Enable-PSRemoting](/powershell/module/microsoft.powershell.core/enable-psremoting) cmdlet uit op de computer die u extern wilt beheren. Alleen leden van de groep Administrators op de computer, kunnen deze cmdlet uitvoeren. Zie voor meer informatie [about_Remote](/powershell/module/microsoft.powershell.core/about/about_remote).

    Opmerking: Als u externe toegang is ingeschakeld op een computer met Windows PowerShell 2.0, externe communicatie is nog steeds ingeschakeld na de installatie van Windows Management Framework 3.0. Echter, op Windows Server 2008 (niet Windows Server 2008 R2), moet u opnieuw inschakelen voor externe toegang na de installatie van Windows Management Framework 3.0.

## <a name="see-also"></a>Zie ook
- [Windows PowerShell installeren](../setup/Installing-Windows-PowerShell.md)
- [Windows PowerShell starten](/powershell/scripting/setup/starting-windows-powershell)