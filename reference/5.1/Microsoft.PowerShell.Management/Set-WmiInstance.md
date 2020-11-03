---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-wmiinstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WmiInstance
ms.openlocfilehash: 03288a2ffbef416937b2c92a7d08a5aed49ffb43
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250546"
---
# <span data-ttu-id="13711-103">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="13711-103">Set-WmiInstance</span></span>

## <span data-ttu-id="13711-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="13711-104">SYNOPSIS</span></span>
<span data-ttu-id="13711-105">Hiermee wordt een exemplaar van een bestaande Windows Management Instrumentation (WMI)-klasse gemaakt of bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="13711-105">Creates or updates an instance of an existing Windows Management Instrumentation (WMI) class.</span></span>

## <span data-ttu-id="13711-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="13711-106">SYNTAX</span></span>

### <span data-ttu-id="13711-107">klasse (standaard)</span><span class="sxs-lookup"><span data-stu-id="13711-107">class (Default)</span></span>

```
Set-WmiInstance [-Class] <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="13711-108">object</span><span class="sxs-lookup"><span data-stu-id="13711-108">object</span></span>

```
Set-WmiInstance -InputObject <ManagementObject> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="13711-109">leertraject</span><span class="sxs-lookup"><span data-stu-id="13711-109">path</span></span>

```
Set-WmiInstance -Path <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="13711-110">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="13711-110">WQLQuery</span></span>

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="13711-111">query</span><span class="sxs-lookup"><span data-stu-id="13711-111">query</span></span>

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="13711-112">list</span><span class="sxs-lookup"><span data-stu-id="13711-112">list</span></span>

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="13711-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="13711-113">DESCRIPTION</span></span>
<span data-ttu-id="13711-114">`Set-WmiInstance`Met de cmdlet wordt een exemplaar van een bestaande Windows Management Instrumentation (WMI)-klasse gemaakt of bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="13711-114">The `Set-WmiInstance` cmdlet creates or updates an instance of an existing Windows Management Instrumentation (WMI) class.</span></span>
<span data-ttu-id="13711-115">Het gemaakte of bijgewerkte exemplaar wordt naar de WMI-opslag plaats geschreven.</span><span class="sxs-lookup"><span data-stu-id="13711-115">The created or updated instance is written to the WMI repository.</span></span>

<span data-ttu-id="13711-116">Nieuwe CIM-cmdlets, geïntroduceerd in Windows Power Shell 3,0, voert dezelfde taken uit als de WMI-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="13711-116">New CIM cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span>
<span data-ttu-id="13711-117">De CIM-cmdlets voldoen aan de WS-Management (WSMan)-standaarden en met de Common Information Model (CIM) standaard.</span><span class="sxs-lookup"><span data-stu-id="13711-117">The CIM cmdlets comply with WS-Management (WSMan) standards and with the Common Information Model (CIM) standard.</span></span>
<span data-ttu-id="13711-118">op deze manier kunnen cmdlets dezelfde technieken gebruiken voor het beheren van Windows-computers en die met andere besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="13711-118">this enables cmdlets to use the same techniques to manage Windows-based computers and those running other operating systems.</span></span>
<span data-ttu-id="13711-119">In plaats van met kunt `Set-WmiInstance` u overwegen de cmdlets [set-CimInstance](/powershell/module/cimcmdlets/set-ciminstance) of [New-CimInstance](/powershell/module/cimcmdlets/new-ciminstance) te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="13711-119">Instead of using `Set-WmiInstance`, consider using the [Set-CimInstance](/powershell/module/cimcmdlets/set-ciminstance) or [New-CimInstance](/powershell/module/cimcmdlets/new-ciminstance) cmdlets.</span></span>

## <span data-ttu-id="13711-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="13711-120">EXAMPLES</span></span>

### <span data-ttu-id="13711-121">Voor beeld 1: WMI-logboek registratie niveau instellen</span><span class="sxs-lookup"><span data-stu-id="13711-121">Example 1: Set WMI logging level</span></span>

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2}
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
```

