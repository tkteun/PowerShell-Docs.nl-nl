---
title: Overzicht van de bij te werken Help | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082088"
---
# <a name="updatable-help-overview"></a>Overzicht van Help die kan worden bijgewerkt

Dit document bevat een algemene inleiding tot het ontwerp en de werking van de Windows PowerShell bij te werken Help-functie. Het is ontworpen voor auteurs en anderen die ervoor zorgen dat gebruikers een Windows PowerShell help-onderwerpen.

## <a name="introduction"></a>Inleiding

Windows PowerShell help-onderwerpen zijn een integraal onderdeel van de Windows PowerShell-ervaring. Help-onderwerpen zijn, zoals Windows PowerShell-modules, voortdurend bijgewerkt en verbeterd door de auteur en de bijdragen van de community van gebruikers van Windows PowerShell.

De *bij te werken Help* functie, geïntroduceerd in Windows PowerShell 3.0, zorgt ervoor dat gebruikers de nieuwste versies van help-onderwerpen bij de opdrachtprompt, zelfs voor de ingebouwde Windows PowerShell-opdrachten, hebben zonder te downloaden van nieuwe modules of Windows Update wordt uitgevoerd. Bij te werken Help vereenvoudigt bijwerken door op te geven van cmdlets die de nieuwste versies van help-onderwerpen vanaf het Internet downloaden en te installeren in de juiste submappen op de lokale computer van de gebruiker. Zelfs als de gebruikers die zich achter een firewall kunnen de nieuwe-cmdlets gebruiken om de bijgewerkte hulp van een interne bestandsshare.

Bij te werken Help wordt volledig ondersteund door alle Windows PowerShell-modules in Windows® 8 en Windows Server® 2012 en de functies zijn beschikbaar voor alle schrijvers van Windows PowerShell-module. Bij te werken Help ondersteunt alleen help op basis van een XML-bestanden. Help op basis van een opmerking worden niet ondersteund.

Bij te werken Help bevat de volgende functies.

- De [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet, waarmee wordt bepaald of gebruikers beschikken over de nieuwste helpbestanden voor een module-bestanden en, als dit niet het geval is, downloadt de nieuwste helpbestanden van het Internet, ze uitgepakt en installeert u ze in de submappen van de juiste module op de de computer van de gebruiker.
  Gebruikers kunnen gebruiken de [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet om de zojuist geïnstalleerde help-onderwerpen onmiddellijk weer te geven.
  Ze hoeft niet opnieuw starten van PowerShell.

- De [Help opslaan](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet, de nieuwste help downloadt-bestanden op het Internet en slaat ze op in een bestand system-map. Gebruikers kunnen gebruiken de `Update-Help` cmdlet help-bestanden van de map van het systeem, verkrijgen en uitpakken en installeert u deze in de submappen van de module op de computer van de gebruiker. De `Save-Help` cmdlet is ontworpen voor gebruikers met beperkte of geen toegang tot Internet en voor bedrijven die wil toegang tot Internet beperken.

- **Help voor een Module**. Help-bestanden voor een module worden beheerd en die worden geleverd als een eenheid, zodat gebruikers toegang krijgen alle van de help-bestanden voor de modules die ze gebruiken. Bij te werken Help-informatie wordt alleen ondersteund voor modules, niet voor Windows PowerShell-modules.

- **Ondersteuning voor versie**. Bij te werken Help gebruikt standaard vier-positie (N1. N2. N3. Versienummers N4). Help bij te werken help-bestanden worden gedownload wanneer het versienummer van de help-op de computer van de gebruiker bestanden (of in de `Save-Help` directory) is lager dan het versienummer van de help-bestanden op de locatie van het Internet.

- **Ondersteuning voor meerdere talen**. Bij te werken Help biedt ondersteuning voor module help-bestanden in meerdere UI culturen. Bij te werken Help bestandsnamen bevatten standaard taalcodes, zoals "en-US" en 'ja-JP', en de `Update-Help` en `Save-Help` cmdlets de help-bestanden in submappen van de modulemap taalspecifieke plaatsen.

- **Automatisch gegenereerde help**. De [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet geeft basic help voor opdrachten waarvoor geen help-bestanden. De automatisch gegenereerde help bevat de opdrachtsyntaxis van de en aliassen en instructies voor het gebruik van online-help en bij te werken Help.

- **Online-help verbeterde**. Eenvoudige toegang tot de online-help is niet langer vereist voor help-bestanden. De **Online** parameter van de `Get-Help` cmdlet nu krijgt u de URL van een online help-onderwerp van de waarde van de **HelpUri** eigenschap van een opdracht, als deze niet de online help-URL in een help-bestand vinden. U kunt vullen de **HelpUri** eigenschap door toe te voegen een **HelpUri** kenmerk in de code van de cmdlets, functies en CIM-opdrachten of met behulp van de **. Koppeling** op basis van een opmerking help-richtlijn in werkstromen en scripts.

  Als u onze help-bestanden worden bijgewerkt, worden de Windows PowerShell-modules in Windows 8 en Windows Server vNext niet geleverd met help-bestanden. Gebruikers kunnen gebruiken bij te werken Help om help-bestanden installeren en deze bijwerken. Auteurs van andere modules kunnen help-bestanden opnemen in modules of deze weglaten. Ondersteuning voor bijwerkbare Help is optioneel, maar wordt aanbevolen.
