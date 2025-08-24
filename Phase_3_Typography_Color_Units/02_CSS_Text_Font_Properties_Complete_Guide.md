# CSS Text และ Font Properties: คู่มือฉบับสมบูรณ์

## ภาพรวม CSS Typography Properties

CSS มี Properties หลายตัวที่ใช้ควบคุมการแสดงผลข้อความ แต่ละตัวมีหน้าที่และวิธีการใช้งานที่แตกต่างกัน เพื่อสร้างการออกแบบที่สวยงามและอ่านง่าย

### การจัดกลุ่ม Properties

```css
/* Font Properties - ควบคุมลักษณะฟอนต์ */
.font-properties {
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  font-weight: 400;
  font-style: normal;
  line-height: 1.5;
}

/* Text Properties - ควบคุมการจัดรูปแบบข้อความ */
.text-properties {
  letter-spacing: 0.5px;
  word-spacing: 2px;
  text-align: left;
  text-decoration: none;
  text-transform: none;
  white-space: normal;
}
```

## 1. font-family: การเลือกฟอนต์

### ความหมายและการทำงาน

`font-family` ใช้กำหนดตระกูลฟอนต์ที่ต้องการใช้ โดยสามารถระบุหลายฟอนต์เป็น fallback

### Syntax และ Values

```css
/* Basic syntax */
font-family: family-name | generic-family;

/* ตัวอย่างการใช้งาน */
.font-examples {
  /* ฟอนต์เฉพาะ */
  font-family: 'Helvetica Neue';

  /* ฟอนต์ทั่วไป */
  font-family: serif;

  /* Font stack */
  font-family: 'Inter', 'Segoe UI', Roboto, sans-serif;

  /* ฟอนต์ที่มีเว้นวรรค */
  font-family: 'Times New Roman', serif;
}
```

### ประเภทของ Generic Families

```css
/* 1. serif - มีหัวท้าย */
.serif-family {
  font-family: serif;
  /* Examples: Times New Roman, Georgia, Book Antiqua */
}

/* 2. sans-serif - ไม่มีหัวท้าย */
.sans-serif-family {
  font-family: sans-serif;
  /* Examples: Arial, Helvetica, Verdana */
}

/* 3. monospace - ความกว้างเท่ากัน */
.monospace-family {
  font-family: monospace;
  /* Examples: Courier New, Monaco, Consolas */
}

/* 4. cursive - ลายมือ */
.cursive-family {
  font-family: cursive;
  /* Examples: Brush Script MT, Lucida Handwriting */
}

/* 5. fantasy - ตกแต่ง */
.fantasy-family {
  font-family: fantasy;
  /* Examples: Impact, Chalkduster, Papyrus */
}

/* 6. system-ui - ฟอนต์ระบบ */
.system-family {
  font-family: system-ui;
  /* ฟอนต์เริ่มต้นของ OS */
}

/* 7. ui-serif, ui-sans-serif, ui-monospace - UI fonts */
.ui-fonts {
  font-family: ui-serif; /* UI serif font */
  font-family: ui-sans-serif; /* UI sans-serif font */
  font-family: ui-monospace; /* UI monospace font */
}

/* 8. math - สำหรับสูตรทางคณิตศาสตร์ */
.math-family {
  font-family: math;
}

/* 9. emoji - สำหรับ emoji */
.emoji-family {
  font-family: emoji;
}

/* 10. fangsong - สำหรับภาษาจีน */
.fangsong-family {
  font-family: fangsong;
}
```

### Font Stack Strategies

```css
/* Performance-first approach */
.performance-first {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
}

/* Design-first approach */
.design-first {
  font-family: 'Inter', 'SF Pro Display', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
}

/* Content-specific stacks */
.news-content {
  font-family: 'Georgia', 'Times New Roman', 'Droid Serif', serif;
}

.code-content {
  font-family: 'Fira Code', 'SF Mono', Monaco, 'Cascadia Code', 'Roboto Mono',
    'Courier New', monospace;
}

.heading-text {
  font-family: 'Playfair Display', 'Crimson Text', Georgia, serif;
}
```

## 2. font-size: การควบคุมขนาดฟอนต์

### ความหมายและการทำงาน

`font-size` ใช้กำหนดขนาดของฟอนต์ มีหน่วยและวิธีการระบุหลายแบบ

### หน่วยและ Values

```css
/* Absolute units */
.absolute-units {
  font-size: 16px; /* Pixels - แม่นยำ */
  font-size: 12pt; /* Points - สำหรับการพิมพ์ */
  font-size: 1pc; /* Picas */
  font-size: 0.5in; /* Inches */
  font-size: 1.27cm; /* Centimeters */
  font-size: 12.7mm; /* Millimeters */
}

/* Relative units */
.relative-units {
  font-size: 1em; /* เทียบกับ parent element */
  font-size: 1.2rem; /* เทียบกับ root element */
  font-size: 2ex; /* เทียบกับความสูงตัว x */
  font-size: 3ch; /* เทียบกับความกว้างตัว 0 */
  font-size: 120%; /* เปอร์เซ็นต์ */
}

/* Keyword values */
.keyword-values {
  font-size: xx-small; /* 9px */
  font-size: x-small; /* 10px */
  font-size: small; /* 13px */
  font-size: medium; /* 16px - default */
  font-size: large; /* 18px */
  font-size: x-large; /* 24px */
  font-size: xx-large; /* 32px */
  font-size: xxx-large; /* 48px */
}

/* Relative keywords */
.relative-keywords {
  font-size: larger; /* ใหญ่กว่า parent */
  font-size: smaller; /* เล็กกว่า parent */
}

/* Mathematical expressions */
.math-expressions {
  font-size: calc(1rem + 2vw);
  font-size: clamp(1rem, 2.5vw, 2rem);
  font-size: min(1.5rem, 4vw);
  font-size: max(1rem, 2vw);
}
```

