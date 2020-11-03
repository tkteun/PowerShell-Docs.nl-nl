---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionoption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionOption
ms.openlocfilehash: c8d51054b2beb4da0e7d54280d85b9688928147e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251295"
---
# <span data-ttu-id="7c1c0-103">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="7c1c0-103">New-PSSessionOption</span></span>

## <span data-ttu-id="7c1c0-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7c1c0-104">SYNOPSIS</span></span>
<span data-ttu-id="7c1c0-105">Hiermee maakt u een object dat geavanceerde opties bevat voor een PSSession.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-105">Creates an object that contains advanced options for a PSSession.</span></span>

## <span data-ttu-id="7c1c0-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7c1c0-106">SYNTAX</span></span>

```
New-PSSessionOption [-MaximumRedirection <Int32>] [-NoCompression] [-NoMachineProfile] [-Culture <CultureInfo>]
 [-UICulture <CultureInfo>] [-MaximumReceivedDataSizePerCommand <Int32>] [-MaximumReceivedObjectSize <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-MaxConnectionRetryCount <Int32>]
 [-ApplicationArguments <PSPrimitiveDictionary>] [-OpenTimeout <Int32>] [-CancelTimeout <Int32>]
 [-IdleTimeout <Int32>] [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <AuthenticationMechanism>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [-IncludePortInSPN] [<CommonParameters>]
```

## <span data-ttu-id="7c1c0-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7c1c0-107">DESCRIPTION</span></span>

