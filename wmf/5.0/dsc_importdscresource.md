---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 46a278b83edb9d8e3d75b0874603710d416be3b5
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998517"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a>Sleutelwoord sleutelwoorden import-dscresource bieden ondersteuning biedt voor de parameter - ModuleVersion

We hebben een nieuwe parameter toegevoegd de `Import-DscResource` dynamische sleutelwoord beschikbaar bij het ontwerpen van DSC-configuraties. Configuratie auteurs kunnen nu precies welke moduleversie voor het laden van de DSC-resources uit opgeven. De nieuwe syntaxis van het sleutelwoord is:

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* **Naam**: naam van een of meer resources te importeren.
* **ModuleName**: modulenamen of ModuleSpecification objecten van een of meer modules te importeren.
* **ModuleVersion**: versie van de module te importeren. Als u gebruikt, moet ModuleName slechts één module met de naam vertegenwoordigen.

In de Windows PowerShell ISE, wordt deze weergegeven met IntelliSense:

![](../images/Import-DscResource-Modversion.jpg)

**Houd er rekening mee**: de `–ModuleVersion` parameter kan alleen worden gebruikt in combinatie met de `–ModuleName` parameter. Deze kan niet worden gebruikt met namen van voorbeeldresources met alleen de `–Name` parameter.

Voordat dit is de enige manier om op te geven van de versie van de module bij het laden van DSC-resources met behulp van de Module-specificatie-object, bijvoorbeeld: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`
