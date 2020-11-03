---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-host?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Host
ms.openlocfilehash: a0c2b5523dd75dfc7c9822fd55804537035d25f1
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93249292"
---
# <span data-ttu-id="8b083-103">Get-Host</span><span class="sxs-lookup"><span data-stu-id="8b083-103">Get-Host</span></span>

## <span data-ttu-id="8b083-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="8b083-104">SYNOPSIS</span></span>
<span data-ttu-id="8b083-105">Hiermee wordt een object opgehaald dat het huidige host-programma vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="8b083-105">Gets an object that represents the current host program.</span></span>

## <span data-ttu-id="8b083-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="8b083-106">SYNTAX</span></span>

```
Get-Host [<CommonParameters>]
```

## <span data-ttu-id="8b083-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8b083-107">DESCRIPTION</span></span>

<span data-ttu-id="8b083-108">De `Get-Host` cmdlet haalt een object op dat staat voor het programma dat als host fungeert voor Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="8b083-108">The `Get-Host` cmdlet gets an object that represents the program that is hosting Windows PowerShell.</span></span>

<span data-ttu-id="8b083-109">De standaard weergave bevat het versie nummer van Windows Power shell en de huidige regio-en taal instellingen die de host gebruikt, maar het object host bevat een schat aan informatie, inclusief gedetailleerde informatie over de versie van Windows Power shell die momenteel wordt uitgevoerd en de huidige cultuur-en GEBRUIKERSINTERFACE cultuur van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="8b083-109">The default display includes the Windows PowerShell version number and the current region and language settings that the host is using, but the host object contains a wealth of information, including detailed information about the version of Windows PowerShell that is currently running and the current culture and UI culture of Windows PowerShell.</span></span> <span data-ttu-id="8b083-110">U kunt deze cmdlet ook gebruiken voor het aanpassen van de functies van de gebruikers interface van het gast programma, zoals de tekst-en achtergrond kleuren.</span><span class="sxs-lookup"><span data-stu-id="8b083-110">You can also use this cmdlet to customize features of the host program user interface, such as the text and background colors.</span></span>

## <span data-ttu-id="8b083-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="8b083-111">EXAMPLES</span></span>

### <span data-ttu-id="8b083-112">Voor beeld 1: informatie over de host van de Power shell-console ophalen</span><span class="sxs-lookup"><span data-stu-id="8b083-112">Example 1: Get information about the PowerShell console host</span></span>

```
PS C:\> Get-Host
Name             : ConsoleHost
Version          : 2.0
InstanceId       : e4e0ab54-cc5e-4261-9117-4081f20ce7a2
UI               : System.Management.Automation.Internal.Host.InternalHostUserInterface
CurrentCulture   : en-US
CurrentUICulture : en-US
PrivateData      : Microsoft.PowerShell.ConsoleHost+ConsoleColorProxy
IsRunspacePushed : False
Runspace         : System.Management.Automation.Runspaces.LocalRunspace
```

<span data-ttu-id="8b083-113">Met deze opdracht wordt informatie weer gegeven over de Windows Power shell-console, het huidige hostprogramma voor Windows Power shell in dit voor beeld.</span><span class="sxs-lookup"><span data-stu-id="8b083-113">This command displays information about the Windows PowerShell console, which is the current host program for Windows PowerShell in this example.</span></span> <span data-ttu-id="8b083-114">Het bevat de naam van de host, de versie van Windows Power shell die wordt uitgevoerd op de host en de huidige cultuur-en GEBRUIKERSINTERFACE cultuur.</span><span class="sxs-lookup"><span data-stu-id="8b083-114">It includes the name of the host, the version of Windows PowerShell that is running in the host, and current culture and UI culture.</span></span>

<span data-ttu-id="8b083-115">De eigenschappen version, UI, CurrentCulture, CurrentUICulture, PrivateData en runs Pace bevatten elk een object met zeer nuttige eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="8b083-115">The Version, UI, CurrentCulture, CurrentUICulture, PrivateData, and Runspace properties each contain an object with very useful properties.</span></span> <span data-ttu-id="8b083-116">In latere voor beelden worden deze eigenschappen onderzocht.</span><span class="sxs-lookup"><span data-stu-id="8b083-116">Later examples examine these properties.</span></span>

