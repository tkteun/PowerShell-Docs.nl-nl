---
description: Hierin worden het Power shell-uitvoerings beleid beschreven en wordt uitgelegd hoe u deze beheert.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Execution_Policies
ms.openlocfilehash: 7a20a5a3743934a5be884766956d34d52b95da5f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252348"
---
# <a name="about-execution-policies"></a><span data-ttu-id="7ef1b-104">Over uitvoerings beleid</span><span class="sxs-lookup"><span data-stu-id="7ef1b-104">About Execution Policies</span></span>

## <a name="short-description"></a><span data-ttu-id="7ef1b-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="7ef1b-105">Short Description</span></span>
<span data-ttu-id="7ef1b-106">Hierin worden het Power shell-uitvoerings beleid beschreven en wordt uitgelegd hoe u deze beheert.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-106">Describes the PowerShell execution policies and explains how to manage them.</span></span>

## <a name="long-description"></a><span data-ttu-id="7ef1b-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="7ef1b-107">Long Description</span></span>

<span data-ttu-id="7ef1b-108">Het uitvoerings beleid van Power shell is een veiligheids functie die de voor waarden bepaalt waaronder Power shell configuratie bestanden laadt en scripts uitvoert.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-108">PowerShell's execution policy is a safety feature that controls the conditions under which PowerShell loads configuration files and runs scripts.</span></span> <span data-ttu-id="7ef1b-109">Deze functie helpt de uitvoering van schadelijke scripts te voor komen.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-109">This feature helps prevent the execution of malicious scripts.</span></span>

<span data-ttu-id="7ef1b-110">Op een Windows-computer kunt u een uitvoerings beleid voor de lokale computer instellen, voor de huidige gebruiker of voor een bepaalde sessie.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-110">On a Windows computer you can set an execution policy for the local computer, for the current user, or for a particular session.</span></span> <span data-ttu-id="7ef1b-111">U kunt ook een groepsbeleid instelling gebruiken om uitvoerings beleid in te stellen voor computers en gebruikers.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-111">You can also use a Group Policy setting to set execution policies for computers and users.</span></span>

<span data-ttu-id="7ef1b-112">Uitvoerings beleid voor de lokale computer en de huidige gebruiker worden opgeslagen in het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-112">Execution policies for the local computer and current user are stored in the registry.</span></span> <span data-ttu-id="7ef1b-113">U hoeft geen uitvoerings beleid in te stellen in uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-113">You don't need to set execution policies in your PowerShell profile.</span></span>
<span data-ttu-id="7ef1b-114">Het uitvoerings beleid voor een bepaalde sessie wordt alleen in het geheugen opgeslagen en gaat verloren wanneer de sessie wordt gesloten.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-114">The execution policy for a particular session is stored only in memory and is lost when the session is closed.</span></span>

<span data-ttu-id="7ef1b-115">Het uitvoerings beleid is geen beveiligings systeem dat gebruikers acties beperkt.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-115">The execution policy isn't a security system that restricts user actions.</span></span> <span data-ttu-id="7ef1b-116">Gebruikers kunnen bijvoorbeeld eenvoudig een beleid overs Laan door de inhoud van het script te typen op de opdracht regel wanneer ze geen script kunnen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-116">For example, users can easily bypass a policy by typing the script contents at the command line when they cannot run a script.</span></span> <span data-ttu-id="7ef1b-117">Het uitvoerings beleid helpt in plaats daarvan basis regels in te stellen en voor komt dat ze per ongeluk worden geschonden.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-117">Instead, the execution policy helps users to set basic rules and prevents them from violating them unintentionally.</span></span>

<span data-ttu-id="7ef1b-118">Op niet-Windows-computers is het standaard uitvoerings beleid **onbeperkt** en kan het niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-118">On non-Windows computers, the default execution policy is **Unrestricted** and cannot be changed.</span></span> <span data-ttu-id="7ef1b-119">De `Set-ExecutionPolicy` cmdlet is beschikbaar, maar in Power shell wordt een console bericht weer gegeven dat niet wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-119">The `Set-ExecutionPolicy` cmdlet is available, but PowerShell displays a console message that it's not supported.</span></span> <span data-ttu-id="7ef1b-120">Hoewel `Get-ExecutionPolicy` retourneert **onbeperkt** op niet-Windows-platforms, komt het gedrag werkelijk overeen met **bypass** , omdat deze platformen de Windows-beveiligings zones niet implementeren.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-120">While `Get-ExecutionPolicy` returns **Unrestricted** on non-Windows platforms, the behavior really matches **Bypass** because those platforms do not implement the Windows Security Zones.</span></span>

## <a name="powershell-execution-policies"></a><span data-ttu-id="7ef1b-121">Power shell-uitvoerings beleid</span><span class="sxs-lookup"><span data-stu-id="7ef1b-121">PowerShell execution policies</span></span>

<span data-ttu-id="7ef1b-122">Het afdwingen van deze beleids regels vindt alleen plaats op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-122">Enforcement of these policies only occurs on Windows platforms.</span></span> <span data-ttu-id="7ef1b-123">Het Power shell-uitvoerings beleid is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-123">The PowerShell execution policies are as follows:</span></span>

