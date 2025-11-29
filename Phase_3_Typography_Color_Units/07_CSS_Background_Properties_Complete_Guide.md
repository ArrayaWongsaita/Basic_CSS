# CSS Background Properties: คู่มือฉบับสมบูรณ์

## ภาพรวม CSS Background Properties

Background properties ใน CSS เป็นเครื่องมือที่ทรงพลังในการควบคุมพื้นหลังของ element ตั้งแต่สีพื้นฐาน ภาพ gradient ไปจนถึง effects ที่ซับซ้อน

### Background Properties ทั้งหมด

```css
/* Background properties แยกตาม function */
.all-background-props {
  /* สีพื้นหลัง */
  background-color: #f0f0f0;
  
  /* ภาพพื้นหลัง */
  background-image: url('image.jpg');
  
  /* ตำแหน่งภาพ */
  background-position: center center;
  
  /* ขนาดภาพ */
  background-size: cover;
  
  /* การทำซ้ำภาพ */
  background-repeat: no-repeat;
  
  /* จุดเริ่มต้นการวาด */
  background-origin: padding-box;
  
  /* พื้นที่ที่แสดงภาพ */
  background-clip: border-box;
  
  /* การติดกับหน้าจอ */
  background-attachment: scroll;
  
  /* Shorthand - รวมทุกอย่าง */
  background: #f0f0f0 url('image.jpg') center/cover no-repeat;
}
```

## 1. background-color: สีพื้นหลัง

### ความหมายและการทำงาน

`background-color` กำหนดสีพื้นหลังของ element โดยจะแสดงอยู่ใต้ background-image

### Syntax และ Values

```css
/* Named colors */
.bg-named {
  background-color: white;
  background-color: black;
  background-color: red;
  background-color: blue;
  background-color: transparent; /* โปร่งใส */
}

/* Hexadecimal */
.bg-hex {
  background-color: #ffffff; /* สีขาว */
  background-color: #000000; /* สีดำ */
  background-color: #f8f9fa; /* เทาอ่อน */
  background-color: #212529; /* เทาเข้ม */
  background-color: #3b82f6; /* น้ำเงิน */
  background-color: #fff; /* shorthand */
}

/* RGB และ RGBA */
.bg-rgb {
  background-color: rgb(255, 255, 255);
  background-color: rgb(248, 249, 250);
  background-color: rgba(0, 0, 0, 0.1); /* ดำโปร่งใส 90% */
  background-color: rgba(255, 255, 255, 0.9); /* ขาวโปร่งใส 10% */
  background-color: rgba(59, 130, 246, 0.5); /* น้ำเงินโปร่งใส 50% */
}

/* HSL และ HSLA */
.bg-hsl {
  background-color: hsl(0, 0%, 100%); /* ขาว */
  background-color: hsl(210, 17%, 98%); /* เทาอ่อนมาก */
  background-color: hsl(217, 91%, 60%); /* น้ำเงิน */
  background-color: hsla(217, 91%, 60%, 0.1); /* น้ำเงินโปร่งใส 90% */
}

/* Modern color spaces */
.bg-modern {
  background-color: oklch(0.95 0.02 240);
  background-color: lab(95% 0 0);
  background-color: lch(95% 5 240);
  background-color: color(display-p3 0.95 0.95 0.95);
}

/* CSS Custom Properties */
.bg-variables {
  background-color: var(--bg-primary);
  background-color: var(--bg-secondary, #f8f9fa); /* with fallback */
}

/* Special values */
.bg-special {
  background-color: currentColor; /* สีเดียวกับ color property */
  background-color: inherit; /* สืบทอดจาก parent */
  background-color: initial; /* ค่าเริ่มต้น (transparent) */
  background-color: unset; /* รีเซ็ต */
}
```

### การใช้งานตามบริบท

```css
/* Semantic backgrounds */
.bg-primary {
  background-color: #007bff;
  color: white;
}

.bg-secondary {
  background-color: #6c757d;
  color: white;
}

.bg-success {
  background-color: #28a745;
  color: white;
}

.bg-danger {
  background-color: #dc3545;
  color: white;
}

.bg-warning {
  background-color: #ffc107;
  color: #212529;
}

.bg-info {
  background-color: #17a2b8;
  color: white;
}

.bg-light {
  background-color: #f8f9fa;
  color: #212529;
}

.bg-dark {
  background-color: #343a40;
  color: white;
}

/* UI Component backgrounds */
.card-background {
  background-color: #ffffff;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.modal-overlay {
  background-color: rgba(0, 0, 0, 0.5);
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.tooltip-background {
  background-color: rgba(0, 0, 0, 0.9);
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 0.25rem;
}

.badge-background {
  background-color: #ef4444;
  color: white;
  padding: 0.25rem 0.5rem;
  border-radius: 9999px;
  font-size: 0.75rem;
}

/* Hover and interactive states */
.button-primary {
  background-color: #3b82f6;
  color: white;
  transition: background-color 0.2s ease;
}

.button-primary:hover {
  background-color: #2563eb; /* เข้มขึ้น */
}

.button-primary:active {
  background-color: #1d4ed8; /* เข้มขึ้นอีก */
}

.button-primary:disabled {
  background-color: rgba(59, 130, 246, 0.5);
  cursor: not-allowed;
}

/* List item states */
.list-item {
  background-color: transparent;
  transition: background-color 0.15s ease;
}

.list-item:hover {
  background-color: #f3f4f6;
}

.list-item:active {
  background-color: #e5e7eb;
}

.list-item.selected {
  background-color: #dbeafe;
  color: #1e40af;
}
```

