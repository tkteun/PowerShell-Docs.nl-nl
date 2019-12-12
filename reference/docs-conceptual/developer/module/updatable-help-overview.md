---
title: Overzicht van bijwerk bare Help | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: 3f7388a9-9fa8-42bc-b294-538c9a01e30a
caps.latest.revision: 12
ms.openlocfilehash: f2dfb9642ba2dde38124142b659b425bbbb00f37
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357293"
---
# <a name="updatable-help-overview"></a>Overzicht van Help die kan worden bijgewerkt

Dit document bevat een basis kennis van het ontwerp en de werking van de Windows Power shell-functie die kan worden bijgewerkt. Het is ontworpen voor auteurs van modules en anderen die Windows Power shell Help-onderwerpen leveren aan gebruikers.

## <a name="introduction"></a>Inleiding

Windows Power shell Help-onderwerpen vormen een integraal onderdeel van de Windows Power shell-ervaring. Net als Windows Power shell-modules worden Help-onderwerpen voortdurend bijgewerkt en verbeterd door de auteurs en door de bijdragen van de community van Windows Power shell-gebruikers.

De *bijwerk bare Help* -functie, geïntroduceerd in Windows power Shell 3,0, zorgt ervoor dat gebruikers over de nieuwste versies van Help-onderwerpen beschikken bij de opdracht prompt, zelfs voor ingebouwde Windows Power shell-opdrachten, zonder nieuwe modules te downloaden of Windows Update uit te voeren. Met de bijwerk bare Help kunt u eenvoudig een update maken door cmdlets te bieden waarmee de nieuwste versies van Help-onderwerpen van Internet worden gedownload en geïnstalleerd in de juiste submappen op de lokale computer van de gebruiker. Zelfs gebruikers die zich achter een firewall bevinden, kunnen de nieuwe cmdlets gebruiken om bijgewerkte hulp te krijgen van een interne bestands share.

Help-informatie die kan worden bijgewerkt, wordt volledig ondersteund door alle Windows Power shell-modules in Windows® 8 en Windows Server® 2012, en de bijbehorende functies zijn beschikbaar voor alle auteurs van Windows Power shell-modules. Help-informatie die kan worden bijgewerkt, ondersteunt alleen op XML gebaseerde Help-bestanden. Het biedt geen ondersteuning voor Help op basis van opmerkingen.

Bij te werken Help omvat de volgende functies.

- De cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) , waarmee wordt bepaald of gebruikers over de nieuwste Help-bestanden voor een module beschikken en, als dat niet het geval is, downloadt de nieuwste Help-bestanden van Internet, pakt ze uit en installeert ze in de juiste module submappen op de computer van de gebruiker.
  Gebruikers kunnen de cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) gebruiken om onmiddellijk de zojuist geïnstalleerde Help-onderwerpen weer te geven.
  Het is niet nodig om Power shell opnieuw te starten.

- De cmdlet [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) , waarmee de nieuwste Help-bestanden van Internet worden gedownload en opgeslagen in een map van het bestands systeem. Gebruikers kunnen de cmdlet `Update-Help` gebruiken om Help-bestanden op te halen uit de map van het bestands systeem en deze uit te pakken en te installeren in de module submappen op de computer van de gebruiker. De cmdlet `Save-Help` is bedoeld voor gebruikers met beperkte of geen Internet toegang en voor ondernemingen die de toegang tot internet liever beperken.

- **Help voor een module**. Help-bestanden voor een module worden beheerd en geleverd als eenheid, zodat gebruikers alle Help-bestanden kunnen ophalen voor de modules die ze gebruiken. Help-informatie die kan worden bijgewerkt, wordt alleen ondersteund voor modules, niet voor Windows Power shell-modules.

- **Versie ondersteuning**. Bij te werken Help wordt standaard vier Position (N1. N2. N3. N4) versie nummers. Bij te werken Help worden Help-bestanden gedownload wanneer het versie nummer van de Help-bestanden op de computer van de gebruiker (of in de `Save-Help` Directory) lager is dan het versie nummer van de Help-bestanden op de Internet locatie.

- **Ondersteuning voor meerdere talen**. Bij te werken Help ondersteunt de Help-bestanden van de module in meerdere GEBRUIKERSINTERFACE culturen. Bij te werken namen van Help-bestanden zijn standaard taal codes, zoals ' en-US ' en ' ja-JP ', en de cmdlets `Update-Help` en `Save-Help` plaatsen de Help-bestanden in taalspecifieke submappen van de module directory.

- **Automatisch gegenereerde Help**. Met de cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) wordt de basis Help weer gegeven voor opdrachten die geen Help-bestanden hebben. De automatisch gegenereerde Help omvat de opdracht syntaxis en aliassen, en instructies voor het gebruik van online-Help en Help bij te werken.

- **Uitgebreide online-Help**. Voor eenvoudige toegang tot online-Help is geen Help-bestanden meer nodig. De para meter **online** van de cmdlet `Get-Help` haalt nu de URL van een online Help-onderwerp op uit de waarde van de eigenschap **HelpUri** van een wille keurige opdracht, als de URL van de online Help niet kan worden gevonden in een Help-bestand. U kunt de eigenschap **HelpUri** invullen door een **HelpUri** -kenmerk toe te voegen aan de code van cmdlets, functions en CIM-opdrachten of door gebruik te maken van de **.** Een Help-instructie op basis van opmerkingen in werk stromen en scripts.

  Om ervoor te zorgen dat de Help-bestanden kunnen worden bijgewerkt, worden de Windows Power shell-modules in Windows 8 en Windows Server vNext niet geleverd met Help-bestanden. Gebruikers kunnen de Help-informatie die kan worden bijgewerkt, gebruiken om Help-bestanden te installeren en ze bij te werken. Auteurs van andere modules kunnen Help-bestanden in modules bevatten of deze weglaten. Ondersteuning voor bijwerk bare Help is optioneel, maar wordt aanbevolen.
