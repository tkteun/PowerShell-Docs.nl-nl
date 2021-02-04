---
description: Hiermee voor komt u dat een script wordt uitgevoerd zonder de vereiste elementen.
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_requires?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Requires
ms.openlocfilehash: d340de615923437bb3e29c1984ef8849fe03a40e
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490889"
---
# <a name="about-requires"></a>Over vereist

## <a name="short-description"></a>Korte beschrijving
Hiermee voor komt u dat een script wordt uitgevoerd zonder de vereiste elementen.

## <a name="long-description"></a>Lange beschrijving

`#Requires`Met deze instructie wordt voor komen dat een script wordt uitgevoerd, tenzij aan de Power shell-versie, modules (en versie), modules (en versie) en aan de editie vereisten wordt voldaan. Als niet aan de vereisten wordt voldaan, voert Power shell het script niet uit.

### <a name="syntax"></a>Syntax

```
#Requires -Version <N>[.<n>]
#Requires -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -Modules { <Module-Name> | <Hashtable> }
#Requires -PSEdition <PSEdition-Name>
#Requires -ShellId <ShellId> -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -RunAsAdministrator
```

Zie [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements)voor meer informatie over de syntaxis.

### <a name="rules-for-use"></a>Regels voor gebruik

Een script kan meer dan één `#Requires` instructie bevatten. De `#Requires` instructies kunnen op elke regel in een script worden weer gegeven.

Als u een `#Requires` instructie in een functie plaatst, wordt het bereik ervan niet beperkt. Alle `#Requires` instructies worden altijd globaal toegepast en moeten worden voldaan voordat het script kan worden uitgevoerd.

> [!WARNING]
> Hoewel een `#Requires` instructie op een regel in een script kan worden weer gegeven, heeft de positie in een script geen invloed op de volg orde van de toepassing. De algemene status `#Requires` van de instructie moet worden voldaan voordat de uitvoering van het script wordt uitgevoerd.

Voorbeeld:

```powershell
Get-Module AzureRM.Netcore | Remove-Module
#Requires -Modules AzureRM.Netcore
```

U kunt denken dat de bovenstaande code niet moet worden uitgevoerd omdat de vereiste module vóór de `#Requires` instructie is verwijderd. Er moest echter wel `#Requires` aan de status worden voldaan voordat het script zelfs kan worden uitgevoerd. De vereiste status is ongeldig voor de eerste regel van het script.

### <a name="parameters"></a>Parameters

#### <a name="-assembly-assembly-path--net-assembly-specification"></a>-Assembly \<Assembly path> |\<.NET assembly specification>

> [!IMPORTANT]
> De `-Assembly` syntaxis is afgeschaft. Deze functie is niet van toepassing. De syntaxis is toegevoegd aan Power shell 5,1, maar de ondersteunende code werd nooit geïmplementeerd. De syntaxis wordt nog steeds geaccepteerd voor achterwaartse compatibiliteit.

Hiermee geeft u het pad naar het DLL-bestand van de assembly of een .NET-assembly-naam op. De **Assembly** -para meter is geïntroduceerd in power shell 5,0. Voor meer informatie over .NET-assembly's raadpleegt u [Assembly namen](/dotnet/standard/assembly/names).

Bijvoorbeeld:

```
#Requires -Assembly path\to\foo.dll
```

```
#Requires -Assembly "System.Management.Automation, Version=3.0.0.0,
  Culture=neutral, PublicKeyToken=31bf3856ad364e35"
```

#### <a name="-version-nn"></a>-Versie \<N\> [. \<n\> ]

Hiermee geeft u de mini maal vereiste versie van Power shell voor het script. Voer een primair versie nummer en een optioneel secundair versie nummer in.

Bijvoorbeeld:

```powershell
#Requires -Version 6.0
```

#### <a name="-pssnapin-pssnapin-name--version-nn"></a>-PSSnapin \<PSSnapin-Name\> [-Version \<N\> [. \<n\> ]]

Hiermee geeft u een Power shell-module op die door het script wordt vereist. Voer de naam van de module en een optioneel versie nummer in.

Bijvoorbeeld:

```powershell
#Requires -PSSnapin DiskSnapin -Version 1.2
```

#### <a name="-modules-module-name--hashtable"></a>-Modules \<Module-Name\> |\<Hashtable\>

Hiermee geeft u Power shell-modules op die door het script worden vereist. Voer de module naam en een optioneel versie nummer in.

Als de vereiste modules zich niet in de huidige sessie bevinden, worden ze door Power shell geïmporteerd.
Als de modules niet kunnen worden geïmporteerd, genereert Power shell een afsluit fout.

