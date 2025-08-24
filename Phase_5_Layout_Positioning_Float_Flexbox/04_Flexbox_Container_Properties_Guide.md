# Flexbox Container Properties: คู่มือฉบับสมบูรณ์

## ภาพรวม Container Properties

Flexbox Container Properties เป็น CSS properties ที่ใช้กับ **flex container** (parent element) เพื่อควบคุมการจัดวางและพฤติกรรมของ **flex items** (child elements)

### Properties ทั้งหมดสำหรับ Container

```css
.flex-container {
  /* 1. สร้าง flex container */
  display: flex | inline-flex;

  /* 2. กำหนดทิศทางของ main axis */
  flex-direction: row | row-reverse | column | column-reverse;

  /* 3. กำหนดการ wrap ของ items */
  flex-wrap: nowrap | wrap | wrap-reverse;

  /* 4. จัดวาง items ตาม main axis */
  justify-content: flex-start | flex-end | center | space-between | space-around
    | space-evenly;

  /* 5. จัดวาง items ตาม cross axis */
  align-items: stretch | flex-start | flex-end | center | baseline;

  /* 6. จัดวาง wrapped lines ตาม cross axis */
  align-content: stretch | flex-start | flex-end | center | space-between |
    space-around | space-evenly;

  /* 7. กำหนดระยะห่างระหว่าง items */
  gap: <length> | <percentage>;
  row-gap: <length> | <percentage>;
  column-gap: <length> | <percentage>;
}
```

## 1. display: การสร้าง Flex Container 🏗️

### ค่าต่างๆ ของ display

```css
/* display: flex - สร้าง block-level flex container */
.block-flex {
  display: flex;
  background: #dbeafe;
  border: 2px solid #3b82f6;
  padding: 1rem;
  margin-bottom: 1rem;
  /* container จะเต็มความกว้างของ parent */
}

/* display: inline-flex - สร้าง inline-level flex container */
.inline-flex {
  display: inline-flex;
  background: #dcfce7;
  border: 2px solid #22c55e;
  padding: 1rem;
  margin: 0 0.5rem;
  /* container จะปรับขนาดตาม content */
}
```

### การใช้งานจริง

```css
/* Navigation bar - ใช้ flex */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
  background: white;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

/* Button group - ใช้ inline-flex */
.button-group {
  display: inline-flex;
  border-radius: 0.375rem;
  overflow: hidden;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.button-group button {
  padding: 0.5rem 1rem;
  border: none;
  background: white;
  border-right: 1px solid #e5e7eb;
  cursor: pointer;
}

/* Badge component - ใช้ inline-flex */
.badge {
  display: inline-flex;
  align-items: center;
  gap: 0.25rem;
  padding: 0.25rem 0.5rem;
  background: #3b82f6;
  color: white;
  border-radius: 0.75rem;
  font-size: 0.75rem;
}
```

## 2. flex-direction: การกำหนดทิศทาง Main Axis 🧭

### ค่าต่างๆ และผลลัพธ์

```css
/* row (ค่าเริ่มต้น) - Main Axis: ซ้าย → ขวา */
.direction-row {
  display: flex;
  flex-direction: row;
  background: #fef3c7;
  padding: 1rem;
  border: 2px solid #f59e0b;
}

/* row-reverse - Main Axis: ขวา → ซ้าย */
.direction-row-reverse {
  display: flex;
  flex-direction: row-reverse;
  background: #fee2e2;
  padding: 1rem;
  border: 2px solid #ef4444;
}

/* column - Main Axis: บน → ล่าง */
.direction-column {
  display: flex;
  flex-direction: column;
  background: #dbeafe;
  padding: 1rem;
  border: 2px solid #3b82f6;
  height: 200px;
}

/* column-reverse - Main Axis: ล่าง → บน */
.direction-column-reverse {
  display: flex;
  flex-direction: column-reverse;
  background: #dcfce7;
  padding: 1rem;
  border: 2px solid #22c55e;
  height: 200px;
}
```

### การใช้งานจริง

