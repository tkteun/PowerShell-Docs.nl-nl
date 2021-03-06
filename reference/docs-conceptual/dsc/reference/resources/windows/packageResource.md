---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-pakket resource
description: DSC-pakket resource
ms.openlocfilehash: 4bcc6dc68a37ebe434e30339452cd7269f984ae9
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142868"
---
# <a name="dsc-package-resource"></a>DSC-pakket resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x

De **pakket** resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het installeren of verwijderen van pakketten, zoals Windows Installer en setup.exe pakketten, op een doel knooppunt.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>Syntax

```Syntax
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ ReturnCode = [UInt32[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Naam |Hiermee wordt de naam aangegeven van het pakket waarvoor u een specifieke status wilt controleren. |
|Pad |Hiermee wordt het pad aangegeven waar het pakket zich bevindt. |
|ProductId |Hiermee wordt de product-ID aangegeven waarmee het pakket uniek wordt geïdentificeerd. |
|Argumenten |Een lijst met argumenten die precies zo worden door gegeven aan het pakket. |
|Referentie |Biedt toegang tot het pakket op een externe bron. Deze eigenschap wordt niet gebruikt om het pakket te installeren. Het pakket wordt altijd op het lokale systeem geïnstalleerd. |
|Logboekpad |Hiermee wordt het volledige pad aangegeven waar u wilt dat de provider een logboek bestand opslaat om het pakket te installeren of te verwijderen. |
|Return code |Geeft de verwachte retour code aan. Als de daad werkelijke retour code niet overeenkomt met de verwachte waarde die hier wordt opgegeven, wordt er een fout geretourneerd door de configuratie. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
|Zo |Hiermee wordt aangegeven of het pakket is geïnstalleerd. Stel deze eigenschap in op **afwezig** om te controleren of het pakket niet is geïnstalleerd (of verwijder het pakket als dit is geïnstalleerd). Stel deze in op **aanwezig** om te controleren of het pakket is geïnstalleerd. De standaard waarde is **aanwezig** . |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="example"></a>Voorbeeld

In dit voor beeld wordt het MSI-installatie programma uitgevoerd dat zich bevindt in het opgegeven pad en heeft de opgegeven product-ID.

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```
