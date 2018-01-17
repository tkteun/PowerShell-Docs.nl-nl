---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC voor Linux nxFileLine Resource
ms.openlocfilehash: 281f08c1dbf42372762a2b1b9838427b910ea791
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxfileline-resource"></a>DSC voor Linux nxFileLine Resource

De **nxFileLine** in PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme op voor het beheren van de regels in een configuratiebestand op een Linux-knooppunt.

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
| FilePath| Het volledige pad naar het bestand om regels in in het doelknooppunt te beheren.| 
| ContainsLine| Een regel om ervoor te zorgen bestaat in het bestand. Deze regel wordt toegevoegd aan het bestand als deze niet in het bestand bestaat nog. **ContainsLine** is verplicht, maar kan worden ingesteld op een lege tekenreeks ('ContainsLine = ''') als deze niet nodig is.| 
| DoesNotContainPattern| Een reguliere-expressiepatroon voor regels die niet in het bestand moet bestaan. Voor alle regels die zijn opgenomen in het bestand die overeenkomen met de reguliere expressie, wordt de regel wordt verwijderd uit het bestand.| 
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="example"></a>Voorbeeld

In dit voorbeeld wordt met behulp van de **nxFileLine** resource voor het configureren van de `/etc/sudoers` -bestand, zorgt u ervoor dat de gebruiker: monuser niet requiretty is geconfigureerd.

```
Import-DSCResource -Module nx 

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
} 
```

