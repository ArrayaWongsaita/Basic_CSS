# CSS Position: คู่มือฉบับสมบูรณ์

## ภาพรวม CSS Position Property

`position` เป็น CSS property ที่กำหนดวิธีการจัดวาง element ใน document โดยทำงานร่วมกับ properties อื่นๆ เช่น `top`, `right`, `bottom`, `left` และ `z-index` เพื่อควบคุมตำแหน่งที่แน่นอนของ elements

### Position Values Overview

```css
/* ค่าต่างๆ ของ position property */
.position-examples {
  position: static; /* ค่าเริ่มต้น - ไม่สามารถปรับตำแหน่งได้ */
  position: relative; /* สัมพัทธ์กับตำแหน่งเดิม */
  position: absolute; /* สัมพัทธ์กับ parent ที่มี position */
  position: fixed; /* สัมพัทธ์กับ viewport */
  position: sticky; /* ผสมระหว่าง relative และ fixed */
}

/* Properties ที่ใช้ร่วมกับ position */
.positioning-properties {
  top: 10px; /* ระยะห่างจากด้านบน */
  right: 10px; /* ระยะห่างจากด้านขวา */
  bottom: 10px; /* ระยะห่างจากด้านล่าง */
  left: 10px; /* ระยะห่างจากด้านซ้าย */
  z-index: 10; /* ลำดับชั้นการซ้อนทับ */
}
```

## 1. Position: static (ค่าเริ่มต้น)

### ความหมายและพฤติกรรม

```css
/* Static positioning (ค่าเริ่มต้น) */
.static-element {
  position: static;
  /* top, right, bottom, left จะไม่ทำงาน */
  top: 50px; /* ไม่มีผล */
  left: 100px; /* ไม่มีผล */
  z-index: 999; /* ไม่มีผล */
}

/* ตัวอย่างการใช้งาน static */
.normal-flow {
  /* Elements จะเรียงตาม document flow ปกติ */
  display: block;
  margin: 10px 0;
  padding: 20px;
  background-color: #f3f4f6;
}

.inline-static {
  /* Inline elements ใน static flow */
  display: inline;
  margin: 0 5px;
  padding: 5px 10px;
  background-color: #ddd6fe;
}

/* Static elements ใน container */
.container {
  width: 100%;
  padding: 20px;
  background-color: #fef3c7;
}

.container .static-child {
  /* จะเรียงตาม normal document flow */
  position: static;
  margin: 10px 0;
  padding: 15px;
  background-color: #ffffff;
  border: 1px solid #d1d5db;
}
```

### ลักษณะเด่นของ Static Position

```css
/* Static positioning characteristics */
.static-characteristics {
  /* 1. ไม่สามารถใช้ top, right, bottom, left */
  position: static;
  /* top: 10px; ← ไม่ทำงาน */

  /* 2. ไม่สามารถใช้ z-index */
  /* z-index: 10; ← ไม่ทำงาน */

  /* 3. ไม่เป็น positioning context สำหรับ children */
  /* absolute children จะหา positioned parent อื่น */

  /* 4. ใช้ margin/padding สำหรับจัดตำแหน่ง */
  margin: 20px;
  padding: 15px;
}

/* ตัวอย่างปัญหาที่พบบ่อย */
.static-issues {
  /* พยายามใช้ positioning properties */
  position: static;
  top: 0; /* ไม่ทำงาน */
  left: 0; /* ไม่ทำงาน */
  z-index: 10; /* ไม่ทำงาน */

  /* แก้ไข: เปลี่ยนเป็น position อื่น */
  position: relative; /* หรือ absolute, fixed, sticky */
  top: 0; /* ทำงานแล้ว */
  left: 0; /* ทำงานแล้ว */
  z-index: 10; /* ทำงานแล้ว */
}
```

## 2. Position: relative (การจัดตำแหน่งสัมพัทธ์)

### ความหมายและการทำงาน

```css
/* Relative positioning */
.relative-element {
  position: relative;
  /* จะเลื่อนจากตำแหน่งเดิม (static position) */
  top: 10px; /* เลื่อนลงจากตำแหน่งเดิม 10px */
  left: 20px; /* เลื่อนขวาจากตำแหน่งเดิม 20px */
  z-index: 1; /* สามารถใช้ z-index ได้ */
}

/* การเปรียบเทียบ static vs relative */
.comparison-container {
  border: 2px solid #6366f1;
  padding: 20px;
  margin: 20px 0;
}

.static-box {
  position: static;
  width: 100px;
  height: 100px;
  background-color: #ef4444;
  margin: 10px;
}

.relative-box {
  position: relative;
  width: 100px;
  height: 100px;
  background-color: #10b981;
  margin: 10px;
  /* เลื่อนจากตำแหน่งเดิม */
  top: 20px;
  left: 30px;
}
```