## 2. background-image: ภาพพื้นหลัง

### ความหมายและการทำงาน

`background-image` ใช้กำหนดภาพหนึ่งหรือหลายภาพเป็นพื้นหลังของ element

### Syntax และ Values

```css
/* Single image */
.bg-image-single {
  background-image: url('images/background.jpg');
  background-image: url('https://example.com/image.jpg');
  background-image: url('../images/pattern.png');
}

/* Multiple images (layering) */
.bg-image-multiple {
  /* ภาพแรกอยู่ด้านบน */
  background-image: 
    url('overlay.png'),
    url('main-image.jpg');
}

/* None - ไม่มีภาพ */
.bg-image-none {
  background-image: none;
}

/* Gradients */
.bg-gradient {
  /* Linear gradient */
  background-image: linear-gradient(to right, #ff0000, #0000ff);
  
  /* Radial gradient */
  background-image: radial-gradient(circle, #ff0000, #0000ff);
  
  /* Conic gradient */
  background-image: conic-gradient(from 0deg, red, yellow, green, blue, red);
}

/* Combining image and gradient */
.bg-image-gradient {
  background-image: 
    linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)),
    url('background.jpg');
}

/* CSS filters with images */
.bg-image-filtered {
  background-image: url('image.jpg');
  filter: grayscale(100%) contrast(1.2);
}
```

### การใช้งานภาพหลายชั้น (Layering)

```css
/* Multiple backgrounds with different positions */
.bg-layered {
  background-image: 
    url('foreground.png'),
    url('middle.png'),
    url('background.jpg');
  
  background-position: 
    top right,
    center center,
    bottom left;
  
  background-repeat: 
    no-repeat,
    repeat-x,
    no-repeat;
  
  background-size: 
    100px 100px,
    auto auto,
    cover;
}

/* Pattern overlays */
.bg-pattern-overlay {
  background-image: 
    url('pattern.png'),
    linear-gradient(to bottom, #ffffff, #f0f0f0);
  
  background-size: 
    50px 50px,
    auto;
  
  background-repeat: 
    repeat,
    no-repeat;
}

/* Decorative elements */
.bg-decorative {
  background-image: 
    url('corner-decoration.svg'),
    url('border-pattern.svg'),
    linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  
  background-position: 
    top left,
    bottom right,
    center;
  
  background-repeat: 
    no-repeat,
    repeat-x,
    no-repeat;
}
```

## 3. Linear Gradients: การไล่สีเชิงเส้น

### ความหมายและการทำงาน

Linear gradient สร้างการเปลี่ยนสีแบบเส้นตรงจากจุดหนึ่งไปอีกจุดหนึ่ง

### Syntax และรูปแบบ

```css
/* Basic linear gradients */
.gradient-basic {
  /* ไล่จากบนลงล่าง (default) */
  background-image: linear-gradient(red, blue);
  
  /* ระบุทิศทาง */
  background-image: linear-gradient(to right, red, blue);
  background-image: linear-gradient(to bottom, red, blue);
  background-image: linear-gradient(to top, red, blue);
  background-image: linear-gradient(to left, red, blue);
  
  /* ทิศทางเฉียง */
  background-image: linear-gradient(to bottom right, red, blue);
  background-image: linear-gradient(to top left, red, blue);
}

/* Angle-based gradients */
.gradient-angles {
  background-image: linear-gradient(0deg, red, blue); /* บนลงล่าง */
  background-image: linear-gradient(45deg, red, blue); /* เฉียง 45 องศา */
  background-image: linear-gradient(90deg, red, blue); /* ซ้ายไปขวา */
  background-image: linear-gradient(180deg, red, blue); /* ล่างขึ้นบน */
  background-image: linear-gradient(270deg, red, blue); /* ขวาไปซ้าย */
  background-image: linear-gradient(-45deg, red, blue); /* เฉียงกลับ */
}

/* Multiple color stops */
.gradient-multiple-colors {
  /* 3 สี */
  background-image: linear-gradient(red, yellow, blue);
  
  /* 4 สี */
  background-image: linear-gradient(red, orange, yellow, green);
  
  /* สีเรนโบว์ */
  background-image: linear-gradient(
    to right,
    red,
    orange,
    yellow,
    green,
    blue,
    indigo,
    violet
  );
}

/* Color stops with positions */
.gradient-positions {
  /* ระบุตำแหน่งเป็น percentage */
  background-image: linear-gradient(
    to right,
    red 0%,
    yellow 50%,
    blue 100%
  );
  
  /* ตำแหน่งไม่เท่ากัน */
  background-image: linear-gradient(
    to right,
    red 0%,
    red 30%,
    yellow 30%,
    yellow 70%,
    blue 70%,
    blue 100%
  );
  
  /* Hard stops - ไม่มีการไล่สี */
  background-image: linear-gradient(
    to right,
    red 0% 33.33%,
    yellow 33.33% 66.66%,
    blue 66.66% 100%
  );
}

/* Transparent gradients */
.gradient-transparent {
  /* จาก transparent ไปสี */
  background-image: linear-gradient(
    to bottom,
    transparent,
    rgba(0, 0, 0, 0.8)
  );
  
  /* Fade in/out */
  background-image: linear-gradient(
    to right,
    transparent 0%,
    white 20%,
    white 80%,
    transparent 100%
  );
  
  /* Overlay gradient */
  background-image: 
    linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),
    url('image.jpg');
}
```

