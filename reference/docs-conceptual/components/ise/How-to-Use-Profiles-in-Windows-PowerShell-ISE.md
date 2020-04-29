---
ms.date: 01/02/2020
keywords: Power shell, cmdlet
title: Profielen gebruiken in Windows PowerShell ISE
ms.openlocfilehash: da7dc2f234ad0c2968fbb213e9e57da875f456e4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736246"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="799c9-103">Profielen gebruiken in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="799c9-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="799c9-104">In dit onderwerp wordt uitgelegd hoe u profielen gebruikt in Windows Power shell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="799c9-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="799c9-105">Het is raadzaam om voordat u de taken in deze sectie uitvoert, [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)te controleren of in het deel venster console het `Get-Help about_Profiles` volgende te typen en op <kbd>Enter</kbd>te drukken.</span><span class="sxs-lookup"><span data-stu-id="799c9-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press <kbd>ENTER</kbd>.</span></span>

<span data-ttu-id="799c9-106">Een profiel is een Windows PowerShell ISE script dat automatisch wordt uitgevoerd wanneer u een nieuwe sessie start.</span><span class="sxs-lookup"><span data-stu-id="799c9-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>
<span data-ttu-id="799c9-107">U kunt een of meer Windows Power shell-profielen voor Windows PowerShell ISE maken en gebruiken om de Windows Power shell-of Windows PowerShell ISE-omgeving configureren toe te voegen, zodat deze wordt voor bereid voor uw gebruik, met variabelen, aliassen, functies en kleuren en lettertype voorkeuren die u beschikbaar wilt stellen.</span><span class="sxs-lookup"><span data-stu-id="799c9-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="799c9-108">Een profiel is van invloed op elke Windows PowerShell ISE-sessie die u start.</span><span class="sxs-lookup"><span data-stu-id="799c9-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="799c9-109">Het Windows Power shell-uitvoerings beleid bepaalt of u scripts kunt uitvoeren en een profiel laden.</span><span class="sxs-lookup"><span data-stu-id="799c9-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span>
> <span data-ttu-id="799c9-110">Het standaard uitvoerings beleid, ' beperkt ', voor komt dat alle scripts worden uitgevoerd, met inbegrip van profielen.</span><span class="sxs-lookup"><span data-stu-id="799c9-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span>
> <span data-ttu-id="799c9-111">Als u het beleid ' beperkt ' gebruikt, kan het profiel niet worden geladen.</span><span class="sxs-lookup"><span data-stu-id="799c9-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="799c9-112">Zie [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies)voor meer informatie over het uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="799c9-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="799c9-113">Een profiel selecteren dat u wilt gebruiken in de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="799c9-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="799c9-114">Windows PowerShell ISE ondersteunt profielen voor de huidige gebruiker en alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="799c9-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="799c9-115">Het ondersteunt ook de Windows Power shell-profielen die van toepassing zijn op alle hosts.</span><span class="sxs-lookup"><span data-stu-id="799c9-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="799c9-116">Het profiel dat u gebruikt, wordt bepaald door de manier waarop u Windows Power shell en Windows PowerShell ISE gebruikt.</span><span class="sxs-lookup"><span data-stu-id="799c9-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="799c9-117">Als u alleen Windows PowerShell ISE gebruikt om Windows Power shell uit te voeren, slaat u al uw items op in een van de ISE profielen, zoals het profiel **CurrentUserCurrentHost** voor Windows PowerShell ISE of het **AllUsersCurrentHost** -profiel voor Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="799c9-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the **CurrentUserCurrentHost** profile for Windows PowerShell ISE or the **AllUsersCurrentHost** profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="799c9-118">Als u meerdere hostgroepen gebruikt om Windows Power shell uit te voeren, slaat u uw functies, aliassen, variabelen en opdrachten op in een profiel dat van invloed is op alle host-Program ma's, zoals de CurrentUserAllHosts of het profiel **AllUsersAllHosts** , en hoe u ISE-specifieke functies, zoals kleur en letter type aanpassing in het profiel **CurrentUserCurrentHost** voor Windows PowerShell ISE profiel of het **AllUsersCurrentHost** -profiel voor Windows PowerShell ISE, opslaat.</span><span class="sxs-lookup"><span data-stu-id="799c9-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the **AllUsersAllHosts** profile, and save ISE-specific features, like color and font customization in the **CurrentUserCurrentHost** profile for Windows PowerShell ISE profile or the **AllUsersCurrentHost** profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="799c9-119">Hieronder vindt u de profielen die kunnen worden gemaakt en gebruikt in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="799c9-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="799c9-120">Elk profiel wordt opgeslagen in een eigen specifiek pad.</span><span class="sxs-lookup"><span data-stu-id="799c9-120">Each profile is saved to its own specific path.</span></span>

