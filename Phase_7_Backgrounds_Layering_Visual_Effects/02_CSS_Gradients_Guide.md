# CSS Gradients: การสร้าง Gradient ด้วย CSS

## ภาพรวม CSS Gradients

**CSS Gradients** เป็นเครื่องมือที่ทรงพลังในการสร้างการไล่สีแบบต่างๆ โดยไม่ต้องใช้รูปภาพ ช่วยลดขนาดไฟล์และเพิ่มความยืดหยุ่นในการปรับแต่ง

### ประเภทของ Gradients

```css
/* ประเภท Gradients หลัก */
.gradient-types {
  /* Linear Gradient - ไล่สีแบบเส้นตรง */
  .linear-example {
    background: linear-gradient(to right, #3b82f6, #8b5cf6);
  }

  /* Radial Gradient - ไล่สีแบบวงกลม/รัศมี */
  .radial-example {
    background: radial-gradient(circle, #3b82f6, #8b5cf6);
  }

  /* Conic Gradient - ไล่สีแบบหมุน */
  .conic-example {
    background: conic-gradient(#3b82f6, #8b5cf6, #ec4899, #3b82f6);
  }

  /* Repeating Gradients - Gradient ซ้ำ */
  .repeating-example {
    background: repeating-linear-gradient(
      45deg,
      #3b82f6 0px,
      #3b82f6 10px,
      #8b5cf6 10px,
      #8b5cf6 20px
    );
  }
}
```

## 1. linear-gradient(): การไล่สีแบบเส้นตรง

### พื้นฐาน linear-gradient()

```css
/* Syntax: linear-gradient(direction, color-stop1, color-stop2, ...) */
.linear-gradient-basics {
  /* Basic linear gradient */
  .basic-linear {
    background: linear-gradient(#3b82f6, #8b5cf6);
    /* จากบนลงล่าง: น้ำเงินไปม่วง (default direction) */
  }

  /* Direction keywords */
  .direction-keywords {
    .to-right {
      background: linear-gradient(to right, #3b82f6, #8b5cf6);
      /* จากซ้ายไปขวา */
    }

    .to-left {
      background: linear-gradient(to left, #3b82f6, #8b5cf6);
      /* จากขวาไปซ้าย */
    }

    .to-top {
      background: linear-gradient(to top, #3b82f6, #8b5cf6);
      /* จากล่างขึ้นบน */
    }

    .to-bottom {
      background: linear-gradient(to bottom, #3b82f6, #8b5cf6);
      /* จากบนลงล่าง (เหมือน default) */
    }

    /* Diagonal directions */
    .to-top-right {
      background: linear-gradient(to top right, #3b82f6, #8b5cf6);
      /* เฉียงขึ้นขวา */
    }

    .to-bottom-left {
      background: linear-gradient(to bottom left, #3b82f6, #8b5cf6);
      /* เฉียงลงซ้าย */
    }

    .to-top-left {
      background: linear-gradient(to top left, #3b82f6, #8b5cf6);
      /* เฉียงขึ้นซ้าย */
    }

    .to-bottom-right {
      background: linear-gradient(to bottom right, #3b82f6, #8b5cf6);
      /* เฉียงลงขวา */
    }
  }

  /* Angle directions */
  .angle-directions {
    .angle-0 {
      background: linear-gradient(0deg, #3b82f6, #8b5cf6);
      /* 0° = to top */
    }

    .angle-45 {
      background: linear-gradient(45deg, #3b82f6, #8b5cf6);
      /* 45° = เฉียงขึ้นขวา */
    }

    .angle-90 {
      background: linear-gradient(90deg, #3b82f6, #8b5cf6);
      /* 90° = to right */
    }

    .angle-135 {
      background: linear-gradient(135deg, #3b82f6, #8b5cf6);
      /* 135° = เฉียงลงขวา */
    }

    .angle-180 {
      background: linear-gradient(180deg, #3b82f6, #8b5cf6);
      /* 180° = to bottom */
    }

    .angle-270 {
      background: linear-gradient(270deg, #3b82f6, #8b5cf6);
      /* 270° = to left */
    }
  }

  /* Multiple colors */
  .multiple-colors {
    .three-colors {
      background: linear-gradient(to right, #ef4444, #f59e0b, #10b981);
      /* แดง -> เหลือง -> เขียว */
    }

    .rainbow {
      background: linear-gradient(
        90deg,
        #ef4444 0%,
        #f59e0b 16.66%,
        #eab308 33.33%,
        #22c55e 50%,
        #3b82f6 66.66%,
        #6366f1 83.33%,
        #8b5cf6 100%
      );
      /* Rainbow colors */
    }

    .sunset {
      background: linear-gradient(
        to bottom,
        #fbbf24,
        #f59e0b,
        #dc2626,
        #7c2d12
      );
      /* Sunset effect */
    }
  }
}
```