### Linear Gradient Patterns

```css
/* Striped patterns */
.gradient-stripes {
  /* แนวนอน */
  background-image: repeating-linear-gradient(
    0deg,
    #e0e0e0,
    #e0e0e0 10px,
    #f5f5f5 10px,
    #f5f5f5 20px
  );
  
  /* แนวตั้ง */
  background-image: repeating-linear-gradient(
    90deg,
    #e0e0e0,
    #e0e0e0 10px,
    #f5f5f5 10px,
    #f5f5f5 20px
  );
  
  /* เฉียง */
  background-image: repeating-linear-gradient(
    45deg,
    #e0e0e0,
    #e0e0e0 10px,
    #f5f5f5 10px,
    #f5f5f5 20px
  );
}

/* Modern UI gradients */
.gradient-modern {
  /* Mesh gradient effect */
  background-image: linear-gradient(
    135deg,
    #667eea 0%,
    #764ba2 100%
  );
  
  /* Sunset gradient */
  background-image: linear-gradient(
    to right,
    #ff512f 0%,
    #dd2476 51%,
    #ff512f 100%
  );
  
  /* Ocean gradient */
  background-image: linear-gradient(
    120deg,
    #89f7fe 0%,
    #66a6ff 100%
  );
  
  /* Aurora gradient */
  background-image: linear-gradient(
    to right,
    #00c6ff 0%,
    #0072ff 100%
  );
}

/* Animated gradients */
.gradient-animated {
  background-image: linear-gradient(
    45deg,
    #667eea,
    #764ba2,
    #f093fb,
    #4facfe
  );
  background-size: 300% 300%;
  animation: gradient-animation 15s ease infinite;
}

@keyframes gradient-animation {
  0%, 100% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
}
```

## 4. Radial Gradients: การไล่สีเป็นวงกลม

### ความหมายและการทำงาน

Radial gradient สร้างการเปลี่ยนสีแบบวงกลมหรือวงรีจากจุดศูนย์กลางออกไปรอบๆ

### Syntax และรูปแบบ

```css
/* Basic radial gradients */
.gradient-radial-basic {
  /* รูปวงกลม (default) */
  background-image: radial-gradient(red, blue);
  
  /* ระบุรูปร่าง */
  background-image: radial-gradient(circle, red, blue);
  background-image: radial-gradient(ellipse, red, blue);
}

/* Size keywords */
.gradient-radial-size {
  background-image: radial-gradient(
    closest-side,
    red, blue
  );
  
  background-image: radial-gradient(
    closest-corner,
    red, blue
  );
  
  background-image: radial-gradient(
    farthest-side,
    red, blue
  );
  
  background-image: radial-gradient(
    farthest-corner,
    red, blue /* default */
  );
}

/* Explicit size */
.gradient-radial-explicit {
  /* ขนาดเป็นค่าตายตัว */
  background-image: radial-gradient(
    100px,
    red, blue
  );
  
  /* ขนาดแบบ percentage */
  background-image: radial-gradient(
    50%,
    red, blue
  );
  
  /* วงรี - กว้าง x สูง */
  background-image: radial-gradient(
    200px 100px,
    red, blue
  );
}

/* Position */
.gradient-radial-position {
  /* Center (default) */
  background-image: radial-gradient(
    circle at center,
    red, blue
  );
  
  /* Top left */
  background-image: radial-gradient(
    circle at top left,
    red, blue
  );
  
  /* Specific coordinates */
  background-image: radial-gradient(
    circle at 30% 40%,
    red, blue
  );
  
  /* Pixel values */
  background-image: radial-gradient(
    circle at 100px 50px,
    red, blue
  );
}

/* Multiple color stops */
.gradient-radial-colors {
  background-image: radial-gradient(
    circle,
    red 0%,
    yellow 30%,
    green 60%,
    blue 100%
  );
  
  /* Hard stops */
  background-image: radial-gradient(
    circle,
    red 0% 25%,
    yellow 25% 50%,
    green 50% 75%,
    blue 75% 100%
  );
}
```

### Radial Gradient Patterns และ Effects

```css
/* Spotlight effect */
.radial-spotlight {
  background-image: radial-gradient(
    circle at center,
    rgba(255, 255, 255, 0.8) 0%,
    rgba(255, 255, 255, 0.4) 30%,
    rgba(255, 255, 255, 0) 60%
  );
}

/* Vignette effect */
.radial-vignette {
  background-image: 
    radial-gradient(
      ellipse at center,
      transparent 0%,
      transparent 50%,
      rgba(0, 0, 0, 0.8) 100%
    ),
    url('image.jpg');
}

/* Circular pattern */
.radial-circles {
  background-image: repeating-radial-gradient(
    circle at center,
    #e0e0e0 0px,
    #e0e0e0 20px,
    #f5f5f5 20px,
    #f5f5f5 40px
  );
}

/* Starburst effect */
.radial-starburst {
  background-image: radial-gradient(
    circle at center,
    white 0%,
    #667eea 40%,
    #764ba2 100%
  );
}

/* Glow effect */
.radial-glow {
  position: relative;
}

.radial-glow::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 200px;
  height: 200px;
  background-image: radial-gradient(
    circle,
    rgba(102, 126, 234, 0.6) 0%,
    rgba(102, 126, 234, 0.3) 40%,
    transparent 70%
  );
  filter: blur(20px);
}

/* Button with radial gradient */
.button-radial {
  background-image: radial-gradient(
    circle at top left,
    #667eea 0%,
    #764ba2 100%
  );
  color: white;
  padding: 1rem 2rem;
  border-radius: 0.5rem;
  transition: transform 0.2s ease;
}

.button-radial:hover {
  transform: scale(1.05);
}
```

