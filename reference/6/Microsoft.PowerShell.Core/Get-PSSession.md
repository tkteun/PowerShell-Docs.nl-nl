---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSession
ms.openlocfilehash: cee14ce93af87d33b4d9d9665c3ef5aaa2aec1d5
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387444"
---
# <span data-ttu-id="32a51-103">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="32a51-103">Get-PSSession</span></span>

## <span data-ttu-id="32a51-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="32a51-104">SYNOPSIS</span></span>
<span data-ttu-id="32a51-105">Hiermee haalt u de Power shell-sessies op lokale en externe computers op.</span><span class="sxs-lookup"><span data-stu-id="32a51-105">Gets the PowerShell sessions on local and remote computers.</span></span>

## <span data-ttu-id="32a51-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="32a51-106">SYNTAX</span></span>

### <span data-ttu-id="32a51-107">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="32a51-107">Name (Default)</span></span>

```
Get-PSSession [-Name <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="32a51-108">ComputerInstanceId</span><span class="sxs-lookup"><span data-stu-id="32a51-108">ComputerInstanceId</span></span>

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="32a51-109">ComputerName</span><span class="sxs-lookup"><span data-stu-id="32a51-109">ComputerName</span></span>

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="32a51-110">ConnectionUriInstanceId</span><span class="sxs-lookup"><span data-stu-id="32a51-110">ConnectionUriInstanceId</span></span>

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-ThrottleLimit <Int32>] [-State <SessionFilterState>]
 [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="32a51-111">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="32a51-111">ConnectionUri</span></span>

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-ThrottleLimit <Int32>] [-State <SessionFilterState>]
 [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### <span data-ttu-id="32a51-112">VMName</span><span class="sxs-lookup"><span data-stu-id="32a51-112">VMName</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="32a51-113">ContainerId</span><span class="sxs-lookup"><span data-stu-id="32a51-113">ContainerId</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="32a51-114">ContainerIdInstanceId</span><span class="sxs-lookup"><span data-stu-id="32a51-114">ContainerIdInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### <span data-ttu-id="32a51-115">VMId</span><span class="sxs-lookup"><span data-stu-id="32a51-115">VMId</span></span>

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -VMId <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="32a51-116">VMIdInstanceId</span><span class="sxs-lookup"><span data-stu-id="32a51-116">VMIdInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -VMId <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="32a51-117">VMNameInstanceId</span><span class="sxs-lookup"><span data-stu-id="32a51-117">VMNameInstanceId</span></span>

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -VMName <String[]> [<CommonParameters>]
```

### <span data-ttu-id="32a51-118">InstanceId</span><span class="sxs-lookup"><span data-stu-id="32a51-118">InstanceId</span></span>

```
Get-PSSession [-InstanceId <Guid[]>] [<CommonParameters>]
```

### <span data-ttu-id="32a51-119">Id</span><span class="sxs-lookup"><span data-stu-id="32a51-119">Id</span></span>

```
Get-PSSession [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="32a51-120">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="32a51-120">DESCRIPTION</span></span>

<span data-ttu-id="32a51-121">De `Get-PSSession` cmdlet haalt de door de gebruiker beheerde Power shell-sessies ( **PSSessions** ) op lokale en externe computers op.</span><span class="sxs-lookup"><span data-stu-id="32a51-121">The `Get-PSSession` cmdlet gets the user-managed PowerShell sessions ( **PSSessions** ) on local and remote computers.</span></span>

<span data-ttu-id="32a51-122">Vanaf Windows Power Shell 3,0 worden sessies opgeslagen op de computers aan het externe uiteinde van elke verbinding.</span><span class="sxs-lookup"><span data-stu-id="32a51-122">Starting in Windows PowerShell 3.0, sessions are stored on the computers at the remote end of each connection.</span></span> <span data-ttu-id="32a51-123">U kunt de para meters **ComputerName** of **ConnectionUri** van gebruiken `Get-PSSession` voor het ophalen van de sessies die verbinding maken met de lokale computer of externe computers, zelfs als ze niet in de huidige sessie zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="32a51-123">You can use the **ComputerName** or **ConnectionUri** parameters of `Get-PSSession` to get the sessions that connect to the local computer or remote computers, even if they were not created in the current session.</span></span>

<span data-ttu-id="32a51-124">Zonder para meters worden `Get-PSSession` alle sessies opgehaald die in de huidige sessie zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="32a51-124">Without parameters, `Get-PSSession` gets all sessions that were created in the current session.</span></span>

<span data-ttu-id="32a51-125">Gebruik de filter parameters, zoals **naam** , **id** , **InstanceId** , **status** , **ApplicationName** en **configuratiepad** om te selecteren uit de sessies die worden `Get-PSSession` geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="32a51-125">Use the filtering parameters, including **Name** , **ID** , **InstanceID** , **State** , **ApplicationName** , and **ConfigurationName** to select from among the sessions that `Get-PSSession` returns.</span></span>

<span data-ttu-id="32a51-126">Gebruik de resterende para meters voor het configureren van de tijdelijke verbinding waarbij de `Get-PSSession` opdracht wordt uitgevoerd wanneer u de para meter **ComputerName** of **ConnectionUri** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="32a51-126">Use the remaining parameters to configure the temporary connection in which the `Get-PSSession` command runs when you use the **ComputerName** or **ConnectionUri** parameters.</span></span>

<span data-ttu-id="32a51-127">Opmerking: in Windows Power Shell 2,0, zonder para meters, worden `Get-PSSession` alle sessies opgehaald die in de huidige sessie zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="32a51-127">NOTE: In Windows PowerShell 2.0, without parameters, `Get-PSSession` gets all sessions that were created in the current session.</span></span> <span data-ttu-id="32a51-128">De para meter **ComputerName** haalt sessies op die in de huidige sessie zijn gemaakt en maakt verbinding met de opgegeven computer.</span><span class="sxs-lookup"><span data-stu-id="32a51-128">The **ComputerName** parameter gets sessions that were created in the current session and connect to the specified computer.</span></span>

<span data-ttu-id="32a51-129">Zie [about_PSSessions](about/about_PSSessions.md)voor meer informatie over Power shell-sessies.</span><span class="sxs-lookup"><span data-stu-id="32a51-129">For more information about PowerShell sessions, see [about_PSSessions](about/about_PSSessions.md).</span></span>

## <span data-ttu-id="32a51-130">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="32a51-130">EXAMPLES</span></span>

### <span data-ttu-id="32a51-131">Voor beeld 1: sessies die zijn gemaakt in de huidige sessie ophalen</span><span class="sxs-lookup"><span data-stu-id="32a51-131">Example 1: Get sessions created in the current session</span></span>

```powershell
Get-PSSession
```

<span data-ttu-id="32a51-132">Met deze opdracht worden alle **PSSessions** opgehaald die in de huidige sessie zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="32a51-132">This command gets all of the **PSSessions** that were created in the current session.</span></span> <span data-ttu-id="32a51-133">Er worden geen **PSSessions** opgehaald die zijn gemaakt in andere sessies of op andere computers, zelfs als ze verbinding maken met deze computer.</span><span class="sxs-lookup"><span data-stu-id="32a51-133">It does not get **PSSessions** that were created in other sessions or on other computers, even if they connect to this computer.</span></span>

### <span data-ttu-id="32a51-134">Voor beeld 2: sessies ophalen die zijn verbonden met de lokale computer</span><span class="sxs-lookup"><span data-stu-id="32a51-134">Example 2: Get sessions connected to the local computer</span></span>

```powershell
Get-PSSession -ComputerName "localhost"
```

<span data-ttu-id="32a51-135">Met deze opdracht worden de **PSSessions** die zijn verbonden met de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="32a51-135">This command gets the **PSSessions** that are connected to the local computer.</span></span> <span data-ttu-id="32a51-136">Typ de computer naam, localhost of een punt (.) om de lokale computer aan te duiden.</span><span class="sxs-lookup"><span data-stu-id="32a51-136">To indicate the local computer, type the computer name, localhost, or a dot (.)</span></span>

<span data-ttu-id="32a51-137">De opdracht retourneert alle sessies op de lokale computer, zelfs als ze zijn gemaakt in verschillende sessies of op verschillende computers.</span><span class="sxs-lookup"><span data-stu-id="32a51-137">The command returns all of the sessions on the local computer, even if they were created in different sessions or on different computers.</span></span>

### <span data-ttu-id="32a51-138">Voor beeld 3: sessies ophalen die zijn verbonden met een computer</span><span class="sxs-lookup"><span data-stu-id="32a51-138">Example 3: Get sessions connected to a computer</span></span>

```powershell
Get-PSSession -ComputerName "Server02"
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  2 Session3        Server02       Disconnected  ITTasks                       Busy
  1 ScheduledJobs   Server02       Opened        Microsoft.PowerShell     Available
  3 Test            Server02       Disconnected  Microsoft.PowerShell          Busy
