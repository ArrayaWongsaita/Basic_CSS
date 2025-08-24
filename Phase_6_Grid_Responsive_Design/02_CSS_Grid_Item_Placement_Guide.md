# CSS Grid Item Placement: การจัดวาง Grid Items

## ภาพรวม Grid Item Placement

การจัดวาง Grid Items เป็นความสามารถที่ทรงพลังของ CSS Grid ที่ให้เราควบคุมตำแหน่งของแต่ละ item ได้อย่างแม่นยำ โดยใช้ **Grid Lines**, **Grid Areas**, และ **Named Areas**

### แนวคิดพื้นฐาน: Grid Lines และ Grid Areas

```css
/* Grid Container Setup */
.grid-container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(3, 100px);
  gap: 1rem;
  padding: 1rem;
  border: 2px solid #3b82f6;
  background: #f8fafc;
}

/* Grid Items */
.grid-item {
  background: #dbeafe;
  border: 2px solid #3b82f6;
  border-radius: 0.5rem;
  padding: 1rem;
  text-align: center;
  font-weight: 600;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Visual Grid Lines */
.grid-container::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image: repeating-linear-gradient(
      to right,
      transparent,
      transparent calc(25% - 1px),
      rgba(59, 130, 246, 0.3) calc(25% - 1px),
      rgba(59, 130, 246, 0.3) 25%
    ), repeating-linear-gradient(to bottom, transparent, transparent calc(33.333% -
            1px), rgba(59, 130, 246, 0.3) calc(33.333% - 1px), rgba(
          59,
          130,
          246,
          0.3
        ) 33.333%);
  pointer-events: none;
  z-index: -1;
}
```

## 1. grid-column: การกำหนดตำแหน่ง Column

### Basic Column Placement

```css
/* การใช้ grid-column */
.column-placement-examples {
  /* Grid container */
  .grid-columns {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    grid-template-rows: repeat(3, 80px);
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #6b7280;
    margin-bottom: 2rem;
  }

  /* การใช้ grid-column-start และ grid-column-end */
  .item-1 {
    grid-column-start: 1;
    grid-column-end: 3; /* จาก line 1 ถึง line 3 (2 columns) */
    background: #fef2f2;
    border-color: #ef4444;
  }

  .item-2 {
    grid-column-start: 3;
    grid-column-end: 6; /* จาก line 3 ถึง line 6 (3 columns) */
    background: #f0fdf4;
    border-color: #10b981;
  }

  /* การใช้ grid-column shorthand */
  .item-3 {
    grid-column: 1 / 4; /* เท่ากับ grid-column-start: 1; grid-column-end: 4; */
    background: #eff6ff;
    border-color: #3b82f6;
  }

  .item-4 {
    grid-column: 4 / -1; /* จาก line 4 ถึง line สุดท้าย */
    background: #fefce8;
    border-color: #f59e0b;
  }

  /* การใช้ span */
  .item-5 {
    grid-column: span 2; /* ขยาย 2 columns จากตำแหน่งปัจจุบัน */
    background: #fdf4ff;
    border-color: #a855f7;
  }

  .item-6 {
    grid-column: 2 / span 3; /* เริ่มที่ line 2 และขยาย 3 columns */
    background: #f0fdfa;
    border-color: #06b6d4;
  }
}
```

### Advanced Column Techniques

