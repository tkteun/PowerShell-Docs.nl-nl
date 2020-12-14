---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Error
ms.openlocfilehash: 7e4f4adf60a4f6386c646d92ada0003f239f05f4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705713"
---
# <span data-ttu-id="fa7a2-102">Get-Error</span><span class="sxs-lookup"><span data-stu-id="fa7a2-102">Get-Error</span></span>

## <span data-ttu-id="fa7a2-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="fa7a2-103">SYNOPSIS</span></span>

<span data-ttu-id="fa7a2-104">Hiermee worden de meest recente fout berichten uit de huidige sessie opgehaald en weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-104">Gets and displays the most recent error messages from the current session.</span></span>

## <span data-ttu-id="fa7a2-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="fa7a2-105">SYNTAX</span></span>

### <span data-ttu-id="fa7a2-106">Nieuwste (standaard)</span><span class="sxs-lookup"><span data-stu-id="fa7a2-106">Newest (Default)</span></span>

```
Get-Error [[-Newest] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="fa7a2-107">Fout</span><span class="sxs-lookup"><span data-stu-id="fa7a2-107">Error</span></span>

```
Get-Error [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="fa7a2-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fa7a2-108">DESCRIPTION</span></span>

<span data-ttu-id="fa7a2-109">Met de `Get-Error` cmdlet wordt een **PSExtendedError** -object opgehaald dat de huidige fout Details vertegenwoordigt van de laatste fout die in de sessie is opgetreden.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-109">The `Get-Error` cmdlet gets a **PSExtendedError** object that represents the current error details from the last error that occurred in the session.</span></span>

<span data-ttu-id="fa7a2-110">U kunt gebruiken `Get-Error` om een opgegeven aantal fouten weer te geven dat in de huidige sessie is opgetreden met de **nieuwste** para meter.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-110">You can use `Get-Error` to display a specified number of errors that have occurred in the current session using the **Newest** parameter.</span></span>

<span data-ttu-id="fa7a2-111">De `Get-Error` cmdlet ontvangt ook fout objecten uit een verzameling, zoals `$Error` , om meerdere fouten van de huidige sessie weer te geven.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-111">The `Get-Error` cmdlet also receives error objects from a collection, such as `$Error`, to display multiple errors from the current session.</span></span>

## <span data-ttu-id="fa7a2-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="fa7a2-112">EXAMPLES</span></span>

### <span data-ttu-id="fa7a2-113">Voor beeld 1: de meest recente fout Details ophalen</span><span class="sxs-lookup"><span data-stu-id="fa7a2-113">Example 1: Get the most recent error details</span></span>

<span data-ttu-id="fa7a2-114">In dit voor beeld `Get-Error` worden de details weer gegeven van de meest recente fout die is opgetreden in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-114">In this example, `Get-Error` displays the details of the most recent error that occurred in the current session.</span></span>

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

### <span data-ttu-id="fa7a2-115">Voor beeld 2: het opgegeven aantal fout berichten ophalen dat is opgetreden in de huidige sessie</span><span class="sxs-lookup"><span data-stu-id="fa7a2-115">Example 2: Get the specified number of error messages that occurred in the current session</span></span>

<span data-ttu-id="fa7a2-116">In dit voor beeld ziet u hoe u `Get-Error` met de **nieuwste** para meter kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-116">This example shows how to use `Get-Error` with the **Newest** parameter.</span></span> <span data-ttu-id="fa7a2-117">In dit voor beeld retourneert **nieuwste** de details van de drie nieuwste fouten die zijn opgetreden tijdens deze sessie.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-117">In this example, **Newest** returns the details of the 3 newest errors that occurred in this session.</span></span>

```powershell
Get-Error -Newest 3
```

### <span data-ttu-id="fa7a2-118">Voor beeld 3: een verzameling fouten verzenden om gedetailleerde berichten te ontvangen</span><span class="sxs-lookup"><span data-stu-id="fa7a2-118">Example 3: Send a collection of errors to receive detailed messages</span></span>

<span data-ttu-id="fa7a2-119">De `$Error` Automatische variabele bevat een matrix met fout objecten in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-119">The `$Error` automatic variable contains an array of error objects in the current session.</span></span> <span data-ttu-id="fa7a2-120">De matrix van objecten kan worden gepiped om `Get-Error` gedetailleerde fout berichten te ontvangen.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-120">The array of objects can be piped to `Get-Error` to receive detailed error messages.</span></span>

<span data-ttu-id="fa7a2-121">In dit voor beeld `$Error` wordt het pipet naar de `Get-Error` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-121">In this example, `$Error` is piped to the `Get-Error` cmdlet.</span></span> <span data-ttu-id="fa7a2-122">het resultaat is een lijst met gedetailleerde fout berichten, vergelijkbaar met het resultaat van voor beeld 1.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-122">the result is list of detailed error messages, similar to the result of Example 1.</span></span>

```powershell
$Error | Get-Error
```

## <span data-ttu-id="fa7a2-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fa7a2-123">PARAMETERS</span></span>

### <span data-ttu-id="fa7a2-124">-Nieuwste</span><span class="sxs-lookup"><span data-stu-id="fa7a2-124">-Newest</span></span>

<span data-ttu-id="fa7a2-125">Hiermee geeft u het aantal fouten op dat moet worden weer gegeven tijdens de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-125">Specifies the number of errors to display that have occurred in the current session.</span></span>

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

### <span data-ttu-id="fa7a2-126">-Input object</span><span class="sxs-lookup"><span data-stu-id="fa7a2-126">-InputObject</span></span>

<span data-ttu-id="fa7a2-127">Deze para meter wordt gebruikt voor de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-127">This parameter is used for pipeline input.</span></span>

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

### <span data-ttu-id="fa7a2-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fa7a2-128">CommonParameters</span></span>

<span data-ttu-id="fa7a2-129">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fa7a2-130">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fa7a2-131">INVOER</span><span class="sxs-lookup"><span data-stu-id="fa7a2-131">INPUTS</span></span>

### <span data-ttu-id="fa7a2-132">PSObject</span><span class="sxs-lookup"><span data-stu-id="fa7a2-132">PSObject</span></span>

<span data-ttu-id="fa7a2-133">Ondersteunt invoer van elk **PSObject**, maar de resultaten variëren, tenzij een **ErrorRecord** of een **uitzonderings** object worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-133">Supports input from any **PSObject**, but results vary unless either an **ErrorRecord** or **Exception** object are supplied.</span></span>

## <span data-ttu-id="fa7a2-134">UITVOER</span><span class="sxs-lookup"><span data-stu-id="fa7a2-134">OUTPUTS</span></span>

### <span data-ttu-id="fa7a2-135">System. Management. Automation. ErrorRecord # PSExtendedError</span><span class="sxs-lookup"><span data-stu-id="fa7a2-135">System.Management.Automation.ErrorRecord#PSExtendedError</span></span>

<span data-ttu-id="fa7a2-136">Uitvoer in een **PSExtendedError** -object.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-136">Output in a **PSExtendedError** object.</span></span>

## <span data-ttu-id="fa7a2-137">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="fa7a2-137">NOTES</span></span>

<span data-ttu-id="fa7a2-138">`Get-Error` accepteert invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-138">`Get-Error` accepts pipeline input.</span></span> <span data-ttu-id="fa7a2-139">Bijvoorbeeld `$Error | Get-Error`.</span><span class="sxs-lookup"><span data-stu-id="fa7a2-139">For example, `$Error | Get-Error`.</span></span>

## <span data-ttu-id="fa7a2-140">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="fa7a2-140">RELATED LINKS</span></span>

[<span data-ttu-id="fa7a2-141">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="fa7a2-141">about_Try_Catch_Finally</span></span>](../Microsoft.PowerShell.Core/About/about_Try_Catch_Finally.md)
