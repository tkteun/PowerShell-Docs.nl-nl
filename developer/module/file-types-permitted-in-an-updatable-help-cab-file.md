---
title: Bestandstypen die zijn toegestaan in een bij te werken Help CAB-bestand | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 931383858c0b83f0a9a66026c215e16481b89e9e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851595"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Bestandstypen die zijn toegestaan in een CAB-bestand voor een Help die kan worden bijgewerkt

In dit onderwerp geeft een lijst van en beschrijft de vereisten voor bijwerkbare Help CAB-bestanden.

## <a name="updatable-help-cab-file-requirements"></a>Vereisten voor bijwerkbare Help CAB-bestand

Niet-gecomprimeerde inhoud van de CAB-bestand is standaard beperkt tot 1 GB. Als u wilt deze beperking omzeilen, gebruikers moeten gebruiken de **Force** parameter van de [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en [Help opslaan](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.
Niet-gecomprimeerde inhoud van de CAB-bestand is standaard beperkt tot 1 GB. Als u wilt deze beperking omzeilen, gebruikers moeten gebruiken de **Force** parameter van de [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en [Help opslaan](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.

Om ervoor te zorgen de beveiliging van help-bestanden die worden gedownload vanaf het Internet, kan een bij te werken Help CAB-bestand bevatten alleen de hieronder vermelde bestandstypen. De [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet valideert alle bestanden op basis van de help-onderwerp schema's. Als de `Update-Help` cmdlet wordt een bestand dat is ongeldig of is geen toegestane type aangetroffen, de ongeldig bestand kan niet worden geïnstalleerd en stopt met het installeren van bestanden uit het CAB-bestand op de computer van de gebruiker.
Om ervoor te zorgen de beveiliging van help-bestanden die worden gedownload vanaf het Internet, kan een bij te werken Help CAB-bestand bevatten alleen de hieronder vermelde bestandstypen. De [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet valideert alle bestanden op basis van de help-onderwerp schema's. Als de `Update-Help` cmdlet wordt een bestand dat is ongeldig of is geen toegestane type aangetroffen, de ongeldig bestand kan niet worden geïnstalleerd en stopt met het installeren van bestanden uit het CAB-bestand op de computer van de gebruiker.

- XML-indeling help-onderwerpen over cmdlets.

- XML-indeling help-onderwerpen voor scripts en functies.

- XML-indeling help-onderwerpen voor Windows PowerShell-providers.

- Op basis van tekst help-onderwerpen, zoals over onderwerpen.

De [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) controleert of de inhoud van het CAB-bestand wanneer dit het CAB-bestand hebt uitgepakt. Als `Update-Help` vindt niet-compatibele bestandstypen in een bij te werken Help CAB-bestand, wordt een afsluitende fout gegenereerd en stopt de bewerking. Wordt een help-bestanden van het CAB-bestand, zelfs als die van compatibele bestandstypen niet geïnstalleerd.
De [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) controleert of de inhoud van het CAB-bestand wanneer dit het CAB-bestand hebt uitgepakt. Als `Update-Help` vindt niet-compatibele bestandstypen in een bij te werken Help CAB-bestand, wordt een afsluitende fout gegenereerd en stopt de bewerking. Wordt een help-bestanden van het CAB-bestand, zelfs als die van compatibele bestandstypen niet geïnstalleerd.