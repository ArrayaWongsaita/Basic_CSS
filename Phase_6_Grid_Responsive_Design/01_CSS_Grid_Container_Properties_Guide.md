# CSS Grid Container Properties: คู่มือฉบับสมบูรณ์

## ภาพรวม CSS Grid

CSS Grid เป็นระบบ layout แบบ two-dimensional ที่ทรงพลังที่สุดใน CSS สำหรับการสร้าง layout ที่ซับซ้อน โดยการทำงานบน **Grid Container** (parent) และ **Grid Items** (children)

### แนวคิดพื้นฐาน: Grid Container

```css
/* Basic Grid Setup */
.grid-container {
  display: grid; /* สร้าง grid container */
  /* หรือ */
  display: inline-grid; /* สำหรับ inline grid container */
}

/* ทุก direct children จะกลายเป็น grid items */
.grid-item {
  /* Properties สำหรับ grid items */
  background-color: #dbeafe;
  padding: 1rem;
  border-radius: 0.5rem;
  text-align: center;
  border: 2px solid #3b82f6;
}

/* ตัวอย่างพื้นฐาน */
.basic-grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr; /* 3 columns เท่าๆ กัน */
  grid-template-rows: auto auto; /* 2 rows ปรับขนาดตาม content */
  gap: 1rem; /* ระยะห่างระหว่าง grid items */
  padding: 1rem;
  border: 3px solid #3b82f6;
  background-color: #f8fafc;
}
```

## 1. display: grid - การสร้าง Grid Container 🎯

### Grid vs Inline-Grid

```css
/* Grid Container Types */
.grid-examples {
  /* Block-level grid container */
  .block-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
    margin-bottom: 2rem;
    padding: 1rem;
    border: 2px solid #ef4444;
    background-color: #fef2f2;
  }

  /* Inline-level grid container */
  .inline-grid {
    display: inline-grid;
    grid-template-columns: repeat(2, 100px);
    gap: 0.5rem;
    padding: 1rem;
    border: 2px solid #10b981;
    background-color: #f0fdf4;
    margin-right: 1rem;
    vertical-align: top;
  }

  /* การใช้งานจริง */
  .card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 1.5rem;
    padding: 2rem;
  }

  .dashboard-grid {
    display: grid;
    grid-template-columns: 250px 1fr;
    grid-template-rows: 60px 1fr 40px;
    height: 100vh;
    gap: 0;
  }
}
```

### Grid Container Properties Overview

```css
/* Grid Container Properties สำคัญ */
.grid-container-properties {
  .complete-grid {
    display: grid;

    /* การกำหนดขนาด columns และ rows */
    grid-template-columns: 200px 1fr 100px;
    grid-template-rows: auto 1fr auto;

    /* การตั้งชื่อ grid lines */
    grid-template-areas:
      'header header header'
      'sidebar main aside'
      'footer footer footer';

    /* ระยะห่าง */
    gap: 1rem;
    /* หรือ */
    row-gap: 1rem;
    column-gap: 1.5rem;

    /* การจัดเรียง */
    justify-items: stretch; /* horizontal alignment ของ items */
    align-items: stretch; /* vertical alignment ของ items */
    justify-content: start; /* horizontal alignment ของ grid */
    align-content: start; /* vertical alignment ของ grid */

    /* Auto sizing */
    grid-auto-columns: minmax(100px, auto);
    grid-auto-rows: minmax(50px, auto);
    grid-auto-flow: row; /* ทิศทางการเพิ่ม items อัตโนมัติ */

    /* ขนาดและตำแหน่ง */
    width: 100%;
    height: 100vh;
    padding: 1rem;
  }
}
```

## 2. grid-template-columns: การกำหนด Columns

### Fixed Size Columns

