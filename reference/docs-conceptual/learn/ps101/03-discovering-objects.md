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
# <a name="chapter-3---discovering-objects-properties-and-methods"></a><span data-ttu-id="26ad4-103">Hoofd stuk 3: objecten, eigenschappen en methoden detecteren</span><span class="sxs-lookup"><span data-stu-id="26ad4-103">Chapter 3 - Discovering objects, properties, and methods</span></span>

<span data-ttu-id="26ad4-104">Mijn eerste kennis Making met computers was een Commodore 64, maar mijn eerste moderne computer was een versie van 286 12-MHz IBM-kloon met 1 MB geheugen, een harde schijf van 40 MB en één 5-1/4 inch-diskette station met een CGA-monitor met micro soft DOS 3,3.</span><span class="sxs-lookup"><span data-stu-id="26ad4-104">My first introduction to computers was a Commodore 64, but my first modern computer was a 286 12-Mhz IBM clone with 1 megabyte of memory, a 40-megabyte hard drive, and one 5-1/4 inch floppy disk drive with a CGA monitor running Microsoft DOS 3.3.</span></span>

<span data-ttu-id="26ad4-105">Veel IT-professionals, zoals mezelf, zijn geen vreemden naar de opdracht regel, maar wanneer het onderwerp van objecten, eigenschappen en methoden wordt opgehaald, krijgen ze de Deer in de koplampen te zien en zeggen we ' Ik ben geen ontwikkelaar '.</span><span class="sxs-lookup"><span data-stu-id="26ad4-105">Many IT Pros, like myself, are no stranger to the command line, but when the subject of objects, properties, and methods comes up, they get the deer in the headlights look and say, "I'm not a developer."</span></span> <span data-ttu-id="26ad4-106">Raden wat?</span><span class="sxs-lookup"><span data-stu-id="26ad4-106">Guess what?</span></span> <span data-ttu-id="26ad4-107">U hoeft geen ontwikkelaar te zijn om te kunnen slagen met Power shell.</span><span class="sxs-lookup"><span data-stu-id="26ad4-107">You don't have to be a developer to be successful with PowerShell.</span></span> <span data-ttu-id="26ad4-108">Ga niet boekt omlaag in de terminologie.</span><span class="sxs-lookup"><span data-stu-id="26ad4-108">Don't get bogged down in the terminology.</span></span> <span data-ttu-id="26ad4-109">Het is niet mogelijk dat alles in eerste instantie zinvol is, maar na een beetje praktijk ervaring moet u deze ' Light lamp ' even laten duren.</span><span class="sxs-lookup"><span data-stu-id="26ad4-109">Not everything may make sense initially, but after a little hands-on experience you'll start to have those "light bulb" moments.</span></span> <span data-ttu-id="26ad4-110">AHA!</span><span class="sxs-lookup"><span data-stu-id="26ad4-110">"Aha!</span></span> <span data-ttu-id="26ad4-111">Dat is alles wat het boek heeft. "</span><span class="sxs-lookup"><span data-stu-id="26ad4-111">So that's what the book was talking about."</span></span>

<span data-ttu-id="26ad4-112">Zorg ervoor dat u de voor beelden van uw computer kunt uitproberen om een deel van de praktijk ervaring te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="26ad4-112">Be sure to try the examples on your computer to gain some of that hands-on experience.</span></span>

## <a name="requirements"></a><span data-ttu-id="26ad4-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="26ad4-113">Requirements</span></span>

<span data-ttu-id="26ad4-114">De Active Directory Power shell-module is vereist voor enkele van de voor beelden die in dit hoofd stuk worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="26ad4-114">The Active Directory PowerShell module is required by some of the examples shown in this chapter.</span></span>
<span data-ttu-id="26ad4-115">De module maakt deel uit van de Remote Server Administration Tools (RSAT) voor Windows.</span><span class="sxs-lookup"><span data-stu-id="26ad4-115">The module is part of the Remote Server Administration Tools (RSAT) for Windows.</span></span> <span data-ttu-id="26ad4-116">Voor de 1809-build (of hoger) van Windows worden de RSAT-hulpprogram ma's geïnstalleerd als een Windows-functie.</span><span class="sxs-lookup"><span data-stu-id="26ad4-116">For the 1809 (or higher) build of Windows, the RSAT tools are installed as a Windows feature.</span></span>