### <span data-ttu-id="8b083-117">Voor beeld 2: het formaat van het Power shell-venster wijzigen</span><span class="sxs-lookup"><span data-stu-id="8b083-117">Example 2: Resize the PowerShell window</span></span>

```powershell
PS C:\> $H = Get-Host
PS C:\> $Win = $H.UI.RawUI.WindowSize
PS C:\> $Win.Height = 10
PS C:\> $Win.Width  = 10
PS C:\> $H.UI.RawUI.Set_WindowSize($Win)
```

<span data-ttu-id="8b083-118">Met deze opdracht wordt het formaat van het Windows Power shell-venster gewijzigd in 10 pixels van 10 pixels.</span><span class="sxs-lookup"><span data-stu-id="8b083-118">This command resizes the Windows PowerShell window to 10 pixels by 10 pixels.</span></span>

### <span data-ttu-id="8b083-119">Voor beeld 3: de Power shell-versie voor de host ophalen</span><span class="sxs-lookup"><span data-stu-id="8b083-119">Example 3: Get the PowerShell version for the host</span></span>

```powershell
PS C:\> (Get-Host).Version | Format-List -Property *
Major         : 2
Minor         : 0
Build         : -1
Revision      : -1
MajorRevision : -1
MinorRevision : -1
```

<span data-ttu-id="8b083-120">Met deze opdracht wordt gedetailleerde informatie opgehaald over de versie van Windows Power shell die wordt uitgevoerd op de host.</span><span class="sxs-lookup"><span data-stu-id="8b083-120">This command gets detailed information about the version of Windows PowerShell running in the host.</span></span>
<span data-ttu-id="8b083-121">U kunt deze waarden weer geven, maar niet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="8b083-121">You can view, but not change, these values.</span></span>

<span data-ttu-id="8b083-122">De versie-eigenschap van `Get-Host` bevat een **System. version** -object.</span><span class="sxs-lookup"><span data-stu-id="8b083-122">The Version property of `Get-Host` contains a **System.Version** object.</span></span> <span data-ttu-id="8b083-123">Met deze opdracht wordt een pijplijn operator (|) gebruikt om het versie object naar de `Format-List` cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="8b083-123">This command uses a pipeline operator (|) to send the version object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="8b083-124">De `Format-List` opdracht gebruikt de *eigenschap* para meter met de waarde all (\*) om alle eigenschappen en eigenschaps waarden van het versie object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="8b083-124">The `Format-List` command uses the *Property* parameter with a value of all (\*) to display all of the properties and property values of the version object.</span></span>

### <span data-ttu-id="8b083-125">Voor beeld 4: de huidige cultuur voor de host ophalen</span><span class="sxs-lookup"><span data-stu-id="8b083-125">Example 4: Get the current culture for the host</span></span>

```powershell
PS C:\> (Get-Host).CurrentCulture | Format-List -Property *
Parent                         : en
LCID                           : 1033
KeyboardLayoutId               : 1033
Name                           : en-US
IetfLanguageTag                : en-US
DisplayName                    : English (United States)
NativeName                     : English (United States)
EnglishName                    : English (United States)
TwoLetterISOLanguageName       : en
ThreeLetterISOLanguageName     : eng
ThreeLetterWindowsLanguageName : ENU
CompareInfo                    : CompareInfo - 1033
TextInfo                       : TextInfo - 1033
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar, System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False
```

<span data-ttu-id="8b083-126">Met deze opdracht wordt gedetailleerde informatie over de huidige cultuur ingesteld voor Windows Power shell die wordt uitgevoerd op de host.</span><span class="sxs-lookup"><span data-stu-id="8b083-126">This command gets detailed information about the current culture set for Windows PowerShell running in the host.</span></span> <span data-ttu-id="8b083-127">Dit is dezelfde informatie die wordt geretourneerd door de `Get-Culture` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8b083-127">This is the same information that is returned by the `Get-Culture` cmdlet.</span></span>

