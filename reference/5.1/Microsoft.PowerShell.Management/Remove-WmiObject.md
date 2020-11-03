---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WmiObject
ms.openlocfilehash: 287eb02e7de2f4182e0ecfd7f6b6a7cafb66969e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250579"
---
# <span data-ttu-id="247e2-103">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="247e2-103">Remove-WmiObject</span></span>

## <span data-ttu-id="247e2-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="247e2-104">SYNOPSIS</span></span>
<span data-ttu-id="247e2-105">Hiermee verwijdert u een exemplaar van een bestaande Windows Management Instrumentation-klasse (WMI).</span><span class="sxs-lookup"><span data-stu-id="247e2-105">Deletes an instance of an existing Windows Management Instrumentation (WMI) class.</span></span>

## <span data-ttu-id="247e2-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="247e2-106">SYNTAX</span></span>

### <span data-ttu-id="247e2-107">klasse (standaard)</span><span class="sxs-lookup"><span data-stu-id="247e2-107">class (Default)</span></span>

```
Remove-WmiObject [-Class] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="247e2-108">object</span><span class="sxs-lookup"><span data-stu-id="247e2-108">object</span></span>

```
Remove-WmiObject -InputObject <ManagementObject> [-AsJob] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="247e2-109">leertraject</span><span class="sxs-lookup"><span data-stu-id="247e2-109">path</span></span>

