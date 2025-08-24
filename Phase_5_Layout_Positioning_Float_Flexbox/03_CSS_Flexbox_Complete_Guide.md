# CSS Flexbox: คู่มือฉบับสมบูรณ์ - Main Axis & Cross Axis

## ภาพรวม Flexbox

Flexbox (Flexible Box Layout) เป็นระบบ layout ที่ออกแบบมาสำหรับการจัดวาง elements ในมิติเดียว (one-dimensional) โดยมีแนวคิดหลักคือการทำงานกับ **Main Axis** และ **Cross Axis** เพื่อควบคุมการจัดวางและการกระจาย space

### แนวคิดพื้นฐาน: Flex Container และ Flex Items

```css
/* Basic Flexbox Setup */
.flex-container {
  display: flex; /* สร้าง flex container */
  /* หรือ */
  display: inline-flex; /* สำหรับ inline flex container */
}

/* ทุก direct children จะกลายเป็น flex items */
.flex-item {
  /* Properties สำหรับ flex items */
  flex: 1; /* shorthand สำหรับ flex-grow, flex-shrink, flex-basis */
}

/* ตัวอย่างพื้นฐาน */
.basic-flex {
  display: flex;
  gap: 1rem; /* ระยะห่างระหว่าง items */
  padding: 1rem;
  border: 2px solid #3b82f6;
}

.flex-item {
  background-color: #dbeafe;
  padding: 1rem;
  border-radius: 0.5rem;
  text-align: center;
}
```

## 1. Main Axis และ Cross Axis: แนวคิดหลัก 🎯

### ความหมายและความสำคัญ

**Main Axis** และ **Cross Axis** เป็นแนวคิดสำคัญที่สุดใน Flexbox ที่กำหนดทิศทางการจัดวาง

```css
/* 🎯 Main Axis = แกนหลัก (ทิศทางหลักของ flex container) */
/* 🎯 Cross Axis = แกนตั้งฉาก (ตั้งฉากกับ main axis) */

/* flex-direction กำหนด Main Axis */
.flex-direction-examples {
  /* flex-direction: row (ค่าเริ่มต้น) */
  .flex-row {
    display: flex;
    flex-direction: row; /* Main Axis = แนวนอน (ซ้าย→ขวา) */
    /* Cross Axis = แนวตั้ง (บน→ล่าง) */
  }

  /* flex-direction: column */
  .flex-column {
    display: flex;
    flex-direction: column; /* Main Axis = แนวตั้ง (บน→ล่าง) */
    /* Cross Axis = แนวนอน (ซ้าย→ขวา) */
  }

  /* flex-direction: row-reverse */
  .flex-row-reverse {
    display: flex;
    flex-direction: row-reverse; /* Main Axis = แนวนอน (ขวา→ซ้าย) */
    /* Cross Axis = แนวตั้ง (บน→ล่าง) */
  }

  /* flex-direction: column-reverse */
  .flex-column-reverse {
    display: flex;
    flex-direction: column-reverse; /* Main Axis = แนวตั้ง (ล่าง→บน) */
    /* Cross Axis = แนวนอน (ซ้าย→ขวา) */
  }
}
```

### Visual Representation

