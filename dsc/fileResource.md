---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-bestandsbron
ms.openlocfilehash: 54d01bf0769eeed0354606eb3543973b0f850a6f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-file-resource"></a>DSC-bestandsbron

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De bron van het bestand in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van bestanden en mappen op het doelknooppunt.

>**Opmerking:** als de **MatchSource** eigenschap is ingesteld op **$false** (dit is de standaardwaarde), de inhoud te kopiëren de eerste keer dat de configuratie is toegepast in cache zijn opgeslagen. 
>Volgende aanvragen van de configuratie wordt niet gecontroleerd op bijgewerkte bestanden en/of mappen in het pad dat is opgegeven door **bronpad**. Als u wilt controleren op updates voor de bestanden en/of mappen in **bronpad** ingesteld telkens wanneer de configuratie is toegepast, **MatchSource** naar **$true**. 

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
| DestinationPath| Geeft de locatie waar u Zorg ervoor dat de status voor een bestand of map.| 
| Kenmerken| Hiermee geeft u de gewenste status van de kenmerken voor het betreffende bestand of map.| 
| Controlesom| Geeft het type controlesom kunt bepalen of twee bestanden hetzelfde zijn. Als __controlesom__ niet is opgegeven, alleen de naam van bestand of map wordt gebruikt voor vergelijking. Geldige waarden zijn: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.| 
| Inhoud| Hiermee geeft u de inhoud van een bestand, zoals een bepaalde tekenreeks.| 
| referentie| Geeft de referenties die vereist voor toegang tot bronnen, zoals de bronbestanden bevat zijn, of deze toegang vereist is.| 
| Zorg ervoor dat| Hiermee wordt aangegeven of het bestand of map bestaat. Deze eigenschap instellen op 'Ontbreekt' om ervoor te zorgen dat het bestand of map niet bestaat. Stel deze in op 'Aanwezig' om ervoor te zorgen dat het bestand of map bestaat. De standaardwaarde is 'Aanwezig'.| 
| Force| Bepaalde bestandsbewerkingen (zoals een bestand te overschrijven of verwijderen van een map die is niet leeg) leidt tot een fout opgetreden. Met de eigenschap Force, overschrijft dergelijke fouten. De standaardwaarde is __$false__.| 
| Recurse| Hiermee wordt aangegeven als submappen opgenomen worden. Deze eigenschap instellen op __$true__ om aan te geven dat u wilt dat de submappen worden opgenomen. De standaardwaarde is __$false__. **Opmerking**: deze eigenschap is alleen geldig wanneer de eigenschap Type is ingesteld op de Directory.| 
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.| 
| SourcePath| Geeft het pad van waaruit de bron van het bestand of map kopiëren.| 
| Type| Hiermee wordt aangegeven of de resource die wordt geconfigureerd een map of een bestand is. Deze eigenschap instellen op 'Map' om aan te geven dat de resource een map is. Stel deze in op 'File' om aan te geven dat de resource een bestand is. De standaardwaarde is 'File'.| 
| MatchSource| Indien ingesteld op de standaardwaarde van __$false__, en vervolgens alle bestanden op de bron (bijvoorbeeld bestanden A, B en C) wordt toegevoegd aan het doel de eerste keer dat de configuratie is toegepast. Als een nieuw bestand (D) wordt toegevoegd aan de bron, het niet toegevoegd aan de bestemming, zelfs wanneer de configuratie wordt later opnieuw toegepast. Als de waarde __$true__, en vervolgens elke keer dat de configuratie is toegepast, nieuwe bestanden vervolgens gevonden op de bron (zoals bestand D in dit voorbeeld) worden toegevoegd aan de bestemming. De standaardwaarde is **$false**.| 

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld ziet u hoe u de bron van het bestand gebruikt om ervoor te zorgen dat een map met het pad `C:\Users\Public\Documents\DSCDemo\DemoSource` in een bron computer (zoals de server 'pull') is ook aanwezig zijn (samen met alle submappen) in het doelknooppunt. Ook een bevestiging bericht schrijft naar het logboek na afloop en bevat een instructie om ervoor te zorgen dat de bestandscontrole bewerking wordt uitgevoerd voordat de bewerking voor logboekregistratie.

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