## 5. Conic Gradients: การไล่สีแบบรัศมี

### ความหมายและการทำงาน

Conic gradient สร้างการเปลี่ยนสีแบบหมุนรอบจุดศูนย์กลาง เหมาะสำหรับสร้างวงล้อสี หรือ pie charts

### Syntax และรูปแบบ

```css
/* Basic conic gradient */
.gradient-conic-basic {
  background-image: conic-gradient(red, blue);
  
  /* With starting angle */
  background-image: conic-gradient(from 0deg, red, blue);
  background-image: conic-gradient(from 45deg, red, blue);
  background-image: conic-gradient(from 90deg, red, blue);
}

/* Position */
.gradient-conic-position {
  background-image: conic-gradient(at center, red, blue);
  background-image: conic-gradient(at top left, red, blue);
  background-image: conic-gradient(at 30% 40%, red, blue);
}

/* Multiple colors */
.gradient-conic-colors {
  /* Color wheel */
  background-image: conic-gradient(
    red,
    orange,
    yellow,
    green,
    cyan,
    blue,
    violet,
    red
  );
  
  /* With specific angles */
  background-image: conic-gradient(
    from 0deg,
    red 0deg,
    yellow 90deg,
    green 180deg,
    blue 270deg,
    red 360deg
  );
}

/* Hard stops */
.gradient-conic-stops {
  /* Pie chart style */
  background-image: conic-gradient(
    red 0deg 120deg,
    yellow 120deg 240deg,
    blue 240deg 360deg
  );
  
  /* Checkered pattern */
  background-image: conic-gradient(
    from 45deg,
    black 0deg 90deg,
    white 90deg 180deg,
    black 180deg 270deg,
    white 270deg 360deg
  );
}
```

### Conic Gradient Patterns และ Applications

```css
/* Loading spinner */
.conic-spinner {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background-image: conic-gradient(
    from 0deg,
    transparent 0deg 270deg,
    #3b82f6 270deg 360deg
  );
  animation: spin 1s linear infinite;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

/* Progress indicator */
.conic-progress {
  --progress: 75; /* 75% */
  width: 150px;
  height: 150px;
  border-radius: 50%;
  background-image: conic-gradient(
    from -90deg,
    #3b82f6 0deg calc(var(--progress) * 1%),
    #e5e7eb calc(var(--progress) * 1%) 360deg
  );
  position: relative;
}

.conic-progress::after {
  content: '';
  position: absolute;
  top: 10%;
  left: 10%;
  width: 80%;
  height: 80%;
  background-color: white;
  border-radius: 50%;
}

/* Pie chart */
.conic-pie-chart {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  background-image: conic-gradient(
    from 0deg,
    #ef4444 0deg 30deg,      /* 8.3% */
    #f59e0b 30deg 108deg,    /* 21.7% */
    #10b981 108deg 252deg,   /* 40% */
    #3b82f6 252deg 360deg    /* 30% */
  );
}

/* Sunburst pattern */
.conic-sunburst {
  background-image: repeating-conic-gradient(
    from 0deg,
    #667eea 0deg 10deg,
    #764ba2 10deg 20deg
  );
}

/* Checkered circle */
.conic-checkered {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  background-image: repeating-conic-gradient(
    from 0deg,
    #000 0deg 45deg,
    #fff 45deg 90deg
  );
}
```

## 6. background-size: ขนาดของภาพพื้นหลัง

### ความหมายและการทำงาน

`background-size` กำหนดขนาดของภาพพื้นหลัง

### Values และการใช้งาน

```css
/* Keyword values */
.bg-size-keywords {
  /* Auto - ขนาดจริงของภาพ */
  background-size: auto;
  
  /* Cover - ขยายเต็มพื้นที่ (อาจตัดภาพ) */
  background-size: cover;
  
  /* Contain - ���สดงภาพทั้งหมด (อาจมีพื้นที่ว่าง) */
  background-size: contain;
}

/* Length values */
.bg-size-length {
  /* กว้าง x สูง */
  background-size: 200px 100px;
  
  /* กว้างอย่างเดียว (สูงเป็น auto) */
  background-size: 200px auto;
  
  /* สูงอย่างเดียว */
  background-size: auto 100px;
  
  /* ขนาดเท่ากัน */
  background-size: 150px 150px;
}

/* Percentage values */
.bg-size-percentage {
  /* % ของ element */
  background-size: 100% 100%; /* เต็มพื้นที่ */
  background-size: 50% 50%; /* ครึ่งหนึ่ง */
  background-size: 100% auto; /* กว้างเต็ม สูง auto */
  background-size: auto 100%; /* สูงเต็ม กว้าง auto */
}

/* Multiple backgrounds */
.bg-size-multiple {
  background-image: 
    url('logo.png'),
    url('pattern.png'),
    url('background.jpg');
  
  background-size: 
    100px auto,     /* logo */
    50px 50px,      /* pattern */
    cover;          /* background */
}
```

