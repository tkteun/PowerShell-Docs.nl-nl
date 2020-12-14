---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pstransportoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSTransportOption
ms.openlocfilehash: fa19ee7d1856eee91a6b1d6a8352017457031202
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705620"
---
# <span data-ttu-id="f98ed-102">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="f98ed-102">New-PSTransportOption</span></span>

## <span data-ttu-id="f98ed-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f98ed-103">SYNOPSIS</span></span>
<span data-ttu-id="f98ed-104">Hiermee maakt u een object dat geavanceerde opties bevat voor een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="f98ed-104">Creates an object that contains advanced options for a session configuration.</span></span>

## <span data-ttu-id="f98ed-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f98ed-105">SYNTAX</span></span>

```
New-PSTransportOption [-MaxIdleTimeoutSec <Int32>] [-ProcessIdleTimeoutSec <Int32>] [-MaxSessions <Int32>]
 [-MaxConcurrentCommandsPerSession <Int32>] [-MaxSessionsPerUser <Int32>] [-MaxMemoryPerSessionMB <Int32>]
 [-MaxProcessesPerSession <Int32>] [-MaxConcurrentUsers <Int32>] [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [<CommonParameters>]
```

## <span data-ttu-id="f98ed-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f98ed-106">DESCRIPTION</span></span>

<span data-ttu-id="f98ed-107">Met de cmdlet **New-PSTransportOption** maakt u een object dat transport opties bevat voor sessie configuraties.</span><span class="sxs-lookup"><span data-stu-id="f98ed-107">The **New-PSTransportOption** cmdlet creates an object that contains transport options for session configurations.</span></span>
<span data-ttu-id="f98ed-108">U kunt het object gebruiken als de waarde van de *TransportOption* -para meter van cmdlets waarmee een sessie configuratie wordt gemaakt of gewijzigd, zoals de Register-PSSessionConfiguration en Set-PSSessionConfiguration-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="f98ed-108">You can use the object as the value of the *TransportOption* parameter of cmdlets that create or change a session configuration, such as the Register-PSSessionConfiguration and Set-PSSessionConfiguration cmdlets.</span></span>

<span data-ttu-id="f98ed-109">U kunt ook de instellingen voor transport opties wijzigen door de waarden van de eigenschappen van de sessie configuratie te bewerken in het WSMan:-station.</span><span class="sxs-lookup"><span data-stu-id="f98ed-109">You can also change the transport option settings by editing the values of the session configuration properties in the WSMan: drive.</span></span>
<span data-ttu-id="f98ed-110">Zie WSMan-provider voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f98ed-110">For more information, see WSMan Provider.</span></span>

<span data-ttu-id="f98ed-111">De opties voor sessie configuratie vertegenwoordigen de sessie waarden die zijn ingesteld aan de server zijde of het ontvangende einde van een externe verbinding.</span><span class="sxs-lookup"><span data-stu-id="f98ed-111">The session configuration options represent the session values set on the server-side, or receiving end of a remote connection.</span></span>
<span data-ttu-id="f98ed-112">Aan de client zijde of het verzenden van het einde van de verbinding, kan de sessie optie waarden instellen wanneer de sessie wordt gemaakt, of wanneer de client de verbinding met de sessie verbreekt of de verbinding opnieuw tot stand brengt.</span><span class="sxs-lookup"><span data-stu-id="f98ed-112">The client-side, or sending end of the connection, can set session option values when the session is created, or when the client disconnects from or reconnects to the session.</span></span>
<span data-ttu-id="f98ed-113">Tenzij anders vermeld, worden de waarden van de client voor rang gegeven wanneer de instellings waarden conflicteren.</span><span class="sxs-lookup"><span data-stu-id="f98ed-113">Unless stated otherwise, when the setting values conflict, the client-side values take precedence.</span></span>
<span data-ttu-id="f98ed-114">De waarden aan de client zijde kunnen echter niet in strijd zijn met de maximum waarden en quota's die in de sessie configuratie zijn ingesteld.</span><span class="sxs-lookup"><span data-stu-id="f98ed-114">However, the client-side values cannot violate maximum values and quotas set in the session configuration.</span></span>

