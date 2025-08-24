# CSS Box-Shadow: คู่มือฉบับสมบูรณ์

## ภาพรวม Box-Shadow Property

`box-shadow` เป็น CSS property ที่ใช้สร้างเงาให้กับ elements ซึ่งเป็นเครื่องมือสำคัญในการเพิ่มความลึก (depth) และมิติ (dimension) ให้กับการออกแบบ ทำให้ UI ดูสวยงาม สมจริง และมี visual hierarchy ที่ชัดเจน

### Syntax และ Structure

```css
/* Basic syntax */
.box-shadow-basic {
  box-shadow: [inset] [offset-x] [offset-y] [blur-radius] [spread-radius]
    [color];
}

/* Multiple shadows */
.box-shadow-multiple {
  box-shadow: shadow1, shadow2, shadow3;
}

/* ตัวอย่างพื้นฐาน */
.shadow-example {
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  /*
    0 = offset-x (ไม่เลื่อนซ้าย-ขวา)
    4px = offset-y (เลื่อนลง 4px)
    6px = blur-radius (เบลอ 6px)
    rgba(0, 0, 0, 0.1) = สีดำโปร่งใส 90%
  */
}

/* ตัวอย่างครบทุก parameter */
.shadow-complete {
  box-shadow: 2px 4px 8px 2px rgba(0, 0, 0, 0.2);
  /*
    2px = offset-x (เลื่อนขวา 2px)
    4px = offset-y (เลื่อนลง 4px)
    8px = blur-radius (เบลอ 8px)
    2px = spread-radius (ขยายเงา 2px)
    rgba(0, 0, 0, 0.2) = สีดำโปร่งใส 80%
  */
}
```

## 1. พารามิเตอร์ของ Box-Shadow

### offset-x และ offset-y: การเลื่อนเงา

```css
/* Horizontal offset (offset-x) */
.shadow-offset-x {
  /* เลื่อนเงาไปทางขวา */
  box-shadow: 5px 0 10px rgba(0, 0, 0, 0.2);

  /* เลื่อนเงาไปทางซ้าย */
  box-shadow: -5px 0 10px rgba(0, 0, 0, 0.2);

  /* ไม่เลื่อนแนวนอน */
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}

/* Vertical offset (offset-y) */
.shadow-offset-y {
  /* เลื่อนเงาลงด้านล่าง */
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);

  /* เลื่อนเงาขึ้นด้านบน */
  box-shadow: 0 -5px 10px rgba(0, 0, 0, 0.2);

  /* ไม่เลื่อนแนวตั้ง */
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
}

/* Combined offsets */
.shadow-combined-offset {
  /* เงาทแยงมุมขวาล่าง */
  box-shadow: 3px 3px 8px rgba(0, 0, 0, 0.15);

  /* เงาทแยงมุมซ้ายบน */
  box-shadow: -3px -3px 8px rgba(0, 0, 0, 0.15);

  /* เงาทแยงมุมซ้ายล่าง */
  box-shadow: -3px 3px 8px rgba(0, 0, 0, 0.15);

  /* เงาทแยงมุมขวาบน */
  box-shadow: 3px -3px 8px rgba(0, 0, 0, 0.15);
}

/* Direction examples */
.shadow-directions {
  /* เงาด้านล่าง (ปกติ) */
  .shadow-bottom {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  /* เงาด้านบน */
  .shadow-top {
    box-shadow: 0 -4px 6px rgba(0, 0, 0, 0.1);
  }

  /* เงาด้านซ้าย */
  .shadow-left {
    box-shadow: -4px 0 6px rgba(0, 0, 0, 0.1);
  }

  /* เงาด้านขวา */
  .shadow-right {
    box-shadow: 4px 0 6px rgba(0, 0, 0, 0.1);
  }

  /* เงารอบๆ (ไม่มี offset) */
  .shadow-around {
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
}
```

### blur-radius: การเบลอเงา

