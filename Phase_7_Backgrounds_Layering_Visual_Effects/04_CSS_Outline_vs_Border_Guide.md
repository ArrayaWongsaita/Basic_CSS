# CSS Outline vs Border: ความแตกต่างและการใช้งาน

## ภาพรวม Outline vs Border

**Border** และ **Outline** เป็น properties ที่ใช้สร้างเส้นรอบ elements แต่มีพื้นที่การทำงานและจุดประสงค์ที่แตกต่างกัน การเข้าใจความแตกต่างจะช่วยให้เลือกใช้ได้อย่างเหมาะสม

### ความแตกต่างพื้นฐาน

```css
/* ความแตกต่างหลัก */
.border-vs-outline-demo {
  /* Border */
  .border-example {
    border: 3px solid #3b82f6;
    padding: 20px;
    margin: 10px;
    /*
    - เป็นส่วนหนึ่งของ box model
    - มีผลต่อ layout และ dimensions
    - สามารถแยกกำหนดแต่ละด้านได้
    - ใช้ในการออกแบบ visual
    */
  }

  /* Outline */
  .outline-example {
    outline: 3px solid #ef4444;
    padding: 20px;
    margin: 10px;
    /*
    - ไม่เป็นส่วนหนึ่งของ box model
    - ไม่มีผลต่อ layout และ dimensions
    - กำหนดทั้ง 4 ด้านพร้อมกัน
    - ใช้สำหรับ accessibility และ focus states
    */
  }

  /* เปรียบเทียบโดยตรง */
  .comparison {
    /* Element เดียวกันแต่ต่างการใช้งาน */
    border: 2px solid #22c55e;
    outline: 2px solid #f59e0b;
    outline-offset: 2px;
    padding: 16px;
    /*
    Border: เส้นสีเขียวติด element
    Outline: เส้นสีส้มห่างออกมา 2px
    */
  }
}
```

## 1. Border Properties: การใช้งาน Border

### พื้นฐาน Border

```css
/* Border properties พื้นฐาน */
.border-basics {
  /* Border shorthand */
  .border-shorthand {
    border: 2px solid #3b82f6;
    /* width style color */
  }

  /* Individual border properties */
  .border-individual {
    border-width: 2px;
    border-style: solid;
    border-color: #3b82f6;
    /* แยกกำหนดแต่ละ property */
  }

  /* Per-side borders */
  .border-per-side {
    border-top: 3px solid #ef4444;
    border-right: 2px dashed #f59e0b;
    border-bottom: 1px dotted #22c55e;
    border-left: 4px double #8b5cf6;
    /* แต่ละด้านต่างกัน */
  }

  /* Individual side properties */
  .border-detailed {
    border-top-width: 3px;
    border-top-style: solid;
    border-top-color: #3b82f6;

    border-right-width: 2px;
    border-right-style: dashed;
    border-right-color: #8b5cf6;
    /* ควบคุมรายละเอียดแต่ละด้าน */
  }
}
```

### Border Styles และ Effects

```css
/* Border styles ต่างๆ */
.border-styles {
  /* Solid styles */
  .solid-borders {
    .border-solid {
      border: 3px solid #3b82f6;
      /* เส้นทึบ */
    }

    .border-thick {
      border: 8px solid #22c55e;
      /* เส้นหนา */
    }

    .border-thin {
      border: 1px solid #6b7280;
      /* เส้นบาง */
    }
  }

  /* Dashed และ Dotted */
  .dashed-dotted-borders {
    .border-dashed {
      border: 3px dashed #f59e0b;
      /* เส้นประ */
    }

    .border-dotted {
      border: 3px dotted #ef4444;
      /* เส้นจุด */
    }

    .border-mixed {
      border-top: 2px dashed #3b82f6;
      border-bottom: 2px dotted #8b5cf6;
      /* ผสมระหว่างด้าน */
    }
  }

  /* Special styles */
  .special-borders {
    .border-double {
      border: 6px double #8b5cf6;
      /* เส้นคู่ (ต้องหนาพอ) */
    }

    .border-groove {
      border: 4px groove #6b7280;
      /* เอฟเฟกต์ร่อง */
    }

    .border-ridge {
      border: 4px ridge #6b7280;
      /* เอฟเฟกต์นูน */
    }

    .border-inset {
      border: 4px inset #6b7280;
      /* เอฟเฟกต์จม */
    }

    .border-outset {
      border: 4px outset #6b7280;
      /* เอฟเฟกต์ยื่น */
    }

    .border-none {
      border: none;
      /* ไม่มี border */
    }

    .border-hidden {
      border: hidden;
      /* ซ่อน border (ใช้ใน tables) */
    }
  }

  /* Responsive borders */
  .responsive-borders {
    .mobile-border {
      border: 1px solid #e5e7eb;
      /* Mobile: เส้นบาง */
    }

    @media (min-width: 768px) {
      .mobile-border {
        border: 2px solid #3b82f6;
        /* Desktop: เส้นหนาขึ้น */
      }
    }
  }
}
```

