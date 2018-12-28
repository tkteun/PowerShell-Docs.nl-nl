---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: 'Snelstart: een website maken met DSC'
ms.openlocfilehash: c62e2d8af46bf74c4dd13069ddff6cc39763a209
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403888"
---
> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="quickstart---create-a-website-with-dsc"></a>Snelstart: een website maken met DSC

In deze oefening helpt bij het maken en toepassen van een Desired State Configuration (DSC)-configuratie van begin tot eind.
Het voorbeeld we gebruiken zorgt ervoor dat een server heeft de `Web-Server` (IIS)-functie ingeschakeld en dat de inhoud voor een eenvoudige 'Hallo wereld'-website is aanwezig in de `intepub\wwwroot` map van die server.

Zie voor een overzicht van wat DSC is en hoe het werkt, [overzicht van Desired State Configuration voor besluitvormers](../overview/decisionMaker.md).

## <a name="requirements"></a>Vereisten

Als u wilt uitvoeren in het volgende voorbeeld, moet u een computer met WindowsServer 2012 of later en PowerShell 4.0 of hoger.

## <a name="write-and-place-the-indexhtm-file"></a>Schrijven en plaats het bestand index.htm

Eerst gaan we de HTML-bestand dat wordt gebruikt als de website-inhoud maken.

Maak een map met de naam in de hoofdmap, `test`.

In een teksteditor, typt u de volgende tekst:

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

Opslaan als `index.htm` in de `test` map die u eerder hebt gemaakt.

## <a name="write-the-configuration"></a>Schrijven van de configuratie

Een [DSC-configuratie](../configurations/configurations.md) is een speciale PowerShell-functie die wordt gedefinieerd hoe u wilt configureren van een of meer doelcomputers (knooppunten).

In de PowerShell ISE, typ het volgende:

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

Sla het bestand op als `WebsiteTest.ps1`.

U kunt zien dat het ziet als een PowerShell-functie met de toevoeging van het sleutelwoord eruit **configuratie** gebruikt vóór de naam van de functie.

De **knooppunt** blok Hiermee geeft u het doelknooppunt moet worden geconfigureerd en in dit geval `localhost`.

De configuratie van de twee roept [resources](../resources/resources.md), **WindowsFeature** en **bestand**.
Resources doen het werk om ervoor te zorgen dat het doelknooppunt gedefinieerd door de configuratie van de status wordt.

## <a name="compile-the-configuration"></a>De configuratie compileren

Voor een DSC-configuratie moet worden toegepast op een knooppunt, moet dit eerst worden gecompileerd naar een MOF-bestand.
Om dit te doen, moet u de configuratie, zoals een functie uitvoeren.
Navigeer naar dezelfde map waar u uw configuratie hebt opgeslagen in een PowerShell-console en voer de volgende opdrachten voor het compileren van de configuratie naar een MOF-bestand:

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

Hiermee wordt de volgende uitvoer gegenereerd:

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

De eerste regel wordt de configuratie-functie beschikbaar in de console.
De tweede regel wordt de configuratie uitgevoerd.
Het resultaat is dat een nieuwe map met de naam `WebsiteTest` als een submap van de huidige map wordt gemaakt.
De `WebsiteTest` map bevat een bestand met de naam `localhost.mof`.
Het is in dit bestand die vervolgens kan worden toegepast op het doelknooppunt.

## <a name="apply-the-configuration"></a>De configuratie toepassen

Nu dat u het gecompileerde MOF hebt, kunt u de configuratie toepassen op het doelknooppunt (in dit geval de lokale computer) door het aanroepen van de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.

De `Start-DscConfiguration` cmdlet geeft de [lokale Configuration Manager (LCM)](../managing-nodes/metaConfig.md), dit is de engine van DSC, om toe te passen van de configuratie.
De LCM komt het werk van het aanroepen van de DSC-resources voor het toepassen van de configuratie.

Navigeer naar dezelfde map waar u uw configuratie hebt opgeslagen in een PowerShell-console en voer de volgende opdracht uit:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>De configuratie testen

U kunt aanroepen de [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet om te controleren of de configuratie is voltooid.

U kunt ook testen de resultaten rechtstreeks, in dit geval door te bladeren naar `http://localhost/` in een webbrowser.
Als de eerste stap in dit voorbeeld ziet u de "Hello World" HTML-pagina die u hebt gemaakt.

## <a name="next-steps"></a>Volgende stappen

- Meer informatie over DSC-configuraties op [DSC-configuraties](../configurations/configurations.md).
- Zie welke DSC-resources beschikbaar zijn en over het maken van aangepaste DSC-resources op [DSC-resources](../resources/resources.md).
- DSC-configuraties en resources in de [PowerShell Gallery](https://www.powershellgallery.com/).
