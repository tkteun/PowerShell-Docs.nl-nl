---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmaninstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManInstance
ms.openlocfilehash: 8eeb050b67d25f428612f42bfec253a78907cce6
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251580"
---
# <span data-ttu-id="3e24e-103">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="3e24e-103">Get-WSManInstance</span></span>

## <span data-ttu-id="3e24e-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3e24e-104">SYNOPSIS</span></span>
<span data-ttu-id="3e24e-105">Geeft beheer gegevens weer voor een resource-exemplaar dat is opgegeven door een resource-URI.</span><span class="sxs-lookup"><span data-stu-id="3e24e-105">Displays management information for a resource instance specified by a Resource URI.</span></span>

## <span data-ttu-id="3e24e-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3e24e-106">SYNTAX</span></span>

### <span data-ttu-id="3e24e-107">GetInstance (standaard)</span><span class="sxs-lookup"><span data-stu-id="3e24e-107">GetInstance (Default)</span></span>

```
Get-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-ConnectionURI <Uri>] [-Dialect <Uri>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet <Hashtable>]
 [-SessionOption <SessionOption>] [-UseSSL] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="3e24e-108">Opsommen</span><span class="sxs-lookup"><span data-stu-id="3e24e-108">Enumerate</span></span>

```
Get-WSManInstance [-ApplicationName <String>] [-BasePropertiesOnly] [-ComputerName <String>]
 [-ConnectionURI <Uri>] [-Dialect <Uri>] [-Enumerate] [-Filter <String>] [-OptionSet <Hashtable>]
 [-Port <Int32>] [-Associations] [-ResourceURI] <Uri> [-ReturnType <String>] [-SessionOption <SessionOption>]
 [-Shallow] [-UseSSL] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="3e24e-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3e24e-109">DESCRIPTION</span></span>
<span data-ttu-id="3e24e-110">De cmdlet **Get-WSManInstance** haalt een exemplaar van een beheer bron op die is opgegeven door een URI (Uniform Resource Identifier) van een resource.</span><span class="sxs-lookup"><span data-stu-id="3e24e-110">The **Get-WSManInstance** cmdlet retrieves an instance of a management resource that is specified by a resource Uniform Resource Identifier (URI).</span></span>
<span data-ttu-id="3e24e-111">De gegevens die worden opgehaald, kunnen een complexe XML-gegevensset zijn, een object of een eenvoudige waarde.</span><span class="sxs-lookup"><span data-stu-id="3e24e-111">The information that is retrieved can be a complex XML information set, which is an object, or a simple value.</span></span>
<span data-ttu-id="3e24e-112">Deze cmdlet komt overeen met de standaard **Get** -opdracht webservices voor beheer (WS-Management).</span><span class="sxs-lookup"><span data-stu-id="3e24e-112">This cmdlet is the equivalent to the standard Web Services for Management (WS-Management) **Get** command.</span></span>

<span data-ttu-id="3e24e-113">Met deze cmdlet wordt de WS-Management Connection/Trans Port-laag gebruikt om informatie op te halen.</span><span class="sxs-lookup"><span data-stu-id="3e24e-113">This cmdlet uses the WS-Management connection/transport layer to retrieve information.</span></span>

## <span data-ttu-id="3e24e-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3e24e-114">EXAMPLES</span></span>

### <span data-ttu-id="3e24e-115">Voor beeld 1: alle gegevens ophalen van WMI</span><span class="sxs-lookup"><span data-stu-id="3e24e-115">Example 1: Get all information from WMI</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI wmicimv2/win32_service -SelectorSet @{name="winrm"} -ComputerName "Server01"
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : true
Caption                 : Windows Remote Management (WS-Management)
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Windows Remote Management (WinRM) service implements the WS-Management protocol for remote
management. WS-Management is a standard web services protocol used for remote software and
hardware management. The WinRM service listens on the network for WS-Management requests
and processes them. The WinRM Service needs to be configured with a listener using the
winrm.cmd command line tool or through Group Policy in order for it to listen over the
network. The WinRM service provides access to WMI data and enables event collection. Event
collection and subscription to events require that the service is running. WinRM messages
use HTTP and HTTPS as transports. The WinRM service does not depend on IIS but is
preconfigured to share a port with IIS on the same computer.  The WinRM service reserves the
/wsman URL prefix. To prevent conflicts with IIS, administrators should ensure that any
websites hosted on IIS do not use the /wsman URL prefix.
DesktopInteract         : false
DisplayName             : Windows Remote Management (WS-Management)
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : winrm
PathName                : C:\Windows\System32\svchost.exe -k NetworkService
ProcessId               : 948
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : true
StartMode               : Auto
StartName               : NT AUTHORITY\NetworkService
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
WaitHint                : 0
```

<span data-ttu-id="3e24e-116">Deze opdracht retourneert alle informatie die Windows Management Instrumentation (WMI) over de **WinRM** -service op de externe Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="3e24e-116">This command returns all of the information that Windows Management Instrumentation (WMI) exposes about the **WinRM** service on the remote server01 computer.</span></span>

### <span data-ttu-id="3e24e-117">Voor beeld 2: de status van de Spooler-service ophalen</span><span class="sxs-lookup"><span data-stu-id="3e24e-117">Example 2: Get the status of the Spooler service</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI wmicimv2/win32_service -SelectorSet @{name="spooler"} -Fragment Status -ComputerName "Server01"
XmlFragment=OK
```

