# Media Queries & Mobile-First Design: คู่มือการออกแบบ Responsive

## ภาพรวม Media Queries และ Mobile-First

**Media Queries** เป็นเครื่องมือสำคัญใน CSS ที่ช่วยให้เราสร้าง responsive design ได้ โดยสามารถกำหนด styles ที่แตกต่างกันตามขนาดหน้าจอ, ความละเอียด, และ device features อื่นๆ

**Mobile-First Approach** เป็นแนวคิดการออกแบบที่เริ่มจากขนาดหน้าจอเล็กที่สุด (mobile) แล้วค่อยๆ ปรับปรุงไปยังหน้าจอใหญ่ขึ้น (tablet, desktop)

### แนวคิดพื้นฐาน: Mobile-First vs Desktop-First

```css
/* ❌ Desktop-First (เก่า) - เริ่มจากหน้าจอใหญ่ */
.desktop-first {
  /* Base styles สำหรับ desktop */
  width: 1200px;
  display: grid;
  grid-template-columns: 300px 1fr 250px;
  gap: 2rem;
  padding: 2rem;
}

/* ลดขนาดลงไปเรื่อยๆ */
@media (max-width: 1024px) {
  .desktop-first {
    width: 100%;
    grid-template-columns: 250px 1fr;
    padding: 1.5rem;
  }
}

@media (max-width: 768px) {
  .desktop-first {
    grid-template-columns: 1fr;
    padding: 1rem;
  }
}

/* ✅ Mobile-First (แนะนำ) - เริ่มจากหน้าจอเล็ก */
.mobile-first {
  /* Base styles สำหรับ mobile */
  width: 100%;
  display: grid;
  grid-template-columns: 1fr;
  gap: 1rem;
  padding: 1rem;
}

/* ขยายขนาดขึ้นเรื่อยๆ */
@media (min-width: 768px) {
  .mobile-first {
    grid-template-columns: 250px 1fr;
    gap: 1.5rem;
    padding: 1.5rem;
  }
}

@media (min-width: 1024px) {
  .mobile-first {
    grid-template-columns: 300px 1fr 250px;
    gap: 2rem;
    padding: 2rem;
    max-width: 1200px;
    margin: 0 auto;
  }
}
```

## 1. Media Queries Syntax และ Types

### Basic Media Query Syntax

```css
/* Basic syntax */
@media media-type and (condition) {
  /* CSS rules */
}

/* ตัวอย่าง Media Query types */
.media-query-examples {
  /* 1. Screen Media Type */
  @media screen {
    /* Styles สำหรับหน้าจอ */
    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    }
  }

  /* 2. Print Media Type */
  @media print {
    /* Styles สำหรับการพิมพ์ */
    .no-print {
      display: none;
    }
    body {
      color: black;
      background: white;
    }
  }

  /* 3. All Media Types (default) */
  @media all {
    /* Styles สำหรับทุก media */
    * {
      box-sizing: border-box;
    }
  }

  /* 4. Width-based Media Queries */
  @media (max-width: 767px) {
    /* Mobile styles */
    .container {
      padding: 1rem;
    }
  }

  @media (min-width: 768px) {
    /* Tablet and up */
    .container {
      padding: 2rem;
    }
  }

  @media (min-width: 1024px) {
    /* Desktop and up */
    .container {
      max-width: 1200px;
      margin: 0 auto;
    }
  }

  /* 5. Height-based Media Queries */
  @media (max-height: 600px) {
    /* สำหรับหน้าจอเตี้ย */
    .header {
      height: 50px;
    }
  }

  @media (min-height: 800px) {
    /* สำหรับหน้าจอสูง */
    .sidebar {
      position: sticky;
      top: 0;
    }
  }

  /* 6. Orientation Media Queries */
  @media (orientation: portrait) {
    /* Portrait mode */
    .gallery {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media (orientation: landscape) {
    /* Landscape mode */
    .gallery {
      grid-template-columns: repeat(4, 1fr);
    }
  }

  /* 7. Resolution Media Queries */
  @media (min-resolution: 2dppx) {
    /* High DPI displays (Retina) */
    .logo {
      background-image: url('logo@2x.png');
      background-size: 100px 50px;
    }
  }

  /* 8. Hover Support */
  @media (hover: hover) {
    /* Devices ที่รองรับ hover */
    .button:hover {
      background-color: #3b82f6;
      transform: translateY(-2px);
    }
  }

  @media (hover: none) {
    /* Touch devices */
    .button:active {
      background-color: #3b82f6;
    }
  }
}
```

### Advanced Media Query Features