<span data-ttu-id="7c1c0-108">De `New-PSSessionOption` cmdlet maakt een object dat geavanceerde opties bevat voor een door de gebruiker beheerde sessie ( **PSSession** ).</span><span class="sxs-lookup"><span data-stu-id="7c1c0-108">The `New-PSSessionOption` cmdlet creates an object that contains advanced options for a user-managed session ( **PSSession** ).</span></span> <span data-ttu-id="7c1c0-109">U kunt het object gebruiken als de waarde van de para meter **SessionOption** van cmdlets die een **PSSession** maken, zoals `New-PSSession` , `Enter-PSSession` , en `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="7c1c0-109">You can use the object as the value of the **SessionOption** parameter of cmdlets that create a **PSSession** , such as `New-PSSession`, `Enter-PSSession`, and `Invoke-Command`.</span></span>

<span data-ttu-id="7c1c0-110">Zonder para meters `New-PSSessionOption` genereert een object dat de standaard waarden voor alle opties bevat.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-110">Without parameters, `New-PSSessionOption` generates an object that contains the default values for all of the options.</span></span> <span data-ttu-id="7c1c0-111">Omdat alle eigenschappen kunnen worden bewerkt, kunt u het resulterende object als sjabloon gebruiken en standaard optie objecten maken voor uw onderneming.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-111">Because all of the properties can be edited, you can use the resulting object as a template, and create standard option objects for your enterprise.</span></span>

<span data-ttu-id="7c1c0-112">U kunt ook een sessie optie object opslaan in de `$PSSessionOption` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-112">You can also save a session option object in the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="7c1c0-113">Met de waarden van deze variabele worden nieuwe standaard waarden voor de sessie opties ingesteld.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-113">The values of this variable establish new default values for the session options.</span></span> <span data-ttu-id="7c1c0-114">Ze zijn effectief wanneer er geen sessie opties zijn ingesteld voor de sessie en ze hebben voor rang boven de opties die zijn ingesteld in de sessie configuratie, maar u kunt ze negeren door sessie opties of een sessie optie object op te geven in een cmdlet waarmee een sessie wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-114">They effective when no session options are set for the session and they take precedence over options set in the session configuration, but you can override them by specifying session options or a session option object in a cmdlet that creates a session.</span></span> <span data-ttu-id="7c1c0-115">Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` Voorkeurs variabele [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="7c1c0-115">For more information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="7c1c0-116">Wanneer u een sessie optie object gebruikt in een cmdlet die een sessie maakt, hebben de sessie optie waarden prioriteit boven de standaard waarden voor sessies die zijn ingesteld in de $PSSessionOption voorkeurs variabele en in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-116">When you use a session option object in a cmdlet that creates a session, the session option values take precedence over default values for sessions set in the $PSSessionOption preference variable and in the session configuration.</span></span> <span data-ttu-id="7c1c0-117">Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-117">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span> <span data-ttu-id="7c1c0-118">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-118">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="7c1c0-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7c1c0-119">EXAMPLES</span></span>

### <span data-ttu-id="7c1c0-120">Voor beeld 1: een standaard sessie maken-optie</span><span class="sxs-lookup"><span data-stu-id="7c1c0-120">Example 1: Create a default session option</span></span>

<span data-ttu-id="7c1c0-121">Met deze opdracht wordt een sessie optie object gemaakt met alle standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-121">This command creates a session option object that has all of the default values.</span></span>

```powershell
New-PSSessionOption
```

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

### <span data-ttu-id="7c1c0-122">Voor beeld 2: een sessie configureren met behulp van een sessie optie object</span><span class="sxs-lookup"><span data-stu-id="7c1c0-122">Example 2: Configure a session by using a session option object</span></span>

<span data-ttu-id="7c1c0-123">In dit voor beeld ziet u hoe u een sessie optie object gebruikt voor het configureren van een sessie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-123">This example shows how to use a session option object to configure a session.</span></span>

```powershell
$pso = New-PSSessionOption -Culture "fr-fr" -MaximumReceivedObjectSize 10MB
New-PSSession -ComputerName Server01 -SessionOption $pso
```

<span data-ttu-id="7c1c0-124">Met de eerste opdracht wordt een nieuw sessie optie object gemaakt en opgeslagen in de waarde van de `$pso` variabele.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-124">The first command creates a new session option object and saves it in the value of the `$pso` variable.</span></span> <span data-ttu-id="7c1c0-125">De tweede opdracht gebruikt de `New-PSSession` cmdlet om een sessie te maken op de externe computer Server01.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-125">The second command uses the `New-PSSession` cmdlet to create a session on the Server01 remote computer.</span></span> <span data-ttu-id="7c1c0-126">De opdracht gebruikt het object Session Option in de waarde van de `$pso` variabele als de waarde van de para meter **SessionOption** van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-126">The command uses the session option object in the value of the `$pso` variable as the value of the **SessionOption** parameter of the command.</span></span>

### <span data-ttu-id="7c1c0-127">Voor beeld 3: een interactieve sessie starten</span><span class="sxs-lookup"><span data-stu-id="7c1c0-127">Example 3: Start an interactive session</span></span>

<span data-ttu-id="7c1c0-128">Met deze opdracht wordt de `Enter-PSSession` cmdlet gebruikt om een interactieve sessie met de Server01-computer te starten.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-128">This command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

```powershell
Enter-PSSession -ComputerName Server01 -SessionOption (New-PSSessionOption -NoEncryption -NoCompression)
```

<span data-ttu-id="7c1c0-129">De waarde van de para meter **SessionOption** is een `New-PSSessionOption` opdracht met de para meters geen **versleuteling** en geen **compressie** .</span><span class="sxs-lookup"><span data-stu-id="7c1c0-129">The value of the **SessionOption** parameter is a `New-PSSessionOption` command that has the **NoEncryption** and **NoCompression** parameters.</span></span>

<span data-ttu-id="7c1c0-130">De `New-PSSessionOption` opdracht bevindt zich tussen haakjes om er zeker van te zijn dat deze vóór de opdracht wordt uitgevoerd `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="7c1c0-130">The `New-PSSessionOption` command is enclosed in parentheses to make sure that it runs before the `Enter-PSSession` command.</span></span>

### <span data-ttu-id="7c1c0-131">Voor beeld 4: een sessie optie object wijzigen</span><span class="sxs-lookup"><span data-stu-id="7c1c0-131">Example 4: Modify a session option object</span></span>

<span data-ttu-id="7c1c0-132">Dit voor beeld laat zien dat u het sessie optie object kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-132">This example demonstrates that you can modify the session option object.</span></span> <span data-ttu-id="7c1c0-133">Alle eigenschappen hebben lees-en schrijf waarden.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-133">All properties have read/write values.</span></span>

```powershell
$a = New-PSSessionOption
$a.OpenTimeout
```

```Output
Days              : 0
Hours             : 0
Minutes           : 3
Seconds           : 0
Milliseconds      : 0
Ticks             : 1800000000
TotalDays         : 0.00208333333333333
TotalHours        : 0.05
TotalMinutes      : 3
TotalSeconds      : 180
TotalMilliseconds : 180000
```

```powershell
$a.UICulture = (Get-UICulture)
$a.OpenTimeout = (New-Timespan -Minutes 4)
$a.MaximumConnectionRedirectionCount = 1
$a
```

```Output
MaximumConnectionRedirectionCount : 1
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         : en-US
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:04:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

<span data-ttu-id="7c1c0-134">Gebruik deze methode om een standaard sessie object te maken voor uw onderneming en vervolgens aangepaste versies van de toepassing te maken voor specifiek gebruik.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-134">Use this method to create a standard session object for your enterprise, and then create customized versions of it for particular uses.</span></span>

### <span data-ttu-id="7c1c0-135">Voor beeld 5: een voorkeurs variabele maken</span><span class="sxs-lookup"><span data-stu-id="7c1c0-135">Example 5: Create a preference variable</span></span>

<span data-ttu-id="7c1c0-136">Met deze opdracht maakt u een `$PSSessionOption` Voorkeurs variabele.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-136">This command creates a `$PSSessionOption` preference variable.</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -OpenTimeOut 120000
```

<span data-ttu-id="7c1c0-137">Wanneer de `$PSSessionOption` Voorkeurs variabele in de sessie plaatsvindt, worden er standaard waarden ingesteld voor opties in de sessies die worden gemaakt met behulp van de `New-PSSession` `Enter-PSSession` `Invoke-Command` cmdlets, en.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-137">When the `$PSSessionOption` preference variable occurs in the session, it establishes default values for options in the sessions that are created by using the `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="7c1c0-138">Als u de `$PSSessionOption` variabele beschikbaar wilt maken in alle sessies, voegt u deze toe aan uw Power shell-sessie en aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-138">To make the `$PSSessionOption` variable available in all sessions, add it to your PowerShell session and to your PowerShell profile.</span></span>

<span data-ttu-id="7c1c0-139">Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` Voorkeurs variabele [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="7c1c0-139">For more information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>
<span data-ttu-id="7c1c0-140">Zie [about_Profiles](About/about_Profiles.md)voor meer informatie over profielen.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-140">For more information about profiles, see [about_Profiles](About/about_Profiles.md).</span></span>

### <span data-ttu-id="7c1c0-141">Voor beeld 6: voldoen aan de vereisten voor een configuratie van een externe sessie</span><span class="sxs-lookup"><span data-stu-id="7c1c0-141">Example 6: Fulfill the requirements for a remote session configuration</span></span>

<span data-ttu-id="7c1c0-142">In dit voor beeld ziet u hoe u een **SessionOption** -object gebruikt om te voldoen aan de vereisten voor een configuratie van een externe sessie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-142">This example shows how to use a **SessionOption** object to fulfill the requirements for a remote session configuration.</span></span>

```powershell
$skipCN = New-PSSessionOption -SkipCNCheck
New-PSSession -ComputerName 171.09.21.207 -UseSSL -Credential Domain01\User01 -SessionOption $SkipCN
```

<span data-ttu-id="7c1c0-143">De eerste opdracht gebruikt de `New-PSSessionOption` cmdlet om een sessie optie object te maken met de eigenschap **SkipCNCheck** .</span><span class="sxs-lookup"><span data-stu-id="7c1c0-143">The first command uses the `New-PSSessionOption` cmdlet to create a session option object that has the **SkipCNCheck** property.</span></span> <span data-ttu-id="7c1c0-144">De opdracht slaat het resulterende sessie object op in de `$skipCN` variabele.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-144">The command saves the resulting session object in the `$skipCN` variable.</span></span>

<span data-ttu-id="7c1c0-145">Met de tweede opdracht wordt de `New-PSSession` cmdlet gebruikt om een nieuwe sessie te maken op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-145">The second command uses the `New-PSSession` cmdlet to create a new session on a remote computer.</span></span> <span data-ttu-id="7c1c0-146">De `$skipCN` controle variabele wordt gebruikt in de waarde van de para meter **SessionOption** .</span><span class="sxs-lookup"><span data-stu-id="7c1c0-146">The `$skipCN` check variable is used in the value of the **SessionOption** parameter.</span></span>

<span data-ttu-id="7c1c0-147">Omdat de computer wordt geïdentificeerd aan de hand van het IP-adres, komt de waarde van de para meter **ComputerName** niet overeen met een van de algemene namen in het certificaat dat wordt gebruikt voor Secure Sockets Layer (SSL).</span><span class="sxs-lookup"><span data-stu-id="7c1c0-147">Because the computer is identified by its IP address, the value of the **ComputerName** parameter does not match any of the common names in the certificate that is used for Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="7c1c0-148">Als gevolg hiervan is de optie **SkipCNCheck** vereist.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-148">As a result, the **SkipCNCheck** option is required.</span></span>

### <span data-ttu-id="7c1c0-149">Voor beeld 7: argumenten beschikbaar maken voor een externe sessie</span><span class="sxs-lookup"><span data-stu-id="7c1c0-149">Example 7: Make arguments available to a remote session</span></span>

<span data-ttu-id="7c1c0-150">In dit voor beeld ziet u hoe u de para meter **ApplicationArguments** van de `New-PSSessionOption` cmdlet gebruikt om extra gegevens beschikbaar te maken voor de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-150">This example shows how to use the **ApplicationArguments** parameter of the `New-PSSessionOption` cmdlet to make additional data available to the remote session.</span></span>

```powershell
$team = @{Team="IT"; Use="Testing"}
$TeamOption = New-PSSessionOption -ApplicationArguments $team
$s = New-PSSession -ComputerName Server01 -SessionOption $TeamOption
Invoke-Command -Session $s {$PSSenderInfo.ApplicationArguments}
```

```Output
Name                 Value
----                 -----
Team                 IT
Use                  Testing
PSVersionTable       {CLRVersion, BuildVersion, PSVersion, WSManStackVersion...}
```

```powershell
Invoke-Command -Session $s {
  if ($PSSenderInfo.ApplicationArguments.Use -ne "Testing") {
    .\logFiles.ps1
  }
  else {
    "Just testing."
  }
}
```

```Output
Just testing.
```

<span data-ttu-id="7c1c0-151">Met de eerste opdracht maakt u een hash-tabel met twee sleutels, **team** en **gebruik**.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-151">The first command creates a hash table with two keys, **Team** and **Use**.</span></span> <span data-ttu-id="7c1c0-152">Met de opdracht wordt de hash-tabel in de `$team` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-152">The command saves the hash table in the `$team` variable.</span></span> <span data-ttu-id="7c1c0-153">Zie [about_Hash_Tables](about/about_Hash_Tables.md)voor meer informatie over hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-153">For more information about hash tables, see [about_Hash_Tables](about/about_Hash_Tables.md).</span></span>

<span data-ttu-id="7c1c0-154">Vervolgens maakt de `New-PSSessionOption` cmdlet met de para meter **ApplicationArguments** een sessie optie object dat is opgeslagen in de `$team` variabele.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-154">Next, the `New-PSSessionOption` cmdlet, using the **ApplicationArguments** parameter, creates a session option object saved in the `$team` variable.</span></span> <span data-ttu-id="7c1c0-155">Wanneer `New-PSSessionOption` u het sessie optie object maakt, wordt de hash-tabel in de waarde van de para meter **ApplicationArguments** automatisch geconverteerd naar een primitieve woorden lijst, zodat de gegevens betrouwbaar kunnen worden verzonden naar de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-155">When `New-PSSessionOption` creates the session option object, it automatically converts the hash table in the value of the **ApplicationArguments** parameter to a primitive dictionary so the data can be reliably transmitted to the remote session.</span></span>

<span data-ttu-id="7c1c0-156">`New-PSSession`Met de cmdlet wordt een sessie gestart op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-156">The `New-PSSession` cmdlet starts a session on the Server01 computer.</span></span> <span data-ttu-id="7c1c0-157">De para meter **SessionOption** wordt gebruikt voor het toevoegen van de opties in de `$teamOption` variabele.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-157">It uses the **SessionOption** parameter to include the options in the `$teamOption` variable.</span></span>

<span data-ttu-id="7c1c0-158">De `Invoke-Command` cmdlet laat zien dat de gegevens in de `$team` variabele beschikbaar zijn voor opdrachten in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-158">The `Invoke-Command` cmdlet demonstrates that the data in the `$team` variable is available to commands in the remote session.</span></span> <span data-ttu-id="7c1c0-159">De gegevens worden weer gegeven in de eigenschap **ApplicationArguments** van de `$PSSenderInfo` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-159">The data appears in the **ApplicationArguments** property of the `$PSSenderInfo` automatic variable.</span></span>

<span data-ttu-id="7c1c0-160">In het eind `Invoke-Command` ziet u hoe de gegevens kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-160">The final `Invoke-Command` shows how the data might be used.</span></span>

## <span data-ttu-id="7c1c0-161">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7c1c0-161">PARAMETERS</span></span>

### <span data-ttu-id="7c1c0-162">-ApplicationArguments</span><span class="sxs-lookup"><span data-stu-id="7c1c0-162">-ApplicationArguments</span></span>

<span data-ttu-id="7c1c0-163">Hiermee geeft u een primitieve woorden lijst op die naar de externe sessie wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-163">Specifies a primitive dictionary that is sent to the remote session.</span></span> <span data-ttu-id="7c1c0-164">Opdrachten en scripts in de externe sessie, met inbegrip van opstart scripts in de sessie configuratie, kunnen deze woorden lijst vinden in de eigenschap **ApplicationArguments** van de `$PSSenderInfo` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-164">Commands and scripts in the remote session, including startup scripts in the session configuration, can find this dictionary in the **ApplicationArguments** property of the `$PSSenderInfo` automatic variable.</span></span> <span data-ttu-id="7c1c0-165">U kunt deze para meter gebruiken om gegevens te verzenden naar de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-165">You can use this parameter to send data to the remote session.</span></span>

<span data-ttu-id="7c1c0-166">Zie [about_Hash_Tables](about/about_Hash_Tables.md), [about_Session_Configurations](About/about_Session_Configurations.md)en [about_Automatic_Variables](about/about_Automatic_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-166">For more information, see [about_Hash_Tables](about/about_Hash_Tables.md), [about_Session_Configurations](About/about_Session_Configurations.md), and [about_Automatic_Variables](about/about_Automatic_Variables.md).</span></span>

```yaml
Type: System.Management.Automation.PSPrimitiveDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-167">-CancelTimeout</span><span class="sxs-lookup"><span data-stu-id="7c1c0-167">-CancelTimeout</span></span>

<span data-ttu-id="7c1c0-168">Hiermee wordt bepaald hoe lang Power shell wacht tot een annulerings bewerking (CTRL + C) is voltooid voordat deze wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-168">Determines how long PowerShell waits for a cancel operation (CTRL+C) to finish before ending it.</span></span>
<span data-ttu-id="7c1c0-169">Voer een waarde in milliseconden in.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-169">Enter a value in milliseconds.</span></span>

<span data-ttu-id="7c1c0-170">De standaard waarde is 60000 (één minuut).</span><span class="sxs-lookup"><span data-stu-id="7c1c0-170">The default value is 60000 (one minute).</span></span> <span data-ttu-id="7c1c0-171">Een waarde van 0 (nul) betekent geen time-out; de opdracht wordt voor onbepaalde tijd voortgezet.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-171">A value of 0 (zero) means no time-out; the command continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: CancelTimeoutMSec

Required: False
Position: Named
Default value: 60000
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-172">-Cultuur</span><span class="sxs-lookup"><span data-stu-id="7c1c0-172">-Culture</span></span>

<span data-ttu-id="7c1c0-173">Hiermee geeft u de cultuur op die voor de sessie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-173">Specifies the culture to use for the session.</span></span> <span data-ttu-id="7c1c0-174">Voer een cultuur naam in de `<languagecode2>-<country/regioncode2>` indeling (like `ja-JP` ) in, een variabele die een **Culture info** -object bevat of een opdracht waarmee een **Culture info** -object wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-174">Enter a culture name in `<languagecode2>-<country/regioncode2>` format (like `ja-JP`), a variable that contains a **CultureInfo** object, or a command that gets a **CultureInfo** object.</span></span>

<span data-ttu-id="7c1c0-175">De standaard waarde is `$Null` en de cultuur die in het besturings systeem is ingesteld, wordt in de sessie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-175">The default value is `$Null`, and the culture that is set in the operating system is used in the session.</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-176">-IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="7c1c0-176">-IdleTimeout</span></span>

<span data-ttu-id="7c1c0-177">Hiermee wordt bepaald hoe lang de sessie geopend blijft als de externe computer geen communicatie van de lokale computer ontvangt.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-177">Determines how long the session stays open if the remote computer does not receive any communication from the local computer.</span></span> <span data-ttu-id="7c1c0-178">Dit omvat het heartbeat-signaal.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-178">This includes the heartbeat signal.</span></span> <span data-ttu-id="7c1c0-179">Wanneer het interval is verlopen, wordt de sessie gesloten.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-179">When the interval expires, the session closes.</span></span>

<span data-ttu-id="7c1c0-180">De time-outwaarde voor inactiviteit is van groot belang als u van plan bent om de verbinding met een sessie te verbreken en opnieuw te verbinden.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-180">The idle time-out value is of significant importance if you intend to disconnect and reconnect to a session.</span></span> <span data-ttu-id="7c1c0-181">U kunt opnieuw verbinding maken als er geen time-out is opgetreden voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-181">You can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="7c1c0-182">Voer een waarde in milliseconden in.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-182">Enter a value in milliseconds.</span></span> <span data-ttu-id="7c1c0-183">De minimum waarde is 60000 (1 minuut).</span><span class="sxs-lookup"><span data-stu-id="7c1c0-183">The minimum value is 60000 (1 minute).</span></span> <span data-ttu-id="7c1c0-184">Het maximum is de waarde van de eigenschap **MaxIdleTimeoutms** van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-184">The maximum is the value of the **MaxIdleTimeoutms** property of the session configuration.</span></span> <span data-ttu-id="7c1c0-185">De standaard waarde,-1, heeft geen time-out voor inactiviteit.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-185">The default value, -1, does not set an idle time-out.</span></span>

<span data-ttu-id="7c1c0-186">De sessie gebruikt de time-out voor inactiviteit die is ingesteld in de sessie opties, indien van toepassing.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-186">The session uses the idle time-out that is set in the session options, if any.</span></span> <span data-ttu-id="7c1c0-187">Als geen is ingesteld (-1), gebruikt de sessie de waarde van de eigenschap **IdleTimeoutMs** van de sessie configuratie of de time-outwaarde van de WSMan-shell ( `WSMan:\<ComputerName>\Shell\IdleTimeout` ), afhankelijk van wat het kleinste is.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-187">If none is set (-1), the session uses the value of the **IdleTimeoutMs** property of the session configuration or the WSMan shell time-out value (`WSMan:\<ComputerName>\Shell\IdleTimeout`), whichever is shortest.</span></span>

<span data-ttu-id="7c1c0-188">Als de time-out voor inactiviteit in de sessie opties groter is dan de waarde van de eigenschap **MaxIdleTimeoutMs** van de sessie configuratie, mislukt de opdracht voor het maken van een sessie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-188">If the idle timeout set in the session options exceeds the value of the **MaxIdleTimeoutMs** property of the session configuration, the command to create a session fails.</span></span>

<span data-ttu-id="7c1c0-189">De **IdleTimeoutMs** -waarde van de standaard **micro soft. Power shell** -sessie configuratie is 7200000 milliseconden (2 uur).</span><span class="sxs-lookup"><span data-stu-id="7c1c0-189">The **IdleTimeoutMs** value of the default **Microsoft.PowerShell** session configuration is 7200000 milliseconds (2 hours).</span></span> <span data-ttu-id="7c1c0-190">De **MaxIdleTimeoutMs** -waarde is 2147483647 milliseconden ( \> 24 dagen).</span><span class="sxs-lookup"><span data-stu-id="7c1c0-190">Its **MaxIdleTimeoutMs** value is 2147483647 milliseconds (\>24 days).</span></span> <span data-ttu-id="7c1c0-191">De standaard waarde van de time-out voor inactiviteit van de WSMan-shell `WSMan:\<ComputerName>\Shell\IdleTimeout` is 7200000 milliseconden (2 uur).</span><span class="sxs-lookup"><span data-stu-id="7c1c0-191">The default value of the WSMan shell idle time-out (`WSMan:\<ComputerName>\Shell\IdleTimeout`) is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="7c1c0-192">De time-outwaarde voor inactiviteit van een sessie kan ook worden gewijzigd wanneer de verbinding met een sessie wordt verbroken of als er opnieuw verbinding wordt gemaakt met een sessie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-192">The idle time-out value of a session can also be changed when disconnecting from a session or reconnecting to a session.</span></span> <span data-ttu-id="7c1c0-193">Zie voor meer informatie `Disconnect-PSSession` en `Connect-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-193">For more information, see `Disconnect-PSSession` and `Connect-PSSession`.</span></span>

<span data-ttu-id="7c1c0-194">In Windows Power Shell 2,0 is de standaard waarde van de para meter **IdleTimeout** 240000 (4 minuten).</span><span class="sxs-lookup"><span data-stu-id="7c1c0-194">In Windows PowerShell 2.0, the default value of the **IdleTimeout** parameter is 240000 (4 minutes).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: IdleTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-195">-IncludePortInSPN</span><span class="sxs-lookup"><span data-stu-id="7c1c0-195">-IncludePortInSPN</span></span>

<span data-ttu-id="7c1c0-196">Bevat het poort nummer in de SPN (Service Principal Name) die voor Kerberos-verificatie wordt gebruikt, bijvoorbeeld `HTTP://<ComputerName>:5985` .</span><span class="sxs-lookup"><span data-stu-id="7c1c0-196">Includes the port number in the Service Principal Name (SPN) used for Kerberos authentication, for example, `HTTP://<ComputerName>:5985`.</span></span> <span data-ttu-id="7c1c0-197">Met deze optie kan een client die een niet-standaard SPN gebruikt, verifiëren bij een externe computer die gebruikmaakt van Kerberos-verificatie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-197">This option allows a client that uses a non-default SPN to authenticate against a remote computer that uses Kerberos authentication.</span></span>

<span data-ttu-id="7c1c0-198">De optie is ontworpen voor ondernemingen waarbij meerdere services die ondersteuning bieden voor Kerberos-verificatie worden uitgevoerd onder verschillende gebruikers accounts.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-198">The option is designed for enterprises where multiple services that support Kerberos authentication are running under different user accounts.</span></span> <span data-ttu-id="7c1c0-199">Zo kan een IIS-toepassing die Kerberos-verificatie toestaat, vereisen dat de standaard-SPN wordt geregistreerd voor een gebruikers account dat verschilt van het computer account.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-199">For example, an IIS application that allows for Kerberos authentication can require the default SPN to be registered to a user account that differs from the computer account.</span></span> <span data-ttu-id="7c1c0-200">In dergelijke gevallen kan externe communicatie van Power shell met Kerberos niet worden geverifieerd omdat hiervoor een SPN is vereist die is geregistreerd bij het computer account.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-200">In such cases, PowerShell remoting cannot use Kerberos to authenticate because it requires an SPN that is registered to the computer account.</span></span> <span data-ttu-id="7c1c0-201">Om dit probleem op te lossen, kunnen beheerders verschillende Spn's maken, zoals met behulp van **Setspn.exe** , die zijn geregistreerd voor verschillende gebruikers accounts en er onderscheid van kunnen worden gemaakt door het poort nummer in de SPN op te nemen.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-201">To resolve this problem, administrators can create different SPNs, such as by using **Setspn.exe** , that are registered to different user accounts and can distinguish between them by including the port number in the SPN.</span></span>

<span data-ttu-id="7c1c0-202">Zie [overzicht van Setspn](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10))voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-202">For more information, see [Setspn Overview](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).</span></span>

