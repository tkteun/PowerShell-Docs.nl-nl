---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Profielen gebruiken in Windows PowerShell ISE
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: b319aa089c2a4a7008acd9850f15342dac70aee2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057525"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a>Profielen gebruiken in Windows PowerShell ISE

In dit onderwerp wordt uitgelegd hoe u profielen in Windows PowerShell® Integrated Scripting Environment (ISE) gebruiken. We raden voordat u de taken in deze sectie, u [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), of in het consolevenster, type, `Get-Help about_Profiles` en druk op **ENTER**.

Een profiel is een Windows PowerShell ISE-script dat automatisch wordt uitgevoerd wanneer u een nieuwe sessie starten.  U kunt een of meer Windows PowerShell-profielen maken voor Windows PowerShell ISE en gebruik ze om toe te voegen van het configureren van de Windows PowerShell of Windows PowerShell ISE-omgeving gereed te maken voor gebruik met variabelen, aliassen, functies, kleur en lettertypen voorkeuren die u beschikbaar wilt stellen. Een profiel is van invloed op elke Windows PowerShell ISE-sessie die u start.

> [!NOTE]
> De Windows PowerShell-uitvoeringsbeleid bepaalt of u kunt scripts uitvoeren en laden van een profiel. Het uitvoeringsbeleid standaard 'Beperkt', voorkomt u dat alle scripts die wordt uitgevoerd, met inbegrip van profielen. Als u het beleid 'Restricted', kan het profiel niet laden. Zie voor meer informatie over uitvoeringsbeleid [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a>Selecteren van een profiel dat u wilt gebruiken in de Windows PowerShell ISE

Windows PowerShell ISE biedt ondersteuning voor profielen voor de huidige gebruiker en voor alle gebruikers. Het ondersteunt ook de Windows PowerShell-profielen die betrekking hebben op alle hosts.

Het profiel dat u gebruikt, is afhankelijk van hoe u Windows PowerShell en Windows PowerShell ISE gebruiken.

- Als u alleen de Windows PowerShell ISE om Windows PowerShell gebruikt, moet u vervolgens alle items opslaan in een van de ISE-specifieke profielen, zoals het profiel CurrentUserCurrentHost voor Windows PowerShell ISE of het profiel AllUsersCurrentHost voor Windows PowerShell ISE.

- Als u meerdere host-programma's gebruikt om Windows PowerShell, uw functies, aliassen, variabelen en opdrachten in een profiel dat is van invloed op alle host-programma's, zoals de CurrentUserAllHosts of het profiel AllUsersAllHosts opslaan en ISE-specifieke functies, zoals opslaan kleuren en lettertypen aanpassing in het profiel CurrentUserCurrentHost voor Windows PowerShell ISE-profiel of de AllUsersCurrentHost voor Windows PowerShell ISE.

Hieronder vindt u profielen dat kunnen worden gemaakt en gebruikt in Windows PowerShell ISE. Elk profiel wordt opgeslagen in een eigen specifiek pad.

| Profieltype | Pad naar profiel |
| --- | --- |
| **Huidige gebruiker, PowerShell ISE**| `$PROFILE.CurrentUserCurrentHost`, of `$PROFILE` |
| **Alle gebruikers, PowerShell ISE**| `$PROFILE.AllUsersCurrentHost` |
| **Huidige gebruiker, alle hosts**| `$PROFILE.CurrentUserAllHosts` |
| **Alle gebruikers, alle hosts** | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a>Een nieuw profiel maken

Het maken van een nieuwe "Current user, Windows PowerShell ISE" profiel, voert u deze opdracht uit:

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

Maak een nieuwe 'Alle gebruikers, Windows PowerShell ISE' profiel, voert u deze opdracht uit:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

Voor het maken van een nieuw profiel voor het 'huidige gebruiker, alle als host fungeert voor', moet u deze opdracht uitvoeren:

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

Voor het maken van een nieuw profiel voor "alle gebruikers, alle als host fungeert voor", typt u:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a>Om een profiel te bewerken

1. Als u wilt openen van het profiel, de opdracht psedit worden uitgevoerd met de variabele die Hiermee geeft u het profiel dat u wilt bewerken. Bijvoorbeeld, om te openen van het 'huidige gebruiker, Windows PowerShell ISE' profiel, typ: `psEdit $PROFILE`

2. Aantal items toevoegen aan uw profiel. Hier volgen enkele voorbeelden om u aan de slag:

   - Wijzigen van de standaard-achtergrondkleur van het consolevenster op blauw, in het bestand profieltype: `$psISE.Options.OutputPaneBackground = 'blue'` . Zie voor meer informatie over de variabele $psISE [naslaginformatie voor Windows PowerShell ISE-objectmodel](object-model/The-ISE-Object-Model-Hierarchy.md).

   - De tekengrootte wijzigen op 20, in het bestandstype voor het profiel: `$psISE.Options.FontSize =20`

3. Voor uw profielbestand op de **bestand** menu, klikt u op **opslaan**. Volgende keer dat u de Windows PowerShell ISE, open worden uw aanpassingen toegepast.

## <a name="see-also"></a>Zie ook

- [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [Maak kennis met de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)