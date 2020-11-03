---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: b2c5b8596da085fab3af7a1545569dd65931a5f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250796"
---
# <span data-ttu-id="c9c0b-103">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c9c0b-103">Get-ItemProperty</span></span>

## <span data-ttu-id="c9c0b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c9c0b-104">SYNOPSIS</span></span>
<span data-ttu-id="c9c0b-105">Hiermee worden de eigenschappen van een opgegeven item opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-105">Gets the properties of a specified item.</span></span>

## <span data-ttu-id="c9c0b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c9c0b-106">SYNTAX</span></span>

### <span data-ttu-id="c9c0b-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="c9c0b-107">Path (Default)</span></span>

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="c9c0b-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c9c0b-108">LiteralPath</span></span>

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="c9c0b-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c9c0b-109">DESCRIPTION</span></span>

<span data-ttu-id="c9c0b-110">`Get-ItemProperty`Met de cmdlet worden de eigenschappen van de opgegeven items opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-110">The `Get-ItemProperty` cmdlet gets the properties of the specified items.</span></span>
<span data-ttu-id="c9c0b-111">U kunt deze cmdlet bijvoorbeeld gebruiken om de waarde van de eigenschap LastAccessTime van een File-object op te halen.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-111">For example, you can use this cmdlet to get the value of the LastAccessTime property of a file object.</span></span>
<span data-ttu-id="c9c0b-112">U kunt deze cmdlet ook gebruiken om Register vermeldingen en hun waarden weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-112">You can also use this cmdlet to view registry entries and their values.</span></span>

## <span data-ttu-id="c9c0b-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c9c0b-113">EXAMPLES</span></span>

### <span data-ttu-id="c9c0b-114">Voor beeld 1: informatie over een specifieke directory ophalen</span><span class="sxs-lookup"><span data-stu-id="c9c0b-114">Example 1: Get information about a specific directory</span></span>

<span data-ttu-id="c9c0b-115">Met deze opdracht wordt informatie over de map C:\Windows opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-115">This command gets information about the "C:\Windows" directory.</span></span>

```powershell
Get-ItemProperty C:\Windows
```

### <span data-ttu-id="c9c0b-116">Voor beeld 2: de eigenschappen van een specifiek bestand ophalen</span><span class="sxs-lookup"><span data-stu-id="c9c0b-116">Example 2: Get the properties of a specific file</span></span>

<span data-ttu-id="c9c0b-117">Met deze opdracht worden de eigenschappen van het bestand ' C:\Test\Weather.xls ' opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-117">This command gets the properties of the "C:\Test\Weather.xls" file.</span></span>
<span data-ttu-id="c9c0b-118">Het resultaat wordt naar de cmdlet gepiped `Format-List` om de uitvoer als een lijst weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-118">The result is piped to the `Format-List` cmdlet to display the output as a list.</span></span>

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### <span data-ttu-id="c9c0b-119">Voor beeld 3: de waardenaam en gegevens van Register vermeldingen in een register sleutel weer geven</span><span class="sxs-lookup"><span data-stu-id="c9c0b-119">Example 3: Display the value name and data of registry entries in a registry subkey</span></span>

<span data-ttu-id="c9c0b-120">Met deze opdracht worden de naam en de gegevens van elk van de Register vermeldingen in de registersubsleutel ' CurrentVersion ' weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-120">This command displays the value name and data of each of the registry entries contained in the "CurrentVersion" registry subkey.</span></span>
<span data-ttu-id="c9c0b-121">Houd er rekening mee dat de opdracht vereist dat er een Power Shell-station `HKLM:` met de naam wordt toegewezen aan de component HKEY_LOCAL_MACHINE van het REGI ster.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-121">Note that the command requires that there is a PowerShell drive named `HKLM:` that is mapped to the "HKEY_LOCAL_MACHINE" hive of the registry.</span></span>
<span data-ttu-id="c9c0b-122">Een station met die naam en toewijzing is standaard beschikbaar in Power shell.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-122">A drive with that name and mapping is available in PowerShell by default.</span></span>
<span data-ttu-id="c9c0b-123">U kunt ook het pad naar deze registersubsleutel opgeven met behulp van het volgende alternatieve pad dat begint met de provider naam gevolgd door twee dubbele punten:</span><span class="sxs-lookup"><span data-stu-id="c9c0b-123">Alternatively, the path to this registry subkey can be specified by using the following alternative path that begins with the provider name followed by two colons:</span></span>

