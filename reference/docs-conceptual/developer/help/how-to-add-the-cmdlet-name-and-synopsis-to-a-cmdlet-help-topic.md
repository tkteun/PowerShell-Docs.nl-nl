---
title: De cmdlet-naam en het cmdlet-overzicht toevoegen aan een Help-onderwerp voor cmdlets
ms.date: 09/13/2016
ms.openlocfilehash: 399defcb596ff9e9a596f4cd25ebcb6bcb7c34d2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892877"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>De cmdlet-naam en het cmdlet-overzicht toevoegen aan een Help-onderwerp voor cmdlets

In deze sectie wordt beschreven hoe u inhoud kunt toevoegen die wordt weer gegeven in de secties **naam** en samen **vatting** van de Help van de cmdlet. In het Help-bestand wordt deze inhoud toegevoegd aan het opdracht knooppunt voor elke cmdlet.

> [!NOTE]
> Als u een volledig overzicht van een Help-bestand wilt weer geven, opent u een van de `dll-Help.xml` bestanden die zich in de installatie directory van Power shell bevinden. Het `Microsoft.PowerShell.Commands.Management.dll-Help.xml` bestand bevat bijvoorbeeld inhoud voor verschillende Power shell-cmdlets.

## <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>De naam van de cmdlet en een samen vatting toevoegen

- De Help van de cmdlet kan twee beschrijvingen voor de cmdlet weer geven. De eerste beschrijving is een korte beschrijving die de samen vatting wordt genoemd. De tweede beschrijving is een gedetailleerde beschrijving die wordt beschreven in [de gedetailleerde beschrijving toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-a-cmdlet-description.md).
  Beide beschrijvingen moeten worden geschreven als één alinea.

- Herhaal de naam van de cmdlet niet in de samen vatting. De gebruiker te informeren dat de `Get-Server` cmdlet een server krijgt, is kort, maar niet informatie. Gebruik in plaats daarvan synoniemen en Voeg details toe aan de beschrijving.

  Voor beeld: "haalt een object op dat een lokale of externe computer vertegenwoordigt."

- Gebruik eenvoudige werk woorden zoals ' Get ', ' maken ' en ' wijzigen ' in de samen vatting. Vermijd het gebruik van ' set ' omdat het Vague is en decoratieve woorden zoals ' Modify '.

  Voor beeld: "haalt informatie op over de Authenticode-hand tekening in een bestand."

- Schrijf in actieve Voice. Bijvoorbeeld ' het object time span gebruiken... ' is veel helderder dan het object time span kan worden gebruikt voor...

- Vermijd het woord ' weer geven ' bij het beschrijven van cmdlets die objecten ophalen. Hoewel er in Windows Power shell cmdlet-gegevens worden weer gegeven, is het belang rijk om gebruikers in te stellen voor het concept dat de cmdlet retourneert .NET Framework objecten waarvan de gegevens niet mogen worden weer gegeven. Als u de weer gave markeert, kan de gebruiker mogelijk niet realiseren dat de cmdlet veel andere nuttige eigenschappen en methoden heeft geretourneerd die niet worden weer gegeven.

## <a name="see-also"></a>Zie ook

[Windows PowerShell SDK](../windows-powershell-reference.md)
