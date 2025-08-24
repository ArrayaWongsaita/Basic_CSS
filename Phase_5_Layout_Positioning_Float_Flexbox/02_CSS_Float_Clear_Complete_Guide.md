# CSS Float & Clear: คู่มือฉบับสมบูรณ์

## ภาพรวม Float Property

`float` เป็น CSS property ที่มีประวัติความเป็นมายาวนาน ออกแบบมาสำหรับการจัดวาง text ให้ล้อมรอบรูปภาพ แต่กลายเป็นเครื่องมือหลักในการสร้าง layout ก่อนที่ Flexbox และ Grid จะเข้ามา ปัจจุบันมีการใช้งานเฉพาะกรณีพิเศษ

### ประวัติและวิวัฒนาการ

```css
/* ตัวอย่างการใช้งานแรกเริ่ม (1990s) */
.historical-float {
  /* จุดประสงค์เดิม: ข้อความล้อมรอบรูป */
  img {
    float: left;
    margin: 0 1rem 1rem 0;
  }

  /* วิวัฒนาการมาเป็น layout tool (2000s) */
  .sidebar {
    float: left;
    width: 300px;
  }

  .main-content {
    float: right;
    width: calc(100% - 320px);
  }
}

/* ปัจจุบัน: ใช้เฉพาะกรณีพิเศษ (2020s+) */
.modern-usage {
  /* ยังคงใช้สำหรับ text wrapping */
  .article-image {
    float: left;
    margin: 0 1rem 1rem 0;
    max-width: 300px;
  }

  /* Layout ใช้ Flexbox/Grid แทน */
  .layout-modern {
    display: flex; /* ไม่ใช้ float */
    gap: 2rem;
  }
}
```

## 1. Float Property Values และ Behaviors

### ค่าต่างๆ ของ Float

```css
/* Float values */
.float-values {
  /* none (ค่าเริ่มต้น) */
  float: none; /* element อยู่ใน normal flow */

  /* left */
  float: left; /* ลอยไปทางซ้าย */

  /* right */
  float: right; /* ลอยไปทางขวา */

  /* inherit */
  float: inherit; /* รับค่าจาก parent */
}

/* พฤติกรรมของ float */
.float-behavior {
  /* Float จะทำให้ element */
  /* 1. ออกจาก normal document flow */
  /* 2. อยู่ติดขอบ container */
  /* 3. Elements อื่นไหลรอบๆ */
  /* 4. กลายเป็น block-level (แม้จะเป็น inline เดิม) */
}

/* ตัวอย่างพื้นฐาน */
.basic-float-example {
  /* Container */
  width: 100%;
  border: 2px solid #e2e8f0;
  padding: 1rem;
  overflow: hidden; /* clearfix */
}

.floated-box {
  float: left;
  width: 200px;
  height: 150px;
  background-color: #3b82f6;
  color: white;
  padding: 1rem;
  margin: 0 1rem 1rem 0;
}

.text-content {
  /* ข้อความจะไหลรอบ floated element */
  line-height: 1.6;
  text-align: justify;
}
```

### การทำงานของ Float

```css
/* Float mechanics */
.float-mechanics {
  /* 1. Float ออกจาก normal flow */
  .removed-from-flow {
    float: left;
    /* parent จะไม่นับความสูงของ element นี้ */
  }

  /* 2. Text และ inline elements ไหลรอบ */
  .text-wrapping {
    /* text จะหลีกทางให้ floated element */
    /* แต่ block elements จะทับ */
  }

  /* 3. Float ต่อเนื่องกัน */
  .multiple-floats {
    .float-1 {
      float: left;
      width: 100px;
    }
    .float-2 {
      float: left;
      width: 150px;
    }
    .float-3 {
      float: left;
      width: 120px;
    }
    /* จะเรียงต่อกันจากซ้ายไปขวา */
  }

  /* 4. Float collision */
  .float-collision {
    .tall-float {
      float: left;
      height: 200px;
      width: 100px;
    }
    .short-float {
      float: left;
      height: 100px;
      width: 100px;
    }
    /* short-float จะอยู่ข้างๆ tall-float */
  }
}

/* ตัวอย่างการไหลของ text */
.text-flow-example {
  padding: 2rem;
  font-size: 1.1rem;
  line-height: 1.8;
}

.pull-quote {
  float: right;
  width: 300px;
  padding: 1.5rem;
  margin: 0 0 1rem 2rem;
  background-color: #f8fafc;
  border-left: 4px solid #3b82f6;
  font-style: italic;
  font-size: 1.25rem;
  color: #1e40af;
}

/* Magazine-style layout */
.magazine-layout {
  columns: 2;
  column-gap: 2rem;
  text-align: justify;
}

.magazine-image {
  float: left;
  width: 200px;
  height: auto;
  margin: 0 1rem 1rem 0;
  border-radius: 0.5rem;
}

.magazine-callout {
  float: right;
  width: 180px;
  padding: 1rem;
  margin: 1rem 0 1rem 1rem;
  background-color: #fef3c7;
  border-radius: 0.5rem;
  font-size: 0.9rem;
  font-weight: 600;
}
```

