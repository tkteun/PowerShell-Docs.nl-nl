---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSession
ms.openlocfilehash: cd0e2b62464a4c34278d42b833a669c6c28e377f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706046"
---
# <span data-ttu-id="ef56c-102">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="ef56c-102">Remove-PSSession</span></span>

## <span data-ttu-id="ef56c-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ef56c-103">SYNOPSIS</span></span>
<span data-ttu-id="ef56c-104">Hiermee sluit u een of meer Power shell-sessies (PSSessions).</span><span class="sxs-lookup"><span data-stu-id="ef56c-104">Closes one or more PowerShell sessions (PSSessions).</span></span>

## <span data-ttu-id="ef56c-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ef56c-105">SYNTAX</span></span>

### <span data-ttu-id="ef56c-106">Id (standaard)</span><span class="sxs-lookup"><span data-stu-id="ef56c-106">Id (Default)</span></span>

```
Remove-PSSession [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ef56c-107">Sessie</span><span class="sxs-lookup"><span data-stu-id="ef56c-107">Session</span></span>

```
Remove-PSSession [-Session] <PSSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ef56c-108">ContainerId</span><span class="sxs-lookup"><span data-stu-id="ef56c-108">ContainerId</span></span>

```
Remove-PSSession -ContainerId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ef56c-109">VMId</span><span class="sxs-lookup"><span data-stu-id="ef56c-109">VMId</span></span>

```
Remove-PSSession -VMId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ef56c-110">VMName</span><span class="sxs-lookup"><span data-stu-id="ef56c-110">VMName</span></span>

```
Remove-PSSession -VMName <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ef56c-111">InstanceId</span><span class="sxs-lookup"><span data-stu-id="ef56c-111">InstanceId</span></span>

```
Remove-PSSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ef56c-112">Name</span><span class="sxs-lookup"><span data-stu-id="ef56c-112">Name</span></span>

```
Remove-PSSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ef56c-113">ComputerName</span><span class="sxs-lookup"><span data-stu-id="ef56c-113">ComputerName</span></span>

```
Remove-PSSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ef56c-114">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ef56c-114">DESCRIPTION</span></span>

<span data-ttu-id="ef56c-115">De cmdlet **Remove-PSSession** sluit Power shell-sessies (**PSSessions**) in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="ef56c-115">The **Remove-PSSession** cmdlet closes PowerShell sessions (**PSSessions**) in the current session.</span></span>
<span data-ttu-id="ef56c-116">Hiermee worden opdrachten gestopt die worden uitgevoerd in de **PSSessions**, wordt de **PSSession** beëindigd en worden de resources vrijgegeven die de **PSSession** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ef56c-116">It stops any commands that are running in the **PSSessions**, ends the **PSSession**, and releases the resources that the **PSSession** was using.</span></span>
<span data-ttu-id="ef56c-117">Als de **PSSession** is verbonden met een externe computer, sluit deze cmdlet ook de verbinding tussen de lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="ef56c-117">If the **PSSession** is connected to a remote computer, this cmdlet also closes the connection between the local and remote computers.</span></span>

<span data-ttu-id="ef56c-118">Als u een **PSSession** wilt verwijderen, voert u de *naam*, *ComputerName*, *id* of *InstanceId* van de sessie in.</span><span class="sxs-lookup"><span data-stu-id="ef56c-118">To remove a **PSSession**, enter the *Name*, *ComputerName*, *ID*, or *InstanceID* of the session.</span></span>

<span data-ttu-id="ef56c-119">Als u de *PSSession* hebt opgeslagen in een variabele, blijft het object Session in de variabele, maar wordt de status van de *PSSession* gesloten.</span><span class="sxs-lookup"><span data-stu-id="ef56c-119">If you have saved the *PSSession* in a variable, the session object remains in the variable, but the state of the *PSSession* is Closed.</span></span>

## <span data-ttu-id="ef56c-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ef56c-120">EXAMPLES</span></span>

