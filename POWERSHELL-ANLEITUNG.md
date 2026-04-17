# BAUER KOMPRESSOREN SharePoint PnP Installation - PowerShell Anleitung

## Quick Start Befehl

```powershell
# 1. Verbindung zu SharePoint herstellen
Connect-PnPOnline -Url "https://yourtenantname.sharepoint.com/sites/bauer-intranet" -Interactive

# 2. Vorlage anwenden
Apply-PnPProvisioningTemplate -Path ".\Bauer-Kompressoren-Vorlage.xml" -Verbose

# 3. Fertig! Die Seite ist einsatzbereit
```

## Vollständige Schritt-für-Schritt Anleitung

### Schritt 1: PowerShell-Modul installieren

```powershell
# PnP PowerShell Modul (neueste Version)
Install-Module PnP.PowerShell -AllowPrerelease -Force

# Oder Updates einspielen
Update-Module PnP.PowerShell
```

### Schritt 2: Mit SharePoint verbinden

```powershell
# Mit interaktivem Login
Connect-PnPOnline -Url "https://yourtenantname.sharepoint.com/sites/IntranetSiteName" -Interactive

# Alternative: Mit globale Admin-Credentials
$credentials = Get-Credential
Connect-PnPOnline -Url "https://yourtenantname.sharepoint.com/sites/IntranetSiteName" -Credentials $credentials
```

### Schritt 3: Vorlage anwenden

```powershell
# XML-Vorlage anwenden (empfohlen)
Apply-PnPProvisioningTemplate -Path "C:\Pfad\Bauer-Kompressoren-Vorlage.xml" -Verbose

# Mit Parameter für erweiterte Optionen
Apply-PnPProvisioningTemplate -Path "C:\Pfad\Bauer-Kompressoren-Vorlage.xml" `
    -ResourceFolder "C:\Pfad" `
    -OverwriteSystemPropertyBagValues `
    -Verbose
```

### Schritt 4: Überprüfung

```powershell
# Listen überprüfen
Get-PnPList | Select Title, ItemCount

# Seiten überprüfen
Get-PnPClientSidePage

# Navigationsstruktur überprüfen
Get-PnPNavigationNode
```

## Weitere nützliche Befehle

### Listen verwalten

```powershell
# Alle Listen anzeigen
Get-PnPList

# Spezifische Liste anzeigen
Get-PnPList -Identity "News"

# Listenelemente hinzufügen
Add-PnPListItem -List "News" -Values @{"Title"="Neue Neuigkeit"; "NewsCategory"="Technik"}

# Listenelemente abrufen
Get-PnPListItem -List "News" -PageSize 100
```

### Seiten verwalten

```powershell
# Alle Seiten auflisten
Get-PnPClientSidePage

# Seite abrufen
Get-PnPClientSidePage -Identity "Startseite.aspx"

# Seite löschen
Remove-PnPClientSidePage -Identity "Startseite.aspx"
```

### Berechtigungen setzen

```powershell
# Benutzer zu Gruppe hinzufügen
Add-PnPGroupMember -LoginName "user@example.com" -GroupName "Intranet-Editoren"

# Besitzer hinzufügen
Add-PnPGroupMember -LoginName "user@example.com" -GroupName "Owners"

# Berechtigungen überprüfen
Get-PnPGroupMembers -GroupName "Intranet-Editoren"
```

### Design anpassen

```powershell
# Theme anwenden
Set-PnPTheme -ColorPaletteUrl "https://yourtenantname.sharepoint.com/sites/bauer/themepalette.json"

# Aktuelles Theme anzeigen
Get-PnPTheme

# Custom CSS anwenden
Set-PnPStorageEntity -Key "CustomCSSUrl" -Value "https://yoursite/sites/bauer/SiteAssets/Bauer-Kompressoren-Styles.css"
```

## Backup und Export

### Vorlage exportieren (für Änderungen)

```powershell
# Aktuelle Konfiguration exportieren
Get-PnPProvisioningTemplate -Out "Bauer-Kompressoren-Backup.xml"

# Mit Daten exportieren
Get-PnPProvisioningTemplate -Out "Bauer-Kompressoren-Backup.xml" -IncludeAllClientSidePages $true
```

### Sicherung erstellen

```powershell
# Alle Listen sichern
Get-PnPList | Foreach-Object {
    Export-PnPListToCSV -List $_.Title -Out "C:\Backup\$($_.Title).csv"
}
```

## Fehlerbehebung

### Fehler: "The file does not exist"

```powershell
# Vollständigen Pfad verwenden
$filePath = Resolve-Path ".\Bauer-Kompressoren-Vorlage.xml"
Apply-PnPProvisioningTemplate -Path $filePath.Path
```

### Fehler: "Access Denied"

```powershell
# Mit Admin-Berechtigungen ausführen
# PowerShell als Administrator starten und erneut verbinden
```

### Fehler: "Operation timed out"

```powershell
# Mit erhöhtem Timeout erneut versuchen
Apply-PnPProvisioningTemplate -Path ".\Bauer-Kompressoren-Vorlage.xml" `
    -TimeoutSecs 600 `
    -Verbose
```

## Skript für automatisierte Installation

Speichern Sie dieses als `Install-BauerIntranet.ps1`:

```powershell
param(
    [Parameter(Mandatory=$true)]
    [string]$SiteUrl,
    
    [Parameter(Mandatory=$false)]
    [string]$TemplateFile = ".\Bauer-Kompressoren-Vorlage.xml"
)

Write-Host "BAUER KOMPRESSOREN Intranet Vorlage Installer" -ForegroundColor Green
Write-Host "============================================" -ForegroundColor Green

# Verbindung herstellen
Write-Host "Verbindung zu $SiteUrl wird hergestellt..." -ForegroundColor Yellow
Connect-PnPOnline -Url $SiteUrl -Interactive

# Vorlage anwenden
Write-Host "Vorlage wird angewendet..." -ForegroundColor Yellow
Apply-PnPProvisioningTemplate -Path $TemplateFile -Verbose

# Überprüfung
Write-Host "Überprüfung..." -ForegroundColor Yellow
$lists = Get-PnPList | Measure-Object
$pages = Get-PnPClientSidePage | Measure-Object

Write-Host "✓ Installation abgeschlossen!" -ForegroundColor Green
Write-Host "  - $($lists.Count) Listen erstellt"
Write-Host "  - $($pages.Count) Seiten erstellt"
Write-Host "  - Startseite: $SiteUrl/SitePages/Startseite.aspx"

Disconnect-PnPOnline
```

Verwendung:

```powershell
.\Install-BauerIntranet.ps1 -SiteUrl "https://yourtenantname.sharepoint.com/sites/bauer-intranet"
```

## Weitere Ressourcen

- PnP PowerShell Dokumentation: https://pnp.github.io/powershell/
- SharePoint Modern Sites: https://docs.microsoft.com/sharepoint/dev/
- Site Designs: https://docs.microsoft.com/sharepoint/dev/declarative-customization/site-design-overview

---

Version 1.0 | April 2026 | BAUER KOMPRESSOREN GmbH
