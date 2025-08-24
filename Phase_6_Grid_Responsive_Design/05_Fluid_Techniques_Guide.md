# Fluid Techniques: การสร้าง Layout ที่ปรับตัวอย่างลื่นไหล

## ภาพรวม Fluid Design

**Fluid Design** คือแนวทางการออกแบบที่ทำให้ elements ปรับขนาดและตำแหน่งอย่างต่อเนื่องตามขนาดของ viewport แทนที่จะเปลี่ยนแบบแยกจุด (breakpoints) เพียงอย่างเดียว

### แนวคิดพื้นฐาน: Fixed vs Fluid vs Responsive

```css
/* เปรียบเทียบแนวทาง Design ต่างๆ */
.design-approaches {
  /* ❌ Fixed Design - ไม่ปรับตัว */
  .fixed-design {
    width: 1200px;
    font-size: 16px;
    margin: 20px;
    /* ปัญหา: ไม่ทำงานดีใน mobile */
  }

  /* ✅ Fluid Design - ปรับตัวต่อเนื่อง */
  .fluid-design {
    width: 80%; /* ปรับตาม parent */
    font-size: clamp(1rem, 2.5vw, 1.5rem); /* ปรับตาม viewport */
    margin: clamp(1rem, 5vw, 3rem); /* ปรับระยะห่าง */
    /* ข้อดี: ปรับตัวอย่างลื่นไหล */
  }

  /* ✅ Responsive Design - ปรับตามจุดหัก */
  .responsive-design {
    width: 100%;
    font-size: 16px;
    margin: 20px;

    /* เปลี่ยนที่จุดหัก */
    @media (max-width: 768px) {
      font-size: 14px;
      margin: 10px;
    }
  }

  /* 🏆 Hybrid Approach - รวมทั้งสองแนวทาง */
  .hybrid-design {
    width: clamp(320px, 90%, 1200px); /* Fluid with limits */
    font-size: clamp(0.875rem, 2vw, 1.125rem);
    margin: clamp(1rem, 4vw, 2rem);

    /* Fine-tuning ที่จุดหัก */
    @media (max-width: 768px) {
      padding: clamp(0.5rem, 3vw, 1rem);
    }
  }
}
```

## 1. max-width: การจำกัดความกว้างอย่างยืดหยุ่น

### พื้นฐาน max-width

```css
/* เข้าใจการทำงานของ max-width */
.max-width-basics {
  /* max-width vs width */
  .width-comparison {
    /* width: ความกว้างคงที่ */
    .fixed-width {
      width: 800px;
      /* ปัญหา: เกินหน้าจอ mobile (320px-768px) */
      /* สร้าง horizontal scroll */
    }

    /* max-width: ความกว้างสูงสุด */
    .flexible-width {
      max-width: 800px;
      width: 100%;
      /* หรือเขียนสั้นๆ ว่า */
      /* max-width: 800px; */

      /* ผลลัพธ์: */
      /* - หน้าจอใหญ่: 800px */
      /* - หน้าจอเล็ก: 100% ของหน้าจอ */
      /* - ไม่มี horizontal scroll */
    }
  }

  /* Container patterns */
  .container {
    max-width: 1200px;
    margin: 0 auto; /* Center alignment */
    padding: 0 1rem; /* Side padding */
    width: 100%; /* Full width until max-width */
  }

  /* Different container sizes */
  .container-sm {
    max-width: 640px;
    margin: 0 auto;
    padding: 0 1rem;
  }

  .container-md {
    max-width: 768px;
    margin: 0 auto;
    padding: 0 1rem;
  }

  .container-lg {
    max-width: 1024px;
    margin: 0 auto;
    padding: 0 1rem;
  }

  .container-xl {
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 1rem;
  }

  /* Responsive containers */
  .responsive-container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 clamp(1rem, 5vw, 3rem);

    /* ปรับ max-width ตาม breakpoint */
    @media (max-width: 1280px) {
      max-width: 95%;
    }

    @media (max-width: 768px) {
      max-width: 100%;
      padding: 0 1rem;
    }
  }
}
```

### Advanced max-width Patterns