- <span data-ttu-id="26ad4-117">Zie [Windows Management modules][](Engelstalig) voor meer informatie over het installeren van de RSAT-hulpprogram ma's.</span><span class="sxs-lookup"><span data-stu-id="26ad4-117">For information about installing the RSAT tools, see [Windows Management modules][].</span></span>
- <span data-ttu-id="26ad4-118">Zie [RSAT voor Windows][]voor oudere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="26ad4-118">For older versions of Windows, see [RSAT for Windows][].</span></span>

## <a name="get-member"></a><span data-ttu-id="26ad4-119">Get-Member</span><span class="sxs-lookup"><span data-stu-id="26ad4-119">Get-Member</span></span>

<span data-ttu-id="26ad4-120">`Get-Member` helpt u te ontdekken welke objecten, eigenschappen en methoden beschikbaar zijn voor-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="26ad4-120">`Get-Member` helps you discover what objects, properties, and methods are available for commands.</span></span>
<span data-ttu-id="26ad4-121">Elke opdracht die een op een object gebaseerde uitvoer produceert kan worden gepiped naar `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="26ad4-121">Any command that produces object-based output can be piped to `Get-Member`.</span></span> <span data-ttu-id="26ad4-122">Een eigenschap is een kenmerk van een item.</span><span class="sxs-lookup"><span data-stu-id="26ad4-122">A property is a characteristic about an item.</span></span> <span data-ttu-id="26ad4-123">De licentie van uw stuur Programma's heeft een eigenschap met de naam oogpictogram en de meest voorkomende waarden voor die eigenschap zijn blauw en bruin.</span><span class="sxs-lookup"><span data-stu-id="26ad4-123">Your drivers license has a property called eye color and the most common values for that property are blue and brown.</span></span> <span data-ttu-id="26ad4-124">Een methode is een actie die op een item kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="26ad4-124">A method is an action that can be taken on an item.</span></span> <span data-ttu-id="26ad4-125">In het geval van een voor beeld van de stuur programma-licentie is een van de methoden ' REVOKE ', omdat het departement motor voertuigen uw stuur programma-licentie kan intrekken.</span><span class="sxs-lookup"><span data-stu-id="26ad4-125">In staying with the drivers license example, one of the methods is "Revoke" because the department of motor vehicles can revoke your drivers license.</span></span>

### <a name="properties"></a><span data-ttu-id="26ad4-126">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="26ad4-126">Properties</span></span>

<span data-ttu-id="26ad4-127">In het volgende voor beeld wordt informatie opgehaald over de Windows Time-service die op mijn computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="26ad4-127">In the following example, I'll retrieve information about the Windows Time service running on my computer.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="26ad4-128">**Status**, **naam** en **DisplayName** zijn voor beelden van eigenschappen, zoals wordt weer gegeven in de vorige set resultaten.</span><span class="sxs-lookup"><span data-stu-id="26ad4-128">**Status**, **Name**, and **DisplayName** are examples of properties as shown in the previous set of results.</span></span> <span data-ttu-id="26ad4-129">De waarde voor de eigenschap **status** is `Running` , de waarde voor de eigenschap **name** `w32time` en de waarde voor **DisplayName** is `Windows Time` .</span><span class="sxs-lookup"><span data-stu-id="26ad4-129">The value for the **Status** property is `Running`, the value for the **Name** property is `w32time`, and the value for **DisplayName** is `Windows Time`.</span></span>

<span data-ttu-id="26ad4-130">Nu pipet u dezelfde opdracht voor het `Get-Member` volgende:</span><span class="sxs-lookup"><span data-stu-id="26ad4-130">Now I'll pipe that same command to `Get-Member`:</span></span>

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

<span data-ttu-id="26ad4-131">De eerste regel van de resultaten in het vorige voor beeld bevat een gedeelte van zeer belang rijke informatie.</span><span class="sxs-lookup"><span data-stu-id="26ad4-131">The first line of the results in the previous example contains one piece of very important information.</span></span> <span data-ttu-id="26ad4-132">**TypeName** vertelt u welk type object is geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="26ad4-132">**TypeName** tells you what type of object was returned.</span></span> <span data-ttu-id="26ad4-133">In dit voor beeld is een **System. ServiceProcess. ServiceController** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="26ad4-133">In this example, a **System.ServiceProcess.ServiceController** object was returned.</span></span> <span data-ttu-id="26ad4-134">Dit wordt vaak afgekort tot het gedeelte van de **TypeName** , net na de laatste periode. **ServiceController** in dit voor beeld.</span><span class="sxs-lookup"><span data-stu-id="26ad4-134">This is often abbreviated as the portion of the **TypeName** just after the last period; **ServiceController** in this example.</span></span>

<span data-ttu-id="26ad4-135">Zodra u weet welk type object een opdracht produceert, kunt u deze informatie gebruiken om opdrachten te vinden die dit type object als invoer accepteren.</span><span class="sxs-lookup"><span data-stu-id="26ad4-135">Once you know what type of object a command produces, you can use this information to find commands that accept that type of object as input.</span></span>

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

<span data-ttu-id="26ad4-136">Al deze opdrachten hebben een para meter waarmee een **ServiceController** -object type wordt geaccepteerd per pijp lijn, parameter invoer of beide.</span><span class="sxs-lookup"><span data-stu-id="26ad4-136">All of those commands have a parameter that accepts a **ServiceController** object type by pipeline, parameter input, or both.</span></span>

<span data-ttu-id="26ad4-137">U ziet dat er meer eigenschappen zijn dan standaard worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="26ad4-137">Notice that there are more properties than are displayed by default.</span></span> <span data-ttu-id="26ad4-138">Hoewel deze extra eigenschappen niet standaard worden weer gegeven, kunnen ze worden geselecteerd in de pijp lijn door de opdracht te sluizen naar de `Select-Object` cmdlet en de **eigenschap** para meter te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="26ad4-138">Although these additional properties aren't displayed by default, they can be selected from the pipeline by piping the command to the `Select-Object` cmdlet and using the **Property** parameter.</span></span> <span data-ttu-id="26ad4-139">In het volgende voor beeld worden alle eigenschappen geselecteerd door de resultaten van `Get-Service` aan te sluizen `Select-Object` en het Joker teken op te geven `*` als de waarde voor de **eigenschaps** parameter.</span><span class="sxs-lookup"><span data-stu-id="26ad4-139">The following example selects all of the properties by piping the results of `Get-Service` to `Select-Object` and specifying the `*` wildcard character as the value for the **Property** parameter.</span></span>

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

<span data-ttu-id="26ad4-140">Specifieke eigenschappen kunnen ook worden geselecteerd met behulp van een lijst met door komma's gescheiden waarden voor de waarde van de **eigenschaps** parameter.</span><span class="sxs-lookup"><span data-stu-id="26ad4-140">Specific properties can also be selected using a comma-separated list for the value of the **Property** parameter.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, Name, DisplayName, ServiceType
```

