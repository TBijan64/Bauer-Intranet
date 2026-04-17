# 🏢 BAUER KOMPRESSOREN - Intranet Struktur (Mockup)

## 📋 Übersicht der Integration

Alle Elemente aus der HTML-Datei wurden erfolgreich in die SharePoint XML-Vorlage integriert.

---

## 🎨 Design & Branding

| Element | Wert |
|---------|------|
| **Primary Color** | #1E5BA8 (Blau) |
| **Secondary Color** | #E63946 (Rot) |
| **Accent Color** | #0066CC (Helles Blau) |
| **Success Color** | #06D6A0 (Grün) |
| **Warning Color** | #FFB703 (Orange) |
| **Tagline** | "Quality. Our DNA." |

---

## 📑 Seiten-Struktur

### 1. **Startseite (Startseite.aspx)**
```
┌─────────────────────────────────────┐
│         HEADER / NAVIGATION         │
├─────────────────────────────────────┤
│  Logo: BAUER KOMPRESSOREN           │
│  Quality. Our DNA.                  │
├─────────────────────────────────────┤
│  Navigation:                        │
│  • Zentrale | Technik | Sales       │
│  • Produktion | Academy             │
└─────────────────────────────────────┘

┌─ HERO SECTION ──────────────────────┐
│ ┌─ Hauptmeldung ────────────────┐   │
│ │ "Willkommen im Team: Neue     │   │
│ │  Kolleginnen & Kollegen"      │   │
│ │ Volker Sandfuchs, HR          │   │
│ │ Heute, 09:30                  │   │
│ └────────────────────────────────┘   │
│ ┌─ Sidebar Cards ─────────────────┐  │
│ │ • Produkt-Launch              │  │
│ │ • Q1 Verkaufszahlen           │  │
│ └────────────────────────────────┘  │
└─────────────────────────────────────┘

┌─ POST NEWS BUTTON ──────────────────┐
│ 📝 Beitrag erstellen                │
│ [+ Event/News posten]               │
└─────────────────────────────────────┘

┌─ NEWS GRID ─────────────────────────┐
│ 📰 Aktuelle News                    │
│                                     │
│ ┌──────┐ ┌──────┐ ┌──────┐         │
│ │🔧    │ │📊    │ │⚙️    │         │
│ │Teknik│ │Sales │ │Prod. │         │
│ │      │ │      │ │      │         │
│ └──────┘ └──────┘ └──────┘         │
│                                     │
│ ┌──────┐ ┌──────┐ ┌──────┐         │
│ │🎓    │ │🛡️    │ │🌍    │         │
│ │Acad. │ │Siche.│ │Markt.│         │
│ │      │ │      │ │      │         │
│ └──────┘ └──────┘ └──────┘         │
└─────────────────────────────────────┘

┌─ QUICK LINKS ───────────────────────┐
│ Service & Hilfe                     │
│                                     │
│ 💬 Help Desk    │📚 Dokumentation  │
│ 🎓 BAUER Acad.  │⚖️  Compliance    │
│ 👥 HR Portal    │🔍 News-Archiv    │
└─────────────────────────────────────┘

┌─ DEPARTMENTS ───────────────────────┐
│ Unsere Abteilungen                  │
│                                     │
│ 🏢 Geschäftsführung    🔬 Entwickl. │
│ ✅ Qualitätsmgmt.      📊 Sales CC  │
│ ⚙️  Operations & Prod.  🚚 Service  │
│ 👥 Human Resources     🔧 Projekte  │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│            FOOTER                   │
├─────────────────────────────────────┤
│ • Schnellzugriff                    │
│ • Ressourcen                        │
│ • Support                           │
│ © 2026 BAUER KOMPRESSOREN GmbH     │
└─────────────────────────────────────┘
```

---

## 📊 Datenlisten

### News List
```json
{
  "Title": "News",
  "Fields": [
    "NewsTitle (Text, erforderlich)",
    "NewsContent (Note, erforderlich)",
    "NewsCategory (Choice: Technik, Sales, Produktion, IT, Marketing, HR, Finanzen)",
    "NewsAuthor (User)",
    "Attachments"
  ],
  "Views": ["All Items"]
}
```

### Events List
```json
{
  "Title": "Events",
  "Fields": [
    "EventTitle (Text)",
    "EventLocation (Text)",
    "EventDate (DateTime)",
    "EventTime (Text)",
    "EventDescription (Note)",
    "EventOrganizer (User)",
    "Attachments"
  ],
  "Views": ["All Items"]
}
```

### Abteilungen List
```json
{
  "Title": "Abteilungen",
  "Fields": [
    "DeptName (Text)",
    "DeptDescription (Note)",
    "DeptLeader (Text)",
    "DeptEmail (Text)",
    "DeptPhone (Text)"
  ],
  "Views": ["All Items"]
}
```

### Service Links List (NEU)
```json
{
  "Title": "Service Links",
  "Fields": [
    "LinkTitle (Text)",
    "LinkDescription (Note)",
    "LinkURL (URL)",
    "LinkIcon (Text)"
  ],
  "DataRows": [
    {
      "LinkTitle": "Help Desk",
      "LinkDescription": "IT-Support von Nuri Al",
      "LinkURL": "https://...",
      "LinkIcon": "💬"
    },
    {
      "LinkTitle": "Dokumenten-Archiv",
      "LinkDescription": "Technische Handbücher & Nachweise",
      "LinkURL": "https://...",
      "LinkIcon": "📚"
    },
    {
      "LinkTitle": "BAUER Academy",
      "LinkDescription": "Schulungen & Weiterbildung",
      "LinkURL": "https://...",
      "LinkIcon": "🎓"
    },
    {
      "LinkTitle": "Recht & Compliance",
      "LinkDescription": "Dokumente von Andreas Huber",
      "LinkURL": "https://...",
      "LinkIcon": "⚖️"
    },
    {
      "LinkTitle": "HR Portal",
      "LinkDescription": "Urlaub, Gehalt, Personalthemen",
      "LinkURL": "https://...",
      "LinkIcon": "👥"
    },
    {
      "LinkTitle": "News-Archiv",
      "LinkDescription": "Alle Meldungen durchsuchen",
      "LinkURL": "News-Verwaltung.aspx",
      "LinkIcon": "🔍"
    }
  ]
}
```

