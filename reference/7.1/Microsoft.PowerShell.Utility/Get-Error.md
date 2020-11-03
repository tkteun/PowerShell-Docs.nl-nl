---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Error
ms.openlocfilehash: c29115a65b46d38039d78b10eee293e6944cede5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250224"
---
# <span data-ttu-id="2a979-103">Get-Error</span><span class="sxs-lookup"><span data-stu-id="2a979-103">Get-Error</span></span>

## <span data-ttu-id="2a979-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2a979-104">SYNOPSIS</span></span>

<span data-ttu-id="2a979-105">Hiermee worden de meest recente fout berichten uit de huidige sessie opgehaald en weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2a979-105">Gets and displays the most recent error messages from the current session.</span></span>

## <span data-ttu-id="2a979-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="2a979-106">SYNTAX</span></span>

### <span data-ttu-id="2a979-107">Nieuwste (standaard)</span><span class="sxs-lookup"><span data-stu-id="2a979-107">Newest (Default)</span></span>

```
Get-Error [[-Newest] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="2a979-108">Fout</span><span class="sxs-lookup"><span data-stu-id="2a979-108">Error</span></span>

```
Get-Error [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="2a979-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="2a979-109">DESCRIPTION</span></span>

<span data-ttu-id="2a979-110">Met de `Get-Error` cmdlet wordt een **PSExtendedError** -object opgehaald dat de huidige fout Details vertegenwoordigt van de laatste fout die in de sessie is opgetreden.</span><span class="sxs-lookup"><span data-stu-id="2a979-110">The `Get-Error` cmdlet gets a **PSExtendedError** object that represents the current error details from the last error that occurred in the session.</span></span>

<span data-ttu-id="2a979-111">U kunt gebruiken `Get-Error` om een opgegeven aantal fouten weer te geven dat in de huidige sessie is opgetreden met de **nieuwste** para meter.</span><span class="sxs-lookup"><span data-stu-id="2a979-111">You can use `Get-Error` to display a specified number of errors that have occurred in the current session using the **Newest** parameter.</span></span>

<span data-ttu-id="2a979-112">De `Get-Error` cmdlet ontvangt ook fout objecten uit een verzameling, zoals `$Error` , om meerdere fouten van de huidige sessie weer te geven.</span><span class="sxs-lookup"><span data-stu-id="2a979-112">The `Get-Error` cmdlet also receives error objects from a collection, such as `$Error`, to display multiple errors from the current session.</span></span>

## <span data-ttu-id="2a979-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2a979-113">EXAMPLES</span></span>

### <span data-ttu-id="2a979-114">Voor beeld 1: de meest recente fout Details ophalen</span><span class="sxs-lookup"><span data-stu-id="2a979-114">Example 1: Get the most recent error details</span></span>

<span data-ttu-id="2a979-115">In dit voor beeld `Get-Error` worden de details weer gegeven van de meest recente fout die is opgetreden in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2a979-115">In this example, `Get-Error` displays the details of the most recent error that occurred in the current session.</span></span>

```powershell
Get-Childitem -path /NoRealDirectory
Get-Error
```

```
Get-ChildItem: Cannot find path 'C:\NoRealDirectory' because it does not exist.

Exception             :
    ErrorRecord          :
        Exception             :
            Message : Cannot find path 'C:\NoRealDirectory' because it does not exist.
            HResult : -2146233087
        TargetObject          : C:\NoRealDirectory
        CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [], ParentContainsErrorRecordException
        FullyQualifiedErrorId : PathNotFound
    ItemName             : C:\NoRealDirectory
    SessionStateCategory : Drive
    TargetSite           :
        Name          : GetChildItems
        DeclaringType : System.Management.Automation.SessionStateInternal
        MemberType    : Method
        Module        : System.Management.Automation.dll
    StackTrace           :
   at System.Management.Automation.SessionStateInternal.GetChildItems(String path, Boolean recurse, UInt32 depth,
CmdletProviderContext context)
   at System.Management.Automation.ChildItemCmdletProviderIntrinsics.Get(String path, Boolean recurse, UInt32
depth, CmdletProviderContext context)
   at Microsoft.PowerShell.Commands.GetChildItemCommand.ProcessRecord()
    Message              : Cannot find path 'C:\NoRealDirectory' because it does not exist.
    Source               : System.Management.Automation
    HResult              : -2146233087
TargetObject          : C:\NoRealDirectory
CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [Get-ChildItem], ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
InvocationInfo        :
    MyCommand        : Get-ChildItem
    ScriptLineNumber : 1
    OffsetInLine     : 1
    HistoryId        : 57
    Line             : Get-Childitem -path c:\NoRealDirectory
    PositionMessage  : At line:1 char:1
                       + Get-Childitem -path c:\NoRealDirectory
                       + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    InvocationName   : Get-Childitem
    CommandOrigin    : Internal
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo :
```

### <span data-ttu-id="2a979-116">Voor beeld 2: het opgegeven aantal fout berichten ophalen dat is opgetreden in de huidige sessie</span><span class="sxs-lookup"><span data-stu-id="2a979-116">Example 2: Get the specified number of error messages that occurred in the current session</span></span>

<span data-ttu-id="2a979-117">In dit voor beeld ziet u hoe u `Get-Error` met de **nieuwste** para meter kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2a979-117">This example shows how to use `Get-Error` with the **Newest** parameter.</span></span> <span data-ttu-id="2a979-118">In dit voor beeld retourneert **nieuwste** de details van de drie nieuwste fouten die zijn opgetreden tijdens deze sessie.</span><span class="sxs-lookup"><span data-stu-id="2a979-118">In this example, **Newest** returns the details of the 3 newest errors that occurred in this session.</span></span>

```powershell
Get-Error -Newest 3
```

### <span data-ttu-id="2a979-119">Voor beeld 3: een verzameling fouten verzenden om gedetailleerde berichten te ontvangen</span><span class="sxs-lookup"><span data-stu-id="2a979-119">Example 3: Send a collection of errors to receive detailed messages</span></span>

<span data-ttu-id="2a979-120">De `$Error` Automatische variabele bevat een matrix met fout objecten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2a979-120">The `$Error` automatic variable contains an array of error objects in the current session.</span></span> <span data-ttu-id="2a979-121">De matrix van objecten kan worden gepiped om `Get-Error` gedetailleerde fout berichten te ontvangen.</span><span class="sxs-lookup"><span data-stu-id="2a979-121">The array of objects can be piped to `Get-Error` to receive detailed error messages.</span></span>

<span data-ttu-id="2a979-122">In dit voor beeld `$Error` wordt het pipet naar de `Get-Error` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2a979-122">In this example, `$Error` is piped to the `Get-Error` cmdlet.</span></span> <span data-ttu-id="2a979-123">het resultaat is een lijst met gedetailleerde fout berichten, vergelijkbaar met het resultaat van voor beeld 1.</span><span class="sxs-lookup"><span data-stu-id="2a979-123">the result is list of detailed error messages, similar to the result of Example 1.</span></span>

```powershell
$Error | Get-Error
```

## <span data-ttu-id="2a979-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2a979-124">PARAMETERS</span></span>

### <span data-ttu-id="2a979-125">-Nieuwste</span><span class="sxs-lookup"><span data-stu-id="2a979-125">-Newest</span></span>

<span data-ttu-id="2a979-126">Hiermee geeft u het aantal fouten op dat moet worden weer gegeven tijdens de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2a979-126">Specifies the number of errors to display that have occurred in the current session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Newest
Aliases: Last

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2a979-127">-Input object</span><span class="sxs-lookup"><span data-stu-id="2a979-127">-InputObject</span></span>

<span data-ttu-id="2a979-128">Deze para meter wordt gebruikt voor de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="2a979-128">This parameter is used for pipeline input.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Error
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2a979-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2a979-129">CommonParameters</span></span>

<span data-ttu-id="2a979-130">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2a979-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2a979-131">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2a979-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2a979-132">INVOER</span><span class="sxs-lookup"><span data-stu-id="2a979-132">INPUTS</span></span>

### <span data-ttu-id="2a979-133">PSObject</span><span class="sxs-lookup"><span data-stu-id="2a979-133">PSObject</span></span>

<span data-ttu-id="2a979-134">Ondersteunt invoer van elk **PSObject** , maar de resultaten variëren, tenzij een **ErrorRecord** of een **uitzonderings** object worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2a979-134">Supports input from any **PSObject** , but results vary unless either an **ErrorRecord** or **Exception** object are supplied.</span></span>

## <span data-ttu-id="2a979-135">UITVOER</span><span class="sxs-lookup"><span data-stu-id="2a979-135">OUTPUTS</span></span>

### <span data-ttu-id="2a979-136">System. Management. Automation. ErrorRecord # PSExtendedError</span><span class="sxs-lookup"><span data-stu-id="2a979-136">System.Management.Automation.ErrorRecord#PSExtendedError</span></span>

<span data-ttu-id="2a979-137">Uitvoer in een **PSExtendedError** -object.</span><span class="sxs-lookup"><span data-stu-id="2a979-137">Output in a **PSExtendedError** object.</span></span>

## <span data-ttu-id="2a979-138">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="2a979-138">NOTES</span></span>

<span data-ttu-id="2a979-139">`Get-Error` accepteert invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="2a979-139">`Get-Error` accepts pipeline input.</span></span> <span data-ttu-id="2a979-140">Bijvoorbeeld `$Error | Get-Error`.</span><span class="sxs-lookup"><span data-stu-id="2a979-140">For example, `$Error | Get-Error`.</span></span>

## <span data-ttu-id="2a979-141">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="2a979-141">RELATED LINKS</span></span>

[<span data-ttu-id="2a979-142">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="2a979-142">about_Try_Catch_Finally</span></span>](../Microsoft.PowerShell.Core/About/about_Try_Catch_Finally.md)
