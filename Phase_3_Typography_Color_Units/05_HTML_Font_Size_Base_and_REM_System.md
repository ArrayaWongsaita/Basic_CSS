# การตั้งฐาน HTML Font-Size และระบบ REM

## ภาพรวม: ทำไมต้องตั้งฐาน HTML Font-Size

การตั้งค่า `html { font-size: 16px; }` เป็นการสร้างฐานที่มั่นคงสำหรับระบบ typography และ spacing ในเว็บไซต์ ทำให้การใช้งาน `rem` units มีประสิทธิภาพและคาดเดาได้

### แนวคิดพื้นฐาน

```css
/* การตั้งฐาน HTML Font-Size */
html {
  font-size: 16px; /* ฐานหลักของระบบ typography */
}

/* REM คำนวณจาก HTML font-size */
.example {
  font-size: 1rem; /* = 16px */
  font-size: 1.5rem; /* = 24px */
  font-size: 2rem; /* = 32px */
  font-size: 0.875rem; /* = 14px */
}

/* ทุกอย่างในระบบจะสัมพันธ์กับฐานนี้ */
.component {
  font-size: 1rem; /* 16px */
  padding: 1rem; /* 16px */
  margin: 0.5rem; /* 8px */
  border-radius: 0.25rem; /* 4px */
}
```

## 1. การตั้งค่า HTML Font-Size Base

### Browser Default vs Custom Base

```css
/* Browser default (ส่วนใหญ่ 16px) */
html {
  /* ไม่ตั้งค่าอะไร = ใช้ browser default */
  /* font-size: 16px; (โดยปกติ) */
}

/* Custom base ที่แนะนำ */
html {
  font-size: 16px; /* กำหนดชัดเจนเพื่อความแน่นอน */
}

/* Alternative: ใช้ percentage */
html {
  font-size: 100%; /* = browser default (มักจะ 16px) */
}

/* Flexible base */
html {
  font-size: 1rem; /* = browser default แต่ยังคง user preferences */
}
```

### ทำไมควรใช้ 16px เป็นฐาน

```css
/* 🎯 เหตุผลที่ควรใช้ 16px */
html {
  font-size: 16px;
}

/* 1. Standard web typography size */
/* 2. Good readability on most devices */
/* 3. Accessibility compliant */
/* 4. Easy math calculations */

/* การคำนวณที่ง่าย */
.easy-math {
  font-size: 1rem; /* 16px */
  font-size: 1.25rem; /* 20px (16 * 1.25) */
  font-size: 1.5rem; /* 24px (16 * 1.5) */
  font-size: 0.75rem; /* 12px (16 * 0.75) */
  font-size: 0.875rem; /* 14px (16 * 0.875) */
}

/* Typography scale ที่สวยงาม */
.beautiful-scale {
  /* Base */
  font-size: 1rem; /* 16px */

  /* Larger sizes */
  font-size: 1.125rem; /* 18px */
  font-size: 1.25rem; /* 20px */
  font-size: 1.5rem; /* 24px */
  font-size: 1.75rem; /* 28px */
  font-size: 2rem; /* 32px */

  /* Smaller sizes */
  font-size: 0.875rem; /* 14px */
  font-size: 0.75rem; /* 12px */
}
```

## 2. สร้างระบบ Typography ด้วย REM

### Typography Scale System

