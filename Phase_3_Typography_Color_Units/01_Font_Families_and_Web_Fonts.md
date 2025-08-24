# CSS Font Families และ Web Fonts: การจัดการฟอนต์แบบมืออาชีพ

## ภาพรวม Typography ใน CSS

Typography เป็นหัวใจสำคัญของการออกแบบเว็บ ฟอนต์ที่เลือกใช้จะส่งผลต่อความสามารถในการอ่าน การรับรู้แบรนด์ และประสบการณ์ผู้ใช้โดยรวม

### หลักการพื้นฐานของ Typography

```css
/* Elements หลักของ Typography */
.typography-basics {
  font-family: 'Helvetica Neue', Arial, sans-serif; /* ตระกูลฟอนต์ */
  font-size: 16px; /* ขนาดฟอนต์ */
  font-weight: 400; /* น้ำหนักฟอนต์ */
  font-style: normal; /* สไตล์ฟอนต์ */
  line-height: 1.6; /* ความสูงบรรทัด */
  letter-spacing: 0.5px; /* ระยะห่างตัวอักษร */
  word-spacing: 2px; /* ระยะห่างคำ */
}
```

## Font Families: ตระกูลฟอนต์

### ประเภทของ Font Families

CSS แบ่งฟอนต์เป็น 5 ประเภทหลัก:

```css
/* 1. Serif - มีหัวและท้ายตัวอักษร */
.serif-font {
  font-family: serif;
  /* ตัวอย่าง: Times New Roman, Georgia, Book Antiqua */
}

/* 2. Sans-serif - ไม่มีหัวและท้ายตัวอักษร */
.sans-serif-font {
  font-family: sans-serif;
  /* ตัวอย่าง: Arial, Helvetica, Verdana */
}

/* 3. Monospace - ตัวอักษรมีความกว้างเท่ากัน */
.monospace-font {
  font-family: monospace;
  /* ตัวอย่าง: Courier New, Monaco, Consolas */
}

/* 4. Cursive - ตัวอักษรลายมือ */
.cursive-font {
  font-family: cursive;
  /* ตัวอย่าง: Comic Sans MS, Brush Script MT */
}

/* 5. Fantasy - ตัวอักษรตกแต่ง */
.fantasy-font {
  font-family: fantasy;
  /* ตัวอย่าง: Impact, Chalkduster, Papyrus */
}
```

### การเลือกใช้ Font Family ตามจุดประสงค์

```css
/* สำหรับเนื้อหาหลัก - อ่านง่าย */
body {
  font-family: 'Inter', 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
}

/* สำหรับหัวข้อ - โดดเด่น */
h1,
h2,
h3,
h4,
h5,
h6 {
  font-family: 'Playfair Display', Georgia, 'Times New Roman', serif;
}

/* สำหรับโค้ด - ชัดเจน */
code,
pre {
  font-family: 'Fira Code', 'Monaco', 'Cascadia Code', 'Courier New', monospace;
}

/* สำหรับข้อมูลตัวเลข - เรียงแนว */
.numbers {
  font-family: 'Roboto Mono', 'SF Mono', Monaco, monospace;
  font-variant-numeric: tabular-nums;
}
```

## Font Stack: ระบบสำรองฟอนต์

### ความหมายและความสำคัญ

Font Stack คือการเรียงลำดับฟอนต์ที่ต้องการใช้ โดยเบราว์เซอร์จะเลือกใช้ฟอนต์แรกที่มีอยู่ในระบบ

### หลักการสร้าง Font Stack ที่ดี

```css
/* หลักการเรียงลำดับ Font Stack */
.optimal-font-stack {
  font-family:
    /* 1. Web Font ที่ต้องการ */ 'Inter',
    /* 2. System Font ที่คล้ายกัน */ -apple-system, BlinkMacSystemFont, 'Segoe UI',
    /* 3. Fallback fonts ทั่วไป */ Roboto, 'Helvetica Neue', Arial,
    /* 4. Generic family เป็นตัวสุดท้าย */ sans-serif;
}
```