```css
/* เทคนิค max-width ขั้นสูง */
.advanced-max-width {
  /* Nested containers */
  .outer-container {
    max-width: 1400px;
    margin: 0 auto;
    padding: 0 2rem;
  }

  .inner-container {
    max-width: 800px;
    margin: 0 auto;
    /* สร้าง content area ที่แคบกว่า */
  }

  /* Multiple max-width zones */
  .content-area {
    max-width: 65ch; /* Optimal reading width */
    margin: 0 auto;
    line-height: 1.6;
  }

  .media-area {
    max-width: 100%;
    /* รูปภาพใช้พื้นที่เต็ม container */
  }

  .sidebar-area {
    max-width: 300px;
    /* Sidebar จำกัดความกว้าง */
  }

  /* Card containers */
  .card-container {
    max-width: 400px;
    margin: 0 auto;
    padding: 1.5rem;
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  /* Form containers */
  .form-container {
    max-width: 500px;
    margin: 0 auto;
    padding: 2rem;
  }

  .form-container input,
  .form-container textarea,
  .form-container select {
    width: 100%;
    max-width: 100%;
    /* Prevent form elements from overflowing */
  }

  /* Grid with max-width items */
  .grid-max-width {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    max-width: 1200px;
    margin: 0 auto;
    padding: 2rem;
  }

  .grid-item {
    max-width: 400px; /* จำกัดขนาดแต่ละ item */
    margin: 0 auto;
    background: white;
    padding: 1.5rem;
    border-radius: 0.5rem;
  }
}
```

## 2. clamp(): ฟังก์ชันสำหรับค่าที่ปรับตัวในช่วงที่กำหนด

### พื้นฐาน clamp()

```css
/* เข้าใจ clamp(min, preferred, max) */
.clamp-basics {
  /* Syntax: clamp(minimum, preferred, maximum) */

  /* Font size responsive */
  .clamp-font {
    font-size: clamp(1rem, 2.5vw, 2rem);
    /*
    - minimum: 1rem (16px)
    - preferred: 2.5vw (2.5% ของ viewport width)
    - maximum: 2rem (32px)

    ผลลัพธ์:
    - Mobile (320px): 16px (ไม่ต่ำกว่า 1rem)
    - Tablet (768px): 19.2px (2.5% ของ 768px)
    - Desktop (1200px): 30px (2.5% ของ 1200px)
    - Large screen: 32px (ไม่เกิน 2rem)
    */
  }

  /* การคำนวณ vw values */
  .vw-calculation {
    /*
    vw = (pixel / viewport-width) * 100

    ตัวอย่าง: ต้องการ 24px ที่ 1000px viewport
    vw = (24 / 1000) * 100 = 2.4vw
    */

    font-size: clamp(1rem, 2.4vw, 1.5rem);
    /* จะได้ 24px ที่ viewport 1000px */
  }

  /* Width responsive */
  .clamp-width {
    width: clamp(300px, 50vw, 800px);
    /*
    - minimum: 300px
    - preferred: 50% ของ viewport width
    - maximum: 800px
    */
  }

  /* Padding responsive */
  .clamp-padding {
    padding: clamp(1rem, 5vw, 4rem);
    /*
    - Mobile: 1rem (16px)
    - ปรับตาม viewport: 5% ของความกว้าง
    - Desktop: สูงสุด 4rem (64px)
    */
  }

  /* Margin responsive */
  .clamp-margin {
    margin: clamp(0.5rem, 3vw, 2rem) clamp(1rem, 5vw, 3rem);
    /*
    - vertical: 0.5rem ถึง 2rem
    - horizontal: 1rem ถึง 3rem
    */
  }
}
```

### Typography with clamp()

```css
/* Typography ด้วย clamp() */
.clamp-typography {
  /* Heading scales */
  .heading-scale {
    /* H1 - Hero heading */
    .h1-hero {
      font-size: clamp(2rem, 6vw, 4rem);
      line-height: 1.1;
      margin-bottom: clamp(1rem, 3vw, 2rem);
      /*
      Mobile: 32px
      Tablet: ~46px (768px * 0.06)
      Desktop: 64px (maximum)
      */
    }

    /* H1 - Page title */
    .h1-title {
      font-size: clamp(1.75rem, 4vw, 2.5rem);
      line-height: 1.2;
      margin-bottom: clamp(0.75rem, 2vw, 1.5rem);
    }

    /* H2 - Section heading */
    .h2-section {
      font-size: clamp(1.5rem, 3vw, 2rem);
      line-height: 1.3;
      margin-bottom: clamp(0.5rem, 1.5vw, 1rem);
    }

    /* H3 - Subsection */
    .h3-subsection {
      font-size: clamp(1.25rem, 2.5vw, 1.5rem);
      line-height: 1.4;
      margin-bottom: clamp(0.5rem, 1vw, 0.75rem);
    }

    /* Body text */
    .body-text {
      font-size: clamp(0.875rem, 2vw, 1.125rem);
      line-height: clamp(1.4, 0.5vw + 1.2, 1.6);
      margin-bottom: clamp(0.75rem, 2vw, 1.25rem);
    }

    /* Small text */
    .small-text {
      font-size: clamp(0.75rem, 1.5vw, 0.875rem);
      line-height: 1.5;
    }
  }

  /* Advanced typography system */
  .typography-system {
    /* Base font size */
    font-size: clamp(0.875rem, 1.5vw + 0.5rem, 1.125rem);

    /* Scale relationships */
    .text-xs {
      font-size: clamp(0.75rem, 1vw + 0.5rem, 0.875rem);
    }
    .text-sm {
      font-size: clamp(0.875rem, 1.2vw + 0.5rem, 1rem);
    }
    .text-base {
      font-size: clamp(1rem, 1.5vw + 0.5rem, 1.125rem);
    }
    .text-lg {
      font-size: clamp(1.125rem, 2vw + 0.5rem, 1.25rem);
    }
    .text-xl {
      font-size: clamp(1.25rem, 2.5vw + 0.5rem, 1.5rem);
    }
    .text-2xl {
      font-size: clamp(1.5rem, 3vw + 0.5rem, 2rem);
    }
    .text-3xl {
      font-size: clamp(1.875rem, 4vw + 0.5rem, 2.5rem);
    }
    .text-4xl {
      font-size: clamp(2.25rem, 5vw + 0.5rem, 3rem);
    }
  }

  /* Line height scaling */
  .line-height-scale {
    /* Responsive line-height */
    .responsive-line-height {
      line-height: clamp(1.4, 0.4vw + 1.2, 1.6);
      /* หัวข้อ: line-height แน่นหน่อย */
      /* เนื้อหา: line-height หลวมหน่อย */
    }

    .heading-line-height {
      line-height: clamp(1.1, 0.2vw + 1, 1.3);
    }

    .body-line-height {
      line-height: clamp(1.5, 0.3vw + 1.3, 1.7);
    }
  }
}
```