```css
/* การมองเห็น Main และ Cross Axis */
.axis-demonstration {
  /* flex-direction: row (ค่าเริ่มต้น) */
  .demo-row {
    display: flex;
    flex-direction: row;
    border: 3px solid #ef4444;
    padding: 1rem;
    position: relative;
  }

  /* แสดง Main Axis (แนวนอน) */
  .demo-row::before {
    content: 'Main Axis →';
    position: absolute;
    top: -2rem;
    left: 50%;
    transform: translateX(-50%);
    background: #ef4444;
    color: white;
    padding: 0.25rem 0.5rem;
    border-radius: 0.25rem;
    font-size: 0.875rem;
  }

  /* แสดง Cross Axis (แนวตั้ง) */
  .demo-row::after {
    content: 'Cross Axis ↓';
    position: absolute;
    top: 50%;
    left: -4rem;
    transform: translateY(-50%) rotate(-90deg);
    background: #10b981;
    color: white;
    padding: 0.25rem 0.5rem;
    border-radius: 0.25rem;
    font-size: 0.875rem;
  }

  /* flex-direction: column */
  .demo-column {
    display: flex;
    flex-direction: column;
    border: 3px solid #3b82f6;
    padding: 1rem;
    position: relative;
    height: 300px;
  }

  /* แสดง Main Axis (แนวตั้ง) */
  .demo-column::before {
    content: 'Main Axis ↓';
    position: absolute;
    top: 50%;
    left: -4rem;
    transform: translateY(-50%) rotate(-90deg);
    background: #3b82f6;
    color: white;
    padding: 0.25rem 0.5rem;
    border-radius: 0.25rem;
    font-size: 0.875rem;
  }

  /* แสดง Cross Axis (แนวนอน) */
  .demo-column::after {
    content: 'Cross Axis →';
    position: absolute;
    bottom: -2rem;
    left: 50%;
    transform: translateX(-50%);
    background: #10b981;
    color: white;
    padding: 0.25rem 0.5rem;
    border-radius: 0.25rem;
    font-size: 0.875rem;
  }
}
```

## 2. justify-content: การจัดวางตาม Main Axis

### ความหมายและ Values

`justify-content` ควบคุมการจัดวาง flex items ตาม **Main Axis**

```css
/* justify-content values */
.justify-content-examples {
  /* flex-start (ค่าเริ่มต้น) */
  .justify-start {
    display: flex;
    justify-content: flex-start; /* จัดไปต้น main axis */
    border: 2px solid #6b7280;
    padding: 1rem;
    margin-bottom: 1rem;
  }

  /* flex-end */
  .justify-end {
    display: flex;
    justify-content: flex-end; /* จัดไปท้าย main axis */
    border: 2px solid #6b7280;
    padding: 1rem;
    margin-bottom: 1rem;
  }

  /* center */
  .justify-center {
    display: flex;
    justify-content: center; /* จัดกึ่งกลาง main axis */
    border: 2px solid #6b7280;
    padding: 1rem;
    margin-bottom: 1rem;
  }

  /* space-between */
  .justify-between {
    display: flex;
    justify-content: space-between; /* กระจายห่างเท่าๆ กัน */
    border: 2px solid #6b7280;
    padding: 1rem;
    margin-bottom: 1rem;
  }

  /* space-around */
  .justify-around {
    display: flex;
    justify-content: space-around; /* space รอบๆ แต่ละ item */
    border: 2px solid #6b7280;
    padding: 1rem;
    margin-bottom: 1rem;
  }

  /* space-evenly */
  .justify-evenly {
    display: flex;
    justify-content: space-evenly; /* space เท่าๆ กันทุกช่วง */
    border: 2px solid #6b7280;
    padding: 1rem;
    margin-bottom: 1rem;
  }
}

/* การใช้งานจริง */
.practical-justify {
  /* Navigation bar */
  .navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .navbar .logo {
    font-size: 1.5rem;
    font-weight: bold;
    color: #1f2937;
  }

  .navbar .nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
    margin: 0;
    padding: 0;
  }

  /* Button group */
  .button-group {
    display: flex;
    justify-content: center;
    gap: 1rem;
    margin-top: 2rem;
  }

  /* Footer */
  .footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 2rem;
    background: #1f2937;
    color: white;
  }

  /* Card actions */
  .card-actions {
    display: flex;
    justify-content: flex-end;
    gap: 0.5rem;
    margin-top: 1rem;
    padding-top: 1rem;
    border-top: 1px solid #e5e7eb;
  }
}
```

### justify-content กับ flex-direction ต่างๆ