```css
/* Advanced media query features */
.advanced-media-queries {
  /* 1. Combining multiple conditions */
  @media screen and (min-width: 768px) and (max-width: 1023px) {
    /* Tablet only */
    .tablet-only {
      display: block;
    }
  }

  @media screen and (min-width: 768px) and (orientation: landscape) {
    /* Tablet landscape */
    .tablet-landscape {
      grid-template-columns: repeat(3, 1fr);
    }
  }

  /* 2. Using OR logic with comma */
  @media (max-width: 767px), (orientation: portrait) {
    /* Mobile OR portrait orientation */
    .mobile-or-portrait {
      font-size: 1.1rem;
    }
  }

  /* 3. Negation with NOT */
  @media not screen and (max-width: 767px) {
    /* Everything EXCEPT mobile screens */
    .not-mobile {
      display: flex;
    }
  }

  /* 4. Pointer accuracy */
  @media (pointer: coarse) {
    /* Touch screens */
    .touch-target {
      min-height: 44px;
      min-width: 44px;
    }
  }

  @media (pointer: fine) {
    /* Mouse/trackpad */
    .fine-pointer {
      cursor: pointer;
    }
  }

  /* 5. Reduced motion preference */
  @media (prefers-reduced-motion: reduce) {
    /* ผู้ใช้ต้องการลด animation */
    * {
      animation-duration: 0.01ms !important;
      animation-iteration-count: 1 !important;
      transition-duration: 0.01ms !important;
    }
  }

  @media (prefers-reduced-motion: no-preference) {
    /* ผู้ใช้ไม่มีข้อจำกัดเรื่อง animation */
    .animated-element {
      animation: slideIn 0.3s ease-out;
      transition: all 0.3s ease;
    }
  }

  /* 6. Color scheme preference */
  @media (prefers-color-scheme: dark) {
    /* Dark mode */
    :root {
      --bg-color: #1a1a1a;
      --text-color: #ffffff;
      --border-color: #333333;
    }
  }

  @media (prefers-color-scheme: light) {
    /* Light mode */
    :root {
      --bg-color: #ffffff;
      --text-color: #000000;
      --border-color: #e5e5e5;
    }
  }

  /* 7. Contrast preference */
  @media (prefers-contrast: high) {
    /* High contrast */
    .button {
      border: 2px solid currentColor;
      font-weight: bold;
    }
  }

  /* 8. Display mode (PWA) */
  @media (display-mode: standalone) {
    /* เมื่อเป็น PWA */
    .pwa-only {
      display: block;
    }
  }
}
```

## 2. Mobile-First Breakpoints และ Best Practices

### Standard Breakpoint System

```css
/* Standard breakpoint system สำหรับ Mobile-First */
:root {
  /* Breakpoint variables */
  --mobile: 320px;
  --mobile-large: 425px;
  --tablet: 768px;
  --tablet-large: 1024px;
  --desktop: 1200px;
  --desktop-large: 1440px;
  --desktop-xl: 1920px;
}

/* Mobile-First approach */
.responsive-container {
  /* 📱 Mobile (320px+) - Base styles */
  width: 100%;
  padding: 1rem;
  margin: 0 auto;

  /* Layout: Single column */
  display: grid;
  grid-template-columns: 1fr;
  gap: 1rem;

  /* Typography */
  font-size: 1rem;
  line-height: 1.5;

  /* Spacing */
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;
  --spacing-lg: 1.5rem;
}

/* 📱 Large Mobile (425px+) */
@media (min-width: 425px) {
  .responsive-container {
    padding: 1.25rem;
    gap: 1.25rem;
  }
}

/* 📱 Tablet (768px+) */
@media (min-width: 768px) {
  .responsive-container {
    padding: 2rem;
    gap: 2rem;

    /* Layout: Two columns */
    grid-template-columns: 250px 1fr;

    /* Typography */
    font-size: 1.125rem;

    /* Spacing */
    --spacing-sm: 0.75rem;
    --spacing-md: 1.5rem;
    --spacing-lg: 2rem;
  }
}

/* 💻 Large Tablet (1024px+) */
@media (min-width: 1024px) {
  .responsive-container {
    max-width: 1200px;
    padding: 2.5rem;
    gap: 2.5rem;

    /* Layout: Three columns */
    grid-template-columns: 300px 1fr 250px;

    /* Typography */
    font-size: 1.125rem;

    /* Spacing */
    --spacing-sm: 1rem;
    --spacing-md: 2rem;
    --spacing-lg: 3rem;
  }
}

/* 🖥️ Desktop (1200px+) */
@media (min-width: 1200px) {
  .responsive-container {
    max-width: 1400px;
    padding: 3rem;
    gap: 3rem;

    /* Enhanced layout */
    grid-template-columns: 350px 1fr 300px;

    /* Typography */
    font-size: 1.25rem;
  }
}

/* 🖥️ Large Desktop (1440px+) */
@media (min-width: 1440px) {
  .responsive-container {
    max-width: 1600px;
    padding: 4rem;

    /* Wide layout */
    grid-template-columns: 400px 1fr 350px;
  }
}

/* 🖥️ Extra Large Desktop (1920px+) */
@media (min-width: 1920px) {
  .responsive-container {
    max-width: 1800px;

    /* Ultra-wide layout */
    grid-template-columns: 450px 1fr 400px;
  }
}
```

