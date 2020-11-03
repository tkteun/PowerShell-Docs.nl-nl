---
description: Hierin wordt beschreven hoe u een Power shell-profiel maakt en gebruikt.
keywords: powershell,cmdlet
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Profiles
ms.openlocfilehash: 3fb6a67e160281f60f20c187bf37c6920a506705
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252094"
---
# <a name="about-profiles"></a><span data-ttu-id="a5f7e-104">Over profielen</span><span class="sxs-lookup"><span data-stu-id="a5f7e-104">About Profiles</span></span>

## <a name="short-description"></a><span data-ttu-id="a5f7e-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="a5f7e-105">Short Description</span></span>
<span data-ttu-id="a5f7e-106">Hierin wordt beschreven hoe u een Power shell-profiel maakt en gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-106">Describes how to create and use a PowerShell profile.</span></span>

## <a name="long-description"></a><span data-ttu-id="a5f7e-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="a5f7e-107">Long Description</span></span>

<span data-ttu-id="a5f7e-108">U kunt een Power shell-profiel maken om uw omgeving aan te passen en om sessie-specifieke elementen toe te voegen aan elke Power shell-sessie die u start.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-108">You can create a PowerShell profile to customize your environment and to add session-specific elements to every PowerShell session that you start.</span></span>

<span data-ttu-id="a5f7e-109">Een Power shell-profiel is een script dat wordt uitgevoerd wanneer Power shell wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-109">A PowerShell profile is a script that runs when PowerShell starts.</span></span> <span data-ttu-id="a5f7e-110">U kunt het profiel als een aanmeldings script gebruiken om de omgeving aan te passen.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-110">You can use the profile as a logon script to customize the environment.</span></span> <span data-ttu-id="a5f7e-111">U kunt opdrachten, aliassen, functies, variabelen, modules, modules en Power Shell-stations toevoegen.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-111">You can add commands, aliases, functions, variables, snap-ins, modules, and PowerShell drives.</span></span> <span data-ttu-id="a5f7e-112">U kunt ook andere sessie-specifieke elementen aan uw profiel toevoegen, zodat deze beschikbaar zijn in elke sessie, zonder dat u ze hoeft te importeren of opnieuw te maken.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-112">You can also add other session-specific elements to your profile so they are available in every session without having to import or re-create them.</span></span>

<span data-ttu-id="a5f7e-113">Power shell ondersteunt meerdere profielen voor gebruikers en hosttoepassingen.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-113">PowerShell supports several profiles for users and host programs.</span></span> <span data-ttu-id="a5f7e-114">De profielen worden echter niet voor u gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-114">However, it does not create the profiles for you.</span></span> <span data-ttu-id="a5f7e-115">In dit onderwerp worden de profielen beschreven, en wordt beschreven hoe u profielen op uw computer maakt en onderhoudt.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-115">This topic describes the profiles, and it describes how to create and maintain profiles on your computer.</span></span>

<span data-ttu-id="a5f7e-116">Hierin wordt uitgelegd hoe u de para meter geen **profiel** van de Power shell-console (PowerShell.exe) kunt gebruiken om Power shell zonder profielen te starten.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-116">It explains how to use the **NoProfile** parameter of the PowerShell console (PowerShell.exe) to start PowerShell without any profiles.</span></span> <span data-ttu-id="a5f7e-117">En wordt het effect van het Power shell-uitvoerings beleid op profielen uitgelegd.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-117">And, it explains the effect of the PowerShell execution policy on profiles.</span></span>

## <a name="the-profile-files"></a><span data-ttu-id="a5f7e-118">De profiel bestanden</span><span class="sxs-lookup"><span data-stu-id="a5f7e-118">The Profile Files</span></span>

<span data-ttu-id="a5f7e-119">Power shell ondersteunt meerdere profiel bestanden.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-119">PowerShell supports several profile files.</span></span> <span data-ttu-id="a5f7e-120">Power shell-host-Program ma's kunnen ook hun eigen platformspecifieke profielen ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-120">Also, PowerShell host programs can support their own host-specific profiles.</span></span>