```css
/* ผลของ justify-content ใน flex-direction ต่างๆ */
.justify-with-direction {
  /* flex-direction: row */
  .row-justify-center {
    display: flex;
    flex-direction: row;
    justify-content: center; /* จัดกึ่งกลางแนวนอน */
    border: 2px dashed #ef4444;
    height: 100px;
    padding: 1rem;
  }

  /* flex-direction: column */
  .column-justify-center {
    display: flex;
    flex-direction: column;
    justify-content: center; /* จัดกึ่งกลางแนวตั้ง */
    border: 2px dashed #3b82f6;
    height: 200px;
    padding: 1rem;
  }

  /* flex-direction: row-reverse */
  .row-reverse-justify-start {
    display: flex;
    flex-direction: row-reverse;
    justify-content: flex-start; /* เริ่มจากขวา (เพราะ reverse) */
    border: 2px dashed #10b981;
    padding: 1rem;
  }

  /* flex-direction: column-reverse */
  .column-reverse-justify-end {
    display: flex;
    flex-direction: column-reverse;
    justify-content: flex-end; /* ลงไปด้านบน (เพราะ reverse) */
    border: 2px dashed #f59e0b;
    height: 200px;
    padding: 1rem;
  }
}
```

## 3. align-items: การจัดวางตาม Cross Axis

### ความหมายและ Values

`align-items` ควบคุมการจัดวาง flex items ตาม **Cross Axis**

```css
/* align-items values */
.align-items-examples {
  /* stretch (ค่าเริ่มต้น) */
  .align-stretch {
    display: flex;
    align-items: stretch; /* ยืดเต็ม cross axis */
    height: 120px;
    border: 2px solid #6b7280;
    padding: 1rem;
    margin-bottom: 1rem;
  }

  /* flex-start */
  .align-start {
    display: flex;
    align-items: flex-start; /* จัดไปต้น cross axis */
    height: 120px;
    border: 2px solid #6b7280;
    padding: 1rem;
    margin-bottom: 1rem;
  }

  /* flex-end */
  .align-end {
    display: flex;
    align-items: flex-end; /* จัดไปท้าย cross axis */
    height: 120px;
    border: 2px solid #6b7280;
    padding: 1rem;
    margin-bottom: 1rem;
  }

  /* center */
  .align-center {
    display: flex;
    align-items: center; /* จัดกึ่งกลาง cross axis */
    height: 120px;
    border: 2px solid #6b7280;
    padding: 1rem;
    margin-bottom: 1rem;
  }

  /* baseline */
  .align-baseline {
    display: flex;
    align-items: baseline; /* จัดตาม baseline ของ text */
    height: 120px;
    border: 2px solid #6b7280;
    padding: 1rem;
    margin-bottom: 1rem;
  }
}

/* การใช้งานจริง */
.practical-align {
  /* Card layout */
  .card {
    display: flex;
    align-items: center;
    padding: 1.5rem;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    margin-bottom: 1rem;
  }

  .card-avatar {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    margin-right: 1rem;
    flex-shrink: 0;
  }

  .card-content {
    flex: 1;
  }

  .card-actions {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  /* Vertical navigation */
  .sidebar {
    display: flex;
    flex-direction: column;
    align-items: stretch; /* menu items เต็มความกว้าง */
    width: 250px;
    height: 100vh;
    background: #f8fafc;
    padding: 1rem 0;
  }

  .sidebar .menu-item {
    padding: 0.75rem 1.5rem;
    text-decoration: none;
    color: #374151;
    border-bottom: 1px solid #e5e7eb;
  }

  .sidebar .menu-item:hover {
    background: #e5e7eb;
  }

  /* Hero section */
  .hero {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    text-align: center;
  }

  /* Modal dialog */
  .modal-overlay {
    display: flex;
    align-items: center;
    justify-content: center;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.5);
  }

  .modal-content {
    background: white;
    border-radius: 0.5rem;
    padding: 2rem;
    max-width: 90vw;
    max-height: 90vh;
  }
}
```