### System Font Stacks ยอดนิยม

```css
/* macOS และ iOS System Font */
.apple-system-font {
  font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display',
    'SF Pro Text', 'Helvetica Neue', Helvetica, Arial, sans-serif;
}

/* Windows System Font */
.windows-system-font {
  font-family: 'Segoe UI', 'Segoe UI Historic', 'Segoe UI Emoji',
    'Segoe UI Symbol', sans-serif;
}

/* Android System Font */
.android-system-font {
  font-family: Roboto, 'Droid Sans', 'Helvetica Neue', Arial, sans-serif;
}

/* Cross-platform System Font Stack */
.universal-system-font {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
    'Helvetica Neue', Arial, 'Noto Sans', sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji',
    'Segoe UI Symbol', 'Noto Color Emoji';
}
```

### Font Stacks สำหรับการใช้งานเฉพาะ

```css
/* สำหรับเว็บไซต์ข่าว */
.news-website {
  font-family: 'Charter', 'Droid Serif', 'DejaVu Serif', Georgia,
    'Times New Roman', serif;
}

/* สำหรับเว็บไซต์เทคโนโลยี */
.tech-website {
  font-family: 'Inter', 'SF Pro Display', 'Segoe UI', Roboto, 'Helvetica Neue',
    Arial, sans-serif;
}

/* สำหรับเว็บไซต์ศิลปะและออกแบบ */
.creative-website {
  font-family: 'Playfair Display', 'Crimson Text', 'Times New Roman', Georgia,
    serif;
}

/* สำหรับเอกสารทางการ */
.formal-document {
  font-family: 'Source Serif Pro', 'Minion Pro', 'Times New Roman', Georgia,
    serif;
}

/* สำหรับแอปพลิเคชัน */
.application-ui {
  font-family: 'SF Pro Text', 'Segoe UI', 'Roboto', 'Oxygen', 'Ubuntu',
    'Cantarell', 'Open Sans', 'Helvetica Neue', sans-serif;
}
```

## การแนะนำ @font-face

### ความหมายและการทำงาน

`@font-face` เป็น CSS rule ที่ใช้กำหนดฟอนต์แบบกำหนดเองที่ไม่ได้มีมาตรฐานในระบบ โดยสามารถโหลดจากเซิร์ฟเวอร์

### Syntax พื้นฐาน

```css
/* Syntax พื้นฐานของ @font-face */
@font-face {
  font-family: 'ชื่อฟอนต์ที่ต้องการ';
  src: url('path/to/font.woff2') format('woff2'), url('path/to/font.woff')
      format('woff'), url('path/to/font.ttf') format('truetype');
  font-weight: normal;
  font-style: normal;
  font-display: swap;
}
```

### ตัวอย่างการใช้งานจริง

```css
/* โหลดฟอนต์จาก Google Fonts แบบ self-hosted */
@font-face {
  font-family: 'Inter';
  src: url('../fonts/Inter-Regular.woff2') format('woff2'), url('../fonts/Inter-Regular.woff')
      format('woff');
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}

@font-face {
  font-family: 'Inter';
  src: url('../fonts/Inter-Bold.woff2') format('woff2'), url('../fonts/Inter-Bold.woff')
      format('woff');
  font-weight: 700;
  font-style: normal;
  font-display: swap;
}

@font-face {
  font-family: 'Inter';
  src: url('../fonts/Inter-Italic.woff2') format('woff2'), url('../fonts/Inter-Italic.woff')
      format('woff');
  font-weight: 400;
  font-style: italic;
  font-display: swap;
}

/* การใช้งานฟอนต์ที่กำหนด */
body {
  font-family: 'Inter', system-ui, sans-serif;
}
```

### Font Formats และการรองรับ

