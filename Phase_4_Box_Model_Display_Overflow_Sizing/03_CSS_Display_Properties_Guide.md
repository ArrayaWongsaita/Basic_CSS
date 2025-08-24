# CSS Display Properties: คู่มือฉบับสมบูรณ์

## ภาพรวม Display Property

`display` property เป็นหนึ่งใน property ที่สำคัญที่สุดใน CSS ที่กำหนดว่า element จะแสดงตัวอย่างไรในหน้าเว็บ โดยมีผลต่อการจัด layout, การไหลของเนื้อหา และการโต้ตอบกับ elements อื่นๆ

### Display Values พื้นฐาน

```css
/* Display values หลัก */
.display-examples {
  /* Block-level elements */
  display: block;

  /* Inline elements */
  display: inline;

  /* Hybrid behavior */
  display: inline-block;

  /* Hide element */
  display: none;

  /* Modern layout methods */
  display: flex;
  display: grid;
  display: table;
}

/* Default display values ของ HTML elements */
/*
div, p, h1-h6, ul, ol, li = block
span, a, strong, em, img = inline
button, input, select = inline-block
*/
```

## 1. display: block - Block-level Elements

### ความหมายและพฤติกรรม

Block-level elements จะสร้าง "block" ใหม่ในการไหลของเอกสาร โดยจะขึ้นบรรทัดใหม่ก่อนและหลัง element และยึดครองความกว้างเต็มที่มี

### คุณสมบัติของ Block Elements

```css
/* พฤติกรรมพื้นฐานของ block elements */
.block-behavior {
  display: block;

  /* ✅ สามารถกำหนด width และ height ได้ */
  width: 300px;
  height: 200px;

  /* ✅ สามารถใช้ margin และ padding ทุกด้านได้ */
  margin: 20px 0;
  padding: 15px;

  /* ✅ ขึ้นบรรทัดใหม่เสมอ */
  /* ✅ ยึดครองความกว้างเต็มที่มี (ถ้าไม่กำหนด width) */

  background-color: #f0f9ff;
  border: 2px solid #3b82f6;
}

/* ตัวอย่างการใช้งาน block elements */
.container-block {
  display: block;
  max-width: 1200px;
  margin: 0 auto; /* จัดกลางด้วย auto margin */
  padding: 2rem;
  background: white;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.heading-block {
  display: block;
  font-size: 2rem;
  font-weight: bold;
  margin-bottom: 1rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #e5e7eb;
}

.paragraph-block {
  display: block;
  margin-bottom: 1.5rem;
  line-height: 1.6;
  text-align: justify;
}

/* การจัด layout ด้วย block elements */
.layout-blocks {
  .header-block {
    display: block;
    width: 100%;
    height: 80px;
    background: #1f2937;
    color: white;
    padding: 0 2rem;
    margin-bottom: 2rem;
  }

  .main-block {
    display: block;
    width: 70%;
    float: left; /* วิธีเก่าในการจัด layout */
    padding-right: 2rem;
  }

  .sidebar-block {
    display: block;
    width: 30%;
    float: right;
    background: #f9fafb;
    padding: 1rem;
  }

  .footer-block {
    display: block;
    clear: both; /* ล้าง float */
    width: 100%;
    height: 60px;
    background: #374151;
    color: white;
    margin-top: 2rem;
  }
}
```

### การเปลี่ยน Inline Elements เป็น Block

```css
/* เปลี่ยน inline elements เป็น block */
.inline-to-block {
  /* Elements ที่ปกติเป็น inline */
  span,
  a,
  strong,
  em {
    display: block;

    /* ตอนนี้สามารถใช้ width, height ได้แล้ว */
    width: 200px;
    height: 50px;
    margin: 10px 0;
    padding: 15px;
    background: #dbeafe;
    border: 1px solid #3b82f6;
    text-align: center;
    line-height: 50px;
  }
}

/* Navigation ที่เปลี่ยนเป็น block */
.nav-block {
  .nav-link {
    display: block; /* เปลี่ยนจาก inline เป็น block */
    padding: 1rem 1.5rem;
    margin-bottom: 0.5rem;
    background: #f3f4f6;
    color: #374151;
    text-decoration: none;
    border-radius: 0.375rem;
    transition: background-color 0.2s ease;
  }

  .nav-link:hover {
    background: #e5e7eb;
  }

  .nav-link.active {
    background: #3b82f6;
    color: white;
  }
}

/* Button เป็น block */
.button-block {
  display: block;
  width: 100%;
  padding: 1rem;
  margin-bottom: 1rem;
  background: #10b981;
  color: white;
  border: none;
  border-radius: 0.5rem;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

.button-block:hover {
  background: #059669;
}
```

