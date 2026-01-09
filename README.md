# MoodleThemeBoostCustomizations

# Moodle Demo / Sandbox – Theme & Styles

## Einführung
Dieses Repository enthält Anpassungen für ausgewählte Moodle-Kategorien (`category-53`, `category-114`, `category-88`) auf Basis des Boost-Themes.  
Ziel ist eine einheitliche Darstellung von Hintergrund, Drawer, Textformatierungen, Fragenblöcken, Karten, Alerts, Kompetenzblöcken und Quickgrade-Kommentarfeldern.

---

## Installation

### 1. Script einfügen
- **Ort:** `Webseiten Administration → Darstellung → Vor dem Schließen von <body> (additionalhtmlfooter)`  
- **Inhalt:**
```html
<script>
document.addEventListener("DOMContentLoaded", function () {

  // Theme für Demo-Kategorien
  const demoCategories = ["category-53", "category-114", "category-88"];
  demoCategories.forEach(cat => {
    if (document.body.classList.contains(cat)) {
      const link = document.createElement("link");
      link.rel = "stylesheet";
      link.href = "https://cdn.jsdelivr.net/npm/bootswatch@5.3.8/dist/yeti/bootstrap.min.css";
      document.head.appendChild(link);
    }
  });

});
</script>
```

### 2. Raw SCSS einfügen
- **Ort:** `Webseiten Administration → Designs → Boost → Zahnrad → Erweiterte Einstellungen → Raw SCSS (theme_boost | scss)`  
- **Inhalt:**

```css
/* ======================================================
   DEMO / SANDBOX – Kurse
   Gültig für:
   - category-53
   - category-114
   - category-88
   ====================================================== */

/* ------------------------------------------------------
   Body Font-Size für Sandbox-Kategorien
------------------------------------------------------ */
body.category-53,
body.category-114,
body.category-88 {
  font-size: 0.9375rem; /* entspricht 15px */
}


/* ======================================================
   1) SEITENHINTERGRUND (nur ausgewählte Pages)
   ====================================================== */

body.category-53#page-course-view-topics,
body.category-53#page-mod-quiz-view,
body.category-53#page-mod-wiki-view,
body.category-53#page-mod-page-view,
body.category-53#page-course-view-section-topics,
body.category-53#page-mod-feedback-view,

body.category-114#page-course-view-topics,
body.category-114#page-mod-quiz-view,
body.category-114#page-mod-wiki-view,
body.category-114#page-mod-page-view,
body.category-114#page-course-view-section-topics,
body.category-114#page-mod-feedback-view,

body.category-88#page-course-view-topics,
body.category-88#page-mod-quiz-view,
body.category-88#page-mod-wiki-view,
body.category-88#page-mod-page-view,
body.category-88#page-course-view-section-topics,
body.category-88#page-mod-feedback-view {
  background-image: linear-gradient(
    90deg,
    rgba(104, 180, 237, 1) 0%,
    rgba(192, 198, 204, 1) 30%,
    rgba(211, 229, 242, 1) 100%
  );
}


/* ======================================================
   2) DRAWER – Links ohne Unterstreichung
   ====================================================== */

body.category-53 .drawercontent.drag-container li a,
body.category-114 .drawercontent.drag-container li a,
body.category-88 .drawercontent.drag-container li a,
body.category-53 .drawercontent.drag-container li a:hover,
body.category-114 .drawercontent.drag-container li a:hover,
body.category-88 .drawercontent.drag-container li a:hover,
body.category-53 .drawercontent.drag-container li a:focus,
body.category-114 .drawercontent.drag-container li a:focus,
body.category-88 .drawercontent.drag-container li a:focus {
  text-decoration: none;
}


/* ======================================================
   3) CONTAINER / MAIN-INNER (Boost-Standard)
   ====================================================== */

/* Mobile */
@media (max-width: 767.98px) {
  body.category-53.limitedwidth #page.drawers .main-inner,
  body.category-114.limitedwidth #page.drawers .main-inner,
  body.category-88.limitedwidth #page.drawers .main-inner {
    max-width: 100%;
    padding: 1rem;
  }
}

/* Desktop */
@media (min-width: 768px) {
  body.category-53.limitedwidth #page.drawers .main-inner,
  body.category-114.limitedwidth #page.drawers .main-inner,
  body.category-88.limitedwidth #page.drawers .main-inner {
    max-width: 1200px;
    margin: 0 auto;
  }

  body.category-53 .header-maxwidth,
  body.category-114 .header-maxwidth,
  body.category-88 .header-maxwidth {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 1rem;
  }
}


/* ======================================================
   4) SECONDARY NAVIGATION / TABS
   ====================================================== */

body.category-53 .secondary-navigation .navigation .nav-tabs,
body.category-114 .secondary-navigation .navigation .nav-tabs,
body.category-88 .secondary-navigation .navigation .nav-tabs {
  border: none;
  max-width: 1200px;
  margin: 0 auto;
}


/* ======================================================
   5) DRAWER (Boost-Originalbreite)
   ====================================================== */

body.category-53 .drawer.drawer-left,
body.category-114 .drawer.drawer-left,
body.category-88 .drawer.drawer-left {
  width: 285px;
  max-width: 285px;
}

body.category-53:not(.drawer-open-index) .drawer.drawer-left,
body.category-114:not(.drawer-open-index) .drawer.drawer-left,
body.category-88:not(.drawer-open-index) .drawer.drawer-left {
  left: calc(-285px - 0.625rem);
}

body.category-53.drawer-open-index .drawer.drawer-left,
body.category-114.drawer-open-index .drawer.drawer-left,
body.category-88.drawer-open-index .drawer.drawer-left {
  left: 0;
}

body.category-53 .drawer,
body.category-114 .drawer,
body.category-88 .drawer {
  background-color: #e8eef8;
}

/* Keine manuelle Container-Verschiebung
   → verhindert Überlagerungen (Quiz-Report, rechte Blockleiste, Editing)
*/


/* ======================================================
   6) TYPOGRAFIE / CODE
   ====================================================== */

body.category-53 strong,
body.category-114 strong,
body.category-88 strong {
  font-weight: 550 !important;
}

body.category-53 code,
body.category-114 code,
body.category-88 code {
  font-size: 0.95rem;
}


/* ======================================================
   7) CARDS / ALERTS / TABELLEN
   ====================================================== */

body.category-53 .card.bg-light,
body.category-53 .card-header.bg-light,
body.category-53 .alert.bg-light,
body.category-53 thead.bg-light,
body.category-53 th.bg-light,
body.category-53 td.bg-light,

body.category-114 .card.bg-light,
body.category-114 .card-header.bg-light,
body.category-114 .alert.bg-light,
body.category-114 thead.bg-light,
body.category-114 th.bg-light,
body.category-114 td.bg-light,

body.category-88 .card.bg-light,
body.category-88 .card-header.bg-light,
body.category-88 .alert.bg-light,
body.category-88 thead.bg-light,
body.category-88 th.bg-light,
body.category-88 td.bg-light {
  background-color: #008cba !important;
  color: #ffffff;
}


/* ======================================================
   8) QUIZ – QUESTION FORMULATION
   ====================================================== */

body.category-53 .que .formulation,
body.category-114 .que .formulation,
body.category-88 .que .formulation {
  color: #222;
  background-color: #fafafa;
  border: 0;
  padding: 1.25rem;
  border-radius: 0.5rem;
}


/* ======================================================
   9) KOMPETENZBLOCK
   ====================================================== */

body.category-53 #course-competence p,
body.category-53 #course-competence th,
body.category-53 #course-competence li,

body.category-114 #course-competence p,
body.category-114 #course-competence th,
body.category-114 #course-competence li,

body.category-88 #course-competence p,
body.category-88 #course-competence th,
body.category-88 #course-competence li {
  font-size: 0.9375rem;
}


/* ======================================================
   10) ALERTS (Feinabstimmung)
   ====================================================== */

body.category-53 .alert,
body.category-114 .alert,
body.category-88 .alert {
  font-size: 0.9rem;
  font-weight: 500;
}


/* ======================================================
   11) TIMETRACKING
   ====================================================== */

div#course-time-tracking i {
  color: #ffffff !important;
  margin-right: 2px !important;
}


/* ======================================================
   12) BEWERTER-INFORMATION
   ====================================================== */

div#course-grading-info .card-header.bg-light {
  background-color: #ffffff !important;
}


/* ======================================================
   13) ASSIGN GRADING – QUICKGRADE COMMENTS
   ====================================================== */

body.category-53#page-mod-assign-grading textarea[id^="quickgrade_comments_"],
body.category-114#page-mod-assign-grading textarea[id^="quickgrade_comments_"],
body.category-88#page-mod-assign-grading textarea[id^="quickgrade_comments_"] {
  width: 300px;
  height: 100px;
  resize: vertical;
}


```