```css
/* รูปแบบไฟล์ฟอนต์และการรองรับ */
@font-face {
  font-family: 'MyFont';
  src:
    /* WOFF2 - รองรับ browsers ใหม่, ขนาดเล็กที่สุด */ url('font.woff2') format('woff2'),
    /* WOFF - รองรับ browsers เก่ากว่า */ url('font.woff') format('woff'),
    /* TTF/OTF - fallback สำหรับ browsers เก่ามาก */ url('font.ttf') format('truetype'),
    url('font.otf') format('opentype'),
    /* EOT - สำหรับ Internet Explorer */ url('font.eot?#iefix') format('embedded-opentype');
}
```

### Font-display Property

```css
/* font-display values และผลกระทบ */
@font-face {
  font-family: 'MyFont';
  src: url('font.woff2') format('woff2');

  /* auto - browser default behavior */
  font-display: auto;

  /* block - ซ่อนข้อความจนกว่าฟอนต์จะโหลดเสร็จ */
  font-display: block;

  /* swap - แสดง fallback font ทันที แล้วเปลี่ยนเมื่อโหลดเสร็จ */
  font-display: swap;

  /* fallback - แสดง fallback ช่วงสั้นๆ แล้วเปลี่ยน */
  font-display: fallback;

  /* optional - ใช้ custom font เฉพาะเมื่อโหลดเร็ว */
  font-display: optional;
}

/* แนะนำให้ใช้ swap สำหรับ web fonts ทั่วไป */
@font-face {
  font-family: 'WebFont';
  src: url('webfont.woff2') format('woff2');
  font-display: swap; /* ป้องกัน FOIT (Flash of Invisible Text) */
}
```

## การใช้งาน Web Fonts ขั้นสูง

### Variable Fonts

```css
/* Variable fonts - ฟอนต์ที่ปรับค่าได้ */
@font-face {
  font-family: 'InterVariable';
  src: url('Inter-Variable.woff2') format('woff2-variations'), url('Inter-Variable.woff2')
      format('woff2');
  font-weight: 100 900; /* รองรับน้ำหนัก 100-900 */
  font-style: normal;
  font-display: swap;
}

/* การใช้งาน Variable fonts */
.variable-font-example {
  font-family: 'InterVariable', sans-serif;
  font-weight: 350; /* ค่าที่ไม่ได้กำหนดไว้แต่ฟอนต์รองรับ */

  /* Custom axes (ถ้าฟอนต์รองรับ) */
  font-variation-settings: 'wght' 350, /* Weight */ 'slnt' -10; /* Slant */
}

/* Responsive typography ด้วย Variable fonts */
@media (min-width: 768px) {
  .responsive-heading {
    font-variation-settings: 'wght' 700;
  }
}

@media (min-width: 1200px) {
  .responsive-heading {
    font-variation-settings: 'wght' 900;
  }
}
```

### Font Loading Strategies

```css
/* 1. Critical fonts - โหลดแบบ inline */
/* วางไว้ใน <head> เพื่อโหลดเร็ว */

/* 2. Non-critical fonts - โหลดแบบ async */
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&display=swap');

/* 3. Progressive Enhancement */
.text-content {
  /* เริ่มด้วย system fonts */
  font-family: system-ui, sans-serif;
}

/* เมื่อ custom font โหลดเสร็จ */
.fonts-loaded .text-content {
  font-family: 'CustomFont', system-ui, sans-serif;
}
```

## ตัวอย่างการใช้งานจริง

### HTML Structure

