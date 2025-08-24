# Box Model Properties: คู่มือฉบับสมบูรณ์

## ภาพรวม Box Model Properties

Properties ที่เกี่ยวข้องกับ Box Model เป็นเครื่องมือหลักในการจัด layout และ spacing ในการออกแบบเว็บ ประกอบด้วย `margin`, `padding`, `border`, `border-radius`, และ `box-sizing` ซึ่ง `box-sizing: border-box` เป็น property ที่สำคัญมากในการออกแบบสมัยใหม่

### โครงสร้างและความสัมพันธ์

```css
/* ตัวอย่างการใช้ Box Model Properties ร่วมกัน */
.box-model-demo {
  /* box-sizing: เปลี่ยนวิธีคำนวณขนาด */
  box-sizing: border-box; /* ⭐ แนะนำ */

  /* ขนาดพื้นฐาน */
  width: 300px;
  height: 200px;

  /* padding: พื้นที่ภายใน */
  padding: 2rem;

  /* border: เส้นขอบ */
  border: 2px solid #3b82f6;

  /* border-radius: มุมโค้ง */
  border-radius: 1rem;

  /* margin: พื้นที่ภายนอก */
  margin: 1.5rem auto;

  /* สไตล์เสริม */
  background-color: #f8fafc;
  color: #1e293b;
}

/*
กับ box-sizing: border-box
- Total width = 300px (รวม padding + border แล้ว)
- Content width = 300px - (2rem * 2) - (2px * 2) = 300px - padding - border
- Total height = 200px (รวม padding + border แล้ว)
*/
```

## 1. box-sizing: การกำหนดวิธีคำนวณขนาด ⭐

### ความหมายและความสำคัญ

`box-sizing` เป็น property ที่กำหนดว่าขนาด width และ height จะคำนวณอย่างไร เป็น property ที่สำคัญมากในการออกแบบ layout สมัยใหม่

### box-sizing Values

```css
/* content-box (default) - วิธีเก่า */
.content-box {
  box-sizing: content-box; /* ค่า default */
  width: 300px;
  height: 200px;
  padding: 2rem; /* 32px */
  border: 2px solid #000;

  /*
  Total width = 300px + 32px + 32px + 2px + 2px = 368px
  Total height = 200px + 32px + 32px + 2px + 2px = 268px
  Content area = 300px × 200px
  */
}

/* border-box (แนะนำ) - วิธีสมัยใหม่ ⭐ */
.border-box {
  box-sizing: border-box; /* แนะนำ! */
  width: 300px;
  height: 200px;
  padding: 2rem; /* 32px */
  border: 2px solid #000;

  /*
  Total width = 300px (รวม padding + border แล้ว)
  Total height = 200px (รวม padding + border แล้ว)
  Content area = 300px - 64px - 4px = 232px × 136px
  */
}

/* inherit - สืบทอดจาก parent */
.inherit-box {
  box-sizing: inherit;
}
```

### ทำไมควรใช้ border-box ⭐

```css
/* 🎯 เหตุผลที่ควรใช้ border-box */

/* ❌ ปัญหาของ content-box */
.content-box-problem {
  box-sizing: content-box; /* default */
  width: 50%;
  padding: 2rem;
  border: 1px solid #ccc;

  /* Total width = 50% + 4rem + 2px = มากกว่า 50%! */
  /* อาจทำให้ layout พัง */
}

/* ✅ ข้อดีของ border-box */
.border-box-solution {
  box-sizing: border-box;
  width: 50%;
  padding: 2rem;
  border: 1px solid #ccc;

  /* Total width = 50% แน่นอน! */
  /* padding และ border รวมอยู่ใน 50% แล้ว */
}

/* การตั้งค่า global (แนะนำ) */
*,
*::before,
*::after {
  box-sizing: border-box;
}

/* หรือแบบ inherit */
html {
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}
```

### การใช้งาน border-box ในทางปฏิบัติ

