---
title: Referentie ondersteuning toevoegen aan Power shell-functies
description: Referentie parameters toevoegen aan uw Power shell-scripts,-functies en-cmdlets.
ms.date: 10/29/2020
ms.custom: contributor-JoshDuffney
ms.openlocfilehash: fb85d47121dc106ae04742254f418e2c727f6157
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143179"
---
# <a name="add-credential-support-to-powershell-functions"></a><span data-ttu-id="1ce91-103">Referentie ondersteuning toevoegen aan Power shell-functies</span><span class="sxs-lookup"><span data-stu-id="1ce91-103">Add Credential support to PowerShell functions</span></span>

> [!NOTE]
> <span data-ttu-id="1ce91-104">De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@joshduffney][] .</span><span class="sxs-lookup"><span data-stu-id="1ce91-104">The [original version][] of this article appeared on the blog written by [@joshduffney][].</span></span> <span data-ttu-id="1ce91-105">Dit artikel is bewerkt voor opname op deze site.</span><span class="sxs-lookup"><span data-stu-id="1ce91-105">This article has been edited for inclusion on this site.</span></span> <span data-ttu-id="1ce91-106">De Power shell-team dank Josh voor het delen van deze inhoud met ons.</span><span class="sxs-lookup"><span data-stu-id="1ce91-106">The PowerShell team thanks Josh for sharing this content with us.</span></span> <span data-ttu-id="1ce91-107">Raadpleeg zijn blog op [duffney.io][].</span><span class="sxs-lookup"><span data-stu-id="1ce91-107">Please check out his blog at [duffney.io][].</span></span>

<span data-ttu-id="1ce91-108">In dit artikel leest u hoe u referentie parameters kunt toevoegen aan Power shell-functies en waarom u dat wilt.</span><span class="sxs-lookup"><span data-stu-id="1ce91-108">This article shows you how to add credential parameters to PowerShell functions and why you'd want to.</span></span> <span data-ttu-id="1ce91-109">Een referentie parameter is het toestaan van de functie of cmdlet als een andere gebruiker uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1ce91-109">A credential parameter is to allow you to run the function or cmdlet as a different user.</span></span> <span data-ttu-id="1ce91-110">Het meest voorkomende gebruik is het uitvoeren van de functie of cmdlet als een gebruikers account met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="1ce91-110">The most common use is to run the function or cmdlet as an elevated user account.</span></span>

<span data-ttu-id="1ce91-111">De cmdlet heeft bijvoorbeeld de `New-ADUser` para meter **Credential** , die u domein beheerders referenties kunt opgeven voor het maken van een account in een domein.</span><span class="sxs-lookup"><span data-stu-id="1ce91-111">For example, the cmdlet `New-ADUser` has a **Credential** parameter, which you could provide domain admin credentials to create an account in a domain.</span></span> <span data-ttu-id="1ce91-112">Ervan uitgaande dat uw normale account dat de Power shell-sessie uitvoert, deze toegang niet al heeft.</span><span class="sxs-lookup"><span data-stu-id="1ce91-112">Assuming your normal account running the PowerShell session doesn't have that access already.</span></span>

## <a name="creating-credential-object"></a><span data-ttu-id="1ce91-113">Referentie object maken</span><span class="sxs-lookup"><span data-stu-id="1ce91-113">Creating credential object</span></span>

