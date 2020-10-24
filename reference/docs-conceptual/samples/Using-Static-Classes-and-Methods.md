---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Statische klassen en methoden gebruiken
description: In dit artikel wordt uitgelegd hoe u de eigenschappen en methoden van .NET statische klassen identificeert en gebruikt.
ms.openlocfilehash: 2e83fe442f7b3fdf62ceaab587450251ac4e7958
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501249"
---
# <a name="using-static-classes-and-methods"></a><span data-ttu-id="c4214-104">Statische klassen en methoden gebruiken</span><span class="sxs-lookup"><span data-stu-id="c4214-104">Using Static Classes and Methods</span></span>

<span data-ttu-id="c4214-105">Niet alle .NET Framework klassen kunnen worden gemaakt met behulp van **New-object**.</span><span class="sxs-lookup"><span data-stu-id="c4214-105">Not all .NET Framework classes can be created by using **New-Object**.</span></span> <span data-ttu-id="c4214-106">Als u bijvoorbeeld probeert een **System. Environment** -of **System. math** -object te maken met **Nieuw-object**, worden de volgende fout berichten weer geven:</span><span class="sxs-lookup"><span data-stu-id="c4214-106">For example, if you try to create a **System.Environment** or a **System.Math** object with **New-Object**, you will get the following error messages:</span></span>

```
PS> New-Object System.Environment
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Environment.
At line:1 char:11
+ New-Object  <<<< System.Environment

PS> New-Object System.Math
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Math.
At line:1 char:11
+ New-Object  <<<< System.Math
```

<span data-ttu-id="c4214-107">Deze fouten treden op omdat er geen manier is om een nieuw object te maken op basis van deze klassen.</span><span class="sxs-lookup"><span data-stu-id="c4214-107">These errors occur because there is no way to create a new object from these classes.</span></span> <span data-ttu-id="c4214-108">Deze klassen zijn referentie bibliotheken met methoden en eigenschappen die de status niet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="c4214-108">These classes are reference libraries of methods and properties that do not change state.</span></span> <span data-ttu-id="c4214-109">U hoeft deze niet te maken, maar u kunt ze gewoon gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c4214-109">You don't need to create them, you simply use them.</span></span> <span data-ttu-id="c4214-110">Klassen en methoden zoals deze worden *statische klassen* genoemd, omdat ze niet zijn gemaakt, vernietigd of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c4214-110">Classes and methods such as these are called *static classes* because they are not created, destroyed, or changed.</span></span> <span data-ttu-id="c4214-111">Om dit duidelijk te maken, bieden we voor beelden die gebruikmaken van statische klassen.</span><span class="sxs-lookup"><span data-stu-id="c4214-111">To make this clear we will provide examples that use static classes.</span></span>

## <a name="getting-environment-data-with-systemenvironment"></a><span data-ttu-id="c4214-112">Omgevings gegevens ophalen met System. Environment</span><span class="sxs-lookup"><span data-stu-id="c4214-112">Getting Environment Data with System.Environment</span></span>

<span data-ttu-id="c4214-113">Normaal gesp roken is de eerste stap bij het werken met een object in Windows Power shell uit het gebruik van Get-Member om erachter te komen welke leden de app bevat.</span><span class="sxs-lookup"><span data-stu-id="c4214-113">Usually, the first step in working with an object in Windows PowerShell is to use Get-Member to find out what members it contains.</span></span> <span data-ttu-id="c4214-114">Bij statische klassen is het proces iets anders omdat de daad werkelijke klasse geen object is.</span><span class="sxs-lookup"><span data-stu-id="c4214-114">With static classes, the process is a little different because the actual class is not an object.</span></span>

### <a name="referring-to-the-static-systemenvironment-class"></a><span data-ttu-id="c4214-115">Verwijzen naar de klasse static System. Environment</span><span class="sxs-lookup"><span data-stu-id="c4214-115">Referring to the Static System.Environment Class</span></span>