```css
/* Grid layout ที่คาดเดาได้ */
.grid-border-box {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
}

.grid-item {
  box-sizing: border-box;
  padding: 1.5rem;
  border: 2px solid #e5e7eb;
  background: white;

  /* แต่ละ item จะมีขนาดเท่ากันแน่นอน */
  /* ไม่ว่า padding หรือ border จะเป็นเท่าไหร่ */
}

/* Responsive columns */
.responsive-columns {
  box-sizing: border-box;
}

.col-6 {
  width: 50%;
  padding: 0 1rem;
  border: 1px solid #ddd;

  /* Total width = 50% เสมอ */
}

.col-4 {
  width: 33.333%;
  padding: 0 1rem;
  border: 1px solid #ddd;

  /* Total width = 33.333% เสมอ */
}

/* Form elements */
.form-border-box input,
.form-border-box textarea,
.form-border-box select {
  box-sizing: border-box;
  width: 100%;
  padding: 0.75rem 1rem;
  border: 1px solid #d1d5db;
  border-radius: 0.375rem;

  /* ทุก input จะมีขนาด 100% แน่นอน */
}
```

## 2. margin: การจัดการพื้นที่ภายนอก

### Margin Properties และ Syntax

```css
/* Individual margin properties */
.margin-individual {
  margin-top: 1rem;
  margin-right: 2rem;
  margin-bottom: 1.5rem;
  margin-left: 0.5rem;
}

/* Shorthand margin syntax */
.margin-shorthand {
  /* ทุกด้านเท่ากัน */
  margin: 1rem;

  /* แนวตั้ง | แนวนอน */
  margin: 1rem 2rem;

  /* บน | แนวนอน | ล่าง */
  margin: 1rem 2rem 1.5rem;

  /* บน | ขวา | ล่าง | ซ้าย (ตามเข็มนาฬิกา) */
  margin: 1rem 2rem 1.5rem 0.5rem;
}

/* Auto margins สำหรับการจัดกลาง */
.margin-auto {
  /* จัดกลางแนวนอน */
  margin: 0 auto;
  width: 600px;
  max-width: 90%;

  /* จัดกลางแนวตั้งและแนวนอน (flex context) */
  margin: auto;
}

/* Negative margins */
.negative-margins {
  /* ดึง element เข้าหาด้านบน */
  margin-top: -2rem;

  /* ยื่นออกจาก container */
  margin: 0 -2rem;
  width: calc(100% + 4rem);

  /* ทับซ้อนกับ element ด้านล่าง */
  margin-bottom: -1rem;
}
```

### Margin Collapse

```css
/* การ collapse ของ margin */
.margin-collapse-demo {
  .element-1 {
    margin-bottom: 2rem; /* 32px */
    background: #fef2f2;
    padding: 1rem;
  }

  .element-2 {
    margin-top: 1rem; /* 16px */
    background: #f0f9ff;
    padding: 1rem;
  }

  /*
  ระยะห่างจริงระหว่าง element = max(2rem, 1rem) = 2rem
  ไม่ใช่ 2rem + 1rem = 3rem
  */
}

/* วิธีป้องกัน margin collapse */
.prevent-collapse {
  /* วิธีที่ 1: ใช้ padding แทน margin */
  .parent-padding {
    padding-top: 2rem;
    padding-bottom: 2rem;
  }

  /* วิธีที่ 2: ใช้ flexbox */
  .flex-container {
    display: flex;
    flex-direction: column;
    gap: 2rem; /* ระยะห่างที่แน่นอน */
  }

  /* วิธีที่ 3: ใช้ border หรือ padding เล็กน้อย */
  .parent-border {
    border-top: 1px solid transparent;
    border-bottom: 1px solid transparent;
  }
}
```

### Responsive Margins

```css
/* Responsive margin system */
.responsive-margins {
  /* Base margins */
  margin: 1rem 0;

  /* Tablet */
  @media (min-width: 768px) {
    margin: 2rem 0;
  }

  /* Desktop */
  @media (min-width: 1024px) {
    margin: 3rem 0;
  }

  /* Large screens */
  @media (min-width: 1440px) {
    margin: 4rem 0;
  }
}

/* Fluid margins */
.fluid-margins {
  margin: clamp(1rem, 5vw, 4rem) 0;
  margin-left: clamp(1rem, 5vw, 3rem);
  margin-right: clamp(1rem, 5vw, 3rem);
}

/* Utility margin classes */
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
  .m-12 {
    margin: 3rem;
  }
  .m-16 {
    margin: 4rem;
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

  /* Negative margins */
  .-m-4 {
    margin: -1rem;
  }
  .-mt-4 {
    margin-top: -1rem;
  }
  .-ml-4 {
    margin-left: -1rem;
  }
}
```

## 3. padding: การจัดการพื้นที่ภายใน

### Padding Properties และ Syntax