### <span data-ttu-id="ef56c-121">Voor beeld 1: sessies verwijderen met behulp van-Id's</span><span class="sxs-lookup"><span data-stu-id="ef56c-121">Example 1: Remove sessions by using IDs</span></span>

```powershell
Remove-PSSession -Id 1, 2
```

<span data-ttu-id="ef56c-122">Met deze opdracht verwijdert u de **PSSessions** met de id's 1 en 2.</span><span class="sxs-lookup"><span data-stu-id="ef56c-122">This command removes the **PSSessions** that have IDs 1 and 2.</span></span>

### <span data-ttu-id="ef56c-123">Voor beeld 2: alle sessies in de huidige sessie verwijderen</span><span class="sxs-lookup"><span data-stu-id="ef56c-123">Example 2: Remove all the sessions in the current session</span></span>

```powershell
Get-PSSession | Remove-PSSession
Remove-PSSession -Session (Get-PSSession)
$s = Get-PSSession
Remove-PSSession -Session $s
```

<span data-ttu-id="ef56c-124">Met deze opdrachten worden alle **PSSessions** in de huidige sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ef56c-124">These commands remove all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="ef56c-125">Hoewel de drie opdracht indelingen er anders uitzien, hebben ze hetzelfde effect.</span><span class="sxs-lookup"><span data-stu-id="ef56c-125">Although the three command formats look different, they have the same effect.</span></span>

### <span data-ttu-id="ef56c-126">Voor beeld 3: sessies sluiten met behulp van namen</span><span class="sxs-lookup"><span data-stu-id="ef56c-126">Example 3: Close sessions by using names</span></span>

```powershell
$r = Get-PSSession -ComputerName Serv*
$r | Remove-PSSession
```

<span data-ttu-id="ef56c-127">Met deze opdrachten sluit u de **PSSessions** die zijn verbonden met computers die namen hebben die met Serviceart beginnen.</span><span class="sxs-lookup"><span data-stu-id="ef56c-127">These commands close the **PSSessions** that are connected to computers that have names that begin with Serv.</span></span>

### <span data-ttu-id="ef56c-128">Voor beeld 4: sessies sluiten die zijn verbonden met een poort</span><span class="sxs-lookup"><span data-stu-id="ef56c-128">Example 4: Close sessions connected to a port</span></span>

```powershell
Get-PSSession | where {$_.port -eq 90} | Remove-PSSession
```

<span data-ttu-id="ef56c-129">Met deze opdracht sluit u de **PSSessions** die zijn verbonden met poort 90.</span><span class="sxs-lookup"><span data-stu-id="ef56c-129">This command closes the **PSSessions** that are connected to port 90.</span></span>
<span data-ttu-id="ef56c-130">U kunt deze opdracht indeling gebruiken om **PSSessions** te identificeren op basis van andere eigenschappen dan *ComputerName*, *name*, *InstanceId* en *id*.</span><span class="sxs-lookup"><span data-stu-id="ef56c-130">You can use this command format to identify **PSSessions** by properties other than *ComputerName*, *Name*, *InstanceID*, and *ID*.</span></span>

### <span data-ttu-id="ef56c-131">Voor beeld 5: een sessie sluiten op basis van exemplaar-ID</span><span class="sxs-lookup"><span data-stu-id="ef56c-131">Example 5: Close a session based on instance ID</span></span>

```powershell
Get-PSSession | Format-Table ComputerName, InstanceID  -AutoSize
```

```Output
ComputerName InstanceId
------------ ----------------
Server01     875d231b-2788-4f36-9f67-2e50d63bb82a
localhost    c065ffa0-02c4-406e-84a3-dacb0d677868
Server02     4699cdbc-61d5-4e0d-b916-84f82ebede1f
Server03     4e5a3245-4c63-43e4-88d0-a7798bfc2414
TX-TEST-01   fc4e9dfa-f246-452d-9fa3-1adbdd64ae85 PS C:\> Remove-PSSession -InstanceID fc4e9dfa-f246-452d-9fa3-1adbdd64ae85
```