```

<span data-ttu-id="32a51-139">Met deze opdracht worden de **PSSessions** opgehaald die zijn verbonden met de Server02-computer.</span><span class="sxs-lookup"><span data-stu-id="32a51-139">This command gets the **PSSessions** that are connected to the Server02 computer.</span></span>

<span data-ttu-id="32a51-140">Met de opdracht worden alle sessies in Server02 geretourneerd, zelfs als ze zijn gemaakt in verschillende sessies of op verschillende computers.</span><span class="sxs-lookup"><span data-stu-id="32a51-140">The command returns all of the sessions on Server02, even if they were created in different sessions or on different computers.</span></span>

<span data-ttu-id="32a51-141">In de uitvoer ziet u dat twee van de sessies een niet-verbonden status hebben en een beschikbaarheids info.</span><span class="sxs-lookup"><span data-stu-id="32a51-141">The output shows that two of the sessions have a Disconnected state and a Busy availability.</span></span> <span data-ttu-id="32a51-142">Ze zijn in verschillende sessies gemaakt en zijn momenteel in gebruik.</span><span class="sxs-lookup"><span data-stu-id="32a51-142">They were created in different sessions and are currently in use.</span></span> <span data-ttu-id="32a51-143">De ScheduledJobs-sessie, die wordt geopend en beschikbaar, is in de huidige sessie gemaakt.</span><span class="sxs-lookup"><span data-stu-id="32a51-143">The ScheduledJobs session, which is Opened and Available, was created in the current session.</span></span>

### <span data-ttu-id="32a51-144">Voor beeld 4: resultaten van deze opdracht opslaan</span><span class="sxs-lookup"><span data-stu-id="32a51-144">Example 4: Save results of this command</span></span>

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
$s1, $s2, $s3 = Get-PSSession
```

<span data-ttu-id="32a51-145">In dit voor beeld ziet u hoe u de resultaten van een `Get-PSSession` opdracht in meerdere variabelen opslaat.</span><span class="sxs-lookup"><span data-stu-id="32a51-145">This example shows how to save the results of a `Get-PSSession` command in multiple variables.</span></span>

<span data-ttu-id="32a51-146">De eerste opdracht gebruikt de `New-PSSession` cmdlet om **PSSessions** te maken op drie externe computers.</span><span class="sxs-lookup"><span data-stu-id="32a51-146">The first command uses the `New-PSSession` cmdlet to create **PSSessions** on three remote computers.</span></span>

<span data-ttu-id="32a51-147">De tweede opdracht maakt gebruik van een `Get-PSSession` cmdlet om de drie **PSSessions** op te halen.</span><span class="sxs-lookup"><span data-stu-id="32a51-147">The second command uses a `Get-PSSession` cmdlet to get the three **PSSessions**.</span></span> <span data-ttu-id="32a51-148">Vervolgens worden alle **PSSessions** in een afzonderlijke variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="32a51-148">It then saves each of the **PSSessions** in a separate variable.</span></span>

<span data-ttu-id="32a51-149">Wanneer Power shell een matrix met objecten toewijst aan een matrix met variabelen, wordt het eerste object toegewezen aan de eerste variabele, het tweede object op de tweede variabele, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="32a51-149">When PowerShell assigns an array of objects to an array of variables, it assigns the first object to the first variable, the second object to the second variable, and so on.</span></span> <span data-ttu-id="32a51-150">Als er meer objecten zijn dan variabelen, worden alle resterende objecten toegewezen aan de laatste variabele in de matrix.</span><span class="sxs-lookup"><span data-stu-id="32a51-150">If there are more objects than variables, it assigns all remaining objects to the last variable in the array.</span></span> <span data-ttu-id="32a51-151">Als er meer variabelen zijn dan objecten, worden de extra variabelen niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="32a51-151">If there are more variables than objects, the extra variables are not used.</span></span>

### <span data-ttu-id="32a51-152">Voor beeld 5: een sessie verwijderen met een exemplaar-ID</span><span class="sxs-lookup"><span data-stu-id="32a51-152">Example 5: Delete a session by using an instance ID</span></span>

```powershell
Get-PSSession | Format-Table -Property ComputerName, InstanceID
$s = Get-PSSession -InstanceID a786be29-a6bb-40da-80fb-782c67f7db0f
Remove-PSSession -Session $s
```

<span data-ttu-id="32a51-153">In dit voor beeld ziet u hoe u een **PSSession** ophaalt met behulp van de instantie-id en vervolgens verwijdert u de **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="32a51-153">This example shows how to get a **PSSession** by using its instance ID, and then to delete the **PSSession**.</span></span>

