---
ms.date: 07/29/2020
title: Nieuwe taal functies in Power shell 5,0
ms.openlocfilehash: dada39c4121a810c7ce87a642f232934152104e5
ms.sourcegitcommit: 339e5fc8a4cc18b4ff6956fe5180343588e40e30
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/29/2020
ms.locfileid: "87410169"
---
# <a name="new-language-features-in-powershell-50"></a>Nieuwe taal functies in Power shell 5,0

Power shell 5,0 heeft de mogelijkheid om klassen en andere door de gebruiker gedefinieerde typen te definiëren met behulp van formele syntaxis en semantiek, zoals andere objectgeoriënteerd programmeer talen. Het doel is om ontwikkel aars en IT-professionals in staat te stellen Power shell te gebruiken voor een breder scala aan gebruiks voorbeelden, het ontwikkelen van Power shell-artefacten (zoals DSC-resources) te vereenvoudigen en de dekking van management-Opper vlakken te versnellen.

Power shell 5,0 introduceert de volgende nieuwe taal elementen in Power shell:

### <a name="class-keyword"></a>Tref woord klasse

Het `class` sleutel woord definieert een nieuwe klasse. Dit is een True .NET Framework type. Klasse-leden zijn openbaar, maar alleen openbaar binnen het module bereik. U kunt niet naar de type naam verwijzen als een teken reeks (bijvoorbeeld `New-Object` niet werkt), en in deze release kunt u geen letterlijke type waarde (bijvoorbeeld) gebruiken `[MyClass]` buiten het script of module bestand waarin de klasse is gedefinieerd.

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a>Tref woord en opsommingen inventariseren

Ondersteuning voor het `enum` tref woord is toegevoegd. Dit maakt gebruik van een nieuwe regel als scheidings teken. Op dit moment kunt u geen enumerator definiëren in termen van zichzelf. U kunt echter een Enum initialiseren in termen van een andere Enum, zoals wordt weer gegeven in het volgende voor beeld. Het basis type kan ook niet worden opgegeven. het is altijd `[int]` .

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Een enumerator-waarde moet een geparseerd tijd constante zijn. U kunt deze niet instellen op het resultaat van een aangeroepen opdracht.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Opsommingen bieden ondersteuning voor reken kundige bewerkingen, zoals wordt weer gegeven in het volgende voor beeld.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a>Import-Dscresource bieden

`Import-DscResource` is nu een echt dynamisch sleutel woord. Power shell parseert de hoofd module van de opgegeven module. er wordt gezocht naar klassen die het kenmerk **dscresource bieden** bevatten.

### <a name="implementingassembly"></a>ImplementingAssembly

Er is een nieuw veld, **ImplementingAssembly**, toegevoegd aan **ModuleInfo**. Deze wordt ingesteld op de dynamische assembly die is gemaakt voor een script module als het script klassen definieert, of de geladen assembly voor binaire modules. Het is niet ingesteld wanneer **module type** is **manifest**.

Reflectie in het veld **ImplementingAssembly** detecteert bronnen in een module. Dit betekent dat u resources kunt detecteren die in Power shell of andere beheerde talen zijn geschreven.

## <a name="further-reading"></a>Meer lezen

- [about_Classes](/powershell/module/microsoft.powershell.core/about/about_classes)
- [about_Enum](/powershell/module/microsoft.powershell.core/about/about_enum)
- [about_Classes_and_DSC](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)