### Responsive Block Elements

```css
/* Responsive behavior ของ block elements */
.responsive-blocks {
  display: block;
  width: 100%;
  margin-bottom: 2rem;
  padding: 1.5rem;
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

/* Mobile first approach */
@media (min-width: 768px) {
  .responsive-blocks {
    width: 48%;
    display: inline-block; /* เปลี่ยนเป็น inline-block ใน tablet+ */
    margin-right: 2%;
    vertical-align: top;
  }
}

@media (min-width: 1024px) {
  .responsive-blocks {
    width: 31.33%;
    margin-right: 2%;
  }
}

@media (min-width: 1024px) {
  .responsive-blocks:nth-child(3n) {
    margin-right: 0; /* ลบ margin ขวาของ item ที่ 3, 6, 9 */
  }
}
```

## 2. display: inline - Inline Elements

### ความหมายและพฤติกรรม

Inline elements ไหลไปตามเนื้อหาและไม่ขึ้นบรรทัดใหม่ มักใช้สำหรับเนื้อหาภายในประโยคหรือย่อหน้า

### คุณสมบัติของ Inline Elements

```css
/* พฤติกรรมพื้นฐานของ inline elements */
.inline-behavior {
  display: inline;

  /* ❌ ไม่สามารถกำหนด width และ height ได้ */
  /* width: 200px; - ไม่มีผล */
  /* height: 100px; - ไม่มีผล */

  /* ✅ สามารถใช้ margin และ padding ซ้าย-ขวาได้ */
  margin: 0 10px; /* บน-ล่าง ไม่มีผล */
  padding: 5px 15px; /* บน-ล่าง อาจทับซ้อนกับบรรทัดอื่น */

  /* ✅ ไหลต่อเนื่องในบรรทัดเดียวกัน */
  /* ✅ ขนาดขึ้นอยู่กับเนื้อหาภายใน */

  background-color: #fef3c7;
  border: 1px solid #f59e0b;
}

/* ตัวอย่างการใช้งาน inline elements */
.text-formatting {
  .highlight {
    display: inline;
    background: #fde68a;
    padding: 0.125rem 0.25rem;
    border-radius: 0.125rem;
  }

  .badge {
    display: inline;
    background: #3b82f6;
    color: white;
    padding: 0.25rem 0.5rem;
    border-radius: 0.75rem;
    font-size: 0.875rem;
    margin-left: 0.5rem;
  }

  .code-inline {
    display: inline;
    background: #f1f5f9;
    color: #dc2626;
    padding: 0.125rem 0.375rem;
    border-radius: 0.25rem;
    font-family: 'Courier New', monospace;
    font-size: 0.9em;
  }
}

/* Links และ interactive inline elements */
.inline-links {
  .link-normal {
    display: inline;
    color: #3b82f6;
    text-decoration: underline;
    margin: 0 0.25rem;
  }

  .link-normal:hover {
    color: #1d4ed8;
    text-decoration: none;
  }

  .link-button {
    display: inline;
    background: #10b981;
    color: white;
    padding: 0.375rem 0.75rem;
    border-radius: 0.25rem;
    text-decoration: none;
    margin: 0 0.5rem;
    transition: background-color 0.2s ease;
  }

  .link-button:hover {
    background: #059669;
  }
}
```

### การจัดการ Inline Elements

