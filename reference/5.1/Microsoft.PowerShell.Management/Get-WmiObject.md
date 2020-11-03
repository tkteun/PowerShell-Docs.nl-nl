---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WmiObject
ms.openlocfilehash: ed759ff3d0dd35cd55f9dac5a2d76e36eac4dc6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250789"
---
# <span data-ttu-id="36a0f-103">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="36a0f-103">Get-WmiObject</span></span>

## <span data-ttu-id="36a0f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="36a0f-104">SYNOPSIS</span></span>
<span data-ttu-id="36a0f-105">Hiermee worden instanties van Windows Management Instrumentation (WMI)-klassen of informatie over de beschik bare klassen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="36a0f-105">Gets instances of Windows Management Instrumentation (WMI) classes or information about the available classes.</span></span>

## <span data-ttu-id="36a0f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="36a0f-106">SYNTAX</span></span>

### <span data-ttu-id="36a0f-107">query (standaard)</span><span class="sxs-lookup"><span data-stu-id="36a0f-107">query (Default)</span></span>

```
Get-WmiObject [-Class] <String> [[-Property] <String[]>] [-Filter <String>] [-Amended] [-DirectRead]
 [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="36a0f-108">list</span><span class="sxs-lookup"><span data-stu-id="36a0f-108">list</span></span>

```
Get-WmiObject [[-Class] <String>] [-Recurse] [-Amended] [-List] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="36a0f-109">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="36a0f-109">WQLQuery</span></span>

```
Get-WmiObject [-Amended] [-DirectRead] -Query <String> [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="36a0f-110">klasse</span><span class="sxs-lookup"><span data-stu-id="36a0f-110">class</span></span>

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### <span data-ttu-id="36a0f-111">leertraject</span><span class="sxs-lookup"><span data-stu-id="36a0f-111">path</span></span>

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

## <span data-ttu-id="36a0f-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="36a0f-112">DESCRIPTION</span></span>

<span data-ttu-id="36a0f-113">Vanaf Power Shell 3,0 is deze cmdlet vervangen door `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="36a0f-113">Starting in PowerShell 3.0, this cmdlet has been superseded by `Get-CimInstance`.</span></span>

<span data-ttu-id="36a0f-114">De `Get-WmiObject` cmdlet krijgt instanties van WMI-klassen of informatie over de beschik bare WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="36a0f-114">The `Get-WmiObject` cmdlet gets instances of WMI classes or information about the available WMI classes.</span></span> <span data-ttu-id="36a0f-115">Als u een externe computer wilt opgeven, gebruikt u de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="36a0f-115">To specify a remote computer, use the **ComputerName** parameter.</span></span> <span data-ttu-id="36a0f-116">Als de **List** -para meter is opgegeven, krijgt de cmdlet informatie over de WMI-klassen die beschikbaar zijn in een opgegeven naam ruimte.</span><span class="sxs-lookup"><span data-stu-id="36a0f-116">If the **List** parameter is specified, the cmdlet gets information about the WMI classes that are available in a specified namespace.</span></span> <span data-ttu-id="36a0f-117">Als de **query** parameter is opgegeven, wordt door de CMDLET een WQL-instructie (WMI Query Language) uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="36a0f-117">If the **Query** parameter is specified, the cmdlet runs a WMI query language (WQL) statement.</span></span>

<span data-ttu-id="36a0f-118">De `Get-WmiObject` cmdlet maakt geen gebruik van externe Windows Power shell om bewerkingen uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="36a0f-118">The `Get-WmiObject` cmdlet does not use Windows PowerShell remoting to perform remote operations.</span></span>
<span data-ttu-id="36a0f-119">U kunt de para meter **ComputerName** van de `Get-WmiObject` cmdlet ook gebruiken als uw computer niet voldoet aan de vereisten voor Windows Power shell Remoting of niet is geconfigureerd voor externe toegang in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="36a0f-119">You can use the **ComputerName** parameter of the `Get-WmiObject` cmdlet even if your computer does not meet the requirements for Windows PowerShell remoting or is not configured for remoting in Windows PowerShell.</span></span>

<span data-ttu-id="36a0f-120">Vanaf Windows Power Shell 3,0 is de eigenschap **__Server** van het object dat `Get-WmiObject` retourneert een **PSComputerName** -alias.</span><span class="sxs-lookup"><span data-stu-id="36a0f-120">Beginning in Windows PowerShell 3.0, the **__Server** property of the object that `Get-WmiObject` returns has a **PSComputerName** alias.</span></span> <span data-ttu-id="36a0f-121">Zo kunt u gemakkelijker de naam van de bron computer in uitvoer en rapporten toevoegen.</span><span class="sxs-lookup"><span data-stu-id="36a0f-121">This makes it easier to include the source computer name in output and reports.</span></span>

## <span data-ttu-id="36a0f-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="36a0f-122">EXAMPLES</span></span>