## 2. Clear Property: การควบคุม Float

### ความหมายและการใช้งาน

```css
/* Clear property values */
.clear-values {
  clear: none; /* ค่าเริ่มต้น - ไม่ clear */
  clear: left; /* clear floated elements ทางซ้าย */
  clear: right; /* clear floated elements ทางขวา */
  clear: both; /* clear floated elements ทุกด้าน */
  clear: inherit; /* รับค่าจาก parent */
}

/* การใช้ clear ควบคุม layout */
.clear-examples {
  /* Float elements */
  .box-1 {
    float: left;
    width: 200px;
    height: 100px;
    background: #ef4444;
  }
  .box-2 {
    float: left;
    width: 200px;
    height: 150px;
    background: #10b981;
  }
  .box-3 {
    float: left;
    width: 200px;
    height: 120px;
    background: #3b82f6;
  }

  /* Clear เพื่อเริ่มบรรทัดใหม่ */
  .new-line {
    clear: both; /* เริ่มใต้ floated elements ทั้งหมด */
    background: #f59e0b;
    padding: 1rem;
  }

  /* Clear เฉพาะด้าน */
  .clear-left-only {
    clear: left; /* เริ่มใต้ left floated elements เท่านั้น */
  }

  .clear-right-only {
    clear: right; /* เริ่มใต้ right floated elements เท่านั้น */
  }
}

/* Practical clearing */
.practical-clearing {
  /* Section breaks */
  .section-break {
    clear: both;
    height: 2rem; /* spacing */
    background: linear-gradient(to right, transparent, #e2e8f0, transparent);
  }

  /* Footer that clears everything */
  .footer {
    clear: both;
    margin-top: 2rem;
    padding: 2rem;
    background-color: #1f2937;
    color: white;
  }

  /* Sidebar clearing */
  .sidebar-end {
    clear: left; /* clear เฉพาะ sidebar */
    padding-top: 1rem;
    border-top: 1px solid #e2e8f0;
  }
}
```

### Clearfix Technique

```css
/* คลาสสิก clearfix methods */

/* 1. Overflow method (ง่ายที่สุด) */
.clearfix-overflow {
  overflow: hidden; /* หรือ auto */
  /* ข้อเสีย: อาจตัดเนื้อหาที่ออกนอกขอบ */
}

/* 2. Float method */
.clearfix-float {
  float: left;
  width: 100%;
  /* ข้อเสีย: element เองก็กลายเป็น floated */
}

/* 3. Classic clearfix (เก่า) */
.clearfix-classic:after {
  content: '.';
  display: block;
  height: 0;
  clear: both;
  visibility: hidden;
}

/* 4. Modern clearfix (แนะนำ) ⭐ */
.clearfix::after {
  content: '';
  display: table;
  clear: both;
}

/* 5. Micro clearfix (นิยมมาก) */
.micro-clearfix::before,
.micro-clearfix::after {
  content: '';
  display: table;
}

.micro-clearfix::after {
  clear: both;
}

/* 6. Display flow-root (ทันสมัยที่สุด) */
.modern-clearfix {
  display: flow-root; /* สร้าง new formatting context */
  /* ไม่ต้องใช้ pseudo-elements */
}

/* การใช้งาน clearfix */
.container-with-floats {
  /* เลือกวิธีใดวิธีหนึ่ง */
  @extend .micro-clearfix; /* Sass */
  /* หรือ */
  display: flow-root; /* Modern */
  /* หรือ */
  overflow: hidden; /* Simple */
}

.floated-children {
  float: left;
  width: 50%;
  padding: 1rem;
  background-color: #f3f4f6;
}
```

