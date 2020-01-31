---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, service, installatie
title: Een configuratie schrijven, compileren en toepassen
ms.openlocfilehash: eb61e518762b9f13e617ecd4711bfef7a86814ec
ms.sourcegitcommit: ea7d87a7a56f368e3175219686dfa2870053c644
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818155"
---
> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

# <a name="write-compile-and-apply-a-configuration"></a>Een configuratie schrijven, compileren en toepassen

In deze oefening wordt uitgelegd hoe u een desired state Configuration (DSC)-configuratie kunt maken en Toep assen van het begin tot het einde.
In het volgende voor beeld wordt uitgelegd hoe u een eenvoudige configuratie kunt schrijven en Toep assen. De configuratie zorgt ervoor dat het bestand HelloWorld. txt bestaat op de lokale computer. Als u het bestand verwijdert, maakt DSC de volgende keer dat het wordt bijgewerkt opnieuw.

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

> ! Belang rijk in meer geavanceerde scenario's waarbij meerdere modules moeten worden geïmporteerd zodat u met een groot aantal DSC-resources in dezelfde configuratie kunt werken, moet u ervoor zorgen dat elke module op een aparte regel wordt geplaatst met behulp van `Import-DscResource`.
> Dit is eenvoudiger te onderhouden in broncode beheer en is vereist bij het werken met DSC in azure-status configuratie.
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

Sla het bestand op als ' HelloWorld. ps1 '.

Het definiëren van een configuratie is vergelijkbaar met het definiëren van een functie. Het **knoop punt** blok geeft het doel knooppunt op dat moet worden geconfigureerd. in dit geval `localhost`.

De configuratie roept één [resources](../resources/resources.md), de `File` resource. Resources maken het werk om ervoor te zorgen dat het doel knooppunt zich in de status bevindt die door de configuratie is gedefinieerd.

## <a name="compile-the-configuration"></a>De configuratie compileren

Een DSC-configuratie die wordt toegepast op een knoop punt, moet eerst worden gecompileerd in een MOF-bestand.
Als u de configuratie uitvoert, zoals een functie, wordt een '. MOF-bestand ' gecompileerd voor elk knoop punt dat is gedefinieerd door het `Node` blok.
Als u de configuratie wilt uitvoeren, moet *u het script* ' HelloWorld. ps1 ' in het huidige bereik.
Zie [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing)voor meer informatie.

<!-- markdownlint-disable MD038 -->
*Stip* het script ' HelloWorld. ps1 ' door te typen in het pad waar u het hebt opgeslagen, na de `. ` (punt, spatie). U kunt vervolgens uw configuratie uitvoeren door deze als een functie aan te roepen.
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

Hiermee wordt de volgende uitvoer gegenereerd:

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>De configuratie Toep assen

Nu u de gecompileerde MOF hebt, kunt u de configuratie Toep assen op het doel knooppunt (in dit geval de lokale computer) door de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aan te roepen.

De cmdlet `Start-DscConfiguration` vertelt de [lokale Configuration Manager (LCM)](../managing-nodes/metaConfig.md), de engine van DSC, om de configuratie toe te passen.
De LCM maakt het mogelijk om de DSC-resources aan te roepen om de configuratie toe te passen.

Gebruik de onderstaande code om de cmdlet `Start-DSCConfiguration` uit te voeren. Geef het mappad op waar uw ' localhost. mof ' wordt opgeslagen in de para meter `-Path`. De `Start-DSCConfiguration`-cmdlet zoekt naar de map die is opgegeven voor de bestanden\<ComputerName\>. mof. De `Start-DSCConfiguration`-cmdlet probeert elk bestand '. mof ' toe te passen op de computer naam die is opgegeven door de filename (' localhost ', ' Server01 ', ' DC-02 ', enzovoort).

> [!NOTE]
> Als de para meter `-Wait` niet is opgegeven, maakt `Start-DSCConfiguration` een achtergrond taak om de bewerking uit te voeren. Als u de para meter `-Verbose` opgeeft, kunt u de **uitgebreide** uitvoer van de bewerking bekijken. `-Wait`en `-Verbose` zijn beide optionele para meters.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>De configuratie testen

Zodra de cmdlet `Start-DSCConfiguration` is voltooid, ziet u het bestand HelloWorld. txt op de locatie die u hebt opgegeven. U kunt de inhoud controleren met de cmdlet [Get-content](/powershell/module/microsoft.powershell.management/get-content) .

U kunt ook de huidige status *testen* met [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

De uitvoer moet ' waar ' zijn als het knoop punt momenteel compatibel is met de toegepaste configuratie.

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

## <a name="re-applying-the-configuration"></a>De configuratie opnieuw Toep assen

Als u wilt zien hoe de configuratie Get opnieuw wordt toegepast, kunt u het tekst bestand verwijderen dat door uw configuratie is gemaakt. De cmdlet `Start-DSCConfiguration` gebruiken met de para meter `-UseExisting`. De para meter `-UseExisting` geeft aan `Start-DSCConfiguration` het huidige. MOF-bestand opnieuw toe te passen, waarmee de meest recent toegepaste configuratie wordt aangeduid.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Volgende stappen

- Meer informatie over DSC-configuraties vindt u in [DSC-configuraties](configurations.md).
- Bekijk welke DSC-resources beschikbaar zijn en hoe u aangepaste DSC-resources maakt op [DSC-resources](../resources/resources.md).
- DSC-configuraties en-resources zoeken in de [PowerShell Gallery](https://www.powershellgallery.com/).
