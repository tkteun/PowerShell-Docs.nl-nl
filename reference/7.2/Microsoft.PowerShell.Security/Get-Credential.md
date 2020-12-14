---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Credential
ms.openlocfilehash: 5630c4d09a2806eb117d005466d4925c1740d3a7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705473"
---
# <span data-ttu-id="9f816-102">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="9f816-102">Get-Credential</span></span>

## <span data-ttu-id="9f816-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9f816-103">SYNOPSIS</span></span>
<span data-ttu-id="9f816-104">Hiermee wordt een referentie object opgehaald op basis van een gebruikers naam en wacht woord.</span><span class="sxs-lookup"><span data-stu-id="9f816-104">Gets a credential object based on a user name and password.</span></span>

## <span data-ttu-id="9f816-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9f816-105">SYNTAX</span></span>

### <span data-ttu-id="9f816-106">Referentieset (standaard)</span><span class="sxs-lookup"><span data-stu-id="9f816-106">CredentialSet (Default)</span></span>

```
Get-Credential [[-Credential] <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="9f816-107">Berichtenset</span><span class="sxs-lookup"><span data-stu-id="9f816-107">MessageSet</span></span>

```
Get-Credential [-Message <String>] [[-UserName] <String>] [-Title <String>] [<CommonParameters>]
```

## <span data-ttu-id="9f816-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9f816-108">DESCRIPTION</span></span>

<span data-ttu-id="9f816-109">`Get-Credential`Met de cmdlet wordt een referentie object gemaakt voor een opgegeven gebruikers naam en wacht woord.</span><span class="sxs-lookup"><span data-stu-id="9f816-109">The `Get-Credential` cmdlet creates a credential object for a specified user name and password.</span></span> <span data-ttu-id="9f816-110">U kunt het referentie object in beveiligings bewerkingen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="9f816-110">You can use the credential object in security operations.</span></span>

<span data-ttu-id="9f816-111">De `Get-Credential` cmdlet vraagt de gebruiker om een wacht woord of een gebruikers naam en wacht woord.</span><span class="sxs-lookup"><span data-stu-id="9f816-111">The `Get-Credential` cmdlet prompts the user for a password or a user name and password.</span></span> <span data-ttu-id="9f816-112">U kunt de para meter **bericht** gebruiken om een aangepast bericht op te geven in de opdracht regel prompt.</span><span class="sxs-lookup"><span data-stu-id="9f816-112">You can use the **Message** parameter to specify a customized message in the command line prompt.</span></span>

## <span data-ttu-id="9f816-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9f816-113">EXAMPLES</span></span>

### <span data-ttu-id="9f816-114">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="9f816-114">Example 1</span></span>

```powershell
$c = Get-Credential
```

<span data-ttu-id="9f816-115">Met deze opdracht wordt een referentie object opgehaald en opgeslagen in de `$c` variabele.</span><span class="sxs-lookup"><span data-stu-id="9f816-115">This command gets a credential object and saves it in the `$c` variable.</span></span>

<span data-ttu-id="9f816-116">Wanneer u de opdracht invoert, wordt u gevraagd om een gebruikers naam en wacht woord op te geven.</span><span class="sxs-lookup"><span data-stu-id="9f816-116">When you enter the command, you are prompted for a user name and password.</span></span> <span data-ttu-id="9f816-117">Wanneer u de aangevraagde informatie invoert, maakt de cmdlet een **PSCredential** -object dat de referenties van de gebruiker vertegenwoordigt en opslaat in de `$c` variabele.</span><span class="sxs-lookup"><span data-stu-id="9f816-117">When you enter the requested information, the cmdlet creates a **PSCredential** object representing the credentials of the user and saves it in the `$c` variable.</span></span>

<span data-ttu-id="9f816-118">U kunt het object gebruiken als invoer voor cmdlets die gebruikers verificatie aanvragen, zoals de para meters met een **referentie** parameter.</span><span class="sxs-lookup"><span data-stu-id="9f816-118">You can use the object as input to cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span> <span data-ttu-id="9f816-119">Sommige providers die zijn geïnstalleerd met Power shell bieden echter geen ondersteuning voor de para meter **Credential** .</span><span class="sxs-lookup"><span data-stu-id="9f816-119">However, some providers that are installed with PowerShell do not support the **Credential** parameter.</span></span>

### <span data-ttu-id="9f816-120">Voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="9f816-120">Example 2</span></span>

```powershell
$c = Get-Credential
Get-CimInstance Win32_DiskDrive -ComputerName Server01 -Credential $c
```

<span data-ttu-id="9f816-121">Deze opdrachten gebruiken een referentie object dat door de `Get-Credential` cmdlet wordt geretourneerd om een gebruiker te verifiëren op een externe computer zodat deze Windows Management Instrumentation (WMI) kan gebruiken om de computer te beheren.</span><span class="sxs-lookup"><span data-stu-id="9f816-121">These commands use a credential object that the `Get-Credential` cmdlet returns to authenticate a user on a remote computer so they can use Windows Management Instrumentation (WMI) to manage the computer.</span></span>

<span data-ttu-id="9f816-122">Met de eerste opdracht wordt een referentie object opgehaald en opgeslagen in de `$c` variabele.</span><span class="sxs-lookup"><span data-stu-id="9f816-122">The first command gets a credential object and saves it in the `$c` variable.</span></span> <span data-ttu-id="9f816-123">Met de tweede opdracht wordt het referentie object in een `Get-CimInstance` opdracht gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9f816-123">The second command uses the credential object in a `Get-CimInstance` command.</span></span> <span data-ttu-id="9f816-124">Met deze opdracht wordt informatie opgehaald over de schijf stations op de Server01-computer.</span><span class="sxs-lookup"><span data-stu-id="9f816-124">This command gets information about the disk drives on the Server01 computer.</span></span>

### <span data-ttu-id="9f816-125">Voorbeeld 3</span><span class="sxs-lookup"><span data-stu-id="9f816-125">Example 3</span></span>

```powershell
Get-CimInstance Win32_BIOS -ComputerName Server01 -Credential (Get-Credential -Credential Domain01\User01)
```

<span data-ttu-id="9f816-126">Met deze opdracht wordt aangegeven hoe u een `Get-Credential` opdracht in een opdracht opneemt  `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="9f816-126">This command shows how to include a `Get-Credential` command in a  `Get-CimInstance` command.</span></span>

