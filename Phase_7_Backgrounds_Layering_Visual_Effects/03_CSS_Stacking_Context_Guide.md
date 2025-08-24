# CSS Stacking Context: การทำความเข้าใจ z-index และ Layer Management

## ภาพรวม Stacking Context

**Stacking Context** เป็นแนวคิดสำคัญใน CSS ที่กำหนดว่า elements จะซ้อนทับกันอย่างไร เมื่อเข้าใจแล้วจะสามารถควบคุม layering ได้อย่างแม่นยำ

### พื้นฐาน Stacking Order

```css
/* ลำดับการซ้อนทับตามธรรมชาติ (ไม่มี z-index) */
.natural-stacking {
  /* ลำดับจากล่างขึ้นบน:
     1. Background และ borders ของ root element
     2. Non-positioned elements ตามลำดับ HTML
     3. Positioned elements ตามลำดับ HTML
     4. Elements ที่มี z-index บวก
  */

  .background-element {
    background-color: #3b82f6;
    /* อยู่ชั้นล่างสุด */
  }

  .normal-element {
    background-color: #22c55e;
    /* อยู่เหนือ background */
  }

  .positioned-element {
    position: relative;
    background-color: #f59e0b;
    /* อยู่เหนือ normal elements */
  }

  .high-z-index {
    position: relative;
    z-index: 10;
    background-color: #ef4444;
    /* อยู่บนสุด */
  }
}
```

## 1. z-index และ Position

### z-index กับ positioned elements

```css
/* z-index ทำงานเฉพาะกับ positioned elements */
.z-index-basics {
  /* ❌ z-index ไม่ทำงานกับ static positioning */
  .static-element {
    position: static; /* default */
    z-index: 999; /* ไม่มีผล */
    background-color: #3b82f6;
  }

  /* ✅ z-index ทำงานกับ positioned elements */
  .relative-element {
    position: relative;
    z-index: 10;
    background-color: #22c55e;
    /* z-index มีผล */
  }

  .absolute-element {
    position: absolute;
    z-index: 20;
    top: 50px;
    left: 50px;
    background-color: #f59e0b;
    /* อยู่เหนือ relative-element */
  }

  .fixed-element {
    position: fixed;
    z-index: 30;
    top: 20px;
    right: 20px;
    background-color: #ef4444;
    /* อยู่บนสุด */
  }

  .sticky-element {
    position: sticky;
    z-index: 25;
    top: 0;
    background-color: #8b5cf6;
    /* z-index ทำงานเมื่อ sticky */
  }
}
```

### การเปรียบเทียบ z-index values

```css
/* การเปรียบเทียบค่า z-index */
.z-index-comparison {
  /* z-index เป็น integer (จำนวนเต็ม) */
  .negative-z {
    position: relative;
    z-index: -1;
    background-color: #6b7280;
    /* อยู่ใต้ elements ที่ไม่มี z-index */
  }

  .zero-z {
    position: relative;
    z-index: 0;
    background-color: #3b82f6;
    /* เท่ากับ default */
  }

  .low-z {
    position: relative;
    z-index: 1;
    background-color: #22c55e;
    /* อยู่เหนือ z-index: 0 */
  }

  .medium-z {
    position: relative;
    z-index: 10;
    background-color: #f59e0b;
    /* อยู่เหนือ z-index: 1 */
  }

  .high-z {
    position: relative;
    z-index: 100;
    background-color: #ef4444;
    /* อยู่เหนือ z-index: 10 */
  }

  .very-high-z {
    position: relative;
    z-index: 9999;
    background-color: #8b5cf6;
    /* อยู่บนสุด */
  }

  /* ❌ ค่าที่ไม่ถูกต้อง */
  .invalid-z {
    position: relative;
    z-index: 1.5; /* ไม่ใช่จำนวนเต็ม - จะกลายเป็น 1 */
    z-index: auto; /* ค่า default */
    z-index: inherit; /* รับค่าจาก parent */
  }
}
```

## 2. Stacking Context Creation

### Properties ที่สร้าง Stacking Context