### Border Radius และ Advanced Border

```css
/* Border radius และเทคนิคขั้นสูง */
.advanced-borders {
  /* Border radius */
  .border-radius {
    .rounded-corners {
      border: 2px solid #3b82f6;
      border-radius: 8px;
      /* มุมโค้งเท่ากันทุกมุม */
    }

    .different-corners {
      border: 2px solid #8b5cf6;
      border-radius: 12px 6px 20px 4px;
      /* top-left, top-right, bottom-right, bottom-left */
    }

    .individual-corners {
      border: 2px solid #22c55e;
      border-top-left-radius: 20px;
      border-top-right-radius: 0;
      border-bottom-right-radius: 20px;
      border-bottom-left-radius: 0;
      /* กำหนดแต่ละมุม */
    }

    .circular {
      border: 3px solid #ef4444;
      width: 100px;
      height: 100px;
      border-radius: 50%;
      /* วงกลม */
    }

    .pill-shape {
      border: 2px solid #f59e0b;
      border-radius: 50px;
      padding: 12px 24px;
      /* รูปแคปซูล */
    }
  }

  /* Border images */
  .border-images {
    .gradient-border {
      border: 4px solid transparent;
      background: linear-gradient(white, white) padding-box, linear-gradient(
            45deg,
            #3b82f6,
            #8b5cf6
          ) border-box;
      /* Gradient border effect */
    }

    .image-border {
      border: 20px solid transparent;
      border-image: url('border-pattern.png') 20 repeat;
      /* ใช้รูปเป็น border */
    }

    .svg-border {
      border: 10px solid transparent;
      border-image: url('data:image/svg+xml,...') 10 repeat;
      /* ใช้ SVG pattern */
    }
  }

  /* Animated borders */
  .animated-borders {
    .loading-border {
      border: 3px solid #e5e7eb;
      border-top: 3px solid #3b82f6;
      border-radius: 50%;
      width: 40px;
      height: 40px;
      animation: spin 1s linear infinite;
      /* Loading spinner */
    }

    @keyframes spin {
      0% {
        transform: rotate(0deg);
      }
      100% {
        transform: rotate(360deg);
      }
    }

    .rainbow-border {
      border: 3px solid;
      border-image: linear-gradient(
          45deg,
          #ef4444,
          #f59e0b,
          #22c55e,
          #3b82f6,
          #8b5cf6
        ) 1;
      animation: rainbowShift 3s ease infinite;
      /* Rainbow border */
    }

    @keyframes rainbowShift {
      0% {
        border-image-source: linear-gradient(
          45deg,
          #ef4444,
          #f59e0b,
          #22c55e,
          #3b82f6,
          #8b5cf6
        );
      }
      50% {
        border-image-source: linear-gradient(
          45deg,
          #8b5cf6,
          #ef4444,
          #f59e0b,
          #22c55e,
          #3b82f6
        );
      }
      100% {
        border-image-source: linear-gradient(
          45deg,
          #ef4444,
          #f59e0b,
          #22c55e,
          #3b82f6,
          #8b5cf6
        );
      }
    }

    .pulse-border {
      border: 2px solid #3b82f6;
      animation: pulseBorder 2s ease-in-out infinite;
      /* Pulsing border */
    }

    @keyframes pulseBorder {
      0% {
        border-color: #3b82f6;
        border-width: 2px;
      }
      50% {
        border-color: #60a5fa;
        border-width: 4px;
      }
      100% {
        border-color: #3b82f6;
        border-width: 2px;
      }
    }
  }
}
```

## 2. Outline Properties: การใช้งาน Outline

### พื้นฐาน Outline

