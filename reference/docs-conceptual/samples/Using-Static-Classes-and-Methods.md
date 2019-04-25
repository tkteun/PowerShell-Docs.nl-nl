---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Statische klassen en methoden gebruiken
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: e4caff63a1ec7295b6fe450c2915baf0cc7e31af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086003"
---
# <a name="using-static-classes-and-methods"></a><span data-ttu-id="b3916-103">Statische klassen en methoden gebruiken</span><span class="sxs-lookup"><span data-stu-id="b3916-103">Using Static Classes and Methods</span></span>

<span data-ttu-id="b3916-104">Niet alle .NET Framework-klassen kunnen worden gemaakt met behulp van **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="b3916-104">Not all .NET Framework classes can be created by using **New-Object**.</span></span> <span data-ttu-id="b3916-105">Bijvoorbeeld, als u probeert te maken een **System.Environment** of een **System.Math** object met **New-Object**, krijgt u de volgende foutberichten:</span><span class="sxs-lookup"><span data-stu-id="b3916-105">For example, if you try to create a **System.Environment** or a **System.Math** object with **New-Object**, you will get the following error messages:</span></span>

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

<span data-ttu-id="b3916-106">Deze fouten zich voordoen als er geen manier om te maken van een nieuw object van deze klassen.</span><span class="sxs-lookup"><span data-stu-id="b3916-106">These errors occur because there is no way to create a new object from these classes.</span></span> <span data-ttu-id="b3916-107">Deze klassen zijn naslagbibliotheken methoden en eigenschappen die de status niet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="b3916-107">These classes are reference libraries of methods and properties that do not change state.</span></span> <span data-ttu-id="b3916-108">U hoeft te maken, u deze gewoon gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b3916-108">You don't need to create them, you simply use them.</span></span> <span data-ttu-id="b3916-109">Klassen en methoden, zoals deze heten *statische klassen* omdat ze niet worden gemaakt, verwijderd of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b3916-109">Classes and methods such as these are called *static classes* because they are not created, destroyed, or changed.</span></span> <span data-ttu-id="b3916-110">We bieden voorbeelden die statische klassen gebruiken om dit te wissen.</span><span class="sxs-lookup"><span data-stu-id="b3916-110">To make this clear we will provide examples that use static classes.</span></span>

## <a name="getting-environment-data-with-systemenvironment"></a><span data-ttu-id="b3916-111">Ophalen van omgevingsgegevens met System.Environment</span><span class="sxs-lookup"><span data-stu-id="b3916-111">Getting Environment Data with System.Environment</span></span>

<span data-ttu-id="b3916-112">De eerste stap bij het werken met een object in Windows PowerShell is meestal, Get-Member gebruiken om erachter te komen welke leden bevat.</span><span class="sxs-lookup"><span data-stu-id="b3916-112">Usually, the first step in working with an object in Windows PowerShell is to use Get-Member to find out what members it contains.</span></span> <span data-ttu-id="b3916-113">Door statische klassen is het proces enigszins anders, omdat de werkelijke klasse niet een object is.</span><span class="sxs-lookup"><span data-stu-id="b3916-113">With static classes, the process is a little different because the actual class is not an object.</span></span>

### <a name="referring-to-the-static-systemenvironment-class"></a><span data-ttu-id="b3916-114">Verwijst naar de statische System.Environment-klasse</span><span class="sxs-lookup"><span data-stu-id="b3916-114">Referring to the Static System.Environment Class</span></span>

<span data-ttu-id="b3916-115">U kunt verwijzen naar een statische klasse door de naam van de klasse tussen vierkante haken staan.</span><span class="sxs-lookup"><span data-stu-id="b3916-115">You can refer to a static class by surrounding the class name with square brackets.</span></span> <span data-ttu-id="b3916-116">Bijvoorbeeld, u kunt verwijzen naar **System.Environment** door de naam tussen vierkante haken te typen.</span><span class="sxs-lookup"><span data-stu-id="b3916-116">For example, you can refer to **System.Environment** by typing the name within brackets.</span></span> <span data-ttu-id="b3916-117">Hiermee geeft u enkele algemene informatie over:</span><span class="sxs-lookup"><span data-stu-id="b3916-117">Doing so displays some generic type information:</span></span>

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> <span data-ttu-id="b3916-118">Zoals we eerder is vermeld, Windows PowerShell automatisch voegt u toe aan elke '**System.**'</span><span class="sxs-lookup"><span data-stu-id="b3916-118">As we mentioned previously, Windows PowerShell automatically prepends '**System.**'</span></span> <span data-ttu-id="b3916-119">namen van typen wanneer u **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="b3916-119">to type names when you use **New-Object**.</span></span> <span data-ttu-id="b3916-120">Hetzelfde gebeurt er wanneer u een typenaam die tussen haakjes, zodat u kunt opgeven aan welke  **\[System.Environment]** als  **\[omgeving]**.</span><span class="sxs-lookup"><span data-stu-id="b3916-120">The same thing happens when using a bracketed type name, so you can specify **\[System.Environment]** as **\[Environment]**.</span></span>