### align-items กับ flex-direction ต่างๆ

```css
/* ผลของ align-items ใน flex-direction ต่างๆ */
.align-with-direction {
  /* flex-direction: row */
  .row-align-center {
    display: flex;
    flex-direction: row;
    align-items: center; /* จัดกึ่งกลางแนวตั้ง */
    height: 120px;
    border: 2px dashed #ef4444;
    padding: 1rem;
  }

  /* flex-direction: column */
  .column-align-center {
    display: flex;
    flex-direction: column;
    align-items: center; /* จัดกึ่งกลางแนวนอน */
    width: 300px;
    height: 200px;
    border: 2px dashed #3b82f6;
    padding: 1rem;
  }

  /* flex-direction: row + ความสูงต่างกัน */
  .row-different-heights {
    display: flex;
    align-items: baseline; /* จัดตาม text baseline */
    border: 2px dashed #10b981;
    padding: 1rem;
  }

  .row-different-heights .item-1 {
    font-size: 1rem;
    padding: 0.5rem;
  }

  .row-different-heights .item-2 {
    font-size: 1.5rem;
    padding: 1rem;
  }

  .row-different-heights .item-3 {
    font-size: 2rem;
    padding: 1.5rem;
  }
}
```

## 4. Perfect Centering: การจัดกึ่งกลางอย่างสมบูรณ์

### Horizontal และ Vertical Centering

```css
/* 🎯 Perfect centering ด้วย Flexbox */
.perfect-center {
  display: flex;
  justify-content: center; /* จัดกึ่งกลาง main axis */
  align-items: center; /* จัดกึ่งกลาง cross axis */
  height: 100vh; /* ต้องมีความสูง */
}

/* การใช้งานจริง */
.centering-examples {
  /* Loading screen */
  .loading-screen {
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(255, 255, 255, 0.9);
    z-index: 9999;
  }

  .spinner {
    width: 40px;
    height: 40px;
    border: 4px solid #f3f4f6;
    border-top: 4px solid #3b82f6;
    border-radius: 50%;
    animation: spin 1s linear infinite;
  }

  /* Error message */
  .error-container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    height: 50vh;
    text-align: center;
    color: #6b7280;
  }

  .error-icon {
    font-size: 4rem;
    margin-bottom: 1rem;
    color: #ef4444;
  }

  /* Login form */
  .login-container {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background: #f8fafc;
  }

  .login-form {
    background: white;
    padding: 2rem;
    border-radius: 0.5rem;
    box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
    width: 100%;
    max-width: 400px;
  }

  /* Card in grid */
  .card-center {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    height: 200px;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    text-align: center;
    padding: 1rem;
  }

  /* Icon with text */
  .icon-text-center {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 0.5rem;
    padding: 0.75rem 1.5rem;
    background: #3b82f6;
    color: white;
    border-radius: 0.375rem;
    text-decoration: none;
  }
}
```

### Different Centering Scenarios