<span data-ttu-id="32a51-154">Met de eerste opdracht worden alle **PSSessions** opgehaald die in de huidige sessie zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="32a51-154">The first command gets all of the **PSSessions** that were created in the current session.</span></span> <span data-ttu-id="32a51-155">De **PSSessions** wordt verzonden naar de cmdlet Format-Table, waarin de eigenschappen **ComputerName** en **InstanceId** van elke **PSSession** worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="32a51-155">It sends the **PSSessions** to the Format-Table cmdlet, which displays the **ComputerName** and **InstanceID** properties of each **PSSession**.</span></span>

<span data-ttu-id="32a51-156">Met de tweede opdracht wordt de `Get-PSSession` cmdlet gebruikt voor het ophalen van een bepaalde **PSSession** en om deze op te slaan in de `$s` variabele.</span><span class="sxs-lookup"><span data-stu-id="32a51-156">The second command uses the `Get-PSSession` cmdlet to get a particular **PSSession** and to save it in the `$s` variable.</span></span> <span data-ttu-id="32a51-157">De opdracht gebruikt de **InstanceId** para meter om de **PSSession** te identificeren.</span><span class="sxs-lookup"><span data-stu-id="32a51-157">The command uses the **InstanceID** parameter to identify the **PSSession**.</span></span>

<span data-ttu-id="32a51-158">De derde opdracht maakt gebruik van de Remove-PSSession cmdlet om de **PSSession** in de variabele te verwijderen `$s` .</span><span class="sxs-lookup"><span data-stu-id="32a51-158">The third command uses the Remove-PSSession cmdlet to delete the **PSSession** in the `$s` variable.</span></span>

### <span data-ttu-id="32a51-159">Voor beeld 6: een sessie met een bepaalde naam ophalen</span><span class="sxs-lookup"><span data-stu-id="32a51-159">Example 6: Get a session that has a particular name</span></span>

<span data-ttu-id="32a51-160">Met de opdrachten in dit voor beeld wordt een sessie met een bepaalde naam indeling gevonden en wordt een bepaalde sessie configuratie gebruikt en wordt vervolgens verbinding gemaakt met de sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-160">The commands in this example find a session that has a particular name format and uses a particular session configuration and then connect to the session.</span></span> <span data-ttu-id="32a51-161">U kunt een opdracht als deze gebruiken om een sessie te vinden waarin een collega een taak begon en verbinding maken om de taak te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="32a51-161">You can use a command like this one to find a session in which a colleague started a task and connect to finish the task.</span></span>

```powershell
Get-PSSession -ComputerName Server02, Server12 -Name BackupJob* -ConfigurationName ITTasks -SessionOption @{OperationTimeout=240000}
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  3 BackupJob04     Server02        Disconnected        ITTasks                  None
```

```powershell
$s = Get-PSSession -ComputerName Server02 -Name BackupJob04 -ConfigurationName ITTasks | Connect-PSSession
$s
```

```Output
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 5 BackupJob04     Server02        Opened        ITTasks                  Available
```

<span data-ttu-id="32a51-162">De eerste opdracht haalt sessies op de Server02 en Server12 externe computers met namen die beginnen met BackupJob en gebruik de ITTasks-sessie configuratie. De opdracht gebruikt de para meter **name** om het naam patroon en de para meter **configuratiepad** op te geven om de sessie configuratie op te geven.</span><span class="sxs-lookup"><span data-stu-id="32a51-162">The first command gets sessions on the Server02 and Server12 remote computers that have names that begin with BackupJob and use the ITTasks session configuration.The command uses the **Name** parameter to specify the name pattern and the **ConfigurationName** parameter to specify the session configuration.</span></span> <span data-ttu-id="32a51-163">De waarde van de para meter **SessionOption** is een hash-tabel waarmee de waarde van de **OperationTimeout** wordt ingesteld op 240000 milliseconden (4 minuten).</span><span class="sxs-lookup"><span data-stu-id="32a51-163">The value of the **SessionOption** parameter is a hash table that sets the value of the **OperationTimeout** to 240000 milliseconds (4 minutes).</span></span> <span data-ttu-id="32a51-164">Deze instelling zorgt ervoor dat de opdracht meer tijd in beslag is. De para meters **configuratiepad** en **SessionOption** worden gebruikt voor het configureren van de tijdelijke sessies waarin de `Get-PSSession` cmdlet op elke computer wordt uitgevoerd. In de uitvoer ziet u dat de opdracht de BackupJob04-sessie retourneert.</span><span class="sxs-lookup"><span data-stu-id="32a51-164">This setting gives the command more time to complete.The **ConfigurationName** and **SessionOption** parameters are used to configure the temporary sessions in which the `Get-PSSession` cmdlet runs on each computer.The output shows that the command returns the BackupJob04 session.</span></span> <span data-ttu-id="32a51-165">De sessie wordt beëindigd en de **Beschik baarheid** is geen, wat aangeeft dat deze niet in gebruik is.</span><span class="sxs-lookup"><span data-stu-id="32a51-165">The session is disconnected and the **Availability** is None, which indicates that it is not in use.</span></span>

<span data-ttu-id="32a51-166">Met de tweede opdracht wordt de `Get-PSSession` cmdlet gebruikt voor het ophalen van de BackupJob04-sessie en de cmdlet Connect-PSSession om verbinding te maken met de sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-166">The second command uses the `Get-PSSession` cmdlet to get to the BackupJob04 session and the Connect-PSSession cmdlet to connect to the session.</span></span> <span data-ttu-id="32a51-167">Met de opdracht wordt de sessie opgeslagen in de variabele $s.</span><span class="sxs-lookup"><span data-stu-id="32a51-167">The command saves the session in the $s variable.</span></span>

<span data-ttu-id="32a51-168">Met de derde opdracht wordt de sessie in de variabele $s opgehaald.</span><span class="sxs-lookup"><span data-stu-id="32a51-168">The third command gets the session in the $s variable.</span></span> <span data-ttu-id="32a51-169">In de uitvoer ziet u dat de `Connect-PSSession` opdracht is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="32a51-169">The output shows that the `Connect-PSSession` command was successful.</span></span> <span data-ttu-id="32a51-170">De sessie bevindt zich in de status **Open** en is beschikbaar voor gebruik.</span><span class="sxs-lookup"><span data-stu-id="32a51-170">The session is in the **Opened** state and is available for use.</span></span>

### <span data-ttu-id="32a51-171">Voor beeld 7: een sessie ophalen met behulp van de ID</span><span class="sxs-lookup"><span data-stu-id="32a51-171">Example 7: Get a session by using its ID</span></span>

```powershell
Get-PSSession -Id 2
```

<span data-ttu-id="32a51-172">Met deze opdracht wordt de **PSSession** met id 2 opgehaald.</span><span class="sxs-lookup"><span data-stu-id="32a51-172">This command gets the **PSSession** with ID 2.</span></span> <span data-ttu-id="32a51-173">Omdat de waarde van de eigenschap **id** alleen uniek is in de huidige sessie, is de **id-** para meter alleen geldig voor lokale opdrachten.</span><span class="sxs-lookup"><span data-stu-id="32a51-173">Because the value of the **ID** property is unique only in the current session, the **Id** parameter is valid only for local commands.</span></span>