```css
/* Individual padding properties */
.padding-individual {
  padding-top: 1rem;
  padding-right: 2rem;
  padding-bottom: 1.5rem;
  padding-left: 0.5rem;
}

/* Shorthand padding syntax */
.padding-shorthand {
  /* ทุกด้านเท่ากัน */
  padding: 1rem;

  /* แนวตั้ง | แนวนอน */
  padding: 1rem 2rem;

  /* บน | แนวนอน | ล่าง */
  padding: 1rem 2rem 1.5rem;

  /* บน | ขวา | ล่าง | ซ้าย (ตามเข็มนาฬิกา) */
  padding: 1rem 2rem 1.5rem 0.5rem;
}

/* Percentage padding */
.percentage-padding {
  /* Padding percentage คำนวณจาก parent width ทุกด้าน */
  padding: 5%; /* 5% ของ parent width ทุกด้าน */

  /* สร้าง aspect ratio */
  padding-bottom: 56.25%; /* 16:9 aspect ratio */
  height: 0;
  position: relative;
}

.percentage-padding > * {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
```

### Component Padding Patterns

```css
/* Button padding system */
.btn-padding {
  /* Base button */
  padding: 0.75rem 1.5rem;
  font-size: 1rem;
  border-radius: 0.375rem;
  border: 1px solid transparent;
  cursor: pointer;
  transition: all 0.2s ease;
}

.btn-xs {
  padding: 0.375rem 0.75rem;
  font-size: 0.75rem;
}
.btn-sm {
  padding: 0.5rem 1rem;
  font-size: 0.875rem;
}
.btn-lg {
  padding: 1rem 2rem;
  font-size: 1.125rem;
}
.btn-xl {
  padding: 1.25rem 2.5rem;
  font-size: 1.25rem;
}

/* Card padding system */
.card-padding {
  /* Base card */
  padding: 1.5rem;
  background: white;
  border: 1px solid #e5e7eb;
  border-radius: 0.5rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.card-header {
  padding: 1rem 1.5rem;
  margin: -1.5rem -1.5rem 1rem;
  border-bottom: 1px solid #e5e7eb;
  border-radius: 0.5rem 0.5rem 0 0;
  background: #f8fafc;
}

.card-footer {
  padding: 1rem 1.5rem;
  margin: 1rem -1.5rem -1.5rem;
  border-top: 1px solid #e5e7eb;
  border-radius: 0 0 0.5rem 0.5rem;
  background: #f8fafc;
}

/* Card sizes */
.card-compact {
  padding: 1rem;
}
.card-comfortable {
  padding: 2rem;
}
.card-spacious {
  padding: 3rem;
}

/* Form padding */
.form-padding {
  .form-input {
    padding: 0.75rem 1rem;
    border: 1px solid #d1d5db;
    border-radius: 0.375rem;
    font-size: 1rem;
    line-height: 1.5;
  }

  .form-input-sm {
    padding: 0.5rem 0.75rem;
    font-size: 0.875rem;
  }
  .form-input-lg {
    padding: 1rem 1.25rem;
    font-size: 1.125rem;
  }

  .form-textarea {
    padding: 0.75rem 1rem;
    min-height: 6rem;
    resize: vertical;
  }

  .form-select {
    padding: 0.75rem 2.5rem 0.75rem 1rem; /* พื้นที่สำหรับ arrow */
  }
}

/* Navigation padding */
.nav-padding {
  .nav-link {
    padding: 1rem 1.5rem;
    display: block;
    text-decoration: none;
    color: #374151;
    transition: all 0.2s ease;
  }

  .nav-link:hover {
    background-color: #f3f4f6;
    color: #1f2937;
  }

  /* Responsive nav padding */
  @media (max-width: 768px) {
    .nav-link {
      padding: 0.75rem 1rem;
    }
  }
}
```

### Responsive Padding

```css
/* Responsive padding system */
.responsive-padding {
  /* Mobile first */
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

/* Fluid padding */
.fluid-padding {
  padding: clamp(1rem, 5vw, 3rem);
  padding: clamp(0.5rem, 2vh, 2rem) clamp(1rem, 5vw, 4rem);
}

/* Container padding */
.container-padding {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;

  @media (min-width: 640px) {
    padding: 0 1.5rem;
  }

  @media (min-width: 1024px) {
    padding: 0 2rem;
  }
}

/* Section padding */
.section-padding {
  .section-sm {
    padding: 2rem 0;
  }
  .section {
    padding: 4rem 0;
  }
  .section-lg {
    padding: 6rem 0;
  }
  .section-xl {
    padding: 8rem 0;
  }

  @media (max-width: 768px) {
    .section-sm {
      padding: 1rem 0;
    }
    .section {
      padding: 2rem 0;
    }
    .section-lg {
      padding: 3rem 0;
    }
    .section-xl {
      padding: 4rem 0;
    }
  }
}
```

