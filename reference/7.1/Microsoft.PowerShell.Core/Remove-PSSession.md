---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSession
ms.openlocfilehash: 1b0fbfca365e9cf369decbf4eafc0a8b4e2741bc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251189"
---
# <span data-ttu-id="71117-103">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="71117-103">Remove-PSSession</span></span>

## <span data-ttu-id="71117-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="71117-104">SYNOPSIS</span></span>
<span data-ttu-id="71117-105">Hiermee sluit u een of meer Power shell-sessies (PSSessions).</span><span class="sxs-lookup"><span data-stu-id="71117-105">Closes one or more PowerShell sessions (PSSessions).</span></span>

## <span data-ttu-id="71117-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="71117-106">SYNTAX</span></span>

### <span data-ttu-id="71117-107">Id (standaard)</span><span class="sxs-lookup"><span data-stu-id="71117-107">Id (Default)</span></span>

```
Remove-PSSession [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="71117-108">Sessie</span><span class="sxs-lookup"><span data-stu-id="71117-108">Session</span></span>

```
Remove-PSSession [-Session] <PSSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="71117-109">ContainerId</span><span class="sxs-lookup"><span data-stu-id="71117-109">ContainerId</span></span>

```
Remove-PSSession -ContainerId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="71117-110">VMId</span><span class="sxs-lookup"><span data-stu-id="71117-110">VMId</span></span>

```
Remove-PSSession -VMId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="71117-111">VMName</span><span class="sxs-lookup"><span data-stu-id="71117-111">VMName</span></span>

```
Remove-PSSession -VMName <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="71117-112">InstanceId</span><span class="sxs-lookup"><span data-stu-id="71117-112">InstanceId</span></span>

```
Remove-PSSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="71117-113">Naam</span><span class="sxs-lookup"><span data-stu-id="71117-113">Name</span></span>

```
Remove-PSSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="71117-114">ComputerName</span><span class="sxs-lookup"><span data-stu-id="71117-114">ComputerName</span></span>

```
Remove-PSSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="71117-115">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="71117-115">DESCRIPTION</span></span>

<span data-ttu-id="71117-116">De cmdlet **Remove-PSSession** sluit Power shell-sessies ( **PSSessions** ) in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="71117-116">The **Remove-PSSession** cmdlet closes PowerShell sessions ( **PSSessions** ) in the current session.</span></span>
<span data-ttu-id="71117-117">Hiermee worden opdrachten gestopt die worden uitgevoerd in de **PSSessions** , wordt de **PSSession** beëindigd en worden de resources vrijgegeven die de **PSSession** gebruikt.</span><span class="sxs-lookup"><span data-stu-id="71117-117">It stops any commands that are running in the **PSSessions** , ends the **PSSession** , and releases the resources that the **PSSession** was using.</span></span>
<span data-ttu-id="71117-118">Als de **PSSession** is verbonden met een externe computer, sluit deze cmdlet ook de verbinding tussen de lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="71117-118">If the **PSSession** is connected to a remote computer, this cmdlet also closes the connection between the local and remote computers.</span></span>

<span data-ttu-id="71117-119">Als u een **PSSession** wilt verwijderen, voert u de *naam* , *ComputerName* , *id* of *InstanceId* van de sessie in.</span><span class="sxs-lookup"><span data-stu-id="71117-119">To remove a **PSSession** , enter the *Name* , *ComputerName* , *ID* , or *InstanceID* of the session.</span></span>

<span data-ttu-id="71117-120">Als u de *PSSession* hebt opgeslagen in een variabele, blijft het object Session in de variabele, maar wordt de status van de *PSSession* gesloten.</span><span class="sxs-lookup"><span data-stu-id="71117-120">If you have saved the *PSSession* in a variable, the session object remains in the variable, but the state of the *PSSession* is Closed.</span></span>

## <span data-ttu-id="71117-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="71117-121">EXAMPLES</span></span>