### Color Stops และ Positioning

```css
/* Color stops และการควบคุมตำแหน่ง */
.color-stops-positioning {
  /* Basic color stops */
  .basic-stops {
    background: linear-gradient(to right, #3b82f6 0%, #8b5cf6 100%);
    /* ระบุตำแหน่งชัดเจน */
  }

  /* Multiple stops with positions */
  .positioned-stops {
    background: linear-gradient(
      to right,
      #ef4444 0%,
      #f59e0b 25%,
      #22c55e 75%,
      #3b82f6 100%
    );
    /* แต่ละสีอยู่ตำแหน่งที่กำหนด */
  }

  /* Abrupt color changes */
  .abrupt-changes {
    background: linear-gradient(
      to right,
      #ef4444 0%,
      #ef4444 33%,
      #22c55e 33%,
      #22c55e 66%,
      #3b82f6 66%,
      #3b82f6 100%
    );
    /* สีเปลี่ยนแบบทันที ไม่ค่อยๆ ไล่ */
  }

  /* Overlapping stops */
  .overlapping-stops {
    background: linear-gradient(
      to right,
      #3b82f6 0%,
      #3b82f6 40%,
      #8b5cf6 60%,
      #8b5cf6 100%
    );
    /* มีจุดที่ไล่สีระหว่าง 40%-60% */
  }

  /* Uneven distribution */
  .uneven-distribution {
    background: linear-gradient(
      to right,
      #ef4444 0%,
      #f59e0b 10%,
      #22c55e 90%,
      #3b82f6 100%
    );
    /* พื้นที่ส่วนใหญ่เป็นสีเขียว */
  }

  /* Color stops without positions */
  .auto-distribution {
    background: linear-gradient(to right, #ef4444, #f59e0b, #22c55e, #3b82f6);
    /* Browser จะกระจายสีให้เท่าๆ กัน */
  }

  /* Mixed positioning */
  .mixed-positioning {
    background: linear-gradient(
      45deg,
      #3b82f6 0%,
      #8b5cf6,
      /* ไม่ระบุตำแหน่ง = auto */ #ec4899 80%,
      #f59e0b
    );
    /* บางสีระบุตำแหน่ง บางสีไม่ระบุ */
  }
}
```

### Advanced Linear Gradient Techniques

