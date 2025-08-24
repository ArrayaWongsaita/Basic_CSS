# CSS Color Properties: คู่มือฉบับสมบูรณ์

## ภาพรวม CSS Color Properties

CSS มี properties หลายตัวที่ใช้ควบคุมสีในการออกแบบเว็บไซต์ ตั้งแต่สีข้อความ สีพื้นหลัง ไปจนถึงสีของ border และ shadow โดยแต่ละ property มีวิธีการใช้งานและระบบสีที่หลากหลาย

### การจัดกลุ่ม Color Properties

```css
/* Text Colors - สีข้อความ */
.text-colors {
  color: #333333;
  text-decoration-color: blue;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

/* Background Colors - สีพื้นหลัง */
.background-colors {
  background-color: #ffffff;
  background: linear-gradient(45deg, red, blue);
}

/* Border Colors - สีขอบ */
.border-colors {
  border-color: #cccccc;
  border-top-color: red;
  outline-color: blue;
}

/* Other Color Properties */
.other-colors {
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  caret-color: blue;
  accent-color: #007bff;
}
```

## 1. color: การควบคุมสีข้อความ

### ความหมายและการทำงาน

`color` property ใช้กำหนดสีของข้อความและเนื้อหาภายใน element รวมถึงสีของ text decorations และ list markers

### Values และการใช้งาน

```css
/* Named colors */
.named-colors {
  color: red;
  color: blue;
  color: green;
  color: black;
  color: white;
  color: transparent;
}

/* Hexadecimal colors */
.hex-colors {
  color: #ff0000; /* สีแดง */
  color: #00ff00; /* สีเขียว */
  color: #0000ff; /* สีน้ำเงิน */
  color: #ffffff; /* สีขาว */
  color: #000000; /* สีดำ */
  color: #333; /* สีเทาเข้ม (shorthand) */
}

/* RGB colors */
.rgb-colors {
  color: rgb(255, 0, 0); /* สีแดง */
  color: rgb(0, 255, 0); /* สีเขียว */
  color: rgb(0, 0, 255); /* สีน้ำเงิน */
  color: rgb(51, 51, 51); /* สีเทา */
}

/* RGBA colors (with transparency) */
.rgba-colors {
  color: rgba(255, 0, 0, 1); /* สีแดงทึบ */
  color: rgba(255, 0, 0, 0.5); /* สีแดงโปร่งใส 50% */
  color: rgba(0, 0, 0, 0.8); /* สีดำโปร่งใส 20% */
}

/* HSL colors */
.hsl-colors {
  color: hsl(0, 100%, 50%); /* สีแดง */
  color: hsl(120, 100%, 50%); /* สีเขียว */
  color: hsl(240, 100%, 50%); /* สีน้ำเงิน */
  color: hsl(0, 0%, 20%); /* สีเทาเข้ม */
}

/* HSLA colors (with transparency) */
.hsla-colors {
  color: hsla(0, 100%, 50%, 1); /* สีแดงทึบ */
  color: hsla(0, 100%, 50%, 0.5); /* สีแดงโปร่งใส 50% */
  color: hsla(240, 100%, 50%, 0.8); /* สีน้ำเงินโปร่งใส 20% */
}

/* Modern color functions */
.modern-colors {
  color: oklch(0.7 0.15 180); /* OKLCH color space */
  color: lab(50% 20 -30); /* LAB color space */
  color: lch(50% 35 120); /* LCH color space */
  color: hwb(120 10% 20%); /* HWB color space */
}

/* CSS custom properties */
.custom-properties {
  color: var(--primary-color);
  color: var(--text-color, #333);
}

/* Special values */
.special-values {
  color: currentColor; /* ใช้สีปัจจุบัน */
  color: inherit; /* สืบทอดจาก parent */
  color: initial; /* ค่าเริ่มต้น */
  color: unset; /* รีเซ็ต */
}
```

### การใช้งานตามบริบท