<span data-ttu-id="b3916-121">De **System.Environment** klasse bevat algemene informatie over de werkomgeving voor het huidige proces powershell.exe is bij het werken in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3916-121">The **System.Environment** class contains general information about the working environment for the current process, which is powershell.exe when working within Windows PowerShell.</span></span>

<span data-ttu-id="b3916-122">Als u probeert details van deze klasse bekijken door te typen  **\[System.Environment] | Get-Member**, het objecttype wordt gerapporteerd als zijnde **System.RuntimeType** , niet **System.Environment**:</span><span class="sxs-lookup"><span data-stu-id="b3916-122">If you try to view details of this class by typing **\[System.Environment] | Get-Member**, the object type is reported as being **System.RuntimeType** , not **System.Environment**:</span></span>

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

<span data-ttu-id="b3916-123">Als u statische leden met Get-Member, geef de **statische** parameter:</span><span class="sxs-lookup"><span data-stu-id="b3916-123">To view static members with Get-Member, specify the **Static** parameter:</span></span>

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

<span data-ttu-id="b3916-124">We kunnen nu eigenschappen om weer te geven van System.Environment selecteren.</span><span class="sxs-lookup"><span data-stu-id="b3916-124">We can now select properties to view from System.Environment.</span></span>

### <a name="displaying-static-properties-of-systemenvironment"></a><span data-ttu-id="b3916-125">Statische eigenschappen van System.Environment weergeven</span><span class="sxs-lookup"><span data-stu-id="b3916-125">Displaying Static Properties of System.Environment</span></span>

<span data-ttu-id="b3916-126">De eigenschappen van System.Environment ook statisch zijn en moeten worden opgegeven in een andere manier dan normaal eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="b3916-126">The properties of System.Environment are also static, and must be specified in a different way than normal properties.</span></span> <span data-ttu-id="b3916-127">We gebruiken **::** om aan te geven aan de Windows PowerShell die we willen werken met een statische methode of eigenschap.</span><span class="sxs-lookup"><span data-stu-id="b3916-127">We use **::** to indicate to Windows PowerShell that we want to work with a static method or property.</span></span> <span data-ttu-id="b3916-128">Als u wilt zien van de opdracht die is gebruikt voor het starten van Windows PowerShell, controleren we de **CommandLine** eigenschap door te typen:</span><span class="sxs-lookup"><span data-stu-id="b3916-128">To see the command that was used to launch Windows PowerShell, we check the **CommandLine** property by typing:</span></span>

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

<span data-ttu-id="b3916-129">Om te controleren of de versie van het besturingssysteem, de eigenschap OSVersion wordt weergegeven door te typen:</span><span class="sxs-lookup"><span data-stu-id="b3916-129">To check the operating system version, display the OSVersion property by typing:</span></span>

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

<span data-ttu-id="b3916-130">Kunnen we uiteraard controleren of de computer wordt afgesloten door weer te geven de **HasShutdownStarted** eigenschap:</span><span class="sxs-lookup"><span data-stu-id="b3916-130">We can check whether the computer is in the process of shutting down by displaying the **HasShutdownStarted** property:</span></span>

```
PS> [System.Environment]::HasShutdownStarted
False
```

## <a name="doing-math-with-systemmath"></a><span data-ttu-id="b3916-131">Math met System.Math doen</span><span class="sxs-lookup"><span data-stu-id="b3916-131">Doing Math with System.Math</span></span>

<span data-ttu-id="b3916-132">De statische klasse System.Math is handig voor het uitvoeren van enkele wiskundige bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="b3916-132">The System.Math static class is useful for performing some mathematical operations.</span></span> <span data-ttu-id="b3916-133">De belangrijke leden van **System.Math** zijn voornamelijk methoden, die we weergeven met behulp van kunnen **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="b3916-133">The important members of **System.Math** are mostly methods, which we can display by using **Get-Member**.</span></span>

> [!NOTE]
> <span data-ttu-id="b3916-134">System.Math verschillende methoden met dezelfde naam heeft, maar ze worden onderscheiden door het type van de bijbehorende parameters.</span><span class="sxs-lookup"><span data-stu-id="b3916-134">System.Math has several methods with the same name, but they are distinguished by the type of their parameters.</span></span>

<span data-ttu-id="b3916-135">Typ de volgende opdracht om een lijst van de methoden van de **System.Math** klasse.</span><span class="sxs-lookup"><span data-stu-id="b3916-135">Type the following command to list the methods of the **System.Math** class.</span></span>

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

<span data-ttu-id="b3916-136">U ziet nu verschillende wiskundige methoden.</span><span class="sxs-lookup"><span data-stu-id="b3916-136">This displays several mathematical methods.</span></span> <span data-ttu-id="b3916-137">Hier volgt een lijst met opdrachten die laten zien hoe sommige van de algemene methoden werken:</span><span class="sxs-lookup"><span data-stu-id="b3916-137">Here is a list of commands that demonstrate how some of the common methods work:</span></span>

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