```css
/* Outline properties พื้นฐาน */
.outline-basics {
  /* Outline shorthand */
  .outline-shorthand {
    outline: 2px solid #ef4444;
    /* width style color */
  }

  /* Individual outline properties */
  .outline-individual {
    outline-width: 2px;
    outline-style: solid;
    outline-color: #ef4444;
    /* แยกกำหนดแต่ละ property */
  }

  /* Outline offset */
  .outline-with-offset {
    outline: 2px solid #3b82f6;
    outline-offset: 4px;
    /* เว้นระยะจาก element 4px */
  }

  /* ข้อจำกัดของ outline */
  .outline-limitations {
    outline: 2px solid #22c55e;
    /* ❌ ไม่สามารถกำหนดแยกแต่ละด้าน */
    /* ❌ ไม่มี outline-radius */
    /* ❌ ไม่เป็นส่วนหนึ่งของ box model */
  }
}
```

### Outline Styles และ Effects

```css
/* Outline styles ต่างๆ */
.outline-styles {
  /* Basic styles */
  .outline-basic-styles {
    .outline-solid {
      outline: 3px solid #3b82f6;
      /* เส้นทึบ */
    }

    .outline-dashed {
      outline: 3px dashed #f59e0b;
      /* เส้นประ */
    }

    .outline-dotted {
      outline: 3px dotted #ef4444;
      /* เส้นจุด */
    }

    .outline-double {
      outline: 6px double #8b5cf6;
      /* เส้นคู่ */
    }

    .outline-groove {
      outline: 4px groove #6b7280;
      /* เอฟเฟกต์ร่อง */
    }

    .outline-ridge {
      outline: 4px ridge #6b7280;
      /* เอฟเฟกต์นูน */
    }

    .outline-none {
      outline: none;
      /* ไม่มี outline (ระวัง accessibility) */
    }
  }

  /* Outline offset variations */
  .outline-offset-variations {
    .outline-close {
      outline: 2px solid #3b82f6;
      outline-offset: 2px;
      /* ใกล้ element */
    }

    .outline-far {
      outline: 2px solid #22c55e;
      outline-offset: 8px;
      /* ไกล element */
    }

    .outline-negative {
      outline: 2px solid #ef4444;
      outline-offset: -4px;
      /* เข้าไปใน element */
    }

    .outline-zero {
      outline: 2px solid #8b5cf6;
      outline-offset: 0;
      /* ติด element (default) */
    }
  }

  /* Thickness variations */
  .outline-thickness {
    .outline-thin {
      outline: 1px solid #6b7280;
      /* เส้นบาง */
    }

    .outline-medium {
      outline: 3px solid #3b82f6;
      /* เส้นปานกลาง */
    }

    .outline-thick {
      outline: 8px solid #ef4444;
      /* เส้นหนา */
    }

    .outline-variable {
      outline: clamp(1px, 0.5vw, 4px) solid #22c55e;
      /* ความหนาปรับตาม viewport */
    }
  }
}
```

### Focus States และ Accessibility

```css
/* Focus states และ accessibility */
.outline-accessibility {
  /* Focus outline patterns */
  .focus-patterns {
    .default-focus input {
      /* ใช้ outline เริ่มต้นของ browser */
      /* ❌ อย่าเอา outline ออกโดยไม่ใส่ทดแทน */
    }

    .custom-focus input {
      outline: none; /* เอา outline เริ่มต้นออก */
      border: 2px solid #e5e7eb;
      border-radius: 6px;
      padding: 8px 12px;
      transition: all 0.2s ease;
    }

    .custom-focus input:focus {
      outline: 2px solid #3b82f6;
      outline-offset: 2px;
      border-color: #3b82f6;
      /* ใส่ outline กลับคืนเมื่อ focus */
    }

    .accessible-button {
      background-color: #3b82f6;
      color: white;
      border: none;
      padding: 12px 24px;
      border-radius: 6px;
      cursor: pointer;
      transition: all 0.2s ease;
    }

    .accessible-button:focus {
      outline: 3px solid #60a5fa;
      outline-offset: 2px;
      /* Focus state ที่ชัดเจน */
    }

    .accessible-button:focus-visible {
      outline: 3px solid #fbbf24;
      outline-offset: 2px;
      /* แสดงเฉพาะเมื่อใช้ keyboard */
    }
  }

  /* High contrast support */
  .high-contrast {
    .contrast-outline {
      outline: 2px solid currentColor;
      /* ใช้สีที่ปรับตาม system */
    }

    @media (prefers-contrast: high) {
      .contrast-outline {
        outline-width: 3px;
        outline-offset: 2px;
        /* เพิ่มความชัดเจนใน high contrast mode */
      }
    }
  }

  /* Motion preferences */
  .motion-sensitive {
    .animated-outline {
      outline: 2px solid #3b82f6;
      transition: outline-color 0.3s ease;
    }

    .animated-outline:hover {
      outline-color: #60a5fa;
    }

    @media (prefers-reduced-motion: reduce) {
      .animated-outline {
        transition: none;
        /* ปิด animation สำหรับคนที่ไม่ต้องการ motion */
      }
    }
  }

  /* Skip links */
  .skip-links {
    .skip-link {
      position: absolute;
      top: -40px;
      left: 6px;
      background: white;
      color: #1f2937;
      padding: 8px;
      text-decoration: none;
      border-radius: 4px;
      outline: 2px solid transparent;
      transition: top 0.3s ease;
    }

    .skip-link:focus {
      top: 6px;
      outline: 2px solid #3b82f6;
      outline-offset: 2px;
      /* แสดงเมื่อ focus */
    }
  }
}
```