```css
/* Blur radius variations */
.shadow-blur-variations {
  /* เงาคมชัด (ไม่เบลอ) */
  .shadow-sharp {
    box-shadow: 2px 2px 0 rgba(0, 0, 0, 0.3);
  }

  /* เบลอเล็กน้อย */
  .shadow-slight-blur {
    box-shadow: 2px 2px 2px rgba(0, 0, 0, 0.3);
  }

  /* เบลอปานกลาง */
  .shadow-medium-blur {
    box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.2);
  }

  /* เบลอมาก */
  .shadow-heavy-blur {
    box-shadow: 2px 2px 20px rgba(0, 0, 0, 0.15);
  }

  /* เบลอมากมาก (soft shadow) */
  .shadow-very-soft {
    box-shadow: 2px 2px 40px rgba(0, 0, 0, 0.1);
  }
}

/* Blur effects for different purposes */
.shadow-blur-purposes {
  /* การ์ดที่ลอยเล็กน้อย */
  .card-subtle {
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }

  /* การ์ดที่ลอยปานกลาง */
  .card-medium {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  /* การ์ดที่ลอยสูง */
  .card-elevated {
    box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
  }

  /* Modal overlay */
  .modal-shadow {
    box-shadow: 0 25px 50px rgba(0, 0, 0, 0.25);
  }
}
```

### spread-radius: การขยายเงา

```css
/* Spread radius examples */
.shadow-spread-examples {
  /* ไม่มี spread (เงาขนาดเท่า element) */
  .no-spread {
    box-shadow: 0 4px 6px 0 rgba(0, 0, 0, 0.1);
  }

  /* Positive spread (เงาใหญ่กว่า element) */
  .positive-spread {
    box-shadow: 0 4px 6px 2px rgba(0, 0, 0, 0.1);
  }

  /* Large positive spread */
  .large-spread {
    box-shadow: 0 4px 6px 8px rgba(0, 0, 0, 0.1);
  }

  /* Negative spread (เงาเล็กกว่า element) */
  .negative-spread {
    box-shadow: 0 4px 6px -2px rgba(0, 0, 0, 0.1);
  }

  /* Large negative spread */
  .large-negative-spread {
    box-shadow: 0 4px 20px -8px rgba(0, 0, 0, 0.2);
  }
}

/* Practical spread usage */
.shadow-spread-practical {
  /* Border-like shadow */
  .border-shadow {
    box-shadow: 0 0 0 1px rgba(0, 0, 0, 0.1);
  }

  /* Thick border shadow */
  .thick-border-shadow {
    box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.2);
  }

  /* Glow effect */
  .glow-effect {
    box-shadow: 0 0 20px 5px rgba(59, 130, 246, 0.3);
  }

  /* Inward shadow effect (using negative spread) */
  .inward-effect {
    box-shadow: 0 8px 16px -4px rgba(0, 0, 0, 0.1);
  }
}
```

### color: สีของเงา

```css
/* Shadow colors */
.shadow-colors {
  /* สีดำ (ปกติ) */
  .black-shadow {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  /* สีเทา */
  .gray-shadow {
    box-shadow: 0 4px 6px rgba(107, 114, 128, 0.15);
  }

  /* สีน้ำเงิน */
  .blue-shadow {
    box-shadow: 0 4px 6px rgba(59, 130, 246, 0.2);
  }

  /* สีเขียว */
  .green-shadow {
    box-shadow: 0 4px 6px rgba(16, 185, 129, 0.2);
  }

  /* สีแดง */
  .red-shadow {
    box-shadow: 0 4px 6px rgba(239, 68, 68, 0.2);
  }

  /* สีม่วง */
  .purple-shadow {
    box-shadow: 0 4px 6px rgba(139, 92, 246, 0.2);
  }
}

/* Brand shadow colors */
.brand-shadows {
  /* Primary brand shadow */
  .primary-shadow {
    --primary-color: 59, 130, 246;
    box-shadow: 0 4px 14px rgba(var(--primary-color), 0.15);
  }

  /* Success shadow */
  .success-shadow {
    --success-color: 16, 185, 129;
    box-shadow: 0 4px 14px rgba(var(--success-color), 0.15);
  }

  /* Warning shadow */
  .warning-shadow {
    --warning-color: 245, 158, 11;
    box-shadow: 0 4px 14px rgba(var(--warning-color), 0.15);
  }

  /* Danger shadow */
  .danger-shadow {
    --danger-color: 239, 68, 68;
    box-shadow: 0 4px 14px rgba(var(--danger-color), 0.15);
  }
}

/* Color intensity variations */
.shadow-intensity {
  /* เงาอ่อน */
  .light-shadow {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
  }

  /* เงาปานกลาง */
  .medium-shadow {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  /* เงาเข้ม */
  .dark-shadow {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
  }

  /* เงาเข้มมาก */
  .very-dark-shadow {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.4);
  }
}
```