<span data-ttu-id="3e24e-118">Met deze opdracht wordt alleen de status van de **spooler** -service op de externe Server01-computer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3e24e-118">This command returns only the status of the **Spooler** service on the remote server01 computer.</span></span>

### <span data-ttu-id="3e24e-119">Voor beeld 3: eindpunt verwijzingen ophalen voor alle services</span><span class="sxs-lookup"><span data-stu-id="3e24e-119">Example 3: Get endpoint references for all services</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -ResourceURI wmicimv2/win32_service -ReturnType EPR
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Visual Studio 2008 Remote Debugger
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Allows members of the Administrators group to remotely debug server applications using Visual
Studio 2008. Use the Visual Studio 2008 Remote Debugging Configuration Wizard to enable this
service.
DesktopInteract         : false
DisplayName             : Visual Studio 2008 Remote Debugger
ErrorControl            : Ignore
ExitCode                : 1077
InstallDate             : InstallDate
Name                    : msvsmon90
PathName                : "C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe" /service msvsmon90
ProcessId               : 0
ServiceSpecificExitCode : 0
ServiceType             : Own Process
Started                 : false
StartMode               : Disabled
StartName               : LocalSystem
State                   : Stopped
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : COMPUTER01
TagId                   : 0
WaitHint                : 0
...
```

<span data-ttu-id="3e24e-120">Met deze opdracht worden eindpunt verwijzingen geretourneerd die overeenkomen met alle services op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3e24e-120">This command returns endpoint references that correspond to all the services on the local computer.</span></span>

### <span data-ttu-id="3e24e-121">Voor beeld 4: services ophalen die voldoen aan opgegeven criteria</span><span class="sxs-lookup"><span data-stu-id="3e24e-121">Example 4: Get services that meet specified criteria</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -ResourceURI wmicimv2/* -Filter "select * from win32_service where StartMode = 'Auto' and State = 'Stopped'" -ComputerName "Server01"
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Windows Media Center Service Launcher
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Starts Windows Media Center Scheduler and Windows Media Center Receiver services
at startup if TV is enabled within Windows Media Center.
DesktopInteract         : false
DisplayName             : Windows Media Center Service Launcher
ErrorControl            : Ignore
ExitCode                : 0
InstallDate             : InstallDate
Name                    : ehstart
PathName                : C:\Windows\system32\svchost.exe -k LocalServiceNoNetwork
ProcessId               : 0
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : false
StartMode               : Auto
StartName               : NT AUTHORITY\LocalService
State                   : Stopped
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : Server01
TagId                   : 0
WaitHint                : 0
...
```

<span data-ttu-id="3e24e-122">Met deze opdracht worden alle services weer gegeven die voldoen aan de volgende criteria op de externe Server01-computer:</span><span class="sxs-lookup"><span data-stu-id="3e24e-122">This command lists all of the services that meet the following criteria on the remote Server01 computer:</span></span>

- <span data-ttu-id="3e24e-123">Het opstart type van de service wordt automatisch.</span><span class="sxs-lookup"><span data-stu-id="3e24e-123">The startup type of the service is Automatic.</span></span>
- <span data-ttu-id="3e24e-124">De service is gestopt.</span><span class="sxs-lookup"><span data-stu-id="3e24e-124">The service is stopped.</span></span>

### <span data-ttu-id="3e24e-125">Voor beeld 5: listener-configuratie ophalen die overeenkomt met de criteria op de lokale computer</span><span class="sxs-lookup"><span data-stu-id="3e24e-125">Example 5: Get listener configuration that matches criteria on the local computer</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{Address="*";Transport="http"}
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 80
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {100.0.0.1, 123.123.123.123, ::1, 2001:4898:0:fff:0:5efe:123.123.123.123...}
```

<span data-ttu-id="3e24e-126">Met deze opdracht wordt de WS-Management listener-configuratie op de lokale computer weer gegeven voor de listener die overeenkomt met de criteria in de selector-set.</span><span class="sxs-lookup"><span data-stu-id="3e24e-126">This command lists the WS-Management listener configuration on the local computer for the listener that matches the criteria in the selector set.</span></span>

### <span data-ttu-id="3e24e-127">Voor beeld 6: listener-configuratie ophalen die overeenkomt met de criteria op een externe computer</span><span class="sxs-lookup"><span data-stu-id="3e24e-127">Example 6: Get listener configuration that matches criteria on a remote computer</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{Address="*";Transport="http"} -ComputerName "Server01"
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 80
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {100.0.0.1, 123.123.123.124, ::1, 2001:4898:0:fff:0:5efe:123.123.123.124...}
```