### <a name="allsigned"></a><span data-ttu-id="7ef1b-124">Alles ondertekend</span><span class="sxs-lookup"><span data-stu-id="7ef1b-124">AllSigned</span></span>

- <span data-ttu-id="7ef1b-125">Scripts kunnen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-125">Scripts can run.</span></span>
- <span data-ttu-id="7ef1b-126">Vereist dat alle scripts en configuratie bestanden worden ondertekend door een vertrouwde uitgever, met inbegrip van scripts die u op de lokale computer schrijft.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-126">Requires that all scripts and configuration files be signed by a trusted publisher, including scripts that you write on the local computer.</span></span>
- <span data-ttu-id="7ef1b-127">Hiermee wordt u gevraagd of u scripts van uitgevers wilt uitvoeren die u nog niet hebt geclassificeerd als vertrouwd of niet-vertrouwde.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-127">Prompts you before running scripts from publishers that you haven't yet classified as trusted or untrusted.</span></span>
- <span data-ttu-id="7ef1b-128">Risico's die ondertekend zijn, maar schadelijke scripts.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-128">Risks running signed, but malicious, scripts.</span></span>

### <a name="bypass"></a><span data-ttu-id="7ef1b-129">Bypass</span><span class="sxs-lookup"><span data-stu-id="7ef1b-129">Bypass</span></span>

- <span data-ttu-id="7ef1b-130">Er is niets geblokkeerd en er zijn geen waarschuwingen of prompts.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-130">Nothing is blocked and there are no warnings or prompts.</span></span>
- <span data-ttu-id="7ef1b-131">Dit uitvoerings beleid is ontworpen voor configuraties waarin een Power shell-script is ingebouwd in een grotere toepassing of voor configuraties waarin Power shell de basis vormt voor een programma dat een eigen beveiligings model heeft.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-131">This execution policy is designed for configurations in which a PowerShell script is built in to a larger application or for configurations in which PowerShell is the foundation for a program that has its own security model.</span></span>

### <a name="default"></a><span data-ttu-id="7ef1b-132">Standaard</span><span class="sxs-lookup"><span data-stu-id="7ef1b-132">Default</span></span>

- <span data-ttu-id="7ef1b-133">Hiermee stelt u het standaard uitvoerings beleid in.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-133">Sets the default execution policy.</span></span>
- <span data-ttu-id="7ef1b-134">**Beperkt** voor Windows-clients.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-134">**Restricted** for Windows clients.</span></span>
- <span data-ttu-id="7ef1b-135">**RemoteSigned** voor Windows-servers.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-135">**RemoteSigned** for Windows servers.</span></span>

### <a name="remotesigned"></a><span data-ttu-id="7ef1b-136">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="7ef1b-136">RemoteSigned</span></span>

