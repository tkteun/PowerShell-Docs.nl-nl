---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-PSSessionConfigurationFile
ms.openlocfilehash: 625611246ea5a07fba16ecb86a2c8c48345d9ea5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250118"
---
# <span data-ttu-id="ee0e5-103">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="ee0e5-103">Test-PSSessionConfigurationFile</span></span>

## <span data-ttu-id="ee0e5-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ee0e5-104">SYNOPSIS</span></span>
<span data-ttu-id="ee0e5-105">Verifieert de sleutels en waarden in een sessie configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-105">Verifies the keys and values in a session configuration file.</span></span>

## <span data-ttu-id="ee0e5-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ee0e5-106">SYNTAX</span></span>

```
Test-PSSessionConfigurationFile [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="ee0e5-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ee0e5-107">DESCRIPTION</span></span>

<span data-ttu-id="ee0e5-108">Met deze cmdlet wordt gecontroleerd of een sessie configuratie bestand geldige sleutels bevat en de waarden van het juiste type zijn.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-108">This cmdlet verifies that a session configuration file contains valid keys and the values are of the correct type.</span></span> <span data-ttu-id="ee0e5-109">Voor opgesomde waarden controleert de cmdlet of de opgegeven waarden geldig zijn.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-109">For enumerated values, the cmdlet verifies that the specified values are valid.</span></span>

<span data-ttu-id="ee0e5-110">De cmdlet wordt geretourneerd `$True` als het bestand alle tests doorgeeft en `$False` als dit niet het geval is.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-110">The cmdlet returns `$True` if the file passes all tests and `$False` if it does not.</span></span> <span data-ttu-id="ee0e5-111">Gebruik de para meter **uitgebreid** om eventuele fouten te vinden.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-111">To find any errors, use the **Verbose** parameter.</span></span>

<span data-ttu-id="ee0e5-112">`Test-PSSessionConfigurationFile` verifieert de sessie configuratie bestanden, zoals die zijn gemaakt door de `New-PSSessionConfigurationFile` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-112">`Test-PSSessionConfigurationFile` verifies the session configuration files, such as those created by the `New-PSSessionConfigurationFile` cmdlet.</span></span> <span data-ttu-id="ee0e5-113">Zie [about_Session_Configurations](About/about_Session_Configurations.md)voor meer informatie over de configuratie van sessies.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-113">For information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span> <span data-ttu-id="ee0e5-114">Zie [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)voor meer informatie over sessie configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-114">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="ee0e5-115">Deze cmdlet is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-115">This cmdlet was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="ee0e5-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ee0e5-116">EXAMPLES</span></span>

### <span data-ttu-id="ee0e5-117">Voor beeld 1: een configuratie bestand voor een sessie testen</span><span class="sxs-lookup"><span data-stu-id="ee0e5-117">Example 1: Test a session configuration file</span></span>

```powershell
Test-PSSessionConfigurationFile -Path "FullLanguage.pssc"
```

```Output
True
```

### <span data-ttu-id="ee0e5-118">Voor beeld 2: het sessie configuratie bestand van een sessie configuratie testen</span><span class="sxs-lookup"><span data-stu-id="ee0e5-118">Example 2: Test the session configuration file of a session configuration</span></span>

<span data-ttu-id="ee0e5-119">In dit voor beeld testen we het configuratie bestand dat wordt gebruikt in de **beperkte** sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-119">In this example, we test the configuration file used in the **Restricted** session configuration.</span></span>
<span data-ttu-id="ee0e5-120">De waarde van de para meter **Path** is het resultaat van de `Get-PSSessionConfiguration` opdracht die de **beperkte** sessie configuratie haalt.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-120">The value of the **Path** parameter is the result of the `Get-PSSessionConfiguration` command that gets the **Restricted** session configuration.</span></span> <span data-ttu-id="ee0e5-121">Het pad van het sessie configuratie bestand wordt opgeslagen in de waarde van de eigenschap **ConfigFilePath** van de sessie configuratie.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-121">The path of the session configuration file is stored in the value of the **ConfigFilePath** property of the session configuration.</span></span>

```powershell
Test-PSSessionConfigurationFile -Path (Get-PSSessionConfiguration -Name Restricted).ConfigFilePath
```

### <span data-ttu-id="ee0e5-122">Voor beeld 3: alle sessie configuratie bestanden testen</span><span class="sxs-lookup"><span data-stu-id="ee0e5-122">Example 3: Test all session configuration files</span></span>

<span data-ttu-id="ee0e5-123">Met de functie in dit voor beeld worden alle sessie configuratie bestanden op de lokale computer getest.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-123">The function in this example tests all session configuration files on the local computer.</span></span> <span data-ttu-id="ee0e5-124">De functie gebruikt de `Get-PSSessionConfiguration` cmdlet om alle sessie configuraties op te halen.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-124">The function uses the `Get-PSSessionConfiguration` cmdlet to get all session configurations.</span></span> <span data-ttu-id="ee0e5-125">Met de code in de `ForEach-Object` lus wordt het bestandspad weer gegeven en worden alle sessie configuraties getest.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-125">The code inside the `ForEach-Object` loop displays the file path and tests each of the session configurations.</span></span>

```powershell
function Test-AllConfigFiles
{
    Get-PSSessionConfiguration | ForEach-Object {
        if ($_.ConfigFilePath) {
            $_.ConfigFilePath
            Test-PSSessionConfigurationFile -Verbose -Path $_.ConfigFilePath
        }
    }
}
Test-AllConfigFiles
```

```Output
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Empty_6fd77bf6-e084-4372-bd8a-af3e207354d3.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
VERBOSE: The member 'AliasDefinitions' must contain the required key 'Description'. Add the require key
to the fileC:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc.
False
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RestrictedLang_b6bd9474-0a6c-4e06-8722-c2c95bb10d3e.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RRS_3fb29420-2c87-46e5-a402-e21436331efc.pssc
True
```

<span data-ttu-id="ee0e5-126">De eigenschap **ConfigFilePath** van een sessie configuratie bevat het pad naar het sessie configuratie bestand dat in de sessie configuratie wordt gebruikt, indien aanwezig.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-126">The **ConfigFilePath** property of a session configuration contains the path of the session configuration file that is used in the session configuration, if any.</span></span>

<span data-ttu-id="ee0e5-127">Als de waarde van de eigenschap **ConfigFilePath** is ingevuld (is waar), wordt met de opdracht de waarde van de eigenschap **ConfigFilePath** opgehaald (afgedrukt).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-127">If the value of the **ConfigFilePath** property is populated (is true), the command gets (prints) the **ConfigFilePath** property value.</span></span> <span data-ttu-id="ee0e5-128">Vervolgens wordt de `Test-PSSessionConfigurationFile` cmdlet gebruikt om het bestand te testen in de waarde **ConfigFilePath** .</span><span class="sxs-lookup"><span data-stu-id="ee0e5-128">Then it uses the `Test-PSSessionConfigurationFile` cmdlet to test the file in the **ConfigFilePath** value.</span></span> <span data-ttu-id="ee0e5-129">De para meter **uitgebreid** retourneert de bestands fout wanneer het bestand de test mislukt.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-129">The **Verbose** parameter returns the file error when the file fails the test.</span></span>

## <span data-ttu-id="ee0e5-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ee0e5-130">PARAMETERS</span></span>

### <span data-ttu-id="ee0e5-131">-Path</span><span class="sxs-lookup"><span data-stu-id="ee0e5-131">-Path</span></span>

<span data-ttu-id="ee0e5-132">Hiermee geeft u het pad en de bestands naam van een sessie configuratie bestand (. pssc).</span><span class="sxs-lookup"><span data-stu-id="ee0e5-132">Specifies the path and filename of a session configuration file (.pssc).</span></span> <span data-ttu-id="ee0e5-133">Als u het pad weglaat, de standaard instelling is de huidige map.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-133">If you omit the path, the default is the current folder.</span></span> <span data-ttu-id="ee0e5-134">Joker tekens worden ondersteund, maar moeten worden omgezet in één bestand.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-134">Wildcard characters are supported, but they must resolve to a single file.</span></span> <span data-ttu-id="ee0e5-135">U kunt ook een pad naar een sessie configuratie bestand door geven aan `Test-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="ee0e5-135">You can also pipe a session configuration file path to `Test-PSSessionConfigurationFile`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="ee0e5-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ee0e5-136">CommonParameters</span></span>