### การใช้งาน Relative Position

```css
/* Use cases สำหรับ relative positioning */

/* 1. เปลี่ยนตำแหน่งเล็กน้อย */
.slight-adjustment {
  position: relative;
  top: -2px; /* ยกขึ้นเล็กน้อย */
}

/* 2. เป็น positioning context สำหรับ absolute children */
.parent-container {
  position: relative; /* สร้าง positioning context */
  width: 300px;
  height: 200px;
  background-color: #f9fafb;
  border: 1px solid #d1d5db;
}

.absolute-child {
  position: absolute;
  top: 10px; /* 10px จากด้านบนของ parent */
  right: 10px; /* 10px จากด้านขวาของ parent */
  width: 50px;
  height: 50px;
  background-color: #3b82f6;
}

/* 3. สร้าง overlay หรือ pseudo-elements */
.overlay-parent {
  position: relative;
  padding: 20px;
  background-color: #ffffff;
}

.overlay-parent::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.1);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.overlay-parent:hover::before {
  opacity: 1;
}

/* 4. การจัดการ z-index */
.layered-content {
  position: relative;
  z-index: 1; /* สร้าง stacking context */
}

.background-layer {
  position: relative;
  z-index: -1; /* อยู่ด้านหลัง */
  background-color: #fef3c7;
}
```

### Relative Position Advanced Techniques

```css
/* เทคนิคขั้นสูงสำหรับ relative positioning */

/* 1. ปรับตำแหน่งสำหรับ responsive design */
.responsive-adjustment {
  position: relative;
}

@media (max-width: 768px) {
  .responsive-adjustment {
    top: 10px;
    left: 5px;
  }
}

@media (min-width: 769px) {
  .responsive-adjustment {
    top: 0;
    left: 0;
  }
}

/* 2. Animation กับ relative positioning */
.animated-relative {
  position: relative;
  transition: all 0.3s ease;
}

.animated-relative:hover {
  top: -5px;
  left: 5px;
}

/* 3. การใช้ negative values */
.negative-positioning {
  position: relative;
  top: -10px; /* เลื่อนขึ้น */
  left: -20px; /* เลื่อนซ้าย */
}

/* 4. การผสมกับ transform */
.relative-transform {
  position: relative;
  top: 10px;
  transform: translateX(20px) rotate(5deg);
  /* รวมการเลื่อนตำแหน่งและ transformation */
}
```

## 3. Position: absolute (การจัดตำแหน่งสัมบูรณ์)

### ความหมายและพฤติกรรม

```css
/* Absolute positioning */
.absolute-element {
  position: absolute;
  /* ตำแหน่งสัมพัทธ์กับ positioned parent ที่ใกล้ที่สุด */
  top: 0; /* ติดด้านบนของ positioned parent */
  right: 0; /* ติดด้านขวาของ positioned parent */
  width: 100px;
  height: 100px;
  background-color: #8b5cf6;
}

/* Positioned parent (relative, absolute, fixed, หรือ sticky) */
.positioned-parent {
  position: relative; /* สร้าง positioning context */
  width: 400px;
  height: 300px;
  background-color: #f3f4f6;
  border: 2px dashed #6b7280;
}

/* หาก parent ไม่มี position, absolute จะอ้างอิงจาก viewport */
.no-positioned-parent {
  /* Parent นี้เป็น static (ค่าเริ่มต้น) */
  width: 400px;
  height: 300px;
  background-color: #fecaca;
}

.absolute-to-viewport {
  position: absolute;
  top: 50px; /* 50px จากด้านบนของ viewport */
  left: 100px; /* 100px จากด้านซ้ายของ viewport */
}
```

### Absolute Positioning Patterns

