# CSS Box Model: คู่มือฉบับสมบูรณ์

## ภาพรวม CSS Box Model

CSS Box Model เป็นแนวคิดพื้นฐานที่สำคัญที่สุดในการเข้าใจ CSS โดยทุก element ในหน้าเว็บจะถูกมองเป็น "กล่อง" ที่ประกอบด้วย 4 ส่วนหลัก: **Content**, **Padding**, **Border**, และ **Margin**

### โครงสร้าง Box Model

```css
/* การแสดงโครงสร้าง Box Model */
.box-model-example {
  /* Content Area */
  width: 200px;
  height: 100px;

  /* Padding - พื้นที่รอบ content */
  padding: 20px;

  /* Border - เส้นขอบ */
  border: 5px solid #3b82f6;

  /* Margin - พื้นที่รอบ element */
  margin: 15px;

  /* Visual styling */
  background-color: #f3f4f6;
  color: #1f2937;
}

/*
Visual representation:
┌─────────────────────────────────────┐ ←── Margin (15px)
│ ┌─────────────────────────────────┐ │ ←── Border (5px)
│ │ ┌─────────────────────────────┐ │ │ ←── Padding (20px)
│ │ │                             │ │ │
│ │ │         Content             │ │ │ ←── Content (200px × 100px)
│ │ │       (200px × 100px)       │ │ │
│ │ │                             │ │ │
│ │ └─────────────────────────────┘ │ │
│ └─────────────────────────────────┘ │
└─────────────────────────────────────┘

Total width = margin + border + padding + content + padding + border + margin
Total width = 15 + 5 + 20 + 200 + 20 + 5 + 15 = 280px
Total height = 15 + 5 + 20 + 100 + 20 + 5 + 15 = 180px
*/
```

## 1. Content Area: พื้นที่เนื้อหา

### ความหมายและการทำงาน

Content Area คือพื้นที่ที่ใช้แสดงเนื้อหาจริงของ element เช่น ข้อความ รูปภาพ หรือ element อื่นๆ

### การกำหนดขนาด Content

```css
/* Basic content sizing */
.content-sizing {
  /* กำหนดขนาด content area */
  width: 300px;
  height: 200px;

  /* Content จะแสดงในพื้นที่นี้ */
  background-color: #fef3c7;
  border: 2px solid #f59e0b;
}

/* Responsive content */
.responsive-content {
  /* Flexible width */
  width: 100%;
  max-width: 600px;
  min-width: 200px;

  /* Auto height based on content */
  height: auto;
  min-height: 150px;

  background-color: #dbeafe;
}

/* Content with different units */
.content-units {
  /* Percentage-based */
  width: 50%;
  height: 200px;

  /* Viewport-based */
  width: 80vw;
  height: 30vh;

  /* REM-based */
  width: 25rem;
  height: 15rem;

  /* Flexible sizing */
  width: clamp(200px, 50vw, 600px);
  height: clamp(150px, 20vh, 400px);
}

/* Content overflow behavior */
.content-overflow {
  width: 200px;
  height: 100px;
  background-color: #f3f4f6;
  border: 1px solid #d1d5db;

  /* How to handle content overflow */
  overflow: visible; /* Default - content flows out */
  overflow: hidden; /* Hide overflowing content */
  overflow: scroll; /* Always show scrollbars */
  overflow: auto; /* Show scrollbars when needed */
}

/* Text content examples */
.text-content {
  width: 300px;
  padding: 1rem;
  line-height: 1.6;

  /* Text wrapping */
  word-wrap: break-word;
  overflow-wrap: break-word;

  /* Text overflow */
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

/* Image content */
.image-content {
  width: 300px;
  height: 200px;

  /* Image sizing within content area */
  img {
    width: 100%;
    height: 100%;
    object-fit: cover; /* cover, contain, fill, scale-down, none */
    object-position: center;
  }
}
```

### Content Box vs Border Box