## 4. border: การจัดการเส้นขอบ

### Border Properties

```css
/* Individual border properties */
.border-individual {
  border-width: 2px;
  border-style: solid;
  border-color: #3b82f6;

  /* แยกตามด้าน */
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

/* Shorthand border syntax */
.border-shorthand {
  /* width | style | color */
  border: 2px solid #3b82f6;

  /* แยกตามด้าน */
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

/* Border widths */
.border-widths {
  .border-0 {
    border: 0;
  }
  .border {
    border: 1px solid;
  }
  .border-2 {
    border: 2px solid;
  }
  .border-4 {
    border: 4px solid;
  }
  .border-8 {
    border: 8px solid;
  }

  /* ตามด้าน */
  .border-t {
    border-top: 1px solid;
  }
  .border-r {
    border-right: 1px solid;
  }
  .border-b {
    border-bottom: 1px solid;
  }
  .border-l {
    border-left: 1px solid;
  }

  .border-t-2 {
    border-top: 2px solid;
  }
  .border-b-4 {
    border-bottom: 4px solid;
  }
}
```

### Border Colors และ Design Patterns

```css
/* Border color system */
.border-colors {
  /* Neutral borders */
  .border-gray-100 {
    border-color: #f3f4f6;
  }
  .border-gray-200 {
    border-color: #e5e7eb;
  }
  .border-gray-300 {
    border-color: #d1d5db;
  }
  .border-gray-400 {
    border-color: #9ca3af;
  }
  .border-gray-500 {
    border-color: #6b7280;
  }

  /* Semantic borders */
  .border-primary {
    border-color: #3b82f6;
  }
  .border-success {
    border-color: #10b981;
  }
  .border-warning {
    border-color: #f59e0b;
  }
  .border-danger {
    border-color: #ef4444;
  }
  .border-info {
    border-color: #06b6d4;
  }

  /* Transparent border */
  .border-transparent {
    border-color: transparent;
  }
  .border-current {
    border-color: currentColor;
  }
}

/* Design patterns */
.border-patterns {
  /* Card with subtle border */
  .card-border {
    border: 1px solid #e5e7eb;
    border-radius: 0.5rem;
    padding: 1.5rem;
    background: white;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }

  /* Accent borders */
  .accent-left {
    border-left: 4px solid #3b82f6;
    padding-left: 1rem;
  }

  .accent-top {
    border-top: 3px solid #10b981;
    padding-top: 1rem;
  }

  /* Quote styling */
  .quote-border {
    border-left: 3px solid #6b7280;
    padding-left: 1.5rem;
    margin-left: 1rem;
    font-style: italic;
    color: #4b5563;
  }

  /* Status indicators */
  .status-success {
    border: 2px solid #10b981;
    background-color: #d1fae5;
    color: #065f46;
    padding: 1rem;
    border-radius: 0.5rem;
  }

  .status-warning {
    border: 2px solid #f59e0b;
    background-color: #fef3c7;
    color: #92400e;
    padding: 1rem;
    border-radius: 0.5rem;
  }

  .status-error {
    border: 2px solid #ef4444;
    background-color: #fee2e2;
    color: #991b1b;
    padding: 1rem;
    border-radius: 0.5rem;
  }
}

/* Interactive borders */
.interactive-borders {
  .input-border {
    border: 1px solid #d1d5db;
    border-radius: 0.375rem;
    padding: 0.75rem 1rem;
    transition: border-color 0.2s ease, box-shadow 0.2s ease;
  }

  .input-border:focus {
    outline: none;
    border-color: #3b82f6;
    box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
  }

  .button-border {
    border: 2px solid #3b82f6;
    background: transparent;
    color: #3b82f6;
    padding: 0.75rem 1.5rem;
    border-radius: 0.375rem;
    cursor: pointer;
    transition: all 0.2s ease;
  }

  .button-border:hover {
    background: #3b82f6;
    color: white;
  }

  .card-hover {
    border: 1px solid #e5e7eb;
    transition: border-color 0.2s ease, box-shadow 0.2s ease;
  }

  .card-hover:hover {
    border-color: #3b82f6;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }
}
```