### Mobile-First Component Examples

```css
/* Mobile-First component examples */
.mobile-first-components {
  /* 1. Navigation Component */
  .navigation {
    /* 📱 Mobile: Hamburger menu */
    position: relative;
    background: #1f2937;
    padding: 1rem;
  }

  .nav-toggle {
    display: block;
    background: none;
    border: none;
    color: white;
    font-size: 1.5rem;
    cursor: pointer;
  }

  .nav-menu {
    display: none;
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background: #1f2937;
    padding: 1rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  .nav-menu.active {
    display: block;
  }

  .nav-item {
    display: block;
    color: white;
    text-decoration: none;
    padding: 0.75rem 0;
    border-bottom: 1px solid #374151;
  }

  /* 📱 Tablet: Horizontal menu */
  @media (min-width: 768px) {
    .navigation {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .nav-toggle {
      display: none;
    }

    .nav-menu {
      display: flex;
      position: static;
      background: none;
      padding: 0;
      box-shadow: none;
      gap: 2rem;
    }

    .nav-item {
      border-bottom: none;
      padding: 0.5rem 0;
      transition: color 0.3s;
    }

    .nav-item:hover {
      color: #93c5fd;
    }
  }

  /* 2. Card Grid Component */
  .card-grid {
    /* 📱 Mobile: Single column */
    display: grid;
    grid-template-columns: 1fr;
    gap: 1rem;
    padding: 1rem;
  }

  .card {
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    padding: 1.5rem;
    transition: transform 0.2s, box-shadow 0.2s;
  }

  .card:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
  }

  /* 📱 Large Mobile: Still single column but larger cards */
  @media (min-width: 425px) {
    .card-grid {
      padding: 1.5rem;
      gap: 1.5rem;
    }
  }

  /* 📱 Tablet: Two columns */
  @media (min-width: 768px) {
    .card-grid {
      grid-template-columns: repeat(2, 1fr);
      gap: 2rem;
      padding: 2rem;
    }
  }

  /* 💻 Desktop: Three columns */
  @media (min-width: 1024px) {
    .card-grid {
      grid-template-columns: repeat(3, 1fr);
      gap: 2.5rem;
    }
  }

  /* 🖥️ Large Desktop: Four columns */
  @media (min-width: 1400px) {
    .card-grid {
      grid-template-columns: repeat(4, 1fr);
    }
  }

  /* 3. Hero Section Component */
  .hero {
    /* 📱 Mobile: Stacked layout */
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 2rem 1rem;
    gap: 2rem;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    min-height: 60vh;
  }

  .hero-content {
    max-width: 100%;
  }

  .hero-title {
    font-size: 2rem;
    font-weight: bold;
    margin-bottom: 1rem;
    line-height: 1.2;
  }

  .hero-description {
    font-size: 1rem;
    opacity: 0.9;
    margin-bottom: 2rem;
    line-height: 1.6;
  }

  .hero-cta {
    background: white;
    color: #667eea;
    padding: 1rem 2rem;
    border-radius: 0.5rem;
    text-decoration: none;
    font-weight: 600;
    transition: transform 0.2s;
  }

  .hero-cta:hover {
    transform: translateY(-2px);
  }

  .hero-image {
    max-width: 100%;
    height: auto;
    border-radius: 0.5rem;
  }

  /* 📱 Tablet: Side-by-side layout */
  @media (min-width: 768px) {
    .hero {
      flex-direction: row;
      text-align: left;
      padding: 4rem 2rem;
      gap: 3rem;
      min-height: 70vh;
    }

    .hero-content {
      flex: 1;
      max-width: 50%;
    }

    .hero-title {
      font-size: 2.5rem;
    }

    .hero-description {
      font-size: 1.125rem;
    }

    .hero-image {
      flex: 0 0 40%;
    }
  }

  /* 💻 Desktop: Enhanced layout */
  @media (min-width: 1024px) {
    .hero {
      padding: 6rem 4rem;
      gap: 4rem;
      min-height: 80vh;
    }

    .hero-title {
      font-size: 3rem;
    }

    .hero-description {
      font-size: 1.25rem;
    }
  }

  /* 4. Form Component */
  .form-container {
    /* 📱 Mobile: Single column form */
    max-width: 100%;
    margin: 0 auto;
    padding: 1rem;
  }

  .form-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 1rem;
  }

  .form-group {
    display: flex;
    flex-direction: column;
  }

  .form-label {
    margin-bottom: 0.5rem;
    font-weight: 500;
    color: #374151;
  }

  .form-input {
    padding: 0.75rem;
    border: 1px solid #d1d5db;
    border-radius: 0.375rem;
    font-size: 1rem;
    transition: border-color 0.2s, box-shadow 0.2s;
  }

  .form-input:focus {
    outline: none;
    border-color: #3b82f6;
    box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
  }

  .form-submit {
    background: #3b82f6;
    color: white;
    padding: 1rem 2rem;
    border: none;
    border-radius: 0.375rem;
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;
    transition: background-color 0.2s;
    margin-top: 1rem;
  }

  .form-submit:hover {
    background: #2563eb;
  }

  /* 📱 Tablet: Two-column form */
  @media (min-width: 768px) {
    .form-container {
      max-width: 600px;
      padding: 2rem;
    }

    .form-grid {
      grid-template-columns: repeat(2, 1fr);
      gap: 1.5rem;
    }

    .form-group.full-width {
      grid-column: 1 / -1;
    }
  }

  /* 💻 Desktop: Enhanced form */
  @media (min-width: 1024px) {
    .form-container {
      max-width: 800px;
      padding: 3rem;
    }

    .form-grid {
      gap: 2rem;
    }

    .form-input {
      padding: 1rem;
    }

    .form-submit {
      padding: 1.25rem 3rem;
    }
  }
}
```

