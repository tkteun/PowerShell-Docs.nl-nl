---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC-Bestandsresource
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688425"
---
# <a name="dsc-file-resource"></a>DSC-Bestandsresource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De resource van het bestand in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van bestanden en mappen op het doelknooppunt. De **doelpad** en **bronpad** moeten beide toegankelijk zijn via het doel-knooppunt.

## <a name="syntax"></a>Syntaxis

```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap       |Beschrijving                                                                   |Vereist|Standaard|
|---------------|------------------------------------------------------------------------------|--------|-------|
|DestinationPath|De locatie op het doelknooppunt die u wilt ervoor zorgen is `Present` of `Absent`.|Ja|Nee|
|Kenmerken     |De gewenste status van de kenmerken voor het betreffende bestand of map. Geldige waarden zijn **archief**, **verborgen**, **ReadOnly**, en **System**.|Nee|Geen|
|Controlesom      |Het type van de controlesom te gebruiken bij het bepalen of twee bestanden hetzelfde zijn. Geldige waarden zijn: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.|Nee|Alleen de naam van bestand of map wordt vergeleken.|
|Inhoud       |Alleen geldig in combinatie met `File` type. Hiermee geeft u de inhoud naar Zorg ervoor dat zijn `Present` of `Absent` van het doelbestand. |Nee|Geen|
|Referentie     |De referenties die vereist voor toegang tot resources, zoals de bronbestanden zijn.|Nee|Het computeraccount van het doelknooppunt. (*Zie Opmerking*)|
|Zorg ervoor dat         |De gewenste status van het doelbestand of map. |Nee|**Aanwezig**|
|Force          |Bewerkingen voor gegevenstoegang die in een fout resulteren zouden (zoals een bestand te overschrijven of verwijderen van een directory die is niet leeg) vervangt.|Nee|`$false`|
|Recurse        |Alleen geldig in combinatie met `Directory` type. Voert de recursief status bewerking op alle submappen.|Nee|`$false`|
|DependsOn      |Hiermee stelt u een afhankelijkheid op de opgegeven resource (s). Deze bron wordt alleen uitgevoerd na voltooiing van uitvoering van alle afhankelijke resources. U kunt opgeven dat afhankelijke resources met behulp van de syntaxis van de `"[ResourceType]ResourceName"`. Zie [about_DependsOn](../../../configurations/resource-depends-on.md)|Nee|Geen|
|SourcePath     |Het pad van waaruit de resource van het bestand of map kopiëren.|Nee|Geen|
|Type           |Het type resource wordt geconfigureerd. Geldige waarden zijn `Directory` en `File`.|Nee|`File`|
|MatchSource    |Hiermee bepaalt u als de resource voor nieuwe bestanden die zijn toegevoegd aan de bronmap na de eerste kopie controleren moet. Een waarde van `$true` geeft aan dat na de eerste kopie een nieuwe bronbestanden moeten worden gekopieerd naar de bestemming. Indien ingesteld op `$False`, de resource in de cache opgeslagen inhoud van de bronmap en negeert alle bestanden die zijn toegevoegd na de eerste kopie.|Nee|`$false`|

> [!WARNING]
> Als u een waarde op voor geen opgeeft `Credential` of `PSRunAsCredential` (PS V.5), de bron wordt het computeraccount van het doelknooppunt gebruiken voor toegang tot de `SourcePath`.  Wanneer de `SourcePath` is een UNC-share, kan dit leiden tot een fout "Toegang geweigerd". Zorg ervoor dat uw machtigingen zijn ingesteld, of gebruik de `Credential` of `PSRunAsCredential` eigenschappen opgeven voor het account dat moet worden gebruikt.

## <a name="present-vs-absent"></a>Aanwezig vs. Absent

Elke DSC-resource voert verschillende bewerkingen op basis van de waarde die u opgeeft voor de `Ensure` eigenschap. De waarden die u opgeeft voor de bovenstaande eigenschappen bepaalt de status-bewerking is uitgevoerd.

### <a name="existence"></a>Bestaan

Wanneer u alleen opgeeft een `DestinationPath`, de bron zorgt ervoor dat het pad bestaat (`Present`) of bestaat niet (`Absent`).

### <a name="copy-operations"></a>Kopieerbewerkingen

Bij het opgeven van een `SourcePath` en een `DestinationPath` met een `Type` waarde van **Directory**, de bronmap resource-exemplaren naar het doelpad. De eigenschappen `Recurse`, `Force`, en `MatchSource` Wijzig het type van de kopieerbewerking uitgevoerd, terwijl `Credential` bepaalt welk account moet worden gebruikt voor toegang tot de bronmap.

### <a name="limitations"></a>Beperkingen

Als u een waarde van de opgegeven `ReadOnly` voor de `Attributes` eigenschap naast een `DestinationPath`, `Ensure = "Present"` maakt het pad dat is opgegeven, terwijl `Contents` stelt u de inhoud van het bestand.  Een `Absent` bewerking van de status wilt negeren de `Attributes` eigenschap volledig, en verwijderen van elk bestand in het opgegeven pad.

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld wordt een map en submappen van een pull-server naar een doelknooppunt met behulp van de Resource-bestand. Als de bewerking is geslaagd, schrijft de logboekresource een bevestigingsbericht wordt weergegeven in het gebeurtenislogboek.

De bronmap is een UNC-pad (`\\PullServer\DemoSource`) gedeeld van de Pull-Server. De `Recurse` eigenschap zorgt ervoor dat alle submappen ook worden gekopieerd.

> [!IMPORTANT]
> De LCM op de doel-knooppunt wordt uitgevoerd in de context van het lokale systeemaccount gebruikt standaard. Toegang verlenen tot de **bronpad**, het doelknooppunt computeraccount geschikte machtigingen geven. De **referentie** en **PSDSCRunAsCredential** (v5) beide wijzigen van de context de LCM gebruikt voor toegang tot de **bronpad**. U moet nog steeds toegang verlenen tot het account dat wordt gebruikt voor toegang tot de **bronpad**.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

Voor het gebruik van meer op **referenties** in DSC Zie [uitvoeren als gebruiker](../../../configurations/runAsUser.md) of [Config gegevens referenties](../../../configurations/configDataCredentials.md).