<span data-ttu-id="a5f7e-121">De Power shell-console ondersteunt bijvoorbeeld de volgende basis profiel bestanden.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-121">For example, the PowerShell console supports the following basic profile files.</span></span> <span data-ttu-id="a5f7e-122">De profielen worden in volg orde van prioriteit weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-122">The profiles are listed in precedence order.</span></span> <span data-ttu-id="a5f7e-123">Het eerste profiel heeft de hoogste prioriteit.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-123">The first profile has the highest precedence.</span></span>

|<span data-ttu-id="a5f7e-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a5f7e-124">Description</span></span>               | <span data-ttu-id="a5f7e-125">Pad</span><span class="sxs-lookup"><span data-stu-id="a5f7e-125">Path</span></span>                                          |
|--------------------------|-----------------------------------------------|
|<span data-ttu-id="a5f7e-126">Alle gebruikers, alle hosts</span><span class="sxs-lookup"><span data-stu-id="a5f7e-126">All Users, All Hosts</span></span>      |<span data-ttu-id="a5f7e-127">$PSHOME \\Profile.ps1</span><span class="sxs-lookup"><span data-stu-id="a5f7e-127">$PSHOME\\Profile.ps1</span></span>                           |
|<span data-ttu-id="a5f7e-128">Alle gebruikers, huidige host</span><span class="sxs-lookup"><span data-stu-id="a5f7e-128">All Users, Current Host</span></span>   |<span data-ttu-id="a5f7e-129">$PSHOME \\Microsoft.PowerShell_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="a5f7e-129">$PSHOME\\Microsoft.PowerShell_profile.ps1</span></span>      |
|<span data-ttu-id="a5f7e-130">Huidige gebruiker, alle hosts</span><span class="sxs-lookup"><span data-stu-id="a5f7e-130">Current User, All Hosts</span></span>   |<span data-ttu-id="a5f7e-131">$Home \\ [mijn] documenten \\ Power shell- \\Profile.ps1</span><span class="sxs-lookup"><span data-stu-id="a5f7e-131">$Home\\[My ]Documents\\PowerShell\\Profile.ps1</span></span> |
|<span data-ttu-id="a5f7e-132">Huidige gebruiker, huidige host</span><span class="sxs-lookup"><span data-stu-id="a5f7e-132">Current user, Current Host</span></span>|<span data-ttu-id="a5f7e-133">$Home \\ [mijn] documenten \\ Power shell</span><span class="sxs-lookup"><span data-stu-id="a5f7e-133">$Home\\[My ]Documents\\PowerShell</span></span>\\<br><span data-ttu-id="a5f7e-134">Microsoft.PowerShell_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="a5f7e-134">Microsoft.PowerShell_profile.ps1</span></span> |

<span data-ttu-id="a5f7e-135">De profiel paden bevatten de volgende variabelen:</span><span class="sxs-lookup"><span data-stu-id="a5f7e-135">The profile paths include the following variables:</span></span>

- <span data-ttu-id="a5f7e-136">De `$PSHOME` variabele waarin de installatie directory voor Power shell wordt opgeslagen</span><span class="sxs-lookup"><span data-stu-id="a5f7e-136">The `$PSHOME` variable, which stores the installation directory for PowerShell</span></span>
- <span data-ttu-id="a5f7e-137">De `$Home` variabele, waarin de basismap van de huidige gebruiker wordt opgeslagen</span><span class="sxs-lookup"><span data-stu-id="a5f7e-137">The `$Home` variable, which stores the current user's home directory</span></span>

<span data-ttu-id="a5f7e-138">Daarnaast kunnen andere Program ma's die Power shell hosten hun eigen profielen ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-138">In addition, other programs that host PowerShell can support their own profiles.</span></span> <span data-ttu-id="a5f7e-139">Visual Studio code ondersteunt bijvoorbeeld de volgende sitespecifieke profielen.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-139">For example, Visual Studio Code supports the following host-specific profiles.</span></span>

