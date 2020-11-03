---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pstransportoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSTransportOption
ms.openlocfilehash: 9257c0a1829cc9cc85029f7c6fdc8e61b0ed7e56
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251475"
---
# <span data-ttu-id="92948-103">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="92948-103">New-PSTransportOption</span></span>

## <span data-ttu-id="92948-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="92948-104">SYNOPSIS</span></span>

<span data-ttu-id="92948-105">Hiermee maakt u een object dat geavanceerde opties bevat voor een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="92948-105">Creates an object that contains advanced options for a session configuration.</span></span>

## <span data-ttu-id="92948-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="92948-106">SYNTAX</span></span>

```
New-PSTransportOption [-MaxIdleTimeoutSec <Int32>] [-ProcessIdleTimeoutSec <Int32>] [-MaxSessions <Int32>]
 [-MaxConcurrentCommandsPerSession <Int32>] [-MaxSessionsPerUser <Int32>] [-MaxMemoryPerSessionMB <Int32>]
 [-MaxProcessesPerSession <Int32>] [-MaxConcurrentUsers <Int32>] [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [<CommonParameters>]
```

## <span data-ttu-id="92948-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="92948-107">DESCRIPTION</span></span>

<span data-ttu-id="92948-108">Met de cmdlet **New-PSTransportOption** maakt u een object dat transport opties bevat voor sessie configuraties.</span><span class="sxs-lookup"><span data-stu-id="92948-108">The **New-PSTransportOption** cmdlet creates an object that contains transport options for session configurations.</span></span>
<span data-ttu-id="92948-109">U kunt het object gebruiken als de waarde van de *TransportOption* -para meter van cmdlets waarmee een sessie configuratie wordt gemaakt of gewijzigd, zoals de Register-PSSessionConfiguration en Set-PSSessionConfiguration-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="92948-109">You can use the object as the value of the *TransportOption* parameter of cmdlets that create or change a session configuration, such as the Register-PSSessionConfiguration and Set-PSSessionConfiguration cmdlets.</span></span>

<span data-ttu-id="92948-110">U kunt ook de instellingen voor transport opties wijzigen door de waarden van de eigenschappen van de sessie configuratie te bewerken in het WSMan:-station.</span><span class="sxs-lookup"><span data-stu-id="92948-110">You can also change the transport option settings by editing the values of the session configuration properties in the WSMan: drive.</span></span>
<span data-ttu-id="92948-111">Zie WSMan-provider voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="92948-111">For more information, see WSMan Provider.</span></span>

<span data-ttu-id="92948-112">De opties voor sessie configuratie vertegenwoordigen de sessie waarden die zijn ingesteld aan de server zijde of het ontvangende einde van een externe verbinding.</span><span class="sxs-lookup"><span data-stu-id="92948-112">The session configuration options represent the session values set on the server-side, or receiving end of a remote connection.</span></span>
<span data-ttu-id="92948-113">Aan de client zijde of het verzenden van het einde van de verbinding, kan de sessie optie waarden instellen wanneer de sessie wordt gemaakt, of wanneer de client de verbinding met de sessie verbreekt of de verbinding opnieuw tot stand brengt.</span><span class="sxs-lookup"><span data-stu-id="92948-113">The client-side, or sending end of the connection, can set session option values when the session is created, or when the client disconnects from or reconnects to the session.</span></span>
<span data-ttu-id="92948-114">Tenzij anders vermeld, worden de waarden van de client voor rang gegeven wanneer de instellings waarden conflicteren.</span><span class="sxs-lookup"><span data-stu-id="92948-114">Unless stated otherwise, when the setting values conflict, the client-side values take precedence.</span></span>
<span data-ttu-id="92948-115">De waarden aan de client zijde kunnen echter niet in strijd zijn met de maximum waarden en quota's die in de sessie configuratie zijn ingesteld.</span><span class="sxs-lookup"><span data-stu-id="92948-115">However, the client-side values cannot violate maximum values and quotas set in the session configuration.</span></span>