### Typography Scale

```css
/* Modular Scale ตาม Design System */
:root {
  --font-size-xs: 0.75rem; /* 12px */
  --font-size-sm: 0.875rem; /* 14px */
  --font-size-base: 1rem; /* 16px */
  --font-size-lg: 1.125rem; /* 18px */
  --font-size-xl: 1.25rem; /* 20px */
  --font-size-2xl: 1.5rem; /* 24px */
  --font-size-3xl: 1.875rem; /* 30px */
  --font-size-4xl: 2.25rem; /* 36px */
  --font-size-5xl: 3rem; /* 48px */
  --font-size-6xl: 3.75rem; /* 60px */
  --font-size-7xl: 4.5rem; /* 72px */
  --font-size-8xl: 6rem; /* 96px */
  --font-size-9xl: 8rem; /* 128px */
}

/* Responsive Typography */
.responsive-heading {
  font-size: clamp(1.5rem, 5vw, 3rem);
}

.fluid-text {
  font-size: calc(1rem + 0.5vw);
}
```

### Accessibility Considerations

```css
/* รองรับการปรับขนาดฟอนต์ */
.accessible-text {
  font-size: 1rem; /* ใช้ rem เพื่อให้ scale ตาม user preference */

  /* ขนาดต่ำสุดสำหรับการอ่าน */
  min-font-size: 14px;
}

/* รองรับ user zoom */
@media (prefers-reduced-motion: no-preference) {
  .scalable-text {
    font-size: clamp(1rem, 2.5vw, 1.5rem);
  }
}
```

## 3. font-weight: การควบคุมน้ำหนักฟอนต์

### ความหมายและการทำงาน

`font-weight` ใช้กำหนดความหนาของฟอนต์ ส่งผลต่อความโดดเด่นและลำดับชั้นของข้อความ

### Values และการใช้งาน

```css
/* Keyword values */
.weight-keywords {
  font-weight: normal; /* 400 */
  font-weight: bold; /* 700 */
  font-weight: lighter; /* เบากว่า parent */
  font-weight: bolder; /* หนักกว่า parent */
}

/* Numeric values (100-900) */
.weight-numeric {
  font-weight: 100; /* Thin/Hairline */
  font-weight: 200; /* Extra Light */
  font-weight: 300; /* Light */
  font-weight: 400; /* Normal/Regular */
  font-weight: 500; /* Medium */
  font-weight: 600; /* Semi Bold */
  font-weight: 700; /* Bold */
  font-weight: 800; /* Extra Bold */
  font-weight: 900; /* Black/Heavy */
}

/* Variable fonts support */
.variable-weight {
  font-weight: 350; /* Custom value with variable fonts */
  font-weight: 450;
  font-weight: 550;
}
```

### Semantic Usage

```css
/* การใช้งานตามความหมาย */
.semantic-weights {
  /* หัวข้อหลัก */
  font-weight: 700;

  /* หัวข้อรอง */
  font-weight: 600;

  /* ข้อความปกติ */
  font-weight: 400;

  /* ข้อความรอง */
  font-weight: 300;

  /* เน้นข้อความ */
  font-weight: 500;
}

/* Design System */
:root {
  --font-weight-thin: 100;
  --font-weight-extralight: 200;
  --font-weight-light: 300;
  --font-weight-normal: 400;
  --font-weight-medium: 500;
  --font-weight-semibold: 600;
  --font-weight-bold: 700;
  --font-weight-extrabold: 800;
  --font-weight-black: 900;
}

/* Responsive weights */
.responsive-weight {
  font-weight: 400;
}

@media (min-width: 768px) {
  .responsive-weight {
    font-weight: 300; /* เบาลงในหน้าจอใหญ่ */
  }
}

@media (min-resolution: 2dppx) {
  .responsive-weight {
    font-weight: 300; /* เบาลงใน high-DPI */
  }
}
```

## 4. line-height: การควบคุมความสูงบรรทัด

### ความหมายและการทำงาน

`line-height` ใช้กำหนดความสูงของแต่ละบรรทัด ส่งผลต่อความสามารถในการอ่านและการจัดวาง

### Values และการคำนวณ

```css
/* Normal value */
.normal-line-height {
  line-height: normal; /* browser default (~1.2) */
}

/* Unitless values (แนะนำ) */
.unitless-line-height {
  line-height: 1.5; /* 1.5 เท่าของ font-size */
  line-height: 1.2; /* สำหรับหัวข้อ */
  line-height: 1.6; /* สำหรับเนื้อหา */
}

/* Length values */
.length-line-height {
  line-height: 24px; /* ค่าคงที่ */
  line-height: 1.5rem; /* เทียบกับ root */
  line-height: 1.5em; /* เทียบกับ font-size */
}

/* Percentage values */
.percentage-line-height {
  line-height: 150%; /* 150% ของ font-size */
  line-height: 120%; /* สำหรับหัวข้อ */
}
```