```css
/* Typography hierarchy */
.heading-primary {
  color: #1a202c; /* สีเข้มสำหรับหัวข้อหลัก */
}

.heading-secondary {
  color: #2d3748; /* สีเข้มปานกลาง */
}

.body-text {
  color: #4a5568; /* สีปานกลางสำหรับเนื้อหา */
}

.text-muted {
  color: #718096; /* สีอ่อนสำหรับข้อความรอง */
}

.text-subtle {
  color: #a0aec0; /* สีอ่อนมากสำหรับข้อความเสริม */
}

/* State colors */
.text-success {
  color: #38a169; /* สีเขียวสำหรับความสำเร็จ */
}

.text-warning {
  color: #ed8936; /* สีส้มสำหรับคำเตือน */
}

.text-error {
  color: #e53e3e; /* สีแดงสำหรับข้อผิดพลาด */
}

.text-info {
  color: #3182ce; /* สีน้ำเงินสำหรับข้อมูล */
}

/* Brand colors */
.brand-primary {
  color: #007bff;
}

.brand-secondary {
  color: #6c757d;
}

/* Link colors */
.link-default {
  color: #007bff;
  text-decoration: none;
}

.link-default:hover {
  color: #0056b3;
  text-decoration: underline;
}

.link-default:visited {
  color: #6f42c1;
}

.link-default:active {
  color: #004085;
}
```

## 2. background-color: การควบคุมสีพื้นหลัง

### ความหมายและการทำงาน

`background-color` property ใช้กำหนดสีพื้นหลังของ element โดยจะแสดงอยู่ใต้ background-image

### Values และการใช้งาน

```css
/* Basic background colors */
.background-basic {
  background-color: white;
  background-color: #f8f9fa;
  background-color: rgb(248, 249, 250);
  background-color: rgba(248, 249, 250, 0.8);
  background-color: hsl(210, 17%, 98%);
  background-color: hsla(210, 17%, 98%, 0.9);
}

/* Transparent backgrounds */
.background-transparent {
  background-color: transparent; /* โปร่งใสทั้งหมด */
  background-color: rgba(255, 255, 255, 0); /* โปร่งใสทั้งหมด */
  background-color: rgba(0, 0, 0, 0.1); /* ดำโปร่งใส 90% */
  background-color: rgba(255, 255, 255, 0.9); /* ขาวโปร่งใส 10% */
}

/* Brand backgrounds */
.bg-primary {
  background-color: #007bff;
  color: white; /* ข้อความสีขาวบนพื้นน้ำเงิน */
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
  color: #212529; /* ข้อความสีเข้มบนพื้นเหลือง */
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
```

### การใช้งานกับความโปร่งใส

```css
/* Overlay effects */
.overlay-dark {
  background-color: rgba(0, 0, 0, 0.5); /* พื้นดำโปร่งใส 50% */
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.overlay-light {
  background-color: rgba(255, 255, 255, 0.8); /* พื้นขาวโปร่งใส 20% */
}

.overlay-colored {
  background-color: rgba(59, 130, 246, 0.1); /* พื้นน้ำเงินโปร่งใส 90% */
}

/* Glass morphism effect */
.glass-effect {
  background-color: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
}

/* Card backgrounds */
.card-white {
  background-color: #ffffff;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.card-gray {
  background-color: #f7fafc;
  border: 1px solid #e2e8f0;
}

.card-dark {
  background-color: #2d3748;
  color: #ffffff;
}
```

## 3. ระบบสี: Hexadecimal Colors

### ความหมายและการทำงาน

Hexadecimal (Hex) เป็นระบบสีที่ใช้เลขฐาน 16 (0-9, A-F) ในการกำหนดค่าสี RGB โดยมีรูปแบบ #RRGGBB หรือ #RGB

### รูปแบบและการใช้งาน

