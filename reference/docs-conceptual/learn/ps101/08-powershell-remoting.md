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
# <a name="chapter-8---powershell-remoting"></a>Hoofd stuk 8-externe communicatie met Power shell

Power Shell heeft veel verschillende manieren om opdrachten uit te voeren op externe computers. In het laatste hoofd stuk hebt u gezien hoe u op afstand WMI kunt query's uitvoeren met behulp van de CIM-cmdlets. Power shell bevat ook verschillende cmdlets die een ingebouwde **ComputerName** -para meter hebben.

Zoals weer gegeven in het volgende voor beeld, `Get-Command` kan worden gebruikt met de **para meter parameter** waarde om te bepalen welke opdrachten een **ComputerName** -para meter hebben.

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

Opdrachten zoals `Get-Process` en `Get-Hotfix` hebben de para meter **ComputerName** . Dit is niet de lange termijn richting die micro soft kop voor het uitvoeren van opdrachten op externe computers. Zelfs als u een opdracht met de para meter **ComputerName** vindt, is het waarschijnlijk dat u alternatieve referenties moet opgeven en geen **referentie** parameter heeft. En als u hebt besloten Power shell uit te voeren vanuit een account met verhoogde bevoegdheden, kan de aanvraag door een firewall tussen u en de externe computer worden geblokkeerd.

Als u de Power shell-opdrachten voor externe communicatie wilt gebruiken die in dit hoofd stuk worden getoond, moet externe toegang tot Power shell zijn ingeschakeld op de externe computer. Gebruik de `Enable-PSRemoting` cmdlet om externe communicatie van Power shell in te scha kelen.

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

## <a name="one-to-one-remoting"></a>Een-op-een externe communicatie

Als u de externe sessie interactief wilt maken, kunt u een-op-een-op-een-een-op-een-een-op-één
Dit type externe toegang wordt via de cmdlet verschaft `Enter-PSSession` .

In het laatste hoofd stuk heb ik de referenties van mijn domein beheerder opgeslagen in een variabele met de naam `$Cred` . Als u dit nog niet hebt gedaan, gaat u naar de referenties van uw domein beheerder opslaan in de `$Cred` variabele.

Zo kunt u de referenties één keer invoeren en deze gebruiken op basis van elke opdracht, zolang uw huidige Power shell-sessie actief is.

```powershell
$Cred = Get-Credential
```

Maak een een-op-een Power shell-externe sessie op de domein controller met de naam DC01.

```powershell
Enter-PSSession -ComputerName dc01 -Credential $Cred
```

```Output
[dc01]: PS C:\Users\Administrator\Documents>
```

U ziet dat in het vorige voor beeld de Power shell-prompt wordt voorafgegaan door `[dc01]` . Dit betekent dat u een interactieve Power shell-sessie hebt met de externe computer met de naam DC01. Opdrachten die u uitvoert, worden uitgevoerd op DC01, niet op uw lokale computer. U moet er ook voor zorgen dat u alleen toegang hebt tot de Power shell-opdrachten die op de externe computer bestaan en niet op uw lokale computer. Met andere woorden, als u extra modules op uw computer hebt geïnstalleerd, zijn ze niet toegankelijk op de externe computer.

Wanneer u via een een-op-een interactieve externe Power shell-sessie verbinding hebt, kunt u de externe computer op een andere computer aansluiten. De objecten zijn normale objecten net als het object waarmee u in dit hele boek werkte.

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

Wanneer u klaar bent met het werken met de externe computer, sluit u de één-op-een externe sessie met behulp van de `Exit-PSSession` cmdlet.

```powershell
[dc01]:  Exit-PSSession
```

## <a name="one-to-many-remoting"></a>Een-op-veel externe communicatie

Soms moet u een taak interactief uitvoeren op een externe computer. Externe toegang is echter veel krachtiger wanneer u een taak op meerdere externe computers tegelijk uitvoert. Gebruik de `Invoke-Command` cmdlet om een opdracht uit te voeren op een of meer externe computers tegelijk.

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

In het vorige voor beeld hebben drie servers een query uitgevoerd voor de status van de Windows Time-service. De `Get-Service` cmdlet is in het script blok van opgenomen `Invoke-Command` . `Get-Service`wordt daad werkelijk uitgevoerd op de externe computer en de resultaten worden teruggestuurd naar de lokale computer als gedeserialiseerd objecten.

Sluizen de vorige opdracht om te laten `Get-Member` zien dat de resultaten inderdaad gedeserialiseerd objecten zijn.

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

U ziet dat de meeste methoden ontbreken in gedeserialiseerd objecten. Dit betekent dat ze geen live objecten zijn. ze zijn inert. U kunt een service niet starten of stoppen met behulp van een gedeserialiseerd object, omdat het een moment opname van de status van dat object is op het moment dat de opdracht wordt uitgevoerd op de externe computer.

