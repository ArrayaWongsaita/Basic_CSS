# CSS Units: คู่มือฉบับสมบูรณ์

## ภาพรวม CSS Units

CSS Units คือหน่วยวัดที่ใช้กำหนดขนาด ระยะห่าง และตำแหน่งของ elements ในหน้าเว็บ การเลือกใช้หน่วยที่เหมาะสมจะส่งผลต่อความสวยงาม การใช้งาน และการตอบสนองของเว็บไซต์

### การจัดกลุ่ม CSS Units

```css
/* Absolute Units - หน่วยวัดสัมบูรณ์ */
.absolute-units {
  width: 300px; /* Pixels */
  border-width: 1pt; /* Points */
}

/* Relative Units - หน่วยวัดสัมพัทธ์ */
.relative-units {
  font-size: 1.5rem; /* Root em - แนะนำสำหรับ font-size ⭐ */
  padding: 2em; /* Em (relative to font-size) */
  width: 50%; /* Percentage */
  height: 100vh; /* Viewport height */
  margin: 10vw; /* Viewport width */
  max-width: 65ch; /* Character width */
  line-height: 2ex; /* X-height */
}

/* Modern Units - หน่วยวัดสมัยใหม่ */
.modern-units {
  width: min(90vw, 800px); /* Minimum function */
  height: max(50vh, 400px); /* Maximum function */
  font-size: clamp(1rem, 4vw, 2rem); /* Clamp function */
}
```

## 1. px (Pixels): หน่วยพิกเซล

### ความหมายและการทำงาน

`px` คือหน่วยวัดสัมบูรณ์ที่อ้างอิงจากพิกเซลบนหน้าจอ เป็นหน่วยที่คงที่และไม่เปลี่ยนแปลงตามบริบทอื่น

### การใช้งานและตัวอย่าง

```css
/* เหมาะสำหรับรายละเอียดที่ต้องการความแม่นยำ */
.pixel-usage {
  /* Borders และ shadows */
  border: 1px solid #ddd;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);

  /* Icon sizes */
  width: 24px;
  height: 24px;

  /* Small spacing */
  margin-bottom: 2px;

  /* Media queries */
  /* @media (max-width: 768px) */
}

/* Card component */
.card-pixel {
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  padding: 16px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}
```

### ข้อดีและข้อเสีย

```css
/* ✅ ข้อดี: ความแม่นยำ, การควบคุมที่ชัดเจน */
/* ❌ ข้อเสีย: ไม่ responsive ตามการตั้งค่าผู้ใช้, ไม่เหมาะกับ high-DPI */
```

## 2. % (Percentage): หน่วยเปอร์เซ็นต์

### ความหมายและการทำงาน

`%` คือหน่วยวัดสัมพัทธ์ที่คำนวณจาก parent element ทำให้สามารถสร้าง layout ที่ยืดหยุ่นได้

### การใช้งานและตัวอย่าง

```css
/* Layout responsive */
.percentage-layout {
  width: 100%; /* เต็มความกว้างของ parent */
  max-width: 1200px;
  margin: 0 auto; /* จัดกึ่งกลาง */
}

/* Grid system */
.grid-container {
  display: flex;
  gap: 2%;
}

.grid-item-half {
  width: 49%;
}
.grid-item-third {
  width: 31.33%;
}
.grid-item-quarter {
  width: 23.5%;
}

/* Responsive images */
.responsive-image {
  width: 100%;
  height: auto;
  max-width: 100%;
}

/* Progress bar */
.progress-bar {
  width: 100%;
  height: 8px;
  background: #f0f0f0;
  border-radius: 4px;
}

.progress-fill {
  height: 100%;
  background: #4caf50;
  width: 75%; /* Progress percentage */
  border-radius: 4px;
  transition: width 0.3s ease;
}

/* Background positioning */
.bg-position {
  background-position: 75% 25%; /* จากซ้าย 75%, จากบน 25% */
}

/* Centering with transform */
.center-absolute {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

### หมายเหตุสำคัญ

```css
/* ⚠️ Percentage padding/margin คำนวณจาก parent width ทุกด้าน */
.percentage-spacing {
  margin: 5%; /* 5% ของ parent width ทุกด้าน */
  padding: 10%; /* 10% ของ parent width ทุกด้าน */
}