## 2. inset Shadows: เงาภายใน

### ความหมายและการใช้งาน

```css
/* Basic inset shadows */
.inset-shadows {
  /* เงาภายในด้านบน */
  .inset-top {
    box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  /* เงาภายในด้านล่าง */
  .inset-bottom {
    box-shadow: inset 0 -2px 4px rgba(0, 0, 0, 0.1);
  }

  /* เงาภายในด้านซ้าย */
  .inset-left {
    box-shadow: inset 2px 0 4px rgba(0, 0, 0, 0.1);
  }

  /* เงาภายในด้านขวา */
  .inset-right {
    box-shadow: inset -2px 0 4px rgba(0, 0, 0, 0.1);
  }

  /* เงาภายในรอบๆ */
  .inset-all {
    box-shadow: inset 0 0 8px rgba(0, 0, 0, 0.1);
  }
}

/* Inset effects for UI elements */
.inset-ui-effects {
  /* Pressed button effect */
  .button-pressed {
    box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.2);
    transform: translateY(1px);
  }

  /* Input field focus */
  .input-focused {
    box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1), 0 0 0 3px rgba(59, 130, 246, 0.1);
  }

  /* Well/container effect */
  .well-container {
    box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.1);
    background-color: #f8f9fa;
    border-radius: 0.375rem;
    padding: 1rem;
  }

  /* Carved/etched effect */
  .carved-effect {
    box-shadow: inset 1px 1px 2px rgba(0, 0, 0, 0.2), inset -1px -1px 2px rgba(255, 255, 255, 0.7);
    background-color: #e5e7eb;
  }
}

/* Complex inset patterns */
.complex-inset {
  /* Beveled edge */
  .beveled {
    box-shadow: inset 2px 2px 5px rgba(255, 255, 255, 0.8), inset -2px -2px 5px
        rgba(0, 0, 0, 0.1);
  }

  /* Embossed effect */
  .embossed {
    box-shadow: inset -1px -1px 2px rgba(0, 0, 0, 0.1), inset 1px 1px 2px rgba(255, 255, 255, 0.8);
  }

  /* Recessed container */
  .recessed {
    box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.2), 0 1px 0 rgba(255, 255, 255, 0.8);
  }
}
```

## 3. Multiple Shadows: เงาหลายชั้น

### การรวมเงาหลายแบบ

```css
/* Multiple shadow combinations */
.multiple-shadows {
  /* เงาชั้นเดียวกับ border */
  .shadow-with-border {
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1), 0 0 0 1px rgba(0, 0, 0, 0.05);
  }

  /* เงาสองชั้น */
  .two-layer-shadow {
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1), 0 4px 6px rgba(0, 0, 0, 0.05);
  }

  /* เงาสามชั้น */
  .three-layer-shadow {
    box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1), 0 4px 8px rgba(0, 0, 0, 0.1),
      0 8px 16px rgba(0, 0, 0, 0.1);
  }

  /* เงาซับซ้อน */
  .complex-shadow {
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1), 0 4px 6px rgba(0, 0, 0, 0.05),
      0 10px 20px rgba(0, 0, 0, 0.05), 0 20px 40px rgba(0, 0, 0, 0.05);
  }
}

/* Material Design inspired shadows */
.material-shadows {
  /* Elevation 1 */
  .elevation-1 {
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
  }

  /* Elevation 2 */
  .elevation-2 {
    box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16), 0 3px 6px rgba(0, 0, 0, 0.23);
  }

  /* Elevation 3 */
  .elevation-3 {
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
  }

  /* Elevation 4 */
  .elevation-4 {
    box-shadow: 0 14px 28px rgba(0, 0, 0, 0.25), 0 10px 10px rgba(0, 0, 0, 0.22);
  }

  /* Elevation 5 */
  .elevation-5 {
    box-shadow: 0 19px 38px rgba(0, 0, 0, 0.3), 0 15px 12px rgba(0, 0, 0, 0.22);
  }
}

/* Creative multiple shadow effects */
.creative-multiple {
  /* Neon glow */
  .neon-glow {
    background-color: #1a1a1a;
    color: #00ffff;
    box-shadow: 0 0 5px #00ffff, 0 0 10px #00ffff, 0 0 20px #00ffff, 0 0 40px
        #00ffff;
  }

  /* Paper stack effect */
  .paper-stack {
    background-color: white;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1), 2px 2px 0 #f8f9fa,
      4px 4px 0 #e9ecef;
  }

  /* Double border */
  .double-border {
    box-shadow: 0 0 0 1px #e5e7eb, 0 0 0 3px #3b82f6;
  }

  /* Layered glow */
  .layered-glow {
    box-shadow: 0 0 10px rgba(59, 130, 246, 0.3), 0 0 20px rgba(59, 130, 246, 0.2),
      0 0 40px rgba(59, 130, 246, 0.1), 0 4px 8px rgba(0, 0, 0, 0.1);
  }
}
```

