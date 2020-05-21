---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC voor Linux nxFileLine-resource
ms.openlocfilehash: 4b07c5dd2715ce9f937b1e52deb97b6b4de64975
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560879"
---
# <a name="dsc-for-linux-nxfileline-resource"></a>DSC voor Linux nxFileLine-resource

De **nxFileLine** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van regels in een configuratie bestand op een Linux-knoop punt.

## <a name="syntax"></a>Syntaxis

```Syntax
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Bestandspad |Het volledige pad naar het bestand voor het beheren van de regels in het doel knooppunt. |
|ContainsLine |Een regel om ervoor te zorgen dat het bestand bestaat. Deze regel wordt toegevoegd aan het bestand als het niet in het bestand voor komt. **ContainsLine** is verplicht, maar kan worden ingesteld op een lege teken reeks ( `ContainsLine = ""` ) als dit niet nodig is. |
|DoesNotContainPattern |Een reguliere-expressie patroon voor lijnen die niet in het bestand moeten voor komen. Voor alle regels die voor komen in het bestand die overeenkomen met deze reguliere expressie, wordt de regel uit het bestand verwijderd. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u hoe u de **nxFileLine** -resource gebruikt om het bestand te configureren `/etc/sudoers` , zodat de gebruiker: monuser is geconfigureerd om niet requiretty.

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = "/etc/sudoers"
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```