/* ⚠️ Height percentage ต้องการ parent มี height ที่กำหนด */
.height-percentage {
  height: 60%; /* parent ต้องมี height ที่ชัดเจน */
}
```

## 3. em: หน่วยสัมพัทธ์กับ font-size

### ความหมายและการทำงาน

`em` คือหน่วยวัดที่อ้างอิงจาก font-size ของ element นั้นเอง หรือ parent element ทำให้ขนาดเปลี่ยนแปลงตาม typography hierarchy

### การใช้งานและตัวอย่าง

```css
/* Basic em usage */
.em-examples {
  font-size: 16px; /* Base font size */
  padding: 1em; /* = 16px */
  margin: 0.5em; /* = 8px */
  border-radius: 0.25em; /* = 4px */
}

/* Em cascading effect (ระวัง compound problem!) */
.parent-em {
  font-size: 18px;
}

.child-em {
  font-size: 1.2em; /* = 18px * 1.2 = 21.6px */
}

.grandchild-em {
  font-size: 1.2em; /* = 21.6px * 1.2 = 25.92px (compound!) */
}

/* เหมาะสำหรับ components ที่ต้อง scale ตาม font-size */
.button-em {
  font-size: 1rem;
  padding: 0.75em 1.5em; /* Scale ตาม font-size */
  border-radius: 0.25em;
  border: 0.125em solid transparent;
}

.button-small {
  font-size: 0.875rem;
} /* padding จะเล็กตาม */
.button-large {
  font-size: 1.25rem;
} /* padding จะใหญ่ตาม */

/* Icon ที่อยู่ในข้อความ */
.icon-em {
  width: 1em;
  height: 1em;
  vertical-align: -0.125em;
}

/* Form elements */
.form-em input {
  font-size: 1em; /* Inherit from parent */
  padding: 0.75em 1em;
  border: 0.125em solid #ccc;
  border-radius: 0.25em;
}

/* Typography spacing */
.text-em {
  line-height: 1.5em;
  margin-bottom: 1em; /* ระยะห่างเท่ากับ font-size */
}
```

## 4. rem: หน่วยสัมพัทธ์กับ root font-size ⭐ (แนะนำสำหรับ font-size)

### ความหมายและการทำงาน

`rem` (root em) อ้างอิงจาก font-size ของ root element (`html`) ทำให้ขนาดคงที่และคาดเดาได้ **เป็นหน่วยที่แนะนำสำหรับ font-size**

### ทำไมควรใช้ rem สำหรับ font-size ⭐

```css
/* 🎯 ข้อดีของ rem สำหรับ font-size */

html {
  font-size: 16px; /* Base size */
}

/* 1. ความสอดคล้อง - ไม่มีการ cascade */
.typography-rem {
  font-size: 1rem; /* = 16px เสมอ */
  font-size: 1.25rem; /* = 20px เสมอ */
  font-size: 1.5rem; /* = 24px เสมอ */
}

/* 2. ไม่มีปัญหา compound */
.parent-rem {
  font-size: 1.2rem;
} /* = 19.2px */
.child-rem {
  font-size: 1.2rem;
} /* = 19.2px (ไม่ใช่ 23.04px) */

/* 3. User accessibility - ตอบสนองการตั้งค่า browser */
/* เมื่อผู้ใช้เปลี่ยน browser font-size rem จะปรับตาม */

/* 4. Design system consistency */
:root {
  --text-xs: 0.75rem; /* 12px */
  --text-sm: 0.875rem; /* 14px */
  --text-base: 1rem; /* 16px */
  --text-lg: 1.125rem; /* 18px */
  --text-xl: 1.25rem; /* 20px */
  --text-2xl: 1.5rem; /* 24px */
  --text-3xl: 1.875rem; /* 30px */
  --text-4xl: 2.25rem; /* 36px */
}

/* 5. Easy global scaling */
@media (max-width: 640px) {
  html {
    font-size: 14px;
  } /* ทุก rem จะเล็กลง */
}

@media (min-width: 1200px) {
  html {
    font-size: 18px;
  } /* ทุก rem จะใหญ่ขึ้น */
}
```

### การใช้งาน rem อย่างมีประสิทธิภาพ

```css
/* Typography system ด้วย rem */
.typography-system {
  /* Headings */
  h1 {
    font-size: 2.5rem;
    font-weight: 700;
    line-height: 1.2;
  }
  h2 {
    font-size: 2rem;
    font-weight: 600;
    line-height: 1.3;
  }
  h3 {
    font-size: 1.5rem;
    font-weight: 600;
    line-height: 1.4;
  }
  h4 {
    font-size: 1.25rem;
    font-weight: 500;
    line-height: 1.5;
  }

  /* Body text */
  p {
    font-size: 1rem;
    line-height: 1.6;
  }
  small {
    font-size: 0.875rem;
    line-height: 1.5;
  }
}