### Layout Spacing with clamp()

```css
/* Layout spacing ด้วย clamp() */
.clamp-spacing {
  /* Container spacing */
  .responsive-container {
    max-width: 1200px;
    margin: 0 auto;
    padding: clamp(1rem, 5vw, 3rem);
    /*
    Mobile: 16px padding
    Desktop: สูงสุด 48px padding
    ปรับตาม viewport
    */
  }

  /* Section spacing */
  .section-spacing {
    margin-bottom: clamp(3rem, 8vw, 8rem);
    padding: clamp(2rem, 6vw, 6rem) clamp(1rem, 4vw, 2rem);
    /*
    Vertical: 32px-128px
    Horizontal: 16px-32px
    */
  }

  /* Grid gaps */
  .responsive-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: clamp(1rem, 4vw, 3rem);
    /*
    Mobile: 16px gap
    Desktop: สูงสุด 48px gap
    */
  }

  /* Card spacing */
  .card-responsive {
    padding: clamp(1rem, 4vw, 2.5rem);
    margin-bottom: clamp(1rem, 3vw, 2rem);
    border-radius: clamp(0.5rem, 1vw, 1rem);
    /*
    ทุกอย่างปรับตาม viewport
    */
  }

  /* Navigation spacing */
  .nav-responsive {
    padding: clamp(0.75rem, 2vw, 1.5rem) clamp(1rem, 5vw, 3rem);
    gap: clamp(1rem, 3vw, 2rem);
  }

  /* Button spacing */
  .button-responsive {
    padding: clamp(0.5rem, 1.5vw, 1rem) clamp(1rem, 3vw, 2rem);
    font-size: clamp(0.875rem, 2vw, 1.125rem);
    border-radius: clamp(0.25rem, 0.5vw, 0.5rem);
  }

  /* Form spacing */
  .form-responsive {
    gap: clamp(1rem, 2vw, 1.5rem);
  }

  .form-responsive input,
  .form-responsive textarea {
    padding: clamp(0.75rem, 2vw, 1.25rem);
    font-size: clamp(0.875rem, 2vw, 1rem);
    border-radius: clamp(0.25rem, 0.5vw, 0.5rem);
  }
}
```

## 3. aspect-ratio: การควบคุมสัดส่วนแบบ Modern

### พื้นฐาน aspect-ratio

