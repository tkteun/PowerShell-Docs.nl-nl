---
description: Hierin worden het Power shell-uitvoerings beleid beschreven en wordt uitgelegd hoe u deze beheert.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Execution_Policies
ms.openlocfilehash: 3332adb76c76fa644d23060abe2af43bd45a15a6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252807"
---
# <a name="about-execution-policies"></a><span data-ttu-id="88552-104">Over uitvoerings beleid</span><span class="sxs-lookup"><span data-stu-id="88552-104">About Execution Policies</span></span>

## <a name="short-description"></a><span data-ttu-id="88552-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="88552-105">Short Description</span></span>

<span data-ttu-id="88552-106">Hierin worden het Power shell-uitvoerings beleid beschreven en wordt uitgelegd hoe u deze beheert.</span><span class="sxs-lookup"><span data-stu-id="88552-106">Describes the PowerShell execution policies and explains how to manage them.</span></span>

## <a name="long-description"></a><span data-ttu-id="88552-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="88552-107">Long Description</span></span>

<span data-ttu-id="88552-108">Het uitvoerings beleid van Power shell is een veiligheids functie die de voor waarden bepaalt waaronder Power shell configuratie bestanden laadt en scripts uitvoert.</span><span class="sxs-lookup"><span data-stu-id="88552-108">PowerShell's execution policy is a safety feature that controls the conditions under which PowerShell loads configuration files and runs scripts.</span></span> <span data-ttu-id="88552-109">Deze functie helpt de uitvoering van schadelijke scripts te voor komen.</span><span class="sxs-lookup"><span data-stu-id="88552-109">This feature helps prevent the execution of malicious scripts.</span></span>

<span data-ttu-id="88552-110">Op een Windows-computer kunt u een uitvoerings beleid voor de lokale computer instellen, voor de huidige gebruiker of voor een bepaalde sessie.</span><span class="sxs-lookup"><span data-stu-id="88552-110">On a Windows computer you can set an execution policy for the local computer, for the current user, or for a particular session.</span></span> <span data-ttu-id="88552-111">U kunt ook een groepsbeleid instelling gebruiken om uitvoerings beleid in te stellen voor computers en gebruikers.</span><span class="sxs-lookup"><span data-stu-id="88552-111">You can also use a Group Policy setting to set execution policies for computers and users.</span></span>

<span data-ttu-id="88552-112">Uitvoerings beleid voor de lokale computer en de huidige gebruiker worden opgeslagen in het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="88552-112">Execution policies for the local computer and current user are stored in the registry.</span></span> <span data-ttu-id="88552-113">U hoeft geen uitvoerings beleid in te stellen in uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="88552-113">You don't need to set execution policies in your PowerShell profile.</span></span>
<span data-ttu-id="88552-114">Het uitvoerings beleid voor een bepaalde sessie wordt alleen in het geheugen opgeslagen en gaat verloren wanneer de sessie wordt gesloten.</span><span class="sxs-lookup"><span data-stu-id="88552-114">The execution policy for a particular session is stored only in memory and is lost when the session is closed.</span></span>

<span data-ttu-id="88552-115">Het uitvoerings beleid is geen beveiligings systeem dat gebruikers acties beperkt.</span><span class="sxs-lookup"><span data-stu-id="88552-115">The execution policy isn't a security system that restricts user actions.</span></span> <span data-ttu-id="88552-116">Gebruikers kunnen bijvoorbeeld eenvoudig een beleid overs Laan door de inhoud van het script te typen op de opdracht regel wanneer ze geen script kunnen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="88552-116">For example, users can easily bypass a policy by typing the script contents at the command line when they cannot run a script.</span></span> <span data-ttu-id="88552-117">Het uitvoerings beleid helpt in plaats daarvan basis regels in te stellen en voor komt dat ze per ongeluk worden geschonden.</span><span class="sxs-lookup"><span data-stu-id="88552-117">Instead, the execution policy helps users to set basic rules and prevents them from violating them unintentionally.</span></span>

## <a name="powershell-execution-policies"></a><span data-ttu-id="88552-118">Power shell-uitvoerings beleid</span><span class="sxs-lookup"><span data-stu-id="88552-118">PowerShell execution policies</span></span>

<span data-ttu-id="88552-119">Het Power shell-uitvoerings beleid is als volgt:</span><span class="sxs-lookup"><span data-stu-id="88552-119">The PowerShell execution policies are as follows:</span></span>

### <a name="allsigned"></a><span data-ttu-id="88552-120">Alles ondertekend</span><span class="sxs-lookup"><span data-stu-id="88552-120">AllSigned</span></span>

- <span data-ttu-id="88552-121">Scripts kunnen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="88552-121">Scripts can run.</span></span>
- <span data-ttu-id="88552-122">Vereist dat alle scripts en configuratie bestanden worden ondertekend door een vertrouwde uitgever, met inbegrip van scripts die u op de lokale computer schrijft.</span><span class="sxs-lookup"><span data-stu-id="88552-122">Requires that all scripts and configuration files be signed by a trusted publisher, including scripts that you write on the local computer.</span></span>
- <span data-ttu-id="88552-123">Hiermee wordt u gevraagd of u scripts van uitgevers wilt uitvoeren die u nog niet hebt geclassificeerd als vertrouwd of niet-vertrouwde.</span><span class="sxs-lookup"><span data-stu-id="88552-123">Prompts you before running scripts from publishers that you haven't yet classified as trusted or untrusted.</span></span>
- <span data-ttu-id="88552-124">Risico's die ondertekend zijn, maar schadelijke scripts.</span><span class="sxs-lookup"><span data-stu-id="88552-124">Risks running signed, but malicious, scripts.</span></span>