```css
/* Responsive layout */
.responsive-container {
  display: flex;
  flex-direction: column; /* Mobile: แนวตั้ง */
  gap: 1rem;
}

@media (min-width: 768px) {
  .responsive-container {
    flex-direction: row; /* Desktop: แนวนอน */
  }
}

/* Mobile navigation */
.mobile-nav {
  display: flex;
  flex-direction: column;
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
}

/* Desktop navigation */
.desktop-nav {
  display: flex;
  flex-direction: row;
  gap: 2rem;
  list-style: none;
}
```

## 3. flex-wrap: การจัดการ Item ที่เกินขนาด 📦

### ค่าต่างๆ ของ flex-wrap

```css
/* nowrap (ค่าเริ่มต้น) - ไม่ให้ items ขึ้นบรรทัดใหม่ */
.wrap-nowrap {
  display: flex;
  flex-wrap: nowrap;
  background: #fef3c7;
  border: 2px solid #f59e0b;
  width: 400px;
}

/* wrap - อนุญาตให้ items ขึ้นบรรทัดใหม่ */
.wrap-wrap {
  display: flex;
  flex-wrap: wrap;
  background: #dbeafe;
  border: 2px solid #3b82f6;
  width: 400px;
}

/* wrap-reverse - ขึ้นบรรทัดใหม่ในทิศทางกลับ */
.wrap-reverse {
  display: flex;
  flex-wrap: wrap-reverse;
  background: #dcfce7;
  border: 2px solid #22c55e;
  width: 400px;
}
```

### flex-flow: Shorthand Property

```css
/* flex-flow = flex-direction + flex-wrap */
.shorthand-examples {
  /* แยกเขียน */
  .separate {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
  }

  /* รวมเป็น flex-flow */
  .shorthand {
    display: flex;
    flex-flow: row wrap; /* เทียบเท่ากับด้านบน */
  }

  /* ตัวอย่างอื่นๆ */
  .flow-column-wrap {
    display: flex;
    flex-flow: column wrap;
  }

  .flow-row-reverse-wrap {
    display: flex;
    flex-flow: row-reverse wrap;
  }
}
```

### การใช้งานจริง

```css
/* Responsive card grid */
.card-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  padding: 1rem;
}

.card {
  flex: 1 1 calc(50% - 0.5rem); /* 2 columns */
  min-width: 280px;
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  padding: 1.5rem;
}

@media (min-width: 1024px) {
  .card {
    flex: 1 1 calc(33.333% - 0.667rem); /* 3 columns */
  }
}

/* Tag list */
.tag-list {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tag {
  background: #e5e7eb;
  color: #374151;
  padding: 0.25rem 0.75rem;
  border-radius: 9999px;
  font-size: 0.875rem;
  white-space: nowrap;
}
```

## 4. justify-content: การจัดวางตาม Main Axis 📐

### ค่าต่างๆ ของ justify-content

```css
/* flex-start (ค่าเริ่มต้น) - จัดไปจุดเริ่มต้นของ main axis */
.justify-flex-start {
  display: flex;
  justify-content: flex-start;
  background: #fef3c7;
  border: 2px solid #f59e0b;
  padding: 1rem;
  min-height: 80px;
}

/* flex-end - จัดไปจุดสิ้นสุดของ main axis */
.justify-flex-end {
  display: flex;
  justify-content: flex-end;
  background: #fee2e2;
  border: 2px solid #ef4444;
  padding: 1rem;
  min-height: 80px;
}

/* center - จัดกึ่งกลาง main axis */
.justify-center {
  display: flex;
  justify-content: center;
  background: #dbeafe;
  border: 2px solid #3b82f6;
  padding: 1rem;
  min-height: 80px;
}

/* space-between - กระจายห่างเท่าๆ กัน ไม่มี space ข้างๆ */
.justify-space-between {
  display: flex;
  justify-content: space-between;
  background: #dcfce7;
  border: 2px solid #22c55e;
  padding: 1rem;
  min-height: 80px;
}

/* space-around - space รอบๆ แต่ละ item */
.justify-space-around {
  display: flex;
  justify-content: space-around;
  background: #f3e8ff;
  border: 2px solid #a855f7;
  padding: 1rem;
  min-height: 80px;
}

/* space-evenly - space เท่าๆ กันทุกช่วง */
.justify-space-evenly {
  display: flex;
  justify-content: space-evenly;
  background: #ecfdf5;
  border: 2px solid #10b981;
  padding: 1rem;
  min-height: 80px;
}
```