<span data-ttu-id="8b083-128">Op dezelfde manier retourneert de eigenschap **CurrentUICulture** hetzelfde object `Get-UICulture` als dat retourneert.</span><span class="sxs-lookup"><span data-stu-id="8b083-128">Similarly, the **CurrentUICulture** property returns the same object that `Get-UICulture` returns.</span></span>

<span data-ttu-id="8b083-129">De eigenschap **CurrentCulture** van het object host bevat een object **System. Globalization. Culture info** .</span><span class="sxs-lookup"><span data-stu-id="8b083-129">The **CurrentCulture** property of the host object contains a **System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="8b083-130">Met deze opdracht wordt een pijplijn operator (|) gebruikt om het **Culture info** -object naar de cmdlet te verzenden `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="8b083-130">This command uses a pipeline operator (|) to send the **CultureInfo** object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="8b083-131">De `Format-List` opdracht maakt gebruik van de *eigenschap* para meter met de waarde all (\*) om alle eigenschappen en eigenschapwaarden van het **Culture info** -object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="8b083-131">The `Format-List` command uses the *Property* parameter with a value of all (\*) to display all of the properties and property values of the **CultureInfo** object.</span></span>

### <span data-ttu-id="8b083-132">Voor beeld 5: de date time format voor de huidige cultuur ophalen</span><span class="sxs-lookup"><span data-stu-id="8b083-132">Example 5: Get the DateTimeFormat for the current culture</span></span>

```powershell
PS C:\> (Get-Host).CurrentCulture.DateTimeFormat | Format-List -Property *
AMDesignator                     : AM
Calendar                         : System.Globalization.GregorianCalendar
DateSeparator                    : /
FirstDayOfWeek                   : Sunday
CalendarWeekRule                 : FirstDay
FullDateTimePattern              : dddd, MMMM dd, yyyy h:mm:ss tt
LongDatePattern                  : dddd, MMMM dd, yyyy
LongTimePattern                  : h:mm:ss tt
MonthDayPattern                  : MMMM dd
PMDesignator                     : PM
RFC1123Pattern                   : ddd, dd MMM yyyy HH':'mm':'ss 'GMT'
ShortDatePattern                 : M/d/yyyy
ShortTimePattern                 : h:mm tt
SortableDateTimePattern          : yyyy'-'MM'-'dd'T'HH':'mm':'ss
TimeSeparator                    : :
UniversalSortableDateTimePattern : yyyy'-'MM'-'dd HH':'mm':'ss'Z'
YearMonthPattern                 : MMMM, yyyy
AbbreviatedDayNames              : {Sun, Mon, Tue, Wed...}
ShortestDayNames                 : {Su, Mo, Tu, We...}
DayNames                         : {Sunday, Monday, Tuesday, Wednesday...}
AbbreviatedMonthNames            : {Jan, Feb, Mar, Apr...}
MonthNames                       : {January, February, March, April...}
IsReadOnly                       : False
NativeCalendarName               : Gregorian Calendar
AbbreviatedMonthGenitiveNames    : {Jan, Feb, Mar, Apr...}
MonthGenitiveNames               : {January, February, March, April...}
```

<span data-ttu-id="8b083-133">Met deze opdracht wordt gedetailleerde informatie geretourneerd over de date time format van de huidige cultuur die wordt gebruikt voor Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="8b083-133">This command returns detailed information about the DateTimeFormat of the current culture that is being used for Windows PowerShell.</span></span>

<span data-ttu-id="8b083-134">De eigenschap **CurrentCulture** van het object host bevat een **Culture info** -object dat op zijn beurt een groot aantal nuttige eigenschappen heeft.</span><span class="sxs-lookup"><span data-stu-id="8b083-134">The **CurrentCulture** property of the host object contains a **CultureInfo** object that, in turn, has many useful properties.</span></span> <span data-ttu-id="8b083-135">De eigenschap **date time format** bevat onder andere een **DateTimeFormatInfo** -object met veel nuttige eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="8b083-135">Among them, the **DateTimeFormat** property contains a **DateTimeFormatInfo** object with many useful properties.</span></span>

<span data-ttu-id="8b083-136">Gebruik de cmdlet om het type van een object te vinden dat is opgeslagen in een object eigenschap `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="8b083-136">To find the type of an object that is stored in an object property, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="8b083-137">Gebruik de cmdlet om de eigenschaps waarden van het object weer te geven `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="8b083-137">To display the property values of the object, use the `Format-List` cmdlet.</span></span>

### <span data-ttu-id="8b083-138">Voor beeld 6: de eigenschap RawUI voor de host ophalen</span><span class="sxs-lookup"><span data-stu-id="8b083-138">Example 6: Get the RawUI property for the host</span></span>

```
PS C:\> (Get-Host).UI.RawUI | Format-List -Property *
ForegroundColor       : DarkYellow
BackgroundColor       : DarkBlue
CursorPosition        : 0,390
WindowPosition        : 0,341
CursorSize            : 25
BufferSize            : 120,3000
WindowSize            : 120,50
MaxWindowSize         : 120,81
MaxPhysicalWindowSize : 182,81
KeyAvailable          : False
WindowTitle           : Windows PowerShell 2.0 (04/11/2008 00:08:14)
```

<span data-ttu-id="8b083-139">Met deze opdracht worden de eigenschappen van de eigenschap **RawUI** van het object host weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8b083-139">This command displays the properties of the **RawUI** property of the host object.</span></span> <span data-ttu-id="8b083-140">Door deze waarden te wijzigen, kunt u de weer gave van het host-programma wijzigen.</span><span class="sxs-lookup"><span data-stu-id="8b083-140">By changing these values, you can change the appearance of the host program.</span></span>

### <span data-ttu-id="8b083-141">Voor beeld 7: de achtergrond kleur voor de Power shell-console instellen</span><span class="sxs-lookup"><span data-stu-id="8b083-141">Example 7: Set the background color for the PowerShell console</span></span>

```powershell
PS C:\> (Get-Host).UI.RawUI.BackgroundColor = "Black"
PS C:\> cls
```

<span data-ttu-id="8b083-142">Met deze opdrachten wordt de achtergrond kleur van de Windows Power shell-console gewijzigd in zwart.</span><span class="sxs-lookup"><span data-stu-id="8b083-142">These commands change the background color of the Windows PowerShell console to black.</span></span> <span data-ttu-id="8b083-143">De **CLS** -opdracht is een alias voor de `Clear-Host` functie, waardoor het scherm wordt gewist en het hele scherm wordt gewijzigd in de nieuwe kleur.</span><span class="sxs-lookup"><span data-stu-id="8b083-143">The **cls** command is an alias for the `Clear-Host` function, which clears the screen and changes the whole screen to the new color.</span></span>

<span data-ttu-id="8b083-144">Deze wijziging is alleen effectief in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="8b083-144">This change is effective only in the current session.</span></span> <span data-ttu-id="8b083-145">Als u de achtergrond kleur van de console voor alle sessies wilt wijzigen, voegt u de opdracht toe aan uw Windows Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="8b083-145">To change the background color of the console for all sessions, add the command to your Windows PowerShell profile.</span></span>

### <span data-ttu-id="8b083-146">Voor beeld 8: de achtergrond kleur voor fout berichten instellen</span><span class="sxs-lookup"><span data-stu-id="8b083-146">Example 8: Set the background color for error messages</span></span>

```
PS C:\> $Host.PrivateData.ErrorBackgroundColor = "white"
```

<span data-ttu-id="8b083-147">Met deze opdracht wordt de achtergrond kleur van fout berichten gewijzigd in wit.</span><span class="sxs-lookup"><span data-stu-id="8b083-147">This command changes the background color of error messages to white.</span></span>

<span data-ttu-id="8b083-148">Met deze opdracht wordt de `$Host` Automatische variabele gebruikt, die het object host bevat voor het huidige host-programma.</span><span class="sxs-lookup"><span data-stu-id="8b083-148">This command uses the `$Host` automatic variable, which contains the host object for the current host program.</span></span> <span data-ttu-id="8b083-149">`Get-Host` retourneert hetzelfde object dat `$Host` bevat, zodat u ze kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8b083-149">`Get-Host` returns the same object that `$Host` contains, so you can use them interchangeably.</span></span>

<span data-ttu-id="8b083-150">Deze opdracht maakt gebruik van de eigenschap **PrivateData** van `$Host` als de eigenschap ErrorBackgroundColor.</span><span class="sxs-lookup"><span data-stu-id="8b083-150">This command uses the **PrivateData** property of `$Host` as its ErrorBackgroundColor property.</span></span> <span data-ttu-id="8b083-151">Om alle eigenschappen van het object in de te bekijken `$Host` . Eigenschap PrivateData, type `$host.privatedata | format-list *` .</span><span class="sxs-lookup"><span data-stu-id="8b083-151">To see all of the properties of the object in the `$Host`.PrivateData property, type `$host.privatedata | format-list *`.</span></span>

## <span data-ttu-id="8b083-152">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8b083-152">PARAMETERS</span></span>

### <span data-ttu-id="8b083-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8b083-153">CommonParameters</span></span>

<span data-ttu-id="8b083-154">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8b083-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8b083-155">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8b083-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8b083-156">INVOER</span><span class="sxs-lookup"><span data-stu-id="8b083-156">INPUTS</span></span>

### <span data-ttu-id="8b083-157">Geen</span><span class="sxs-lookup"><span data-stu-id="8b083-157">None</span></span>
<span data-ttu-id="8b083-158">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8b083-158">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="8b083-159">UITVOER</span><span class="sxs-lookup"><span data-stu-id="8b083-159">OUTPUTS</span></span>

### <span data-ttu-id="8b083-160">System. Management. Automation. internal. host. InternalHost</span><span class="sxs-lookup"><span data-stu-id="8b083-160">System.Management.Automation.Internal.Host.InternalHost</span></span>

<span data-ttu-id="8b083-161">`Get-Host` retourneert het object **System. Management. Automation. internal. host. InternalHost** .</span><span class="sxs-lookup"><span data-stu-id="8b083-161">`Get-Host` returns a **System.Management.Automation.Internal.Host.InternalHost** object.</span></span>

## <span data-ttu-id="8b083-162">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="8b083-162">NOTES</span></span>

<span data-ttu-id="8b083-163">De `$Host` Automatische variabele bevat hetzelfde object dat `Get-Host` retourneert, en u kunt het op dezelfde manier gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8b083-163">The `$Host` automatic variable contains the same object that `Get-Host` returns, and you can use it in the same way.</span></span> <span data-ttu-id="8b083-164">Op dezelfde manier `$PSCulture` bevatten de en `$PSUICulture` automatische variabelen dezelfde objecten die de eigenschappen CurrentCulture en CurrentUICulture van het object host bevatten.</span><span class="sxs-lookup"><span data-stu-id="8b083-164">Similarly, the `$PSCulture` and `$PSUICulture` automatic variables contain the same objects that the CurrentCulture and CurrentUICulture properties of the host object contain.</span></span> <span data-ttu-id="8b083-165">U kunt deze functies door elkaar gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8b083-165">You can use these features interchangeably.</span></span>

<span data-ttu-id="8b083-166">Zie [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8b083-166">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

## <span data-ttu-id="8b083-167">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="8b083-167">RELATED LINKS</span></span>

[<span data-ttu-id="8b083-168">Wissen-host</span><span class="sxs-lookup"><span data-stu-id="8b083-168">Clear-Host</span></span>](../Microsoft.PowerShell.Core/Clear-Host.md)

[<span data-ttu-id="8b083-169">Read-host</span><span class="sxs-lookup"><span data-stu-id="8b083-169">Read-Host</span></span>](Read-Host.md)

[<span data-ttu-id="8b083-170">Write-host</span><span class="sxs-lookup"><span data-stu-id="8b083-170">Write-Host</span></span>](Write-Host.md)
