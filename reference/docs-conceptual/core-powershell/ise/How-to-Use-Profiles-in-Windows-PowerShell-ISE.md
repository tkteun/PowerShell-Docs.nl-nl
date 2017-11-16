---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Het gebruik van de profielen in Windows PowerShell ISE
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: f959aeb91eecc8056c91c56162ea9bff53537be9
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a>Het gebruik van de profielen in Windows PowerShell ISE
In dit onderwerp wordt uitgelegd hoe profielen in Windows PowerShell® Integrated Scripting Environment (ISE) gebruiken. We raden voordat u de taken uitvoert in deze sectie, u [about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630)), of in het consolevenster, type, `Get-Help about_Profiles` en druk op **ENTER**.

Een profiel is een Windows PowerShell ISE-script dat wordt automatisch uitgevoerd wanneer u een nieuwe sessie starten.  U kunt een of meer Windows PowerShell-profielen maken voor Windows PowerShell ISE en ze gebruiken om toe te voegen, het configureren van de Windows PowerShell of Windows PowerShell ISE-omgeving gereed te maken voor gebruik, variabelen, aliassen, functies, kleur en lettertype voorkeuren die u beschikbaar wilt stellen. Een profiel is van invloed op elke Windows PowerShell ISE-sessie die u start.

> [!NOTE]
> De Windows PowerShell-uitvoeringsbeleid bepaalt of u kunt scripts uitvoeren en een profiel laden. Het standaarduitvoeringsbeleid 'Beperkt', voorkomt u dat alle scripts worden uitgevoerd, met inbegrip van profielen. Als u het beleid 'Restricted' gebruikt, wordt het profiel niet laden. Zie voor meer informatie over het uitvoeringsbeleid [about_Execution_Policies [v4]](https://technet.microsoft.com/library/347708dc-1515-4d74-978b-8334603472e6(v=wps.630)).

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a>Een profiel moet worden gebruikt in de Windows PowerShell ISE selecteren
Windows PowerShell ISE ondersteunt profielen voor de huidige gebruiker en voor alle gebruikers. Het ondersteunt ook de Windows PowerShell-profielen die van toepassing op alle hosts.

Het profiel dat u gebruikt, is afhankelijk van hoe u Windows PowerShell en Windows PowerShell ISE gebruiken.

- Als u alleen de Windows PowerShell ISE om uit te voeren van Windows PowerShell gebruikt, moet u vervolgens al uw objecten opslaan in een van de ISE-specifieke profielen, zoals het profiel CurrentUserCurrentHost voor Windows PowerShell ISE of het profiel AllUsersCurrentHost voor Windows PowerShell ISE.

- Als u meerdere host-programma's gebruikt voor het uitvoeren van Windows PowerShell, opslaan van uw functies, aliassen, variabelen en opdrachten in een profiel dat is van invloed op alle host-programma's, zoals de CurrentUserAllHosts of het profiel AllUsersAllHosts en slaat u ISE-specifieke functies, zoals kleuren en lettertypen aanpassing in het profiel CurrentUserCurrentHost voor Windows PowerShell ISE-profiel of het profiel AllUsersCurrentHost voor Windows PowerShell ISE.

Hieronder vindt u profielen die kunnen worden gemaakt en gebruikt in Windows PowerShell ISE. Elk profiel wordt opgeslagen in een eigen specifiek pad.

| Profieltype | Profielpad |
| --- | --- |
| **Huidige gebruiker, PowerShell ISE**| `$PROFILE.CurrentUserCurrentHost`, of`$PROFILE` |
| **Alle gebruikers, PowerShell ISE**| `$PROFILE.AllUsersCurrentHost` |
| **Huidige gebruiker, alle hosts**| `$PROFILE.CurrentUserAllHosts` |
| **Alle gebruikers, alle hosts** | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a>Een nieuw profiel maken
Maken van een nieuwe "Current user, Windows PowerShell ISE" profiel, voert u deze opdracht:

```powershell
if (!(Test-Path -Path $PROFILE )) 
{ New-Item -Type File -Path $PROFILE -Force }
```

Maak een nieuwe 'Alle gebruikers, Windows PowerShell ISE' profiel, voert u deze opdracht:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost)) 
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

Als u wilt een nieuw 'huidige gebruiker, alle fungeert als host voor'-profiel maakt, moet u deze opdracht uitvoeren:

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts)) 
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

Een nieuwe 'alle gebruikers alle fungeert als host voor' om profiel te maken, typt u:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts)) 
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a>Een profiel bewerken

1. Om te openen van het profiel, de opdracht psedit worden uitgevoerd met de variabele die het profiel dat u wilt bewerken. Bijvoorbeeld, 'Current user, Windows PowerShell ISE' openen profiel, typ:`psEdit $PROFILE`

2. Sommige items toevoegen aan uw profiel. Hier volgen enkele voorbeelden aan u op weg:

    -   Om de standaardachtergrondkleur van het consolevenster blauw, in het bestandstype voor het profiel te wijzigen: `$psISE.Options.OutputPaneBackground = 'blue'` . Zie voor meer informatie over de variabele $psISE [naslaginformatie voor Windows PowerShell ISE-objectmodel](The-ISE-Object-Model-Hierarchy.md).

    -   Tekengrootte op 20, in het profiel bestandstype wijzigen:`$psISE.Options.FontSize =20`

3. Uw profielbestand wilt opslaan, op de **bestand** menu, klikt u op **opslaan**. Wanneer die u de Windows PowerShell ISE opent worden uw aanpassingen toegepast.

## <a name="see-also"></a>Zie ook
- [about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630))
- [Met behulp van de Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)