<span data-ttu-id="9f816-127">Met deze opdracht wordt de `Get-CimInstance` cmdlet gebruikt om informatie over het BIOS op de Server01-computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="9f816-127">This command uses the `Get-CimInstance` cmdlet to get information about the BIOS on the Server01 computer.</span></span> <span data-ttu-id="9f816-128">De para meter **Credential** wordt gebruikt voor het verifiëren van de gebruiker, Domain01\User01 en een `Get-Credential` opdracht als de waarde van de para meter **Credential** .</span><span class="sxs-lookup"><span data-stu-id="9f816-128">It uses the **Credential** parameter to authenticate the user, Domain01\User01, and a `Get-Credential` command as the value of the **Credential** parameter.</span></span>

### <span data-ttu-id="9f816-129">Voorbeeld 4</span><span class="sxs-lookup"><span data-stu-id="9f816-129">Example 4</span></span>

```powershell
$c = Get-Credential -credential User01
$c.Username
User01
```

<span data-ttu-id="9f816-130">In dit voor beeld wordt een referentie gemaakt die een gebruikers naam zonder domein naam bevat.</span><span class="sxs-lookup"><span data-stu-id="9f816-130">This example creates a credential that includes a user name without a domain name.</span></span>

<span data-ttu-id="9f816-131">Met de eerste opdracht wordt een referentie opgehaald met de gebruikers naam gebruiker01 en opgeslagen in de `$c` variabele.</span><span class="sxs-lookup"><span data-stu-id="9f816-131">The first command gets a credential with the user name User01 and stores it in the `$c` variable.</span></span>
<span data-ttu-id="9f816-132">Met de tweede opdracht wordt de waarde van de eigenschap **username** van het resulterende referentie object weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9f816-132">The second command displays the value of the **Username** property of the resulting credential object.</span></span>

### <span data-ttu-id="9f816-133">Voorbeeld 5</span><span class="sxs-lookup"><span data-stu-id="9f816-133">Example 5</span></span>

```powershell
$Credential = $host.ui.PromptForCredential("Need credentials", "Please enter your user name and password.", "", "NetBiosUserName")
```