```css
/* Full hex format (#RRGGBB) */
.hex-full-format {
  color: #ff0000; /* สีแดงเต็ม (R=255, G=0, B=0) */
  color: #00ff00; /* สีเขียวเต็ม (R=0, G=255, B=0) */
  color: #0000ff; /* สีน้ำเงินเต็ม (R=0, G=0, B=255) */
  color: #ffffff; /* สีขาว (R=255, G=255, B=255) */
  color: #000000; /* สีดำ (R=0, G=0, B=0) */
}

/* Short hex format (#RGB) */
.hex-short-format {
  color: #f00; /* เท่ากับ #ff0000 */
  color: #0f0; /* เท่ากับ #00ff00 */
  color: #00f; /* เท่ากับ #0000ff */
  color: #fff; /* เท่ากับ #ffffff */
  color: #000; /* เท่ากับ #000000 */
  color: #abc; /* เท่ากับ #aabbcc */
}

/* Extended hex with alpha (#RRGGBBAA) */
.hex-with-alpha {
  background-color: #ff0000ff; /* สีแดงทึบ (alpha = 255) */
  background-color: #ff000080; /* สีแดงโปร่งใส 50% (alpha = 128) */
  background-color: #00ff0040; /* สีเขียวโปร่งใส 75% (alpha = 64) */
  background-color: #0000ff00; /* สีน้ำเงินโปร่งใสทั้งหมด (alpha = 0) */
}

/* Short hex with alpha (#RGBA) */
.hex-short-alpha {
  background-color: #f00f; /* เท่ากับ #ff0000ff */
  background-color: #f008; /* เท่ากับ #ff000088 */
  background-color: #0f04; /* เท่ากับ #00ff0044 */
  background-color: #00f0; /* เท่ากับ #0000ff00 */
}
```

### การแปลงค่า Hex

```css
/* Understanding hex values */
.hex-breakdown {
  /* #RRGGBB format breakdown */
  color: #3b82f6;
  /* 3b = 59 (Red), 82 = 130 (Green), f6 = 246 (Blue) */

  background-color: #ef4444;
  /* ef = 239 (Red), 44 = 68 (Green), 44 = 68 (Blue) */
}

/* Common hex colors */
.common-hex-colors {
  /* Grays */
  color: #000000; /* Black */
  color: #1f2937; /* Gray 800 */
  color: #374151; /* Gray 700 */
  color: #4b5563; /* Gray 600 */
  color: #6b7280; /* Gray 500 */
  color: #9ca3af; /* Gray 400 */
  color: #d1d5db; /* Gray 300 */
  color: #e5e7eb; /* Gray 200 */
  color: #f3f4f6; /* Gray 100 */
  color: #ffffff; /* White */

  /* Brand colors */
  background-color: #3b82f6; /* Blue 500 */
  background-color: #ef4444; /* Red 500 */
  background-color: #10b981; /* Green 500 */
  background-color: #f59e0b; /* Yellow 500 */
  background-color: #8b5cf6; /* Purple 500 */
  background-color: #ec4899; /* Pink 500 */
}

/* Design system hex colors */
:root {
  --color-primary-50: #eff6ff;
  --color-primary-100: #dbeafe;
  --color-primary-200: #bfdbfe;
  --color-primary-300: #93c5fd;
  --color-primary-400: #60a5fa;
  --color-primary-500: #3b82f6;
  --color-primary-600: #2563eb;
  --color-primary-700: #1d4ed8;
  --color-primary-800: #1e40af;
  --color-primary-900: #1e3a8a;
}
```

## 4. ระบบสี: RGB และ RGBA

### ความหมายและการทำงาน

RGB ใช้ค่าสี Red, Green, Blue (0-255) ส่วน RGBA เพิ่ม Alpha channel (0-1) สำหรับความโปร่งใส

### Syntax และการใช้งาน

```css
/* Basic RGB syntax */
.rgb-basic {
  color: rgb(255, 0, 0); /* สีแดง */
  color: rgb(0, 255, 0); /* สีเขียว */
  color: rgb(0, 0, 255); /* สีน้ำเงิน */
  color: rgb(255, 255, 255); /* สีขาว */
  color: rgb(0, 0, 0); /* สีดำ */
  color: rgb(128, 128, 128); /* สีเทา */
}

/* RGBA with transparency */
.rgba-transparency {
  background-color: rgba(255, 0, 0, 1); /* สีแดงทึบ (100%) */
  background-color: rgba(255, 0, 0, 0.8); /* สีแดงโปร่งใส 20% */
  background-color: rgba(255, 0, 0, 0.5); /* สีแดงโปร่งใส 50% */
  background-color: rgba(255, 0, 0, 0.2); /* สีแดงโปร่งใส 80% */
  background-color: rgba(255, 0, 0, 0); /* โปร่งใสทั้งหมด */
}

/* Modern RGB syntax (CSS Color Level 4) */
.rgb-modern {
  color: rgb(255 0 0); /* ไม่ใช้คอมม่า */
  color: rgb(255 0 0 / 0.5); /* RGB with alpha */
  color: rgb(255 0 0 / 50%); /* RGB with alpha percentage */
}

/* RGBA modern syntax */
.rgba-modern {
  background-color: rgba(255 0 0 / 0.8);
  background-color: rgba(255 0 0 / 80%);
}
```