- <span data-ttu-id="7ef1b-137">Het standaard uitvoerings beleid voor Windows Server-computers.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-137">The default execution policy for Windows server computers.</span></span>
- <span data-ttu-id="7ef1b-138">Scripts kunnen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-138">Scripts can run.</span></span>
- <span data-ttu-id="7ef1b-139">Vereist een digitale hand tekening van een vertrouwde uitgever op scripts en configuratie bestanden die worden gedownload van het Internet, waaronder e-mail en chat Programma's.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-139">Requires a digital signature from a trusted publisher on scripts and configuration files that are downloaded from the internet which includes email and instant messaging programs.</span></span>
- <span data-ttu-id="7ef1b-140">Vereist geen digitale hand tekeningen voor scripts die zijn geschreven op de lokale computer en niet vanaf internet zijn gedownload.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-140">Doesn't require digital signatures on scripts that are written on the local computer and not downloaded from the internet.</span></span>
- <span data-ttu-id="7ef1b-141">Voert scripts uit die zijn gedownload van het internet en niet zijn ondertekend, als de blok kering van de scripts is opgeheven, bijvoorbeeld door gebruik te maken van de `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-141">Runs scripts that are downloaded from the internet and not signed, if the scripts are unblocked, such as by using the `Unblock-File` cmdlet.</span></span>
- <span data-ttu-id="7ef1b-142">Risico's voor het uitvoeren van niet-ondertekende scripts uit andere bronnen dan het internet en ondertekende scripts die schadelijk kunnen zijn.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-142">Risks running unsigned scripts from sources other than the internet and signed scripts that could be malicious.</span></span>

### <a name="restricted"></a><span data-ttu-id="7ef1b-143">Beperkt</span><span class="sxs-lookup"><span data-stu-id="7ef1b-143">Restricted</span></span>

- <span data-ttu-id="7ef1b-144">Het standaard uitvoerings beleid voor Windows-client computers.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-144">The default execution policy for Windows client computers.</span></span>
- <span data-ttu-id="7ef1b-145">Maakt afzonderlijke opdrachten mogelijk, maar staat geen scripts toe.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-145">Permits individual commands, but does not allow scripts.</span></span>
- <span data-ttu-id="7ef1b-146">Hiermee wordt voor komen dat alle script bestanden worden uitgevoerd, inclusief opmaak-en configuratie bestanden ( `.ps1xml` ), module script bestanden ( `.psm1` ) en Power shell-profielen ( `.ps1` ).</span><span class="sxs-lookup"><span data-stu-id="7ef1b-146">Prevents running of all script files, including formatting and configuration files (`.ps1xml`), module script files (`.psm1`), and PowerShell profiles (`.ps1`).</span></span>

### <a name="undefined"></a><span data-ttu-id="7ef1b-147">Undefined</span><span class="sxs-lookup"><span data-stu-id="7ef1b-147">Undefined</span></span>

- <span data-ttu-id="7ef1b-148">Er is geen uitvoerings beleid ingesteld in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-148">There is no execution policy set in the current scope.</span></span>
- <span data-ttu-id="7ef1b-149">Als het uitvoerings beleid in alle bereiken niet is **gedefinieerd** , wordt het effectief uitvoerings beleid **beperkt** voor Windows-clients en **RemoteSigned** voor Windows Server.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-149">If the execution policy in all scopes is **Undefined** , the effective execution policy is **Restricted** for Windows clients and **RemoteSigned** for Windows Server.</span></span>

### <a name="unrestricted"></a><span data-ttu-id="7ef1b-150">Onbeperkt</span><span class="sxs-lookup"><span data-stu-id="7ef1b-150">Unrestricted</span></span>

- <span data-ttu-id="7ef1b-151">Het standaard uitvoerings beleid voor niet-Windows-computers en kan niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-151">The default execution policy for non-Windows computers and cannot be changed.</span></span>
- <span data-ttu-id="7ef1b-152">Niet-ondertekende scripts kunnen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-152">Unsigned scripts can run.</span></span> <span data-ttu-id="7ef1b-153">Er is een risico op het uitvoeren van schadelijke scripts.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-153">There is a risk of running malicious scripts.</span></span>
- <span data-ttu-id="7ef1b-154">Waarschuwt de gebruiker voordat scripts en configuratie bestanden worden uitgevoerd die niet afkomstig zijn uit de zone Lokaal intranet.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-154">Warns the user before running scripts and configuration files that are not from the local intranet zone.</span></span>

> [!NOTE]
> <span data-ttu-id="7ef1b-155">Op systemen die geen UNC-paden (Universal Naming Convention) van Internet paden onderscheiden, mogen scripts die door een UNC-pad worden geïdentificeerd, mogelijk niet worden uitgevoerd met het **RemoteSigned** -uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-155">On systems that do not distinguish Universal Naming Convention (UNC) paths from internet paths, scripts that are identified by a UNC path might not be permitted to run with the **RemoteSigned** execution policy.</span></span>

## <a name="execution-policy-scope"></a><span data-ttu-id="7ef1b-156">Bereik van uitvoerings beleid</span><span class="sxs-lookup"><span data-stu-id="7ef1b-156">Execution policy scope</span></span>

<span data-ttu-id="7ef1b-157">U kunt een uitvoerings beleid instellen dat alleen effectief is in een bepaald bereik.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-157">You can set an execution policy that is effective only in a particular scope.</span></span>

<span data-ttu-id="7ef1b-158">De geldige waarden voor **Scope** zijn **MachinePolicy** , **User Policy** , **process** , **CurrentUser** en **LocalMachine**.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-158">The valid values for **Scope** are **MachinePolicy** , **UserPolicy** , **Process** , **CurrentUser** , and **LocalMachine**.</span></span> <span data-ttu-id="7ef1b-159">**LocalMachine** is de standaard instelling bij het instellen van een uitvoerings beleid.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-159">**LocalMachine** is the default when setting an execution policy.</span></span>

<span data-ttu-id="7ef1b-160">De **bereik** waarden worden weer gegeven in volg orde van prioriteit.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-160">The **Scope** values are listed in precedence order.</span></span> <span data-ttu-id="7ef1b-161">Het beleid dat prioriteit krijgt, is effectief in de huidige sessie, zelfs als een meer beperkend beleid is ingesteld op een lager niveau van prioriteit.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-161">The policy that takes precedence is effective in the current session, even if a more restrictive policy was set at a lower level of precedence.</span></span>

<span data-ttu-id="7ef1b-162">Zie [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-162">For more information, see [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy).</span></span>

### <a name="machinepolicy"></a><span data-ttu-id="7ef1b-163">MachinePolicy</span><span class="sxs-lookup"><span data-stu-id="7ef1b-163">MachinePolicy</span></span>

<span data-ttu-id="7ef1b-164">Ingesteld door een groepsbeleid voor alle gebruikers van de computer.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-164">Set by a Group Policy for all users of the computer.</span></span>

### <a name="userpolicy"></a><span data-ttu-id="7ef1b-165">User Policy</span><span class="sxs-lookup"><span data-stu-id="7ef1b-165">UserPolicy</span></span>

<span data-ttu-id="7ef1b-166">Ingesteld door een groepsbeleid voor de huidige gebruiker van de computer.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-166">Set by a Group Policy for the current user of the computer.</span></span>

### <a name="process"></a><span data-ttu-id="7ef1b-167">Proces</span><span class="sxs-lookup"><span data-stu-id="7ef1b-167">Process</span></span>

<span data-ttu-id="7ef1b-168">Het **proces** bereik is alleen van invloed op de huidige Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-168">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="7ef1b-169">Het uitvoerings beleid wordt opgeslagen in de omgevings variabele in `$env:PSExecutionPolicyPreference` plaats van het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-169">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference`, rather than the registry.</span></span> <span data-ttu-id="7ef1b-170">Wanneer de Power shell-sessie wordt gesloten, worden de variabele en de waarde verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-170">When the PowerShell session is closed, the variable and value are deleted.</span></span>

