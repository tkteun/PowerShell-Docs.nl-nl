---
title: Over het maken en uploaden CAB-bestanden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082376"
---
# <a name="how-to-create-and-upload-cab-files"></a>CAB-bestanden maken en uploaden

In dit onderwerp wordt uitgelegd hoe u bij te werken Help CAB-bestanden maken en ze uploaden naar de locatie waar de cmdlets bij te werken Help ze kunnen vinden.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>Over het maken en uploaden van bij te werken Help CAB-bestanden

U kunt de bij te werken Help-functie gebruiken om nieuwe of bijgewerkte helpbestanden voor een module in meerdere talen en culturen te leveren. Een pakket bij te werken Help voor een module bestaat uit één HelpInfo XML-bestand en een of meer CAB-bestand (. CAB-bestanden). Elk CAB-bestand bevat help-bestanden voor de module in één gebruikersinterfacecultuur. Gebruik de volgende procedure om te maken van CAB-bestanden voor bijwerkbare Help.

1. De help-bestanden voor de module door gebruikersinterfacecultuur indelen. Elke bij te werken Help CAB-bestand bevat de help-bestanden voor een module in één gebruikersinterfacecultuur. U kunt meerdere help CAB-bestanden voor de module, elk voor een andere gebruikersinterfacecultuur leveren.

2. Controleer of dat help-bestanden bevatten alleen de bestandstypen toegestaan voor bij te werken Help en te valideren op basis van een help-bestand-schema. Als de `Update-Help` cmdlet wordt een bestand dat is ongeldig of is geen toegestane type aangetroffen, de ongeldig bestand kan niet worden geïnstalleerd en stopt met het installeren van bestanden uit het CAB-bestand. Zie voor een lijst van toegestane bestandstypen, [bestand typen die zijn toegestaan in een bij te werken Help CAB-bestand](./file-types-permitted-in-an-updatable-help-cab-file.md).

3. De help-bestanden digitaal te ondertekenen. Digitale handtekeningen zijn niet vereist, maar ze zijn een best practice.

4. Alle van de help-bestanden voor de module in de gebruikersinterface van de cultuur, niet alleen de bestanden die zijn nieuw of zijn gewijzigd bevatten. Als het cabinetbestand onvolledig is, help-bestanden downloaden voor de eerste keer of elke update niet downloaden gebruikers geen alle van de module help-bestanden.

5. Gebruik een hulpprogramma waarmee u cab-bestanden, zoals MakeCab.exe maakt. Windows PowerShell bevat geen cmdlets die CAB-bestanden maken.

6. Naam van de CAB-bestanden. Zie voor meer informatie, [naamconventies voor een bij te werken Help CAB-bestand](./how-to-name-an-updatable-help-cab-file.md).

7. De CAB-bestanden voor de module uploaden naar de locatie die is opgegeven door de **HelpContentUri** -element in het HelpInfo XML-bestand voor de module. Vervolgens de HelpInfo XML-bestand uploaden naar de locatie die is opgegeven door de **HelpInfoUri** sleutel van de module-manifest. De **HelpContentUri** en **HelpInfoUri** kunnen verwijzen naar dezelfde locatie.

> [!CAUTION]
> De waarde van de **HelpInfoUri** sleutel en de **HelpContentUri** element moet beginnen met 'http' of 'https'. De waarde moet een Internet-locatie geven en mogen geen een bestandsnaam op.