```css
/* รูปแบบการใช้งาน absolute positioning */

/* 1. การจัดตำแหน่งมุมต่างๆ */
.corner-positioning {
  position: relative;
  width: 300px;
  height: 200px;
  background-color: #f9fafb;
}

/* มุมบนซ้าย */
.top-left {
  position: absolute;
  top: 0;
  left: 0;
}

/* มุมบนขวา */
.top-right {
  position: absolute;
  top: 0;
  right: 0;
}

/* มุมล่างซ้าย */
.bottom-left {
  position: absolute;
  bottom: 0;
  left: 0;
}

/* มุมล่างขวา */
.bottom-right {
  position: absolute;
  bottom: 0;
  right: 0;
}

/* กึ่งกลาง */
.center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

/* 2. การยืดเต็มพื้นที่ */
.full-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  /* หรือใช้ width: 100%; height: 100%; */
  background-color: rgba(0, 0, 0, 0.5);
}

/* 3. Navigation และ UI elements */
.dropdown-menu {
  position: absolute;
  top: 100%; /* ใต้ parent element */
  left: 0;
  min-width: 200px;
  background-color: white;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  border-radius: 0.375rem;
  z-index: 10;
}

.tooltip {
  position: absolute;
  bottom: 100%; /* เหนือ parent element */
  left: 50%;
  transform: translateX(-50%);
  background-color: #1f2937;
  color: white;
  padding: 0.5rem 0.75rem;
  border-radius: 0.25rem;
  font-size: 0.875rem;
  white-space: nowrap;
}

/* 4. Modal และ popover */
.modal-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 50;
}

.modal-content {
  background-color: white;
  border-radius: 0.5rem;
  padding: 2rem;
  max-width: 90vw;
  max-height: 90vh;
  overflow: auto;
}
```

### การคำนวณตำแหน่ง Absolute

```css
/* เทคนิคการคำนวณตำแหน่ง */

/* 1. การใช้ calc() */
.calculated-position {
  position: absolute;
  top: calc(50% - 25px); /* กึ่งกลางแนวตั้ง - ครึ่งความสูง */
  left: calc(100% + 10px); /* ขวาของ parent + margin */
  width: 50px;
  height: 50px;
}

/* 2. การใช้ negative margins */
.negative-margin-center {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 200px;
  height: 100px;
  margin-top: -50px; /* -ครึ่งความสูง */
  margin-left: -100px; /* -ครึ่งความกว้าง */
}

/* 3. การใช้ auto สำหรับ centering */
.auto-center {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  margin: auto;
  width: 200px; /* ต้องกำหนด width และ height */
  height: 100px;
}

/* 4. การจัดตำแหน่งตามเปอร์เซ็นต์ */
.percentage-positioning {
  position: absolute;
  top: 25%; /* 1/4 ของความสูง parent */
  left: 75%; /* 3/4 ของความกว้าง parent */
  transform: translate(-50%, -50%); /* ปรับให้อยู่กึ่งกลางของตัวเอง */
}
```

## 4. Position: fixed (การจัดตำแหน่งคงที่)

### ความหมายและการทำงาน

```css
/* Fixed positioning */
.fixed-element {
  position: fixed;
  /* ตำแหน่งสัมพัทธ์กับ viewport เสมอ */
  top: 0;
  left: 0;
  width: 100%;
  height: 60px;
  background-color: #1f2937;
  color: white;
  z-index: 100;
}

/* Fixed elements ไม่ขึ้นอยู่กับ parent positioning */
.some-container {
  position: relative;
  /* Fixed child จะไม่อ้างอิงจาก container นี้ */
}

.fixed-child {
  position: fixed;
  /* จะอ้างอิงจาก viewport ไม่ใช่ .some-container */
  bottom: 20px;
  right: 20px;
}
```

### Fixed Position Use Cases

