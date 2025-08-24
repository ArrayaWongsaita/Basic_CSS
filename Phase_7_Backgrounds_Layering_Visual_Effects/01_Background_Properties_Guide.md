# Background Properties: การจัดการพื้นหลังอย่างมืออาชีพ

## ภาพรวม Background Properties

**Background properties** เป็นเครื่องมือสำคัญในการสร้างความสวยงามและบรรยากาศให้กับเว็บไซต์ ช่วยให้เราสามารถควบคุมพื้นหลังได้อย่างละเอียดและสร้างเอฟเฟกต์ที่น่าประทับใจ

### Background Properties Family

```css
/* ครอบครัว Background Properties */
.background-overview {
  /* พื้นฐาน */
  background-color: #f3f4f6;
  background-image: url('image.jpg');

  /* การจัดวาง */
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;

  /* Shorthand */
  background: #f3f4f6 url('image.jpg') center / cover no-repeat;
}
```

## 1. background-color: การกำหนดสีพื้นหลัง

### สีพื้นฐานและการใช้งาน

```css
/* รูปแบบการกำหนดสีต่างๆ */
.background-colors {
  /* Hex colors */
  .hex-color {
    background-color: #3b82f6; /* Blue */
  }

  /* RGB/RGBA colors */
  .rgb-color {
    background-color: rgb(59, 130, 246);
    background-color: rgba(59, 130, 246, 0.8); /* With transparency */
  }

  /* HSL/HSLA colors */
  .hsl-color {
    background-color: hsl(217, 91%, 60%);
    background-color: hsla(217, 91%, 60%, 0.8);
  }

  /* Named colors */
  .named-color {
    background-color: royalblue;
    background-color: transparent;
    background-color: currentColor; /* ใช้สีเดียวกับ text */
  }

  /* CSS Custom Properties */
  :root {
    --primary-color: #3b82f6;
    --primary-alpha: #3b82f680;
  }

  .custom-property {
    background-color: var(--primary-color);
  }
}
```

### Gradient Backgrounds

```css
/* Background gradients */
.gradient-backgrounds {
  /* Linear gradients */
  .linear-basic {
    background: linear-gradient(to right, #3b82f6, #8b5cf6);
    /* จากซ้ายไปขวา: น้ำเงินไปม่วง */
  }

  .linear-angle {
    background: linear-gradient(45deg, #8b5cf6, #ec4899);
    /* ทิศทาง 45 องศา */
  }

  .linear-multi {
    background: linear-gradient(
      90deg,
      #ef4444 0%,
      #f59e0b 25%,
      #10b981 50%,
      #3b82f6 75%,
      #8b5cf6 100%
    );
    /* Rainbow gradient */
  }

  /* Radial gradients */
  .radial-basic {
    background: radial-gradient(circle, #3b82f6, #1e40af);
    /* วงกลมจากกลางออกไป */
  }

  .radial-positioned {
    background: radial-gradient(circle at top left, #8b5cf6, #6366f1, #1e40af);
    /* วงกลมที่มุมซ้ายบน */
  }

  /* Conic gradients */
  .conic-basic {
    background: conic-gradient(#3b82f6, #8b5cf6, #ec4899, #3b82f6);
    /* หมุนรอบจุดกลาง */
  }

  /* Repeating gradients */
  .repeating-linear {
    background: repeating-linear-gradient(
      45deg,
      #3b82f6 0px,
      #3b82f6 10px,
      #8b5cf6 10px,
      #8b5cf6 20px
    );
    /* ลายทแยง */
  }
}
```

## 2. background-image: การใส่รูปภาพพื้นหลัง

### พื้นฐาน background-image

```css
/* การใช้ background-image */
.background-images {
  /* Basic image usage */
  .single-image {
    background-image: url('hero-background.jpg');
  }

  /* Different formats */
  .image-formats {
    .jpg-background {
      background-image: url('photo.jpg'); /* ดีสำหรับรูปถ่าย */
    }

    .png-background {
      background-image: url('logo.png'); /* รองรับ transparency */
    }

    .svg-background {
      background-image: url('pattern.svg'); /* Vector, scalable */
    }

    .webp-background {
      background-image: url('modern.webp'); /* Modern format */
    }
  }

  /* Path types */
  .image-paths {
    /* Relative path */
    background-image: url('../images/background.jpg');

    /* Absolute path */
    background-image: url('/assets/images/hero.jpg');

    /* External URL */
    background-image: url('https://images.unsplash.com/photo-xyz');

    /* Data URL */
    background-image: url('data:image/svg+xml;base64,PHN2Zy4uLg==');
  }

  /* Fallback strategies */
  .with-fallback {
    background-color: #3b82f6; /* Fallback color */
    background-image: url('hero.jpg');
    /* ถ้ารูปโหลดไม่ได้จะแสดงสี */
  }
}
```

