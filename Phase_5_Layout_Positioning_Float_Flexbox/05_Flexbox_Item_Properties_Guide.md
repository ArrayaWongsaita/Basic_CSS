# Flexbox Item Properties: คู่มือฉบับสมบูรณ์

## ภาพรวม Item Properties

Flexbox Item Properties เป็น CSS properties ที่ใช้กับ **flex items** (child elements) เพื่อควบคุมพฤติกรรมการขยาย หด จัดวาง และลำดับของแต่ละ item ภายใน flex container

### Properties ทั้งหมดสำหรับ Flex Items

```css
.flex-item {
  /* 1. การขยายตัวเมื่อมี space เหลือ */
  flex-grow: <number>; /* ค่าเริ่มต้น: 0 */

  /* 2. การหดตัวเมื่อ space ไม่พอ */
  flex-shrink: <number>; /* ค่าเริ่มต้น: 1 */

  /* 3. ขนาดเริ่มต้นก่อนการขยาย/หด */
  flex-basis: <length> | auto | content; /* ค่าเริ่มต้น: auto */

  /* 4. ลำดับการแสดงผล */
  order: <integer>; /* ค่าเริ่มต้น: 0 */

  /* 5. การจัดวางตาม cross axis สำหรับ item นี้เท่านั้น */
  align-self: auto | flex-start | flex-end | center | baseline | stretch;

  /* 6. Shorthand สำหรับ flex-grow, flex-shrink, flex-basis */
  flex: none | auto | <flex-grow> <flex-shrink> <flex-basis>;
}
```

## 1. flex-grow: การขยายตัวเมื่อมี Space เหลือ 📈

### ความหมายและการทำงาน

`flex-grow` กำหนดสัดส่วนการขยายตัวของ flex item เมื่อมี space เหลือใน container

```css
/* Basic flex-grow examples */
.flex-grow-examples {
  .container {
    display: flex;
    background: #f8fafc;
    border: 2px solid #6b7280;
    padding: 1rem;
    margin-bottom: 1rem;
    height: 100px;
  }

  /* flex-grow: 0 (ค่าเริ่มต้น) - ไม่ขยาย */
  .item-no-grow {
    flex-grow: 0;
    background: #fee2e2;
    border: 1px solid #ef4444;
    padding: 1rem;
    margin: 0.25rem;
  }

  /* flex-grow: 1 - ขยายได้ */
  .item-grow-1 {
    flex-grow: 1;
    background: #dbeafe;
    border: 1px solid #3b82f6;
    padding: 1rem;
    margin: 0.25rem;
  }

  /* flex-grow: 2 - ขยายได้ 2 เท่า */
  .item-grow-2 {
    flex-grow: 2;
    background: #dcfce7;
    border: 1px solid #22c55e;
    padding: 1rem;
    margin: 0.25rem;
  }
}
```

### การคำนวณสัดส่วน

```css
/* การคำนวณ flex-grow */
.grow-calculation {
  /* Container กว้าง 600px, items รวม 200px, space เหลือ 400px */
  .container {
    display: flex;
    width: 600px;
    background: #f1f5f9;
    padding: 1rem;
  }

  /* Item A: flex-grow: 1 - ได้ 1/4 ของ space เหลือ = 100px */
  .item-a {
    flex-grow: 1; /* 1 ส่วน */
    width: 50px; /* ขนาดเริ่มต้น */
    background: #fecaca;
    /* ขนาดสุดท้าย: 50px + 100px = 150px */
  }

  /* Item B: flex-grow: 2 - ได้ 2/4 ของ space เหลือ = 200px */
  .item-b {
    flex-grow: 2; /* 2 ส่วน */
    width: 50px;
    background: #fed7aa;
    /* ขนาดสุดท้าย: 50px + 200px = 250px */
  }

  /* Item C: flex-grow: 1 - ได้ 1/4 ของ space เหลือ = 100px */
  .item-c {
    flex-grow: 1; /* 1 ส่วน */
    width: 100px;
    background: #d9f99d;
    /* ขนาดสุดท้าย: 100px + 100px = 200px */
  }

  /* รวม flex-grow: 1 + 2 + 1 = 4 ส่วน */
}
```

### การใช้งานจริง