```css
/* เข้าใจ aspect-ratio property */
.aspect-ratio-basics {
  /* Syntax: aspect-ratio: width / height */

  /* Common aspect ratios */
  .ratio-examples {
    /* Square */
    .square {
      aspect-ratio: 1 / 1;
      /* หรือ aspect-ratio: 1; */
      background: #e5e7eb;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    /* Video/Cinema */
    .video-16-9 {
      aspect-ratio: 16 / 9; /* 1.777... */
      background: #1f2937;
      color: white;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    /* Golden ratio */
    .golden-ratio {
      aspect-ratio: 1.618 / 1;
      background: #f59e0b;
      color: white;
    }

    /* Photo formats */
    .photo-4-3 {
      aspect-ratio: 4 / 3; /* 1.333... */
      background: #10b981;
    }

    .photo-3-2 {
      aspect-ratio: 3 / 2; /* 1.5 */
      background: #3b82f6;
    }

    /* Mobile friendly */
    .mobile-9-16 {
      aspect-ratio: 9 / 16; /* Portrait */
      background: #8b5cf6;
      color: white;
    }

    /* Landscape formats */
    .landscape-21-9 {
      aspect-ratio: 21 / 9; /* Ultra-wide */
      background: #ef4444;
      color: white;
    }
  }

  /* การทำงานของ aspect-ratio */
  .aspect-ratio-behavior {
    /* ถ้ากำหนด width */
    .fixed-width {
      width: 300px;
      aspect-ratio: 16 / 9;
      /* height จะถูกคำนวณเป็น 168.75px */
    }

    /* ถ้ากำหนด height */
    .fixed-height {
      height: 200px;
      aspect-ratio: 16 / 9;
      /* width จะถูกคำนวณเป็น 355.56px */
    }

    /* ถ้าไม่กำหนดขนาด */
    .auto-size {
      aspect-ratio: 16 / 9;
      /* ขึ้นอยู่กับ content และ parent */
    }

    /* กับ max-width */
    .responsive-aspect {
      max-width: 100%;
      aspect-ratio: 16 / 9;
      /* ปรับตาม container แต่รักษาสัดส่วน */
    }
  }
}
```

### Images with aspect-ratio

```css
/* รูปภาพกับ aspect-ratio */
.images-aspect-ratio {
  /* Container กำหนดสัดส่วน */
  .image-container {
    aspect-ratio: 16 / 9;
    overflow: hidden;
    border-radius: 0.5rem;
    background: #f3f4f6;
  }

  .image-container img {
    width: 100%;
    height: 100%;
    object-fit: cover; /* ครอบคลุมพื้นที่ */
    object-position: center;
  }

  /* Gallery ด้วย aspect-ratio */
  .gallery-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1rem;
    padding: 1rem;
  }

  .gallery-item {
    aspect-ratio: 1; /* Square thumbnails */
    overflow: hidden;
    border-radius: 0.5rem;
    cursor: pointer;
    transition: transform 0.2s ease;
  }

  .gallery-item:hover {
    transform: scale(1.05);
  }

  .gallery-item img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  /* Different ratios for different content */
  .content-gallery {
    display: grid;
    gap: 1.5rem;
    padding: 2rem;
  }

  /* Portrait images */
  .portrait-item {
    aspect-ratio: 3 / 4;
    background: #f8fafc;
    overflow: hidden;
    border-radius: 0.5rem;
  }

  /* Landscape images */
  .landscape-item {
    aspect-ratio: 4 / 3;
    background: #f8fafc;
    overflow: hidden;
    border-radius: 0.5rem;
  }

  /* Banner images */
  .banner-item {
    aspect-ratio: 21 / 9;
    background: #f8fafc;
    overflow: hidden;
    border-radius: 0.5rem;
  }

  /* Responsive aspect ratios */
  .responsive-aspect-image {
    aspect-ratio: 16 / 9;
    max-width: 100%;
    overflow: hidden;
    border-radius: 0.5rem;
  }

  @media (max-width: 768px) {
    .responsive-aspect-image {
      aspect-ratio: 4 / 3; /* เปลี่ยนสัดส่วนใน mobile */
    }
  }

  @media (max-width: 480px) {
    .responsive-aspect-image {
      aspect-ratio: 1; /* Square ใน mobile เล็ก */
    }
  }
}
```

### Cards and Components with aspect-ratio

```css
/* Cards และ components ด้วย aspect-ratio */
.components-aspect-ratio {
  /* Card grid */
  .card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    padding: 2rem;
  }

  /* Basic card */
  .card {
    background: white;
    border-radius: 0.5rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    transition: transform 0.2s ease;
  }

  .card:hover {
    transform: translateY(-4px);
  }

  /* Card image */
  .card-image {
    aspect-ratio: 16 / 9;
    overflow: hidden;
    background: #f3f4f6;
  }

  .card-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s ease;
  }

  .card:hover .card-image img {
    transform: scale(1.1);
  }

  /* Card content */
  .card-content {
    padding: 1.5rem;
  }

  /* Product cards */
  .product-card .card-image {
    aspect-ratio: 1; /* Square for products */
    background: white;
    padding: 1rem;
  }

  .product-card .card-image img {
    object-fit: contain; /* Show full product */
  }

  /* Video cards */
  .video-card .card-image {
    aspect-ratio: 16 / 9;
    position: relative;
    background: #000;
  }

  .video-card .play-button {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 60px;
    height: 60px;
    background: rgba(255, 255, 255, 0.9);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.5rem;
    color: #1f2937;
    cursor: pointer;
  }

  /* Profile cards */
  .profile-card {
    text-align: center;
    background: white;
    padding: 2rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .profile-avatar {
    aspect-ratio: 1;
    width: 120px;
    margin: 0 auto 1rem;
    overflow: hidden;
    border-radius: 50%;
    background: #f3f4f6;
  }

  .profile-avatar img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  /* Testimonial cards */
  .testimonial-card {
    background: white;
    padding: 2rem;
    border-radius: 0.5rem;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    display: flex;
    gap: 1rem;
  }

  .testimonial-avatar {
    flex: 0 0 60px;
    aspect-ratio: 1;
    overflow: hidden;
    border-radius: 50%;
    background: #f3f4f6;
  }

  .testimonial-avatar img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .testimonial-content {
    flex: 1;
  }
}
```