<span data-ttu-id="f98ed-115">Zonder para meters, **New-PSTransportOption** genereert een transport optie object dat Null-waarden heeft voor alle opties.</span><span class="sxs-lookup"><span data-stu-id="f98ed-115">Without parameters, **New-PSTransportOption** generates a transport option object that has null values for all of the options.</span></span>
<span data-ttu-id="f98ed-116">Als u een para meter weglaat, heeft het object een null-waarde voor de eigenschap die door de para meter wordt vertegenwoordigd.</span><span class="sxs-lookup"><span data-stu-id="f98ed-116">If you omit a parameter, the object has a null value for the property that the parameter represents.</span></span>
<span data-ttu-id="f98ed-117">Een null-waarde heeft geen invloed op de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="f98ed-117">A null value does not affect the session configuration.</span></span>

<span data-ttu-id="f98ed-118">Zie New-PSSessionOption voor meer informatie over sessie opties.</span><span class="sxs-lookup"><span data-stu-id="f98ed-118">For more information about session options, see New-PSSessionOption.</span></span>
<span data-ttu-id="f98ed-119">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="f98ed-119">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="f98ed-120">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f98ed-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="f98ed-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f98ed-121">EXAMPLES</span></span>

### <span data-ttu-id="f98ed-122">Voor beeld 1: een standaard transport optie genereren</span><span class="sxs-lookup"><span data-stu-id="f98ed-122">Example 1: Generate a default transport option</span></span>

```powershell
New-PSTransportOption
```

```Output
ProcessIdleTimeoutSec           :
MaxIdleTimeoutSec               :
MaxSessions                     :
MaxConcurrentCommandsPerSession :
MaxSessionsPerUser              :
MaxMemoryPerSessionMB           :
MaxProcessesPerSession          :
MaxConcurrentUsers              :
IdleTimeoutSec                  :
OutputBufferingMode             :
```

<span data-ttu-id="f98ed-123">Met deze opdracht wordt de **New-PSTransportOption** zonder para meters uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f98ed-123">This command runs the **New-PSTransportOption** without parameters.</span></span>
<span data-ttu-id="f98ed-124">De uitvoer laat zien dat de cmdlet een transport optie object genereert dat Null-waarden voor alle eigenschappen heeft.</span><span class="sxs-lookup"><span data-stu-id="f98ed-124">The output shows that the cmdlet generates a transport option object that has null values for all properties.</span></span>

### <span data-ttu-id="f98ed-125">Voor beeld 2: opties voor sessie configuratie ophalen</span><span class="sxs-lookup"><span data-stu-id="f98ed-125">Example 2: Get session configuration options</span></span>

<span data-ttu-id="f98ed-126">In dit voor beeld ziet u hoe u een object transport opties gebruikt om opties voor sessie configuratie in te stellen.</span><span class="sxs-lookup"><span data-stu-id="f98ed-126">This example shows how to use a transport options object to set session configuration options.</span></span>

```powershell
$t = New-PSTransportOption -MaxSessions 40
Register-PSSessionConfiguration -Name ITTasks -TransportOption $t
Get-PSSessionConfiguration -Name ITTasks | Format-List -Property *
```

```Output
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITTasks
MaxConcurrentCommandsPerShell : 1000
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 40
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 2
Name                          : ITTasks
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
Enabled                       : True
MaxShellsPerUser              : 25
Permission                    :
```

<span data-ttu-id="f98ed-127">De eerste opdracht maakt gebruik van de cmdlet **New-PSTransportOption** voor het maken van een transport opties-object, dat wordt opgeslagen in de variabele $t.</span><span class="sxs-lookup"><span data-stu-id="f98ed-127">The first command uses the **New-PSTransportOption** cmdlet to create a transport options object, which it saves in the $t variable.</span></span> <span data-ttu-id="f98ed-128">De opdracht gebruikt de para meter *maxsessions* om het maximum aantal sessies tot 40 te verhogen.</span><span class="sxs-lookup"><span data-stu-id="f98ed-128">The command uses the *MaxSessions* parameter to increase the maximum number of sessions to 40.</span></span>

<span data-ttu-id="f98ed-129">De tweede opdracht maakt gebruik **van de cmdlet REGI ster-PSSessionConfiguration** om de configuratie van de ITTasks-sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="f98ed-129">The second command uses the **Register-PSSessionConfiguration** cmdlet create the ITTasks session configuration.</span></span> <span data-ttu-id="f98ed-130">De opdracht gebruikt de para meter *TransportOption* om het object transport opties in de variabele $t op te geven.</span><span class="sxs-lookup"><span data-stu-id="f98ed-130">The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.</span></span>

