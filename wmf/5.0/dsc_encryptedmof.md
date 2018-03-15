---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 60abe525ca1bdcebca570f2ef3656f32dca3747f
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="mof-documents-are-encrypted-by-default"></a>MOF documenten worden gecodeerd

Configuratiedocumenten bevatten gevoelige gegevens. In eerdere versies van DSC moest u distribueren en beheren van certificaten voor het beveiligen van referenties in een configuratie. Dit is een belangrijke management last voor een groot deel en zelfs met al het werk geduurd hiervoor die u nog steeds bepaalde configuratie-informatie die niet en kan niet worden beveiligd zijn weggelaten. 

Dat is niet meer het geval omdat **de configuratie van alle MOF-bestanden zijn standaard beveiligd**. Er zijn geen certificaten of meta-configuratie-instellingen zijn vereist. Telkens wanneer u een configuratie MOF wordt opgeslagen naar de schijf met de lokale Configuration Manager (LCM) op een doelknooppunt, zijn versleuteld. Het MOF-bestanden zijn versleuteld met [DPAPI](https://msdn.microsoft.com/library/ms995355.aspx). **Opmerking:** MOF-bestanden die worden gegenereerd door een configuratiescript zijn niet versleuteld.

**Voorbeeld:** -versleuteling in de modus push ![MOF-versleuteling](../images/MOF_Encryption.jpg)

Als u al van de certificaat-methode gebruikmaakt voor het versleutelen van wachtwoorden of als u extra beveiliging nodig hebt voor uw wachtwoorden de [bestaande methode van certificaatversleuteling op basis van](https://msdn.microsoft.com/powershell/dsc/securemof) blijven werken. Het resultaat wordt een MOF-document dat volledig is versleuteld met behulp van de DPAPIs en bovendien wachtwoorden hebben binnen deze versleuteld.

Deze versleuteling is alleen van toepassing op configuration MOF documenten (pending.mof, current.mof, previous.mof en gedeeltelijke MOF-bestanden). META-configuratie MOF-bestanden worden nog steeds opgeslagen als tekst zonder opmaak, omdat ze minder waarschijnlijk geheimen bevatten.

