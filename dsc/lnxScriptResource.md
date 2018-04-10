---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC voor Linux nxScript Resource
ms.openlocfilehash: 7c8c3aa16af5b31c0a549972288c9466bb56609d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxscript-resource"></a>DSC voor Linux nxScript Resource

De **nxScript** in PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het Linux-scripts uitvoeren op een Linux-knooppunt.

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
| GetScript| Biedt een script dat wordt uitgevoerd wanneer u aanroept de [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet. Het script moet beginnen met een shebang, zoals #! / bin/bash.|
| SetScript| Bevat een script. Wanneer u aanroept de [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) -cmdlet de **TestScript** als eerste wordt gestart. Als de **TestScript** blok retourneert een afsluitcode dan 0 is, de **SetScript** blok wordt uitgevoerd. Als de **TestScript** retourneert een afsluitcode 0, de **SetScript** kan niet worden uitgevoerd. Het script moet beginnen met een shebang zoals `#!/bin/bash`.|
| TestScript| Bevat een script. Wanneer u aanroept de [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet dit script wordt uitgevoerd. Als deze een afsluitcode die gelijk zijn aan 0 retourneert, wordt de SetScript wordt uitgevoerd. Als deze een afsluitcode 0 retourneert, de **SetScript** kan niet worden uitgevoerd. De **TestScript** wordt ook uitgevoerd wanneer u aanroept de [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet. Echter, in dit geval de **SetScript** niet wordt uitgevoerd, ongeacht welke afsluitcode wordt geretourneerd vanaf de **TestScript**. De **TestScript** moet een afsluitcode 0 retourneren als de configuratie van de werkelijke overeenkomt met de huidige configuratie van de gewenste status en een afsluitcode code andere dan 0 als het niet overeenkomen. (De huidige configuratie van de gewenste status is de laatste configuratie van kracht op het knooppunt dat van DSC gebruikmaakt). Het script moet beginnen met een shebang, zoals 1#!/bin/bash.1|
| Gebruiker| De gebruiker het script als uitvoeren.|
| Groep| De groep het script als uitvoeren.|
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld toont het gebruik van de **nxScript** resource toe aan het beheer van aanvullende configuratie uitvoeren.

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