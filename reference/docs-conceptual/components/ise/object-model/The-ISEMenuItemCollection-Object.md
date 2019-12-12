---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Het ISEMenuItemCollection-object
ms.openlocfilehash: b3795af1a6ed61ed6e371e5fc20cc4e95f643fd4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030537"
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="d0c3e-103">Het ISEMenuItemCollection-object</span><span class="sxs-lookup"><span data-stu-id="d0c3e-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="d0c3e-104">Een **ISEMenuItemCollection** -object is een verzameling **ISEMenuItem** -objecten.</span><span class="sxs-lookup"><span data-stu-id="d0c3e-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="d0c3e-105">Het is een exemplaar van de klasse micro soft. Power shell. host. ISE. ISEMenuItemCollection.</span><span class="sxs-lookup"><span data-stu-id="d0c3e-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="d0c3e-106">Een voor beeld is het object **$psISE. CurrentPowerShellTab. AddOnsMenu. submenu's** dat wordt gebruikt voor het aanpassen van het **invoeg** menu in Windows Power shell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="d0c3e-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="d0c3e-107">Methode</span><span class="sxs-lookup"><span data-stu-id="d0c3e-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="d0c3e-108">\(teken reeks weergave naam, System. Management. Automation. script block-actie, System. Windows. input. toets-beweging toevoegen \)</span><span class="sxs-lookup"><span data-stu-id="d0c3e-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="d0c3e-109">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="d0c3e-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d0c3e-110">Hiermee wordt een menu opdracht toegevoegd aan de verzameling.</span><span class="sxs-lookup"><span data-stu-id="d0c3e-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="d0c3e-111">**DisplayName** De weergave naam van het menu dat moet worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="d0c3e-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="d0c3e-112">**Actie** Het object **System. Management. Automation. script Block** dat de actie specificeert die is gekoppeld aan deze menu opdracht.</span><span class="sxs-lookup"><span data-stu-id="d0c3e-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="d0c3e-113">**Snelkoppeling** De sneltoets voor de actie.</span><span class="sxs-lookup"><span data-stu-id="d0c3e-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="d0c3e-114">**Retourneert** Het ISEMenuItem-object dat zojuist is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="d0c3e-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="d0c3e-115">\(\) wissen</span><span class="sxs-lookup"><span data-stu-id="d0c3e-115">Clear\(\)</span></span>

<span data-ttu-id="d0c3e-116">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="d0c3e-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d0c3e-117">Hiermee verwijdert u alle submenu's uit de menu opdracht.</span><span class="sxs-lookup"><span data-stu-id="d0c3e-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="d0c3e-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d0c3e-118">See Also</span></span>

- [<span data-ttu-id="d0c3e-119">Het ISEMenuItem-object</span><span class="sxs-lookup"><span data-stu-id="d0c3e-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="d0c3e-120">Doel van het Windows PowerShell ISE scripting object model</span><span class="sxs-lookup"><span data-stu-id="d0c3e-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="d0c3e-121">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="d0c3e-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