### การใช้งานปรับละเอียด

```css
/* Fine-tuned colors */
.rgb-subtle {
  /* Subtle grays */
  color: rgb(248, 250, 252); /* Very light gray */
  color: rgb(241, 245, 249); /* Light gray */
  color: rgb(226, 232, 240); /* Medium light gray */
  color: rgb(203, 213, 225); /* Medium gray */
  color: rgb(148, 163, 184); /* Dark gray */
  color: rgb(100, 116, 139); /* Very dark gray */

  /* Brand variations */
  background-color: rgb(59, 130, 246); /* Primary blue */
  background-color: rgb(37, 99, 235); /* Darker blue */
  background-color: rgb(29, 78, 216); /* Even darker blue */
}

/* Overlay combinations */
.overlay-combinations {
  /* Dark overlays */
  background-color: rgba(0, 0, 0, 0.1); /* Very light dark overlay */
  background-color: rgba(0, 0, 0, 0.25); /* Light dark overlay */
  background-color: rgba(0, 0, 0, 0.5); /* Medium dark overlay */
  background-color: rgba(0, 0, 0, 0.75); /* Heavy dark overlay */

  /* Light overlays */
  background-color: rgba(255, 255, 255, 0.1); /* Very light white overlay */
  background-color: rgba(255, 255, 255, 0.25); /* Light white overlay */
  background-color: rgba(255, 255, 255, 0.5); /* Medium white overlay */
  background-color: rgba(255, 255, 255, 0.9); /* Heavy white overlay */

  /* Colored overlays */
  background-color: rgba(59, 130, 246, 0.1); /* Blue tint */
  background-color: rgba(16, 185, 129, 0.1); /* Green tint */
  background-color: rgba(239, 68, 68, 0.1); /* Red tint */
}

/* Interactive states */
.interactive-rgb {
  background-color: rgb(59, 130, 246);
  transition: background-color 0.2s ease;
}

.interactive-rgb:hover {
  background-color: rgb(37, 99, 235); /* Darker on hover */
}

.interactive-rgb:active {
  background-color: rgb(29, 78, 216); /* Even darker on active */
}

.interactive-rgb:disabled {
  background-color: rgba(
    59,
    130,
    246,
    0.5
  ); /* Semi-transparent when disabled */
}
```

## 5. ระบบสี: HSL และ HSLA

### ความหมายและการทำงาน

HSL ใช้ Hue (สี 0-360°), Saturation (ความอิ่มตัว 0-100%), Lightness (ความสว่าง 0-100%) ส่วน HSLA เพิ่ม Alpha channel

### Syntax และแนวคิด