### การใช้งานตามเนื้อหา

```css
/* Typography hierarchy */
.typography-line-heights {
  /* Display text - บิด */
  line-height: 1.1;

  /* Headings - หัวข้อ */
  line-height: 1.2;

  /* Body text - เนื้อหา */
  line-height: 1.5;

  /* Caption text - คำบรรยาย */
  line-height: 1.4;

  /* Code text - โค้ด */
  line-height: 1.6;
}

/* Language-specific adjustments */
.thai-text {
  line-height: 1.8; /* เพิ่มความสูงสำหรับภาษาไทย */
}

.chinese-text {
  line-height: 1.7; /* สำหรับภาษาจีน */
}

.arabic-text {
  line-height: 2; /* สำหรับภาษาอาหรับ */
}
```

### Responsive Line Height

```css
/* Responsive line-height */
.responsive-line-height {
  line-height: 1.4;
}

@media (min-width: 768px) {
  .responsive-line-height {
    line-height: 1.6; /* เพิ่มใน desktop */
  }
}

/* Fluid line-height */
.fluid-line-height {
  line-height: clamp(1.2, 1.2 + 0.4 * ((100vw - 320px) / 680), 1.6);
}

/* Context-based adjustments */
.tight-layout {
  line-height: 1.2; /* สำหรับพื้นที่จำกัด */
}

.comfortable-reading {
  line-height: 1.7; /* สำหรับการอ่านที่สบาย */
}
```

## 5. font-style: การควบคุมสไตล์ฟอนต์

### ความหมายและการทำงาน

`font-style` ใช้กำหนดลักษณะการเอียงของฟอนต์

### Values และการใช้งาน

```css
/* Standard values */
.font-style-values {
  font-style: normal; /* ฟอนต์ปกติ */
  font-style: italic; /* ฟอนต์เอียงแบบ true italic */
  font-style: oblique; /* ฟอนต์เอียงแบบเทียม */
}

/* Oblique with angle */
.oblique-angles {
  font-style: oblique 14deg; /* เอียง 14 องศา */
  font-style: oblique -14deg; /* เอียงทางตรงข้าม */
  font-style: oblique 0deg; /* ไม่เอียง */
}

/* Variable fonts */
.variable-oblique {
  font-style: oblique 5deg 15deg; /* ช่วงมุมที่รองรับ */
}
```

### การใช้งานตามบริบท

```css
/* Semantic usage */
.emphasis-text {
  font-style: italic; /* เน้นข้อความ */
}

.citation-text {
  font-style: italic; /* อ้างอิง */
}

.foreign-language {
  font-style: italic; /* ภาษาต่างประเทศ */
}

.book-title {
  font-style: italic; /* ชื่อหนังสือ */
}

/* Reset styles */
.no-italic {
  font-style: normal; /* ยกเลิกการเอียง */
}

/* Conditional styles */
@supports (font-style: oblique 14deg) {
  .modern-oblique {
    font-style: oblique 12deg;
  }
}

/* Fallback for fonts without italic */
.italic-fallback {
  font-style: italic;
}

.italic-fallback:not(:is([style*='font-style: italic'])) {
  font-style: oblique 14deg; /* fallback */
}
```

## 6. letter-spacing: การควบคุมระยะห่างตัวอักษร

### ความหมายและการทำงาน

`letter-spacing` ใช้กำหนดระยะห่างระหว่างตัวอักษร ส่งผลต่อความหนาแน่นและอารมณ์ของข้อความ

### Values และการใช้งาน

```css
/* Normal value */
.normal-spacing {
  letter-spacing: normal; /* browser default */
}

/* Length values */
.length-spacing {
  letter-spacing: 0.1em; /* เทียบกับ font-size */
  letter-spacing: 1px; /* ค่าคงที่ */
  letter-spacing: 0.05rem; /* เทียบกับ root */
  letter-spacing: -0.02em; /* ลบระยะห่าง */
}

/* Percentage values */
.percentage-spacing {
  letter-spacing: 2%; /* 2% ของ font-size */
}
```

### การใช้งานตามจุดประสงค์

```css
/* Typography applications */
.display-text {
  letter-spacing: -0.02em; /* บิดระยะห่างในหัวข้อใหญ่ */
}

.heading-text {
  letter-spacing: -0.01em; /* ลดเล็กน้อยในหัวข้อ */
}

.body-text {
  letter-spacing: 0; /* ปกติในเนื้อหา */
}

.caption-text {
  letter-spacing: 0.02em; /* เพิ่มในตัวเล็ก */
}

.uppercase-text {
  letter-spacing: 0.1em; /* เพิ่มในตัวพิมพ์ใหญ่ */
  text-transform: uppercase;
}

.button-text {
  letter-spacing: 0.05em; /* ปุ่มกด */
  text-transform: uppercase;
}

.logo-text {
  letter-spacing: 0.15em; /* โลโก้ */
}

/* Responsive letter-spacing */
.responsive-spacing {
  letter-spacing: 0;
}

@media (min-width: 768px) {
  .responsive-spacing {
    letter-spacing: 0.02em;
  }
}

/* Language-specific adjustments */
.thai-spacing {
  letter-spacing: 0; /* ไม่เว้นในภาษาไทย */
}

.english-spacing {
  letter-spacing: 0.01em; /* เว้นเล็กน้อยในภาษาอังกฤษ */
}
```