|<span data-ttu-id="a5f7e-140">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a5f7e-140">Description</span></span>               | <span data-ttu-id="a5f7e-141">Pad</span><span class="sxs-lookup"><span data-stu-id="a5f7e-141">Path</span></span>                                     |
|--------------------------|------------------------------------------|
|<span data-ttu-id="a5f7e-142">Alle gebruikers, huidige host</span><span class="sxs-lookup"><span data-stu-id="a5f7e-142">All users, Current Host</span></span>   |<span data-ttu-id="a5f7e-143">$PSHOME \\Microsoft.VSCode_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="a5f7e-143">$PSHOME\\Microsoft.VSCode_profile.ps1</span></span>|
|<span data-ttu-id="a5f7e-144">Huidige gebruiker, huidige host</span><span class="sxs-lookup"><span data-stu-id="a5f7e-144">Current user, Current Host</span></span>|<span data-ttu-id="a5f7e-145">$Home \\ [mijn] documenten \\ Power shell</span><span class="sxs-lookup"><span data-stu-id="a5f7e-145">$Home\\[My ]Documents\\PowerShell</span></span>\\<br><span data-ttu-id="a5f7e-146">Microsoft.VSCode_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="a5f7e-146">Microsoft.VSCode_profile.ps1</span></span>|

<span data-ttu-id="a5f7e-147">In de Help van Power shell is het profiel ' CurrentUser, Current Host ' het profiel dat het vaakst wordt aangeduid als ' uw Power shell-profiel '.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-147">In PowerShell Help, the "CurrentUser, Current Host" profile is the profile most often referred to as "your PowerShell profile".</span></span>

## <a name="the-profile-variable"></a><span data-ttu-id="a5f7e-148">De variabele $PROFILE</span><span class="sxs-lookup"><span data-stu-id="a5f7e-148">The $PROFILE variable</span></span>

<span data-ttu-id="a5f7e-149">De `$PROFILE` Automatische variabele slaat de paden op naar de Power shell-profielen die beschikbaar zijn in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-149">The `$PROFILE` automatic variable stores the paths to the PowerShell profiles that are available in the current session.</span></span>

<span data-ttu-id="a5f7e-150">Als u een profielpad wilt weer geven, geeft u de waarde van de `$PROFILE` variabele weer.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-150">To view a profile path, display the value of the `$PROFILE` variable.</span></span> <span data-ttu-id="a5f7e-151">U kunt ook de `$PROFILE` variabele in een opdracht gebruiken om een pad weer te geven.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-151">You can also use the `$PROFILE` variable in a command to represent a path.</span></span>

<span data-ttu-id="a5f7e-152">De `$PROFILE` variabele slaat het pad op naar het profiel huidige gebruiker, huidige host.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-152">The `$PROFILE` variable stores the path to the "Current User, Current Host" profile.</span></span> <span data-ttu-id="a5f7e-153">De andere profielen worden opgeslagen in notitie-eigenschappen van de `$PROFILE` variabele.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-153">The other profiles are saved in note properties of the `$PROFILE` variable.</span></span>

<span data-ttu-id="a5f7e-154">De `$PROFILE` variabele bevat bijvoorbeeld de volgende waarden in de Windows Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-154">For example, the `$PROFILE` variable has the following values in the Windows PowerShell console.</span></span>

|<span data-ttu-id="a5f7e-155">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a5f7e-155">Description</span></span>                |<span data-ttu-id="a5f7e-156">Naam</span><span class="sxs-lookup"><span data-stu-id="a5f7e-156">Name</span></span>                              |
|---------------------------|----------------------------------|
|<span data-ttu-id="a5f7e-157">Huidige gebruiker, huidige host</span><span class="sxs-lookup"><span data-stu-id="a5f7e-157">Current User, Current Host</span></span> |`$PROFILE`                        |
|<span data-ttu-id="a5f7e-158">Huidige gebruiker, huidige host</span><span class="sxs-lookup"><span data-stu-id="a5f7e-158">Current User, Current Host</span></span> |`$PROFILE.CurrentUserCurrentHost` |
|<span data-ttu-id="a5f7e-159">Huidige gebruiker, alle hosts</span><span class="sxs-lookup"><span data-stu-id="a5f7e-159">Current User, All Hosts</span></span>    |`$PROFILE.CurrentUserAllHosts`    |
|<span data-ttu-id="a5f7e-160">Alle gebruikers, huidige host</span><span class="sxs-lookup"><span data-stu-id="a5f7e-160">All Users, Current Host</span></span>    |`$PROFILE.AllUsersCurrentHost`    |
|<span data-ttu-id="a5f7e-161">Alle gebruikers, alle hosts</span><span class="sxs-lookup"><span data-stu-id="a5f7e-161">All Users, All Hosts</span></span>       |`$PROFILE.AllUsersAllHosts`       |