Voor elke module typt u de module naam ( \<String\> ) of een hash-tabel. De waarde kan bestaan uit een combi natie van teken reeksen en hash-tabellen. De hash-tabel bevat de volgende sleutels.

- `ModuleName` - **Vereist** Hiermee geeft u de module naam op.
- `GUID` - **Optioneel** Hiermee geeft u de GUID van de module.
- Het is ook **vereist** om een van de drie onderstaande sleutels op te geven. Deze sleutels kunnen niet tegelijk worden gebruikt.
  - `ModuleVersion` -Hiermee geeft u een mini maal toegestane versie van de module op.
  - `RequiredVersion` -Hiermee geeft u een exacte, vereiste versie van de module op.
  - `MaximumVersion` -Hiermee geeft u de Maxi maal toegestane versie van de module op.

> [!NOTE]
> `RequiredVersion` is toegevoegd in Windows Power shell 5,0.
> `MaximumVersion` is toegevoegd in Windows Power shell 5,1.

Bijvoorbeeld:

Vereisen dat `AzureRM.Netcore` (versie `0.12.0` of hoger) is geïnstalleerd.

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; ModuleVersion="0.12.0" }
```

Vereisen dat `AzureRM.Netcore` (**alleen** versie `0.12.0` ) is geïnstalleerd.

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12.0" }
```

Vereist dat `AzureRM.Netcore` (versie `0.12.0` of lager) is geïnstalleerd.

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; MaximumVersion="0.12.0" }
```

Vereisen dat elke versie van `AzureRM.Netcore` en `PowerShellGet` is geïnstalleerd.

```powershell
#Requires -Modules AzureRM.Netcore, PowerShellGet
```

Wanneer u de `RequiredVersion` sleutel gebruikt, moet u ervoor zorgen dat uw versie teken reeks precies overeenkomt met de versie teken reeks die u nodig hebt.

```powershell
Get-Module AzureRM.Netcore -ListAvailable
```

```Output
    Directory: /home/azureuser/.local/share/powershell/Modules

ModuleType Version Name            PSEdition ExportedCommands
---------- ------- ----            --------- ----------------
Script     0.12.0  AzureRM.Netcore Core
```

Het volgende voor beeld mislukt omdat **0,12** niet exact overeenkomt met **0.12.0**.

```powershell
#Requires -Modules @{ ModuleName="AzureRM.Netcore"; RequiredVersion="0.12" }
```

#### <a name="-psedition-psedition-name"></a>-PSEdition \<PSEdition-Name\>

Hiermee geeft u een Power shell-editie op die door het script wordt vereist. Geldige waarden zijn **kern geheugen** voor Power shell core en **Desktop** voor Windows Power shell.

Bijvoorbeeld:

```powershell
#Requires -PSEdition Core
```

#### <a name="-shellid"></a>-ShellId

Hiermee geeft u de shell op die door het script wordt vereist. Voer de shell-ID in. Als u de para meter **ShellId** gebruikt, moet u ook de para meter **PSSnapin** toevoegen.
U kunt de huidige **ShellId** vinden door de `$ShellId` Automatische variabele te doorzoeken.

Bijvoorbeeld:

```powershell
#Requires -ShellId MyLocalShell -PSSnapin Microsoft.PowerShell.Core
```

> [!NOTE]
> Deze para meter is bedoeld voor gebruik in Mini shells, die zijn afgeschaft.

#### <a name="-runasadministrator"></a>-RunAsAdministrator

Wanneer deze switch parameter wordt toegevoegd aan uw `#Requires` -instructie, wordt opgegeven dat de Power shell-sessie waarin u het script uitvoert, moet worden gestart met verhoogde gebruikers rechten. De para meter **RunAsAdministrator** wordt genegeerd op een niet-Windows-besturings systeem. De para meter **RunAsAdministrator** is geïntroduceerd in power Shell 4,0.

Bijvoorbeeld:

```powershell
#Requires -RunAsAdministrator
```

### <a name="examples"></a>Voorbeelden

Het volgende script heeft twee `#Requires` instructies. Als de vereisten die zijn opgegeven in beide instructies niet worden voldaan, wordt het script niet uitgevoerd. Elke `#Requires` instructie moet het eerste item op een regel zijn:

```powershell
#Requires -Modules AzureRM.Netcore
#Requires -Version 6.0
Param
(
    [parameter(Mandatory=$true)]
    [String[]]
    $Path
)
...
```

## <a name="see-also"></a>Zie ook

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Language_Keywords](about_Language_Keywords.md)