## 4. Shadow Presets และ Design Systems

### Common Shadow Scales

```css
/* Shadow scale system */
:root {
  /* Shadow levels */
  --shadow-xs: 0 1px 2px rgba(0, 0, 0, 0.05);
  --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.1), 0 1px 2px rgba(0, 0, 0, 0.06);
  --shadow-md: 0 4px 6px rgba(0, 0, 0, 0.07), 0 2px 4px rgba(0, 0, 0, 0.06);
  --shadow-lg: 0 10px 15px rgba(0, 0, 0, 0.1), 0 4px 6px rgba(0, 0, 0, 0.05);
  --shadow-xl: 0 20px 25px rgba(0, 0, 0, 0.1), 0 10px 10px rgba(0, 0, 0, 0.04);
  --shadow-2xl: 0 25px 50px rgba(0, 0, 0, 0.25);
  --shadow-inner: inset 0 2px 4px rgba(0, 0, 0, 0.06);
  --shadow-none: 0 0 #0000;

  /* Colored shadows */
  --shadow-blue: 0 4px 14px rgba(59, 130, 246, 0.15);
  --shadow-green: 0 4px 14px rgba(16, 185, 129, 0.15);
  --shadow-red: 0 4px 14px rgba(239, 68, 68, 0.15);
  --shadow-yellow: 0 4px 14px rgba(245, 158, 11, 0.15);
  --shadow-purple: 0 4px 14px rgba(139, 92, 246, 0.15);
}

/* Using shadow variables */
.shadow-utilities {
  .shadow-xs {
    box-shadow: var(--shadow-xs);
  }
  .shadow-sm {
    box-shadow: var(--shadow-sm);
  }
  .shadow-md {
    box-shadow: var(--shadow-md);
  }
  .shadow-lg {
    box-shadow: var(--shadow-lg);
  }
  .shadow-xl {
    box-shadow: var(--shadow-xl);
  }
  .shadow-2xl {
    box-shadow: var(--shadow-2xl);
  }
  .shadow-inner {
    box-shadow: var(--shadow-inner);
  }
  .shadow-none {
    box-shadow: var(--shadow-none);
  }

  .shadow-blue {
    box-shadow: var(--shadow-blue);
  }
  .shadow-green {
    box-shadow: var(--shadow-green);
  }
  .shadow-red {
    box-shadow: var(--shadow-red);
  }
  .shadow-yellow {
    box-shadow: var(--shadow-yellow);
  }
  .shadow-purple {
    box-shadow: var(--shadow-purple);
  }
}
```

### Component-Specific Shadows