## 3. Layout Patterns (ประวัติศาสตร์)

### Traditional Float Layouts

```css
/* 2-column layout (คลาสสิก) */
.two-column-float {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  overflow: hidden; /* clearfix */
}

.sidebar-float {
  float: left;
  width: 300px;
  padding: 1rem;
  background-color: #f8fafc;
  border-right: 1px solid #e2e8f0;
}

.main-content-float {
  float: right;
  width: calc(100% - 320px); /* 300px + 20px margin */
  padding: 1rem;
}

/* 3-column layout */
.three-column-float {
  max-width: 1200px;
  margin: 0 auto;
  overflow: hidden;
}

.left-sidebar {
  float: left;
  width: 200px;
  padding: 1rem;
  background-color: #fef3c7;
}

.right-sidebar {
  float: right;
  width: 200px;
  padding: 1rem;
  background-color: #fecaca;
}

.center-content {
  margin: 0 220px; /* เว้นที่สำหรับ sidebars */
  padding: 1rem;
  background-color: #f0fdf4;
}

/* Holy Grail Layout (ด้วย float) */
.holy-grail-float {
  min-height: 100vh;
  display: flex;
  flex-direction: column; /* ใช้ flex สำหรับ header/footer */
}

.header-float,
.footer-float {
  background-color: #1f2937;
  color: white;
  padding: 1rem;
}

.content-wrapper {
  flex: 1;
  overflow: hidden; /* clearfix */
}

.main-holy-grail {
  float: left;
  width: 100%;
  background-color: #ffffff;
}

.main-holy-grail-inner {
  margin: 0 200px; /* เว้นที่สำหรับ sidebars */
  padding: 2rem;
}

.left-holy-grail {
  float: left;
  width: 200px;
  margin-left: -100%; /* ย้ายไปซ้าย */
  background-color: #f8fafc;
  padding: 1rem;
}

.right-holy-grail {
  float: left;
  width: 200px;
  margin-left: -200px; /* ย้ายไปขวา */
  background-color: #f8fafc;
  padding: 1rem;
}

/* Grid system ด้วย float */
.float-grid {
  width: 100%;
  overflow: hidden;
  margin-bottom: 1rem;
}

.float-col {
  float: left;
  padding: 0 15px;
  box-sizing: border-box;
}

.col-1 {
  width: 8.33333%;
}
.col-2 {
  width: 16.66667%;
}
.col-3 {
  width: 25%;
}
.col-4 {
  width: 33.33333%;
}
.col-6 {
  width: 50%;
}
.col-8 {
  width: 66.66667%;
}
.col-9 {
  width: 75%;
}
.col-12 {
  width: 100%;
}

/* Responsive float grid */
@media (max-width: 768px) {
  .float-col {
    float: none;
    width: 100% !important;
    margin-bottom: 1rem;
  }
}
```

### Card Layouts

```css
/* Card masonry ด้วย float */
.masonry-float {
  column-count: 3;
  column-gap: 1rem;
}

.masonry-item {
  display: inline-block;
  width: 100%;
  margin-bottom: 1rem;
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  padding: 1rem;
  break-inside: avoid; /* ไม่ให้แบ่งข้าม column */
}

/* Float-based card grid */
.card-grid-float {
  overflow: hidden;
  margin: -0.5rem; /* negative margin สำหรับ spacing */
}

.card-float {
  float: left;
  width: calc(33.333% - 1rem);
  margin: 0.5rem;
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  padding: 1.5rem;
  box-sizing: border-box;
}

@media (max-width: 1024px) {
  .card-float {
    width: calc(50% - 1rem);
  }
}

@media (max-width: 640px) {
  .card-float {
    width: calc(100% - 1rem);
  }
}

/* Pinterest-style layout */
.pinterest-float {
  columns: auto;
  column-width: 250px;
  column-gap: 1rem;
  padding: 1rem;
}

.pin-item {
  display: inline-block;
  width: 100%;
  margin-bottom: 1rem;
  break-inside: avoid;
  background: white;
  border-radius: 1rem;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.2s ease;
}

.pin-item:hover {
  transform: translateY(-2px);
}

.pin-image {
  width: 100%;
  height: auto;
  display: block;
}

.pin-content {
  padding: 1rem;
}
```

