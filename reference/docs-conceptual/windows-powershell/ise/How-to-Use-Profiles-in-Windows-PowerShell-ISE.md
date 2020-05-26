---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Profielen gebruiken in Windows PowerShell ISE
ms.openlocfilehash: da7dc2f234ad0c2968fbb213e9e57da875f456e4
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810286"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a>Profielen gebruiken in Windows PowerShell ISE

In dit onderwerp wordt uitgelegd hoe u profielen gebruikt in Windows Power shell® Integrated Scripting Environment (ISE). Het is raadzaam om voordat u de taken in deze sectie uitvoert, [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)te controleren of in het deel venster console het volgende te typen `Get-Help about_Profiles` en op <kbd>Enter</kbd>te drukken.

Een profiel is een Windows PowerShell ISE script dat automatisch wordt uitgevoerd wanneer u een nieuwe sessie start.
U kunt een of meer Windows Power shell-profielen voor Windows PowerShell ISE maken en gebruiken om de Windows Power shell-of Windows PowerShell ISE-omgeving configureren toe te voegen, zodat deze wordt voor bereid voor uw gebruik, met variabelen, aliassen, functies en kleuren en lettertype voorkeuren die u beschikbaar wilt stellen. Een profiel is van invloed op elke Windows PowerShell ISE-sessie die u start.

> [!NOTE]
> Het Windows Power shell-uitvoerings beleid bepaalt of u scripts kunt uitvoeren en een profiel laden.
> Het standaard uitvoerings beleid, ' beperkt ', voor komt dat alle scripts worden uitgevoerd, met inbegrip van profielen.
> Als u het beleid ' beperkt ' gebruikt, kan het profiel niet worden geladen. Zie [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies)voor meer informatie over het uitvoerings beleid.

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a>Een profiel selecteren dat u wilt gebruiken in de Windows PowerShell ISE

Windows PowerShell ISE ondersteunt profielen voor de huidige gebruiker en alle gebruikers. Het ondersteunt ook de Windows Power shell-profielen die van toepassing zijn op alle hosts.

Het profiel dat u gebruikt, wordt bepaald door de manier waarop u Windows Power shell en Windows PowerShell ISE gebruikt.

- Als u alleen Windows PowerShell ISE gebruikt om Windows Power shell uit te voeren, slaat u al uw items op in een van de ISE profielen, zoals het profiel **CurrentUserCurrentHost** voor Windows PowerShell ISE of het **AllUsersCurrentHost** -profiel voor Windows PowerShell ISE.

- Als u meerdere hostgroepen gebruikt om Windows Power shell uit te voeren, slaat u uw functies, aliassen, variabelen en opdrachten op in een profiel dat van invloed is op alle host-Program ma's, zoals de CurrentUserAllHosts of het profiel **AllUsersAllHosts** , en hoe u ISE-specifieke functies, zoals kleur en letter type aanpassing in het profiel **CurrentUserCurrentHost** voor Windows PowerShell ISE profiel of het **AllUsersCurrentHost** -profiel voor Windows PowerShell ISE, opslaat.

Hieronder vindt u de profielen die kunnen worden gemaakt en gebruikt in Windows PowerShell ISE. Elk profiel wordt opgeslagen in een eigen specifiek pad.

|           Profiel type           |                   Profielpad                   |
| -------------------------------- | ------------------------------------------------ |
| **Huidige gebruiker, Power shell-ISE** | `$PROFILE.CurrentUserCurrentHost` of `$PROFILE` |
| **Alle gebruikers, Power shell ISE**    | `$PROFILE.AllUsersCurrentHost`                   |
| **Huidige gebruiker, alle hosts**      | `$PROFILE.CurrentUserAllHosts`                   |
| **Alle gebruikers, alle hosts**         | `$PROFILE.AllUsersAllHosts`                      |

## <a name="to-create-a-new-profile"></a>Een nieuw profiel maken

Als u een nieuw profiel ' huidige gebruiker, Windows PowerShell ISE ' wilt maken, voert u deze opdracht uit:

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

Als u een nieuw profiel ' alle gebruikers, Windows PowerShell ISE ' wilt maken, voert u deze opdracht uit:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

Als u een nieuw profiel ' huidige gebruiker, alle hosts ' wilt maken, voert u deze opdracht uit:

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

Als u een nieuw profiel ' alle gebruikers, alle hosts ' wilt maken, typt u:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a>Een profiel bewerken

1. Als u het profiel wilt openen, voert u de opdracht uit `psEdit` met de variabele die het profiel aangeeft dat u wilt bewerken. Als u bijvoorbeeld het profiel ' huidige gebruiker, Windows PowerShell ISE ' wilt openen, typt u:`psEdit $PROFILE`

2. Voeg enkele items toe aan uw profiel. Hier volgen enkele voor beelden om aan de slag te gaan:

   - Als u de standaard achtergrond kleur van het console venster wilt wijzigen in blauw, in het profiel bestands type: `$psISE.Options.OutputPaneBackground = 'blue'` . `$psISE`Zie [Windows PowerShell ISE object model-verwijzing](object-model/The-ISE-Object-Model-Hierarchy.md)voor meer informatie over de variabele.

   - Als u de teken grootte wilt wijzigen in 20, in het profiel bestands type:`$psISE.Options.FontSize =20`

3. Als u uw profiel bestand wilt opslaan, klikt u in het menu **bestand** op **Opslaan**. De volgende keer dat u de Windows PowerShell ISE opent, worden uw aanpassingen toegepast.

## <a name="see-also"></a>Zie ook

- [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [Introductie van de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
