---
title: Typen van de Cmdlet-Parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: 59921a92661482b8d518b82f490c9879643543bb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849516"
---
# <a name="types-of-cmdlet-parameters"></a><span data-ttu-id="dc3aa-102">Typen cmdlet-parameters</span><span class="sxs-lookup"><span data-stu-id="dc3aa-102">Types of Cmdlet Parameters</span></span>

<span data-ttu-id="dc3aa-103">Dit onderwerp beschrijft de verschillende typen parameters die u in de cmdlets aangeven kunt.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-103">This topic describes the different types of parameters that you can declare in cmdlets.</span></span> <span data-ttu-id="dc3aa-104">Cmdlet-parameters worden positionele, met de naam, vereist, optioneel of verwissel de parameters.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-104">Cmdlet parameters can be positional, named, required, optional, or switch parameters.</span></span>

## <a name="positional-and-named-parameters"></a><span data-ttu-id="dc3aa-105">Positionele en benoemde Parameters</span><span class="sxs-lookup"><span data-stu-id="dc3aa-105">Positional and Named Parameters</span></span>

<span data-ttu-id="dc3aa-106">Alle cmdlet-parameters zijn benoemde of positionele parameters.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-106">All cmdlet parameters are either named or positional parameters.</span></span> <span data-ttu-id="dc3aa-107">Een benoemde parameter is vereist dat u de parameternaam en argument invoeren bij het aanroepen van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-107">A named parameter requires that you type the parameter name and argument when calling the cmdlet.</span></span> <span data-ttu-id="dc3aa-108">Een positionele parameter is alleen vereist dat u de argumenten in de juiste volgorde typen.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-108">A positional parameter requires only that you type the arguments in relative order.</span></span> <span data-ttu-id="dc3aa-109">Het systeem wordt het eerste argument naamloze vervolgens toegewezen aan de eerste positionele parameter.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-109">The system then maps the first unnamed argument to the first positional parameter.</span></span> <span data-ttu-id="dc3aa-110">Het systeem het tweede argument naamloze toegewezen aan de tweede naamloze parameter, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-110">The system maps the second unnamed argument to the second unnamed parameter, and so on.</span></span> <span data-ttu-id="dc3aa-111">Standaard worden alle parameters van de cmdlet benoemde parameters.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-111">By default, all cmdlet parameters are named parameters.</span></span>

<span data-ttu-id="dc3aa-112">Voor het definiëren van een benoemde parameter, laat de `Position` sleutelwoord in de **Parameter** declaratie van het kenmerk zoals wordt weergegeven in de volgende parameterdeclaratie.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-112">To define a named parameter, omit the `Position` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="dc3aa-113">Voor het definiëren van een positionele parameter toevoegen de `Position` sleutelwoord in de Parameter declaratie van het kenmerk en geef vervolgens een positie.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-113">To define a positional parameter, add the `Position` keyword in the Parameter attribute declaration, and then specify a position.</span></span> <span data-ttu-id="dc3aa-114">In het volgende voorbeeld wordt de `UserName` parameter is gedeclareerd als een positionele parameter met de positie 0.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-114">In the following sample, the `UserName` parameter is declared as a positional parameter with position 0.</span></span> <span data-ttu-id="dc3aa-115">Dit betekent dat het eerste argument van de aanroep automatisch worden gekoppeld aan deze parameter.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-115">This means that the first argument of the call will be automatically bound to this parameter.</span></span>

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
> <span data-ttu-id="dc3aa-116">Goede cmdlet ontwerp raadt aan dat de meest gebruikte parameters worden gedeclareerd als positionele parameters, zodat de gebruiker heeft geen naam van de parameter invoeren wanneer de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-116">Good cmdlet design recommends that the most-used parameters be declared as positional parameters so that the user does not have to enter the parameter name when the cmdlet is run.</span></span>

<span data-ttu-id="dc3aa-117">Positionele en benoemde parameters accepteren één argumenten of meerdere argumenten gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-117">Positional and named parameters accept single arguments or multiple arguments separated by commas.</span></span> <span data-ttu-id="dc3aa-118">Meerdere argumenten zijn alleen toegestaan als de parameter een verzameling, zoals een matrix met tekenreeksen accepteert.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-118">Multiple arguments are allowed only if the parameter accepts a collection such as an array of strings.</span></span> <span data-ttu-id="dc3aa-119">Positionele en benoemde parameters in dezelfde cmdlet kan worden gecombineerd.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-119">You may mix positional and named parameters in the same cmdlet.</span></span> <span data-ttu-id="dc3aa-120">In dit geval wordt de benoemde argumenten eerst opgehaald en vervolgens probeert toe te wijzen de resterende benoemde argumenten aan de positionele parameters.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-120">In this case, the system retrieves the named arguments first, and then attempts to map the remaining unnamed arguments to the positional parameters.</span></span>