```css
/* Navigation แบบ inline */
.nav-inline {
  .nav-list {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  .nav-item {
    display: inline; /* list items เป็น inline */
    margin-right: 2rem;
  }

  .nav-link {
    display: inline;
    color: #374151;
    text-decoration: none;
    padding: 0.5rem 0;
    border-bottom: 2px solid transparent;
    transition: all 0.2s ease;
  }

  .nav-link:hover,
  .nav-link.active {
    color: #3b82f6;
    border-bottom-color: #3b82f6;
  }
}

/* Text formatting elements */
.text-inline-elements {
  .bold {
    display: inline;
    font-weight: bold;
  }
  .italic {
    display: inline;
    font-style: italic;
  }
  .underline {
    display: inline;
    text-decoration: underline;
  }

  .small-caps {
    display: inline;
    font-variant: small-caps;
    letter-spacing: 0.05em;
  }

  .subscript {
    display: inline;
    font-size: 0.75em;
    vertical-align: sub;
  }

  .superscript {
    display: inline;
    font-size: 0.75em;
    vertical-align: super;
  }
}

/* Image inline behavior */
.inline-images {
  .icon-inline {
    display: inline;
    width: 1em; /* ขนาดตาม font-size */
    height: 1em;
    vertical-align: -0.125em; /* จัดตำแหน่งกับข้อความ */
    margin: 0 0.25rem;
  }

  .avatar-inline {
    display: inline;
    width: 2rem;
    height: 2rem;
    border-radius: 50%;
    vertical-align: middle;
    margin: 0 0.5rem;
  }
}
```

### ข้อจำกัดของ Inline Elements

```css
/* ปัญหาและข้อจำกัดของ inline elements */
.inline-limitations {
  /* ❌ ไม่สามารถกำหนด width/height */
  .cannot-size {
    display: inline;
    width: 200px; /* ไม่มีผล */
    height: 100px; /* ไม่มีผล */
    background: #fee2e2;
  }

  /* ❌ margin/padding บน-ล่าง ไม่ทำงานปกติ */
  .margin-padding-issues {
    display: inline;
    margin: 20px; /* บน-ล่าง ไม่มีผล */
    padding: 20px; /* บน-ล่าง อาจทับซ้อน */
    background: #fef3c7;
  }

  /* ❌ vertical-align ยาก */
  .alignment-problems {
    display: inline;
    vertical-align: middle; /* ไม่เสมอที่จะทำงาน */
    background: #e0f2fe;
  }
}

/* Solutions: เปลี่ยนเป็น inline-block */
.inline-solutions {
  .better-approach {
    display: inline-block; /* แก้ปัญหาได้ */
    width: 200px;
    height: 100px;
    margin: 20px 10px;
    padding: 15px;
    vertical-align: top;
    background: #dcfce7;
  }
}
```

## 3. display: inline-block - Hybrid Behavior

### ความหมายและพฤติกรรม

`inline-block` รวมข้อดีของทั้ง inline และ block โดยไหลในบรรทัดเดียวกันเหมือน inline แต่สามารถกำหนดขนาดได้เหมือน block

### คุณสมบัติของ Inline-block Elements

```css
/* พฤติกรรมของ inline-block elements */
.inline-block-behavior {
  display: inline-block;

  /* ✅ สามารถกำหนด width และ height ได้ */
  width: 200px;
  height: 150px;

  /* ✅ สามารถใช้ margin และ padding ทุกด้านได้ */
  margin: 15px;
  padding: 20px;

  /* ✅ ไหลในบรรทัดเดียวกัน (ถ้ามีพื้นที่) */
  /* ✅ สามารถจัด vertical-align ได้ */
  vertical-align: top;

  background-color: #f0fdf4;
  border: 2px solid #22c55e;
  text-align: center;
}

/* การใช้งานพื้นฐาน */
.inline-block-examples {
  .card-inline-block {
    display: inline-block;
    width: 300px;
    height: 200px;
    margin: 1rem;
    padding: 1.5rem;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    vertical-align: top;
    text-align: left;
  }

  .button-inline-block {
    display: inline-block;
    padding: 0.75rem 1.5rem;
    margin: 0.5rem;
    background: #3b82f6;
    color: white;
    text-decoration: none;
    border-radius: 0.375rem;
    transition: background-color 0.2s ease;
  }

  .button-inline-block:hover {
    background: #2563eb;
  }
}
```

