---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Statische klassen en methoden gebruiken
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: e4caff63a1ec7295b6fe450c2915baf0cc7e31af
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59983997"
---
# <a name="using-static-classes-and-methods"></a>Statische klassen en methoden gebruiken

Niet alle .NET Framework-klassen kunnen worden gemaakt met behulp van **New-Object**. Bijvoorbeeld, als u probeert te maken een **System.Environment** of een **System.Math** object met **New-Object**, krijgt u de volgende foutberichten:

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

Deze fouten zich voordoen als er geen manier om te maken van een nieuw object van deze klassen. Deze klassen zijn naslagbibliotheken methoden en eigenschappen die de status niet wijzigen. U hoeft te maken, u deze gewoon gebruiken. Klassen en methoden, zoals deze heten *statische klassen* omdat ze niet worden gemaakt, verwijderd of gewijzigd. We bieden voorbeelden die statische klassen gebruiken om dit te wissen.

## <a name="getting-environment-data-with-systemenvironment"></a>Ophalen van omgevingsgegevens met System.Environment

De eerste stap bij het werken met een object in Windows PowerShell is meestal, Get-Member gebruiken om erachter te komen welke leden bevat. Door statische klassen is het proces enigszins anders, omdat de werkelijke klasse niet een object is.

### <a name="referring-to-the-static-systemenvironment-class"></a>Verwijst naar de statische System.Environment-klasse

U kunt verwijzen naar een statische klasse door de naam van de klasse tussen vierkante haken staan. Bijvoorbeeld, u kunt verwijzen naar **System.Environment** door de naam tussen vierkante haken te typen. Hiermee geeft u enkele algemene informatie over:

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> Zoals we eerder is vermeld, Windows PowerShell automatisch voegt u toe aan elke '**System.**' namen van typen wanneer u **New-Object**. Hetzelfde gebeurt er wanneer u een typenaam die tussen haakjes, zodat u kunt opgeven aan welke  **\[System.Environment]** als  **\[omgeving]**.

De **System.Environment** klasse bevat algemene informatie over de werkomgeving voor het huidige proces powershell.exe is bij het werken in Windows PowerShell.

Als u probeert details van deze klasse bekijken door te typen  **\[System.Environment] | Get-Member**, het objecttype wordt gerapporteerd als zijnde **System.RuntimeType** , niet **System.Environment**:

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

Als u statische leden met Get-Member, geef de **statische** parameter:

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

We kunnen nu eigenschappen om weer te geven van System.Environment selecteren.

### <a name="displaying-static-properties-of-systemenvironment"></a>Statische eigenschappen van System.Environment weergeven

De eigenschappen van System.Environment ook statisch zijn en moeten worden opgegeven in een andere manier dan normaal eigenschappen. We gebruiken **::** om aan te geven aan de Windows PowerShell die we willen werken met een statische methode of eigenschap. Als u wilt zien van de opdracht die is gebruikt voor het starten van Windows PowerShell, controleren we de **CommandLine** eigenschap door te typen:

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

Om te controleren of de versie van het besturingssysteem, de eigenschap OSVersion wordt weergegeven door te typen:

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

Kunnen we uiteraard controleren of de computer wordt afgesloten door weer te geven de **HasShutdownStarted** eigenschap:

```
PS> [System.Environment]::HasShutdownStarted
False
```

## <a name="doing-math-with-systemmath"></a>Math met System.Math doen

De statische klasse System.Math is handig voor het uitvoeren van enkele wiskundige bewerkingen. De belangrijke leden van **System.Math** zijn voornamelijk methoden, die we weergeven met behulp van kunnen **Get-Member**.

> [!NOTE]
> System.Math verschillende methoden met dezelfde naam heeft, maar ze worden onderscheiden door het type van de bijbehorende parameters.

Typ de volgende opdracht om een lijst van de methoden van de **System.Math** klasse.

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

U ziet nu verschillende wiskundige methoden. Hier volgt een lijst met opdrachten die laten zien hoe sommige van de algemene methoden werken:

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