```Output
 Status Name    DisplayName        ServiceType
 ------ ----    -----------        -----------
Running w32time Windows Time Win32ShareProcess
```

<span data-ttu-id="26ad4-141">Standaard worden vier eigenschappen geretourneerd in een tabel en worden er vijf of meer waarden in een lijst geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="26ad4-141">By default, four properties are returned in a table and five or more are returned in a list.</span></span> <span data-ttu-id="26ad4-142">Sommige opdrachten maken gebruik van aangepaste opmaak om te overschrijven hoeveel eigenschappen standaard worden weer gegeven in een tabel.</span><span class="sxs-lookup"><span data-stu-id="26ad4-142">Some commands use custom formatting to override how many properties are displayed by default in a table.</span></span>
<span data-ttu-id="26ad4-143">Er zijn verschillende `Format-*` cmdlets die kunnen worden gebruikt om deze standaard waarden hand matig te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="26ad4-143">There are several `Format-*` cmdlets that can be used to manually override these defaults.</span></span> <span data-ttu-id="26ad4-144">De meest voorkomende waarden zijn `Format-Table` en `Format-List` , beide worden behandeld in een gepland hoofd stuk.</span><span class="sxs-lookup"><span data-stu-id="26ad4-144">The most common ones are `Format-Table` and `Format-List`, both of which will be covered in an upcoming chapter.</span></span>

<span data-ttu-id="26ad4-145">Joker tekens kunnen worden gebruikt bij het opgeven van de namen van eigenschappen met `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="26ad4-145">Wildcard characters can be used when specifying the property names with `Select-Object`.</span></span>

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

<span data-ttu-id="26ad4-146">In het vorige voor beeld `Can*` is gebruikt als een van de waarden voor de para meter **Property** om alle eigenschappen te retour neren die beginnen met `Can` .</span><span class="sxs-lookup"><span data-stu-id="26ad4-146">In the previous example, `Can*` was used as one of the values for the **Property** parameter to return all the properties that start with `Can`.</span></span> <span data-ttu-id="26ad4-147">Dit zijn onder andere **CanPauseAndContinue**, **CanShutdown** en **CanStop**.</span><span class="sxs-lookup"><span data-stu-id="26ad4-147">These include **CanPauseAndContinue**, **CanShutdown**, and **CanStop**.</span></span>

### <a name="methods"></a><span data-ttu-id="26ad4-148">Methoden</span><span class="sxs-lookup"><span data-stu-id="26ad4-148">Methods</span></span>

<span data-ttu-id="26ad4-149">Methoden zijn een actie die kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="26ad4-149">Methods are an action that can be taken.</span></span> <span data-ttu-id="26ad4-150">Gebruik de para meter **member type** om de resultaten te verfijnen `Get-Member` zodat alleen de methoden voor worden weer gegeven `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="26ad4-150">Use the **MemberType** parameter to narrow down the results of `Get-Member` to only show the methods for `Get-Service`.</span></span>

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

