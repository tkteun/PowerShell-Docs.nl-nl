---
ms.date: 07/17/2020
ms.topic: reference
title: DSC voor Linux nxPackage-resource
description: DSC voor Linux nxPackage-resource
ms.openlocfilehash: b84c7963297e8a88e729cd67611245b017c27fb7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648844"
---
# <a name="dsc-for-linux-nxpackage-resource"></a>DSC voor Linux nxPackage-resource

De **nxPackage** -resource in Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van pakketten op een Linux-knoop punt.

## <a name="syntax"></a>Syntax

```Syntax
nxPackage <string> #ResourceName
{
    Name = <string>
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ FilePath = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Naam |De naam van het pakket waarvoor u een specifieke status wilt controleren. |
|PackageManager |Ondersteunde waarden zijn **yum** , **apt** en **Zypper** . Hiermee geeft u op welke pakket beheer moet worden gebruikt bij het installeren van pakketten. Als **filepath** is opgegeven, wordt het opgegeven pad gebruikt om het pakket te installeren. Anders wordt een pakket beheer gebruikt om het pakket te installeren vanuit een vooraf geconfigureerde opslag plaats. Als geen van beide **PackageManager** of **filepath** wordt gegeven, wordt de standaard pakket beheerder voor het systeem gebruikt. |
|PackageGroup |Als `$true` de **naam** naar verwachting de naam van een pakket groep is voor gebruik met een **PackageManager** . **PackageGroup** is niet geldig voor het opgeven van een **bestandspad** . |
|Argumenten |Een teken reeks argumenten die exact als opgegeven worden door gegeven aan het pakket. |
|Return code |De verwachte retour code. Als de daad werkelijke retour code niet overeenkomt met de verwachte waarde die hier wordt opgegeven, wordt er een fout geretourneerd door de configuratie. |
|Bestandspad |Het bestandspad waar het pakket zich bevindt. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
|Zo |Hiermee wordt bepaald of er wordt gecontroleerd of het pakket bestaat. Stel deze eigenschap in op **aanwezig** om te controleren of het pakket bestaat. Stel deze in op **afwezig** om ervoor te zorgen dat het pakket niet bestaat. De standaard waarde is **aanwezig** . |

## <a name="example"></a>Voorbeeld

In het volgende voor beeld wordt ervoor gezorgd dat het pakket met de naam ' httpd ' is geïnstalleerd op een Linux-computer met behulp van het pakket beheer ' yum '.

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxPackage httpd
    {
        Name = "httpd"
        Ensure = "Present"
        PackageManager = "Yum"
    }
}
```
