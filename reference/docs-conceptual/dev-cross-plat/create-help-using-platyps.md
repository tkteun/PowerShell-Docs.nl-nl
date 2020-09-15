---
title: Help maken op basis van XML met behulp van PlatyPS
description: Het gebruik van PlatyPS is de snelle en efficiënte manier om op XML gebaseerde Help te maken.
ms.date: 07/21/2020
ms.openlocfilehash: 79cf8c077a07bf1e7aa8ea1ea799be5f8d4af12c
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "86972608"
---
# <a name="create-xml-based-help-using-platyps"></a>Help maken op basis van XML met behulp van PlatyPS

Wanneer u een Power shell-module maakt, is het raadzaam om gedetailleerde hulp te bieden voor de cmdlets die u maakt. Als uw cmdlets in gecompileerde code worden geïmplementeerd, moet u de Help op XML gebruiken. Deze XML-indeling wordt ook wel bekend als micro soft Assistance Markup Language (MAML).

De verouderde Power shell SDK-documentatie bevat informatie over het maken van Help voor Power shell-cmdlets, verpakt in modules. Power shell biedt echter geen hulp middelen voor het maken van XML-Help. In de SDK-documentatie wordt de structuur van de MAML-Help uitgelegd, maar u kunt de taak voor het maken van de complexe en diep geneste MAML-inhoud hand matig door bladeren.

Hier kunt u de [PlatyPS][] -module helpen.

## <a name="what-is-platyps"></a>Wat is PlatyPS?

PlatyPS is een [open source-][platyps-repo] hulp programma dat is gestart als een _hackathon_ -project om het maken en onderhouden van MAML eenvoudiger te maken. PlatyPS documenten de syntaxis van parameter sets en de afzonderlijke para meters voor elke cmdlet in uw module. PlatyPS maakt gestructureerde bestanden met een [afkorting][] die de syntaxis informatie bevatten. U kunt geen beschrijvingen maken of voor beelden opgeven.

PlatyPS maakt tijdelijke aanduidingen zodat u beschrijvingen en voor beelden kunt invullen. Nadat de vereiste informatie is toegevoegd, compileert PlatyPS de bestanden van de verlaging in MAML-bestanden. In het Help-systeem van Power shell kunt u ook Help-bestanden met tekst zonder opmaak (informatie over onderwerpen). PlatyPS heeft een cmdlet voor het maken van een gestructureerde prijsverlagings sjabloon voor een nieuw _info_ bestand, maar deze `about_*.help.txt` bestanden moeten hand matig worden bewaard.

U kunt de Help-bestanden voor MAML en tekst toevoegen aan uw module. U kunt PlatyPS ook gebruiken om de Help-bestanden te compileren in een CAB-pakket dat kan worden gehost op de Help die kan worden bijgewerkt.

## <a name="get-started-using-platyps"></a>Aan de slag met PlatyPS

Eerst moet u PlatyPS installeren vanaf de PowerShell Gallery.

```powershell
Install-Module platyps -Force
Import-Module platyps
```

Het volgende stroom diagram geeft een overzicht van het proces voor het maken of bijwerken van Power shell-referentie-inhoud.

:::image type="content" source="./media/create-help-using-platyps/cmdlet-ref-flow-v2.png" alt-text="De werk stroom voor het maken van XML-Help-informatie met behulp van PlatyPS":::

##  <a name="create-markdown-content-for-a-powershell-module"></a>Inhoud voor afprijsing maken voor een Power shell-module

1. Importeer uw nieuwe module in de sessie. Herhaal deze stap voor elke module die u wilt documenteren.

   Voer de volgende opdracht uit om de modules te importeren:

   ```powershell
   Import-Module <your module name>
   ```