<span data-ttu-id="26ad4-151">Zoals u kunt zien, zijn er veel methoden.</span><span class="sxs-lookup"><span data-stu-id="26ad4-151">As you can see, there are many methods.</span></span> <span data-ttu-id="26ad4-152">De methode **Stop** kan worden gebruikt om een Windows-service te stoppen.</span><span class="sxs-lookup"><span data-stu-id="26ad4-152">The **Stop** method can be used to stop a Windows service.</span></span>

```powershell
(Get-Service -Name w32time).Stop()
```

<span data-ttu-id="26ad4-153">U kunt nu controleren of de Windows Time-service is gestopt.</span><span class="sxs-lookup"><span data-stu-id="26ad4-153">Now to verify the Windows time service has indeed been stopped.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  w32time            Windows Time
```

<span data-ttu-id="26ad4-154">Ik vind zelf nooit zelf methoden, maar het is iets wat u nodig hebt om op de hoogte te zijn.</span><span class="sxs-lookup"><span data-stu-id="26ad4-154">I rarely find myself using methods, but they're something you need to be aware of.</span></span> <span data-ttu-id="26ad4-155">Er is een aantal keren dat u bij een `Get-*` opdracht komt zonder een bijbehorende opdracht om dat item te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="26ad4-155">There are times that you'll come across a `Get-*` command without a corresponding command to modify that item.</span></span>
<span data-ttu-id="26ad4-156">Een methode kan vaak worden gebruikt om een actie uit te voeren die deze wijzigt.</span><span class="sxs-lookup"><span data-stu-id="26ad4-156">Often, a method can be used to perform an action that modifies it.</span></span> <span data-ttu-id="26ad4-157">De `Get-SqlAgentJob` cmdlet in de sqlserver Power shell-module is een goed voor beeld hiervan.</span><span class="sxs-lookup"><span data-stu-id="26ad4-157">The `Get-SqlAgentJob` cmdlet in the SqlServer PowerShell module is a good example of this.</span></span> <span data-ttu-id="26ad4-158">De module wordt geïnstalleerd als onderdeel van [SQL Server Management Studio (smss)][SMSS].</span><span class="sxs-lookup"><span data-stu-id="26ad4-158">The module installs as part of [SQL Server Management Studio (SMSS)][SMSS].</span></span> <span data-ttu-id="26ad4-159">Er bestaat geen bijbehorende `Set-*` cmdlet, maar een methode kan worden gebruikt om dezelfde taak te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="26ad4-159">No corresponding `Set-*` cmdlet exists, but a method can be used to complete the same task.</span></span>

<span data-ttu-id="26ad4-160">Een andere reden om op de hoogte te zijn van methoden is dat veel beginners aannemen dat destructieve wijzigingen niet met opdrachten kunnen worden aangebracht `Get-*` .</span><span class="sxs-lookup"><span data-stu-id="26ad4-160">Another reason to be aware of methods is that many beginners assume destructive changes can't be made with `Get-*` commands.</span></span> <span data-ttu-id="26ad4-161">Maar ze kunnen ernstige problemen veroorzaken als ze niet op de juiste wijze worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="26ad4-161">But they indeed can cause serious problems if used inappropriately.</span></span>

<span data-ttu-id="26ad4-162">Een betere optie is het gebruik van een cmdlet voor het uitvoeren van de actie als deze bestaat.</span><span class="sxs-lookup"><span data-stu-id="26ad4-162">A better option is to use a cmdlet to perform the action if one exists.</span></span> <span data-ttu-id="26ad4-163">Start de Windows Time-service, maar gebruik de cmdlet voor het starten van services.</span><span class="sxs-lookup"><span data-stu-id="26ad4-163">Go ahead and start the Windows Time service, except this time use the cmdlet for starting services.</span></span>

```powershell
Get-Service -Name w32time | Start-Service -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="26ad4-164">Standaard retourneert geen `Start-Service` resultaten zoals de start methode van `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="26ad4-164">By default, `Start-Service` doesn't return any results just like the start method of `Get-Service`.</span></span>
<span data-ttu-id="26ad4-165">Maar een van de voor delen van het gebruik van een cmdlet is dat vaak de cmdlet extra functionaliteit biedt die niet beschikbaar is met een methode.</span><span class="sxs-lookup"><span data-stu-id="26ad4-165">But one of the benefits of using a cmdlet is that many times the cmdlet offers additional functionality that isn't available with a method.</span></span> <span data-ttu-id="26ad4-166">In het vorige voor beeld is de para meter **PassThru** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="26ad4-166">In the previous example, the **PassThru** parameter was used.</span></span> <span data-ttu-id="26ad4-167">Dit veroorzaakt een cmdlet die Norma liter geen uitvoer produceert, voor het produceren van uitvoer.</span><span class="sxs-lookup"><span data-stu-id="26ad4-167">This causes a cmdlet that doesn't normally produce output, to produce output.</span></span>

<span data-ttu-id="26ad4-168">Wees voorzichtig met veronderstellingen over de uitvoer van een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="26ad4-168">Be careful with assumptions about the output of a cmdlet.</span></span> <span data-ttu-id="26ad4-169">We weten wat er gebeurt wanneer u dat gaat doen.</span><span class="sxs-lookup"><span data-stu-id="26ad4-169">We all know what happens when you assume things.</span></span> <span data-ttu-id="26ad4-170">Ik krijg informatie over het Power Shell-proces dat wordt uitgevoerd op de computer met de Windows 10-test omgeving.</span><span class="sxs-lookup"><span data-stu-id="26ad4-170">I'll retrieve information about the PowerShell process running on my Windows 10 lab environment computer.</span></span>

```powershell
Get-Process -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    922      48   107984     140552       2.84   9020   1 powershell