<span data-ttu-id="f98ed-131">De derde opdracht maakt gebruik van de cmdlet Get-PSSessionConfiguration om de ITTasks-sessie configuraties en de Format-List-cmdlet te verkrijgen om alle eigenschappen van het sessie configuratie object in een lijst weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f98ed-131">The third command uses the Get-PSSessionConfiguration cmdlet to get the ITTasks session configurations and the Format-List cmdlet to display all of the properties of the session configuration object in a list.</span></span> <span data-ttu-id="f98ed-132">In de uitvoer ziet u dat de waarde van de eigenschap **MaxShells** van de sessie configuratie 40 is.</span><span class="sxs-lookup"><span data-stu-id="f98ed-132">The output shows that the value of the **MaxShells** property of the session configuration is 40.</span></span>

### <span data-ttu-id="f98ed-133">Voor beeld 3: een transport optie instellen</span><span class="sxs-lookup"><span data-stu-id="f98ed-133">Example 3: Setting a transport option</span></span>

<span data-ttu-id="f98ed-134">Met deze opdracht wordt het effect weer gegeven van het instellen van een transport optie in een sessie configuratie op de sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="f98ed-134">This command shows the effect of setting a transport option in a session configuration on the sessions that use the session configuration.</span></span>

```powershell
$t = New-PSTransportOption -IdleTimeoutSec 3600
Set-PSSessionConfiguration -Name ITTasks -TransportOption $t
$s = New-PSSession -Name MyITTasks -ConfigurationName ITTasks
$s | Format-List -Property *
```

```Output
State                  : Opened
IdleTimeout            : 3600000
OutputBufferingMode    : Block
ComputerName           : localhost
ConfigurationName      : ITTasks
InstanceId             : 4110c3f5-68ea-40fa-9bbf-04a433dbb02d
Id                     : 1
Name                   : MyITTasks
Availability           : Available
ApplicationPrivateData : {PSVersionTable}
Runspace               : System.Management.Automation.RemoteRunspace
```

<span data-ttu-id="f98ed-135">De eerste opdracht maakt gebruik van de cmdlet **New-PSTransportOption** om een transport optie object te maken.</span><span class="sxs-lookup"><span data-stu-id="f98ed-135">The first command uses the **New-PSTransportOption** cmdlet to create a transport option object.</span></span> <span data-ttu-id="f98ed-136">De opdracht gebruikt de para meter *IdleTimeoutSec* om de waarde van de eigenschap **IdleTimeoutSec** van het object in te stellen op één uur (3600 seconden).</span><span class="sxs-lookup"><span data-stu-id="f98ed-136">The command uses the *IdleTimeoutSec* parameter to set the **IdleTimeoutSec** property value of the object to one hour (3600 seconds).</span></span> <span data-ttu-id="f98ed-137">Met de opdracht wordt het object Trans Port-objecten opgeslagen in de variabele $t.</span><span class="sxs-lookup"><span data-stu-id="f98ed-137">The command saves the transport objects object in the $t variable.</span></span>

<span data-ttu-id="f98ed-138">De tweede opdracht gebruikt de cmdlet Set-PSSessionConfiguration om de transport opties van de ITTasks-sessie configuratie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="f98ed-138">The second command uses the Set-PSSessionConfiguration cmdlet to change the transport options of the ITTasks session configuration.</span></span> <span data-ttu-id="f98ed-139">De opdracht gebruikt de para meter *TransportOption* om het object transport opties in de variabele $t op te geven.</span><span class="sxs-lookup"><span data-stu-id="f98ed-139">The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.</span></span>