### <a name="bypass"></a><span data-ttu-id="88552-125">Bypass</span><span class="sxs-lookup"><span data-stu-id="88552-125">Bypass</span></span>

- <span data-ttu-id="88552-126">Er is niets geblokkeerd en er zijn geen waarschuwingen of prompts.</span><span class="sxs-lookup"><span data-stu-id="88552-126">Nothing is blocked and there are no warnings or prompts.</span></span>
- <span data-ttu-id="88552-127">Dit uitvoerings beleid is ontworpen voor configuraties waarin een Power shell-script is ingebouwd in een grotere toepassing of voor configuraties waarin Power shell de basis vormt voor een programma dat een eigen beveiligings model heeft.</span><span class="sxs-lookup"><span data-stu-id="88552-127">This execution policy is designed for configurations in which a PowerShell script is built in to a larger application or for configurations in which PowerShell is the foundation for a program that has its own security model.</span></span>

### <a name="default"></a><span data-ttu-id="88552-128">Standaard</span><span class="sxs-lookup"><span data-stu-id="88552-128">Default</span></span>

- <span data-ttu-id="88552-129">Hiermee stelt u het standaard uitvoerings beleid in.</span><span class="sxs-lookup"><span data-stu-id="88552-129">Sets the default execution policy.</span></span>
- <span data-ttu-id="88552-130">**Beperkt** voor Windows-clients.</span><span class="sxs-lookup"><span data-stu-id="88552-130">**Restricted** for Windows clients.</span></span>
- <span data-ttu-id="88552-131">**RemoteSigned** voor Windows-servers.</span><span class="sxs-lookup"><span data-stu-id="88552-131">**RemoteSigned** for Windows servers.</span></span>

### <a name="remotesigned"></a><span data-ttu-id="88552-132">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="88552-132">RemoteSigned</span></span>

