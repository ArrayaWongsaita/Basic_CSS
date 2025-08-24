# Contrast และ Accessibility: คู่มือเบื้องต้น

## ภาพรวม Contrast ในการออกแบบเว็บ

Contrast (ความคมชัด) คือความแตกต่างระหว่างสีข้อความและสีพื้นหลัง ซึ่งเป็นปัจจัยสำคัญในการทำให้เนื้อหาอ่านง่ายและเข้าถึงได้สำหรับผู้ใช้ทุกคน

### ทำไม Contrast ถึงสำคัญ

```css
/* ❌ Contrast ต่ำ - อ่านยาก */
.poor-contrast {
  color: #cccccc; /* สีอ่อน */
  background-color: #ffffff; /* พื้นขาว */
  /* Contrast ratio: 1.6:1 (ไม่ผ่านมาตรฐาน) */
}

/* ✅ Contrast สูง - อ่านง่าย */
.good-contrast {
  color: #333333; /* สีเข้ม */
  background-color: #ffffff; /* พื้นขาว */
  /* Contrast ratio: 12.6:1 (ผ่านมาตรฐาน AAA) */
}

/* ✅ Alternative combinations */
.excellent-contrast {
  color: #000000; /* สีดำ */
  background-color: #ffffff; /* พื้นขาว */
  /* Contrast ratio: 21:1 (สูงสุด) */
}

.dark-theme {
  color: #ffffff; /* สีขาว */
  background-color: #1a1a1a; /* พื้นเข้ม */
  /* Contrast ratio: 18.5:1 (ดีมาก) */
}
```

## 1. WCAG Guidelines และมาตรฐาน

### WCAG Contrast Standards

```css
/* WCAG 2.1 Level AA (ขั้นต่ำที่แนะนำ) */
.wcag-aa-normal {
  /* Normal text: ต้องมี contrast ratio อย่างน้อย 4.5:1 */
  color: #595959; /* 4.54:1 ratio */
  background-color: #ffffff;
  font-size: 1rem;
}

.wcag-aa-large {
  /* Large text (18pt+/14pt+ bold): ต้องมี contrast ratio อย่างน้อย 3:1 */
  color: #767676; /* 3.05:1 ratio */
  background-color: #ffffff;
  font-size: 1.125rem; /* 18px */
  font-weight: bold;
}

/* WCAG 2.1 Level AAA (มาตรฐานสูง) */
.wcag-aaa-normal {
  /* Normal text: ต้องมี contrast ratio อย่างน้อย 7:1 */
  color: #4a4a4a; /* 7.95:1 ratio */
  background-color: #ffffff;
  font-size: 1rem;
}

.wcag-aaa-large {
  /* Large text: ต้องมี contrast ratio อย่างน้อย 4.5:1 */
  color: #595959; /* 4.54:1 ratio */
  background-color: #ffffff;
  font-size: 1.125rem;
  font-weight: bold;
}
```

### ตัวอย่างการคำนวณ Contrast Ratio

```css
/* การคำนวณ Contrast Ratio */
/* Formula: (L1 + 0.05) / (L2 + 0.05) */
/* L1 = สีที่สว่างกว่า, L2 = สีที่เข้มกว่า */

/* ตัวอย่างการประยุกต์ใช้ */
:root {
  /* สีที่ผ่านมาตรฐาน WCAG AA */
  --text-primary: #1f2937; /* 15.3:1 บนพื้นขาว */
  --text-secondary: #4b5563; /* 7.04:1 บนพื้นขาว */
  --text-muted: #6b7280; /* 4.76:1 บนพื้นขาว */

  /* สีพื้นหลัง */
  --bg-white: #ffffff;
  --bg-gray-50: #f9fafb;
  --bg-gray-100: #f3f4f6;

  /* สีสำหรับ dark theme */
  --dark-text-primary: #f9fafb; /* 18.7:1 บนพื้นเข้ม */
  --dark-text-secondary: #d1d5db; /* 11.2:1 บนพื้นเข้ม */
  --dark-bg: #111827;
}

/* การใช้งานสีที่ผ่านมาตรฐาน */
.text-system {
  .text-primary {
    color: var(--text-primary);
    background-color: var(--bg-white);
  }

  .text-secondary {
    color: var(--text-secondary);
    background-color: var(--bg-white);
  }

  .text-muted {
    color: var(--text-muted);
    background-color: var(--bg-white);
  }
}

/* Dark theme */
[data-theme='dark'] {
  .text-primary {
    color: var(--dark-text-primary);
    background-color: var(--dark-bg);
  }

  .text-secondary {
    color: var(--dark-text-secondary);
    background-color: var(--dark-bg);
  }
}
```

## 2. สีที่เหมาะสมสำหรับ Accessibility

