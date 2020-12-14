---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: 0c6cac03f1acbda35069780f0c53eaf6685813ff
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706029"
---
# <span data-ttu-id="054ba-102">Set-Service</span><span class="sxs-lookup"><span data-stu-id="054ba-102">Set-Service</span></span>

## <span data-ttu-id="054ba-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="054ba-103">SYNOPSIS</span></span>
<span data-ttu-id="054ba-104">Hiermee wordt een service gestart, gestopt en onderbroken, en worden de eigenschappen ervan gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="054ba-104">Starts, stops, and suspends a service, and changes its properties.</span></span>

## <span data-ttu-id="054ba-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="054ba-105">SYNTAX</span></span>

### <span data-ttu-id="054ba-106">Naam (standaard)</span><span class="sxs-lookup"><span data-stu-id="054ba-106">Name (Default)</span></span>

```
Set-Service [-Name] <String> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-Status <String>]
 [-SecurityDescriptorSddl <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="054ba-107">Input object</span><span class="sxs-lookup"><span data-stu-id="054ba-107">InputObject</span></span>

```
Set-Service [-InputObject] <ServiceController> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-SecurityDescriptorSddl <String>]
 [-Status <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="054ba-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="054ba-108">DESCRIPTION</span></span>

<span data-ttu-id="054ba-109">`Set-Service`Met de cmdlet worden de eigenschappen van een service gewijzigd, zoals de **status**, **Beschrijving**, **DisplayName** en **opstart type**.</span><span class="sxs-lookup"><span data-stu-id="054ba-109">The `Set-Service` cmdlet changes the properties of a service such as the **Status**, **Description**, **DisplayName**, and **StartupType**.</span></span> <span data-ttu-id="054ba-110">`Set-Service` kan een service starten, stoppen, onderbreken of onderbreken.</span><span class="sxs-lookup"><span data-stu-id="054ba-110">`Set-Service` can start, stop, suspend, or pause a service.</span></span> <span data-ttu-id="054ba-111">Als u een service wilt identificeren, voert u de service naam in of verzendt u een service object.</span><span class="sxs-lookup"><span data-stu-id="054ba-111">To identify a service, enter its service name or submit a service object.</span></span> <span data-ttu-id="054ba-112">Of verzend een service naam of Service object omlaag in de pijp lijn `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="054ba-112">Or, send a service name or service object down the pipeline to `Set-Service`.</span></span>

## <span data-ttu-id="054ba-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="054ba-113">EXAMPLES</span></span>

### <span data-ttu-id="054ba-114">Voor beeld 1: een weergave naam wijzigen</span><span class="sxs-lookup"><span data-stu-id="054ba-114">Example 1: Change a display name</span></span>

<span data-ttu-id="054ba-115">In dit voor beeld wordt de weergave naam van een service gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="054ba-115">In this example, a service's display name is changed.</span></span> <span data-ttu-id="054ba-116">Als u de oorspronkelijke weergave naam wilt weer geven, gebruikt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="054ba-116">To view the original display name, use `Get-Service`.</span></span>

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

<span data-ttu-id="054ba-117">`Set-Service` maakt gebruik van de para meter **name** om de naam van de service op te geven, **lanmanworkstation**.</span><span class="sxs-lookup"><span data-stu-id="054ba-117">`Set-Service` uses the **Name** parameter to specify the service's name, **LanmanWorkstation**.</span></span> <span data-ttu-id="054ba-118">Met de para meter **DisplayName** geeft u de nieuwe weergave naam op: **LANMAN-werk station**.</span><span class="sxs-lookup"><span data-stu-id="054ba-118">The **DisplayName** parameter specifies the new display name, **LanMan Workstation**.</span></span>

### <span data-ttu-id="054ba-119">Voor beeld 2: het opstart type van Services wijzigen</span><span class="sxs-lookup"><span data-stu-id="054ba-119">Example 2: Change the startup type of services</span></span>

<span data-ttu-id="054ba-120">In dit voor beeld ziet u hoe u het opstart type van een service wijzigt.</span><span class="sxs-lookup"><span data-stu-id="054ba-120">This example shows how to change a service's startup type.</span></span>

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

<span data-ttu-id="054ba-121">`Set-Service`maakt gebruik van de para meter **name** om de naam van de service **op te geven.**</span><span class="sxs-lookup"><span data-stu-id="054ba-121">`Set-Service` uses the **Name** parameter to specify the service's name, **BITS**.</span></span> <span data-ttu-id="054ba-122">Met de para meter **opstart type** wordt de service ingesteld op **automatisch**.</span><span class="sxs-lookup"><span data-stu-id="054ba-122">The **StartupType** parameter sets the service to **Automatic**.</span></span>

<span data-ttu-id="054ba-123">`Get-Service` maakt gebruik van de para meter **name** om de **bits** -service op te geven en verzendt het object omlaag in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="054ba-123">`Get-Service` uses the **Name** parameter to specify the **BITS** service and sends the object down the pipeline.</span></span> <span data-ttu-id="054ba-124">`Select-Object` gebruikt de para meter **Property** om de status van de **bits** -service weer te geven.</span><span class="sxs-lookup"><span data-stu-id="054ba-124">`Select-Object` uses the **Property** parameter to display the **BITS** service's status.</span></span>

### <span data-ttu-id="054ba-125">Voor beeld 3: de beschrijving van een service wijzigen</span><span class="sxs-lookup"><span data-stu-id="054ba-125">Example 3: Change the description of a service</span></span>

<span data-ttu-id="054ba-126">In dit voor beeld wordt de beschrijving van de BITS-service gewijzigd en wordt het resultaat weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="054ba-126">This example changes the BITS service's description and displays the result.</span></span>

<span data-ttu-id="054ba-127">De `Get-CimInstance` cmdlet wordt gebruikt omdat deze een **Win32_Service** -object retourneert dat de **Beschrijving** van de service bevat.</span><span class="sxs-lookup"><span data-stu-id="054ba-127">The `Get-CimInstance` cmdlet is used because it returns a **Win32_Service** object that includes the service's **Description**.</span></span>

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

<span data-ttu-id="054ba-128">`Get-CimInstance` Hiermee wordt het object naar beneden verzonden naar de pijp lijn `Format-List` en worden de naam en beschrijving van de service weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="054ba-128">`Get-CimInstance` sends the object down the pipeline to `Format-List` and displays the service's name and description.</span></span> <span data-ttu-id="054ba-129">Voor vergelijkings doeleinden wordt de opdracht uitgevoerd vóór en na het bijwerken van de beschrijving.</span><span class="sxs-lookup"><span data-stu-id="054ba-129">For comparison purposes, the command is run before and after the description is updated.</span></span>

<span data-ttu-id="054ba-130">`Set-Service` maakt gebruik van de para meter **name** om de **bits** -service op te geven.</span><span class="sxs-lookup"><span data-stu-id="054ba-130">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="054ba-131">De **beschrijvings** parameter bevat de bijgewerkte tekst voor de beschrijving van de service.</span><span class="sxs-lookup"><span data-stu-id="054ba-131">The **Description** parameter specifies the updated text for the services' description.</span></span>

### <span data-ttu-id="054ba-132">Voor beeld 4: een service starten</span><span class="sxs-lookup"><span data-stu-id="054ba-132">Example 4: Start a service</span></span>

<span data-ttu-id="054ba-133">In dit voor beeld wordt een service gestart.</span><span class="sxs-lookup"><span data-stu-id="054ba-133">In this example, a service is started.</span></span>

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

<span data-ttu-id="054ba-134">`Set-Service` maakt gebruik van de para meter **name** om de service, **WinRM** op te geven.</span><span class="sxs-lookup"><span data-stu-id="054ba-134">`Set-Service` uses the **Name** parameter to specify the service, **WinRM**.</span></span> <span data-ttu-id="054ba-135">De para meter **status** gebruikt de waarde **die wordt gebruikt** om de service te starten.</span><span class="sxs-lookup"><span data-stu-id="054ba-135">The **Status** parameter uses the value **Running** to start the service.</span></span> <span data-ttu-id="054ba-136">De para meter **PassThru** voert een **ServiceController** -object uit dat de resultaten weergeeft.</span><span class="sxs-lookup"><span data-stu-id="054ba-136">The **PassThru** parameter outputs a **ServiceController** object that displays the results.</span></span>

### <span data-ttu-id="054ba-137">Voor beeld 5: een service opschorten</span><span class="sxs-lookup"><span data-stu-id="054ba-137">Example 5: Suspend a service</span></span>

<span data-ttu-id="054ba-138">In dit voor beeld wordt de pijp lijn gebruikt om de service te onderbreken.</span><span class="sxs-lookup"><span data-stu-id="054ba-138">This example uses the pipeline to pause to service.</span></span>

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

<span data-ttu-id="054ba-139">`Get-Service` maakt gebruik van de para meter **name** om de **Schedule** -service op te geven en verzendt het object omlaag in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="054ba-139">`Get-Service` uses the **Name** parameter to specify the **Schedule** service, and sends the object down the pipeline.</span></span> <span data-ttu-id="054ba-140">`Set-Service` maakt gebruik van de para meter **status** om de service in te stellen op **onderbroken**.</span><span class="sxs-lookup"><span data-stu-id="054ba-140">`Set-Service` uses the **Status** parameter to set the service to **Paused**.</span></span>

### <span data-ttu-id="054ba-141">Voor beeld 6: een service stoppen</span><span class="sxs-lookup"><span data-stu-id="054ba-141">Example 6: Stop a service</span></span>

<span data-ttu-id="054ba-142">In dit voor beeld wordt een variabele gebruikt om een service te stoppen.</span><span class="sxs-lookup"><span data-stu-id="054ba-142">This example uses a variable to stop a service.</span></span>

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

<span data-ttu-id="054ba-143">`Get-Service` maakt gebruik van de para meter **name** om de service, de **planning** op te geven.</span><span class="sxs-lookup"><span data-stu-id="054ba-143">`Get-Service` uses the **Name** parameter to specify the service, **Schedule**.</span></span> <span data-ttu-id="054ba-144">Het object wordt opgeslagen in de variabele `$S` .</span><span class="sxs-lookup"><span data-stu-id="054ba-144">The object is stored in the variable, `$S`.</span></span> <span data-ttu-id="054ba-145">`Set-Service` maakt gebruik van de para meter **input object** en geeft het object op dat is opgeslagen `$S` .</span><span class="sxs-lookup"><span data-stu-id="054ba-145">`Set-Service` uses the **InputObject** parameter and specifies the object stored `$S`.</span></span> <span data-ttu-id="054ba-146">Met de para meter **status** wordt de service ingesteld op **gestopt**.</span><span class="sxs-lookup"><span data-stu-id="054ba-146">The **Status** parameter sets the service to **Stopped**.</span></span>

### <span data-ttu-id="054ba-147">Voor beeld 7: een service op een extern systeem stoppen</span><span class="sxs-lookup"><span data-stu-id="054ba-147">Example 7: Stop a service on a remote system</span></span>

<span data-ttu-id="054ba-148">In dit voor beeld wordt een service op een externe computer gestopt.</span><span class="sxs-lookup"><span data-stu-id="054ba-148">This example stops a service on a remote computer.</span></span>
<span data-ttu-id="054ba-149">Zie [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="054ba-149">For more information, see [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```powershell
$Cred = Get-Credential
$S = Get-Service -Name Schedule
Invoke-Command -ComputerName server01.contoso.com -Credential $Cred -ScriptBlock {
  Set-Service -InputObject $S -Status Stopped
}
```

<span data-ttu-id="054ba-150">`Get-Credential` vraagt naar een gebruikers naam en wacht woord en slaat de referenties op in de `$Cred` variabele.</span><span class="sxs-lookup"><span data-stu-id="054ba-150">`Get-Credential` prompts for a username and password, and stores the credentials in the `$Cred` variable.</span></span> <span data-ttu-id="054ba-151">`Get-Service` maakt gebruik van de para meter **name** om de **Schedule** -service op te geven.</span><span class="sxs-lookup"><span data-stu-id="054ba-151">`Get-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="054ba-152">Het object wordt opgeslagen in de variabele `$S` .</span><span class="sxs-lookup"><span data-stu-id="054ba-152">The object is stored in the variable, `$S`.</span></span>

<span data-ttu-id="054ba-153">`Invoke-Command` maakt gebruik van de para meter **ComputerName** om een externe computer op te geven.</span><span class="sxs-lookup"><span data-stu-id="054ba-153">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer.</span></span> <span data-ttu-id="054ba-154">De para meter **Credential** gebruikt de `$Cred` variabele om u aan te melden bij de computer.</span><span class="sxs-lookup"><span data-stu-id="054ba-154">The **Credential** parameter uses the `$Cred` variable to sign on to the computer.</span></span> <span data-ttu-id="054ba-155">De **script Block** -aanroepen `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="054ba-155">The **ScriptBlock** calls `Set-Service`.</span></span> <span data-ttu-id="054ba-156">De **input object** para meter geeft u het Service object op dat is opgeslagen `$S` .</span><span class="sxs-lookup"><span data-stu-id="054ba-156">The **InputObject** parameter specifies the service object stored `$S`.</span></span> <span data-ttu-id="054ba-157">Met de para meter **status** wordt de service ingesteld op **gestopt**.</span><span class="sxs-lookup"><span data-stu-id="054ba-157">The **Status** parameter sets the service to **Stopped**.</span></span>

### <span data-ttu-id="054ba-158">Voor beeld 8: de referentie van een service wijzigen</span><span class="sxs-lookup"><span data-stu-id="054ba-158">Example 8: Change credential of a service</span></span>

<span data-ttu-id="054ba-159">In dit voor beeld worden de referenties gewijzigd die worden gebruikt voor het beheren van een service.</span><span class="sxs-lookup"><span data-stu-id="054ba-159">This example changes the credentials that are used to manage a service.</span></span>

```powershell
$credential = Get-Credential
Set-Service -Name Schedule -Credential $credential
```

<span data-ttu-id="054ba-160">`Get-Credential` vraagt naar een gebruikers naam en wacht woord en slaat de referenties op in de `$credential` variabele.</span><span class="sxs-lookup"><span data-stu-id="054ba-160">`Get-Credential` prompts for a username and password, and stores the credentials in the `$credential` variable.</span></span> <span data-ttu-id="054ba-161">`Set-Service` maakt gebruik van de para meter **name** om de **Schedule** -service op te geven.</span><span class="sxs-lookup"><span data-stu-id="054ba-161">`Set-Service` uses the **Name** parameter to specify the **Schedule** service.</span></span> <span data-ttu-id="054ba-162">De para meter **Credential** maakt gebruik van de `$credential` variabele en werkt de **Schedule** -service bij.</span><span class="sxs-lookup"><span data-stu-id="054ba-162">The **Credential** parameter uses the `$credential` variable and updates the **Schedule** service.</span></span>

### <span data-ttu-id="054ba-163">Voor beeld 9: de security descriptor van een service wijzigen</span><span class="sxs-lookup"><span data-stu-id="054ba-163">Example 9: Change the SecurityDescriptor of a service</span></span>

<span data-ttu-id="054ba-164">In dit voor beeld wordt de **security descriptor** van een service gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="054ba-164">This example changes a service's **SecurityDescriptor**.</span></span>

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
Set-Service -Name "BITS" -SecurityDescriptorSddl $SDDL
```

<span data-ttu-id="054ba-165">De **security descriptor** wordt opgeslagen in de `$SDDL` variabele.</span><span class="sxs-lookup"><span data-stu-id="054ba-165">The **SecurityDescriptor** is stored in the `$SDDL` variable.</span></span> <span data-ttu-id="054ba-166">`Set-Service` maakt gebruik van de para meter **name** om de **bits** -service op te geven.</span><span class="sxs-lookup"><span data-stu-id="054ba-166">`Set-Service` uses the **Name** parameter to specify the **BITS** service.</span></span> <span data-ttu-id="054ba-167">De para meter **SecurityDescriptorSddl** maakt gebruik `$SDDL` van om de **security descriptor** voor de **bits** -service te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="054ba-167">The **SecurityDescriptorSddl** parameter uses `$SDDL` to change the **SecurityDescriptor** for the **BITS** service.</span></span>

## <span data-ttu-id="054ba-168">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="054ba-168">PARAMETERS</span></span>

### <span data-ttu-id="054ba-169">-Confirm</span><span class="sxs-lookup"><span data-stu-id="054ba-169">-Confirm</span></span>

<span data-ttu-id="054ba-170">Vraagt u om bevestiging voordat deze wordt uitgevoerd `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="054ba-170">Prompts you for confirmation before running `Set-Service`.</span></span>

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

### <span data-ttu-id="054ba-171">-Credential</span><span class="sxs-lookup"><span data-stu-id="054ba-171">-Credential</span></span>

<span data-ttu-id="054ba-172">Hiermee geeft u het account op dat door de service wordt gebruikt als [account voor aanmelding](/windows/desktop/ad/about-service-logon-accounts)bij de service.</span><span class="sxs-lookup"><span data-stu-id="054ba-172">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="054ba-173">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**, of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="054ba-173">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="054ba-174">Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="054ba-174">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="054ba-175">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="054ba-175">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="054ba-176">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="054ba-176">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

<span data-ttu-id="054ba-177">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="054ba-177">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="054ba-178">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="054ba-178">-Description</span></span>

<span data-ttu-id="054ba-179">Hiermee geeft u een nieuwe beschrijving op voor de service.</span><span class="sxs-lookup"><span data-stu-id="054ba-179">Specifies a new description for the service.</span></span>

<span data-ttu-id="054ba-180">De beschrijving van de service wordt weer gegeven in **computer beheer, services**.</span><span class="sxs-lookup"><span data-stu-id="054ba-180">The service description appears in **Computer Management, Services**.</span></span> <span data-ttu-id="054ba-181">De **Beschrijving** is geen eigenschap van het `Get-Service` **ServiceController** -object.</span><span class="sxs-lookup"><span data-stu-id="054ba-181">The **Description** isn't a property of the `Get-Service` **ServiceController** object.</span></span> <span data-ttu-id="054ba-182">Als u de beschrijving van de service wilt zien, gebruikt u `Get-CimInstance` die een **Win32_Service** -object retourneert dat de service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="054ba-182">To see the service description, use `Get-CimInstance` that returns a **Win32_Service** object that represents the service.</span></span>

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

### <span data-ttu-id="054ba-183">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="054ba-183">-DisplayName</span></span>

<span data-ttu-id="054ba-184">Hiermee geeft u een nieuwe weergave naam voor de service op.</span><span class="sxs-lookup"><span data-stu-id="054ba-184">Specifies a new display name for the service.</span></span>

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

### <span data-ttu-id="054ba-185">-Force</span><span class="sxs-lookup"><span data-stu-id="054ba-185">-Force</span></span>

<span data-ttu-id="054ba-186">Hiermee geeft u de stop modus van de service op.</span><span class="sxs-lookup"><span data-stu-id="054ba-186">Specifies the Stop mode of the service.</span></span> <span data-ttu-id="054ba-187">Deze para meter werkt alleen wanneer `-Status Stopped` wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="054ba-187">This parameter only works when `-Status Stopped` is used.</span></span> <span data-ttu-id="054ba-188">Bij inschakeling worden `Set-Service` de afhankelijke services gestopt voordat de doel service wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="054ba-188">If enabled, `Set-Service` stops the dependent services before the target service is stopped.</span></span> <span data-ttu-id="054ba-189">Standaard worden uitzonde ringen gegenereerd wanneer andere actieve services afhankelijk zijn van de doel service.</span><span class="sxs-lookup"><span data-stu-id="054ba-189">By default, exceptions are raised when other running services depend on the target service.</span></span>

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

### <span data-ttu-id="054ba-190">-Input object</span><span class="sxs-lookup"><span data-stu-id="054ba-190">-InputObject</span></span>

<span data-ttu-id="054ba-191">Hiermee geeft u een **ServiceController** -object op dat de service vertegenwoordigt die moet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="054ba-191">Specifies a **ServiceController** object that represents the service to change.</span></span> <span data-ttu-id="054ba-192">Voer een variabele in die het object bevat of typ een opdracht of expressie waarmee het object wordt opgehaald, zoals een `Get-Service` opdracht.</span><span class="sxs-lookup"><span data-stu-id="054ba-192">Enter a variable that contains the object, or type a command or expression that gets the object, such as a `Get-Service` command.</span></span> <span data-ttu-id="054ba-193">U kunt de pijp lijn gebruiken om een service object naar te verzenden `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="054ba-193">You can use the pipeline to send a service object to `Set-Service`.</span></span>

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

### <span data-ttu-id="054ba-194">-Name</span><span class="sxs-lookup"><span data-stu-id="054ba-194">-Name</span></span>

<span data-ttu-id="054ba-195">Hiermee geeft u de service naam op van de service die moet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="054ba-195">Specifies the service name of the service to be changed.</span></span> <span data-ttu-id="054ba-196">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="054ba-196">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="054ba-197">U kunt de pijp lijn gebruiken om een service naam naar te verzenden `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="054ba-197">You can use the pipeline to send a service name to `Set-Service`.</span></span>

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

### <span data-ttu-id="054ba-198">-PassThru</span><span class="sxs-lookup"><span data-stu-id="054ba-198">-PassThru</span></span>

<span data-ttu-id="054ba-199">Retourneert een **ServiceController** -object dat staat voor de services die zijn gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="054ba-199">Returns a **ServiceController** object that represents the services that were changed.</span></span> <span data-ttu-id="054ba-200">Standaard genereert geen `Set-Service` uitvoer.</span><span class="sxs-lookup"><span data-stu-id="054ba-200">By default, `Set-Service` doesn't generate any output.</span></span>

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

### <span data-ttu-id="054ba-201">-Opstart type</span><span class="sxs-lookup"><span data-stu-id="054ba-201">-StartupType</span></span>

<span data-ttu-id="054ba-202">Hiermee geeft u de start modus van de service op.</span><span class="sxs-lookup"><span data-stu-id="054ba-202">Specifies the start mode of the service.</span></span>

<span data-ttu-id="054ba-203">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="054ba-203">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="054ba-204">**Automatisch** : de service wordt gestart of is door het besturings systeem gestart tijdens het opstarten van het systeem.</span><span class="sxs-lookup"><span data-stu-id="054ba-204">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="054ba-205">Als een service die automatisch wordt gestart, afhankelijk is van een hand matig gestarte service, wordt de hand matig gestarte service ook automatisch gestart bij het opstarten van het systeem.</span><span class="sxs-lookup"><span data-stu-id="054ba-205">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="054ba-206">**AutomaticDelayedStart** -binnenkort gestart nadat het systeem is opgestart.</span><span class="sxs-lookup"><span data-stu-id="054ba-206">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="054ba-207">**Uitgeschakeld** : de service is uitgeschakeld en kan niet worden gestart door een gebruiker of toepassing.</span><span class="sxs-lookup"><span data-stu-id="054ba-207">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="054ba-208">**InvalidValue** -heeft geen effect.</span><span class="sxs-lookup"><span data-stu-id="054ba-208">**InvalidValue** - Has no effect.</span></span> <span data-ttu-id="054ba-209">De cmdlet retourneert geen fout, maar de opstart type van de service is niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="054ba-209">The cmdlet does not return an error but the StartupType of the service is not changed.</span></span>
- <span data-ttu-id="054ba-210">**Hand matig** : de service wordt alleen hand matig gestart door een gebruiker, met behulp van service besturings beheer of door een toepassing.</span><span class="sxs-lookup"><span data-stu-id="054ba-210">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

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

### <span data-ttu-id="054ba-211">-Status</span><span class="sxs-lookup"><span data-stu-id="054ba-211">-Status</span></span>

<span data-ttu-id="054ba-212">Hiermee geeft u de status van de service op.</span><span class="sxs-lookup"><span data-stu-id="054ba-212">Specifies the status for the service.</span></span>

<span data-ttu-id="054ba-213">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="054ba-213">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="054ba-214">**Onderbroken**.</span><span class="sxs-lookup"><span data-stu-id="054ba-214">**Paused**.</span></span> <span data-ttu-id="054ba-215">Hiermee wordt de service onderbroken.</span><span class="sxs-lookup"><span data-stu-id="054ba-215">Suspends the service.</span></span>
- <span data-ttu-id="054ba-216">**Wordt uitgevoerd**.</span><span class="sxs-lookup"><span data-stu-id="054ba-216">**Running**.</span></span> <span data-ttu-id="054ba-217">De service wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="054ba-217">Starts the service.</span></span>
- <span data-ttu-id="054ba-218">**Gestopt**.</span><span class="sxs-lookup"><span data-stu-id="054ba-218">**Stopped**.</span></span> <span data-ttu-id="054ba-219">Hiermee stopt u de service.</span><span class="sxs-lookup"><span data-stu-id="054ba-219">Stops the service.</span></span>

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

### <span data-ttu-id="054ba-220">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="054ba-220">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="054ba-221">Hiermee geeft u de **security descriptor** voor de service op in **SDDL** -indeling.</span><span class="sxs-lookup"><span data-stu-id="054ba-221">Specifies the **SecurityDescriptor** for the service in **Sddl** format.</span></span>

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

### <span data-ttu-id="054ba-222">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="054ba-222">-WhatIf</span></span>

<span data-ttu-id="054ba-223">Hier wordt weer gegeven wat er gebeurt als er `Set-Service` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="054ba-223">Shows what would happen if `Set-Service` runs.</span></span> <span data-ttu-id="054ba-224">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="054ba-224">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="054ba-225">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="054ba-225">CommonParameters</span></span>

<span data-ttu-id="054ba-226">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="054ba-226">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="054ba-227">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="054ba-227">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="054ba-228">INVOER</span><span class="sxs-lookup"><span data-stu-id="054ba-228">INPUTS</span></span>

### <span data-ttu-id="054ba-229">System. ServiceProcess. ServiceController, System. String</span><span class="sxs-lookup"><span data-stu-id="054ba-229">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="054ba-230">U kunt de pijp lijn gebruiken om een service object of een teken reeks die een service naam bevat te verzenden naar `Set-Service` .</span><span class="sxs-lookup"><span data-stu-id="054ba-230">You can use the pipeline to send a service object or a string that contains a service name to `Set-Service`.</span></span>

## <span data-ttu-id="054ba-231">UITVOER</span><span class="sxs-lookup"><span data-stu-id="054ba-231">OUTPUTS</span></span>

### <span data-ttu-id="054ba-232">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="054ba-232">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="054ba-233">Er worden standaard `Set-Service` geen objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="054ba-233">By default, `Set-Service` doesn't return any objects.</span></span> <span data-ttu-id="054ba-234">Gebruik de para meter **PassThru** voor het uitvoeren van een **ServiceController** -object.</span><span class="sxs-lookup"><span data-stu-id="054ba-234">Use the **PassThru** parameter to output a **ServiceController** object.</span></span>

## <span data-ttu-id="054ba-235">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="054ba-235">NOTES</span></span>

<span data-ttu-id="054ba-236">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="054ba-236">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="054ba-237">`Set-Service` vereist verhoogde machtigingen.</span><span class="sxs-lookup"><span data-stu-id="054ba-237">`Set-Service` requires elevated permissions.</span></span> <span data-ttu-id="054ba-238">Gebruik de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="054ba-238">Use the **Run as administrator** option.</span></span>

<span data-ttu-id="054ba-239">`Set-Service` kan alleen services beheren wanneer de huidige gebruiker machtigingen heeft om services te beheren.</span><span class="sxs-lookup"><span data-stu-id="054ba-239">`Set-Service` can only control services when the current user has permissions to manage services.</span></span> <span data-ttu-id="054ba-240">Als een opdracht niet correct werkt, beschikt u mogelijk niet over de vereiste machtigingen.</span><span class="sxs-lookup"><span data-stu-id="054ba-240">If a command doesn't work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="054ba-241">Als u de service naam of weergave naam van een service wilt zoeken, gebruikt u `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="054ba-241">To find a service's service name or display name, use `Get-Service`.</span></span> <span data-ttu-id="054ba-242">De service namen bevinden zich in de kolom **naam** en de weergave namen bevinden zich in de kolom **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="054ba-242">The service names are in the **Name** column and the display names are in the **DisplayName** column.</span></span>

## <span data-ttu-id="054ba-243">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="054ba-243">RELATED LINKS</span></span>

[<span data-ttu-id="054ba-244">Get-Service</span><span class="sxs-lookup"><span data-stu-id="054ba-244">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="054ba-245">New-Service</span><span class="sxs-lookup"><span data-stu-id="054ba-245">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="054ba-246">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="054ba-246">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="054ba-247">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="054ba-247">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="054ba-248">Start-Service</span><span class="sxs-lookup"><span data-stu-id="054ba-248">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="054ba-249">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="054ba-249">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="054ba-250">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="054ba-250">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="054ba-251">Verwijderen-service</span><span class="sxs-lookup"><span data-stu-id="054ba-251">Remove-Service</span></span>](Remove-Service.md)
