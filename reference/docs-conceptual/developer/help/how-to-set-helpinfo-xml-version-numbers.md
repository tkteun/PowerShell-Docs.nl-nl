---
ms.date: 09/12/2016
ms.topic: reference
title: HelpInfo-XML-versienummers instellen
description: HelpInfo-XML-versienummers instellen
ms.openlocfilehash: 9ef1940ca05d8aa9b04770013287490b71c8065a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658832"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="6caea-103">HelpInfo-XML-versienummers instellen</span><span class="sxs-lookup"><span data-stu-id="6caea-103">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="6caea-104">In dit onderwerp wordt uitgelegd hoe u de versie nummers instelt en verhoogt in een Help-informatie bestand dat kan worden bijgewerkt, ook wel bekend als een ' HelpInfo XML-bestand '.</span><span class="sxs-lookup"><span data-stu-id="6caea-104">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="6caea-105">HelpInfo-XML-versienummers instellen</span><span class="sxs-lookup"><span data-stu-id="6caea-105">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="6caea-106">De versie nummers in een HelpInfo XML-bestand zijn essentieel voor de werking van de Help-informatie die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="6caea-106">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="6caea-107">Met de cmdlets [Update Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) en [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) worden nieuwe Help-bestanden alleen gedownload wanneer het versie nummer voor een gebruikersinterface cultuur in het HelpInfo-bestand van de externe-XML groter is dan het versie nummer voor die gebruikersinterface cultuur in de lokale HelpInfo-XML, of er is geen lokaal HelpInfo XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="6caea-107">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="6caea-108">Het HelpInfo XML-bestand maakt gebruik van het versie nummer van 4 onderdelen dat is gedefinieerd in de klasse **System. version** van het Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6caea-108">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="6caea-109">De indeling is `N1.N2.N3.N4`.</span><span class="sxs-lookup"><span data-stu-id="6caea-109">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="6caea-110">Module auteurs kunnen elk schema voor versie nummering gebruiken dat is toegestaan door de klasse **System. version** .</span><span class="sxs-lookup"><span data-stu-id="6caea-110">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="6caea-111">Bij te werken Help is alleen vereist dat het versie nummer van een UI-cultuur toeneemt wanneer een nieuwe versie van het CAB-bestand voor die GEBRUIKERSINTERFACE cultuur wordt geüpload naar de locatie die is opgegeven door het element **HelpContentURI** in het XML-bestand HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="6caea-111">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="6caea-112">In het volgende voor beeld ziet u de elementen van het HelpInfo XML-bestand voor de Duitse interface cultuur (de-DE) wanneer de versie 2.15.0.10 is.</span><span class="sxs-lookup"><span data-stu-id="6caea-112">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml
<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="6caea-113">Het versie nummer voor een GEBRUIKERSINTERFACE cultuur weerspiegelt de versie van het CAB-bestand voor die GEBRUIKERSINTERFACE cultuur.</span><span class="sxs-lookup"><span data-stu-id="6caea-113">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="6caea-114">Het versie nummer is van toepassing op het hele CAB-bestand.</span><span class="sxs-lookup"><span data-stu-id="6caea-114">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="6caea-115">U kunt geen andere versie nummers instellen voor verschillende bestanden in het CAB-bestand.</span><span class="sxs-lookup"><span data-stu-id="6caea-115">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="6caea-116">Het versie nummer voor elke UI-cultuur wordt onafhankelijk geëvalueerd en hoeft niet te zijn gerelateerd aan de versie nummers voor andere GEBRUIKERSINTERFACE culturen die door de module worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="6caea-116">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>