### Grid Systems ด้วย Inline-block

```css
/* Grid system ด้วย inline-block */
.grid-inline-block {
  font-size: 0; /* แก้ปัญหา whitespace */
  text-align: center;
}

.col-inline-block {
  display: inline-block;
  vertical-align: top;
  font-size: 1rem; /* คืนค่า font-size */
  text-align: left;
  padding: 0 1rem;
  box-sizing: border-box;
}

/* Grid columns */
.col-1 {
  width: 8.333%;
}
.col-2 {
  width: 16.666%;
}
.col-3 {
  width: 25%;
}
.col-4 {
  width: 33.333%;
}
.col-6 {
  width: 50%;
}
.col-8 {
  width: 66.666%;
}
.col-9 {
  width: 75%;
}
.col-12 {
  width: 100%;
}

/* Responsive grid */
@media (max-width: 768px) {
  .col-inline-block {
    width: 100% !important;
    margin-bottom: 1rem;
  }
}

/* การใช้งาน grid */
.grid-example {
  .header-col {
    display: inline-block;
    width: 100%;
    padding: 2rem 1rem;
    background: #1f2937;
    color: white;
    margin-bottom: 2rem;
  }

  .main-col {
    display: inline-block;
    width: 66.666%;
    padding: 0 1rem;
    vertical-align: top;
  }

  .sidebar-col {
    display: inline-block;
    width: 33.333%;
    padding: 0 1rem;
    vertical-align: top;
    background: #f9fafb;
  }
}
```

### Practical Inline-block Patterns

```css
/* Navigation horizontal */
.nav-horizontal {
  background: #ffffff;
  border-bottom: 1px solid #e5e7eb;
  padding: 0 2rem;
}

.nav-item-horizontal {
  display: inline-block;
  margin-right: 2rem;
}

.nav-link-horizontal {
  display: inline-block;
  padding: 1rem 0;
  color: #374151;
  text-decoration: none;
  border-bottom: 2px solid transparent;
  transition: all 0.2s ease;
}

.nav-link-horizontal:hover,
.nav-link-horizontal.active {
  color: #3b82f6;
  border-bottom-color: #3b82f6;
}

/* Feature cards */
.feature-cards {
  text-align: center;
  padding: 4rem 0;
}

.feature-card {
  display: inline-block;
  width: 300px;
  margin: 1rem;
  padding: 2rem;
  background: white;
  border-radius: 1rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  vertical-align: top;
  text-align: center;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.feature-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

.feature-icon {
  display: inline-block;
  width: 4rem;
  height: 4rem;
  margin-bottom: 1rem;
  background: #3b82f6;
  border-radius: 50%;
  line-height: 4rem;
  color: white;
  font-size: 1.5rem;
}

/* Button groups */
.button-group {
  display: inline-block;
  border-radius: 0.375rem;
  overflow: hidden;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.button-group .btn {
  display: inline-block;
  padding: 0.75rem 1rem;
  background: white;
  color: #374151;
  text-decoration: none;
  border: 1px solid #d1d5db;
  border-right: none;
  margin: 0;
  transition: all 0.2s ease;
}

.button-group .btn:last-child {
  border-right: 1px solid #d1d5db;
}

.button-group .btn:hover {
  background: #f3f4f6;
  z-index: 1;
  position: relative;
}

.button-group .btn.active {
  background: #3b82f6;
  color: white;
  z-index: 2;
  position: relative;
}
```

### การแก้ปัญหา Inline-block