```css
/* การใช้งานจริงของ flex-grow */
.practical-grow {
  /* Sidebar layout */
  .app-layout {
    display: flex;
    min-height: 100vh;
  }

  .sidebar {
    flex-grow: 0; /* ไม่ขยาย - ขนาดคงที่ */
    flex-basis: 250px;
    background: #f8fafc;
    border-right: 1px solid #e5e7eb;
  }

  .main-content {
    flex-grow: 1; /* ขยายเต็ม space ที่เหลือ */
    padding: 2rem;
    background: white;
  }

  /* Dashboard cards */
  .dashboard-row {
    display: flex;
    gap: 1rem;
    margin-bottom: 1rem;
  }

  .card-small {
    flex-grow: 1; /* ขยายเท่าๆ กัน */
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    padding: 1.5rem;
  }

  .card-large {
    flex-grow: 2; /* ขยายได้ 2 เท่า */
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    padding: 1.5rem;
  }

  /* Form layout */
  .form-row {
    display: flex;
    gap: 1rem;
    margin-bottom: 1rem;
  }

  .form-group-small {
    flex-grow: 1; /* ขยายปกติ */
  }

  .form-group-large {
    flex-grow: 2; /* ขยายได้มากกว่า */
  }

  /* Navigation tabs */
  .tab-nav {
    display: flex;
    background: #f1f5f9;
    border-radius: 0.5rem;
    padding: 0.25rem;
  }

  .tab-item {
    flex-grow: 1; /* แต่ละ tab ขยายเท่าๆ กัน */
    text-align: center;
    padding: 0.75rem;
    border-radius: 0.25rem;
    cursor: pointer;
    color: #6b7280;
    font-weight: 500;
  }

  .tab-item.active {
    background: white;
    color: #3b82f6;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }
}
```

## 2. flex-shrink: การหดตัวเมื่อ Space ไม่พอ 📉

### ความหมายและการทำงาน

`flex-shrink` กำหนดสัดส่วนการหดตัวของ flex item เมื่อ space ใน container ไม่เพียงพอ

```css
/* Basic flex-shrink examples */
.flex-shrink-examples {
  .container {
    display: flex;
    width: 300px; /* Container แคบ */
    background: #f8fafc;
    border: 2px solid #6b7280;
    padding: 1rem;
    margin-bottom: 1rem;
  }

  /* flex-shrink: 0 - ไม่หด (อาจ overflow) */
  .item-no-shrink {
    flex-shrink: 0;
    flex-basis: 150px;
    background: #fee2e2;
    border: 1px solid #ef4444;
    padding: 0.5rem;
    margin: 0.25rem;
  }

  /* flex-shrink: 1 (ค่าเริ่มต้น) - หดได้ปกติ */
  .item-shrink-1 {
    flex-shrink: 1;
    flex-basis: 150px;
    background: #dbeafe;
    border: 1px solid #3b82f6;
    padding: 0.5rem;
    margin: 0.25rem;
  }

  /* flex-shrink: 2 - หดได้มากกว่า */
  .item-shrink-2 {
    flex-shrink: 2;
    flex-basis: 150px;
    background: #dcfce7;
    border: 1px solid #22c55e;
    padding: 0.5rem;
    margin: 0.25rem;
  }
}
```

### การคำนวณการหด

```css
/* การคำนวณ flex-shrink */
.shrink-calculation {
  /* Container กว้าง 200px, items ต้องการรวม 300px, ต้องหด 100px */
  .container {
    display: flex;
    width: 200px;
    background: #f1f5f9;
    padding: 1rem;
  }

  /* Item A: flex-basis: 100px, flex-shrink: 1 */
  .item-a {
    flex-shrink: 1; /* หด 1 ส่วน */
    flex-basis: 100px;
    background: #fecaca;
    /* การหด: (100 * 1) / (100*1 + 100*2 + 100*1) = 25px */
    /* ขนาดสุดท้าย: 100px - 25px = 75px */
  }

  /* Item B: flex-basis: 100px, flex-shrink: 2 */
  .item-b {
    flex-shrink: 2; /* หด 2 ส่วน */
    flex-basis: 100px;
    background: #fed7aa;
    /* การหด: (100 * 2) / 400 * 100px = 50px */
    /* ขนาดสุดท้าย: 100px - 50px = 50px */
  }

  /* Item C: flex-basis: 100px, flex-shrink: 1 */
  .item-c {
    flex-shrink: 1; /* หด 1 ส่วน */
    flex-basis: 100px;
    background: #d9f99d;
    /* การหด: (100 * 1) / 400 * 100px = 25px */
    /* ขนาดสุดท้าย: 100px - 25px = 75px */
  }
}
```

### การใช้งานจริง