### <span data-ttu-id="36a0f-123">Voor beeld 1: processen op de lokale computer ophalen</span><span class="sxs-lookup"><span data-stu-id="36a0f-123">Example 1: Get processes on the local computer</span></span>

<span data-ttu-id="36a0f-124">In dit voor beeld worden de processen op de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="36a0f-124">This example get the processes on the local computer.</span></span>

```powershell
Get-WmiObject -Class Win32_Process
```

### <span data-ttu-id="36a0f-125">Voor beeld 2: Hiermee worden services op een externe computer opgehaald</span><span class="sxs-lookup"><span data-stu-id="36a0f-125">Example 2: Gets services on a remote computer</span></span>

<span data-ttu-id="36a0f-126">In dit voor beeld worden de services op een externe computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="36a0f-126">This example gets the services on a remote computer.</span></span> <span data-ttu-id="36a0f-127">Met de para meter **ComputerName** wordt het IP-adres van een externe computer opgegeven.</span><span class="sxs-lookup"><span data-stu-id="36a0f-127">The **ComputerName** parameter specifies the IP address of a remote computer.</span></span> <span data-ttu-id="36a0f-128">Standaard moet het huidige gebruikers account lid zijn van de groep **Administrators** op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="36a0f-128">By default, the current user account must be a member of the **Administrators** group on the remote computer.</span></span>

```powershell
Get-WmiObject -Class Win32_Service -ComputerName 10.1.4.62
```

### <span data-ttu-id="36a0f-129">Voor beeld 3: WMI-klassen ophalen in de hoofdmap of standaard naam ruimte van de lokale computer</span><span class="sxs-lookup"><span data-stu-id="36a0f-129">Example 3: Get WMI classes in the root or default namespace of the local computer</span></span>

<span data-ttu-id="36a0f-130">In dit voor beeld worden de WMI-klassen in de hoofdmap of standaard naam ruimte van de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="36a0f-130">This example gets the WMI classes in the root or default namespace of the local computer.</span></span>

```powershell
Get-WmiObject -Namespace "root/default" -List
```

### <span data-ttu-id="36a0f-131">Voor beeld 4: een benoemde service op meerdere computers ophalen</span><span class="sxs-lookup"><span data-stu-id="36a0f-131">Example 4: Get a named service on multiple computers</span></span>

<span data-ttu-id="36a0f-132">In dit voor beeld wordt de WinRM-service op de computers opgehaald die zijn opgegeven met de waarde van de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="36a0f-132">This example gets the WinRM service on the computers specified by the value of the **ComputerName** parameter.</span></span>

```powershell
Get-WmiObject -Query "select * from win32_service where name='WinRM'" -ComputerName Server01, Server02 |
  Format-List -Property PSComputerName, Name, ExitCode, Name, ProcessID, StartMode, State, Status
```

```Output
PSComputerName : SERVER01
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 844
StartMode      : Auto
State          : Running
Status         : OK

PSComputerName : SERVER02
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 932
StartMode      : Auto
State          : Running
Status         : OK
```

<span data-ttu-id="36a0f-133">Een pijplijn operator (|) verzendt de uitvoer naar de `Format-List` cmdlet, waarmee de eigenschap **PSComputerName** wordt toegevoegd aan de standaard uitvoer.</span><span class="sxs-lookup"><span data-stu-id="36a0f-133">A pipeline operator (|) sends the output to the `Format-List` cmdlet, which adds the **PSComputerName** property to the default output.</span></span> <span data-ttu-id="36a0f-134">**PSComputerName** is een alias van de eigenschap **__Server** van de objecten die worden `Get-WmiObject` geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="36a0f-134">**PSComputerName** is an alias of the **__Server** property of the objects that `Get-WmiObject` returns.</span></span> <span data-ttu-id="36a0f-135">Deze alias is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="36a0f-135">This alias was introduced in PowerShell 3.0.</span></span>

### <span data-ttu-id="36a0f-136">Voor beeld 5: een service stoppen op een externe computer</span><span class="sxs-lookup"><span data-stu-id="36a0f-136">Example 5: Stop a service on a remote computer</span></span>

<span data-ttu-id="36a0f-137">In dit voor beeld wordt de WinRM-service op een externe computer gestopt.</span><span class="sxs-lookup"><span data-stu-id="36a0f-137">This example stops the WinRM service on a remote computer.</span></span> <span data-ttu-id="36a0f-138">`Get-WmiObject` Hiermee wordt het exemplaar van het WinRM-service object op Server01 opgehaald.</span><span class="sxs-lookup"><span data-stu-id="36a0f-138">`Get-WmiObject` gets the instance of the WinRM service object on Server01.</span></span> <span data-ttu-id="36a0f-139">Vervolgens wordt de methode **Stop Service** aangeroepen van de WMI-klasse **Win32_Service** voor dat object.</span><span class="sxs-lookup"><span data-stu-id="36a0f-139">Then, it invokes the **StopService** method of the **Win32_Service** WMI class on that object.</span></span>

```powershell
(Get-WmiObject -Class Win32_Service -Filter "name='WinRM'" -ComputerName Server01).StopService()
```