```css
/* เทคนิค linear gradient ขั้นสูง */
.advanced-linear-techniques {
  /* Transparency gradients */
  .transparency-gradients {
    .fade-to-transparent {
      background: linear-gradient(to right, #3b82f6, transparent);
      /* ไล่จากสีน้ำเงินไปใส */
    }

    .alpha-fade {
      background: linear-gradient(
        to bottom,
        rgba(59, 130, 246, 1),
        rgba(59, 130, 246, 0)
      );
      /* ควบคุม opacity แบบละเอียด */
    }

    .overlay-gradient {
      background: linear-gradient(
          to bottom,
          rgba(0, 0, 0, 0.7),
          rgba(0, 0, 0, 0.3)
        ), url('background-image.jpg');
      /* Gradient overlay บนรูป */
    }
  }

  /* Text effects */
  .text-effects {
    .gradient-text {
      background: linear-gradient(45deg, #3b82f6, #8b5cf6, #ec4899);
      -webkit-background-clip: text;
      background-clip: text;
      -webkit-text-fill-color: transparent;
      color: transparent; /* Fallback */
      font-size: 3rem;
      font-weight: bold;
    }

    .animated-gradient-text {
      background: linear-gradient(
        45deg,
        #3b82f6,
        #8b5cf6,
        #ec4899,
        #f59e0b,
        #3b82f6
      );
      background-size: 300% 300%;
      -webkit-background-clip: text;
      background-clip: text;
      -webkit-text-fill-color: transparent;
      animation: gradientShift 3s ease infinite;
    }

    @keyframes gradientShift {
      0% {
        background-position: 0% 50%;
      }
      50% {
        background-position: 100% 50%;
      }
      100% {
        background-position: 0% 50%;
      }
    }
  }

  /* Border gradients */
  .border-gradients {
    .gradient-border {
      background: linear-gradient(white, white) padding-box, linear-gradient(
            45deg,
            #3b82f6,
            #8b5cf6
          ) border-box;
      border: 4px solid transparent;
      border-radius: 8px;
      padding: 20px;
    }

    .animated-border {
      background: linear-gradient(white, white) padding-box, linear-gradient(
            45deg,
            #3b82f6,
            #8b5cf6,
            #ec4899,
            #3b82f6
          ) border-box;
      background-size: 100% 100%, 300% 300%;
      border: 3px solid transparent;
      border-radius: 12px;
      padding: 24px;
      animation: borderGradient 3s ease infinite;
    }

    @keyframes borderGradient {
      0% {
        background-position: 0% 0%, 0% 50%;
      }
      50% {
        background-position: 0% 0%, 100% 50%;
      }
      100% {
        background-position: 0% 0%, 0% 50%;
      }
    }
  }

  /* Button gradients */
  .button-gradients {
    .gradient-button {
      background: linear-gradient(135deg, #3b82f6, #1d4ed8);
      color: white;
      border: none;
      padding: 12px 24px;
      border-radius: 6px;
      font-size: 16px;
      cursor: pointer;
      transition: all 0.3s ease;
      position: relative;
      overflow: hidden;
    }

    .gradient-button::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(
        90deg,
        transparent,
        rgba(255, 255, 255, 0.2),
        transparent
      );
      transition: left 0.5s ease;
    }

    .gradient-button:hover::before {
      left: 100%;
    }

    .gradient-button:hover {
      background: linear-gradient(135deg, #2563eb, #1e40af);
      transform: translateY(-2px);
      box-shadow: 0 8px 16px rgba(59, 130, 246, 0.3);
    }
  }

  /* Card gradients */
  .card-gradients {
    .gradient-card {
      background: linear-gradient(
        135deg,
        rgba(255, 255, 255, 0.9),
        rgba(255, 255, 255, 0.7)
      );
      backdrop-filter: blur(10px);
      border: 1px solid rgba(255, 255, 255, 0.2);
      border-radius: 16px;
      padding: 24px;
      box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
    }

    .glass-card {
      background: linear-gradient(
        135deg,
        rgba(59, 130, 246, 0.1),
        rgba(139, 92, 246, 0.1)
      );
      backdrop-filter: blur(20px);
      border: 1px solid rgba(255, 255, 255, 0.1);
      border-radius: 20px;
      padding: 32px;
      box-shadow: 0 12px 40px rgba(0, 0, 0, 0.15);
    }
  }
}
```

## 2. radial-gradient(): การไล่สีแบบรัศมี

### พื้นฐาน radial-gradient()