## 3. Responsive Typography และ Spacing

### Fluid Typography

```css
/* Responsive typography with Mobile-First */
.responsive-typography {
  /* Base typography for mobile */
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  line-height: 1.6;
  color: #1f2937;

  /* Mobile typography scale */
  --text-xs: 0.75rem; /* 12px */
  --text-sm: 0.875rem; /* 14px */
  --text-base: 1rem; /* 16px */
  --text-lg: 1.125rem; /* 18px */
  --text-xl: 1.25rem; /* 20px */
  --text-2xl: 1.5rem; /* 24px */
  --text-3xl: 1.875rem; /* 30px */
  --text-4xl: 2.25rem; /* 36px */
  --text-5xl: 3rem; /* 48px */

  /* Responsive headings */
  h1 {
    font-size: var(--text-3xl);
    font-weight: 800;
    line-height: 1.2;
    margin-bottom: 1rem;
  }

  h2 {
    font-size: var(--text-2xl);
    font-weight: 700;
    line-height: 1.3;
    margin-bottom: 0.875rem;
  }

  h3 {
    font-size: var(--text-xl);
    font-weight: 600;
    line-height: 1.4;
    margin-bottom: 0.75rem;
  }

  h4 {
    font-size: var(--text-lg);
    font-weight: 600;
    line-height: 1.4;
    margin-bottom: 0.5rem;
  }

  p {
    font-size: var(--text-base);
    margin-bottom: 1rem;
  }

  small {
    font-size: var(--text-sm);
    color: #6b7280;
  }

  /* Tablet typography adjustments */
  @media (min-width: 768px) {
    :root {
      --text-xs: 0.8125rem; /* 13px */
      --text-sm: 0.9375rem; /* 15px */
      --text-base: 1.0625rem; /* 17px */
      --text-lg: 1.1875rem; /* 19px */
      --text-xl: 1.375rem; /* 22px */
      --text-2xl: 1.625rem; /* 26px */
      --text-3xl: 2.125rem; /* 34px */
      --text-4xl: 2.625rem; /* 42px */
      --text-5xl: 3.5rem; /* 56px */
    }

    h1 {
      margin-bottom: 1.25rem;
    }
    h2 {
      margin-bottom: 1rem;
    }
    h3 {
      margin-bottom: 0.875rem;
    }
    p {
      margin-bottom: 1.25rem;
    }
  }

  /* Desktop typography adjustments */
  @media (min-width: 1024px) {
    :root {
      --text-xs: 0.875rem; /* 14px */
      --text-sm: 1rem; /* 16px */
      --text-base: 1.125rem; /* 18px */
      --text-lg: 1.25rem; /* 20px */
      --text-xl: 1.5rem; /* 24px */
      --text-2xl: 1.75rem; /* 28px */
      --text-3xl: 2.5rem; /* 40px */
      --text-4xl: 3rem; /* 48px */
      --text-5xl: 4rem; /* 64px */
    }

    h1 {
      margin-bottom: 1.5rem;
    }
    h2 {
      margin-bottom: 1.25rem;
    }
    h3 {
      margin-bottom: 1rem;
    }
    p {
      margin-bottom: 1.5rem;
    }
  }

  /* Large desktop typography */
  @media (min-width: 1440px) {
    :root {
      --text-5xl: 4.5rem; /* 72px */
      --text-4xl: 3.5rem; /* 56px */
      --text-3xl: 2.75rem; /* 44px */
    }
  }
}

/* Fluid typography using clamp() */
.fluid-typography {
  /* Modern approach with clamp() */
  h1 {
    font-size: clamp(1.875rem, 4vw, 4rem);
    /* Min: 30px, Preferred: 4vw, Max: 64px */
  }

  h2 {
    font-size: clamp(1.5rem, 3vw, 2.5rem);
    /* Min: 24px, Preferred: 3vw, Max: 40px */
  }

  h3 {
    font-size: clamp(1.25rem, 2.5vw, 1.875rem);
    /* Min: 20px, Preferred: 2.5vw, Max: 30px */
  }

  p {
    font-size: clamp(1rem, 1.5vw, 1.125rem);
    /* Min: 16px, Preferred: 1.5vw, Max: 18px */
  }

  /* Fluid line-height */
  .content {
    line-height: clamp(1.4, 1.5vw, 1.8);
  }
}
```