<span data-ttu-id="f98ed-140">De derde opdracht maakt gebruik van de cmdlet New-PSSession om de MyITTasks-sessie te maken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f98ed-140">The third command uses the New-PSSession cmdlet to create the MyITTasks session on the local computer.</span></span> <span data-ttu-id="f98ed-141">De opdracht gebruikt de eigenschap **configuratiepad** om de ITTasks-sessie configuratie op te geven.</span><span class="sxs-lookup"><span data-stu-id="f98ed-141">The command uses the **ConfigurationName** property to specify the ITTasks session configuration.</span></span> <span data-ttu-id="f98ed-142">Met de opdracht wordt de sessie opgeslagen in de variabele $s. U ziet dat met de opdracht de para meter *SessionOption* van **New-PSSession** niet wordt gebruikt om een aangepaste time-out voor inactiviteit voor de sessie in te stellen.</span><span class="sxs-lookup"><span data-stu-id="f98ed-142">The command saves the session in the $s variable.Notice that the command does not use the *SessionOption* parameter of **New-PSSession** to set a custom idle time-out for the session.</span></span> <span data-ttu-id="f98ed-143">Als dat het geval is, heeft de time-outwaarde voor inactiviteit in de sessie optie voor rang op de time-out voor inactiviteit die in de sessie configuratie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="f98ed-143">If it did, the idle time-out value set in the session option would take precedence over the idle time-out set in the session configuration.</span></span>

<span data-ttu-id="f98ed-144">De vierde opdracht maakt gebruik van de cmdlet Format-List om alle eigenschappen van de sessie weer te geven in de $s variabele in een lijst.</span><span class="sxs-lookup"><span data-stu-id="f98ed-144">The fourth command uses the Format-List cmdlet to display all properties of the session in the $s variable in a list.</span></span> <span data-ttu-id="f98ed-145">In de uitvoer ziet u dat de sessie een time-out voor inactiviteit van één uur (360.000 milliseconden) heeft.</span><span class="sxs-lookup"><span data-stu-id="f98ed-145">The output shows that the session has an idle time-out of one hour (360,000 milliseconds).</span></span>

## <span data-ttu-id="f98ed-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f98ed-146">PARAMETERS</span></span>

### <span data-ttu-id="f98ed-147">-IdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="f98ed-147">-IdleTimeoutSec</span></span>

<span data-ttu-id="f98ed-148">Hiermee wordt bepaald hoe lang elke sessie open blijft als de externe computer geen communicatie van de lokale computer ontvangt.</span><span class="sxs-lookup"><span data-stu-id="f98ed-148">Determines how long each session stays open if the remote computer does not receive any communication from the local computer.</span></span>
<span data-ttu-id="f98ed-149">Dit omvat het heartbeat-signaal.</span><span class="sxs-lookup"><span data-stu-id="f98ed-149">This includes the heartbeat signal.</span></span>
<span data-ttu-id="f98ed-150">Wanneer het interval is verlopen, wordt de sessie gesloten.</span><span class="sxs-lookup"><span data-stu-id="f98ed-150">When the interval expires, the session closes.</span></span>

<span data-ttu-id="f98ed-151">De time-outwaarde voor inactiviteit is van groot belang wanneer de gebruiker de verbinding verbreekt en opnieuw verbinding maakt met een sessie.</span><span class="sxs-lookup"><span data-stu-id="f98ed-151">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="f98ed-152">De gebruiker kan opnieuw verbinding maken als er geen time-out is opgetreden voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="f98ed-152">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="f98ed-153">De para meter *IdleTimeoutSec* komt overeen met de eigenschap **IdleTimeoutMs** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="f98ed-153">The *IdleTimeoutSec* parameter corresponds to the **IdleTimeoutMs** property of a session configuration.</span></span>