```css
/* การกำหนดขนาด columns แบบต่างๆ */
.column-examples {
  /* Fixed pixel values */
  .fixed-columns {
    display: grid;
    grid-template-columns: 200px 300px 150px; /* 3 columns ขนาดคงที่ */
    gap: 1rem;
    margin-bottom: 2rem;
    padding: 1rem;
    border: 2px dashed #6b7280;
  }

  /* Percentage values */
  .percentage-columns {
    display: grid;
    grid-template-columns: 25% 50% 25%; /* 3 columns เป็น % */
    gap: 1rem;
    margin-bottom: 2rem;
    padding: 1rem;
    border: 2px dashed #3b82f6;
  }

  /* Mixed units */
  .mixed-columns {
    display: grid;
    grid-template-columns: 200px 1fr 100px; /* fixed + flexible + fixed */
    gap: 1rem;
    margin-bottom: 2rem;
    padding: 1rem;
    border: 2px dashed #10b981;
  }

  /* Em/rem units */
  .em-columns {
    display: grid;
    grid-template-columns: 15rem 20rem 10rem; /* responsive กับ font-size */
    gap: 1rem;
    margin-bottom: 2rem;
    padding: 1rem;
    border: 2px dashed #f59e0b;
  }
}
```

### Fractional Unit (fr)

```css
/* การใช้ fr unit - หน่วยที่ยืดหยุ่น */
.fr-unit-examples {
  /* Equal columns */
  .equal-fr {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr; /* แบ่งเท่าๆ กัน 3 ส่วน */
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #ef4444;
    margin-bottom: 1rem;
  }

  /* Proportional columns */
  .proportional-fr {
    display: grid;
    grid-template-columns: 1fr 2fr 1fr; /* อัตราส่วน 1:2:1 */
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #3b82f6;
    margin-bottom: 1rem;
  }

  /* Mixed fr and fixed */
  .mixed-fr {
    display: grid;
    grid-template-columns: 200px 1fr 2fr 100px; /* fixed + flex + flex + fixed */
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #10b981;
    margin-bottom: 1rem;
  }

  /* Real-world example: Blog layout */
  .blog-layout {
    display: grid;
    grid-template-columns: 250px 2fr 1fr; /* sidebar + main + aside */
    gap: 2rem;
    min-height: 100vh;
    padding: 1rem;
  }

  .sidebar {
    background: #f8fafc;
    padding: 1.5rem;
    border-radius: 0.5rem;
  }

  .main-content {
    background: white;
    padding: 2rem;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  .aside-content {
    background: #f8fafc;
    padding: 1.5rem;
    border-radius: 0.5rem;
  }
}
```

### การใช้ fr กับ min-content, max-content

```css
/* Advanced fr usage */
.advanced-fr {
  /* min-content: ขนาดเล็กที่สุดที่เป็นไปได้ */
  .min-content-example {
    display: grid;
    grid-template-columns: min-content 1fr min-content;
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #8b5cf6;
    margin-bottom: 1rem;
  }

  /* max-content: ขนาดใหญ่ที่สุดที่ content ต้องการ */
  .max-content-example {
    display: grid;
    grid-template-columns: max-content 1fr max-content;
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #ec4899;
    margin-bottom: 1rem;
  }

  /* fit-content(): จำกัดขนาดไม่ให้เกิน */
  .fit-content-example {
    display: grid;
    grid-template-columns: fit-content(200px) 1fr fit-content(150px);
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #f59e0b;
    margin-bottom: 1rem;
  }
}
```

## 3. grid-template-rows: การกำหนด Rows

### Basic Row Definitions

```css
/* การกำหนดขนาด rows */
.row-examples {
  /* Fixed height rows */
  .fixed-rows {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 100px 200px 150px; /* 3 rows ขนาดคงที่ */
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #ef4444;
    margin-bottom: 2rem;
  }

  /* Auto-sizing rows */
  .auto-rows {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: auto auto auto; /* ขนาดตาม content */
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #3b82f6;
    margin-bottom: 2rem;
  }

  /* Fractional rows */
  .fr-rows {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: 1fr 2fr 1fr; /* อัตราส่วน 1:2:1 */
    height: 400px; /* ต้องมีความสูงที่กำหนด */
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #10b981;
    margin-bottom: 2rem;
  }

  /* Mixed row units */
  .mixed-rows {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: 80px 1fr auto; /* header + main + footer */
    height: 500px;
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #f59e0b;
  }
}
```

### Practical Row Examples