### Responsive Spacing System

```css
/* Mobile-First spacing system */
.responsive-spacing {
  /* Mobile spacing scale */
  --space-xs: 0.25rem; /* 4px */
  --space-sm: 0.5rem; /* 8px */
  --space-md: 1rem; /* 16px */
  --space-lg: 1.5rem; /* 24px */
  --space-xl: 2rem; /* 32px */
  --space-2xl: 3rem; /* 48px */
  --space-3xl: 4rem; /* 64px */

  /* Component spacing */
  .section {
    padding: var(--space-lg) var(--space-md);
    margin-bottom: var(--space-xl);
  }

  .container {
    padding: 0 var(--space-md);
    margin: 0 auto;
  }

  .card {
    padding: var(--space-lg);
    margin-bottom: var(--space-lg);
    gap: var(--space-md);
  }

  /* Tablet spacing adjustments */
  @media (min-width: 768px) {
    :root {
      --space-xs: 0.375rem; /* 6px */
      --space-sm: 0.75rem; /* 12px */
      --space-md: 1.5rem; /* 24px */
      --space-lg: 2rem; /* 32px */
      --space-xl: 3rem; /* 48px */
      --space-2xl: 4rem; /* 64px */
      --space-3xl: 6rem; /* 96px */
    }

    .section {
      padding: var(--space-xl) var(--space-lg);
      margin-bottom: var(--space-2xl);
    }
  }

  /* Desktop spacing adjustments */
  @media (min-width: 1024px) {
    :root {
      --space-xs: 0.5rem; /* 8px */
      --space-sm: 1rem; /* 16px */
      --space-md: 2rem; /* 32px */
      --space-lg: 3rem; /* 48px */
      --space-xl: 4rem; /* 64px */
      --space-2xl: 6rem; /* 96px */
      --space-3xl: 8rem; /* 128px */
    }

    .section {
      padding: var(--space-2xl) var(--space-xl);
      margin-bottom: var(--space-3xl);
    }

    .container {
      max-width: 1200px;
    }
  }

  /* Large desktop spacing */
  @media (min-width: 1440px) {
    :root {
      --space-2xl: 8rem; /* 128px */
      --space-3xl: 12rem; /* 192px */
    }

    .container {
      max-width: 1400px;
    }
  }
}

/* Fluid spacing with clamp() */
.fluid-spacing {
  .section {
    padding: clamp(1rem, 4vw, 4rem) clamp(1rem, 3vw, 3rem);
    margin-bottom: clamp(1.5rem, 5vw, 6rem);
  }

  .container {
    padding: 0 clamp(1rem, 4vw, 3rem);
    max-width: clamp(320px, 90vw, 1400px);
    margin: 0 auto;
  }

  .grid-gap {
    gap: clamp(1rem, 3vw, 3rem);
  }
}
```

## 4. Responsive Images และ Media

### Responsive Images

```css
/* Responsive images and media */
.responsive-media {
  /* Basic responsive image */
  .responsive-image {
    max-width: 100%;
    height: auto;
    display: block;
  }

  /* Picture element for art direction */
  .art-direction {
    display: block;
    width: 100%;
  }

  .art-direction img {
    width: 100%;
    height: auto;
    object-fit: cover;
  }

  /* Responsive image grid */
  .image-grid {
    display: grid;
    gap: 1rem;

    /* Mobile: Single column */
    grid-template-columns: 1fr;
  }

  @media (min-width: 768px) {
    .image-grid {
      grid-template-columns: repeat(2, 1fr);
      gap: 1.5rem;
    }
  }

  @media (min-width: 1024px) {
    .image-grid {
      grid-template-columns: repeat(3, 1fr);
      gap: 2rem;
    }
  }

  /* Aspect ratio containers */
  .aspect-ratio-container {
    position: relative;
    width: 100%;
    overflow: hidden;
    border-radius: 0.5rem;
  }

  /* 16:9 aspect ratio */
  .aspect-16-9 {
    aspect-ratio: 16 / 9;
  }

  /* 4:3 aspect ratio */
  .aspect-4-3 {
    aspect-ratio: 4 / 3;
  }

  /* Square aspect ratio */
  .aspect-square {
    aspect-ratio: 1 / 1;
  }

  .aspect-ratio-container img,
  .aspect-ratio-container video {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  /* Responsive video */
  .responsive-video {
    position: relative;
    width: 100%;
    aspect-ratio: 16 / 9;
    overflow: hidden;
    border-radius: 0.5rem;
  }

  .responsive-video iframe,
  .responsive-video video {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border: none;
  }

  /* Image with different sizes for different screens */
  .hero-image {
    width: 100%;
    height: 300px;
    object-fit: cover;
    border-radius: 0.5rem;
  }

  @media (min-width: 768px) {
    .hero-image {
      height: 400px;
    }
  }

  @media (min-width: 1024px) {
    .hero-image {
      height: 500px;
    }
  }

  @media (min-width: 1440px) {
    .hero-image {
      height: 600px;
    }
  }
}
```

