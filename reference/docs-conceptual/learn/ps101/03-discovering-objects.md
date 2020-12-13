---
title: Objecten, eigenschappen en methoden ontdekken
description: U hoeft geen ontwikkelaar te zijn om objecten, eigenschappen en methoden te begrijpen en te gebruiken.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 5ab972755afeba0d94bf6c2debaf84ec84cd9244
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "84436363"
---
# <a name="chapter-3---discovering-objects-properties-and-methods"></a>Hoofd stuk 3: objecten, eigenschappen en methoden detecteren

Mijn eerste kennis Making met computers was een Commodore 64, maar mijn eerste moderne computer was een versie van 286 12-MHz IBM-kloon met 1 MB geheugen, een harde schijf van 40 MB en één 5-1/4 inch-diskette station met een CGA-monitor met micro soft DOS 3,3.

Veel IT-professionals, zoals mezelf, zijn geen vreemden naar de opdracht regel, maar wanneer het onderwerp van objecten, eigenschappen en methoden wordt opgehaald, krijgen ze de Deer in de koplampen te zien en zeggen we ' Ik ben geen ontwikkelaar '. Raden wat? U hoeft geen ontwikkelaar te zijn om te kunnen slagen met Power shell. Ga niet boekt omlaag in de terminologie. Het is niet mogelijk dat alles in eerste instantie zinvol is, maar na een beetje praktijk ervaring moet u deze ' Light lamp ' even laten duren. AHA! Dat is alles wat het boek heeft. "

Zorg ervoor dat u de voor beelden van uw computer kunt uitproberen om een deel van de praktijk ervaring te verkrijgen.

## <a name="requirements"></a>Vereisten

De Active Directory Power shell-module is vereist voor enkele van de voor beelden die in dit hoofd stuk worden weer gegeven.
De module maakt deel uit van de Remote Server Administration Tools (RSAT) voor Windows. Voor de 1809-build (of hoger) van Windows worden de RSAT-hulpprogram ma's geïnstalleerd als een Windows-functie.

- Zie [Windows Management modules][](Engelstalig) voor meer informatie over het installeren van de RSAT-hulpprogram ma's.
- Zie [RSAT voor Windows][]voor oudere versies van Windows.

## <a name="get-member"></a>Get-Member

`Get-Member` helpt u te ontdekken welke objecten, eigenschappen en methoden beschikbaar zijn voor-opdrachten.
Elke opdracht die een op een object gebaseerde uitvoer produceert kan worden gepiped naar `Get-Member` . Een eigenschap is een kenmerk van een item. De licentie van uw stuur Programma's heeft een eigenschap met de naam oogpictogram en de meest voorkomende waarden voor die eigenschap zijn blauw en bruin. Een methode is een actie die op een item kan worden uitgevoerd. In het geval van een voor beeld van de stuur programma-licentie is een van de methoden ' REVOKE ', omdat het departement motor voertuigen uw stuur programma-licentie kan intrekken.

### <a name="properties"></a>Eigenschappen

In het volgende voor beeld wordt informatie opgehaald over de Windows Time-service die op mijn computer wordt uitgevoerd.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

**Status**, **naam** en **DisplayName** zijn voor beelden van eigenschappen, zoals wordt weer gegeven in de vorige set resultaten. De waarde voor de eigenschap **status** is `Running` , de waarde voor de eigenschap **name** `w32time` en de waarde voor **DisplayName** is `Windows Time` .

Nu pipet u dezelfde opdracht voor het `Get-Member` volgende:

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

De eerste regel van de resultaten in het vorige voor beeld bevat een gedeelte van zeer belang rijke informatie. **TypeName** vertelt u welk type object is geretourneerd. In dit voor beeld is een **System. ServiceProcess. ServiceController** -object geretourneerd. Dit wordt vaak afgekort tot het gedeelte van de **TypeName** , net na de laatste periode. **ServiceController** in dit voor beeld.