```css
/* Root font-size setting */
html {
  font-size: 16px; /* Base foundation */
}

/* Typography scale variables */
:root {
  /* Font sizes */
  --font-xs: 0.75rem; /* 12px */
  --font-sm: 0.875rem; /* 14px */
  --font-base: 1rem; /* 16px */
  --font-lg: 1.125rem; /* 18px */
  --font-xl: 1.25rem; /* 20px */
  --font-2xl: 1.5rem; /* 24px */
  --font-3xl: 1.875rem; /* 30px */
  --font-4xl: 2.25rem; /* 36px */
  --font-5xl: 3rem; /* 48px */
  --font-6xl: 3.75rem; /* 60px */
  --font-7xl: 4.5rem; /* 72px */
  --font-8xl: 6rem; /* 96px */
  --font-9xl: 8rem; /* 128px */
}

/* Semantic typography */
.typography-system {
  /* Display text */
  .text-display-1 {
    font-size: var(--font-9xl);
    font-weight: 900;
  }
  .text-display-2 {
    font-size: var(--font-8xl);
    font-weight: 800;
  }
  .text-display-3 {
    font-size: var(--font-7xl);
    font-weight: 700;
  }

  /* Headings */
  .text-h1 {
    font-size: var(--font-6xl);
    font-weight: 700;
  }
  .text-h2 {
    font-size: var(--font-5xl);
    font-weight: 600;
  }
  .text-h3 {
    font-size: var(--font-4xl);
    font-weight: 600;
  }
  .text-h4 {
    font-size: var(--font-3xl);
    font-weight: 500;
  }
  .text-h5 {
    font-size: var(--font-2xl);
    font-weight: 500;
  }
  .text-h6 {
    font-size: var(--font-xl);
    font-weight: 500;
  }

  /* Body text */
  .text-lead {
    font-size: var(--font-lg);
    font-weight: 400;
  }
  .text-body {
    font-size: var(--font-base);
    font-weight: 400;
  }
  .text-small {
    font-size: var(--font-sm);
    font-weight: 400;
  }
  .text-caption {
    font-size: var(--font-xs);
    font-weight: 400;
  }
}

/* HTML semantic elements */
h1 {
  font-size: var(--font-6xl);
  font-weight: 700;
  line-height: 1.1;
}
h2 {
  font-size: var(--font-5xl);
  font-weight: 600;
  line-height: 1.2;
}
h3 {
  font-size: var(--font-4xl);
  font-weight: 600;
  line-height: 1.3;
}
h4 {
  font-size: var(--font-3xl);
  font-weight: 500;
  line-height: 1.4;
}
h5 {
  font-size: var(--font-2xl);
  font-weight: 500;
  line-height: 1.5;
}
h6 {
  font-size: var(--font-xl);
  font-weight: 500;
  line-height: 1.5;
}

p {
  font-size: var(--font-base);
  line-height: 1.6;
}
small {
  font-size: var(--font-sm);
  line-height: 1.5;
}
```

### Spacing System ที่สัมพันธ์กัน

```css
/* Spacing scale based on typography */
:root {
  /* Base spacing unit = base font size */
  --space-base: 1rem; /* 16px */

  /* Spacing scale */
  --space-0: 0;
  --space-1: 0.25rem; /* 4px */
  --space-2: 0.5rem; /* 8px */
  --space-3: 0.75rem; /* 12px */
  --space-4: 1rem; /* 16px = base */
  --space-5: 1.25rem; /* 20px */
  --space-6: 1.5rem; /* 24px */
  --space-8: 2rem; /* 32px */
  --space-10: 2.5rem; /* 40px */
  --space-12: 3rem; /* 48px */
  --space-16: 4rem; /* 64px */
  --space-20: 5rem; /* 80px */
  --space-24: 6rem; /* 96px */
  --space-32: 8rem; /* 128px */
  --space-40: 10rem; /* 160px */
  --space-48: 12rem; /* 192px */
  --space-56: 14rem; /* 224px */
  --space-64: 16rem; /* 256px */
}

/* Component spacing */
.spacing-system {
  /* Small components */
  .btn-sm {
    padding: var(--space-2) var(--space-3);
  }
  .btn {
    padding: var(--space-3) var(--space-4);
  }
  .btn-lg {
    padding: var(--space-4) var(--space-6);
  }

  /* Cards */
  .card-sm {
    padding: var(--space-4);
  }
  .card {
    padding: var(--space-6);
  }
  .card-lg {
    padding: var(--space-8);
  }

  /* Sections */
  .section-sm {
    padding: var(--space-8) 0;
  }
  .section {
    padding: var(--space-16) 0;
  }
  .section-lg {
    padding: var(--space-24) 0;
  }

  /* Margins */
  .mb-1 {
    margin-bottom: var(--space-1);
  }
  .mb-2 {
    margin-bottom: var(--space-2);
  }
  .mb-4 {
    margin-bottom: var(--space-4);
  }
  .mb-6 {
    margin-bottom: var(--space-6);
  }
  .mb-8 {
    margin-bottom: var(--space-8);
  }
}
```

## 3. Responsive Typography System

### Mobile-First Responsive Scaling

```css
/* Base setup */
html {
  font-size: 16px; /* Default base */
}

/* Mobile adjustments */
@media (max-width: 640px) {
  html {
    font-size: 14px; /* เล็กลงสำหรับ mobile */
  }

  /* ทุก rem จะปรับตามอัตโนมัติ */
  /* 1rem = 14px แทน 16px */
}

/* Tablet adjustments */
@media (min-width: 641px) and (max-width: 1024px) {
  html {
    font-size: 15px; /* ปานกลางสำหรับ tablet */
  }
}

/* Desktop normal */
@media (min-width: 1025px) {
  html {
    font-size: 16px; /* ขนาดปกติ */
  }
}

/* Large desktop */
@media (min-width: 1440px) {
  html {
    font-size: 18px; /* ใหญ่ขึ้นสำหรับ large screens */
  }
}

/* Extra large displays */
@media (min-width: 1920px) {
  html {
    font-size: 20px; /* ใหญ่สุดสำหรับ 4K displays */
  }
}
```