<span data-ttu-id="f98ed-154">Voer een waarde in seconden in.</span><span class="sxs-lookup"><span data-stu-id="f98ed-154">Enter a value in seconds.</span></span>
<span data-ttu-id="f98ed-155">De standaard waarde is 7200 (2 uur).</span><span class="sxs-lookup"><span data-stu-id="f98ed-155">The default value is 7200 (2 hours).</span></span>
<span data-ttu-id="f98ed-156">De minimum waarde is 60 (1 minuut).</span><span class="sxs-lookup"><span data-stu-id="f98ed-156">The minimum value is 60 (1 minute).</span></span>
<span data-ttu-id="f98ed-157">Het maximum is de waarde van de eigenschap **IdleTimeout** van shell-objecten in de WSMan-configuratie ( `WSMan:\\\<ComputerName\>\Shell\IdleTimeout` ).</span><span class="sxs-lookup"><span data-stu-id="f98ed-157">The maximum is the value of the **IdleTimeout** property of Shell objects in the WSMan configuration (`WSMan:\\\<ComputerName\>\Shell\IdleTimeout`).</span></span>
<span data-ttu-id="f98ed-158">De standaard waarde is 7200000 milliseconden (2 uur).</span><span class="sxs-lookup"><span data-stu-id="f98ed-158">The default value is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="f98ed-159">Als er een time-outwaarde voor inactiviteit is ingesteld in de sessie opties en in de sessie configuratie, krijgt de waarde die in de sessie opties is ingesteld prioriteit, maar kan de waarde van de eigenschap **MaxIdleTimeoutMs** van de sessie configuratie niet groter worden.</span><span class="sxs-lookup"><span data-stu-id="f98ed-159">If an idle time-out value is set in the session options and in the session configuration, value set in the session options takes precedence, but it cannot exceed the value of the **MaxIdleTimeoutMs** property of the session configuration.</span></span>
<span data-ttu-id="f98ed-160">Als u de waarde van de eigenschap **MaxIdleTimeoutMs** wilt instellen, gebruikt u de para meter *MaxIdleTimeoutSec* .</span><span class="sxs-lookup"><span data-stu-id="f98ed-160">To set the value of the **MaxIdleTimeoutMs** property, use the *MaxIdleTimeoutSec* parameter.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f98ed-161">-MaxConcurrentCommandsPerSession</span><span class="sxs-lookup"><span data-stu-id="f98ed-161">-MaxConcurrentCommandsPerSession</span></span>

<span data-ttu-id="f98ed-162">Beperkt het aantal opdrachten dat tegelijkertijd in elke sessie kan worden uitgevoerd naar de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="f98ed-162">Limits the number of commands that can run at the same time in each session to the specified value.</span></span>
<span data-ttu-id="f98ed-163">De standaardwaarde is 1000.</span><span class="sxs-lookup"><span data-stu-id="f98ed-163">The default value is 1000.</span></span>

<span data-ttu-id="f98ed-164">De para meter *MaxConcurrentCommandsPerSession* komt overeen met de eigenschap **MaxConcurrentCommandsPerShell** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="f98ed-164">The *MaxConcurrentCommandsPerSession* parameter corresponds to the **MaxConcurrentCommandsPerShell** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f98ed-165">-MaxConcurrentUsers</span><span class="sxs-lookup"><span data-stu-id="f98ed-165">-MaxConcurrentUsers</span></span>

<span data-ttu-id="f98ed-166">Beperkt het aantal gebruikers dat op hetzelfde moment in elke sessie opdrachten kan uitvoeren op de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="f98ed-166">Limits the number of users who can run commands at the same time in each session to the specified value.</span></span>
<span data-ttu-id="f98ed-167">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="f98ed-167">The default value is 5.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f98ed-168">-MaxIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="f98ed-168">-MaxIdleTimeoutSec</span></span>

<span data-ttu-id="f98ed-169">Hiermee wordt de time-out voor inactiviteit voor elke sessie beperkt tot de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="f98ed-169">Limits the idle time-out set for each session to the specified value.</span></span>
<span data-ttu-id="f98ed-170">De standaard waarde is \[ int \] :: MaxValue (~ 25 dagen).</span><span class="sxs-lookup"><span data-stu-id="f98ed-170">The default value is \[Int\]::MaxValue (~25 days).</span></span>

<span data-ttu-id="f98ed-171">De time-outwaarde voor inactiviteit is van groot belang wanneer de gebruiker de verbinding verbreekt en opnieuw verbinding maakt met een sessie.</span><span class="sxs-lookup"><span data-stu-id="f98ed-171">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="f98ed-172">De gebruiker kan opnieuw verbinding maken als er geen time-out is opgetreden voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="f98ed-172">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="f98ed-173">De para meter *MaxIdleTimeoutSec* komt overeen met de eigenschap **MaxIdleTimeoutMs** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="f98ed-173">The *MaxIdleTimeoutSec* parameter corresponds to the **MaxIdleTimeoutMs** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f98ed-174">-MaxMemoryPerSessionMB</span><span class="sxs-lookup"><span data-stu-id="f98ed-174">-MaxMemoryPerSessionMB</span></span>