<span data-ttu-id="3e24e-128">Met deze opdracht wordt de WS-Management listener-configuratie op de externe Server01-computer weer gegeven voor de listener die overeenkomt met de criteria in de selector-set.</span><span class="sxs-lookup"><span data-stu-id="3e24e-128">This command lists the WS-Management listener configuration on the remote server01 computer for the listener that matches the criteria in the selector set.</span></span>

### <span data-ttu-id="3e24e-129">Voor beeld 7: gekoppelde instanties ophalen die zijn gerelateerd aan een opgegeven exemplaar</span><span class="sxs-lookup"><span data-stu-id="3e24e-129">Example 7: Get associated instances related to a specified instance</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -Dialect Association -Filter "{Object=win32_service?name=winrm}" -ResourceURI wmicimv2/*
xsi                       : http://www.w3.org/2001/XMLSchema-instance
p                         : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_ComputerSystem
cim                       : http://schemas.dmtf.org/wbem/wscim/1/common
type                      : p:Win32_ComputerSystem_Type
lang                      : en-US
AdminPasswordStatus       : 1
AutomaticManagedPagefile  : true
AutomaticResetBootOption  : true
AutomaticResetCapability  : true
BootOptionOnLimit         : BootOptionOnLimit
BootOptionOnWatchDog      : BootOptionOnWatchDog
BootROMSupported          : true
BootupState               : Normal boot
Caption                   : SERVER01
ChassisBootupState        : 3
CreationClassName         : Win32_ComputerSystem
CurrentTimeZone           : -480
DaylightInEffect          : false
Description               : AT/AT COMPATIBLE
DNSHostName               : server01
Domain                    : site01.corp.fabrikam.com
DomainRole                : 1
EnableDaylightSavingsTime : true
FrontPanelResetStatus     : 2
InfraredSupported         : false
InstallDate               : InstallDate
KeyboardPasswordStatus    : 2
LastLoadInfo              : LastLoadInfo
Manufacturer              : Dell Inc.
Model                     : OptiPlex 745
Name                      : SERVER01
NameFormat                : NameFormat
NetworkServerModeEnabled  : true
NumberOfLogicalProcessors : 2
NumberOfProcessors        : 1
OEMStringArray            : www.dell.com
PartOfDomain              : true
PauseAfterReset           : -1
PCSystemType              : 5
PowerManagementSupported  : PowerManagementSupported
PowerOnPasswordStatus     : 1
PowerState                : 0
PowerSupplyState          : 3
PrimaryOwnerContact       : PrimaryOwnerContact
PrimaryOwnerName          : testuser01
ResetCapability           : 1
ResetCount                : -1
ResetLimit                : -1
Roles                     : {LM_Workstation, LM_Server, SQLServer, NT}
Status                    : OK
SystemStartupDelay        : SystemStartupDelay
SystemStartupSetting      : SystemStartupSetting
SystemType                : X86-based PC
ThermalState              : 3
TotalPhysicalMemory       : 3217760256
UserName                  : FABRIKAM\testuser01
WakeUpType                : 6
Workgroup                 : Workgroup
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Remote Procedure Call (RPC)
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Serves as the endpoint mapper and COM Service Control Manager. If this service is stopped
or disabled, programs using COM or Remote Procedure Call (RPC) services will not function
properly.
DesktopInteract         : false
DisplayName             : Remote Procedure Call (RPC)
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : RpcSs
PathName                : C:\Windows\system32\svchost.exe -k rpcss
ProcessId               : 1100
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : true
StartMode               : Auto
StartName               : NT AUTHORITY\NetworkService
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
WaitHint                : 0

xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_SystemDriver
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_SystemDriver_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : true
Caption                 : HTTP
CreationClassName       : Win32_SystemDriver
Description             : HTTP
DesktopInteract         : false
DisplayName             : HTTP
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : HTTP
PathName                : C:\Windows\system32\drivers\HTTP.sys
ServiceSpecificExitCode : 0
ServiceType             : Kernel Driver
Started                 : true
StartMode               : Manual
StartName               :
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
```

<span data-ttu-id="3e24e-130">Met deze opdracht worden de gekoppelde exemplaren opgehaald die zijn gerelateerd aan het opgegeven exemplaar (WinRM).</span><span class="sxs-lookup"><span data-stu-id="3e24e-130">This command gets the associated instances that are related to the specified instance (winrm).</span></span>

<span data-ttu-id="3e24e-131">U moet het filter tussen dubbele aanhalings tekens plaatsen, zoals wordt weer gegeven in het voor beeld.</span><span class="sxs-lookup"><span data-stu-id="3e24e-131">You must enclose the filter in quotation marks, as shown in the example.</span></span>

### <span data-ttu-id="3e24e-132">Voor beeld 8: koppelings instanties die zijn gerelateerd aan een opgegeven exemplaar ophalen</span><span class="sxs-lookup"><span data-stu-id="3e24e-132">Example 8: Get association instances related to a specified instance</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -Dialect Association -Associations -Filter "{Object=win32_service?name=winrm}" -ResourceURI wmicimv2/*
```