<span data-ttu-id="1ce91-114">Het [PSCredential][] -object vertegenwoordigt een set beveiligings referenties, zoals een gebruikers naam en wacht woord.</span><span class="sxs-lookup"><span data-stu-id="1ce91-114">The [PSCredential][] object represents a set of security credentials such as a user name and password.</span></span> <span data-ttu-id="1ce91-115">Het object kan worden door gegeven als een para meter voor een functie die wordt uitgevoerd als het gebruikers account in dat referentie object.</span><span class="sxs-lookup"><span data-stu-id="1ce91-115">The object can be passed as a parameter to a function that runs as the user account in that credential object.</span></span> <span data-ttu-id="1ce91-116">Er zijn een paar manieren waarop u een referentie object kunt maken.</span><span class="sxs-lookup"><span data-stu-id="1ce91-116">There are a few ways that you can create a credential object.</span></span> <span data-ttu-id="1ce91-117">De eerste manier om een referentie object te maken, is met behulp van de Power shell-cmdlet `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="1ce91-117">The first way to create a credential object is to use the PowerShell cmdlet `Get-Credential`.</span></span> <span data-ttu-id="1ce91-118">Wanneer u zonder para meters uitvoert, wordt u gevraagd om een gebruikers naam en wacht woord.</span><span class="sxs-lookup"><span data-stu-id="1ce91-118">When you run without parameters, it prompts you for a username and password.</span></span> <span data-ttu-id="1ce91-119">U kunt de cmdlet ook aanroepen met enkele optionele para meters.</span><span class="sxs-lookup"><span data-stu-id="1ce91-119">Or you can call the cmdlet with some optional parameters.</span></span>

<span data-ttu-id="1ce91-120">Als u de domein naam en gebruikers naam van tevoren wilt opgeven, kunt u de para meters **referentie** of **gebruikers naam** gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1ce91-120">To specify the domain name and username ahead of time you can use either the **Credential** or **UserName** parameters.</span></span> <span data-ttu-id="1ce91-121">Wanneer u de para meter **username** gebruikt, moet u ook een **bericht** waarde opgeven.</span><span class="sxs-lookup"><span data-stu-id="1ce91-121">When you use the **UserName** parameter, you're also required to provide a **Message** value.</span></span> <span data-ttu-id="1ce91-122">De volgende code laat zien hoe u de cmdlet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1ce91-122">The code below demonstrates using the cmdlet.</span></span> <span data-ttu-id="1ce91-123">U kunt het referentie object ook opslaan in een variabele, zodat u de referentie meerdere keren kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1ce91-123">You can also store the credential object in a variable so that you can use the credential multiple times.</span></span> <span data-ttu-id="1ce91-124">In het onderstaande voor beeld wordt het referentie object opgeslagen in de variabele `$Cred` .</span><span class="sxs-lookup"><span data-stu-id="1ce91-124">In the example below, the credential object is stored in the variable `$Cred`.</span></span>

```powershell
$Cred = Get-Credential
$Cred = Get-Credential -Credential domain\user
$Cred = Get-Credential -UserName domain\user -Message 'Enter Password'
```

<span data-ttu-id="1ce91-125">Soms is het niet mogelijk om de interactieve methode voor het maken van referentie objecten te gebruiken die in het vorige voor beeld worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="1ce91-125">Sometimes, you can't use the interactive method of creating credential objects shown in the previous example.</span></span> <span data-ttu-id="1ce91-126">Voor de meeste hulpprogram ma's voor automatisering is een niet-interactieve methode vereist.</span><span class="sxs-lookup"><span data-stu-id="1ce91-126">Most automation tools require a non-interactive method.</span></span> <span data-ttu-id="1ce91-127">Als u een referentie wilt maken zonder tussen komst van de gebruiker, maakt u een veilige teken reeks met het wacht woord.</span><span class="sxs-lookup"><span data-stu-id="1ce91-127">To create a credential without user interaction, create a secure string containing the password.</span></span> <span data-ttu-id="1ce91-128">Geef vervolgens de beveiligde teken reeks en gebruikers naam door aan de- `System.Management.Automation.PSCredential()` methode.</span><span class="sxs-lookup"><span data-stu-id="1ce91-128">Then pass the secure string and user name to the `System.Management.Automation.PSCredential()` method.</span></span>

<span data-ttu-id="1ce91-129">Gebruik de volgende opdracht om een beveiligde teken reeks te maken met het wacht woord:</span><span class="sxs-lookup"><span data-stu-id="1ce91-129">Use the following command to create a secure string containing the password:</span></span>

```powershell
ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
```

<span data-ttu-id="1ce91-130">Zowel de para meters **AsPlainText** als **Force** zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="1ce91-130">Both the **AsPlainText** and **Force** parameters are required.</span></span> <span data-ttu-id="1ce91-131">Zonder deze para meters ontvangt u een bericht waarin wordt gemeld dat u geen tekst zonder opmaak in een beveiligde teken reeks hoeft door te geven.</span><span class="sxs-lookup"><span data-stu-id="1ce91-131">Without those parameters, you receive a message warning that you shouldn't pass plain text into a secure string.</span></span> <span data-ttu-id="1ce91-132">Power shell retourneert deze waarschuwing omdat het wacht woord voor onbewerkte tekst in verschillende logboeken wordt vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="1ce91-132">PowerShell returns this warning because the plain text password gets recorded in various logs.</span></span> <span data-ttu-id="1ce91-133">Zodra u een beveiligde teken reeks hebt gemaakt, moet u deze door geven aan de `PSCredential()` methode voor het maken van het referentie object.</span><span class="sxs-lookup"><span data-stu-id="1ce91-133">Once you have a secure string created, you need to pass it to the `PSCredential()` method to create the credential object.</span></span> <span data-ttu-id="1ce91-134">In het volgende voor beeld bevat de variabele de `$password` beveiligde teken reeks `$Cred` bevat het referentie object.</span><span class="sxs-lookup"><span data-stu-id="1ce91-134">In the following example, the variable `$password` contains the secure string `$Cred` contains the credential object.</span></span>

```powershell
$password = ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("username", $password)
```

<span data-ttu-id="1ce91-135">Nu u weet hoe u referentie objecten maakt, kunt u referentie parameters toevoegen aan uw Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="1ce91-135">Now that you know how to create credential objects, you can add credential parameters to your PowerShell functions.</span></span>

## <a name="adding-a-credential-parameter"></a><span data-ttu-id="1ce91-136">Een referentie parameter toevoegen</span><span class="sxs-lookup"><span data-stu-id="1ce91-136">Adding a Credential Parameter</span></span>

<span data-ttu-id="1ce91-137">Net als bij andere para meters, kunt u beginnen met het toevoegen in het `param` blok van uw functie.</span><span class="sxs-lookup"><span data-stu-id="1ce91-137">Just like any other parameter, you start off by adding it in the `param` block of your function.</span></span>
<span data-ttu-id="1ce91-138">Het is raadzaam om de para meter een naam te benoemen, `$Credential` omdat dat de bestaande Power shell-cmdlets gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1ce91-138">It's recommended that you name the parameter `$Credential` because that's what existing PowerShell cmdlets use.</span></span> <span data-ttu-id="1ce91-139">Het type van de para meter moet zijn `[System.Management.Automation.PSCredential]` .</span><span class="sxs-lookup"><span data-stu-id="1ce91-139">The type of the parameter should be `[System.Management.Automation.PSCredential]`.</span></span>

<span data-ttu-id="1ce91-140">In het volgende voor beeld ziet u het parameter blok voor een functie met de naam `Get-Something` .</span><span class="sxs-lookup"><span data-stu-id="1ce91-140">The following example shows the parameter block for a function called `Get-Something`.</span></span> <span data-ttu-id="1ce91-141">Er zijn twee para meters: `$Name` en `$Credential` .</span><span class="sxs-lookup"><span data-stu-id="1ce91-141">It has two parameters: `$Name` and `$Credential`.</span></span>

```powershell
function Get-Something {
    param(
        $Name,
        [System.Management.Automation.PSCredential]$Credential
    )
```

<span data-ttu-id="1ce91-142">De code in dit voor beeld is voldoende om een para meter voor een werk referentie te hebben, maar er zijn een aantal dingen die u kunt toevoegen om het betrouwbaarder te maken.</span><span class="sxs-lookup"><span data-stu-id="1ce91-142">The code in this example is enough to have a working credential parameter, however there are a few things you can add to make it more robust.</span></span>

- <span data-ttu-id="1ce91-143">Voeg het `[ValidateNotNull()]` validatie kenmerk toe om te controleren of de waarde wordt door gegeven aan de **referentie** .</span><span class="sxs-lookup"><span data-stu-id="1ce91-143">Add the `[ValidateNotNull()]` validation attribute to check that the value being passed to **Credential** .</span></span> <span data-ttu-id="1ce91-144">Als de waarde van de para meter null is, voor komt dit kenmerk dat de functie wordt uitgevoerd met ongeldige referenties.</span><span class="sxs-lookup"><span data-stu-id="1ce91-144">If the parameter value is null, this attribute prevents the function from executing with invalid credentials.</span></span>

- <span data-ttu-id="1ce91-145">Toevoegen `[System.Management.Automation.Credential()]` .</span><span class="sxs-lookup"><span data-stu-id="1ce91-145">Add `[System.Management.Automation.Credential()]`.</span></span> <span data-ttu-id="1ce91-146">Zo kunt u een gebruikers naam door geven als een teken reeks en een interactieve prompt voor het wacht woord hebben.</span><span class="sxs-lookup"><span data-stu-id="1ce91-146">This allows you to pass in a username as a string and have an interactive prompt for the password.</span></span>

- <span data-ttu-id="1ce91-147">Stel een standaard waarde voor de `$Credential` para meter in op `[System.Management.Automation.PSCredential]::Empty` .</span><span class="sxs-lookup"><span data-stu-id="1ce91-147">Set a default value for the `$Credential` parameter to `[System.Management.Automation.PSCredential]::Empty`.</span></span> <span data-ttu-id="1ce91-148">Uw functie kunt u dit object door geven `$Credential` aan bestaande Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="1ce91-148">Your function you might be passing this `$Credential` object to existing PowerShell cmdlets.</span></span> <span data-ttu-id="1ce91-149">Als u een null-waarde opgeeft voor de cmdlet die in de functie wordt aangeroepen, treedt er een fout op.</span><span class="sxs-lookup"><span data-stu-id="1ce91-149">Providing a null value to the cmdlet called inside your function causes an error.</span></span> <span data-ttu-id="1ce91-150">Deze fout wordt voor komen door een leeg referentie object op te geven.</span><span class="sxs-lookup"><span data-stu-id="1ce91-150">Providing an empty credential object avoids this error.</span></span>

> [!TIP]
> <span data-ttu-id="1ce91-151">Sommige cmdlets die een referentie parameter accepteren, bieden geen ondersteuning `[System.Management.Automation.PSCredential]::Empty` .</span><span class="sxs-lookup"><span data-stu-id="1ce91-151">Some cmdlets that accept a credential parameter do not support `[System.Management.Automation.PSCredential]::Empty` as they should.</span></span> <span data-ttu-id="1ce91-152">Zie de sectie [omgaan met verouderde cmdlets](#dealing-with-legacy-cmdlets) voor een tijdelijke oplossing.</span><span class="sxs-lookup"><span data-stu-id="1ce91-152">See the [Dealing with Legacy Cmdlets](#dealing-with-legacy-cmdlets) section for a workaround.</span></span>

## <a name="using-credential-parameters"></a><span data-ttu-id="1ce91-153">Referentie parameters gebruiken</span><span class="sxs-lookup"><span data-stu-id="1ce91-153">Using credential parameters</span></span>

<span data-ttu-id="1ce91-154">In het volgende voor beeld ziet u hoe u referentie parameters kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1ce91-154">The following example demonstrates how to use credential parameters.</span></span> <span data-ttu-id="1ce91-155">In dit voor beeld ziet u een functie `Set-RemoteRegistryValue` met de naam, die buiten [het inpests Book][]valt.</span><span class="sxs-lookup"><span data-stu-id="1ce91-155">This example shows a function called `Set-RemoteRegistryValue`, which is out of [The Pester Book][].</span></span> <span data-ttu-id="1ce91-156">Deze functie definieert de referentie parameter met behulp van de technieken die in de vorige sectie worden beschreven.</span><span class="sxs-lookup"><span data-stu-id="1ce91-156">This function defines the credential parameter using the techniques describe in the previous section.</span></span> <span data-ttu-id="1ce91-157">De functie aanroepen `Invoke-Command` met behulp van de `$Credential` variabele die door de functie is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="1ce91-157">The function calls `Invoke-Command` using the `$Credential` variable created by the function.</span></span> <span data-ttu-id="1ce91-158">Hiermee kunt u de gebruiker wijzigen die wordt uitgevoerd `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="1ce91-158">This allows you to change the user who's running `Invoke-Command`.</span></span> <span data-ttu-id="1ce91-159">Omdat de standaard waarde van `$Credential` is een lege referentie, kan de functie worden uitgevoerd zonder referenties op te geven.</span><span class="sxs-lookup"><span data-stu-id="1ce91-159">Because the default value of `$Credential` is an empty credential, the function can run without providing credentials.</span></span>

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )
        $null = Invoke-Command -ComputerName $ComputerName -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } -Credential $Credential
}
```

<span data-ttu-id="1ce91-160">In de volgende secties worden verschillende methoden voor het opgeven van referenties weer gegeven `Set-RemoteRegistryValue` .</span><span class="sxs-lookup"><span data-stu-id="1ce91-160">The following sections show different methods of providing credentials to `Set-RemoteRegistryValue`.</span></span>

### <a name="prompting-for-credentials"></a><span data-ttu-id="1ce91-161">Vragen om referenties</span><span class="sxs-lookup"><span data-stu-id="1ce91-161">Prompting for credentials</span></span>

<span data-ttu-id="1ce91-162">`Get-Credential`Als u tussen haakjes tijdens runtime gebruikt, wordt `()` de `Get-credential` om eerst uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1ce91-162">Using `Get-Credential` in parentheses `()` at run time causes the `Get-credential` to run first.</span></span> <span data-ttu-id="1ce91-163">U wordt gevraagd om een gebruikers naam en wacht woord.</span><span class="sxs-lookup"><span data-stu-id="1ce91-163">You are prompted for a username and password.</span></span> <span data-ttu-id="1ce91-164">U kunt de **referenties** of de para meters van de **gebruikers naam** van gebruiken `Get-credential` om de gebruikers naam en het domein vooraf in te vullen.</span><span class="sxs-lookup"><span data-stu-id="1ce91-164">You could use the **Credential** or **UserName** parameters of `Get-credential` to pre-populate the username and domain.</span></span> <span data-ttu-id="1ce91-165">In het volgende voor beeld wordt een techniek gebruikt met de naam splatting om para meters door te geven aan de `Set-RemoteRegistryValue` functie.</span><span class="sxs-lookup"><span data-stu-id="1ce91-165">The following example uses a technique called splatting to pass parameters to the `Set-RemoteRegistryValue` function.</span></span> <span data-ttu-id="1ce91-166">Raadpleeg het [about_Splatting][] -artikel voor meer informatie over splatting.</span><span class="sxs-lookup"><span data-stu-id="1ce91-166">For more information about splatting, check out the [about_Splatting][] article.</span></span>

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential (Get-Credential)
```