### HTML for Responsive Images

```html
<!-- HTML examples for responsive images -->

<!-- 1. Basic responsive image -->
<img src="image.jpg" alt="Description" class="responsive-image" />

<!-- 2. Responsive images with srcset -->
<img
  src="image-800w.jpg"
  srcset="image-400w.jpg 400w, image-800w.jpg 800w, image-1200w.jpg 1200w"
  sizes="
    (max-width: 767px) 100vw,
    (max-width: 1023px) 50vw,
    33vw
  "
  alt="Description"
  class="responsive-image"
/>

<!-- 3. Art direction with picture element -->
<picture class="art-direction">
  <!-- Mobile: Portrait crop -->
  <source media="(max-width: 767px)" srcset="image-mobile.jpg" />
  <!-- Tablet: Square crop -->
  <source media="(max-width: 1023px)" srcset="image-tablet.jpg" />
  <!-- Desktop: Landscape crop -->
  <source media="(min-width: 1024px)" srcset="image-desktop.jpg" />
  <!-- Fallback -->
  <img src="image-desktop.jpg" alt="Description" />
</picture>

<!-- 4. WebP with fallback -->
<picture>
  <source type="image/webp" srcset="image.webp" />
  <source type="image/jpeg" srcset="image.jpg" />
  <img src="image.jpg" alt="Description" class="responsive-image" />
</picture>

<!-- 5. Responsive video -->
<div class="responsive-video">
  <video autoplay muted loop>
    <source src="video.mp4" type="video/mp4" />
    <source src="video.webm" type="video/webm" />
  </video>
</div>

<!-- 6. YouTube embed responsive -->
<div class="responsive-video">
  <iframe
    src="https://www.youtube.com/embed/dQw4w9WgXcQ"
    title="YouTube video player"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
  >
  </iframe>
</div>
```

## 5. Performance Optimization สำหรับ Mobile-First

### CSS Performance Best Practices

```css
/* Performance optimization for mobile-first */
.performance-optimized {
  /* 1. Critical CSS - ใส่ inline ใน <head> */
  /* Base styles ที่จำเป็นสำหรับ above-the-fold content */

  /* 2. ใช้ efficient selectors */
  .efficient-selector {
    /* ✅ Good: Simple class selector */
    background: white;
  }

  /* ❌ Avoid: Complex selectors */
  .container .sidebar ul li a:hover {
    /* ช้า - หลีกเลี่ยง */
  }

  /* 3. Minimize repaints and reflows */
  .optimized-animations {
    /* ใช้ transform แทน top/left */
    transform: translateX(0);
    transition: transform 0.3s ease;
  }

  .optimized-animations:hover {
    transform: translateX(10px);
  }

  /* 4. Use will-change for animations */
  .animated-element {
    will-change: transform;
    transition: transform 0.3s ease;
  }

  /* Remove will-change after animation */
  .animated-element:not(:hover) {
    will-change: auto;
  }

  /* 5. Efficient responsive images */
  .optimized-image {
    /* ใช้ object-fit แทน background-image */
    width: 100%;
    height: 200px;
    object-fit: cover;

    /* Lazy loading hint */
    content-visibility: auto;
    contain-intrinsic-size: 300px 200px;
  }

  /* 6. Efficient grid layouts */
  .optimized-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: clamp(1rem, 3vw, 2rem);

    /* Contain layout shifts */
    contain: layout style;
  }

  /* 7. Optimize fonts loading */
  .font-optimized {
    /* System fonts for fast loading */
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
      'Helvetica Neue', Arial, sans-serif;

    /* Smooth font rendering */
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  /* 8. Efficient color management */
  :root {
    /* Use HSL for better performance */
    --primary: hsl(210, 100%, 50%);
    --primary-light: hsl(210, 100%, 60%);
    --primary-dark: hsl(210, 100%, 40%);

    /* Define color scheme */
    color-scheme: light dark;
  }

  /* 9. Container queries for better performance */
  @container (min-width: 300px) {
    .card {
      padding: 1.5rem;
    }
  }

  @container (min-width: 500px) {
    .card {
      padding: 2rem;
    }
  }
}
```

