---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: 3249ce91a63417f2790997d37e2420c6fcb374d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250594"
---
# <span data-ttu-id="a6128-103">New-Service</span><span class="sxs-lookup"><span data-stu-id="a6128-103">New-Service</span></span>

## <span data-ttu-id="a6128-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a6128-104">SYNOPSIS</span></span>
<span data-ttu-id="a6128-105">Hiermee maakt u een nieuwe Windows-service.</span><span class="sxs-lookup"><span data-stu-id="a6128-105">Creates a new Windows service.</span></span>

## <span data-ttu-id="a6128-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a6128-106">SYNTAX</span></span>

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Credential <PSCredential>] [-DependsOn <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a6128-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a6128-107">DESCRIPTION</span></span>

<span data-ttu-id="a6128-108">De `New-Service` cmdlet maakt een nieuwe vermelding voor een Windows-service in het REGI ster en in de service database.</span><span class="sxs-lookup"><span data-stu-id="a6128-108">The `New-Service` cmdlet creates a new entry for a Windows service in the registry and in the service database.</span></span> <span data-ttu-id="a6128-109">Een nieuwe service vereist een uitvoerbaar bestand dat tijdens de service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a6128-109">A new service requires an executable file that runs during the service.</span></span>

<span data-ttu-id="a6128-110">Met de para meters van deze cmdlet kunt u de weergave naam, de beschrijving, het opstart type en de afhankelijkheden van de service instellen.</span><span class="sxs-lookup"><span data-stu-id="a6128-110">The parameters of this cmdlet let you set the display name, description, startup type, and dependencies of the service.</span></span>

## <span data-ttu-id="a6128-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a6128-111">EXAMPLES</span></span>

### <span data-ttu-id="a6128-112">Voor beeld 1: een service maken</span><span class="sxs-lookup"><span data-stu-id="a6128-112">Example 1: Create a service</span></span>

```powershell
New-Service -Name "TestService" -BinaryPathName "C:\WINDOWS\System32\svchost.exe -k netsvcs"
```

<span data-ttu-id="a6128-113">Met deze opdracht maakt u een service met de naam TestService.</span><span class="sxs-lookup"><span data-stu-id="a6128-113">This command creates a service named TestService.</span></span>

### <span data-ttu-id="a6128-114">Voor beeld 2: een service maken die de beschrijving, het opstart type en de weergave naam bevat</span><span class="sxs-lookup"><span data-stu-id="a6128-114">Example 2: Create a service that includes description, startup type, and display name</span></span>

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

<span data-ttu-id="a6128-115">Met deze opdracht maakt u een service met de naam TestService.</span><span class="sxs-lookup"><span data-stu-id="a6128-115">This command creates a service named TestService.</span></span> <span data-ttu-id="a6128-116">Hierbij worden de para meters van gebruikt `New-Service` om een beschrijving, opstart type en weergave naam voor de nieuwe service op te geven.</span><span class="sxs-lookup"><span data-stu-id="a6128-116">It uses the parameters of `New-Service` to specify a description, startup type, and display name for the new service.</span></span>

### <span data-ttu-id="a6128-117">Voor beeld 3: de nieuwe service weer geven</span><span class="sxs-lookup"><span data-stu-id="a6128-117">Example 3: View the new service</span></span>

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

<span data-ttu-id="a6128-118">Met deze opdracht wordt `Get-CimInstance` het **Win32_Service** -object voor de nieuwe service opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a6128-118">This command uses `Get-CimInstance` to get the **Win32_Service** object for the new service.</span></span> <span data-ttu-id="a6128-119">Dit object bevat de start modus en de beschrijving van de service.</span><span class="sxs-lookup"><span data-stu-id="a6128-119">This object includes the start mode and the service description.</span></span>

### <span data-ttu-id="a6128-120">Voor beeld 4: een service verwijderen</span><span class="sxs-lookup"><span data-stu-id="a6128-120">Example 4: Delete a service</span></span>

```powershell
sc.exe delete TestService
# - or -
(Get-CimInstance -Class Win32_Service -Filter "name='TestService'").delete()
```

<span data-ttu-id="a6128-121">In dit voor beeld ziet u twee manieren om de TestService-service te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="a6128-121">This example shows two ways to delete the TestService service.</span></span> <span data-ttu-id="a6128-122">De eerste opdracht maakt gebruik van de optie verwijderen van `Sc.exe` .</span><span class="sxs-lookup"><span data-stu-id="a6128-122">The first command uses the delete option of `Sc.exe`.</span></span> <span data-ttu-id="a6128-123">Met de tweede opdracht wordt de methode **Delete** gebruikt van de **Win32_Service** -objecten die worden `Get-CimInstance` geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="a6128-123">The second command uses the **Delete** method of the **Win32_Service** objects that `Get-CimInstance` returns.</span></span>

## <span data-ttu-id="a6128-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a6128-124">PARAMETERS</span></span>

### <span data-ttu-id="a6128-125">-BinaryPathName</span><span class="sxs-lookup"><span data-stu-id="a6128-125">-BinaryPathName</span></span>

<span data-ttu-id="a6128-126">Hiermee geeft u het pad van het uitvoer bare bestand voor de service.</span><span class="sxs-lookup"><span data-stu-id="a6128-126">Specifies the path of the executable file for the service.</span></span> <span data-ttu-id="a6128-127">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="a6128-127">This parameter is required.</span></span>

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

### <span data-ttu-id="a6128-128">-Credential</span><span class="sxs-lookup"><span data-stu-id="a6128-128">-Credential</span></span>

<span data-ttu-id="a6128-129">Hiermee geeft u het account op dat door de service wordt gebruikt als [account voor aanmelding](/windows/desktop/ad/about-service-logon-accounts)bij de service.</span><span class="sxs-lookup"><span data-stu-id="a6128-129">Specifies the account used by the service as the [Service Logon Account](/windows/desktop/ad/about-service-logon-accounts).</span></span>

<span data-ttu-id="a6128-130">Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a6128-130">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="a6128-131">Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="a6128-131">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="a6128-132">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="a6128-132">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="a6128-133">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="a6128-133">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="a6128-134">-DependsOn</span><span class="sxs-lookup"><span data-stu-id="a6128-134">-DependsOn</span></span>

<span data-ttu-id="a6128-135">Hiermee geeft u de namen op van andere services waarvan de nieuwe service afhankelijk is.</span><span class="sxs-lookup"><span data-stu-id="a6128-135">Specifies the names of other services upon which the new service depends.</span></span> <span data-ttu-id="a6128-136">Als u meerdere service namen wilt opgeven, gebruikt u een komma om de namen van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="a6128-136">To enter multiple service names, use a comma to separate the names.</span></span>

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

### <span data-ttu-id="a6128-137">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a6128-137">-Description</span></span>

<span data-ttu-id="a6128-138">Hiermee geeft u een beschrijving van de service.</span><span class="sxs-lookup"><span data-stu-id="a6128-138">Specifies a description of the service.</span></span>

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

### <span data-ttu-id="a6128-139">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="a6128-139">-DisplayName</span></span>

<span data-ttu-id="a6128-140">Hiermee geeft u een weergave naam voor de service op.</span><span class="sxs-lookup"><span data-stu-id="a6128-140">Specifies a display name for the service.</span></span>

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

### <span data-ttu-id="a6128-141">-Name</span><span class="sxs-lookup"><span data-stu-id="a6128-141">-Name</span></span>

<span data-ttu-id="a6128-142">Hiermee geeft u de naam van de service.</span><span class="sxs-lookup"><span data-stu-id="a6128-142">Specifies the name of the service.</span></span>
<span data-ttu-id="a6128-143">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="a6128-143">This parameter is required.</span></span>

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

### <span data-ttu-id="a6128-144">-Opstart type</span><span class="sxs-lookup"><span data-stu-id="a6128-144">-StartupType</span></span>

<span data-ttu-id="a6128-145">Hiermee stelt u het opstart type van de service in.</span><span class="sxs-lookup"><span data-stu-id="a6128-145">Sets the startup type of the service.</span></span> <span data-ttu-id="a6128-146">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="a6128-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a6128-147">**Automatisch** : de service wordt gestart of is door het besturings systeem gestart tijdens het opstarten van het systeem.</span><span class="sxs-lookup"><span data-stu-id="a6128-147">**Automatic** - The service is started or was started by the operating system, at system start-up.</span></span>
  <span data-ttu-id="a6128-148">Als een service die automatisch wordt gestart, afhankelijk is van een hand matig gestarte service, wordt de hand matig gestarte service ook automatisch gestart bij het opstarten van het systeem.</span><span class="sxs-lookup"><span data-stu-id="a6128-148">If an automatically started service depends on a manually started service, the manually started service is also started automatically at system startup.</span></span>
- <span data-ttu-id="a6128-149">**Uitgeschakeld** : de service is uitgeschakeld en kan niet worden gestart door een gebruiker of toepassing.</span><span class="sxs-lookup"><span data-stu-id="a6128-149">**Disabled** - The service is disabled and cannot be started by a user or application.</span></span>
- <span data-ttu-id="a6128-150">**Hand matig** : de service wordt alleen hand matig gestart door een gebruiker, met behulp van service besturings beheer of door een toepassing.</span><span class="sxs-lookup"><span data-stu-id="a6128-150">**Manual** - The service is started only manually, by a user, using the Service Control Manager, or by an application.</span></span>
- <span data-ttu-id="a6128-151">**Boot** : geeft aan dat de service een apparaatstuurprogramma is dat door de System loader wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="a6128-151">**Boot** - Indicates that the service is a device driver started by the system loader.</span></span> <span data-ttu-id="a6128-152">Deze waarde is alleen geldig voor apparaatstuurprogramma's.</span><span class="sxs-lookup"><span data-stu-id="a6128-152">This value is valid only for device drivers.</span></span>
- <span data-ttu-id="a6128-153">**Systeem** : geeft aan dat de service een apparaatstuurprogramma is dat is gestart door de functie IOInitSystem ().</span><span class="sxs-lookup"><span data-stu-id="a6128-153">**System** - Indicates that the service is a device driver started by the 'IOInitSystem()' function.</span></span> <span data-ttu-id="a6128-154">Deze waarde is alleen geldig voor apparaatstuurprogramma's.</span><span class="sxs-lookup"><span data-stu-id="a6128-154">This value is valid only for device drivers.</span></span>

 <span data-ttu-id="a6128-155">De standaard waarde is **automatisch**.</span><span class="sxs-lookup"><span data-stu-id="a6128-155">The default value is **Automatic**.</span></span>

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

### <span data-ttu-id="a6128-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a6128-156">-Confirm</span></span>

<span data-ttu-id="a6128-157">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a6128-157">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a6128-158">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a6128-158">-WhatIf</span></span>

<span data-ttu-id="a6128-159">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a6128-159">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a6128-160">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a6128-160">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a6128-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a6128-161">CommonParameters</span></span>

<span data-ttu-id="a6128-162">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a6128-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a6128-163">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a6128-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a6128-164">INVOER</span><span class="sxs-lookup"><span data-stu-id="a6128-164">INPUTS</span></span>

### <span data-ttu-id="a6128-165">Geen</span><span class="sxs-lookup"><span data-stu-id="a6128-165">None</span></span>

<span data-ttu-id="a6128-166">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a6128-166">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a6128-167">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a6128-167">OUTPUTS</span></span>

### <span data-ttu-id="a6128-168">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="a6128-168">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="a6128-169">Met deze cmdlet wordt een object geretourneerd dat de nieuwe service vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="a6128-169">This cmdlet returns an object that represents the new service.</span></span>

## <span data-ttu-id="a6128-170">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a6128-170">NOTES</span></span>

<span data-ttu-id="a6128-171">Als u deze cmdlet wilt uitvoeren op Windows Vista en latere versies van het Windows-besturings systeem, start u Power shell met de optie als administrator uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="a6128-171">To run this cmdlet on Windows Vista and later versions of the Windows operating system, start PowerShell by using the Run as administrator option.</span></span>

<span data-ttu-id="a6128-172">Als u een service wilt verwijderen, gebruikt u Sc.exe of gebruikt `Get-CimInstance` u de cmdlet om het **Win32_Service** -object op te halen dat de service vertegenwoordigt en gebruikt u vervolgens de **Delete** -methode om de service te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="a6128-172">To delete a service, use Sc.exe, or use the `Get-CimInstance` cmdlet to get the **Win32_Service** object that represents the service and then use the **Delete** method to delete the service.</span></span> <span data-ttu-id="a6128-173">Het `Get-Service` geretourneerde object heeft geen verwijderings methode.</span><span class="sxs-lookup"><span data-stu-id="a6128-173">The object that `Get-Service` returns does not have a delete method.</span></span>

## <span data-ttu-id="a6128-174">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a6128-174">RELATED LINKS</span></span>

[<span data-ttu-id="a6128-175">Get-Service</span><span class="sxs-lookup"><span data-stu-id="a6128-175">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="a6128-176">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="a6128-176">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="a6128-177">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="a6128-177">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="a6128-178">Set-Service</span><span class="sxs-lookup"><span data-stu-id="a6128-178">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="a6128-179">Start-Service</span><span class="sxs-lookup"><span data-stu-id="a6128-179">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="a6128-180">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="a6128-180">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="a6128-181">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="a6128-181">Suspend-Service</span></span>](Suspend-Service.md)