![Een referentie tijdens runtime ophalen](./media/add-credentials-to-powershell-functions/GetCredAtRunTime.gif)

<span data-ttu-id="1ce91-168">Gebruiken is zeer `(Get-Credential)` omslachtig.</span><span class="sxs-lookup"><span data-stu-id="1ce91-168">Using `(Get-Credential)` seems cumbersome.</span></span> <span data-ttu-id="1ce91-169">Normaal gesp roken wordt de cmdlet automatisch gevraagd naar het wacht woord wanneer u de para meter **Credential** gebruikt met alleen een gebruikers naam.</span><span class="sxs-lookup"><span data-stu-id="1ce91-169">Normally, when you use the **Credential** parameter with only a username, the cmdlet automatically prompts for the password.</span></span> <span data-ttu-id="1ce91-170">`[System.Management.Automation.Credential()]`Dit gedrag kan worden ingeschakeld met het kenmerk.</span><span class="sxs-lookup"><span data-stu-id="1ce91-170">The `[System.Management.Automation.Credential()]` attribute enables this behavior.</span></span>

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential duffney
```

![Vragen om referenties](./media/add-credentials-to-powershell-functions/GetCredsPrompt.gif)

> [!NOTE]
> <span data-ttu-id="1ce91-172">In deze voor beelden wordt ervan uitgegaan dat u de **webserver** functies van Windows hebt geïnstalleerd om de weer gegeven register waarde in te stellen.</span><span class="sxs-lookup"><span data-stu-id="1ce91-172">To set the registry value shown, these examples assume you have the **Web Server** features of Windows installed.</span></span> <span data-ttu-id="1ce91-173">Voer uit `Install-WindowsFeature Web-Server` en `Install-WindowsFeature web-mgmt-tools` indien nodig.</span><span class="sxs-lookup"><span data-stu-id="1ce91-173">Run `Install-WindowsFeature Web-Server` and `Install-WindowsFeature web-mgmt-tools` if required.</span></span>

### <a name="provide-credentials-in-a-variable"></a><span data-ttu-id="1ce91-174">Referenties opgeven in een variabele</span><span class="sxs-lookup"><span data-stu-id="1ce91-174">Provide credentials in a variable</span></span>

<span data-ttu-id="1ce91-175">U kunt ook een referentie variabele vooraf invullen en deze door geven aan de para meter **Credential** van de `Set-RemoteRegistryValue` functie.</span><span class="sxs-lookup"><span data-stu-id="1ce91-175">You can also populate a credential variable ahead of time and pass it to the **Credential** parameter of `Set-RemoteRegistryValue` function.</span></span> <span data-ttu-id="1ce91-176">Gebruik deze methode met doorlopende hulpprogram ma's voor integratie/doorlopende implementatie (CI/CD) zoals Jenkins, TeamCity en Octopus Deploy.</span><span class="sxs-lookup"><span data-stu-id="1ce91-176">Use this method with Continuous Integration / Continuous Deployment (CI/CD) tools such as Jenkins, TeamCity, and Octopus Deploy.</span></span> <span data-ttu-id="1ce91-177">Voor een voor beeld van het gebruik van Jenkins raadpleegt u het blog bericht van Hodge [met Jenkins en Power shell in Windows-deel 2][].</span><span class="sxs-lookup"><span data-stu-id="1ce91-177">For an example using Jenkins, check out Hodge's blog post [Automating with Jenkins and PowerShell on Windows - Part 2][].</span></span>

<span data-ttu-id="1ce91-178">In dit voor beeld wordt de .NET-methode gebruikt om het referentie object te maken en een beveiligde teken reeks om het wacht woord door te geven.</span><span class="sxs-lookup"><span data-stu-id="1ce91-178">This example uses the .NET method to create the credential object and a secure string to pass in the password.</span></span>

```powershell
$password = ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("duffney", $password)