### <a name="currentuser"></a><span data-ttu-id="7ef1b-171">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="7ef1b-171">CurrentUser</span></span>

<span data-ttu-id="7ef1b-172">Het uitvoerings beleid is alleen van invloed op de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-172">The execution policy affects only the current user.</span></span> <span data-ttu-id="7ef1b-173">Deze wordt opgeslagen in de registersubsleutel **HKEY_CURRENT_USER** .</span><span class="sxs-lookup"><span data-stu-id="7ef1b-173">It's stored in the **HKEY_CURRENT_USER** registry subkey.</span></span>

### <a name="localmachine"></a><span data-ttu-id="7ef1b-174">LocalMachine</span><span class="sxs-lookup"><span data-stu-id="7ef1b-174">LocalMachine</span></span>

<span data-ttu-id="7ef1b-175">Het uitvoerings beleid is van invloed op alle gebruikers op de huidige computer.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-175">The execution policy affects all users on the current computer.</span></span> <span data-ttu-id="7ef1b-176">Deze wordt opgeslagen in de registersubsleutel **HKEY_LOCAL_MACHINE** .</span><span class="sxs-lookup"><span data-stu-id="7ef1b-176">It's stored in the **HKEY_LOCAL_MACHINE** registry subkey.</span></span>

## <a name="managing-the-execution-policy-with-powershell"></a><span data-ttu-id="7ef1b-177">Het uitvoerings beleid beheren met Power shell</span><span class="sxs-lookup"><span data-stu-id="7ef1b-177">Managing the execution policy with PowerShell</span></span>

<span data-ttu-id="7ef1b-178">Gebruik de cmdlet om het effectief uitvoerings beleid voor de huidige Power shell-sessie te verkrijgen `Get-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="7ef1b-178">To get the effective execution policy for the current PowerShell session, use the `Get-ExecutionPolicy` cmdlet.</span></span>

<span data-ttu-id="7ef1b-179">Met de volgende opdracht wordt het effectief uitvoerings beleid opgehaald:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-179">The following command gets the effective execution policy:</span></span>

```powershell
Get-ExecutionPolicy
```

<span data-ttu-id="7ef1b-180">Ga als volgt te werk om alle uitvoerings beleidsregels op te halen die van invloed zijn op de huidige sessie en deze weer te geven in volg orde:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-180">To get all of the execution policies that affect the current session and display them in precedence order:</span></span>

```powershell
Get-ExecutionPolicy -List
```

<span data-ttu-id="7ef1b-181">Het resultaat ziet er ongeveer uit als in de volgende voorbeeld uitvoer:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-181">The result looks similar to the following sample output:</span></span>

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine       AllSigned
```

<span data-ttu-id="7ef1b-182">In dit geval is het effectief uitvoerings beleid **RemoteSigned** omdat het uitvoerings beleid voor de huidige gebruiker voor rang heeft op het uitvoerings beleid dat is ingesteld voor de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-182">In this case, the effective execution policy is **RemoteSigned** because the execution policy for the current user takes precedence over the execution policy set for the local computer.</span></span>

<span data-ttu-id="7ef1b-183">Als u wilt ophalen van het uitvoerings beleid dat is ingesteld voor een bepaald bereik, gebruikt u de para meter **bereik** van `Get-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="7ef1b-183">To get the execution policy set for a particular scope, use the **Scope** parameter of `Get-ExecutionPolicy`.</span></span>

<span data-ttu-id="7ef1b-184">Met de volgende opdracht wordt bijvoorbeeld het uitvoerings beleid voor het bereik **CurrentUser** opgehaald:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-184">For example, the following command gets the execution policy for the **CurrentUser** scope:</span></span>

```powershell
Get-ExecutionPolicy -Scope CurrentUser
```

### <a name="change-the-execution-policy"></a><span data-ttu-id="7ef1b-185">Het uitvoerings beleid wijzigen</span><span class="sxs-lookup"><span data-stu-id="7ef1b-185">Change the execution policy</span></span>

<span data-ttu-id="7ef1b-186">Als u het Power shell-uitvoerings beleid wilt wijzigen op uw Windows-computer, gebruikt u de `Set-ExecutionPolicy` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-186">To change the PowerShell execution policy on your Windows computer, use the `Set-ExecutionPolicy` cmdlet.</span></span> <span data-ttu-id="7ef1b-187">De wijziging is direct van kracht.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-187">The change is effective immediately.</span></span> <span data-ttu-id="7ef1b-188">U hoeft Power shell niet opnieuw te starten.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-188">You don't need to restart PowerShell.</span></span>

<span data-ttu-id="7ef1b-189">Als u het uitvoerings beleid voor de scopes **LocalMachine** of de **CurrentUser** instelt, wordt de wijziging opgeslagen in het REGI ster en blijft deze geldig totdat u deze opnieuw wijzigt.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-189">If you set the execution policy for the scopes **LocalMachine** or the **CurrentUser** , the change is saved in the registry and remains effective until you change it again.</span></span>

<span data-ttu-id="7ef1b-190">Als u het uitvoerings beleid voor het **proces** bereik instelt, wordt het niet opgeslagen in het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-190">If you set the execution policy for the **Process** scope, it's not saved in the registry.</span></span> <span data-ttu-id="7ef1b-191">Het uitvoerings beleid wordt bewaard totdat het huidige proces en alle onderliggende processen worden gesloten.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-191">The execution policy is retained until the current process and any child processes are closed.</span></span>

> [!NOTE]
> <span data-ttu-id="7ef1b-192">In Windows Vista en latere versies van Windows, voor het uitvoeren van opdrachten waarmee het uitvoerings beleid voor de lokale computer wordt gewijzigd, **LocalMachine** bereik, start Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="7ef1b-192">In Windows Vista and later versions of Windows, to run commands that change the execution policy for the local computer, **LocalMachine** scope, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="7ef1b-193">Het uitvoerings beleid wijzigen:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-193">To change your execution policy:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName>
```

