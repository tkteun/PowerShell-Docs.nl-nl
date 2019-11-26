---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC voor Linux nxSshAuthorizedKeys-resource
ms.openlocfilehash: 6e008efcbff2e679650d0bc3d5b8b573f6ef83e0
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941458"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>DSC voor Linux nxSshAuthorizedKeys-resource

De **nxAuthorizedKeys** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van geautoriseerde SSH-sleutels voor een opgegeven gebruiker.

## <a name="syntax"></a>Syntaxis

```Syntax
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>properties

|Eigenschap |Description |
|---|---|
|Opmerkingaanwijzer |Een unieke opmerking voor de sleutel. Dit wordt gebruikt om sleutels uniek te identificeren. |
|Gebruikersnaam |De gebruikers naam voor het beheren van geautoriseerde SSH-sleutels voor. Als dit niet is gedefinieerd, is de standaard gebruiker **root**. |
|Sleutel |De inhoud van de sleutel. Dit is vereist als **dat** is ingesteld op **aanwezig**.|

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Description |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is. |
|Zo |Hiermee wordt aangegeven of de sleutel is gedefinieerd. Stel deze eigenschap in op **afwezig** om ervoor te zorgen dat de sleutel niet bestaat in het geautoriseerde sleutel bestand van de gebruiker. Stel deze in op **aanwezig** om te controleren of de sleutel is gedefinieerd in het geautoriseerde sleutel bestand van de gebruiker. |

## <a name="example"></a>Voorbeeld

In het volgende voor beeld wordt een open bare SSH-sleutel gedefinieerd voor de gebruiker ' monuser '.

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxSshAuthorizedKeys myKey
    {
        KeyComment = "myKey"
        Ensure = "Present"
        Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
        UserName = "monuser"
    }
}
```