```css
/* การใช้งานจริงของ fixed positioning */

/* 1. Navigation bar ที่ติดด้านบน */
.fixed-navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  height: 64px;
  background-color: white;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  z-index: 100;
  display: flex;
  align-items: center;
  padding: 0 1rem;
}

/* ต้องเพิ่ม padding-top ให้ body เพื่อไม่ให้ content ถูก navbar บัง */
body {
  padding-top: 64px; /* เท่ากับความสูงของ navbar */
}

/* 2. Sidebar ที่ติดข้าง */
.fixed-sidebar {
  position: fixed;
  top: 0;
  left: 0;
  width: 250px;
  height: 100vh;
  background-color: #f8fafc;
  border-right: 1px solid #e2e8f0;
  z-index: 90;
  overflow-y: auto; /* เลื่อนได้หากเนื้อหายาว */
}

/* ต้องเพิ่ม margin-left ให้ main content */
.main-content {
  margin-left: 250px; /* เท่ากับความกว้างของ sidebar */
}

/* 3. Floating action button */
.fab {
  position: fixed;
  bottom: 24px;
  right: 24px;
  width: 56px;
  height: 56px;
  border-radius: 50%;
  background-color: #3b82f6;
  color: white;
  border: none;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  cursor: pointer;
  z-index: 50;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
}

.fab:hover {
  background-color: #2563eb;
  transform: scale(1.1);
  transition: all 0.2s ease;
}

/* 4. Toast notifications */
.toast-container {
  position: fixed;
  top: 20px;
  right: 20px;
  z-index: 200;
  max-width: 400px;
}

.toast {
  background-color: white;
  border-radius: 0.5rem;
  box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
  padding: 1rem;
  margin-bottom: 0.5rem;
  border-left: 4px solid #10b981;
}

/* 5. Modal backdrop */
.modal-backdrop {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 150;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* 6. Loading spinner overlay */
.loading-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(255, 255, 255, 0.8);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 300;
}

.spinner {
  width: 40px;
  height: 40px;
  border: 4px solid #f3f4f6;
  border-top: 4px solid #3b82f6;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
```

### Fixed Position Responsive Design

```css
/* การจัดการ fixed elements ใน responsive design */

/* Mobile-first approach */
.responsive-fixed-nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  height: 56px; /* น้อยกว่าใน desktop */
  background-color: white;
  z-index: 100;
}

/* Tablet และ desktop */
@media (min-width: 768px) {
  .responsive-fixed-nav {
    height: 64px;
  }
}

/* การซ่อน/แสดง fixed elements ใน mobile */
@media (max-width: 767px) {
  .fixed-sidebar {
    transform: translateX(-100%);
    transition: transform 0.3s ease;
  }

  .fixed-sidebar.open {
    transform: translateX(0);
  }

  /* ไม่ต้อง margin-left ใน mobile */
  .main-content {
    margin-left: 0;
  }
}

/* การปรับ FAB ใน mobile */
@media (max-width: 767px) {
  .fab {
    bottom: 16px;
    right: 16px;
    width: 48px;
    height: 48px;
  }
}
```

## 5. Position: sticky (การจัดตำแหน่งแบบผสม)

### ความหมายและพฤติกรรม

```css
/* Sticky positioning */
.sticky-element {
  position: sticky;
  top: 0; /* ระยะห่างจากด้านบนของ container เมื่อ "ติด" */
  background-color: white;
  z-index: 10;
}

/* Sticky ต้องอยู่ในเมื่อ container ที่มีความสูงเพียงพอ */
.scrollable-container {
  height: 400px;
  overflow-y: auto;
  border: 1px solid #d1d5db;
}

.sticky-header {
  position: sticky;
  top: 0;
  background-color: #f9fafb;
  padding: 1rem;
  border-bottom: 1px solid #e5e7eb;
  font-weight: 600;
}

.content-section {
  padding: 1rem;
  height: 200px; /* เนื้อหาที่ยาวพอที่จะทำให้เลื่อนได้ */
}
```

### Sticky Position Use Cases