### Fallbacks สำหรับ aspect-ratio

```css
/* Fallbacks สำหรับ browsers เก่า */
.aspect-ratio-fallbacks {
  /* Modern approach */
  .modern-aspect {
    aspect-ratio: 16 / 9;
    background: #f3f4f6;
    border-radius: 0.5rem;
  }

  /* Fallback ด้วย padding-bottom trick */
  @supports not (aspect-ratio: 1) {
    .fallback-aspect {
      position: relative;
      overflow: hidden;
      border-radius: 0.5rem;
    }

    /* 16:9 = (9/16) * 100% = 56.25% */
    .fallback-aspect.ratio-16-9::before {
      content: '';
      display: block;
      padding-bottom: 56.25%;
    }

    /* 4:3 = (3/4) * 100% = 75% */
    .fallback-aspect.ratio-4-3::before {
      content: '';
      display: block;
      padding-bottom: 75%;
    }

    /* 1:1 = 100% */
    .fallback-aspect.ratio-1-1::before {
      content: '';
      display: block;
      padding-bottom: 100%;
    }

    /* Content positioning */
    .fallback-aspect > * {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
    }

    .fallback-aspect img {
      object-fit: cover;
    }
  }

  /* Universal approach (modern + fallback) */
  .universal-aspect {
    /* Modern browsers */
    aspect-ratio: 16 / 9;

    /* Fallback */
    position: relative;
    overflow: hidden;
  }

  @supports not (aspect-ratio: 1) {
    .universal-aspect::before {
      content: '';
      display: block;
      padding-bottom: 56.25%; /* 16:9 */
    }

    .universal-aspect > * {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
    }
  }

  /* Mixin approach (Sass) */
  /*
  @mixin aspect-ratio($width, $height) {
    aspect-ratio: #{$width} / #{$height};

    @supports not (aspect-ratio: 1) {
      position: relative;
      overflow: hidden;

      &::before {
        content: '';
        display: block;
        padding-bottom: percentage($height / $width);
      }

      > * {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
      }
    }
  }

  .video-container {
    @include aspect-ratio(16, 9);
  }
  */
}
```

## 4. การรวม Fluid Techniques เข้าด้วยกัน

### Complete Fluid Layout System

