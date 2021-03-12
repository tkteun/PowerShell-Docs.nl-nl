---
description: Hierin wordt beschreven hoe u een Power shell-profiel maakt en gebruikt.
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Profiles
ms.openlocfilehash: 61458b60767f2bd51342546b74eb408433b8d29a
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195968"
---
# <a name="about-profiles"></a>Over profielen

## <a name="short-description"></a>Korte beschrijving
Hierin wordt beschreven hoe u een Power shell-profiel maakt en gebruikt.

## <a name="long-description"></a>Lange beschrijving

U kunt een Power shell-profiel maken om uw omgeving aan te passen en om sessie-specifieke elementen toe te voegen aan elke Power shell-sessie die u start.

Een Power shell-profiel is een script dat wordt uitgevoerd wanneer Power shell wordt gestart. U kunt het profiel als een aanmeldings script gebruiken om de omgeving aan te passen. U kunt opdrachten, aliassen, functies, variabelen, modules, modules en Power Shell-stations toevoegen. U kunt ook andere sessie-specifieke elementen aan uw profiel toevoegen, zodat deze beschikbaar zijn in elke sessie, zonder dat u ze hoeft te importeren of opnieuw te maken.

Power shell ondersteunt meerdere profielen voor gebruikers en hosttoepassingen. De profielen worden echter niet voor u gemaakt. In dit onderwerp worden de profielen beschreven, en wordt beschreven hoe u profielen op uw computer maakt en onderhoudt.

Hierin wordt uitgelegd hoe u de para meter geen **profiel** van de Power shell-console (PowerShell.exe) kunt gebruiken om Power shell zonder profielen te starten. En wordt het effect van het Power shell-uitvoerings beleid op profielen uitgelegd.

## <a name="the-profile-files"></a>De profiel bestanden

Power shell ondersteunt meerdere profiel bestanden. Power shell-host-Program ma's kunnen ook hun eigen platformspecifieke profielen ondersteunen.

De Power shell-console ondersteunt bijvoorbeeld de volgende basis profiel bestanden. De profielen worden in volg orde van prioriteit weer gegeven. Het eerste profiel heeft de hoogste prioriteit.

|Beschrijving               | Pad                                          |
|--------------------------|-----------------------------------------------|
|Alle gebruikers, alle hosts      |$PSHOME \\Profile.ps1                           |
|Alle gebruikers, huidige host   |$PSHOME \\Microsoft.PowerShell_profile.ps1      |
|Huidige gebruiker, alle hosts   |$Home \\ [mijn] documenten \\ Power shell- \\Profile.ps1 |
|Huidige gebruiker, huidige host|$Home \\ [mijn] documenten \\ Power shell\\<br>Microsoft.PowerShell_profile.ps1 |

De profiel paden bevatten de volgende variabelen:

- De `$PSHOME` variabele waarin de installatie directory voor Power shell wordt opgeslagen
- De `$Home` variabele, waarin de basismap van de huidige gebruiker wordt opgeslagen

Daarnaast kunnen andere Program ma's die Power shell hosten hun eigen profielen ondersteunen. Visual Studio code ondersteunt bijvoorbeeld de volgende sitespecifieke profielen.

|Beschrijving               | Pad                                     |
|--------------------------|------------------------------------------|
|Alle gebruikers, huidige host   |$PSHOME \\Microsoft.VSCode_profile.ps1|
|Huidige gebruiker, huidige host|$Home \\ [mijn] documenten \\ Power shell\\<br>Microsoft.VSCode_profile.ps1|

In de Help van Power shell is het profiel ' CurrentUser, Current Host ' het profiel dat het vaakst wordt aangeduid als ' uw Power shell-profiel '.

## <a name="the-profile-variable"></a>De variabele $PROFILE

De `$PROFILE` Automatische variabele slaat de paden op naar de Power shell-profielen die beschikbaar zijn in de huidige sessie.

Als u een profielpad wilt weer geven, geeft u de waarde van de `$PROFILE` variabele weer. U kunt ook de `$PROFILE` variabele in een opdracht gebruiken om een pad weer te geven.

De `$PROFILE` variabele slaat het pad op naar het profiel huidige gebruiker, huidige host. De andere profielen worden opgeslagen in notitie-eigenschappen van de `$PROFILE` variabele.

De `$PROFILE` variabele bevat bijvoorbeeld de volgende waarden in de Windows Power shell-console.

|Beschrijving                |Name                              |
|---------------------------|----------------------------------|
|Huidige gebruiker, huidige host |`$PROFILE`                        |
|Huidige gebruiker, huidige host |`$PROFILE.CurrentUserCurrentHost` |
|Huidige gebruiker, alle hosts    |`$PROFILE.CurrentUserAllHosts`    |
|Alle gebruikers, huidige host    |`$PROFILE.AllUsersCurrentHost`    |
|Alle gebruikers, alle hosts       |`$PROFILE.AllUsersAllHosts`       |

