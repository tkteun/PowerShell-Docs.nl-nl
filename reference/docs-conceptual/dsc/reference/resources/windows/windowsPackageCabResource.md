---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC WindowsPackageCab-resource
ms.openlocfilehash: 1b1b8b6d065882400608d26a991318fec9ad5747
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563951"
---
# <a name="dsc-windowspackagecab-resource"></a>DSC WindowsPackageCab-resource

> Van toepassing op: Windows Power shell 5,1

De **WindowsPackageCab** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het installeren of verwijderen van Windows CAB-pakketten (CAB) op een doel knooppunt.

Op het doel knooppunt moet de Power shell-module DISM zijn geïnstalleerd. Zie [DISM gebruiken in Windows Power shell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14)voor meer informatie.

## <a name="syntax"></a>Syntaxis

```Syntax
{
    Name = [string]
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    Ensure = [string] { Absent | Present }
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Name |Hiermee wordt de naam van het pakket aangegeven dat u een specifieke status wilt bieden. |
|Bronpad |Hiermee wordt het pad aangegeven waar het pakket zich bevindt. |
|Logboekpad |Hiermee wordt het volledige pad aangegeven waar u wilt dat de provider een logboek bestand opslaat om het pakket te installeren of te verwijderen. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
|Zo |Hiermee wordt aangegeven of het pakket is geïnstalleerd. Stel deze eigenschap in op **afwezig** om te controleren of het pakket niet is geïnstalleerd (of verwijder het pakket als dit is geïnstalleerd). Stel deze in op **aanwezig** om te controleren of het pakket is geïnstalleerd. **Zorg ervoor dat** de eigenschap vereist is voor de **WindowsPackageCab** -resource. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

## <a name="example"></a>Voorbeeld

De volgende voorbeeld configuratie haalt invoer parameters op en zorgt ervoor dat het CAB-bestand dat is opgegeven met de `$Name` para meter, wordt geïnstalleerd.

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```
