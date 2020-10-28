---
ms.date: 09/13/2016
ms.topic: reference
title: Opmaakgegevens laden en exporteren
description: Opmaakgegevens laden en exporteren
ms.openlocfilehash: 38857526801051bf6d31d300d5be1a3fd2c80391
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666515"
---
# <a name="loading-and-exporting-formatting-data"></a>Opmaakgegevens laden en exporteren

Nadat u het opmaak bestand hebt gemaakt, moet u de indelings gegevens van de sessie bijwerken door uw bestanden in de huidige sessie te laden. (De indelings bestanden die worden meegeleverd met Windows Power shell worden geladen door modules die zijn geregistreerd bij het openen van de huidige sessie.) Zodra de indelings gegevens van de huidige sessie worden bijgewerkt, gebruikt Windows Power shell die gegevens om de .NET-objecten weer te geven die zijn gekoppeld aan de weer gaven die zijn gedefinieerd in de geladen opmaak bestanden. Er is geen limiet voor het aantal indelings bestanden dat u in de huidige sessie kunt laden. Naast het bijwerken van de opmaak gegevens, kunt u de indelings gegevens in de huidige sessie weer exporteren naar een opmaak bestand.

## <a name="loading-format-data"></a>Indelings gegevens laden

Indelings bestanden kunnen worden geladen in de huidige sessie met de volgende methoden:

- U kunt het opmaak bestand importeren in de huidige sessie vanaf de opdracht regel. Gebruik de cmdlet [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) zoals beschreven in de volgende procedure.

- U kunt een module manifest maken dat verwijst naar uw indelings bestand. Met modules kunt u het format teren van bestanden voor distributie verpakken. Gebruik de cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) om het manifest te maken en de cmdlet [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) om de module in de huidige sessie te laden. Zie [een Windows Power shell-module schrijven](../module/writing-a-windows-powershell-module.md)voor meer informatie over modules.

- U kunt een module maken die verwijst naar uw indelings bestand. Gebruik [System. Management. Automation. PSSnapIn. formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) om naar uw indelings bestanden te verwijzen. Het wordt ten zeerste aanbevolen modules te gebruiken voor het inpakken van cmdlets en eventuele bijbehorende indelings-en type bestanden voor distributie. Zie [een Windows Power shell-module schrijven](../module/writing-a-windows-powershell-module.md)voor meer informatie over modules.

- Als u opdrachten via een programma aanroept, kunt u een vermelding in het indelings bestand toevoegen aan de oorspronkelijke sessie status van de runs Pace waar de opdrachten worden uitgevoerd. Voor meer informatie over .NET-type dat wordt gebruikt om het opmaak bestand toe te voegen, Zie [System. Management. Automation. Runspaces. Sessionstateformatentry? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) -klasse.

Wanneer een opmaak bestand wordt geladen, wordt het toegevoegd aan een interne lijst die door Windows Power shell wordt gebruikt om te bepalen welke weer gave moet worden gebruikt bij het weer geven van objecten op de opdracht regel. U kunt het opmaak bestand laten voorafgaan door aan het begin van de lijst of u kunt het toevoegen aan het einde van de lijst. Als u weet waar uw opmaak bestand wordt toegevoegd aan deze lijst is belang rijk als u een opmaak bestand laadt dat een weer gave definieert voor een object waarvoor een bestaande weer gave is gedefinieerd, zoals wanneer u wilt wijzigen hoe een object dat wordt geretourneerd door een Windows Power shell core-cmdlet wordt weer gegeven. Als u een opmaak bestand laadt dat de enige weer gave voor een object definieert, kunt u een van de eerder beschreven methoden gebruiken.  Als u een opmaak bestand laadt dat een andere weer gave voor een object definieert, moet u de cmdlet [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) gebruiken en uw bestand laten voorafgaan door aan het begin van de lijst.

## <a name="storing-your-formatting-file"></a>Uw indelings bestand opslaan

Er is geen vereiste voor het opslaan van uw indelings bestanden op schijf. Het wordt echter aangeraden om deze op te slaan in de volgende map: `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>Een indelings bestand laden met behulp van Import-FormatData

1. Sla het opmaak bestand op schijf op.

2. Voer de cmdlet [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) uit met een van de volgende opdrachten.

   Gebruik deze opdracht om uw opmaak bestand toe te voegen aan het begin van de lijst. Gebruik deze opdracht als u de weer gave van een object wilt wijzigen.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   Gebruik deze opdracht om uw opmaak bestand toe te voegen aan het einde van de lijst.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   Wanneer u een bestand hebt toegevoegd met de cmdlet [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) , kunt u het bestand niet verwijderen uit de lijst wanneer de sessie is geopend. U moet de sessie sluiten om het opmaak bestand te verwijderen uit de lijst.

## <a name="exporting-format-data"></a>Indelings gegevens exporteren

Voeg hier het hoofdgedeelte van de sectie in.