- <span data-ttu-id="88552-133">Het standaard uitvoerings beleid voor Windows Server-computers.</span><span class="sxs-lookup"><span data-stu-id="88552-133">The default execution policy for Windows server computers.</span></span>
- <span data-ttu-id="88552-134">Scripts kunnen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="88552-134">Scripts can run.</span></span>
- <span data-ttu-id="88552-135">Vereist een digitale hand tekening van een vertrouwde uitgever op scripts en configuratie bestanden die worden gedownload van het Internet, waaronder e-mail en chat Programma's.</span><span class="sxs-lookup"><span data-stu-id="88552-135">Requires a digital signature from a trusted publisher on scripts and configuration files that are downloaded from the internet which includes email and instant messaging programs.</span></span>
- <span data-ttu-id="88552-136">Vereist geen digitale hand tekeningen voor scripts die zijn geschreven op de lokale computer en niet vanaf internet zijn gedownload.</span><span class="sxs-lookup"><span data-stu-id="88552-136">Doesn't require digital signatures on scripts that are written on the local computer and not downloaded from the internet.</span></span>
- <span data-ttu-id="88552-137">Voert scripts uit die zijn gedownload van het internet en niet zijn ondertekend, als de blok kering van de scripts is opgeheven, bijvoorbeeld door gebruik te maken van de `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="88552-137">Runs scripts that are downloaded from the internet and not signed, if the scripts are unblocked, such as by using the `Unblock-File` cmdlet.</span></span>
- <span data-ttu-id="88552-138">Risico's voor het uitvoeren van niet-ondertekende scripts uit andere bronnen dan het internet en ondertekende scripts die schadelijk kunnen zijn.</span><span class="sxs-lookup"><span data-stu-id="88552-138">Risks running unsigned scripts from sources other than the internet and signed scripts that could be malicious.</span></span>

### <a name="restricted"></a><span data-ttu-id="88552-139">Beperkt</span><span class="sxs-lookup"><span data-stu-id="88552-139">Restricted</span></span>

- <span data-ttu-id="88552-140">Het standaard uitvoerings beleid voor Windows-client computers.</span><span class="sxs-lookup"><span data-stu-id="88552-140">The default execution policy for Windows client computers.</span></span>
- <span data-ttu-id="88552-141">Maakt afzonderlijke opdrachten mogelijk, maar staat geen scripts toe.</span><span class="sxs-lookup"><span data-stu-id="88552-141">Permits individual commands, but does not allow scripts.</span></span>
- <span data-ttu-id="88552-142">Hiermee wordt voor komen dat alle script bestanden worden uitgevoerd, inclusief opmaak-en configuratie bestanden ( `.ps1xml` ), module script bestanden ( `.psm1` ) en Power shell-profielen ( `.ps1` ).</span><span class="sxs-lookup"><span data-stu-id="88552-142">Prevents running of all script files, including formatting and configuration files (`.ps1xml`), module script files (`.psm1`), and PowerShell profiles (`.ps1`).</span></span>

### <a name="undefined"></a><span data-ttu-id="88552-143">Undefined</span><span class="sxs-lookup"><span data-stu-id="88552-143">Undefined</span></span>

- <span data-ttu-id="88552-144">Er is geen uitvoerings beleid ingesteld in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="88552-144">There is no execution policy set in the current scope.</span></span>
- <span data-ttu-id="88552-145">Als het uitvoerings beleid in alle bereiken niet is **gedefinieerd** , wordt het effectief uitvoerings beleid **beperkt** voor Windows-clients en **RemoteSigned** voor Windows Server.</span><span class="sxs-lookup"><span data-stu-id="88552-145">If the execution policy in all scopes is **Undefined** , the effective execution policy is **Restricted** for Windows clients and **RemoteSigned** for Windows Server.</span></span>

### <a name="unrestricted"></a><span data-ttu-id="88552-146">Onbeperkt</span><span class="sxs-lookup"><span data-stu-id="88552-146">Unrestricted</span></span>

- <span data-ttu-id="88552-147">Niet-ondertekende scripts kunnen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="88552-147">Unsigned scripts can run.</span></span> <span data-ttu-id="88552-148">Er is een risico op het uitvoeren van schadelijke scripts.</span><span class="sxs-lookup"><span data-stu-id="88552-148">There is a risk of running malicious scripts.</span></span>
- <span data-ttu-id="88552-149">Waarschuwt de gebruiker voordat scripts en configuratie bestanden worden uitgevoerd die niet afkomstig zijn uit de zone Lokaal intranet.</span><span class="sxs-lookup"><span data-stu-id="88552-149">Warns the user before running scripts and configuration files that are not from the local intranet zone.</span></span>

> [!NOTE]
> <span data-ttu-id="88552-150">Op systemen die geen UNC-paden (Universal Naming Convention) van Internet paden onderscheiden, mogen scripts die door een UNC-pad worden geïdentificeerd, mogelijk niet worden uitgevoerd met het **RemoteSigned** -uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="88552-150">On systems that do not distinguish Universal Naming Convention (UNC) paths from internet paths, scripts that are identified by a UNC path might not be permitted to run with the **RemoteSigned** execution policy.</span></span>

## <a name="execution-policy-scope"></a><span data-ttu-id="88552-151">Bereik van uitvoerings beleid</span><span class="sxs-lookup"><span data-stu-id="88552-151">Execution policy scope</span></span>

<span data-ttu-id="88552-152">U kunt een uitvoerings beleid instellen dat alleen effectief is in een bepaald bereik.</span><span class="sxs-lookup"><span data-stu-id="88552-152">You can set an execution policy that is effective only in a particular scope.</span></span>

<span data-ttu-id="88552-153">De geldige waarden voor **Scope** zijn **MachinePolicy** , **User Policy** , **process** , **CurrentUser** en **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="88552-153">The valid values for **Scope** are **MachinePolicy** , **UserPolicy** , **Process** , **CurrentUser** , and **LocalMachine**.</span></span> <span data-ttu-id="88552-154">**LocalMachine** is de standaard instelling bij het instellen van een uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="88552-154">**LocalMachine** is the default when setting an execution policy.</span></span>

<span data-ttu-id="88552-155">De **bereik** waarden worden weer gegeven in volg orde van prioriteit.</span><span class="sxs-lookup"><span data-stu-id="88552-155">The **Scope** values are listed in precedence order.</span></span> <span data-ttu-id="88552-156">Het beleid dat prioriteit krijgt, is effectief in de huidige sessie, zelfs als een meer beperkend beleid is ingesteld op een lager niveau van prioriteit.</span><span class="sxs-lookup"><span data-stu-id="88552-156">The policy that takes precedence is effective in the current session, even if a more restrictive policy was set at a lower level of precedence.</span></span>

<span data-ttu-id="88552-157">Zie [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="88552-157">For more information, see [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy).</span></span>

### <a name="machinepolicy"></a><span data-ttu-id="88552-158">MachinePolicy</span><span class="sxs-lookup"><span data-stu-id="88552-158">MachinePolicy</span></span>

<span data-ttu-id="88552-159">Ingesteld door een groepsbeleid voor alle gebruikers van de computer.</span><span class="sxs-lookup"><span data-stu-id="88552-159">Set by a Group Policy for all users of the computer.</span></span>

### <a name="userpolicy"></a><span data-ttu-id="88552-160">User Policy</span><span class="sxs-lookup"><span data-stu-id="88552-160">UserPolicy</span></span>

<span data-ttu-id="88552-161">Ingesteld door een groepsbeleid voor de huidige gebruiker van de computer.</span><span class="sxs-lookup"><span data-stu-id="88552-161">Set by a Group Policy for the current user of the computer.</span></span>

### <a name="process"></a><span data-ttu-id="88552-162">Proces</span><span class="sxs-lookup"><span data-stu-id="88552-162">Process</span></span>

<span data-ttu-id="88552-163">Het **proces** bereik is alleen van invloed op de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="88552-163">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="88552-164">Het uitvoerings beleid wordt opgeslagen in de omgevings variabele in `$env:PSExecutionPolicyPreference` plaats van het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="88552-164">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference`, rather than the registry.</span></span> <span data-ttu-id="88552-165">Wanneer de Power shell-sessie wordt gesloten, worden de variabele en de waarde verwijderd.</span><span class="sxs-lookup"><span data-stu-id="88552-165">When the PowerShell session is closed, the variable and value are deleted.</span></span>