<span data-ttu-id="ee0e5-137">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ee0e5-138">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ee0e5-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ee0e5-139">INVOER</span><span class="sxs-lookup"><span data-stu-id="ee0e5-139">INPUTS</span></span>

### <span data-ttu-id="ee0e5-140">System. String</span><span class="sxs-lookup"><span data-stu-id="ee0e5-140">System.String</span></span>

<span data-ttu-id="ee0e5-141">U kunt een pad naar een sessie configuratie bestand door geven aan `Test-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="ee0e5-141">You can pipe a session configuration file path to `Test-PSSessionConfigurationFile`.</span></span>

## <span data-ttu-id="ee0e5-142">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ee0e5-142">OUTPUTS</span></span>

### <span data-ttu-id="ee0e5-143">System. Boolean</span><span class="sxs-lookup"><span data-stu-id="ee0e5-143">System.Boolean</span></span>

## <span data-ttu-id="ee0e5-144">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ee0e5-144">NOTES</span></span>

## <span data-ttu-id="ee0e5-145">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ee0e5-145">RELATED LINKS</span></span>

[<span data-ttu-id="ee0e5-146">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee0e5-146">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="ee0e5-147">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee0e5-147">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="ee0e5-148">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee0e5-148">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="ee0e5-149">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="ee0e5-149">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="ee0e5-150">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="ee0e5-150">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="ee0e5-151">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee0e5-151">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="ee0e5-152">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee0e5-152">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="ee0e5-153">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="ee0e5-153">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="ee0e5-154">Registratie ongedaan maken-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee0e5-154">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="ee0e5-155">WSMan Provider</span><span class="sxs-lookup"><span data-stu-id="ee0e5-155">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="ee0e5-156">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="ee0e5-156">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="ee0e5-157">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="ee0e5-157">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)