```css
/* เทคนิคขั้นสูงสำหรับ grid-column */
.advanced-columns {
  /* Auto placement กับ specific column */
  .auto-placement-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: 80px;
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #8b5cf6;
  }

  /* Item ที่กำหนด column เฉพาะ */
  .featured-item {
    grid-column: 1 / -1; /* ขยายเต็มความกว้าง */
    background: #1f2937;
    color: white;
    font-size: 1.25rem;
    font-weight: bold;
  }

  .sidebar-item {
    grid-column: 1 / 2; /* column แรก */
    background: #f3f4f6;
    border-color: #6b7280;
  }

  .main-item {
    grid-column: 2 / -1; /* ส่วนที่เหลือ */
    background: white;
    border-color: #d1d5db;
  }

  /* Responsive column placement */
  .responsive-item {
    grid-column: 1 / -1; /* mobile: full width */
    background: #ecfdf5;
    border-color: #10b981;
  }

  @media (min-width: 768px) {
    .responsive-item {
      grid-column: 2 / 4; /* tablet: middle columns */
    }
  }

  @media (min-width: 1024px) {
    .responsive-item {
      grid-column: 3 / 5; /* desktop: last columns */
    }
  }

  /* Overlapping items */
  .overlay-base {
    grid-column: 1 / 3;
    grid-row: 1 / 3;
    background: #dbeafe;
    border-color: #3b82f6;
    z-index: 1;
  }

  .overlay-top {
    grid-column: 2 / 4;
    grid-row: 1 / 2;
    background: rgba(239, 68, 68, 0.9);
    border-color: #ef4444;
    color: white;
    z-index: 2;
  }
}
```

### Practical Column Examples

```css
/* ตัวอย่างการใช้งานจริง */
.practical-columns {
  /* Magazine layout */
  .magazine-layout {
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    grid-auto-rows: minmax(100px, auto);
    gap: 1.5rem;
    padding: 2rem;
  }

  .magazine-header {
    grid-column: 1 / -1; /* เต็มความกว้าง */
    background: #1f2937;
    color: white;
    padding: 2rem;
    text-align: center;
    font-size: 2rem;
    font-weight: bold;
  }

  .magazine-featured {
    grid-column: 1 / 4; /* 3 columns แรก */
    background: white;
    padding: 1.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  .magazine-sidebar {
    grid-column: 4 / -1; /* 3 columns สุดท้าย */
    background: #f8fafc;
    padding: 1.5rem;
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .magazine-article {
    grid-column: 1 / 3; /* 2 columns */
    background: white;
    padding: 1.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .magazine-ads {
    grid-column: 3 / -1; /* ส่วนที่เหลือ */
    background: #fef3c7;
    padding: 1rem;
    text-align: center;
    border: 2px dashed #f59e0b;
  }

  /* Dashboard layout */
  .dashboard-columns {
    display: grid;
    grid-template-columns: repeat(12, 1fr); /* 12-column system */
    gap: 1rem;
    padding: 1rem;
  }

  .widget-small {
    grid-column: span 3; /* 3/12 = 25% */
    background: white;
    padding: 1.5rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .widget-medium {
    grid-column: span 6; /* 6/12 = 50% */
    background: white;
    padding: 1.5rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .widget-large {
    grid-column: span 12; /* 12/12 = 100% */
    background: white;
    padding: 2rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  /* Mobile responsive */
  @media (max-width: 767px) {
    .widget-small,
    .widget-medium {
      grid-column: span 12; /* mobile: full width */
    }
  }

  @media (min-width: 768px) and (max-width: 1023px) {
    .widget-small {
      grid-column: span 6; /* tablet: half width */
    }
  }
}
```

## 2. grid-row: การกำหนดตำแหน่ง Row

### Basic Row Placement

```css
/* การใช้ grid-row */
.row-placement-examples {
  /* Grid container */
  .grid-rows {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(5, 80px);
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #6b7280;
    margin-bottom: 2rem;
  }

  /* การใช้ grid-row-start และ grid-row-end */
  .row-item-1 {
    grid-row-start: 1;
    grid-row-end: 3; /* จาก line 1 ถึง line 3 (2 rows) */
    background: #fef2f2;
    border-color: #ef4444;
  }

  .row-item-2 {
    grid-row-start: 3;
    grid-row-end: 6; /* จาก line 3 ถึง line 6 (3 rows) */
    background: #f0fdf4;
    border-color: #10b981;
  }

  /* การใช้ grid-row shorthand */
  .row-item-3 {
    grid-row: 1 / 4; /* เท่ากับ grid-row-start: 1; grid-row-end: 4; */
    background: #eff6ff;
    border-color: #3b82f6;
  }

  .row-item-4 {
    grid-row: 4 / -1; /* จาก line 4 ถึง line สุดท้าย */
    background: #fefce8;
    border-color: #f59e0b;
  }

  /* การใช้ span */
  .row-item-5 {
    grid-row: span 2; /* ขยาย 2 rows จากตำแหน่งปัจจุบัน */
    background: #fdf4ff;
    border-color: #a855f7;
  }

  .row-item-6 {
    grid-row: 2 / span 3; /* เริ่มที่ line 2 และขยาย 3 rows */
    background: #f0fdfa;
    border-color: #06b6d4;
  }
}
```