```css
/* Properties ที่สร้าง stacking context ใหม่ */
.stacking-context-creators {
  /* 1. Root element (html) - สร้าง root stacking context */

  /* 2. Position + z-index */
  .positioned-with-z {
    position: relative;
    z-index: 1;
    /* สร้าง stacking context */
  }

  /* 3. Opacity < 1 */
  .opacity-element {
    opacity: 0.9;
    /* สร้าง stacking context */
  }

  /* 4. Transform (any value except 'none') */
  .transform-element {
    transform: translateX(10px);
    /* สร้าง stacking context */
  }

  .transform-scale {
    transform: scale(1.1);
    /* สร้าง stacking context */
  }

  .transform-rotate {
    transform: rotate(5deg);
    /* สร้าง stacking context */
  }

  /* 5. Filter */
  .filter-element {
    filter: blur(2px);
    /* สร้าง stacking context */
  }

  .filter-shadow {
    filter: drop-shadow(0 4px 8px rgba(0, 0, 0, 0.1));
    /* สร้าง stacking context */
  }

  /* 6. Isolation */
  .isolation-element {
    isolation: isolate;
    /* สร้าง stacking context */
  }

  /* 7. Mix-blend-mode */
  .blend-mode-element {
    mix-blend-mode: multiply;
    /* สร้าง stacking context */
  }

  /* 8. Will-change */
  .will-change-element {
    will-change: transform;
    /* อาจสร้าง stacking context */
  }

  /* 9. Contain */
  .contain-element {
    contain: layout;
    /* สร้าง stacking context */
  }

  /* 10. Flexbox และ Grid children ที่มี z-index */
  .flex-container {
    display: flex;
  }

  .flex-child-with-z {
    z-index: 1;
    /* สร้าง stacking context ใน flex container */
  }

  .grid-container {
    display: grid;
  }

  .grid-child-with-z {
    z-index: 1;
    /* สร้าง stacking context ใน grid container */
  }
}
```

### ตัวอย่างการทำงานของ Stacking Context

```css
/* ตัวอย่างการทำงานของ stacking context */
.stacking-context-examples {
  /* Example 1: Basic stacking context */
  .parent-context {
    position: relative;
    z-index: 1;
    background-color: #f3f4f6;
    padding: 20px;
    /* สร้าง stacking context */
  }

  .child-high-z {
    position: relative;
    z-index: 999;
    background-color: #3b82f6;
    /* z-index สูงแต่อยู่ใน parent context */
  }

  .outside-low-z {
    position: relative;
    z-index: 2;
    background-color: #ef4444;
    /* z-index ต่ำแต่อยู่นอก parent context
       จะอยู่เหนือ child-high-z */
  }

  /* Example 2: Opacity creating context */
  .opacity-parent {
    opacity: 0.9;
    background-color: #22c55e;
    /* สร้าง stacking context */
  }

  .opacity-child {
    position: relative;
    z-index: 100;
    background-color: #f59e0b;
    /* อยู่ใน opacity context */
  }

  .normal-sibling {
    position: relative;
    z-index: 1;
    background-color: #8b5cf6;
    /* อาจอยู่เหนือ opacity-child ขึ้นอยู่กับ opacity-parent */
  }

  /* Example 3: Transform creating context */
  .transform-parent {
    transform: translateZ(0);
    background-color: #ec4899;
    /* สร้าง stacking context */
  }

  .transform-child {
    position: relative;
    z-index: 50;
    background-color: #06b6d4;
    /* อยู่ใน transform context */
  }
}
```

## 3. Advanced Stacking Scenarios

### Complex Layering Situations

```css
/* สถานการณ์ซับซ้อนของ stacking */
.complex-stacking {
  /* Modal และ Overlay management */
  .modal-backdrop {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.5);
    z-index: 1000;
    /* Modal backdrop */
  }

  .modal-content {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: white;
    z-index: 1001;
    border-radius: 8px;
    padding: 24px;
    /* Modal content อยู่เหนือ backdrop */
  }

  .modal-close-button {
    position: absolute;
    top: 12px;
    right: 12px;
    z-index: 1002;
    background: none;
    border: none;
    font-size: 24px;
    cursor: pointer;
    /* Close button อยู่บนสุดใน modal */
  }

  /* Dropdown menu management */
  .dropdown {
    position: relative;
    display: inline-block;
  }

  .dropdown-button {
    background-color: #3b82f6;
    color: white;
    padding: 12px 16px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }

  .dropdown-menu {
    position: absolute;
    top: 100%;
    left: 0;
    background-color: white;
    border: 1px solid #e5e7eb;
    border-radius: 4px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    z-index: 100;
    min-width: 160px;
    /* Dropdown menu */
  }

  .dropdown-item {
    display: block;
    padding: 8px 16px;
    text-decoration: none;
    color: #374151;
    border-bottom: 1px solid #f3f4f6;
  }

  .dropdown-item:hover {
    background-color: #f9fafb;
  }

  /* Tooltip management */
  .tooltip-container {
    position: relative;
    display: inline-block;
  }

  .tooltip {
    position: absolute;
    bottom: 125%;
    left: 50%;
    transform: translateX(-50%);
    background-color: #1f2937;
    color: white;
    padding: 8px 12px;
    border-radius: 4px;
    font-size: 14px;
    white-space: nowrap;
    z-index: 200;
    opacity: 0;
    visibility: hidden;
    transition: opacity 0.3s, visibility 0.3s;
    /* Tooltip */
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

  .tooltip-container:hover .tooltip {
    opacity: 1;
    visibility: visible;
  }
}
```

