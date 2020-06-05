---
title: Externe communicatie van powershell
description: Er zijn veel verschillende manieren om opdrachten uit te voeren op externe computers in Power shell.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: ee83af41b53b254dd3dd993931333edac2f44f5a
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84436461"
---
# <a name="chapter-8---powershell-remoting"></a><span data-ttu-id="9e13c-103">Hoofd stuk 8-externe communicatie met Power shell</span><span class="sxs-lookup"><span data-stu-id="9e13c-103">Chapter 8 - PowerShell remoting</span></span>

<span data-ttu-id="9e13c-104">Power Shell heeft veel verschillende manieren om opdrachten uit te voeren op externe computers.</span><span class="sxs-lookup"><span data-stu-id="9e13c-104">PowerShell has many different ways to run commands against remote computers.</span></span> <span data-ttu-id="9e13c-105">In het laatste hoofd stuk hebt u gezien hoe u op afstand WMI kunt query's uitvoeren met behulp van de CIM-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="9e13c-105">In the last chapter, you saw how to remotely query WMI using the CIM cmdlets.</span></span> <span data-ttu-id="9e13c-106">Power shell bevat ook verschillende cmdlets die een ingebouwde **ComputerName** -para meter hebben.</span><span class="sxs-lookup"><span data-stu-id="9e13c-106">PowerShell also includes several cmdlets that have a built-in **ComputerName** parameter.</span></span>

<span data-ttu-id="9e13c-107">Zoals weer gegeven in het volgende voor beeld, `Get-Command` kan worden gebruikt met de **para meter parameter** waarde om te bepalen welke opdrachten een **ComputerName** -para meter hebben.</span><span class="sxs-lookup"><span data-stu-id="9e13c-107">As shown in the following example, `Get-Command` can be used with the **ParameterName** parameter to determine what commands have a **ComputerName** parameter.</span></span>

```powershell
Get-Command -ParameterName ComputerName
```

```Output
CommandType Name                        Version Source
----------- ----                        ------- ------
Cmdlet      Connect-PSSession           7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Connect-WSMan               7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Disconnect-WSMan            7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Enter-PSSession             7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Get-CimAssociatedInstance   7.0.0.0 CimCmdlets
Cmdlet      Get-CimClass                7.0.0.0 CimCmdlets
Cmdlet      Get-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      Get-CimSession              7.0.0.0 CimCmdlets
Cmdlet      Get-Counter                 7.0.0.0 Microsoft.PowerShell.Diagnostics
Cmdlet      Get-HotFix                  7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Get-PSSession               7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Get-WinEvent                7.0.0.0 Microsoft.PowerShell.Diagnostics
Cmdlet      Get-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Invoke-CimMethod            7.0.0.0 CimCmdlets
Cmdlet      Invoke-Command              7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Invoke-WSManAction          7.0.0.0 Microsoft.WSMan.Management
Cmdlet      New-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      New-CimSession              7.0.0.0 CimCmdlets
Cmdlet      New-PSSession               7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      New-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Receive-Job                 7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Receive-PSSession           7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Register-CimIndicationEvent 7.0.0.0 CimCmdlets
Cmdlet      Remove-CimInstance          7.0.0.0 CimCmdlets
Cmdlet      Remove-CimSession           7.0.0.0 CimCmdlets
Cmdlet      Remove-PSSession            7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Remove-WSManInstance        7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Rename-Computer             7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Restart-Computer            7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Send-MailMessage            7.0.0.0 Microsoft.PowerShell.Utility
Cmdlet      Set-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      Set-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Stop-Computer               7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Test-Connection             7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Test-WSMan                  7.0.0.0 Microsoft.WSMan.Management
```