Dat betekent dat u een service niet kunt starten of stoppen met behulp van een methode met `Invoke-Command` Hoewel. Dit betekent alleen dat de methode moet worden aangeroepen in de externe sessie.

Ik stop de Windows Time-service op alle drie de externe servers met behulp van de methode **stop ()** om dit punt te bewijzen.

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

Zoals vermeld in een voor gaande hoofd stuk, raden we u aan om het te gebruiken als er een cmdlet voor het uitvoeren van een taak wordt gebruikt in plaats van een methode te gebruiken. In het vorige scenario raden we u aan de `Stop-Service` cmdlet te gebruiken in plaats van de methode stop. Ik heb ervoor gekozen om de methode **stop ()** te gebruiken om een punt te bewijzen, omdat veel mensen onder het hoofd zijn van de niet-berekenings wijze die niet kan worden aangeroepen wanneer externe communicatie van Power shell wordt gebruikt. Ze kunnen niet worden aangeroepen op het object dat wordt geretourneerd, omdat het is gedeserialiseerd, maar kan worden aangeroepen in de externe sessie.

## <a name="powershell-sessions"></a>Power shell-sessies

In het laatste voor beeld in de vorige sectie hebt u twee opdrachten uitgevoerd met behulp van de `Invoke-Command` cmdlet.
Dit betekent dat er twee afzonderlijke sessies moeten worden ingesteld en gescheurd om deze twee opdrachten uit te voeren.

Net als bij de CIM-sessies die worden besproken in hoofd stuk 7, kan een Power shell-sessie op een externe computer worden gebruikt om meerdere opdrachten uit te voeren op de externe computer zonder de overhead van een nieuwe sessie voor elke afzonderlijke opdracht.

Maak een Power shell-sessie op elk van de drie computers waarmee we werken in dit hoofd stuk, DC01, SQL02 en WEB01.

```powershell
$Session = New-PSSession -ComputerName dc01, sql02, web01 -Credential $Cred
```

Gebruik nu de variabele met de naam `$Session` voor het starten van de Windows Time-service met een methode en controleer de status van de service.

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

Zodra de sessie is gemaakt met behulp van alternatieve referenties, is het niet meer nodig om de referenties op te geven telkens wanneer een opdracht wordt uitgevoerd.

Wanneer u klaar bent met het gebruik van de sessies, moet u deze verwijderen.

```powershell
Get-PSSession | Remove-PSSession
```

## <a name="summary"></a>Samenvatting

In dit hoofd stuk hebt u geleerd over externe communicatie met Power shell, het uitvoeren van opdrachten in een interactieve sessie met één externe computer en het uitvoeren van opdrachten op meerdere computers met behulp van een-op-veel externe toegang. U hebt ook de voor delen geleerd van het gebruik van een Power shell-sessie wanneer u meerdere opdrachten uitvoert op dezelfde externe computer.

## <a name="review"></a>Beoordelen

1. Hoe schakelt u externe communicatie van Power shell in?
1. Wat is de Power shell-opdracht voor het starten van een interactieve sessie met een externe computer?
1. Wat is een voor deel van het gebruik van een externe Power shell-sessie en alleen de computer naam opgeven bij elke opdracht?
1. Kan een externe sessie van Power shell worden gebruikt met een een-op-een externe sessie?
1. Wat is het verschil in het type objecten dat wordt geretourneerd door cmdlets en die worden geretourneerd wanneer dezelfde cmdlets worden uitgevoerd op externe computers met `Invoke-Command` ?

## <a name="recommended-reading"></a>Aanbevolen Lees bewerkingen

- [about_Remote][]
- [about_Remote_FAQ][]
- [about_Remote_Output][]
- [about_Remote_Requirements][]
- [about_Remote_Troubleshooting][]
- [about_Remote_Variables][]

<!-- link references -->
[about_Remote]: /powershell/module/microsoft.powershell.core/about/about_remote
[about_Remote_FAQ]: /powershell/module/microsoft.powershell.core/about/about_remote_faq
[about_Remote_Output]: /powershell/module/microsoft.powershell.core/about/about_remote_output
[about_Remote_Requirements]: /powershell/module/microsoft.powershell.core/about/about_remote_requirements
[about_Remote_Troubleshooting]: /powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting
[about_Remote_Variables]: /powershell/module/microsoft.powershell.core/about/about_remote_variables
[Breaking changes in PowerShell 6.0]: /powershell/scripting/whats-new/breaking-changes-ps6#remove--protocol-from--computer-cmdlets-5277