### CSS Grid และ Flexbox Stacking

```css
/* Stacking ใน CSS Grid และ Flexbox */
.layout-stacking {
  /* Grid stacking */
  .grid-container {
    display: grid;
    grid-template-areas:
      'header header'
      'sidebar main'
      'footer footer';
    grid-template-rows: auto 1fr auto;
    grid-template-columns: 250px 1fr;
    min-height: 100vh;
  }

  .grid-header {
    grid-area: header;
    background-color: #3b82f6;
    position: sticky;
    top: 0;
    z-index: 100;
    /* Header ติด top */
  }

  .grid-sidebar {
    grid-area: sidebar;
    background-color: #f3f4f6;
    position: relative;
    z-index: 10;
    /* Sidebar */
  }

  .grid-main {
    grid-area: main;
    background-color: white;
    position: relative;
    /* Main content */
  }

  .grid-footer {
    grid-area: footer;
    background-color: #374151;
    color: white;
    /* Footer */
  }

  /* Overlapping grid items */
  .grid-overlay-container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 200px;
  }

  .grid-item-1 {
    grid-column: 1 / 2;
    grid-row: 1 / 2;
    background-color: #3b82f6;
    z-index: 1;
  }

  .grid-item-2 {
    grid-column: 1 / 3;
    grid-row: 1 / 2;
    background-color: rgba(239, 68, 68, 0.8);
    z-index: 2;
    margin-left: 50px;
    /* ทับซ้อนกับ item-1 */
  }

  /* Flex stacking */
  .flex-container {
    display: flex;
    position: relative;
    height: 300px;
  }

  .flex-item {
    flex: 1;
    background-color: #22c55e;
    margin: 10px;
    position: relative;
  }

  .flex-item:nth-child(2) {
    z-index: 2;
    transform: translateX(-20px);
    /* ทับซ้อนกับ item อื่น */
  }

  .flex-overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(139, 92, 246, 0.5);
    z-index: 10;
    /* Overlay ทั้ง flex container */
  }
}
```

## 4. Debugging Stacking Issues

### เครื่องมือ Debug Stacking Context

```css
/* วิธี debug stacking context issues */
.debug-stacking {
  /* เพิ่ม outline เพื่อเห็น boundaries */
  .debug-outline * {
    outline: 1px solid red;
    outline-offset: -1px;
  }

  /* เพิ่ม background สีต่างๆ */
  .debug-backgrounds .layer-1 {
    background-color: rgba(255, 0, 0, 0.3);
  }

  .debug-backgrounds .layer-2 {
    background-color: rgba(0, 255, 0, 0.3);
  }

  .debug-backgrounds .layer-3 {
    background-color: rgba(0, 0, 255, 0.3);
  }

  /* แสดง z-index values */
  .debug-z-index::before {
    content: 'z-index: ' attr(data-z-index);
    position: absolute;
    top: 0;
    left: 0;
    background-color: black;
    color: white;
    padding: 2px 4px;
    font-size: 10px;
    z-index: 9999;
  }

  /* Test stacking context creation */
  .test-context {
    /* เทสว่าสร้าง stacking context หรือไม่ */
    position: relative;
    z-index: 1;
    /* ลองใส่ z-index */
  }

  .test-context::after {
    content: 'Context: ' attr(data-context);
    position: absolute;
    bottom: 0;
    right: 0;
    background-color: yellow;
    color: black;
    padding: 2px 4px;
    font-size: 10px;
  }
}
```

### Common Stacking Problems และ Solutions

