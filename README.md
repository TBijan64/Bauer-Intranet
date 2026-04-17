# BAUER KOMPRESSOREN - SharePoint PnP Vorlage

Willkommen zur SharePoint Provisioning Vorlage für BAUER KOMPRESSOREN Intranet!

## 📦 Inhalt der Vorlage

Diese Vorlage enthält folgende Dateien:

1. **Bauer-Kompressoren-Vorlage.xml** - XML-basierte PnP-Provisioning-Template
2. **Bauer-Kompressoren-SiteScript.json** - JSON-basiertes Site Script (moderneres Format)
3. **Bauer-Kompressoren-Styles.css** - Custom CSS für das moderne Design
4. **Bauer Kompressoren GmbH Intranet.html** - Original HTML-Version (für Referenz)

## 🚀 Installation mit PnP PowerShell

### Voraussetzungen:
- PowerShell 5.0 oder höher
- PnP PowerShell Modul installiert

```powershell
# PnP PowerShell Modul installieren (falls nicht vorhanden)
Install-Module PnP.PowerShell -AllowPrerelease
```

### Schritt-für-Schritt Installation:

#### 1. Mit der XML-Vorlage (empfohlen):

```powershell
# Mit SharePoint verbinden
Connect-PnPOnline -Url "https://[YourTenant].sharepoint.com/sites/YourSite" -Interactive

# Vorlage anwenden
Apply-PnPProvisioningTemplate -Path "Bauer-Kompressoren-Vorlage.xml"
```

#### 2. Mit dem JSON Site Script:

```powershell
# Mit SharePoint verbinden
Connect-PnPOnline -Url "https://[YourTenant].sharepoint.com" -Interactive

# Site Script hochladen
$siteScriptId = Add-PnPSiteScript -Title "Bauer Kompressoren" -Description "Unternehmens-Intranet" -Content (Get-Content "Bauer-Kompressoren-SiteScript.json" -Raw)

# Site Design erstellen (optional)
Add-PnPSiteDesign -Title "Bauer Kompressoren Intranet" -SiteScriptIds $siteScriptId -WebTemplate "68"
```

## 📋 Was wird erstellt?

Die Vorlage erstellt automatisch:

### Listen:
- **News** - Aktuelle Neuigkeiten (Titel, Inhalt, Kategorie, Autor, Anhänge)
- **Events** - Unternehmens-Events (Titel, Ort, Datum, Uhrzeit, Beschreibung, Organisator)
- **Abteilungen** - Abteilungsinformationen (Name, Beschreibung, Leiter, Kontakt)

### Seiten:
- **Startseite** - Intranet-Startseite mit News, Events und Abteilungen
- **News-Verwaltung** - Vollständige News-Liste
- **Events-Verwaltung** - Vollständige Events-Liste

### Design:
- Modernes helles Design (Weiß & Blau)
- Responsive Layout
- Custom Theme mit Unternehmensfarben
- Navigation mit Quick Links

## 🎨 Design-Farben

- **Primärfarbe**: #1E5BA8 (Blau)
- **Akzentfarbe**: #0066CC (Leuchtendes Blau)
- **Hintergrund**: #F8FAFC (Helles Grau-Weiß)
- **Text**: #1A1A1A (Dunkelgrau)

## ✨ Funktionen

✅ News & Events Posting
✅ Automatische Kategorisierung
✅ Benutzer-Autorisierung
✅ Versionskontrolle
✅ Moderne SharePoint-Integration
✅ Responsive Design
✅ Dunkles/Helles Design Support
✅ Mehrsprachig (DE/EN möglich)

## 🔧 Konfiguration

Nach der Installation können Sie folgende Anpassungen vornehmen:

1. **Kategorien hinzufügen** - Bearbeiten Sie die Kategorien-Liste in der News-Liste
2. **Design anpassen** - Modifizieren Sie die CSS-Datei in SiteAssets
3. **Navigation anpassen** - Passen Sie die globale Navigation an
4. **Berechtigungen setzen** - Definieren Sie Zugriffsrechte für Listen

## 📱 Responsive Design

Die Vorlage ist vollständig responsive und funktioniert auf:
- Desktop-Browsern
- Tablets
- Mobilgeräten

## 🔐 Sicherheit & Governance

- Alle Listen haben Versionskontrolle aktiviert
- Benutzer können nur autorisierte Bereiche bearbeiten
- Audit Trails sind aktiv
- Content Approval kann aktiviert werden

## 📞 Support

Für Fragen oder Änderungen:
- Kontaktieren Sie die IT-Abteilung
- E-Mail: it@bauer-kompressoren.de

## 📝 Lizenz

Intern nur für BAUER KOMPRESSOREN GmbH
Quality. Our DNA.

---
Version: 1.0
Erstellt: April 2026
