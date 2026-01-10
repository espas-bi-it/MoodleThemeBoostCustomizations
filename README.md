
# MoodleThemeBoostCustomizations

## Introduction
This repository contains customizations for selected Moodle categories  
(`category-53`, `category-114`, `category-88`) based on the **Boost theme**.

The goal is to provide a consistent visual appearance for:
- page backgrounds
- drawers
- typography
- quiz question blocks
- cards and alerts
- competence blocks
- quickgrade comment fields

All changes are **category-scoped**, upgrade-safe, and avoid layout hacks.

---

## Design Goals & Rationale

These customizations are not purely visual.  
They are based on concrete didactic, usability, and maintenance goals.

### Primary Goals
- More space for content and complex questions
- Reduced scrolling and improved readability
- Clear visual separation between:
  - tasks
  - information
  - instructions
  - grading context
- Consistent look & feel across all courses
- Upgrade-safe implementation without theme hacks

All decisions documented below directly map to implemented CSS and templates.

---

## Supported Moodle Categories

The following Moodle categories are covered by these theme customizations:

- **category-53** – *Gezielte Vorbereitung (GV)*
- **category-88** – *Abklärung (AK)*
- **category-114** – *Dokumentationen*

---

## Installation

### 1. Insert Script
- **Location:**  
  `Webseiten Administration → Designs → Zusätzliches HTML -> Vor dem Schliessen von </body> (additionalhtmlfooter)`

- **Content:**
```html
<script>
document.addEventListener("DOMContentLoaded", function () {

  // Theme for demo / sandbox categories
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
### 2. Insert Raw SCSS

-   **Location:** `Webseiten Administration → Designs → Boost → Zahnrad → Erweiterte Einstellungen → Raw SCSS (theme_boost | scss)`
    
-   **Content:**
```css
/* ======================================================
   DEMO / SANDBOX – Courses
   Applies to:
   - category-53
   - category-114
   - category-88
   ====================================================== */

/* ------------------------------------------------------
   Body font size for sandbox categories
------------------------------------------------------ */
body.category-53,
body.category-114,
body.category-88 {
  font-size: 0.9375rem; /* equals 15px */
}


/* ======================================================
   1) PAGE BACKGROUND (selected pages only)
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
   2) DRAWER – remove link underline
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
   3) CONTAINER / MAIN-INNER (Boost default)
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
   5) DRAWER (Boost default width)
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

/* No manual container shifting
   → prevents overlaps (quiz reports, right blocks, editing mode)
*/


/* ======================================================
   6) TYPOGRAPHY / CODE
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
   7) CARDS / ALERTS / TABLES
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
   9) COMPETENCE BLOCK
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
   10) ALERTS (fine tuning)
   ====================================================== */

body.category-53 .alert,
body.category-114 .alert,
body.category-88 .alert {
  font-size: 0.9rem;
  font-weight: 500;
}


/* ======================================================
   11) TIME TRACKING
   ====================================================== */

div#course-time-tracking i {
  color: #ffffff !important;
  margin-right: 2px !important;
}