### Responsive Images

```css
/* Responsive background images */
.responsive-images {
  /* CSS-only responsive */
  .responsive-bg {
    background-image: url('hero-mobile.jpg');
  }

  @media (min-width: 768px) {
    .responsive-bg {
      background-image: url('hero-tablet.jpg');
    }
  }

  @media (min-width: 1024px) {
    .responsive-bg {
      background-image: url('hero-desktop.jpg');
    }
  }

  /* High DPI support */
  .high-dpi {
    background-image: url('image-1x.jpg');
  }

  @media (-webkit-min-device-pixel-ratio: 2), (min-resolution: 2dppx) {
    .high-dpi {
      background-image: url('image-2x.jpg');
    }
  }

  /* Progressive enhancement */
  .progressive-bg {
    background-image: url('low-quality.jpg');
  }

  .progressive-bg.loaded {
    background-image: url('high-quality.jpg');
    transition: opacity 0.3s ease;
  }
}
```

## 3. background-size: การปรับขนาดรูปพื้นหลัง

### พื้นฐาน background-size

```css
/* background-size values */
.background-sizing {
  /* Keywords */
  .size-keywords {
    /* cover: ครอบคลุมพื้นที่ทั้งหมด */
    .cover-size {
      background-image: url('landscape.jpg');
      background-size: cover;
      /*
      ผลลัพธ์:
      - รูปจะขยายให้ครอบคลุม container ทั้งหมด
      - รักษาสัดส่วนเดิม
      - อาจมีส่วนของรูปที่ถูกตัดออก
      - ไม่มีพื้นที่ว่าง
      */
    }

    /* contain: แสดงรูปทั้งหมด */
    .contain-size {
      background-image: url('portrait.jpg');
      background-size: contain;
      /*
      ผลลัพธ์:
      - รูปจะแสดงทั้งหมดใน container
      - รักษาสัดส่วนเดิม
      - อาจมีพื้นที่ว่าง
      - ไม่มีการตัดรูป
      */
    }

    /* auto: ขนาดเดิมของรูป */
    .auto-size {
      background-image: url('icon.png');
      background-size: auto;
    }
  }

  /* Specific dimensions */
  .specific-dimensions {
    /* Fixed pixels */
    .pixel-size {
      background-size: 200px 150px; /* กว้าง 200px สูง 150px */
    }

    /* Percentages */
    .percentage-size {
      background-size: 100% 100%; /* เต็มพื้นที่ (อาจบิดเบี้ยว) */
    }

    /* Mixed units */
    .mixed-size {
      background-size: 100% auto; /* กว้างเต็ม สูงตามสัดส่วน */
    }

    /* Single value */
    .single-value {
      background-size: 80px; /* กว้าง 80px สูงตามสัดส่วน */
    }
  }

  /* Responsive sizing */
  .responsive-sizing {
    /* Viewport units */
    .viewport-size {
      background-size: 100vw 100vh; /* เต็ม viewport */
    }

    /* With calc() */
    .calculated-size {
      background-size: calc(100% - 40px) auto;
    }
  }
}
```

### เปรียบเทียบ cover vs contain

```css
/* Use cases comparison */
.cover-vs-contain {
  /* cover: เหมาะสำหรับ */
  .cover-use-cases {
    /* Hero sections */
    .hero-section {
      height: 100vh;
      background-image: url('hero.jpg');
      background-size: cover;
      background-position: center;
      /* ต้องการพื้นหลังเต็มหน้าจอ */
    }

    /* Card backgrounds */
    .card-background {
      height: 200px;
      background-image: url('card-bg.jpg');
      background-size: cover;
      /* ต้องการพื้นหลังเต็มการ์ด */
    }
  }

  /* contain: เหมาะสำหรับ */
  .contain-use-cases {
    /* Logo backgrounds */
    .logo-container {
      width: 200px;
      height: 100px;
      background-image: url('logo.svg');
      background-size: contain;
      background-repeat: no-repeat;
      background-position: center;
      /* ต้องการแสดงโลโก้ทั้งหมด */
    }

    /* Product images */
    .product-image {
      width: 300px;
      height: 300px;
      background-image: url('product.png');
      background-size: contain;
      background-repeat: no-repeat;
      background-position: center;
      background-color: #f8fafc;
    }
  }
}
```