## <span data-ttu-id="32a51-174">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="32a51-174">PARAMETERS</span></span>

### <span data-ttu-id="32a51-175">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="32a51-175">-AllowRedirection</span></span>

<span data-ttu-id="32a51-176">Geeft aan dat deze cmdlet omleiding van deze verbinding met een alternatieve URI (Uniform Resource Identifier) mogelijk maakt.</span><span class="sxs-lookup"><span data-stu-id="32a51-176">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="32a51-177">Standaard worden verbindingen door Power shell niet omgeleid.</span><span class="sxs-lookup"><span data-stu-id="32a51-177">By default, PowerShell does not redirect connections.</span></span>

<span data-ttu-id="32a51-178">Met deze para meter configureert u de tijdelijke verbinding die wordt gemaakt om een opdracht uit te voeren `Get-PSSession` met de para meter **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="32a51-178">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ConnectionUri** parameter.</span></span>

<span data-ttu-id="32a51-179">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="32a51-179">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-180">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="32a51-180">-ApplicationName</span></span>

<span data-ttu-id="32a51-181">Hiermee geeft u de naam van een toepassing op.</span><span class="sxs-lookup"><span data-stu-id="32a51-181">Specifies the name of an application.</span></span> <span data-ttu-id="32a51-182">Deze cmdlet maakt alleen verbinding met sessies die gebruikmaken van de opgegeven toepassing.</span><span class="sxs-lookup"><span data-stu-id="32a51-182">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="32a51-183">Voer het segment van de toepassings naam van de verbindings-URI in.</span><span class="sxs-lookup"><span data-stu-id="32a51-183">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="32a51-184">In de volgende verbindings-URI is de naam van de toepassing bijvoorbeeld WSMan: `http://localhost:5985/WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="32a51-184">For example, in the following connection URI, the application name is WSMan: `http://localhost:5985/WSMAN`.</span></span> <span data-ttu-id="32a51-185">De toepassings naam van een sessie wordt opgeslagen in de eigenschap **runs Pace. Connection info. appName** van de sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-185">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="32a51-186">De waarde van deze para meter wordt gebruikt voor het selecteren en filteren van sessies.</span><span class="sxs-lookup"><span data-stu-id="32a51-186">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="32a51-187">De toepassing die door de sessie wordt gebruikt, wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="32a51-187">It does not change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-188">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="32a51-188">-Authentication</span></span>

<span data-ttu-id="32a51-189">Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van referenties voor de sessie waarin de `Get-PSSession` opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="32a51-189">Specifies the mechanism that is used to authenticate credentials for the session in which the `Get-PSSession` command runs.</span></span>

<span data-ttu-id="32a51-190">Met deze para meter configureert u de tijdelijke verbinding die wordt gemaakt om een opdracht uit te voeren `Get-PSSession` met de para meter **ComputerName** of **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="32a51-190">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="32a51-191">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="32a51-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="32a51-192">Standaard</span><span class="sxs-lookup"><span data-stu-id="32a51-192">Default</span></span>
- <span data-ttu-id="32a51-193">Basic</span><span class="sxs-lookup"><span data-stu-id="32a51-193">Basic</span></span>
- <span data-ttu-id="32a51-194">CredSSP</span><span class="sxs-lookup"><span data-stu-id="32a51-194">Credssp</span></span>
- <span data-ttu-id="32a51-195">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="32a51-195">Digest</span></span>
- <span data-ttu-id="32a51-196">Kerberos</span><span class="sxs-lookup"><span data-stu-id="32a51-196">Kerberos</span></span>
- <span data-ttu-id="32a51-197">Negotiate</span><span class="sxs-lookup"><span data-stu-id="32a51-197">Negotiate</span></span>
- <span data-ttu-id="32a51-198">NegotiateWithImplicitCredential.</span><span class="sxs-lookup"><span data-stu-id="32a51-198">NegotiateWithImplicitCredential.</span></span>

<span data-ttu-id="32a51-199">De standaard waarde is standaard.</span><span class="sxs-lookup"><span data-stu-id="32a51-199">The default value is Default.</span></span>

<span data-ttu-id="32a51-200">Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.</span><span class="sxs-lookup"><span data-stu-id="32a51-200">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

<span data-ttu-id="32a51-201">Let op: de verificatie van de referentie provider (CredSSP), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten die verificatie vereisen voor meer dan één bron, zoals het openen van een externe netwerk share.</span><span class="sxs-lookup"><span data-stu-id="32a51-201">CAUTION: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="32a51-202">Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.</span><span class="sxs-lookup"><span data-stu-id="32a51-202">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="32a51-203">Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.</span><span class="sxs-lookup"><span data-stu-id="32a51-203">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

<span data-ttu-id="32a51-204">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="32a51-204">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-205">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="32a51-205">-CertificateThumbprint</span></span>

<span data-ttu-id="32a51-206">Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat gemachtigd is om de sessie te maken waarin de `Get-PSSession` opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="32a51-206">Specifies the digital public key certificate (X509) of a user account that has permission to create the session in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="32a51-207">Voer de vinger afdruk van het certificaat in.</span><span class="sxs-lookup"><span data-stu-id="32a51-207">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="32a51-208">Met deze para meter configureert u de tijdelijke verbinding die wordt gemaakt om een opdracht uit te voeren `Get-PSSession` met de para meter **ComputerName** of **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="32a51-208">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="32a51-209">Certificaten worden gebruikt in authenticatie op basis van client certificaten.</span><span class="sxs-lookup"><span data-stu-id="32a51-209">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="32a51-210">Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.</span><span class="sxs-lookup"><span data-stu-id="32a51-210">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="32a51-211">Als u een certificaat vingerafdruk wilt krijgen, gebruikt u een Get-Item-of Get-ChildItem opdracht in het Power shell-certificaat: station.</span><span class="sxs-lookup"><span data-stu-id="32a51-211">To get a certificate thumbprint, use a Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

<span data-ttu-id="32a51-212">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="32a51-212">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-213">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="32a51-213">-ComputerName</span></span>

<span data-ttu-id="32a51-214">Hiermee geeft u een matrix met namen van computers op.</span><span class="sxs-lookup"><span data-stu-id="32a51-214">Specifies an array of names of computers.</span></span> <span data-ttu-id="32a51-215">Hiermee worden de sessies opgehaald die verbinding maken met de opgegeven computers.</span><span class="sxs-lookup"><span data-stu-id="32a51-215">Gets the sessions that connect to the specified computers.</span></span>
<span data-ttu-id="32a51-216">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="32a51-216">Wildcard characters are not permitted.</span></span> <span data-ttu-id="32a51-217">Er is geen standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="32a51-217">There is no default value.</span></span>

