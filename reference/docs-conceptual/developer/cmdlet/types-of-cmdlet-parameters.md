---
ms.date: 09/13/2016
ms.topic: reference
title: Typen cmdlet-parameters
description: Typen cmdlet-parameters
ms.openlocfilehash: 8daaa3c778396e06a826de3b93e0610c51160fb4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660492"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="c6448-103">Typen cmdlet-parameters</span><span class="sxs-lookup"><span data-stu-id="c6448-103">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="c6448-104">In dit onderwerp worden de verschillende typen para meters beschreven die u in cmdlets kunt declareren.</span><span class="sxs-lookup"><span data-stu-id="c6448-104">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="c6448-105">Cmdlet-para meters kunnen positioneel, benoemde, required, optional of switch-para meters zijn.</span><span class="sxs-lookup"><span data-stu-id="c6448-105">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="c6448-106">Positionele en benoemde para meters</span><span class="sxs-lookup"><span data-stu-id="c6448-106">Positional and Named Parameters</span></span>

<span data-ttu-id="c6448-107">Alle cmdlet-para meters hebben de naam of positionele para meters.</span><span class="sxs-lookup"><span data-stu-id="c6448-107">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="c6448-108">Voor een benoemde para meter moet u de parameter naam en het argument typen bij het aanroepen van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c6448-108">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="c6448-109">Een positionele para meter vereist alleen dat u de argumenten in relatieve volg orde typt.</span><span class="sxs-lookup"><span data-stu-id="c6448-109">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="c6448-110">Het systeem wijst vervolgens het eerste ongenoemde argument toe aan de eerste positie parameter.</span><span class="sxs-lookup"><span data-stu-id="c6448-110">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="c6448-111">Het systeem wijst het tweede ongenoemde argument toe aan de tweede niet-genaamde para meter, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="c6448-111">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="c6448-112">Standaard zijn alle cmdlet-para meters benoemde para meters.</span><span class="sxs-lookup"><span data-stu-id="c6448-112">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="c6448-113">Als u een benoemde para meter wilt definiëren, laat u het `Position` sleutel woord in de declaratie van het **parameter** kenmerk weg, zoals wordt weer gegeven in de volgende parameter declaratie.</span><span class="sxs-lookup"><span data-stu-id="c6448-113">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="c6448-114">Als u een positionele para meter wilt definiëren, voegt u het `Position` tref woord toe aan de declaratie van het parameter kenmerk en geeft u een positie op.</span><span class="sxs-lookup"><span data-stu-id="c6448-114">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="c6448-115">In het volgende voor beeld `UserName` wordt de para meter gedeclareerd als een positionele para meter met positie 0.</span><span class="sxs-lookup"><span data-stu-id="c6448-115">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="c6448-116">Dit betekent dat het eerste argument van de aanroep automatisch wordt gebonden aan deze para meter.</span><span class="sxs-lookup"><span data-stu-id="c6448-116">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> <span data-ttu-id="c6448-117">Goede cmdlet-ontwerp beveelt aan dat de meest gebruikte para meters worden gedeclareerd als positionele para meters, zodat de gebruiker de naam van de para meter niet hoeft in te voeren wanneer de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c6448-117">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="c6448-118">Positionele en benoemde para meters accepteren enkelvoudige argumenten of meerdere argumenten, gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="c6448-118">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="c6448-119">Meerdere argumenten zijn alleen toegestaan als de para meter een verzameling accepteert, zoals een matrix met teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="c6448-119">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="c6448-120">U kunt positionele en benoemde para meters in dezelfde cmdlet combi neren.</span><span class="sxs-lookup"><span data-stu-id="c6448-120">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="c6448-121">In dit geval haalt het systeem eerst de benoemde argumenten op en probeert vervolgens de resterende niet-benoemde argumenten toe te wijzen aan de positionele para meters.</span><span class="sxs-lookup"><span data-stu-id="c6448-121">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="c6448-122">De volgende opdrachten tonen de verschillende manieren waarop u één en meerdere argumenten kunt opgeven voor de para meters van de `Get-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c6448-122">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="c6448-123">U ziet dat in de laatste twee voor beelden **-name** niet moet worden opgegeven omdat de `Name` para meter is gedefinieerd als een positionele para meter.</span><span class="sxs-lookup"><span data-stu-id="c6448-123">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="c6448-124">Verplichte en optionele para meters</span><span class="sxs-lookup"><span data-stu-id="c6448-124">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="c6448-125">U kunt ook cmdlet-para meters definiëren als verplichte of optionele para meters.</span><span class="sxs-lookup"><span data-stu-id="c6448-125">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="c6448-126">(Er moet een verplichte para meter worden opgegeven voordat de Windows Power shell-runtime de cmdlet aanroept.)  Standaard worden para meters gedefinieerd als optioneel.</span><span class="sxs-lookup"><span data-stu-id="c6448-126">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="c6448-127">Als u een verplichte para meter wilt definiëren, voegt u het `Mandatory` sleutel woord in de declaratie van het parameter kenmerk toe en stelt u het in op `true` , zoals wordt weer gegeven in de volgende parameter declaratie.</span><span class="sxs-lookup"><span data-stu-id="c6448-127">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="c6448-128">Als u een optionele para meter wilt definiëren, laat u het `Mandatory` sleutel woord in de declaratie van het **parameter** kenmerk weg, zoals wordt weer gegeven in de volgende parameter declaratie.</span><span class="sxs-lookup"><span data-stu-id="c6448-128">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="c6448-129">Switch parameters</span><span class="sxs-lookup"><span data-stu-id="c6448-129">Switch Parameters</span></span>

<span data-ttu-id="c6448-130">Windows Power shell biedt een [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) -type waarmee u een para meter kunt definiëren waarvan de waarde automatisch wordt ingesteld `false` als de para meter niet wordt opgegeven wanneer de cmdlet wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="c6448-130">Windows PowerShell provides a [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="c6448-131">Als dat mogelijk is, gebruikt u switch-para meters in plaats van Boole-para meters.</span><span class="sxs-lookup"><span data-stu-id="c6448-131">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="c6448-132">Bekijk het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="c6448-132">Consider the following sample.</span></span> <span data-ttu-id="c6448-133">Verschillende Windows Power shell-cmdlets geven standaard geen uitvoer object omlaag in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="c6448-133">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="c6448-134">Deze cmdlets hebben echter een `PassThru` Switch parameter die het standaard gedrag overschrijft.</span><span class="sxs-lookup"><span data-stu-id="c6448-134">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="c6448-135">Als de `PassThru` para meter wordt opgegeven wanneer deze cmdlets worden aangeroepen, retourneert de cmdlet een uitvoer object naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="c6448-135">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="c6448-136">Als u de para meter nodig hebt om een standaard waarde te hebben `true` als de para meter niet is opgegeven in de aanroep, overweeg dan om de gevoel van de para meter te omkeren.</span><span class="sxs-lookup"><span data-stu-id="c6448-136">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="c6448-137">Voor het voor beeld moet u in plaats van het parameter kenmerk in te stellen op een Booleaanse waarde van `true` , de eigenschap declareren als het type [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) en vervolgens de standaard waarde van de para meter in te stellen op `false` .</span><span class="sxs-lookup"><span data-stu-id="c6448-137">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="c6448-138">Als u een para meter switch wilt definiëren, declareert u de eigenschap als het type [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) , zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="c6448-138">To define a switch parameter, declare the property as the [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="c6448-139">Als u de cmdlet wilt uitvoeren op de para meter wanneer deze is opgegeven, gebruikt u de volgende structuur binnen een van de invoer verwerkings methoden.</span><span class="sxs-lookup"><span data-stu-id="c6448-139">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a><span data-ttu-id="c6448-140">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c6448-140">See Also</span></span>

[<span data-ttu-id="c6448-141">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="c6448-141">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