<span data-ttu-id="7c1c0-203">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-203">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-204">-MaxConnectionRetryCount</span><span class="sxs-lookup"><span data-stu-id="7c1c0-204">-MaxConnectionRetryCount</span></span>

<span data-ttu-id="7c1c0-205">Hiermee geeft u het aantal keren op dat Power shell probeert verbinding te maken met een doel computer als de huidige poging mislukt vanwege netwerk problemen.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-205">Specifies the number of times that PowerShell attempts to make a connection to a target machine if the current attempt fails due to network issues.</span></span> <span data-ttu-id="7c1c0-206">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-206">The default value is 5.</span></span>

<span data-ttu-id="7c1c0-207">Deze para meter is toegevoegd voor Power shell-versie 5,0.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-207">This parameter was added for PowerShell version 5.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-208">-MaximumReceivedDataSizePerCommand</span><span class="sxs-lookup"><span data-stu-id="7c1c0-208">-MaximumReceivedDataSizePerCommand</span></span>

<span data-ttu-id="7c1c0-209">Hiermee geeft u het maximum aantal bytes op dat de lokale computer kan ontvangen van de externe computer in één opdracht.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-209">Specifies the maximum number of bytes that the local computer can receive from the remote computer in a single command.</span></span> <span data-ttu-id="7c1c0-210">Voer een waarde in bytes in.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-210">Enter a value in bytes.</span></span> <span data-ttu-id="7c1c0-211">Standaard is er geen limiet voor de gegevens grootte.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-211">By default, there is no data size limit.</span></span>