<span data-ttu-id="a5f7e-162">Omdat de waarden van de `$PROFILE` variabele wijzigen voor elke gebruiker en in elke hosttoepassing, moet u ervoor zorgen dat u de waarden van de profiel variabelen weergeeft in elke Power shell-hosttoepassing die u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-162">Because the values of the `$PROFILE` variable change for each user and in each host application, ensure that you display the values of the profile variables in each PowerShell host application that you use.</span></span>

<span data-ttu-id="a5f7e-163">Als u de huidige waarden van de variabele wilt weer geven `$PROFILE` , typt u:</span><span class="sxs-lookup"><span data-stu-id="a5f7e-163">To see the current values of the `$PROFILE` variable, type:</span></span>

```powershell
$PROFILE | Get-Member -Type NoteProperty
```

<span data-ttu-id="a5f7e-164">U kunt de `$PROFILE` variabele in veel opdrachten gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-164">You can use the `$PROFILE` variable in many commands.</span></span> <span data-ttu-id="a5f7e-165">Met de volgende opdracht wordt bijvoorbeeld het profiel ' huidige gebruiker, huidige host ' geopend in Klad blok:</span><span class="sxs-lookup"><span data-stu-id="a5f7e-165">For example, the following command opens the "Current User, Current Host" profile in Notepad:</span></span>

```powershell
notepad $PROFILE
```

<span data-ttu-id="a5f7e-166">Met de volgende opdracht wordt bepaald of het profiel ' alle gebruikers, alle hosts ' is gemaakt op de lokale computer:</span><span class="sxs-lookup"><span data-stu-id="a5f7e-166">The following command determines whether an "All Users, All Hosts" profile has been created on the local computer:</span></span>

```powershell
Test-Path -Path $PROFILE.AllUsersAllHosts
```

## <a name="how-to-create-a-profile"></a><span data-ttu-id="a5f7e-167">Een profiel maken</span><span class="sxs-lookup"><span data-stu-id="a5f7e-167">How to create a profile</span></span>

<span data-ttu-id="a5f7e-168">Als u een Power shell-profiel wilt maken, gebruikt u de volgende opdracht indeling:</span><span class="sxs-lookup"><span data-stu-id="a5f7e-168">To create a PowerShell profile, use the following command format:</span></span>

```powershell
if (!(Test-Path -Path <profile-name>)) {
  New-Item -ItemType File -Path <profile-name> -Force
}
```

