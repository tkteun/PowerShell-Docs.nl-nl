---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC voor Linux nxSshAuthorizedKeys Resource
ms.openlocfilehash: a36d158735839727e98893ce9fce174a0f37f764
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>DSC voor Linux nxSshAuthorizedKeys Resource

De **nxAuthorizedKeys** in PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme voor het beheren van geautoriseerd ssh-sleutels voor een opgegeven gebruiker.

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
| KeyComment| Een unieke Opmerking voor de sleutel. Dit wordt gebruikt om sleutels uniek te identificeren.|
| Zorg ervoor dat| Hiermee geeft u op of de sleutel is gedefinieerd. Deze eigenschap instellen op 'Ontbreekt' om te controleren of dat de sleutel bestaat niet in het gebruikersbestand geautoriseerde sleutels. Stel deze in op 'Aanwezig' om te controleren of dat de sleutel is gedefinieerd in het geautoriseerde sleutelbestand van de gebruiker.|
| Gebruikersnaam| De gebruikersnaam voor het beheren van de ssh-sleutels voor gemachtigd. Als geen gedefinieerd, is de standaardgebruiker 'root'.|
| Toets| De inhoud van de sleutel. Dit is vereist als **Zorg ervoor dat** is ingesteld op 'Aanwezig'.|
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld definieert een ssh geautoriseerd openbare sleutel voor de gebruiker 'monuser'.

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