### การใช้งานจริง

```css
/* Header navigation */
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
  background: white;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

/* Card actions */
.card-footer {
  display: flex;
  justify-content: flex-end;
  gap: 0.5rem;
  margin-top: 1.5rem;
  padding-top: 1rem;
  border-top: 1px solid #e5e7eb;
}

/* Modal dialog */
.modal-overlay {
  display: flex;
  justify-content: center;
  align-items: center;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
}

/* Stats section */
.stats-container {
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 3rem 2rem;
  background: #f8fafc;
  border-radius: 0.5rem;
}
```

## 5. align-items: การจัดวางตาม Cross Axis 📏

### ค่าต่างๆ ของ align-items

```css
/* stretch (ค่าเริ่มต้น) - ยืดเต็ม cross axis */
.align-stretch {
  display: flex;
  align-items: stretch;
  background: #fef3c7;
  border: 2px solid #f59e0b;
  padding: 1rem;
  height: 120px;
}

/* flex-start - จัดไปจุดเริ่มต้นของ cross axis */
.align-flex-start {
  display: flex;
  align-items: flex-start;
  background: #fee2e2;
  border: 2px solid #ef4444;
  padding: 1rem;
  height: 120px;
}

/* flex-end - จัดไปจุดสิ้นสุดของ cross axis */
.align-flex-end {
  display: flex;
  align-items: flex-end;
  background: #dbeafe;
  border: 2px solid #3b82f6;
  padding: 1rem;
  height: 120px;
}

/* center - จัดกึ่งกลาง cross axis */
.align-center {
  display: flex;
  align-items: center;
  background: #dcfce7;
  border: 2px solid #22c55e;
  padding: 1rem;
  height: 120px;
}

/* baseline - จัดตาม baseline ของ text */
.align-baseline {
  display: flex;
  align-items: baseline;
  background: #f3e8ff;
  border: 2px solid #a855f7;
  padding: 1rem;
  height: 120px;
}
```

### การใช้งานจริง

```css
/* Navigation bar */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center; /* จัดให้อยู่กึ่งกลางแนวตั้ง */
  padding: 1rem 2rem;
  background: white;
  height: 70px;
}

/* Product card */
.product-card {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  padding: 1.5rem;
}

.product-image {
  width: 80px;
  height: 80px;
  border-radius: 0.5rem;
  object-fit: cover;
  flex-shrink: 0;
}

/* Comment item */
.comment {
  display: flex;
  align-items: flex-start; /* จัด avatar กับ content ชิดด้านบน */
  gap: 1rem;
  padding: 1.5rem;
  border-bottom: 1px solid #e5e7eb;
}

.comment-avatar {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  flex-shrink: 0;
}

/* Form row */
.form-row {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 1rem;
}

.form-label {
  flex: 0 0 120px;
  font-weight: 500;
  color: #374151;
}

.form-input {
  flex: 1;
  padding: 0.75rem;
  border: 1px solid #d1d5db;
  border-radius: 0.375rem;
}
```

## 6. align-content: การจัดวาง Wrapped Lines 📚

### ความแตกต่างจาก align-items

```css
/* align-items: จัดวาง items ใน single line */
.single-line {
  display: flex;
  align-items: center; /* ใช้งานได้กับ line เดียว */
  height: 120px;
  background: #f0f9ff;
  border: 2px dashed #0ea5e9;
  padding: 1rem;
}

/* align-content: จัดวาง wrapped lines (ต้องมี flex-wrap) */
.multi-line {
  display: flex;
  flex-wrap: wrap; /* จำเป็น! */
  align-content: center; /* จัดวาง lines */
  height: 200px;
  width: 300px;
  background: #f0fdf4;
  border: 2px dashed #22c55e;
  padding: 1rem;
}
```

### ค่าต่างๆ ของ align-content