### Loading Performance

```css
/* Loading optimization strategies */
.loading-optimization {
  /* 1. Critical resource hints in HTML */
  /*
  <link rel="preload" href="critical.css" as="style">
  <link rel="preload" href="hero-image.jpg" as="image">
  <link rel="prefetch" href="secondary.css">
  */

  /* 2. Skeleton loading states */
  .skeleton {
    background: linear-gradient(90deg, #f0f0f0 25%, #e0e0e0 50%, #f0f0f0 75%);
    background-size: 200% 100%;
    animation: skeleton-loading 1.5s infinite;
  }

  @keyframes skeleton-loading {
    0% {
      background-position: 200% 0;
    }
    100% {
      background-position: -200% 0;
    }
  }

  /* 3. Progressive enhancement */
  .progressive-enhancement {
    /* Base styles without JavaScript */
    opacity: 1;
    transform: translateY(0);
  }

  /* Enhanced styles with JavaScript */
  .js .progressive-enhancement {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }

  .js .progressive-enhancement.loaded {
    opacity: 1;
    transform: translateY(0);
  }

  /* 4. Intersection Observer optimizations */
  .lazy-load {
    opacity: 0;
    transform: translateY(50px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }

  .lazy-load.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* 5. Reduced motion respect */
  @media (prefers-reduced-motion: reduce) {
    .skeleton {
      animation: none;
    }

    .progressive-enhancement,
    .lazy-load {
      transition: none;
    }
  }
}
```

## 6. Common Patterns และ Examples

### Complete Mobile-First Layout