/* Spacing system */
.spacing-rem {
  --space-1: 0.25rem; /* 4px */
  --space-2: 0.5rem; /* 8px */
  --space-4: 1rem; /* 16px */
  --space-6: 1.5rem; /* 24px */
  --space-8: 2rem; /* 32px */
  --space-12: 3rem; /* 48px */
}

/* Component with rem */
.card-rem {
  font-size: 1rem;
  padding: 1.5rem;
  margin-bottom: 2rem;
  border-radius: 0.5rem;
}

.card-rem h3 {
  font-size: 1.25rem;
  margin-bottom: 1rem;
}

/* Button system */
.btn {
  font-size: 1rem;
  padding: 0.75rem 1.5rem;
  border-radius: 0.375rem;
}

.btn-sm {
  font-size: 0.875rem;
  padding: 0.5rem 1rem;
}
.btn-lg {
  font-size: 1.125rem;
  padding: 1rem 2rem;
}
```

### rem vs em: การเปรียบเทียบ

```css
/* ❌ ปัญหาของ em: Compound effect */
.em-compound {
  font-size: 1.2em;
}
.em-compound .nested {
  font-size: 1.2em; /* = 1.2 * 1.2 = 1.44em */
}

/* ✅ ข้อดีของ rem: Predictable */
.rem-predictable {
  font-size: 1.2rem; /* = 19.2px */
}
.rem-predictable .nested {
  font-size: 1.2rem; /* = 19.2px (ไม่ compound) */
}
```

## 5. vw และ vh: Viewport Units

### ความหมายและการทำงาน

- `vw` (viewport width): 1vw = 1% ของความกว้าง viewport
- `vh` (viewport height): 1vh = 1% ของความสูง viewport

### การใช้งานและตัวอย่าง

```css
/* Full viewport */
.viewport-full {
  width: 100vw; /* เต็มความกว้าง viewport */
  height: 100vh; /* เต็มความสูง viewport */
}

/* Hero section */
.hero {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.hero h1 {
  font-size: clamp(2rem, 6vw, 4rem); /* Responsive font */
}

/* Sidebar layout */
.layout {
  display: flex;
  height: 100vh;
}

.sidebar {
  width: 20vw;
  min-width: 250px; /* Minimum width */
}

.main {
  width: 80vw;
  overflow-y: auto;
}

/* Modal */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal {
  width: 90vw;
  max-width: 600px;
  max-height: 80vh;
  background: white;
  border-radius: 8px;
  padding: 2rem;
  overflow-y: auto;
}

/* Responsive spacing */
.section {
  padding: 5vh 5vw;
  min-height: 100vh;
}

/* Grid with viewport */
.grid-viewport {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(300px, 45vw), 1fr));
  gap: 2vw;
  padding: 3vh 5vw;
}
```

### การแก้ปัญหา Mobile

```css
/* iOS Safari vh fix */
.vh-fix {
  height: 100vh;
  height: -webkit-fill-available; /* iOS fix */
}

/* Mobile adjustments */
@media (max-width: 768px) {
  .mobile-viewport {
    width: 95vw; /* เว้นพื้นที่ขอบ */
    height: 90vh; /* เว้นพื้นที่ UI */
    padding: 2vh 2.5vw;
  }
}

/* Large screen limits */
@media (min-width: 1400px) {
  .large-limit {
    max-width: 1200px;
    margin: 0 auto;
    padding: 5vh 2rem; /* ใช้ rem แทน vw */
  }
}
```

## 6. ch (Character Width): หน่วยตัวอักษร

### ความหมายและการทำงาน

`ch` คือความกว้างของอักษร "0" ในฟอนต์ปัจจุบัน ใช้สำหรับการจัด layout ที่เกี่ยวกับข้อความ

### การใช้งานและตัวอย่าง

```css
/* Reading width ที่เหมาะสม */
.article {
  max-width: 65ch; /* ความกว้างอ่านง่าย */
  line-height: 1.6;
  margin: 0 auto;
  padding: 2rem;
}

/* Form input sizing */
.form-inputs {
  .name-input {
    width: 25ch;
  }
  .email-input {
    width: 35ch;
  }
  .phone-input {
    width: 15ch;
  }
  .zip-input {
    width: 8ch;
  }
  .year-input {
    width: 6ch;
  }
  .cvv-input {
    width: 5ch;
  }
}