## 4. background-position: การจัดตำแหน่งรูพื้นหลัง

### พื้นฐาน background-position

```css
/* background-position values */
.background-positioning {
  /* Keywords */
  .keyword-positions {
    .top-left {
      background-position: top left;
    }
    .top-center {
      background-position: top center;
    }
    .top-right {
      background-position: top right;
    }
    .center-left {
      background-position: center left;
    }
    .center-center {
      background-position: center center;
    }
    .center-right {
      background-position: center right;
    }
    .bottom-left {
      background-position: bottom left;
    }
    .bottom-center {
      background-position: bottom center;
    }
    .bottom-right {
      background-position: bottom right;
    }

    /* Single keyword */
    .center-position {
      background-position: center; /* เท่ากับ center center */
    }
  }

  /* Percentage values */
  .percentage-positions {
    .percent-examples {
      background-position: 0% 0%; /* เท่ากับ top left */
      background-position: 50% 50%; /* เท่ากับ center */
      background-position: 100% 100%; /* เท่ากับ bottom right */
      background-position: 25% 75%; /* 25% จากซ้าย, 75% จากบน */
    }

    /*
    การคำนวณ percentage:
    X = (container-width - image-width) × percentage
    Y = (container-height - image-height) × percentage
    */
  }

  /* Length values */
  .length-positions {
    .pixel-positions {
      background-position: 20px 30px; /* 20px จากซ้าย, 30px จากบน */
      background-position: -10px -20px; /* เลื่อนออกไปนอก container */
    }

    /* Mixed units */
    .mixed-units {
      background-position: 50% 20px; /* 50% horizontally, 20px from top */
    }

    /* Four-value syntax */
    .four-value {
      background-position: right 20px bottom 30px;
      /* 20px จากขวา, 30px จากล่าง */
    }
  }
}
```

### การใช้งานในทางปฏิบัติ

```css
/* Practical positioning examples */
.practical-positioning {
  /* Hero sections */
  .hero-positioning {
    .hero-portrait {
      height: 500px;
      background-image: url('hero-portrait.jpg');
      background-size: cover;
      background-position: center top; /* โฟกัสที่หน้าคน */
    }

    .hero-landscape {
      height: 400px;
      background-image: url('hero-landscape.jpg');
      background-size: cover;
      background-position: center bottom; /* โฟกัสที่ส่วนล่าง */
    }
  }

  /* Logo positioning */
  .logo-positioning {
    .corner-logo {
      padding: 20px;
      background-image: url('watermark-logo.png');
      background-size: 80px auto;
      background-repeat: no-repeat;
      background-position: bottom right; /* โลโก้มุมขวาล่าง */
    }

    .inset-logo {
      background-image: url('company-logo.svg');
      background-size: 120px auto;
      background-repeat: no-repeat;
      background-position: right 20px top 20px; /* 20px จากขวาและบน */
    }
  }

  /* Interactive positioning */
  .hover-shift {
    background-image: url('background.jpg');
    background-size: 110%;
    background-position: center;
    transition: background-position 0.3s ease;
  }

  .hover-shift:hover {
    background-position: top center; /* เลื่อนขึ้นเมื่อ hover */
  }
}
```

## 5. background-repeat: การควบคุมการทำซ้ำ

### พื้นฐาน background-repeat

