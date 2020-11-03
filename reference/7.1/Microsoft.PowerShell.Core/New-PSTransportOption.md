---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pstransportoption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSTransportOption
ms.openlocfilehash: 7b7734c60a6a13d86f398418aeefce932e91a363
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251511"
---
# <span data-ttu-id="ac9c3-103">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="ac9c3-103">New-PSTransportOption</span></span>

## <span data-ttu-id="ac9c3-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ac9c3-104">SYNOPSIS</span></span>
<span data-ttu-id="ac9c3-105">Hiermee maakt u een object dat geavanceerde opties bevat voor een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-105">Creates an object that contains advanced options for a session configuration.</span></span>

## <span data-ttu-id="ac9c3-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ac9c3-106">SYNTAX</span></span>

```
New-PSTransportOption [-MaxIdleTimeoutSec <Int32>] [-ProcessIdleTimeoutSec <Int32>] [-MaxSessions <Int32>]
 [-MaxConcurrentCommandsPerSession <Int32>] [-MaxSessionsPerUser <Int32>] [-MaxMemoryPerSessionMB <Int32>]
 [-MaxProcessesPerSession <Int32>] [-MaxConcurrentUsers <Int32>] [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [<CommonParameters>]
```

## <span data-ttu-id="ac9c3-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ac9c3-107">DESCRIPTION</span></span>

<span data-ttu-id="ac9c3-108">Met de cmdlet **New-PSTransportOption** maakt u een object dat transport opties bevat voor sessie configuraties.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-108">The **New-PSTransportOption** cmdlet creates an object that contains transport options for session configurations.</span></span>
<span data-ttu-id="ac9c3-109">U kunt het object gebruiken als de waarde van de *TransportOption* -para meter van cmdlets waarmee een sessie configuratie wordt gemaakt of gewijzigd, zoals de Register-PSSessionConfiguration en Set-PSSessionConfiguration-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-109">You can use the object as the value of the *TransportOption* parameter of cmdlets that create or change a session configuration, such as the Register-PSSessionConfiguration and Set-PSSessionConfiguration cmdlets.</span></span>

<span data-ttu-id="ac9c3-110">U kunt ook de instellingen voor transport opties wijzigen door de waarden van de eigenschappen van de sessie configuratie te bewerken in het WSMan:-station.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-110">You can also change the transport option settings by editing the values of the session configuration properties in the WSMan: drive.</span></span>
<span data-ttu-id="ac9c3-111">Zie WSMan-provider voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-111">For more information, see WSMan Provider.</span></span>

<span data-ttu-id="ac9c3-112">De opties voor sessie configuratie vertegenwoordigen de sessie waarden die zijn ingesteld aan de server zijde of het ontvangende einde van een externe verbinding.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-112">The session configuration options represent the session values set on the server-side, or receiving end of a remote connection.</span></span>
<span data-ttu-id="ac9c3-113">Aan de client zijde of het verzenden van het einde van de verbinding, kan de sessie optie waarden instellen wanneer de sessie wordt gemaakt, of wanneer de client de verbinding met de sessie verbreekt of de verbinding opnieuw tot stand brengt.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-113">The client-side, or sending end of the connection, can set session option values when the session is created, or when the client disconnects from or reconnects to the session.</span></span>
<span data-ttu-id="ac9c3-114">Tenzij anders vermeld, worden de waarden van de client voor rang gegeven wanneer de instellings waarden conflicteren.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-114">Unless stated otherwise, when the setting values conflict, the client-side values take precedence.</span></span>
<span data-ttu-id="ac9c3-115">De waarden aan de client zijde kunnen echter niet in strijd zijn met de maximum waarden en quota's die in de sessie configuratie zijn ingesteld.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-115">However, the client-side values cannot violate maximum values and quotas set in the session configuration.</span></span>

<span data-ttu-id="ac9c3-116">Zonder para meters, **New-PSTransportOption** genereert een transport optie object dat Null-waarden heeft voor alle opties.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-116">Without parameters, **New-PSTransportOption** generates a transport option object that has null values for all of the options.</span></span>
<span data-ttu-id="ac9c3-117">Als u een para meter weglaat, heeft het object een null-waarde voor de eigenschap die door de para meter wordt vertegenwoordigd.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-117">If you omit a parameter, the object has a null value for the property that the parameter represents.</span></span>
<span data-ttu-id="ac9c3-118">Een null-waarde heeft geen invloed op de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-118">A null value does not affect the session configuration.</span></span>

