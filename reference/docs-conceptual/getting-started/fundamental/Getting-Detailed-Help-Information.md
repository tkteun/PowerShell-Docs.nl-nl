---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Gedetailleerde Help-informatie verkrijgen
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: 29c24af3f688f9388893044952442910e793842d
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34483029"
---
# <a name="getting-detailed-help-information"></a>Gedetailleerde Help-informatie verkrijgen
Windows PowerShell bevat gedetailleerde Help-onderwerpen waarin wordt uitgelegd concepten voor Windows PowerShell en de Windows PowerShell-taal. Er zijn ook Help-onderwerpen voor elke cmdlet en de provider en Help-onderwerpen voor veel functies en scripts.

U kunt de meest recente versies van de volgende onderwerpen in de Microsoft TechNet Library weergeven of deze Help-onderwerpen bij de opdrachtprompt weer. Veel programma's die als host fungeren van Windows PowerShell, zoals Windows PowerShell Integrated Scripting Environment, bieden extra hulp-functies, zoals contextgevoelige Help en gecompileerde Help-bestand (.chm).

## <a name="getting-help-for-cmdlets"></a>Help bij Cmdlets voor ophalen
Als u Help-informatie over Windows PowerShell-cmdlets, gebruikt de [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet. Als u bijvoorbeeld ondersteuning voor de [Get-ChildItem [m2]](https://technet.microsoft.com/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, type:

```
get-help get-childitem
```

of

```
get-childitem -?
```

U kunt zelfs Help-informatie ophalen over de cmdlet Get-Help. Bijvoorbeeld:

```
get-help get-help
```

Als u een lijst met de cmdlet Help-onderwerpen in uw sessie, typt u:

```
get-help -category cmdlet
```

Gebruiken om een pagina te openen van elke Help-onderwerp op een tijdstip, de **help** functie of de alias **man**. Typ bijvoorbeeld als Help wilt weergeven voor de cmdlet Get-ChildItem,

```
man get-childitem
```

of

```
help get-childitem
```

Gedetailleerde informatie over een cmdlet, een functie of een script, met inbegrip van beschrijvingen van de parameters en voorbeelden van het gebruik ervan, gebruiken de *gedetailleerd* parameter van de cmdlet Get-Help. Bijvoorbeeld, als u gedetailleerde informatie over de cmdlet Get-ChildItem, typt u:

```
get-help get-childitem -detailed
```

U kunt alle inhoud weergeven in het Help-onderwerp gebruiken de *volledige* parameter van de cmdlet Get-Help. Bijvoorbeeld, als u wilt weergeven van alle inhoud in de Help-onderwerp voor de cmdlet Get-ChildItem, typt u:

```
get-help get-childitem -full
```

Gedetailleerde ophalen Help-informatie over de parameters van een cmdlet, gebruik de *Parameter* parameter van de cmdlet Get-Help. Bijvoorbeeld, om op te halen gedetailleerde Help voor alle parameters van de cmdlet Get-ChildItem, type:

```
get-help get-childitem -parameter *
```

Gebruikt u alleen de voorbeelden in een Help-onderwerp weergeven door de *voorbeeld* parameter van de Get-Help. Typ bijvoorbeeld het volgende zodat alleen de voorbeelden in het Help-onderwerp voor de cmdlet Get-ChildItem:

```
get-help get-childitem -examples
```

Zie voor meer informatie over het schrijven van Help-onderwerpen voor de cmdlets die u schrijft [schrijven Cmdlet helpen](https://go.microsoft.com/fwlink/?LinkID=123415) in de MSDN-bibliotheek.

## <a name="getting-conceptual-help"></a>Conceptuele Help opvragen
De cmdlet Get-Help bevat ook informatie over conceptuele onderwerpen in Windows PowerShell, met inbegrip van onderwerpen over de Windows PowerShell-taal. Conceptuele Help-onderwerpen beginnen met het voorvoegsel 'about_', zoals about_line_editing. (De naam van het conceptuele onderwerp moet worden ingevoerd in het Engels zelfs op niet-Engelse versies van Windows PowerShell.)

Als een lijst met algemene onderwerpen weergeven, typt u:

```
get-help about_*
```

Als u wilt een bepaalde Help-onderwerp weergeven, typt u bijvoorbeeld de naam van het onderwerp:

```
get-help about_command_syntax
```

De parameters van Get-Help, zoals *gedetailleerd*, *Parameter*, en *voorbeelden*, hebben geen effect op de weergave van de conceptuele Help-onderwerpen.

## <a name="getting-help-about-providers"></a>Help-informatie over Providers
De cmdlet Get-Help bevat informatie over Windows PowerShell-providers. Als u de Help voor een provider, typ 'Get-Help"gevolgd door de naam van de provider. Bijvoorbeeld, als u de Help voor de Register-provider, typt u:

```
get-help registry
```

Als u een lijst van alle provider Help-onderwerpen in uw sessie, typt u het volgende:

```
get-help -category provider
```

De parameters van Get-Help, zoals *gedetailleerd*, *Parameter*, en *voorbeelden*, hebben geen effect op de weergave van de provider Help-onderwerpen.

## <a name="getting-help-about-scripts-and-functions"></a>Help opvragen over Scripts en functies
Veel scripts en functies in Windows PowerShell beschikken over de Help-onderwerpen. Gebruik de cmdlet Get-Help om Help-onderwerpen voor scripts en functies weer te geven.

Als u de Help voor een functie, typt u 'get-help"gevolgd door de naam van de functie. Bijvoorbeeld, als u de Help voor de functie Disable-PSRemoting, typt u:

```
get-help disable-psremoting
```

Typ de volledig gekwalificeerde pad naar het scriptbestand de Help-informatie voor een script. Als het script in een pad dat wordt vermeld in de omgevingsvariabele Path is, kunt u het pad van de opdracht weglaten.

Bijvoorbeeld, als er een script met de naam 'TestScript.ps1' in uw C:\\PS-Test directory, zodat het Help-onderwerp voor het script, type:

```
get-help c:\ps-test\TestScript.ps1
```

De parameters die zijn ontworpen voor het weergeven van de cmdlet Help zoals *gedetailleerd*, *volledige*, *voorbeelden*, en *Parameter*, voor script Help-informatie en hulp nodig hebt, te werken. Echter, wanneer u alle Help weergeven door in te voeren ' get-help \*', Help voor functies en scripts niet wordt weergegeven.

Zie voor meer informatie over het schrijven van Help-onderwerpen voor de functies en scripts [about_Functions [m2]](https://technet.microsoft.com/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/library/7dc08334-dcfe-450b-b949-0554855623af), en [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).

## <a name="getting-help-online"></a>Help-informatie Online
Als u met het Internet verbonden bent, is een van de aanbevolen manieren om hulp te krijgen om de Help-onderwerpen online weer te geven. Omdat online-onderwerpen gemakkelijk om bij te werken, zijn ze waarschijnlijk de meest actuele informatie bieden.

Als u online Help, probeert de *Online* parameter van de cmdlet Get-Help. De *Online* parameter van de Get-Help cmdlet werkt alleen voor cmdlet Help Help functioneren en Help script. U kunt geen gebruiken de *Online* parameter met de conceptuele (over) onderwerpen of provider Help-onderwerpen. Bovendien omdat deze functie optioneel is, werkt het niet voor elke cmdlet, een functie of een script Help-onderwerp.

Echter alle Help-onderwerpen die worden geleverd met Windows PowerShell, met inbegrip van provider Help en conceptuele (over) Help-onderwerpen zijn online beschikbaar de [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) sectie van de Microsoft TechNet Library.

Gebruik de *Online* parameter van de cmdlet Get-Help, gebruik de volgende notatie voor de opdracht.

```
get-help <command-name> -online
```

Bijvoorbeeld, als u de online versie van het Help-onderwerp over de cmdlet Get-ChildItem, typt u:

```
get-help get-childitem -online
```

Als een onlineversie van het Help-onderwerp beschikbaar is, wordt deze in de standaardbrowser geopend.

Als de online-Help wordt ondersteund voor een Help-onderwerp, kunt u ook het internetadres (URL) van het Help-onderwerp weergeven. Het internetadres wordt weergegeven in de sectie Verwante koppelingen van een Help-onderwerp.

Bijvoorbeeld, als u wilt zien van de URL voor de online versie van de cmdlet Add-Computer, typt u:

```
get-help add-computer
```

De eerste regel in het gedeelte Verwante koppelingen van het onderwerp worden hieronder weergegeven.

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

Zie voor meer informatie over het online ondersteuning bieden voor uw Help-onderwerpen [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf), en zien [schrijven Cmdlet helpen](https://go.microsoft.com/fwlink/?LinkID=123415) in de MSDN-bibliotheek.

## <a name="see-also"></a>Zie ook
- [about_Functions [m2]](https://technet.microsoft.com/library/61d40692-5300-4de9-a9b5-bae31815e105)
- [about_Scripts](https://technet.microsoft.com/library/7dc08334-dcfe-450b-b949-0554855623af)
- [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)