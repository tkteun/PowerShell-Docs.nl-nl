---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-bestands resource
ms.openlocfilehash: 4c6945d4cdcbc64ac6d52db563823efe8fd0247e
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324502"
---
# <a name="dsc-file-resource"></a>DSC-bestands resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x

De bron van het **bestand** in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het beheren van bestanden en mappen op het doel knooppunt. **Doelpad** en **bronpad** moeten beide toegankelijk zijn voor het doel knooppunt.

## <a name="syntax"></a>Syntaxis

```Syntax
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>properties

|Eigenschap |Description |
|---|---|
|DestinationPath |De locatie, op het doel knooppunt, wilt **ervoor zorgen dat** **deze aanwezig** is of **ontbreekt** . |
|Kenmerken |De gewenste status van de kenmerken voor het betreffende bestand of de doel directory. Geldige waarden zijn _Archief_, _verborgen_, _alleen-lezen_en _systeem_. |
|Controlesom |Het type controlesom dat moet worden gebruikt om te bepalen of twee bestanden hetzelfde zijn. Geldige waarden zijn: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**. |
|Inhoud |Alleen geldig als deze wordt gebruikt met het **type** **bestand**. Hiermee wordt **aangegeven dat de** inhoud **aanwezig** is of **ontbreekt** in het doel bestand. |
|Referentie |De referenties die nodig zijn voor toegang tot bronnen, zoals bron bestanden. |
|Force |Onderdrukt de toegangs bewerkingen die resulteren in een fout (bijvoorbeeld het overschrijven van een bestand of het verwijderen van een niet-lege map). De standaard waarde `$false`is. |
|Recurse |Alleen geldig als deze wordt gebruikt met het **type** **Directory**. Voert de status bewerking recursief uit op alle submappen. De standaard waarde `$false`is. |
|Bronpad |Het pad waaruit de bron van het bestand of de map moet worden gekopieerd. |
|type |Het type resource dat wordt geconfigureerd. Geldige waarden zijn **map** en **bestand**. De standaard waarde is een **bestand**. |
|MatchSource |Hiermee wordt bepaald of de resource moet controleren op nieuwe bestanden die worden toegevoegd aan de bron directory na de eerste kopie. Een waarde van `$true` geeft aan dat na de eerste kopie nieuwe bron bestanden moeten worden gekopieerd naar de bestemming. Als deze is `$false`ingesteld op, wordt de inhoud van de bronmap in cache opgeslagen en worden alle bestanden die na de eerste kopie worden toegevoegd, genegeerd. De standaard waarde `$false`is. |

> [!WARNING]
> Als u geen waarde opgeeft voor **referentie** -of **PSRunAsCredential**, gebruikt de resource het computer account van het doel knooppunt om toegang te krijgen tot het **bronpad**. Wanneer het **bronpad** een UNC-share is, kan dit resulteren in een fout ' toegang geweigerd '. Zorg ervoor dat uw machtigingen dienovereenkomstig zijn ingesteld, of gebruik de eigenschappen **Credential** of **PSRunAsCredential** om het account op te geven dat moet worden gebruikt.

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Description |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is. |
|Zo |Hiermee wordt bepaald of het bestand en de **inhoud** op de **bestemming** bestaan of niet. Stel deze eigenschap in op **presen teren** om te controleren of het bestand bestaat. Stel deze in op **afwezig** om ervoor te zorgen dat ze niet bestaan. De standaard waarde is **aanwezig**. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

### <a name="additional-information"></a>Aanvullende informatie

- Wanneer u alleen een **doelpad**opgeeft, zorgt de bron ervoor dat het pad bestaat, indien het **aanwezig** is of niet bestaat als het **ontbreekt**.
- Wanneer u een **bronpad** en een **doelpad** met de **type** waarde **Directory**opgeeft, wordt de bron Directory gekopieerd naar het doelpad. Met de **Eigenschappen wordt**het type Kopieer bewerking dat wordt uitgevoerd, gewijzigd, **geforceerd**en **MatchSource** , terwijl de **referentie** bepaalt welk account moet worden gebruikt om toegang te krijgen tot de bron directory.
- Als u voor de eigenschap **Attributes** naast een **doelpad**de waarde **ReadOnly** hebt opgegeven **, moet u** **ervoor zorgen dat** het opgegeven pad wordt gemaakt, terwijl de **inhoud** van het bestand is ingesteld. Als u **ervoor zorgt dat** de instelling niet **aanwezig** is, wordt de eigenschap **Attributes** volledig genegeerd en worden alle bestanden verwijderd uit het opgegeven pad.

## <a name="example"></a>Voorbeeld

In het volgende voor beeld wordt een map en de bijbehorende submappen gekopieerd van een pull-server naar een doel knooppunt met behulp van de bestands resource. Als de bewerking is geslaagd, schrijft de logboek bron een bevestigings bericht naar het gebeurtenis logboek.

De bron directory is een UNC-pad`\\PullServer\DemoSource`() dat wordt gedeeld vanaf de pull-server. Met de **recursieve** eigenschap zorgt u ervoor dat alle submappen ook worden gekopieerd.

> [!IMPORTANT]
> De LCM op het doel knooppunt wordt standaard uitgevoerd in de context van het lokale systeem account. Als u toegang wilt verlenen tot het **bronpad**, geeft u het computer account van het doel knooppunt de juiste machtigingen. De **referentie** -en **PSDSCRunAsCredential** wijzigen de context die de LCM gebruikt om toegang te krijgen tot het **bronpad**. U moet nog steeds toegang verlenen tot het account dat wordt gebruikt voor toegang tot het **bronpad**.

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

Zie [uitvoeren als gebruiker](../../../configurations/runAsUser.md) of [configuratie gegevens referenties](../../../configurations/configDataCredentials.md)voor meer informatie over het gebruik van **referenties** in DSC.