<span data-ttu-id="ef56c-132">Deze opdrachten laten zien hoe u een **PSSession** kunt sluiten op basis van de instantie-id of **RemoteRunspaceID**.</span><span class="sxs-lookup"><span data-stu-id="ef56c-132">These commands show how to close a **PSSession** based on its instance ID, or **RemoteRunspaceID**.</span></span>

<span data-ttu-id="ef56c-133">De eerste opdracht maakt gebruik van de cmdlet **Get-PSSession** om de **PSSessions** in de huidige sessie op te halen.</span><span class="sxs-lookup"><span data-stu-id="ef56c-133">The first command uses the **Get-PSSession** cmdlet to get the **PSSessions** in the current session.</span></span>
<span data-ttu-id="ef56c-134">Er wordt gebruikgemaakt van een pijplijn operator (|) om de **PSSessions** te verzenden naar de cmdlet Format-Table, waarmee de eigenschappen **ComputerName** en **InstanceId** worden opgemaakt in een tabel.</span><span class="sxs-lookup"><span data-stu-id="ef56c-134">It uses a pipeline operator (|) to send the **PSSessions** to the Format-Table cmdlet, which formats their **ComputerName** and **InstanceID** properties in a table.</span></span>
<span data-ttu-id="ef56c-135">De *AutoSize* -para meter comprimeert de kolommen voor weer gave.</span><span class="sxs-lookup"><span data-stu-id="ef56c-135">The *AutoSize* parameter compresses the columns for display.</span></span>

<span data-ttu-id="ef56c-136">Vanuit de resulterende weer gave kunt u de **PSSession** die moeten worden gesloten identificeren en de *InstanceId* van die **PSSession** kopiëren en plakken in de tweede opdracht.</span><span class="sxs-lookup"><span data-stu-id="ef56c-136">From the resulting display, you can identify the **PSSession** to be closed, and copy and paste the *InstanceID* of that **PSSession** into the second command.</span></span>

<span data-ttu-id="ef56c-137">De tweede opdracht maakt gebruik van de cmdlet **Remove-PSSession** om de *PSSession* te verwijderen met de opgegeven exemplaar-id.</span><span class="sxs-lookup"><span data-stu-id="ef56c-137">The second command uses the **Remove-PSSession** cmdlet to remove the *PSSession* with the specified instance ID.</span></span>

### <span data-ttu-id="ef56c-138">Voor beeld 6: een functie maken waarmee alle sessies in de huidige sessie worden verwijderd</span><span class="sxs-lookup"><span data-stu-id="ef56c-138">Example 6: Create a function that deletes all sessions in the current session</span></span>

```powershell
Function EndPSS { Get-PSSession | Remove-PSSession }
```

<span data-ttu-id="ef56c-139">Deze functie verwijdert alle **PSSessions** in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="ef56c-139">This function deletes all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="ef56c-140">Nadat u deze functie aan uw Power shell-profiel hebt toegevoegd, kunt u alle sessies verwijderen `EndPSS` .</span><span class="sxs-lookup"><span data-stu-id="ef56c-140">After you add this function to your PowerShell profile, to delete all sessions, type `EndPSS`.</span></span>

## <span data-ttu-id="ef56c-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ef56c-141">PARAMETERS</span></span>

### <span data-ttu-id="ef56c-142">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="ef56c-142">-ComputerName</span></span>

<span data-ttu-id="ef56c-143">Hiermee geeft u een matrix met namen van computers op.</span><span class="sxs-lookup"><span data-stu-id="ef56c-143">Specifies an array of names of computers.</span></span>
<span data-ttu-id="ef56c-144">Met deze cmdlet worden de **PSSessions** die zijn verbonden met de opgegeven computers gesloten.</span><span class="sxs-lookup"><span data-stu-id="ef56c-144">This cmdlet closes the **PSSessions** that are connected to the specified computers.</span></span>
<span data-ttu-id="ef56c-145">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="ef56c-145">Wildcard characters are permitted.</span></span>