```html
<!DOCTYPE html>
<html lang="th">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Font Families & Web Fonts Demo</title>

    <!-- Preload critical fonts -->
    <link
      rel="preload"
      href="fonts/Inter-Regular.woff2"
      as="font"
      type="font/woff2"
      crossorigin
    />
    <link
      rel="preload"
      href="fonts/Inter-Bold.woff2"
      as="font"
      type="font/woff2"
      crossorigin
    />

    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Playfair+Display:wght@400;600;700&display=swap"
      rel="stylesheet"
    />

    <link rel="stylesheet" href="typography-demo.css" />
  </head>
  <body>
    <div class="container">
      <!-- Font Stack Examples -->
      <section class="font-examples">
        <h1 class="main-heading">Typography & Font Families</h1>

        <div class="font-showcase">
          <div class="font-demo serif-demo">
            <h3>Serif Fonts</h3>
            <p class="serif-text">
              ฟอนต์ Serif มีหัวและท้ายตัวอักษร เหมาะสำหรับการอ่านเนื้อหาที่ยาว
              ให้ความรู้สึกคลาสสิกและเป็นทางการ
            </p>
            <code class="font-info"
              >font-family: 'Playfair Display', Georgia, serif;</code
            >
          </div>

          <div class="font-demo sans-serif-demo">
            <h3>Sans-serif Fonts</h3>
            <p class="sans-serif-text">
              ฟอนต์ Sans-serif ไม่มีหัวและท้าย เหมาะสำหรับหน้าจอดิจิทัล
              ให้ความรู้สึกทันสมัยและอ่านง่าย
            </p>
            <code class="font-info"
              >font-family: 'Inter', system-ui, sans-serif;</code
            >
          </div>

          <div class="font-demo monospace-demo">
            <h3>Monospace Fonts</h3>
            <p class="monospace-text">
              ฟอนต์ Monospace มีความกว้างเท่ากันทุกตัว
              เหมาะสำหรับการแสดงโค้ดและตัวเลข
            </p>
            <code class="font-info"
              >font-family: 'Fira Code', 'Courier New', monospace;</code
            >
          </div>
        </div>
      </section>

      <!-- System Font Examples -->
      <section class="system-fonts">
        <h2>System Font Stacks</h2>

        <div class="system-demo">
          <div class="apple-system">
            <h4>Apple System</h4>
            <p>ฟอนต์ระบบของ macOS และ iOS</p>
          </div>

          <div class="windows-system">
            <h4>Windows System</h4>
            <p>ฟอนต์ระบบของ Windows</p>
          </div>

          <div class="universal-system">
            <h4>Universal System</h4>
            <p>ฟอนต์ระบบที่รองรับทุกแพลตฟอร์ม</p>
          </div>
        </div>
      </section>

      <!-- Web Font Loading Demo -->
      <section class="webfont-demo">
        <h2>Web Fonts Loading</h2>

        <div class="loading-states">
          <div class="font-loading">
            <h4>Font Loading States</h4>
            <p class="fallback-font">ข้อความนี้แสดงด้วย fallback font ก่อน</p>
            <p class="webfont-loaded">
              ข้อความนี้จะเปลี่ยนเมื่อ web font โหลดเสร็จ
            </p>
          </div>
        </div>
      </section>

      <!-- Typography Scale -->
      <section class="typography-scale">
        <h2>Typography Scale</h2>
        <h1 class="scale-h1">Heading 1 - 2.5rem</h1>
        <h2 class="scale-h2">Heading 2 - 2rem</h2>
        <h3 class="scale-h3">Heading 3 - 1.75rem</h3>
        <h4 class="scale-h4">Heading 4 - 1.5rem</h4>
        <h5 class="scale-h5">Heading 5 - 1.25rem</h5>
        <h6 class="scale-h6">Heading 6 - 1rem</h6>
        <p class="body-text">Body text - 1rem</p>
        <small class="small-text">Small text - 0.875rem</small>
      </section>

      <!-- Font Performance -->
      <section class="performance-demo">
        <h2>Font Performance Tips</h2>
        <div class="performance-tips">
          <div class="tip">
            <h4>1. Font Preloading</h4>
            <code
              >&lt;link rel="preload" href="font.woff2" as="font"
              type="font/woff2" crossorigin&gt;</code
            >
          </div>

          <div class="tip">
            <h4>2. Font Display Swap</h4>
            <code>font-display: swap;</code>
          </div>

          <div class="tip">
            <h4>3. WOFF2 Format</h4>
            <code>src: url('font.woff2') format('woff2');</code>
          </div>
        </div>
      </section>
    </div>

    <script src="font-loading.js"></script>
  </body>
</html>
```