## 3. เปรียบเทียบ Border vs Outline

### Box Model Impact

```css
/* ผลกระทบต่อ box model */
.box-model-comparison {
  /* Border มีผลต่อ layout */
  .border-impact {
    .with-border {
      width: 200px;
      height: 100px;
      padding: 20px;
      border: 10px solid #3b82f6;
      background-color: #f3f4f6;
      /*
      Total width = 200px + 20px + 20px + 10px + 10px = 260px
      Total height = 100px + 20px + 20px + 10px + 10px = 160px
      */
    }

    .with-border-box-sizing {
      width: 200px;
      height: 100px;
      padding: 20px;
      border: 10px solid #3b82f6;
      background-color: #f3f4f6;
      box-sizing: border-box;
      /*
      Total width = 200px (รวม padding และ border)
      Content width = 200px - 40px - 20px = 140px
      */
    }
  }

  /* Outline ไม่มีผลต่อ layout */
  .outline-impact {
    .with-outline {
      width: 200px;
      height: 100px;
      padding: 20px;
      outline: 10px solid #ef4444;
      background-color: #f3f4f6;
      /*
      Total width = 200px + 20px + 20px = 240px
      Outline ไม่เพิ่มขนาด element
      */
    }

    .with-outline-offset {
      width: 200px;
      height: 100px;
      padding: 20px;
      outline: 5px solid #22c55e;
      outline-offset: 10px;
      background-color: #f3f4f6;
      /*
      Element size เท่าเดิม
      Outline แสดงห่างออกไป 10px
      */
    }
  }

  /* เปรียบเทียบใน container */
  .container-comparison {
    .border-container {
      width: 300px;
      height: 200px;
      border: 2px solid #e5e7eb;
      padding: 10px;
      display: flex;
      gap: 10px;
    }

    .border-item {
      flex: 1;
      border: 3px solid #3b82f6;
      background-color: #dbeafe;
      /* Border ทำให้ items มีขนาดต่างกัน */
    }

    .outline-item {
      flex: 1;
      outline: 3px solid #ef4444;
      background-color: #fee2e2;
      /* Outline ไม่ทำให้ items มีขนาดต่างกัน */
    }
  }
}
```

### Use Cases และ Best Practices