### Creative Applications

```css
/* Design effects */
.spaced-heading {
  letter-spacing: 0.2em;
  text-transform: uppercase;
  font-weight: 300;
}

.tight-heading {
  letter-spacing: -0.05em;
  font-weight: 700;
}

.monospace-spacing {
  font-family: monospace;
  letter-spacing: 0.1em;
}

/* Animation effects */
.animated-spacing {
  letter-spacing: 0;
  transition: letter-spacing 0.3s ease;
}

.animated-spacing:hover {
  letter-spacing: 0.1em;
}
```

## 7. word-spacing: การควบคุมระยะห่างคำ

### ความหมายและการทำงาน

`word-spacing` ใช้กำหนดระยะห่างระหว่างคำ ส่งผลต่อความหนาแน่นและการอ่าน

### Values และการใช้งาน

```css
/* Normal value */
.normal-word-spacing {
  word-spacing: normal; /* browser default */
}

/* Length values */
.length-word-spacing {
  word-spacing: 0.2em; /* เพิ่มระยะห่าง */
  word-spacing: 2px; /* ค่าคงที่ */
  word-spacing: -0.1em; /* ลดระยะห่าง */
  word-spacing: 0.5ch; /* เทียบกับความกว้างตัว 0 */
}

/* Percentage values */
.percentage-word-spacing {
  word-spacing: 50%; /* 50% ของ space character */
}
```

### การใช้งานเฉพาะ

```css
/* Specific use cases */
.justified-text {
  text-align: justify;
  word-spacing: 0.1em; /* ปรับระยะห่างในข้อความชิดขอบ */
}

.poetry-text {
  word-spacing: 0.3em; /* เพิ่มระยะห่างในบทกวี */
  line-height: 1.8;
}

.headline-text {
  word-spacing: 0.05em; /* เพิ่มเล็กน้อยในหัวข้อ */
  letter-spacing: -0.02em;
}

.code-comments {
  font-family: monospace;
  word-spacing: 0.2em; /* เพิ่มในคอมเมนต์โค้ด */
}

/* Language-specific */
.thai-word-spacing {
  word-spacing: 0.1em; /* เพิ่มระยะห่างในภาษาไทย */
}

.german-word-spacing {
  word-spacing: -0.05em; /* ลดในภาษาเยอรมัน */
}
```

### Advanced Techniques

```css
/* Responsive word spacing */
.responsive-word-spacing {
  word-spacing: normal;
}

@media (min-width: 768px) {
  .responsive-word-spacing {
    word-spacing: 0.1em;
  }
}

/* Contextual adjustments */
.narrow-column {
  word-spacing: -0.05em; /* ลดในคอลัมน์แคบ */
}

.wide-column {
  word-spacing: 0.05em; /* เพิ่มในคอลัมน์กว้าง */
}

/* Print optimization */
@media print {
  .print-text {
    word-spacing: 0.02em; /* ปรับสำหรับการพิมพ์ */
  }
}
```

## 8. text-align: การจัดแนวข้อความ

### ความหมายและการทำงาน

`text-align` ใช้กำหนดการจัดแนวข้อความในแนวนอนภายใน element

### Values และการใช้งาน

```css
/* Basic alignment */
.text-alignment {
  text-align: left; /* ชิดซ้าย (default) */
  text-align: right; /* ชิดขวา */
  text-align: center; /* กึ่งกลาง */
  text-align: justify; /* ชิดขอบทั้งสองข้าง */
}

/* Advanced alignment */
.advanced-alignment {
  text-align: start; /* จุดเริ่มต้น (ตาม direction) */
  text-align: end; /* จุดสิ้นสุด */
  text-align: match-parent; /* ตาม parent */
}

/* Justify with last line */
.justify-options {
  text-align: justify;
  text-align-last: left; /* บรรทัดสุดท้ายชิดซ้าย */
  text-align-last: right; /* บรรทัดสุดท้ายชิดขวา */
  text-align-last: center; /* บรรทัดสุดท้ายกึ่งกลาง */
  text-align-last: justify; /* บรรทัดสุดท้ายชิดขอบ */
}
```

### การใช้งานตามบริบท

```css
/* Content types */
.heading-center {
  text-align: center; /* หัวข้อกึ่งกลาง */
}

.body-left {
  text-align: left; /* เนื้อหาชิดซ้าย */
}

.quote-center {
  text-align: center; /* คำพูดกึ่งกลาง */
  font-style: italic;
}

.address-right {
  text-align: right; /* ที่อยู่ชิดขวา */
}

.legal-text {
  text-align: justify; /* ข้อความกฎหมายชิดขอบ */
  text-align-last: left;
}

/* UI components */
.button-text {
  text-align: center; /* ข้อความปุ่ม */
}

.form-label {
  text-align: right; /* ป้ายกำกับฟอร์ม */
}

.table-number {
  text-align: right; /* ตัวเลขในตาราง */
}

.table-text {
  text-align: left; /* ข้อความในตาราง */
}
```