## 4. Modern Use Cases (กรณีที่ยังใช้ Float)

### Text Wrapping และ Editorial Design

```css
/* Article images ที่ text ล้อมรอบ */
.article-content {
  max-width: 65ch;
  margin: 0 auto;
  padding: 2rem;
  line-height: 1.8;
  font-size: 1.1rem;
}

.article-image {
  max-width: 300px;
  height: auto;
  border-radius: 0.5rem;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  margin-bottom: 1rem;
}

.article-image--left {
  float: left;
  margin-right: 2rem;
  margin-bottom: 1rem;
}

.article-image--right {
  float: right;
  margin-left: 2rem;
  margin-bottom: 1rem;
}

.article-image--small {
  max-width: 200px;
}

.article-image--large {
  max-width: 400px;
}

/* Pull quotes */
.pull-quote {
  float: right;
  width: 250px;
  padding: 1.5rem;
  margin: 1rem 0 1rem 2rem;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border-radius: 0.75rem;
  font-size: 1.25rem;
  font-style: italic;
  text-align: center;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.15);
}

.pull-quote::before {
  content: '"';
  font-size: 3rem;
  opacity: 0.3;
  display: block;
  line-height: 0.8;
}

.pull-quote::after {
  content: '"';
  font-size: 3rem;
  opacity: 0.3;
  display: block;
  line-height: 0.8;
  text-align: right;
}

/* Figure captions */
.figure-float {
  float: left;
  max-width: 350px;
  margin: 0 2rem 1rem 0;
  background: white;
  border-radius: 0.5rem;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.figure-float img {
  width: 100%;
  height: auto;
  display: block;
}

.figure-caption {
  padding: 1rem;
  font-size: 0.9rem;
  color: #6b7280;
  font-style: italic;
  line-height: 1.5;
}

/* Info boxes */
.info-box {
  float: right;
  width: 280px;
  padding: 1.5rem;
  margin: 1rem 0 1rem 2rem;
  background-color: #eff6ff;
  border: 1px solid #bfdbfe;
  border-radius: 0.5rem;
  font-size: 0.95rem;
}

.info-box h4 {
  margin: 0 0 1rem 0;
  color: #1e40af;
  font-size: 1.1rem;
}

/* Magazine-style drop caps */
.drop-cap::first-letter {
  float: left;
  font-size: 4rem;
  line-height: 3rem;
  margin: 0.5rem 0.5rem 0 0;
  font-weight: bold;
  color: #3b82f6;
  font-family: Georgia, serif;
}
```

### Icon และ UI Elements

```css
/* Icon alignment ใน text */
.icon-text {
  line-height: 1.6;
}

.icon-left {
  float: left;
  width: 1.2em;
  height: 1.2em;
  margin-right: 0.5em;
  margin-top: 0.2em;
}

.icon-right {
  float: right;
  width: 1.2em;
  height: 1.2em;
  margin-left: 0.5em;
  margin-top: 0.2em;
}

/* Button groups */
.button-group-float {
  overflow: hidden;
}

.button-float {
  float: left;
  margin-right: 0.5rem;
  margin-bottom: 0.5rem;
  padding: 0.75rem 1.5rem;
  background-color: #3b82f6;
  color: white;
  border: none;
  border-radius: 0.375rem;
  cursor: pointer;
}

.button-float:last-child {
  margin-right: 0;
}

.button-float--right {
  float: right;
  margin-right: 0;
  margin-left: 0.5rem;
}

/* Badge positioning */
.badge-container {
  position: relative;
  display: inline-block;
}

.badge-float {
  float: right;
  margin-left: 0.5rem;
  padding: 0.25rem 0.5rem;
  background-color: #ef4444;
  color: white;
  border-radius: 1rem;
  font-size: 0.75rem;
  font-weight: 600;
}

/* Small UI components */
.status-indicator {
  float: right;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  margin-left: 0.5rem;
  margin-top: 0.25rem;
}

.status-online {
  background-color: #10b981;
}
.status-away {
  background-color: #f59e0b;
}
.status-offline {
  background-color: #6b7280;
}
```

### Special Layout Cases