Omdat de waarden van de `$PROFILE` variabele wijzigen voor elke gebruiker en in elke hosttoepassing, moet u ervoor zorgen dat u de waarden van de profiel variabelen weergeeft in elke Power shell-hosttoepassing die u gebruikt.

Als u de huidige waarden van de variabele wilt weer geven `$PROFILE` , typt u:

```powershell
$PROFILE | Get-Member -Type NoteProperty
```

U kunt de `$PROFILE` variabele in veel opdrachten gebruiken. Met de volgende opdracht wordt bijvoorbeeld het profiel ' huidige gebruiker, huidige host ' geopend in Klad blok:

```powershell
notepad $PROFILE
```

Met de volgende opdracht wordt bepaald of het profiel ' alle gebruikers, alle hosts ' is gemaakt op de lokale computer:

```powershell
Test-Path -Path $PROFILE.AllUsersAllHosts
```

## <a name="how-to-create-a-profile"></a>Een profiel maken

Als u een Power shell-profiel wilt maken, gebruikt u de volgende opdracht indeling:

```powershell
if (!(Test-Path -Path <profile-name>)) {
  New-Item -ItemType File -Path <profile-name> -Force
}
```

Als u bijvoorbeeld een profiel voor de huidige gebruiker in de huidige Power shell-hosttoepassing wilt maken, gebruikt u de volgende opdracht:

```powershell
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
```

In deze opdracht `If` voor komt u dat u een bestaand profiel kunt overschrijven met de instructie. Vervang de waarde van de \<profile-path\> tijdelijke aanduiding door het pad naar het profiel bestand dat u wilt maken.

> [!NOTE]
> Als u profielen voor alle gebruikers wilt maken in Windows Vista en latere versies van Windows, start u Power shell met de optie **als administrator uitvoeren** .

## <a name="how-to-edit-a-profile"></a>Een profiel bewerken

U kunt elk Power shell-profiel openen in een tekst editor, zoals Klad blok.

Als u het profiel van de huidige gebruiker in de huidige Power shell-hosttoepassing in Klad blok wilt openen, typt u:

```powershell
notepad $PROFILE
```

Als u andere profielen wilt openen, geeft u de profiel naam op. Als u bijvoorbeeld het profiel voor alle gebruikers van alle hosttoepassingen wilt openen, typt u:

```powershell
notepad $PROFILE.AllUsersAllHosts
```

Sla het profiel bestand op en start Power shell opnieuw om de wijzigingen toe te passen.

## <a name="how-to-choose-a-profile"></a>Een profiel kiezen

Als u meerdere hosttoepassingen gebruikt, plaatst u de items die u in de hosttoepassingen in uw `$PROFILE.CurrentUserAllHosts` profiel gebruikt. Plaats items die specifiek zijn voor een hosttoepassing, zoals een opdracht waarmee de achtergrond kleur voor een hosttoepassing wordt ingesteld in een profiel dat specifiek is voor die hosttoepassing.

Als u een beheerder bent die Power shell voor veel gebruikers wilt aanpassen, volgt u deze richt lijnen:

- De algemene items in het `$PROFILE.AllUsersAllHosts` profiel opslaan
- Items die specifiek zijn voor een hosttoepassing opslaan in `$PROFILE.AllUsersCurrentHost` profielen die specifiek zijn voor de hosttoepassing
- Items voor bepaalde gebruikers opslaan in de gebruikersspecifieke profielen

Controleer de documentatie van de host-toepassing voor een speciale implementatie van Power shell-profielen.

## <a name="how-to-use-a-profile"></a>Een profiel gebruiken

Veel van de items die u in Power Shell maakt en de meeste opdrachten die u uitvoert, zijn alleen van invloed op de huidige sessie. Wanneer u de sessie beëindigt, worden de items verwijderd.

De sessie-specifieke opdrachten en items bevatten variabelen, voorkeurs variabelen, aliassen, functies, opdrachten (met uitzonde ring van [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)) en Power shell-modules die u aan de sessie toevoegt.

Als u deze items wilt opslaan en deze beschikbaar wilt maken in alle toekomstige sessies, voegt u deze toe aan een Power shell-profiel.

Een ander algemeen gebruik voor profielen is het opslaan van veelgebruikte functies, aliassen en variabelen. Wanneer u de items in een profiel opslaat, kunt u ze in elke gewenste sessie gebruiken zonder ze opnieuw te maken.

## <a name="how-to-start-a-profile"></a>Een profiel starten

Wanneer u het profiel bestand opent, is het leeg. U kunt deze ook vullen met de variabelen, aliassen en opdrachten die u regel matig gebruikt.

Hier volgen enkele suggesties om aan de slag te gaan.

