---
title: De naam en samen vatting van de cmdlet toevoegen aan een Help-onderwerp voor cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353254"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>De cmdlet-naam en het cmdlet-overzicht toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u inhoud kunt toevoegen die wordt weer gegeven in de secties naam en samen VATTING van de Help van de cmdlet. In het Help-bestand wordt deze inhoud toegevoegd aan het opdracht knooppunt voor elke cmdlet.

> [!NOTE]
> Voor een volledig overzicht van een Help-bestand opent u een van de dll-Help. XML-bestanden die zich in de installatiemap van Windows Power shell bevinden. Het bestand micro soft. Power shell. commands. Management. dll-Help. XML bevat bijvoorbeeld inhoud voor verschillende Windows Power shell-cmdlets.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>De naam van de cmdlet en een samen vatting toevoegen

- De Help van de cmdlet kan twee beschrijvingen voor de cmdlet weer geven. De eerste beschrijving is een korte beschrijving die de samen vatting wordt genoemd. De tweede beschrijving is een gedetailleerde beschrijving die wordt beschreven in [de gedetailleerde beschrijving toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-a-cmdlet-description.md). Beide beschrijvingen moeten worden geschreven als één alinea.

- Herhaal de naam van de cmdlet niet in de samen vatting. Door de gebruiker te informeren dat de get-server-cmdlet een server krijgt, is kort, maar niet informatief. Gebruik in plaats daarvan synoniemen en Voeg details toe aan de beschrijving.

  Voor beeld: "haalt een object op dat een lokale of externe computer vertegenwoordigt."

- Gebruik eenvoudige werk woorden zoals ' Get ', ' maken ' en ' wijzigen ' in de samen vatting. Vermijd het gebruik van ' set ' omdat het Vague is en decoratieve woorden zoals ' Modify '.

  Voor beeld: "haalt informatie op over de Authenticode-hand tekening in een bestand."

- Schrijf in actieve Voice. Bijvoorbeeld ' het object time span gebruiken... ' is veel helderder dan het object time span kan worden gebruikt voor...

- Vermijd het woord ' weer geven ' bij het beschrijven van cmdlets die objecten ophalen. Hoewel er in Windows Power shell cmdlet-gegevens worden weer gegeven, is het belang rijk om gebruikers in te stellen voor het concept dat de cmdlet retourneert .NET Framework objecten waarvan de gegevens niet mogen worden weer gegeven. Als u de weer gave markeert, kan de gebruiker mogelijk niet realiseren dat de cmdlet veel andere nuttige eigenschappen en methoden heeft geretourneerd die niet worden weer gegeven.

## <a name="see-also"></a>Zie ook

 [Windows Power shell SDK](../windows-powershell-reference.md)