```css
/* Basic HSL syntax */
.hsl-basic {
  /* Hue values (0-360 degrees) */
  color: hsl(0, 100%, 50%); /* สีแดง (0°) */
  color: hsl(60, 100%, 50%); /* สีเหลือง (60°) */
  color: hsl(120, 100%, 50%); /* สีเขียว (120°) */
  color: hsl(180, 100%, 50%); /* สีฟ้า (180°) */
  color: hsl(240, 100%, 50%); /* สีน้ำเงิน (240°) */
  color: hsl(300, 100%, 50%); /* สีม่วง (300°) */
}

/* Saturation variations */
.hsl-saturation {
  background-color: hsl(240, 100%, 50%); /* สีน้ำเงินเต็ม */
  background-color: hsl(240, 75%, 50%); /* ลดความอิ่มตัว */
  background-color: hsl(240, 50%, 50%); /* ลดความอิ่มตัวมากขึ้น */
  background-color: hsl(240, 25%, 50%); /* ความอิ่มตัวต่ำ */
  background-color: hsl(240, 0%, 50%); /* สีเทา (ไม่มีความอิ่มตัว) */
}

/* Lightness variations */
.hsl-lightness {
  background-color: hsl(240, 100%, 10%); /* สีน้ำเงินเข้มมาก */
  background-color: hsl(240, 100%, 25%); /* สีน้ำเงินเข้ม */
  background-color: hsl(240, 100%, 50%); /* สีน้ำเงินปกติ */
  background-color: hsl(240, 100%, 75%); /* สีน้ำเงินอ่อน */
  background-color: hsl(240, 100%, 90%); /* สีน้ำเงินอ่อนมาก */
}

/* HSLA with transparency */
.hsla-transparency {
  background-color: hsla(240, 100%, 50%, 1); /* ทึบ */
  background-color: hsla(240, 100%, 50%, 0.8); /* โปร่งใส 20% */
  background-color: hsla(240, 100%, 50%, 0.5); /* โปร่งใส 50% */
  background-color: hsla(240, 100%, 50%, 0.2); /* โปร่งใส 80% */
  background-color: hsla(240, 100%, 50%, 0); /* โปร่งใสทั้งหมด */
}

/* Modern HSL syntax */
.hsl-modern {
  color: hsl(240 100% 50%); /* ไม่ใช้คอมม่า */
  color: hsl(240 100% 50% / 0.5); /* HSL with alpha */
  color: hsl(240 100% 50% / 50%); /* HSL with alpha percentage */
}
```

### การสร้าง Color Palette ด้วย HSL

```css
/* Color palette generation */
:root {
  /* Base hue */
  --primary-hue: 240;

  /* Lightness scale */
  --color-50: hsl(var(--primary-hue), 100%, 95%);
  --color-100: hsl(var(--primary-hue), 100%, 90%);
  --color-200: hsl(var(--primary-hue), 100%, 80%);
  --color-300: hsl(var(--primary-hue), 100%, 70%);
  --color-400: hsl(var(--primary-hue), 100%, 60%);
  --color-500: hsl(var(--primary-hue), 100%, 50%);
  --color-600: hsl(var(--primary-hue), 100%, 40%);
  --color-700: hsl(var(--primary-hue), 100%, 30%);
  --color-800: hsl(var(--primary-hue), 100%, 20%);
  --color-900: hsl(var(--primary-hue), 100%, 10%);
}

/* Complementary colors */
.complementary-colors {
  --primary-hue: 240;
  --complementary-hue: calc(var(--primary-hue) + 180); /* 60 */

  background-color: hsl(var(--primary-hue), 100%, 50%);
  color: hsl(var(--complementary-hue), 100%, 50%);
}

/* Triadic color scheme */
.triadic-colors {
  --base-hue: 240;
  --triadic-1: calc(var(--base-hue) + 120); /* 360 = 0 */
  --triadic-2: calc(var(--base-hue) + 240); /* 120 */

  background: linear-gradient(
    45deg,
    hsl(var(--base-hue), 100%, 50%),
    hsl(var(--triadic-1), 100%, 50%),
    hsl(var(--triadic-2), 100%, 50%)
  );
}

/* Analogous color scheme */
.analogous-colors {
  --base-hue: 240;
  --analogous-1: calc(var(--base-hue) - 30); /* 210 */
  --analogous-2: calc(var(--base-hue) + 30); /* 270 */

  background: linear-gradient(
    90deg,
    hsl(var(--analogous-1), 70%, 50%),
    hsl(var(--base-hue), 70%, 50%),
    hsl(var(--analogous-2), 70%, 50%)
  );
}
```

### การใช้งาน HSL ในการออกแบบ