### Responsive Alignment

```css
/* Responsive text alignment */
.responsive-align {
  text-align: center;
}

@media (min-width: 768px) {
  .responsive-align {
    text-align: left;
  }
}

/* RTL/LTR support */
.directional-align {
  text-align: start; /* ปรับตาม direction */
}

[dir='rtl'] .directional-align {
  text-align: start; /* start = right ใน RTL */
}

[dir='ltr'] .directional-align {
  text-align: start; /* start = left ใน LTR */
}
```

### Justify Improvements

```css
/* Better justify */
.improved-justify {
  text-align: justify;
  text-justify: inter-word; /* จัดระยะห่างระหว่างคำ */
  text-align-last: left;
  hyphens: auto; /* ขีดคั่นคำ */
  word-break: break-word; /* แบ่งคำยาว */
}

/* Print-optimized justify */
@media print {
  .print-justify {
    text-align: justify;
    text-justify: inter-character; /* จัดระยะห่างระหว่างตัวอักษร */
  }
}
```

## 9. text-decoration: การตกแต่งข้อความ

### ความหมายและการทำงาน

`text-decoration` เป็น shorthand property ที่ควบคุมการตกแต่งข้อความ เช่น ขีดเส้นใต้ ขีดทับ

### Properties และ Values

```css
/* Shorthand syntax */
.text-decoration-shorthand {
  text-decoration: underline; /* พื้นฐาน */
  text-decoration: underline solid red; /* เส้น สไตล์ สี */
  text-decoration: underline wavy blue 2px; /* เส้น สไตล์ สี หนา */
}

/* Individual properties */
.text-decoration-individual {
  text-decoration-line: underline; /* ประเภทเส้น */
  text-decoration-style: solid; /* สไตล์เส้น */
  text-decoration-color: red; /* สีเส้น */
  text-decoration-thickness: 2px; /* ความหนาเส้น */
}

/* text-decoration-line values */
.decoration-lines {
  text-decoration-line: none; /* ไม่มีเส้น */
  text-decoration-line: underline; /* เส้นใต้ */
  text-decoration-line: overline; /* เส้นบน */
  text-decoration-line: line-through; /* เส้นทับ */
  text-decoration-line: underline overline; /* หลายเส้น */
}

/* text-decoration-style values */
.decoration-styles {
  text-decoration-style: solid; /* เส้นเต็ม */
  text-decoration-style: double; /* เส้นคู่ */
  text-decoration-style: dotted; /* เส้นจุด */
  text-decoration-style: dashed; /* เส้นประ */
  text-decoration-style: wavy; /* เส้นคลื่น */
}

/* text-decoration-thickness values */
.decoration-thickness {
  text-decoration-thickness: auto; /* อัตโนมัติ */
  text-decoration-thickness: from-font; /* ตามฟอนต์ */
  text-decoration-thickness: 1px; /* ค่าคงที่ */
  text-decoration-thickness: 0.1em; /* เทียบกับฟอนต์ */
  text-decoration-thickness: 10%; /* เปอร์เซ็นต์ */
}
```

### การใช้งานตามบริบท

```css
/* Link styles */
.link-styles {
  /* Default link */
  text-decoration: underline;
  text-decoration-color: blue;
  text-decoration-thickness: 1px;
}

.link-styles:hover {
  text-decoration-style: wavy;
  text-decoration-color: darkblue;
}

.link-styles:visited {
  text-decoration-color: purple;
}

/* Remove default underline */
.clean-link {
  text-decoration: none;
}

.clean-link:hover {
  text-decoration: underline;
  text-decoration-style: solid;
  text-decoration-color: currentColor;
}

/* Content styling */
.deleted-text {
  text-decoration: line-through;
  text-decoration-color: red;
}

.inserted-text {
  text-decoration: underline;
  text-decoration-color: green;
  text-decoration-style: double;
}

.highlighted-text {
  text-decoration: underline;
  text-decoration-style: wavy;
  text-decoration-color: gold;
}

.abbreviation {
  text-decoration: underline;
  text-decoration-style: dotted;
  text-decoration-color: gray;
}
```

### Advanced Techniques

```css
/* Gradient underlines */
.gradient-underline {
  text-decoration: none;
  background: linear-gradient(to right, blue, red);
  background-size: 100% 2px;
  background-position: 0 100%;
  background-repeat: no-repeat;
}

/* Animated underlines */
.animated-underline {
  text-decoration: none;
  position: relative;
}

.animated-underline::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background: blue;
  transition: width 0.3s ease;
}

.animated-underline:hover::after {
  width: 100%;
}

/* Custom underline offset */
.custom-offset {
  text-decoration: underline;
  text-underline-offset: 0.3em; /* ระยะห่างจากข้อความ */
}

/* Skip ink for descenders */
.skip-ink {
  text-decoration: underline;
  text-decoration-skip-ink: auto; /* ข้ามตัวอักษรที่ยื่นลง */
}
```

### Browser Support Fallbacks

