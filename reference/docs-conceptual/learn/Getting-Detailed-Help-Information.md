---
ms.date: 08/27/2018
keywords: PowerShell-cmdlet
title: Gedetailleerde Help-informatie verkrijgen
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: 8b56f003fdef38b0f126cfe82eefcc145cc54783
ms.sourcegitcommit: 3402a478cf118c11a5642038eb117bc76553e3ab
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53411596"
---
# <a name="getting-detailed-help-information"></a>Gedetailleerde Help-informatie verkrijgen

PowerShell bevat gedetailleerde Help-artikelen waarin wordt uitgelegd van de PowerShell-concepten en de PowerShell-taal. Er zijn ook Help-artikelen voor elke cmdlet en de provider en voor veel functies en scripts.

U kunt deze Help-artikelen weergeven bij de opdrachtprompt of weergave de meest recente bijgewerkte versies van de volgende artikelen in de [PowerShell](/powershell/scripting/overview) online documentatie.

## <a name="getting-help-for-cmdlets"></a>Help-informatie voor cmdlets

Als u Help-informatie over PowerShell-cmdlets, gebruikt de [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet. Als u bijvoorbeeld ondersteuning voor de `Get-ChildItem` cmdlet, type:

```powershell
Get-Help Get-ChildItem
```

of

```powershell
Get-ChildItem -?
```

U kunt ook hulp krijgen over de cmdlet Get-Help. Bijvoorbeeld:

```powershell
Get-Help Get-Help
```

Als u een lijst met alle van de cmdlet Help-artikelen in uw sessie, typt u:

```powershell
Get-Help -Category Cmdlet
```

Als u een pagina van de Help-artikel weergeven op een tijdstip, gebruiken de `help` functie of de alias `man`.
Bijvoorbeeld, om de Help voor weer te geven de `Get-ChildItem` cmdlet, type

```powershell
man Get-ChildItem
```

of

```powershell
help Get-ChildItem
```

Als u gedetailleerde informatie weergeven, gebruiken de **gedetailleerd** parameter van de `Get-Help` cmdlet. Bijvoorbeeld, voor gedetailleerde informatie over de `Get-ChildItem` cmdlet, type:

```powershell
Get-Help Get-ChildItem -Detailed
```

Als u alle inhoud weergeven in het Help-artikel, gebruiken de **volledige** parameter van de `Get-Help` cmdlet. Bijvoorbeeld, om weer te geven van alle inhoud in het Help-artikel voor de `Get-ChildItem` cmdlet, type:

```powershell
Get-Help Get-ChildItem -Full
```

Informatie ophalen over over de parameters van een cmdlet, gebruik de **Parameter** parameter van de `Get-Help` cmdlet. Bijvoorbeeld, om op te halen gedetailleerde Help-informatie voor alle van de parameters van de `Get-ChildItem` cmdlet, type:

```powershell
Get-Help Get-ChildItem -Parameter *
```

Als u alleen de voorbeelden weergeven in een Help-artikel, gebruiken de **voorbeelden** parameter van de `Get-Help`.
Bijvoorbeeld, om weer te geven alleen de voorbeelden in het Help-artikel voor de `Get-ChildItem `cmdlet, type:

```powershell
Get-Help Get-ChildItem -Examples
```

Zie voor meer informatie over het schrijven van Help-artikelen voor de cmdlets die u schrijft [schrijven Cmdlet helpen](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).

## <a name="getting-conceptual-help"></a>Algemene hulp

De `Get-Help` cmdlet ook informatie over conceptuele artikelen in PowerShell, met inbegrip van de artikelen over de PowerShell-taal weergegeven. Algemene Help artikelen met het voorvoegsel 'about_', zoals about_line_editing beginnen. (De naam van het conceptueel artikel moet worden ingevoerd in het Engels zelfs op niet-Engelse versies van PowerShell.)

Als een lijst van de conceptuele artikelen weergeven, typt u:

```powershell
Get-Help about_*
```

Als een bepaalde Help-artikel weergeven, typt u de artikelnaam, bijvoorbeeld:

```powershell
Get-Help about_command_syntax
```

De parameters van `Get-Help`, zoals **gedetailleerd**, **Parameter**, en **voorbeelden**, hebben geen effect op de weergave van de conceptuele Help-artikelen.

## <a name="getting-help-about-providers"></a>Help opvragen over providers

De `Get-Help` cmdlet geeft informatie weer over de PowerShell-providers. Typ voor hulp bij een provider, `Get-Help` gevolgd door de naam van de provider. Bijvoorbeeld, als u de Help voor de provider register, typt u:

```powershell
Get-Help registry
```

Als u een lijst met alle van de provider Help-artikelen in uw sessie, typt u het volgende:

```powershell
Get-Help -Category provider
```

De parameters van `Get-Help`, zoals **gedetailleerd**, **Parameter**, en **voorbeelden**, hebben geen effect op de weergave van de provider Help-artikelen.

## <a name="getting-help-about-scripts-and-functions"></a>Help opvragen over scripts en functies

Veel scripts en functies in PowerShell hebben de Help-artikelen. Gebruik de `Get-Help` cmdlet om de Help-artikelen voor scripts en functies weer te geven.

Als u de Help voor een functie, typt `Get-Help` gevolgd door de naam van de functie. Als u bijvoorbeeld ondersteuning voor de `Disable-PSRemoting` functie, typ:

```powershell
Get-Help Disable-PSRemoting
```

Als de Help voor een script weergeven, typt u het pad naar het scriptbestand. Als het script zich niet in een pad dat is opgenomen in de omgevingsvariabele Path, moet u de volledig gekwalificeerde pad gebruiken.

Bijvoorbeeld, als u een script met de naam 'TestScript.ps1' op uw C: hebt\\PS-/ Test-directory, om weer te geven van het Help-artikel voor het script, type:

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

De parameters die zijn ontworpen voor het weergeven van de cmdlet Help werken voor het script en de functie helpen te. Help voor functies en scripts wordt echter niet weergegeven tijdens het uitvoeren van `Get-Help *`.

Zie de volgende artikelen voor meer informatie over het schrijven van Help-artikelen voor de functies en -scripts:

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a>Online hulp

Voor het weergeven van de Help-artikelen online is een van de beste manieren om hulp te krijgen. Online artikelen zijn gemakkelijker te werken en geef de meest recente inhoud.

Als u online Help, gebruikt u de **Online** parameter van de `Get-Help` cmdlet. Alle Help-artikelen die worden geleverd met PowerShell, met inbegrip van provider Help en conceptuele (Help-artikelen over) zijn online beschikbaar in de [PowerShell](/powershell/scripting/powershell-scripting) documentatie.

> [!NOTE]
> U kunt geen gebruiken de **Online** parameter met de conceptuele (about_\*) of provider Help-artikelen.
> Online-help is optioneel, zodat deze niet voor elke cmdlet, een functie of een script werkt.

Bijvoorbeeld, om op te halen van de online versie van het Help-artikel over de `Get-ChildItem` cmdlet, type:

```powershell
Get-Help Get-ChildItem -Online
```

PowerShell wordt het artikel in de standaardbrowser geopend. Als online-Help wordt ondersteund voor een Help-artikel, kunt u ook de URL van het Help-artikel weergeven. De URL wordt weergegeven in de sectie Verwante koppelingen van een Help-artikel.

Bijvoorbeeld, als u wilt zien van de URL voor de online versie van de cmdlet Add-Computer, typt u:

```powershell
Get-Help Add-Computer
```

Hieronder ziet u de eerste regel in de sectie Verwante koppelingen van het artikel.

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

Zie voor meer informatie over hoe u online om ondersteuning te bieden voor de Help-artikelen [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

## <a name="see-also"></a>Zie ook

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [Get-Help](/powershell/module/microsoft.powershell.core/get-help)