<span data-ttu-id="7c1c0-212">Deze optie is ontworpen om de resources op de client computer te beveiligen.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-212">This option is designed to protect the resources on the client computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-213">-MaximumReceivedObjectSize</span><span class="sxs-lookup"><span data-stu-id="7c1c0-213">-MaximumReceivedObjectSize</span></span>

<span data-ttu-id="7c1c0-214">Hiermee geeft u de maximale grootte van een object op dat de lokale computer kan ontvangen van de externe computer.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-214">Specifies the maximum size of an object that the local computer can receive from the remote computer.</span></span> <span data-ttu-id="7c1c0-215">Deze optie is ontworpen om de resources op de client computer te beveiligen.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-215">This option is designed to protect the resources on the client computer.</span></span> <span data-ttu-id="7c1c0-216">Voer een waarde in bytes in.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-216">Enter a value in bytes.</span></span>

<span data-ttu-id="7c1c0-217">Als u deze para meter weglaat in Windows Power Shell 2,0, geldt er geen limiet voor de object grootte.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-217">In Windows PowerShell 2.0, if you omit this parameter, there is no object size limit.</span></span> <span data-ttu-id="7c1c0-218">Als u deze para meter weglaat in Windows Power Shell 3,0, is de standaard waarde 200 MB.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-218">Beginning in Windows PowerShell 3.0, if you omit this parameter, the default value is 200 MB.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 200 MB
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-219">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="7c1c0-219">-MaximumRedirection</span></span>