```
Remove-WmiObject -Path <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="247e2-110">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="247e2-110">WQLQuery</span></span>

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="247e2-111">query</span><span class="sxs-lookup"><span data-stu-id="247e2-111">query</span></span>

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="247e2-112">list</span><span class="sxs-lookup"><span data-stu-id="247e2-112">list</span></span>

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="247e2-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="247e2-113">DESCRIPTION</span></span>
<span data-ttu-id="247e2-114">De cmdlet **Remove-WmiObject** verwijdert een exemplaar van een bestaande Windows Management INSTRUMENTATION (WMI)-klasse.</span><span class="sxs-lookup"><span data-stu-id="247e2-114">The **Remove-WmiObject** cmdlet deletes an instance of an existing Windows Management Instrumentation (WMI)class.</span></span>

## <span data-ttu-id="247e2-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="247e2-115">EXAMPLES</span></span>

### <span data-ttu-id="247e2-116">Voor beeld 1: alle exemplaren van een Win32-proces sluiten</span><span class="sxs-lookup"><span data-stu-id="247e2-116">Example 1: Close all instances of a Win32 process</span></span>

```
PS C:\> notepad
PS C:\> $np = Get-WmiObject -Query "select * from win32_process where name='notepad.exe'"
PS C:\> $np | Remove-WmiObject
```

<span data-ttu-id="247e2-117">In dit voor beeld worden alle exemplaren van Notepad.exe gesloten.</span><span class="sxs-lookup"><span data-stu-id="247e2-117">This example closes all the instances of Notepad.exe.</span></span>

<span data-ttu-id="247e2-118">Met de eerste opdracht wordt een exemplaar van Klad blok gestart.</span><span class="sxs-lookup"><span data-stu-id="247e2-118">The first command starts an instance of Notepad.</span></span>

<span data-ttu-id="247e2-119">Met de tweede opdracht wordt de cmdlet Get-WmiObject gebruikt voor het ophalen van de exemplaren van de Win32_Process die overeenkomen met Notepad.exe en vervolgens opgeslagen in de variabele $np.</span><span class="sxs-lookup"><span data-stu-id="247e2-119">The second command uses the Get-WmiObject cmdlet to retrieve the instances of the Win32_Process that correspond to Notepad.exe, and then stores them in the $np variable.</span></span>

<span data-ttu-id="247e2-120">Met de derde opdracht wordt het object in de variabele $np door gegeven aan **Remove-WmiObject** , waarmee alle instanties van Notepad.exe worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="247e2-120">The third command passes the object in the $np variable to **Remove-WmiObject** , which deletes all the instances of Notepad.exe.</span></span>

### <span data-ttu-id="247e2-121">Voor beeld 2: een map verwijderen</span><span class="sxs-lookup"><span data-stu-id="247e2-121">Example 2: Delete a folder</span></span>

```
PS C:\> $a = Get-WMIObject -Query "Select * From Win32_Directory Where Name ='C:\\Test'"
PS C:\> $a | Remove-WMIObject
```

<span data-ttu-id="247e2-122">Met deze opdracht wordt de map C:\Test verwijderd.</span><span class="sxs-lookup"><span data-stu-id="247e2-122">This command deletes the C:\Test folder.</span></span>

<span data-ttu-id="247e2-123">De eerste opdracht gebruikt **Get-WMIObject** om te zoeken naar de map C:\Test en slaat het object vervolgens op in de variabele $a.</span><span class="sxs-lookup"><span data-stu-id="247e2-123">The first command uses **Get-WMIObject** to query for the C:\Test folder, and then stores the object in the $a variable.</span></span>

<span data-ttu-id="247e2-124">Met de tweede opdracht pipet u de $a variabele voor **Remove-WMIObject** , waarmee de map wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="247e2-124">The second command pipes the $a variable to **Remove-WMIObject** , which deletes the folder.</span></span>

## <span data-ttu-id="247e2-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="247e2-125">PARAMETERS</span></span>

### <span data-ttu-id="247e2-126">-AsJob</span><span class="sxs-lookup"><span data-stu-id="247e2-126">-AsJob</span></span>
<span data-ttu-id="247e2-127">Geeft aan dat deze cmdlet als achtergrond taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="247e2-127">Indicates that this cmdlet run as a background job.</span></span>
<span data-ttu-id="247e2-128">Gebruik deze para meter om opdrachten uit te voeren die lange tijd duren om te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="247e2-128">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="247e2-129">Nieuwe CIM-cmdlets, geïntroduceerd in Windows Power Shell 3,0, voert dezelfde taken uit als de WMI-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="247e2-129">New CIM cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span>
<span data-ttu-id="247e2-130">De CIM-cmdlets voldoen aan de WS-Management (WSMan)-standaarden en met de Common Information Model (CIM) standaard, waardoor de-cmdlets dezelfde technieken kunnen gebruiken voor het beheren van computers waarop het Windows-besturings systeem wordt uitgevoerd en die met andere besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="247e2-130">The CIM cmdlets comply with WS-Management (WSMan) standards and with the Common Information Model (CIM) standard, which enables the cmdlets to use the same techniques to manage computers that run the Windows operating system and those running other operating systems.</span></span>
<span data-ttu-id="247e2-131">In plaats van **Remove-WmiObject** te gebruiken, kunt u overwegen de cmdlet Remove-CimInstance te gebruiken https://go.microsoft.com/fwlink/?LinkId=227964 .</span><span class="sxs-lookup"><span data-stu-id="247e2-131">Instead of using **Remove-WmiObject** , consider using the Remove-CimInstancehttps://go.microsoft.com/fwlink/?LinkId=227964 cmdlet.</span></span>

<span data-ttu-id="247e2-132">Wanneer u de para meter *AsJob* gebruikt, retourneert de opdracht een object dat de achtergrond taak vertegenwoordigt en wordt vervolgens de opdracht prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="247e2-132">When you use the *AsJob* parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span>
<span data-ttu-id="247e2-133">U kunt in de sessie blijven werken terwijl de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="247e2-133">You can continue to work in the session while the job finishes.</span></span>
<span data-ttu-id="247e2-134">Als **Remove-WmiObject** wordt gebruikt voor een externe computer, wordt de taak gemaakt op de lokale computer en worden de resultaten van externe computers automatisch teruggestuurd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="247e2-134">If **Remove-WmiObject** is used against a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="247e2-135">Als u de taak wilt beheren, gebruikt u de cmdlets die het zelfstandige **taak** onderdeel (de **taak** -cmdlets) bevatten.</span><span class="sxs-lookup"><span data-stu-id="247e2-135">To manage the job, use the cmdlets that contain the **Job** noun (the **Job** cmdlets).</span></span>
<span data-ttu-id="247e2-136">Gebruik de cmdlet Receive-Job om de taak resultaten te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="247e2-136">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="247e2-137">Als u deze para meter voor externe computers wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="247e2-137">To use this parameter for remote computers, the local and remote computers must be configured for remoting.</span></span>
<span data-ttu-id="247e2-138">Start Windows Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="247e2-138">Start Windows PowerShell by using the Run as administrator option.</span></span>
<span data-ttu-id="247e2-139">Zie about_Remote_Requirements voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="247e2-139">For more information, see about_Remote_Requirements.</span></span>

<span data-ttu-id="247e2-140">Zie about_Jobs en about_Remote_Jobs voor meer informatie over Windows Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="247e2-140">For more information about Windows PowerShell background jobs, see about_Jobs and about_Remote_Jobs.</span></span>

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

### <span data-ttu-id="247e2-141">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="247e2-141">-Authentication</span></span>
<span data-ttu-id="247e2-142">Hiermee geeft u het verificatie niveau op dat moet worden gebruikt voor de WMI-verbinding.</span><span class="sxs-lookup"><span data-stu-id="247e2-142">Specifies the authentication level to use for the WMI connection.</span></span>
<span data-ttu-id="247e2-143">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="247e2-143">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="247e2-144">-1: ongewijzigd.</span><span class="sxs-lookup"><span data-stu-id="247e2-144">-1: Unchanged.</span></span>
- <span data-ttu-id="247e2-145">0: standaard.</span><span class="sxs-lookup"><span data-stu-id="247e2-145">0: Default.</span></span>
- <span data-ttu-id="247e2-146">1: geen.</span><span class="sxs-lookup"><span data-stu-id="247e2-146">1: None.</span></span>
<span data-ttu-id="247e2-147">Er is geen verificatie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="247e2-147">No authentication in performed.</span></span>
- <span data-ttu-id="247e2-148">2: verbinding maken.</span><span class="sxs-lookup"><span data-stu-id="247e2-148">2: Connect.</span></span>
<span data-ttu-id="247e2-149">Verificatie wordt alleen uitgevoerd wanneer de client een relatie met de toepassing tot stand brengt.</span><span class="sxs-lookup"><span data-stu-id="247e2-149">Authentication is performed only when the client establishes a relationship with the application.</span></span>
- <span data-ttu-id="247e2-150">3: bellen.</span><span class="sxs-lookup"><span data-stu-id="247e2-150">3: Call.</span></span>
<span data-ttu-id="247e2-151">Verificatie wordt alleen aan het begin van elke aanroep uitgevoerd wanneer de toepassing de aanvraag ontvangt.</span><span class="sxs-lookup"><span data-stu-id="247e2-151">Authentication is performed only at the start of each call when the application receives the request.</span></span>
- <span data-ttu-id="247e2-152">4: pakket.</span><span class="sxs-lookup"><span data-stu-id="247e2-152">4: Packet.</span></span>
<span data-ttu-id="247e2-153">Verificatie wordt uitgevoerd op alle gegevens die van de client worden ontvangen.</span><span class="sxs-lookup"><span data-stu-id="247e2-153">Authentication is performed on all the data that is received from the client.</span></span>
- <span data-ttu-id="247e2-154">5: PacketIntegrity.</span><span class="sxs-lookup"><span data-stu-id="247e2-154">5: PacketIntegrity.</span></span>
<span data-ttu-id="247e2-155">Alle gegevens die worden overgebracht tussen de client en de toepassing, worden geverifieerd en geverifieerd.</span><span class="sxs-lookup"><span data-stu-id="247e2-155">All the data that is transferred between the client and the application is authenticated and verified.</span></span>
- <span data-ttu-id="247e2-156">6: PacketPrivacy.</span><span class="sxs-lookup"><span data-stu-id="247e2-156">6: PacketPrivacy.</span></span>
<span data-ttu-id="247e2-157">De eigenschappen van de andere authenticatie niveaus worden gebruikt en alle gegevens worden versleuteld.</span><span class="sxs-lookup"><span data-stu-id="247e2-157">The properties of the other authentication levels are used, and all the data is encrypted.</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="247e2-158">-Authority</span><span class="sxs-lookup"><span data-stu-id="247e2-158">-Authority</span></span>
<span data-ttu-id="247e2-159">Hiermee geeft u de instantie op die moet worden gebruikt om de WMI-verbinding te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="247e2-159">Specifies the authority to use to authenticate the WMI connection.</span></span>
<span data-ttu-id="247e2-160">U kunt standaard NTLM-of Kerberos-verificatie opgeven.</span><span class="sxs-lookup"><span data-stu-id="247e2-160">You can specify standard NTLM or Kerberos authentication.</span></span>
<span data-ttu-id="247e2-161">Als u NTLM wilt gebruiken, stelt u de instelling van de instantie in op ntlmdomain: \<DomainName\> , waarbij \<DomainName\> een geldige NTLM-domein naam wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="247e2-161">To use NTLM, set the authority setting to ntlmdomain:\<DomainName\>, where \<DomainName\> identifies a valid NTLM domain name.</span></span>
<span data-ttu-id="247e2-162">Als u Kerberos wilt gebruiken, geeft u Kerberos op: \<DomainName\> \\ \<ServerName\> .</span><span class="sxs-lookup"><span data-stu-id="247e2-162">To use Kerberos, specify kerberos:\<DomainName\>\\\<ServerName\>.</span></span>
<span data-ttu-id="247e2-163">U kunt de instelling van de instantie niet toevoegen wanneer u verbinding maakt met de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="247e2-163">You cannot include the authority setting when you connect to the local computer.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="247e2-164">-Klasse</span><span class="sxs-lookup"><span data-stu-id="247e2-164">-Class</span></span>
<span data-ttu-id="247e2-165">Hiermee geeft u de naam van een WMI-klasse op die met deze cmdlet wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="247e2-165">Specifies the name of a WMI class that this cmdlet deletes.</span></span>

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="247e2-166">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="247e2-166">-ComputerName</span></span>
<span data-ttu-id="247e2-167">Hiermee geeft u de naam op van de computer waarop deze cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="247e2-167">Specifies the name of the computer on which this cmdlet runs.</span></span>
<span data-ttu-id="247e2-168">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="247e2-168">The default is the local computer.</span></span>

<span data-ttu-id="247e2-169">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een of meer computers.</span><span class="sxs-lookup"><span data-stu-id="247e2-169">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more computers.</span></span>
<span data-ttu-id="247e2-170">Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt (.) of localhost.</span><span class="sxs-lookup"><span data-stu-id="247e2-170">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="247e2-171">Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="247e2-171">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="247e2-172">U kunt de para meter *ComputerName* ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="247e2-172">You can use the *ComputerName* parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: class, path, WQLQuery, query, list
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="247e2-173">-Credential</span><span class="sxs-lookup"><span data-stu-id="247e2-173">-Credential</span></span>
<span data-ttu-id="247e2-174">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="247e2-174">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="247e2-175">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="247e2-175">The default is the current user.</span></span>

<span data-ttu-id="247e2-176">Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de cmdlet Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="247e2-176">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="247e2-177">Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="247e2-177">If you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="247e2-178">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="247e2-178">-EnableAllPrivileges</span></span>
<span data-ttu-id="247e2-179">Hiermee wordt aangegeven dat met deze cmdlet alle machtigingen van de huidige gebruiker worden ingeschakeld voordat de opdracht de WMI-aanroep uitvoert.</span><span class="sxs-lookup"><span data-stu-id="247e2-179">Indicates that this cmdlet enables all the permissions of the current user before the command it makes the WMI call.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="247e2-180">-Imitatie</span><span class="sxs-lookup"><span data-stu-id="247e2-180">-Impersonation</span></span>
<span data-ttu-id="247e2-181">Hiermee geeft u het imitatie niveau op dat moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="247e2-181">Specifies the impersonation level to use.</span></span>
<span data-ttu-id="247e2-182">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="247e2-182">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="247e2-183">0: standaard.</span><span class="sxs-lookup"><span data-stu-id="247e2-183">0: Default.</span></span>
<span data-ttu-id="247e2-184">Leest het lokale REGI ster voor het standaard imitatie niveau, dat meestal is ingesteld op 3: imiteren.</span><span class="sxs-lookup"><span data-stu-id="247e2-184">Reads the local registry for the default impersonation level, which is usually set to 3: Impersonate.</span></span>
- <span data-ttu-id="247e2-185">1: anoniem.</span><span class="sxs-lookup"><span data-stu-id="247e2-185">1: Anonymous.</span></span>
<span data-ttu-id="247e2-186">Hiermee worden de referenties van de aanroep functie verborgen.</span><span class="sxs-lookup"><span data-stu-id="247e2-186">Hides the credentials of the caller.</span></span>
- <span data-ttu-id="247e2-187">2: identificeren.</span><span class="sxs-lookup"><span data-stu-id="247e2-187">2: Identify.</span></span>
<span data-ttu-id="247e2-188">Hiermee kunnen objecten query's uitvoeren op de referenties van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="247e2-188">Allows objects to query the credentials of the caller.</span></span>
- <span data-ttu-id="247e2-189">3: imiteren.</span><span class="sxs-lookup"><span data-stu-id="247e2-189">3: Impersonate.</span></span>
<span data-ttu-id="247e2-190">Toestaan dat objecten de referenties van de aanroep functie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="247e2-190">Allows objects to use the credentials of the caller.</span></span>
- <span data-ttu-id="247e2-191">4: delegeren.</span><span class="sxs-lookup"><span data-stu-id="247e2-191">4: Delegate.</span></span>
<span data-ttu-id="247e2-192">Hiermee kunnen objecten andere objecten toestaan de referenties van de aanroeper te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="247e2-192">Allows objects to permit other objects to use the credentials of the caller.</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="247e2-193">-Input object</span><span class="sxs-lookup"><span data-stu-id="247e2-193">-InputObject</span></span>
<span data-ttu-id="247e2-194">Hiermee geeft u een **ManagementObject** -object moet worden gebruikt als invoer.</span><span class="sxs-lookup"><span data-stu-id="247e2-194">Specifies a **ManagementObject** object to use as input.</span></span>
<span data-ttu-id="247e2-195">Als deze para meter wordt gebruikt, worden alle andere para meters genegeerd.</span><span class="sxs-lookup"><span data-stu-id="247e2-195">When this parameter is used, all other parameters are ignored.</span></span>

```yaml
Type: System.Management.ManagementObject
Parameter Sets: object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="247e2-196">-Land instellingen</span><span class="sxs-lookup"><span data-stu-id="247e2-196">-Locale</span></span>
<span data-ttu-id="247e2-197">Hiermee geeft u de voorkeurs land instelling voor WMI-objecten.</span><span class="sxs-lookup"><span data-stu-id="247e2-197">Specifies the preferred locale for WMI objects.</span></span>
<span data-ttu-id="247e2-198">De para meter *locale* wordt opgegeven als een matrix in de MS_ \<LCID\> indeling in de gewenste volg orde.</span><span class="sxs-lookup"><span data-stu-id="247e2-198">The *Locale* parameter is specified as an array in the MS_\<LCID\> format in the preferred order.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="247e2-199">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="247e2-199">-Namespace</span></span>
<span data-ttu-id="247e2-200">Hiermee geeft u de naam ruimte van de WMI-opslag plaats waar de WMI-klasse waarnaar wordt verwezen zich bevindt als deze wordt gebruikt met de para meter *Class* .</span><span class="sxs-lookup"><span data-stu-id="247e2-200">Specifies the WMI repository namespace where the referenced WMI class is located when it is used with the *Class* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="247e2-201">-Path</span><span class="sxs-lookup"><span data-stu-id="247e2-201">-Path</span></span>
<span data-ttu-id="247e2-202">Hiermee wordt het WMI-objectpad van een WMI-klasse opgegeven, of het WMI-objectpad van een exemplaar van een WMI-klasse dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="247e2-202">Specifies the WMI object path of a WMI class, or specifies the WMI object path of an instance of a WMI class to delete.</span></span>