```css
/* ตัวอย่างการ center ในสถานการณ์ต่างๆ */
.centering-scenarios {
  /* ข้อความใน button */
  .button-center {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 44px; /* มาตรฐาน touch target */
    padding: 0 1.5rem;
    background: #3b82f6;
    color: white;
    border: none;
    border-radius: 0.375rem;
    cursor: pointer;
  }

  /* Avatar กับ text */
  .user-info {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 1rem;
  }

  .avatar {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    flex-shrink: 0;
  }

  .user-details {
    flex: 1;
  }

  /* Badge */
  .badge {
    display: inline-flex;
    justify-content: center;
    align-items: center;
    min-width: 1.5rem;
    height: 1.5rem;
    padding: 0 0.5rem;
    background: #ef4444;
    color: white;
    border-radius: 0.75rem;
    font-size: 0.75rem;
    font-weight: 600;
  }

  /* Empty state */
  .empty-state {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    height: 300px;
    border: 2px dashed #d1d5db;
    border-radius: 0.5rem;
    color: #6b7280;
    text-align: center;
  }

  .empty-icon {
    font-size: 3rem;
    margin-bottom: 1rem;
    opacity: 0.5;
  }

  /* Notification toast */
  .toast {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    padding: 1rem;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
    margin-bottom: 0.5rem;
    min-width: 300px;
  }

  .toast-icon {
    width: 1.5rem;
    height: 1.5rem;
    flex-shrink: 0;
  }

  .toast-content {
    flex: 1;
  }

  .toast-close {
    width: 1rem;
    height: 1rem;
    cursor: pointer;
    opacity: 0.5;
    flex-shrink: 0;
  }
}
```

## 5. Responsive Flexbox: การปรับตัวใน Breakpoints ต่างๆ

### Mobile-First Approach

```css
/* Responsive flexbox patterns */
.responsive-flex {
  /* Mobile first: column layout */
  .responsive-container {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    padding: 1rem;
  }

  /* Tablet: row layout */
  @media (min-width: 768px) {
    .responsive-container {
      flex-direction: row;
      align-items: stretch;
      gap: 2rem;
      padding: 2rem;
    }
  }

  /* Card grid responsive */
  .card-grid {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  @media (min-width: 640px) {
    .card-grid {
      flex-direction: row;
      flex-wrap: wrap;
    }

    .card-grid .card {
      flex: 1 1 calc(50% - 0.5rem);
    }
  }

  @media (min-width: 1024px) {
    .card-grid .card {
      flex: 1 1 calc(33.333% - 0.667rem);
    }
  }

  /* Navigation responsive */
  .nav-responsive {
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }

  @media (min-width: 768px) {
    .nav-responsive {
      flex-direction: row;
      align-items: center;
      justify-content: space-between;
    }
  }

  /* Sidebar responsive */
  .layout-responsive {
    display: flex;
    flex-direction: column;
  }

  .sidebar-responsive {
    order: 2; /* sidebar ใต้ content ใน mobile */
  }

  .main-responsive {
    order: 1;
  }

  @media (min-width: 1024px) {
    .layout-responsive {
      flex-direction: row;
    }

    .sidebar-responsive {
      order: 1;
      flex: 0 0 250px;
    }

    .main-responsive {
      order: 2;
      flex: 1;
    }
  }
}
```

### Direction Changes

```css
/* การเปลี่ยน direction ตาม breakpoint */
.direction-responsive {
  /* Hero section */
  .hero-responsive {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 2rem 1rem;
    gap: 2rem;
  }

  @media (min-width: 768px) {
    .hero-responsive {
      flex-direction: row;
      text-align: left;
      padding: 4rem 2rem;
    }

    .hero-content {
      flex: 1;
    }

    .hero-image {
      flex: 0 0 40%;
    }
  }

  /* Feature list */
  .features-responsive {
    display: flex;
    flex-direction: column;
    gap: 2rem;
    padding: 2rem 1rem;
  }

  @media (min-width: 768px) {
    .features-responsive {
      flex-direction: row;
      flex-wrap: wrap;
    }

    .feature-item {
      flex: 1 1 calc(50% - 1rem);
    }
  }

  @media (min-width: 1024px) {
    .feature-item {
      flex: 1 1 calc(33.333% - 1.333rem);
    }
  }

  /* Stats section */
  .stats-responsive {
    display: flex;
    flex-direction: column;
    text-align: center;
    gap: 1.5rem;
    padding: 2rem 1rem;
  }

  @media (min-width: 640px) {
    .stats-responsive {
      flex-direction: row;
      justify-content: space-around;
    }

    .stat-item {
      flex: 1;
    }
  }
}
```

## 6. Common Flexbox Patterns

