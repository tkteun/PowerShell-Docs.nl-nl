---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: 758b0a8ef9a5f65f0e7cfa7f3633086cf9f0445d
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891765"
---
# <span data-ttu-id="c350d-103">New-Service</span><span class="sxs-lookup"><span data-stu-id="c350d-103">New-Service</span></span>

## <span data-ttu-id="c350d-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c350d-104">SYNOPSIS</span></span>
<span data-ttu-id="c350d-105">Hiermee maakt u een nieuwe Windows-service.</span><span class="sxs-lookup"><span data-stu-id="c350d-105">Creates a new Windows service.</span></span>

## <span data-ttu-id="c350d-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c350d-106">SYNTAX</span></span>

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Credential <PSCredential>] [-DependsOn <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c350d-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c350d-107">DESCRIPTION</span></span>

<span data-ttu-id="c350d-108">De `New-Service` cmdlet maakt een nieuwe vermelding voor een Windows-service in het REGI ster en in de service database.</span><span class="sxs-lookup"><span data-stu-id="c350d-108">The `New-Service` cmdlet creates a new entry for a Windows service in the registry and in the service database.</span></span> <span data-ttu-id="c350d-109">Een nieuwe service vereist een uitvoerbaar bestand dat tijdens de service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c350d-109">A new service requires an executable file that runs during the service.</span></span>

<span data-ttu-id="c350d-110">Met de para meters van deze cmdlet kunt u de weergave naam, de beschrijving, het opstart type en de afhankelijkheden van de service instellen.</span><span class="sxs-lookup"><span data-stu-id="c350d-110">The parameters of this cmdlet let you set the display name, description, startup type, and dependencies of the service.</span></span>

## <span data-ttu-id="c350d-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c350d-111">EXAMPLES</span></span>

### <span data-ttu-id="c350d-112">Voor beeld 1: een service maken</span><span class="sxs-lookup"><span data-stu-id="c350d-112">Example 1: Create a service</span></span>

```powershell
New-Service -Name "TestService" -BinaryPathName '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
```

<span data-ttu-id="c350d-113">Met deze opdracht maakt u een service met de naam TestService.</span><span class="sxs-lookup"><span data-stu-id="c350d-113">This command creates a service named TestService.</span></span>

### <span data-ttu-id="c350d-114">Voor beeld 2: een service maken die de beschrijving, het opstart type en de weergave naam bevat</span><span class="sxs-lookup"><span data-stu-id="c350d-114">Example 2: Create a service that includes description, startup type, and display name</span></span>

```powershell
$params = @{
  Name = "TestService"
  BinaryPathName = '"C:\WINDOWS\System32\svchost.exe -k netsvcs"'
  DependsOn = "NetLogon"
  DisplayName = "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
}
New-Service @params
```

<span data-ttu-id="c350d-115">Met deze opdracht maakt u een service met de naam TestService.</span><span class="sxs-lookup"><span data-stu-id="c350d-115">This command creates a service named TestService.</span></span> <span data-ttu-id="c350d-116">Hierbij worden de para meters van gebruikt `New-Service` om een beschrijving, opstart type en weergave naam voor de nieuwe service op te geven.</span><span class="sxs-lookup"><span data-stu-id="c350d-116">It uses the parameters of `New-Service` to specify a description, startup type, and display name for the new service.</span></span>

### <span data-ttu-id="c350d-117">Voor beeld 3: de nieuwe service weer geven</span><span class="sxs-lookup"><span data-stu-id="c350d-117">Example 3: View the new service</span></span>

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

<span data-ttu-id="c350d-118">Met deze opdracht wordt `Get-CimInstance` het **Win32_Service** -object voor de nieuwe service opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c350d-118">This command uses `Get-CimInstance` to get the **Win32_Service** object for the new service.</span></span> <span data-ttu-id="c350d-119">Dit object bevat de start modus en de beschrijving van de service.</span><span class="sxs-lookup"><span data-stu-id="c350d-119">This object includes the start mode and the service description.</span></span>

### <span data-ttu-id="c350d-120">Voor beeld 4: een service verwijderen</span><span class="sxs-lookup"><span data-stu-id="c350d-120">Example 4: Delete a service</span></span>

```powershell
sc.exe delete TestService
# - or -
(Get-CimInstance -Class Win32_Service -Filter "name='TestService'").delete()
```

<span data-ttu-id="c350d-121">In dit voor beeld ziet u twee manieren om de TestService-service te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="c350d-121">This example shows two ways to delete the TestService service.</span></span> <span data-ttu-id="c350d-122">De eerste opdracht maakt gebruik van de optie verwijderen van `Sc.exe` .</span><span class="sxs-lookup"><span data-stu-id="c350d-122">The first command uses the delete option of `Sc.exe`.</span></span> <span data-ttu-id="c350d-123">Met de tweede opdracht wordt de methode **Delete** gebruikt van de **Win32_Service** -objecten die worden `Get-CimInstance` geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c350d-123">The second command uses the **Delete** method of the **Win32_Service** objects that `Get-CimInstance` returns.</span></span>

## <span data-ttu-id="c350d-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c350d-124">PARAMETERS</span></span>

### <span data-ttu-id="c350d-125">-BinaryPathName</span><span class="sxs-lookup"><span data-stu-id="c350d-125">-BinaryPathName</span></span>

<span data-ttu-id="c350d-126">Hiermee geeft u het pad van het uitvoer bare bestand voor de service.</span><span class="sxs-lookup"><span data-stu-id="c350d-126">Specifies the path of the executable file for the service.</span></span> <span data-ttu-id="c350d-127">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="c350d-127">This parameter is required.</span></span>

<span data-ttu-id="c350d-128">Het volledig gekwalificeerde pad naar het binaire bestand van de service.</span><span class="sxs-lookup"><span data-stu-id="c350d-128">The fully qualified path to the service binary file.</span></span> <span data-ttu-id="c350d-129">Als het pad een spatie bevat, moet het een aanhalings teken bevatten zodat het op de juiste wijze wordt geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="c350d-129">If the path contains a space, it must be quoted so that it is correctly interpreted.</span></span> <span data-ttu-id="c350d-130">Bijvoorbeeld `d:\my share\myservice.exe` moet worden opgegeven als `'"d:\my share\myservice.exe"'` .</span><span class="sxs-lookup"><span data-stu-id="c350d-130">For example, `d:\my share\myservice.exe` should be specified as `'"d:\my share\myservice.exe"'`.</span></span>

<span data-ttu-id="c350d-131">Het pad kan ook argumenten bevatten voor een service die automatisch wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="c350d-131">The path can also include arguments for an auto-start service.</span></span> <span data-ttu-id="c350d-132">Bijvoorbeeld `'"d:\myshare\myservice.exe arg1 arg2"'`.</span><span class="sxs-lookup"><span data-stu-id="c350d-132">For example, `'"d:\myshare\myservice.exe arg1 arg2"'`.</span></span> <span data-ttu-id="c350d-133">Deze argumenten worden door gegeven aan het service toegangs punt.</span><span class="sxs-lookup"><span data-stu-id="c350d-133">These arguments are passed to the service entry point.</span></span>

<span data-ttu-id="c350d-134">Zie de para meter **lpBinaryPathName** van [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) API voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c350d-134">For more information, see the **lpBinaryPathName** parameter of [CreateServiceW](/windows/win32/api/winsvc/nf-winsvc-createservicew) API.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c350d-135">-Credential</span><span class="sxs-lookup"><span data-stu-id="c350d-135">-Credential</span></span>

<span data-ttu-id="c350d-136">Hiermee geeft u het account op dat door de service wordt gebruikt als [account voor aanmelding](/windows/desktop/ad/about-service-logon-accounts)bij de service.</span><span class="sxs-lookup"><span data-stu-id="c350d-136">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="c350d-137">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01**, of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c350d-137">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="c350d-138">Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="c350d-138">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="c350d-139">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="c350d-139">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="c350d-140">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="c350d-140">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="c350d-141">-DependsOn</span><span class="sxs-lookup"><span data-stu-id="c350d-141">-DependsOn</span></span>

<span data-ttu-id="c350d-142">Hiermee geeft u de namen op van andere services waarvan de nieuwe service afhankelijk is.</span><span class="sxs-lookup"><span data-stu-id="c350d-142">Specifies the names of other services upon which the new service depends.</span></span> <span data-ttu-id="c350d-143">Als u meerdere service namen wilt opgeven, gebruikt u een komma om de namen van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="c350d-143">To enter multiple service names, use a comma to separate the names.</span></span>

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

### <span data-ttu-id="c350d-144">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c350d-144">-Description</span></span>

<span data-ttu-id="c350d-145">Hiermee geeft u een beschrijving van de service.</span><span class="sxs-lookup"><span data-stu-id="c350d-145">Specifies a description of the service.</span></span>

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

### <span data-ttu-id="c350d-146">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="c350d-146">-DisplayName</span></span>

<span data-ttu-id="c350d-147">Hiermee geeft u een weergave naam voor de service op.</span><span class="sxs-lookup"><span data-stu-id="c350d-147">Specifies a display name for the service.</span></span>

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

### <span data-ttu-id="c350d-148">-Name</span><span class="sxs-lookup"><span data-stu-id="c350d-148">-Name</span></span>

<span data-ttu-id="c350d-149">Hiermee geeft u de naam van de service.</span><span class="sxs-lookup"><span data-stu-id="c350d-149">Specifies the name of the service.</span></span> <span data-ttu-id="c350d-150">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="c350d-150">This parameter is required.</span></span>

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

### <span data-ttu-id="c350d-151">-Opstart type</span><span class="sxs-lookup"><span data-stu-id="c350d-151">-StartupType</span></span>

<span data-ttu-id="c350d-152">Hiermee stelt u het opstart type van de service in.</span><span class="sxs-lookup"><span data-stu-id="c350d-152">Sets the startup type of the service.</span></span> <span data-ttu-id="c350d-153">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="c350d-153">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c350d-154">**Automatisch** : de service wordt gestart of is door het besturings systeem gestart tijdens het opstarten van het systeem.</span><span class="sxs-lookup"><span data-stu-id="c350d-154">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="c350d-155">Als een service die automatisch wordt gestart, afhankelijk is van een hand matig gestarte service, wordt de hand matig gestarte service ook automatisch gestart bij het opstarten van het systeem.</span><span class="sxs-lookup"><span data-stu-id="c350d-155">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="c350d-156">**Uitgeschakeld** : de service is uitgeschakeld en kan niet worden gestart door een gebruiker of toepassing.</span><span class="sxs-lookup"><span data-stu-id="c350d-156">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="c350d-157">**Hand matig** : de service wordt alleen hand matig gestart door een gebruiker, met behulp van service besturings beheer of door een toepassing.</span><span class="sxs-lookup"><span data-stu-id="c350d-157">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>
- <span data-ttu-id="c350d-158">**Boot** : geeft aan dat de service een apparaatstuurprogramma is dat door de System loader wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="c350d-158">**Boot** - Indicates that the service is a device driver started by the system loader.</span></span> <span data-ttu-id="c350d-159">Deze waarde is alleen geldig voor apparaatstuurprogramma's.</span><span class="sxs-lookup"><span data-stu-id="c350d-159">This value is valid only for device drivers.</span></span>
- <span data-ttu-id="c350d-160">**Systeem** : geeft aan dat de service een apparaatstuurprogramma is dat is gestart door de functie IOInitSystem ().</span><span class="sxs-lookup"><span data-stu-id="c350d-160">**System** - Indicates that the service is a device driver started by the 'IOInitSystem()' function.</span></span> <span data-ttu-id="c350d-161">Deze waarde is alleen geldig voor apparaatstuurprogramma's.</span><span class="sxs-lookup"><span data-stu-id="c350d-161">This value is valid only for device drivers.</span></span>

 <span data-ttu-id="c350d-162">De standaard waarde is **automatisch**.</span><span class="sxs-lookup"><span data-stu-id="c350d-162">The default value is **Automatic**.</span></span>

```yaml
Type: System.ServiceProcess.ServiceStartMode
Parameter Sets: (All)
Aliases:
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c350d-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c350d-163">-Confirm</span></span>

<span data-ttu-id="c350d-164">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c350d-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c350d-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c350d-165">-WhatIf</span></span>

<span data-ttu-id="c350d-166">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c350d-166">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="c350d-167">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c350d-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c350d-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c350d-168">CommonParameters</span></span>

<span data-ttu-id="c350d-169">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c350d-169">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c350d-170">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c350d-170">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c350d-171">INVOER</span><span class="sxs-lookup"><span data-stu-id="c350d-171">INPUTS</span></span>

### <span data-ttu-id="c350d-172">Geen</span><span class="sxs-lookup"><span data-stu-id="c350d-172">None</span></span>

<span data-ttu-id="c350d-173">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c350d-173">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c350d-174">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c350d-174">OUTPUTS</span></span>

### <span data-ttu-id="c350d-175">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="c350d-175">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="c350d-176">Met deze cmdlet wordt een object geretourneerd dat de nieuwe service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="c350d-176">This cmdlet returns an object that represents the new service.</span></span>

## <span data-ttu-id="c350d-177">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c350d-177">NOTES</span></span>

<span data-ttu-id="c350d-178">Als u deze cmdlet wilt uitvoeren, start u Power shell met de optie **als administrator uitvoeren** .</span><span class="sxs-lookup"><span data-stu-id="c350d-178">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

<span data-ttu-id="c350d-179">Als u een service wilt verwijderen, gebruikt u Sc.exe of gebruikt `Get-CimInstance` u de cmdlet om het **Win32_Service** -object op te halen dat de service vertegenwoordigt en gebruikt u vervolgens de **Delete** -methode om de service te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="c350d-179">To delete a service, use Sc.exe, or use the `Get-CimInstance` cmdlet to get the **Win32_Service** object that represents the service and then use the **Delete** method to delete the service.</span></span> <span data-ttu-id="c350d-180">Het `Get-Service` geretourneerde object heeft geen verwijderings methode.</span><span class="sxs-lookup"><span data-stu-id="c350d-180">The object that `Get-Service` returns does not have a delete method.</span></span>

## <span data-ttu-id="c350d-181">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c350d-181">RELATED LINKS</span></span>

[<span data-ttu-id="c350d-182">Get-Service</span><span class="sxs-lookup"><span data-stu-id="c350d-182">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="c350d-183">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="c350d-183">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="c350d-184">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="c350d-184">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="c350d-185">Set-Service</span><span class="sxs-lookup"><span data-stu-id="c350d-185">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="c350d-186">Start-Service</span><span class="sxs-lookup"><span data-stu-id="c350d-186">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="c350d-187">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="c350d-187">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="c350d-188">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="c350d-188">Suspend-Service</span></span>](Suspend-Service.md)