```yaml
Type: System.String
Parameter Sets: path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="247e2-203">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="247e2-203">-ThrottleLimit</span></span>
<span data-ttu-id="247e2-204">Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="247e2-204">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="247e2-205">Deze para meter wordt gebruikt in combi natie met de para meter *AsJob* .</span><span class="sxs-lookup"><span data-stu-id="247e2-205">This parameter is used together with the *AsJob* parameter.</span></span>
<span data-ttu-id="247e2-206">De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="247e2-206">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="247e2-207">-Confirm</span><span class="sxs-lookup"><span data-stu-id="247e2-207">-Confirm</span></span>
<span data-ttu-id="247e2-208">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="247e2-208">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="247e2-209">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="247e2-209">-WhatIf</span></span>
<span data-ttu-id="247e2-210">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="247e2-210">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="247e2-211">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="247e2-211">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="247e2-212">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="247e2-212">CommonParameters</span></span>
<span data-ttu-id="247e2-213">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="247e2-213">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="247e2-214">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="247e2-214">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="247e2-215">INVOER</span><span class="sxs-lookup"><span data-stu-id="247e2-215">INPUTS</span></span>

### <span data-ttu-id="247e2-216">System. Management. ManagementObject</span><span class="sxs-lookup"><span data-stu-id="247e2-216">System.Management.ManagementObject</span></span>
<span data-ttu-id="247e2-217">U kunt een beheer object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="247e2-217">You can pipe a management object to this cmdlet.</span></span>

## <span data-ttu-id="247e2-218">UITVOER</span><span class="sxs-lookup"><span data-stu-id="247e2-218">OUTPUTS</span></span>

### <span data-ttu-id="247e2-219">Geen, System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="247e2-219">None, System.Management.Automation.RemotingJob</span></span>
<span data-ttu-id="247e2-220">Met deze cmdlet wordt een taak object geretourneerd als u de para meter *AsJob* opgeeft.</span><span class="sxs-lookup"><span data-stu-id="247e2-220">This cmdlet returns a job object, if you specify the *AsJob* parameter.</span></span>
<span data-ttu-id="247e2-221">Anders wordt er geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="247e2-221">Otherwise, it does not generate any output.</span></span>

## <span data-ttu-id="247e2-222">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="247e2-222">NOTES</span></span>

## <span data-ttu-id="247e2-223">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="247e2-223">RELATED LINKS</span></span>

[<span data-ttu-id="247e2-224">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="247e2-224">Get-WmiObject</span></span>](Get-WmiObject.md)

[<span data-ttu-id="247e2-225">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="247e2-225">Invoke-WmiMethod</span></span>](Invoke-WmiMethod.md)

[<span data-ttu-id="247e2-226">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="247e2-226">Set-WmiInstance</span></span>](Set-WmiInstance.md)