### CSS Implementation

```css
/* typography-demo.css */

/* Custom Font Definitions */
@font-face {
  font-family: 'InterCustom';
  src: url('fonts/Inter-Regular.woff2') format('woff2'), url('fonts/Inter-Regular.woff')
      format('woff');
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}

@font-face {
  font-family: 'InterCustom';
  src: url('fonts/Inter-Bold.woff2') format('woff2'), url('fonts/Inter-Bold.woff')
      format('woff');
  font-weight: 700;
  font-style: normal;
  font-display: swap;
}

/* CSS Custom Properties for Typography */
:root {
  /* Font Families */
  --font-serif: 'Playfair Display', Georgia, 'Times New Roman', serif;
  --font-sans: 'Inter', system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI',
    sans-serif;
  --font-mono: 'Fira Code', 'SF Mono', Monaco, 'Cascadia Code', 'Courier New',
    monospace;

  /* Font Sizes */
  --text-xs: 0.75rem; /* 12px */
  --text-sm: 0.875rem; /* 14px */
  --text-base: 1rem; /* 16px */
  --text-lg: 1.125rem; /* 18px */
  --text-xl: 1.25rem; /* 20px */
  --text-2xl: 1.5rem; /* 24px */
  --text-3xl: 1.875rem; /* 30px */
  --text-4xl: 2.25rem; /* 36px */
  --text-5xl: 3rem; /* 48px */

  /* Font Weights */
  --font-light: 300;
  --font-normal: 400;
  --font-medium: 500;
  --font-semibold: 600;
  --font-bold: 700;

  /* Line Heights */
  --leading-tight: 1.25;
  --leading-normal: 1.5;
  --leading-relaxed: 1.75;
}

/* Base Styles */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: var(--font-sans);
  font-size: var(--text-base);
  line-height: var(--leading-normal);
  color: #1a202c;
  background: #f7fafc;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
}

/* Main Heading */
.main-heading {
  font-family: var(--font-serif);
  font-size: var(--text-5xl);
  font-weight: var(--font-bold);
  text-align: center;
  margin-bottom: 3rem;
  color: #2d3748;
}

/* Font Showcase */
.font-showcase {
  display: grid;
  gap: 2rem;
  margin-bottom: 4rem;
}

.font-demo {
  background: white;
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
  border-left: 4px solid;
}

.font-demo h3 {
  margin-bottom: 1rem;
  color: #2d3748;
}

.font-demo p {
  margin-bottom: 1rem;
  font-size: var(--text-lg);
  line-height: var(--leading-relaxed);
}

.font-info {
  display: block;
  background: #f1f5f9;
  padding: 0.75rem;
  border-radius: 6px;
  font-family: var(--font-mono);
  font-size: var(--text-sm);
  color: #475569;
}

/* Serif Demo */
.serif-demo {
  border-left-color: #dc2626;
}

.serif-text {
  font-family: var(--font-serif);
  font-weight: var(--font-normal);
}

/* Sans-serif Demo */
.sans-serif-demo {
  border-left-color: #2563eb;
}

.sans-serif-text {
  font-family: var(--font-sans);
  font-weight: var(--font-normal);
}

/* Monospace Demo */
.monospace-demo {
  border-left-color: #059669;
}

.monospace-text {
  font-family: var(--font-mono);
  font-weight: var(--font-normal);
}

/* System Fonts Section */
.system-fonts {
  margin-bottom: 4rem;
}

.system-fonts h2 {
  font-family: var(--font-serif);
  font-size: var(--text-3xl);
  margin-bottom: 2rem;
  color: #2d3748;
}

.system-demo {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
}

.system-demo > div {
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
}

.apple-system {
  font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', sans-serif;
}

.windows-system {
  font-family: 'Segoe UI', 'Segoe UI Historic', sans-serif;
}

.universal-system {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
    sans-serif;
}

/* Web Font Loading Demo */
.webfont-demo {
  margin-bottom: 4rem;
}

.webfont-demo h2 {
  font-family: var(--font-serif);
  font-size: var(--text-3xl);
  margin-bottom: 2rem;
  color: #2d3748;
}

.font-loading {
  background: white;
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
}

.fallback-font {
  font-family: Arial, sans-serif;
  font-size: var(--text-lg);
  margin-bottom: 1rem;
  color: #64748b;
}

.webfont-loaded {
  font-family: 'InterCustom', Arial, sans-serif;
  font-size: var(--text-lg);
  font-weight: var(--font-medium);
  color: #1e293b;
}

/* Typography Scale */
.typography-scale {
  margin-bottom: 4rem;
}

.typography-scale h2 {
  font-family: var(--font-serif);
  font-size: var(--text-3xl);
  margin-bottom: 2rem;
  color: #2d3748;
}

.scale-h1 {
  font-family: var(--font-serif);
  font-size: var(--text-5xl);
  font-weight: var(--font-bold);
  margin-bottom: 1rem;
  color: #1a202c;
}

.scale-h2 {
  font-family: var(--font-serif);
  font-size: var(--text-4xl);
  font-weight: var(--font-semibold);
  margin-bottom: 0.875rem;
  color: #2d3748;
}

.scale-h3 {
  font-family: var(--font-sans);
  font-size: var(--text-3xl);
  font-weight: var(--font-semibold);
  margin-bottom: 0.75rem;
  color: #374151;
}

.scale-h4 {
  font-family: var(--font-sans);
  font-size: var(--text-2xl);
  font-weight: var(--font-medium);
  margin-bottom: 0.625rem;
  color: #4b5563;
}

.scale-h5 {
  font-family: var(--font-sans);
  font-size: var(--text-xl);
  font-weight: var(--font-medium);
  margin-bottom: 0.5rem;
  color: #6b7280;
}

.scale-h6 {
  font-family: var(--font-sans);
  font-size: var(--text-base);
  font-weight: var(--font-semibold);
  margin-bottom: 0.5rem;
  color: #6b7280;
}

.body-text {
  font-family: var(--font-sans);
  font-size: var(--text-base);
  font-weight: var(--font-normal);
  margin-bottom: 0.5rem;
  color: #374151;
}

.small-text {
  font-family: var(--font-sans);
  font-size: var(--text-sm);
  font-weight: var(--font-normal);
  color: #6b7280;
}

/* Performance Tips */
.performance-demo h2 {
  font-family: var(--font-serif);
  font-size: var(--text-3xl);
  margin-bottom: 2rem;
  color: #2d3748;
}

.performance-tips {
  display: grid;
  gap: 1.5rem;
}

.tip {
  background: white;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
  border-left: 4px solid #3b82f6;
}

.tip h4 {
  font-family: var(--font-sans);
  font-size: var(--text-lg);
  font-weight: var(--font-semibold);
  margin-bottom: 0.75rem;
  color: #1e293b;
}

.tip code {
  display: block;
  background: #f1f5f9;
  padding: 0.75rem;
  border-radius: 6px;
  font-family: var(--font-mono);
  font-size: var(--text-sm);
  color: #475569;
  overflow-x: auto;
}

/* Responsive Design */
@media (max-width: 768px) {
  .container {
    padding: 1rem;
  }

  .main-heading {
    font-size: var(--text-4xl);
  }

  .font-demo p {
    font-size: var(--text-base);
  }

  .scale-h1 {
    font-size: var(--text-4xl);
  }

  .scale-h2 {
    font-size: var(--text-3xl);
  }
}

/* Font Loading Animation */
.font-loading-animation {
  opacity: 0;
  animation: fadeIn 0.3s ease-in-out forwards;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

/* Print Styles */
@media print {
  body {
    font-family: Georgia, 'Times New Roman', serif;
    font-size: 12pt;
    line-height: 1.4;
    color: black;
  }

  .main-heading {
    font-size: 24pt;
  }

  .font-demo {
    break-inside: avoid;
    margin-bottom: 1rem;
  }
}
```