```css
/* Card shadows */
.card-shadows {
  .card-flat {
    box-shadow: none;
    border: 1px solid #e5e7eb;
  }

  .card-raised {
    box-shadow: var(--shadow-sm);
    border: 1px solid transparent;
  }

  .card-floating {
    box-shadow: var(--shadow-lg);
  }

  .card-modal {
    box-shadow: var(--shadow-2xl);
  }
}

/* Button shadows */
.button-shadows {
  .btn-flat {
    box-shadow: none;
  }

  .btn-raised {
    box-shadow: var(--shadow-sm);
  }

  .btn-raised:hover {
    box-shadow: var(--shadow-md);
    transform: translateY(-1px);
  }

  .btn-raised:active {
    box-shadow: var(--shadow-xs);
    transform: translateY(0);
  }

  .btn-floating {
    box-shadow: var(--shadow-lg);
    border-radius: 50%;
  }

  .btn-floating:hover {
    box-shadow: var(--shadow-xl);
  }
}

/* Input shadows */
.input-shadows {
  .input-default {
    box-shadow: var(--shadow-xs);
    border: 1px solid #d1d5db;
  }

  .input-default:focus {
    box-shadow: var(--shadow-xs), 0 0 0 3px rgba(59, 130, 246, 0.1);
    border-color: #3b82f6;
  }

  .input-error {
    box-shadow: var(--shadow-xs), 0 0 0 3px rgba(239, 68, 68, 0.1);
    border-color: #ef4444;
  }

  .input-success {
    box-shadow: var(--shadow-xs), 0 0 0 3px rgba(16, 185, 129, 0.1);
    border-color: #10b981;
  }
}

/* Navigation shadows */
.nav-shadows {
  .navbar {
    box-shadow: var(--shadow-sm);
    background: white;
    position: sticky;
    top: 0;
    z-index: 100;
  }

  .dropdown-menu {
    box-shadow: var(--shadow-lg);
    background: white;
    border: 1px solid #e5e7eb;
    border-radius: 0.375rem;
  }

  .sidebar {
    box-shadow: var(--shadow-md);
    background: white;
  }
}
```

## 5. Interactive Shadow Effects

### Hover และ Focus Effects

```css
/* Interactive shadow animations */
.interactive-shadows {
  .card-interactive {
    background: white;
    border-radius: 0.5rem;
    padding: 1.5rem;
    box-shadow: var(--shadow-sm);
    transition: all 0.3s ease;
    cursor: pointer;
  }

  .card-interactive:hover {
    box-shadow: var(--shadow-lg);
    transform: translateY(-2px);
  }

  .card-interactive:active {
    box-shadow: var(--shadow-md);
    transform: translateY(0);
  }
}

/* Button interactions */
.button-interactions {
  .btn-shadow {
    background: #3b82f6;
    color: white;
    padding: 0.75rem 1.5rem;
    border: none;
    border-radius: 0.375rem;
    box-shadow: var(--shadow-sm);
    transition: all 0.2s ease;
    cursor: pointer;
  }

  .btn-shadow:hover {
    box-shadow: var(--shadow-md);
    transform: translateY(-1px);
  }

  .btn-shadow:active {
    box-shadow: var(--shadow-xs);
    transform: translateY(0);
  }

  .btn-shadow:focus {
    outline: none;
    box-shadow: var(--shadow-md), 0 0 0 3px rgba(59, 130, 246, 0.2);
  }
}

/* Image hover effects */
.image-hover-shadows {
  .image-card {
    border-radius: 0.5rem;
    overflow: hidden;
    box-shadow: var(--shadow-sm);
    transition: all 0.3s ease;
  }

  .image-card:hover {
    box-shadow: var(--shadow-xl);
    transform: scale(1.02);
  }

  .image-card img {
    width: 100%;
    height: 200px;
    object-fit: cover;
    transition: transform 0.3s ease;
  }

  .image-card:hover img {
    transform: scale(1.1);
  }
}

/* Progressive shadow loading */
.progressive-shadows {
  .card-loading {
    box-shadow: var(--shadow-xs);
    animation: shadow-pulse 2s ease-in-out infinite;
  }

  @keyframes shadow-pulse {
    0%,
    100% {
      box-shadow: var(--shadow-xs);
    }
    50% {
      box-shadow: var(--shadow-md);
    }
  }

  .card-loaded {
    box-shadow: var(--shadow-sm);
    animation: shadow-appear 0.5s ease-out;
  }

  @keyframes shadow-appear {
    from {
      box-shadow: none;
      transform: translateY(10px);
      opacity: 0;
    }
    to {
      box-shadow: var(--shadow-sm);
      transform: translateY(0);
      opacity: 1;
    }
  }
}
```

### State-Based Shadows

