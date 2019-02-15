---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Quick Start - maken van een website met DSC
ms.openlocfilehash: d98607939ccd3cc5e660936d8c0a6d54fce7d65f
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265481"
---
> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="quickstart---create-a-website-with-dsc"></a>Quick Start - maken van een website met DSC

In deze oefening helpt bij het maken en toepassen van een configuratie Desired State Configuration (DSC) van begin tot eind.
In het voorbeeld we gebruiken zorgt ervoor dat een server heeft de `Web-Server` (IIS)-functie ingeschakeld en de inhoud voor een eenvoudige 'Hallo wereld'-website is aanwezig in de `inetpub\wwwroot` map van die server.

Zie voor een overzicht van DSC en hoe het werkt [Desired Configuration overzicht voor besluitvormers](../overview/decisionMaker.md).

## <a name="requirements"></a>Vereisten

U voert dit voorbeeld, moet u een computer met WindowsServer 2012 of later en PowerShell 4.0 of hoger.

## <a name="write-and-place-the-indexhtm-file"></a>Schrijven en plaats het bestand index.htm

Eerst maakt de HTML-bestand dat wordt gebruikt als de inhoud van de website.

Maak een map met de naam in de hoofdmap, `test`.

Typ de volgende tekst in een teksteditor:

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

Opslaan als `index.htm` in de `test` map die u eerder hebt gemaakt.

## <a name="write-the-configuration"></a>Schrijven van de configuratie

Een [DSC-configuratie](../configurations/configurations.md) is een speciale PowerShell-functie die hoe u aangeeft een of meer doelcomputers (knooppunten) configureren.

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

Sla het bestand als `WebsiteTest.ps1`.

U kunt zien dat het lijkt erop dat een functie PowerShell met de toevoeging van het sleutelwoord **configuratie** gebruikt vóór de naam van de functie.

De **knooppunt** blok Hiermee geeft u het doelknooppunt te configureren in dit geval `localhost`.

De configuratie van de twee roept [resources](../resources/resources.md), **WindowsFeature** en **bestand**.
Resources doen het werk om ervoor te zorgen dat het doelknooppunt de status is gedefinieerd door de configuratie heeft.

## <a name="compile-the-configuration"></a>De configuratie compileren

Voor een DSC-configuratie op een knooppunt moet worden toegepast, moet deze eerst worden gecompileerd naar een MOF-bestand.
Om dit te doen, moet u de configuratie zoals een functie uitvoeren.
Navigeer naar dezelfde map waarin u de configuratie hebt opgeslagen in een PowerShell-console en voer de volgende opdrachten voor het compileren van de configuratie naar een MOF-bestand:

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
De tweede regel wordt uitgevoerd voor de configuratie.
Het resultaat is dat er een nieuwe map met de naam `WebsiteTest` gemaakt als een submap van de huidige map.
De `WebsiteTest` map bevat een bestand met de naam `localhost.mof`.
Het is dit bestand die vervolgens kan worden toegepast op het doelknooppunt.

## <a name="apply-the-configuration"></a>De configuratie toepassen

Nu dat u de gecompileerde MOF hebt, kunt u de configuratie toepassen op het doelknooppunt (in dit geval de lokale computer) door het aanroepen van de [Start DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.

De `Start-DscConfiguration` cmdlet vertelt de [lokale Configuration Manager (LCM)](../managing-nodes/metaConfig.md), dit is de engine van DSC toepassen van de configuratie.
De LCM komt het werk van het aanroepen van de DSC-resources als de configuratie wilt toepassen.

Navigeer naar dezelfde map waarin u de configuratie hebt opgeslagen in een PowerShell-console en voer de volgende opdracht:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>Test de configuratie

U kunt aanroepen de [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet om te controleren of de configuratie is voltooid.

U kunt ook de resultaten testen rechtstreeks in dit geval door te bladeren naar `http://localhost/` in een webbrowser.
Als de eerste stap in dit voorbeeld ziet u de 'Hallo wereld' HTML-pagina die u hebt gemaakt.

## <a name="next-steps"></a>Volgende stappen

- Meer informatie over DSC-configuraties op [DSC-configuraties](../configurations/configurations.md).
- Zie wat DSC-resources beschikbaar zijn en het maken van aangepaste DSC-resources op [DSC-resources](../resources/resources.md).
- DSC-configuraties en resources in de [PowerShell Gallery](https://www.powershellgallery.com/).