```css
/* stretch (ค่าเริ่มต้น) - ยืด lines เต็ม cross axis */
.content-stretch {
  display: flex;
  flex-wrap: wrap;
  align-content: stretch;
  height: 200px;
  width: 300px;
  background: #fef3c7;
  border: 2px solid #f59e0b;
}

/* flex-start - จัด lines ไปจุดเริ่มต้น */
.content-flex-start {
  display: flex;
  flex-wrap: wrap;
  align-content: flex-start;
  height: 200px;
  width: 300px;
  background: #fee2e2;
  border: 2px solid #ef4444;
}

/* center - จัด lines กึ่งกลาง */
.content-center {
  display: flex;
  flex-wrap: wrap;
  align-content: center;
  height: 200px;
  width: 300px;
  background: #dcfce7;
  border: 2px solid #22c55e;
}

/* space-between - กระจาย lines ห่างเท่าๆ กัน */
.content-space-between {
  display: flex;
  flex-wrap: wrap;
  align-content: space-between;
  height: 200px;
  width: 300px;
  background: #f3e8ff;
  border: 2px solid #a855f7;
}
```

### การใช้งานจริง

```css
/* Tag cloud */
.tag-cloud {
  display: flex;
  flex-wrap: wrap;
  align-content: center;
  justify-content: center;
  min-height: 200px;
  padding: 2rem;
  background: #f8fafc;
  border-radius: 0.5rem;
}

.tag-cloud .tag {
  background: white;
  color: #374151;
  padding: 0.5rem 1rem;
  margin: 0.25rem;
  border-radius: 9999px;
  border: 1px solid #e5e7eb;
  font-size: 0.875rem;
  cursor: pointer;
}

/* Photo gallery */
.photo-gallery {
  display: flex;
  flex-wrap: wrap;
  align-content: flex-start;
  gap: 1rem;
  padding: 1rem;
  background: #f1f5f9;
  border-radius: 0.5rem;
  min-height: 400px;
}

.photo-item {
  flex: 1 1 calc(33.333% - 0.667rem);
  min-width: 150px;
  aspect-ratio: 1;
  background: white;
  border-radius: 0.5rem;
  overflow: hidden;
}
```

## 7. gap: การกำหนดระยะห่างระหว่าง Items 📏

### ค่าต่างๆ ของ gap

```css
/* gap - ระยะห่างทั้งแนวนอนและแนวตั้ง */
.gap-example {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem; /* 16px ทุกทิศทาง */
  padding: 1rem;
  background: #f8fafc;
  border: 2px solid #6b7280;
}

/* row-gap - ระยะห่างแนวตั้ง */
.row-gap-example {
  display: flex;
  flex-wrap: wrap;
  row-gap: 2rem; /* 32px แนวตั้ง */
  column-gap: 1rem; /* 16px แนวนอน */
  padding: 1rem;
  background: #f0f9ff;
  border: 2px solid #3b82f6;
}

/* ใช้หน่วยต่างๆ */
.gap-units {
  display: flex;
  gap: 20px; /* pixels */
  /* gap: 1.5rem; */ /* rem units */
  /* gap: 2%; */ /* percentage */
  /* gap: 1em; */ /* em units */
}
```

### ข้อดีของ gap เหนือ margin

```css
/* ❌ วิธีเก่า: ใช้ margin */
.old-way {
  display: flex;
}

.old-way .item {
  margin-right: 1rem; /* ปัญหา: item สุดท้ายก็มี margin */
}

.old-way .item:last-child {
  margin-right: 0; /* ต้องมาแก้ */
}

/* ✅ วิธีใหม่: ใช้ gap */
.new-way {
  display: flex;
  gap: 1rem; /* สะอาด ไม่ต้องแก้อะไร */
}
```

### การใช้งานจริง

```css
/* Card grid with gap */
.card-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 1.5rem;
  padding: 1.5rem;
}

.card {
  flex: 1 1 calc(33.333% - 1rem);
  min-width: 300px;
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  padding: 1.5rem;
}

/* Navigation with gap */
.nav-menu {
  display: flex;
  gap: 2rem;
  list-style: none;
  margin: 0;
  padding: 0;
}

/* Button toolbar */
.button-toolbar {
  display: flex;
  gap: 0.5rem;
  padding: 1rem;
  background: #f1f5f9;
  border-radius: 0.5rem;
}

.toolbar-button {
  padding: 0.5rem 1rem;
  background: white;
  border: 1px solid #d1d5db;
  border-radius: 0.25rem;
  cursor: pointer;
}

/* Form layout */
.form-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.form-group {
  flex: 1;
  min-width: 250px;
}

/* Responsive gap */
.responsive-gap {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem; /* Mobile */
}

@media (min-width: 768px) {
  .responsive-gap {
    gap: 1.5rem; /* Tablet */
  }
}

@media (min-width: 1024px) {
  .responsive-gap {
    gap: 2rem; /* Desktop */
  }
}
```