```css
/* Fallback for older browsers */
.modern-underline {
  text-decoration: underline;
  text-decoration-color: blue;
  text-decoration-thickness: 2px;
}

/* Fallback */
@supports not (text-decoration-thickness: 2px) {
  .modern-underline {
    border-bottom: 2px solid blue;
    text-decoration: none;
  }
}
```

## 10. text-transform: การแปลงรูปแบบข้อความ

### ความหมายและการทำงาน

`text-transform` ใช้แปลงรูปแบบตัวอักษรโดยไม่เปลี่ยนแปลงเนื้อหาต้นฉบับ

### Values และการใช้งาน

```css
/* Basic transformations */
.text-transform-basic {
  text-transform: none; /* ไม่แปลง (default) */
  text-transform: uppercase; /* ตัวพิมพ์ใหญ่ทั้งหมด */
  text-transform: lowercase; /* ตัวพิมพ์เล็กทั้งหมด */
  text-transform: capitalize; /* ตัวแรกของแต่ละคำเป็นใหญ่ */
}

/* Advanced transformations */
.text-transform-advanced {
  text-transform: full-width; /* ตัวอักษรกว้างเต็ม */
  text-transform: full-size-kana; /* hiragana/katakana ขนาดเต็ม */
}
```

### การใช้งานตามบริบท

```css
/* UI Components */
.button-uppercase {
  text-transform: uppercase;
  letter-spacing: 0.1em; /* เพิ่มระยะห่างด้วย */
  font-weight: 600;
}

.nav-items {
  text-transform: uppercase;
  font-size: 0.875rem;
  letter-spacing: 0.05em;
}

.form-labels {
  text-transform: uppercase;
  font-size: 0.75rem;
  font-weight: 600;
  color: #666;
}

/* Typography */
.heading-caps {
  text-transform: uppercase;
  letter-spacing: 0.15em;
  font-weight: 300;
}

.subtitle-caps {
  text-transform: lowercase;
  font-variant: small-caps; /* ใช้ร่วมกับ small-caps */
}

.title-case {
  text-transform: capitalize;
}

/* Content types */
.code-lowercase {
  text-transform: lowercase; /* โค้ดเป็นตัวเล็ก */
  font-family: monospace;
}

.acronym-uppercase {
  text-transform: uppercase; /* ตัวย่อเป็นใหญ่ */
  font-size: 0.9em;
  letter-spacing: 0.1em;
}
```

### Language-specific Considerations

```css
/* ภาษาไทย - ไม่มีตัวพิมพ์ใหญ่เล็ก */
.thai-text {
  text-transform: none; /* ไม่ใช้กับภาษาไทย */
}

/* ภาษาตุรกี - การแปลง i/I พิเศษ */
.turkish-text {
  text-transform: uppercase;
  /* i → İ, ı → I */
}

/* ภาษาเยอรมัน - การจัดการ ß */
.german-text {
  text-transform: uppercase;
  /* ß → SS */
}

/* ภาษากรีก */
.greek-text {
  text-transform: uppercase;
  /* ς → Σ ตอนท้ายคำ */
}
```

### Responsive Applications

```css
/* Responsive text transform */
.responsive-transform {
  text-transform: none;
}

@media (min-width: 768px) {
  .responsive-transform {
    text-transform: uppercase;
    letter-spacing: 0.1em;
  }
}

/* Context-based transforms */
.mobile-menu {
  text-transform: none;
}

.desktop-menu {
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

/* Print adjustments */
@media print {
  .screen-uppercase {
    text-transform: none; /* ยกเลิกในการพิมพ์ */
  }
}
```

### Creative Applications

```css
/* Design effects */
.stylized-heading {
  text-transform: uppercase;
  letter-spacing: 0.2em;
  word-spacing: 0.3em;
  font-weight: 100;
}

.retro-text {
  text-transform: uppercase;
  letter-spacing: 0.15em;
  font-family: monospace;
}

/* Brand styling */
.brand-name {
  text-transform: lowercase;
  font-weight: 300;
  letter-spacing: 0.05em;
}

.brand-tagline {
  text-transform: uppercase;
  font-size: 0.7em;
  letter-spacing: 0.2em;
  opacity: 0.8;
}
```

## 11. white-space: การควบคุมช่องว่างและการขึ้นบรรทัดใหม่

### ความหมายและการทำงาน

`white-space` ควบคุมวิธีการจัดการกับช่องว่าง (spaces) และการขึ้นบรรทัดใหม่ (line breaks)

### Values และการทำงาน

```css
/* Basic values */
.white-space-values {
  white-space: normal; /* default - รวมช่องว่าง, wrap ข้อความ */
  white-space: nowrap; /* รวมช่องว่าง, ไม่ wrap */
  white-space: pre; /* เก็บช่องว่าง, ไม่ wrap */
  white-space: pre-wrap; /* เก็บช่องว่าง, wrap ข้อความ */
  white-space: pre-line; /* รวมช่องว่าง, เก็บ line break, wrap */
  white-space: break-spaces; /* เหมือน pre-wrap แต่แบ่งที่ช่องว่าง */
}
```

### การเปรียบเทียบ Values