```css
/* ปัญหาที่พบบ่อยและวิธีแก้ */
.stacking-problems {
  /* Problem 1: z-index ไม่ทำงาน */
  .problem-static {
    /* ❌ ปัญหา: element เป็น static */
    position: static;
    z-index: 999; /* ไม่มีผล */
  }

  .solution-positioned {
    /* ✅ แก้ไข: เปลี่ยนเป็น positioned */
    position: relative;
    z-index: 999; /* ทำงาน */
  }

  /* Problem 2: Child ไม่ขึ้นมาเหนือ sibling ของ parent */
  .problem-parent {
    position: relative;
    z-index: 1;
    /* สร้าง stacking context */
  }

  .problem-child {
    position: relative;
    z-index: 999;
    /* อยู่ใน parent context - ไม่สามารถขึ้นเหนือ sibling ของ parent */
  }

  .solution-parent {
    /* ✅ แก้ไข: เพิ่ม z-index ของ parent */
    position: relative;
    z-index: 1000;
  }

  .solution-child {
    position: relative;
    z-index: 999;
    /* ตอนนี้สามารถขึ้นเหนือ siblings ของ parent ได้ */
  }

  /* Problem 3: Opacity/Transform สร้าง context ไม่คาดคิด */
  .problem-opacity {
    opacity: 0.99;
    /* สร้าง stacking context โดยไม่ตั้งใจ */
  }

  .problem-opacity-child {
    position: relative;
    z-index: 100;
    /* อยู่ใน opacity context */
  }

  .solution-remove-opacity {
    /* ✅ แก้ไข: เอา opacity ออกหรือใช้ rgba */
    background-color: rgba(255, 255, 255, 0.99);
    /* แทน opacity */
  }

  /* Problem 4: Will-change สร้าง context */
  .problem-will-change {
    will-change: transform;
    /* สร้าง stacking context */
  }

  .solution-will-change {
    /* ✅ แก้ไข: เอา will-change ออกเมื่อไม่ต้องการ */
    will-change: auto;
  }

  /* Problem 5: Flex/Grid children ที่มี z-index */
  .flex-parent {
    display: flex;
  }

  .flex-child-problem {
    z-index: 1;
    /* สร้าง stacking context ใน flex container */
  }

  .solution-no-z-index {
    /* ✅ แก้ไข: ใช้ order แทน z-index ใน flex */
    order: 2;
  }
}
```

## 5. Best Practices และ Patterns

### Z-index Management Systems

```css
/* ระบบจัดการ z-index */
:root {
  /* Z-index scale */
  --z-negative: -1;
  --z-default: 0;
  --z-content: 1;
  --z-header: 10;
  --z-sidebar: 20;
  --z-dropdown: 100;
  --z-tooltip: 200;
  --z-modal-backdrop: 1000;
  --z-modal-content: 1001;
  --z-notification: 1100;
  --z-debug: 9999;
}

.z-index-system {
  /* Content layers */
  .content-base {
    z-index: var(--z-content);
  }

  /* Navigation layers */
  .header {
    position: sticky;
    top: 0;
    z-index: var(--z-header);
  }

  .sidebar {
    position: fixed;
    z-index: var(--z-sidebar);
  }

  /* Interactive layers */
  .dropdown {
    z-index: var(--z-dropdown);
  }

  .tooltip {
    z-index: var(--z-tooltip);
  }

  /* Modal layers */
  .modal-backdrop {
    z-index: var(--z-modal-backdrop);
  }

  .modal-content {
    z-index: var(--z-modal-content);
  }

  /* Notification layers */
  .notification {
    position: fixed;
    top: 20px;
    right: 20px;
    z-index: var(--z-notification);
  }

  /* Debug layers */
  .debug-overlay {
    z-index: var(--z-debug);
  }
}
```

### Responsive Stacking

```css
/* Responsive stacking patterns */
.responsive-stacking {
  /* Mobile-first stacking */
  .mobile-nav {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: var(--z-header);
    background-color: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .mobile-menu {
    position: fixed;
    top: 60px;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: white;
    z-index: calc(var(--z-header) - 1);
    transform: translateX(-100%);
    transition: transform 0.3s ease;
  }

  .mobile-menu.open {
    transform: translateX(0);
  }

  /* Desktop stacking */
  @media (min-width: 768px) {
    .desktop-layout {
      display: grid;
      grid-template-columns: 250px 1fr;
    }

    .desktop-sidebar {
      position: sticky;
      top: 80px;
      height: calc(100vh - 80px);
      z-index: var(--z-sidebar);
      /* Sidebar ใน desktop */
    }

    .mobile-menu {
      /* Reset mobile styles */
      position: static;
      transform: none;
      background: none;
      z-index: auto;
    }
  }

  /* Print stacking */
  @media print {
    * {
      /* Reset z-index เมื่อพิมพ์ */
      z-index: auto !important;
      position: static !important;
    }
  }
}
```