<span data-ttu-id="a5f7e-169">Als u bijvoorbeeld een profiel voor de huidige gebruiker in de huidige Power shell-hosttoepassing wilt maken, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="a5f7e-169">For example, to create a profile for the current user in the current PowerShell host application, use the following command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
```

<span data-ttu-id="a5f7e-170">In deze opdracht `If` voor komt u dat u een bestaand profiel kunt overschrijven met de instructie.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-170">In this command, the `If` statement prevents you from overwriting an existing profile.</span></span> <span data-ttu-id="a5f7e-171">Vervang de waarde van de \<profile-path\> tijdelijke aanduiding door het pad naar het profiel bestand dat u wilt maken.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-171">Replace the value of the \<profile-path\> placeholder with the path to the profile file that you want to create.</span></span>

> [!NOTE]
> <span data-ttu-id="a5f7e-172">Als u profielen voor alle gebruikers wilt maken in Windows Vista en latere versies van Windows, start u Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="a5f7e-172">To create "All Users" profiles in Windows Vista and later versions of Windows, start PowerShell with the **Run as administrator** option.</span></span>

## <a name="how-to-edit-a-profile"></a><span data-ttu-id="a5f7e-173">Een profiel bewerken</span><span class="sxs-lookup"><span data-stu-id="a5f7e-173">How to edit a profile</span></span>

<span data-ttu-id="a5f7e-174">U kunt elk Power shell-profiel openen in een tekst editor, zoals Klad blok.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-174">You can open any PowerShell profile in a text editor, such as Notepad.</span></span>

<span data-ttu-id="a5f7e-175">Als u het profiel van de huidige gebruiker in de huidige Power shell-hosttoepassing in Klad blok wilt openen, typt u:</span><span class="sxs-lookup"><span data-stu-id="a5f7e-175">To open the profile of the current user in the current PowerShell host application in Notepad, type:</span></span>

```powershell
notepad $PROFILE
```

<span data-ttu-id="a5f7e-176">Als u andere profielen wilt openen, geeft u de profiel naam op.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-176">To open other profiles, specify the profile name.</span></span> <span data-ttu-id="a5f7e-177">Als u bijvoorbeeld het profiel voor alle gebruikers van alle hosttoepassingen wilt openen, typt u:</span><span class="sxs-lookup"><span data-stu-id="a5f7e-177">For example, to open the profile for all the users of all the host applications, type:</span></span>

```powershell
notepad $PROFILE.AllUsersAllHosts
```

<span data-ttu-id="a5f7e-178">Sla het profiel bestand op en start Power shell opnieuw om de wijzigingen toe te passen.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-178">To apply the changes, save the profile file, and then restart PowerShell.</span></span>

## <a name="how-to-choose-a-profile"></a><span data-ttu-id="a5f7e-179">Een profiel kiezen</span><span class="sxs-lookup"><span data-stu-id="a5f7e-179">How to choose a profile</span></span>

<span data-ttu-id="a5f7e-180">Als u meerdere hosttoepassingen gebruikt, plaatst u de items die u in de hosttoepassingen in uw `$PROFILE.CurrentUserAllHosts` profiel gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-180">If you use multiple host applications, put the items that you use in all the host applications into your `$PROFILE.CurrentUserAllHosts` profile.</span></span> <span data-ttu-id="a5f7e-181">Plaats items die specifiek zijn voor een hosttoepassing, zoals een opdracht waarmee de achtergrond kleur voor een hosttoepassing wordt ingesteld in een profiel dat specifiek is voor die hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-181">Put items that are specific to a host application, such as a command that sets the background color for a host application, in a profile that is specific to that host application.</span></span>

<span data-ttu-id="a5f7e-182">Als u een beheerder bent die Power shell voor veel gebruikers wilt aanpassen, volgt u deze richt lijnen:</span><span class="sxs-lookup"><span data-stu-id="a5f7e-182">If you are an administrator who is customizing PowerShell for many users, follow these guidelines:</span></span>

- <span data-ttu-id="a5f7e-183">De algemene items in het `$PROFILE.AllUsersAllHosts` profiel opslaan</span><span class="sxs-lookup"><span data-stu-id="a5f7e-183">Store the common items in the `$PROFILE.AllUsersAllHosts` profile</span></span>
- <span data-ttu-id="a5f7e-184">Items die specifiek zijn voor een hosttoepassing opslaan in `$PROFILE.AllUsersCurrentHost` profielen die specifiek zijn voor de hosttoepassing</span><span class="sxs-lookup"><span data-stu-id="a5f7e-184">Store items that are specific to a host application in `$PROFILE.AllUsersCurrentHost` profiles that are specific to the host application</span></span>
- <span data-ttu-id="a5f7e-185">Items voor bepaalde gebruikers opslaan in de gebruikersspecifieke profielen</span><span class="sxs-lookup"><span data-stu-id="a5f7e-185">Store items for particular users in the user-specific profiles</span></span>

<span data-ttu-id="a5f7e-186">Controleer de documentatie van de host-toepassing voor een speciale implementatie van Power shell-profielen.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-186">Be sure to check the host application documentation for any special implementation of PowerShell profiles.</span></span>

## <a name="how-to-use-a-profile"></a><span data-ttu-id="a5f7e-187">Een profiel gebruiken</span><span class="sxs-lookup"><span data-stu-id="a5f7e-187">How to use a profile</span></span>

<span data-ttu-id="a5f7e-188">Veel van de items die u in Power Shell maakt en de meeste opdrachten die u uitvoert, zijn alleen van invloed op de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-188">Many of the items that you create in PowerShell and most commands that you run affect only the current session.</span></span> <span data-ttu-id="a5f7e-189">Wanneer u de sessie beëindigt, worden de items verwijderd.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-189">When you end the session, the items are deleted.</span></span>

<span data-ttu-id="a5f7e-190">De sessie-specifieke opdrachten en items bevatten variabelen, voorkeurs variabelen, aliassen, functies, opdrachten (met uitzonde ring van [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)) en Power shell-modules die u aan de sessie toevoegt.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-190">The session-specific commands and items include variables, preference variables, aliases, functions, commands (except for [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)), and PowerShell modules that you add to the session.</span></span>

<span data-ttu-id="a5f7e-191">Als u deze items wilt opslaan en deze beschikbaar wilt maken in alle toekomstige sessies, voegt u deze toe aan een Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-191">To save these items and make them available in all future sessions, add them to a PowerShell profile.</span></span>

<span data-ttu-id="a5f7e-192">Een ander algemeen gebruik voor profielen is het opslaan van veelgebruikte functies, aliassen en variabelen.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-192">Another common use for profiles is to save frequently-used functions, aliases, and variables.</span></span> <span data-ttu-id="a5f7e-193">Wanneer u de items in een profiel opslaat, kunt u ze in elke gewenste sessie gebruiken zonder ze opnieuw te maken.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-193">When you save the items in a profile, you can use them in any applicable session without recreating them.</span></span>

## <a name="how-to-start-a-profile"></a><span data-ttu-id="a5f7e-194">Een profiel starten</span><span class="sxs-lookup"><span data-stu-id="a5f7e-194">How to start a profile</span></span>

<span data-ttu-id="a5f7e-195">Wanneer u het profiel bestand opent, is het leeg.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-195">When you open the profile file, it is blank.</span></span> <span data-ttu-id="a5f7e-196">U kunt deze ook vullen met de variabelen, aliassen en opdrachten die u regel matig gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-196">However, you can fill it with the variables, aliases, and commands that you use frequently.</span></span>

<span data-ttu-id="a5f7e-197">Hier volgen enkele suggesties om aan de slag te gaan.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-197">Here are a few suggestions to get you started.</span></span>

### <a name="add-commands-that-make-it-easy-to-open-your-profile"></a><span data-ttu-id="a5f7e-198">Opdrachten toevoegen waarmee u uw profiel eenvoudig kunt openen</span><span class="sxs-lookup"><span data-stu-id="a5f7e-198">Add commands that make it easy to open your profile</span></span>

<span data-ttu-id="a5f7e-199">Dit is vooral handig als u een ander profiel gebruikt dan het profiel huidige gebruiker, huidige host.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-199">This is especially useful if you use a profile other than the "Current User, Current Host" profile.</span></span> <span data-ttu-id="a5f7e-200">Voeg bijvoorbeeld de volgende opdracht toe:</span><span class="sxs-lookup"><span data-stu-id="a5f7e-200">For example, add the following command:</span></span>

```powershell
function Pro {notepad $PROFILE.CurrentUserAllHosts}
```

### <a name="add-a-function-that-lists-the-aliases-for-any-cmdlet"></a><span data-ttu-id="a5f7e-201">Een functie toevoegen die de aliassen voor een wille keurige cmdlet vermeldt</span><span class="sxs-lookup"><span data-stu-id="a5f7e-201">Add a function that lists the aliases for any cmdlet</span></span>

```powershell
function Get-CmdletAlias ($cmdletname) {
  Get-Alias |
    Where-Object -FilterScript {$_.Definition -like "$cmdletname"} |
      Format-Table -Property Definition, Name -AutoSize
}
```

### <a name="customize-your-console"></a><span data-ttu-id="a5f7e-202">Uw console aanpassen</span><span class="sxs-lookup"><span data-stu-id="a5f7e-202">Customize your console</span></span>

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

### <a name="add-a-customized-powershell-prompt"></a><span data-ttu-id="a5f7e-203">Een aangepaste Power shell-prompt toevoegen</span><span class="sxs-lookup"><span data-stu-id="a5f7e-203">Add a customized PowerShell prompt</span></span>

```powershell
function Prompt
{
$env:COMPUTERNAME + "\" + (Get-Location) + "> "
}
```

<span data-ttu-id="a5f7e-204">Zie [about_Prompts](about_Prompts.md)voor meer informatie over de Power shell-prompt.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-204">For more information about the PowerShell prompt, see [about_Prompts](about_Prompts.md).</span></span>

## <a name="the-noprofile-parameter"></a><span data-ttu-id="a5f7e-205">De para meter geen profiel</span><span class="sxs-lookup"><span data-stu-id="a5f7e-205">The NoProfile parameter</span></span>

<span data-ttu-id="a5f7e-206">Als u Power shell zonder profielen wilt starten, gebruikt u de para meter geen **profiel** van **PowerShell.exe** , het programma dat Power shell start.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-206">To start PowerShell without profiles, use the **NoProfile** parameter of **PowerShell.exe** , the program that starts PowerShell.</span></span>

<span data-ttu-id="a5f7e-207">Open om te beginnen een programma dat Power shell kan starten, zoals Cmd.exe of Power shell zelf.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-207">To begin, open a program that can start PowerShell, such as Cmd.exe or PowerShell itself.</span></span> <span data-ttu-id="a5f7e-208">U kunt ook het dialoog venster uitvoeren in Windows gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-208">You can also use the Run dialog box in Windows.</span></span>

<span data-ttu-id="a5f7e-209">Type:</span><span class="sxs-lookup"><span data-stu-id="a5f7e-209">Type:</span></span>

```
PowerShell -NoProfile
```

<span data-ttu-id="a5f7e-210">Voor een volledige lijst met de para meters van PowerShell.exe, typt u:</span><span class="sxs-lookup"><span data-stu-id="a5f7e-210">For a complete list of the parameters of PowerShell.exe, type:</span></span>

```
PowerShell -?
```

## <a name="profiles-and-execution-policy"></a><span data-ttu-id="a5f7e-211">Profielen en uitvoerings beleid</span><span class="sxs-lookup"><span data-stu-id="a5f7e-211">Profiles and Execution Policy</span></span>

<span data-ttu-id="a5f7e-212">Het Power shell-uitvoerings beleid bepaalt, in deel, of u scripts kunt uitvoeren en configuratie bestanden wilt laden, inclusief de profielen.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-212">The PowerShell execution policy determines, in part, whether you can run scripts and load configuration files, including the profiles.</span></span> <span data-ttu-id="a5f7e-213">Het beleid voor **beperkte** uitvoering is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-213">The **Restricted** execution policy is the default.</span></span> <span data-ttu-id="a5f7e-214">Hiermee voor komt u dat alle scripts worden uitgevoerd, met inbegrip van de profielen.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-214">It prevents all scripts from running, including the profiles.</span></span> <span data-ttu-id="a5f7e-215">Als u het beleid ' beperkt ' gebruikt, wordt het profiel niet uitgevoerd en wordt de inhoud ervan niet toegepast.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-215">If you use the "Restricted" policy, the profile does not run, and its contents are not applied.</span></span>

<span data-ttu-id="a5f7e-216">`Set-ExecutionPolicy`Met een opdracht wordt het uitvoerings beleid ingesteld en gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-216">A `Set-ExecutionPolicy` command sets and changes your execution policy.</span></span> <span data-ttu-id="a5f7e-217">Het is een van de enkele opdrachten die van toepassing zijn in alle Power shell-sessies, omdat de waarde wordt opgeslagen in het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-217">It is one of the few commands that applies in all PowerShell sessions because the value is saved in the registry.</span></span> <span data-ttu-id="a5f7e-218">U hoeft deze niet in te stellen wanneer u de-console opent en u hoeft geen opdracht op te slaan `Set-ExecutionPolicy` in uw profiel.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-218">You do not have to set it when you open the console, and you do not have to store a `Set-ExecutionPolicy` command in your profile.</span></span>

## <a name="profiles-and-remote-sessions"></a><span data-ttu-id="a5f7e-219">Profielen en externe sessies</span><span class="sxs-lookup"><span data-stu-id="a5f7e-219">Profiles and remote sessions</span></span>

<span data-ttu-id="a5f7e-220">Power shell-profielen worden niet automatisch uitgevoerd in externe sessies, waardoor de opdrachten die de profielen toevoegen niet aanwezig zijn in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-220">PowerShell profiles are not run automatically in remote sessions, so the commands that the profiles add are not present in the remote session.</span></span> <span data-ttu-id="a5f7e-221">Daarnaast `$PROFILE` wordt de automatische variabele niet ingevuld in externe sessies.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-221">In addition, the `$PROFILE` automatic variable is not populated in remote sessions.</span></span>

<span data-ttu-id="a5f7e-222">Als u een profiel in een sessie wilt uitvoeren, gebruikt u de cmdlet [invoke-opdracht](xref:Microsoft.PowerShell.Core.Invoke-Command) .</span><span class="sxs-lookup"><span data-stu-id="a5f7e-222">To run a profile in a session, use the [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlet.</span></span>

<span data-ttu-id="a5f7e-223">Met de volgende opdracht wordt bijvoorbeeld het profiel ' huidige gebruiker, huidige host ' uitgevoerd van de lokale computer in de sessie in `$s` .</span><span class="sxs-lookup"><span data-stu-id="a5f7e-223">For example, the following command runs the "Current user, Current Host" profile from the local computer in the session in `$s`.</span></span>

```powershell
Invoke-Command -Session $s -FilePath $PROFILE
```

<span data-ttu-id="a5f7e-224">Met de volgende opdracht voert u het profiel ' huidige gebruiker, huidige host ' van de externe computer in de sessie in uit `$s` .</span><span class="sxs-lookup"><span data-stu-id="a5f7e-224">The following command runs the "Current user, Current Host" profile from the remote computer in the session in `$s`.</span></span> <span data-ttu-id="a5f7e-225">Omdat de `$PROFILE` variabele niet is ingevuld, gebruikt de opdracht het expliciete pad naar het profiel.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-225">Because the `$PROFILE` variable is not populated, the command uses the explicit path to the profile.</span></span> <span data-ttu-id="a5f7e-226">We gebruiken de operator dot sourcing zodat het profiel wordt uitgevoerd in het huidige bereik op de externe computer en niet in een eigen bereik.</span><span class="sxs-lookup"><span data-stu-id="a5f7e-226">We use dot sourcing operator so that the profile executes in the current scope on the remote computer and not in its own scope.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {
  . "$HOME\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

<span data-ttu-id="a5f7e-227">Nadat u deze opdracht hebt uitgevoerd, zijn de opdrachten die door het profiel aan de sessie worden toegevoegd, beschikbaar in `$s` .</span><span class="sxs-lookup"><span data-stu-id="a5f7e-227">After running this command, the commands that the profile adds to the session are available in `$s`.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5f7e-228">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a5f7e-228">See Also</span></span>

[<span data-ttu-id="a5f7e-229">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="a5f7e-229">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="a5f7e-230">about_Functions</span><span class="sxs-lookup"><span data-stu-id="a5f7e-230">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="a5f7e-231">about_Prompts</span><span class="sxs-lookup"><span data-stu-id="a5f7e-231">about_Prompts</span></span>](about_Prompts.md)

[<span data-ttu-id="a5f7e-232">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="a5f7e-232">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="a5f7e-233">about_Signing</span><span class="sxs-lookup"><span data-stu-id="a5f7e-233">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="a5f7e-234">about_Remote</span><span class="sxs-lookup"><span data-stu-id="a5f7e-234">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="a5f7e-235">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="a5f7e-235">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="a5f7e-236">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="a5f7e-236">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)
