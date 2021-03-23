---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/22/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Host
ms.openlocfilehash: da48cdaf11a7dd0f1d8a169ca145fecc5052bf02
ms.sourcegitcommit: a0148ef8bf9757f68c788d24f2eaf92792c3979f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104796257"
---
# <span data-ttu-id="326ea-102">Get-Host</span><span class="sxs-lookup"><span data-stu-id="326ea-102">Get-Host</span></span>

## <span data-ttu-id="326ea-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="326ea-103">SYNOPSIS</span></span>
<span data-ttu-id="326ea-104">Hiermee wordt een object opgehaald dat het huidige host-programma vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="326ea-104">Gets an object that represents the current host program.</span></span>

## <span data-ttu-id="326ea-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="326ea-105">SYNTAX</span></span>

```
Get-Host [<CommonParameters>]
```

## <span data-ttu-id="326ea-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="326ea-106">DESCRIPTION</span></span>

<span data-ttu-id="326ea-107">De `Get-Host` cmdlet haalt een object op dat staat voor het programma dat als host fungeert voor Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="326ea-107">The `Get-Host` cmdlet gets an object that represents the program that is hosting Windows PowerShell.</span></span>

<span data-ttu-id="326ea-108">De standaard weergave bevat het versie nummer van Windows Power shell en de huidige regio-en taal instellingen die de host gebruikt, maar het object host bevat een schat aan informatie, inclusief gedetailleerde informatie over de versie van Windows Power shell die momenteel wordt uitgevoerd en de huidige cultuur-en GEBRUIKERSINTERFACE cultuur van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="326ea-108">The default display includes the Windows PowerShell version number and the current region and language settings that the host is using, but the host object contains a wealth of information, including detailed information about the version of Windows PowerShell that is currently running and the current culture and UI culture of Windows PowerShell.</span></span> <span data-ttu-id="326ea-109">U kunt deze cmdlet ook gebruiken voor het aanpassen van de functies van de gebruikers interface van het gast programma, zoals de tekst-en achtergrond kleuren.</span><span class="sxs-lookup"><span data-stu-id="326ea-109">You can also use this cmdlet to customize features of the host program user interface, such as the text and background colors.</span></span>

## <span data-ttu-id="326ea-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="326ea-110">EXAMPLES</span></span>

### <span data-ttu-id="326ea-111">Voor beeld 1: informatie over de host van de Power shell-console ophalen</span><span class="sxs-lookup"><span data-stu-id="326ea-111">Example 1: Get information about the PowerShell console host</span></span>

```
Get-Host

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

<span data-ttu-id="326ea-112">Met deze opdracht wordt informatie weer gegeven over de Power shell-console, het huidige hostprogramma voor Power shell in dit voor beeld.</span><span class="sxs-lookup"><span data-stu-id="326ea-112">This command displays information about the PowerShell console, which is the current host program for PowerShell in this example.</span></span> <span data-ttu-id="326ea-113">Het bevat de naam van de host, de versie van Power shell die wordt uitgevoerd op de host en de huidige cultuur-en GEBRUIKERSINTERFACE cultuur.</span><span class="sxs-lookup"><span data-stu-id="326ea-113">It includes the name of the host, the version of PowerShell that is running in the host, and current culture and UI culture.</span></span>

<span data-ttu-id="326ea-114">De eigenschappen **Version**, **UI**, **CurrentCulture**, **CurrentUICulture**, **PrivateData** en **runs Pace** bevatten elk een object met andere nuttige eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="326ea-114">The **Version**, **UI**, **CurrentCulture**, **CurrentUICulture**, **PrivateData**, and **Runspace** properties each contain an object with other useful properties.</span></span> <span data-ttu-id="326ea-115">In latere voor beelden worden deze eigenschappen onderzocht.</span><span class="sxs-lookup"><span data-stu-id="326ea-115">Later examples examine these properties.</span></span>

### <span data-ttu-id="326ea-116">Voor beeld 2: het formaat van het Power shell-venster wijzigen</span><span class="sxs-lookup"><span data-stu-id="326ea-116">Example 2: Resize the PowerShell window</span></span>

```powershell
$H = Get-Host
$Win = $H.UI.RawUI.WindowSize
$Win.Height = 10
$Win.Width  = 10
$H.UI.RawUI.Set_WindowSize($Win)
```

<span data-ttu-id="326ea-117">Met deze opdracht wordt het formaat van het Windows Power shell-venster gewijzigd in 10 regels van 10 tekens.</span><span class="sxs-lookup"><span data-stu-id="326ea-117">This command resizes the Windows PowerShell window to 10 lines by 10 characters.</span></span>

### <span data-ttu-id="326ea-118">Voor beeld 3: de Power shell-versie voor de host ophalen</span><span class="sxs-lookup"><span data-stu-id="326ea-118">Example 3: Get the PowerShell version for the host</span></span>

```powershell
(Get-Host).Version | Format-List -Property *

