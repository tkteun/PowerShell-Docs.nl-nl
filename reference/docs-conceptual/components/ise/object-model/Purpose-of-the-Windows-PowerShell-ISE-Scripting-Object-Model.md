---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Doel van het scriptobjectmodel van Windows PowerShell ISE
ms.openlocfilehash: e59593ef06911c709e92fa7a1eabd96d2636ca30
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030908"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Doel van het scriptobjectmodel van Windows PowerShell ISE

Objecten zijn gekoppeld aan het formulier en de functie van Windows PowerShell Integrated Scripting Environment (ISE). De naslaginformatie over objectmodel bevat informatie over het lid van de eigenschappen en methoden die deze objecten beschikbaar maken. Voorbeelden zijn bedoeld om weer te geven hoe u scripts kunt gebruiken voor rechtstreekse toegang tot deze eigenschappen en methoden. Het Scriptobjectmodel vergemakkelijkt het volgende bereik van taken.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>Aanpassen van het uiterlijk van Windows PowerShell ISE

Het objectmodel kunt u de toepassings- en opties wijzigen. Bijvoorbeeld, kunt u ze als volgt:

- U kunt de kleur van fouten, waarschuwingen, uitgebreide uitvoer wijzigen en foutopsporing weergeeft.
- U kunt ophalen of instellen van de achtergrondkleuren voor het opdrachtvenster, het deelvenster Uitvoer en het scriptvenster.
- U kunt de voorgrondkleur van het deelvenster Uitvoer instellen.
- U kunt het lettertype en de tekengrootte instellen voor Windows PowerShell ISE.
- U kunt waarschuwingen configureren. Deze instelling bevat waarschuwingen die zijn uitgegeven wanneer een bestand wordt geopend in meerdere tabbladen met PowerShell of wanneer een script in het bestand wordt uitgevoerd voordat het bestand is opgeslagen.
- U kunt schakelen tussen een weergave waarbij het scriptvenster en het deelvenster Uitvoer side-by-side zijn en een weergave waarbij het scriptvenster is boven op het deelvenster Uitvoer. U kunt het deelvenster opdracht verankeren aan de onderkant of aan de bovenkant van het deelvenster Uitvoer.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>Verbetering van de functionaliteit van Windows PowerShell ISE

U kunt het objectmodel gebruiken voor het verbeteren van de functionaliteit van Windows PowerShell ISE. U kunt bijvoorbeeld het volgende doen:

- Toevoegen en wijzigen van het exemplaar van Windows PowerShell ISE zelf. Bijvoorbeeld, als u wilt wijzigen van de menu's, kunt u nieuwe menu-items toevoegen en het nieuwe menu-items worden toegewezen aan de scripts.
- Scripts maken die enkele van de taken die u uitvoeren kunt met behulp van de opdrachten in het menu en knoppen in Windows PowerShell ISE uitvoeren. Bijvoorbeeld, u kunt toevoegen, verwijderen of Selecteer een PowerShell-tabblad.
- Aanvullende taken die kunnen worden uitgevoerd met behulp van opdrachten in het menu en knoppen. U kunt bijvoorbeeld een PowerShell-tabblad wijzigen.
- Tekst buffers voor het opdrachtvenster, het deelvenster Uitvoer en het scriptvenster die gekoppeld aan een bestand zijn te manipuleren. U kunt bijvoorbeeld het volgende doen:
  - Ophalen of instellen van alle tekst.
  - Ophalen of instellen van een selectie van tekst.
  - Uitvoeren van een script of een geselecteerd gedeelte van een script uitvoeren.
  - Een regel in beeld schuiven.
  - Tekst invoegen op de positie van een caret-teken.
  - Selecteer een blok tekst.
  - De laatste regel getal ophalen.
- Bestandsbewerkingen uitvoeren. U kunt bijvoorbeeld het volgende doen:
  - Openen van een bestand, een bestand opslaat of een bestand opslaan met behulp van een andere naam.
  - Bepalen of een bestand is gewijzigd nadat het laatst is opgeslagen.
  - Naam van het bestand ophalen.
  - Selecteer een bestand.

## <a name="automating-tasks"></a>Het automatiseren van taken

U kunt het Scriptobjectmodel sneltoetsen voor frequente activiteiten maken.

## <a name="see-also"></a>Zie ook

- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)
