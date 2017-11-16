---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Met behulp van statische klassen en methoden
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: fe41c7d6b45564e7b5bc2b922a18587c9745e26d
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="using-static-classes-and-methods"></a><span data-ttu-id="725e5-103">Met behulp van statische klassen en methoden</span><span class="sxs-lookup"><span data-stu-id="725e5-103">Using Static Classes and Methods</span></span>
<span data-ttu-id="725e5-104">Niet alle .NET Framework-klassen kunnen worden gemaakt met behulp van **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="725e5-104">Not all .NET Framework classes can be created by using **New-Object**.</span></span> <span data-ttu-id="725e5-105">Bijvoorbeeld, als u probeert te maken van een **System.Environment** of een **System.Math** object met **New-Object**, krijgt u de volgende foutberichten weergegeven:</span><span class="sxs-lookup"><span data-stu-id="725e5-105">For example, if you try to create a **System.Environment** or a **System.Math** object with **New-Object**, you will get the following error messages:</span></span>

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

<span data-ttu-id="725e5-106">Deze fouten optreden omdat er geen mogelijkheid om te maken van een nieuw object van deze klassen.</span><span class="sxs-lookup"><span data-stu-id="725e5-106">These errors occur because there is no way to create a new object from these classes.</span></span> <span data-ttu-id="725e5-107">Deze klassen zijn verwijzing tapewisselaars methoden en eigenschappen die de status niet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="725e5-107">These classes are reference libraries of methods and properties that do not change state.</span></span> <span data-ttu-id="725e5-108">U hoeft niet om ze te maken, u ze gewoon gebruiken.</span><span class="sxs-lookup"><span data-stu-id="725e5-108">You don't need to create them, you simply use them.</span></span> <span data-ttu-id="725e5-109">Klassen en -methoden zoals deze heten *statische klassen* omdat ze niet worden gemaakt, verwijderd of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="725e5-109">Classes and methods such as these are called *static classes* because they are not created, destroyed, or changed.</span></span> <span data-ttu-id="725e5-110">We bieden voorbeelden die statische klassen gebruiken om dit te wissen.</span><span class="sxs-lookup"><span data-stu-id="725e5-110">To make this clear we will provide examples that use static classes.</span></span>

### <a name="getting-environment-data-with-systemenvironment"></a><span data-ttu-id="725e5-111">Ophalen van omgevingsgegevens met System.Environment</span><span class="sxs-lookup"><span data-stu-id="725e5-111">Getting Environment Data with System.Environment</span></span>
<span data-ttu-id="725e5-112">Normaal gesproken is de eerste stap bij het werken met een Windows PowerShell-object lid zijn van Get gebruiken om erachter te komen welke leden bevat.</span><span class="sxs-lookup"><span data-stu-id="725e5-112">Usually, the first step in working with an object in Windows PowerShell is to use Get-Member to find out what members it contains.</span></span> <span data-ttu-id="725e5-113">Met statische klassen is het proces enigszins verschillen, omdat de werkelijke klasse geen object is.</span><span class="sxs-lookup"><span data-stu-id="725e5-113">With static classes, the process is a little different because the actual class is not an object.</span></span>

#### <a name="referring-to-the-static-systemenvironment-class"></a><span data-ttu-id="725e5-114">Verwijst naar de statische System.Environment-klasse</span><span class="sxs-lookup"><span data-stu-id="725e5-114">Referring to the Static System.Environment Class</span></span>
<span data-ttu-id="725e5-115">U kunt verwijzen naar een statische klasse door de naam van de klasse vierkante haken.</span><span class="sxs-lookup"><span data-stu-id="725e5-115">You can refer to a static class by surrounding the class name with square brackets.</span></span> <span data-ttu-id="725e5-116">Bijvoorbeeld, u kunt verwijzen naar **System.Environment** door de naam tussen vierkante haakjes te typen.</span><span class="sxs-lookup"><span data-stu-id="725e5-116">For example, you can refer to **System.Environment** by typing the name within brackets.</span></span> <span data-ttu-id="725e5-117">Hiermee geeft u de informatie over een aantal algemene typen:</span><span class="sxs-lookup"><span data-stu-id="725e5-117">Doing so displays some generic type information:</span></span>

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> <span data-ttu-id="725e5-118">Zoals we eerder vermeld, Windows PowerShell automatisch voegt u toe aan elke '**System.**'</span><span class="sxs-lookup"><span data-stu-id="725e5-118">As we mentioned previously, Windows PowerShell automatically prepends '**System.**'</span></span> <span data-ttu-id="725e5-119">namen van typen wanneer u **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="725e5-119">to type names when you use **New-Object**.</span></span> <span data-ttu-id="725e5-120">Hetzelfde geldt er gebeurt wanneer u een tussen haakjes typenaam, zodat u kunt opgeven  **\[System.Environment]** als  **\[omgeving]**.</span><span class="sxs-lookup"><span data-stu-id="725e5-120">The same thing happens when using a bracketed type name, so you can specify **\[System.Environment]** as **\[Environment]**.</span></span>