<span data-ttu-id="dc3aa-121">De volgende opdrachten tonen de verschillende manieren waarop u en één of meerdere argumenten voor de parameters van opgeven kunt de `Get-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-121">The following commands show the different ways in which you can specify single and multiple arguments for the parameters of the `Get-Command` cmdlet.</span></span> <span data-ttu-id="dc3aa-122">U ziet dat in de laatste twee bewakingen, **-naam** hoeft niet te worden opgegeven omdat de `Name` parameter wordt gedefinieerd als een positionele parameter.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-122">Notice that in the last two samples, **-name** does not need to be specified because the `Name` parameter is defined as a positional parameter.</span></span>

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a><span data-ttu-id="dc3aa-123">Verplichte en optionele Parameters</span><span class="sxs-lookup"><span data-stu-id="dc3aa-123">Mandatory and Optional Parameters</span></span>

<span data-ttu-id="dc3aa-124">U kunt ook de cmdlet-parameters definiëren als verplicht of optioneel parameters.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-124">You can also define cmdlet parameters as mandatory or optional parameters.</span></span> <span data-ttu-id="dc3aa-125">(Een verplichte parameter moet worden opgegeven voordat de runtime van de Windows PowerShell de cmdlet aanroept.)  Parameters worden gedefinieerd als optionele standaard.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-125">(A mandatory parameter must be specified before the Windows PowerShell runtime invokes the cmdlet.)  By default, parameters are defined as optional.</span></span>

<span data-ttu-id="dc3aa-126">Toevoegen voor het definiëren van een verplichte parameter, de `Mandatory` sleutelwoord in de Parameter declaratie van het kenmerk en stel deze in op `true`, zoals weergegeven in de volgende parameterdeclaratie.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-126">To define a mandatory parameter, add the `Mandatory` keyword in the Parameter attribute declaration, and set it to `true`, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

<span data-ttu-id="dc3aa-127">Voor het definiëren van een optionele parameter, laat de `Mandatory` sleutelwoord in de **Parameter** declaratie van het kenmerk zoals wordt weergegeven in de volgende parameterdeclaratie.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-127">To define an optional parameter, omit the `Mandatory` keyword in the **Parameter** attribute declaration, as shown in the following parameter declaration.</span></span>

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a><span data-ttu-id="dc3aa-128">Verwissel de Parameters</span><span class="sxs-lookup"><span data-stu-id="dc3aa-128">Switch Parameters</span></span>

<span data-ttu-id="dc3aa-129">Windows PowerShell biedt een [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) type waarmee u een parameter definiëren waarvan de waarde automatisch is ingesteld op `false` als de parameter niet wordt opgegeven wanneer de cmdlet is met de naam.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-129">Windows PowerShell provides a [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) type that allows you to define a parameter whose value is automatically set to `false` if the parameter is not specified when the cmdlet is called.</span></span> <span data-ttu-id="dc3aa-130">Gebruik indien mogelijk de switch-parameters in plaats van Booleaanse parameters.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-130">Whenever possible, use switch parameters in place of Boolean parameters.</span></span>

<span data-ttu-id="dc3aa-131">Houd rekening met het volgende voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-131">Consider the following sample.</span></span> <span data-ttu-id="dc3aa-132">Standaard worden een object op in de pijplijn in verschillende Windows PowerShell-cmdlets niet geslaagd.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-132">By default, several Windows PowerShell cmdlets do not pass an output object down the pipeline.</span></span> <span data-ttu-id="dc3aa-133">Deze cmdlets hebben echter een `PassThru` switch-parameter die het standaardgedrag overschrijft.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-133">However, these cmdlets have a `PassThru` switch parameter that overrides the default behavior.</span></span> <span data-ttu-id="dc3aa-134">Als de `PassThru` parameter is opgegeven wanneer deze cmdlets worden aangeroepen, wordt de cmdlet retourneert een uitvoerobject aan de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-134">If the `PassThru` parameter is specified when these cmdlets are called, the cmdlet returns an output object to the pipeline.</span></span>

<span data-ttu-id="dc3aa-135">Als u de parameter een standaardwaarde van `true` als de parameter niet is opgegeven in de aanroep, houd rekening met het gevoel van de parameter omkeren.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-135">If you need the parameter to have a default value of `true` when the parameter is not specified in the call, consider reversing the sense of the parameter.</span></span> <span data-ttu-id="dc3aa-136">Voor het voorbeeld in plaats van de parameterkenmerk instelt op een Booleaanse waarde `true`, de eigenschap declareert de [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) typt, en stel de standaardwaarde van de parameter `false`.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-136">For sample, instead of setting the parameter attribute to a Boolean value of `true`, declare the property as the [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, and then set the default value of the parameter to `false`.</span></span>

<span data-ttu-id="dc3aa-137">Voor het definiëren van een switch-parameter, de eigenschap als declareren de [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) typt, zoals wordt weergegeven in het volgende voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-137">To define a switch parameter, declare the property as the [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, as shown in the following sample.</span></span>

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

<span data-ttu-id="dc3aa-138">Als u de cmdlet reageren op de parameter wanneer deze is opgegeven, gebruik de volgende structuur binnen een van de invoer verwerkingsmethoden.</span><span class="sxs-lookup"><span data-stu-id="dc3aa-138">To make the cmdlet act on the parameter when it is specified, use the following structure within one of the input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dc3aa-139">Zie ook</span><span class="sxs-lookup"><span data-stu-id="dc3aa-139">See Also</span></span>

[<span data-ttu-id="dc3aa-140">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="dc3aa-140">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
