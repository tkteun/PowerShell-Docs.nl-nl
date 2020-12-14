---
description: Beschrijft de groepsbeleid-instellingen voor Power shell
Locale: en-US
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_group_policy_settings?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Group_Policy_Settings
ms.openlocfilehash: 5ca13d22c69213dd8bae57a0dd08587c9c2b1541
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705381"
---
# <a name="about-group-policy-settings"></a>Over groepsbeleid-instellingen

## <a name="short-description"></a>Korte beschrijving
Beschrijft de groepsbeleid-instellingen voor Power shell

## <a name="long-description"></a>Lange beschrijving

Power shell bevat groepsbeleid instellingen die u helpen bij het definiëren van consistente configuratie waarden voor Windows-computers in een bedrijfs omgeving.

De Power shell-groepsbeleid-instellingen bevinden zich in de volgende groepsbeleid paden:

```
Computer Configuration\
  Administrative Templates\
    PowerShell Core

User Configuration\
  Administrative Templates\
    PowerShell Core
```

Instellingen voor groeps beleid in het pad gebruikers configuratie hebben voor rang op groepsbeleid instellingen in het pad computer configuratie.

Power shell 7 bevat groepsbeleid sjablonen en een installatie script in `$PSHOME` .

Groepsbeleid-hulpprogram ma's gebruiken beheer sjabloon bestanden ( `.admx` , `.adml` ) om beleids instellingen in de gebruikers interface in te vullen. Hiermee kunnen beheerders beleids instellingen op basis van het REGI ster beheren. `InstallPSCorePolicyDefinitions.ps1`Met het script wordt **Power shell Core-Beheersjablonen** op de lokale computer geïnstalleerd.

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode       LastWriteTime         Length Name
----       -------------         ------ ----
-a---      2/27/2020 12:38 AM     15861 InstallPSCorePolicyDefinitions.ps1
-a---      2/27/2020 12:28 AM      9675 PowerShellCoreExecutionPolicy.adml
-a---      2/27/2020 12:28 AM      6201 PowerShellCoreExecutionPolicy.admx
```

Nadat u de sjablonen hebt geïnstalleerd, kunt u deze instellingen bewerken in de groepsbeleid editor ( `gpedit.msc` ).

De beleids regels zijn als volgt:

- Console sessie configuratie: Hiermee stelt u een configuratie-eind punt in waarin Power shell wordt uitgevoerd.
- Module logboek registratie inschakelen: Hiermee wordt de eigenschap **LogPipelineExecutionDetails** van modules ingesteld.
- Power shell-script blok logboek registratie inschakelen: Hiermee wordt gedetailleerde logboek registratie van alle Power shell-scripts ingeschakeld.
- Script uitvoering inschakelen: Hiermee stelt u het Power shell-uitvoerings beleid in.
- Power shell transcriptie inschakelen: Hiermee wordt de invoer en uitvoer van Power shell-opdrachten vastgelegd in Transcripten op basis van tekst.
- Het standaardpad voor de bron instellen `Update-Help` : Hiermee stelt u de bron in op Help-informatie voor een directory, niet via internet.

Elke Power shell-groepsbeleid instelling heeft een optie (' Windows Power shell-beleids instelling gebruiken ') om de waarde te gebruiken van een vergelijk bare Windows Power shell-groepsbeleid instelling die zich in de volgende groepsbeleid paden bevindt:

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

> [!NOTE]
> Deze **Power shell core-Beheersjablonen** bevatten geen instellingen voor Windows Power shell. Voor meer informatie over het verkrijgen van andere sjablonen en het configureren van groeps beleid raadpleegt [u het centraal archief maken en beheren voor groepsbeleid Beheersjablonen in Windows][gpstore].

## <a name="console-session-configuration"></a>Configuratie van console sessie

Met de beleids instelling **console sessie configuratie** geeft u een configuratie-eind punt op waarin Power shell wordt uitgevoerd. Dit kan elk eind punt zijn dat is geregistreerd op de lokale computer, met inbegrip van de standaard externe communicatie-eind punten in Power shell of een aangepast eind punt met specifieke mogelijkheden voor de gebruikersrol.

## <a name="turn-on-module-logging"></a>Module logboek registratie inschakelen

Met de beleids instelling **module logboek registratie inschakelen** wordt logboek registratie ingeschakeld voor geselecteerde Power shell-modules. De instelling is effectief in alle sessies op alle betrokken computers.

Als u deze beleids instelling inschakelt en een of meer modules opgeeft, worden de pijplijn uitvoerings gebeurtenissen voor de opgegeven modules vastgelegd in het Windows Power shell-aanmeld Logboeken.

Als u deze beleids instelling uitschakelt, wordt het vastleggen van uitvoerings gebeurtenissen uitgeschakeld voor alle Power shell-modules.

Als deze beleids instelling niet is geconfigureerd, bepaalt de eigenschap **LogPipelineExecutionDetails** van elke module of de uitvoerings gebeurtenissen van een module worden vastgelegd. De eigenschap **LogPipelineExecutionDetails** van alle modules is standaard ingesteld op ONWAAR.

Als u module logboek registratie wilt inschakelen voor een module, gebruikt u de volgende opdracht indeling. De module moet in de sessie worden geïmporteerd en de instelling is alleen effectief in de huidige sessie.

```powershell
Import-Module <Module-Name>
(Get-Module <Module-Name>).LogPipelineExecutionDetails = $true
```

Als u module logboek registratie wilt inschakelen voor alle sessies op een bepaalde computer, voegt u de vorige opdrachten toe aan het Power shell-profiel ' alle gebruikers ' ( `$Profile.AllUsersAllHosts` ).

Zie [about_Modules](about_Modules.md)voor meer informatie over het vastleggen van module-Logboeken.

## <a name="turn-on-powershell-script-block-logging"></a>Logboek registratie van Power shell-script blokken inschakelen

Met de beleids instelling **logboek registratie van Power shell-script blok inschakelen** wordt logboek registratie van alle Power shell-script invoer naar het gebeurtenis logboek van micro soft-Windows-Power shell/operationeel ingeschakeld. Als u deze beleids instelling inschakelt, wordt de verwerking van opdrachten, script blokken, functies en scripts door Power shell core geregistreerd, ongeacht of deze interactief of via Automation is aangeroepen.

Als u deze beleidsinstelling uitschakelt, wordt logboekregistratie van PowerShell-scriptinvoer uitgeschakeld. Als u de logboekregistratie voor het aanroepen van script blokkeren inschakelt, worden gebeurtenissen door PowerShell vastgelegd bij het aanroepen van een opdracht, scriptblokkering, functie of bij het starten of stoppen van een script. Als het aanroeplogbestand wordt ingeschakeld, wordt er een groot aantal gebeurtenislogboeken gegenereerd.

## <a name="turn-on-script-execution"></a>Script uitvoering inschakelen

Met de instelling **Script Execution** Policy wordt het uitvoerings beleid voor computers en gebruikers ingesteld, waarmee wordt bepaald welke scripts mogen worden uitgevoerd.

Als u de beleids instelling inschakelt, kunt u een van de volgende beleids instellingen selecteren.

- **Alleen ondertekende scripts toestaan** dat scripts alleen kunnen worden uitgevoerd als ze door een vertrouwde uitgever zijn ondertekend. Deze beleids instelling is gelijk aan het alles ondertekend-uitvoerings beleid.

- Met **lokale scripts en externe ondertekende scripts** kunnen alle lokale scripts worden uitgevoerd. Scripts die afkomstig zijn van Internet, moeten zijn ondertekend door een vertrouwde uitgever. Deze beleids instelling is gelijk aan het RemoteSigned-uitvoerings beleid.

- **Alle scripts toestaan** dat alle scripts kunnen worden uitgevoerd. Deze beleids instelling is gelijk aan het beleid voor onbeperkte uitvoering.

Als u deze beleids instelling uitschakelt, mogen er geen scripts worden uitgevoerd. Deze beleids instelling is gelijk aan het beleid voor beperkte uitvoering.

Als u deze beleids instelling uitschakelt of niet configureert, bepaalt het uitvoerings beleid dat is ingesteld voor de computer of gebruiker door de `Set-ExecutionPolicy` cmdlet, of scripts mogen worden uitgevoerd. De standaard waarde is beperkt.

Zie [about_Execution_Policies](about_Execution_Policies.md)voor meer informatie.

## <a name="turn-on-powershell-transcription"></a>Power shell transcriptie inschakelen

Met de beleids instelling **Power shell transcriptie inschakelen** kunt u de invoer en uitvoer van Power shell core-opdrachten vastleggen in Transcripten op basis van tekst. Als u deze beleids instelling inschakelt, schakelt Power shell core transcriptie-logboek registratie in voor Power shell core en andere toepassingen die gebruikmaken van de Power shell Core-Engine. Power shell core registreert standaard transcript uitvoer naar de map Mijn documenten van elke gebruiker, met een bestands naam die ' PowerShell_transcript ' bevat, samen met de computer naam en tijd gestart.
Het inschakelen van dit beleid is gelijk aan het aanroepen van de Start-Transcript cmdlet op elke Power shell-kern sessie.

Als u deze beleids instelling uitschakelt, wordt de transcriptie-logboek registratie van op Power shell gebaseerde toepassingen standaard uitgeschakeld, maar u kunt transcripten nog steeds inschakelen via de Start-Transcript-cmdlet.

Als u de instelling output directory gebruikt om logboek registratie van transcriptie in te scha kelen op een gedeelde locatie, moet u ervoor zorgen dat u de toegang tot die Directory beperkt om te voor komen dat gebruikers de transcripten van andere gebruikers of computers weer geven.

## <a name="set-the-default-source-path-for-update-help"></a>Het standaard bronpad instellen voor Update-Help

Het **standaard bronpad instellen voor update-Help** beleids instelling stelt een standaard waarde in voor de para meter **SourcePath** van de `Update-Help` cmdlet.
Deze instelling voor komt dat gebruikers de `Update-Help` cmdlet gebruiken om Help-bestanden van Internet te downloaden.

> [!NOTE]
> Deze groepsbeleid instelling wordt weer gegeven onder **computer configuratie** en **gebruikers configuratie**. Maar alleen de instelling groepsbeleid onder **computer configuratie** is van kracht. De instelling groepsbeleid onder **gebruikers configuratie** wordt genegeerd.

De `Update-Help` cmdlet downloadt en installeert de nieuwste Help-bestanden voor Power shell-modules en installeert deze op de computer. Standaard `Update-Help` downloadt nieuwe Help-bestanden van een Internet locatie die is opgegeven door de module.

U kunt de cmdlet echter gebruiken `Save-Help` om de nieuwste Help-bestanden te downloaden naar een bestandssysteem locatie, zoals een netwerk share. vervolgens gebruikt u de `Update-Help` cmdlet om de Help-bestanden van de bestandssysteem locatie op te halen en te installeren op de computer. De para meter **SourcePath** van de `Update-Help` cmdlet specificeert de locatie van het bestands systeem.

Als u een standaard waarde voor de para meter **SourcePath** opgeeft, voegt deze Groepsbeleid impliciet de para meter **SourcePath** toe aan alle `Update-Help` opdrachten. Gebruikers kunnen de specifieke locatie van het bestands systeem die is opgegeven als de standaard waarde overschrijven door een andere locatie voor het bestands systeem in te voeren.
Maar ze kunnen de para meter **SourcePath** niet uit de `Update-Help` opdracht verwijderen.

Als u deze beleids instelling inschakelt, kunt u een standaard waarde opgeven voor de para meter **SourcePath** . Voer een locatie voor het bestands systeem in.

Als u deze beleids instelling uitschakelt of niet configureert, is er geen standaard waarde voor de para meter **SourcePath** van de `Update-Help` cmdlet. Gebruikers kunnen Help downloaden van Internet of vanaf elke locatie van een bestands systeem.

Zie [about_Updatable_Help](about_Updatable_Help.md) voor meer informatie.

## <a name="keywords"></a>Trefwoorden

about_Group_Policies about_GroupPolicy

## <a name="see-also"></a>Zie ook

[RFC-kern beleid van Power shell](https://github.com/PowerShell/PowerShell-RFC/blob/master/4-Experimental-Accepted/RFC0041-Policy.md)

[about_Execution_Policies](about_Execution_Policies.md)

[about_Modules](about_Modules.md)

[about_Updatable_Help](about_Updatable_Help.md)

[Get-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Get-module](xref:Microsoft.PowerShell.Core.Get-Module)

[Update-Help](xref:Microsoft.PowerShell.Core.Update-Help)

[Opslaan-Help](xref:Microsoft.PowerShell.Core.Save-Help)

<!-- link references -->
[gpstore]: https://support.microsoft.com/help/3087759