```css
/* Component states */
.state-shadows {
  .component-default {
    box-shadow: var(--shadow-sm);
    transition: box-shadow 0.2s ease;
  }

  .component-hover:hover {
    box-shadow: var(--shadow-md);
  }

  .component-active:active,
  .component-active.active {
    box-shadow: var(--shadow-inner);
  }

  .component-focus:focus {
    box-shadow: var(--shadow-sm), 0 0 0 3px rgba(59, 130, 246, 0.1);
  }

  .component-disabled {
    box-shadow: none;
    opacity: 0.5;
  }

  .component-loading {
    box-shadow: var(--shadow-xs);
    opacity: 0.7;
  }
}

/* Form validation shadows */
.validation-shadows {
  .form-field {
    box-shadow: var(--shadow-xs);
    border: 1px solid #d1d5db;
    transition: all 0.2s ease;
  }

  .form-field:focus {
    box-shadow: var(--shadow-xs), 0 0 0 3px rgba(59, 130, 246, 0.1);
    border-color: #3b82f6;
  }

  .form-field.valid {
    box-shadow: var(--shadow-xs), 0 0 0 1px #10b981;
    border-color: #10b981;
  }

  .form-field.invalid {
    box-shadow: var(--shadow-xs), 0 0 0 1px #ef4444;
    border-color: #ef4444;
  }

  .form-field.warning {
    box-shadow: var(--shadow-xs), 0 0 0 1px #f59e0b;
    border-color: #f59e0b;
  }
}
```

## 6. Special Shadow Effects

### Creative และ Artistic Effects

```css
/* Creative shadow effects */
.creative-effects {
  /* Neumorphism */
  .neumorphic {
    background: #e0e5ec;
    border-radius: 1rem;
    box-shadow: 9px 9px 16px #a3b1c6, -9px -9px 16px #ffffff;
  }

  .neumorphic-inset {
    background: #e0e5ec;
    border-radius: 1rem;
    box-shadow: inset 9px 9px 16px #a3b1c6, inset -9px -9px 16px #ffffff;
  }

  /* Glassmorphism */
  .glassmorphic {
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.2);
    box-shadow: 0 8px 32px rgba(31, 38, 135, 0.37), inset 0 1px 0 rgba(255, 255, 255, 0.4);
  }

  /* Retro/Vintage effect */
  .retro-shadow {
    background: #ff6b6b;
    color: white;
    box-shadow: 4px 4px 0 #ff5252, 8px 8px 0 #ff3d3d, 12px 12px 0 #ff2828;
  }

  /* Neon effect */
  .neon-box {
    background: #0a0a0a;
    border: 2px solid #00ffff;
    color: #00ffff;
    box-shadow: 0 0 10px #00ffff, 0 0 20px #00ffff, 0 0 40px #00ffff, inset 0 0
        10px rgba(0, 255, 255, 0.1);
  }
}

/* Paper and material effects */
.paper-effects {
  /* Folded paper */
  .folded-paper {
    background: white;
    position: relative;
    box-shadow: 0 1px 4px rgba(0, 0, 0, 0.1), 0 0 40px rgba(0, 0, 0, 0.1);
  }

  .folded-paper::before {
    content: '';
    position: absolute;
    top: 0;
    right: 0;
    width: 0;
    height: 0;
    border-left: 20px solid white;
    border-bottom: 20px solid transparent;
    box-shadow: -1px 1px 2px rgba(0, 0, 0, 0.2);
  }

  /* Torn paper */
  .torn-paper {
    background: white;
    border-radius: 0;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1), 0 0 25px rgba(0, 0, 0, 0.05);
    position: relative;
  }

  .torn-paper::before {
    content: '';
    position: absolute;
    top: -5px;
    left: 0;
    right: 0;
    height: 10px;
    background: white;
    clip-path: polygon(
      0% 50%,
      10% 0%,
      20% 80%,
      30% 20%,
      40% 90%,
      50% 30%,
      60% 70%,
      70% 10%,
      80% 60%,
      90% 40%,
      100% 80%
    );
  }

  /* Curled corner */
  .curled-corner {
    background: white;
    position: relative;
    box-shadow: 0 1px 4px rgba(0, 0, 0, 0.1);
  }

  .curled-corner::after {
    content: '';
    position: absolute;
    bottom: 0;
    right: 0;
    width: 20px;
    height: 20px;
    background: linear-gradient(
      -45deg,
      transparent 46%,
      rgba(0, 0, 0, 0.1) 50%,
      rgba(0, 0, 0, 0.05) 54%,
      transparent 54%
    );
    border-radius: 0 0 15px 0;
  }
}

/* 3D and depth effects */
.depth-effects {
  /* Floating island */
  .floating-island {
    background: white;
    border-radius: 1rem;
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1), 0 15px 25px rgba(0, 0, 0, 0.08),
      0 5px 10px rgba(0, 0, 0, 0.05);
    transform: translateZ(0);
  }

  /* Embossed button */
  .embossed-button {
    background: linear-gradient(145deg, #f0f0f0, #cacaca);
    box-shadow: 5px 5px 10px #bebebe, -5px -5px 10px #ffffff;
    border: none;
    border-radius: 0.5rem;
    padding: 1rem 2rem;
  }

  .embossed-button:active {
    box-shadow: inset 5px 5px 10px #bebebe, inset -5px -5px 10px #ffffff;
  }

  /* Layered depth */
  .layered-depth {
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1), 0 2px 4px rgba(0, 0, 0, 0.1),
      0 4px 8px rgba(0, 0, 0, 0.1), 0 8px 16px rgba(0, 0, 0, 0.1),
      0 16px 32px rgba(0, 0, 0, 0.1);
  }
}
```