```css
/* Default box-sizing: content-box */
.content-box {
  box-sizing: content-box; /* Default */
  width: 200px;
  height: 100px;
  padding: 20px;
  border: 5px solid #3b82f6;

  /* Total width = 200 + 20 + 20 + 5 + 5 = 250px */
  /* Total height = 100 + 20 + 20 + 5 + 5 = 150px */
}

/* Modern approach: border-box */
.border-box {
  box-sizing: border-box;
  width: 200px;
  height: 100px;
  padding: 20px;
  border: 5px solid #3b82f6;

  /* Total width = 200px (padding และ border รวมอยู่ใน width) */
  /* Content width = 200 - 20 - 20 - 5 - 5 = 150px */
  /* Total height = 100px */
  /* Content height = 100 - 20 - 20 - 5 - 5 = 50px */
}

/* Global border-box (แนะนำ) */
*,
*::before,
*::after {
  box-sizing: border-box;
}

/* หรือ */
html {
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}
```

## 2. Padding: พื้นที่รอบ Content

### ความหมายและการทำงาน

Padding คือพื้นที่โปร่งใสระหว่าง content และ border ใช้สร้างพื้นที่หายใจให้กับเนื้อหา

### Padding Properties

```css
/* Individual padding properties */
.padding-individual {
  padding-top: 10px;
  padding-right: 15px;
  padding-bottom: 20px;
  padding-left: 25px;

  background-color: #fef2f2;
  border: 2px solid #ef4444;
}

/* Shorthand padding */
.padding-shorthand {
  /* All sides equal */
  padding: 20px;

  /* Vertical | Horizontal */
  padding: 15px 25px;

  /* Top | Horizontal | Bottom */
  padding: 10px 20px 15px;

  /* Top | Right | Bottom | Left (clockwise) */
  padding: 10px 15px 20px 25px;
}

/* Padding with different units */
.padding-units {
  /* Pixels */
  padding: 16px;

  /* REM (recommended) */
  padding: 1rem;

  /* EM (relative to font-size) */
  padding: 1.5em;

  /* Percentage (relative to parent width) */
  padding: 5%;

  /* Mixed units */
  padding: 1rem 2rem;
  padding: 0.5rem 5%;
}

/* Responsive padding */
.responsive-padding {
  /* Base padding */
  padding: 1rem;

  /* Tablet */
  @media (min-width: 768px) {
    padding: 1.5rem;
  }

  /* Desktop */
  @media (min-width: 1024px) {
    padding: 2rem;
  }

  /* Large screens */
  @media (min-width: 1440px) {
    padding: 2.5rem;
  }
}

/* Fluid padding with clamp */
.fluid-padding {
  padding: clamp(1rem, 5vw, 3rem);
  padding: clamp(0.5rem, 2vh, 2rem) clamp(1rem, 5vw, 4rem);
}
```

### Practical Padding Examples

```css
/* Button padding */
.btn {
  padding: 0.75rem 1.5rem;
  border: 1px solid transparent;
  border-radius: 0.375rem;
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.2s ease;
}

.btn-sm {
  padding: 0.5rem 1rem;
}
.btn-lg {
  padding: 1rem 2rem;
}
.btn-xl {
  padding: 1.25rem 2.5rem;
}

/* Card padding */
.card {
  padding: 1.5rem;
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.card-header {
  padding: 1rem 1.5rem;
  margin: -1.5rem -1.5rem 1rem;
  border-bottom: 1px solid #e5e7eb;
}

.card-footer {
  padding: 1rem 1.5rem;
  margin: 1rem -1.5rem -1.5rem;
  border-top: 1px solid #e5e7eb;
}

/* Form element padding */
.form-input {
  padding: 0.75rem 1rem;
  border: 1px solid #d1d5db;
  border-radius: 0.375rem;
  width: 100%;
  font-size: 1rem;
}

.form-textarea {
  padding: 0.75rem 1rem;
  min-height: 120px;
  resize: vertical;
}

/* Navigation padding */
.nav-link {
  padding: 1rem 1.5rem;
  display: block;
  text-decoration: none;
  transition: background-color 0.2s ease;
}

.nav-link:hover {
  background-color: #f3f4f6;
}

/* Content sections */
.section {
  padding: 4rem 0; /* Vertical rhythm */
}

.container {
  padding: 0 1rem; /* Horizontal spacing */
  max-width: 1200px;
  margin: 0 auto;
}

@media (min-width: 768px) {
  .container {
    padding: 0 2rem;
  }
}
```

