---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 11b5e36f703c242e0bc820ab19d11d39305fa90c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187908"
---
# <a name="network-switch-management-with-powershell"></a>Beheer van netwerkswitch met PowerShell

De **Get-NetworkSwitchEthernetPort** cmdlet retourneert nu de volgende aanvullende informatie met exemplaren:

- IP-adres – het IP-adres die zijn gekoppeld aan de poort
- PortMode: de poortmodus: toegang, route of trunk
- AccessVLAN – de de VLAN-ID die is gekoppeld aan deze poort in de toegangsmodus
- TrunkedVLANList – een lijst met de id van VLAN's die zijn gekoppeld aan deze poort in de trunkmodus

## <a name="fundamental-network-switch-management-with-windows-powershell"></a>Fundamentele netwerkbeheer switch met Windows PowerShell

De netwerkswitch-cmdlets die zijn geïntroduceerd in WMF 5.0, kunt u switch, virtuele LAN (VLAN) en basic Layer 2-switch-poort netwerkconfiguratie van toepassing op Windows Server 2012 R2-logo gecertificeerde netwerkswitches. Microsoft blijft doorgevoerd in de ondersteuning van de [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) visie Layer (DAL), en waarde voor onze klanten en partners in deze ruimte weergeven. Met deze cmdlets kunt u uitvoeren:

- Global switch configuratie, zoals:
    - Naam van de host
    - Set switch banner
    - Configuratie blijven behouden
    - Functie- of uitschakelen

- VLAN-configuratie:
    - Maken of verwijderen van VLAN
    - In- of uitschakelen van VLAN
    - VLAN opsommen
    - Beschrijvende naam van de set met een VLAN

- Configuratie van laag 2-poort:
    - Poorten opsommen
    - In- of uitschakelen van poorten
    - Set-poort modi en eigenschappen
    - Toevoegen of koppelen van de VLAN Trunk of toegang op de poort

Te verkennen door te zoeken naar alle van de cmdlets NetworkSwitch!

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

Meer informatie is beschikbaar in de Jeffrey Snover WMF 5.0 Preview aankondiging blogbericht: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx>
