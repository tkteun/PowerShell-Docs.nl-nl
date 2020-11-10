---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-xml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Xml
ms.openlocfilehash: 7e3d02dedb9f7809a8f8e1c657987fef8ec38fa9
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387988"
---
# <span data-ttu-id="d84b0-103">Select-Xml</span><span class="sxs-lookup"><span data-stu-id="d84b0-103">Select-Xml</span></span>

## <span data-ttu-id="d84b0-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d84b0-104">SYNOPSIS</span></span>
<span data-ttu-id="d84b0-105">Zoekt tekst in een XML-teken reeks of-document.</span><span class="sxs-lookup"><span data-stu-id="d84b0-105">Finds text in an XML string or document.</span></span>

## <span data-ttu-id="d84b0-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d84b0-106">SYNTAX</span></span>

### <span data-ttu-id="d84b0-107">XML (standaard)</span><span class="sxs-lookup"><span data-stu-id="d84b0-107">Xml (Default)</span></span>

```
Select-Xml [-Xml] <XmlNode[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="d84b0-108">Pad</span><span class="sxs-lookup"><span data-stu-id="d84b0-108">Path</span></span>

```
Select-Xml [-Path] <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="d84b0-109">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d84b0-109">LiteralPath</span></span>

```
Select-Xml -LiteralPath <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="d84b0-110">Inhoud</span><span class="sxs-lookup"><span data-stu-id="d84b0-110">Content</span></span>

```
Select-Xml -Content <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

## <span data-ttu-id="d84b0-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d84b0-111">DESCRIPTION</span></span>

<span data-ttu-id="d84b0-112">Met de cmdlet **Select-XML** kunt u XPath-query's gebruiken om te zoeken naar tekst in XML-teken reeksen en documenten.</span><span class="sxs-lookup"><span data-stu-id="d84b0-112">The **Select-Xml** cmdlet lets you use XPath queries to search for text in XML strings and documents.</span></span>
<span data-ttu-id="d84b0-113">Voer een XPath-query in en gebruik de para meter *Content* , *Path* of *XML* om op te geven welke XML moet worden doorzocht.</span><span class="sxs-lookup"><span data-stu-id="d84b0-113">Enter an XPath query, and use the *Content* , *Path* , or *Xml* parameter to specify the XML to be searched.</span></span>

## <span data-ttu-id="d84b0-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d84b0-114">EXAMPLES</span></span>

### <span data-ttu-id="d84b0-115">Voor beeld 1: AliasProperty-knoop punten selecteren</span><span class="sxs-lookup"><span data-stu-id="d84b0-115">Example 1: Select AliasProperty nodes</span></span>

```
PS C:\> $Path = "$Pshome\Types.ps1xml"
PS C:\> $XPath = "/Types/Type/Members/AliasProperty"
PS C:\> Select-Xml -Path $Path -XPath $Xpath | Select-Object -ExpandProperty Node
Name                 ReferencedMemberName
----                 --------------------
Count                Length
Name                 Key
Name                 ServiceName
RequiredServices     ServicesDependedOn
ProcessName          Name
Handles              Handlecount
VM                   VirtualSize
WS                   WorkingSetSize
Name                 ProcessName
Handles              Handlecount
VM                   VirtualMemorySize
WS                   WorkingSet
PM                   PagedMemorySize
NPM                  NonpagedSystemMemorySize
Name                 __Class
Namespace            ModuleName
```