```css
/* การใช้งานจริงของ flex-shrink */
.practical-shrink {
  /* Navigation bar responsive */
  .navbar {
    display: flex;
    align-items: center;
    padding: 1rem 2rem;
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .logo {
    flex-shrink: 0; /* ไม่ให้ logo หด */
    font-size: 1.5rem;
    font-weight: bold;
    margin-right: 2rem;
  }

  .nav-menu {
    flex-shrink: 1; /* ให้ menu หดได้ */
    display: flex;
    gap: 1.5rem;
    list-style: none;
    margin: 0;
    padding: 0;
  }

  .user-actions {
    flex-shrink: 0; /* ไม่ให้ user actions หด */
    display: flex;
    align-items: center;
    gap: 1rem;
    margin-left: auto;
  }

  /* Card content */
  .product-card {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 1rem;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .product-image {
    flex-shrink: 0; /* รูปไม่หด */
    width: 80px;
    height: 80px;
    border-radius: 0.5rem;
    object-fit: cover;
  }

  .product-info {
    flex-shrink: 1; /* ข้อมูลหดได้ */
    min-width: 0; /* สำคัญ! ให้ text overflow ทำงาน */
  }

  .product-title {
    font-weight: 600;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .product-price {
    flex-shrink: 0; /* ราคาไม่หด */
    font-size: 1.25rem;
    font-weight: bold;
    color: #3b82f6;
    margin-left: auto;
  }

  /* Breadcrumb navigation */
  .breadcrumb {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 1rem;
    background: #f8fafc;
    border-radius: 0.5rem;
    overflow: hidden;
  }

  .breadcrumb-item {
    flex-shrink: 1; /* items หดได้ */
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    color: #6b7280;
    text-decoration: none;
  }

  .breadcrumb-item:last-child {
    flex-shrink: 0; /* item สุดท้ายไม่หด */
    color: #1f2937;
    font-weight: 500;
  }

  .breadcrumb-separator {
    flex-shrink: 0; /* separator ไม่หด */
    color: #d1d5db;
  }
}
```

## 3. flex-basis: ขนาดเริ่มต้นก่อนการขยาย/หด 📏

### ความหมายและการทำงาน

`flex-basis` กำหนดขนาดเริ่มต้นของ flex item ก่อนที่จะมีการขยายหรือหดตัว

```css
/* Basic flex-basis examples */
.flex-basis-examples {
  .container {
    display: flex;
    background: #f8fafc;
    border: 2px solid #6b7280;
    padding: 1rem;
    margin-bottom: 1rem;
  }

  /* flex-basis: auto (ค่าเริ่มต้น) - ใช้ขนาดของ content */
  .item-auto {
    flex-basis: auto;
    background: #fee2e2;
    border: 1px solid #ef4444;
    padding: 1rem;
    margin: 0.25rem;
  }

  /* flex-basis: 0 - ไม่มีขนาดเริ่มต้น */
  .item-zero {
    flex-basis: 0;
    flex-grow: 1;
    background: #dbeafe;
    border: 1px solid #3b82f6;
    padding: 1rem;
    margin: 0.25rem;
  }

  /* flex-basis: 200px - ขนาดเริ่มต้นแน่นอน */
  .item-fixed {
    flex-basis: 200px;
    background: #dcfce7;
    border: 1px solid #22c55e;
    padding: 1rem;
    margin: 0.25rem;
  }

  /* flex-basis: 50% - ขนาดเป็นเปอร์เซ็นต์ */
  .item-percent {
    flex-basis: 50%;
    background: #f3e8ff;
    border: 1px solid #a855f7;
    padding: 1rem;
    margin: 0.25rem;
  }

  /* flex-basis: content - ใช้ขนาดของ content (สำหรับ browser ใหม่) */
  .item-content {
    flex-basis: content;
    background: #fef3c7;
    border: 1px solid #f59e0b;
    padding: 1rem;
    margin: 0.25rem;
  }
}
```

### ความแตกต่างระหว่าง width กับ flex-basis

```css
/* width vs flex-basis */
.width-vs-basis {
  .container {
    display: flex;
    width: 600px;
    background: #f1f5f9;
    padding: 1rem;
  }

  /* ใช้ width - อาจไม่ flexible */
  .item-with-width {
    width: 200px; /* แข็งกระด้าง */
    background: #fecaca;
    padding: 1rem;
    margin: 0.25rem;
  }

  /* ใช้ flex-basis - flexible กว่า */
  .item-with-basis {
    flex-basis: 200px; /* สามารถขยาย/หดได้ */
    flex-grow: 1;
    flex-shrink: 1;
    background: #bae6fd;
    padding: 1rem;
    margin: 0.25rem;
  }

  /* ในกรณีนี้ item-with-basis จะขยายได้ แต่ item-with-width จะคงที่ */
}
```

### การใช้งานจริง