### Gray Scale Palette

```css
/* Gray scale ที่ผ่านมาตรฐาน accessibility */
:root {
  /* Light theme grays */
  --gray-50: #f9fafb; /* พื้นหลังอ่อนมาก */
  --gray-100: #f3f4f6; /* พื้นหลังอ่อน */
  --gray-200: #e5e7eb; /* Border อ่อน */
  --gray-300: #d1d5db; /* Border ปกติ */
  --gray-400: #9ca3af; /* ข้อความรอง (3.05:1) */
  --gray-500: #6b7280; /* ข้อความปกติ (4.76:1) */
  --gray-600: #4b5563; /* ข้อความหลัก (7.04:1) */
  --gray-700: #374151; /* ข้อความเข้ม (9.73:1) */
  --gray-800: #1f2937; /* ข้อความเข้มมาก (15.3:1) */
  --gray-900: #111827; /* สีเข้มสุด (18.7:1) */
}

/* การใช้งาน */
.accessibility-text {
  .heading {
    color: var(--gray-900);
    background: white;
  }

  .body-text {
    color: var(--gray-700);
    background: white;
  }

  .secondary-text {
    color: var(--gray-600);
    background: white;
  }

  .muted-text {
    color: var(--gray-500);
    background: white;
    font-size: 1.125rem; /* ขนาดใหญ่ขึ้นเพื่อชดเชย contrast ที่ต่ำ */
  }
}
```

### Brand Colors ที่ปลอดภัย

```css
/* Brand colors ที่ผ่านมาตรฐาน accessibility */
:root {
  /* Blue palette */
  --blue-50: #eff6ff;
  --blue-100: #dbeafe;
  --blue-600: #2563eb; /* 5.14:1 บนพื้นขาว */
  --blue-700: #1d4ed8; /* 7.0:1 บนพื้นขาว */
  --blue-800: #1e40af; /* 9.68:1 บนพื้นขาว */
  --blue-900: #1e3a8a; /* 12.04:1 บนพื้นขาว */

  /* Green palette */
  --green-600: #16a34a; /* 4.89:1 บนพื้นขาว */
  --green-700: #15803d; /* 6.93:1 บนพื้นขาว */
  --green-800: #166534; /* 9.35:1 บนพื้นขาว */

  /* Red palette */
  --red-600: #dc2626; /* 5.87:1 บนพื้นขาว */
  --red-700: #b91c1c; /* 7.73:1 บนพื้นขาว */
  --red-800: #991b1b; /* 9.74:1 บนพื้นขาว */
}

/* Semantic colors */
.semantic-colors {
  .success {
    color: var(--green-700);
    background: var(--green-50);
    border: 1px solid var(--green-200);
  }

  .warning {
    color: #b45309; /* 7.48:1 บนพื้นเหลือง */
    background: #fef3c7;
    border: 1px solid #fde68a;
  }

  .error {
    color: var(--red-700);
    background: #fef2f2;
    border: 1px solid #fecaca;
  }

  .info {
    color: var(--blue-700);
    background: var(--blue-50);
    border: 1px solid var(--blue-200);
  }
}
```

## 3. การทดสอบ Contrast

### CSS สำหรับการทดสอบ

```css
/* ตัวอย่างการทดสอบ contrast */
.contrast-test {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1rem;
  padding: 2rem;
}

.contrast-sample {
  padding: 1rem;
  border-radius: 0.5rem;
  border: 1px solid #e5e7eb;
  text-align: center;
}

/* ตัวอย่างที่ผ่านมาตรฐาน */
.pass-aa {
  color: #374151;
  background: white;
}

.pass-aa::after {
  content: '✅ AA: 9.73:1';
  display: block;
  font-size: 0.75rem;
  margin-top: 0.5rem;
  color: #059669;
}

.pass-aaa {
  color: #1f2937;
  background: white;
}

.pass-aaa::after {
  content: '✅ AAA: 15.3:1';
  display: block;
  font-size: 0.75rem;
  margin-top: 0.5rem;
  color: #059669;
}

/* ตัวอย่างที่ไม่ผ่านมาตรฐาน */
.fail-contrast {
  color: #d1d5db;
  background: white;
}

.fail-contrast::after {
  content: '❌ Fail: 1.84:1';
  display: block;
  font-size: 0.75rem;
  margin-top: 0.5rem;
  color: #dc2626;
}

/* Large text variations */
.large-text {
  font-size: 1.125rem;
  font-weight: bold;
}

.large-text-aa {
  color: #6b7280;
  background: white;
}

.large-text-aa::after {
  content: '✅ Large AA: 4.76:1';
  display: block;
  font-size: 0.75rem;
  margin-top: 0.5rem;
  color: #059669;
}
```