```

<span data-ttu-id="26ad4-171">Nu pipet u dezelfde opdracht voor Get-lid:</span><span class="sxs-lookup"><span data-stu-id="26ad4-171">Now I'll pipe that same command to Get-Member:</span></span>

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

<span data-ttu-id="26ad4-172">U ziet dat er meer eigenschappen worden vermeld dan standaard worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="26ad4-172">Notice that there are more properties listed than are displayed by default.</span></span> <span data-ttu-id="26ad4-173">Een aantal van de standaard eigenschappen die worden weer gegeven, worden niet weer geven als eigenschappen bij het weer geven van de resultaten van `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="26ad4-173">A number of the default properties displayed don't show up as properties when viewing the results of `Get-Member`.</span></span> <span data-ttu-id="26ad4-174">Dit komt doordat veel van de weer gegeven waarden, zoals `NPM(K)` , `PM(K)` , `WS(K)` en `CPU(s)` , berekende eigenschappen zijn.</span><span class="sxs-lookup"><span data-stu-id="26ad4-174">This is because many of the displayed values, such as `NPM(K)`, `PM(K)`, `WS(K)`, and `CPU(s)`, are calculated properties.</span></span> <span data-ttu-id="26ad4-175">Als u de werkelijke eigenschapnamen wilt bepalen, moet de opdracht worden gepiped naar `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="26ad4-175">To determine the actual property names, the command must be piped to `Get-Member`.</span></span>

<span data-ttu-id="26ad4-176">Als een opdracht geen uitvoer produceert, kan er geen pipeing op worden uitgevoerd `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="26ad4-176">If a command does not produce output, it can't be piped to `Get-Member`.</span></span> <span data-ttu-id="26ad4-177">Aangezien er geen `Start-Service` uitvoer wordt gemaakt, wordt er een fout gegenereerd wanneer u deze wilt door sluizen naar `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="26ad4-177">Since `Start-Service` doesn't produce any output by default, it generates an error when you try to pipe it to `Get-Member`.</span></span>

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

<span data-ttu-id="26ad4-178">De para meter **PassThru** kan worden opgegeven met de `Start-Service` cmdlet maken deze uitvoer, waardoor er `Get-Member` geen fout is opgetreden.</span><span class="sxs-lookup"><span data-stu-id="26ad4-178">The **PassThru** parameter can be specified with the `Start-Service` cmdlet make it produce output, which is then piped to `Get-Member` without error.</span></span>

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

<span data-ttu-id="26ad4-179">Om te worden gepiped naar `Get-Member` , moet een opdracht uitvoer op basis van een object opleveren.</span><span class="sxs-lookup"><span data-stu-id="26ad4-179">To be piped to `Get-Member`, a command must produce object-based output.</span></span>

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