<span data-ttu-id="c9c0b-124">"REGI ster:: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion".</span><span class="sxs-lookup"><span data-stu-id="c9c0b-124">"Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion".</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

### <span data-ttu-id="c9c0b-125">Voor beeld 4: de waardenaam en gegevens van een register vermelding in een registersubsleutel ophalen</span><span class="sxs-lookup"><span data-stu-id="c9c0b-125">Example 4: Get the value name and data of a registry entry in a registry subkey</span></span>

<span data-ttu-id="c9c0b-126">Met deze opdracht worden de waardenaam en de gegevens van de register vermelding ' ProgramFilesDir ' in de registersubsleutel ' CurrentVersion ' opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-126">This command gets the value name and data of the "ProgramFilesDir" registry entry in the "CurrentVersion" registry subkey.</span></span>
<span data-ttu-id="c9c0b-127">De opdracht gebruikt de para meter **Path** om de subsleutel en de para meter name op te geven om de waardenaam van het item op te geven.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-127">The command uses the **Path** parameter to specify the subkey and the Name parameter to specify the value name of the entry.</span></span>

<span data-ttu-id="c9c0b-128">De opdracht maakt gebruik van een schuine streep of accent grave ( \` ), het Power shell vervolg teken, om de opdracht op de tweede regel voort te zetten.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-128">The command uses a back tick or grave accent (\`), the PowerShell continuation character, to continue the command on the second line.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### <span data-ttu-id="c9c0b-129">Voor beeld 5: de waardenamen en gegevens van Register vermeldingen in een register sleutel ophalen</span><span class="sxs-lookup"><span data-stu-id="c9c0b-129">Example 5: Get the value names and data of registry entries in a registry key</span></span>

<span data-ttu-id="c9c0b-130">Met deze opdracht worden de waardenamen en gegevens van de Register vermeldingen in de register sleutel ' PowerShellEngine ' opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-130">This command gets the value names and data of the registry entries in the "PowerShellEngine" registry key.</span></span>
<span data-ttu-id="c9c0b-131">De resultaten worden weer gegeven in de volgende voorbeeld uitvoer.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-131">The results are shown in the following sample output.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\PowerShellEngine
```

```output
ApplicationBase         : C:\Windows\system32\WindowsPowerShell\v1.0\
ConsoleHostAssemblyName : Microsoft.PowerShell.ConsoleHost, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, ProcessorArchitecture=msil
PowerShellVersion       : 2.0
RuntimeVersion          : v2.0.50727
CTPVersion              : 5
PSCompatibleVersion     : 1.0,2.0
```

### <span data-ttu-id="c9c0b-132">Voor beeld 6: de resultaten van register waarden en-gegevens ophalen, opmaken en weer geven</span><span class="sxs-lookup"><span data-stu-id="c9c0b-132">Example 6: Get, format, and display the results of registry values and data</span></span>

<span data-ttu-id="c9c0b-133">In dit voor beeld ziet u hoe u de uitvoer van een `Get-ItemProperty` opdracht in een lijst kunt opmaken, zodat u de register waarden en gegevens eenvoudig kunt zien en de resultaten gemakkelijk kunt interpreteren.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-133">This example shows how to format the output of a `Get-ItemProperty` command in a list to make it easy to see the registry values and data and to make it easy to interpret the results.</span></span>

<span data-ttu-id="c9c0b-134">De eerste opdracht gebruikt de `Get-ItemProperty` cmdlet om de Register vermeldingen in de subsleutel **micro soft. Power shell** op te halen.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-134">The first command uses the `Get-ItemProperty` cmdlet to get the registry entries in the **Microsoft.PowerShell** subkey.</span></span>
<span data-ttu-id="c9c0b-135">Met deze subsleutel worden de opties voor de standaard shell voor Power shell opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-135">This subkey stores options for the default shell for PowerShell.</span></span>
<span data-ttu-id="c9c0b-136">De resultaten worden weer gegeven in de volgende voorbeeld uitvoer.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-136">The results are shown in the following sample output.</span></span>

<span data-ttu-id="c9c0b-137">In de uitvoer ziet u dat er twee Register vermeldingen, "pad" en "ExecutionPolicy" zijn.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-137">The output shows that there are two registry entries, "Path" and "ExecutionPolicy".</span></span>
<span data-ttu-id="c9c0b-138">Wanneer een register sleutel minder dan vijf vermeldingen bevat, wordt deze standaard weer gegeven in een tabel, maar het is vaak gemakkelijker om in een lijst te zien.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-138">When a registry key contains fewer than five entries, by default it is displayed in a table, but it is often easier to view in a list.</span></span>

<span data-ttu-id="c9c0b-139">De tweede opdracht maakt gebruik van dezelfde `Get-ItemProperty` opdracht.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-139">The second command uses the same `Get-ItemProperty` command.</span></span>
<span data-ttu-id="c9c0b-140">Deze keer gebruikt de opdracht echter een pijplijn operator ( `|` ) om de resultaten van de opdracht naar de cmdlet te verzenden `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="c9c0b-140">However, this time, the command uses a pipeline operator (`|`) to send the results of the command to the `Format-List` cmdlet.</span></span>
<span data-ttu-id="c9c0b-141">De `Format-List` opdracht gebruikt de eigenschaps parameter met de waarde ' \* ' (alle) om alle eigenschappen van de objecten in een lijst weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-141">The `Format-List` command uses the Property parameter with a value of '\*' (all) to display all of the properties of the objects in a list.</span></span>
<span data-ttu-id="c9c0b-142">De resultaten worden weer gegeven in de volgende voorbeeld uitvoer.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-142">The results are shown in the following sample output.</span></span>

<span data-ttu-id="c9c0b-143">In het resulterende venster worden de Register vermeldingen ' pad ' en ' ExecutionPolicy ' weer gegeven, samen met een aantal minder bekende eigenschappen van het register sleutel object.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-143">The resulting display shows the "Path" and "ExecutionPolicy" registry entries, along with several less familiar properties of the registry key object.</span></span>
<span data-ttu-id="c9c0b-144">De andere eigenschappen, voorafgegaan door PS, zijn eigenschappen van aangepaste Power shell-objecten, zoals de objecten die de register sleutels vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-144">The other properties, prefixed with PS, are properties of PowerShell custom objects, such as the objects that represent the registry keys.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell
```

```output
Path                                                        ExecutionPolicy
----                                                        ---------------
C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe   RemoteSigned
```

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell | Format-List -Property *
```

```output
PSPath          : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds\Micro
soft.PowerShell
PSParentPath    : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds
PSChildName     : Microsoft.PowerShell
PSDrive         : HKLM
PSProvider      : Microsoft.PowerShell.Core\Registry
Path            : C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe
ExecutionPolicy : RemoteSigned
```

## <span data-ttu-id="c9c0b-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c9c0b-145">PARAMETERS</span></span>

### <span data-ttu-id="c9c0b-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="c9c0b-146">-Credential</span></span>

<span data-ttu-id="c9c0b-147">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-147">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="c9c0b-148">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-148">The default is the current user.</span></span>

<span data-ttu-id="c9c0b-149">Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-149">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="c9c0b-150">Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-150">If you type a user name, you are prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="c9c0b-151">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-151">This parameter is not supported by any providers installed with Windows PowerShell.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c9c0b-152">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="c9c0b-152">-Exclude</span></span>

<span data-ttu-id="c9c0b-153">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-153">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="c9c0b-154">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="c9c0b-154">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="c9c0b-155">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-155">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="c9c0b-156">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-156">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="c9c0b-157">-Filter</span><span class="sxs-lookup"><span data-stu-id="c9c0b-157">-Filter</span></span>

<span data-ttu-id="c9c0b-158">Hiermee geeft u een filter op in de indeling of taal van de provider.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-158">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="c9c0b-159">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="c9c0b-159">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="c9c0b-160">De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-160">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="c9c0b-161">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-161">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c9c0b-162">-Include</span><span class="sxs-lookup"><span data-stu-id="c9c0b-162">-Include</span></span>

<span data-ttu-id="c9c0b-163">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-163">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="c9c0b-164">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="c9c0b-164">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="c9c0b-165">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-165">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="c9c0b-166">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-166">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="c9c0b-167">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c9c0b-167">-LiteralPath</span></span>

<span data-ttu-id="c9c0b-168">Hiermee geeft u het pad op naar de huidige locatie van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-168">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="c9c0b-169">In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-169">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="c9c0b-170">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-170">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="c9c0b-171">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-171">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="c9c0b-172">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-172">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c9c0b-173">-Name</span><span class="sxs-lookup"><span data-stu-id="c9c0b-173">-Name</span></span>

<span data-ttu-id="c9c0b-174">Hiermee geeft u de naam op van de eigenschap of eigenschappen die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-174">Specifies the name of the property or properties to retrieve.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c9c0b-175">-Path</span><span class="sxs-lookup"><span data-stu-id="c9c0b-175">-Path</span></span>

<span data-ttu-id="c9c0b-176">Hiermee geeft u het pad op naar het item of de items.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-176">Specifies the path to the item or items.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c9c0b-177">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="c9c0b-177">-UseTransaction</span></span>

<span data-ttu-id="c9c0b-178">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-178">Includes the command in the active transaction.</span></span>
<span data-ttu-id="c9c0b-179">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-179">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="c9c0b-180">Zie de opdracht opnemen in de actieve trans actie voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-180">For more information, see Includes the command in the active transaction.</span></span>
<span data-ttu-id="c9c0b-181">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-181">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="c9c0b-182">Zie [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-182">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c9c0b-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c9c0b-183">CommonParameters</span></span>

<span data-ttu-id="c9c0b-184">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="c9c0b-184">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="c9c0b-185">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-185">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c9c0b-186">INVOER</span><span class="sxs-lookup"><span data-stu-id="c9c0b-186">INPUTS</span></span>

### <span data-ttu-id="c9c0b-187">System. String</span><span class="sxs-lookup"><span data-stu-id="c9c0b-187">System.String</span></span>

<span data-ttu-id="c9c0b-188">U kunt een teken reeks met een pad naar door sluizen `Get-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="c9c0b-188">You can pipe a string that contains a path to `Get-ItemProperty`.</span></span>

## <span data-ttu-id="c9c0b-189">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c9c0b-189">OUTPUTS</span></span>

### <span data-ttu-id="c9c0b-190">System. Boolean, System. String, System. DateTime</span><span class="sxs-lookup"><span data-stu-id="c9c0b-190">System.Boolean, System.String, System.DateTime</span></span>

<span data-ttu-id="c9c0b-191">`Get-ItemProperty` retourneert een object voor elke item eigenschap die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-191">`Get-ItemProperty` returns an object for each item property that it gets.</span></span>
<span data-ttu-id="c9c0b-192">Het object type is afhankelijk van het object dat wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-192">The object type depends on the object that is retrieved.</span></span>
<span data-ttu-id="c9c0b-193">Zo kan een bestand of map in een bestandssysteem station worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-193">For example, in a file system drive, it might return a file or folder.</span></span>

## <span data-ttu-id="c9c0b-194">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c9c0b-194">NOTES</span></span>

<span data-ttu-id="c9c0b-195">De `Get-ItemProperty` cmdlet is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-195">The `Get-ItemProperty` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="c9c0b-196">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u " `Get-PSProvider` ".</span><span class="sxs-lookup"><span data-stu-id="c9c0b-196">To list the providers available in your session, type "`Get-PSProvider`".</span></span> <span data-ttu-id="c9c0b-197">Zie about_Providers voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c9c0b-197">For more information, see about_Providers.</span></span>

## <span data-ttu-id="c9c0b-198">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c9c0b-198">RELATED LINKS</span></span>

[<span data-ttu-id="c9c0b-199">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="c9c0b-199">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="c9c0b-200">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="c9c0b-200">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="c9c0b-201">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="c9c0b-201">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="c9c0b-202">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="c9c0b-202">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="c9c0b-203">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="c9c0b-203">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="c9c0b-204">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="c9c0b-204">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="c9c0b-205">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="c9c0b-205">Set-ItemProperty</span></span>](Set-ItemProperty.md)