```css
/* การใช้งานจริงของ flex-basis */
.practical-basis {
  /* Responsive grid layout */
  .card-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    padding: 1rem;
  }

  .card {
    flex-basis: calc(33.333% - 0.667rem); /* 3 columns */
    flex-grow: 1;
    flex-shrink: 1;
    min-width: 280px; /* ขนาดขั้นต่ำ */
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    padding: 1.5rem;
  }

  @media (max-width: 768px) {
    .card {
      flex-basis: calc(50% - 0.5rem); /* 2 columns */
    }
  }

  @media (max-width: 480px) {
    .card {
      flex-basis: 100%; /* 1 column */
    }
  }

  /* Dashboard layout */
  .dashboard-container {
    display: flex;
    gap: 1.5rem;
    padding: 1.5rem;
  }

  .main-panel {
    flex-basis: 70%; /* เริ่มต้น 70% */
    flex-grow: 1;
    flex-shrink: 1;
  }

  .side-panel {
    flex-basis: 30%; /* เริ่มต้น 30% */
    flex-grow: 0;
    flex-shrink: 0;
    min-width: 250px;
    background: #f8fafc;
    border-radius: 0.5rem;
    padding: 1.5rem;
  }

  /* Form layout */
  .form-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
  }

  .form-group-full {
    flex-basis: 100%; /* เต็มแถว */
  }

  .form-group-half {
    flex-basis: calc(50% - 0.5rem); /* ครึ่งแถว */
  }

  .form-group-third {
    flex-basis: calc(33.333% - 0.667rem); /* หนึ่งในสาม */
  }

  /* Tab content */
  .tab-container {
    display: flex;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  .tab-sidebar {
    flex-basis: 200px; /* ความกว้างคงที่ */
    flex-shrink: 0;
    background: #f8fafc;
    border-right: 1px solid #e5e7eb;
    padding: 1rem;
  }

  .tab-content {
    flex-basis: 0; /* ให้ขยายเต็มที่ */
    flex-grow: 1;
    padding: 1.5rem;
  }
}
```

## 4. order: การกำหนดลำดับการแสดงผล 🔢

### ความหมายและการทำงาน

`order` กำหนดลำดับการแสดงผลของ flex items โดยไม่ต้องเปลี่ยน HTML structure

```css
/* Basic order examples */
.order-examples {
  .container {
    display: flex;
    background: #f8fafc;
    border: 2px solid #6b7280;
    padding: 1rem;
    margin-bottom: 1rem;
  }

  /* order: 0 (ค่าเริ่มต้น) */
  .item-1 {
    order: 3; /* แสดงเป็นอันดับที่ 3 */
    background: #fee2e2;
    border: 1px solid #ef4444;
    padding: 1rem;
    margin: 0.25rem;
  }

  .item-2 {
    order: 1; /* แสดงเป็นอันดับที่ 1 */
    background: #dbeafe;
    border: 1px solid #3b82f6;
    padding: 1rem;
    margin: 0.25rem;
  }

  .item-3 {
    order: 2; /* แสดงเป็นอันดับที่ 2 */
    background: #dcfce7;
    border: 1px solid #22c55e;
    padding: 1rem;
    margin: 0.25rem;
  }

  /* ผลลัพธ์: item-2, item-3, item-1 */
}

/* การใช้ negative order */
.negative-order {
  .container {
    display: flex;
    background: #f1f5f9;
    padding: 1rem;
  }

  .item-normal {
    order: 0; /* ปกติ */
    background: #e5e7eb;
    padding: 1rem;
    margin: 0.25rem;
  }

  .item-first {
    order: -1; /* แสดงก่อน order: 0 */
    background: #fecaca;
    padding: 1rem;
    margin: 0.25rem;
  }

  .item-last {
    order: 1; /* แสดงหลัง order: 0 */
    background: #bae6fd;
    padding: 1rem;
    margin: 0.25rem;
  }
}
```

### การใช้งานจริง