|           <span data-ttu-id="799c9-121">Profiel type</span><span class="sxs-lookup"><span data-stu-id="799c9-121">Profile Type</span></span>           |                   <span data-ttu-id="799c9-122">Profielpad</span><span class="sxs-lookup"><span data-stu-id="799c9-122">Profile Path</span></span>                   |
| -------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="799c9-123">**Huidige gebruiker, Power shell-ISE**</span><span class="sxs-lookup"><span data-stu-id="799c9-123">**Current user, PowerShell ISE**</span></span> | <span data-ttu-id="799c9-124">`$PROFILE.CurrentUserCurrentHost` of `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="799c9-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="799c9-125">**Alle gebruikers, Power shell ISE**</span><span class="sxs-lookup"><span data-stu-id="799c9-125">**All users, PowerShell ISE**</span></span>    | `$PROFILE.AllUsersCurrentHost`                   |
| <span data-ttu-id="799c9-126">**Huidige gebruiker, alle hosts**</span><span class="sxs-lookup"><span data-stu-id="799c9-126">**Current user, All hosts**</span></span>      | `$PROFILE.CurrentUserAllHosts`                   |
| <span data-ttu-id="799c9-127">**Alle gebruikers, alle hosts**</span><span class="sxs-lookup"><span data-stu-id="799c9-127">**All users, All hosts**</span></span>         | `$PROFILE.AllUsersAllHosts`                      |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="799c9-128">Een nieuw profiel maken</span><span class="sxs-lookup"><span data-stu-id="799c9-128">To create a new profile</span></span>

<span data-ttu-id="799c9-129">Als u een nieuw profiel ' huidige gebruiker, Windows PowerShell ISE ' wilt maken, voert u deze opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="799c9-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="799c9-130">Als u een nieuw profiel ' alle gebruikers, Windows PowerShell ISE ' wilt maken, voert u deze opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="799c9-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="799c9-131">Als u een nieuw profiel ' huidige gebruiker, alle hosts ' wilt maken, voert u deze opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="799c9-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="799c9-132">Als u een nieuw profiel ' alle gebruikers, alle hosts ' wilt maken, typt u:</span><span class="sxs-lookup"><span data-stu-id="799c9-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="799c9-133">Een profiel bewerken</span><span class="sxs-lookup"><span data-stu-id="799c9-133">To edit a profile</span></span>

1. <span data-ttu-id="799c9-134">Als u het profiel wilt openen, voert `psEdit` u de opdracht uit met de variabele die het profiel aangeeft dat u wilt bewerken.</span><span class="sxs-lookup"><span data-stu-id="799c9-134">To open the profile, run the command `psEdit` with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="799c9-135">Als u bijvoorbeeld het profiel ' huidige gebruiker, Windows PowerShell ISE ' wilt openen, typt u:`psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="799c9-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="799c9-136">Voeg enkele items toe aan uw profiel.</span><span class="sxs-lookup"><span data-stu-id="799c9-136">Add some items to your profile.</span></span> <span data-ttu-id="799c9-137">Hier volgen enkele voor beelden om aan de slag te gaan:</span><span class="sxs-lookup"><span data-stu-id="799c9-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="799c9-138">Als u de standaard achtergrond kleur van het console venster wilt wijzigen in blauw, in het profiel bestands `$psISE.Options.OutputPaneBackground = 'blue'` type:.</span><span class="sxs-lookup"><span data-stu-id="799c9-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="799c9-139">Zie [Windows PowerShell ISE object model](object-model/The-ISE-Object-Model-Hierarchy.md)- `$psISE` verwijzing voor meer informatie over de variabele.</span><span class="sxs-lookup"><span data-stu-id="799c9-139">For more information about the `$psISE` variable, see [Windows PowerShell ISE Object Model Reference](object-model/The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="799c9-140">Als u de teken grootte wilt wijzigen in 20, in het profiel bestands type:`$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="799c9-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="799c9-141">Als u uw profiel bestand wilt opslaan, klikt u in het menu **bestand** op **Opslaan**.</span><span class="sxs-lookup"><span data-stu-id="799c9-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="799c9-142">De volgende keer dat u de Windows PowerShell ISE opent, worden uw aanpassingen toegepast.</span><span class="sxs-lookup"><span data-stu-id="799c9-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="799c9-143">Zie ook</span><span class="sxs-lookup"><span data-stu-id="799c9-143">See Also</span></span>

- [<span data-ttu-id="799c9-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="799c9-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="799c9-145">Introductie van de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="799c9-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