```css
/* ปัญหา whitespace ระหว่าง inline-block elements */
.whitespace-problem {
  /* ปัญหา: มี space ระหว่าง elements */
  .problem-demo .item {
    display: inline-block;
    width: 25%;
    background: #fee2e2;
    /* จะมี space ระหว่าง items */
  }
}

/* วิธีแก้ปัญหา whitespace */
.whitespace-solutions {
  /* วิธีที่ 1: font-size: 0 ใน parent */
  .solution-1 {
    font-size: 0;
  }

  .solution-1 .item {
    display: inline-block;
    width: 25%;
    font-size: 1rem; /* คืนค่า font-size */
    background: #dcfce7;
  }

  /* วิธีที่ 2: float ร่วมกับ clearfix */
  .solution-2::after {
    content: '';
    display: table;
    clear: both;
  }

  .solution-2 .item {
    float: left;
    width: 25%;
    background: #dbeafe;
  }

  /* วิธีที่ 3: flexbox (modern approach) */
  .solution-3 {
    display: flex;
  }

  .solution-3 .item {
    flex: 1;
    background: #f3e8ff;
  }
}

/* การจัด vertical alignment */
.vertical-alignment {
  height: 200px;
  line-height: 200px; /* สำหรับ single line */
}

.aligned-top {
  display: inline-block;
  vertical-align: top;
  line-height: normal;
  width: 150px;
  height: 100px;
  background: #fef3c7;
}

.aligned-middle {
  display: inline-block;
  vertical-align: middle;
  line-height: normal;
  width: 150px;
  height: 150px;
  background: #fce7f3;
}

.aligned-bottom {
  display: inline-block;
  vertical-align: bottom;
  line-height: normal;
  width: 150px;
  height: 80px;
  background: #e0f2fe;
}
```

## 4. display: none - Hiding Elements

### ความหมายและพฤติกรรม

`display: none` จะซ่อน element และลบออกจาก document flow ทำให้ไม่มีการยึดครองพื้นที่ใดๆ

### การใช้งาน Display None

```css
/* Basic hiding */
.hide-element {
  display: none; /* ซ่อนและไม่ยึดครองพื้นที่ */
}

.show-element {
  display: block; /* แสดง element กลับมา */
}

/* Conditional showing */
.conditional-display {
  /* Hide by default */
  .mobile-only {
    display: none;
  }

  .desktop-only {
    display: block;
  }

  /* Show on mobile */
  @media (max-width: 768px) {
    .mobile-only {
      display: block;
    }

    .desktop-only {
      display: none;
    }
  }
}

/* JavaScript interaction */
.js-toggle {
  /* CSS classes for JavaScript */
  .hidden {
    display: none;
  }

  .visible {
    display: block;
  }

  /* Inline-block version */
  .visible-inline {
    display: inline-block;
  }
}

/* Print styles */
@media print {
  .no-print {
    display: none; /* ซ่อนเมื่อพิมพ์ */
  }

  .print-only {
    display: block; /* แสดงเฉพาะเมื่อพิมพ์ */
  }
}

@media screen {
  .print-only {
    display: none; /* ซ่อนบนหน้าจอ */
  }
}
```

### Display None vs Visibility Hidden

```css
/* เปรียบเทียบวิธีซ่อน elements */
.hiding-comparison {
  /* display: none - ลบออกจาก layout */
  .display-none {
    display: none;
    /* ไม่ยึดครองพื้นที่ */
    /* ไม่สามารถ focus ได้ */
    /* Screen readers จะไม่อ่าน */
  }

  /* visibility: hidden - ซ่อนแต่ยังยึดครองพื้นที่ */
  .visibility-hidden {
    visibility: hidden;
    /* ยังยึดครองพื้นที่อยู่ */
    /* ไม่สามารถ focus ได้ */
    /* Screen readers จะไม่อ่าน */
  }

  /* opacity: 0 - โปร่งใสแต่ยังอยู่ใน layout */
  .opacity-zero {
    opacity: 0;
    /* ยังยึดครองพื้นที่อยู่ */
    /* ยังสามารถ focus ได้ */
    /* Screen readers ยังอ่านได้ */
  }

  /* position: absolute + off-screen */
  .screen-reader-only {
    position: absolute;
    left: -9999px;
    /* ไม่ยึดครองพื้นที่ */
    /* Screen readers ยังอ่านได้ */
  }
}
```

### Responsive Display Control