### Combined Column และ Row Placement

```css
/* การใช้ทั้ง grid-column และ grid-row ร่วมกัน */
.combined-placement {
  /* Complex grid layout */
  .complex-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(4, 100px);
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #3b82f6;
  }

  /* Header ขยายเต็มความกว้าง */
  .header-item {
    grid-column: 1 / -1; /* ทุก columns */
    grid-row: 1 / 2; /* row แรก */
    background: #1f2937;
    color: white;
    font-size: 1.25rem;
    font-weight: bold;
  }

  /* Sidebar สูง 2 rows */
  .sidebar-item {
    grid-column: 1 / 2; /* column แรก */
    grid-row: 2 / 4; /* rows 2-3 */
    background: #f8fafc;
    border-color: #6b7280;
  }

  /* Main content area */
  .main-item {
    grid-column: 2 / -1; /* columns ที่เหลือ */
    grid-row: 2 / 4; /* rows 2-3 */
    background: white;
    border-color: #d1d5db;
  }

  /* Footer ขยายเต็มความกว้าง */
  .footer-item {
    grid-column: 1 / -1; /* ทุก columns */
    grid-row: 4 / 5; /* row สุดท้าย */
    background: #374151;
    color: white;
    text-align: center;
  }

  /* Card ที่ขยาย 2x2 */
  .featured-card {
    grid-column: 2 / 4; /* 2 columns */
    grid-row: 2 / 4; /* 2 rows */
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    font-size: 1.5rem;
    font-weight: bold;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
  }

  /* Small cards */
  .small-card {
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    border-radius: 0.5rem;
    padding: 1rem;
  }

  .small-card-1 {
    grid-column: 4 / 5;
    grid-row: 2 / 3;
  }

  .small-card-2 {
    grid-column: 4 / 5;
    grid-row: 3 / 4;
  }
}
```

### Responsive Row Layouts

```css
/* Responsive row layouts */
.responsive-rows {
  /* Mobile-first approach */
  .responsive-layout {
    display: grid;
    grid-template-columns: 1fr;
    gap: 1rem;
    padding: 1rem;
  }

  /* Mobile: Stack vertically */
  .mobile-header {
    grid-column: 1;
    grid-row: 1;
    background: #1f2937;
    color: white;
    padding: 1rem;
    text-align: center;
  }

  .mobile-main {
    grid-column: 1;
    grid-row: 2;
    background: white;
    padding: 1.5rem;
  }

  .mobile-sidebar {
    grid-column: 1;
    grid-row: 3;
    background: #f8fafc;
    padding: 1rem;
  }

  .mobile-footer {
    grid-column: 1;
    grid-row: 4;
    background: #374151;
    color: white;
    padding: 1rem;
    text-align: center;
  }

  /* Tablet: 2-column layout */
  @media (min-width: 768px) {
    .responsive-layout {
      grid-template-columns: 1fr 300px;
      grid-template-rows: auto 1fr auto;
    }

    .mobile-header {
      grid-column: 1 / -1;
      grid-row: 1;
    }

    .mobile-main {
      grid-column: 1;
      grid-row: 2;
    }

    .mobile-sidebar {
      grid-column: 2;
      grid-row: 2;
    }

    .mobile-footer {
      grid-column: 1 / -1;
      grid-row: 3;
    }
  }

  /* Desktop: Complex layout */
  @media (min-width: 1024px) {
    .responsive-layout {
      grid-template-columns: 250px 1fr 200px;
      grid-template-rows: auto 1fr auto;
    }

    .mobile-sidebar {
      grid-column: 1;
      grid-row: 1 / -1; /* Full height sidebar */
    }

    .mobile-header {
      grid-column: 2 / -1;
      grid-row: 1;
    }

    .mobile-main {
      grid-column: 2;
      grid-row: 2;
    }

    .mobile-footer {
      grid-column: 2 / -1;
      grid-row: 3;
    }

    /* Add aside on desktop */
    .desktop-aside {
      grid-column: 3;
      grid-row: 2;
      background: #fef3c7;
      padding: 1rem;
    }
  }
}
```