<span data-ttu-id="725e5-121">De **System.Environment** klasse bevat algemene informatie over de werkomgeving voor het huidige proces powershell.exe is wanneer u in Windows PowerShell werkt.</span><span class="sxs-lookup"><span data-stu-id="725e5-121">The **System.Environment** class contains general information about the working environment for the current process, which is powershell.exe when working within Windows PowerShell.</span></span>

<span data-ttu-id="725e5-122">Als u details wilt weergeven van deze klasse door te typen proberen  **\[System.Environment] | Get-lid**, het objecttype wordt gemeld dat **System.RuntimeType** , niet **System.Environment**:</span><span class="sxs-lookup"><span data-stu-id="725e5-122">If you try to view details of this class by typing **\[System.Environment] | Get-Member**, the object type is reported as being **System.RuntimeType** , not **System.Environment**:</span></span>

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

<span data-ttu-id="725e5-123">Als u wilt weergeven statische leden met Get-lid, geef de **statische** parameter:</span><span class="sxs-lookup"><span data-stu-id="725e5-123">To view static members with Get-Member, specify the **Static** parameter:</span></span>

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

<span data-ttu-id="725e5-124">We kunnen nu eigenschappen om weer te geven van System.Environment selecteren.</span><span class="sxs-lookup"><span data-stu-id="725e5-124">We can now select properties to view from System.Environment.</span></span>

#### <a name="displaying-static-properties-of-systemenvironment"></a><span data-ttu-id="725e5-125">Statische eigenschappen van System.Environment weer te geven</span><span class="sxs-lookup"><span data-stu-id="725e5-125">Displaying Static Properties of System.Environment</span></span>
<span data-ttu-id="725e5-126">De eigenschappen van System.Environment ook statisch zijn en moeten worden opgegeven in een andere manier dan normale eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="725e5-126">The properties of System.Environment are also static, and must be specified in a different way than normal properties.</span></span> <span data-ttu-id="725e5-127">We gebruiken **::** om aan te geven in Windows PowerShell die we willen werken met een statische methode of eigenschap.</span><span class="sxs-lookup"><span data-stu-id="725e5-127">We use **::** to indicate to Windows PowerShell that we want to work with a static method or property.</span></span> <span data-ttu-id="725e5-128">Overzicht van de opdracht die is gebruikt voor het starten van Windows PowerShell, controleren we de **CommandLine** eigenschap door te typen:</span><span class="sxs-lookup"><span data-stu-id="725e5-128">To see the command that was used to launch Windows PowerShell, we check the **CommandLine** property by typing:</span></span>

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

<span data-ttu-id="725e5-129">Als u wilt controleren de versie van het besturingssysteem, de eigenschap OSVersion wordt weergegeven door te typen:</span><span class="sxs-lookup"><span data-stu-id="725e5-129">To check the operating system version, display the OSVersion property by typing:</span></span>

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

<span data-ttu-id="725e5-130">Kunnen we controleren of de computer wordt afgesloten door weer te geven de **HasShutdownStarted** eigenschap:</span><span class="sxs-lookup"><span data-stu-id="725e5-130">We can check whether the computer is in the process of shutting down by displaying the **HasShutdownStarted** property:</span></span>

```
PS> [System.Environment]::HasShutdownStarted
False
```

### <a name="doing-math-with-systemmath"></a><span data-ttu-id="725e5-131">Math met System.Math doen</span><span class="sxs-lookup"><span data-stu-id="725e5-131">Doing Math with System.Math</span></span>
<span data-ttu-id="725e5-132">De statische klasse System.Math is nuttig voor het uitvoeren van sommige rekenkundige bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="725e5-132">The System.Math static class is useful for performing some mathematical operations.</span></span> <span data-ttu-id="725e5-133">De belangrijke leden van **System.Math** zijn voornamelijk methoden, waarin kunnen worden weergegeven met behulp van **Get-lid**.</span><span class="sxs-lookup"><span data-stu-id="725e5-133">The important members of **System.Math** are mostly methods, which we can display by using **Get-Member**.</span></span>

> [!NOTE]
> <span data-ttu-id="725e5-134">System.Math verschillende methoden met dezelfde naam heeft, maar ze elkaar worden onderscheiden door het type van hun parameters.</span><span class="sxs-lookup"><span data-stu-id="725e5-134">System.Math has several methods with the same name, but they are distinguished by the type of their parameters.</span></span>

<span data-ttu-id="725e5-135">Typ de volgende opdracht voor het weergeven van de methoden van de **System.Math** klasse.</span><span class="sxs-lookup"><span data-stu-id="725e5-135">Type the following command to list the methods of the **System.Math** class.</span></span>

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

<span data-ttu-id="725e5-136">Hiermee worden verschillende methoden voor wiskundige weergegeven.</span><span class="sxs-lookup"><span data-stu-id="725e5-136">This displays several mathematical methods.</span></span> <span data-ttu-id="725e5-137">Hier volgt een lijst met opdrachten die laten zien hoe u enkele algemene methoden werken:</span><span class="sxs-lookup"><span data-stu-id="725e5-137">Here is a list of commands that demonstrate how some of the common methods work:</span></span>

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