```css
/* Syntax: radial-gradient(shape size at position, color-stop1, color-stop2, ...) */
.radial-gradient-basics {
  /* Basic radial gradient */
  .basic-radial {
    background: radial-gradient(#3b82f6, #8b5cf6);
    /* วงกลมจากกลาง ไล่จากน้ำเงินไปม่วง */
  }

  /* Shape types */
  .shape-types {
    .circle-gradient {
      background: radial-gradient(circle, #3b82f6, #8b5cf6);
      /* วงกลมสมบูรณ์ */
    }

    .ellipse-gradient {
      background: radial-gradient(ellipse, #3b82f6, #8b5cf6);
      /* วงรี (default) */
    }
  }

  /* Size keywords */
  .size-keywords {
    .closest-side {
      background: radial-gradient(circle closest-side, #3b82f6, #8b5cf6);
      /* วงกลมที่มีรัศมีถึงด้านที่ใกล้ที่สุด */
    }

    .closest-corner {
      background: radial-gradient(circle closest-corner, #3b82f6, #8b5cf6);
      /* วงกลมที่มีรัศมีถึงมุมที่ใกล้ที่สุด */
    }

    .farthest-side {
      background: radial-gradient(circle farthest-side, #3b82f6, #8b5cf6);
      /* วงกลมที่มีรัศมีถึงด้านที่ไกลที่สุด */
    }

    .farthest-corner {
      background: radial-gradient(circle farthest-corner, #3b82f6, #8b5cf6);
      /* วงกลมที่มีรัศมีถึงมุมที่ไกลที่สุด (default) */
    }
  }

  /* Explicit sizes */
  .explicit-sizes {
    .pixel-size {
      background: radial-gradient(circle 100px, #3b82f6, #8b5cf6);
      /* วงกลมรัศมี 100px */
    }

    .percentage-size {
      background: radial-gradient(ellipse 80% 60%, #3b82f6, #8b5cf6);
      /* วงรี กว้าง 80% สูง 60% ของ container */
    }

    .mixed-units {
      background: radial-gradient(ellipse 200px 100px, #3b82f6, #8b5cf6);
      /* วงรี กว้าง 200px สูง 100px */
    }
  }

  /* Position */
  .position-variations {
    .center-position {
      background: radial-gradient(circle at center, #3b82f6, #8b5cf6);
      /* ตรงกลาง (default) */
    }

    .corner-positions {
      .top-left {
        background: radial-gradient(circle at top left, #3b82f6, #8b5cf6);
        /* มุมซ้ายบน */
      }

      .bottom-right {
        background: radial-gradient(circle at bottom right, #3b82f6, #8b5cf6);
        /* มุมขวาล่าง */
      }
    }

    .percentage-positions {
      background: radial-gradient(circle at 25% 75%, #3b82f6, #8b5cf6);
      /* 25% จากซ้าย, 75% จากบน */
    }

    .pixel-positions {
      background: radial-gradient(circle at 100px 50px, #3b82f6, #8b5cf6);
      /* 100px จากซ้าย, 50px จากบน */
    }
  }
}
```

### Advanced Radial Gradient Techniques