### <a name="add-commands-that-make-it-easy-to-open-your-profile"></a>Opdrachten toevoegen waarmee u uw profiel eenvoudig kunt openen

Dit is vooral handig als u een ander profiel gebruikt dan het profiel huidige gebruiker, huidige host. Voeg bijvoorbeeld de volgende opdracht toe:

```powershell
function Pro {notepad $PROFILE.CurrentUserAllHosts}
```

### <a name="add-a-function-that-lists-the-aliases-for-any-cmdlet"></a>Een functie toevoegen die de aliassen voor een wille keurige cmdlet vermeldt

```powershell
function Get-CmdletAlias ($cmdletname) {
  Get-Alias |
    Where-Object -FilterScript {$_.Definition -like "$cmdletname"} |
      Format-Table -Property Definition, Name -AutoSize
}
```

### <a name="customize-your-console"></a>Uw console aanpassen

```powershell
function Color-Console {
  $Host.ui.rawui.backgroundcolor = "white"
  $Host.ui.rawui.foregroundcolor = "black"
  $hosttime = (Get-ChildItem -Path $PSHOME\PowerShell.exe).CreationTime
  $hostversion="$($Host.Version.Major)`.$($Host.Version.Minor)"
  $Host.UI.RawUI.WindowTitle = "PowerShell $hostversion ($hosttime)"
  Clear-Host
}
Color-Console
```

### <a name="add-a-customized-powershell-prompt"></a>Een aangepaste Power shell-prompt toevoegen

```powershell
function Prompt
{
$env:COMPUTERNAME + "\" + (Get-Location) + "> "
}
```

Zie [about_Prompts](about_Prompts.md)voor meer informatie over de Power shell-prompt.

## <a name="the-noprofile-parameter"></a>De para meter geen profiel

Als u Power shell zonder profielen wilt starten, gebruikt u de para meter geen **profiel** van **PowerShell.exe**, het programma dat Power shell start.

Open om te beginnen een programma dat Power shell kan starten, zoals Cmd.exe of Power shell zelf. U kunt ook het dialoog venster uitvoeren in Windows gebruiken.

Type:

```
PowerShell -NoProfile
```

Voor een volledige lijst met de para meters van PowerShell.exe, typt u:

```
PowerShell -?
```

## <a name="profiles-and-execution-policy"></a>Profielen en uitvoerings beleid

Het Power shell-uitvoerings beleid bepaalt, in deel, of u scripts kunt uitvoeren en configuratie bestanden wilt laden, inclusief de profielen. Het beleid voor **beperkte** uitvoering is de standaard instelling. Hiermee voor komt u dat alle scripts worden uitgevoerd, met inbegrip van de profielen. Als u het beleid ' beperkt ' gebruikt, wordt het profiel niet uitgevoerd en wordt de inhoud ervan niet toegepast.

`Set-ExecutionPolicy`Met een opdracht wordt het uitvoerings beleid ingesteld en gewijzigd. Het is een van de enkele opdrachten die van toepassing zijn in alle Power shell-sessies, omdat de waarde wordt opgeslagen in het REGI ster. U hoeft deze niet in te stellen wanneer u de-console opent en u hoeft geen opdracht op te slaan `Set-ExecutionPolicy` in uw profiel.

## <a name="profiles-and-remote-sessions"></a>Profielen en externe sessies

Power shell-profielen worden niet automatisch uitgevoerd in externe sessies, waardoor de opdrachten die de profielen toevoegen niet aanwezig zijn in de externe sessie. Daarnaast `$PROFILE` wordt de automatische variabele niet ingevuld in externe sessies.

Als u een profiel in een sessie wilt uitvoeren, gebruikt u de cmdlet [invoke-opdracht](xref:Microsoft.PowerShell.Core.Invoke-Command) .

Met de volgende opdracht wordt bijvoorbeeld het profiel ' huidige gebruiker, huidige host ' uitgevoerd van de lokale computer in de sessie in `$s` .

```powershell
Invoke-Command -Session $s -FilePath $PROFILE
```

Met de volgende opdracht voert u het profiel ' huidige gebruiker, huidige host ' van de externe computer in de sessie in uit `$s` . Omdat de `$PROFILE` variabele niet is ingevuld, gebruikt de opdracht het expliciete pad naar het profiel. We gebruiken de operator dot sourcing zodat het profiel wordt uitgevoerd in het huidige bereik op de externe computer en niet in een eigen bereik.

```powershell
Invoke-Command -Session $s -ScriptBlock {
  . "$HOME\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

Nadat u deze opdracht hebt uitgevoerd, zijn de opdrachten die door het profiel aan de sessie worden toegevoegd, beschikbaar in `$s` .

## <a name="see-also"></a>Zie ook

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Prompts](about_Prompts.md)

[about_Execution_Policies](about_Execution_Policies.md)

[about_Signing](about_Signing.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