Major         : 2
Minor         : 0
Build         : -1
Revision      : -1
MajorRevision : -1
MinorRevision : -1
```

<span data-ttu-id="326ea-119">Met deze opdracht wordt gedetailleerde informatie opgehaald over de versie van Windows Power shell die wordt uitgevoerd op de host.</span><span class="sxs-lookup"><span data-stu-id="326ea-119">This command gets detailed information about the version of Windows PowerShell running in the host.</span></span>
<span data-ttu-id="326ea-120">U kunt deze waarden weer geven, maar niet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="326ea-120">You can view, but not change, these values.</span></span>

<span data-ttu-id="326ea-121">De versie-eigenschap van `Get-Host` bevat een **System. version** -object.</span><span class="sxs-lookup"><span data-stu-id="326ea-121">The Version property of `Get-Host` contains a **System.Version** object.</span></span> <span data-ttu-id="326ea-122">Met deze opdracht wordt een pijplijn operator ( `|` ) gebruikt om het versie object naar de `Format-List` cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="326ea-122">This command uses a pipeline operator (`|`) to send the version object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="326ea-123">De `Format-List` opdracht gebruikt de **eigenschap** para meter met de waarde all ( `*` ) om alle eigenschappen en eigenschaps waarden van het versie object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="326ea-123">The `Format-List` command uses the **Property** parameter with a value of all (`*`) to display all of the properties and property values of the version object.</span></span>

### <span data-ttu-id="326ea-124">Voor beeld 4: de huidige cultuur voor de host ophalen</span><span class="sxs-lookup"><span data-stu-id="326ea-124">Example 4: Get the current culture for the host</span></span>

```powershell
(Get-Host).CurrentCulture | Format-List -Property *

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

<span data-ttu-id="326ea-125">Met deze opdracht wordt gedetailleerde informatie over de huidige cultuur ingesteld voor Windows Power shell die wordt uitgevoerd op de host.</span><span class="sxs-lookup"><span data-stu-id="326ea-125">This command gets detailed information about the current culture set for Windows PowerShell running in the host.</span></span> <span data-ttu-id="326ea-126">Dit is dezelfde informatie die wordt geretourneerd door de `Get-Culture` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="326ea-126">This is the same information that is returned by the `Get-Culture` cmdlet.</span></span>

<span data-ttu-id="326ea-127">Op dezelfde manier retourneert de eigenschap **CurrentUICulture** hetzelfde object `Get-UICulture` als dat retourneert.</span><span class="sxs-lookup"><span data-stu-id="326ea-127">Similarly, the **CurrentUICulture** property returns the same object that `Get-UICulture` returns.</span></span>

<span data-ttu-id="326ea-128">De eigenschap **CurrentCulture** van het object host bevat een object **System. Globalization. Culture info** .</span><span class="sxs-lookup"><span data-stu-id="326ea-128">The **CurrentCulture** property of the host object contains a **System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="326ea-129">Met deze opdracht wordt een pijplijn operator ( `|` ) gebruikt om het **Culture info** -object naar de cmdlet te verzenden `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="326ea-129">This command uses a pipeline operator (`|`) to send the **CultureInfo** object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="326ea-130">De `Format-List` opdracht gebruikt de **eigenschap** para meter met de waarde all ( `*` ) om alle eigenschappen en eigenschaps waarden van het **Culture info** -object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="326ea-130">The `Format-List` command uses the **Property** parameter with a value of all (`*`) to display all of the properties and property values of the **CultureInfo** object.</span></span>

### <span data-ttu-id="326ea-131">Voor beeld 5: de date time format voor de huidige cultuur ophalen</span><span class="sxs-lookup"><span data-stu-id="326ea-131">Example 5: Get the DateTimeFormat for the current culture</span></span>

```powershell
(Get-Host).CurrentCulture.DateTimeFormat | Format-List -Property *

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