/* Code block */
.code-block {
  font-family: 'Courier New', monospace;
  width: 80ch;
  padding: 1rem;
  background: #f5f5f5;
  border-radius: 4px;
  overflow-x: auto;
}

/* Text indentation */
.indent {
  text-indent: 4ch;
}

/* Menu spacing */
.menu {
  display: flex;
  gap: 3ch;
}

/* Responsive reading */
@media (max-width: 768px) {
  .article {
    max-width: 50ch; /* ลดความกว้างใน mobile */
  }
}

/* Table columns */
.table {
  .col-id {
    width: 8ch;
  }
  .col-name {
    width: 30ch;
  }
  .col-email {
    width: 35ch;
  }
  .col-date {
    width: 12ch;
  }
}

/* Chat interface */
.chat-message {
  max-width: 50ch;
  padding: 0.75rem 1rem;
  border-radius: 1rem;
  margin-bottom: 1rem;
  word-wrap: break-word;
}

.chat-input {
  width: 60ch;
  max-width: 100%;
  padding: 0.75rem 1rem;
  border: 1px solid #ddd;
  border-radius: 2rem;
}
```

## 7. ex (X-height): หน่วยความสูงตัวอักษร

### ความหมายและการทำงาน

`ex` คือความสูงของอักษร "x" ในฟอนต์ปัจจุบัน ใช้สำหรับการจัดตำแหน่งที่ละเอียด

### การใช้งานและตัวอย่าง

```css
/* Fine typography adjustments */
.superscript {
  vertical-align: 1ex;
  font-size: 0.7em;
}

.subscript {
  vertical-align: -0.5ex;
  font-size: 0.7em;
}

/* Icon alignment */
.icon-inline {
  vertical-align: -0.125ex;
  width: 1em;
  height: 1em;
}

/* Drop cap */
.drop-cap::first-letter {
  font-size: 4ex;
  float: left;
  line-height: 1;
  margin-right: 0.2em;
  margin-top: 0.1ex;
}

/* Math expressions */
.fraction {
  border-top: 1px solid black;
  padding-top: 0.5ex;
  margin-top: 0.5ex;
}

/* Small caps effect */
.small-caps {
  font-size: 0.8em;
  vertical-align: 0.1ex;
  letter-spacing: 0.1em;
}
```

## 8. Modern CSS Functions

### min(), max(), clamp()

```css
/* Modern responsive functions */
.modern-sizing {
  /* min() - เลือกค่าที่เล็กกว่า */
  width: min(90vw, 800px);

  /* max() - เลือกค่าที่ใหญ่กว่า */
  height: max(50vh, 400px);

  /* clamp() - จำกัดค่าระหว่างต่ำสุดและสูงสุด */
  font-size: clamp(1rem, 4vw, 2.5rem);
  padding: clamp(1rem, 5vw, 3rem);
}

/* Fluid typography */
.fluid-text {
  h1 {
    font-size: clamp(2rem, 6vw, 4rem);
  }
  h2 {
    font-size: clamp(1.5rem, 4vw, 3rem);
  }
  p {
    font-size: clamp(1rem, 2.5vw, 1.125rem);
  }
}

/* Responsive grid */
.modern-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(300px, 100%), 1fr));
  gap: clamp(1rem, 3vw, 2rem);
}
```

## 9. การเลือกใช้ Units อย่างเหมาะสม

### Decision Matrix

```css
/* 🎯 เมื่อไหร่ควรใช้ unit ไหน */

/* ใช้ px เมื่อ: */
.use-px {
  /* ✅ ความแม่นยำสำคัญ: borders, shadows, icons */
  border: 1px solid #ddd;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  icon-size: 16px;
}

/* ใช้ % เมื่อ: */
.use-percent {
  /* ✅ Layout responsive, images, grid systems */
  width: 50%;
  max-width: 100%;
  background-position: 50% 75%;
}

/* ใช้ em เมื่อ: */
.use-em {
  /* ✅ ขนาดที่ scale ตาม font-size: padding, icons ในข้อความ */
  padding: 0.75em 1.5em;
  width: 1em; /* icon */
}

/* ใช้ rem เมื่อ: (แนะนำสำหรับ font-size!) */
.use-rem {
  /* ✅ Font sizes, consistent spacing, component dimensions */
  font-size: 1.25rem;
  padding: 1.5rem;
  border-radius: 0.5rem;
}