```css
/* ระบบ layout แบบ fluid ครบครัน */
.fluid-layout-system {
  /* Root variables */
  :root {
    /* Fluid spacing scale */
    --space-xs: clamp(0.25rem, 1vw, 0.5rem);
    --space-sm: clamp(0.5rem, 2vw, 1rem);
    --space-md: clamp(1rem, 3vw, 2rem);
    --space-lg: clamp(2rem, 5vw, 4rem);
    --space-xl: clamp(3rem, 8vw, 6rem);
    --space-2xl: clamp(4rem, 10vw, 8rem);

    /* Fluid font sizes */
    --text-xs: clamp(0.75rem, 1vw + 0.5rem, 0.875rem);
    --text-sm: clamp(0.875rem, 1.2vw + 0.5rem, 1rem);
    --text-base: clamp(1rem, 1.5vw + 0.5rem, 1.125rem);
    --text-lg: clamp(1.125rem, 2vw + 0.5rem, 1.25rem);
    --text-xl: clamp(1.25rem, 2.5vw + 0.5rem, 1.5rem);
    --text-2xl: clamp(1.5rem, 3vw + 0.5rem, 2rem);
    --text-3xl: clamp(1.875rem, 4vw + 0.5rem, 2.5rem);
    --text-4xl: clamp(2.25rem, 5vw + 0.5rem, 3rem);

    /* Container sizes */
    --container-sm: clamp(320px, 90%, 640px);
    --container-md: clamp(320px, 90%, 768px);
    --container-lg: clamp(320px, 90%, 1024px);
    --container-xl: clamp(320px, 90%, 1280px);
    --container-2xl: clamp(320px, 90%, 1536px);
  }

  /* Base layout */
  .container {
    max-width: var(--container-xl);
    margin: 0 auto;
    padding: 0 var(--space-md);
  }

  /* Section layout */
  .section {
    padding: var(--space-xl) 0;
    margin-bottom: var(--space-lg);
  }

  /* Grid system */
  .grid-fluid {
    display: grid;
    gap: var(--space-md);
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  }

  /* Card system */
  .card-fluid {
    background: white;
    padding: var(--space-lg);
    border-radius: clamp(0.5rem, 1vw, 1rem);
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  .card-image {
    aspect-ratio: 16 / 9;
    max-width: 100%;
    margin-bottom: var(--space-md);
    overflow: hidden;
    border-radius: clamp(0.25rem, 0.5vw, 0.5rem);
  }

  .card-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  /* Typography system */
  .heading-fluid {
    font-size: var(--text-3xl);
    line-height: clamp(1.1, 0.2vw + 1, 1.3);
    margin-bottom: var(--space-md);
  }

  .subheading-fluid {
    font-size: var(--text-xl);
    line-height: clamp(1.2, 0.2vw + 1.1, 1.4);
    margin-bottom: var(--space-sm);
  }

  .body-fluid {
    font-size: var(--text-base);
    line-height: clamp(1.5, 0.3vw + 1.3, 1.7);
    margin-bottom: var(--space-md);
  }

  /* Navigation */
  .nav-fluid {
    padding: var(--space-md) var(--space-lg);
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: var(--space-md);
  }

  .nav-links {
    display: flex;
    gap: var(--space-md);
    font-size: var(--text-sm);
  }

  /* Buttons */
  .button-fluid {
    padding: var(--space-sm) var(--space-md);
    font-size: var(--text-base);
    border-radius: clamp(0.25rem, 0.5vw, 0.5rem);
    border: none;
    background: #3b82f6;
    color: white;
    cursor: pointer;
    transition: all 0.2s ease;
  }

  .button-fluid:hover {
    background: #2563eb;
    transform: translateY(-1px);
  }

  /* Forms */
  .form-fluid {
    max-width: var(--container-md);
    margin: 0 auto;
    display: grid;
    gap: var(--space-md);
  }

  .form-fluid input,
  .form-fluid textarea,
  .form-fluid select {
    width: 100%;
    padding: var(--space-sm);
    font-size: var(--text-base);
    border: 1px solid #d1d5db;
    border-radius: clamp(0.25rem, 0.5vw, 0.5rem);
  }

  /* Footer */
  .footer-fluid {
    background: #1f2937;
    color: white;
    padding: var(--space-xl) var(--space-lg);
    margin-top: var(--space-2xl);
  }

  .footer-content {
    max-width: var(--container-xl);
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: var(--space-lg);
  }
}
```

### Advanced Fluid Patterns

```css
/* เทคนิค fluid ขั้นสูง */
.advanced-fluid-patterns {
  /* Responsive columns */
  .responsive-columns {
    columns: clamp(1, 20vw - 5rem, 4);
    column-gap: var(--space-lg);
    column-rule: 1px solid #e5e7eb;
  }

  /* Fluid masonry */
  .fluid-masonry {
    display: grid;
    grid-template-columns: repeat(
      auto-fill,
      minmax(clamp(250px, 30vw, 350px), 1fr)
    );
    grid-auto-rows: 20px;
    gap: clamp(1rem, 2vw, 2rem);
  }

  .masonry-item {
    background: white;
    border-radius: clamp(0.5rem, 1vw, 1rem);
    padding: var(--space-md);
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .masonry-item.small {
    grid-row: span 15;
  }
  .masonry-item.medium {
    grid-row: span 25;
  }
  .masonry-item.large {
    grid-row: span 35;
  }

  /* Fluid sidebar layout */
  .sidebar-layout {
    display: grid;
    grid-template-columns: clamp(250px, 25vw, 350px) 1fr;
    gap: var(--space-lg);
    max-width: var(--container-2xl);
    margin: 0 auto;
    padding: var(--space-lg);
  }

  @media (max-width: 768px) {
    .sidebar-layout {
      grid-template-columns: 1fr;
    }
  }

  /* Fluid hero section */
  .hero-fluid {
    height: clamp(60vh, 100vh, 100vh);
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    color: white;
    padding: var(--space-lg);
  }

  .hero-content {
    max-width: clamp(300px, 80vw, 800px);
  }

  .hero-title {
    font-size: clamp(2rem, 8vw, 6rem);
    font-weight: bold;
    line-height: 1.1;
    margin-bottom: var(--space-md);
  }

  .hero-subtitle {
    font-size: clamp(1rem, 3vw, 1.5rem);
    opacity: 0.9;
    margin-bottom: var(--space-lg);
  }

  /* Fluid pricing table */
  .pricing-table {
    display: grid;
    grid-template-columns: repeat(
      auto-fit,
      minmax(clamp(250px, 30vw, 350px), 1fr)
    );
    gap: var(--space-lg);
    max-width: var(--container-xl);
    margin: 0 auto;
    padding: var(--space-lg);
  }

  .pricing-card {
    background: white;
    border-radius: clamp(0.5rem, 1vw, 1.5rem);
    padding: var(--space-xl);
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
    text-align: center;
    position: relative;
    overflow: hidden;
  }

  .pricing-card.featured {
    transform: scale(1.05);
    border: 2px solid #3b82f6;
  }

  .pricing-amount {
    font-size: clamp(2rem, 6vw, 4rem);
    font-weight: bold;
    color: #3b82f6;
    margin: var(--space-md) 0;
  }

  /* Fluid testimonials */
  .testimonials-grid {
    display: grid;
    grid-template-columns: repeat(
      auto-fit,
      minmax(clamp(300px, 40vw, 400px), 1fr)
    );
    gap: var(--space-lg);
    padding: var(--space-xl);
  }

  .testimonial {
    background: white;
    padding: var(--space-lg);
    border-radius: clamp(0.5rem, 1vw, 1rem);
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    position: relative;
  }

  .testimonial::before {
    content: '"';
    font-size: clamp(3rem, 8vw, 6rem);
    color: #3b82f6;
    position: absolute;
    top: -10px;
    left: 20px;
    opacity: 0.3;
  }

  .testimonial-text {
    font-size: var(--text-base);
    line-height: 1.6;
    margin-bottom: var(--space-md);
    font-style: italic;
  }

  .testimonial-author {
    display: flex;
    align-items: center;
    gap: var(--space-sm);
  }

  .author-avatar {
    width: clamp(40px, 8vw, 60px);
    height: clamp(40px, 8vw, 60px);
    aspect-ratio: 1;
    border-radius: 50%;
    overflow: hidden;
    background: #f3f4f6;
  }

  .author-avatar img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
```