---

## 🧭 Navigation

```
Startseite
├─ News & Events
│  ├─ Aktuelle News (News-Verwaltung.aspx)
│  └─ Events (Events-Verwaltung.aspx)
├─ Zentrale (#zentrale)
├─ Technik (#technik)
├─ Sales (#sales)
├─ Produktion (#produktion)
├─ Academy (#academy)
├─ Abteilungen (Lists/Abteilungen)
└─ Service & Hilfe (Service-Links.aspx)
```

---

## 🎯 Abteilungen (mit Kontaktdaten)

| Icon | Abteilung | Beschreibung | Kontakt |
|------|-----------|-------------|---------|
| 🏢 | Geschäftsführung | Strategische Führung | geschaeftsfuehrung@bauer-kompressoren.de |
| 🔬 | Zentrale Entwicklung | Innovation & Technologie | entwicklung@bauer-kompressoren.de |
| ✅ | Qualitätsmanagement | Höchste Standards | qualitaet@bauer-kompressoren.de |
| 📊 | Sales CC | Vertrieb & Marketing | sales@bauer-kompressoren.de |
| ⚙️ | Operations & Produktion | Fertigung & Montage | produktion@bauer-kompressoren.de |
| 🚚 | Service & Logistik | Kundenservice | service@bauer-kompressoren.de |
| 👥 | Human Resources | Personalmanagement | hr@bauer-kompressoren.de |
| 🔧 | Projektmanagement | Projektkoordination | projekte@bauer-kompressoren.de |

---

## 📱 Responsive Features

- ✅ Mobile Navigation (Hamburger-Menü bei < 768px)
- ✅ Touch-freundliche Elemente
- ✅ Adaptive Grid-Layouts
- ✅ Flexible Bildgrößen
- ✅ Swipe-Unterstützung (Drag & Drop für Dateien)

---

## 🎭 Modales Fenster (News/Event erstellen)

```
┌──── Neuen Beitrag erstellen ────┐
│                           [✕]   │
├─────────────────────────────────┤
│ 📰 News  │  📅 Event  (Tabs)     │
├─────────────────────────────────┤
│ News-Tab:                       │
│ • Titel (erforderlich)          │
│ • Autor (erforderlich)          │
│ • Kategorie (Dropdown)          │
│ • Inhalt (Textarea)             │
│ • Bild hochladen (Drag & Drop)  │
│                                 │
│ Event-Tab:                      │
│ • Event Titel                   │
│ • Organisator                   │
│ • Ort                           │
│ • Datum & Uhrzeit               │
│ • Event Beschreibung            │
│ • Event Bild                    │
├─────────────────────────────────┤
│ [Abbrechen]  [Beitrag veröff.]  │
└─────────────────────────────────┘
```

---

## 🎨 CSS Styling Features

- ✅ Glassmorphism-Effekt im Header
- ✅ Gradient-Hintergründe (Accent + Secondary)
- ✅ Smooth Animations (fadeIn, slideDown, slideUp)
- ✅ Hover-Effekte (translateY, Border-Animation)
- ✅ Backdrop-Filter für moderne Effekte
- ✅ Custom Scrollbar mit Branding-Farben
- ✅ Responsive Breakpoints (1024px, 768px, 600px)

---

## 📦 Dateien der Vorlage

```
Bauer Kompressoren GmbH Intranet.html      ← Design-Vorlage
Bauer-Kompressoren-Vorlage.xml             ← SharePoint Provisioning
Bauer-Kompressoren-Styles.css              ← CSS Stylesheet
Bauer-Kompressoren-SiteScript.json         ← Site Script (optional)
POWERSHELL-ANLEITUNG.md                    ← Deployment-Anleitung
README.md                                  ← Dokumentation
```

---

## ✨ Highlight Features

1. **Hero Section** mit dynamischem Parallax-Effekt
2. **Modal-Fenster** mit Tab-Navigation für News/Events
3. **Drag & Drop** Bild-Upload
4. **Dynamische News-Karten** die beim Veröffentlichen oben erscheinen
5. **Success-Benachrichtigungen** (Toast-Meldungen)
6. **Abteilungs-Grid** mit Kontaktinformationen
7. **Quick Links** zu wichtigen Services
8. **Responsive Footer** mit Multi-Column Layout

---

## 🚀 Deployment-Status

| Element | Status |
|---------|--------|
| News List | ✅ Implementiert |
| Events List | ✅ Implementiert |
| Abteilungen List | ✅ Implementiert |
| Service Links List | ✅ Neu hinzugefügt |
| Startseite | ✅ Definiert |
| Navigation | ✅ Erweitert |
| Styling | ✅ CSS-Datei referenziert |
| Branding | ✅ Farben in PropertyBag |

---

**Generated:** April 17, 2026  
**Template Version:** 1.0  
**Company:** BAUER KOMPRESSOREN GmbH