### JavaScript for Font Loading

```javascript
// font-loading.js

// Font Loading API Demo
if ('fonts' in document) {
  // ตรวจสอบการโหลดฟอนต์
  const fontLoadPromises = [
    document.fonts.load('400 1rem Inter'),
    document.fonts.load('700 1rem Inter'),
    document.fonts.load('400 1rem "Playfair Display"'),
  ];

  Promise.all(fontLoadPromises)
    .then(() => {
      console.log('All fonts loaded successfully');
      document.body.classList.add('fonts-loaded');

      // เพิ่ม animation เมื่อฟอนต์โหลดเสร็จ
      const elements = document.querySelectorAll('.webfont-loaded');
      elements.forEach((el) => {
        el.classList.add('font-loading-animation');
      });
    })
    .catch((error) => {
      console.error('Font loading failed:', error);
    });

  // Event listener สำหรับการโหลดฟอนต์
  document.fonts.addEventListener('loadingdone', (event) => {
    console.log(`${event.fontfaces.length} fonts loaded`);
  });

  // แสดงสถานะการโหลดฟอนต์
  document.fonts.ready.then(() => {
    console.log('Font loading complete');
    updateFontStatus();
  });
}

// ฟังก์ชันอัพเดทสถานะฟอนต์
function updateFontStatus() {
  const statusElements = document.querySelectorAll('.font-status');
  const loadedFonts = Array.from(document.fonts.values())
    .filter((font) => font.status === 'loaded')
    .map((font) => font.family);

  statusElements.forEach((el) => {
    el.textContent = `Loaded fonts: ${loadedFonts.join(', ')}`;
  });
}

// Performance monitoring
if ('PerformanceObserver' in window) {
  const observer = new PerformanceObserver((list) => {
    const entries = list.getEntries();
    entries.forEach((entry) => {
      if (entry.name.includes('font')) {
        console.log(`Font ${entry.name} loaded in ${entry.duration}ms`);
      }
    });
  });

  observer.observe({ entryTypes: ['resource'] });
}

// Fallback font detection
function detectFontSupport(fontName) {
  const canvas = document.createElement('canvas');
  const context = canvas.getContext('2d');

  // ทดสอบด้วยฟอนต์ fallback
  context.font = '16px monospace';
  const fallbackWidth = context.measureText('mmmmmmmmmmlli').width;

  // ทดสอบด้วยฟอนต์ที่ต้องการ
  context.font = `16px ${fontName}, monospace`;
  const testWidth = context.measureText('mmmmmmmmmmlli').width;

  return fallbackWidth !== testWidth;
}

// ตัวอย่างการใช้งาน
const isInterSupported = detectFontSupport('Inter');
console.log('Inter font supported:', isInterSupported);

// Font loading strategy
class FontLoader {
  constructor() {
    this.loadedFonts = new Set();
    this.loadingFonts = new Set();
  }

  async loadFont(fontFamily, weight = '400', style = 'normal') {
    const fontKey = `${fontFamily}-${weight}-${style}`;

    if (this.loadedFonts.has(fontKey)) {
      return true;
    }

    if (this.loadingFonts.has(fontKey)) {
      return false; // Already loading
    }

    this.loadingFonts.add(fontKey);

    try {
      await document.fonts.load(`${weight} 1rem "${fontFamily}"`);
      this.loadedFonts.add(fontKey);
      this.loadingFonts.delete(fontKey);
      return true;
    } catch (error) {
      console.error(`Failed to load font ${fontKey}:`, error);
      this.loadingFonts.delete(fontKey);
      return false;
    }
  }

  isLoaded(fontFamily, weight = '400', style = 'normal') {
    const fontKey = `${fontFamily}-${weight}-${style}`;
    return this.loadedFonts.has(fontKey);
  }

  getLoadedFonts() {
    return Array.from(this.loadedFonts);
  }
}

// การใช้งาน FontLoader
const fontLoader = new FontLoader();

// โหลดฟอนต์หลัก
fontLoader.loadFont('Inter', '400').then((loaded) => {
  if (loaded) {
    console.log('Inter 400 loaded successfully');
  }
});

fontLoader.loadFont('Playfair Display', '600').then((loaded) => {
  if (loaded) {
    console.log('Playfair Display 600 loaded successfully');
  }
});
```

