---
ms.date: 06/22/2020
keywords: DSC, Power shell, configuratie, service, installatie
title: Een configuratie schrijven, compileren en toepassen
description: In deze oefening wordt het maken en Toep assen van een DSC-configuratie van begin tot eind door lopen. In het volgende voor beeld wordt uitgelegd hoe u een eenvoudige configuratie kunt schrijven en Toep assen
ms.openlocfilehash: f173fe0dc6cd73e2b49bb8c44a9ee1a53eab475f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645038"
---
# <a name="write-compile-and-apply-a-configuration"></a>Een configuratie schrijven, compileren en toepassen

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

In deze oefening wordt uitgelegd hoe u een desired state Configuration (DSC)-configuratie kunt maken en Toep assen van het begin tot het einde. In het volgende voor beeld wordt uitgelegd hoe u een eenvoudige configuratie kunt schrijven en Toep assen. De configuratie zorgt ervoor dat het bestand ' HelloWorld.txt ' bestaat op uw lokale computer.
Als u het bestand verwijdert, maakt DSC de volgende keer dat het wordt bijgewerkt opnieuw.

Voor een overzicht van wat DSC is en hoe het werkt, raadpleegt u [overzicht van desired state Configuration voor ontwikkel aars](../overview/overview.md).

## <a name="requirements"></a>Vereisten

Als u dit voor beeld wilt uitvoeren, hebt u een computer nodig waarop Power Shell 4,0 of hoger wordt uitgevoerd.

## <a name="write-the-configuration"></a>De configuratie schrijven

Een DSC- [configuratie](configurations.md) is een speciale Power shell-functie die definieert hoe u een of meer doel computers (knoop punten) wilt configureren.

In Power shell ISE of een andere Power shell-editor typt u het volgende:

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when
    # this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a
        # source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

> [!IMPORTANT]
> In meer geavanceerde scenario's waarin meerdere modules moeten worden geïmporteerd zodat u met een groot aantal DSC-resources in dezelfde configuratie kunt werken, moet u ervoor zorgen dat elke module op een aparte regel wordt geplaatst met `Import-DscResource` . Dit is eenvoudiger te onderhouden in broncode beheer en is vereist bij het werken met DSC in azure-status configuratie.
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

Sla het bestand op als "HelloWorld.ps1".

Het definiëren van een configuratie is vergelijkbaar met het definiëren van een functie. Het **knoop punt** blok geeft het doel knooppunt op dat moet worden geconfigureerd. in dit geval `localhost` .

De configuratie roept één [resources](../resources/resources.md)aan, de `File` resource. Resources maken het werk om ervoor te zorgen dat het doel knooppunt zich in de status bevindt die door de configuratie is gedefinieerd.

## <a name="compile-the-configuration"></a>De configuratie compileren

Een DSC-configuratie die wordt toegepast op een knoop punt, moet eerst worden gecompileerd in een MOF-bestand. Het uitvoeren van de configuratie, zoals een functie, compileert één `.mof` bestand voor elk knoop punt dat door het blok wordt gedefinieerd `Node` . Als u de configuratie wilt uitvoeren, moet u de _bron_ van uw `HelloWorld.ps1` script naar het huidige bereik gaan. Zie [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts#script-scope-and-dot-sourcing)voor meer informatie.

<!-- markdownlint-disable MD038 -->
_Punt_ de bron `HelloWorld.ps1` van uw script door het pad te typen waar u het hebt opgeslagen, na de `. ` (punt, spatie). U kunt vervolgens uw configuratie uitvoeren door deze als een functie aan te roepen. U kunt ook de configuratie functie onder aan het script aanroepen, zodat u niet hoeft te stip-bron.
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

Hiermee wordt de volgende uitvoer gegenereerd:

```Output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>De configuratie toepassen

Nu u de gecompileerde MOF hebt, kunt u de configuratie Toep assen op het doel knooppunt (in dit geval de lokale computer) door de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aan te roepen.

De `Start-DscConfiguration` cmdlet vertelt de [lokale Configuration Manager (LCM)](../managing-nodes/metaConfig.md), de engine van DSC, om de configuratie toe te passen. De LCM maakt het mogelijk om de DSC-resources aan te roepen om de configuratie toe te passen.

Gebruik de onderstaande code om de cmdlet uit te voeren `Start-DSCConfiguration` . Geef het mappad op waar uw `localhost.mof` wordt opgeslagen in de para meter **Path** . De `Start-DSCConfiguration` cmdlet zoekt naar de map die is opgegeven voor `<computername>.mof` bestanden. De `Start-DSCConfiguration` cmdlet probeert elk `.mof` gevonden bestand toe te passen op het `computername` opgegeven door de bestands naam (' localhost ', ' Server01 ', ' DC-02 ', enzovoort).

> [!NOTE]
> Als de `-Wait` para meter niet wordt opgegeven, `Start-DSCConfiguration` maakt een achtergrond taak om de bewerking uit te voeren. Door de `-Verbose` para meter op te geven, kunt u de **uitgebreide** uitvoer van de bewerking bekijken. `-Wait`en `-Verbose` zijn beide optionele para meters.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>De configuratie testen

Zodra de `Start-DSCConfiguration` cmdlet is voltooid, ziet u een `HelloWorld.txt` bestand op de locatie die u hebt opgegeven. U kunt de inhoud controleren met de cmdlet [Get-content](/powershell/module/microsoft.powershell.management/get-content) .

U kunt ook de huidige status _testen_ met [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

De uitvoer moet zijn `True` als het knoop punt momenteel compatibel is met de toegepaste configuratie.

```powershell
Test-DSCConfiguration
```

```Output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```Output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a>De configuratie opnieuw Toep assen

Als u wilt zien hoe de configuratie Get opnieuw wordt toegepast, kunt u het tekst bestand verwijderen dat door uw configuratie is gemaakt. De cmdlet gebruiken `Start-DSCConfiguration` met de `-UseExisting` para meter. De `-UseExisting` para meter geeft `Start-DSCConfiguration` aan dat het huidige. MOF-bestand opnieuw moet worden toegepast. Dit is de meest recent toegepaste configuratie.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Volgende stappen

- Meer informatie over DSC-configuraties vindt u in [DSC-configuraties](configurations.md).
- Bekijk welke DSC-resources beschikbaar zijn en hoe u aangepaste DSC-resources maakt op [DSC-resources](../resources/resources.md).
- DSC-configuraties en-resources zoeken in de [PowerShell Gallery](https://www.powershellgallery.com/).