```css
/* เทคนิค radial gradient ขั้นสูง */
.advanced-radial-techniques {
  /* Multiple color stops */
  .multiple-stops {
    .concentric-circles {
      background: radial-gradient(
        circle,
        #3b82f6 0%,
        #8b5cf6 25%,
        #ec4899 50%,
        #f59e0b 75%,
        #ef4444 100%
      );
      /* วงกลมหลายชั้น */
    }

    .bulls-eye {
      background: radial-gradient(
        circle,
        #ef4444 0%,
        #ef4444 20%,
        #ffffff 20%,
        #ffffff 40%,
        #ef4444 40%,
        #ef4444 60%,
        #ffffff 60%,
        #ffffff 80%,
        #ef4444 80%
      );
      /* ลายเป้า */
    }
  }

  /* Spotlight effects */
  .spotlight-effects {
    .spotlight {
      background: radial-gradient(
        circle 300px at center,
        rgba(255, 255, 255, 0.3),
        rgba(0, 0, 0, 0.8)
      );
      /* เอฟเฟกต์แสงสปอตไลท์ */
    }

    .vignette {
      background: radial-gradient(
        ellipse at center,
        transparent 30%,
        rgba(0, 0, 0, 0.7)
      );
      /* เอฟเฟกต์ vignette */
    }

    .glowing-orb {
      background: radial-gradient(
        circle,
        #ffffff 0%,
        #3b82f6 30%,
        #1e40af 60%,
        #000000 100%
      );
      /* ลูกโลกเรืองแสง */
    }
  }

  /* Button effects */
  .radial-buttons {
    .glowing-button {
      background: radial-gradient(ellipse at center, #60a5fa, #3b82f6);
      color: white;
      border: none;
      padding: 16px 32px;
      border-radius: 25px;
      font-size: 16px;
      cursor: pointer;
      position: relative;
      overflow: hidden;
      transition: all 0.3s ease;
    }

    .glowing-button::before {
      content: '';
      position: absolute;
      top: 50%;
      left: 50%;
      width: 0;
      height: 0;
      background: radial-gradient(
        circle,
        rgba(255, 255, 255, 0.5),
        transparent 70%
      );
      transition: all 0.6s ease;
      transform: translate(-50%, -50%);
      border-radius: 50%;
    }

    .glowing-button:hover::before {
      width: 300px;
      height: 300px;
    }

    .glowing-button:hover {
      background: radial-gradient(ellipse at center, #93c5fd, #2563eb);
      box-shadow: 0 0 20px rgba(59, 130, 246, 0.5);
    }
  }

  /* Background patterns */
  .radial-patterns {
    .dots-pattern {
      background-image: radial-gradient(
        circle 2px,
        #3b82f6 100%,
        transparent 100%
      );
      background-size: 20px 20px;
      background-repeat: repeat;
      /* ลายจุด */
    }

    .ripple-pattern {
      background-image: radial-gradient(
        circle 10px,
        transparent 9px,
        #3b82f6 9px,
        #3b82f6 11px,
        transparent 11px
      );
      background-size: 30px 30px;
      background-repeat: repeat;
      /* ลายคลื่น */
    }

    .bubble-pattern {
      background-image: radial-gradient(
          circle 15px,
          rgba(59, 130, 246, 0.3) 50%,
          transparent 50%
        ), radial-gradient(
          circle 8px,
          rgba(139, 92, 246, 0.4) 50%,
          transparent 50%
        ), radial-gradient(circle 12px, rgba(236, 72, 153, 0.2) 50%, transparent
            50%);
      background-size: 60px 60px, 40px 40px, 80px 80px;
      background-position: 0 0, 20px 20px, 40px 40px;
      /* ลายฟองน้ำ */
    }
  }

  /* Card effects */
  .radial-cards {
    .radial-card {
      background: radial-gradient(
        ellipse at top left,
        rgba(59, 130, 246, 0.2),
        rgba(139, 92, 246, 0.1),
        rgba(255, 255, 255, 0.9)
      );
      border-radius: 16px;
      padding: 24px;
      box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
      backdrop-filter: blur(4px);
      border: 1px solid rgba(255, 255, 255, 0.2);
    }

    .glowing-card {
      background: radial-gradient(
        circle at center,
        rgba(59, 130, 246, 0.1),
        rgba(139, 92, 246, 0.05),
        transparent
      );
      border-radius: 20px;
      padding: 32px;
      position: relative;
      overflow: hidden;
    }

    .glowing-card::before {
      content: '';
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: radial-gradient(
        circle,
        rgba(59, 130, 246, 0.1),
        transparent 50%
      );
      animation: cardGlow 4s ease-in-out infinite;
    }

    @keyframes cardGlow {
      0%,
      100% {
        transform: scale(1) rotate(0deg);
      }
      50% {
        transform: scale(1.1) rotate(180deg);
      }
    }
  }
}
```

## 3. Combining Gradients: การผสม Gradients

### Multiple Gradients