### Layout Patterns

```css
/* รูปแบบ layout ที่ใช้บ่อย */
.common-patterns {
  /* Header layout */
  .header-pattern {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  /* Card layout */
  .card-pattern {
    display: flex;
    flex-direction: column;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;
  }

  /* Equal-height cards container */
  .cards-equal-height {
    display: flex;
    gap: 1.5rem;
    align-items: stretch; /* สำคัญ! ทำให้ cards สูงเท่ากัน */
  }

  .card {
    flex: 1;
    display: flex;
    flex-direction: column;
  }

  .card-content {
    flex: 1; /* ขยายเต็มพื้นที่ที่เหลือ */
  }

  .card-footer {
    margin-top: auto; /* ผลักไปด้านล่างเสมอ */
  }

  /* Sidebar layout */
  .app-layout {
    display: flex;
    min-height: 100vh;
  }

  .sidebar-pattern {
    flex: 0 0 250px;
    background: #f8fafc;
    border-right: 1px solid #e5e7eb;
    display: flex;
    flex-direction: column;
  }

  .sidebar-header {
    padding: 1.5rem;
    border-bottom: 1px solid #e5e7eb;
    font-weight: 600;
  }

  .sidebar-nav {
    flex: 1;
    padding: 1rem 0;
  }

  .sidebar-footer {
    padding: 1rem 1.5rem;
    border-top: 1px solid #e5e7eb;
    margin-top: auto;
  }

  .main-content-pattern {
    flex: 1;
    display: flex;
    flex-direction: column;
  }

  .content-header {
    padding: 2rem;
    border-bottom: 1px solid #e5e7eb;
    background: white;
  }

  .content-body {
    flex: 1;
    padding: 2rem;
    overflow-y: auto;
  }

  /* Dashboard grid */
  .dashboard-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 1.5rem;
    padding: 2rem;
  }

  .dashboard-card {
    flex: 1 1 calc(50% - 0.75rem);
    min-width: 300px;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    padding: 1.5rem;
  }

  @media (min-width: 1024px) {
    .dashboard-card {
      flex: 1 1 calc(33.333% - 1rem);
    }
  }

  @media (min-width: 1400px) {
    .dashboard-card {
      flex: 1 1 calc(25% - 1.125rem);
    }
  }
}
```

### Component Patterns

```css
/* รูปแบบ components ที่ใช้บ่อย */
.component-patterns {
  /* Form layout */
  .form-row {
    display: flex;
    gap: 1rem;
    margin-bottom: 1rem;
  }

  .form-group {
    flex: 1;
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
  }

  /* Button group */
  .button-group-pattern {
    display: flex;
    gap: 0.5rem;
  }

  .button-group-pattern .btn {
    flex: 1;
    padding: 0.75rem 1.5rem;
    border: 1px solid #d1d5db;
    background: white;
    border-radius: 0.375rem;
    cursor: pointer;
    transition: all 0.2s;
  }

  .button-group-pattern .btn:hover {
    background: #f3f4f6;
  }

  .button-group-pattern .btn.active {
    background: #3b82f6;
    color: white;
    border-color: #3b82f6;
  }

  /* Media object */
  .media-object {
    display: flex;
    gap: 1rem;
    padding: 1rem;
  }

  .media-image {
    flex-shrink: 0;
    width: 60px;
    height: 60px;
    border-radius: 50%;
    object-fit: cover;
  }

  .media-content {
    flex: 1;
    min-width: 0; /* ป้องกัน flex item overflow */
  }

  .media-title {
    font-weight: 600;
    margin-bottom: 0.25rem;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .media-description {
    color: #6b7280;
    font-size: 0.875rem;
    line-height: 1.4;
  }

  /* Notification */
  .notification-pattern {
    display: flex;
    align-items: flex-start;
    gap: 0.75rem;
    padding: 1rem;
    background: white;
    border-left: 4px solid #3b82f6;
    border-radius: 0.375rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    margin-bottom: 1rem;
  }

  .notification-icon {
    flex-shrink: 0;
    width: 1.5rem;
    height: 1.5rem;
    margin-top: 0.125rem;
  }

  .notification-content {
    flex: 1;
    min-width: 0;
  }

  .notification-title {
    font-weight: 600;
    margin-bottom: 0.25rem;
    color: #1f2937;
  }

  .notification-message {
    color: #6b7280;
    font-size: 0.875rem;
    line-height: 1.5;
  }

  .notification-close {
    flex-shrink: 0;
    width: 1.25rem;
    height: 1.25rem;
    cursor: pointer;
    opacity: 0.5;
    transition: opacity 0.2s;
  }

  .notification-close:hover {
    opacity: 1;
  }
}
```