<span data-ttu-id="26ad4-180">`Out-Host` schrijft rechtstreeks naar de Power shell-host, maar produceert geen op objecten gebaseerde uitvoer voor de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="26ad4-180">`Out-Host` writes directly to the PowerShell host, but it doesn't produce object-based output for the pipeline.</span></span> <span data-ttu-id="26ad4-181">Zodat deze niet kan worden gepiped `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="26ad4-181">So it can't be piped to `Get-Member`.</span></span>

## <a name="active-directory"></a><span data-ttu-id="26ad4-182">Active Directory</span><span class="sxs-lookup"><span data-stu-id="26ad4-182">Active Directory</span></span>

> [!NOTE]
> <span data-ttu-id="26ad4-183">De Remote Server Administration Tools die worden vermeld in de sectie vereisten van dit hoofd stuk zijn vereist om deze sectie te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="26ad4-183">The Remote Server Administration Tools listed in the requirements section of this chapter are required to complete this section.</span></span> <span data-ttu-id="26ad4-184">Zoals vermeld in de inleiding tot dit boek, moet uw computer met Windows 10 lab-omgeving ook lid zijn van het domein van de test omgeving.</span><span class="sxs-lookup"><span data-stu-id="26ad4-184">Also, as mentioned in the introduction to this book, your Windows 10 lab environment computer must be a member of the lab environment domain.</span></span>

<span data-ttu-id="26ad4-185">Gebruik `Get-Command` met de **module** parameter om te bepalen welke opdrachten zijn toegevoegd als onderdeel van de Active Directory Power shell-module toen de Remote Server Administration Tools werd geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="26ad4-185">Use `Get-Command` with the **Module** parameter to determine what commands were added as part of the ActiveDirectory PowerShell module when the remote server administration tools were installed.</span></span>

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

<span data-ttu-id="26ad4-186">Er zijn in totaal 147 opdrachten toegevoegd als onderdeel van de Active Directory Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="26ad4-186">A total of 147 commands were added as part of the ActiveDirectory PowerShell module.</span></span> <span data-ttu-id="26ad4-187">Sommige opdrachten van deze opdrachten retour neren standaard alleen een gedeelte van de beschik bare eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="26ad4-187">Some commands of these commands only return a portion of the available properties by default.</span></span>

<span data-ttu-id="26ad4-188">Hebt u iets anders genoteerd over de namen van de opdrachten in deze module?</span><span class="sxs-lookup"><span data-stu-id="26ad4-188">Did you notice anything different about the names of the commands in this module?</span></span> <span data-ttu-id="26ad4-189">Het gedeelte van de zelfstandig naam woord van de opdrachten bevat een AD-voor voegsel.</span><span class="sxs-lookup"><span data-stu-id="26ad4-189">The noun portion of the commands has an AD prefix.</span></span> <span data-ttu-id="26ad4-190">Dit is gebruikelijk om te zien wat de opdrachten van de meeste modules zijn.</span><span class="sxs-lookup"><span data-stu-id="26ad4-190">This is common to see on the commands of most modules.</span></span> <span data-ttu-id="26ad4-191">Het voor voegsel is ontworpen om naam conflicten te voor komen.</span><span class="sxs-lookup"><span data-stu-id="26ad4-191">The prefix is designed to help prevent naming conflicts.</span></span>

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

<span data-ttu-id="26ad4-192">Zelfs als u alleen vaguely vertrouwd bent met Active Directory, weet u waarschijnlijk dat een gebruikers account meer eigenschappen heeft dan in dit voor beeld wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="26ad4-192">Even if you're only vaguely familiar with Active Directory, you're probably aware that a user account has more properties than are shown in this example.</span></span>

<span data-ttu-id="26ad4-193">De `Get-ADUser` cmdlet heeft een **Eigenschappen** parameter die wordt gebruikt om de aanvullende (niet-standaard) eigenschappen op te geven die u wilt retour neren.</span><span class="sxs-lookup"><span data-stu-id="26ad4-193">The `Get-ADUser` cmdlet has a **Properties** parameter that is used to specify the additional (non-default) properties you want to return.</span></span> <span data-ttu-id="26ad4-194">Als u het Joker teken opgeeft, worden `*` alle geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="26ad4-194">Specifying the `*` wildcard character returns all of them.</span></span>

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

<span data-ttu-id="26ad4-195">Nu ziet u dat er meer lijkt.</span><span class="sxs-lookup"><span data-stu-id="26ad4-195">Now that looks more like it.</span></span>

