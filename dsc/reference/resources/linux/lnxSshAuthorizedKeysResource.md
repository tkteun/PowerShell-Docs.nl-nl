---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxSshAuthorizedKeys-Resource
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687802"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>DSC voor Linux nxSshAuthorizedKeys-Resource

De **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van geautoriseerde ssh-sleutels voor een opgegeven gebruiker.

## <a name="syntax"></a>Syntaxis

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap |  Beschrijving |
|---|---|
| KeyComment| Een unieke Opmerking voor de sleutel. Dit wordt gebruikt voor het aanduiden van sleutels.|
| Zorg ervoor dat| Hiermee geeft u op of de sleutel is gedefinieerd. Deze eigenschap instellen op 'Ontbreekt' om te controleren of dat de sleutel bestaat niet in het geautoriseerde sleutelsbestand van de gebruiker. Stel deze in op 'Aanwezig' om te controleren of dat de sleutel is gedefinieerd in de gemachtigde sleutelbestand van de gebruiker.|
| Gebruikersnaam| De gebruikersnaam voor het beheren van ssh-sleutels voor gemachtigd. Als niet is gedefinieerd, is de standaardwaarde 'root'.|
| Toets| De inhoud van de sleutel. Dit is vereist als **Zorg ervoor dat** is ingesteld op 'Aanwezig'.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld definieert een openbare ssh gemachtigd voor de gebruiker 'monuser'.

```
Import-DSCResource -Module nx

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
}
}
```