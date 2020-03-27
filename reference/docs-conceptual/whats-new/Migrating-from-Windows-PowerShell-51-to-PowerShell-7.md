---
title: Migreren van Windows Power shell 5,1 naar Power shell 7
description: Update van Power shell 5,1 naar Power shell 7 voor uw Windows-platforms.
ms.date: 03/25/2020
ms.openlocfilehash: e04ab24d2ea94e51f4510d2e96891549c1ede5a4
ms.sourcegitcommit: 7ab6da5169765f06771493b28c44cb24a09d6776
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/26/2020
ms.locfileid: "80296527"
---
# <a name="migrating-from-windows-powershell-51-to-powershell-7"></a>Migreren van Windows Power shell 5,1 naar Power shell 7

Power shell 7 is ontworpen voor Cloud-, on-premises en hybride omgevingen en is voorzien van verbeteringen en [nieuwe functies](What-s-New-in-PowerShell-70.md).

- Installeert en voert side-by-side uit met Windows Power shell
- Verbeterde compatibiliteit met bestaande Windows Power shell-modules
- Nieuwe taal functies, zoals ternaire Opera tors en `ForEach-Object -Parallel`
- Verbeterde prestaties
- Externe toegang op basis van SSH
- Interoperabiliteit tussen verschillende platforms
- Ondersteuning voor docker-containers

Power shell 7 werkt naast Windows Power shell eenvoudig te testen en vergelijken van edities vóór de implementatie. Migratie is eenvoudig, snel en veilig. veroorzaakt.

Power shell 7 wordt ondersteund op de volgende Windows-besturings systemen:

- Windows 8,1 en 10
- Windows Server 2012, 2012 R2, 2016 en 2019

Power shell 7 wordt ook uitgevoerd op macOS en verschillende Linux-distributies. Voor een lijst met ondersteunde besturings systemen en informatie over de ondersteunings levenscyclus raadpleegt u de [levens cyclus van Power Shell-ondersteuning](/powershell/scripting/powershell-support-lifecycle).

## <a name="installing-powershell-7"></a>Power shell 7 installeren

Voor flexibiliteit en het ondersteunen van de behoeften van IT, DevOps engineers en ontwikkel aars zijn er verschillende opties beschikbaar om Power shell 7 te installeren. In de meeste gevallen kunnen de installatie opties worden beperkt tot de volgende methoden:

- Power shell implementeren met het [MSI-pakket](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)
- Power shell implementeren met behulp van het [zip-pakket](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)

