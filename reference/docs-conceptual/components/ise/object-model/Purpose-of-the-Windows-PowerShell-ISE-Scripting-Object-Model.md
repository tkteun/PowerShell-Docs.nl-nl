---
ms.date: 12/31/2019
keywords: Power shell, cmdlet
title: Doel van het scriptobjectmodel van Windows PowerShell ISE
ms.openlocfilehash: 1f48df112bd19297baa311116e79d3d7603d7c81
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736229"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Doel van het scriptobjectmodel van Windows PowerShell ISE

Objecten zijn gekoppeld aan de vorm en functie van Windows Power shell Integrated Scripting Environment (ISE). De verwijzing naar het object model bevat details over de lideigenschappen en methoden die deze objecten beschikbaar maken. Er worden voor beelden gegeven om te laten zien hoe u scripts kunt gebruiken om rechtstreeks toegang te krijgen tot deze methoden en eigenschappen. Het script object model maakt het volgende bereik van taken eenvoudiger.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>Het uiterlijk van Windows PowerShell ISE aanpassen

U kunt het object model gebruiken om de toepassings instellingen en-opties te wijzigen. U kunt deze bijvoorbeeld als volgt wijzigen:

- Wijzig de kleur van fouten, waarschuwingen, uitgebreide uitvoer en Debug-uitvoer.
- De achtergrond kleuren voor het opdracht venster, het deel venster uitvoer en het script paneel ophalen of instellen.
- Stel de voorgrond kleur in voor het deel venster uitvoer.
- Stel de lettertype naam en teken grootte in voor Windows PowerShell ISE.
- Waarschuwingen configureren. Deze instelling bevat waarschuwingen die worden gegeven wanneer een bestand wordt geopend in meerdere Power shell-tabbladen of wanneer een script in het bestand wordt uitgevoerd voordat het bestand is opgeslagen.
- Scha kelen tussen een weer gave waarin het Script venster en het deel venster uitvoer naast elkaar staan en een weer gave waarin het Script venster boven in het deel venster uitvoer staat.
- Het opdracht venster dokken aan de onderkant of boven in het deel venster uitvoer.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>De functionaliteit van Windows PowerShell ISE verbeteren

U kunt het object model gebruiken om de functionaliteit van Windows PowerShell ISE te verbeteren. U kunt bijvoorbeeld:

- Het exemplaar van Windows PowerShell ISE zichzelf toevoegen en wijzigen. Als u bijvoorbeeld de menu's wilt wijzigen, kunt u nieuwe menu opdrachten toevoegen en de nieuwe menu-items toewijzen aan scripts.
- Maak scripts waarmee u een aantal taken uitvoert die u kunt uitvoeren met behulp van de menu opdrachten en knoppen in Windows PowerShell ISE. U kunt bijvoorbeeld een Power shell-tabblad toevoegen, verwijderen of selecteren.
- Een aanvulling op taken die kunnen worden uitgevoerd met menu opdrachten en knoppen. U kunt bijvoorbeeld de naam van een Power shell-tabblad wijzigen.
- Bewerk tekst buffers voor het opdracht venster, het deel venster uitvoer en het script deel venster dat is gekoppeld aan een bestand. U kunt bijvoorbeeld:
  - Alle tekst ophalen of instellen.
  - Een tekst selectie ophalen of instellen.
  - Een script uitvoeren of een geselecteerd deel van een script uitvoeren.
  - Schuif een regel in de weer gave.
  - Tekst invoegen bij een caret-positie.
  - Selecteer een blok tekst.
  - Het laatste regel nummer ophalen.
- Voer Bestands bewerkingen uit. U kunt bijvoorbeeld:
  - Open een bestand, sla een bestand op of sla een bestand op met een andere naam.
  - Bepalen of een bestand is gewijzigd nadat het voor het laatst is opgeslagen.
  - De bestands naam ophalen.
  - Selecteer een bestand.

## <a name="automating-tasks"></a>Taken automatiseren

U kunt het script-object model gebruiken om sneltoetsen te maken voor frequente bewerkingen.

## <a name="see-also"></a>Zie ook

- [De ISE-object model hiërarchie](The-ISE-Object-Model-Hierarchy.md)