$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential $Cred
```

<span data-ttu-id="1ce91-179">Voor dit voor beeld wordt de beveiligde teken reeks gemaakt met een wacht woord met een lees bare tekst.</span><span class="sxs-lookup"><span data-stu-id="1ce91-179">For this example, the secure string is created using a clear text password.</span></span> <span data-ttu-id="1ce91-180">Alle eerder genoemde CI/CD hebben een veilige methode voor het opgeven van het wacht woord tijdens runtime.</span><span class="sxs-lookup"><span data-stu-id="1ce91-180">All of the previously mentioned CI/CD have a secure method of providing that password at run time.</span></span> <span data-ttu-id="1ce91-181">Wanneer u deze hulpprogram ma's gebruikt, vervangt u het wacht woord voor onbewerkte tekst door de variabele die is gedefinieerd in het CI/CD-hulp programma dat u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1ce91-181">When using those tools, replace the plain text password with the variable defined within the CI/CD tool you use.</span></span>

### <a name="run-without-credentials"></a><span data-ttu-id="1ce91-182">Zonder referenties uitvoeren</span><span class="sxs-lookup"><span data-stu-id="1ce91-182">Run without credentials</span></span>

<span data-ttu-id="1ce91-183">Omdat `$Credential` de standaard instelling is ingesteld op een leeg referentie object, kunt u de opdracht zonder referenties uitvoeren, zoals wordt weer gegeven in dit voor beeld:</span><span class="sxs-lookup"><span data-stu-id="1ce91-183">Since `$Credential` defaults to an empty credential object, you can run the command without credentials, as shown in this example:</span></span>

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams
```