<span data-ttu-id="326ea-132">Met deze opdracht wordt gedetailleerde informatie geretourneerd over de date time format van de huidige cultuur die wordt gebruikt voor Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="326ea-132">This command returns detailed information about the DateTimeFormat of the current culture that is being used for Windows PowerShell.</span></span>

<span data-ttu-id="326ea-133">De eigenschap **CurrentCulture** van het object host bevat een **Culture info** -object dat op zijn beurt een groot aantal nuttige eigenschappen heeft.</span><span class="sxs-lookup"><span data-stu-id="326ea-133">The **CurrentCulture** property of the host object contains a **CultureInfo** object that, in turn, has many useful properties.</span></span> <span data-ttu-id="326ea-134">De eigenschap **date time format** bevat onder andere een **DateTimeFormatInfo** -object met veel nuttige eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="326ea-134">Among them, the **DateTimeFormat** property contains a **DateTimeFormatInfo** object with many useful properties.</span></span>

<span data-ttu-id="326ea-135">Gebruik de cmdlet om het type van een object te vinden dat is opgeslagen in een object eigenschap `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="326ea-135">To find the type of an object that is stored in an object property, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="326ea-136">Gebruik de cmdlet om de eigenschaps waarden van het object weer te geven `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="326ea-136">To display the property values of the object, use the `Format-List` cmdlet.</span></span>

### <span data-ttu-id="326ea-137">Voor beeld 6: de eigenschap RawUI voor de host ophalen</span><span class="sxs-lookup"><span data-stu-id="326ea-137">Example 6: Get the RawUI property for the host</span></span>

