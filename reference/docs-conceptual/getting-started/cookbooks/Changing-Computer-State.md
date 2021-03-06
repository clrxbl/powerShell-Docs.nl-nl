---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Computerstatus wijzigen
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: f2fadcedaeddfa6f8b9dd4d70738ee062b907d61
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851080"
---
# <a name="changing-computer-state"></a>Computerstatus wijzigen

Als u wilt herstellen op een computer in Windows PowerShell, een standaard opdrachtregelprogramma of een WMI-klasse te gebruiken. Hoewel u Windows PowerShell gebruiken om alleen uit te voeren van het hulpprogramma, leren hoe u kunt de energiestatus van de computer in Windows PowerShell wijzigen ziet u enkele van de belangrijke informatie over het werken met externe hulpprogramma's in Windows PowerShell.

### <a name="locking-a-computer"></a>Vergrendelen van een Computer

De enige manier om het vergrendelen van een computer rechtstreeks met de tools die standaard beschikbaar is om aan te roepen de **LockWorkstation()** werken in **user32.dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

Met deze opdracht wordt onmiddellijk vergrendeld voor het werkstation. Hierbij *rundll32.exe*, die wordt uitgevoerd Windows dll-bestanden (en slaat de bibliotheken voor herhaalde gebruik) om uit te voeren user32.dll, een bibliotheek met functies voor het beheer van Windows.

Wanneer u vergrendelen een werkstation snelle gebruikerswisseling is ingeschakeld, zoals op Windows XP, toont de computer het aanmeldingsscherm van de gebruiker in plaats van vanaf de screensaver van de huidige gebruiker.

Als u wilt afsluiten bepaalde sessies op een Terminal Server, gebruikt u de **tsshutdn.exe** opdrachtregel-hulpprogramma.

### <a name="logging-off-the-current-session"></a>De huidige sessie afmelden

U kunt meerdere verschillende technieken worden afgemeld bij een sessie op het lokale systeem. De eenvoudigste manier is het gebruik van het opdrachtregelprogramma van extern bureaublad/Terminal Services **logoff.exe** (voor meer informatie bij de Windows PowerShell-prompt, typ **Afmelden /?**). De huidige actieve sessie afmelden, typt u **Afmelden** zonder argumenten.

U kunt ook de **shutdown.exe** hulpprogramma met de optie voor afmelden:

```
shutdown.exe -l
```

Een derde optie is het gebruik van WMI. De Win32_OperatingSystem-klasse heeft een methode Win32Shutdown. Aanroepen van de methode met de vlag 0 initieert afmelden:

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Zie "Win32Shutdown methode van de Win32_OperatingSystem Class" in MSDN voor meer informatie en andere functies van de methode Win32Shutdown vinden.

### <a name="shutting-down-or-restarting-a-computer"></a>Afsluiten of opnieuw opstarten van een Computer

Afgesloten en opnieuw opstarten van computers worden in het algemeen dezelfde gegevenstypen van de taak. Hulpprogramma's die een computer afsluiten dan in het algemeen start ook, en vice versa. Er zijn twee eenvoudige opties voor opnieuw opstarten van een computer vanuit Windows PowerShell. Tsshutdn.exe of Shutdown.exe gebruiken met de juiste argumenten. Krijgt u gedetailleerde gebruiksinformatie van **tsshutdn.exe /?** of **shutdown.exe /?**.

U kunt ook afsluiten en opnieuw starten van bewerkingen rechtstreeks vanuit Windows PowerShell ook.

Als u wilt afsluiten de computer, gebruikt u de opdracht Stop-Computer

```powershell
Stop-Computer
```

Als u wilt het besturingssysteem opnieuw hebt opgestart, gebruikt u de opdracht Computer opnieuw opstarten

```powershell
Restart-Computer
```

Als u wilt afdwingen dat een onmiddellijk opnieuw opstarten van de computer, gebruikt u de parameter - Force.

```powershell
Restart-Computer -Force
```