```css
/* background-repeat values */
.background-repeating {
  /* Main values */
  .repeat-values {
    /* repeat: ทำซ้ำทั้งสองแกน (default) */
    .repeat-default {
      background-image: url('small-pattern.png');
      background-repeat: repeat;
      /* เหมาะสำหรับ pattern และ texture */
    }

    /* repeat-x: ทำซ้ำแนวนอนเท่านั้น */
    .repeat-horizontal {
      background-image: url('horizontal-border.png');
      background-repeat: repeat-x;
      /* เหมาะสำหรับ border บนล่าง */
    }

    /* repeat-y: ทำซ้ำแนวตั้งเท่านั้น */
    .repeat-vertical {
      background-image: url('vertical-border.png');
      background-repeat: repeat-y;
      /* เหมาะสำหรับ border ซ้ายขวา */
    }

    /* no-repeat: ไม่ทำซ้ำ */
    .no-repeat {
      background-image: url('single-image.jpg');
      background-repeat: no-repeat;
      /* เหมาะสำหรับรูปภาพ hero, logo */
    }
  }

  /* Modern values */
  .modern-repeat {
    /* space: กระจายด้วยช่องว่าง */
    .repeat-space {
      background-image: url('tile.png');
      background-repeat: space;
      /* ทำซ้ำโดยไม่ตัดรูป, เติมช่องว่าง */
    }

    /* round: ปรับขนาดให้พอดี */
    .repeat-round {
      background-image: url('flexible-tile.svg');
      background-repeat: round;
      /* ปรับขนาดรูปให้พอดีกับพื้นที่ */
    }
  }

  /* Two-value syntax */
  .mixed-repeat {
    background-image: url('pattern.png');
    background-repeat: repeat-x no-repeat; /* แนวนอน: repeat, แนวตั้ง: no-repeat */
  }
}
```

### การใช้งานในทางปฏิบัติ

```css
/* Practical repeat examples */
.practical-repeat {
  /* Pattern backgrounds */
  .patterns {
    .seamless-pattern {
      background-image: url('seamless-dots.svg');
      background-repeat: repeat;
      background-size: 50px 50px;
      /* Dot patterns, geometric patterns */
    }

    .grid-pattern {
      background-image: url('grid.svg');
      background-repeat: repeat;
      background-size: 20px 20px;
      opacity: 0.3;
      /* Graph paper effect */
    }
  }

  /* Borders and decorations */
  .borders {
    .top-border {
      background-image: url('decorative-border.svg');
      background-repeat: repeat-x;
      background-position: top;
      background-size: auto 20px;
      padding-top: 30px;
      /* Decorative top borders */
    }

    .side-border {
      background-image: url('side-decoration.svg');
      background-repeat: repeat-y;
      background-position: left;
      background-size: 15px auto;
      padding-left: 25px;
      /* Vertical separators */
    }
  }

  /* Icon patterns */
  .icon-patterns {
    .icon-grid {
      background-image: url('social-icon.svg');
      background-repeat: space;
      background-size: 40px 40px;
      min-height: 200px;
      /* Social media backgrounds */
    }
  }
}
```

## 6. Multiple Backgrounds: การใช้พื้นหลังหลายชั้น

### พื้นฐาน Multiple Backgrounds

```css
/* Multiple backgrounds syntax */
.multiple-backgrounds {
  /* Basic multiple backgrounds */
  .basic-multiple {
    /* Layer order: first = top, last = bottom */
    background-image: url('overlay.png'), /* Top layer */ url('pattern.svg'), /* Middle layer */
        url('background.jpg'); /* Bottom layer */

    background-repeat: no-repeat, /* overlay */ repeat, /* pattern */ no-repeat; /* background */

    background-position: center, /* overlay */ top left, /* pattern */ center; /* background */

    background-size: 300px 200px, /* overlay */ 50px 50px, /* pattern */ cover; /* background */
  }

  /* Shorthand syntax */
  .shorthand-multiple {
    background: url('top.png') center / 100px 100px no-repeat, url('middle.svg')
        repeat, #f3f4f6 url('bottom.jpg') center / cover no-repeat;
  }

  /* Mixed content types */
  .mixed-content {
    background: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)),
      url('pattern.svg') repeat, radial-gradient(circle, #3b82f6, #1e40af), url('fallback.jpg')
        center / cover;
  }
}
```

### เทคนิค Layering ขั้นสูง

```css
/* Advanced layering techniques */
.advanced-layering {
  /* Overlay effects */
  .overlay-effects {
    /* Dark overlay on image */
    .dark-overlay {
      background: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.4)),
        url('bright-image.jpg') center / cover;
      color: white;
      /* เหมาะสำหรับ hero sections with text */
    }

    /* Gradient overlay */
    .gradient-overlay {
      background: linear-gradient(
          135deg,
          rgba(59, 130, 246, 0.8),
          rgba(139, 92, 246, 0.6)
        ), url('hero-bg.jpg') center / cover;
      /* Brand color overlay */
    }

    /* Pattern overlay */
    .pattern-overlay {
      background: url('dots-overlay.svg') repeat, linear-gradient(
          45deg,
          #f8fafc,
          #e2e8f0
        ), url('texture.jpg') center / cover;
      background-size: 20px 20px, auto, cover;
      /* Textured backgrounds */
    }
  }

  /* Complex compositions */
  .complex-hero {
    background:
      /* Top overlay */ linear-gradient(
        to bottom,
        rgba(0, 0, 0, 0.3) 0%,
        rgba(0, 0, 0, 0.1) 50%,
        rgba(0, 0, 0, 0.4) 100%
      ),
      /* Particles */ radial-gradient(circle at 20% 20%, rgba(
              255,
              255,
              255,
              0.1
            ) 1px, transparent 1px), /* Pattern */ url('geometric-pattern.svg')
        center / 400px 400px,
      /* Main background */ url('hero-background.jpg') center / cover;

    background-repeat: no-repeat, repeat, no-repeat, no-repeat;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
  }
}
```

