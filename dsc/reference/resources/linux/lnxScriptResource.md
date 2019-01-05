---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxScript Resource
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048258"
---
# <a name="dsc-for-linux-nxscript-resource"></a>DSC voor Linux nxScript Resource

De **nxScript** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het Linux-scripts uitvoeren op een Linux-knooppunt.

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

|  Eigenschap |  Beschrijving |
|---|---|
| Ophalen script| Biedt een script dat wordt uitgevoerd wanneer u aanroepen de [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet. Het script moet beginnen met een shebang, zoals #! / bin/bash.|
| SetScript| Bevat een script. Wanneer u aanroepen de [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, de **TestScript** als eerste wordt gestart. Als de **TestScript** blok retourneert een afsluitcode dan 0, de **SetScript** blok wordt uitgevoerd. Als de **TestScript** retourneert een afsluitcode 0, de **SetScript** kan niet worden uitgevoerd. Het script moet beginnen met een shebang zoals `#!/bin/bash`.|
| TestScript| Bevat een script. Wanneer u aanroepen de [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, met dit script wordt uitgevoerd. Als deze een afsluitcode dan 0 retourneert, wordt de SetScript wordt uitgevoerd. Als deze een afsluitcode 0 retourneert, de **SetScript** kan niet worden uitgevoerd. De **TestScript** wordt ook uitgevoerd wanneer u aanroepen de [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet. Echter, in dit geval de **SetScript** niet wordt uitgevoerd, ongeacht welke afsluitcode wordt geretourneerd vanaf de **TestScript**. De **TestScript** moet retourneert een afsluitcode 0 als de feitelijke configuratie komt overeen met de huidige configuratie van gewenste status en een afsluiten code dan 0 als deze niet overeenkomt. (De huidige configuratie van gewenste status is de laatste configuratie van kracht op het knooppunt dat van DSC gebruikmaakt). Het script moet beginnen met een shebang, zoals 1#!/bin/bash.1|
| Gebruiker| De gebruiker het script als uit te voeren.|
| Groep| De groep het script als uit te voeren.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet u het gebruik van de **nxScript** resource die u wilt het beheer van aanvullende configuratie uitvoeren.

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