### การใช้งานตามสถานการณ์

```css
/* Hero section - เต็มหน้าจอ */
.hero-section {
  background-image: url('hero-image.jpg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  min-height: 100vh;
}

/* Card with background image */
.card-with-bg {
  background-image: url('card-bg.jpg');
  background-size: cover;
  background-position: center;
  padding: 2rem;
  border-radius: 0.5rem;
}

/* Pattern backgrounds */
.pattern-background {
  background-image: url('pattern.svg');
  background-size: 100px 100px;
  background-repeat: repeat;
}

/* Icon backgrounds */
.icon-background {
  background-image: url('icon.svg');
  background-size: 24px 24px;
  background-repeat: no-repeat;
  background-position: left center;
  padding-left: 32px;
}

/* Responsive background images */
.responsive-bg {
  background-image: url('image.jpg');
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
}

@media (min-width: 768px) {
  .responsive-bg {
    background-size: cover;
  }
}

/* Parallax effect preparation */
.parallax-bg {
  background-image: url('parallax.jpg');
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
}
```

## 7. background-position: ตำแหน่งภาพพื้นหลัง

### ความหมายและการทำงาน

`background-position` กำหนดตำแหน่งเริ่มต้นของภาพพื้นหลัง

### Values และการใช้งาน

```css
/* Keyword values */
.bg-position-keywords {
  /* แนวนอน: left, center, right */
  /* แนวตั้ง: top, center, bottom */
  
  background-position: center; /* center center */
  background-position: top;
  background-position: bottom;
  background-position: left;
  background-position: right;
  
  /* สองคำ */
  background-position: top left;
  background-position: top center;
  background-position: top right;
  background-position: center left;
  background-position: center center;
  background-position: center right;
  background-position: bottom left;
  background-position: bottom center;
  background-position: bottom right;
}

/* Percentage values */
.bg-position-percentage {
  background-position: 0% 0%; /* top left */
  background-position: 50% 50%; /* center center */
  background-position: 100% 100%; /* bottom right */
  background-position: 25% 75%;
  background-position: 0% 50%; /* center left */
  background-position: 100% 50%; /* center right */
}

/* Length values */
.bg-position-length {
  background-position: 20px 30px; /* จากซ้าย 20px, จากบน 30px */
  background-position: 1rem 2rem;
  background-position: 0 0; /* top left */
}

/* Mixed values */
.bg-position-mixed {
  background-position: left 20px top 30px;
  background-position: right 10px bottom 20px;
  background-position: center top 50px;
  background-position: 25% 2rem;
}

/* Multiple backgrounds */
.bg-position-multiple {
  background-image: 
    url('overlay.png'),
    url('main.jpg');
  
  background-position: 
    top right,
    center center;
}
```

### การใช้งาน Creative Positioning

```css
/* Logo positioning */
.header-with-logo {
  background-image: url('logo.svg');
  background-position: left 20px center;
  background-repeat: no-repeat;
  background-size: 150px auto;
  padding-left: 190px;
}

/* Decorative elements */
.card-decorated {
  background-image: 
    url('corner-tl.svg'),
    url('corner-br.svg');
  
  background-position: 
    top left,
    bottom right;
  
  background-repeat: no-repeat, no-repeat;
  background-size: 100px 100px, 100px 100px;
  padding: 2rem;
}

/* Offset backgrounds */
.offset-background {
  background-image: url('texture.jpg');
  background-position: -50px -50px;
  background-repeat: repeat;
}

/* Focal point positioning */
.focal-point {
  background-image: url('portrait.jpg');
  background-position: 30% 20%; /* โฟกัสที่ใบหน้า */
  background-size: cover;
  background-repeat: no-repeat;
}

/* Animated position */
.animated-position {
  background-image: url('sprite.png');
  background-position: 0 0;
  background-size: 400px 100px;
  width: 100px;
  height: 100px;
  animation: sprite-animation 1s steps(4) infinite;
}

@keyframes sprite-animation {
  to {
    background-position: -400px 0;
  }
}

/* Responsive positioning */
.responsive-position {
  background-image: url('landscape.jpg');
  background-position: center top;
  background-size: cover;
}

@media (min-width: 768px) {
  .responsive-position {
    background-position: center center;
  }
}
```

## 8. background-repeat: การทำซ้ำภาพ

### ความหมายและการทำงาน

`background-repeat` กำหนดว่าภาพพื้นหลังจะทำซ้ำอย่างไร

### Values และการใช้งาน

```css
/* Single keyword values */
.bg-repeat-values {
  /* Repeat in both directions (default) */
  background-repeat: repeat;
  
  /* No repeat */
  background-repeat: no-repeat;
  
  /* Repeat horizontally only */
  background-repeat: repeat-x;
  
  /* Repeat vertically only */
  background-repeat: repeat-y;
  
  /* Space - เว้นระยะให้พอดี */
  background-repeat: space;
  
  /* Round - ขยาย/ย่อให้พอดี */
  background-repeat: round;
}

/* Two-value syntax */
.bg-repeat-two-values {
  /* แนวนอน แนวตั้ง */
  background-repeat: repeat no-repeat;
  background-repeat: no-repeat repeat;
  background-repeat: space round;
  background-repeat: round space;
}

/* Multiple backgrounds */
.bg-repeat-multiple {
  background-image: 
    url('pattern.png'),
    url('main.jpg');
  
  background-repeat: 
    repeat,
    no-repeat;
}
```