<span data-ttu-id="3e24e-133">Met deze opdracht worden koppelings instanties opgehaald die zijn gerelateerd aan het opgegeven exemplaar (WinRM).</span><span class="sxs-lookup"><span data-stu-id="3e24e-133">This command gets association instances that are related to the specified instance (winrm).</span></span>
<span data-ttu-id="3e24e-134">Omdat de *dialect* waarde Association is en de para meter *Associations* wordt gebruikt, retourneert deze opdracht koppelings instanties, niet-gekoppelde exemplaren.</span><span class="sxs-lookup"><span data-stu-id="3e24e-134">Because the *Dialect* value is association and the *Associations* parameter is used, this command returns association instances, not associated instances.</span></span>

<span data-ttu-id="3e24e-135">U moet het filter tussen dubbele aanhalings tekens plaatsen, zoals wordt weer gegeven in het voor beeld.</span><span class="sxs-lookup"><span data-stu-id="3e24e-135">You must enclose the filter in quotation marks, as shown in the example.</span></span>

## <span data-ttu-id="3e24e-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3e24e-136">PARAMETERS</span></span>

### <span data-ttu-id="3e24e-137">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="3e24e-137">-ApplicationName</span></span>
<span data-ttu-id="3e24e-138">Hiermee geeft u de naam van de toepassing in de verbinding.</span><span class="sxs-lookup"><span data-stu-id="3e24e-138">Specifies the application name in the connection.</span></span>
<span data-ttu-id="3e24e-139">De standaard waarde van de para meter *ApplicationName* is WSMAN.</span><span class="sxs-lookup"><span data-stu-id="3e24e-139">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="3e24e-140">De volledige id voor het externe eind punt heeft de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="3e24e-140">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="3e24e-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="3e24e-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="3e24e-142">Bijvoorbeeld: `http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="3e24e-142">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="3e24e-143">Internet Information Services (IIS), die als host fungeert voor de sessie, stuurt aanvragen door met dit eind punt naar de opgegeven toepassing.</span><span class="sxs-lookup"><span data-stu-id="3e24e-143">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="3e24e-144">Deze standaard instelling van WSMAN is geschikt voor de meeste toepassingen.</span><span class="sxs-lookup"><span data-stu-id="3e24e-144">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="3e24e-145">Deze para meter is ontworpen om te worden gebruikt als veel computers externe verbindingen tot stand brengen met één computer waarop Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3e24e-145">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="3e24e-146">In dit geval fungeert IIS als host WS-Management voor efficiëntie.</span><span class="sxs-lookup"><span data-stu-id="3e24e-146">In this case, IIS hosts WS-Management for efficiency.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-147">-Koppelingen</span><span class="sxs-lookup"><span data-stu-id="3e24e-147">-Associations</span></span>
<span data-ttu-id="3e24e-148">Geeft aan dat deze cmdlet koppelings instanties, niet-gekoppelde exemplaren, ontvangt.</span><span class="sxs-lookup"><span data-stu-id="3e24e-148">Indicates that this cmdlet gets association instances, not associated instances.</span></span>
<span data-ttu-id="3e24e-149">U kunt deze para meter alleen gebruiken als de *dialect* parameter de waarde Association heeft.</span><span class="sxs-lookup"><span data-stu-id="3e24e-149">You can use this parameter only when the *Dialect* parameter has a value of Association.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-150">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="3e24e-150">-Authentication</span></span>
<span data-ttu-id="3e24e-151">Hiermee geeft u het verificatie mechanisme op dat moet worden gebruikt op de server.</span><span class="sxs-lookup"><span data-stu-id="3e24e-151">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="3e24e-152">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="3e24e-152">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3e24e-153">Hoofd.</span><span class="sxs-lookup"><span data-stu-id="3e24e-153">Basic.</span></span>
<span data-ttu-id="3e24e-154">Basic is een schema waarin de gebruikers naam en het wacht woord als niet-gecodeerde tekst naar de server of proxy worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="3e24e-154">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="3e24e-155">Standaard.</span><span class="sxs-lookup"><span data-stu-id="3e24e-155">Default.</span></span>
<span data-ttu-id="3e24e-156">Gebruik de verificatie methode die wordt geïmplementeerd door het WS-Management-protocol.</span><span class="sxs-lookup"><span data-stu-id="3e24e-156">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="3e24e-157">Dit is de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="3e24e-157">This is the default.</span></span>
- <span data-ttu-id="3e24e-158">Vatting.</span><span class="sxs-lookup"><span data-stu-id="3e24e-158">Digest.</span></span>
<span data-ttu-id="3e24e-159">Digest is een vraag/antwoord-schema dat gebruikmaakt van een door de server opgegeven gegevens reeks voor de uitdaging.</span><span class="sxs-lookup"><span data-stu-id="3e24e-159">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="3e24e-160">Kerberos.</span><span class="sxs-lookup"><span data-stu-id="3e24e-160">Kerberos.</span></span>
<span data-ttu-id="3e24e-161">De client computer en de server worden wederzijds geverifieerd met behulp van Kerberos-certificaten.</span><span class="sxs-lookup"><span data-stu-id="3e24e-161">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="3e24e-162">Afspraken.</span><span class="sxs-lookup"><span data-stu-id="3e24e-162">Negotiate.</span></span>
<span data-ttu-id="3e24e-163">Onderhandelen is een vraag/antwoord-schema waarmee wordt onderhandeld over de server of proxy om te bepalen welk schema moet worden gebruikt voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="3e24e-163">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="3e24e-164">Met deze parameter waarde kan bijvoorbeeld worden geonderhandelingd om te bepalen of het Kerberos-protocol of NTLM wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3e24e-164">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="3e24e-165">CredSSP.</span><span class="sxs-lookup"><span data-stu-id="3e24e-165">CredSSP.</span></span>
<span data-ttu-id="3e24e-166">Gebruik CredSSP-verificatie (Credential Security Support Provider) waarmee de gebruiker referenties kan delegeren.</span><span class="sxs-lookup"><span data-stu-id="3e24e-166">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="3e24e-167">Deze optie is bedoeld voor opdrachten die op één externe computer worden uitgevoerd, maar die gegevens verzamelen van of extra opdrachten op andere externe computers worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3e24e-167">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="3e24e-168">Let op: CredSSP delegeert de gebruikers referenties van de lokale computer naar een externe computer.</span><span class="sxs-lookup"><span data-stu-id="3e24e-168">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="3e24e-169">Deze procedure verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="3e24e-169">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="3e24e-170">Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="3e24e-170">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am
Accepted values: None, Default, Digest, Negotiate, Basic, Kerberos, ClientCertificate, Credssp

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-171">-BasePropertiesOnly</span><span class="sxs-lookup"><span data-stu-id="3e24e-171">-BasePropertiesOnly</span></span>
<span data-ttu-id="3e24e-172">Geeft aan dat met deze cmdlet alleen de eigenschappen worden opgesomd die deel uitmaken van de basis klasse die is opgegeven door de para meter *ResourceURI* .</span><span class="sxs-lookup"><span data-stu-id="3e24e-172">Indicates that this cmdlet enumerates only the properties that are part of the base class that is specified by the *ResourceURI* parameter.</span></span>
<span data-ttu-id="3e24e-173">Deze para meter heeft geen effect als de meest *recente* para meter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3e24e-173">This parameter has no effect if the *Shallow* parameter is specified.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases: UBPO, Base

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-174">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="3e24e-174">-CertificateThumbprint</span></span>
<span data-ttu-id="3e24e-175">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="3e24e-175">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="3e24e-176">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="3e24e-176">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="3e24e-177">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="3e24e-177">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="3e24e-178">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="3e24e-178">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="3e24e-179">Als u een certificaat vingerafdruk wilt krijgen, gebruikt u de opdracht Get-Item of Get-ChildItem in het Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="3e24e-179">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-180">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="3e24e-180">-ComputerName</span></span>
<span data-ttu-id="3e24e-181">Hiermee geeft u de computer op waarop de beheer bewerking moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3e24e-181">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="3e24e-182">De waarde kan een Fully Qualified Domain Name, een NetBIOS-naam of een IP-adres zijn.</span><span class="sxs-lookup"><span data-stu-id="3e24e-182">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="3e24e-183">Gebruik de naam van de lokale computer, gebruik localhost of gebruik een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="3e24e-183">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="3e24e-184">De lokale computer is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="3e24e-184">The local computer is the default.</span></span>
<span data-ttu-id="3e24e-185">Wanneer de externe computer zich in een ander domein van de gebruiker bevindt, moet u een Fully Qualified Domain Name gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3e24e-185">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="3e24e-186">U kunt een waarde voor deze para meter door geven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3e24e-186">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-187">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="3e24e-187">-ConnectionURI</span></span>
<span data-ttu-id="3e24e-188">Hiermee geeft u het eind punt van de verbinding.</span><span class="sxs-lookup"><span data-stu-id="3e24e-188">Specifies the connection endpoint.</span></span>
<span data-ttu-id="3e24e-189">De indeling van deze teken reeks is als volgt:</span><span class="sxs-lookup"><span data-stu-id="3e24e-189">The format of this string is as follows:</span></span>

<span data-ttu-id="3e24e-190">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="3e24e-190">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="3e24e-191">De volgende teken reeks is een correct ingedeelde waarde voor deze para meter:</span><span class="sxs-lookup"><span data-stu-id="3e24e-191">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="3e24e-192">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="3e24e-192">The URI must be fully qualified.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: CURI, CU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-193">-Credential</span><span class="sxs-lookup"><span data-stu-id="3e24e-193">-Credential</span></span>
<span data-ttu-id="3e24e-194">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="3e24e-194">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="3e24e-195">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="3e24e-195">The default is the current user.</span></span>
<span data-ttu-id="3e24e-196">Typ een gebruikers naam, zoals gebruiker01, Domain01\User01 of User@Domain.com .</span><span class="sxs-lookup"><span data-stu-id="3e24e-196">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="3e24e-197">U kunt ook een **PSCredential** -object invoeren, zoals het dat wordt geretourneerd door de cmdlet Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="3e24e-197">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="3e24e-198">Wanneer u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="3e24e-198">When you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases: cred, c

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-199">-Dialect</span><span class="sxs-lookup"><span data-stu-id="3e24e-199">-Dialect</span></span>
<span data-ttu-id="3e24e-200">Hiermee geeft u het dialect op dat moet worden gebruikt in het filter predicaat.</span><span class="sxs-lookup"><span data-stu-id="3e24e-200">Specifies the dialect to use in the filter predicate.</span></span>
<span data-ttu-id="3e24e-201">Dit kan elk dialect zijn dat wordt ondersteund door de externe service.</span><span class="sxs-lookup"><span data-stu-id="3e24e-201">This can be any dialect that is supported by the remote service.</span></span>
<span data-ttu-id="3e24e-202">De volgende aliassen kunnen worden gebruikt voor de dialect-URI:</span><span class="sxs-lookup"><span data-stu-id="3e24e-202">The following aliases can be used for the dialect URI:</span></span>

- <span data-ttu-id="3e24e-203">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span><span class="sxs-lookup"><span data-stu-id="3e24e-203">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span></span>
- <span data-ttu-id="3e24e-204">Selector `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span><span class="sxs-lookup"><span data-stu-id="3e24e-204">Selector `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span></span>
- <span data-ttu-id="3e24e-205">Organisatie `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span><span class="sxs-lookup"><span data-stu-id="3e24e-205">Association `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-206">-Opsommen</span><span class="sxs-lookup"><span data-stu-id="3e24e-206">-Enumerate</span></span>
<span data-ttu-id="3e24e-207">Geeft aan dat met deze cmdlet alle exemplaren van een beheer bron worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3e24e-207">Indicates that this cmdlet returns all of the instances of a management resource.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-208">-Filter</span><span class="sxs-lookup"><span data-stu-id="3e24e-208">-Filter</span></span>
<span data-ttu-id="3e24e-209">Hiermee geeft u de filter expressie voor de opsomming op.</span><span class="sxs-lookup"><span data-stu-id="3e24e-209">Specifies the filter expression for the enumeration.</span></span>
<span data-ttu-id="3e24e-210">Als u deze para meter opgeeft, moet u ook *dialect* opgeven.</span><span class="sxs-lookup"><span data-stu-id="3e24e-210">If you specify this parameter, you must also specify *Dialect*.</span></span>

<span data-ttu-id="3e24e-211">De geldige waarden van deze para meter zijn afhankelijk van het dialect dat is opgegeven in *dialect*.</span><span class="sxs-lookup"><span data-stu-id="3e24e-211">The valid values of this parameter depend on the dialect that is specified in *Dialect*.</span></span>
<span data-ttu-id="3e24e-212">Als *dialect* bijvoorbeeld WQL is, moet de *filter* parameter een teken reeks bevatten en moet de teken reeks een geldige WQL-query bevatten, zoals de volgende query:</span><span class="sxs-lookup"><span data-stu-id="3e24e-212">For example, if *Dialect* is WQL, the *Filter* parameter must contain a string, and the string must contain a valid WQL query such as the following query:</span></span>

`"Select * from Win32_Service where State != Running"`

<span data-ttu-id="3e24e-213">Als *dialect* is gekoppeld, moet het *filter* een teken reeks bevatten en moet de teken reeks een geldig filter bevatten, bijvoorbeeld het volgende filter:</span><span class="sxs-lookup"><span data-stu-id="3e24e-213">If *Dialect* is Association, *Filter* must contain a string, and the string must contain a valid filter, such as the following filter:</span></span>

`-filter:Object=EPR\[;AssociationClassName=AssocClassName\]\[;ResultClassName=ClassName\]\[;Role=RefPropertyName\]\[;ResultRole=RefPropertyName\]}`

```yaml
Type: System.String
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-214">-Fragment</span><span class="sxs-lookup"><span data-stu-id="3e24e-214">-Fragment</span></span>
<span data-ttu-id="3e24e-215">Hiermee geeft u een sectie in het exemplaar op dat moet worden bijgewerkt of opgehaald voor de opgegeven bewerking.</span><span class="sxs-lookup"><span data-stu-id="3e24e-215">Specifies a section inside the instance that is to be updated or retrieved for the specified operation.</span></span>
<span data-ttu-id="3e24e-216">Als u bijvoorbeeld de status van een Spooler-service wilt ophalen, geeft u het volgende op:</span><span class="sxs-lookup"><span data-stu-id="3e24e-216">For example, to get the status of a spooler service, specify the following:</span></span>