```css
/* ตัวอย่างการใช้งานจริง */
.practical-rows {
  /* App layout */
  .app-layout {
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: auto 1fr auto; /* header + main + footer */
    min-height: 100vh;
    gap: 0;
  }

  .app-header {
    background: #1f2937;
    color: white;
    padding: 1rem 2rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .app-main {
    background: #f8fafc;
    padding: 2rem;
    overflow-y: auto;
  }

  .app-footer {
    background: #374151;
    color: white;
    padding: 1rem 2rem;
    text-align: center;
  }

  /* Dashboard layout */
  .dashboard {
    display: grid;
    grid-template-columns: 250px 1fr;
    grid-template-rows: 60px 1fr;
    height: 100vh;
    gap: 0;
  }

  .dashboard-header {
    grid-column: 1 / -1; /* ขยายเต็มทุก column */
    background: white;
    border-bottom: 1px solid #e5e7eb;
    display: flex;
    align-items: center;
    padding: 0 2rem;
  }

  .dashboard-sidebar {
    background: #f8fafc;
    border-right: 1px solid #e5e7eb;
    overflow-y: auto;
  }

  .dashboard-main {
    background: white;
    padding: 2rem;
    overflow-y: auto;
  }

  /* Card grid with rows */
  .card-rows {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    grid-template-rows: repeat(auto-fit, minmax(200px, auto));
    gap: 1.5rem;
    padding: 2rem;
  }

  .card {
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    padding: 1.5rem;
    display: flex;
    flex-direction: column;
  }

  .card-header {
    margin-bottom: 1rem;
    padding-bottom: 1rem;
    border-bottom: 1px solid #e5e7eb;
  }

  .card-content {
    flex: 1;
  }

  .card-footer {
    margin-top: 1rem;
    padding-top: 1rem;
    border-top: 1px solid #e5e7eb;
  }
}
```

## 4. gap: การกำหนดระยะห่าง

### Gap Properties

```css
/* การใช้ gap properties */
.gap-examples {
  /* gap - ระยะห่างทั้ง row และ column */
  .uniform-gap {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem; /* ระยะห่างเท่ากันทุกทิศทาง */
    padding: 1rem;
    border: 2px solid #6b7280;
    margin-bottom: 2rem;
  }

  /* แยก row-gap และ column-gap */
  .separate-gaps {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    row-gap: 2rem; /* ระยะห่างระหว่าง rows */
    column-gap: 1rem; /* ระยะห่างระหว่าง columns */
    padding: 1rem;
    border: 2px solid #3b82f6;
    margin-bottom: 2rem;
  }

  /* Gap shorthand */
  .shorthand-gap {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1.5rem 1rem; /* row-gap column-gap */
    padding: 1rem;
    border: 2px solid #10b981;
    margin-bottom: 2rem;
  }

  /* No gap */
  .no-gap {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 0; /* ไม่มีระยะห่าง */
    padding: 1rem;
    border: 2px solid #ef4444;
    margin-bottom: 2rem;
  }

  .no-gap .grid-item {
    border: 1px solid #d1d5db;
    margin: 0;
  }
}
```

### Responsive Gap

```css
/* Gap ที่ responsive */
.responsive-gap {
  .adaptive-gap {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1rem; /* mobile gap */
    padding: 1rem;
  }

  /* Tablet gap */
  @media (min-width: 768px) {
    .adaptive-gap {
      gap: 1.5rem;
      padding: 1.5rem;
    }
  }

  /* Desktop gap */
  @media (min-width: 1024px) {
    .adaptive-gap {
      gap: 2rem;
      padding: 2rem;
    }
  }

  /* Different gaps for different contexts */
  .context-gaps {
    /* Card grid - เว้นระยะมาก */
    .card-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 2rem;
    }

    /* Button group - เว้นระยะน้อย */
    .button-group {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
      gap: 0.5rem;
    }

    /* Form layout - เว้นระยะปานกลาง */
    .form-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 1rem;
    }

    /* Image gallery - เว้นระยะน้อย */
    .image-gallery {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
      gap: 0.25rem;
    }
  }
}
```

### Gap vs Margin Comparison