## 5. Performance และ Best Practices

### Performance Optimization

```css
/* การเพิ่มประสิทธิภาพ */
.performance-optimization {
  /* CSS Custom Properties สำหรับ fluid values */
  :root {
    /* Pre-calculate fluid values */
    --fluid-space-sm: clamp(0.5rem, 2vw, 1rem);
    --fluid-space-md: clamp(1rem, 4vw, 2rem);
    --fluid-space-lg: clamp(2rem, 6vw, 4rem);

    /* Use these instead of recalculating */
  }

  /* Efficient clamp calculations */
  .efficient-clamp {
    /* ✅ Good: Simple calculations */
    font-size: clamp(1rem, 2vw, 1.5rem);

    /* ❌ Avoid: Complex calculations */
    /* font-size: clamp(1rem, calc(2vw + 0.5rem - 2px), 1.5rem); */
  }

  /* Use transform instead of changing layout properties */
  .performance-animations {
    /* ✅ Good: GPU accelerated */
    .smooth-scale {
      transform: scale(1);
      transition: transform 0.3s ease;
    }

    .smooth-scale:hover {
      transform: scale(1.05);
    }

    /* ❌ Avoid: Layout-triggering properties */
    .avoid-layout-changes {
      width: 300px;
      transition: width 0.3s ease; /* Triggers layout */
    }
  }

  /* Container queries preparation */
  .container-query-ready {
    /* Modern approach for container-based scaling */
    container-type: inline-size;
    container-name: card;
  }

  @container card (min-width: 300px) {
    .container-content {
      font-size: 1.125rem;
      padding: 1.5rem;
    }
  }

  @container card (min-width: 500px) {
    .container-content {
      font-size: 1.25rem;
      padding: 2rem;
    }
  }

  /* Reduced motion preferences */
  @media (prefers-reduced-motion: reduce) {
    * {
      animation-duration: 0.01ms !important;
      animation-iteration-count: 1 !important;
      transition-duration: 0.01ms !important;
    }
  }

  /* Print styles */
  @media print {
    .print-optimized {
      /* Use fixed units for print */
      font-size: 12pt;
      line-height: 1.4;
      max-width: none;
      aspect-ratio: auto;
    }
  }
}
```

### Debugging Fluid Layouts