```css
/* Newspaper columns */
.newspaper-layout {
  columns: 3;
  column-gap: 2rem;
  column-rule: 1px solid #e2e8f0;
  text-align: justify;
  line-height: 1.6;
}

.newspaper-image {
  float: top; /* CSS3 property สำหรับ column layout */
  width: 100%;
  margin-bottom: 1rem;
  break-inside: avoid;
}

.newspaper-callout {
  float: top;
  width: 100%;
  padding: 1rem;
  background-color: #f8fafc;
  border-left: 4px solid #3b82f6;
  margin: 1rem 0;
  break-inside: avoid;
}

/* Email template layout */
.email-layout {
  width: 600px;
  margin: 0 auto;
  font-family: Arial, sans-serif;
}

.email-header {
  overflow: hidden;
  background-color: #1f2937;
  color: white;
  padding: 1rem;
}

.logo-float {
  float: left;
  height: 40px;
  width: auto;
}

.nav-float {
  float: right;
  margin-top: 0.5rem;
}

.nav-float a {
  color: white;
  text-decoration: none;
  margin-left: 1rem;
  font-size: 0.9rem;
}

/* Print stylesheet */
@media print {
  .article-print {
    font-size: 12pt;
    line-height: 1.4;
  }

  .sidebar-print {
    float: right;
    width: 200pt;
    margin-left: 12pt;
    font-size: 10pt;
    background: #f5f5f5;
    padding: 6pt;
  }

  .image-print {
    float: left;
    max-width: 150pt;
    margin: 0 12pt 6pt 0;
  }
}
```

## 5. Float Issues และ Solutions

### Common Problems

```css
/* ปัญหา 1: Parent collapse */
.collapsed-parent {
  /* Parent ไม่มีความสูง */
  border: 2px solid red;
  /* children ทั้งหมดเป็น float */
}

.floated-child {
  float: left;
  width: 200px;
  height: 100px;
  background: blue;
}

/* Solution: Clearfix */
.fixed-parent {
  border: 2px solid green;
  overflow: hidden; /* หรือใช้ clearfix */
}

/* ปัญหา 2: Text wrapping ไม่ต้องการ */
.unwanted-wrapping {
  /* Block element ถูก text wrap */
  background: yellow;
  /* แต่เราต้องการให้อยู่ใต้ float */
}

/* Solution: Clear หรือ margin */
.fixed-wrapping {
  clear: both; /* หรือ */
  margin-left: 220px; /* เท่ากับ width ของ float + margin */
}

/* ปัญหา 3: Float direction ใน RTL */
.rtl-issue {
  direction: rtl;
  /* float: left จะกลายเป็น right */
}

/* Solution: Logical properties */
.rtl-fixed {
  float: inline-start; /* CSS Logical Properties */
  /* หรือใช้ CSS-in-JS สำหรับ dynamic */
}

/* ปัญหา 4: Mobile responsive */
.desktop-float {
  float: left;
  width: 300px;
  /* ใน mobile จะแคบเกินไป */
}

/* Solution: Responsive clear */
@media (max-width: 768px) {
  .desktop-float {
    float: none;
    width: 100%;
    margin-bottom: 1rem;
  }
}

/* ปัญหา 5: Z-index issues */
.float-z-index {
  float: left;
  z-index: 10; /* ไม่ทำงาน */
  /* float ไม่สร้าง stacking context */
}

/* Solution: Position relative */
.float-z-index-fixed {
  float: left;
  position: relative;
  z-index: 10; /* ทำงานแล้ว */
}
```

### Debugging Float Layouts

```css
/* เครื่องมือ debug float */
.debug-float {
  /* แสดงขอบเขต float elements */
  outline: 2px solid red;
}

.debug-container {
  /* แสดงขอบเขต container */
  outline: 2px solid blue;
  /* แสดง clearfix */
  background: rgba(0, 255, 0, 0.1);
}

/* Utility classes สำหรับ debug */
.debug-floats * {
  outline: 1px solid rgba(255, 0, 0, 0.5);
}

.debug-floats [style*='float'] {
  outline: 2px solid red;
  background: rgba(255, 0, 0, 0.1);
}

/* Visual guide */
.float-guide::before {
  content: 'FLOAT: ' attr(style);
  position: absolute;
  top: -1.5rem;
  left: 0;
  font-size: 0.75rem;
  background: red;
  color: white;
  padding: 0.25rem;
  border-radius: 0.25rem;
  z-index: 1000;
}
```