## 5. border-radius: การจัดการมุมโค้ง

### Border Radius Properties

```css
/* Individual border-radius properties */
.border-radius-individual {
  border-top-left-radius: 0.5rem;
  border-top-right-radius: 1rem;
  border-bottom-right-radius: 1.5rem;
  border-bottom-left-radius: 2rem;
}

/* Shorthand border-radius */
.border-radius-shorthand {
  /* ทุกมุมเท่ากัน */
  border-radius: 0.5rem;

  /* มุมบนซ้าย + ล่างขวา | มุมบนขวา + ล่างซ้าย */
  border-radius: 1rem 0.5rem;

  /* บนซ้าย | บนขวา + ล่างซ้าย | ล่างขวา */
  border-radius: 1rem 0.5rem 1.5rem;

  /* บนซ้าย | บนขวา | ล่างขวา | ล่างซ้าย */
  border-radius: 1rem 0.5rem 1.5rem 2rem;
}

/* Elliptical border-radius */
.elliptical-radius {
  /* horizontal-radius / vertical-radius */
  border-radius: 2rem / 1rem;

  /* แต่ละมุมแยก elliptical */
  border-radius: 2rem 1rem 2rem 1rem / 1rem 2rem 1rem 2rem;
}

/* Common border-radius utilities */
.border-radius-utilities {
  .rounded-none {
    border-radius: 0;
  }
  .rounded-sm {
    border-radius: 0.125rem;
  } /* 2px */
  .rounded {
    border-radius: 0.25rem;
  } /* 4px */
  .rounded-md {
    border-radius: 0.375rem;
  } /* 6px */
  .rounded-lg {
    border-radius: 0.5rem;
  } /* 8px */
  .rounded-xl {
    border-radius: 0.75rem;
  } /* 12px */
  .rounded-2xl {
    border-radius: 1rem;
  } /* 16px */
  .rounded-3xl {
    border-radius: 1.5rem;
  } /* 24px */
  .rounded-full {
    border-radius: 9999px;
  } /* วงกลม/pill */

  /* ตามด้าน */
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

  /* ตามมุม */
  .rounded-tl {
    border-top-left-radius: 0.25rem;
  }
  .rounded-tr {
    border-top-right-radius: 0.25rem;
  }
  .rounded-br {
    border-bottom-right-radius: 0.25rem;
  }
  .rounded-bl {
    border-bottom-left-radius: 0.25rem;
  }
}
```

### Design Patterns ด้วย Border Radius

```css
/* Card designs */
.card-designs {
  .card-basic {
    border-radius: 0.5rem;
    padding: 1.5rem;
    background: white;
    border: 1px solid #e5e7eb;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }

  .card-rounded {
    border-radius: 1rem;
    padding: 2rem;
    background: white;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  .card-modern {
    border-radius: 1.5rem;
    padding: 2rem;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
  }

  .card-organic {
    border-radius: 2rem 0.5rem 2rem 0.5rem;
    padding: 2rem;
    background: white;
    border: 2px solid #f3f4f6;
  }
}

/* Button designs */
.button-designs {
  .btn-sharp {
    border-radius: 0;
    padding: 0.75rem 1.5rem;
    background: #3b82f6;
    color: white;
    border: none;
  }

  .btn-rounded {
    border-radius: 0.375rem;
    padding: 0.75rem 1.5rem;
    background: #3b82f6;
    color: white;
    border: none;
  }

  .btn-pill {
    border-radius: 9999px;
    padding: 0.75rem 2rem;
    background: #3b82f6;
    color: white;
    border: none;
  }

  .btn-organic {
    border-radius: 1rem 0.25rem 1rem 0.25rem;
    padding: 0.75rem 1.5rem;
    background: #10b981;
    color: white;
    border: none;
  }
}

/* Avatar และ Image shapes */
.avatar-shapes {
  .avatar-square {
    width: 4rem;
    height: 4rem;
    border-radius: 0.5rem;
    object-fit: cover;
  }

  .avatar-rounded {
    width: 4rem;
    height: 4rem;
    border-radius: 1rem;
    object-fit: cover;
  }

  .avatar-circle {
    width: 4rem;
    height: 4rem;
    border-radius: 50%;
    object-fit: cover;
  }

  .avatar-organic {
    width: 4rem;
    height: 4rem;
    border-radius: 30% 70% 70% 30% / 30% 30% 70% 70%;
    object-fit: cover;
  }
}

/* Form elements */
.form-radius {
  .input-sharp {
    border-radius: 0;
    padding: 0.75rem 1rem;
    border: 1px solid #d1d5db;
  }

  .input-rounded {
    border-radius: 0.375rem;
    padding: 0.75rem 1rem;
    border: 1px solid #d1d5db;
  }

  .input-pill {
    border-radius: 9999px;
    padding: 0.75rem 1.5rem;
    border: 1px solid #d1d5db;
  }

  .input-top-rounded {
    border-radius: 0.375rem 0.375rem 0 0;
    padding: 0.75rem 1rem;
    border: 1px solid #d1d5db;
    border-bottom: none;
  }

  .input-bottom-rounded {
    border-radius: 0 0 0.375rem 0.375rem;
    padding: 0.75rem 1rem;
    border: 1px solid #d1d5db;
  }
}
```