### <span data-ttu-id="71117-122">Voor beeld 1: sessies verwijderen met behulp van-Id's</span><span class="sxs-lookup"><span data-stu-id="71117-122">Example 1: Remove sessions by using IDs</span></span>

```powershell
Remove-PSSession -Id 1, 2
```

<span data-ttu-id="71117-123">Met deze opdracht verwijdert u de **PSSessions** met de id's 1 en 2.</span><span class="sxs-lookup"><span data-stu-id="71117-123">This command removes the **PSSessions** that have IDs 1 and 2.</span></span>

### <span data-ttu-id="71117-124">Voor beeld 2: alle sessies in de huidige sessie verwijderen</span><span class="sxs-lookup"><span data-stu-id="71117-124">Example 2: Remove all the sessions in the current session</span></span>

```powershell
Get-PSSession | Remove-PSSession
Remove-PSSession -Session (Get-PSSession)
$s = Get-PSSession
Remove-PSSession -Session $s
```

<span data-ttu-id="71117-125">Met deze opdrachten worden alle **PSSessions** in de huidige sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="71117-125">These commands remove all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="71117-126">Hoewel de drie opdracht indelingen er anders uitzien, hebben ze hetzelfde effect.</span><span class="sxs-lookup"><span data-stu-id="71117-126">Although the three command formats look different, they have the same effect.</span></span>

### <span data-ttu-id="71117-127">Voor beeld 3: sessies sluiten met behulp van namen</span><span class="sxs-lookup"><span data-stu-id="71117-127">Example 3: Close sessions by using names</span></span>

```powershell
$r = Get-PSSession -ComputerName Serv*
$r | Remove-PSSession
```

<span data-ttu-id="71117-128">Met deze opdrachten sluit u de **PSSessions** die zijn verbonden met computers die namen hebben die met Serviceart beginnen.</span><span class="sxs-lookup"><span data-stu-id="71117-128">These commands close the **PSSessions** that are connected to computers that have names that begin with Serv.</span></span>

### <span data-ttu-id="71117-129">Voor beeld 4: sessies sluiten die zijn verbonden met een poort</span><span class="sxs-lookup"><span data-stu-id="71117-129">Example 4: Close sessions connected to a port</span></span>

```powershell
Get-PSSession | where {$_.port -eq 90} | Remove-PSSession
```

<span data-ttu-id="71117-130">Met deze opdracht sluit u de **PSSessions** die zijn verbonden met poort 90.</span><span class="sxs-lookup"><span data-stu-id="71117-130">This command closes the **PSSessions** that are connected to port 90.</span></span>
<span data-ttu-id="71117-131">U kunt deze opdracht indeling gebruiken om **PSSessions** te identificeren op basis van andere eigenschappen dan *ComputerName* , *name* , *InstanceId* en *id*.</span><span class="sxs-lookup"><span data-stu-id="71117-131">You can use this command format to identify **PSSessions** by properties other than *ComputerName* , *Name* , *InstanceID* , and *ID*.</span></span>

### <span data-ttu-id="71117-132">Voor beeld 5: een sessie sluiten op basis van exemplaar-ID</span><span class="sxs-lookup"><span data-stu-id="71117-132">Example 5: Close a session based on instance ID</span></span>

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

<span data-ttu-id="71117-133">Deze opdrachten laten zien hoe u een **PSSession** kunt sluiten op basis van de instantie-id of **RemoteRunspaceID**.</span><span class="sxs-lookup"><span data-stu-id="71117-133">These commands show how to close a **PSSession** based on its instance ID, or **RemoteRunspaceID**.</span></span>