```css
/* Theme variations */
.theme-light {
  --bg-hue: 240;
  --bg-saturation: 10%;
  --text-hue: 240;

  background-color: hsl(var(--bg-hue), var(--bg-saturation), 98%);
  color: hsl(var(--text-hue), 10%, 15%);
}

.theme-dark {
  --bg-hue: 240;
  --bg-saturation: 15%;
  --text-hue: 240;

  background-color: hsl(var(--bg-hue), var(--bg-saturation), 8%);
  color: hsl(var(--text-hue), 5%, 90%);
}

/* Semantic colors with HSL */
.semantic-hsl {
  /* Success - Green */
  --success-color: hsl(120, 60%, 50%);
  --success-bg: hsl(120, 60%, 95%);
  --success-border: hsl(120, 60%, 80%);

  /* Warning - Yellow/Orange */
  --warning-color: hsl(35, 90%, 50%);
  --warning-bg: hsl(35, 90%, 95%);
  --warning-border: hsl(35, 90%, 80%);

  /* Error - Red */
  --error-color: hsl(0, 70%, 50%);
  --error-bg: hsl(0, 70%, 95%);
  --error-border: hsl(0, 70%, 80%);

  /* Info - Blue */
  --info-color: hsl(210, 80%, 50%);
  --info-bg: hsl(210, 80%, 95%);
  --info-border: hsl(210, 80%, 80%);
}

/* Interactive states with HSL */
.button-hsl {
  --button-hue: 240;
  --button-saturation: 100%;
  --button-lightness: 50%;

  background-color: hsl(
    var(--button-hue),
    var(--button-saturation),
    var(--button-lightness)
  );
  color: white;
  transition: all 0.2s ease;
}

.button-hsl:hover {
  --button-lightness: 45%; /* เข้มขึ้นเมื่อ hover */
}

.button-hsl:active {
  --button-lightness: 40%; /* เข้มขึ้นเมื่อ active */
}

.button-hsl:disabled {
  --button-saturation: 20%; /* ลดความอิ่มตัวเมื่อ disabled */
  --button-lightness: 70%;
}
```

## 6. Modern Color Functions และ Features

### New Color Spaces

```css
/* CSS Color Level 4 และ Level 5 */
.modern-color-spaces {
  /* OKLCH - Perceptually uniform */
  color: oklch(0.7 0.15 180);
  background-color: oklch(0.9 0.05 240);

  /* LAB - Device independent */
  color: lab(50% 20 -30);
  background-color: lab(95% 0 0);

  /* LCH - Cylindrical LAB */
  color: lch(50% 35 120);
  background-color: lch(95% 5 240);

  /* HWB - Hue, Whiteness, Blackness */
  color: hwb(120 10% 20%);
  background-color: hwb(240 90% 5%);

  /* Display P3 color space */
  color: color(display-p3 0.8 0.2 0.6);
  background-color: color(display-p3 0.95 0.95 0.95);

  /* Rec2020 color space */
  color: color(rec2020 0.7 0.3 0.8);
}

/* Color mixing */
.color-mixing {
  /* CSS Color Level 5 - Color mixing */
  background-color: color-mix(in srgb, red 60%, blue);
  color: color-mix(in oklch, hsl(120, 100%, 50%) 70%, white);
  border-color: color-mix(in lab, #ff0000 30%, #00ff00);
}

/* Relative colors */
.relative-colors {
  --base-color: hsl(240, 100%, 50%);

  /* Adjust lightness */
  background-color: hsl(from var(--base-color) h s calc(l + 20%));

  /* Adjust saturation */
  border-color: hsl(from var(--base-color) h calc(s - 30%) l);

  /* Adjust hue */
  color: hsl(from var(--base-color) calc(h + 180) s l);
}
```

### CSS Custom Properties with Colors