Zodra u weet welk type object een opdracht produceert, kunt u deze informatie gebruiken om opdrachten te vinden die dit type object als invoer accepteren.

```powershell
Get-Command -ParameterType ServiceController
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
```

Al deze opdrachten hebben een para meter waarmee een **ServiceController** -object type wordt geaccepteerd per pijp lijn, parameter invoer of beide.

U ziet dat er meer eigenschappen zijn dan standaard worden weer gegeven. Hoewel deze extra eigenschappen niet standaard worden weer gegeven, kunnen ze worden geselecteerd in de pijp lijn door de opdracht te sluizen naar de `Select-Object` cmdlet en de **eigenschap** para meter te gebruiken. In het volgende voor beeld worden alle eigenschappen geselecteerd door de resultaten van `Get-Service` aan te sluizen `Select-Object` en het Joker teken op te geven `*` als de waarde voor de **eigenschaps** parameter.

```powershell
Get-Service -Name w32time | Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

Specifieke eigenschappen kunnen ook worden geselecteerd met behulp van een lijst met door komma's gescheiden waarden voor de waarde van de **eigenschaps** parameter.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, Name, DisplayName, ServiceType
```

```Output
 Status Name    DisplayName        ServiceType
 ------ ----    -----------        -----------
Running w32time Windows Time Win32ShareProcess
```

Standaard worden vier eigenschappen geretourneerd in een tabel en worden er vijf of meer waarden in een lijst geretourneerd. Sommige opdrachten maken gebruik van aangepaste opmaak om te overschrijven hoeveel eigenschappen standaard worden weer gegeven in een tabel.
Er zijn verschillende `Format-*` cmdlets die kunnen worden gebruikt om deze standaard waarden hand matig te overschrijven. De meest voorkomende waarden zijn `Format-Table` en `Format-List` , beide worden behandeld in een gepland hoofd stuk.