### <a name="currentuser"></a><span data-ttu-id="88552-166">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="88552-166">CurrentUser</span></span>

<span data-ttu-id="88552-167">Het uitvoerings beleid is alleen van invloed op de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="88552-167">The execution policy affects only the current user.</span></span> <span data-ttu-id="88552-168">Deze wordt opgeslagen in de registersubsleutel **HKEY_CURRENT_USER** .</span><span class="sxs-lookup"><span data-stu-id="88552-168">It's stored in the **HKEY_CURRENT_USER** registry subkey.</span></span>

### <a name="localmachine"></a><span data-ttu-id="88552-169">LocalMachine</span><span class="sxs-lookup"><span data-stu-id="88552-169">LocalMachine</span></span>

<span data-ttu-id="88552-170">Het uitvoerings beleid is van invloed op alle gebruikers op de huidige computer.</span><span class="sxs-lookup"><span data-stu-id="88552-170">The execution policy affects all users on the current computer.</span></span> <span data-ttu-id="88552-171">Deze wordt opgeslagen in de registersubsleutel **HKEY_LOCAL_MACHINE** .</span><span class="sxs-lookup"><span data-stu-id="88552-171">It's stored in the **HKEY_LOCAL_MACHINE** registry subkey.</span></span>

## <a name="managing-the-execution-policy-with-powershell"></a><span data-ttu-id="88552-172">Het uitvoerings beleid beheren met Power shell</span><span class="sxs-lookup"><span data-stu-id="88552-172">Managing the execution policy with PowerShell</span></span>

<span data-ttu-id="88552-173">Gebruik de cmdlet om het effectief uitvoerings beleid voor de huidige Power shell-sessie te verkrijgen `Get-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="88552-173">To get the effective execution policy for the current PowerShell session, use the `Get-ExecutionPolicy` cmdlet.</span></span>

<span data-ttu-id="88552-174">Met de volgende opdracht wordt het effectief uitvoerings beleid opgehaald:</span><span class="sxs-lookup"><span data-stu-id="88552-174">The following command gets the effective execution policy:</span></span>

```powershell
Get-ExecutionPolicy
```

<span data-ttu-id="88552-175">Ga als volgt te werk om alle uitvoerings beleidsregels op te halen die van invloed zijn op de huidige sessie en deze weer te geven in volg orde:</span><span class="sxs-lookup"><span data-stu-id="88552-175">To get all of the execution policies that affect the current session and display them in precedence order:</span></span>

```powershell
Get-ExecutionPolicy -List
```

<span data-ttu-id="88552-176">Het resultaat ziet er ongeveer uit als in de volgende voorbeeld uitvoer:</span><span class="sxs-lookup"><span data-stu-id="88552-176">The result looks similar to the following sample output:</span></span>

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine       AllSigned
```

<span data-ttu-id="88552-177">In dit geval is het effectief uitvoerings beleid **RemoteSigned** omdat het uitvoerings beleid voor de huidige gebruiker voor rang heeft op het uitvoerings beleid dat is ingesteld voor de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="88552-177">In this case, the effective execution policy is **RemoteSigned** because the execution policy for the current user takes precedence over the execution policy set for the local computer.</span></span>

<span data-ttu-id="88552-178">Als u wilt ophalen van het uitvoerings beleid dat is ingesteld voor een bepaald bereik, gebruikt u de para meter **bereik** van `Get-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="88552-178">To get the execution policy set for a particular scope, use the **Scope** parameter of `Get-ExecutionPolicy`.</span></span>

<span data-ttu-id="88552-179">Met de volgende opdracht wordt bijvoorbeeld het uitvoerings beleid voor het bereik **CurrentUser** opgehaald:</span><span class="sxs-lookup"><span data-stu-id="88552-179">For example, the following command gets the execution policy for the **CurrentUser** scope:</span></span>

```powershell
Get-ExecutionPolicy -Scope CurrentUser
```

### <a name="change-the-execution-policy"></a><span data-ttu-id="88552-180">Het uitvoerings beleid wijzigen</span><span class="sxs-lookup"><span data-stu-id="88552-180">Change the execution policy</span></span>

<span data-ttu-id="88552-181">Als u het Power shell-uitvoerings beleid wilt wijzigen op uw Windows-computer, gebruikt u de `Set-ExecutionPolicy` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="88552-181">To change the PowerShell execution policy on your Windows computer, use the `Set-ExecutionPolicy` cmdlet.</span></span> <span data-ttu-id="88552-182">De wijziging is direct van kracht.</span><span class="sxs-lookup"><span data-stu-id="88552-182">The change is effective immediately.</span></span> <span data-ttu-id="88552-183">U hoeft Power shell niet opnieuw te starten.</span><span class="sxs-lookup"><span data-stu-id="88552-183">You don't need to restart PowerShell.</span></span>

<span data-ttu-id="88552-184">Als u het uitvoerings beleid voor de scopes **LocalMachine** of de **CurrentUser** instelt, wordt de wijziging opgeslagen in het REGI ster en blijft deze geldig totdat u deze opnieuw wijzigt.</span><span class="sxs-lookup"><span data-stu-id="88552-184">If you set the execution policy for the scopes **LocalMachine** or the **CurrentUser** , the change is saved in the registry and remains effective until you change it again.</span></span>

<span data-ttu-id="88552-185">Als u het uitvoerings beleid voor het **proces** bereik instelt, wordt het niet opgeslagen in het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="88552-185">If you set the execution policy for the **Process** scope, it's not saved in the registry.</span></span> <span data-ttu-id="88552-186">Het uitvoerings beleid wordt bewaard totdat het huidige proces en alle onderliggende processen worden gesloten.</span><span class="sxs-lookup"><span data-stu-id="88552-186">The execution policy is retained until the current process and any child processes are closed.</span></span>

> [!NOTE]
> <span data-ttu-id="88552-187">In Windows Vista en latere versies van Windows, voor het uitvoeren van opdrachten waarmee het uitvoerings beleid voor de lokale computer wordt gewijzigd, **LocalMachine** bereik, start Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="88552-187">In Windows Vista and later versions of Windows, to run commands that change the execution policy for the local computer, **LocalMachine** scope, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="88552-188">Het uitvoerings beleid wijzigen:</span><span class="sxs-lookup"><span data-stu-id="88552-188">To change your execution policy:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName>
```