## 3. grid-area: การใช้พิกัดและ Named Areas

### grid-area กับพิกัด (Coordinate-based)

```css
/* การใช้ grid-area กับพิกัด */
.grid-area-coordinates {
  /* grid-area: row-start / column-start / row-end / column-end */

  .coordinates-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(3, 100px);
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #8b5cf6;
  }

  /* การใช้ grid-area shorthand */
  .area-item-1 {
    grid-area: 1 / 1 / 2 / 3; /* row 1, column 1-2 */
    background: #fef2f2;
    border-color: #ef4444;
  }

  .area-item-2 {
    grid-area: 1 / 3 / 3 / 5; /* row 1-2, column 3-4 */
    background: #f0fdf4;
    border-color: #10b981;
  }

  .area-item-3 {
    grid-area: 2 / 1 / 4 / 2; /* row 2-3, column 1 */
    background: #eff6ff;
    border-color: #3b82f6;
  }

  .area-item-4 {
    grid-area: 3 / 2 / 4 / 4; /* row 3, column 2-3 */
    background: #fefce8;
    border-color: #f59e0b;
  }

  /* การใช้ span กับ grid-area */
  .area-span-1 {
    grid-area: 1 / 1 / span 2 / span 2; /* ขยาย 2 rows และ 2 columns */
    background: #fdf4ff;
    border-color: #a855f7;
  }

  .area-span-2 {
    grid-area: span 1 / span 3 / 4 / 5; /* ขยาย 1 row และ 3 columns */
    background: #f0fdfa;
    border-color: #06b6d4;
  }
}
```

### Named Grid Areas

```css
/* การใช้ grid-template-areas กับ named areas */
.named-areas {
  /* Basic named areas layout */
  .basic-named-layout {
    display: grid;
    grid-template-columns: 250px 1fr 200px;
    grid-template-rows: auto 1fr auto;
    grid-template-areas:
      'header header header'
      'sidebar main aside'
      'footer footer footer';
    gap: 1rem;
    min-height: 100vh;
    padding: 1rem;
  }

  /* Grid items ใช้ชื่อ areas */
  .named-header {
    grid-area: header;
    background: #1f2937;
    color: white;
    padding: 1.5rem;
    text-align: center;
    font-size: 1.5rem;
    font-weight: bold;
  }

  .named-sidebar {
    grid-area: sidebar;
    background: #f8fafc;
    padding: 1.5rem;
    border: 1px solid #e5e7eb;
    border-radius: 0.5rem;
  }

  .named-main {
    grid-area: main;
    background: white;
    padding: 2rem;
    border: 1px solid #e5e7eb;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .named-aside {
    grid-area: aside;
    background: #fef3c7;
    padding: 1.5rem;
    border: 1px solid #f59e0b;
    border-radius: 0.5rem;
  }

  .named-footer {
    grid-area: footer;
    background: #374151;
    color: white;
    padding: 1.5rem;
    text-align: center;
    border-radius: 0.5rem;
  }

  /* Complex named areas */
  .complex-named-layout {
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    grid-template-rows: auto auto 1fr auto;
    grid-template-areas:
      'nav nav nav nav nav nav'
      'hero hero hero hero sidebar sidebar'
      'content content content content sidebar sidebar'
      'footer footer footer footer footer footer';
    gap: 1.5rem;
    padding: 2rem;
    min-height: 100vh;
  }

  .complex-nav {
    grid-area: nav;
    background: white;
    padding: 1rem 2rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    border-radius: 0.5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .complex-hero {
    grid-area: hero;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 3rem;
    border-radius: 0.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    font-size: 2rem;
    font-weight: bold;
  }

  .complex-content {
    grid-area: content;
    background: white;
    padding: 2rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .complex-sidebar {
    grid-area: sidebar;
    background: #f8fafc;
    padding: 1.5rem;
    border-radius: 0.5rem;
    border: 1px solid #e5e7eb;
  }

  .complex-footer {
    grid-area: footer;
    background: #1f2937;
    color: white;
    padding: 2rem;
    border-radius: 0.5rem;
    text-align: center;
  }
}
```