```css
/* Comparison table */
/*
Property       | New lines | Spaces/Tabs | Text wrapping | End-of-line spaces
---------------|-----------|-------------|---------------|-------------------
normal         | Collapse  | Collapse    | Wrap          | Remove
nowrap         | Collapse  | Collapse    | No wrap       | Remove
pre            | Preserve  | Preserve    | No wrap       | Preserve
pre-wrap       | Preserve  | Preserve    | Wrap          | Hang
pre-line       | Preserve  | Collapse    | Wrap          | Remove
break-spaces   | Preserve  | Preserve    | Wrap          | Wrap
*/

/* Visual examples */
.normal-example {
  white-space: normal;
  /* "Hello    world\nNext line" → "Hello world Next line" */
}

.nowrap-example {
  white-space: nowrap;
  /* "Hello    world\nNext line" → "Hello world Next line" (no wrap) */
}

.pre-example {
  white-space: pre;
  /* "Hello    world\nNext line" → "Hello    world
                                      Next line" (no wrap) */
}

.pre-wrap-example {
  white-space: pre-wrap;
  /* "Hello    world\nNext line" → "Hello    world
                                      Next line" (with wrap) */
}

.pre-line-example {
  white-space: pre-line;
  /* "Hello    world\nNext line" → "Hello world
                                      Next line" */
}

.break-spaces-example {
  white-space: break-spaces;
  /* เหมือน pre-wrap แต่แบ่งบรรทัดที่ช่องว่างได้ */
}
```

### การใช้งานตามบริบท

```css
/* Code display */
.code-block {
  white-space: pre; /* เก็บการจัดรูปแบบโค้ด */
  font-family: monospace;
  background: #f5f5f5;
  padding: 1rem;
}

.code-inline {
  white-space: nowrap; /* ไม่ให้โค้ดขึ้นบรรทัดใหม่ */
  font-family: monospace;
  background: #f0f0f0;
  padding: 0.2em 0.4em;
}

/* Text content */
.poetry {
  white-space: pre-line; /* เก็บการขึ้นบรรทัดใหม่ */
  font-style: italic;
}

.address {
  white-space: pre-line; /* เก็บรูปแบบที่อยู่ */
}

.single-line {
  white-space: nowrap; /* บังคับให้อยู่บรรทัดเดียว */
  overflow: hidden;
  text-overflow: ellipsis;
}

/* UI Components */
.button-text {
  white-space: nowrap; /* ป้องกันการขึ้นบรรทัดใหม่ในปุ่ม */
}

.breadcrumb {
  white-space: nowrap; /* breadcrumb ไม่ขึ้นบรรทัดใหม่ */
}

.tag {
  white-space: nowrap; /* tag ไม่แบ่งบรรทัด */
  display: inline-block;
}
```

### Advanced Applications

```css
/* Responsive white-space */
.responsive-whitespace {
  white-space: normal;
}

@media (max-width: 768px) {
  .responsive-whitespace {
    white-space: pre-line; /* เก็บ line break ในมือถือ */
  }
}

/* Copy-paste friendly */
.copyable-text {
  white-space: pre-wrap; /* เก็บการจัดรูปแบบสำหรับ copy */
  user-select: all;
}

/* Table cells */
.table-nowrap {
  white-space: nowrap; /* ป้องกันการขึ้นบรรทัดใหม่ในตาราง */
}

.table-wrap {
  white-space: normal; /* อนุญาตให้ขึ้นบรรทัดใหม่ */
  word-break: break-word;
}

/* Form elements */
.form-input {
  white-space: pre; /* เก็บช่องว่างใน input */
}

.form-textarea {
  white-space: pre-wrap; /* เก็บรูปแบบใน textarea */
}
```

### Creative Effects

```css
/* ASCII Art */
.ascii-art {
  white-space: pre; /* เก็บการจัดรูปแบบ ASCII */
  font-family: monospace;
  line-height: 1;
}

/* Typewriter effect */
.typewriter {
  white-space: nowrap;
  overflow: hidden;
  border-right: 2px solid;
  animation: typing 3s steps(30), blink 0.5s step-end infinite alternate;
}

@keyframes typing {
  from {
    width: 0;
  }
  to {
    width: 100%;
  }
}

@keyframes blink {
  50% {
    border-color: transparent;
  }
}

/* Chat messages */
.chat-message {
  white-space: pre-wrap; /* เก็บการขึ้นบรรทัดใหม่ */
  word-wrap: break-word;
  max-width: 70%;
}

/* Code diff */
.code-added {
  white-space: pre;
  background: #e6ffed;
  color: #24292e;
}

.code-removed {
  white-space: pre;
  background: #ffeef0;
  color: #24292e;
}
```

## การรวม Properties เข้าด้วยกัน

### Typography System

