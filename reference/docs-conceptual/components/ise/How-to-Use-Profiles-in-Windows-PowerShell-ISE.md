---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Profielen gebruiken in Windows PowerShell ISE
ms.openlocfilehash: 28354f39aaaa577cec69c1b3f62cfe16ef091218
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030598"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="42f04-103">Profielen gebruiken in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="42f04-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="42f04-104">In dit onderwerp wordt uitgelegd hoe u profielen in Windows PowerShell® Integrated Scripting Environment (ISE) gebruiken.</span><span class="sxs-lookup"><span data-stu-id="42f04-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="42f04-105">We raden voordat u de taken in deze sectie, u [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), of in het consolevenster, type, `Get-Help about_Profiles` en druk op **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="42f04-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="42f04-106">Een profiel is een Windows PowerShell ISE-script dat automatisch wordt uitgevoerd wanneer u een nieuwe sessie starten.</span><span class="sxs-lookup"><span data-stu-id="42f04-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="42f04-107">U kunt een of meer Windows PowerShell-profielen maken voor Windows PowerShell ISE en gebruik ze om toe te voegen van het configureren van de Windows PowerShell of Windows PowerShell ISE-omgeving gereed te maken voor gebruik met variabelen, aliassen, functies, kleur en lettertypen voorkeuren die u beschikbaar wilt stellen.</span><span class="sxs-lookup"><span data-stu-id="42f04-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="42f04-108">Een profiel is van invloed op elke Windows PowerShell ISE-sessie die u start.</span><span class="sxs-lookup"><span data-stu-id="42f04-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="42f04-109">De Windows PowerShell-uitvoeringsbeleid bepaalt of u kunt scripts uitvoeren en laden van een profiel.</span><span class="sxs-lookup"><span data-stu-id="42f04-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="42f04-110">Het uitvoeringsbeleid standaard 'Beperkt', voorkomt u dat alle scripts die wordt uitgevoerd, met inbegrip van profielen.</span><span class="sxs-lookup"><span data-stu-id="42f04-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="42f04-111">Als u het beleid 'Restricted', kan het profiel niet laden.</span><span class="sxs-lookup"><span data-stu-id="42f04-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="42f04-112">Zie voor meer informatie over uitvoeringsbeleid [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="42f04-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="42f04-113">Selecteren van een profiel dat u wilt gebruiken in de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="42f04-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="42f04-114">Windows PowerShell ISE biedt ondersteuning voor profielen voor de huidige gebruiker en voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="42f04-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="42f04-115">Het ondersteunt ook de Windows PowerShell-profielen die betrekking hebben op alle hosts.</span><span class="sxs-lookup"><span data-stu-id="42f04-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="42f04-116">Het profiel dat u gebruikt, is afhankelijk van hoe u Windows PowerShell en Windows PowerShell ISE gebruiken.</span><span class="sxs-lookup"><span data-stu-id="42f04-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="42f04-117">Als u alleen de Windows PowerShell ISE om Windows PowerShell gebruikt, moet u vervolgens alle items opslaan in een van de ISE-specifieke profielen, zoals het profiel CurrentUserCurrentHost voor Windows PowerShell ISE of het profiel AllUsersCurrentHost voor Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="42f04-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="42f04-118">Als u meerdere host-programma's gebruikt om Windows PowerShell, uw functies, aliassen, variabelen en opdrachten in een profiel dat is van invloed op alle host-programma's, zoals de CurrentUserAllHosts of het profiel AllUsersAllHosts opslaan en ISE-specifieke functies, zoals opslaan kleuren en lettertypen aanpassing in het profiel CurrentUserCurrentHost voor Windows PowerShell ISE-profiel of de AllUsersCurrentHost voor Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="42f04-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="42f04-119">Hieronder vindt u profielen dat kunnen worden gemaakt en gebruikt in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="42f04-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="42f04-120">Elk profiel wordt opgeslagen in een eigen specifiek pad.</span><span class="sxs-lookup"><span data-stu-id="42f04-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="42f04-121">Profieltype</span><span class="sxs-lookup"><span data-stu-id="42f04-121">Profile Type</span></span> | <span data-ttu-id="42f04-122">Pad naar profiel</span><span class="sxs-lookup"><span data-stu-id="42f04-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="42f04-123">**Huidige gebruiker, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="42f04-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="42f04-124">`$PROFILE.CurrentUserCurrentHost`, of `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="42f04-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="42f04-125">**Alle gebruikers, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="42f04-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="42f04-126">**Huidige gebruiker, alle hosts**</span><span class="sxs-lookup"><span data-stu-id="42f04-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="42f04-127">**Alle gebruikers, alle hosts**</span><span class="sxs-lookup"><span data-stu-id="42f04-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="42f04-128">Een nieuw profiel maken</span><span class="sxs-lookup"><span data-stu-id="42f04-128">To create a new profile</span></span>

<span data-ttu-id="42f04-129">Het maken van een nieuwe "Current user, Windows PowerShell ISE" profiel, voert u deze opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="42f04-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="42f04-130">Maak een nieuwe 'Alle gebruikers, Windows PowerShell ISE' profiel, voert u deze opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="42f04-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="42f04-131">Voor het maken van een nieuw profiel voor het 'huidige gebruiker, alle als host fungeert voor', moet u deze opdracht uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="42f04-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="42f04-132">Voor het maken van een nieuw profiel voor "alle gebruikers, alle als host fungeert voor", typt u:</span><span class="sxs-lookup"><span data-stu-id="42f04-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="42f04-133">Om een profiel te bewerken</span><span class="sxs-lookup"><span data-stu-id="42f04-133">To edit a profile</span></span>

1. <span data-ttu-id="42f04-134">Als u wilt openen van het profiel, de opdracht psedit worden uitgevoerd met de variabele die Hiermee geeft u het profiel dat u wilt bewerken.</span><span class="sxs-lookup"><span data-stu-id="42f04-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="42f04-135">Bijvoorbeeld, om te openen van het 'huidige gebruiker, Windows PowerShell ISE' profiel, typ: `psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="42f04-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="42f04-136">Aantal items toevoegen aan uw profiel.</span><span class="sxs-lookup"><span data-stu-id="42f04-136">Add some items to your profile.</span></span> <span data-ttu-id="42f04-137">Hier volgen enkele voorbeelden om u aan de slag:</span><span class="sxs-lookup"><span data-stu-id="42f04-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="42f04-138">Wijzigen van de standaard-achtergrondkleur van het consolevenster op blauw, in het bestand profieltype: `$psISE.Options.OutputPaneBackground = 'blue'` .</span><span class="sxs-lookup"><span data-stu-id="42f04-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="42f04-139">Zie voor meer informatie over de variabele $psISE [naslaginformatie voor Windows PowerShell ISE-objectmodel](object-model/The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="42f04-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](object-model/The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="42f04-140">De tekengrootte wijzigen op 20, in het bestandstype voor het profiel: `$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="42f04-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="42f04-141">Voor uw profielbestand op de **bestand** menu, klikt u op **opslaan**.</span><span class="sxs-lookup"><span data-stu-id="42f04-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="42f04-142">Volgende keer dat u de Windows PowerShell ISE, open worden uw aanpassingen toegepast.</span><span class="sxs-lookup"><span data-stu-id="42f04-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="42f04-143">Zie ook</span><span class="sxs-lookup"><span data-stu-id="42f04-143">See Also</span></span>

- [<span data-ttu-id="42f04-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="42f04-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="42f04-145">Maak kennis met de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="42f04-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