<span data-ttu-id="92948-116">Zonder para meters, **New-PSTransportOption** genereert een transport optie object dat Null-waarden heeft voor alle opties.</span><span class="sxs-lookup"><span data-stu-id="92948-116">Without parameters, **New-PSTransportOption** generates a transport option object that has null values for all of the options.</span></span>
<span data-ttu-id="92948-117">Als u een para meter weglaat, heeft het object een null-waarde voor de eigenschap die door de para meter wordt vertegenwoordigd.</span><span class="sxs-lookup"><span data-stu-id="92948-117">If you omit a parameter, the object has a null value for the property that the parameter represents.</span></span>
<span data-ttu-id="92948-118">Een null-waarde heeft geen invloed op de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="92948-118">A null value does not affect the session configuration.</span></span>

<span data-ttu-id="92948-119">Zie New-PSSessionOption voor meer informatie over sessie opties.</span><span class="sxs-lookup"><span data-stu-id="92948-119">For more information about session options, see New-PSSessionOption.</span></span>
<span data-ttu-id="92948-120">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="92948-120">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="92948-121">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="92948-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="92948-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="92948-122">EXAMPLES</span></span>

### <span data-ttu-id="92948-123">Voor beeld 1: een standaard transport optie genereren</span><span class="sxs-lookup"><span data-stu-id="92948-123">Example 1: Generate a default transport option</span></span>

```
PS C:\> New-PSTransportOption
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

<span data-ttu-id="92948-124">Met deze opdracht wordt de **New-PSTransportOption** zonder para meters uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="92948-124">This command runs the **New-PSTransportOption** without parameters.</span></span>
<span data-ttu-id="92948-125">De uitvoer laat zien dat de cmdlet een transport optie object genereert dat Null-waarden voor alle eigenschappen heeft.</span><span class="sxs-lookup"><span data-stu-id="92948-125">The output shows that the cmdlet generates a transport option object that has null values for all properties.</span></span>

### <span data-ttu-id="92948-126">Voor beeld 2: opties voor sessie configuratie ophalen</span><span class="sxs-lookup"><span data-stu-id="92948-126">Example 2: Get session configuration options</span></span>

```
The first command uses the **New-PSTransportOption** cmdlet to create a transport options object, which it saves in the $t variable. The command uses the *MaxSessions* parameter to increase the maximum number of sessions to 40.
PS C:\> $t = New-PSTransportOption -MaxSessions 40

The second command uses the **Register-PSSessionConfiguration** cmdlet create the ITTasks session configuration. The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.
PS C:\> Register-PSSessionConfiguration -Name ITTasks -TransportOption $t

The third command uses the Get-PSSessionConfiguration cmdlet to get the ITTasks session configurations and the Format-List cmdlet to display all of the properties of the session configuration object in a list. The output shows that the value of the **MaxShells** property of the session configuration is 40.
PS C:\> Get-PSSessionConfiguration -Name ITTasks | Format-List -Property *
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

<span data-ttu-id="92948-127">In dit voor beeld ziet u hoe u een object transport opties gebruikt om opties voor sessie configuratie in te stellen.</span><span class="sxs-lookup"><span data-stu-id="92948-127">This example shows how to use a transport options object to set session configuration options.</span></span>

### <span data-ttu-id="92948-128">Voor beeld 3: een transport optie instellen</span><span class="sxs-lookup"><span data-stu-id="92948-128">Example 3: Setting a transport option</span></span>