Joker tekens kunnen worden gebruikt bij het opgeven van de namen van eigenschappen met `Select-Object` .

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```powershell
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

In het vorige voor beeld `Can*` is gebruikt als een van de waarden voor de para meter **Property** om alle eigenschappen te retour neren die beginnen met `Can` . Dit zijn onder andere **CanPauseAndContinue**, **CanShutdown** en **CanStop**.

### <a name="methods"></a>Methoden

Methoden zijn een actie die kan worden uitgevoerd. Gebruik de para meter **member type** om de resultaten te verfijnen `Get-Member` zodat alleen de methoden voor worden weer gegeven `Get-Service` .

```powershell
Get-Service -Name w32time | Get-Member -MemberType Method
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType Definition
----                      ---------- ----------
Close                     Method     void Close()
Continue                  Method     void Continue()
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type ...
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Equals                    Method     bool Equals(System.Object obj)
ExecuteCommand            Method     void ExecuteCommand(int command)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Pause                     Method     void Pause()
Refresh                   Method     void Refresh()
Start                     Method     void Start(), void Start(string[] args)
Stop                      Method     void Stop()
WaitForStatus             Method     void WaitForStatus(System.ServiceProcess.ServiceC...
```

Zoals u kunt zien, zijn er veel methoden. De methode **Stop** kan worden gebruikt om een Windows-service te stoppen.

```powershell
(Get-Service -Name w32time).Stop()
```

U kunt nu controleren of de Windows Time-service is gestopt.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  w32time            Windows Time
```

Ik vind zelf nooit zelf methoden, maar het is iets wat u nodig hebt om op de hoogte te zijn. Er is een aantal keren dat u bij een `Get-*` opdracht komt zonder een bijbehorende opdracht om dat item te wijzigen.
Een methode kan vaak worden gebruikt om een actie uit te voeren die deze wijzigt. De `Get-SqlAgentJob` cmdlet in de sqlserver Power shell-module is een goed voor beeld hiervan. De module wordt geïnstalleerd als onderdeel van [SQL Server Management Studio (smss)][SMSS]. Er bestaat geen bijbehorende `Set-*` cmdlet, maar een methode kan worden gebruikt om dezelfde taak te volt ooien.

Een andere reden om op de hoogte te zijn van methoden is dat veel beginners aannemen dat destructieve wijzigingen niet met opdrachten kunnen worden aangebracht `Get-*` . Maar ze kunnen ernstige problemen veroorzaken als ze niet op de juiste wijze worden gebruikt.

Een betere optie is het gebruik van een cmdlet voor het uitvoeren van de actie als deze bestaat. Start de Windows Time-service, maar gebruik de cmdlet voor het starten van services.

```powershell
Get-Service -Name w32time | Start-Service -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

Standaard retourneert geen `Start-Service` resultaten zoals de start methode van `Get-Service` .
Maar een van de voor delen van het gebruik van een cmdlet is dat vaak de cmdlet extra functionaliteit biedt die niet beschikbaar is met een methode. In het vorige voor beeld is de para meter **PassThru** gebruikt. Dit veroorzaakt een cmdlet die Norma liter geen uitvoer produceert, voor het produceren van uitvoer.

Wees voorzichtig met veronderstellingen over de uitvoer van een cmdlet. We weten wat er gebeurt wanneer u dat gaat doen. Ik krijg informatie over het Power Shell-proces dat wordt uitgevoerd op de computer met de Windows 10-test omgeving.

```powershell
Get-Process -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    922      48   107984     140552       2.84   9020   1 powershell

```

Nu pipet u dezelfde opdracht voor Get-lid:

```powershell
Get-Process -Name PowerShell | Get-Member
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
```

U ziet dat er meer eigenschappen worden vermeld dan standaard worden weer gegeven. Een aantal van de standaard eigenschappen die worden weer gegeven, worden niet weer geven als eigenschappen bij het weer geven van de resultaten van `Get-Member` . Dit komt doordat veel van de weer gegeven waarden, zoals `NPM(K)` , `PM(K)` , `WS(K)` en `CPU(s)` , berekende eigenschappen zijn. Als u de werkelijke eigenschapnamen wilt bepalen, moet de opdracht worden gepiped naar `Get-Member` .

Als een opdracht geen uitvoer produceert, kan er geen pipeing op worden uitgevoerd `Get-Member` . Aangezien er geen `Start-Service` uitvoer wordt gemaakt, wordt er een fout gegenereerd wanneer u deze wilt door sluizen naar `Get-Member` .

```powershell
Start-Service -Name w32time | Get-Member
```

```Output
Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:31
+ Start-Service -Name w32time | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMembe
   rCommand
```

De para meter **PassThru** kan worden opgegeven met de `Start-Service` cmdlet maken deze uitvoer, waardoor er `Get-Member` geen fout is opgetreden.

```powershell
Start-Service -Name w32time -PassThru | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

Om te worden gepiped naar `Get-Member` , moet een opdracht uitvoer op basis van een object opleveren.

```powershell
Get-Service -Name w32time | Out-Host | Get-Member
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time

Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:40
+ Get-Service -Name w32time | Out-Host | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMemberCommand
```

`Out-Host` schrijft rechtstreeks naar de Power shell-host, maar produceert geen op objecten gebaseerde uitvoer voor de pijp lijn. Zodat deze niet kan worden gepiped `Get-Member` .

## <a name="active-directory"></a>Active Directory

> [!NOTE]
> De Remote Server Administration Tools die worden vermeld in de sectie vereisten van dit hoofd stuk zijn vereist om deze sectie te volt ooien. Zoals vermeld in de inleiding tot dit boek, moet uw computer met Windows 10 lab-omgeving ook lid zijn van het domein van de test omgeving.

Gebruik `Get-Command` met de **module** parameter om te bepalen welke opdrachten zijn toegevoegd als onderdeel van de Active Directory Power shell-module toen de Remote Server Administration Tools werd geïnstalleerd.

```powershell
Get-Command -Module ActiveDirectory
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Add-ADCentralAccessPolicyMember                    1.0.0.0    ActiveDi...
Cmdlet          Add-ADComputerServiceAccount                       1.0.0.0    ActiveDi...
Cmdlet          Add-ADDomainControllerPasswordReplicationPolicy    1.0.0.0    ActiveDi...
Cmdlet          Add-ADFineGrainedPasswordPolicySubject             1.0.0.0    ActiveDi...
Cmdlet          Add-ADGroupMember                                  1.0.0.0    ActiveDi...
Cmdlet          Add-ADPrincipalGroupMembership                     1.0.0.0    ActiveDi...
Cmdlet          Add-ADResourcePropertyListMember                   1.0.0.0    ActiveDi...
Cmdlet          Clear-ADAccountExpiration                          1.0.0.0    ActiveDi...
Cmdlet          Clear-ADClaimTransformLink                         1.0.0.0    ActiveDi...
Cmdlet          Disable-ADAccount                                  1.0.0.0    ActiveDi...
...
```

Er zijn in totaal 147 opdrachten toegevoegd als onderdeel van de Active Directory Power shell-module. Sommige opdrachten van deze opdrachten retour neren standaard alleen een gedeelte van de beschik bare eigenschappen.

Hebt u iets anders genoteerd over de namen van de opdrachten in deze module? Het gedeelte van de zelfstandig naam woord van de opdrachten bevat een AD-voor voegsel. Dit is gebruikelijk om te zien wat de opdrachten van de meeste modules zijn. Het voor voegsel is ontworpen om naam conflicten te voor komen.

```powershell
Get-ADUser -Identity mike | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name              MemberType            Definition
----              ----------            ----------
Contains          Method                bool Contains(string propertyName)
Equals            Method                bool Equals(System.Object obj)
GetEnumerator     Method                System.Collections.IDictionaryEnumerator GetEn...
GetHashCode       Method                int GetHashCode()
GetType           Method                type GetType()
ToString          Method                string ToString()
Item              ParameterizedProperty Microsoft.ActiveDirectory.Management.ADPropert...
DistinguishedName Property              System.String DistinguishedName {get;set;}
Enabled           Property              System.Boolean Enabled {get;set;}
GivenName         Property              System.String GivenName {get;set;}
Name              Property              System.String Name {get;}
ObjectClass       Property              System.String ObjectClass {get;set;}
ObjectGUID        Property              System.Nullable`1[[System.Guid, mscorlib, Vers...
SamAccountName    Property              System.String SamAccountName {get;set;}
SID               Property              System.Security.Principal.SecurityIdentifier S...
Surname           Property              System.String Surname {get;set;}
UserPrincipalName Property              System.String UserPrincipalName {get;set;}
```

Zelfs als u alleen vaguely vertrouwd bent met Active Directory, weet u waarschijnlijk dat een gebruikers account meer eigenschappen heeft dan in dit voor beeld wordt weer gegeven.

De `Get-ADUser` cmdlet heeft een **Eigenschappen** parameter die wordt gebruikt om de aanvullende (niet-standaard) eigenschappen op te geven die u wilt retour neren. Als u het Joker teken opgeeft, worden `*` alle geretourneerd.

```powershell
Get-ADUser -Identity mike -Properties * | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name                                 MemberType            Definition
----                                 ----------            ----------
Contains                             Method                bool Contains(string proper...
Equals                               Method                bool Equals(System.Object obj)
GetEnumerator                        Method                System.Collections.IDiction...
GetHashCode                          Method                int GetHashCode()
GetType                              Method                type GetType()
ToString                             Method                string ToString()
Item                                 ParameterizedProperty Microsoft.ActiveDirectory.M...
AccountExpirationDate                Property              System.DateTime AccountExpi...
accountExpires                       Property              System.Int64 accountExpires...
AccountLockoutTime                   Property              System.DateTime AccountLock...
AccountNotDelegated                  Property              System.Boolean AccountNotDe...
AllowReversiblePasswordEncryption    Property              System.Boolean AllowReversi...
AuthenticationPolicy                 Property              Microsoft.ActiveDirectory.M...
AuthenticationPolicySilo             Property              Microsoft.ActiveDirectory.M...
BadLogonCount                        Property              System.Int32 BadLogonCount ...
badPasswordTime                      Property              System.Int64 badPasswordTim...
badPwdCount                          Property              System.Int32 badPwdCount {g...
CannotChangePassword                 Property              System.Boolean CannotChange...
CanonicalName                        Property              System.String CanonicalName...
Certificates                         Property              Microsoft.ActiveDirectory.M...
City                                 Property              System.String City {get;set;}
CN                                   Property              System.String CN {get;}
codePage                             Property              System.Int32 codePage {get;...
Company                              Property              System.String Company {get;...
CompoundIdentitySupported            Property              Microsoft.ActiveDirectory.M...
Country                              Property              System.String Country {get;...
countryCode                          Property              System.Int32 countryCode {g...
Created                              Property              System.DateTime Created {get;}
createTimeStamp                      Property              System.DateTime createTimeS...
Deleted                              Property              System.Boolean Deleted {get;}
Department                           Property              System.String Department {g...
Description                          Property              System.String Description {...
DisplayName                          Property              System.String DisplayName {...
DistinguishedName                    Property              System.String Distinguished...
Division                             Property              System.String Division {get...
DoesNotRequirePreAuth                Property              System.Boolean DoesNotRequi...
dSCorePropagationData                Property              Microsoft.ActiveDirectory.M...
EmailAddress                         Property              System.String EmailAddress ...
EmployeeID                           Property              System.String EmployeeID {g...
EmployeeNumber                       Property              System.String EmployeeNumbe...
Enabled                              Property              System.Boolean Enabled {get...
Fax                                  Property              System.String Fax {get;set;}
GivenName                            Property              System.String GivenName {ge...
HomeDirectory                        Property              System.String HomeDirectory...
HomedirRequired                      Property              System.Boolean HomedirRequi...
HomeDrive                            Property              System.String HomeDrive {ge...
HomePage                             Property              System.String HomePage {get...
HomePhone                            Property              System.String HomePhone {ge...
Initials                             Property              System.String Initials {get...
instanceType                         Property              System.Int32 instanceType {...
isDeleted                            Property              System.Boolean isDeleted {g...
KerberosEncryptionType               Property              Microsoft.ActiveDirectory.M...
LastBadPasswordAttempt               Property              System.DateTime LastBadPass...
LastKnownParent                      Property              System.String LastKnownPare...
lastLogoff                           Property              System.Int64 lastLogoff {ge...
lastLogon                            Property              System.Int64 lastLogon {get...
LastLogonDate                        Property              System.DateTime LastLogonDa...
lastLogonTimestamp                   Property              System.Int64 lastLogonTimes...
LockedOut                            Property              System.Boolean LockedOut {g...
logonCount                           Property              System.Int32 logonCount {ge...
LogonWorkstations                    Property              System.String LogonWorkstat...
Manager                              Property              System.String Manager {get;...
MemberOf                             Property              Microsoft.ActiveDirectory.M...
MNSLogonAccount                      Property              System.Boolean MNSLogonAcco...
MobilePhone                          Property              System.String MobilePhone {...
Modified                             Property              System.DateTime Modified {g...
modifyTimeStamp                      Property              System.DateTime modifyTimeS...
msDS-User-Account-Control-Computed   Property              System.Int32 msDS-User-Acco...
Name                                 Property              System.String Name {get;}
nTSecurityDescriptor                 Property              System.DirectoryServices.Ac...
ObjectCategory                       Property              System.String ObjectCategor...
ObjectClass                          Property              System.String ObjectClass {...
ObjectGUID                           Property              System.Nullable`1[[System.G...
objectSid                            Property              System.Security.Principal.S...
Office                               Property              System.String Office {get;s...
OfficePhone                          Property              System.String OfficePhone {...
Organization                         Property              System.String Organization ...
OtherName                            Property              System.String OtherName {ge...
PasswordExpired                      Property              System.Boolean PasswordExpi...
PasswordLastSet                      Property              System.DateTime PasswordLas...
PasswordNeverExpires                 Property              System.Boolean PasswordNeve...
PasswordNotRequired                  Property              System.Boolean PasswordNotR...
POBox                                Property              System.String POBox {get;set;}
PostalCode                           Property              System.String PostalCode {g...
PrimaryGroup                         Property              System.String PrimaryGroup ...
primaryGroupID                       Property              System.Int32 primaryGroupID...
PrincipalsAllowedToDelegateToAccount Property              Microsoft.ActiveDirectory.M...
ProfilePath                          Property              System.String ProfilePath {...
ProtectedFromAccidentalDeletion      Property              System.Boolean ProtectedFro...
pwdAnswer                            Property              System.String pwdAnswer {ge...
pwdLastSet                           Property              System.Int64 pwdLastSet {ge...
pwdQuestion                          Property              System.String pwdQuestion {...
SamAccountName                       Property              System.String SamAccountNam...
sAMAccountType                       Property              System.Int32 sAMAccountType...
ScriptPath                           Property              System.String ScriptPath {g...
sDRightsEffective                    Property              System.Int32 sDRightsEffect...
ServicePrincipalNames                Property              Microsoft.ActiveDirectory.M...
SID                                  Property              System.Security.Principal.S...
SIDHistory                           Property              Microsoft.ActiveDirectory.M...
SmartcardLogonRequired               Property              System.Boolean SmartcardLog...
sn                                   Property              System.String sn {get;set;}
State                                Property              System.String State {get;set;}
StreetAddress                        Property              System.String StreetAddress...
Surname                              Property              System.String Surname {get;...
Title                                Property              System.String Title {get;set;}
TrustedForDelegation                 Property              System.Boolean TrustedForDe...
TrustedToAuthForDelegation           Property              System.Boolean TrustedToAut...
UseDESKeyOnly                        Property              System.Boolean UseDESKeyOnl...
userAccountControl                   Property              System.Int32 userAccountCon...
userCertificate                      Property              Microsoft.ActiveDirectory.M...
UserPrincipalName                    Property              System.String UserPrincipal...
uSNChanged                           Property              System.Int64 uSNChanged {get;}
uSNCreated                           Property              System.Int64 uSNCreated {get;}
whenChanged                          Property              System.DateTime whenChanged...
whenCreated                          Property              System.DateTime whenCreated...
```

Nu ziet u dat er meer lijkt.

Kunt u een reden bedenken waarom de eigenschappen van een Active Directory gebruikers account standaard beperkt zijn? Stel dat u elke eigenschap voor elk gebruikers account in uw productie Active Directory omgeving hebt geretourneerd. Denk na over de prestatie vermindering die u zou kunnen veroorzaken, niet alleen voor de domein controllers zelf, maar ook voor uw netwerk. Het is twijfelt dat u elke eigenschap toch nodig hebt. Het retour neren van alle eigenschappen voor één gebruikers account is perfect acceptabel wanneer u probeert te bepalen welke eigenschappen er bestaan.

Het is niet ongebruikelijk om een opdracht meermaals uit te voeren wanneer het prototypet. Als u een enorme query wilt uitvoeren, voert u de query één keer uit en slaat u de resultaten op in een variabele. Werk vervolgens met de inhoud van de variabele in plaats van herhaaldelijk een duur query te gebruiken.

```powershell
$Users = Get-ADUser -Identity mike -Properties *
```

Gebruik de inhoud van de `$Users` variabele in plaats van de vorige opdracht talrijke keer uit te voeren.
Houd er wel voor dat de inhoud van de variabele niet wordt bijgewerkt wanneer er wijzigingen worden aangebracht aan die gebruiker in Active Directory.

U kunt de variabele door sluizen `$Users` naar `Get-Member` om de beschik bare eigenschappen te detecteren.

```powershell
$Users | Get-Member
```

Selecteer vervolgens de afzonderlijke eigenschappen van sluizen `$Users` naar `Select-Object` , zonder dat u meer dan één keer hoeft op te vragen Active Directory.

```powershell
$Users | Select-Object -Property Name, LastLogonDate, LastBadPasswordAttempt
```

Als u Active Directory meer dan een keer wilt zoeken, gebruikt u de para meter **Eigenschappen** om de niet-standaard eigenschappen op te geven die u wilt gebruiken.

```powershell
Get-ADUser -Identity mike -Properties LastLogonDate, LastBadPasswordAttempt
```

```Output
DistinguishedName      : CN=Mike F. Robbins,OU=Sales,DC=mikefrobbins,DC=com
Enabled                : True
GivenName              : Mike
LastBadPasswordAttempt : 2/4/2017 10:46:15 AM
LastLogonDate          : 2/18/2017 12:45:14 AM
Name                   : Mike F. Robbins
ObjectClass            : user
ObjectGUID             : a82a8c58-1332-4a57-a6e2-68e0c750ea56
SamAccountName         : mike
SID                    : S-1-5-21-2989741381-570885089-3319121794-1108
Surname                : Robbins
UserPrincipalName      : miker@mikefrobbins.com
```

## <a name="summary"></a>Samenvatting

In dit hoofd stuk hebt u geleerd hoe u kunt bepalen welk type object een opdracht produceert, hoe u kunt bepalen welke eigenschappen en methoden beschikbaar zijn voor een opdracht en hoe u kunt werken met opdrachten die de eigenschappen die standaard worden geretourneerd, beperken.

## <a name="review"></a>Beoordelen

1. Welk type object `Get-Process` produceert de cmdlet?
1. Hoe kunt u bepalen wat de beschik bare eigenschappen zijn voor een opdracht?
1. Als er een opdracht bestaat voor het verkrijgen van iets, maar niet voor het instellen van hetzelfde, wat moet u controleren?
1. Hoe kunnen bepaalde opdrachten die geen uitvoer produceren standaard worden gemaakt voor het produceren van uitvoer?
1. Als u wilt werken met de resultaten van een opdracht die een enorme hoeveelheid uitvoer produceert, wat moet u overwegen?

## <a name="recommended-reading"></a>Aanbevolen Lees bewerkingen

- [Get-member][]
- [Objectstructuur weergeven (Get-Member)][]
- [about_Objects][]
- [about_Properties][]
- [about_Methods][]
- [Geen Power shell-cmdlet om iets te starten of te stoppen? Vergeet niet om te controleren op methoden op de Get-cmdlets][use-methods]

<!-- link references -->
[RSAT voor Windows]: https://support.microsoft.com/help/2693643
[Windows-beheer modules]: /powershell/scripting/whats-new/module-compatibility#windows-management-modules
[Get-member]: /powershell/module/microsoft.powershell.utility/get-member
[Objectstructuur weergeven (Get-Member)]: /powershell/scripting/samples/viewing-object-structure--get-member-
[about_Objects]: /powershell/module/microsoft.powershell.core/about/about_objects
[about_Properties]: /powershell/module/microsoft.powershell.core/about/about_properties
[about_Methods]: /powershell/module/microsoft.powershell.core/about/about_methods
[use-methods]: https://mikefrobbins.com/2016/12/15/no-powershell-cmdlet-to-start-or-stop-something-dont-forget-to-check-for-methods-on-the-get-cmdlets/
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