<span data-ttu-id="9e13c-108">Opdrachten zoals `Get-Process` en `Get-Hotfix` hebben de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="9e13c-108">Commands such as `Get-Process` and `Get-Hotfix` have a **ComputerName** parameter.</span></span> <span data-ttu-id="9e13c-109">Dit is niet de lange termijn richting die micro soft kop voor het uitvoeren van opdrachten op externe computers.</span><span class="sxs-lookup"><span data-stu-id="9e13c-109">This isn't the long-term direction that Microsoft is heading for running commands against remote computers.</span></span> <span data-ttu-id="9e13c-110">Zelfs als u een opdracht met de para meter **ComputerName** vindt, is het waarschijnlijk dat u alternatieve referenties moet opgeven en geen **referentie** parameter heeft.</span><span class="sxs-lookup"><span data-stu-id="9e13c-110">Even if you find a command that has a **ComputerName** parameter, chances are that you'll need to specify alternate credentials and it won't have a **Credential** parameter.</span></span> <span data-ttu-id="9e13c-111">En als u hebt besloten Power shell uit te voeren vanuit een account met verhoogde bevoegdheden, kan de aanvraag door een firewall tussen u en de externe computer worden geblokkeerd.</span><span class="sxs-lookup"><span data-stu-id="9e13c-111">And if you decided to run PowerShell from an elevated account, a firewall between you and the remote computer can block the request.</span></span>

<span data-ttu-id="9e13c-112">Als u de Power shell-opdrachten voor externe communicatie wilt gebruiken die in dit hoofd stuk worden getoond, moet externe toegang tot Power shell zijn ingeschakeld op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="9e13c-112">To use the PowerShell remoting commands that are demonstrated in this chapter, PowerShell remoting must be enabled on the remote computer.</span></span> <span data-ttu-id="9e13c-113">Gebruik de `Enable-PSRemoting` cmdlet om externe communicatie van Power shell in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="9e13c-113">Use the `Enable-PSRemoting` cmdlet to enable PowerShell remoting.</span></span>

```powershell
Enable-PSRemoting
```

```Output
WinRM has been updated to receive requests.
WinRM service type changed successfully.
WinRM service started.

WinRM has been updated for remote management.
WinRM firewall exception enabled.
```

## <a name="one-to-one-remoting"></a><span data-ttu-id="9e13c-114">Een-op-een externe communicatie</span><span class="sxs-lookup"><span data-stu-id="9e13c-114">One-To-One Remoting</span></span>