<span data-ttu-id="88552-189">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="88552-189">For example:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="88552-190">Het uitvoerings beleid instellen in een bepaald bereik:</span><span class="sxs-lookup"><span data-stu-id="88552-190">To set the execution policy in a particular scope:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName> -Scope <scope>
```

<span data-ttu-id="88552-191">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="88552-191">For example:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

<span data-ttu-id="88552-192">Een opdracht voor het wijzigen van een uitvoerings beleid kan slagen, maar nog steeds niet het daad werkelijke uitvoerings beleid wijzigen.</span><span class="sxs-lookup"><span data-stu-id="88552-192">A command to change an execution policy can succeed but still not change the effective execution policy.</span></span>

<span data-ttu-id="88552-193">Een opdracht waarmee het uitvoerings beleid voor de lokale computer wordt ingesteld, kan bijvoorbeeld slagen, maar worden overschreven door het uitvoerings beleid voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="88552-193">For example, a command that sets the execution policy for the local computer can succeed but be overridden by the execution policy for the current user.</span></span>

### <a name="remove-the-execution-policy"></a><span data-ttu-id="88552-194">Het uitvoerings beleid verwijderen</span><span class="sxs-lookup"><span data-stu-id="88552-194">Remove the execution policy</span></span>

<span data-ttu-id="88552-195">Als u het uitvoerings beleid voor een bepaald bereik wilt verwijderen, stelt u het uitvoerings beleid in op **ongedefinieerd**.</span><span class="sxs-lookup"><span data-stu-id="88552-195">To remove the execution policy for a particular scope, set the execution policy to **Undefined**.</span></span>

<span data-ttu-id="88552-196">U kunt bijvoorbeeld het uitvoerings beleid voor alle gebruikers van de lokale computer verwijderen:</span><span class="sxs-lookup"><span data-stu-id="88552-196">For example, to remove the execution policy for all the users of the local computer:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope LocalMachine
```

