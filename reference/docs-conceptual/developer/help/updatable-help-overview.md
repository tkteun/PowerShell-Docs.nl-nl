---
ms.date: 03/22/2012
ms.topic: reference
title: Overzicht van Help die kan worden bijgewerkt
description: Overzicht van Help die kan worden bijgewerkt
ms.openlocfilehash: b8008b7c28d94ebaac135934606042e6a6053591
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649563"
---
# <a name="updatable-help-overview"></a>Overzicht van Help die kan worden bijgewerkt

Dit document bevat een basis kennis van het ontwerp en de werking van de Help-functie die voor Power shell kan worden bijgewerkt. Het is ontworpen voor auteurs van modules en anderen die Windows Power shell Help-onderwerpen leveren aan gebruikers.

## <a name="introduction"></a>Introductie

Help-onderwerpen voor Power shell vormen een integraal onderdeel van de Power shell-ervaring. Net als Power shell-modules worden Help-onderwerpen voortdurend bijgewerkt en verbeterd door de auteurs en door de bijdragen van de community van Power shell-gebruikers.

De *bijwerk bare Help* -functie, geïntroduceerd in Windows power Shell 3,0, zorgt ervoor dat gebruikers over de nieuwste versies van Help-onderwerpen beschikken bij de opdracht prompt, zelfs voor ingebouwde Power shell-opdrachten, zonder nieuwe modules te downloaden of Windows Update uit te voeren. Met de bijwerk bare Help kunt u eenvoudig een update maken door cmdlets te bieden waarmee de nieuwste versies van Help-onderwerpen van Internet worden gedownload en geïnstalleerd in de juiste submappen op de lokale computer van de gebruiker. Zelfs gebruikers die zich achter een firewall bevinden, kunnen de nieuwe cmdlets gebruiken om bijgewerkte hulp te krijgen van een interne bestands share.

Help-informatie die kan worden bijgewerkt, wordt volledig ondersteund door alle Windows Power shell-modules in Windows 8 en Windows Server 2012, en de bijbehorende functies zijn beschikbaar voor alle auteurs van Windows Power shell-modules. Help-informatie die kan worden bijgewerkt, ondersteunt alleen op XML gebaseerde Help-bestanden. Het biedt geen ondersteuning voor Help op basis van opmerkingen.

Bij te werken Help omvat de volgende functies.

- De cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) , waarmee wordt bepaald of gebruikers over de nieuwste Help-bestanden voor een module beschikken en, als dat niet het geval is, downloadt de nieuwste Help-bestanden van Internet, pakt ze uit en installeert ze in de juiste module submappen op de computer van de gebruiker. Gebruikers kunnen de cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) gebruiken om onmiddellijk de zojuist geïnstalleerde Help-onderwerpen weer te geven. Het is niet nodig om Power shell opnieuw te starten.

- De cmdlet [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) , waarmee de nieuwste Help-bestanden van Internet worden gedownload en opgeslagen in een map van het bestands systeem. Gebruikers kunnen de `Update-Help` cmdlet gebruiken om Help-bestanden op te halen uit de map van het bestands systeem en deze uit te pakken en te installeren in de module submappen op de computer van de gebruiker. De `Save-Help` cmdlet is bedoeld voor gebruikers met beperkte of geen Internet toegang en voor ondernemingen die de toegang tot internet liever beperken.

- **Help voor een module**. Help-bestanden voor een module worden beheerd en geleverd als eenheid, zodat gebruikers alle Help-bestanden kunnen ophalen voor de modules die ze gebruiken. Help-informatie die kan worden bijgewerkt, wordt alleen ondersteund voor modules, niet voor Windows Power shell-modules.

- **Versie ondersteuning**. Bij te werken Help wordt standaard vier Position (N1. N2. N3. N4) versie nummers.
  Bij te werken Help worden Help-bestanden gedownload wanneer het versie nummer van de Help-bestanden op de computer van de gebruiker (of in de `Save-Help` map) lager is dan het versie nummer van de Help-bestanden op de Internet locatie.

- **Ondersteuning voor meerdere talen**. Bij te werken Help ondersteunt de Help-bestanden van de module in meerdere GEBRUIKERSINTERFACE culturen.
  Bij te werken Help-bestands namen zijn de standaard taal codes, zoals ' en-US ' en ' ja-JP ', en de `Update-Help` `Save-Help` cmdlets en de Help-bestanden worden in taalspecifieke submappen van de module directory geplaatst.

- **Automatisch gegenereerde Help**. Met de cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) wordt de basis Help weer gegeven voor opdrachten die geen Help-bestanden hebben. De automatisch gegenereerde Help omvat de opdracht syntaxis en aliassen, en instructies voor het gebruik van online-Help en Help bij te werken.

- **Uitgebreide online-Help**. Voor eenvoudige toegang tot online-Help is geen Help-bestanden meer nodig. De para meter **online** van de `Get-Help` cmdlet haalt nu de URL van een online Help-onderwerp op uit de waarde van de eigenschap **HelpUri** van elke opdracht, als de URL van de online Help niet kan worden gevonden in een Help-bestand. U kunt de eigenschap **HelpUri** invullen door een **HelpUri** -kenmerk toe te voegen aan de code van cmdlets, functions en CIM-opdrachten of door gebruik te maken van de **.** Een Help-instructie op basis van opmerkingen in werk stromen en scripts.

  Om ervoor te zorgen dat de Help-bestanden kunnen worden bijgewerkt, worden de Windows Power shell-modules in Windows 8 en Windows Server vNext niet geleverd met Help-bestanden. Gebruikers kunnen de Help-informatie die kan worden bijgewerkt, gebruiken om Help-bestanden te installeren en ze bij te werken. Auteurs van andere modules kunnen Help-bestanden in modules bevatten of deze weglaten. Ondersteuning voor bijwerk bare Help is optioneel, maar wordt aanbevolen.