```css
/* Responsive display utilities */
.responsive-display {
  /* Hide on different screen sizes */
  .hide-mobile {
    @media (max-width: 767px) {
      display: none;
    }
  }

  .hide-tablet {
    @media (min-width: 768px) and (max-width: 1023px) {
      display: none;
    }
  }

  .hide-desktop {
    @media (min-width: 1024px) {
      display: none;
    }
  }

  /* Show only on specific sizes */
  .show-mobile-only {
    display: none;

    @media (max-width: 767px) {
      display: block;
    }
  }

  .show-tablet-only {
    display: none;

    @media (min-width: 768px) and (max-width: 1023px) {
      display: block;
    }
  }

  .show-desktop-only {
    display: none;

    @media (min-width: 1024px) {
      display: block;
    }
  }
}

/* Complex responsive patterns */
.responsive-patterns {
  .responsive-nav {
    /* Mobile: hidden by default */
    display: none;
    position: absolute;
    top: 100%;
    left: 0;
    width: 100%;
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .responsive-nav.active {
    /* Show when toggled */
    display: block;
  }

  @media (min-width: 768px) {
    .responsive-nav {
      /* Desktop: always visible */
      display: flex !important;
      position: static;
      width: auto;
      background: none;
      box-shadow: none;
    }
  }

  .nav-toggle {
    display: block;

    @media (min-width: 768px) {
      display: none; /* Hide hamburger on desktop */
    }
  }
}
```

### Animation และ Transitions

```css
/* Animated showing/hiding */
.animated-display {
  /* CSS transitions ไม่ทำงานกับ display: none */
  /* ต้องใช้วิธีอื่น */

  .fade-toggle {
    opacity: 1;
    visibility: visible;
    transition: opacity 0.3s ease, visibility 0.3s ease;
  }

  .fade-toggle.hidden {
    opacity: 0;
    visibility: hidden;
  }

  /* Slide animation */
  .slide-toggle {
    max-height: 1000px; /* ใส่ค่าที่ใหญ่พอ */
    overflow: hidden;
    transition: max-height 0.3s ease;
  }

  .slide-toggle.hidden {
    max-height: 0;
  }

  /* Scale animation */
  .scale-toggle {
    transform: scale(1);
    opacity: 1;
    transition: transform 0.3s ease, opacity 0.3s ease;
  }

  .scale-toggle.hidden {
    transform: scale(0);
    opacity: 0;
  }
}

/* Modal/Overlay patterns */
.modal-patterns {
  .modal-overlay {
    display: none; /* Hidden by default */
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    z-index: 1000;
  }

  .modal-overlay.active {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .modal-content {
    background: white;
    border-radius: 0.5rem;
    padding: 2rem;
    max-width: 500px;
    width: 90%;
    max-height: 90vh;
    overflow-y: auto;
  }

  /* Dropdown patterns */
  .dropdown {
    position: relative;
  }

  .dropdown-menu {
    display: none;
    position: absolute;
    top: 100%;
    left: 0;
    background: white;
    border: 1px solid #e5e7eb;
    border-radius: 0.375rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    z-index: 100;
  }

  .dropdown:hover .dropdown-menu,
  .dropdown.active .dropdown-menu {
    display: block;
  }
}
```

## 5. Practical Patterns และ Use Cases

### Component Patterns

```css
/* Card component ที่ใช้ display หลายแบบ */
.card-component {
  /* Container เป็น block */
  display: block;
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  margin-bottom: 2rem;
}

.card-header {
  /* Header เป็น block */
  display: block;
  padding: 1.5rem;
  background: #f8fafc;
  border-bottom: 1px solid #e2e8f0;
}

.card-title {
  /* Title เป็น block */
  display: block;
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.card-subtitle {
  /* Subtitle เป็น block */
  display: block;
  color: #64748b;
  font-size: 0.875rem;
}

.card-body {
  /* Body เป็น block */
  display: block;
  padding: 1.5rem;
}

.card-actions {
  /* Actions container เป็น block */
  display: block;
  padding: 1rem 1.5rem;
  background: #f8fafc;
  border-top: 1px solid #e2e8f0;
}

.card-btn {
  /* Buttons เป็น inline-block */
  display: inline-block;
  padding: 0.5rem 1rem;
  margin-right: 0.5rem;
  background: #3b82f6;
  color: white;
  text-decoration: none;
  border-radius: 0.25rem;
  font-size: 0.875rem;
  transition: background-color 0.2s ease;
}

.card-btn:hover {
  background: #2563eb;
}

.card-btn.secondary {
  background: #6b7280;
}

.card-btn.secondary:hover {
  background: #4b5563;
}

/* Responsive card behavior */
@media (min-width: 768px) {
  .card-grid .card-component {
    display: inline-block;
    width: calc(50% - 1rem);
    margin: 0 0.5rem 2rem;
    vertical-align: top;
  }
}

@media (min-width: 1024px) {
  .card-grid .card-component {
    width: calc(33.333% - 1rem);
  }
}
```