<span data-ttu-id="c4214-116">U kunt naar een statische klasse verwijzen door de naam van de klasse te omgeven door rechte haken.</span><span class="sxs-lookup"><span data-stu-id="c4214-116">You can refer to a static class by surrounding the class name with square brackets.</span></span> <span data-ttu-id="c4214-117">U kunt bijvoorbeeld verwijzen naar **System. Environment** door de naam tussen vier Kante haken te typen.</span><span class="sxs-lookup"><span data-stu-id="c4214-117">For example, you can refer to **System.Environment** by typing the name within brackets.</span></span> <span data-ttu-id="c4214-118">Dit geeft een aantal algemene type gegevens weer:</span><span class="sxs-lookup"><span data-stu-id="c4214-118">Doing so displays some generic type information:</span></span>

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> <span data-ttu-id="c4214-119">Zoals eerder vermeld, voegt Windows Power shell automatisch '**System.**' toe.</span><span class="sxs-lookup"><span data-stu-id="c4214-119">As we mentioned previously, Windows PowerShell automatically prepends '**System.**'</span></span> <span data-ttu-id="c4214-120">Als u namen wilt typen wanneer u **Nieuw-object**gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c4214-120">to type names when you use **New-Object**.</span></span> <span data-ttu-id="c4214-121">Hetzelfde gebeurt wanneer u een type naam tussen haakjes gebruikt, zodat u \*\* \[ System. Environment]\*\* als \*\* \[ omgeving\*\*kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="c4214-121">The same thing happens when using a bracketed type name, so you can specify **\[System.Environment]** as **\[Environment]**.</span></span>

<span data-ttu-id="c4214-122">De klasse **System. Environment** bevat algemene informatie over de werk omgeving voor het huidige proces, dat powershell.exe wanneer u werkt in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="c4214-122">The **System.Environment** class contains general information about the working environment for the current process, which is powershell.exe when working within Windows PowerShell.</span></span>

<span data-ttu-id="c4214-123">Als u de details van deze klasse wilt bekijken door \*\* \[ System. Environment te typen] | Get-member\*\*, het object type wordt gerapporteerd als **System. RuntimeType** , niet **System. Environment**:</span><span class="sxs-lookup"><span data-stu-id="c4214-123">If you try to view details of this class by typing **\[System.Environment] | Get-Member**, the object type is reported as being **System.RuntimeType** , not **System.Environment**:</span></span>

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

<span data-ttu-id="c4214-124">Als u statische leden wilt weer geven met Get-member, geeft u de **statische** para meter op:</span><span class="sxs-lookup"><span data-stu-id="c4214-124">To view static members with Get-Member, specify the **Static** parameter:</span></span>

```
PS> [System.Environment] | Get-Member -Static

   TypeName: System.Environment

Name                       MemberType Definition
----                       ---------- ----------
Equals                     Method     static System.Boolean Equals(Object ob...
Exit                       Method     static System.Void Exit(Int32 exitCode)
...
CommandLine                Property   static System.String CommandLine {get;}
CurrentDirectory           Property   static System.String CurrentDirectory ...
ExitCode                   Property   static System.Int32 ExitCode {get;set;}
HasShutdownStarted         Property   static System.Boolean HasShutdownStart...
MachineName                Property   static System.String MachineName {get;}
NewLine                    Property   static System.String NewLine {get;}
OSVersion                  Property   static System.OperatingSystem OSVersio...
ProcessorCount             Property   static System.Int32 ProcessorCount {get;}
StackTrace                 Property   static System.String StackTrace {get;}
SystemDirectory            Property   static System.String SystemDirectory {...
TickCount                  Property   static System.Int32 TickCount {get;}
UserDomainName             Property   static System.String UserDomainName {g...
UserInteractive            Property   static System.Boolean UserInteractive ...
UserName                   Property   static System.String UserName {get;}
Version                    Property   static System.Version Version {get;}
WorkingSet                 Property   static System.Int64 WorkingSet {get;}
TickCount                               ExitCode
```

<span data-ttu-id="c4214-125">U kunt nu eigenschappen selecteren om uit System. Environment weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c4214-125">We can now select properties to view from System.Environment.</span></span>

### <a name="displaying-static-properties-of-systemenvironment"></a><span data-ttu-id="c4214-126">Statische eigenschappen van System. Environment weer geven</span><span class="sxs-lookup"><span data-stu-id="c4214-126">Displaying Static Properties of System.Environment</span></span>

<span data-ttu-id="c4214-127">De eigenschappen van System. Environment zijn ook statisch en moeten op een andere manier worden opgegeven dan de normale eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="c4214-127">The properties of System.Environment are also static, and must be specified in a different way than normal properties.</span></span> <span data-ttu-id="c4214-128">We gebruiken **::** om aan te geven dat Windows Power shell moet werken met een statische methode of eigenschap.</span><span class="sxs-lookup"><span data-stu-id="c4214-128">We use **::** to indicate to Windows PowerShell that we want to work with a static method or property.</span></span> <span data-ttu-id="c4214-129">Als u de opdracht wilt zien die is gebruikt om Windows Power shell te starten, wordt de eigenschap **commandline** gecontroleerd door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="c4214-129">To see the command that was used to launch Windows PowerShell, we check the **CommandLine** property by typing:</span></span>

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

<span data-ttu-id="c4214-130">Als u de versie van het besturings systeem wilt controleren, geeft u de eigenschap onproperty weer door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="c4214-130">To check the operating system version, display the OSVersion property by typing:</span></span>

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