## 7. Performance และ Optimization

### Performance Best Practices

```css
/* Optimized shadows */
.optimized-shadows {
  /* Use transform for animations instead of changing box-shadow */
  .efficient-hover {
    box-shadow: var(--shadow-sm);
    transform: translateZ(0); /* Force GPU acceleration */
    transition: transform 0.2s ease;
  }

  .efficient-hover:hover {
    transform: translateY(-2px) translateZ(0);
  }

  /* Pre-calculate shadow values */
  .pre-calculated {
    --base-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    --hover-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);

    box-shadow: var(--base-shadow);
    transition: box-shadow 0.2s ease;
  }

  .pre-calculated:hover {
    box-shadow: var(--hover-shadow);
  }
}

/* Reduce complexity for mobile */
@media (max-width: 768px) {
  .mobile-optimized {
    /* Simpler shadows on mobile */
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1) !important;
  }

  /* Disable complex animations on mobile */
  .complex-shadow-animation {
    animation: none !important;
    transition: none !important;
  }
}

/* Prefer reduced motion */
@media (prefers-reduced-motion: reduce) {
  .motion-sensitive {
    transition: none;
    animation: none;
  }
}

/* Use will-change judiciously */
.will-change-shadow {
  will-change: box-shadow;
  /* Remove will-change after animation */
}

.will-change-shadow:hover {
  /* Animation completed, remove will-change in JS */
}
```

### Browser Support Fallbacks

```css
/* Fallbacks for older browsers */
.shadow-fallbacks {
  /* Basic fallback */
  border: 1px solid #e5e7eb;

  /* Modern shadow */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

/* Feature detection */
@supports (backdrop-filter: blur(10px)) {
  .glassmorphic-supported {
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
    box-shadow: 0 8px 32px rgba(31, 38, 135, 0.37);
  }
}

@supports not (backdrop-filter: blur(10px)) {
  .glassmorphic-fallback {
    background: rgba(255, 255, 255, 0.9);
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }
}

/* Progressive enhancement */
.enhanced-shadow {
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* Basic shadow */
}

@supports (box-shadow: 0 0 0 1px red, 0 2px 4px blue) {
  .enhanced-shadow {
    /* Multiple shadows for supported browsers */
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1), 0 4px 6px rgba(0, 0, 0, 0.05);
  }
}
```

## 8. Dark Theme Shadow Adaptations

### Dark Mode Considerations

```css
/* Dark theme shadow adjustments */
[data-theme='light'] {
  --shadow-color: 0, 0, 0;
  --shadow-opacity: 0.1;
}

[data-theme='dark'] {
  --shadow-color: 0, 0, 0;
  --shadow-opacity: 0.3; /* เข้มขึ้นใน dark mode */
}

.adaptive-shadow {
  box-shadow: 0 4px 6px rgba(var(--shadow-color), var(--shadow-opacity));
}

/* Dark theme specific shadows */
.dark-theme-shadows {
  [data-theme='dark'] & {
    /* เงาเข้มขึ้นเพื่อให้เห็นชัดใน dark background */
    .card {
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3), 0 1px 3px rgba(0, 0, 0, 0.4);
    }

    /* ใช้เงาสีขาวบางครั้งใน dark theme */
    .highlight-card {
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3), 0 0 0 1px rgba(255, 255, 255, 0.1);
    }

    /* Inset shadows ใน dark theme */
    .inset-dark {
      box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.4);
    }
  }
}

/* Auto dark mode with prefers-color-scheme */
@media (prefers-color-scheme: dark) {
  .auto-dark-shadow {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
  }
}

@media (prefers-color-scheme: light) {
  .auto-light-shadow {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }
}
```

