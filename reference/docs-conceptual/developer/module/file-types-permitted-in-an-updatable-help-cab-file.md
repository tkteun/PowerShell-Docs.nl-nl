---
title: Toegestane bestands typen in een Help CAB-bestand dat kan worden bijgewerkt | Microsoft Docs
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
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357503"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Bestandstypen die zijn toegestaan in een CAB-bestand voor een Help die kan worden bijgewerkt

In deze onderwerpen vindt u een overzicht van de inhouds vereisten voor CAB-bestanden die kunnen worden bijgewerkt.

## <a name="updatable-help-cab-file-requirements"></a>Bijwerk bare CAB-bestands vereisten voor Help

Inhoud van niet-gecomprimeerd CAB-bestand is standaard beperkt tot 1 GB. Als u deze limiet wilt overs Laan, moeten gebruikers de para meter **Force** van de cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) gebruiken.

Om de beveiliging te waarborgen van de Help-bestanden die worden gedownload van Internet, kan een Help CAB-bestand dat kan worden bijgewerkt, alleen de onderstaande bestands typen bevatten. Met de cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) worden alle bestanden gevalideerd op basis van de schema's van het Help-onderwerp. Als de `Update-Help`-cmdlet een bestand tegen komt dat ongeldig is of niet het toegestane type heeft, wordt het ongeldige bestand niet geïnstalleerd en worden er geen bestanden meer geïnstalleerd van de CAB op de computer van de gebruiker.

- Help-onderwerpen over XML voor cmdlets.

- Help-onderwerpen over XML voor scripts en functies.

- Help-onderwerpen over XML voor Windows Power shell-providers.

- Help-onderwerpen op basis van tekst, zoals over onderwerpen.

De [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) de inhoud van het CAB-bestand te controleren wanneer het CAB-bestand wordt uitgepakt. Als `Update-Help` niet-compatibele bestands typen vindt in een Help CAB-bestand dat kan worden bijgewerkt, wordt er een afsluit fout gegenereerd en wordt de bewerking gestopt. Er worden geen Help-bestanden van het CAB-bestand geïnstalleerd, zelfs van de bestands typen die voldoen aan het beleid.