<span data-ttu-id="13711-122">Met deze opdracht wordt het WMI-logboek registratie niveau ingesteld op 2.</span><span class="sxs-lookup"><span data-stu-id="13711-122">This command sets the WMI logging level to 2.</span></span>
<span data-ttu-id="13711-123">De opdracht geeft de eigenschap die moet worden ingesteld en de waarde, samen als een waardepaar, in de para meter argument.</span><span class="sxs-lookup"><span data-stu-id="13711-123">The command passes the property to be set and the value, together considered a value pair, in the argument parameter.</span></span>
<span data-ttu-id="13711-124">De para meter gebruikt een hash-tabel die is gedefinieerd door de constructie @ {Property = Value}.</span><span class="sxs-lookup"><span data-stu-id="13711-124">The parameter takes a hash table that is defined by the @{property = value} construction.</span></span>
<span data-ttu-id="13711-125">De geretourneerde klasse-informatie weerspiegelt de nieuwe waarde.</span><span class="sxs-lookup"><span data-stu-id="13711-125">The class information that is returned reflects the new value.</span></span>

### <span data-ttu-id="13711-126">Voor beeld 2: een omgevings variabele en de waarde ervan maken</span><span class="sxs-lookup"><span data-stu-id="13711-126">Example 2: Create an environment variable and its value</span></span>

```
PS C:\> Set-WmiInstance -Class win32_environment -Argument @{Name="testvar";VariableValue="testvalue";UserName="<SYSTEM>"}
__GENUS          : 2
__CLASS          : Win32_Environment
__SUPERCLASS     : CIM_SystemResource
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Environment.Name="testvar",UserName="<SYSTEM>"
__PROPERTY_COUNT : 8
__DERIVATION     : {CIM_SystemResource, CIM_LogicalElement, CIM_ManagedSystemElement}
__SERVER         : SYSTEM01
__NAMESPACE      : root\cimv2
__PATH           : \\SYSTEM01\root\cimv2:Win32_Environment.Name="testvar",UserName="<SYSTEM>"
Caption          : <SYSTEM>\testvar
Description      : <SYSTEM>\testvar
InstallDate      :
Name             : testvar
Status           : OK
SystemVariable   : True
UserName         : <SYSTEM>
VariableValue    : testvalue
```

<span data-ttu-id="13711-127">Met deze opdracht maakt u de omgevings variabele TestVar met de waarde testvalue.</span><span class="sxs-lookup"><span data-stu-id="13711-127">This command creates the testvar environment variable that has the value testvalue.</span></span>
<span data-ttu-id="13711-128">Dit doet u door een nieuw exemplaar van de WMI-klasse **Win32_Environment** te maken.</span><span class="sxs-lookup"><span data-stu-id="13711-128">It does this by creating a new instance of the **Win32_Environment** WMI class.</span></span>
<span data-ttu-id="13711-129">Deze bewerking vereist de juiste referenties en u moet Windows Power shell mogelijk opnieuw opstarten om de nieuwe omgevings variabele te zien.</span><span class="sxs-lookup"><span data-stu-id="13711-129">This operation requires appropriate credentials and that you may have to restart Windows PowerShell to see the new environment variable.</span></span>