<span data-ttu-id="36a0f-140">Dit is gelijk aan het gebruik van de `Stop-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="36a0f-140">This is equivalent to using the `Stop-Service` cmdlet.</span></span>

### <span data-ttu-id="36a0f-141">Voor beeld 6: het BIOS op de lokale computer ophalen</span><span class="sxs-lookup"><span data-stu-id="36a0f-141">Example 6: Get the BIOS on the local computer</span></span>

<span data-ttu-id="36a0f-142">In dit voor beeld worden de BIOS-gegevens van de lokale computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="36a0f-142">This example gets the BIOS information from the local computer.</span></span> <span data-ttu-id="36a0f-143">De **eigenschaps** parameter van de `Format-List` cmdlet wordt gebruikt om alle eigenschappen van het geretourneerde object in een lijst weer te geven.</span><span class="sxs-lookup"><span data-stu-id="36a0f-143">The **Property** parameter of the `Format-List` cmdlet is used to display all properties of the returned object in a list.</span></span> <span data-ttu-id="36a0f-144">Standaard worden alleen de subset eigenschappen `Types.ps1xml` weer gegeven die in het configuratie bestand zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="36a0f-144">By default, only the subset of properties defined in the `Types.ps1xml` configuration file are displayed.</span></span>

```powershell
Get-WmiObject -Class Win32_Bios | Format-List -Property *
```

```Output
Status                : OK
Name                  : Phoenix ROM BIOS PLUS Version 1.10 A05
Caption               : Phoenix ROM BIOS PLUS Version 1.10 A05
SMBIOSPresent         : True
__GENUS               : 2
__CLASS               : Win32_BIOS
__SUPERCLASS          : CIM_BIOSElement
__DYNASTY             : CIM_ManagedSystemElement
__RELPATH             : Win32_BIOS.Name="Phoenix ROM BIOS PLUS Version 1.10
__PROPERTY_COUNT      : 27
__DERIVATION          : {CIM_BIOSElement, CIM_SoftwareElement, CIM_LogicalElement,
__SERVER              : Server01
__NAMESPACE           : root\cimv2
__PATH                : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
BiosCharacteristics   : {7, 9, 10, 11...}
BIOSVersion           : {DELL   - 15, Phoenix ROM BIOS PLUS Version 1.10 A05}
BuildNumber           :
CodeSet               :
CurrentLanguage       : en|US|iso8859-1
Description           : Phoenix ROM BIOS PLUS Version 1.10 A05
IdentificationCode    :
InstallableLanguages  : 1
InstallDate           :
LanguageEdition       :
ListOfLanguages       : {en|US|iso8859-1}
Manufacturer          : Dell Inc.
OtherTargetOS         :
PrimaryBIOS           : True
ReleaseDate           : 20101103000000.000000+000
SerialNumber          : 8VDM9P1
SMBIOSBIOSVersion     : A05
SMBIOSMajorVersion    : 2
SMBIOSMinorVersion    : 6
SoftwareElementID     : Phoenix ROM BIOS PLUS Version 1.10 A05
SoftwareElementState  : 3
TargetOperatingSystem : 0
Version               : DELL   - 15
Scope                 : System.Management.ManagementScope
Path                  : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
Options               : System.Management.ObjectGetOptions
ClassPath             : \\JUNE-PC\root\cimv2:Win32_BIOS
Properties            : {BiosCharacteristics, BIOSVersion, BuildNumber, Caption...}
SystemProperties      : {__GENUS, __CLASS, __SUPERCLASS, __DYNASTY...}
Qualifiers            : {dynamic, Locale, provider, UUID}
Site                  :
Container             :
```

### <span data-ttu-id="36a0f-145">Voor beeld 7: de services op een externe computer ophalen</span><span class="sxs-lookup"><span data-stu-id="36a0f-145">Example 7: Get the services on a remote computer</span></span>

<span data-ttu-id="36a0f-146">In dit voor beeld wordt de para meter **Credential** van de `Get-WmiObject` cmdlet gebruikt om de services op een externe computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="36a0f-146">This example uses the **Credential** parameter of the `Get-WmiObject` cmdlet to get the services on a remote computer.</span></span> <span data-ttu-id="36a0f-147">De waarde van de **referentie** parameter is de naam van een gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="36a0f-147">The value of the **Credential** parameter is a user account name.</span></span> <span data-ttu-id="36a0f-148">De gebruiker wordt gevraagd om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="36a0f-148">The user is prompted for a password.</span></span>

```powershell
Get-WmiObject Win32_Service -Credential FABRIKAM\administrator -ComputerName Fabrikam
```

> [!NOTE]
> <span data-ttu-id="36a0f-149">Referenties kunnen niet worden gebruikt bij het richten op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="36a0f-149">Credentials cannot be used when targeting the local computer.</span></span>

## <span data-ttu-id="36a0f-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="36a0f-150">PARAMETERS</span></span>

### <span data-ttu-id="36a0f-151">-Gewijzigd</span><span class="sxs-lookup"><span data-stu-id="36a0f-151">-Amended</span></span>

<span data-ttu-id="36a0f-152">Hiermee wordt een waarde opgehaald of ingesteld die aangeeft of de objecten die worden geretourneerd door WMI, gewijzigde informatie bevatten.</span><span class="sxs-lookup"><span data-stu-id="36a0f-152">Gets or sets a value that indicates whether the objects that are returned from WMI should contain amended information.</span></span> <span data-ttu-id="36a0f-153">Normaal gesp roken wordt gewijzigde informatie gelokaliseerde informatie, zoals object-en eigenschaps beschrijvingen, die aan het WMI-object is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="36a0f-153">Typically, amended information is localizable information, such as object and property descriptions, that is attached to the WMI object.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-154">-AsJob</span><span class="sxs-lookup"><span data-stu-id="36a0f-154">-AsJob</span></span>

<span data-ttu-id="36a0f-155">De opdracht wordt uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="36a0f-155">Runs the command as a background job.</span></span> <span data-ttu-id="36a0f-156">Gebruik deze para meter om opdrachten uit te voeren die lange tijd duren om te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="36a0f-156">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="36a0f-157">Wanneer u de para meter **AsJob** gebruikt, retourneert de opdracht een object dat de achtergrond taak vertegenwoordigt en wordt vervolgens de opdracht prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="36a0f-157">When you use the **AsJob** parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span> <span data-ttu-id="36a0f-158">U kunt in de sessie blijven werken terwijl de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="36a0f-158">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="36a0f-159">Als `Get-WmiObject` op een externe computer wordt gebruikt, wordt de taak op de lokale computer gemaakt en worden de resultaten van externe computers automatisch naar de lokale computer geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="36a0f-159">If `Get-WmiObject` is used on a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="36a0f-160">Als u de taak wilt beheren, gebruikt u de cmdlets die de taak-cmdlets bevatten.</span><span class="sxs-lookup"><span data-stu-id="36a0f-160">To manage the job, use the cmdlets that contain the Job cmdlets.</span></span> <span data-ttu-id="36a0f-161">Gebruik de cmdlet om de taak resultaten te verkrijgen `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="36a0f-161">To get the job results, use the `Receive-Job` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="36a0f-162">Als u deze para meter met externe computers wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="36a0f-162">To use this parameter with remote computers, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="36a0f-163">Daarnaast moet u Windows Power shell starten met de optie als administrator uitvoeren in Windows Vista en latere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="36a0f-163">Additionally, you must start Windows PowerShell by using the "Run as administrator" option in Windows Vista and later versions of Windows.</span></span> <span data-ttu-id="36a0f-164">Zie [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="36a0f-164">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="36a0f-165">Zie [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md) en [about_Remote_Jobs](../Microsoft.PowerShell.Core/about/about_Remote_Jobs.md)voor meer informatie over Windows Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="36a0f-165">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/about/about_Remote_Jobs.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-166">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="36a0f-166">-Authentication</span></span>

<span data-ttu-id="36a0f-167">Hiermee geeft u het verificatie niveau op dat moet worden gebruikt met de WMI-verbinding.</span><span class="sxs-lookup"><span data-stu-id="36a0f-167">Specifies the authentication level to be used with the WMI connection.</span></span>
<span data-ttu-id="36a0f-168">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="36a0f-168">Valid values are:</span></span>

- <span data-ttu-id="36a0f-169">-1: ongewijzigd</span><span class="sxs-lookup"><span data-stu-id="36a0f-169">-1: Unchanged</span></span>
- <span data-ttu-id="36a0f-170">0: standaard</span><span class="sxs-lookup"><span data-stu-id="36a0f-170">0: Default</span></span>
- <span data-ttu-id="36a0f-171">1: geen (er is geen verificatie uitgevoerd.)</span><span class="sxs-lookup"><span data-stu-id="36a0f-171">1: None (No authentication in performed.)</span></span>
- <span data-ttu-id="36a0f-172">2: verbinding maken (verificatie wordt alleen uitgevoerd wanneer de client een relatie tot stand brengt met de toepassing.)</span><span class="sxs-lookup"><span data-stu-id="36a0f-172">2: Connect (Authentication is performed only when the client establishes a relationship with the application.)</span></span>
- <span data-ttu-id="36a0f-173">3: aanroep (verificatie wordt alleen uitgevoerd aan het begin van elke aanroep wanneer de toepassing de aanvraag ontvangt.)</span><span class="sxs-lookup"><span data-stu-id="36a0f-173">3: Call (Authentication is performed only at the beginning of each call when the application receives the request.)</span></span>
- <span data-ttu-id="36a0f-174">4: pakket (verificatie wordt uitgevoerd op alle gegevens die van de client worden ontvangen.)</span><span class="sxs-lookup"><span data-stu-id="36a0f-174">4: Packet (Authentication is performed on all the data that is received from the client.)</span></span>
- <span data-ttu-id="36a0f-175">5: PacketIntegrity (alle gegevens die worden overgebracht tussen de client en de toepassing worden geverifieerd en geverifieerd.)</span><span class="sxs-lookup"><span data-stu-id="36a0f-175">5: PacketIntegrity (All the data that is transferred between the client and the application is authenticated and verified.)</span></span>
- <span data-ttu-id="36a0f-176">6: PacketPrivacy (de eigenschappen van de andere authenticatie niveaus worden gebruikt en alle gegevens worden versleuteld.)</span><span class="sxs-lookup"><span data-stu-id="36a0f-176">6: PacketPrivacy (The properties of the other authentication levels are used, and all the data is encrypted.)</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-177">-Authority</span><span class="sxs-lookup"><span data-stu-id="36a0f-177">-Authority</span></span>

<span data-ttu-id="36a0f-178">Hiermee geeft u de instantie op die moet worden gebruikt om de WMI-verbinding te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="36a0f-178">Specifies the authority to use to authenticate the WMI connection.</span></span> <span data-ttu-id="36a0f-179">U kunt standaard NTLM-of Kerberos-verificatie opgeven.</span><span class="sxs-lookup"><span data-stu-id="36a0f-179">You can specify standard NTLM or Kerberos authentication.</span></span> <span data-ttu-id="36a0f-180">Als u NTLM wilt gebruiken, stelt u de instelling instantie in op `ntlmdomain:<DomainName>` , waarbij `<DomainName>` een geldige NTLM-domein naam wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="36a0f-180">To use NTLM, set the authority setting to `ntlmdomain:<DomainName>`, where `<DomainName>` identifies a valid NTLM domain name.</span></span> <span data-ttu-id="36a0f-181">Als u Kerberos wilt gebruiken, geeft u op `kerberos:<DomainName>\<ServerName>` .</span><span class="sxs-lookup"><span data-stu-id="36a0f-181">To use Kerberos, specify `kerberos:<DomainName>\<ServerName>`.</span></span> <span data-ttu-id="36a0f-182">U kunt de instelling van de instantie niet toevoegen wanneer u verbinding maakt met de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="36a0f-182">You cannot include the authority setting when you connect to the local computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-183">-Klasse</span><span class="sxs-lookup"><span data-stu-id="36a0f-183">-Class</span></span>

<span data-ttu-id="36a0f-184">Hiermee geeft u de naam van een WMI-klasse op.</span><span class="sxs-lookup"><span data-stu-id="36a0f-184">Specifies the name of a WMI class.</span></span> <span data-ttu-id="36a0f-185">Als deze para meter wordt gebruikt, haalt de cmdlet instanties van de WMI-klasse op.</span><span class="sxs-lookup"><span data-stu-id="36a0f-185">When this parameter is used, the cmdlet retrieves instances of the WMI class.</span></span>

```yaml
Type: System.String
Parameter Sets: query, list
Aliases: ClassName

Required: True (query), False (list)
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-186">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="36a0f-186">-ComputerName</span></span>

<span data-ttu-id="36a0f-187">Hiermee geeft u de doel computer voor de beheer bewerking op.</span><span class="sxs-lookup"><span data-stu-id="36a0f-187">Specifies the target computer for the management operation.</span></span> <span data-ttu-id="36a0f-188">Voer een Fully Qualified Domain Name (FQDN), een NetBIOS-naam of een IP-adres in.</span><span class="sxs-lookup"><span data-stu-id="36a0f-188">Enter a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="36a0f-189">Wanneer de externe computer zich in een ander domein bevindt dan de lokale computer, is de Fully Qualified Domain Name vereist.</span><span class="sxs-lookup"><span data-stu-id="36a0f-189">When the remote computer is in a different domain than the local computer, the fully qualified domain name is required.</span></span>

<span data-ttu-id="36a0f-190">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="36a0f-190">The default is the local computer.</span></span> <span data-ttu-id="36a0f-191">Gebruik ' localhost ', de naam van de lokale computer of een punt (.) om de lokale computer op te geven, zoals in een lijst met computer namen.</span><span class="sxs-lookup"><span data-stu-id="36a0f-191">To specify the local computer, such as in a list of computer names, use "localhost", the local computer name, or a dot (.).</span></span>

<span data-ttu-id="36a0f-192">Deze para meter is niet afhankelijk van Windows Power shell remoting en maakt gebruik van WS-Management.</span><span class="sxs-lookup"><span data-stu-id="36a0f-192">This parameter does not rely on Windows PowerShell remoting, which uses WS-Management.</span></span> <span data-ttu-id="36a0f-193">U kunt de para meter **ComputerName** gebruiken `Get-WmiObject` , zelfs als uw computer niet is geconfigureerd om WS-Management externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="36a0f-193">You can use the **ComputerName** parameter of `Get-WmiObject` even if your computer is not configured to run WS-Management remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-194">-Credential</span><span class="sxs-lookup"><span data-stu-id="36a0f-194">-Credential</span></span>

<span data-ttu-id="36a0f-195">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="36a0f-195">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="36a0f-196">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="36a0f-196">The default is the current user.</span></span> <span data-ttu-id="36a0f-197">Typ een gebruikers naam, zoals "gebruiker01", "Domain01\User01" of User@Contoso.com .</span><span class="sxs-lookup"><span data-stu-id="36a0f-197">Type a user name, such as "User01", "Domain01\User01", or User@Contoso.com.</span></span> <span data-ttu-id="36a0f-198">U kunt ook een **PSCredential** -object invoeren, zoals een object dat door de cmdlet wordt geretourneerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="36a0f-198">Or, enter a **PSCredential** object, such as an object that is returned by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="36a0f-199">Wanneer u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="36a0f-199">When you type a user name, you are prompted for a password.</span></span> <span data-ttu-id="36a0f-200">Referenties kunnen niet worden gebruikt bij het richten op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="36a0f-200">Credentials cannot be used when targeting the local computer.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-201">-DirectRead</span><span class="sxs-lookup"><span data-stu-id="36a0f-201">-DirectRead</span></span>

<span data-ttu-id="36a0f-202">Hiermee geeft u op of directe toegang tot de WMI-provider is aangevraagd voor de opgegeven klasse, zonder enige voor de basis klasse of de afgeleide klassen ervan.</span><span class="sxs-lookup"><span data-stu-id="36a0f-202">Specifies whether direct access to the WMI provider is requested for the specified class without any regard to its base class or to its derived classes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: query, WQLQuery
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-203">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="36a0f-203">-EnableAllPrivileges</span></span>

<span data-ttu-id="36a0f-204">Hiermee worden alle bevoegdheden van de huidige gebruiker ingeschakeld voordat de opdracht de WMI-aanroep uitvoert.</span><span class="sxs-lookup"><span data-stu-id="36a0f-204">Enables all the privileges of the current user before the command makes the WMI call.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-205">-Filter</span><span class="sxs-lookup"><span data-stu-id="36a0f-205">-Filter</span></span>

<span data-ttu-id="36a0f-206">Hiermee geeft u een **where** -component moet worden gebruikt als een filter.</span><span class="sxs-lookup"><span data-stu-id="36a0f-206">Specifies a **Where** clause to use as a filter.</span></span> <span data-ttu-id="36a0f-207">Gebruikt de syntaxis van de WMI Query Language (WQL).</span><span class="sxs-lookup"><span data-stu-id="36a0f-207">Uses the syntax of the WMI Query Language (WQL).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36a0f-208">Neem het sleutel woord **waar** niet op in de waarde van de para meter.</span><span class="sxs-lookup"><span data-stu-id="36a0f-208">Do not include the **Where** keyword in the value of the parameter.</span></span> <span data-ttu-id="36a0f-209">De volgende opdrachten retour neren bijvoorbeeld alleen de logische schijven met een **DeviceID** van c: en services die de naam ' WinRM ' hebben zonder het sleutel woord **where** te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="36a0f-209">For example, the following commands return only the logical disks that have a **DeviceID** of 'c:' and services that have the name 'WinRM' without using the **Where** keyword.</span></span>

`Get-WmiObject Win32_LogicalDisk -filter "DeviceID = 'c:' "`

`Get-WmiObject win32_service -filter "name='WinRM'"`

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-210">-Imitatie</span><span class="sxs-lookup"><span data-stu-id="36a0f-210">-Impersonation</span></span>

<span data-ttu-id="36a0f-211">Hiermee geeft u het imitatie niveau op dat moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="36a0f-211">Specifies the impersonation level to use.</span></span>

<span data-ttu-id="36a0f-212">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="36a0f-212">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="36a0f-213">0: standaard.</span><span class="sxs-lookup"><span data-stu-id="36a0f-213">0: Default.</span></span> <span data-ttu-id="36a0f-214">Hiermee wordt het lokale REGI ster voor het standaard imitatie niveau gelezen.</span><span class="sxs-lookup"><span data-stu-id="36a0f-214">Reads the local registry for the default impersonation level.</span></span> <span data-ttu-id="36a0f-215">De standaard instelling is doorgaans ingesteld op **imiteren**.</span><span class="sxs-lookup"><span data-stu-id="36a0f-215">The default is usually set to **Impersonate**.</span></span>
- <span data-ttu-id="36a0f-216">1: anoniem.</span><span class="sxs-lookup"><span data-stu-id="36a0f-216">1: Anonymous.</span></span> <span data-ttu-id="36a0f-217">Hiermee worden de referenties van de aanroep functie verborgen.</span><span class="sxs-lookup"><span data-stu-id="36a0f-217">Hides the credentials of the caller.</span></span>
- <span data-ttu-id="36a0f-218">2: identificeren.</span><span class="sxs-lookup"><span data-stu-id="36a0f-218">2: Identify.</span></span> <span data-ttu-id="36a0f-219">Hiermee kunnen objecten query's uitvoeren op de referenties van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="36a0f-219">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="36a0f-220">3: imiteren.</span><span class="sxs-lookup"><span data-stu-id="36a0f-220">3: Impersonate.</span></span> <span data-ttu-id="36a0f-221">Toestaan dat objecten de referenties van de aanroep functie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="36a0f-221">Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="36a0f-222">4: delegeren.</span><span class="sxs-lookup"><span data-stu-id="36a0f-222">4: Delegate.</span></span> <span data-ttu-id="36a0f-223">Hiermee kunnen objecten andere objecten toestaan de referenties van de aanroeper te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="36a0f-223">Allows objects to permit other objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-224">-Lijst</span><span class="sxs-lookup"><span data-stu-id="36a0f-224">-List</span></span>

<span data-ttu-id="36a0f-225">Hiermee worden de namen opgehaald van de WMI-klassen in de naam ruimte van de WMI-opslag plaats die is opgegeven door de para meter van de **naam ruimte** .</span><span class="sxs-lookup"><span data-stu-id="36a0f-225">Gets the names of the WMI classes in the WMI repository namespace that is specified by the **Namespace** parameter.</span></span>

<span data-ttu-id="36a0f-226">Als u de **lijst** parameter opgeeft, maar niet de para meter van de **naam ruimte** , `Get-WmiObject` wordt standaard de **Root\Cimv2** -naam ruimte gebruikt.</span><span class="sxs-lookup"><span data-stu-id="36a0f-226">If you specify the **List** parameter, but not the **Namespace** parameter, `Get-WmiObject` uses the **Root\Cimv2** namespace by default.</span></span> <span data-ttu-id="36a0f-227">Deze cmdlet gebruikt niet de standaard register vermelding voor de **naam ruimte** in de `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WBEM\Scripting` register sleutel om de standaard naam ruimte te bepalen.</span><span class="sxs-lookup"><span data-stu-id="36a0f-227">This cmdlet does not use the **Default Namespace** registry entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WBEM\Scripting` registry key to determine the default namespace.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-228">-Land instellingen</span><span class="sxs-lookup"><span data-stu-id="36a0f-228">-Locale</span></span>

<span data-ttu-id="36a0f-229">Hiermee geeft u de voorkeurs land instelling voor WMI-objecten.</span><span class="sxs-lookup"><span data-stu-id="36a0f-229">Specifies the preferred locale for WMI objects.</span></span>
<span data-ttu-id="36a0f-230">Voer een waarde in MS_ \<LCID\> notatie in.</span><span class="sxs-lookup"><span data-stu-id="36a0f-230">Enter a value in MS_\<LCID\> format.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-231">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="36a0f-231">-Namespace</span></span>

<span data-ttu-id="36a0f-232">Bij gebruik in combi natie met de para meter **Class** specificeert de **naam ruimte** parameter de naam ruimte van de WMI-opslag plaats waarin de opgegeven WMI-klasse zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="36a0f-232">When used with the **Class** parameter, the **Namespace** parameter specifies the WMI repository namespace where the specified WMI class is located.</span></span> <span data-ttu-id="36a0f-233">In combi natie met de para meter **List** geeft u de naam ruimte op waaruit u informatie over de WMI-klasse wilt verzamelen.</span><span class="sxs-lookup"><span data-stu-id="36a0f-233">When used with the **List** parameter, it specifies the namespace from which to gather WMI class information.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-234">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="36a0f-234">-Property</span></span>

<span data-ttu-id="36a0f-235">Hiermee geeft u de eigenschappen van de WMI-klasse op waarvan deze cmdlet gegevens ophaalt.</span><span class="sxs-lookup"><span data-stu-id="36a0f-235">Specifies the WMI class properties that this cmdlet gets information from.</span></span> <span data-ttu-id="36a0f-236">Voer de namen van de eigenschappen in.</span><span class="sxs-lookup"><span data-stu-id="36a0f-236">Enter the property names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: query
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-237">-Query uitvoeren</span><span class="sxs-lookup"><span data-stu-id="36a0f-237">-Query</span></span>

<span data-ttu-id="36a0f-238">Hiermee wordt de opgegeven WMI Query Language-instructie (WQL) uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="36a0f-238">Runs the specified WMI Query Language (WQL) statement.</span></span> <span data-ttu-id="36a0f-239">Deze para meter biedt geen ondersteuning voor gebeurtenis query's.</span><span class="sxs-lookup"><span data-stu-id="36a0f-239">This parameter does not support event queries.</span></span>

```yaml
Type: System.String
Parameter Sets: WQLQuery
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-240">-Recursief</span><span class="sxs-lookup"><span data-stu-id="36a0f-240">-Recurse</span></span>

<span data-ttu-id="36a0f-241">Zoekt in de huidige naam ruimte en alle andere naam ruimten voor de klassenaam die is opgegeven door de para meter **Class** .</span><span class="sxs-lookup"><span data-stu-id="36a0f-241">Searches the current namespace and all other namespaces for the class name that is specified by the **Class** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-242">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="36a0f-242">-ThrottleLimit</span></span>

<span data-ttu-id="36a0f-243">Hiermee geeft u het maximum aantal WMI-bewerkingen op dat tegelijkertijd kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="36a0f-243">Specifies the maximum number of WMI operations that can be executed simultaneously.</span></span> <span data-ttu-id="36a0f-244">Deze para meter is alleen geldig als de para meter **AsJob** in de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="36a0f-244">This parameter is valid only when the **AsJob** parameter is used in the command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36a0f-245">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36a0f-245">CommonParameters</span></span>

<span data-ttu-id="36a0f-246">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="36a0f-246">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="36a0f-247">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="36a0f-247">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="36a0f-248">INVOER</span><span class="sxs-lookup"><span data-stu-id="36a0f-248">INPUTS</span></span>

### <span data-ttu-id="36a0f-249">Geen</span><span class="sxs-lookup"><span data-stu-id="36a0f-249">None</span></span>

<span data-ttu-id="36a0f-250">U kunt geen pipe invoer naar `Get-WmiObject` .</span><span class="sxs-lookup"><span data-stu-id="36a0f-250">You cannot pipe input to `Get-WmiObject`.</span></span>

## <span data-ttu-id="36a0f-251">UITVOER</span><span class="sxs-lookup"><span data-stu-id="36a0f-251">OUTPUTS</span></span>

### <span data-ttu-id="36a0f-252">PSObject of System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="36a0f-252">PSObject or System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="36a0f-253">Wanneer u de para meter **AsJob** gebruikt, retourneert de cmdlet een taak object.</span><span class="sxs-lookup"><span data-stu-id="36a0f-253">When you use the **AsJob** parameter, the cmdlet returns a job object.</span></span> <span data-ttu-id="36a0f-254">Anders is het object dat `Get-WmiObject` retourneert, afhankelijk van de waarde van de **klasse** para meter.</span><span class="sxs-lookup"><span data-stu-id="36a0f-254">Otherwise, the object that `Get-WmiObject` returns depends on the value of the **Class** parameter.</span></span>

## <span data-ttu-id="36a0f-255">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="36a0f-255">NOTES</span></span>

<span data-ttu-id="36a0f-256">Om toegang te krijgen tot WMI-gegevens op een externe computer, moet de cmdlet worden uitgevoerd onder een account dat lid is van de lokale groep Administrators op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="36a0f-256">To access WMI information on a remote computer, the cmdlet must run under an account that is a member of the local administrators group on the remote computer.</span></span> <span data-ttu-id="36a0f-257">Of het standaard toegangs beheer voor de WMI-naam ruimte van de externe opslag plaats kan worden gewijzigd om toegangs rechten te geven voor andere accounts.</span><span class="sxs-lookup"><span data-stu-id="36a0f-257">Or, the default access control on the WMI namespace of the remote repository can be changed to give access rights to other accounts.</span></span>

<span data-ttu-id="36a0f-258">Standaard worden slechts enkele eigenschappen van elke WMI-klasse weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="36a0f-258">Only some of the properties of each WMI class are displayed by default.</span></span> <span data-ttu-id="36a0f-259">De set eigenschappen die voor elke WMI-klasse wordt weer gegeven, is opgegeven in het XML-configuratie bestand van Types.ps1.</span><span class="sxs-lookup"><span data-stu-id="36a0f-259">The set of properties that is displayed for each WMI class is specified in the Types.ps1xml configuration file.</span></span> <span data-ttu-id="36a0f-260">Als u alle eigenschappen van een WMI-object wilt ophalen, gebruikt u de `Get-Member` `Format-List` cmdlets of.</span><span class="sxs-lookup"><span data-stu-id="36a0f-260">To get all properties of a WMI object, use the `Get-Member` or `Format-List` cmdlets.</span></span>

## <span data-ttu-id="36a0f-261">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="36a0f-261">RELATED LINKS</span></span>

[<span data-ttu-id="36a0f-262">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="36a0f-262">Invoke-WmiMethod</span></span>](Invoke-WmiMethod.md)

[<span data-ttu-id="36a0f-263">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="36a0f-263">Remove-WmiObject</span></span>](Remove-WmiObject.md)

[<span data-ttu-id="36a0f-264">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="36a0f-264">Set-WmiInstance</span></span>](Set-WmiInstance.md)

[<span data-ttu-id="36a0f-265">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="36a0f-265">Get-WSManInstance</span></span>](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[<span data-ttu-id="36a0f-266">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="36a0f-266">Invoke-WSManAction</span></span>](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[<span data-ttu-id="36a0f-267">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="36a0f-267">New-WSManInstance</span></span>](../Microsoft.WsMan.Management/New-WSManInstance.md)

[<span data-ttu-id="36a0f-268">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="36a0f-268">Remove-WSManInstance</span></span>](../Microsoft.WsMan.Management/Remove-WSManInstance.md)