<span data-ttu-id="7ef1b-194">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-194">For example:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

<span data-ttu-id="7ef1b-195">Het uitvoerings beleid instellen in een bepaald bereik:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-195">To set the execution policy in a particular scope:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName> -Scope <scope>
```

<span data-ttu-id="7ef1b-196">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-196">For example:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

<span data-ttu-id="7ef1b-197">Een opdracht voor het wijzigen van een uitvoerings beleid kan slagen, maar nog steeds niet het daad werkelijke uitvoerings beleid wijzigen.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-197">A command to change an execution policy can succeed but still not change the effective execution policy.</span></span>

<span data-ttu-id="7ef1b-198">Een opdracht waarmee het uitvoerings beleid voor de lokale computer wordt ingesteld, kan bijvoorbeeld slagen, maar worden overschreven door het uitvoerings beleid voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-198">For example, a command that sets the execution policy for the local computer can succeed but be overridden by the execution policy for the current user.</span></span>

### <a name="remove-the-execution-policy"></a><span data-ttu-id="7ef1b-199">Het uitvoerings beleid verwijderen</span><span class="sxs-lookup"><span data-stu-id="7ef1b-199">Remove the execution policy</span></span>

<span data-ttu-id="7ef1b-200">Als u het uitvoerings beleid voor een bepaald bereik wilt verwijderen, stelt u het uitvoerings beleid in op **ongedefinieerd**.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-200">To remove the execution policy for a particular scope, set the execution policy to **Undefined**.</span></span>

<span data-ttu-id="7ef1b-201">U kunt bijvoorbeeld het uitvoerings beleid voor alle gebruikers van de lokale computer verwijderen:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-201">For example, to remove the execution policy for all the users of the local computer:</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope LocalMachine
```

