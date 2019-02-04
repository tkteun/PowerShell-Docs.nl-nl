---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxFileLine-Resource
ms.openlocfilehash: 6a91db25638b09659adfabcec78f91bcb2e69dd9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684967"
---
# <a name="dsc-for-linux-nxfileline-resource"></a>DSC voor Linux nxFileLine-Resource

De **nxFileLine** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van de regels in een configuratiebestand op een Linux-knooppunt.

## <a name="syntax"></a>Syntaxis

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap |  Beschrijving |
|---|---|
| FilePath| Het volledige pad naar het bestand om regels in op het doelknooppunt te beheren.|
| ContainsLine| Een regel om ervoor te zorgen bestaat in het bestand. Deze regel wordt toegevoegd aan het bestand als deze niet in het bestand bestaat. **ContainsLine** is verplicht, maar kan worden ingesteld op een lege tekenreeks (`ContainsLine = ""`) als deze niet nodig is.|
| DoesNotContainPattern| Een reguliere-expressiepatroon voor regels die niet in het bestand moet bestaan. Voor alle regels die zijn opgenomen in het bestand die overeenkomen met deze reguliere expressie, wordt de regel wordt verwijderd uit het bestand.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Voorbeeld

In dit voorbeeld wordt met behulp van de **nxFileLine** resource die u wilt configureren van de `/etc/sudoers` -bestand, ervoor zorgen dat de gebruiker: monuser is geconfigureerd voor het niet requiretty.

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```