<span data-ttu-id="32a51-218">Vanaf Windows Power Shell 3,0 worden **PSSession** -objecten opgeslagen op de computers aan het externe uiteinde van elke verbinding.</span><span class="sxs-lookup"><span data-stu-id="32a51-218">Beginning in Windows PowerShell 3.0, **PSSession** objects are stored on the computers at the remote end of each connection.</span></span> <span data-ttu-id="32a51-219">Om de sessies op de opgegeven computers op te halen, maakt Power shell een tijdelijke verbinding met elke computer en voert een `Get-PSSession` opdracht uit.</span><span class="sxs-lookup"><span data-stu-id="32a51-219">To get the sessions on the specified computers, PowerShell creates a temporary connection to each computer and runs a `Get-PSSession` command.</span></span>

<span data-ttu-id="32a51-220">Typ de NetBIOS-naam, een IP-adres of een FQDN-naam (Fully Qualified Domain Name) van een of meer computers.</span><span class="sxs-lookup"><span data-stu-id="32a51-220">Type the NetBIOS name, an IP address, or a fully-qualified domain name of one or more computers.</span></span> <span data-ttu-id="32a51-221">Typ de computer naam, localhost of een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="32a51-221">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span>

<span data-ttu-id="32a51-222">Opmerking: met deze para meter worden alleen sessies opgehaald van computers waarop Windows Power Shell 3,0 of hoger van Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="32a51-222">Note: This parameter gets sessions only from computers that run Windows PowerShell 3.0 or later versions of PowerShell.</span></span> <span data-ttu-id="32a51-223">In eerdere versies worden geen sessies opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="32a51-223">Earlier versions do not store sessions.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerInstanceId, ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-224">-Configuratiepad</span><span class="sxs-lookup"><span data-stu-id="32a51-224">-ConfigurationName</span></span>

<span data-ttu-id="32a51-225">Hiermee geeft u de naam van een configuratie.</span><span class="sxs-lookup"><span data-stu-id="32a51-225">Specifies the name of a configuration.</span></span> <span data-ttu-id="32a51-226">Deze cmdlet wordt alleen gebruikt voor sessies die gebruikmaken van de opgegeven sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="32a51-226">This cmdlet gets only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="32a51-227">Voer een configuratie naam of de volledig gekwalificeerde resource-URI in voor een sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="32a51-227">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="32a51-228">Als u alleen de configuratie naam opgeeft, wordt de volgende schema-URI voor voegsel: `http://schemas.microsoft.com/powershell` .</span><span class="sxs-lookup"><span data-stu-id="32a51-228">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span> <span data-ttu-id="32a51-229">De configuratie naam van een sessie wordt opgeslagen in de eigenschap **configuratiepad** van de sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-229">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="32a51-230">De waarde van deze para meter wordt gebruikt voor het selecteren en filteren van sessies.</span><span class="sxs-lookup"><span data-stu-id="32a51-230">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="32a51-231">De sessie configuratie die door de sessie wordt gebruikt, wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="32a51-231">It does not change the session configuration that the session uses.</span></span>

<span data-ttu-id="32a51-232">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="32a51-232">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, VMNameInstanceId, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-233">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="32a51-233">-ConnectionUri</span></span>

<span data-ttu-id="32a51-234">Hiermee geeft u een URI op die het verbindings eindpunt definieert voor de tijdelijke sessie waarin de `Get-PSSession` opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="32a51-234">Specifies a URI that defines the connection endpoint for the temporary session in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="32a51-235">De URI moet volledig gekwalificeerd zijn.</span><span class="sxs-lookup"><span data-stu-id="32a51-235">The URI must be fully qualified.</span></span>

<span data-ttu-id="32a51-236">Met deze para meter configureert u de tijdelijke verbinding die wordt gemaakt om een opdracht uit te voeren `Get-PSSession` met de para meter **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="32a51-236">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ConnectionUri** parameter.</span></span>

<span data-ttu-id="32a51-237">De notatie van deze teken reeks is:</span><span class="sxs-lookup"><span data-stu-id="32a51-237">The format of this string is:</span></span>

`<Transport>://<ComputerName>:<Port\>/<ApplicationName>`

<span data-ttu-id="32a51-238">De standaard waarde is: `http://localhost:5985/WSMAN` .</span><span class="sxs-lookup"><span data-stu-id="32a51-238">The default value is: `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="32a51-239">Als u geen **ConnectionUri** opgeeft, kunt u de para meters **UseSSL** , **ComputerName** , **Port** en **ApplicationName** gebruiken om de **ConnectionUri** -waarden op te geven.</span><span class="sxs-lookup"><span data-stu-id="32a51-239">If you do not specify a **ConnectionUri** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span> <span data-ttu-id="32a51-240">Geldige waarden voor het transport segment van de URI zijn HTTP en HTTPS.</span><span class="sxs-lookup"><span data-stu-id="32a51-240">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="32a51-241">Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met standaard poorten: 80 voor HTTP en 443 voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="32a51-241">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="32a51-242">Als u de standaard poorten voor externe communicatie van Power shell wilt gebruiken, geeft u poort 5985 voor HTTP of 5986 op voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="32a51-242">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="32a51-243">Als de doel computer de verbinding omleidt naar een andere URI, wordt de omleiding door Power shell voor komen, tenzij u de para meter **AllowRedirection** in de opdracht gebruikt.</span><span class="sxs-lookup"><span data-stu-id="32a51-243">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

<span data-ttu-id="32a51-244">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="32a51-244">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="32a51-245">Met deze para meter worden alleen sessies opgehaald van computers waarop Windows Power Shell 3,0 of een latere versie van Windows Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="32a51-245">This parameter gets sessions only from computers that run Windows PowerShell 3.0 or later versions of Windows PowerShell.</span></span> <span data-ttu-id="32a51-246">In eerdere versies worden geen sessies opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="32a51-246">Earlier versions do not store sessions.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases: URI, CU

Required: True
Position: 0
Default value: Http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-247">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="32a51-247">-ContainerId</span></span>

<span data-ttu-id="32a51-248">Hiermee geeft u een matrix met Id's van containers op.</span><span class="sxs-lookup"><span data-stu-id="32a51-248">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="32a51-249">Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven containers.</span><span class="sxs-lookup"><span data-stu-id="32a51-249">This cmdlet starts an interactive session with each of the specified containers.</span></span> <span data-ttu-id="32a51-250">Gebruik de `docker ps` opdracht om een lijst met container-id's op te halen.</span><span class="sxs-lookup"><span data-stu-id="32a51-250">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="32a51-251">Zie de Help voor de opdracht [docker PS](https://docs.docker.com/engine/reference/commandline/ps/) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="32a51-251">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId, ContainerIdInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-252">-Credential</span><span class="sxs-lookup"><span data-stu-id="32a51-252">-Credential</span></span>

<span data-ttu-id="32a51-253">Hiermee geeft u een gebruikers referentie op.</span><span class="sxs-lookup"><span data-stu-id="32a51-253">Specifies a user credential.</span></span> <span data-ttu-id="32a51-254">Met deze cmdlet wordt de opdracht uitgevoerd met de machtigingen van de opgegeven gebruiker.</span><span class="sxs-lookup"><span data-stu-id="32a51-254">This cmdlet runs the command with the permissions of the specified user.</span></span> <span data-ttu-id="32a51-255">Geef een gebruikers account op dat is gemachtigd om verbinding te maken met de externe computer en een opdracht uit te voeren `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="32a51-255">Specify a user account that has permission to connect to the remote computer and run a `Get-PSSession` command.</span></span> <span data-ttu-id="32a51-256">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="32a51-256">The default is the current user.</span></span>