```css
/* การใช้ gradients หลายชั้น */
.combining-gradients {
  /* Layered gradients */
  .layered-gradients {
    .gradient-overlay {
      background: linear-gradient(
          45deg,
          rgba(59, 130, 246, 0.7),
          rgba(139, 92, 246, 0.7)
        ), radial-gradient(
          circle at top right,
          rgba(236, 72, 153, 0.3),
          transparent
        ), linear-gradient(135deg, #f3f4f6, #e5e7eb);
      /*
      ชั้นที่ 1: Linear gradient แบบโปร่งใส
      ชั้นที่ 2: Radial gradient ที่มุมขวาบน
      ชั้นที่ 3: Linear gradient พื้นหลัง
      */
    }

    .complex-background {
      background: radial-gradient(
          ellipse at top,
          rgba(59, 130, 246, 0.1),
          transparent
        ), radial-gradient(
          ellipse at bottom,
          rgba(139, 92, 246, 0.1),
          transparent
        ), linear-gradient(to right, #fafafa, #f8fafc, #fafafa);
      /* สร้างเอฟเฟกต์แสงนุ่มๆ */
    }

    .artistic-blend {
      background: conic-gradient(
          from 45deg at 30% 70%,
          rgba(59, 130, 246, 0.3),
          rgba(139, 92, 246, 0.3),
          rgba(236, 72, 153, 0.3)
        ), radial-gradient(
          circle at 80% 20%,
          rgba(245, 158, 11, 0.2),
          transparent
        ), linear-gradient(135deg, #f8fafc, #f1f5f9);
      /* การผสมที่ซับซ้อน */
    }
  }

  /* Interactive gradients */
  .interactive-gradients {
    .hover-gradient {
      background: linear-gradient(45deg, #3b82f6, #8b5cf6);
      transition: all 0.3s ease;
      padding: 20px;
      border-radius: 12px;
      cursor: pointer;
    }

    .hover-gradient:hover {
      background: radial-gradient(
          circle at center,
          rgba(255, 255, 255, 0.2),
          transparent
        ), linear-gradient(45deg, #2563eb, #7c3aed);
      transform: translateY(-2px);
      box-shadow: 0 12px 24px rgba(59, 130, 246, 0.3);
    }

    .animated-blend {
      background: linear-gradient(45deg, #3b82f6, #8b5cf6, #ec4899, #f59e0b),
        radial-gradient(circle, rgba(255, 255, 255, 0.1), transparent);
      background-size: 400% 400%, 100% 100%;
      animation: gradientShift 8s ease infinite;
      padding: 24px;
      border-radius: 16px;
    }

    @keyframes gradientShift {
      0% {
        background-position: 0% 50%, center;
      }
      50% {
        background-position: 100% 50%, center;
      }
      100% {
        background-position: 0% 50%, center;
      }
    }
  }
}
```

### Gradient Masks และ Clipping

```css
/* Gradient masks และ clipping effects */
.gradient-masks {
  /* Text masking */
  .gradient-text-mask {
    .rainbow-text {
      background: linear-gradient(
        to right,
        #ef4444,
        #f59e0b,
        #22c55e,
        #3b82f6,
        #8b5cf6
      );
      -webkit-background-clip: text;
      background-clip: text;
      -webkit-text-fill-color: transparent;
      color: transparent;
      font-size: 4rem;
      font-weight: bold;
      text-align: center;
    }

    .radial-text {
      background: radial-gradient(circle, #3b82f6, #8b5cf6, #ec4899);
      -webkit-background-clip: text;
      background-clip: text;
      -webkit-text-fill-color: transparent;
      color: transparent;
      font-size: 3rem;
      font-weight: bold;
    }
  }

  /* Image masking */
  .gradient-image-mask {
    .fade-image {
      position: relative;
      overflow: hidden;
      border-radius: 12px;
    }

    .fade-image img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .fade-image::after {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: linear-gradient(
        to bottom,
        transparent 0%,
        transparent 60%,
        rgba(0, 0, 0, 0.8) 100%
      );
      pointer-events: none;
    }

    .radial-mask {
      position: relative;
      overflow: hidden;
      border-radius: 50%;
    }

    .radial-mask img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .radial-mask::after {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: radial-gradient(
        circle at center,
        transparent 40%,
        rgba(0, 0, 0, 0.9) 80%
      );
    }
  }

  /* Border effects */
  .gradient-borders {
    .animated-border {
      position: relative;
      background: white;
      padding: 24px;
      border-radius: 12px;
      z-index: 1;
    }

    .animated-border::before {
      content: '';
      position: absolute;
      top: -3px;
      left: -3px;
      right: -3px;
      bottom: -3px;
      background: linear-gradient(
        45deg,
        #3b82f6,
        #8b5cf6,
        #ec4899,
        #f59e0b,
        #3b82f6
      );
      background-size: 300% 300%;
      border-radius: 15px;
      z-index: -1;
      animation: borderAnimation 3s ease infinite;
    }

    @keyframes borderAnimation {
      0% {
        background-position: 0% 50%;
      }
      50% {
        background-position: 100% 50%;
      }
      100% {
        background-position: 0% 50%;
      }
    }
  }
}
```