```css
/* Use cases แต่ละประเภท */
.use-cases {
  /* Border use cases */
  .border-use-cases {
    /* 1. Visual design elements */
    .card-border {
      border: 1px solid #e5e7eb;
      border-radius: 8px;
      padding: 24px;
      background: white;
      /* Card styling */
    }

    /* 2. Separators */
    .section-separator {
      border-bottom: 1px solid #e5e7eb;
      padding-bottom: 16px;
      margin-bottom: 16px;
      /* แบ่งแยก sections */
    }

    /* 3. Input styling */
    .input-border {
      border: 2px solid #d1d5db;
      border-radius: 6px;
      padding: 8px 12px;
      transition: border-color 0.2s ease;
    }

    .input-border:focus {
      border-color: #3b82f6;
      /* เปลี่ยนสี border เมื่อ focus */
    }

    /* 4. Button styling */
    .button-border {
      background: transparent;
      border: 2px solid #3b82f6;
      color: #3b82f6;
      padding: 10px 20px;
      border-radius: 6px;
      cursor: pointer;
      /* Outline button style */
    }

    /* 5. Table styling */
    .table-border {
      border-collapse: collapse;
      width: 100%;
    }

    .table-border td,
    .table-border th {
      border: 1px solid #e5e7eb;
      padding: 8px 12px;
      text-align: left;
    }

    /* 6. Image frames */
    .image-frame {
      border: 8px solid #ffffff;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      border-radius: 4px;
      /* Photo frame effect */
    }
  }

  /* Outline use cases */
  .outline-use-cases {
    /* 1. Focus indicators */
    .focus-indicator {
      outline: none;
      border: 2px solid #e5e7eb;
      padding: 12px;
      border-radius: 6px;
    }

    .focus-indicator:focus {
      outline: 2px solid #3b82f6;
      outline-offset: 2px;
      /* Accessibility focus */
    }

    /* 2. Debugging layout */
    .debug-outline * {
      outline: 1px solid red;
      /* เห็น boundaries ของทุก element */
    }

    /* 3. Hover effects */
    .hover-outline {
      padding: 16px;
      transition: outline 0.2s ease;
    }

    .hover-outline:hover {
      outline: 2px solid #8b5cf6;
      outline-offset: 4px;
      /* Hover effect โดยไม่เปลี่ยน layout */
    }

    /* 4. Selection indicators */
    .selectable-item {
      padding: 12px;
      cursor: pointer;
      border-radius: 6px;
    }

    .selectable-item.selected {
      outline: 3px solid #22c55e;
      outline-offset: 2px;
      /* แสดงว่าถูกเลือก */
    }

    /* 5. Error states */
    .error-outline {
      outline: 2px solid #ef4444;
      outline-offset: 1px;
      /* แสดง error โดยไม่เปลี่ยน layout */
    }

    /* 6. Temporary highlights */
    .highlight-outline {
      outline: 3px solid #fbbf24;
      outline-offset: 2px;
      animation: highlightPulse 1s ease-in-out;
      /* Temporary attention */
    }

    @keyframes highlightPulse {
      0%,
      100% {
        outline-color: #fbbf24;
      }
      50% {
        outline-color: #f59e0b;
      }
    }
  }
}
```

### Performance และ Accessibility Considerations

```css
/* การพิจารณา performance และ accessibility */
.performance-accessibility {
  /* Performance best practices */
  .performance-tips {
    /* ✅ Efficient border animations */
    .efficient-border {
      border: 2px solid #3b82f6;
      transition: border-color 0.2s ease;
      /* เปลี่ยนเฉพาะสี ไม่ใช่ขนาด */
    }

    .efficient-border:hover {
      border-color: #60a5fa;
      /* ไม่ trigger layout reflow */
    }

    /* ❌ Expensive border animations */
    .expensive-border {
      border: 2px solid #3b82f6;
      transition: border-width 0.3s ease;
      /* เปลี่ยนขนาด = layout reflow */
    }

    .expensive-border:hover {
      border-width: 5px;
      /* ทำให้ layout เปลี่ยน */
    }

    /* ✅ Efficient outline animations */
    .efficient-outline {
      outline: 2px solid transparent;
      outline-offset: 2px;
      transition: outline-color 0.2s ease;
    }

    .efficient-outline:focus {
      outline-color: #3b82f6;
      /* ไม่มีผลต่อ layout */
    }
  }

  /* Accessibility best practices */
  .accessibility-tips {
    /* ✅ Proper focus management */
    .good-focus {
      border: 2px solid #e5e7eb;
      padding: 12px;
      border-radius: 6px;
    }

    .good-focus:focus {
      outline: 2px solid #3b82f6;
      outline-offset: 2px;
      border-color: #3b82f6;
      /* ทั้ง visual และ accessibility */
    }

    /* ❌ Poor focus management */
    .bad-focus {
      border: 2px solid #e5e7eb;
      outline: none; /* อันตราย! */
    }

    .bad-focus:focus {
      border-color: #3b82f6;
      /* มองเห็นได้แต่อาจไม่เพียงพอสำหรับ accessibility */
    }

    /* ✅ High contrast support */
    .contrast-friendly {
      border: 2px solid #374151;
      outline: 2px solid transparent;
      outline-offset: 2px;
    }

    .contrast-friendly:focus {
      outline-color: currentColor;
      /* ปรับตาม color scheme */
    }

    @media (prefers-contrast: high) {
      .contrast-friendly:focus {
        outline-width: 3px;
        outline-style: solid;
      }
    }

    /* ✅ Motion sensitivity */
    .motion-friendly {
      border: 2px solid #3b82f6;
      transition: border-color 0.2s ease;
    }

    @media (prefers-reduced-motion: reduce) {
      .motion-friendly {
        transition: none;
      }
    }
  }

  /* Browser compatibility */
  .compatibility {
    /* Modern approach */
    .modern-outline {
      outline: 2px solid #3b82f6;
      outline-offset: 2px;
    }

    /* Legacy support */
    .legacy-outline {
      border: 2px solid transparent;
      box-shadow: 0 0 0 2px #3b82f6;
      /* fallback สำหรับ browsers เก่า */
    }

    /* Progressive enhancement */
    .progressive-outline {
      border: 2px solid #3b82f6;
      /* fallback */
    }

    @supports (outline-offset: 2px) {
      .progressive-outline {
        border: 2px solid transparent;
        outline: 2px solid #3b82f6;
        outline-offset: 2px;
        /* ใช้ outline เมื่อ browser รองรับ */
      }
    }
  }
}
```