<span data-ttu-id="7ef1b-202">Het uitvoerings beleid voor een **Scope** verwijderen:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-202">To remove the execution policy for a **Scope** :</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
```

<span data-ttu-id="7ef1b-203">Als er geen uitvoerings beleid is ingesteld in een bereik, wordt het effectief uitvoerings beleid **beperkt**. Dit is de standaard instelling voor Windows-clients.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-203">If no execution policy is set in any scope, the effective execution policy is **Restricted** , which is the default for Windows clients.</span></span>

### <a name="set-a-different-policy-for-one-session"></a><span data-ttu-id="7ef1b-204">Een ander beleid voor één sessie instellen</span><span class="sxs-lookup"><span data-stu-id="7ef1b-204">Set a different policy for one session</span></span>

<span data-ttu-id="7ef1b-205">U kunt de para meter **ExecutionPolicy** van **pwsh.exe** gebruiken om een uitvoerings beleid voor een nieuwe Power shell-sessie in te stellen.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-205">You can use the **ExecutionPolicy** parameter of **pwsh.exe** to set an execution policy for a new PowerShell session.</span></span> <span data-ttu-id="7ef1b-206">Het beleid is alleen van invloed op de huidige sessie en onderliggende sessies.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-206">The policy affects only the current session and child sessions.</span></span>

<span data-ttu-id="7ef1b-207">Als u het uitvoerings beleid voor een nieuwe sessie wilt instellen, start u Power shell op de opdracht regel, zoals **cmd.exe** of vanuit Power shell. vervolgens gebruikt u de para meter **ExecutionPolicy** van **pwsh.exe** om het uitvoerings beleid in te stellen.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-207">To set the execution policy for a new session, start PowerShell at the command line, such as **cmd.exe** or from PowerShell, and then use the **ExecutionPolicy** parameter of **pwsh.exe** to set the execution policy.</span></span>

<span data-ttu-id="7ef1b-208">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-208">For example:</span></span>

```powershell
pwsh.exe -ExecutionPolicy AllSigned
```

<span data-ttu-id="7ef1b-209">Het uitvoerings beleid dat u instelt, wordt niet opgeslagen in het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-209">The execution policy that you set isn't stored in the registry.</span></span> <span data-ttu-id="7ef1b-210">In plaats daarvan wordt het opgeslagen in de `$env:PSExecutionPolicyPreference` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-210">Instead, it's stored in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="7ef1b-211">De variabele wordt verwijderd wanneer u de sessie sluit waarin het beleid is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-211">The variable is deleted when you close the session in which the policy is set.</span></span> <span data-ttu-id="7ef1b-212">U kunt het beleid niet wijzigen door de waarde van de variabele te bewerken.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-212">You cannot change the policy by editing the variable value.</span></span>

<span data-ttu-id="7ef1b-213">Tijdens de sessie heeft het uitvoerings beleid dat is ingesteld voor de sessie voor rang op een uitvoerings beleid dat is ingesteld in het REGI ster voor de lokale computer of de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-213">During the session, the execution policy that is set for the session takes precedence over an execution policy that is set in the registry for the local computer or current user.</span></span> <span data-ttu-id="7ef1b-214">Het heeft echter geen voor rang op het uitvoerings beleid dat is ingesteld met behulp van een groepsbeleid.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-214">However, it doesn't take precedence over the execution policy set by using a Group Policy.</span></span>

## <a name="use-group-policy-to-manage-execution-policy"></a><span data-ttu-id="7ef1b-215">Het uitvoerings beleid beheren met groepsbeleid</span><span class="sxs-lookup"><span data-stu-id="7ef1b-215">Use Group Policy to Manage Execution Policy</span></span>

<span data-ttu-id="7ef1b-216">U kunt de instelling **Script Execution Groepsbeleid inschakelen** gebruiken om het uitvoerings beleid van computers in uw onderneming te beheren.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-216">You can use the **Turn on Script Execution** Group Policy setting to manage the execution policy of computers in your enterprise.</span></span> <span data-ttu-id="7ef1b-217">De instelling groepsbeleid overschrijft het uitvoerings beleid dat in Power shell in alle bereiken is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-217">The Group Policy setting overrides the execution policies set in PowerShell in all scopes.</span></span>

<span data-ttu-id="7ef1b-218">De beleids instellingen **voor het uitvoeren van scripts** worden als volgt ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-218">The **Turn on Script Execution** policy settings are as follows:</span></span>

- <span data-ttu-id="7ef1b-219">Als u het **uitvoeren van scripts** uitschakelt, worden scripts niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-219">If you disable **Turn on Script Execution** , scripts do not run.</span></span> <span data-ttu-id="7ef1b-220">Dit is gelijk aan het beleid voor **beperkte** uitvoering.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-220">This is equivalent to the **Restricted** execution policy.</span></span>
- <span data-ttu-id="7ef1b-221">Als u het **uitvoeren van scripts** inschakelen inschakelt, kunt u een uitvoerings beleid selecteren.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-221">If you enable **Turn on Script Execution** , you can select an execution policy.</span></span> <span data-ttu-id="7ef1b-222">De groepsbeleid-instellingen zijn gelijk aan de volgende beleids instellingen voor uitvoering:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-222">The Group Policy settings are equivalent to the following execution policy settings:</span></span>

  | <span data-ttu-id="7ef1b-223">Groepsbeleid</span><span class="sxs-lookup"><span data-stu-id="7ef1b-223">Group Policy</span></span>                                  | <span data-ttu-id="7ef1b-224">Uitvoerings beleid</span><span class="sxs-lookup"><span data-stu-id="7ef1b-224">Execution Policy</span></span> |
  | --------------------------------------------- | ---------------- |
  | <span data-ttu-id="7ef1b-225">Alle scripts toestaan</span><span class="sxs-lookup"><span data-stu-id="7ef1b-225">Allow all scripts</span></span>                             | <span data-ttu-id="7ef1b-226">Onbeperkt</span><span class="sxs-lookup"><span data-stu-id="7ef1b-226">Unrestricted</span></span>     |
  | <span data-ttu-id="7ef1b-227">Lokale scripts en externe ondertekende scripts toestaan</span><span class="sxs-lookup"><span data-stu-id="7ef1b-227">Allow local scripts and remote signed scripts</span></span> | <span data-ttu-id="7ef1b-228">RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="7ef1b-228">RemoteSigned</span></span>     |
  | <span data-ttu-id="7ef1b-229">Alleen ondertekende scripts toestaan</span><span class="sxs-lookup"><span data-stu-id="7ef1b-229">Allow only signed scripts</span></span>                     | <span data-ttu-id="7ef1b-230">Alles ondertekend</span><span class="sxs-lookup"><span data-stu-id="7ef1b-230">AllSigned</span></span>        |

- <span data-ttu-id="7ef1b-231">Als het **uitvoeren van scripts** niet is geconfigureerd, heeft dit geen effect.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-231">If **Turn on Script Execution** is not configured, it has no effect.</span></span> <span data-ttu-id="7ef1b-232">Het uitvoerings beleid dat is ingesteld in Power shell is effectief.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-232">The execution policy set in PowerShell is effective.</span></span>

<span data-ttu-id="7ef1b-233">De bestanden PowerShellExecutionPolicy. adm en PowerShellExecutionPolicy. ADMX Voeg het beleid **voor het uitvoeren van scripts** voor de computer configuratie en gebruikers configuratie knooppunten in Groepsbeleid editor in de volgende paden toe.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-233">The PowerShellExecutionPolicy.adm and PowerShellExecutionPolicy.admx files add the **Turn on Script Execution** policy to the Computer Configuration and User Configuration nodes in Group Policy Editor in the following paths.</span></span>

<span data-ttu-id="7ef1b-234">Voor Windows XP en Windows Server 2003:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-234">For Windows XP and Windows Server 2003:</span></span>

<span data-ttu-id="7ef1b-235">Gebruikersconfiguratie\beheersjablonen\windows-onderdelen\Windows Power shell voor beheer</span><span class="sxs-lookup"><span data-stu-id="7ef1b-235">Administrative Templates\Windows Components\Windows PowerShell</span></span>

<span data-ttu-id="7ef1b-236">Voor Windows Vista en latere versies van Windows:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-236">For Windows Vista and later versions of Windows:</span></span>

<span data-ttu-id="7ef1b-237">Beheer Templates\Classic Beheersjablonen </span><span class="sxs-lookup"><span data-stu-id="7ef1b-237">Administrative Templates\Classic Administrative Templates</span></span>\
<span data-ttu-id="7ef1b-238">Windows Gebruikersconfiguratie\beheersjablonen\windows-onderdelen\Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="7ef1b-238">Windows Components\Windows PowerShell</span></span>

<span data-ttu-id="7ef1b-239">Beleids regels die in het knoop punt computer configuratie zijn ingesteld, hebben voor rang op beleids regels die zijn ingesteld in het knoop punt gebruikers configuratie.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-239">Policies set in the Computer Configuration node take precedence over policies set in the User Configuration node.</span></span>

<span data-ttu-id="7ef1b-240">Zie [about_Group_Policy_Settings](about_Group_Policy_Settings.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-240">For more information, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

### <a name="execution-policy-precedence"></a><span data-ttu-id="7ef1b-241">Prioriteit van uitvoerings beleid</span><span class="sxs-lookup"><span data-stu-id="7ef1b-241">Execution policy precedence</span></span>

<span data-ttu-id="7ef1b-242">Bij het bepalen van het effectief uitvoerings beleid voor een sessie, evalueert Power shell het uitvoerings beleid in de volgende volg orde:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-242">When determining the effective execution policy for a session, PowerShell evaluates the execution policies in the following precedence order:</span></span>

- <span data-ttu-id="7ef1b-243">Groepsbeleid: MachinePolicy</span><span class="sxs-lookup"><span data-stu-id="7ef1b-243">Group Policy: MachinePolicy</span></span>
- <span data-ttu-id="7ef1b-244">Groepsbeleid: User Policy</span><span class="sxs-lookup"><span data-stu-id="7ef1b-244">Group Policy: UserPolicy</span></span>
- <span data-ttu-id="7ef1b-245">Uitvoerings beleid: proces (of `pwsh.exe -ExecutionPolicy` )</span><span class="sxs-lookup"><span data-stu-id="7ef1b-245">Execution Policy: Process (or `pwsh.exe -ExecutionPolicy`)</span></span>
- <span data-ttu-id="7ef1b-246">Uitvoerings beleid: CurrentUser</span><span class="sxs-lookup"><span data-stu-id="7ef1b-246">Execution Policy: CurrentUser</span></span>
- <span data-ttu-id="7ef1b-247">Uitvoerings beleid: LocalMachine</span><span class="sxs-lookup"><span data-stu-id="7ef1b-247">Execution Policy: LocalMachine</span></span>

## <a name="manage-signed-and-unsigned-scripts"></a><span data-ttu-id="7ef1b-248">Ondertekende en niet-ondertekende scripts beheren</span><span class="sxs-lookup"><span data-stu-id="7ef1b-248">Manage signed and unsigned scripts</span></span>

<span data-ttu-id="7ef1b-249">In Windows kunnen Program ma's zoals Internet Explorer en micro soft Edge een alternatieve gegevens stroom toevoegen aan bestanden die worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-249">In Windows, programs like Internet Explorer and Microsoft Edge add an alternate data stream to files that are downloaded.</span></span> <span data-ttu-id="7ef1b-250">Hiermee markeert u het bestand als ' afkomstig van Internet '.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-250">This marks the file as "coming from the Internet".</span></span> <span data-ttu-id="7ef1b-251">Als uw Power shell-uitvoerings beleid **RemoteSigned** is, voert Power shell geen niet-ondertekende scripts uit die zijn gedownload van Internet en die e-mail-en chat Programma's bevatten.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-251">If your PowerShell execution policy is **RemoteSigned** , PowerShell won't run unsigned scripts that are downloaded from the internet which includes email and instant messaging programs.</span></span>

<span data-ttu-id="7ef1b-252">U kunt het script ondertekenen of ervoor kiezen om een niet-ondertekend script uit te voeren zonder het uitvoerings beleid te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-252">You can sign the script or elect to run an unsigned script without changing the execution policy.</span></span>

<span data-ttu-id="7ef1b-253">Vanaf Power Shell 3,0 kunt u de **Stream** -para meter van de `Get-Item` cmdlet gebruiken om bestanden te detecteren die zijn geblokkeerd omdat deze zijn gedownload van het internet.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-253">Beginning in PowerShell 3.0, you can use the **Stream** parameter of the `Get-Item` cmdlet to detect files that are blocked because they were downloaded from the internet.</span></span> <span data-ttu-id="7ef1b-254">Gebruik de `Unblock-File` cmdlet voor het blok keren van de scripts zodat u deze in Power shell kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-254">Use the `Unblock-File` cmdlet to unblock the scripts so that you can run them in PowerShell.</span></span>

<span data-ttu-id="7ef1b-255">Zie [about_Signing](about_Signing.md), [Get-item](xref:Microsoft.PowerShell.Management.Get-Item)en [deblokkering-bestand](xref:Microsoft.PowerShell.Utility.Unblock-File)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-255">For more information, see [about_Signing](about_Signing.md), [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item), and [Unblock-File](xref:Microsoft.PowerShell.Utility.Unblock-File).</span></span>

> [!NOTE]
> <span data-ttu-id="7ef1b-256">Andere methoden voor het downloaden van bestanden kunnen de bestanden niet markeren als afkomstig van de zone Internet.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-256">Other methods of downloading files may not mark the files as coming from the Internet Zone.</span></span> <span data-ttu-id="7ef1b-257">Voorbeelden zijn:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-257">Some examples include:</span></span>
>
> - `curl.exe`
> - `Invoke-RestMethod`
> - `Invoke-WebRequest`

## <a name="execution-policy-on-windows-server-core-and-window-nano-server"></a><span data-ttu-id="7ef1b-258">Uitvoerings beleid op Windows Server Core en Window nano server</span><span class="sxs-lookup"><span data-stu-id="7ef1b-258">Execution policy on Windows Server Core and Window Nano Server</span></span>

<span data-ttu-id="7ef1b-259">Wanneer Power shell 6 onder bepaalde voor waarden wordt uitgevoerd op Windows Server Core of Windows nano server, kan het uitvoerings beleid mislukken met de volgende fout:</span><span class="sxs-lookup"><span data-stu-id="7ef1b-259">When PowerShell 6 is run on Windows Server Core or Windows Nano Server under certain conditions, execution policies can fail with the following error:</span></span>

```Output
AuthorizationManager check failed.
At line:1 char:1
+ C:\scriptpath\scriptname.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