> [!NOTE]
> Het MSI-pakket kan worden geïmplementeerd en bijgewerkt met beheer producten als [System Center Configuration Manager (SCCM)](/configmgr/apps/). Down load de pakketten van [github release pagina](https://github.com/PowerShell/PowerShell/releases).

Voor het implementeren van het MSI-pakket is beheerders machtigingen vereist. Het ZIP-pakket kan door elke gebruiker worden geïmplementeerd. Het ZIP-pakket is de eenvoudigste manier om Power shell 7 te installeren voor tests voordat een volledige installatie wordt uitgevoerd.

## <a name="using-powershell-7-side-by-side-with-windows-powershell-51"></a>Power shell 7 side-by-side gebruiken met Windows Power shell 5,1

Power shell 7 is ontworpen om samen te bestaan met Windows Power shell 5,1. De volgende functies zorgen ervoor dat uw investering in Power shell is beveiligd en dat de migratie naar Power shell 7 eenvoudig is.

- Afzonderlijk installatiepad en uitvoer bare naam
- Afzonderlijke PSModulePath
- Afzonderlijke profielen voor elke versie
- Verbeterde module compatibiliteit
- Nieuwe externe eind punten
- Ondersteuning voor groeps beleid
- Afzonderlijke gebeurtenis logboeken

### <a name="separate-installation-path-and-executable-name"></a>Afzonderlijk installatiepad en uitvoer bare naam

Power shell 7 wordt geïnstalleerd in een nieuwe map, waardoor gelijktijdige uitvoering kan worden uitgevoerd met Windows Power shell 5,1.

Locaties installeren op versie:

- Windows Power shell 5,1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`
- Power shell Core 6. x: `$env:ProgramFiles\PowerShell\6`
- Power shell 7: `$env:ProgramFiles\PowerShell\7`

De nieuwe locatie wordt toegevoegd aan het pad, zodat u Windows Power shell 5,1 en Power shell 7 kunt uitvoeren. Als u migreert van Power shell Core 6. x naar Power shell 7, wordt Power shell 6 verwijderd en wordt het pad vervangen.

In Windows Power Shell heeft het uitvoer bare Power shell-bestand de naam `powershell.exe`. In versie 6 en hoger wordt het uitvoer bare bestand de naam `pwsh.exe`. De nieuwe naam maakt het eenvoudig om gelijktijdige uitvoering van beide versies te ondersteunen.

### <a name="separate-psmodulepath"></a>Afzonderlijke PSModulePath

Standaard worden modules voor Windows Power shell en Power shell 7 opgeslagen op verschillende locaties. Power shell 7 combineert die locaties in de omgevings variabele `$Env:PSModulePath`. Wanneer u een module op naam importeert, controleert Power shell de locatie die is opgegeven door `$Env:PSModulePath`. Hierdoor kan Power shell 7 zowel de kern-als bureaublad modules laden.

|            Installatie bereik            |                Windows Power shell 5,1                 |             Power shell 7,0             |
| ----------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| PowerShell-modules                  | `$env:WINDIR\system32\WindowsPowerShell\v1.0\Modules` | `$PSHOME\Modules`                      |
| Gebruiker geïnstalleerd<br>AllUsers-bereik    | `$env:ProgramFiles\WindowsPowerShell\Modules`         | `$env:ProgramFiles\PowerShell\Modules` |
| Gebruiker geïnstalleerd<br>Het bereik CurrentUser | `$HOME\Documents\WindowsPowerShell\Modules`           | `$HOME\Documents\PowerShell\Modules`   |

In de volgende voor beelden ziet u de standaard waarden van `$Env:PSModulePath` voor elke versie.

- Voor Windows Power shell 5,1:

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\WindowsPowerShell\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

- Voor Power shell 7:

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\PowerShell\Modules
  C:\Program Files\PowerShell\Modules
  C:\Program Files\PowerShell\7\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

Power shell 7 bevat de Windows Power shell-paden en de Power shell 7-paden om modules te kunnen laden.

> [!NOTE]
> Er kunnen extra paden bestaan als u de omgevings variabele PSModulePath of geïnstalleerde aangepaste modules of toepassingen hebt gewijzigd.

Zie `PSModulePath` in [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences)voor meer informatie.

Zie [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules)voor meer informatie over modules.

### <a name="separate-profiles"></a>Afzonderlijke profielen

Een Power shell-profiel is een script dat wordt uitgevoerd wanneer Power shell wordt gestart. Met dit script past u uw omgeving aan door opdrachten, aliassen, functies, variabelen, modules en Power Shell-stations toe te voegen. Het profiel script maakt deze aanpassingen beschikbaar in elke sessie, zonder dat u ze hand matig opnieuw hoeft te maken.

Het pad naar de locatie van het profiel is gewijzigd in Power shell 7.

- In Windows Power shell 5,1 is de locatie van het profiel `$HOME\Documents\WindowsPowerShell`.
- In Power shell 7 is de locatie van het profiel `$HOME\Documents\PowerShell`.

De bestands namen van het profiel zijn ook gewijzigd:

   ```powershell
   PS> $PROFILE | Select-Object *Host* | Format-List

   AllUsersAllHosts       : C:\Program Files\PowerShell\7\profile.ps1
   AllUsersCurrentHost    : C:\Program Files\PowerShell\7\Microsoft.PowerShell_profile.ps1
   CurrentUserAllHosts    : C:\Users\<user>\Documents\PowerShell\profile.ps1
   CurrentUserCurrentHost : C:\Users\<user>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
   ```

[About_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)voor meer informatie.

### <a name="powershell-7-compatibility-with-windows-powershell-51-modules"></a>Compatibiliteit met Power shell 7 met Windows Power shell 5,1-modules

De meeste modules die u in Windows Power shell 5,1 gebruikt, werken al met Power shell 7, met inbegrip van Azure PowerShell en Active Directory. We blijven samen werken met andere teams om native Power shell 7-ondersteuning toe te voegen voor meer modules, waaronder Microsoft Graph, Office 365 en anderen. Voor de huidige lijst met ondersteunde modules raadpleegt u compatibiliteit met de [module Power shell 7](/powershell/scripting/whats-new/module-compatibility).

[!NOTE]
> In Windows hebben we ook een **UseWindowsPowerShell** -Schakel optie toegevoegd aan `Import-Module` om de overgang naar Power shell 7 te vereenvoudigen voor degenen die gebruikmaken van incompatibele modules. Zie [about_Windows_PowerShell_Compatibility](/powershell/modules/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility)voor meer informatie over deze functionaliteit.

### <a name="powershell-remoting"></a>Externe communicatie met Power shell

Met externe communicatie van Power shell kunt u elke Power shell-opdracht op een of meer externe computers uitvoeren. U kunt permanente verbindingen tot stand brengen, interactieve sessies starten en scripts uitvoeren op externe computers.

#### <a name="ws-management-remoting"></a>Externe communicatie van WS-Management

Windows Power shell 5,1 en lager gebruiken het WS-Management-Protocol (WSMAN) voor verbindings onderhandeling en gegevens overdracht. Windows Remote Management (WinRM) maakt gebruik van het WSMAN-protocol. Als WinRM is ingeschakeld, gebruikt Power shell 7 het bestaande Windows Power shell 5,1-eind punt met de naam `Microsoft.PowerShell` voor externe verbindingen. Als u Power shell 7 wilt bijwerken om een eigen eind punt op te halen, voert u de `Enable-PSRemoting`-cmdlet uit. Zie voor meer informatie over het maken van verbinding met specifieke eind punten [WS-Management Remoting in Power shell core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)

Als u externe toegang tot Windows Power shell wilt gebruiken, moet u de computer configureren voor extern beheer.
Zie [over externe vereisten](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)voor meer informatie, waaronder instructies.

Zie voor meer informatie over het werken met externe communicatie [over externe](/powershell/module/microsoft.powershell.core/about/about_remote)

#### <a name="ssh-based-remoting"></a>Externe toegang op basis van SSH

Op SSH gebaseerde externe toegang is toegevoegd aan Power shell Core 6. x ter ondersteuning van andere besturings systemen die geen Windows systeem eigen onderdelen zoals **WinRM**kunnen gebruiken. Externe SSH-processen maken een Power shell-hostproces op de doel computer als een SSH-subsysteem. Zie voor meer informatie en voor beelden over het instellen van op SSH gebaseerde externe toegang op Windows of Linux: [Power shell Remoting via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

> [!NOTE]
> De PowerShell Gallery (PSGallery) bevat een module en cmdlet waarmee op SSH gebaseerde externe toegang automatisch wordt geconfigureerd. Installeer de `Microsoft.PowerShell.RemotingTools`-module van de [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) en voer de `Enable-SSH`-cmdlet uit.

De cmdlets `New-PSSession`, `Enter-PSSession`en `Invoke-Command` hebben nieuwe parameter sets voor de ondersteuning van SSH-verbindingen.

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Als u een externe sessie wilt maken, geeft u de doel computer op met de para meter **hostname** en geeft u de gebruikers naam met de **naam**van de gebruiker. Wanneer de cmdlets interactief worden uitgevoerd, wordt u gevraagd een wacht woord op te vragen.

```powershell
Enter-PSSession -HostName <Computer> -UserName <Username>
```

U kunt ook bij het gebruik van de para meter **hostname** de gebruikers naam gegevens opgeven, gevolgd door het apen staartje (@), gevolgd door de naam van de computer.

```powershell
Enter-PSSession -HostName <Username>@<Computer>
```

U kunt SSH-sleutel verificatie instellen met behulp van een persoonlijke-sleutel bestand **met de para** meter sleutelpad.
Zie [OpenSSH key management](/windows-server/administration/openssh/openssh_keymanagement)(Engelstalig) voor meer informatie.

### <a name="group-policy-supported"></a>groepsbeleid ondersteund

Power shell bevat groepsbeleid instellingen die u helpen bij het definiëren van consistente optie waarden voor servers in een bedrijfs omgeving. Deze instellingen omvatten:

- Console sessie configuratie: Hiermee stelt u een configuratie-eind punt in waarin Power shell wordt uitgevoerd.
- Module logboek registratie inschakelen: Hiermee wordt de eigenschap LogPipelineExecutionDetails van modules ingesteld.
- Power shell-script blok logboek registratie inschakelen: Hiermee wordt gedetailleerde logboek registratie van alle Power shell-scripts ingeschakeld.
- Script uitvoering inschakelen: Hiermee stelt u het Power shell-uitvoerings beleid in.
- Power shell transcriptie inschakelen: Hiermee wordt de invoer en uitvoer van Power shell-opdrachten vastgelegd in Transcripten op basis van tekst.
- Het standaardpad instellen voor update-Help: Hiermee stelt u de bron in op Help-informatie voor een directory, niet via internet.

Zie [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings)voor meer informatie.

Power shell 7 bevat groepsbeleid sjablonen en een installatie script in `$PSHOME`.

Groepsbeleid-hulpprogram ma's gebruiken beheer sjabloon bestanden (`.admx`, `.adml`) om beleids instellingen in de gebruikers interface in te vullen. Hiermee kunnen beheerders beleids instellingen op basis van het REGI ster beheren. Met het script `InstallPSCorePolicyDefinitions.ps1` wordt Power shell core-Beheersjablonen geïnstalleerd op de lokale computer.

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/27/2020 12:38 AM          15861 InstallPSCorePolicyDefinitions.ps1
-a---           2/27/2020 12:28 AM           9675 PowerShellCoreExecutionPolicy.adml
-a---           2/27/2020 12:28 AM           6201 PowerShellCoreExecutionPolicy.admx
```

### <a name="separate-event-logs"></a>Afzonderlijke gebeurtenis logboeken

Windows Power shell en Power shell 7-logboek gebeurtenissen voor het scheiden van gebeurtenis Logboeken. Gebruik de volgende opdracht om een lijst met de Power shell-logboeken op te halen.

```powershell
Get-WinEvent -ListLog *PowerShell*
```

Zie [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows)voor meer informatie.

## <a name="improved-editing-experience-with-visual-studio-code"></a>Verbeterde bewerkings ervaring met Visual Studio code

[Visual Studio code (VSCode)](https://code.visualstudio.com/) met de [Power shell-extensie](https://code.visualstudio.com/docs/languages/powershell) is de ondersteunde script omgeving voor Power shell 7. De Windows Power shell Integrated Scripting Environment (ISE) biedt alleen ondersteuning voor Windows Power shell.

De bijgewerkte Power shell-extensie bevat:

- Nieuwe ISE-compatibiliteits modus
- PSReadLine in de geïntegreerde console, met inbegrip van syntaxis markering, meerdere regels bewerken en terug zoeken
- Verbeteringen in stabiliteit en prestaties
- Nieuwe code lens-integratie
- Verbeterde automatische aanvulling van paden

Als u de overgang naar Visual Studio code eenvoudiger wilt maken, gebruikt u de functie **ISE-modus inschakelen** die beschikbaar is in het **opdracht palet**. Deze functie schakelt VSCode in een ISE-opmaak. De ISE-indeling biedt u alle nieuwe functies en mogelijkheden van Power shell in een vertrouwde gebruikers ervaring.

Als u wilt overschakelen naar de nieuwe ISE-indeling, drukt u op <kbd>Ctrl</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd> om het **opdracht palet**te openen, typt u `PowerShell` en selecteert u **Power shell: modus ISE inschakelen**.

Als u de indeling wilt instellen op de oorspronkelijke indeling, opent u het **opdracht palet**en selecteert u **Power shell: de modus ISE uitschakelen (standaard instellingen herstellen)** .

Zie [de ISE-ervaring repliceren in Visual Studio code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode) voor meer informatie over het aanpassen van de VSCode-indeling naar ISE.

> [!NOTE]
> Er zijn geen plannen om de ISE bij te werken met nieuwe functies. De ISE is nu een functie die door de gebruiker kan worden verwijderd in de nieuwste versies van Windows 10 en Windows Server. Er zijn geen plannen om de ISE permanent te verwijderen. Het Power shell-team en de bijbehorende partners zijn gericht op het verbeteren van de scripting ervaring in de Power shell-extensie voor Visual Studio code.

## <a name="next-steps"></a>Volgende stappen

U kunt met de kennis die effectief kan worden gemigreerd, [Power shell 7 nu installeren](/powershell/scripting/install/installing-powershell-core-on-windows) .