### <span data-ttu-id="13711-130">Voor beeld 3: het WMI-logboek registratie niveau instellen voor verschillende externe computers</span><span class="sxs-lookup"><span data-stu-id="13711-130">Example 3: Set WMI logging level for several remote computers</span></span>

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2} -Computername "system01", "system02", "system03"
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
...
```

<span data-ttu-id="13711-131">Met deze opdracht wordt het WMI-logboek registratie niveau ingesteld op 2.</span><span class="sxs-lookup"><span data-stu-id="13711-131">This command sets the WMI logging level to 2.</span></span>
<span data-ttu-id="13711-132">De opdracht geeft de eigenschap die moet worden ingesteld en de waarde, samen als een waardepaar, in de para meter argument.</span><span class="sxs-lookup"><span data-stu-id="13711-132">The command passes the property to be set and the value, together considered a value pair, in the argument parameter.</span></span>
<span data-ttu-id="13711-133">De para meter gebruikt een hash-tabel die is gedefinieerd door de constructie @ {Property = Value}.</span><span class="sxs-lookup"><span data-stu-id="13711-133">The parameter takes a hash table that is defined by the @{property = value} construction.</span></span>
<span data-ttu-id="13711-134">De geretourneerde klassegegevens weerspiegelt de nieuwe waarde.</span><span class="sxs-lookup"><span data-stu-id="13711-134">The returned class information reflects the new value.</span></span>

## <span data-ttu-id="13711-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="13711-135">PARAMETERS</span></span>

### <span data-ttu-id="13711-136">-Argumenten</span><span class="sxs-lookup"><span data-stu-id="13711-136">-Arguments</span></span>
<span data-ttu-id="13711-137">Hiermee geeft u de naam op van de eigenschap die moet worden gewijzigd en de nieuwe waarde voor die eigenschap.</span><span class="sxs-lookup"><span data-stu-id="13711-137">Specifies the name of the property to be changed and the new value for that property.</span></span>
<span data-ttu-id="13711-138">De naam en de waarde moeten een naam/waarde-paar zijn.</span><span class="sxs-lookup"><span data-stu-id="13711-138">The name and value must be a name-value pair.</span></span>
<span data-ttu-id="13711-139">De naam/waarde-paar wordt door gegeven op de opdracht regel als een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="13711-139">The name-value pair is passed on the command line as a hash table.</span></span>
<span data-ttu-id="13711-140">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="13711-140">For example:</span></span>

`@{Setting1=1; Setting2=5; Setting3="test"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: class, object, path
Aliases: Args, Property

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13711-141">-AsJob</span><span class="sxs-lookup"><span data-stu-id="13711-141">-AsJob</span></span>
<span data-ttu-id="13711-142">Geeft aan dat deze cmdket wordt uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="13711-142">Indicates that this cmdket runs as a background job.</span></span>
<span data-ttu-id="13711-143">Gebruik deze para meter om opdrachten uit te voeren die lange tijd duren om te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="13711-143">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="13711-144">Wanneer u de para meter *AsJob* opgeeft, retourneert de opdracht een object dat de achtergrond taak vertegenwoordigt en wordt vervolgens de opdracht prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="13711-144">When you specify the *AsJob* parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span>
<span data-ttu-id="13711-145">U kunt in de sessie blijven werken terwijl de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="13711-145">You can continue to work in the session while the job finishes.</span></span>
<span data-ttu-id="13711-146">Als **set-WmiInstance** wordt gebruikt voor een externe computer, wordt de taak gemaakt op de lokale computer en worden de resultaten van externe computers automatisch teruggestuurd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="13711-146">If **Set-WmiInstance** is used for a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="13711-147">Als u de taak wilt beheren, gebruikt u de cmdlets die het zelfstandige **taak** onderdeel (de **taak** -cmdlets) bevatten.</span><span class="sxs-lookup"><span data-stu-id="13711-147">To manage the job, use the cmdlets that contain the **Job** noun (the **Job** cmdlets).</span></span>
<span data-ttu-id="13711-148">Gebruik de cmdlet Receive-Job om de taak resultaten te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="13711-148">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="13711-149">Als u deze para meter samen met externe computers wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="13711-149">To use this parameter together with remote computers, the local and remote computers must be configured for remoting.</span></span>
<span data-ttu-id="13711-150">Daarnaast moet u Windows Power shell starten met de optie als administrator uitvoeren in Windows Vista en latere versies van het Windows-besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="13711-150">Additionally, you must start Windows PowerShell by using the Run as administrator option in Windows Vista and later versions of the Windows operating system.</span></span>
<span data-ttu-id="13711-151">Zie about_Remote_Requirements voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="13711-151">For more information, see about_Remote_Requirements.</span></span>

<span data-ttu-id="13711-152">Zie about_Jobs en about_Remote_Jobs voor meer informatie over Windows Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="13711-152">For more information about Windows PowerShell background jobs, see about_Jobs and about_Remote_Jobs.</span></span>

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

### <span data-ttu-id="13711-153">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="13711-153">-Authentication</span></span>
<span data-ttu-id="13711-154">Hiermee geeft u het verificatie niveau op dat moet worden gebruikt met de WMI-verbinding.</span><span class="sxs-lookup"><span data-stu-id="13711-154">Specifies the authentication level that must be used with the WMI connection.</span></span>
<span data-ttu-id="13711-155">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="13711-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="13711-156">-1: ongewijzigd.</span><span class="sxs-lookup"><span data-stu-id="13711-156">-1: Unchanged.</span></span>
- <span data-ttu-id="13711-157">0: standaard.</span><span class="sxs-lookup"><span data-stu-id="13711-157">0: Default.</span></span>
- <span data-ttu-id="13711-158">1: geen.</span><span class="sxs-lookup"><span data-stu-id="13711-158">1: None.</span></span>
<span data-ttu-id="13711-159">Er is geen verificatie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="13711-159">No authentication in performed.</span></span>
- <span data-ttu-id="13711-160">2: verbinding maken.</span><span class="sxs-lookup"><span data-stu-id="13711-160">2: Connect.</span></span>
<span data-ttu-id="13711-161">Verificatie wordt alleen uitgevoerd wanneer de client een relatie met de toepassing tot stand brengt.</span><span class="sxs-lookup"><span data-stu-id="13711-161">Authentication is performed only when the client establishes a relationship with the application.</span></span>
- <span data-ttu-id="13711-162">3: bellen.</span><span class="sxs-lookup"><span data-stu-id="13711-162">3: Call.</span></span>
<span data-ttu-id="13711-163">Verificatie wordt alleen aan het begin van elke aanroep uitgevoerd wanneer de toepassing de aanvraag ontvangt.</span><span class="sxs-lookup"><span data-stu-id="13711-163">Authentication is performed only at the start of each call when the application receives the request.</span></span>
- <span data-ttu-id="13711-164">4: pakket.</span><span class="sxs-lookup"><span data-stu-id="13711-164">4: Packet.</span></span>
<span data-ttu-id="13711-165">Verificatie wordt uitgevoerd op alle gegevens die van de client worden ontvangen.</span><span class="sxs-lookup"><span data-stu-id="13711-165">Authentication is performed on all the data that is received from the client.</span></span>
- <span data-ttu-id="13711-166">5: PacketIntegrity.</span><span class="sxs-lookup"><span data-stu-id="13711-166">5: PacketIntegrity.</span></span>
<span data-ttu-id="13711-167">Alle gegevens die worden overgebracht tussen de client en de toepassing, worden geverifieerd en geverifieerd.</span><span class="sxs-lookup"><span data-stu-id="13711-167">All the data that is transferred between the client and the application is authenticated and verified.</span></span>
- <span data-ttu-id="13711-168">6: PacketPrivacy.</span><span class="sxs-lookup"><span data-stu-id="13711-168">6: PacketPrivacy.</span></span>
<span data-ttu-id="13711-169">De eigenschappen van de andere authenticatie niveaus worden gebruikt en alle gegevens worden versleuteld.</span><span class="sxs-lookup"><span data-stu-id="13711-169">The properties of the other authentication levels are used, and all the data is encrypted.</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13711-170">-Authority</span><span class="sxs-lookup"><span data-stu-id="13711-170">-Authority</span></span>
<span data-ttu-id="13711-171">Hiermee geeft u de instantie op die moet worden gebruikt om de WMI-verbinding te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="13711-171">Specifies the authority to use to authenticate the WMI connection.</span></span>
<span data-ttu-id="13711-172">U kunt standaard NTLM-of Kerberos-verificatie opgeven.</span><span class="sxs-lookup"><span data-stu-id="13711-172">You can specify standard NTLM or Kerberos authentication.</span></span>
<span data-ttu-id="13711-173">Als u NTLM wilt gebruiken, stelt u de instelling van de instantie in op ntlmdomain: \<DomainName\> , waarbij \<DomainName\> een geldige NTLM-domein naam wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="13711-173">To use NTLM, set the authority setting to ntlmdomain:\<DomainName\>, where \<DomainName\> identifies a valid NTLM domain name.</span></span>
<span data-ttu-id="13711-174">Als u Kerberos wilt gebruiken, geeft u Kerberos op: \<DomainName\> \\ \<ServerName\> .</span><span class="sxs-lookup"><span data-stu-id="13711-174">To use Kerberos, specify kerberos:\<DomainName\>\\\<ServerName\>.</span></span>
<span data-ttu-id="13711-175">U kunt de instelling van de instantie niet toevoegen wanneer u verbinding maakt met de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="13711-175">You cannot include the authority setting when you connect to the local computer.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13711-176">-Klasse</span><span class="sxs-lookup"><span data-stu-id="13711-176">-Class</span></span>
<span data-ttu-id="13711-177">Hiermee geeft u de naam van een WMI-klasse op.</span><span class="sxs-lookup"><span data-stu-id="13711-177">Specifies the name of a WMI class.</span></span>

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13711-178">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="13711-178">-ComputerName</span></span>
<span data-ttu-id="13711-179">Hiermee geeft u de naam op van de computer waarop deze cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="13711-179">Specifies the name of the computer on which this cmdlet runs.</span></span>
<span data-ttu-id="13711-180">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="13711-180">The default is the local computer.</span></span>

<span data-ttu-id="13711-181">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een of meer computers.</span><span class="sxs-lookup"><span data-stu-id="13711-181">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more computers.</span></span>
<span data-ttu-id="13711-182">Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt (.) of localhost.</span><span class="sxs-lookup"><span data-stu-id="13711-182">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="13711-183">Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="13711-183">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="13711-184">U kunt de para meter *ComputerName* ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="13711-184">You can use the *ComputerName* parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: class, path, WQLQuery, query, list
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13711-185">-Credential</span><span class="sxs-lookup"><span data-stu-id="13711-185">-Credential</span></span>
<span data-ttu-id="13711-186">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="13711-186">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="13711-187">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="13711-187">The default is the current user.</span></span>

<span data-ttu-id="13711-188">Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de cmdlet Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="13711-188">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="13711-189">Als u een gebruikers naam typt, wordt met deze cmdlet om een wacht woord gevraagd.</span><span class="sxs-lookup"><span data-stu-id="13711-189">If you type a user name, this cmdlet prompts for a password.</span></span>

<span data-ttu-id="13711-190">Deze para meter wordt niet ondersteund door providers die met een para meter zijn geïnstalleerd, worden niet ondersteund door providers die zijn geïnstalleerd met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="13711-190">This parameter is not supported by any providers installed with parameter is not supported by any providers installed with Windows PowerShell.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13711-191">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="13711-191">-EnableAllPrivileges</span></span>
<span data-ttu-id="13711-192">Hiermee wordt aangegeven dat met deze cmdlet alle machtigingen van de huidige gebruiker worden ingeschakeld voordat de opdracht de WMI-aanroep uitvoert.</span><span class="sxs-lookup"><span data-stu-id="13711-192">Indicates that this cmdlet enables all the permissions of the current user before the command it makes the WMI call.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13711-193">-Imitatie</span><span class="sxs-lookup"><span data-stu-id="13711-193">-Impersonation</span></span>
<span data-ttu-id="13711-194">Hiermee geeft u het imitatie niveau op dat moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="13711-194">Specifies the impersonation level to use.</span></span>
<span data-ttu-id="13711-195">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="13711-195">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="13711-196">0: standaard.</span><span class="sxs-lookup"><span data-stu-id="13711-196">0: Default.</span></span>
<span data-ttu-id="13711-197">Leest het lokale REGI ster voor het standaard imitatie niveau, dat meestal is ingesteld op 3: imiteren.</span><span class="sxs-lookup"><span data-stu-id="13711-197">Reads the local registry for the default impersonation level, which is usually set to 3: Impersonate.</span></span>
- <span data-ttu-id="13711-198">1: anoniem.</span><span class="sxs-lookup"><span data-stu-id="13711-198">1: Anonymous.</span></span>
<span data-ttu-id="13711-199">Hiermee worden de referenties van de aanroep functie verborgen.</span><span class="sxs-lookup"><span data-stu-id="13711-199">Hides the credentials of the caller.</span></span>
- <span data-ttu-id="13711-200">2: identificeren.</span><span class="sxs-lookup"><span data-stu-id="13711-200">2: Identify.</span></span>
<span data-ttu-id="13711-201">Hiermee kunnen objecten query's uitvoeren op de referenties van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="13711-201">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="13711-202">3: imiteren.</span><span class="sxs-lookup"><span data-stu-id="13711-202">3: Impersonate.</span></span>
<span data-ttu-id="13711-203">Toestaan dat objecten de referenties van de aanroep functie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="13711-203">Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="13711-204">4: delegeren.</span><span class="sxs-lookup"><span data-stu-id="13711-204">4: Delegate.</span></span>
<span data-ttu-id="13711-205">Hiermee kunnen objecten andere objecten toestaan de referenties van de aanroeper te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="13711-205">Allows objects to permit other objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13711-206">-Input object</span><span class="sxs-lookup"><span data-stu-id="13711-206">-InputObject</span></span>
<span data-ttu-id="13711-207">Hiermee geeft u een **ManagementObject** -object moet worden gebruikt als invoer.</span><span class="sxs-lookup"><span data-stu-id="13711-207">Specifies a **ManagementObject** object to use as input.</span></span>
<span data-ttu-id="13711-208">Als deze para meter wordt gebruikt, worden alle andere para meters, met uitzonde ring van de *argumenten* para meter, genegeerd.</span><span class="sxs-lookup"><span data-stu-id="13711-208">When this parameter is used, all other parameters ,except the *Arguments* parameter, are ignored.</span></span>

```yaml
Type: System.Management.ManagementObject
Parameter Sets: object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="13711-209">-Land instellingen</span><span class="sxs-lookup"><span data-stu-id="13711-209">-Locale</span></span>
<span data-ttu-id="13711-210">Hiermee geeft u de voorkeurs land instelling voor WMI-objecten.</span><span class="sxs-lookup"><span data-stu-id="13711-210">Specifies the preferred locale for WMI objects.</span></span>
<span data-ttu-id="13711-211">De para meter *locale* is opgegeven in een matrix in de MS_ \<LCID\> indeling in de gewenste volg orde.</span><span class="sxs-lookup"><span data-stu-id="13711-211">The *Locale* parameter is specified in an array in the MS_\<LCID\> format in the preferred order.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13711-212">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="13711-212">-Namespace</span></span>
<span data-ttu-id="13711-213">Hiermee geeft u de naam ruimte van de WMI-opslag plaats waar de WMI-klasse waarnaar wordt verwezen zich bevindt als deze wordt gebruikt met de para meter *Class* .</span><span class="sxs-lookup"><span data-stu-id="13711-213">Specifies the WMI repository namespace where the referenced WMI class is located when it is used with the *Class* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13711-214">-Path</span><span class="sxs-lookup"><span data-stu-id="13711-214">-Path</span></span>
<span data-ttu-id="13711-215">Hiermee geeft u een WMI-objectpad van het exemplaar dat u wilt maken of bijwerken.</span><span class="sxs-lookup"><span data-stu-id="13711-215">Specifies a WMI object path of the instance that you want to create or update.</span></span>

```yaml
Type: System.String
Parameter Sets: path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13711-216">-PutType</span><span class="sxs-lookup"><span data-stu-id="13711-216">-PutType</span></span>
<span data-ttu-id="13711-217">Hiermee wordt aangegeven of het WMI-exemplaar moet worden gemaakt of bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="13711-217">Indicates whether to create or update the WMI instance.</span></span>
<span data-ttu-id="13711-218">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="13711-218">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="13711-219">UpdateOnly.</span><span class="sxs-lookup"><span data-stu-id="13711-219">UpdateOnly.</span></span>
<span data-ttu-id="13711-220">Hiermee wordt een bestaand WMI-exemplaar bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="13711-220">Updates an existing WMI instance.</span></span>
- <span data-ttu-id="13711-221">CreateOnly.</span><span class="sxs-lookup"><span data-stu-id="13711-221">CreateOnly.</span></span>
<span data-ttu-id="13711-222">Hiermee maakt u een nieuw WMI-exemplaar.</span><span class="sxs-lookup"><span data-stu-id="13711-222">Creates a new WMI instance.</span></span>
- <span data-ttu-id="13711-223">UpdateOrCreate.</span><span class="sxs-lookup"><span data-stu-id="13711-223">UpdateOrCreate.</span></span>
<span data-ttu-id="13711-224">Hiermee wordt het WMI-exemplaar bijgewerkt als het bestaat of een nieuw exemplaar maakt als er geen exemplaar bestaat.</span><span class="sxs-lookup"><span data-stu-id="13711-224">Updates the WMI instance if it exists or creates a new instance if an instance does not exist.</span></span>

```yaml
Type: System.Management.PutType
Parameter Sets: (All)
Aliases:
Accepted values: None, UpdateOnly, CreateOnly, UpdateOrCreate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13711-225">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="13711-225">-ThrottleLimit</span></span>
<span data-ttu-id="13711-226">Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="13711-226">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="13711-227">Deze para meter wordt gebruikt in combi natie met de para meter *AsJob* .</span><span class="sxs-lookup"><span data-stu-id="13711-227">This parameter is used together with the *AsJob* parameter.</span></span>
<span data-ttu-id="13711-228">De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="13711-228">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="13711-229">-Confirm</span><span class="sxs-lookup"><span data-stu-id="13711-229">-Confirm</span></span>
<span data-ttu-id="13711-230">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="13711-230">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13711-231">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="13711-231">-WhatIf</span></span>
<span data-ttu-id="13711-232">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="13711-232">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="13711-233">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="13711-233">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="13711-234">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="13711-234">CommonParameters</span></span>
<span data-ttu-id="13711-235">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="13711-235">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="13711-236">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="13711-236">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="13711-237">INVOER</span><span class="sxs-lookup"><span data-stu-id="13711-237">INPUTS</span></span>

### <span data-ttu-id="13711-238">Geen</span><span class="sxs-lookup"><span data-stu-id="13711-238">None</span></span>
<span data-ttu-id="13711-239">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="13711-239">This cmdlet does not accept input.</span></span>

## <span data-ttu-id="13711-240">UITVOER</span><span class="sxs-lookup"><span data-stu-id="13711-240">OUTPUTS</span></span>

### <span data-ttu-id="13711-241">Geen</span><span class="sxs-lookup"><span data-stu-id="13711-241">None</span></span>
<span data-ttu-id="13711-242">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="13711-242">This cmdlet does not generate output.</span></span>

## <span data-ttu-id="13711-243">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="13711-243">NOTES</span></span>

## <span data-ttu-id="13711-244">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="13711-244">RELATED LINKS</span></span>

[<span data-ttu-id="13711-245">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="13711-245">Get-WmiObject</span></span>](Get-WmiObject.md)

[<span data-ttu-id="13711-246">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="13711-246">Invoke-WmiMethod</span></span>](Invoke-WmiMethod.md)

[<span data-ttu-id="13711-247">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="13711-247">Remove-WmiObject</span></span>](Remove-WmiObject.md)