## 6. Migration จาก Float ไป Modern Layout

### From Float to Flexbox

```css
/* เดิม: Float layout */
.old-float-layout {
  overflow: hidden;
}

.old-sidebar {
  float: left;
  width: 300px;
  padding: 1rem;
}

.old-main {
  float: right;
  width: calc(100% - 320px);
  padding: 1rem;
}

/* ใหม่: Flexbox layout */
.new-flex-layout {
  display: flex;
  gap: 1rem;
}

.new-sidebar {
  flex: 0 0 300px; /* ไม่ grow/shrink, ขนาด 300px */
  padding: 1rem;
}

.new-main {
  flex: 1; /* ขยายเต็มที่เหลือ */
  padding: 1rem;
}

/* เดิม: Float grid */
.old-grid {
  overflow: hidden;
}

.old-col {
  float: left;
  width: 33.333%;
  padding: 0 15px;
  box-sizing: border-box;
}

/* ใหม่: CSS Grid */
.new-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
}

.new-col {
  /* ไม่ต้องกำหนดอะไร */
}
```

### From Float to Grid

```css
/* เดิม: Complex float layout */
.old-complex {
  width: 100%;
  overflow: hidden;
}

.old-header {
  width: 100%;
  background: #333;
  color: white;
  padding: 1rem;
}

.old-nav {
  float: left;
  width: 200px;
  background: #f5f5f5;
  min-height: 500px;
  padding: 1rem;
}

.old-content {
  float: left;
  width: calc(100% - 400px);
  padding: 1rem;
  min-height: 500px;
}

.old-aside {
  float: right;
  width: 200px;
  background: #f5f5f5;
  min-height: 500px;
  padding: 1rem;
}

.old-footer {
  clear: both;
  width: 100%;
  background: #333;
  color: white;
  padding: 1rem;
}

/* ใหม่: CSS Grid layout */
.new-complex {
  display: grid;
  grid-template-areas:
    'header header header'
    'nav content aside'
    'footer footer footer';
  grid-template-columns: 200px 1fr 200px;
  grid-template-rows: auto 1fr auto;
  min-height: 100vh;
  gap: 0;
}

.new-header {
  grid-area: header;
  background: #333;
  color: white;
  padding: 1rem;
}

.new-nav {
  grid-area: nav;
  background: #f5f5f5;
  padding: 1rem;
}

.new-content {
  grid-area: content;
  padding: 1rem;
}

.new-aside {
  grid-area: aside;
  background: #f5f5f5;
  padding: 1rem;
}

.new-footer {
  grid-area: footer;
  background: #333;
  color: white;
  padding: 1rem;
}

/* Responsive grid */
@media (max-width: 768px) {
  .new-complex {
    grid-template-areas:
      'header'
      'nav'
      'content'
      'aside'
      'footer';
    grid-template-columns: 1fr;
  }
}
```

### Progressive Enhancement

```css
/* Progressive enhancement approach */
.progressive-layout {
  /* Base: Mobile-first, no float */
  padding: 1rem;
}

.progressive-sidebar,
.progressive-main {
  width: 100%;
  margin-bottom: 1rem;
}

/* Medium screens: Float fallback */
@media (min-width: 768px) {
  .progressive-layout {
    overflow: hidden;
  }

  .progressive-sidebar {
    float: left;
    width: 300px;
    margin-bottom: 0;
    margin-right: 1rem;
  }

  .progressive-main {
    margin-left: 320px;
    margin-bottom: 0;
  }
}

/* Modern browsers: Flexbox */
@supports (display: flex) {
  @media (min-width: 768px) {
    .progressive-layout {
      display: flex;
      gap: 1rem;
      overflow: visible;
    }

    .progressive-sidebar {
      float: none;
      flex: 0 0 300px;
      margin-right: 0;
    }

    .progressive-main {
      margin-left: 0;
      flex: 1;
    }
  }
}

/* CSS Grid support */
@supports (display: grid) {
  @media (min-width: 768px) {
    .progressive-layout {
      display: grid;
      grid-template-columns: 300px 1fr;
      gap: 1rem;
    }

    .progressive-sidebar,
    .progressive-main {
      width: auto;
      margin: 0;
      float: none;
      flex: none;
    }
  }
}
```

## 7. Performance และ Best Practices

### Performance Considerations