```css
/* การใช้งานจริงของ sticky positioning */

/* 1. Table headers ที่ติดด้านบน */
.sticky-table {
  width: 100%;
  border-collapse: collapse;
}

.sticky-table thead th {
  position: sticky;
  top: 0;
  background-color: #f8fafc;
  border-bottom: 2px solid #e2e8f0;
  padding: 0.75rem;
  text-align: left;
  font-weight: 600;
  z-index: 10;
}

.sticky-table tbody td {
  padding: 0.75rem;
  border-bottom: 1px solid #e2e8f0;
}

/* 2. Section headers ใน long content */
.article-container {
  max-height: 80vh;
  overflow-y: auto;
}

.section-header {
  position: sticky;
  top: 0;
  background-color: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(8px);
  padding: 1rem 0;
  margin: 2rem 0 1rem 0;
  border-bottom: 2px solid #3b82f6;
  font-size: 1.25rem;
  font-weight: 700;
  z-index: 5;
}

/* 3. Navigation ที่ติดหลังจากเลื่อนผ่าน header */
.page-header {
  height: 300px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 2rem;
}

.sticky-nav {
  position: sticky;
  top: 0;
  background-color: white;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  z-index: 100;
}

.nav-list {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
}

.nav-item {
  padding: 1rem 1.5rem;
  border-bottom: 3px solid transparent;
  transition: all 0.2s ease;
}

.nav-item:hover,
.nav-item.active {
  background-color: #f8fafc;
  border-bottom-color: #3b82f6;
}

/* 4. Sidebar ที่ติดในขณะเลื่อน */
.content-with-sidebar {
  display: flex;
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.main-article {
  flex: 1;
}

.sticky-sidebar {
  flex: 0 0 250px;
}

.sidebar-content {
  position: sticky;
  top: 2rem; /* เว้นระยะจากด้านบน */
  background-color: #f8fafc;
  border-radius: 0.5rem;
  padding: 1.5rem;
  border: 1px solid #e2e8f0;
}

/* 5. Call-to-action ที่ติดด้านล่าง */
.sticky-cta {
  position: sticky;
  bottom: 0;
  background-color: #3b82f6;
  color: white;
  padding: 1rem;
  text-align: center;
  margin-top: 2rem;
  z-index: 20;
}

.cta-button {
  background-color: white;
  color: #3b82f6;
  border: none;
  border-radius: 0.375rem;
  padding: 0.75rem 2rem;
  font-weight: 600;
  cursor: pointer;
}
```

### Sticky Position Advanced Techniques

```css
/* เทคนิคขั้นสูงสำหรับ sticky positioning */

/* 1. Multiple sticky elements */
.multi-sticky-container {
  height: 80vh;
  overflow-y: auto;
}

.sticky-primary {
  position: sticky;
  top: 0;
  background-color: #1f2937;
  color: white;
  padding: 1rem;
  z-index: 30;
}

.sticky-secondary {
  position: sticky;
  top: 60px; /* ห่างจาก primary sticky */
  background-color: #374151;
  color: white;
  padding: 0.75rem;
  z-index: 25;
}

/* 2. Sticky ที่เปลี่ยนสีตามการเลื่อน */
.color-changing-sticky {
  position: sticky;
  top: 0;
  padding: 1rem;
  transition: all 0.3s ease;
  z-index: 10;
}

/* ใช้ JavaScript เพื่อเพิ่ม class เมื่อ stick */
.color-changing-sticky.is-stuck {
  background-color: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

/* 3. Sticky elements ใน grid layout */
.grid-with-sticky {
  display: grid;
  grid-template-columns: 250px 1fr;
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.sticky-grid-sidebar {
  height: fit-content;
  position: sticky;
  top: 2rem;
}

/* 4. การจัดการ sticky ใน responsive */
@media (max-width: 768px) {
  .responsive-sticky {
    position: static; /* ยกเลิก sticky ใน mobile */
  }

  .multi-sticky-container {
    height: auto;
    overflow-y: visible;
  }
}

/* 5. Sticky footer ที่ปรากฏเมื่อเลื่อนถึงท้าย */
.sticky-footer {
  position: sticky;
  bottom: 0;
  background-color: #f8fafc;
  border-top: 1px solid #e2e8f0;
  padding: 1rem;
  margin-top: auto; /* ผลักไปด้านล่างสุด */
}
```

## 6. Z-Index: การควบคุมลำดับชั้น

### ความหมายและการทำงาน

```css
/* Z-index basics */
.z-index-examples {
  /* z-index ทำงานเฉพาะกับ positioned elements */
  position: relative; /* หรือ absolute, fixed, sticky */
  z-index: 10;
}

/* การเปรียบเทียบ z-index */
.layer-1 {
  position: relative;
  z-index: 1;
  background-color: #ef4444;
  width: 100px;
  height: 100px;
}

.layer-2 {
  position: relative;
  z-index: 2; /* อยู่บน layer-1 */
  background-color: #10b981;
  width: 100px;
  height: 100px;
  margin-top: -50px; /* ทับกับ layer-1 */
  margin-left: 25px;
}

.layer-3 {
  position: relative;
  z-index: 3; /* อยู่บนสุด */
  background-color: #3b82f6;
  width: 100px;
  height: 100px;
  margin-top: -50px;
  margin-left: 50px;
}
```

### Z-Index Scale และ Organization