### Navigation Patterns

```css
/* Complex navigation ที่ใช้ display หลายแบบ */
.navigation-complex {
  /* Main nav container */
  .main-nav {
    display: block;
    background: white;
    border-bottom: 1px solid #e5e7eb;
    position: relative;
  }

  .nav-container {
    display: block;
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 1rem;
    position: relative;
  }

  /* Logo */
  .nav-logo {
    display: inline-block;
    padding: 1rem 0;
    font-size: 1.5rem;
    font-weight: bold;
    color: #1f2937;
    text-decoration: none;
  }

  /* Desktop menu */
  .nav-menu {
    display: none; /* Hidden on mobile */

    @media (min-width: 768px) {
      display: inline-block;
      float: right;
    }
  }

  .nav-item {
    display: inline-block;
    position: relative;
  }

  .nav-link {
    display: inline-block;
    padding: 1.5rem 1rem;
    color: #4b5563;
    text-decoration: none;
    transition: color 0.2s ease;
  }

  .nav-link:hover,
  .nav-link.active {
    color: #3b82f6;
  }

  /* Dropdown */
  .nav-dropdown {
    display: none; /* Hidden by default */
    position: absolute;
    top: 100%;
    left: 0;
    background: white;
    border: 1px solid #e5e7eb;
    border-radius: 0.375rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    min-width: 200px;
    z-index: 100;
  }

  .nav-item:hover .nav-dropdown {
    display: block;
  }

  .nav-dropdown-item {
    display: block;
    padding: 0.75rem 1rem;
    color: #4b5563;
    text-decoration: none;
    transition: background-color 0.2s ease;
  }

  .nav-dropdown-item:hover {
    background: #f3f4f6;
  }

  /* Mobile toggle */
  .nav-toggle {
    display: inline-block;
    float: right;
    padding: 1rem;
    margin-top: 0.5rem;
    background: none;
    border: none;
    cursor: pointer;

    @media (min-width: 768px) {
      display: none;
    }
  }

  /* Mobile menu */
  .nav-mobile {
    display: none; /* Hidden by default */
    position: absolute;
    top: 100%;
    left: 0;
    width: 100%;
    background: white;
    border-top: 1px solid #e5e7eb;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    z-index: 50;

    @media (min-width: 768px) {
      display: none !important; /* Always hidden on desktop */
    }
  }

  .nav-mobile.active {
    display: block;
  }

  .nav-mobile-item {
    display: block;
    padding: 1rem;
    color: #4b5563;
    text-decoration: none;
    border-bottom: 1px solid #f3f4f6;
    transition: background-color 0.2s ease;
  }

  .nav-mobile-item:hover {
    background: #f8fafc;
  }
}
```

### Utility Classes System