<span data-ttu-id="32a51-257">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="32a51-257">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="32a51-258">Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="32a51-258">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="32a51-259">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="32a51-259">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="32a51-260">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="32a51-260">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

<span data-ttu-id="32a51-261">Deze para meter wordt geconfigureerd voor de tijdelijke verbinding die wordt gemaakt om een opdracht uit te voeren `Get-PSSession` met de para meter **ComputerName** of **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="32a51-261">This parameter configures to the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="32a51-262">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="32a51-262">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-263">-Id</span><span class="sxs-lookup"><span data-stu-id="32a51-263">-Id</span></span>

<span data-ttu-id="32a51-264">Hiermee geeft u een matrix met sessie-Id's op.</span><span class="sxs-lookup"><span data-stu-id="32a51-264">Specifies an array of session IDs.</span></span> <span data-ttu-id="32a51-265">Met deze cmdlet worden alleen de sessies met de opgegeven Id's opgehaald.</span><span class="sxs-lookup"><span data-stu-id="32a51-265">This cmdlet gets only the sessions with the specified IDs.</span></span> <span data-ttu-id="32a51-266">Typ een of meer Id's, gescheiden door komma's, of gebruik de operator Range (..) om een bereik van Id's op te geven.</span><span class="sxs-lookup"><span data-stu-id="32a51-266">Type one or more IDs, separated by commas, or use the range operator (..) to specify a range of IDs.</span></span> <span data-ttu-id="32a51-267">U kunt de ID-para meter niet gebruiken in combi natie met de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="32a51-267">You cannot use the ID parameter together with the **ComputerName** parameter.</span></span>

<span data-ttu-id="32a51-268">Een ID is een geheel getal dat de door de gebruiker beheerde sessies op unieke wijze identificeert in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-268">An ID is an integer that uniquely identifies the user-managed sessions in the current session.</span></span> <span data-ttu-id="32a51-269">Het is gemakkelijker te onthouden en te typen dan de **InstanceId** , maar is alleen uniek binnen de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-269">It is easier to remember and type than the **InstanceId** , but it is unique only within the current session.</span></span> <span data-ttu-id="32a51-270">De ID van een sessie wordt opgeslagen in de eigenschap ID van de sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-270">The ID of a session is stored in the ID property of the session.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-271">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="32a51-271">-InstanceId</span></span>

<span data-ttu-id="32a51-272">Hiermee geeft u een matrix met exemplaar-Id's van sessies.</span><span class="sxs-lookup"><span data-stu-id="32a51-272">Specifies an array of instance IDs of sessions.</span></span> <span data-ttu-id="32a51-273">Met deze cmdlet worden alleen de sessies met de opgegeven exemplaar-Id's opgehaald.</span><span class="sxs-lookup"><span data-stu-id="32a51-273">This cmdlet gets only the sessions with the specified instance IDs.</span></span>

<span data-ttu-id="32a51-274">De exemplaar-ID is een GUID waarmee een sessie op een lokale of externe computer uniek wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="32a51-274">The instance ID is a GUID that uniquely identifies a session on a local or remote computer.</span></span> <span data-ttu-id="32a51-275">De **InstanceId** is uniek, zelfs wanneer er meerdere sessies in Power shell worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="32a51-275">The **InstanceID** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="32a51-276">De exemplaar-ID van een sessie wordt opgeslagen in de eigenschap **InstanceId** van de sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-276">The instance ID of a session is stored in the **InstanceID** property of the session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, VMNameInstanceId, ContainerIdInstanceId, VMIdInstanceId
Aliases:

Required: True (ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId), False (InstanceId)
Position: Named
Default value: All sessions
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-277">-Name</span><span class="sxs-lookup"><span data-stu-id="32a51-277">-Name</span></span>

<span data-ttu-id="32a51-278">Hiermee geeft u een matrix met sessie namen op.</span><span class="sxs-lookup"><span data-stu-id="32a51-278">Specifies an array of session names.</span></span> <span data-ttu-id="32a51-279">Met deze cmdlet worden alleen de sessies met de opgegeven beschrijvende namen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="32a51-279">This cmdlet gets only the sessions that have the specified friendly names.</span></span> <span data-ttu-id="32a51-280">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="32a51-280">Wildcard characters are permitted.</span></span>

<span data-ttu-id="32a51-281">De beschrijvende naam van een sessie wordt opgeslagen in de eigenschap **name** van de sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-281">The friendly name of a session is stored in the **Name** property of the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri, ContainerId, VMId, VMName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="32a51-282">-Port</span><span class="sxs-lookup"><span data-stu-id="32a51-282">-Port</span></span>

<span data-ttu-id="32a51-283">Hiermee geeft u de opgegeven netwerk poort die wordt gebruikt voor de tijdelijke verbinding waarin de `Get-PSSession` opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="32a51-283">Specifies the specified network port that is used for the temporary connection in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="32a51-284">Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="32a51-284">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="32a51-285">De standaard poorten zijn 5985, de WinRM-poort voor HTTP en 5986, de WinRM-poort voor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="32a51-285">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="32a51-286">Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren.</span><span class="sxs-lookup"><span data-stu-id="32a51-286">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="32a51-287">Als u de listener wilt configureren, typt u de volgende twee opdrachten bij de Power shell-prompt:</span><span class="sxs-lookup"><span data-stu-id="32a51-287">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="32a51-288">Deze para meter wordt geconfigureerd voor de tijdelijke verbinding die wordt gemaakt om een opdracht uit te voeren `Get-PSSession` met de para meter **ComputerName** of **ConnectionUri** .</span><span class="sxs-lookup"><span data-stu-id="32a51-288">This parameter configures to the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** or **ConnectionUri** parameter.</span></span>

<span data-ttu-id="32a51-289">Gebruik de para meter **poort** alleen als dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="32a51-289">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="32a51-290">De **poort** die in de opdracht is ingesteld, is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="32a51-290">The **Port** set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="32a51-291">Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.</span><span class="sxs-lookup"><span data-stu-id="32a51-291">An alternate port setting might prevent the command from running on all computers.</span></span>