```css
/* Z-index scale system */
:root {
  /* Base layers */
  --z-base: 0;
  --z-below: -1;

  /* Content layers */
  --z-content: 1;
  --z-elevated: 10;
  --z-overlay: 100;

  /* Navigation layers */
  --z-dropdown: 1000;
  --z-sticky: 1100;
  --z-navbar: 1200;

  /* Modal layers */
  --z-backdrop: 2000;
  --z-modal: 2100;
  --z-popover: 2200;

  /* System layers */
  --z-toast: 3000;
  --z-tooltip: 3100;
  --z-loading: 3200;

  /* Top layers */
  --z-debug: 9000;
  --z-emergency: 9999;
}

/* การใช้งาน z-index scale */
.background-element {
  z-index: var(--z-below);
}

.card {
  z-index: var(--z-content);
}

.dropdown-menu {
  z-index: var(--z-dropdown);
}

.modal-backdrop {
  z-index: var(--z-backdrop);
}

.modal-content {
  z-index: var(--z-modal);
}

.toast-notification {
  z-index: var(--z-toast);
}
```

### Stacking Context

```css
/* Stacking context concepts */

/* 1. Elements ที่สร้าง stacking context */
.stacking-context-creators {
  /* กรณีต่างๆ ที่สร้าง stacking context */
  position: relative;
  z-index: 1; /* position + z-index ≠ auto */

  /* หรือ */
  position: fixed; /* fixed/absolute/sticky + z-index auto */

  /* หรือ */
  opacity: 0.99; /* opacity < 1 */

  /* หรือ */
  transform: translateZ(0); /* transform ≠ none */

  /* หรือ */
  filter: blur(1px); /* filter ≠ none */

  /* หรือ */
  isolation: isolate; /* สร้าง stacking context โดยตรง */
}

/* 2. ปัญหา z-index ที่พบบ่อย */
.parent-context {
  position: relative;
  z-index: 1; /* สร้าง stacking context */
}

.child-high-z {
  position: absolute;
  z-index: 9999; /* จะไม่ออกนอก parent context */
}

.sibling-low-z {
  position: relative;
  z-index: 2; /* จะอยู่บน child-high-z */
}

/* แก้ไข: ย้าย z-index ไปที่ parent level */
.fixed-parent-context {
  position: relative;
  z-index: 10; /* เพิ่ม z-index ของ parent */
}

/* 3. การใช้ isolation เพื่อควบคุม stacking context */
.isolated-component {
  isolation: isolate; /* สร้าง stacking context ใหม่ */
}

.isolated-component .internal-layer-1 {
  position: relative;
  z-index: 1;
}

.isolated-component .internal-layer-2 {
  position: relative;
  z-index: 2;
}
/* internal layers จะไม่ขัดแย้งกับ external elements */
```

### Z-Index Best Practices

```css
/* Best practices สำหรับ z-index */

/* 1. Component-level z-index management */
.component {
  /* กำหนด z-index ระดับ component */
  position: relative;
  z-index: var(--component-z-index, 1);
}

.component__overlay {
  position: absolute;
  z-index: 1; /* local z-index ภายใน component */
}

.component__tooltip {
  position: absolute;
  z-index: 2; /* สูงกว่า overlay */
}

/* 2. Conditional z-index */
.modal {
  position: fixed;
  z-index: var(--z-modal);

  /* เมื่อ active */
  &.is-active {
    z-index: var(--z-modal);
  }

  /* เมื่อไม่ active ให้ซ่อนออกไป */
  &:not(.is-active) {
    z-index: -1;
    opacity: 0;
    pointer-events: none;
  }
}

/* 3. Responsive z-index */
.responsive-layer {
  position: relative;
  z-index: 1;
}

@media (max-width: 768px) {
  .responsive-layer {
    z-index: 10; /* เพิ่มใน mobile เพื่อให้แน่ใจว่าอยู่บน */
  }
}

/* 4. การจัดการ z-index ใน JavaScript framework */
.react-component {
  --local-z-base: 1;
  --local-z-elevated: 2;
  --local-z-modal: 3;
}

.vue-component {
  /* ใช้ CSS custom properties เพื่อความยืดหยุ่น */
  z-index: var(--component-z-index, var(--z-content));
}
```

### Common Z-Index Issues และ Solutions