## Troubleshooting

### Änderungen sind nicht sichtbar
- Moodle-Cache leeren:  
  `Website-Administration → Entwicklung → Cache leeren`
- Browser-Cache hart neu laden (`Ctrl + F5`)
- Prüfen, ob das **Boost-Theme** aktiv ist

### Raw SCSS wird nicht angewendet
- Sicherstellen, dass der Code im Feld  
  **„Raw SCSS (theme_boost | scss)“** eingefügt wurde
- Keine Syntaxfehler im SCSS (z. B. fehlende `{}` oder ungültige Selektoren)
- Nach dem Speichern **Cache zwingend leeren**

### JavaScript wird nicht ausgeführt
- Script befindet sich wirklich unter  
  **„Vor dem Schließen von `<body>` (additionalhtmlfooter)“**
- Browser-DevTools öffnen → Tab **Console** → nach Fehlern suchen
- Prüfen, ob die Zielklasse (z. B. `category-53`) im `<body>` existiert

### Styles greifen nur auf manchen Seiten
- Prüfen, ob die Seite die erwartete `page-*`-ID besitzt  
  (z. B. `page-course-view-topics`, `page-mod-quiz-view`)

### Drawer oder Inhalte überlagern sich
- Keine manuelle Verschiebung von `#page.drawers` erzwingen
- Breite des Drawers nicht verändern, solange Editing-Modus oder Reports genutzt werden
- Besonders kritisch bei:
  - `page-mod-quiz-report`
  - `page-mod-assign-grading`
  - Seiten mit rechter Blockleiste

### CSS-Validator meldet Fehler
- Der Selektor `:is()` wird von manchen Validatoren nicht akzeptiert  
  → Daher im SCSS explizit ausgeschrieben (`body.category-53, body.category-114, body.category-88`)

---

## Best Practice: Keine Layout-Hacks
- **Keine manuelle Verschiebung von Containern** (`margin-left` bei Drawer-Öffnung)  
  → verhindert Überlagerungen, besonders bei Editing-Modus oder Reports
- **Breite des Drawers** nur auf Standard belassen (285px)
- **Responsive Layout** über Boost / Standardklassen steuern (`main-inner`, `.header-maxwidth`)
- **Hintergrund- und Stilelemente** selektiv auf Kategorie + Seite anwenden
- Änderungen sollen **robust, upgrade-sicher und cache-freundlich** bleiben
