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
# <a name="using-static-classes-and-methods"></a>Statische klassen en methoden gebruiken

Niet alle .NET Framework klassen kunnen worden gemaakt met behulp van **New-object**. Als u bijvoorbeeld probeert een **System. Environment** -of **System. math** -object te maken met **Nieuw-object**, worden de volgende fout berichten weer geven:

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

Deze fouten treden op omdat er geen manier is om een nieuw object te maken op basis van deze klassen. Deze klassen zijn referentie bibliotheken met methoden en eigenschappen die de status niet wijzigen. U hoeft deze niet te maken, maar u kunt ze gewoon gebruiken. Klassen en methoden zoals deze worden *statische klassen* genoemd, omdat ze niet zijn gemaakt, vernietigd of gewijzigd. Om dit duidelijk te maken, bieden we voor beelden die gebruikmaken van statische klassen.

## <a name="getting-environment-data-with-systemenvironment"></a>Omgevings gegevens ophalen met System. Environment

Normaal gesp roken is de eerste stap bij het werken met een object in Windows Power shell uit het gebruik van Get-Member om erachter te komen welke leden de app bevat. Bij statische klassen is het proces iets anders omdat de daad werkelijke klasse geen object is.

### <a name="referring-to-the-static-systemenvironment-class"></a>Verwijzen naar de klasse static System. Environment

U kunt naar een statische klasse verwijzen door de naam van de klasse te omgeven door rechte haken. U kunt bijvoorbeeld verwijzen naar **System. Environment** door de naam tussen vier Kante haken te typen. Dit geeft een aantal algemene type gegevens weer:

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> Zoals eerder vermeld, voegt Windows Power shell automatisch '**System.**' toe. Als u namen wilt typen wanneer u **Nieuw-object**gebruikt. Hetzelfde gebeurt wanneer u een type naam tussen haakjes gebruikt, zodat u ** \[ System. Environment]** als ** \[ omgeving**kunt opgeven.

De klasse **System. Environment** bevat algemene informatie over de werk omgeving voor het huidige proces, dat powershell.exe wanneer u werkt in Windows Power shell.

Als u de details van deze klasse wilt bekijken door ** \[ System. Environment te typen] | Get-member**, het object type wordt gerapporteerd als **System. RuntimeType** , niet **System. Environment**:

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

Als u statische leden wilt weer geven met Get-member, geeft u de **statische** para meter op:

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

U kunt nu eigenschappen selecteren om uit System. Environment weer te geven.

### <a name="displaying-static-properties-of-systemenvironment"></a>Statische eigenschappen van System. Environment weer geven

De eigenschappen van System. Environment zijn ook statisch en moeten op een andere manier worden opgegeven dan de normale eigenschappen. We gebruiken **::** om aan te geven dat Windows Power shell moet werken met een statische methode of eigenschap. Als u de opdracht wilt zien die is gebruikt om Windows Power shell te starten, wordt de eigenschap **commandline** gecontroleerd door het volgende te typen:

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

Als u de versie van het besturings systeem wilt controleren, geeft u de eigenschap onproperty weer door het volgende te typen:

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

We kunnen controleren of de computer bezig is met afsluiten door de eigenschap **HasShutdownStarted** weer te geven:

```
PS> [System.Environment]::HasShutdownStarted
False
```

## <a name="doing-math-with-systemmath"></a>Wiskunde uitvoeren met System. math

De statische klasse System. Math is handig voor het uitvoeren van een aantal reken kundige bewerkingen. De belang rijke leden van **System. math** worden voornamelijk beschreven, die kunnen worden weer gegeven met behulp van **Get-member**.

> [!NOTE]
> System. math heeft verschillende methoden met dezelfde naam, maar ze worden onderscheiden door het type van de bijbehorende para meters.

Typ de volgende opdracht om de methoden van de klasse **System. math** weer te geven.

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

Er worden verschillende Mathematische methoden weer gegeven. Hier volgt een lijst met opdrachten die laten zien hoe sommige algemene methoden werken:

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