## 4. Responsive Gradients

### Adaptive Gradients

```css
/* Responsive gradients */
.responsive-gradients {
  /* Mobile-first gradient design */
  .adaptive-gradient {
    /* Mobile: Simple gradient */
    background: linear-gradient(to bottom, #3b82f6, #8b5cf6);
  }

  @media (min-width: 768px) {
    .adaptive-gradient {
      /* Tablet: More complex */
      background: radial-gradient(
          ellipse at top right,
          rgba(59, 130, 246, 0.3),
          transparent
        ), linear-gradient(135deg, #3b82f6, #8b5cf6);
    }
  }

  @media (min-width: 1024px) {
    .adaptive-gradient {
      /* Desktop: Full complexity */
      background: radial-gradient(
          ellipse at top right,
          rgba(59, 130, 246, 0.2),
          transparent
        ), radial-gradient(
          ellipse at bottom left,
          rgba(139, 92, 246, 0.2),
          transparent
        ), linear-gradient(135deg, #3b82f6, #8b5cf6, #ec4899);
    }
  }

  /* Orientation-based gradients */
  .orientation-gradients {
    /* Portrait orientation */
    background: linear-gradient(to bottom, #3b82f6, #8b5cf6);
  }

  @media (orientation: landscape) {
    .orientation-gradients {
      /* Landscape orientation */
      background: linear-gradient(to right, #3b82f6, #8b5cf6);
    }
  }

  /* Viewport-based sizes */
  .viewport-gradients {
    .vw-gradient {
      background: radial-gradient(
        circle clamp(100px, 20vw, 300px),
        #3b82f6,
        #8b5cf6
      );
      /* รัศมีปรับตาม viewport */
    }

    .responsive-position {
      background: radial-gradient(
        circle at clamp(20%, 10vw + 10%, 80%) center,
        #3b82f6,
        #8b5cf6
      );
      /* ตำแหน่งปรับตาม viewport */
    }
  }

  /* CSS Custom Properties */
  .css-variables {
    :root {
      --gradient-primary: #3b82f6;
      --gradient-secondary: #8b5cf6;
      --gradient-angle: 45deg;
      --gradient-size: 300px;
    }

    .variable-gradient {
      background: linear-gradient(
        var(--gradient-angle),
        var(--gradient-primary),
        var(--gradient-secondary)
      );
    }

    .variable-radial {
      background: radial-gradient(
        circle var(--gradient-size),
        var(--gradient-primary),
        var(--gradient-secondary)
      );
    }

    /* Theme switching */
    [data-theme='dark'] {
      --gradient-primary: #1e40af;
      --gradient-secondary: #7c3aed;
    }

    [data-theme='light'] {
      --gradient-primary: #60a5fa;
      --gradient-secondary: #a78bfa;
    }
  }
}
```

### Performance Optimization

