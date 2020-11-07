---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: aadb0d53ad180ba1e88d31e5d008c6090ae0c9b3
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345218"
---
# <span data-ttu-id="8b7b2-103">New-Service</span><span class="sxs-lookup"><span data-stu-id="8b7b2-103">New-Service</span></span>

## <span data-ttu-id="8b7b2-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="8b7b2-104">SYNOPSIS</span></span>
<span data-ttu-id="8b7b2-105">Hiermee maakt u een nieuwe Windows-service.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-105">Creates a new Windows service.</span></span>

## <span data-ttu-id="8b7b2-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="8b7b2-106">SYNTAX</span></span>

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartupType>] [-Credential <PSCredential>] [-DependsOn <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8b7b2-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8b7b2-107">DESCRIPTION</span></span>

<span data-ttu-id="8b7b2-108">De `New-Service` cmdlet maakt een nieuwe vermelding voor een Windows-service in het REGI ster en in de service database.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-108">The `New-Service` cmdlet creates a new entry for a Windows service in the registry and in the service database.</span></span> <span data-ttu-id="8b7b2-109">Een nieuwe service vereist een uitvoerbaar bestand dat tijdens de service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-109">A new service requires an executable file that runs during the service.</span></span>

<span data-ttu-id="8b7b2-110">Met de para meters van deze cmdlet kunt u de weergave naam, de beschrijving, het opstart type en de afhankelijkheden van de service instellen.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-110">The parameters of this cmdlet let you set the display name, description, startup type, and dependencies of the service.</span></span>

## <span data-ttu-id="8b7b2-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="8b7b2-111">EXAMPLES</span></span>

### <span data-ttu-id="8b7b2-112">Voor beeld 1: een service maken</span><span class="sxs-lookup"><span data-stu-id="8b7b2-112">Example 1: Create a service</span></span>

```powershell
New-Service -Name "TestService" -BinaryPathName "C:\WINDOWS\System32\svchost.exe -k netsvcs"
```

<span data-ttu-id="8b7b2-113">Met deze opdracht maakt u een service met de naam TestService.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-113">This command creates a service named TestService.</span></span>

### <span data-ttu-id="8b7b2-114">Voor beeld 2: een service maken die de beschrijving, het opstart type en de weergave naam bevat</span><span class="sxs-lookup"><span data-stu-id="8b7b2-114">Example 2: Create a service that includes description, startup type, and display name</span></span>

```powershell
$params = @{
  Name = "TestService"
  BinaryPathName = "C:\WINDOWS\System32\svchost.exe -k netsvcs"
  DependsOn = "NetLogon"
  DisplayName = "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
}
New-Service @params
```

<span data-ttu-id="8b7b2-115">Met deze opdracht maakt u een service met de naam TestService.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-115">This command creates a service named TestService.</span></span> <span data-ttu-id="8b7b2-116">Hierbij worden de para meters van gebruikt `New-Service` om een beschrijving, opstart type en weergave naam voor de nieuwe service op te geven.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-116">It uses the parameters of `New-Service` to specify a description, startup type, and display name for the new service.</span></span>

### <span data-ttu-id="8b7b2-117">Voor beeld 3: de nieuwe service weer geven</span><span class="sxs-lookup"><span data-stu-id="8b7b2-117">Example 3: View the new service</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -Filter "Name='testservice'"
```

```Output
ExitCode  : 0
Name      : testservice
ProcessId : 0
StartMode : Auto
State     : Stopped
Status    : OK
```

<span data-ttu-id="8b7b2-118">Met deze opdracht wordt `Get-CimInstance` het **Win32_Service** -object voor de nieuwe service opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-118">This command uses `Get-CimInstance` to get the **Win32_Service** object for the new service.</span></span> <span data-ttu-id="8b7b2-119">Dit object bevat de start modus en de beschrijving van de service.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-119">This object includes the start mode and the service description.</span></span>

## <span data-ttu-id="8b7b2-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8b7b2-120">PARAMETERS</span></span>

### <span data-ttu-id="8b7b2-121">-BinaryPathName</span><span class="sxs-lookup"><span data-stu-id="8b7b2-121">-BinaryPathName</span></span>

<span data-ttu-id="8b7b2-122">Hiermee geeft u het pad van het uitvoer bare bestand voor de service.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-122">Specifies the path of the executable file for the service.</span></span> <span data-ttu-id="8b7b2-123">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-123">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8b7b2-124">-Credential</span><span class="sxs-lookup"><span data-stu-id="8b7b2-124">-Credential</span></span>

<span data-ttu-id="8b7b2-125">Hiermee geeft u het account op dat door de service wordt gebruikt als [account voor aanmelding](/windows/desktop/ad/about-service-logon-accounts)bij de service.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-125">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="8b7b2-126">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-126">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="8b7b2-127">Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-127">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="8b7b2-128">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="8b7b2-128">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="8b7b2-129">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-129">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="8b7b2-130">-DependsOn</span><span class="sxs-lookup"><span data-stu-id="8b7b2-130">-DependsOn</span></span>

<span data-ttu-id="8b7b2-131">Hiermee geeft u de namen op van andere services waarvan de nieuwe service afhankelijk is.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-131">Specifies the names of other services upon which the new service depends.</span></span> <span data-ttu-id="8b7b2-132">Als u meerdere service namen wilt opgeven, gebruikt u een komma om de namen van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-132">To enter multiple service names, use a comma to separate the names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8b7b2-133">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8b7b2-133">-Description</span></span>

<span data-ttu-id="8b7b2-134">Hiermee geeft u een beschrijving van de service.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-134">Specifies a description of the service.</span></span>

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

### <span data-ttu-id="8b7b2-135">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="8b7b2-135">-DisplayName</span></span>

<span data-ttu-id="8b7b2-136">Hiermee geeft u een weergave naam voor de service op.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-136">Specifies a display name for the service.</span></span>

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

### <span data-ttu-id="8b7b2-137">-Name</span><span class="sxs-lookup"><span data-stu-id="8b7b2-137">-Name</span></span>

<span data-ttu-id="8b7b2-138">Hiermee geeft u de naam van de service.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-138">Specifies the name of the service.</span></span> <span data-ttu-id="8b7b2-139">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-139">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8b7b2-140">-Opstart type</span><span class="sxs-lookup"><span data-stu-id="8b7b2-140">-StartupType</span></span>

<span data-ttu-id="8b7b2-141">Hiermee stelt u het opstart type van de service in.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-141">Sets the startup type of the service.</span></span> <span data-ttu-id="8b7b2-142">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="8b7b2-142">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8b7b2-143">**Automatisch** : de service wordt gestart of is door het besturings systeem gestart tijdens het opstarten van het systeem.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-143">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="8b7b2-144">Als een service die automatisch wordt gestart, afhankelijk is van een hand matig gestarte service, wordt de hand matig gestarte service ook automatisch gestart bij het opstarten van het systeem.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-144">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="8b7b2-145">**AutomaticDelayedStart** -binnenkort gestart nadat het systeem is opgestart.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-145">**AutomaticDelayedStart** - Starts shortly after the system boots.</span></span>
- <span data-ttu-id="8b7b2-146">**Uitgeschakeld** : de service is uitgeschakeld en kan niet worden gestart door een gebruiker of toepassing.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-146">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="8b7b2-147">**InvalidValue** : deze waarde wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-147">**InvalidValue** - This value is not supported.</span></span> <span data-ttu-id="8b7b2-148">Als u deze waarde gebruikt, resulteert dit in een fout.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-148">Using this value results in an error.</span></span>
- <span data-ttu-id="8b7b2-149">**Hand matig** : de service wordt alleen hand matig gestart door een gebruiker, met behulp van service besturings beheer of door een toepassing.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-149">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>

 <span data-ttu-id="8b7b2-150">De standaard waarde is **automatisch**.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-150">The default value is **Automatic**.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases:
Accepted values: Automatic, Manual, Disabled, AutomaticDelayedStart, InvalidValue

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8b7b2-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8b7b2-151">-Confirm</span></span>

<span data-ttu-id="8b7b2-152">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8b7b2-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8b7b2-153">-WhatIf</span></span>

<span data-ttu-id="8b7b2-154">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-154">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="8b7b2-155">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8b7b2-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8b7b2-156">CommonParameters</span></span>

<span data-ttu-id="8b7b2-157">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8b7b2-158">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8b7b2-159">INVOER</span><span class="sxs-lookup"><span data-stu-id="8b7b2-159">INPUTS</span></span>

### <span data-ttu-id="8b7b2-160">Geen</span><span class="sxs-lookup"><span data-stu-id="8b7b2-160">None</span></span>

<span data-ttu-id="8b7b2-161">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-161">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="8b7b2-162">UITVOER</span><span class="sxs-lookup"><span data-stu-id="8b7b2-162">OUTPUTS</span></span>

### <span data-ttu-id="8b7b2-163">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="8b7b2-163">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="8b7b2-164">Met deze cmdlet wordt een object geretourneerd dat de nieuwe service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-164">This cmdlet returns an object that represents the new service.</span></span>

## <span data-ttu-id="8b7b2-165">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="8b7b2-165">NOTES</span></span>

<span data-ttu-id="8b7b2-166">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="8b7b2-166">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="8b7b2-167">Als u deze cmdlet wilt uitvoeren, start u Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="8b7b2-167">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="8b7b2-168">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="8b7b2-168">RELATED LINKS</span></span>

[<span data-ttu-id="8b7b2-169">Get-Service</span><span class="sxs-lookup"><span data-stu-id="8b7b2-169">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="8b7b2-170">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="8b7b2-170">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="8b7b2-171">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="8b7b2-171">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="8b7b2-172">Set-Service</span><span class="sxs-lookup"><span data-stu-id="8b7b2-172">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="8b7b2-173">Start-Service</span><span class="sxs-lookup"><span data-stu-id="8b7b2-173">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="8b7b2-174">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="8b7b2-174">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="8b7b2-175">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="8b7b2-175">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="8b7b2-176">Verwijderen-service</span><span class="sxs-lookup"><span data-stu-id="8b7b2-176">Remove-Service</span></span>](Remove-Service.md)