### Alternative: Fluid Typography

```css
/* Fluid base font-size */
html {
  font-size: clamp(14px, 4vw, 20px);
  /* ขั้นต่ำ 14px, ปรับตาม viewport, สูงสุด 20px */
}

/* Components จะปรับตามอัตโนมัติ */
.fluid-component {
  font-size: 1rem; /* ปรับตาม base */
  padding: 1rem 1.5rem; /* ปรับตาม base */
  margin-bottom: 2rem; /* ปรับตาม base */
  border-radius: 0.5rem; /* ปรับตาม base */
}

/* Mixed approach: Fluid + Breakpoints */
html {
  font-size: 16px; /* Default */
}

@media (max-width: 480px) {
  html {
    font-size: clamp(12px, 3.5vw, 14px);
  }
}

@media (min-width: 1200px) {
  html {
    font-size: clamp(16px, 1.5vw, 20px);
  }
}
```

## 4. Component System ด้วย REM

### Button System

```css
/* Button base */
.btn {
  /* Typography */
  font-size: 1rem; /* 16px */
  font-weight: 500;
  line-height: 1.5;

  /* Spacing */
  padding: 0.75rem 1.5rem; /* 12px 24px */

  /* Visual */
  border: 1px solid transparent;
  border-radius: 0.375rem; /* 6px */

  /* Transitions */
  transition: all 0.2s ease;
}

/* Button sizes */
.btn-xs {
  font-size: 0.75rem; /* 12px */
  padding: 0.375rem 0.75rem; /* 6px 12px */
  border-radius: 0.25rem; /* 4px */
}

.btn-sm {
  font-size: 0.875rem; /* 14px */
  padding: 0.5rem 1rem; /* 8px 16px */
  border-radius: 0.25rem; /* 4px */
}

.btn-lg {
  font-size: 1.125rem; /* 18px */
  padding: 1rem 2rem; /* 16px 32px */
  border-radius: 0.5rem; /* 8px */
}

.btn-xl {
  font-size: 1.25rem; /* 20px */
  padding: 1.25rem 2.5rem; /* 20px 40px */
  border-radius: 0.75rem; /* 12px */
}
```

### Card System

```css
/* Card base */
.card {
  /* Spacing */
  padding: 1.5rem; /* 24px */
  margin-bottom: 2rem; /* 32px */

  /* Visual */
  background: white;
  border: 1px solid #e5e7eb;
  border-radius: 0.5rem; /* 8px */
  box-shadow: 0 0.25rem 0.75rem rgba(0, 0, 0, 0.1);
}

.card-header {
  padding: 1rem 1.5rem; /* 16px 24px */
  margin: -1.5rem -1.5rem 1rem;
  border-bottom: 1px solid #e5e7eb;
  border-radius: 0.5rem 0.5rem 0 0;
}

.card-title {
  font-size: 1.25rem; /* 20px */
  font-weight: 600;
  margin-bottom: 0.5rem; /* 8px */
}

.card-content {
  font-size: 1rem; /* 16px */
  line-height: 1.6;
  margin-bottom: 1rem; /* 16px */
}

.card-footer {
  padding: 1rem 1.5rem; /* 16px 24px */
  margin: 1rem -1.5rem -1.5rem;
  border-top: 1px solid #e5e7eb;
  border-radius: 0 0 0.5rem 0.5rem;
}

/* Card sizes */
.card-sm {
  padding: 1rem; /* 16px */

  .card-title {
    font-size: 1.125rem; /* 18px */
  }
}

.card-lg {
  padding: 2rem; /* 32px */

  .card-title {
    font-size: 1.5rem; /* 24px */
  }
}
```

### Form System

