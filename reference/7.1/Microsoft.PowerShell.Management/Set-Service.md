---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: cf9c44fecde650ab0b4747aea5910da49638f297
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344317"
---
# <span data-ttu-id="7454c-103">Set-Service</span><span class="sxs-lookup"><span data-stu-id="7454c-103">Set-Service</span></span>

## <span data-ttu-id="7454c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7454c-104">SYNOPSIS</span></span>
<span data-ttu-id="7454c-105">Hiermee wordt een service gestart, gestopt en onderbroken, en worden de eigenschappen ervan gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="7454c-105">Starts, stops, and suspends a service, and changes its properties.</span></span>

## <span data-ttu-id="7454c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7454c-106">SYNTAX</span></span>

### <span data-ttu-id="7454c-107">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="7454c-107">Name (Default)</span></span>

```
Set-Service [-Name] <String> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-Status <String>]
 [-SecurityDescriptorSddl <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7454c-108">Input object</span><span class="sxs-lookup"><span data-stu-id="7454c-108">InputObject</span></span>

```
Set-Service [-InputObject] <ServiceController> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-SecurityDescriptorSddl <String>]
 [-Status <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7454c-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7454c-109">DESCRIPTION</span></span>

<span data-ttu-id="7454c-110">`Set-Service`Met de cmdlet worden de eigenschappen van een service gewijzigd, zoals de **status** , **Beschrijving** , **DisplayName** en **opstart type**.</span><span class="sxs-lookup"><span data-stu-id="7454c-110">The `Set-Service` cmdlet changes the properties of a service such as the **Status** , **Description** , **DisplayName** , and **StartupType**.</span></span> <span data-ttu-id="7454c-111">`Set-Service` kan een service starten, stoppen, onderbreken of onderbreken.</span><span class="sxs-lookup"><span data-stu-id="7454c-111">`Set-Service` can start, stop, suspend, or pause a service.</span></span> <span data-ttu-id="7454c-112">Als u een service wilt identificeren, voert u de service naam in of verzendt u een service object.</span><span class="sxs-lookup"><span data-stu-id="7454c-112">To identify a service, enter its service name or submit a service object.</span></span> <span data-ttu-id="7454c-113">Of verzend een service naam of Service object omlaag in de pijp lijn `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="7454c-113">Or, send a service name or service object down the pipeline to `Set-Service`.</span></span>

## <span data-ttu-id="7454c-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7454c-114">EXAMPLES</span></span>

### <span data-ttu-id="7454c-115">Voor beeld 1: een weergave naam wijzigen</span><span class="sxs-lookup"><span data-stu-id="7454c-115">Example 1: Change a display name</span></span>

<span data-ttu-id="7454c-116">In dit voor beeld wordt de weergave naam van een service gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="7454c-116">In this example, a service's display name is changed.</span></span> <span data-ttu-id="7454c-117">Als u de oorspronkelijke weergave naam wilt weer geven, gebruikt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="7454c-117">To view the original display name, use `Get-Service`.</span></span>

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

<span data-ttu-id="7454c-118">`Set-Service` maakt gebruik van de para meter **name** om de naam van de service op te geven, **lanmanworkstation**.</span><span class="sxs-lookup"><span data-stu-id="7454c-118">`Set-Service` uses the **Name** parameter to specify the service's name, **LanmanWorkstation**.</span></span> <span data-ttu-id="7454c-119">Met de para meter **DisplayName** geeft u de nieuwe weergave naam op: **LANMAN-werk station**.</span><span class="sxs-lookup"><span data-stu-id="7454c-119">The **DisplayName** parameter specifies the new display name, **LanMan Workstation**.</span></span>

### <span data-ttu-id="7454c-120">Voor beeld 2: het opstart type van Services wijzigen</span><span class="sxs-lookup"><span data-stu-id="7454c-120">Example 2: Change the startup type of services</span></span>

<span data-ttu-id="7454c-121">In dit voor beeld ziet u hoe u het opstart type van een service wijzigt.</span><span class="sxs-lookup"><span data-stu-id="7454c-121">This example shows how to change a service's startup type.</span></span>

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

<span data-ttu-id="7454c-122">`Set-Service`maakt gebruik van de para meter **name** om de naam van de service **op te geven.**</span><span class="sxs-lookup"><span data-stu-id="7454c-122">`Set-Service` uses the **Name** parameter to specify the service's name, **BITS**.</span></span> <span data-ttu-id="7454c-123">Met de para meter **opstart type** wordt de service ingesteld op **automatisch**.</span><span class="sxs-lookup"><span data-stu-id="7454c-123">The **StartupType** parameter sets the service to **Automatic**.</span></span>

<span data-ttu-id="7454c-124">`Get-Service` maakt gebruik van de para meter **name** om de **bits** -service op te geven en verzendt het object omlaag in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="7454c-124">`Get-Service` uses the **Name** parameter to specify the **BITS** service and sends the object down the pipeline.</span></span> <span data-ttu-id="7454c-125">`Select-Object` gebruikt de para meter **Property** om de status van de **bits** -service weer te geven.</span><span class="sxs-lookup"><span data-stu-id="7454c-125">`Select-Object` uses the **Property** parameter to display the **BITS** service's status.</span></span>

### <span data-ttu-id="7454c-126">Voor beeld 3: de beschrijving van een service wijzigen</span><span class="sxs-lookup"><span data-stu-id="7454c-126">Example 3: Change the description of a service</span></span>

<span data-ttu-id="7454c-127">In dit voor beeld wordt de beschrijving van de BITS-service gewijzigd en wordt het resultaat weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7454c-127">This example changes the BITS service's description and displays the result.</span></span>

<span data-ttu-id="7454c-128">De `Get-CimInstance` cmdlet wordt gebruikt omdat deze een **Win32_Service** -object retourneert dat de **Beschrijving** van de service bevat.</span><span class="sxs-lookup"><span data-stu-id="7454c-128">The `Get-CimInstance` cmdlet is used because it returns a **Win32_Service** object that includes the service's **Description**.</span></span>

```powershell
Get-CimInstance Win32_Service -Filter 'Name = "BITS"'  | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth. If the service is
              disabled, then any applications that depend on BITS, such as Windows Update or MSN
              Explorer, will be unable to automatically download programs and other information.
```

```powershell
Set-Service -Name BITS -Description "Transfers files in the background using idle network bandwidth."
Get-CimInstance Win32_Service -Filter 'Name = "BITS"' | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth.
```

<span data-ttu-id="7454c-129">`Get-CimInstance` Hiermee wordt het object naar beneden verzonden naar de pijp lijn `Format-List` en worden de naam en beschrijving van de service weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7454c-129">`Get-CimInstance` sends the object down the pipeline to `Format-List` and displays the service's name and description.</span></span> <span data-ttu-id="7454c-130">Voor vergelijkings doeleinden wordt de opdracht uitgevoerd vóór en na het bijwerken van de beschrijving.</span><span class="sxs-lookup"><span data-stu-id="7454c-130">For comparison purposes, the command is run before and after the description is updated.</span></span>

<span data-ttu-id="7454c-131">`Set-Service` maakt gebruik van de para meter **name** om de **bits** -service op te geven.</span><span class="sxs-lookup"><span data-stu-id="7454c-131">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="7454c-132">De **beschrijvings** parameter bevat de bijgewerkte tekst voor de beschrijving van de service.</span><span class="sxs-lookup"><span data-stu-id="7454c-132">The **Description** parameter specifies the updated text for the services' description.</span></span>

### <span data-ttu-id="7454c-133">Voor beeld 4: een service starten</span><span class="sxs-lookup"><span data-stu-id="7454c-133">Example 4: Start a service</span></span>

<span data-ttu-id="7454c-134">In dit voor beeld wordt een service gestart.</span><span class="sxs-lookup"><span data-stu-id="7454c-134">In this example, a service is started.</span></span>

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

<span data-ttu-id="7454c-135">`Set-Service` maakt gebruik van de para meter **name** om de service, **WinRM** op te geven.</span><span class="sxs-lookup"><span data-stu-id="7454c-135">`Set-Service` uses the **Name** parameter to specify the service, **WinRM**.</span></span> <span data-ttu-id="7454c-136">De para meter **status** gebruikt de waarde **die wordt gebruikt** om de service te starten.</span><span class="sxs-lookup"><span data-stu-id="7454c-136">The **Status** parameter uses the value **Running** to start the service.</span></span> <span data-ttu-id="7454c-137">De para meter **PassThru** voert een **ServiceController** -object uit dat de resultaten weergeeft.</span><span class="sxs-lookup"><span data-stu-id="7454c-137">The **PassThru** parameter outputs a **ServiceController** object that displays the results.</span></span>

### <span data-ttu-id="7454c-138">Voor beeld 5: een service opschorten</span><span class="sxs-lookup"><span data-stu-id="7454c-138">Example 5: Suspend a service</span></span>

<span data-ttu-id="7454c-139">In dit voor beeld wordt de pijp lijn gebruikt om de service te onderbreken.</span><span class="sxs-lookup"><span data-stu-id="7454c-139">This example uses the pipeline to pause to service.</span></span>

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

<span data-ttu-id="7454c-140">`Get-Service` maakt gebruik van de para meter **name** om de **Schedule** -service op te geven en verzendt het object omlaag in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="7454c-140">`Get-Service` uses the **Name** parameter to specify the **Schedule** service, and sends the object down the pipeline.</span></span> <span data-ttu-id="7454c-141">`Set-Service` maakt gebruik van de para meter **status** om de service in te stellen op **onderbroken**.</span><span class="sxs-lookup"><span data-stu-id="7454c-141">`Set-Service` uses the **Status** parameter to set the service to **Paused**.</span></span>

### <span data-ttu-id="7454c-142">Voor beeld 6: een service stoppen</span><span class="sxs-lookup"><span data-stu-id="7454c-142">Example 6: Stop a service</span></span>

<span data-ttu-id="7454c-143">In dit voor beeld wordt een variabele gebruikt om een service te stoppen.</span><span class="sxs-lookup"><span data-stu-id="7454c-143">This example uses a variable to stop a service.</span></span>

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

<span data-ttu-id="7454c-144">`Get-Service` maakt gebruik van de para meter **name** om de service, de **planning** op te geven.</span><span class="sxs-lookup"><span data-stu-id="7454c-144">`Get-Service` uses the **Name** parameter to specify the service, **Schedule**.</span></span> <span data-ttu-id="7454c-145">Het object wordt opgeslagen in de variabele `$S` .</span><span class="sxs-lookup"><span data-stu-id="7454c-145">The object is stored in the variable, `$S`.</span></span> <span data-ttu-id="7454c-146">`Set-Service` maakt gebruik van de para meter **input object** en geeft het object op dat is opgeslagen `$S` .</span><span class="sxs-lookup"><span data-stu-id="7454c-146">`Set-Service` uses the **InputObject** parameter and specifies the object stored `$S`.</span></span> <span data-ttu-id="7454c-147">Met de para meter **status** wordt de service ingesteld op **gestopt**.</span><span class="sxs-lookup"><span data-stu-id="7454c-147">The **Status** parameter sets the service to **Stopped**.</span></span>

### <span data-ttu-id="7454c-148">Voor beeld 7: een service op een extern systeem stoppen</span><span class="sxs-lookup"><span data-stu-id="7454c-148">Example 7: Stop a service on a remote system</span></span>

<span data-ttu-id="7454c-149">In dit voor beeld wordt een service op een externe computer gestopt.</span><span class="sxs-lookup"><span data-stu-id="7454c-149">This example stops a service on a remote computer.</span></span>
<span data-ttu-id="7454c-150">Zie [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7454c-150">For more information, see [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```powershell
$Cred = Get-Credential
$S = Get-Service -Name Schedule
Invoke-Command -ComputerName server01.contoso.com -Credential $Cred -ScriptBlock {
  Set-Service -InputObject $S -Status Stopped
}
```

<span data-ttu-id="7454c-151">`Get-Credential` vraagt naar een gebruikers naam en wacht woord en slaat de referenties op in de `$Cred` variabele.</span><span class="sxs-lookup"><span data-stu-id="7454c-151">`Get-Credential` prompts for a username and password, and stores the credentials in the `$Cred` variable.</span></span> <span data-ttu-id="7454c-152">`Get-Service` maakt gebruik van de para meter **name** om de **Schedule** -service op te geven.</span><span class="sxs-lookup"><span data-stu-id="7454c-152">`Get-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="7454c-153">Het object wordt opgeslagen in de variabele `$S` .</span><span class="sxs-lookup"><span data-stu-id="7454c-153">The object is stored in the variable, `$S`.</span></span>

<span data-ttu-id="7454c-154">`Invoke-Command` maakt gebruik van de para meter **ComputerName** om een externe computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="7454c-154">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer.</span></span> <span data-ttu-id="7454c-155">De para meter **Credential** gebruikt de `$Cred` variabele om u aan te melden bij de computer.</span><span class="sxs-lookup"><span data-stu-id="7454c-155">The **Credential** parameter uses the `$Cred` variable to sign on to the computer.</span></span> <span data-ttu-id="7454c-156">De **script Block** -aanroepen `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="7454c-156">The **ScriptBlock** calls `Set-Service`.</span></span> <span data-ttu-id="7454c-157">De **input object** para meter geeft u het Service object op dat is opgeslagen `$S` .</span><span class="sxs-lookup"><span data-stu-id="7454c-157">The **InputObject** parameter specifies the service object stored `$S`.</span></span> <span data-ttu-id="7454c-158">Met de para meter **status** wordt de service ingesteld op **gestopt**.</span><span class="sxs-lookup"><span data-stu-id="7454c-158">The **Status** parameter sets the service to **Stopped**.</span></span>

### <span data-ttu-id="7454c-159">Voor beeld 8: de referentie van een service wijzigen</span><span class="sxs-lookup"><span data-stu-id="7454c-159">Example 8: Change credential of a service</span></span>

<span data-ttu-id="7454c-160">In dit voor beeld worden de referenties gewijzigd die worden gebruikt voor het beheren van een service.</span><span class="sxs-lookup"><span data-stu-id="7454c-160">This example changes the credentials that are used to manage a service.</span></span>

```powershell
$credential = Get-Credential
Set-Service -Name Schedule -Credential $credential
```

<span data-ttu-id="7454c-161">`Get-Credential` vraagt naar een gebruikers naam en wacht woord en slaat de referenties op in de `$credential` variabele.</span><span class="sxs-lookup"><span data-stu-id="7454c-161">`Get-Credential` prompts for a username and password, and stores the credentials in the `$credential` variable.</span></span> <span data-ttu-id="7454c-162">`Set-Service` maakt gebruik van de para meter **name** om de **Schedule** -service op te geven.</span><span class="sxs-lookup"><span data-stu-id="7454c-162">`Set-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="7454c-163">De para meter **Credential** maakt gebruik van de `$credential` variabele en werkt de **Schedule** -service bij.</span><span class="sxs-lookup"><span data-stu-id="7454c-163">The **Credential** parameter uses the `$credential` variable and updates the **Schedule** service.</span></span>

### <span data-ttu-id="7454c-164">Voor beeld 9: de security descriptor van een service wijzigen</span><span class="sxs-lookup"><span data-stu-id="7454c-164">Example 9: Change the SecurityDescriptor of a service</span></span>

<span data-ttu-id="7454c-165">In dit voor beeld wordt de **security descriptor** van een service gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="7454c-165">This example changes a service's **SecurityDescriptor**.</span></span>

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
Set-Service -Name "BITS" -SecurityDescriptorSddl $SDDL
```

<span data-ttu-id="7454c-166">De **security descriptor** wordt opgeslagen in de `$SDDL` variabele.</span><span class="sxs-lookup"><span data-stu-id="7454c-166">The **SecurityDescriptor** is stored in the `$SDDL` variable.</span></span> <span data-ttu-id="7454c-167">`Set-Service` maakt gebruik van de para meter **name** om de **bits** -service op te geven.</span><span class="sxs-lookup"><span data-stu-id="7454c-167">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="7454c-168">De para meter **SecurityDescriptorSddl** maakt gebruik `$SDDL` van om de **security descriptor** voor de **bits** -service te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="7454c-168">The **SecurityDescriptorSddl** parameter uses `$SDDL` to change the **SecurityDescriptor** for the **BITS** service.</span></span>

## <span data-ttu-id="7454c-169">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7454c-169">PARAMETERS</span></span>

### <span data-ttu-id="7454c-170">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7454c-170">-Confirm</span></span>

<span data-ttu-id="7454c-171">Vraagt u om bevestiging voordat deze wordt uitgevoerd `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="7454c-171">Prompts you for confirmation before running `Set-Service`.</span></span>

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

### <span data-ttu-id="7454c-172">-Credential</span><span class="sxs-lookup"><span data-stu-id="7454c-172">-Credential</span></span>

<span data-ttu-id="7454c-173">Hiermee geeft u het account op dat door de service wordt gebruikt als [account voor aanmelding](/windows/desktop/ad/about-service-logon-accounts)bij de service.</span><span class="sxs-lookup"><span data-stu-id="7454c-173">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="7454c-174">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7454c-174">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="7454c-175">Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="7454c-175">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="7454c-176">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="7454c-176">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="7454c-177">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="7454c-177">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

<span data-ttu-id="7454c-178">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="7454c-178">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="7454c-179">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7454c-179">-Description</span></span>

<span data-ttu-id="7454c-180">Hiermee geeft u een nieuwe beschrijving op voor de service.</span><span class="sxs-lookup"><span data-stu-id="7454c-180">Specifies a new description for the service.</span></span>

<span data-ttu-id="7454c-181">De beschrijving van de service wordt weer gegeven in **computer beheer, services**.</span><span class="sxs-lookup"><span data-stu-id="7454c-181">The service description appears in **Computer Management, Services**.</span></span> <span data-ttu-id="7454c-182">De **Beschrijving** is geen eigenschap van het `Get-Service` **ServiceController** -object.</span><span class="sxs-lookup"><span data-stu-id="7454c-182">The **Description** isn't a property of the `Get-Service` **ServiceController** object.</span></span> <span data-ttu-id="7454c-183">Als u de beschrijving van de service wilt zien, gebruikt u `Get-CimInstance` die een **Win32_Service** -object retourneert dat de service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="7454c-183">To see the service description, use `Get-CimInstance` that returns a **Win32_Service** object that represents the service.</span></span>

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

### <span data-ttu-id="7454c-184">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="7454c-184">-DisplayName</span></span>

<span data-ttu-id="7454c-185">Hiermee geeft u een nieuwe weergave naam voor de service op.</span><span class="sxs-lookup"><span data-stu-id="7454c-185">Specifies a new display name for the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: DN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7454c-186">-Force</span><span class="sxs-lookup"><span data-stu-id="7454c-186">-Force</span></span>

<span data-ttu-id="7454c-187">Hiermee geeft u de stop modus van de service op.</span><span class="sxs-lookup"><span data-stu-id="7454c-187">Specifies the Stop mode of the service.</span></span> <span data-ttu-id="7454c-188">Deze para meter werkt alleen wanneer `-Status Stopped` wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7454c-188">This parameter only works when `-Status Stopped` is used.</span></span> <span data-ttu-id="7454c-189">Bij inschakeling worden `Set-Service` de afhankelijke services gestopt voordat de doel service wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="7454c-189">If enabled, `Set-Service` stops the dependent services before the target service is stopped.</span></span> <span data-ttu-id="7454c-190">Standaard worden uitzonde ringen gegenereerd wanneer andere actieve services afhankelijk zijn van de doel service.</span><span class="sxs-lookup"><span data-stu-id="7454c-190">By default, exceptions are raised when other running services depend on the target service.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7454c-191">-Input object</span><span class="sxs-lookup"><span data-stu-id="7454c-191">-InputObject</span></span>

<span data-ttu-id="7454c-192">Hiermee geeft u een **ServiceController** -object op dat de service vertegenwoordigt die moet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="7454c-192">Specifies a **ServiceController** object that represents the service to change.</span></span> <span data-ttu-id="7454c-193">Voer een variabele in die het object bevat of typ een opdracht of expressie waarmee het object wordt opgehaald, zoals een `Get-Service` opdracht.</span><span class="sxs-lookup"><span data-stu-id="7454c-193">Enter a variable that contains the object, or type a command or expression that gets the object, such as a `Get-Service` command.</span></span> <span data-ttu-id="7454c-194">U kunt de pijp lijn gebruiken om een service object naar te verzenden `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="7454c-194">You can use the pipeline to send a service object to `Set-Service`.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7454c-195">-Name</span><span class="sxs-lookup"><span data-stu-id="7454c-195">-Name</span></span>

<span data-ttu-id="7454c-196">Hiermee geeft u de service naam op van de service die moet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="7454c-196">Specifies the service name of the service to be changed.</span></span> <span data-ttu-id="7454c-197">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7454c-197">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="7454c-198">U kunt de pijp lijn gebruiken om een service naam naar te verzenden `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="7454c-198">You can use the pipeline to send a service name to `Set-Service`.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7454c-199">-PassThru</span><span class="sxs-lookup"><span data-stu-id="7454c-199">-PassThru</span></span>

<span data-ttu-id="7454c-200">Retourneert een **ServiceController** -object dat staat voor de services die zijn gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="7454c-200">Returns a **ServiceController** object that represents the services that were changed.</span></span> <span data-ttu-id="7454c-201">Standaard genereert geen `Set-Service` uitvoer.</span><span class="sxs-lookup"><span data-stu-id="7454c-201">By default, `Set-Service` doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7454c-202">-Opstart type</span><span class="sxs-lookup"><span data-stu-id="7454c-202">-StartupType</span></span>

<span data-ttu-id="7454c-203">Hiermee geeft u de start modus van de service op.</span><span class="sxs-lookup"><span data-stu-id="7454c-203">Specifies the start mode of the service.</span></span>

<span data-ttu-id="7454c-204">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="7454c-204">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="7454c-205">**Automatisch** : de service wordt gestart of is door het besturings systeem gestart tijdens het opstarten van het systeem.</span><span class="sxs-lookup"><span data-stu-id="7454c-205">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="7454c-206">Als een service die automatisch wordt gestart, afhankelijk is van een hand matig gestarte service, wordt de hand matig gestarte service ook automatisch gestart bij het opstarten van het systeem.</span><span class="sxs-lookup"><span data-stu-id="7454c-206">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="7454c-207">**AutomaticDelayedStart** -binnenkort gestart nadat het systeem is opgestart.</span><span class="sxs-lookup"><span data-stu-id="7454c-207">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="7454c-208">**Uitgeschakeld** : de service is uitgeschakeld en kan niet worden gestart door een gebruiker of toepassing.</span><span class="sxs-lookup"><span data-stu-id="7454c-208">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="7454c-209">**InvalidValue** -heeft geen effect.</span><span class="sxs-lookup"><span data-stu-id="7454c-209">**InvalidValue** - Has no effect.</span></span> <span data-ttu-id="7454c-210">De cmdlet retourneert geen fout, maar de opstart type van de service is niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="7454c-210">The cmdlet does not return an error but the StartupType of the service is not changed.</span></span>
- <span data-ttu-id="7454c-211">**Hand matig** : de service wordt alleen hand matig gestart door een gebruiker, met behulp van service besturings beheer of door een toepassing.</span><span class="sxs-lookup"><span data-stu-id="7454c-211">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases: StartMode, SM, ST, StartType
Accepted values: Automatic, AutomaticDelayedStart, Disabled, InvalidValue, Manual

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7454c-212">-Status</span><span class="sxs-lookup"><span data-stu-id="7454c-212">-Status</span></span>

<span data-ttu-id="7454c-213">Hiermee geeft u de status van de service op.</span><span class="sxs-lookup"><span data-stu-id="7454c-213">Specifies the status for the service.</span></span>

<span data-ttu-id="7454c-214">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="7454c-214">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="7454c-215">**Onderbroken**.</span><span class="sxs-lookup"><span data-stu-id="7454c-215">**Paused**.</span></span> <span data-ttu-id="7454c-216">Hiermee wordt de service onderbroken.</span><span class="sxs-lookup"><span data-stu-id="7454c-216">Suspends the service.</span></span>
- <span data-ttu-id="7454c-217">**Wordt uitgevoerd**.</span><span class="sxs-lookup"><span data-stu-id="7454c-217">**Running**.</span></span> <span data-ttu-id="7454c-218">De service wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="7454c-218">Starts the service.</span></span>
- <span data-ttu-id="7454c-219">**Gestopt**.</span><span class="sxs-lookup"><span data-stu-id="7454c-219">**Stopped**.</span></span> <span data-ttu-id="7454c-220">Hiermee stopt u de service.</span><span class="sxs-lookup"><span data-stu-id="7454c-220">Stops the service.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Paused, Running, Stopped

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7454c-221">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="7454c-221">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="7454c-222">Hiermee geeft u de **security descriptor** voor de service op in **SDDL** -indeling.</span><span class="sxs-lookup"><span data-stu-id="7454c-222">Specifies the **SecurityDescriptor** for the service in **Sddl** format.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sd

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7454c-223">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7454c-223">-WhatIf</span></span>

<span data-ttu-id="7454c-224">Hier wordt weer gegeven wat er gebeurt als er `Set-Service` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7454c-224">Shows what would happen if `Set-Service` runs.</span></span> <span data-ttu-id="7454c-225">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7454c-225">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="7454c-226">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7454c-226">CommonParameters</span></span>

<span data-ttu-id="7454c-227">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7454c-227">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7454c-228">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7454c-228">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7454c-229">INVOER</span><span class="sxs-lookup"><span data-stu-id="7454c-229">INPUTS</span></span>

### <span data-ttu-id="7454c-230">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="7454c-230">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="7454c-231">U kunt de pijp lijn gebruiken om een service object of een teken reeks die een service naam bevat te verzenden naar `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="7454c-231">You can use the pipeline to send a service object or a string that contains a service name to `Set-Service`.</span></span>

## <span data-ttu-id="7454c-232">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7454c-232">OUTPUTS</span></span>

### <span data-ttu-id="7454c-233">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="7454c-233">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="7454c-234">Er worden standaard `Set-Service` geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="7454c-234">By default, `Set-Service` doesn't return any objects.</span></span> <span data-ttu-id="7454c-235">Gebruik de para meter **PassThru** voor het uitvoeren van een **ServiceController** -object.</span><span class="sxs-lookup"><span data-stu-id="7454c-235">Use the **PassThru** parameter to output a **ServiceController** object.</span></span>

## <span data-ttu-id="7454c-236">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7454c-236">NOTES</span></span>

<span data-ttu-id="7454c-237">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="7454c-237">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="7454c-238">`Set-Service` vereist verhoogde machtigingen.</span><span class="sxs-lookup"><span data-stu-id="7454c-238">`Set-Service` requires elevated permissions.</span></span> <span data-ttu-id="7454c-239">Gebruik de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="7454c-239">Use the **Run as administrator** option.</span></span>

<span data-ttu-id="7454c-240">`Set-Service` kan alleen services beheren wanneer de huidige gebruiker machtigingen heeft om services te beheren.</span><span class="sxs-lookup"><span data-stu-id="7454c-240">`Set-Service` can only control services when the current user has permissions to manage services.</span></span> <span data-ttu-id="7454c-241">Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.</span><span class="sxs-lookup"><span data-stu-id="7454c-241">If a command doesn't work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="7454c-242">Als u de service naam of weergave naam van een service wilt zoeken, gebruikt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="7454c-242">To find a service's service name or display name, use `Get-Service`.</span></span> <span data-ttu-id="7454c-243">De service namen bevinden zich in de kolom **naam** en de weergave namen bevinden zich in de kolom **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="7454c-243">The service names are in the **Name** column and the display names are in the **DisplayName** column.</span></span>

## <span data-ttu-id="7454c-244">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7454c-244">RELATED LINKS</span></span>

[<span data-ttu-id="7454c-245">Get-Service</span><span class="sxs-lookup"><span data-stu-id="7454c-245">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="7454c-246">New-Service</span><span class="sxs-lookup"><span data-stu-id="7454c-246">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="7454c-247">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="7454c-247">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="7454c-248">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="7454c-248">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="7454c-249">Start-Service</span><span class="sxs-lookup"><span data-stu-id="7454c-249">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="7454c-250">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="7454c-250">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="7454c-251">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="7454c-251">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="7454c-252">Verwijderen-service</span><span class="sxs-lookup"><span data-stu-id="7454c-252">Remove-Service</span></span>](Remove-Service.md)