## Best Practices สำหรับ Font Management

### 1. Performance Optimization

```css
/* ลำดับความสำคัญในการโหลดฟอนต์ */

/* 1. Critical fonts - inline ใน CSS */
@font-face {
  font-family: 'CriticalFont';
  src: url('data:font/woff2;base64,...') format('woff2');
  font-display: block; /* รอฟอนต์โหลด */
}

/* 2. Important fonts - preload */
/* <link rel="preload" href="font.woff2" as="font" type="font/woff2" crossorigin> */

/* 3. Non-critical fonts - lazy load */
@font-face {
  font-family: 'NonCriticalFont';
  src: url('font.woff2') format('woff2');
  font-display: swap; /* แสดง fallback ก่อน */
}
```

### 2. Accessibility Considerations

```css
/* รองรับผู้ใช้ที่มีปัญหาการมองเห็น */
@media (prefers-reduced-motion: reduce) {
  .font-loading-animation {
    animation: none;
  }
}

/* รองรับ high contrast mode */
@media (prefers-contrast: high) {
  body {
    font-family: system-ui, sans-serif; /* ใช้ system font */
  }
}

/* รองรับการปรับขนาดฟอนต์ */
@media (min-resolution: 2dppx) {
  body {
    font-weight: 300; /* ลดน้ำหนักในหน้าจอ high-DPI */
  }
}
```