<span data-ttu-id="88552-197">Het uitvoerings beleid voor een **Scope** verwijderen:</span><span class="sxs-lookup"><span data-stu-id="88552-197">To remove the execution policy for a **Scope** :</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
```

<span data-ttu-id="88552-198">Als er geen uitvoerings beleid is ingesteld in een bereik, wordt het effectief uitvoerings beleid **beperkt**. Dit is de standaard instelling voor Windows-clients.</span><span class="sxs-lookup"><span data-stu-id="88552-198">If no execution policy is set in any scope, the effective execution policy is **Restricted** , which is the default for Windows clients.</span></span>

### <a name="set-a-different-policy-for-one-session"></a><span data-ttu-id="88552-199">Een ander beleid voor één sessie instellen</span><span class="sxs-lookup"><span data-stu-id="88552-199">Set a different policy for one session</span></span>

<span data-ttu-id="88552-200">U kunt de para meter **ExecutionPolicy** van **powershell.exe** gebruiken om een uitvoerings beleid voor een nieuwe Power shell-sessie in te stellen.</span><span class="sxs-lookup"><span data-stu-id="88552-200">You can use the **ExecutionPolicy** parameter of **powershell.exe** to set an execution policy for a new PowerShell session.</span></span> <span data-ttu-id="88552-201">Het beleid is alleen van invloed op de huidige sessie en onderliggende sessies.</span><span class="sxs-lookup"><span data-stu-id="88552-201">The policy affects only the current session and child sessions.</span></span>

<span data-ttu-id="88552-202">Als u het uitvoerings beleid voor een nieuwe sessie wilt instellen, start u Power shell op de opdracht regel, zoals **cmd.exe** of vanuit Power shell. vervolgens gebruikt u de para meter **ExecutionPolicy** van **powershell.exe** om het uitvoerings beleid in te stellen.</span><span class="sxs-lookup"><span data-stu-id="88552-202">To set the execution policy for a new session, start PowerShell at the command line, such as **cmd.exe** or from PowerShell, and then use the **ExecutionPolicy** parameter of **powershell.exe** to set the execution policy.</span></span>

<span data-ttu-id="88552-203">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="88552-203">For example:</span></span>

```powershell
powershell.exe -ExecutionPolicy AllSigned
```

<span data-ttu-id="88552-204">Het uitvoerings beleid dat u instelt, wordt niet opgeslagen in het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="88552-204">The execution policy that you set isn't stored in the registry.</span></span> <span data-ttu-id="88552-205">In plaats daarvan wordt het opgeslagen in de `$env:PSExecutionPolicyPreference` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="88552-205">Instead, it's stored in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="88552-206">De variabele wordt verwijderd wanneer u de sessie sluit waarin het beleid is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="88552-206">The variable is deleted when you close the session in which the policy is set.</span></span> <span data-ttu-id="88552-207">U kunt het beleid niet wijzigen door de waarde van de variabele te bewerken.</span><span class="sxs-lookup"><span data-stu-id="88552-207">You cannot change the policy by editing the variable value.</span></span>

<span data-ttu-id="88552-208">Tijdens de sessie heeft het uitvoerings beleid dat is ingesteld voor de sessie voor rang op een uitvoerings beleid dat is ingesteld in het REGI ster voor de lokale computer of de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="88552-208">During the session, the execution policy that is set for the session takes precedence over an execution policy that is set in the registry for the local computer or current user.</span></span> <span data-ttu-id="88552-209">Het heeft echter geen voor rang op het uitvoerings beleid dat is ingesteld met behulp van een groepsbeleid.</span><span class="sxs-lookup"><span data-stu-id="88552-209">However, it doesn't take precedence over the execution policy set by using a Group Policy.</span></span>

## <a name="use-group-policy-to-manage-execution-policy"></a><span data-ttu-id="88552-210">Het uitvoerings beleid beheren met groepsbeleid</span><span class="sxs-lookup"><span data-stu-id="88552-210">Use Group Policy to Manage Execution Policy</span></span>

<span data-ttu-id="88552-211">U kunt de instelling **Script Execution Groepsbeleid inschakelen** gebruiken om het uitvoerings beleid van computers in uw onderneming te beheren.</span><span class="sxs-lookup"><span data-stu-id="88552-211">You can use the **Turn on Script Execution** Group Policy setting to manage the execution policy of computers in your enterprise.</span></span> <span data-ttu-id="88552-212">De instelling groepsbeleid overschrijft het uitvoerings beleid dat in Power shell in alle bereiken is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="88552-212">The Group Policy setting overrides the execution policies set in PowerShell in all scopes.</span></span>

<span data-ttu-id="88552-213">De beleids instellingen **voor het uitvoeren van scripts** worden als volgt ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="88552-213">The **Turn on Script Execution** policy settings are as follows:</span></span>

- <span data-ttu-id="88552-214">Als u het **uitvoeren van scripts** uitschakelt, worden scripts niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="88552-214">If you disable **Turn on Script Execution** , scripts do not run.</span></span> <span data-ttu-id="88552-215">Dit is gelijk aan het beleid voor **beperkte** uitvoering.</span><span class="sxs-lookup"><span data-stu-id="88552-215">This is equivalent to the **Restricted** execution policy.</span></span>
- <span data-ttu-id="88552-216">Als u het **uitvoeren van scripts** inschakelen inschakelt, kunt u een uitvoerings beleid selecteren.</span><span class="sxs-lookup"><span data-stu-id="88552-216">If you enable **Turn on Script Execution** , you can select an execution policy.</span></span> <span data-ttu-id="88552-217">De groepsbeleid-instellingen zijn gelijk aan de volgende beleids instellingen voor uitvoering:</span><span class="sxs-lookup"><span data-stu-id="88552-217">The Group Policy settings are equivalent to the following execution policy settings:</span></span>

  | <span data-ttu-id="88552-218">Groepsbeleid</span><span class="sxs-lookup"><span data-stu-id="88552-218">Group Policy</span></span>                                  | <span data-ttu-id="88552-219">Uitvoerings beleid</span><span class="sxs-lookup"><span data-stu-id="88552-219">Execution Policy</span></span> |
  | --------------------------------------------- | ---------------- |
  | <span data-ttu-id="88552-220">Alle scripts toestaan</span><span class="sxs-lookup"><span data-stu-id="88552-220">Allow all scripts</span></span>                             | <span data-ttu-id="88552-221">Onbeperkt</span><span class="sxs-lookup"><span data-stu-id="88552-221">Unrestricted</span></span>     |
  | <span data-ttu-id="88552-222">Lokale scripts en externe ondertekende scripts toestaan</span><span class="sxs-lookup"><span data-stu-id="88552-222">Allow local scripts and remote signed scripts</span></span> | <span data-ttu-id="88552-223">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="88552-223">RemoteSigned</span></span>     |
  | <span data-ttu-id="88552-224">Alleen ondertekende scripts toestaan</span><span class="sxs-lookup"><span data-stu-id="88552-224">Allow only signed scripts</span></span>                     | <span data-ttu-id="88552-225">Alles ondertekend</span><span class="sxs-lookup"><span data-stu-id="88552-225">AllSigned</span></span>        |

- <span data-ttu-id="88552-226">Als het **uitvoeren van scripts** niet is geconfigureerd, heeft dit geen effect.</span><span class="sxs-lookup"><span data-stu-id="88552-226">If **Turn on Script Execution** is not configured, it has no effect.</span></span> <span data-ttu-id="88552-227">Het uitvoerings beleid dat is ingesteld in Power shell is effectief.</span><span class="sxs-lookup"><span data-stu-id="88552-227">The execution policy set in PowerShell is effective.</span></span>

<span data-ttu-id="88552-228">De bestanden PowerShellExecutionPolicy. adm en PowerShellExecutionPolicy. ADMX Voeg het beleid **voor het uitvoeren van scripts** voor de computer configuratie en gebruikers configuratie knooppunten in Groepsbeleid editor in de volgende paden toe.</span><span class="sxs-lookup"><span data-stu-id="88552-228">The PowerShellExecutionPolicy.adm and PowerShellExecutionPolicy.admx files add the **Turn on Script Execution** policy to the Computer Configuration and User Configuration nodes in Group Policy Editor in the following paths.</span></span>

<span data-ttu-id="88552-229">Voor Windows XP en Windows Server 2003:</span><span class="sxs-lookup"><span data-stu-id="88552-229">For Windows XP and Windows Server 2003:</span></span>

<span data-ttu-id="88552-230">Gebruikersconfiguratie\beheersjablonen\windows-onderdelen\Windows Power shell voor beheer</span><span class="sxs-lookup"><span data-stu-id="88552-230">Administrative Templates\Windows Components\Windows PowerShell</span></span>

<span data-ttu-id="88552-231">Voor Windows Vista en latere versies van Windows:</span><span class="sxs-lookup"><span data-stu-id="88552-231">For Windows Vista and later versions of Windows:</span></span>

<span data-ttu-id="88552-232">Beheer Templates\Classic Beheersjablonen </span><span class="sxs-lookup"><span data-stu-id="88552-232">Administrative Templates\Classic Administrative Templates</span></span>\
<span data-ttu-id="88552-233">Windows Gebruikersconfiguratie\beheersjablonen\windows-onderdelen\Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="88552-233">Windows Components\Windows PowerShell</span></span>

<span data-ttu-id="88552-234">Beleids regels die in het knoop punt computer configuratie zijn ingesteld, hebben voor rang op beleids regels die zijn ingesteld in het knoop punt gebruikers configuratie.</span><span class="sxs-lookup"><span data-stu-id="88552-234">Policies set in the Computer Configuration node take precedence over policies set in the User Configuration node.</span></span>

<span data-ttu-id="88552-235">Zie [about_Group_Policy_Settings](about_Group_Policy_Settings.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="88552-235">For more information, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

### <a name="execution-policy-precedence"></a><span data-ttu-id="88552-236">Prioriteit van uitvoerings beleid</span><span class="sxs-lookup"><span data-stu-id="88552-236">Execution policy precedence</span></span>

<span data-ttu-id="88552-237">Bij het bepalen van het effectief uitvoerings beleid voor een sessie, evalueert Power shell het uitvoerings beleid in de volgende volg orde:</span><span class="sxs-lookup"><span data-stu-id="88552-237">When determining the effective execution policy for a session, PowerShell evaluates the execution policies in the following precedence order:</span></span>

- <span data-ttu-id="88552-238">Groepsbeleid: MachinePolicy</span><span class="sxs-lookup"><span data-stu-id="88552-238">Group Policy: MachinePolicy</span></span>
- <span data-ttu-id="88552-239">Groepsbeleid: User Policy</span><span class="sxs-lookup"><span data-stu-id="88552-239">Group Policy: UserPolicy</span></span>
- <span data-ttu-id="88552-240">Uitvoerings beleid: proces (of `powershell.exe -ExecutionPolicy` )</span><span class="sxs-lookup"><span data-stu-id="88552-240">Execution Policy: Process (or `powershell.exe -ExecutionPolicy`)</span></span>
- <span data-ttu-id="88552-241">Uitvoerings beleid: CurrentUser</span><span class="sxs-lookup"><span data-stu-id="88552-241">Execution Policy: CurrentUser</span></span>
- <span data-ttu-id="88552-242">Uitvoerings beleid: LocalMachine</span><span class="sxs-lookup"><span data-stu-id="88552-242">Execution Policy: LocalMachine</span></span>

## <a name="manage-signed-and-unsigned-scripts"></a><span data-ttu-id="88552-243">Ondertekende en niet-ondertekende scripts beheren</span><span class="sxs-lookup"><span data-stu-id="88552-243">Manage signed and unsigned scripts</span></span>

<span data-ttu-id="88552-244">In Windows kunnen Program ma's zoals Internet Explorer en micro soft Edge een alternatieve gegevens stroom toevoegen aan bestanden die worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="88552-244">In Windows, programs like Internet Explorer and Microsoft Edge add an alternate data stream to files that are downloaded.</span></span> <span data-ttu-id="88552-245">Hiermee markeert u het bestand als ' afkomstig van Internet '.</span><span class="sxs-lookup"><span data-stu-id="88552-245">This marks the file as "coming from the Internet".</span></span> <span data-ttu-id="88552-246">Als uw Power shell-uitvoerings beleid **RemoteSigned** is, voert Power shell geen niet-ondertekende scripts uit die zijn gedownload van Internet en die e-mail-en chat Programma's bevatten.</span><span class="sxs-lookup"><span data-stu-id="88552-246">If your PowerShell execution policy is **RemoteSigned** , PowerShell won't run unsigned scripts that are downloaded from the internet which includes email and instant messaging programs.</span></span>

<span data-ttu-id="88552-247">U kunt het script ondertekenen of ervoor kiezen om een niet-ondertekend script uit te voeren zonder het uitvoerings beleid te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="88552-247">You can sign the script or elect to run an unsigned script without changing the execution policy.</span></span>

<span data-ttu-id="88552-248">Vanaf Power Shell 3,0 kunt u de **Stream** -para meter van de `Get-Item` cmdlet gebruiken om bestanden te detecteren die zijn geblokkeerd omdat deze zijn gedownload van het internet.</span><span class="sxs-lookup"><span data-stu-id="88552-248">Beginning in PowerShell 3.0, you can use the **Stream** parameter of the `Get-Item` cmdlet to detect files that are blocked because they were downloaded from the internet.</span></span> <span data-ttu-id="88552-249">Gebruik de `Unblock-File` cmdlet voor het blok keren van de scripts zodat u deze in Power shell kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="88552-249">Use the `Unblock-File` cmdlet to unblock the scripts so that you can run them in PowerShell.</span></span>

<span data-ttu-id="88552-250">Zie [about_Signing](about_Signing.md), [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)en [deblokkering-bestand](xref:Microsoft.PowerShell.Utility.Unblock-File)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="88552-250">For more information, see [about_Signing](about_Signing.md), [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item), and [Unblock-File](xref:Microsoft.PowerShell.Utility.Unblock-File).</span></span>

> [!NOTE]
> <span data-ttu-id="88552-251">Andere methoden voor het downloaden van bestanden kunnen de bestanden niet markeren als afkomstig van de zone Internet.</span><span class="sxs-lookup"><span data-stu-id="88552-251">Other methods of downloading files may not mark the files as coming from the Internet Zone.</span></span> <span data-ttu-id="88552-252">Voorbeelden zijn:</span><span class="sxs-lookup"><span data-stu-id="88552-252">Some examples include:</span></span>
>
> - `curl.exe`
> - `Invoke-RestMethod`
> - `Invoke-WebRequest`

## <a name="execution-policy-on-windows-server-core-and-window-nano-server"></a><span data-ttu-id="88552-253">Uitvoerings beleid op Windows Server Core en Window nano server</span><span class="sxs-lookup"><span data-stu-id="88552-253">Execution policy on Windows Server Core and Window Nano Server</span></span>

<span data-ttu-id="88552-254">Wanneer Power shell 5,1 onder bepaalde omstandigheden wordt uitgevoerd op Windows Server Core of Windows nano server, kan het uitvoerings beleid mislukken met de volgende fout:</span><span class="sxs-lookup"><span data-stu-id="88552-254">When PowerShell 5.1 is run on Windows Server Core or Windows Nano Server under certain conditions, execution policies can fail with the following error:</span></span>

```Output
AuthorizationManager check failed.
At line:1 char:1
+ C:\scriptpath\scriptname.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