<span data-ttu-id="7c1c0-220">Bepaalt hoe vaak Power shell een verbinding met een alternatieve URI (Uniform Resource Identifier) omleidt voordat de verbinding is mislukt.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-220">Determines how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="7c1c0-221">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-221">The default value is 5.</span></span> <span data-ttu-id="7c1c0-222">Een waarde van 0 (nul) voor komt dat alle omleidingen.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-222">A value of 0 (zero) prevents all redirection.</span></span>

<span data-ttu-id="7c1c0-223">Deze optie wordt alleen in de sessie gebruikt wanneer de para meter **AllowRedirection** wordt gebruikt in de opdracht voor het maken van de sessie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-223">This option is used in the session only when the **AllowRedirection** parameter is used in the command that creates the session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-224">-Geen compressie</span><span class="sxs-lookup"><span data-stu-id="7c1c0-224">-NoCompression</span></span>

<span data-ttu-id="7c1c0-225">Hiermee schakelt u pakket compressie uit in de sessie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-225">Turns off packet compression in the session.</span></span> <span data-ttu-id="7c1c0-226">Compressie maakt gebruik van meer processor cycli, maar maakt sneller verzen ding.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-226">Compression uses more processor cycles, but it makes transmission faster.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-227">-Geen versleuteling</span><span class="sxs-lookup"><span data-stu-id="7c1c0-227">-NoEncryption</span></span>