### Pattern Designs

```css
/* Seamless pattern */
.pattern-seamless {
  background-image: url('seamless-pattern.png');
  background-repeat: repeat;
  background-size: 200px 200px;
}

/* Border pattern */
.pattern-border-top {
  background-image: url('border-pattern.svg');
  background-repeat: repeat-x;
  background-position: top center;
  background-size: auto 20px;
  padding-top: 30px;
}

.pattern-border-left {
  background-image: url('border-pattern.svg');
  background-repeat: repeat-y;
  background-position: left center;
  background-size: 20px auto;
  padding-left: 30px;
}

/* Spaced pattern */
.pattern-spaced {
  background-image: url('icon.svg');
  background-repeat: space;
  background-size: 50px 50px;
}

/* Rounded pattern */
.pattern-rounded {
  background-image: url('tile.png');
  background-repeat: round;
  background-size: 100px 100px;
}

/* Wallpaper effect */
.wallpaper {
  background-image: url('wallpaper-tile.jpg');
  background-repeat: repeat;
  background-size: 300px 300px;
}

/* Dot pattern */
.dot-pattern {
  background-image: radial-gradient(
    circle,
    #333 1px,
    transparent 1px
  );
  background-size: 20px 20px;
  background-repeat: repeat;
}

/* Grid pattern */
.grid-pattern {
  background-image: 
    linear-gradient(rgba(0, 0, 0, 0.1) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0, 0, 0, 0.1) 1px, transparent 1px);
  background-size: 20px 20px;
  background-repeat: repeat;
}
```

## 9. background-attachment: การยึดติดพื้นหลัง

### ความหมายและการทำงาน

`background-attachment` กำหนดว่าภาพพื้นหลังจะเลื่อนตาม content หรือตรึงไว้

### Values และการใช้งาน

```css
/* Values */
.bg-attachment-values {
  /* Scroll - เลื่อนตาม element (default) */
  background-attachment: scroll;
  
  /* Fixed - ตรึงกับ viewport */
  background-attachment: fixed;
  
  /* Local - เลื่อนตาม content ภายใน */
  background-attachment: local;
}

/* Multiple backgrounds */
.bg-attachment-multiple {
  background-image: 
    url('foreground.png'),
    url('background.jpg');
  
  background-attachment: 
    scroll,
    fixed;
}
```

### Parallax และ Effects

```css
/* Parallax scrolling effect */
.parallax-section {
  background-image: url('mountain.jpg');
  background-attachment: fixed;
  background-position: center;
  background-size: cover;
  min-height: 500px;
  position: relative;
}

.parallax-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.3);
}

/* Scrolling content with fixed background */
.fixed-bg-container {
  height: 100vh;
  overflow-y: scroll;
  background-image: url('texture.jpg');
  background-attachment: fixed;
  background-size: cover;
}

/* Local attachment for scrollable content */
.scrollable-content {
  height: 300px;
  overflow-y: scroll;
  background-image: url('watermark.png');
  background-attachment: local;
  background-repeat: no-repeat;
  background-position: center;
  background-size: 200px 200px;
  padding: 2rem;
}

/* Multi-layer parallax */
.multi-parallax {
  position: relative;
  min-height: 100vh;
}

.multi-parallax .layer-1 {
  background-image: url('layer-back.png');
  background-attachment: fixed;
  background-position: center;
  position: absolute;
  width: 100%;
  height: 100%;
  z-index: 1;
}

.multi-parallax .layer-2 {
  background-image: url('layer-front.png');
  background-attachment: scroll;
  background-position: center;
  position: relative;
  z-index: 2;
}
```

## 10. background-origin และ background-clip

### background-origin: จุดเริ่มต้นการวาดพื้นหลัง

```css
/* Values */
.bg-origin-values {
  /* padding-box - เริ่มจาก padding (default) */
  background-origin: padding-box;
  
  /* border-box - เริ่มจาก border */
  background-origin: border-box;
  
  /* content-box - เริ่มจาก content */
  background-origin: content-box;
}

/* Practical examples */
.card-origin-padding {
  border: 10px solid rgba(0, 0, 0, 0.2);
  padding: 20px;
  background-image: url('texture.jpg');
  background-origin: padding-box; /* เริ่มที่ padding */
  background-repeat: no-repeat;
  background-size: cover;
}

.card-origin-border {
  border: 10px solid rgba(0, 0, 0, 0.2);
  padding: 20px;
  background-image: url('texture.jpg');
  background-origin: border-box; /* เริ่มที่ border */
  background-repeat: no-repeat;
  background-size: cover;
}

.card-origin-content {
  border: 10px solid rgba(0, 0, 0, 0.2);
  padding: 20px;
  background-image: url('texture.jpg');
  background-origin: content-box; /* เริ่มที่ content */
  background-repeat: no-repeat;
  background-size: cover;
}
```

### background-clip: พื้นที่ที่แสดงพื้นหลัง

