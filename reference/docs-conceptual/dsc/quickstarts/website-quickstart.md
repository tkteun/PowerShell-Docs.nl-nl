---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: 'Quick Start: een website maken met DSC'
ms.openlocfilehash: d98607939ccd3cc5e660936d8c0a6d54fce7d65f
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942725"
---
> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

# <a name="quickstart---create-a-website-with-dsc"></a>Quick Start: een website maken met DSC

In deze oefening wordt uitgelegd hoe u een desired state Configuration (DSC)-configuratie kunt maken en Toep assen van het begin tot het einde.
In het voor beeld dat we gebruiken, zorgt u ervoor dat de functie `Web-Server` (IIS) is ingeschakeld op een server en dat de inhoud voor een eenvoudige website ' Hallo wereld ' aanwezig is in de map `inetpub\wwwroot` van die server.

Voor een overzicht van wat DSC is en hoe het werkt, raadpleegt [u overzicht van desired state Configuration voor besluit vormers](../overview/decisionMaker.md).

## <a name="requirements"></a>Vereisten

Als u dit voor beeld wilt uitvoeren, hebt u een computer met Windows Server 2012 of hoger en Power Shell 4,0 of hoger nodig.

## <a name="write-and-place-the-indexhtm-file"></a>Het bestand index. htm schrijven en plaatsen

Eerst maken we het HTML-bestand dat we als website-inhoud gaan gebruiken.

Maak een map met de naam `test` in de hoofdmap.

Typ de volgende tekst in een tekst editor:

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

Sla dit op als `index.htm` in de `test`-map die u eerder hebt gemaakt.

## <a name="write-the-configuration"></a>De configuratie schrijven

Een [DSC-configuratie](../configurations/configurations.md) is een speciale Power shell-functie die definieert hoe u een of meer doel computers (knoop punten) wilt configureren.

Typ het volgende in het Power shell-ISE:

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

Sla het bestand op `WebsiteTest.ps1`als.

U ziet dat deze eruitziet als een Power shell-functie, met toevoeging van de trefwoord **configuratie** die wordt gebruikt voor de naam van de functie.

Het **knoop punt** blok geeft het doel knooppunt op dat moet worden geconfigureerd. `localhost`in dit geval.

De configuratie roept twee [resources](../resources/resources.md), **WindowsFeature** en **File**aan.
Resources maken het werk om ervoor te zorgen dat het doel knooppunt zich in de status bevindt die door de configuratie is gedefinieerd.

## <a name="compile-the-configuration"></a>De configuratie compileren

Een DSC-configuratie die wordt toegepast op een knoop punt, moet eerst worden gecompileerd in een MOF-bestand.
Hiervoor voert u de configuratie uit, zoals een functie.
In een Power shell-console gaat u naar de map waar u de configuratie hebt opgeslagen en voert u de volgende opdrachten uit om de configuratie in een MOF-bestand te compileren:

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

De eerste regel maakt de configuratie functie beschikbaar in de-console.
De tweede regel voert de configuratie uit.
Het resultaat is dat een nieuwe map met de naam `WebsiteTest` wordt gemaakt als een submap van de huidige map.
De map @no__t 0 bevat een bestand met de naam `localhost.mof`.
Dit bestand kan vervolgens worden toegepast op het doel knooppunt.

## <a name="apply-the-configuration"></a>De configuratie Toep assen

Nu u de gecompileerde MOF hebt, kunt u de configuratie Toep assen op het doel knooppunt (in dit geval de lokale computer) door de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aan te roepen.

De cmdlet `Start-DscConfiguration` vertelt de [lokale Configuration Manager (LCM)](../managing-nodes/metaConfig.md), de engine van DSC, om de configuratie toe te passen.
De LCM maakt het mogelijk om de DSC-resources aan te roepen om de configuratie toe te passen.

In een Power shell-console gaat u naar de map waar u de configuratie hebt opgeslagen en voert u de volgende opdracht uit:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>De configuratie testen

U kunt de cmdlet [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) aanroepen om te zien of de configuratie is geslaagd.

U kunt de resultaten ook rechtstreeks testen, in dit geval door te bladeren naar `http://localhost/` in een webbrowser.
U ziet de HTML-pagina ' Hallo wereld ' die u hebt gemaakt als de eerste stap in dit voor beeld.

## <a name="next-steps"></a>Volgende stappen

- Meer informatie over DSC-configuraties vindt u in [DSC-configuraties](../configurations/configurations.md).
- Bekijk welke DSC-resources beschikbaar zijn en hoe u aangepaste DSC-resources maakt op [DSC-resources](../resources/resources.md).
- DSC-configuraties en-resources zoeken in de [PowerShell Gallery](https://www.powershellgallery.com/).