<span data-ttu-id="7c1c0-228">Hiermee schakelt u gegevens versleuteling uit.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-228">Turns off data encryption.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-229">-NoMachineProfile</span><span class="sxs-lookup"><span data-stu-id="7c1c0-229">-NoMachineProfile</span></span>

<span data-ttu-id="7c1c0-230">Hiermee wordt voor komen dat het Windows-gebruikers profiel van de gebruiker wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-230">Prevents loading the user's Windows user profile.</span></span> <span data-ttu-id="7c1c0-231">Als gevolg hiervan kan de sessie sneller worden gemaakt, maar gebruikersspecifieke register instellingen, items als omgevings variabelen en certificaten zijn niet beschikbaar in de sessie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-231">As a result, the session might be created faster, but user-specific registry settings, items such as environment variables, and certificates are not available in the session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-232">-Opentime-out</span><span class="sxs-lookup"><span data-stu-id="7c1c0-232">-OpenTimeout</span></span>

<span data-ttu-id="7c1c0-233">Hiermee wordt bepaald hoe lang de client computer wacht totdat de sessie verbinding tot stand is gebracht.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-233">Determines how long the client computer waits for the session connection to be established.</span></span> <span data-ttu-id="7c1c0-234">Wanneer het interval is verlopen, mislukt de opdracht om de verbinding tot stand te brengen.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-234">When the interval expires, the command to establish the connection fails.</span></span> <span data-ttu-id="7c1c0-235">Voer een waarde in milliseconden in.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-235">Enter a value in milliseconds.</span></span>

<span data-ttu-id="7c1c0-236">De standaard waarde is 180000 (3 minuten).</span><span class="sxs-lookup"><span data-stu-id="7c1c0-236">The default value is 180000 (3 minutes).</span></span> <span data-ttu-id="7c1c0-237">Een waarde van 0 (nul) betekent geen time-out; de opdracht wordt voor onbepaalde tijd voortgezet.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-237">A value of 0 (zero) means no time-out; the command continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OpenTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-238">-OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="7c1c0-238">-OperationTimeout</span></span>

<span data-ttu-id="7c1c0-239">Hiermee wordt de maximale tijd bepaald dat elke bewerking in de sessie kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-239">Determines the maximum time that any operation in the session can run.</span></span> <span data-ttu-id="7c1c0-240">Wanneer het interval is verlopen, mislukt de bewerking.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-240">When the interval expires, the operation fails.</span></span> <span data-ttu-id="7c1c0-241">Voer een waarde in milliseconden in.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-241">Enter a value in milliseconds.</span></span>

<span data-ttu-id="7c1c0-242">De standaard waarde is 180000 (3 minuten).</span><span class="sxs-lookup"><span data-stu-id="7c1c0-242">The default value is 180000 (3 minutes).</span></span> <span data-ttu-id="7c1c0-243">Een waarde van 0 (nul) betekent geen time-out; de bewerking wordt voor onbepaalde tijd voortgezet.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-243">A value of 0 (zero) means no time-out; the operation continues indefinitely.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-244">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="7c1c0-244">-OutputBufferingMode</span></span>