<span data-ttu-id="7ef1b-260">Power shell gebruikt Api's in Windows Desktop shell ( `explorer.exe` ) om de zone van een script bestand te valideren.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-260">PowerShell uses APIs in the Windows Desktop Shell (`explorer.exe`) to validate the Zone of a script file.</span></span> <span data-ttu-id="7ef1b-261">De Windows-shell is niet beschikbaar op Windows Server Core en Windows nano server.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-261">The Windows Shell is not available on Windows Server Core and Windows Nano Server.</span></span>

<span data-ttu-id="7ef1b-262">U kunt deze fout ook vinden op elk Windows-systeem als de Windows Desktop shell niet beschikbaar is of niet meer reageert.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-262">You could also get this error on any Windows system if the Windows Desktop Shell is unavailable or unresponsive.</span></span> <span data-ttu-id="7ef1b-263">Tijdens het aanmelden kan bijvoorbeeld een Power shell-aanmeldings script worden gestart voordat het Windows-bureau blad gereed is, wat een fout heeft veroorzaakt.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-263">For example, during sign on, a PowerShell logon script could start execution before the Windows Desktop is ready, resulting in failure.</span></span>

<span data-ttu-id="7ef1b-264">Voor het uitvoeren van een uitvoerings beleid voor **bypass** of **Alles ondertekend** is geen zone controle vereist waarmee het probleem wordt voor komen.</span><span class="sxs-lookup"><span data-stu-id="7ef1b-264">Using an execution policy of **ByPass** or **AllSigned** does not require a Zone check which avoids the problem.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ef1b-265">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7ef1b-265">See Also</span></span>

[<span data-ttu-id="7ef1b-266">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="7ef1b-266">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="7ef1b-267">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="7ef1b-267">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="7ef1b-268">about_Signing</span><span class="sxs-lookup"><span data-stu-id="7ef1b-268">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="7ef1b-269">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="7ef1b-269">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="7ef1b-270">Get-item</span><span class="sxs-lookup"><span data-stu-id="7ef1b-270">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

[<span data-ttu-id="7ef1b-271">Help bij Pwsh-console</span><span class="sxs-lookup"><span data-stu-id="7ef1b-271">Pwsh Console Help</span></span>](about_pwsh.md)

[<span data-ttu-id="7ef1b-272">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="7ef1b-272">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="7ef1b-273">Blok kering van bestand opheffen</span><span class="sxs-lookup"><span data-stu-id="7ef1b-273">Unblock-File</span></span>](xref:Microsoft.PowerShell.Utility.Unblock-File)