> **📖 เรียนรู้เพิ่มเติม**: สำหรับ patterns ที่ใช้บ่อยเช่น Navbar และ Equal-Height Cards โดยละเอียด ดูได้ที่ [Flexbox Common Patterns Guide](./06_Flexbox_Common_Patterns_Guide.md)

## 7. Flexbox Best Practices

### Performance และ Accessibility

```css
/* การเขียน Flexbox ที่มีประสิทธิภาพ */
.flexbox-best-practices {
  /* ✅ ใช้ gap แทน margin */
  .good-spacing {
    display: flex;
    gap: 1rem; /* ดีกว่า margin */
  }

  /* ❌ หลีกเลี่ยง margin ระหว่าง flex items */
  .avoid-margins .item {
    margin-right: 1rem; /* หลีกเลี่ยง */
  }

  /* ✅ ใช้ min-width: 0 สำหรับ text overflow */
  .text-overflow-fix {
    display: flex;
    align-items: center;
    gap: 1rem;
  }

  .text-content {
    flex: 1;
    min-width: 0; /* จำเป็นสำหรับ text overflow */
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  /* ✅ ใช้ semantic HTML */
  .semantic-flex {
    /* ใช้ nav สำหรับ navigation */
    nav {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    /* ใช้ ul/li สำหรับ menu */
    ul {
      display: flex;
      list-style: none;
      gap: 1rem;
      margin: 0;
      padding: 0;
    }

    /* ใช้ button สำหรับ interactive elements */
    button {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
    }
  }

  /* ✅ Accessibility considerations */
  .accessible-flex {
    /* Focus management */
    .focusable:focus {
      outline: 2px solid #3b82f6;
      outline-offset: 2px;
    }

    /* Screen reader support */
    .sr-only {
      position: absolute;
      width: 1px;
      height: 1px;
      padding: 0;
      margin: -1px;
      overflow: hidden;
      clip: rect(0, 0, 0, 0);
      white-space: nowrap;
      border: 0;
    }

    /* Skip links */
    .skip-link {
      position: absolute;
      top: -40px;
      left: 6px;
      background: #000;
      color: #fff;
      padding: 8px;
      text-decoration: none;
      z-index: 1000;
    }

    .skip-link:focus {
      top: 6px;
    }
  }
}
```

### Common Mistakes และ Solutions