<span data-ttu-id="7c1c0-245">Hiermee wordt bepaald hoe de uitvoer van de opdracht wordt beheerd in verbroken sessies wanneer de uitvoer buffer vol raakt.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-245">Determines how command output is managed in disconnected sessions when the output buffer becomes full.</span></span>

<span data-ttu-id="7c1c0-246">Als de uitvoer buffer modus niet is ingesteld in de sessie of in de sessie configuratie, is de standaard waarde **blok keren**.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-246">If the output buffering mode is not set in the session or in the session configuration, the default value is **Block**.</span></span> <span data-ttu-id="7c1c0-247">Gebruikers kunnen ook de uitvoer buffer modus wijzigen wanneer de verbinding met de sessie wordt verbroken.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-247">Users can also change the output buffering mode when disconnecting the session.</span></span>

<span data-ttu-id="7c1c0-248">Als u deze para meter weglaat, is de waarde van de **OutputBufferingMode** van het object Session Option geen.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-248">If you omit this parameter, the value of the **OutputBufferingMode** of the session option object is None.</span></span> <span data-ttu-id="7c1c0-249">De waarde **blok keren** of **verwijderen** overschrijft de transport optie uitvoer buffer modus die in de sessie configuratie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-249">A value of **Block** or **Drop** overrides the output buffering mode transport option set in the session configuration.</span></span> <span data-ttu-id="7c1c0-250">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="7c1c0-250">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7c1c0-251">Blok keren.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-251">Block.</span></span> <span data-ttu-id="7c1c0-252">Wanneer de uitvoer buffer vol is, wordt de uitvoering onderbroken totdat de buffer leeg is.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-252">When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="7c1c0-253">Directe.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-253">Drop.</span></span> <span data-ttu-id="7c1c0-254">Wanneer de uitvoer buffer vol is, wordt de uitvoering voortgezet.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-254">When the output buffer is full, execution continues.</span></span> <span data-ttu-id="7c1c0-255">Wanneer er een nieuwe uitvoer wordt opgeslagen, wordt de oudste uitvoer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-255">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="7c1c0-256">Geen.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-256">None.</span></span> <span data-ttu-id="7c1c0-257">Er is geen uitvoer buffer modus opgegeven.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-257">No output buffering mode is specified.</span></span>

<span data-ttu-id="7c1c0-258">Zie voor meer informatie over de transport optie uitvoer buffer modus `New-PSTransportOption` .</span><span class="sxs-lookup"><span data-stu-id="7c1c0-258">For more information about the output buffering mode transport option, see `New-PSTransportOption`.</span></span>

<span data-ttu-id="7c1c0-259">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-259">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-260">-ProxyAccessType</span><span class="sxs-lookup"><span data-stu-id="7c1c0-260">-ProxyAccessType</span></span>

<span data-ttu-id="7c1c0-261">Hiermee wordt bepaald welk mechanisme wordt gebruikt voor het omzetten van de hostnaam.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-261">Determines which mechanism is used to resolve the host name.</span></span> <span data-ttu-id="7c1c0-262">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="7c1c0-262">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7c1c0-263">IEConfig</span><span class="sxs-lookup"><span data-stu-id="7c1c0-263">IEConfig</span></span>
- <span data-ttu-id="7c1c0-264">WinHttpConfig</span><span class="sxs-lookup"><span data-stu-id="7c1c0-264">WinHttpConfig</span></span>
- <span data-ttu-id="7c1c0-265">Auto detectie</span><span class="sxs-lookup"><span data-stu-id="7c1c0-265">AutoDetect</span></span>
- <span data-ttu-id="7c1c0-266">NoProxyServer</span><span class="sxs-lookup"><span data-stu-id="7c1c0-266">NoProxyServer</span></span>
- <span data-ttu-id="7c1c0-267">Geen</span><span class="sxs-lookup"><span data-stu-id="7c1c0-267">None</span></span>

<span data-ttu-id="7c1c0-268">De standaard waarde is geen.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-268">The default value is None.</span></span>

<span data-ttu-id="7c1c0-269">Zie [ProxyAccessType Enumeration (Engelstalig)](/dotnet/api/system.management.automation.remoting.proxyaccesstype?redirectedfrom=MSDN&view=powershellsdk-1.1.0)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-269">For information about the values of this parameter, see [ProxyAccessType Enumeration](/dotnet/api/system.management.automation.remoting.proxyaccesstype?redirectedfrom=MSDN&view=powershellsdk-1.1.0).</span></span>

