---
ms.date: 09/13/2016
ms.topic: reference
title: CAB-bestanden maken en uploaden
description: CAB-bestanden maken en uploaden
ms.openlocfilehash: bdcf534f48cff27b403d82440ad4ec6a3212b67d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653891"
---
# <a name="how-to-create-and-upload-cab-files"></a>CAB-bestanden maken en uploaden

In dit onderwerp wordt uitgelegd hoe u te updaten CAB-bestanden kunt maken en deze kunt uploaden naar de locatie waar de bijwerk bare Help-cmdlets kunnen worden gevonden.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>Bewerk bare CAB-bestanden voor Help maken en uploaden

U kunt de Help-functie die kan worden bijgewerkt gebruiken om nieuwe of bijgewerkte Help-bestanden te leveren voor een module in meerdere talen en cult uren. Een Help-pakket dat kan worden bijgewerkt voor een module bestaat uit één HelpInfo XML-bestand en een of meer Cabinet ( `.CAB` )-bestanden. Elk CAB-bestand bevat Help-bestanden voor de module in één UI-cultuur. Gebruik de volgende procedure om CAB-bestanden te maken voor Help bij te werken.

1. De Help-bestanden voor de module indelen door UI-cultuur. Elk CAB-bestand dat kan worden bijgewerkt bevat de Help-bestanden voor één module in één UI-cultuur. U kunt meerdere CAB-bestanden voor de Help leveren voor de module, elk voor een andere GEBRUIKERSINTERFACE cultuur.

1. Controleer of de Help-bestanden alleen de bestands typen bevatten die zijn toegestaan voor Help bij te werken en deze valideren op basis van een Help-bestands schema. Als `Update-Help` met de cmdlet een bestand wordt aangetroffen dat ongeldig is of niet het toegestane type heeft, wordt het ongeldige bestand niet geïnstalleerd en wordt het installeren van bestanden van het cab gestopt. Voor een lijst met toegestane bestands typen raadpleegt u [Bestands typen die zijn toegestaan in een CAB-bestand](./file-types-permitted-in-an-updatable-help-cab-file.md)dat kan worden bijgewerkt.

1. De Help-bestanden digitaal ondertekenen. Digitale hand tekeningen zijn niet vereist, maar ze zijn een best practice.

1. Neem alle Help bestanden voor de module op in de UI-cultuur, niet alleen bestanden die nieuw zijn of gewijzigd zijn. Als het CAB-bestand onvolledig is, hebben gebruikers die de eerste keer Help-bestanden downloaden of niet elke update downloaden, niet alle Help-bestanden van de module.

1. Gebruik een hulp programma voor het maken van cabinetbestanden, zoals `MakeCab.exe` . Power shell bevat geen cmdlets waarmee CAB-bestanden worden gemaakt.

1. Noem de CAB-bestanden. Zie [een CAB-bestand voor bijwerk bare Help-bestanden benoemen](./how-to-name-an-updatable-help-cab-file.md)voor meer informatie.

1. Upload de CAB-bestanden voor de module naar de locatie die is opgegeven door het element **HelpContentUri** in het XML-bestand HelpInfo voor de module. Upload vervolgens het HelpInfo XML-bestand naar de locatie die is opgegeven door de **HelpInfoUri** -sleutel van het module manifest. De **HelpContentUri** en **HelpInfoUri** kunnen naar dezelfde locatie verwijzen.

> [!CAUTION]
> De waarde van de sleutel **HelpInfoUri** en het element **HelpContentUri** moet beginnen met `http` of `https` . De waarde moet duiden op een Internet locatie en mag geen bestands naam bevatten.
