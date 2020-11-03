---
description: Hierin wordt beschreven hoe u alternatieve namen gebruikt voor cmdlets en opdrachten in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_aliases?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Aliases
ms.openlocfilehash: e0a1fa357e591dd17986a8dd685a1818751ab355
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252950"
---
# <a name="about-aliases"></a>Over aliassen

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt beschreven hoe u alternatieve namen gebruikt voor cmdlets en opdrachten in Power shell.

## <a name="long-description"></a>LANGE BESCHRIJVING

Een alias is een alternatieve naam of bijnaam voor een cmdlet of voor een opdracht element, zoals een functie, script, bestand of een uitvoerbaar bestand. U kunt de alias gebruiken in plaats van de naam van de opdracht in Power shell-opdrachten.

Als u een alias wilt maken, gebruikt u de cmdlet New-Alias. Met de volgende opdracht wordt bijvoorbeeld het ' gas ' alias voor de `Get-AuthenticodeSignature` cmdlet gemaakt:

```powershell
New-Alias -Name gas -Value Get-AuthenticodeSignature
```

Nadat u de alias voor de naam van de cmdlet hebt gemaakt, kunt u de alias gebruiken in plaats van de naam van de cmdlet. Als u bijvoorbeeld de Authenticode-hand tekening wilt ophalen voor het SqlScript.ps1 bestand, typt u:

```powershell
Get-AuthenticodeSignature SqlScript.ps1
```

Of typ:

```powershell
gas SqlScript.ps1
```

Als u ' Word ' maakt als alias voor Microsoft Office woord, typt u ' woord ' in plaats van het volgende:

```powershell
"C:\Program Files\Microsoft Office\Office11\Winword.exe"
```

## <a name="built-in-aliases"></a>INGEBOUWDE ALIASSEN

Power shell bevat een reeks ingebouwde aliassen, waaronder "CD" en "chdir" voor de Set-Location cmdlet en "ls" en "dir" voor de Get-ChildItem-cmdlet.

Als u alle aliassen op de computer wilt ophalen, inclusief de ingebouwde aliassen, typt u:

```powershell
Get-Alias
```

## <a name="alias-cmdlets"></a>ALIAS-CMDLETS

Power shell bevat de volgende cmdlets, die zijn ontworpen voor het werken met aliassen:

- `Get-Alias` -Haalt alle aliassen in de huidige sessie op.
- `New-Alias` -Maakt een nieuwe alias.
- `Set-Alias` -Maakt of wijzigt een alias.
- `Export-Alias` -Exporteert een of meer aliassen naar een bestand.
- `Import-Alias` -Hiermee wordt een alias bestand in Power shell geïmporteerd.

Voor gedetailleerde informatie over de cmdlets typt u:

```powershell
Get-Help <cmdlet-Name> -Detailed
```

Typ bijvoorbeeld:

```powershell
Get-Help Export-Alias -Detailed
```

## <a name="creating-an-alias"></a>EEN ALIAS MAKEN

Als u een nieuwe alias wilt maken, gebruikt u de cmdlet New-Alias. Als u bijvoorbeeld de alias "GH" wilt maken voor Get-Help, typt u:

```powershell
New-Alias -Name gh -Value Get-Help
```

U kunt de alias gebruiken in opdrachten, net zoals u de volledige naam van de cmdlet gebruikt, en u kunt de alias gebruiken met para meters.

Als u bijvoorbeeld gedetailleerde Help-informatie voor de cmdlet Get-WmiObject wilt weer geven, typt u:

```powershell
Get-Help Get-WmiObject -Detailed
```

Of typ:

```powershell
gh Get-WmiObject -Detailed
```

## <a name="saving-aliases"></a>ALIASSEN OPSLAAN

De aliassen die u maakt, worden alleen in de huidige sessie opgeslagen. Als u de aliassen in een andere sessie wilt gebruiken, voegt u de alias toe aan uw Power shell-profiel. Of gebruik de Export-Alias cmdlet om de aliassen op te slaan in een bestand.

Typ voor meer informatie:

```powershell
Get-Help about_Profiles
```

## <a name="getting-aliases"></a>ALIASSEN OPHALEN

Als u alle aliassen in de huidige sessie wilt ophalen, met inbegrip van de ingebouwde aliassen, de aliassen in uw Power shell-profielen en de aliassen die u hebt gemaakt in de huidige sessie, typt u:

```powershell
Get-Alias
```

Als u bepaalde aliassen wilt ophalen, gebruikt u de para meter name van de cmdlet Get-Alias. Als u bijvoorbeeld aliassen wilt ophalen die beginnen met ' p ', typt u:

```powershell
Get-Alias -Name p*
```

Als u de aliassen voor een bepaald item wilt ophalen, gebruikt u de para meter definitie. Als u bijvoorbeeld de aliassen voor het Get-ChildItem-cmdlet-type wilt ophalen:

```powershell
Get-Alias -Definition Get-ChildItem
```

### <a name="get-alias-output"></a>GET-ALIAS UITVOER