```css
/* Complete typography system */
:root {
  /* Font families */
  --font-display: 'Playfair Display', Georgia, serif;
  --font-body: 'Inter', system-ui, sans-serif;
  --font-mono: 'Fira Code', monospace;

  /* Font sizes */
  --text-xs: 0.75rem;
  --text-sm: 0.875rem;
  --text-base: 1rem;
  --text-lg: 1.125rem;
  --text-xl: 1.25rem;
  --text-2xl: 1.5rem;
  --text-3xl: 1.875rem;
  --text-4xl: 2.25rem;

  /* Font weights */
  --font-light: 300;
  --font-normal: 400;
  --font-medium: 500;
  --font-semibold: 600;
  --font-bold: 700;

  /* Line heights */
  --leading-tight: 1.25;
  --leading-normal: 1.5;
  --leading-relaxed: 1.75;

  /* Letter spacing */
  --tracking-tight: -0.025em;
  --tracking-normal: 0;
  --tracking-wide: 0.025em;
  --tracking-wider: 0.1em;
}

/* Typography classes */
.display-1 {
  font-family: var(--font-display);
  font-size: var(--text-4xl);
  font-weight: var(--font-bold);
  line-height: var(--leading-tight);
  letter-spacing: var(--tracking-tight);
}

.heading-1 {
  font-family: var(--font-display);
  font-size: var(--text-3xl);
  font-weight: var(--font-semibold);
  line-height: var(--leading-tight);
  letter-spacing: var(--tracking-normal);
}

.body-text {
  font-family: var(--font-body);
  font-size: var(--text-base);
  font-weight: var(--font-normal);
  line-height: var(--leading-normal);
  letter-spacing: var(--tracking-normal);
  text-align: left;
}

.caption-text {
  font-family: var(--font-body);
  font-size: var(--text-sm);
  font-weight: var(--font-medium);
  line-height: var(--leading-normal);
  letter-spacing: var(--tracking-wide);
  text-transform: uppercase;
}

.code-text {
  font-family: var(--font-mono);
  font-size: var(--text-sm);
  font-weight: var(--font-normal);
  line-height: var(--leading-relaxed);
  white-space: pre;
  letter-spacing: var(--tracking-normal);
}
```

### Responsive Typography

```css
/* Responsive typography combinations */
.responsive-heading {
  font-family: var(--font-display);
  font-weight: var(--font-bold);
  line-height: var(--leading-tight);
  letter-spacing: var(--tracking-tight);
  text-align: center;

  /* Mobile first */
  font-size: var(--text-2xl);
}

@media (min-width: 640px) {
  .responsive-heading {
    font-size: var(--text-3xl);
    text-align: left;
  }
}

@media (min-width: 1024px) {
  .responsive-heading {
    font-size: var(--text-4xl);
    letter-spacing: var(--tracking-normal);
  }
}

/* Fluid typography */
.fluid-text {
  font-family: var(--font-body);
  font-size: clamp(var(--text-base), 2.5vw, var(--text-xl));
  line-height: clamp(
    var(--leading-normal),
    1.2 + 0.5vw,
    var(--leading-relaxed)
  );
  font-weight: var(--font-normal);
  letter-spacing: var(--tracking-normal);
}
```

## Best Practices และ Tips

### Performance

```css
/* Optimize font loading */
.optimized-text {
  font-family: 'Inter', system-ui, sans-serif;
  font-display: swap; /* ป้องกัน FOIT */
}

/* Use system fonts for better performance */
.fast-loading {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, sans-serif;
}
```

### Accessibility

```css
/* Accessibility considerations */
.accessible-text {
  font-size: 1rem; /* ใช้ rem สำหรับ scaling */
  line-height: 1.5; /* ความสูงบรรทัดที่เหมาะสม */
  color: #2d3748; /* Contrast ratio ≥ 4.5:1 */
  text-align: left; /* ชิดซ้ายอ่านง่าย */
}

/* Support for user preferences */
@media (prefers-reduced-motion: reduce) {
  .animated-text {
    animation: none;
    transition: none;
  }
}

@media (prefers-contrast: high) {
  .high-contrast-text {
    font-weight: var(--font-bold);
    text-decoration: underline;
  }
}
```

### Print Optimization

```css
/* Print-friendly typography */
@media print {
  .print-text {
    font-family: Georgia, 'Times New Roman', serif;
    font-size: 12pt;
    line-height: 1.4;
    color: black;
    text-align: justify;
    letter-spacing: normal;
    word-spacing: normal;
  }

  .print-heading {
    font-family: Arial, sans-serif;
    font-weight: bold;
    text-transform: none;
    text-decoration: none;
  }
}
```

## สรุป Best Practices

### 1. Font Management

- ใช้ font stack ที่มี fallback ที่ดี
- โหลดเฉพาะ font weights ที่จำเป็น
- ใช้ `font-display: swap` สำหรับ web fonts

### 2. Responsive Typography

- ใช้ relative units (rem, em)
- ใช้ clamp() สำหรับ fluid typography
- ปรับ line-height ตาม viewport

### 3. Readability

- line-height: 1.4-1.6 สำหรับ body text
- line-height: 1.1-1.3 สำหรับ headings
- text-align: left สำหรับ body text

### 4. Performance

- ลดจำนวน font files ที่โหลด
- ใช้ system fonts เมื่อเป็นไปได้
- Preload critical fonts

### 5. Accessibility

- รองรับ user preferences
- ใช้ contrast ratio ที่เหมาะสม
- รองรับการ scale ฟอนต์

การเรียนรู้และใช้งาน CSS Typography Properties อย่างถูกต้องจะช่วยสร้างประสบการณ์การอ่านที่ดีและการออกแบบที่สวยงาม!