### Responsive Named Areas

```css
/* Responsive named areas */
.responsive-named-areas {
  /* Mobile layout */
  .responsive-named-grid {
    display: grid;
    grid-template-columns: 1fr;
    grid-template-areas:
      'header'
      'main'
      'sidebar'
      'footer';
    gap: 1rem;
    padding: 1rem;
  }

  /* Tablet layout */
  @media (min-width: 768px) {
    .responsive-named-grid {
      grid-template-columns: 1fr 300px;
      grid-template-areas:
        'header header'
        'main sidebar'
        'footer footer';
      gap: 1.5rem;
      padding: 1.5rem;
    }
  }

  /* Desktop layout */
  @media (min-width: 1024px) {
    .responsive-named-grid {
      grid-template-columns: 250px 1fr 200px;
      grid-template-areas:
        'header header header'
        'sidebar main aside'
        'footer footer footer';
      gap: 2rem;
      padding: 2rem;
    }

    /* เพิ่ม aside area สำหรับ desktop */
    .responsive-aside {
      grid-area: aside;
      background: #fef3c7;
      padding: 1.5rem;
      border-radius: 0.5rem;
      border: 1px solid #f59e0b;
    }
  }

  /* Wide desktop layout */
  @media (min-width: 1400px) {
    .responsive-named-grid {
      grid-template-columns: 300px 1fr 250px 200px;
      grid-template-areas:
        'header header header header'
        'sidebar main content aside'
        'footer footer footer footer';
    }

    /* เพิ่ม content area สำหรับ wide desktop */
    .responsive-content {
      grid-area: content;
      background: #ecfdf5;
      padding: 1.5rem;
      border-radius: 0.5rem;
      border: 1px solid #10b981;
    }
  }

  /* Grid items */
  .resp-header {
    grid-area: header;
    background: #1f2937;
    color: white;
    padding: 1.5rem;
    text-align: center;
    border-radius: 0.5rem;
  }

  .resp-main {
    grid-area: main;
    background: white;
    padding: 2rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .resp-sidebar {
    grid-area: sidebar;
    background: #f8fafc;
    padding: 1.5rem;
    border-radius: 0.5rem;
    border: 1px solid #e5e7eb;
  }

  .resp-footer {
    grid-area: footer;
    background: #374151;
    color: white;
    padding: 1.5rem;
    text-align: center;
    border-radius: 0.5rem;
  }
}
```

### Advanced Named Areas Techniques

