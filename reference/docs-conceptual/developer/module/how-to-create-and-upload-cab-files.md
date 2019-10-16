---
title: CAB-bestanden maken en uploaden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357552"
---
# <a name="how-to-create-and-upload-cab-files"></a>CAB-bestanden maken en uploaden

In dit onderwerp wordt uitgelegd hoe u te updaten CAB-bestanden kunt maken en deze kunt uploaden naar de locatie waar de bijwerk bare Help-cmdlets kunnen worden gevonden.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>Bewerk bare CAB-bestanden voor Help maken en uploaden

U kunt de Help-functie die kan worden bijgewerkt gebruiken om nieuwe of bijgewerkte Help-bestanden te leveren voor een module in meerdere talen en cult uren. Een Help-pakket dat kan worden bijgewerkt voor een module bestaat uit één HelpInfo XML-bestand en een of meer cabinetbestanden (. CAB-bestanden). Elk CAB-bestand bevat Help-bestanden voor de module in één UI-cultuur. Gebruik de volgende procedure om CAB-bestanden te maken voor Help bij te werken.

1. De Help-bestanden voor de module indelen door UI-cultuur. Elk CAB-bestand dat kan worden bijgewerkt bevat de Help-bestanden voor één module in één UI-cultuur. U kunt meerdere CAB-bestanden voor de Help leveren voor de module, elk voor een andere GEBRUIKERSINTERFACE cultuur.

2. Controleer of de Help-bestanden alleen de bestands typen bevatten die zijn toegestaan voor Help bij te werken en deze valideren op basis van een Help-bestands schema. Als de `Update-Help`-cmdlet een bestand tegen komt dat ongeldig is of niet het toegestane type heeft, wordt het ongeldige bestand niet geïnstalleerd en stopt het installeren van bestanden van het CAB. Voor een lijst met toegestane bestands typen raadpleegt u [Bestands typen die zijn toegestaan in een CAB-bestand](./file-types-permitted-in-an-updatable-help-cab-file.md)dat kan worden bijgewerkt.

3. De Help-bestanden digitaal ondertekenen. Digitale hand tekeningen zijn niet vereist, maar ze zijn een best practice.

4. Neem alle Help bestanden voor de module op in de UI-cultuur, niet alleen bestanden die nieuw zijn of gewijzigd zijn. Als het CAB-bestand onvolledig is, hebben gebruikers die de eerste keer Help-bestanden downloaden of niet elke update downloaden, niet alle Help-bestanden van de module.

5. Gebruik een hulp programma voor het maken van cabinetbestanden, zoals MakeCab. exe. Windows Power shell bevat geen cmdlets waarmee CAB-bestanden worden gemaakt.

6. Noem de CAB-bestanden. Zie [een CAB-bestand voor bijwerk bare Help-bestanden benoemen](./how-to-name-an-updatable-help-cab-file.md)voor meer informatie.

7. Upload de CAB-bestanden voor de module naar de locatie die is opgegeven door het element **HelpContentUri** in het XML-bestand HelpInfo voor de module. Upload vervolgens het HelpInfo XML-bestand naar de locatie die is opgegeven door de **HelpInfoUri** -sleutel van het module manifest. De **HelpContentUri** en **HelpInfoUri** kunnen naar dezelfde locatie verwijzen.

> [!CAUTION]
> De waarde van de **HelpInfoUri** -sleutel en het **HelpContentUri** -element moet beginnen met http of https. De waarde moet duiden op een Internet locatie en mag geen bestands naam bevatten.