<span data-ttu-id="f98ed-175">Hiermee wordt het geheugen dat door elke sessie wordt gebruikt, beperkt tot de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="f98ed-175">Limits the memory used by each session to the specified value.</span></span>
<span data-ttu-id="f98ed-176">Voer een waarde in mega bytes in.</span><span class="sxs-lookup"><span data-stu-id="f98ed-176">Enter a value in megabytes.</span></span>
<span data-ttu-id="f98ed-177">De standaard waarde is 1024 MB (1 GB).</span><span class="sxs-lookup"><span data-stu-id="f98ed-177">The default value is 1024 megabytes (1 GB).</span></span>

<span data-ttu-id="f98ed-178">De para meter *MaxMemoryPerSessionMB* komt overeen met de eigenschap **MaxMemoryPerShellMB** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="f98ed-178">The *MaxMemoryPerSessionMB* parameter corresponds to the **MaxMemoryPerShellMB** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f98ed-179">-MaxProcessesPerSession</span><span class="sxs-lookup"><span data-stu-id="f98ed-179">-MaxProcessesPerSession</span></span>

<span data-ttu-id="f98ed-180">Beperkt het aantal processen dat in elke sessie wordt uitgevoerd op de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="f98ed-180">Limits the number of processes running in each session to the specified value.</span></span>
<span data-ttu-id="f98ed-181">De standaard waarde is 15.</span><span class="sxs-lookup"><span data-stu-id="f98ed-181">The default value is 15.</span></span>

<span data-ttu-id="f98ed-182">De para meter *MaxProcessesPerSession* komt overeen met de eigenschap **MaxProcessesPerShell** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="f98ed-182">The *MaxProcessesPerSession* parameter corresponds to the **MaxProcessesPerShell** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f98ed-183">-MaxSessions</span><span class="sxs-lookup"><span data-stu-id="f98ed-183">-MaxSessions</span></span>

<span data-ttu-id="f98ed-184">Hiermee beperkt u het aantal sessies dat de sessie configuratie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f98ed-184">Limits the number of sessions that use the session configuration.</span></span>
<span data-ttu-id="f98ed-185">De standaard waarde is 25.</span><span class="sxs-lookup"><span data-stu-id="f98ed-185">The default value is 25.</span></span>

<span data-ttu-id="f98ed-186">De para meter *maxsessions* komt overeen met de eigenschap **MaxShells** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="f98ed-186">The *MaxSessions* parameter corresponds to the **MaxShells** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f98ed-187">-MaxSessionsPerUser</span><span class="sxs-lookup"><span data-stu-id="f98ed-187">-MaxSessionsPerUser</span></span>

<span data-ttu-id="f98ed-188">Hiermee beperkt u het aantal sessies dat de sessie configuratie gebruikt en voert u uit met de referenties van een bepaalde gebruiker naar de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="f98ed-188">Limits the number of sessions that use the session configuration and run with the credentials of a given user to the specified value.</span></span>
<span data-ttu-id="f98ed-189">De standaard waarde is 25.</span><span class="sxs-lookup"><span data-stu-id="f98ed-189">The default value is 25.</span></span>

<span data-ttu-id="f98ed-190">Wanneer u deze waarde opgeeft, moet u er rekening mee houden dat veel gebruikers mogelijk gebruikmaken van de referenties van een run as-gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f98ed-190">When you specify this value, consider that many users might be using the credentials of a run as user.</span></span>

<span data-ttu-id="f98ed-191">De para meter *MaxSessionsPerUser* komt overeen met de eigenschap **MaxShellsPerUser** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="f98ed-191">The *MaxSessionsPerUser* parameter corresponds to the **MaxShellsPerUser** property of a session configuration.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f98ed-192">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="f98ed-192">-OutputBufferingMode</span></span>