<span data-ttu-id="9f816-134">Met deze opdracht wordt de methode **PromptForCredential** gebruikt om de gebruiker te vragen naar de gebruikers naam en het wacht woord.</span><span class="sxs-lookup"><span data-stu-id="9f816-134">This command uses the **PromptForCredential** method to prompt the user for their user name and password.</span></span> <span data-ttu-id="9f816-135">Met de opdracht worden de resulterende referenties in de `$Credential` variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="9f816-135">The command saves the resulting credentials in the `$Credential` variable.</span></span>

<span data-ttu-id="9f816-136">De methode **PromptForCredential** is een alternatief voor het gebruik van de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f816-136">The **PromptForCredential** method is an alternative to using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="9f816-137">Wanneer u **PromptForCredential** gebruikt, kunt u de bijschriften, berichten en gebruikers namen opgeven die in de prompt worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9f816-137">When you use **PromptForCredential**, you can specify the caption, messages, and user name that appear in the prompt.</span></span>

<span data-ttu-id="9f816-138">Zie de [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) -documentatie in de SDK voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9f816-138">For more information, see the [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) documentation in the SDK.</span></span>

### <span data-ttu-id="9f816-139">Voorbeeld 6</span><span class="sxs-lookup"><span data-stu-id="9f816-139">Example 6</span></span>

<span data-ttu-id="9f816-140">In dit voor beeld ziet u hoe u een referentie object maakt dat identiek is aan het object dat `Get-Credential` wordt geretourneerd zonder dat de gebruiker om toestemming wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="9f816-140">This example shows how to create a credential object that is identical to the object that `Get-Credential` returns without prompting the user.</span></span> <span data-ttu-id="9f816-141">Voor deze methode is een wacht woord met tekst zonder opmaak vereist, wat in sommige ondernemingen de beveiligings normen kan schenden.</span><span class="sxs-lookup"><span data-stu-id="9f816-141">This method requires a plain text password, which might violate the security standards in some enterprises.</span></span>

```powershell
$User = "Domain01\User01"
$PWord = ConvertTo-SecureString -String "P@sSwOrd" -AsPlainText -Force
$Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $User, $PWord
```

<span data-ttu-id="9f816-142">Met de eerste opdracht slaat u de naam van het gebruikers account op in de `$User` para meter.</span><span class="sxs-lookup"><span data-stu-id="9f816-142">The first command saves the user account name in the `$User` parameter.</span></span> <span data-ttu-id="9f816-143">De waarde moet de indeling "Domein\gebruiker" of "ComputerName\User" hebben.</span><span class="sxs-lookup"><span data-stu-id="9f816-143">The value must have the "Domain\User" or "ComputerName\User" format.</span></span>

<span data-ttu-id="9f816-144">Met de tweede opdracht wordt de `ConvertTo-SecureString` cmdlet gebruikt om een veilige teken reeks te maken van een wacht woord voor onbewerkte tekst.</span><span class="sxs-lookup"><span data-stu-id="9f816-144">The second command uses the `ConvertTo-SecureString` cmdlet to create a secure string from a plain text password.</span></span> <span data-ttu-id="9f816-145">De opdracht gebruikt de para meter **AsPlainText** om aan te geven dat de teken reeks tekst zonder opmaak is en de para meter **Force** om te bevestigen dat u de Risico's van het gebruik van onbewerkte tekst begrijpt.</span><span class="sxs-lookup"><span data-stu-id="9f816-145">The command uses the **AsPlainText** parameter to indicate that the string is plain text and the **Force** parameter to confirm that you understand the risks of using plain text.</span></span>

<span data-ttu-id="9f816-146">De derde opdracht gebruikt de `New-Object` cmdlet om een **PSCredential** -object te maken op basis van de waarden in de `$User` `$PWord` variabelen en.</span><span class="sxs-lookup"><span data-stu-id="9f816-146">The third command uses the `New-Object` cmdlet to create a **PSCredential** object from the values in the `$User` and `$PWord` variables.</span></span>

### <span data-ttu-id="9f816-147">Voorbeeld 7</span><span class="sxs-lookup"><span data-stu-id="9f816-147">Example 7</span></span>

```powershell
Get-Credential -Message "Credential are required for access to the \\Server1\Scripts file share." -User Server01\PowerUser
```

```Output
PowerShell Credential Request
Credential are required for access to the \\Server1\Scripts file share.
Password for user Server01\PowerUser:
```