```css
/* เทคนิคขั้นสูงสำหรับ named areas */
.advanced-named-areas {
  /* Dashboard layout กับ named areas */
  .dashboard-named {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    grid-template-rows: auto auto 1fr auto;
    grid-template-areas:
      'nav nav nav nav nav nav nav nav nav nav nav nav'
      'stats stats stats stats stats stats stats stats stats stats stats stats'
      'sidebar sidebar main main main main main main charts charts charts charts'
      'footer footer footer footer footer footer footer footer footer footer footer footer';
    gap: 1.5rem;
    padding: 2rem;
    min-height: 100vh;
  }

  .dashboard-nav {
    grid-area: nav;
    background: white;
    padding: 1rem 2rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    border-radius: 0.5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .dashboard-stats {
    grid-area: stats;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1rem;
  }

  .stat-card {
    background: white;
    padding: 1.5rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    text-align: center;
  }

  .dashboard-sidebar {
    grid-area: sidebar;
    background: #f8fafc;
    padding: 1.5rem;
    border-radius: 0.5rem;
    border: 1px solid #e5e7eb;
  }

  .dashboard-main {
    grid-area: main;
    background: white;
    padding: 2rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .dashboard-charts {
    grid-area: charts;
    background: white;
    padding: 1.5rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .dashboard-footer {
    grid-area: footer;
    background: #1f2937;
    color: white;
    padding: 1.5rem;
    text-align: center;
    border-radius: 0.5rem;
  }

  /* Magazine layout กับ complex areas */
  .magazine-named {
    display: grid;
    grid-template-columns: repeat(8, 1fr);
    grid-template-rows: auto auto auto 1fr auto;
    grid-template-areas:
      'header header header header header header header header'
      'featured featured featured featured featured sidebar sidebar sidebar'
      'article1 article1 article2 article2 article3 sidebar sidebar sidebar'
      'article4 article4 article5 article5 article6 ads ads ads'
      'footer footer footer footer footer footer footer footer';
    gap: 1.5rem;
    padding: 2rem;
  }

  .magazine-header {
    grid-area: header;
    background: #1f2937;
    color: white;
    padding: 2rem;
    text-align: center;
    font-size: 2.5rem;
    font-weight: bold;
    border-radius: 0.5rem;
  }

  .magazine-featured {
    grid-area: featured;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 2rem;
    border-radius: 0.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    font-size: 1.5rem;
    font-weight: bold;
  }

  .magazine-sidebar {
    grid-area: sidebar;
    background: #f8fafc;
    padding: 1.5rem;
    border-radius: 0.5rem;
    border: 1px solid #e5e7eb;
  }

  .magazine-article1 {
    grid-area: article1;
  }
  .magazine-article2 {
    grid-area: article2;
  }
  .magazine-article3 {
    grid-area: article3;
  }
  .magazine-article4 {
    grid-area: article4;
  }
  .magazine-article5 {
    grid-area: article5;
  }
  .magazine-article6 {
    grid-area: article6;
  }

  .magazine-article1,
  .magazine-article2,
  .magazine-article3,
  .magazine-article4,
  .magazine-article5,
  .magazine-article6 {
    background: white;
    padding: 1.5rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .magazine-ads {
    grid-area: ads;
    background: #fef3c7;
    padding: 1.5rem;
    border-radius: 0.5rem;
    border: 2px dashed #f59e0b;
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    color: #92400e;
  }

  .magazine-footer {
    grid-area: footer;
    background: #374151;
    color: white;
    padding: 1.5rem;
    text-align: center;
    border-radius: 0.5rem;
  }
}
```

## 4. Practical Examples และ Common Patterns

### Card Layouts

```css
/* การใช้ grid placement สำหรับ card layouts */
.card-layouts {
  /* Pinterest-style layout */
  .pinterest-layout {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    grid-auto-rows: 10px; /* Small row height */
    gap: 1rem;
    padding: 2rem;
  }

  .pinterest-card {
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    padding: 1rem;
    break-inside: avoid; /* Prevent breaking */
  }

  /* Dynamic card heights */
  .card-small {
    grid-row: span 20; /* 200px */
  }

  .card-medium {
    grid-row: span 30; /* 300px */
  }

  .card-large {
    grid-row: span 40; /* 400px */
  }

  .card-extra-large {
    grid-row: span 50; /* 500px */
  }

  /* Featured card layout */
  .featured-layout {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    grid-auto-rows: 200px;
    gap: 1.5rem;
    padding: 2rem;
  }

  .featured-card {
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    padding: 1.5rem;
    transition: transform 0.2s;
  }

  .featured-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 12px rgba(0, 0, 0, 0.15);
  }

  /* Hero card - spans 2x2 */
  .hero-card {
    grid-column: span 2;
    grid-row: span 2;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    font-size: 1.5rem;
    font-weight: bold;
  }

  /* Tall card */
  .tall-card {
    grid-row: span 2;
    background: #ecfdf5;
    border: 2px solid #10b981;
  }

  /* Wide card */
  .wide-card {
    grid-column: span 2;
    background: #fef3c7;
    border: 2px solid #f59e0b;
  }
}
```

### Layout Patterns