### Responsive Border Radius

```css
/* Responsive border radius */
.responsive-radius {
  /* Mobile */
  border-radius: 0.25rem;

  /* Tablet */
  @media (min-width: 768px) {
    border-radius: 0.5rem;
  }

  /* Desktop */
  @media (min-width: 1024px) {
    border-radius: 0.75rem;
  }
}

/* Dynamic radius based on container */
.dynamic-radius {
  border-radius: clamp(0.25rem, 2vw, 1rem);
}

/* CSS Custom Properties สำหรับ radius system */
:root {
  --radius-sm: 0.125rem;
  --radius-base: 0.25rem;
  --radius-md: 0.375rem;
  --radius-lg: 0.5rem;
  --radius-xl: 0.75rem;
  --radius-2xl: 1rem;
  --radius-3xl: 1.5rem;
  --radius-full: 9999px;
}

.radius-system {
  .card {
    border-radius: var(--radius-lg);
  }
  .button {
    border-radius: var(--radius-md);
  }
  .input {
    border-radius: var(--radius-base);
  }
  .avatar {
    border-radius: var(--radius-full);
  }
}
```

## 6. Practical Examples และ Patterns

### Complete Component Examples

```css
/* Modern Card Component */
.modern-card {
  /* box-sizing ให้ขนาดคาดเดาได้ */
  box-sizing: border-box;

  /* ขนาดและพื้นฐาน */
  width: 100%;
  max-width: 400px;

  /* padding สำหรับพื้นที่ภายใน */
  padding: 2rem;

  /* margin สำหรับระยะห่าง */
  margin: 0 auto 2rem;

  /* border และ radius */
  border: 1px solid #e5e7eb;
  border-radius: 1rem;

  /* สไตล์เสริม */
  background: white;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: all 0.2s ease;
}

.modern-card:hover {
  border-color: #3b82f6;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
  transform: translateY(-2px);
}

/* Button System */
.button-system {
  /* Base button */
  box-sizing: border-box;
  padding: 0.75rem 1.5rem;
  margin: 0 0.5rem 0.5rem 0;
  border: 1px solid transparent;
  border-radius: 0.375rem;
  font-size: 1rem;
  font-weight: 500;
  text-align: center;
  cursor: pointer;
  transition: all 0.2s ease;
}

.btn-primary {
  background: #3b82f6;
  color: white;
  border-color: #3b82f6;
}

.btn-primary:hover {
  background: #2563eb;
  border-color: #2563eb;
}

.btn-outline {
  background: transparent;
  color: #3b82f6;
  border-color: #3b82f6;
}

.btn-outline:hover {
  background: #3b82f6;
  color: white;
}

/* Form System */
.form-system {
  box-sizing: border-box;
  width: 100%;
  max-width: 500px;
  margin: 0 auto;
  padding: 2rem;
  border: 1px solid #e5e7eb;
  border-radius: 0.5rem;
  background: white;
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group:last-child {
  margin-bottom: 0;
}

.form-label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: 500;
  color: #374151;
}

.form-input {
  box-sizing: border-box;
  width: 100%;
  padding: 0.75rem 1rem;
  border: 1px solid #d1d5db;
  border-radius: 0.375rem;
  font-size: 1rem;
  background: white;
  transition: border-color 0.2s ease, box-shadow 0.2s ease;
}

.form-input:focus {
  outline: none;
  border-color: #3b82f6;
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
}

/* Grid System */
.grid-system {
  box-sizing: border-box;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  padding: 2rem;
  margin: 0 auto;
  max-width: 1200px;
}

.grid-item {
  box-sizing: border-box;
  padding: 1.5rem;
  border: 1px solid #e5e7eb;
  border-radius: 0.5rem;
  background: white;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
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
  --space-12: 3rem;
  --space-16: 4rem;
}

/* ✅ ใช้ semantic margin patterns */
.content {
  margin-bottom: 1.5rem; /* ใช้ bottom margin เป็นหลัก */
}

.content:last-child {
  margin-bottom: 0; /* ลบ margin สุดท้าย */
}

/* ✅ ใช้ padding สำหรับ internal spacing */
.component {
  padding: var(--space-6);
}

/* ✅ ใช้ border-radius ที่สอดคล้องกัน */
:root {
  --radius-sm: 0.125rem;
  --radius-base: 0.25rem;
  --radius-lg: 0.5rem;
  --radius-xl: 0.75rem;
  --radius-full: 9999px;
}
```