<span data-ttu-id="9f816-148">Met deze opdracht worden de para meters **bericht** en **gebruikers naam** van de `Get-Credential` cmdlet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9f816-148">This command uses the **Message** and **UserName** parameters of the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="9f816-149">Deze opdracht indeling is ontworpen voor gedeelde scripts en functies.</span><span class="sxs-lookup"><span data-stu-id="9f816-149">This command format is designed for shared scripts and functions.</span></span> <span data-ttu-id="9f816-150">In dit geval geeft het bericht aan de gebruiker door dat er referenties nodig zijn en zorgt u ervoor dat de aanvraag betrouwbaar is.</span><span class="sxs-lookup"><span data-stu-id="9f816-150">In this case, the message tells the user why credentials are needed and gives them confidence that the request is legitimate.</span></span>

### <span data-ttu-id="9f816-151">Voorbeeld 8</span><span class="sxs-lookup"><span data-stu-id="9f816-151">Example 8</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Get-Credential Domain01\User02}
```

```Output
PowerShell Credential Request : PowerShell Credential Request
Warning: This credential is being requested by a script or application on the SERVER01 remote computer. Enter your credentials only if you
 trust the remote computer and the application or script requesting it.

Enter your credentials.
Password for user Domain01\User02: ***************

PSComputerName     : Server01
RunspaceId         : 422bdf52-9886-4ada-ab2f-130497c6777f
PSShowComputerName : True
UserName           : Domain01\User01
Password           : System.Security.SecureString
```

<span data-ttu-id="9f816-152">Met deze opdracht wordt een referentie opgehaald van de externe computer Server01.</span><span class="sxs-lookup"><span data-stu-id="9f816-152">This command gets a credential from the Server01 remote computer.</span></span> <span data-ttu-id="9f816-153">De opdracht gebruikt de `Invoke-Command` cmdlet om een opdracht uit te voeren `Get-Credential` op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="9f816-153">The command uses the `Invoke-Command` cmdlet to run a `Get-Credential` command on the remote computer.</span></span> <span data-ttu-id="9f816-154">De uitvoer toont het externe beveiligings bericht dat is `Get-Credential` opgenomen in de verificatie prompt.</span><span class="sxs-lookup"><span data-stu-id="9f816-154">The output shows the remote security message that `Get-Credential` includes in the authentication prompt.</span></span>

## <span data-ttu-id="9f816-155">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9f816-155">PARAMETERS</span></span>

### <span data-ttu-id="9f816-156">-Credential</span><span class="sxs-lookup"><span data-stu-id="9f816-156">-Credential</span></span>

<span data-ttu-id="9f816-157">Hiermee geeft u een gebruikers naam op voor de referentie, zoals **gebruiker01** of **Domain01\User01**.</span><span class="sxs-lookup"><span data-stu-id="9f816-157">Specifies a user name for the credential, such as **User01** or **Domain01\User01**.</span></span> <span data-ttu-id="9f816-158">De parameter naam, `-Credential` , is optioneel.</span><span class="sxs-lookup"><span data-stu-id="9f816-158">The parameter name, `-Credential`, is optional.</span></span>

<span data-ttu-id="9f816-159">Wanneer u de opdracht verzendt en een gebruikers naam opgeeft, wordt u gevraagd een wacht woord op te geven.</span><span class="sxs-lookup"><span data-stu-id="9f816-159">When you submit the command and specify a user name, you're prompted for a password.</span></span> <span data-ttu-id="9f816-160">Als u deze para meter weglaat, wordt u gevraagd om een gebruikers naam en wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="9f816-160">If you omit this parameter, you're prompted for a user name and a password.</span></span>

<span data-ttu-id="9f816-161">Als u vanaf Power Shell 3,0 een gebruikers naam zonder domein opgeeft, wordt `Get-Credential` er niet langer een back slash voor de naam ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="9f816-161">Starting in PowerShell 3.0, if you enter a user name without a domain, `Get-Credential` no longer inserts a backslash before the name.</span></span>

<span data-ttu-id="9f816-162">Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="9f816-162">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="9f816-163">Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.</span><span class="sxs-lookup"><span data-stu-id="9f816-163">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f816-164">-Bericht</span><span class="sxs-lookup"><span data-stu-id="9f816-164">-Message</span></span>

<span data-ttu-id="9f816-165">Hiermee geeft u een bericht dat wordt weer gegeven in de verificatie prompt.</span><span class="sxs-lookup"><span data-stu-id="9f816-165">Specifies a message that appears in the authentication prompt.</span></span> <span data-ttu-id="9f816-166">Deze para meter is ontworpen voor gebruik in een functie of script.</span><span class="sxs-lookup"><span data-stu-id="9f816-166">This parameter is designed for use in a function or script.</span></span> <span data-ttu-id="9f816-167">U kunt het bericht gebruiken om uitleg te geven over de gebruiker waarom u referenties aanvraagt en hoe deze worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9f816-167">You can use the message to explain to the user why you are requesting credentials and how they will be used.</span></span>

<span data-ttu-id="9f816-168">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9f816-168">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f816-169">-Titel</span><span class="sxs-lookup"><span data-stu-id="9f816-169">-Title</span></span>

<span data-ttu-id="9f816-170">Hiermee stelt u de tekst van de titel regel voor de verificatie prompt in de-console.</span><span class="sxs-lookup"><span data-stu-id="9f816-170">Sets the text of the title line for the authentication prompt in the console.</span></span>

<span data-ttu-id="9f816-171">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="9f816-171">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f816-172">-GebruikersNaam</span><span class="sxs-lookup"><span data-stu-id="9f816-172">-UserName</span></span>

<span data-ttu-id="9f816-173">Hiermee geeft u een gebruikers naam op.</span><span class="sxs-lookup"><span data-stu-id="9f816-173">Specifies a user name.</span></span> <span data-ttu-id="9f816-174">De verificatie prompt vraagt een wacht woord op voor de gebruikers naam.</span><span class="sxs-lookup"><span data-stu-id="9f816-174">The authentication prompt requests a password for the user name.</span></span> <span data-ttu-id="9f816-175">De gebruikers naam is standaard leeg en de verificatie prompt vraagt om een gebruikers naam en wacht woord.</span><span class="sxs-lookup"><span data-stu-id="9f816-175">By default, the user name is blank and the authentication prompt requests both a user name and password.</span></span>

<span data-ttu-id="9f816-176">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9f816-176">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: 1
Default value: None (blank)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f816-177">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9f816-177">CommonParameters</span></span>

<span data-ttu-id="9f816-178">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9f816-178">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9f816-179">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9f816-179">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9f816-180">INVOER</span><span class="sxs-lookup"><span data-stu-id="9f816-180">INPUTS</span></span>

### <span data-ttu-id="9f816-181">Geen</span><span class="sxs-lookup"><span data-stu-id="9f816-181">None</span></span>

<span data-ttu-id="9f816-182">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f816-182">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="9f816-183">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9f816-183">OUTPUTS</span></span>

### <span data-ttu-id="9f816-184">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="9f816-184">System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="9f816-185">`Get-Credential` retourneert een referentie object.</span><span class="sxs-lookup"><span data-stu-id="9f816-185">`Get-Credential` returns a credential object.</span></span>

## <span data-ttu-id="9f816-186">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9f816-186">NOTES</span></span>

<span data-ttu-id="9f816-187">U kunt het **PSCredential** -object gebruiken dat `Get-Credential` maakt in cmdlets die gebruikers verificatie aanvragen, zoals de para meters met een **referentie** parameter.</span><span class="sxs-lookup"><span data-stu-id="9f816-187">You can use the **PSCredential** object that `Get-Credential` creates in cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span>

<span data-ttu-id="9f816-188">De **referentie** parameter wordt niet ondersteund door alle providers die met Power shell zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9f816-188">The **Credential** parameter is not supported by all providers that are installed with PowerShell.</span></span>
<span data-ttu-id="9f816-189">Vanaf Power Shell 3,0 wordt het ondersteund op Select-cmdlets, zoals de `Get-Content` `New-PSDrive` cmdlets en.</span><span class="sxs-lookup"><span data-stu-id="9f816-189">Beginning in PowerShell 3.0, it is supported on select cmdlets, such as the `Get-Content` and `New-PSDrive` cmdlets.</span></span>

## <span data-ttu-id="9f816-190">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9f816-190">RELATED LINKS</span></span>

[<span data-ttu-id="9f816-191">PromptForCredential</span><span class="sxs-lookup"><span data-stu-id="9f816-191">PromptForCredential</span></span>](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential)