```css
/* Complete mobile-first layout example */
.mobile-first-layout {
  /* CSS Custom Properties */
  :root {
    /* Colors */
    --primary: #3b82f6;
    --secondary: #64748b;
    --success: #10b981;
    --warning: #f59e0b;
    --error: #ef4444;
    --gray-50: #f8fafc;
    --gray-100: #f1f5f9;
    --gray-200: #e2e8f0;
    --gray-500: #64748b;
    --gray-700: #374151;
    --gray-900: #1f2937;

    /* Spacing */
    --space-1: 0.25rem;
    --space-2: 0.5rem;
    --space-3: 0.75rem;
    --space-4: 1rem;
    --space-6: 1.5rem;
    --space-8: 2rem;
    --space-12: 3rem;

    /* Typography */
    --font-sm: 0.875rem;
    --font-base: 1rem;
    --font-lg: 1.125rem;
    --font-xl: 1.25rem;
    --font-2xl: 1.5rem;
    --font-3xl: 1.875rem;

    /* Shadows */
    --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.05);
    --shadow-md: 0 4px 6px rgba(0, 0, 0, 0.1);
    --shadow-lg: 0 10px 15px rgba(0, 0, 0, 0.1);

    /* Borders */
    --border-radius: 0.375rem;
    --border-radius-lg: 0.5rem;
  }

  /* Base styles */
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    line-height: 1.6;
    color: var(--gray-700);
    background: var(--gray-50);
  }

  /* Layout Container */
  .layout {
    display: grid;
    grid-template-areas:
      'header'
      'main'
      'footer';
    min-height: 100vh;
    gap: 0;
  }

  /* Header */
  .header {
    grid-area: header;
    background: white;
    border-bottom: 1px solid var(--gray-200);
    padding: var(--space-4);
    position: sticky;
    top: 0;
    z-index: 50;
    box-shadow: var(--shadow-sm);
  }

  .header-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: 1200px;
    margin: 0 auto;
  }

  .logo {
    font-size: var(--font-xl);
    font-weight: 700;
    color: var(--primary);
  }

  .nav-toggle {
    display: block;
    background: none;
    border: none;
    font-size: var(--font-lg);
    cursor: pointer;
    padding: var(--space-2);
  }

  .nav-menu {
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background: white;
    border-top: 1px solid var(--gray-200);
    box-shadow: var(--shadow-md);
    display: none;
  }

  .nav-menu.active {
    display: block;
  }

  .nav-link {
    display: block;
    padding: var(--space-4);
    color: var(--gray-700);
    text-decoration: none;
    border-bottom: 1px solid var(--gray-100);
    transition: background-color 0.2s;
  }

  .nav-link:hover {
    background: var(--gray-50);
  }

  /* Main Content */
  .main {
    grid-area: main;
    padding: var(--space-6) var(--space-4);
    max-width: 1200px;
    margin: 0 auto;
    width: 100%;
  }

  /* Hero Section */
  .hero {
    text-align: center;
    padding: var(--space-8) 0;
    margin-bottom: var(--space-12);
  }

  .hero-title {
    font-size: var(--font-3xl);
    font-weight: 800;
    color: var(--gray-900);
    margin-bottom: var(--space-4);
    line-height: 1.2;
  }

  .hero-description {
    font-size: var(--font-lg);
    color: var(--gray-500);
    margin-bottom: var(--space-6);
    max-width: 600px;
    margin-left: auto;
    margin-right: auto;
  }

  .hero-cta {
    display: inline-block;
    background: var(--primary);
    color: white;
    padding: var(--space-3) var(--space-6);
    border-radius: var(--border-radius);
    text-decoration: none;
    font-weight: 600;
    transition: background-color 0.2s, transform 0.2s;
  }

  .hero-cta:hover {
    background: #2563eb;
    transform: translateY(-2px);
  }

  /* Content Grid */
  .content-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: var(--space-6);
    margin-bottom: var(--space-12);
  }

  .card {
    background: white;
    border-radius: var(--border-radius-lg);
    padding: var(--space-6);
    box-shadow: var(--shadow-md);
    transition: transform 0.2s, box-shadow 0.2s;
  }

  .card:hover {
    transform: translateY(-4px);
    box-shadow: var(--shadow-lg);
  }

  .card-title {
    font-size: var(--font-xl);
    font-weight: 600;
    color: var(--gray-900);
    margin-bottom: var(--space-3);
  }

  .card-description {
    color: var(--gray-500);
    line-height: 1.6;
  }

  /* Footer */
  .footer {
    grid-area: footer;
    background: var(--gray-900);
    color: white;
    padding: var(--space-8) var(--space-4);
    text-align: center;
  }

  .footer-content {
    max-width: 1200px;
    margin: 0 auto;
  }

  /* Tablet Styles */
  @media (min-width: 768px) {
    .layout {
      grid-template-areas:
        'header'
        'main'
        'footer';
    }

    .header {
      padding: var(--space-6) var(--space-8);
    }

    .nav-toggle {
      display: none;
    }

    .nav-menu {
      position: static;
      display: flex;
      background: none;
      border: none;
      box-shadow: none;
      gap: var(--space-6);
    }

    .nav-link {
      padding: var(--space-2) 0;
      border: none;
    }

    .main {
      padding: var(--space-8) var(--space-8);
    }

    .hero {
      padding: var(--space-12) 0;
    }

    .hero-title {
      font-size: 3rem;
    }

    .content-grid {
      grid-template-columns: repeat(2, 1fr);
      gap: var(--space-8);
    }
  }

  /* Desktop Styles */
  @media (min-width: 1024px) {
    .header {
      padding: var(--space-6) var(--space-12);
    }

    .main {
      padding: var(--space-12) var(--space-12);
    }

    .hero {
      padding: var(--space-12) 0 var(--space-12);
    }

    .hero-title {
      font-size: 4rem;
    }

    .content-grid {
      grid-template-columns: repeat(3, 1fr);
    }

    .footer {
      padding: var(--space-12) var(--space-12);
    }
  }

  /* Large Desktop */
  @media (min-width: 1440px) {
    .hero-title {
      font-size: 4.5rem;
    }

    .content-grid {
      grid-template-columns: repeat(4, 1fr);
    }
  }
}
```

## สรุป: Media Queries และ Mobile-First

### Key Concepts 🎯

1. **Mobile-First Approach**

   - เริ่มจากหน้าจอเล็กที่สุด
   - ใช้ `min-width` ใน media queries
   - Progressive enhancement

2. **Standard Breakpoints**

   ```css
   /* Mobile: 320px+ (base) */
   @media (min-width: 768px) {
     /* Tablet */
   }
   @media (min-width: 1024px) {
     /* Desktop */
   }
   @media (min-width: 1440px) {
     /* Large Desktop */
   }
   ```

3. **Media Query Features**

   - Width/Height: `min-width`, `max-width`
   - Orientation: `portrait`, `landscape`
   - Resolution: `min-resolution`
   - Interaction: `hover`, `pointer`
   - Preferences: `prefers-color-scheme`, `prefers-reduced-motion`

4. **Performance Best Practices**

   - Critical CSS inline
   - Efficient selectors
   - Optimize animations
   - Responsive images
   - Progressive enhancement

5. **Responsive Design Patterns**
   - Fluid typography with `clamp()`
   - Flexible spacing system
   - Container-based layouts
   - Component-driven approach

Mobile-First design ไม่เพียงแต่ช่วยปรับปรุง performance บน mobile devices เท่านั้น แต่ยังช่วยให้เราคิดเรื่อง content hierarchy และ user experience ได้ดีขึ้น!