```css
/* Values */
.bg-clip-values {
  /* border-box - แสดงถึง border (default) */
  background-clip: border-box;
  
  /* padding-box - แสดงถึง padding */
  background-clip: padding-box;
  
  /* content-box - แสดงเฉพาะ content */
  background-clip: content-box;
  
  /* text - ตัดตามข้อความ (ต้องใช้ -webkit-) */
  -webkit-background-clip: text;
  background-clip: text;
}

/* Gradient text effect */
.gradient-text {
  background-image: linear-gradient(
    45deg,
    #667eea,
    #764ba2
  );
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  color: transparent;
  font-size: 3rem;
  font-weight: bold;
}

/* Animated gradient text */
.animated-gradient-text {
  background-image: linear-gradient(
    90deg,
    #667eea,
    #764ba2,
    #f093fb,
    #4facfe
  );
  background-size: 300% 100%;
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: gradient-animation 3s ease infinite;
}

/* Image text effect */
.image-text {
  background-image: url('texture.jpg');
  background-size: cover;
  background-position: center;
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  font-size: 4rem;
  font-weight: bold;
}

/* Border with background-clip */
.clipped-border {
  border: 20px solid transparent;
  padding: 20px;
  background-image: 
    linear-gradient(white, white),
    linear-gradient(45deg, #667eea, #764ba2);
  background-origin: padding-box, border-box;
  background-clip: padding-box, border-box;
}
```

## 11. Background Shorthand Property

### Syntax และ Order

```css
/* Shorthand syntax order:
 * background: [color] [image] [position] / [size] [repeat] [attachment] [origin] [clip]
 */

/* Basic shorthand */
.bg-shorthand-basic {
  background: #f0f0f0;
  background: url('image.jpg');
  background: url('image.jpg') no-repeat;
  background: url('image.jpg') center;
  background: url('image.jpg') center/cover;
}

/* Complete shorthand */
.bg-shorthand-complete {
  background: 
    #f0f0f0 
    url('image.jpg') 
    center/cover 
    no-repeat 
    fixed 
    padding-box 
    content-box;
}

/* Multiple backgrounds shorthand */
.bg-shorthand-multiple {
  background: 
    url('top.png') top/100px no-repeat,
    url('bottom.png') bottom/100px no-repeat,
    #f0f0f0;
}

/* Gradient shorthand */
.bg-shorthand-gradient {
  background: linear-gradient(to right, red, blue);
  
  background: 
    linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)),
    url('image.jpg') center/cover no-repeat;
}

/* Common patterns */
.bg-hero {
  background: 
    url('hero.jpg') 
    center/cover 
    no-repeat 
    fixed;
}

.bg-pattern {
  background: 
    url('pattern.png') 
    repeat;
}

.bg-card {
  background: 
    #ffffff 
    url('logo.svg') 
    top right/50px 
    no-repeat;
  padding: 2rem;
}
```

## 12. Advanced Background Techniques

### Multiple Background Layers

```css
/* Complex layering */
.complex-backgrounds {
  background-image: 
    linear-gradient(rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.3)),
    url('overlay-texture.png'),
    url('main-image.jpg');
  
  background-position: 
    center,
    0 0,
    center;
  
  background-size: 
    cover,
    50px 50px,
    cover;
  
  background-repeat: 
    no-repeat,
    repeat,
    no-repeat;
  
  background-attachment: 
    scroll,
    scroll,
    fixed;
}

/* Decorative corners */
.decorative-corners {
  background-image: 
    url('corner-tl.svg'),
    url('corner-tr.svg'),
    url('corner-bl.svg'),
    url('corner-br.svg'),
    linear-gradient(to bottom, #f8f9fa, #ffffff);
  
  background-position: 
    top left,
    top right,
    bottom left,
    bottom right,
    center;
  
  background-size: 
    80px 80px,
    80px 80px,
    80px 80px,
    80px 80px,
    cover;
  
  background-repeat: no-repeat;
  padding: 3rem;
}

/* Frame effect */
.frame-effect {
  background-image: 
    linear-gradient(to right, black 2px, transparent 2px),
    linear-gradient(to bottom, black 2px, transparent 2px),
    linear-gradient(to left, black 2px, transparent 2px),
    linear-gradient(to top, black 2px, transparent 2px);
  
  background-position: 
    top left,
    top right,
    bottom right,
    bottom left;
  
  background-size: 
    100% 2px,
    2px 100%,
    100% 2px,
    2px 100%;
  
  background-repeat: no-repeat;
}
```

### Blend Modes with Backgrounds

```css
/* background-blend-mode */
.bg-blend-modes {
  background-image: 
    linear-gradient(45deg, rgba(255, 0, 0, 0.5), rgba(0, 0, 255, 0.5)),
    url('image.jpg');
  background-size: cover;
  background-position: center;
  background-blend-mode: multiply;
}

/* Different blend modes */
.blend-multiply {
  background-blend-mode: multiply;
}

.blend-screen {
  background-blend-mode: screen;
}

.blend-overlay {
  background-blend-mode: overlay;
}

.blend-darken {
  background-blend-mode: darken;
}

.blend-lighten {
  background-blend-mode: lighten;
}

.blend-color-dodge {
  background-blend-mode: color-dodge;
}

.blend-saturation {
  background-blend-mode: saturation;
}

.blend-hue {
  background-blend-mode: hue;
}

/* Duotone effect */
.duotone-effect {
  background-image: 
    linear-gradient(#667eea, #764ba2),
    url('photo.jpg');
  background-size: cover;
  background-position: center;
  background-blend-mode: multiply;
  filter: contrast(1.2);
}

/* Color overlay effect */
.color-overlay {
  position: relative;
  background-image: url('image.jpg');
  background-size: cover;
  background-position: center;
}

.color-overlay::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, #667eea, #764ba2);
  mix-blend-mode: multiply;
  opacity: 0.7;
}
```