```css
/* การเพิ่มประสิทธิภาพ gradients */
.gradient-performance {
  /* Hardware acceleration */
  .accelerated-gradient {
    background: linear-gradient(45deg, #3b82f6, #8b5cf6);
    transform: translateZ(0); /* Force GPU acceleration */
    will-change: background; /* Hint to browser */
  }

  /* Efficient animations */
  .efficient-animation {
    background: linear-gradient(45deg, #3b82f6, #8b5cf6, #ec4899, #3b82f6);
    background-size: 300% 300%;
    animation: efficientGradient 3s ease infinite;
  }

  @keyframes efficientGradient {
    0% {
      background-position: 0% 50%;
    }
    50% {
      background-position: 100% 50%;
    }
    100% {
      background-position: 0% 50%;
    }
  }

  /* Prefers-reduced-motion */
  @media (prefers-reduced-motion: reduce) {
    .efficient-animation {
      animation: none;
      background-position: 0% 50%;
    }
  }

  /* CSS-only vs Image comparison */
  .css-gradient {
    /* ✅ Better: CSS gradient */
    background: linear-gradient(to right, #3b82f6, #8b5cf6);
    /* Advantages: Scalable, smaller file size, customizable */
  }

  .image-gradient {
    /* ❌ Avoid: Image gradient */
    background-image: url('gradient.png');
    /* Issues: Fixed size, larger file, not customizable */
  }

  /* Fallbacks for older browsers */
  .gradient-fallback {
    /* Fallback color */
    background-color: #3b82f6;

    /* Modern gradient */
    background-image: linear-gradient(to right, #3b82f6, #8b5cf6);

    /* Older browser support */
    background-image: -webkit-linear-gradient(left, #3b82f6, #8b5cf6);
    background-image: -moz-linear-gradient(left, #3b82f6, #8b5cf6);
    background-image: -o-linear-gradient(left, #3b82f6, #8b5cf6);
  }
}
```

## สรุป: CSS Gradients Best Practices

### Key Concepts 🎯

1. **linear-gradient(): ไล่สีแบบเส้นตรง**

   ```css
   .linear {
     background: linear-gradient(45deg, #3b82f6, #8b5cf6);
   }
   ```

2. **radial-gradient(): ไล่สีแบบรัศมี**

   ```css
   .radial {
     background: radial-gradient(circle, #3b82f6, #8b5cf6);
   }
   ```

3. **การผสม gradients**

   ```css
   .combined {
     background: radial-gradient(
         circle at top,
         rgba(59, 130, 246, 0.3),
         transparent
       ), linear-gradient(45deg, #8b5cf6, #ec4899);
   }
   ```

4. **Performance considerations**
   - ใช้ CSS แทนรูปภาพเมื่อเป็นไปได้
   - ระวัง animations ที่ซับซ้อน
   - ให้ fallback สำหรับ browsers เก่า

### Quick Reference 📋

```css
/* Common gradient patterns */
.gradient-patterns {
  /* Simple linear */
  .linear {
    background: linear-gradient(to right, #3b82f6, #8b5cf6);
  }

  /* Simple radial */
  .radial {
    background: radial-gradient(circle, #3b82f6, #8b5cf6);
  }

  /* Text gradient */
  .text {
    background: linear-gradient(45deg, #3b82f6, #8b5cf6);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  /* Button gradient */
  .button {
    background: linear-gradient(135deg, #3b82f6, #1d4ed8);
    border: none;
    color: white;
    padding: 12px 24px;
    border-radius: 6px;
  }

  /* Card gradient */
  .card {
    background: linear-gradient(
      135deg,
      rgba(255, 255, 255, 0.9),
      rgba(255, 255, 255, 0.7)
    );
    backdrop-filter: blur(10px);
    border-radius: 16px;
    padding: 24px;
  }
}
```

CSS Gradients เป็นเครื่องมือที่ทรงพลังในการสร้างเอฟเฟกต์ที่สวยงามโดยไม่ต้องใช้รูปภาพ ช่วยให้เว็บไซต์โหลดเร็วขึ้นและปรับแต่งได้ง่าย!