<span data-ttu-id="26ad4-196">Kunt u een reden bedenken waarom de eigenschappen van een Active Directory gebruikers account standaard beperkt zijn?</span><span class="sxs-lookup"><span data-stu-id="26ad4-196">Can you think of a reason why the properties of an Active Directory user account would be so limited by default?</span></span> <span data-ttu-id="26ad4-197">Stel dat u elke eigenschap voor elk gebruikers account in uw productie Active Directory omgeving hebt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="26ad4-197">Imagine if you returned every property for every user account in your production Active Directory environment.</span></span> <span data-ttu-id="26ad4-198">Denk na over de prestatie vermindering die u zou kunnen veroorzaken, niet alleen voor de domein controllers zelf, maar ook voor uw netwerk.</span><span class="sxs-lookup"><span data-stu-id="26ad4-198">Think of the performance degradation that you could cause, not only to the domain controllers themselves, but also to your network.</span></span> <span data-ttu-id="26ad4-199">Het is twijfelt dat u elke eigenschap toch nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="26ad4-199">It's doubtful that you'll actually need every property anyway.</span></span> <span data-ttu-id="26ad4-200">Het retour neren van alle eigenschappen voor één gebruikers account is perfect acceptabel wanneer u probeert te bepalen welke eigenschappen er bestaan.</span><span class="sxs-lookup"><span data-stu-id="26ad4-200">Returning all of the properties for a single user account is perfectly acceptable when you're trying to determine what properties exist.</span></span>

<span data-ttu-id="26ad4-201">Het is niet ongebruikelijk om een opdracht meermaals uit te voeren wanneer het prototypet.</span><span class="sxs-lookup"><span data-stu-id="26ad4-201">It's not uncommon to run a command many times when prototyping it.</span></span> <span data-ttu-id="26ad4-202">Als u een enorme query wilt uitvoeren, voert u de query één keer uit en slaat u de resultaten op in een variabele.</span><span class="sxs-lookup"><span data-stu-id="26ad4-202">If you're going to perform some huge query, query it once and store the results in a variable.</span></span> <span data-ttu-id="26ad4-203">Werk vervolgens met de inhoud van de variabele in plaats van herhaaldelijk een duur query te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="26ad4-203">Then work with the contents of the variable instead of repeatedly using some expensive query.</span></span>

```powershell
$Users = Get-ADUser -Identity mike -Properties *
```

<span data-ttu-id="26ad4-204">Gebruik de inhoud van de `$Users` variabele in plaats van de vorige opdracht talrijke keer uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="26ad4-204">Use the contents of the `$Users` variable instead of running the previous command numerous times.</span></span>
<span data-ttu-id="26ad4-205">Houd er wel voor dat de inhoud van de variabele niet wordt bijgewerkt wanneer er wijzigingen worden aangebracht aan die gebruiker in Active Directory.</span><span class="sxs-lookup"><span data-stu-id="26ad4-205">Keep in mind that the contents of the variable aren't updated when changes are made to that user in Active Directory.</span></span>

<span data-ttu-id="26ad4-206">U kunt de variabele door sluizen `$Users` naar `Get-Member` om de beschik bare eigenschappen te detecteren.</span><span class="sxs-lookup"><span data-stu-id="26ad4-206">You could pipe the `$Users` variable to `Get-Member` to discover the available properties.</span></span>

```powershell
$Users | Get-Member
```

<span data-ttu-id="26ad4-207">Selecteer vervolgens de afzonderlijke eigenschappen van sluizen `$Users` naar `Select-Object` , zonder dat u meer dan één keer hoeft op te vragen Active Directory.</span><span class="sxs-lookup"><span data-stu-id="26ad4-207">Then select the individual properties by piping `$Users` to `Select-Object`, all without ever having to query Active Directory more than one time.</span></span>

```powershell
$Users | Select-Object -Property Name, LastLogonDate, LastBadPasswordAttempt
```

<span data-ttu-id="26ad4-208">Als u Active Directory meer dan een keer wilt zoeken, gebruikt u de para meter **Eigenschappen** om de niet-standaard eigenschappen op te geven die u wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="26ad4-208">If you are going to query Active Directory more than once, use the **Properties** parameter to specify any non-default properties you want.</span></span>

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

## <a name="summary"></a><span data-ttu-id="26ad4-209">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="26ad4-209">Summary</span></span>

<span data-ttu-id="26ad4-210">In dit hoofd stuk hebt u geleerd hoe u kunt bepalen welk type object een opdracht produceert, hoe u kunt bepalen welke eigenschappen en methoden beschikbaar zijn voor een opdracht en hoe u kunt werken met opdrachten die de eigenschappen die standaard worden geretourneerd, beperken.</span><span class="sxs-lookup"><span data-stu-id="26ad4-210">In this chapter, you've learned how to determine what type of object a command produces, how to determine what properties and methods are available for a command, and how to work with commands that limit the properties that are returned by default.</span></span>