```css
/* Advanced color system with custom properties */
:root {
  /* Base colors */
  --primary-h: 240;
  --primary-s: 100%;
  --primary-l: 50%;

  /* Generated variations */
  --primary-50: hsl(var(--primary-h), calc(var(--primary-s) * 0.5), 95%);
  --primary-100: hsl(var(--primary-h), calc(var(--primary-s) * 0.6), 90%);
  --primary-200: hsl(var(--primary-h), calc(var(--primary-s) * 0.7), 80%);
  --primary-300: hsl(var(--primary-h), calc(var(--primary-s) * 0.8), 70%);
  --primary-400: hsl(var(--primary-h), calc(var(--primary-s) * 0.9), 60%);
  --primary-500: hsl(var(--primary-h), var(--primary-s), var(--primary-l));
  --primary-600: hsl(
    var(--primary-h),
    var(--primary-s),
    calc(var(--primary-l) - 10%)
  );
  --primary-700: hsl(
    var(--primary-h),
    var(--primary-s),
    calc(var(--primary-l) - 20%)
  );
  --primary-800: hsl(
    var(--primary-h),
    var(--primary-s),
    calc(var(--primary-l) - 30%)
  );
  --primary-900: hsl(
    var(--primary-h),
    var(--primary-s),
    calc(var(--primary-l) - 40%)
  );

  /* Alpha variations */
  --primary-alpha-10: hsla(
    var(--primary-h),
    var(--primary-s),
    var(--primary-l),
    0.1
  );
  --primary-alpha-20: hsla(
    var(--primary-h),
    var(--primary-s),
    var(--primary-l),
    0.2
  );
  --primary-alpha-50: hsla(
    var(--primary-h),
    var(--primary-s),
    var(--primary-l),
    0.5
  );
}

/* Theme switching */
[data-theme='light'] {
  --bg-primary: var(--primary-50);
  --bg-secondary: white;
  --text-primary: var(--primary-900);
  --text-secondary: var(--primary-700);
}

[data-theme='dark'] {
  --bg-primary: var(--primary-900);
  --bg-secondary: var(--primary-800);
  --text-primary: var(--primary-100);
  --text-secondary: var(--primary-300);
}

/* Dynamic color adjustments */
.dynamic-colors {
  background-color: var(--bg-primary);
  color: var(--text-primary);
  border: 1px solid var(--primary-alpha-20);
  box-shadow: 0 4px 6px var(--primary-alpha-10);
}
```

## 7. Color Accessibility และ Best Practices

### Contrast Ratios

```css
/* WCAG compliant color combinations */
.wcag-aa-normal {
  /* Minimum contrast ratio 4.5:1 for normal text */
  background-color: #ffffff;
  color: #757575; /* 4.54:1 ratio */
}

.wcag-aa-large {
  /* Minimum contrast ratio 3:1 for large text (18pt+ or 14pt+ bold) */
  background-color: #ffffff;
  color: #949494; /* 3.04:1 ratio */
  font-size: 1.25rem;
  font-weight: bold;
}

.wcag-aaa-normal {
  /* Enhanced contrast ratio 7:1 for normal text */
  background-color: #ffffff;
  color: #595959; /* 7.04:1 ratio */
}

.wcag-aaa-large {
  /* Enhanced contrast ratio 4.5:1 for large text */
  background-color: #ffffff;
  color: #757575; /* 4.54:1 ratio */
  font-size: 1.25rem;
}

/* Dark theme compliance */
.dark-theme-wcag {
  background-color: #1a1a1a;
  color: #e0e0e0; /* 12.63:1 ratio */
}

.dark-theme-muted {
  background-color: #1a1a1a;
  color: #b0b0b0; /* 7.95:1 ratio */
}
```

### Color Blind Accessibility

```css
/* Color blind friendly palettes */
.colorblind-friendly {
  /* Don't rely solely on color for meaning */

  /* Success state */
  background-color: #22c55e; /* Green */
  border-left: 4px solid #15803d; /* Visual indicator */
}

.colorblind-friendly::before {
  content: '✓'; /* Icon indicator */
  color: #15803d;
  font-weight: bold;
  margin-right: 0.5rem;
}

/* Error state */
.error-colorblind {
  background-color: #ef4444; /* Red */
  border-left: 4px solid #dc2626;
  position: relative;
}

.error-colorblind::before {
  content: '✕'; /* Icon indicator */
  color: #dc2626;
  font-weight: bold;
  margin-right: 0.5rem;
}

/* Use patterns/textures in addition to color */
.pattern-red {
  background: repeating-linear-gradient(
    45deg,
    #ef4444,
    #ef4444 10px,
    #dc2626 10px,
    #dc2626 20px
  );
}

.pattern-green {
  background: repeating-linear-gradient(
    90deg,
    #22c55e,
    #22c55e 5px,
    #15803d 5px,
    #15803d 10px
  );
}
```

### Reduced Motion Support