```css
/* ปัญหาและการแก้ไขที่พบบ่อย */

/* ปัญหา 1: z-index ไม่ทำงานบน static elements */
.problem-static {
  position: static; /* z-index ไม่ทำงาน */
  z-index: 999;
}

.solution-positioned {
  position: relative; /* แก้: เพิ่ม position */
  z-index: 999; /* ทำงานแล้ว */
}

/* ปัญหา 2: Modal ไม่อยู่บนสุด */
.problematic-modal {
  position: fixed;
  z-index: 1000;
  /* แต่มี element อื่นที่มี z-index สูงกว่า */
}

.solution-modal {
  position: fixed;
  z-index: var(--z-modal); /* ใช้ systematic z-index */
  /* หรือ */
  z-index: 9999; /* ค่าที่แน่ใจว่าสูงสุด */
}

/* ปัญหา 3: Dropdown อยู่ใต้ content อื่น */
.dropdown-container {
  position: relative;
  /* ต้องแน่ใจว่า container มี z-index เพียงพอ */
  z-index: var(--z-dropdown);
}

.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  z-index: 1; /* local z-index ภายใน container */
}

/* ปัญหา 4: Fixed header ไม่อยู่บน absolute content */
.fixed-header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: var(--z-navbar); /* ใช้ค่าที่กำหนดไว้ */
}

/* ปัญหา 5: การใช้ z-index มากเกินไป */
.bad-practice {
  z-index: 999999; /* หลีกเลี่ยง */
}

.good-practice {
  z-index: var(--z-overlay); /* ใช้ systematic approach */
}
```

## 7. Practical Examples และ Real-World Applications

### Layout Patterns

```css
/* Layout patterns ที่ใช้ positioning */

/* 1. Header + Sidebar + Main layout */
.app-layout {
  min-height: 100vh;
}

.app-header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  height: 64px;
  background-color: white;
  border-bottom: 1px solid #e5e7eb;
  z-index: var(--z-navbar);
}

.app-sidebar {
  position: fixed;
  top: 64px; /* ใต้ header */
  left: 0;
  width: 250px;
  bottom: 0;
  background-color: #f8fafc;
  border-right: 1px solid #e5e7eb;
  overflow-y: auto;
  z-index: var(--z-elevated);
}

.app-main {
  margin-top: 64px; /* เท่ากับ header height */
  margin-left: 250px; /* เท่ากับ sidebar width */
  padding: 2rem;
  min-height: calc(100vh - 64px);
}

/* 2. Overlay navigation (hamburger menu) */
.overlay-nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: var(--z-overlay);
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
}

.overlay-nav.is-open {
  opacity: 1;
  visibility: visible;
}

.overlay-nav-content {
  position: absolute;
  top: 0;
  left: 0;
  width: 300px;
  height: 100%;
  background-color: white;
  transform: translateX(-100%);
  transition: transform 0.3s ease;
}

.overlay-nav.is-open .overlay-nav-content {
  transform: translateX(0);
}

/* 3. Card stack effect */
.card-stack {
  position: relative;
}

.card-stack .card {
  position: relative;
  background-color: white;
  border-radius: 0.5rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  padding: 1.5rem;
  margin-bottom: 1rem;
}

.card-stack .card:nth-child(1) {
  z-index: 3;
}

.card-stack .card:nth-child(2) {
  z-index: 2;
  transform: translateY(-0.5rem) scale(0.98);
}

.card-stack .card:nth-child(3) {
  z-index: 1;
  transform: translateY(-1rem) scale(0.96);
}

/* 4. Timeline layout */
.timeline {
  position: relative;
  padding: 2rem 0;
}

.timeline::before {
  content: '';
  position: absolute;
  top: 0;
  left: 50%;
  width: 2px;
  height: 100%;
  background-color: #e5e7eb;
  transform: translateX(-50%);
}

.timeline-item {
  position: relative;
  margin-bottom: 2rem;
  width: 45%;
}

.timeline-item:nth-child(odd) {
  left: 0;
}

.timeline-item:nth-child(even) {
  left: 55%;
}

.timeline-item::before {
  content: '';
  position: absolute;
  top: 1rem;
  width: 12px;
  height: 12px;
  background-color: #3b82f6;
  border-radius: 50%;
  z-index: 1;
}

.timeline-item:nth-child(odd)::before {
  right: -6px;
}

.timeline-item:nth-child(even)::before {
  left: -6px;
}
```

### Interactive Components