## 8. การรวม Properties เพื่อสร้าง Layout Patterns

### Perfect Centering Pattern

```css
.perfect-center {
  display: flex;
  justify-content: center; /* จัดกึ่งกลาง main axis */
  align-items: center; /* จัดกึ่งกลาง cross axis */
  height: 100vh;
}
```

### Header Layout Pattern

```css
.header-layout {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
  background: white;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}
```

### Card Grid Pattern

```css
.card-grid-pattern {
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  align-content: flex-start;
  gap: 1.5rem;
  padding: 1.5rem;
}

.card-item {
  flex: 1 1 calc(33.333% - 1rem);
  min-width: 280px;
}
```

### Sidebar Layout Pattern

```css
.app-layout {
  display: flex;
  min-height: 100vh;
}

.sidebar {
  flex: 0 0 250px;
  display: flex;
  flex-direction: column;
  background: #f8fafc;
}

.main-content {
  flex: 1;
  display: flex;
  flex-direction: column;
}
```

### Responsive Navigation Pattern

```css
.nav-responsive {
  display: flex;
  flex-direction: column; /* Mobile */
  gap: 1rem;
}

@media (min-width: 768px) {
  .nav-responsive {
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
  }
}
```

## 9. Best Practices และ Tips

### Performance Tips

```css
/* ✅ ใช้ gap แทน margin */
.good-spacing {
  display: flex;
  gap: 1rem;
}

/* ✅ ใช้ min-width: 0 สำหรับ text overflow */
.text-overflow {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.text-content {
  flex: 1;
  min-width: 0; /* สำคัญ! */
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
```

### Common Mistakes

```css
/* ❌ ลืมใช้ flex-wrap กับ align-content */
.mistake-1 {
  display: flex;
  align-content: center; /* ไม่ทำงานถ้าไม่มี wrap */
}

/* ✅ แก้ไข */
.fix-1 {
  display: flex;
  flex-wrap: wrap;
  align-content: center;
}

/* ❌ ใช้ height: 100% โดยไม่มี parent height */
.mistake-2 {
  display: flex;
  align-items: center;
  height: 100%; /* ไม่ทำงาน */
}

/* ✅ แก้ไข */
.fix-2 {
  display: flex;
  align-items: center;
  min-height: 100vh; /* ใช้ viewport height */
}
```

## สรุป: Container Properties Quick Reference

| Property          | ควบคุม                | ค่าที่ใช้บ่อย             |
| ----------------- | --------------------- | ------------------------- |
| `display`         | สร้าง flex container  | `flex`, `inline-flex`     |
| `flex-direction`  | ทิศทาง main axis      | `row`, `column`           |
| `flex-wrap`       | การ wrap items        | `nowrap`, `wrap`          |
| `justify-content` | จัดวางตาม main axis   | `center`, `space-between` |
| `align-items`     | จัดวางตาม cross axis  | `center`, `flex-start`    |
| `align-content`   | จัดวาง wrapped lines  | `center`, `flex-start`    |
| `gap`             | ระยะห่างระหว่าง items | `1rem`, `16px`            |

### การใช้งานร่วมกัน

```css
/* Layout พื้นฐาน */
.basic-layout {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
}

/* Responsive grid */
.responsive-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  align-content: flex-start;
  gap: 1.5rem;
}

/* Perfect center */
.center-everything {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
```

เมื่อเข้าใจ Container Properties ทั้ง 7 ตัวนี้แล้ว คุณจะสามารถสร้าง layout ที่ยืดหยุ่นและ responsive ได้อย่างมีประสิทธิภาพ! 🎯