```css
/* รูปแบบ layout ที่ใช้บ่อย */
.layout-patterns {
  /* Holy Grail Layout */
  .holy-grail {
    display: grid;
    grid-template-columns: 200px 1fr 150px;
    grid-template-rows: auto 1fr auto;
    grid-template-areas:
      'header header header'
      'nav main aside'
      'footer footer footer';
    min-height: 100vh;
    gap: 1rem;
    padding: 1rem;
  }

  .holy-grail-header {
    grid-area: header;
    background: #1f2937;
    color: white;
    padding: 1.5rem;
    text-align: center;
  }

  .holy-grail-nav {
    grid-area: nav;
    background: #f8fafc;
    padding: 1.5rem;
  }

  .holy-grail-main {
    grid-area: main;
    background: white;
    padding: 2rem;
    min-width: 0; /* Prevent overflow */
  }

  .holy-grail-aside {
    grid-area: aside;
    background: #fef3c7;
    padding: 1rem;
  }

  .holy-grail-footer {
    grid-area: footer;
    background: #374151;
    color: white;
    padding: 1.5rem;
    text-align: center;
  }

  /* App Shell Layout */
  .app-shell {
    display: grid;
    grid-template-columns: 280px 1fr;
    grid-template-rows: 60px 1fr;
    grid-template-areas:
      'sidebar header'
      'sidebar main';
    height: 100vh;
    gap: 0;
  }

  .app-shell-header {
    grid-area: header;
    background: white;
    border-bottom: 1px solid #e5e7eb;
    padding: 0 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }

  .app-shell-sidebar {
    grid-area: sidebar;
    background: #1f2937;
    color: white;
    padding: 1rem 0;
    overflow-y: auto;
  }

  .app-shell-main {
    grid-area: main;
    background: #f8fafc;
    padding: 2rem;
    overflow-y: auto;
  }

  /* Blog Layout */
  .blog-layout {
    display: grid;
    grid-template-columns: 1fr minmax(200px, 300px);
    grid-template-rows: auto 1fr auto;
    grid-template-areas:
      'header sidebar'
      'main sidebar'
      'footer footer';
    gap: 2rem;
    max-width: 1200px;
    margin: 0 auto;
    padding: 2rem;
  }

  .blog-header {
    grid-area: header;
    background: white;
    padding: 2rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .blog-main {
    grid-area: main;
    background: white;
    padding: 2rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    min-width: 0;
  }

  .blog-sidebar {
    grid-area: sidebar;
    background: #f8fafc;
    padding: 1.5rem;
    border-radius: 0.5rem;
    border: 1px solid #e5e7eb;
    align-self: start; /* ไม่ยืดเต็มความสูง */
  }

  .blog-footer {
    grid-area: footer;
    background: #1f2937;
    color: white;
    padding: 2rem;
    text-align: center;
    border-radius: 0.5rem;
  }

  /* Mobile responsive */
  @media (max-width: 768px) {
    .holy-grail,
    .blog-layout {
      grid-template-columns: 1fr;
      grid-template-areas:
        'header'
        'main'
        'nav'
        'aside'
        'footer';
    }

    .app-shell {
      grid-template-columns: 1fr;
      grid-template-rows: 60px auto 1fr;
      grid-template-areas:
        'header'
        'sidebar'
        'main';
    }

    .app-shell-sidebar {
      height: auto;
      max-height: 200px;
    }
  }
}
```

## 5. Best Practices และ Tips

### Performance และ Maintainability