```css
/* การใช้งานจริงของ order */
.practical-order {
  /* Responsive layout reordering */
  .article-layout {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }

  .article-header {
    order: 1; /* Mobile: header ก่อน */
    background: white;
    padding: 1.5rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .article-content {
    order: 2; /* Mobile: content กลาง */
    background: white;
    padding: 1.5rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .article-sidebar {
    order: 3; /* Mobile: sidebar ล่าง */
    background: #f8fafc;
    padding: 1.5rem;
    border-radius: 0.5rem;
  }

  @media (min-width: 1024px) {
    .article-layout {
      flex-direction: row;
    }

    .article-header {
      order: 1;
      flex-basis: 100%;
    }

    .article-content {
      order: 2;
      flex: 1;
    }

    .article-sidebar {
      order: 3;
      flex-basis: 300px;
    }
  }

  /* Navigation reordering */
  .mobile-nav {
    display: flex;
    flex-direction: column;
  }

  .nav-logo {
    order: 1; /* Logo ก่อน */
    padding: 1rem;
    text-align: center;
    font-size: 1.5rem;
    font-weight: bold;
  }

  .nav-menu {
    order: 3; /* Menu หลัง */
    display: flex;
    flex-direction: column;
  }

  .nav-user {
    order: 2; /* User info กลาง */
    padding: 1rem;
    border-top: 1px solid #e5e7eb;
    border-bottom: 1px solid #e5e7eb;
  }

  @media (min-width: 768px) {
    .mobile-nav {
      flex-direction: row;
      align-items: center;
    }

    .nav-logo {
      order: 1;
      text-align: left;
    }

    .nav-menu {
      order: 2;
      flex-direction: row;
      flex: 1;
      justify-content: center;
    }

    .nav-user {
      order: 3;
      border: none;
      margin-left: auto;
    }
  }

  /* Card priority ordering */
  .dashboard-cards {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    padding: 1rem;
  }

  .card-primary {
    order: -1; /* แสดงก่อน */
    flex-basis: 100%;
    background: #3b82f6;
    color: white;
    padding: 1.5rem;
    border-radius: 0.5rem;
  }

  .card-secondary {
    order: 0; /* แสดงปกติ */
    flex: 1;
    min-width: calc(50% - 0.5rem);
    background: white;
    padding: 1.5rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .card-tertiary {
    order: 1; /* แสดงหลัง */
    flex-basis: 100%;
    background: #f8fafc;
    padding: 1.5rem;
    border-radius: 0.5rem;
  }

  /* Form field ordering */
  .form-responsive {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
  }

  .field-name {
    order: 1;
    flex-basis: 100%;
  }

  .field-email {
    order: 2;
    flex-basis: 100%;
  }

  .field-phone {
    order: 3;
    flex-basis: 100%;
  }

  .field-submit {
    order: 4;
    flex-basis: 100%;
  }

  @media (min-width: 768px) {
    .field-name {
      order: 1;
      flex-basis: calc(50% - 0.5rem);
    }

    .field-email {
      order: 2;
      flex-basis: calc(50% - 0.5rem);
    }

    .field-phone {
      order: 3;
      flex-basis: 100%;
    }

    .field-submit {
      order: 4;
      flex-basis: auto;
      margin-left: auto;
    }
  }
}
```

## 5. align-self: การจัดวางตาม Cross Axis สำหรับ Item เฉพาะ 🎯

### ความหมายและการทำงาน

`align-self` กำหนดการจัดวางตาม cross axis สำหรับ flex item เฉพาะตัว โดยจะ override ค่า `align-items` ของ container

```css
/* Basic align-self examples */
.align-self-examples {
  .container {
    display: flex;
    align-items: center; /* ค่าเริ่มต้นสำหรับทุก items */
    background: #f8fafc;
    border: 2px solid #6b7280;
    padding: 1rem;
    margin-bottom: 1rem;
    height: 150px;
  }

  /* align-self: auto (ค่าเริ่มต้น) - ใช้ค่าจาก align-items */
  .item-auto {
    align-self: auto; /* ใช้ center จาก container */
    background: #fee2e2;
    border: 1px solid #ef4444;
    padding: 1rem;
    margin: 0.25rem;
  }

  /* align-self: flex-start - จัดไปจุดเริ่มต้น cross axis */
  .item-start {
    align-self: flex-start;
    background: #dbeafe;
    border: 1px solid #3b82f6;
    padding: 1rem;
    margin: 0.25rem;
  }

  /* align-self: flex-end - จัดไปจุดสิ้นสุด cross axis */
  .item-end {
    align-self: flex-end;
    background: #dcfce7;
    border: 1px solid #22c55e;
    padding: 1rem;
    margin: 0.25rem;
  }

  /* align-self: center - จัดกึ่งกลาง cross axis */
  .item-center {
    align-self: center;
    background: #f3e8ff;
    border: 1px solid #a855f7;
    padding: 1rem;
    margin: 0.25rem;
  }

  /* align-self: stretch - ยืดเต็ม cross axis */
  .item-stretch {
    align-self: stretch;
    background: #fef3c7;
    border: 1px solid #f59e0b;
    padding: 1rem;
    margin: 0.25rem;
  }

  /* align-self: baseline - จัดตาม text baseline */
  .item-baseline {
    align-self: baseline;
    background: #ecfdf5;
    border: 1px solid #10b981;
    padding: 1rem;
    margin: 0.25rem;
    font-size: 1.5rem; /* ขนาดใหญ่เพื่อเห็นความแตกต่าง */
  }
}
```