## 3. Border: เส้นขอบ

### ความหมายและการทำงาน

Border คือเส้นขอบที่อยู่ระหว่าง padding และ margin สามารถมีสี ความหนา และรูปแบบต่างๆ

### Border Properties

```css
/* Individual border properties */
.border-individual {
  border-width: 2px;
  border-style: solid;
  border-color: #3b82f6;

  /* หรือแยกตามด้าน */
  border-top-width: 1px;
  border-right-width: 2px;
  border-bottom-width: 3px;
  border-left-width: 4px;

  border-top-style: solid;
  border-right-style: dashed;
  border-bottom-style: dotted;
  border-left-style: double;

  border-top-color: #ef4444;
  border-right-color: #10b981;
  border-bottom-color: #3b82f6;
  border-left-color: #f59e0b;
}

/* Shorthand border */
.border-shorthand {
  /* width | style | color */
  border: 2px solid #3b82f6;

  /* Individual sides */
  border-top: 1px solid #ef4444;
  border-right: 2px dashed #10b981;
  border-bottom: 3px dotted #3b82f6;
  border-left: 4px double #f59e0b;
}

/* Border styles */
.border-styles {
  .solid {
    border: 2px solid #000;
  }
  .dashed {
    border: 2px dashed #000;
  }
  .dotted {
    border: 2px dotted #000;
  }
  .double {
    border: 4px double #000;
  }
  .groove {
    border: 4px groove #000;
  }
  .ridge {
    border: 4px ridge #000;
  }
  .inset {
    border: 4px inset #000;
  }
  .outset {
    border: 4px outset #000;
  }
  .none {
    border: none;
  }
  .hidden {
    border: hidden;
  }
}

/* Border radius */
.border-radius {
  /* All corners */
  border-radius: 0.5rem;

  /* Individual corners */
  border-top-left-radius: 0.5rem;
  border-top-right-radius: 1rem;
  border-bottom-right-radius: 1.5rem;
  border-bottom-left-radius: 2rem;

  /* Shorthand (clockwise from top-left) */
  border-radius: 0.5rem 1rem 1.5rem 2rem;

  /* Vertical | Horizontal */
  border-radius: 1rem / 0.5rem;

  /* Elliptical corners */
  border-radius: 2rem 1rem 2rem 1rem / 1rem 2rem 1rem 2rem;
}

/* Common border radius patterns */
.border-patterns {
  .rounded-none {
    border-radius: 0;
  }
  .rounded-sm {
    border-radius: 0.125rem;
  }
  .rounded {
    border-radius: 0.25rem;
  }
  .rounded-md {
    border-radius: 0.375rem;
  }
  .rounded-lg {
    border-radius: 0.5rem;
  }
  .rounded-xl {
    border-radius: 0.75rem;
  }
  .rounded-2xl {
    border-radius: 1rem;
  }
  .rounded-3xl {
    border-radius: 1.5rem;
  }
  .rounded-full {
    border-radius: 9999px;
  }

  /* Partial rounding */
  .rounded-t {
    border-radius: 0.25rem 0.25rem 0 0;
  }
  .rounded-r {
    border-radius: 0 0.25rem 0.25rem 0;
  }
  .rounded-b {
    border-radius: 0 0 0.25rem 0.25rem;
  }
  .rounded-l {
    border-radius: 0.25rem 0 0 0.25rem;
  }
}
```

### Practical Border Examples