```css
/* Form base */
.form-group {
  margin-bottom: 1.5rem; /* 24px */
}

.form-label {
  display: block;
  font-size: 0.875rem; /* 14px */
  font-weight: 500;
  margin-bottom: 0.5rem; /* 8px */
  color: #374151;
}

.form-input {
  /* Typography */
  font-size: 1rem; /* 16px */
  line-height: 1.5;

  /* Spacing */
  padding: 0.75rem 1rem; /* 12px 16px */
  width: 100%;

  /* Visual */
  background: white;
  border: 1px solid #d1d5db;
  border-radius: 0.375rem; /* 6px */

  /* States */
  transition: border-color 0.2s ease, box-shadow 0.2s ease;
}

.form-input:focus {
  outline: none;
  border-color: #3b82f6;
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
}

/* Input sizes */
.form-input-sm {
  font-size: 0.875rem; /* 14px */
  padding: 0.5rem 0.75rem; /* 8px 12px */
  border-radius: 0.25rem; /* 4px */
}

.form-input-lg {
  font-size: 1.125rem; /* 18px */
  padding: 1rem 1.25rem; /* 16px 20px */
  border-radius: 0.5rem; /* 8px */
}

/* Help text */
.form-help {
  font-size: 0.75rem; /* 12px */
  color: #6b7280;
  margin-top: 0.25rem; /* 4px */
}

/* Error states */
.form-error {
  color: #ef4444;
  font-size: 0.75rem; /* 12px */
  margin-top: 0.25rem; /* 4px */
}

.form-input.error {
  border-color: #ef4444;
  box-shadow: 0 0 0 3px rgba(239, 68, 68, 0.1);
}
```

## 5. Layout System ด้วย REM

### Container System

```css
/* Container base */
.container {
  width: 100%;
  margin: 0 auto;
  padding: 0 1rem; /* 16px horizontal padding */
  max-width: 75rem; /* 1200px max width */
}

/* Container sizes */
.container-sm {
  max-width: 40rem; /* 640px */
}

.container-md {
  max-width: 48rem; /* 768px */
}

.container-lg {
  max-width: 64rem; /* 1024px */
}

.container-xl {
  max-width: 80rem; /* 1280px */
}

.container-2xl {
  max-width: 96rem; /* 1536px */
}

/* Responsive containers */
@media (min-width: 640px) {
  .container {
    padding: 0 1.5rem; /* 24px */
  }
}

@media (min-width: 1024px) {
  .container {
    padding: 0 2rem; /* 32px */
  }
}
```

### Grid System

```css
/* Grid base */
.grid {
  display: grid;
  gap: 1.5rem; /* 24px */
}

/* Grid columns */
.grid-cols-1 {
  grid-template-columns: repeat(1, 1fr);
}
.grid-cols-2 {
  grid-template-columns: repeat(2, 1fr);
}
.grid-cols-3 {
  grid-template-columns: repeat(3, 1fr);
}
.grid-cols-4 {
  grid-template-columns: repeat(4, 1fr);
}
.grid-cols-6 {
  grid-template-columns: repeat(6, 1fr);
}
.grid-cols-12 {
  grid-template-columns: repeat(12, 1fr);
}

/* Gap sizes */
.gap-1 {
  gap: 0.25rem;
} /* 4px */
.gap-2 {
  gap: 0.5rem;
} /* 8px */
.gap-4 {
  gap: 1rem;
} /* 16px */
.gap-6 {
  gap: 1.5rem;
} /* 24px */
.gap-8 {
  gap: 2rem;
} /* 32px */

/* Responsive grid */
@media (max-width: 640px) {
  .grid-cols-2,
  .grid-cols-3,
  .grid-cols-4,
  .grid-cols-6,
  .grid-cols-12 {
    grid-template-columns: 1fr;
  }
}

@media (min-width: 641px) and (max-width: 1024px) {
  .grid-cols-3,
  .grid-cols-4,
  .grid-cols-6,
  .grid-cols-12 {
    grid-template-columns: repeat(2, 1fr);
  }
}
```

## 6. Advanced REM Techniques

### Dynamic Scaling System

```css
/* CSS Custom Properties for dynamic scaling */
:root {
  --scale-factor: 1;
  --base-font-size: calc(16px * var(--scale-factor));
}

html {
  font-size: var(--base-font-size);
}

/* JavaScript controlled scaling */
/*
document.documentElement.style.setProperty('--scale-factor', '1.2');
*/

/* Conditional scaling */
.large-text-mode {
  --scale-factor: 1.25;
}

.compact-mode {
  --scale-factor: 0.875;
}

/* High contrast mode */
@media (prefers-contrast: high) {
  :root {
    --scale-factor: 1.1;
  }
}
```

### Theme-Based Scaling

```css
/* Light theme */
[data-theme='light'] {
  --base-font-size: 16px;
}

/* Dark theme - slightly larger for readability */
[data-theme='dark'] {
  --base-font-size: 17px;
}

/* Print styles */
@media print {
  html {
    font-size: 12pt; /* Print points instead of pixels */
  }
}

/* High DPI displays */
@media (-webkit-min-device-pixel-ratio: 2) {
  html {
    font-size: 15px; /* Slightly smaller on high DPI */
  }
}
```