<span data-ttu-id="f98ed-193">Hiermee wordt bepaald hoe de uitvoer van de opdracht wordt beheerd in verbroken sessies wanneer de uitvoer buffer vol raakt.</span><span class="sxs-lookup"><span data-stu-id="f98ed-193">Determines how command output is managed in disconnected sessions when the output buffer becomes full.</span></span>
<span data-ttu-id="f98ed-194">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="f98ed-194">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f98ed-195">Blok keren.</span><span class="sxs-lookup"><span data-stu-id="f98ed-195">Block.</span></span>
<span data-ttu-id="f98ed-196">Wanneer de uitvoer buffer vol is, wordt de uitvoering onderbroken totdat de buffer leeg is.</span><span class="sxs-lookup"><span data-stu-id="f98ed-196">When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="f98ed-197">Directe.</span><span class="sxs-lookup"><span data-stu-id="f98ed-197">Drop.</span></span>
<span data-ttu-id="f98ed-198">Wanneer de uitvoer buffer vol is, wordt de uitvoering voortgezet.</span><span class="sxs-lookup"><span data-stu-id="f98ed-198">When the output buffer is full, execution continues.</span></span>
<span data-ttu-id="f98ed-199">Wanneer er een nieuwe uitvoer wordt opgeslagen, wordt de oudste uitvoer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f98ed-199">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="f98ed-200">Geen.</span><span class="sxs-lookup"><span data-stu-id="f98ed-200">None.</span></span>
<span data-ttu-id="f98ed-201">Er is geen uitvoer buffer modus opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f98ed-201">No output buffering mode is specified.</span></span>

<span data-ttu-id="f98ed-202">De standaard waarde van de eigenschap **OutputBufferingMode** van sessies is blok keren.</span><span class="sxs-lookup"><span data-stu-id="f98ed-202">The default value of the **OutputBufferingMode** property of sessions is Block.</span></span>

```yaml
Type: System.Nullable`1[System.Management.Automation.Runspaces.OutputBufferingMode]
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f98ed-203">-ProcessIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="f98ed-203">-ProcessIdleTimeoutSec</span></span>

<span data-ttu-id="f98ed-204">Hiermee wordt de time-out voor elk hostproces beperkt tot de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="f98ed-204">Limits the time-out for each host process to the specified value.</span></span>
<span data-ttu-id="f98ed-205">De standaard waarde, 0, betekent dat er geen time-outwaarde is voor het proces.</span><span class="sxs-lookup"><span data-stu-id="f98ed-205">The default value, 0, means that there is no time-out value for the process.</span></span>

<span data-ttu-id="f98ed-206">Andere sessie configuraties hebben time-outwaarden per proces.</span><span class="sxs-lookup"><span data-stu-id="f98ed-206">Other session configurations have per-process time-out values.</span></span>
<span data-ttu-id="f98ed-207">Bijvoorbeeld: de **micro soft. Power shell. werk stroom** sessie configuratie heeft een time-outwaarde van 28800 seconden (8 uur).</span><span class="sxs-lookup"><span data-stu-id="f98ed-207">For example, the **Microsoft.PowerShell.Workflow** session configuration has a per-process time-out value of 28800 seconds (8 hours).</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f98ed-208">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f98ed-208">CommonParameters</span></span>

<span data-ttu-id="f98ed-209">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f98ed-209">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f98ed-210">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f98ed-210">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f98ed-211">INVOER</span><span class="sxs-lookup"><span data-stu-id="f98ed-211">INPUTS</span></span>

### <span data-ttu-id="f98ed-212">Geen</span><span class="sxs-lookup"><span data-stu-id="f98ed-212">None</span></span>

<span data-ttu-id="f98ed-213">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f98ed-213">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="f98ed-214">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f98ed-214">OUTPUTS</span></span>

### <span data-ttu-id="f98ed-215">Micro soft. Power shell. commands. WSManConfigurationOption</span><span class="sxs-lookup"><span data-stu-id="f98ed-215">Microsoft.PowerShell.Commands.WSManConfigurationOption</span></span>

## <span data-ttu-id="f98ed-216">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f98ed-216">NOTES</span></span>

- <span data-ttu-id="f98ed-217">De eigenschappen van een sessie configuratie object zijn afhankelijk van de opties die zijn ingesteld voor de sessie configuratie en de waarden van deze opties.</span><span class="sxs-lookup"><span data-stu-id="f98ed-217">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="f98ed-218">Daarnaast hebben sessie configuraties die gebruikmaken van een sessie configuratie bestand extra eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="f98ed-218">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="f98ed-219">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f98ed-219">RELATED LINKS</span></span>

[<span data-ttu-id="f98ed-220">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="f98ed-220">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="f98ed-221">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="f98ed-221">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="f98ed-222">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f98ed-222">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="f98ed-223">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f98ed-223">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