`-Fragment Status`

```yaml
Type: System.String
Parameter Sets: GetInstance
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-217">-Optieset</span><span class="sxs-lookup"><span data-stu-id="3e24e-217">-OptionSet</span></span>
<span data-ttu-id="3e24e-218">Hiermee geeft u een set switches naar een service op om de aard van de aanvraag te wijzigen of te verfijnen.</span><span class="sxs-lookup"><span data-stu-id="3e24e-218">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="3e24e-219">Deze lijken op de Schakel opties die worden gebruikt in opdracht regel shells, omdat deze service-specifiek zijn.</span><span class="sxs-lookup"><span data-stu-id="3e24e-219">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="3e24e-220">U kunt een wille keurig aantal opties opgeven.</span><span class="sxs-lookup"><span data-stu-id="3e24e-220">Any number of options can be specified.</span></span>

<span data-ttu-id="3e24e-221">In het volgende voor beeld ziet u de syntaxis waarmee de waarden 1, 2 en 3 worden door gegeven voor de para meters a, b en c:</span><span class="sxs-lookup"><span data-stu-id="3e24e-221">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: OS

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-222">-Port</span><span class="sxs-lookup"><span data-stu-id="3e24e-222">-Port</span></span>
<span data-ttu-id="3e24e-223">Hiermee geeft u de poort op die moet worden gebruikt wanneer de client verbinding maakt met de WinRM-service.</span><span class="sxs-lookup"><span data-stu-id="3e24e-223">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="3e24e-224">Wanneer het Trans Port HTTP is, is de standaard poort 80.</span><span class="sxs-lookup"><span data-stu-id="3e24e-224">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="3e24e-225">Wanneer het Trans Port HTTPS is, is de standaard poort 443.</span><span class="sxs-lookup"><span data-stu-id="3e24e-225">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="3e24e-226">Wanneer u HTTPS gebruikt als het Trans Port, moet de waarde van de para meter *ComputerName* overeenkomen met de common name (CN) van het server certificaat.</span><span class="sxs-lookup"><span data-stu-id="3e24e-226">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="3e24e-227">Als de para meter *SkipCNCheck* echter is opgegeven als onderdeel van de *SessionOption* -para meter, moet de algemene naam van het certificaat van de server niet overeenkomen met de hostnaam van de server.</span><span class="sxs-lookup"><span data-stu-id="3e24e-227">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="3e24e-228">De para meter *SkipCNCheck* moet alleen worden gebruikt voor vertrouwde computers.</span><span class="sxs-lookup"><span data-stu-id="3e24e-228">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="3e24e-229">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="3e24e-229">-ResourceURI</span></span>
<span data-ttu-id="3e24e-230">Hiermee geeft u de URI van de resource klasse of het exemplaar.</span><span class="sxs-lookup"><span data-stu-id="3e24e-230">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="3e24e-231">De URI identificeert een specifiek type bron, zoals schijven of processen, op een computer.</span><span class="sxs-lookup"><span data-stu-id="3e24e-231">The URI identifies a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="3e24e-232">Een URI bestaat uit een voor voegsel en een pad van een resource.</span><span class="sxs-lookup"><span data-stu-id="3e24e-232">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="3e24e-233">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="3e24e-233">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: RURI

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-234">-Return type</span><span class="sxs-lookup"><span data-stu-id="3e24e-234">-ReturnType</span></span>
<span data-ttu-id="3e24e-235">Hiermee geeft u het type gegevens dat moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3e24e-235">Specifies the type of data to be returned.</span></span>
<span data-ttu-id="3e24e-236">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="3e24e-236">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3e24e-237">Object</span><span class="sxs-lookup"><span data-stu-id="3e24e-237">Object</span></span>
- <span data-ttu-id="3e24e-238">EPR</span><span class="sxs-lookup"><span data-stu-id="3e24e-238">EPR</span></span>
- <span data-ttu-id="3e24e-239">ObjectAndEPR</span><span class="sxs-lookup"><span data-stu-id="3e24e-239">ObjectAndEPR</span></span>

<span data-ttu-id="3e24e-240">De standaard waarde is object.</span><span class="sxs-lookup"><span data-stu-id="3e24e-240">The default value is Object.</span></span>

<span data-ttu-id="3e24e-241">Als u object opgeeft of als u deze para meter niet opgeeft, retourneert deze cmdlet alleen objecten.</span><span class="sxs-lookup"><span data-stu-id="3e24e-241">If you specify Object or do not specify this parameter, this cmdlet returns only objects.</span></span>
<span data-ttu-id="3e24e-242">Als u een eindpunt referentie opgeeft (EPR), retourneert deze cmdlet alleen de eindpunt verwijzingen van de objecten.</span><span class="sxs-lookup"><span data-stu-id="3e24e-242">If you specify endpoint reference (EPR) this cmdlet returns only the endpoint references of the objects.</span></span>
<span data-ttu-id="3e24e-243">Eindpunt verwijzingen bevatten informatie over de resource-URI en de selecters voor het exemplaar.</span><span class="sxs-lookup"><span data-stu-id="3e24e-243">Endpoint references contain information about the resource URI and the selectors for the instance.</span></span>
<span data-ttu-id="3e24e-244">Als u ObjectAndEPR opgeeft, retourneert deze cmdlet zowel het object als de bijbehorende eindpunt verwijzingen.</span><span class="sxs-lookup"><span data-stu-id="3e24e-244">If you specify ObjectAndEPR, this cmdlet returns both the object and its associated endpoint references.</span></span>

```yaml
Type: System.String
Parameter Sets: Enumerate
Aliases: RT
Accepted values: object, epr, objectandepr

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-245">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="3e24e-245">-SelectorSet</span></span>
<span data-ttu-id="3e24e-246">Hiermee geeft u een set waardeparen op die worden gebruikt om bepaalde beheer resource-instanties te selecteren.</span><span class="sxs-lookup"><span data-stu-id="3e24e-246">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="3e24e-247">De para meter *SelectorSet* wordt gebruikt wanneer er meer dan één exemplaar van de bron bestaat.</span><span class="sxs-lookup"><span data-stu-id="3e24e-247">The *SelectorSet* parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="3e24e-248">De waarde van de para meter *SelectorSet* moet een hash-tabel zijn.</span><span class="sxs-lookup"><span data-stu-id="3e24e-248">The value of the *SelectorSet* parameter must be a hash table.</span></span>