```css
/* Utility classes สำหรับ display */
.display-utilities {
  /* Basic display utilities */
  .d-none {
    display: none;
  }
  .d-inline {
    display: inline;
  }
  .d-inline-block {
    display: inline-block;
  }
  .d-block {
    display: block;
  }
  .d-flex {
    display: flex;
  }
  .d-grid {
    display: grid;
  }
  .d-table {
    display: table;
  }
  .d-table-cell {
    display: table-cell;
  }

  /* Responsive display utilities */
  .d-sm-none {
    @media (min-width: 576px) {
      display: none;
    }
  }
  .d-sm-inline {
    @media (min-width: 576px) {
      display: inline;
    }
  }
  .d-sm-inline-block {
    @media (min-width: 576px) {
      display: inline-block;
    }
  }
  .d-sm-block {
    @media (min-width: 576px) {
      display: block;
    }
  }

  .d-md-none {
    @media (min-width: 768px) {
      display: none;
    }
  }
  .d-md-inline {
    @media (min-width: 768px) {
      display: inline;
    }
  }
  .d-md-inline-block {
    @media (min-width: 768px) {
      display: inline-block;
    }
  }
  .d-md-block {
    @media (min-width: 768px) {
      display: block;
    }
  }

  .d-lg-none {
    @media (min-width: 1024px) {
      display: none;
    }
  }
  .d-lg-inline {
    @media (min-width: 1024px) {
      display: inline;
    }
  }
  .d-lg-inline-block {
    @media (min-width: 1024px) {
      display: inline-block;
    }
  }
  .d-lg-block {
    @media (min-width: 1024px) {
      display: block;
    }
  }

  .d-xl-none {
    @media (min-width: 1280px) {
      display: none;
    }
  }
  .d-xl-inline {
    @media (min-width: 1280px) {
      display: inline;
    }
  }
  .d-xl-inline-block {
    @media (min-width: 1280px) {
      display: inline-block;
    }
  }
  .d-xl-block {
    @media (min-width: 1280px) {
      display: block;
    }
  }
}

/* Print utilities */
.print-utilities {
  .d-print-none {
    @media print {
      display: none;
    }
  }
  .d-print-inline {
    @media print {
      display: inline;
    }
  }
  .d-print-inline-block {
    @media print {
      display: inline-block;
    }
  }
  .d-print-block {
    @media print {
      display: block;
    }
  }
}
```

## Best Practices Summary

### เมื่อไหร่ควรใช้ Display Type ไหน

```css
/* 🎯 Decision guide */

/* ใช้ block เมื่อ: */
.use-block {
  /* ✅ ต้องการ element ที่ยึดครองความกว้างเต็ม */
  /* ✅ ต้องการขึ้นบรรทัดใหม่ */
  /* ✅ ต้องการกำหนด width/height */
  /* ✅ เป็น container หลัก */

  display: block;
  width: 100%;
  margin-bottom: 2rem;
}

/* ใช้ inline เมื่อ: */
.use-inline {
  /* ✅ อยู่ในเนื้อหาข้อความ */
  /* ✅ ไม่ต้องการขึ้นบรรทัดใหม่ */
  /* ✅ ขนาดตามเนื้อหา */
  /* ✅ เป็น text formatting */

  display: inline;
  background: #fef3c7;
  padding: 0.125rem 0.25rem;
}

/* ใช้ inline-block เมื่อ: */
.use-inline-block {
  /* ✅ ต้องการกำหนด width/height */
  /* ✅ ต้องการอยู่ในบรรทัดเดียวกัน */
  /* ✅ สร้าง grid แบบเก่า */
  /* ✅ button หรือ card ที่เรียงกัน */

  display: inline-block;
  width: 200px;
  vertical-align: top;
}

/* ใช้ none เมื่อ: */
.use-none {
  /* ✅ ต้องการซ่อน element */
  /* ✅ Responsive hiding */
  /* ✅ JavaScript toggle */
  /* ✅ Print styles */

  display: none;
}
```

### Modern Alternatives

```css
/* 🔄 Modern approaches */

/* แทน inline-block grid ใช้ flexbox */
.modern-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.modern-grid-item {
  flex: 1;
  min-width: 200px;
}

/* แทน inline-block ใช้ CSS Grid */
.css-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1rem;
}

/* แทน float layout ใช้ flexbox */
.modern-layout {
  display: flex;
}

.main-content {
  flex: 2;
}

.sidebar {
  flex: 1;
}

/* แทน display: none animation */
.modern-toggle {
  opacity: 1;
  visibility: visible;
  transition: opacity 0.3s ease, visibility 0.3s ease;
}

.modern-toggle.hidden {
  opacity: 0;
  visibility: hidden;
}
```

การเข้าใจ Display Properties เป็นพื้นฐานสำคัญในการสร้าง layout และการจัดการการแสดงผลของ elements ใน CSS!