<span data-ttu-id="c4214-131">We kunnen controleren of de computer bezig is met afsluiten door de eigenschap **HasShutdownStarted** weer te geven:</span><span class="sxs-lookup"><span data-stu-id="c4214-131">We can check whether the computer is in the process of shutting down by displaying the **HasShutdownStarted** property:</span></span>

```
PS> [System.Environment]::HasShutdownStarted
False
```

## <a name="doing-math-with-systemmath"></a><span data-ttu-id="c4214-132">Wiskunde uitvoeren met System. math</span><span class="sxs-lookup"><span data-stu-id="c4214-132">Doing Math with System.Math</span></span>

<span data-ttu-id="c4214-133">De statische klasse System. Math is handig voor het uitvoeren van een aantal reken kundige bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="c4214-133">The System.Math static class is useful for performing some mathematical operations.</span></span> <span data-ttu-id="c4214-134">De belang rijke leden van **System. math** worden voornamelijk beschreven, die kunnen worden weer gegeven met behulp van **Get-member**.</span><span class="sxs-lookup"><span data-stu-id="c4214-134">The important members of **System.Math** are mostly methods, which we can display by using **Get-Member**.</span></span>

> [!NOTE]
> <span data-ttu-id="c4214-135">System. math heeft verschillende methoden met dezelfde naam, maar ze worden onderscheiden door het type van de bijbehorende para meters.</span><span class="sxs-lookup"><span data-stu-id="c4214-135">System.Math has several methods with the same name, but they are distinguished by the type of their parameters.</span></span>

<span data-ttu-id="c4214-136">Typ de volgende opdracht om de methoden van de klasse **System. math** weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c4214-136">Type the following command to list the methods of the **System.Math** class.</span></span>

```
PS> [System.Math] | Get-Member -Static -MemberType Methods

   TypeName: System.Math

Name            MemberType Definition
----            ---------- ----------
Abs             Method     static System.Single Abs(Single value), static Sy...
Acos            Method     static System.Double Acos(Double d)
Asin            Method     static System.Double Asin(Double d)
Atan            Method     static System.Double Atan(Double d)
Atan2           Method     static System.Double Atan2(Double y, Double x)
BigMul          Method     static System.Int64 BigMul(Int32 a, Int32 b)
Ceiling         Method     static System.Double Ceiling(Double a), static Sy...
Cos             Method     static System.Double Cos(Double d)
Cosh            Method     static System.Double Cosh(Double value)
DivRem          Method     static System.Int32 DivRem(Int32 a, Int32 b, Int3...
Equals          Method     static System.Boolean Equals(Object objA, Object ...
Exp             Method     static System.Double Exp(Double d)
Floor           Method     static System.Double Floor(Double d), static Syst...
IEEERemainder   Method     static System.Double IEEERemainder(Double x, Doub...
Log             Method     static System.Double Log(Double d), static System...
Log10           Method     static System.Double Log10(Double d)
Max             Method     static System.SByte Max(SByte val1, SByte val2), ...
Min             Method     static System.SByte Min(SByte val1, SByte val2), ...
Pow             Method     static System.Double Pow(Double x, Double y)
ReferenceEquals Method     static System.Boolean ReferenceEquals(Object objA...
Round           Method     static System.Double Round(Double a), static Syst...
Sign            Method     static System.Int32 Sign(SByte value), static Sys...
Sin             Method     static System.Double Sin(Double a)
Sinh            Method     static System.Double Sinh(Double value)
Sqrt            Method     static System.Double Sqrt(Double d)
Tan             Method     static System.Double Tan(Double a)
Tanh            Method     static System.Double Tanh(Double value)
Truncate        Method     static System.Decimal Truncate(Decimal d), static...
```

<span data-ttu-id="c4214-137">Er worden verschillende Mathematische methoden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c4214-137">This displays several mathematical methods.</span></span> <span data-ttu-id="c4214-138">Hier volgt een lijst met opdrachten die laten zien hoe sommige algemene methoden werken:</span><span class="sxs-lookup"><span data-stu-id="c4214-138">Here is a list of commands that demonstrate how some of the common methods work:</span></span>

```
PS> [System.Math]::Sqrt(9)
3
PS> [System.Math]::Pow(2,3)
8
PS> [System.Math]::Floor(3.3)
3
PS> [System.Math]::Floor(-3.3)
-4
PS> [System.Math]::Ceiling(3.3)
4
PS> [System.Math]::Ceiling(-3.3)
-3
PS> [System.Math]::Max(2,7)
7
PS> [System.Math]::Min(2,7)
2
PS> [System.Math]::Truncate(9.3)
9
PS> [System.Math]::Truncate(-9.3)
-9
```