## <a name="review"></a><span data-ttu-id="26ad4-211">Beoordelen</span><span class="sxs-lookup"><span data-stu-id="26ad4-211">Review</span></span>

1. <span data-ttu-id="26ad4-212">Welk type object `Get-Process` produceert de cmdlet?</span><span class="sxs-lookup"><span data-stu-id="26ad4-212">What type of object does the `Get-Process` cmdlet produce?</span></span>
1. <span data-ttu-id="26ad4-213">Hoe kunt u bepalen wat de beschik bare eigenschappen zijn voor een opdracht?</span><span class="sxs-lookup"><span data-stu-id="26ad4-213">How do you determine what the available properties are for a command?</span></span>
1. <span data-ttu-id="26ad4-214">Als er een opdracht bestaat voor het verkrijgen van iets, maar niet voor het instellen van hetzelfde, wat moet u controleren?</span><span class="sxs-lookup"><span data-stu-id="26ad4-214">If a command exists for getting something but not for setting the same thing, what should you check for?</span></span>
1. <span data-ttu-id="26ad4-215">Hoe kunnen bepaalde opdrachten die geen uitvoer produceren standaard worden gemaakt voor het produceren van uitvoer?</span><span class="sxs-lookup"><span data-stu-id="26ad4-215">How can certain commands that don't produce output by default be made to produce output?</span></span>
1. <span data-ttu-id="26ad4-216">Als u wilt werken met de resultaten van een opdracht die een enorme hoeveelheid uitvoer produceert, wat moet u overwegen?</span><span class="sxs-lookup"><span data-stu-id="26ad4-216">If you're going to be working with the results of a command that produces an enormous amount of output, what should you consider doing?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="26ad4-217">Aanbevolen Lees bewerkingen</span><span class="sxs-lookup"><span data-stu-id="26ad4-217">Recommended Reading</span></span>

- <span data-ttu-id="26ad4-218">[Get-member][]</span><span class="sxs-lookup"><span data-stu-id="26ad4-218">[Get-Member][]</span></span>
- <span data-ttu-id="26ad4-219">[Objectstructuur weergeven (Get-Member)][]</span><span class="sxs-lookup"><span data-stu-id="26ad4-219">[Viewing Object Structure (Get-Member)][]</span></span>
- <span data-ttu-id="26ad4-220">[about_Objects][]</span><span class="sxs-lookup"><span data-stu-id="26ad4-220">[about_Objects][]</span></span>
- <span data-ttu-id="26ad4-221">[about_Properties][]</span><span class="sxs-lookup"><span data-stu-id="26ad4-221">[about_Properties][]</span></span>
- <span data-ttu-id="26ad4-222">[about_Methods][]</span><span class="sxs-lookup"><span data-stu-id="26ad4-222">[about_Methods][]</span></span>
- <span data-ttu-id="26ad4-223">[Geen Power shell-cmdlet om iets te starten of te stoppen? Vergeet niet om te controleren op methoden op de Get-cmdlets][use-methods]</span><span class="sxs-lookup"><span data-stu-id="26ad4-223">[No PowerShell Cmdlet to Start or Stop Something? Don’t Forget to Check for Methods on the Get Cmdlets][use-methods]</span></span>

<!-- link references -->
[RSAT voor Windows]: https://support.microsoft.com/help/2693643
[RSAT for Windows]: https://support.microsoft.com/help/2693643
[Windows-beheer modules]: /powershell/scripting/whats-new/module-compatibility#windows-management-modules
[Windows Management modules]: /powershell/scripting/whats-new/module-compatibility#windows-management-modules
[Get-member]: /powershell/module/microsoft.powershell.utility/get-member
[Get-Member]: /powershell/module/microsoft.powershell.utility/get-member
[Objectstructuur weergeven (Get-Member)]: /powershell/scripting/samples/viewing-object-structure--get-member-
[Viewing Object Structure (Get-Member)]: /powershell/scripting/samples/viewing-object-structure--get-member-
[about_Objects]: /powershell/module/microsoft.powershell.core/about/about_objects
[about_Properties]: /powershell/module/microsoft.powershell.core/about/about_properties
[about_Methods]: /powershell/module/microsoft.powershell.core/about/about_methods
[use-methods]: https://mikefrobbins.com/2016/12/15/no-powershell-cmdlet-to-start-or-stop-something-dont-forget-to-check-for-methods-on-the-get-cmdlets/
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