## 4. Practical Examples และ Patterns

### Common UI Patterns

```css
/* UI patterns ที่ใช้บ่อย */
.ui-patterns {
  /* Form elements */
  .form-patterns {
    .input-group {
      margin-bottom: 16px;
    }

    .form-input {
      width: 100%;
      border: 2px solid #d1d5db;
      border-radius: 6px;
      padding: 12px 16px;
      font-size: 16px;
      transition: all 0.2s ease;
      outline: none;
    }

    .form-input:focus {
      border-color: #3b82f6;
      outline: 2px solid #3b82f6;
      outline-offset: -2px;
      /* Focus ใน input field */
    }

    .form-input.error {
      border-color: #ef4444;
    }

    .form-input.error:focus {
      outline-color: #ef4444;
      /* Error state focus */
    }

    .form-input.success {
      border-color: #22c55e;
    }

    .form-input.success:focus {
      outline-color: #22c55e;
      /* Success state focus */
    }
  }

  /* Button patterns */
  .button-patterns {
    .btn {
      padding: 12px 24px;
      border-radius: 6px;
      font-size: 16px;
      font-weight: 500;
      cursor: pointer;
      transition: all 0.2s ease;
      outline: none;
      position: relative;
    }

    .btn-primary {
      background-color: #3b82f6;
      border: 2px solid #3b82f6;
      color: white;
    }

    .btn-primary:focus {
      outline: 2px solid #60a5fa;
      outline-offset: 2px;
      /* Primary button focus */
    }

    .btn-secondary {
      background-color: transparent;
      border: 2px solid #6b7280;
      color: #6b7280;
    }

    .btn-secondary:focus {
      outline: 2px solid #6b7280;
      outline-offset: 2px;
      border-color: #374151;
      color: #374151;
      /* Secondary button focus */
    }

    .btn-ghost {
      background-color: transparent;
      border: 2px solid transparent;
      color: #3b82f6;
    }

    .btn-ghost:focus {
      outline: 2px solid #3b82f6;
      outline-offset: 2px;
      background-color: rgba(59, 130, 246, 0.05);
      /* Ghost button focus */
    }
  }

  /* Card patterns */
  .card-patterns {
    .card {
      background: white;
      border: 1px solid #e5e7eb;
      border-radius: 12px;
      padding: 24px;
      box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
      transition: all 0.2s ease;
    }

    .card-clickable {
      cursor: pointer;
    }

    .card-clickable:hover {
      border-color: #d1d5db;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      transform: translateY(-1px);
    }

    .card-clickable:focus {
      outline: 2px solid #3b82f6;
      outline-offset: 2px;
      border-color: #3b82f6;
      /* Focusable card */
    }

    .card-selected {
      border-color: #3b82f6;
      outline: 2px solid #3b82f6;
      outline-offset: 1px;
      /* Selected state */
    }
  }

  /* Navigation patterns */
  .navigation-patterns {
    .nav-tabs {
      display: flex;
      border-bottom: 2px solid #e5e7eb;
    }

    .nav-tab {
      padding: 12px 24px;
      border: 2px solid transparent;
      border-bottom: none;
      background: none;
      cursor: pointer;
      outline: none;
      position: relative;
      top: 2px;
    }

    .nav-tab:focus {
      outline: 2px solid #3b82f6;
      outline-offset: 2px;
      /* Tab focus */
    }

    .nav-tab.active {
      border-color: #e5e7eb;
      border-bottom-color: white;
      background: white;
      /* Active tab with border */
    }

    .nav-breadcrumb {
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .breadcrumb-item {
      padding: 4px 8px;
      border-radius: 4px;
      text-decoration: none;
      color: #6b7280;
      outline: none;
    }

    .breadcrumb-item:focus {
      outline: 2px solid #3b82f6;
      outline-offset: 1px;
      /* Breadcrumb focus */
    }

    .breadcrumb-item.current {
      color: #1f2937;
      font-weight: 500;
      background-color: #f3f4f6;
      /* Current page indicator */
    }
  }
}
```