<span data-ttu-id="88552-255">Power shell gebruikt Api's in Windows Desktop shell ( `explorer.exe` ) om de zone van een script bestand te valideren.</span><span class="sxs-lookup"><span data-stu-id="88552-255">PowerShell uses APIs in the Windows Desktop Shell (`explorer.exe`) to validate the Zone of a script file.</span></span> <span data-ttu-id="88552-256">De Windows-shell is niet beschikbaar op Windows Server Core en Windows nano server.</span><span class="sxs-lookup"><span data-stu-id="88552-256">The Windows Shell is not available on Windows Server Core and Windows Nano Server.</span></span>

<span data-ttu-id="88552-257">U kunt deze fout ook vinden op elk Windows-systeem als de Windows Desktop shell niet beschikbaar is of niet meer reageert.</span><span class="sxs-lookup"><span data-stu-id="88552-257">You could also get this error on any Windows system if the Windows Desktop Shell is unavailable or unresponsive.</span></span> <span data-ttu-id="88552-258">Tijdens het aanmelden kan bijvoorbeeld een Power shell-aanmeldings script worden gestart voordat het Windows-bureau blad gereed is, wat een fout heeft veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="88552-258">For example, during sign on, a PowerShell logon script could start execution before the Windows Desktop is ready, resulting in failure.</span></span>