<span data-ttu-id="ef56c-146">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een of meer externe computers.</span><span class="sxs-lookup"><span data-stu-id="ef56c-146">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span>
<span data-ttu-id="ef56c-147">Typ de computer naam, localhost of een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="ef56c-147">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ef56c-148">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="ef56c-148">-ContainerId</span></span>

<span data-ttu-id="ef56c-149">Hiermee geeft u een matrix met Id's van containers op.</span><span class="sxs-lookup"><span data-stu-id="ef56c-149">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="ef56c-150">Met deze cmdlet worden sessies voor elk van de opgegeven containers verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ef56c-150">This cmdlet removes sessions for each of the specified containers.</span></span> <span data-ttu-id="ef56c-151">Gebruik de `docker ps` opdracht om een lijst met container-id's op te halen.</span><span class="sxs-lookup"><span data-stu-id="ef56c-151">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="ef56c-152">Zie de Help voor de opdracht [docker PS](https://docs.docker.com/engine/reference/commandline/ps/) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ef56c-152">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ef56c-153">-Id</span><span class="sxs-lookup"><span data-stu-id="ef56c-153">-Id</span></span>

<span data-ttu-id="ef56c-154">Hiermee geeft u een matrix met Id's van sessies.</span><span class="sxs-lookup"><span data-stu-id="ef56c-154">Specifies an array of IDs of sessions.</span></span>
<span data-ttu-id="ef56c-155">Met deze cmdlet wordt de *PSSessions* met de opgegeven id's gesloten.</span><span class="sxs-lookup"><span data-stu-id="ef56c-155">This cmdlet closes the *PSSessions* with the specified IDs.</span></span>
<span data-ttu-id="ef56c-156">Typ een of meer Id's, gescheiden door komma's, of gebruik de operator Range (..) om een bereik van Id's op te geven.</span><span class="sxs-lookup"><span data-stu-id="ef56c-156">Type one or more IDs, separated by commas, or use the range operator (..) to specify a range of IDs.</span></span>

<span data-ttu-id="ef56c-157">Een ID is een geheel getal dat de **PSSession** in de huidige sessie uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="ef56c-157">An ID is an integer that uniquely identifies the **PSSession** in the current session.</span></span>
<span data-ttu-id="ef56c-158">Het is gemakkelijker te onthouden en te typen dan de *InstanceId*, maar is alleen uniek in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="ef56c-158">It is easier to remember and type than the *InstanceId*, but it is unique only in the current session.</span></span>
<span data-ttu-id="ef56c-159">Als u de ID van een **PSSession** wilt zoeken, voert u de cmdlet Get-PSSession zonder para meters uit.</span><span class="sxs-lookup"><span data-stu-id="ef56c-159">To find the ID of a **PSSession**, run the Get-PSSession cmdlet without parameters.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ef56c-160">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="ef56c-160">-InstanceId</span></span>

<span data-ttu-id="ef56c-161">Hiermee geeft u een matrix met exemplaar-Id's op.</span><span class="sxs-lookup"><span data-stu-id="ef56c-161">Specifies an array of instance IDs.</span></span>
<span data-ttu-id="ef56c-162">Met deze cmdlet wordt de **PSSessions** gesloten met de opgegeven exemplaar-id's.</span><span class="sxs-lookup"><span data-stu-id="ef56c-162">This cmdlet closes the **PSSessions** that have the specified instance IDs.</span></span>

<span data-ttu-id="ef56c-163">De exemplaar-ID is een GUID waarmee een **PSSession** in de huidige sessie uniek wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="ef56c-163">The instance ID is a GUID that uniquely identifies a **PSSession** in the current session.</span></span>
<span data-ttu-id="ef56c-164">De exemplaar-ID is uniek, zelfs wanneer er meerdere sessies worden uitgevoerd op één computer.</span><span class="sxs-lookup"><span data-stu-id="ef56c-164">The instance ID is unique, even when you have multiple sessions running on a single computer.</span></span>

<span data-ttu-id="ef56c-165">De exemplaar-ID wordt opgeslagen in de eigenschap **InstanceId** van het object dat een **PSSession** vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="ef56c-165">The instance ID is stored in the **InstanceID** property of the object that represents a **PSSession**.</span></span>
<span data-ttu-id="ef56c-166">Als u wilt zoeken naar de **InstanceId** van de **PSSessions** in de huidige sessie, typt u `Get-PSSession | Format-Table Name, ComputerName, InstanceId` .</span><span class="sxs-lookup"><span data-stu-id="ef56c-166">To find the **InstanceID** of the **PSSessions** in the current session, type `Get-PSSession | Format-Table Name, ComputerName, InstanceId`.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ef56c-167">-Name</span><span class="sxs-lookup"><span data-stu-id="ef56c-167">-Name</span></span>

<span data-ttu-id="ef56c-168">Hiermee geeft u een matrix met beschrijvende namen van sessies.</span><span class="sxs-lookup"><span data-stu-id="ef56c-168">Specifies an array of friendly names of sessions.</span></span>
<span data-ttu-id="ef56c-169">Met deze cmdlet worden de **PSSessions** met de opgegeven beschrijvende namen gesloten.</span><span class="sxs-lookup"><span data-stu-id="ef56c-169">This cmdlet closes the **PSSessions** that have the specified friendly names.</span></span>
<span data-ttu-id="ef56c-170">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="ef56c-170">Wildcard characters are permitted.</span></span>

<span data-ttu-id="ef56c-171">Omdat de beschrijvende naam van een **PSSession** mogelijk niet uniek is, moet u, wanneer u de para meter *name* gebruikt, ook de *WhatIf* of de para meter *confirm* gebruiken in de opdracht **Remove-PSSession** .</span><span class="sxs-lookup"><span data-stu-id="ef56c-171">Because the friendly name of a **PSSession** might not be unique, when you use the *Name* parameter, consider also using the *WhatIf* or *Confirm* parameter in the **Remove-PSSession** command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ef56c-172">-Sessie</span><span class="sxs-lookup"><span data-stu-id="ef56c-172">-Session</span></span>

<span data-ttu-id="ef56c-173">Hiermee geeft u de sessie objecten van de **PSSessions** moeten worden gesloten.</span><span class="sxs-lookup"><span data-stu-id="ef56c-173">Specifies the session objects of the **PSSessions** to close.</span></span>
<span data-ttu-id="ef56c-174">Voer een variabele in die de **PSSessions** bevat of een opdracht die de **PSSessions**, zoals een New-PSSession of **Get-PSSession** opdracht, maakt of ontvangt.</span><span class="sxs-lookup"><span data-stu-id="ef56c-174">Enter a variable that contains the **PSSessions** or a command that creates or gets the **PSSessions**, such as a New-PSSession or **Get-PSSession** command.</span></span>
<span data-ttu-id="ef56c-175">U kunt ook een of meer sessie objecten pipeen om **-PSSession te verwijderen**.</span><span class="sxs-lookup"><span data-stu-id="ef56c-175">You can also pipe one or more session objects to **Remove-PSSession**.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ef56c-176">-VMId</span><span class="sxs-lookup"><span data-stu-id="ef56c-176">-VMId</span></span>

<span data-ttu-id="ef56c-177">Hiermee geeft u een ID-matrix van virtuele machines op.</span><span class="sxs-lookup"><span data-stu-id="ef56c-177">Specifies an array of ID of virtual machines.</span></span>
<span data-ttu-id="ef56c-178">Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="ef56c-178">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="ef56c-179">Als u de virtuele machines wilt zien die voor u beschikbaar zijn, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="ef56c-179">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ef56c-180">-VMName</span><span class="sxs-lookup"><span data-stu-id="ef56c-180">-VMName</span></span>

<span data-ttu-id="ef56c-181">Hiermee geeft u een matrix met namen van virtuele machines op.</span><span class="sxs-lookup"><span data-stu-id="ef56c-181">Specifies an array of names of virtual machines.</span></span>
<span data-ttu-id="ef56c-182">Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="ef56c-182">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="ef56c-183">Als u de virtuele machines wilt zien die voor u beschikbaar zijn, gebruikt u de cmdlet **Get-VM** .</span><span class="sxs-lookup"><span data-stu-id="ef56c-183">To see the virtual machines that are available to you, use the **Get-VM** cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ef56c-184">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ef56c-184">-Confirm</span></span>

<span data-ttu-id="ef56c-185">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="ef56c-185">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ef56c-186">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ef56c-186">-WhatIf</span></span>

<span data-ttu-id="ef56c-187">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="ef56c-187">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ef56c-188">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ef56c-188">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ef56c-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ef56c-189">CommonParameters</span></span>

<span data-ttu-id="ef56c-190">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ef56c-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ef56c-191">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ef56c-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ef56c-192">INVOER</span><span class="sxs-lookup"><span data-stu-id="ef56c-192">INPUTS</span></span>

### <span data-ttu-id="ef56c-193">System. Management. Automation. Runspaces. PSSession</span><span class="sxs-lookup"><span data-stu-id="ef56c-193">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="ef56c-194">U kunt een sessie object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ef56c-194">You can pipe a session object to this cmdlet.</span></span>

## <span data-ttu-id="ef56c-195">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ef56c-195">OUTPUTS</span></span>

### <span data-ttu-id="ef56c-196">Geen</span><span class="sxs-lookup"><span data-stu-id="ef56c-196">None</span></span>

<span data-ttu-id="ef56c-197">Met deze cmdlet worden geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ef56c-197">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="ef56c-198">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ef56c-198">NOTES</span></span>

* <span data-ttu-id="ef56c-199">De *id-* para meter is verplicht.</span><span class="sxs-lookup"><span data-stu-id="ef56c-199">The *Id* parameter is mandatory.</span></span> <span data-ttu-id="ef56c-200">Als u wilt verwijderen van alle **PSSessions** in de huidige sessie, typt u `Get-PSSession | Remove-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="ef56c-200">To delete all the **PSSessions** in the current session, type `Get-PSSession | Remove-PSSession`.</span></span>
* <span data-ttu-id="ef56c-201">Een **PSSession** maakt gebruik van een permanente verbinding met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="ef56c-201">A **PSSession** uses a persistent connection to a remote computer.</span></span> <span data-ttu-id="ef56c-202">Een **PSSession** maken om een reeks opdrachten uit te voeren die gegevens delen.</span><span class="sxs-lookup"><span data-stu-id="ef56c-202">Create a **PSSession** to run a series of commands that share data.</span></span> <span data-ttu-id="ef56c-203">Typ `Get-Help about_PSSessions` voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ef56c-203">For more information, type `Get-Help about_PSSessions`.</span></span>
* <span data-ttu-id="ef56c-204">**PSSessions** zijn specifiek voor de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="ef56c-204">**PSSessions** are specific to the current session.</span></span> <span data-ttu-id="ef56c-205">Wanneer u een sessie beëindigt, wordt de **PSSessions** die u in die sessie hebt gemaakt, geforceerd gesloten.</span><span class="sxs-lookup"><span data-stu-id="ef56c-205">When you end a session, the **PSSessions** that you created in that session are forcibly closed.</span></span>

## <span data-ttu-id="ef56c-206">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ef56c-206">RELATED LINKS</span></span>

[<span data-ttu-id="ef56c-207">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="ef56c-207">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="ef56c-208">Verbinding verbreken-PSSession</span><span class="sxs-lookup"><span data-stu-id="ef56c-208">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="ef56c-209">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="ef56c-209">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="ef56c-210">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="ef56c-210">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="ef56c-211">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="ef56c-211">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="ef56c-212">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="ef56c-212">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="ef56c-213">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="ef56c-213">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="ef56c-214">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="ef56c-214">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="ef56c-215">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="ef56c-215">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="ef56c-216">about_Remote</span><span class="sxs-lookup"><span data-stu-id="ef56c-216">about_Remote</span></span>](About/about_Remote.md)

