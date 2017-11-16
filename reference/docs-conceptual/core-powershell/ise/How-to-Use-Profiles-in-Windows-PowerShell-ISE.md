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
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="33562-103">Het gebruik van de profielen in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="33562-103">How to Use Profiles in Windows PowerShell ISE</span></span>
<span data-ttu-id="33562-104">In dit onderwerp wordt uitgelegd hoe profielen in Windows PowerShell® Integrated Scripting Environment (ISE) gebruiken.</span><span class="sxs-lookup"><span data-stu-id="33562-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="33562-105">We raden voordat u de taken uitvoert in deze sectie, u [about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630)), of in het consolevenster, type, `Get-Help about_Profiles` en druk op **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="33562-105">We recommend that before performing the tasks in this section, you review [about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630)), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="33562-106">Een profiel is een Windows PowerShell ISE-script dat wordt automatisch uitgevoerd wanneer u een nieuwe sessie starten.</span><span class="sxs-lookup"><span data-stu-id="33562-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="33562-107">U kunt een of meer Windows PowerShell-profielen maken voor Windows PowerShell ISE en ze gebruiken om toe te voegen, het configureren van de Windows PowerShell of Windows PowerShell ISE-omgeving gereed te maken voor gebruik, variabelen, aliassen, functies, kleur en lettertype voorkeuren die u beschikbaar wilt stellen.</span><span class="sxs-lookup"><span data-stu-id="33562-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="33562-108">Een profiel is van invloed op elke Windows PowerShell ISE-sessie die u start.</span><span class="sxs-lookup"><span data-stu-id="33562-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="33562-109">De Windows PowerShell-uitvoeringsbeleid bepaalt of u kunt scripts uitvoeren en een profiel laden.</span><span class="sxs-lookup"><span data-stu-id="33562-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="33562-110">Het standaarduitvoeringsbeleid 'Beperkt', voorkomt u dat alle scripts worden uitgevoerd, met inbegrip van profielen.</span><span class="sxs-lookup"><span data-stu-id="33562-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="33562-111">Als u het beleid 'Restricted' gebruikt, wordt het profiel niet laden.</span><span class="sxs-lookup"><span data-stu-id="33562-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="33562-112">Zie voor meer informatie over het uitvoeringsbeleid [about_Execution_Policies [v4]](https://technet.microsoft.com/library/347708dc-1515-4d74-978b-8334603472e6(v=wps.630)).</span><span class="sxs-lookup"><span data-stu-id="33562-112">For more information about execution policy, see [about_Execution_Policies [v4]](https://technet.microsoft.com/library/347708dc-1515-4d74-978b-8334603472e6(v=wps.630)).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="33562-113">Een profiel moet worden gebruikt in de Windows PowerShell ISE selecteren</span><span class="sxs-lookup"><span data-stu-id="33562-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>
<span data-ttu-id="33562-114">Windows PowerShell ISE ondersteunt profielen voor de huidige gebruiker en voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="33562-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="33562-115">Het ondersteunt ook de Windows PowerShell-profielen die van toepassing op alle hosts.</span><span class="sxs-lookup"><span data-stu-id="33562-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="33562-116">Het profiel dat u gebruikt, is afhankelijk van hoe u Windows PowerShell en Windows PowerShell ISE gebruiken.</span><span class="sxs-lookup"><span data-stu-id="33562-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="33562-117">Als u alleen de Windows PowerShell ISE om uit te voeren van Windows PowerShell gebruikt, moet u vervolgens al uw objecten opslaan in een van de ISE-specifieke profielen, zoals het profiel CurrentUserCurrentHost voor Windows PowerShell ISE of het profiel AllUsersCurrentHost voor Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="33562-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="33562-118">Als u meerdere host-programma's gebruikt voor het uitvoeren van Windows PowerShell, opslaan van uw functies, aliassen, variabelen en opdrachten in een profiel dat is van invloed op alle host-programma's, zoals de CurrentUserAllHosts of het profiel AllUsersAllHosts en slaat u ISE-specifieke functies, zoals kleuren en lettertypen aanpassing in het profiel CurrentUserCurrentHost voor Windows PowerShell ISE-profiel of het profiel AllUsersCurrentHost voor Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="33562-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="33562-119">Hieronder vindt u profielen die kunnen worden gemaakt en gebruikt in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="33562-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="33562-120">Elk profiel wordt opgeslagen in een eigen specifiek pad.</span><span class="sxs-lookup"><span data-stu-id="33562-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="33562-121">Profieltype</span><span class="sxs-lookup"><span data-stu-id="33562-121">Profile Type</span></span> | <span data-ttu-id="33562-122">Profielpad</span><span class="sxs-lookup"><span data-stu-id="33562-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="33562-123">**Huidige gebruiker, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="33562-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="33562-124">`$PROFILE.CurrentUserCurrentHost`, of`$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="33562-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="33562-125">**Alle gebruikers, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="33562-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="33562-126">**Huidige gebruiker, alle hosts**</span><span class="sxs-lookup"><span data-stu-id="33562-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="33562-127">**Alle gebruikers, alle hosts**</span><span class="sxs-lookup"><span data-stu-id="33562-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="33562-128">Een nieuw profiel maken</span><span class="sxs-lookup"><span data-stu-id="33562-128">To create a new profile</span></span>
<span data-ttu-id="33562-129">Maken van een nieuwe "Current user, Windows PowerShell ISE" profiel, voert u deze opdracht:</span><span class="sxs-lookup"><span data-stu-id="33562-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE )) 
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="33562-130">Maak een nieuwe 'Alle gebruikers, Windows PowerShell ISE' profiel, voert u deze opdracht:</span><span class="sxs-lookup"><span data-stu-id="33562-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost)) 
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="33562-131">Als u wilt een nieuw 'huidige gebruiker, alle fungeert als host voor'-profiel maakt, moet u deze opdracht uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="33562-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts)) 
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="33562-132">Een nieuwe 'alle gebruikers alle fungeert als host voor' om profiel te maken, typt u:</span><span class="sxs-lookup"><span data-stu-id="33562-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts)) 
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="33562-133">Een profiel bewerken</span><span class="sxs-lookup"><span data-stu-id="33562-133">To edit a profile</span></span>

