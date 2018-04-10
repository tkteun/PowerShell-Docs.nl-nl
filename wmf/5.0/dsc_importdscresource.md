---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: a3b176101bebf7081febd8629bddcfa0ae1e7540
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a>Importeren DscResource sleutelwoord ondersteunt ModuleVersion - parameter

We hebben een nieuwe parameter voor toegevoegd de `Import-DscResource` dynamische sleutelwoord beschikbaar bij het ontwerpen van DSC-configuraties. Configuratie auteurs kunnen nu precies welke moduleversie om te laden van de DSC-resources van opgeven. De nieuwe syntaxis van het trefwoord is:

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* **Naam**: namen van een of meer resources om te importeren.
* **Modulenaam**: modulenamen of ModuleSpecification objecten van een of meer modules voor het importeren.
* **ModuleVersion**: versie van de module iet importeren. Als u gebruikt, moet de modulenaam slechts één module met de naam vertegenwoordigen.

In de Windows PowerShell ISE, wordt deze weergegeven met IntelliSense:

![](../images/Import-DscResource-Modversion.jpg)

**Opmerking**: de `–ModuleVersion` parameter kan alleen worden gebruikt in combinatie met de `–ModuleName` parameter. Deze kan niet worden gebruikt met resourcenamen met alleen de `–Name` parameter.

Voordat dit is de enige manier om de moduleversie opgeven bij het laden van DSC-resources met behulp van de specificatie moduleobject bijvoorbeeld: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`