1. Gebruik PlatyPS om kortings bestanden te genereren voor uw module pagina en alle bijbehorende cmdlets in de module. Herhaal deze stap voor elke module die u wilt documenteren.

   ```powershell
   $OutputFolder = <output path>
   $parameters = @{
       Module = <ModuleName>
       OutputFolder = $OutputFolder
       AlphabeticParamsOrder = $true
       WithModulePage = $true
       ExcludeDontShow = $true
       Encoding = 'UTF8BOM'
   }
   New-MarkdownHelp @parameters

   New-MarkdownAboutHelp -OutputFolder $OutputFolder -AboutName "topic_name"
   ```

   Als de uitvoermap niet bestaat, `New-MarkdownHelp` maakt u deze. In dit voor beeld `New-MarkdownHelp` maakt u een bestand voor korting voor elke cmdlet in de module. Ook wordt de _module pagina_ gemaakt in een bestand met de naam `<ModuleName>.md` . Deze module pagina bevat een lijst met de cmdlets in de module en de tijdelijke aanduidingen voor de beschrijving van de samen **vatting** . De meta gegevens in de module pagina zijn afkomstig uit het module manifest en worden door PlatyPS gebruikt om het XML-bestand HelpInfo te maken (zoals [hieronder](#creating-an-updateable-help-package)wordt uitgelegd).

   `New-MarkdownAboutHelp` Hiermee maakt u _een nieuw bestand_ met de naam `about_topic_name.md` .

   Zie [New-MarkdownHelp][] en [New-MarkdownAboutHelp][]voor meer informatie.

### <a name="update-existing-markdown-content-when-the-module-changes"></a>Bestaande inhoud voor prijs verlaging bijwerken wanneer de module wordt gewijzigd

PlatyPS kan ook bestaande prijsverlagings bestanden voor een module bijwerken. Gebruik deze stap om bestaande modules bij te werken met nieuwe cmdlets, nieuwe para meters of para meters die zijn gewijzigd.

1. Importeer uw nieuwe module in de sessie. Herhaal deze stap voor elke module die u wilt documenteren.

   Voer de volgende opdracht uit om de modules te importeren:

   ```powershell
   Import-Module <your module name>
   ```

1. Gebruik PlatyPS om de prijsverlagings bestanden voor de module landings pagina en alle bijbehorende cmdlets in de module bij te werken. Herhaal deze stap voor elke module die u wilt documenteren.

   ```powershell
   $parameters = @{
       Path = <folder with Markdown>
       RefreshModulePage = $true
       AlphabeticParamsOrder = $true
       UpdateInputOutput = $true
       ExcludeDontShow = $true
       LogPath = <path to store log file>
       Encoding = 'UTF8BOM'
   }
   Update-MarkdownHelpModule @parameters
   ```

   `Update-MarkdownHelpModule` Hiermee worden de bestanden van de cmdlet en module bijgewerkt in de opgegeven map.
   De bestanden worden niet bijgewerkt `about_*.md` . Het module bestand ( `ModuleName.md` ) ontvangt nieuwe samen **vattingen** die zijn toegevoegd aan de cmdlet-bestanden. Updates voor cmdlet-bestanden bevatten de volgende wijziging:

   - Nieuwe parameter sets
   - Nieuwe parameters
   - Meta gegevens van de para meter bijgewerkt
   - Informatie over invoer en uitvoer type bijgewerkt

   Zie [Update-MarkdownHelpModule][]voor meer informatie.

## <a name="edit-the-new-or-updated-markdown-files"></a>De nieuwe of bijgewerkte verkortings bestanden bewerken

PlatyPS documenten de syntaxis van de parameter sets en de afzonderlijke para meters. U kunt geen beschrijvingen maken of voor beelden opgeven. De specifieke gebieden waar inhoud nodig is, zijn opgenomen in accolades. Bijvoorbeeld: `{{ Fill in the Description }}`

:::image type="content" source="./media/create-help-using-platyps/placeholders-example.png" alt-text="Sjabloon voor korting met de tijdelijke aanduidingen in VS code":::

U moet een samen vatting toevoegen, een beschrijving van de cmdlet, beschrijvingen voor elke para meter en ten minste één voor beeld.

Voor gedetailleerde informatie over het schrijven van Power shell-inhoud raadpleegt u de volgende artikelen:

- [Power shell-stijl gids](/powershell/scripting/community/contributing/powershell-style-guide)
- [Verwijzings artikelen bewerken](/powershell/scripting/community/contributing/editing-cmdlet-ref)

> [!NOTE]
> PlatyPS heeft een specifiek schema dat wordt gebruikt voor cmdlet-referentie. Dit schema staat alleen bepaalde blokken met prijs verlagingen in specifieke secties van het document toe. Als u inhoud op de verkeerde locatie plaatst, mislukt de PlatyPS-build-stap. Zie de [schema][] documentatie in de PlatyPS-opslag plaats voor meer informatie. Zie [Get-item][]voor een volledig voor beeld van een juist opgemaakte cmdlet-verwijzing.

Nadat u de vereiste inhoud voor elk van de cmdlets hebt opgegeven, moet u ervoor zorgen dat u de landings pagina van de module bijwerkt. Controleer of uw module de juiste `Module Guid` en `Download Help Link` waarden in de yaml-meta gegevens van het `<module-name>.md` bestand bevat. Voeg ontbrekende meta gegevens toe.

Het is ook mogelijk dat er voor sommige cmdlets een samen **vatting** (_korte beschrijving_) ontbreekt. Met de volgende opdracht wordt de module landings pagina bijgewerkt met de beschrijvende tekst van de samen **vatting** . Open de pagina module overloop om de beschrijvingen te controleren.

```powershell
Update-MarkdownHelpModule –Path <full path output folder> -RefreshModulePage
```

Nu u alle inhoud hebt ingevoerd, kunt u de MAML-Help-bestanden maken die worden weer gegeven `Get-Help` in de Power shell-console.

## <a name="create-the-external-help-files"></a>De externe Help-bestanden maken

Met deze stap maakt u de MAML Help-bestanden die worden weer gegeven `Get-Help` in de Power shell-console.

Voer de volgende opdracht uit om de MAML-bestanden te bouwen:

```powershell
New-ExternalHelp –Path <folder with MDs> -OutputPath <output help folder>
```

`New-ExternalHelp` Hiermee converteert u alle bestanden van de cmdlet voor het afprijsen van een (of meer) MAML-bestanden. Over bestanden worden geconverteerd naar onbewerkte-tekst bestanden met de volgende naam indeling: `about_topic_name.help.txt` .
De inhoud van de prijs opgave moet voldoen aan de vereiste van het PlatyPS-schema. `New-ExternalHelp` wordt afgesloten met fouten wanneer de inhoud niet voldoet aan het schema. U moet de bestanden bewerken om de schendingen van het schema op te lossen.

> [!CAUTION]
> PlatyPS voert een slechte taak om de `about_*.md` bestanden om te zetten in tekst zonder opmaak. U moet een zeer eenvoudige prijs verlaging gebruiken om aanvaard bare resultaten te krijgen. Mogelijk wilt u de bestanden in de indeling tekst zonder opmaak behouden `about_topic_name.help.txt` , in plaats van PlatyPS toe te staan om ze te converteren.

Zodra deze stap is voltooid, ziet u `*-help.xml` `about_*.help.txt` de bestanden in de doelmap.

Zie [New-ExternalHelp][] voor meer informatie.

### <a name="test-the-compiled-help-files"></a>De gecompileerde Help-bestanden testen

U kunt de inhoud controleren met de cmdlet [Get-HelpPreview][] :

```powershell
Get-HelpPreview -Path "<ModuleName>-Help.xml"
```

De cmdlet leest het gecompileerde MAML-bestand en voert de inhoud uit met dezelfde indeling als waaruit u zou ontvangen `Get-Help` . Hierdoor kunt u de resultaten controleren om te verifiëren of de verkortings bestanden correct zijn gecompileerd en de gewenste resultaten opleveren. Als er een fout optreedt, wijzigt u de bestanden voor de prijs verlaging opnieuw en compileert u de MAML opnieuw.

U bent nu klaar om uw Help-bestanden te publiceren.

## <a name="publishing-your-help"></a>Uw Help publiceren

Nu u de bestanden voor de prijs verlaging hebt gecompileerd in Power shell Help-bestanden, kunt u de bestanden beschikbaar maken voor gebruikers. Er zijn twee opties om hulp te bieden in de Power shell-console.

- De Help-bestanden inpakken met de module
- Een Help-pakket maken dat door gebruikers kan worden geïnstalleerd met de `Update-Help` cmdlet

### <a name="packaging-help-with-the-module"></a>Help bij de module inpakken

De Help-bestanden kunnen worden verpakt met uw module. Zie [hulp bij het schrijven van Help voor modules][] voor meer informatie over de mapstructuur. U moet de lijst met Help-bestanden opnemen in de waarde van de sleutel **File List** in het module manifest.

### <a name="creating-an-updateable-help-package"></a>Een Help-pakket maken dat kan worden bijgewerkt

Op hoog niveau zijn de stappen voor het maken van de updateable de volgende informatie:

1. Een Internet site zoeken om uw Help-bestanden te hosten
1. Een **HelpInfoURI** -sleutel toevoegen aan het module manifest
1. Een HelpInfo XML-bestand maken
1. CAB-bestanden maken
1. Uw bestanden uploaden

Zie voor meer informatie [ondersteunende Help-informatie: stapsgewijze instructies][step-by-step].

PlatyPS helpt u bij het uitvoeren van een aantal van deze stappen.

De **HelpInfoURI** is een URL die verwijst naar de locatie waar uw Help-bestanden worden gehost op internet. Deze waarde wordt geconfigureerd in het module manifest. `Update-Help` Hiermee wordt het module manifest gelezen om deze URL op te halen en de Help-inhoud te downloaden die kan worden bijgewerkt. Deze URL mag alleen verwijzen naar de maplocatie en niet naar afzonderlijke bestanden. `Update-Help` maakt de bestands namen die moeten worden gedownload op basis van andere informatie uit het module manifest en het HelpInfo XML-bestand.

> [!IMPORTANT]
> De **HelpInfoURI** moet eindigen met een slash ( `/` ). Zonder dat teken `Update-Help` kunt u niet de juiste bestands paden maken om de inhoud te downloaden. Daarnaast zijn de meeste op HTTP gebaseerde bestands Services hoofdletter gevoelig. Het is belang rijk dat de meta gegevens van de module in het XML-bestand van de HelpInfo de juiste letters bevatten.

`New-ExternalHelp`Met de cmdlet maakt u het HelpInfo XML-bestand in de uitvoermap. Het HelpInfo XML-bestand wordt gemaakt met behulp van YAML-meta gegevens die zijn opgenomen in de module reprijsing files ( `ModuleName.md` ).

De `New-ExternalHelpCab` cmdlet maakt zip-en cab-bestanden met de MAML en `about_*.help.txt` bestanden die u hebt opgesteld. CAB-bestanden zijn compatibel met alle versies van Power shell.
Power shell 6 en hoger kunnen ZIP-bestanden gebruiken.

```powershell
$helpCabParameters = @{
    CabFilesFolder = $MamlOutputFolder
    LandingPagePath = $LandingPage
    OutputFolder = $CabOutputFolder
}
New-ExternalHelpCab @helpCabParameters
```

Nadat u de ZIP-en CAB-bestanden hebt gemaakt, uploadt u de ZIP-, CAB-en HelpInfo-XML-bestanden naar de HTTP-Bestands server. Plaats de bestanden op de locatie die wordt aangegeven door de **HelpInfoURI**.

Zie [New-ExternalHelpCab][]voor meer informatie.

### <a name="other-publishing-options"></a>Andere publicatie opties

De prijs verlaging is een veelzijdige indeling die eenvoudig kan worden omgezet naar andere indelingen voor publicatie. Met een hulp programma, zoals [pandoc][], kunt u uw Help-bestanden voor prijs verlaging omzetten in veel verschillende document indelingen, waaronder tekst zonder opmaak, HTML, PDF en Office-document.

Daarnaast kunnen de cmdlets [ConvertFrom-][] prijs verlaging en [weer geven][] in Power shell 6 en hoger worden gebruikt om de prijs verlaging naar HTML te converteren of een kleur rijke weer gave in de Power shell-console te maken.

## <a name="known-issues"></a>Bekende problemen

PlatyPS is zeer gevoelig voor het [schema][] voor de structuur van de geprijsde bestanden die het maakt en compileert. Het is heel eenvoudig om een geldige prijs verlaging te schrijven die in strijd is met dit schema. Raadpleeg de [Power shell-stijl gids][] en [Bewerk referentie artikelen][]voor meer informatie.

<!-- link references -->
[platyps-repo]: https://github.com/PowerShell/platyps
[PlatyPS]: https://www.powershellgallery.com/packages/platyPS/
[Markdown]: https://commonmark.org
[markdig]: https://github.com/lunet-io/markdig
[schema]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[Get-item]: https://github.com/MicrosoftDocs/PowerShell-Docs/blob/staging/reference/7.0/Microsoft.PowerShell.Management/Get-Item.md
[New-MarkdownHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownHelp.md
[Update-MarkdownHelpModule]: https://github.com/PowerShell/platyPS/blob/master/docs/Update-MarkdownHelpModule.md
[New-MarkdownAboutHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownAboutHelp.md
[New-ExternalHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelp.md
[Get-HelpPreview]: https://github.com/PowerShell/platyPS/blob/master/docs/Get-HelpPreview.md
[New-ExternalHelpCab]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelpCab.md
[Power shell-stijl gids]: /powershell/scripting/community/contributing/powershell-style-guide
[Verwijzings artikelen bewerken]: /powershell/scripting/community/contributing/editing-cmdlet-ref
[Help-informatie over modules schrijven]: /powershell/scripting/developer/help/writing-help-for-windows-powershell-modules
[step-by-step]: /powershell/scripting/developer/help/updatable-help-authoring-step-by-step
[Pandoc]: https://pandoc.org
[ConvertFrom-prijs verlaging]: /powershell/module/microsoft.powershell.utility/convertfrom-markdown
[Weer geven-prijs verlaging]: /powershell/module/microsoft.powershell.utility/show-markdown
