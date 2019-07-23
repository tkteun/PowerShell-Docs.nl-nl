---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: DSC voor Linux nxScript-resource
ms.openlocfilehash: 0ad0530f1de7b86ff48c4eb1f79870f6682894a1
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372165"
---
# <a name="dsc-for-linux-nxscript-resource"></a>DSC voor Linux nxScript-resource

De **nxScript** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het uitvoeren van Linux-scripts op een Linux-knoop punt.

## <a name="syntax"></a>Syntaxis

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap |  Description |
|---|---|
| GetScript| Biedt een script om de huidige status van de machine te retour neren.  Dit script wordt uitgevoerd wanneer u het script [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) aanroept. Het script moet beginnen met een shebang, zoals #!/bin/bash.|
| SetScript| Bevat een script dat de computer in de juiste status plaatst. Wanneer u het script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) aanroept, wordt eerst de **TestScript** uitgevoerd. Als het **TestScript** -blok een andere afsluit code dan 0 retourneert, wordt het blok **SetScript** uitgevoerd. Als de **TestScript** de afsluit code 0 retourneert, wordt de **SetScript** niet uitgevoerd. Het script moet beginnen met een shebang, zoals `#!/bin/bash`.|
| TestScript| Voorziet in een script dat evalueert of het knoop punt momenteel de juiste status heeft. Wanneer u het script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) aanroept, wordt dit script uitgevoerd. Als het een andere afsluit code dan 0 retourneert, wordt de SetScript uitgevoerd. Als de methode de afsluit code 0 retourneert, wordt de **SetScript** niet uitgevoerd. De **TestScript** wordt ook uitgevoerd wanneer u het script [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) aanroept. In dit geval wordt de **SetScript** echter niet uitgevoerd, ongeacht de afsluit code die wordt geretourneerd door de **TestScript**. De **TestScript** moet inhoud bevatten en moet een afsluit code van 0 retour neren als de werkelijke configuratie overeenkomt met de huidige gewenste status configuratie en een andere afsluit code dan 0 als deze niet overeenkomt. (De huidige gewenste status configuratie is de laatste configuratie die is uitgevaardigd op het knoop punt dat gebruikmaakt van DSC). Het script moet beginnen met een shebang, zoals 1 #!/bin/bash.1|
| Gebruiker| De gebruiker voor het uitvoeren van het script als.|
| Groep| De groep waarop het script moet worden uitgevoerd.|
| DependsOn | Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van `DependsOn = "[ResourceType]ResourceName"`deze eigenschap is bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de **naam** **ResourceName** is en het type van de bron **resource is.**|

## <a name="example"></a>Voorbeeld

In het volgende voor beeld wordt het gebruik van de **nxScript** -resource voor het uitvoeren van extra configuratie beheer gedemonstreerd.

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
}
}
```