```css
/* เปรียบเทียบ gap กับ margin */
.gap-vs-margin {
  /* ❌ ใช้ margin - ซับซ้อนและมีปัญหา */
  .margin-spacing {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    padding: 1rem;
    border: 2px solid #ef4444;
    margin-bottom: 2rem;
  }

  .margin-spacing .grid-item {
    margin: 0.5rem; /* ปัญหา: margin รอบนอก */
  }

  /* ต้องแก้ไขด้วย negative margin */
  .margin-spacing {
    margin: -0.5rem;
    padding: 1.5rem;
  }

  /* ✅ ใช้ gap - ง่ายและสะอาด */
  .gap-spacing {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem; /* ง่ายและชัดเจน */
    padding: 1rem;
    border: 2px solid #10b981;
  }

  .gap-spacing .grid-item {
    margin: 0; /* ไม่ต้องใช้ margin */
  }
}
```

## 5. repeat(): การทำซ้ำแบบ Pattern

### Basic repeat() Function

```css
/* การใช้ repeat() function */
.repeat-examples {
  /* Basic repeat - ทำซ้ำขนาดเดียวกัน */
  .basic-repeat {
    display: grid;
    grid-template-columns: repeat(4, 1fr); /* 4 columns เท่ากัน */
    /* เท่ากับ: 1fr 1fr 1fr 1fr */
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #6b7280;
    margin-bottom: 2rem;
  }

  /* Repeat with different sizes */
  .mixed-repeat {
    display: grid;
    grid-template-columns: repeat(3, 200px); /* 3 columns ขนาด 200px */
    /* เท่ากับ: 200px 200px 200px */
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #3b82f6;
    margin-bottom: 2rem;
  }

  /* Repeat pattern */
  .pattern-repeat {
    display: grid;
    grid-template-columns: repeat(2, 1fr 2fr); /* ทำซ้ำ pattern 1fr 2fr */
    /* เท่ากับ: 1fr 2fr 1fr 2fr */
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #10b981;
    margin-bottom: 2rem;
  }

  /* Complex pattern */
  .complex-repeat {
    display: grid;
    grid-template-columns: repeat(3, 100px 1fr 50px); /* ทำซ้ำ 3 รอบ */
    /* เท่ากับ: 100px 1fr 50px 100px 1fr 50px 100px 1fr 50px */
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #f59e0b;
    margin-bottom: 2rem;
  }
}
```

### repeat() กับ Rows

```css
/* การใช้ repeat() กับ rows */
.repeat-rows {
  /* Equal height rows */
  .equal-rows {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: repeat(3, 150px); /* 3 rows สูงเท่ากัน */
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #8b5cf6;
    margin-bottom: 2rem;
  }

  /* Auto rows with repeat */
  .auto-repeat-rows {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(4, auto); /* 4 rows ขนาดตาม content */
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #ec4899;
    margin-bottom: 2rem;
  }

  /* Mixed pattern rows */
  .pattern-rows {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: repeat(2, 100px 1fr); /* ทำซ้ำ pattern */
    height: 500px;
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #06b6d4;
  }
}
```

### Practical repeat() Examples

```css
/* ตัวอย่างการใช้งานจริง */
.practical-repeat {
  /* Photo gallery */
  .photo-gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, 200px); /* ใช้กับ auto-fill */
    gap: 1rem;
    padding: 1rem;
    justify-content: center;
  }

  /* Navigation menu */
  .nav-menu {
    display: grid;
    grid-template-columns: repeat(5, 1fr); /* 5 menu items เท่ากัน */
    gap: 0;
    background: #1f2937;
    border-radius: 0.5rem;
    overflow: hidden;
  }

  .nav-item {
    padding: 1rem;
    text-align: center;
    color: white;
    text-decoration: none;
    transition: background-color 0.2s;
  }

  .nav-item:hover {
    background: #374151;
  }

  /* Dashboard metrics */
  .metrics-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr); /* 4 metrics cards */
    gap: 1.5rem;
    margin-bottom: 2rem;
  }

  .metric-card {
    background: white;
    padding: 1.5rem;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    text-align: center;
  }

  .metric-value {
    font-size: 2rem;
    font-weight: bold;
    color: #3b82f6;
    margin-bottom: 0.5rem;
  }

  .metric-label {
    color: #6b7280;
    font-size: 0.875rem;
  }

  /* Form grid */
  .form-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr); /* 2 columns form */
    gap: 1rem;
    margin-bottom: 1rem;
  }

  .form-group {
    display: flex;
    flex-direction: column;
  }

  .form-group.full-width {
    grid-column: 1 / -1; /* ขยายเต็มความกว้าง */
  }

  /* Product grid */
  .product-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 2rem;
    padding: 2rem;
  }

  .product-card {
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    transition: transform 0.2s;
  }

  .product-card:hover {
    transform: translateY(-4px);
  }
}
```