```css
/* การ optimize float performance */
.optimized-float {
  /* ใช้ transform แทนการเปลี่ยน position */
  transform: translateX(0); /* สร้าง new stacking context */
  will-change: transform; /* hint สำหรับ browser */
}

/* หลีกเลี่ยง reflow ที่ไม่จำเป็น */
.avoid-reflow {
  /* กำหนดขนาดล่วงหน้า */
  width: 300px;
  height: 200px;
  /* แทนที่จะให้ browser คำนวณ */
}

/* ใช้ CSS containment */
.float-container {
  contain: layout style paint; /* จำกัดผลกระทบ */
}

/* Minimize layout thrashing */
.batch-changes {
  /* รวมการเปลี่ยนแปลงหลายๆ อย่าง */
  float: left;
  width: 200px;
  margin-left: 1rem;
  /* แทนที่จะทีละอย่าง */
}
```

### Modern Float Best Practices

```css
/* เมื่อใดที่ควรใช้ float */
.appropriate-float-usage {
  /* ✅ เหมาะสม: Text wrapping */
  .article-image {
    float: left;
    margin: 0 1rem 1rem 0;
  }

  /* ✅ เหมาะสม: Drop caps */
  .first-letter {
    float: left;
    font-size: 3em;
    line-height: 1;
    margin-right: 0.1em;
  }

  /* ❌ ไม่เหมาะสม: Layout หลัก */
  .avoid-layout {
    /* ใช้ Flexbox หรือ Grid แทน */
    display: flex;
    /* หรือ */
    display: grid;
  }

  /* ❌ ไม่เหมาะสม: Centering */
  .avoid-centering {
    /* ใช้ Flexbox แทน */
    display: flex;
    align-items: center;
    justify-content: center;
  }
}

/* Accessibility considerations */
.accessible-float {
  /* รองรับ screen reader */
  .floated-image {
    float: left;
    alt: 'Descriptive text'; /* ใน HTML */
  }

  /* รองรับ keyboard navigation */
  .float-content:focus {
    outline: 2px solid #3b82f6;
    outline-offset: 2px;
  }

  /* รองรับ RTL languages */
  [dir='rtl'] .floated-element {
    float: right;
  }
}

/* Responsive considerations */
.responsive-float {
  float: left;
  width: 300px;
  margin: 0 1rem 1rem 0;
}

@media (max-width: 768px) {
  .responsive-float {
    float: none;
    width: 100%;
    margin: 0 0 1rem 0;
    max-width: 100%;
  }
}
```

## สรุป: Float ในยุคปัจจุบัน

### เมื่อไหร่ควรใช้ Float

```css
/* ✅ กรณีที่ควรใช้ Float */
.should-use-float {
  /* 1. Text wrapping รอบ images */
  .wrap-image {
    float: left;
  }

  /* 2. Drop caps */
  .drop-cap::first-letter {
    float: left;
  }

  /* 3. Pull quotes ใน article */
  .pull-quote {
    float: right;
  }

  /* 4. Icon alignment ใน text */
  .text-icon {
    float: left;
  }

  /* 5. Legacy browser support */
  /* เมื่อต้องรองรับ IE < 11 */
}

/* ❌ กรณีที่ไม่ควรใช้ Float */
.should-not-use-float {
  /* 1. Layout หลัก - ใช้ Flexbox/Grid */
  /* 2. Centering - ใช้ Flexbox */
  /* 3. Equal height columns - ใช้ Flexbox/Grid */
  /* 4. Complex responsive design - ใช้ Grid */
  /* 5. Component layouts - ใช้ Flexbox */
}
```

### การเปลี่ยนผ่าน (Migration Strategy)

1. **ประเมิน current usage**: ดูว่าใช้ float อะไรบ้าง
2. **แยกประเภท**: layout vs text wrapping
3. **เปลี่ยน layout ไป Flexbox/Grid**
4. **เก็บ float สำหรับ text wrapping**
5. **Test thoroughly**: ตรวจสอบทุก breakpoint

Float ยังคงมีบทบาทในการทำ text wrapping และ editorial design แต่ไม่ควรใช้สำหรับ layout หลักแล้ว การเข้าใจประวัติและวิธีการทำงานของ float จะช่วยให้เราใช้งานได้อย่างเหมาะสมและแก้ปัญหาเก่าได้อย่างมีประสิทธิภาพ!
