---
title: Over het instellen van de versienummers HelpInfo XML | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: b98e6879bbfe0e3ec1a9ab37496dde44caf523a4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082274"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="aa1ae-102">HelpInfo-XML-versienummers instellen</span><span class="sxs-lookup"><span data-stu-id="aa1ae-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="aa1ae-103">In dit onderwerp wordt uitgelegd hoe u het instellen en het verhogen van de versienummers in een bestand bij te werken Help-informatie, bekend als een 'HelpInfo XML file'.</span><span class="sxs-lookup"><span data-stu-id="aa1ae-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="aa1ae-104">HelpInfo-XML-versienummers instellen</span><span class="sxs-lookup"><span data-stu-id="aa1ae-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="aa1ae-105">De versienummers in een HelpInfo XML-bestand zijn essentieel voor de werking van het bij te werken Help.</span><span class="sxs-lookup"><span data-stu-id="aa1ae-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span>
<span data-ttu-id="aa1ae-106">De [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en [Help opslaan](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets nieuwe help-bestanden te downloaden alleen wanneer het versienummer voor een UI-cultuur in de externe HelpInfo XML-bestand is groter dan het versienummer voor die gebruikersinterfacecultuur in de lokale HelpInfo XML, of er is geen lokale HelpInfo XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="aa1ae-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="aa1ae-107">Het HelpInfo XML-bestand maakt gebruik van de 4-onderdeel versienummer dat is gedefinieerd in de **System.Version** klasse van Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa1ae-107">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="aa1ae-108">De indeling is `N1.N2.N3.N4`.</span><span class="sxs-lookup"><span data-stu-id="aa1ae-108">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="aa1ae-109">Module-auteurs kunnen een schema dat is toegestaan door de nummering versie gebruiken de **System.Version** klasse.</span><span class="sxs-lookup"><span data-stu-id="aa1ae-109">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="aa1ae-110">Bij te werken Help vereist alleen dat het versienummer voor een verhoging van de cultuur gebruikersinterface wanneer een nieuwe versie van het CAB-bestand voor dat gebruikersinterfacecultuur wordt geüpload naar de locatie die is opgegeven door de **HelpContentURI** -element in het HelpInfo XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="aa1ae-110">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="aa1ae-111">Het volgende voorbeeld ziet u de elementen van het HelpInfo XML-bestand voor de Duitse (nl-nl) gebruikersinterface van de cultuur als de versie 2.15.0.10.</span><span class="sxs-lookup"><span data-stu-id="aa1ae-111">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="aa1ae-112">Het versienummer voor een gebruikersinterfacecultuur geeft de versie van het CAB-bestand voor dat gebruikersinterfacecultuur.</span><span class="sxs-lookup"><span data-stu-id="aa1ae-112">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="aa1ae-113">Het versienummer is van toepassing op het hele CAB-bestand.</span><span class="sxs-lookup"><span data-stu-id="aa1ae-113">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="aa1ae-114">U kunt verschillende versienummers voor verschillende bestanden niet instellen in het CAB-bestand.</span><span class="sxs-lookup"><span data-stu-id="aa1ae-114">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="aa1ae-115">Het versienummer voor elk gebruikersinterfacecultuur onafhankelijk wordt geëvalueerd en moet niet worden gerelateerd aan de versienummers voor andere UI-culturen die ondersteuning biedt voor de module.</span><span class="sxs-lookup"><span data-stu-id="aa1ae-115">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>