## <a name="dealing-with-legacy-cmdlets"></a><span data-ttu-id="1ce91-184">Omgaan met verouderde cmdlets</span><span class="sxs-lookup"><span data-stu-id="1ce91-184">Dealing with legacy cmdlets</span></span>

<span data-ttu-id="1ce91-185">Niet alle cmdlets ondersteunen referentie objecten of lege referenties toestaan.</span><span class="sxs-lookup"><span data-stu-id="1ce91-185">Not all cmdlets support credential objects or allow empty credentials.</span></span> <span data-ttu-id="1ce91-186">In plaats daarvan wil de cmdlet gebruikers naam-en wachtwoord parameters als teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="1ce91-186">Instead, the cmdlet wants username and password parameters as strings.</span></span> <span data-ttu-id="1ce91-187">Er zijn enkele manieren om deze beperking te omzeilen.</span><span class="sxs-lookup"><span data-stu-id="1ce91-187">There are a few ways to work around this limitation.</span></span>

### <a name="using-if-else-to-handle-empty-credentials"></a><span data-ttu-id="1ce91-188">Een if-else gebruiken voor het verwerken van lege referenties</span><span class="sxs-lookup"><span data-stu-id="1ce91-188">Using if-else to handle empty credentials</span></span>

<span data-ttu-id="1ce91-189">In dit scenario accepteert de cmdlet die u wilt uitvoeren geen leeg referentie object.</span><span class="sxs-lookup"><span data-stu-id="1ce91-189">In this scenario, the cmdlet you want to run doesn't accept an empty credential object.</span></span> <span data-ttu-id="1ce91-190">In dit voor beeld wordt de para meter **Credential** `Invoke-Command` alleen toegevoegd als deze niet leeg is.</span><span class="sxs-lookup"><span data-stu-id="1ce91-190">This example adds the **Credential** parameter to `Invoke-Command` only if it's not empty.</span></span> <span data-ttu-id="1ce91-191">Anders wordt de `Invoke-Command` para meter zonder **referenties** uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1ce91-191">Otherwise, it runs the `Invoke-Command` without the **Credential** parameter.</span></span>

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

    if($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
        Invoke-Command -ComputerName:$ComputerName -Credential:$Credential  {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    } else {
        Invoke-Command -ComputerName:$ComputerName {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    }
}
```

### <a name="using-splatting-to-handle-empty-credentials"></a><span data-ttu-id="1ce91-192">Splatting gebruiken voor het afhandelen van lege referenties</span><span class="sxs-lookup"><span data-stu-id="1ce91-192">Using splatting to handle empty credentials</span></span>

<span data-ttu-id="1ce91-193">In dit voor beeld wordt de para meter splatting gebruikt om de verouderde cmdlet aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="1ce91-193">This example uses parameter splatting to call the legacy cmdlet.</span></span> <span data-ttu-id="1ce91-194">Het `$Credential` object wordt voorwaardelijk toegevoegd aan de hashtabel voor splatting en voor komt dat het script blok moet worden herhaald `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="1ce91-194">The `$Credential` object is conditionally added to the hash table for splatting and avoids the need to repeat the `Invoke-Command` script block.</span></span> <span data-ttu-id="1ce91-195">Zie het blog bericht [splatting para meters in Advanced functions][] (Engelstalig) voor meer informatie over splatting binnen functions.</span><span class="sxs-lookup"><span data-stu-id="1ce91-195">To learn more about splatting inside functions, see the [Splatting Parameters Inside Advanced Functions][] blog post.</span></span>

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $Splat = @{
            ComputerName = $ComputerName
        }

        if ($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
            $Splat['Credential'] = $Credential
        }

        $null = Invoke-Command -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } @splat
}
```

### <a name="working-with-string-passwords"></a><span data-ttu-id="1ce91-196">Werken met wacht woorden voor teken reeksen</span><span class="sxs-lookup"><span data-stu-id="1ce91-196">Working with string passwords</span></span>

<span data-ttu-id="1ce91-197">De `Invoke-Sqlcmd` cmdlet is een voor beeld van een cmdlet waarmee een teken reeks als wacht woord wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="1ce91-197">The `Invoke-Sqlcmd` cmdlet is an example of a cmdlet that accepts a string as a password.</span></span>
<span data-ttu-id="1ce91-198">`Invoke-Sqlcmd` met kunt u eenvoudige SQL INSERT-, update-en DELETE-instructies uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="1ce91-198">`Invoke-Sqlcmd` allows you to run simple SQL insert, update, and delete statements.</span></span> <span data-ttu-id="1ce91-199">`Invoke-Sqlcmd` vereist een gebruikers naam en wacht woord met een lees bare tekst in plaats van een veiliger referentie object.</span><span class="sxs-lookup"><span data-stu-id="1ce91-199">`Invoke-Sqlcmd` requires a clear-text username and password rather than a more secure credential object.</span></span> <span data-ttu-id="1ce91-200">In dit voor beeld ziet u hoe u de gebruikers naam en het wacht woord uitpakt uit een referentie object.</span><span class="sxs-lookup"><span data-stu-id="1ce91-200">This example shows how to extract the username and password from a credential object.</span></span>

<span data-ttu-id="1ce91-201">Met de `Get-AllSQLDatabases` functie in dit voor beeld wordt de `Invoke-Sqlcmd` cmdlet aangeroepen om een query uit te voeren op een SQL-Server voor alle data bases.</span><span class="sxs-lookup"><span data-stu-id="1ce91-201">The `Get-AllSQLDatabases` function in this example calls the `Invoke-Sqlcmd` cmdlet to query a SQL server for all its databases.</span></span> <span data-ttu-id="1ce91-202">De functie definieert een **referentie** parameter met hetzelfde kenmerk dat in de vorige voor beelden wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1ce91-202">The function defines a **Credential** parameter with the same attribute used in the previous examples.</span></span> <span data-ttu-id="1ce91-203">Omdat de gebruikers naam en het wacht woord in de `$Credential` variabele bestaan, kunt u deze waarden extra heren voor gebruik met `Invoke-Sqlcmd` .</span><span class="sxs-lookup"><span data-stu-id="1ce91-203">Since the username and password exist within the `$Credential` variable, you can extract those values for use with `Invoke-Sqlcmd`.</span></span>

<span data-ttu-id="1ce91-204">De gebruikers naam is beschikbaar via de eigenschap **username** van de `$Credential` variabele.</span><span class="sxs-lookup"><span data-stu-id="1ce91-204">The user name is available from the **UserName** property of the `$Credential` variable.</span></span> <span data-ttu-id="1ce91-205">Om het wacht woord te verkrijgen, moet u de `GetNetworkCredential()` methode van het `$Credential` object gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1ce91-205">To obtain the password, you have to use the `GetNetworkCredential()` method of the `$Credential` object.</span></span> <span data-ttu-id="1ce91-206">De waarden worden geëxtraheerd in variabelen die worden toegevoegd aan een hash-tabel die wordt gebruikt voor splatting-para meters voor `Invoke-Sqlcmd` .</span><span class="sxs-lookup"><span data-stu-id="1ce91-206">The values are extracted into variables that are added to a hash table used for splatting parameters to `Invoke-Sqlcmd`.</span></span>

```powershell
function Get-AllSQLDatabases {
    param(
        $SQLServer,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $UserName = $Credential.UserName
        $Password = $Credential.GetNetworkCredential().Password

        $splat = @{
            UserName = $UserName
            Password = $Password
            ServerInstance = 'SQLServer'
            Query = "Select * from Sys.Databases"
        }

        Invoke-Sqlcmd @splat
}

$credSplat = @{
    TypeName = 'System.Management.Automation.PSCredential'
    ArgumentList = 'duffney',('P@ssw0rd' | ConvertTo-SecureString -AsPlainText -Force)
}
$Credential= New-Object @credSplat
ConvertTo-SecureString -AsPlainText -Force)