## 6. minmax(): การกำหนดขนาดขั้นต่ำและสูงสุด

### Basic minmax() Usage

```css
/* การใช้ minmax() function */
.minmax-examples {
  /* Basic minmax */
  .basic-minmax {
    display: grid;
    grid-template-columns: minmax(200px, 1fr) minmax(100px, 300px) 1fr;
    /* column 1: อย่างน้อย 200px, มากสุดเท่าที่มี space */
    /* column 2: อย่างน้อย 100px, มากสุด 300px */
    /* column 3: ยืดหยุ่นตาม space ที่เหลือ */
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #6b7280;
    margin-bottom: 2rem;
  }

  /* minmax with auto */
  .minmax-auto {
    display: grid;
    grid-template-columns: repeat(3, minmax(auto, 1fr));
    /* ขนาดตาม content แต่ไม่เกิน 1fr */
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #3b82f6;
    margin-bottom: 2rem;
  }

  /* minmax for responsive design */
  .responsive-minmax {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    /* columns จะปรับขนาดตามหน้าจอ แต่ไม่เล็กกว่า 250px */
    gap: 1.5rem;
    padding: 1rem;
    border: 2px solid #10b981;
    margin-bottom: 2rem;
  }

  /* minmax for content fitting */
  .content-minmax {
    display: grid;
    grid-template-columns: minmax(min-content, max-content) 1fr minmax(100px, auto);
    /* column 1: ขนาดตาม content (min ถึง max) */
    /* column 2: ยืดหยุ่น */
    /* column 3: อย่างน้อย 100px, มากสุดตาม content */
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #f59e0b;
    margin-bottom: 2rem;
  }
}
```

### minmax() กับ Rows

```css
/* การใช้ minmax() กับ rows */
.minmax-rows {
  /* Flexible row heights */
  .flexible-rows {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: minmax(100px, auto) 1fr minmax(50px, 100px);
    /* row 1: อย่างน้อย 100px, ขยายตาม content */
    /* row 2: ยืดหยุ่น */
    /* row 3: 50px-100px */
    height: 500px;
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #8b5cf6;
    margin-bottom: 2rem;
  }

  /* Auto-fit rows with minmax */
  .auto-rows-minmax {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-auto-rows: minmax(150px, auto); /* rows ใหม่จะมีขนาดอย่างน้อย 150px */
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #ec4899;
    margin-bottom: 2rem;
  }
}
```

### Practical minmax() Examples

```css
/* ตัวอย่างการใช้งานจริง */
.practical-minmax {
  /* Responsive card grid */
  .card-responsive {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    padding: 2rem;
  }

  .card {
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    padding: 1.5rem;
    min-height: 200px;
  }

  /* Sidebar layout with minmax */
  .sidebar-layout {
    display: grid;
    grid-template-columns: minmax(200px, 300px) 1fr;
    /* sidebar: 200px-300px, main: ส่วนที่เหลือ */
    gap: 0;
    min-height: 100vh;
  }

  .sidebar {
    background: #f8fafc;
    padding: 1.5rem;
    border-right: 1px solid #e5e7eb;
    overflow-y: auto;
  }

  .main-content {
    padding: 2rem;
    overflow-y: auto;
  }

  /* Image gallery with minmax */
  .image-gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 1rem;
    padding: 1rem;
  }

  .image-item {
    aspect-ratio: 1;
    background: #f3f4f6;
    border-radius: 0.5rem;
    overflow: hidden;
  }

  .image-item img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  /* Dashboard with minmax constraints */
  .dashboard-minmax {
    display: grid;
    grid-template-columns: minmax(250px, 300px) 1fr minmax(200px, 250px);
    grid-template-rows: auto 1fr auto;
    gap: 1rem;
    height: 100vh;
    padding: 1rem;
  }

  .dashboard-header {
    grid-column: 1 / -1;
    background: white;
    padding: 1rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .dashboard-sidebar {
    background: white;
    padding: 1.5rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    overflow-y: auto;
  }

  .dashboard-main {
    background: white;
    padding: 2rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    overflow-y: auto;
  }

  .dashboard-aside {
    background: white;
    padding: 1.5rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    overflow-y: auto;
  }

  .dashboard-footer {
    grid-column: 1 / -1;
    background: white;
    padding: 1rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    text-align: center;
  }
}
```