<span data-ttu-id="71117-134">De eerste opdracht maakt gebruik van de cmdlet **Get-PSSession** om de **PSSessions** in de huidige sessie op te halen.</span><span class="sxs-lookup"><span data-stu-id="71117-134">The first command uses the **Get-PSSession** cmdlet to get the **PSSessions** in the current session.</span></span>
<span data-ttu-id="71117-135">Er wordt gebruikgemaakt van een pijplijn operator (|) om de **PSSessions** te verzenden naar de cmdlet Format-Table, waarmee de eigenschappen **ComputerName** en **InstanceId** worden opgemaakt in een tabel.</span><span class="sxs-lookup"><span data-stu-id="71117-135">It uses a pipeline operator (|) to send the **PSSessions** to the Format-Table cmdlet, which formats their **ComputerName** and **InstanceID** properties in a table.</span></span>
<span data-ttu-id="71117-136">De *AutoSize* -para meter comprimeert de kolommen voor weer gave.</span><span class="sxs-lookup"><span data-stu-id="71117-136">The *AutoSize* parameter compresses the columns for display.</span></span>

<span data-ttu-id="71117-137">Vanuit de resulterende weer gave kunt u de **PSSession** die moeten worden gesloten identificeren en de *InstanceId* van die **PSSession** kopiëren en plakken in de tweede opdracht.</span><span class="sxs-lookup"><span data-stu-id="71117-137">From the resulting display, you can identify the **PSSession** to be closed, and copy and paste the *InstanceID* of that **PSSession** into the second command.</span></span>

<span data-ttu-id="71117-138">De tweede opdracht maakt gebruik van de cmdlet **Remove-PSSession** om de *PSSession* te verwijderen met de opgegeven exemplaar-id.</span><span class="sxs-lookup"><span data-stu-id="71117-138">The second command uses the **Remove-PSSession** cmdlet to remove the *PSSession* with the specified instance ID.</span></span>

### <span data-ttu-id="71117-139">Voor beeld 6: een functie maken waarmee alle sessies in de huidige sessie worden verwijderd</span><span class="sxs-lookup"><span data-stu-id="71117-139">Example 6: Create a function that deletes all sessions in the current session</span></span>

```powershell
Function EndPSS { Get-PSSession | Remove-PSSession }
```

<span data-ttu-id="71117-140">Deze functie verwijdert alle **PSSessions** in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="71117-140">This function deletes all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="71117-141">Nadat u deze functie aan uw Power shell-profiel hebt toegevoegd, kunt u alle sessies verwijderen `EndPSS` .</span><span class="sxs-lookup"><span data-stu-id="71117-141">After you add this function to your PowerShell profile, to delete all sessions, type `EndPSS`.</span></span>

## <span data-ttu-id="71117-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="71117-142">PARAMETERS</span></span>

### <span data-ttu-id="71117-143">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="71117-143">-ComputerName</span></span>

<span data-ttu-id="71117-144">Hiermee geeft u een matrix met namen van computers op.</span><span class="sxs-lookup"><span data-stu-id="71117-144">Specifies an array of names of computers.</span></span>
<span data-ttu-id="71117-145">Met deze cmdlet worden de **PSSessions** die zijn verbonden met de opgegeven computers gesloten.</span><span class="sxs-lookup"><span data-stu-id="71117-145">This cmdlet closes the **PSSessions** that are connected to the specified computers.</span></span>
<span data-ttu-id="71117-146">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="71117-146">Wildcard characters are permitted.</span></span>

<span data-ttu-id="71117-147">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een of meer externe computers.</span><span class="sxs-lookup"><span data-stu-id="71117-147">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span>
<span data-ttu-id="71117-148">Typ de computer naam, localhost of een punt (.) om de lokale computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="71117-148">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span>

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

### <span data-ttu-id="71117-149">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="71117-149">-ContainerId</span></span>