Get-Alias retourneert slechts één type object, een AliasInfo-object (System. Management. Automation. AliasInfo). De naam van aliassen die geen afbreek streepje bevatten, zoals ' cd ' wordt weer gegeven in de volgende indeling:

```powershell
Get-Alias ac
```

```Output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Alias           ac -> Add-Content
```

Zo kunt u snel en eenvoudig de benodigde informatie ophalen.

De op de pijl gebaseerde alias naam indeling wordt niet gebruikt voor aliassen die een koppel teken bevatten. Dit zijn waarschijnlijk vervangende namen voor cmdlets en functies, in plaats van gebruikelijke afkortingen of bijnamen, en de auteur wil er mogelijk niet van zijn.

## <a name="alternate-names-for-commands-with-parameters"></a>ALTERNATIEVE NAMEN VOOR OPDRACHTEN MET PARA METERS

U kunt een alias toewijzen aan een cmdlet, een script, een functie of een uitvoerbaar bestand. U kunt een alias niet toewijzen aan een opdracht en de bijbehorende para meters. U kunt bijvoorbeeld een alias toewijzen aan de `Get-Eventlog` cmdlet, maar u kunt geen alias toewijzen aan de `Get-Eventlog -LogName System` opdracht.

U kunt een functie maken die de opdracht bevat. Als u een functie wilt maken, typt u het woord ' function ' gevolgd door een naam voor de functie. Typ de opdracht en plaats deze tussen accolades ( {} ).

Met de volgende opdracht maakt u bijvoorbeeld de functie syslog. Deze functie vertegenwoordigt de `Get-Eventlog -LogName System` opdracht:

```powershell
function Get-SystemEventlog {Get-Eventlog -LogName System}
Set-Alias -Name syslog -Value Get-SystemEventlog
```

U kunt nu ' syslog ' typen in plaats van de opdracht. En u kunt aliassen maken voor de nieuwe functie.

Typ voor meer informatie over functies:

```powershell
Get-Help about_Functions
```

## <a name="alias-objects"></a>ALIAS OBJECTEN

Power shell-aliassen worden vertegenwoordigd door objecten die exemplaren zijn van de klasse System. Management. Automation. AliasInfo. Zie [AliasInfo-klasse][aliasinfo] in de MSDN-bibliotheek (micro soft Developer Network) voor meer informatie over dit type object.

Als u de eigenschappen en methoden van de alias objecten wilt bekijken, moet u de aliassen ophalen.
Vervolgens kunt u ze naar de Get-Member-cmdlet sluizen. Bijvoorbeeld:

```powershell
Get-Alias | Get-Member
```

Als u de waarden van de eigenschappen van een specifieke alias, zoals de alias, wilt weer geven, moet u `dir` de alias ophalen. Vervolgens pipet u het naar de cmdlet Format-List. Met de volgende opdracht wordt bijvoorbeeld de alias ' dir ' opgehaald. Vervolgens wordt de alias door de opdracht sluizen naar de cmdlet Format-List. Vervolgens gebruikt de opdracht de eigenschaps parameter van Format-List met een Joker teken ( \* ) om alle eigenschappen van de alias weer te geven `dir` . De volgende opdracht voert deze taken uit:

```powershell
Get-Alias -Name dir | Format-List -Property *
```

## <a name="powershell-alias-provider"></a>Power shell-ALIAS PROVIDER

Power shell bevat de alias provider. Met de alias provider kunt u de aliassen in Power shell bekijken alsof ze zich op een bestandssysteem station bevonden.

De alias provider toont de alias: station. Ga naar de alias: station, type:

```powershell
Set-Location Alias:
```

Als u de inhoud van het station wilt weer geven, typt u:

```powershell
Get-ChildItem
```

Als u de inhoud van het station van een ander Power Shell-station wilt weer geven, start u het pad met de naam van het station. Neem de dubbele punt (:). Bijvoorbeeld:

```powershell
Get-ChildItem -Path Alias:
```

Als u informatie wilt ophalen over een bepaalde alias, typt u de naam van het station en de naam van de alias. Of typ een naam patroon. Als u bijvoorbeeld alle aliassen wilt ophalen die beginnen met ' p ', typt u:

```powershell
Get-ChildItem -Path Alias:p*
```

Voor meer informatie over de Power shell-alias provider typt u:

```powershell
Get-Help Alias
```

## <a name="see-also"></a>ZIE OOK

- [Nieuwe alias](xref:Microsoft.PowerShell.Utility.New-Alias)
- [Get-alias](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [Set-alias](xref:Microsoft.PowerShell.Utility.Set-Alias)
- [Exporteren-alias](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [Import-alias](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [Get-PSProvider](xref:Microsoft.PowerShell.Management.Get-PSProvider)
- [Get-PSDrive](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [about_functions](about_functions.md)
- [about_profiles](about_profiles.md)
- [about_providers](about_providers.md)

<!-- External links -->
[aliasinfo]: /dotnet/api/system.management.automation.aliasinfo