## 7. auto-fit vs auto-fill: การปรับ Columns อัตโนมัติ

### ความแตกต่างพื้นฐาน

```css
/* เปรียบเทียบ auto-fit vs auto-fill */
.auto-comparison {
  /* auto-fill: สร้าง columns ใหม่แม้ว่าจะว่าง */
  .auto-fill-example {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #ef4444;
    margin-bottom: 2rem;
    background: #fef2f2;
  }

  /* auto-fit: ยุบ columns ที่ว่าง ให้ items ขยาย */
  .auto-fit-example {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1rem;
    padding: 1rem;
    border: 2px solid #10b981;
    margin-bottom: 2rem;
    background: #f0fdf4;
  }

  /* Demo items */
  .demo-item {
    background: white;
    padding: 2rem;
    text-align: center;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    font-weight: 600;
  }
}
```

### Visual Comparison

```css
/* การแสดงผลที่ต่างกัน */
.visual-comparison {
  /* Container สำหรับเปรียบเทียบ */
  .comparison-container {
    display: flex;
    flex-direction: column;
    gap: 2rem;
    margin-bottom: 3rem;
  }

  .comparison-title {
    text-align: center;
    font-size: 1.125rem;
    font-weight: 600;
    margin-bottom: 1rem;
    padding: 0.5rem;
    border-radius: 0.375rem;
  }

  .fill-title {
    background: #fef2f2;
    color: #ef4444;
    border: 2px solid #ef4444;
  }

  .fit-title {
    background: #f0fdf4;
    color: #10b981;
    border: 2px solid #10b981;
  }

  /* Grid กับ items น้อย */
  .few-items {
    display: grid;
    gap: 1rem;
    padding: 1rem;
    border-radius: 0.5rem;
  }

  .few-items.auto-fill {
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
    background: #fef2f2;
    border: 2px solid #ef4444;
  }

  .few-items.auto-fit {
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    background: #f0fdf4;
    border: 2px solid #10b981;
  }

  /* Grid กับ items เยอะ */
  .many-items {
    display: grid;
    gap: 1rem;
    padding: 1rem;
    border-radius: 0.5rem;
  }

  .many-items.auto-fill {
    grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
    background: #fef2f2;
    border: 2px solid #ef4444;
  }

  .many-items.auto-fit {
    grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
    background: #f0fdf4;
    border: 2px solid #10b981;
  }
}
```

### When to Use Each

```css
/* เมื่อไหร่ควรใช้ auto-fit vs auto-fill */
.when-to-use {
  /* ✅ ใช้ auto-fit เมื่อ: ต้องการให้ items ขยายเต็มพื้นที่ */
  .use-auto-fit {
    /* Card layout - ต้องการให้ cards ขยายเต็มพื้นที่ */
    .card-layout {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 2rem;
      padding: 2rem;
    }

    /* Feature sections - ต้องการให้ features กระจายเต็ม */
    .feature-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 2rem;
      padding: 2rem;
    }

    /* Stats display - ต้องการให้ stats ขยายเต็ม */
    .stats-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 1.5rem;
      padding: 1.5rem;
    }
  }

  /* ✅ ใช้ auto-fill เมื่อ: ต้องการขนาดคงที่และจัดเรียงแบบ grid */
  .use-auto-fill {
    /* Image gallery - ต้องการ images ขนาดเท่ากัน */
    .image-gallery {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      gap: 1rem;
      padding: 1rem;
    }

    /* Product catalog - ต้องการ products ขนาดเท่ากัน */
    .product-catalog {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
      gap: 1.5rem;
      padding: 2rem;
    }

    /* Avatar grid - ต้องการ avatars ขนาดเท่ากัน */
    .avatar-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(80px, 1fr));
      gap: 1rem;
      padding: 1rem;
    }

    .avatar {
      aspect-ratio: 1;
      border-radius: 50%;
      background: #f3f4f6;
    }
  }
}
```