<span data-ttu-id="ac9c3-119">Zie New-PSSessionOption voor meer informatie over sessie opties.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-119">For more information about session options, see New-PSSessionOption.</span></span>
<span data-ttu-id="ac9c3-120">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-120">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="ac9c3-121">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="ac9c3-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ac9c3-122">EXAMPLES</span></span>

### <span data-ttu-id="ac9c3-123">Voor beeld 1: een standaard transport optie genereren</span><span class="sxs-lookup"><span data-stu-id="ac9c3-123">Example 1: Generate a default transport option</span></span>

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

<span data-ttu-id="ac9c3-124">Met deze opdracht wordt de **New-PSTransportOption** zonder para meters uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-124">This command runs the **New-PSTransportOption** without parameters.</span></span>
<span data-ttu-id="ac9c3-125">De uitvoer laat zien dat de cmdlet een transport optie object genereert dat Null-waarden voor alle eigenschappen heeft.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-125">The output shows that the cmdlet generates a transport option object that has null values for all properties.</span></span>

### <span data-ttu-id="ac9c3-126">Voor beeld 2: opties voor sessie configuratie ophalen</span><span class="sxs-lookup"><span data-stu-id="ac9c3-126">Example 2: Get session configuration options</span></span>

<span data-ttu-id="ac9c3-127">In dit voor beeld ziet u hoe u een object transport opties gebruikt om opties voor sessie configuratie in te stellen.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-127">This example shows how to use a transport options object to set session configuration options.</span></span>

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

<span data-ttu-id="ac9c3-128">De eerste opdracht maakt gebruik van de cmdlet **New-PSTransportOption** voor het maken van een transport opties-object, dat wordt opgeslagen in de variabele $t.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-128">The first command uses the **New-PSTransportOption** cmdlet to create a transport options object, which it saves in the $t variable.</span></span> <span data-ttu-id="ac9c3-129">De opdracht gebruikt de para meter *maxsessions* om het maximum aantal sessies tot 40 te verhogen.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-129">The command uses the *MaxSessions* parameter to increase the maximum number of sessions to 40.</span></span>

<span data-ttu-id="ac9c3-130">De tweede opdracht maakt gebruik **van de cmdlet REGI ster-PSSessionConfiguration** om de configuratie van de ITTasks-sessie te maken.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-130">The second command uses the **Register-PSSessionConfiguration** cmdlet create the ITTasks session configuration.</span></span> <span data-ttu-id="ac9c3-131">De opdracht gebruikt de para meter *TransportOption* om het object transport opties in de variabele $t op te geven.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-131">The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.</span></span>

<span data-ttu-id="ac9c3-132">De derde opdracht maakt gebruik van de cmdlet Get-PSSessionConfiguration om de ITTasks-sessie configuraties en de Format-List-cmdlet te verkrijgen om alle eigenschappen van het sessie configuratie object in een lijst weer te geven.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-132">The third command uses the Get-PSSessionConfiguration cmdlet to get the ITTasks session configurations and the Format-List cmdlet to display all of the properties of the session configuration object in a list.</span></span> <span data-ttu-id="ac9c3-133">In de uitvoer ziet u dat de waarde van de eigenschap **MaxShells** van de sessie configuratie 40 is.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-133">The output shows that the value of the **MaxShells** property of the session configuration is 40.</span></span>

### <span data-ttu-id="ac9c3-134">Voor beeld 3: een transport optie instellen</span><span class="sxs-lookup"><span data-stu-id="ac9c3-134">Example 3: Setting a transport option</span></span>

<span data-ttu-id="ac9c3-135">Met deze opdracht wordt het effect weer gegeven van het instellen van een transport optie in een sessie configuratie op de sessies die gebruikmaken van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-135">This command shows the effect of setting a transport option in a session configuration on the sessions that use the session configuration.</span></span>

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