<span data-ttu-id="3e24e-249">In het volgende voor beeld ziet u hoe u een waarde voor deze para meter opgeeft:</span><span class="sxs-lookup"><span data-stu-id="3e24e-249">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: GetInstance
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-250">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="3e24e-250">-SessionOption</span></span>
<span data-ttu-id="3e24e-251">Hiermee worden uitgebreide opties voor de WS-Management-sessie opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3e24e-251">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="3e24e-252">Voer een **SessionOption** -object in dat u maakt met behulp van de cmdlet New-WSManSessionOption.</span><span class="sxs-lookup"><span data-stu-id="3e24e-252">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="3e24e-253">Typ voor meer informatie over de beschik bare opties `Get-Help New-WSManSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="3e24e-253">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

```yaml
Type: Microsoft.WSMan.Management.SessionOption
Parameter Sets: (All)
Aliases: SO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-254">-Recente</span><span class="sxs-lookup"><span data-stu-id="3e24e-254">-Shallow</span></span>
<span data-ttu-id="3e24e-255">Geeft aan dat deze cmdlet alleen exemplaren retourneert van de basis klasse die is opgegeven in de resource-URI.</span><span class="sxs-lookup"><span data-stu-id="3e24e-255">Indicates that this cmdlet returns only instances of the base class that is specified in the resource URI.</span></span>
<span data-ttu-id="3e24e-256">Als u deze para meter niet opgeeft, retourneert deze cmdlet instanties van de basis klasse die is opgegeven in de URI en in alle afgeleide klassen.</span><span class="sxs-lookup"><span data-stu-id="3e24e-256">If you do not specify this parameter,, this cmdlet returns instances of the base class that is specified in the URI and in all its derived classes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-257">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="3e24e-257">-UseSSL</span></span>
<span data-ttu-id="3e24e-258">Hiermee geeft u op dat het SSL-protocol (Secure Sockets Layer) wordt gebruikt om verbinding te maken met de externe computer.</span><span class="sxs-lookup"><span data-stu-id="3e24e-258">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="3e24e-259">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3e24e-259">By default, SSL is not used.</span></span>

<span data-ttu-id="3e24e-260">WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="3e24e-260">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="3e24e-261">Met de para meter *UseSSL* kunt u de extra beveiliging van https in plaats van http opgeven.</span><span class="sxs-lookup"><span data-stu-id="3e24e-261">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="3e24e-262">Als SSL niet beschikbaar is op de poort die voor de verbinding wordt gebruikt en u deze para meter opgeeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="3e24e-262">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SSL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e24e-263">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3e24e-263">CommonParameters</span></span>
<span data-ttu-id="3e24e-264">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3e24e-264">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3e24e-265">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3e24e-265">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3e24e-266">INVOER</span><span class="sxs-lookup"><span data-stu-id="3e24e-266">INPUTS</span></span>

### <span data-ttu-id="3e24e-267">Geen</span><span class="sxs-lookup"><span data-stu-id="3e24e-267">None</span></span>
<span data-ttu-id="3e24e-268">Deze opdracht accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="3e24e-268">This command does not accept any input.</span></span>

## <span data-ttu-id="3e24e-269">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3e24e-269">OUTPUTS</span></span>

### <span data-ttu-id="3e24e-270">System.Xml.Xml-element</span><span class="sxs-lookup"><span data-stu-id="3e24e-270">System.Xml.XmlElement</span></span>
<span data-ttu-id="3e24e-271">Met deze cmdlet wordt een **XMLElement** -object gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="3e24e-271">This cmdlet generates an **XMLElement** object.</span></span>

## <span data-ttu-id="3e24e-272">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3e24e-272">NOTES</span></span>

## <span data-ttu-id="3e24e-273">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3e24e-273">RELATED LINKS</span></span>

[<span data-ttu-id="3e24e-274">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="3e24e-274">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="3e24e-275">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="3e24e-275">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="3e24e-276">Verbinding verbreken-WSMan</span><span class="sxs-lookup"><span data-stu-id="3e24e-276">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="3e24e-277">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="3e24e-277">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="3e24e-278">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="3e24e-278">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="3e24e-279">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="3e24e-279">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="3e24e-280">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="3e24e-280">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="3e24e-281">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="3e24e-281">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="3e24e-282">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="3e24e-282">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="3e24e-283">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="3e24e-283">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="3e24e-284">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="3e24e-284">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="3e24e-285">Testen-WSMan</span><span class="sxs-lookup"><span data-stu-id="3e24e-285">Test-WSMan</span></span>](Test-WSMan.md)