### Advanced Examples

```css
/* ตัวอย่างขั้นสูง */
.advanced-auto {
  /* Responsive dashboard ใช้ auto-fit */
  .dashboard-auto-fit {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    padding: 2rem;
  }

  .dashboard-widget {
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    padding: 1.5rem;
    min-height: 200px;
  }

  /* Photo grid ใช้ auto-fill */
  .photo-grid-auto-fill {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
    gap: 0.5rem;
    padding: 1rem;
  }

  .photo {
    aspect-ratio: 1;
    background: #f3f4f6;
    border-radius: 0.375rem;
    overflow: hidden;
  }

  /* Mixed layout */
  .mixed-auto-layout {
    display: grid;
    grid-template-rows: auto 1fr auto;
    gap: 2rem;
    min-height: 100vh;
    padding: 2rem;
  }

  .header-auto {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1rem;
    background: white;
    padding: 1.5rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .main-auto {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 1.5rem;
    align-content: start;
  }

  .footer-auto {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 1rem;
    background: white;
    padding: 1.5rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
}
```

### Responsive Behavior

```css
/* พฤติกรรม responsive ของ auto-fit และ auto-fill */
.responsive-auto {
  /* Mobile: 1 column */
  .responsive-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1rem;
    padding: 1rem;
  }

  /* ปรับ minmax ตาม breakpoint */
  @media (min-width: 640px) {
    .responsive-grid {
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 1.5rem;
      padding: 1.5rem;
    }
  }

  @media (min-width: 1024px) {
    .responsive-grid {
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 2rem;
      padding: 2rem;
    }
  }

  /* Complex responsive example */
  .complex-responsive {
    display: grid;
    gap: 1rem;
    padding: 1rem;
  }

  /* Mobile: Stack vertically */
  .complex-responsive {
    grid-template-columns: 1fr;
  }

  /* Tablet: Use auto-fill */
  @media (min-width: 768px) {
    .complex-responsive {
      grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      gap: 1.5rem;
      padding: 1.5rem;
    }
  }

  /* Desktop: Use auto-fit */
  @media (min-width: 1024px) {
    .complex-responsive {
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 2rem;
      padding: 2rem;
    }
  }
}
```

## สรุป: Grid Container Properties

### Key Concepts 🎯

1. **display: grid**

   - สร้าง grid container
   - แตกต่างจาก `inline-grid`

2. **grid-template-columns/rows**

   - กำหนดขนาดและจำนวน tracks
   - ใช้ได้หลากหลายหน่วย: px, %, fr, auto

3. **gap**

   - ระยะห่างระหว่าง grid items
   - ง่ายกว่าการใช้ margin

4. **repeat()**

   - ทำซ้ำ pattern การกำหนดขนาด
   - ใช้กับ auto-fit และ auto-fill

5. **fr unit**

   - หน่วยยืดหยุ่นสำหรับ grid
   - แบ่งพื้นที่ตามอัตราส่วน

6. **minmax()**

   - กำหนดขนาดขั้นต่ำและสูงสุด
   - สำคัญสำหรับ responsive design

7. **auto-fit vs auto-fill**
   - auto-fit: ขยาย items เต็มพื้นที่
   - auto-fill: รักษาขนาด grid ไว้

### Best Practices 📋

```css
/* ✅ Recommended patterns */
.best-practices {
  /* Responsive card grid */
  .card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
  }

  /* Sidebar layout */
  .sidebar-layout {
    display: grid;
    grid-template-columns: minmax(250px, 300px) 1fr;
    gap: 2rem;
  }

  /* Full-height app layout */
  .app-layout {
    display: grid;
    grid-template-rows: auto 1fr auto;
    min-height: 100vh;
    gap: 0;
  }
}
```

CSS Grid Container Properties เป็นพื้นฐานสำคัญสำหรับการสร้าง layout ที่ซับซ้อนและ responsive ได้อย่างมีประสิทธิภาพ!