```css
/* Card with subtle border */
.card-border {
  border: 1px solid #e5e7eb;
  border-radius: 0.5rem;
  padding: 1.5rem;
  background: white;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

/* Focus states */
.input-focus {
  border: 1px solid #d1d5db;
  border-radius: 0.375rem;
  padding: 0.75rem 1rem;
  transition: border-color 0.2s ease, box-shadow 0.2s ease;
}

.input-focus:focus {
  outline: none;
  border-color: #3b82f6;
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
}

/* Status borders */
.status-borders {
  .success {
    border: 2px solid #10b981;
    background-color: #d1fae5;
  }

  .warning {
    border: 2px solid #f59e0b;
    background-color: #fef3c7;
  }

  .error {
    border: 2px solid #ef4444;
    background-color: #fee2e2;
  }

  .info {
    border: 2px solid #3b82f6;
    background-color: #dbeafe;
  }
}

/* Decorative borders */
.decorative-borders {
  /* Accent border */
  .accent-border {
    border-left: 4px solid #3b82f6;
    padding-left: 1rem;
  }

  /* Quote styling */
  .quote-border {
    border-left: 3px solid #6b7280;
    padding-left: 1.5rem;
    font-style: italic;
  }

  /* Card with top accent */
  .card-accent {
    border-top: 4px solid #10b981;
    border: 1px solid #e5e7eb;
    border-radius: 0.5rem;
  }
}

/* Button borders */
.button-borders {
  .btn-outline {
    border: 2px solid #3b82f6;
    background: transparent;
    color: #3b82f6;
    padding: 0.75rem 1.5rem;
    border-radius: 0.375rem;
    transition: all 0.2s ease;
  }

  .btn-outline:hover {
    background: #3b82f6;
    color: white;
  }

  .btn-ghost {
    border: 1px solid transparent;
    background: transparent;
    color: #6b7280;
  }

  .btn-ghost:hover {
    border-color: #d1d5db;
    background: #f9fafb;
  }
}

/* Image borders */
.image-borders {
  .avatar {
    border: 3px solid white;
    border-radius: 50%;
    box-shadow: 0 0 0 1px rgba(0, 0, 0, 0.1);
  }

  .image-frame {
    border: 8px solid #f3f4f6;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }
}
```

## 4. Margin: พื้นที่รอบ Element

### ความหมายและการทำงาน

Margin คือพื้นที่โปร่งใสรอบๆ element ใช้สร้างระยะห่างระหว่าง elements

### Margin Properties

```css
/* Individual margin properties */
.margin-individual {
  margin-top: 10px;
  margin-right: 15px;
  margin-bottom: 20px;
  margin-left: 25px;
}

/* Shorthand margin */
.margin-shorthand {
  /* All sides equal */
  margin: 20px;

  /* Vertical | Horizontal */
  margin: 15px 25px;

  /* Top | Horizontal | Bottom */
  margin: 10px 20px 15px;

  /* Top | Right | Bottom | Left (clockwise) */
  margin: 10px 15px 20px 25px;
}

/* Auto margins for centering */
.margin-centering {
  /* Center horizontally */
  margin: 0 auto;
  width: 300px;

  /* Center vertically and horizontally */
  margin: auto;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  width: 200px;
  height: 100px;
}

/* Negative margins */
.negative-margins {
  /* Pull element closer */
  margin-top: -10px;
  margin-left: -15px;

  /* Overlap elements */
  margin-bottom: -20px;

  /* Extend beyond container */
  margin: 0 -2rem;
  width: calc(100% + 4rem);
}

/* Margin collapse */
.margin-collapse-demo {
  .element-1 {
    margin-bottom: 30px;
    background: #fef2f2;
  }

  .element-2 {
    margin-top: 20px;
    background: #f0f9ff;
  }

  /* Actual margin between elements = max(30px, 20px) = 30px */
  /* ไม่ใช่ 30px + 20px = 50px */
}
```

### Margin Patterns และ Best Practices