### Interactive States

```css
/* Interactive states และ animations */
.interactive-states {
  /* Hover states */
  .hover-states {
    .hover-border-change {
      border: 2px solid #e5e7eb;
      padding: 16px;
      border-radius: 8px;
      transition: border-color 0.2s ease;
    }

    .hover-border-change:hover {
      border-color: #3b82f6;
      /* เปลี่ยนสี border */
    }

    .hover-outline-appear {
      padding: 16px;
      border-radius: 8px;
      outline: 2px solid transparent;
      outline-offset: 2px;
      transition: outline-color 0.2s ease;
    }

    .hover-outline-appear:hover {
      outline-color: #8b5cf6;
      /* แสดง outline เมื่อ hover */
    }

    .hover-both {
      border: 2px solid #e5e7eb;
      padding: 16px;
      border-radius: 8px;
      outline: 2px solid transparent;
      outline-offset: 2px;
      transition: all 0.2s ease;
    }

    .hover-both:hover {
      border-color: #22c55e;
      outline-color: #22c55e;
      /* เปลี่ยนทั้งคู่ */
    }
  }

  /* Active states */
  .active-states {
    .active-border {
      border: 2px solid #d1d5db;
      padding: 12px 16px;
      background: white;
      cursor: pointer;
      outline: none;
      transition: all 0.1s ease;
    }

    .active-border:active {
      border-color: #1d4ed8;
      background-color: #eff6ff;
      transform: scale(0.98);
      /* Active press effect */
    }

    .active-outline {
      padding: 12px 16px;
      background: #f3f4f6;
      border: none;
      cursor: pointer;
      border-radius: 6px;
      outline: 2px solid transparent;
      outline-offset: 2px;
      transition: all 0.1s ease;
    }

    .active-outline:active {
      outline-color: #7c3aed;
      background-color: #ede9fe;
      transform: translateY(1px);
      /* Active state with outline */
    }
  }

  /* Loading states */
  .loading-states {
    .loading-border {
      border: 3px solid #f3f4f6;
      border-top: 3px solid #3b82f6;
      border-radius: 50%;
      width: 32px;
      height: 32px;
      animation: spin 1s linear infinite;
      /* Loading spinner */
    }

    .loading-outline {
      outline: 3px solid transparent;
      outline-offset: 2px;
      animation: pulseOutline 1.5s ease-in-out infinite;
      /* Pulsing outline */
    }

    @keyframes spin {
      0% {
        transform: rotate(0deg);
      }
      100% {
        transform: rotate(360deg);
      }
    }

    @keyframes pulseOutline {
      0% {
        outline-color: transparent;
      }
      50% {
        outline-color: #3b82f6;
      }
      100% {
        outline-color: transparent;
      }
    }
  }

  /* Error and success states */
  .validation-states {
    .input-validation {
      border: 2px solid #d1d5db;
      padding: 12px;
      border-radius: 6px;
      outline: none;
      transition: all 0.2s ease;
    }

    .input-validation.error {
      border-color: #ef4444;
      background-color: #fef2f2;
    }

    .input-validation.error:focus {
      outline: 2px solid #ef4444;
      outline-offset: 2px;
      /* Error focus state */
    }

    .input-validation.success {
      border-color: #22c55e;
      background-color: #f0fdf4;
    }

    .input-validation.success:focus {
      outline: 2px solid #22c55e;
      outline-offset: 2px;
      /* Success focus state */
    }

    .input-validation.warning {
      border-color: #f59e0b;
      background-color: #fffbeb;
    }

    .input-validation.warning:focus {
      outline: 2px solid #f59e0b;
      outline-offset: 2px;
      /* Warning focus state */
    }
  }
}
```