### Responsive Backgrounds

```css
/* Mobile-first approach */
.responsive-background {
  background-image: url('mobile-bg.jpg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}

@media (min-width: 768px) {
  .responsive-background {
    background-image: url('tablet-bg.jpg');
  }
}

@media (min-width: 1024px) {
  .responsive-background {
    background-image: url('desktop-bg.jpg');
  }
}

@media (min-width: 1440px) {
  .responsive-background {
    background-image: url('large-desktop-bg.jpg');
  }
}

/* Retina displays */
.retina-background {
  background-image: url('image.jpg');
  background-size: cover;
}

@media (-webkit-min-device-pixel-ratio: 2),
       (min-resolution: 192dpi) {
  .retina-background {
    background-image: url('image@2x.jpg');
  }
}

/* Dark mode backgrounds */
.theme-background {
  background-color: #ffffff;
  background-image: url('light-pattern.png');
}

@media (prefers-color-scheme: dark) {
  .theme-background {
    background-color: #1a1a1a;
    background-image: url('dark-pattern.png');
  }
}

/* Print backgrounds */
@media print {
  .print-background {
    background: none;
    color: black;
  }
}
```

## 13. Performance และ Best Practices

### Image Optimization

```css
/* Use appropriate image formats */
.optimized-backgrounds {
  /* JPEG for photos */
  background-image: url('photo.jpg');
  
  /* PNG for transparency */
  background-image: url('logo.png');
  
  /* SVG for icons and simple graphics */
  background-image: url('icon.svg');
  
  /* WebP with fallback */
  background-image: url('image.webp');
  background-image: image-set(
    url('image.webp') type('image/webp'),
    url('image.jpg') type('image/jpeg')
  );
}

/* Lazy loading backgrounds */
.lazy-background {
  background-color: #f0f0f0; /* Placeholder */
}

.lazy-background.loaded {
  background-image: url('heavy-image.jpg');
  transition: background-image 0.3s ease;
}

/* Use CSS gradients instead of images */
.gradient-instead-of-image {
  /* Instead of background-image: url('gradient.png'); */
  background-image: linear-gradient(to bottom, #667eea, #764ba2);
}

/* Minimize background layers */
.efficient-layers {
  /* Good - necessary layers only */
  background-image: 
    linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)),
    url('image.jpg');
  
  /* Avoid - too many layers */
  /* background-image: 
    url('layer1.png'),
    url('layer2.png'),
    url('layer3.png'),
    url('layer4.png'),
    url('layer5.png'),
    url('main.jpg');
  */
}
```

### Accessibility Considerations

```css
/* Ensure sufficient contrast */
.accessible-background {
  background-color: #ffffff;
  color: #1a1a1a;
}

/* Provide fallback for background images */
.with-fallback {
  background-color: #3b82f6; /* Fallback color */
  background-image: url('pattern.png');
  color: white;
}

/* Respect reduced motion */
@media (prefers-reduced-motion: reduce) {
  .animated-background {
    background-image: url('static.jpg');
    animation: none;
  }
}

@media (prefers-reduced-motion: no-preference) {
  .animated-background {
    animation: background-animation 20s ease infinite;
  }
}

/* High contrast mode */
@media (prefers-contrast: high) {
  .high-contrast-bg {
    background-image: none;
    background-color: white;
    color: black;
    border: 2px solid black;
  }
}

/* Forced colors mode */
@media (forced-colors: active) {
  .forced-colors-bg {
    background-image: none;
  }
}
```

## สรุป Background Properties Best Practices

### 1. การเลือกใช้ Property

- **background-color**: ใช้สำหรับสีพื้นฐาน เป็น fallback สำหรับ background-image
- **background-image**: ใช้สำหรับภาพ, gradients, patterns
- **background-size**: `cover` สำหรับเต็มพื้นที่, `contain` สำหรับแสดงภาพทั้งหมด
- **background-position**: จัดวางภาพให้เหมาะสม โดยเฉพาะกับ `cover`
- **background-repeat**: `no-repeat` สำหรับภาพหลัก, `repeat` สำหรับ patterns

### 2. Performance

- Optimize รูปภาพก่อนใช้งาน
- ใช้ CSS gradients แทนรูปภาพเมื่อเป็นไปได้
- จำกัดจำนวน background layers
- ใช้ image-set() สำหรับ responsive images
- พิจารณาใช้ lazy loading

### 3. Accessibility

- รักษา contrast ratio ที่เหมาะสม
- ใส่ fallback color เสมอ
- รองรับ reduced motion
- รองรับ high contrast mode
- ไม่ใช้ background-image สำหรับ content ที่สำคัญ

### 4. Responsive Design

- ใช้ mobile-first approach
- จัดเตรียมภาพหลายขนาด
- ใช้ media queries สำหรับจุด breakpoint ต่างๆ
- รองรับ retina displays
- รองรับ dark mode

### 5. Code Organization

- ใช้ CSS custom properties สำหรับค่าที่ใช้บ่อย
- จัดกลุ่ม backgrounds ตาม semantic meaning
- Comment สำหรับ complex background layers
- ใช้ shorthand property เมื่อเหมาะสม

การเรียนรู้และใช้งาน Background Properties อย่างถูกต้องจะช่วยสร้างการออกแบบที่สวยงาม มีประสิทธิภาพ และเข้าถึงได้!