/* ======================================================
   12) GRADER INFORMATION
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
## Layout Decisions (Mapped to Implementation)

### Container Width & Spacing
- Main content width increased to `1200px`
- Implemented via:
  - `.main-inner`
  - `.header-maxwidth`
- Result:
  - more horizontal space for questions and code
  - reduced vertical scrolling
  - improved overview for complex tasks

No manual container shifting is used to avoid drawer-related issues.

### Question Background & Visual Separation
- Question blocks use a neutral white background
- Replaces the former light-blue background
- Implemented via:
  - `.que .formulation`
- Benefits:
  - reduced visual noise
  - better focus on question content
  - clearer separation from informational blocks

### Question & Content Structure

#### Semantic Markup
- All questions use valid, semantic Bootstrap markup
- No inline styles
- Bootstrap utility classes preferred over custom CSS

This ensures:
- consistent rendering
- lower maintenance cost
- easier global style changes

#### Visual Context Separation
- Quiz questions are visually separated from:
  - information blocks
  - installation instructions
  - meta content
- Context colors are used consistently:
  - Blue → information
  - Red → task / assignment

Font Awesome icons are used sparingly to support orientation.

### Media, Code & Readability

#### Code Blocks
- Code is always wrapped in `<pre><code>`
- Ensures:
  - clean separation from text
  - readable submissions
  - easier grading

#### Images
- Images use subtle shadows
- Improves separation from surrounding text
- Reduces visual blending with content blocks

### Grader Information Templates
- Unified grader information structure
- Includes:
  - grading rules
  - point allocation
  - evaluation hints

Goal:
- consistent grading across courses
- reproducible assessments
- reduced subjective interpretation

### Maintenance & Future-Proofing
- All visual changes are controlled via CSS
- No course content needs modification for design updates
- Category-scoped selectors ensure isolation
- No dependency on undocumented Moodle internals

This allows:
- safe Moodle upgrades
- global design changes
- scalable course development

## Troubleshooting

### Changes are not visible
- Purge Moodle caches:  
  `Website-Administration → Entwicklung → Cache leeren`
- Hard reload browser cache (`Ctrl + F5`)
- Verify that the **Boost theme** is active

### Raw SCSS is not applied
- Ensure the code is placed in  
  **“Raw SCSS (theme_boost | scss)”**
- Check for syntax errors (missing `{}`, invalid selectors)
- Always **purge caches after saving**

### JavaScript is not executed
- Script must be placed under  
  **“Before </body> is closed (additionalhtmlfooter)”**
- Open browser DevTools → **Console** → check for errors
- Verify the `<body>` contains the expected category class  
  (e.g. `category-53`)

### Styles only apply on some pages
- Verify the page has the expected `page-*` body ID  
  (e.g. `page-course-view-topics`, `page-mod-quiz-view`)

### Drawer or content overlaps
- Do **not** force container shifts (`margin-left` when drawer opens)
- Keep drawer width at the **Boost default (285px)**
- Especially critical for:
  - `page-mod-quiz-report`
  - `page-mod-assign-grading`
  - Pages with a right-side block region

### CSS validator reports errors
- Some validators do not accept the `:is()` selector  
  → Therefore all selectors are explicitly written:
  - `body.category-53`
  - `body.category-114`
  - `body.category-88`

## Best Practice: No Layout Hacks
- No manual container shifting when the drawer opens
- Keep drawer width at the Boost default
- Use Boost layout classes (`main-inner`, `.header-maxwidth`)
- Apply styles only via **category + page selectors**
- Keep changes **robust, upgrade-safe, and cache-friendly**

## Reusable HTML Template Blocks
For consistent content creation, a set of **reusable HTML template blocks** is provided.  
These blocks are designed for use within Moodle content areas and follow the established Boost-based styling and conventions used in this project.

### Available Template Blocks
- **Quiz Info Block**
- **Installation Instructions**
- **Image Block**
- **Internal Link**
- **External Link**
- **Code Block**
- **Alert**
- **Alert (Subtle)**
- **To-Do Block**
- **Accordion**

## Answer & Grading Concept

### Answer Templates
- Free-text questions provide predefined answer areas
- Clearly communicates:
  - what must be submitted
  - expected format (text, code, screenshots)

Instructions are intentionally placed in the answer template,
not in the question text.

Result:
- fewer incorrect submissions
- less clarification effort during grading

### Template Collection
All template examples are available in the following Moodle course:

🔗 **Template Library (Moodle Course)**  
https://moodle-espas.ch/course/view.php?id=193

> ℹ️ These templates are intended to be copied directly into Moodle HTML editors  
> (e.g. Page, Label, Description fields, or Activity introductions).

## Course Template for New Courses
A **course template** is available for creating new courses.  
It already contains the commonly used structure and elements aligned with the templates and styles defined in this repository.

🔗 **Course Template (Moodle Course)**  
https://moodle-espas.ch/course/view.php?id=194

> ℹ️ Recommended starting point for new courses to ensure consistent layout, structure,  
> and reuse of established HTML components.
