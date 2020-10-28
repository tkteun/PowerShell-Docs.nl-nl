---
ms.date: 03/22/2012
ms.topic: reference
title: Bestandstypen die zijn toegestaan in een CAB-bestand voor een Help die kan worden bijgewerkt
description: Bestandstypen die zijn toegestaan in een CAB-bestand voor een Help die kan worden bijgewerkt
ms.openlocfilehash: bb69b8b89a9a3a5c8c00059ec404a4d41a5db9a5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654730"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Bestandstypen die zijn toegestaan in een CAB-bestand voor een Help die kan worden bijgewerkt

Inhoud van niet-gecomprimeerd CAB-bestand is standaard beperkt tot 1 GB. Als u deze limiet wilt overs Laan, moeten gebruikers de para meter **Force** van de cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) gebruiken.

Om de beveiliging te waarborgen van de Help-bestanden die worden gedownload van Internet, kan een Help CAB-bestand dat kan worden bijgewerkt, alleen de onderstaande bestands typen bevatten. Met de cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) worden alle bestanden gevalideerd op basis van de schema's van het Help-onderwerp. Als `Update-Help` met de cmdlet een bestand wordt aangetroffen dat ongeldig is of niet het toegestane type heeft, wordt het ongeldige bestand niet geïnstalleerd en worden er geen bestanden meer geïnstalleerd op de computer van de gebruiker.

- Help-onderwerpen over XML voor cmdlets.
- Help-onderwerpen over XML voor scripts en functies.
- Help-onderwerpen over XML voor Power shell-providers.
- Help-onderwerpen op basis van tekst, zoals over onderwerpen.

De [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) de inhoud van het CAB-bestand te controleren wanneer het CAB-bestand wordt uitgepakt. Als `Update-Help` niet-compatibele bestands typen worden gevonden in een Help CAB-bestand dat kan worden bijgewerkt, wordt er een afsluit fout gegenereerd en wordt de bewerking gestopt. Er worden geen Help-bestanden van het CAB-bestand geïnstalleerd, zelfs van de bestands typen die voldoen aan het beleid.
