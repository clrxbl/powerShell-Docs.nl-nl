---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Een grafische datumkiezer maken
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 3727c90c314a6fc1b3a338ec60e44259f153d954
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954837"
---
# <a name="creating-a-graphical-date-picker"></a>Een grafische datumkiezer maken

Gebruik Windows PowerShell 3.0 en latere versies te maken van een formulier met een grafische, agenda-stijl-besturingselement waarmee gebruikers een dag van de maand selecteren.

## <a name="create-a-graphical-date-picker-control"></a>Het maken van een besturingselement grafische datum kiezen

Kopieer en plak het volgende in Windows PowerShell ISE en vervolgens opslaan als een Windows PowerShell-script (.ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form

$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'

$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

Het script begint met het laden van twee klassen van .NET Framework: **System.Drawing** en **System.Windows.Forms**. Vervolgens start u een nieuw exemplaar van de .NET Framework-klasse **Windows.Forms.Form**; die zorgt voor een leeg formulier of besturingselementen venster waarnaar u kunt starten toe te voegen.

```powershell
$form = New-Object Windows.Forms.Form
```

Nadat u een exemplaar van de klasse van het formulier hebt gemaakt, kunt u de waarden toewijzen aan drie eigenschappen van deze klasse.

- **De tekst.** Dit wordt de titel van het venster.

- **Size.** Dit is de grootte van het formulier in pixels. Dit script maakt een formulier 243 pixels breed met 230 pixels hoog.

- **StartingPosition.** Deze optionele eigenschap is ingesteld op **CenterScreen** in het voorgaande script. Als u deze eigenschap niet toevoegt, wordt een locatie geselecteerd wanneer het formulier wordt geopend. Door in te stellen de **StartingPosition** naar **CenterScreen**, u automatisch weergeeft het formulier in het midden van het scherm elke keer dat wordt geladen.

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

Vervolgens maken en voeg vervolgens een kalenderbesturingselement in het formulier. De huidige dag is niet in dit voorbeeld gemarkeerd of omcirkeld. Gebruikers kunnen slechts één dag in de kalender in één keer selecteren.

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

Maak vervolgens een **OK** knop voor het formulier. Geef de grootte en het gedrag van de **OK** knop. In dit voorbeeld is de knop positie 165 pixels vanaf de bovenkant van het formulier en 38 pixels van de linkerrand. De hoogte van de knop wordt 23 pixels wanneer de lengte van de knop 75 pixels. Het script maakt gebruik van vooraf gedefinieerde Windows Forms-typen om te bepalen het gedrag van de knop.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Op deze manier maakt u een **annuleren** knop. De **annuleren** knop 165 pixels vanaf de bovenkant, maar 113 pixels van de linkerrand van het venster is.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Stel de **Topmost** eigenschap **$true** om af te dwingen van het venster te openen op een andere geopende vensters en dialoogvensters.

```powershell
$form.Topmost = $true
```

Voeg de volgende regel code om het formulier in Windows weer te geven.

```powershell
$result = $form.ShowDialog()
```

Ten slotte de code in de **als** blok geeft Windows opdracht wat te doen met het formulier wanneer gebruikers een dag in de kalender selecteren en klik vervolgens op de **OK** of drukt u op de **Enter** sleutel. Windows PowerShell geeft de geselecteerde datum bij gebruikers.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Zie ook

- [Hey Scripting Guy: Waarom werken niet op deze voorbeelden PowerShell GUI?](http://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt van WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell Tip van de Week: een grafische datum objectkiezer maken](http://technet.microsoft.com/library/ff730942.aspx)