## 9. Practical Examples และ Use Cases

### Complete Component Examples

```css
/* Modern card component */
.modern-card {
  background: white;
  border-radius: 0.75rem;
  padding: 1.5rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1), 0 1px 2px rgba(0, 0, 0, 0.06);
  transition: all 0.3s ease;
  border: 1px solid transparent;
}

.modern-card:hover {
  box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1), 0 4px 6px rgba(0, 0, 0, 0.05);
  transform: translateY(-1px);
}

.modern-card.featured {
  box-shadow: 0 20px 25px rgba(0, 0, 0, 0.1), 0 10px 10px rgba(0, 0, 0, 0.04),
    0 0 0 1px rgba(59, 130, 246, 0.1);
  border-color: rgba(59, 130, 246, 0.2);
}

/* Navigation with shadows */
.navigation {
  background: white;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  position: sticky;
  top: 0;
  z-index: 100;
}

.nav-dropdown {
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1), 0 4px 6px rgba(0, 0, 0, 0.05);
  border: 1px solid rgba(0, 0, 0, 0.05);
  margin-top: 0.5rem;
}

/* Modal dialog */
.modal-overlay {
  background: rgba(0, 0, 0, 0.5);
  backdrop-filter: blur(4px);
}

.modal-content {
  background: white;
  border-radius: 0.75rem;
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.25), 0 10px 10px rgba(0, 0, 0, 0.04);
  max-width: 90vw;
  max-height: 90vh;
  margin: auto;
}

/* Form elements */
.form-input {
  background: white;
  border: 1px solid #d1d5db;
  border-radius: 0.375rem;
  padding: 0.75rem 1rem;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05);
  transition: all 0.2s ease;
}

.form-input:focus {
  outline: none;
  border-color: #3b82f6;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05), 0 0 0 3px rgba(59, 130, 246, 0.1);
}

/* Buttons with shadows */
.btn-primary {
  background: #3b82f6;
  color: white;
  padding: 0.75rem 1.5rem;
  border-radius: 0.375rem;
  border: none;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05), 0 1px 3px rgba(59, 130, 246, 0.2);
  transition: all 0.2s ease;
}

.btn-primary:hover {
  background: #2563eb;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1), 0 2px 4px rgba(59, 130, 246, 0.3);
  transform: translateY(-1px);
}

.btn-primary:active {
  transform: translateY(0);
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1), 0 1px 3px rgba(59, 130, 246, 0.2);
}

/* Image gallery */
.gallery-item {
  border-radius: 0.5rem;
  overflow: hidden;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  cursor: pointer;
}

.gallery-item:hover {
  box-shadow: 0 20px 25px rgba(0, 0, 0, 0.15);
  transform: translateY(-4px) scale(1.02);
}

.gallery-item img {
  width: 100%;
  height: 200px;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.gallery-item:hover img {
  transform: scale(1.1);
}
```

## สรุป Best Practices

### 1. Shadow Hierarchy

- ใช้ shadow เพื่อสร้าง visual hierarchy
- Shadow ที่เข้มและใหญ่ = ความสำคัญมากขึ้น
- รักษาความสอดคล้องใน shadow scale

### 2. Performance

- ใช้ transform แทนการเปลี่ยน box-shadow ใน animations
- Pre-calculate shadow values ด้วย CSS custom properties
- ใช้ will-change อย่างระมัดระวัง

### 3. Accessibility

- รองรับ prefers-reduced-motion
- ปรับ shadow ให้เหมาะกับ dark/light themes
- ไม่ใช้ shadow เป็นวิธีเดียวในการสื่อความหมาย

### 4. Design Consistency

- สร้าง shadow design system
- ใช้ semantic naming (elevation-1, elevation-2, etc.)
- กำหนด shadow presets สำหรับ components

### 5. Browser Support

- ใช้ fallbacks สำหรับ browsers เก่า
- Feature detection สำหรับ modern effects
- Progressive enhancement approach

การใช้งาน box-shadow อย่างมีประสิทธิภาพจะช่วยสร้าง UI ที่มีความลึก สวยงาม และใช้งานได้ดีในทุกสถานการณ์!