### การใช้งานจริง

```css
/* การใช้งานจริงของ align-self */
.practical-align-self {
  /* Card layout with special items */
  .card-container {
    display: flex;
    align-items: stretch; /* ทุก cards ยืดเท่ากัน */
    gap: 1rem;
    padding: 1rem;
    min-height: 300px;
  }

  .card-normal {
    flex: 1;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    padding: 1.5rem;
  }

  .card-featured {
    align-self: flex-start; /* Card พิเศษไม่ยืด */
    flex: 1;
    background: #3b82f6;
    color: white;
    border-radius: 0.5rem;
    box-shadow: 0 8px 12px rgba(0, 0, 0, 0.15);
    padding: 1.5rem;
    position: relative;
  }

  .card-featured::before {
    content: 'Featured';
    position: absolute;
    top: -10px;
    right: 1rem;
    background: #ef4444;
    color: white;
    padding: 0.25rem 0.75rem;
    border-radius: 0.25rem;
    font-size: 0.75rem;
    font-weight: 600;
  }

  /* Navigation with user profile */
  .navbar-special {
    display: flex;
    align-items: center;
    padding: 1rem 2rem;
    background: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    min-height: 80px;
  }

  .nav-logo {
    font-size: 1.5rem;
    font-weight: bold;
    margin-right: 2rem;
  }

  .nav-menu {
    display: flex;
    gap: 2rem;
    list-style: none;
    margin: 0;
    padding: 0;
    flex: 1;
  }

  .nav-notification {
    align-self: flex-start; /* Notification อยู่ด้านบน */
    position: relative;
    background: #fee2e2;
    color: #991b1b;
    padding: 0.5rem;
    border-radius: 0.25rem;
    font-size: 0.875rem;
  }

  .nav-user {
    align-self: center; /* User profile อยู่กึ่งกลาง */
    display: flex;
    align-items: center;
    gap: 0.75rem;
  }

  .nav-user-avatar {
    width: 40px;
    height: 40px;
    border-radius: 50%;
  }

  /* Form with different field heights */
  .form-mixed {
    display: flex;
    align-items: flex-start; /* เริ่มต้นทุก fields ชิดบน */
    gap: 1rem;
    padding: 1rem;
  }

  .form-field {
    flex: 1;
    display: flex;
    flex-direction: column;
  }

  .form-field label {
    margin-bottom: 0.5rem;
    font-weight: 500;
  }

  .form-field input {
    padding: 0.75rem;
    border: 1px solid #d1d5db;
    border-radius: 0.375rem;
  }

  .form-field textarea {
    padding: 0.75rem;
    border: 1px solid #d1d5db;
    border-radius: 0.375rem;
    resize: vertical;
    min-height: 100px;
  }

  .form-submit {
    align-self: flex-end; /* Submit button อยู่ด้านล่าง */
    padding: 0.75rem 1.5rem;
    background: #3b82f6;
    color: white;
    border: none;
    border-radius: 0.375rem;
    cursor: pointer;
    margin-top: 1.5rem; /* เว้นระยะจาก label */
  }

  /* Stats dashboard */
  .stats-row {
    display: flex;
    align-items: stretch; /* ทุก stat cards ยืดเท่ากัน */
    gap: 1.5rem;
    padding: 1.5rem;
  }

  .stat-card {
    flex: 1;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    padding: 1.5rem;
    text-align: center;
  }

  .stat-card-highlight {
    align-self: flex-start; /* Highlight card ไม่ยืด */
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    transform: translateY(-10px); /* ยกขึ้นเล็กน้อย */
  }

  .stat-number {
    font-size: 2.5rem;
    font-weight: bold;
    margin-bottom: 0.5rem;
  }

  .stat-label {
    color: #6b7280;
    font-size: 0.875rem;
  }

  .stat-card-highlight .stat-label {
    color: rgba(255, 255, 255, 0.8);
  }

  /* Media object with different alignments */
  .media-list {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    padding: 1rem;
  }

  .media-item {
    display: flex;
    align-items: flex-start; /* เริ่มต้นชิดบน */
    gap: 1rem;
    padding: 1rem;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .media-avatar {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    flex-shrink: 0;
  }

  .media-content {
    flex: 1;
    min-width: 0;
  }

  .media-timestamp {
    align-self: flex-start; /* Timestamp อยู่บนสุด */
    color: #6b7280;
    font-size: 0.875rem;
    white-space: nowrap;
  }

  .media-actions {
    align-self: center; /* Actions อยู่กึ่งกลาง */
    display: flex;
    gap: 0.5rem;
  }

  .media-status {
    align-self: flex-end; /* Status อยู่ล่างสุด */
    background: #22c55e;
    color: white;
    padding: 0.25rem 0.5rem;
    border-radius: 0.75rem;
    font-size: 0.75rem;
  }
}
```