### DON'Ts ❌

```css
/* ❌ หลีกเลี่ยง content-box ใน modern layouts */
.avoid-content-box {
  box-sizing: content-box; /* ยากต่อการคำนวณ */
  width: 50%;
  padding: 2rem; /* Total width > 50% */
}

/* ❌ หลีกเลี่ยง margin collapse ที่ไม่ต้องการ */
.avoid-margin-issues {
  margin: 2rem 0 2rem 0; /* อาจ collapse */
}

/* ❌ หลีกเลี่ยง negative margins ที่ไม่จำเป็น */
.avoid-negative {
  margin-left: -50px; /* อาจทำให้ layout พัง */
}

/* ❌ หลีกเลี่ยง arbitrary values */
.avoid-arbitrary {
  padding: 13px 27px; /* ไม่อยู่ในระบบ */
  border-radius: 9px; /* ค่าแปลกๆ */
}

/* ❌ หลีกเลี่ยง mixed units ที่ไม่สอดคล้อง */
.avoid-mixed {
  padding: 16px; /* px */
  margin: 1rem; /* rem */
  border-radius: 8px; /* px อีก */
  /* ไม่มีความสัมพันธ์กัน */
}
```

### Quick Setup Template

```css
/* Complete Box Model setup template */

/* 1. Global box-sizing */
*,
*::before,
*::after {
  box-sizing: border-box;
}

/* 2. Design tokens */
:root {
  /* Spacing scale */
  --space-0: 0;
  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-3: 0.75rem;
  --space-4: 1rem;
  --space-5: 1.25rem;
  --space-6: 1.5rem;
  --space-8: 2rem;
  --space-10: 2.5rem;
  --space-12: 3rem;
  --space-16: 4rem;
  --space-20: 5rem;
  --space-24: 6rem;

  /* Border radius scale */
  --radius-none: 0;
  --radius-sm: 0.125rem;
  --radius-base: 0.25rem;
  --radius-md: 0.375rem;
  --radius-lg: 0.5rem;
  --radius-xl: 0.75rem;
  --radius-2xl: 1rem;
  --radius-3xl: 1.5rem;
  --radius-full: 9999px;

  /* Border colors */
  --border-light: #f3f4f6;
  --border-base: #e5e7eb;
  --border-dark: #d1d5db;
  --border-focus: #3b82f6;
}

/* 3. Base styles */
body {
  margin: 0;
  padding: 0;
  line-height: 1.6;
}

/* 4. Layout utilities */
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 var(--space-4);
}

/* 5. Component base */
.btn {
  box-sizing: border-box;
  padding: var(--space-3) var(--space-6);
  border: 1px solid transparent;
  border-radius: var(--radius-md);
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.2s ease;
}

.card {
  box-sizing: border-box;
  padding: var(--space-6);
  border: 1px solid var(--border-base);
  border-radius: var(--radius-lg);
  background: white;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.form-input {
  box-sizing: border-box;
  width: 100%;
  padding: var(--space-3) var(--space-4);
  border: 1px solid var(--border-dark);
  border-radius: var(--radius-md);
  font-size: 1rem;
}

.form-input:focus {
  outline: none;
  border-color: var(--border-focus);
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
}
```

การใช้งาน Box Model Properties อย่างถูกต้องและมีระบบจะทำให้การออกแบบ layout มีความสอดคล้อง คาดเดาได้ และ maintainable!