## 7. Debugging และ Tools

### Visual Debugging

```css
/* Debug typography system */
.debug-typography * {
  outline: 1px solid rgba(255, 0, 0, 0.3);
  position: relative;
}

.debug-typography *::before {
  content: attr(class) ' | ' attr(data-font-size);
  position: absolute;
  top: -1.5rem;
  left: 0;
  font-size: 0.75rem;
  background: rgba(255, 0, 0, 0.8);
  color: white;
  padding: 0.25rem;
  border-radius: 0.25rem;
  white-space: nowrap;
  z-index: 1000;
}

/* Show current font-size */
.show-font-size::after {
  content: 'Font: ' attr(data-computed-font-size);
  display: block;
  font-size: 0.75rem;
  color: #666;
  margin-top: 0.25rem;
}

/* Grid overlay */
.debug-grid {
  background-image: linear-gradient(rgba(255, 0, 0, 0.1) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 0, 0, 0.1) 1px, transparent 1px);
  background-size: 1rem 1rem; /* 16px grid based on base font-size */
}
```

### Development Utilities

```css
/* Quick size reference */
.size-reference {
  position: fixed;
  top: 1rem;
  right: 1rem;
  background: rgba(0, 0, 0, 0.8);
  color: white;
  padding: 1rem;
  border-radius: 0.5rem;
  font-size: 0.75rem;
  z-index: 9999;
}

.size-reference::before {
  content: 'Base: ' var(--base-font-size, '16px') '\A''1rem = ' var(
      --base-font-size,
      '16px'
    )
    '\A''0.5rem = ' calc(var(--base-font-size, 16px) * 0.5) '\A''2rem = ' calc(
      var(--base-font-size, 16px) * 2
    );
  white-space: pre;
  line-height: 1.4;
}
```

## 8. Best Practices Summary

### DO's ✅

```css
/* ✅ ตั้งฐาน HTML font-size ชัดเจน */
html {
  font-size: 16px;
}

/* ✅ ใช้ rem สำหรับ font-size */
.component {
  font-size: 1rem;
}

/* ✅ ใช้ rem สำหรับ spacing ที่สอดคล้อง */
.component {
  padding: 1rem;
  margin: 1rem 0;
}

/* ✅ สร้าง scale system */
:root {
  --font-sm: 0.875rem;
  --font-base: 1rem;
  --font-lg: 1.125rem;
}

/* ✅ Responsive scaling */
@media (max-width: 640px) {
  html {
    font-size: 14px;
  }
}
```

### DON'Ts ❌

```css
/* ❌ ไม่ตั้งฐาน HTML font-size */
/* html { } */

/* ❌ ผสม units แบบไม่มีระบบ */
.bad-component {
  font-size: 18px; /* px */
  padding: 1.5em; /* em */
  margin: 2rem; /* rem */
  width: 300px; /* px */
}

/* ❌ ใช้ arbitrary values */
.arbitrary {
  font-size: 1.234rem; /* ไม่อยู่ในระบบ */
  padding: 0.789rem; /* ค่าที่แปลก */
}

/* ❌ ลืม responsive considerations */
.non-responsive {
  font-size: 3rem; /* ใหญ่เกินไปใน mobile */
}
```

### Quick Setup Template

```css
/* Complete REM system setup template */

/* 1. Base setup */
html {
  font-size: 16px;
  line-height: 1.5;
}

/* 2. Typography scale */
:root {
  --font-xs: 0.75rem;
  --font-sm: 0.875rem;
  --font-base: 1rem;
  --font-lg: 1.125rem;
  --font-xl: 1.25rem;
  --font-2xl: 1.5rem;
  --font-3xl: 1.875rem;
  --font-4xl: 2.25rem;
}

/* 3. Spacing scale */
:root {
  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-4: 1rem;
  --space-6: 1.5rem;
  --space-8: 2rem;
  --space-12: 3rem;
  --space-16: 4rem;
}

/* 4. Responsive scaling */
@media (max-width: 640px) {
  html {
    font-size: 14px;
  }
}

@media (min-width: 1200px) {
  html {
    font-size: 18px;
  }
}

/* 5. Component base */
body {
  font-size: var(--font-base);
  line-height: 1.6;
  margin: 0;
  padding: 0;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  margin: 0 0 var(--space-4) 0;
  line-height: 1.2;
}

p {
  margin: 0 0 var(--space-4) 0;
}
```

การตั้งฐาน HTML font-size และใช้ระบบ REM อย่างถูกต้องจะทำให้เว็บไซต์มีความสอดคล้อง อ่านง่าย และตอบสนองได้ดี!