<span data-ttu-id="32a51-292">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="32a51-292">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: 5985, 5986
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-293">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="32a51-293">-SessionOption</span></span>

<span data-ttu-id="32a51-294">Hiermee geeft u geavanceerde opties voor de sessie op.</span><span class="sxs-lookup"><span data-stu-id="32a51-294">Specifies advanced options for the session.</span></span> <span data-ttu-id="32a51-295">Voer een **SessionOption** -object in, zoals het, dat u maakt met behulp van de cmdlet New-PSSessionOption, of een hash-tabel waarin de sleutels de naam van de sessie optie zijn en de waarden zijn de waarden van de sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-295">Enter a **SessionOption** object, such as one that you create by using the New-PSSessionOption cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="32a51-296">De standaard waarden voor de opties worden bepaald door de waarde van de $PSSessionOption voorkeurs variabele, als deze is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="32a51-296">The default values for the options are determined by the value of the $PSSessionOption preference variable, if it is set.</span></span> <span data-ttu-id="32a51-297">Anders worden de standaard waarden bepaald door opties die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="32a51-297">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="32a51-298">De waarden van de sessie optie hebben voor rang op de standaard waarden voor sessies die zijn ingesteld in de $PSSessionOption voorkeurs variabele en in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="32a51-298">The session option values take precedence over default values for sessions set in the $PSSessionOption preference variable and in the session configuration.</span></span> <span data-ttu-id="32a51-299">Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="32a51-299">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="32a51-300">Zie voor een beschrijving van de sessie opties, met inbegrip van de standaard waarden `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="32a51-300">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="32a51-301">Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` voorkeurs [about_Preference_Variables](About/about_Preference_Variables.md)variabele.</span><span class="sxs-lookup"><span data-stu-id="32a51-301">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="32a51-302">Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.</span><span class="sxs-lookup"><span data-stu-id="32a51-302">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-303">-Status</span><span class="sxs-lookup"><span data-stu-id="32a51-303">-State</span></span>

<span data-ttu-id="32a51-304">Hiermee geeft u een sessie status op.</span><span class="sxs-lookup"><span data-stu-id="32a51-304">Specifies a session state.</span></span> <span data-ttu-id="32a51-305">Met deze cmdlet worden alleen sessies in de opgegeven status opgehaald.</span><span class="sxs-lookup"><span data-stu-id="32a51-305">This cmdlet gets only sessions in the specified state.</span></span> <span data-ttu-id="32a51-306">De acceptabele waarden voor deze para meter zijn: alle, geopend, losgekoppeld, gesloten en verbroken.</span><span class="sxs-lookup"><span data-stu-id="32a51-306">The acceptable values for this parameter are: All, Opened, Disconnected, Closed, and Broken.</span></span> <span data-ttu-id="32a51-307">De standaardwaarde is Alle.</span><span class="sxs-lookup"><span data-stu-id="32a51-307">The default value is All.</span></span>

<span data-ttu-id="32a51-308">De sessie status waarde is relatief ten opzichte van de huidige sessies.</span><span class="sxs-lookup"><span data-stu-id="32a51-308">The session state value is relative to the current sessions.</span></span> <span data-ttu-id="32a51-309">Sessies die niet in de huidige sessies zijn gemaakt en niet zijn verbonden met de huidige sessie, hebben de status losgekoppeld, zelfs wanneer ze zijn verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-309">Sessions that were not created in the current sessions and are not connected to the current session have a state of Disconnected even when they are connected to a different session.</span></span>

<span data-ttu-id="32a51-310">De status van een sessie wordt opgeslagen in de eigenschap **State** van de sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-310">The state of a session is stored in the **State** property of the session.</span></span>

<span data-ttu-id="32a51-311">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="32a51-311">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.SessionFilterState
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, VMNameInstanceId, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName
Aliases:
Accepted values: All, Opened, Disconnected, Closed, Broken

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-312">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="32a51-312">-ThrottleLimit</span></span>