<span data-ttu-id="ac9c3-136">De eerste opdracht maakt gebruik van de cmdlet **New-PSTransportOption** om een transport optie object te maken.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-136">The first command uses the **New-PSTransportOption** cmdlet to create a transport option object.</span></span> <span data-ttu-id="ac9c3-137">De opdracht gebruikt de para meter *IdleTimeoutSec* om de waarde van de eigenschap **IdleTimeoutSec** van het object in te stellen op één uur (3600 seconden).</span><span class="sxs-lookup"><span data-stu-id="ac9c3-137">The command uses the *IdleTimeoutSec* parameter to set the **IdleTimeoutSec** property value of the object to one hour (3600 seconds).</span></span> <span data-ttu-id="ac9c3-138">Met de opdracht wordt het object Trans Port-objecten opgeslagen in de variabele $t.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-138">The command saves the transport objects object in the $t variable.</span></span>

<span data-ttu-id="ac9c3-139">De tweede opdracht gebruikt de cmdlet Set-PSSessionConfiguration om de transport opties van de ITTasks-sessie configuratie te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-139">The second command uses the Set-PSSessionConfiguration cmdlet to change the transport options of the ITTasks session configuration.</span></span> <span data-ttu-id="ac9c3-140">De opdracht gebruikt de para meter *TransportOption* om het object transport opties in de variabele $t op te geven.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-140">The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.</span></span>

<span data-ttu-id="ac9c3-141">De derde opdracht maakt gebruik van de cmdlet New-PSSession om de MyITTasks-sessie te maken op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-141">The third command uses the New-PSSession cmdlet to create the MyITTasks session on the local computer.</span></span> <span data-ttu-id="ac9c3-142">De opdracht gebruikt de eigenschap **configuratiepad** om de ITTasks-sessie configuratie op te geven.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-142">The command uses the **ConfigurationName** property to specify the ITTasks session configuration.</span></span> <span data-ttu-id="ac9c3-143">Met de opdracht wordt de sessie opgeslagen in de variabele $s. U ziet dat met de opdracht de para meter *SessionOption* van **New-PSSession** niet wordt gebruikt om een aangepaste time-out voor inactiviteit voor de sessie in te stellen.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-143">The command saves the session in the $s variable.Notice that the command does not use the *SessionOption* parameter of **New-PSSession** to set a custom idle time-out for the session.</span></span> <span data-ttu-id="ac9c3-144">Als dat het geval is, heeft de time-outwaarde voor inactiviteit in de sessie optie voor rang op de time-out voor inactiviteit die in de sessie configuratie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-144">If it did, the idle time-out value set in the session option would take precedence over the idle time-out set in the session configuration.</span></span>

<span data-ttu-id="ac9c3-145">De vierde opdracht maakt gebruik van de cmdlet Format-List om alle eigenschappen van de sessie weer te geven in de $s variabele in een lijst.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-145">The fourth command uses the Format-List cmdlet to display all properties of the session in the $s variable in a list.</span></span> <span data-ttu-id="ac9c3-146">In de uitvoer ziet u dat de sessie een time-out voor inactiviteit van één uur (360.000 milliseconden) heeft.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-146">The output shows that the session has an idle time-out of one hour (360,000 milliseconds).</span></span>

## <span data-ttu-id="ac9c3-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ac9c3-147">PARAMETERS</span></span>

### <span data-ttu-id="ac9c3-148">-IdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="ac9c3-148">-IdleTimeoutSec</span></span>

<span data-ttu-id="ac9c3-149">Hiermee wordt bepaald hoe lang elke sessie open blijft als de externe computer geen communicatie van de lokale computer ontvangt.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-149">Determines how long each session stays open if the remote computer does not receive any communication from the local computer.</span></span>
<span data-ttu-id="ac9c3-150">Dit omvat het heartbeat-signaal.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-150">This includes the heartbeat signal.</span></span>
<span data-ttu-id="ac9c3-151">Wanneer het interval is verlopen, wordt de sessie gesloten.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-151">When the interval expires, the session closes.</span></span>

<span data-ttu-id="ac9c3-152">De time-outwaarde voor inactiviteit is van groot belang wanneer de gebruiker de verbinding verbreekt en opnieuw verbinding maakt met een sessie.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-152">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="ac9c3-153">De gebruiker kan opnieuw verbinding maken als er geen time-out is opgetreden voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-153">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="ac9c3-154">De para meter *IdleTimeoutSec* komt overeen met de eigenschap **IdleTimeoutMs** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-154">The *IdleTimeoutSec* parameter corresponds to the **IdleTimeoutMs** property of a session configuration.</span></span>

