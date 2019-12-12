---
ms.date: 08/27/2018
keywords: Power shell, cmdlet
title: Gedetailleerde Help-informatie verkrijgen
ms.openlocfilehash: e722eb8a0ca13e3d2de864314775a0a9fa578390
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417657"
---
# <a name="getting-detailed-help-information"></a>Gedetailleerde Help-informatie verkrijgen

Power shell bevat gedetailleerde Help-artikelen waarin Power shell-concepten en de Power shell-taal worden uitgelegd. Er zijn ook Help-artikelen voor elke cmdlet en provider en voor veel functies en scripts.

U kunt deze Help-artikelen weer geven via de opdracht prompt of de meest recent bijgewerkte versies van deze artikelen weer geven in de [Power shell](/powershell/scripting/overview) -documentatie online.

## <a name="getting-help-for-cmdlets"></a>Hulp krijgen voor cmdlets

Gebruik de cmdlet [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) voor meer informatie over Power shell-cmdlets. Als u bijvoorbeeld hulp wilt krijgen voor de cmdlet `Get-ChildItem`, typt u:

```powershell
Get-Help Get-ChildItem
```

of

```powershell
Get-ChildItem -?
```

U kunt zelfs hulp krijgen bij de cmdlet Get-Help. Bijvoorbeeld:

```powershell
Get-Help Get-Help
```

Als u een lijst wilt weer geven met alle Help-artikelen over cmdlets in uw sessie, typt u:

```powershell
Get-Help -Category Cmdlet
```

Als u per keer één pagina van elk Help-artikel wilt weer geven, gebruikt u de functie `help` of de alias `man`.
Als u bijvoorbeeld de Help voor de cmdlet `Get-ChildItem` wilt weer geven, typt u

```powershell
man Get-ChildItem
```

of

```powershell
help Get-ChildItem
```

Als u gedetailleerde informatie wilt weer geven, gebruikt u de para meter **Details** van de cmdlet `Get-Help`. Als u bijvoorbeeld gedetailleerde informatie over de cmdlet `Get-ChildItem` wilt ophalen, typt u:

```powershell
Get-Help Get-ChildItem -Detailed
```

Als u alle inhoud in het Help-artikel wilt weer geven, gebruikt u de **volledige** para meter van de cmdlet `Get-Help`. Als u bijvoorbeeld alle inhoud wilt weer geven in het Help-artikel voor de cmdlet `Get-ChildItem`, typt u:

```powershell
Get-Help Get-ChildItem -Full
```

Voor gedetailleerde informatie over de para meters van een cmdlet gebruikt u de para meter **parameter** van de cmdlet `Get-Help`. Als u bijvoorbeeld gedetailleerde Help wilt ophalen voor alle para meters van de cmdlet `Get-ChildItem`, typt u:

```powershell
Get-Help Get-ChildItem -Parameter *
```

Als u alleen de voor beelden in een Help-artikel wilt weer geven, gebruikt u de para meter **voor beelden** van de `Get-Help`.
Als u bijvoorbeeld alleen de voor beelden in het Help-artikel voor de cmdlet `Get-ChildItem` wilt weer geven, typt u:

```powershell
Get-Help Get-ChildItem -Examples
```

Zie de [Help bij cmdlet schrijven](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)voor meer informatie over het schrijven van Help-artikelen voor de cmdlets die u schrijft.

## <a name="getting-conceptual-help"></a>Conceptuele hulp krijgen

De cmdlet `Get-Help` bevat ook informatie over conceptuele artikelen in Power shell, inclusief artikelen over de Power shell-taal. Conceptuele Help-artikelen beginnen met het voor voegsel ' about_ ', zoals about_line_editing. (De naam van het conceptuele artikel moet worden ingevoerd in het Engels, zelfs op niet-Engelse versies van Power shell.)

Als u een lijst met conceptuele artikelen wilt weer geven, typt u:

```powershell
Get-Help about_*
```

Als u een bepaald Help-artikel wilt weer geven, typt u de artikel naam, bijvoorbeeld:

```powershell
Get-Help about_command_syntax
```

De para meters van `Get-Help`, zoals **gedetailleerde**, **para meters**en **voor beelden**, hebben geen effect op de weer gave van conceptuele Help-artikelen.

## <a name="getting-help-about-providers"></a>Hulp krijgen bij providers

De cmdlet `Get-Help` geeft informatie weer over Power shell-providers. Als u hulp wilt krijgen voor een provider, typt u `Get-Help` gevolgd door de naam van de provider. Als u bijvoorbeeld hulp wilt krijgen voor de register provider, typt u:

```powershell
Get-Help registry
```

Als u een lijst wilt weer geven met alle Help-artikelen van de provider in uw sessie, typt u

```powershell
Get-Help -Category provider
```

De para meters van `Get-Help`, zoals **gedetailleerde**, **para meters**en **voor beelden**, hebben geen invloed op de weer gave van de Help-artikelen van de provider.

## <a name="getting-help-about-scripts-and-functions"></a>Hulp krijgen over scripts en functies

Veel scripts en functies in Power Shell hebben Help-artikelen. Gebruik de cmdlet `Get-Help` om de Help-artikelen voor scripts en functies weer te geven.

Als u de Help voor een functie wilt weer geven, typt u `Get-Help` gevolgd door de naam van de functie. Als u bijvoorbeeld hulp wilt krijgen voor de functie `Disable-PSRemoting`, typt u:

```powershell
Get-Help Disable-PSRemoting
```

Als u de Help voor een script wilt weer geven, typt u het pad naar het script bestand. Als het script zich niet bevindt in een pad dat wordt vermeld in de omgevings variabele PATH, moet u het volledig gekwalificeerde pad gebruiken.

Als u bijvoorbeeld een script met de naam ' TestScript. ps1 ' in de map C:\\PS-test, om het Help-artikel voor het script weer te geven, typt u:

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

De para meters die zijn ontworpen voor het weer geven van cmdlet Help, werken ook voor de Help van script en functie. Help voor functies en scripts wordt echter niet weer gegeven wanneer u `Get-Help *`uitvoert.

Raadpleeg de volgende artikelen voor informatie over het schrijven van Help-artikelen voor uw functies en scripts:

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a>Online hulp krijgen

De Help-artikelen online bekijken is een van de beste manieren om hulp te krijgen. Online artikelen kunnen gemakkelijker worden bijgewerkt en bieden de meest actuele inhoud.

Gebruik de para meter **online** van de cmdlet `Get-Help` om online hulp te krijgen. Alle Help-artikelen die worden geleverd met Power shell, inclusief Help-artikelen voor de provider Help en conceptuele informatie, zijn online beschikbaar in de [Power shell](/powershell/scripting/powershell-scripting) -documentatie.

> [!NOTE]
> U kunt de para meter **online** niet gebruiken met de conceptuele (about_\*) of de Help-artikelen van de provider.
> Online-Help is optioneel en werkt daarom niet voor elke cmdlet, functie of script.

Als u bijvoorbeeld de online versie van het Help-artikel over de cmdlet `Get-ChildItem` wilt ophalen, typt u:

```powershell
Get-Help Get-ChildItem -Online
```

Power shell opent het artikel in de standaard browser. Als online-Help wordt ondersteund voor een Help-artikel, kunt u ook de URL van het Help-artikel weer geven. De URL wordt weer gegeven in de sectie verwante koppelingen van een Help-artikel.

Als u bijvoorbeeld de URL voor de online versie van de cmdlet Add-computer wilt weer geven, typt u:

```powershell
Get-Help Add-Computer
```

De eerste regel in de sectie verwante koppelingen van het artikel wordt hieronder weer gegeven.

```Output
Online version: https://go.microsoft.com/fwlink/?LinkId=821564
```

Zie [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)voor meer informatie over het bieden van online ondersteuning voor uw Help-artikelen.

## <a name="see-also"></a>Zie ook

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [Get-Help](/powershell/module/microsoft.powershell.core/get-help)