### Tools และ Techniques

```css
/* CSS สำหรับ debug contrast */
.debug-contrast {
  position: relative;
}

.debug-contrast::before {
  content: attr(data-contrast-ratio);
  position: absolute;
  top: -1.5rem;
  left: 0;
  font-size: 0.75rem;
  padding: 0.25rem 0.5rem;
  background: rgba(0, 0, 0, 0.8);
  color: white;
  border-radius: 0.25rem;
  white-space: nowrap;
  z-index: 100;
}

/* Highlight accessibility issues */
.contrast-warning {
  outline: 2px solid #f59e0b;
  outline-offset: 2px;
}

.contrast-error {
  outline: 2px solid #dc2626;
  outline-offset: 2px;
}

/* Alternative text for images */
img:not([alt]),
img[alt=''] {
  outline: 3px solid #dc2626;
}

img:not([alt])::after,
img[alt='']::after {
  content: 'Missing alt text';
  position: absolute;
  background: #dc2626;
  color: white;
  padding: 0.25rem;
  font-size: 0.75rem;
}
```

## 4. Dark Theme และ Contrast

### Dark Theme Best Practices

```css
/* Dark theme color system */
[data-theme='dark'] {
  /* Background colors */
  --bg-primary: #0f172a;
  --bg-secondary: #1e293b;
  --bg-tertiary: #334155;

  /* Text colors with proper contrast */
  --text-primary: #f1f5f9; /* 16.2:1 */
  --text-secondary: #cbd5e1; /* 9.85:1 */
  --text-muted: #94a3b8; /* 5.74:1 */

  /* Border colors */
  --border-primary: #475569;
  --border-secondary: #64748b;
}

/* Dark theme components */
[data-theme='dark'] .card {
  background: var(--bg-secondary);
  color: var(--text-primary);
  border: 1px solid var(--border-primary);
}

[data-theme='dark'] .text-muted {
  color: var(--text-muted);
  /* ใน dark theme อาจต้องทำให้ใหญ่ขึ้นเพื่อความชัดเจน */
  font-size: 1.0625rem;
}

/* Button contrast ใน dark theme */
[data-theme='dark'] .btn-primary {
  background: #3b82f6;
  color: white;
  /* Blue 500 มี contrast 3.54:1 กับ dark background */
  /* แต่ปลอดภัยเพราะใช้ white text */
}

[data-theme='dark'] .btn-secondary {
  background: var(--bg-tertiary);
  color: var(--text-primary);
  border: 1px solid var(--border-secondary);
}
```

### High Contrast Mode

```css
/* High contrast mode support */
@media (prefers-contrast: high) {
  :root {
    --text-primary: #000000;
    --text-secondary: #000000;
    --bg-primary: #ffffff;
    --border-primary: #000000;
  }

  .btn {
    border: 2px solid;
  }

  .card {
    border: 2px solid;
  }

  /* Remove subtle effects ใน high contrast mode */
  .shadow {
    box-shadow: none;
  }

  .gradient {
    background: var(--bg-primary);
  }
}

/* Forced colors mode (Windows High Contrast) */
@media (forced-colors: active) {
  .custom-colors {
    color: CanvasText;
    background: Canvas;
    border-color: ButtonText;
  }

  .btn {
    color: ButtonText;
    background: ButtonFace;
    border: 1px solid ButtonText;
  }

  .btn:focus,
  .btn:hover {
    color: HighlightText;
    background: Highlight;
  }
}
```

## 5. Practical Examples

### Form Accessibility

```css
/* Form contrast best practices */
.form-accessible {
  .form-label {
    color: #374151; /* 9.73:1 ratio */
    font-weight: 500;
    margin-bottom: 0.5rem;
  }

  .form-input {
    color: #1f2937; /* 15.3:1 ratio */
    background: white;
    border: 1px solid #d1d5db;
    padding: 0.75rem 1rem;
    border-radius: 0.375rem;
  }

  .form-input:focus {
    outline: 2px solid #3b82f6;
    outline-offset: 2px;
    border-color: #3b82f6;
  }

  .form-error {
    color: #b91c1c; /* 7.73:1 ratio */
    font-size: 0.875rem;
    margin-top: 0.25rem;
  }

  .form-help {
    color: #4b5563; /* 7.04:1 ratio */
    font-size: 0.875rem;
    margin-top: 0.25rem;
  }
}

/* Required field indicators */
.required::after {
  content: ' *';
  color: #dc2626;
  font-weight: bold;
}

/* Focus indicators */
.form-input:focus,
.btn:focus,
a:focus {
  outline: 2px solid #3b82f6;
  outline-offset: 2px;
}
```

### Navigation Accessibility