<span data-ttu-id="ac9c3-155">Voer een waarde in seconden in.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-155">Enter a value in seconds.</span></span>
<span data-ttu-id="ac9c3-156">De standaard waarde is 7200 (2 uur).</span><span class="sxs-lookup"><span data-stu-id="ac9c3-156">The default value is 7200 (2 hours).</span></span>
<span data-ttu-id="ac9c3-157">De minimum waarde is 60 (1 minuut).</span><span class="sxs-lookup"><span data-stu-id="ac9c3-157">The minimum value is 60 (1 minute).</span></span>
<span data-ttu-id="ac9c3-158">Het maximum is de waarde van de eigenschap **IdleTimeout** van shell-objecten in de WSMan-configuratie ( `WSMan:\\\<ComputerName\>\Shell\IdleTimeout` ).</span><span class="sxs-lookup"><span data-stu-id="ac9c3-158">The maximum is the value of the **IdleTimeout** property of Shell objects in the WSMan configuration (`WSMan:\\\<ComputerName\>\Shell\IdleTimeout`).</span></span>
<span data-ttu-id="ac9c3-159">De standaard waarde is 7200000 milliseconden (2 uur).</span><span class="sxs-lookup"><span data-stu-id="ac9c3-159">The default value is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="ac9c3-160">Als er een time-outwaarde voor inactiviteit is ingesteld in de sessie opties en in de sessie configuratie, krijgt de waarde die in de sessie opties is ingesteld prioriteit, maar kan de waarde van de eigenschap **MaxIdleTimeoutMs** van de sessie configuratie niet groter worden.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-160">If an idle time-out value is set in the session options and in the session configuration, value set in the session options takes precedence, but it cannot exceed the value of the **MaxIdleTimeoutMs** property of the session configuration.</span></span>
<span data-ttu-id="ac9c3-161">Als u de waarde van de eigenschap **MaxIdleTimeoutMs** wilt instellen, gebruikt u de para meter *MaxIdleTimeoutSec* .</span><span class="sxs-lookup"><span data-stu-id="ac9c3-161">To set the value of the **MaxIdleTimeoutMs** property, use the *MaxIdleTimeoutSec* parameter.</span></span>

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

### <span data-ttu-id="ac9c3-162">-MaxConcurrentCommandsPerSession</span><span class="sxs-lookup"><span data-stu-id="ac9c3-162">-MaxConcurrentCommandsPerSession</span></span>

<span data-ttu-id="ac9c3-163">Beperkt het aantal opdrachten dat tegelijkertijd in elke sessie kan worden uitgevoerd naar de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-163">Limits the number of commands that can run at the same time in each session to the specified value.</span></span>
<span data-ttu-id="ac9c3-164">De standaardwaarde is 1000.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-164">The default value is 1000.</span></span>

<span data-ttu-id="ac9c3-165">De para meter *MaxConcurrentCommandsPerSession* komt overeen met de eigenschap **MaxConcurrentCommandsPerShell** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-165">The *MaxConcurrentCommandsPerSession* parameter corresponds to the **MaxConcurrentCommandsPerShell** property of a session configuration.</span></span>

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

### <span data-ttu-id="ac9c3-166">-MaxConcurrentUsers</span><span class="sxs-lookup"><span data-stu-id="ac9c3-166">-MaxConcurrentUsers</span></span>

<span data-ttu-id="ac9c3-167">Beperkt het aantal gebruikers dat op hetzelfde moment in elke sessie opdrachten kan uitvoeren op de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-167">Limits the number of users who can run commands at the same time in each session to the specified value.</span></span>
<span data-ttu-id="ac9c3-168">De standaard waarde is 5.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-168">The default value is 5.</span></span>

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

### <span data-ttu-id="ac9c3-169">-MaxIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="ac9c3-169">-MaxIdleTimeoutSec</span></span>

<span data-ttu-id="ac9c3-170">Hiermee wordt de time-out voor inactiviteit voor elke sessie beperkt tot de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-170">Limits the idle time-out set for each session to the specified value.</span></span>
<span data-ttu-id="ac9c3-171">De standaard waarde is \[ int \] :: MaxValue (~ 25 dagen).</span><span class="sxs-lookup"><span data-stu-id="ac9c3-171">The default value is \[Int\]::MaxValue (~25 days).</span></span>