Get-AllSQLDatabases -SQLServer SQL01 -Credential $Credential
```

## <a name="continued-learning-credential-management"></a><span data-ttu-id="1ce91-207">Voortgezet leer referentie beheer</span><span class="sxs-lookup"><span data-stu-id="1ce91-207">Continued learning credential management</span></span>

<span data-ttu-id="1ce91-208">Het is veilig om referentie objecten te maken en op te slaan.</span><span class="sxs-lookup"><span data-stu-id="1ce91-208">Creating and storing credential objects securely can be difficult.</span></span> <span data-ttu-id="1ce91-209">De volgende bronnen kunnen u helpen bij het onderhouden van Power shell-referenties.</span><span class="sxs-lookup"><span data-stu-id="1ce91-209">The following resources can help you maintain PowerShell credentials.</span></span>

- <span data-ttu-id="1ce91-210">[BetterCredentials][]</span><span class="sxs-lookup"><span data-stu-id="1ce91-210">[BetterCredentials][]</span></span>
- <span data-ttu-id="1ce91-211">[Azure Key Vault][]</span><span class="sxs-lookup"><span data-stu-id="1ce91-211">[Azure Key Vault][]</span></span>
- <span data-ttu-id="1ce91-212">[Kluis project][]</span><span class="sxs-lookup"><span data-stu-id="1ce91-212">[Vault Project][]</span></span>
- <span data-ttu-id="1ce91-213">[SecretManagement-module][]</span><span class="sxs-lookup"><span data-stu-id="1ce91-213">[SecretManagement module][]</span></span>

<!-- link references -->
[oorspronkelijke versie]: https://duffney.io/addcredentialstopowershellfunctions/
[original version]: https://duffney.io/addcredentialstopowershellfunctions/
[@joshduffney]: https://twitter.com/joshduffney
[duffney.io]: https://duffney.io/posts/
[BetterCredentials]: https://www.powershellgallery.com/packages/BetterCredentials/
[Azure Key Vault]: https://azure.microsoft.com/services/key-vault/
[Kluis project]: https://www.vaultproject.io/
[Vault Project]: https://www.vaultproject.io/
[Splatting-para meters in geavanceerde functies]: http://duffney.io/Splatting-Parameters-Within-AdvancedFunctions
[Splatting Parameters Inside Advanced Functions]: http://duffney.io/Splatting-Parameters-Within-AdvancedFunctions
[Automatiseren met Jenkins en Power shell in Windows-deel 2]: https://hodgkins.io/automating-with-jenkins-and-powershell-on-windows-part-2
[Automating with Jenkins and PowerShell on Windows - Part 2]: https://hodgkins.io/automating-with-jenkins-and-powershell-on-windows-part-2
[PSCredential]: /dotnet/api/system.management.automation.pscredential
[Het ziekte-boek]: https://leanpub.com/the-pester-book
[The Pester Book]: https://leanpub.com/the-pester-book
[about_Splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[SecretManagement-module]: https://devblogs.microsoft.com/powershell/secretmanagement-and-secretstore-updates/
[SecretManagement module]: https://devblogs.microsoft.com/powershell/secretmanagement-and-secretstore-updates/