### การประยุกต์ใช้ในทางปฏิบัติ

```css
/* Practical applications */
.practical-applications {
  /* Modern header */
  .modern-header {
    background: linear-gradient(
        135deg,
        rgba(99, 102, 241, 0.95),
        rgba(139, 92, 246, 0.9)
      ), url('pattern.svg') repeat, url('header-bg.jpg') center / cover;
    background-size: auto, 50px 50px, cover;
    padding: 80px 0;
    color: white;
  }

  /* Product card */
  .product-card {
    background: linear-gradient(
        to bottom right,
        rgba(255, 255, 255, 1),
        rgba(248, 250, 252, 1)
      ), url('brand-pattern.svg') bottom right / 100px 100px no-repeat, #ffffff;
    border-radius: 12px;
    padding: 24px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  /* Testimonials section */
  .testimonials-bg {
    background: url('quote-left.svg') 5% 20% / 40px 40px no-repeat, url('quote-right.svg')
        95% 80% / 40px 40px no-repeat, url('paper-texture.svg') repeat, linear-gradient(
        to bottom,
        #fafafa,
        #f5f5f5
      );
    background-size: 40px 40px, 40px 40px, 200px 200px, auto;
    padding: 80px 0;
  }

  /* Interactive button */
  .enhanced-button {
    background: linear-gradient(
        45deg,
        transparent 30%,
        rgba(255, 255, 255, 0.2) 50%,
        transparent 70%
      ), linear-gradient(135deg, #3b82f6, #2563eb);
    background-size: 200% 100%, 100% 100%;
    background-position: -100% 0, 0 0;
    color: white;
    border: none;
    padding: 12px 24px;
    border-radius: 6px;
    transition: background-position 0.3s ease;
  }

  .enhanced-button:hover {
    background-position: 100% 0, 0 0; /* Shine effect */
  }
}
```

## สรุป: Background Properties Best Practices

### Key Concepts 🎯

1. **background-color: พื้นฐานที่สำคัญ**

   ```css
   .element {
     background-color: #f3f4f6; /* Always provide fallback */
     background-image: url('image.jpg');
   }
   ```

2. **background-size: cover vs contain**

   ```css
   .hero {
     background-size: cover;
   } /* Fill container, may crop */
   .logo {
     background-size: contain;
   } /* Show full image, may have space */
   ```

3. **background-position: จัดตำแหน่งอย่างแม่นยำ**

   ```css
   .positioned {
     background-position: right 20px bottom 30px;
   }
   ```

4. **Multiple backgrounds: ลำดับชั้นสำคัญ**
   ```css
   .layered {
     background: url('top.png'), /* Top layer */ url('middle.svg'), /* Middle */
         url('bottom.jpg'); /* Bottom */
   }
   ```

### Quick Reference 📋

```css
/* Complete background system */
.background-system {
  /* Fallback color first */
  background-color: #f3f4f6;

  /* Multiple layers */
  background-image: linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),
    url('pattern.svg'), url('background.jpg');

  /* Individual properties */
  background-repeat: no-repeat, repeat, no-repeat;
  background-position: center, top left, center;
  background-size: auto, 50px 50px, cover;
}

/* Common patterns */
.common-patterns {
  /* Hero with overlay */
  .hero {
    background: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)),
      url('hero.jpg') center / cover;
  }

  /* Logo container */
  .logo {
    background: url('logo.svg') center / contain no-repeat;
  }

  /* Pattern background */
  .pattern {
    background: url('pattern.svg') repeat;
    background-size: 50px 50px;
  }
}
```

Background Properties ช่วยให้เราสร้างพื้นหลังที่สวยงามและมีประสิทธิภาพ จากสีธรรมดาไปจนถึง composition ที่ซับซ้อน!
