---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 9af931a1a2b545ba36826246c4155f42052a16bf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688432"
---
# <a name="mof-documents-are-encrypted-by-default"></a>MOF-documenten worden standaard versleuteld

Van configuratiedocumenten bevatten vertrouwelijke gegevens. In eerdere versies van DSC moest u distribueren en beheren van certificaten voor het beveiligen van referenties in een configuratie. Voor veel, dit is een belangrijke werk te verrichten en zelfs met al het werk die het heeft hiervoor die u nog steeds zijn links met sommige configuratie-informatie die niet is en kan niet worden beveiligd.

Dat is niet langer het geval omdat **de configuratie van alle MOF-bestanden worden beveiligd door standaard**. Er zijn geen certificaten of meta-configuratie-instellingen nodig zijn. Telkens wanneer u een configuratie MOF wordt opgeslagen naar de schijf met de lokale Configuration Manager (LCM) op een doelknooppunt, het is versleuteld. Het MOF-bestanden zijn versleuteld met behulp van [DPAPI](https://msdn.microsoft.com/library/ms995355.aspx). **Opmerking:** MOF-bestanden die worden gegenereerd door een configuratiescript zijn niet versleuteld.

**Voorbeeld:** Versleuteling in de pushmodus gebruikt ![MOF-versleuteling](../images/MOF_Encryption.jpg)

Als u al van de certificaat-methode gebruikmaakt voor het versleutelen van wachtwoorden of als u extra beveiliging nodig voor uw wachtwoorden hebt, de [bestaande methode van versleuteling op basis van certificaten](https://msdn.microsoft.com/powershell/dsc/securemof) blijven werken. Het resultaat wordt een MOF-document dat volledig is versleuteld met behulp van de DPAPIs en daarnaast wachtwoorden hebben binnen deze versleuteld.

Deze versleuteling is alleen van toepassing op configuratie MOF-documenten (pending.mof, current.mof, previous.mof en gedeeltelijke MOF-bestanden). META-configuratie van de MOF-bestanden nog steeds worden opgeslagen als tekst zonder opmaak omdat ze minder waarschijnlijk geheimen bevatten.