```css
/* Interactive components ที่ใช้ positioning */

/* 1. Tooltip system */
.tooltip-trigger {
  position: relative;
  display: inline-block;
  cursor: help;
}

.tooltip {
  position: absolute;
  bottom: 100%;
  left: 50%;
  transform: translateX(-50%);
  background-color: #1f2937;
  color: white;
  padding: 0.5rem 0.75rem;
  border-radius: 0.25rem;
  font-size: 0.875rem;
  white-space: nowrap;
  opacity: 0;
  visibility: hidden;
  transition: all 0.2s ease;
  z-index: var(--z-tooltip);
}

.tooltip::after {
  content: '';
  position: absolute;
  top: 100%;
  left: 50%;
  transform: translateX(-50%);
  border: 5px solid transparent;
  border-top-color: #1f2937;
}

.tooltip-trigger:hover .tooltip {
  opacity: 1;
  visibility: visible;
  transform: translateX(-50%) translateY(-5px);
}

/* 2. Dropdown menu */
.dropdown {
  position: relative;
  display: inline-block;
}

.dropdown-toggle {
  background-color: #3b82f6;
  color: white;
  border: none;
  padding: 0.75rem 1rem;
  border-radius: 0.375rem;
  cursor: pointer;
}

.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  min-width: 200px;
  background-color: white;
  border: 1px solid #e5e7eb;
  border-radius: 0.375rem;
  box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
  opacity: 0;
  visibility: hidden;
  transform: translateY(-10px);
  transition: all 0.2s ease;
  z-index: var(--z-dropdown);
}

.dropdown.is-open .dropdown-menu {
  opacity: 1;
  visibility: visible;
  transform: translateY(0);
}

.dropdown-item {
  display: block;
  padding: 0.75rem 1rem;
  text-decoration: none;
  color: #374151;
  border-bottom: 1px solid #f3f4f6;
}

.dropdown-item:hover {
  background-color: #f9fafb;
}

/* 3. Modal dialog */
.modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
  z-index: var(--z-modal);
}

.modal.is-open {
  opacity: 1;
  visibility: visible;
}

.modal-content {
  background-color: white;
  border-radius: 0.5rem;
  padding: 2rem;
  max-width: 90vw;
  max-height: 90vh;
  overflow: auto;
  transform: scale(0.9);
  transition: transform 0.3s ease;
}

.modal.is-open .modal-content {
  transform: scale(1);
}

.modal-close {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
  color: #6b7280;
}

/* 4. Sticky notification bar */
.notification-bar {
  position: sticky;
  top: 0;
  background-color: #3b82f6;
  color: white;
  padding: 0.75rem 1rem;
  text-align: center;
  z-index: var(--z-sticky);
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.notification-close {
  background: none;
  border: none;
  color: white;
  font-size: 1.25rem;
  cursor: pointer;
  opacity: 0.8;
}

.notification-close:hover {
  opacity: 1;
}
```

## สรุป Best Practices

### 1. Position Selection

- **static**: สำหรับ elements ที่ไม่ต้องการ positioning พิเศษ
- **relative**: สำหรับการปรับตำแหน่งเล็กน้อยและเป็น positioning context
- **absolute**: สำหรับ elements ที่ต้องการตำแหน่งที่แน่นอน
- **fixed**: สำหรับ elements ที่ต้องการติดกับ viewport
- **sticky**: สำหรับ elements ที่ต้องการ scroll behavior พิเศษ

### 2. Z-Index Management

- ใช้ systematic z-index scale
- สร้าง CSS custom properties สำหรับ z-index values
- เข้าใจ stacking context
- หลีกเลี่ยงการใช้ z-index ที่สูงเกินจำเป็น

### 3. Performance

- ใช้ transform แทน top/left สำหรับ animations
- หลีกเลี่ยงการเปลี่ยน position บ่อยๆ
- ใช้ will-change อย่างระมัดระวัง

### 4. Responsive Design

- ปรับ positioning strategies สำหรับ mobile
- ใช้ media queries เพื่อเปลี่ยน position values
- พิจารณา touch interactions ใน mobile

### 5. Accessibility

- ใช้ semantic HTML structure
- รองรับ keyboard navigation
- พิจารณา screen reader compatibility
- ใช้ focus management ที่เหมาะสม

การเข้าใจและใช้งาน CSS positioning อย่างถูกต้องจะช่วยสร้าง layouts ที่ยืดหยุ่น responsive และมีประสิทธิภาพ!