```
The first command uses the **New-PSTransportOption** cmdlet to create a transport option object. The command uses the *IdleTimeoutSec* parameter to set the **IdleTimeoutSec** property value of the object to one hour (3600 seconds). The command saves the transport objects object in the $t variable.
PS C:\> $t = New-PSTransportOption -IdleTimeoutSec 3600

The second command uses the Set-PSSessionConfiguration cmdlet to change the transport options of the ITTasks session configuration. The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.
PS C:\> Set-PSSessionConfiguration -Name ITTasks -TransportOption $t

The third command uses the New-PSSession cmdlet to create the MyITTasks session on the local computer. The command uses the **ConfigurationName** property to specify the ITTasks session configuration. The command saves the session in the $s variable.Notice that the command does not use the *SessionOption* parameter of **New-PSSession** to set a custom idle time-out for the session. If it did, the idle time-out value set in the session option would take precedence over the idle time-out set in the session configuration.
PS C:\> $s = New-PSSession -Name MyITTasks -ConfigurationName ITTasks

The fourth command uses the Format-List cmdlet to display all properties of the session in the $s variable in a list. The output shows that the session has an idle time-out of one hour (360,000 milliseconds).
PS C:\> $s | Format-List -Property *
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

<span data-ttu-id="92948-129">Met deze opdracht wordt het effect weer gegeven van het instellen van een transport optie in een sessie configuratie op de sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="92948-129">This command shows the effect of setting a transport option in a session configuration on the sessions that use the session configuration.</span></span>

## <span data-ttu-id="92948-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="92948-130">PARAMETERS</span></span>

### <span data-ttu-id="92948-131">-IdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="92948-131">-IdleTimeoutSec</span></span>

<span data-ttu-id="92948-132">Hiermee wordt bepaald hoe lang elke sessie open blijft als de externe computer geen communicatie van de lokale computer ontvangt.</span><span class="sxs-lookup"><span data-stu-id="92948-132">Determines how long each session stays open if the remote computer does not receive any communication from the local computer.</span></span>
<span data-ttu-id="92948-133">Dit omvat het heartbeat-signaal.</span><span class="sxs-lookup"><span data-stu-id="92948-133">This includes the heartbeat signal.</span></span>
<span data-ttu-id="92948-134">Wanneer het interval is verlopen, wordt de sessie gesloten.</span><span class="sxs-lookup"><span data-stu-id="92948-134">When the interval expires, the session closes.</span></span>

<span data-ttu-id="92948-135">De time-outwaarde voor inactiviteit is van groot belang wanneer de gebruiker de verbinding verbreekt en opnieuw verbinding maakt met een sessie.</span><span class="sxs-lookup"><span data-stu-id="92948-135">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="92948-136">De gebruiker kan opnieuw verbinding maken als er geen time-out is opgetreden voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="92948-136">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="92948-137">De para meter *IdleTimeoutSec* komt overeen met de eigenschap **IdleTimeoutMs** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="92948-137">The *IdleTimeoutSec* parameter corresponds to the **IdleTimeoutMs** property of a session configuration.</span></span>

<span data-ttu-id="92948-138">Voer een waarde in seconden in.</span><span class="sxs-lookup"><span data-stu-id="92948-138">Enter a value in seconds.</span></span>
<span data-ttu-id="92948-139">De standaard waarde is 7200 (2 uur).</span><span class="sxs-lookup"><span data-stu-id="92948-139">The default value is 7200 (2 hours).</span></span>
<span data-ttu-id="92948-140">De minimum waarde is 60 (1 minuut).</span><span class="sxs-lookup"><span data-stu-id="92948-140">The minimum value is 60 (1 minute).</span></span>
<span data-ttu-id="92948-141">Het maximum is de waarde van de eigenschap **IdleTimeout** van shell-objecten in de WSMan-configuratie ( `WSMan:\\\<ComputerName\>\Shell\IdleTimeout` ).</span><span class="sxs-lookup"><span data-stu-id="92948-141">The maximum is the value of the **IdleTimeout** property of Shell objects in the WSMan configuration (`WSMan:\\\<ComputerName\>\Shell\IdleTimeout`).</span></span>
<span data-ttu-id="92948-142">De standaard waarde is 7200000 milliseconden (2 uur).</span><span class="sxs-lookup"><span data-stu-id="92948-142">The default value is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="92948-143">Als er een time-outwaarde voor inactiviteit is ingesteld in de sessie opties en in de sessie configuratie, krijgt de waarde die in de sessie opties is ingesteld prioriteit, maar kan de waarde van de eigenschap **MaxIdleTimeoutMs** van de sessie configuratie niet groter worden.</span><span class="sxs-lookup"><span data-stu-id="92948-143">If an idle time-out value is set in the session options and in the session configuration, value set in the session options takes precedence, but it cannot exceed the value of the **MaxIdleTimeoutMs** property of the session configuration.</span></span>
<span data-ttu-id="92948-144">Als u de waarde van de eigenschap **MaxIdleTimeoutMs** wilt instellen, gebruikt u de para meter *MaxIdleTimeoutSec* .</span><span class="sxs-lookup"><span data-stu-id="92948-144">To set the value of the **MaxIdleTimeoutMs** property, use the *MaxIdleTimeoutSec* parameter.</span></span>

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

### <span data-ttu-id="92948-145">-MaxConcurrentCommandsPerSession</span><span class="sxs-lookup"><span data-stu-id="92948-145">-MaxConcurrentCommandsPerSession</span></span>

<span data-ttu-id="92948-146">Beperkt het aantal opdrachten dat tegelijkertijd in elke sessie kan worden uitgevoerd naar de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="92948-146">Limits the number of commands that can run at the same time in each session to the specified value.</span></span>
<span data-ttu-id="92948-147">De standaardwaarde is 1000.</span><span class="sxs-lookup"><span data-stu-id="92948-147">The default value is 1000.</span></span>

<span data-ttu-id="92948-148">De para meter *MaxConcurrentCommandsPerSession* komt overeen met de eigenschap **MaxConcurrentCommandsPerShell** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="92948-148">The *MaxConcurrentCommandsPerSession* parameter corresponds to the **MaxConcurrentCommandsPerShell** property of a session configuration.</span></span>

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

### <span data-ttu-id="92948-149">-MaxConcurrentUsers</span><span class="sxs-lookup"><span data-stu-id="92948-149">-MaxConcurrentUsers</span></span>

<span data-ttu-id="92948-150">Beperkt het aantal gebruikers dat op hetzelfde moment in elke sessie opdrachten kan uitvoeren op de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="92948-150">Limits the number of users who can run commands at the same time in each session to the specified value.</span></span>
<span data-ttu-id="92948-151">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="92948-151">The default value is 5.</span></span>

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

### <span data-ttu-id="92948-152">-MaxIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="92948-152">-MaxIdleTimeoutSec</span></span>

<span data-ttu-id="92948-153">Hiermee wordt de time-out voor inactiviteit voor elke sessie beperkt tot de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="92948-153">Limits the idle time-out set for each session to the specified value.</span></span>
<span data-ttu-id="92948-154">De standaard waarde is \[ int \] :: MaxValue (~ 25 dagen).</span><span class="sxs-lookup"><span data-stu-id="92948-154">The default value is \[Int\]::MaxValue (~25 days).</span></span>

<span data-ttu-id="92948-155">De time-outwaarde voor inactiviteit is van groot belang wanneer de gebruiker de verbinding verbreekt en opnieuw verbinding maakt met een sessie.</span><span class="sxs-lookup"><span data-stu-id="92948-155">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="92948-156">De gebruiker kan opnieuw verbinding maken als er geen time-out is opgetreden voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="92948-156">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="92948-157">De para meter *MaxIdleTimeoutSec* komt overeen met de eigenschap **MaxIdleTimeoutMs** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="92948-157">The *MaxIdleTimeoutSec* parameter corresponds to the **MaxIdleTimeoutMs** property of a session configuration.</span></span>

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

### <span data-ttu-id="92948-158">-MaxMemoryPerSessionMB</span><span class="sxs-lookup"><span data-stu-id="92948-158">-MaxMemoryPerSessionMB</span></span>

<span data-ttu-id="92948-159">Hiermee wordt het geheugen dat door elke sessie wordt gebruikt, beperkt tot de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="92948-159">Limits the memory used by each session to the specified value.</span></span>
<span data-ttu-id="92948-160">Voer een waarde in mega bytes in.</span><span class="sxs-lookup"><span data-stu-id="92948-160">Enter a value in megabytes.</span></span>
<span data-ttu-id="92948-161">De standaard waarde is 1024 MB (1 GB).</span><span class="sxs-lookup"><span data-stu-id="92948-161">The default value is 1024 megabytes (1 GB).</span></span>

<span data-ttu-id="92948-162">De para meter *MaxMemoryPerSessionMB* komt overeen met de eigenschap **MaxMemoryPerShellMB** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="92948-162">The *MaxMemoryPerSessionMB* parameter corresponds to the **MaxMemoryPerShellMB** property of a session configuration.</span></span>

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

### <span data-ttu-id="92948-163">-MaxProcessesPerSession</span><span class="sxs-lookup"><span data-stu-id="92948-163">-MaxProcessesPerSession</span></span>

<span data-ttu-id="92948-164">Beperkt het aantal processen dat in elke sessie wordt uitgevoerd op de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="92948-164">Limits the number of processes running in each session to the specified value.</span></span>
<span data-ttu-id="92948-165">De standaard waarde is 15.</span><span class="sxs-lookup"><span data-stu-id="92948-165">The default value is 15.</span></span>

<span data-ttu-id="92948-166">De para meter *MaxProcessesPerSession* komt overeen met de eigenschap **MaxProcessesPerShell** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="92948-166">The *MaxProcessesPerSession* parameter corresponds to the **MaxProcessesPerShell** property of a session configuration.</span></span>

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

### <span data-ttu-id="92948-167">-MaxSessions</span><span class="sxs-lookup"><span data-stu-id="92948-167">-MaxSessions</span></span>

<span data-ttu-id="92948-168">Hiermee beperkt u het aantal sessies dat de sessie configuratie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="92948-168">Limits the number of sessions that use the session configuration.</span></span>
<span data-ttu-id="92948-169">De standaard waarde is 25.</span><span class="sxs-lookup"><span data-stu-id="92948-169">The default value is 25.</span></span>

<span data-ttu-id="92948-170">De para meter *maxsessions* komt overeen met de eigenschap **MaxShells** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="92948-170">The *MaxSessions* parameter corresponds to the **MaxShells** property of a session configuration.</span></span>

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

### <span data-ttu-id="92948-171">-MaxSessionsPerUser</span><span class="sxs-lookup"><span data-stu-id="92948-171">-MaxSessionsPerUser</span></span>

<span data-ttu-id="92948-172">Hiermee beperkt u het aantal sessies dat de sessie configuratie gebruikt en voert u uit met de referenties van een bepaalde gebruiker naar de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="92948-172">Limits the number of sessions that use the session configuration and run with the credentials of a given user to the specified value.</span></span>
<span data-ttu-id="92948-173">De standaard waarde is 25.</span><span class="sxs-lookup"><span data-stu-id="92948-173">The default value is 25.</span></span>

<span data-ttu-id="92948-174">Wanneer u deze waarde opgeeft, moet u er rekening mee houden dat veel gebruikers mogelijk gebruikmaken van de referenties van een run as-gebruiker.</span><span class="sxs-lookup"><span data-stu-id="92948-174">When you specify this value, consider that many users might be using the credentials of a run as user.</span></span>

<span data-ttu-id="92948-175">De para meter *MaxSessionsPerUser* komt overeen met de eigenschap **MaxShellsPerUser** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="92948-175">The *MaxSessionsPerUser* parameter corresponds to the **MaxShellsPerUser** property of a session configuration.</span></span>

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

### <span data-ttu-id="92948-176">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="92948-176">-OutputBufferingMode</span></span>

<span data-ttu-id="92948-177">Hiermee wordt bepaald hoe de uitvoer van de opdracht wordt beheerd in verbroken sessies wanneer de uitvoer buffer vol raakt.</span><span class="sxs-lookup"><span data-stu-id="92948-177">Determines how command output is managed in disconnected sessions when the output buffer becomes full.</span></span>
<span data-ttu-id="92948-178">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="92948-178">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="92948-179">Blok keren.</span><span class="sxs-lookup"><span data-stu-id="92948-179">Block.</span></span>
<span data-ttu-id="92948-180">Wanneer de uitvoer buffer vol is, wordt de uitvoering onderbroken totdat de buffer leeg is.</span><span class="sxs-lookup"><span data-stu-id="92948-180">When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="92948-181">Directe.</span><span class="sxs-lookup"><span data-stu-id="92948-181">Drop.</span></span>
<span data-ttu-id="92948-182">Wanneer de uitvoer buffer vol is, wordt de uitvoering voortgezet.</span><span class="sxs-lookup"><span data-stu-id="92948-182">When the output buffer is full, execution continues.</span></span>
<span data-ttu-id="92948-183">Wanneer er een nieuwe uitvoer wordt opgeslagen, wordt de oudste uitvoer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="92948-183">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="92948-184">Geen.</span><span class="sxs-lookup"><span data-stu-id="92948-184">None.</span></span>
<span data-ttu-id="92948-185">Er is geen uitvoer buffer modus opgegeven.</span><span class="sxs-lookup"><span data-stu-id="92948-185">No output buffering mode is specified.</span></span>

<span data-ttu-id="92948-186">De standaard waarde van de eigenschap **OutputBufferingMode** van sessies is blok keren.</span><span class="sxs-lookup"><span data-stu-id="92948-186">The default value of the **OutputBufferingMode** property of sessions is Block.</span></span>

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

### <span data-ttu-id="92948-187">-ProcessIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="92948-187">-ProcessIdleTimeoutSec</span></span>

<span data-ttu-id="92948-188">Hiermee wordt de time-out voor elk hostproces beperkt tot de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="92948-188">Limits the time-out for each host process to the specified value.</span></span>
<span data-ttu-id="92948-189">De standaard waarde, 0, betekent dat er geen time-outwaarde is voor het proces.</span><span class="sxs-lookup"><span data-stu-id="92948-189">The default value, 0, means that there is no time-out value for the process.</span></span>

<span data-ttu-id="92948-190">Andere sessie configuraties hebben time-outwaarden per proces.</span><span class="sxs-lookup"><span data-stu-id="92948-190">Other session configurations have per-process time-out values.</span></span>
<span data-ttu-id="92948-191">Bijvoorbeeld: de **micro soft. Power shell. werk stroom** sessie configuratie heeft een time-outwaarde van 28800 seconden (8 uur).</span><span class="sxs-lookup"><span data-stu-id="92948-191">For example, the **Microsoft.PowerShell.Workflow** session configuration has a per-process time-out value of 28800 seconds (8 hours).</span></span>

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

### <span data-ttu-id="92948-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="92948-192">CommonParameters</span></span>
<span data-ttu-id="92948-193">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="92948-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="92948-194">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="92948-194">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="92948-195">INVOER</span><span class="sxs-lookup"><span data-stu-id="92948-195">INPUTS</span></span>

### <span data-ttu-id="92948-196">Geen</span><span class="sxs-lookup"><span data-stu-id="92948-196">None</span></span>

<span data-ttu-id="92948-197">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="92948-197">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="92948-198">UITVOER</span><span class="sxs-lookup"><span data-stu-id="92948-198">OUTPUTS</span></span>

### <span data-ttu-id="92948-199">Micro soft. Power shell. commands. WSManConfigurationOption</span><span class="sxs-lookup"><span data-stu-id="92948-199">Microsoft.PowerShell.Commands.WSManConfigurationOption</span></span>

## <span data-ttu-id="92948-200">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="92948-200">NOTES</span></span>

- <span data-ttu-id="92948-201">De eigenschappen van een sessie configuratie object zijn afhankelijk van de opties die zijn ingesteld voor de sessie configuratie en de waarden van deze opties.</span><span class="sxs-lookup"><span data-stu-id="92948-201">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="92948-202">Daarnaast hebben sessie configuraties die gebruikmaken van een sessie configuratie bestand extra eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="92948-202">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="92948-203">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="92948-203">RELATED LINKS</span></span>

[<span data-ttu-id="92948-204">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="92948-204">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="92948-205">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="92948-205">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="92948-206">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="92948-206">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="92948-207">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="92948-207">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)