### Performance-Optimized Stacking

```css
/* Stacking ที่เพิ่มประสิทธิภาพ */
.performance-stacking {
  /* ใช้ isolation แทน z-index เมื่อเป็นไปได้ */
  .isolated-layer {
    isolation: isolate;
    /* สร้าง stacking context โดยไม่ใช้ z-index */
  }

  /* ใช้ transform แทน position เมื่อเป็นไปได้ */
  .transform-layer {
    transform: translateZ(0);
    /* สร้าง stacking context และ GPU acceleration */
  }

  /* จำกัดการใช้ will-change */
  .animation-layer {
    will-change: transform;
    /* ใช้เฉพาะตอน animate */
  }

  .animation-layer.animation-complete {
    will-change: auto;
    /* เอาออกเมื่อ animation เสร็จ */
  }

  /* ใช้ contain เพื่อจำกัด scope */
  .contained-layer {
    contain: layout style paint;
    /* จำกัดผลกระทบของ style changes */
  }

  /* เพิ่มประสิทธิภาพ modal */
  .efficient-modal {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: var(--z-modal-backdrop);
    backdrop-filter: blur(4px);
    /* ใช้ backdrop-filter แทน overlay element */
  }

  .efficient-modal-content {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    /* ไม่ต้องใช้ z-index เพิ่ม */
  }
}
```

## 6. Modern Stacking Techniques

### CSS Container Queries และ Stacking

```css
/* Stacking กับ Container Queries */
.container-stacking {
  .adaptive-component {
    container-type: size;
    position: relative;
  }

  /* Stacking ปรับตาม container size */
  @container (width > 400px) {
    .adaptive-layer {
      position: absolute;
      top: 0;
      right: 0;
      z-index: 1;
      /* แสดง overlay เมื่อ container ใหญ่พอ */
    }
  }

  @container (width <= 400px) {
    .adaptive-layer {
      position: static;
      z-index: auto;
      /* เป็น normal flow เมื่อ container เล็ก */
    }
  }
}
```

### CSS Cascade Layers และ Stacking

```css
/* Cascade layers สำหรับ stacking management */
@layer base, components, utilities;

@layer base {
  .base-element {
    z-index: var(--z-content);
  }
}

@layer components {
  .component-modal {
    z-index: var(--z-modal-content);
  }
}

@layer utilities {
  .utility-debug {
    z-index: var(--z-debug) !important;
  }
}
```

## สรุป: Stacking Context Best Practices

### Key Concepts 🎯

1. **Stacking Context Creation**

   ```css
   /* Properties ที่สร้าง stacking context */
   .creates-context {
     position: relative;
     z-index: 1; /* position + z-index */
     opacity: 0.9; /* opacity < 1 */
     transform: translateZ(0); /* any transform */
     filter: blur(1px); /* any filter */
     isolation: isolate; /* isolation */
   }
   ```

2. **Z-index Management**

   ```css
   /* ระบบจัดการ z-index */
   :root {
     --z-content: 1;
     --z-dropdown: 100;
     --z-modal: 1000;
   }
   ```

3. **Debugging Techniques**

   ```css
   /* Debug stacking */
   .debug * {
     outline: 1px solid red;
   }
   ```

4. **Performance Considerations**
   - ใช้ `isolation: isolate` แทน z-index เมื่อเป็นไปได้
   - จำกัดการใช้ `will-change`
   - ใช้ CSS custom properties สำหรับ z-index values

### Quick Reference 📋

```css
/* Stacking essentials */
.stacking-essentials {
  /* Basic stacking */
  .positioned {
    position: relative;
    z-index: 10;
  }

  /* Context creation */
  .context {
    opacity: 0.99;
    /* หรือ transform: translateZ(0); */
  }

  /* Modal pattern */
  .modal {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 1000;
  }

  /* Debug pattern */
  .debug {
    outline: 2px solid red;
    background: rgba(255, 0, 0, 0.1);
  }
}
```

การเข้าใจ Stacking Context และ z-index เป็นสิ่งสำคัญสำหรับการควบคุม layering ใน CSS ให้ได้ผลลัพธ์ที่ต้องการ!