/* ใช้ vw/vh เมื่อ: */
.use-viewport {
  /* ✅ Full-screen, hero sections, responsive spacing */
  height: 100vh;
  font-size: clamp(1rem, 4vw, 2rem);
  padding: 5vh 5vw;
}

/* ใช้ ch เมื่อ: */
.use-ch {
  /* ✅ Reading width, form inputs, code blocks */
  max-width: 65ch;
  width: 30ch; /* email input */
}

/* ใช้ ex เมื่อ: */
.use-ex {
  /* ✅ Fine typography adjustments, icon alignment */
  vertical-align: 0.5ex;
  margin-top: -0.1ex;
}
```

### Best Practice Combinations

```css
/* 🏆 แนวทางปฏิบัติที่ดี */

/* Typography system */
.typography-best {
  font-size: 1rem; /* rem สำหรับ font-size */
  line-height: 1.6; /* unitless สำหรับ line-height */
  margin-bottom: 1em; /* em สำหรับ spacing ที่เกี่ยวกับ text */
  max-width: 65ch; /* ch สำหรับ reading width */
}

/* Button component */
.button-best {
  font-size: 1rem; /* rem สำหรับ font-size */
  padding: 0.75em 1.5em; /* em สำหรับ padding ที่ scale */
  border-radius: 0.375rem; /* rem สำหรับ border-radius */
  border: 1px solid transparent; /* px สำหรับ border */
}

/* Card component */
.card-best {
  padding: 1.5rem; /* rem สำหรับขนาดหลัก */
  margin-bottom: 2rem; /* rem สำหรับ spacing */
  border-radius: 0.5rem; /* rem สำหรับ border-radius */
  width: 100%; /* % สำหรับ responsive */
  max-width: 400px; /* px สำหรับ max constraint */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* px สำหรับ shadow */
}

/* Form styling */
.form-best input {
  font-size: 1rem; /* rem สำหรับ font-size */
  padding: 0.75rem 1rem; /* rem สำหรับ spacing */
  border: 1px solid #ddd; /* px สำหรับ border */
  border-radius: 0.25rem; /* rem สำหรับ border-radius */
  width: 30ch; /* ch สำหรับ input width */
  max-width: 100%; /* % สำหรับ responsive */
}

/* Layout responsive */
.layout-best {
  width: 100%; /* % สำหรับ flexible width */
  max-width: 1200px; /* px สำหรับ max constraint */
  padding: clamp(1rem, 5vw, 3rem); /* clamp สำหรับ fluid spacing */
  margin: 0 auto; /* การจัดกลาง */
}
```

## 10. สรุป Best Practices

### หลักการเลือกใช้ Units

1. **rem สำหรับ font-size** ⭐ - ความสอดคล้อง, accessibility, ไม่มี compound problem
2. **px สำหรับ borders, shadows, icons** - ความแม่นยำ
3. **% สำหรับ layout responsive** - ความยืดหยุ่น
4. **em สำหรับ spacing ที่เกี่ยวกับ typography** - scale ตาม font-size
5. **vw/vh สำหรับ viewport-based design** - full-screen, responsive
6. **ch สำหรับ text-based sizing** - reading width, form inputs
7. **ex สำหรับ fine typography** - การจัดตำแหน่งละเอียด
8. **clamp() สำหรับ fluid design** - responsive ขั้นสูง

### สูตรสำเร็จ

```css
/* สูตรการใช้ units อย่างมีประสิทธิภาพ */
.optimal-component {
  /* Typography */
  font-size: 1rem; /* rem: predictable, accessible */
  line-height: 1.6; /* unitless: relative to font-size */

  /* Spacing */
  padding: 1rem 1.5rem; /* rem: consistent */
  margin-bottom: 1em; /* em: relative to text */

  /* Layout */
  width: 100%; /* %: flexible */
  max-width: min(65ch, 90vw); /* ch + vw: readable + responsive */

  /* Details */
  border: 1px solid #ddd; /* px: precise */
  border-radius: 0.5rem; /* rem: consistent */
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1); /* px: precise */
}

/* Responsive system */
html {
  font-size: 16px;
}

@media (max-width: 640px) {
  html {
    font-size: 14px;
  } /* ทุก rem จะเล็กลง */
}

@media (min-width: 1200px) {
  html {
    font-size: 18px;
  } /* ทุก rem จะใหญ่ขึ้น */
}
```

การเรียนรู้และใช้งาน CSS Units อย่างถูกต้องจะช่วยสร้างการออกแบบที่สวยงาม ตอบสนอง และเข้าถึงได้!