<span data-ttu-id="d84b0-116">In dit voor beeld worden de alias eigenschappen in de Types.ps1XML opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d84b0-116">This example gets the alias properties in the Types.ps1xml.</span></span>
<span data-ttu-id="d84b0-117">(Zie about_Types.ps1XML (Engelstalig) voor meer informatie over dit bestand.</span><span class="sxs-lookup"><span data-stu-id="d84b0-117">(For information about this file, see about_Types.ps1xml.)</span></span>

<span data-ttu-id="d84b0-118">Met de eerste opdracht wordt het pad naar het Types.ps1XML-bestand in de $Path variabele opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="d84b0-118">The first command saves the path to the Types.ps1xml file in the $Path variable.</span></span>

<span data-ttu-id="d84b0-119">Met de tweede opdracht slaat u het XML-pad op naar het AliasProperty-knoop punt in de variabele $XPath.</span><span class="sxs-lookup"><span data-stu-id="d84b0-119">The second command saves the XML path to the AliasProperty node in the $XPath variable.</span></span>

<span data-ttu-id="d84b0-120">De derde opdracht maakt gebruik van de **Select-XML-** cmdlet om de AliasProperty-knoop punten op te halen die worden geïdentificeerd door de XPath-instructie van het Types.ps1XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="d84b0-120">The third command uses the **Select-Xml** cmdlet to get the AliasProperty nodes that are identified by the XPath statement from the Types.ps1xml file.</span></span>
<span data-ttu-id="d84b0-121">De opdracht maakt gebruik van een pijplijn operator om de AliasProperty-knoop punten te verzenden naar de cmdlet Select-Object.</span><span class="sxs-lookup"><span data-stu-id="d84b0-121">The command uses a pipeline operator to send the AliasProperty nodes to the Select-Object cmdlet.</span></span>
<span data-ttu-id="d84b0-122">De para meter *ExpandProperty* breidt het **knooppunt** object uit en retourneert de eigenschappen name en ReferencedMemberName.</span><span class="sxs-lookup"><span data-stu-id="d84b0-122">The *ExpandProperty* parameter expands the **Node** object and returns its Name and ReferencedMemberName properties.</span></span>

<span data-ttu-id="d84b0-123">Het resultaat toont de naam en ReferencedMemberName van elke alias eigenschap in het XML-bestand Types.ps1.</span><span class="sxs-lookup"><span data-stu-id="d84b0-123">The result shows the Name and ReferencedMemberName of each alias property in the Types.ps1xml file.</span></span>
<span data-ttu-id="d84b0-124">Er is bijvoorbeeld een eigenschap **Count** die een alias is van de eigenschap **Length** .</span><span class="sxs-lookup"><span data-stu-id="d84b0-124">For example, there is a **Count** property that is an alias of the **Length** property.</span></span>

### <span data-ttu-id="d84b0-125">Voor beeld 2: een XML-document invoeren</span><span class="sxs-lookup"><span data-stu-id="d84b0-125">Example 2: Input an XML document</span></span>

```
PS C:\> [xml]$Types = Get-Content $Pshome\Types.ps1xml
PS C:\> Select-Xml -Xml $Types -XPath "//MethodName"
```

<span data-ttu-id="d84b0-126">In dit voor beeld ziet u hoe u de *XML-* para meter gebruikt om een XML-document te voorzien van de cmdlet **Select-XML** .</span><span class="sxs-lookup"><span data-stu-id="d84b0-126">This example shows how to use the *XML* parameter to provide an XML document to the **Select-Xml** cmdlet.</span></span>

<span data-ttu-id="d84b0-127">De eerste opdracht gebruikt de cmdlet Get-Content om de inhoud van het Types.ps1XML-bestand op te halen en op te slaan in de $Types variabele.</span><span class="sxs-lookup"><span data-stu-id="d84b0-127">The first command uses the Get-Content cmdlet to get the content of the Types.ps1xml file and save it in the $Types variable.</span></span>
<span data-ttu-id="d84b0-128">Het \[ XML \] cast de variabele als een XML-object.</span><span class="sxs-lookup"><span data-stu-id="d84b0-128">The \[xml\] casts the variable as an XML object.</span></span>

<span data-ttu-id="d84b0-129">De tweede opdracht maakt gebruik van de **Select-XML-** cmdlet voor het ophalen van de methodName-knoop punten in het Types.ps1XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="d84b0-129">The second command uses the **Select-Xml** cmdlet to get the MethodName nodes in the Types.ps1xml file.</span></span>
<span data-ttu-id="d84b0-130">De opdracht gebruikt de *XML-* para meter om de XML-inhoud in de variabele $types en de para meter *XPath* op te geven het pad naar het knoop punt van de methode.</span><span class="sxs-lookup"><span data-stu-id="d84b0-130">The command uses the *Xml* parameter to specify the XML content in the $Types variable and the *XPath* parameter to specify the path to the MethodName node.</span></span>

### <span data-ttu-id="d84b0-131">Voor beeld 3: Help-bestanden voor Power shell zoeken</span><span class="sxs-lookup"><span data-stu-id="d84b0-131">Example 3: Search PowerShell Help files</span></span>

```
PS C:\> $Namespace = @{command = "http://schemas.microsoft.com/maml/dev/command/2004/10"; maml = "http://schemas.microsoft.com/maml/2004/10"; dev = "http://schemas.microsoft.com/maml/dev/2004/10"}

The second command saves the path to the help files in the $Path variable.If there are no help files in this path on your computer, use the Update-Help cmdlet to download the help files. For more information about Updatable Help, see about_Updatable_Help (https://go.microsoft.com/fwlink/?LinkId=235801).
PS C:\> $Path = "$Pshome\en-us\*dll-Help.xml"

The third command uses the **Select-Xml** cmdlet to search the XML for cmdlet names by finding Command:Name element anywhere in the files. It saves the results in the $Xml variable.**Select-Xml** returns a **SelectXmlInfo** object that has a Node property, which is a **System.Xml.XmlElement** object. The Node property has an InnerXML property, which contains the actual XML that is retrieved.
PS C:\> $Xml = Select-Xml -Path $Path -Namespace $Namespace -XPath "//command:name"

The fourth command sends the XML in the $Xml variable to the Format-Table cmdlet. The **Format-Table** command uses a calculated property to get the Node.InnerXML property of each object in the $Xml variable, trim the white space before and after the text, and display it in the table, along with the path to the source file.
PS C:\> $Xml | Format-Table @{Label="Name"; Expression= {($_.node.innerxml).trim()}}, Path -AutoSize

Name                    Path
----                    ----
Export-Counter          C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Get-Counter             C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Get-WinEvent            C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Import-Counter          C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Add-Computer            C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
Add-Content             C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
Checkpoint-Computer     C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
...
```

<span data-ttu-id="d84b0-132">In dit voor beeld ziet u hoe u met de cmdlet **Select-XML** de Help-bestanden op basis van de Power shell-cmdlet doorzoekt.</span><span class="sxs-lookup"><span data-stu-id="d84b0-132">This example shows how to use the **Select-Xml** cmdlet to search the PowerShell XML-based cmdlet help files.</span></span>
<span data-ttu-id="d84b0-133">In dit voor beeld wordt gezocht naar de naam van de cmdlet die fungeert als titel voor elk Help-bestand en het pad naar het Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="d84b0-133">In this example, we'll search for the cmdlet name that serves as a title for each help file and the path to the help file.</span></span>

<span data-ttu-id="d84b0-134">Met de eerste opdracht maakt u een hash-tabel die de XML-naam ruimte vertegenwoordigt die wordt gebruikt voor de Help-bestanden en slaat u deze op in de variabele $Namespace.</span><span class="sxs-lookup"><span data-stu-id="d84b0-134">The first command creates a hash table that represents the XML namespace that is used for the help files and saves it in the $Namespace variable.</span></span>

### <span data-ttu-id="d84b0-135">Voor beeld 4: verschillende manieren voor het invoeren van XML</span><span class="sxs-lookup"><span data-stu-id="d84b0-135">Example 4: Different ways to input XML</span></span>

```
PS C:\> $Xml = @"
<?xml version="1.0" encoding="utf-8"?>
<Book>
  <projects>
    <project name="Book1" date="2009-01-20">
      <editions>
        <edition language="English">En.Book1.com</edition>
        <edition language="German">Ge.Book1.Com</edition>
        <edition language="French">Fr.Book1.com</edition>
        <edition language="Polish">Pl.Book1.com</edition>
      </editions>
    </project>
  </projects>
</Book>
"@

The second command uses the *Content* parameter of **Select-Xml** to specify the XML in the $Xml variable.
PS C:\> Select-Xml -Content $Xml -XPath "//edition" | foreach {$_.node.InnerXML}

En.Book1.com
Ge.Book1.Com
Fr.Book1.com
Pl.Book1.com

The third command is equivalent to the second. It uses a pipeline operator (|) to send the XML in the $Xml variable to the **Select-Xml** cmdlet.
PS C:\> $Xml | Select-Xml -XPath "//edition" | foreach {$_.node.InnerXML}

En.Book1.com
Ge.Book1.Com
Fr.Book1.com
Pl.Book1.com
```

<span data-ttu-id="d84b0-136">In dit voor beeld ziet u twee verschillende manieren voor het verzenden van XML naar de cmdlet **Select-XML** .</span><span class="sxs-lookup"><span data-stu-id="d84b0-136">This example shows two different ways to send XML to the **Select-Xml** cmdlet.</span></span>

<span data-ttu-id="d84b0-137">Met de eerste opdracht slaat u een hier-teken reeks op die XML bevat in de variabele $Xml.</span><span class="sxs-lookup"><span data-stu-id="d84b0-137">The first command saves a here-string that contains XML in the $Xml variable.</span></span>
<span data-ttu-id="d84b0-138">(Zie about_Quoting_Rules voor meer informatie over hier teken reeksen.)</span><span class="sxs-lookup"><span data-stu-id="d84b0-138">(For more information about here-strings, see about_Quoting_Rules.)</span></span>

### <span data-ttu-id="d84b0-139">Voor beeld 5: de standaard xmlns-naam ruimte gebruiken</span><span class="sxs-lookup"><span data-stu-id="d84b0-139">Example 5: Use the default xmlns namespace</span></span>

```
PS C:\> $SnippetNamespace = @{snip = "http://schemas.microsoft.com/PowerShell/Snippets"}

The second command uses the **Select-Xml** cmdlet to get the content of the Title element of each snippet. It uses the *Path* parameter to specify the Snippets directory and the *Namespace* parameter to specify the namespace in the $SnippetNamespace variable. The value of the *XPath* parameter is the "snip" namespace key, a colon (:), and the name of the Title element.The command uses a pipeline operator (|) to send each **Node** property that **Select-Xml** returns to the ForEach-Object cmdlet, which gets the title in the value of the **InnerXml** property of the node.
PS C:\> Select-Xml -Path $Home\Documents\WindowsPowerShell\Snippets -Namespace $SnippetNamespace -XPath "//snip:Title" | foreach {$_.Node.Innerxml}
```

<span data-ttu-id="d84b0-140">In dit voor beeld ziet u hoe u de cmdlet **Select-XML** gebruikt met XML-documenten die de standaard xmlns-naam ruimte gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d84b0-140">This example shows how to use the **Select-Xml** cmdlet with XML documents that use the default xmlns namespace.</span></span>
<span data-ttu-id="d84b0-141">In het voor beeld worden de titels van Windows PowerShell ISE door de gebruiker gemaakte fragment bestanden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d84b0-141">The example gets the titles of Windows PowerShell ISE user-created snippet files.</span></span>
<span data-ttu-id="d84b0-142">Zie New-IseSnippet voor meer informatie over fragmenten.</span><span class="sxs-lookup"><span data-stu-id="d84b0-142">For information about snippets, see New-IseSnippet.</span></span>

<span data-ttu-id="d84b0-143">Met de eerste opdracht maakt u een hash-tabel voor de standaard naam ruimte die XML-bestanden van het fragment gebruikt en wijst u deze toe aan de $SnippetNamespace variabele.</span><span class="sxs-lookup"><span data-stu-id="d84b0-143">The first command creates a hash table for the default namespace that snippet XML files use and assigns it to the $SnippetNamespace variable.</span></span>
<span data-ttu-id="d84b0-144">De waarde van de hash-tabel is de XMLNS-schema-URI in het XML-code fragment.</span><span class="sxs-lookup"><span data-stu-id="d84b0-144">The hash table value is the XMLNS schema URI in the snippet XML.</span></span>
<span data-ttu-id="d84b0-145">De sleutel naam van de hash-tabel, knipsel, is wille keurig.</span><span class="sxs-lookup"><span data-stu-id="d84b0-145">The hash table key name, snip, is arbitrary.</span></span>
<span data-ttu-id="d84b0-146">U kunt een naam gebruiken die niet is gereserveerd, maar u kunt geen xmlns gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d84b0-146">You can use any name that is not reserved, but you cannot use xmlns.</span></span>

## <span data-ttu-id="d84b0-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d84b0-147">PARAMETERS</span></span>

### <span data-ttu-id="d84b0-148">-Inhoud</span><span class="sxs-lookup"><span data-stu-id="d84b0-148">-Content</span></span>

<span data-ttu-id="d84b0-149">Hiermee geeft u een teken reeks op die de XML bevat waarnaar moet worden gezocht.</span><span class="sxs-lookup"><span data-stu-id="d84b0-149">Specifies a string that contains the XML to search.</span></span>
<span data-ttu-id="d84b0-150">U kunt ook teken reeksen door sluizen naar **Select-XML**.</span><span class="sxs-lookup"><span data-stu-id="d84b0-150">You can also pipe strings to **Select-Xml**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Content
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d84b0-151">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d84b0-151">-LiteralPath</span></span>

<span data-ttu-id="d84b0-152">Hiermee geeft u de paden en bestands namen op van de XML-bestanden die u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="d84b0-152">Specifies the paths and file names of the XML files to search.</span></span>
<span data-ttu-id="d84b0-153">In tegens telling tot *Path* wordt de waarde van de para meter *LiteralPath* exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="d84b0-153">Unlike *Path* , the value of the *LiteralPath* parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="d84b0-154">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="d84b0-154">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="d84b0-155">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="d84b0-155">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="d84b0-156">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="d84b0-156">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="d84b0-157">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="d84b0-157">-Namespace</span></span>

<span data-ttu-id="d84b0-158">Hiermee geeft u een hash-tabel op van de naam ruimten die worden gebruikt in de XML.</span><span class="sxs-lookup"><span data-stu-id="d84b0-158">Specifies a hash table of the namespaces used in the XML.</span></span>
<span data-ttu-id="d84b0-159">Gebruik de indeling @ { \<namespaceName\>  =  \<namespaceValue\> }.</span><span class="sxs-lookup"><span data-stu-id="d84b0-159">Use the format @{\<namespaceName\> = \<namespaceValue\>}.</span></span>

<span data-ttu-id="d84b0-160">Wanneer de XML de standaard naam ruimte gebruikt, die begint met xmlns, gebruikt u een wille keurige sleutel voor de naam van de naam ruimte.</span><span class="sxs-lookup"><span data-stu-id="d84b0-160">When the XML uses the default namespace, which begins with xmlns, use an arbitrary key for the namespace name.</span></span>
<span data-ttu-id="d84b0-161">U kunt xmlns niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d84b0-161">You cannot use xmlns.</span></span>
<span data-ttu-id="d84b0-162">In de XPath-instructie, voor voegsel van elke knooppunt naam met de naam van de naam ruimte en een dubbele punt, zoals//namespaceName: node.</span><span class="sxs-lookup"><span data-stu-id="d84b0-162">In the XPath statement, prefix each node name with the namespace name and a colon, such as //namespaceName:Node.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d84b0-163">-Path</span><span class="sxs-lookup"><span data-stu-id="d84b0-163">-Path</span></span>

<span data-ttu-id="d84b0-164">Hiermee geeft u het pad en de bestands namen op van de XML-bestanden die u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="d84b0-164">Specifies the path and file names of the XML files to search.</span></span>
<span data-ttu-id="d84b0-165">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="d84b0-165">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="d84b0-166">-XML</span><span class="sxs-lookup"><span data-stu-id="d84b0-166">-Xml</span></span>

<span data-ttu-id="d84b0-167">Hiermee geeft u een of meer XML-knoop punten op.</span><span class="sxs-lookup"><span data-stu-id="d84b0-167">Specifies one or more XML nodes.</span></span>

<span data-ttu-id="d84b0-168">Een XML-document wordt verwerkt als een verzameling van XML-knoop punten.</span><span class="sxs-lookup"><span data-stu-id="d84b0-168">An XML document will be processed as a collection of XML nodes.</span></span>
<span data-ttu-id="d84b0-169">Als u een XML-document pipet naar **Select-XML** , wordt elk document knooppunt afzonderlijk doorzocht, zoals het door de pijp lijn wordt geleverd.</span><span class="sxs-lookup"><span data-stu-id="d84b0-169">If you pipe an XML document to **Select-Xml** , each document node will be searched separately as it comes through the pipeline.</span></span>

```yaml
Type: System.Xml.XmlNode[]
Parameter Sets: Xml
Aliases: Node

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d84b0-170">-XPath</span><span class="sxs-lookup"><span data-stu-id="d84b0-170">-XPath</span></span>

<span data-ttu-id="d84b0-171">Hiermee geeft u een XPath-Zoek query op.</span><span class="sxs-lookup"><span data-stu-id="d84b0-171">Specifies an XPath search query.</span></span>
<span data-ttu-id="d84b0-172">De query taal is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="d84b0-172">The query language is case-sensitive.</span></span>
<span data-ttu-id="d84b0-173">Deze parameter is vereist.</span><span class="sxs-lookup"><span data-stu-id="d84b0-173">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d84b0-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d84b0-174">CommonParameters</span></span>

<span data-ttu-id="d84b0-175">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d84b0-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d84b0-176">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d84b0-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d84b0-177">INVOER</span><span class="sxs-lookup"><span data-stu-id="d84b0-177">INPUTS</span></span>

### <span data-ttu-id="d84b0-178">Knoop punt System. String of System.Xml.Xml</span><span class="sxs-lookup"><span data-stu-id="d84b0-178">System.String or System.Xml.XmlNode</span></span>

<span data-ttu-id="d84b0-179">U kunt een pad of XML-knoop punt door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d84b0-179">You can pipe a path or XML node to this cmdlet.</span></span>

## <span data-ttu-id="d84b0-180">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d84b0-180">OUTPUTS</span></span>

### <span data-ttu-id="d84b0-181">Micro soft. Power shell. commands. SelectXmlInfo</span><span class="sxs-lookup"><span data-stu-id="d84b0-181">Microsoft.PowerShell.Commands.SelectXmlInfo</span></span>

## <span data-ttu-id="d84b0-182">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d84b0-182">NOTES</span></span>

<span data-ttu-id="d84b0-183">XPath is een standaard taal die is ontworpen om delen van een XML-document te identificeren.</span><span class="sxs-lookup"><span data-stu-id="d84b0-183">XPath is a standard language that is designed to identify parts of an XML document.</span></span> <span data-ttu-id="d84b0-184">Zie [XPath-verwijzing](/dotnet/standard/data/xml/select-nodes-using-xpath-navigation) en het gedeelte selectie filters van de [gebeurtenis selectie](/previous-versions//aa385231(v=vs.85))voor meer informatie over de XPath-taal.</span><span class="sxs-lookup"><span data-stu-id="d84b0-184">For more information about the XPath language, see [XPath Reference](/dotnet/standard/data/xml/select-nodes-using-xpath-navigation) and the Selection Filters section of [Event Selection](/previous-versions//aa385231(v=vs.85)).</span></span>

## <span data-ttu-id="d84b0-185">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d84b0-185">RELATED LINKS</span></span>

[<span data-ttu-id="d84b0-186">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="d84b0-186">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)