```css
/* Respect user preferences */
@media (prefers-reduced-motion: reduce) {
  .animated-colors {
    transition: none;
  }
}

@media (prefers-reduced-motion: no-preference) {
  .animated-colors {
    transition: background-color 0.3s ease, color 0.3s ease;
  }
}

/* High contrast mode support */
@media (prefers-contrast: high) {
  .high-contrast-colors {
    background-color: white;
    color: black;
    border: 2px solid black;
  }
}

@media (prefers-contrast: low) {
  .low-contrast-colors {
    background-color: #f8f9fa;
    color: #6c757d;
  }
}

/* Color scheme preference */
@media (prefers-color-scheme: dark) {
  .auto-dark {
    background-color: #1a1a1a;
    color: #e0e0e0;
  }
}

@media (prefers-color-scheme: light) {
  .auto-light {
    background-color: #ffffff;
    color: #1a1a1a;
  }
}
```

## 8. Color Performance และ Optimization

### Efficient Color Usage

```css
/* Use CSS custom properties for consistency */
:root {
  --primary: #3b82f6;
  --primary-rgb: 59, 130, 246;
  --primary-hsl: 217, 91%, 60%;
}

.efficient-colors {
  /* Reuse color values */
  background-color: var(--primary);
  border-color: var(--primary);

  /* Use RGB values for alpha variations */
  box-shadow: 0 4px 6px rgba(var(--primary-rgb), 0.1);

  /* Use HSL values for variations */
  color: hsl(var(--primary-hsl), 0.8);
}

/* Minimize color calculations */
.optimized-colors {
  /* Pre-calculate common variations */
  --primary-light: #60a5fa; /* Instead of calc() */
  --primary-dark: #2563eb;
  --primary-alpha: rgba(59, 130, 246, 0.1);

  background-color: var(--primary-light);
  border-color: var(--primary-dark);
  box-shadow: 0 1px 3px var(--primary-alpha);
}
```

### Browser Support Fallbacks

```css
/* Progressive enhancement */
.modern-colors {
  background-color: #3b82f6; /* Fallback */
  background-color: oklch(0.7 0.15 240); /* Modern color space */
}

.gradient-fallback {
  background-color: #3b82f6; /* Solid fallback */
  background: linear-gradient(45deg, #3b82f6, #8b5cf6);
}

/* Feature detection */
@supports (background-color: oklch(0.7 0.15 240)) {
  .oklch-colors {
    background-color: oklch(0.7 0.15 240);
  }
}

@supports not (background-color: oklch(0.7 0.15 240)) {
  .oklch-colors {
    background-color: hsl(240, 100%, 60%);
  }
}
```

## สรุป Best Practices

### 1. Color System Design

- ใช้ Design System ที่มี color palette ที่สอดคล้องกัน
- ใช้ CSS Custom Properties สำหรับการจัดการสี
- สร้าง semantic color names (primary, success, warning, error)

### 2. Accessibility

- ตรวจสอบ contrast ratio ให้เป็นไปตาม WCAG guidelines
- ไม่ใช้สีเพียงอย่างเดียวในการสื่อความหมาย
- รองรับ prefers-color-scheme และ prefers-contrast

### 3. Performance

- ใช้ CSS Custom Properties แทนการคำนวณสีซ้ำๆ
- เลือกใช้ color format ที่เหมาะสมกับการใช้งาน
- ใช้ fallback สำหรับ modern color functions

### 4. Color Format Selection

- **Hex**: สำหรับสีที่แน่นอนและไม่ต้องการความโปร่งใส
- **RGB/RGBA**: สำหรับสีที่ต้องการความโปร่งใสหรือการคำนวณ
- **HSL/HSLA**: สำหรับการสร้าง color variations และ themes
- **Modern formats**: สำหรับ wide gamut displays และ design systems ที่ทันสมัย

### 5. Maintenance

- ใช้ naming convention ที่สอดคล้องกัน
- จัดกลุ่มสีตาม semantic meaning
- สร้างเอกสาร color palette สำหรับทีม

การเรียนรู้และใช้งาน CSS Colors อย่างถูกต้องจะช่วยสร้างการออกแบบที่สวยงาม เข้าถึงได้ และมีประสิทธิภาพ!