<span data-ttu-id="ac9c3-172">De time-outwaarde voor inactiviteit is van groot belang wanneer de gebruiker de verbinding verbreekt en opnieuw verbinding maakt met een sessie.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-172">The idle time-out value is of significant importance when the user intends to disconnect and reconnect to a session.</span></span>
<span data-ttu-id="ac9c3-173">De gebruiker kan opnieuw verbinding maken als er geen time-out is opgetreden voor de sessie.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-173">The user can reconnect only if the session has not timed out.</span></span>

<span data-ttu-id="ac9c3-174">De para meter *MaxIdleTimeoutSec* komt overeen met de eigenschap **MaxIdleTimeoutMs** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-174">The *MaxIdleTimeoutSec* parameter corresponds to the **MaxIdleTimeoutMs** property of a session configuration.</span></span>

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

### <span data-ttu-id="ac9c3-175">-MaxMemoryPerSessionMB</span><span class="sxs-lookup"><span data-stu-id="ac9c3-175">-MaxMemoryPerSessionMB</span></span>

<span data-ttu-id="ac9c3-176">Hiermee wordt het geheugen dat door elke sessie wordt gebruikt, beperkt tot de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-176">Limits the memory used by each session to the specified value.</span></span>
<span data-ttu-id="ac9c3-177">Voer een waarde in mega bytes in.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-177">Enter a value in megabytes.</span></span>
<span data-ttu-id="ac9c3-178">De standaard waarde is 1024 MB (1 GB).</span><span class="sxs-lookup"><span data-stu-id="ac9c3-178">The default value is 1024 megabytes (1 GB).</span></span>

<span data-ttu-id="ac9c3-179">De para meter *MaxMemoryPerSessionMB* komt overeen met de eigenschap **MaxMemoryPerShellMB** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-179">The *MaxMemoryPerSessionMB* parameter corresponds to the **MaxMemoryPerShellMB** property of a session configuration.</span></span>

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

### <span data-ttu-id="ac9c3-180">-MaxProcessesPerSession</span><span class="sxs-lookup"><span data-stu-id="ac9c3-180">-MaxProcessesPerSession</span></span>

<span data-ttu-id="ac9c3-181">Beperkt het aantal processen dat in elke sessie wordt uitgevoerd op de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-181">Limits the number of processes running in each session to the specified value.</span></span>
<span data-ttu-id="ac9c3-182">De standaard waarde is 15.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-182">The default value is 15.</span></span>

<span data-ttu-id="ac9c3-183">De para meter *MaxProcessesPerSession* komt overeen met de eigenschap **MaxProcessesPerShell** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-183">The *MaxProcessesPerSession* parameter corresponds to the **MaxProcessesPerShell** property of a session configuration.</span></span>

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

### <span data-ttu-id="ac9c3-184">-MaxSessions</span><span class="sxs-lookup"><span data-stu-id="ac9c3-184">-MaxSessions</span></span>

<span data-ttu-id="ac9c3-185">Hiermee beperkt u het aantal sessies dat de sessie configuratie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-185">Limits the number of sessions that use the session configuration.</span></span>
<span data-ttu-id="ac9c3-186">De standaard waarde is 25.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-186">The default value is 25.</span></span>

<span data-ttu-id="ac9c3-187">De para meter *maxsessions* komt overeen met de eigenschap **MaxShells** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-187">The *MaxSessions* parameter corresponds to the **MaxShells** property of a session configuration.</span></span>

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

### <span data-ttu-id="ac9c3-188">-MaxSessionsPerUser</span><span class="sxs-lookup"><span data-stu-id="ac9c3-188">-MaxSessionsPerUser</span></span>

<span data-ttu-id="ac9c3-189">Hiermee beperkt u het aantal sessies dat de sessie configuratie gebruikt en voert u uit met de referenties van een bepaalde gebruiker naar de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-189">Limits the number of sessions that use the session configuration and run with the credentials of a given user to the specified value.</span></span>
<span data-ttu-id="ac9c3-190">De standaard waarde is 25.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-190">The default value is 25.</span></span>

<span data-ttu-id="ac9c3-191">Wanneer u deze waarde opgeeft, moet u er rekening mee houden dat veel gebruikers mogelijk gebruikmaken van de referenties van een run as-gebruiker.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-191">When you specify this value, consider that many users might be using the credentials of a run as user.</span></span>

<span data-ttu-id="ac9c3-192">De para meter *MaxSessionsPerUser* komt overeen met de eigenschap **MaxShellsPerUser** van een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-192">The *MaxSessionsPerUser* parameter corresponds to the **MaxShellsPerUser** property of a session configuration.</span></span>

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