1. <span data-ttu-id="33562-134">Om te openen van het profiel, de opdracht psedit worden uitgevoerd met de variabele die het profiel dat u wilt bewerken.</span><span class="sxs-lookup"><span data-stu-id="33562-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="33562-135">Bijvoorbeeld, 'Current user, Windows PowerShell ISE' openen profiel, typ:`psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="33562-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="33562-136">Sommige items toevoegen aan uw profiel.</span><span class="sxs-lookup"><span data-stu-id="33562-136">Add some items to your profile.</span></span> <span data-ttu-id="33562-137">Hier volgen enkele voorbeelden aan u op weg:</span><span class="sxs-lookup"><span data-stu-id="33562-137">The following are a few examples to get you started:</span></span>

    -   <span data-ttu-id="33562-138">Om de standaardachtergrondkleur van het consolevenster blauw, in het bestandstype voor het profiel te wijzigen: `$psISE.Options.OutputPaneBackground = 'blue'` .</span><span class="sxs-lookup"><span data-stu-id="33562-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="33562-139">Zie voor meer informatie over de variabele $psISE [naslaginformatie voor Windows PowerShell ISE-objectmodel](The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="33562-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](The-ISE-Object-Model-Hierarchy.md).</span></span>

    -   <span data-ttu-id="33562-140">Tekengrootte op 20, in het profiel bestandstype wijzigen:`$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="33562-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="33562-141">Uw profielbestand wilt opslaan, op de **bestand** menu, klikt u op **opslaan**.</span><span class="sxs-lookup"><span data-stu-id="33562-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="33562-142">Wanneer die u de Windows PowerShell ISE opent worden uw aanpassingen toegepast.</span><span class="sxs-lookup"><span data-stu-id="33562-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="33562-143">Zie ook</span><span class="sxs-lookup"><span data-stu-id="33562-143">See Also</span></span>
- <span data-ttu-id="33562-144">[about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630))</span><span class="sxs-lookup"><span data-stu-id="33562-144">[about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630))</span></span>
- [<span data-ttu-id="33562-145">Met behulp van de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="33562-145">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)