<span data-ttu-id="32a51-313">Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om de opdracht uit te voeren `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="32a51-313">Specifies the maximum number of concurrent connections that can be established to run the `Get-PSSession` command.</span></span> <span data-ttu-id="32a51-314">Als u deze para meter weglaat of een waarde van 0 (nul) opgeeft, wordt de standaard waarde 32 gebruikt.</span><span class="sxs-lookup"><span data-stu-id="32a51-314">If you omit this parameter or enter a value of 0 (zero), the default value, 32, is used.</span></span> <span data-ttu-id="32a51-315">De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="32a51-315">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

<span data-ttu-id="32a51-316">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="32a51-316">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-317">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="32a51-317">-UseSSL</span></span>

<span data-ttu-id="32a51-318">Geeft aan dat deze cmdlet het Secure Sockets Layer-Protocol (SSL) gebruikt om de verbinding tot stand te brengen waarin de `Get-PSSession` opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="32a51-318">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish the connection in which the `Get-PSSession` command runs.</span></span> <span data-ttu-id="32a51-319">Standaard wordt SSL niet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="32a51-319">By default, SSL is not used.</span></span> <span data-ttu-id="32a51-320">Als u deze para meter gebruikt maar SSL is niet beschikbaar op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="32a51-320">If you use this parameter, but SSL is not available on the port used for the command, the command fails.</span></span>

<span data-ttu-id="32a51-321">Met deze para meter configureert u de tijdelijke verbinding die wordt gemaakt om een opdracht uit te voeren `Get-PSSession` met de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="32a51-321">This parameter configures the temporary connection that is created to run a `Get-PSSession` command with the **ComputerName** parameter.</span></span>

<span data-ttu-id="32a51-322">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="32a51-322">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-323">-VMId</span><span class="sxs-lookup"><span data-stu-id="32a51-323">-VMId</span></span>

<span data-ttu-id="32a51-324">Hiermee geeft u een ID-matrix van virtuele machines op.</span><span class="sxs-lookup"><span data-stu-id="32a51-324">Specifies an array of ID of virtual machines.</span></span> <span data-ttu-id="32a51-325">Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="32a51-325">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="32a51-326">Als u de virtuele machines wilt zien die voor u beschikbaar zijn, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="32a51-326">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId, VMIdInstanceId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-327">-VMName</span><span class="sxs-lookup"><span data-stu-id="32a51-327">-VMName</span></span>

<span data-ttu-id="32a51-328">Hiermee geeft u een matrix met namen van virtuele machines op.</span><span class="sxs-lookup"><span data-stu-id="32a51-328">Specifies an array of names of virtual machines.</span></span> <span data-ttu-id="32a51-329">Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="32a51-329">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span> <span data-ttu-id="32a51-330">Gebruik de cmdlet om de virtuele machines weer te geven die voor u beschikbaar zijn `Get-VM` .</span><span class="sxs-lookup"><span data-stu-id="32a51-330">To see the virtual machines that are available to you, use the `Get-VM` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMNameInstanceId, VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="32a51-331">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="32a51-331">CommonParameters</span></span>

<span data-ttu-id="32a51-332">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="32a51-332">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="32a51-333">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="32a51-333">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="32a51-334">INVOER</span><span class="sxs-lookup"><span data-stu-id="32a51-334">INPUTS</span></span>

### <span data-ttu-id="32a51-335">Geen</span><span class="sxs-lookup"><span data-stu-id="32a51-335">None</span></span>

<span data-ttu-id="32a51-336">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="32a51-336">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="32a51-337">UITVOER</span><span class="sxs-lookup"><span data-stu-id="32a51-337">OUTPUTS</span></span>

### <span data-ttu-id="32a51-338">System. Management. Automation. Runspaces. PSSession</span><span class="sxs-lookup"><span data-stu-id="32a51-338">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="32a51-339">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="32a51-339">NOTES</span></span>

- <span data-ttu-id="32a51-340">Met deze cmdlet worden door gebruikers beheerde sessies **PSSession** objecten, zoals de-cmdlets New-PSSession, `Enter-PSSession` en Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="32a51-340">This cmdlet gets user-managed sessions **PSSession** objects" such as those that are created by using the New-PSSession, `Enter-PSSession`, and Invoke-Command cmdlets.</span></span> <span data-ttu-id="32a51-341">Er wordt geen door het systeem beheerde sessie opgehaald die wordt gemaakt wanneer u Power shell start.</span><span class="sxs-lookup"><span data-stu-id="32a51-341">It does not get the system-managed session that is created when you start PowerShell.</span></span>
- <span data-ttu-id="32a51-342">Vanaf Windows Power Shell 3,0 worden **PSSession** -objecten opgeslagen op de computer die zich aan de server zijde bevindt of het einde van een verbinding ontvangt.</span><span class="sxs-lookup"><span data-stu-id="32a51-342">Starting in Windows PowerShell 3.0, **PSSession** objects are stored on the computer that is at the server-side or receiving end of a connection.</span></span> <span data-ttu-id="32a51-343">Voor het ophalen van de sessies die zijn opgeslagen op de lokale computer of een externe computer, brengt Power shell een tijdelijke sessie tot stand met de opgegeven computer en worden query opdrachten uitgevoerd in de sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-343">To get the sessions that are stored on the local computer or a remote computer, PowerShell establishes a temporary session to the specified computer and runs query commands in the session.</span></span>
- <span data-ttu-id="32a51-344">Als u sessies wilt ontvangen die verbinding maken met een externe computer, gebruikt u de para meters **ComputerName** of **ConnectionUri** om de externe computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="32a51-344">To get sessions that connect to a remote computer, use the **ComputerName** or **ConnectionUri** parameters to specify the remote computer.</span></span> <span data-ttu-id="32a51-345">Als u de sessies wilt filteren die `Get-PSSession` worden opgehaald, gebruikt u de para meters **naam** , **id** , **InstanceId** en **status** .</span><span class="sxs-lookup"><span data-stu-id="32a51-345">To filter the sessions that `Get-PSSession` gets, use the **Name** , **ID** , **InstanceID** , and **State** parameters.</span></span> <span data-ttu-id="32a51-346">Gebruik de resterende para meters voor het configureren van de tijdelijke sessie die `Get-PSSession` gebruikt.</span><span class="sxs-lookup"><span data-stu-id="32a51-346">Use the remaining parameters to configure the temporary session that `Get-PSSession` uses.</span></span>
- <span data-ttu-id="32a51-347">Wanneer u de para meter **ComputerName** of **ConnectionUri** gebruikt, worden `Get-PSSession` alleen sessies opgehaald van computers met Windows Power Shell 3,0 en latere versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="32a51-347">When you use the **ComputerName** or **ConnectionUri** parameters, `Get-PSSession` gets only sessions from computers running Windows PowerShell 3.0 and later versions of PowerShell.</span></span>
- <span data-ttu-id="32a51-348">De waarde van de eigenschap **State** van een **PSSession** is relatief ten opzichte van de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-348">The value of the **State** property of a **PSSession** is relative to the current session.</span></span>
  <span data-ttu-id="32a51-349">Als de waarde voor de **verbinding is verbroken** , betekent dit daarom dat de **PSSession** niet is verbonden met de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-349">Therefore, a value of **Disconnected** means that the **PSSession** is not connected to the current session.</span></span> <span data-ttu-id="32a51-350">Het betekent echter niet dat de **PSSession** -verbinding met alle sessies is verbroken.</span><span class="sxs-lookup"><span data-stu-id="32a51-350">However, it does not mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="32a51-351">Deze is mogelijk verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-351">It might be connected to a different session.</span></span> <span data-ttu-id="32a51-352">Gebruik de eigenschap **Beschik baarheid** om te bepalen of u verbinding kunt maken met de **PSSession** via de huidige sessie en hoe u er opnieuw verbinding mee maakt.</span><span class="sxs-lookup"><span data-stu-id="32a51-352">To determine whether you can connect or reconnect to the **PSSession** from the current session, use the **Availability** property.</span></span>

<span data-ttu-id="32a51-353">Een **beschikbaarheids** waarde van **geen** geeft aan dat u verbinding kunt maken met de sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-353">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="32a51-354">De waarde **bezet** geeft aan dat u geen verbinding kunt maken met de **PSSession** omdat deze is verbonden met een andere sessie.</span><span class="sxs-lookup"><span data-stu-id="32a51-354">A value of **Busy** indicates that you cannot connect to the **PSSession** because it is connected to another session.</span></span>

<span data-ttu-id="32a51-355">Zie [RunspaceState Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.runspacestate)voor meer informatie over de waarden van de eigenschap **State** van sessies.</span><span class="sxs-lookup"><span data-stu-id="32a51-355">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span>

<span data-ttu-id="32a51-356">Zie [RunspaceAvailability Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.runspaceavailability)voor meer informatie over de waarden van de eigenschap **Beschik baarheid** van sessies.</span><span class="sxs-lookup"><span data-stu-id="32a51-356">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="32a51-357">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="32a51-357">RELATED LINKS</span></span>

[<span data-ttu-id="32a51-358">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="32a51-358">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="32a51-359">Verbinding verbreken-PSSession</span><span class="sxs-lookup"><span data-stu-id="32a51-359">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="32a51-360">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="32a51-360">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="32a51-361">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="32a51-361">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="32a51-362">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="32a51-362">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="32a51-363">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="32a51-363">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="32a51-364">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="32a51-364">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="32a51-365">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="32a51-365">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="32a51-366">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="32a51-366">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="32a51-367">about_Remote</span><span class="sxs-lookup"><span data-stu-id="32a51-367">about_Remote</span></span>](About/about_Remote.md)