```css
/* Typography margins */
.typography-margins {
  h1,
  h2,
  h3,
  h4,
  h5,
  h6 {
    margin: 0 0 1rem 0; /* Bottom margin only */
  }

  p {
    margin: 0 0 1.5rem 0;
  }

  ul,
  ol {
    margin: 0 0 1.5rem 0;
    padding-left: 2rem;
  }

  li {
    margin-bottom: 0.5rem;
  }

  /* Last element remove bottom margin */
  :last-child {
    margin-bottom: 0;
  }
}

/* Section spacing */
.section-margins {
  .section {
    margin: 4rem 0;
  }

  .section-sm {
    margin: 2rem 0;
  }

  .section-lg {
    margin: 6rem 0;
  }

  .section-xl {
    margin: 8rem 0;
  }
}

/* Component spacing */
.component-margins {
  .card + .card {
    margin-top: 2rem; /* Space between cards */
  }

  .btn + .btn {
    margin-left: 1rem; /* Space between buttons */
  }

  .form-group {
    margin-bottom: 1.5rem;
  }

  .form-group:last-child {
    margin-bottom: 0;
  }
}

/* Grid spacing with margins */
.grid-margins {
  .grid-container {
    margin: 0 -1rem; /* Negative margin for grid */
  }

  .grid-item {
    margin: 0 1rem 2rem; /* Horizontal and bottom spacing */
  }

  /* Alternative: Use gap instead */
  .grid-modern {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem; /* Modern approach - no margin needed */
  }
}

/* Responsive margins */
.responsive-margins {
  /* Base margins */
  margin: 1rem 0;

  @media (min-width: 768px) {
    margin: 2rem 0;
  }

  @media (min-width: 1024px) {
    margin: 3rem 0;
  }
}

/* Utility margins */
.margin-utilities {
  .m-0 {
    margin: 0;
  }
  .m-1 {
    margin: 0.25rem;
  }
  .m-2 {
    margin: 0.5rem;
  }
  .m-4 {
    margin: 1rem;
  }
  .m-6 {
    margin: 1.5rem;
  }
  .m-8 {
    margin: 2rem;
  }

  .mt-4 {
    margin-top: 1rem;
  }
  .mr-4 {
    margin-right: 1rem;
  }
  .mb-4 {
    margin-bottom: 1rem;
  }
  .ml-4 {
    margin-left: 1rem;
  }

  .mx-4 {
    margin-left: 1rem;
    margin-right: 1rem;
  }
  .my-4 {
    margin-top: 1rem;
    margin-bottom: 1rem;
  }

  .mx-auto {
    margin-left: auto;
    margin-right: auto;
  }
}
```

## 5. Box Model Debugging และ Tools

### Visual Debugging

```css
/* Debug box model */
.debug-box-model {
  outline: 2px solid red;
  outline-offset: -1px;
}

.debug-box-model * {
  outline: 1px solid rgba(255, 0, 0, 0.3);
  outline-offset: -1px;
}

/* Show different areas */
.debug-content {
  background-color: rgba(255, 0, 0, 0.1);
}

.debug-padding {
  background-color: rgba(0, 255, 0, 0.1);
}

.debug-border {
  border: 2px solid rgba(0, 0, 255, 0.5);
}

.debug-margin {
  box-shadow: 0 0 0 10px rgba(255, 255, 0, 0.2);
}

/* Box model information */
.box-info::before {
  content: 'Width: ' attr(data-width) ' | Height: ' attr(data-height)
    ' | Padding: ' attr(data-padding) ' | Border: ' attr(data-border)
    ' | Margin: ' attr(data-margin);
  position: absolute;
  top: -2rem;
  left: 0;
  font-size: 0.75rem;
  background: rgba(0, 0, 0, 0.8);
  color: white;
  padding: 0.25rem 0.5rem;
  border-radius: 0.25rem;
  white-space: nowrap;
  z-index: 1000;
}
```

### Box Model Reset

```css
/* Modern box model reset */
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

/* Alternative reset */
html {
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}

body {
  margin: 0;
  padding: 0;
  line-height: 1.6;
}

h1,
h2,
h3,
h4,
h5,
h6,
p,
ul,
ol,
dl,
dd,
blockquote,
pre,
table,
fieldset,
figure {
  margin: 0;
  padding: 0;
}

/* Sensible defaults */
img {
  max-width: 100%;
  height: auto;
}

button,
input,
select,
textarea {
  font: inherit;
}

button {
  border: none;
  background: none;
  cursor: pointer;
}
```

## 6. Common Box Model Patterns

### Card Components

```css
/* Basic card */
.card {
  /* Content area */
  background: white;

  /* Padding for inner spacing */
  padding: 1.5rem;

  /* Border for definition */
  border: 1px solid #e5e7eb;
  border-radius: 0.5rem;

  /* Margin for separation from other elements */
  margin-bottom: 2rem;

  /* Shadow for depth */
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

/* Card variations */
.card-compact {
  padding: 1rem;
  margin-bottom: 1rem;
}

.card-spacious {
  padding: 2rem;
  margin-bottom: 3rem;
}

.card-featured {
  padding: 2rem;
  border: 2px solid #3b82f6;
  margin: 2rem 0;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}
```