### 3. Cross-browser Compatibility

```css
/* รองรับ browsers เก่า */
.font-stack {
  /* Modern browsers */
  font-family: 'CustomFont', system-ui, sans-serif;

  /* Fallback for older browsers */
  font-family: 'CustomFont', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
    Helvetica, Arial, sans-serif;
}

/* รองรับ Internet Explorer */
@font-face {
  font-family: 'CustomFont';
  src: url('font.eot'); /* IE9 Compat Modes */
  src: url('font.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
      url('font.woff2') format('woff2'),
    /* Modern Browsers */ url('font.woff') format('woff'), /* Pretty Modern Browsers */
      url('font.ttf') format('truetype'); /* Safari, Android, iOS */
}
```

## สรุป Key Points

### Font Families:

- **Serif**: เหมาะสำหรับการอ่านเนื้อหายาว, ให้ความรู้สึกคลาสสิก
- **Sans-serif**: เหมาะสำหรับหน้าจอดิจิทัล, ทันสมัย อ่านง่าย
- **Monospace**: เหมาะสำหรับโค้ดและตัวเลข
- **System fonts**: โหลดเร็ว, คุ้นเคยกับผู้ใช้

### Font Stack Best Practices:

- เรียงจากเฉพาะเจาะจงไปทั่วไป
- ใส่ Generic family เป็นตัวสุดท้าย
- ใช้ System fonts เป็น fallback
- ทดสอบในหลาย platforms

### @font-face Guidelines:

- ใช้ `font-display: swap` สำหรับ web fonts
- โหลด WOFF2 format ก่อน
- Preload critical fonts
- จัดกลุ่มตาม font-weight และ font-style

### Performance Tips:

- ลดจำนวนฟอนต์ที่โหลด
- ใช้ font subsetting
- Optimize file sizes
- Monitor loading performance

การเลือกและจัดการฟอนต์ที่ดีจะส่งผลต่อทั้งประสบการณ์ผู้ใช้และประสิทธิภาพของเว็บไซต์!