```
(Get-Host).UI.RawUI | Format-List -Property *

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

<span data-ttu-id="326ea-138">Met deze opdracht worden de eigenschappen van de eigenschap **RawUI** van het object host weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="326ea-138">This command displays the properties of the **RawUI** property of the host object.</span></span> <span data-ttu-id="326ea-139">Door deze waarden te wijzigen, kunt u de weer gave van het host-programma wijzigen.</span><span class="sxs-lookup"><span data-stu-id="326ea-139">By changing these values, you can change the appearance of the host program.</span></span>

### <span data-ttu-id="326ea-140">Voor beeld 7: de achtergrond kleur voor de Power shell-console instellen</span><span class="sxs-lookup"><span data-stu-id="326ea-140">Example 7: Set the background color for the PowerShell console</span></span>

```powershell
(Get-Host).UI.RawUI.BackgroundColor = "Black"
cls
```

<span data-ttu-id="326ea-141">Met deze opdrachten wordt de achtergrond kleur van de Windows Power shell-console gewijzigd in zwart.</span><span class="sxs-lookup"><span data-stu-id="326ea-141">These commands change the background color of the Windows PowerShell console to black.</span></span> <span data-ttu-id="326ea-142">De **CLS** -opdracht is een alias voor de `Clear-Host` functie, waardoor het scherm wordt gewist en het hele scherm wordt gewijzigd in de nieuwe kleur.</span><span class="sxs-lookup"><span data-stu-id="326ea-142">The **cls** command is an alias for the `Clear-Host` function, which clears the screen and changes the whole screen to the new color.</span></span>

<span data-ttu-id="326ea-143">Deze wijziging is alleen effectief in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="326ea-143">This change is effective only in the current session.</span></span> <span data-ttu-id="326ea-144">Als u de achtergrond kleur van de console voor alle sessies wilt wijzigen, voegt u de opdracht toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="326ea-144">To change the background color of the console for all sessions, add the command to your PowerShell profile.</span></span>

### <span data-ttu-id="326ea-145">Voor beeld 8: de achtergrond kleur voor fout berichten instellen</span><span class="sxs-lookup"><span data-stu-id="326ea-145">Example 8: Set the background color for error messages</span></span>

```powershell
$Host.PrivateData.ErrorBackgroundColor = "white"
```

<span data-ttu-id="326ea-146">Met deze opdracht wordt de achtergrond kleur van fout berichten gewijzigd in wit.</span><span class="sxs-lookup"><span data-stu-id="326ea-146">This command changes the background color of error messages to white.</span></span>

<span data-ttu-id="326ea-147">Met deze opdracht wordt de `$Host` Automatische variabele gebruikt, die het object host bevat voor het huidige host-programma.</span><span class="sxs-lookup"><span data-stu-id="326ea-147">This command uses the `$Host` automatic variable, which contains the host object for the current host program.</span></span> <span data-ttu-id="326ea-148">`Get-Host` retourneert hetzelfde object dat `$Host` bevat, zodat u ze kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="326ea-148">`Get-Host` returns the same object that `$Host` contains, so you can use them interchangeably.</span></span>

<span data-ttu-id="326ea-149">Deze opdracht maakt gebruik van de eigenschap **PrivateData** van `$Host` als de eigenschap ErrorBackgroundColor.</span><span class="sxs-lookup"><span data-stu-id="326ea-149">This command uses the **PrivateData** property of `$Host` as its ErrorBackgroundColor property.</span></span> <span data-ttu-id="326ea-150">Om alle eigenschappen van het object in de te bekijken `$Host` . Eigenschap PrivateData, type `$host.PrivateData | format-list *` .</span><span class="sxs-lookup"><span data-stu-id="326ea-150">To see all of the properties of the object in the `$Host`.PrivateData property, type `$host.PrivateData | format-list *`.</span></span>

## <span data-ttu-id="326ea-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="326ea-151">PARAMETERS</span></span>

### <span data-ttu-id="326ea-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="326ea-152">CommonParameters</span></span>

<span data-ttu-id="326ea-153">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="326ea-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="326ea-154">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="326ea-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="326ea-155">INVOER</span><span class="sxs-lookup"><span data-stu-id="326ea-155">INPUTS</span></span>

### <span data-ttu-id="326ea-156">Geen</span><span class="sxs-lookup"><span data-stu-id="326ea-156">None</span></span>

<span data-ttu-id="326ea-157">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="326ea-157">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="326ea-158">UITVOER</span><span class="sxs-lookup"><span data-stu-id="326ea-158">OUTPUTS</span></span>

### <span data-ttu-id="326ea-159">System. Management. Automation. internal. host. InternalHost</span><span class="sxs-lookup"><span data-stu-id="326ea-159">System.Management.Automation.Internal.Host.InternalHost</span></span>

<span data-ttu-id="326ea-160">`Get-Host` retourneert het object **System. Management. Automation. internal. host. InternalHost** .</span><span class="sxs-lookup"><span data-stu-id="326ea-160">`Get-Host` returns a **System.Management.Automation.Internal.Host.InternalHost** object.</span></span>

## <span data-ttu-id="326ea-161">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="326ea-161">NOTES</span></span>

<span data-ttu-id="326ea-162">De `$Host` Automatische variabele bevat hetzelfde object dat `Get-Host` retourneert, en u kunt het op dezelfde manier gebruiken.</span><span class="sxs-lookup"><span data-stu-id="326ea-162">The `$Host` automatic variable contains the same object that `Get-Host` returns, and you can use it in the same way.</span></span> <span data-ttu-id="326ea-163">Op dezelfde manier `$PSCulture` bevatten de en `$PSUICulture` automatische variabelen dezelfde objecten die de eigenschappen CurrentCulture en CurrentUICulture van het object host bevatten.</span><span class="sxs-lookup"><span data-stu-id="326ea-163">Similarly, the `$PSCulture` and `$PSUICulture` automatic variables contain the same objects that the CurrentCulture and CurrentUICulture properties of the host object contain.</span></span> <span data-ttu-id="326ea-164">U kunt deze functies door elkaar gebruiken.</span><span class="sxs-lookup"><span data-stu-id="326ea-164">You can use these features interchangeably.</span></span>

<span data-ttu-id="326ea-165">Zie [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="326ea-165">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

## <span data-ttu-id="326ea-166">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="326ea-166">RELATED LINKS</span></span>

[<span data-ttu-id="326ea-167">Wissen-host</span><span class="sxs-lookup"><span data-stu-id="326ea-167">Clear-Host</span></span>](../Microsoft.PowerShell.Core/Clear-Host.md)

[<span data-ttu-id="326ea-168">Read-host</span><span class="sxs-lookup"><span data-stu-id="326ea-168">Read-Host</span></span>](Read-Host.md)

[<span data-ttu-id="326ea-169">Write-host</span><span class="sxs-lookup"><span data-stu-id="326ea-169">Write-Host</span></span>](Write-Host.md)
