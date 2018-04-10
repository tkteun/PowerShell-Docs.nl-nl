---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Doel van het scriptobjectmodel van Windows PowerShell ISE
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: fd5ac2c34b173d4eba7636bb5760b1ac9abb4277
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Doel van het scriptobjectmodel van Windows PowerShell ISE

Objecten zijn gekoppeld aan het formulier en de functie van Windows PowerShell Integrated Scripting Environment (ISE). De objectverwijzing model biedt informatie over het lid eigenschappen en methoden die deze objecten beschikbaar. Voorbeelden zijn bedoeld om te zien hoe u scripts rechtstreeks toegang krijgen tot deze eigenschappen en methoden kunt gebruiken. Het uitvoeren van scripts objectmodel vergemakkelijkt het volgende bereik van taken.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>De vormgeving van Windows PowerShell ISE aanpassen

Het objectmodel kunt u de, toepassingsinstellingen en opties wijzigen. Bijvoorbeeld, kunt u deze aanpassen als volgt:

- U kunt de kleur van fouten, waarschuwingen, uitgebreide uitvoer wijzigen en foutopsporing levert.
- U kunt ophalen of instellen van de achtergrondkleuren voor het opdrachtvenster, het deelvenster Uitvoer en het scriptvenster.
- U kunt instellen dat de voorgrondkleur van het deelvenster Uitvoer.
- U kunt de naam van het lettertype en de tekengrootte instellen voor Windows PowerShell ISE.
- U kunt waarschuwingen configureren. Deze instelling bevat waarschuwingen die zijn uitgegeven wanneer een bestand wordt geopend in meerdere tabbladen met PowerShell of als een script in het bestand wordt uitgevoerd voordat het bestand is opgeslagen.
- U kunt schakelen tussen een weergave waarop het scriptvenster en het deelvenster Uitvoer side-by-side zijn en een weergave waarin het scriptvenster is boven op het deelvenster Uitvoer. U kunt het opdrachtvenster verankeren aan de onderkant of aan de bovenkant van het deelvenster Uitvoer.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>Verbetering van de functionaliteit van Windows PowerShell ISE

U kunt het objectmodel gebruiken voor het verbeteren van de functionaliteit van Windows PowerShell ISE. U kunt bijvoorbeeld het volgende doen:

- Toevoegen en wijzigen van het exemplaar van Windows PowerShell ISE zelf. Bijvoorbeeld, om te wijzigen van de menu's, kunt u nieuwe menu-items toevoegen en de nieuwe menu-items worden toegewezen aan de scripts.
- Scripts maken die de taken die u uitvoeren kunt met behulp van de knoppen en menuopdrachten in Windows PowerShell ISE uitvoeren. Bijvoorbeeld, u kunt toevoegen, verwijderen of Selecteer een PowerShell-tabblad.
- Aanvullende taken die kunnen worden uitgevoerd met behulp van menuopdrachten en knoppen. U kunt bijvoorbeeld een PowerShell-tabblad wijzigen.
- Tekst buffers voor het opdrachtvenster, het deelvenster Uitvoer en het scriptvenster die gekoppeld aan een bestand zijn bewerken. U kunt bijvoorbeeld het volgende doen:
  - Ophalen of instellen van alle tekst.
  - Ophalen of instellen van een tekstselectie.
  - Uitvoeren van een script of een geselecteerde deel van een script uitvoeren.
  - Een regel in beeld schuiven.
  - Tekst op een invoegpositie invoegen.
  - Selecteer een blok van tekst.
  - Het regelnummer van de laatste ophalen.
- Bestandsbewerkingen uitvoeren. U kunt bijvoorbeeld het volgende doen:
  - Openen van een bestand, een bestand opslaan of een bestand opslaan met behulp van een andere naam.
  - Bepalen of een bestand is gewijzigd nadat het laatst is opgeslagen.
  - De bestandsnaam niet ophalen.
  - Selecteer een bestand.

## <a name="automating-tasks"></a>Taken automatiseren

U kunt het uitvoeren van scripts objectmodel sneltoetsen voor regelmatige bewerkingen maken.

## <a name="see-also"></a>Zie ook

- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)