```yaml
Type: System.Management.Automation.Remoting.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: None, IEConfig, WinHttpConfig, AutoDetect, NoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-270">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="7c1c0-270">-ProxyAuthentication</span></span>

<span data-ttu-id="7c1c0-271">Hiermee geeft u de verificatie methode op die wordt gebruikt voor het omzetten van de proxy.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-271">Specifies the authentication method that is used for proxy resolution.</span></span> <span data-ttu-id="7c1c0-272">De acceptabele waarden voor deze para meter zijn: **Basic** , **Digest** en **Negotiate**.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-272">The acceptable values for this parameter are: **Basic** , **Digest** , and **Negotiate**.</span></span> <span data-ttu-id="7c1c0-273">De standaard waarde is **Negotiate**.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-273">The default value is **Negotiate**.</span></span>

<span data-ttu-id="7c1c0-274">Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?redirectedfrom=MSDN&view=powershellsdk-1.1.0)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-274">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?redirectedfrom=MSDN&view=powershellsdk-1.1.0).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Negotiate
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-275">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="7c1c0-275">-ProxyCredential</span></span>

<span data-ttu-id="7c1c0-276">Hiermee geeft u de referenties op die moeten worden gebruikt voor proxy verificatie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-276">Specifies the credentials to use for proxy authentication.</span></span> <span data-ttu-id="7c1c0-277">Voer een variabele in die een **PSCredential** -object bevat of een opdracht waarmee een **PSCredential** -object wordt opgehaald, zoals een `Get-Credential` opdracht.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-277">Enter a variable that contains a **PSCredential** object or a command that gets a **PSCredential** object, such as a `Get-Credential` command.</span></span> <span data-ttu-id="7c1c0-278">Als deze optie niet is ingesteld, worden er geen referenties opgegeven.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-278">If this option is not set, no credentials are specified.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-279">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="7c1c0-279">-SkipCACheck</span></span>

<span data-ttu-id="7c1c0-280">Hiermee geeft u op dat wanneer verbinding wordt gemaakt via HTTPS, de client niet controleert of het server certificaat is ondertekend door een vertrouwde certificerings instantie (CA).</span><span class="sxs-lookup"><span data-stu-id="7c1c0-280">Specifies that when it connects over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>

<span data-ttu-id="7c1c0-281">Gebruik deze optie alleen als de externe computer wordt vertrouwd door een ander mechanisme te gebruiken, bijvoorbeeld wanneer de externe computer deel uitmaakt van een netwerk dat fysiek is beveiligd en geïsoleerd of wanneer de externe computer wordt vermeld als een vertrouwde host in een WinRM-configuratie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-281">Use this option only when the remote computer is trusted by using another mechanism, such as when the remote computer is part of a network that is physically secure and isolated or when the remote computer is listed as a trusted host in a WinRM configuration.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-282">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="7c1c0-282">-SkipCNCheck</span></span>

<span data-ttu-id="7c1c0-283">Hiermee geeft u op dat de algemene naam (CN) van het certificaat van de server niet overeenkomt met de hostnaam van de server.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-283">Specifies that the certificate common name (CN) of the server does not have to match the host name of the server.</span></span> <span data-ttu-id="7c1c0-284">Deze optie wordt alleen gebruikt in externe bewerkingen die gebruikmaken van het HTTPS-protocol.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-284">This option is used only in remote operations that use the HTTPS protocol.</span></span>

<span data-ttu-id="7c1c0-285">Gebruik deze optie alleen voor vertrouwde computers.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-285">Use this option only for trusted computers.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-286">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="7c1c0-286">-SkipRevocationCheck</span></span>

<span data-ttu-id="7c1c0-287">Valideert niet de intrekkings status van het server certificaat.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-287">Does not validate the revocation status of the server certificate.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-288">-UICulture</span><span class="sxs-lookup"><span data-stu-id="7c1c0-288">-UICulture</span></span>

<span data-ttu-id="7c1c0-289">Hiermee geeft u de UI-cultuur op die voor de sessie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-289">Specifies the UI culture to use for the session.</span></span>

<span data-ttu-id="7c1c0-290">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="7c1c0-290">Valid values include:</span></span>

- <span data-ttu-id="7c1c0-291">Een cultuur naam in `<languagecode2>-<country/regioncode2>` indeling, zoals `ja-JP`</span><span class="sxs-lookup"><span data-stu-id="7c1c0-291">A culture name in `<languagecode2>-<country/regioncode2>` format, such as `ja-JP`</span></span>
- <span data-ttu-id="7c1c0-292">Een variabele die een **Culture info** -object bevat</span><span class="sxs-lookup"><span data-stu-id="7c1c0-292">A variable that contains a **CultureInfo** object</span></span>
- <span data-ttu-id="7c1c0-293">Een opdracht waarmee een **Culture info** -object wordt opgehaald, zoals `Get-Culture`</span><span class="sxs-lookup"><span data-stu-id="7c1c0-293">A command that gets a **CultureInfo** object, such as `Get-Culture`</span></span>

<span data-ttu-id="7c1c0-294">De standaard waarde is `$null` en de UI-cultuur die in het besturings systeem is ingesteld tijdens het maken van de sessie, wordt in de sessie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-294">The default value is `$null`, and the UI culture that is set in the operating system when the session is created is used in the session.</span></span>

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-295">-UseUTF16</span><span class="sxs-lookup"><span data-stu-id="7c1c0-295">-UseUTF16</span></span>

<span data-ttu-id="7c1c0-296">Geeft aan dat deze cmdlet de aanvraag in een UTF16-indeling codeert in plaats van UTF8-indeling.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-296">Indicates that this cmdlet encodes the request in UTF16 format instead of UTF8 format.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7c1c0-297">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7c1c0-297">CommonParameters</span></span>

<span data-ttu-id="7c1c0-298">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-298">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7c1c0-299">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-299">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7c1c0-300">INVOER</span><span class="sxs-lookup"><span data-stu-id="7c1c0-300">INPUTS</span></span>

### <span data-ttu-id="7c1c0-301">Geen</span><span class="sxs-lookup"><span data-stu-id="7c1c0-301">None</span></span>

<span data-ttu-id="7c1c0-302">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-302">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="7c1c0-303">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7c1c0-303">OUTPUTS</span></span>

### <span data-ttu-id="7c1c0-304">System. Management. Automation. Remoting. PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="7c1c0-304">System.Management.Automation.Remoting.PSSessionOption</span></span>

## <span data-ttu-id="7c1c0-305">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7c1c0-305">NOTES</span></span>

<span data-ttu-id="7c1c0-306">Als de para meter **SessionOption** niet wordt gebruikt in een opdracht voor het maken van een **PSSession** , worden de sessie opties bepaald door de eigenschaps waarden van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-306">If the **SessionOption** parameter is not used in a command to create a **PSSession** , the session options are determined by the property values of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="7c1c0-307">Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` variabele [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="7c1c0-307">For more information about the `$PSSessionOption` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="7c1c0-308">De eigenschappen van een sessie configuratie object zijn afhankelijk van de opties die zijn ingesteld voor de sessie configuratie en de waarden van deze opties.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-308">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="7c1c0-309">Daarnaast hebben sessie configuraties die gebruikmaken van een sessie configuratie bestand extra eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="7c1c0-309">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="7c1c0-310">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7c1c0-310">RELATED LINKS</span></span>

[<span data-ttu-id="7c1c0-311">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="7c1c0-311">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="7c1c0-312">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="7c1c0-312">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="7c1c0-313">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="7c1c0-313">New-PSSession</span></span>](New-PSSession.md)