## 6. flex: Shorthand Property 🎭

### ความหมายและการใช้งาน

`flex` เป็น shorthand property ที่รวม `flex-grow`, `flex-shrink`, และ `flex-basis` เข้าด้วยกัน

```css
/* flex shorthand syntax */
.flex-shorthand {
  /* Syntax: flex: <grow> <shrink> <basis> */

  /* ค่าที่ใช้บ่อย */
  .flex-none {
    flex: none; /* เทียบเท่า flex: 0 0 auto - ไม่ขยาย ไม่หด */
  }

  .flex-auto {
    flex: auto; /* เทียบเท่า flex: 1 1 auto - ขยายหดได้ตาม content */
  }

  .flex-1 {
    flex: 1; /* เทียบเท่า flex: 1 1 0% - ขยายหดได้เท่าๆ กัน */
  }

  .flex-2 {
    flex: 2; /* เทียบเท่า flex: 2 1 0% - ขยายได้ 2 เท่า */
  }

  .flex-initial {
    flex: initial; /* เทียบเท่า flex: 0 1 auto - ค่าเริ่มต้น */
  }

  /* การระบุค่าแบบละเอียด */
  .custom-flex-1 {
    flex: 1 0 200px; /* grow: 1, shrink: 0, basis: 200px */
  }

  .custom-flex-2 {
    flex: 2 1 100px; /* grow: 2, shrink: 1, basis: 100px */
  }

  .custom-flex-3 {
    flex: 0 0 300px; /* grow: 0, shrink: 0, basis: 300px - fixed size */
  }
}
```

### การใช้งานจริงของ flex shorthand

```css
/* การใช้งานจริงของ flex */
.practical-flex {
  /* Layout patterns */
  .app-layout {
    display: flex;
    min-height: 100vh;
  }

  .sidebar {
    flex: none; /* ขนาดคงที่ */
    width: 250px;
    background: #f8fafc;
  }

  .main-content {
    flex: 1; /* ขยายเต็มพื้นที่ที่เหลือ */
    padding: 2rem;
  }

  /* Card layouts */
  .card-row {
    display: flex;
    gap: 1rem;
    margin-bottom: 1rem;
  }

  .card-equal {
    flex: 1; /* การ์ดขนาดเท่าๆ กัน */
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    padding: 1.5rem;
  }

  .card-double {
    flex: 2; /* การ์ดใหญ่ 2 เท่า */
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    padding: 1.5rem;
  }

  .card-fixed {
    flex: none; /* การ์ดขนาดคงที่ */
    width: 200px;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    padding: 1.5rem;
  }

  /* Form layouts */
  .form-flex {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
  }

  .field-full {
    flex: 1 1 100%; /* เต็มแถว */
  }

  .field-half {
    flex: 1 1 calc(50% - 0.5rem); /* ครึ่งแถว */
  }

  .field-auto {
    flex: auto; /* ปรับตาม content */
  }

  .field-fixed {
    flex: none; /* ขนาดคงที่ */
    width: 120px;
  }

  /* Button groups */
  .button-group {
    display: flex;
  }

  .btn-equal {
    flex: 1; /* ปุ่มขนาดเท่าๆ กัน */
    padding: 0.75rem;
    border: 1px solid #d1d5db;
    background: white;
    cursor: pointer;
  }

  .btn-primary {
    flex: 2; /* ปุ่มหลักใหญ่กว่า */
    padding: 0.75rem;
    background: #3b82f6;
    color: white;
    border: 1px solid #3b82f6;
    cursor: pointer;
  }

  .btn-icon {
    flex: none; /* ปุ่ม icon ขนาดคงที่ */
    width: 44px;
    height: 44px;
    background: #f3f4f6;
    border: 1px solid #d1d5db;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  /* Media objects */
  .media-object {
    display: flex;
    gap: 1rem;
    padding: 1rem;
  }

  .media-image {
    flex: none; /* รูปขนาดคงที่ */
    width: 80px;
    height: 80px;
    border-radius: 50%;
  }

  .media-content {
    flex: 1; /* เนื้อหาขยายเต็มที่ */
    min-width: 0; /* สำคัญสำหรับ text overflow */
  }

  .media-actions {
    flex: none; /* actions ขนาดคงที่ */
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }
}
```