<span data-ttu-id="71117-150">Hiermee geeft u een matrix met Id's van containers op.</span><span class="sxs-lookup"><span data-stu-id="71117-150">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="71117-151">Met deze cmdlet worden sessies voor elk van de opgegeven containers verwijderd.</span><span class="sxs-lookup"><span data-stu-id="71117-151">This cmdlet removes sessions for each of the specified containers.</span></span> <span data-ttu-id="71117-152">Gebruik de `docker ps` opdracht om een lijst met container-id's op te halen.</span><span class="sxs-lookup"><span data-stu-id="71117-152">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="71117-153">Zie de Help voor de opdracht [docker PS](https://docs.docker.com/engine/reference/commandline/ps/) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="71117-153">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

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

### <span data-ttu-id="71117-154">-Id</span><span class="sxs-lookup"><span data-stu-id="71117-154">-Id</span></span>

<span data-ttu-id="71117-155">Hiermee geeft u een matrix met Id's van sessies.</span><span class="sxs-lookup"><span data-stu-id="71117-155">Specifies an array of IDs of sessions.</span></span>
<span data-ttu-id="71117-156">Met deze cmdlet wordt de *PSSessions* met de opgegeven id's gesloten.</span><span class="sxs-lookup"><span data-stu-id="71117-156">This cmdlet closes the *PSSessions* with the specified IDs.</span></span>
<span data-ttu-id="71117-157">Typ een of meer Id's, gescheiden door komma's, of gebruik de operator Range (..) om een bereik van Id's op te geven.</span><span class="sxs-lookup"><span data-stu-id="71117-157">Type one or more IDs, separated by commas, or use the range operator (..) to specify a range of IDs.</span></span>

<span data-ttu-id="71117-158">Een ID is een geheel getal dat de **PSSession** in de huidige sessie uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="71117-158">An ID is an integer that uniquely identifies the **PSSession** in the current session.</span></span>
<span data-ttu-id="71117-159">Het is gemakkelijker te onthouden en te typen dan de *InstanceId* , maar is alleen uniek in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="71117-159">It is easier to remember and type than the *InstanceId* , but it is unique only in the current session.</span></span>
<span data-ttu-id="71117-160">Als u de ID van een **PSSession** wilt zoeken, voert u de cmdlet Get-PSSession zonder para meters uit.</span><span class="sxs-lookup"><span data-stu-id="71117-160">To find the ID of a **PSSession** , run the Get-PSSession cmdlet without parameters.</span></span>

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

### <span data-ttu-id="71117-161">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="71117-161">-InstanceId</span></span>

<span data-ttu-id="71117-162">Hiermee geeft u een matrix met exemplaar-Id's op.</span><span class="sxs-lookup"><span data-stu-id="71117-162">Specifies an array of instance IDs.</span></span>
<span data-ttu-id="71117-163">Met deze cmdlet wordt de **PSSessions** gesloten met de opgegeven exemplaar-id's.</span><span class="sxs-lookup"><span data-stu-id="71117-163">This cmdlet closes the **PSSessions** that have the specified instance IDs.</span></span>

<span data-ttu-id="71117-164">De exemplaar-ID is een GUID waarmee een **PSSession** in de huidige sessie uniek wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="71117-164">The instance ID is a GUID that uniquely identifies a **PSSession** in the current session.</span></span>
<span data-ttu-id="71117-165">De exemplaar-ID is uniek, zelfs wanneer er meerdere sessies worden uitgevoerd op één computer.</span><span class="sxs-lookup"><span data-stu-id="71117-165">The instance ID is unique, even when you have multiple sessions running on a single computer.</span></span>

<span data-ttu-id="71117-166">De exemplaar-ID wordt opgeslagen in de eigenschap **InstanceId** van het object dat een **PSSession** vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="71117-166">The instance ID is stored in the **InstanceID** property of the object that represents a **PSSession**.</span></span>
<span data-ttu-id="71117-167">Als u wilt zoeken naar de **InstanceId** van de **PSSessions** in de huidige sessie, typt u `Get-PSSession | Format-Table Name, ComputerName, InstanceId` .</span><span class="sxs-lookup"><span data-stu-id="71117-167">To find the **InstanceID** of the **PSSessions** in the current session, type `Get-PSSession | Format-Table Name, ComputerName, InstanceId`.</span></span>

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

### <span data-ttu-id="71117-168">-Name</span><span class="sxs-lookup"><span data-stu-id="71117-168">-Name</span></span>

<span data-ttu-id="71117-169">Hiermee geeft u een matrix met beschrijvende namen van sessies.</span><span class="sxs-lookup"><span data-stu-id="71117-169">Specifies an array of friendly names of sessions.</span></span>
<span data-ttu-id="71117-170">Met deze cmdlet worden de **PSSessions** met de opgegeven beschrijvende namen gesloten.</span><span class="sxs-lookup"><span data-stu-id="71117-170">This cmdlet closes the **PSSessions** that have the specified friendly names.</span></span>
<span data-ttu-id="71117-171">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="71117-171">Wildcard characters are permitted.</span></span>

<span data-ttu-id="71117-172">Omdat de beschrijvende naam van een **PSSession** mogelijk niet uniek is, moet u, wanneer u de para meter *name* gebruikt, ook de *WhatIf* of de para meter *confirm* gebruiken in de opdracht **Remove-PSSession** .</span><span class="sxs-lookup"><span data-stu-id="71117-172">Because the friendly name of a **PSSession** might not be unique, when you use the *Name* parameter, consider also using the *WhatIf* or *Confirm* parameter in the **Remove-PSSession** command.</span></span>

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

### <span data-ttu-id="71117-173">-Sessie</span><span class="sxs-lookup"><span data-stu-id="71117-173">-Session</span></span>

<span data-ttu-id="71117-174">Hiermee geeft u de sessie objecten van de **PSSessions** moeten worden gesloten.</span><span class="sxs-lookup"><span data-stu-id="71117-174">Specifies the session objects of the **PSSessions** to close.</span></span>
<span data-ttu-id="71117-175">Voer een variabele in die de **PSSessions** bevat of een opdracht die de **PSSessions** , zoals een New-PSSession of **Get-PSSession** opdracht, maakt of ontvangt.</span><span class="sxs-lookup"><span data-stu-id="71117-175">Enter a variable that contains the **PSSessions** or a command that creates or gets the **PSSessions** , such as a New-PSSession or **Get-PSSession** command.</span></span>
<span data-ttu-id="71117-176">U kunt ook een of meer sessie objecten pipeen om **-PSSession te verwijderen**.</span><span class="sxs-lookup"><span data-stu-id="71117-176">You can also pipe one or more session objects to **Remove-PSSession**.</span></span>

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

### <span data-ttu-id="71117-177">-VMId</span><span class="sxs-lookup"><span data-stu-id="71117-177">-VMId</span></span>

<span data-ttu-id="71117-178">Hiermee geeft u een ID-matrix van virtuele machines op.</span><span class="sxs-lookup"><span data-stu-id="71117-178">Specifies an array of ID of virtual machines.</span></span>
<span data-ttu-id="71117-179">Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="71117-179">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="71117-180">Als u de virtuele machines wilt zien die voor u beschikbaar zijn, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="71117-180">To see the virtual machines that are available to you, use the following command:</span></span>

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

### <span data-ttu-id="71117-181">-VMName</span><span class="sxs-lookup"><span data-stu-id="71117-181">-VMName</span></span>

<span data-ttu-id="71117-182">Hiermee geeft u een matrix met namen van virtuele machines op.</span><span class="sxs-lookup"><span data-stu-id="71117-182">Specifies an array of names of virtual machines.</span></span>
<span data-ttu-id="71117-183">Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="71117-183">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="71117-184">Als u de virtuele machines wilt zien die voor u beschikbaar zijn, gebruikt u de cmdlet **Get-VM** .</span><span class="sxs-lookup"><span data-stu-id="71117-184">To see the virtual machines that are available to you, use the **Get-VM** cmdlet.</span></span>

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

### <span data-ttu-id="71117-185">-Confirm</span><span class="sxs-lookup"><span data-stu-id="71117-185">-Confirm</span></span>

<span data-ttu-id="71117-186">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="71117-186">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="71117-187">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="71117-187">-WhatIf</span></span>

<span data-ttu-id="71117-188">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="71117-188">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="71117-189">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="71117-189">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="71117-190">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="71117-190">CommonParameters</span></span>

<span data-ttu-id="71117-191">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="71117-191">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="71117-192">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="71117-192">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="71117-193">INVOER</span><span class="sxs-lookup"><span data-stu-id="71117-193">INPUTS</span></span>

### <span data-ttu-id="71117-194">System. Management. Automation. Runspaces. PSSession</span><span class="sxs-lookup"><span data-stu-id="71117-194">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="71117-195">U kunt een sessie object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="71117-195">You can pipe a session object to this cmdlet.</span></span>

## <span data-ttu-id="71117-196">UITVOER</span><span class="sxs-lookup"><span data-stu-id="71117-196">OUTPUTS</span></span>

### <span data-ttu-id="71117-197">Geen</span><span class="sxs-lookup"><span data-stu-id="71117-197">None</span></span>

<span data-ttu-id="71117-198">Met deze cmdlet worden geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="71117-198">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="71117-199">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="71117-199">NOTES</span></span>

* <span data-ttu-id="71117-200">De *id-* para meter is verplicht.</span><span class="sxs-lookup"><span data-stu-id="71117-200">The *Id* parameter is mandatory.</span></span> <span data-ttu-id="71117-201">Als u wilt verwijderen van alle **PSSessions** in de huidige sessie, typt u `Get-PSSession | Remove-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="71117-201">To delete all the **PSSessions** in the current session, type `Get-PSSession | Remove-PSSession`.</span></span>
* <span data-ttu-id="71117-202">Een **PSSession** maakt gebruik van een permanente verbinding met een externe computer.</span><span class="sxs-lookup"><span data-stu-id="71117-202">A **PSSession** uses a persistent connection to a remote computer.</span></span> <span data-ttu-id="71117-203">Een **PSSession** maken om een reeks opdrachten uit te voeren die gegevens delen.</span><span class="sxs-lookup"><span data-stu-id="71117-203">Create a **PSSession** to run a series of commands that share data.</span></span> <span data-ttu-id="71117-204">Typ `Get-Help about_PSSessions` voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="71117-204">For more information, type `Get-Help about_PSSessions`.</span></span>
* <span data-ttu-id="71117-205">**PSSessions** zijn specifiek voor de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="71117-205">**PSSessions** are specific to the current session.</span></span> <span data-ttu-id="71117-206">Wanneer u een sessie beëindigt, wordt de **PSSessions** die u in die sessie hebt gemaakt, geforceerd gesloten.</span><span class="sxs-lookup"><span data-stu-id="71117-206">When you end a session, the **PSSessions** that you created in that session are forcibly closed.</span></span>

## <span data-ttu-id="71117-207">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="71117-207">RELATED LINKS</span></span>

[<span data-ttu-id="71117-208">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="71117-208">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="71117-209">Verbinding verbreken-PSSession</span><span class="sxs-lookup"><span data-stu-id="71117-209">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="71117-210">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="71117-210">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="71117-211">Afsluiten-PSSession</span><span class="sxs-lookup"><span data-stu-id="71117-211">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="71117-212">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="71117-212">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="71117-213">Invoke-opdracht</span><span class="sxs-lookup"><span data-stu-id="71117-213">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="71117-214">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="71117-214">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="71117-215">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="71117-215">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="71117-216">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="71117-216">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="71117-217">about_Remote</span><span class="sxs-lookup"><span data-stu-id="71117-217">about_Remote</span></span>](About/about_Remote.md)