```css
/* Best practices สำหรับ grid placement */
.best-practices {
  /* ✅ ใช้ named areas สำหรับ layout ที่ซับซ้อน */
  .good-named-layout {
    display: grid;
    grid-template-areas:
      'header header'
      'sidebar main'
      'footer footer';
    /* ชัดเจนและอ่านง่าย */
  }

  /* ❌ หลีกเลี่ยง hardcoded line numbers ที่ซับซ้อน */
  .avoid-complex-numbers {
    grid-column: 3 / 7;
    grid-row: 2 / 5;
    /* ยากต่อการ maintain */
  }

  /* ✅ ใช้ semantic naming */
  .semantic-areas {
    display: grid;
    grid-template-areas:
      'navigation navigation navigation'
      'sidebar content advertisements'
      'footer footer footer';
    /* ชื่อที่มีความหมาย */
  }

  /* ✅ Mobile-first responsive design */
  .mobile-first-grid {
    display: grid;
    grid-template-areas:
      'header'
      'main'
      'sidebar'
      'footer';
    gap: 1rem;
  }

  @media (min-width: 768px) {
    .mobile-first-grid {
      grid-template-columns: 1fr 300px;
      grid-template-areas:
        'header header'
        'main sidebar'
        'footer footer';
    }
  }

  /* ✅ ใช้ CSS Custom Properties */
  .custom-properties-grid {
    --sidebar-width: 250px;
    --gap-size: 2rem;
    --header-height: 80px;

    display: grid;
    grid-template-columns: var(--sidebar-width) 1fr;
    grid-template-rows: var(--header-height) 1fr;
    gap: var(--gap-size);
  }

  /* ✅ Fallback สำหรับ browsers เก่า */
  .fallback-layout {
    /* Flexbox fallback */
    display: flex;
    flex-direction: column;

    /* Grid enhancement */
    display: grid;
    grid-template-areas:
      'header'
      'main'
      'footer';
  }

  @supports (display: grid) {
    .fallback-layout {
      display: grid;
    }
  }
}
```

### Debugging และ Development

```css
/* เครื่องมือสำหรับ debug grid */
.debug-grid {
  /* แสดง grid lines */
  .debug-container {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    grid-template-rows: repeat(8, 50px);
    gap: 1rem;
    padding: 1rem;

    /* Debug styles */
    background-image: linear-gradient(
        rgba(255, 0, 0, 0.1) 1px,
        transparent 1px
      ), linear-gradient(90deg, rgba(255, 0, 0, 0.1) 1px, transparent 1px);
    background-size: calc(100% / 12) 50px;
  }

  /* แสดง area boundaries */
  .debug-areas {
    display: grid;
    grid-template-areas:
      'a a b b'
      'c c d d';
    gap: 1rem;
  }

  .debug-areas > * {
    border: 2px dashed red;
    background: rgba(255, 0, 0, 0.1);
  }

  /* Grid line numbers */
  .grid-with-numbers {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(3, 100px);
    gap: 1rem;
    position: relative;
  }

  /* คำแนะนำสำหรับ development */
  .development-tips {
    /* ใช้ Firefox DevTools Grid Inspector */
    /* ใช้ Chrome DevTools Grid overlay */
    /* ใช้ gap แทน margin เสมอ */
    /* ตั้งชื่อ areas ให้สื่อความหมาย */
    /* ทดสอบใน mobile devices */
  }
}
```

## สรุป: Grid Item Placement

### Key Concepts 🎯

1. **Grid Lines และ Coordinates**

   - `grid-column: start / end`
   - `grid-row: start / end`
   - `grid-area: row-start / column-start / row-end / column-end`

2. **Named Areas**

   ```css
   .container {
     grid-template-areas:
       'header header'
       'sidebar main'
       'footer footer';
   }

   .item {
     grid-area: header;
   }
   ```

3. **Span Syntax**

   - `grid-column: span 2` - ขยาย 2 columns
   - `grid-row: span 3` - ขยาย 3 rows

4. **Responsive Placement**

   - เปลี่ยน `grid-template-areas` ตาม breakpoint
   - ใช้ mobile-first approach

5. **Best Practices**
   - ใช้ named areas สำหรับ layout ซับซ้อน
   - ใช้ semantic naming
   - เริ่มจาก mobile design
   - ใช้ CSS Custom Properties

### Common Patterns 📋

```css
/* Layout หลักที่ใช้บ่อย */

/* Holy Grail */
.holy-grail {
  grid-template-areas:
    'header header header'
    'nav main aside'
    'footer footer footer';
}

/* App Shell */
.app-shell {
  grid-template-areas:
    'sidebar header'
    'sidebar main';
}

/* Blog Layout */
.blog {
  grid-template-areas:
    'header sidebar'
    'main sidebar'
    'footer footer';
}
```

CSS Grid Item Placement ให้ความยืดหยุ่นอย่างมากในการสร้าง layout ที่ซับซ้อน โดยเฉพาะการใช้ Named Areas ที่ทำให้ code อ่านง่ายและ maintain ได้ดี!
