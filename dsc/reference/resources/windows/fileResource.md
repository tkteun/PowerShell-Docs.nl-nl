---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC-Bestandsresource
ms.openlocfilehash: e5f7a91e5f19c8c7bbada090804d8f29a7cfedd5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048314"
---
# <a name="dsc-file-resource"></a>DSC-Bestandsresource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De resource van het bestand in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van bestanden en mappen op het doelknooppunt.

>**Opmerking:** Als de **MatchSource** eigenschap is ingesteld op **$false** (dit is de standaardwaarde), de inhoud wordt gekopieerd in de cache opgeslagen de eerste keer dat de configuratie is toegepast.
>Volgende aanvragen van de configuratie wordt niet gecontroleerd op bijgewerkte bestanden en/of mappen in het pad dat is opgegeven door **bronpad**. Als u wilt controleren op updates voor de bestanden en/of mappen in **bronpad** telkens wanneer de configuratie is toegepast, stel **MatchSource** naar **$true**.

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

|  Eigenschap  |  Beschrijving   |
|---|---|
| DestinationPath| Geeft de locatie waar u om te controleren of de status van een bestand of map.|
| Kenmerken| Hiermee geeft u de gewenste status van de kenmerken voor het betreffende bestand of map.|
| Controlesom| Geeft het type controlesom te gebruiken bij het bepalen of twee bestanden hetzelfde zijn. Als __controlesom__ niet is opgegeven, alleen de naam van bestand of map wordt gebruikt voor de vergelijking. Geldige waarden zijn: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.|
| Inhoud| Hiermee geeft u de inhoud van een bestand, zoals een bepaalde tekenreeks.|
| Referentie| Geeft aan dat de referenties die vereist voor toegang tot resources, zoals de bronbestanden bevat zijn, als deze toegang vereist is.|
| Zorg ervoor dat| Geeft aan of het bestand of map bestaat. Deze eigenschap instellen op 'Ontbreekt' om ervoor te zorgen dat het bestand of map niet bestaat. Stel deze in op 'Aanwezig' om ervoor te zorgen dat het bestand of map bestaat. De standaardwaarde is 'Aanwezig'.|
| Force| Bepaalde bestandsbewerkingen (zoals een bestand te overschrijven of verwijderen van een directory die is niet leeg), een fout leidt. Met behulp van de Force-eigenschap heeft voorrang op dergelijke fouten. De standaardwaarde is __$false__.|
| Recurse| Hiermee wordt aangegeven als submappen opgenomen worden. Deze eigenschap instellen op __$true__ om aan te geven dat u wilt dat de submappen moeten worden opgenomen. De standaardwaarde is __$false__. **Houd er rekening mee**: Deze eigenschap is alleen geldig wanneer de eigenschap Type is ingesteld op de Directory.|
| DependsOn | Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|
| Bronpad| Geeft het pad van waaruit de resource van het bestand of map kopiëren.|
| Type| Geeft aan of de resource wordt geconfigureerd een map of een bestand is. Deze eigenschap instellen op 'Directory' om aan te geven dat de resource een map is. Stel deze in op 'File' om aan te geven dat de resource een bestand is. De standaardwaarde is 'File'.|
| MatchSource| Indien ingesteld op de standaardwaarde van __$false__, en vervolgens alle bestanden op de bron (bijvoorbeeld bestanden A, B en C) wordt toegevoegd aan het doel de eerste keer dat de configuratie is toegepast. Als een nieuw bestand (D) is toegevoegd aan de bron, wordt deze niet toegevoegd aan de bestemming, zelfs wanneer de configuratie wordt later opnieuw toegepast. Als de waarde __$true__, en vervolgens elke keer dat de configuratie is toegepast, nieuwe bestanden vervolgens gevonden op de bron (zoals bestand D in dit voorbeeld) worden toegevoegd aan de bestemming. De standaardwaarde is **$false**.|

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet u hoe u de resource van het bestand om ervoor te zorgen dat een map met het pad `C:\Users\Public\Documents\DSCDemo\DemoSource` op een computer (zoals de server 'pull') is ook aanwezig zijn (samen met alle submappen) op het doelknooppunt. Ook een bevestiging bericht wordt geschreven naar het logboek voor als u klaar bent en bevat een instructie om ervoor te zorgen dat de bestandscontrole bewerking wordt uitgevoerd voordat de bewerking voor logboekregistratie.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```