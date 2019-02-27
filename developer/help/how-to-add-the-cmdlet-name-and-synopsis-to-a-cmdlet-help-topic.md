---
title: De naam van Cmdlet en samenvatting toevoegen aan een Cmdlet Help-onderwerp | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850888"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>De cmdlet-naam en het cmdlet-overzicht toevoegen aan een Help-onderwerp voor cmdlets

Deze sectie wordt beschreven hoe u inhoud die wordt weergegeven in de secties naam en samenvatting van de help van de cmdlet toe te voegen. In het Help-bestand, wordt deze inhoud toegevoegd aan het knooppunt van de opdracht voor elke cmdlet.

> [!NOTE]
> Voor een volledige weergave van een Help-bestand, open een van de dll-Help.xml-bestanden zich in de installatiemap van Windows PowerShell. Bijvoorbeeld, worden de inhoud van het bestand Microsoft.PowerShell.Commands.Management.dll Help.xml bevat voor verschillende van de Windows PowerShell-cmdlets.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>De Cmdlet-naam en een samenvatting toe te voegen

- De cmdlet Help kan twee beschrijvingen voor de cmdlet worden weergegeven. De beschrijving van de eerste is een korte beschrijving die wordt aangeduid als de samenvatting. De beschrijving van de tweede is een gedetailleerde beschrijving die wordt besproken in [de gedetailleerde beschrijving toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-a-cmdlet-description.md). Beide deze beschrijvingen tekstberichten worden geschreven als een enkele alinea.

- Herhaal de cmdlet-naam niet in de samenvatting. Waarin de gebruiker die de cmdlet Get-Server krijgt u een server is korte, maar niet informatieve. In plaats daarvan gebruik van synoniemen en details toevoegen aan de beschrijving.

  Voorbeeld: "Haalt een object dat staat voor een lokale of externe computer."

- Gebruik eenvoudige woorden als 'ophalen', 'maken' en '' in de samenvatting wijzigen. Vermijd het gebruik van 'instellen' omdat het vaag zijn, en decoratieve woorden zoals 'wijzigen."

  Voorbeeld: "Hiermee haalt informatie over de Authenticode-handtekening in een bestand."

- In de actieve stem schrijven. Bijvoorbeeld, "gebruiken het object TimeSpan..." is veel beter dan 'de TimeSpan-object kan worden gebruikt om te...'

- Vermijd de term 'weergegeven' bij de beschrijving van cmdlets die objecten ophalen. Hoewel Windows PowerShell cmdlet gegevens worden weergegeven, is het belangrijk om te introduceren van gebruikers met het concept die de cmdlet retourneert .NET Framework-objecten waarvan de gegevens kunnen niet worden weergegeven. Als u de weergave benadrukken, kan de gebruiker niet realiseren dat de cmdlet mogelijk geretourneerd veel andere nuttige eigenschappen en methoden die niet worden weergegeven.

## <a name="see-also"></a>Zie ook

 [Windows PowerShell SDK](../windows-powershell-reference.md)