```css
/* ปัญหาที่พบบ่อยและวิธีแก้ */
.common-mistakes {
  /* ❌ ปัญหา: flex items ไม่เท่ากัน */
  .unequal-items {
    display: flex;
    gap: 1rem;
  }

  .unequal-items .item {
    flex: 1; /* อาจไม่เท่ากันถ้ามี content ต่างกัน */
  }

  /* ✅ แก้ไข: ใช้ flex-basis */
  .equal-items {
    display: flex;
    gap: 1rem;
  }

  .equal-items .item {
    flex: 1 1 0; /* หรือ flex-basis: 0 */
  }

  /* ❌ ปัญหา: overflow ใน flex container */
  .overflow-problem {
    display: flex;
    width: 300px;
  }

  .overflow-problem .long-content {
    flex: 1;
    /* content ยาวจะทำให้ container กว้างเกิน */
  }

  /* ✅ แก้ไข: ใช้ min-width: 0 */
  .overflow-solution {
    display: flex;
    width: 300px;
  }

  .overflow-solution .long-content {
    flex: 1;
    min-width: 0; /* อนุญาตให้เล็กได้ */
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }

  /* ❌ ปัญหา: การใช้ height: 100% */
  .height-problem {
    display: flex;
    flex-direction: column;
    height: 100%; /* ไม่ทำงานถ้า parent ไม่มี height */
  }

  /* ✅ แก้ไข: ใช้ min-height: 100vh */
  .height-solution {
    display: flex;
    flex-direction: column;
    min-height: 100vh; /* หรือใช้ height กับ parent */
  }

  /* ❌ ปัญหา: การ center ที่ไม่สมบูรณ์ */
  .incomplete-center {
    display: flex;
    justify-content: center; /* center เฉพาะแนวนอน */
    height: 200px;
  }

  /* ✅ แก้ไข: center ทั้งสองแกน */
  .complete-center {
    display: flex;
    justify-content: center;
    align-items: center; /* center ทั้งสองแกน */
    height: 200px;
  }
}
```

## สรุป: Key Concepts ของ Flexbox

### แนวคิดสำคัญ 🎯

1. **Main Axis และ Cross Axis เป็นพื้นฐาน**

   - `flex-direction` กำหนด Main Axis
   - `justify-content` ควบคุม Main Axis
   - `align-items` ควบคุม Cross Axis

2. **Perfect Centering**

   ```css
   .center {
     display: flex;
     justify-content: center;
     align-items: center;
   }
   ```

3. **Responsive Design**

   - เปลี่ยน `flex-direction` ตาม breakpoint
   - ใช้ `flex-wrap` สำหรับ responsive grid
   - Mobile-first approach

4. **Best Practices**

   - ใช้ `gap` แทน `margin`
   - ใช้ `min-width: 0` สำหรับ text overflow
   - พิจารณา semantic HTML และ accessibility

5. **Common Patterns**
   - Navbar: `justify-content: space-between` + `align-items: center`
   - Equal-Height Cards: `align-items: stretch` + `flex-direction: column`
   - Perfect Centering: `justify-content: center` + `align-items: center`

### Related Guides 📚

- [Container Properties Guide](./04_Flexbox_Container_Properties_Guide.md) - คู่มือ properties สำหรับ container
- [Item Properties Guide](./05_Flexbox_Item_Properties_Guide.md) - คู่มือ properties สำหรับ items
- [Common Patterns Guide](./06_Flexbox_Common_Patterns_Guide.md) - รูปแบบการใช้งานที่นิยม

Flexbox เป็นเครื่องมือที่ทรงพลังสำหรับการสร้าง layout ที่ยืดหยุ่น responsive และเข้าใจได้ง่าย การเข้าใจแนวคิด Main Axis และ Cross Axis จะช่วยให้คุณใช้ Flexbox ได้อย่างมีประสิทธิภาพ!
justify-content: center;
align-items: center;
}

```

3. **Responsive Design**

- เปลี่ยน `flex-direction` ตาม breakpoint
- ใช้ `flex-wrap` สำหรับ responsive grid
- Mobile-first approach

4. **Best Practices**
- ใช้ `gap` แทน `margin`
- ใช้ `min-width: 0` สำหรับ text overflow
- พิจารณา semantic HTML และ accessibility

Flexbox เป็นเครื่องมือที่ทรงพลังสำหรับการสร้าง layout ที่ยืดหยุ่น responsive และเข้าใจได้ง่าย การเข้าใจแนวคิด Main Axis และ Cross Axis จะช่วยให้คุณใช้ Flexbox ได้อย่างมีประสิทธิภาพ!
```
