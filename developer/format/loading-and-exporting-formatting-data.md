---
title: Het laden en opmaken van gegevens exporteren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 86a0e8b7e8967280daa57faf5c323efcd3b1368b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794192"
---
# <a name="loading-and-exporting-formatting-data"></a>Opmaakgegevens laden en exporteren

Nadat u uw opmaak-bestand hebt gemaakt, moet u de gegevens van de indeling van de sessie bijwerken door het laden van uw bestanden in de huidige sessie. (De opmaak bestanden geleverd door Windows PowerShell worden geladen door de modules die zijn geregistreerd wanneer de huidige sessie wordt geopend.) Zodra de gegevens van de indeling van de huidige sessie wordt bijgewerkt, Windows PowerShell maakt gebruik van die gegevens om de .NET-objecten die zijn gekoppeld aan de weergaven die zijn gedefinieerd in de geladen opmaak bestanden weer te geven. Er is geen limiet voor het aantal opmaak bestanden die u kunt in de huidige sessie laden. Naast het bijwerken van het opmaken van gegevens, kunt u de gegevens opmaken in de huidige sessie naar een opmaak bestand exporteren.

## <a name="loading-format-data"></a>Het laden van gegevens opmaken

Opmaak bestanden kunnen worden geladen in de huidige sessie met de volgende methoden:

- U kunt de opmaak bestand importeren in de huidige sessie vanaf de opdrachtregel. Gebruik de [Update FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet zoals beschreven in de volgende procedure.

- U kunt een modulemanifest dat verwijst naar het bestand met opmaak maken. Modules kunnen u verpakt u opmaak van bestanden voor distributie. Gebruik de [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet voor het maken van het manifest en de [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet voor het laden van de module in de huidige sessie. Zie voor meer informatie over modules [schrijven van een Windows PowerShell-Module](../module/writing-a-windows-powershell-module.md).

- U kunt een module die verwijst naar het bestand met opmaak. Gebruik de [System.Management.Automation.Pssnapin.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) om te verwijzen naar uw opmaak bestanden. Het wordt ten zeerste aangeraden modules voor pakket-cmdlets en de bijbehorende opmaak en typen bestanden gebruiken om te worden gedistribueerd. Zie voor meer informatie over modules [schrijven van een Windows PowerShell-Module](../module/writing-a-windows-powershell-module.md).

- Als u opdrachten via een programma aanroept, kunt u een vermelding in het opmaak toevoegen aan de eerste sessiestatus van de runspace waarin de opdrachten worden uitgevoerd. Zie voor meer informatie over .NET-type gebruikt voor het toevoegen van het bestand opmaak, de [System.Management.Automation.Runspaces.Sessionstateformatentry? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) klasse.

Wanneer een opmaak bestand wordt geladen, wordt deze aan een interne lijst toegevoegd dat Windows PowerShell gebruikt om te bepalen welke weergave moet worden gebruikt bij het weergeven van objecten op de opdrachtregel. U kunt uw opmaak bestand aan het begin van de lijst toevoegen, of kunt u deze toevoegen aan het einde van de lijst. Weten waar uw opmaak bestand wordt toegevoegd aan deze lijst is belangrijk als u het laden van opmaak-bestand dat een weergave voor een object dat een bestaande weergave gedefinieerd definieert heeft, zoals wanneer u wilt wijzigen hoe een object dat wordt geretourneerd door de cmdlet van een Windows PowerShell core is  weergegeven. Als u het laden van een opmaak-bestand dat de enige weergave voor een object wordt gedefinieerd, kunt u een van de methoden die eerder zijn beschreven.  Als u het laden van een opmaak-bestand dat een andere weergave voor een object wordt gedefinieerd, moet u de [Update FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet en voeg het bestand aan het begin van de lijst.

## <a name="storing-your-formatting-file"></a>Het opmaak-bestand opslaan

Er is geen vereiste voor waar uw opmaak bestanden worden opgeslagen op schijf. Het wordt echter sterk aangeraden u ze opslaat in de volgende map: `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>Het laden van een indelingsbestand met behulp van de Import-FormatData

1. Store uw opmaak bestand op schijf.

2. Voer de [Update FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet met behulp van een van de volgende opdrachten.

   Als u wilt toevoegen de notaties bestand aan het begin van de lijst met deze opdracht gebruiken. Gebruik deze opdracht als u wijzigen hoe een object wordt weergegeven.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   Als u wilt toevoegen de notaties bestand aan het einde van de lijst met deze opdracht gebruiken.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   Nadat u hebt toegevoegd een bestand met de [Update FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet, u niet het bestand verwijderen uit de lijst tijdens de sessie geopend is. U moet de sessie voor de opmaak bestand verwijderen uit de lijst sluiten.

## <a name="exporting-format-data"></a>Exporteren van gegevens opmaken

Voeg hier het hoofdgedeelte sectie.