```css
/* Tools สำหรับ debug fluid layouts */
.debugging-tools {
  /* Visual debugging */
  .debug-mode * {
    outline: 1px solid red;
    background: rgba(255, 0, 0, 0.1);
  }

  .debug-mode .container {
    outline: 2px solid blue;
    background: rgba(0, 0, 255, 0.1);
  }

  .debug-mode .grid-item {
    outline: 1px solid green;
    background: rgba(0, 255, 0, 0.1);
  }

  /* Viewport size indicator */
  .viewport-indicator {
    position: fixed;
    top: 10px;
    right: 10px;
    background: rgba(0, 0, 0, 0.8);
    color: white;
    padding: 0.5rem;
    border-radius: 0.25rem;
    font-size: 0.75rem;
    z-index: 9999;
    font-family: monospace;
  }

  .viewport-indicator::before {
    content: 'W: ' attr(data-width) 'px H: ' attr(data-height) 'px';
  }

  /* Fluid value display */
  .fluid-display {
    position: relative;
  }

  .fluid-display::after {
    content: 'Font: ' attr(data-font-size);
    position: absolute;
    top: -20px;
    left: 0;
    font-size: 10px;
    background: yellow;
    padding: 2px 4px;
    pointer-events: none;
  }

  /* Breakpoint indicators */
  .breakpoint-indicator {
    display: none;
    position: fixed;
    bottom: 10px;
    left: 10px;
    background: rgba(0, 0, 0, 0.8);
    color: white;
    padding: 0.5rem;
    border-radius: 0.25rem;
    font-size: 0.75rem;
  }

  @media (max-width: 640px) {
    .breakpoint-indicator.sm {
      display: block;
    }
    .breakpoint-indicator.sm::before {
      content: 'SM: ≤640px';
    }
  }

  @media (min-width: 641px) and (max-width: 768px) {
    .breakpoint-indicator.md {
      display: block;
    }
    .breakpoint-indicator.md::before {
      content: 'MD: 641px-768px';
    }
  }

  @media (min-width: 769px) and (max-width: 1024px) {
    .breakpoint-indicator.lg {
      display: block;
    }
    .breakpoint-indicator.lg::before {
      content: 'LG: 769px-1024px';
    }
  }

  @media (min-width: 1025px) {
    .breakpoint-indicator.xl {
      display: block;
    }
    .breakpoint-indicator.xl::before {
      content: 'XL: ≥1025px';
    }
  }
}

/* JavaScript helper for debugging */
/*
// Viewport size indicator
function updateViewportIndicator() {
  const indicator = document.querySelector('.viewport-indicator');
  if (indicator) {
    indicator.setAttribute('data-width', window.innerWidth);
    indicator.setAttribute('data-height', window.innerHeight);
  }
}

window.addEventListener('resize', updateViewportIndicator);
updateViewportIndicator();

// Fluid value display
function updateFluidDisplay() {
  const elements = document.querySelectorAll('.fluid-display');
  elements.forEach(el => {
    const fontSize = window.getComputedStyle(el).fontSize;
    el.setAttribute('data-font-size', fontSize);
  });
}

window.addEventListener('resize', updateFluidDisplay);
updateFluidDisplay();
*/
```

## สรุป: Fluid Techniques Best Practices

### Key Concepts 🎯

1. **max-width: ความยืดหยุ่นพื้นฐาน**

   ```css
   .container {
     max-width: 1200px;
     margin: 0 auto;
     padding: 0 1rem;
   }
   ```

2. **clamp(): ปรับค่าในช่วงที่กำหนด**

   ```css
   .fluid-text {
     font-size: clamp(1rem, 2.5vw, 2rem);
     padding: clamp(1rem, 5vw, 3rem);
   }
   ```

3. **aspect-ratio: ควบคุมสัดส่วน**

   ```css
   .aspect-container {
     aspect-ratio: 16 / 9;
     max-width: 100%;
   }
   ```

4. **การรวมเทคนิค**
   - ใช้ CSS Custom Properties สำหรับ fluid values
   - รวม clamp() กับ responsive breakpoints
   - ใช้ aspect-ratio กับ object-fit

### Quick Reference 📋

```css
/* Essential fluid system */
:root {
  --space-sm: clamp(0.5rem, 2vw, 1rem);
  --space-md: clamp(1rem, 4vw, 2rem);
  --text-base: clamp(1rem, 2vw, 1.125rem);
  --container: clamp(320px, 90%, 1200px);
}

.fluid-component {
  max-width: var(--container);
  padding: var(--space-md);
  font-size: var(--text-base);
  aspect-ratio: 16 / 9;
}

/* Common clamp patterns */
.clamp-patterns {
  /* Typography */
  font-size: clamp(1rem, 2.5vw, 1.5rem);

  /* Spacing */
  padding: clamp(1rem, 5vw, 3rem);
  margin: clamp(0.5rem, 3vw, 2rem);
  gap: clamp(1rem, 4vw, 2rem);

  /* Sizes */
  width: clamp(300px, 50vw, 800px);
  border-radius: clamp(0.5rem, 1vw, 1rem);
}
```

Fluid Techniques ช่วยให้เราสร้าง responsive design ที่ปรับตัวอย่างลื่นไหลและธรรมชาติ ลดการพึ่งพา breakpoints เพียงอย่างเดียว!