<span data-ttu-id="88552-259">Voor het uitvoeren van een uitvoerings beleid voor **bypass** of **Alles ondertekend** is geen zone controle vereist waarmee het probleem wordt voor komen.</span><span class="sxs-lookup"><span data-stu-id="88552-259">Using an execution policy of **ByPass** or **AllSigned** does not require a Zone check which avoids the problem.</span></span>

## <a name="see-also"></a><span data-ttu-id="88552-260">Zie ook</span><span class="sxs-lookup"><span data-stu-id="88552-260">See Also</span></span>

[<span data-ttu-id="88552-261">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="88552-261">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="88552-262">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="88552-262">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="88552-263">about_Signing</span><span class="sxs-lookup"><span data-stu-id="88552-263">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="88552-264">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="88552-264">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="88552-265">Get-item</span><span class="sxs-lookup"><span data-stu-id="88552-265">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

[<span data-ttu-id="88552-266">PowerShell.exe Command-Line Help</span><span class="sxs-lookup"><span data-stu-id="88552-266">PowerShell.exe Command-Line Help</span></span>](about_PowerShell_exe.md)

[<span data-ttu-id="88552-267">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="88552-267">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="88552-268">Blok kering van bestand opheffen</span><span class="sxs-lookup"><span data-stu-id="88552-268">Unblock-File</span></span>](xref:Microsoft.PowerShell.Utility.Unblock-File)