### <span data-ttu-id="ac9c3-193">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="ac9c3-193">-OutputBufferingMode</span></span>

<span data-ttu-id="ac9c3-194">Hiermee wordt bepaald hoe de uitvoer van de opdracht wordt beheerd in verbroken sessies wanneer de uitvoer buffer vol raakt.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-194">Determines how command output is managed in disconnected sessions when the output buffer becomes full.</span></span>
<span data-ttu-id="ac9c3-195">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="ac9c3-195">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ac9c3-196">Blok keren.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-196">Block.</span></span>
<span data-ttu-id="ac9c3-197">Wanneer de uitvoer buffer vol is, wordt de uitvoering onderbroken totdat de buffer leeg is.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-197">When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="ac9c3-198">Directe.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-198">Drop.</span></span>
<span data-ttu-id="ac9c3-199">Wanneer de uitvoer buffer vol is, wordt de uitvoering voortgezet.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-199">When the output buffer is full, execution continues.</span></span>
<span data-ttu-id="ac9c3-200">Wanneer er een nieuwe uitvoer wordt opgeslagen, wordt de oudste uitvoer verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-200">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="ac9c3-201">Geen.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-201">None.</span></span>
<span data-ttu-id="ac9c3-202">Er is geen uitvoer buffer modus opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-202">No output buffering mode is specified.</span></span>

<span data-ttu-id="ac9c3-203">De standaard waarde van de eigenschap **OutputBufferingMode** van sessies is blok keren.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-203">The default value of the **OutputBufferingMode** property of sessions is Block.</span></span>

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

### <span data-ttu-id="ac9c3-204">-ProcessIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="ac9c3-204">-ProcessIdleTimeoutSec</span></span>

<span data-ttu-id="ac9c3-205">Hiermee wordt de time-out voor elk hostproces beperkt tot de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-205">Limits the time-out for each host process to the specified value.</span></span>
<span data-ttu-id="ac9c3-206">De standaard waarde, 0, betekent dat er geen time-outwaarde is voor het proces.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-206">The default value, 0, means that there is no time-out value for the process.</span></span>

<span data-ttu-id="ac9c3-207">Andere sessie configuraties hebben time-outwaarden per proces.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-207">Other session configurations have per-process time-out values.</span></span>
<span data-ttu-id="ac9c3-208">Bijvoorbeeld: de **micro soft. Power shell. werk stroom** sessie configuratie heeft een time-outwaarde van 28800 seconden (8 uur).</span><span class="sxs-lookup"><span data-stu-id="ac9c3-208">For example, the **Microsoft.PowerShell.Workflow** session configuration has a per-process time-out value of 28800 seconds (8 hours).</span></span>

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

### <span data-ttu-id="ac9c3-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ac9c3-209">CommonParameters</span></span>

<span data-ttu-id="ac9c3-210">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ac9c3-211">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ac9c3-212">INVOER</span><span class="sxs-lookup"><span data-stu-id="ac9c3-212">INPUTS</span></span>

### <span data-ttu-id="ac9c3-213">Geen</span><span class="sxs-lookup"><span data-stu-id="ac9c3-213">None</span></span>

<span data-ttu-id="ac9c3-214">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-214">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="ac9c3-215">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ac9c3-215">OUTPUTS</span></span>

### <span data-ttu-id="ac9c3-216">Micro soft. Power shell. commands. WSManConfigurationOption</span><span class="sxs-lookup"><span data-stu-id="ac9c3-216">Microsoft.PowerShell.Commands.WSManConfigurationOption</span></span>

## <span data-ttu-id="ac9c3-217">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ac9c3-217">NOTES</span></span>

- <span data-ttu-id="ac9c3-218">De eigenschappen van een sessie configuratie object zijn afhankelijk van de opties die zijn ingesteld voor de sessie configuratie en de waarden van deze opties.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-218">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="ac9c3-219">Daarnaast hebben sessie configuraties die gebruikmaken van een sessie configuratie bestand extra eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="ac9c3-219">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="ac9c3-220">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ac9c3-220">RELATED LINKS</span></span>

[<span data-ttu-id="ac9c3-221">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="ac9c3-221">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="ac9c3-222">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="ac9c3-222">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="ac9c3-223">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ac9c3-223">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="ac9c3-224">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ac9c3-224">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