### Button System

```css
/* Button base */
.btn {
  /* Content styling */
  font-size: 1rem;
  font-weight: 500;
  text-align: center;
  text-decoration: none;

  /* Padding for click area */
  padding: 0.75rem 1.5rem;

  /* Border for structure */
  border: 1px solid transparent;
  border-radius: 0.375rem;

  /* No margin by default */
  margin: 0;

  /* Background and interaction */
  background: #3b82f6;
  color: white;
  cursor: pointer;
  transition: all 0.2s ease;
}

/* Button spacing in groups */
.btn-group .btn + .btn {
  margin-left: 0.5rem;
}

.btn-group-vertical .btn + .btn {
  margin-top: 0.5rem;
  margin-left: 0;
}
```

### Form Layout

```css
/* Form container */
.form {
  max-width: 500px;
  margin: 0 auto;
  padding: 2rem;
  background: white;
  border: 1px solid #e5e7eb;
  border-radius: 0.5rem;
}

/* Form groups */
.form-group {
  margin-bottom: 1.5rem;
}

.form-group:last-child {
  margin-bottom: 0;
}

/* Form elements */
.form-label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: 500;
}

.form-input {
  width: 100%;
  padding: 0.75rem 1rem;
  border: 1px solid #d1d5db;
  border-radius: 0.375rem;
  background: white;
}

.form-help {
  margin-top: 0.25rem;
  font-size: 0.875rem;
  color: #6b7280;
}
```

## 7. Best Practices Summary

### DO's ✅

```css
/* ✅ ใช้ border-box เป็น default */
*,
*::before,
*::after {
  box-sizing: border-box;
}

/* ✅ ใช้ consistent spacing scale */
:root {
  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-4: 1rem;
  --space-6: 1.5rem;
  --space-8: 2rem;
}

/* ✅ ใช้ margin bottom เป็นหลัก */
.typography {
  margin: 0 0 1.5rem 0;
}

/* ✅ Reset margins sensibly */
h1,
h2,
h3,
h4,
h5,
h6,
p {
  margin: 0 0 1rem 0;
}

/* ✅ ใช้ padding สำหรับ internal spacing */
.component {
  padding: 1.5rem;
}
```

### DON'Ts ❌

```css
/* ❌ หลีกเลี่ยง content-box ใน modern layouts */
.avoid-content-box {
  box-sizing: content-box; /* ยากต่อการคำนวณ */
}

/* ❌ หลีกเลี่ยง margin collapse ที่ไม่ต้องการ */
.avoid-double-margins {
  margin: 1rem 0 1rem 0; /* อาจ collapse กับ element อื่น */
}

/* ❌ หลีกเลี่ยง negative margins ที่ไม่จำเป็น */
.avoid-negative {
  margin-left: -100px; /* อาจทำให้ layout พัง */
}

/* ❌ หลีกเลี่ยง fixed dimensions ที่ไม่ responsive */
.avoid-fixed {
  width: 500px; /* ไม่ responsive */
  height: 300px;
}
```

### Quick Reference

```css
/* Box model quick reference */
.box-model-ref {
  /* Content */
  width: 200px;
  height: 100px;

  /* Padding - internal spacing */
  padding: 1rem;

  /* Border - visual boundary */
  border: 1px solid #ccc;
  border-radius: 0.5rem;

  /* Margin - external spacing */
  margin: 1rem 0;

  /* Box sizing */
  box-sizing: border-box;
}

/* ผลลัพธ์ขั้นสุดท้าย:
   - Total width = 200px (รวม padding + border แล้ว)
   - Total height = 100px (รวม padding + border แล้ว)
   - Space around element = 1rem top/bottom
*/
```

การเข้าใจ Box Model เป็นพื้นฐานสำคัญในการออกแบบ layout ที่สวยงามและใช้งานได้ดี!