<span data-ttu-id="9e13c-115">Als u de externe sessie interactief wilt maken, kunt u een-op-een-op-een-een-op-een-een-op-één</span><span class="sxs-lookup"><span data-stu-id="9e13c-115">If you want your remote session to be interactive, then one-to-one remoting is what you want.</span></span>
<span data-ttu-id="9e13c-116">Dit type externe toegang wordt via de cmdlet verschaft `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="9e13c-116">This type of remoting is provided via the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="9e13c-117">In het laatste hoofd stuk heb ik de referenties van mijn domein beheerder opgeslagen in een variabele met de naam `$Cred` .</span><span class="sxs-lookup"><span data-stu-id="9e13c-117">In the last chapter, I stored my domain admin credentials in a variable named `$Cred`.</span></span> <span data-ttu-id="9e13c-118">Als u dit nog niet hebt gedaan, gaat u naar de referenties van uw domein beheerder opslaan in de `$Cred` variabele.</span><span class="sxs-lookup"><span data-stu-id="9e13c-118">If you haven't already done so, go ahead and store your domain admin credentials in the `$Cred` variable.</span></span>

<span data-ttu-id="9e13c-119">Zo kunt u de referenties één keer invoeren en deze gebruiken op basis van elke opdracht, zolang uw huidige Power shell-sessie actief is.</span><span class="sxs-lookup"><span data-stu-id="9e13c-119">This allows you to enter the credentials once and use them on a per command basis as long as your current PowerShell session is active.</span></span>

```powershell
$Cred = Get-Credential
```

<span data-ttu-id="9e13c-120">Maak een een-op-een Power shell-externe sessie op de domein controller met de naam DC01.</span><span class="sxs-lookup"><span data-stu-id="9e13c-120">Create a one-to-one PowerShell remoting session to the domain controller named dc01.</span></span>

```powershell
Enter-PSSession -ComputerName dc01 -Credential $Cred
```

```Output
[dc01]: PS C:\Users\Administrator\Documents>
```

<span data-ttu-id="9e13c-121">U ziet dat in het vorige voor beeld de Power shell-prompt wordt voorafgegaan door `[dc01]` .</span><span class="sxs-lookup"><span data-stu-id="9e13c-121">Notice that in the previous example that the PowerShell prompt is preceded by `[dc01]`.</span></span> <span data-ttu-id="9e13c-122">Dit betekent dat u een interactieve Power shell-sessie hebt met de externe computer met de naam DC01.</span><span class="sxs-lookup"><span data-stu-id="9e13c-122">This means you're in an interactive PowerShell session to the remote computer named dc01.</span></span> <span data-ttu-id="9e13c-123">Opdrachten die u uitvoert, worden uitgevoerd op DC01, niet op uw lokale computer.</span><span class="sxs-lookup"><span data-stu-id="9e13c-123">Any commands you execute run on dc01, not on your local computer.</span></span> <span data-ttu-id="9e13c-124">U moet er ook voor zorgen dat u alleen toegang hebt tot de Power shell-opdrachten die op de externe computer bestaan en niet op uw lokale computer.</span><span class="sxs-lookup"><span data-stu-id="9e13c-124">Also, keep in mind that you only have access to the PowerShell commands that exist on the remote computer and not the ones on your local computer.</span></span> <span data-ttu-id="9e13c-125">Met andere woorden, als u extra modules op uw computer hebt geïnstalleerd, zijn ze niet toegankelijk op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="9e13c-125">In other words, if you've installed additional modules on your computer, they aren't accessible on the remote computer.</span></span>

<span data-ttu-id="9e13c-126">Wanneer u via een een-op-een interactieve externe Power shell-sessie verbinding hebt, kunt u de externe computer op een andere computer aansluiten.</span><span class="sxs-lookup"><span data-stu-id="9e13c-126">When you're connected to a remote computer via a one-to-one interactive PowerShell remoting session, you're effectively sitting at the remote computer.</span></span> <span data-ttu-id="9e13c-127">De objecten zijn normale objecten net als het object waarmee u in dit hele boek werkte.</span><span class="sxs-lookup"><span data-stu-id="9e13c-127">The objects are normal objects just like the ones you've been working with throughout this entire book.</span></span>

```powershell
[dc01]:  Get-Process | Get-Member
```

```Output
   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