## สรุป: Border vs Outline Best Practices

### เมื่อไหร่ควรใช้อะไร 🎯

#### ใช้ **Border** เมื่อ:

```css
.when-to-use-border {
  /* 1. Visual design elements */
  .design-element {
    border: 1px solid #e5e7eb;
    border-radius: 8px;
    padding: 16px;
  }

  /* 2. Layout structure */
  .layout-structure {
    border-bottom: 1px solid #d1d5db;
    padding-bottom: 16px;
  }

  /* 3. Form styling */
  .form-control {
    border: 2px solid #d1d5db;
    border-radius: 6px;
    padding: 12px;
  }

  /* 4. Decorative purposes */
  .decorative {
    border: 3px solid #3b82f6;
    border-radius: 50%;
  }
}
```

#### ใช้ **Outline** เมื่อ:

```css
.when-to-use-outline {
  /* 1. Focus indicators */
  .focus-indicator:focus {
    outline: 2px solid #3b82f6;
    outline-offset: 2px;
  }

  /* 2. Debugging */
  .debug * {
    outline: 1px solid red;
  }

  /* 3. Temporary highlights */
  .highlight {
    outline: 3px solid #fbbf24;
    outline-offset: 2px;
  }

  /* 4. Non-layout affecting indicators */
  .indicator:hover {
    outline: 2px solid #8b5cf6;
    outline-offset: 4px;
  }
}
```

### Quick Reference 📋

```css
/* ความแตกต่างสำคัญ */
.key-differences {
  /* Border */
  .border-example {
    border: 2px solid #3b82f6;
    /* ✅ เป็นส่วนหนึ่งของ box model */
    /* ✅ กำหนดแยกแต่ละด้านได้ */
    /* ✅ มี border-radius */
    /* ❌ มีผลต่อ layout */
  }

  /* Outline */
  .outline-example {
    outline: 2px solid #ef4444;
    outline-offset: 2px;
    /* ✅ ไม่มีผลต่อ layout */
    /* ✅ มี outline-offset */
    /* ✅ เหมาะสำหรับ accessibility */
    /* ❌ ไม่สามารถกำหนดแยกด้าน */
    /* ❌ ไม่มี outline-radius */
  }
}

/* Best practices */
.best-practices {
  /* ✅ Good: ใช้ outline สำหรับ focus */
  .good-focus:focus {
    outline: 2px solid #3b82f6;
    outline-offset: 2px;
  }

  /* ❌ Bad: เอา outline ออกโดยไม่ทดแทน */
  .bad-focus {
    outline: none; /* อันตราย! */
  }

  /* ✅ Good: ใช้ border สำหรับ design */
  .good-design {
    border: 1px solid #e5e7eb;
    border-radius: 8px;
  }

  /* ✅ Good: รวมทั้งคู่ */
  .comprehensive {
    border: 2px solid #e5e7eb;
    outline: none;
  }

  .comprehensive:focus {
    border-color: #3b82f6;
    outline: 2px solid #3b82f6;
    outline-offset: 2px;
  }
}
```

### Performance Tips 🚀

```css
/* เพิ่มประสิทธิภาพ */
.performance-tips {
  /* ✅ Efficient: เปลี่ยนสีเท่านั้น */
  .efficient {
    border: 2px solid #d1d5db;
    transition: border-color 0.2s ease;
  }

  .efficient:hover {
    border-color: #3b82f6;
  }

  /* ❌ Expensive: เปลี่ยนขนาด */
  .expensive {
    border: 2px solid #d1d5db;
    transition: border-width 0.2s ease;
  }

  .expensive:hover {
    border-width: 4px; /* ทำให้ layout เปลี่ยน */
  }

  /* ✅ Best: ใช้ outline สำหรับ hover effects */
  .best-hover {
    outline: 2px solid transparent;
    outline-offset: 2px;
    transition: outline-color 0.2s ease;
  }

  .best-hover:hover {
    outline-color: #8b5cf6;
    /* ไม่มีผลต่อ layout */
  }
}
```

การเข้าใจความแตกต่างระหว่าง Border และ Outline จะช่วยให้เลือกใช้ได้อย่างเหมาะสม สร้าง UI ที่สวยงามและ accessible!
