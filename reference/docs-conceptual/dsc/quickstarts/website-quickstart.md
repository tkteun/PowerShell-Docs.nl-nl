---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: 'Quick Start: een website maken met DSC'
ms.openlocfilehash: 08ca25604998ce8c913ef8112b5342f2e0216b6e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75416134"
---
# <a name="quickstart---create-a-website-with-desired-state-configuration-dsc"></a>Quick Start: een website maken met desired state Configuration (DSC)

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

In deze oefening wordt uitgelegd hoe u een desired state Configuration (DSC)-configuratie kunt maken en Toep assen van het begin tot het einde.
In het voor beeld dat we gebruiken, zorgt u ervoor `Web-Server` dat de functie (IIS) is ingeschakeld op een server en dat de inhoud van een eenvoudige website ' Hallo wereld `inetpub\wwwroot` ' aanwezig is in de directory van die server.

Voor een overzicht van wat DSC is en hoe het werkt, raadpleegt [u overzicht van desired state Configuration voor besluit vormers](../overview/decisionMaker.md).

## <a name="requirements"></a>Vereisten

Als u dit voor beeld wilt uitvoeren, hebt u een computer met Windows Server 2012 of hoger en Power Shell 4,0 of hoger nodig.

## <a name="write-and-place-the-indexhtm-file"></a>Het bestand index. htm schrijven en plaatsen

Eerst maken we het HTML-bestand dat we als website-inhoud gaan gebruiken.

Maak in de hoofdmap een map met de naam `test`.

Typ de volgende tekst in een tekst editor:

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

Sla dit `index.htm` op in de `test` map die u eerder hebt gemaakt.

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

Sla het bestand op als `WebsiteTest.ps1`.

U ziet dat deze eruitziet als een Power shell-functie, met toevoeging van de trefwoord **configuratie** die wordt gebruikt voor de naam van de functie.

Het **knoop punt** blok geeft het doel knooppunt op dat moet worden geconfigureerd. In dit geval `localhost`.

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
Het resultaat is dat een nieuwe map met de `WebsiteTest` naam wordt gemaakt als een submap van de huidige map.
De `WebsiteTest` map bevat een bestand met `localhost.mof`de naam.
Dit is het bestand dat vervolgens kan worden toegepast op het doel knooppunt.

## <a name="apply-the-configuration"></a>De configuratie Toep assen

Nu u de gecompileerde MOF hebt, kunt u de configuratie Toep assen op het doel knooppunt (in dit geval de lokale computer) door de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aan te roepen.

De `Start-DscConfiguration` cmdlet vertelt de [lokale Configuration Manager (LCM)](../managing-nodes/metaConfig.md), de engine van DSC, om de configuratie toe te passen.
De LCM maakt het mogelijk om de DSC-resources aan te roepen om de configuratie toe te passen.

> [!NOTE]
> Om DSC te kunnen uitvoeren, moet Windows worden geconfigureerd voor het ontvangen van externe Power shell-opdrachten, zelfs wanneer u `localhost` een configuratie uitvoert. Als u uw omgeving eenvoudig op de juiste wijze `Set-WsManQuickConfig -Force` wilt configureren, voert u de opdracht uit in een Power shell-terminal met verhoogde bevoegdheden.

In een Power shell-console gaat u naar de map waar u de configuratie hebt opgeslagen en voert u de volgende opdracht uit:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>De configuratie testen

U kunt de cmdlet [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) aanroepen om te zien of de configuratie is geslaagd.

U kunt de resultaten ook rechtstreeks testen, in dit geval door te bladeren `http://localhost/` naar in een webbrowser.
U ziet de HTML-pagina ' Hallo wereld ' die u hebt gemaakt als de eerste stap in dit voor beeld.

## <a name="next-steps"></a>Volgende stappen

- Meer informatie over DSC-configuraties vindt u in [DSC-configuraties](../configurations/configurations.md).
- Bekijk welke DSC-resources beschikbaar zijn en hoe u aangepaste DSC-resources maakt op [DSC-resources](../resources/resources.md).
- DSC-configuraties en-resources zoeken in de [PowerShell Gallery](https://www.powershellgallery.com/).