NPM                        AliasProperty  NPM = NonpagedSystemMemorySize64
PM                         AliasProperty  PM = PagedMemorySize64
SI                         AliasProperty  SI = SessionId
VM                         AliasProperty  VM = VirtualMemorySize64
WS                         AliasProperty  WS = WorkingSet64
Disposed                   Event          System.EventHandler Disposed(System.Object, ...
ErrorDataReceived          Event          System.Diagnostics.DataReceivedEventHandler ...
Exited                     Event          System.EventHandler Exited(System.Object, Sy...
OutputDataReceived         Event          System.Diagnostics.DataReceivedEventHandler ...
BeginErrorReadLine         Method         void BeginErrorReadLine()
BeginOutputReadLine        Method         void BeginOutputReadLine()
CancelErrorRead            Method         void CancelErrorRead()
CancelOutputRead           Method         void CancelOutputRead()
Close                      Method         void Close()
CloseMainWindow            Method         bool CloseMainWindow()
CreateObjRef               Method         System.Runtime.Remoting.ObjRef CreateObjRef(...
Dispose                    Method         void Dispose(), void IDisposable.Dispose()
Equals                     Method         bool Equals(System.Object obj)
GetHashCode                Method         int GetHashCode()
GetLifetimeService         Method         System.Object GetLifetimeService()
GetType                    Method         type GetType()
InitializeLifetimeService  Method         System.Object InitializeLifetimeService()
Kill                       Method         void Kill()
Refresh                    Method         void Refresh()
Start                      Method         bool Start()
ToString                   Method         string ToString()
WaitForExit                Method         bool WaitForExit(int milliseconds), void Wai...
WaitForInputIdle           Method         bool WaitForInputIdle(int milliseconds), boo...
__NounName                 NoteProperty   string __NounName=Process
BasePriority               Property       int BasePriority {get;}
Container                  Property       System.ComponentModel.IContainer Container {...
EnableRaisingEvents        Property       bool EnableRaisingEvents {get;set;}
ExitCode                   Property       int ExitCode {get;}
ExitTime                   Property       datetime ExitTime {get;}
Handle                     Property       System.IntPtr Handle {get;}
HandleCount                Property       int HandleCount {get;}
HasExited                  Property       bool HasExited {get;}
Id                         Property       int Id {get;}
MachineName                Property       string MachineName {get;}
MainModule                 Property       System.Diagnostics.ProcessModule MainModule ...
MainWindowHandle           Property       System.IntPtr MainWindowHandle {get;}
MainWindowTitle            Property       string MainWindowTitle {get;}
MaxWorkingSet              Property       System.IntPtr MaxWorkingSet {get;set;}
MinWorkingSet              Property       System.IntPtr MinWorkingSet {get;set;}
Modules                    Property       System.Diagnostics.ProcessModuleCollection M...
NonpagedSystemMemorySize   Property       int NonpagedSystemMemorySize {get;}
NonpagedSystemMemorySize64 Property       long NonpagedSystemMemorySize64 {get;}
PagedMemorySize            Property       int PagedMemorySize {get;}
PagedMemorySize64          Property       long PagedMemorySize64 {get;}
PagedSystemMemorySize      Property       int PagedSystemMemorySize {get;}
PagedSystemMemorySize64    Property       long PagedSystemMemorySize64 {get;}
PeakPagedMemorySize        Property       int PeakPagedMemorySize {get;}
PeakPagedMemorySize64      Property       long PeakPagedMemorySize64 {get;}
PeakVirtualMemorySize      Property       int PeakVirtualMemorySize {get;}
PeakVirtualMemorySize64    Property       long PeakVirtualMemorySize64 {get;}
PeakWorkingSet             Property       int PeakWorkingSet {get;}
PeakWorkingSet64           Property       long PeakWorkingSet64 {get;}
PriorityBoostEnabled       Property       bool PriorityBoostEnabled {get;set;}
PriorityClass              Property       System.Diagnostics.ProcessPriorityClass Prio...
PrivateMemorySize          Property       int PrivateMemorySize {get;}
PrivateMemorySize64        Property       long PrivateMemorySize64 {get;}
PrivilegedProcessorTime    Property       timespan PrivilegedProcessorTime {get;}
ProcessName                Property       string ProcessName {get;}
ProcessorAffinity          Property       System.IntPtr ProcessorAffinity {get;set;}
Responding                 Property       bool Responding {get;}
SafeHandle                 Property       Microsoft.Win32.SafeHandles.SafeProcessHandl...
SessionId                  Property       int SessionId {get;}
Site                       Property       System.ComponentModel.ISite Site {get;set;}
StandardError              Property       System.IO.StreamReader StandardError {get;}
StandardInput              Property       System.IO.StreamWriter StandardInput {get;}
StandardOutput             Property       System.IO.StreamReader StandardOutput {get;}
StartInfo                  Property       System.Diagnostics.ProcessStartInfo StartInf...
StartTime                  Property       datetime StartTime {get;}
SynchronizingObject        Property       System.ComponentModel.ISynchronizeInvoke Syn...
Threads                    Property       System.Diagnostics.ProcessThreadCollection T...
TotalProcessorTime         Property       timespan TotalProcessorTime {get;}
UserProcessorTime          Property       timespan UserProcessorTime {get;}
VirtualMemorySize          Property       int VirtualMemorySize {get;}
VirtualMemorySize64        Property       long VirtualMemorySize64 {get;}
WorkingSet                 Property       int WorkingSet {get;}
WorkingSet64               Property       long WorkingSet64 {get;}
PSConfiguration            PropertySet    PSConfiguration {Name, Id, PriorityClass, Fi...
PSResources                PropertySet    PSResources {Name, Id, Handlecount, WorkingS...
Company                    ScriptProperty System.Object Company {get=$this.Mainmodule....
CPU                        ScriptProperty System.Object CPU {get=$this.TotalProcessorT...
Description                ScriptProperty System.Object Description {get=$this.Mainmod...
FileVersion                ScriptProperty System.Object FileVersion {get=$this.Mainmod...
Path                       ScriptProperty System.Object Path {get=$this.Mainmodule.Fil...
Product                    ScriptProperty System.Object Product {get=$this.Mainmodule....
ProductVersion             ScriptProperty System.Object ProductVersion {get=$this.Main...
[dc01]:
```

<span data-ttu-id="9e13c-128">Wanneer u klaar bent met het werken met de externe computer, sluit u de één-op-een externe sessie met behulp van de `Exit-PSSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9e13c-128">When you're done working with the remote computer, exit the one-to-one remoting session by using the `Exit-PSSession` cmdlet.</span></span>

```powershell
[dc01]:  Exit-PSSession
```

## <a name="one-to-many-remoting"></a><span data-ttu-id="9e13c-129">Een-op-veel externe communicatie</span><span class="sxs-lookup"><span data-stu-id="9e13c-129">One-To-Many Remoting</span></span>

<span data-ttu-id="9e13c-130">Soms moet u een taak interactief uitvoeren op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="9e13c-130">Sometimes you may need to perform a task interactively on a remote computer.</span></span> <span data-ttu-id="9e13c-131">Externe toegang is echter veel krachtiger wanneer u een taak op meerdere externe computers tegelijk uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9e13c-131">But remoting is much more powerful when performing a task on multiple remote computers at the same time.</span></span> <span data-ttu-id="9e13c-132">Gebruik de `Invoke-Command` cmdlet om een opdracht uit te voeren op een of meer externe computers tegelijk.</span><span class="sxs-lookup"><span data-stu-id="9e13c-132">Use the `Invoke-Command` cmdlet to run a command against one or more remote computers at the same time.</span></span>

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

<span data-ttu-id="9e13c-133">In het vorige voor beeld hebben drie servers een query uitgevoerd voor de status van de Windows Time-service.</span><span class="sxs-lookup"><span data-stu-id="9e13c-133">In the previous example, three servers were queried for the status of the Windows Time service.</span></span> <span data-ttu-id="9e13c-134">De `Get-Service` cmdlet is in het script blok van opgenomen `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="9e13c-134">The `Get-Service` cmdlet was placed inside the script block of `Invoke-Command`.</span></span> <span data-ttu-id="9e13c-135">`Get-Service`wordt daad werkelijk uitgevoerd op de externe computer en de resultaten worden teruggestuurd naar de lokale computer als gedeserialiseerd objecten.</span><span class="sxs-lookup"><span data-stu-id="9e13c-135">`Get-Service` actually runs on the remote computer and the results are returned to your local computer as deserialized objects.</span></span>

<span data-ttu-id="9e13c-136">Sluizen de vorige opdracht om te laten `Get-Member` zien dat de resultaten inderdaad gedeserialiseerd objecten zijn.</span><span class="sxs-lookup"><span data-stu-id="9e13c-136">Piping the previous command to `Get-Member` shows that the results are indeed deserialized objects.</span></span>

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred | Get-Member
```

```Output
   TypeName: Deserialized.System.ServiceProcess.ServiceController

Name                MemberType   Definition
----                ----------   ----------
GetType             Method       type GetType()
ToString            Method       string ToString(), string ToString(string format, Sys...
Name                NoteProperty string Name=W32time
PSComputerName      NoteProperty string PSComputerName=sql02
PSShowComputerName  NoteProperty bool PSShowComputerName=True
RequiredServices    NoteProperty Deserialized.System.ServiceProcess.ServiceController[...
RunspaceId          NoteProperty guid RunspaceId=570313c4-ac84-4109-bf67-c6b33236af0a
CanPauseAndContinue Property     System.Boolean {get;set;}
CanShutdown         Property     System.Boolean {get;set;}
CanStop             Property     System.Boolean {get;set;}
Container           Property      {get;set;}
DependentServices   Property     Deserialized.System.ServiceProcess.ServiceController[...
DisplayName         Property     System.String {get;set;}
MachineName         Property     System.String {get;set;}
ServiceHandle       Property     System.String {get;set;}
ServiceName         Property     System.String {get;set;}
ServicesDependedOn  Property     Deserialized.System.ServiceProcess.ServiceController[...
ServiceType         Property     System.String {get;set;}
Site                Property      {get;set;}
StartType           Property     System.String {get;set;}
Status              Property     System.String {get;set;}
```

<span data-ttu-id="9e13c-137">U ziet dat de meeste methoden ontbreken in gedeserialiseerd objecten.</span><span class="sxs-lookup"><span data-stu-id="9e13c-137">Notice that the majority of the methods are missing on deserialized objects.</span></span> <span data-ttu-id="9e13c-138">Dit betekent dat ze geen live objecten zijn. ze zijn inert.</span><span class="sxs-lookup"><span data-stu-id="9e13c-138">This means they're not live objects; they're inert.</span></span> <span data-ttu-id="9e13c-139">U kunt een service niet starten of stoppen met behulp van een gedeserialiseerd object, omdat het een moment opname van de status van dat object is op het moment dat de opdracht wordt uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="9e13c-139">You can't start or stop a service using a deserialized object because it's a snapshot of the state of that object the point when the command ran on the remote computer.</span></span>

<span data-ttu-id="9e13c-140">Dat betekent dat u een service niet kunt starten of stoppen met behulp van een methode met `Invoke-Command` Hoewel.</span><span class="sxs-lookup"><span data-stu-id="9e13c-140">That doesn't mean you can't start or stop a service using a method with `Invoke-Command` though.</span></span> <span data-ttu-id="9e13c-141">Dit betekent alleen dat de methode moet worden aangeroepen in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="9e13c-141">It just means that the method has to be called in the remote session.</span></span>

<span data-ttu-id="9e13c-142">Ik stop de Windows Time-service op alle drie de externe servers met behulp van de methode **stop ()** om dit punt te bewijzen.</span><span class="sxs-lookup"><span data-stu-id="9e13c-142">I'll stop the Windows Time service on all three of those remote servers using the **Stop()** method to prove this point.</span></span>

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {(Get-Service -Name W32time).Stop()} -Credential $Cred
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

<span data-ttu-id="9e13c-143">Zoals vermeld in een voor gaande hoofd stuk, raden we u aan om het te gebruiken als er een cmdlet voor het uitvoeren van een taak wordt gebruikt in plaats van een methode te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="9e13c-143">As mentioned in a previous chapter, if a cmdlet exists for accomplishing a task, I recommend using it instead of using a method.</span></span> <span data-ttu-id="9e13c-144">In het vorige scenario raden we u aan de `Stop-Service` cmdlet te gebruiken in plaats van de methode stop.</span><span class="sxs-lookup"><span data-stu-id="9e13c-144">In the previous scenario, I recommend using the `Stop-Service` cmdlet instead of the stop method.</span></span> <span data-ttu-id="9e13c-145">Ik heb ervoor gekozen om de methode **stop ()** te gebruiken om een punt te bewijzen, omdat veel mensen onder het hoofd zijn van de niet-berekenings wijze die niet kan worden aangeroepen wanneer externe communicatie van Power shell wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9e13c-145">I chose to use the **Stop()** method to prove a point since many people are under the misconception that methods can't be called when using PowerShell remoting.</span></span> <span data-ttu-id="9e13c-146">Ze kunnen niet worden aangeroepen op het object dat wordt geretourneerd, omdat het is gedeserialiseerd, maar kan worden aangeroepen in de externe sessie.</span><span class="sxs-lookup"><span data-stu-id="9e13c-146">They can't be called on the object that's returned because it's deserialized, but they can be called in the remote session itself.</span></span>

## <a name="powershell-sessions"></a><span data-ttu-id="9e13c-147">Power shell-sessies</span><span class="sxs-lookup"><span data-stu-id="9e13c-147">PowerShell Sessions</span></span>

<span data-ttu-id="9e13c-148">In het laatste voor beeld in de vorige sectie hebt u twee opdrachten uitgevoerd met behulp van de `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9e13c-148">In the last example in the previous section, I ran two commands using the `Invoke-Command` cmdlet.</span></span>
<span data-ttu-id="9e13c-149">Dit betekent dat er twee afzonderlijke sessies moeten worden ingesteld en gescheurd om deze twee opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="9e13c-149">That means two separate sessions had to be set up and torn down to run those two commands.</span></span>

<span data-ttu-id="9e13c-150">Net als bij de CIM-sessies die worden besproken in hoofd stuk 7, kan een Power shell-sessie op een externe computer worden gebruikt om meerdere opdrachten uit te voeren op de externe computer zonder de overhead van een nieuwe sessie voor elke afzonderlijke opdracht.</span><span class="sxs-lookup"><span data-stu-id="9e13c-150">Similar to the CIM sessions discussed in Chapter 7, a PowerShell session to a remote computer can be used to run multiple commands against the remote computer without the overhead of a new session for each individual command.</span></span>

<span data-ttu-id="9e13c-151">Maak een Power shell-sessie op elk van de drie computers waarmee we werken in dit hoofd stuk, DC01, SQL02 en WEB01.</span><span class="sxs-lookup"><span data-stu-id="9e13c-151">Create a PowerShell session to each of the three computers we've been working with in this chapter, DC01, SQL02, and WEB01.</span></span>

```powershell
$Session = New-PSSession -ComputerName dc01, sql02, web01 -Credential $Cred
```

<span data-ttu-id="9e13c-152">Gebruik nu de variabele met de naam `$Session` voor het starten van de Windows Time-service met een methode en controleer de status van de service.</span><span class="sxs-lookup"><span data-stu-id="9e13c-152">Now use the variable named `$Session` to start the Windows Time service using a method and check the status of the service.</span></span>

```powershell
Invoke-Command -Session $Session {(Get-Service -Name W32time).Start()}
Invoke-Command -Session $Session {Get-Service -Name W32time}
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

<span data-ttu-id="9e13c-153">Zodra de sessie is gemaakt met behulp van alternatieve referenties, is het niet meer nodig om de referenties op te geven telkens wanneer een opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9e13c-153">Once the session is created using alternate credentials, it's no longer necessary to specify the credentials each time a command is run.</span></span>

<span data-ttu-id="9e13c-154">Wanneer u klaar bent met het gebruik van de sessies, moet u deze verwijderen.</span><span class="sxs-lookup"><span data-stu-id="9e13c-154">When you're finished using the sessions, be sure to remove them.</span></span>

```powershell
Get-PSSession | Remove-PSSession
```

## <a name="summary"></a><span data-ttu-id="9e13c-155">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="9e13c-155">Summary</span></span>

<span data-ttu-id="9e13c-156">In dit hoofd stuk hebt u geleerd over externe communicatie met Power shell, het uitvoeren van opdrachten in een interactieve sessie met één externe computer en het uitvoeren van opdrachten op meerdere computers met behulp van een-op-veel externe toegang.</span><span class="sxs-lookup"><span data-stu-id="9e13c-156">In this chapter you've learned about PowerShell remoting, how to run commands in an interactive session with one remote computer, and how to run commands against multiple computers using one-to-many remoting.</span></span> <span data-ttu-id="9e13c-157">U hebt ook de voor delen geleerd van het gebruik van een Power shell-sessie wanneer u meerdere opdrachten uitvoert op dezelfde externe computer.</span><span class="sxs-lookup"><span data-stu-id="9e13c-157">You've also learned the benefits of using a PowerShell session when running multiple commands against the same remote computer.</span></span>

## <a name="review"></a><span data-ttu-id="9e13c-158">Beoordelen</span><span class="sxs-lookup"><span data-stu-id="9e13c-158">Review</span></span>

1. <span data-ttu-id="9e13c-159">Hoe schakelt u externe communicatie van Power shell in?</span><span class="sxs-lookup"><span data-stu-id="9e13c-159">How do you enable PowerShell remoting?</span></span>
1. <span data-ttu-id="9e13c-160">Wat is de Power shell-opdracht voor het starten van een interactieve sessie met een externe computer?</span><span class="sxs-lookup"><span data-stu-id="9e13c-160">What is the PowerShell command for starting an interactive session with a remote computer?</span></span>
1. <span data-ttu-id="9e13c-161">Wat is een voor deel van het gebruik van een externe Power shell-sessie en alleen de computer naam opgeven bij elke opdracht?</span><span class="sxs-lookup"><span data-stu-id="9e13c-161">What is a benefit of using a PowerShell remoting session versus just specifying the computer name with each command?</span></span>
1. <span data-ttu-id="9e13c-162">Kan een externe sessie van Power shell worden gebruikt met een een-op-een externe sessie?</span><span class="sxs-lookup"><span data-stu-id="9e13c-162">Can a PowerShell remoting session be used with a one-to-one remoting session?</span></span>
1. <span data-ttu-id="9e13c-163">Wat is het verschil in het type objecten dat wordt geretourneerd door cmdlets en die worden geretourneerd wanneer dezelfde cmdlets worden uitgevoerd op externe computers met `Invoke-Command` ?</span><span class="sxs-lookup"><span data-stu-id="9e13c-163">What is the difference in the type of objects that are returned by cmdlets versus those returned when running those same cmdlets against remote computers with `Invoke-Command`?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="9e13c-164">Aanbevolen Lees bewerkingen</span><span class="sxs-lookup"><span data-stu-id="9e13c-164">Recommended Reading</span></span>

- <span data-ttu-id="9e13c-165">[about_Remote][]</span><span class="sxs-lookup"><span data-stu-id="9e13c-165">[about_Remote][]</span></span>
- <span data-ttu-id="9e13c-166">[about_Remote_FAQ][]</span><span class="sxs-lookup"><span data-stu-id="9e13c-166">[about_Remote_FAQ][]</span></span>
- <span data-ttu-id="9e13c-167">[about_Remote_Output][]</span><span class="sxs-lookup"><span data-stu-id="9e13c-167">[about_Remote_Output][]</span></span>
- <span data-ttu-id="9e13c-168">[about_Remote_Requirements][]</span><span class="sxs-lookup"><span data-stu-id="9e13c-168">[about_Remote_Requirements][]</span></span>
- <span data-ttu-id="9e13c-169">[about_Remote_Troubleshooting][]</span><span class="sxs-lookup"><span data-stu-id="9e13c-169">[about_Remote_Troubleshooting][]</span></span>
- <span data-ttu-id="9e13c-170">[about_Remote_Variables][]</span><span class="sxs-lookup"><span data-stu-id="9e13c-170">[about_Remote_Variables][]</span></span>

<!-- link references -->
[about_Remote]: /powershell/module/microsoft.powershell.core/about/about_remote
[about_Remote_FAQ]: /powershell/module/microsoft.powershell.core/about/about_remote_faq
[about_Remote_Output]: /powershell/module/microsoft.powershell.core/about/about_remote_output
[about_Remote_Requirements]: /powershell/module/microsoft.powershell.core/about/about_remote_requirements
[about_Remote_Troubleshooting]: /powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting
[about_Remote_Variables]: /powershell/module/microsoft.powershell.core/about/about_remote_variables
[Breaking changes in PowerShell 6.0]: /powershell/scripting/whats-new/breaking-changes-ps6#remove--protocol-from--computer-cmdlets-5277