## 7. Best Practices และ Common Patterns

### การใช้ Item Properties อย่างมีประสิทธิภาพ

```css
/* Best practices */
.best-practices {
  /* ✅ การใช้ flex shorthand */
  .good-flex {
    flex: 1; /* ดีกว่าการเขียนแยก */
    /* แทนที่จะเขียน:
    flex-grow: 1;
    flex-shrink: 1;
    flex-basis: 0%; */
  }

  /* ✅ การใช้ min-width กับ flex items */
  .text-container {
    flex: 1;
    min-width: 0; /* สำคัญ! ให้ text overflow ทำงาน */
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  /* ✅ การใช้ order สำหรับ responsive */
  .responsive-item {
    order: 1; /* Mobile order */
  }

  @media (min-width: 768px) {
    .responsive-item {
      order: 0; /* Desktop order */
    }
  }

  /* ✅ การใช้ align-self เฉพาะจุด */
  .special-item {
    align-self: flex-start; /* เฉพาะ item นี้ */
  }
}
```

### Common Patterns

```css
/* รูปแบบที่ใช้บ่อย */
.common-patterns {
  /* Equal height cards */
  .card-container {
    display: flex;
    gap: 1rem;
  }

  .card {
    flex: 1; /* ขนาดเท่าๆ กัน */
    display: flex;
    flex-direction: column;
  }

  .card-content {
    flex: 1; /* เนื้อหาขยายเต็มที่ */
  }

  .card-footer {
    flex: none; /* footer คงที่ */
    margin-top: auto;
  }

  /* Sticky footer layout */
  .page-layout {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }

  .page-header {
    flex: none; /* header คงที่ */
  }

  .page-main {
    flex: 1; /* main ขยายเต็มที่ */
  }

  .page-footer {
    flex: none; /* footer คงที่ */
  }

  /* Holy grail layout */
  .holy-grail {
    display: flex;
    min-height: 100vh;
    flex-direction: column;
  }

  .holy-grail-body {
    flex: 1;
    display: flex;
  }

  .holy-grail-nav {
    flex: none;
    order: -1; /* nav ก่อน main */
    width: 200px;
  }

  .holy-grail-content {
    flex: 1; /* content ขยายเต็มที่ */
  }

  .holy-grail-ads {
    flex: none;
    width: 150px;
  }
}
```

## สรุป: Item Properties Quick Reference

| Property      | ควบคุม            | ค่าที่ใช้บ่อย                  | การใช้งาน             |
| ------------- | ----------------- | ------------------------------ | --------------------- |
| `flex-grow`   | การขยายตัว        | `0`, `1`, `2`                  | กระจาย space          |
| `flex-shrink` | การหดตัว          | `0`, `1`, `2`                  | จัดการ overflow       |
| `flex-basis`  | ขนาดเริ่มต้น      | `auto`, `0`, `200px`, `50%`    | กำหนดขนาดฐาน          |
| `order`       | ลำดับแสดงผล       | `-1`, `0`, `1`, `2`            | เรียงลำดับ responsive |
| `align-self`  | จัดวาง cross axis | `auto`, `center`, `flex-start` | override align-items  |
| `flex`        | shorthand         | `1`, `auto`, `none`            | รวม grow/shrink/basis |

### การใช้งานร่วมกัน

```css
/* Responsive grid item */
.grid-item {
  flex: 1 1 calc(33.333% - 1rem); /* grow shrink basis */
  order: 0; /* ลำดับปกติ */
  align-self: stretch; /* ยืดเต็มความสูง */
}

@media (max-width: 768px) {
  .grid-item {
    flex: 1 1 100%; /* เต็มแถวใน mobile */
    order: 1; /* เปลี่ยนลำดับ */
  }
}

/* Flexible navigation */
.nav-item {
  flex: none; /* ขนาดคงที่ */
  order: 0; /* ลำดับปกติ */
}

.nav-item.logo {
  order: -1; /* logo ก่อนสุด */
  align-self: center; /* จัดกึ่งกลาง */
}

.nav-item.user {
  order: 1; /* user หลังสุด */
  margin-left: auto; /* ผลักไปขวา */
}
```

เมื่อเข้าใจ Item Properties ทั้ง 5 ตัวนี้แล้ว คุณจะสามารถควบคุมพฤติกรรมของแต่ละ flex item ได้อย่างละเอียดและยืดหยุ่น! 🎯
