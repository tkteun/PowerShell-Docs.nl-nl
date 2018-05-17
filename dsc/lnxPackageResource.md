---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: DSC voor Linux nxPackage Resource
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-for-linux-nxpackage-resource"></a>DSC voor Linux nxPackage Resource

De **nxPackage** in PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van pakketten op een Linux-knooppunt.

## <a name="syntax"></a>Syntaxis

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap |  Beschrijving |
|---|---|
| Naam| De naam van het pakket waarvan u wilt om te controleren of een specifieke status.|
| Zorg ervoor dat| Bepaalt of Controleer of het pakket bestaat. Deze eigenschap instellen op 'Aanwezig' om te controleren of dat het pakket bestaat. Stel deze in op 'Ontbreekt' om te controleren of dat het pakket bestaat niet. De standaardwaarde is 'Aanwezig'.|
| PackageManager| Ondersteunde waarden zijn 'yum', 'apt' en 'zypper'. Hiermee geeft u de package manager te gebruiken bij het installeren van pakketten. Als **FilePath** is opgegeven, wordt het opgegeven pad wordt gebruikt om het pakket te installeren. Een Package Manager anders wordt gebruikt voor het installeren van het pakket van een vooraf geconfigureerde opslagplaats. Als geen van beide **PackageManager** noch **FilePath** zijn opgegeven, de standaard package manager voor het systeem wordt gebruikt.|
| filePath| Het pad waar het pakket zich bevindt|
| PackageGroup| Als **$true**, wordt de **naam** wordt verwacht dat de naam van de groep van een pakket voor gebruik met een **PackageManager**. **PacakgeGroup** is niet geldig bij het opgeven van een **FilePath**.|
| Argumenten| Een tekenreeks van de argumenten die worden doorgegeven aan het pakket precies zoals opgegeven.|
| ReturnCode| De verwachte retourcode. Als de werkelijke retourcode komt niet overeen met die zijn de verwachte waarde opgegeven, dat wordt de configuratie een fout geretourneerd.|
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld zorgt ervoor dat het pakket met de naam 'httpd' op een Linux-computer, met behulp van de 'Yum' package manager is geïnstalleerd.

```
Import-DSCResource -Module nx

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```