```css
/* Navigation with proper contrast */
.nav-accessible {
  background: white;
  border-bottom: 1px solid #e5e7eb;
}

.nav-link {
  color: #374151; /* 9.73:1 ratio */
  text-decoration: none;
  padding: 1rem 1.5rem;
  display: block;
  transition: all 0.2s ease;
}

.nav-link:hover {
  color: #1f2937; /* 15.3:1 ratio */
  background: #f9fafb;
}

.nav-link:focus {
  outline: 2px solid #3b82f6;
  outline-offset: -2px;
  background: #eff6ff;
}

.nav-link.active {
  color: #1d4ed8; /* 7.0:1 ratio */
  background: #eff6ff;
  font-weight: 500;
}

/* Skip navigation link */
.skip-nav {
  position: absolute;
  top: -40px;
  left: 6px;
  background: #000;
  color: white;
  padding: 8px;
  text-decoration: none;
  border-radius: 0 0 4px 4px;
  z-index: 1000;
}

.skip-nav:focus {
  top: 0;
}
```

## 6. Testing และ Tools

### Manual Testing Checklist

```css
/* Visual testing helpers */
.accessibility-test {
  /* Test different backgrounds */
  .on-white {
    background: white;
  }
  .on-light-gray {
    background: #f9fafb;
  }
  .on-dark-gray {
    background: #374151;
  }
  .on-black {
    background: black;
  }

  /* Test text sizes */
  .normal-text {
    font-size: 1rem;
  }
  .large-text {
    font-size: 1.125rem;
    font-weight: bold;
  }
  .small-text {
    font-size: 0.875rem;
  }

  /* Test different weights */
  .light {
    font-weight: 300;
  }
  .normal {
    font-weight: 400;
  }
  .medium {
    font-weight: 500;
  }
  .bold {
    font-weight: 700;
  }
}

/* Simulation tools */
.simulate-color-blindness {
  /* Protanopia simulation */
  .protanopia {
    filter: url('#protanopia');
  }

  /* Deuteranopia simulation */
  .deuteranopia {
    filter: url('#deuteranopia');
  }

  /* Tritanopia simulation */
  .tritanopia {
    filter: url('#tritanopia');
  }

  /* Grayscale test */
  .grayscale {
    filter: grayscale(100%);
  }
}

/* Browser zoom test */
@media (max-resolution: 1dppx) {
  .zoom-test::before {
    content: 'Test at 200% zoom';
    position: fixed;
    top: 0;
    right: 0;
    background: #dc2626;
    color: white;
    padding: 0.5rem;
    font-size: 0.75rem;
    z-index: 9999;
  }
}
```

### Quick Reference

```css
/* Quick contrast reference */
:root {
  /* Minimum ratios for compliance */
  --min-aa-normal: 4.5; /* Normal text AA */
  --min-aa-large: 3; /* Large text AA */
  --min-aaa-normal: 7; /* Normal text AAA */
  --min-aaa-large: 4.5; /* Large text AAA */

  /* Safe color combinations (on white background) */
  --safe-aa: #767676; /* 3.05:1 - Large text only */
  --safe-aa-normal: #595959; /* 4.54:1 - Normal text AA */
  --safe-aaa: #4a4a4a; /* 7.95:1 - Normal text AAA */
  --safe-perfect: #000000; /* 21:1 - Perfect contrast */
}

/* Usage examples */
.contrast-examples {
  .aa-large-only {
    color: var(--safe-aa);
    font-size: 1.125rem;
    font-weight: bold;
  }

  .aa-compliant {
    color: var(--safe-aa-normal);
  }

  .aaa-compliant {
    color: var(--safe-aaa);
  }

  .perfect-contrast {
    color: var(--safe-perfect);
  }
}
```

## Summary: Best Practices

### 1. Always Test Contrast

- ใช้ tools เช่น WebAIM Contrast Checker
- ทดสอบใน different devices และ lighting conditions
- ตรวจสอบทั้ง normal และ large text

### 2. Follow WCAG Guidelines

- AA level เป็นขั้นต่ำ (4.5:1 normal, 3:1 large)
- AAA level สำหรับ content สำคัญ (7:1 normal, 4.5:1 large)
- Large text = 18pt+ หรือ 14pt+ bold

### 3. Consider All Users

- Color blindness (8% ของผู้ชาย, 0.5% ของผู้หญิง)
- Low vision conditions
- Environmental factors (bright sunlight, etc.)

### 4. Design System Approach

- สร้าง color palette ที่ผ่านมาตรฐาน
- ใช้ CSS custom properties สำหรับ consistency
- Test combinations systematically

การออกแบบที่คำนึงถึง contrast และ accessibility จะทำให้เว็บไซต์ใช้งานได้ดีสำหรับทุกคน!
