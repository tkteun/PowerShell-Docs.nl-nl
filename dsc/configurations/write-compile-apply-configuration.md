---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie, service, instellen
title: Schrijven en toepassen van een configuratie compileren
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403927"
---
> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>Schrijven en toepassen van een configuratie compileren

In deze oefening helpt bij het maken en toepassen van een Desired State Configuration (DSC)-configuratie van begin tot eind.
In het volgende voorbeeld leert u hoe u kunt schrijven en een zeer eenvoudige configuratie toe te passen. De configuratie zorgt ervoor dat een 'HelloWorld.txt'-bestand bestaat op uw lokale computer. Als u het bestand verwijdert, DSC wordt het opnieuw maken de volgende keer die wordt bijgewerkt.

Zie voor een overzicht van wat DSC is en hoe het werkt, [overzicht van Desired State Configuration voor ontwikkelaars](../overview/overview.md).

## <a name="requirements"></a>Vereisten

Als u wilt uitvoeren in het volgende voorbeeld, moet u een computer met PowerShell 4.0 of hoger.

## <a name="write-the-configuration"></a>Schrijven van de configuratie

Een DSC [configuratie](configurations.md) is een speciale PowerShell-functie die wordt gedefinieerd hoe u wilt configureren van een of meer doelcomputers (knooppunten).

In de PowerShell ISE, of een andere editor PowerShell, typ het volgende:

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

Sla het bestand als 'HelloWorld.ps1'.

Voor het definiëren van een configuratie is vergelijkbaar met het definiëren van een functie. De **knooppunt** blok Hiermee geeft u het doelknooppunt moet worden geconfigureerd en in dit geval `localhost`.

De configuratie van de roept een [resources](../resources/resources.md), wordt de `File` resource. Resources doen het werk om ervoor te zorgen dat het doelknooppunt gedefinieerd door de configuratie van de status wordt.

## <a name="compile-the-configuration"></a>De configuratie compileren

Voor een DSC-configuratie moet worden toegepast op een knooppunt, moet dit eerst worden gecompileerd naar een MOF-bestand.
Uitvoeren van de configuratie, zoals een functie, wordt één ".mof" bestand gecompileerd voor elk knooppunt dat is gedefinieerd door de `Node` blokkeren.
Als u wilt uitvoeren van de configuratie, moet u *stip bron* uw script 'HelloWorld.ps1' in het huidige bereik.
Zie voor meer informatie, [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).

*Punt bron* uw script 'HelloWorld.ps1' door te typen in het pad waar u deze nadat opgeslagen de `. ` (punt, spatie). Vervolgens kunt u uw configuratie uitvoeren door deze als een functie aan te roepen.

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

Hiermee wordt de volgende uitvoer gegenereerd:

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>De configuratie toepassen

Nu dat u het gecompileerde MOF hebt, kunt u de configuratie toepassen op het doelknooppunt (in dit geval de lokale computer) door het aanroepen van de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.

De `Start-DscConfiguration` cmdlet geeft de [lokale Configuration Manager (LCM)](../managing-nodes/metaConfig.md), de DSC, om toe te passen van de configuratie-engine.
De LCM komt het werk van het aanroepen van de DSC-resources voor het toepassen van de configuratie.

De onderstaande code gebruiken om uit te voeren de `Start-DSCConfiguration` cmdlet. Geef het pad waar uw "localhost.mof" is opgeslagen op de `-Path` parameter. De `Start-DSCConfiguration` cmdlet gezocht in de map die is opgegeven voor een '\<computername\>.mof "bestanden. De `Start-DSCConfiguration` cmdlet probeert toe te passen van elk ".mof" bestand gevonden op de computernaam die is opgegeven door de bestandsnaam ("localhost", "server01", "dc-02", enzovoort).

> [!NOTE]
> Als de `-Wait` parameter niet wordt opgegeven, `Start-DSCConfiguration` maakt u een achtergrondtaak als de bewerking wilt uitvoeren. Op te geven de `-Verbose` parameter kunt u bekijken de **uitgebreid** uitvoer van de bewerking. `-Wait`, en `-Verbose` beide parameters zijn optioneel.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>De configuratie testen

Zodra de `Start-DSCConfiguration` cmdlet is voltooid, ziet u een bestand 'HelloWorld.txt' in de opgegeven locatie. U kunt controleren of de inhoud met de [Get-inhoud](/powershell/module/microsoft.powershell.management/get-content) cmdlet.

U kunt ook *testen* de huidige status via [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

De uitvoer moet 'True' als het knooppunt momenteel compatibel is met de toegepaste configuratie.

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a>De configuratie toepassen opnieuw

Als u wilt zien van uw configuratie opnieuw toegepast, kunt u het tekstbestand dat is gemaakt door uw configuratie verwijderen. Gebruik de `Start-DSCConfiguration` cmdlet met de `-UseExisting` parameter. De `-UseExisting` parameter geeft de opdracht `Start-DSCConfiguration` om toe te passen opnieuw het bestand 'current.mof', die het meest recent zijn vertegenwoordigt configuratie toegepast.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Volgende stappen

- Meer informatie over DSC-configuraties op [DSC-configuraties](configurations.md).
- Zie welke DSC-resources beschikbaar zijn en over het maken van aangepaste DSC-resources op [DSC-resources](../resources/resources.md).
- DSC-configuraties en resources in de [PowerShell Gallery](https://www.powershellgallery.com/).
